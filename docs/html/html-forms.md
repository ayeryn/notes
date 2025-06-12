# Nav, Tables, and Forms

## Navigation

## Tables

If data is being presented, compared, sorted, calculated, or cross-referenced, then `<table>` is probably the right choice.

If you simply want to lay out non-tabular content neatly, such as a large group of thumbnail images, tables are NOT appropriate; create a _list of images and style the grid with CSS_.

### `<table>`

If the table maintains a selection state, has two-dimensional navigation, or allows the user to rearrange cell order, set `role=""grid`.

If the rows of the `grid` can be expanded and collapsed, use `role="treegrid`.

<!-- TODO: sandbox -->

### `<caption>`

`<caption>` is a native and semantic element, and the preferred method of **giving a name to a table**.

## Forms

### `<input>`

- **Outside of form**: useful for search bars, filters, etc.
- **Inside of form**
  - Enter-to-submit
  - form validation
  - working with `<input type="submit">` to actually work

### `submit`

1. The browser gathers all input values
   - Fields with `name` attributes are collected
   - Data is serialized into a string

<!-- TODO: review -->
