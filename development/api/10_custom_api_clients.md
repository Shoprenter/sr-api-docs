# Shop Custom API Clients

If you only need access to the API of a specific shop, there's no need to develop a full app for the platform. Instead, the shop administrator can create an API client for you via the shop’s admin interface and provide you its credentials.

## Client permissions

Such clients will only have access to the API of the specific shop they were created in and will be limited to the
scopes the shop administrator has explicitly granted them. The set of scopes permitted for any such client is
modifiable, so if you realize during development that additional permissions are needed, the shop administrator can
update your client’s allowed scopes accordingly.

The interface for creating, updating, or deleting a shop’s custom API clients is available in the shop admin under
_Settings > API Settings_.

These clients can use the **Client Credentials** grant type to obtain an OAuth access token as described [here](./12_acquiring_an_access_token.md).
