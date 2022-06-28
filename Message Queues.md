# Message Queues

## Socket.io Chat example :

Sockets have traditionally been the solution around which most real-time chat systems are architected, providing a bi-directional communication channel between a client and a server The server can push messages to clients, Whenever you write a chat message, the idea is that the server will get it and push it to all other connected clients.

I will submit the Link of the example in reference section at the End.

## Rooms :

A room is an arbitrary channel that sockets can join and leave. It can be used to broadcast events to a subset of clients.

### Joining and leaving :

You can call join to subscribe the socket to a given channel:

```js
io.on("connection", (socket) => {
  socket.join("some room");
});
```

And then simply use to or in (they are the same) when broadcasting or emitting:

```js
io.to("some room").emit("some event");
```

You can emit to several rooms at the same time:

```js
io.to("room1").to("room2").to("room3").emit("some event");
```

In that case, a union is performed: every socket that is at least in one of the rooms will get the event once (even if the socket is in two or more rooms).

You can also broadcast to a room from a given socket:

```js
io.on("connection", (socket) => {
  socket.to("some room").emit("some event");
});
```

In that case, every socket in the room excluding the sender will get the event.

### Room events :

Starting with socket.io@3.1.0, the underlying Adapter will emit the following events:

- `create-room` (argument: room)
- `delete-room` (argument: room)
- `join-room` (argument: room, id)
- `leave-room` (argument: room, id)

Example:

```js
io.of("/").adapter.on("create-room", (room) => {
  console.log(`room ${room} was created`);
});

io.of("/").adapter.on("join-room", (room, id) => {
  console.log(`socket ${id} has joined room ${room}`);
});
```

## Namespaces :

A Namespace is a communication channel that allows you to split the logic of your application over a single shared connection (also called "multiplexing").

Each namespace has its own:

- event handlers :

```js
io.of("/orders").on("connection", (socket) => {
  socket.on("order:list", () => {});
  socket.on("order:create", () => {});
});

io.of("/users").on("connection", (socket) => {
  socket.on("user:list", () => {});
});
```

- rooms

```js
const orderNamespace = io.of("/orders");

orderNamespace.on("connection", (socket) => {
  socket.join("room1");
  orderNamespace.to("room1").emit("hello");
});

const userNamespace = io.of("/users");

userNamespace.on("connection", (socket) => {
  socket.join("room1"); // distinct from the room in the "orders" namespace
  userNamespace.to("room1").emit("holà");
});
```

- middlewares

```js
const orderNamespace = io.of("/orders");

orderNamespace.use((socket, next) => {
  // ensure the socket has access to the "orders" namespace, and then
  next();
});

const userNamespace = io.of("/users");

userNamespace.use((socket, next) => {
  // ensure the socket has access to the "users" namespace, and then
  next();
});
```

### Main namespace

Until now, you interacted with the main namespace, called /. The io instance inherits all of its methods:

```js
io.on("connection", (socket) => {});
io.use((socket, next) => {
  next();
});
io.emit("hello");
// are actually equivalent to
io.of("/").on("connection", (socket) => {});
io.of("/").use((socket, next) => {
  next();
});
io.of("/").emit("hello");
```

Some tutorials may also mention io.sockets, it's simply an alias for io.of("/").

```js
io.sockets === io.of("/");
```

Note :

- Existing namespaces have priority over dynamic namespaces. For example:

```js
// register "dynamic-101" namespace
io.of("/dynamic-101");

io.of(/^\/dynamic-\d+$/).on("connection", (socket) => {
  // will not be called for a connection on the "dynamic-101" namespace
});
```

# References :

- [Socket.io Chat Example](https://socket.io/get-started/chat/)
- [Rooms](https://socket.io/docs/v4/rooms)
- [Namespaces](https://socket.io/docs/v4/namespaces/)

### Bookmark and Review

- [Socket.io Emit Cheatsheet](https://socket.io/docs/v4/emit-cheatsheet/)
