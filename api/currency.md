# Currency Resource

## Tulajdonságok

<ResourceProperties :resource="'currency'" :lang="'hu'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'currency'" :endpoint="'get'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/currency/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/currency/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'currency'" :endpoint="'getCollection'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/currency/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/currency/response/xml/get_page.xml

</template>

</ResourceEndpoint>

