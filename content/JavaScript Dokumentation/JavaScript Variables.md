---
Author: stormy
creation date: 27.08.2024 21:14
tags:
  - code/javascript
---
# Datatypes
JavaScript is a **dynamically typed** language which means no datatype annotations are necessary. Which means its allowed to reassign the same variable another datatype.

| Data Type   | Description                                                                                                                                |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| `number`    | Any number, including numbers with decimals: `1`, `-2`, `99`, `3.14`.                                                                      |
| `bigint`    | Any number, greater than 2^53-1 or less than -(2^53-1) with `n` appended to the number: `1234567890123456n`.                               |
| `string`    | Any grouping of characters on your keyboard (letters, numbers, spaces, symbols, etc.) surrounded by single `''` or double `""`.            |
| `boolean`   | This data type only has two possible values — either `true` or `false`.                                                                    |
| `null`      | This data type represents the intentional absence of a value, and is represented by the keyword `null`.                                    |
| `undefined` | This data type is denoted by the keyword `undefined`. It also represents the absence of a value though it has a different use than `null`. |
| `symbol`    | A newer feature to the language, symbols are unique identifiers, useful in more complex coding. No need to worry about these for now.      |
## Example

```js
let number = 66

number = '88'
// 88
```

![[JavaScript Basics in easy way PDF Version.pdf#page=4]]
# How to use variables
In JavaScript, `var` is function-scoped and was traditionally used to declare variables. `let` and `const` are block-scoped. The key difference between `let` and `const` is that `let` allows for reassignment while `const` creates a read-only reference.

- `var` and `let` create variables that can be reassigned another value.
- `const` creates "constant" variables that cannot be reassigned another value.
- if you're not going to change the value of a variable, it is good practice to use `const`.
## How to name variables
There are a few general rules for naming variables:

- Variable names cannot start with numbers.
- Variable names are **case sensitive**, so `myName` and `myname` would be different variables. It is bad practice to create two variables that have the same name using different cases.
- Variable names cannot be the same as _keywords_. For a comprehensive list of keywords check out [MDN’s keyword documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Lexical_grammar#Keywords).

# Lexical Environment

```js
var a = global;

function fun() {
	let a = 'local;

	if (true) {
		let a = 'block'
	}
}
```

## Scopes
 - `global` - can be accessed from anywhere in the code
 - `local` - only accessible inside a **function**
 - `block` - only exist within the block they are defined in

|                       |  `var`  |  `let`  | `const` |
| --------------------- | :-----: | :-----: | :-----: |
| global                | &#10004 | &#10006 | &#10006 |
| local                 | &#10004 | &#10004 | &#10004 |
| block                 | &#10006 | &#10004 | &#10004 |
| can be <br>reassigned | &#10004 | &#10004 | &#10006 |

## Hoisting
In JavaScript, hoisting refers to the process of moving variable and function declarations to the top of their scope, regardless of their original position in the code. It means you can use variables and functions before they are declared in the code.

![[JavaScript Variables explanation#How to hoist variables declared with `let`]]

# Template Literals

Template literals are strings that allow embedded expressions, `${expression}`. While regular strings use single `'` or double `"` quotes, template literals use backticks instead.

```Js
let name = "stormy";
console.log(`Hello, ${name}`); 
// Hello, stormy

console.log(`stormy is ${11+8} years old.`); 
// Billy is 19 years old.
```
