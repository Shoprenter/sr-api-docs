# Reload Order Url Resource

## Properties

<ResourceProperties :resource="'reload_order_url'" :lang="'en'"/>

<ResourceScopes :resource="'reload_order_url'"/>

## Endpoints

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'reload_order_url'" :endpoint="'post'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/reload_order_url/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/reload_order_url/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/reload_order_url/response/xml/get_id.xml

</template>

</ResourceEndpoint>
