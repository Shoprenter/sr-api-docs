# Dynamic Modules

In the Theme File Editor, dynamic modules are located in the **sections** directory. Dynamic modules are modules where both the frontend appearance and the admin interface settings can be managed simultaneously.

Variables created outside of dynamic modules cannot be accessed within dynamic modules. Similarly, variables created within dynamic modules cannot be accessed outside of them.

Within dynamic modules, a new tag can be used:

``` {% schema %}```

More details about the schema tag will be provided later.

## Using Dynamic Modules
Dynamic modules can be added to theme files manually or dynamically through module positions.

### Manual Usage
To add a dynamic module to a theme file, use the *viewHelper.loadModule()* function. For example:

``` 
{{ viewHelper.loadModule('sections/my-first-section') }}
``` 

_The dynamically inserted module as shown above is referred to as a "manually inserted module" in the following._

A dynamic module can be inserted into multiple theme files; however, each specific dynamic module can only appear once in the modules list on the Modules page. If we modify the configuration of a manually inserted module, the changes will apply everywhere that module is found. It's important to note that dynamic modules cannot contain other dynamic modules. For manual usage, specifying a **name** attribute in the _attributes_ object is sufficient.

### Usage in Positions
Dynamic modules can also be placed within positions using the **viewHelper.loadPosition()** function. For example:

```
{{ viewHelper.loadPosition('home') }}
```

This means that ShopRenter displays all modules whose position is **_home_**. Positions can be defined in the **positions** object within the **settings.json** file in the Theme File Editor.

:red_circle: **IMPORTANT**: If you want to create new positions, you need to add them here. Administrators can change the positions of dynamic modules within the admin interface on the dynamic module editing page. Dynamic modules must have a **position**, **status**, and **sort_order** set in the schema settings object; otherwise, the module will not appear.

## Using Dynamic Module Schema
The schema of dynamic modules is defined within the Twig **{% schema %}** tag. Similar to the Twig comment tag, the schema does not produce any output, and the Twig code within the schema tag is not executed.

Each dynamic module can have one schema tag containing valid JSON. The schema tag can be placed anywhere within the dynamic module theme file, except inside another Twig tag.

Within the schema tag of a dynamic module, the following properties can be defined:

### attributes
The schema of a dynamic module must include an **attributes** object and a **name** property. If these are missing, an error will occur when the module is loaded.

#### name property
The **name** property is used to define the name of the dynamic module. It can be a simple string or an object. Using an object is useful when specifying the module name in a language-specific manner.

For example:
```
{% schema %}
{
    "attributes": {
         "name": "Teszt modul név"
    }
}
{% endschema %}
```
Or:
```
{% schema %}
{
    "attributes": {
         "name": {
            "en": "English section name",
            "hu": "Magyar modul név"
         }
    }
}
{% endschema %}
```

#### helpLink property

There is an option to specify a **helpLink** property, where you need to provide a URL. The "Help" button will link to this URL.

For example:

```
{% schema %}
{
    "attributes": {
         "name": "My first section",
         "helpLink": {
              "en": "https://www.shoprenter.hu/blog/1",
              "hu": "https://www.shoprenter.hu/blog/1"
         }
    }
}
{% endschema %}
```

#### maxBlocks property

If you create a dynamic module that also uses blocks (see more: [blocks](#blocks)), you have the option to specify the maximum number of block items that can be added to the module.

By default, you can add as many blocks as needed to a dynamic module. However, if you want to set a maximum limit, it's important to provide a positive integer value for the maxBlocks property.

Incorrect values for this property will result in an error message, preventing the module from loading.

Example of correct usage:

```
{% schema %}
{
    "attributes": {
         "name": "My first section",
         "maxBlocks": 6
    }
}
{% endschema %}
```

### settings

Dynamic modules have their own settings within the settings object.
Settings can be used to provide an admin interface for editing the dynamic module.
Users can access the dynamic module from the module list in the admin interface by clicking on its name or the edit button.

For example:

```
{% schema %}
    {
        "attributes": {
            "name": "My first section"
        },
        "settings": [
            {
                "type": "text",
                "name": "title",
                "label": "Title",
                "default": "My first section title"
            }
        ]
    }
{% endschema %}
```

Within the settings object of a dynamic module, the **name** property must be unique within that specific dynamic module, but it does not need to be globally unique. No special characters other than underscore (_) can be used in the value of the name property.

The value of the setting can be accessed in HTML through the **section Object**, for example:

```
{{ section.settings.name }}
```

The default property serves to set a field's default value. This is an optional setting. The property value can be string|int|bool|object, depending on whether the field is multilingual or not.

- If there is no default field, it is empty in all languages.
- If there is a default field but it is empty, it is empty in all languages.
- If there is a default field and it is not an object, it has the specified value in all languages.
- If it is an object, it receives the entered value in the language determined by the language code.

### blocks
There are cases where we want to dynamically create multiple versions from certain settings, and this is where blocks come into play.
Users can dynamically create these versions without requiring the programmer to add additional settings or "setting groups."

For example:


```
{% schema %}
    {
        "attributes": {},
        "settings": [],
        "blocks": [
            {
                "type": "image",
                "name": "Image",
                "settings": [
                    {
                        "type": "text",
                        "name": "title",
                        "label": "Title of image",
                        "default": ""
                    },
                    {
                        "type": "image",
                        "name": "image",
                        "label": "Image",
                        "default": "no_image.jpg"
                    }
                ]
            }
        ]
    }
{% endschema %}
```

Within the blocks object, the **type** property can be set to anything, but it must be unique as it identifies the specific block. The **type** can only contain lowercase Latin letters, numbers, and underscores (_).
The **name** property is the user-friendly name of the **type** displayed in the admin interface.
The **settings** object inside the block functions in the same way as the **settings** object mentioned above.

The blocks object can be accessed in HTML through the **section Object**, for example:


```
{{ section.blocks }}
```

An example of iterating over blocks in Twig HTML:

```
<ul class="list">
{% for block in section.blocks %}
    {% if block.type == 'image' %}
    <li>{{ block.settings.title }}</li>
    {% endif %}
{% endfor %}
</ul>
```

#### Special fields within the Blocks settings object
Unique **name** properties that influence the appearance of the "Content" list in the admin interface.

<table>
<tr>
  <th>name</th>
  <th>purpose</th>
</tr>
<tr>
  <td>status</td>
  <td>Displays the status of the specific block instance in the list</td>
</tr>
<tr>
  <td>title</td>
  <td>Represents the name of the specific block instance in the list</td>
</tr>
<tr>
  <td>image</td>
  <td>Represents the image of the specific block instance in the list</td>
</tr>
</table>

### presets

This is an optional setting.

If we want to predefine the value of a field, we can use the "presets" property. Within this object, we can define initial values for each field. It's important to note that the system sets and saves the values defined in "presets" only when changing themes.

Using presets makes the most sense with blocks, where we want to establish sample elements for a created block.

For example, consider the block created above:

```
"presets": {
    "blocks": [
        {
            "type": "image",
            "settings": {
                "title": "Lorem ipsum",
                "image": "no_image.jpg"
            }
        }
    ]
}
```

Essentially, we have pre-created a block within our module.

**Important!** If a field is multilingual, meaning we specify among its settings that:

```
"multilang": true
```

In this case, the value of the `presets` field should be defined not as a string, but as an object based on the language code.

Example:


**Blokk schema:**

```
{% schema %}
    {
        "attributes": {},
        "settings": [],
        "blocks": [
            {
                "type": "image",
                "name": "Image",
                "settings": [
                    {
                        "type": "text",
                        "name": "title",
                        "multilang": true
                        "label": {
                            "hu": "Cím",
                            "en": "Title of something"
                        },
                        "default": ""
                    },
                    {
                        "type": "image",
                        "name": "image",
                        "label": "Image",
                        "default": "no_image.jpg"
                    }
                ]
            }
        ]
    }
{% endschema %}
```

**Correct definition of presets:**

```
"presets": {
    "blocks": [
        {
            "type": "image",
            "settings": {
                "title": {
                    "hu": "Magyar preset érték",
                    "en": "Preset value in english"
                },
                "image": "no_image.jpg"
            }
        }
    ]
}
```

**If a multilingual field's presets value is not an object, we will receive an "Unexpected error message" during module saving. The same applies in reverse: for a non-multilingual field, the preset value cannot be an object, otherwise an error will occur during saving.**

## Input Types
Currently available input types:

text  
textarea  
htmleditor  
image  
select  
checkbox  
number  
position  
datetime

### Single-line text input
We can use a single-line text input field when we want to display short text, such as a title or a name.

Input

<table>
<tr>
  <th>field</th>
  <th>value</th>
  <th>required</th>
</tr>
<tr>
  <td>type</td>
  <td>"text"</td>
  <td>required</td>
</tr>
<tr>
  <td>name</td>
  <td>Text (abcABC_)</td>
  <td>required</td>
</tr>
<tr>
  <td>label</td>
  <td>Text | Object</td>
  <td>required</td>
</tr>
<tr>
  <td>default</td>
  <td>Text | Object</td>
  <td>required</td>
</tr>
<tr>
  <td>help</td>
  <td>Text | Object</td>
  <td></td>
</tr>
<tr>
  <td>multilang</td>
  <td>Boolean</td>
  <td></td>
</tr>
<tr>
  <td>required</td>
  <td>Boolean</td>
  <td></td>
</tr>
</table>

Example:
```
{
    "type": "text",
    "name": "title",
    "label": "Title",
    "default": "My first section title",
    "help": "This is my first section title.",
    "multilang": true
}
```

### Multi-line text input field

We can use a multi-line text input field when we want to display longer text or HTML code.

Input

<table>
<tr>
  <th>field</th>
  <th>value</th>
  <th>required</th>
</tr>
<tr>
  <td>type</td>
  <td>"textarea"</td>
  <td>required</td>
</tr>
<tr>
  <td>name</td>
  <td>Text (abcABC_)</td>
  <td>required</td>
</tr>
<tr>
  <td>label</td>
  <td>Text | Object</td>
  <td>required</td>
</tr>
<tr>
  <td>default</td>
  <td>Text | Object</td>
  <td>required</td>
</tr>
<tr>
  <td>help</td>
  <td>Text | Object</td>
  <td></td>
</tr>
<tr>
  <td>multilang</td>
  <td>Boolean</td>
  <td></td>
</tr>
<tr>
  <td>required</td>
  <td>Boolean</td>
  <td></td>
</tr>
</table>

Example:
```
{
    "type": "textarea",
    "name": "description",
    "label": "Description",
    "default": "My first section description",
    "help": "This is my first section description.",
    "multilang": true
}
```

### HTML Editor
The HTML editor can be used similarly to the multi-line text input field for editing longer text or HTML code.

Input

<table>
<tr>
  <th>field</th>
  <th>value</th>
  <th>required</th>
</tr>
<tr>
  <td>type</td>
  <td>"htmleditor"</td>
  <td>required</td>
</tr>
<tr>
  <td>name</td>
  <td>Text (abcABC_)</td>
  <td>required</td>
</tr>
<tr>
  <td>label</td>
  <td>Text | Object</td>
  <td>required</td>
</tr>
<tr>
  <td>default</td>
  <td>Text | Object</td>
  <td>required</td>
</tr>
<tr>
  <td>help</td>
  <td>Text | Object</td>
  <td></td>
</tr>
<tr>
  <td>multilang</td>
  <td>Boolean</td>
  <td></td>
</tr>
<tr>
  <td>required</td>
  <td>Boolean</td>
  <td></td>
</tr>
</table>

Example:
```
{
    "type": "htmleditor",
    "name": "description",
    "label": "Description",
    "default": "My first section description",
    "help": "This is my first section description.",
    "multilang": true
}
```

### Image Upload

The image upload field is used for uploading images such as pictures, fav icons, or images used for slideshows.

Input

<table>
<tr>
  <th>field</th>
  <th>value</th>
  <th>required</th>
</tr>
<tr>
  <td>type</td>
  <td>"image"</td>
  <td>required</td>
</tr>
<tr>
  <td>name</td>
  <td>Text (abcABC_)</td>
  <td>required</td>
</tr>
<tr>
  <td>label</td>
  <td>Text | Object</td>
  <td>required</td>
</tr>
<tr>
  <td>default</td>
  <td>Text | Object</td>
  <td>required</td>
</tr>
<tr>
  <td>help</td>
  <td>Text | Object</td>
  <td></td>
</tr>
<tr>
  <td>multilang</td>
  <td>Boolean</td>
  <td></td>
</tr>
<tr>
  <td>required</td>
  <td>Boolean</td>
  <td></td>
</tr>
</table>

Example:
```
{
    "type": "image",
    "name": "image",
    "label": "Image",
    "default": "My first section image",
    "help": "This is my first section image.",
    "multilang": true
}
```

Using the [asset_image_url](../theme-global/02_global_functions.md#asset-image-url) Function in Twig Templates

### Dropdown Menu (select)
The dropdown type is used to present various options to the user.
For example, they can select which products they want to display on the product page.

The dropdown menu must be provided with an **options** object listing the selectable values.


Input

<table>
<tr>
  <th>field</th>
  <th>value</th>
  <th>required</th>
</tr>
<tr>
  <td>type</td>
  <td>"select"</td>
  <td>required</td>
</tr>
<tr>
  <td>name</td>
  <td>Text (abcABC_)</td>
  <td>required</td>
</tr>
<tr>
  <td>label</td>
  <td>Text | Object</td>
  <td>required</td>
</tr>
<tr>
  <td>default</td>
  <td>Text | Object</td>
  <td>required</td>
</tr>
<tr>
  <td>help</td>
  <td>Text | Object</td>
  <td></td>
</tr>
<tr>
  <td>multilang</td>
  <td>Boolean</td>
  <td></td>
</tr>
<tr>
  <td>required</td>
  <td>Boolean</td>
  <td></td>
</tr>
<tr>
  <td>options</td>
  <td>Object</td>
  <td>required</td>
</tr>
</table>

Example:
```
{
    "type": "select",
    "name": "columns",
    "label": "Columns",
    "default": "2",
    "help": "This is my first section select.",
    "options": [
        {
            "value": "1",
            "label": "one column"
        },
        {
            "value": "2",
            "label": "two columns"
        },
        {
            "value": "3",
            "label": "three columns"
        }
    ],
    "multilang": true
}
```

### Checkbox
Using the checkbox type, you can toggle settings on and off, for example, displaying or hiding elements on the page.


Input

<table>
<tr>
  <th>field</th>
  <th>value</th>
  <th>required</th>
</tr>
<tr>
  <td>type</td>
  <td>"checkbox"</td>
  <td>required</td>
</tr>
<tr>
  <td>name</td>
  <td>Text (abcABC_)</td>
  <td>required</td>
</tr>
<tr>
  <td>label</td>
  <td>Text | Object</td>
  <td>required</td>
</tr>
<tr>
  <td>default</td>
  <td>Boolean | Object</td>
  <td>required</td>
</tr>
<tr>
  <td>help</td>
  <td>Text | Object</td>
  <td></td>
</tr>
<tr>
  <td>multilang</td>
  <td>Boolean</td>
  <td></td>
</tr>
<tr>
  <td>required</td>
  <td>Boolean</td>
  <td></td>
</tr>
</table>

Example:
```
{
    "type": "checkbox",
    "name": "show_element",
    "label": "Show element",
    "default": true,
    "help": "This is my first section checkbox.",
    "multilang": true
}
```

### Number Input Field
The number input field accepts only numeric characters.

Input

<table>
<tr>
  <th>field</th>
  <th>value</th>
  <th>required</th>
</tr>
<tr>
  <td>type</td>
  <td>"number"</td>
  <td>required</td>
</tr>
<tr>
  <td>name</td>
  <td>Text (abcABC_)</td>
  <td>required</td>
</tr>
<tr>
  <td>label</td>
  <td>Text | Object</td>
  <td>required</td>
</tr>
<tr>
  <td>default</td>
  <td>Number | Object</td>
  <td>required</td>
</tr>
<tr>
  <td>help</td>
  <td>Text | Object</td>
  <td></td>
</tr>
<tr>
  <td>multilang</td>
  <td>Boolean</td>
  <td></td>
</tr>
<tr>
  <td>required</td>
  <td>Boolean</td>
  <td></td>
</tr>
</table>

Example:
```
{
    "type": "number",
    "name": "number",
    "label": "Number",
    "default": 156,
    "help": "This is my first section number.",
    "multilang": true
}
```

### Position Type
When setting the type to `position`, it allows us to select system positions from a dropdown menu. The difference between a dropdown menu and the position type is that the position type has predefined values. These predefined values are defined in the `positions` object of the `settings.json` file.


Input

<table>
<tr>
  <th>field</th>
  <th>value</th>
  <th>required</th>
</tr>
<tr>
  <td>type</td>
  <td>"position"</td>
  <td>required</td>
</tr>
<tr>
  <td>name</td>
  <td>Text (abcABC_)</td>
  <td>required</td>
</tr>
<tr>
  <td>label</td>
  <td>Text | Object</td>
  <td>required</td>
</tr>
<tr>
  <td>default</td>
  <td>Text | Object</td>
  <td>required</td>
</tr>
<tr>
  <td>help</td>
  <td>Text | Object</td>
  <td></td>
</tr>
<tr>
  <td>required</td>
  <td>Boolean</td>
  <td></td>
</tr>
</table>

Example:
```
{
    "type": "position",
    "name": "position",
    "label": "Position",
    "default": "home",
    "help": "You can change sections position ."
}
```

### Date Time Picker

Using `datetime`, we can place an input field with a user-friendly date and time selector interface.  
In the `default` field, you can specify an empty string or a date-time format in `YYYY-MM-DD HH:mm:ss` format (e.g., `"default": ""` or `"default": "2019-01-01 12:00:00"`).  
Upon saving, values are stored in this format.  
If the field is not required (`"required": false`), a delete button will also appear.
s.

Input

|field|value|required|
|:---:|:---|:---:|
|type|`"datetime"`|required|
|name|Text (abcABC_)|required|
|label|Text &#124; Object|required|
|default|Text (`""` &#124; `"2019-01-01 12:00:00"`)|required|
|help|Text &#124; Object||
|required|boolean||


Example:
```json
{
  "type": "datetime",
  "name": "a_datetime_field",
  "label": {
    "hu": "Válasszon egy időpontot",
    "en": "Select a date and time"
  },
  "default": "2019-01-01 12:00:00",
  "help": {
    "hu": "Segítség szöveg magyarul",
    "en": "Help text in English"
  }
}
```

**Warning!**  
In Twig template, `{{ ""|date('Y-m-d H:i:s') }}` will return the current date and time.  
Therefore, if the field is not required and we save an empty value, this needs to be handled separately!

### Colorpicker
Using the color picker type, you can select a color from a palette. This is useful for customizing visual elements, such as changing background colors or text highlights.

Input

<table>
<tr>
  <th>field</th>
  <th>value</th>
  <th>required</th>
</tr>
<tr>
  <td>type</td>
  <td>"colorpicker"</td>
  <td>required</td>
</tr>
<tr>
  <td>name</td>
  <td>Text (abcABC_)</td>
  <td>required</td>
</tr>
<tr>
  <td>label</td>
  <td>Text | Object</td>
  <td>required</td>
</tr>
<tr>
  <td>default</td>
  <td>Text | Object</td>
  <td></td>
</tr>
<tr>
  <td>help</td>
  <td>Text | Object</td>
  <td></td>
</tr>
<tr>
  <td>multilang</td>
  <td>Boolean</td>
  <td></td>
</tr>
<tr>
  <td>required</td>
  <td>Boolean</td>
  <td></td>
</tr>
</table>

Example:
```json
{
  "type": "colorpicker",
  "name": "color",
  "label": {
    "hu": "Szöveg cím",
    "en": "Text color"
  },
  "default": "#000000",
  "help": {
    "hu": "Segítség szöveg magyarul",
    "en": "Help text in English"
  }
}
```

## Using Multilingual Fields
In case of multilingual fields, the **multilang** property should be set to true.  
The label, default, help, and options properties can accept multilingual values.

Example:

```
{
    "type": "select",
    "name": "status",
    "label": {
      "hu": "Állapot",
      "en": "Status"
    },
    "default": "0",  
    "help": {
      "hu": "Segítség szöveg magyarul",
      "en": "Help text in English"
    },
    "options": [
        {
            "value": "0",
            "label": {
                "hu": "Letiltott",
                "en": "Disabled"
            }
        },
            {
            "value": "1",
            "label": {
                "hu": "Engedélyezett",
                "en": "Enabled"
            }
        }
    ]
}
```
