# Product Class Resource

## ATTENTION!
The functionality of the product class feature will change in the Shoprenter API from June 3, 2024. The fix is necessary because the different operations of the API and the admin interface can lead to inconsistent states. By standardizing, however, we can simplify and make the management of product types more efficient.

The changes will result in backward incompatible operation. We ask everyone who uses this part of the API to review the operation of the affected codes!

Further details can be read in the following [entry of the Shoprenter changelog.](https://changelog.shoprenter.hu/hu/termektipus-valtozasok-az-api_ban-juniustol-Vzq3OfnF)

## Properties

<ResourceProperties :resource="'product_class'" :lang="'en'"/>

<ResourceScopes :resource="'product_class'"/>

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'product_class'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/product_class/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/product_class/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'product_class'" :endpoint="'getCollection'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/product_class/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/product_class/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'product_class'" :endpoint="'post'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/product_class/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/product_class/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/product_class/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (PUT ENDPOINT)
<ResourceEndpoint :resource="'product_class'" :endpoint="'put'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/product_class/request/put.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/product_class/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/product_class/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (DELETE ENDPOINT)
<ResourceEndpoint :resource="'product_class'" :endpoint="'delete'" :lang="'en'"/>

## Possible Error Codes
These error codes will come into effect starting from June 3, 2024.

| Method(s) | HTTP Status Code | Error Code | Error Message |
| --- | --- | --- | --- |
| POST, PUT | 400 | 40021 | Both variant parameters cannot reference the same attribute! |
| POST, PUT | 400 | 40022 | Text attribute cannot be used as variant parameter |
| POST, PUT | 400 | 40023 | Only list attributes can have ICON select type |
| POST, PUT | 400 | 40024 | Another product class with the same name already exists! |
| DELETE | 400 | 40025 | Cannot delete product class which has products! |

## Examples
- [**Product attribute handling**](../development/api-examples/08_product_attribute_handling.md)
