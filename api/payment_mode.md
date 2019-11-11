# Payment Mode Resource

## Tulajdonságok

<ResourceProperties :resource="'payment_mode'" :lang="'hu'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'payment_mode'" :endpoint="'get'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/payment_mode/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/payment_mode/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'payment_mode'" :endpoint="'getCollection'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/payment_mode/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/payment_mode/response/xml/get_page.xml

</template>

</ResourceEndpoint>

