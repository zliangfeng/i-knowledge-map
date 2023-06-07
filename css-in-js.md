## refs
- https://dev.to/srmagura/why-were-breaking-up-wiht-css-in-js-4g9b

## contents

### Props

- 能使用JS变量
- 作用于局部范围

### Cons

- 增加运行时后开销
	- 频繁插入CSS规则迫使浏览器做很多额外的工作，如在并发渲染中，频繁检查插入的CSS规则是否适用于现有的树，导致在 React 渲染时针对所有 DOM 节点的每一帧重新计算所有 CSS 规则
	- 不可能修复
- 容易出错
- 增加 bundle size

### Alternative

- SASS
- Bootstrap/Tailwind