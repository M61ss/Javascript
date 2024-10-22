# 00 - Basics <!-- omit from toc -->

- [Comments](#comments)
- [Data types](#data-types)
- [Variables](#variables)
  - [`var`](#var)
  - [`let`](#let)
  - [`const`](#const)
  - [Strict mode](#strict-mode)
- [Operators](#operators)

> [**RETURN to full index**](Index.md)

## Comments

```js
// in-line comment
/*
multi-line comment
*/
```

## Data types

- `boolean`;
- `string`;
- `symbol`;
- `number`: it is an 8 byte floating point, so there is no distinction between floating point numbers and integers;
- `object`.

A variable is `null` since it is not declared. Then, a variable contains `undefined` since it is not initialized.

If a function performs a forbidden operation, then the variable which store the result contains `NaN`.
 
## Variables

### `var`

This variable type has **function scope**:

```js
var myName = "Mattia";
```

`var` allows to declare the same variable many times in the same scope.

Function scope means that if a `var` is declared inside a block of code, however it is visible in the whole function:

```js
function checkScope() {
  if (true) {
    var i = "block scope";
    console.log("i has: ", i);
  }
  console.log("i has: ", i);
  return i;
}
```

This piece of code works as well.

> [!WARNING] DO NOT USE VAR
>
> It is very recommended to use `let` or `const` instead of `var`, which is considered dangerous because of its scope.

### `let`

This variable type has **block scope**, which works like the normal C variable scope. It means that a variable is seen only inside the block where it has been declared:

```js
let myName = "Mattia";
```

`let` forbids, unlike `var`, to declare a variable two or more times in the same scope:

```js
let variableOutside = "something";
let variableOutside = "another value";
```

It falls into error.

### `const`

Simply a read-only constant value:

```js
const MYNAME = "Mattia";
```

> [!IMPORTANT]
>
> `const` variable's names has to be uppercase.

> [!IMPORTANT] Declaring without initializing
>
> When a variable is declared, it contains `undefined` by default.

### Strict mode

To avoid mistakes or unsafe actions, since javascript performs a lot of hidden and unsafe operations, some people add at the start of the file or inside a function this line:

```js
"use strict";
```

Adding this line of code to a block, the javascript interpreter performs:

- Changes converting mistakes into errors (as syntax errors or at runtime);
- Changes simplifying how variable references are resolved. 
  \
  For instance:

  ```js
  "use strict";
  let mistypeVariable;

  // Assuming no global variable mistypeVarible exists
  // this line throws a ReferenceError due to the
  // misspelling of "mistypeVariable" (lack of an "a")
  mistypeVarible = 17;
  ```

  In sloppy mode, that is to say javascript code without `"use script";` statement, javascript silently creates a property, called `mistypeVarible`, in the global object `mistypeVariable`. In most cases, it is not desired.

- Changes simplifying `eval` and `arguments`;
- Changes making it easier to write "secure" JavaScript;
- Changes anticipating future ECMAScript evolution.

> [!WARNING]
>
> Browsers not supporting strict mode will run strict mode code with different behavior from browsers that do, so don't rely on strict mode without feature-testing for support for the relevant aspects of strict mode.

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
  var output = 3 == "3"; // It is true
  ```

- `===`, `!==`: respectively strict equality and strict inequality operators:

  ```js
  var output = 3 === "3"; // It is false
  var output = 3 !== "3"; // it is true
  ```

- `>`, `<`, `>=`, `<=`: respectively greater than, less than, greater than or equal, less than or equal operators;
- `&&`: logical and operator;
- `||`: logical or operator;
- `?`: ternary operator (see [inline if](04%20-%20Flow%20control%20statements.md#inline-if));
- `...`: [rest operator](03%20-%20Functions.md#rest-operator) or [spread operator](02%20-%20Arrays.md#spread-operator).
