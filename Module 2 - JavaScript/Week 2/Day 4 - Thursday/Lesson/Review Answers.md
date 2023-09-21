# Week 2 Quiz

## JavaScript

1. How would you declare a variable in JavaScript?

- let for variables that change (let x = 2)

- const for variables that don't change (const x = 2)

2. What is the difference between `==` and `===`?

- `==` - Checks to see if two values are equal
- `===` - Checks to see if two values are equal including the type

3. Name all the main primitive types.

- String
- Boolean
- Integer
- Undefined
- Null
- Double
- Float

4. What will the value of `x` be after the following code:
   ```javascript
   let x = [1, 2, 3, 4, 5];
   let y = x;
   y[0] = 0;
   ```

- x will be [0, 2, 3, 4, 5]. Since we set y = x, it points to the same place in memory, meaning if we change y we also change x.

5. What is the basic structure of a for loop?

```javascript
for (let i = 0; i < 10; i++) {
    // Code that does something each loop
}
```

6. What does "use strict" do?

- Gives you the silent errors it normally wouldn't otherwise.

7. Assuming you have the object below how would you access `user`'s dog's name?
   ```javascript
   let user = {
     name: "Billy",
     petDog: {
       name: "Roger",
     },
   };
   ```

- user.petDog.name

8. What is `"2" + "3"` in javascript?

- It will output "23"

9. What is the preferred way to include variables in a string?
    ```javascript
    let userName = "Frank";
    console.log(`The username is ${userName}`);
    ```

10. How would you have some sort of functionality run after one second? What about run EVERY second?

```javascript
// Once after one second
setTimeout(() => {
    // Code
}, 1000);

// Every second
const timer = setInterval(() => {
    // Code
}, 1000);

// If you want to stop the timer...
clearInterval(timer);
```

11. What is scope and what problems can it solve and/or fix?

- Where you can access variables depends on where you declared them. Can fix unpexpected behavivor when it comes to changing/creating variables with the same name.

12. How would you declare a function and then invoke it?

```javascript
// Declaration
const name = () => {
    // Code
}
function name() {
    // Code
}
// Invocation
name();
```

13. What are parameters and arguments?

- `parameters` - The variables that are listed inside the parenthesis in the function.
Example: function name(a, b) {}
- `arguments` - The values that you pass into a function when it's called
Example: name(a, b);

14. What are the two main ways to include JavaScript to a webpage?

- Separate file:
<script src="./script.js"></script>
- Same file inside the script tags
<script>
    //code
</script>

15. What would happen with the following code:
    ```javascript
    const x = 4;
    x = 5;
    ```

- It will give you an error because you cannot reassign constant variables.

16. What would log to the console given the following code:
    ```javascript
    let t = true;
    let f = false;
    if (t && (f || t) && (t || f || f)) {
      console.log("It is true");
    }
    console.log("It is false");
    ```

- Should be true.

19. What is an arrow function and why might you use one?

- const name = () => {

}

- Can also do an anonymous function like this:
() => {}

- You might want to use it since it can be shorter and more concise. Anonymous functions are usually used for functions that you don't need to run more than once.

## DOM

1. What is the DOM?

- Document Object Model. It's basically what the user sees on their screen.

2. How would you select any element with a class of `class1`?

- document.querySelectorAll(".class1");
- document.getElementsByClassName("class1");

3. Name some of the most common events and how you would listen for them?

- 'click', 'keypress', 'mouseenter', 'mouseover'

```javascript
element.addEventListener("click", () => {
    // Code to run when they click the element
});
```

4. How would you change the style of an element with JavaScript?

- element.style.color = "red";

5. How do you create and add a new element to the page with JavaScript?

```javascript
const newDiv = document.createElement("div");
document.body.appendChild(newDiv);
```

6. How do you get the element that fired an event callback?

- e.target

```javascript
element.addEventListener("click", (e) => {
    const clickedElement = e.target;
})
```

7. How would you remove an element with JavaScript (let's assume you have the element saved in a variable called `toDelete`)?

- `toDelete.remove()`

## Prototypical Functions

1. How would you turn an array into a string or vice versa?

- Array to string - array.join("");
- String to Array - string.split("");

2. How would you generate a random number?

- `Math.floor(Math.random() * maxValue)`

3. How would you loop through all elements in an array and add 1 to each of them?

```javascript
array.map(element => element + 1);
// Using forEach
array.forEach(elemeny => element + 1);
```

4. How would you remove all elements that are less than 4 from an array?

```javascript
array.filter(element => element >= 4);
```

5. How would you make all letters in a string lower case?

- string.toLowerCase();

6. How would you add new elements to the start or end of an array?

- To the start - array.unshift(4);
- To the end - array.push(4);

7. How and why would you make a shallow copy of an array?

- array.slice();
