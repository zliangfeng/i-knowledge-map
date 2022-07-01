# send-an-http-request-on-page-exit

## refs

- <https://css-tricks.com/send-an-http-request-on-page-exit/>

## contents

> 在 page 被关闭之时发送请求

- fetch + keepAlive:true
  - 适合请求一定要完成才能关闭 page 的情况
  - 网络请求级别高
- Navigator.sendBeacon()
  - 适合请求不一定需要到达，如发送日志等
  - 网络请求级别低
