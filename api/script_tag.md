# Script Tag Resource

## Properties

<ResourceProperties :resource="'script_tag'" :lang="'en'"/>

<ResourceScopes :resource="'script_tag'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'script_tag'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/script_tag/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/script_tag/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'script_tag'" :endpoint="'getCollection'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/script_tag/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/script_tag/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'script_tag'" :endpoint="'post'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/script_tag/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/script_tag/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/script_tag/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (PUT ENDPOINT)
<ResourceEndpoint :resource="'script_tag'" :endpoint="'put'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/script_tag/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/script_tag/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/script_tag/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (DELETE ENDPOINT)
<ResourceEndpoint :resource="'script_tag'" :endpoint="'delete'" :lang="'en'"/>

