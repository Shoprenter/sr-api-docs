# Postman használata és példakódok

## API használatához példák

- PHP testeléshez használható API klienst [ide kattintva](https://github.com/Shoprenter/api-client) érheti el.
- Shoprenter API példa kollekciók. (Használatáról bővebben a cikkben) [Letöltés](https://www.shoprenter.hu/api/postman/ShoprenterAPI.postman_collection.json)
- [További példák](../api-examples/01_0_product_special.md)

## Postman használata

A Postman egy komplett eszköztár API fejlesztők részére, a programmal gyorsan és hatékonyan lehet dolgozni az API-val, mivel támogatja a fejlesztők minden munkafolyamatát. A szoftver az alábbi platformokon érhető el: Mac OS X, Windows, Linux valamint Chrome.

### Telepítés

A [Postman oldalán](https://www.postman.com/downloads/) válasszuk ki milyen rendszert használunk, majd kattintsunk a letöltés gombra.

![postman client download](./images/postman_client_download.png)

#### macOS telepítés

Amint sikerült a letöltés a file-t húzzuk be a “Applications” mappába. Dupla kattintással meg tudjuk nyitni az applikációt.

#### Windows telepítés

- Töltsük le a setup file-t.
- Futtassuk a telepítőt

#### Linux telepítés

A Linuxon történő telepítés eltérő lehet. A következő útmutatóban bővebb információ található erről: [Postman app on Ubuntu 16.04.](https://www.bluematador.com/blog/postman-how-to-install-on-ubuntu-1604?utm_source=hootsuite&utm_medium=twitter&utm_campaign=)

#### Böngésző bővítmény telepítés

Chrome böngésző esetén lehetőség van bővítményként hozzáadni a böngészőhöz a [Postman-t.](https://chrome.google.com/webstore/search/Postman?hl=hu)

### Használat

A Postman indítása után nincs más dolgunk mint elküldeni 
[az első kérést](https://learning.postman.com/docs/getting-started/sending-the-first-request/)
vagy létrehozni a [saját kollekciónkat](https://learning.postman.com/docs/getting-started/creating-the-first-collection/).
Amennyiben további információ szükséges az induláshoz, az 
[itt lévő dokumentációban](https://learning.postman.com/docs/getting-started/introduction/) ezekre rá tudunk keresni.


#### Example kollekció importálása

Shoprenter részről előre elkészítettünk egy kollekciót amit be lehet importálni és használni. A kérdéses JSON file ezen az URL-en érhető el: https://www.shoprenter.hu/api/postman/ShoprenterAPI.postman_collection.json

A Postman-en belül a bal felső sarokban találunk egy import gombot, ezzel be tudjuk importálni URL-ből vagy akár file-ból is a fenti példát:

![postman_collection_import](./images/postman_collection_import.png)

Az import után a bal oldalon láthatjuk is, hogy kaptunk 5db POST példát.

![postman_post](./images/postman_post.png)

Ezen az oldalon szükségünk lesz a Shoprenteres API belépési adatokra, ezeket a bolt admin felületén,
a **Beállítások > Integrációk > API beállítások** menüben fogjuk megtalálni.<br/>Az új admin felület esetén ugyanezt pedig a **Beállítások > API beállítások** menüben fogjuk megtalálni.

A következő képen egy sikeres POST-ot láthatunk, amivel egy új terméket jött létre a bolton belül. Sikeres GET kérés esetén a standard 200-as válaszkódok kapjuk, jelen esetben POST-olás történt, ezért 201-es válaszüzenetet kaptunk. Ha a státusz fülé visszük az egeret, akkor bővebb információt kaphatunk a kapott válaszkódról.
[További API státuszkódok a Shoprenterben.](https://doc.shoprenter.hu/development/api/02_status_codes.html)

![postman_success_post](./images/postman_success_post.png)

A kollekcióban lévő [**Batch szerkezetet**](./04_batch.md)
mindenképpen ajánljuk tanulmányozásra, ezzel ugyanis szignifikánsan tudjuk csökkenteni az elküldött kérések számát, így az API kapcsolat is sokkal optimálisabb lehet.
 
#### Válasz átváltása JSON formátumra

A fenti példánál maradva lehetőség van JSON formátumban is megkapni a választ. Ehhez a headers fülön szükséges aktiválni a application/json key-t.

![postman_json_response](./images/postman_json_response.png) 

### Kódgenerálás több nyelvre

A Postman az API hívások számos programnyelven (pl: PHP, Go, Java, Python stb.) történő implementálásában is könnyed segítséget nyújt 
ún. kódgenerálással (lásd bővebben [**link**](https://learning.postman.com/docs/sending-requests/generate-code-snippets/)). 

A Postman-ben elkészített requestből a felület bal oldalán található **Code** gomb segítségével generálhatunk kódot,
ahol is a felugró ablakon belül kiválaszthatjuk, hogy mely nyelven szeretnénk a requestet végrehajtani. 


![postman_code_generate](./images/postman_code_generate.png)

![postman_code_generate](./images/postman_code_generate_php.png)

