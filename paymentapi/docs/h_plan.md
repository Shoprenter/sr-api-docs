# Fizetési terv az ismétlődő díjfizetéshez

Az Ismétlő díjfizetéshez elengedhetetlen, hogy fizetési tervekkel rendelkezzünk.
A fizetési terveinket a https://billing.shoprenter.hu/plans oldalon tudjuk szerkeszteni.
Bejelentkezés után listaszerűen láthatjuk a meglévő terveinket, illetve újakat adhatunk hozzá.

A fizetési terv árának és nevének megváltoztatása hatással van a már meglévő előfizetésekre is,
ha a két adat valamelyike módosul, a meglévő előfizetések következő díjfizetési időszaka már az új adatok alapján történik.

Fizetési terv lista oldal:

![Kép 1](../image/plan1.jpg)


Fizetési terv létrehozása:

![Kép 2](../image/plan2.jpg)

|Mező               |        Leírás      |
|---------------|--------------|
| Fizetési terv név| Itt lehet meg adni a terv nevét. Pl.: "Az alkalmazásom Bronze csomagja"|
| Fizetési ciklusok hossza | Itt adható meg, milyen időközönként vonódjon le az alkalmazás használatért kért összeg |
| Fizetési ciklusok száma | Itt adható meg, hogy hány alkalommal terheljük a bolt tulajdonos kártyáját|
| Fizetési terv nettó ára forintban | A nettó ár. Az ÁFA számítását lásd: [Számlakiállítás és ÁFA kalkuláció](../docs/price_calc.md) |

A lista oldalon, az **Azonosító** oszlopban lévő értékkel tudunk hivatkozni az egyes Fizetési tervekre,
amikor Ismétlődő díjfizetést akarunk létrehozni az API-n keresztül.

[Példa az Ismétlődő díjfizetésnél](../docs/recurring_charge.md)
