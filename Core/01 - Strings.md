# 01 - Strings <!-- omit from toc -->

- [Escaping](#escaping)
  - [Escape characters](#escape-characters)
  - [Escape sequences](#escape-sequences)
- [Strings](#strings)
  - [Concatenation](#concatenation)
  - [Lenght](#lenght)
  - [String manipulation](#string-manipulation)
  - [Converting `string` in integer](#converting-string-in-integer)
  - [Template literals](#template-literals)

> [**RETURN to full index**](Index.md)

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

Strings in javascript are UNICODE.

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

### Converting `string` in integer

```js
var int = parseInt("43");
```

> [!IMPORTANT]
> 
> It is possible to specify the base:
> 
> ```js
> var intBin = parseInt("01101", 2);
> ```

### Template literals

It is more convenient to compose strings with backticks, so that we can use template literals and a lot of special characters without escaping them:

```js
var person = {
  name: "Mattia",
  age: 21
}
var string = `My name is ${person.name} and I am ${person.age} old!`
```