# Flask

> [!WARNING]
>
> For detailed informations, like imports, functions, implementations, etc., see sample application and try to run it.

## Dependencies

```shell
pip install flask sqlalchemy
```

## `@app.route`

What is this?

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

## Code blocks

It is possible to expand a Python line of code to a string: 

```html
{{ print("Hello") }}
```

It expands to `Hello`.

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

## Database

To use the database, you need to add these lines inside `app.py`:

```py
# Necessary to avoid warning using SQLAlchemy from the Python shell
app.config['SQLALCHEMY_TRACK_MODIFICATIONS'] = False

# ... other configs ...

# Necessary to use the database in the Python shell
app.app_context().push()
```

Then, to create the database, open the Python shell and run these instructions:

```py
from app import db
db.create_all()
```

## `for` loop

It is possible to iterate some html code using a `for` loop:

```html
{% for element in elements %}
    <!-- content -->
{% endfor %}
```

It is equivalent to copy and paste the same code sequentially, but this way you can automate and control the number of repetitions.
