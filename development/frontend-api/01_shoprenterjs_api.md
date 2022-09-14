# ShopRenter.js

Tartalomjegyzék
* [ShopRenter Object](#shoprenter-object)
  * [Properties](#properties)
    * [customer](#customer)
    * [theme](#theme)
    * [shop](#shop)
    * [page](#page)
    * [product](#product)
  * [Events](#events)
    * [onItemAdd](#onitemadd)
    * [onCartUpdate](#oncartupdate)
    * [onItemDelete](#onitemdelete)
    * [onSearchResultViewed](#onsearchresultviewed)
    * [onSubscribedForNewsletter](#onsubscribedfornewsletter)
    * [onCheckoutInitiated](#oncheckoutinitiated)
    * [onCheckoutPaymentInfoAdded](#oncheckoutpaymentinfoadded)
    * [onCheckoutShippingInfoAdded](#oncheckoutshippinginfoadded)
    * [onCheckoutOrderConfirmed](#oncheckoutorderconfirmed)
    * [onCheckoutOrderPaid](#oncheckoutorderpaid)
    * [onCheckoutOrderPaidUnsuccessful](#oncheckoutorderpaidunsuccessful)
    * [onProductPageViewed](#onproductpageviewed)
    * [onMarketingConsentChanged](#onmarketingconsentchanged)
    * [onCustomerRegistered](#oncustomerregistered)
    * [onCustomerLoggedIn](#oncustomerloggedin)
    * [onCustomerUpdated](#oncustomerupdated)
    * [Események használata](#esemenyek-hasznalata)

## ShopRenter Object
A frontendre beépülő alkalmazásoknál szükség lehet olyan adatokra, melyek elengedhetetlenek az alkalmazás üzleti logikájához.
A ShopRenter globális JavaScript objektum frontenden elérhető minden oldalbetöltődésnél, amely webshop adatokat tároló objektumokat és eseményfigyelőket tartalmaz.

## Properties

### customer
A bolt frontendjének minden oldalán lekérhető az aktuális Vevő néhány adata,
melyet ShopRenter javascript objektum **customer** property-je tartalmazza. 
Az objektum szenzitív adatokat nem tartalmaz, amely alapján azonosítható lenne a Vevő.

Példa:
```javascript
console.log(ShopRenter.customer);
```

Kimenet:
```javascript
{
    userId: 0, 
    userGroupId: 8, 
    customerGroupTaxMode: "gross", 
    customerGroupPriceMode: "gross_net_tax",
    email: "test@test.com",
    name: {
        firstName: "First name",
        lastName: "Last name"
    }
}
```

Egyes mezők jelentése:
<table> 
    <tr>
        <th>property</th>
        <th>jelentés</th>
    </tr>
    <tr>
        <td>userId</td>
        <td>A Vevő belső id-ja. Ha 0, akkor a Vevő nem regisztrált felhasználó</td>
    </tr>
    <tr>
        <td>userGroupId</td>
        <td>A vevő vásárlói csoportjának azonosítója</td>
    </tr>  
    <tr>
        <td>customerGroupTaxMode</td>
        <td>
           Megadja az aktuális Vevő vásárlói csoportja szerint, hogy a <strong>termékoldalon kívül</strong>, milyen módon jelenjen meg az ár
           <ul>
              <li><strong>gross</strong>: Bruttó ár</li>
              <li><strong>net</strong>: Nettó ár</li>
           </ul>
        </td>
    </tr> 
    <tr>
        <td>customerGroupPriceMode</td>
        <td>
           Megadja az aktuális Vevő vásárlói csoportja szerint, hogy a <strong>termékoldalon</strong>, milyen módon jelenjen meg az ár
              <li><strong>only_gross</strong>: Csak a bruttó ár kiírása</li>
              <li><strong>gross_net_tax</strong>: Bruttó ár, mögötte zárójelben a nettó + ÁFA kiírása</li>
              <li><strong>only_net</strong>: Csak a nettó ár kiírása</li>
              <li><strong>net_tax</strong>: A nettó ár és mögötte a + ÁFA kiírása</li>
              <li><strong>net_tax_gross</strong>: A nettó ár és mögötte a + ÁFA kiírása, illetve zárójelben a bruttó ár kiírása</li>
        </td>
    </tr>
    <tr>
        <td>email</td>
        <td>A vevő e-mail címe</td>
    </tr>
    <tr>
        <td>name</td>
        <td>A name objektum tartalmazza a vevő vezeték, illetve keresztnevét</td>
    </tr>
</table>

### theme
A bolt frontendjének minden oldalán lekérhető az aktuális sablon néhány adata,
melyet ShopRenter javascript objektum **theme** property-je tartalmazza. 

Példa:
```javascript
console.log(ShopRenter.theme);
```

Kimenet:
```javascript
{
    name: "tokyo_glacierblue", 
    family: "tokyo", 
    parent: "bootstrap"
}
```

Egyes mezők jelentése:

<table> 
    <tr>
        <th>property</th>
        <th>jelentés</th>
    </tr>
    <tr>
        <td>name</td>
        <td>A sablon neve</td>
    </tr>
    <tr>
        <td>family</td>
        <td>A sablon család neve, amelybe az aktuális sablon tartozik</td>
    </tr>  
    <tr>
        <td>parent</td>
        <td>A szülő sablon neve</td>
    </tr>
</table>

### shop
A bolt frontendjének minden oldalán lekérhető a bolt fontosabb adata,
melyet ShopRenter javascript objektum **theme** property-je tartalmazza. 

Példa:
```javascript
console.log(ShopRenter.shop);
```

Kimenet:
```javascript
{
    name: "tokyo", 
    locale: "hu", 
    currency: {
        code: "HUF", 
        rate: 1
    }, 
    domain: "tokyo.shoprenter.hu"
}
```

Egyes mezők jelentése:
<table> 
    <tr>
        <th>property</th>
        <th>jelentés</th>
    </tr>
    <tr>
        <td>name</td>
        <td>A bolt neve</td>
    </tr>
    <tr>
        <td>locale</td>
        <td>A bolt aktuális frontend nyelve</td>
    </tr>  
    <tr>
        <td>currency</td>
        <td>
           A bolt aktuális valutájára vonatkozó adatok:
           <ul>
              <li><strong>code</strong>: A valuta nyelvi kódja</li>
              <li><strong>rate</strong>: A bolt alapértelmezett valutájához mérten használt pénznem váltó érték.
                  Pl.: 1-et kell elosztanunk az adott pénznem árfolyamának értékével, például ha a valuta árfolyama 195 Ft, akkor az értékmező: 1/195, tehát 0,005128 lesz a rate
              </li>
           </ul>
        </td>
    </tr>
    <tr>
        <td>domain</td>
        <td>
           A bolt rendszer domain-ja
        </td>
    </tr>
</table>

### page
A ShopRenter objektum **page** property tartalmazza az aktuális oldal adatait.

Példa:
```javascript
console.log(ShopRenter.page);
```

Kimenet:
```javascript
{
    route: "product/list"
}
```

Egyes mezők jelentése:
<table> 
    <tr>
        <th>property</th>
        <th>jelentés</th>
    </tr>
    <tr>
        <td>route</td>
        <td>Az adott aloldal route értéke</td>
    </tr>
</table>

### product
A ShopRenter objektum **product** property tartalmazza a termékhez tartozó információkat. Ez a property csak termékoldalon érhető el!

Példa:
```javascript
console.log(ShopRenter.product);
```

Kimenet:
```javascript
{
    id: "201",
    sku: "ASDF201",
    parent: {
        id: "200",
        sku: "ASDF200"
    }
}
```

Egyes mezők jelentése:
<table> 
    <tr>
        <th>property</th>
        <th>jelentés</th>
    </tr>
    <tr>
        <td>id</td>
        <td>Az aktuális termék azonosítója</td>
    </tr>
    <tr>
        <td>sku</td>
        <td>Az aktuális termék cikkszáma</td>
    </tr>
    <tr>
        <td>parent.id</td>
        <td>Az szülő termék azonosítója</td>
    </tr>
    <tr>
        <td>parent.sku</td>
        <td>Az szülő termék cikkszáma</td>
    </tr>
</table>

## Events
A ShopRenter egyes kosár és vásárlótól származó események bekövetkezésekor kiváltanak olyan javascript eseményeket, melyre feliratkozva, azok kiváltódása után, további viselkedést valósíthatunk meg.

Az új, hozzáadott eseményfigyelők (Event Listener) megkapják az eseményhez tartozó adatokat.

A rendszer az eseményt egy CustomEvent objektumba adja vissza, melynek a **detail** property-je tartalmazza az adott eseménnyel kapcsolatos adatokat.

### onItemAdd
Kosárba helyezés a bolt bármely részéről (modul termékkártya, termékoldal, kategóriaoldal). Megkapja a kosárba helyezett termék adatait.

Példa:
```json
{
    "detail": {
        "cartToken": "27828acb2141b0b16bbfc14358b0cbcd1d26aee0860c5",
        "product": {
            "id": "[367]",
            "sku": 9950000044,
            "price": "18415.00",
            "currency": "HUF",
            "quantity": "1",
            "quantityName": "db",
            "name": "Sztreccs farmer",
            "brand": "Farmer Kft."
        },
        "addedItems": [
          {
            "id": "[532]",
            "sku": "9950000044",
            "price": "18415.00",
            "quantityName": "db",
            "currency": "HUF",
            "quantity": 1,
            "name": "Sztreccs farmer",
            "brand": "Farmer Kft."
          }
        ]
    }
}
```

### onCartUpdate
A kosár módosításakor (termék hozzáadásakor/törlésekor/módosításakor) végbemenő eseményre lehet feliratkozni. A feliratkozott eventlistener paraméterben megkapja a módosított kosár adatait.

Példa:
```json
{
    "detail": {
                "cartToken": "27828acb2141b0b16bbfc14358b0cbcd1d26aee0860c5",
                "products": [
                  {
                    "0": "",
                    "productId": 318,
                    "sku": "TTA1234",
                    "minimumPlural": "0",
                    "isPresent": false,
                    "shippingTime": 1565965848,
                    "isParentOrChild": false,
                    "image": "",
                    "cartKey": "S7QytqrOtDKwzrQyNrQAkoYgbAQkjKwTrQytqoutzK2U8gtKMvPzipWAQgZW1bW1tQA=",
                    "download": [],
                    "cartItemType": "Product",
                    "name": "Teszt termék akcióhoz",
                    "thumbWidth": "60",
                    "thumbHeight": "60",
                    "imageUrl": "https://demo.shoprenter.hu/custom/demo/image/cache/w60h60/no_image.jpg?lastmod=0.1560858478",
                    "option": [],
                    "quantity": 12,
                    "quantityName": "db",
                    "minimum": "1",
                    "maximum": "0",
                    "summedQuantity": 48,
                    "step": 1,
                    "stock": true,
                    "priceNumber": 10000,
                    "totalNumber": 120000,
                    "totalOriginalNumber": 120000,
                    "originalPriceNumber": 10000,
                    "isSpecial": false,
                    "href": "https://demo.shoprenter.hu/teszt_termek_akciohoz_318",
                    "values": [],
                    "displaySpecialPrice": false,
                    "isModified": false,
                    "customerMessage": null,
                    "needToShip": true,
                    "weight": 0,
                    "weightClass": "kg",
                    "isMaximumQuantityReached": false
                  },
                  {
                    "0": "",
                    "productId": 317,
                    "sku": "TESZTOPC1234",
                    "minimumPlural": "0",
                    "isPresent": false,
                    "shippingTime": 1565965848,
                    "isParentOrChild": false,
                    "image": "",
                    "cartKey": "S7QytqrOtDKwzrQyNjQHkoZQbGSdaGVoVV1sZW6llF9QkpmfV6wEFDKwqq6trQUA",
                    "download": [],
                    "cartItemType": "Product",
                    "name": "Teszt opciós termék",
                    "thumbWidth": "60",
                    "thumbHeight": "60",
                    "imageUrl": "https://demo.shoprenter.hu/custom/demo/image/cache/w60h60/no_image.jpg?lastmod=0.1560858478",
                    "option": [],
                    "quantity": 1,
                    "quantityName": "db",
                    "minimum": "1",
                    "maximum": "0",
                    "summedQuantity": 1228,
                    "step": 1,
                    "stock": true,
                    "priceNumber": 10000,
                    "totalNumber": 10000,
                    "totalOriginalNumber": 10000,
                    "originalPriceNumber": 10000,
                    "isSpecial": false,
                    "href": "https://demo.shoprenter.hu/teszt_opcios_termek_317",
                    "values": [],
                    "displaySpecialPrice": false,
                    "isModified": false,
                    "customerMessage": null,
                    "needToShip": true,
                    "weight": 0,
                    "weightClass": "kg",
                    "isMaximumQuantityReached": false
                  }
                ],
                "updatedItems": [
                  {
                    "sku": "TTA1234",
                    "name": "Teszt termék akcióhoz",
                    "quantityName": "db",
                    "oldQuantity": 11,
                    "newQuantity": 12,
                    "grossUnitPrice": 10000,
                    "brand": "Teszt Kft."
                  }
                ]
              }
}
```

### onItemDelete
A kosárból való törlés eseményre lehet feliratkozni. A feliratkozott eventlistener paraméterben megkapja a törlés utáni kosár adatait.

Példa:
```json
{
    "detail": {
                "cartToken": "27828acb2141b0b16bbfc14358b0cbcd1d26aee0860c5",
                "products": [
                  {
                    "0": "",
                    "productId": 318,
                    "sku": "TTA1234",
                    "minimumPlural": "0",
                    "isPresent": false,
                    "shippingTime": 1565965848,
                    "isParentOrChild": false,
                    "image": "",
                    "cartKey": "S7QytqrOtDKwzrQyNrQAkoYgbAQkjKwTrQytqoutzK2U8gtKMvPzipWAQgZW1bW1tQA=",
                    "download": [],
                    "cartItemType": "Product",
                    "name": "Teszt termék akcióhoz",
                    "thumbWidth": "60",
                    "thumbHeight": "60",
                    "imageUrl": "https://demo.shoprenter.hu/custom/demo/image/cache/w60h60/no_image.jpg?lastmod=0.1560858478",
                    "option": [],
                    "quantity": 12,
                    "quantityName": "db",
                    "minimum": "1",
                    "maximum": "0",
                    "summedQuantity": 48,
                    "step": 1,
                    "stock": true,
                    "priceNumber": 10000,
                    "totalNumber": 120000,
                    "totalOriginalNumber": 120000,
                    "originalPriceNumber": 10000,
                    "isSpecial": false,
                    "href": "https://demo.shoprenter.hu/teszt_termek_akciohoz_318",
                    "values": [],
                    "displaySpecialPrice": false,
                    "isModified": false,
                    "customerMessage": null,
                    "needToShip": true,
                    "weight": 0,
                    "weightClass": "kg",
                    "isMaximumQuantityReached": false
                  },
                  {
                    "0": "",
                    "productId": 317,
                    "sku": "TESZTOPC1234",
                    "minimumPlural": "0",
                    "isPresent": false,
                    "shippingTime": 1565965848,
                    "isParentOrChild": false,
                    "image": "",
                    "cartKey": "S7QytqrOtDKwzrQyNjQHkoZQbGSdaGVoVV1sZW6llF9QkpmfV6wEFDKwqq6trQUA",
                    "download": [],
                    "cartItemType": "Product",
                    "name": "Teszt opciós termék",
                    "thumbWidth": "60",
                    "thumbHeight": "60",
                    "imageUrl": "https://demo.shoprenter.hu/custom/demo/image/cache/w60h60/no_image.jpg?lastmod=0.1560858478",
                    "option": [],
                    "quantity": 1,
                    "quantityName": "db",
                    "minimum": "1",
                    "maximum": "0",
                    "summedQuantity": 1228,
                    "step": 1,
                    "stock": true,
                    "priceNumber": 10000,
                    "totalNumber": 10000,
                    "totalOriginalNumber": 10000,
                    "originalPriceNumber": 10000,
                    "isSpecial": false,
                    "href": "https://demo.shoprenter.hu/teszt_opcios_termek_317",
                    "values": [],
                    "displaySpecialPrice": false,
                    "isModified": false,
                    "customerMessage": null,
                    "needToShip": true,
                    "weight": 0,
                    "weightClass": "kg",
                    "isMaximumQuantityReached": false
                  }
                ],
                "removedItems": [
                  {
                    "sku": "kerekparos-cipo",
                    "name": "Kerékpáros cipő",
                    "quantityName": "db",
                    "quantity": 7,
                    "grossUnitPrice": 49990,
                    "grossTotalPrice": 349930,
                    "brand": "Teszt Kft."
                  }
                ]
              }
}
```

### onSearchResultViewed
Termék keresési eredmény megjelenésekor bekövetkező esemény. Fontos, hogy nem a keresés pillanatában, hanem a keresési eredmény megjelenésekor váltódik ki az esemény.

Példa:
```json
{
  "detail": {
    "user": {
      "id": 5,
      "email": "teszt@shoprenter.hu",
      "phoneNumber": "+36201234567",
      "name": {
        "firstName": "TesztVezetéknév",
        "lastName": "TesztKeresztnév"
      },
      "ipAddress": "172.30.128.0",
      "userAgent": "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/104.0.0.0 Safari/537.36"
    },
    "shop": {
      "name": "demo",
      "locale": "hu",
      "currency": {
        "code": "HUF",
        "rate": 1
      },
      "domain": "demo.myshoprenter.hu"
    },
    "event": {
      "id": "1661245666379-2778",
      "time": 1661245666,
      "sourceUrl": "https://demo.myshoprenter.hu/index.php?route=product/list&keyword=notebook&description=0",
      "name": "SearchResultViewed",
      "keyword": "notebook"
    }
  }
}
```

### onSubscribedForNewsletter
Hírlevél feliratkozáskor bekövetkező esemény.

Példa:
```json
{
  "detail": {
    "user": {
      "id": 5,
      "email": "teszt@shoprenter.hu",
      "phoneNumber": "+36201234567",
      "name": {
        "firstName": "TesztVezetéknév",
        "lastName": "TesztKeresztnév"
      },
      "ipAddress": "172.30.128.0",
      "userAgent": "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/104.0.0.0 Safari/537.36"
    },
    "shop": {
      "name": "demo",
      "locale": "hu",
      "currency": {
        "code": "HUF",
        "rate": 1
      },
      "domain": "demo.myshoprenter.hu"
    },
    "event": {
      "id": "1661253893316-900",
      "time": 1661253893,
      "sourceUrl": "https://demo.myshoprenter.hu/index.php?route=account/account",
      "name": "SubscribedForNewsletter"
    }
  }
}
```

### onCheckoutInitiated
Pénztár folyamat elkezdésekor bekövetkező esemény.

Példa:
```json
{
  "detail": {
    "user": {
      "id": 5,
      "email": "teszt@shoprenter.hu",
      "phoneNumber": "+36201234567",
      "name": {
        "firstName": "TesztVezetéknév",
        "lastName": "TesztKeresztnév"
      },
      "ipAddress": "172.30.128.0",
      "userAgent": "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/104.0.0.0 Safari/537.36"
    },
    "shop": {
      "name": "demo",
      "locale": "hu",
      "currency": {
        "code": "HUF",
        "rate": 1
      },
      "domain": "demo.myshoprenter.hu"
    },
    "event": {
      "id": "1661254177910-3746",
      "time": 1661254177,
      "sourceUrl": "https://demo.myshoprenter.hu/checkout#/customerdata/",
      "name": "CheckoutInitiated"
    },
    "cart": {
      "items": [
        {
          "type": "product",
          "id": 311,
          "sku": "7700000",
          "grossTotalPrice": 7874,
          "grossUnitPrice": 3937,
          "currency": "HUF",
          "quantity": 2,
          "quantityName": "db",
          "name": "Termék 2",
          "brand": "márka"
        },
        {
          "type": "product",
          "id": 306,
          "sku": "6600000",
          "grossTotalPrice": 787.4,
          "grossUnitPrice": 787.4,
          "currency": "HUF",
          "quantity": 1,
          "quantityName": "db",
          "name": "Termék 1",
          "brand": "márka"
        }
      ],
      "paymentMethod": {
        "name": "Barion"
      },
      "shippingMethod": {
        "name": "Személyes átvétel"
      },
      "grossTotalPrice": 8661.4,
      "couponCode": "TEST1234"
    }
  }
}
```

### onCheckoutPaymentInfoAdded
A pénztár folyamatban, sikeres fizetési adatok megadása után bekövetkező esemény.

Példa:
```json
{
  "detail": {
    "user": {
      "id": 5,
      "email": "teszt@shoprenter.hu",
      "phoneNumber": "+36201234567",
      "name": {
        "firstName": "TesztVezetéknév",
        "lastName": "TesztKeresztnév"
      },
      "ipAddress": "172.30.128.0",
      "userAgent": "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/104.0.0.0 Safari/537.36"
    },
    "shop": {
      "name": "demo",
      "locale": "hu",
      "currency": {
        "code": "HUF",
        "rate": 1
      },
      "domain": "demo.myshoprenter.hu"
    },
    "event": {
      "id": "1661254548535-3623",
      "time": 1661254548,
      "sourceUrl": "https://demo.myshoprenter.hu/checkout#/paymentmethod/",
      "name": "CheckoutPaymentInfoAdded"
    },
    "cart": {
      "items": [
        {
          "type": "product",
          "id": 311,
          "sku": "7700000",
          "grossTotalPrice": 7874,
          "grossUnitPrice": 3937,
          "currency": "HUF",
          "quantity": 2,
          "quantityName": "db",
          "name": "Termék 2",
          "brand": "márka"
        },
        {
          "type": "product",
          "id": 306,
          "sku": "6600000",
          "grossTotalPrice": 787.4,
          "grossUnitPrice": 787.4,
          "currency": "HUF",
          "quantity": 1,
          "quantityName": "db",
          "name": "Termék 1",
          "brand": "márka"
        }
      ],
      "paymentMethod": {
        "name": "Barion"
      },
      "shippingMethod": {
        "name": "Személyes átvétel"
      },
      "couponCode": "TEST1234"
    }
  }
}
```

### onCheckoutShippingInfoAdded
A pénztár folyamatban, sikeres szállítási adatok megadása után bekövetkező esemény.

Példa:
```json
{
  "detail": {
    "user": {
      "id": 5,
      "email": "teszt@shoprenter.hu",
      "phoneNumber": "+36201234567",
      "name": {
        "firstName": "TesztVezetéknév",
        "lastName": "TesztKeresztnév"
      },
      "ipAddress": "172.30.128.0",
      "userAgent": "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/104.0.0.0 Safari/537.36"
    },
    "shop": {
      "name": "demo",
      "locale": "hu",
      "currency": {
        "code": "HUF",
        "rate": 1
      },
      "domain": "demo.myshoprenter.hu"
    },
    "event": {
      "id": "1662964179898-2566",
      "time": 1662964179,
      "sourceUrl": "https://demo.myshoprenter.hu/checkout#/shippingmethod/",
      "name": "CheckoutShippingInfoAdded"
    },
    "cart": {
      "items": [
        {
          "type": "product",
          "id": 311,
          "sku": "7700000",
          "grossTotalPrice": 7874,
          "grossUnitPrice": 3937,
          "currency": "HUF",
          "quantity": 2,
          "quantityName": "db",
          "name": "Termék 2"
        },
        {
          "type": "product",
          "id": 306,
          "sku": "6600000",
          "grossTotalPrice": 787.4,
          "grossUnitPrice": 787.4,
          "currency": "HUF",
          "quantity": 1,
          "quantityName": "db",
          "name": "Termék 1"
        }
      ],
      "paymentMethod": {
        "name": "Barion"
      },
      "shippingMethod": {
        "name": "Személyes átvétel"
      },
      "couponCode": "TEST1234"
    }
  }
}
```

### onCheckoutOrderConfirmed
Rendelés rögzítésekor bekövetkező esemény. Fontos, hogy ekkor kerül rögzítésre a rendelés viszont a fizetettség ténye még nem ismert.

Példa:
```json
{
  "detail": {
    "user": {
      "id": 5,
      "email": "teszt@shoprenter.hu",
      "phoneNumber": "+36201234567",
      "name": {
        "firstName": "TesztKeresztnév",
        "lastName": "TesztVezetéknév"
      },
      "ipAddress": "172.30.128.0",
      "userAgent": "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/104.0.0.0 Safari/537.36"
    },
    "shop": {
      "name": "demo",
      "locale": "hu",
      "currency": {
        "code": "HUF",
        "rate": 1
      },
      "domain": "demo.myshoprenter.hu"
    },
    "event": {
      "id": "1661255423774-7093",
      "time": 1661255423,
      "sourceUrl": "https://demo.myshoprenter.hu/index.php?route=checkout/success",
      "name": "CheckoutOrderConfirmed"
    },
    "order": {
      "id": 156,
      "currency": "HUF",
      "total": 9762.6696,
      "customer": {
        "name": {
          "firstName": "TesztKeresztnév",
          "lastName": "TesztVezetéknév"
        },
        "phoneNumber": "+36201234567",
        "email": "teszt@shoprenter.hu"
      },
      "items": [
        {
          "type": "product",
          "id": 311,
          "sku": "7700000",
          "grossUnitPrice": 3937,
          "grossTotalPrice": 7874,
          "currency": "HUF",
          "quantity": 2,
          "quantityName": "db",
          "name": "Termék 2",
          "brand": "márka"
        },
        {
          "type": "product",
          "id": 306,
          "sku": "6600000",
          "grossUnitPrice": 787.4,
          "grossTotalPrice": 787.4,
          "currency": "HUF",
          "quantity": 1,
          "quantityName": "db",
          "name": "Termék 1",
          "brand": "márka"
        }
      ],
      "paymentMethod": {
        "name": "Barion"
      },
      "shippingMethod": {
        "name": "Személyes átvétel"
      },
      "couponCode": "TEST1234"
    }
  }
}
```

### onCheckoutOrderPaid
Sikeres rendelés kifizetéskor végbemenő esemény. Az esemény a rendelés leadásakor párhuzamosan végbe megy, ha offline fizetési formát választottak például Banki Átutalás, mert a nem bankártyával történő fizetéseket automatikusan sikeres fizetésként értelmezzük.

Példa:
```json
{
  "detail": {
    "user": {
      "id": 5,
      "email": "teszt@shoprenter.hu",
      "phoneNumber": "+36201234567",
      "name": {
        "firstName": "TesztKeresztnév",
        "lastName": "TesztVezetéknév"
      },
      "ipAddress": "172.30.128.0",
      "userAgent": "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/104.0.0.0 Safari/537.36"
    },
    "shop": {
      "name": "demo",
      "locale": "hu",
      "currency": {
        "code": "HUF",
        "rate": 1
      },
      "domain": "demo.myshoprenter.hu"
    },
    "event": {
      "id": "1661255423710-6465",
      "time": 1661255423,
      "sourceUrl": "https://demo.myshoprenter.hu/index.php?route=checkout/success",
      "name": "CheckoutOrderPaid"
    },
    "order": {
      "id": 156,
      "currency": "HUF",
      "total": 9762.6696,
      "customer": {
        "name": {
          "firstName": "TesztKeresztnév",
          "lastName": "TesztVezetéknév"
        },
        "phoneNumber": "+36201234567",
        "email": "teszt@shoprenter.hu"
      },
      "items": [
        {
          "type": "product",
          "id": 311,
          "sku": "7700000",
          "grossUnitPrice": 3937,
          "grossTotalPrice": 7874,
          "currency": "HUF",
          "quantity": 2,
          "quantityName": "db",
          "name": "Termék 2",
          "brand": "márka"
        },
        {
          "type": "product",
          "id": 306,
          "sku": "6600000",
          "grossUnitPrice": 787.4,
          "grossTotalPrice": 787.4,
          "currency": "HUF",
          "quantity": 1,
          "quantityName": "db",
          "name": "Termék 1",
          "brand": "márka"
        }
      ],
      "couponCode": "TEST1234"
    }
  }
}
```

### onCheckoutOrderPaidUnsuccessful
Sikertelen online bankkártyás fizetéskor végbemenő esemény.

Példa:
```json
{
  "detail": {
    "user": {
      "id": 5,
      "email": "teszt@shoprenter.hu",
      "phoneNumber": "+36201234567",
      "name": {
        "firstName": "TesztKeresztnév",
        "lastName": "TesztVezetéknév"
      },
      "ipAddress": "172.30.128.0",
      "userAgent": "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/104.0.0.0 Safari/537.36"
    },
    "shop": {
      "name": "demo",
      "locale": "hu",
      "currency": {
        "code": "HUF",
        "rate": 1
      },
      "domain": "demo.myshoprenter.hu"
    },
    "event": {
      "id": "1661255423710-6465",
      "time": 1661255423,
      "sourceUrl": "https://demo.myshoprenter.hu/index.php?route=checkout/success",
      "name": "CheckoutOrderPaymentUnsuccessful"
    },
    "order": {
      "id": 156,
      "currency": "HUF",
      "total": 9762.6696,
      "customer": {
        "name": {
          "firstName": "TesztKeresztnév",
          "lastName": "TesztVezetéknév"
        },
        "phoneNumber": "+36201234567",
        "email": "teszt@shoprenter.hu"
      },
      "items": [
        {
          "type": "product",
          "id": 311,
          "sku": "7700000",
          "grossUnitPrice": 3937,
          "grossTotalPrice": 7874,
          "currency": "HUF",
          "quantity": 2,
          "quantityName": "db",
          "name": "Termék 2",
          "brand": "márka"
        },
        {
          "type": "product",
          "id": 306,
          "sku": "6600000",
          "grossUnitPrice": 787.4,
          "grossTotalPrice": 787.4,
          "currency": "HUF",
          "quantity": 1,
          "quantityName": "db",
          "name": "Termék 1",
          "brand": "márka"
        }
      ],
      "couponCode": "TEST1234"
    }
  }
}
```

### onProductPageViewed
Termékoldal megtekintéskor bekövetkező esemény.

Példa:
```json
{
  "detail": {
    "user": {
      "id": 5,
      "email": "teszt@shoprenter.hu",
      "phoneNumber": "+36201234567",
      "name": {
        "firstName": "TesztVezetéknév",
        "lastName": "TesztKeresztnév"
      },
      "ipAddress": "172.30.128.0",
      "userAgent": "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/104.0.0.0 Safari/537.36"
    },
    "shop": {
      "name": "demo",
      "locale": "hu",
      "currency": {
        "code": "HUF",
        "rate": 1
      },
      "domain": "demo.myshoprenter.hu"
    },
    "event": {
      "id": "1661256412700-752",
      "time": 1661256412,
      "sourceUrl": "https://demo.myshoprenter.hu/teszt-termek",
      "name": "ProductPageViewed"
    },
    "product": {
      "type": "product",
      "id": 306,
      "sku": "6600000",
      "grossUnitPrice": 787.4,
      "currency": "HUF",
      "quantity": 1,
      "name": "Termék 1",
      "brand": "ShopRenter",
      "unit": "db"
    }
  }
}
```

### onMarketingConsentChanged
Marketing cookiek elfogadás/tiltása esetén bekövetkező esemény.

Példa:
```json
{
  "detail": {
    "user": {
      "id": 5,
      "email": "teszt@shoprenter.hu",
      "phoneNumber": "+36201234567",
      "name": {
        "firstName": "TesztVezetéknév",
        "lastName": "TesztKeresztnév"
      },
      "ipAddress": "172.30.128.0",
      "userAgent": "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/104.0.0.0 Safari/537.36"
    },
    "shop": {
      "name": "demo",
      "locale": "hu",
      "currency": {
        "code": "HUF",
        "rate": 1
      },
      "domain": "demo.myshoprenter.hu"
    },
    "event": {
      "id": "1661258401667-6059",
      "time": 1661258401,
      "sourceUrl": "https://demo.myshoprenter.hu/",
      "name": "MarketingConsentChanged"
    },
    "isAccepted": true
  }
}
```

### onCustomerRegistered
A vásárló regisztráció bekövetkező esemény.

Példa:
```json
{
  "detail": {
    "user": {
      "id": 5,
      "email": "teszt@shoprenter.hu",
      "phoneNumber": "+36201234567",
      "name": {
        "firstName": "TesztVezetéknév",
        "lastName": "TesztKeresztnév"
      },
      "ipAddress": "172.30.128.0",
      "userAgent": "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/104.0.0.0 Safari/537.36"
    },
    "shop": {
      "name": "demo",
      "locale": "hu",
      "currency": {
        "code": "HUF",
        "rate": 1
      },
      "domain": "demo.myshoprenter.hu"
    },
    "event": {
      "id": "1661258401667-6059",
      "time": 1661258401,
      "sourceUrl": "https://demo.myshoprenter.hu/",
      "name": "CustomerRegistered"
    }
  }
}
```

### onCustomerLoggedIn
A vásárló bejelentkezésekor bekövetkező esemény.

Példa:
```json
{
  "detail": {
    "user": {
      "id": 5,
      "email": "teszt@shoprenter.hu",
      "phoneNumber": "+36201234567",
      "name": {
        "firstName": "TesztVezetéknév",
        "lastName": "TesztKeresztnév"
      },
      "ipAddress": "172.30.128.0",
      "userAgent": "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/104.0.0.0 Safari/537.36"
    },
    "shop": {
      "name": "demo",
      "locale": "hu",
      "currency": {
        "code": "HUF",
        "rate": 1
      },
      "domain": "demo.myshoprenter.hu"
    },
    "event": {
      "id": "1661258401667-6059",
      "time": 1661258401,
      "sourceUrl": "https://demo.myshoprenter.hu/customer/login",
      "name": "CustomerLoggedIn"
    }
  }
}
```

### onCustomerUpdated
A vásárló fiók adatainak módosításakor bekövetkező esemény.

Példa:
```json
{
  "detail": {
    "user": {
      "id": 5,
      "email": "teszt@shoprenter.hu",
      "phoneNumber": "+36201234567",
      "name": {
        "firstName": "TesztVezetéknév",
        "lastName": "TesztKeresztnév"
      },
      "ipAddress": "172.30.128.0",
      "userAgent": "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/104.0.0.0 Safari/537.36"
    },
    "shop": {
      "name": "demo",
      "locale": "hu",
      "currency": {
        "code": "HUF",
        "rate": 1
      },
      "domain": "demo.myshoprenter.hu"
    },
    "event": {
      "id": "1661258401667-6059",
      "time": 1661258401,
      "sourceUrl": "https://demo.myshoprenter.hu/index.php?route=account/account",
      "name": "CustomerUpdated"
    }
  }
}
```

Nem regisztrált vásárlók esetén a ``user`` objektum egyes tulajdonságai üres stringek lehetnek. Továbbá regisztrálatlan látogató esetén a ``user.id`` nulla.

A ``shippingMethod`` és ``paymentMethod`` objektumok egyes eseményeknél szerepelhetnek üres ``name`` tulajdonsággal. Például értelem szerűen egy pénztár folyamat elkezdésekor még ezeket nem lehet értelmezni, viszont ha a vásárló már megadja ezeket és vissza ugrik az első lépésre, akkor már értelmezhetőek.

Figyelni kell arra, hogy az átadott javascript closure-nek legyen egy paramétere, melynek a neve tetszőleges lehet, pl. event vagy e. Így az e.details property kikéréssel, hozzájutunk az esemény adataihoz.

### Események használata
A ShopRenter nevű objektum a frontend egész felületén elérhető, így bármely oldalon fel tudunk iratkozni a kosár eseményekre a következőképpen:

```html
<script type="application/javascript">
ShopRenter.onCartUpdate(function(event) {
    console.log(event.detail)
});
</script>
```
