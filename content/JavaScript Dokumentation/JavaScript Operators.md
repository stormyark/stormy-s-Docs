---
Author: stormy
creation date: 07.09.2024 16:27
tags:
  - code/javascript
source: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math
---
# Arithmetic Operators

Arithmetic operators are symbols used in programming and mathematics to perform basic mathematical operations. Here are the common ones:

- **Addition (`+`)**: Adds two values. For example, `5 + 3` equals `8`.
- **Subtraction (`-`)**: Subtracts one value from another. For example, `5 - 3` equals `2`.
- **Multiplication (`*`)**: Multiplies two values. For example, `5 * 3` equals `15`.
- **Division (`/`)**: Divides one value by another. For example, `6 / 3` equals `2`.
- **Modulus (`%`)**: Gives the remainder of a division operation. For example, `5 % 3` equals `2`.
# Assignment Operators

An assignment operator assigns a value to its left operand based on the value of its right operand. Here are some of them:

- `+=` addition assignment
- `-=` subtraction assignment
- `*=` multiplication assignment
- `/=` division assignment

```js 
let number = 100;

// Both statements will add 10
number = number + 10;
number += 10;

console.log(number);
// 120
```

## What is the difference between == and === ?

The == equality operator converts the operands if they are not of the same type, then applies strict comparison. The === strict equality operator only considers values equal that have the same type.

```js
console.log(1 == '1'); // true
console.log(1 === '1'); // false
console.log(1 === 1); // true
```
# Logical Operators
## `||`
The logical **OR** operator `||` checks two values and returns a boolean. If one or both values are truthy, it returns `true`. If both values are falsy, it returns `false`.

| B     | A     | A \|\| B |
|:----- | ----- | -------- |
| false | false | false    |
| true  | false | true     |
| false | true  | true     |
| true  | true  | true     |
## `&&`
The logical AND operator `&&` checks two values and returns a boolean. If _both_ values are truthy, then it returns `true`. If one, or both, of the values is falsy, then it returns `false`.
```js
true && true;      // true
1 > 2 && 2 > 1;    // false
true && false;     // false
4 === 4 && 3 > 1;  // true
```
## `!`
# Ternary operator 
The ternary operator allows for a compact syntax in the case of binary (choosing between two choices) decisions.
```
variable = bedingung ? wertWennWahr : wertWennFalsch;
```
## Example
```js
let price = 10.5;
let day = "Monday";

day === "Monday" ? price -= 1.5 : price += 1.5;
```

