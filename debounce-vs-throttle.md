# debounce-vs-throttle
## Refs
- https://css-tricks.com/debouncing-throttling-explained-examples/

## Debounce
- 一种策略（implementations 参考 lodash）
  - 将所有的事件按间隔时间分组，只执行队首的一个事件
  - If you only need the _.debounce and _.throttle functions
```bash
npm i -g lodash-cli
lodash include = debounce, throttle
```
```js
// WRONG
$(window).on('scroll', function() {
   _.debounce(doSomething, 300); 
});

// RIGHT
var debounced_version = _.debounce(doSomething, 200);
$(window).on('scroll', debounced_version);
// If you need it
debounced_version.cancel();

```

## throttle
- main difference between this and debouncing
  - throttle guarantees the execution of the function regularly, at least every X milliseconds.
- 典型场景
  - 下拉到 infinite-scrolling page 底部，需要 ajax 获取内容；这个时候 debounce 是无能为力的（scroll事件不触发了）
## requestAnimationFrame
- 约等于 _.throttle(dosomething, 16)，但更加精准（browser native API，Aims for 60fps (frames of 16 ms) ）
- cons
  - If the browser tab is not active, it would not execute. Although for scroll, mouse or keyboard events this doesn’t matter.
  - not supported in IE9, etc.
  - The start/cancelation of rAFs it’s our responsibility.

## Summary:
- debounce: Grouping a sudden burst of events (like keystrokes) into a single one.
- throttle: Guaranteeing a constant flow of executions every X milliseconds. Like checking every 200ms your scroll position to trigger a CSS animation.
- requestAnimationFrame: a throttle alternative. When your function recalculates and renders elements on screen and you want to guarantee smooth changes or animations. Note: no IE9 support.