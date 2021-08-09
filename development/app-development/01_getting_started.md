# Kezdeti lépések

### Az Alkalmazás integrációhoz szükséges adatok:

Az alkalmazás beregisztrálásához szükséges adatokat kérjük elküldeni a partnersupport@shoprenter.hu email címre.

**Az alkalmazás tulajának a következő adatokat kell biztosítania.**
- **Alkalmazás neve:** ez fog megjelenni a telepíthető alkalmazások listájába.
- **EntryPoint:** Az alkalmazás belépési pontja. Az alkalmazás fejlesztője adja. HTTPS-protokollon keresztül elérhetőnek kell lennie.
- **RedirectUri:** Az alkalmazás authentikációs belépési pontja ezen az URL-en keresztül fogja az authentikációs adatokat igényelni az adott Shoprenter-es bolt API-jához. HTTPS protokollon keresztül elérhetőnek kell lennie. 
  **Figyelem!** Ha pl. egy Single-Page Application (SPA) lesz a kliens, ahol URL resource azonosítóval van megadva egy-egy route (`https://example.com/shoprenter#redirect`), azt technikai okok miatt nem tudjuk elfogadni.
- **UninstallUri:** Az alkalmazás törlése után egy GET kérés lesz elküldve erre az URL-re, hogy az alkalmazás még egy utolsó műveletet tudjon végrehajtani. 
  (Megjegyzés: QueryString-ben hozzá lesznek fűzve a következő adatok: `shopname`, `code`, `timestamp`, `hmac`.)
- **Alkalmazás logo:** az alkalmazás listában megjelenő logó kép (**250x150px**).
- **Alkalmazás rövid leírása:** Maximum 70 karakteres rövid szöveg.
- **Alkalmazás részletek link:** Az alkalmazás részleteire/sales oldalára mutató link.
- **Alakalmazás típusa:** Az alkalmazásnak két formája van:
  - Beágyazott: Az EntryPoint-nak megadott URL-t betöltjük egy Iframe-be, amit az alkalmazáshoz tartozó URL-en lehet elérni, a Shoprenter admin felületén (pl. `https://shopname.myshoprenter.hu/admin/app/1`).
  - Átírányított: Átírányításnál a felhasználót szimplán átírányítjuk a megadott EntryPoint URL-re.
- **A tesztbolt neve:** A fejlesztés legelején igényelni kell egy próbaboltot a [shoprenter.hu](https://www.shoprenter.hu/) oldalon. 
  Itt megadható a boltnév, ami a bolt domain első részeben - `[boltNev].myshoprenter.hu` - lesz látható.

**Az alkalmazás rendszerbe való felvétele után a következő adatokat küldi el a Shoprenter:**
- **AppId:** az alkalmazás azonosítója a Shoprenteren belül. 
- **ClientId:** az alkalmazás azonosító.
- **ClientSecret:** kulcs a kérések azonosításához.
- **App URL:** az alkalmazás admin oldali Shoprenter-es URL-je.

### Alkalmazás telepítésének menete:
1. A felhasználó az alkalmazás telepítésére kattint a Shoprenter admin felületén.
2. A Shoprenter meghívja az alkalmazás által bíztosított RedirectUri-t (GET Request).
    A hívás során átadott paraméterek:
    - **shopname:** a bolt neve amiből a hívást indították
    - **code:** generált hash
    - **timestamp:** kérés ideje
    - **hmac:** ellenőrző hash
3. Kiszolgáló félnek célszerű ellenőrizni, hogy a kérést valóban a Shoprenter küldte.
   Annak ellenőrzése, hogy a kérést a Shoprenter küldte:
   A QueryString HMAC nélküli részének (`code=0907a61c0c8d55e99db179b68161bc00&shopname=example&timestamp=1337178173`) a **ClientSecret**-el sha256 algoritmussal elkódolva egyenértékűnek kell lennie a QueryString HMAC paraméterének értékével.
4. Ha a kiszolgáló fél rendben találta a kérést. Küld egy POST Request-et a Shoprenter felé a `https://[shopname].myshoprenter.hu/admin/oauth/access_credential` URL-re. 
   A POST Request-nek tartalmaznia kell az alábbi mezőket:
    - **client_id:** Az alkalmazás ClientId-ja
    - **client_secret:** Az alkalmazás ClientSecret értéke 
    - **code:** a Request-ben kapott code
    - **timestamp:** a Request-ben kapott timestamp
    - **hmac:** a Request-ben kapott HMAC
    
    Amennyiben valamelyik adat hiányos vagy téves, úgy az API hibaüzenetet fog küldeni a megfelelő hibakóddal JSON formátumban. 
    
    **Hibák**:
    - Ha elküldendő adatok közül valamelyik hiányzik, akkor `{"message":"Missing data in credential request","code":400}` választ fog adni.
    - Ha elküldendő client_id és secret_id eltér, akkor `{"message":"App client and request client data mismatch","code":401}` választ fog adni.
    - Ha a hitelesítési idő meghaladja a 30 másodpercet, akkor `{"message":"Authorization time expired","code":408}` választ fog adni.
    - Ha a telepítés közben hiba merült fel, akkor  `{"message":"App is not installed","code":409}` választ fog adni.
5. Amennyiben a Shoprenter megfelelőnek találja a POST Request-et egy `username`, `password` párossal fog válaszolni, amivel az alkalmazás hozzáfér az adott bolt API-jához. 
   A 2. lépésben indított Shoprenteres kérésben lévő timestamp arra szolgál, hogy megvizsgáljuk, a kliens alkalmazás **30 másodpercen belül** megkezdi-e a API hozzáférés kérését!
6. Ha az alkalmazás megkapta az authentikációs adatokat, át kell irányítania a `https://[primaryDomain]/admin/app/[appId]` URL-re.
   - A "primaryDomain" jelzi, hogy a boltoknak **egyedi domain neve** is lehet.
   - Tehát a bolt admin oldalának URL-je eltérhet a rendszer domain URL-től (pl. `https://shopname.shoprenter.hu/admin/`).
   - Szerencsénkre az authentikációs adatokhoz hozzá lett még fűzve az `app_url` (a QueryString-ben), ami az aktuális alkalmazás elérésének az URL-jét tartalmazza. 
   - Alternatív megoldás lehet még, hogy a "primaryDomain" értékét a [Domain Resource](https://doc.shoprenter.hu/api/domain.html#tulajdonsagok)-ból is le lehet kérdezni.
   - **Megjegyzés:** Van lehetőség egyedi QueryString paraméterekkel dekorálni az `app_url` értékét (az alkalmazás Shoprenteres URL-jét).
     Ezek a paraméterek az EntryPoint URL-ben is meg fognak jelenni, az authentikációhoz használt paraméterek (`shopname`, `code`, `timestamp`, `hmac`) mellett.

    Példa: 
    Legyen az EntryPoint: `https://app.example.com/entryPoint`
    Erre irányít át az alkalmazás: `https://[primaryDomain]/admin/app/[appId]?pelda=parameter`
    Ez esetben az EntryPoint íly módon hívódik meg: `https://app.example.com/entryPoint?shopname=[shopname]&code=[code]&timestamp=[timestamp]&hmac=[hmac]&pelda=parameter`
7. A Shoprenter egy Iframe-ben megnyitja az alkalmazáshoz tartozó EntryPoint-ot. A Request tartalmazni fogja a 2. pontban írt paramétereket.
8. Feltelepítés után a Shoprenter csak az Entrypoint-ra küld kéréseket. Minden esetben a 2. pontban írt paraméterekkel.

### Példa alkalmazások
- [SR Demo app PHP](https://github.com/Shoprenter/sr-demo-app-php)
- [SR Demo app PHP Slim](https://github.com/Shoprenter/sr-demo-app-php-slim)
- [SR Demo app Node.js](https://github.com/Shoprenter/sr-demo-app-node)
