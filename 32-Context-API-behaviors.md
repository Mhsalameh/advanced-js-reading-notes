# Context API - Behaviors

Context provides a way to pass data through the component tree without having to pass props down manually at every level.

## When to use a context

Context is designed to share data that can be considered “global” for a tree of React components, such as the current authenticated user, theme, or preferred language.

Using context, we can avoid passing props through intermediate elements

There’s a lot of buzz around how you can replace a lot of what Redux does with useContext and useReducer. The combination of these two hooks means we can have a global state and use Redux-like reducers, actions, and dispatchers to mutate that global state. To an extent, it’s possible.

## Before You Use Context

Context is primarily used when some data needs to be accessible by many components at different nesting levels. Apply it sparingly because it makes component reuse more difficult.

If you only want to avoid passing some props through many levels, component composition is often a simpler solution than context.

## API

### `React.createContext`

```jsx
const MyContext = React.createContext(defaultValue);
```

Creates a Context object. When React renders a component that subscribes to this Context object it will read the current context value from the closest matching Provider above it in the tree.

### `Context.Provider`

```jsx
<MyContext.Provider value={/* some value */}>
```

The Provider component accepts a value prop to be passed to consuming components that are descendants of this Provider. One Provider can be connected to many consumers. Providers can be nested to override values deeper within the tree.

All consumers that are descendants of a Provider will re-render whenever the Provider’s value prop changes. The propagation from Provider to its descendant consumers (including .contextType and useContext) is not subject to the shouldComponentUpdate method, so the consumer is updated even when an ancestor component skips an update.

## Bookmarks

[context API](https://reactjs.org/docs/context.html)
[hooks and context example](https://medium.com/swlh/snackbars-in-react-an-exercise-in-hooks-and-context-299b43fd2a2b)
[react context links](https://github.com/diegohaz/awesome-react-context)
