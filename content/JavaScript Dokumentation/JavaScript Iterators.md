---
Author: stormy
creation date: 13.09.2024 11:59
tags:
  - code/javascript
---
# Iterators
## `.forEach()`

```js
const artists = ['Picasso', 'Kahlo', 'Matisse', 'Utamaro'];

artists.forEach(artist => {
  console.log(artist + ' is one of my favorite artists.');
});

// Picasso is one of my favorite artists.
// Kahlo is one of my favorite artists.
// Matisse is one of my favorite artists.
// Utamaro is one of my favorite artists.
```

## `.map()`

```js
const numbers = [1, 2, 3, 4, 5];

const squareNumbers = numbers.map(number => {
  return number * number;
});

console.log(squareNumbers);

// [ 1, 4, 9, 16, 25 ]
```

## `.filter()`

```js
const things = ['desk', 'chair', 5, 'backpack', 3.14, 100];

const onlyNumbers = things.filter(thing => {
  return typeof thing === 'number';
});

console.log(onlyNumbers);

// [ 5, 3.14, 100 ]
```