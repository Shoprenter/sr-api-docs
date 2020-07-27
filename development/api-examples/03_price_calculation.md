# Árszámítás

Az alábbi példában bemutatásra kerül, hogy miként lehet egy termék árát kiszámolni, az alapértelmezett pénznemről egy számunkra ideális másik pénznemre.

Az árszámolás 3 lépésből áll.

## 1. lépés

Egy batch kérésben le kell kérdezni az összes számoláshoz szükséges befolyásoló tényezőt:
- az összes **Currency**-t (Pénznem), 
- az összes **TaxRate**-et (ÁFA kulcs),
- az összes **GeoZone**-t (Földrajzi zóna).

#### Request

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/batch</td>
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
            "method": "GET",
            "uri": "http://shopname.api.shoprenter.hu/geoZones?full=1"
         },
         {
            "method": "GET",
            "uri": "http://shopname.api.shoprenter.hu/taxRates?full=1"
         },
         {
            "method": "GET",
            "uri": "http://shopname.api.shoprenter.hu/currencies?full=1"
         }
      ]
   }
}
```

A Batch API válaszából kiderül, hogy a bolt milyen beállításokat tartalmaz:

**Földrajzi zónák:**

```json
{
    "items": [
        {
            "href": "http://shopname.api.shoprenter.hu/geoZones/Z2VvWm9uZS1nZW9fem9uZV9pZD01",
            "id": "Z2VvWm9uZS1nZW9fem9uZV9pZD01",
            "name": "Magyarország",
            "description": "HUN",
            "countries": [
                {
                    "href": "http://shopname.api.shoprenter.hu/countries/Y291bnRyeS1jb3VudHJ5X2lkPTk3",
                    "id": "Y291bnRyeS1jb3VudHJ5X2lkPTk3",
                    "name": "Magyarország",
                    "isoCode2": "HU",
                    "isoCode3": "HUN",
                    "status": "1",
                    "zones": {
                        "href": "http://shopname.api.shoprenter.hu/zones?countryId=Y291bnRyeS1jb3VudHJ5X2lkPTk3"
                    }
                }
            ]
        },
        {
            "href": "http://shopname.api.shoprenter.hu/geoZones/Z2VvWm9uZS1nZW9fem9uZV9pZD02",
            "id": "Z2VvWm9uZS1nZW9fem9uZV9pZD02",
            "name": "Európai Unió",
            "description": "EU",
            "countries": [...]
        }
    ]
}
```

**ÁFA kulcsok:**

```json
{
    "items": [
        {
            "href": "http://shopname.api.shoprenter.hu/taxRates/dGF4UmF0ZS10YXhfcmF0ZV9pZD05NA==",
            "id": "dGF4UmF0ZS10YXhfcmF0ZV9pZD05NA==",
            "priority": "1",
            "rate": "0.0000",
            "description": "ÁFA (0%)",
            "dateCreated": "2020-01-01T12:00:00",
            "dateUpdated": "2020-01-01T12:00:00",
            "geoZone": {
                "href": "http://shopname.api.shoprenter.hu/geoZones/Z2VvWm9uZS1nZW9fem9uZV9pZD01"
            },
            "taxClass": {
                "href": "http://shopname.api.shoprenter.hu/taxClasses/dGF4Q2xhc3MtdGF4X2NsYXNzX2lkPTEx"
            }
        },
        {
            "href": "http://shopname.api.shoprenter.hu/taxRates/dGF4UmF0ZS10YXhfcmF0ZV9pZD05NQ==",
            "id": "dGF4UmF0ZS10YXhfcmF0ZV9pZD05NQ==",
            "priority": "1",
            "rate": "27.0000",
            "description": "ÁFA (27%)",
            "dateCreated": "2020-01-01T12:00:00",
            "dateUpdated": "2020-01-01T12:00:00",
            "geoZone": {
                "href": "http://shopname.api.shoprenter.hu/geoZones/Z2VvWm9uZS1nZW9fem9uZV9pZD01"
            },
            "taxClass": {
                "href": "http://shopname.api.shoprenter.hu/taxClasses/dGF4Q2xhc3MtdGF4X2NsYXNzX2lkPTEw"
            }
        }
    ]
}
```

**Pénznemek:**

```json
{
    "items": [
        {
            "href": "http://shopname.api.shoprenter.hu/currencies/Y3VycmVuY3ktY3VycmVuY3lfaWQ9NA==",
            "id": "Y3VycmVuY3ktY3VycmVuY3lfaWQ9NA==",
            "name": "HUF",
            "code": "HUF",
            "symbolLeft": "",
            "symbolRight": " Ft",
            "decimalPlace": "0",
            "value": "311.85000000",
            "status": "1",
            "dateUpdated": "2020-01-01 12:00:00"
        },
        {
            "href": "http://shopname.api.shoprenter.hu/currencies/Y3VycmVuY3ktY3VycmVuY3lfaWQ9NQ==",
            "id": "Y3VycmVuY3ktY3VycmVuY3lfaWQ9NQ==",
            "name": "EUR",
            "code": "EUR",
            "symbolLeft": "€ ",
            "symbolRight": "",
            "decimalPlace": "3",
            "value": "1.00000000",
            "status": "1",
            "dateUpdated": "2020-01-01 12:00:00"
        }
    ]
}
```

## 2. lépés

Azt aktuális termék lekérdezése a **productExtend** resource segítségével.

#### Request

<table>
  <tr>
    <td><b>method:</b></td>
    <td>GET</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.shoprenter.hu/productExtend/cHJvZHVjdC1wcm9kdWN0X2lkPTYx</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>
        Accept:application/json<br>
        Content-Type:application/json
    </td>
  </tr>
</table>

#### Response

```json
{
   "productPrices": [
      {
         "customerGroup": {
            "id": "Y3VzdG9tZXJHcm91cC1jdXN0b21lcl9ncm91cF9pZD02",
            "innerId": 6,
            "default": false
         },
         "net": "1200.000",
         "netOriginal": "1200.000",
         "netSpecial": null,
         "gross": "1524.000",
         "grossOriginal": "1524.000",
         "grossSpecial": null,
         "currencyCode": "EUR"
      },
      {
         "customerGroup": {
            "id": "Y3VzdG9tZXJHcm91cC1jdXN0b21lcl9ncm91cF9pZD04",
            "innerId": 8,
            "default": true
         },
         "net": "1200.000",
         "netOriginal": "1200.000",
         "netSpecial": null,
         "gross": "1524.000",
         "grossOriginal": "1524.000",
         "grossSpecial": null,
         "currencyCode": "EUR"
      }
   ]
}
```

A válaszból számunkra csak a **productPrices** értéke lesz fontos.
A **productPrices** lista tartalmazza a boltban alapértelmezettnek beállított pénznemmel kiszámolt árakat, vevői csoportok szerint lebontva.

## 3. lépés

Az utolsó lépés maga az árszámítás, mivel az összes szükséges adatunk meg van hozzá.

A fenti példában látható, hogy a termék alapértelmezett pénzneme az euró ("EUR"). Valamint tudjuk, hogy melyik az alapértelmezett vevői csoport (CustomerGroup), 8-as innerId-val.

Ha pl. meg akarom kapni magyar forintban ("HUF") a példában látható termék **alapértelmezett vevői csoporttal**, a termék **bruttó árát**, 
akkor a lekérdezett **földrajzi zónák** (GeoZone) közül ki kell keresnem, hogy melyikhez tartozik Magyarország.

Ha megvan a **földrajzi zóna** (GeoZone), akkor az alapján behatárolom az **adó kulcsot** (TaxRate).

Ezután a termék nettó árát megszorzom a már lekérdezett **pénznemek** (Currency) között megtalálható magyar forint **értékével**.
Végül az **adó kulcs rátá** (TaxRate) segítségével kiszámolom a termék árát Áfával együtt.

- Nettó (net):

`termék nettó ára * pénznem értéke = nettó ár`

`1200.000 * 311.85000000 = 374220 Ft`

- Bruttó (gross):

`termék nettó ára * pénznem értéke * (ÁFA kulcs / 100 + 1.0) = bruttó ár`

`1200.000 * 311.85000000 * (27.0000 / 100 + 1.0) = 475259.4 Ft`

- Áfa összeg:

`termék nettó ára * pénznem értéke * (ÁFA kulcs / 100) = áfa összeg`

`1200.000 * 311.85000000 * (27.0000 / 100) = 101039.4 Ft`
