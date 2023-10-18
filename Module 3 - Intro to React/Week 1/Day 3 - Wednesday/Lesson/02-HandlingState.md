# How to Use State

There are 8 key ways to handle state in React applications. There are more if you count offshoots but the main ones are listed below with a brief explanation:

1. URL (Can be used with React or ANY webpage)
   - You can use the URL to store things like filtering or pagination as a query param `someurl?page=2&filter=filterWord`
   - You can use it on sub-routes to find some information such as `/items/boots` where boots can be used to only see the items that are `boots`
2. Web Storage (Can be used with React or ANY webpage)
   - localStorage is a type of web storage
   - IndexedDB or WebSQL can be used to store things locally to the browser as needed
   - Cookies are another way which we will get into more later.
3. Local State (Used in most FE frameworks)
   - This could be the state that only that component needs to see. This wouldn't include any form of parent keeping track of state
   - Some component needs to keep track of button clicks but if no other component cares why would you store that information anywhere but in the requisite component?
4. Lifted State (Can be used in most FE frameworks but heavily used in React)
   - This is your example of the parent housing state and passing properties down to the children.
   - The parent keeps track of the state as it is 'lifted' out of the children so the parent can handle all of the heavy lifting
5. Derived State (Used in most FE frameworks)
   - State that isn't actually stored but is instead calculated based off some other piece of state
   - If you have an array of user objects, you could use a piece of state to track `totalUsers` but that is unneeded. You would instead just use the `.length` attribute and derive that value
6. Refs (React Specific for the most part)
   - DOM Reference for uncontrolled components.
   - Bypasses the need for element selectors and can be used to track state that isn't displayed
7. Context (React specific)
   - Global or Broadly Used State and functions
   - Things like logged in user, auth setting, themes, i18n are all things that might be an example of this
8. Third Party State (Most FE Frameworks have some variation of this)
   - Redux, Mobx, Recoil Libraries
   - Can help with global state management across your entire application with more robust tools at your disposal

For the purposes of this week, we will be focusing on 3, 4, and 5. We'll get into 6-8 in more depth in the future and will talk through the benefits of each.
