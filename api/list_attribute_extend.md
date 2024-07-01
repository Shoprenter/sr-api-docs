# List Attribute Extend Resource

## ATTENTION!
A maximum of 300 product attributes can be created!

## Properties

<ResourceProperties :resource="'list_attribute_extend'" :lang="'en'"/>

### `attributeDescriptions` Field Properties
<div class="resource-properties">
<table>
<tr><th>Property</th> <th>Description</th> <th>Required</th> <th>Readonly</th></tr>
<tr> <td>language</td> <td>Language identifier.</td> <td></td> <td></td> </tr>
<tr> <td>name</td> <td>Attribute name in the given language.</td> <td></td> <td></td> </tr>
<tr> <td>description</td> <td>Attribute description in the given language.</td> <td></td> <td></td> </tr>
<tr> <td>prefix</td> <td>Text before the attribute value in the given language.</td> <td></td> <td></td> </tr>
<tr> <td>postfix</td> <td>Text after the attribute value in the given language.</td> <td></td> <td></td> </tr>
</table>
</div>

### `listAttributeValues` Field Properties
<div class="resource-properties">
<table>
<tr><th>Property</th> <th>Description</th> <th>Required</th> <th>Readonly</th></tr>
<tr> <td>valueId</td> <td>Value identifier.</td> <td></td> <td></td> </tr>
<tr> <td>listAttributeValueDescriptions</td> <td>Attribute value descriptions. <a href='#listattributevaluedescriptions-field-properties'>See properties</a></td> <td></td> <td></td> </tr>
</table>
</div>

#### `listAttributeValueDescriptions` Field Properties
<div class="resource-properties">
<table>
<tr><th>Property</th> <th>Description</th> <th>Required</th> <th>Readonly</th></tr>
<tr> <td>language</td> <td>Language identifier.</td> <td></td> <td></td> </tr>
<tr> <td>name</td> <td>Textual representation of the attribute value in the given language.</td> <td></td> <td></td> </tr>
<tr> <td>image</td> <td>Visual representation of the attribute value. A hex color code, or the path to an uploaded image file.</td> <td></td> <td></td> </tr>
<tr> <td>sortOrder</td> <td>Position of the value in the list of filterable values.</td> <td></td> <td></td> </tr>
</table>
</div>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'list_attribute_extend'" :endpoint="'get'" :lang="'en'">
<template v-slot:responseJSON>

<<< @/docs/fixtures/api/list_attribute_extend/response/json/get_id.json

</template>
<template v-slot:responseXML>

<<< @/docs/fixtures/api/list_attribute_extend/response/xml/get_id.xml

</template>
</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'list_attribute_extend'" :endpoint="'getCollection'" :lang="'en'">
<template v-slot:responseJSON>

<<< @/docs/fixtures/api/list_attribute_extend/response/json/get_page.json

</template>
<template v-slot:responseXML>

<<< @/docs/fixtures/api/list_attribute_extend/response/xml/get_page.xml

</template>
</ResourceEndpoint>


