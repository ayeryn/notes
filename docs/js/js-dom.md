# JS and DOM (Document Object Model)

## Styling elements

The syntax follows `element.style.property`

## Events

Events are either **user interactions** or **browser manipulations**.

## Loops

```js
items.forEach(function (item) {
  console.log("This function will be applied to each item");
});
```

## `Handlebars.js`

### Setup

#### HTML

1. Include `<script type="text/x-handlebars-template">` block that includes template string
2. A target element to receive the final-rendered text

#### JavaScript

1. Grab the template string using `document` selector
2. Convert template into a render function
3. Create data-object with mapping
4. Find target element and update its content

#### Code

```html title="index.html"
<head id="greet" type="text/x-handlebars-template">
  <!-- prettier-ignore -->
  <script>{{ greeting }}</script>
</head>
<body>
  <div id="hello"><!-- Insert code here --></div>
  <script src="public/main.js" type="text/javascript"></script>
</body>
```

```js title="script.js"
// Gets the template string - "<s>{{}}</s>"
const source = document.getElementById("greet").innerHTML;

// Run the template into a render function
const template = Handlebars.compile(source);

// The key-value data object
const context = {
  greeting: "Hello World!",
};

// Apply render function to mapping
const compiledHtml = template(context);

// Finds the target element and set the text
const fill = document.getElementById("hello");
fill.innerHTML = compiledHtml;
```
