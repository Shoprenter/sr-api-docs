# Starter (deprecated)
## style.scss
The stylesheet related to the theme is **assets/style.scss**, which is written in the [SCSS](https://sass-lang.com) preprocessor. At the top of the file, there is meta information related to the theme, such as which framework the theme uses, or the name of the theme.

Variables in the theme can be used in the **style.scss** stylesheet. Every variable that is defined within the presets object in the **config.data.json** file is available as an **SCSS** variable!

For example, the value of global-font-color in the JSON is #8e8e8e, and it can be used in style.scss as $global-font-color:

```scss
body {
    color: $global-font-color; // #8e8e8e
}
```

Tip: If we cannot find the initial assignment of a variable in style.scss, it is likely defined in the config.data.json file.

IMPORTANT: Do not place a background postfix SCSS variable inside a linear-gradient, as it will cause an error and prevent the CSS file from being generated!

---

## Theme files

### common/header.tpl - deprecated

The theme file representing the header. Typically includes the header along with the category menu, and in some themes, it also includes the banner manager. It is located in the ***common*** folder in the Theme File Editor.

All functions that are globally available can be used in the header.tpl as well. Details about this can be found in the [Global Functions](../theme-global/02_global_functions.md) documentation.

#### Structure

The header is included in the source code after `pagehead.tpl`. There are two HTML elements here whose closing pair
is not found in `header.tpl`. One is `<div class="page-wrap">` and the other is `<main>`. The closing parts of these two
HTML tags are found in `footer.tpl`.

The content part of the header is within the `<header>` tag. Since the header is unique for every theme, let's explore
what the **Tokyo theme** includes.

* **Mobile Menu**

Loading of the mobile menu is included in the header, within the first 3 lines. The mobile menu is displayed only if
maintenance is not enabled (`maintance`).

* **Messages**

Error messages or system messages are displayed at the top of `page-wrap` through the **shop_warning** variable. If logged
in as an admin user, a red banner appears at the top of the page.

* **Header Top Position**

The Tokyo theme includes a **header-top** position. For example, the Top line module appears here.

* **Navigation Bar**

Several modules are displayed in the navbar. On the left side, the phone number may appear (if enabled in the header) along
with language and currency switcher modules (except on mobile devices). On the right side, login and text menu items appear.

* **Footer of the Header**

Below the navigation bar, the footer of the header appears with the logo, category menu, and search and cart modules. The
search module in the Tokyo theme is special because only an icon appears. Clicking on the icon opens a full-screen window for
search. Between the search and cart icons, the wishlist icon may also appear, depending on settings and if content has been
added to the wishlist.

This bar also serves as the sticky header, meaning it stays at the top of the window when scrolling.

The header top position, navigation bar, and footer of the header do not appear in maintenance mode; only the logo is visible.
Handling this is also part of `header.tpl`.

* **Banner Position**

In the Tokyo theme, a dedicated position called `scroller` is created for the banner manager module in the header. This is
displayed only on the homepage and not in maintenance mode.

* **Breadcrumb**

The pathway or breadcrumb appears below the header and between the main content in the `pathway-top` position. The pathway
module can also be moved to another position, such as `pathway-inside`.

#### Passed Data to `header.tpl`

* **maintance**

If the site is in maintenance mode, the value of the `maintance` variable is true; otherwise, it is false.

* **shop_warning**

If there is such a message, `<div id="page-warnings">...</div>` is displayed with the appropriate text.

* **phone**

Returns the phone number provided in the store information.

* **isFrontPage** (deprecated)

If on the homepage, its value is true; otherwise, false.

---

### pagehead.tpl

Contains the opening elements `<head>` and `<body>` in the pagehead.tpl, where meta tags and scripts are placed.

##### content_for_header

It is mandatory to provide this variable in pagehead.tpl, without which the system will not function.
Place it between the opening `<head>` and closing `</head>` tags.
This variable contains the necessary ShopRenter scripts required for the system to operate.
