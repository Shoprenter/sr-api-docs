# Order Extend Resource

## Tulajdonságok

<ResourceProperties :resource="'order_extend'" :lang="'hu'"/>

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
| Sameday házhozszállítás           | SAMEDAYSHIPPING  |
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
| MBH online áruhitel             | MBH                   |
| Global Payments                 | GP                    |
| Paysafecard                     | PAYSAFECARD           |
| Paysafecash                     | PAYSAFECASH           |
| Global Payments                 | GP                    |
| QENTA QPAY                      | QENTA_QPAY            |
| Saferpay - SIX Payment Services | SAFERPAY              |
| InstaCash részletfizetés        | INSTACASH             |
| IzzyPay                         | IZZYPAY               |
| PastPay                         | PASTPAY               |

## Endpoints

[//]: <> (GET ENDPOINT)
<ResourceEndpoint :resource="'order_extend'" :endpoint="'get'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/order_extend/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/order_extend/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'order_extend'" :endpoint="'getCollection'" :lang="'hu'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/order_extend/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/order_extend/response/xml/get_page.xml

</template>

</ResourceEndpoint>
