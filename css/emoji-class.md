# emoji class

## Content

- `<template class="replace-long-class-name-with-emoji" />`
- `<template class="🤓"/>`
- 固定长款

```css
.container-16x9 {
  position: relative;
  padding-top: 56.25%;
}
video {
  width: 100%;
  position: absolute;
  top: 0;
}

// or

video {
  width: 100%;
  aspect-ratio: 16/9;
}

```

- variables for variables

```css
:root {
  --r: 255;
  --g: 0;
  --b: 0;
  --text-color: rgb(var(--r), var(--g), var(--b));
}
p {
  --text-color: green;
  color: var(--text-color);
}
// ！待验证
h2 {
  --b: 255;
  color: var(--text-color);
}
```

- Fancy Calculations

```html
<style>
.drop {
  animation: dropIn 1s ease forward;
  animation-delay: calc(var(--order) * 100ms);
}
@keyframes dropIn {
  from { transform: translateY(-500px); }
  to { transform: translateY(0px); }
}
</style>
<i class="drop" style="--order: 1;">1</i>
<i class="drop" style="--order: 2;">1</i>
<i class="drop" style="--order: 3;">1</i>
```

- Counter

```css
:root {
  counter-reset: headings;
}
h1 {
  counter-increment: headings;
}
h1::before {
  content: counter(headings);
}
```

- Finding focus-within | 下拉框与父元素一起展示

```css
button:focus-within .dropdown {
  opacity: 1;
  visibility: visible;
}
```
