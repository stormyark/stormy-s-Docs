---
Author: stormy
creation date: 27.08.2024 16:37
tags:
  - code/javascript
cssclasses:
  - image-borders
  - center-images
source: https://codingtute.com/javascript-cheatsheets/
---
# String Methods

![[JavaScript String Methods CheatSheet.pdf#page=1]]


| `Math.random()`      | Returns a number between 0 and 1                                   |
| -------------------- | ------------------------------------------------------------------ |
| `Math.floor()`       | returns the largest integer less than or equal to the given number |
| `.toUpperCase()`     | returns a string in all capital letters                            |
| `.trim()`            |                                                                    |
| `.startsWith()`      |                                                                    |
| `Number.isInteger()` |                                                                    |


# Number Methods


# Array Methods

| Methods        | Explaination                                                                                                                                                          | Example   | Example Output |
| -------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------- | -------------- |
| `.length`      | returns the length (size)                                                                                                                                             | [1, 2, 3] | ``             |
| `.push()`      | adds an element at the end                                                                                                                                            | [1, 2, 3] | ``             |
| `.pop()`       | removes the last element                                                                                                                                              | [1, 2, 3] | ``             |
| `.shift()`     | removes the first element                                                                                                                                             |           | ``             |
| `.unshift()`   | adds the specified elements to the beginning                                                                                                                          |           | ``             |
| `.concat()`    | merge two or more arrays                                                                                                                                              |           | ``             |
| `.join()`      | creates a new string by concatenating all of the elements in this array                                                                                               |           | ``             |
| `.slice()`     | returns a shallow copy of a portion of an array into a new array object selected from `start` to `end`                                                                |           | ``             |
| `.indexOf()`   | returns the first index at which a given element can be found in the array                                                                                            |           | ``             |
| `.includes()`  | determines whether an array includes a certain value among its entries                                                                                                |           | ``             |
| `.find()`      | returns the first element in the provided array that satisfies the provided testing function                                                                          |           | ``             |
| `.findIndex()` | returns the index of the first element in an array that satisfies the provided testing function                                                                       |           | ``             |
| `.map()`       | creates a new array populated with the results of calling a provided function on every element in the calling array                                                   |           | ``             |
| `.filter()`    | creates a shallow copy of a portion of a given array, filtered down to just the elements from the given array that pass the test implemented by the provided function |           | ``             |
| `.reduce()`    | executes a user-supplied "reducer" callback function on each element of the array                                                                                     |           | ``             |
| `.every()`     | tests whether all elements in the array pass the test                                                                                                                 |           | ``             |
| `.some()`      | tests whether at least one element in the array passes the test implemented                                                                                           |           | ``             |
| `.reverse()`   | reverses an array                                                                                                                                                     |           | ``             |
| `.at()`        | takes an integer value and returns the item at that index, allowing for positive and negative integers                                                                |           | ``             |
![[Pasted image 20240921103943.png]]
## `.reduce`

```js
const newNumbers = [1, 3, 5, 7]; 

const newSum = newNumbers.reduce((accumulator, currentValue) => {
  console.log("The value of accumulator: ", accumulator);
  console.log("The value of currentValue: ", currentValue);
  return currentValue + accumulator;

});

console.log(newSum)

//The value of accumulator:  1
//The value of currentValue:  3
//The value of accumulator:  4
//The value of currentValue:  5
//The value of accumulator:  9
//The value of currentValue:  7
//re16
```

### Example

```js
const cities = ["Orlando", "Dubai", "Edinburgh", "Chennai", "Accra", "Denver", "Eskisehir", "Medellin", "Yokohama",
];

const nums = [1, 50, 75, 200, 350, 525, 1000];

//  Choose a method that will return undefined
cities.forEach((city) => console.log("Have you visited " + city + "?"));

// Choose a method that will return a new array
const longCities = cities.filter((city) => city.length > 7);

// Choose a method that will return a single value
const word = cities.reduce((acc, currVal) => {
  return acc + currVal[0];
}, "C");

console.log(word);

// Choose a method that will return a new array
const smallerNums = nums.map((num) => num - 5);

// Choose a method that will return a boolean value
nums.every((num) => num < 0);
```