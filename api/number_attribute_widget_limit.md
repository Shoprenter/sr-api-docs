# Number Attribute Widget Limit Resource

## Tulajdonságok

<ResourceProperties :resource="'number_attribute_widget_limit'" :lang="'hu'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'number_attribute_widget_limit'" :endpoint="'get'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/number_attribute_widget_limit/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/number_attribute_widget_limit/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'number_attribute_widget_limit'" :endpoint="'getCollection'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/number_attribute_widget_limit/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/number_attribute_widget_limit/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'number_attribute_widget_limit'" :endpoint="'post'" :lang="'hu'">

<template v-slot:request>

<<< @/docs/fixtures/api/number_attribute_widget_limit/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/number_attribute_widget_limit/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/number_attribute_widget_limit/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (PUT ENDPOINT)
<ResourceEndpoint :resource="'number_attribute_widget_limit'" :endpoint="'put'" :lang="'hu'">

<template v-slot:request>

<<< @/docs/fixtures/api/number_attribute_widget_limit/request/put.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/number_attribute_widget_limit/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/number_attribute_widget_limit/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (DELETE ENDPOINT)
<ResourceEndpoint :resource="'number_attribute_widget_limit'" :endpoint="'delete'" :lang="'hu'"/>

