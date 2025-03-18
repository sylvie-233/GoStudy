# go-redis


## 基础介绍


redis数据库连接库
`github.com/go-redis/redis/v8`


## 核心内容
```yaml
redis:
    Client: # 连接客户端
        Del():
        Get(): # string get
        HGet(): # hash get
        HSet(): # hash set
        Incr():
        LPop(): # list pop
        LPush(): # list push
        Ping(): # 连接测试
        Publish(): # channel 消息发布
        Set(): # string set
        Subscribe(): # channel 消息订阅
    Message: # 发布订阅消息
        Payload:
    Options: # 连接配置
        Addr:
        DB:
        Password:
    PubSub: # channel发布订阅类
        ReceiveMessage():
    StringCmd: # 字符串结果
        Result():
    StatusCmd: # 状态结果
        Err():
        Result():
    NewClient(): # 新建客户端
```
