# Length Class Resource

## Properties

<ResourceProperties :resource="'length_class'" :lang="'en'"/>

<ResourceScopes :resource="'length_class'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'length_class'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/length_class/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/length_class/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'length_class'" :endpoint="'getCollection'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/length_class/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/length_class/response/xml/get_page.xml

</template>

</ResourceEndpoint>

