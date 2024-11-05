# Theme editor

The Theme editor is a new feature in the ShopRenter system that allows customers to implement their unique design requirements independently or with external assistance! This feature is currently in beta and can be enabled in the Labor menu of the ShopRenter store admin interface. Developers have the option to seek technical assistance from the [Storefront](mailto:storefront@shoprenter.hu) team.

:red_circle: **IMPORTANT:** Editing theme files is the responsibility of the designer creating the custom theme. Shoprenter does not assume responsibility and cannot provide support for stores using custom themes. If there are technical issues related to the theme, it is the responsibility of the custom theme creator to resolve them. ShopRenter only guarantees and takes responsibility for its own themes and developments.

## General Information:
The Theme editor is accessible on the **Choose Theme** page under the **Actions** button for selected templates. It can also be accessed from **Settings** > **Appearance** > **Theme editor** in the top menu.

The Theme editor is structured with template files associated with the theme on the left side. This includes stylesheets and configuration files. HTML codes are available in template files with a .tpl extension, utilizing the [TWIG](https://twig.symfony.com) template engine by ShopRenter.

## Creating Custom Designs, Theme Duplication Feature:
To create a new custom design, click on the **duplicate theme** button within **Actions**. In the popup window, provide a name for the theme and click on the duplicate theme button. This will create a new theme with the specified name, accessible again with the Theme editor button.

The **config/config.data.json** file defines the theme's color variables. This means that properties defined in this JSON object determine the colors used in our theme.

## File Search
Located in the top left corner of the Theme editor is the file search function. You can search for theme files based on keywords, making it easier to access files.

## Version Management
To ensure safe use of files and to test modifications, version tracking is applied to all files used in the Theme editor. Above the editor interface of opened files, there is a link for **Previous Versions**. Clicking here allows selection of a previous version or even the original! Once selected, the content of that version loads into the editor, and using the save button will make that version active.

## Creating New Files
In the directory containing theme files, there is an option to create new files. The file name does not need an extension. These new files can be inserted into a specific template file using the Twig include function.

## Keyboard Shortcuts
To facilitate developer work within the editor interface, consider using the following keyboard shortcuts:

- **CTRL + F / Command + G**

  Keyword search. Enter the keyword in the search popup and press enter. Use F3 / Command + G for the next match and SHIFT + F3 / Command + Shift + G for the previous match.

- **CTRL + G / Control + G**

  After pressing the button, a popup window appears where you can enter the line number you want to jump to in the code. For example, entering 1200 jumps to the 1200th line.

- **F11**

  Pressing F11 enables full-screen mode for the Theme editor, utilizing the entire screen for easier code modification.

- **CTRL + S**

  Save the current file using this keyboard shortcut.
