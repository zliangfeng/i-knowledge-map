# memoizing

## refs

- <https://stackfull.dev/memoizing-async-functions-in-javascript>

## contents

### 同步 memoizing

```javascript
function memoize(fn, getKey) {
  const store = {};
  return function memoized(...params) {
    const key = getKey(...params);
    if (store.hasOwnProperty(key)) return store[key];
    store[key] = fn.apply(this, params);
    return store[key];
  }
}
```

### 异步 memoizing

```javascript
// 不推荐写法 ，调用不够清晰
// 这种写法，参数 params 一定要在最后一个传递 callback
function asyncMemoize(fn, getKey = (_key) => _key) {
  const store = {};
  const progressQueues = {}; // { [key]: [ ...callbacks ] }
  return function memoized(params) {
    const callback = params[params.length-1];
    const args = params.slice(0, -1);
    // ... return if exists 
    // ... store progressQueues
    fn.call(this, ...args, (data) => {
      store[key] = data;
      for (let callback of progressQueues[key]) {
        callback[data];
      }
      delete progressQueues[key];
    });
  } 
}
const memoExpensiveOperation = asyncMemoize((params) => {
  // ...
  const data = someAsyncActions();
  const storeResultThenProgressQueuesAndClean= params.slice(-1)[0];
  storeResultThenProgressQueuesAndClean(data);
})

function asyncMemoizeWithPromise(processData, getKey) {
  const store = {};
  const progressQueues = {}; // { [key]: [[ resolve, reject ], ...] }
  return new Promise((resolve, reject)) => {
    // ... return if exists 
    // ... store progressQueues
    processData(key).then(data => {
      store[key] = data;
      // process progressQueues' resolvers
    }).catch(
      // process progressQueues' rejectors
    ).finally(() => {
      delete progressQueues[key];
    });
  }); 
}
```
