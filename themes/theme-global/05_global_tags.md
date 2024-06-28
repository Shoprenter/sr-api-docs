# Tagek

Hamarosan

## jshrink

A jshrink segítségével a JavaScript kódunkat minimalizálhatjuk, ami csökkenti a forráskód méretét és gyorsítja a betöltési időt.

### Használat
A TPL fájlban, ahol a JavaScript kódot használjuk, a kódunkat `{% jshrink %}` és `{% endjshrink %}` közé kell tenni. Ez a két tag közötti kód automatikusan minifikáljuk a jshrink segítségével.

### Példakód

<table>
<tr>
    <td>Kód:</td>
    <td>Kimenet:</td>
</tr>
<tr>
<td>

```twig
{% jshrink %}
    <script>
        function myFunction() {
            console.log('Hello');
            // JavaScript kód
        }
    </script>
{% endjshrink %}
```

</td>
<td>

```
<script>function myFunction(){console.log('Hello');}</script>
```

</td>
</tr>
</table>

---

## schema

A `{% schema %}` tag egy speciális tag, amelyet kizárólag Dinamikus moduloknál használható a sablonokban.

Bővebben információ a [Dinamikus modulok](../theme-development-tools/02_theme_sections.md#dinamikus-modulok-schema-használata) dokumentációban található.
