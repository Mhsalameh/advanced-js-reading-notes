# Component Lifecycle / `useEffect()` Hook

Now that we know what hooks are and we had an example with `useState()` hooks, we will be talking about the `useEffect()` Hooks and the lifecycle of components.

## `ueseEffect` hooks

**Side effects** (effects for short) are operations that affects other components and can't be done during rendering such as:

- data fetching
- subscription
- manually changin DOM from react Components

for example:

```javascript
import React, { useState, useEffect } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    // Update the document title using the browser API
    document.title = `You clicked ${count} times`;
  });

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}
```

Calling the `useEffect()` is like telling React to run the effect function after flushing changes to DOM. Declaring effects inside components gives them access to their props and state, side note : react runs the effects after every render — including the first render by default.

There are two common kinds of side effects in React components: **those that don’t require cleanup**, **and those that do**.

## Effects Without Cleanup

Network requests, Manual DOM mutations, and loggins are an example of effects that do not require cleanup, they are considered additional code that runs after React has updated the DOM. So we can run them and immediately forget about them as an example :

```js
import React, { useState, useEffect } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `You clicked ${count} times`;
  });

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}
```

**What does useEffect do?** using this hook enabled us to tell React that this component needs to do something after render. React will then remember the function the we passed (this is our effect) and React will call it later after performing the DOM updates.

**What does useEffect do?** Placing it inside the component will let us use the count state or any props that the component has

**Does useEffect run after every render?** useEffect run both after and before the first render and after every update in the component that's by default, and this is customizable. In this case we can say react guarantees the DOM has been updated by the time it runs the effects.

the function passed to useEffect is going to be different on every render. This is intentional. In fact, this is what lets us read the count value from inside the effect without worrying about it getting stale. Every time we re-render, we schedule a different effect, replacing the previous one.

## Effects with Cleanup

Some effects requires cleanup i.e. We might want to set up a subscription to some external data source. In that case, it is important to clean up so that we don’t introduce a memory leak! Let’s compare how we can do it with classes and with Hooks.

You might be thinking that we’d need a separate effect to perform the cleanup. But code for adding and removing a subscription is so tightly related that useEffect is designed to keep it together. If your effect returns a function, React will run it when it is time to clean up:

```js
import React, { useState, useEffect } from 'react';

function FriendStatus(props) {
  const [isOnline, setIsOnline] = useState(null);

  useEffect(() => {
    function handleStatusChange(status) {
      setIsOnline(status.isOnline);
    }
    ChatAPI.subscribeToFriendStatus(props.friend.id, handleStatusChange);
    // Specify how to clean up after this effect:
    return function cleanup() {
      ChatAPI.unsubscribeFromFriendStatus(props.friend.id, handleStatusChange);
    };
  });

  if (isOnline === null) {
    return 'Loading...';
  }
  return isOnline ? 'Online' : 'Offline';
}
```

**Why did we return a function from our effect?** this is the optional cleanup mechanism for effects. Every effect may return a function that cleans up after it. This lets us keep the logic for adding and removing subscriptions close to each other. They’re part of the same effect.

**When exactly does React clean up an effect?** React performs the cleanup when the component unmounts. However, as we learned earlier, effects run for every render and not just once. This is why React also cleans up effects from the previous render before running the effects next time, this helps to avoid bugs.

## Bookmarks

- [effect hooks](https://reactjs.org/docs/hooks-effect.html)
- [recap on effect hooks and tips](https://reactjs.org/docs/hooks-effect.html#recap)
