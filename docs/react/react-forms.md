# React Forms

_What is the difference between HTML and React forms?_  
All changes to input values in a React form are sent to the server as soon as they happen as it uses event handlers.

## Controlled component

A controlled component doesn't maintain any internal state. If you ask information and it needs to get it via `props` then it's controlled.

Most React components are controlled.

## Uncontrolled component

An uncontrolled component maintains its own internal state.

```js
let input = document.querySelector('input[type="text"]');

let typedText = input.value; // input.value will be equal to whatever text is currently in the text box.
```

The fact that `<input>` keeps track of information makes it _uncontrolled_.

When you give an `<input>` element a `value` attribute, then the `<input>` element becomes controlled. It stops using its internal storage.
