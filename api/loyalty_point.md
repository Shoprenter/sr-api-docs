# Loyalty Point Resource

## Properties

<ResourceProperties :resource="'loyalty_point'" :lang="'en'"/>

<ResourceScopes :resource="'loyalty_point'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'loyalty_point'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/loyalty_point/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/loyalty_point/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'loyalty_point'" :endpoint="'getCollection'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/loyalty_point/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/loyalty_point/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'loyalty_point'" :endpoint="'post'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/loyalty_point/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/loyalty_point/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/loyalty_point/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (PUT ENDPOINT)
<ResourceEndpoint :resource="'loyalty_point'" :endpoint="'put'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/loyalty_point/request/put.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/loyalty_point/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/loyalty_point/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (DELETE ENDPOINT)
<ResourceEndpoint :resource="'loyalty_point'" :endpoint="'delete'" :lang="'en'"/>

