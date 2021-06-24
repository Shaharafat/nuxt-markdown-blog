---
title: JavsScript Principles You should Know
description: This is a simple desctip of my postIn this blog, I will discuss some core JavaScript concepts. If you are new to the JavaScript world, then you must have a clear idea about that topic. I will try to explain those very clear and concisely. 
author:
  name: Shah Arafat
  image: /_nuxt/assets/images/arafat.jpg
  designation: Frontend Developer
---
In this blog, I will discuss some core JavaScript concepts. If you are new to the JavaScript world, then you must have a clear idea about that topic. I will try to explain those very clear and concisely. 
#Types
There are 7 primitive data types in JavaScript. Those are:
- Number
- String
- Boolean
- null
- undefined
- Big int
- Symbol

and 2 structural data types:
- Object
- Function

**No other types?** In JavaScript, there are no other fundamental value types other than the ones we have just enumerated.​ The rest are all objects! 

For example, even arrays, dates and regular expressions fundamentally ​are​ objects in JavaScript.

#Expressions
An expression is a valid set of literals, variables, operators, and expressions that evaluates to a single value.

```js
0 // 0

1 + 1 // 2

'Hello' + ' ' + 'World' // 'Hello World'

{ answer: 42 } // { answer: 42 }

Object.assign({}, { answer: 42 }) // { answer: 42 }

answer !== 42 ? 42 : answer // 42
```

Each example shown above is an expression. Every line represents some value.

#Hoisting
In JS hoisting is a behaviour, where all variable declared with the `var` keyword and all functions defined with function declaration is moved to the top of the program.

So that if you use a function before functions declaration, it will not throw any error.

```js
greeting('Programmer'); // Programmer

// functions declaration
function greeting(name){
  console.log(name);
}
```

This program will run perfectly, though you used the function before the declaration. But JS hoisting moves the function on top of all code. Like:

```js
// functions declaration
function greeting(name){
  console.log(name);
}

greeting('Programmer');
```
That's why it is perfectly working.
> Remember, Hoisting happens for function declaration. If you define a function by functions expression. It will give you an error.

In the case of a variable, when we declare a variable with the `var` keyword, JavaScript will hoist the variable to the top of the program. But, its value will not be assigned before we reach the line where we assigned the value.

```js
console.log(name); // undefined

var name = 'John Doe';

console.log(name); // 'John Doe'
```

If you run this, you will not get any error. Instead, it will print undefined. Because of hoisting, variable declaration moved to the top but the value was not assigned. So, the value is undefined. After reaching the line where the value was assigned then the value is visible as the value of that variable. 

From ES6 variable declaration with `let` and `const` does not have any hoisting issue. We will discuss that later.

#Global Block Binding

When we declare a variable with the `var` keyword, it changes the global object. For the browser, it is a window object.

```js
var RegExp = 'Regular Expression';

console.log(window.RegExp === RegExp); // true
```
It's a big issue because we are mutating the global object. In the example above it 'RegExp' variable change the global 'RegExp', Which is unexpected. 

Here `let` and `const` comes into the picture. If we declare a variable using `let` and `const`, it will never mutate the global object.

```js
let RegExp = 'Regular Expression';

console.log(window.RegExp === RegExp); // false
```


#Block Bindings in For loop

```js
for (var i = 0; i < 5; i++){
  console.log(i); // 0 1 2 3 4 
}

console.log(i) // 5
```
In the example above, I defined the variable 'i' with `var` keyword. after loop execution complete, the variable 'i' is visible outside the block or for loop. But we don't want that. Here `let` keyword comes to the rescue. 
```js
for (let i = 0; i < 5; i++){
  console.log(i); // 0 1 2 3 4 
}

console.log(i) // i is not defined.
```
Here the value of the variable exists only inside the for loop. so, below the loop, we will get an error.

#Arrow Functions
Arrow function is a new way of writing functions in JavaScript.
Syntax: 
```js
const func = (param1, param2, ...) => {
  // ....
}
```
The syntax is very simple, right? If you have only one parameter, then you do not need to use a brace for the parameter and you can directly return a value without using the second bracket.

```js
const func = x => x * x;

func(2); // returns 4
```

> Remember, when we define an arrow function expression. It's not hoisted. It's an expression, not a declaration. Function declarations are hoisted, not function expressions.
That's why we need to write the function before we use it. Another thing is arrow function doesn't have its own `this`.

With all that being said, I highly recommend you keep learning JavaScript. Trust me it's a very powerful and impressive language.

Thank you for reading my blog. Feel free to connect on [Linkedin](https://www.linkedin.com/in/shah-arafat/) and [Twitter](https://twitter.com/sharafhat)
