# Required settings

The Payment API can only be used to sell Shoprenter applications. Consequently, in order to access and create payments, you need access to the Shoprenter API.

The two most important endpoints of the Payment API are a
- [store name].api.myshoprenter.hu/billing/recurringCharges
- [store name].api.myshoprenter.hu/billing/oneTimeCharges

To access them, you need the username/password pair obtained during the installation of the given application, with which we also use any other Shoprenter API resource.

Before using the Payment API - if we already have an application - we must apply to partnersupport@shoprenter.hu
a username and a token via email address. ShopRenter employees register the request
and then the API can be used. Then we create a username and token pair, which is ShopRenter
Provides access to the Partner Dashboard page.

The token does not have to be placed either in the header or in the payload of the POST request when calling the two endpoints mentioned above for creating payments!

Financial statements for the application can be viewed on the Shoprenter Partner Dashboard and
payment plans can also be managed: https://billing.shoprenter.hu/login

*Important!** **The username and password are application specific!**
So if we have multiple apps, each app needs separate access.

In any case, fill in the billing data of the requested test store with the correct data, since in the case of incomplete billing data, the system cannot issue an invoice, so the lack of these settings also prevents the creation of payments.
The most important data is the email address, as the system will send it here in test mode
the billing data summary test email.

All relevant data can be modified in the "My Account" menu item on the test shop's admin interface. Link: https://Something.shoprenter.hu/admin/sales/account#/billingAddress

It is recommended to store the identifier of the prepared payments, which
the
- [shop name].api.myshoprenter.hu/billing/recurringCharges ( [Recurring charge payment](../docs/i_recurring_charge.md) )
- [shop name].api.myshoprenter.hu/billing/oneTimeCharges ( [One-time charge payment](../docs/g_one_time_charge.md) )

they arrive in endpoint responses.

From the messages received in [Notification webhooks](../docs/l_notifications.md), the partner is informed which status the given payment has changed to.

E.g.: In the case of a Recurring fee payment, some problem occurred with the card to be charged during the next charging attempt, so a webhook is received from the Payment API informing the user that the Recurring Charge with ID 2345 has switched to FROZEN status.

Thus, in order to be able to follow the status changes, the application developers need to create their own database to track ongoing payments.
