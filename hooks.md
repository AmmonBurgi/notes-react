# Hooks

Hooks were introduced in React 16.8 and they let us use React's features like managing your component's state and/or performing an after effect when certain changes occur in state(s) without writing a class.

## State Hooks
- useState - declares a state variable that you can update directly
``` const [index, setIndex] = useState(0) ```

- useReducer - declares a state variable with the update logic inside a reducer function
``` const [state, dispatch] = useReducer(reducer, initialArg, init?) ```

## Context Hooks
Context lets a component receive information from distant parents without passing it as props. For example, your app's top-level component can pass the current UI theme to all components below, no matter how deep.
- useContext - reads and subscribes to a context
``` const theme = useContext(ThemeContext) ```

## Ref Hooks
Refs let a component hold some information that isn't used for rendering, like a DOM node or a timeout ID. Unlike with state, updating a ref does not re-render your component.
- useRef - declares a ref. You can hold any value in it, but most often it's used to hold a DOM node.
``` const inputRef = useRef(null); ```

- useImperativeHandle - lets you customize the ref exposed by your component. This is rarely used.

## Effect hooks
Effects let a component connect to and synchronize with external systems. This includes dealing with network, browser DOM, animations, widgets written using a different UI library, and other non-React code.
- useEffect - connects a component to an external system.
```
useEffect(() => {
  const connection = createConnection(roomId);
  connection.connect()
  return () => connection.disconnect();
}, [roomId]);
```

Effects are an escape hatch from the React paradigm. Don't use Effects to orchestrate the data flow of your application. If you're not interacting with an external system, you might not need an Effect.

There are two rarely used variations of useEffect with differences in timing.
- useLayoutEffect - fires before the browser repaints the screen. You can measure layout here.
- useInsertionEffect - fires before React makes changes to the DOM. Libraries can insert dynamic CSS here.

## Performance Hooks

A common way to optimize re-rendering performance is to skip unnecessary work. For example, you can tell React to reuse a cached calculation or to skip a re-render if the data had not changed since the previous render.

To skip calculations and unnecessary re-rendering, use one of these Hooks:
- useMemo - lets you cache the result of an expensive calculation
``` const visibleTodos = useMemo(() => filterTodos(todos, tab), [todos, tab]) ```

- useCallback - lets you cache a function definition before passing it down to an optimized component

