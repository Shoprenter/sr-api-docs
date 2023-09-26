# Attach image to product

The example below shows how to add a primary main product image and additional product images to a newly created product.

An example for uploading a file can be found at the [link] below (https://support.shoprenter.hu/hc/hu/articles/215106038-F%C3%A1jlok-felt%C3%B6lt%C3%A9se-%C3%A9s-kezel%C3 %A9se) can be read.

The task consists of 3 steps.
1. Upload a file using [**File Resource**](../../api/file.md).
2. Create a product using [**Product Extend Resource**](../../api/product_extend.md), for which we already specify the primary main product image during creation.
3. Add additional product images to the product using [**Product Image Resource**](../../api/product_image.md).

## Step 1.

We use [**File Resource**](../../api/file.md) to upload the primary main product image. Since we want to set the image as the product, it is important that the **filePath property has the following form "product\/[image name]", eg: "filePath": "product\/termekkep.jpg"**. We also recommend the jpg extension for the image file format. The image must be sent in base64.
After uploading, the product image can be found on the admin interface in the Filemanager in the product folder.

**filePath**: <strong>ATTENTION!</strong> The files to be uploaded can only contain the letters of the English ABC and (),_,-, characters and numbers!

**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/files</td>
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
    "filePath": "product\/mainPicture.jpg",
    "type": "image",
    "attachment": "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"
}
```

**Response**

```json
{
    "filePath": "product/mainPicture.jpg",
    "type": "image"
}
```

## Step 2

We create the new product using [**Product Extend Resource**](../../api/product_extend.md).

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

```json{6}
{
    "stock1": "12",
    "stock2": "22",
    "sku": "ABCD-1234",
    "price": "2200",
    "mainPicture": "product\/mainPicture.jpg",
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
    "productCategoryRelations": [...],
    "productRelatedProductRelations": [...],
    "productProductBadgeRelations": [...],
    "productTags": [...],
    "productCollateralProductRelations": [...],
    "customerGroupProductPrices": [...]
}
```

**Response**

```json{17}
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
    "mainPicture": "product\/mainPicture.jpg",
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
    "allImages": {
        "mainImage": "https://shopname.shoprenter.hu/custom/shopname/image/cache/w460h460wt1/product/mainPicture.jpg?lastmod=1537961896.1537962288",
        "image1": "https://shopname.shoprenter.hu/custom/shopname/image/cache/w460h460wt1/product/other_image1.jpg?lastmod=1537961896.1537962288"
    },
    "productDescriptions": [
        {
            "href": "http://shopname.api.myshoprenter.hu/productDescriptions/cHJvZHVjdERlc2NyaXB0aW9uLXByb2R1Y3RfaWQ9MTcwNyZsYW5ndWFnZV9pZD0x",
            "id": "cHJvZHVjdERlc2NyaXB0aW9uLXByb2R1Y3RfaWQ9MTcwNyZsYW5ndWFnZV9pZD0x",
            "name": "Product Name",
            "metaKeywords": {},
            "metaDescription": {},
            "shortDescription": "Short description",
            "description": "Long description",
            "parameters": "Color: green Size: XL",
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
    "productCategoryRelations": [...],
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

## Step 3

Additional product images belonging to the product can be attached using [**Product Image Resource**](../../api/product_image.md).

**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/productImages</td>
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
    "imageAlt": "Image Alt",
    "sortOrder": "1",
    "product": {
        "id": "cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc="
    }
}
```

**Response**

```json
{
    "href": "http://shopname.api.myshoprenter.hu/productImages/cHJvZHVjdEltYWdlLXByb2R1Y3RfaW1hZ2VfaWQ9MQ==",
    "id": "cHJvZHVjdEltYWdlLXByb2R1Y3RfaW1hZ2VfaWQ9MQ==",
    "imagePath": "product\/image.jpg",
    "imageAlt": "Image Alt",
    "sortOrder": "1",
    "product": {
        "href": "http://shopname.api.myshoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE3MDc="
    }
}
```



