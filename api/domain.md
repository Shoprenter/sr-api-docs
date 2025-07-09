# Domain Resource

## Properties

<ResourceProperties :resource="'domain'" :lang="'en'"/>

<ResourceScopes :resource="'domain'"/>

## Endpoints

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'domain'" :endpoint="'getCollection'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/domain/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/domain/response/xml/get_page.xml

</template>

</ResourceEndpoint>

