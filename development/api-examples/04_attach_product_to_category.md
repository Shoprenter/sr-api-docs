# Adding a Product to a Category

The following example demonstrates how to add a newly created product to a newly created category. 
A more efficient batched version of this example with Outer IDs is available within the documentation at this [**link**](../api/04_batch.md#termek-hozzaadasa-kategoriahoz-outer-id-segitsegevel).

The task consists of three steps.
1. Creating a category using the [**Category Extend Resource**](../../api/category_extend.md).
2. Creating a product using the [**Product Extend Resource**](../../api/product_extend.md) and specifying the category during creation.
3. Adding additional categories to the product using the [**Product Category Relation Resource**](../../api/product_category_relation.md) Resource.

## Step 1.

Creating a category using the [**Category Extend Resource**](../../api/category_extend.md).

**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/categoryExtend</td>
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
    "sortOrder": "10",
    "status": "1",
    "productsStatus": "1",
    "picture": "data/category_picture.jpg",
    "categoryDescriptions": [
        {
            "name": "Test Category",
            "language": {
                "id": "bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ=="
            }
        },
        {
            "name": "Test Category",
            "language": {
                "id": "bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9Mg=="
            }
        }
    ],
    "categoryCustomerGroupRelations": [...]
}
```

**Response**

```json
{
    "href": "http://demo.api.aurora.shopname/categoryExtend/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTE5",
    "id": "Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTE5",
    "innerId": "119",
    "picture": "data/category_picture.jpg",
    "sortOrder": "10",
    "status": "1",
    "productsStatus": "1",
    "groupCode": null,
    "dateCreated": "2020-10-21T14:48:22",
    "dateUpdated": "2020-10-21T14:48:22",
    "parentCategory": null,
    "centralCategory": null,
    "categoryDescriptions": [
        {
            "href": "http://demo.api.aurora.shopname/categoryDescriptions/Y2F0ZWdvcnlEZXNjcmlwdGlvbi1jYXRlZ29yeV9pZD0xMTkmbGFuZ3VhZ2VfaWQ9MQ==",
            "id": "Y2F0ZWdvcnlEZXNjcmlwdGlvbi1jYXRlZ29yeV9pZD0xMTkmbGFuZ3VhZ2VfaWQ9MQ==",
            "name": "Test Category",
            "metaKeywords": "",
            "metaDescription": "",
            "description": "",
            "customTitle": null,
            "robotsMetaTag": "0",
            "footerSeoText": null,
            "heading": null,
            "shortDescription": "",
            "category": {
                "href": "http://demo.api.aurora.shopname/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTE5"
            },
            "language": {
                "href": "http://demo.api.aurora.shopname/languages/bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ=="
            }
        },
        {
            "href": "http://demo.api.aurora.shopname/categoryDescriptions/Y2F0ZWdvcnlEZXNjcmlwdGlvbi1jYXRlZ29yeV9pZD0xMTkmbGFuZ3VhZ2VfaWQ9Mg==",
            "id": "Y2F0ZWdvcnlEZXNjcmlwdGlvbi1jYXRlZ29yeV9pZD0xMTkmbGFuZ3VhZ2VfaWQ9Mg==",
            "name": "Test Category",
            "metaKeywords": "",
            "metaDescription": "",
            "description": "",
            "customTitle": null,
            "robotsMetaTag": "0",
            "footerSeoText": null,
            "heading": null,
            "shortDescription": "",
            "category": {
                "href": "http://demo.api.aurora.shopname/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTE5"
            },
            "language": {
                "href": "http://demo.api.aurora.shopname/languages/bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9Mg=="
            }
        }
    ],
    "categoryCustomerGroupRelations": [...],
    "customerGroups": {
        "href": "http://demo.api.aurora.shopname/categoryExtend/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTE5/customerGroups"
    },
    "urlAliases": []
}
```

## Step 2.

Creating a product using the [**Product Extend Resource**](../../api/product_extend.md) and specifying the category during creation

**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/productExtend</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>
        Accept:application/json<br>
        Content-Type:application/json
    </td>
  </tr>
</table>

```json{26-32}
{
    "stock1": "12",
    "stock2": "22",
    "sku": "ABCD-1234",
    "price": "2200",
    "manufacturer": {...},
    "productDescriptions": [
        {
            "name": "Product name",
            "shortDescription": "Short description",
            "description": "Long description",
            "language": {
                "id": "bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ=="
            }
        },
        {
            "name": "Product Name",
            "shortDescription": "Short Description",
            "description": "Long Description",
            "language": {
                "id": "bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9Mg=="
            }
        }
    ],
    "productSpecials": [...],
    "productCategoryRelations": [
        {
            "category": {
                "id": "Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTE5"
            }
        }
    ],
    "productRelatedProductRelations": [...],
    "productProductBadgeRelations": [...],
    "productTags": [...],
    "productCollateralProductRelations": [...],
    "customerGroupProductPrices": [...]
}
```

**Response**

```json{98-109}
{
    "href": "http://shopname.api.myshoprenter.hu/productExtend/cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc=",
    "id": "cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc=",
    "innerId": "1707",
    "sku": "ABCD-1234",
    "modelNumber": {},
    "orderable": "1",
    "price": "2200.0000",
    "multiplier": "1.0000",
    "multiplierLock": "0",
    "loyaltyPoints": {},
    "stock1": "12",
    "stock2": "22",
    "stock3": "0",
    "stock4": "0",
    "subtractStock": "1",
    "mainPicture": "product/ABCD-pic.jpg",
    "width": "0.00",
    "height": "0.00",
    "length": "0.00",
    "weight": "0.00",
    "status": "1",
    "shipped": "1",
    "minimalOrderNumber": "1",
    "maximalOrderNumber": "0",
    "minimalOrderNumberMultiply": "0",
    "availableDate": "0000-00-00",
    "quantity": "0.0000",
    "sortOrder": "0",
    "dateCreated": "2017-10-20T09:25:30",
    "dateUpdated": "2017-10-20T09:25:30",
    "imageAlt": "image alt",
    "freeShipping": "0",
    "productAttributeExtend": [...],
    "productPrices": [...],
    "taxClass": {...},
    "noStockStatus": {...},
    "inStockStatus": {...},
    "productClass": {...},
    "parentProduct": {...},
    "volumeUnit": {...},
    "weightUnit": {...},
    "manufacturer": {...},
    "onlyStock1Status": {...},
    "onlyStock2Status": {...},
    "onlyStock3Status": {...},
    "onlyStock4Status": {...},
    "allImages": {...},
    "productDescriptions": [
        {
            "href": "http://shopname.api.myshoprenter.hu/productDescriptions/cHJvZHVjdERlc2NyaXB0aW9uLXByb2R1Y3RfaWQ9MTcwNyZsYW5ndWFnZV9pZD0x",
            "id": "cHJvZHVjdERlc2NyaXB0aW9uLXByb2R1Y3RfaWQ9MTcwNyZsYW5ndWFnZV9pZD0x",
            "name": "Product name",
            "metaKeywords": {},
            "metaDescription": {},
            "shortDescription": "Short description",
            "description": "Long description",
            "parameters": "Szín: green Size: XL",
            "packagingUnit": {},
            "measurementUnit": "db",
            "customContentTitle": {},
            "customContent": {},
            "dateCreated": "2017-10-20T09:25:30",
            "dateUpdated": "2017-10-20T09:25:30",
            "videoCode": {},
            "product": {
                "href": "http://shopname.api.myshoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc="
            },
            "language": {
                "href": "http://shopname.api.myshoprenter.hu/languages/bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ=="
            }
        },
        {
            "href": "http://shopname.api.myshoprenter.hu/productDescriptions/cHJvZHVjdERlc2NyaXB0aW9uLXByb2R1Y3RfaWQ9MTcwNyZsYW5ndWFnZV9pZD0y",
            "id": "cHJvZHVjdERlc2NyaXB0aW9uLXByb2R1Y3RfaWQ9MTcwNyZsYW5ndWFnZV9pZD0y",
            "name": "Product Name",
            "metaKeywords": {},
            "metaDescription": {},
            "shortDescription": "Short Description",
            "description": "Long Description",
            "parameters": "Color: green Size: XL",
            "packagingUnit": {},
            "measurementUnit": "pc",
            "customContentTitle": {},
            "customContent": {},
            "dateCreated": "2017-10-20T09:25:30",
            "dateUpdated": "2017-10-20T09:25:30",
            "videoCode": {},
            "product": {
                "href": "http://shopname.api.myshoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc="
            },
            "language": {
                "href": "http://shopname.api.myshoprenter.hu/languages/bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9Mg=="
            }
        }
    ],
    "productRelatedProductRelations": [...],
    "productCategoryRelations": [
        {
            "href": "http://shopname.api.myshoprenter.hu/productCategoryRelations/cHJvZHVjdENhdGVnb3J5LXByb2R1Y3RfaWQ9MTcwNyZjYXRlZ29yeV9pZD01Mw==",
            "id": "cHJvZHVjdENhdGVnb3J5LXByb2R1Y3RfaWQ9MTcwNyZjYXRlZ29yeV9pZD01Mw==",
            "product": {
                "href": "http://shopname.api.myshoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc="
            },
            "category": {
                "href": "http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTE5"
            }
        }
    ],
    "productSpecials": [...],
    "productProductBadgeRelations": [...],
    "productListAttributeValueRelations": {...},
    "numberAttributeValues": {...},
    "textAttributeValues": {...},
    "productTags": [...],
    "productCollateralProductRelations": [...],
    "customerGroupProductPrices": [...],
    "relatedProducts": {...},
    "collateralProducts": {...},
    "urlAliases": {...}
}
```

## Step 3.

If you do not specify the category for the product during creation, you can still do so later using the [**Product Category Relation Resource**](../../api/product_category_relation.md) Resource. 
Note that for existing products, you can also add additional categories using the PUT method of the [**Product Extend Resource**](../../api/product_extend.md).

**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/productCategoryRelations</td>
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
    "product": {
        "id": "cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc="
    },
    "category": {
        "id": "Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTE5"
    }
}
```

**Response**

```json
{
    "href": "http://shopname.api.myshoprenter.hu/productCategoryRelations/cHJvZHVjdENhdGVnb3J5LXByb2R1Y3RfaWQ9MTcwNyZjYXRlZ29yeV9pZD0xMTk=",
    "id": "cHJvZHVjdENhdGVnb3J5LXByb2R1Y3RfaWQ9MTcwNyZjYXRlZ29yeV9pZD0xMTk=",
    "product": {
        "href": "http://shopname.api.myshoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc="
    },
    "category": {
        "href": "http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTE5"
    }
}
```
