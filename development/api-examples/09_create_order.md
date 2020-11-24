# Rendelés felvétele

Az alábbi példában bemutatásra kerül, hogy miként lehet egy rendelést felvenni Shoprenter API segítségével.

A feladat az alábbi lépésekből áll:

1. Rendelés létrehozása az [**Order Resource**](../../api/order.md) segítségével
2. További tételek hozzáadása az [**Order Total**](../../api/order_total.md) segítségével
3. Rendelt termékek hozzáadása a [**Order Product**](../../api/order_product.md) segítségével
4. Rendelés total értékének módosítása az [**Order Resource**](../../api/order.md) segítségével

## 1. lépés

Az [**Order Resource**](../../api/order.md) segítségével létrehozzuk az új rendelést.
Itt figyelnünk kell arra, hogy a rendeléshez már ilyenkor hozzá kell adni a
 - Nyelvet [Language Resource](../../api/language.md) resource id-t
 - Valutát [Currency Resource](../../api/currency.md) resource id-t
 - Rendelés státuszt [Order Status Resource](../../api/order_status.md) resource id-t
 - Szállítási módot (([Shipping Mode Extend Resource](../../api/shipping_mode_extend.md) )csatolásakor ügyeljünk arra, 
   hogy a megfelelő shippingMethodName-et adjunk meg)
 - Vásárlót és vásárlói csoportot [Customer Extend Resource](../../api/customer_extend.md) 
   és [Customer Group Resource](../../api/customer_group.md). (Amennyiben regisztrált vásárlóról van szó abban az 
   esetben meg kell adni a 
   customer ID-t és customerGroup ID-t. Ha nem regisztrált abban az esetben nem szükséges. 
 - a total értéket érdemes 0 értékkel megadni és ha minden lépéssel végeztünk utána megadni a Bruttó végösszeget, 
   mert lehetséges, hogy változik ez az érték, ha minden lépéssel végeztünk.
 - Itt még nem feltétlenül szükséges a "total" mezőt felvenni. Mikor a rendeléshez tartozó minden al-resource megadásra
   került, és pontosan megvan a rendelés végösszege, ezután vesszük fel a rendeléshez. 
 
**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/orders</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>
        Accept:application/json<br>
        Content-Type:application/json
    </td>
  </tr>
</table> 

```json
{
    "invoiceId": "0",
    "invoicePrefix": null,
    "firstname": "Teszt",
    "lastname": "Teszt",
    "phone": "+36201234567",
    "fax": null,
    "email": "teszt@teszt.com",
    "shippingFirstname": "Teszt",
    "shippingLastname": "Teszt",
    "shippingCompany": null,
    "shippingAddress1": "Teszt út 11",
    "shippingAddress2": null,
    "shippingCity": "Teszt",
    "shippingPostcode": "4033",
    "shippingZoneName": null,
    "shippingCountryName": "Magyarország",
    "shippingAddressFormat": null,
    "shippingMethodName": "Házhozszállítás futárszolgálattal",
    "shippingMethodTaxRate": "27.0000",
    "shippingMethodTaxName": "27 %",
    "shippingMethodExtension": "WSESHIP",
    "shippingReceivingPointId": "0",
    "paymentFirstname": "Teszt",
    "paymentLastname": "Teszt",
    "paymentCompany": null,
    "paymentAddress1": "Teszt út 11",
    "paymentAddress2": null,
    "paymentCity": "Teszt",
    "paymentPostcode": "4033",
    "paymentZoneName": null,
    "paymentCountryName": "Magyarország",
    "paymentAddressFormat": null,
    "paymentMethodName": "Fizetési mód",
    "paymentMethodCode": "COD",
    "paymentMethodTaxRate": "0.0000",
    "paymentMethodTaxName": null,
    "paymentMethodAfter": "1",
    "comment": "Megjegyzés",
    "total": null,
    "value": "1.00000000",
    "couponTaxRate": "-1.0000",
    "dateCreated": "2020-11-19T18:13:31",
    "dateUpdated": "2020-11-19T18:13:31",
    "ip": "11.11.11.11",
    "pickPackPontShopCode": "100010",
    "customer": {
        "id": "Y3VzdG9tZXItY3VzdG9tZXJfaWQ9MzQ="
    },
    "customerGroup": {
        "id": "Y3VzdG9tZXJHcm91cC1jdXN0b21lcl9ncm91cF9pZD04"
    },
    "shippingZone": null,
    "shippingCountry": {
        "id": "Y291bnRyeS1jb3VudHJ5X2lkPTk3"
    },
    "paymentZone": null,
    "paymentCountry": {
        "id": "Y291bnRyeS1jb3VudHJ5X2lkPTk3"
    },
    "orderStatus": {
        "id": "b3JkZXJTdGF0dXMtb3JkZXJfc3RhdHVzX2lkPTE="
    },
    "language": {
        "id": "bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ=="
    },
    "currency": {
        "id": "Y3VycmVuY3ktY3VycmVuY3lfaWQ9NA=="
    },
    "shippingMode" : {
        "id": "c2hpcHBpbmdNb2RlLWlkPTE4"
    }
}
```
**Response**

```json

{
    "href": "http://shopname.api.shoprenter.hu/orders/b3JkZXItb3JkZXJfaWQ9NDk=",
    "id": "b3JkZXItb3JkZXJfaWQ9NDk=",
    "innerId": "49",
    "invoiceId": "0",
    "invoicePrefix": "",
    "firstname": "Fekete",
    "lastname": "Márton",
    "phone": "+36201234567",
    "fax": "",
    "email": "teszt@teszt.com",
    "shippingFirstname": "Teszt",
    "shippingLastname": "Teszt",
    "shippingCompany": "",
    "shippingAddress1": "Teszt út 11",
    "shippingAddress2": "",
    "shippingCity": "Teszt",
    "shippingPostcode": "4033",
    "shippingZoneName": "",
    "shippingCountryName": "Magyarország",
    "shippingAddressFormat": "",
    "shippingMethodName": "Házhozszállítás futárszolgálattal",
    "shippingMethodTaxRate": "27.0000",
    "shippingMethodTaxName": "27 %",
    "shippingMethodExtension": "WSESHIP",
    "shippingReceivingPointId": "0",
    "paymentFirstname": "Teszt",
    "paymentLastname": "Teszt",
    "paymentCompany": "",
    "paymentAddress1": "Teszt út 11",
    "paymentAddress2": "",
    "paymentCity": "Teszt",
    "paymentPostcode": "4033",
    "paymentZoneName": "",
    "paymentCountryName": "Magyarország",
    "paymentAddressFormat": "",
    "paymentMethodName": "Fizetési mód",
    "paymentMethodCode": "COD",
    "paymentMethodTaxRate": "0.0000",
    "paymentMethodTaxName": "",
    "paymentMethodAfter": "1",
    "taxNumber": "",
    "comment": "Megjegyzés",
    "total": "24060.0000",
    "value": "1.00000000",
    "couponTaxRate": "-1.0000",
    "dateCreated": "2020-11-19T23:05:26",
    "dateUpdated": "2020-11-19T23:05:26",
    "ip": "11.11.11.11",
    "pickPackPontShopCode": "100010",
    "loyaltyPointsTaxRate": "-1.0000",
    "customer": {
        "href": "http://shopname.api.shoprenter.hu/customers/Y3VzdG9tZXItY3VzdG9tZXJfaWQ9MQ=="
    },
    "customerGroup": {
        "href": "http://shopname.api.shoprenter.hu/customerGroups/Y3VzdG9tZXJHcm91cC1jdXN0b21lcl9ncm91cF9pZD04"
    },
    "shippingZone": null,
    "shippingCountry": {
        "href": "http://shopname.api.shoprenter.hu/countries/Y291bnRyeS1jb3VudHJ5X2lkPTk3"
    },
    "paymentZone": null,
    "paymentCountry": {
        "href": "http://shopname.api.shoprenter.hu/countries/Y291bnRyeS1jb3VudHJ5X2lkPTk3"
    },
    "orderStatus": {
        "href": "http://shopname.api.shoprenter.hu/orderStatuses/b3JkZXJTdGF0dXMtb3JkZXJfc3RhdHVzX2lkPTE="
    },
    "language": {
        "href": "http://shopname.api.shoprenter.hu/languages/bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ=="
    },
    "currency": {
        "href": "http://shopname.api.shoprenter.hu/currencies/Y3VycmVuY3ktY3VycmVuY3lfaWQ9NA=="
    },
    "shippingMode": {
        "href": "http://shopname.api.shoprenter.hu/shippingModes/c2hpcHBpbmdNb2RlLWlkPTE4"
    },
    "furgefutarWaybill": 0,
    "orderTotals": {
        "href": "http://shopname.api.shoprenter.hu/orderTotals?orderId=b3JkZXItb3JkZXJfaWQ9NDk="
    },
    "orderProducts": {
        "href": "http://shopname.api.shoprenter.hu/orderProducts?orderId=b3JkZXItb3JkZXJfaWQ9NDk="
    },
    "orderGiftWrappings": {
        "href": "http://shopname.api.shoprenter.hu/orderGiftWrappings?orderId=b3JkZXItb3JkZXJfaWQ9NDk="
    }
}
```
 
## 2. lépés 
 
Ahhoz, hogy a rendelés megjelenjen az admin felületen belül Bolt > Rendelések listában, az alábbi típusú [**Order Total**](../../api/order_total.md) -nak léteznie kell:
 -  "SUB_TOTAL" típusú értéknek, mely a Nettó részösszegnek felel meg
 -  "TAX" típusú értéknek, mely az ÁFA értékének felel meg
 -  "SUB_TOTAL_WITH_TAX" típusú értéknek, mely a Bruttó részösszegnek felel meg
 -  "SHIPPING" típusú értéknek, mely a Szállítási díjnak felel meg
 -  "TOTAL" típusú értéknek, mely a Bruttó vgéösszegnek felel meg
 
 Az [**Order Total**](../../api/order_total.md)-ban a sortOrder tulajdonsággal tudjuk megadni, hogy a rendelés táblázatában hanyadik sorban szerepeljen a felvett [**Order Total**](../../api/order_total.md) resource. 
 Az [**Order Total**](../../api/order_total.md) -ban megadott value értékek nem kerülnek automatikus számolásra, így azokat manuálisan szükséges megadni.
 

 Az alábbi példa segít abban, hogy "Nettó részösszeg" esetén milyen kérést kell elküldenünk:

**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/orderTotals</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>
        Accept:application/json<br>
        Content-Type:application/json
    </td>
  </tr>
</table> 

```json
{
    "name": "Nettó részösszeg:",
    "valueText": "18.000 Ft ",
    "value": "18000.0000",
    "sortOrder": "3",
    "type": "SUB_TOTAL ",
    "key": null,
    "description": null,
    "order": {
        "id": "b3JkZXItb3JkZXJfaWQ9NDk="
    }
}
```
**Response**

```json
{
    "href": "http://shopname.api.shoprenter.hu/orderTotals/b3JkZXJUb3RhbC1vcmRlcl90b3RhbF9pZD02NjQ=",
    "id": "b3JkZXJUb3RhbC1vcmRlcl90b3RhbF9pZD02NjQ=",
    "name": "Nettó részösszeg:",
    "valueText": "18.000 Ft ",
    "value": "18000.0000",
    "sortOrder": "3",
    "type": "",
    "key": "",
    "description": "",
    "dateCreated": "2020-11-19T23:22:46",
    "dateUpdated": "2020-11-19T23:22:46",
    "order": {
        "href": "http://shopname.api.shoprenter.hu/orders/b3JkZXItb3JkZXJfaWQ9NDk="
    }
}
```

 Az alábbi példa segít abban, hogy "ÁFA (27%):" esetén milyen kérést kell megadnunk:
 
**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/orderTotals</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>
        Accept:application/json<br>
        Content-Type:application/json
    </td>
  </tr>
</table> 

```json
{
    "name": "ÁFA (27%): ",
    "valueText": " 4.860 Ft ",
    "value": "4860.0000",
    "sortOrder": "4",
    "type": "TAX",
    "key": null,
    "description": null,
    "order": {
        "id": "b3JkZXItb3JkZXJfaWQ9NDk="
    }
}
```
**Response**

```json
{
    "href": "http://shopname.api.shoprenter.hu/orderTotals/b3JkZXJUb3RhbC1vcmRlcl90b3RhbF9pZD02NjU=",
    "id": "b3JkZXJUb3RhbC1vcmRlcl90b3RhbF9pZD02NjU=",
    "name": "ÁFA (27%): ",
    "valueText": " 4.860 Ft ",
    "value": "4860.0000",
    "sortOrder": "4",
    "type": "TAX",
    "key": "",
    "description": "",
    "dateCreated": "2020-11-19T23:23:46",
    "dateUpdated": "2020-11-19T23:23:46",
    "order": {
        "href": "http://shopname.api.shoprenter.hu/orders/b3JkZXItb3JkZXJfaWQ9NDk="
    }
}
```

Az alábbi példa segít abban, hogy "Bruttó részösszeg:" esetén milyen kérést kell elküldenünk:


**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/orderTotals</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>
        Accept:application/json<br>
        Content-Type:application/json
    </td>
  </tr>
</table> 

```json
{
    "name": "Bruttó részösszeg:",
    "valueText": "22.860 Ft",
    "value": "22860.0000",
    "sortOrder": "5",
    "type": "SUB_TOTAL_WITH_TAX",
    "key": null,
    "description": null,
    "order": {
        "id": "b3JkZXItb3JkZXJfaWQ9NDk="
    }
}
```
**Response**

```json
{
    "href": "http://shopname.api.shoprenter.hu/orderTotals/b3JkZXJUb3RhbC1vcmRlcl90b3RhbF9pZD02NjY=",
    "id": "b3JkZXJUb3RhbC1vcmRlcl90b3RhbF9pZD02NjY=",
    "name": "Bruttó részösszeg:",
    "valueText": "22.860 Ft",
    "value": "22860.0000",
    "sortOrder": "5",
    "type": "SUB_TOTAL_WITH_TAX",
    "key": "",
    "description": "",
    "dateCreated": "2020-11-19T23:24:59",
    "dateUpdated": "2020-11-19T23:24:59",
    "order": {
        "href": "http://shopname.api.shoprenter.hu/orders/b3JkZXItb3JkZXJfaWQ9NDk="
    }
}
```

Az alábbi példa segít abban, hogy "Házhozszállítás futárszolgálattal:" esetén milyen kérést kell elküldenünk:


**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/orderTotals</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>
        Accept:application/json<br>
        Content-Type:application/json
    </td>
  </tr>
</table> 

```json
{
    "name": "Házhozszállítás futárszolgálattal:",
    "valueText": "1.200 Ft",
    "value": "1200.0000",
    "sortOrder": "6",
    "type": "SHIPPING",
    "key": null,
    "description": null,
    "order": {
        "id": "b3JkZXItb3JkZXJfaWQ9NDk="
    }
}
```
**Response**

```json
{
    "href": "http://shopname.api.shoprenter.hu/orderTotals/b3JkZXJUb3RhbC1vcmRlcl90b3RhbF9pZD02Njc=",
    "id": "b3JkZXJUb3RhbC1vcmRlcl90b3RhbF9pZD02Njc=",
    "name": "Házhozszállítás futárszolgálattal:",
    "valueText": "1.200 Ft",
    "value": "1200.0000",
    "sortOrder": "6",
    "type": "SHIPPING",
    "key": "",
    "description": "",
    "dateCreated": "2020-11-19T23:27:05",
    "dateUpdated": "2020-11-19T23:27:05",
    "order": {
        "href": "http://shopname.api.shoprenter.hu/orders/b3JkZXItb3JkZXJfaWQ9NDk="
    }
}
```


Az alábbi példa segít abban, hogy "Bruttó végösszeg:" esetén milyen kérést kell megadnunk:


**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/orderTotals</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>
        Accept:application/json<br>
        Content-Type:application/json
    </td>
  </tr>
</table> 

```json
{
    "name": "Bruttó végösszeg:",
    "valueText": "24060 Ft",
    "value": "24060.0000",
    "sortOrder": "7",
    "type": "TOTAL",
    "key": null,
    "description": null,
    "order": {
        "id": "b3JkZXItb3JkZXJfaWQ9NDk="
    }
}
```
**Response**

```json
{
    "href": "http://shopname.api.shoprenter.hu/orderTotals/b3JkZXJUb3RhbC1vcmRlcl90b3RhbF9pZD02NjM=",
    "id": "b3JkZXJUb3RhbC1vcmRlcl90b3RhbF9pZD02NjM=",
    "name": "Bruttó végösszeg:",
    "valueText": "24060 Ft",
    "value": "24060.0000",
    "sortOrder": "7",
    "type": "TOTAL",
    "key": "",
    "description": "",
    "dateCreated": "2020-11-19T23:19:24",
    "dateUpdated": "2020-11-19T23:19:24",
    "order": {
        "href": "http://shopname.api.shoprenter.hu/orders/b3JkZXItb3JkZXJfaWQ9NDk="
    }
}
```

## 3. lépés 

Küssünk össze egy tetszőleges terméket a rendeléssel.  Ezt az [**Order Product Resource**](../../api/order_product.md) 
resoruce-al tegyük. (Láthatjuk, hogy resourceba újra fel kell vennünk külön néhány termék adatot, nem elég csak 
a terméket resource id-t megadnunk. Kövessük a rendelésben megadott árakat, és figyeljük, hogy mennyibe kerül 
a kiválasztott termék. Az OrderProducts adatai megadásakor figyeljünk arra pl., hogy ha 'stock1'-nek 3 db-ot adunk, 
úgy a 'total' legyen 'stock1' * 'price')

**FONTOS**, hogy az első rendelés felvétele után érdemes a kérdéses bolt adminisztrációs felületen is ellenőriznünk,
 miképp jelenik meg. A rendelésen belül érdemes módosítani a Termékek fül alatt a darabszámot. 
 Amennyiben bekerül plusz "ÁFA" mező és teljesen irreális árak fognak megjelenni, 
 annak az lesz az oka, hogy hiányos az OrderTotal, illetve nem követtük a termék árát az OrderProducts-ban. 

**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/orderProducts</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>
        Accept:application/json<br>
        Content-Type:application/json
    </td>
  </tr>
</table> 

```json

{
    "name": "Bőrnadrág, Mango",
    "sku": "9950000051",
    "modelNumber": null,
    "originalPrice": "18000.0000",
    "price": "18000.0000",
    "total": "18000.0000",
    "taxRate": "27.0000",
    "stock1": "1",
    "stock2": "0",
    "subtractStock": "1",
    "width": "1.0",
    "height": "1.0",
    "length": "1.0",
    "weight": "1.0",
    "order": {
        "id": "b3JkZXItb3JkZXJfaWQ9NDk="
    },
    "product": {
        "id": "cHJvZHVjdC1wcm9kdWN0X2lkPTM3MA=="
    }
}
```

**Response**

```json
{
    "href": "http://shopname.api.shoprenter.hu/orderProducts/b3JkZXJQcm9kdWN0LW9yZGVyX3Byb2R1Y3RfaWQ9MTMw",
    "id": "b3JkZXJQcm9kdWN0LW9yZGVyX3Byb2R1Y3RfaWQ9MTMw",
    "name": "Bőrnadrág, Mango",
    "sku": "9950000051",
    "modelNumber": "",
    "originalPrice": "18000.0000",
    "price": "18000.0000",
    "total": "18000.0000",
    "taxRate": "27.0000",
    "stock1": "1",
    "stock2": "0",
    "stock3": "0",
    "stock4": "0",
    "subtractStock": "1",
    "dateCreated": "2020-11-19T23:32:52",
    "dateUpdated": "2020-11-19T23:32:52",
    "width": "1.00",
    "height": "1.00",
    "length": "1.00",
    "weight": "1.00",
    "order": {
        "href": "http://shopname.api.shoprenter.hu/orders/b3JkZXItb3JkZXJfaWQ9NDk="
    },
    "product": {
        "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTM3MA=="
    },
    "orderProductOptions": {
        "href": "http://shopname.api.shoprenter.hu/orderProductOptions?orderProductId=b3JkZXJQcm9kdWN0LW9yZGVyX3Byb2R1Y3RfaWQ9MTMw"
    }
}
```
## 4. lépés 

Mikor elvégeztünk minden al-resource felvitelével, az [**Order Resource**](../../api/order.md) 
segítségével a "total" értéket módosítjuk, és ezt az alábbi példa alapján tudjuk megtenni:

**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>PUT</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/orders/b3JkZXItb3JkZXJfaWQ9NDk=</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>
        Accept:application/json<br>
        Content-Type:application/json
    </td>
  </tr>
</table> 

```json
{
    "total": "24060.0000"
}
```
**Response**

```json
{
    "href": "http://shopname.api.shoprenter.hu/orders/b3JkZXItb3JkZXJfaWQ9NDk=",
    "id": "b3JkZXItb3JkZXJfaWQ9NDk=",
    "innerId": "49",
    "invoiceId": "0",
    "invoicePrefix": "",
    "firstname": "Fekete",
    "lastname": "Márton",
    "phone": "+36201234567",
    "fax": "",
    "email": "teszt@teszt.com",
    "shippingFirstname": "Teszt",
    "shippingLastname": "Teszt",
    "shippingCompany": "",
    "shippingAddress1": "Teszt út 11",
    "shippingAddress2": "",
    "shippingCity": "Teszt",
    "shippingPostcode": "4033",
    "shippingZoneName": "",
    "shippingCountryName": "Magyarország",
    "shippingAddressFormat": "",
    "shippingMethodName": "Házhozszállítás futárszolgálattal",
    "shippingMethodTaxRate": "25.0000",
    "shippingMethodTaxName": "25 %",
    "shippingMethodExtension": "WSESHIP",
    "shippingReceivingPointId": "0",
    "paymentFirstname": "Teszt",
    "paymentLastname": "Teszt",
    "paymentCompany": "",
    "paymentAddress1": "Teszt út 11",
    "paymentAddress2": "",
    "paymentCity": "Teszt",
    "paymentPostcode": "4033",
    "paymentZoneName": "",
    "paymentCountryName": "Magyarország",
    "paymentAddressFormat": "",
    "paymentMethodName": "Fizetési mód",
    "paymentMethodCode": "COD",
    "paymentMethodTaxRate": "0.0000",
    "paymentMethodTaxName": "",
    "paymentMethodAfter": "1",
    "taxNumber": "",
    "comment": "Megjegyzés",
    "total": "24060.0000",
    "value": "1.00000000",
    "couponTaxRate": "-1.0000",
    "dateCreated": "2020-11-19T23:05:26",
    "dateUpdated": "2020-11-23T17:16:03",
    "ip": "11.11.11.11",
    "pickPackPontShopCode": "100010",
    "loyaltyPointsTaxRate": "-1.0000",
    "customer": {
        "href": "http://shopname.api.shoprenter.hu/customers/Y3VzdG9tZXItY3VzdG9tZXJfaWQ9MQ=="
    },
    "customerGroup": {
        "href": "http://shopname.api.shoprenter.hu/customerGroups/Y3VzdG9tZXJHcm91cC1jdXN0b21lcl9ncm91cF9pZD04"
    },
    "shippingZone": null,
    "shippingCountry": {
        "href": "http://shopname.api.shoprenter.hu/countries/Y291bnRyeS1jb3VudHJ5X2lkPTk3"
    },
    "paymentZone": null,
    "paymentCountry": {
        "href": "http://shopname.api.shoprenter.hu/countries/Y291bnRyeS1jb3VudHJ5X2lkPTk3"
    },
    "orderStatus": {
        "href": "http://shopname.api.shoprenter.hu/orderStatuses/b3JkZXJTdGF0dXMtb3JkZXJfc3RhdHVzX2lkPTE="
    },
    "language": {
        "href": "http://shopname.api.shoprenter.hu/languages/bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ=="
    },
    "currency": {
        "href": "http://shopname.api.shoprenter.hu/currencies/Y3VycmVuY3ktY3VycmVuY3lfaWQ9NA=="
    },
    "shippingMode": {
        "href": "http://shopname.api.shoprenter.hu/shippingModes/c2hpcHBpbmdNb2RlLWlkPTE4"
    },
    "furgefutarWaybill": 0,
    "orderTotals": {
        "href": "http://shopname.api.shoprenter.hu/orderTotals?orderId=b3JkZXItb3JkZXJfaWQ9NDk="
    },
    "orderProducts": {
        "href": "http://shopname.api.shoprenter.hu/orderProducts?orderId=b3JkZXItb3JkZXJfaWQ9NDk="
    },
    "orderGiftWrappings": {
        "href": "http://shopname.api.shoprenter.hu/orderGiftWrappings?orderId=b3JkZXItb3JkZXJfaWQ9NDk="
    }
}
```
