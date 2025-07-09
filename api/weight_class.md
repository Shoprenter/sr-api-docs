# Weight Class Resource

## Properties

<ResourceProperties :resource="'weight_class'" :lang="'en'"/>

<ResourceScopes :resource="'weight_class'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'weight_class'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/weight_class/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/weight_class/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'weight_class'" :endpoint="'getCollection'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/weight_class/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/weight_class/response/xml/get_page.xml

</template>

</ResourceEndpoint>

