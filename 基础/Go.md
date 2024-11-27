# Go

## 基础介绍

`package main`声明主模块

`gopath`go模块搜索路径 




### go
```yaml
go:
    build:
    clean:
    doc:
    env: # go环境变量
    fmt: # 格式化代码
    help:
    install:
    list: #
    mod: # 模块管理工具
        init: # 初始化模块
        tidy:
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
        float32:
        nil:
        rune: # int32字符
        slice:
        string:
        len():
        make():
        new():
        panic():
    bufio: # 输入缓冲
        Reader:
            ReadString():
        NewReader():
    fmt: # 格式化
        Printf():
        Println():
    os:
        Stdin: # 标准输入
    strconv: # 字符串转换
        ParseFloat():
    strings: # 字符串工具
        Trim():
    time: # 时间
        Date:
        Location:
        Month:
        Time:
            Format():
        Now(): 
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



#### string

字符串


#### pointers


指针

`&`、`*ptr`


#### array

`[]T`



#### slice





#### goroutine


### 流程控制
```yaml
:
    if ... else ...:
```



### function



### Struct




### module





### 并发










