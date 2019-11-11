# List Attribute Widget Resource

## Tulajdonságok

<ResourceProperties :resource="'list_attribute_widget'" :lang="'hu'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'list_attribute_widget'" :endpoint="'get'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/list_attribute_widget/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/list_attribute_widget/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'list_attribute_widget'" :endpoint="'getCollection'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/list_attribute_widget/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/list_attribute_widget/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'list_attribute_widget'" :endpoint="'post'" :lang="'hu'">

<template v-slot:request>

<<< @/docs/fixtures/api/list_attribute_widget/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/list_attribute_widget/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/list_attribute_widget/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (PUT ENDPOINT)
<ResourceEndpoint :resource="'list_attribute_widget'" :endpoint="'put'" :lang="'hu'">

<template v-slot:request>

<<< @/docs/fixtures/api/list_attribute_widget/request/put.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/list_attribute_widget/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/list_attribute_widget/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (DELETE ENDPOINT)
<ResourceEndpoint :resource="'list_attribute_widget'" :endpoint="'delete'" :lang="'hu'"/>

