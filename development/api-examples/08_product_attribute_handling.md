# Termék típusok, egyedi tulajdonságok és termékváltozatok kezelése

_Mielőtt belekezdünk a típusok és tulajdonságok API-n keresztül történő kezelésének a megismerkedésébe:_

**Ajánlatos** a Shoprenter Akadémián megtalálható [cikk](https://support.shoprenter.hu/hc/hu/articles/215106088-T%C3%ADpusok-tulajdons%C3%A1gok-sz%C5%B1r%C5%91k-matric%C3%A1k)
 áttanulmányozása. **Értenünk kell**, mi történik a kezelt bolt adminisztrációs felületén, hogy teljesen biztosak 
 legyünk a dolgunkban, mialatt API-n keresztül kezeljük ezt a részt!

A boltokban található termékek mindegyikének lehetnek olyan jellemzői,
mely meghatározzák a termék jellegét pl. színét, méretét stb. Ezeket a jellemzőket
a termék **egyedi tulajdonságának** hívjuk. Ezek segítségével a bolt tulajdonos képes megoldani pl.:
a termék jellemzőinek struktúrált megjelenítését a termék oldalon, illetve megkönnyíteni a Vásárlók számára 
a termékek szűrését.
 
A Shoprenter ezeket a tulajdonságokat
**termék típusokba** csoportosítja, aminek a célja, hogy egy tulajdonság-együttessel
leírhatóak legyenek a hasonló termékek közös vonásai.
Fontos megemlíteni, hogy egy egyedi terméktulajdonság több termék típus alá tartozhat.

A termék típusok és egyedi tulajdonságoknak a termékváltozatok képzésében is nagy szerepük van.
Egy egyedi tulajdonság mentén, képezhetjük egy termék több másik változatát, amelyek valójában önálló termékeknek számítanak.

A Shoprenter API segítségével képesek vagyunk kialakítani saját tulajdonság-rendszereinket.
A kialakítás folyamata **nagy odafigyelést igényel**, így egy példával fogjuk szemléltetni az építkezés egyes
fázisait.

1.-5. lépés: Termék típus és egyedi tulajdonságok kezelése, összekapcsolásuk termékekkel.

6.lépés (opcionális): A termékváltozatok kialakítása. Ha nincs szükség termékváltozatok képzésére, ezt a lépést
elhagyhatjuk.

**Fontos megjegyzés:** Lehetőség van egy termék egyedi tulajdonságinak egyszerűsített lekérésére
a [Product Extend Resource](../../api/product_extend.md) segítségével. 
A **productAttributeExtend** mező egy listát tartalmaz, amely a termékhez tartozó egyedi tulajdonságokat jeleníti meg.

#### Példa, amivel levezetjük a folyamatot:
Növényeket forgalmazó boltban, létre akarok hozni egy olyan nevű termék típust, hogy **Szobanövény**. 
A jövőben minden olyan növényhez hozzá akarom majd rendelni ezt a típust, amely jellegéből adódóan,
 szobanövénynek mondható.

Hogy a példa egyszerű legyen, és minden tulajdonság típust végig vegyünk,
 ez a típus 3 egyedi tulajdonságot fog tartalmazni:

 * Napsütötte órák száma - **Egész szám** típusú tulajdonság
 * Levelek formája - **Szöveges (választólista)** típusú tulajdonság: "Hegyes" és "Kerek" választható értékekkel
 * Latin megnevezés: **Tetszőleges** típusú tulajdonság
 
Ezután, egy létező termékhez hozzárendeljük az elkészült termék típusunkat, majd megnézzük,
hogyan adhatjuk meg a termék tulajdonságainak az értékeit.

## 1. lépés - Termék típus létrehozása

Egy egyszerű kéréssel létrehozzuk a termék típusunkat, amely összefogja majd egy Szobanövény
egyedi tulajdonságait.

_A változatképző paramétereket [itt](#6-lps---termkvltozatok-kialaktsa) tárgyaljuk._ 

#### Használt Resource

[Product Class](../../api/product_class.md)

#### Request

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/productClasses</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>
        Accept:application/json<br>
        Content-Type:application/json
    </td>
  </tr>
</table>

```json
{
    "name": "Szobanövény",
    "description": "Ez a szobanoveny típus leírása"
}
```

#### Response

```json
{
    "href": "http://shopname.api.shoprenter.hu/productClasses/cHJvZHVjdENsYXNzLXByb2R1Y3RfY2xhc3NfaWQ9MTQ=",
    "id": "cHJvZHVjdENsYXNzLXByb2R1Y3RfY2xhc3NfaWQ9MTQ=",
    "name": "Szobanövény",
    "description": "Ez a szobanoveny típus leírása",
    "firstVariantSelectType": "SELECT",
    "secondVariantSelectType": "SELECT",
    "firstVariantParameter": null,
    "secondVariantParameter": null,
    "productClassAttributeRelations": {
        "href": "http://shopname.api.shoprenter.hu/productClassAttributeRelations?productClassId=cHJvZHVjdENsYXNzLXByb2R1Y3RfY2xhc3NfaWQ9MTQ="
    }
}
```

## 2. lépés - Egyedi tulajdonságok létrehozása

Ebben a lépésben megismerkedünk 3 egyedi tulajdonság API Resource-ával:
 - Number Attribute Resource - Egész/Tört szám típusú tulajdonság
 - Text Attribute Resource - Tetszőleges típusú tulajdonság
 - List Attribute Resouce - Szöveges (választólista) típusú tulajdonság
 
Elkészítjük a 3 egyedi tulajdonságunkat, ezután mindhárom tulajdonsághoz rendelünk címkét az 
Attribute Description Resource-al.

### Number Attribute Resource
A Resource-al olyan tulajdonságokat vehetünk fel, melyek értékei egész vagy tört szám típusúak lehetnek.

A példát követve, nekünk egy egész típusú tulajdonságra lesz szükségünk, mely a napsütötte órák számát adja meg
egy termék esetén.

#### Használt Resource

[Number Attribute Resource](../../api/number_attribute.md)

#### Request

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/numberAttributes</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>
        Accept:application/json<br>
        Content-Type:application/json
    </td>
  </tr>
</table>


```json
{
    "type": "INTEGER",
    "name": "napsutotte_orak_szama",
    "priority": "NORMAL",
    "sortOrder": "1",
    "defaultValue": "4",
    "required": "1",
    "minValue": "1",
    "maxValue": "24"
}
```

#### Response

```json
{
    "href": "http://shopname.api.shoprenter.hu/numberAttributes/bnVtYmVyQXR0cmlidXRlLWF0dHJpYnV0ZV9pZD0xMw==",
    "id": "bnVtYmVyQXR0cmlidXRlLWF0dHJpYnV0ZV9pZD0xMw==",
    "type": "INTEGER",
    "name": "napsutotte_orak_szama",
    "priority": "NORMAL",
    "sortOrder": "1",
    "defaultValue": "10",
    "required": "1",
    "minValue": "1",
    "maxValue": "24",
    "showValueIfZero": null,
    "valuePrecision": null,
    "numberAttributeWidget": {
        "href": "http://shopname.api.shoprenter.hu/numberAttributeWidgets/bnVtYmVyQXR0cmlidXRlV2lkZ2V0LWF0dHJpYnV0ZV9pZD0xMw=="
    },
    "attributeDescriptions": {
        "href": "http://shopname.api.shoprenter.hu/attributeDescriptions?numberAttributeId=bnVtYmVyQXR0cmlidXRlLWF0dHJpYnV0ZV9pZD0xMw=="
    },
    "numberAttributeValues": {
        "href": "http://shopname.api.shoprenter.hu/numberAttributeValues?numberAttributeId=bnVtYmVyQXR0cmlidXRlLWF0dHJpYnV0ZV9pZD0xMw=="
    }
}
```
**Fontosabb mezők:**
- A **type** mező értéke INTEGER vagy FLOAT. Ez határozza meg, hogy a 
Resource egész vagy tört szám típusú tulajdonságot hozzon-e létre.
- A **priority** mezővel a láthatóságát NORMAL típusúra állítottuk, 
így csak a termékoldalon fog megjelenni.
- A **required** mező értéke 1, hogy annál a terméknél, ahol felhasználják a tulajdonságot, legyen kötelező a kitöltése.
- A **minValue** és **maxValue** mezőkkel behatároltuk az értéktartományt 24 órára.

### Text Attribute Resource 

A Resource-al olyan tulajdonságokat vehetünk fel, melyek értékei tetszőleges _string_ értékek lehetnek.

A példát követve, most létrehozunk egy tulajdonságot, amely a latin megnevezését fogja tartalmaznia a növénynek.

#### Használt Resource

[Text Attribute Resource](../../api/text_attribute.md)

#### Request

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/textAttributes</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>
        Accept:application/json<br>
        Content-Type:application/json
    </td>
  </tr>
</table>

```json
{
    "type": "TEXT",
    "name": "latin_megnevezes",
    "priority": "NORMAL",
    "sortOrder": "3",
    "required": "0",
    "textFieldType": "INPUT",
    "translateable": "0"
}
```

### Response

```json
{
    "href": "http://shopname.api.shoprenter.hu/textAttributes/dGV4dEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTU=",
    "id": "dGV4dEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTU=",
    "type": "TEXT",
    "name": "latin_megnevezes",
    "priority": "NORMAL",
    "sortOrder": "2",
    "required": "0",
    "textFieldType": "INPUT",
    "translateable": "0",
    "attributeDescriptions": {
        "href": "http://shopname.api.shoprenter.hu/attributeDescriptions?textAttributeId=dGV4dEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTU="
    },
    "textAttributeValues": {
        "href": "http://shopname.api.shoprenter.hu/textAttributeValues?textAttributeId=dGV4dEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTU="
    }
}
```

**Fontosabb mezők:**
- A **type** mező értéke TEXT. Kötelező megadni.
- A **priority** mezővel a láthatóságát NORMAL típusúra állítottuk, 
így csak a termékoldalon fog megjelenni.
- A **required** mező értéke 0, mert nem biztos, hogy minden növénynek tudni fogjuk a latin nevét, ezért nem is 
tesszük kötelezővé
- A **textFieldType** mezőnek INPUT értéket adtunk, így a termékszerkesztő oldalon, a tulajdonság értéket
 egy egysoros, szövegbeviteli mezőben tudjuk felvenni.
- A **translateable** mező mondja meg, hogy a megadható-e az érték több nyelven, vagy sem. Mivel nyelvtől független 
a tulajdonság értékünk (latin nyelvű), 0 értéket kap.

### List Attribute Resource 

A Resource-al olyan tulajdonságokat vehetünk fel, melyeknek értékeit egy előre meghatározott listából választhatjuk ki.

A taglalt egyedi tulajdonság elkészítése komplexebb, mint az előző két tulajdonság esetén tapasztaltuk:
- Létre kell hoznunk az tulajdonságot List Attribute Resource-al.
- Meg kell adnunk, hány darab értéket vehet fel a tulajdonság List Attribute Value Resource-al. Tehát annyi 
List Attribute Value Resource egyedet kell létrehoznunk, amennyi értéket szeretnénk választhatóvá tenni.
- Amikor az értékeket egyesével létrehoztuk, a List Attribute Value Description Resource-al megadjuk, hogy egyes 
nyelvek esetén, mi lesz a konkrét érték.

A példát követve, most létrehozunk egy tulajdonságot, amely a növény leveleinek a formáját fogja megadni.
A két választható érték: "Hegyes", "Kerek".

#### Használt Resource

- [List Attribute Resource](../../api/list_attribute.md)
- [List Attribute Value Resource](../../api/list_attribute_value.md)
- [List Attribute Value Description Resource](../../api/list_attribute_value_description.md)

#### Request - List Attribute Resource

Az előző példákhoz hasonlóan, először magát a tulajdonságot hozzuk létre.

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/listAttributes</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>
        Accept:application/json<br>
        Content-Type:application/json
    </td>
  </tr>
</table>

```json
{
    "type": "LIST",
    "name": "levelek_formaja",
    "priority": "NORMAL",
    "sortOrder": "2",
    "required": "1",
    "presentation": "TEXT"
}
```

### Response

```json
{
    "href": "http://shopname.api.shoprenter.hu/listAttributes/bGlzdEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTY=",
        "id": "bGlzdEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTY=",
        "type": "LIST",
        "name": "levelek_formaja",
        "priority": "NORMAL",
        "sortOrder": "2",
        "required": "1",
        "presentation": "TEXT",
        "listAttributeWidget": {
            "href": "http://shopname.api.shoprenter.hu/listAttributeWidgets/bGlzdEF0dHJpYnV0ZVdpZGdldC1hdHRyaWJ1dGVfaWQ9MTY="
        },
        "defaultListAttributeValue": null,
        "attributeDescriptions": {
            "href": "http://shopname.api.shoprenter.hu/attributeDescriptions?listAttributeId=bGlzdEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTY="
        },
        "listAttributeValues": {
            "href": "http://shopname.api.shoprenter.hu/listAttributeValues?listAttributeId=bGlzdEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTY="
        }
}
```

Az elkészült tulajdonság resource id-ját megjegyezzük: **bGlzdEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTY=**
Szükségünk lesz rá a következő lépésben, hogy értékekkel töltsük fel a választó listás tulajdonságunkat.

**Fontosabb mezők:**
- A **type** mező értéke LIST. Kötelező megadni.
- A **priority** mezővel a láthatóságát NORMAL típusúra állítottuk, 
így csak a termékoldalon fog megjelenni.
- A **presentation** mezőnek akkor van szerepe, ha ezt a tulajdonságot termékváltozat képzésére használjuk.
A termékoldalon megjelenő termékváltozat választó típusát adja meg. Jelen esetben TEXT lesz, tehát szöveges
választólista jelenne meg.

#### Request - List Attribute Value Resource

Két értéket szeretnénk a kiválaszthatóvá tenni választólistában: "Hegyes" és "Kerek".
Ahogy említettem, a Resource-al csak létrehozunk két "üres" értéket, amiknek még konkrétan nem adjuk meg,
melyik fogja a "Hegyes" és melyik a "Kerek" értéket reprezentálni.

Az előző lépésben létrehozott List Attribute tulajdonság resource id-ját fogjuk használni, hogy hozzákapcsoljuk
a két új értéket a "Levelek formája" egyedi tulajdonsághoz.

**A következő requestet ismételjük meg kétszer:**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/listAttributeValues</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>
        Accept:application/json<br>
        Content-Type:application/json
    </td>
  </tr>
</table>

```json
{
    "listAttribute": {
        "id": "bGlzdEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTY="
    }
}
```

**A két request Response-a:**

```json
{
    "href": "http://shopname.api.shoprenter.hu/listAttributeValues/bGlzdEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNiZ2YWx1ZV9pZD0x",
    "id": "bGlzdEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNiZ2YWx1ZV9pZD0x",
    "listAttribute": {
        "href": "http://shopname.api.shoprenter.hu/listAttributes/bGlzdEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTY="
    },
    "listAttributeValueDescriptions": {
        "href": "http://shopname.api.shoprenter.hu/listAttributeValueDescriptions?listAttributeValueId=bGlzdEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNiZ2YWx1ZV9pZD0x"
    }
}
```

```json
{
    "href": "http://shopname.api.shoprenter.hu/listAttributeValues/bGlzdEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNiZ2YWx1ZV9pZD0y",
    "id": "bGlzdEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNiZ2YWx1ZV9pZD0y",
    "listAttribute": {
        "href": "http://shopname.api.shoprenter.hu/listAttributes/bGlzdEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTY="
    },
    "listAttributeValueDescriptions": {
        "href": "http://shopname.api.shoprenter.hu/listAttributeValueDescriptions?listAttributeValueId=bGlzdEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNiZ2YWx1ZV9pZD0y"
    }
}
```

Megjegyezzük a két, létrehozott érték resource id-ját:
- **bGlzdEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNiZ2YWx1ZV9pZD0x**
- **bGlzdEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNiZ2YWx1ZV9pZD0y**

A következő lépésben fogjuk felhasználni őket, hogy konkretizáljuk a két értéket.

#### Request - List Attribute Value Description Resource

A választó lista konkrét értékeit kell megadnunk. Az egyszerűség kedvéért csak egy nyelvvel mutatjuk meg a 
folyamatot.

Az előző lépésben megjegyzett két List Attribute Value resource id-hoz felveszem, hogy, **magyar** nyelven, melyik legyen a "Hegyes" és melyik legyen
a "Kerek" érték.

**A "Hegyes" érték - Request:**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/listAttributeValueDescription</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>
        Accept:application/json<br>
        Content-Type:application/json
    </td>
  </tr>
</table>

```json
{
    "name": "Hegyes",
    "language": {
        "id": "bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ=="
    },
    "listAttributeValue": {
        "id": "bGlzdEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNiZ2YWx1ZV9pZD0y"
    }
}
```

**Response:**

```json
{
    "href": "http://shopname.api.shoprenter.hu/listAttributeValueDescriptions/bGlzdEF0dHJpYnV0ZVZhbHVlRGVzY3JpcHRpb24tbGFuZ3VhZ2VfaWQ9MSZhdHRyaWJ1dGVfaWQ9MTYmdmFsdWVfaWQ9Mg==",
    "id": "bGlzdEF0dHJpYnV0ZVZhbHVlRGVzY3JpcHRpb24tbGFuZ3VhZ2VfaWQ9MSZhdHRyaWJ1dGVfaWQ9MTYmdmFsdWVfaWQ9Mg==",
    "name": "Hegyes",
    "language": {
        "href": "http://shopname.api.shoprenter.hu/languages/bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ=="
    },
    "listAttributeValue": {
        "href": "http://shopname.api.shoprenter.hu/listAttributeValues/bGlzdEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNiZ2YWx1ZV9pZD0y"
    }
}
```

**A "Kerek" érték - Request:**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/listAttributeValueDescription</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>
        Accept:application/json<br>
        Content-Type:application/json
    </td>
  </tr>
</table>

```json
{
    "name": "Kerek",
    "language": {
        "id": "bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ=="
    },
    "listAttributeValue": {
        "id": "bGlzdEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNiZ2YWx1ZV9pZD0x"
    }
}
```

**Response:**

```json
{
    "href": "http://shopname.api.shoprenter.hu/listAttributeValueDescriptions/bGlzdEF0dHJpYnV0ZVZhbHVlRGVzY3JpcHRpb24tbGFuZ3VhZ2VfaWQ9MSZhdHRyaWJ1dGVfaWQ9MTYmdmFsdWVfaWQ9Mg==",
    "id": "bGlzdEF0dHJpYnV0ZVZhbHVlRGVzY3JpcHRpb24tbGFuZ3VhZ2VfaWQ9MSZhdHRyaWJ1dGVfaWQ9MTYmdmFsdWVfaWQ9Mg==",
    "name": "Kerek",
    "language": {
        "href": "http://shopname.api.shoprenter.hu/languages/bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ=="
    },
    "listAttributeValue": {
        "href": "http://shopname.api.shoprenter.hu/listAttributeValues/bGlzdEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNiZ2YWx1ZV9pZD0y"
    }
}
```

Természetesen, ha szeretnénk, hogy a bolt aktuális nyelvi beállításaihoz igazodva jelenjen meg az érték termék oldalon,
pl.: angol nyelven a "Hegyes" úgy, hogy "Sharp", akkor ugyan ezt a lépést kell megismételnünk, az angol nyelv resource id-jával
és a **name** mezőnek adott "Sharp" értékkel, például.

### Attribute Description Resource

Mindhárom egyedi tulajdonságot fel kell címkéznünk, hogy mind admin felületen, mind pedig a boltban látható legyen adott
nyelven a tulajonság neve.

Természetesen, a címkék több nyelven megadhatóak. Egy példát mutatunk a Napsütötte órák száma tulajdonság,
 magyar nyelvű felcímkézésére.
Ugyanígy járjunk el a másik két tulajdonság esetén is.

Amire szükségünk lesz:
 - A Napsütötte órák száma tulajdonság resource id-jára: **bnVtYmVyQXR0cmlidXRlLWF0dHJpYnV0ZV9pZD0xMw==**
 - A magyar nyelv resource id-ja: **bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ==**

#### Használt Resoruce

[Attribute Description Resource](../../api/attribute_description.md)

#### Request

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/attributeDescriptions</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>
        Accept:application/json<br>
        Content-Type:application/json
    </td>
  </tr>
</table>

```json
{
    "name": "Napsütötte órák száma",
    "description": "Megmondja, naponta, hány óra szükséges a növénynek napfényben töltenie",
    "attribute": {
        "id": "bnVtYmVyQXR0cmlidXRlLWF0dHJpYnV0ZV9pZD0xMw=="
    },
    "language": {
        "id": "bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ=="
    }
}
```

#### Response

```json
{
    "href": "http://shopname.api.shoprenter.hu/attributeDescriptions/YXR0cmlidXRlRGVzY3JpcHRpb24tYXR0cmlidXRlX2lkPTcmbGFuZ3VhZ2VfaWQ9NA==",
    "id": "YXR0cmlidXRlRGVzY3JpcHRpb24tYXR0cmlidXRlX2lkPTcmbGFuZ3VhZ2VfaWQ9NA==",
    "name": "Napsütötte órák száma",
    "description": "Megmondja, naponta, hány óra szükséges a növénynek napfényben töltenie",
    "attribute": {
        "href": "http://shopname.api.shoprenter.hu/numberAttributes/bnVtYmVyQXR0cmlidXRlLWF0dHJpYnV0ZV9pZD0xMw=="
    },
    "language": {
        "href": "http://shopname.api.shoprenter.hu/languages/bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9NA=="
    }
}
```

## 3. lépés - Egyedi tulajdonságok hozzárendelése termék típushoz

Most, hogy elkészült a 3 egyedi tulajdonságunk, a következő lépésben hozzákapcsoljuk őket az első lépésben létrehozott,
Szobanövény termék típushoz.

Szükségünk lesz a 3 egyedi tulajdonság resource id-jára:
- Napsütötte órák száma - Number Attribute Resource: **bnVtYmVyQXR0cmlidXRlLWF0dHJpYnV0ZV9pZD0xMw==**
- Latin megnevezés - Text Attribute Resource: **dGV4dEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTU=**
- Levelek formája - List Attribute Resource : b**GlzdEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTY=**

Illetve, természetesen a Szobanövény termék típus resource id-jára: cHJvZHVjdENsYXNzLXByb2R1Y3RfY2xhc3NfaWQ9MTQ=

#### Használt resource

[Product Class Attribute Relation Resource](../../api/product_class_attribute_relation.md)

#### Request

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/productClassAttributeRelations</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>
        Accept:application/json<br>
        Content-Type:application/json
    </td>
  </tr>
</table>

```json
{
    "productClass": {
        "id": "cHJvZHVjdENsYXNzLXByb2R1Y3RfY2xhc3NfaWQ9MTQ="
    },
    "attribute": {
        "id": "bnVtYmVyQXR0cmlidXRlLWF0dHJpYnV0ZV9pZD0xMw=="
    }
}
```

#### Response

```json
{
    "href": "http://shopname.api.shoprenter.hu/productClassAttributeRelations/cHJvZHVjdENsYXNzQXR0cmlidXRlUmVsYXRpb24tcHJvZHVjdF9jbGFzc19pZD0xNCZhdHRyaWJ1dGVfaWQ9MTM=",
    "id": "cHJvZHVjdENsYXNzQXR0cmlidXRlUmVsYXRpb24tcHJvZHVjdF9jbGFzc19pZD0xNCZhdHRyaWJ1dGVfaWQ9MTM=",
    "productClass": {
        "href": "http://shopname.api.shoprenter.hu/productClasses/cHJvZHVjdENsYXNzLXByb2R1Y3RfY2xhc3NfaWQ9MTQ="
    },
    "attribute": {
        "href": "http://shopname.api.shoprenter.hu/numberAttributes/bnVtYmVyQXR0cmlidXRlLWF0dHJpYnV0ZV9pZD0xMw=="
    }
}
```

A példa a "Napsütötte órák száma" tulajdonságot kapcsolta a "Szobanövény" termék típushoz.
Természetesen, **a két másik tulajdonsággal is hasonlóképpen járunk el**.

Ha mindhárom tulajdonság kapcsolódik a típushoz, a Szobanövény termék típust beállíthatjuk bármelyik termékhez.

## 4. lépés - Termék típus hozzárendelése egy termékhez

Most, hogy elkészült a Szobanövény termék típus és hozzá az egyedi tulajdonságai, következő lépésben megnézzük,
hogyan lehet egy termékhez hozzárendelni.

Ehhez szükségünk lesz a Szobanövény termék típus resource id-jára: **cHJvZHVjdENsYXNzLXByb2R1Y3RfY2xhc3NfaWQ9MTQ**=.

A következőkben, egy létező termékhez rendeljük hozzá a termék típust. Tehát, Egy PUT kéréssel módosítjuk a productClass
mezőjét. Természetesen, új termék létrehozásánál is hozzárendelhetjük a termék típust.

#### Használt resource

[Product Extend Resource](../../api/product_extend.md)

#### Request

<table>
  <tr>
    <td><b>method:</b></td>
    <td>PUT</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/productExtend/cHJvZHVjdC1wcm9kdWN0X2lkPTYxNA==</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>
        Accept:application/json<br>
        Content-Type:application/json
    </td>
  </tr>
</table>

```json
{
    "productClass": {
        "id": "cHJvZHVjdENsYXNzLXByb2R1Y3RfY2xhc3NfaWQ9MTQ="
    }
}
```

#### Response

```json
{
    "href": "http://shopname.api.shoprenter.hu/productExtend/cHJvZHVjdC1wcm9kdWN0X2lkPTYxNA==",
    "id": "cHJvZHVjdC1wcm9kdWN0X2lkPTYxNA==",
...
 "productClass": {
        "href": "http://shopname.api.shoprenter.hu/productClasses/cHJvZHVjdENsYXNzLXByb2R1Y3RfY2xhc3NfaWQ9MTQ="
    },
...

}
```

Most már minden készen áll, hogy valóban használni tudjuk az egyedi terméktulajdonságainkat.

## 5. lépés - Egyedi tulajdonság értékek felvétele

Ebben a lépésben nyer értelmet az eddig elkészített termék típus és egyedi tulajdonságok.
Az előző lépésben, egy tetszőleges termékhez megadtuk a Szobanövény termék típust. Nevezzük most ezt a terméket
Szobanövény 1-nek.

Ebben a lépésben megadjuk, hogy a Szobanövény 1 termék esetén, a Szobanövény termék típus által összefogott Napsütötte órák száma, 
Levelek formája és Latin megnevezés egyedi tulajdonságok, milyen aktuális értéket kapjanak.

Tegyük fel, hogy szeretnénk a **Napsütötte órák számát** (Number Attribute) 3-ra, a **Levelek formáját** (List Attribute) 
"Kerek"-re és a **Latin megnevezést** (Text Attribute) pedig "Lorem ipsum"-ra állítani.

Úgy kell elképzelni, mintha egy formot töltenénk ki API-n keresztül: két beviteli mezőbe beírom a kívánt értékeket 
(Number Attribute, Text Attribute), illetve egy listából kiválasztom a kívánt értéket (List Attribute).

A 3 különböző terméktulajdonság aktuális értékeit egymástól eltérő módon tudjuk beállítani a termékhez.

### Napsütötte órák száma (Number Attribute)

Az érték megadása ennél a Resource-nál a legegyszerűbb.

Amire szükségünk van:
- Napsütötte órák száma tulajdonság resource id-jára: **bnVtYmVyQXR0cmlidXRlLWF0dHJpYnV0ZV9pZD0xMw==**
- A termék resource id-jára: **cHJvZHVjdC1wcm9kdWN0X2lkPTYxNA==**

#### Használt Resouce

[Number Attribute Value](../../api/number_attribute_value.md)

#### Request
<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/numberAttributeValues</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>
        Accept:application/json<br>
        Content-Type:application/json
    </td>
  </tr>
</table>

```json
{
    "value": "3",
    "numberAttribute": {
        "id": "bnVtYmVyQXR0cmlidXRlLWF0dHJpYnV0ZV9pZD0xMw=="
    },
    "product": {
        "id": "cHJvZHVjdC1wcm9kdWN0X2lkPTYxNA=="
    }
}
```

#### Response

```json
{
    "href": "http://shopname.api.shoprenter.hu/numberAttributeValues/bnVtYmVyQXR0cmlidXRlVmFsdWUtYXR0cmlidXRlX2lkPTEzJnByb2R1Y3RfaWQ9NjE0",
    "id": "bnVtYmVyQXR0cmlidXRlVmFsdWUtYXR0cmlidXRlX2lkPTEzJnByb2R1Y3RfaWQ9NjE0",
    "value": "3",
    "numberAttribute": {
        "href": "http://shopname.api.shoprenter.hu/numberAttributes/bnVtYmVyQXR0cmlidXRlLWF0dHJpYnV0ZV9pZD0xMw=="
    },
    "product": {
        "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTYxNA=="
    }
}
```

### Latin megnevezés (Text Attribute)

Az értékadás nagyon hasonlít ahhoz, amikor a Szöveg (választólista) típusú tulajdonságot töltöttük fel értékekkel.
Itt is először az értékadás tényét kell "jelezni" a Text Attribute Value Resource segítségével, majd konkretizálni
a Text Attribute Value Description Resource-al, hogy egyes nyelveken, mi lesz a tényleges érték.

Amire szükségünk van:
- Latin megnevezés tulajdonság resource id-jára: **dGV4dEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTU=**
- A termék resource id-jára: **cHJvZHVjdC1wcm9kdWN0X2lkPTYxNA==**


#### Használt Resouce

 - [Text Attribute Value Resource](../../api/text_attribute_value.md)
 - [Text Attribute Value Description Resource](../../api/text_attribute_value_description.md)

#### Request - Text Attribute Value Resource

<table>
  <tr>
    <td><b>method:</b></td>
    <td>PUT</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/textAttributeValues</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>
        Accept:application/json<br>
        Content-Type:application/json
    </td>
  </tr>
</table>

```json
{
    "textAttribute": {
        "id": "dGV4dEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTU="
    },
    "product": {
        "id": "cHJvZHVjdC1wcm9kdWN0X2lkPTYxNA=="
    }
}
```

#### Response

```json
{
    "href": "http://shopname.api.shoprenter.hu/textAttributeValues/dGV4dEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNSZwcm9kdWN0X2lkPTYxNA==",
    "id": "dGV4dEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNSZwcm9kdWN0X2lkPTYxNA==",
    "textAttribute": {
        "href": "http://shopname.api.shoprenter.hu/textAttributes/dGV4dEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTU="
    },
    "product": {
        "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTYxNA=="
    },
    "textAttributeValueDescriptions": {
        "href": "http://shopname.api.shoprenter.hu/textAttributeValueDescriptions?textAttributeValueId=dGV4dEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNSZwcm9kdWN0X2lkPTYxNA=="
    }
}
```

#### Request - Text Attribute Value Description Resource

Most, hogy elkészült az "üres" érték a termékhez, meg kell adnunk az értékhez tartozó szöveges tartalmat.

A kérdés jogos: Miért kell külön Resource a tényleges érték megadásához? A válasz az, hogy a tulajdonság 
értéke többnyelvesíthető.
Tehát egy érték, más-más nyelven, másképpen reprezentálódik. Ezért, ha Tetszőleges típusú tulajdonságot úgy hozom létre,
hogy többnyelvűsíthető legyen, akkor nyelvenként fel kellene vinnünk az érték reprezentációit.

Amire szükségünk lesz, az az előbb készített Text Attribute Value egyed resource id-ja: **dGV4dEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNSZwcm9kdWN0X2lkPTYxNA==**

Mivel megadtuk, hogy a **latin_megnevezes** nevű egyedi tulajdonság egynyelvű lesz, így a **language** mezőt **null** értékre állítjuk.


<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/textAttributeValueDescriptions</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>
        Accept:application/json<br>
        Content-Type:application/json
    </td>
  </tr>
</table>

```json
{
    "name": "Lorem ipsum",
    "language": null,
    "textAttributeValue": {
        "id": "dGV4dEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNSZwcm9kdWN0X2lkPTYxNA=="
    }
}
```

#### Response - Text Attribute Value Description Resource

```json
{
    "href": "http://shopname.api.shoprenter.hu/textAttributeValues/dGV4dEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNSZwcm9kdWN0X2lkPTYxNA==",
    "id": "dGV4dEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNSZwcm9kdWN0X2lkPTYxNA==",
    "textAttribute": {
        "href": "http://shopname.api.shoprenter.hu/textAttributes/dGV4dEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTU="
    },
    "product": {
        "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTYxNA=="
    },
    "textAttributeValueDescriptions": {
        "href": "http://shopname.api.shoprenter.hu/textAttributeValueDescriptions?textAttributeValueId=dGV4dEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNSZwcm9kdWN0X2lkPTYxNA=="
    }
}
```

### Levelek formája (List Attribute)

A kérdéses tulajdonság egy választó lista, amiből a "Kerek" értéket szeretnénk kiválasztani a termékünkhöz. 
Tehát, ez esetben, a kiválasztott értéket és a terméket kell összekapcsolnunk.

Amire szükségünk van:
- Levelek formája tulajdonság azon értékének (List Attribute Value) resource id-ja, amelynek magyar megfelelője "Kerek": bGlzdEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNiZ2YWx1ZV9pZD0x
- A termék resource id-ja: **cHJvZHVjdC1wcm9kdWN0X2lkPTYxNA==**

#### Használt Resouce

[Product List Attribute Value Relation Resource](../../api/product_list_attribute_value_relation.md)

#### Request

<table>
  <tr>
    <td><b>method:</b></td>
    <td>PUT</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/productListAttributeValueRelations</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>
        Accept:application/json<br>
        Content-Type:application/json
    </td>
  </tr>
</table>

```json
{
    "product": {
        "id": "cHJvZHVjdC1wcm9kdWN0X2lkPTYxNA=="
    },
    "listAttributeValue": {
        "id": "bGlzdEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNiZ2YWx1ZV9pZD0x"
    }
}
```

#### Response

```json
{
    "href": "http://shopname.api.shoprenter.hu/productListAttributeValueRelations/cHJvZHVjdExpc3RBdHRyaWJ1dGVWYWx1ZVJlbGF0aW9uLXByb2R1Y3RfaWQ9NjE0JmF0dHJpYnV0ZV9pZD0xNiZ2YWx1ZV9pZD0y",
    "id": "cHJvZHVjdExpc3RBdHRyaWJ1dGVWYWx1ZVJlbGF0aW9uLXByb2R1Y3RfaWQ9NjE0JmF0dHJpYnV0ZV9pZD0xNiZ2YWx1ZV9pZD0y",
    "product": {
        "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTYxNA=="
    },
    "listAttributeValue": {
        "href": "http://shopname.api.shoprenter.hu/listAttributeValues/bGlzdEF0dHJpYnV0ZVZhbHVlLWF0dHJpYnV0ZV9pZD0xNiZ2YWx1ZV9pZD0y"
    }
}
```

## 6. lépés - Termékváltozatok kialakítása

Gondoljuk tovább a példánkat. Tegyük fel, hogy van két növényünk, amely ugyanazon növényfajba tartoznak, viszont 
leveleiknek a formája eltérő. A két növénynek különböző cikkszáma, ára, raktárkészlete van, 
de nem akarjuk külön termékoldalon kínálni őket. Szeretnénk, hogy a Vásárló egy termékoldalról tudjon navigálni
az összes változatra.

Az előző lépésekben elkészített **Levelek formája** egyedi tulajdonsággal, és a szülő-gyerek viszonnyal, 
egyszerűen megtehetjük ezt.

### változatképző paraméterek beállítása termék típushoz

A 2. lépésben létrehozott Szobanövény termék típust fogjuk módosítani úgy, hogy beállítjuk az első változatképző paraméterének
a Levelek formája egyedi tulajdonságot. Tehát a Szobanövény tipusba tartozó termékek Levelek formája tulajdonság értékének
a különbözősége határozza majd meg a változatainkat.

Amire szükségünk van:
Szobanövény termék típus resource id-ja: **cHJvZHVjdENsYXNzLXByb2R1Y3RfY2xhc3NfaWQ9MTQ=**
A "levelek formája" egyedi tulajdonság resource id-jára: **bGlzdEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTY=**

#### Használt Resource
[Porduct Class Resource](../../api/product_class.md)

#### Request

<table>
  <tr>
    <td><b>method:</b></td>
    <td>PUT</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/productClasses/cHJvZHVjdENsYXNzLXByb2R1Y3RfY2xhc3NfaWQ9MTQ</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>
        Accept:application/json<br>
        Content-Type:application/json
    </td>
  </tr>
</table>

```json
{
   "firstVariantParameter": {
        "id": "bGlzdEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTY="
    }
}
```

#### Response

```json
{
    "href": "http://shopname.api.shoprenter.hu/productClasses/cHJvZHVjdENsYXNzLXByb2R1Y3RfY2xhc3NfaWQ9MTQ=",
    "id": "cHJvZHVjdENsYXNzLXByb2R1Y3RfY2xhc3NfaWQ9MTQ=",
    "name": "Szobanövény",
    "description": "Ez a szobanoveny típus leírása",
    "firstVariantSelectType": "SELECT",
    "secondVariantSelectType": "SELECT",
    "firstVariantParameter": {
        "href": "http://shopname.api.shoprenter.hu/listAttributes/bGlzdEF0dHJpYnV0ZS1hdHRyaWJ1dGVfaWQ9MTY="
    },
    "secondVariantParameter": null,
    "productClassAttributeRelations": {
        "href": "http://shopname.api.shoprenter.hu/productClassAttributeRelations?productClassId=cHJvZHVjdENsYXNzLXByb2R1Y3RfY2xhc3NfaWQ9MTQ="
    }
}
```

**Fontosabb mezők:**
A **firstVariantParameter** mezőben adjuk az egyedi tulajdonság resource id-ját. **Ez csak a típus által összefogott tulajdonságokból származhat!**
A **firstVariantSelectType** határozza meg, hogy termékoldalon hogyan fog megjelenni termékváltozat választó select mező

**Megjegyzés:** Lehetőség van második változatképző paraméter megadására is. Ilyenkor két tényező határozza meg a 
különböző változatokat.

### Szülő-gyerek viszony kialakítása

Az utolsó lépés a szülő-gyerek viszony kialakítása. Ezzel a speciális kapcsolattal tudjuk a változatokat egy csokorba
szedni.
A levelek formája tulajdonságnak két értéke van: "Hegyes" és "Kerek"

Két lehetőségünk van:
- Létrehozunk egy terméket, amelyet kijelölünk szülőnek és további kettőt, amely a két gyerek termék lesz.
- Lérehozunk egy terméket, amelynek a Levelek formája tulajdonsága "Hegyes" értéket vesz fel. Majd létrehozunk egy másik
terméket, amelyet gyerek terméknek nevezünk ki és a Levelek formája tulajdonsága "Kerek" értéket vesz fel.

A példa egyszerűsége végett a második lehetőséget mutatjuk meg.
A beállítás API-on keresztül nagyon egyszerű: végig kell mennünk az összes gyerekterméken és a Product Extend Resource-al
a parentProduct mezőben megadjuk annak a terméknek a resource id-ját, amelyet szülőnek akarunk nyílvánitani.

Tegyük fel, hogy létezik két termékünk és előre beállítottuk a Levelek formája tulajdonságait:
 - Szobanövény 1 - "Hegyes"
 - Szobanövény 2 - "Kerek"
 
 Természetesen, mindkettőnek a termék típusa Szobanövény.

 Képezzünk úgy egy termékváltozatot, hogy:
 - Szobanövény 1 lesz a Szülő termék  | Product resource id: **cHJvZHVjdC1wcm9kdWN0X2lkPTYxMg==**
 - Szobanövény 2 lesz a Gyerek termék  | Product resource id: **cHJvZHVjdC1wcm9kdWN0X2lkPTYxNA==**
 
 **Tehát, a Szobanövény 2 terméknek beállítom a parentProduct mezőjébe a Szobanövény 1 resource id-ját!**
 
 #### Request
 
<table>
  <tr>
    <td><b>method:</b></td>
    <td>PUT</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/productExtend/cHJvZHVjdC1wcm9kdWN0X2lkPTYxNA==</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>
        Accept:application/json<br>
        Content-Type:application/json
    </td>
  </tr>
</table>

```json
{
  "parentProduct": {
      "id": "cHJvZHVjdC1wcm9kdWN0X2lkPTYxMg=="
  } 
}
```

#### Response

```json
{
    "href": "http://shopname.api.shoprenter.hu/productExtend/cHJvZHVjdC1wcm9kdWN0X2lkPTYxNA==",
    "id": "cHJvZHVjdC1wcm9kdWN0X2lkPTYxNA==",
     ...
     "parentProduct": {
        "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTYxMg=="
     },
     "volumeUnit": {
        "href": "http://shopname.api.shoprenter.hu/lengthClasses/bGVuZ3RoQ2xhc3MtbGVuZ3RoX2NsYXNzX2lkPTE="
     },
     ...
   }
```
Ezzel el is készültünk!