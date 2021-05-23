# 跨域

## refs

- [AJAX 与跨域通信（二）：跨域解决方案](https://cloud.tencent.com/developer/article/1536496)

## content

- JSONP

```js
// 1.DomainA 回调函数
function handleResponse(data){
    console.log(data);
}
// 2.动态创建 script 
var script = document.createElement('script');
script.src = 'http://DomainB/json?callback=handleResponse';
document.body.insertBefore(script,document.body.firstChild);
// 加载完了上述<script>之后，里面执行`handleResponse(someDataFromTestCom)`
// DomainA 就这样获取了 DomainB 的数据，实现了跨域
```

- CORS
  - 简单请求: {head|post|get} 携带的头信息仅限于 {Accept|Accept-Language|Content-Language|Last-Event-ID|Content-Type{application/x-www-form-urlencoded|multipart/form-data|text/plain}，CORS的时候header额外携带origin字段；
  - 非简单请求：preflight request;

- 图像 ping

- document.domain
  - 适用于主域相同、子域不同的两个域之间的跨域通信

- window.name
  - 