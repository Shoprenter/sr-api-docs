# Product Resource

## Properties

<ResourceProperties :resource="'product'" :lang="'en'"/>

<ResourceScopes :resource="'product'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'product'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/product/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/product/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'product'" :endpoint="'getCollection'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/product/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/product/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'product'" :endpoint="'post'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/product/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/product/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/product/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (PUT ENDPOINT)
<ResourceEndpoint :resource="'product'" :endpoint="'put'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/product/request/put.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/product/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/product/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (DELETE ENDPOINT)
<ResourceEndpoint :resource="'product'" :endpoint="'delete'" :lang="'en'"/>

## Examples

- [**Attach product to category**](../development/api-examples/04_attach_product_to_category.md)
- [**Attach image to product**](../development/api-examples/05_attach_uploaded_image_to_product.md)
- [**Product Special**](../development/api-examples/01_0_product_special.md)
- [**Product of day**](../development/api-examples/01_1_product_special_product_of_day.md)
- [**Product creation with batch**](../development/api/04_batch.md#tomeges-termekfeltoltes)
- [**Attach Product to category with batch using OuterId**](../development/api/04_batch.md#termek-hozzaadasa-kategoriahoz-outer-id-segitsegevel)
