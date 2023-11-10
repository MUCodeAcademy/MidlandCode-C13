# Review Module 3 Part 2

## State Management

1. What are some key ways to handle global state?

- Context, Flux, Redux, other third party tools.

2. What is Context and what is flux?

- Context - state management to share state across the entire app (global state)

- Flux - pattern to manage global state with actions, dispatchers, stores, view.
    - Implemented this with reducers

3. What is the general pattern for context?

- Create the context (createContext()) in the context file.
- Build a provider component.
- Wrap your application in that provider.
- In the components that need the context, use the `useContext` hook.

4. How could you implement the flux pattern with a hook?

- Use the `useReducer` hook and set up the actions in the reducer file.

5. What is a good folder structure for Context?

- Ultimately, it's up to you. You could put all of your context in a context folder and separate each piece of context to its own file. Also, put your reducers in their own folder.

6. What is wrong with the following bit of code:

```javascript
const [arr, setArr] = useState([1, 2, 3]);
setArr([...arr, 4]);
```

- Write the update like this: `setArr(curr => [...curr, 4]);`
- curr represents the most up-to-date state of the array. This ensures that we're using the most recent data and not 'stale' data.

7. What is a dispatch function with a flux pattern?

- An action triggers the dispatch function which updates the store.

8. What is a context provider?

- JSX element that you wrap every component in; the provider gives state/data/functions to those child components.

Example:
```js
    <ContextProvider>
        <App />
    </ContextProvider>
```

9. Assume you have an application with 30 pieces of state that could be shared across 15 different components. What would be the worst and best ways to track state in that application?

- Worst - Put useState in the highest parent component and then deliver the state as properties to each child component. This is called 'prop drilling'.

- Best - Using context or any other state management.

## Routing

1. How would you create routes and why would you want to in a React application?

- `npm install react-router-dom`. We want to use them for rendering different components based on what page they're on.

Example:

```js
<Router>
    <Routes>
        // All of your routes go here
        <Routes exact path='/' element={<HomePage />}/>
        <Routes path='/login' element={<LoginPage />}/>
    </Routes>
</Router>
```

2. How would you declare and access route parameters and why might they be useful?

- Inside the Route path write `/user/:id`, where id is the parameter that could be any value. They're useful for accessing different pages depending on the parameter.

3. What does the 'exact' do in the following code: `<Route exact path="/">`

- 'exact' ensures that the route path matches perfectly. Otherwise, if you had a route like `/users`, it will always go to `/` because it routes to the first match.

4. How would you implement sub-routes for an application?

- On the users page, set up routes like `/users/settings` or `/users/friends`

5. How do you handle Authentication with routes?

- Make a function that will check if they're authorized. Wrap the routes with that authentication function, and it will render the component they're authorized to see or it will redirect them to another accessible page. (we did this in the ProtectedRoutes file)

## API Calls in React

1. Is there any difference between API calls in React and normal JavaScript? If so, what are they?

- There is basically no difference unless you're choosing to use React Query.

2. Explain what is (and what might be) wrong with the following piece of code:

   ```javascript
   import { useState, useEffect } from "react";

   const baseUrl = "...";

   export default function useFetch(url) {
     const [data, setData] = useState(null);
     const [loading, setLoading] = useState(true);

     useEffect(() => {
       function init() {
         const response = await fetch(baseUrl + url);
         const json = await response.json();
         setData(json);
         setLoading(false);
       }
       init();
     }, [url]);

     return { data, loading };
   }
   ```

- We need to add `async` in front of function init().
- We should reset the data to null after each call.
- We should probably set loading to true at the start of the useEffect.
- We should probably use a try-catch block.

```javascript
import { useState, useEffect } from "react";

const baseUrl = "...";

export default function useFetch(url) {
    const [data, setData] = useState(null);
    const [loading, setLoading] = useState(true);
    const [error, setError] = useState(null);

    useEffect(() => {
        setLoading(true);
        setData(null);
        async function init() {
            try {
                const response = await fetch(baseUrl + url);
                const json = await response.json();
                setData(json);
            } catch (e) {
                setError(e);
            } finally {
                setLoading(false);
            }
        }
        init();
    }, [url]);

    return { data, loading };
}
```

## Hooks

1. What does the useEffect Hook do and when should you use it?

- The useEffect hook runs the code inside of it at specified intervals. Those intervals are on one of the lifecycle stages: mount, update, and unmount. It will always run the code when the component mounts regardless of what you do. It will run when the component updates depending on what you put in the dependency array. It will run when the component unmounts if you have a return inside the useEffect.

- Typically you use a useEffect either when you want to run code at a certain lifecycle stage, or for a 'side effect' like data fetching, subscribing/unsubscribing, set up/clean up events or timers.

```js
useEffect(() => {
    // Whatever you want the useEffect to do goes here.

    // Add a return if you want to run some code when the component unmounts 
    return (

    )
}, [user]); // This is the dependency array. Since I put 'user' inside the array, it will only run the useEffect when the 'user' state changes.
// If the dependency array was empty, it would only run once when the component mounts.
```

2. What is memoization and how could you use it with Hooks?

- Memoization is the process of rembering the output of a calculation. It stores it in memory to prevent it from being rebuilt.

- Two hooks: useMemo for any data type. You can also use useCallback for memoizing functions.

3. What is the difference between a custom hook and a custom function?

- They're almost the same, except for a few things: 
    - Custom hooks, like all other hooks, can only be used at the top-level of a component.
    - Custom hooks can use other hooks.
    - Usually you make a hook if you want to use it in several different files.

Example of a custom hook (put this in its own file)

```js
export default useFetchRequest() {
    // Code
}
```

4. Where can you use hooks in a React project?

- Has to be in the top-level component. You can only use them in custom hooks or functional components. You can't use hooks in class components or regular JavaScript functions.

5. What is missing from the following code:

```javascript
useEffect(() => {
  document.title = `You clicked ${count} times`;
});
```

- Dependency array. Currently, the effect will run on any update to the component. We want it to run only when 'count' changes.

```javascript
useEffect(() => {
  document.title = `You clicked ${count} times`;
}, [count]);
```

6. What (if anything) is wrong with the following custom Hook:

```javascript
export function customUserHook(data){
    [user, setUser] = useState({});
    // ... hook functionality
}
```

- If it's a hook, it has to start with 'use'.

```javascript
export function useCustomUserHook(data){
    [user, setUser] = useState({});
    // ... hook functionality
}
```

# React Query

1. What is React Query?

- It's a package that helps fetching from APIs.

2. When should you or should you not use React Query?

- If you want to. It has features from React like background refetching, caching, automatic retries. It also has built-in state for data, loading, and errors.

3. What benefits does React Query have over a custom hook?

- Built-in functionality to configure API calls.
