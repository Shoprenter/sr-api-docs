# File Resource

## Tulajdonságok

<ResourceProperties :resource="'file'" :lang="'hu'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'file'" :endpoint="'get'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/file/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/file/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'file'" :endpoint="'post'" :lang="'hu'">

<template v-slot:request>

<<< @/docs/fixtures/api/file/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/file/response/json/post.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/file/response/xml/post.xml

</template>

</ResourceEndpoint>

[//]: <> (DELETE ENDPOINT)
<ResourceEndpoint :resource="'file'" :endpoint="'delete'" :lang="'hu'"/>

