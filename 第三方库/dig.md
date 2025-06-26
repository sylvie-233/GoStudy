# dig


## 基础介绍


依赖注入（Dependency Injection, DI）框架，由 Uber 团队开发



## 核心内容
```yaml
go.uber.org/dig:
    dig:
        In: # 注入多个参数
        Out: # 返回多个构造值
        New(): # 创建容器
    Container: # 
        Invoke(): # 调用函数并自动注入参数
        Provide(): # 注入
```