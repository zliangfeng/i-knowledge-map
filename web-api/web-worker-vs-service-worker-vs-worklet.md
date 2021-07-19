# web worker vs service worker vs worklet

## refs

- <https://www.jianshu.com/p/e2cdc78ff47c>
- <https://www.smashingmagazine.com/2021/06/web-workers-2021/>
- <https://surma.dev/things/omt-for-three-xr/index.html>

## web worker

> 可以简单的理解成运行在本地的 server，可以通过类似 rpc 的方式调用（通过api：onMessage/postMessage 通讯）；

## service worker

```js
/* main.js */
navigator.serviceWorker.register('/service-worker.js');

/* service-worker.js */
// Install 
self.addEventListener('install', function(event) {
    // ...
});
// Activate 
self.addEventListener('activate', function(event) {
    // ...
});
// Listen for network requests from the main document
self.addEventListener('fetch', function(event) {
    // Return data from cache
    event.respondWith(
        caches.match(event.request);
    );
});


```

> service worker 一旦安装并激活它们，就可以拦截从页面文档发出的任何网络请求，实现代理功能；
> 基于代理功能，service worker 可以将请求重定向到缓存，从而实现脱机访问

## worklet

```js
/* main.js */

CSS.paintWorklet.addModule('myWorklet.js');

/* myWorklet.js */

registerPaint('myGradient', class {
  paint(ctx, size, properties) {
    var gradient = ctx.createLinearGradient(0, 0, 0, size.height / 3);

    gradient.addColorStop(0, "black");
    gradient.addColorStop(0.7, "rgb(210, 210, 210)");
    gradient.addColorStop(0.8, "rgb(230, 230, 230)");
    gradient.addColorStop(1, "white");

    ctx.fillStyle = gradient;
    ctx.fillRect(0, 0, size.width, size.height / 3);
  }
});

```

```css
div {
  background-image: paint(myGradient);
}
```

> worklet 与浏览器的渲染管道挂钩，使我们能够对浏览器的渲染过程（例如样式和布局）进行低级访问；
