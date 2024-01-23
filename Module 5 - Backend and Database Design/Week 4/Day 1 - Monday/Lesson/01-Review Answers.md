# Review Module 5 Week 3

## Passport and Authentication

1. Explain Authentication and Authorization.

- Authentication verifies the user and authorization determines what they can access.

2. What is OAuth?

- Open Authentication: Allows for single-sign-on and allows users to give third-party access to the server.

3. What is session based authentication?

- Logging in the user with username/password. Way of having a persistent user while on a site.

4. What is a JWT?

- Stands for JSON Web Token. It is an encrypted JSON object that you can use to encrypt data and authorize users.

5. Explain the differences and benefits of cookies over JWT and vice versa.

- Cookies store less information (typically strings). JWTs are encrypted. Cookies are also easier to implement.
- Use cookies when you're trying to track user's information.
- Use JWTs when you need more information to store or encrypted information.

6. What is passport.js?

- Middleware for Node.js, simplifies authentication. Provides different built-in strategies.

7. Why would (or would not) you want to allow for a user to log in via Google or GitHub on your application?

- Benefits: You don't need to authenticate locally (don't need to store information). Reduces password fatigue (people don't need to remember their password).
- Disadvantages: Can be a security issue if they sign in with that service on a bunch of websites. Limits the ability to track the user. Increases dependency on external services. It requires the user to have an account on those sites.

8. Explain the process you would go through to set up passport authentication for some routes.

- Set up a strategy (local, google, facebook, etc.), set up middleware to trigger that strategy.

9. What are some of the benefits for using FireAuth in an application?

- It gives easy authentication methods.

10. What is FireAuth and why might it be useful?

- Part of Google's Firebase platform, FireAuth allows for easy authentication.

## Sockets

1. What are WebSockets?

- They're endpoints for sending and receiving data with the server. They let users connect to a server and get real-time updates.

2. How can you utilize sockets to improve your application?

- You can ensure that data stays in sync across all users. Examples: chat application and live updates.

3. What are some of the things to look out for with socket implementation?

- Ensuring that data is sent to the intended socket.
- Ensuring that data that is sent is updated. 
- Only disconnect/reconnect users when necessary.

4. How would you add sockets to a React application?

- Use `socket.io` package for the server, use `socket.io-client` for the front-end. Connect to the server, and send data with events.