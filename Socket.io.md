# Socket.io

## Web Socket :

WebSocket : is a computer communications protocol, providing full-duplex communication channels over a single TCP connection.

The WebSocket protocol enables interaction between a web browser (or other client application) and a web server with lower overhead than half-duplex alternatives such as HTTP polling, facilitating real-time data transfer from and to the server.

## How does Websocket work?

![Websocket works](./assets/websocket%20work.png)

The client asks to open a WebSocket connection, and the server responds (if its able to). If this initial handshake is successful, the client and server have agreed to use the existing TCP/IP connection that was established for the HTTP request as a WebSocket connection.

# Socket.IO :

Socket.IO is a JavaScript library for real-time web applications. It enables real-time, bi-directional communication between web clients and servers. It has two parts − a client-side library that runs in the browser, and a server-side library for node.js. Both components have an identical API.

## Real-time Applications :

A real-time application (RTA) is an application that functions within a period that the user senses as immediate or current.

Examples of real-time applications :

- Instant messengers.
- Push Notifications.
- Collaboration Applications.
- Online Gaming.

## Socket.IO - Environment :

To get started with developing using the Socket.IO, you need to have Node and npm (node package manager) installed. Then we need to install `Express` and `Socket.IO`. To install these and save them to package.json file, enter the following command in your terminal, into the project directory :

```
npm install --save express socket.io
```

Example : (this require Socket.IO), it will log "A user connected", every time a user goes to this page and "A user disconnected", every time someone navigates away/closes this page.

```js
var app = require("express")();
var http = require("http").Server(app);
var io = require("socket.io")(http);

app.get("/", function (req, res) {
  res.sendFile("E:/test/index.html");
});

//Whenever someone connects this gets executed
io.on("connection", function (socket) {
  console.log("A user connected");

  //Whenever someone disconnects this piece of code executed
  socket.on("disconnect", function () {
    console.log("A user disconnected");
  });
});
http.listen(3000, function () {
  console.log("listening on *:3000");
});
```

After completing the above procedure, the index.html file will look as follows :

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Hello world</title>
  </head>
  <script src="/socket.io/socket.io.js"></script>
  <script>
    var socket = io();
  </script>
  <body>
    Hello world
  </body>
</html>
```

If you refresh your browser, it will disconnect the socket connection and recreate. You can see the following on your console logs :

```
A user connected
A user disconnected
A user connected
```

### Socket.IO - Event Handling

Sockets work based on events. There are some reserved events, which can be accessed using the socket object on the server side.

These are :

- Connect
- Message
- Disconnect
- Reconnect
- Ping
- Join and
- Leave.

The client-side socket object also provides us with some reserved events, which are −

- Connect
- Connect_error
- Connect_timeout
- Reconnect, etc.

### Socket.IO - Broadcasting :

Broadcasting means sending a message to all connected clients. Broadcasting can be done at multiple levels. We can send the message to all the connected clients, to clients on a namespace and clients in a particular room. To broadcast an event to all the clients, we can use the io.sockets.emit method.

### Socket.IO - Namespaces :

Socket.IO allows you to "namespace" your sockets, which essentially means assigning different endpoints or paths. This is a useful feature to minimize the number of resources (TCP connections) and at the same time separate concerns within your application by introducing separation between communication channels. Multiple namespaces actually share the same WebSockets connection thus saving us socket ports on the server.

Namespaces are created on the server side. However, they are joined by clients by sending a request to the server.

# References :

- [Web Sockets](https://en.wikipedia.org/wiki/WebSocket)
- [Socket.io Tutorial](https://www.tutorialspoint.com/socket.io/)
- [Socket.io vs Web Sockets](https://www.educba.com/websocket-vs-socket-io/)

## Videos

- [OSI Model Explained](https://www.youtube.com/watch?v=vv4y_uOneC0&ab_channel=TechTerms)
- [TCP Handshakes Explained](https://www.youtube.com/watch?v=xMtP5ZB3wSk)

## Bookmark and Review
- [Socket.io Documentation](https://socket.io/docs/v4/)
- [Socket.io Server API](https://socket.io/docs/v4/server-api)
- [Socket.io Client API](https://socket.io/docs/v4/client-api)
- [Socket Testing Tool](https://amritb.github.io/socketio-client-tool/)
