# Starter 2.0

Starter 2.0 is a starter theme within the Shoprenter system, specifically developed for partners creating unique designs. Developers have the opportunity to fully customize the theme.

---

## CSS Structure

The theme optimally loads CSS files to minimize page load times and enhance user experience.

CSS files are loaded only when necessary for the specific page or functionality.

In general, we strive to load only those CSS files that are actually used in different parts of the application, with a few exceptions. These exceptions include fundamental style files and third-party CSS files essential for page rendering and proper functionality.
1. <b>base.css</b>: Contains fundamental base styles and formatting essential for structuring the page and overall appearance.
2. <b>header.css</b> and <b>footer.css</b>: Contains styling for the header and footer.
3. <b>product-card.css</b>: Includes styling for product cards.
3. <b>Third-party CSS files</b>: In some cases, we use third-party styles necessary for certain functionalities or components.

CSS files are located in the <b>assets</b> folder and can be modified using the theme file editor.

CSS files are loaded in TPLs using the [stylesheet_tag](../theme-global/01_global_filters.md#stylesheet-tag) filter. Example:
``` {{ 'base.css' | asset_url | stylesheet_tag(preload = true) }} ```

---

## CSS Variables

General CSS properties (e.g., gap, gutter) are defined in base.css, while colors are set in pagehead.tpl.
Here's an example of adding a general rule:

``` 
:root {
    --custom-property: red;
}
```
usage:
``` 
body {
    color: var(--custom-property);
}
```

---

## Images

Images in the theme are handled using [image_tag](../theme-global/01_global_filters.md#image-tag) or [image_url](../theme-global/01_global_filters.md#image-url) filters. Below-the-fold images are always equipped with the loading="lazy" attribute.

---

## Featured TPL Files
### pagehead.tpl (common/pagehead.tpl)

Contains the opening `<head>` and `<body>` elements, where meta tags and scripts are placed.

#### content_for_header
It's mandatory to provide this variable in pagehead.tpl; the system won't function without it.
It should be placed between the opening `<head>` and closing `</head>` tags.
This variable includes essential ShopRenter scripts required for the system to operate.

## Colors
Colors are injected into the document via CSS variables using the :root pseudo-class, defined in the [config.data.json](../theme-configs/01_config_data_json.md) file. This allows colors to be used at both tpl and css levels. Ensuring proper color contrast is achieved using the [color_contrast](../theme-global/01_global_filters.md#color-contrast) filter.

## Fonts
Fonts are loaded through the snippets/fonts.tpl file using @font-face rules, which are then applied to the body element in base.css. By default, fonts hosted on our own server are used.

---

## header.tpl (sections/header.tpl)
Handles the display and functionality of the header [dynamic module](../theme-development-tools/02_theme_sections.md ). Includes:
1. Phone number, email address
2. Header links
3. Language switcher and currency switcher modules
4. Hamburger/mobile menu
5. Logo
6. Search module
7. Wishlist module
8. Login link
9. Cart module
10. Category module

<i>The logo within the dynamic module appears exclusively in the header. In the admin interface, the general settings logo appears in all other cases (e.g., order confirmation emails).</i>

---

## footer_scripts.tpl (common/footer_scripts.tpl)
Handles the loading of JS files specific to the theme. JavaScript codes within this file are inserted just before the closing ``</body>`` tag of the document in the layout/base.tpl file using the [include twig tag](https://twig.symfony.com/doc/1.x/tags/include.html).

---

# 3rd Party Solutions
Third-party tools are hosted on our own server and loaded using the [script_tag](../theme-global/01_global_filters.md#script_tag) filter.
1. [jQuery 3.7.1](https://jquery.com/)
2. [FancyBox 3.5.7](https://fancyapps.com/)
3. [Mmenu JS 9.3.0](https://mmenujs.com/)
4. [Slick JS 1.9.0](https://kenwheeler.github.io/slick/)
5. [Tippy JS 6.3.7](https://atomiks.github.io/tippyjs/)
6. [Popper JS 2.11.8](https://floating-ui.com/?utm_source=popper.js.org)
7. [jQuery.countdown](https://github.com/hilios/jQuery.countdown)
