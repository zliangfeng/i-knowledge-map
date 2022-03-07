# bundle-size-optimization

## refs

- <https://calibreapp.com/blog/bundle-size-optimization>
- <https://philipwalton.com/articles/deploying-es2015-code-in-production-today/>
- <https://www.smashingmagazine.com/2022/02/javascript-bundle-performance-code-splitting/>

## content

### 在 html 引入 es5/es6+ 两个版本的包

```html
<head>
  <script nomodule src="some/path/main.es5.js"></script>
  <script type="module" src="some/path/main.es6.mjs"></script>
</head>
```

### webpack 编译两个版本的包

参考 [[yarnpkg]]
