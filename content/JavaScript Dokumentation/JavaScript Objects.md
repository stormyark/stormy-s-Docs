---
Author: stormy
creation date: 15.09.2024 14:23
tags:
  - code/javascript
source: https://www.codecademy.com/learn/introduction-to-javascript/modules/learn-javascript-objects/cheatsheet
---
# What are Objects
An _object_ is a built-in data type for storing key-value pairs. Data inside objects are unordered, and the values can be of any type.
## Creating Object Literals

Objects can be assigned to variables just like any JavaScript type. We use curly braces, `{}`, to designate an _object literal_:

```js
let spaceship = {}; // spaceship is an empty object
```

We fill an object with unordered data. This data is organized into _key-value pairs_. A key is like a variable name that points to a location in memory that holds a value.

![](https://content.codecademy.com/courses/learn-javascript-objects/key%20value.svg)

A key’s value can be of any data type in the language including functions or other objects.

We make a key-value pair by writing the key’s name, or _identifier_, followed by a colon and then the value. We separate each key-value pair in an object literal with a comma (`,`). Keys are strings, but when we have a key that does not have any special characters in it, JavaScript allows us to omit the quotation marks:

![](https://static-assets.codecademy.com/Courses/learn-javascript-objects/javascript_object.svg)

```js
// An object literal with two key-value pairs
let spaceship = {  
	'Fuel Type': 'diesel',  
	color: 'silver'
};
```

The `spaceship` object has two properties `Fuel Type` and `color`. *`'Fuel Type'` has quotation marks because it contains a space character.*

## Accessing Properties

There are two ways we can access an object’s property. Let’s explore the first way— dot notation, `.`. You’ve used dot notation to access the properties and methods of built-in objects and data instances:

```js
'hello'.length; // Returns 5
```

With property dot notation, we write the object’s name, followed by the dot operator and then the property name (key):

```js
let spaceship = {  
	homePlanet: 'Earth',  
	color: 'silver'
};

spaceship.homePlanet; // Returns 'Earth',
spaceship.color; // Returns 'silver',
```

![](https://content.codecademy.com/courses/learn-javascript-objects/object%20dot%20notation.svg)

If we try to access a property that does not exist on that object, `undefined` will be returned.

```js
spaceship.favoriteIcecream; // Returns undefined
```
### Bracket Notation

The second way to access a key’s value is by using bracket notation, `[ ]`:

```js
['A', 'B', 'C'][0]; // Returns 'A'
```

To use bracket notation to access an object’s property, we pass in the property name (key) as a string.

![](https://content.codecademy.com/courses/learn-javascript-objects/object%20access%20bracket.svg)

We **must** use bracket notation when accessing keys that have numbers, spaces, or special characters in them. Without bracket notation in these situations, our code would throw an error.

```js
let spaceship = {  
	'Fuel Type': 'Turbo Fuel',  
	'Active Duty': true,  
	homePlanet: 'Earth',  
	numCrew: 5
};
spaceship['Active Duty']; // Returns true
spaceship['Fuel Type']; // Returns  'Turbo Fuel'
spaceship['numCrew']; // Returns 5
spaceship['!!!!!!!!!!!']; // Returns undefined
```

With bracket notation you can also use a variable inside the brackets to select the keys of an object. This can be especially helpful when working with functions:

```js
let returnAnyProp = (objectName, propName) => objectName[propName];

returnAnyProp(spaceship, 'homePlanet'); // Returns 'Earth'
```

If we tried to write our `returnAnyProp()` function with dot notation (`objectName.propName`) the computer would look for a key of `'propName'` on our object and not the value of the `propName` parameter.

## Property Assignment

Once we’ve defined an object, we’re not stuck with all the properties we wrote. [Objects](https://www.codecademy.com/resources/docs/javascript/objects) are _mutable_ meaning we can update them after we create them!

We can use either dot notation, `.`, or bracket notation, `[]`, and the assignment operator, = to add new key-value pairs to an object or change an existing property.

![](https://static-assets.codecademy.com/Courses/Learn-JavaScript/objects/object_property_assignment.svg)

One of two things can happen with property assignment:

- If the property already exists on the object, whatever value it held before will be replaced with the newly assigned value.
- If there was no property with that name, a new property will be added to the object.

It’s important to know that although we can’t reassign an object declared with `const`, we can still mutate it, meaning we can add new properties and change the properties that are there.

```js
const spaceship = {type: 'shuttle'};
spaceship = {type: 'alien'}; // TypeError: Assignment to constant variable.spaceship.
type = 'alien'; // Changes the value of the type propertyspaceship.
speed = 'Mach 5'; // Creates a new key of 'speed' with a value of 'Mach 5'
```

You can delete a property from an object with the `delete` operator.

```js
const spaceship = {  
	'Fuel Type': 'Turbo Fuel',  
	homePlanet: 'Earth',  
	mission: 'Explore the universe' 
};

delete spaceship.mission;  // Removes the mission property
delete spaceship.['Fuel Type'];  // Removes the 'Fuel Type' property
```

## Object-Methods

When the data stored on an object is a function we call that a [_method_](https://www.codecademy.com/resources/docs/javascript/methods?page_ref=catalog). A property is what an object has, while a method is what an object does.

Do object methods seem familiar? That’s because you’ve been using them all along! For example `console` is a global JavaScript object and `.log()` is a method on that object. `Math` is also a global JavaScript object and `.floor()` is a method on it.

We can include methods in our object literals by creating ordinary, colon-separated key-value pairs. The key serves as our method’s name, while the value is an anonymous function expression.

```js
const alienShip = {  
	invade: function () {     
		console.log('Hello! We have come to dominate your planet. Instead of Earth, it shall be called New Xaculon.')  
	}
};
```

With the new method syntax introduced in ES6 we can omit the colon and the `function` keyword.

```js
const alienShip = {  
	invade () {     
		console.log('Hello! We have come to dominate your planet. Instead of Earth, it shall be called New Xaculon.')  
	}
};
```

Object methods are invoked by appending the object’s name with the dot operator followed by the method name and parentheses:

```js
alienShip.invade(); // Prints 'Hello! We have come to dominate your planet. Instead of Earth, it shall be called New Xaculon.'
```

## Pass By Reference

[Objects](https://www.codecademy.com/resources/docs/javascript/objects) are _passed by reference_. This means when we pass a variable assigned to an object into a function as an argument, the computer interprets the parameter name as pointing to the space in memory holding that object. As a result, [functions](https://www.codecademy.com/resources/docs/javascript/functions) which change object properties actually mutate the object permanently (even when the object is assigned to a `const` variable).

```js
let spaceship = {
  'Fuel Type' : 'Turbo Fuel',
  homePlanet : 'Earth'
};

let greenEnergy = obj => {
  obj['Fuel Type'] = 'avocado oil'
} 

let remotelyDisable = obj => {
  obj.disabled = true;
}

remotelyDisable(spaceship)
greenEnergy(spaceship)
console.log(spaceship)

//{ 'Fuel Type': 'avocado oil',
  homePlanet: 'Earth',
  disabled: true }
```

### Looping Through Objects

[Loops](https://www.codecademy.com/resources/docs/javascript/loops) are programming tools that repeat a block of code until a condition is met. We learned how to iterate through [arrays](https://www.codecademy.com/resources/docs/javascript/arrays) using their numerical indexing, but the key-value pairs in [objects](https://www.codecademy.com/resources/docs/javascript/objects) aren’t ordered! [JavaScript has given us alternative solution for iterating through objects with the `for...in` syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...in) .

`for...in` will execute a given block of code for each property in an object.

```js
let spaceship = {
  crew: {
    captain: {
      name: "Lily",
      degree: "Computer Engineering",
      cheerTeam() {
        console.log("You got this!");
      },
    },
    "chief officer": {
      name: "Dan",
      degree: "Aerospace Engineering",
      agree() {
        console.log("I agree, captain!");
      },
    },
    medic: {
      name: "Clementine",
      degree: "Physics",
      announce() {
        console.log(`Jets on!`);
      },
    },
    translator: {
      name: "Shauna",
      degree: "Conservation Science",
      powerFuel() {
        console.log("The tank is full!");
      },
    },
  },
};

// for...in
for (let crewMember in spaceship.crew) {  
	console.log(`${crewMember}: ${spaceship.crew[crewMember].name}`);
}

// Output:
//captain: Lily
//chief officer: Dan
//medic: Clementine
//translator: Shauna
```

Our `for...in` will iterate through each element of the `spaceship.crew` object. In each iteration, the variable `crewMember` is set to one of `spaceship.crew`‘s keys, enabling us to log a list of crew members’ role and `name`.

## The this Keyword

[Objects](https://www.codecademy.com/resources/docs/javascript/objects) are collections of related data and functionality. We store that functionality in [methods](https://www.codecademy.com/resources/docs/javascript/methods) on our objects:
```js
const goat = {  
	dietType: 'herbivore',  
	makeSound() {    
		console.log('baaa');  
	}
};
```

In our `goat` object we have a `.makeSound()` method. We can invoke the `.makeSound()` method on `goat`.
```js
goat.makeSound(); // Prints baaa
```

Nice, we have a `goat` object that can print `baaa` to the console. Everything seems to be working fine. What if we wanted to add a new method to our `goat` object called `.diet()` that prints the `goat`‘s `dietType`?

```js
const goat = {  
	dietType: 'herbivore',  
	makeSound() {    
		console.log('baaa');  
	},  
	diet() {    
		console.log(dietType);  
	}
};

goat.diet(); // Output will be "ReferenceError: dietType is not defined"
```

That’s strange, why is `dietType` not defined even though it’s a property of `goat`? That’s because inside the scope of the `.diet()` method, we don’t automatically have access to other properties of the `goat` object.

Here’s where the [`this`](https://www.codecademy.com/resources/docs/javascript/this?page_ref=catalog) keyword comes to the rescue. If we change the `.diet()` method to use the `this`, the `.diet()` works! :

```js
const goat = {  
	dietType: 'herbivore',  
	makeSound() {    
		console.log('baaa');  
	},  
	diet() {    
		console.log(this.dietType);  
	}
};

goat.diet(); // Output: herbivore
```

The `this` keyword references the _calling object_ which provides access to the calling object’s properties. In the example above, the calling object is `goat` and by using `this` we’re accessing the `goat` object itself, and then the `dietType` property of `goat` by using property dot notation.

## Arrow Functions and this

We saw in the previous exercise that for a method, the calling object is the object the method belongs to. If we use the [`this`](https://www.codecademy.com/resources/docs/javascript/this?page_ref=catalog) keyword in a method then the value of `this` is the calling object. However, it becomes a bit more complicated when we start using arrow [functions](https://www.codecademy.com/resources/docs/javascript/functions) for [methods](https://www.codecademy.com/resources/docs/javascript/methods). Take a look at the example below:

```js
const goat = {  
	dietType: 'herbivore',  
	makeSound() {    
		console.log('baaa');  
	},  
	diet: () => {    
		console.log(this.dietType);  
	}
};

goat.diet(); // Prints undefined
```

In the comment, you can see that `goat.diet()` would log `undefined`. So what happened? Notice that the `.diet()` method is defined using an arrow function.

Arrow functions inherently _bind_, or tie, an already defined `this` value to the function itself that is NOT the calling object. In the code snippet above, the value of `this` is the _global object_, or an object that exists in the global scope, which doesn’t have a `dietType` property and therefore returns `undefined`.

To read more about either arrow functions or the global object check out the MDN documentation of [the global object](https://developer.mozilla.org/en-US/docs/Glossary/Global_object) and [arrow functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions).

The key takeaway from the example above is to _avoid_ using arrow functions when using `this` in a method!

## Privacy

Accessing and updating properties is fundamental in working with [objects](https://www.codecademy.com/resources/docs/javascript/objects). However, there are cases in which we don’t want other code simply accessing and updating an object’s properties. When discussing _privacy_ in objects, we define it as the idea that only certain properties should be mutable or able to change in value.

Certain languages have privacy built-in for objects, but JavaScript does not have this feature. Rather, JavaScript developers follow naming conventions that signal to other developers how to interact with a property. One common convention is to place an underscore `_` before the name of a property to mean that the property should not be altered. Here’s an example of using `_` to prepend a property.

```js
const bankAccount = {  
	_amount: 1000
}
```

In the example above, the `_amount` is not intended to be directly manipulated.

Even so, it is still possible to reassign `_amount`:

```js
bankAccount._amount = 1000000;
```

## Getters

_Getters_ are [methods](https://www.codecademy.com/resources/docs/javascript/methods) that get and return the internal properties of an object. But they can do more than just retrieve the value of a property! Let’s take a look at a getter method:

```js
const person = {  
	_firstName: 'John',  
	_lastName: 'Doe',  
	get fullName() {    
		if (this._firstName && this._lastName) {      
			return `${this._firstName} ${this._lastName}`;    
		} else {
			return 'Missing a first name or a last name.';
		}  
	}
}// To call the getter method: person.fullName; // 'John Doe'
```

Notice that in the getter method above:

- We use the `get` keyword followed by a function.
- We use an `if...else` conditional to check if both `_firstName` and `_lastName` exist (by making sure they both return truthy values) and then return a different value depending on the result.
- We can access the calling object’s internal properties using [`this`](https://www.codecademy.com/resources/docs/javascript/this). In `fullName`, we’re accessing both `this._firstName` and `this._lastName`.
- In the last line we call `fullName` on `person`. In general, getter methods do not need to be called with a set of parentheses. Syntactically, it looks like we’re accessing a property.

Now that we’ve gone over syntax, let’s discuss some notable advantages of using getter methods:

- Getters can perform an action on the data when getting a property.
- Getters can return different values using [conditionals](https://www.codecademy.com/resources/docs/javascript/conditionals).
- In a getter, we can access the properties of the calling object using `this`.
- The functionality of our code is easier for other developers to understand.

Another thing to keep in mind when using getter (and setter) methods is that properties cannot share the same name as the getter/setter function. If we do so, then calling the method will result in an infinite call stack error. One workaround is to add an underscore before the property name like we did in the example above.

## Setters

Along with getter [methods](https://www.codecademy.com/resources/docs/javascript/methods), we can also create _setter_ methods which reassign values of existing properties within an object. Let’s see an example of a setter method:

```js
const person = {  
	_age: 37,  
	set age(newAge){    
		if (typeof newAge === 'number'){
			this._age = newAge;
		} else {      
			console.log('You must assign a number to age');    
		}  
	}
};
```

Notice that in the example above:

- We can perform a check for what value is being assigned to `this._age`.
- When we use the setter method, only values that are numbers will reassign `this._age`
- There are different outputs depending on what values are used to reassign `this._age`.

Then to use the setter method:

```js
person.age = 40;
console.log(person._age); // Logs: 40
person.age = '40'; // Logs: You must assign a number to age
```

Setter methods like `age` do not need to be called with a set of parentheses. Syntactically, it looks like we’re reassigning the value of a property.

Like getter methods, there are similar advantages to using setter methods that include checking input, performing actions on properties, and displaying a clear intention for how the object is supposed to be used. Nonetheless, even with a setter method, it is still possible to directly reassign properties. For example, in the example above, we can still set `._age` directly:

```js
person._age = 'forty-five'
console.log(person._age); // Prints forty-five
```

## Factory Functions

So far we’ve been creating objects individually, but there are times where we want to create many instances of an object quickly. Here’s where _factory functions_ come in. A real world factory manufactures multiple copies of an item quickly and on a massive scale. A factory function is a function that returns an object and can be reused to make multiple object instances. Factory functions can also have parameters allowing us to customize the object that gets returned.

Let’s say we wanted to create an object to represent monsters in JavaScript. There are many different types of monsters and we could go about making each monster individually but we can also use a factory function to make our lives easier. To achieve this diabolical plan of creating multiple monsters objects, we can use a factory function that has parameters:

```js
const monsterFactory = (name, age, energySource, catchPhrase) => {  
	return {     
		name: name,    
		age: age,     
		energySource: energySource,    
		scare() {      
			console.log(catchPhrase);
		}   
	}
};
```

In the `monsterFactory` function above, it has four parameters and returns an object that has the properties: `name`, `age`, `energySource`, and `scare()`. To make an object that represents a specific monster like a ghost, we can call `monsterFactory` with the necessary arguments and assign the return value to a variable:

```js
const ghost = monsterFactory('Ghouly', 251, 'ectoplasm', 'BOO!');
ghost.scare(); // 'BOO!'
```

Now we have a `ghost` object as a result of calling `monsterFactory()` with the needed arguments. With `monsterFactory` in place, we don’t have to create an object literal every time we need a new monster. Instead, we can invoke the `monsterFactory` function with the necessary arguments to ~~take over the world~~ make a monster for us!

### How to call

```js
const refrigerator = {  
	dairy: ['cheese', 'milk', 'sour cream'],  
	temperature: 35,  
	'produce drawer': {    
		vegetables: ['lettuce', 'broccoli', 'peas'],    
		fruit: ['apples', 'berries', 'grapes']   
	}
}
```
```js
refriferator['produce drawer'].vegetables[0]
// apples
```
## Property Value Shorthand

ES6 introduced some new shortcuts for assigning properties to [variables](https://www.codecademy.com/resources/docs/javascript/variables) known as _destructuring_.

In the previous exercise, we created a factory function that helped us create [objects](https://www.codecademy.com/resources/docs/javascript/objects). We had to assign each property a key and value even though the key name was the same as the parameter name we assigned to it. To remind ourselves, here’s a truncated version of the factory function:

```js
const monsterFactory = (name, age) => {  
	return {     
		name: name,    
		age: age  
	}
};
```

Imagine if we had to include more properties, that process would quickly become tedious! But we can use a destructuring technique, called _property value shorthand_, to save ourselves some keystrokes. The example below works exactly like the example above:

```js
const monsterFactory = (name, age) => {  
	return {     
		name,    
		age   
	}
};
```

Notice that we don’t have to repeat ourselves for property assignments!

## Destructured Assignment

We often want to extract key-value pairs from [objects](https://www.codecademy.com/resources/docs/javascript/objects) and save them as [variables](https://www.codecademy.com/resources/docs/javascript/variables). Take for example the following object:

```js
const vampire = {  
	name: 'Dracula',  
	residence: 'Transylvania',  
	preferences: {    
		day: 'stay inside',    
		night: 'satisfy appetite'  
	}
};
```

If we wanted to extract the `residence` property as a variable, we could use the following code:

```js
const residence = vampire.residence; 
console.log(residence); // Prints 'Transylvania' 
```

However, we can also take advantage of a destructuring technique called _destructured assignment_ to save ourselves some keystrokes. In destructured assignment we create a variable with the name of an object’s key that is wrapped in curly braces `{ }` and assign to it the object. Take a look at the example below:

```js
const { residence } = vampire; 
console.log(residence); // Prints 'Transylvania'
```

Look back at the `vampire` object’s properties in the first code example. Then, in the example above, we declare a new variable `residence` that extracts the value of the `residence` property of `vampire`. When we log the value of `residence` to the console, `'Transylvania'` is printed.

We can even use destructured assignment to grab nested properties of an object:

```js
const { day } = vampire.preferences; 
console.log(day); // Prints 'stay inside'
```

## Built-in Object Methods

```js
const robot = {
	model: 'SAL-1000',
	mobile: true,
	sentient: false,
	armor: 'Steel-plated',
	energyLevel: 75
};
```

### `Object.keys()`
The **`Object.keys()`** static method returns an array of a given object's own enumerable string-keyed property names.
```js
const robotKeys = Object.keys(robot);

console.log(robotKeys);
// Output:
// [ 'model', 'mobile', 'sentient', 'armor', 'energyLevel' ]
```

### `Object.entries()`
The **`Object.entries()`** static method returns an array of a given object's own enumerable string-keyed property key-value pairs.
```js
const robotEntries = Object.entries(robot);

console.log(robotEntries);
//Output:
//[ [ 'model', 'SAL-1000' ],
//[ 'mobile', true ],
//[ 'sentient', false ],[ 'armor', 'Steel-plated' ],
//[ 'energyLevel', 75 ] ]
```

### `Object.assign()`
The **`Object.assign()`** static method copies all [enumerable](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/propertyIsEnumerable) [own properties](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/hasOwn) from one or more _source objects_ to a _target object_. It returns the modified target object.
```js
const newRobot = Object.assign({laserBlaster: true, voiceRecognition: true}, robot);

console.log(newRobot);
// Output:
//{ laserBlaster: true,
//voiceRecognition: true,
//model: 'SAL-1000',
//mobile: true,
//sentient: false,
//armor: 'Steel-plated',
//energyLevel: 75 }
```