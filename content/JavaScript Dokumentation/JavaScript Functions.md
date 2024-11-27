---
Author: stormy
creation date: 22.08.2024 23:11
tags:
  - code/javascript
cssclasses:
  - image-borders
  - center-titles
---
# Functions in general
## Function Declaration and Calling

```js
// Defining the function
function sum(num1, num2) {
  return num1 + num2;
}

// Calling the function
sum(2, 4); // 6
```

## Anonymous Functions

![[expression.svg|float-right-small]]
_Anonymous functions_ in JavaScript do not have a name property. They can be defined using the `function` keyword, or as an arrow function. See the code example for the difference between a named function and an anonymous function.

```js
// Named function
function rocketToMars() {
  return 'BOOM!';
}

// Anonymous function
const rocketToMars = function() {
  return 'BOOM!';
}
```

# Arrow Functions (ES6)

The syntax for an arrow function expression does not require the `function` keyword and uses a fat arrow => to separate the parameter(s) from the body.

There are several variations of arrow functions:

- Arrow functions with a single parameter do not require `()` around the parameter list.
- Arrow functions with a single expression can use the concise function body which returns the result of the expression without the `return` keyword.

```js
const plantNeedsWater = function(day) {
	return day;
};
```

**to**

```js
const plantNeedsWater = day => {
	return day;
};
```
## Concise Body Arrow Functions

JavaScript also provides several ways to refactor arrow function syntax. The most condensed form of the function is known as _concise body_. 
![[parameters.svg|float-right-small]]
1. Functions that take only a single parameter do not need that parameter to be enclosed in parentheses. However, if a function takes zero or multiple parameters, parentheses are required.
![[return.svg|float-right-small]]
3. A function body composed of a single-line block does not need curly braces. Without the curly braces, whatever that line evaluates will be automatically returned. The contents of the block should immediately follow the arrow => and the `return` keyword can be removed. This is referred to as _implicit return_.

So if we have a function:

```js
const squareNum = (num) => {  
	return num * num;
};
```

We can refactor the function to:

```js
const squareNum = num => num * num;
```

Notice the following changes:

- The parentheses around `num` have been removed, since it has a single parameter.
- The curly braces `{ }` have been removed since the function consists of a single-line block.
- The `return` keyword has been removed since the function consists of a single-line block.

### Example
**From** *function*
```js
function squareNum(num) {  
	return num * num;
};
```
to *Anonymous function*
```js
const squareNum = function(num) {  
	return num * num;
};
```
to Arrow function
```js
const squareNum = (num) => {  
	return num * num;
};
```
to *Concise Body Arrow Functions*
```js
const squareNum = num => {  
	return num * num;
};
```
to *removing curly braces*
```js
const squareNum = num =>  
	return num * num
;
```
to *removing the return keyword*
```js
const squareNum = num => num * num;
```

rockpaperscissors.js
```js
const getUserChoice = (userInput) => {
  userInput = userInput.toLowerCase();
  if (
    userInput === "rock" ||
    userInput === "paper" ||
    userInput === "scissors" ||
    userInput === "bomb"
  ) {
    return userInput;
  } else {
    console.log("You can only choose between rock, paper or scissors");
  }
};
const getComputerChoice = () => {
  randInt = Math.floor(Math.random() * 3);
  if (randInt === 0) {
    return "rock";
  } else if (randInt === 1) {
    return "paper";
  } else if (randInt === 2) {
    return "scissors";
  }
};
const determineWinner = (userChoice, computerChoice) => {
  if (userChoice === computerChoice) {
    return "Tie!";
  }
  if (userChoice === "bomb") {
    return "You won!";
  } else {
    if (userChoice === "rock") {
      if (computerChoice === "paper") {
        return "The computer won!";
      } else {
        return "You won!";
      }
    }
    if (userChoice === "paper") {
      if (computerChoice === "scissors") {
        return "The computer won!";
      } else {
        return "You won!";
      }
    }
    if (userChoice === "scissors") {
      if (computerChoice === "rock") {
        return "The computer won!";
      } else {
        return "You won!";
      }
    }
  }
};
const playgame = () => {
  let userChoice = getUserChoice("bomb");
  let computerChoice = getComputerChoice();
  console.log(userChoice, computerChoice);
  console.log(determineWinner(userChoice, computerChoice));
};
playgame();
```