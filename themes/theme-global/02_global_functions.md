# Functions

The ShopRenter uses the [TWIG](https://twig.symfony.com) template engine for theme files. Therefore, every tpl file is based on TWIG syntax. In addition to the basic functions and filters shown in the TWIG documentation, ShopRenter provides custom functions and filters to facilitate frontend development.

## add_body_class()

Using `add_body_class`, you can add a class to the `<body>` tag. It expects a string type parameter.

### Syntax

```
{{ add_body_class(className) }}
```

Example:

```twig
{{ add_body_class("new-class") }}
```

Output:

```
<body class="page-body new-class">
```

## asset()

The `asset` function complements the file path with the CDN domain and version.

### Syntax

```
asset(filePath)
```

### Arguments

**filePath**: The file path from the root directory.

### Return value

Returns the full URL as a string.

Example:

```twig
<script src="{{ asset('catalog/view/javascript/filter/mobile_filter.js') }}"></script>
```

Output:

```
<script src="https://[BOLTNEV].cdn.shoprenter.hu/catalog/view/javascript/filter/mobile_filter.js?v=[TIMESTAMP]"></script>
```

## asset_image_url()

The `asset_image_url` function requires only the image file name and complements it with the CDN domain and version. It is recommended for uploading images in [dynamic modules](../theme-development-tools/02_theme_sections.md).

### Syntax

```
asset_image_url(fileName)
```

### Arguments

**fileName**: The name of the file to display with the full URL.

### Return value

Returns the full URL as a string.

Example:

```twig
<img src="{{ asset_image_url('kepfajl.jpg') }}" />
```

Output:

```html
<img src="https://[BOLTNEV].cdn.shoprenter.hu/custom/boltnev/image/data/kepfajl.jpg?v=[TIMESTAMP]" />
```

## add_script_asset()

The `add_script_asset` function is used to add system JavaScript files in TPL files. The function automatically complements the file URL with the CDN domain and a version parameter, creating a `<script>` tag. This function ensures that the necessary JS files are properly included during page load for the system functions to work correctly.

### Syntax

```
{{ add_script_asset(filePath) }}
```

### Arguments

**filePath**: The file path from the root directory.

### Return value

Returns the full URL as a string.

Example:

```twig
{{ add_script_asset('catalog/view/javascript/addtocart/addtocart.js') }}
```

Output:

```
<script src="https://[BOLTNEV].cdn.shoprenter.hu/catalog/view/javascript/addtocart/addtocart.js?v=[TIMESTAMP]"></script>
```

- :red_circle: IMPORTANT: Please do not remove or modify files added this way. These scripts are essential for the proper functioning of the system.
- :red_circle: IMPORTANT: In certain cases, system-level grouping and concatenation occur for files added with add_script_asset. These files are accessible under a different name after minification to optimize loading times and performance.


## isDeviceType()

If you want to create different appearances for mobile devices and prefer not to display HTML code in the template, you can use the `isDeviceType` function to create conditions in the template. 

### Syntax

```
isDeviceType(deviceType)
```

### Arguments

**deviceType**: Specify the device name. Possible values: mobile, tablet, desktop.

### Return value

The function returns a boolean value: true or false.


Example:

```twig
{% if isDeviceType('desktop') %}
    Only appears on desktop
{% else if isDeviceType('mobile') %}
    <div>[-.-]</div>
{% endif %}
```

Output when viewed on a PC:

```html
Only appears on desktop
```

Output when viewed on a mobile phone:

```html
<div>[-.-]</div>
```
