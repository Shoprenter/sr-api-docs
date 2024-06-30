# List Attribute Extend Resource

## ATTENTION!
A maximum of 300 product attributes can be created!

## Properties

<ResourceProperties :resource="'list_attribute_extend'" :lang="'en'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'list_attribute_extend'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/list_attribute_extend/response/json/get_id.json

</template>
<template v-slot:responseXML>

<<< @/docs/fixtures/api/list_attribute_extend/response/xml/get_id.xml

</template>

</ResourceEndpoint>


