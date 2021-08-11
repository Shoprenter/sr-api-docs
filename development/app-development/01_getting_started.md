# Kezdeti lépések

### Az Alkalmazás regisztrációjához szükséges adatok:

A szükséges adatokat kérjük elküldeni a partnersupport@shoprenter.hu email címre.

**Az alkalmazás tulajának a következő adatokat kell biztosítania.**
- **Alkalmazás neve:** ez fog megjelenni a telepíthető alkalmazások listájába.
- **EntryPoint:** Az alkalmazás belépési pontja. Az alkalmazás fejlesztője adja. HTTPS-protokollon keresztül elérhetőnek kell lennie.
- **RedirectUri:** Az alkalmazás authentikációs belépési pontja ezen az URL-en keresztül fogja az authentikációs adatokat igényelni az adott Shoprenter-es bolt API-jához. HTTPS protokollon keresztül elérhetőnek kell lennie. 
  **Figyelem!** Ha pl. egy Single-Page Application (SPA) lesz a kliens, ahol URL resource azonosítóval van megadva egy-egy route (`https://example.com/shoprenter#redirect`), azt technikai okok miatt nem tudjuk elfogadni.
- **UninstallUri:** Az alkalmazás törlése után egy GET kérés lesz elküldve erre az URL-re, hogy az alkalmazás még egy utolsó műveletet tudjon végrehajtani. 
  (Megjegyzés: query string-ben hozzá lesznek fűzve a következő adatok: `shopname`, `code`, `timestamp`, `hmac`.)
- **Alkalmazás logo:** az alkalmazás listában megjelenő logó kép (**250x150px**).
- **Alkalmazás rövid leírása:** Maximum 70 karakteres rövid szöveg.
- **Alkalmazás részletek link:** Az alkalmazás részleteire/sales oldalára mutató link.
- **Alakalmazás típusa:** Az alkalmazásnak két formája van:
  - Beágyazott: Az EntryPoint-nak megadott URL-t betöltjük egy Iframe-be, amit az alkalmazáshoz tartozó URL-en lehet elérni, a Shoprenter admin felületén (pl. `https://shopname.myshoprenter.hu/admin/app/1`).
  - Átírányított: Átírányításnál a felhasználót szimplán átírányítjuk a megadott EntryPoint URL-re.
- **A tesztbolt neve:** A fejlesztés legelején igényelni kell egy próbaboltot a [shoprenter.hu](https://www.shoprenter.hu/) oldalon. 
  Itt megadható a boltnév, ami a bolt domain első részeben - `[boltNev].myshoprenter.hu` - lesz látható.

**Az alkalmazás regisztrálása után, a következő adatokat küldi el a Partner Support:**
- **AppId:** az alkalmazás azonosítója a Shoprenteren belül. 
- **ClientId:** az alkalmazás azonosító.
- **ClientSecret:** kulcs a kérések azonosításához.
- **App URL:** az alkalmazás admin oldali Shoprenter-es URL-je. Pl.: `demo.myshoprenter.hu/admin/app/55`

### Alkalmazás telepítésének menete:
1. A felhasználó az alkalmazás telepítésére kattint a Shoprenter admin felületén.
2. A Shoprenter meghívja az alkalmazás fejlesztője által megadott RedirectUri-t (GET Request).
    A hívás során átadott paraméterek:
    - **shopname:** a bolt neve amiből a hívást indították
    - **code:** generált hash
    - **timestamp:** kérés ideje
    - **hmac:** ellenőrző hash
    - **app_url** Az az URL, amire vissza kell irányítani a felhasználót a RedirectUri alatt lévő script lefutása után
3. Kiszolgáló félnek célszerű ellenőrizni, hogy a kérést valóban a Shoprenter küldte.
   Annak ellenőrzése, hogy a kérést a Shoprenter küldte:
   A query string HMAC nélküli részének (`code=0907a61c0c8d55e99db179b68161bc00&shopname=example&timestamp=1337178173`) a **ClientSecret**-el sha256 algoritmussal elkódolva egyenértékűnek kell lennie a query string HMAC paraméterének értékével.
4. Ha a kiszolgáló fél rendben találta a kérést, küld egy POST Request-et a Shoprenter felé a `https://[shopname].myshoprenter.hu/admin/oauth/access_credential` URL-re. Ezzel a kéréssel tudja az alkalmazás kikérni az adott bolt API-jának használatához szükséges username/password párost.<br>
  **A POST Request _multipart/form-data_ típusként kell elküldeni.**<br>
   
   A kérés payload-jának tartalmaznia kell az alábbi mezőket:
    - **client_id:** Az alkalmazás ClientId-ja
    - **client_secret:** Az alkalmazás ClientSecret értéke 
    - **code:** a Request-ben kapott code
    - **timestamp:** a Request-ben kapott timestamp
    - **hmac:** a Request-ben kapott HMAC

A username/password páros egy JSON Response-al érkezik meg, pl.:<br><br>
`{"username":"YLQVeH2sFFptfR88LjDXb4A","password":"AcmNWFmzSPaqfNXdnaeN6D5"}` <br><br>
    
  Amennyiben valamelyik adat hiányos vagy téves, úgy az API hibaüzenetet fog küldeni a megfelelő hibakóddal JSON formátumban.
    
  <br>**Hibák**:
  - Ha elküldendő adatok közül valamelyik hiányzik, akkor `{"message":"Missing data in credential request","code":400}` választ fog adni.
  - Ha elküldendő client_id és secret_id eltér, akkor `{"message":"App client and request client data mismatch","code":401}` választ fog adni.
  - Ha a hitelesítési idő meghaladja a 30 másodpercet, akkor `{"message":"Authorization time expired","code":408}` választ fog adni.
  - Ha a telepítés közben hiba merült fel, akkor  `{"message":"App is not installed","code":409}` választ fog adni.
6. Amennyiben a Shoprenter megfelelőnek találja a POST Request-et egy `username`, `password` párossal fog válaszolni, amivel az alkalmazás hozzáfér az adott bolt API-jához. 
   A 2. lépésben indított Shoprenteres kérésben lévő timestamp arra szolgál, hogy megvizsgáljuk, a kliens alkalmazás **30 másodpercen belül** megkezdi-e a API hozzáférés kérését!
7. Ha az alkalmazás megkapta az authentikációs adatokat, a felhasználót át kell irányítani a query string-ben kapott **app_url**-re.
8. A Shoprenter megnyitja az alkalmazáshoz tartozó EntryPoint-ot. A Request tartalmazni fogja a 2. pontban írt paramétereket.
9. Feltelepítés után a Shoprenter csak az Entrypoint-ra küld kéréseket. Minden esetben a 2. pontban írt paraméterekkel.

**Megjegyzés:** Van lehetőség egyedi query string paraméterekkel dekorálni az `app_url` értékét (az alkalmazás Shoprenteres URL-jét).
  Ezek a paraméterek az EntryPoint URL-ben is meg fognak jelenni, az authentikációhoz használt paraméterek (`shopname`, `code`, `timestamp`, `hmac`) mellett.

  Példa:
  Legyen az EntryPoint: `https://app.example.com/entryPoint`
  Erre irányít át az alkalmazás: `https://[primaryDomain]/admin/app/[appId]?pelda=parameter`
  Ez esetben az EntryPoint íly módon hívódik meg: `https://app.example.com/entryPoint?shopname=[shopname]&code=[code]&timestamp=[timestamp]&hmac=[hmac]&pelda=parameter`

### Példa alkalmazások
- [SR Demo app PHP](https://github.com/Shoprenter/sr-demo-app-php)
- [SR Demo app PHP Slim](https://github.com/Shoprenter/sr-demo-app-php-slim)
- [SR Demo app Node.js](https://github.com/Shoprenter/sr-demo-app-node)
