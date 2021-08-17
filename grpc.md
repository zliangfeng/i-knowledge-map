# gRPC

## Refs

- <https://www.programmableweb.com/news/what-grpc-api-and-how-does-it-work/analysis/2020/10/08>
- <https://adityasridhar.com/posts/how-to-effectively-use-grpc-streams-in-nodejs>

## What

- RPC | Remote Procedure Calls，远程处理调用，如：
  - DB 中的 Stored Procedures
  - Java Remote Method Invocation (Java RMI): 缺点是 Client Side 也需要是 Java 编写
  - XML-RPC：Wordpress
  - SOAP：WDSL
- gRPC (gRPC Remote Procedure Calls) 是 Google 发起的一个开源远程过程调用 (Remote procedure call) 系统；
  - Information is serialized into a compact collection of bits and then sent over the network. Then, when the bits reach the target destination they are deserialized back into text.
  - Protocol Buffers - gRPC_Schema.proto file: 该文件可以类比接口文件，描述了 rpc 的版本/请求响应/methods 等

```proto
syntax = "proto3";
package simplegrpc;
message Request {
    repeated double numbers = 1; // index number of 1
    string data = 2; // index number of 2
    int32 limit = 3; // // index number of 3
}
message Response {
    double result = 1;
}
...
service SimpleService {
    rpc Add (Request) returns (Response) {}
}
```

二进制编码示意图：
｜ 1 ｜--some numbers ｜ 2 ｜--string--｜ 3 ｜--int32--｜

## Why

有了 http/restful 为啥还需要 RPC

- RPC 可以解决 http 协议中无效信息过多的问题；
- 适用场景：分布式服务

## Difference

- REST

  - text-based formats / JSON / XML
  - http

- gRPC
  - binary format
  - 有一个 .proto 文件，定义了 data 的格式
  - 发送端根据 proto 将 data 串化（serialized）
  - 接收端解串化（deserialized）

```diff
function addTwoNumbers (num1, num2) {
-  return 1 + 2
+  return num1 + num2
}
```
