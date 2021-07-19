# vue event 实践

## Refs

## Content

- 场景：input 使用 blur 事件触发保存/校验，另有按钮保存/删除，当焦点在 input 上的时候，点击保存/删除，会触发 blur 事件导致点击失效
- 已知优先级 blur > click
  - 方案1: 使用 setTimeout(blurFn, millisenconds)，click 可以执行，但如果执行校验成功，会有明显的卡顿感觉
  - 方案2: mousedown 事件优于 blur，在 button 上添加 mousedown 事件阻止冒泡

```javascript
render: (h) => {
  return h('button',
    {
      nativeOn: {
        mousedown: (e) => {
          e.preventDefault();
        },
      },
      on: {
        click: () => {},
      }
    },
  );
}
  - 思考：不修改定义事件，捕获/冒泡 or not？
```

## method 参数


- 默认传参为 $event；自定义传参如：someVal1，someVal2，$event


```vue

```

## 子组件向父组件传参


- 传一个参数，父组件第一个参数接收

- 传多个参数，父组件第一个参数为 arguments


## 父组件接收混合传参

- method 中，第一个参数来自子组件，第二个参数之后接收父组件参数

