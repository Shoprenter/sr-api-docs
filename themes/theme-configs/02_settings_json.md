# settings.json

Az adott témához tartozó pozíciók beállítását tartalmazza.

```json
{
 "positions": {}
}
```

## layouts (deprecated)
A layoutok setting.json-ből való beállítását Starter 2-től nem támogatjuk. A layoutokat az adott tpl-ben kell definiálni extends segítségével. Bővebb információ a Layoutok használatáról a [Layoutok](../theme-development-tools/03_layouts.md) című fejezetben található. Az alapértelmezett layout a `layout/1-column-layout.tpl`.



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
