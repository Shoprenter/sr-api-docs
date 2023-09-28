# Recurring Charge

## Properties

| Property           | Description                                                                                                                                                                                                                                                                                     |Obligatory       | Readable |
|--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-------------:|:--------:|
| planId             | Payment plan identity. (see: [Payment Plan](../docs/h_plan.md))                                                                                                                                                                                                                                 |       x       |    x     |
| billingCycleLength | Payment cycle length. How many months is the fee paid?<br/>Ex.: the value 1 means 1 month (30 days), so the deduction takes place every month.                                                                                                                                                  |               |    x     |
| billingCycleCount  | Payment cycle number. How many times are repeated fee payments made? <br/>**Attention:** If it is null, the fee collection will never stop!                                                                                                                                                     |               |    x     |
| expirationDate     | Expiration date. It shows when the system will repeat the fee collection                                                                                                                                                                                                                        |               |    x     |
| id                 | Identity                                                                                                                                                                                                                                                                                        |               |    x     |
| name               | Name (pl.: Teljes Version)                                                                                                                                                                                                                                                                      |               |    x     |
| status             | Status (See: [Statuses](../docs/k_statuses.md))                                                                                                                                                                                                                                                 |               |    x     |
| price              | An object, contains:                                                                                                                                                                                                                                                                            |               |    x     |
|                    | **grossAmount**: Gross price                                                                                                                                                                                                                                                                    |               |          |
|                    | **vatAmount**: VAT amount                                                                                                                                                                                                                                                                       |               |          |
|                    | **netPrice**: Net price                                                                                                                                                                                                                                                                         |               |          |
|                    | **roundedGrossAmount**: Rounded gross amount                                                                                                                                                                                                                                                    |               |          |
| netPrice           | Net price                                                                                                                                                                                                                                                                                       |               |    x     |
| notificationUrl    | The API sends notification of events in the system to this URL                                                                                                                                                                                                                                  |               |    x     |
| successUrl         | If the payment is successful, we will direct the store owner here                                                                                                                                                                                                                               |       x       |    x     |
| failedUrl          | In case of payment failure, we will direct the store owner here                                                                                                                                                                                                                                 |       x       |    x     |
| updatedAt          | Date of modification                                                                                                                                                                                                                                                                            |               |    x     |
| createdAt          | Date of creation                                                                                                                                                                                                                                                                                |               |    x     |
| deletedAt          | Date of deletion                                                                                                                                                                                                                                                                                |               |    x     |
| test               | If the value is **true**, the payment is processed in test mode. It does not issue an invoice. (Default: false)*                                                                                                                                                                                |               |    x     |
| confirmationUrl    | After creation, the store owner must be directed to this URL                                                                                                                                                                                                                                    |               |    x     |
| trialDays          | Number of trial period days, which the app owner does not charge the app user. The invoice is issued by sliding the number of these days. By default, this is 0 days<br/>(see: [Trial Recurring Charge (Trial Recurring Charge)](#probaidoszakos-ismetlodo-dijfizetes-trial-recurring-charge)). |               |    x     |

\* The system sends an invoice summary email to the email address specified in the store's billing information.

## Entry point

POST https://<shop_name>.api.myshoprenter.hu/billing/recurringCharges

Example payload:

```javascript
{
    "planId": 1,
    "notificationUrl": "https://notification-webhook-url.com",
    "failedUrl": "https://failedUrl.com",
    "successUrl": "https://successUrl.com",
    "test": true,
    "trialDays": 10
}
```

Response:

```javascript
{
    "planId": 1,
    "billingCycleLength": 1,
    "billingCycleCount": 12,
    "expirationDate": null,
    "trialDays": 10,
    "id": 5,
    "name": "ACME application Gold package",
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
    "confirmationUrl": "https://<shop_name>.shoprenter.hu/admin/app/payment/recurring/5"
}
```

## Request Recurring Charge

GET https://<shop_name>.api.myshoprenter.hu/billing/recurringCharges/<charge_id>

Example request:
GET https://exampleshop.api.myshoprenter.hu/billing/recurringCharges/12

Response:

```javascript
{
    "planId": 1,
        "billingCycleLength": 1,
        "billingCycleCount": 12,
        "expirationDate": null,
        "trialDays": 10,
        "id": 12,
        "name": "ACME application Gold package",
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

## Termination of Recurring Charge

Developers have the option to stop the Recurring Charge from running, thus closing the payment cycle.
Simply, a DELETE HTTP request with the recurring charge ID must be sent to the entry point described above.

DELETE https://<shop_name>.api.myshoprenter.hu/billing/recurringCharges/<recurring_charge_id>

## Usage

It is exactly the same as using One Time Payment. It differs only in the handling within the system.

## Operation by example
I would like to sell my application on a monthly fee plan. I want to assign 3 types of monthly fee packages to this:
Bronze, Silver, Gold.
This means 3 different payment plans with different names, prices and possibly billing periods.

After logging in, you can create the plans on the billing.shoprenter.hu/plans/create link.

I would like to make the Bronze package a monthly fee, I will give it to you for a period of one year for HUF 10,000 net, it is called "Bronze package of my application".
So my monthly premium Bronze package should look like this:

- Payment plan Name: "Bronze package of my application"
- Length of payment cycles (in months): 1
- Number of payment cycles (infinite if left blank): 12
- Payment plan net price in HUF: 10,000

So, if the store owner subscribes, he pays a net amount of HUF 10,000 per month (billingCycleLength: 1) and this charge is made 12 times (billingCycleCount: 12).

In summary: the shop owner pays HUF 10,000 net per month for the application (billingCycleLength * billingCycleCount).

**Attention**: If the "Number of Payment Cycles" field is left blank, the Recurring Payment made on the basis of this payment plan will never expire.

### Error handling
If an error occurs during the transaction that affects the customer's card data, e.g. expired bank card, the Recurring Charge status changes to FROZEN status. From then on, the system tries to carry out the given repeated fee collection for **15 days**.
If it is not possible to continue collecting the fee from now on, the system will set the given Recurring Charge to the status CANCELED.

Of course, here too, the application is notified of all errors via the notificationUrl.

## Flow chart

![One Time Charge](../image/recurring-charge-flow.png)

## Trial Recurring Charge

### Positive Trial Recurring Charge

The owner of the app can take advantage of the opportunity to provide all or only some of the functionality of the app to the prospective customer of the app for free in the form of a trial period for a specific period, e.g. 30 days.
Let's say that the user of the app decides during the trial period that the app is valuable to him and therefore subscribes, but he still wants to use the remaining 20 days of the free trial period.
In order for the subscription to take place, but only for the date 20 days later to appear on the invoice, and for subsequent deductions to be made depending on this, we must create the subscription using the Payment API by passing the remaining 20 days to the **trialDays property .**

#### Example

<table>
    <tr>
        <td>Application installation date</td>
        <td><strong>2020-09-01</strong></td>
    </tr>
    <tr>
        <td>Number of free trial days offered</td>
        <td><strong>30</strong></td>
    </tr>
    <tr>
        <td>Subscription start date</td>
        <td><strong>2020-09-10</strong></td>
    </tr>
    <tr>
        <td>Number of free days remaining after subscription</td>
        <td><strong>20</strong></td>
    </tr>
    <tr>
        <td>Subscription cycle length in days</td>
        <td><strong>30</strong></td>
    </tr>
    <tr>
        <td>Date appearing on the invoice issued for the first subscription period</td>
        <td><strong>2020-10-01 - 2020-10-30</strong></td>
    </tr>
</table>

### Negative Trial Recurring Charge

In order to understand the negative trial-period recurring fee payment, we need to forget a little to what we read about using the positive recurring fee payment above.
The negative trial period recurring fee payment is a tool for those **active subscribers** who have used the app until now, but before using the Payment API, fees were requested from them and invoices were issued in a different way.
In order to now be able to use the Payment API to request the fee for the already running period and issue an invoice, a subscription must be created that starts on a date in the past. This can be done by specifying the **trialDays property with a negative value.**

For example, if the subscription has been running for 24 days in the app owner's system and you want to switch to the Payment API system, you must create the subscription by specifying -24 for the **trialDays property**.

#### Example

<table>
    <tr>
        <td>Start of a new subscription cycle in the app owner's system</td>
        <td><strong>2020-09-01</strong></td>
    </tr>
    <tr>
        <td>Subscription cycle length in days</td>
        <td><strong>90</strong></td>
    </tr>
    <tr>
        <td>Subscription start date in the Payment API system</td>
        <td><strong>2020-09-24</strong></td>
    </tr>
    <tr>
        <td>This number of days must be backdated for invoicing</td>
        <td><strong>-24</strong></td>
    </tr>
    <tr>
        <td>Date appearing on the invoice issued for the first subscription period</td>
        <td><strong>2020-09-01 - 2020-11-30</strong></td>
    </tr>
</table>

**IMPORTANT:** In the case of negative trial period recurring fee payments, the absolute value of trialDays cannot be greater than the value of billingCycleLength expressed in days, otherwise an error will be thrown. If, for example, the length of a subscription cycle is 120 days (billingCycleLength = 4), then trialDays cannot be smaller than -120, i.e. cannot be -121, -122...etc. There is no such restriction for recurring fee payments with a positive trial period.
