# Text, Links, and Lists

## Headings

By default, browsers style `<h1>` the largest, `<h2>` slightly smaller, with each subsequent heading level being smaller by default.

Browsers by default also decrement the `<h1>` font size based on how many `<article>`, `<aside>`, `<nav>`, or `<section>` elements it is nested in.

<img src="https://web.dev/static/learn/html/text-basics/image/nested-h1-examples-cc207f75ad01d_1920.png" width="250" />

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

## Quotes and citations

1. `<blockquote>`
2. `<q>`
3. `<cite>`

<!-- FIXME: image not loading on GHP -->
<img src='img/quotes.png' width='400' />

```html
<h1>Quotes and Citations</h1>
<ul>
  <li>blockquote</li>
  <li>
    <blockquote>
      “She is a friend of my mind. She gather me, man. The pieces I am, she
      gather them and give them back to me in all the right order. It's good,
      you know, when you got a woman who is a friend of your mind.”
    </blockquote>
  </li>
  <li>cite</li>
  <li><cite>To be or not to be, that is the question.</cite></li>
  <li>q</li>
  <li><q>This is a quote.</q></li>
</ul>
```

### HTML Entities

- `&copy;`: ©
- `&trade;`: (™)

## Hyperlinks

Links can be created by `<a>`, `<area>`, `<form>`, and `<link>`.

### The `href` attribute

It's used to create hyperlinks to:

1. locations within the current page
2. other pages within a site
3. other sites;
4. it can also be coded to download files or send emails.

```html
<a href="http://mypage.com">My Page</a>
<a href="#about">About Me</a>
<a href="#top">Go to top.</a>
<a href="http://mypage.com#about">About Me</a>
<a href="mailto:help@mypage.com">Email me</a>
<a href="tel:1234567889">Call me</a>
```

#### Types of URLs

- **Absolute URLs** include a protocol (`http://`) and a domain name.
- **Relative URLs** do not include a protocol or a domain name.
  - relative to the current file

#### Downloadable resources

The `download` attribute should be included when the `href` points to a downloadable resource.

#### Browsing context

- `target`
  - `_self`
  - `_blank`
  - `_parent`
  - `top`
- `nofollow`

## Links and JS

```js
let a = document.links[0]; //obtain the first link in the document

a.href = "newpage.html"; //change the destination URL of the link
a.protocol = "ftp"; //change just the scheme part of the URL
a.setAttribute("href", "http://google.com/"); // change the attribute content directly
```

## Lists

- [Lists](https://web.dev/learn/html/lists)

<!-- TODO: come back and review if time permits -->
