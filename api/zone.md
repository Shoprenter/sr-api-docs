# Zone Resource

## Tulajdonságok

<ResourceProperties :resource="'zone'" :lang="'hu'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'zone'" :endpoint="'get'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/zone/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/zone/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'zone'" :endpoint="'getCollection'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/zone/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/zone/response/xml/get_page.xml

</template>

</ResourceEndpoint>

