# 05 - Objects <!-- omit from toc -->

- [Objects](#objects)
  - [Accessing object properties](#accessing-object-properties)
  - [Update object properties](#update-object-properties)
  - [Add object properties](#add-object-properties)
  - [Delete object properties](#delete-object-properties)
  - [Check object properties](#check-object-properties)
  - [Object array](#object-array)
  - [Nested object](#nested-object)
  - [`freeze`](#freeze)
  - [Destructuring assignment](#destructuring-assignment)
  - [Simple fields](#simple-fields)
  - [Declarative functions](#declarative-functions)
- [Class](#class)
  - [Getters and setters](#getters-and-setters)
- [Random numbers](#random-numbers)
  - [Random whole number](#random-whole-number)

> [**RETURN to full index**](Index.md)

## Objects

```js
var someObject = {
  "name": "something",
  "number": 43,
  "array": [23, "other"],
  3: "something identified by a number",
  "property with spaces": true,
  property: 453
};
```

The object data type can contain both built-in objects and user defined objects.
\
Built-in object types can be:

- `object`; 
- `array`; 
- `date`;
- `map`;
- `set`;
- `intarray`;
- `floatarray`;
- `promise`; 
- ...more. 

> [!IMPORTANT] const objects
>
> Like arrays, it is impossible to replace a `const` object, but it is possible to modify its properties:
>
> ```js
> const obj = {
>   "property": "value"
> };
> obj.property = "another value";
> // obj = anotherObj;  <-  ERROR
> ```

> [!WARNING] Reference to object
>
> Be careful! Variables contains reference to objects, so copying an object inside a variable means that, if you modify properties of that copy, then you will modify also the origial object properties:
> ```js
> var obj1 = {
>   prop: "value" 
> };
> var obj2 = obj1;
> obj2.prop = "change";
> ```
>
> Then, the `obj2`'s change will reflect on `obj1` property.

### Accessing object properties

- Regular property:
  
  ```js
  var objectProperty = someObject.name;
  ```
- Property identified by a number:

  ```js
  var accessKey = 3;
  var objectProperty = someObject[accessKey];
  ```
  
- Property of which name contains one or more spaces (brackets notation):

  ```js
  var objectProperty = someObject["property with spaces"];
  ```

### Update object properties

```js
someObject.name = "Another name";
```

### Add object properties

To add a property to an existing object, it is possible to do this:

```js
someObject.newProperty = "Something other";
// Alternatively
someObject["new property"] ="Something other"; 
```

Then, the object is updated and permanently has `newProperty`.

### Delete object properties

```js
delete someObject.newProperty;
```

Then, `newProperty` has permanently removed from `someObject`.

> [!TIP] Lookup tables
>
> ```js
> var lookup = {
>   "first": "value1",
>   "second": "value2"
> }
> 
> var someInput = "second";
> var retrivedValue = lookup[someInput];
> ```
>
> So I can use objects as lookup tables, like Java's `map`.
> \
> Notice that this is why double quotes in object property declarations are useful.

### Check object properties

It exists a method shared by all `object` which can check if an object has a property:

```js
someObject.hasOwnProperty(someProperty);
```

It returns a `boolean`.

### Object array

It is possible to create an array of objects:

```js
var multipleObjects = [
  {
    name: "some name",
    second: "other"
  },
  {
    name: "another name",
    second: "something",
    third: "some other value"
  }
]
```

> [!NOTE]
>
> It is not required that objects have same properties.

### Nested object

```js
var someObject = {
  "nested object": {
    "key": "value"
  },
  property: "something"
}
```

As you can see, there is a property which is an object with its own properties.

### `freeze`

To prevent objects mutations, it is possible to "freeze" them:

```js
const MATH_CONSTANTS = {
  PI: 3.1415
};

Object.freeze(MATH_CONSTANTS);
```

It will be impossible to modify `MATH_CONSTANTS`'s fields.

### Destructuring assignment

```js
var obj = {
  property1: 22,
  property2: 54
}
const { property1 : someVariable } = obj;
```

In this piece of code we declare `someVariable` and assign to it `property1`. 
\
It is a quicker way to assign object properties to variables.

Destructuting works also with nested objects:

```js
var obj = {
  property1: 22,
  property2: {
    nestedprop: 32
  }
}
const { property1 : { nestedprop : someVariable } } = obj;
```

### Simple fields

It is possible to create functions that returns object in a very compact way:

```js
const createPerson = (name, age) => ( { name, age } );
```

### Declarative functions

It is possible in javascript to declare and assign a function to an object property very fast:

```js
var obj = {
  prop: 1,
  fun(param) {
    // ...
  }
}
```

`fun` is an `obj` property for all intents and purposes.

## Class

An object can be created also as `class`, so that you can instantiate a class, like Java, and you have the possibility to use a constructor, getters and setters:

```js
class SomeClass {
  constructor(param) {
    this.prop = param;
  }
}

var variable = new SomeClass("parameter");
```

> [!NOTE] 
>
> There is no need to declare `prop` because it is created calling `this.prop`.

> [!NOTE] Strict mode
>
> All classes are in strict mode since their declaration by default. 

There is another way to build class, even if it is terrible, so **DO NOT DO THIS**:

```js
var SomeConstructor = function(prop) {
  this.prop = prop;
}

var someClass = new SomeConstructor("don't do this please");
```

### Getters and setters

```js
class SomeClass {
  constructor(param) {
    this.prop = param;
  }

  get getProperty() {
    return this.prop;
  }

  set setProperty(param) {
    this.prop = param
  }
}
```

## Random numbers

```js
var rnd = Math.random();
```

> [!WARNING]
> This random function returns a random number between 0 and 1, **excluding** 1.

### Random whole number

For example, we want a whole number between 0 and 19:

```js
var wholeRnd = Math.floor(Math.random() * 20);
```

`floor` rounds the result of the expression passed as argument to the nearest whole number.

> [!TIP] Range
>
> ```js
> var min = 3;
> var max = 9;
> var rndInRange = Math.floor(Math.random() * (max - min + 1)) + min;
> ```

