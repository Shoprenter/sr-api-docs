# Language Resource

## Tulajdonságok

<ResourceProperties :resource="'language'" :lang="'hu'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'language'" :endpoint="'get'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/language/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/language/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'language'" :endpoint="'getCollection'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/language/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/language/response/xml/get_page.xml

</template>

</ResourceEndpoint>

