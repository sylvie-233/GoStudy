# dubbo-go



## 基础介绍

dubbo go语言实现


### dubbogo.yaml
```yaml
dubbo:
    application:
        name: # 应用名称
    protocols: # rpc协议
        dubbo:
            name: # "dubbo"
            port: # 20000
    registry: # 注册中心
        protocol: # "nacos"
        address: # "127.0.0.1:8848"
```



## 核心内容
```yaml
github.com/apache/dubbo-go/v3:
    config:
        Load():
        SetConsumerService():
```