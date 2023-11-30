# preact/signals

## code

```js
import { signal } from "@preact/signals-react";

const count = signal(0);

// Unoptimized: Will trigger the surrounding
// component to re-render
/*function Counter() {
  return <p>Value: {count.value}</p>;
}*/

// Optimized: Will update the text node directly
function Counter() {
  return (
    <p>
      <>Value: {count}</>
    </p>
  );
}
```

### Wrapper

有点写 vuejs 的味了！
