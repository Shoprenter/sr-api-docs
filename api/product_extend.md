# Product Extend Resource

## Properties

<ResourceProperties :resource="'product_extend'" :lang="'en'"/>

<ResourceScopes :resource="'product_extend'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'product_extend'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/product_extend/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/product_extend/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'product_extend'" :endpoint="'getCollection'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/product_extend/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/product_extend/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'product_extend'" :endpoint="'post'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/product_extend/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/product_extend/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/product_extend/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (PUT ENDPOINT)
<ResourceEndpoint :resource="'product_extend'" :endpoint="'put'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/product_extend/request/put.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/product_extend/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/product_extend/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (DELETE ENDPOINT)
<ResourceEndpoint :resource="'product_extend'" :endpoint="'delete'" :lang="'en'"/>

## Examples

- [**Attach product to category**](../development/api-examples/04_attach_product_to_category.md)
- [**Attach image to product**](../development/api-examples/05_attach_uploaded_image_to_product.md)
- [**Product Special**](../development/api-examples/01_0_product_special.md)
- [**Product of day**](../development/api-examples/01_1_product_special_product_of_day.md)
- [**Product creation with batch**](../development/api/04_batch.md#tomeges-termekfeltoltes)
- [**Attach Product to category with batch using OuterId**](../development/api/04_batch.md#termek-hozzaadasa-kategoriahoz-outer-id-segitsegevel)
- [**Product attribute handling**](../development/api-examples/08_product_attribute_handling.md)

