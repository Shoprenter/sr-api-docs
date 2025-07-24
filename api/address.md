# Address Resource

## Properties

<ResourceProperties :resource="'address'" :lang="'en'"/>

<ResourceScopes :resource="'address'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'address'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/address/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/address/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'address'" :endpoint="'getCollection'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/address/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/address/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'address'" :endpoint="'post'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/address/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/address/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/address/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (PUT ENDPOINT)
<ResourceEndpoint :resource="'address'" :endpoint="'put'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/address/request/put.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/address/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/address/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (DELETE ENDPOINT)
<ResourceEndpoint :resource="'address'" :endpoint="'delete'" :lang="'en'"/>

