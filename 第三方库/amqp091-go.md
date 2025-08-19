# rabbitmq/amqp091-go


## 基础介绍

rabbitmq客户端库


## 核心内容
```yaml
rabbitmq/amqp091-go:
    amqp:
        Dial(): # 获取连接
    Channel: # 通道 
        Close():
        Consume(): # 消息消费
        ExchangeDeclare(): # 交换机声明
        Publish(): # 消息发布
        PublishWithContext():
        Qos():
        QueueBind(): # 队列绑定
        QueueDeclare(): # 队列声明
    Connection: # 连接
        Channel(): # 创建通道
        Close():
    Publishing: # 发布消息
    Queue: # 队列
```