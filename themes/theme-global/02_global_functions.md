# Függvények

A téma fájlokhoz a [TWIG](https://twig.sensiolabs.org) template motort használja a ShopRenter. Így minden tpl
kiterjesztésű fájl TWIG szintaxisra épül. A TWIG dokumentációban látható alap függvények és filterek mellett vannak a
ShopRenter által biztosított függvények és filterek is. Ezek azért készültek, hogy a frontend fejlesztést megkönnyítsék.

## add_body_class()

Az `add_body_class` használatával tudunk a `<body>` tag-hez class-t hozzáadni. String típusú paramétert vár.

### Szintaxis

```
{{ add_body_class(className) }}
```

Példa:

```twig
{{ add_body_class("new-class") }}
```

Kimenet:

```
<body class="page-body new-class">
```

## asset()

Az `asset` függvény az elérési útvonalat kiegészíti a cdn-es domain névvel és verziót is kap.

### Szintaxis

```
asset(filePath)
```

### Argumentumok

**filePath**: A fájl útvonala a gyökér könyvtártól.

### Visszatérési érték

A teljes url -el tér vissza, string típusként.

Példa:

```twig
<script src="{{ asset('catalog/view/javascript/filter/mobile_filter.js') }}"></script>
```

Kimenet:

```
<script src="https://[BOLTNEV].cdn.shoprenter.hu/catalog/view/javascript/filter/mobile_filter.js?v=[TIMESTAMP]"></script>
```

## asset_image_url()

Az `asset_image_url` függvénynek a kép fájl nevét kell csak megadni és kiegészíti a cdn-es domain névvel és verziót is kap.
Célszerű a [dinamikus modulok](../theme-development-tools/02_theme_sections.md) képfeltöltésénél használni.

### Szintaxis

```
asset_image_url(fileName)
```

### Argumentumok

**fileName**: A fájl neve amit szeretnénk teljes url-el megjeleníteni.

### Visszatérési érték

A teljes url -el tér vissza, string típusként.

Példa:

```twig
<img src="{{ asset_image_url('kepfajl.jpg') }}" />
```

Kimenet:

```html
<img src="https://[BOLTNEV].cdn.shoprenter.hu/custom/boltnev/image/data/kepfajl.jpg?v=[TIMESTAMP]" />
```

## add_script_asset()

Az `add_script_asset` függvény a rendszer saját JavaScript fájljainak hozzáadására szolgál a TPL fájlokban.  A függvény automatikusan kiegészíti a fájl URL-jét a CDN-es domain névvel és egy verzió paraméterrel és létrehoz egy `<script>` tag-et. Ez a függvény biztosítja, hogy a szükséges JS fájlok megfelelően beillesztésre kerüljenek az oldal betöltése során, és a rendszer funkciói helyesen működjenek.

### Szintaxis

```
{{ add_script_asset(filePath) }}
```

### Argumentumok

**filePath**: A fájl útvonala a gyökér könyvtártól.

### Visszatérési érték

A teljes url -el tér vissza, string típusként.

Példa:

```twig
{{ add_script_asset('catalog/view/javascript/addtocart/addtocart.js') }}
```

Kimenet:

```
<script src="https://[BOLTNEV].cdn.shoprenter.hu/catalog/view/javascript/addtocart/addtocart.js?v=[TIMESTAMP]"></script>
```

- :red_circle: **FONTOS:** Kérjük ne távolítsa el vagy módosítsa az így hozzáadott fájlokat. Ezek a szkriptek elengedhetetlenek a rendszer funkcióinak helyes működéséhez. Ezen függvény használata a rendszer saját JS fájljaira korlátozódik.
- :red_circle: **FONTOS:** Bizonyos esetekben rendszer szinten történik egy csoportosítás  és egybegyúrás az add_script_asset-el hozzáadott fájlok esetében. Ezek a fájlok minify-olva, egy másik néven érhetők el, hogy optimalizálják a betöltési időt és a teljesítményt.


## isDeviceType()

Ha szeretnénk mobil eszközön más megjelenést készíteni és már a html kódot se szeretnénk megjeleníteni, akkor az
`isDeviceType` függvény segítségével lehet feltételeket készíteni a templateben.

### Szintaxis

```
isDeviceType(deviceType)
```

### Argumentumok

**deviceType**: A device nevét kell megadni. Lehetséges értékek: mobile, tablet, desktop.

### Visszatérési érték

Boolean értékkel tér vissza: true vagy false.


Példa:

```twig
{% if isDeviceType('desktop') %}
    Csak asztalon jelenik meg
{% else if isDeviceType('mobile') %}
    <div>[-.-]</div>
{% endif %}
```

Kimenet ha PC-ről nézzük:

```html
Csak asztalon jelenik meg
```

Kimenet ha Mobiltelefonról nézzük:

```html
<div>[-.-]</div>
```
