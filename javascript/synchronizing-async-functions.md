# synchronizing async functions in nodejs

## refs

- <https://www.youtube.com/watch?v=sPKYeQkzvVk>

## content

- Semaphore to block the main thread until the worker unblocks it

```js
// main thread
const { receiveMessageOnPort, MessageChannel } = require('worker_thread');
const subChannel = new MessageChannel();
const signal = new Int32Array(new SharedArrayBuffer(4));
signal[0] = 0;
worker.postMessage({ signal, port: subChannel.port1 }, [subChannel.port1]);
// block while the value at index 0 is 0;
Atomics.wait(signal, 0, 0, TIMEOUT);
const result = receiveMessageOnPort(subChannel.port2);

// worker
const result = await asyncFunction(...args);
// post the result to the main thread before unlocking signal
post.postMessage({ result });
post.close();
Atomics.store(signal, 0, 1);
Atomics.notify(signal, 0);
```
