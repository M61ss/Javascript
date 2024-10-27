# Flask <!-- omit from toc -->

> [!WARNING]
>
> For detailed informations, like imports, functions, implementations, etc., see sample application and try to run it.

- [Dependencies](#dependencies)
- [Blocks](#blocks)
- [Code blocks](#code-blocks)
- [`@app.route`](#approute)
- [Static contents](#static-contents)
- [Database (Flask extention)](#database-flask-extention)
- [`for` loop](#for-loop)
- [`if` statement](#if-statement)
- [Documentation](#documentation)

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

## Code blocks

It is possible to expand a Python line of code to a string: 

```html
{{ print("Hello") }}
```

It expands to `Hello`.

## `@app.route`

This decorator takes one mandatory parameter, which is the hierarchical position, called "URL rule", of the page returned by the decorated function. 

_Example_:

Let's take a slice of code of the sample application

```html
<!-- ... -->
<td>
    <a href="/delete/{{ task.id }}">Delete</a>
    <br>
    <!-- ... -->
```

Here I call `task.id` which expands to a string of the unique task id, so `href` goes to that URL...

```py
@app.route('/delete/<int:id>')
def delete(id):
    task_to_delete = Todo.query.get_or_404(id)
    # ...
```

... which is associated to this function, that requires a parameter in input. So, this parameter is filled with the content of `<int:id>` provided by `task.id`. In this example we need to distinguish tasks by their id to be able to delete the correct one.

So, to make a function accessible from a webpage on Flask, we need to assign to that function an URL and, if needed, we can add a variable parameter, so that we can pass that to the function.

It is intuitive that `index.html` is loaded at startup because Flask loads first the root URL, which is `/` by default.

Other parameters of `@app.route` should be added only if needed, see [documentation](https://flask.palletsprojects.com/en/stable/api/#flask.Flask.route).

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

## Database (Flask extention)

> [!NOTE]
>
> A database is not required to make the application work. Anyway, it is very common to use a database and Flask provides an extention, called "Flask-SQLAlchemy", to easily manipulate SQLAlchemy databases.

To use comfortably SQLAlchemy database, add these lines inside `app.py`:

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

```html
{% for element in elements %}
    <!-- content -->
{% endfor %}
```

It is equivalent to copy and paste the same code sequentially, but this way you can automate and control the number of repetitions.

## `if` statement

```html
{% if tasks|lenght < 1 %}
    <!-- content -->
{% else %}
    <!-- content -->
{% endif %}
```

`|` is a Jinja2 filter. It returns the length of a list.

The content of the `if` will be rendered only if the condition is satisfied.

## Documentation

[Flask - Documentation](https://flask.palletsprojects.com/en/stable/)
