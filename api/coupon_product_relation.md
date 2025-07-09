# Coupon Product Relation Resource

## Properties

<ResourceProperties :resource="'coupon_product_relation'" :lang="'en'"/>

<ResourceScopes :resource="'coupon_product_relation'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'coupon_product_relation'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/coupon_product_relation/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/coupon_product_relation/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'coupon_product_relation'" :endpoint="'getCollection'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/coupon_product_relation/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/coupon_product_relation/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'coupon_product_relation'" :endpoint="'post'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/coupon_product_relation/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/coupon_product_relation/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/coupon_product_relation/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (PUT ENDPOINT)
<ResourceEndpoint :resource="'coupon_product_relation'" :endpoint="'put'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/coupon_product_relation/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/coupon_product_relation/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/coupon_product_relation/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (DELETE ENDPOINT)
<ResourceEndpoint :resource="'coupon_product_relation'" :endpoint="'delete'" :lang="'en'"/>

