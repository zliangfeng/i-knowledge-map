# node-js-image-processing

## Refs
- https://medium.com/better-programming/sharp-high-performance-node-js-image-processing-library-3f04df66c722

## 目的
- user-friendly
- loader faster
- even higher quality

## SharpJS 功能
- 调整大小
```js
const sharp = require˜˜˜("sharp");

sharp("example-image.jpg")
  .resize({ width: 500, height: 450 })
  .toFile("output.jpg");
```

- 格式化 / 旋转
```js
const sharp = require("sharp");

sharp("example-image.jpg")
  .resize({ width: 500, height: 450 })
  .rotate(180)
  .toFormat("png")
  .png({ quality: 100 })
  .toFile("output.png");
```

- 