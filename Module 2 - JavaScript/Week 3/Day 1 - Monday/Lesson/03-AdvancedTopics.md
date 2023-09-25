# Advanced Topics

## Closures

These may become more important as we progress into more complex javascript. A closure is the combination of a function bundled together with references to its surrounding state.  In simpler terms, a closure gives you access to an outer function's scope from an inner function. 

In JavaScript, closures are created every time a function is created, at function creation time.

```javascript
function outerFunction() {
  let message = 'Hello, world!';

  function innerFunction() { // this 'closes over' the variable message, and allows it to access its value
    console.log(message);
  }
  return innerFunction;
}

const inner = outerFunction();
inner(); // output: "Hello, world!"

function multiplier(a) {
  let timesCalled = 0;
  function returnedFunction(b) {
    timesCalled++;
    console.log(`TimesCalled with multiplier ${a}: ${timesCalled}`);
    console.log("Result: ", a * b);
  }
  return returnedFunction;
}

let timesTwo = multiplier(2);
let timesThree = multiplier(3);
timesTwo(2); // timesCalled = 1
timesThree(2); // timesCalled = 1
timesTwo(2); // timesCalled = 2
timesThree(2) // timesCalled = 2
multiplier(2)(2); // timesCalled = 1

function timesTwoNoClosure(a, b) {
  let timesCalled = 0;
  timesCalled++;
  console.log(timesCalled);
  return a * b;
}
timesTwoNoClosure(2, 2); // timesCalled = 1
timesTwoNoClosure(2, 2); // timesCalled = 1
timesTwoNoClosure(2, 2); // timesCalled = 1
timesTwoNoClosure(2, 2); // timesCalled = 1
timesTwoNoClosure(2, 2); // timesCalled = 1
```

## Logical || operator vs Nullish Coalescing operator ??

What if you want to set some variable to another, but have a default value. In parameters for functions that's quite easy, but with normal declaration, you have to follow one of the two patterns:


Logical OR Operator. X will be set to whatever the value of Y is UNLESS y is falsy.
```javascript
let x = y || 12;
```

Nullish Coalescing Operator. If 'y' is null or undefined, the value of 'x' will be assigned to the default value of '12'.
If 'y' is not null or undefined, the value of 'x' will be assigned to the value of 'y'.
```javascript
let x = y ?? 12;
```

## Object and Array Destructuring

### Array Destructuring

Let's say you have an array but you want to grab the first element out of it and save it into a new variable. You could do the following:

```javascript
let students = ["John", "Steve", "George"];
let first = students[0];
```

There is nothing wrong with that, but an easier (and better) way to do it is the following:

```javascript
let students = ["John", "Steve", "George"];
let [first] = students;
```

By surrounding the variable name in `[]` it will extract the 0th index and save it into that variable. You can do it with more variables such as `let [first, second, third] = students`. As you can see, the real benefit is when you need to extract out multiple pieces of the array. It is important to note that although we use the word "extract" it doesn't actually change the array in any way. It also will not update if the array is changed in any way, it ONLY pulls the value at run time. In addition, you can then change the `first` variable without changing the array.

### Object Destructuring

Similarly to the above, you can strip out (without editing the object itself) the values of individual keys. Take the following object and code:

```javascript
const me = { first: "Justin", last: "Luce", age: 23 };

const { first, age } = me;
```

By running that code, it will create a variable named `first` that is equal to `me.first` and the same concept for the variable `age`. Similarly to the array destructuring, any future edits to `me.first` will not change the `first` variable and vice versa.

## Rest For Functions

Let's say you have a function that can take in two arguments and only two. Well, that's easy: `const funcName = (paramA, paramB) =>{}`. What happens though if you could take in 2 but then there might be a third, and potentially 4th, etc? Well you can update the code to look like:

```javascript
// It's important to note that the third variable doesn't have to be called rest, but the ... ARE required.
const funcName = (paramA, paramB, ...rest) => {};
```

With the above, if you called the function with:

```javascript
funcName(1, 2, 3, 4, 5, 6, 7);
```

Then `paramA` would have a value of `1`, `paramB` would be `2` and then `rest` would be an array with ANY other arguments passed in.

## Module Pattern

Module pattern. The main purpose of modules is to allow you to make reusable code that is in small independent units, and create private and public properties and methods. Modules can be exported and imported by other parts of the application, which we'll get more into tomorrow when we talk about Node.js.

```javascript
const myModule = (function() {
    'use strict';

    const privateProperty = 'Hello World';

    function privateMethod() {
        console.log(privateProperty);
    }

    return {
        publicMethod: function() {
            privateMethod();
        }
    };
}());

myModule.publicMethod();                    // outputs 'Hello World'
console.log(myModule.privateProperty);     
// The above console log is undefined because privateProperty is not returned by the enclosing function and is not a property of the myModule object – it's private within the closure.
myModule.privateMethod();                  // is TypeError
```
