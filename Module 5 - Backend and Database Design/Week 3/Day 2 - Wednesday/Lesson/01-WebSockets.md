# What are Web Sockets?

Simply put, a socket is a form of connection that is opened between a client and a server to allow continuous updates. To think about it another way, if we take an example like a chat room, think of it like this:

1. User calls in to the 'server' to ask for data, then leaves the line open
2. Other users do the same and tell the server any new data. Only the server can hear that new data
3. ANY time the server gets new data, it immediately tells everyone connected.
4. When the user navigates away form the site, they hang up

That removes the need for multiple recalls as it stays open in the background, the server doesn't have to cache information and only has to handle incoming calls when they connect or send data. Otherwise it's just pushing data out.

# How are they implemented?

Because it is done with a connection from client to server and vice-versa, it requires code on both ends to work. Basically you need to do the following:

1. Set up the server to allow for socket connections (simplest to do with the `socket.io` package which we will cover shortly)
2. Set up handler functions to handle whatever incoming socket events you decide. The event names for these are chosen by you, so think of them like variables
3. Set up the front-end to automatically connect to the server's socket
4. Set the front-end to send and handle socket events and the code needed to do so

From there you can (depending on the package) use an `emit` or an `on` function to send out or listen for events of some sort. Let's take a further look.
