# fetch

## refs

## contents

### cancel requests

```js
const url = "https://jsonplaceholder.typicode.com/todos";

const controller = new AbortController();
const signal = controller.signal;
setTimeout(() => controller.abort(), 4000);

fetch(url, {
  signal: signal
})
  .then((response) => response.json())
  .then(console.log)
  .catch((err) => {
    console.error(err.message);
  });
```
