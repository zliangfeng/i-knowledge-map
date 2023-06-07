## refs
- <https://twitter.com/mattpocockuk/status/1625838626742435842>

## contents

> 如果是为了炫技，大可不必使用泛型；但对于编写API、重构代码等场景，泛型确实能减少冗余代码，保持设计简洁，降低心智认知。

### 应用场景

1. 传递 types to types
```ts
type PartialUser = Partial<{ id: string; name: string;}>;
```
2. 传递 types to functions
```ts
const stringSet = new Set<string>();
```
3. 传递 arguments types to functions
```ts
const objectKeys = <T extends object>(obj: T) => {
	return Object.keys(obj) as Array<keyof T>;
}
```

### 示例

以下是一段简单但不简约的类型定义：
```typescript
//  original code snippets
type ErrorShape = {
	message: string;
	code: string;
};
type GetUserData = {
	data: {
		id: string;
		name: string;
	};
	error?: ErrorShape;
};
type GetPostsData = {
	data: {
		id: string;
		title: string;
	}[];
	error?: ErrorShape;
};
type GetCommentData = {
	data: {
		id: string;
		content: string;
	}[];
	error?: ErrorShape;
};
```

使用`type function`, neatly!!!
```ts
type DataShape<T> = {
	data: T;
	error?: ErrorShape;
}
type GetUserData = DataShape<{
	id: string;
	name: string;
}>;
type GetPostsData = DataShape<{
	id: string;
	title: string;
}[]>;
type GetCommentData = DataShape<{
	id: string;
	content: string;
}[]>;
```

PS: 如果采用 OOP 方式重构，见仁见智；
```ts
interface DataBase {
	error?: ErrorShape;
}
interface GetUserData extends DataBase {
	data: {
		id: string;
		name: string;
	};
}
interface GetPostsData extends DataBase {
	data: {
		id: string;
		title: string;
	}[];
}
interface GetCommentData extends DataBase {
	data: {
		id: string;
		content: string;
	}[];
}
```
