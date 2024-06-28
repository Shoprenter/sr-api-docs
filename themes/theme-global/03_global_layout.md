# Layout

## Twig
A template rendszer Twig motorra épül. További információ a [Twig hivatalos dokumentációjában](https://twig.symfony.com) található.

---

## Kiterjesztés
A Twig sablonok kiterjesztéséhez az `extends` kulcsszót használjuk, amely lehetővé teszi, hogy egy meglévő sablonból kiindulva új sablonokat hozzunk létre. Az alábbiakban egy példa látható a `1-column-layout.tpl` kiterjesztésére a `base.tpl` használatával:

### 1-column-layout.tpl

```
{% extends "layout/base.tpl" %}

{% block body_content %}
    <div class="container">
        {{ viewHelper.loadPosition('pathway') }}
        {% block page_head %}
            <div class="page-head">
                {% block content_title %}
                    <h1 class="page-head-title">{{ heading_title }}</h1>
                {% endblock %}
            </div>
        {% endblock %}

        {% block page_body %}
            {% block content %}{% endblock %}
        {% endblock %}
    </div>
{% endblock %}
```

### base.tpl

```
{% spaceless %}
    {% set page %}
        {% block body_header %}
            {{ viewHelper.loadModule('sections/header') }}
        {% endblock %}

        <main class="main-content">
            {% block body_content %}
                <!-- Ez egy alapértelmezett tartalom, ha felülírjuk nem jelenik meg -->
            {% endblock %}
        </main>

        {% block body_footer %}
            {{ viewHelper.loadModule('common/footer') }}
        {% endblock %}
    {% endset %}
{% endspaceless %}
{{ page }}
</body>
</html>
```


Ebben a példában a `1-column-layout.tpl` kiterjeszti a `base.tpl` sablont, és definiál különböző blokkokat, például `body_content`, hogy testreszabja az alapsablon tartalmát. A `body_content` blokkban nemcsak a `container` osztályt adjuk hozzá, hanem felülírjuk a `base.tpl`-ben definiált `{% block body_content %}` blokk tartalmát is. Ennek eredményeképpen a `1-column-layout.tpl`-t használó helyeken a `base.tpl`-ben található `main-content` elem tartalmazni fogja a `1-column-layout.tpl`-ben meghatározott `page_head`, `page_body` és egyéb elemeket. Emellett a `header` és `footer` modulok is megjelennek, amelyeket a `base.tpl`-ben a [loadModule](04_global_objects.md#viewhelperloadmodule) segítségével töltöttünk be.

---

## Layout felépítés
A layout két részre bontható: a route (útvonal) és a hozzá kapcsolódó HTML felépítés. Példaként vegyük a `product/product` útvonalat, amely a következő láncot követi: `product/product.tpl` → `1-column-layout.tpl` → `base.tpl`. A `base.tpl`-ben a `pagehead`, `header` és `footer` modulok a loadModule függvénnyel vannak betöltve, így áll össze a végső HTML struktúra.

---

## Modul felépítés
Egy modul felépítése több sablonból állhat, amelyek egymásra épülnek. Például a termék modul esetében a következő láncolatot követhetjük: `featured.tpl` → `product_module.tpl` → `module.tpl`. Ezen sablonok rétegezése lehetővé teszi a modulok testreszabását és újrafelhasználhatóságát a rendszerben.

Fontos megjegyezni, hogy egy aloldalhoz tartozó blokk, amelyet a `loadModule` függvény segítségével húztunk be (nem include-oltuk), nem érhető el a modulban. Ez azt jelenti, hogy nem tudjuk felülírni vagy módosítani az aloldalhoz tartozó blokkot a modul sablonjában.

---

## Layout rendelése route-hoz

A `settings.json` fájlban lehet meghatározni az alapértelmezett layoutot, amely a TFSZ-ben nem elérhető template fájlokhoz tartozik. Ez biztosítja, hogy a megfelelő layout töltődjön be az adott oldalon. Az alábbiakban egy példa látható a [settings.json](../theme-configs/02_settings_json.md) fájlból:

```json
{
    "layouts": [
        {
            "name": "layout/1-column-layout",
            "route": "default"
        }
    ]
}
```
[Teljes lista a route-okról](04_global_objects.md#routes)

:red_circle: **Amennyiben a `product/product` route-ra szeretnénk egy layoutot beállítani, akkor azt nem itt tudjuk szabályozni, hanem a hozzá tartozó tpl fájlban lehet megadni.**
