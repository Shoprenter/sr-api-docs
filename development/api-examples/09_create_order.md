# Order creating

The example below shows how to place an order using the Shoprenter API.

The task consists of the following steps:

1. Create an order using [**Order Resource**](../../api/order.md).
2. Add more items using [**Order Total**](../../api/order_total.md)
3. Add ordered products using [**Order Product**](../../api/order_product.md)
4. Changing the total value of an order using [**Order Resource**](../../api/order.md)

## Step 1.

We create the new order using [**Order Resource**](../../api/order.md).
Here we must pay attention to the fact that the order must already be added at this time
- Language [Language Resource](../../api/language.md) resource id
- Currency [Currency Resource](../../api/currency.md) resource id
- Order status [Order Status Resource](../../api/order_status.md) resource id
- When attaching the shipping mode [Shipping Mode Extend Resource](../../api/shipping_mode_extend.md), make sure
  to specify the correct shippingMethodName
- Customer and customer group [Customer Extend Resource](../../api/customer_extend.md)
  and [Customer Group Resource](../../api/customer_group.md). (If it is a registered customer
  in this case, the
  customer ID and customerGroup ID. If you are not registered, it is not necessary.
- the total value should be entered as 0 and when all steps have been completed, enter the Gross total afterwards,
  because it is possible that this value changes when we are done with each step.
- It is not absolutely necessary to add the "total" field here. When all sub-resources belonging to the order are specified
  and we have the exact total amount of the order, then we will add it to the order.
 
**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/orders</td>
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
    "firstname": "Test",
    "lastname": "Test",
    "phone": "+36201234567",
    "fax": null,
    "email": "test@test.com",
    "shippingFirstname": "Test",
    "shippingLastname": "Test",
    "shippingCompany": null,
    "shippingAddress1": "Test street 11",
    "shippingAddress2": null,
    "shippingCity": "Test",
    "shippingPostcode": "4033",
    "shippingZoneName": null,
    "shippingCountryName": "Hungary",
    "shippingAddressFormat": null,
    "shippingMethodName": "Home delivery with courier service",
    "shippingMethodTaxRate": "27.0000",
    "shippingMethodTaxName": "27 %",
    "shippingMethodExtension": "WSESHIP",
    "shippingReceivingPointId": "0",
    "paymentFirstname": "Test",
    "paymentLastname": "Test",
    "paymentCompany": null,
    "paymentAddress1": "Test street 11",
    "paymentAddress2": null,
    "paymentCity": "Test",
    "paymentPostcode": "4033",
    "paymentZoneName": null,
    "paymentCountryName": "Hungary",
    "paymentAddressFormat": null,
    "paymentMethodName": "Payment method",
    "paymentMethodCode": "COD",
    "paymentMethodTaxRate": "0.0000",
    "paymentMethodTaxName": null,
    "paymentMethodAfter": "1",
    "comment": "Comment",
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
    "href": "http://shopname.api.myshoprenter.hu/orders/b3JkZXItb3JkZXJfaWQ9NDk=",
    "id": "b3JkZXItb3JkZXJfaWQ9NDk=",
    "innerId": "49",
    "invoiceId": "0",
    "invoicePrefix": "",
    "firstname": "Fekete",
    "lastname": "Márton",
    "phone": "+36201234567",
    "fax": "",
    "email": "test@test.com",
    "shippingFirstname": "Test",
    "shippingLastname": "Test",
    "shippingCompany": "",
    "shippingAddress1": "Test street 11",
    "shippingAddress2": "",
    "shippingCity": "Test",
    "shippingPostcode": "4033",
    "shippingZoneName": "",
    "shippingCountryName": "Hungary",
    "shippingAddressFormat": "",
    "shippingMethodName": "Home delivery with courier service",
    "shippingMethodTaxRate": "27.0000",
    "shippingMethodTaxName": "27 %",
    "shippingMethodExtension": "WSESHIP",
    "shippingReceivingPointId": "0",
    "paymentFirstname": "Test",
    "paymentLastname": "Test",
    "paymentCompany": "",
    "paymentAddress1": "Test street 11",
    "paymentAddress2": "",
    "paymentCity": "Test",
    "paymentPostcode": "4033",
    "paymentZoneName": "",
    "paymentCountryName": "Hungary",
    "paymentAddressFormat": "",
    "paymentMethodName": "Payment method",
    "paymentMethodCode": "COD",
    "paymentMethodTaxRate": "0.0000",
    "paymentMethodTaxName": "",
    "paymentMethodAfter": "1",
    "taxNumber": "",
    "comment": "Comment",
    "total": "24060.0000",
    "value": "1.00000000",
    "couponTaxRate": "-1.0000",
    "dateCreated": "2020-11-19T23:05:26",
    "dateUpdated": "2020-11-19T23:05:26",
    "ip": "11.11.11.11",
    "pickPackPontShopCode": "100010",
    "loyaltyPointsTaxRate": "-1.0000",
    "customer": {
        "href": "http://shopname.api.myshoprenter.hu/customers/Y3VzdG9tZXItY3VzdG9tZXJfaWQ9MQ=="
    },
    "customerGroup": {
        "href": "http://shopname.api.myshoprenter.hu/customerGroups/Y3VzdG9tZXJHcm91cC1jdXN0b21lcl9ncm91cF9pZD04"
    },
    "shippingZone": null,
    "shippingCountry": {
        "href": "http://shopname.api.myshoprenter.hu/countries/Y291bnRyeS1jb3VudHJ5X2lkPTk3"
    },
    "paymentZone": null,
    "paymentCountry": {
        "href": "http://shopname.api.myshoprenter.hu/countries/Y291bnRyeS1jb3VudHJ5X2lkPTk3"
    },
    "orderStatus": {
        "href": "http://shopname.api.myshoprenter.hu/orderStatuses/b3JkZXJTdGF0dXMtb3JkZXJfc3RhdHVzX2lkPTE="
    },
    "language": {
        "href": "http://shopname.api.myshoprenter.hu/languages/bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ=="
    },
    "currency": {
        "href": "http://shopname.api.myshoprenter.hu/currencies/Y3VycmVuY3ktY3VycmVuY3lfaWQ9NA=="
    },
    "shippingMode": {
        "href": "http://shopname.api.myshoprenter.hu/shippingModes/c2hpcHBpbmdNb2RlLWlkPTE4"
    },
    "furgefutarWaybill": 0,
    "orderTotals": {
        "href": "http://shopname.api.myshoprenter.hu/orderTotals?orderId=b3JkZXItb3JkZXJfaWQ9NDk="
    },
    "orderProducts": {
        "href": "http://shopname.api.myshoprenter.hu/orderProducts?orderId=b3JkZXItb3JkZXJfaWQ9NDk="
    },
    "orderGiftWrappings": {
        "href": "http://shopname.api.myshoprenter.hu/orderGiftWrappings?orderId=b3JkZXItb3JkZXJfaWQ9NDk="
    }
}
```

## Step 2

In order for the order to appear within the admin interface in the Shop > Orders list, the following type [**Order Total**](../../api/order_total.md) must exist:
- "SUB_TOTAL" type value, which corresponds to the Net subtotal
- "TAX" type value, which corresponds to the VAT value
- "SUB_TOTAL_WITH_TAX" type value, which corresponds to the Gross subtotal
- "SHIPPING" type value, which corresponds to the Shipping fee
- "TOTAL" type value, which corresponds to the Gross final amount

In [**Order Total**](../../api/order_total.md) we can specify with the sortOrder property that the recorded [**Order Total**](.. /../api/order_total.md) resource.
The values specified in [**Order Total**](../../api/order_total.md) are not calculated automatically, so they must be entered manually.


The following example will help you determine what kind of request we should send in the case of "Net partial amount":

**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/orderTotals</td>
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
    "name": "Net partial amount:",
    "valueText": "18.000 Huf ",
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
    "href": "http://shopname.api.myshoprenter.hu/orderTotals/b3JkZXJUb3RhbC1vcmRlcl90b3RhbF9pZD02NjQ=",
    "id": "b3JkZXJUb3RhbC1vcmRlcl90b3RhbF9pZD02NjQ=",
    "name": "Net partial amount:",
    "valueText": "18.000 Huf ",
    "value": "18000.0000",
    "sortOrder": "3",
    "type": "",
    "key": "",
    "description": "",
    "dateCreated": "2020-11-19T23:22:46",
    "dateUpdated": "2020-11-19T23:22:46",
    "order": {
        "href": "http://shopname.api.myshoprenter.hu/orders/b3JkZXItb3JkZXJfaWQ9NDk="
    }
}
```

The following example will help you determine what kind of request we should enter in the case of "VAT (27%):":
 
**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/orderTotals</td>
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
    "name": "VAT (27%): ",
    "valueText": " 4.860 HUF ",
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
    "href": "http://shopname.api.myshoprenter.hu/orderTotals/b3JkZXJUb3RhbC1vcmRlcl90b3RhbF9pZD02NjU=",
    "id": "b3JkZXJUb3RhbC1vcmRlcl90b3RhbF9pZD02NjU=",
    "name": "VAT (27%): ",
    "valueText": " 4.860 Huf ",
    "value": "4860.0000",
    "sortOrder": "4",
    "type": "TAX",
    "key": "",
    "description": "",
    "dateCreated": "2020-11-19T23:23:46",
    "dateUpdated": "2020-11-19T23:23:46",
    "order": {
        "href": "http://shopname.api.myshoprenter.hu/orders/b3JkZXItb3JkZXJfaWQ9NDk="
    }
}
```

The following example will help you determine what kind of request we should send in the case of "Gross partial amount:":

**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/orderTotals</td>
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
    "name": "Gross partial amount:",
    "valueText": "22.860 Huf",
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
    "href": "http://shopname.api.myshoprenter.hu/orderTotals/b3JkZXJUb3RhbC1vcmRlcl90b3RhbF9pZD02NjY=",
    "id": "b3JkZXJUb3RhbC1vcmRlcl90b3RhbF9pZD02NjY=",
    "name": "Gross partial amount:",
    "valueText": "22.860 Huf",
    "value": "22860.0000",
    "sortOrder": "5",
    "type": "SUB_TOTAL_WITH_TAX",
    "key": "",
    "description": "",
    "dateCreated": "2020-11-19T23:24:59",
    "dateUpdated": "2020-11-19T23:24:59",
    "order": {
        "href": "http://shopname.api.myshoprenter.hu/orders/b3JkZXItb3JkZXJfaWQ9NDk="
    }
}
```

The following example will help you with what kind of request we should send in the case of "Home delivery with courier service:":

**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/orderTotals</td>
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
    "name": "Home delivery with courier service:",
    "valueText": "1.200 Huf",
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
    "href": "http://shopname.api.myshoprenter.hu/orderTotals/b3JkZXJUb3RhbC1vcmRlcl90b3RhbF9pZD02Njc=",
    "id": "b3JkZXJUb3RhbC1vcmRlcl90b3RhbF9pZD02Njc=",
    "name": "Home delivery with courier service:",
    "valueText": "1.200 Huf",
    "value": "1200.0000",
    "sortOrder": "6",
    "type": "SHIPPING",
    "key": "",
    "description": "",
    "dateCreated": "2020-11-19T23:27:05",
    "dateUpdated": "2020-11-19T23:27:05",
    "order": {
        "href": "http://shopname.api.myshoprenter.hu/orders/b3JkZXItb3JkZXJfaWQ9NDk="
    }
}
```

The following example will help you determine what kind of request we should enter in the case of "Gross total:":

**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/orderTotals</td>
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
    "name": "Gross total:",
    "valueText": "24060 Huf",
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
    "href": "http://shopname.api.myshoprenter.hu/orderTotals/b3JkZXJUb3RhbC1vcmRlcl90b3RhbF9pZD02NjM=",
    "id": "b3JkZXJUb3RhbC1vcmRlcl90b3RhbF9pZD02NjM=",
    "name": "Gross total:",
    "valueText": "24060 Huf",
    "value": "24060.0000",
    "sortOrder": "7",
    "type": "TOTAL",
    "key": "",
    "description": "",
    "dateCreated": "2020-11-19T23:19:24",
    "dateUpdated": "2020-11-19T23:19:24",
    "order": {
        "href": "http://shopname.api.myshoprenter.hu/orders/b3JkZXItb3JkZXJfaWQ9NDk="
    }
}
```

## Step 3

Combine any product with your order. This [**Order Product Resource**](../../api/order_product.md)
do it with resource. (We can see that we have to re-add some product data separately to the resource, it's not enough
we must specify the resource id of the product) Follow the prices specified in the order and watch how much it costs
the selected product. When entering the data of OrderProducts, pay attention to, for example, that if we add 3 pcs to 'stock1',
so 'total' should be 'stock1' * 'price'

**IMPORTANT** that after placing the first order, we should also check the administration interface of the store in question,
how it appears. Within the order, it is worth changing the number of pieces under the Products tab.
If an additional "VAT" field is entered and completely unrealistic prices will appear,
the reason will be that the OrderTotal is incomplete or that we did not track the price of the product in OrderProducts.

**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/orderProducts</td>
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
    "href": "http://shopname.api.myshoprenter.hu/orderProducts/b3JkZXJQcm9kdWN0LW9yZGVyX3Byb2R1Y3RfaWQ9MTMw",
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
        "href": "http://shopname.api.myshoprenter.hu/orders/b3JkZXItb3JkZXJfaWQ9NDk="
    },
    "product": {
        "href": "http://shopname.api.myshoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTM3MA=="
    },
    "orderProductOptions": {
        "href": "http://shopname.api.myshoprenter.hu/orderProductOptions?orderProductId=b3JkZXJQcm9kdWN0LW9yZGVyX3Byb2R1Y3RfaWQ9MTMw"
    }
}
```

## Step 4

When we are done adding all sub-resources, [**Order Resource**](../../api/order.md)
change the "total" value using the following example:

**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>PUT</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/orders/b3JkZXItb3JkZXJfaWQ9NDk=</td>
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
    "href": "http://shopname.api.myshoprenter.hu/orders/b3JkZXItb3JkZXJfaWQ9NDk=",
    "id": "b3JkZXItb3JkZXJfaWQ9NDk=",
    "innerId": "49",
    "invoiceId": "0",
    "invoicePrefix": "",
    "firstname": "Fekete",
    "lastname": "Márton",
    "phone": "+36201234567",
    "fax": "",
    "email": "test@test.com",
    "shippingFirstname": "Test",
    "shippingLastname": "Test",
    "shippingCompany": "",
    "shippingAddress1": "Test street 11",
    "shippingAddress2": "",
    "shippingCity": "Test",
    "shippingPostcode": "4033",
    "shippingZoneName": "",
    "shippingCountryName": "Hungary",
    "shippingAddressFormat": "",
    "shippingMethodName": "Home delivery with courier service",
    "shippingMethodTaxRate": "25.0000",
    "shippingMethodTaxName": "25 %",
    "shippingMethodExtension": "WSESHIP",
    "shippingReceivingPointId": "0",
    "paymentFirstname": "Test",
    "paymentLastname": "Test",
    "paymentCompany": "",
    "paymentAddress1": "Test street 11",
    "paymentAddress2": "",
    "paymentCity": "Test",
    "paymentPostcode": "4033",
    "paymentZoneName": "",
    "paymentCountryName": "Hungary",
    "paymentAddressFormat": "",
    "paymentMethodName": "Payment method",
    "paymentMethodCode": "COD",
    "paymentMethodTaxRate": "0.0000",
    "paymentMethodTaxName": "",
    "paymentMethodAfter": "1",
    "taxNumber": "",
    "comment": "Comment",
    "total": "24060.0000",
    "value": "1.00000000",
    "couponTaxRate": "-1.0000",
    "dateCreated": "2020-11-19T23:05:26",
    "dateUpdated": "2020-11-23T17:16:03",
    "ip": "11.11.11.11",
    "pickPackPontShopCode": "100010",
    "loyaltyPointsTaxRate": "-1.0000",
    "customer": {
        "href": "http://shopname.api.myshoprenter.hu/customers/Y3VzdG9tZXItY3VzdG9tZXJfaWQ9MQ=="
    },
    "customerGroup": {
        "href": "http://shopname.api.myshoprenter.hu/customerGroups/Y3VzdG9tZXJHcm91cC1jdXN0b21lcl9ncm91cF9pZD04"
    },
    "shippingZone": null,
    "shippingCountry": {
        "href": "http://shopname.api.myshoprenter.hu/countries/Y291bnRyeS1jb3VudHJ5X2lkPTk3"
    },
    "paymentZone": null,
    "paymentCountry": {
        "href": "http://shopname.api.myshoprenter.hu/countries/Y291bnRyeS1jb3VudHJ5X2lkPTk3"
    },
    "orderStatus": {
        "href": "http://shopname.api.myshoprenter.hu/orderStatuses/b3JkZXJTdGF0dXMtb3JkZXJfc3RhdHVzX2lkPTE="
    },
    "language": {
        "href": "http://shopname.api.myshoprenter.hu/languages/bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ=="
    },
    "currency": {
        "href": "http://shopname.api.myshoprenter.hu/currencies/Y3VycmVuY3ktY3VycmVuY3lfaWQ9NA=="
    },
    "shippingMode": {
        "href": "http://shopname.api.myshoprenter.hu/shippingModes/c2hpcHBpbmdNb2RlLWlkPTE4"
    },
    "furgefutarWaybill": 0,
    "orderTotals": {
        "href": "http://shopname.api.myshoprenter.hu/orderTotals?orderId=b3JkZXItb3JkZXJfaWQ9NDk="
    },
    "orderProducts": {
        "href": "http://shopname.api.myshoprenter.hu/orderProducts?orderId=b3JkZXItb3JkZXJfaWQ9NDk="
    },
    "orderGiftWrappings": {
        "href": "http://shopname.api.myshoprenter.hu/orderGiftWrappings?orderId=b3JkZXItb3JkZXJfaWQ9NDk="
    }
}
```
