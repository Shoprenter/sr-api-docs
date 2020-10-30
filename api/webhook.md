# WebHook Resource

## Tulajdonságok

<ResourceProperties :resource="'webhook'" :lang="'hu'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'webhook'" :endpoint="'get'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/webhook/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/webhook/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'webhook'" :endpoint="'getCollection'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/webhook/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/webhook/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'webhook'" :endpoint="'post'" :lang="'hu'">

<template v-slot:request>

<<< @/docs/fixtures/api/webhook/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/webhook/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/webhook/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (PUT ENDPOINT)
<ResourceEndpoint :resource="'webhook'" :endpoint="'put'" :lang="'hu'">

<template v-slot:request>

<<< @/docs/fixtures/api/webhook/request/put.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/webhook/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/webhook/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (DELETE ENDPOINT)
<ResourceEndpoint :resource="'webhook'" :endpoint="'delete'" :lang="'hu'"/>

## Példák

- [**"Új rendelés feladás" webhook működése**](../development/api-examples/06_webhook.md)