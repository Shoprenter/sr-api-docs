# Tags

## jshrink

Using jshrink, you can minimize your JavaScript code, reducing the size of the source code and speeding up loading times.

### Usage
In the TPL file where JavaScript code is used, wrap your code between `{% jshrink %}` and `{% endjshrink %}` tags. The code between these tags will automatically be minified using jshrink.

### Example

<table>
<tr>
    <td>Code:</td>
    <td>Output:</td>
</tr>
<tr>
<td>

```twig
{% jshrink %}
    <script>
        function myFunction() {
            console.log('Hello');
            // JavaScript kód
        }
    </script>
{% endjshrink %}
```

</td>
<td>

```
<script>function myFunction(){console.log('Hello');}</script>
```

</td>
</tr>
</table>

---

## schema

The `{% schema %}` tag is a special tag used exclusively for Dynamic modules in templates.

For more information, refer to the [Dynamic modules](../theme-development-tools/02_theme_sections.md#using-schema-in-dynamic-modules) documentation.

