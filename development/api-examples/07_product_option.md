# Handling Product Option

In order to understand the example, it is worth reading the following [article](https://support.shoprenter.hu/hc/hu/articles/215106128) in advance.

The following example shows how different product options can be specified for a product.

The task consists of 4 steps.
1. Create a product option for an existing product using [**Product Option Resource**](../../api/product_option.md).
2. Preparation of the language for the created product option using [**Product Option Description Resource**](../../api/product_option_description.md).
3. Creating the values of the created product option using [**Product Option Value Resource**](../../api/product_option_value.md).
4. Language of the values of the created product option using [**Product Option Value Description Resource**](../../api/product_option_value_description.md).

An example that demonstrates the preparation process:

Let's say that we sell cakes in our store and we want to sell a 10- and a 12-slice version of the Dobos cake product.
The price of the 10-slice version is the same as the base price of the product, but we would like to sell the 12-slice version HUF 2,000 more expensive.

## Step 1.

We create the new product option using [**Product Option Resource**](../../api/product_option.md).

**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/productOptions</td>
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
    "sortOrder": "1",
    "product": {
        "id": "cHJvZHVjdC1wcm9kdWN0X2lkPTUw"
    }
}
```

**Response**

```json
{
    "href": "http://shopname.api.myshoprenter.hu/productOptions/cHJvZHVjdE9wdGlvbi1wcm9kdWN0X29wdGlvbl9pZD00",
    "id": "cHJvZHVjdE9wdGlvbi1wcm9kdWN0X29wdGlvbl9pZD00",
    "innerId": "4",
    "sortOrder": "1",
    "product": {
        "href": "http://shopname.api.myshoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTUw"
    },
    "productOptionDescriptions": {
        "href": "http://shopname.api.myshoprenter.hu/productOptionDescriptions?productOptionId=cHJvZHVjdE9wdGlvbi1wcm9kdWN0X29wdGlvbl9pZD00"
    },
    "productOptionValues": {
        "href": "http://shopname.api.myshoprenter.hu/productOptionValues?productOptionId=cHJvZHVjdE9wdGlvbi1wcm9kdWN0X29wdGlvbl9pZD00"
    }
}
```

## Step 2.

With the help of [**Product Option Description Resource**](../../api/product_option_description.md) we prepare the language for the created product option.
The example shows a English translation. If we want to assign a name to the given product option in additional languages, the step below must be repeated with the resource id of the desired language.

**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/productOptionDescriptions</td>
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
    "name": "Number of slices",
    "productOption": {
        "id": "cHJvZHVjdE9wdGlvbi1wcm9kdWN0X29wdGlvbl9pZD00"
    },
    "language": {
        "id": "bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ=="
    }
}
```

**Response**

```json
{
    "href": "http://shopname.api.myshoprenter.hu/productOptionDescriptions/cHJvZHVjdE9wdGlvbkRlc2NyaXB0aW9uLXByb2R1Y3Rfb3B0aW9uX2lkPTUxOCZsYW5ndWFnZV9pZD0x",
    "id": "cHJvZHVjdE9wdGlvbkRlc2NyaXB0aW9uLXByb2R1Y3Rfb3B0aW9uX2lkPTUxOCZsYW5ndWFnZV9pZD01",
    "name": "Number of slices",
    "productOption": {
        "href": "http://shopname.api.myshoprenter.hu/productOptions/cHJvZHVjdE9wdGlvbi1wcm9kdWN0X29wdGlvbl9pZD00"
    },
    "language": {
        "href": "http://shopname.api.myshoprenter.hu/languages/bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ=="
    }
}
```

## Step 3.

With the help of [**Product Option Value Resource**](../../api/product_option_value.md) we prepare the values for the created product option.

n the request below, we create two versions: a 10- and a 12-slice version.
The 10-slice version does not change the price of the product, we consider it to be the same as the original price of the product.
The price of the 12-slice version will be increased by HUF 2,000 compared to the price of the original product.

**Request for the 10-slice version**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/productOptionValues</td>
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
    "sortOrder": "1",
    "productOption": {
        "id": "cHJvZHVjdE9wdGlvbi1wcm9kdWN0X29wdGlvbl9pZD00"
    }
}
```


**Response to the 10-slice version**

```json
{
    "href": "http://shopname.api.myshoprenter.hu/productOptionValues/cHJvZHVjdE9wdGlvblZhbHVlLXByb2R1Y3Rfb3B0aW9uX3ZhbHVlX2lkPTc0OA==",
    "id": "cHJvZHVjdE9wdGlvblZhbHVlLXByb2R1Y3Rfb3B0aW9uX3ZhbHVlX2lkPTc0OA==",
    "price": "0000.0000",
    "prefix": "",
    "sortOrder": "1",
    "productOption": {
        "href": "http://shopname.api.myshoprenter.hu/productOptions/cHJvZHVjdE9wdGlvbi1wcm9kdWN0X29wdGlvbl9pZD00"
    },
    "productOptionValueDescriptions": {
        "href": "http://shopname.api.myshoprenter.hu/productOptionValueDescriptions?productOptionValueId=cHJvZHVjdE9wdGlvblZhbHVlLXByb2R1Y3Rfb3B0aW9uX3ZhbHVlX2lkPTc0OA=="
    }
}
```

**Request for the 12-slice version**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/productOptionValues</td>
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
    "price": "2000.0000",
    "sortOrder": "2",
    "prefix": "+",
    "productOption": {
        "id": "cHJvZHVjdE9wdGlvbi1wcm9kdWN0X29wdGlvbl9pZD00"
    }
}
```

**Response to the 12-slice version**

```json
{
    "href": "http://shopname.api.myshoprenter.hu/productOptionValues/cHJvZHVjdE9wdGlvblZhbHVlLXByb2R1Y3Rfb3B0aW9uX3ZhbHVlX2lkPTc0OA==",
    "id": "cHJvZHVjdE9wdGlvblZhbHVlLXByb2R1Y3Rfb3B0aW9uX3ZhbHVlX2lkPTc0OA==",
    "price": "2000.0000",
    "prefix": "+",
    "sortOrder": "2",
    "productOption": {
        "href": "http://shopname.api.myshoprenter.hu/productOptions/cHJvZHVjdE9wdGlvbi1wcm9kdWN0X29wdGlvbl9pZD00"
    },
    "productOptionValueDescriptions": {
        "href": "http://shopname.api.myshoprenter.hu/productOptionValueDescriptions?productOptionValueId=cHJvZHVjdE9wdGlvblZhbHVlLXByb2R1Y3Rfb3B0aW9uX3ZhbHVlX2lkPTc0OA=="
    }
}
```

## Step 4.

With the help of [**Product Option Value Description Resource**](../../api/product_option_value_description.md), we prepare the Hungarian language of the values belonging to the created product option for the 10 and 12 slice versions. 

**Request for the 10-slice version**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/productOptionValueDescriptions</td>
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
    "name": "10 slices",
    "productOptionValue": {
        "id": "cHJvZHVjdE9wdGlvblZhbHVlLXByb2R1Y3Rfb3B0aW9uX3ZhbHVlX2lkPTc0OA=="
    },
    "language": {
        "id": "bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ=="
    }
}
```

**Response to the 10-slice version**

```json
{
    "href": "http://shopname.api.myshoprenter.hu/productOptionValueDescriptions/cHJvZHVjdE9wdGlvblZhbHVlRGVzY3JpcHRpb24tcHJvZHVjdF9vcHRpb25fdmFsdWVfaWQ9NzQ4Jmxhbmd1YWdlX2lkPTE=",
    "id": "cHJvZHVjdE9wdGlvblZhbHVlRGVzY3JpcHRpb24tcHJvZHVjdF9vcHRpb25fdmFsdWVfaWQ9NzQ4Jmxhbmd1YWdlX2lkPTQ=",
    "name": "10 slices",
    "productOptionValue": {
        "href": "http://shopname.api.myshoprenter.hu/productOptionValues/cHJvZHVjdE9wdGlvblZhbHVlLXByb2R1Y3Rfb3B0aW9uX3ZhbHVlX2lkPTc0OA=="
    },
    "language": {
        "href": "http://shopname.api.myshoprenter.hu/languages/bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ=="
    }
}
```

**Request for the 12-slice version**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/productOptionValueDescriptions</td>
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
    "name": "12 slices",
    "productOptionValue": {
        "id": "cHJvZHVjdE9wdGlvblZhbHVlLXByb2R1Y3Rfb3B0aW9uX3ZhbHVlX2lkPTc0OA=="
    },
    "language": {
        "id": "bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ=="
    }
}
```

**Response to the 10-slice version**

```json
{
    "href": "http://shopname.api.myshoprenter.hu/productOptionValueDescriptions/cHJvZHVjdE9wdGlvblZhbHVlRGVzY3JpcHRpb24tcHJvZHVjdF9vcHRpb25fdmFsdWVfaWQ9NzQ5Jmxhbmd1YWdlX2lkPTE=",
    "id": "cHJvZHVjdE9wdGlvblZhbHVlRGVzY3JpcHRpb24tcHJvZHVjdF9vcHRpb25fdmFsdWVfaWQ9NzQ4Jmxhbmd1YWdlX2lkPTQ=",
    "name": "12 slices",
    "productOptionValue": {
        "href": "http://shopname.api.myshoprenter.hu/productOptionValues/cHJvZHVjdE9wdGlvblZhbHVlLXByb2R1Y3Rfb3B0aW9uX3ZhbHVlX2lkPTc0OA=="
    },
    "language": {
        "href": "http://shopname.api.myshoprenter.hu/languages/bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ=="
    }
}
```
