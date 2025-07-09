# URL Alias Resource

## Properties

<ResourceProperties :resource="'url_alias'" :lang="'en'"/>

<ResourceScopes :resource="'url_alias'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'url_alias'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/url_alias/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/url_alias/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'url_alias'" :endpoint="'getCollection'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/url_alias/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/url_alias/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'url_alias'" :endpoint="'post'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/url_alias/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/url_alias/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/url_alias/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (PUT ENDPOINT)
<ResourceEndpoint :resource="'url_alias'" :endpoint="'put'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/url_alias/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/url_alias/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/url_alias/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (DELETE ENDPOINT)
<ResourceEndpoint :resource="'url_alias'" :endpoint="'delete'" :lang="'en'"/>

