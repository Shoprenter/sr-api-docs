# Termék hozzáadása kategóriához

Az alábbi példában bemutatásra kerül, hogy miként lehet egy újonnan létrehozott kategóriához hozzáadni egy újonnan létrehozott terméket.

A feladat 3 lépésből áll.
1. Kategória létrehozása a [**Category Extend Resource**](../../api/category_extend.md) segítségével
2. Termék létrehozása a [**Product Extend Resource**](../../api/product_extend.md) segítségével
3. Termék hozzáadása a kategóriához a [**Product Category Relation Resource**](../../api/product_category_relation.md) segítségével

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
    "categoryCustomerGroupRelations": [
        {
            "customerGroup": {
                "id": "Y3VzdG9tZXJHcm91cC1jdXN0b21lcl9ncm91cF9pZD02"
            }
        },
        {
            "customerGroup": {
                "id": "Y3VzdG9tZXJHcm91cC1jdXN0b21lcl9ncm91cF9pZD05"
            }
        }
    ]
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
    "categoryCustomerGroupRelations": [
        {
            "href": "http://demo.api.aurora.shopname/categoryCustomerGroupRelations/Y2F0ZWdvcnlDdXN0b21lckdyb3VwLWNhdGVnb3J5X2lkPTExOSZjdXN0b21lcl9ncm91cF9pZD02",
            "id": "Y2F0ZWdvcnlDdXN0b21lckdyb3VwLWNhdGVnb3J5X2lkPTExOSZjdXN0b21lcl9ncm91cF9pZD02",
            "category": {
                "href": "http://demo.api.aurora.shopname/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTE5"
            },
            "customerGroup": {
                "href": "http://demo.api.aurora.shopname/customerGroups/Y3VzdG9tZXJHcm91cC1jdXN0b21lcl9ncm91cF9pZD02"
            }
        },
        {
            "href": "http://demo.api.aurora.shopname/categoryCustomerGroupRelations/Y2F0ZWdvcnlDdXN0b21lckdyb3VwLWNhdGVnb3J5X2lkPTExOSZjdXN0b21lcl9ncm91cF9pZD05",
            "id": "Y2F0ZWdvcnlDdXN0b21lckdyb3VwLWNhdGVnb3J5X2lkPTExOSZjdXN0b21lcl9ncm91cF9pZD05",
            "category": {
                "href": "http://demo.api.aurora.shopname/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTE5"
            },
            "customerGroup": {
                "href": "http://demo.api.aurora.shopname/customerGroups/Y3VzdG9tZXJHcm91cC1jdXN0b21lcl9ncm91cF9pZD05"
            }
        }
    ],
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

```json
{
    "stock1": "12",
    "stock2": "22",
    "sku": "ABCD-1234",
    "price": "2200",
    "manufacturer": {
        "name": "Manufacturer name",
        "picture": "image.jpg",
        "sortOrder": 0,
        "robotsMetaTag": 0
    },
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
    "productSpecials": [
        {
            "price": "1000"
        },
        {
            "price": "2000"
        }
    ],
    "productCategoryRelations": [
        {
            "category": {
                "id": "Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9NTU="
            }
        },
        {
            "category": {
                "id": "Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9NTM="
            }
        },
        {
            "category": {
                "id": "Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9NTQ="
            }
        }
    ],
    "productRelatedProductRelations": [
        {
            "relatedProduct": {
                "id": "cHJvZHVjdC1wcm9kdWN0X2lkPTE0OQ=="
            }
        },
        {
            "relatedProduct": {
                "id": "cHJvZHVjdC1wcm9kdWN0X2lkPTE2MA=="
            }
        },
        {
            "relatedProduct": {
                "id": "cHJvZHVjdC1wcm9kdWN0X2lkPTE2Nw=="
            }
        }
    ],
    "productProductBadgeRelations": [
        {
            "productBadge": {
                "id": "cHJvZHVjdEJhZGdlLWJhZGdlX2lkPTE="
            }
        },
        {
            "productBadge": {
                "id": "cHJvZHVjdEJhZGdlLWJhZGdlX2lkPTM="
            }
        }
    ],
    "productTags": [
        {
            "language": {
                "id": "bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ=="
            },
            "tags": "valami1, valami2, valami3"
        },
        {
            "language": {
                "id": "bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9Mg=="
            },
            "tags": "something1, something2, something3"
        }
    ],
    "productCollateralProductRelations": [
        {
            "collateralProduct": {
                "id": "cHJvZHVjdC1wcm9kdWN0X2lkPTEyMA=="
            }
        },
        {
            "collateralProduct": {
                "id": "cHJvZHVjdC1wcm9kdWN0X2lkPTExOQ=="
            }
        },
        {
            "collateralProduct": {
                "id": "cHJvZHVjdC1wcm9kdWN0X2lkPTExOA=="
            }
        }
    ],
    "customerGroupProductPrices": [
        {
            "customerGroup": {
                "id": "Y3VzdG9tZXJHcm91cC1jdXN0b21lcl9ncm91cF9pZD05"
            },
            "price": "1200"
        },
        {
            "customerGroup": {
                "id": "Y3VzdG9tZXJHcm91cC1jdXN0b21lcl9ncm91cF9pZD02"
            },
            "price": "1500",
            "product": {
                "id": "cHJvZHVjdC1wcm9kdWN0X2lkPTE0OQ=="
            }
        }
    ]
}
```

**Response**

```json
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
    "productAttributeExtend": [
        {
            "href": "http://shopname.api.shoprenter.hu/listAttributes/bGlzdEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9Mg==",
            "id": "bGlzdEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9Mg==",
            "type": "LIST",
            "name": "szin",
            "value": [
                {
                    "value": "Magenta",
                    "language": {
                        "href": "http://shopname.api.shoprenter.hu/languages/bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ==",
                        "id": "bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ=="
                    },
                    "href": "http://shopname.api.shoprenter.hu/listAttributeValueDescriptions/bGlzdEF0dHJpYnV0ZVZhbHVlRGVzY3JpcHRpb24tYXR0cmlidXRlX2lkPTImbGFuZ3VhZ2VfaWQ9MSZ2YWx1ZV9pZD0x",
                    "id": "bGlzdEF0dHJpYnV0ZVZhbHVlRGVzY3JpcHRpb24tYXR0cmlidXRlX2lkPTImbGFuZ3VhZ2VfaWQ9MSZ2YWx1ZV9pZD0x"
                },
                {
                    "value": "Pink",
                    "language": {
                        "href": "http://shopname.api.shoprenter.hu/languages/bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9Mg==",
                        "id": "bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9Mg=="
                    },
                    "href": "http://shopname.api.shoprenter.hu/listAttributeValueDescriptions/bGlzdEF0dHJpYnV0ZVZhbHVlRGVzY3JpcHRpb24tYXR0cmlidXRlX2lkPTImbGFuZ3VhZ2VfaWQ9MiZ2YWx1ZV9pZD0x",
                    "id": "bGlzdEF0dHJpYnV0ZVZhbHVlRGVzY3JpcHRpb24tYXR0cmlidXRlX2lkPTImbGFuZ3VhZ2VfaWQ9MiZ2YWx1ZV9pZD0x"
                }
            ]
        }
    ],
    "productPrices": [
        {
            "customerGroup": {
                "id": "Y3VzdG9tZXJHcm91cC1jdXN0b21lcl9ncm91cF9pZD02",
                "innerId": 6,
                "default": false
            },
            "net": "1900",
            "netOriginal": "1900",
            "netSpecial": null,
            "gross": "2413",
            "grossOriginal": "2413",
            "grossSpecial": null,
            "currencyCode": "HUF"
        },
        {
            "customerGroup": {
                "id": "Y3VzdG9tZXJHcm91cC1jdXN0b21lcl9ncm91cF9pZD04",
                "innerId": 8,
                "default": true
            },
            "net": "1900",
            "netOriginal": "1900",
            "netSpecial": null,
            "gross": "2413",
            "grossOriginal": "2413",
            "grossSpecial": null,
            "currencyCode": "HUF"
        },
        {
            "customerGroup": {
                "id": "Y3VzdG9tZXJHcm91cC1jdXN0b21lcl9ncm91cF9pZD0xMw==",
                "innerId": 13,
                "default": false
            },
            "net": "1710",
            "netOriginal": "1710",
            "netSpecial": null,
            "gross": "2172",
            "grossOriginal": "2172",
            "grossSpecial": null,
            "currencyCode": "HUF"
        }
    ],
    "taxClass": {
        "href": "http://shopname.api.shoprenter.hu/taxClasses/dGF4Q2xhc3MtdGF4X2NsYXNzX2lkPTEw"
    },
    "noStockStatus": {
        "href": "http://shopname.api.shoprenter.hu/stockStatuses/c3RvY2tTdGF0dXMtc3RvY2tfc3RhdHVzX2lkPTU="
    },
    "inStockStatus": {
        "href": "http://shopname.api.shoprenter.hu/stockStatuses/c3RvY2tTdGF0dXMtc3RvY2tfc3RhdHVzX2lkPTk="
    },
    "productClass": {
        "href": "http://shopname.api.shoprenter.hu/productClasses/cHJvZHVjdENsYXNzLXByb2R1Y3RfY2xhc3NfaWQ9MQ=="
    },
    "parentProduct": {
        "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc="
    },
    "volumeUnit": {
        "href": "http://shopname.api.shoprenter.hu/lengthClasses/bGVuZ3RoQ2xhc3MtbGVuZ3RoX2NsYXNzX2lkPTE="
    },
    "weightUnit": {
        "href": "http://shopname.api.shoprenter.hu/weightClasses/d2VpZ2h0Q2xhc3Mtd2VpZ2h0X2NsYXNzX2lkPTE="
    },
    "manufacturer": {
        "href": "http://shopname.api.shoprenter.hu/manufacturers/bWFudWZhY3R1cmVyLW1hbnVmYWN0dXJlcl9pZD0y",
        "id": "bWFudWZhY3R1cmVyLW1hbnVmYWN0dXJlcl9pZD0x",
        "innerId": "1",
        "name": "Manufacturer name",
        "picture": "image.jpg",
        "sortOrder": "0",
        "robotsMetaTag": "0",
        "dateCreated": "2013-08-08T12:30:00",
        "dateUpdated": "2013-08-08T12:30:00",
        "manufacturerDescriptions": {
            "href": "http://shopname.api.shoprenter.hu/manufacturerDescriptions?manufacturerId=bWFudWZhY3R1cmVyLW1hbnVmYWN0dXJlcl9pZD0x"
        }
    },
    "onlyStock1Status": {
        "href": "http://shopname.api.shoprenter.hu/stockStatuses/c3RvY2tTdGF0dXMtc3RvY2tfc3RhdHVzX2lkPTU="
    },
    "onlyStock2Status": {
        "href": "http://shopname.api.shoprenter.hu/stockStatuses/c3RvY2tTdGF0dXMtc3RvY2tfc3RhdHVzX2lkPTk="
    },
    "onlyStock3Status": {
        "href": "http://shopname.api.shoprenter.hu/stockStatuses/c3RvY2tTdGF0dXMtc3RvY2tfc3RhdHVzX2lkPTl="
    },
    "onlyStock4Status": {
        "href": "http://shopname.api.shoprenter.hu/stockStatuses/c3RvY2tTdGF0dXMtc3RvY2tfc3RhdHVzX2lkPTm="
    },
    "allImages": {
        "mainImage": "https://shopname.shoprenter.hu/custom/shopname/image/cache/w460h460wt1/product/main_image.jpg?lastmod=1537961896.1537962288",
        "image1": "https://shopname.shoprenter.hu/custom/shopname/image/cache/w460h460wt1/product/other_image1.jpg?lastmod=1537961896.1537962288"
    },
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
    "productRelatedProductRelations": [
        {
            "href": "http://shopname.api.shoprenter.hu/productRelatedProductRelations/cmVsYXRlZFByb2R1Y3QtcHJvZHVjdF9pZD0xNzA3JnJlbGF0ZWRfaWQ9MTQ5",
            "id": "cmVsYXRlZFByb2R1Y3QtcHJvZHVjdF9pZD0xNzA3JnJlbGF0ZWRfaWQ9MTQ5",
            "product": {
                "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc="
            },
            "relatedProduct": {
                "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE0OQ=="
            }
        },
        {
            "href": "http://shopname.api.shoprenter.hu/productRelatedProductRelations/cmVsYXRlZFByb2R1Y3QtcHJvZHVjdF9pZD0xNzA3JnJlbGF0ZWRfaWQ9MTYw",
            "id": "cmVsYXRlZFByb2R1Y3QtcHJvZHVjdF9pZD0xNzA3JnJlbGF0ZWRfaWQ9MTYw",
            "product": {
                "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc="
            },
            "relatedProduct": {
                "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE2MA=="
            }
        },
        {
            "href": "http://shopname.api.shoprenter.hu/productRelatedProductRelations/cmVsYXRlZFByb2R1Y3QtcHJvZHVjdF9pZD0xNzA3JnJlbGF0ZWRfaWQ9MTY3",
            "id": "cmVsYXRlZFByb2R1Y3QtcHJvZHVjdF9pZD0xNzA3JnJlbGF0ZWRfaWQ9MTY3",
            "product": {
                "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc="
            },
            "relatedProduct": {
                "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE2Nw=="
            }
        }
    ],
    "productCategoryRelations": [
        {
            "href": "http://shopname.api.shoprenter.hu/productCategoryRelations/cHJvZHVjdENhdGVnb3J5LXByb2R1Y3RfaWQ9MTcwNyZjYXRlZ29yeV9pZD01Mw==",
            "id": "cHJvZHVjdENhdGVnb3J5LXByb2R1Y3RfaWQ9MTcwNyZjYXRlZ29yeV9pZD01Mw==",
            "product": {
                "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc="
            },
            "category": {
                "href": "http://shopname.api.shoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9NTM="
            }
        },
        {
            "href": "http://shopname.api.shoprenter.hu/productCategoryRelations/cHJvZHVjdENhdGVnb3J5LXByb2R1Y3RfaWQ9MTcwNyZjYXRlZ29yeV9pZD01NA==",
            "id": "cHJvZHVjdENhdGVnb3J5LXByb2R1Y3RfaWQ9MTcwNyZjYXRlZ29yeV9pZD01NA==",
            "product": {
                "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc="
            },
            "category": {
                "href": "http://shopname.api.shoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9NTQ="
            }
        },
        {
            "href": "http://shopname.api.shoprenter.hu/productCategoryRelations/cHJvZHVjdENhdGVnb3J5LXByb2R1Y3RfaWQ9MTcwNyZjYXRlZ29yeV9pZD01NQ==",
            "id": "cHJvZHVjdENhdGVnb3J5LXByb2R1Y3RfaWQ9MTcwNyZjYXRlZ29yeV9pZD01NQ==",
            "product": {
                "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc="
            },
            "category": {
                "href": "http://shopname.api.shoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9NTU="
            }
        }
    ],
    "productSpecials": [
        {
            "href": "http://shopname.api.shoprenter.hu/productSpecials/cHJvZHVjdFNwZWNpYWwtcHJvZHVjdF9zcGVjaWFsX2lkPTIyNDE=",
            "id": "cHJvZHVjdFNwZWNpYWwtcHJvZHVjdF9zcGVjaWFsX2lkPTIyNDE=",
            "priority": "1",
            "price": "1000.0000",
            "dateFrom": "0000-00-00 00:00:00",
            "dateTo": "0000-00-00 00:00:00",
            "minQuantity": "0",
            "maxQuantity": "0",
            "dateCreated": "2017-10-20T09:25:30",
            "product": {
                "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc="
            },
            "customerGroup": {}
        },
        {
            "href": "http://shopname.api.shoprenter.hu/productSpecials/cHJvZHVjdFNwZWNpYWwtcHJvZHVjdF9zcGVjaWFsX2lkPTIyNDI=",
            "id": "cHJvZHVjdFNwZWNpYWwtcHJvZHVjdF9zcGVjaWFsX2lkPTIyNDI=",
            "priority": "1",
            "price": "2000.0000",
            "dateFrom": "0000-00-00 00:00:00",
            "dateTo": "0000-00-00 00:00:00",
            "minQuantity": "0",
            "maxQuantity": "0",
            "dateCreated": "2017-10-20T09:25:30",
            "product": {
                "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc="
            },
            "customerGroup": {}
        }
    ],
    "productProductBadgeRelations": [
        {
            "href": "http://shopname.api.shoprenter.hu/productProductBadgeRelations/cHJvZHVjdFByb2R1Y3RCYWRnZS1wcm9kdWN0X2lkPTE3MDcmYmFkZ2VfaWQ9MQ==",
            "id": "cHJvZHVjdFByb2R1Y3RCYWRnZS1wcm9kdWN0X2lkPTE3MDcmYmFkZ2VfaWQ9MQ==",
            "product": {
                "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc="
            },
            "productBadge": {
                "href": "http://shopname.api.shoprenter.hu/productBadges/cHJvZHVjdEJhZGdlLWJhZGdlX2lkPTE="
            }
        },
        {
            "href": "http://shopname.api.shoprenter.hu/productProductBadgeRelations/cHJvZHVjdFByb2R1Y3RCYWRnZS1wcm9kdWN0X2lkPTE3MDcmYmFkZ2VfaWQ9Mw==",
            "id": "cHJvZHVjdFByb2R1Y3RCYWRnZS1wcm9kdWN0X2lkPTE3MDcmYmFkZ2VfaWQ9Mw==",
            "product": {
                "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc="
            },
            "productBadge": {
                "href": "http://shopname.api.shoprenter.hu/productBadges/cHJvZHVjdEJhZGdlLWJhZGdlX2lkPTM="
            }
        }
    ],
    "productListAttributeValueRelations": {
        "href": "http://shopname.api.shoprenter.hu/productListAttributeValueRelations?productId=cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc="
    },
    "numberAttributeValues": {
        "href": "http://shopname.api.shoprenter.hu/numberAttributeValues?productId=cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc="
    },
    "textAttributeValues": {
        "href": "http://shopname.api.shoprenter.hu/textAttributeValues?productId=cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc="
    },
    "productTags": [
        {
            "href": "http://shopname.api.shoprenter.hu/productTags/cHJvZHVjdFRhZy1wcm9kdWN0X2lkPTE3MDcmbGFuZ3VhZ2VfaWQ9MQ==",
            "id": "cHJvZHVjdFRhZy1wcm9kdWN0X2lkPTE3MDcmbGFuZ3VhZ2VfaWQ9MQ==",
            "tags": "valami1,valami2,valami3",
            "product": {
                "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc="
            },
            "language": {
                "href": "http://shopname.api.shoprenter.hu/languages/bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ=="
            }
        },
        {
            "href": "http://shopname.api.shoprenter.hu/productTags/cHJvZHVjdFRhZy1wcm9kdWN0X2lkPTE3MDcmbGFuZ3VhZ2VfaWQ9Mg==",
            "id": "cHJvZHVjdFRhZy1wcm9kdWN0X2lkPTE3MDcmbGFuZ3VhZ2VfaWQ9Mg==",
            "tags": "something1,something2,something3",
            "product": {
                "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc="
            },
            "language": {
                "href": "http://shopname.api.shoprenter.hu/languages/bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9Mg=="
            }
        }
    ],
    "productCollateralProductRelations": [
        {
            "href": "http://shopname.api.shoprenter.hu/productCollateralProductRelations/cHJvZHVjdENvbGxhdGVyYWxQcm9kdWN0UmVsYXRpb24tcHJvZHVjdF9pZD0xNzA3JmNvbGxhdGVyYWxfaWQ9MTE4",
            "id": "cHJvZHVjdENvbGxhdGVyYWxQcm9kdWN0UmVsYXRpb24tcHJvZHVjdF9pZD0xNzA3JmNvbGxhdGVyYWxfaWQ9MTE4",
            "product": {
                "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc="
            },
            "collateralProduct": {
                "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTExOA=="
            }
        },
        {
            "href": "http://shopname.api.shoprenter.hu/productCollateralProductRelations/cHJvZHVjdENvbGxhdGVyYWxQcm9kdWN0UmVsYXRpb24tcHJvZHVjdF9pZD0xNzA3JmNvbGxhdGVyYWxfaWQ9MTE5",
            "id": "cHJvZHVjdENvbGxhdGVyYWxQcm9kdWN0UmVsYXRpb24tcHJvZHVjdF9pZD0xNzA3JmNvbGxhdGVyYWxfaWQ9MTE5",
            "product": {
                "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc="
            },
            "collateralProduct": {
                "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTExOQ=="
            }
        },
        {
            "href": "http://shopname.api.shoprenter.hu/productCollateralProductRelations/cHJvZHVjdENvbGxhdGVyYWxQcm9kdWN0UmVsYXRpb24tcHJvZHVjdF9pZD0xNzA3JmNvbGxhdGVyYWxfaWQ9MTIw",
            "id": "cHJvZHVjdENvbGxhdGVyYWxQcm9kdWN0UmVsYXRpb24tcHJvZHVjdF9pZD0xNzA3JmNvbGxhdGVyYWxfaWQ9MTIw",
            "product": {
                "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc="
            },
            "collateralProduct": {
                "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTEyMA=="
            }
        }
    ],
    "customerGroupProductPrices": [
        {
            "href": "http://shopname.api.shoprenter.hu/customerGroupProductPrices/Y3VzdG9tZXJHcm91cFByb2R1Y3RQcmljZS1jdXN0b21lcl9ncm91cF9pZD02JnByb2R1Y3RfaWQ9MTcwNw==",
            "id": "Y3VzdG9tZXJHcm91cFByb2R1Y3RQcmljZS1jdXN0b21lcl9ncm91cF9pZD02JnByb2R1Y3RfaWQ9MTcwNw==",
            "price": "1500.0000",
            "customerGroup": {
                "href": "http://shopname.api.shoprenter.hu/customerGroups/Y3VzdG9tZXJHcm91cC1jdXN0b21lcl9ncm91cF9pZD02"
            },
            "product": {
                "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc="
            }
        },
        {
            "href": "http://shopname.api.shoprenter.hu/customerGroupProductPrices/Y3VzdG9tZXJHcm91cFByb2R1Y3RQcmljZS1jdXN0b21lcl9ncm91cF9pZD05JnByb2R1Y3RfaWQ9MTcwNw==",
            "id": "Y3VzdG9tZXJHcm91cFByb2R1Y3RQcmljZS1jdXN0b21lcl9ncm91cF9pZD05JnByb2R1Y3RfaWQ9MTcwNw==",
            "price": "1200.0000",
            "customerGroup": {
                "href": "http://shopname.api.shoprenter.hu/customerGroups/Y3VzdG9tZXJHcm91cC1jdXN0b21lcl9ncm91cF9pZD05"
            },
            "product": {
                "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc="
            }
        }
    ],
    "relatedProducts": {
        "href": "http://shopname.api.shoprenter.hu/productExtend/cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc=/relatedProducts"
    },
    "collateralProducts": {
        "href": "http://shopname.api.shoprenter.hu/productExtend/cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc=/collateralProducts"
    },
    "urlAliases": {
        "href": "http://shopname.api.shoprenter.hu/urlAliases/dXJsQWxpYXMtdXJsX2FsaWFzX2lkPTYyOA==",
        "id": "dXJsQWxpYXMtdXJsX2FsaWFzX2lkPTYyOA==",
        "type": "PRODUCT",
        "urlAlias": "ABCD_tshirt",
        "urlAliasEntity": {
            "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc="
        }
    }
}
```

## 3. lépés

A [**Product Category Relation Resource**](../../api/product_category_relation.md)  segítségével a terméket hozzáadjuk a kategóriához.

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