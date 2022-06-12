# Readings: Express, NPM, TDD, CI/CD

# NodeJS :

Node.js : is an open-source, cross-platform runtime environment that allows developers to create all kinds of server-side tools and applications in JavaScript.

### Node benefits :

- Great performance! Node was designed to optimize throughput and scalability in web applications and is a good solution for many common web-development problems.
- Code is written in "plain old JavaScript", which means that less time is spent dealing with "context shift" between languages when you're writing both client-side and server-side code.
- JavaScript is a relatively new programming language and benefits from improvements in language design when compared to other traditional web-server languages as Python, PHP, etc.
- The node package manager (NPM) provides access to hundreds of thousands of reusable packages.
- Node.js is portable and well-supported by many web hosting providers.
- It has a very active third party ecosystem and developer community, with lots of people who are willing to help.

# Express :

Express : is the most popular Node web framework, and is the underlying library for a number of other popular Node web frameworks.

### It provides mechanisms to:

- Write handlers for requests with different HTTP verbs at different URL paths (routes).
- Integrate with "view" rendering engines in order to generate responses by inserting data into templates.
- Set common web application settings like the port to use for connecting, and the location of templates that are used for rendering the response.
- Add additional request processing "middleware" at any point within the request handling pipeline.

### Helloworld Express Example :

```js
const express = require("express");
const app = express();
const port = 3000;

app.get("/", function (req, res) {
  res.send("Hello World!");
});

app.listen(port, function () {
  console.log(`Example app listening on port ${port}!`);
});
```

### Importing and creating modules :

A module is a JavaScript library/file that you can import into other code using Node's `require()` function.

Express itself is a module, as are the middleware and database libraries that we use in our Express applications.

The code below shows how we import a module by name, using the Express framework as an example:

```js
const express = require("express");
const app = express();
```

If you want to export a complete object in one assignment instead of building it one property at a time, assign it to `module.exports` as shown below (you can also do this to make the root of the exports object a constructor or other function):

```js
module.exports = {
  area: function (width) {
    return width * width;
  },

  perimeter: function (width) {
    return 4 * width;
  },
};
```

You can think of `exports` as a shortcut to `module.exports` within a given module. In fact, `exports` is just a variable that gets initialized to the value of `module.exports` before the module is evaluated. That value is a reference to an object (empty object in this case).

This means that `exports` holds a reference to the same object referenced by `module.exports`. It also means that by assigning another value to `exports` it's no longer bound to `module.exports`.

A common convention for Node and Express is to use error-first callbacks.

### Handling errors :

```js
app.use(function (err, req, res, next) {
  console.error(err.stack);
  res.status(500).send("Something broke!");
});
```

### Most Important Express Methods :

- POST.
- PUT.
- DELETE.
- GET.

# NPM :

npm : is the world's largest software registry. Open source developers from every continent use npm to share and borrow packages, and many organizations use npm to manage private development as well.

### npm consists of three distinct components:

- the website.
- the Command Line Interface (CLI).
- the registry.

### Use npm to :

- Adapt packages of code for your apps, or - incorporate packages as they are.
- Download standalone tools you can use right away.
- Run packages without downloading using npx.
- Share code with any npm user, anywhere.
- Restrict code to specific developers.
- Create organizations to coordinate package maintenance, coding, and developers.
- Form virtual teams by using organizations.
- Manage multiple versions of code and code dependencies.
- Update applications easily when underlying code is updated.
- Discover multiple ways to solve the same puzzle.
- Find other developers who are working on similar problems and projects.

# TDD

“Test-driven development” refers to a style of programming in which three activities are tightly interwoven: coding, testing and design.

### It can be succinctly described by the following set of rules:

- write a “single” unit test describing an aspect of the program.
- run the test, which should fail because the program lacks that feature.
- write “just enough” code, the simplest possible, to make the test pass.
- “refactor” the code until it conforms to the simplicity criteria.
- repeat, “accumulating” unit tests over time.

# CI/CD

### CI : Continuous Integration

Is a workflow strategy that helps ensure everyone's changes will integrate with the current version of the project. This lets you :

- catch bugs.
- reduce merge conflicts.
- Give you confidence about your software is working.

### CD :

- Continuous Delivery :

  - develop to release at any time.

- Continuous Deployment :
  - deploy new features immediately.

# Bookmark and Review :

- [nodeJS docs](https://nodejs.org/en/docs/)
- [npm docs](https://docs.npmjs.com/)
- [express docs](https://expressjs.com/en/4x/api.html)
- [http status codes](https://www.restapitutorial.com/httpstatuscodes.html)
- [supertest](https://github.com/visionmedia/supertest)

# References :

- [An introduction to NodeJS and Express](https://developer.mozilla.org/en-US/docs/Learn/Server-side/Express_Nodejs/Introduction)
- [NPM](https://docs.npmjs.com/about-npm)
- [TDD](<https://www.agilealliance.org/glossary/tdd/#q=~(infinite~false~filters~(postType~(~'page~'post~'aa_book~'aa_event_session~'aa_experience_report~'aa_glossary~'aa_research_paper~'aa_video)~tags~(~'tdd))~searchTerm~'~sort~false~sortDirection~'asc~page~1)>)
- [CI/CD](https://www.youtube.com/watch?v=xSv_m3KhUO8&ab_channel=GitHubTraining%26Guides)
