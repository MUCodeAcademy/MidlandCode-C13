# The Virtual DOM

When talking about react, it's important to understand how it works. We're not talking about all of the ins and outs on day 1 of React, we're talking broad strokes. One of the most important concepts to understand with React is something called the Virtual DOM. In order to more easily understand this concept it is important to understand a couple concepts outlined below:

## Virtual DOM vs Traditional DOM

What we traditionally see in raw javascript is the DOM. This is what we worked with for the last few weeks and this is the main backbone of web technology for applications in browsers. There are some things to understand about the two first:

### Real DOM

- What is directly on the screen. We see this when we changes things with an `element.style.backgroundColor = 'blue';`
- Only way to actually change the UI for the user
- Because it doesn't handle comparison of changes well, it can lead to re-rendering of elements that didn't need to be changed. For example, look at these steps:
  1. You have a list of 5 items
  2. You change one item in the list using some sort of JS interaction
  3. The ENTIRE list on the browser gets re rendered directly via DOM Manipulation

With the above, it's not a huge issue with only a couple items in a list, but what happens if you have 100 items and you're continuously making changes to only one at a time? If you had 100 items in a list and made changes to 20 of them, that is (including the initial render of the 100 list items): 100 items rendered then 100 items rendered again for each of the 20 changes. In total that would be 2100 items rendered. That is a TON of work for the browser when only 20 items changed after initial render. Even MORE work than necessary if say only a background color of each of those list items changed as opposed to the whole item itself.

### Virtual DOM

- Sounds weird but it's a representation of the DOM that is kept in JavaScript memory
- JS performs very quickly when not having to continuously render elements to the page, so the Virtual DOM can make changes to itself at a MUCH faster speed
- Is used with some form of front-end framework such as React
- It CANNOT change the UI directly but it is used in conjunction with the Real DOM and can tell the Real DOM when to re-render and what the only items to re-render should be. So continuing the above example, the steps would look like:
  1. You have a list of 5 items
  2. The Virtual DOM creates a matching version of the Real DOM
  3. You change one thing via some sort of JS that the framework is paying attention to
  4. The Virtual DOM compares any changes to what it currently has in memory (through a process of diffing and reconciliation outlined below)
  5. The Virtual DOM tells the DOM to re-render ONLY the item(s) that changed and even then, ONLY the property of the item that needed to change.
  6. The Real DOM updates the page

So expanding on the above, because the Virtual DOM can tell the DOM when to render, it can massively improve performance. There are some issues to keep in mind with this though as there could be accidental renders if you're not careful with how you set up your React components. We'll talk more about that as we progress, but assuming you had the same 100 list items as above the Virtual DOM would allow you to have only 120 items rendered. The initial 100 and then ONLY the 20 items that were changed. That is a MASSIVE improvement over the 2100 renders that happen with just the Real DOM.

## Diffing and Reconciliation

When you're talking about the Virtual DOM you might be asking, well how does it know what to change, and when to tell the DOM to render items again? There is A LOT that goes into it and I encourage you to read more about it in the [React Documentation](https://reactjs.org/docs/reconciliation.html). Simply put though, because the Virtual DOM keeps track of the state of UI in JavaScript form, whenever there is any change / function run / etc, React uses it's diffing algorithm to compare the two. It does this by comparing the top level elements, any references to attributes, any `key` (which are a way to tell React that two items are effectively the same even if they are in different parent elements), and other things and then decides whether or not to tell the DOM to render something again.

### Re-renders

One thing to keep in mind is WHEN the DOM is actually re-rendered. Don't worry about these for right now, I simply wanted to include them so you'll have them as reference later. We talked a bit about diffing and reconciliation above, but an easier way to look at it is it will re-render if one of the following happens:

1. State Changes - State is internal values stored in a component in a way React needs them to be. We'll get more into these tomorrow
2. Prop Changes - Properties are values passed to children to help them render data needed
3. Parent Renders - This is the most straight forward. If a parent component renders, it will force re render all of the components inside of it.
4. Context Change - Context is like state for your whole application
