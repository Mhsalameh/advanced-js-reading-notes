# Redux - Additional Topics

- Redux Toolkit

  - Purpose:
  - The Redux Toolkit package is intended to be the standard way to write Redux logic. It was originally created to help address three common concerns about Redux:

1. “Configuring a Redux store is too complicated”
2. “I have to add a lot of packages to get Redux to do anything useful”
   3.“Redux requires too much boilerplate code”

- Advantages

  1. Simple Includes utilities to simplify common use cases like store setup, creating reducers, immutable update logic, and more.

  2. Opinionated Provides good defaults for store setup out of the box, and includes the most commonly used Redux addons built-in.
  3. Powerful Takes inspiration from libraries like Immer and Autodux to let you write “mutative” immutable update logic, and even create entire “slices” of state automatically.

  4. Effective Lets you focus on the core logic your app needs, so you can do more work with less code.

- Redux Toolkit includes:
  - !. configureStore() function with simplified configuration options. It can automatically combine your slice reducers, adds whatever Redux middleware you supply, includes redux-thunk by default, and enables use of the Redux DevTools Extension.

1. reateReducer() utility that lets you supply a lookup table of action types to case reducer functions, rather than writing switch statements.

2. createAction() utility that returns an action creator function for the given action type string. The function itself has toString() defined, so that it can be used in place of the type constant.

3. createSlice() function that accepts a set of reducer functions, a slice name, and an initial state value, and automatically generates a slice reducer with corresponding action creators and action types.

4. createSelector utility from the Reselect library, re-exported for ease of use.

---

- The core idea

  - State is the heart of each application and there is no quicker way to create buggy, unmanageable applications than by producing an inconsistent state or state that is out-of-sync with local variables that linger around. Hence many state management solutions try to restrict the ways in which you can modify state, for example by making state immutable. But this introduces new problems; data needs to be normalized, referential integrity can no longer be guaranteed and it becomes next to impossible to use powerful concepts like classes in case you fancy those.

    - The Redux Toolkit provides a set of utilities that help you write Redux logic in a way that is easy to understand and maintain.

## bookmarks

- [Redux Toolkit (RTK)](https://redux-toolkit.js.org/)
- [Tutorial](https://redux-toolkit.js.org/tutorials/overview)

- [MobX](https://mobx.js.org/getting-started.html)
- [HookState](https://hookstate.js.org/)
