# Order Product Option Resource

## Properties

<ResourceProperties :resource="'order_product_option'" :lang="'en'"/>

<ResourceScopes :resource="'order_product_option'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'order_product_option'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/order_product_option/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/order_product_option/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'order_product_option'" :endpoint="'getCollection'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/order_product_option/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/order_product_option/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'order_product_option'" :endpoint="'post'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/order_product_option/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/order_product_option/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/order_product_option/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (PUT ENDPOINT)
<ResourceEndpoint :resource="'order_product_option'" :endpoint="'put'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/order_product_option/request/put.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/order_product_option/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/order_product_option/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (DELETE ENDPOINT)
<ResourceEndpoint :resource="'order_product_option'" :endpoint="'delete'" :lang="'en'"/>

