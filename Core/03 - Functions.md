# 03 - Functions <!-- omit from toc -->

- [Functions](#functions)
  - [Default parameters](#default-parameters)
  - [Destructured parameters](#destructured-parameters)
  - [High level functions](#high-level-functions)
  - [Stream](#stream)
  - [Rest operator](#rest-operator)
  - [`import` and `export`](#import-and-export)

> [**RETURN to full index**](Index.md)

## Functions

```js
function functionName(parameter1, parameter2) {
    // ...
    return 2;   // Omissible if the function returns undefined
}

functionName("parameter", 34);
```

### Default parameters

It is possible to assign default values to parameters of functions:

```js
function fun(parameter1, parameter2 = 1) {
  return parameter1 + parameter2;
}
```

### Destructured parameters

```js
var obj = {
  prop1: 23,
  prop2: 2,
  prop3: "value",
  prop4: true
}

function sum({ prop1, prop3 }) {
  return prop1 + prop3;
}

sum(obj);
```

`sum` takes as parameter properties `prop1` and `prop3` destructuring `obj`, automatically extracting them from it.

### High level functions

It is possible to store function inside variables:

```js
var fun = function() {
  // ...
};
```

Javascript has its own lambda notation:

```js
var fun = () => {
  // ...
};
```

> [!TIP] Return a single value
>
> ```js
> const FUN = () => new Date();
> ```
>
> `const` is not mandatory, but it is nicer.

### Stream

It is possible to build streams like Java. 
\
For instance:

```js
var filteredArray = array.filter(n => n > 0).map(x => x * x);
```

### Rest operator

It allows a function to take a variable number of parameters:

```js
const sum = (function() {
  return function sum(...args) {
    return args.reduce((a, b) => a + b, 0);
  }
})();

console.log(sum(1, 2, 3, 4));
console.log(sum(1, 2));
```

The rest operator convert parameters into an array.

### `import` and `export`

Export a function from a `.js` file to another `.js` file.
\
For instance, we can consider to have 2 files in the same directory:

1. `file1.js`:
   
   ```js
   export const capitalizeString = str => str.toUpperCase();
   // Alternatively
   const lowercaseString = str => str.toLowerCase();
   export { lowercaseString };
   ```

2. `file2.js`:

   ```js
   import { capitalizeString } from "./file1.js";
   // If you want to import everything (*) or to use a custom name (as):
   import * as strManipulator from "./file1.js";
   ```

> [!IMPORTANT] Naming
> If you do not rename exported elements, you must use exactly same names used in the exported module.

> [!NOTE] Strict mode
>
> Imported modules are in strict mode by default.

It is also possible to define one `default` export per module:

```js
export default function() {
  // ...
}
```

`default` keyword is useful because without this it would be impossible to export anonymous functions. Importing the `default` export allows to the importer to give a arbitrary name to the imported module:

```js
import arbitraryName from "path_to_file"
```

Notice that curly braces are not necessary.