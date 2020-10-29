# Termék hozzáadása kategóriához

Az alábbi példában bemutatásra kerül, hogy miként lehet egy újonnan létrehozott kategóriához hozzáadni egy újonnan létrehozott terméket.
A dokumentáción belül ennek a példának a hatékonyabb batchelt Outer ID-s változata elérhető ezen a [**linken**](../api/04_batch.md#termék-hozzáadása-kategóriához-outer-id-segítségével)

A feladat 3 lépésből áll.
1. Kategória létrehozása a [**Category Extend Resource**](../../api/category_extend.md) segítségével.
2. Termék létrehozása a [**Product Extend Resource**](../../api/product_extend.md) segítségével, amelyhez már létrehozáskor megadjuk a kategóriát.
3. További kategóriák hozzáadása a termékhez a [**Product Category Relation Resource**](../../api/product_category_relation.md) segítségével.

## 1. lépés

A [**Category Extend Resource**](../../api/category_extend.md) segítségével létrehozzuk az új kategóriát.

**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/categoryExtend</td>
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
            "name": "Teszt Kategória",
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
            "name": "Teszt Kategória",
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

## 2. lépés

A [**Product Extend Resource**](../../api/product_extend.md) segítségével létrehozzuk az új terméket.

**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/productExtend</td>
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
            "name": "Termék Név",
            "shortDescription": "Rövid Leírás",
            "description": "Hosszú Leírás",
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
    "href": "http://shopname.api.shoprenter.hu/productExtend/cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc=",
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
            "href": "http://shopname.api.shoprenter.hu/productDescriptions/cHJvZHVjdERlc2NyaXB0aW9uLXByb2R1Y3RfaWQ9MTcwNyZsYW5ndWFnZV9pZD0x",
            "id": "cHJvZHVjdERlc2NyaXB0aW9uLXByb2R1Y3RfaWQ9MTcwNyZsYW5ndWFnZV9pZD0x",
            "name": "Termék Név",
            "metaKeywords": {},
            "metaDescription": {},
            "shortDescription": "Rövid Leírás",
            "description": "Hosszú Leírás",
            "parameters": "Szín: zöld Méret: XL",
            "packagingUnit": {},
            "measurementUnit": "db",
            "customContentTitle": {},
            "customContent": {},
            "dateCreated": "2017-10-20T09:25:30",
            "dateUpdated": "2017-10-20T09:25:30",
            "videoCode": {},
            "product": {
                "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc="
            },
            "language": {
                "href": "http://shopname.api.shoprenter.hu/languages/bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ=="
            }
        },
        {
            "href": "http://shopname.api.shoprenter.hu/productDescriptions/cHJvZHVjdERlc2NyaXB0aW9uLXByb2R1Y3RfaWQ9MTcwNyZsYW5ndWFnZV9pZD0y",
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
                "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc="
            },
            "language": {
                "href": "http://shopname.api.shoprenter.hu/languages/bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9Mg=="
            }
        }
    ],
    "productRelatedProductRelations": [...],
    "productCategoryRelations": [
        {
            "href": "http://shopname.api.shoprenter.hu/productCategoryRelations/cHJvZHVjdENhdGVnb3J5LXByb2R1Y3RfaWQ9MTcwNyZjYXRlZ29yeV9pZD01Mw==",
            "id": "cHJvZHVjdENhdGVnb3J5LXByb2R1Y3RfaWQ9MTcwNyZjYXRlZ29yeV9pZD01Mw==",
            "product": {
                "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc="
            },
            "category": {
                "href": "http://shopname.api.shoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTE5"
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

## 3. lépés

Amennyiben nem létrehozáskor adjuk meg a kategóriát a termékhez, úgy utólag a [**Product Category Relation Resource**](../../api/product_category_relation.md) segítségével is megtehetjük. (Megjegyzés: Meglévő termékhez további kategóriákat a [**Product Extend Resource**](../../api/product_extend.md) PUT methodjával is meg lehet valósítani.)

**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/productCategoryRelations</td>
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
    "href": "http://shopname.api.shoprenter.hu/productCategoryRelations/cHJvZHVjdENhdGVnb3J5LXByb2R1Y3RfaWQ9MTcwNyZjYXRlZ29yeV9pZD0xMTk=",
    "id": "cHJvZHVjdENhdGVnb3J5LXByb2R1Y3RfaWQ9MTcwNyZjYXRlZ29yeV9pZD0xMTk=",
    "product": {
        "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc="
    },
    "category": {
        "href": "http://shopname.api.shoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTE5"
    }
}
```