## Refs
- https://medium.com/dailyjs/13-javascript-one-liners-thatll-make-you-look-like-a-pro-29a27b6f51cb

## Contents
```js
const isBrowserTabInView = () => document.hidden;
const toFixed = (n, fixed) => ~~(Math.pow(10, fixed) \* n) / Math.pow(10, fixed);
const elementIsInFocus = (el) => (el === document.activeElement);
const touchSupported = () => {  
('ontouchstart' in window || window.DocumentTouch && document instanceof window.DocumentTouch);  
}
const isAppleDevice = /Mac|iPod|iPhone|iPad/.test(navigator.platform);
const goToTop = () => window.scrollTo(0, 0);

```