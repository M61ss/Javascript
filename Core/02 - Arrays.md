# 02 - Arrays <!-- omit from toc -->

- [Arrays](#arrays)
  - [Nested arrays](#nested-arrays)
  - [`push`](#push)
  - [`pop`](#pop)
  - [`shift`](#shift)
  - [`unshift`](#unshift)
  - [Turn an array into string](#turn-an-array-into-string)
  - [Destructuring arrays](#destructuring-arrays)
  - [Spread operator](#spread-operator)

> [**RETURN to full index**](Index.md)

## Arrays

```js
var array = ["First", 23];
```

To access arrays you can use indexing as for string ([String manipulation](01%20-%20Strings.md#string-manipulation)). Unlike strings, it is possible to change value of elements of arrays.

> [!IMPORTANT] const arrays
>
> It is impossible to reassign a `const` array, but it is possible to change single values:
>
> ```js
> const s = [5, 8, 4];
> s[0] = 2;
> // s = [3, 6];  <-  ERROR
> ```

> [!WARNING] 
>
> Since all in javascript is an object, if you assign an array to another variable, modifying this one, you will modify both because you copied an object reference, not its content:
>
> ```js
> var array1 = [1, 2, 3, 4];
> var array2 = array1;
> array2[0] = 10;   // It modifies both array1 and array2
> ```

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

### Destructuring arrays

```js
const [z, y] = [1, 2, 5, 7, 6];
```

We declared `z` and `y` `const` variables to which will be assigned first two elements of the array, `1` and `2`.

```js
const [z, , y] = [1, 2, 5, 7, 6];
```

Then, we skip second element, so `y` contains `5`.

> [!TIP] Swap variables
>
> It is possible to swap variables using destructuring:
>
> ```js
> [a, b] = [b, a];
> ```

### Spread operator

It is possible to copy the content of an array into another one without iterate it or using functions:

```js
const array1 = [1, 2, 3, 4];
let array2 = [...array1];
array1[0] = "value";
```

Then, `array1[0]` changed, but not `array2[0]`.

> [!TIP] 
>
> It is easy to exploit the spread operator combined with the destructuring to manipulate arrays.
> \
> For example:
>
> ```js
> var source = [1, 2, 3, 4, 5, 6, 7, 8, 9];
> const [ , , ...array] = source;
> ```
>
> `array` contains a copy of `source`, excluding first two elements.