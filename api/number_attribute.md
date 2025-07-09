# Number Attribute Resource

## ATTENTION!
A maximum of 300 product attributes can be created!

## Properties

<ResourceProperties :resource="'number_attribute'" :lang="'en'"/>

<ResourceScopes :resource="'number_attribute'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'number_attribute'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/number_attribute/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/number_attribute/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'number_attribute'" :endpoint="'getCollection'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/number_attribute/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/number_attribute/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'number_attribute'" :endpoint="'post'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/number_attribute/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/number_attribute/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/number_attribute/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (PUT ENDPOINT)
<ResourceEndpoint :resource="'number_attribute'" :endpoint="'put'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/number_attribute/request/put.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/number_attribute/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/number_attribute/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (DELETE ENDPOINT)
<ResourceEndpoint :resource="'number_attribute'" :endpoint="'delete'" :lang="'en'"/>

## Examples
- [**Product attribute handling**](../development/api-examples/08_product_attribute_handling.md)
