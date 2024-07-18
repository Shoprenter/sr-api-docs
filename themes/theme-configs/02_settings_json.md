# settings.json

Contains the position settings for the given theme.

```json
{
 "positions": {}
}
```

## layouts (deprecated)

The configuration of layouts from settings.json is not supported from Starter 2 onwards. Layouts should be defined in the respective tpl file using extends. More information on using layouts can be found in the [Layouts]((../theme-development-tools/03_layouts.md)) chapter. The default layout is layout/1-column-layout.tpl.



## positions

In the positions object, you can set module positions for the given theme. The property names in the positions object will be the names of the positions, and the value will be an object where two properties can be defined:

<table>
<tr>
<td>
deniedfor <strong>deprecated</strong>
</td>
<td>
Tömb
</td>
<td><del>
List the modules that you want to disable in this position
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
List of modules that are allowed in this position. <strong>Dynamic modules must be included.</strong>
</td>
</tr>
</table>

Example:

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

Based on the example, the `home` position has 5 modules enabled: `categoryoffer`, `news`, `bannerslider`, `infographs`, and `kickerimage`.

In another example, the `footer-top` position only has custom HTML modules enabled. You don't need to list them individually as `customcontent1`, `customcontent2`, etc., because there is a reserved keyword for this: `customcontents`.

In a third example, the `pathway` position only has the `pathway` module enabled.

The use of positions is one of the most commonly used features in ShopRenter. It is worth understanding them when using [dynamic modules](../theme-development-tools/02_theme_sections.md).

