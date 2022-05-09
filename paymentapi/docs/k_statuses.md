# Státuszok

## Fizetések

A két fizetési típushoz tartoznak státuszok, melyek az adott fizetés életciklusának állapotáról adnak információt.
Bár az első sikeres tranzakció után a két típusnak eltérő az életpályája, a fizetések által felvehető állapotok nagyrészt megegyeznek

|Státusz                    |Leírás                                                                                                                                                                                                                                         |
|---------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|pending                    | Az újonnan létrehozott függőben lévő fizetés státusza.                                                                                                                                                                                        |
|accepted                   | A fizetés előtti állapot, amikor a bolt tulajdonos az 'approve oldalon' elfogadta a fizetési feltételeket.                                                                                                                                               |
|active                     | Sikeres fizetés utáni állapot.                                                                                                                                                                                                                 |
|declined                   | Elutasított fizetés. Ez megtörténhet a fizetést megerősítő oldalon vagy a tranzakciót lebonyolító szolgáltatás felületén.                                                                                                                      |
|expired                    | Az az Ismételt díjfizetés kerülhet ebbe a státuszba, amely véglegesen lejárt. (Nem kell tovább díjat levonni.)                                                                                                                             |
|frozen                     | Az Ismételt díjfizetés esetén jöhet elő, ha a tranzakció lebonyolítása közben olyan hiba lép fel, mely a bolt tulajdonos problémás banki adatai miatt következik be.                                                                                  |
|failed                     | A bankkártyás fizetést lebonyolító szolgáltatásban történt olyan hiba, amely nem feloldható, nem folytatható.                                                                                                                                  |
|cancelled                  | Ha az Ismételt díjfizetés FROZEN állapotú, 15 nap után - ha nem sikerült ACTIVE állapotra visszaállítani - úgy ebbe az állapotba kerül. Ezen felül, ha a fizetés direkt megszakításra kerül pl. alkalmazás törlésénél, úgy CANCELLED lesz a státusz.  |

## Bankkártya csere

Egy adott Ismétlődő díjfizetésen végrehajtott bankkártya csere életciklusának állapotáról adnak információt.
Hasonló állapotokat figyelhetünk meg, mint a normál fizetések esetén, hiszen technikailag minden csere egy bankkártyás fizetésnek felel meg.

|Státusz                    | Leírás                                                                                                                                                         |
|---------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
|pending                    | Az újonnan létrehozott, függőben lévő bannkártya csere státusza.                                                                                               |
|accepted                   | A fizetés előtti állapot, amikor a bolt tulajdonos a megerősítő elfogadta a cserét.                                                                            |
|active                     | Sikeres csere tranzakció utáni állapot. Ekkora a 10 Ft-os díj levonásra került és már az Ismétlődő díjfizetés a következő terhelésnél az új kártyáról történik |
|declined                   | Elutasított csere. Ez megtörténhet a fizetést megerősítő oldalon vagy a tranzakciót lebonyolító szolgáltatás felületén.                                        |
|failed                     | Vagy bankkártyás fizetést lebonyolító szolgáltatásban vagy a Payment API-ban történt olyan hiba, amely nem feloldható, nem folytatható.                        |

