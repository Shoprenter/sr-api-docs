# Language Resource

## Properties

<ResourceProperties :resource="'language'" :lang="'en'"/>

<ResourceScopes :resource="'language'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'language'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/language/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/language/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'language'" :endpoint="'getCollection'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/language/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/language/response/xml/get_page.xml

</template>

</ResourceEndpoint>

