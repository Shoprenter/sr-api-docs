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
- **Name of the test store:** At the very beginning of the development, a test store must be requested on [shoprenter.hu](https://www.shoprenter.hu/testigenyles/?devstore=1).
  Here you can enter the shop name, which will be visible in the first part of the shop domain - `[shopName].myshoprenter.hu`.

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
4. If the server found the request OK, it sends a POST Request to Shoprenter to the URL `https://[shopname].myshoprenter.hu/admin/oauth/access_credential`. With this request, the application can retrieve the username/password pair required to use the API of the given store.<br>
   **POST Request must be sent as _multipart/form-data_ type.**<br>

The payload of the request must contain the following fields:
- **client_id:** The ClientId of the application
- **client_secret:** The ClientSecret value of the application
- **code:** code received in Request
- **timestamp:** timestamp received in Request
- **hmac:** HMAC received in Request

The username/password pair arrives with a JSON Response, e.g.:<br><br>
`{"username":"YLQVeH2sFFptfR88LjDXb4A","password":"AcmNWFmzSPaqfNXdnaeN6D5"}` <br><br>

If any data is incomplete or incorrect, the API will send an error message with the corresponding error code in JSON format.

<br>**Errors**:
- If any of the data to be sent is missing, `{"message":"Missing data in credential request","code":400}` will be returned.
- If the client_id and secret_id to be sent differ, `{"message":"App client and request client data mismatch","code":401}` will be returned.
- If the authorization time exceeds 30 seconds, it will return `{"message":"Authorization time expired","code":408}`.
- If an error occurred during installation, `{"message":"App is not installed","code":409}` will be answered.
6. If Shoprenter finds the POST Request appropriate, it will respond with a `username`, `password` pair, which allows the application to access the API of the given store.
   The timestamp in the Shoprenteres request started in step 2 is used to check whether the client application starts requesting API access **within 30 seconds**!
7. If the application has received the authentication data, the user must be redirected to the **app_url** received in the query string.
8. Shoprenter opens the EntryPoint for the application. The Request will contain the parameters written in point 2.
9. After installation, Shoprenter only sends requests to the Entrypoint. In all cases, with the parameters written in point 2.

**Note:** It is possible to decorate the value of `app_url` (the Shoprenteres URL of the application) with unique query string parameters.
These parameters will also appear in the EntryPoint URL, along with the parameters used for authentication (`shopname`, `code`, `timestamp`, `hmac`).

Example:
Let EntryPoint be `https://app.example.com/entryPoint`
The application redirects to: `https://[primaryDomain]/admin/app/[appId]?pelda=parameter`
In this case, EntryPoint is called like this: `https://app.example.com/entryPoint?shopname=[shopname]&code=[code]&timestamp=[timestamp]&hmac=[hmac]&pelda=parameter`

### Example applications
- [SR Demo app PHP](https://github.com/Shoprenter/sr-demo-app-php)
- [SR Demo app PHP Slim](https://github.com/Shoprenter/sr-demo-app-php-slim)
- [SR Demo app Node.js](https://github.com/Shoprenter/sr-demo-app-node)
