# Number Attribute Widget Resource

## Properties

<ResourceProperties :resource="'number_attribute_widget'" :lang="'en'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'number_attribute_widget'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/number_attribute_widget/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/number_attribute_widget/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'number_attribute_widget'" :endpoint="'getCollection'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/number_attribute_widget/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/number_attribute_widget/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'number_attribute_widget'" :endpoint="'post'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/number_attribute_widget/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/number_attribute_widget/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/number_attribute_widget/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (PUT ENDPOINT)
<ResourceEndpoint :resource="'number_attribute_widget'" :endpoint="'put'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/number_attribute_widget/request/put.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/number_attribute_widget/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/number_attribute_widget/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (DELETE ENDPOINT)
<ResourceEndpoint :resource="'number_attribute_widget'" :endpoint="'delete'" :lang="'en'"/>

