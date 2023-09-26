# Order Resource

## Properties

<ResourceProperties :resource="'order'" :lang="'en'"/>

## Shipping methods

Possible values for **shippingMethodExtension**:

| Description                        | Value            |
|------------------------------------|------------------|
| Pickup points                      | RECEIVINGPOINT   |
| Parcel sender - (Béta)             | CSOMAGKULDO      |
| DHL Express                        | DHLEXPRESS       |
| DPD package point                  | DPDPARCELSHOP    |
| FoxPost Parcel machine             | FOXPOST          |
| FoxPost Home delivery              | FOXPOSTAUTOMATA  |
| GLS package point (old)            | GLSPARCELSHOP    |
| GLS package point                  | GLSPARCELPOINT   |
| GLS Parcel machine                 | GLSPARCELLOCKER  |
| MPL Parcel machine                 | MPLPARCELMACHINE |
| MPL Post office transport          | MPLPOSTPOINT     |
| Delivery in the MPL post office    | MPLPOSTSTAY      |
| Pick Pack Pont transport           | PICKPACKPONT     |
| Express One package point          | TOFPARCELSHOP    |
| Home delivery with courier service | WSESHIP          |
| Personal pick up                   | WSESHIP          |


## Payment Methods

Possible values for **paymentMethodCode**:

| Description                     | Value                 |
|---------------------------------|-----------------------|
| PayU                            | PAY                   |
| OTP online goods loan           | OTP                   |
| CIB bank card CIB               |
| Cash on delivery                | COD, COD2, COD3, COD4 |
| Cetelem payment method          | CETELEM               |
| Bank transfer                   | BANK_TRANSFER         |
| PayPal                          | PAYPAL                |
| Check Deposit                   | CHECK                 |
| Loyalty points using            | LOYALTYPOINT          |
| Escalion                        | ESCALION              |
| Unicredit                       | UNICREDIT             |
| Euplatesc                       | EUPLATESC             |
| PaySecure                       | PAYSECURE             |
| Payment at the Pick Pack Point  | PICKUP POINT          |
| K&H Bank card card              | KHB                   |
| Barion bank card payment        | BARION                |
| Payment by FoxPoston bank card  | FOXPOST_CREDIT_CARD   |
| Simple                          | SIMPLE                |
| Simple transfer                 | SIMPLEWIRE            |
| Sofort banking                  | DRIVE                 |
| Borgun (B-payment)              | SRPAY                 |
| Borgun                          | BORGUN                |
| Budapest Bank online goods loan | BUDAPEST BANK         |
| Global Payments                 | GP                    |
| Paysafecard                     | PAYSAFECARD           |
| Paysafecash                     | PAYSAFECASH           |
| Global Payments                 | GP                    |
| Wirecard QPAY                   | QPAY                  |
| Saferpay - SIX Payment Services | SAFERPAY              |
| InstaCash                       | INSTACASH             |
| IzzyPay                         | IZZYPAY               |
| PastPay                         | PASTPAY               |

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'order'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/order/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/order/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'order'" :endpoint="'getCollection'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/order/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/order/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'order'" :endpoint="'post'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/order/request/post.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/order/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/order/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (PUT ENDPOINT)
<ResourceEndpoint :resource="'order'" :endpoint="'put'" :lang="'en'">

<template v-slot:request>

<<< @/docs/fixtures/api/order/request/put.json

</template>

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/order/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/order/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (DELETE ENDPOINT)
<ResourceEndpoint :resource="'order'" :endpoint="'delete'" :lang="'en'"/>
