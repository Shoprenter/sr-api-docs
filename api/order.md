# Order Resource

## Tulajdonságok

<ResourceProperties :resource="'order'" :lang="'hu'"/>

## Szállítási mód típusok

A **shippingMethodExtension** lehetséges értékei:

| Megnevezés                        | Érték            |
|-----------------------------------|------------------|
| Átvevőpontok                      | RECEIVINGPOINT   |
| Csomagküldő - (Béta)              | CSOMAGKULDO      |
| DHL Express                       | DHLEXPRESS       |
| DPD csomagpont                    | DPDPARCELSHOP    |
| FoxPost Csomagautomata            | FOXPOST          |
| FoxPost Házhozszállítás           | FOXPOSTAUTOMATA  |
| GLS csomagpont (régi)             | GLSPARCELSHOP    |
| GLS csomagpont                    | GLSPARCELPOINT   |
| GLS csomagautomata                | GLSPARCELLOCKER  |
| MPL Csomagautomata                | MPLPARCELMACHINE |
| MPL Posta Pont szállítás          | MPLPOSTPOINT     |
| MPL Postán maradó szállítás       | MPLPOSTSTAY      |
| Pick Pack Pont szállítás          | PICKPACKPONT     |
| Express One csomagpont            | TOFPARCELSHOP    |
| Házhozszállítás futárszolgálattal | WSESHIP          |
| Személyes átvétel                 | WSESHIP          |

## Fízetés mód típusok

A **paymentMethodCode** lehetséges értékei:

| Megnevezés                      | Érték                 |
|---------------------------------|-----------------------|
| PayU                            | PAYU                  |
| OTP online áruhitel             | OTP                   |
| CIB bankkártyás fizetés         | CIB                   |
| Utánvétel                       | COD, COD2, COD3, COD4 |
| Cetelem fizetési mód            | CETELEM               |
| Banki átutalás                  | BANK_TRANSFER         |
| PayPal                          | PAYPAL                |
| Csekkbefizetés                  | CHEQUE                |
| Hűségpont beváltás              | LOYALTYPOINT          |
| Escalion                        | ESCALION              |
| Unicredit                       | UNICREDIT             |
| Euplatesc                       | EUPLATESC             |
| PaySecure                       | PAYSECURE             |
| Fizetés a Pick Pack Ponton      | PICKPACKPONT          |
| K&H Bank kártyás fizetés        | KHB                   |
| Barion bankkártyás fizetés      | BARION                |
| Fizetés FoxPoston bankkártyával | FOXPOST_CREDIT_CARD   |
| Simple                          | SIMPLE                |
| Simple átutalás                 | SIMPLEWIRE            |
| Sofort banking                  | SOFORT                |
| Borgun (B-payment)              | SRPAY                 |
| Borgun                          | BORGUN                |
| Budapest Bank online áruhitel   | BUDAPESTBANK          |
| Global Payments                 | GP                    |
| Paysafecard                     | PAYSAFECARD           |
| Paysafecash                     | PAYSAFECASH           |
| Global Payments                 | GP                    |
| Wirecard QPAY                   | QPAY                  |
| Saferpay - SIX Payment Services | SAFERPAY              |
| InstaCash részletfizetés        | INSTACASH             |

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'order'" :endpoint="'get'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/order/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/order/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'order'" :endpoint="'getCollection'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/order/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/order/response/xml/get_page.xml

</template>

</ResourceEndpoint>

[//]: <> (POST ENDPOINT)
<ResourceEndpoint :resource="'order'" :endpoint="'post'" :lang="'hu'">

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
<ResourceEndpoint :resource="'order'" :endpoint="'put'" :lang="'hu'">

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
<ResourceEndpoint :resource="'order'" :endpoint="'delete'" :lang="'hu'"/>

