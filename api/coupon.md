# Coupon Resource

## Properties

<ResourceProperties :resource="'coupon'" :lang="'en'"/>

<ResourceScopes :resource="'coupon'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'coupon'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/coupon/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/coupon/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'coupon'" :endpoint="'getCollection'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/coupon/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/coupon/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'coupon'" :endpoint="'post'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/coupon/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/coupon/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/coupon/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (PUT ENDPOINT)
<ResourceEndpoint :resource="'coupon'" :endpoint="'put'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/coupon/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/coupon/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/coupon/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (DELETE ENDPOINT)
<ResourceEndpoint :resource="'coupon'" :endpoint="'delete'" :lang="'en'"/>

