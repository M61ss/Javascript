# Flask

> [!WARNING]
>
> For detailed informations, like imports, functions, implementations, etc., see sample application and try to run it.

## Dependencies

```shell
pip install flask sqlalchemy
```

## Blocks

You can create html templates and reuse them.

This is possible because Flask provides a syntax to define which pieces of the template have to be replaced with a particular code provided by another file.

**`file1.html`**:

```html
<!-- stuff -->
{% block block_name %}  {% endblock block_name %}
<!-- stuff -->
```

**`file2.html`**:

```html
{% extends 'file1.html' %}

{% block block_name %}
<!-- CODE -->
{% endblock block_name %}

<!-- other blocks here -->
```

All is written at the place of `<!-- CODE -->`, will replace the block inside `file1.html` and the site works as well.

So, the template can be reused to build the entire site extending it, implementing features in low level modules.

## Static contents

Static contents are all static resources of the site. They have to be saved inside the `static` folder, which have to be placed inside the root folder of the site.
\
For example, we can access data stored in `static/css/main.css` file using this notation:

**`file1.html`**:

```html
<!-- stuff -->
<link rel="stylesheet" href="{{ url_for('static', filename='css/main.css') }}">
<!-- stuff -->
```

It works at the same way for all resources, so also for `.js` files.
