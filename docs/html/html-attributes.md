# HTML Attributes

Attributes provide information about and functionality for the element. Attributes define the behavior, linkages, and functionality of elements.

## Boolean attributes

If one (or more) of these attributes is present, the element is disabled, required, readonly, etc. If not present, it isn't.

Boolean values can either be omitted, set to an empty string, or be the name of the attribute. All values will resolve to true.

```html
<!-- They are equivalent -->
<input required />
<input required="" />
<input required="required" />
```

When toggling between true and false, add and remove the attribute altogether with JavaScript rather than toggling the value.

```js
const myMedia = document.getElementById("mediaFile");
myMedia.removeAttribute("muted");
myMedia.setAttribute("muted");
```

## Enumerated attributes

They have a limited set of predefined valid values.

## Global attributes

They are attributes that can be set on any HTML element, includign elements in the `<head>`. [Global attributes](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes#list_of_global_attributes)

### `<id>`

- The target of a link's fragment identifier
- Identifying an element for scripting
- Associating a form element with its label
- Providing a label or description for assistive technologies
- Targeting styles with (high specificity or as attribute selectors) in CSS.

#### Link fragment identifier

Links are not restricted to HTTP-based URLs; they can be **fragment identifiers** to sections of the page in the current document (or in other documents)

When a URL includes a hash mar (`#`) followed by a string of characters, that string is a fragment identifier. If that string matches an `id` of an element in the web page, the fragment is an anchor, or bookmark, to that element.

Setting `href="top`, case-insensitive, or simply `href=#`, will scroll the user to the top of the page.

`#` is not part of the fragment identifier. It's always the last part of the URL and is not sent to the server.

#### CSS selectors

Is CSS, you can target each section using an id selector, such as `#news` or, for less specificity, a case-sensitive attribute selector, `[id="news]`.

```html title="index.html"
<div id="news">News</div>
```

```css title="style.css"
#news {
  color: red;
}
```

#### Scripting

#### `<label>`

`<label>` has a `for` attribute that takes as its value the `id` of the form control with which it is associated.

```html
<label for="name">Name: </label><input id="name" type="text" name="name" /> >
```

The association between for and id makes the information available to users of assistive technologies. In addition, clicking anywhere on a label gives focus to the associated element, extending the control's click area.
