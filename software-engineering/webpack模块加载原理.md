# webpack 模块加载原理

## refs

- <https://juejin.cn/post/6872354325553741838>

## commonJS

- 复习：require 相当于其他语言的内联（inline），同步
- 简化模型

```js
(function(modules) {
  // the module cache
  var installedModules = {};

  // the require function
  function __webpack_require__(moduleId) {
    // …
  }
  // load entry module and return exports
  return __webpack_pack__(__webpack_require__.s = "./src/index.js")
})({
  // pathX: functionX
  "./src/index.js": (function(module, exports, __webpack_require__){
    eval(/*webpack eval code*/);
  }),

})

// webpack eval code format
const test2 = __webpack_require__("./src/test2.js\")"
function test() {}
test()
test2()
```

> 小结：webpack 对源码用 webapck_require 封装后，再通过 eval 引入

## ES6 module

- 打包后的代码与 commonJS 绝大部分一致
- 差异：多了 \_\_webpack_require\_\_.n 分析 export 对象是否是 ES6 module，如果是则返回 module["default"]，否则返回 export

## 按需加载

- 多了核心函数 \_\_webpack_require\_\_.e(chunkId).then(\_\_webpack_require\_\_.bind(null, "./src/test2.js"))
- e() 下载动态资源，执行返回第一次为 undefined，新建 Promise 用于加载远程 js 资源
- 返回 0 代表加载成功
- 返回其他表示加载中，将这个加载中的 Promise 推入 promises 数组（类似 call queue）
- TODO: 加载 `<script src="0.bundle.js" charset="utf-8" nonce />`
