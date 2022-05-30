# Redux - Combined Reducers

## Combined Reducers

- Why we use Combined Reducers?

- When the application grows **bigger**, the number of states that we want to maintain the user experience and the whole workflow of the application also increases.
- Therefore, we tend to **create multiple reducers** for each state instead of making one giant reducer that holds all the information and the functions we want to execute.

- `combineReducers` is simply a utility function to simplify the most common use case when writing Redux reducers.

- Redux solved this problem by introducing the `combineReducer({reducer_1,reducer_2,...})` function.
- This function takes multiple reducers as an object argument and return one single reducer that manages all the dispatch actions from it.

```js
// reducers.js
export default theDefaultReducer = (state = 0, action) => state;

export const firstNamedReducer = (state = 1, action) => state;

export const secondNamedReducer = (state = 2, action) => state;

// rootReducer.js
import { combineReducers, createStore } from 'redux';

import theDefaultReducer, {
  firstNamedReducer,
  secondNamedReducer,
} from './reducers';

// Use ES6 object literal shorthand syntax to define the object shape
const rootReducer = combineReducers({
  theDefaultReducer,
  firstNamedReducer,
  secondNamedReducer,
});

const store = createStore(rootReducer);
```

- What happens when we dispatch an action is that combineReducer invokes all the reducers at once giving each reducer a chance to respond to the action being dispatched. This behavior is somehow not so efficient but it gets the job done, and it will retain the consistency of the whole application work flow.

## combineReducers(reducers)

- As your app grows more complex, you'll want to split your reducing function into separate functions, each managing independent parts of the state.
- The combineReducers helper function turns an object whose values are different reducing functions into a single reducing function you can pass to createStore.

- The resulting reducer calls every child reducer, and gathers their results into a single state object. The state produced by combineReducers() namespaces the states of each reducer under their keys as passed to combineReducers()

`Arguments`

- reducers (Object): An object whose values correspond to different reducing functions that need to be combined into one. See the notes below for some rules every passed reducer must follow.

`Returns`

- (Function): A reducer that invokes every reducer inside the reducers object, and constructs a state object with the same shape.

## Bookmarks

- [Multiple Reducers Example](https://www.youtube.com/watch?v=gBER4Or86hE)
- [Redux Docs: Using Combined Reducers](https://redux.js.org/usage/structuring-reducers/using-combinereducers/)
- [Redux Docs: Combined Reducer Syntax](https://redux.js.org/api/combinereducers/)
