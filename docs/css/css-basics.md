# CSS Basics

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
