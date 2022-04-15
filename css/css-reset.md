# css-reset

## refs

- <https://www.joshwcomeau.com/css/custom-css-reset/>

## contents

```css
/*
  1. Use a more-intuitive box-sizing model.
  注：达成的效果 box-sizing = content-width + padding + border;
*/
*, *::before, *::after {
  box-sizing: border-box;
}
/*
  2. Remove default margin
*/
* {
  margin: 0;
}
/*
  3. Allow percentage-based heights in the application
  In Flow layout, the width of an element is calculated based on its parent, but the height of an element is calculated based on its children.(流式布局元素宽度基于父元素，高度反之)
*/
html, body {
  height: 100%;
}
/*
  Typographic tweaks!
  4. Add accessible line-height
  5. Improve text rendering
*/
body {
  line-height: 1.5;
  -webkit-font-smoothing: antialiased;
}
/*
  6. Improve media defaults
*/
img, picture, video, canvas, svg {
  display: block;
  max-width: 100%;
}
/*
  7. Remove built-in form typography styles
  by default, buttons and inputs don't inherit typographical styles from their parents
*/
input, button, textarea, select {
  font: inherit;
}
/*
  8. Avoid text overflows
*/
p, h1, h2, h3, h4, h5, h6 {
  overflow-wrap: break-word;
}
/*
  9. Create a root stacking context
*/
#root, #__next {
  isolation: isolate;
}
```
