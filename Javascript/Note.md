# React/Javascipt Notes

## React
- What is React?
- React is a popular open-source Javascript __library__ used for building UIs or front-end applications

- Key: reusable components
- Components:
- Properties (Props)

### State
Always lift the state up to the parent component.      
The parent component can pass that state back to the children via __props__. This keeps the child components in sync with each other and with their parent. _All children re-render automatically when parent changes._

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
### Spread syntax (`...`)
- Allows an iterable to be expanded. 
- In an object literal, the spread syntax enumerates the properties of an object and adds the key-value pairs to the object being created.    

<span style="color:purple;">kinda like python scripting.  </span>

All indices are enumerable own properties, so arrays can be spread into objects.
```
const array = [1, 2, 3]
const obj = { ...array };
// { 0: 1, 1: 2, 2: 3}

```


### array `map` method
```
[1, 2, 3].map((x) => x * 2) //[2, 4, 6]
```


### `var` v. `let`
- `var`: used to declare a function-scoped variable.
    - accessible throughout the entire function.
- `let`: used to declare a block-scoped variable.
    - only accessible within the block scope in which it is defined

```
function example() {
  let x = 10;
  if (true) {
    let x = 20;
    console.log(x); // Output: 20
  }
  console.log(x); // Output: 10
}
```
