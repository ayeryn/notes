# Transitions and Animations

## Transitions

We can control the following four aspects of an element’s transition:

- `transition-property`: which CSS properties transition
- `transition-duration`: how long a transition lasts
- `transition-time-function`: how a transition accelerates
- `transition-delay`: how much time there is before a transition begins
- **shorthand**: `transition`

### Combining transitions

Transition of multiple properties can be combined into one `transition` property, each separated by a comma(,).

```css
transition: color 1s linear, font-size 750ms ease-in 100ms;

/* Apply to all changed properties */
transition: all 0.5s ease-out allow-discrete;
transition: 200ms linear 50ms;
```

## Responsive Design

Responsive design refers to the ability of a website to **resize and reorganize its content** based on:

- The size of other content on the website.
- The size of the screen the website is being viewed on.

### `em`

`em` is relative to the font size of this element, or the font size of the parent element when used for font-size. `rem` is relative to the font size of the root element.
