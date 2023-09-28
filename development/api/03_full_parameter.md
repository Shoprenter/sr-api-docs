# Full parameter

Starting further API request to process the received link-list in order to get the data that belongs to the Resource is a recurring task during queries from the Resources.

**The following examples are only illustrations, therefore the complete API response is not included!**

**For example:**

In case of a product list query, we may receive the following result:

<table>
  <tr>
    <td><b>method:</b></td>
    <td>GET</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/products</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>Accept:application/json</td>
  </tr>
</table>

```json
{
  "response": {
    "items": [
      {
        "href": "http://shopname.api.myshoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTQ5"
      },
      {
        "href": "http://shopname.api.myshoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTUw"
      }
    ]
  }
}
```
All Resources have a parameter called **full** in order to decrease the number of API requests in case of GET requests.

The content of the invited links will appear instead of the link-list by using `full=1` parameter.

<table>
  <tr>
    <td><b>method:</b></td>
    <td>GET</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/products?full=1</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>Accept:application/json</td>
  </tr>
</table>

```json
{
  "response": {
    "items": [
      {
        "href": "http://shopname.api.myshoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTQ5",
        "id": "cHJvZHVjdC1wcm9kdWN0X2lkPTQ5",
        "innerId": "49",
        "sku": "9789639884328"
      },
      {
        "href": "http://shopname.api.myshoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTQ5",
        "id": "cHJvZHVjdC1wcm9kdWN0X2lkPTQ5",
        "innerId": "49",
        "sku": "9789639884328"
      }
    ]
  }
}
```
The usage of this parameter results in a faster and more transparent code.
