# Shipping Mode Extend Resource

## Properties

<ResourceProperties :resource="'shipping_mode_extend'" :lang="'en'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'shipping_mode_extend'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/shipping_mode_extend/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/shipping_mode_extend/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'shipping_mode_extend'" :endpoint="'getCollection'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/shipping_mode_extend/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/shipping_mode_extend/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'shipping_mode_extend'" :endpoint="'post'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/shipping_mode_extend/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/shipping_mode_extend/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/shipping_mode_extend/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (PUT ENDPOINT)
<ResourceEndpoint :resource="'shipping_mode_extend'" :endpoint="'put'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/shipping_mode_extend/request/put.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/shipping_mode_extend/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/shipping_mode_extend/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (DELETE ENDPOINT)
<ResourceEndpoint :resource="'shipping_mode_extend'" :endpoint="'delete'" :lang="'en'"/>

