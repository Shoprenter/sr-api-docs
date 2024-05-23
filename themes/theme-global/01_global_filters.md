# Filterek

A filterek segítségével bizonyos adatok kimenetét módosíthatjuk. Amennyiben használni szeretnénk egy filtert dupla kapcsos zárójelek között kell hozzáadnunk pipe **|** karaktert használva.
Egy kimeneten több szűrő is használható. Balról jobbra vannak elemezve.

```
{{ data | filter_name | filter_name2 }}
```

---

## asset_url

`string | asset_url` - _string visszatérési érték_

Az assets mappa alatt található css fájl minified cdn url címét adja vissza.

<table>
<tr>
    <td>Kód:</td>
    <td>Kimenet:</td>
</tr>
<tr>
<td>

```
{{ 'product-card.css' | asset_url }}
```

</td>
<td>

```
https://[SHOPNAME].cdn.shoprenter.hu/catalog/view/theme/[THEMENAME]
/minified/template/assets/product-card.css?v=1715786464.1716384141
```

</td>
</tr>
</table>

Kombinálható a [stylesheet_tag](#stylesheet-tag) filter-el.

---

## color_contrast

`string | color_contrast(string)` - _number visszatérési érték_

Kiszámítja a kontrasztarányt két szín között, és visszaadja ezt az arányszámot. A színek megadásának sorrendje nem számít.<br>
A megadott string hexadecimális színkóddal működik.

<table>
<tr>
    <td>Kód:</td>
    <td>Kimenet:</td>
</tr>
<tr>
<td>

```
{{ '#FF0000' | color_contrast('#FFFFFF') }}
```

</td>
<td>

```
4
```

</td>
</tr>
<tr>
<td>

```
{{ '#FFFFFF' | color_contrast('#FF0000') }}
```

</td>
<td>

```
4
```

</td>
</tr>
</table>

---

## currency_format
`number | currency_format` - _string visszatérési érték_

Egy adott árat formáz a webáruház pénznembeállítása alapján.

<table>
<tr>
    <td>Kód:</td>
    <td>Kimenet:</td>
</tr>
<tr>
<td>

```
{{ 105 | currency_format }}
```

</td>
<td>

```
105 Ft
```

</td>
</tr>
<tr>
<td>

```
{{ 999.6 | currency_format }}
```

</td>
<td>

```
1.000 Ft
```

</td>
</tr>
</table>

---

## global_asset_url


`string | global_asset_url` - _string visszatérési érték_


Rendszerszintű JS és CSS fájlok cdn url-jét adja vissza.

<table>
<tr>
    <td>Kód:</td>
    <td>Kimenet:</td>
</tr>
<tr>
<td>

```
{{ 'fancybox/3.5.7/css/jquery.fancybox.min.css' | global_asset_url }}
```

</td>
<td>

```
https://[SHOPNAME].cdn.shoprenter.hu/
catalog/view/javascript/vendor/
fancybox/3.5.7/css/jquery.fancybox.min.css?v=1709134277
```


</td>
</tr>
</table>

Kombinálható a [stylesheet_tag](#stylesheet-tag) és [script_tag](#script-tag) filterekkel.

---

## image_url

Hamarosan

---

## image_tag

Hamarosan

---

## placeholder_svg

Hamarosan

---

## stylesheet_tag

Hamarosan

---
## script_tag

Hamarosan

---
