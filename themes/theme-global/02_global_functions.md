# Függvények

A téma fájlokhoz a [TWIG](https://twig.sensiolabs.org) template motort használja a ShopRenter. Így minden tpl
kiterjesztésű fájl TWIG szintaxisra épül. A TWIG dokumentációban látható alap függvények és filterek mellett vannak a
ShopRenter által biztosított függvények és filterek is. Ezek azért készültek, hogy a frontend fejlesztést megkönnyítsék.


## asset()

Az asset függvény az elérési útvonalat kiegészíti a cdn-es domain névvel és verziót is kap.

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
<script src="https://boltnev.cdn.shoprenter.hu/catalog/view/javascript/filter/mobile_filter.js?v=12345678"></script>
```


## asset_image_url()

Az asset_image_url függvénynek a kép fájl nevét kell csak megadni és kiegészíti a cdn-es domain névvel és verziót is kap.
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
<img src="https://boltnev.cdn.shoprenter.hu/custom/boltnev/image/data/kepfajl.jpg?v=12345678" />
```

## isDeviceType()

Ha szeretnénk mobil eszközön más megjelenést készíteni és már a html kódot se szeretnénk megjeleníteni, akkor az
isDeviceType függvény segítségével lehet feltételeket készíteni a templateben.

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
