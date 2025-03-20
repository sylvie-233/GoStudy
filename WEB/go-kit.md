# go-kit


## 基础介绍


Go kit 是一个专注于构建微服务的工具包，提供了各种功能，如服务发现、负载均衡、日志、监控、分布式追踪等。Go kit 适合需要高度定制的微服务架构，尤其适用于构建可扩展且高可靠性的服务
`github.com/go-kit/kit`
- 服务接口
- 服务实现
- 服务端点
- 传输层
- 中间件
- 服务发现、负载均衡
- 分布式追踪、监控
- 上下文传递



## 核心内容
```yaml
go-kit/kit:
    endpoint:
        Middleware: # 路由中间件
        Endpoint: # 路由处理函数
        Chain(): # 应用中间件到 Endpoint
    transport:
        http:
            NewServer():
```



### Endpoint

路由处理函数、请求、响应、编解码