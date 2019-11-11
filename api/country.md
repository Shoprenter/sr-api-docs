# Country Resource

## Tulajdonságok

<ResourceProperties :resource="'country'" :lang="'hu'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'country'" :endpoint="'get'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/country/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/country/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'country'" :endpoint="'getCollection'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/country/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/country/response/xml/get_page.xml

</template>

</ResourceEndpoint>

