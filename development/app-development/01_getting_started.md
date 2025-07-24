# Initial steps

### Data required to register the Application:

Please send the necessary data to the email address partnersupport@shoprenter.hu.

**The application owner must provide the following information.**
- **Application name:** this will appear in the list of installable applications.
- **EntryPoint:** Application entry point. Provided by the app developer. It must be accessible via HTTPS protocol.
- **RedirectUri:** The authentication entry point of the application will request the authentication data for the API of the Shoprenter store via this URL. It must be accessible via the HTTPS protocol.
  **Attention!** If e.g. the client will be a Single-Page Application (SPA), where each route is specified with a URL resource identifier (`https://example.com/shoprenter#redirect`), we cannot accept it for technical reasons.
- **UninstallUri:** After the application is uninstalled, a GET request will be sent to this URL so that the application can perform one last operation.
  (Note: the following data will be added to the query string: `shopname`, `code`, `timestamp`, `hmac`.)
- **Application logo:** the logo image appearing in the application list (**250x150px**).
- **Short description of application:** Short text of maximum 70 characters.
- **Application details link:** Link to the application details/sales page.
- **Type of application:** The application has two forms:
    - Embedded: The URL given to the EntryPoint is loaded into an Iframe, which can be accessed via the URL belonging to the application, on the Shoprenter admin interface (e.g. `https://shopname.myshoprenter.hu/admin/app/1 `).
    - Redirected: When redirecting, the user is simply redirected to the specified EntryPoint URL.
- **Name of the test store:** At the very beginning of the development, a test store must be requested on [shoprenter.hu](https://www.shoprenter.hu/tesztigenyles/?devstore=1).
  Here you can enter the shop name, which will be visible in the first part of the shop domain - `[shopName].myshoprenter.hu`.
- **Required scopes:** You must specify the scopes your application will require in advance. The client credentials you'll receive will only grant access to these pre-defined scopes. Required scopes per API resource are listed [here](../api/11_scopes.md). When installing the app, the shop owner will be presented with this list of required scopes, allowing them to grant informed consent to the app’s data access.

**After registering the application, Partner Support will send the following data:**
- **AppId:** the identifier of the application within Shoprenter.
- **ClientId:** is the application ID.
- **ClientSecret:** key to identify requests.
- **App URL:** the Shoprenter URL of the application on the admin side. E.g.: `demo.myshoprenter.hu/admin/app/55`

### Application installation process:
1. The user clicks to install the application on the Shoprenter admin interface.
2. Shoprenter calls the RedirectUri (GET Request) provided by the application developer.
   Parameters passed during the call:
    - **shopname:** the name of the shop from which the call was initiated
    - **code:** generated hash
    - **timestamp:** request time
    - **hmac:** check hash
    - **app_url** The URL to which the user must be redirected after running the script under RedirectUri
3. It is advisable for the serving party to check that the request was indeed sent by Shoprenter.
   To verify that the request was sent by Shoprenter:
   The part of the query string without HMAC (`code=0907a61c0c8d55e99db179b68161bc00&shopname=example&timestamp=1337178173`) encoded with **ClientSecret** using the sha256 algorithm must be equivalent to the value of the HMAC parameter of the query string.
4. Once the request is validated, the user must be redirected to the **app_url** received in the query string. <br> _Previously, the application server was supposed to request credentials for Basic Authentication from Shoprenter at this point in the process, but Basic Authentication has since been deprecated and is no longer supported. Attempting to request Basic Authentication credentials will result in a 403 error response from the Shoprenter endpoint._ <br><br>**Note:** It is possible to decorate the value of `app_url` (Shoprenter's URL of the application) with unique query string parameters.
   These parameters will also appear in the EntryPoint URL, along with the parameters used for request authentication (`shopname`, `code`, `timestamp`, `hmac`).<br>
   **Example:** <br> Let EntryPoint be `https://app.example.com/entryPoint`<br>
   The application redirects to: `https://[primaryDomain]/admin/app/[appId]?pelda=parameter`<br>
   In this case, EntryPoint is called like this: `https://app.example.com/entryPoint?shopname=[shopname]&code=[code]&timestamp=[timestamp]&hmac=[hmac]&pelda=parameter`<br><br>
5. Shoprenter opens the EntryPoint for the application. The request will contain the parameters described in step 2.
6. After installation, Shoprenter only sends requests to the Entrypoint. In all cases, with the parameters described in step 2.
7. After obtaining the client credentials from Partner Support and completing the installation process, the application is ready to request access tokens for the shop's API. Instructions for requesting an access token are specified [here](../api/12_acquiring_an_access_token.md)

### Updating application scopes

Over time, your application may require additional API permissions, for example, when new features are added. In such cases, you should contact Partner Support with the updated list of required scopes so they can update them on the Shoprenter platform.

However, by this time, the application may have been installed in multiple shops, and their owners have not consented to the app acquiring these new access privileges in their shops.

To obtain consent for the new scopes in shops that have already installed the app, the shop owners must be directed to the following URL:

#### `GET https://{shopName}.myshoprenter.hu/admin/app/{clientId}/approveScopes`

**Path Parameters:**

| Parameter  | Type   | Description                      |
|------------|--------|----------------------------------|
| `shopName` | string | The name of the shop.            |
| `clientId` | string | The ClientId of the application. |

It is up to the application to decide whether consent is obtained via in-app redirection or by emailing shop owners who have already installed the app — or any other way. 

Until the shop owner grants consent — by clicking the button on the URL mentioned above — the application will not have access to the new scopes in that specific store.


### Example applications
- [SR Demo app PHP](https://github.com/Shoprenter/sr-demo-app-php)
- [SR Demo app PHP Slim](https://github.com/Shoprenter/sr-demo-app-php-slim)
- [SR Demo app Node.js](https://github.com/Shoprenter/sr-demo-app-node)
