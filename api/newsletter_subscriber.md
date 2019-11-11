# Newsletter Subscriber Resource

## Tulajdonságok

<ResourceProperties :resource="'newsletter_subscriber'" :lang="'hu'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'newsletter_subscriber'" :endpoint="'get'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/newsletter_subscriber/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/newsletter_subscriber/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'newsletter_subscriber'" :endpoint="'getCollection'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/newsletter_subscriber/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/newsletter_subscriber/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'newsletter_subscriber'" :endpoint="'post'" :lang="'hu'">

<template v-slot:request>

<<< @/docs/fixtures/api/newsletter_subscriber/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/newsletter_subscriber/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/newsletter_subscriber/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (PUT ENDPOINT)
<ResourceEndpoint :resource="'newsletter_subscriber'" :endpoint="'put'" :lang="'hu'">

<template v-slot:request>

<<< @/docs/fixtures/api/newsletter_subscriber/request/put.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/newsletter_subscriber/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/newsletter_subscriber/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (DELETE ENDPOINT)
<ResourceEndpoint :resource="'newsletter_subscriber'" :endpoint="'delete'" :lang="'hu'"/>

