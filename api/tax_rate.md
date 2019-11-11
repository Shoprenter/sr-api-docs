# Tax Rate Resource

## Tulajdonságok

<ResourceProperties :resource="'tax_rate'" :lang="'hu'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'tax_rate'" :endpoint="'get'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/tax_rate/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/tax_rate/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'tax_rate'" :endpoint="'getCollection'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/tax_rate/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/tax_rate/response/xml/get_page.xml

</template>

</ResourceEndpoint>

