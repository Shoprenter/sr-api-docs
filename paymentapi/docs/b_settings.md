# Szükséges beállítások

A Payment API-t csak a Shoprenteres alkalmazások értékesítésére használható. Következésképpen, ahhoz, hogy hozzáférjünk és fizetéseket hozzunk létre, használatához szükséges a Shoprenter API hozzáférés.

A Payment API két legfontosabb végpontja a
- [boltnev].api.myshoprenter.hu/billing/recurringCharges
- [boltnev].api.myshoprenter.hu/billing/oneTimeCharges

Ezek elérésehez szükséges az adott alkalmazás telepítése során megszerzett username/password páros, amellyekkel bármely más Shoprenter API resource-ot is használjuk.

A Payment API használata előtt - ha már van alkalmazásunk - igényelnünk kell a partnersupport@shoprenter.hu
email címen keresztül egy felhasználó nevet és egy token-t. A ShopRenter munkatársai regisztrálják a kérést
és ezután használatba vehető az API. Ekkor egy felhasználó név és token párost készítünk el ami a ShopRenter
Partner Dashboard oldalra való belépést biztosítja.

A tokent a fent említett két, fizetés létrehozására szolgáló végpont hívásainál se header-ben, se pedig a POST kérés payload-jában nem kell elhelyezni!

A Shoprenter Partner Dashboardon tekinthetőek meg a pénzügyi kimutatások az alkalmazásra vonatkozóan és
 kezelhetőek a fizetési tervek is: https://billing.shoprenter.hu/login


**Fontos!** **A felhasználó név és jelszó alkalmazás specifikus!**
Tehát ha több alkalmazásunk van, minden alkalmazáshoz külön hozzáférést kell igényelni.


Az igényelt teszt bolt számlázási adatait minden esetben a megfelelő adatokkal töltsük ki, hiszen hiányos számlázási adatok esetén, a rendszer nem képes számlát kiállítani, így ezen beállítások hiánya a fizetések létrehozását is gátolja.
A legfontosabb adat az email cím, mivel teszt üzemmódban ide fogja kiküldeni a rendszer
a számlázási adat-összesítő teszt emailt. 

Minden ide vonatkozó adatot a teszt bolt admin felületén a "Fiókom" menüpontban tudnak módosítani. Link: https://valami.shoprenter.hu/admin/sales/account#/billingAddress

Ajánlott letárolni az elkészített fizetések azonosítóját, amelyek 
a
- [boltnev].api.myshoprenter.hu/billing/recurringCharges ( [Ismétlődő díjfizetés](../docs/recurring_charge.md) )
- [boltnev].api.myshoprenter.hu/billing/oneTimeCharges ( [Egyszeri díjfizetés](../docs/one_time_charge.md) )

végpontok válaszaiban érkeznek.

Az [Értesítési webhookokban](../docs/notifications.md)  érkező üzenetekből értesül a partner, hogy az adott fizetés, mely státuszba váltott át.

Pl.: Egy Ismétlődő díjfizetés esetén a terhelendő kártyával valamilyen probléma történt a soron következő terhelési kisérlet alatt, így a Payment API-tól érkezik egy webhook, melyben értesül a felhasználó, hogy a 2345-ös azonosítóval rendelkező Recurring Charge FROZEN állapotra váltott át.

Így ahhoz, hogy követni tudják az állapot változásokat, az alkalmazás fejlesztőknek szükséges saját adatbázist kialakítani a futó fizetések nyomonkövetéséhez.
