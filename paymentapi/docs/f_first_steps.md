# Kezdeti lépések

Mivel a fizetési tervek létrehozásához API-t használunk, minden esetben a fejlesztőnek kell biztosítani egy felületet az alkalmazásán belül,
ahol a bolt tulajdonos elindíthatja a fizetési folyamatot. Ha pl. az Ismétlődő díjfizetést vesszük alapul, az alkalmazásunk tartalmazhat
egy olyan aloldalt, ahol különböző havi díjas csomagokat kínálhatunk. A csomag kiválasztása után, ennek megfelelően POST kérést küld
az alkalmazás a Payment API felé, hogy létrehozzon egy Ismétlődő díjfizetést.

Amire szükség lesz tehát:

- Vásárlás elindításáért felelős aloldal ahol az összes elérhető fizetés lehetőség megtekinthető. Itt ki kell listázni az adott csomagokhoz tartozó funkciókat is!

- notificationUrl: A fizetés közben történt eseményekről küldeni fog az API webhook-ot erre az Url-re. Ezen események kezelését is kivitelezni kell.

- failedUrl és successUrl: Ezekre az oldalakra lesz irányítva a bolt tulajdonos, ahol tájékoztatást kaphat a fizetés kimeneteléről.
