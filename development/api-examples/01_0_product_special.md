# Sale product

The following example shows how to assign, modify and delete a discount price for a product.

## Add discount price

A discount price for a product can be specified using [**Product Special Resource**](../../api/product_special.md).
When posting, we need the resource ID of the previously uploaded product ([**Product Resource**](../../api/product.md)),
and to the resource ID of the customer group ([**Customer Group Resource**](../../api/customer_group.md)) to whom we want to provide the promotion.
It is only necessary to enter a number higher than 0 for the value of the minimum quantity and maximum quantity if a quantity discount is set.

**Note:** Product of the day is considered a special sale price (see more in the example [**Product of day**](./01_1_product_special_product_of_day.md))

### Example

#### Request

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/productSpecials</td>
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
    "priority": "1",
    "price": "1000.0000",
    "dateFrom": "2020-11-01",
    "dateTo": "2022-11-15",
    "minQuantity": "0",
    "maxQuantity": "100",
    "product": {
        "id": "cHJvZHVjdC1wcm9kdWN0X2lkPTE2OQ=="
    },
    "customerGroup": {
        "id": "Y3VzdG9tZXJHcm91cC1jdXN0b21lcl9ncm91cF9pZD04"
    }
}
```

#### Response

```json
{
    "href": "http://demo.api.aurora.ballapeter/productSpecials/cHJvZHVjdFNwZWNpYWwtcHJvZHVjdF9zcGVjaWFsX2lkPTEwOQ==",
    "id": "cHJvZHVjdFNwZWNpYWwtcHJvZHVjdF9zcGVjaWFsX2lkPTEwOQ==",
    "priority": "1",
    "price": "1000.0000",
    "dateFrom": "2020-11-01 00:00:00",
    "dateTo": "2022-11-15 00:00:00",
    "minQuantity": "0",
    "maxQuantity": "100",
    "dateCreated": "2020-10-26T10:30:26",
    "type": "interval",
    "dayOfWeek": null,
    "product": {
        "href": "http://demo.api.aurora.ballapeter/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE2OQ=="
    },
    "customerGroup": {
        "href": "http://demo.api.aurora.ballapeter/customerGroups/Y3VzdG9tZXJHcm91cC1jdXN0b21lcl9ncm91cF9pZD04"
    }
}
```

## Modification of promotional price

To change a special price, we will need the resource ID of the previously entered special price.
If we want to change the customer group to "Everyone" customer group, it is worth deleting the action first and creating a new one. Modifications can be made for all other customer groups.

### Example

#### Request

<table>
  <tr>
    <td><b>method:</b></td>
    <td>PUT</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/productSpecials/product_special_id</td>
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
    "priority": "1",
    "price": "2000.0000",
    "dateFrom": "2020-11-01",
    "dateTo": "2020-11-10",
    "minQuantity": "0",
    "maxQuantity": "100",
    "product": {
        "id": "cHJvZHVjdC1wcm9kdWN0X2lkPTE2OQ=="
    },
    "customerGroup": {
        "id": "Y3VzdG9tZXJHcm91cC1jdXN0b21lcl9ncm91cF9pZD04"
    }
}
```

#### Response

```json
{
    "href": "http://demo.api.aurora.ballapeter/productSpecials/cHJvZHVjdFNwZWNpYWwtcHJvZHVjdF9zcGVjaWFsX2lkPTEwOQ==",
    "id": "cHJvZHVjdFNwZWNpYWwtcHJvZHVjdF9zcGVjaWFsX2lkPTEwOQ==",
    "priority": "1",
    "price": "2000.0000",
    "dateFrom": "2020-11-01 00:00:00",
    "dateTo": "2020-11-10 00:00:00",
    "minQuantity": "0",
    "maxQuantity": "100",
    "dateCreated": "2020-10-26T10:30:26",
    "type": "interval",
    "dayOfWeek": null,
    "product": {
        "href": "http://demo.api.aurora.ballapeter/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE2OQ=="
    },
    "customerGroup": {
        "href": "http://demo.api.aurora.ballapeter/customerGroups/Y3VzdG9tZXJHcm91cC1jdXN0b21lcl9ncm91cF9pZD04"
    }
}
```

## Delete special price

To delete a special price, we will need the resource identifier of the previously entered special price.

### Example

#### Request

<table>
  <tr>
    <td><b>method:</b></td>
    <td>DELETE</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/productSpecials/product_special_id</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>
        Accept:application/json<br>
        Content-Type:application/json
    </td>
  </tr>
</table>
