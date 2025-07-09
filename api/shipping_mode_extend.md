# Shipping Mode Extend Resource

## Properties

<ResourceProperties :resource="'shipping_mode_extend'" :lang="'en'"/>

<ResourceScopes :resource="'shipping_mode_extend'"/>

## Types of shipping mode

Possible values for **extension**:

| Name                               | Value              |
|------------------------------------|--------------------|
| Receiving points                   | RECEIVINGPOINT     |
| Parcel Sender - (Beta)             | PARCEL DELIVERY    |
| DHL Express                        | DHL EXPRESS        |
| DPD parcel point                   | DPDPARCELSHOP      |
| FoxPost Parcel Vending Machine     | FOXPOST            |
| FoxPost Home Delivery              | FOXPOST AUTOMATIC  |
| GLS package point (old)            | GLSPARCELSHOP      |
| GLS package point                  | GLSPARCELPOINT     |
| GLS parcel machine                 | GLSPARCELLOCKER    |
| MPL Parcel Vending Machine         | MPLPARCELMACHINE   |
| MPL Post Point delivery           | MPLPOSTPOINT       |
| MPL Delivery in post office        | MPLPOSTSTAY        |
| Sameday shipping                   | SAMEDAYSHIPPING    |
| Shoprenter Go GLS Home delivery | SHOPRENTERGOGLSSHIPPING |
| Shoprenter Go GLS Parcel point | SHOPRENTERGOGLSPARCELPOINT |
| Shoprenter Go GLS Parcel locker | SHOPRENTERGOGLSPARCELLOCKER |
| Easybox parcel locker              | EASYBOX            |
| Pick Pack Point Delivery           | PICKUP POINT       |
| Express One package point          | TOFPARCELSHOP      |
| Home delivery with courier service | WSESHIP            |
| Personal collection                | WSESHIP            |
| Wolt courier service               | WOLT               |


## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'shipping_mode_extend'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/shipping_mode_extend/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/shipping_mode_extend/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'shipping_mode_extend'" :endpoint="'getCollection'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/shipping_mode_extend/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/shipping_mode_extend/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'shipping_mode_extend'" :endpoint="'post'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/shipping_mode_extend/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/shipping_mode_extend/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/shipping_mode_extend/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (PUT ENDPOINT)
<ResourceEndpoint :resource="'shipping_mode_extend'" :endpoint="'put'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/shipping_mode_extend/request/put.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/shipping_mode_extend/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/shipping_mode_extend/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (DELETE ENDPOINT)
<ResourceEndpoint :resource="'shipping_mode_extend'" :endpoint="'delete'" :lang="'en'"/>

