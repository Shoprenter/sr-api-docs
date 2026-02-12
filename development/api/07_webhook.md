# WebHook automation

Webhook is an automatic message from the webshop towards an external system, that may be triggered by events such as placing an order, changing of the order status, newsletter subscription, unsubscribing from a newsletter, or data modification of a newsletter subscriber.
With the help of [WebHook Resource](/api/webhook.md) we can create such automations via API. The type of data sent by webhooks can be XML or JSON. The external system can be an ERP or an invoicing system, but several additional uses are possible.

## Properties
[WebHook Resource](/api/webhook.md) has the below properties
- **label**: Serves the internal identification of the notification, the name entered here will not be visible in the message.
- **event**: The type of the selected event, which can be the following:
  - **Order_confirm**: We can send a message, that is triggered by an order. We can use this, for example, to ask customers on their opinions on the ordered products.
  - **order_status_change**: If we would like to inform customers or colleagues on the change of order status, it is recommended to use this option. And we can use this trigger event in the same way in connection with customer groups as well, when the status change of an order is followed by movement in the customer groups.
  - **newsletter_subscribe**: When a new subscription to the newsletter occurs.
  - **newsletter_unsubscribe**: When someone unsubscribes from the newsletter.
  - **newsletter_update_subscriber**: When someone changes their data used for newsletter subscription.
  - **abandoned_cart**: When a visitor abandons their cart.
- **status**: Here we can enable or disable the notification. Values:
  - **0** - Disabled
  - **1** - Enabled
- **webHookParameters**: Parameters can be used to set the type or the url where the webhook should be sent. Parameters should be sent as an object stored in a batch.
  Parameters:
  - **type**: json or xml
  - **Url**
- **webHookDelay**: Delay can be used to set when the webhook notification is being sent after the triggering event. If this value is not specified, sending is immediate.
  Parameters:
  - **delay**: e.g.: 10
  - **delayUnit**: day or hour

Concrete example for a  JSON type POST request:
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

## List of data that can be sent

### Fields of events related to the order

Meaning of the fields of the sent webhook.

|Key|Value|
|-----|-----|
|storeName|The name of the store|
|innerId|ID of the order|
|innerResourceId|Internal ID of the order resource|
|outerResourceId|External ID of the order resource|
|firstname|first name of the customer|
|lastname|last name of the customer|
|phone|phone number|
|fax|Fax|
|email|E-mail address|
|cart_token|Cart token|
|shippingFirstname|First name for shipping address|
|shippingLastname|Last name for shipping address|
|shippingCompany|Company name of shipping address|
|shippingAddress1|Street and number of shipping address 1|
|shippingAddress2|Street and number of shipping address 2|
|shippingCity|City of shipping address|
|shippingCountryName|Country of shipping address|
|shippingZoneName|County of shipping address|
|shippingPostcode|Postal code of shipping address|
|shippingMethodName|Shipping method|
|shippingInnerResourceId|Resource ID of shipping method|
|shippingNetPrice|Net price of shipping method|
|shippingGrossPrice|Gross price of shipping method|
|paymentFirstname|First name for billing address|
|paymentLastname|Last name for billing address|
|paymentCompany|Company name of billing address|
|paymentAddress1|Street and number of billing address 1|
|paymentAddress2|Street and number of billing address 2|
|paymentCity|City of billing address|
|paymentCountryName|Country of billing address|
|paymentPostcode|Postal code of billing address|
|paymentTaxnumber|Tax number of billing address|
|paymentZoneName|County of billing address|
|paymentMethodName|Name of payment method|
|paymentNetPrice|Net price of payment fee|
|paymentGrossPrice|Gross price of payment fee|
|couponCode|Coupon code|
|couponGrossPrice|Gross value of coupon|
|languageId|ID of language|
|languageCode|Code of language|
|comment|Order comment|
|total|Net value of the order|
|totalGross|Total gross value of the order|
|taxPrice|Value of VAT included in the order|
|currency|Code of currency|
|orderHistory|Status of the order|
|orderProducts|Block of ordered products|

Information on the ordered products can be found in the **orderProducts** block, meanings are the below:

|Key|Value|
|-----|-----|
|innerId|Product ID|
|innerResourceId|ID of product resource|
|name|Name|
|sku|Article number|
|price|Net value|
|currency|Currency|
|taxRate|VAT rate|
|quantity|Quatity|
|image|Image link|
|category|Product category|
|volume|height, length, width, unit of measure|
|weight|Weight|

Sample webhook:

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
            "lastname":"Peter",
            "phone":"+36304573549",
            "fax":"",
            "email":"pterballa@gmail.com",
            "cart_token":"cart",
            "shippingFirstname":"Test",
            "shippingLastname":"Peter",
            "shippingCompany":"",
            "shippingAddress1":"Test utca 5",
            "shippingAddress2":"",
            "shippingCity":"Debrecen",
            "shippingCountryName":"Hungary",
            "shippingZoneName":"Hajdú-Bihar",
            "shippingPostcode":"4033",
            "paymentFirstname":"Test",
            "paymentLastname":"Peter",
            "paymentCompany":"",
            "paymentAddress1":"Test utca 5",
            "paymentAddress2":"",
            "paymentCity":"Debrecen",
            "paymentCountryName":"Hungary",
            "paymentZoneName":"Hajdú-Bihar",
            "shippingMethodName":"Home delivery with courier",
            "shippingNetPrice":970.0714,
            "shippingGrossPrice":"1006",
            "shippingInnerResourceId":"shippingModeExtend\/c2hpcHBpbmdNb2RlLWlkPTE4",
            "paymentMethodName":"Cash on delivery",
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
               "statusText":"Pending",
               "comment":"",
               "dateAdded":"2025-12-01 20:57:40"
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
                     "category":"Flovers, Tulips",
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
                     "name":"Test product for sale",
                     "sku":"TTA1234",
                     "price":"9000",
                     "currency":"HUF",
                     "taxRate":"0.0000",
                     "quantity":"1",
                     "image":"https:\/\/shopname.api.myshoprenter.hu\/custom\/demo\/image\/no_image.jpg",
                     "category":"FISHER-PRICE toy",
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

### Fields of events related to newsletter

Meaning of the fields of webhook related to newsletter

| Key                    | Value                                      |
|---------------------------|---------------------------------------------|
| subscriber_id             | ID of the subscriber                     |
| subscriber_firstname      | First name of the subscriber                                 |
| subscriber_lastname       | Last name of the subscriber                                |
| subscriber_email          | E-mail address of the subscriber                                |
| subscriber_phone          | Phone number of subscriber                                |
| subscriber_status         | Status                                    |
| subscriber_language       | Language ID of subscription        |
| subscriber_hash           | hash for subscription, unsubscription |
| subscriber_subscribe_date | Date of subscription                         |

Sample webhook:

```json
{
  "newsletter": {
    "subscriber": [
      {
        "id": "1",
        "firstname": "Test",
        "lastname": "Peter",
        "email": "Test@shoprenter.hu",
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

## Further examples

- [**"Order submission" operation of webhook**](../api-examples/06_webhook.md)
