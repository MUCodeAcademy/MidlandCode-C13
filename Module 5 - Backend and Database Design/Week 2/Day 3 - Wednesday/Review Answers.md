# Review Week 1

## Databases

1. What steps (if any) need to be taken to store passwords in a database?

- They should be hashed first.

```js
// Use the bcrypt.hash function and put in the password and salt rounds
bcrypt.hash(password, 10);
```

2. How would you find all users based off a username in an SQL database? (Assume you have a users table with `id`, `username`, and `email` columns)

```SQL
SELECT username 
FROM users
WHERE username = "Username";
```

3. What are joins in SQL?

- Combine two or more tables together based on a shared column.

```SQL
SELECT * FROM users
JOIN favorites ON users.id = favorites.id;
```

4. In MySQL databases, what are the main different types to store values?

- INT - integer
- DATE - a date (YYYY-MM-DD)
- TEXT - text
- DATETIME - a date and a time (YYYY-MM-DD HH:MI:SS)
- VARCHAR - variable character
- DECIMAL - a fixed-point decimal

5. If you need to store user information, all the blog posts from a user, and all their friends, how would you structure that in SQL?

It's up to you, but here's a good example

- Users Table - userId, username, password
- Blog Table - blogId, userId, content
- Friends Table - friendId, userId, requests

6. How would you get all users from a database (assume there's a 'users' table) sorted in descending order from oldest to youngest?

```SQL
SELECT * FROM users
ORDER BY age DESC;
```

7. What is the difference between `HAVING someColumn < 10` and `WHERE someColumn < 10`?

- They do the exact same thing, but you can't use `WHERE` with aggregate functions like `SUM` or `COUNT`.
- `WHERE` - Used to filter rows before they're aggregated.
- `HAVING` - Used to filter rows after they're aggregated.

8. How would you add up all numbers in a column for all the rows that match the same criteria?

```SQL
SELECT SUM(users.score) FROM users;
```

9. Assuming you have a column name of `userID` but you wanted it to appear as `uID` in your output, how would you do that?

- You would use an alias.

```SQL
SELECT userID AS uID FROM users;
```

## API Creation and Express

1. How do you set up express?

- After you did `npm i express` in the server.js file:

```js
// Import express
const express = require('express');
// Creates a new instance of express
const app = express();
```

2. How do you set up SQL queries in an express application?

- After you did `npm i mysql`

```js
// Import mysql
const mysql = require('mysql');
const connection = mysql.createConnection({
    // Database info
});

// Connect to the database
connection.connect();

connection.query(
    // Put your SQL query here
)
```

3. In express how and why would you implement a middleware?

- Middleware is used for any functionality to happen between the request and the route. Mainly used for authenticating users.

```js
function middlewareFunction() {
    // Stuff you want to do
    next();
}

app.get('/login', middlewareFunction, (req, res, next) => {});
```

4. What is the `next()` function and why should you use it?

- Used in middleware functions to move on to the next function or the final route.

5. What are the main http verbs and when would you use each?

- `GET` - Reading data
- `POST` - Sending data
- `PUT` - Creating new data
- `PATCH` - Changing data
- `DELETE` - Removing data

6. What function arguments are available to Express JS route handlers / middleware and what are they?

- `req` - Request, holds information about the request sent to the server.
- `res` - Response, holds information about the response being sent from the server.
- `next` - Function that lets middleware move on to the next step.

7. How would you send a response?

```js
return res.send("Whatever");
```

8. Will the following code cause any errors if a user went to that route? Explain why or why not.

```js
app.get("/route", (req, res) => {
    if (true) {
        res.send("Valid");
    }
    res.send("invalid");
});
```

- It will always send two responses which will cause an error because you can only send one reponse per request. The solution is either add a return in front of the first res.send(), or make it an if-else statement.

```js
app.get("/route", (req, res) => {
    if (true) {
        return res.send("Valid");
    } else {
        return res.send("invalid");
    }
});
```