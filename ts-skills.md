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