# Order Total Resource

## Properties

<ResourceProperties :resource="'order_total'" :lang="'en'"/>

<ResourceScopes :resource="'order_total'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'order_total'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/order_total/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/order_total/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'order_total'" :endpoint="'getCollection'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/order_total/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/order_total/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'order_total'" :endpoint="'post'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/order_total/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/order_total/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/order_total/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (PUT ENDPOINT)
<ResourceEndpoint :resource="'order_total'" :endpoint="'put'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/order_total/request/put.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/order_total/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/order_total/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (DELETE ENDPOINT)
<ResourceEndpoint :resource="'order_total'" :endpoint="'delete'" :lang="'en'"/>

