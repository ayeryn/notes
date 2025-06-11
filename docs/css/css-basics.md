# CSS Styling

Cascading Style Sheets.

## Styling

### External stylesheets

Within `<head>`, link to a separate CSS file.

```html
<head>
  <link rel="stylesheet" href="style.css" />
  ...
</head>
```

### Internal stylesheets

Within `<head>`, contained within `<style>`.

```html
<head>
  <style>
    h1 {
      color: red;
    }
  </style>
</head>
```

### Inline styling

Adding the `style` attribute directly onto an element. **Avoid if possible**.

## Selectors

<!-- TODO: finish review -->

1. Element selector (type selector): directly matches an HTML element name

   1. Multiple selectors can be targeted at once:

   ```css
   p,
   li {
     color: green;
   }
   ```

## Handling Conflicts

### Order of overriding declarations ❗

1. Declarations in user agent style sheets (e.g., the browser's default styles, used when no other styling is set).
2. Normal declarations in user style sheets (custom styles set by a user)
3. Normal declarations in author style sheets (these are the styles set by us, the web developers)
4. Import declarations in author style sheets
5. Import declarations in user style sheets
6. Import declarations in user agent style sheets

### Cascade

There are three factors to consider, listed here in increasing order of importance. Later ones overrule earlier ones:

1. Source order
2. Specificity
3. Importance

### Specificity

- Element selectors, pseudo-element selectors
- Class selectors, attribute selectors, pseudo-classes

### Inheritance

Some property values are inherit and some are not.

- `inherit`
- `initial`
- `revert`
- `revert-layer`
- `unset`

## Transition

- `transition` is shorthand for:

  - `transition-property`
  - `transition-duration`
  - `transition-timing-function`
  - `transition-delay`

- Always put it on the base class instead of modified class

```css
#box {
  background-color: lightskyblue;
  width: 50%;
  height: 50%;
  /* put here instead of on hover */
  transition: transform 1s ease-in 3s;
}

#box:hover {
  transform: translateX(100%);
}
```

### `transition-property`

`transition-property` is used to define what properties to apply a transition
effect to.

- `all` - (_Default_) all properties will get a transition effect
- `none` - no property will get a transition effect
- `<property>` - defines a comma separated list of CSS property names
- `initial` - sets this property to its default value
- `inherit` - inherits the property from its parent element

```css
div {
  transition-property: width, height;
}

div:hover {
  width: 300px;
  height: 400px;
}
```

### `transition-timing-function`

- `ease` - (_Default_) specifies a transition effect with a slow start, then
  fast, then end slowly
- `linear` - the same speed from start to end
- `ease-in` - slow start
- `ease-out` - slow end
- `ease-in-out` - start start and slow end
- `cubic-bezier(n, n, n, n)` - lets you define your own values in a cubic-bezier
  function.
  - **Tip**: You can inspect an element with transition and adjust visually\
    ![Alt text](image.png)

## Animation

- `animation` is short for:

  - `animation-name` (_required_)
  - `animation-duration` (_required_)
  - `animation-timing-function`
  - `animation-delay`
  - `animation-iteration-count`
  - `animation-direction`
  - `animation-fill-mode`
  - `animation-play-state`

- Write it in the place where you want it to happen, i.e., on the modified class

```css
#box {
  background-color: lightskyblue;
  width: 50%;
  height: 50%;
  transition: transform 1s ease-in 3s;
}

#box:hover {
  animation: left-to-right 1s ease-in;
}

@keyframes left-to-right {
  100% {
    transform: translateX(100%);
  }
}
```

- `@keyframes`: specifies the animation code. The animation is created by
  gradually changing from one set of CSS styles to another

```css
#box {
  background-color: lightskyblue;
  width: 50%;
  height: 50%;
  transition: transform 1s ease-in 3s;
}

#box:hover {
  animation: left-to-right 1s ease-in;
}

@keyframes left-to-right {
  /* default state */
  0% {
    transform: translateX(0);
  }

  33% {
    background-color: purple;
    transform: translateY(100%);
  }

  100% {
    transform: translateX(100%);
  }
}
```
