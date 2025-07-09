# Category Resource

## Properties

<ResourceProperties :resource="'category'" :lang="'en'"/>

<ResourceScopes :resource="'category'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'category'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/category/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/category/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'category'" :endpoint="'getCollection'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/category/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/category/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'category'" :endpoint="'post'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/category/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/category/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/category/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (PUT ENDPOINT)
<ResourceEndpoint :resource="'category'" :endpoint="'put'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/category/request/put.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/category/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/category/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (DELETE ENDPOINT)
<ResourceEndpoint :resource="'category'" :endpoint="'delete'" :lang="'en'"/>

## Examples

- [**Attach product to category**](../development/api-examples/04_attach_product_to_category.md)
- [**Attach product to category using batch with OuterId**](../development/api/04_batch.md#termek-hozzaadasa-kategoriahoz-outer-id-segitsegevel)
