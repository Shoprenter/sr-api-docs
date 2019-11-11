# Order Resource

## Tulajdonságok

<ResourceProperties :resource="'order'" :lang="'hu'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'order'" :endpoint="'get'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/order/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/order/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'order'" :endpoint="'getCollection'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/order/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/order/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'order'" :endpoint="'post'" :lang="'hu'">

<template v-slot:request>

<<< @/docs/fixtures/api/order/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/order/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/order/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (PUT ENDPOINT)
<ResourceEndpoint :resource="'order'" :endpoint="'put'" :lang="'hu'">

<template v-slot:request>

<<< @/docs/fixtures/api/order/request/put.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/order/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/order/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (DELETE ENDPOINT)
<ResourceEndpoint :resource="'order'" :endpoint="'delete'" :lang="'hu'"/>

