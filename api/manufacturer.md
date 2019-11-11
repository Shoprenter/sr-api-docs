# Manufacturer Resource

## Tulajdonságok

<ResourceProperties :resource="'manufacturer'" :lang="'hu'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'manufacturer'" :endpoint="'get'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/manufacturer/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/manufacturer/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'manufacturer'" :endpoint="'getCollection'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/manufacturer/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/manufacturer/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'manufacturer'" :endpoint="'post'" :lang="'hu'">

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
<ResourceEndpoint :resource="'manufacturer'" :endpoint="'put'" :lang="'hu'">

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
<ResourceEndpoint :resource="'manufacturer'" :endpoint="'delete'" :lang="'hu'"/>

