# Access

The payment system is available through three ShopRenter API resources.
- POST _**https://<shop_name>.api.myshoprenter.hu/billing/oneTimeCharges**_
- POST _**https://<shop_name>.api.myshoprenter.hu/billing/recurringCharges**_
- DELETE _**https://<shop_name>.api.myshoprenter.hu/billing/recurringCharges/{recurring_charge_id}**_

## Requesting credentials

The application needs basic auth credentials to use the resources mentioned above. These credentials can be obtained during the application installation process. Further details of the full installation process can be found in the [App development docs](../../development/app-development/01_getting_started.md#application-installation-process).

- The credentials can be requested when Shoprenter calls the RedirectUri provided by the application developer. 
- Once the request HMAC is validated, the app should send a POST Request to Shoprenter to the URL `https://<shopname>.myshoprenter.hu/admin/oauth/access_credential`.<br>
   **POST Request must be sent as _multipart/form-data_ type.**<br>
- The payload of the request must contain the following fields:
  - **client_id:** The ClientId of the application
  - **client_secret:** The ClientSecret value of the application
  - **code:** code received in Request
  - **timestamp:** timestamp received in Request
  - **hmac:** HMAC received in Request
- The request needs to be sent **within 30 seconds** of the initial request sent by Shoprenter to the RedirectUri. The credentials cannot be requested later. Requesting them at a later point requires reinstalling the application.<br>

If the request is valid, a response with a `username`, `password` is returned, which allows the application to access the Payment API. e.g.:<br>
```json
{"username":"YLQVeH2sFFptfR88LjDXb4A", "password":"AcmNWFmzSPaqfNXdnaeN6D5"}
```
<br>

If any data is incomplete or incorrect, the API will send an error message with the corresponding error code in JSON format.

**Errors**:
- If any of the data to be sent is missing, `{"message":"Missing data in credential request","code":400}` will be returned.
- If the client_id and client_secret do not match, `{"message":"App client and request client data mismatch","code":401}` will be returned.
- If the authorization time exceeds 30 seconds, it will return `{"message":"Authorization time expired","code":408}`.
- If an error occurred during installation, `{"message":"App is not installed","code":409}` will be returned.


## Accessing Shoprenter Partner Dashboard

On the Shoprenter Partner Dashboard, financial statements can be viewed and [Payment plans](../docs/h_plan.md) can be managed:
http://billing.shoprenter.hu/login

On the login interface, we can enter the dashboard of the application with the username/token pair received during the [previously mentioned registration](../docs/b_settings.md).

IMPORTANT: It is not necessary to reinstall the applications after the integration of the Payment API.
