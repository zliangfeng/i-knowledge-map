#typescript 中， #type 与 #interface 是经常用来做比较的
类比来看，interface 是一种申明（statement），而 type 是一种表达式（expression）
```ts
// statement
let cache;
// 不同点 1
interface Cache {
	[id: string]: any;
};
// expression
const num = 1;
type Wrapper<T> = {
	value: T;
}

// 不同点 2
interface CacheStore extends Cache {
	uuid: string;
}
type NumberWrapper = Wrapper<number>;
```