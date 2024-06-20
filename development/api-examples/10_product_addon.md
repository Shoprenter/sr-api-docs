# Product Addon
**The following example demonstrates how to create a deposit fee for products.**

**1. Creating a Deposit:** `Product Addon Resource`<br>
- **Function:**  This API Resource allows the creation of deposits in the system.
- **Data:** All necessary data for each deposit is defined here, such as amount, type, VAT.<br>

**2. Linking Deposit with Product:** `Product Addon Product Relation Resource`<br>

- **Function**`: This API Resource is responsible for linking deposits and products.

- **Opportunity:** It allows adding the appropriate deposit to a given product.<br>

## Step 1.

Creating a deposit

**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/productAddons</td>
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
  "sku": "BETETDIJ01",
  "name": "1L Üveg Betétdíj",
  "type": "DEPOSIT_FEE",
  "price": "50.0000",
  "taxRate": "",
  "required": "1",
  "autoScaling": "1",
  "separatedItem": "1",
  "quantityModifiable": "0"
}
```


## Step 2.

Linking Deposit with Product:

**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/productAddonProductRelations/cmVsYXRlZFByb2R1Y3QtcHJvZHVjdF9pZD0yNDUxJnJlbGF0ZWRfaWQ9MzAxMg==</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>
        Accept:application/json<br>
        Content-Type:application/json
    </td>
  </tr>
</table>

**Request**

```json
{
  "product": {
    "id": "cHJvZHVjdC1wcm9kdWN0X2lkPTI0NTE="
  },
  "productAddon": {
    "id": "cHJvZHVjdC1wcm9kdWN0X2lkPTMwMTI="
  }
}
```
