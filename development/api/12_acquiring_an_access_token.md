# Acquiring an Access Token

To access the API resources, you first need to obtain client credentials.
Depending on your use case, you can either:

- [Create a custom API client](./10_custom_api_clients.md) for a specific shop (recommended for shop-specific integrations), or
- Register a platform app by completing the [initial app development steps](../app-development/01_getting_started.md).

Once you have your credentials — a client identifier and a client secret — you can send the following request to acquire an access token to the shop's API:

### `POST https://oauth.app.shoprenter.net/{shopName}/app/token`

### Request

**Path Parameters:**

| Parameter  | Type   | Description           |
|------------|--------|-----------------------|
| `shopName` | string | The name of the shop. |


**Request Body Schema:**

| Field           | Type     | Required | Description                                          |
|-----------------|----------|----------|------------------------------------------------------|
| `grant_type`    | string   | Yes      | The value is always `client_credentials` in this case. |
| `client_id`     | string   | Yes      | Your API client's ID.                          |
| `client_secret` | string   | Yes      | Your API client's secret.                      |

**Request Body Example:**

```json
{
  "grant_type": "client_credentials",
  "client_id": "60ef06b358a23f1cd4d89d750694799a",
  "client_secret": "67abd059759611a16a2f2ccb36a7e2c8aa1dc4661c597879d1ad2ce25bc19ea5ea2ba5e7c817b9b6a679"
}
```

### Success Response

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

### Error Responses

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
  `https://{shopName}.api2.myshoprenter.hu/api/`

- Include the access token in the `Authorization` header of each request, using the Bearer scheme:

  ```
  Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJhdWQiOiJlMUlFSEhNeW5nQTJWOHQ2WnM1N1ZibWgiLCJqdGkiOiJhMWUxOWZkYzg...
  ```

Make sure to replace `{shopName}` with the actual shop name.
