# Alkalmazás törlése

Az alkalmazás törlése esetén, az adott boltban a rendszer automatikusan megszünteti az aktuálisan futó Ismétlődő díjfizetéseket.
Ezután, az alkalmazás regisztrációjánál megadott, uninstallUrl-re a ShopRenter küld egy **GET** HTTP kérést, ezzel jelezve a törlés tényét.

A GET kérés 4 query paraméter tartalmaz:
- shopName: a bolt neve, amelyben törölték az alkalmazást
- code: Generált hash
- timestamp: Kérés ideje
- hmac: Ellenőrző hash

A code, timestamp és a hmac paraméter a kérés ellenőrzésére szolgál. További információ a hmac ellenőrzéséről [itt](https://github.com/Shoprenter/developers/blob/master/app-development/GETTING_STARTED.md) található.
