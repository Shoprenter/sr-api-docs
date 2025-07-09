# Order Invoice Resource

## Properties

<ResourceProperties :resource="'order_invoice'" :lang="'en'"/>

<ResourceScopes :resource="'order_invoice'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'order_invoice'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/order_invoice/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/order_invoice/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'order_invoice'" :endpoint="'getCollection'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/order_invoice/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/order_invoice/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'order_invoice'" :endpoint="'post'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/order_invoice/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/order_invoice/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/order_invoice/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (PUT ENDPOINT)
<ResourceEndpoint :resource="'order_invoice'" :endpoint="'put'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/order_invoice/request/put.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/order_invoice/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/order_invoice/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (DELETE ENDPOINT)
<ResourceEndpoint :resource="'order_invoice'" :endpoint="'delete'" :lang="'en'"/>

