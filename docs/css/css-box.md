# Box and Layout

Everything in CSS has a box around it.

Depending on how the box behaves in terms of _page flow and in relation to other boxes on the page_.

Boxes have:

- an **inner display type**: how elements inside the box are laid out
- an **outer display type**: how the box is laid out in relation to other boxes around it
  - `block` v. `inline`

<!-- TODO: make a table for the outer type comparison -->

## Block boxes

- The box will break onto a new line
- The `width` and `height` properties are respected
- Padding, margin and border will cause other elements to be pushed away from the box
- If `width` is not specified, the box will extend in the inline direction to fill the space available in its container
- In most cases, the box will become as wide as its container, filling up 100% of the space available

Some elements, such as `<h1>` and `<p>`, use `block` as their outer display type by default.

## Inline boxes

- The box will not break onto a new line
- The `width` and `height` properties will not apply
- Top and bottom padding, margins, and borders will apply but will not cause other inline boxes to move away from the box
- Left and right padding, margins, and borders will apply and will cause other inline boxes to move away from the box

Elements such as `<a>`, `<span>`, `<em>` and `<strong>` use `inline` as their outer display type by default.

## Setting the type

`display` sets both outer and inner at once.

```css
display: block; /* block outer, normal inner (flow) */
display: flex; /* block outer, flex inner */
display: inline-flex; /* inliner outer, flex inner */
display: grid; /* block outer, grid inner */
display: inline-grid; /* inline outer, grid inner */
```

<!-- FIXME: what's the rule? -->

It seems that unless `<>-<>` format is used, the `display` value is for the outer display.

## Standard Box Model

<img src='img/box-model.png' width='300' />

What is the actual dimension of `box`?

```css
.box {
  width: 350px;
  height: 150px;
  margin: 10px;
  padding: 25px;
  border: 5px solid black;
}
```

- `width` and `height ` define the dimension of the **content box**.
- The margin is not counted towards the actual size of the box - it only affects the space outside the box.
- Actual width: `350  + 25*2 + 5*2 =  410`
- Actual height: `150 + 25*2 + 5*2 = 210`
- **Summary**: `content_dimension + padding * 2 + border * 2`

## Alternative Box Model

To turn it on, set `box-sizing: border-box`.

Any width is the width of the visible box on the page. The content area width is `width - padding - border`.
