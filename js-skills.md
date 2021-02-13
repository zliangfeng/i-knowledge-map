## Refs
- https://medium.com/dailyjs/13-javascript-one-liners-thatll-make-you-look-like-a-pro-29a27b6f51cb
- https://github.com/kettanaito/naming-cheatsheet
- https://dev.to/noseratio/a-few-handy-javascript-tricks-an9

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
### Naming
- isXxxExists => hasXxx
- A/HC/LC Pattern: prefix? + action (A) + high context (HC) + low context? (LC)
### promise-memoization
```ts
import memoize from 'memoizee';

const getUserById = memoize(async (userId: string): Promise<User> => {
  const user = await request.get(`https://users-service/${userId}`);
  return user;
}, { promise: true});
```
### exponential backoff retry strategy
```js
const callWithProgress = async (fn, status, depth = 0) => {
	const result = await fn(status);
  // check completion
  if (result.progress === 1) { 
    // finished
    return result.result;
  } else { // unfinished
  	if (depth > 7) { throw result; } 
  	await wait(2 ** depth * 10);
  	return callWithProgress(fn, result.progress, depth + 1);
  }
}