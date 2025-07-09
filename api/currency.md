# Currency Resource

## Properties

<ResourceProperties :resource="'currency'" :lang="'en'"/>

<ResourceScopes :resource="'currency'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'currency'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/currency/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/currency/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'currency'" :endpoint="'getCollection'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/currency/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/currency/response/xml/get_page.xml

</template>

</ResourceEndpoint>

