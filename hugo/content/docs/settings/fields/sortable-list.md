---
aliases:
- "/docs/front-matter-fields/sortable-list-field/"
title: Sortable List Field
publishdate: 2017-12-31 04:00:00 +0000
expirydate: 2030-01-01 04:00:00 +0000
date: 2017-12-31 00:00:00 -0400

---

![](/uploads/2018/01/sortable-list-preview.png)

A list of values with drag & drop reordering.

## Options

- **General**
  - _Label_ &mdash; the human-friendly label shown above the input field in the editor.
  - _Name_ &mdash; the key stored in your content’s front matter, used to access it in your templates.
  - _Description_ &mdash; a human friendly description of what the field does and/or instructions for your editors.
  - _Hidden_ &mdash; hides the field in the editor, but allows developers to set default values or maintain the field for legacy purposes.
- **Widget**
  - _Text/Select_ &mdash; toggles the sortable list to allow text input, or to restrict options to a [select field](/docs/settings/fields/select)
- **Validation**
  - _Minimum_ &mdash; the lowest number of items that must be added to this field.
  - _Maximum_ &mdash; the highest number of items that can be added to this field.

## Templating
You can access this field in your templates using the field’s `name`:

#### Hugo
```
<p>{{ delimit .Params.ingredients ", " }}</p>
```

{{% tip %}}
Easily display a comma delimited string using the `delimit` filter
{{% /tip %}}

```
<h2>Ingredients:</h2>
<ul>
{{ range .Params.ingredients }}
  <li>{{ . }}</li>
{{ end }}
</ul> 
```

#### Jekyll
```
<p>{{ page.ingredients | array_to_sentence_string }}</p>
```

{{% tip %}}
Easily display a comma delimited string using the `array_to_sentence_string` filter
{{% /tip %}}

```
<h2>Ingredients:</h2>
<ul>
  {% for ingredient in page.ingredients %}
    <li>{{ ingredient }}</li>
  {% endfor %}
</ul>
```

## Config Files
You can configure this field in _Front Matter Template_ [Config Files](/docs/settings/config-files/) as follows:

```
type: list
name: [String]
label: [String]
description: [String]
hidden: [true|false]
default:
- [String]
config:
  use_select: [true|false]
```

### Example
```
type: select
name: ingredients
label: Ingredients
description: Provide ingredients for this recipe
hidden: false
default:
- 1 cup water
config:
    use_select: [false]
```

{{% tip %}}
See the [select field](/docs/settings/fields/select) documentation for configuring the select when `config.use_select` is set to `true`
{{% /tip %}}