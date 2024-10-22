# 05 - Objects <!-- omit from toc -->

- [Objects](#objects)
  - [Object types](#object-types)
  - [Accessing object properties](#accessing-object-properties)
    - [Brackets notation](#brackets-notation)
  - [Update object properties](#update-object-properties)
  - [Add object properties](#add-object-properties)
  - [Delete object properties](#delete-object-properties)
  - [Check object properties](#check-object-properties)
  - [Object array](#object-array)
  - [Nested object](#nested-object)
  - [`freeze`](#freeze)
  - [Destructuring assignment](#destructuring-assignment)
  - [Simple fields](#simple-fields)
  - [Methods](#methods)
  - [Constructors](#constructors)
  - [Static methods](#static-methods)
- [Class](#class)
  - [Getters and setters](#getters-and-setters)
- [`Symbol`](#symbol)
  - [`Symbol` as property](#symbol-as-property)
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
> 
> ```js
> var obj1 = {
>   prop: "value" 
> };
> var obj2 = obj1;
> obj2.prop = "change";
> ```
>
> Then, the `obj2`'s change will reflect on `obj1` property.

### Object types

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
- ...more, see [MDN Docs - Built-in objects](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects).

> [!WARNING]
>
> Anyway, the `typeof` operator will return `object` if tested on any type of objects listed above.

### Accessing object properties
  
```js
var objectProperty = someObject.name;
```

#### Brackets notation

Objects are called also "associative arrays" because it is possible to access their properties using an array-like notation, called "brackets notation".
\
That notation is mandatory for:

- Properties identified by a number:

  ```js
  var accessKey = 3;
  var objectProperty = someObject[accessKey];
  ```
  
- Properties identified by a string which contains one or more spaces:

  ```js
  var objectProperty = someObject["identifier with spaces"];
  ```

- Properties identified by a `symbol`: 

  ```js
  var mySymbol = new Symbol("id");
  var objectProperty = someObject[mySymbol];
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

### Methods

```js
var obj = {
  prop: 1,
  prop2: function(param) {
    // ...
  }
}
```

It is possible in javascript to declare and assign a function to an object property very fast:

```js
var obj = {
  prop: 1,
  fun(param) {
    // ...
  }
}
```

`fun` is an `obj` property. It works like Java's methods.

> [!WARNING]
>
> `object` is not wrapped by `Object`, however, it inherits `Objects.prototype`, which is a set of methods of `Object`; for example, `toString` or `hasOwnProperty`.

### Constructors

Since in javascript objects has no constructor, it is possible to create functions which works as constructors as well:

```js
function SomeConstructor(prop) {
  this.prop = prop;
  // ...
}
var someObject = new SomeConstructor("parameter");
```

### Static methods

Since constructors are functions, but functions are objects, so it is not necessary to assign them to a variable to access its methods or properties:

```js
function SomeConstructor(prop) {
  this.prop = prop;
}
SomeConstructor.prop2 = "value";
```

`prop2` has been added to `SomeConstructor` statically.

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

## `Symbol`

`Symbol` is a built-in object whose constuctor returns a `symbol`. This is the unique way to create a `symbol`.

```js
var sym1 = Symbol("string");
```

Each `Symbol` is unique:

```js
var sym1 = Symbol("string");
var sym2 = Symbol("string");
sym1 === sym2     // FALSE
```

It is possible to retrive a `symbol` previously created knowing the `"key"` used to generate it:

```js
var sym = Symbol("id");
// ...
var copyOfSym = Symbol.for("id");
```

At the same way, it is possible to retrive the `"key"` from a `symbol`:

```js
var sym = Symbol("id");
// ...
var keyOfSym = Symbol.keyFor(sym);
```

> [!WARNING]
>
> It is impossible to instantiate a `Symbol` with the `new` keyword. 
> \
> The only way to create a `Symbol` wrapper is:
>
> ```js
> var sym = Symbol("str");
> var symWrapper = Object(sym);
> ```

More at [MDN - Symbols](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol).

### `Symbol` as property

A `symbol` can be an identifier for object properties using this notation:

```js
var sym = Symbol("id");
var obj = {
  prop1: 23,
  [sym]: 65
}
```

However, if you try to iterate on `obj`'s properties, then the only accessible is `prop1`. This means that, to access a property identified by a `symbol`, you must to direct access it:

```js
for (let key in obj) {
  console.log(key);   // It prints "prop1", but not "sym"
}
console.log(obj[sym]);  // It prints "65"
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

