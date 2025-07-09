# Customer Resource

## Properties

<ResourceProperties :resource="'customer'" :lang="'en'"/>

<ResourceScopes :resource="'customer'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'customer'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/customer/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/customer/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'customer'" :endpoint="'getCollection'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/customer/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/customer/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'customer'" :endpoint="'post'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/customer/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/customer/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/customer/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (PUT ENDPOINT)
<ResourceEndpoint :resource="'customer'" :endpoint="'put'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/customer/request/put.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/customer/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/customer/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (DELETE ENDPOINT)
<ResourceEndpoint :resource="'customer'" :endpoint="'delete'" :lang="'en'"/>

