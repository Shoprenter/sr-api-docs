# API Batch feldolgozó

Az API kérések számának csökkentése, valamint a kérések gyorsabb kiszolgálása érdekében, az API kéréseket kötegelt (batch) módon is fel tudjuk dolgozni. Ahhoz, hogy a batch feldolgozót igénybe tudjuk venni, egy speciális szerkezetű tömböt kell elküldenünk POST metódussal, az `[API_DOMAIN]/batch` URL-re.

## Működés

1. A kliens elküldi **POST** metódus segítségével, a kéréseket tartalmazó tömböt a `[API_DOMAIN]/batch` URL-re.

2. Az API ellenőrzi hogy a kliens rendelkezik-e megfelelő jogosultsággal a kérések kiszolgáláshoz, valamint hogy a kérések megfelelő szerkezetűk-e. Ha igen, akkor megkezdődik a kérések feldolgozása, ellenkező esetben a válasz valamilyen hibaüzenet formájában, a válaszoknak megfelelő struktúrában kerül visszaküldésre a kliensnek.

3. Egy ciklusban feldolgozza a szerver a kéréseket és egy speciális szerkezetű tömbben összegyűjti a kapott válaszokat.

4. Miután lefutott az összes kérés feldolgozása, a válaszokat tartalmazó tömböt a kérésnek megfelelő formátumban (javasoltan JSON, esetleg XML) a kimenetre küldi a szerver, amit aztán a kliens megkap és feldolgoz.

Batch kérés esetén az **ajánlott request szám 1000** legyen.

Egy post mérete *(max_post_size)* **32MB** lehet. Érdemes figyelni kép feltöltés esetén, hogy ezt ne lépjük túl.

**A lenti példákat szemléltetésképp mutatjuk be, ezért nem tartalmazzák az egész API request-et és response-t!**

## API kérés

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/batch</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>
        Accept:application/json<br>
        Content-Type:application/json
    </td>
  </tr>
</table>

A API kérés a következő struktúrát kell hogy kövesse:

```json
{
  "data": {
    "requests": [
      {
        "method": "GET",
        "uri": "http://shopname.api.myshoprenter.hu/productExtend?full=1&limit=200&page=0"
      },
      {
        "method": "POST",
        "uri": "http://shopname.api.myshoprenter.hu/products/[ID]",
        "data": {}
      }
    ]
  }
}
```

- **method:** GET, POST, PUT, DELETE
- **uri:** A resource-okhoz kapcsolódó API URI
- **data:** POST vagy PUT esetén az adatokat tartalmazó objektum

## API válasz

```json
{
  "requests": {
    "request": [
      {
        "method": "GET",
        "uri": "http://shopname.api.myshoprenter.hu/productExtend?full=1&limit=200&page=0",
        "response": {
          "header": { "statusCode": "200" },
          "body": {}
        }
      },
      {
        "method": "POST",
        "uri": "http://shopname.api.myshoprenter.hu/products/[ID]",
        "response": {
          "header": { "statusCode": "200" },
          "body": {}
        }
      }
    ]
  }
}
```

- **statusCode:** HTTP státusz kódja. Ha rendben volt a kérés kiszolgálása, ennek az értéke 200, 201 vagy 204 egyébként a hibára utaló státuszkód
- **body:** a választ tartalmazza, hiba esetén a hiba szöveges üzenete

**Bármilyen error keletkezik a batch API-n belüli kérésekben, technikai okok miatt, minden esetben 200-as státuszkóddal tér vissza, így a batch requestekben szereplő statusCode-okat a kliens alkalmazásban kell vizsgálni.**

További gyakorlati példák a tömeges küldés használatára.

Kérés

<details class="example-dropdown"><summary>PÉLDA</summary>
<p>

```php
Array(
    [requests] => Array(
        [0] => Array(
            [method] => GET
            [uri] => http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=
        )
        [1] => Array(
            [method] => DELETE
            [uri] => http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=
        )
        [2] => Array(
            [method] => PUT
            [uri] => http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=
            [data] => Array(
                [picture] => /data/cukorbetegek.JPG
                [sortOrder] => 2
                [status] => 1
                [multiplier] => 1.00000
                [productsStatus] => 1
                [groupCode] =>
                [parentCategory] => Array(
                    [id] => Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9NTM=
                )

                [centralCategory] => Array(
                    [id] => Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=
                )
            )
        )
        [3] => Array(
            [method] => POST
            [uri] => http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=
            [data] => Array(
                [status] => 0
            )
        )
        [4] => Array(
            [method] => GET
            [uri] => http://shopname.api.myshoprenter.hu/category/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=
        )
    )
)
```

</p>
</details>

Válasz

<details class="example-dropdown"><summary>PÉLDA</summary>
<p>

```xml
<response>
     <requests>
         <request>
             <method><![CDATA[GET]]></method>
             <uri><![CDATA[http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></uri>
             <response>
                 <header>
                     <statusCode>200</statusCode>
                 </header>
                 <body>
                     <href><![CDATA[http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></href>
                     <id><![CDATA[Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></id>
                     <innerId><![CDATA[18]]></innerId>
                     <picture><![CDATA[/data/cukorbetegek.JPG]]></picture>
                     <sortOrder><![CDATA[2]]></sortOrder>
                     <status><![CDATA[0]]></status>
                     <multiplier><![CDATA[1.00000]]></multiplier>
                     <productsStatus><![CDATA[1]]></productsStatus>
                     <groupCode/>
                     <dateCreated><![CDATA[2014-09-15T15:32:02]]></dateCreated>
                     <dateUpdated><![CDATA[2014-09-15T15:32:02]]></dateUpdated>
                     <parentCategory>
                         <href><![CDATA[http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9NTM=]]></href>
                     </parentCategory>
                     <centralCategory>
                         <href><![CDATA[http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></href>
                     </centralCategory>
                     <categoryDescriptions>
                         <href><![CDATA[http://shopname.api.myshoprenter.hu/categoryDescriptions?categoryId=Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></href>
                     </categoryDescriptions>
                     <categoryCustomerGroupRelations>
                         <href><![CDATA[http://shopname.api.myshoprenter.hu/categoryCustomerGroupRelations?categoryId=Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></href>
                     </categoryCustomerGroupRelations>
                     <customerGroups>
                         <href><![CDATA[http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=/customerGroups]]></href>
                     </customerGroups>
                 </body>
             </response>
         </request>
         <request>
             <method><![CDATA[DELETE]]></method>
             <uri><![CDATA[http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></uri>
             <response>
                 <header>
                     <statusCode>200</statusCode>
                 </header>
                 <body/>
             </response>
         </request>
         <request>
             <method><![CDATA[PUT]]></method>
             <uri><![CDATA[http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></uri>
             <response>
                 <header>
                     <statusCode>200</statusCode>
                 </header>
                 <body>
                     <href><![CDATA[http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></href>
                     <id><![CDATA[Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></id>
                     <innerId><![CDATA[18]]></innerId>
                     <picture><![CDATA[/data/cukorbetegek.JPG]]></picture>
                     <sortOrder><![CDATA[2]]></sortOrder>
                     <status><![CDATA[1]]></status>
                     <multiplier><![CDATA[1.00000]]></multiplier>
                     <productsStatus><![CDATA[1]]></productsStatus>
                     <groupCode/>
                     <dateCreated><![CDATA[2014-09-15T15:32:02]]></dateCreated>
                     <dateUpdated><![CDATA[2014-09-15T15:33:53]]></dateUpdated>
                     <parentCategory>
                         <href><![CDATA[http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9NTM=]]></href>
                     </parentCategory>
                     <centralCategory>
                         <href><![CDATA[http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></href>
                     </centralCategory>
                     <categoryDescriptions>
                         <href><![CDATA[http://shopname.api.myshoprenter.hu/categoryDescriptions?categoryId=Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></href>
                     </categoryDescriptions>
                     <categoryCustomerGroupRelations>
                         <href><![CDATA[http://shopname.api.myshoprenter.hu/categoryCustomerGroupRelations?categoryId=Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></href>
                     </categoryCustomerGroupRelations>
                     <customerGroups>
                         <href><![CDATA[http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=/customerGroups]]></href>
                     </customerGroups>
                 </body>
             </response>
         </request>
         <request>
             <method><![CDATA[POST]]></method>
             <uri><![CDATA[http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></uri>
             <response>
                 <header>
                     <statusCode>200</statusCode>
                 </header>
                 <body>
                     <href><![CDATA[http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></href>
                     <id><![CDATA[Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></id>
                     <innerId><![CDATA[18]]></innerId>
                     <picture><![CDATA[/data/cukorbetegek.JPG]]></picture>
                     <sortOrder><![CDATA[2]]></sortOrder>
                     <status><![CDATA[0]]></status>
                     <multiplier><![CDATA[1.00000]]></multiplier>
                     <productsStatus><![CDATA[1]]></productsStatus>
                     <groupCode/>
                     <dateCreated><![CDATA[2014-09-15T15:32:02]]></dateCreated>
                     <dateUpdated><![CDATA[2014-09-15T15:33:53]]></dateUpdated>
                     <parentCategory>
                         <href><![CDATA[http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9NTM=]]></href>
                     </parentCategory>
                     <centralCategory>
                         <href><![CDATA[http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></href>
                     </centralCategory>
                     <categoryDescriptions>
                         <href><![CDATA[http://shopname.api.myshoprenter.hu/categoryDescriptions?categoryId=Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></href>
                     </categoryDescriptions>
                     <categoryCustomerGroupRelations>
                         <href><![CDATA[http://shopname.api.myshoprenter.hu/categoryCustomerGroupRelations?categoryId=Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></href>
                     </categoryCustomerGroupRelations>
                     <customerGroups>
                         <href><![CDATA[http://shopname.api.myshoprenter.hu/categories/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=/customerGroups]]></href>
                     </customerGroups>
                 </body>
             </response>
         </request>
         <request>
             <method><![CDATA[GET]]></method>
             <uri><![CDATA[http://shopname.api.myshoprenter.hu/category/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=]]></uri>
             <response>
                 <header>
                     <statusCode>404</statusCode>
                 </header>
                 <body>
                     <message><![CDATA[Resource matching URI "/category/Y2F0ZWdvcnktY2F0ZWdvcnlfaWQ9MTg=" not found]]></message>
                 </body>
             </response>
         </request>
     </requests>
 </response>
```

</p>
</details>

## Gyakori problémák

1. **Üres válasz, vagy "Data parameter not found in POST/PUT!" hibaüzenet 400-as státusz kóddal:**<br>
Értelemszerűen nem található **data** paraméter a küldött tömbben.


###

## További példák

### Tömeges termékfeltöltés

A következő példában az előzőhöz példához hasonló gyakori művelet kerül bemutatásra, ahol is batchelés segítségével több terméket töltünk fel egyszerre.
Annak érdekében, hogy a termék feltöltés során minden a termékhez kapcsolódó további adat is feltöltésre kerüljön (pl: képek, tulajdonságok stb.), így érdemes a
[**Product Extend Resource-t**](../../api/product_extend.md) használni.

**Fontos megjegyezni, hogy a batchelésnek vannak korlátai, amit a gördülékeny hívások érdekében ajánlott betartani. Ilyenek például:**
1. A batchelt kéréseket lehetőség szerint ne aszinkron módon küldjük el, azaz egy batchelt hívást csak azt követően indítsunk, miután az előző batchelt hívás befejeződött, tehát kaptunk responset.
2. A dokumentáció elején megemlített egyszerre történő maximum megadható request szám 1000 legyen, illetve a post maximális mérete (max_post_size) 32 MB legyen.

**Az alábbi példa csak szemléltetésképp mutatja be a működést,
így azok a teljesség igénye nélkül nem tartalmazzák az egész API request-et és response-t!**

**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/batch</td>
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
  "data": {
    "requests": [
        {
            "method": "POST",
            "uri": "http://shopname.api.myshoprenter.hu/productExtend",
            "data": {...}
        },
        {
            "method": "POST",
            "uri": "http://shopname.api.myshoprenter.hu/productExtend",
            "data": {...}
        },
        {
            "method": "POST",
            "uri": "http://shopname.api.myshoprenter.hu/productExtend",
            "data": {...}
        }
    ]
  }
}
```

**Response**

```json
{
    "requests": {
        "request": [
            {
                "method": "POST",
                "uri": "http://shopname.api.myshoprenter.hu/productExtend",
                "response": {
                    "header": {
                        "statusCode": 200
                    },
                    "body": {...}
                }
            },
            {
                "method": "POST",
                "uri": "http://shopname.api.myshoprenter.hu/productExtend",
                "response": {
                    "header": {
                        "statusCode": 200
                    },
                    "body": {...}
                }
            },
            {
                "method": "POST",
                "uri": "http://shopname.api.myshoprenter.hu/productExtend",
                "response": {
                    "header": {
                        "statusCode": 200
                    },
                    "body": {...}
                }
            }
        ]
    }
}
```

### Termék hozzáadása kategóriához Outer ID segítségével

Ennek a példának a dokumentáción belül ugyan már létezik egy hasonló Outer ID nélküli részletes ([**Termék hozzáadása kategóriához**](../api-examples/04_attach_product_to_category.md)) leírása,
de az API hívások csökkentése érdekében az alábbi példában bemutatásra kerül, hogyan is lehet batchelve egyetlen kérés elküldésével ugyanezt megvalósítani.
Mind a kategóriat mind a terméket külsős azonosítókkal, azaz [**Outer ID-kal**](./05_outer_id.md) fogjuk létrehozni.
Az Outer ID szerepe azért lényeges a batchelt kérések küldése során, mivel előfordulhat, hogy egymáshoz kapcsolódó resourceokat (pl: termék-kategória) kell megadni
anélkül, hogy tudnánk például a kategória resource azonosítóját. 

**Fontos megjegyezni, hogy a batchelésnek vannak korlátai, amit a gördülékeny hívások érdekében ajánlott betartani. Ilyenek például:**
1. A batchelt kéréseket lehetőség szerint ne aszinkron módon küldjük el, azaz egy batchelt hívást csak azt követően indítsunk, miután az előző batchelt hívás befejeződött, tehát kaptunk responset.
2. A dokumentáció elején megemlített egyszerre történő maximum megadható request szám 1000 legyen, illetve a post maximális mérete (max_post_size) 32 MB legyen.

**Az alábbi példa csak szemléltetésképp mutatja be a működést,
így azok a teljesség igénye nélkül nem tartalmazzák az egész API request-et és response-t!**

**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/batch</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>
        Accept:application/json<br>
        Content-Type:application/json
    </td>
  </tr>
</table>

```json{6,11,14-20}
{
  "data": {
    "requests": [
        {
            "method": "POST",
            "uri": "http://shopname.api.myshoprenter.hu/categoryExtend/123",
            "data": {...}
        },
        {
            "method": "POST",
            "uri": "http://shopname.api.myshoprenter.hu/productExtend/456",
            "data": {
                ...
                "productCategoryRelations": [
                    {
                        "category": {
                            "id": "123"
                        }
                    }
                ]
            }
        }
    ]
  }
}
```

**Response**

```json{6,12,13,21,27,28,31-42}
{
    "requests": {
        "request": [
            {
                "method": "POST",
                "uri": "http://shopname.api.myshoprenter.hu/categoryExtend/123",
                "response": {
                    "header": {
                        "statusCode": 200
                    },
                    "body": {
                        "href": "http://shopname.api.myshoprenter.hu/categoryExtend/123",
                        "id": "123",
                        "innerId": "8797",
                        ...
                    }
                }
            },
            {
                "method": "POST",
                "uri": "http://shopname.api.myshoprenter.hu/productExtend/456",
                "response": {
                    "header": {
                        "statusCode": 200
                    },
                    "body": {
                        "href": "http://shopname.api.myshoprenter.hu/productExtend/456",
                        "id": "456",
                        "innerId": "41706",
                        ...
                        "productCategoryRelations": [
                            {
                                "href": "http://shopname.api.myshoprenter.hu/productCategoryRelations/cHJvZHVjdENhdGVnb3J5LXByb2R1Y3RfaWQ9NDE3MDYmY2F0ZWdvcnlfaWQ9MTIy",
                                "id": "cHJvZHVjdENhdGVnb3J5LXByb2R1Y3RfaWQ9NDE3MDYmY2F0ZWdvcnlfaWQ9MTIy",
                                "product": {
                                    "href": "http://shopname.api.myshoprenter.hu/products/456"
                                },
                                "category": {
                                    "href": "http://shopname.api.myshoprenter.hu/categories/123"
                                }
                            }
                        ],
                        ...
                    }
                }
            }
        ]
    }
}
```