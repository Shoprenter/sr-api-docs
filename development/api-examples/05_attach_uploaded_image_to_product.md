# Termékkép hozzáadása termékhez

Az alábbi példában bemutatásra kerül, hogy miként lehet egy újonnan létrehozott termékhez elsődleges fő termékképet illetve további termékképeket hozzáadni. 

A feladat 3 lépésből áll.
1. Fájl feltöltése a [**File Resource**](../../api/file.md) segítségével.
2. Termék létrehozása a [**Product Extend Resource**](../../api/product_extend.md) segítségével, amelyhez már létrehozáskor megadjuk az elsődleges fő termékképet.
3. További termékképek hozzáadása a termékhez a [**Product Image Resource**](../../api/product_image.md) segítségével.

## 1. lépés

A [**File Resource**](../../api/file.md) segítségével feltöltjük az elsődleges fő termékképet. Mivel a képet a terméknek szeretnénk beállítani, így fontos, hogy a **filePath property az alábbi alakú legyen "product\/[kép neve]", pl: "filePath": "product\/termekkep.jpg"**. Továbbá a kép fájlformátumának a jpg kiterjesztést javasoljuk. A képet base64-elve kell elküldeni.

**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/files</td>
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
	"data": {
	    "filePath": "product\/image.jpg",
	    "type": "image",
	    "attachment": "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"
	}
}
```

**Response**

```json
{
    "filePath": "product/image.jpg",
    "type": "image"
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

```json{5}
{
    "stock1": "12",
    "stock2": "22",
    "sku": "ABCD-1234",
    "price": "2200",
    "mainPicture": "product\/image.jpg",
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

```json{16}
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
    "mainPicture": "product\/image.jpg",
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

## 3.lépés

A termékhez tartozó további termékképek csatolását a [**Product Image Resource**](../../api/product_image.md) segítségével lehet megvalósítani.

**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/productImages</td>
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
    "imagePath": "product\/image.jpg",
    "sortOrder": "1",
    "product": {
        "id": "cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc="
    }
}
```

**Response**

```json
{
    "href": "http://shopname.api.shoprenter.hu/productImages/cHJvZHVjdEltYWdlLXByb2R1Y3RfaW1hZ2VfaWQ9MQ==",
    "id": "cHJvZHVjdEltYWdlLXByb2R1Y3RfaW1hZ2VfaWQ9MQ==",
    "imagePath": "product\/image.jpg",
    "imageAlt": "Image Alt",
    "sortOrder": "1",
    "product": {
        "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc="
    }
}
```



