# Layout

## Twig
The template system is built on the Twig engine. Further information can be found in the [official Twig documentation](https://twig.symfony.com).

---

## Extend a layout
To extend Twig templates, we use the `extends` keyword, which allows us to create new templates based on an existing one. Below is an example of extending `1-column-layout.tpl` using `base.tpl`:

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


In this example, `1-column-layout.tpl` extends the `base.tpl` template and defines various blocks such as `body_content` to customize the base template's content. In the `body_content` block, we not only add the `container` class but also override the content of `{% block body_content %}` defined in `base.tpl`. As a result, in places where `1-column-layout.tpl` is used, the `main-content` element in `base.tpl` will include the `page_head`, `page_body`, and other elements defined in `1-column-layout.tpl`. Additionally, the `header` and `footer` modules will appear, loaded using the [loadModule](04_global_objects.md#viewhelperloadmodule) function in `base.tpl`.


---

## Layout Structure

The layout can be divided into two parts: the route and its associated HTML structure. For example, let's consider the `product/product` route, which follows the following chain: `product/product.tpl` → `1-column-layout.tpl` → `base.tpl`. In `base.tpl`, the `pagehead`, `header`, and `footer` modules are loaded using the `loadModule` function, resulting in the final HTML structure.

---

## Module Structure

A module's structure can consist of multiple templates that build upon each other. For example, in the case of a product module, we can follow the chain: `featured.tpl` → `product_module.tpl` → `module.tpl`. Layering these templates allows for customization and reusability of modules within the system.

It's important to note that a block belonging to a subpage, pulled in using the `loadModule` function (not included directly), is not accessible within the module. This means we cannot override or modify the block associated with the subpage in the module template.

---

## Assigning Layout to Routes

In the `settings.json` file, you can define the default layout for template files that are not accessible in the TFSZ. This ensures that the appropriate layout is loaded on the specific page. Below is an example from the [settings.json](../theme-configs/02_settings_json.md) file:

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

[Full list of routes](04_global_objects.md#routes)

:red_circle: **If you want to set a layout for the `product/product` route, it cannot be controlled here. You need to specify it in the corresponding tpl file.**

