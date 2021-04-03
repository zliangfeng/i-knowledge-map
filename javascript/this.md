# this

## Refs

- <https://web.dev/javascript-this/>

## Content

 在Javascript中，this的值是根据**方法如何调用**来定义的，当通过引用调用该方法时，`this`的值就变成了所谓的[[全局对象]]

```js
/*
 * 箭头函数为匿名函数，this = outer functions
 */
const myObject = {
  method(items) {
    console.log(this); // logs "myObject"
    const callback = () => {
      console.log(this); // logs "myObject"
    };
    items.forEach(callback);
  },
};
myObject.method([]); // logs "myObject"
/*** fn_ref的例子 ***/
// 这里将method赋值给一个变量，在浏览器运行的时候，上下文就变成了 window
const myObjectMethod = myObject.method;
myObjectMethod([]); // logs "window"
```
