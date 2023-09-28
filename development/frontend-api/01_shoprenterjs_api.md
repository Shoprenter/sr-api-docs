# ShopRenter.js

Contents:
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
    * [onCartPageViewed](#oncartpageviewed)
    * [Using_events](#esemenyek-hasznalata)

## ShopRenter Object
Applications that are integrated into the front end may require data that is essential for the business logic of the application.
The ShopRenter global JavaScript object is available on the frontend for every page load, which contains objects and event monitors that store webshop data.

## Properties

### customer
Some data of the current Customer can be requested on each page of the store's frontend,
which is contained in the **customer** property of the ShopRenter javascript object.
The object does not contain sensitive data on the basis of which the Buyer could be identified.

Example:
```javascript
console.log(ShopRenter.customer);
```

Output:
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

Meaning of some fields:
<table> 
    <tr>
        <th>property</th>
        <th>meaning</th>
    </tr>
    <tr>
        <td>userId</td>
        <td>Internal ID of the Customer. If 0, then the Customer is not a registered user</td>
    </tr>
    <tr>
        <td>userGroupId</td>
        <td>The customer's customer group ID</td>
    </tr>  
    <tr>
        <td>customerGroupTaxMode</td>
        <td>
           According to the customer group of the current Buyer, you specify how the price should be displayed outside of the product page
           <ul>
              <li><strong>gross</strong>: Gross price</li>
              <li><strong>net</strong>: Net price</li>
           </ul>
        </td>
    </tr> 
    <tr>
        <td>customerGroupPriceMode</td>
        <td>
           Specifies how the price should be displayed on the <strong>product page</strong> according to the customer group of the current Customer
              <li><strong>only_gross</strong>: Only listing the gross price</li>
              <li><strong>gross_net_tax</strong>: Gross price, followed by the net price + VAT in brackets</li>
              <li><strong>only_net</strong>: Only display the net price</li>
              <li><strong>net_tax</strong>: The net price and the +VAT behind it</li>
              <li><strong>net_tax_gross</strong>: The net price followed by +VAT, and the gross price in parentheses</li>
        </td>
    </tr>
    <tr>
        <td>email</td>
        <td>Buyer's e-mail address</td>
    </tr>
    <tr>
        <td>name</td>
        <td>The name object contains the line and first name of the receiver</td>
    </tr>
</table>

### theme
Some data of the current template can be requested on each page of the store's frontend,
which is contained in the **theme** property of the ShopRenter javascript object.

Example:
```javascript
console.log(ShopRenter.theme);
```

Output:
```javascript
{
    name: "tokyo_glacierblue", 
    family: "tokyo", 
    parent: "bootstrap"
}
```

Meaning of some fields:

<table> 
    <tr>
        <th>property</th>
        <th>meaning</th>
    </tr>
    <tr>
        <td>name</td>
        <td>Name</td>
    </tr>
    <tr>
        <td>family</td>
        <td>The name of the template family to which the current template belongs</td>
    </tr>  
    <tr>
        <td>parent</td>
        <td>The name of the parent template</td>
    </tr>
</table>

### shop
The store's most important data can be requested on all pages of the store's frontend,
which is contained in the **theme** property of the ShopRenter javascript object.

Example:
```javascript
console.log(ShopRenter.shop);
```

Output:
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

Meaning of some fields:
<table> 
    <tr>
        <th>property</th>
        <th>meaning</th>
    </tr>
    <tr>
        <td>name</td>
        <td>Name of the shop</td>
    </tr>
    <tr>
        <td>locale</td>
        <td>The shop's current frontend language</td>
    </tr>  
    <tr>
        <td>currency</td>
        <td>
           Data on the current currency of the shop::
           <ul>
              <li><strong>code</strong>: The language code of the currency</li>
              <li><strong>rate</strong>: Currency exchange value used for the shop's default currency.
                  E.g.: we must divide 1 by the value of the exchange rate of the given currency, for example, if the exchange rate of the currency is HUF 195, then the value field is: 1/195, so the rate will be 0.005128
              </li>
           </ul>
        </td>
    </tr>
    <tr>
        <td>domain</td>
        <td>
           The system domain of the shop
        </td>
    </tr>
</table>

### page
The **page** property of the ShopRenter object contains the data of the current page.

Example:
```javascript
console.log(ShopRenter.page);
```

Output:
```javascript
{
    route: "product/list"
}
```

Meaning of some fields:
<table> 
    <tr>
        <th>property</th>
        <th>meaning</th>
    </tr>
    <tr>
        <td>route</td>
        <td>The route value of the given subpage</td>
    </tr>
</table>

### product
The **product** property of the ShopRenter object contains the information related to the product. This property is only available on the product page!

Example:
```javascript
console.log(ShopRenter.product);
```

Output:
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

Meaning of some fields:
<table> 
    <tr>
        <th>property</th>
        <th>meaning</th>
    </tr>
    <tr>
        <td>id</td>
        <td>The identifier of the current product</td>
    </tr>
    <tr>
        <td>sku</td>
        <td>The sku of the current product</td>
    </tr>
    <tr>
        <td>parent.id</td>
        <td>The ID of the parent product</td>
    </tr>
    <tr>
        <td>parent.sku</td>
        <td>The sku of the parent product</td>
    </tr>
</table>

## Events
ShopRenter triggers javascript events when certain shopping cart and customer events occur, to which additional behavior can be implemented by subscribing to them.

Newly added event listeners (Event Listeners) receive the data associated with the event.

The system returns the event to a CustomEvent object, whose **detail** property contains the data related to the given event.

### onItemAdd
Add to cart from any part of the store (module product card, product page, category page). You will receive the data of the product placed in the basket.

Example:
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
You can subscribe to an event that occurs when the basket is changed (when a product is added/deleted/changed). You will receive the modified basket data in the subscribed eventlistener parameter.

Example:
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
                    "name": "test product for sale",
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
                    "href": "https://demo.shoprenter.hu/test_termek_akciohoz_318",
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
                    "sku": "TestOPC1234",
                    "minimumPlural": "0",
                    "isPresent": false,
                    "shippingTime": 1565965848,
                    "isParentOrChild": false,
                    "image": "",
                    "cartKey": "S7QytqrOtDKwzrQyNjQHkoZQbGSdaGVoVV1sZW6llF9QkpmfV6wEFDKwqq6trQUA",
                    "download": [],
                    "cartItemType": "Product",
                    "name": "Test sale product",
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
                    "href": "https://demo.shoprenter.hu/test_opcios_termek_317",
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
                    "name": "Test product for sale",
                    "quantityName": "db",
                    "oldQuantity": 11,
                    "newQuantity": 12,
                    "grossUnitPrice": 10000,
                    "brand": "Test Kft."
                  }
                ]
              }
}
```

### onItemDelete
You can subscribe to the cart deletion event. In the subscribed eventlistener parameter, you will receive the data of the basket after deletion.

Example:
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
                    "name": "Test product for sale",
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
                    "href": "https://demo.shoprenter.hu/test_termek_akciohoz_318",
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
                    "sku": "TestOPC1234",
                    "minimumPlural": "0",
                    "isPresent": false,
                    "shippingTime": 1565965848,
                    "isParentOrChild": false,
                    "image": "",
                    "cartKey": "S7QytqrOtDKwzrQyNjQHkoZQbGSdaGVoVV1sZW6llF9QkpmfV6wEFDKwqq6trQUA",
                    "download": [],
                    "cartItemType": "Product",
                    "name": "Test product with option",
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
                    "href": "https://demo.shoprenter.hu/test_opcios_termek_317",
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
                    "brand": "Test Kft."
                  }
                ]
              }
}
```

### onSearchResultViewed
Event that occurs when a product search result appears. It is important that the event is not triggered at the moment of the search, but when the search result appears.

Example:
```json
{
  "detail": {
    "user": {
      "id": 5,
      "email": "test@shoprenter.hu",
      "phoneNumber": "+36201234567",
      "name": {
        "firstName": "Test firstname",
        "lastName": "Test lastname"
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
Event that occurs when signing up for a newsletter.

Example:
```json
{
  "detail": {
    "user": {
      "id": 5,
      "email": "test@shoprenter.hu",
      "phoneNumber": "+36201234567",
      "name": {
        "firstName": "Test Firstname",
        "lastName": "Test Lastname"
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
Event that occurs when the checkout process starts.

Example:
```json
{
  "detail": {
    "user": {
      "id": 5,
      "email": "test@shoprenter.hu",
      "phoneNumber": "+36201234567",
      "name": {
        "firstName": "Test First Name",
        "lastName": "Test Last Name"
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
          "name": "Product 2",
          "brand": "brand"
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
          "name": "Product 1",
          "brand": "branch"
        }
      ],
      "paymentMethod": {
        "name": "Barion"
      },
      "shippingMethod": {
        "name": "Personal Pickup"
      },
      "grossTotalPrice": 8661.4,
      "couponCode": "TEST1234"
    }
  }
}
```

### onCheckoutPaymentInfoAdded
An event that occurs during the checkout process, after successful payment data has been entered.

Example:
```json
{
  "detail": {
    "user": {
      "id": 5,
      "email": "test@shoprenter.hu",
      "phoneNumber": "+36201234567",
      "name": {
        "firstName": "Test First Name",
        "lastName": "Test Last Name"
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
          "name": "Product 2",
          "brand": "brand"
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
          "name": "Product 1",
          "brand": "brand"
        }
      ],
      "paymentMethod": {
        "name": "Barion"
      },
      "shippingMethod": {
        "name": "Personal pickup"
      },
      "couponCode": "TEST1234"
    }
  }
}
```

### onCheckoutShippingInfoAdded
Event that occurs during the checkout process, after successful delivery data has been entered.

Example:
```json
{
  "detail": {
    "user": {
      "id": 5,
      "email": "test@shoprenter.hu",
      "phoneNumber": "+36201234567",
      "name": {
        "firstName": "Test firstname",
        "lastName": "Test lastname"
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
          "name": "Product 2"
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
          "name": "Product 1"
        }
      ],
      "paymentMethod": {
        "name": "Barion"
      },
      "shippingMethod": {
        "name": "Personal pickup"
      },
      "couponCode": "TEST1234"
    }
  }
}
```

### onCheckoutOrderConfirmed
Event that occurs when an order is recorded. It is important that the order is recorded at this time, but the fact of payment is not yet known.

Example:
```json
{
  "detail": {
    "user": {
      "id": 5,
      "email": "test@shoprenter.hu",
      "phoneNumber": "+36201234567",
      "name": {
        "firstName": "Test lastname",
        "lastName": "Test firstname"
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
          "firstName": "Test lastname",
          "lastName": "Test firstname"
        },
        "phoneNumber": "+36201234567",
        "email": "test@shoprenter.hu"
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
          "name": "Product 2",
          "brand": "brand"
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
          "name": "Product 1",
          "brand": "brand"
        }
      ],
      "paymentMethod": {
        "name": "Barion"
      },
      "shippingMethod": {
        "name": "Personal pickup",
        "grossTotal": 990
      },
      "couponCode": "TEST1234",
      "totals": {
        "taxes": [
          {
            "name": "27%",
            "value": 250
          }
        ]
      }
    }
  }
}
```

### onCheckoutOrderPaid
Event that occurs when a successful order is paid. The event takes place in parallel when the order is placed, if an offline payment method has been chosen, for example Bank Transfer, because payments made without a bank card are automatically interpreted as a successful payment.

Example:
```json
{
  "detail": {
    "user": {
      "id": 5,
      "email": "test@shoprenter.hu",
      "phoneNumber": "+36201234567",
      "name": {
        "firstName": "Test lastname",
        "lastName": "Test firstname"
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
          "firstName": "Test lastname",
          "lastName": "Test firstname"
        },
        "phoneNumber": "+36201234567",
        "email": "test@shoprenter.hu"
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
          "name": "Product 2",
          "brand": "brand"
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
          "name": "Product 1",
          "brand": "brand"
        }
      ],
      "couponCode": "TEST1234"
    }
  }
}
```

### onCheckoutOrderPaidUnsuccessful
Event that occurs when an online bank card payment fails.

Example:
```json
{
  "detail": {
    "user": {
      "id": 5,
      "email": "test@shoprenter.hu",
      "phoneNumber": "+36201234567",
      "name": {
        "firstName": "Test lastname",
        "lastName": "Test firstname"
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
          "firstName": "Test lastname",
          "lastName": "Test firstname"
        },
        "phoneNumber": "+36201234567",
        "email": "test@shoprenter.hu"
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
          "name": "Product 2",
          "brand": "brand"
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
          "name": "Product 1",
          "brand": "brand"
        }
      ],
      "couponCode": "TEST1234"
    }
  }
}
```

### onProductPageViewed
Event that occurs when viewing a product page.

Example:
```json
{
  "detail": {
    "user": {
      "id": 5,
      "email": "test@shoprenter.hu",
      "phoneNumber": "+36201234567",
      "name": {
        "firstName": "Test firstname",
        "lastName": "Test lastname"
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
      "sourceUrl": "https://demo.myshoprenter.hu/test-termek",
      "name": "ProductPageViewed"
    },
    "product": {
      "type": "product",
      "id": 306,
      "sku": "6600000",
      "grossUnitPrice": 787.4,
      "currency": "HUF",
      "quantity": 1,
      "name": "Product 1",
      "brand": "ShopRenter",
      "unit": "db"
    }
  }
}
```

### onMarketingConsentChanged
Event that occurs when marketing cookies are accepted/disallowed.

Example:
```json
{
  "detail": {
    "user": {
      "id": 5,
      "email": "test@shoprenter.hu",
      "phoneNumber": "+36201234567",
      "name": {
        "firstName": "Test firstname",
        "lastName": "Test lastname"
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
Customer registration is an event that occurs.

Example:
```json
{
  "detail": {
    "user": {
      "id": 5,
      "email": "test@shoprenter.hu",
      "phoneNumber": "+36201234567",
      "name": {
        "firstName": "Test firstname",
        "lastName": "Test lastname"
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
Event that occurs when the customer logs in.

Example:
```json
{
  "detail": {
    "user": {
      "id": 5,
      "email": "test@shoprenter.hu",
      "phoneNumber": "+36201234567",
      "name": {
        "firstName": "Test firstname",
        "lastName": "Test lastname"
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
Event that occurs when customer account data is changed.

Example:
```json
{
  "detail": {
    "user": {
      "id": 5,
      "email": "test@shoprenter.hu",
      "phoneNumber": "+36201234567",
      "name": {
        "firstName": "Test firstname",
        "lastName": "Test lastname"
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

In the case of unregistered customers, some properties of the ``user`` object can be empty strings. Furthermore, ``user.id`` is zero in the case of an unregistered visitor.

The ``shippingMethod`` and ``paymentMethod`` objects can be included in some events with an empty ``name`` property. For example, by definition, these cannot be interpreted at the start of a checkout process, but if the customer has already entered them and jumps back to the first step, they can already be interpreted.

Make sure that the passed javascript closure has a parameter, the name of which can be arbitrary, e.g. event or e. Thus, by requesting the e.details property, we get access to the event data.

### onCartPageViewed
The event occurs when the customer opens the cart page.

Example:
```json
{
  "detail": {
    "user": {
      "id": 5,
      "email": "test@shoprenter.hu",
      "phoneNumber": "+36201234567",
      "name": {
        "firstName": "Test firstname",
        "lastName": "Test lastname"
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
      "sourceUrl": "https://demo.myshoprenter.hu/cart",
      "name": "CartPageViewed"
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
          "name": "Product 2",
          "brand": "brand"
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
          "name": "Product 1",
          "brand": "brand"
        }
      ]
    }
  }
}
```

### Using events
The object called ShopRenter is available on the entire interface of the frontend, so we can subscribe to cart events on any page as follows:

```html
<script type="application/javascript">
ShopRenter.onCartUpdate(function(event) {
    console.log(event.detail)
});
</script>
```
