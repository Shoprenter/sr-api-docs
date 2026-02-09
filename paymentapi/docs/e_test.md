# Test mode

We provide an opportunity to safely test the integration of the Payment API - during its development.
To start a payment in test mode, when creating a new payment, which can be [one-time](../docs/g_one_time_charge.md) or even [recurring](../docs/i_recurring_charge.md), the payload must contain the **test** property with a value of **true**.

Example of POST data in case of recurring charge:

```javascript
{
    "planId": 1,
    "notificationUrl": "https://notification-webhook-url.com",
    "failedUrl": "https://failedUrl.com",
    "successUrl": "https://successUrl.com",
    "test": true
}
```
In this case, bank card payment starts in sandbox mode. No invoice is issued.
Instead, the system sends a data summary to the email address specified in the store's billing information.
In this way, it can be checked that the invoice is issued with the correct data, even in the case of live payment.

Test Barion card data:
https://docs.barion.com/Sandbox

Successful test card payment details:<br>
Card number: **4444 8888 8888 5559**<br>
Expiration date: **Any future date eg: 12/25**<br>
CVC: **Any three-digit number eg: 123**<br>

Unsuccessful test card payment data:<br>
Card number: **4444 8888 8888 4446**<br>
Expiration date: **Any future date eg: 12/25**<br>
CVC: **Any three-digit number eg: 123**<br>
