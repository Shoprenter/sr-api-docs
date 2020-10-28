# Product Extend Resource

## Tulajdonságok

<ResourceProperties :resource="'product_extend'" :lang="'hu'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'product_extend'" :endpoint="'get'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/product_extend/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/product_extend/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'product_extend'" :endpoint="'getCollection'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/product_extend/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/product_extend/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'product_extend'" :endpoint="'post'" :lang="'hu'">

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
<ResourceEndpoint :resource="'product_extend'" :endpoint="'put'" :lang="'hu'">

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
<ResourceEndpoint :resource="'product_extend'" :endpoint="'delete'" :lang="'hu'"/>

## Példák

- [**Termék hozzáadása kategóriához**](../development/api-examples/04_attach_product_to_category.md)
- [**Termékkép hozzáadása termékhez**](../development/api-examples/05_attach_uploaded_image_to_product.md)
- [**Akciós termék**](../development/api-examples/01_0_product_special.md)
- [**Nap terméke**](../development/api-examples/01_1_product_special_product_of_day.md)
- [**Tömeges termékfeltöltés**](../development/api/04_batch.md#tömeges-termékfeltöltés)
- [**Termék hozzáadása kategóriához batchelve OuterID-val**](../development/api/04_batch.md#termék-hozzáadása-kategóriához-outer-id-segítségével)

