# Shop Custom API Clients

If you only need access to the API of a specific shop, there's no need to develop a full app for the platform. Instead,
the shop administrator can create an API client for you and give you it's credentials to use.

## Client permissions

Such clients will only have access to the API of the specific shop they were created in and will be limited to the
scopes the shop administrator has explicitly granted them. The set of scopes permitted for any such client is
modifiable, so if you realize during development that additional permissions are needed, the shop administrator can
update your client’s allowed scopes accordingly.

The interface for creating, updating, or deleting a shop’s custom API clients is available in the shop admin under
_Settings > API Settings_.

These clients can use the **Client Credentials** grant type to obtain an OAuth access token as described below.

## Acquiring an Access Token

Once you have your credentials — a client identifier and a client secret — you can send the following request to acquire
an access token to the shop's API:

### `POST https://oauth.app.shoprenter.net/{shop_id}/app/token`

#### Request

**Path Parameters:**

| Parameter | Type   | Description                     |
|-----------|--------|---------------------------------|
| `shop_id` | string | The ID of the shop (it's name). |


**Request Body Schema:**

| Field           | Type     | Required | Description                                            |
|-----------------|----------|----------|--------------------------------------------------------|
| `grant_type`    | string   | Yes      | The value is always `client_credentials` in this case. |
| `client_id`     | string   | Yes      | Your API client's client ID.                           |
| `client_secret` | string   | Yes      | Your API client's client secret.                       |

**Request Body Example:**

```json
{
  "grant_type": "client_credentials",
  "client_id": "60ef06b358a23f1cd4d89d750694799a",
  "client_secret": "67abd059759611a16a2f2ccb36a7e2c8aa1dc4661c597879d1ad2ce25bc19ea5ea2ba5e7c817b9b6a679"
}
```

#### Success Response

**Status:** `200 OK`

**Response Body Example:**

```json
{
  "token_type": "Bearer",
  "expires_in": 3600,
  "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJhdWQiOiJlMUlFSEhNeW5nQTJWOHQ2WnM1N1ZibWgiLCJqdGkiOiJhMWUxOWZkYzg..."
}
```

**Response Body Schema:**

| Field          | Type   | Description                                                                                                                                          |
|----------------|--------|------------------------------------------------------------------------------------------------------------------------------------------------------|
| `token_type`   | string | Value is always "Bearer" in this case.                                                                                                               |
| `expires_in`   | number | The number of seconds the token is valid for. After it has expired, a new token must be requested the same way to continue accessing the shop's API. |
| `access_token` | string | JWT access token.                                                                                                                                    |

#### Error Responses
**Status:** `401 Unauthorized`

**Response Body Example:**

```json
{
    "error": "invalid_client",
    "error_description": "Client authentication failed",
    "message": "Client authentication failed"
}
```

**Status:** `400 Bad Request`

**Response Body Example:**

```json
{
    "error": "invalid_request",
    "error_description": "The request is missing a required parameter, includes an invalid parameter value, includes a parameter more than once, or is otherwise malformed.",
    "hint": "Check the `client_id` parameter",
    "message": "The request is missing a required parameter, includes an invalid parameter value, includes a parameter more than once, or is otherwise malformed."
}
```

## Accessing the API with the Access Token

To make authenticated requests to the API using an access token:

- Use the API2 base URL for the specific shop:  
  `https://{shop_id}.api2.myshoprenter.hu/`

- Include the access token in the `Authorization` header of each request, using the Bearer scheme:

  ```
  Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJhdWQiOiJlMUlFSEhNeW5nQTJWOHQ2WnM1N1ZibWgiLCJqdGkiOiJhMWUxOWZkYzg...
  ```

Make sure to replace `{shop_id}` with the actual shop name.
