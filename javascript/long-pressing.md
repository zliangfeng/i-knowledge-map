# long-pressing

## refs

- <https://spacejelly.dev/posts/how-to-detect-long-press-gestures-in-javascript-events-in-react/>

## contents

- 基本的思路
  - 在 onTouchStart/onMouseDown 中添加一个时长为 tos 的 timeout 事件（超过 tos 触发）
  - 在 onTouchEnd/onMouseUp 中 clearTimeout，清除 timeout 事件
