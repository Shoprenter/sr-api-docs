# Price Multiplier Resource

## Properties

<ResourceProperties :resource="'price_multiplier'" :lang="'en'"/>

<ResourceScopes :resource="'price_multiplier'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'price_multiplier'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/price_multiplier/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/price_multiplier/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'price_multiplier'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/price_multiplier/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/price_multiplier/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'price_multiplier'" :endpoint="'post'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/price_multiplier/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/price_multiplier/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/price_multiplier/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (PUT ENDPOINT)
<ResourceEndpoint :resource="'price_multiplier'" :endpoint="'put'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/price_multiplier/request/put.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/price_multiplier/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/price_multiplier/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (DELETE ENDPOINT)
<ResourceEndpoint :resource="'price_multiplier'" :endpoint="'delete'" :lang="'en'"/>

