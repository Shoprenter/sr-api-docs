# Filters

Filters allow us to modify the output of certain data. To use a filter, enclose it in double curly braces and separate multiple filters with a pipe **|** character. Filters are applied sequentially from left to right.

```
{{ data | filter_name | filter_name2 }}
```

---

## asset_url

`string | asset_url` - _string return value_

The CDN URL address for the minified CSS file located under the assets folder.

<table>
<tr>
    <td>Code:</td>
    <td>Output:</td>
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

It can be combined with the [stylesheet_tag](#stylesheet-tag) filter.

---

## color_contrast

`string | color_contrast(string)` - _number return value_

It calculates the contrast ratio between two colors and returns this ratio. The order of providing the colors does not matter.<br>
It works with the provided string of hexadecimal color codes.

<table>
<tr>
    <td>Code:</td>
    <td>Output:</td>
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
`number | currency_format` - _string return value_

It formats a given price according to the currency settings of the online store.

<table>
<tr>
    <td>Code:</td>
    <td>Output:</td>
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


`string | global_asset_url` - _string return value_


It returns the CDN URLs of system JS and CSS files.

<table>
<tr>
    <td>Code:</td>
    <td>Output:</td>
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

It can be combined with the [stylesheet_tag](#stylesheet-tag) and [script_tag](#script-tag) filters.

### Available assets:
<table>
<tr>
<td>bootstrap-touchspin/4.3.0/js/jquery.bootstrap-touchspin.min.js</td>
</tr>
<tr>
<td>fancybox/3.5.7/css/jquery.fancybox.min.css</td>
<tr>
<td>fancybox/3.5.7/js/jquery.fancybox.min.js</td>
</tr>
<tr>
<td>headroom/0.12.0/js/headroom.min.js</td>
</tr>
<tr>
<td>jquery/3.7.1/js/jquery.min.js</td>
</tr>
<tr>
<td>mmenu/9.3.0/css/mmenu.min.css</td>
</tr>
<tr>
<td>mmenu/9.3.0/js/mmenu.min.js</td>
</tr>
<tr>
<td>popperjs/2.11.8/js/popper.min.js</td>
</tr>
<tr>
<td>slick/1.9.0/js/slick.min.js</td>
</tr>
<tr>
<td>splidejs/4.1.4/css/splide.min.css</td>
</tr>
<tr>
<td>splidejs/4.1.4/js/splide.min.js</td>
</tr>
<tr>
<td>tippyjs/6.3.7/js/tippy.min.js</td>
</tr>
</table>

---

## image_url

`string | image_url(width, height, watermark)` - _string return value_

The image_url filter creates a CDN path for an image, optionally including specified width, height, and watermark parameters. Displaying the watermark requires enabling it in the admin interface.

:red_circle: **IMPORTANT:**
If the "Serve WebP images automatically" setting is enabled in the admin interface under the Labs menu, image_url returns the value in WebP format.

### Parameters:

<table>
<tr>
<td>width</td>
<td>number</td>
<td>The width of the image. Its value can be between 1 and 5760.</td>
</tr>
<tr>
<td>height</td>
<td>number</td>
<td>The height of the image. Its value can be between 1 and 5760.</td>
</tr>
<tr>
<td>watermark</td>
<td>boolean</td>
<td>If true, it returns the path of the image containing a watermark.</td>
</tr>
</table>

### Error handling:
- If the value of width or height is not between 1 and 5760, it returns an error message: "Image url error: Width and height must be between 1 and 5760"

### Examples:
<table>
<tr>
<td>Code:</td>
<td>Output:</td>
</tr>
<tr>
<td>

```
{{ 'path/to/image.jpg' | image_url }}
```

</td>
<td>

```
https://[SHOPNAME].cdn.shoprenter.hu/custom/[SHOPNAME]/image/path/to/image.jpg?lastmod=[TIMESTAMP]
```

</td>
</tr>
<tr>
<td>

```
{{ 'path/to/image.jpg' | image_url(width = 100, height = 150) }}
```

</td>
<td>

```
https://[SHOPNAME].cdn.shoprenter.hu/custom/[SHOPNAME]/image/cache/w100h150q100/path/to/image.jpg?lastmod=[TIMESTAMP]
```

</td>
</tr>
<tr>
<td>

```
{{ 'path/to/image.jpg' | image_url(width = 100, height = 150, watermark=true) }}
```

</td>
<td>

```
https://[SHOPNAME].cdn.shoprenter.hu/custom/[SHOPNAME]/image/cache/w100h150wt1q100/path/to/image.jpg?lastmod=[TIMESTAMP]
```

</td>
</tr>
<tr>
<td>

```
{{ kickerimage.settings.image | image_url(width = 420, height = 420) }}
```

</td>
<td>

```
https://[SHOPNAME].cdn.shoprenter.hu/custom/[SHOPNAME]/image/cache/w420h420q100/starter2_kicker_1.jpg?lastmod=[TIMESTAMP]
```

</td>
</tr>
</table>

---

## image_tag

`string | image_tag(width, height, widths, alt, class, loading, sizes)` - _string return value_

Az image_tag filter egy HTML `<img>` címkét generál az adott image_url alapján. Az attribútumokat az opcionális Parameters segítségével állíthatjuk be.

### Parameters:

<table>
<tr>
<td>width</td>
<td>number</td>
<td>The image width. If not provided, it takes the value set in the image_url filter as the default. Its value can be between 1 and 5760.</td>
</tr>
<tr>
<td>height</td>
<td>number</td>
<td> The image height. If not provided, it takes the value set in the image_url filter as the default. Its value can be between 1 and 5760.</td>
</tr>
<tr>
<td>widths</td>
<td>array</td>
<td>The array of different widths from which to generate a srcset attribute. The values of the array cannot be 0.</td>
</tr>
<tr>
<td>alt</td>
<td>string</td>
<td>Alternative text for the image. If not specified, it will be entered in the HTML with an empty value.</td>
</tr>
<tr>
<td>class</td>
<td>string</td>
<td>The CSS classes of the image. If not specified, the attribute is not included in the output.</td>
</tr>
<tr>
<td>loading</td>
<td>string</td>
<td>The loading attribute of the image (e.g. lazy). If not specified, the attribute is not included in the output.</td>
</tr>
<tr>
<td>sizes</td>
<td>string</td>
<td>The sizes attribute of the image. If not specified, the attribute is omitted from the output.</td>
</tr>
</table>

### Error handling
- If the value of width or height does not fall into the range between 1 and 5760, it gives an error message: "Image tag error: Width and height must be between 1 and 5760"
- If the widths array contains a value of 0, it gives an error message.

### Example
<table>
<tr>
<td>
Code:

```
{{ 'path/to/image.jpg' | image_url(width = 370, height = 370) | image_tag(
    loading = "lazy",
    sizes = "(max-width: 576px) 190px, (max-width: 1200px) 270px, 370px",
    widths = [370, 270 , 190],
    class = "news-card__image img-fluid",
    alt = "Test alt"
)
}}
```
</td>
</tr>
<tr>
<td>
Output:

```
<img 
  src="https://[SHOPNAME].cdn.shoprenter.hu/custom/[SHOPNAME]/image/cache/w370h370q100/path/to/image.jpg?lastmod=[TIMESTAMP]" 
  srcset="
    https://[SHOPNAME].cdn.shoprenter.hu/custom/[SHOPNAME]/image/cache/w370h370q100/path/to/image.jpg?lastmod=[TIMESTAMP] 370w,
    https://[SHOPNAME].cdn.shoprenter.hu/custom/[SHOPNAME]/image/cache/w270h270q100/path/to/image.jpg?lastmod=[TIMESTAMP] 270w, 
    https://[SHOPNAME].cdn.shoprenter.hu/custom/[SHOPNAME]/image/cache/w190h190q100/path/to/image.jpg?lastmod=[TIMESTAMP] 190w" 
  width="370" 
  height="370" 
  class="news-card__image img-fluid" 
  loading="lazy" 
  alt="Test alt" 
  sizes="(max-width: 576px) 190px, (max-width: 1200px) 270px, 370px"
 >
```

</td>
</tr>
</table>

---

## placeholder_svg

`string | placeholder_svg_tag` - _string return value_


The placeholder_svg filter can be used to generate SVG-format placeholder images.

### Example
<table>
<tr>
<td>Code:</td>
<td>Output:</td>
</tr>
<tr>
<td>

```
{{ 'default-preset' | placeholder_svg_tag }}
```
</td>
<td>
<svg width="445" height="390" viewBox="0 0 445 390" class="placeholder-svg" fill="none" xmlns="http://www.w3.org/2000/svg">
    <g filter="url(#filter0_b_2001_1057)">
        <circle cx="125" cy="265" r="125" fill="#6EB400"></circle>
        <circle cx="125" cy="265" r="124.5" stroke="white" stroke-opacity="0.3"></circle>
    </g>
    <path d="M287.68 30C295.378 16.6666 314.622 16.6667 322.321 30L439.234 232.5C446.932 245.833 437.309 262.5 421.913 262.5H188.087C172.691 262.5 163.068 245.833 170.766 232.5L287.68 30Z" fill="#AAE600"></path>
    <g filter="url(#filter1_b_2001_1057)">
        <mask id="path-4-inside-1_2001_1057" fill="white">
            <path fill-rule="evenodd" clip-rule="evenodd" d="M97 95C91.4772 95 87 99.4772 87 105V335C87 340.523 91.4772 345 97 345H327C332.523 345 337 340.523 337 335V105C337 99.4772 332.523 95 327 95H97ZM117 115C111.477 115 107 119.477 107 125V315C107 320.523 111.477 325 117 325H307C312.523 325 317 320.523 317 315V125C317 119.477 312.523 115 307 115H117Z"></path>
        </mask>
        <path fill-rule="evenodd" clip-rule="evenodd" d="M97 95C91.4772 95 87 99.4772 87 105V335C87 340.523 91.4772 345 97 345H327C332.523 345 337 340.523 337 335V105C337 99.4772 332.523 95 327 95H97ZM117 115C111.477 115 107 119.477 107 125V315C107 320.523 111.477 325 117 325H307C312.523 325 317 320.523 317 315V125C317 119.477 312.523 115 307 115H117Z" fill="white" fill-opacity="0.6"></path>
        <path d="M88 105C88 100.029 92.0294 96 97 96V94C90.9249 94 86 98.9249 86 105H88ZM88 335V105H86V335H88ZM97 344C92.0294 344 88 339.971 88 335H86C86 341.075 90.9249 346 97 346V344ZM327 344H97V346H327V344ZM336 335C336 339.971 331.971 344 327 344V346C333.075 346 338 341.075 338 335H336ZM336 105V335H338V105H336ZM327 96C331.971 96 336 100.029 336 105H338C338 98.9249 333.075 94 327 94V96ZM97 96H327V94H97V96ZM108 125C108 120.029 112.029 116 117 116V114C110.925 114 106 118.925 106 125H108ZM108 315V125H106V315H108ZM117 324C112.029 324 108 319.971 108 315H106C106 321.075 110.925 326 117 326V324ZM307 324H117V326H307V324ZM316 315C316 319.971 311.971 324 307 324V326C313.075 326 318 321.075 318 315H316ZM316 125V315H318V125H316ZM307 116C311.971 116 316 120.029 316 125H318C318 118.925 313.075 114 307 114V116ZM117 116H307V114H117V116Z" fill="white" fill-opacity="0.3" mask="url(#path-4-inside-1_2001_1057)"></path>
    </g>
    <defs>
        <filter id="filter0_b_2001_1057" x="-50" y="90" width="350" height="350" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
            <feFlood flood-opacity="0" result="BackgroundImageFix"></feFlood>
            <feGaussianBlur in="BackgroundImageFix" stdDeviation="25"></feGaussianBlur>
            <feComposite in2="SourceAlpha" operator="in" result="effect1_backgroundBlur_2001_1057"></feComposite>
            <feBlend mode="normal" in="SourceGraphic" in2="effect1_backgroundBlur_2001_1057" result="shape"></feBlend>
        </filter>
        <filter id="filter1_b_2001_1057" x="67" y="75" width="290" height="290" filterUnits="userSpaceOnUse" color-interpolation-filters="sRGB">
            <feFlood flood-opacity="0" result="BackgroundImageFix"></feFlood>
            <feGaussianBlur in="BackgroundImageFix" stdDeviation="10"></feGaussianBlur>
            <feComposite in2="SourceAlpha" operator="in" result="effect1_backgroundBlur_2001_1057"></feComposite>
            <feBlend mode="normal" in="SourceGraphic" in2="effect1_backgroundBlur_2001_1057" result="shape"></feBlend>
        </filter>
    </defs>
</svg>
</td>
</tr>
</table>

---

## stylesheet_tag

`string | stylesheet_tag` - _string return value_


The stylesheet_tag filter facilitates the loading of stylesheets with various options such as preload and lazy load. It creates a `<link>` element to load the specified CSS file. The return value is a minified version.

### Parameters:

<table>
<tr>
<td>preload</td>
<td>boolean</td>
<td>If true, we set a `Link` request header. This setting allows the stylesheet to be preloaded, thereby improving website speed and performance. Default value is false.</td>
</tr>
<tr>
<td>lazy</td>
<td>boolean</td>
<td>If true, the stylesheet is loaded later. Default value: false.</td>
</tr>
</table>

### Példák:
<table>
<tr>
    <td>Code:</td>
    <td>Output:</td>
</tr>
<tr>
<td>

```
{{ 'base.css' | asset_url | stylesheet_tag }}
```

</td>
<td>

```
<link rel="stylesheet" href="https://[SHOPNAME].cdn.shoprenter.hu/catalog/view/theme/starter2_global/minified/template/assets/base.css?v=[TIMESTAMP]">
```

</td>
</tr>
<tr>

<td>

```
{{ 'footer.css' | asset_url | stylesheet_tag(lazy = true) }}
```

</td>
<td>

```
<link rel="stylesheet" href="https://[SHOPNAME].cdn.shoprenter.hu/catalog/view/theme/starter2_global/minified/template/assets/footer.css?v=[TIMESTAMP]" media="print" onload="this.media='all'">
```

</td>
</tr>
<tr>
<td>

```
{{ 'base.css' | asset_url | stylesheet_tag(preload = true) }}
```

</td>
<td>

```
<link rel="stylesheet" href="https://[SHOPNAME].cdn.shoprenter.hu/catalog/view/theme/starter2_global/minified/template/assets/base.css?v=[TIMESTAMP]">
```

Request header:
```http request
Link: <https://[SHOPNAME].cdn.shoprenter.hu/catalog/view/theme/starter2_global/minified/template/assets/style.css?v=[]TIMESTAMP]>; rel=preload; as=style
```

</td>
</tr>
</table>

---
## script_tag

`string | script_tag` - _string return value_

The `script_tag` filter facilitates the loading of system-provided JS files with various options such as preload, defer, and async. It creates a `<script>` element to load the specified JS file. It can be combined with the [global_asset_url](#global-asset-url) filter.

### Parameters:
<table>
<tr>
<td>preload</td>
<td>boolean</td>
<td>If `true`, sets a `Link` request header. This allows the script to be preloaded, improving website speed and performance. Default value: `false`.</td>
</tr>
<tr>
<td>defer</td>
<td>boolean</td>
<td>If `true`, the script will be executed after the document parsing is complete. Default value: `false`.</td>
</tr>
<tr>
<td>async</td>
<td>boolean</td>
<td>If `true`, the script will be executed asynchronously as soon as it becomes available. Default value: `false`.</td>
</tr>
</table>


### Examples:
<table>
<tr>
    <td>Code:</td>
    <td>Output:</td>
</tr>
<tr>
<td>

```
{{ 'mmenu/9.3.0/js/mmenu.min.js' | global_asset_url | script_tag }}
```

</td>
<td>

```
<script src="https://[SHOPNAME].cdn.shoprenter.hu/catalog/view/javascript/vendor/mmenu/9.3.0/js/mmenu.min.js?v=[TIMESTAMP]"></script>
```

</td>
</tr>
<tr>
<td>

```
{{ 'mmenu/9.3.0/js/mmenu.min.js' | global_asset_url | script_tag(defer = true) }}
```

</td>
<td>

```
<script defer src="https://[SHOPNAME].cdn.shoprenter.hu/catalog/view/javascript/vendor/mmenu/9.3.0/js/mmenu.min.js?v=[TIMESTAMP]"></script>
```

</td>
<tr>
<td>

```
{{ 'jquery/3.7.1/js/jquery.min.js' | global_asset_url | script_tag(preload = true) }}
```

</td>
<td>

```
<script src="https://[SHOPNAME].cdn.shoprenter.hu/catalog/view/javascript/vendor/jquery/3.7.1/js/jquery.min.js?v=[TIMESTAMP]"></script>
```

Request header:

```http request
Link: <https://[SHOPNAME].cdn.shoprenter.hu/catalog/view/javascript/vendor/jquery/3.7.1/js/jquery.min.js?v=[TIMESTAMP]>; rel=preload; as=script
```

</td>
</tr>
<tr>
<td>



</td>
<td>



</td>
</tr>
</table>

---
