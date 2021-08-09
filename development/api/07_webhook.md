# WebHook automatizmus

A WebHook egy olyan automatikus üzenet a webáruháztól egy külső rendszer felé, amely olyan események hatására váltódhat ki, mint például egy rendelés feladása vagy egy rendelés állapotának megváltozása.
A [WebHook Resource](/api/webhook.md) segítségével ilyen automatizmusokat hozhatunk létre API-n keresztül. A webhookkal küldött adat formátuma lehet XML vagy JSON. A külső rendszer lehet akár egy ERP rendszer vagy egy számlázó, de számos további felhasználási módja lehetséges.  

## Tulajdonságok
A [WebHook Resource](/api/webhook.md) az alábbi tulajdonságokkal rendelkezik
- **Megnevezés (label)**: Az értesítés belső azonosítására szolgál, az üzenetben nem lesz látható az itt megadott név.
- **Esemény (event)**: Az általunk kiválasztott esemény típusa, amely az alábbi lehet:
    - **Új rendelés feladás (order_confirm)**: Olyan üzenetet küldhetünk, melynek kiváltó eseménye egy megrendelés. Ezt például használhatjuk arra, hogy vevőinktől véleményeket kérjük a megrendelt termékekre vonatkozóan.
    - **Rendelés állapot váltás (order_status_change )**: Amennyiben a rendelések státuszának változásáról szeretnénk értesíteni az ügyfeleinket vagy kollégáinkat, úgy érdemes ezt a menüpontot  is használni. Illetve ugyanígy használhatjuk ezt a kiváltó eseményt a vevőcsoportok kapcsán is, amikor egy rendelés állapotának változását a vevőcsoportokban történő mozgatás követ.
- **Státusz (status)**: Itt lehet engedélyezni, vagy letiltani az értesítést. Értékei:
    - **0** - Letiltott
    - **1** - Engedélyezett
- **Paraméterek (webHookParameters)**: A paraméterek segítségével beállítható, hogy milyen formátumban (type) vagy hova (url) menjen ki a webhook. A paramétereket egy tömbben tárolt objectként kell átadni. Paraméterei:
    - **Formátum (type)**: json vagy xml
    - **Url (url)**
- **Időzítés (webHookDelay)**: Az időzítés segítéségvel beállítható, hogy a kiváltó eseményt követően mikor történjen meg az értesítés, azaz menjen ki a webhook. Amennyiben ez az érték nincs megadva úgy a kiküldés azonnali. Paraméterei:
    - **Késletetés mennyisége (delay)**: pl: 10
    - **Késleltetés mértékegysége (delayUnit)**: nap (day) vagy óra (hour)

Konkrét példa POST kérésre JSON formátumban:
```json
{
    "label": "teszt webhook",
    "event": "order_confirm",
    "status": 1,
    "webHookParameters": [
        {
            "type": "json",
            "url": "http:\/\/shoprenter.hu\n"
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

A rendelésről kiküldött webhook értékeinek a jelentése.

|Kulcs|Érték|
|-----|-----|
|storeName|Bolt neve|
|innerId|Rendelés azonosító|
|innerResourceId|Rendelés resource azonosító|
|outerResourceId|Rendelés külső resource azonosító|
|firstname|Vevő keresztneve|
|lastname|Vevő vezetékneve|
|phone|Tefonszám|
|fax|Fax|
|email|Email cím|
|cart_token|Cart token|
|shippingFirstname|Szállítási cím keresztneve|
|shippingLastname|Szállítási cím vezetékneve|
|shippingCompany|Szállítási cím cégneve|
|shippingAddress1|Szállítási cím 1 utcája, házszáma|
|shippingAddress2|Szállítási cím 2 utcája, házszáma|
|shippingCity|Szállítási cím városa|
|shippingCountryName|Szállítási cím országának neve|
|shippingZoneName|Szállítási cím megyéjének neve|
|shippingPostcode|Szállítási cím irányítószáma|
|shippingMethodName|Szállítási mód típusa|
|shippingInnerResourceId|Szállítási mód resource azonosítója|
|shippingNetPrice|Szállítási mód nettó költsége|
|shippingGrossPrice|Szállítási mód bruttó költsége|
|paymentFirstname|Számlázási cím keresztneve|
|paymentLastname|Számlázási cím vezetékneve|
|paymentCompany|Számlázási cím cégneve|
|paymentAddress1|Számlázási cím 1 utcája, házszáma|
|paymentAddress2|Számlázási cím 2 utcája, házszáma|
|paymentCity|Számlázási cím városa|
|paymentCountryName|Számlázási cím országának neve|
|paymentPostcode|Számlázási cím irányítószáma|
|paymentTaxnumber|Számlázási cím adószáma|
|paymentZoneName|Számlázási cím megyéjének neve|
|paymentMethodName|Fizetési mód neve|
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

|Kulcs|Érték|
|-----|-----|
|innerId|Termék azonosító|
|innerResourceId|Termék resource azonosító|
|name|Név|
|sku|Cikkszám|
|price|Nettóérték|
|currency|Pénznem|
|taxRate|ÁFA kulcs|
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
            "firstname":"Teszt",
            "lastname":"P\u00e9ter",
            "phone":"+36304573549",
            "fax":"",
            "email":"pterballa@gmail.com",
            "cart_token":"cart",
            "shippingFirstname":"Teszt",
            "shippingLastname":"P\u00e9ter",
            "shippingCompany":"",
            "shippingAddress1":"Teszt utca 5",
            "shippingAddress2":"",
            "shippingCity":"Debrecen",
            "shippingCountryName":"Magyarorsz\u00e1g",
            "shippingZoneName":"Hajd\u00fa-Bihar",
            "shippingPostcode":"4033",
            "paymentFirstname":"Teszt",
            "paymentLastname":"P\u00e9ter",
            "paymentCompany":"",
            "paymentAddress1":"Teszt utca 5",
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
                     "name":"Teszt term\u00e9k akci\u00f3hoz",
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

## További példák

- [**"Új rendelés feladás" webhook működése**](../development/api-examples/06_webhook.md)