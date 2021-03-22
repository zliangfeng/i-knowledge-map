# DOM Event 实践

## Refs

## Content

### input.blur 事件覆盖了 button.click 事件
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
  - 思考：可不可不修改定义事件，捕获/冒泡 or not？
```