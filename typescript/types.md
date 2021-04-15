# types

## refs

- <https://segmentfault.com/a/1190000016981025>

## contents

```ts
// basic syntax
type someType = somePrimitives | Object;
const val: someType = someValue;

// interface
interface Foo {
  [x: any]: someType;
}

// generic
interface Bar<T> {
  <T> (args: T): T; // function
  someProp: T; // normal key
}

// foo-class.d.ts
/**
 * .d.ts 不会产生具体的代码实体, 使用 declare 关键字，且不要使用 export 语句
 * 如果使用了 export，该文件就会变成实体 ts 文件，不会被 ts 的自动类型解析所识别，只能通过 import 使用
 */
declare class FooClass {
  someProp: someType;
  someMethod(someArgs: someType): someType;
}

// 
```
