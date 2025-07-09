# Country Resource

## Properties

<ResourceProperties :resource="'country'" :lang="'en'"/>

<ResourceScopes :resource="'country'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'country'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/country/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/country/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'country'" :endpoint="'getCollection'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/country/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/country/response/xml/get_page.xml

</template>

</ResourceEndpoint>

