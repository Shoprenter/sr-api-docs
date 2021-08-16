# Teszt üzemmód

Lehetőséget adunk arra, hogy a Payment API integrációját - annak fejlesztése közben - biztonságosan lehessen tesztelni.
Ahhoz, hogy egy fizetést teszt üzemmódban indítsuk el, az új fizetést létrehozásánál, ami lehet [egyszeri](../docs/one_time_charge.md) vagy akár [ismétlődő](../docs/recurring_charge.md), a payload-nak tartalmaznia kell a **test** tulajdonságot **true** értékkel.

Példa POST adatokra recurring charge esetén:

```javascript
{
    "planId": 1,
    "notificationUrl": "https://notification-webhook-url.com",
    "failedUrl": "https://failedUrl.com",
    "successUrl": "https://successUrl.com",
    "test": true
}
```
Ebben az esetben a bankkártyás fizetés sandbox üzemmódban indul. Számlakiállítás nem történik.
Ehelyett, a bolt számlázási adataiban megadott email címre, egy adat összesítőt küld ki a rendszer.
Így ellenőrízhető, hogy éles fizetés esetén is, megfelelő adatokkal állítódna ki a számla.

Teszt Barion kártyaadatok:
https://docs.barion.com/Sandbox

Sikeres teszt kártyás fizetési adatok:<br>
Kártyaszám: **4444 8888 8888 5559**<br>
Lejárati idő: **Bármilyen jövőbeli dátum pl: 12/25**<br>
CVC: **Bármilyen háromjegyű szám pl: 123**<br>

Sikertelen teszt kártyás fizetési adatok:<br>
Kártyaszám: **4444 8888 8888 4446**<br>
Lejárati idő: **Bármilyen jövőbeli dátum pl: 12/25**<br>
CVC: **Bármilyen háromjegyű szám pl: 123**<br>
