---
Author: stormy
creation date: 12.07.2024 22:53
tags:
  - code/javascript
cssclasses:
  - center-images
  - image-borders
---
> [!info] Info
> JavaScript is a high level, [[versatile]], interpreted or just-in-time compiled, prototype-based, multi-paradigm, dynamic language with a non-blocking event loop primarily known for its role in **web development**. 

Scripts are often, but not always, interpreted from the source code or "semi-compiled" to byte-code which is interpreted, unlike the applications they are associated with, which are traditionally compiled to native machine code for the system on which they run

It was created in 1995 in just one week by Brendan Eich with the goal of adding an easy to learn scripting language to the Netscape browser. It was originally named mocha but the genius marketing people of the time wanted it to sound like that sexy new java language. 

Today it's a fully featured language that continues to evolve through the ECMAScript standard. 

![[Pasted image 20240818193153.png]]

It's most well known for building front-end web applications because it's **the only language other than web assembly that is natively supported in browsers**. However anything that can be built with JavaScript will be built with JavaScript. Like server-side applications with node.js, mobile applications with react, native or ionic and desktop apps with electron. It's an interpreted scripting language but tools like the v8 engine and chromium use a just-in-time compiler to convert it to machine code at runtime. It's also excellent at handling IO intensive jobs. Despite the fact that it's a single threaded language made possible by a non-blocking event loop that can queue up work in the background without blocking the main thread.

---
## get started

JavaScript files ending in .js will start executing your code from the global context. Use the console to log a value with the built-in debugger. Think about where you want to run this file is it a front-end browser or a back-end node.js server.
On a website JavaScript is often used to grab an element from the dom. Document query selector will grab the first button then we can assign it to a variable with var, let or const. var is the OG way to do it, but is typically avoided, **let is for variables that can be reassigned**, while **const is for variables that cannot be reassigned**. Functions are first class objects to support functional programming patterns, but JavaScript also supports classes and inheritance for object oriented patterns. Even though it's single threaded it can do work asynchronously with the promise API which also supports the "async await" syntax, js code can also run on the server thanks to the node.js runtime. Instead of buttons on a web page it interacts with things like the file system API.

[JavaScript Recources](https://developer.mozilla.org/en-US/docs/Web/JavaScript)