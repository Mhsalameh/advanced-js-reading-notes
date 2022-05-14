# Context API

1. Describe use cases useState() vs useReducer().

- `useReducer()` is useful when you need to use complex state logic, when you have multiple sub values, or when the next state depends on the previous state.

2. Why do custom hooks need the use prefix?

- It’s a convention, and without it react wouldn’t be able to automatically check for violations of rules of hooks.

3. What do custom hooks usually do?

- It's allow you to extract and share logic in a way that was not possible with class components.

4. Using any list of custom hooks, research and name one that you think will be useful in your applications.

- useWebSocket would be useful when building a game web app that needs to communicate with a websocket api.

5. Describe how a hook that fetches API data might work.

-An API fetching hook would take in a url and any info necessary for the request and return the results of the API call. It could use a callback to update the state with the returned results.

---

## Vocabulary Terms

- Reducer:
  - is a function that determines changes to an application's state. It uses the action it receives to determine this change.

---

## Preparation Materials

Context API

- **Context** provides a way to pass data through the component tree without having to pass props down manually at every level.

- Before You Use Context :Context is primarily used when some data needs to be accessible by many components at different nesting levels. Apply it sparingly because it makes component reuse more difficult.

- If you only want to avoid passing some props through many levels, component composition is often a simpler solution than context.

- Creates a Context object. When React renders a component that subscribes to this Context object it will read the current context value from the closest matching Provider above it in the tree.

- The defaultValue argument is only used when a component does not have a matching Provider above it in the tree. This can be helpful for testing components in isolation without wrapping them. Note: passing undefined as a Provider value does not cause consuming components to use defaultValue.

- Creates a Context object. When React renders a component that subscribes to this Context object it will read the current context value from the closest matching Provider above it in the tree.

- The defaultValue argument is only used when a component does not have a matching Provider above it in the tree. This can be helpful for testing components in isolation without wrapping them. Note: passing undefined as a Provider value does not cause consuming components to use defaultValue.

---

## bookmarks:

- [react context links](https://github.com/diegohaz/awesome-react-context)
- [context api](https://reactjs.org/docs/context.html)
- [hooks and context example](https://medium.com/swlh/snackbars-in-react-an-exercise-in-hooks-and-context-299b43fd2a2b)
