# clickjacking-attacks

## Refs

- <https://auth0.com/blog/preventing-clickjacking-attacks/>

## Desc

- 存在诈骗（如有付款按钮）的页面（vulnerable_website）A
- 存在引导的页面（attacker_website）B
- 将 A 嵌入到 B（如 B 中引入 A 的 iframe），且 A 将 B 完全覆盖（如 A 的 z-index 大于 B）
- 客户本意是要点击 B 页面的按钮，但实际上点击了 A 的按钮（如付款按钮）

## 预防

- Client-side defenses
  - frame-busting

```html
<html>
  <head>
    <title>Vulnerable Page</title>
    <script>
      if (top != window) {
        /**
         * 注意，这个方法并不能 100% 防御
         * 该段代码触发 window.onbeforeunload event, 如果 Attracker Page 重写了该事件：
         * window.onbeforeunload = () => false;
         * 则页面不会重加载；
         */
        top.location = window.location;
      }
    </script>
  </head>
</html>

<html>
  <head>
    <title>Attracker Page</title>
    <script>
      window.onbeforeunload = function () {
        return false;
      };
    </script>
  </head>
  <body>
    <iframe id="vulnerable_website" src="http://localhost:3000" sandbox="allow-scripts allow-forms allow-same-origin">
    </iframe>
  </body>
</html>
```

// 总结来看，client-side 通过 block clickjacking attacks 容易被绕过去

- 使用 X-Frame-Options header

```js
// server.js
app.use(function (req, res, next) {
  res.setHeader("X-Frame-Options", "sameorigin");
  next();
});
```

// 可能遇到浏览器不支持 X-Frame-Options，继续：

- Using CSP / Content-Security-Policy

```js
// server.js
app.use(function (req, res, next) {
  // same as { X-Frame-Options: "sameorigin" }
  res.setHeader("Content-Security-Policy", "frame-ancestors 'self';");

  // frame-ancestors 'none' - Not allowed to use frame at all.
  // frame-ancestors https://www.authorized-website.com - Only allowed at specific websit.
  next();
});
```

// 注意：X-Frame-Options 优先级高

- Using cookie's sameSite origin

```js
// server.js
app.use(
  session({
    secret: "my-secret",
    resave: true,
    saveUninitialized: true,
    cookie: {
      httpOnly: true, // Cookie 只能通过服务器端修改，Js 是操作不了的
      sameSite: "strict", //👈 new code
    },
  })
);
```
