# Cart.json API

```
GET /cart.json
```

This endpoint can be used if we want to retrieve the contents of the shopping cart with JavaScript.

The response is passed in JSON format.

Example:
```json
{
    "subTotal": 1950,
    "subTotalWithTax": 2476.5,
    "total": 2476.5,
    "taxTotal": 526.5,
    "token": "27828acb2141b0b16bbfc14358b0cbcd1d26aee0860c5",
    "itemCount": 1,
    "items": [
        {
            "cartKey":"S7QytqrOtDKwzrQyNbAAkoZQbGSdaGVoVV1sZW6llF9QkpmfV6wEFDKwqq6trQUA",
            "id": 409,
            "sku": "POTTED3500",
            "name": "Potted Double Stem Kaleidoscope Orchid",
            "quantity": 1,
            "image": "product/00011.jpg",
            "href": "https://demo.myshoprenter.hu/potted-double-stem-kaleidoscope-orchid-409",
            "price": 2476.5,
            "total": 2476.5,
            "totalOriginal": 2476.5,
            "priceOriginal": 2476.5,
            "special": false,
            "present": false,
            "requiresShipping": true,
            "option": [
              
            ],
            "values": [
              
            ],
            "weight": 0,
            "weightClass": "kg"
        }
    ]
}
```

Example of an empty basket:
```json
{
    "subTotal": 0,
    "subTotalWithTax": 0,
    "total": 0,
    "taxTotal": 0,
    "token": "",
    "itemCount": 0,
    "items": []
}
```

Example code to use:
```javascript
$.ajax({
    type: 'GET',
    url: 'https://demo.myshoprenter.hu/cart.json',
    success: function(res) {
        console.log(res);
    },
    error: function (request, status, error) {
        alert(request.responseText);
    }
});
```
```
GET /cart/reload/{token}
```

This endpoint is used to refill the cart.
The cart token must be entered instead of the token.
If we have entered the correct token, we will get back the basket contents corresponding to the given token, and then we will be redirected to the basket page.
If the wrong token is handed over, the contents of the basket will not change, but you will also be redirected to the basket page.
