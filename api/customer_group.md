# Customer Group Resource

## Properties

<ResourceProperties :resource="'customer_group'" :lang="'en'"/>

<ResourceScopes :resource="'customer_group'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'customer_group'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/customer_group/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/customer_group/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'customer_group'" :endpoint="'getCollection'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/customer_group/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/customer_group/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'customer_group'" :endpoint="'post'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/customer_group/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/customer_group/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/customer_group/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (PUT ENDPOINT)
<ResourceEndpoint :resource="'customer_group'" :endpoint="'put'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/customer_group/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/customer_group/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/customer_group/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (DELETE ENDPOINT)
<ResourceEndpoint :resource="'customer_group'" :endpoint="'delete'" :lang="'en'"/>

## Examples

- [**Product special**](../development/api-examples/01_0_product_special.md)
- [**Product of day**](../development/api-examples/01_1_product_special_product_of_day.md)
