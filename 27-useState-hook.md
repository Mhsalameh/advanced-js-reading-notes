# useState() Hook

There are many common cases that that couldn't be broken down into smaller components because the logic in it is stateful. Such as animations, form handling, connecting to external data sources , and many other things we want to do from components. But when we try to do that using components alone we face some issues including:

- **Huge components** that are hard to refactor and test.
- **Duplicated logic** between different components and lifecycle methods.
- **Complex patterns** like render props and higher-order components.

We think that using hooks will solve these problems, as it will let us organize the logic inside a component into reusable isolated units

## What Are hooks Exactly?

There are many ways to reuse code in react, like a simple function that can be called to calculate something, or a components which themselves can either be functions and classes. Components are powerful but they have to render some UI, so it's more convenient using them in only visual logic, this leaves us with more complex patterns like render props and higher-order components.

Functions seem to be a perfect mechanism for code reuse. Moving logic between functions takes the least amount of effort. However, functions can’t have local React state inside them. You can’t extract behavior like “watch window size and update the state” or “animate a value over time” from a class component without restructuring your code or introducing an abstraction like Observables. Both approaches hurt the simplicity that we like about React.

Hooks solve exactly that problem. Hooks let you use React features (like state) from a function — by doing a single function call. React provides a few built-in Hooks exposing the “building blocks” of React: state, lifecycle, and context.

A Hook is a special function that lets you “hook into” React features. For example, useState is a Hook that lets you add React state to function components.

If you write a function component and realize you need to add some state to it, previously you had to convert it to a class. Now you can use a Hook inside the existing function component.

## Hooks overview

This example renders a counter. When you click the button, it increments the value:

```js
import React, { useState } from 'react';

function Example() {
  // Declare a new state variable, which we'll call "count"
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}
```

Here, useState is a Hook (we’ll talk about what this means in a moment). We call it inside a function component to add some local state to it. React will preserve this state between re-renders. useState returns a pair: the current state value and a function that lets you update it. You can call this function from an event handler or somewhere else. It’s similar to this.setState in a class, except it doesn’t merge the old and new state together. (We’ll show an example comparing useState to this.state in Using the State Hook.)

The only argument to useState is the initial state. In the example above, it is 0 because our counter starts from zero. Note that unlike this.state, the state here doesn’t have to be an object — although it can be if you want. The initial state argument is only used during the first render.

You can use the State Hook more than once in a single component:

```js
function ExampleWithManyStates() {
  // Declare multiple state variables!
  const [age, setAge] = useState(42);
  const [fruit, setFruit] = useState('banana');
  const [todos, setTodos] = useState([{ text: 'Learn Hooks' }]);
  // ...
}
```

## Using useState Hooks

this is a function component:

```js
const Example = (props) => {
  // You can use Hooks here!
  return <div />;
};
```

- importing useState:

  first we import the useState hook from react

  ```js
  import { useState } from 'react';
  ```

- calling useState:

  It declares a “state variable”. Our variable is called count but we could call it anything else, like banana. This is a way to “preserve” some values between the function calls — useState is a new way to use the exact same capabilities that this.state provides in a class. Normally, variables “disappear” when the function exits but state variables are preserved by React.

  ```js
  import React, { useState } from 'react';

     function Example() {
     // Declare a new state variable, which we'll call "count"
     const [count, setCount] = useState(0);
  ```

- passing arguments to useState:

  The only argument to the useState() Hook is the initial state. Unlike with classes, the state doesn’t have to be an object. We can keep a number or a string if that’s all we need. In our example, we just want a number for how many times the user clicked, so pass 0 as initial state for our variable. (If we wanted to store two different values in state, we would call useState() twice.)

- useState returns:

  It returns a pair of values: the current state and a function that updates it. This is why we write const `[count, setCount] = useState();`.

## bookmarks and references

- [overview](https://reactjs.org/docs/hooks-overview.html)
- [usestate](https://reactjs.org/docs/hooks-state.html)
- [what are hooks?](https://reactjs.org/docs/hooks-state.html)
- [hooks api references](https://reactjs.org/docs/hooks-reference.html)
