# Component Types

In React, there are two main ways to declare components. While there are many offshoots of these two, the big two are functional and class based components. While we will talk about Class based components here, React now mainly uses functional components instead, and so the remainder of the course will be focusing on functional components.

## Class Based Components

Class based components are one of the most robust ways of creating components and for a long time were (still are with _some_ older code but are being used less and less) the best option for the majority of components. They follow a pattern that creates an ES6 class that then returns a `render` function that allows for the UI to be updated. At this point, class based components are almost exclusively used for ErrorBoundaries.

```javascript
import React from "react";

class Welcome extends React.Component {
  // We'll talk more about props tomorrow. If your component isn't using them, then you can omit the constructor.
  // For the sake of argument let's say they are needed so your component would have this added.

  constructor(props) {
    super(props); // Allows the component to inherit methods from its parent (React.Component)
  }

  // Any class attributes or methods can go here

  // This is the function that gets run when displaying something to the browser
  // it MUST return some form of jsx that will render to the page
  render() {
    return <div>Hello!</div>;
  }
}

// Exposes the component to the outside world. At that point it can be used in any other component by importing it and putting <Welcome / > in the JSX
export default Welcome;
```

As you can see you're basically just creating a class with a required render function. That function is what returns the actual JSX to render.

## Functional Components

In contrast to Class based components, functional components are literally just that: A function that returns something to render to the UI. They are gaining a lot more popularity ESPECIALLY with the addition of React Hooks. For the longest time they were not able to do everything a class based component could do. Because Hooks are a newer addition, it would be too difficult to rewrite all of the class components in existing application to utilize Hooks as functional components. Taking the example from above, a functional component would look like:

- OPTION 1 - Declaring and exporting in a single line with `export default function`

```javascript
import React from "react";

// As you can see, props get passed into the function as opposed to a constructor as it would be in a class
export default function Welcome(props) {
  // The function needs a return statement that returns the JSX to render (much like the return value of )
  return <div>Hello!</div>;
}
```

- OPTION 2 - Creating the function as an arrow function (generally seen more often) and exporting on a lower line

```javascript
import React from "react";

// As you can see, props get passed into the function as opposed to a constructor as it would be in a class
const Welcome = (props) => {
  // The function needs a return statement that returns the JSX to render (much like the return value of )
  return <div>Hello!</div>;
};
export default Welcome;
```

As you can see, the components are STILL named with a capital letter at the beginning. Whether it is a class or functional component, you ALWAYS have the component be capitalized and follow Pascal Casing `ExampleComponent` as opposed to `exampleComponent`. That makes it clear WHAT that export is through the capitalization of it's name. In addition, it is also required by React.

# Rendering with Class or Functional Components

While not mentioned above, one of the MOST important things about rendering is that there can be only _ONE_ top level HTML element in the render function / returned by the functional component. The following would be invalid JSX and would actually trigger an error at compile time (the same would be true if it were in a class's render function):

```javascript
export default function Welcome(props) {
  // The function needs a return statement that returns the JSX to render (much like the return value of )
  return (
    <div>Hello!</div>
    <div>Hello!</div>);
}
```

Everything needs to be in a single element. There are two ways to fix the above, the first would be to simply wrap everything in a div like:

```javascript
export default function Welcome(props) {
  // The function needs a return statement that returns the JSX to render (much like the return value of )
  return (
    <div>
      <div>Hello!</div>
      <div>Hello!</div>
    </div>
  );
}
```

But what if that might mess up your styling to have another parent div? JSX/React has a special element that you can use as a wrapper that doesn't break layout. It is simply an empty element (`<></>`) called a JSX fragment. You could then have the above look like:

```javascript
export default function Welcome(props) {
  // The function needs a return statement that returns the JSX to render (much like the return value of )
  return (
    <>
      <div>Hello!</div>
      <div>Hello!</div>
    </>
  );
}
```
