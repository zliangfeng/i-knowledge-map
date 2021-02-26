场景：render生成的input autofocus
方案：
```js
creatElement(“input”, {
  ref: ”ref”,
  refInFor:true, //与v-for同时使用生成一个ref数组 
})
this.$refs.ref[0].focus();

// or
render: (h, params) => {
 return this.$createElement(compoent, {
   ref: “xxx”,
 }
}
```