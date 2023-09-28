# Price calculation

The following example demonstrates how to calculate the price of a product from the default currency to another currency that is ideal for you.

The price calculation consists of three steps:

1. Retrieving all the necessary data for the calculation.
2. Querying the current product.
3. Performing the specific price calculation.

## Step 1.

In a batch request, you need to retrieve all the influencing factors required for the calculation:
- all [**GeoZone**-t (Geo Zone)](../../api/geo_zone.md),
- all [**TaxRate**-et (Tax class)](../../api/tax_rate.md),
- all [**Currency**-t (Currency)](../../api/currency.md).

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
            "method": "GET",
            "uri": "http://shopname.api.myshoprenter.hu/geoZones?full=1"
         },
         {
            "method": "GET",
            "uri": "http://shopname.api.myshoprenter.hu/taxRates?full=1"
         },
         {
            "method": "GET",
            "uri": "http://shopname.api.myshoprenter.hu/currencies?full=1"
         }
      ]
   }
}
```

The response from the [Batch API](../api/04_batch.md) reveals the settings contained in the store:

### Geo Zone:

```json
{
    "items": [
        {
            "href": "http://shopname.api.myshoprenter.hu/geoZones/Z2VvWm9uZS1nZW9fem9uZV9pZD01",
            "id": "Z2VvWm9uZS1nZW9fem9uZV9pZD01",
            "name": "Hungary",
            "description": "HUN",
            "countries": [
                {
                    "href": "http://shopname.api.myshoprenter.hu/countries/Y291bnRyeS1jb3VudHJ5X2lkPTk3",
                    "id": "Y291bnRyeS1jb3VudHJ5X2lkPTk3",
                    "name": "Hungary",
                    "isoCode2": "HU",
                    "isoCode3": "HUN",
                    "status": "1",
                    "zones": {
                        "href": "http://shopname.api.myshoprenter.hu/zones?countryId=Y291bnRyeS1jb3VudHJ5X2lkPTk3"
                    }
                }
            ]
        },
        {
            "href": "http://shopname.api.myshoprenter.hu/geoZones/Z2VvWm9uZS1nZW9fem9uZV9pZD02",
            "id": "Z2VvWm9uZS1nZW9fem9uZV9pZD02",
            "name": "European Union",
            "description": "EU",
            "countries": [...]
        }
    ]
}
```

### Tax class:

```json
{
    "items": [
        {
            "href": "http://shopname.api.myshoprenter.hu/taxRates/dGF4UmF0ZS10YXhfcmF0ZV9pZD05NA==",
            "id": "dGF4UmF0ZS10YXhfcmF0ZV9pZD05NA==",
            "priority": "1",
            "rate": "0.0000",
            "description": "VAT (0%)",
            "dateCreated": "2020-01-01T12:00:00",
            "dateUpdated": "2020-01-01T12:00:00",
            "geoZone": {
                "href": "http://shopname.api.myshoprenter.hu/geoZones/Z2VvWm9uZS1nZW9fem9uZV9pZD01"
            },
            "taxClass": {
                "href": "http://shopname.api.myshoprenter.hu/taxClasses/dGF4Q2xhc3MtdGF4X2NsYXNzX2lkPTEx"
            }
        },
        {
            "href": "http://shopname.api.myshoprenter.hu/taxRates/dGF4UmF0ZS10YXhfcmF0ZV9pZD05NQ==",
            "id": "dGF4UmF0ZS10YXhfcmF0ZV9pZD05NQ==",
            "priority": "1",
            "rate": "27.0000",
            "description": "TAX (27%)",
            "dateCreated": "2020-01-01T12:00:00",
            "dateUpdated": "2020-01-01T12:00:00",
            "geoZone": {
                "href": "http://shopname.api.myshoprenter.hu/geoZones/Z2VvWm9uZS1nZW9fem9uZV9pZD01"
            },
            "taxClass": {
                "href": "http://shopname.api.myshoprenter.hu/taxClasses/dGF4Q2xhc3MtdGF4X2NsYXNzX2lkPTEw"
            }
        }
    ]
}
```

### Currency:

```json
{
    "items": [
        {
            "href": "http://shopname.api.myshoprenter.hu/currencies/Y3VycmVuY3ktY3VycmVuY3lfaWQ9NA==",
            "id": "Y3VycmVuY3ktY3VycmVuY3lfaWQ9NA==",
            "name": "HUF",
            "code": "HUF",
            "symbolLeft": "",
            "symbolRight": " HUF",
            "decimalPlace": "0",
            "value": "311.85000000",
            "status": "1",
            "dateUpdated": "2020-01-01 12:00:00"
        },
        {
            "href": "http://shopname.api.myshoprenter.hu/currencies/Y3VycmVuY3ktY3VycmVuY3lfaWQ9NQ==",
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

## Step 2.

Querying the current product using the [**productExtend**](../../api/product_extend.md) resource.

**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>GET</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/productExtend/cHJvZHVjdC1wcm9kdWN0X2lkPTYx</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>
        Accept:application/json<br>
        Content-Type:application/json
    </td>
  </tr>
</table>

**Response**

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

The value of **productPrices** in the response is the one that is important for us. 
The **productPrices** list contains prices calculated in the store's default currency, broken down by customer groups.

## Step 3.

The last step is the actual price calculation since we have all the necessary data for it.

In the example above, it's evident that the default currency for the product is the Euro ("EUR"). Additionally, we know the default customer group (CustomerGroup) with an innerId of 8.

If, for example, you want to retrieve the **gross price** of the product shown in the example in Hungarian HUF ("HUF") for **the default customer group*, you would need to look up which **geographic zone** (GeoZone) corresponds to Hungary among the queried ones.

If I have the **geographical zone** (GeoZone), then I will define the **tax rate** (TaxRate) based on it

Next, I multiply the net price of the product by the Hungarian forint **value** found in the already queried **currencies** (Currency).
Finally, I calculate the price of the product including VAT using the **tax rate** (TaxRate).

**Some example:**

- Net (net):

`product net price * currency value = net price`

`1200.000 * 311.85000000 = HUF 374220`

- Gross:

`product net price * currency value * (VAT rate / 100 + 1.0) = gross price`

`1200.000 * 311.85000000 * (27.0000 / 100 + 1.0) = HUF 475259.4`

- VAT amount:

`product net price * currency value * (VAT rate / 100) = VAT amount`

`1200.000 * 311.85000000 * (27.0000 / 100) = HUF 101039.4`
