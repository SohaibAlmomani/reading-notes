# Context API - Behaviors

## Snackbars:

```js
const { addAlert } = useSnackBars()
...
addAlert('Your profile is updated!')
```

## Globally Accessible


The state of our snackbars (which ones are visible) can be localized to a single centralized component. That same centralized component can be responsible for rendering them. There’s really no need for another component somewhere in the tree to hook into that state (at least not in our use-case).

However, the management of that state (adding, removing) needs to be globally accessible

```js
export const SnackBarContext = createContext()

export function SnackBarProvider({ children }) {
  const [alerts, setAlerts] = useState([])

  return (
    <SnackBarContext.Provider value={{ setAlerts }}>
      {children}
      {alerts.map((alert) => <SnackBar key={alert}>{alert}</SnackBar>)}
    </SnackBarContext.Provider>
  )
}
```
The other half of the puzzle is we now need a consumer for this provider. It turns out that our custom hook from before is nothing more than a small wrapper around the useContext internal React hook, which consumes our new context.

## Room for Change

There’s a lot of buzz around how you can replace a lot of what Redux does with `useContext` and `useReducer`. The combination of these two hooks means we can have a global state and use Redux-like reducers, actions, and dispatchers to mutate that global state. To an extent, it’s possible.

# References

## [Hooks and Context example](https://reactjs.org/docs/context.html)

## [Awesome React Context links](https://github.com/diegohaz/awesome-react-context)
