# React

React is a popular open-source Javascript **library** used for building UIs or front-end applications

- Key: reusable components
- Components
- Properties (Props)

## Props

Information that gets passed from one component to another is known as **prop**.

## Hooks

React Hooks, are functions that let us _manage the internal state of components and handle post-rendering side effects_ directly from our function components.

Using Hooks, we can determine what we want to show the users by declaring how our user interface should look based on the state.

### State

Always lift the state up to the parent component.  
The parent component can pass that state back to the children via **props**. This keeps the child components in sync with each other and with their parent. _All children re-render automatically when parent changes._

#### `useState`

A function that allows you to add state to functional components. It requires the initial value of the state and returns an array with two elements:

1. current state value
2. a function that allows you to update the state

```js
import React, { useState } from "react";

export default function Counter() {
  const [count, setCount] = useState(0);

  const handleClick = () => {
    setCount((count) => count + 1);
  };
}
```

#### Re-rendering a list

🚨 Each child in a list should have a unique "key" prop.

When a list is re-rendered, React takes each list item's ley and searches the previous list's items for a matching key.

- If the current list has a key that didn't exist before, React creates a component.
- If the current list is missing a key that existed in the previous list, React destroys the previous component.
- If two keys match, the corresponding component is moved.

Keys tell React about the identity of each component, which allows React to maintain state between re-renders.

- If a component's key changes, the component will be destroyed and re-created with a new state.

When a element is created, React extracts the `key` property and sotres the key directly on the returned element. There's no way for a component to ask what `key` its parent specified.

### Effect

This tells the page what to do when it re-renders. This can also contain cleanup actions.

#### Cleaning up

We don't want to incorrectly or accidentally accumulate hooks on the page every time it re-renders. Is this like garbage collection or deconstructions in java and cpp?

```js
useEffect(() => {
  const handleClick = () => console.log("Click!");
  window.addEventListener("click", handleClick);

  return () => {
    window.removeEventListener("click", handleClick);
  };
}, []);
```

❗ The `return` statement does **NOT** run the cleanup function right away. It's simply returning the function to be used _when the component unmounts or the effect re-runs_.

## Separation of components

### Presentational/stateless

- The presentational components' only job is to contain JSX
- It should be exported
- It should not render itself, because it will always get rendered by the container component
- Stateless can still be reactive

Container component passes information down to presentational components using `props`.

In order for a presentation component to communicate changes to a container component, the container component must define and provide a way for the presentational component to communicate with it using a change handler function passed as a prop.
