# React/Javascipt Notes

## React

- What is React?
- React is a popular open-source Javascript **library** used for building UIs or front-end applications

- Key: reusable components
- Components:
- Properties (Props)

### State

Always lift the state up to the parent component.  
The parent component can pass that state back to the children via **props**. This keeps the child components in sync with each other and with their parent. _All children re-render automatically when parent changes._

### `useState`

A function that allows you to add state to functional components. It requires the initial value of the state and returns an array with two elements:

1. current state value
2. a function that allows you to update the state

### Re-rendering a list

`Warning: Each child in a list should have a unique "key" prop.`

When a list is re-rendered, React takes each list item's ley and searches the previous list's items for a matching key.

- If the current list has a key that didn't exist before, React creates a component.
- If the current list is missing a key that existed in the previous list, React destroys the previous component.
- If two keys match, the corresponding component is moved.

Keys tell React about the identity of each component, which allows React to maintain state between re-renders.

- If a component's key changes, the component will be destroyed and re-created with a new state.

When a element is created, React extracts the `key` property and sotres the key directly on the returned element. There's no way for a component to ask what `key` its parent specified.

## JS
