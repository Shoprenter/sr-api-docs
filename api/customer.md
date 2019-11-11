# Customer Resource

## Tulajdonságok

<ResourceProperties :resource="'customer'" :lang="'hu'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'customer'" :endpoint="'get'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/customer/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/customer/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'customer'" :endpoint="'getCollection'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/customer/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/customer/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'customer'" :endpoint="'post'" :lang="'hu'">

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
<ResourceEndpoint :resource="'customer'" :endpoint="'put'" :lang="'hu'">

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
<ResourceEndpoint :resource="'customer'" :endpoint="'delete'" :lang="'hu'"/>

