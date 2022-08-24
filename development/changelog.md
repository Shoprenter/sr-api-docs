# API changelog

#### 2022.08.25
Elérhetővé vált 4 új [Frontend API Event](frontend-api/01_shoprenterjs_api.md).\
Az új események segítségével sikertelen fizetésre és vásárlói profil tevékenységekre íratkozhatunk fel.
- [onCheckoutOrderPaidUnsuccessful](frontend-api/01_shoprenterjs_api.md#oncheckoutorderpaidunsuccessful)
- [onCustomerRegistered](frontend-api/01_shoprenterjs_api.md#oncustomerregistered)
- [onCustomerLoggedIn](frontend-api/01_shoprenterjs_api.md#oncustomerloggedin)
- [onCustomerUpdated](frontend-api/01_shoprenterjs_api.md#oncustomerupdated)

#### 2022.08.24
Elérhetővé vált 8 új [Frontend API Event](frontend-api/01_shoprenterjs_api.md).
Az új események segítségével látogatói és vásárlói tevékenységekre íratkozhatunk fel.

#### 2022.05.09
Elérhetővé vált egy új feature a Payment API-hoz, [Bankkártya csere](../paymentapi/docs/j_funding_source_change.md).
Segítségével az Ismétlődő díjfizetéseinkhez tartozó bankkártyákat cseréltethetjük ki a felhasználóinkkal.

#### 2022.03.23.
Az [Order](../api/order.md) resource-unk ‘DELETE’ metódusát megszüntettük.

#### 2022.03.09.
Az [Order](../api/order.md) resource-unk ‘DELETE’ metódusát megszüntetjük 2022. március 23-ával. A dokumentációból a mai nappal kikerül az erre vonatkozó leírás de természetesen az említett dátumig még elérhető és használható gond nélkül a metódus.

#### 2022.02.15.
A [Weight](../api/weight_class.md) és [Length](../api/length_class.md) Class Resource-ok mellé bekerültek a Description-jeik.
- [Weight Class Description](../api/weight_class_description.md)
- [Length Class Description](../api/length_class_description.md)

A szöveges tartalmak immáron API-n kresztül is elérhetőek: 
- [CMS Content Extend Resource](../api/cms_content_extend.md)
- [CMS Content Description Resource](../api/cms_content_description.md)

Az Webhook API kibővült a Mennyiségi árkedvezmény mezővel. [Webhook Resource](../api/webhook.md)

#### 2022.01.10.
A [WebHook Resource](../api/webhook.md) kapott két új elküldhető mezőt:
- order_expectedDeliveryDate (Rendelés Állapotváltás)
- order_newsletterChecked  (Új rendelés feladás

#### 2021.12.20.
Egy új korlátozást vezettünk be a terméktulajdonságokra: Összesen maximum 300 db egyed hozható létre
a [List Attribute](../api/list_attribute.md), [Text Attribute](../api/text_attribute.md) és a [Number Attribute](../api/number_attribute.md) Resource használatával. 

#### 2021.11.09
A [Settings Resource](../api/setting.md) két, a matricákra vonatkozó beállítással bővült: config_badge_max és config_badge_orientation

#### 2021.10.11
A Payment API [Egyszeri](../paymentapi/docs/g_one_time_charge.md) és [Ismételődő díjfizetései](../paymentapi/docs/i_recurring_charge.md) immáron lekérdezhetőek GET kéréssel.

#### 2021.08.17

A Shoprenter Payment API dokumentáció elérhetővé tettük az oldalon. [SR Payment API](../paymentapi/docs/a_introduce.md)

#### 2021.08.10

- Hamarosan meg fog szünni a ***.api.shoprenter.hu** rendszer domain, helyette a ***.api.myshoprenter.hu** domain-en lesznek elérhetőek az API Resource-ok. Így érdemes lesz mielőbb váltani és frissíteni az integrációkat.
- A [Order Resource](../api/order.md) és a [Order Extend Resource](../api/order_extend.md) dokumentációjában feltüntettük **shippingMethodExtension** és **paymentMethodCode** lehetséges értékeit, táblázatba foglalva.
- Az [Order Resource](../api/order.md),  [Order Extend Resource](../api/order_extend.md), [Product  Resource](../api/product.md) és [Product Extend Resource](../api/product_extend.md) egyes tulajdonságainak leírását pontosítottuk.
- Pontosítottuk a API limitre vonatkozó megszorításokat

#### 2021.07.07
Immáron a [Webhook Resource](../api/webhook.md) -ban, a webHookParameters **fields** property-jével szabályozni tudjuk, hogy a Shoprenter milyen mezőket küldjön el az általunk megadott url-re.

#### 2021.05.06.
A Product és Product Extend Resource POST és PUT kéréseinél immáron frissül a árszorzó, a "sávos árszorzók" funkció beállításai szerint.

#### 2021.03.10
Az [Order Product Resource](../api/order_product.md) -ba bekerült az productInnerId mező.
Ez a megrendelt termék belső azonosítója, így nincs szükség a product resource linket meghívni, ha csak erre vagyunk
kíváncsiak

#### 2021.02.23
Az [Order Product Resource](../api/order_product.md) -ba bekerült az innerId mező.
Természetesen, ez a rendelés és a termék közötti kapcsolatot leíró egyedek belső azonosítója,
nem a terméké!

#### 2021.02.16.
Az [**Order**](../api/order.md) és az [**Order Extend**](../api/order_extend.md) Resource egy új tulajdonsággal bővült:
**shippingMethodLocalizedName**
Ez a rendelés nyelvén tartalmazza a szállítási mód **aktuális** nevét.


#### 2021.02.11.
- A **Customer/Customer Extend** és az **Order/OrderExtend Resource**-ok dátum szűrői kiegészültek.
A kollekció lekérés dátum szerinti szűkítése sokkal testreszabhatóbbá vált.
- Bekerült egy új API végpont: [**Tax Class Extend Resource**](../api/tax_class_extend.md)
Így az áfakulcsokat nem kell linken keresztül lekérni.

#### 2021.02.09.
- A [**Order Product Resource**](../api/order_product.md) kiegészült egy **parentProduct** tulajdonsággal. 
  Tipikusan olyan feladatok ihlették, amikor rendelés feldolgozásnál tudnunk kell, hogya rendelt terméknek 
  van-e szülőterméke. Csak olvasható!
- A [**Order Extend Resource**](../api/order_extend.md) kiegészült egy **coupon** tulajdonsággal. A használt kupon összes adatát
  tartalmazza. Csak olvasható!
- A [**Order Extend Resource**](../api/order_product.md) -ban a **paymentCountry**, a **shippingCountry**, 
  a **language** és a **currency** tulajdonságot kinyítottuk.  Csak olvashatóak!

#### 2021.01.27.
- A Product és Product Extend Resource POST és PUT kéréseinél immáron frissül a árszorzó, a "sávos árszorzók" funkció beállításai szerint.

#### 2021.01.19.
- A [**Kezdeti lépések**](./app-development/01_getting_started.md) dokumentum javítva lett, és ki lett egészítve az "app_url" leírással.
- Setting resource kiegészült az áruház időzónájával (**config_timezone**). [dokumentáció](../api/setting.md)

#### 2020.11.24.
- Az API példák kiegészültek egy [**Rendelés felvétele**](./api-examples/09_create_order.md) példával.

#### 2020.10.30.
- Az API példák kiegészültek egy [**"Új rendelés feladás" webhook működése**](./api-examples/06_webhook.md) példával.
- Az API példák kiegészültek egy [**termékopció kezelése**](./api-examples/07_product_option.md) példával.
- Az API példák kiegészültek egy [**Termék típusok, egyedi tulajdonságok és termékváltozatok kezelése**](./api-examples/08_product_attribute_handling.md) példával.

#### 2020.10.29.
- Az [**API Batch feldolgozó**](api/04_batch.md) menüpont kiegészült további példákkal: [**Tömeges termékfeltöltés**](api/04_batch.md#tomeges-termekfeltoltes), [**Termék hozzáadása kategóriához Outer ID segítségével**](api/04_batch.md#termek-hozzaadasa-kategoriahoz-outer-id-segitsegevel)
- Az [**Outer ID használata**](api/05_outer_id.md) kiegészült egy bejegyzéssel, amelyben leírja milyen esetekben helytelen az Outer ID-t használni.

#### 2020.10.27.
- Az API menüpont kiegészült a [**Postman használatát példakódokkal bemutató bejegyzéssel**](api/08_postman.md)

#### 2020.10.26.
- Az API példák kiegészültek egy [**termékkép hozzáadása termékhez**](./api-examples/05_attach_uploaded_image_to_product.md) példával.
- Az API példák kiegészültek egy [**akciós termék**](./api-examples/01_0_product_special.md) példával.

#### 2020.10.22.
- Az API példák kiegészültek egy [**termék hozzáadása kategóriához**](./api-examples/04_attach_product_to_category.md) példával.

#### 2020.10.13.
- Az oldalkeresője módosult, amelyen belül most már nem csak az oldal nevére, hanem a benne lévő tartalmakra is rá lehet keresni.

#### 2020.07.21.
- A Product Extend Resource "productPrices" értéke megváltozott. Leírás a működésről [link](./api-examples/03_price_calculation.md)

#### 2020.05.18.
- A Shipping Mode Extend Resource-on keresztül elérhetőek lettek  integrált szállítási módok is. Fontos: csak, a Shoprenter adminon szerkesztett, szállítási módok érhetőek el és a WSESHIP (egyedi, felhasználók által létrehozott) típusúak módosíthatóak API-on keresztül.

#### 2020.05.14.
- Az Information Extend Resource-ba bekerült az UrlAliases property, illetve szabályozhatóvá vált a láthatósága a resouce-al felvett Szöveges menüpontoknak:

https://doc.shoprenter.hu/api/information_extend.html

Természetesen bővült az URL Alias Resource is. Ezentúl INFORMATION típusú alias is kezelhető:

https://doc.shoprenter.hu/api/url_alias.html

#### 2020.04.15.
- A példa alkalmazások menüpont kiegészült egy bővebb Slim keretrendszerre épülő demo alkalmazással.

#### 2020.04.07.
- Product Description Resource kiegészült a metaTitle propertyvel.

#### 2020.01.22.
- Pótolva lett a CustomerGroup Resource és a Product Extend Resource ProductPrice adataiban a Customer Group InnerId-t.

#### 2019.11.21.
- [WebHook automatizmus](api/07_webhook.md) dokumentációja hozzáadva.

#### 2019.11.20.
- A Product Extend Resource GET endpoint hívása kiegészült egy **productPrices** tömbbel, amellyel a termékek árait kaphatjuk meg vevőcsoportokra szétbontva. [dokumentáció](../api/product_extend.md)

- Ha a Customer Resource-t használva új vevőt szeretnénk létrehozni, és nem adunk meg **customerGroup**-t, akkor a vevő az alapértelmezett vevőcsoportba fog kerülni.

#### 2019.10.24.
- Elérhető vált a **Payment Mode Resource** API végpont, amellyel kikérhetjük az aktuális bolt **telepített** fizetési módjait. Mivel a rendszer nem támogatja a saját fizetési módok létrehozását, így ez a resource teljesen readOnly. [dokumentáció](../api/payment_mode.md)

#### 2019.10.21.
- A **ProductExtend** resource-ba bekerült egy új property, a "**productAttributeExtend**" nevű lista, ami tartalmazza a termékhez tartozó tulajdonságokat. Fontos megjegyezni, hogy ez jelenleg csak readonly, tehát nem lehet küldeni rá POST adatokat. [dokumentáció](../api/product_extend.md)

#### 2019.10.17.
- Setting resource kiegészült a bolt üzemeltetőjének címével (**config_address**) és telefonszámával (**config_telephone**). [dokumentáció](../api/setting.md)

#### 2019.10.14
- Elérhetővé vált a szöveges tartalmak menedzseléséhez szükséges API végpont Information Extend néven. [dokumentáció](../api/information_extend.md)

#### 2019.09.23
- Sok problémát okozott ügyfeleinknek az egyes fő resoruce-ok (Product, Order, Category stb.) törlése esetén, hogy bár a rájuk küldött DELETE kérések esetén, a hozzájuk tartozó OuterID megfelelelően törlődött. Viszont, ha volt kapcsolódó resource-a, pl. egy termék esetén a termék leírások, így ehhez is tartozott külön OuterID, ez sajnos nem törlődött automatikusan. Ezt oldottuk meg, így most már nem kell tartani attól, hogy később név ütközésbe futnak bele a fejlesztők, OuterID felvételekor.

#### 2019.09.10
- Bekerült a Shipping Mode Extend resource, amellyel a szállítási módokkal kapcsolatos műveleteket lehet végrehajtani. [dokumentáció](../api/shipping_mode_extend.md)
- Bekerült a Shipping Mode Description resource, amellyel a szállítási módokkal kapcsolatos adatokat (név, leírás, nyelv) lehet kezelni. [dokumentáció](../api/shipping_mode_description.md)
- Bekerült a Shipping Lane resource, amellyel a szállítási módokkal kapcsolatos szállítási sávokat lehet kezelni. [dokumentáció](../api/shipping_lane.md)
- Order resource kiegészült egy shippingMode kereső paraméterrel és egy shippingMode propertyvel. [dokumentáció](../api/order.md)
- Order Extend resource kiegészült egy shippingMode kereső paraméterrel és egy shippingMode propertyvel. [dokumentáció](../api/order_extend.md)

#### 2019.09.03
- Bekerült a GeoZone resource, amellyel le lehet kérdezni, hogy milyen földrajzi zónához milyen országok tartoznak. [dokumentáció](../api/geo_zone.md)
- A Country resource kiegészült a geoZones propertyvel, amellyel megkaphatjuk, hogy egy adott ország milyen földrajzi zónákhoz tartozik. [dokumentáció](../api/country.md)
- Az OrderProduct resource kiegészült további propertykkel, amellyel megkaphatjuk a rendelt termék szélességét (**width**), magasságát (**height**), hosszát (**length**) és súlyát (**weight**). [dokumentáció](../api/order_product.md)
- A ProductImage resource kiegészült egy sortOrder propertyvel, amellyel meg lehet adni a termékképek sorrendjét. [dokumentáció](../api/product_image.md)
- Elérhetővé vált a Domain Resource. Ezzel kikérhető az adott bolthoz felvett domainek adatai: a domain-ek nyelve és hogy elsődleges domain-ek vagy sem. [dokumentáció](../api/domain.md)

#### 2019.08.08
- Bekerült a **Json-alapú** kommunikáció az API-val. Emellett az API dokumentáció ki lett bővítve **Json** formátumú példákkal.

#### 2019.08.06
- A Product és Product Extend resource-ban elérhető lett az **allImages** property, mely az adott terméhez tartozó fő termékkép (mainImage) és a hozzá tartozó további képek (image1, image2,...) **teljes** url elérését tartalmazza, cache-elt formában.

#### 2019.07.05.
- Customer és Customer Extend resource-khoz elkészült egy **updatedAtMin** filter, ami a megadott dátum után módosított 
vásárlókat adja vissza. [dokumentáció](../api/customer_extend.md)

#### 2019.06.23. 
- **Product Extend** resource-ba belekerült a **manufacturer** kibontva, hogy ne kelljen újabb lekérés hozzá 
[dokumentáció](../api/product_extend.md)    

#### 2019.06.21.
- **API batch feldolgozó**nál memória optimalizálás történt, hogy egyszerre több request-et is tudjon kezelni. 
[dokumentáció](./api/04_batch.md)

#### 2019.05.30.
- Order resource-ba bekerült az **originalPrice** mező [dokumentáció](../api/order.md)

#### 2019.05.03.
- Product és ProductExtend resource-ba bekerült a **cost** mező [dokumentáció](../api/product.md)

#### 2019.04.29.
- A **full** paraméter segítségével a lista lekéréseknél már egy requestben elérjük a lista elemek tartalmát, 
análkül hogy újabb kéréseket kellene indítani. Ez minden resource esetén elérhető. 
[dokumentáció](./api/03_full_parameter.md)

#### 2019.02.01.
- **Address resource**-ba bekerült a telephone mező [dokumentáció](../api/address.md)

#### 2018.12.05.
- **CategoryExtend resource** elkészítése [dokumentáció](../api/category_extend.md)
- **CustomerExtend resource** elkészítése [dokumentáció](../api/customer_extend.md)  
- [Mire használhatóak a kiterjesztett Resourceok?](./api/06_extend_resource.md)

#### 2018.09.25.
- **Webhook resource** elkészítése, aminek segítségével webhook-ot lehet létrehozni
 [dokumentáció](../api/webhook.md)

#### 2018.09.13.
- **ScriptTag resource** elkészítése, aminek segítségével a frontendre lehet API-n keresztül script-et elhelyezni
 [dokumentáció](../api/script_tag.md)

#### 2017.10.20.
- **ProductExtend resource** elkészítése [dokumentáció](../api/product_extend.md)
- **OrderExtend resource** elkészítése [dokumentáció](../api/order_extend.md)
- [Mire használhatóak a kiterjesztett Resourceok?](./api/06_extend_resource.md)

#### 2017.07.27. 
- **Többnyelvűség** lekezelése a **Document Description** resource-nál
 [dokumentáció](../api/document_description.md)

#### 2017.06.30. 
- Beszédes **hibaüzenetek** visszaadása [dokumentáció](./api/02_status_codes.md)
