# Értesítés webhookok - a notificationUrl

A Payment API, a fizetési folyamat közben történő események üzeneteit a notificationUrl tulajdonságnál megadott URL-re küldi el.
A webhook tartalmazza a fizetési mód azonosítóját és a aktuális állapotát. A Payment API által küldött webhook kérés HTTP metódusa **POST**.

A státuszok vizsgálatával következtethetünk egy fizetési mód életciklusában bekövetkezett változásokra, esetleges hibákra.
A lehetséges státuszok itt érhetőek el: [elérhető státuszok](../docs/statuses.md).

## Az üzenet felépítése

### Ismétlődő és egyszeri díjfizetés

| Tulajdonság | Leírás                                                |
|-------------|-------------------------------------------------------|
| id          | Fizetés azonosítója. Ez lehet One Time vagy Recurring |
| status   |    A fizetési mód aktuális állapota |

#### Példa 

```javascript
{
    "id": 2,
    "status": "pending",
    "time": 1606740386
}
```

### Bankkártya csere

| Tulajdonság    | Leírás                               |
|----------------|--------------------------------------|
| changeId       | Kártya csere kérés azonosítója       |
| subscriptionId | Fizetés azonosítója                  |
 | status         | A csere állapota. Jelzi, hol tart a folyamat |
| paymentStatus  | A fizetési mód aktuális állapota     |
| message | Az esetleges hibákról ad tájékoztatást |

### Példa

```javascript
{
    "changeId": 42,
    "subscriptionId": 12,
    "status": "declined",
    "paymentStatus": "active",
    "message": "The Customer canceled this payment.",
    "time": 1651662894
}
```

## Webhook hitelesítése

A Payment API-tól érkező webhookok hitelesítését legkönnyebben a kiküldött url-hez hozzáfűzött **hmac** query paraméter és a post payloadban található time property közös ellenőrzésével lehet megvalósítani.

A hmac generálás a gyakorlatban úgy néz, hogy az alkalmazás felvétele során regisztrált **WebhookSecretKey*** használatával az elküldött post payloadot hash_hmac függvénnyel (sha256 algoritmussal) egy sztringet generálunk.
Amennyiben a fogadó fél, azaz alkalmazás elvégzi az előbbi műveletet és összeveti a webhookban található **hmac-kel** és az egyezik, akkor a webhook a Payment API-tól származhat.

Az autentikálás második felében továbbá érdemes ellenőrizni, hogy a post payloadban található **time** propertyben tárolt timestamp körülbelül egybeesik-e a webhook beérkezésének timestampjével.
A time property és a beérkezés ideje között pár másodperc különbség is adódhat. Az ideális időkülönbség kialakítása az alkalmazás fejlesztő feladata.

**Fontos megjegyezni, hogy a Payment API kiküldéskor előállított timestampje a Etc/UTC (UTC, +0000) időzóna alapján van generálva!**

*Ha még nem rendelkezünk WebhookSecretKey-el, a partnersupport@shoprenter.hu email címen megtehetjük.

## Példa HMAC generálás

<table>
    <tr>
        <td>URL</td>
        <td>https://example.com/</td>
    </tr>
    <tr>
        <td>Post payload (one-line stringként szóközök nélkül)</td>
        <td>{"id":69,"status":"pending","time":1606740386}</td>
    </tr>
    <tr>
        <td>WebhookSecretKey</td>
        <td>ppmunf3z66qx6c9cpo0klmyq</td>
    </tr>
    <tr>
        <td>HMAC<br>hash_hmac('sha256', $payload, $webhookSecretKey);</td>
        <td>317a52549acd37817dfdf2d8989c9386b3d448faa6bc2ff597c71eaa37c76ee3</td>
    </tr>
    <tr>
        <td>Teljes URL</td>
        <td>https://example.com?hmac=317a52549acd37817dfdf2d8989c9386b3d448faa6bc2ff597c71eaa37c76ee3</td>
    </tr>
</table>
