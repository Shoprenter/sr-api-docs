# Akciós termék

Az alábbi példában bemutatásra kerül, hogy miként lehet egy termékhez akciós árat rendelni, módosítani és törölni.

## Akciós ár felvétele

Akciós árat egy termékhez a [**Product Special Resource**](../../api/product_special.md) segítségével lehet megadni. 
A posztolás során szükségünk van a korábban felvett termék ([**Product Resource**](../../api/product.md)) resource azonosítójára,
illetve annak a vevőcsoportnak ([**Customer Group Resource**](../../api/customer_group.md)) resource azonosítójára, akiknek az akciót szeretnénk biztosítani.
A minimum mennyiség és maximum mennyiség értékének csak abban az esetben szükséges 0-nál magasabb számot megadni, ha mennyiségi árkedvezmény kerül beállításra.

**Megjegyzés:** A nap terméke egy speciális akciós árnak számít (lásd bővebben a [**Nap terméke**](./01_1_product_special_product_of_day.md) példában) 

### Példa

#### Request

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/productSpecials</td>
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
    "priority": "1",
    "price": "1000.0000",
    "dateFrom": "2020-11-01",
    "dateTo": "2022-11-15",
    "minQuantity": "0",
    "maxQuantity": "100",
    "product": {
        "id": "cHJvZHVjdC1wcm9kdWN0X2lkPTE2OQ=="
    },
    "customerGroup": {
        "id": "Y3VzdG9tZXJHcm91cC1jdXN0b21lcl9ncm91cF9pZD04"
    }
}
```

#### Response

```json
{
    "href": "http://demo.api.aurora.ballapeter/productSpecials/cHJvZHVjdFNwZWNpYWwtcHJvZHVjdF9zcGVjaWFsX2lkPTEwOQ==",
    "id": "cHJvZHVjdFNwZWNpYWwtcHJvZHVjdF9zcGVjaWFsX2lkPTEwOQ==",
    "priority": "1",
    "price": "1000.0000",
    "dateFrom": "2020-11-01 00:00:00",
    "dateTo": "2022-11-15 00:00:00",
    "minQuantity": "0",
    "maxQuantity": "100",
    "dateCreated": "2020-10-26T10:30:26",
    "type": "interval",
    "dayOfWeek": null,
    "product": {
        "href": "http://demo.api.aurora.ballapeter/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE2OQ=="
    },
    "customerGroup": {
        "href": "http://demo.api.aurora.ballapeter/customerGroups/Y3VzdG9tZXJHcm91cC1jdXN0b21lcl9ncm91cF9pZD04"
    }
}
```

## Akciós ár módosítása

Akciós ár módosításához szükségünk lesz a korábban felvitt akciós ár resource azonosítójára.
Amennyiben a vevőcsoportot szeretnénk módosítani "Mindenki" vevőcsoportra, úgy érdemes törölni előbb az akciót és egy újat létrehozni. Minden más vevőcsoport esetén a módosítás végrehajtható.

### Példa

#### Request

<table>
  <tr>
    <td><b>method:</b></td>
    <td>PUT</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/productSpecials/product_special_id</td>
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
    "priority": "1",
    "price": "2000.0000",
    "dateFrom": "2020-11-01",
    "dateTo": "2020-11-10",
    "minQuantity": "0",
    "maxQuantity": "100",
    "product": {
        "id": "cHJvZHVjdC1wcm9kdWN0X2lkPTE2OQ=="
    },
    "customerGroup": {
        "id": "Y3VzdG9tZXJHcm91cC1jdXN0b21lcl9ncm91cF9pZD04"
    }
}
```

#### Response

```json
{
    "href": "http://demo.api.aurora.ballapeter/productSpecials/cHJvZHVjdFNwZWNpYWwtcHJvZHVjdF9zcGVjaWFsX2lkPTEwOQ==",
    "id": "cHJvZHVjdFNwZWNpYWwtcHJvZHVjdF9zcGVjaWFsX2lkPTEwOQ==",
    "priority": "1",
    "price": "2000.0000",
    "dateFrom": "2020-11-01 00:00:00",
    "dateTo": "2020-11-10 00:00:00",
    "minQuantity": "0",
    "maxQuantity": "100",
    "dateCreated": "2020-10-26T10:30:26",
    "type": "interval",
    "dayOfWeek": null,
    "product": {
        "href": "http://demo.api.aurora.ballapeter/products/cHJvZHVjdC1wcm9kdWN0X2lkPTE2OQ=="
    },
    "customerGroup": {
        "href": "http://demo.api.aurora.ballapeter/customerGroups/Y3VzdG9tZXJHcm91cC1jdXN0b21lcl9ncm91cF9pZD04"
    }
}
```

## Akciós ár törlése

Akciós ár törléséhez szükségünk lesz a korábban felvitt akciós ár resource azonosítójára.

### Példa

#### Request

<table>
  <tr>
    <td><b>method:</b></td>
    <td>DELETE</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/productSpecials/product_special_id</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>
        Accept:application/json<br>
        Content-Type:application/json
    </td>
  </tr>
</table>
