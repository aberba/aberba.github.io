---
title:  "Simplistic JavaScript coding style with ES6"
date:   2018-02-13 10:20:23
categories: [JavaScript]
tags: [JavaScript, Code Simplicity, nodejs]
---

![JavaScript](/images/javascript.png) 

Recently, JavaScript has played huge role in projects I've been working on more than ever. EcmaScript 6 (ES6) has made JavaScript much appealing than it already was, for both front-end and back-end development.

> ## JavaScipt is everywhere!

Almost all major cloud vendors support JavaScript (NodeJS ) as first class language and have official SDKs written for it. I've been using JavaScript intensively since the ES5 days but I never bothered to write anything about it since none seemed interesting.

> ## Did I just say "ES5 days" like it was centuries ago?

Some interesting and **simplistic** coding styles I've been using recently have proved quite productive. Below are some few:

## Destructuring

This syntactic sugar makes is much cleaner to access properties of an object and arrays.

```js
let user = { name: "Samuel Adongo", age: 28 };
const { name, age } = user;
console.log(name, age);
```

Function parameters and arguments can also be made more self-documenting using [destructuring](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment), a common pattern used in [React](https://reactjs.org/) ES6 code. [Template literals](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals) are also more readable compared to concatenation.

```js
function fetchUser({ name, age }) {
    console.log(`fetching ${name} of age ${age}`);
}

const name = "Samuel Adongo";
const age = 28;
fetchUser({ name: name, age: age });
```

The function call can even be simplified as so:

```js
fetchUser({ name, age });
```

Object destructuring can be used in module imports as well:

```js
import React, { Component } from "react";
```

## Async & Await

[Async/await](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function) provides a more readable and easy-to-reason-about way of writing asynchronous code: making it look synchronous in syntax. Combining this with the [fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch) makes async requests simplistic.

```js
(async () => {
    const response = await fetch("https://example.com/json");
    const data = await response.json();
    console.log(data);
})();
```

This also minimizes the use of the `then` and `catch` style of [Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises). By the way, anonymous function with fat arrow syntax is very useful when writing simplistic code.

> ## Code Simplicity!

## Spread syntax

Expanding an object to construct a new object or expanding an array as arguments to a function has never been simpler with [spread syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax):

```js
let data = { name: "Samuel Adongo", age: 28 };

// prints { name: 'Samuel Adongo', age: 28, weight: 75 }
console.log({ ...data, weight: 75 });



function sum(x, y, z) {
  return x + y + z;
}

const numbers = [1, 2, 3];
console.log(sum(...numbers)); // prints 6
```

## Some functional programming

[Array methods](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) such as filter, map, reduce, sort, reverse, every, find, includes, forEach, keys, entries and many already existing ones serve as convenient functions for performing common task.

```js
const numbers = [1, 2, 3, 4, 5];
console.log(
    numbers
        .map(number => number * 2) // multiply each by 2
        .filter(number => number % 2 == 0) // select only even numbers
        .reverse() // reverse array in descending order
);
```

These are just few of the goodies in ES6 that has made coding in JavaScipt  more productive for me.