# Layout

## Twig
A projekt jelenleg a Twig 1.43.1 verzióját használja. További információ a [Twig hivatalos dokumentációjában](https://twig.symfony.com/doc/1.x/) található.

---

## Layout rendelése route-hoz

A `settings.json` fájlban a különböző layoutok és azok útvonalakhoz való rendelése található. Ez biztosítja, hogy a megfelelő layout töltődjön be az adott útvonalhoz. Az alábbiakban egy példa látható a [settings.json](../theme-configs/02_settings_json.md) fájlból:

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
Ebben a fájlban minden egyes objektum egy layout és egy hozzá tartozó útvonal párost tartalmaz. Például, ha a felhasználó a "product/list" útvonalra navigál, akkor a "layout/2-column-left-layout" layout-ot fogja betölteni.

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
            {% block body_content %}{% endblock %}
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

Ebben a példában a 1-column-layout.tpl a base.tpl sablont terjeszti ki, és különböző blokkokat (pl. body_content) definiál, hogy testreszabja az alap sablon tartalmát. A `body_content`-en belül jól látszik, hogy hogy hozzáadunk egy `container` class-t, ami azt eredményezi, hogy ahol a 1-column-layout.tpl van használatban, ott a base.tpl-ben található `main-content` elemen belül lesz egy `container` elem.

---
