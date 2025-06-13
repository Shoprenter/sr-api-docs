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

## product

The main data associated with the product can be accessed in the `product.tpl` file through the `product_info` object. Example code:

<table>
<tr>
    <td>Code:</td>
    <td>Output:</td>
</tr>
<tr>
<td>

```twig
{{ product_info.name}}
```

</td>
<td>

```
The product name
```

</td>
</tr>
</table>

### Full list
<table>
<tr>
    <td>Field Name:</td>
    <td>Description:</td>
    <td>Example value:</td>
</tr>
<tr>
    <td><code>product_id</code></td>
    <td>The ID of the product (string)</td>
    <td>"001"</td>
</tr>
<tr>
    <td><code>model</code></td>
    <td>Item number of manufacturers</td>
    <td>"99_001"</td>
</tr>
<tr>
    <td><code>sku</code></td>
    <td>Stock Keeping Unit - Item number (string)</td>
    <td>997000012_00</td>
</tr>
<tr>
    <td><code>gtin</code></td>
    <td>Global Trade Item Number (string)</td>
    <td>"23432420023"</td>
</tr>
<tr>
    <td><code>quantity</code></td>
    <td>Total quantity of the product in stock (number)</td>
    <td>400</td>
</tr>
<tr>
    <td><code>quantity_2</code></td>
    <td>Quantity in Warehouse 1 (string)</td>
    <td>"100"</td>
</tr>
<tr>
    <td><code>quantity_3</code></td>
    <td>Quantity in Warehouse 2 (string)</td>
    <td>"100"</td>
</tr>
<tr>
    <td><code>quantity_4</code></td>
    <td>Quantity in Warehouse 3 (string)</td>
    <td>"100"</td>
</tr>
<tr>
    <td><code>quantity_5</code></td>
    <td>Quantity in Warehouse 4 (string)</td>
    <td>"100"</td>
</tr>
<tr>
    <td><code>stock_status_id</code></td>
    <td>Out of stock status ID (string)</td>
    <td>"5"</td>
</tr>
<tr>
    <td><code>instock_status_id</code></td>
    <td>In stock status ID (string) </td>
    <td>"9"</td>
</tr>
<tr>
    <td><code>wh2_stock_status_id</code></td>
    <td>Only Warehouse 1 stock status ID (string)</td>
    <td>"9"</td>
</tr>
<tr>
    <td><code>wh3_stock_status_id</code></td>
    <td>Only Warehouse 2 stock status ID (string)</td>
    <td>"0"</td>
</tr>
<tr>
    <td><code>wh4_stock_status_id</code></td>
    <td>Only Warehouse 3 stock status ID (string)</td>
    <td>"0"</td>
</tr>
<tr>
    <td><code>wh5_stock_status_id</code></td>
    <td>Only Warehouse 4 stock status ID (string)</td>
    <td>"0"</td>
</tr>
<tr>
    <td><code>image</code></td>
    <td>Path to the main image file (string) </td>
    <td>"product/0003.jpg"</td>
</tr>
<tr>
    <td><code>manufacturer_id</code></td>
    <td>Manufacturer ID related to the product (string)</td>
    <td>"23"</td>
</tr>
<tr>
    <td><code>shipping</code></td>
    <td>Indicates if shipping is applicable for the product (string)</td>
    <td>"1"</td>
</tr>
<tr>
    <td><code>price</code></td>
    <td>Net price of the product without tax (string)</td>
    <td>"1500.0000"</td>
</tr>
<tr>
    <td><code>tax_class_id</code></td>
    <td>Tax ID associated with the product (string)</td>
    <td>"10"</td>
</tr>
<tr>
    <td><code>date_available</code></td>
    <td>Date when the product is available (string)</td>
    <td>"2015-06-05"</td>
</tr>
<tr>
    <td><code>weight</code></td>
    <td>Weight (string)</td>
    <td>"0.00"</td>
</tr>
<tr>
    <td><code>weight_class_id</code></td>
    <td>Weight measurement ID (string)</td>
    <td>"1"</td>
</tr>
<tr>
    <td><code>length</code></td>
    <td>Length (string)</td>
    <td>"0.00"</td>
</tr>
<tr>
    <td><code>width</code></td>
    <td>Width (string)</td>
    <td>"0.00"</td>
</tr>
<tr>
    <td><code>height</code></td>
    <td>Height (string)</td>
    <td>"0.00"</td>
</tr>
<tr>
    <td><code>length_class_id</code></td>
    <td>Length measurement ID (string)</td>
    <td>"1"</td>
</tr>
<tr>
    <td><code>status</code></td>
    <td>Product status: Enabled: 0, Disabled: 1, Discontinued: 2 (string)</td>
    <td>"0"</td>
</tr>
<tr>
    <td><code>date_added</code></td>
    <td>Date the product was added (string)</td>
    <td>"2013-06-05 14:57:35"</td>
</tr>
<tr>
      <td><code>date_modified</code></td>
      <td>Date of the last modification (string)</td>
      <td>"2024-10-22 12:58:23"</td>
    </tr>
    <tr>
      <td><code>sort_order</code></td>
      <td>Sorting value (string)</td>
      <td>"121"</td>
    </tr>
    <tr>
      <td><code>subtract</code></td>
      <td>Inventory reduction (1: Yes, 0: No) (string)</td>
      <td>"1"</td>
    </tr>
    <tr>
      <td><code>minimum</code></td>
      <td>Minimum order quantity (string)</td>
      <td>"1"</td>
    </tr>
    <tr>
      <td><code>maximum</code></td>
      <td>Maximum order quantity (0 means unlimited) (string)</td>
      <td>"0"</td>
    </tr>
    <tr>
      <td><code>minimum_plural</code></td>
      <td>Only multiples of the minimum order can be purchased (0: No, 1: Yes) (string)</td>
      <td>"0"</td>
    </tr>
    <tr>
      <td><code>unit_quantity</code></td>
      <td>Unit of measure (string)</td>
      <td>"0.0000"</td>
    </tr>
    <tr>
      <td><code>product_cost</code></td>
      <td>Product cost (string)</td>
      <td>"0.0000"</td>
    </tr>
    <tr>
      <td><code>szorzo</code></td>
      <td>Price multiplier (string)</td>
      <td>"1.0000"</td>
    </tr>
    <tr>
      <td><code>szorzo_lock</code></td>
      <td>Multiplier lock (1: Yes, 0: No) (string)</td>
      <td>"0"</td>
    </tr>
    <tr>
      <td><code>product_class_id</code></td>
      <td>Product type ID related to the product (string)</td>
      <td>"4"</td>
    </tr>
    <tr>
      <td><code>available</code></td>
      <td>Is the product orderable? (0: No, 1: Yes, 3: Request Quote, 4: Order) (string)</td>
      <td>"1"</td>
    </tr>
    <tr>
      <td><code>product_ring_id</code></td>
      <td>Parent product ID, if none then itself the product ID (string)</td>
      <td>"188"</td>
    </tr>
    <tr>
      <td><code>loyalty_points</code></td>
      <td>Loyalty points set for the product (string)</td>
      <td>"123"</td>
    </tr>
    <tr>
      <td><code>cetelem_free_loan</code></td>
      <td>Eligible for promotional loan (1: Yes, 0: No) (string)</td>
      <td>"0"</td>
    </tr>
    <tr>
      <td><code>custom_css_class</code></td>
      <td>Custom CSS class (string)</td>
      <td>""</td>
    </tr>
    <tr>
      <td><code>image_alt</code></td>
      <td>Alt text for the main image (string)</td>
      <td>"alt tag"</td>
    </tr>
    <tr>
      <td><code>parent_sku</code></td>
      <td>Parent product SKU (string)</td>
      <td>""</td>
    </tr>
    <tr>
      <td><code>stock_decline_notification_value</code></td>
      <td>Stock decline notification value; if empty, takes global value (string)</td>
      <td>""</td>
    </tr>
    <tr>
      <td><code>free_shipping</code></td>
      <td>Is free shipping applicable? (1: Yes, 0: No) (string)</td>
      <td>"0"</td>
    </tr>
    <tr>
      <td><code>archivable_product</code></td>
      <td>Is this a discontinued product? (0: No, 1: Yes) (string)</td>
      <td>"0"</td>
    </tr>
    <tr>
      <td><code>durable_media_device</code></td>
      <td>Is this a durable medium? (1: Yes, 0: No) (string)</td>
      <td>"0"</td>
    </tr>
    <tr>
      <td><code>name</code></td>
      <td>Product name (string)</td>
      <td>"The product name"</td>
    </tr>
    <tr>
      <td><code>meta_keywords</code></td>
      <td>Meta keywords (string)</td>
      <td>""</td>
    </tr>
    <tr>
      <td><code>meta_description</code></td>
      <td>Meta description (string)</td>
      <td>"this is the meta description"</td>
    </tr>
    <tr>
      <td><code>description</code></td>
      <td>Description (string)</td>
      <td>"description content"</td>
    </tr>
    <tr>
      <td><code>short_description</code></td>
      <td>Short description/Short specification (string)</td>
      <td>"Short description content"</td>
    </tr>
    <tr>
      <td><code>parameters</code></td>
      <td>Parameters (string)</td>
      <td>"Parameter prop: Paramtere value"</td>
    </tr>
    <tr>
      <td><code>unit_name</code></td>
      <td>Unit of measure name (string)</td>
      <td>"test"</td>
    </tr>
    <tr>
      <td><code>custom_title</code></td>
      <td>Meta title (string)</td>
      <td>"Meta title"</td>
    </tr>
    <tr>
      <td><code>robots_meta_tag</code></td>
      <td>0: Global setting; 2: index, nofollow; 3: noindex, follow; 4: noindex, nofollow (string)</td>
      <td>"0"</td>
    </tr>
    <tr>
      <td><code>quantity_name</code></td>
      <td>Name of the quantity (string)</td>
      <td>"db"</td>
    </tr>
    <tr>
      <td><code>manufacturer</code></td>
      <td>Manufacturer name associated with the product (string)</td>
      <td>"Test manufactuer"</td>
    </tr>
    <tr>
      <td><code>manufacturer_image</code></td>
      <td>Image associated with the manufacturer (string)</td>
      <td>"data/man_test.jpg"</td>
    </tr>
    <tr>
      <td><code>secondary_product_image</code></td>
      <td>URL of the first additional image among additional images (string)</td>
      <td>"product/test/test.jpg</td>
    </tr>
    <tr>
      <td><code>secondary_product_image_modified</code></td>
      <td>Date of the last modification of the second image (string)</td>
      <td>"2024-08-27 13:36:12"</td>
    </tr>
 <tr>
            <td><code>_disable_addtocart</code></td>
            <td>
                "Disable add to cart button when stock is 0" setting is set to Yes and the product is in stock (boolean)
            </td>
            <td>false</td>
        </tr>
        <tr>
            <td><code>allImages</code></td>
            <td>Array of images associated with the product</td>
            <td>Array</td>
        </tr>
        <tr>
            <td colspan="3"><strong>allImages: </strong>Each image is defined as an object. The following fields are included in the data of each image.
            <table>
                <tr>
                    <td><code>main_pic</code></td>
                    <td>Indicates whether the image is the main image for the product. (boolean)</td>
                    <td>true</td>
                </tr>
                <tr>
                    <td><code>product_id</code></td>
                    <td>The identifier of the product associated with the image. (string)</td>
                    <td>"188"</td>
                </tr>
                <tr>
                    <td><code>image</code></td>
                    <td>The file path of the image. (string)</td>
                    <td>"product/0003.jpg"</td>
                </tr>
                <tr>
                    <td><code>image_alt</code></td>
                    <td>The alternative text for the image, which appears if the image cannot be loaded. (string)</td>
                    <td>"alt text"</td>
                </tr>
                <tr>
                    <td><code>date_added</code></td>
                    <td>The date and time the image was added. (string)</td>
                    <td>"2013-06-05 14:57:35"</td>
                </tr>
                <tr>
                    <td><code>date_modified</code></td>
                    <td>The date and time of the last modification. (string)</td>
                    <td>"2024-10-22 13:17:34"</td>
                </tr>
                <tr>
                    <td><code>product_image_id</code></td>
                    <td>The unique identifier of the image associated with the product. (string)</td>
                    <td>"1530"</td>
                </tr>
                <tr>
                    <td><code>order</code></td>
                    <td>The number indicating the display order of the images. (string)</td>
                    <td>"1"</td>
                </tr>
            </table>
            </td>
        </tr>
        <tr>
            <td><code>formated_price</code></td>
            <td>The formatted price of the product (string)</td>
            <td>"1.905 Ft"</td>
        </tr>
        <tr>
            <td><code>category_name</code></td>
            <td>The name of the category in which the product is found (string)</td>
            <td>"Category name"</td>
        </tr>
        <tr>
            <td><code>parent_category_name</code></td>
            <td>The name of the parent category (string)</td>
            <td>"Parent category name"</td>
        </tr>
        <tr>
            <td><code>manufacturer_name</code></td>
            <td>The name of the manufacturer associated with the product (string)</td>
            <td></td>
        </tr>
        <tr>
            <td><code>product_on_wishlist</code></td>
            <td>Whether the product is on the wishlist (boolean)</td>
            <td>false</td>
        </tr>
        <tr>
            <td><code>product_video_code (string)</code></td>
            <td>The YouTube video identifier string associated with the product (string)</td>
            <td>""</td>
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
