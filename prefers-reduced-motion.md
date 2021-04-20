# 减少 Web 页面动效

```ts
const match: boolean = window.matchMedia(
  "(prefers-reduced-motion: no-preference)"
).matches;
// args: reduce | no-preference
```

```css
//unset
@media (prefers-reduced-motion: reduce) {
  * {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
}
```