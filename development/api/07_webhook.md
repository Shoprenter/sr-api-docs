# WebHook Automation

A WebHook is an automatic message from an online store to an external system triggered by events such as placing an order, changing the status of an order, newsletter subscription, newsletter unsubscription, or newsletter subscriber data modification.

Using the [WebHook Resource](/api/webhook.md), you can create such automations via an API. The data format sent with the webhook can be either XML or JSON. The external system can be an ERP system or an invoicing system, but there are many other possible use cases.

## Properties
The [WebHook Resource](/api/webhook.md) has the following properties:
- **Label**: Used for internal identification of the notification; the name provided here will not be visible in the message.
- **Event**: The type of event selected by us, which can be:
  - **New Order Confirmation (order_confirm)**: You can send a message triggered by a new order event. For example, you can use this to request feedback from customers about the ordered products.
  - **Order Status Change (order_status_change)**: If you want to notify customers or colleagues about changes in order status, it's a good idea to use this option. You can also use this event for customer groups when moving an order's status change within customer groups.
  - **Newsletter Subscribe (newsletter_subscribe)**: When a new subscription is made to the newsletter.
  - **Newsletter Unsubscribe (newsletter_unsubscribe)**: When someone unsubscribes from the newsletter.
  - **Newsletter Update Subscriber Data (newsletter_update_subscriber)**: When someone updates their data used for newsletter subscriptions.
- **Status**: Here, you can enable or disable the notification. Values:
  - **0** - Disabled
  - **1** - Enabled
- **Parameters (webHookParameters)**: Using parameters, you can configure the format (type) and destination (url) of the webhook. The parameters should be passed as an array of objects. Parameters include:
  - **Format (type)**: json or xml
  - **URL (url)**
- **Timing (webHookDelay)**: Timing can be set to determine when the notification, i.e., the webhook, should be sent after the triggering event. If this value is not specified, the notification will be sent immediately. Parameters include:
  - **Delay Amount (delay)**: e.g., 10
  - **Delay Unit (delayUnit)**: day or hour

An example of a POST request in JSON format:
```json
{
    "label": "test webhook",
    "event": "order_confirm",
    "status": 1,
    "webHookParameters": [
        {
            "type": "json",
            "url": "http://shoprenter.hu"
        }
    ],
    "webHookDelay": [
        {
            "delay": 10,
            "delayUnit": "day"
        }
    ]
}
```

## Elküldhető adatok listája

### A megrendeléshez kapcsolódó események mezői

A rendelésről kiküldött webhook mezőinek a jelentése.

|Key|Value|
|-----|-----|
|storeName|Bolt neve|
|innerId|Rendelés azonosító|
|innerResourceId|Rendelés resource azonosító|
|outerResourceId|Rendelés külső resource azonosító|
|firstname|Vevő keresztneve|
|lastname|Vevő vezetékneve|
|phone|Tefonszám|
|fax|Fax|
|email|Email title|
|cart_token|Cart token|
|shippingFirstname|Shipping address keresztneve|
|shippingLastname|Shipping address vezetékneve|
|shippingCompany|Shipping address cégneve|
|shippingAddress1|Shipping address 1 utcája, házszáma|
|shippingAddress2|Shipping address 2 utcája, házszáma|
|shippingCity|Shipping address városa|
|shippingCountryName|Shipping address országának neve|
|shippingZoneName|Shipping address megyéjének neve|
|shippingPostcode|Shipping address Zipcodea|
|shippingMethodName|Szállítási mód típusa|
|shippingInnerResourceId|Szállítási mód resource azonosítója|
|shippingNetPrice|Szállítási mód nettó költsége|
|shippingGrossPrice|Szállítási mód bruttó költsége|
|paymentFirstname|Billing address keresztneve|
|paymentLastname|Billing address vezetékneve|
|paymentCompany|Billing address cégneve|
|paymentAddress1|Billing address 1 utcája, házszáma|
|paymentAddress2|Billing address 2 utcája, házszáma|
|paymentCity|Billing address városa|
|paymentCountryName|Billing address országának neve|
|paymentPostcode|Billing address Zipcodea|
|paymentTaxnumber|Billing address adószáma|
|paymentZoneName|Billing address megyéjének neve|
|paymentMethodName|Payment method neve|
|paymentNetPrice|Fizetési illeték nettó költsége|
|paymentGrossPrice|Fizetési illeték bruttó költsége|
|couponCode|Kupon kódja|
|couponGrossPrice|Kupon bruttó összege|
|languageId|Nyelv azonosítója|
|languageCode|Nyelv kódja|
|comment|Rendelés megjegyzése|
|total|Rendelés nettó összege|
|totalGross|Rendelés bruttó végösszege|
|taxPrice|Rendelés áfa tartalma|
|orderHistory|Rendelés állapota|
|currency|Rendelés pénznemének kódja|
|orderHistory|Rendelés állapota|
|orderProducts|Rendelt termékek tömbje|

A rendelt termékekkel kapcsolatos információk az **orderProducts** tömbben találhatók, melynek jelentései az alábbiak.

|Key|Value|
|-----|-----|
|innerId|Termék azonosító|
|innerResourceId|Termék resource azonosító|
|name|Name|
|sku|Cikkszám|
|price|Nettóérték|
|currency|Pénznem|
|taxRate|VAT kulcs|
|quantity|Mennyiség|
|image|Kép link|
|category|Termékkategória|
|volume|Méretek: height (magasság), hosszúság (length), szélesség (width), mértékegység (volumeUnit)|
|weight|Súly|

Példa webhook:

```json
{  
   "orders":{  
      "order":[  
         {  
            "storeName":"demo",
            "innerId":"190",
            "innerResourceId":"orders\/b3JkZXItb3JkZXJfaWQ9MTkw",
            "outerResourceId":"",
            "firstname":"Test",
            "lastname":"P\u00e9ter",
            "phone":"+36304573549",
            "fax":"",
            "email":"pterballa@gmail.com",
            "cart_token":"cart",
            "shippingFirstname":"Test",
            "shippingLastname":"P\u00e9ter",
            "shippingCompany":"",
            "shippingAddress1":"Test utca 5",
            "shippingAddress2":"",
            "shippingCity":"Debrecen",
            "shippingCountryName":"Magyarorsz\u00e1g",
            "shippingZoneName":"Hajd\u00fa-Bihar",
            "shippingPostcode":"4033",
            "paymentFirstname":"Test",
            "paymentLastname":"P\u00e9ter",
            "paymentCompany":"",
            "paymentAddress1":"Test utca 5",
            "paymentAddress2":"",
            "paymentCity":"Debrecen",
            "paymentCountryName":"Magyarorsz\u00e1g",
            "paymentZoneName":"Hajd\u00fa-Bihar",
            "shippingMethodName":"H\u00e1zhozsz\u00e1ll\u00edt\u00e1s fut\u00e1rszolg\u00e1lattal",
            "shippingNetPrice":970.0714,
            "shippingGrossPrice":"1006",
            "shippingInnerResourceId":"shippingModeExtend\/c2hpcHBpbmdNb2RlLWlkPTE4",
            "paymentMethodName":"Ut\u00e1nv\u00e9tel",
            "paymentNetPrice":0,
            "paymentGrossPrice":0,
            "couponCode":"",
            "couponGrossPrice":null,
            "languageId":"1",
            "languageCode":"hu",
            "comment":"",
            "total":"9945",
            "totalGross":"11206",
            "taxPrice":"255",
            "currency":"HUF",
            "paymentPostcode":"4033",
            "paymentTaxnumber":"",
            "orderHistory":{  
               "status":"1",
               "statusText":"F\u00fcgg\u0151ben l\u00e9v\u0151",
               "comment":""
            },
            "orderProducts":{  
               "orderProduct":[  
                  {  
                     "innerId":"608",
                     "innerResourceId":"orderProducts\/b3JkZXJQcm9kdWN0LW9yZGVyX3Byb2R1Y3RfaWQ9NjA4",
                     "outerResourceId":"",
                     "name":"30 Multi-Colored Tulips",
                     "sku":"996000004",
                     "price":"945",
                     "currency":"HUF",
                     "taxRate":"27.0000",
                     "quantity":"1",
                     "image":"https:\/\/shopname.api.myshoprenter.hu\/custom\/demo\/image\/data\/product\/PF_11_00000000M232_VA0211_W1_PF.jpg",
                     "category":"Vir\u00e1gok, Tulip\u00e1nok",
                     "volume":{  
                        "height":"0.00",
                        "width":"0.00",
                        "length":"0.00",
                        "volumeUnit":[  
                           {  
                              "unit":"cm",
                              "language":"hu"
                           },
                           {  
                              "unit":"cm",
                              "language":"en"
                           }
                        ]
                     },
                     "weight":{  
                        "weight":"0.00",
                        "weightUnit":[  
                           {  
                              "unit":"kg",
                              "language":"hu"
                           },
                           {  
                              "unit":"kg",
                              "language":"en"
                           }
                        ]
                     }
                  },
                  {  
                     "innerId":"609",
                     "innerResourceId":"orderProducts\/b3JkZXJQcm9kdWN0LW9yZGVyX3Byb2R1Y3RfaWQ9NjA5",
                     "outerResourceId":"",
                     "name":"Test term\u00e9k akci\u00f3hoz",
                     "sku":"TTA1234",
                     "price":"9000",
                     "currency":"HUF",
                     "taxRate":"0.0000",
                     "quantity":"1",
                     "image":"https:\/\/shopname.api.myshoprenter.hu\/custom\/demo\/image\/no_image.jpg",
                     "category":"FISHER-PRICE j\u00e1t\u00e9kok",
                     "volume":{  
                        "height":"0.00",
                        "width":"0.00",
                        "length":"0.00",
                        "volumeUnit":[  
                           {  
                              "unit":"cm",
                              "language":"hu"
                           },
                           {  
                              "unit":"cm",
                              "language":"en"
                           }
                        ]
                     },
                     "weight":{  
                        "weight":"0.00",
                        "weightUnit":[  
                           {  
                              "unit":"kg",
                              "language":"hu"
                           },
                           {  
                              "unit":"kg",
                              "language":"en"
                           }
                        ]
                     }
                  }
               ]
            }
         }
      ]
   }
}
```


### A hírlevélhez kapcsolódó események mezői

A hírlevélhez kapcsolódóan kiküldött webhook mezőinek a jelentése.

| Key                     | Value                                       |
|---------------------------|---------------------------------------------|
| subscriber_id             | Feliratkozó azonosítója                     |
| subscriber_firstname      | Lastname                                  |
| subscriber_lastname       | Firstname                                  |
| subscriber_email          | E-mail title                                  |
| subscriber_phone          | Telefonszám                                 |
| subscriber_status         | Status                                     |
| subscriber_language       | A feliratkozás nyelvének azonosítója        |
| subscriber_hash           | Aktiváláshoz, leiratkozáshoz szükséges hash |
| subscriber_subscribe_date | Feliratkozás dátuma                         |

Példa webhook:

```json
{
  "newsletter": {
    "subscriber": [
      {
        "id": "1",
        "firstname": "Test",
        "lastname": "P\u00e9ter",
        "email": "test@shoprenter.hu",
        "phone": "+36201234567",
        "status": 1,
        "language": "1",
        "hash": "b53807cef8e6582bc95c31f4b5ac17f8",
        "subscribe_date": "2023-01-20 11:11:11"
      }
    ]
  }
}
```

## További példák

- [**"Új rendelés feladás" webhook működése**](../api-examples/06_webhook.md)
