## Classwork

#### Finish setting up the database for the giphy app:

- Try to make a query for login, and another for register
    - If the user registers, add the username/password to the table
    - If the username already exists, tell that to the user
    - If the user logs in, check if that data is in the table
    - If the username doesn't exist, tell that to the user
    - If the username/password combo is incorrect, tell that to the user
- Make a Favorites table
    - This should have a favorite_id, gif_id, and user_id
    - When a user goes to their favorites tab, query the favorites table to display the favorites associated with their ID.