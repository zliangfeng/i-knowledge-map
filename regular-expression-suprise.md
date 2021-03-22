# Regular Expression Surprise

## Refs
- <https://blog.rebased.pl/2021/03/16/a-regular-expression-surprise-in-javascript.html>

## Content
```javascript
exports.digits = /\d+/g;
const { digits } = require("./regex");

digits.test("Hello world! 123");
// true
digits.test("321");
// false, 原因是正则开启 global 之后，digits.lastIndex 会记录上一次匹配的位置，下一次执行 test()/exec()的时候，会从 lastIndex 开始执行查找
digits.test("321"); // 上一次执行失败，则 set： lasteIndex = 0；所以这一次执行的结果为 true
// true
```
改进方案：
```javascript
const { digits } = require("./regex");

"Hello world! 123".search(digits) > -1;
// true
"321".search(digits) > -1;
// true
"321".search(digits) > -1;
// true
```