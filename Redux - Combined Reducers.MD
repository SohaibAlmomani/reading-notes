# Redux - Combined Reducers

The most common state shape for a Redux app is a plain Javascript object containing "slices" of domain-specific data at each top-level key. Similarly, the most common approach to writing reducer logic for that state shape is to have "slice reducer" functions, each with the same `(state, action)` signature, and each responsible for managing all updates to that specific slice of state. Multiple slice reducers can respond to the same action, independently update their own slice as needed, and the updated slices are combined into the new state object.

### There are several important ideas to be aware of when using combineReducers:

- First and foremost, `combineReducers` is simply a utility function to simplify the most common use case when writing Redux reducers.

- While Redux itself is not opinionated about how your state is organized, combineReducers enforces several rules to help users avoid common errors.

- One frequently asked question is whether Redux "calls all reducers" when dispatching an action. Since there really is only one root reducer function, the default answer is "no, it does not". However, `combineReducers` has specific behavior that does work that way.

- You can use it at all levels of your reducer structure, not just to create the root reducer. It's very common to have multiple combined reducers in various places, which are composed together to create the root reducer.

## Defining State Shape

`combineReducers` takes an object full of slice reducer functions, and creates a function that outputs a corresponding state object with the same keys. This means that if no preloaded state is provided to `createStore`, the naming of the keys in the input slice reducer object will define the naming of the keys in the output state object. The correlation between these names is not always apparent, especially when using ES6 features such as default module exports and object literal shorthands.

## combineReducers(reducers)

As your app grows more complex, you'll want to split your reducing function into separate functions, each managing independent parts of the state.

The `combineReducers` helper function turns an object whose values are different reducing functions into a single reducing function you can pass to `createStore`.

he resulting reducer calls every child reducer, and gathers their results into a single state object. **The state produced by `combineReducers()` namespaces the states of each reducer under their keys as passed to `combineReducers()`**

**Returns**

(Function): A reducer that invokes every reducer inside the reducers object, and constructs a state object with the same shape.

Any reducer passed to `combineReducers` must satisfy these rules:

- For any action that is not recognized, it must `return` the `state` given to it as the first argument.

- It must never return `undefined`. It is too easy to do this by mistake via an early return statement, so `combineReducers` throws if you do that instead of letting the error manifest itself somewhere else.

- If the `state` given to it is `undefined`, it must return the initial state for this specific reducer. According to the previous rule, the initial state must not be `undefined` either. It is handy to specify it with ES6 optional arguments syntax, but you can also explicitly check the first argument for being `undefined`.

# References

## [Multiple Reducers Example](https://www.youtube.com/watch?v=gBER4Or86hE)

## [Redux Docs: Using Combined Reducers](https://redux.js.org/usage/structuring-reducers/using-combinereducers/)

## [Redux Docs: Combined Reducer Syntax](https://redux.js.org/api/combinereducers/)
