# obj-proto-vs-fn-prototype

## Refs
- https://segmentfault.com/a/1190000021232132
- https://juejin.im/post/6844903782229213197
- https://juejin.im/post/6844904093828251662

## Function.prototype
- prototype是函数独有的
- prototype属性可以看作成一块特殊的存储空间，提供了子类使用的方法和属性

## Object.__proto__
- 使用__proto__是有争议的，也不鼓励使用它
- __proto__属性是对象（包括函数）独有的，指向该对象的原型对象，相当于通往prototype的指针

## Object.constructor
- constructor是对象才有的属性，指向该对象的构造函数

## new一个新对象的过程，发生了什么？
(1) 创建一个空对象 son {}
(2) 为 son 准备原型链连接 son.__proto__ = Father.prototype
(3) 重新绑定this，使构造函数的this指向新对象 Father.call(this)
(4) 为新对象属性赋值 son.name
(5) return this，此时的新对象就拥有了构造函数的方法和属性了


```js
function Function() {
    this.constructor = Function; // 是其本身
    this.__proto__  = Function.prototype;
    this.prototype = Function.prototype;
}
Function.prototype = {
    __proto__: Object.prototype,
}
function Object() {
    this.constructor = Function;
    this.__proto__ = Function.prototype;
    this.prototype = Object.prototype;
}
Object.prototype = {
    __proto__: null,
    constructor: Object(),
}
function Parent() {
    this.constructor = Function;
}
const children = new Parent();
children.__proto__ === Parent.prototype; // true
Parent.__proto__ = Function.prototype; // true；Parent 本质上是 Function 的一个实例
Parent.prototype.__proto__ === Object.prototype; //true；Parent.prototype 是 Object 的一个实例
Object.prototype.__proto__ === null; // true；
```
