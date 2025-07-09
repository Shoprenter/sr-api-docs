# Stock Status Resource

## Properties

<ResourceProperties :resource="'stock_status'" :lang="'en'"/>

<ResourceScopes :resource="'stock_status'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'stock_status'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/stock_status/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/stock_status/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'stock_status'" :endpoint="'getCollection'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/stock_status/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/stock_status/response/xml/get_page.xml

</template>

</ResourceEndpoint>

