# Document Resource

## Properties

<ResourceProperties :resource="'document'" :lang="'en'"/>

<ResourceScopes :resource="'document'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'document'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/document/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/document/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'document'" :endpoint="'getCollection'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/document/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/document/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'document'" :endpoint="'post'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/document/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/document/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/document/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (PUT ENDPOINT)
<ResourceEndpoint :resource="'document'" :endpoint="'put'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/document/request/put.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/document/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/document/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (DELETE ENDPOINT)
<ResourceEndpoint :resource="'document'" :endpoint="'delete'" :lang="'en'"/>

