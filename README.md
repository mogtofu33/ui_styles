# Layout Builder Classes

This module allow site builders to attach a style to apply to layout builder blocks and sections.

A "style" is just a list of concurrent CSS classes.

Heavily inspired by [drupal/layout\_builder\_styles](https://www.drupal.org/project/layout_builder_styles) module, with those differences:

* styles are plugin-based instead of being config-entity-based, to be created and managed by the themer (inside a YML file), and then only used by the site builder in the layout builder interface (see also: [#3107972](https://www.drupal.org/project/layout_builder_styles/issues/3107972))
* styles are organized as groups of classes, because some styles should only allow one class to be chosen (see also: [#3075502](https://www.drupal.org/project/layout_builder_styles/issues/3075502))
* with a preview page, like [ui_patterns_library](https://ui-patterns.readthedocs.io/en/8.x-1.x/content/patterns-definition.html), available there: /styles 
* on rendering, classes are attached to the first render array inside the block, instead of being attached to the block wrapper

## Example of a plugin declaration in the YML file

```
colors_background_color:
  label: Background color
  description: Similar to the contextual text color classes, easily set the background of an element to any contextual class.
  options:
    bg-primary: Primary
    bg-secondary: Secondary
    bg-success: Success
    bg-danger: Danger
    bg-warning: Warning
    bg-info: Info
    bg-light: Light
    bg-dark: Dark
    bg-white: White
    bg-transparent: Transparent
  previewed_with:
    - border
    - p-2
```

Where:

* `colors_background_color` is the plugin ID
* 'label' is used in the library and the layout builder forms
* 'description' is only used in the library
* 'options' is the list of all classes and labels of the style
* 'previewed_with' is a list of classes used in the library to pimp the preview

## A perfect combo with ui_patterns

[ui\_patterns\_bootstrap](https://github.com/pdureau/ui_patterns_bootstrap) theme is a example of using both [ui\_patterns](https://www.drupal.org/project/ui_patterns) and [layout\_builder\_classes](https://github.com/pdureau/layout_builder_classes) to implements Bootstrap 4 designs:

![Overview](doc/schema.png)