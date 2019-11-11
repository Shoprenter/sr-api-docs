# Loyalty Point Resource

## Tulajdonságok

<ResourceProperties :resource="'loyalty_point'" :lang="'hu'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'loyalty_point'" :endpoint="'get'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/loyalty_point/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/loyalty_point/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'loyalty_point'" :endpoint="'getCollection'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/loyalty_point/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/loyalty_point/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'loyalty_point'" :endpoint="'post'" :lang="'hu'">

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
<ResourceEndpoint :resource="'loyalty_point'" :endpoint="'put'" :lang="'hu'">

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
<ResourceEndpoint :resource="'loyalty_point'" :endpoint="'delete'" :lang="'hu'"/>

