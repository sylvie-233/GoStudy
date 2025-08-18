# sentinel-golang


## 基础介绍


Sentinel SDK



## 核心内容
```yaml
github.com/alibaba/sentinel-golang:
    /adapter:
        /gin:
            ginadapter: # gin适配
                SentinelMiddleware(): # Sentinel 中间件
                WithBlockFallback(): # 限流 处理
    /api:
        api: # 调用器
            Entry(): # 执行slot链，手动触发
            InitDefault(): # 初始化Sentinel 
            WithArgs(): # 携带参数
            WithAttachment():
            WithTrafficType():
    /core:
        /auth:
            auth: # 授权控制
                Rule:
                    LimitApp:
                    Resource:
                    Strategy:
                LoadRules():
        /degrade:
            degrade: # 熔断
                ErrorRatio: # 异常比例
                Rule: # 熔断规则
                    Resource:
                    Strategy: # 策略
                    Threshold:
                    TimeWindow:
                LoadRules():    
        /flow:
            flow: # 限流
                Rule: # 限流规则
                    ControlBehavior:
                    Resource: # 资源名
                    StatIntervalInMs:
                    Threshold:
                    TokenCalculateStrategy:
                LoadRules(): # 加载限流规则
                RegisterToProperty(): # 绑定数据源
        /hotspot:
            hotspot: # 热点参数
                Rule: # 热点参数规则
                    MetricType: # 
                    ParamIndex:
                    Resource:    
                LoadRules():
        /system:
            system: # 系统保护
                Rule:
                    MetricType:
                    Threshold:
                LoadRules():
    /ext:
        /datasource:
            /nacos:
                nacos: # nacos配置源
                    NewNacosDataSource():
    /logging:
    /stat:  
        stat:
            RegisterStatPropertySupplier(): # 开启 metric 上报接口 /metrics
```


### 流量控制




### 熔断降级

熔断策略：
- 平均响应时间
- 异常比例
- 异常次数


### 热点参数



### 系统保护



### 授权控制