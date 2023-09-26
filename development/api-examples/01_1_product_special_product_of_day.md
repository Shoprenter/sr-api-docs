# Product of the day

The example below shows how to add and modify a product as a product of the day.

### Introduction

### Introduction

The management of discount products has already been discussed (see: [**Product Special**](./01_0_product_special.md) example). The product of the day is considered a special discount price, where you can specify which product with a discount price should be highlighted on a given day of the week.
This is specified using the [Product Special Resource](../../api/product_special.md) known for the discount price.
The product of the day can be set on the admin interface of the webshop under **Settings > Appearance > Module settings**. [More information](https://support.shoprenter.hu/hc/hu/articles/215106328-Aj%C3%A1nl%C3%B3-modulok#nap_termeke)

### Add product of the day

Although the product of the day uses the same **Product Special resource** as when we charge discount prices, the request to be sent differs as follows:
- **The value of priority is -1**. The reason for this is that a sale may already be set on a product for the day to be set.
- A **type** field is added, which must be set to `day_spec`.
- A **dayOfWeek** field is added, which must be an integer between 1-7.<br>
  The days of the week:
    - 1 - Monday;
    - 2 - Tuesday;
    - 3 - Wednesday;
    - 4 - Thursday;
    - 5 - Friday;
    - 6 - Saturday;
    - 7 - Sunday.
- The dateFrom field is optional.
- It is not mandatory to enter the dateTo field.
- The minQuantity field is optional.
- The maxQuantity field is optional.
- It is not mandatory to enter the customerGroup field.

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
    "priority": -1,
    "price": 1000.0000,
    "product": {
        "id": "cHJvZHVjdC1wcm9kdWN0X2lkPTE2OQ=="
    },
    "type": "day_spec",
    "dayOfWeek": 4
}
```

#### Response

```json
{
    "href": "http://shopname.api.myshoprenter.hu/productSpecials/cHJvZHVjdFNwZWNpYWwtcHJvZHVjdF9zcGVjaWFsX2lkPTg4",
    "id": "cHJvZHVjdFNwZWNpYWwtcHJvZHVjdF9zcGVjaWFsX2lkPTg4",
    "priority": "-1",
    "price": "1000.0000",
    "dateFrom": "0000-00-00 00:00:00",
    "dateTo": "0000-00-00 00:00:00",
    "minQuantity": "0",
    "maxQuantity": "0",
    "dateCreated": "2019-09-12T13:04:33",
    "type": "day_spec",
    "dayOfWeek": "4",
    "product": {
        "href": "http://shopname.api.myshoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE2OQ=="
    },
    "customerGroup": null
}
```

### Change product of the day

In case of modification, the identifier of the product resource must be entered as a mandatory element next to the fields to be modified.
If we want to change the customer group to the "Everyone" customer group, it is worth first deleting the product of the day and creating a new one. Modifications can be made for all other customer groups.
 
### Example

#### Request

<table>
  <tr>
    <td><b>method:</b></td>
    <td>PUT</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/productSpecials/[ProductSpecialResourceID]</td>
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
    "price": 900.0000,
    "dayOfWeek": 5,
    "product": {
        "id": "cHJvZHVjdC1wcm9kdWN0X2lkPTE2OQ"
    }
}
```

#### Response

```json
{
    "href": "http://shopname.api.myshoprenter.hu/productSpecials/cHJvZHVjdFNwZWNpYWwtcHJvZHVjdF9zcGVjaWFsX2lkPTg4",
    "id": "cHJvZHVjdFNwZWNpYWwtcHJvZHVjdF9zcGVjaWFsX2lkPTg4",
    "priority": "-1",
    "price": 900.0000,
    "dateFrom": "0000-00-00 00:00:00",
    "dateTo": "0000-00-00 00:00:00",
    "minQuantity": "0",
    "maxQuantity": "0",
    "dateCreated": "2019-09-12T13:04:33",
    "type": "day_spec",
    "dayOfWeek": 5,
    "product": {
        "href": "http://shopname.api.myshoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE2OQ=="
    },
    "customerGroup": null
}
```
