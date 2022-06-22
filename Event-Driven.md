# Event-Driven Programming in Node.js

Event-Driven Programming is a logical pattern that we can choose to confine our programming within to avoid issues of complexity and collision.

## Overview

Every time you interact with a webpage through it’s user interface, an event is happening. When you click a button a `click` event is triggered. When you press a key a `keydown` event is triggered. These events have associated functions that, when triggered, are executed to make a change to the user interface in some way.

Event-Driven Programming makes use of the following concepts:

- An Event Handler is a `callback` function that will be called when an event is triggered.
- A Main Loop listens for event triggers and calls the associated event handler for that event.

## EventEmitter :

We access the EventEmitter class through the events module. Once imported we’ll need to create a new object from the class to start using it.

```js
const EventEmitter = require("events").EventEmitter;
const myEventEmitter = new EventEmitter();
```

### Example :

Creating a chat room, We want to alert everyone when a new user joins the chat room.

```js
const EventEmitter = require("events").EventEmitter;
const chatRoomEvents = new EventEmitter();

function userJoined(username) {
  // Assuming we already have a function to alert all users.
  alertAllUsers("User " + username + " has joined the chat.");
}

// Run the userJoined function when a 'userJoined' event is triggered.
chatRoomEvents.on("userJoined", userJoined);
```

The next step would be to make sure that our chat room triggers a userJoined event whenever someone logs in so that our event handler is called. EventEmitter has an emit method that we we use to trigger the event.
We would want to trigger this event from within a login function inside of our chatroom module.

```js
function login(username) {
  chatRoomEvents.emit("userJoined", username);
}
```

## Removing Listeners :

To remove event listeners in EventEmitter we can use the `removeListener` or `removeAllListeners` method :

```js
const EventEmitter = require("events").EventEmitter;
const chatRoomEvents = new EventEmitter();

function displayMessage(message) {
  document.write(message);
}

function userJoined(username) {
  chatRoomEvents.on("message", displayMessage);
}

chatRoomEvents.on("userJoined", userJoined);
```

- if we want to remove the `displayMessage` function from the message event’s list of handlers:

```js
chatRoomEvents.removeListener("message", displayMessage);
```

## Object Oriented Programming + Event-Driven Programming :

The Object Oriented approach promotes the idea that all behavior of an individual unit (or object) be handled from code within that unit. Using this approach, applications are built with many different units that all speak to and interact with each other. These two paradigms make for a very valuable combination in a wide variety of situations.

### Example :

Let’s imagine we have a hungry alligator, represented by the gator class. Using a non-event-driven approach, the process of eating for our alligator looks like this:

```js
const EventEmitter = require("events").EventEmitter;
const myGatorEvents = new EventEmitter();

class Food {
  constructor(name) {
    this.name = name;
    // Become eaten when gator emits 'gatorEat'
    myGatorEvents.on("gatorEat", this.becomeEaten);
  }

  becomeEaten() {
    return "I have been eaten.";
  }
}

var bacon = new Food("bacon");

const gator = {
  eat() {
    myGatorEvents.emit("gatorEat");
  },
};
```

## References :

- [Event-Driven Programming in Node.js](https://www.digitalocean.com/community/tutorials/nodejs-event-driven-programming)

- [Event - Node.js (Cheat Sheet)](https://nodejs.org/api/events.html)
