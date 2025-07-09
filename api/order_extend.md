# Order Extend Resource


## Properties

<ResourceProperties :resource="'order_extend'" :lang="'en'"/>

<ResourceScopes :resource="'order_extend'"/>

## Types of shipping method

Possible values for **shippingMethodExtension**:

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

## Payment method types

Possible values of **paymentMethodCode**:

| Name                            | Value                 |
|---------------------------------|-----------------------|
| PayU                            | PAYU                  |
| OTP online goods loan           | OTP                   |
| CIB credit card payment         | CIB                   |
| Cash on delivery                | COD, COD2, COD3, COD4 |
| Cetelem payment method          | CETELEM               |
| Bank Transfer                   | BANK_TRANSFER         |
| PayPal                          | PAYPAL                |
| Check payments                  | CHEQUE                |
| Loyalty point redemption        | LOYALTYPOINT          |
| Escalion                        | ESCALION              |
| Unicredit                       | UNICREDIT             |
| Euplatesc                       | EUPLATESC             |
| PaySecure                       | PAYSECURE             |
| Payment at the Pick Pack Point  | PICKPACKPONT          |
| K&H Bank credit card payment    | KHB                   |
| Barion credit card payment      | BARION                |
| Payment by FoxPoston bank card  | FOXPOST_CREDIT_CARD   |
| Simple                          | SIMPLE                |
| Simple transfer                 | SIMPLEWIRE            |
| Sofort banking                  | SOFORT                |
| Borgun (B-payment)              | SRPAY                 |
| Borgun                          | BORGUN                |
| MBH online goods credit         | MBH                   |
| Global Payments                 | GP                    |
| Paysafecard                     | PAYSAFECARD           |
| Paysafecash                     | PAYSAFECASH           |
| Global Payments                 | GP                    |
| QENTA QPAY                      | QENTA_QPAY            |
| Saferpay - SIX Payment Services | SAFERPAY              |
| InstaCash installment payment   | INSTACASH             |
| IzzyPay                         | IZZYPAY               |
| PastPay                         | PASTPAY               |
| Simple subscription             | SIMPLE_SUBSCRIPTION   |
| Barion subscription             | BARION_SUBSCRIPTION   |
| Stripe                          | STRIPE                |
| Viva Walet                      | VIVA_WALLET           |
| OTP Szép kártya                 | OTP_SZEP              |
| KHB Szép kártya                 | KHB_SZEP              |
| MKB Szép kártya                 | MKB_SZEP              |
| OTP EP kártya                   | OTP_EP                |
| Milpay                          | MILPAY                |

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
