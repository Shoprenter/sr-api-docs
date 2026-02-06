# One Time Charge

## Properties

| Property        | Description                                                                                                      |Obligatory       |Readable            |
|-----------------|------------------------------------------------------------------------------------------------------------------|:-------------:|:-------------------:|
| id              | Identity                                                                                                         |               |          x          |
| name            | Name (e.g.: Full Version, Monthly Gold package, etc.)                                                            |       x       |          x          |
| status          | Status (see [Statuses](../docs/k_statuses.md))                                                                     |               |          x          |
| price           | An object, contains:                                                                                             |               |          x          |
|                 | **grossAmount**: Gross price                                                                                     |               |                     |
|                 | **vatAmount**: VAT amount                                                                                        |               |                     |
|                 | **netPrice**: Net price                                                                                          |               |                     |
|                 | **roundedGrossAmount**: Rounded Gross price                                                                      |               |                     |
| netPrice        | Net Price                                                                                                        |       x       |          x          |
| notificationUrl | An API webhook notification about events in the system is sent to this URL                                       |               |          x          |
| successUrl      | If the payment is successful, we will direct the store owner here                                                |       x       |          x          |
| failedUrl       | In case of payment failure, we will direct the store owner here                                                  |       x       |          x          |
| updatedAt       | Date of modification                                                                                             |               |          x          |
| createdAt       | Date of creation                                                                                                 |               |          x          |
| deletedAt       | Date of deletion                                                                                                 |               |          x          |
| test            | If the value is **true**, the payment is processed in test mode. It does not issue an invoice. (Default: false)* |               |          x          |
| confirmationUrl | After creation, the customer must be redirected to this URL                                                      |               |          x          |

\* The system sends an invoice summary email to the email title specified in the store's billing information.

## Entry point

POST https://<shop_name>.api.myshoprenter.hu/billing/oneTimeCharges

Example payload:

```javascript
{
    "name": "ACME app purchase",
    "netPrice": 10000,
    "notificationUrl": "https://notification-webhook-url.com",
    "failedUrl": "https://failedUrl.com",
    "successUrl": "https://successUrl.com",
    "test": true
}
```

Response:

```javascript
{
    "id": 5,
    "name": "ACME app purchase",
    "status": "pending",
    "price": {
        "grossAmount": 12700,
        "vatAmount": 2700,
        "netPrice": 10000,
        "roundedGrossAmount": 12700
    },
    "netPrice": 10000,
    "paymentUrl": "",
    "notificationUrl": "https://notification-webhook-url.com",
    "successUrl": "https://successUrl.com",
    "failedUrl": "https://failedUrl.com",
    "updatedAt": "2020-02-24 15:13:15",
    "createdAt": "2020-02-24 15:13:15",
    "deletedAt": null,
    "test": true,
    "confirmationUrl": "https://<shop_name>.shoprenter.hu/admin/app/payment/onetime/5"
}
```

## The payment requesting

GET https://<shop_name>.api.myshoprenter.hu/billing/oneTimeCharges/<charge_id>

Example:
GET https://exampleshop.api.myshoprenter.hu/billing/oneTimeCharges/12

Response:

```javascript
{
    "id": 12,
    "name": "ACME app purchase",
    "status": "pending",
    "price": {
        "grossAmount": 12700,
        "vatAmount": 2700,
        "netPrice": 10000,
        "roundedGrossAmount": 12700
    },
    "netPrice": 10000,
    "paymentUrl": "",
    "notificationUrl": "https://notification-webhook-url.com",
    "successUrl": "https://successUrl.com",
    "failedUrl": "https://failedUrl.com",
    "updatedAt": "2020-02-24 15:13:15",
    "createdAt": "2020-02-24 15:13:15",
    "deletedAt": null,
    "test": true
}
```

## Usage
1. I create a new oneTimeCharge with a POST request
2. In the response, I receive the confirmationUrl, to which I redirect the current customer
3. The current customer is transferred to the Shoprenter payment confirmation page
4. The current customer decides whether to accept or reject the purchase. In case of rejection, the system redirects you back to the entry point of the application.
5. If accepted, you will be redirected to the interface of the service handling the transaction.
6. In case of successful payment, the system directs the customer to successUrl, in case of failure to failedUrl.

The system continuously informs the application about events during the process
via notificationUrl.

## Operation by example
I would like to provide my application to Shoprenter stores for a one-time installation fee. My installation fee is no different, I only have to collect one type of amount.

My payment can therefore be purchased in the form of a one-time charge (One Time Charge) for HUF 10,000 net. Since we charge an installation fee, the name of the package should be e.g. "Installation Fee".
The "Installation fee" package will look like this:

```javascript
{
    "name": "Install fee",
    "netPrice": 10000,
    "notificationUrl": "https://notification-webhook-url.com",
    "failedUrl": "https://failedUrl.com",
    "successUrl": "https://successUrl.com",
    "test": false
}
```

So, if the shop owner subscribes, it only happens once in the net value of HUF 10,000.

## Flow chart

![One Time Charge](../image/one-time-charge-flow.png)
