# Management of product types, unique properties and product variants

_Before we start learning about handling types and properties via API:_

**Recommended** [article](https://support.shoprenter.hu/hc/hu/articles/215106088-T%C3%ADpusok-tluodnosts%C3%A1gok-sz%C5%B1r%C5%91k-matrix%C3%A1k) found on the Shoprenter Academy study. **We need to understand** what happens in the administration interface of the managed store, so that they are completely secure
let's get down to business while we handle this part via API!

Each of the products in the stores may have characteristics that
which determine the nature of the product, e.g. color, size, etc. These characteristics
we call it the **unique feature** of the product. With the help of these, the store owner can solve, for example:
the structured presentation of the product's characteristics on the product page, and to make it easier for the Buyers
product filtering.

The Shoprenter has these qualities
It is grouped into **product types**, the purpose of which is to have a set of properties
the common features of similar products should be described.
It is important to mention that a single product property can belong to several product types.

Product types and unique features also play a major role in the formation of product variants.
Along a unique feature, we can form several other versions of a product, which are actually considered independent products.

With the help of the Shoprenter API, we are able to create our own property systems.
The design process **requires a lot of attention**, so we will use an example to illustrate the construction process
phases.

1.-5. step: Management of product type and unique properties, connecting them with products.

Step 6 (optional): Creating the product variants. If there is no need to train product variants, skip this step
we can leave it.

**Important note:** It is possible to retrieve the unique properties of a product in a simplified manner
with [Product Extend Resource](../../api/product_extend.md).
The **productAttributeExtend** field contains a list that displays unique attributes for the product.

#### An example to demonstrate the process:
In a store selling plants, I want to create a product type named **Houseplant**.
In the future, I will want to assign this type to all plants that, due to their nature,
it can be said to be a houseplant.

To keep the example simple and go through all property types,
this type will contain 3 unique properties:

* Number of hours of sunshine - **Integer** type property
* Shape of letters - **Text (selection list)** type property: "Pointed" and "Round" with selectable values
* Latin designation: **Arbitrary** type property

Next, we assign our completed product type to an existing product, and then check
how to enter the values of the product properties.

## Step 1 - Create a product type

With a simple request, we create our product type, which will be combined with a Houseplant
its unique properties.

_The versioning parameters are discussed [here](#step-6-creating-product-variants)._

#### Used Resource

[Product Class](../../api/product_class.md)

#### Request

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/productClasses</td>
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
    "name": "houseplant",
    "description": "Ez a szobanoveny típus leírása"
}
```

#### Response

```json
{
    "href": "http://shopname.api.myshoprenter.hu/productClasses/cHJvZHVjdENsYXNzLXByb2R1Y3RfY2xhc3NfaWQ9MTQ=",
    "id": "cHJvZHVjdENsYXNzLXByb2R1Y3RfY2xhc3NfaWQ9MTQ=",
    "name": "houseplant",
    "description": "This is the houseplant type description",
    "firstVariantSelectType": "SELECT",
    "secondVariantSelectType": "SELECT",
    "firstVariantParameter": null,
    "secondVariantParameter": null,
    "productClassAttributeRelations": {
        "href": "http://shopname.api.myshoprenter.hu/productClassAttributeRelations?productClassId=cHJvZHVjdENsYXNzLXByb2R1Y3RfY2xhc3NfaWQ9MTQ="
    }
}
```

## Step 2 - Create custom properties

In this step, we get to know the API Resource of 3 unique properties:
- Number Attribute Resource - Integer/Fraction number type attribute
- Text Attribute Resource - Any type of attribute
- List Attribute Resource - Text (selection list) type attribute

We create our 3 unique properties, then assign a label to all three properties
With Attribute Description Resource.

### Number Attribute Resource
With Resource, we can add properties whose values can be of integer or fractional number type.

Following the example, we will need an Integer property that specifies the number of hours of sunshine
for a product.

#### Used Resource

[Number Attribute Resource](../../api/number_attribute.md)

#### Request

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/numberAttributes</td>
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
    "type": "INTEGER",
    "name": "number_of_sunny_hours",
    "priority": "NORMAL",
    "sortOrder": "1",
    "defaultValue": "4",
    "required": "1",
    "minValue": "1",
    "maxValue": "24"
}
```

#### Response

```json
{
    "href": "http://shopname.api.myshoprenter.hu/numberAttributes/bnVtYmVyQXR0cmlidXRlLWF0dHJpYnV0ZV9pZD0xMw==",
    "id": "bnVtYmVyQXR0cmlidXRlLWF0dHJpYnV0ZV9pZD0xMw==",
    "type": "INTEGER",
    "name": "number_of_sunny_hours",
    "priority": "NORMAL",
    "sortOrder": "1",
    "defaultValue": "10",
    "required": "1",
    "minValue": "1",
    "maxValue": "24",
    "showValueIfZero": null,
    "valuePrecision": null,
    "numberAttributeWidget": {
        "href": "http://shopname.api.myshoprenter.hu/numberAttributeWidgets/bnVtYmVyQXR0cmlidXRlV2lkZ2V0LWF0dHJpYnV0ZV9pZD0xMw=="
    },
    "attributeDescriptions": {
        "href": "http://shopname.api.myshoprenter.hu/attributeDescriptions?numberAttributeId=bnVtYmVyQXR0cmlidXRlLWF0dHJpYnV0ZV9pZD0xMw=="
    },
    "numberAttributeValues": {
        "href": "http://shopname.api.myshoprenter.hu/numberAttributeValues?numberAttributeId=bnVtYmVyQXR0cmlidXRlLWF0dHJpYnV0ZV9pZD0xMw=="
    }
}
```
**More important fields:**
- The value of the **type** field is INTEGER or FLOAT. This determines whether a
  Whether to create an Integer or Fraction type Resource property.
- With the **priority** field, its visibility was set to NORMAL type,
  so it will only appear on the product page.
- The value of the **required** field is 1 so that it is mandatory for the product where the property is used.
- With the **minValue** and **maxValue** fields, we limited the value range to 24 hours.

### Text Attribute Resource 

With Resource we can include properties whose values can be arbitrary _string_ values.

Following the example, we will now create a property that will contain the Latin name of the plant.

#### Used Resource

[Text Attribute Resource](../../api/text_attribute.md)

#### Request

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/textAttributes</td>
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
    "type": "TEXT",
    "name": "latin_name",
    "priority": "NORMAL",
    "sortOrder": "3",
    "required": "0",
    "textFieldType": "INPUT",
    "translateable": "0"
}
```

### Response

```json
{
    "href": "http://shopname.api.myshoprenter.hu/textAttributes/dGV4dEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTU=",
    "id": "dGV4dEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTU=",
    "type": "TEXT",
    "name": "latin_name",
    "priority": "NORMAL",
    "sortOrder": "2",
    "required": "0",
    "textFieldType": "INPUT",
    "translateable": "0",
    "attributeDescriptions": {
        "href": "http://shopname.api.myshoprenter.hu/attributeDescriptions?textAttributeId=dGV4dEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTU="
    },
    "textAttributeValues": {
        "href": "http://shopname.api.myshoprenter.hu/textAttributeValues?textAttributeId=dGV4dEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTU="
    }
}
```

**More important fields:**
- The value of the **type** field is TEXT. Required.
- With the **priority** field, its visibility was set to NORMAL type,
  so it will only appear on the product page.
- The value of the **required** field is 0, because it is not certain that we will know the Latin name of every plant, so we do not
  we make it mandatory
- The **textFieldType** field was given an INPUT value, so on the product editor page, the property value
  we can record it in a one-line text input field.
- The **translateable** field tells whether the value can be entered in several languages or not. Because it is independent of language
  our property value (in Latin), is given a value of 0.

### List Attribute Resource 

With Resource, we can add properties whose values can be selected from a predefined list.

The preparation of the detailed unique property is more complex than we experienced in the case of the previous two properties:
- We need to create the property with List Attribute Resource.
- We need to specify how many values the property can take with List Attribute Value Resource. So that's it
  We need to create a List Attribute Value Resource individual, as many values as we want to make selectable.
- When the values were created individually, we specify that they are single with the List Attribute Value Description Resource
  languages, what will be the specific value.

Following the example, we will now create a property that will specify the shape of the plant's leaves.
The two possible values are: "Pointed", "Round".

#### Used Resource

- [List Attribute Resource](../../api/list_attribute.md)
- [List Attribute Value Resource](../../api/list_attribute_value.md)
- [List Attribute Value Description Resource](../../api/list_attribute_value_description.md)

#### Request - List Attribute Resource

As with the previous examples, we first create the attribute itself.

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/listAttributes</td>
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
    "type": "LIST",
    "name": "shape_of_leaves",
    "priority": "NORMAL",
    "sortOrder": "2",
    "required": "1",
    "presentation": "TEXT"
}
```

### Response

```json
{
    "href": "http://shopname.api.myshoprenter.hu/listAttributes/bGlzdEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTY=",
        "id": "bGlzdEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTY=",
        "type": "LIST",
        "name": "shape_of_leaves",
        "priority": "NORMAL",
        "sortOrder": "2",
        "required": "1",
        "presentation": "TEXT",
        "listAttributeWidget": {
            "href": "http://shopname.api.myshoprenter.hu/listAttributeWidgets/bGlzdEF0dHJpYnV0ZVdpZGdldC1hdHRyaWJ1dGVfaWQ9MTY="
        },
        "defaultListAttributeValue": null,
        "attributeDescriptions": {
            "href": "http://shopname.api.myshoprenter.hu/attributeDescriptions?listAttributeId=bGlzdEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTY="
        },
        "listAttributeValues": {
            "href": "http://shopname.api.myshoprenter.hu/listAttributeValues?listAttributeId=bGlzdEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTY="
        }
}
```

Note the resource id of the completed property: **bGlzdEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTY=**
We will need it in the next step to populate our picklist property with values.

**More important fields:**
- The value of the **type** field is LIST. Required.
- With the **priority** field, its visibility was set to NORMAL type,
  so it will only appear on the product page.
- The **presentation** field has a role if this property is used to create a product version.
  Enter the selector type of the product variant displayed on the product page. In this case, it will be TEXT, so it is textual
  a selection list would appear.

#### Request - List Attribute Value Resource

We want to make two values selectable in the picklist: "Pointed" and "Round".
As I mentioned, with Resource we only create two "empty" values, which we do not specify yet,
which will represent "Pointed" and which will represent "Round".

We will use the resource id of the List Attribute property created in the previous step to attach it
the two new values for the "Form of letters" unique property.

**Repeat the following request twice:**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/listAttributeValues</td>
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
    "listAttribute": {
        "id": "bGlzdEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTY="
    }
}
```

**Response of the two requests:**

```json
{
    "href": "http://shopname.api.myshoprenter.hu/listAttributeValues/bGlzdEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNiZ2YWx1ZV9pZD0x",
    "id": "bGlzdEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNiZ2YWx1ZV9pZD0x",
    "listAttribute": {
        "href": "http://shopname.api.myshoprenter.hu/listAttributes/bGlzdEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTY="
    },
    "listAttributeValueDescriptions": {
        "href": "http://shopname.api.myshoprenter.hu/listAttributeValueDescriptions?listAttributeValueId=bGlzdEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNiZ2YWx1ZV9pZD0x"
    }
}
```

```json
{
    "href": "http://shopname.api.myshoprenter.hu/listAttributeValues/bGlzdEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNiZ2YWx1ZV9pZD0y",
    "id": "bGlzdEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNiZ2YWx1ZV9pZD0y",
    "listAttribute": {
        "href": "http://shopname.api.myshoprenter.hu/listAttributes/bGlzdEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTY="
    },
    "listAttributeValueDescriptions": {
        "href": "http://shopname.api.myshoprenter.hu/listAttributeValueDescriptions?listAttributeValueId=bGlzdEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNiZ2YWx1ZV9pZD0y"
    }
}
```

Note the resource id of the two created values:
- **bGlzdEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNiZ2YWx1ZV9pZD0x**
- **bGlzdEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNiZ2YWx1ZV9pZD0y**

We will use them in the next step to instantiate the two values.

#### Request - List Attribute Value Description Resource

We need to specify the specific values of the selection list. For the sake of simplicity, we show a with only one language
process.

For the two List Attribute Value resource ids noted in the previous step, I add, in **Hungarian** language, which should be "Pointed" and which should be
the "Round" value.

**The "Pointed" value - Request:**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/listAttributeValueDescriptions</td>
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
    "name": "spiky",
    "language": {
        "id": "bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ=="
    },
    "listAttributeValue": {
        "id": "bGlzdEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNiZ2YWx1ZV9pZD0y"
    }
}
```

**Response:**

```json
{
    "href": "http://shopname.api.myshoprenter.hu/listAttributeValueDescriptions/bGlzdEF0dHJpYnV0ZVZhbHVlRGVzY3JpcHRpb24tbGFuZ3VhZ2VfaWQ9MSZhdHRyaWJ1dGVfaWQ9MTYmdmFsdWVfaWQ9Mg==",
    "id": "bGlzdEF0dHJpYnV0ZVZhbHVlRGVzY3JpcHRpb24tbGFuZ3VhZ2VfaWQ9MSZhdHRyaWJ1dGVfaWQ9MTYmdmFsdWVfaWQ9Mg==",
    "name": "spiky",
    "language": {
        "href": "http://shopname.api.myshoprenter.hu/languages/bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ=="
    },
    "listAttributeValue": {
        "href": "http://shopname.api.myshoprenter.hu/listAttributeValues/bGlzdEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNiZ2YWx1ZV9pZD0y"
    }
}
```

**The "rounded" value - Request:**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/listAttributeValueDescriptions</td>
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
    "name": "rounded",
    "language": {
        "id": "bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ=="
    },
    "listAttributeValue": {
        "id": "bGlzdEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNiZ2YWx1ZV9pZD0x"
    }
}
```

**Response:**

```json
{
    "href": "http://shopname.api.myshoprenter.hu/listAttributeValueDescriptions/bGlzdEF0dHJpYnV0ZVZhbHVlRGVzY3JpcHRpb24tbGFuZ3VhZ2VfaWQ9MSZhdHRyaWJ1dGVfaWQ9MTYmdmFsdWVfaWQ9Mg==",
    "id": "bGlzdEF0dHJpYnV0ZVZhbHVlRGVzY3JpcHRpb24tbGFuZ3VhZ2VfaWQ9MSZhdHRyaWJ1dGVfaWQ9MTYmdmFsdWVfaWQ9Mg==",
    "name": "rounded",
    "language": {
        "href": "http://shopname.api.myshoprenter.hu/languages/bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ=="
    },
    "listAttributeValue": {
        "href": "http://shopname.api.myshoprenter.hu/listAttributeValues/bGlzdEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNiZ2YWx1ZV9pZD0y"
    }
}
```

Of course, if we want the value to appear on the product page in line with the store's current language settings,
e.g.: "spiky" in English as "Sharp", then we have to repeat this step, with the resource id of the English language
and with the value "Sharp" given to the **name** field, for example.

### Attribute Description Resource

We need to label all three unique properties so that they are visible both on the admin interface and in the store
in language the name of the property.

Of course, labels can be entered in several languages. We show an example of the number of sunny hours property,
labeling in Hungarian.
Do the same for the other two properties.

What we will need:
- Number of sunny hours for resource id: **bnVtYmVyQXR0cmlidXRlLWF0dHJpYnV0ZV9pZD0xMw==**
- Hungarian language resource id: **bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ==**

#### Used Resource

[Attribute Description Resource](../../api/attribute_description.md)

#### Request

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/attributeDescriptions</td>
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
    "name": "Number of sunny hours",
    "description": "It tells you how many hours per day the plant needs to spend in sunlight",
    "attribute": {
        "id": "bnVtYmVyQXR0cmlidXRlLWF0dHJpYnV0ZV9pZD0xMw=="
    },
    "language": {
        "id": "bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ=="
    }
}
```

#### Response

```json
{
    "href": "http://shopname.api.myshoprenter.hu/attributeDescriptions/YXR0cmlidXRlRGVzY3JpcHRpb24tYXR0cmlidXRlX2lkPTcmbGFuZ3VhZ2VfaWQ9NA==",
    "id": "YXR0cmlidXRlRGVzY3JpcHRpb24tYXR0cmlidXRlX2lkPTcmbGFuZ3VhZ2VfaWQ9NA==",
    "name": "Number of sunny hours",
    "description": "It tells you how many hours per day the plant needs to spend in sunlight",
    "attribute": {
        "href": "http://shopname.api.myshoprenter.hu/numberAttributes/bnVtYmVyQXR0cmlidXRlLWF0dHJpYnV0ZV9pZD0xMw=="
    },
    "language": {
        "href": "http://shopname.api.myshoprenter.hu/languages/bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9NA=="
    }
}
```

## Step 3 - Assign unique properties to product type

Now that our 3 unique properties are ready, in the next step we will connect them to the created in the first step,
For indoor plant product type.

We will need the resource id of the 3 unique properties:
- Number of sunny hours - Number Attribute Resource: **bnVtYmVyQXR0cmlidXRlLWF0dHJpYnV0ZV9pZD0xMw==**
- Latin name - Text Attribute Resource: **dGV4dEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTU=**
- Form of letters - List Attribute Resource : b**GlzdEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTY=**

Or, of course, for the resource id of the Indoor plant product type: cHJvZHVjdENsYXNzLXByb2R1Y3RfY2xhc3NfaWQ9MTQ=

#### Used resource

[Product Class Attribute Relation Resource](../../api/product_class_attribute_relation.md)

#### Request

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/productClassAttributeRelations</td>
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
    "productClass": {
        "id": "cHJvZHVjdENsYXNzLXByb2R1Y3RfY2xhc3NfaWQ9MTQ="
    },
    "attribute": {
        "id": "bnVtYmVyQXR0cmlidXRlLWF0dHJpYnV0ZV9pZD0xMw=="
    }
}
```

#### Response

```json
{
    "href": "http://shopname.api.myshoprenter.hu/productClassAttributeRelations/cHJvZHVjdENsYXNzQXR0cmlidXRlUmVsYXRpb24tcHJvZHVjdF9jbGFzc19pZD0xNCZhdHRyaWJ1dGVfaWQ9MTM=",
    "id": "cHJvZHVjdENsYXNzQXR0cmlidXRlUmVsYXRpb24tcHJvZHVjdF9jbGFzc19pZD0xNCZhdHRyaWJ1dGVfaWQ9MTM=",
    "productClass": {
        "href": "http://shopname.api.myshoprenter.hu/productClasses/cHJvZHVjdENsYXNzLXByb2R1Y3RfY2xhc3NfaWQ9MTQ="
    },
    "attribute": {
        "href": "http://shopname.api.myshoprenter.hu/numberAttributes/bnVtYmVyQXR0cmlidXRlLWF0dHJpYnV0ZV9pZD0xMw=="
    }
}
```

The example linked the property "Number of sunny hours" to the product type "Houseplant".
Of course, **we do the same with the other two properties**.

If all three properties are related to the type, the Indoor plant product type can be set to any product.

## Step 4 - Assign a product type to a product

Now that the Indoor plant product type and its unique properties have been completed, in the next step we will look at
how to assign it to a product.

For this we will need the resource id of the Indoor plant product type: **cHJvZHVjdENsYXNzLXByb2R1Y3RfY2xhc3NfaWQ9MTQ**=.

In the following, we assign the product type to an existing product. So, we change the productClass with a PUT request
field. Of course, we can also assign the product type when creating a new product.

#### Used resource

[Product Extend Resource](../../api/product_extend.md)

#### Request

<table>
  <tr>
    <td><b>method:</b></td>
    <td>PUT</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/productExtend/cHJvZHVjdC1wcm9kdWN0X2lkPTYxNA==</td>
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
    "productClass": {
        "id": "cHJvZHVjdENsYXNzLXByb2R1Y3RfY2xhc3NfaWQ9MTQ="
    }
}
```

#### Response

```json
{
    "href": "http://shopname.api.myshoprenter.hu/productExtend/cHJvZHVjdC1wcm9kdWN0X2lkPTYxNA==",
    "id": "cHJvZHVjdC1wcm9kdWN0X2lkPTYxNA==",
...
 "productClass": {
        "href": "http://shopname.api.myshoprenter.hu/productClasses/cHJvZHVjdENsYXNzLXByb2R1Y3RfY2xhc3NfaWQ9MTQ="
    },
...

}
```

Now everything is ready to really use our unique product features.

## Step 5 - Adding custom property values

In this step, the product type and unique features created so far gain meaning.
In the previous step, we entered the Indoor plant product type for any product. Now let's name this product
Indoor plant for 1.

In this step, we specify that in the case of Indoor Plant 1 product, the Number of sunny hours summarized by the Indoor Plant product type,
The shape of the letters and the Latin name are unique properties, what current value should they be given.

Let's say we want **Number of hours of sunshine** (Number Attribute) to 3, **Form of letters** (List Attribute)
to "rounded" and the **Latin name** (Text Attribute) to "Lorem ipsum".

It should be imagined as if we were filling out a form via API: I enter the desired values in two input fields
(Number Attribute, Text Attribute), or I select the desired value from a list (List Attribute).

We can set the current values of the 3 different product properties for the product in different ways.

### Number of sunny hours (Number Attribute)

Entering the value is the easiest for this Resource.

What we need:
- Number of sunny hours property for resource id: **bnVtYmVyQXR0cmlidXRlLWF0dHJpYnV0ZV9pZD0xMw==**
- For the resource id of the product: **cHJvZHVjdC1wcm9kdWN0X2lkPTYxNA==**

#### Used Resource

[Number Attribute Value](../../api/number_attribute_value.md)

#### Request
<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/numberAttributeValues</td>
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
    "value": "3",
    "numberAttribute": {
        "id": "bnVtYmVyQXR0cmlidXRlLWF0dHJpYnV0ZV9pZD0xMw=="
    },
    "product": {
        "id": "cHJvZHVjdC1wcm9kdWN0X2lkPTYxNA=="
    }
}
```

#### Response

```json
{
    "href": "http://shopname.api.myshoprenter.hu/numberAttributeValues/bnVtYmVyQXR0cmlidXRlVmFsdWUtYXR0cmlidXRlX2lkPTEzJnByb2R1Y3RfaWQ9NjE0",
    "id": "bnVtYmVyQXR0cmlidXRlVmFsdWUtYXR0cmlidXRlX2lkPTEzJnByb2R1Y3RfaWQ9NjE0",
    "value": "3",
    "numberAttribute": {
        "href": "http://shopname.api.myshoprenter.hu/numberAttributes/bnVtYmVyQXR0cmlidXRlLWF0dHJpYnV0ZV9pZD0xMw=="
    },
    "product": {
        "href": "http://shopname.api.myshoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTYxNA=="
    }
}
```

### Latin name (Text Attribute)

Giving a value is very similar to when we filled the Text (picklist) type property with values.
Here, too, the fact of assigning a value must first be "indicated" using the Text Attribute Value Resource, and then specified
with the Text Attribute Value Description Resource to see what the actual value will be in some languages.

What we need:
- Latin name for property resource id: **dGV4dEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTU=**
- For the resource id of the product: **cHJvZHVjdC1wcm9kdWN0X2lkPTYxNA==**


#### Used Resouce

 - [Text Attribute Value Resource](../../api/text_attribute_value.md)
 - [Text Attribute Value Description Resource](../../api/text_attribute_value_description.md)

#### Request - Text Attribute Value Resource

<table>
  <tr>
    <td><b>method:</b></td>
    <td>PUT</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/textAttributeValues</td>
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
    "textAttribute": {
        "id": "dGV4dEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTU="
    },
    "product": {
        "id": "cHJvZHVjdC1wcm9kdWN0X2lkPTYxNA=="
    }
}
```

#### Response

```json
{
    "href": "http://shopname.api.myshoprenter.hu/textAttributeValues/dGV4dEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNSZwcm9kdWN0X2lkPTYxNA==",
    "id": "dGV4dEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNSZwcm9kdWN0X2lkPTYxNA==",
    "textAttribute": {
        "href": "http://shopname.api.myshoprenter.hu/textAttributes/dGV4dEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTU="
    },
    "product": {
        "href": "http://shopname.api.myshoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTYxNA=="
    },
    "textAttributeValueDescriptions": {
        "href": "http://shopname.api.myshoprenter.hu/textAttributeValueDescriptions?textAttributeValueId=dGV4dEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNSZwcm9kdWN0X2lkPTYxNA=="
    }
}
```

#### Request - Text Attribute Value Description Resource

Now that the "empty" value for the product is ready, we need to enter the text content for the value.

The question is valid: Why do you need a separate Resource to enter the actual value? The answer is that property
value can be multilingual.
So a value is represented differently in different languages. Therefore, if I create an Arbitrary type property as
in order to be multilingual, we would have to upload the representations of the value per language.

What we will need is the individual resource id of the Text Attribute Value created earlier: **dGV4dEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNSZwcm9kdWN0X2lkPTYxNA==**

Since we specified that the unique property named **latin_name** will be monolingual, we set the **language** field to **null**.


<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/textAttributeValueDescriptions</td>
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
    "name": "Lorem ipsum",
    "language": null,
    "textAttributeValue": {
        "id": "dGV4dEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNSZwcm9kdWN0X2lkPTYxNA=="
    }
}
```

#### Response - Text Attribute Value Description Resource

```json
{
    "href": "http://shopname.api.myshoprenter.hu/textAttributeValues/dGV4dEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNSZwcm9kdWN0X2lkPTYxNA==",
    "id": "dGV4dEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNSZwcm9kdWN0X2lkPTYxNA==",
    "textAttribute": {
        "href": "http://shopname.api.myshoprenter.hu/textAttributes/dGV4dEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTU="
    },
    "product": {
        "href": "http://shopname.api.myshoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTYxNA=="
    },
    "textAttributeValueDescriptions": {
        "href": "http://shopname.api.myshoprenter.hu/textAttributeValueDescriptions?textAttributeValueId=dGV4dEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNSZwcm9kdWN0X2lkPTYxNA=="
    }
}
```

### Shape of leaves (List Attribute)

The property in question is a selection list from which we want to select the "rounded" value for our product.
So, in this case, we have to connect the selected value and the product.

What we need:
- The resource id of the List Attribute Value, whose Hungarian equivalent is "rounded": bGlzdEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNiZ2YWx1ZV9pZD0x
- Product resource id: **cHJvZHVjdC1wcm9kdWN0X2lkPTYxNA==**

#### Used Resouce

[Product List Attribute Value Relation Resource](../../api/product_list_attribute_value_relation.md)

#### Request

<table>
  <tr>
    <td><b>method:</b></td>
    <td>PUT</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/productListAttributeValueRelations</td>
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
        "id": "cHJvZHVjdC1wcm9kdWN0X2lkPTYxNA=="
    },
    "listAttributeValue": {
        "id": "bGlzdEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNiZ2YWx1ZV9pZD0x"
    }
}
```

#### Response

```json
{
    "href": "http://shopname.api.myshoprenter.hu/productListAttributeValueRelations/cHJvZHVjdExpc3RBdHRyaWJ1dGVWYWx1ZVJlbGF0aW9uLXByb2R1Y3RfaWQ9NjE0JmF0dHJpYnV0ZV9pZD0xNiZ2YWx1ZV9pZD0y",
    "id": "cHJvZHVjdExpc3RBdHRyaWJ1dGVWYWx1ZVJlbGF0aW9uLXByb2R1Y3RfaWQ9NjE0JmF0dHJpYnV0ZV9pZD0xNiZ2YWx1ZV9pZD0y",
    "product": {
        "href": "http://shopname.api.myshoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTYxNA=="
    },
    "listAttributeValue": {
        "href": "http://shopname.api.myshoprenter.hu/listAttributeValues/bGlzdEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNiZ2YWx1ZV9pZD0y"
    }
}
```

## Step 6 - Creating product variants

Let's think about our example further. Suppose we have two plants that belong to the same plant species, on the other hand
the shape of their leaves is different. The two plants have different article numbers, prices, and stocks,
but we don't want to offer them on a separate product page. We would like the Customer to be able to navigate from a product page
for all versions.

The **Form of Letters** created in the previous steps with a unique property and the parent-child relationship,
we can easily do this.

### setting of versioning parameters for product type

We will modify the Houseplant product type created in step 2 by setting it as the parameter of the first variant
The shape of the leaves is a unique feature. So the value of the Leaf shape property of products belonging to the Houseplant type
its difference will define our versions.

What we need:
Resource id of indoor plant product type: **cHJvZHVjdENsYXNzLXByb2R1Y3RfY2xhc3NfaWQ9MTQ=**
For the resource id of the unique property "form of letters": **bGlzdEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTY=**

#### Used Resource
[Porduct Class Resource](../../api/product_class.md)

#### Request

<table>
  <tr>
    <td><b>method:</b></td>
    <td>PUT</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/productClasses/cHJvZHVjdENsYXNzLXByb2R1Y3RfY2xhc3NfaWQ9MTQ</td>
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
   "firstVariantParameter": {
        "id": "bGlzdEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTY="
    }
}
```

#### Response

```json
{
    "href": "http://shopname.api.myshoprenter.hu/productClasses/cHJvZHVjdENsYXNzLXByb2R1Y3RfY2xhc3NfaWQ9MTQ=",
    "id": "cHJvZHVjdENsYXNzLXByb2R1Y3RfY2xhc3NfaWQ9MTQ=",
    "name": "houseplant",
    "description": "This is the houseplant type description",
    "firstVariantSelectType": "SELECT",
    "secondVariantSelectType": "SELECT",
    "firstVariantParameter": {
        "href": "http://shopname.api.myshoprenter.hu/listAttributes/bGlzdEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTY="
    },
    "secondVariantParameter": null,
    "productClassAttributeRelations": {
        "href": "http://shopname.api.myshoprenter.hu/productClassAttributeRelations?productClassId=cHJvZHVjdENsYXNzLXByb2R1Y3RfY2xhc3NfaWQ9MTQ="
    }
}
```

**More important fields:**
In the **firstVariantParameter** field, we enter the resource id of the unique property. **This can only come from the properties summarized by the type!**
**firstVariantSelectType** determines how the product variant select field will appear on the product page

**Note:** It is also possible to enter a second versioning parameter. In this case, two factors determine the
different versions.

### Establishing a parent-child relationship

The last step is to establish the parent-child relationship. With this special connection, we can bundle the variants
collect.
The leaf shape property has two values: "spiky" and "rounded"

We have two options:
- We create one product that we designate as the parent and two more that will be the two child products.
- We create a product whose Shape of Leaves property takes on the value "spiky". We will create another one
  product, which is designated as a child product and the Shape of Letters property takes the value "rounded".

For the simplicity of the example, we show the second option.
The setup via API is very simple: we need to go through all the child products and the Product Extend Resource
in the parentProduct field, we enter the resource id of the product that we want to open as a parent.

Let's say that we have two products and we have pre-set the properties of the Form of Letters:
- Indoor plant 1 - "spiky"
- Houseplant 2 - "rounded"

Of course, the product type for both is Indoor plant.

Let's create a product variant in such a way that:
- Indoor plant 1 will be the Parent product | Product resource id: **cHJvZHVjdC1wcm9kdWN0X2lkPTYxMg==**
- Houseplant 2 will be the Children's product | Product resource id: **cHJvZHVjdC1wcm9kdWN0X2lkPTYxNA==**

**So, for the Indoor Plant 2 product, I set the resource id of Indoor Plant 1 in the parentProduct field!**
 
 #### Request
 
<table>
  <tr>
    <td><b>method:</b></td>
    <td>PUT</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/productExtend/cHJvZHVjdC1wcm9kdWN0X2lkPTYxNA==</td>
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
  "parentProduct": {
      "id": "cHJvZHVjdC1wcm9kdWN0X2lkPTYxMg=="
  } 
}
```

#### Response

```json
{
    "href": "http://shopname.api.myshoprenter.hu/productExtend/cHJvZHVjdC1wcm9kdWN0X2lkPTYxNA==",
    "id": "cHJvZHVjdC1wcm9kdWN0X2lkPTYxNA==",
     ...
     "parentProduct": {
        "href": "http://shopname.api.myshoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTYxMg=="
     },
     "volumeUnit": {
        "href": "http://shopname.api.myshoprenter.hu/lengthClasses/bGVuZ3RoQ2xhc3MtbGVuZ3RoX2NsYXNzX2lkPTE="
     },
     ...
   }
```
We are done with that!
