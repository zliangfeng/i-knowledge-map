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
// todo