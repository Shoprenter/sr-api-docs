# Order Extend Resource

## Properties

<ResourceProperties :resource="'order_extend'" :lang="'en'"/>

## Types of shipping method

Possible values for **shippingMethodExtension**:

| Name                                | Value             |
|-------------------------------------|-------------------|
| Receiving points                    | RECEIVINGPOINT    |
| Parcel Sender - (Beta)              | PARCEL DELIVERY   |
| DHL Express                         | DHL EXPRESS       |
| DPD parcel point                    | DPDPARCELSHOP     |
| FoxPost Parcel Vending Machine      | FOXPOST           |
| FoxPost Home Delivery               | FOXPOST AUTOMATIC |
| GLS package point (old)             | GLSPARCELSHOP     |
| GLS package point                   | GLSPARCELPOINT    |
| GLS parcel machine                  | GLSPARCELLOCKER   |
| MPL Parcel Vending Machine          | MPLPARCELMACHINE  |
| MPL Posta Point delivery            | MPLPOSTPOINT      |
| MPL Delivery in post office         | MPLPOSTSTAY       |
| Pick Pack Point Delivery            | PICKUP POINT      |
| Express One package point           | TOFPARCELSHOP     |
| Home delivery with courier service  | WSESHIP           |
| Personal collection                 | WSESHIP           |

## Payment method types

Possible values of **paymentMethodCode**:

| Megnevezés                      | Value                 |
|---------------------------------|-----------------------|
| PayU                            | PAYU                  |
| OTP online áruhitel             | OTP                   |
| CIB bankkártyás fizetés         | CIB                   |
| Cash on delivery                       | COD, COD2, COD3, COD4 |
| Cetelem fizetési mód            | CETELEM               |
| Banki átutalás                  | BANK_TRANSFER         |
| PayPal                          | PAYPAL                |
| Csekkbefizetés                  | CHEQUE                |
| Loyaltypoint beváltás              | LOYALTYPOINT          |
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
<ResourceEndpoint :resource="'order_extend'" :endpoint="'get'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/order_extend/response/json/get_id.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/order_extend/response/xml/get_id.xml

</template>

</ResourceEndpoint>

[//]: <> (GETCOLLECTION ENDPOINT)
<ResourceEndpoint :resource="'order_extend'" :endpoint="'getCollection'" :lang="'en'">

<template v-slot:responseJSON>

<<< @/docs/fixtures/api/order_extend/response/json/get_page.json

</template>

<template v-slot:responseXML>

<<< @/docs/fixtures/api/order_extend/response/xml/get_page.xml

</template>

</ResourceEndpoint>

