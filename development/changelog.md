# API changelog

#### 2026.01.15
A change has been made to the [Webhook Resource](../api/webhook.md):

- Three new fields have been added to the "Order confirm" and "Order status change" events:
  - **orderProduct_durableMediaDevice** - Boolean value indicating whether the ordered product is a durable media device, enabling billing systems to associate the appropriate license code.
  - **orderProduct_gtin** - The barcode of the ordered product.
  - **orderProduct_model** - Manufacturer's part number of the ordered product.
- A new field **orderHistory_dateAdded** has been added.
- We have expanded the events that can be added to [WebHook resource](../api/webhook.md) with an additional option: **abandoned_cart** - When a visitor abandons their cart.

#### 2025.09.03
We introduced a new API Resources:
- [CmsContentListExtend](../api/cms_content_list_extend.md) - This resource can be used to manage CMS content lists.
- [CmsContentListDescription](../api/cms_content_list_description.md) - This resource can be used to manage descriptions of CMS content lists in different languages.
- [CmsContentListCmsContentRelation](../api/cms_content_cms_list_relation.md) - This resource can be used to manage the relationship between CMS content lists and CMS content items.

We improved the [CmsContentExtend Resource](../api/cms_content_extend.md) by adding a new field: **cmsContentLists**. This field provides information about the CMS content lists associated with a specific CMS content item.

#### 2025.08.14
We’ve expanded the orderProducts object with four new fields:
- originalPriceCurrency
- priceCurrency
- grossPriceCurrency
- originalGrossPriceCurrency

This allows product base prices to be correctly multiplied by exchange rates when converting between currencies.

#### 2025.08.06
A new API Resource [OrderHistories](../api/order_history.md) has been added.
This resource allows you to retrieve the status change history of orders.

#### 2025.07.24
We are introducing OAuth2 Authentication for enhanced API security and flexibility.

**New documentation available:**
- [**Guide for custom shop API client credentials**](api/10_custom_api_clients.md) - Learn how shop owners can generate their own API clients
- [**Required scopes for each API endpoint**](/api/address.md) - Every API endpoint now displays the required scopes for each request method
- [**Complete API scopes overview**](api/11_scopes.md) - Comprehensive list of all scopes across all endpoints
- [**Acquiring access tokens**](api/12_acquiring_an_access_token.md) - Step-by-step guide for obtaining OAuth2 access tokens
- [**Authentication migration guide**](api/12_acquiring_an_access_token.md#authentication-migration-guide) - Instructions for migrating from legacy authentication to OAuth2

#### 2025.05.28
A change has been made to the [Order Product Resource](../api/order_product.md):

- Two new fields have been added: **gtin** and **durableMediaDevice**.

#### 2025.05.27

A change has been made to the [Coupon Resource](../api/coupon.md):

- A new field has been added: **bypassMinOrderLimitWithCoupon**.

#### 2025.05.07
A new API Resource [OrderCreditCards](../api/order_credit_card.md) has been added.
- This resource can be used to get the credit card information associated with an order.
- The new resource is also available in the **orderCreditCards** field of the [Order Extend Resource](../api/order_extend.md).

#### 2025.03.19
A change has been made to the following resources:

- [Product Addon Resource](../api/product_addon.md)
- [Order Product Addon Resource](../api/order_product_addon.md)

taxClass field added

#### 2025.03.05
A change has been made to the following resources:

- [Product Description Resource](../api/product_description.md)
- [Product Extend Resource](../api/product_extend.md)
- [Product Resource](../api/product.md)

Requests containing an invalid languageId or taxClassId will now be rejected with a 400 Bad Request response.

#### 2025.02.25

A change has been made to the [Coupon Resource](../api/coupon.md):

- Four new fields have been added: **validToSpecialProducts**, **validWithGiftProducts**, **validWithBulkDiscount** and **validWithLoyaltyPoints**.

#### 2025.01.22
Updated Status Codes for DELETE Requests on [Extend Resources](api/06_extend_resource.md):
- The API now returns a **204** status code upon a successful DELETE request for Extend Resources.
- If the target resource does not exist, the API will respond with a **404** status code.
- In cases of other errors, the API will continue to return the appropriate status codes.

#### 2025.01.08
The following setting has been added to the [Settings Resource](../api/setting.md):
- **feature_switch_libvips** - Automatic serving of WebP images.

#### 2024.12.12
A change has been made to the [CMS Content Extend Resource](../api/cms_content_extend.html):
- A new field have been added: **cmsContentTags**

#### 2024.12.11

A change has been made to the [Webhook Resource](../api/webhook.md):

- Two new fields have been added: **order_loyaltyPoints** and **order_loyaltyPointsUsed**.

#### 2024.12.03

A change has been made to the [Coupon Resource](../api/coupon.md):

- A new field **maxOrderLimit** has been added.

#### 2024.10.07

We have introduced the following updates to our API:

[Order Products Resource:](../api/order_product.md)

Two new properties have been added:

- grossPrice: The gross price of the product at the time of purchase

- originalGrossPrice: The original gross price of the product.

[Webhook Resource:](../api/webhook.md)

A new property has been added to the webhook:

- orderProduct_grossPrice: The gross price of the ordered products.

#### 2024.09.05
A change has been made to the [Webhook Resource](../api/webhook.md):

- A new field **orderProduct_durableMediaDevice** has been added to the "Order confirm" event.

#### 2024.09.02

The following changes have been made to the [Webhook Resource](../api/webhook.md):

The fields **order_paymentCountryIsoCode2** and **order_paymentCountryIsoCode3** are now available for both the "Order confirm" and "Order status change" events.

#### 2024.08.29

We’ve enhanced the Payment API by introducing a new feature: Plan management. You can now create, update, and delete plans directly through the API, giving you greater control and flexibility in managing your payment offerings.

#### 2024.08.15

The following changes have been made to the [Webhook Resource](../api/webhook.md):

- The field **order_shippingCountryIsoCode2** is now available for the "Order status change" event.
- A new field **order_shippingCountryIsoCode3** has been added to both the "Order confirm" and "Order status change" events.

#### 2024.08.15

We created new API Resource for [OrderInvoice](../api/order_invoice.md).

#### 2024.08.13

The durable media device field has been added to the [Product](../api/product.md) and 
[ProductExtend](../api/product_extend.md) resource documentation.

#### 2024.07.15

We have fixed the issue where if a script was placed via a Script tag Resource on the "thank_you_page", it did not execute upon order submission.

#### 2024.07.03

The announced bug fixes on the [ProductClass](../api/product_class.md) and [ProductClassAttributeRelation](../api/product_class_attribute_relation.md) resources have been implemented, which may cause backward incompatible behavior. More detailed information can be found at the [following link.](https://changelog.shoprenter.hu/hu/termektipus-valtozasok-az-api_ban-juniustol-Vzq3OfnF)

#### 2024.06.20
The Deposit Fee system has become available in Hungary, for which we created new API Resources and expanded old ones.

**New API Resources:**<br>

**1. Creating a Deposit:** `Product Addon Resource`<br>
- **Function:**  This API Resource allows the creation of deposits in the system.
- **Data:** All necessary data for each deposit is defined here, such as amount, type, VAT.<br>

**2. Linking Deposit with Product:** `Product Addon Product Relation Resource`<br>

- **Function**`: This API Resource is responsible for linking deposits and products.

- **Opportunity:** It allows adding the appropriate deposit to a given product.<br>

**3. Ordered Deposits:** `Order Product Addon Resource`<br>

- **Function:** This API Resource is used for managing the deposits ordered during the ordering process.<br>

- **Information:** It provides information about the ordered deposits and ensures their tracking in the order process.<br>

Extending existing API Resources with Product Addon information:

- [Order Resource](../api/order.md)

- [Order Extend Resource](../api/order_extend.md)

- [Product Resource](../api/product.md)

- [Product Extend Resource](../api/product_extend.md)

- [Webhook](../api/webhook.md)

#### 2024.04.12
The Shipping Additional Cost fields have been added to Webhook Resource. [Webhook Resource](../api/webhook.md)

#### 2024.04.11
Limited discount fields were added to Product Special Resource. [Product Special Resource](../api/product_special.md)

#### 2024.03.16
We have fixed the encoding of special characters used in the shipping and billing addresses associated with orders in API requests.

The following setting has been added to the [Settings Resource](../api/setting.md):

- **config_mobile_simple_snapshot** - Simplified mobile product card
- **config_number_of_columns_in_category_page** - Number of products per row on category page in desktop view
- **config_number_of_columns_in_category_page_in_mobile** - Number of products per row on category page in mobile view
- **config_search_dropdown** - Enable dropdown search module

#### 2024.03.11
All Shipping Mode has become queryable from the Shipping Mode Extend Resource. [Shipping Mode Extend Resource](../api/shipping_mode_extend.md) But the 'extension' field is still read-only!

#### 2024.01.17
The Wolt Shipping mode has been added to the possible values of shippingMethodExtension [Order Extend Resource](../api/order_extend.md)

#### 2024.01.03
If we added a product to an order through the admin interface and then queried the order via the API using the [Order Product Resource](../api/order_product.md), we might have observed that the product appeared in the query without price. We have fixed this issue.

#### 2023.11.09
Deleting the default customer group will no longer be possible via API requests. The response code will be "400 The default customer group cannot be deleted."

The maximum identifier for orders created via API requests can be the maximum value of a 32-bit signed integer (2,147,483,647). Order identifiers greater than this number will not be generated in the system.

#### 2023.10.02
The following setting has been added to the [Settings Resource](../api/setting.md):
<br>**config_display_quantity_name** - Unit of measurement appears on the product page after the input field.

#### 2023.09.28
Two new shipping methods were added: Sameday shipping and Easybox parcel locker. These methods' values are the following: SAMEDAYSHIPPING and EASYBOX.

#### 2023.09.26
We translated the whole developer documentation to english.

#### 2023.09.05
We made it easier to retrieve and manage parent-child product relationships in the Shoprenter API. Filtering has become possible in the [Product](../api/product.md) and [ProductExtend](../api/product_extend.md) resources. Specifying `parentProductId` as a parameter in the filter returns products with the same `parentProductId`.

If we deleted a manufacturer using the [Manufacturer](../api/manufacturer.md) Resource, the corresponding search-friendly url value remained in the database and could be queried. Thanks to a fix, when the manufacturer is deleted, the corresponding url will also be deleted.

#### 2023.09.04
The following setting has been added to the Setting Resource:
- **config_display_quantity_in_category** - Display the quantity field on the category page when shopping.

#### 2023.08.21
In the event that textual content was deleted using the [CMS Extend](../api/cms_content_extend.md) Resource, the corresponding search-friendly url value remained in the database and could be queried. Thanks to a fix, when text content is deleted, the associated url will also be deleted.

#### 2023.08.05
If a category was deleted using the [Category Extend](../api/category_extend.md) Resource, the corresponding search-friendly url value remained in the database and could be queried. Thanks to a fix, when you delete the category, the corresponding url will also be deleted.

#### 2023.08.01
If we try to delete a property several times with the DELETE method, after each request the API returns a status code of 204, i.e. a successful deletion. According to this bugfix, the API will return a 204 response code only after the first successful deletion, and all subsequent deletion requests will return with a 404 response code.

#### 2023.07.10
[Order](../api/order.md) and [OrderExtended](../api/order_extend.md) resource added a new optional field `externalInfo`. This field contains two required parameters: `partner_order_id` and `partner_prefix`.
These identifiers can be useful if an order placed on an external marketplace (e.g. Emag marketplace) is also created in the Shoprenter web store using an API. If these identifiers are entered for the order, it is also possible to search for them on the order list page.

#### 2023.05.23
We have created the [Reload Order Url resource](../api/reload_order_url.md). This resource can be used to create a unique url for incomplete orders (Abandoned carts).

#### 2023.05.10
In the case of [Product List Attribute Value Relation Resource](../api/product_list_attribute_value_relation.md), we have improved the use of the “page” parameter and from now on the results of all pages can be queried.

#### 2023.03.29
We expanded the content of [webhooks](../paymentapi/docs/l_notifications.md) that notify app developers. The reason for sending is now also included in the webhooks that we send when a subscription is stopped.

We have improved the functionality of [Payment plans](../paymentapi/docs/h_plan.md) that can be defined by app developers. Now, if the price or name of the Payment plan changes, the existing app subscriptions will be renewed with the changes.

#### 2023.03.01
We have expanded the possible values of [Order extend resource](../api/order_extend.md) and [Order resource](../api/order.md) with an additional option:
- **shippingMethodExtension** - GLSPARCELSHOP has been split into two, it now has GLSPARCELPOINT and GLSPARCELLOCKER instead.
- **shippingMethodExtension** - Foxpost home delivery and Foxpost
  parcel machine value has been improved.

#### 2023.01.02
We expanded the [Script Tag resource](../api/script_tag.md) parameters with an additional option:
- **displayArea** - This field shows exactly where the script used in the call was or can be placed.

#### 2023.01.27
We have expanded the events that can be added to [WebHook resource](../api/webhook.md) with three additional options:
- newsletter subscription (newsletter_subscribe)
- newsletter unsubscribe (newsletter_unsubscribe)
- change newsletter subscriber data (newsletter_update_subscriber)

#### 2022.12.23
We have improved the functionality of the 'onCheckoutInitiated' event to ensure that it activates at the beginning of the checkout process.

#### 2022.11.30
A new search parameter has been added to the [Order](../api/order.md) and [OrderExtend](../api/order_extend.md) Resources called "innerIdMin".\
With this, we can filter by the internal identifier of orders, with greater than or equal logic.

#### 2022.11.21
Fix WebHook Resource Parameters.\
From now on [WebHook Resource](../api/webhook.md) "page", "limit" and "full" Parameters can be used properly. These were indicated in the documentation as such before, however, it was not possible to use them, we fixed this problem.

Customer Group Product Price Resource change.\
When using [Customer Group Product Price Resource](../api/customer_group_product_price.md) "customerGroup" and "product" are now required properties. Without specifying them, it is not possible to create customer group product prices. This requirement is also stated in the developer documentation. It is not mandatory to enter them when changing the resource.

#### 2022.10.05
2 new [Frontend API Events](frontend-api/01_shoprenterjs_api.md) have become available.\
With the help of new events, we can subscribe to additional customer activities.
- [onCheckoutShippingInfoAdded](frontend-api/01_shoprenterjs_api.md#oncheckoutshippinginfoadded)
- [onCartPageViewed](frontend-api/01_shoprenterjs_api.md#oncartpageviewed)

Furthermore, the existing [onCheckoutOrderConfirmed](frontend-api/01_shoprenterjs_api.md#oncheckoutorderconfirmed) has been expanded with the gross price of the delivery method and the VAT content of the order.

#### 2022.08.25
4 new [Frontend API Events](frontend-api/01_shoprenterjs_api.md) have become available.\
With the help of new events, we can subscribe to failed payment and customer profile activities.
- [onCheckoutOrderPaidUnsuccessful](frontend-api/01_shoprenterjs_api.md#oncheckoutorderpaidunsuccessful)
- [onCustomerRegistered](frontend-api/01_shoprenterjs_api.md#oncustomerregistered)
- [onCustomerLoggedIn](frontend-api/01_shoprenterjs_api.md#oncustomerloggedin)
- [onCustomerUpdated](frontend-api/01_shoprenterjs_api.md#oncustomerupdated)

#### 2022.08.24
8 new [Frontend API Events](frontend-api/01_shoprenterjs_api.md) became available.
With the help of new events, we can subscribe to visitor and customer activities.

#### 2022.05.09
A new feature has become available for the Payment API, [Bank card change](../paymentapi/docs/j_funding_source_change.md).
With its help, we can exchange the bank cards for our Recurring fee payments with our users.

#### 2022.03.23.
The 'DELETE' method of our [Order](../api/order.md) resource has been removed.

#### 2022.03.09.
The 'DELETE' method of our [Order](../api/order.md) resource will be discontinued on March 23, 2022. The relevant description will be removed from the documentation as of today, but of course the method is still available and can be used without any problems until the mentioned date.

#### 2022.02.15.
Descriptions have been added to the [Weight](../api/weight_class.md) and [Length](../api/length_class.md) Class Resources.
- [Weight Class Description](../api/weight_class_description.md)
- [Length Class Description](../api/length_class_description.md)

Texts contents are now also available via API:
- [CMS Content Extend Resource](../api/cms_content_extend.md)
- [CMS Content Description Resource](../api/cms_content_description.md)

The Webhook API has been extended with a Volume Discount field. [Webhook Resource](../api/webhook.md)

#### 2022.01.10.
[WebHook Resource](../api/webhook.md) got two new sendable fields:
- order_expectedDeliveryDate (Order Status Change)
- order_newsletterChecked (Send new order

#### 2021.12.20.
We have introduced a new limitation on product properties: A maximum of 300 units can be created
using [List Attribute](../api/list_attribute.md), [Text Attribute](../api/text_attribute.md) and [Number Attribute](../api/number_attribute.md) Resource.

#### 2021.11.09
Added two badge settings to [Settings Resource](../api/setting.md): config_badge_max and config_badge_orientation

#### 2021.10.11
Payment API [One-time](../paymentapi/docs/g_one_time_charge.md) and [Recurring charges](../paymentapi/docs/i_recurring_charge.md) can now be queried with a GET request.

#### 2021.08.17

The Shoprenter Payment API documentation has been made available on the site. [SR Payment API](../paymentapi/docs/a_introduce.md)

#### 2021.08.10

- The ***.api.shoprenter.hu** system domain will soon cease to exist, the API Resources will be available on the ***.api.myshoprenter.hu** domain instead. So it will be worthwhile to switch and update the integrations as soon as possible.
- In the documentation of [Order Resource](../api/order.md) and [Order Extend Resource](../api/order_extend.md), we indicated the possible values of **shippingMethodExtension** and **paymentMethodCode**, in a table reserved.
- [Order Resource](../api/order.md), [Order Extend Resource](../api/order_extend.md), [Product Resource](../api/product.md) and [Product We clarified the description of some of the properties of Extend Resource](../api/product_extend.md).
- We clarified the API limit restrictions

#### 2021.07.07
Now in [Webhook Resource](../api/webhook.md), with the **fields** property of webHookParameters, we can control which fields Shoprenter sends to the url we specify.

#### 2021.05.06
For POST and PUT requests of Product and Product Extend Resource, the price multiplier is now updated according to the settings of the "band price multipliers" function.

#### 2021.03.10
Added productInnerId field to [Order Product Resource](../api/order_product.md).
This is the internal identifier of the ordered product, so there is no need to call the product resource link if that's all we're after
they are curious

#### 2021.02.23
Added innerId field to [Order Product Resource](../api/order_product.md).
Of course, this is the internal identifier of the individuals describing the relationship between the order and the product,
not the product!

#### 2021.02.16
Added a new property to [**Order**](../api/order.md) and [**Order Extend**](../api/order_extend.md) Resource:
**shippingMethodLocalizedName**
This contains the **current** name of the delivery method in the language of the order.

#### 2021.02.11
- Date filters for **Customer/Customer Extend** and **Order/OrderExtend Resource** have been added.
  Narrowing the collection by date has become much more customizable.
- Added a new API endpoint: [**Tax Class Extend Resource**](../api/tax_class_extend.md)
  Thus, the VAT rates do not have to be retrieved via a link.
- 
#### 2021.02.09
- Added a **parentProduct** property to [**Order Product Resource**](../api/order_product.md).
  It is typically inspired by tasks where we need to know what the ordered product is when processing an order
  does it have a parent product. Read only!
- Added a **coupon** property to [**Order Extend Resource**](../api/order_extend.md). All data of the used coupon
  included. Read only!
- In [**Order Extend Resource**](../api/order_product.md) **paymentCountry**, **shippingCountry**,
  **language** and **currency** properties have been opened. They are read only!

#### 2021.01.27
- For POST and PUT requests of Product and Product Extend Resource, the price multiplier is now updated according to the settings of the "band price multipliers" function.

#### 2021.01.19
- The [**Getting started**](./app-development/01_getting_started.md) document has been corrected and the "app_url" description has been added.
- Setting resource was added with the store's time zone (**config_timezone**). [documentation](../api/setting.md)

#### 2020.11.24
- Added a [**Add Order**](./api-examples/09_create_order.md) example to the API examples.

#### 2020.10.30
- The API examples have been supplemented with an example [**"Send new order" webhook operation**](./api-examples/06_webhook.md).
- Added a [**Handling product option**](./api-examples/07_product_option.md) example to the API examples.
- Added a [**Product attribute handling**](./api-examples/08_product_attribute_handling.md) example to the API examples.

#### 2020.10.29
- The [**API Batch processing**](api/04_batch.md) menu item has been added with additional examples: [**Product creation with batch**](api/04_batch.md#tomeges-termekeftolttes), [**Attach product to category using Outer ID**](api/04_batch.md#product-add-to-category-with-outer-id-help)
- [**Usage of Outer ID**](api/05_outer_id.md) has been added with an entry describing in which cases it is wrong to use Outer ID.

#### 2020.10.27
- The API menu item has been supplemented with [**postman usage example code entry**](api/08_postman.md)

#### 2020.10.26
- Added an [**Attach image to product**](./api-examples/05_attach_uploaded_image_to_product.md) example to the API examples.
- Added a [**Product Special**](./api-examples/01_0_product_special.md) example to the API examples.

#### 2020.10.22
- Added an [**Attach product to category**](./api-examples/04_attach_product_to_category.md) example to the API examples.

#### 2020.13.10
- The page search engine has been changed, in which you can now search not only for the name of the page, but also for its contents.

#### 2020.07.21
- The value of the Product Extend Resource "productPrices" has changed. Description of the operation [link](./api-examples/03_price_calculation.md)

#### 2020.05.18
- Integrated shipping modes have become available through the Shipping Mode Extend Resource. Important: only shipping methods edited on the Shoprenter admin are available and WSESHIP (custom, created by users) types can be changed via API.

#### 2020.05.14
- The UrlAliases property was added to the Information Extend Resource, and the visibility of the Text menu items added with resouce became controllable:

https://doc.shoprenter.hu/api/information_extend.html

Of course, the URL Alias Resource has also been expanded. From now on, INFORMATION type alias can also be handled:

https://doc.shoprenter.hu/api/url_alias.html

#### 2020.04.15
- The example applications menu item has been supplemented with a demo application based on a wider Slim framework.

#### 2020.07.04
- Product Description Resource was added with the metaTitle property.

#### 2020.01.22
- The Customer Group InnerId has been replaced in the CustomerGroup Resource and Product Extend Resource ProductPrice data.

#### 2019.11.21
- [WebHook automation](api/07_webhook.md) documentation added.

#### 2019.11.20
- The call to the Product Extend Resource GET endpoint has been supplemented with a **productPrices** array, with which we can get the prices of the products broken down into customer groups. [documentation](../api/product_extend.md)

- If we want to create a new customer using Customer Resource and do not specify **customerGroup**, then the customer will be included in the default customer group.

#### 2019.10.24
- The **Payment Mode Resource** API endpoint has become available, with which we can retrieve the **installed** payment methods of the current store. Since the system does not support creating your own payment methods, this resource is completely readOnly. [documentation](../api/payment_mode.md)

#### 2019.10.21
- A new property, the "**productAttributeExtend**" list, containing the properties belonging to the product, was added to the **ProductExtend** resource. It's important to note that this is currently readonly, so you can't POST data to it. [documentation](../api/product_extend.md)

#### 2019.10.17
- Setting resource was supplemented with the title (**config_address**) and telephone number (**config_telephone**) of the store operator. [documentation](../api/setting.md)

#### 2019.10.14
- The API endpoint required for managing texts content has become available under the name Information Extend. [documentation](../api/information_extend.md)

#### 2019.09.23
- It caused a lot of problems for our customers when deleting individual main resources (Product, Order, Category, etc.) that although in the case of DELETE requests sent to them, the corresponding OuterID was deleted accordingly. However, if you had a related resource, e.g. in the case of a product, the product descriptions, so this also included a separate OuterID, unfortunately this was not deleted automatically. We solved this, so now you don't have to worry about the fact that developers will later run into a Name conflict when adding an OuterID.

#### 2019.09.10
- Added the Shipping Mode Extend resource, which can be used to perform operations related to shipping modes. [documentation](../api/shipping_mode_extend.md)
- The Shipping Mode Description resource has been added, which can be used to manage data related to shipping modes (Name, description, language). [documentation](../api/shipping_mode_description.md)
- The Shipping Lane resource has been added, which can be used to manage shipping lanes related to shipping methods. [documentation](../api/shipping_lane.md)
- Order resource was added with a shippingMode search parameter and a shippingMode property. [documentation](../api/order.md)
- Order Extend resource was added with a shippingMode search parameter and a shippingMode property. [documentation](../api/order_extend.md)

#### 2019.03.09
- The GeoZone resource has been added, which can be used to query which countries belong to which geographic zone. [documentation](../api/geo_zone.md)
- The Country resource has been supplemented with the geoZones property, with which we can get the geographic zones a given country belongs to. [documentation](../api/country.md)
- The OrderProduct resource has been supplemented with additional properties with which we can obtain the width (**width**), height (**height**), length (**length**) and weight (**weight**) of the ordered product. [documentation](../api/order_product.md)
- The ProductImage resource has been supplemented with a sortOrder property, which can be used to specify the order of product images. [documentation](../api/product_image.md)
- Domain Resource has become available. With this you can request the data of the domains registered for the given store: the language of the domains and whether they are primary domains or not. [documentation](../api/domain.md)

#### 2019.08.08
- Added **Json-based** communication with the API. In addition, the API documentation has been expanded with examples in **Json** format.

#### 2019.08.06
- The **allImages** property has become available in the Product and Product Extend resource, which is the main product image (mainImage) of the given room and the additional images (image1, image2,...) **full** url access, in cached form.

#### 2019.05.07
- An **updatedAtMin** filter was created for Customer and Customer Extend resources, which was modified after the specified date
  returns customers. [documentation](../api/customer_extend.md)

#### 2019.06.23
- **manufacturer** was included in the **Product Extend** resource expanded so that it does not need to be requested again
  [documentation](../api/product_extend.md)

#### 2019.06.21
- **API batch processor** has been memory optimized so that it can handle several requests at the same time.
  [documentation](./api/04_batch.md)

#### 2019.05.30
- **originalPrice** field added to Order resource [documentation](../api/order.md)

#### 2019.03.05
- **cost** field added to Product and ProductExtend resource [documentation](../api/product.md)

#### 2019.04.29
- With the help of the **full** parameter, when retrieving a list, the content of the list elements can be reached in one request,
  without having to start new requests. This is available for all resources.
  [documentation](./api/03_full_parameter.md)

#### 2019.01.02
- The telephone field was added to **Address resource** [documentation](../api/address.md)

#### 2018.12.05
- Create **CategoryExtend resource** [documentation](../api/category_extend.md)
- Creating **CustomerExtend resource** [documentation](../api/customer_extend.md)
- [What can extended Resources be used for?](./api/06_extend_resource.md)

#### 2018.25.09
- Creation of a **Webhook resource**, which can be used to create a webhook
  [documentation](../api/webhook.md)

#### 2018.09.13
- Preparation of **ScriptTag resource**, which can be used to place scripts on the front end via API
  [documentation](../api/script_tag.md)

#### 2017.10.20
- Create **ProductExtend resource** [documentation](../api/product_extend.md)
- Create **OrderExtend resource** [documentation](../api/order_extend.md)
- [What can extended Resources be used for?](./api/06_extend_resource.md)

#### 2017.07.27
- Handling of **Multilingualism** at the **Document Description** resource
  [documentation](../api/document_description.md)

#### 2017.06.30
- Return verbose **error messages** [documentation](./api/02_status_codes.md)
