# CMS Content Description Resource

## Tulajdonságok

<ResourceProperties :resource="'cms_content_description'" :lang="'hu'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'cms_content_description'" :endpoint="'get'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/cms_content_description/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/cms_content_description/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'cms_content_description'" :endpoint="'getCollection'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/cms_content_description/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/cms_content_description/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'cms_content_description'" :endpoint="'post'" :lang="'hu'">

<template v-slot:request>

<<< @/docs/fixtures/api/cms_content_description/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/cms_content_description/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/cms_content_description/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (PUT ENDPOINT)
<ResourceEndpoint :resource="'cms_content_description'" :endpoint="'put'" :lang="'hu'">

<template v-slot:request>

<<< @/docs/fixtures/api/cms_content_description/request/put.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/cms_content_description/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/cms_content_description/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (DELETE ENDPOINT)
<ResourceEndpoint :resource="'cms_content_description'" :endpoint="'delete'" :lang="'hu'"/>

