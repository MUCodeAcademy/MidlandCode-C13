# React

What is React? Simply put, it is a font-end library created by Facebook (Meta) that provides a way for you to create more robust web apps that have a better performance and allow for a better user experience. When talking about any form of library or framework for the front end (React, Svelte, Angular, etc.) it is important to know the difference first between frameworks and libraries.

## Frameworks

Frameworks provide a predefined structure/template for creating applications.

- Include an entire list of things to use
- Very strict about how to implement each piece of the application's technology
- Highly prescriptive in how and when to use each piece
- Removes most guesswork but also reduces flexibility

Examples: Angular.js, Vue.js, Ember.js

## Libraries

Libraries are collections of tools that you can use as needed.

- Provide code you can utilize to add functionality to a page
- Limited number of things you can do right out of the box
- Usually requires extra libraries for extra functionality
- Highly un-opinionated with different approaches which is great for piecemeal implementation

Examples: React.js, Axios, jQuery 

## Why React?

Here's some stats about React compared to other frameworks: https://gist.github.com/tkrotoff/b1caa4c3a185629299ec234d2314e190

Essentially, React has had the highest market share of any front-end framework. A few years ago it was Angular.js, so in a few years React may not be the most popular anymore, which is why you should keep your eye on other technologies like Vue.js or Svelte. Still, React is the most popular, which is why we teach it in this course instead of other technologies.

Sites that use React: Facebook/Meta, Netflix, PayPal, Dropbox.

A lot of mobile applications are also made using React Native: Facebook (Meta) apps, a lot of Microsoft apps, Discord, Pinterest. [Source](https://reactnative.dev/showcase)

Here's a brief rundown of how React become so popular if you're curious: [Why React](https://jscomplete.com/learn/why-react)

# Using React

React is a SPA (Single Page Application) library that allows you to reuse code extensively and provide faster loading times even with infinitely more complex sites. Like most SPA libraries/frameworks it is component based. What does that mean though? Let's say you have a list of users in a contact table. For each user you would have to (manually or through some sort of JavaScript) create each individual item. Assuming we pull the data from an API somewhere, the steps might look like this:

1. Render a blank page with placeholder `loading` message or similar
2. Make an API call and, assuming you get the data back,
3. Loop through the array of data and for each item in the array do something like the following:
   1. Create a parent div to house user information
   2. Add any classes to the parent div
   3. Create any child elements with their needed data points (Maybe first and last name keys inside of an h2)
   4. Attach those elements in order to the parent div created in step 1
   5. Attach that parent element (with all it's children) to the needed container in the browser

So that might not be all that hard, but what if you want to use those divs (housing the user's data) elsewhere on your site? What if you only wanted to use ONE person's div elsewhere thereby not needing the loop at all? This is where the component nature of React really comes into play. While this might not make sense yet, you would do the following:

1. Create the blank page with placeholder message as before
2. Create a component with all of the template HTML that you would need for each of the users. Basically steps 2-4 but allowing for data to be passed in similar to how a function takes arguments
3. Attach the above component for each element in the array using a simple for loop OR add just one if you only needed a single user's information

What is a component? Think of it as a reusable function to create HTML / elements that will be displayed in the browser. It functions off of JSX which is basically HTML combined with javascript.
