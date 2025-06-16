# JavaScript Basics

## The Trinity

- HTML is the content
- CSS is the look and feel
- JS is the "brain" BTS

The purpose of JS is to **modify HTML and CSS** via the DOM (Document Object Model). P.S.: DOM is an API.

### Runtimes

1. In the browser
2. In NodeJS

### Server-side vs. client-side

**Client-side code** is run on the user's computer.
**Server-side code** is run on the server, then its results are downloaded and displayed in the browser.

### Including JS

#### Internal JS

Since JS wants to manipulate the HTML and CSS, it has to wait for the whole page to finish loading before performing actions. Therefore, `<script>` be the last element in `<body>`.

#### External JS

A reference has to be made.

```html
<head>
  <script type="module" src="script.js"></script>
</head>
```

## Functions

### Arrow functions

#### `function(){}` vs. `const func = ()=>{}`

```js
function func() {} // Function declaration
const func = () => {}; // Arrow function expression
```

1. `this` binding

   - `function` gets its own `this` (dynamic binding).
   - Arrow function does NOT. It closes over the `this` from _where it was defined_.

   ```js
   const obj = {
     val: 42,
     regular: function () {
       return this.val;
     },
     arrow: () => {
       this.val;
     },
   };

   console.log(obj.regular()); // 42
   console.log(obj.arrow());
   // undefined cuz this is from outside obj
   ```

2. `arguments` object
   - Regular functions have access to the special `arguments` object
3. Can be hoisted
   - Regular function is hoisted - you can call it before it's defined.
4. As constructors

- `function` can be used with `new` to create objects.

  ```js
  function Person(name) {
    this.name = name;
  }
  const p = new Person("Eryn"); // works

  const Human = (name) => (this.name = name);
  // const h = new Human("Eryn");
  // TypeError: Human is not a constructor
  ```

#### Why are arrow functions preferred in web-dev?

## Arrays

### Spread syntax (`...`)

- Allows an iterable to be expanded.
- In an object literal, the spread syntax enumerates the properties of an object and adds the key-value pairs to the object being created.

<span style="color:purple;">kinda like python scripting. </span>

All indices are enumerable own properties, so arrays can be spread into objects.

```js
const array = [1, 2, 3];
const obj = { ...array };
// { 0: 1, 1: 2, 2: 3}
```

### array `map` method

```js
[1, 2, 3].map((x) => x * 2); //[2, 4, 6]
```

### `var` v. `let`

- `var`: used to declare a function-scoped variable.
  - accessible throughout the entire function.
- `let`: used to declare a block-scoped variable.
  - only accessible within the block scope in which it is defined

```js
function example() {
  let x = 10;
  if (true) {
    let x = 20;
    console.log(x); // Output: 20
  }
  console.log(x); // Output: 10
}
```
