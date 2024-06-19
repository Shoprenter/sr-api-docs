# settings.json

Az adott témához tartozó téma beállításokat tartalmazza, mint például a layout-ok és pozíciók.

```json
{
 "layouts": [],
 "positions": {}
}
```

## layouts

A layouts tömbben lehet beállítani azt hogy az adott [route](../theme-global/06_routing_system.md)-hoz milyen elrendezés
tartozzon. A layoutokhoz tartozó téma fájlokat a téma fájl szerkesztő layout mappájában lehet elérni.

Példa:

```json
{
 "layouts": [
  {
   "name": "layout/1-column-layout",
   "route": "error/not_found"
  },
  {
   "name": "layout/1-column-home-layout",
   "route": "common/home"
  },
  {
   "name": "layout/1-column-product-layout",
   "route": "product/product"
  },
  {
   "name": "layout/2-column-left-layout",
   "route": "default"
  }
 ]
}
```

A példa alapján a `default` route esetén a `layout/2-column-left-layout.tpl` fájl alapján épül fel a frontend.
Ha nincs megadva egy route-hoz egyedi layout, akkor mindig a default-nál beállított layout lesz érvényes.

Egy másik elem a példában a `common/home` route, vagyis a kezdőlap esetén már egy másik layout fájl lesz használva:
`layout/1-column-home-layout`.

## positions

A positions objektumban az adott témához tartozó modul pozíciókat lehet beállítani. A positions objektumban lévő
értékek tulajdonság nevei lesznek a pozíciók nevei, az értéke pedig egy objektum, aminél két tulajdonságot lehet
definiálni:

<table>
<tr>
<td>
deniedfor <strong>deprecated</strong>
</td>
<td>
Tömb
</td>
<td><del>
Fel lehet sorolni azokat a modulokat amiket szeretnénk letiltani ebben a pozícióban
</del>
</td>
<tr>
<td>
allowedfor
</td>
<td>
Tömb
</td>
<td>
Azon modulok felsorolása, amelyek engedélyezettek ebben a pozícióban. <strong>Dinamikus modulokat közelezően fel kell venni.</strong>
</td>
</tr>
</table>

Példa:

``` json
"positions": {
        "home": {
            "allowedfor": [
                "categoryoffer",
                "news",
                "sections/bannerslider",
                "sections/infographs",
                "sections/kickerimage"
            ]
        },
        "left": {
            "allowedfor": [
                "paf_filter",
                "customcontents"
            ]
        },
        "right": {
            "allowedfor": [
                "blog_filter",
                "customcontents"
            ]
        },
        "footer-col-1": {
            "allowedfor": [
                "sections/contact",
                "sections/likebox",
                "newsletter_subscribe"
            ]
        },
        "footer-top": {
            "allowedfor": [
                "customcontents"
            ]
        },
        "pathway": {
            "allowedfor": [
                "pathway"
            ]
        }
    }
```

A példa alapján a `home` pozícióban 5 modul van engedélyezve. `categoryoffer`, `news`, `bannerslider`, `infographs` és `kickerimage` modul.

Másik példát megnézve a `footer-top` pozícióban csak az egyedi html modulok vannak engedélyezve.
Ezeket nem kell felsorolni egyesével, hogy `customcontent1`, `customcontent2`, stb., hanem létezik egy foglalt
kulcsszó erre: `customcontents`.

Harmadik példát nézve a `pathway` pozícióban csak a `pathway` modul engedélyezett.

A pozíciók használata a ShopRenter egyik leggyakrabban használt része. Érdemes tisztában lenni velük,
ha a [dinamikus modulokat](../theme-development-tools/02_theme_sections.md) használjuk.
