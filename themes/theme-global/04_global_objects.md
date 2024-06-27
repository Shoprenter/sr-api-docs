# Objektumok

Az elérhető objektumok segítségével könnyedén felépítheted és testreszabhatod a témákat a rendszerben. Az objektumok metódusokkal és/vagy tulajdonságokkal rendelkeznek, amelyek lehetővé teszik a beállítások kezelését, pénznemek kezelését, képek kezelését, általános rendszerinformációk lekérdezését és különféle útvonalak elérését. Az alábbiakban részletes leírást találsz az egyes objektumokról és azok használatáról.

Globálisan minden template fájlban elérhetőek ezek az objektumok.

## config

### Leírás

Az admin felületen található beállítások objektuma.

### get() metódusa

#### Szintaxis

```
config.get(configName)
```

#### Argumentum

**configName**: String amely a lekérni kívánt konfigurációs beállítás nevét jelenti.

#### Visszatérési érték

Visszatérhet több típussal is, lehet String, Boolean vagy Integer is. Amennyiben nem létezik NULL.


#### Példakód:

<table>
<tr>
    <td>Kód:</td>
    <td>Kimenet:</td>
</tr>
<tr>
<td>

```twig
{% if config.get('config_show_header_phone') == 1 %}
    <div class="header-phone">{{ phone }}</div>
{% endif %}
```

</td>
<td>

```html
<div class="header-phone">06-30-123-4567</div>
```

</td>
</tr>
</table>

---
## currency
### Leírás
Az objektum információkat tartalmaz a webáruházban beállított pénznemekről.
### Tulajdonságok

<table>
<tr>
    <th>Tulajdonság</th>
    <th>Leírás</th>
    <th>Típus</th>
</tr>
<tr>
    <td>currencyId</td>
    <td>aktuális pénznem id, pl. 4</td>
    <td>String</td>
</tr>
<tr>
    <td>currencyCode</td>
    <td>aktuális pénznem code, pl. HUF</td>
    <td>String</td>
</tr>
<tr>
    <td>currencyTitle</td>
    <td>aktuális pénznem title, pl. Hungarian Forint</td>
    <td>String</td>
</tr>
</table>

### Használat
A `Currency` objektum lekérhető a [shop](#shop) objektumból a currentCurrency és az availableCurrencies tulajdonságokon keresztül


### Példakód
Az aktív pénznemek 1. elemének a title-je, ebben a példában a HUF:

<table>
<tr>
    <td>Kód:</td>
    <td>Kimenet:</td>
</tr>
<tr>
<td>

```
{{ shop.availableCurrencies[0].currencyTitle }}
```

</td>
<td>

```
HUF
```

</td>
</tr>
</table>

---

## image

Az `Image` objektumot a képek kezelésére használjuk, melynek jelenleg csak egy `src` tulajdonsága van, amely a kép forrását (URL-jét) tárolja. Az `src` tulajdonság típusa sztring. Csak abban a TPL-ben elérhető, ahol átadásra került.

### Példakód:

A news.tpl-ben a content változón belül elérhető egy image objektum.

<table>
<tr>
    <td>Kód:</td>
    <td>Kimenet:</td>
</tr>
<tr>
<td>

```twig
{{ content.image_data.src }}
```

</td>
<td>

```
data/test.png
```

</td>
</tr>
</table>

---

## page

A `page` objektum egy globális objektum, amely a rendszer általános információinak lekérdezésére szolgál.

### metódusok
<table>
<tr>
    <th>név</th>
    <th>Leírás</th>
    <th>Típus</th>
</tr>
<tr>
    <td>getRoute()</td>
    <td>visszaadja az aktuális kérés útvonalát, ha nem érhető el üres karakterláncot kapunk</td>
    <td>String</td>
</tr>
<tr>
    <td>getUrl()</td>
    <td>visszaadja az aktuális kérés teljes URL-jét</td>
    <td>String</td>
</tr>
</table>

### Példakód ha termékoldalon vagyunk

<table>
<tr>
    <td>Kód:</td>
    <td>Kimenet:</td>
</tr>
<tr>
<td>

```twig
{{ page.getRoute() }}
```

</td>
<td>

```
product/product
```

</td>
</tr>
</table>

---

## routes

A routes objektum egy olyan asszociatív tömb, amelyben a kulcsok a route nevei, az értékek pedig az adott route-hoz tartozó URL-ek. Ez mindig sztring típusú.

### Példakód

<table>
<tr>
    <td>Kód:</td>
    <td>Kimenet:</td>
</tr>
<tr>
<td>

```twig
{{ routes.login_url }}
```

</td>
<td>

```
/customer/login
```

</td>
</tr>
</table>

### Teljes lista
<table>
<tr>
    <td>Kulcs:</td>
    <td>érték:</td>
</tr>
<tr><td>account_url</td><td>/index.php?route=account/account</td></tr>
<tr><td>account_edit_url</td><td>/index.php?route=account/edit</td></tr>
<tr><td>account_insert_url</td><td>/index.php?route=account/address/insert</td></tr>
<tr><td>account_password_url</td><td>/index.php?route=account/password</td></tr>
<tr><td>account_address_url</td><td>/index.php?route=account/address</td></tr>
<tr><td>account_waitinglist_url</td><td>/index.php?route=account/waitinglist</td></tr>
<tr><td>account_history_url</td><td>/index.php?route=account/history</td></tr>
<tr><td>account_invoice_url</td><td>/index.php?route=account/invoice</td></tr>
<tr><td>account_download_url</td><td>/index.php?route=account/download</td></tr>
<tr><td>account_newsletter_url</td><td>/index.php?route=account/newsletter</td></tr>
<tr><td>account_registration_contribution_url</td><td>/index.php?route=account/registration_contribution</td></tr>
<tr><td>account_affiliate_url</td><td>/index.php?route=account/aaffiliate</td></tr>
<tr><td>account_affiliate_commissions_all_url</td><td>/index.php?route=account/aaffiliate_commissions/all</td></tr>
<tr><td>account_affiliate_commissions_month_url</td><td>/index.php?route=account/aaffiliate_commissions/month</td></tr>
<tr><td>cart_url</td><td>/cart</td></tr>
<tr><td>cartpresent_url</td><td>/index.php?route=checkout/cartchildren/cartpresent</td></tr>
<tr><td>checkout_url</td><td>/checkout</td></tr>
<tr><td>contact_url</td><td>/index.php?route=information/contact</td></tr>
<tr><td>forgotten_url</td><td>/index.php?route=account/forgotten</td></tr>
<tr><td>login_url</td><td>/customer/login</td></tr>
<tr><td>logout_url</td><td>/index.php?route=account/logout</td></tr>
<tr><td>personaldata_url</td><td>/index.php?route=information/personaldata</td></tr>
<tr><td>register_url</td><td>/customer/register</td></tr>
<tr><td>manufacturer_list_url</td><td>/index.php?route=product/manufacturers</td></tr>
<tr><td>search_url</td><td>/index.php?route=product/list</td></tr>
<tr><td>sitemap_url</td><td>/index.php?route=information/sitemap</td></tr>
<tr><td>style_guide_url</td><td>/index.php?route=information/style_guide</td></tr>
<tr><td>wishlist_url</td><td>/index.php?route=wishlist/wishlist</td></tr>
<tr><td>checkout_cart_url</td><td>index.php?route=checkout/cart</td></tr>
</table>

:red_circle: Kerüljük el, hogy a rendszer útvonalát közvetlenül beírjuk a sablonba. **Helyette használjuk a routes objektumot.**

---

## settings
Ezt az objektumot használjuk a témához beállított színek kezelésére. A színek a config.data.json fájlban vannak definiálva.


### get() metódusa

#### Használat

```twig
{{ settings.get('key', 'default_value') }}
```

Ez a kód a `key` nevű beállítás értékét adja vissza, ha létezik. Ha a `key` nevű beállítás nem létezik, akkor az `default_value` értéket adja vissza. Sztring típussal tér vissza.

#### Példakód

A config.data.json fájlban beállított "global-color" szín kikérése

<table>
<tr>
    <td>Kód:</td>
    <td>Kimenet:</td>
</tr>
<tr>
<td>

```twig
{{ settings.get('global-color', '#000') }}
```

</td>
<td>

```
#364270
```

</td>
</tr>
</table>

---

## shop

A shop objektum segítségével a webáruházhoz tartozó általános információk kérhetők ki.


### Tulajdonságok

<table>
<tr>
    <th>Tulajdonság neve</th>
    <th>Leírás</th>
    <th>Típus</th>
</tr>
<tr>
    <td>name</td>
    <td>a shop nevét adja vissza</td>
    <td>Sztring</td>
</tr>
<tr>
    <td>title</td>
    <td>a shop címét adja vissza</td>
    <td>Sztring</td>
</tr>
<tr>
    <td>needCountdown</td>
    <td>egy logikai értéket ad vissza, amely azt jelzi, hogy az adott oldalon van-e akció visszaszámláló </td>
    <td>Boolean</td>
</tr>
<tr>
    <td>currency</td>
    <td>a shop aktuális pénznemét adja vissza, tulajdonságai a <a href="#currency">currency objektumnál</a> megtalálahtóak </td>
    <td>Currency</td>
</tr>
<tr>
    <td>availableCurrencies</td>
    <td>a shopban elérhető pénznemek listáját adja vissza</td>
    <td>Array</td>
</tr>
</table>

### Példakód

A shop nevét írjuk ki

<table>
<tr>
    <td>Kód:</td>
    <td>Kimenet:</td>
</tr>
<tr>
<td>

```twig
{{ shop.name }}
```

</td>
<td>

```
Demo
```

</td>
</tr>
</table>

---

## viewHelper

### viewHelper.loadModule()

Az engedélyezett modulok vagy dinamikus modulok beillesztésére szolgál. Ha egy modul hozzá van rendelve egy pozícióhoz
és a viewHelper.loadModule segítségével is behúzzuk, akkor megjelenik a pozícióban és ott is ahol a loadModule-t használtuk.

#### Szintaxis

```
viewHelper.loadModule(moduleRoute)
```

#### Argumentumok

**moduleRoute**: A modul elérés, ahogy az admin felületen is hivatkozunk rá.

#### Visszatérési érték

A loadModule a hivatkozott modul html kódjával tér vissza.

<table>
<tr>
    <td>Kód:</td>
    <td>Kimenet:</td>
</tr>
<tr>
<td>

```twig
{{ viewHelper.loadModule('module/headerlinks') }}
```

</td>
<td>

```html
<ul class="list-unstyled headermenu-list d-flex">
    <li class="headermenu-list__item d-flex nav-item">
        <a href="[BOLTNEV]/test" target="_self" class="nav-link" title="Test">
            test
        </a>
    </li>
</ul>
```

</td>
</tr>
<tr>
<td>

```twig
{{ viewHelper.loadModule('sections/section-name') }}
```

</td>
<td>

```html

<div id="section-section-name" class="section-wrapper module-editable">
    ...
</div>
```

</td>
</tr>
</table>

### viewHelper.loadPosition()

Az adott pozícióban megjelenő összes modult jeleníti meg, amik engedélyezett állapotra vannak állítva. A pozíciók
amik a témában definiálva vannak a **config/settings.json** fájlban találhatóak.

#### Szintaxis

```
viewHelper.loadPosition(positionName)
```

#### Argumentumok

**positionName**: A pozíció nevét kell megadni.

#### Visszatérési érték

Minden modul htmljét visszaadja ami az adott pozícióban megjelenhet.

Példa:

<table>
<tr>
    <td>Kód:</td>
    <td>Kimenet:</td>
</tr>
<tr>
<td>

```twig
{{ viewHelper.loadPosition('home') }}
```

</td>
<td>

```html
<div id="section-section-name" class="section-wrapper module-editable">...</div>
<div id="module_news_wrapper" class="module-news-wrapper">...</div>
<div id="module_latest_wrapper" class="module-latest-wrapper">...</div>
<div id="module_kickerimage_wrapper" class="module-kickerimage-wrapper">...</div>
```

</td>
</tr>
</table>

### viewHelper.isPositionEmpty()

Azt vizsgálja, hogy egy adott pozícióhoz van-e modul hozzárendelve.

#### Szintaxis

```
viewHelper.loadPosition(positionName)
```

#### Argumentumok

**positionName**: A pozíció nevét kell megadni.

#### Visszatérési érték

Boolean értékkel tér vissza: true vagy false.

Példa:

<table>
<tr>
    <td>Kód:</td>
    <td>Kimenet:</td>
</tr>
<tr>
<td>

```twig
{% if viewHelper.isPositionEmpty('home') %}
    {{ viewHelper.loadPosition('home') }}
{% endif %}
```

</td>
<td>

```html
<div id="section-section-name" class="section-wrapper module-editable">...</div>
<div id="module_news_wrapper" class="module-news-wrapper">...</div>
<div id="module_latest_wrapper" class="module-latest-wrapper">...</div>
<div id="module_kickerimage_wrapper" class="module-kickerimage-wrapper">...</div>
```

</td>
</tr>
</table>
