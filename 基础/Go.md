# Go

`go官方文档：https://golang.google.cn/doc/`
``


## 基础介绍

`package main`声明主模块（主运行模块）






`GOPATH`：go模块搜索路径

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
        -tags:
    clean:
    doc:
    env: # go环境变量
        -w: # 修改环境变量
        GO111MODULE: # 模块功能go.mod
        GOCACHE:
        GOENV:
        GOMODCACHE:
        GOPATH: # go项目默认路径（包路径）
        GOPROXY: # Go模块代理
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
        download: # 下载依赖
        edit: # 编辑go.mod
            -replace:
        graph: # 查看依赖结构
        init: # 初始化模块
        tidy: # 清理依赖
        vendor: # 导出所有依赖到vendor目录
        verify: # 校验模块
        why:
    run: # 运行
    test: # 运行测试用例
    tool: # go工具链
    version: # go版本

```

go命令行


#### go.mod
```yaml
go.mod:
    go: # 指定go版本
    module: # 模块声明
    replace: # 项目包依赖替换
    require: # 项目依赖包
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
        make(): # 开辟内存（slice、map、channel）（返回引用）
        new(): # 开辟内存（返回指针）
        panic(): # 抛出异常
        print(): # 控制台输出
        recover():
    archive:
        tar:
        zip:
    bufio: # 输入缓冲
        Reader:
            Read():
            ReadLine():
            ReadString():
            Reset():
            UnreadByte():
        ReadWriter:
        Scanner:
            Err():
            Scan():
            Split():
            Text():
        ScanBytes:
        ScanRunes:
        ScanWords:
        SplitFunc:
        Writer:
            Available():
            Buffered():
            Flush():
            ReadFrom():
            Reset():
            Write():
            WriteString():
        NewReader():
        NewWriter():
        Peek(): 
    bytes: # 字节切片
        Buffer:
            Bytes():
            Len():
            NextA():
            Read():
            ReadByte():
            ReadBytes():
            ReadFrom():
            ReadString():
            Reset():
            String():
            Write():
            WriteByte():
            WriteRune():
            WriteString():
            WriteTo():
        Reader:
            Len():
            Read():
            ReadAt():
            ReadByte():
            Seek():
            Size():
        Compare():
        Contains():
        ContainsRune():
        Count():
        Equal():
        Fields(): # 同Split
        Index():
        IndexFunc():
        Join():
        Map():
        NewBuffer():
        NewBufferString():
        NewReader():
        Repeat():
        Replace():
        Runes():
        Split():
        ToUpper():
        Trim():
        TrimFunc():
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
            Done(): # 上下文结束channel
            Err():
            Value():
        Background():
            Value():
        TODO():
        WithCancel(): # 上下文结束函数
        WithDeadline():
        WithTimeout():
        WithValue(): # 设置context kv
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
            Named(): # sql具名参数
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
        error:
            Error():
        Is():
        New(): # 新建错误
    flag: # 命令行解析
        Args*(L)
        Int():
        IntVar():
        NArg():
        NFlag():
        Parse(): # 参数解析
        String():
        StringVar(): # 参数绑定
    fmt: # 格式化
        Errorf(): # 异常格式化
        Fprint(): # 文件内容写入
        Fprintf():
        Fprintln():
        Fscan():
        Fscanf():
        Fscanln():
        Print():
        Printf():
            %b: # 二进制
            %d: # 十进制数字
            %e: # 科学计数法
            %f: # 浮点数
            %s: # 字符串
            %t: # 布尔字面量
            %v: # 输出值
                %+v: # 结构体输出字段
                %#v: # 结构体带包名输出字段
            %x: # 十六进制
            %T: # 数据类型
                width.precision: # 宽度.精度
                -: # 左对齐
                0: # 0填充
        Println(): # 打印换行
        Scan():
        Scanf():
        Scanln(): # 输入一行
        Sprint():
        Sprintf(): # 格式化字符串
        Sprintln():
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
        Closer:
            Close():
        EOF:
        LimitedReader:
            N:
            R:
        PipeReader:
        Reader:
            Read():
        ReaderFrom():
            ReadFrom():
        ReadWriter:
            Reader:
            Writer:
        SectionReader:
            Size():
        Seeker:
            Seek():
        Writer:
            Write():
        Copy(): # 复制
        CopyBuffer():
        CopyN():
        LimitReader():
        MultiReader():
        MultiWriter():
        NewSectionReader():
        Pipe():
        ReadAll():
        ReadAtLeast():
        ReadFull():
        WriteString(): # 写入字符串
            file:
            str:
            ---
            length:
    ioutil:
        NopCloser():
        ReadAll():
        ReadDir():
        ReadFile():
        TempDir():
        TempFile():
        WriteFile():
    iter:
    log: # 日志
        Logger:
            Fatal():
            Panic():
            Print():
        Fatal():
        Flags(): # 日志配置
        New(): # 新建日志器
        Panic():
        Prefix(): # 日志信息前缀
        Print():
        Printf():
        Println():
        SetFlags():
        SetOutput(): # 设置日志输出
        SetPrefix():
    maps:
    math:
        big:
        complx:
        rand:
            Int():
            Intn():
            Seed():
        MaxInt32:
        Pi:
        Abs():
        Cbrt():
        Ceil():
        Dim():
        Floor():
        IsNaN():
        Max():
        Min():
        Mod():
        Pow():
        Sqrt():
        Trunc():
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
        mail:
        netip:
        rpc:
        smtp:
        textproto:
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
        Conn:
            Close():
            Read():
            RemoteAddr():
            Write():
        Listener:
            Accept():
            Close():
        Dial(): # socket连接
        Listen(): # socket监听
    os:
        exec:
        signal:
        user:
        Args: # 命令行参数
        DirEntry:
        File: # 文件对象
            Close(): # 关闭文件
            Read():
            ReadAt():
            Seek():
            Stat(): # 文件信息
            Write():
            WriteAt():
            WriteString():
        FileInfo: # 文件信息对象
            IsDir():
            Mode():
            ModTime():
            Name():
            Size():
            Sys():
        Interrupt:
        Kill: # 进程结束信号
        PathError:
        ProcAttr: # 进程属性
            Env:
            Files:
        Process: # 进程对象
            Pid:
            Signal(): # 进程发送信号
            Wait(): # 进程等待（阻塞当前进程）
        O_APPEND:
        O_CREATE:
        O_RDWR:
        O_TRUNC:
        O_WRONLY:
        Signal:
        Stdin: # 标准输入
        Stdout: # 标准输出
        Chdir(): # 修改工作目录
        Chmod():
        Chown():
        Clearenv(): # 清空环境变量
        Create(): # 创建文件File
        Environ(): # 获取所有环境变量
        Executable(): # 获取可执行文件路径
        Exit(): # 进程结束
        FileMode(): # 文件权限
        FindProcess(): 
        Getenv(): # 获取环境变量
        Getgid():
        Getpid(): # 获取进程id
        Getppid():
        Getuid():
        Getwd(): # 获取当前工作目录
        Hostname(): # 主机名
        Mkdir(): # 创建单个目录
        MkdirAll():
        Open(): # 打开文件
        OpenFile():
        ReadDir(): # 读取目录
        Remove():
        RemoveAll():
        Rename():
        Setenv(): # 设置环境变量
        StartProcess(): # 开启子进程
        TempDir():
    path:
        filepath:
            Abs(): # 获取绝对路径
            Join(): # 路径合并
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
        syntax:
    runtime:
        cgo:
        coverage:
        debug:
        metrics:
        pprof:
        race:
        trace:
        Goexit(): # 退出goroutine
        GOMAXPROCS():
        Gosched(): # 让出时间片
        NumCPU():
    signal: # 信号
        Notify(): # 信号监听（配合chan）
    slices:
    sort:
        Interface:
            Len():
            Less():
            Swap():
        StringSlice:
        Float64s():
        Ints():
        IsSorted():
        Reverse():
        Search(): # 查找
        SearchInts():
        Sort():
        Strings():
    strconv: # 字符串转换
        Itoa():
        ParseFloat():
    strings: # 字符串工具
        Builder:
            String():
            Write(): # 写入
        Reader:
        NewReader(): # 生成Reader
        Trim():
    structs:
    sync:
        atomic:
        Mutex: # 互斥锁
            Lock():
            Unlock():
        RWMutex: # 读写锁
            RLock():
            RUnlock():
        WaitGroup: # 等待计数
            Add(): # 计数+1
            Done(): # 计数-1
            Wait(): # 等待
    syscall: # 系统调用
        js:
        SIGINT:
        SIGKILL:
    testing: # 测试
        fstest:
        iotest:
        quick:
        slogtest:
        T:
    text:
        scanner:
        tabwriter:
        template:
            parse:
    time: # 时间
        Date: # 日期
        Duration: # 时间间隔
        Location: # 时区
        Millisecond:
        Month:
        Second: # 秒
        Time: # 时间
            Add():
            After():
            Before():
            Equal():
            Format(): # 时间字符串格式化
            Sub():
            Unix():
            Year():
        AfterFunc(): # 延迟执行
        LoadLocation(): # 
        NewTicker():
        NewTimer():
        Now(): # 当前时间
        Parse(): # 时间字符串解析(Time): 2006-01-02 15:04:05
        ParseInLocation():
        Sleep(): # 进程睡眠
        Tick(): # 定时器(chan)
        Unix():
    unique:
    unsafe:
```




### 数据类型
```yaml
types:
    bool:
    byte: # 字节
    fload64: # 浮点数默认
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


#### channel

- `chan T`
- `chan`
- `chan`

go通道：`chan T`

go协程通信

通道默认无缓存

for...range.. 遍历channel
select 多路复用channel


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
        fallthrough: # 默认不穿透
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

package定义包、主执行包`main`

公共访问：首字母大写

`init()`：包初始化函数



### 并发

#### Goroutine

go协程

main主协程退出，程序结束运行

#### GMP

- G：协程
- P：协程调度器（本地队列、全局队列）
- M：线程



#### Context

多级Goroutine实现通信的一种工具，并发安全

Context上下文树


### Test

`testing`

`_test.go`测试文件、大驼峰命名测试函数`testing.T`






