# Reload Order Url Resource

## Tulajdonságok

<ResourceProperties :resource="'reload_order_url'" :lang="'hu'"/>

## Endpoints

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'reload_order_url'" :endpoint="'post'" :lang="'hu'">

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
