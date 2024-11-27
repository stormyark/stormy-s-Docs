---
Author: stormy
creation date: 02.09.2024 16:02
tags:
  - code/javascript
---
# Floating-Point precision value
```js
0.1 + 0.2
//Output: 0.3000000000000000000004
```

Computers can only store `0` and `1` while Humans can count from 0 to 9, so there is sort of a mismatch between our number system.

## Explanation 
1. **Binary Representation**: Computers represent numbers in binary (base 2), not decimal (base 10). Some decimal numbers, like 0.1 and 0.2, cannot be precisely represented in binary. When you write `0.1` or `0.2` in your code, the computer stores a binary approximation of these numbers.

2. **Precision Limitations**: Floating-point numbers have a limited precision. For most languages, this precision is usually about 15 number ints and 17 decimal places. When performing operations with floating-point numbers, small rounding errors can occur because the binary approximations of the numbers aren't exact.

3. **Addition of Approximate Values**: When you add `0.1` and `0.2`, you're actually adding their binary approximations. The result isn't exactly `0.3`, but a very close value. Due to the precision limits, this result is displayed as something like `0.30000000000000004`.

## Example
- In binary, `0.1` might be approximated as `0.00011001100110011...` (repeating).
- Similarly, `0.2` is approximated as `0.0011001100110011...` (repeating).
- When you add these two approximations, the result is slightly off from the exact `0.3`.

## Conclusion
This is a common issue with floating-point arithmetic in most programming languages, and it’s generally something programmers need to account for when precision is critical. One common approach to mitigate this issue is to round the result to the desired number of decimal places if exact values are needed.
# Falsy Values
The list of falsy values includes:

- `0`
- Empty strings like `""` or `''`
- `null` which represent when there is no value at all
- `undefined` which represent when a declared variable lacks a value
- `NaN` (=Not a Number)
## What is the difference between `null` and `undefined`?
The `null` is an assignment value. It can be assigned to a variable as a representation of no value. But the `undefined` is a primitive value that represents the absence of a value, or a variable that has not been assigned a value.

# Shorthand
## Declaring Variables
### Shorthand:
```js
let x;
let y;
let z = "a";
```
### Longhand:
```js
let x, y, z = "a";
```
## Ternary Operator
### Shorthand:
```js
let number;
if (x > 9) {
	number = true;
} else {
	number = false;
}
```
### Longhand:
```js
let number = x > 9 ? true : false;
```
## Switch Case
### Shorthand:
```js
switch (something) {
	case 1:
		doSomething();
		break;
	case 2:
		doSomethingElse();
		break;
}
```
### Longhand:
```js
var cases = {
	1: doSomething,
	2: doSomethingElse
}
```
## If presence
### Shorthand:
```js
if (boolGoesHere === true) {}
```
### Longhand:
```js
if (boolGoesHere) {}
```
## charAt()
### Shorthand:
```js
"myString".charAt(0);
```
### Longhand:
```js
"myString"[0];
```