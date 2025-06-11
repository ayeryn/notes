# HTML Text Basics

## Headings

By default, browsers style `<h1>` the largest, `<h2>` slightly smaller, with each subsequent heading level being smaller by default.

Browsers by default also decrement the `<h1>` font size based on how many `<article>`, `<aside>`, `<nav>`, or `<section>` elements it is nested in.

<img src="https://web.dev/static/learn/html/text-basics/image/nested-h1-examples-cc207f75ad01d_1920.png" width="300" />

To style nested `<h1>` elements:

```css
/* 
- Any <h2> elements
- Any <h1> elements that are inside any <article>, <aside>, <nav>, or <section> */
h2,
:is(article, aside, nav, section) h1 {
}

/* 
- Any h3 element
- Any h1 that is inside a (article, aside, nav, section), which is itself inside a (article, aside, nav, section) */
h3,
:is(article, aside, nav, section) :is(article, aside, nav, section) h1 {
}
```

`:is()` is a CSS pseudo-class for grouping selectors, making them easier to write and more efficient.

`:is(a, b, c)` matches any element that matches selector a, b, or c.
