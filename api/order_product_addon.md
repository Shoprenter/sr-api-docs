# Order Product Addon Resource

## Properties

<ResourceProperties :resource="'order_product_addon'" :lang="'en'"/>

<ResourceScopes :resource="'order_product_addon'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'order_product_addon'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/order_product_addon/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/order_product_addon/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'order_product_addon'" :endpoint="'getCollection'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/order_product_addon/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/order_product_addon/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'order_product_addon'" :endpoint="'post'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/order_product_addon/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/order_product_addon/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/order_product_addon/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (PUT ENDPOINT)
<ResourceEndpoint :resource="'order_product_addon'" :endpoint="'put'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/order_product_addon/request/put.json

</template>


<template v-slot:responseJSON>

<<< @/docs/fixtures/api/order_product_addon/response/json/get_id.json

</template>
 

<template v-slot:responseXML>

<<< @/docs/fixtures/api/order_product_addon/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (DELETE ENDPOINT)
<ResourceEndpoint :resource="'order_product_addon'" :endpoint="'delete'" :lang="'en'"/>

