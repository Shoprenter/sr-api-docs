# EmptyBody parameter

In order to reduce bandwidth and improve response times, the API supports an `emptyBody` parameter for `POST` and `PUT` requests. When `emptyBody` parameter is used, the response body will be omitted — except the product endpoints, where the full response body is still returned.

This parameter is especially useful when only the HTTP status code or headers are required, and the actual content is not needed.


**The following examples are only illustrations, therefore the complete API response is not included!**

**For example:**

In case of a coupon list query, we may receive the following result:

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/coupons/[resource id]</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>Accept:application/json</td>
  </tr>
</table>

```json
{
  "href": "http://shopname.api.myshoprenter.hu/coupons/Y291cG9uLWNvdXBvbl9pZD0x",
  "id": "Y291cG9uLWNvdXBvbl9pZD0x",
  "code": "10wevb",
  "discountType": "PERCENT",
  "percentDiscountValue": "10.0000",
  "loginRequired": "0",
  "freeShipping": "1",
  "fixDiscountValue": "0.0000",
  "dateStart": "0000-00-00",
  "dateEnd": "0000-00-00",
  "totalNumberOfCoupons": "100",
  "totalNumberOfCouponsPerCustomer": "1",
  "status": "1",
  "dateCreated": "2013-12-31 11:45:51",
  "dateUpdated": "0000-00-00 00:00:00",
  "email": {},
  "minOrderLimit": "0.00",
  "maxOrderLimit": "0.00",
  "validToSpecialProducts": "1",
  "validWithGiftProducts": "1",
  "validWithBulkDiscount": "1",
  "validWithLoyaltyPoints": "1",
  "targetType": "CATEGORY",
  "taxClass": {
    "href": "http://shopname.api.myshoprenter.hu/taxClasses/dGF4Q2xhc3MtdGF4X2NsYXNzX2lkPTEw"
  },
  "couponDescriptions": {
    "href": "http://shopname.api.myshoprenter.hu/couponDescriptions?couponId=Y291cG9uLWNvdXBvbl9pZD0x"
  }
}
```

In case of non-product endpoints, the same request with `emptyBody=1` would return

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/coupons/[resource id]?emptyBody=1</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>Accept:application/json</td>
  </tr>
</table>

```json
[]
```
No body is returned, but status and headers remain available.

> `emptyBody=1` is ignored for product-related endpoints to ensure compatibility with systems expecting full product data.

Using emptyBody results in leaner API calls when body content is unnecessary.