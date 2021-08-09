# "Új rendelés feladás" webhook működése

## Bevezetés

Előfordulhatnak olyan igények, hogy szükség van egy a webáruház által küldött üzenetre, amely értesít bennünket, ha feladtak egy új rendelést a webáruházban.
Ezek az értesítők, más néven **"webhook-ok"**, egy olyan API koncepció, amely "real-time" biztosít információt más rendszer felé.
Ezt az eseményt például felhasználhatjuk arra, hogy vevőink véleményét kérjük ki a megrendelt termékekre vonatkozóan.
Pontosabb leírást a webáruház webhook rendszeréről [itt](https://support.shoprenter.hu/hc/hu/articles/215106408-Automatizmusok) található.

## Példa

Az alábbi példában a [**Webhook Resource**](../../api/webhook.md) segítségével létrehozzuk egy új webhook küldő automatizmust,
amely minden rendelés felvételt követően azonnal kiküldi az általunk megadott url-re a rendeléshez tartozó adatokat.
A kiküldött webhookok tesztelésére az ingyenesen használható [**Webhook.site-ot**](https://webhook.site) fogjuk használni, amely biztosítja azt az urlt, amit webhook létrehozása során meg kell adnunk.

![webhook_webhooksite_blank](./images/webhook_webhooksite_blank.png)

A webhook kiküldése azonnali, amit úgy adhatunk meg, hogy a posztolás során nem adjuk meg a **webHookDelay** paramétert.

**Request**

<table>
  <tr>
    <td><b>method:</b></td>
    <td>POST</td>
  </tr>
  <tr>
    <td><b>url:</b></td>
    <td>http://shopname.api.myshoprenter.hu/webHooks</td>
  </tr>
  <tr>
    <td><b>headers:</b></td>
    <td>
        Accept:application/json<br>
        Content-Type:application/json
    </td>
  </tr>
</table>

**Request**

```json
{
    "event": "order_confirm",
    "status": "1",
    "label": "Teszt webhook",
    "webHookParameters": [
        {
            "type": "json",
            "url": "https://webhook.site/ef62fe6d-2ca0-42a5-831d-5ab8457bcac6"
        }
    ]
}
```

**Response**

```json
{
    "href": "http://shopname.api.myshoprenter.hu/webHooks/d2ViSG9vay1ub3RpZmljYXRpb25faWQ9Njg=",
    "id": "d2ViSG9vay1ub3RpZmljYXRpb25faWQ9Njg=",
    "event": "order_confirm",
    "status": "1",
    "label": "Teszt webhook",
    "webHookParameters": [
        {
            "type": "json",
            "url": "https://webhook.site/ef62fe6d-2ca0-42a5-831d-5ab8457bcac6",
            "webHook": {
                "href": "http://shopname.api.myshoprenter.hu/webHooks/d2ViSG9vay1ub3RpZmljYXRpb25faWQ9Njg="
            }
        }
    ],
    "webHookDelay": []
}
```

Ezt követően ha új rendelés leadás történik, akkor a webhook.site-on látható a beérkezett webhook.

![webhook_webhooksite_post](./images/webhook_webhooksite_post.png)

