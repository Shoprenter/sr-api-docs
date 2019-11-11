# Weight Class Resource

## Tulajdonságok

<ResourceProperties :resource="'weight_class'" :lang="'hu'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'weight_class'" :endpoint="'get'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/weight_class/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/weight_class/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'weight_class'" :endpoint="'getCollection'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/weight_class/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/weight_class/response/xml/get_page.xml

</template>

</ResourceEndpoint>

