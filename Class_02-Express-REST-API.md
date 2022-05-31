# Express REST API
### 1- Review: ES6 Classes
### 2- Using Express Routing
### 3- Express Routing


> # Classes
 Classes are a template for creating objects. They encapsulate data with code to work on that data. Classes in JS are built on prototypes but also have some syntax and semantics that are not shared with ES5 class-like semantics.

## Class declarations

One way to define a class is using a class declaration.
    
    class newClass {
    constructor(height, width) {
        this.height = height;
        this.width = width;
    }
    }

## Class expressions

A class expression is another way to define a class.

        // unnamed
    let Rectangle = class {
    constructor(height, width) {
        this.height = height;
        this.width = width;
    }
    };
    console.log(Rectangle.name);
    // output: "Rectangle"

    // named
    let Rectangle = class Rectangle2 {
    constructor(height, width) {
        this.height = height;
        this.width = width;
    }
    };
    console.log(Rectangle.name);
    // output: "Rectangle2"

## Class body and method definitions

The body of a class is the part that is in curly brackets {}. This is where you define class members, such as methods or constructor.

## Constructor

The constructor method is a special method for creating and initializing an object created with a class. There can only be one special method with the name "constructor" in a class. A SyntaxError will be thrown if the class contains more than one occurrence of a constructor method.


> # Using Express Routing
>> # Routing :

Routing refers to how an application’s endpoints (URIs) respond to client requests.

We can use them like: `app.get('path',handlePathFun);`.

        // GET method route
        app.get('/', (req, res) => {
        res.send('GET request homepage');
        });

        // POST method route
        app.post('/', (req, res) => {
        res.send('POST request homepage');
        });

        app.all('/secret', (req, res, next) => {
        console.log('Accessing the secret section ');
        next(); 
        });

## Route paths
Here are some examples of route paths based on strings.

This route path will match requests to the root route, /.

    app.get('/', (req, res) => {
    res.send('root');
    });
This route path will match requests to /about.

    app.get('/about', (req, res) => {
    res.send('about');
    });
This route path will match requests to /random.text.

    app.get('/random.text', (req, res) => {
    res.send('random.text');
    });
Here are some examples of route paths based on string patterns.

This route path will match acd and abcd.

    app.get('/ab?cd', (req, res) => {
    res.send('ab?cd');
    });
This route path will match abcd, abbcd, abbbcd, and so on.

    app.get('/ab+cd', (req, res) => {
    res.send('ab+cd');
    });
This route path will match abcd, abxcd, abRANDOMcd, ab123cd, and so on.

    app.get('/ab*cd', (req, res) => {
    res.send('ab*cd');
    });
This route path will match /abe and /abcde.

    app.get('/ab(cd)?e', (req, res) => {
    res.send('ab(cd)?e');
    });
Examples of route paths based on regular expressions:

This route path will match anything with an “a” in it.

    app.get(/a/, (req, res) => {
    res.send('/a/');
    });
This route path will match butterfly and dragonfly, but not butterflyman, dragonflyman, and so on.

    app.get(/.*fly$/, (req, res) => {
    res.send('/.*fly$/');
    });

> # Express Routing

Router is like a mini-Express application.
Router doesn’t bring in views or settings but provides us with the routing APIs like:

- `.use`
- `.get`
- `.params`
- `.route`

Create a router file :

    onst express = require('express');
    const router = express.Router();

    router.use((req, res, next) => {
    console.log('Time: ', Date.now());
    next();
    });

    router.get('/', (req, res) => {
    res.send('Home Page');
    });

    router.get('/about', (req, res) => {
    res.send('About Page');
    });

    module.exports = router;

### With Express Router we can :

- Use `express.Router()` multiple times to define groups of routes.
- Apply the `express.Router()` to a section of our site using `app.use()`.
- Use route middleware to process requests.
- Use route middleware to validate parameters using `.param()`.
- Use `app.route()` as a shortcut to the Router to define multiple requests on a route.

