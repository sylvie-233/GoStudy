# RxGo

## 基础介绍

go的响应式编程，可以用于异步处理、流式数据处理、事件驱动编程


## 核心内容
```yaml
rxgo:
    Disposed: # 流结束通知对象，本质上是通道 <-chan struct{}
    Duration: # 时间间隔
    Item: # 数据对象
        E: # 异常值
        V: # 数据值
        Error():
    Observable: # 可观测对象接口，数据流（流式数据源）
    ObservableImpl: # 可观测对象实现
        BufferWithCount(): # 批处理 
        BufferWithTime():
        BufferWithTimeOrCount():
        Debounce():
        Distinct():
        DoOnNext(): # 异步消费Item
        ElementAt():
        Filter(): # 过滤
        ForEach(): # 遍历，结束流
        GroupBy(): # 分组
        Map(): # 转换
        Marshal(): # 编码
        Observe(): # 返回通道数据chan，配合for循环遍历
        Repeat(): # 定时重复创建
        Skip():
        Take():
        Unmarshal(): # 解码
    Option: # 配置策略
    Predicate: # (v) bool
    Producer: # Item生产者：(Context, chan<- Item)
    Supplier: # 类似Item生产者： (Context) Item
    Assert():
    Create(): # 根据Producer生产者创建Observable
    Defer(): # 根据Producer 创建 Cold Observable
    Empty(): # 空 Observable
    Error(): # 异常Error Item
    FromChannel(): # 根据Item chan 创建 Observable
    Interval(): # 定时创建Observable，无穷的数字序列
    Just(): # 根据字面量 返回 Observable创建函数
    Merge(): # Observable数据流合并
    Of(): # 根据值 创建Item
    Range(): # 根据范围 创建 Observable
    SendItems():
    Start(): # 根据Supplier 创建 Observable
    WithContext(): # 上下文管理Option
    WithDuration():
    WithPool(): # goroutine 并发池
    WithPublishStrategy():
```


### Observable

数据流、可观测对象
- Hot Observable: 第一次Observe()消耗了所有的数据，第二个就没有数据输出了
- Cold Observable: 创建的流是独立于每个观察者的。即每次调用Observe()都创建一个新的channel


### Item

数据对象

### Option

数据流配置

### Operator

#### BufferWithCount
#### Distinct
#### ElementAt
#### Filter
#### GroupBy
#### Map


#### Marshal

#### Skip
#### Take
#### Unmarshal