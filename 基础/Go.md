# Go

`go官方文档：https://golang.google.cn/doc/`
`8小时转职Golang工程师: P26`


## 基础介绍

`package main`声明主模块（主运行模块）






`gopath`：go模块搜索路径

`GOPATH/pkg/mod` :存放下载的第三方包




### 安装目录
```yaml
安装目录:
    /api:
    /bin:
        go.exe: # go运行文件
        gofmt.exe:
    /doc:
    /lib:
    /misc:
    /pkg:
        /cache: # 第三方包安装缓存
        /include:
        /mod: # 第三方包安装目录 
        /sumdb:
        /tool:
            /windows_amd64:
                asm.exe:
                compile.exe:
                objdump.exe:
                pack.exe:
                pprof.exe:
    /src:
    /test: # go 测试用例
    go.env:
```




### go
```yaml
go:
    build:
    clean:
    doc:
    env: # go环境变量
        GO111MODULE:
        GOCACHE:
        GOENV:
        GOMODCACHE:
        GOPATH: # go项目默认路径（包路径）
        GOPROXY:
        GOROOT: # go安装根目录
        GOTOOLDIR: # go工具链目录
        GOVERSION:
        GOMOD:
        GOWORK:
    fmt: # 格式化代码
    get: # 下载包
    help:
    install: # 本地安装包（本地发布）
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


#### go.mod
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
        int:
        int64:
        map:
            Add():
            Set():
        nil: # 空值
        rune: # int32字符
        slice:
        string:
        append(): # slice追加元素
        cap(): # 数组容量
        close(): # 关闭chan
        delete(): # 删除键值对
        len(): # 数组长度
        make(): # 开辟内存（slice、）
        new():
        panic():
    archive:
        tar:
        zip:
    big:
        NewInt():
    bufio: # 输入缓冲
        Reader:
            ReadString():
        NewReader():
    bytes:
    cmp:
    compress:
        gzip:
        zlib:
    container:
        heap:
        list:
        ring:
    context:
        Context:
            Deadline():
            Done():
            Err():
            Value():
        Background():
            Value():
        TODO():
        WithCancel():
        WithTimeout():
        WithValue():
    crypto:
        aes:
        des:
        md5:
        rand:
    database:
        sql:
            driver:
            Db:
                SetMaxOpenConns():
    debug:
        buildinfo:
        elf:
        pe:
    encoding:
        base64:
        csv:
        hex:
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
        xml:
    errors:
        Is():
        New():
    fmt: # 格式化
        Printf():
            %T: # 数据类型
        Println(): # 打印换行
    go:
        ast:
        build:
        doc:
        format:
        parser:
        types:
    hash:
    html:
        template:
    image:
        color:
        draw:
        gif:
        jpeg:
        png:
    io:
        fs:
        ioutil: # io工具包
            ReadAll():
                ---
                bytes:
            ReadFile():
        Copy():
        CopyBuffer():
        WriteString(): # 写入字符串
            file:
            str:
            ---
            length:
    iter:
    log:
        Fatal():
    maps:
    math:
        rand:
            Intn():
            Seed():
    mime:
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
            StatusOK:
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
    path:
    plugin:
    reflect: # 反射
        Float32:
        Int32:
        Method: # 字段方法
            Name:
            Type:
            Call():
        rtype:
        StructField: # 字段结构
            Name:
            Tag:
                Get():
            Type:
            Interface(): # 字段值
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
    regexp:
    runtime:
    signal: # 信号
        Notify(): # 监听信号（配合chan）
    slices:
    sort:
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
    structs:
    sync:
        atomic:
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
    syscall:
    testing:
        T:
    text:
    time: # 时间
        Date:
        Location:
        Millisecond:
        Month:
        Time: # 时间
            Format():
        After():
        Now(): # 当前时间
        Sleep(): # 进程睡眠
    unsafe:
x:
    crypto:
        bcrypt:
```




### 数据类型
```yaml
types:
    bool:
    fload64:
    int:
    int64:
    nil:
    string:
    uint64:
```

`var`定义变量、`const`定义常量

`:=`自动类型推断声明（不能声明全局变量）

`.(T)`：类型断言

`const itoa`：定义常量枚举（0开始）







#### string

字符串


#### pointers


指针

`&`、`*ptr`






#### array

`[]T`

值传递

#### slice

切片、动态数组

引用传递

默认长度、容量为0，没有开辟空间

切片截取：左闭右开


#### map

映射：`map[K]V`

引用传递

默认长度、容量为0，没有开辟空间(nil)


#### goroutine

go携程


#### channel

go通道：`chan T`


### 流程控制
```yaml
:
    defer: # 延迟处理（在return之后）
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

值传递



#### method

方法
```golang
func (u *User) myMethod() {
    ...
}
```

#### extends

通过匿名字段组合实现继承




#### interface
```go
type Animal interface {
    myFunc() string
}
```


用于实现多态

隐式接口实现

接口没有实体、用指针接收
接口指针持有真实类型的引用


万能接口：`interface{}`



#### tag




#### reflect

反射

Type、Value








### module

公共访问：首字母大写

`init()`：包初始化函数



### 并发


#### Context

多级Goroutine实现通信的一种工具，并发安全

Context上下文树


### 测试

`testing`






