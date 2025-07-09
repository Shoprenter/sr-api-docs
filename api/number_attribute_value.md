# Number Attribute Value Resource

## Properties

<ResourceProperties :resource="'number_attribute_value'" :lang="'en'"/>

<ResourceScopes :resource="'number_attribute_value'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'number_attribute_value'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/number_attribute_value/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/number_attribute_value/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'number_attribute_value'" :endpoint="'getCollection'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/number_attribute_value/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/number_attribute_value/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'number_attribute_value'" :endpoint="'post'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/number_attribute_value/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/number_attribute_value/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/number_attribute_value/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (PUT ENDPOINT)
<ResourceEndpoint :resource="'number_attribute_value'" :endpoint="'put'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/number_attribute_value/request/put.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/number_attribute_value/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/number_attribute_value/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (DELETE ENDPOINT)
<ResourceEndpoint :resource="'number_attribute_value'" :endpoint="'delete'" :lang="'en'"/>

## Examples
- [**Product attribute handling**](../development/api-examples/08_product_attribute_handling.md)
