# Product Resource

## Tulajdonságok

<ResourceProperties :resource="'product'" :lang="'hu'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'product'" :endpoint="'get'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/product/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/product/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'product'" :endpoint="'getCollection'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/product/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/product/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'product'" :endpoint="'post'" :lang="'hu'">

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
<ResourceEndpoint :resource="'product'" :endpoint="'put'" :lang="'hu'">

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
<ResourceEndpoint :resource="'product'" :endpoint="'delete'" :lang="'hu'"/>

## Példák

- [**Termék hozzáadása kategóriához**](../development/api-examples/04_attach_product_to_category.md)
- [**Termékkép hozzáadása termékhez**](../development/api-examples/05_attach_uploaded_image_to_product.md)
