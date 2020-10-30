# Termékopció kezelése

A példa megértése érdekében érdemes előzetesen elolvasni az alábbi [cikket](https://support.shoprenter.hu/hc/hu/articles/215106128).

Az alábbi példában bemutatásra kerül, hogy miként lehet egy termékhez különböző termékopciókat megadni.

A feladat 4 lépésből áll.
1. Termékopció létrehozása létező termékhez a [**Product Option Resource**](../../api/product_option.md) segítségével.
2. A létrehozott termékopcióhoz tartozó nyelvesítés elkészítése a [**Product Option Description Resource**](../../api/product_option_description.md) segítségével.
3. A létrehozott termékopció értékeinek létrehozása a [**Product Option Value Resource**](../../api/product_option_value.md) segítségével.
4. A létrehozott termékopció értékeinek nyelvesítése a [**Product Option Value Description Resource**](../../api/product_option_value_description.md) segítségével.

Példa, amivel levezetjük az elkészítés folyamatát:

Tegyük fel, hogy a boltunkban tortákat árulunk és a Dobos torta termékből szeretnénk egy 10 és egy 12 szeletes változatát értékesíteni.
A 10 szeletes változat ára megegyezik a termék alapárával, viszont a 12 szeletes változatot 2000 forinttal drágábban szeretnénk árusítani. 

## 1. lépés

A [**Product Option Resource**](../../api/product_option.md) segítségével létrehozzuk az új termékopciót.

**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/productOptions</td>
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
    "sortOrder": "1",
    "product": {
        "id": "cHJvZHVjdC1wcm9kdWN0X2lkPTUw"
    }
}
```

**Response**

```json
{
    "href": "http://shopname.api.shoprenter.hu/productOptions/cHJvZHVjdE9wdGlvbi1wcm9kdWN0X29wdGlvbl9pZD00",
    "id": "cHJvZHVjdE9wdGlvbi1wcm9kdWN0X29wdGlvbl9pZD00",
    "innerId": "4",
    "sortOrder": "1",
    "product": {
        "href": "http://shopname.api.shoprenter.hu/products/cHJvZHVjdC1wcm9kdWN0X2lkPTUw"
    },
    "productOptionDescriptions": {
        "href": "http://shopname.api.shoprenter.hu/productOptionDescriptions?productOptionId=cHJvZHVjdE9wdGlvbi1wcm9kdWN0X29wdGlvbl9pZD00"
    },
    "productOptionValues": {
        "href": "http://shopname.api.shoprenter.hu/productOptionValues?productOptionId=cHJvZHVjdE9wdGlvbi1wcm9kdWN0X29wdGlvbl9pZD00"
    }
}
```

## 2. lépés

A [**Product Option Description Resource**](../../api/product_option_description.md) segítségével elkészítjük a létrehozott termékopcióhoz tartozó nyelvesítést.
A példa magyar nyelvű fordítást mutatja be. Amennyiben további nyelveken szeretnénk hozzárendelni nevet az adott termékopcióhoz, úgy az alábbi lépést meg kell ismételni a kívánt nyelv resource id-jával.   

**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/productOptionDescriptions</td>
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
    "name": "Szeletek száma",
    "productOption": {
        "id": "cHJvZHVjdE9wdGlvbi1wcm9kdWN0X29wdGlvbl9pZD00"
    },
    "language": {
        "id": "bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ=="
    }
}
```

**Response**

```json
{
    "href": "http://shopname.api.shoprenter.hu/productOptionDescriptions/cHJvZHVjdE9wdGlvbkRlc2NyaXB0aW9uLXByb2R1Y3Rfb3B0aW9uX2lkPTUxOCZsYW5ndWFnZV9pZD0x",
    "id": "cHJvZHVjdE9wdGlvbkRlc2NyaXB0aW9uLXByb2R1Y3Rfb3B0aW9uX2lkPTUxOCZsYW5ndWFnZV9pZD01",
    "name": "Szeletek száma",
    "productOption": {
        "href": "http://shopname.api.shoprenter.hu/productOptions/cHJvZHVjdE9wdGlvbi1wcm9kdWN0X29wdGlvbl9pZD00"
    },
    "language": {
        "href": "http://shopname.api.shoprenter.hu/languages/bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ=="
    }
}
```

## 3. lépés

A [**Product Option Value Resource**](../../api/product_option_value.md) segítségével elkészítjük a létrehozott termékopcióhoz tartozó értékeket.

Az alábbi requestben létrehozunk két változatot: egy 10 és egy 12 szeletes változatot.
A 10 szeletes változat nem módosítja a termék árát, úgy vesszük, hogy ez a termék eredeti árával azonos.
A 12 szeletes változat árát megnöveljük az eredeti termék árához képest 2000 forinttal.

**Request a 10 szeletes változatra**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/productOptionValues</td>
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
    "sortOrder": "1",
    "productOption": {
        "id": "cHJvZHVjdE9wdGlvbi1wcm9kdWN0X29wdGlvbl9pZD00"
    }
}
```

**Response a 10 szeletes változatra**

```json
{
    "href": "http://shopname.api.shoprenter.hu/productOptionValues/cHJvZHVjdE9wdGlvblZhbHVlLXByb2R1Y3Rfb3B0aW9uX3ZhbHVlX2lkPTc0OA==",
    "id": "cHJvZHVjdE9wdGlvblZhbHVlLXByb2R1Y3Rfb3B0aW9uX3ZhbHVlX2lkPTc0OA==",
    "price": "0000.0000",
    "prefix": "",
    "sortOrder": "1",
    "productOption": {
        "href": "http://shopname.api.shoprenter.hu/productOptions/cHJvZHVjdE9wdGlvbi1wcm9kdWN0X29wdGlvbl9pZD00"
    },
    "productOptionValueDescriptions": {
        "href": "http://shopname.api.shoprenter.hu/productOptionValueDescriptions?productOptionValueId=cHJvZHVjdE9wdGlvblZhbHVlLXByb2R1Y3Rfb3B0aW9uX3ZhbHVlX2lkPTc0OA=="
    }
}
```

**Request a 12 szeletes változatra**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/productOptionValues</td>
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
    "price": "2000.0000",
    "sortOrder": "2",
    "prefix": "+",
    "productOption": {
        "id": "cHJvZHVjdE9wdGlvbi1wcm9kdWN0X29wdGlvbl9pZD00"
    }
}
```

**Response a 12 szeletes változatra**

```json
{
    "href": "http://shopname.api.shoprenter.hu/productOptionValues/cHJvZHVjdE9wdGlvblZhbHVlLXByb2R1Y3Rfb3B0aW9uX3ZhbHVlX2lkPTc0OA==",
    "id": "cHJvZHVjdE9wdGlvblZhbHVlLXByb2R1Y3Rfb3B0aW9uX3ZhbHVlX2lkPTc0OA==",
    "price": "2000.0000",
    "prefix": "+",
    "sortOrder": "2",
    "productOption": {
        "href": "http://shopname.api.shoprenter.hu/productOptions/cHJvZHVjdE9wdGlvbi1wcm9kdWN0X29wdGlvbl9pZD00"
    },
    "productOptionValueDescriptions": {
        "href": "http://shopname.api.shoprenter.hu/productOptionValueDescriptions?productOptionValueId=cHJvZHVjdE9wdGlvblZhbHVlLXByb2R1Y3Rfb3B0aW9uX3ZhbHVlX2lkPTc0OA=="
    }
}
```

## 4. lépés

A [**Product Option Value Description Resource**](../../api/product_option_value_description.md) segítségével elkészítjük a létrehozott termékopcióhoz tartozó értékek nyelvesítését magyar nyelven a 10 és 12 szeletes változathoz.   

**Request a 10 szeletes változatra**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/productOptionValueDescriptions</td>
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
    "name": "10 szeletes",
    "productOptionValue": {
        "id": "cHJvZHVjdE9wdGlvblZhbHVlLXByb2R1Y3Rfb3B0aW9uX3ZhbHVlX2lkPTc0OA=="
    },
    "language": {
        "id": "bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ=="
    }
}
```

**Response a 10 szeletes változatra magyar nyelven**

```json
{
    "href": "http://shopname.api.shoprenter.hu/productOptionValueDescriptions/cHJvZHVjdE9wdGlvblZhbHVlRGVzY3JpcHRpb24tcHJvZHVjdF9vcHRpb25fdmFsdWVfaWQ9NzQ4Jmxhbmd1YWdlX2lkPTE=",
    "id": "cHJvZHVjdE9wdGlvblZhbHVlRGVzY3JpcHRpb24tcHJvZHVjdF9vcHRpb25fdmFsdWVfaWQ9NzQ4Jmxhbmd1YWdlX2lkPTQ=",
    "name": "10 szeletes",
    "productOptionValue": {
        "href": "http://shopname.api.shoprenter.hu/productOptionValues/cHJvZHVjdE9wdGlvblZhbHVlLXByb2R1Y3Rfb3B0aW9uX3ZhbHVlX2lkPTc0OA=="
    },
    "language": {
        "href": "http://shopname.api.shoprenter.hu/languages/bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ=="
    }
}
```

**Request a 12 szeletes változatra magyar nyelven**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/productOptionValueDescriptions</td>
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
    "name": "12 szeletes",
    "productOptionValue": {
        "id": "cHJvZHVjdE9wdGlvblZhbHVlLXByb2R1Y3Rfb3B0aW9uX3ZhbHVlX2lkPTc0OA=="
    },
    "language": {
        "id": "bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ=="
    }
}
```

**Response a 12 szeletes változatra magyar nyelven**

```json
{
    "href": "http://shopname.api.shoprenter.hu/productOptionValueDescriptions/cHJvZHVjdE9wdGlvblZhbHVlRGVzY3JpcHRpb24tcHJvZHVjdF9vcHRpb25fdmFsdWVfaWQ9NzQ5Jmxhbmd1YWdlX2lkPTE=",
    "id": "cHJvZHVjdE9wdGlvblZhbHVlRGVzY3JpcHRpb24tcHJvZHVjdF9vcHRpb25fdmFsdWVfaWQ9NzQ4Jmxhbmd1YWdlX2lkPTQ=",
    "name": "12 szeletes",
    "productOptionValue": {
        "href": "http://shopname.api.shoprenter.hu/productOptionValues/cHJvZHVjdE9wdGlvblZhbHVlLXByb2R1Y3Rfb3B0aW9uX3ZhbHVlX2lkPTc0OA=="
    },
    "language": {
        "href": "http://shopname.api.shoprenter.hu/languages/bGFuZ3VhZ2UtbGFuZ3VhZ2VfaWQ9MQ=="
    }
}
```