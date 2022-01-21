## example

```js
function createWebService(baseUrl) {
  return new Proxy({}, {
    get(target, propKey, receiver){
      return () => httpGet(baseUrl + "/" + propKey);
    }
  });
}
```