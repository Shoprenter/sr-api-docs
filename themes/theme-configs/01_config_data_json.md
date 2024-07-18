# config.data.json

Contains the necessary data for theme configuration in JSON format.

It consists of two parts: assets and presets:

```json
{
 "assets": {},
 "presets": {}
}
```

## assets

In the assets object, images associated with the theme are recorded. These include thumbnails that appear on the theme selection page in the admin interface.

Example:

```json
{
 "assets": {
  "base": {
   "thumb": "starter2.jpg"
  },
  "blue": {
   "thumb_small": "starter2_blue.jpg",
   "thumb_big": "starter2_blue_n.jpg"
  },
  "green": {
   "thumb_small": "starter2_green.jpg",
   "thumb_big": "starter2_green_n.jpg"
  }
 }
}
```

## presets

The presets object contains the color variables associated with the theme. Based on these variables, the content of the **Theme Colors** tab is created on the **Theme Customization** page.

Each variable is associated with either a ColorPicker or BackgroundPicker.
If the variable name has the postfix color, a ColorPicker appears; if the postfix is background, a BackgroundPicker appears; and if neither, then a text-type input field appears. The ColorPicker allows selecting a single color, while the BackgroundPicker enables specifying gradients.

<table>
  <tr>
    <th>Postfix</th>
    <th>Appearance</th>
  </tr> 
  <tr>
    <td>-color</td>
    <td>ColorPicker</td>
  </tr>
  <tr>
    <td>-background</td>
    <td>BackgroundPicker</td>
  </tr>
  <tr>
    <td>none/td>
    <td>input['type=text']</td>
  </tr>
</table>   


Example:

```json
{
    "presets": {
        "base": {
            "cart-icon": "50",
            "global-border-radius": "0",
            "body-background": "#ffffff",
            "global-font-color": "#8e8e8e",
            "global-font-light-color": "#ffffff",
            "global-light-color": "#ffffff",
            "global-dark-color": "#2d2d2d",
            "input-border-color": "#ebebeb",
            "input-color": "#2d2d2d",
            "input-background": "#ffffff"
        },
        "blue": {
            "global-color": "#3da0e3",
            "global-hover-color": "#2487CA",
            "link-color": "#3da0e3",
            "link-hover-color": "#2487CA"
        },
        "green": {
            "global-color": "#68a742",
            "global-hover-color": "#4F8E29",
            "link-color": "#68a742",
            "link-hover-color": "#4F8E29"
        },
        "custom": {
            "global-color": "#ffcc00"
        }
  }
}
```

The `presets` object contains direct children which include various color variations, as well as the **base** and **custom**
objects which are special reserved names. The **base** object contains base variables that remain consistent across all color variations.
In the example, the **blue** and **green** variations contain variables where the color variation differs.
The assets and presets objects include the same variations. If an admin user modifies colors on the Theme Colors
page, the modified value is stored in the **custom** object.

When using **Theme Copy**, the variations (blue, green) are not copied over. Instead, the copied theme, for example
if it was blue, moves the blue object's variables into the **base** object.

## Usage
The variables can be accessed in any tpl file using the **get** method of the [settings](../theme-global/04_global_objects.md#settings) object.


```
{{ settings.get('global-color', '#000') }}
```

Variables retrieved from the settings object using the get method are best passed through CSS variables in the
pseudo-class. This approach makes them easily usable in any CSS file.

```
<style>
:root {
    --main-color: {{ settings.get('global-color', '#000') }};
}
</style>
```
base.css:
```css
body {
 color: var(--main-color);
}
```
