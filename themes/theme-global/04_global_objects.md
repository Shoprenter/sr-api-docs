# Objects

Objects available in the system allow you to easily build and customize themes. These objects come with methods and/or properties that facilitate handling settings, managing currencies, handling images, querying general system information, and accessing various routes. Below you'll find detailed descriptions of each object and how to use them.

These objects are globally accessible in every template file.

## config

### Description

Object representing the settings available in the admin interface.

### get() method

#### Syntax

```
config.get(configName)
```

#### Argument

**configName**: String representing the name of the configuration setting to retrieve.

#### Return Value

Can return various types such as String, Boolean, or Integer. Returns NULL if the setting doesn't exist.

#### Example Code:

<table>
<tr>
    <td>Code:</td>
    <td>Output:</td>
</tr>
<tr>
<td>

```twig
{% if config.get('config_show_header_phone') == 1 %}
    <div class="header-phone">{{ phone }}</div>
{% endif %}
```

</td>
<td>

```html
<div class="header-phone">06-30-123-4567</div>
```

</td>
</tr>
</table>

---
## currency
### Description
Contains information about currencies set in the online shop.

### Properties
<table>
<tr>
    <th>Property</th>
    <th>Description</th>
    <th>Type</th>
</tr>
<tr>
    <td>currencyId</td>
    <td>current currency ID, e.g., 4</td>
    <td>String</td>
</tr>
<tr>
    <td>currencyCode</td>
    <td>current currency code, e.g., HUF</td>
    <td>String</td>
</tr>
<tr>
    <td>currencyTitle</td>
    <td>current currency title, e.g., Hungarian Forint</td>
    <td>String</td>
</tr>
</table>

### Usage
The `Currency` object can be accessed via the [shop](#shop) object through the `currentCurrency` and `availableCurrencies` properties.

### Example
Retrieve the title of the first active currency (HUF in this example):

<table>
<tr>
    <td>Code:</td>
    <td>Output:</td>
</tr>
<tr>
<td>

```
{{ shop.availableCurrencies[0].currencyTitle }}
```

</td>
<td>

```
HUF
```

</td>
</tr>
</table>

---

## image

Used for handling images, the `Image` object currently only has an `src` property which stores the image source (URL). The `src` property is of type string. Available only in templates where passed.

### Example:

Accessing an image object within the content variable in news.tpl:

<table>
<tr>
    <td>Code:</td>
    <td>Output:</td>
</tr>
<tr>
<td>

```twig
{{ content.image_data.src }}
```

</td>
<td>

```
data/test.png
```

</td>
</tr>
</table>

---

## page

The `page` object is a global object used for querying general system information.

### methods
<table>
<tr>
    <th>Name</th>
    <th>Description</th>
    <th>Type</th>
</tr>
<tr>
    <td>getRoute()</td>
    <td>Returns the current request route, returns an empty string if not available.</td>
    <td>String</td>
</tr>
<tr>
    <td>getUrl()</td>
    <td>Returns the full URL of the current request.</td>
    <td>String</td>
</tr>
</table>

### Example Code for Product Page

Retrieve the current route on a product page:

<table>
<tr>
    <td>Code:</td>
    <td>Output:</td>
</tr>
<tr>
<td>

```twig
{{ page.getRoute() }}
```

</td>
<td>

```
product/product
```

</td>
</tr>
</table>

---

## language

Global object for accessing language and localization information.

### getActLangName() method

Returns the full name of the current language.

#### Szintaxis

```
language.getActLangName()
```

### getActCode() method

Returns the code of the currently set language.

#### Syntax

```
language.getActCode()
```

### getLanguages() method

Returns the list of available languages.

#### Syntax

```
language.getLanguages()
```

#### Return Value

Returns an array with the below properties.

<table>
<tr>
    <th>Property</th>
    <th>Description</th>
    <th>Type</th>
</tr>
<tr>
    <td>language_id</td>
    <td>Unique identifier of the language</td>
    <td>String</td>
</tr>
<tr>
    <td>name</td>
    <td>Name of the language</td>
    <td>String</td>
</tr>
<tr>
    <td>code</td>
    <td>Short language code (ISO-style)</td>
    <td>String</td>
</tr>
<tr>
    <td>locale</td>
    <td>Comma-separated list of locale identifiers for the language</td>
    <td>String</td>
</tr>
<tr>
    <td>image</td>
    <td>Full URL of the flag image representing the language</td>
    <td>String</td>
</tr>
<tr>
    <td>image_path</td>
    <td>Relative path to the language flag image</td>
    <td>String</td>
</tr>
<tr>
    <td>image_file</td>
    <td>Filename of the language flag image</td>
    <td>String</td>
</tr>
</table>

---

## routes

The `routes` object is an associative array where keys are route names and values are URLs associated with those routes. Always of string type.

### Example

<table>
<tr>
    <td>Code:</td>
    <td>Output:</td>
</tr>
<tr>
<td>

```twig
{{ routes.login_url }}
```

</td>
<td>

```
/customer/login
```

</td>
</tr>
</table>

### Full list
<table>
<tr>
    <td>Key:</td>
    <td>Value:</td>
</tr>
<tr><td>account_url</td><td>/index.php?route=account/account</td></tr>
<tr><td>account_edit_url</td><td>/index.php?route=account/edit</td></tr>
<tr><td>account_insert_url</td><td>/index.php?route=account/address/insert</td></tr>
<tr><td>account_password_url</td><td>/index.php?route=account/password</td></tr>
<tr><td>account_address_url</td><td>/index.php?route=account/address</td></tr>
<tr><td>account_waitinglist_url</td><td>/index.php?route=account/waitinglist</td></tr>
<tr><td>account_history_url</td><td>/index.php?route=account/history</td></tr>
<tr><td>account_invoice_url</td><td>/index.php?route=account/invoice</td></tr>
<tr><td>account_download_url</td><td>/index.php?route=account/download</td></tr>
<tr><td>account_newsletter_url</td><td>/index.php?route=account/newsletter</td></tr>
<tr><td>account_registration_contribution_url</td><td>/index.php?route=account/registration_contribution</td></tr>
<tr><td>account_affiliate_url</td><td>/index.php?route=account/aaffiliate</td></tr>
<tr><td>account_affiliate_commissions_all_url</td><td>/index.php?route=account/aaffiliate_commissions/all</td></tr>
<tr><td>account_affiliate_commissions_month_url</td><td>/index.php?route=account/aaffiliate_commissions/month</td></tr>
<tr><td>cart_url</td><td>/cart</td></tr>
<tr><td>cartpresent_url</td><td>/index.php?route=checkout/cartchildren/cartpresent</td></tr>
<tr><td>checkout_url</td><td>/checkout</td></tr>
<tr><td>contact_url</td><td>/index.php?route=information/contact</td></tr>
<tr><td>forgotten_url</td><td>/index.php?route=account/forgotten</td></tr>
<tr><td>login_url</td><td>/customer/login</td></tr>
<tr><td>logout_url</td><td>/index.php?route=account/logout</td></tr>
<tr><td>personaldata_url</td><td>/index.php?route=information/personaldata</td></tr>
<tr><td>register_url</td><td>/customer/register</td></tr>
<tr><td>manufacturer_list_url</td><td>/index.php?route=product/manufacturers</td></tr>
<tr><td>search_url</td><td>/index.php?route=product/list</td></tr>
<tr><td>sitemap_url</td><td>/index.php?route=information/sitemap</td></tr>
<tr><td>style_guide_url</td><td>/index.php?route=information/style_guide</td></tr>
<tr><td>wishlist_url</td><td>/index.php?route=wishlist/wishlist</td></tr>
<tr><td>checkout_cart_url</td><td>index.php?route=checkout/cart</td></tr>
</table>

:red_circle: Avoid hardcoding system routes directly in templates. **Use the routes object instead.**

---

## settings
Used for managing color settings defined in `config.data.json` for themes.


### get() method

#### Usage

```twig
{{ settings.get('key', 'default_value') }}
```

Returns the value of the setting named `key` if it exists. If `key` doesn't exist, returns `default_value`. Returns as a string.

#### Example

Retrieve the "global-color" setting from `config.data.json`:

<table>
<tr>
    <td>Code:</td>
    <td>Output:</td>
</tr>
<tr>
<td>

```twig
{{ settings.get('global-color', '#000') }}
```

</td>
<td>

```
#364270
```

</td>
</tr>
</table>

---

## shop

The shop object can be used to request general information about the online store.


### Properties

<table>
<tr>
    <th>Property name</th>
    <th>Description</th>
    <th>Type</th>
</tr>
<tr>
    <td>name</td>
    <td>Returns the name of the shop</td>
    <td>Sztring</td>
</tr>
<tr>
    <td>title</td>
    <td>Returns the title of the shop.</td>
    <td>Sztring</td>
</tr>
<tr>
    <td>needCountdown</td>
    <td>Returns a Boolean indicating whether there's a countdown active on the page.</td>
    <td>Boolean</td>
</tr>
<tr>
    <td>currency</td>
    <td>Returns the current currency of the shop, its properties can be found in the <a href="#currency">currency object</a></td>
    <td>Currency</td>
</tr>
<tr>
    <td>availableCurrencies</td>
    <td>Returns a list of currencies available in the shop.</td>
    <td>Array</td>
</tr>
</table>

### Example

Output the name of the shop:

<table>
<tr>
    <td>Code:</td>
    <td>Output:</td>
</tr>
<tr>
<td>

```twig
{{ shop.name }}
```

</td>
<td>

```
Demo
```

</td>
</tr>
</table>

---

## viewHelper

### viewHelper.loadModule()

Used to insert enabled or dynamic modules. If a module is assigned to a position and is also pulled in using `viewHelper.loadModule`, it will appear both in its assigned position and where `loadModule` is used.

#### Szintaxis

```
viewHelper.loadModule(moduleRoute)
```

#### Argumentok

**moduleRoute**: The module path as referenced in the admin interface.

#### Return Value

Returns the HTML code of the referenced module.

<table>
<tr>
    <td>Code:</td>
    <td>Output:</td>
</tr>
<tr>
<td>

```twig
{{ viewHelper.loadModule('module/headerlinks') }}
```

</td>
<td>

```html
<ul class="list-unstyled headermenu-list d-flex">
    <li class="headermenu-list__item d-flex nav-item">
        <a href="[BOLTNEV]/test" target="_self" class="nav-link" title="Test">
            test
        </a>
    </li>
</ul>
```

</td>
</tr>
<tr>
<td>

```twig
{{ viewHelper.loadModule('sections/section-name') }}
```

</td>
<td>

```html

<div id="section-section-name" class="section-wrapper module-editable">
    ...
</div>
```

</td>
</tr>
</table>

### viewHelper.loadPosition()

Displays all modules enabled for a given position. Positions are defined in the theme's **config/settings.json** file.

#### Syntax

```
viewHelper.loadPosition(positionName)
```

#### Arguments

**positionName**: Name of the position to load.

#### Return Value

Returns the HTML of all modules that can appear in the specified position.

Example:

<table>
<tr>
    <td>Code:</td>
    <td>Output:</td>
</tr>
<tr>
<td>

```twig
{{ viewHelper.loadPosition('home') }}
```

</td>
<td>

```html
<div id="section-section-name" class="section-wrapper module-editable">...</div>
<div id="module_news_wrapper" class="module-news-wrapper">...</div>
<div id="module_latest_wrapper" class="module-latest-wrapper">...</div>
<div id="module_kickerimage_wrapper" class="module-kickerimage-wrapper">...</div>
```

</td>
</tr>
</table>

### viewHelper.isPositionEmpty()

Checks if a given position has any modules assigned to it.

#### Syntax

```
viewHelper.loadPosition(positionName)
```

#### Arguments

**positionName**: Name of the position to check.

#### Return Value

Returns a Boolean: true or false.

Example:

<table>
<tr>
    <td>Code:</td>
    <td>Output:</td>
</tr>
<tr>
<td>

```twig
{% if viewHelper.isPositionEmpty('home') %}
    {{ viewHelper.loadPosition('home') }}
{% endif %}
```

</td>
<td>

```html
<div id="section-section-name" class="section-wrapper module-editable">...</div>
<div id="module_news_wrapper" class="module-news-wrapper">...</div>
<div id="module_latest_wrapper" class="module-latest-wrapper">...</div>
<div id="module_kickerimage_wrapper" class="module-kickerimage-wrapper">...</div>
```

</td>
</tr>
</table>
