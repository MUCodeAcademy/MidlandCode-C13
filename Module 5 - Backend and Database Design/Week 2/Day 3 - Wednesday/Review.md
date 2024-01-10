# Review Week 1

## Databases

1. What steps (if any) need to be taken to store passwords in a database?

2. How would you find all users based off a username in an SQL database? (Assume you have a users table with `id`, `username`, and `email` columns)

3. What are joins in SQL?

4. In MySQL databases, what are the main different types to store values?

5. If you need to store user information, all the blog posts from a user, and all their friends, how would you structure that in SQL?

6. How would you get all users from a database (assume there's a 'users' table) sorted in descending order from oldest to youngest?

7. What is the difference between `HAVING someColumn < 10` and `WHERE someColumn <10`?

8. How would you add up all numbers in a column for all the rows that match the same criteria?

9. Assuming you have a column name of `userID` but you wanted it to appear as `uID` in your output, how would you do that?

## API Creation and Express

1. How do you set up express?

2. How do you set up SQL queries in an express application?

3. In express how and why would you implement a middleware?

4. What is the `next()` function and why should you use it?

5. What are the main http verbs and when would you use each?

6. What function arguments are available to Express JS route handlers / middleware and what are they?

7. How would you send a response?

8. Will the following code cause any errors if a user went to that route? Explain why or why not.

```js
app.get("/route", (req, res) => {
    if (true) {
        res.send("Valid");
    }
    res.send("invalid");
});
```