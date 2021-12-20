# Text Attribute Resource

## FIGYELEM!
A termék tulajdonságokból maximum 300 db hozható létre!  

## Tulajdonságok

<ResourceProperties :resource="'text_attribute'" :lang="'hu'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'text_attribute'" :endpoint="'get'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/text_attribute/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/text_attribute/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'text_attribute'" :endpoint="'getCollection'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/text_attribute/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/text_attribute/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'text_attribute'" :endpoint="'post'" :lang="'hu'">

<template v-slot:request>

<<< @/docs/fixtures/api/text_attribute/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/text_attribute/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/text_attribute/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (PUT ENDPOINT)
<ResourceEndpoint :resource="'text_attribute'" :endpoint="'put'" :lang="'hu'">

<template v-slot:request>

<<< @/docs/fixtures/api/text_attribute/request/put.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/text_attribute/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/text_attribute/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (DELETE ENDPOINT)
<ResourceEndpoint :resource="'text_attribute'" :endpoint="'delete'" :lang="'hu'"/>

## Példa
- [**Termék típusok, egyedi tulajdonságok és termékváltozatok kezelése**](../development/api-examples/08_product_attribute_handling.md)
