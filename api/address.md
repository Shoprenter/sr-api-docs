# Address Resource

## Tulajdonságok

<ResourceProperties :resource="'address'" :lang="'hu'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'address'" :endpoint="'get'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/address/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/address/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'address'" :endpoint="'getCollection'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/address/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/address/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'address'" :endpoint="'post'" :lang="'hu'">

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
<ResourceEndpoint :resource="'address'" :endpoint="'put'" :lang="'hu'">

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
<ResourceEndpoint :resource="'address'" :endpoint="'delete'" :lang="'hu'"/>

