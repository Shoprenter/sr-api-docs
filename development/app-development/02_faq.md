# Frequently asked Questions

#### If I want to query the data of a resource, do I have to generate the base64 resource code?

This is the very first step that is often messed up when developing for the API. Do not generate IDs for yourself! Why? In the meantime, the resource identification may change in the API, or the generation of links may be completely transformed on our part. Never deal with URL decryption. Although you have to perform more queries this way, you will not depend on the resource identification functionality.

---

#### What is the correct solution if I still want to ask about a specific resource?

This depends on the situation, if you know specifically what you want to ask from the API, then you already have at least one resource ID. For products, for example, it is possible to query by **_sku_**. Another option is to use Outer ID. You can read more about how you can use search parameters for a specific resource or how to create Outer IDs in the documentation:

- [Product Resource](../../api/product.md)
- [Outer ID](../api/05_outer_id.md)

---

#### Should we also create the Outer ID in base64 format?

No, Outer ID can be any string. The point is that by storing this on your pages,
you could easily query resources, you don't have to worry about base64 resource identifiers.

---

#### When developing the app, do we need to ask the user for API authentication data?

No, it's completely automatic. When the app is installed, the code on the authentication URLs
will request the API authentication data for the current ShopRenter store. You have to get off here
save these and use this to access the store's API.

---

#### What is the use of client secret and client id if the API has separate authentication data?

ShopRenter uses Oauth standard authentication when communicating with apps.
This is to let ShopRenter know that the requests are coming from you,
and for you to make sure that ShopRenter requests really come from ShopRenter.

---

#### I should see our app in the Integrations menu item on the ShopRenter admin. Why can not I see?

It won't appear there. The applications can be found under the Applications menu item.

---

#### When creating a new Customer resource, which phone number format is accepted?

[https://github.com/googlei18n/libphonenumber](https://github.com/googlei18n/libphonenumber) package is used for
to manage phone numbers. It is worth studying and using the phone numbers
input, so the format problem can be avoided.

---

#### When creating a new Customer resource, how does ShopRenter handle passwords?

We use bcrypt to encode passwords, which means that you also have to enter them in the same way if you are a new customer.

---

#### If I work with orders and want to track newly received orders, do I always have to query all orders through the API?

Not necessary. It is possible to create a webhook, for example, for the "Order confirm" event, which can be specified
an endpoint. After triggering the event, the system will send the data of the new order to the URL you specified. More information at [WebHook Resource](../../api/webhook.md).

---

#### What is the difference between Extend resources and the full switch?

**Extend resource:** We can query and modify the related data of a specific resource individual with a single request. (For example, this way we can get the data of a product and the associated descriptions and not just a link to the individual resource containing the description of the product.)

**The full parameter:** When querying a resource individual collection, in the case of normal resources, we only see links to resource individuals in the resulting list. In order to reach the specific data, we have to make one more request to the server for each individual. In order to save on the number of necessary requests, we can request the data of individual resource individuals in the collection in 1 step with the `full=1` parameter.

---

#### We don't see our application in the iframe, what could be the problem?
We get a 'Refused to display' error in the DevTools console. Rendering is probably blocked by the 'X-Frame-Options' HTTP response header, as this tells the browser whether to allow the page to be rendered.
(More on this: [https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options](https://developer.mozilla.org/en-US/docs/ Web/HTTP/Headers/X-Frame-Options))

---

#### cUrl call not working with Batch API in terminal, what's the problem?
I send the POST data with the `-F` switch, but I get the error `40014 - 'POST is either empty or content length exceeds the limit of %s bytes``.
The `-F' switch sends the data as `multipart/form-data', so you don't need to include the 'content-type' header.
(More about this: [https://ec.haxx.se/http-postvspost.html](https://ec.haxx.se/http-postvspost.html))

---

#### After adding new text content (Information Extend resource), the javascript specified in the content does not run and does not even display an error, what could be the problem?
If the text content has a script tag, it is mandatory to enter the **type="text/javascript"** attribute. Example:

```js
<script type="text/javascript">
console.log('OK');
</script>
```
