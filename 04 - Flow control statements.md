# 04 - Flow control statements <!-- omit from toc -->

- [Flow control statements](#flow-control-statements)
  - [`if-else`](#if-else)
  - [Inline `if`](#inline-if)
  - [`switch`](#switch)
  - [`while` loop](#while-loop)
  - [`for` loop](#for-loop)
  - [`do-while` loop](#do-while-loop)
  - [`try-catch`](#try-catch)

> [**RETURN to full index**](Index.md)

## Flow control statements

### `if-else`

```js
var condition1;
var condition2;
if (condition1) {

} else if (condition2) {

} else {

}
```

### Inline `if`

```js
var output = a === b ? 1 : 0;
```

`output` is 1 if the condition is true, 0 otherwise.

It is possible in javascript to build multiple conditions with the ternary operator:

```js
var output = a < 5 ? "less than 5" : a < 10 ? "less than 10" : "10 or more";
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

### `try-catch`

```js
try {
  // ...
} catch(ex) {
  // ...
}
```