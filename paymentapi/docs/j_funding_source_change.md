# Bank card change

In the case of Recurring payments, bank cards that have exceeded their expiration date or cannot be charged due to other problems can be a problem..

## In operation

It is very similar to the [Recurring Charge Payment](./i_recurring_charge.md) process.
The application makes a call to the billing/fundingSourceChange endpoint, where it sends the ID of the Recurring payment.
It then returns a **changeUrl** to which the application redirects the customer.

The admin will arrive at the card replacement confirmation page, which will be available on the Shoprenter admin interface.
You can accept or reject the exchange of the card.

After acceptance, you enter the details of your new card on the Barion Gateway, and we register the new payment device for the given subscription with a HUF 10 transaction.

In case of successful payment, we will **immediately** return the deducted HUF 10.

At the end of the process, the admin is redirected to a page indicating success or failure.

The bank card can only be changed in the case of recurring payments!

## Usage

We need:
- A button on the interface of our application, with which the subscriber can start the exchange
- For the identifier of the Recurring payment - recurringChargeId
- To a notification url (optional) - notificationUrl

**Important:**
- Only ACTIVE and FROZEN status and
- you can only apply for a card change for subscriptions created after 19.05.2021.

## Entry point

POST https://<shopname>.api.myshoprenter.hu/billing/fundingSourceChanges

Example payload:

```javascript
{
    "recurringChargeId": 12, 
    "notificationUrl": "https://notficationUrl.com"
}
```

Example response:

```javascript
{
        "changeId": 43, 
        "subscriptionId": 12, 
        "paymentStatus": "active", 
        "status": "pending", 
        "changeUrl": "https://<shop_domain>/admin/app/payment/12/change/43",
        "notificationUrl": "https://notficationUrl.com", 
        "createdAt": "2022-05-09 08:09:41"
}
```

You can read about the statuses generated during the card change process here: [Card exchange statuses](./k_statuses.md)

## Testing

For testing, we need a test Recurring payment, you can read more about it [here](./e_test.md). The bank card change performed on this payment will also take place in the test system.

## Webhook

Here, too, it is possible to request a notification about status changes related to the card replacement process.
More information can be found here: [Notification webhooks - a notificationUrl](./l_notifications.md)
