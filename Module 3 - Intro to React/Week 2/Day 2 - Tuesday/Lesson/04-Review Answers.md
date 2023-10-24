# Key Takeaways

A lot was covered this module and it probably feels a bit overwhelming at the moment. Bearing that in mind, let's take a look at the MOST important things to focus on for now. While these aren't the only things you need to retain, if you get these concepts down, then you'll have a much easier time grasping the rest of the topics in React as well as the other topics from this week. We'll go through and give an explanation of these together, but the key topics are:

1. What is React?

- JavaScript library created by Meta (formerly known as Facebook).

2. Creating a React Application and Folder Structure:

- Creating a React application: `npx create-react-app app-name`
- To run the application: `npm start`
- src folder: Used for the main files (logic, components, styling)
- public folder: Used for images, anything you want to be public

3. What is the Virtual DOM?

- React's representation of the traditional DOM (document object model). When you work with React, you work with the virtual DOM. React efficiently updates the page with comparisons between the virtual DOM and the traditional DOM.

4. What is wrong with this return statement?
    ```javascript
        return (
            <div>
                Hello!
            </div>
            <div>
                Goodbye!
            </div>
        )
    ```

- All of the elements need to be contained inside one parent div.

5. What does `<></>` mean in JSX?

- They are called JSX Fragments or React Fragments. Allows you to group multiple elements together without adding an extra node to the DOM.

6. What are Components?

- Similar to regular JavaScript functions - a piece of reusable code that has their own properties/state. Usually returns something to render to the screen.

7. What are the two main ways to declare components and what are the differences?

- Class Components (not very common anymore):
```javascript
    class ComponentName extends React.Component {
        constructor(props) {
            super(props);
        }

        render() {
            return <div>Hello</div>
        }
    }
```

- Functional Components:
```javascript
    function ComponentName(props) {
        // javascript logic goes here

        return (
            <div>Hello</div>
        )
    }
```

8. What Triggers a Component to Re-Render in React?

- Its state changes
- Its props change
- Its parent changes
- Its context changes

9. Handling Events and User Interaction:

```javascript
function buttonClicked(e) {
    //code
}

<button onClick={buttonClicked}>Click</button>
// If you want to access the element they clicked on, you need to pass in the event object
<button onClick={e => buttonClicked(e.target.value)}>
```

10. What are Props?

- Props (properties) are a way to pass data into other component.

11. What Is State?

- Object in React that stores data. We need to use state since React won't re-render regular variables.

12. Handling State in class or functional components?

- In functional components:

```javascript
import { useState } from 'react';

const [username, setUsername] = useState('');

setUsername("Justin");
```

- In class components, they have state inherently, so you don't need useState:

```javascript
this.username = "";

setUsername("Justin");
```

13. Atomic Design principles:

- Method of breaking down components into their smallest parts. 
- Atoms, molecules, organisms, pages, templates.

14. Styled components:

- Instead of writing CSS in a CSS file, you can create your own custom components with the emotion package. It increases reusability and smaller CSS files.

```javascript
export const Button = styled.button`
    color: red;
`
```