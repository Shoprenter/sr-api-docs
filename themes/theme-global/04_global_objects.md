# Objektumok

Hamarosan

## config.get()

Az admin felületen található beállítások kikérésére szolgáló függvény.

### Szintaxis

```
config.get(configName)
```

### Argumentumok

**configName**: A beállítás neve

### Visszatérési érték

Visszatérhet több típussal is, lehet String, Boolean vagy Integer is.


Példa:

```twig
{% if config.get('config_show_header_phone') == 1 %}
    <div class="header-phone">{{ phone }}</div>
{% endif %}
```

Kimenet:

```html
<div class="header-phone">06-30-123-4567</div>
```


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
<tr>
    <td>availableCurrencies</td>
    <td>tömb, amely az aktív pénznemeket tartalmazza</td>
    <td>Array</td>
</tr>
</table>

### Példakód
Az aktív pénznemek 1. elemének a title-je:
``` 
{{ shop.availableCurrencies[0].getCurrencyTitle }}
```
---

## image

Hamarosan

---

## page

Hamarosan

---

## routes

Hamarosan

---

## settings
A témához beállított színeket tartalmazza. A színek a config.data.json fájlban vannak definiálva.

### Példakód
A config.data.json fájlban beállított "global-color" színt adja vissza. Ha nem található meg a "global-color", akkor a fallback: #000
``` 
{{ settings.get('global-color', '#000') }}
```

---

## shop

Hamarosan

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

Példa 1:

```twig
{{ viewHelper.loadModule('module/logo') }}
```

Kimenet 1:

```html

<div id="logo" class="module content-module header-position logo-module logo-text hide-top">
    <a href="/">Tokyo</a>
</div>
```

Példa 2:

```twig
{{ viewHelper.loadModule('sections/section-name') }}
```

Kimenet 2:

```html
<div id="section-section-name" class="section-wrapper module-editable">
  ...
</div>
```


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

```twig
{{ viewHelper.loadPosition('home') }}
```

Kimenet:

```html
<div id="section-section-name" class="section-wrapper module-editable">...</div>
<div id="module_news_wrapper" class="module-news-wrapper">...</div>
<div id="module_latest_wrapper" class="module-latest-wrapper">...</div>
<div id="module_kickerimage_wrapper" class="module-kickerimage-wrapper">...</div>
```


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

```twig
{% if viewHelper.isPositionEmpty('home') %}
    {{ viewHelper.loadPosition('home') }}
{% endif %}
```

Kimenet:

```html
<div id="section-section-name" class="section-wrapper module-editable">...</div>
<div id="module_news_wrapper" class="module-news-wrapper">...</div>
<div id="module_latest_wrapper" class="module-latest-wrapper">...</div>
<div id="module_kickerimage_wrapper" class="module-kickerimage-wrapper">...</div>
```


