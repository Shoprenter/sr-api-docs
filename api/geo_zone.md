# Geo Zone Resource

## Properties

<ResourceProperties :resource="'geo_zone'" :lang="'en'"/>

<ResourceScopes :resource="'geo_zone'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'geo_zone'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/geo_zone/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/geo_zone/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'geo_zone'" :endpoint="'getCollection'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/geo_zone/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/geo_zone/response/xml/get_page.xml

</template>

</ResourceEndpoint>

