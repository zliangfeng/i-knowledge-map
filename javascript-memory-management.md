# javascript-memory-management

## Refs
- https://felixgerschau.com/javascript-memory-management/

## 数据分配
### Stack: Static memory allocation
- 编译期（compile time）
- 在栈（Stack）中
- 为每个值，包括 primitive values (strings, numbers, booleans, undefined, and null) and references
- 分配固定大小内存（fixed amount of memory ）

### Heap: Dynamic memory allocation
- 在堆（Heap）
- 为 objects and functions 动态分配内存
- 注意：objects 中的 primitive values 仍然分配在 Stack 

## Garbage collection
### Reference-counting garbage collection
- 当 no references 指向 objects 之后，就会被标记 GA
- 循环引用 ｜ Cycles
  - objects 出现了循环引用，即使将变量赋值为 null，也不能被 GA 标记
  - 主要是此刻的 objects 仍在 heap 中持有相互的引用

### Mark-and-sweep algorithm
- 解决循环引用的问题
- 当变量不能被 root object 访问时候，就可以标记清除了
- root object：window（Browsers） / global（Node）

## Memory leaks
### Global variables
- 当变量不限定 scope 的时候（without var / let / const），将会自动 attach 到 root object；
- `use strict;` mode 下不允许上述赋值
- `window.xxx = null;` 释放

### Forgotten timers and callbacks
- `clearInterval(intervalId);` 显式清除定时器
- `element.removeEventListener('click', onClick);` 显式清除监听事件
- `element.parentNode.removeChild(element);` 显式清除元素

### Out of DOM reference
```javascript
const elements = [];
const element = document.getElementById('button');
elements.push(element);

function removeAllElements() {
  elements.forEach((item, index) => {
    document.body.removeChild(document.getElementById(item.id)); // 显式清除 DOM
    elements.splice(index, 1); // 显式清除 Array 中的引用
  });
}
```