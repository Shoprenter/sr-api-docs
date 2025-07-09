# Zone Resource

## Properties

<ResourceProperties :resource="'zone'" :lang="'en'"/>

<ResourceScopes :resource="'zone'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'zone'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/zone/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/zone/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'zone'" :endpoint="'getCollection'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/zone/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/zone/response/xml/get_page.xml

</template>

</ResourceEndpoint>

