## Classes

Classes are a blueprint for creating objects in JavaScript. They define the properties and methods that an object will have, and can be used to create multiple instances of that object.

There are three main ideas that make classes useful:

1. Encapsulating: Classes allow you to encapsulate behavior within objects, which bundles data and methods into a single unit. This makes it easier to reason about and debug your code.

2. Inheritance: By extending classes, you can create new classes that inherit the properties and methods of existing classes, which allows you to build on top of existing functionality and create more complex objects.

3. Abstraction: Classes can be used to abstract away complex implementation details, making it easier to use and interact with your code.

Classes will be used with older React code. While a lot of React components now are made as functions, there is plenty of legacy code that will still use classes.

```javascript
// Classes are always capitalized
class Animal {
  // Requires a constructor function which is called whenever the object is created.
  // You can have default values (for all functions)
  constructor(name) {
    this.name = name;
  }

  speak() {
    console.log(`${this.name} makes a noise.`);
  }
}

// Classes that extend other classes... (also known as class inheritence)
class Dog extends Animal {
  constructor(name) {
    super(name); // super() inherits the properties/methods of the 'Animal' class
  }

  speak() {
    console.log(`${this.name} barks.`);
  }
}

// Create a new instance of the class with 'new' keyword
const dog = new Dog('Spot');
dog.speak(); // output: "Spot barks."

class Rectangle {
  constructor(height = 1, width = 1) {
    this.height = height;
    this.width = width;
  }
  getArea() {
    console.log(`The area is ${this.height * this.width}`);
  }
}

let myRectangle = new Rectangle();
let myOtherRectangle = new Rectangle(10, 5);

console.log(myOtherRectangle.width); // 5
console.log(myOtherRectangle.height); // 10
myOtherRectangle.getArea(); // 50

class Square extends Rectangle {
  constructor(side) {
    super(side, side);
  }
  getArea() {
    super.getArea();
  }
}

let mySquare = new Square(5); // 25
```
