# Product Category Relation Resource

## Properties

<ResourceProperties :resource="'product_category_relation'" :lang="'en'"/>

<ResourceScopes :resource="'product_category_relation'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'product_category_relation'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/product_category_relation/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/product_category_relation/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'product_category_relation'" :endpoint="'getCollection'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/product_category_relation/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/product_category_relation/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'product_category_relation'" :endpoint="'post'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/product_category_relation/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/product_category_relation/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/product_category_relation/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (PUT ENDPOINT)
<ResourceEndpoint :resource="'product_category_relation'" :endpoint="'put'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/product_category_relation/request/put.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/product_category_relation/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/product_category_relation/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (DELETE ENDPOINT)
<ResourceEndpoint :resource="'product_category_relation'" :endpoint="'delete'" :lang="'en'"/>

## Examples

- [**Attach product to category**](../development/api-examples/04_attach_product_to_category.md)
- [**Attach Product to category with batch using OuterId**](../development/api/04_batch.md#termek-hozzaadasa-kategoriahoz-outer-id-segitsegevel)
