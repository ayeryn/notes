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

The `id` attribute of an element can by used as the parameter for the `getElementById()` method and, with a `#` prefix, as part of a parameter for the `querySelector()` and `querySelectorAll()` methods.

```html title="index.html"
<img src="svg/switch.svg>" id="switch alt="light switch" class="light />
```

```js title="script.js"
const switchViaID = document.getElementById("switch");
const switchViaSelector = document.querySelector("#switch");
```

```js title="index.html"
<head>
  <script>
  const onoff = document.getElementById("switch");
  onoff.addEventListener('click',function(){
    document.body.classList.toggle('black');
  });
  </script>
</head>
```

#### `<label>`

`<label>` has a `for` attribute that takes as its value the `id` of the form control with which it is associated.

```html
<label for="name">Name: </label><input id="name" type="text" name="name" /> >
```

The association between for and id makes the information available to users of assistive technologies. In addition, clicking anywhere on a label gives focus to the associated element, extending the control's click area.

### `tabindex`

This attribute can be added to any element to enable it to receive focus. The value defines whether it gets added to the tab order, and, optionally into a non-default tabbing order.

### `role`

The `role` attribute is part of the ARIA specification. It can be used to provide semantic meaning to content, enabling screen readers to inform site users of an object's expected user interaction.

It doesn't change browser behavior or alter keyboard or pointer device interactions-adding `role=button` to a `<spam>` does not turn it into a button.

### `contenteditable`

An element with the `contenteditable` attribute set to `true` is editable, is focusable, and is added ot the tab order as if `tabindex="0"` were set.

```html
<!-- These are equivalent>
<An enumerated attribute: inherit(d), true, false -->
 <style contenteditable>
 <style contenteditable="">
 <style contenteditable="true">
```

#### Toggle and set

```js
const editor = document.getElementById("myElement");
if (editor.contentEditable) {
  editor.setAttribute("contenteditable", "false");
} else {
  editor.setAttribute("contenteditable", "");
}
```

#### Fun stuff

Since `contenteditable` is a global attribute, it can be applied to even `<style>`.

```html
<style contenteditable>
  style {
    color: inherit;
    display: block;
    border: 1px solid;
    font: inherit;
    font-family: monospace;
    padding: 1em;
    border-radius: 1em;
    white-space: pre;
  }
</style>
```

1. Adding `<style contenteditable>` makes the `<style>` element's content **editable in the browser**.
2. The code inside `<style>` is CSS that targets `<style>` elements so that they all have the style defined there.
3. As a result, `<style>` renders on the final page unlike hidden per usual. We can also click into the element and change it. This also updates the style simultaneously.

## Custom Attributes

You can create any custom attribute you want by adding the `data-` prefix.

They are an excellent way of communicating application-specific information via JavaScript. Add custom attributes to elements in the form of `data-name` and access these through the DOM using `dataset[name]` on the element in question.

```js
el.dataset["hello"];
e.dataset.hello;

for (let key in el.dataset) {
  customObject[key] = el.dataset[key];
}
```
