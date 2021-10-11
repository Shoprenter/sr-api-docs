# Elérés

A fizetési rendszer három ShopRenter API resource-on keresztül érhető el.
- POST _**https://<shop_name>.api.myshoprenter.hu/billing/oneTimeCharges**_
- POST _**https://<shop_name>.api.myshoprenter.hu/billing/recurringCharges**_
- DELETE _**https://<shop_name>.api.myshoprenter.hu/billing/recurringCharges/{recurring_charge_id}**_

A Shoprenter Partner Dashboardon tekinthetőek meg a pénzügyi kimutatások és kezelhetőek a [Fizetési tervek](../docs/plan.md):
http://billing.shoprenter.hu/login

A login felületen, a már [korábban említett regisztráció](../docs/settings.md) során kapott felhasználó név/token párossal tudunk belépni az alkalmazáshoz tartozó dashboardra.

FONTOS: A Payment API integrációja után az alkalmazások újratelepítése nem szükséges.
