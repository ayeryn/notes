# HTML5

HyperText Markup Language.

## Links

- [web.dev HTML](https://web.dev/learn/html/overview)

## Document Structure

```html
<html lang="en-us">
  <head>
    <meta charset="utf-8" />
    <title>My Page</title>
    <meta name="viewport" content="width=device-width" />
  </head>
  <body>
    <header></header>
    <footer></footer>
  </body>
</html>
```

- `<!DOCTYPE` html>: the preamble
  - doctype, tells the browser to use standards mode
- `<html>`: the root element
  - `<head>`: the document metadata header, contains all the metadata for a site or application
  - `<body>`: contains the visible content

## `<head>`

### Mandatory

Always include **character set, title, and viewport settings**.

- Character encoding: the **first** element to ensure the page loads properly
- Document title
- Viewport metadata

### Other content

#### CSS

There are three ways to include CSS:

1. `<link>`: use an external source with `rel="stylesheet"` 🌟

   - `style.css` is the URL of the stylesheet
   - `type="text/css"` is not necessary

   ```html
   <link rel="stylesheet" href="style.css" />
   ```

2. `<style>`: direct CSS
   - `@import`: if you want the external stylesheet styles to be within a cascade layer but you don't have access to edit the CSS file to put the layer information in it.
3. the `style` attribute

#### Scripts

The default type is JavaScript.

## Metadata

### Pragma directives

The `http-equiv` attribute has as its value a pragma directive. These directives describe how the page should be parsed. Supported `http-equiv` values enable setting directives when you are unable to set HTTP headers directly.

```html
<meta http-equiv="refresh" content="60; https://mypage.com/regTimeout" />
```

### Open Graph

Can be used to control how social media sites, like Twitter and Facebook, display links to your content. OG meta tags are used to create social media cards for your pages.

## Semantic HTML

_Semantic_ means "relating to meaning".

### Accessibility object model (AOM)

As the browser parses the content received, it builds the document object model (DOM) and the CSS object model (CSSOM). It then also builds an accessibility tree.

The DOM is a tree of all the nodes in the document. The AOM is like a semantic version of the DOM.

#### The `role` attribute

It describes the role an element has in the context of the document.

### Semantic elements

HTML should be used to **structure content**, not to define content's appearance. The appearance is the realm of CSS.

## `<body>`

A layout with a header, two sidebars, and a footer, is known as the holy grail layout.

```html
<body>
  <header>My Blog</header>
  <nav>Nav</nav>
  <main>
    <h1>Posts</h1>
    <article>Article 1</article>
    <article>Article 2</article>
  </main>
  <aisde>Aside</aside>
  <footer>Footer</footer>
</body>
```

### `<main>`

This contains the main content of the document. There should be only one `<main>` per page.

### `<aside>`

This is for content that is indirectly or tangentially related to the document's main content.

### `<article>`

An `<article>` represents a complete, or self-contained, section of content that is, in principle, independently reusable.

### `<section>`

This is used to encompass generic standalone sections of a document when there is no more specific semantic element to use.

```html
<header>
  <h1>Machine Learning Workshop</h1>
  <nav>
    <a href="#reg">Register</a>
    <a href="#about">About</a>
    <a href="#teachers">Instructors</a>
    <a href="#feedback">Testimonials</a>
  </nav>
</header>
...
<footer>
  <p>&copy;2022 Machine Learning Workshop, LLC. All rights reserved.</p>
  <address>
    Instructors: <a href="/hal.html">Hal</a> and <a href="/eve.html">Eve</a>
  </address>
</footer>
```

![structure](https://web.dev/static/learn/html/headings-and-sections/image/a-layout-a-header-three-31026f6b6c4b4_856.png)
