# Javascript <!-- omit from toc -->

- [Comments](#comments)
- [Data types and variables](#data-types-and-variables)
  - [Data types](#data-types)
  - [Variables](#variables)
- [Operators](#operators)
- [Escaping](#escaping)
  - [Escape characters](#escape-characters)
  - [Escape sequences](#escape-sequences)
- [Strings](#strings)
  - [Concatenation](#concatenation)
  - [Lenght](#lenght)
  - [String manipulation](#string-manipulation)
- [Arrays](#arrays)
  - [Nested arrays](#nested-arrays)
  - [`push`](#push)
  - [`pop`](#pop)
  - [`shift`](#shift)
  - [`unshift`](#unshift)
  - [Turn an array into string](#turn-an-array-into-string)
- [Functions](#functions)
- [Control flow statements](#control-flow-statements)
  - [`if-else`](#if-else)
  - [`switch`](#switch)
  - [`while` loop](#while-loop)
  - [`for` loop](#for-loop)
  - [`do-while` loop](#do-while-loop)
- [Objects](#objects)
  - [Accessing object properties](#accessing-object-properties)
  - [Update object properties](#update-object-properties)
  - [Add object properties](#add-object-properties)
  - [Delete object properties](#delete-object-properties)
  - [Check object properties](#check-object-properties)
  - [Object array](#object-array)
  - [Nesed object](#nesed-object)

## Comments

```js
// in-line comment
/*
multi-line comment
*/
```

## Data types and variables

### Data types

- `undefined`: something that isn't defined;
- `null`: it corresponds to "nothing". A variable that contains `null` means that contains nothing;
- `boolean`;
- `string`;
- `symbol`;
- `number`;
- `object`.

### Variables

There are 3 ways to declare variables in javascript:

- Variable which has scope on the whole function in which it is declared:

  ```js
  var myName = "Mattia";
  ```

- Variable which can used only in the block where it is defined:

  ```js
  let myName = "Mattia";
  ```

- Constant:

  ```js
  const myName = "Mattia";
  ```

> [!NOTE] Declaring without initializing
>
> When a variable is declared, it contains `null` by default.

## Operators

- `=`: assignment;
- `+`:
  - arithmetic sum between `number`;
  - concatenation between `string`;
- `-`: arithmetic subtraction;
- `*`: arithmetic multiplication;
- `/`: arithmetic division;
- `varName++`: increment by 1;
- `varName--`: decrement by 1;
- `%`: remainder of division;
- `+=`, `-=`, `*=`, `/=`: respectively sum/concatenation and assignment, subtraction and assignment, multiplication and assignment, division and assignment;
- `==`: equality operator. It checks if two elements are equals even if of different types. For example:
  
  ```js
  var output = 3 == '3';     // It is true
  ```

- `===`, `!==`: respectively strict equality and strict inequality operators:
  
  ```js
  var output = 3 === '3';   // It is false
  var output = 3 !== '3';   // it is true
  ```

- `>`, `<`, `>=`, `<=`: respectively greater than, less than, greater than or equal, less than or equal operators;
- `&&`: logical and operator;
- `||`: logical or operator.

## Escaping

### Escape characters

The escape character to distinguish syntax symbols and character is `\`.

Anyway, if you have a string and you need only to escape double quotes, you can simply put the string inside single quotes:

```js
var str = 'no error if I "put double quotes inside"';
```

It is also possible to use backquotes:

```js
var str = `I can put 'single quotes' and "double quotes" inside and no error occurs`;
```

### Escape sequences

- `\'`: single quote;
- `\"`: double quotes;
- `\\`: backslash;
- `\n`: newline;
- `\r`: carrige return;
- `\t`: tab;
- `\b`: backspace;
- `\f`: form feed.

## Strings

### Concatenation

```js
var concatenated = "This is " + "concatenated.\n";
concatenated += "Second sentence.\n";
var moreConcatenation =
  "This is the header.\n" + concatenanted + "This is the footer.\n";
```

> [!WARNING] Concatenate number
>
> If you try to concatenate a `string` with a `number`, then javascript create a `string` result of the concatenation of the first one with the `number` converted to string or vice versa:
>
> ```js
> var somethingTerrible = 3 + '2';      // It corresponds to '32'
> somethingTerrible = '2' + 5;          // '25'
> ```

### Lenght

```js
var lenght = str.lenght;
```

### String manipulation

Obtain the first letter:

```js
var firstLetter = str[0];
```

> [!WARNING] Immutable strings
>
> Strings are immutable, so it is impossible to change value of a single letter.

## Arrays

```js
var array = ["First", 23];
```

To access arrays you can use indexing as for string ([String manipulation](#string-manipulation)). Unlike strings, it is possible to change value of elements of arrays.

### Nested arrays

```js
var multidimensionalArray = [["something", 8], ["other", 16, true]];
```

### `push`

It appends data at the end of arrays:

```js
var array = ["element", 34];
array.push(23);
array.push(["something", false]);   // It pushes an array inside an array
```

### `pop`

It pics and remove an element from the tail of arrays:

```js
var array = [23, true, false];
var popped = array.pop();       // popped = false
```

### `shift`

It works like `pop`, but it pics and remove the element from the head of arrays:

```js
var array = [3, true, "string"];
var shifted = array.shift();         // shifted = 3
```

### `unshift`

It works like `push`, but it add an element at the beginning of arrays:

```js
var array = [98, 3, "something"];
array.unshift("other");
```

### Turn an array into string

```js
var stringFromArray = JSON.stringify([0, "something", true]);
```

## Functions

```js
function functionName(parameter1, parameter2) {
    // ...
    return 2;   // Omissible if the function returns undefined
}

functionName("parameter", 34);
```

## Control flow statements

### `if-else`

```js
var condition1;
var condition2;
if (condition1) {

} else if (condition2) {

} else {

}
```

### `switch`

```js
switch(val) {
  case 1:
    break;
  default:
    break;
}
```

> [!WARNING] Equality condition of switches
>
> The equality between `switch` parameter and `case` parameters is checked with the `===` operator.

### `while` loop

```js
while (i < 3) {
  i++;
}
```

### `for` loop

```js
for (var i = 0; i < 5; i++) {
  // ...
}
```

### `do-while` loop

```js
do {

} while (i < 4)
```

## Objects

```js
var someObject = {
  "name": "something",
  "number": 43,
  "array": [23, "other"],
  3: "something identified by a number",
  "property with spaces": true
}
```

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
    "name": "some name",
    "second": "other"
  },
  {
    "name": "another name",
    "second": "something",
    "third": "some other value"
  }
]
```

> [!NOTE]
>
> It is not required that objects have same properties.

### Nesed object

```js
var someObject = {
  "nested object": {
    "key": "value"
  },
  "property": "something"
}
```

As you can see, there is a property which is an object with its own properties.

