# API Batch processor

In order to decrease the number of API requests, and to fasten the processing of requests, we can process API requests in batches as well. In order to do so, we have to send a specially structured block with POST method to the `[API_DOMAIN]/batch` URL.

## Operation

1. The client forwards the bunch of requests with the help of **POST** method to the `[API_DOMAIN]/batch` URL.

2. API checks if the client has permission to process the requests, and if the structure of the requests is suitable. Processing will start if yes, otherwise an error message will be sent to the client, corresponding to the structure of responses.

3. The server processes the requests in a cycle and collects the responses in a specially structured block.

4. Once the processing of requests is finished, the server will forward the block of responses to the output in the appropriate format (recommendation: JSON, maybe XML).

The **recommended number of requests should be 200** in case of Batch requests.

The size limit of a post is *(max_post_size)* **32MB**. Please pay attention to this in case of photo upload, not to exceed the limit.

**The following examples are only illustrations, therefore the complete API request and response is not included.**

## API request

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/batch</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>
        Accept:application/json<br>
        Content-Type:application/json
    </td>
  </tr>
</table>

The API request should follow the below structure:

```json
{
  "data": {
    "requests": [
      {
        "method": "GET",
        "uri": "http://shopname.api.myshoprenter.hu/productExtend?full=1&limit=200&page=0"
      },
      {
        "method": "POST",
        "uri": "http://shopname.api.myshoprenter.hu/products/[ID]",
        "data": {}
      }
    ]
  }
}
```

- **method:** GET, POST, PUT, DELETE
- **uri:** The resources’  API URI
- **data:** The object including data in case of POST or PUT

## API response

```json
{
  "requests": {
    "request": [
      {
        "method": "GET",
        "uri": "http://shopname.api.myshoprenter.hu/productExtend?full=1&limit=200&page=0",
        "response": {
          "header": { "statusCode": "200" },
          "body": {}
        }
      },
      {
        "method": "POST",
        "uri": "http://shopname.api.myshoprenter.hu/products/[ID]",
        "response": {
          "header": { "statusCode": "200" },
          "body": {}
        }
      }
    ]
  }
}
```
- **statusCode:** Code of HTTP status. If request processing was correct, the value is 200, 201 or 204, otherwise the status code implying error.
- **body:** includes the response, text message of the error in case of failure.

**Any error of technical reason in requests within batch API results in 200 status code, therefore statusCodes of batch requests should be checked in the client application.**

Further practical examples for the use of batch requests.

Request

<details class="example-dropdown"><summary>Example</summary>
<p>

```php
Array(
    [requests] => Array(
        [0] => Array(
            [method] => GET
            [uri] => http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=
        )
        [1] => Array(
            [method] => DELETE
            [uri] => http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=
        )
        [2] => Array(
            [method] => PUT
            [uri] => http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=
            [data] => Array(
                [picture] => /data/cukorbetegek.JPG
                [sortOrder] => 2
                [status] => 1
                [multiplier] => 1.00000
                [productsStatus] => 1
                [groupCode] =>
                [parentCategory] => Array(
                    [id] => Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9NTM=
                )

                [centralCategory] => Array(
                    [id] => Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=
                )
            )
        )
        [3] => Array(
            [method] => POST
            [uri] => http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=
            [data] => Array(
                [status] => 0
            )
        )
        [4] => Array(
            [method] => GET
            [uri] => http://shopname.api.myshoprenter.hu/category/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=
        )
    )
)
```

</p>
</details>

Response

<details class="example-dropdown"><summary>Example</summary>
<p>

```xml
<response>
     <requests>
         <request>
             <method><![CDATA[GET]]></method>
             <uri><![CDATA[http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></uri>
             <response>
                 <header>
                     <statusCode>200</statusCode>
                 </header>
                 <body>
                     <href><![CDATA[http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></href>
                     <id><![CDATA[Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></id>
                     <innerId><![CDATA[18]]></innerId>
                     <picture><![CDATA[/data/cukorbetegek.JPG]]></picture>
                     <sortOrder><![CDATA[2]]></sortOrder>
                     <status><![CDATA[0]]></status>
                     <multiplier><![CDATA[1.00000]]></multiplier>
                     <productsStatus><![CDATA[1]]></productsStatus>
                     <groupCode/>
                     <dateCreated><![CDATA[2014-09-15T15:32:02]]></dateCreated>
                     <dateUpdated><![CDATA[2014-09-15T15:32:02]]></dateUpdated>
                     <parentCategory>
                         <href><![CDATA[http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9NTM=]]></href>
                     </parentCategory>
                     <centralCategory>
                         <href><![CDATA[http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></href>
                     </centralCategory>
                     <categoryDescriptions>
                         <href><![CDATA[http://shopname.api.myshoprenter.hu/categoryDescriptions?categoryId=Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></href>
                     </categoryDescriptions>
                     <categoryCustomerGroupRelations>
                         <href><![CDATA[http://shopname.api.myshoprenter.hu/categoryCustomerGroupRelations?categoryId=Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></href>
                     </categoryCustomerGroupRelations>
                     <customerGroups>
                         <href><![CDATA[http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=/customerGroups]]></href>
                     </customerGroups>
                 </body>
             </response>
         </request>
         <request>
             <method><![CDATA[DELETE]]></method>
             <uri><![CDATA[http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></uri>
             <response>
                 <header>
                     <statusCode>200</statusCode>
                 </header>
                 <body/>
             </response>
         </request>
         <request>
             <method><![CDATA[PUT]]></method>
             <uri><![CDATA[http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></uri>
             <response>
                 <header>
                     <statusCode>200</statusCode>
                 </header>
                 <body>
                     <href><![CDATA[http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></href>
                     <id><![CDATA[Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></id>
                     <innerId><![CDATA[18]]></innerId>
                     <picture><![CDATA[/data/cukorbetegek.JPG]]></picture>
                     <sortOrder><![CDATA[2]]></sortOrder>
                     <status><![CDATA[1]]></status>
                     <multiplier><![CDATA[1.00000]]></multiplier>
                     <productsStatus><![CDATA[1]]></productsStatus>
                     <groupCode/>
                     <dateCreated><![CDATA[2014-09-15T15:32:02]]></dateCreated>
                     <dateUpdated><![CDATA[2014-09-15T15:33:53]]></dateUpdated>
                     <parentCategory>
                         <href><![CDATA[http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9NTM=]]></href>
                     </parentCategory>
                     <centralCategory>
                         <href><![CDATA[http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></href>
                     </centralCategory>
                     <categoryDescriptions>
                         <href><![CDATA[http://shopname.api.myshoprenter.hu/categoryDescriptions?categoryId=Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></href>
                     </categoryDescriptions>
                     <categoryCustomerGroupRelations>
                         <href><![CDATA[http://shopname.api.myshoprenter.hu/categoryCustomerGroupRelations?categoryId=Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></href>
                     </categoryCustomerGroupRelations>
                     <customerGroups>
                         <href><![CDATA[http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=/customerGroups]]></href>
                     </customerGroups>
                 </body>
             </response>
         </request>
         <request>
             <method><![CDATA[POST]]></method>
             <uri><![CDATA[http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></uri>
             <response>
                 <header>
                     <statusCode>200</statusCode>
                 </header>
                 <body>
                     <href><![CDATA[http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></href>
                     <id><![CDATA[Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></id>
                     <innerId><![CDATA[18]]></innerId>
                     <picture><![CDATA[/data/cukorbetegek.JPG]]></picture>
                     <sortOrder><![CDATA[2]]></sortOrder>
                     <status><![CDATA[0]]></status>
                     <multiplier><![CDATA[1.00000]]></multiplier>
                     <productsStatus><![CDATA[1]]></productsStatus>
                     <groupCode/>
                     <dateCreated><![CDATA[2014-09-15T15:32:02]]></dateCreated>
                     <dateUpdated><![CDATA[2014-09-15T15:33:53]]></dateUpdated>
                     <parentCategory>
                         <href><![CDATA[http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9NTM=]]></href>
                     </parentCategory>
                     <centralCategory>
                         <href><![CDATA[http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></href>
                     </centralCategory>
                     <categoryDescriptions>
                         <href><![CDATA[http://shopname.api.myshoprenter.hu/categoryDescriptions?categoryId=Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></href>
                     </categoryDescriptions>
                     <categoryCustomerGroupRelations>
                         <href><![CDATA[http://shopname.api.myshoprenter.hu/categoryCustomerGroupRelations?categoryId=Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></href>
                     </categoryCustomerGroupRelations>
                     <customerGroups>
                         <href><![CDATA[http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=/customerGroups]]></href>
                     </customerGroups>
                 </body>
             </response>
         </request>
         <request>
             <method><![CDATA[GET]]></method>
             <uri><![CDATA[http://shopname.api.myshoprenter.hu/category/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></uri>
             <response>
                 <header>
                     <statusCode>404</statusCode>
                 </header>
                 <body>
                     <message><![CDATA[Resource matching URI "/category/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=" not found]]></message>
                 </body>
             </response>
         </request>
     </requests>
 </response>
```

</p>
</details>

## frequent issues

1. **Empty response, or "Data parameter not found in POST/PUT!" error message with 400 status code:**<br>
   Obviously **data** parameter cannot be found in the batch.


###

## Further examples

### Mass product upload

The following example illustrates a frequent action similar to the aforementioned, in which multiple products are being uploaded at the same time with the help of batching.
In order to upload all further data of the products (e.g. pictures, details, etc.), [**Product Extend Resource**](../../api/product_extend.md) is recommended to be used.

**It is important to note, that batching has its limits, that are recommended to be applied in order to ensure the smooth operation of requests. Such as:**
1. If possible, batch requests should not be sent asynchronously, new requests should be initiated after the receipt of the response to the previous one.
2. As mentioned previously, the number of requests should not exceed 200, and the size limit of the post (max_post_size) is 32 MB.

**The following examples are only illustrations, therefore the complete API request and response is not included!**

**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/batch</td>
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
    "requests": [
        {
            "method": "POST",
            "uri": "http://shopname.api.myshoprenter.hu/productExtend",
            "data": {...}
        },
        {
            "method": "POST",
            "uri": "http://shopname.api.myshoprenter.hu/productExtend",
            "data": {...}
        },
        {
            "method": "POST",
            "uri": "http://shopname.api.myshoprenter.hu/productExtend",
            "data": {...}
        }
    ]
  }
}
```

**Response**

```json
{
    "requests": {
        "request": [
            {
                "method": "POST",
                "uri": "http://shopname.api.myshoprenter.hu/productExtend",
                "response": {
                    "header": {
                        "statusCode": 200
                    },
                    "body": {...}
                }
            },
            {
                "method": "POST",
                "uri": "http://shopname.api.myshoprenter.hu/productExtend",
                "response": {
                    "header": {
                        "statusCode": 200
                    },
                    "body": {...}
                }
            },
            {
                "method": "POST",
                "uri": "http://shopname.api.myshoprenter.hu/productExtend",
                "response": {
                    "header": {
                        "statusCode": 200
                    },
                    "body": {...}
                }
            }
        ]
    }
}
```

