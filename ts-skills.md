## refs
- <https://startup-cto.net/10-bad-typescript-habits-to-break-this-year/>
- <https://jakearchibald.com/2021/function-callback-risks/>


## contents
- `any` is convenient, as it basically disables all type-checks
```ts
async function loadProducts(): Promise<Product[]> {
  const response = await fetch('https://api.mysite.com/products')
  const products: unknown = await response.json()
  return products as Product[]
}
```

```ts
function isArrayOfProducts (obj: unknown): obj is Product[] {
  return Array.isArray(obj) && obj.every(isProduct)
}

function isProduct (obj: unknown): obj is Product {
  return obj != null
    && typeof (obj as Product).id === 'string'
}

async function loadProducts(): Promise<Product[]> {
  const response = await fetch('https://api.mysite.com/products')
  const products: unknown = await response.json()
  if (!isArrayOfProducts(products)) {
    throw new TypeError('Received malformed products API response')
  }
  return products
}
```

```js
const controller = new AbortController();
const { signal } = controller;
el.addEventListener(name, callback, { signal });
```

### type
```ts
/*class BeeKeeper {

hasMask: boolean;

}

class ZooKeeper {

nametag: string;

}

class Animal {

numLegs: number;

}

class Bee extends Animal {

keeper: BeeKeeper;

}

class Lion extends Animal {

keeper: ZooKeeper;

}*/
function createInstance<A extends Animal>(c: new () => A): A {

return new c();

}
//createInstance(Lion).keeper.nametag;

//createInstance(Bee).keeper.hasMask;
```

```ts
interface {
	fn(): void;
	foo: string;
	bar: number;
}

// SomeType extends OtherType ? TrueType : FalseType;
type NameOrId<T extends number | string\> = T extends number

? IdLabel

: NameLabel;
			  
function createLabel<T extends number | string\>(idOrName: T): NameOrId<T\> {

throw "unimplemented";

}

let a = createLabel("typescript");

// ^ = let a: NameLabel

let b = createLabel(2.8);

// ^ = let b: IdLabel

let c = createLabel(Math.random() ? "hello" : 42);

// ^ = let c: NameLabel | IdLabel