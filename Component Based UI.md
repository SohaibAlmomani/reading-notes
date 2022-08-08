# Component Based UI

## React hello world :

`React`: is a JavaScript library.

The smallest React example looks like this:

```js
const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(<h1>Hello, world!</h1>);
```

### building blocks of a React app :

- Elements.
- Components.

### What is the difference between an element and a React component?

| Element                                                                    | Component                                                                                                                           |
| -------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| An element is always gets returned by a component.                         | A component can be functional or a class that optionally takes input and returns an element.                                        |
| The element does not have any methods.                                     | Each component has its life cycle methods.                                                                                          |
| A React element is an object representation of a DOM node.                 | A component encapsulates a DOM tree.                                                                                                |
| Elements are immutable i,e once created cannot be changed.                 | The state in a component is mutable.                                                                                                |
| An element can be created using React.createElement( ) with type property. | A component can be declared in different ways like it can be an element class with render() method or can be defined as a function. |
| We cannot use React Hooks with elements as elements are immutable.         | React hooks can be used with only functional components                                                                             |
| Elements are light, stateless and hence it is faster.                      | It is comparatively slower than elements.                                                                                           |

### some advantages of React’s component based architecture?

- Reusability.
- Repetition.
- Scalability.
- Simpler maintenance.

## introducing JSX

### JSX :

It is a syntax extension to JavaScript. We recommend using it with React to describe what the UI should look like. JSX may remind you of a template language, but it comes with the full power of JavaScript.

React doesn’t require using JSX, but most people find it helpful as a visual aid when working with UI inside the JavaScript code. It also allows React to show more useful error and warning messages.

### Describe the process of embedding JavaScript expressions in JSX.

In the example below, we declare a variable called name and then use it inside JSX by wrapping it in curly braces:

```js
const name = "Josh Perez";
const element = <h1>Hello, {name}</h1>;
```

## Rendering Elements :

### Explain what a React Component

React Components Components are independent and reusable bits of code. They serve the same purpose as JavaScript functions, but work in isolation and return HTML.

Components come in two types, Class components and Function components, in this tutorial we will concentrate on Function components.

### Updating the Rendered Element

The only way to update the UI is to create a new element, and pass it to root.render(). Consider this ticking clock example:

```js
const root = ReactDOM.createRoot(document.getElementById("root"));

function tick() {
  const element = (
    <div>
      <h1>Hello, world!</h1>
      <h2>It is {new Date().toLocaleTimeString()}.</h2>
    </div>
  );
  root.render(element);
}
setInterval(tick, 1000);
```

React Only Updates What’s Necessary. React DOM compares the element and its children to the previous one, and only applies the DOM updates necessary to bring the DOM to the desired state.

# References :

- ## [React hello world](https://reactjs.org/docs/hello-world.html)

- ## [Intoduction to JSX](https://reactjs.org/docs/introducing-jsx.html)

- ## [Rendering Elements](https://reactjs.org/docs/rendering-elements.html)

- ## Cheatsheet :

  - ## [SASS Cheatsheet](https://devhints.io/sass)

  - ## [React Cheatsheet](https://devhints.io/react)

  - ## [Another React Cheatsheet](https://reactcheatsheet.com/)
