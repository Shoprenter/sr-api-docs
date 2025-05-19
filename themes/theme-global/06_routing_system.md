# Routing System

The routing system is closely integrated with the ShopRenter theme system. A route represents an identifier that determines which subpage we are currently on. This is crucial during theme development as it helps locate the appropriate theme file and modify the layout associated with that route.

## Routes in ShopRenter

<table>
<tr>
<th>route</th>
<th>description</th>
</tr>

<tr>
<td>
product/list
</td>
<td>
Product list/category page
</td>
</tr>

<tr>
<td>
product/manufacturers
</td>
<td>
All manufacturers list page 
</td>
</tr>

<tr>
<td>
filter
</td>
<td>
Product list page after filtering 
</td>
</tr>

<tr>
<td>
product/product
</td>
<td>
Product page
</td>
</tr>

<tr>
<td>
information/information_list
</td>
<td>
Content list page   
</td>
</tr>

<tr>
<td>
information/information
</td>
<td>
Content page 
</td>
</tr>

<tr>
<td>
information/contact
</td>
<td>
Contact page
</td>
</tr>

<tr>
<td>
information/personaldata
</td>
<td>
Manage personal data page 
</td>
</tr>

<tr>
<td>
information/sitemap
</td>
<td>
Sitemap page
</td>
</tr>

<tr>
<td>
information/style_guide
</td>
<td>
Style guide page
</td>
</tr>

<tr>
<td>
error/not_found
</td>
<td>
404 error page
</td>
</tr>

<tr>
<td>
account/account
</td>
<td>
User account page
</td>
</tr>

<tr>
<td>
account/edit
</td>
<td>
Edit account details page 
</td>
</tr>

<tr>
<td>
account/password
</td>
<td>
Password change page  
</td>
</tr>

<tr>
<td>
account/address
</td>
<td>
Modify address details page
</td>
</tr>

<tr>
<td>
account/waitinglist
</td>
<td>
Notification requests page
</td>
</tr>

<tr>
<td>
account/history
</td>
<td>
List of past orders page 
</td>
</tr>

<tr>
<td>
account/invoice
</td>
<td>
Detailed page of a past order
</td>
</tr>

<tr>
<td>
account/download
</td>
<td>
List of downloadable products page
</td>
</tr>

<tr>
<td>
account/newsletter
</td>
<td>
Newsletter subscription/unsubscription page 
</td>
</tr>

<tr>
<td>
account/registration_contribution
</td>
<td>
Accept/reject registration contribution
</td>
</tr>

<tr>
<td>
account/aaffiliate
</td>
<td>
Affiliate subpage
</td>
</tr>

<tr>
<td>
wishlist/wishlist
</td>
<td>
List of products in the wishlist
</td>
</tr>

</table>

The template files for login, registration, cart, and checkout pages are not accessible in ShopRenter; the route value for these pages will be empty.

## Where and How to Use Routes?

1. To determine the current page, you can retrieve it from the `ShopRenter.page.route` object in [ShopRenter.js](../../development/frontend-api/01_shoprenterjs_api.md#page).

2. Specify which layout corresponds to which route in the `settings.json` under the `layouts` property.

3. In the Theme File Editor, locate theme files based on the route. For example, the `product/product` route corresponds to `product/product.tpl`.

An exception is the `product/list` route, which has multiple associated theme files instead of just `product/list.tpl`:
  
<table>

<tr>
<td>
product/search.tpl
</td>
<td>
Search results
</td>
</tr>

<tr>
<td>
product/category.tpl
</td>
<td>
Product list/category page 
</td>
</tr>

<tr>
<td>
product/manufacturer.tpl
</td> 
<td>
Product list for a specific manufacturer 
</td>
</tr>

<tr>
<td>
product/productspecial.tpl
</td> 
<td>
Special offers list page 
</td>
</tr>

<tr>
<td>
product/latestlist.tpl
</td> 
<td>
Newest products list page 
</td>
</tr>

</table>
