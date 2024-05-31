# config.data.json

A téma konfigurálásához szükséges adatokat tartalmazza JSON formátumban.

Két részből áll, az assets és a presets részből:

```json
{
 "assets": {},
 "presets": {}
}
```

## assets

Az assets objektumban vannak nyilvántartva a témához tartozó képek. Ezek például a bélyegképek, amelyek az admin
felületen megjelennek a téma kiválasztás oldalon.


Példa:

```json
{
 "assets": {
  "base": {
   "thumb": "starter2.jpg"
  },
  "blue": {
   "thumb_small": "starter2_blue.jpg",
   "thumb_big": "starter2_blue_n.jpg"
  },
  "green": {
   "thumb_small": "starter2_green.jpg",
   "thumb_big": "starter2_green_n.jpg"
  }
 }
}
```

## presets

A presets objektumban találhatóak a témához tartozó szín változók. Ezen változók alapján jön létre
a **Téma testreszabás** oldalon a **Téma színek** fül tartalma.

Minden változóhoz tartozik egy ColorPicker vagy BackgroundPicker.
Ha a változó nevében a postfix color, akkor ColorPicker jelenik meg, ha a postfix background akkor BackgroundPicker,
ha pedig egyik sem, akkor egy text típusú input mező. A ColorPicker-nél egy színt lehet csak kiválasztani, míg a
BackgroundPicker segítségével színátmeneteket is lehet megadni.

<table>
  <tr>
    <th>Postfix</th>
    <th>Megjelenés</th>
  </tr> 
  <tr>
    <td>-color</td>
    <td>ColorPicker</td>
  </tr>
  <tr>
    <td>-background</td>
    <td>BackgroundPicker</td>
  </tr>
  <tr>
    <td>egyik sem</td>
    <td>input['type=text']</td>
  </tr>
</table>   


Példa:

```json
{
    "presets": {
        "base": {
            "cart-icon": "50",
            "global-border-radius": "0",
            "body-background": "#ffffff",
            "global-font-color": "#8e8e8e",
            "global-font-light-color": "#ffffff",
            "global-light-color": "#ffffff",
            "global-dark-color": "#2d2d2d",
            "input-border-color": "#ebebeb",
            "input-color": "#2d2d2d",
            "input-background": "#ffffff"
        },
        "blue": {
            "global-color": "#3da0e3",
            "global-hover-color": "#2487CA",
            "link-color": "#3da0e3",
            "link-hover-color": "#2487CA"
        },
        "green": {
            "global-color": "#68a742",
            "global-hover-color": "#4F8E29",
            "link-color": "#68a742",
            "link-hover-color": "#4F8E29"
        },
        "custom": {
            "global-color": "#ffcc00"
        }
  }
}
```

A presets objektum közvetlen gyerek elemei a különböző színváltozatokat tartalmazza, illetve a **base** és a **custom**
objektumok speciális foglalt nevek. A **base** objektum tartalmazza az alap változókat, amik minden színváltozatnál megegyeznek,
a példában a **blue** és a **green** változatok pedig azokat a változókat tartalmazza amikben a színváltozat eltér.
Az assets és a presets objektumban ugyanazok a változatok szerepelnek. Ha az admin felhasználó a Téma színek
oldalon módosítja a színeket akkor a módosult érték a **custom** objektumban kerül eltárolásra.

**Téma másolás** használatakor a változatok (blue, green) nem kerülnek átmásolásra, a lemásolt téma, ha például
a blue volt, akkor a blue objektum változói átkerülnek a **base** objektumon belülre.

## Használat
A változók bármely tpl fájlban elérhetőek, a [settings](../theme-global/04_global_objects.md#settings) objektum **get** metódusának segítségével:

```
{{ settings.get('global-color', '#000') }}
```

A settings objektumból a get metódus segítségével lekért változókat érdemes a :root pszeudó-osztályban CSS változókon keresztül átadni, így könnyen használható bármelyik CSS fájlban:

```
<style>
:root {
    --main-color: {{ settings.get('global-color', '#000') }};
}
</style>
```
base.css:
```css
body {
 color: var(--main-color);
}
```
