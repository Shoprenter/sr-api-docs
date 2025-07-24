# Manufacturer Resource

## Properties

<ResourceProperties :resource="'manufacturer'" :lang="'en'"/>

<ResourceScopes :resource="'manufacturer'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'manufacturer'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/manufacturer/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/manufacturer/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'manufacturer'" :endpoint="'getCollection'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/manufacturer/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/manufacturer/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'manufacturer'" :endpoint="'post'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/manufacturer/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/manufacturer/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/manufacturer/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (PUT ENDPOINT)
<ResourceEndpoint :resource="'manufacturer'" :endpoint="'put'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/manufacturer/request/put.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/manufacturer/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/manufacturer/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (DELETE ENDPOINT)
<ResourceEndpoint :resource="'manufacturer'" :endpoint="'delete'" :lang="'en'"/>

