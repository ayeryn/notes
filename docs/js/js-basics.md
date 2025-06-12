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
