## So now the time has come to play around with node.

Here's the download link: https://nodejs.org/en/download

### Basics

- Node allows you to run (once or continuously) some JavaScript file using `node fileName.js`
- Comes pre-loaded with A TON of different tools to allow you to do all sorts of fun things.
- Can declare dependencies and install from NPM

### Package.json

- Three major sections for this:
  1. Scripts - This is what allows you to declare custom scripts for building, running, serving your application.
  2. Dependencies - When you install using the `npm i somePackage` tag, anything you declare gets added to the dependencies section. This allows for easy retrieval and reinstall from a github clone.
  3. devDependencies - Similar to number 2 but with this, you can also leave things you only need in dev in this category so when it's deployed ONLY the required prod dependencies will be installed.
- Also allows you to add project information and keywords for easy searching on NPM / Other published locations.
- Is important to keep up to date to allow for easy review of dependencies etc.

### The Process

- Node allows you access to the process which can house ALL sorts of information. A single log of a process can look like a little overwhelming.
- With just `process.env` it starts to look a little bit more manageable. This is the environment of the process.
- It's important to note that the process itself allows you to add and change keys. This is what allows you to customize things at run time and call them later. ANY time you call `process.env.someKey` in your app it all points to the same location regardless of imports etc. This makes it incredibly easy to declare things such as secret keys or connection information for a database, etc.
- NOTE: This is almost ALWAYS done with the use of a file added to your `.gitignore` file. Why though?

### What if we want to keep a file running continuously like a server?

- You can use the `nodemon` package as a workaround for this! With a simple `npm i nodemon` you can now call `nodemon filename` and it will run the file and keep it open, restarting anytime changes have been registered.
- You might also try npx nodemon to run the file in the package.json file.
- If you're also using Babel you can simply change the start script to: `nodemon --exec babel-node src/server.js` and now it will use both!
