# Payment Mode Resource

## Properties

<ResourceProperties :resource="'payment_mode'" :lang="'en'"/>

<ResourceScopes :resource="'payment_mode'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'payment_mode'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/payment_mode/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/payment_mode/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'payment_mode'" :endpoint="'getCollection'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/payment_mode/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/payment_mode/response/xml/get_page.xml

</template>

</ResourceEndpoint>

