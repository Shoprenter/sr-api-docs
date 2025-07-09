# File Resource

## Properties

<ResourceProperties :resource="'file'" :lang="'en'"/>

<ResourceScopes :resource="'file'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'file'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/file/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/file/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'file'" :endpoint="'post'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/file/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/file/response/json/post.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/file/response/xml/post.xml

</template>

</ResourceEndpoint>

[//]: <> (DELETE ENDPOINT)
<ResourceEndpoint :resource="'file'" :endpoint="'delete'" :lang="'en'"/>

## Examples

- [**Attach image to product**](../development/api-examples/05_attach_uploaded_image_to_product.md)

