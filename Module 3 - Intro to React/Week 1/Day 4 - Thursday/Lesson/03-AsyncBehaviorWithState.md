# Issues With State

One of the biggest issues with state is that any updates to state are made asynchronously. While this might not be a major issue right off the bat, it can cause some problems if you're not careful with your design patterns. One common mistake is the following:

1. Handle some form of input / interaction
2. Update state
3. Immediately use the newly updated state in someway

If you were to do the above that could cause some problems for you if you're not careful. Let's say for the sake of argument that the JS for updating state is `update(newValue)` and the value is stored in `state`. Depending on the method of state management you're using, that's actually not too far off from what it could be. Bearing that in mind, let's take a look at this function handling an input into a field.

```javascript
function handleEvent(e) {
  updateState(e.target.value);
  otherFunction(state); // passing what would be the new state
}
```

Because of the asynchronous nature, it is very likely that the argument that would be passed into `otherFunction()` would be the old version of state. It is however easy to get around this. There are many different methods, but the easiest for something this simple would be

```javascript
function handleEvent(e) {
  updateState(e.target.value);
  otherFunction(e.target.value); // passing what will be used to update state.
}
```

By doing the above, you're still utilizing state for your component and the React lifecycle, but you're bypassing the asynchronous nature for ONLY that one function call, thereby not having any issues.
