# Bankkártya csere

Az Ismétlődő díjfizetések esetén problémát jelenthetnek az olyan bankkártyák, amelyek meghaladták a lejárati idejüket, esetleg más probléma miatt nem terhelhetőek.

## Működése

Nagyon hasonló az [Ismétlődő díjfizetés](./i_recurring_charge.md) folyamatához.
Az alkalmazás egy hívást indít a billing/fundingSourceChange végpontra, ahova elküldi az Ismétlődő díjfizetés azonosítóját.
Ekkor a visszakap egy **changeUrl**-t, amelyre az alkalmazás átirányítja az előfizetőt.

A bolt tualjdonos megérkezik a kártya csere megerősítő oldalára, amely a Shoprenter admin felületén lesz elérhető.
A kártya cserét elfogadhatja vagy elutasíthatja.

Az elfogadás után, a Barion Gatewayen megadja az új kártyájának az adatait, és 10 Ft-os tranzakcióval regisztráljuk az új fizető eszközt az adott előfizetéshez.

Sikeres fizetés esetén **azonnal** visszautaljuk a levont 10 Ft-ot.

A folyamat végén a bolt tulajdonost visszairányítjuk egy, sikerességet vagy sikertelenséget jelző oldalra.

Csak Ismétlődő díjfizetések esetén cserélhető a bankkártya!

## Használata

Szükségünk van:
- Az alkalmazásunk felületén egy gombra, amivel elindíthatja az előfizető a cserét
- Az Ismétlődő fizetés azonosítójára - recurringChargeId
- Egy nofication url-re (opcionális) - notificationUrl

**Fontos:** 
- Csak a ACTIVE és FROZEN státuszú és
- csak a 2021.05.19-ke után 

létrejött előfizetések esetén lehet kérvényezni a kártyacserét.

## Belépési pont

POST https://<bolt_név>.api.myshoprenter.hu/billing/fundingSourceChange

Példa payload:

```javascript
{
    "recurringChargeId": 12, 
    "notificationUrl": "https://notficationUrl.com"
}
```

Példa response:

```javascript
{
        "changeId": 43, 
        "subscriptionId": 12, 
        "paymentStatus": "active", 
        "status": "pending", 
        "changeUrl": "https://<shop_domain>/admin/app/payment/12/change/43",
        "notificationUrl": "https://notficationUrl.com", 
        "createdAt": "2022-05-09 08:09:41"
}
```

A kártyacsere folyamat során generálódó státuszokról itt olvashatsz: [Kártya csere státuszok](./k_statuses.md) 

## Tesztelés

Teszteléshez szükségünk van egy teszt Ismétlődő díjfizetésre, erről [itt](./e_test.md) olvashatsz bővebben. Ezen a fizetésen végrehajtott bankkártya csere is a teszt rendszerben fog történni.

## Webhook

Itt is van lehetőség értesítést kérni az állapot változásokról a kártyacsere folyamattal kapcsolatosan.
További információt itt találsz: [Értesítés webhookok - a notificationUrl](./l_notifications.md)
