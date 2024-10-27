# Flask

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

