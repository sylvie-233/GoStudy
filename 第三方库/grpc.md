# grpc

## 基础介绍

gRPC是由Google开发的一个高性能、开源且通用的远程过程调用（RPC）框架，它基于HTTP/2协议并使用Protocol Buffers（Protobuf）作为接口定义语言（IDL）来定义服务和消息


- `google.golang.org/grpc`
- `google.golang.org/protobuf/cmd/protoc-gen-go`
- `google.golang.org/grpc/cmd/protoc-gen-go-grpc`


gRPC支持四种类型的 API：
- 简单RPC：客户端发送一个请求并接收一个响应
- 服务器流式RPC：客户端发送一个请求，服务器返回一个流的响应
- 客户端流式RPC：客户端发送多个请求，服务器返回一个响应
- 双向流式RPC：客户端和服务器都可以发送多个请求和响应，适用于实时通信


### protoc
```yaml
protoc:
    --go-grpc_out:
    --go_out:
```


## 核心内容
```yaml
grpc:
    reflection:
        Register():
    Dial():
    NewServer():
    WithInsecure():
```