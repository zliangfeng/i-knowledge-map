# yarnpkg

## 指定依赖/子依赖版本|覆盖特定嵌套依赖项的版本

package.json

```json
{
  "name": "project",
  "version": "1.0.0",
  "dependencies": {
    "left-pad": "1.0.0",
    "c": "file:../c-1",
    "d2": "file:../d2-1"
  },
  "resolutions": {
    "d2/left-pad": "1.1.1",
    "c/**/left-pad": "1.1.2"
  }
}
```

之后执行 yarn install

## 替换 lodash/moment

```json
{
  "rules": {
    "no-restricted-imports": [
      "error",
      {
        "paths": [
          {
            "name": "moment",
            "message": "Use date-fns instead. See https://bundlephobia.com/package/moment"
          }
        ]
      }
    ]
  }
}
```

## build es5 / es6+ 两个版本

```html
<!-- Deliver ES5 code to non-module supporting browsers -->
<script nomodule src="legacy-support-bundle.js"></script>

<!-- Deliver ES2015+ code to module capable browsers -->
<script type="module" src="bundle.js"></script>
```

```js
// webpack.es5.js
module.exports = {
  entry: './path/to/main.mjs',
  output: {
    filename: 'main.es5.js',
    path: path.resolve(__dirname, 'public'),
  },
  module: {
    rules: [{
      test: /\.m?js$/,
      use: {
        loader: 'babel-loader',
        options: {
          presets: [
            ['env', {
              modules: false,
              useBuiltIns: true,
              targets: {
                browsers: [
                  '> 1%',
                  'last 2 versions',
                  'Firefox ESR',
                ],
              },
            }],
          ],
        },
      },
    }],
  },
};
```

```js
// webpack.es6.js
module.exports = {
  entry: './path/to/main.mjs',
  output: {
    filename: 'main.mjs',
    path: path.resolve(__dirname, 'public'),
  },
  module: {
    rules: [{
      test: /\.m?js$/,
      use: {
        loader: 'babel-loader',
        options: {
          presets: [
            ['env', {
              modules: false,
              useBuiltIns: true,
              targets: {
                browsers: [
                  'Chrome >= 60',
                  'Safari >= 10.1',
                  'iOS >= 10.3',
                  'Firefox >= 54',
                  'Edge >= 15',
                ],
              },
            }],
          ],
        },
      },
    }],
  },
};
```
