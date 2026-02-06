# Access

The payment system is available through three ShopRenter API resources.
- POST _**https://<shop_name>.api.myshoprenter.hu/billing/oneTimeCharges**_
- POST _**https://<shop_name>.api.myshoprenter.hu/billing/recurringCharges**_
- DELETE _**https://<shop_name>.api.myshoprenter.hu/billing/recurringCharges/{recurring_charge_id}**_

On the Shoprenter Partner Dashboard, financial statements can be viewed and [Payment plans](../docs/h_plan.md) can be managed:
http://billing.shoprenter.hu/login

On the login interface, we can enter the dashboard of the application with the username/token pair received during the [previously mentioned registration](../docs/b_settings.md).

IMPORTANT: It is not necessary to reinstall the applications after the integration of the Payment API.
