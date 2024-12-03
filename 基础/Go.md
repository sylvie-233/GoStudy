# Go

## 基础介绍

`package main`声明主模块

`gopath`：go模块搜索路径

`GOPATH/pkg/mod` :存放下载的第三方包




### go
```yaml
go:
    build:
    clean:
    doc:
    env: # go环境变量
    fmt: # 格式化代码
    get: # 下载包
    help:
    install:
    list: #
    mod: # 模块管理工具
        edit:
        init: # 初始化模块
        tidy:
        vendor:
    run: # 运行
    test:
    tool: # go工具链
    version: # go版本

```

go命令行


### go.mod
```yaml
go.mod:
    module: # 模块声明
    go: # 指定go版本
```

模块配置文件




## 核心内容
```yaml
std:
    _builtin:
        bool:
        byte: # uint8字节
        chan:
            Close():
        error:
        float32:
        map:
            Add():
            Set():
        nil: # 空值
        rune: # int32字符
        slice:
        string:
        append(): # slice追加元素
        close(): # 关闭chan
        delete(): # 删除键值对
        len():
        make():
        new():
        panic():
    big:
        NewInt():
    bufio: # 输入缓冲
        Reader:
            ReadString():
        NewReader():
    context:
        Context:
            Deadline():
            Done():
            Err():
            Value():
        Background():
            Value():
        \TODO():
        WithCancel():
        WithTimeout():
        WithValue():
    crypto:
        rand:
    database:
        sql:
            Db:
                SetMaxOpenConns():
    encoding:
        json:
            _tag:
                json:
                    omitempty:
            Decoder:
                Decode():
            Encoder:
                Encode():
            Marshal(): # json序列化
            MarshalIndent():
            NewDecoder():
            NewEncoder):
            Unmarshal(): # json反序列化
            Valid(): # json格式校验
    errors:
        Is():
        New():
    fmt: # 格式化
        Printf():
        Println(): # 打印换行
    io:
        CopyBuffer():
        WriteString(): # 写入字符串
            file:
            str:
            ---
            length:
    ioutil: # io工具包
        ReadAll():
            ---
            bytes:
        ReadFile():
    log:
        Fatal():
    math:
        rand:
            Intn():
            Seed():
    net:
        http:
            Request:
                Body:
            Response: # 响应对象
                Body:
                ContentLength:
                StatusCode:
            ResponseWrite:
                Header():
                Write():
            Server:
                Addr:
                Handler:
                Shutdown():
            Get(): # get请求
            ListenAndServe(): # 监听服务
            PostForm():
        url:
            URL:
                Host:
                Path:
                RawQuery:
                Scheme:
                Port():
                Query():
                String():
            Values:
            Parse():
    os:
        File:
            Close(): # 关闭文件
        Interrupt:
        Signal:
        Stdin: # 标准输入
        Chdir():
        Create(): # 创建文件File
    reflect: # 反射
        Float32:
        Int32:
        Method: # 方法
            Name():
            Call():
            Type():
        rtype:
        StructField: # 字段结构
            Name:
            Tag:
                Get():
            Type:
        Type: # 类型
            Field(): # 根据index获取字段
            FieldByName(): # 根据名称查找字段
            Kind(): # 类型种类
            Method(): # 根据index获取方法
            MethodByName():
            Name(): # 类型名
            NumField(): # 字段个数
            NumMethod():
        Value: # 值
            Elem(): # 根据指针取值
            FieldByName():
            Float():
            Int():
            IsNil():
            Kind():
            MapIndex():
            MethodByName():
            SetInt():
        TypeOf():
        ValueOf():
    signal: # 信号
        Notify(): # 监听信号（配合chan）
    strconv: # 字符串转换
        Itoa():
        ParseFloat():
    strings: # 字符串工具
        Builder:
            String():
            Write(): # 写入
        Reader:

        NewReader():
        Trim():
    sync:
        Mutex: # 互斥锁
            Lock():
            Unlock():
        RWMutex:
            RLock():
            RUnlock():
        WaitGroup: # 等待计数
            Add(): # 计数+1
            Done(): # 计数-1
            Wait(): # 等待
    testing:
        T:
    time: # 时间
        Date:
        Location:
        Millisecond:
        Month:
        Time: # 时间
            Format():
        After():
        Now(): # 当前时间
        Sleep():
```




### 数据类型
```yaml
types:
    bool:
    int64:
    string:
    uint64:
```

`var`定义变量、`const`定义常量

`:=`自动类型推断

`.(T)`：类型断言

#### string

字符串


#### pointers


指针

`&`、`*ptr`


#### array

`[]T`



#### slice


#### map

映射：`map[K]V`


#### goroutine

go携程


#### channel

go通道：`chan T`


### 流程控制
```yaml
:
    defer: # 延迟处理
    for ... range ...: # 迭代遍历
    go ...: # goroutine
    if ... else if ... else ...:
    loop ...:
        break:
        continue:
        goto:
    select ... case ...: # channel select
    switch ... case ... default ...:
        fallthrough:
```



### function

```golang
func myfunc() (int, string) {
    return ...
}
```





### Struct


```golang
type User struct {
    Name string
    Age int
}
```

结构体



#### method

方法
```golang
func (u *User) myMethod() {
    ...
}
```

#### interface





#### tag


#### reflect

反射

### module





### 并发


#### Context

多级Goroutine实现通信的一种工具，并发安全

Context上下文树


### 测试

`testing`






