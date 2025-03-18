# Go

`go官方文档：https://golang.google.cn/doc/`
`Go by Example文档：https://gobyexample.com/multiple-return-values`


## 基础介绍

无需分号结束`;`
`package main`声明主模块（主运行模块）




`GOPROXY`: 模块代理
`GOMODCACHE`: 第三方模块安装

`GOPATH`: go模块搜索路径
`GOPATH/pkg/mod`: 存放下载的第三方包

mingw安装：`https://sourceforge.net/projects/mingw/`


核心io.Reader、io.Writer实现
- bytes.Reader/Writer
- Strings.Reader/Writer
- os.File
- net.Conn
- bufio.Reader/Writer


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
    benchmark:
    build: # 构建
        -tags:
    clean:
    doc:
    env: # go环境变量
        -w: # 修改环境变量
        GO111MODULE: # 模块功能go.mod
        GOCACHE:
        GOENV:
        GOMODCACHE: # 模块安装路径
        GOPATH: # go项目默认路径（包路径）
        GOPROXY: # Go模块代理
        GOROOT: # go安装根目录
        GOTOOLDIR: # go工具链目录
        GOVERSION:
        GOMOD:
        GOWORK:
    fmt: # 格式化代码
    get: # 下载、更新包
        -u: # 更新包
    help: # 帮助命令
    install: # 本地安装包（本地发布）
    list: # 列出所有模块
    mod: # 模块管理工具
        download: # 下载所有依赖
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
        -bench: # 基准测试
        -count:
        -cover: # 测试覆盖率
        -coverprofile:
        -failfast:
        -parallel:
        -run: # 运行指定测试
        -tags: # 运行指定测试
        -v: # 详细信息
    tool: # go工具链
        asm:
        compilie:
        cover: # 查看基准测试报告
        link:
        nm:
        objdump:
        pack:
        pprof:  
        trace:
        vet:
    version: # go版本
```

go命令行


#### go.mod
```yaml
go.mod:
    go: # 指定go版本
    module: # 模块声明
    replace: # 项目包依赖替换，常用于引入本地依赖
    require: # 项目依赖包
```

模块配置文件




## 核心内容
```yaml
std:
    archive:
        tar:
        zip:
    bufio: # 输入、输出缓冲
        Reader: # 输入缓冲区
            Read():
            ReadLine(): # 读取整行
            ReadString(): # 读取整行，推荐（包含回车\n）
            Reset():
            UnreadByte():
        ReadWriter: # 输出缓冲区
        Scanner: # 输入扫描
            Err():
            Scan(): # 循环扫描
            Split():
            Text(): # 输入的文档
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
        NewScanner():
        NewReader(): # 新建输入缓冲区
        NewWriter():
        Peek(): 
    builtin: # 内置模块
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
        copy(): # 值拷贝、切片拷贝
        delete(): # 删除map键值对
        len(): # 数组长度、字符串长度
        make(): # 开辟内存（slice、map、channel）（返回引用）
        new(): # 开辟内存（返回指针）
        panic(): # 抛出异常
        print(): # 控制台输出
        recover(): # 错误恢复
    bytes: # 字节切片
        Buffer: # 字节缓存流
            Bytes():
            Len():
            NextA():
            Read():
            ReadByte():
            ReadBytes():
            ReadFrom():
            ReadString():
            Reset():
            String(): # 缓冲区内字节数据转字符串
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
        bzip2:
        gzip:
        zlib:
    container: # 容器
        heap: # 堆
        list: # 双向链表
            Element: # 联表节点
                Next():
                Prev():
            List: # 双向链表
                Back():
                Front():
                InsertAfter():
                InsertBefore():
                Len():
                Remove():
            New():
        ring: # 环形链表
    context: # 上下文管理
        Context:
            Deadline():
            Done(): # 上下文结束channel，<-chan struct{}
            Err():
            Value():
        Background():
            Value():
        TODO():
        WithCancel(): # 带结束 上下文
        WithDeadline(): # 超时结束 上下文
        WithTimeout(): # 超时关闭duration 上下文
        WithValue(): # 设置context kv
    crypto: # 加密
        aes: # 高效对称加密
            NewCipher():
        cipher:
        des:
        hmac:
            New():
        md5:
            Sum(): # 计算md5哈希，返回字节数组
        rand:
        rsa: # 公私钥加密
        sha512:
            Sum256():
    database: # 数据库
        sql:
            Conn:
            Db: # 数据库连接
                Close():
                Exec(): # 执行sql，返回Result
                Query(): # 执行查询sql，返回Rows
                QueryRow():
                SetMaxOpenConns():
            Driver:
            Result: # ddl操作结果
                LastInsertId():
                RowsAffected():
            Rows: # sql查询结果
                Close():
                Err(): # 异常
                Next(): # 结果迭代
                Scan(): # 值扫描输入
            Tx:
            Named(): # sql具名参数
            Open(): # 打开数据库连接
            Register(): # 注册数据库驱动
    debug:
        buildinfo:
        elf:
        pe:
    embed:
    encoding: # 编解码
        base64: # Base64
            StdEncoding:
                EncodeToString():
        binary:
        csv:
        hex: # 十六进制
            EncodeToString(): # 字节数据解码成十六进制字符串
        json: # JSON
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
    errors: # 异常
        error: # 异常基类
            Error():
        Is(): # 异常类型判断
        New(): # 新建错误
    expvar:
    flag: # 命令行解析
        FlagSet:
        Args():
        Int():
        IntVar():
        NArg():
        NFlag():
        Parse(): # 命令行解析
        String(): # 定义参数
        StringVar(): # 参数绑定
        Var():
    fmt: # 格式化
        Errorf(): # 异常格式化
        Fprint(): # 文件内容写入
        Fprintf():
        Fprintln():
        Fscan():
        Fscanf():
        Fscanln():
        Print():
        Printf(): # 格式化输出
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
        Scanf(): # 格式化输入
        Scanln(): # 输入一行
        Sprint():
        Sprintf(): # 字符串格式化
        Sprintln():
    go:
        ast:
        build:
        doc:
        format:
        parser:
        types:
    hash:
        crc64:
        Hash: # 哈希
            Sum():
    html:
        template: # html模板引擎
            Template: # HTML模板
                Execute(): # 传递模板数据，并执行解析
                ExecuteTemplate(): # 模板渲染输出
                Parse(): # 解析字符串
                ParseFiles(): # 解析文件
                ParseGlob():
            New(): # 新建模板
        EscapeString(): # 转义 HTML
        UnescapeString(): # 反转义 HTML
    image:
        color:
        draw:
        gif:
        jpeg:
        png:
    index:
    io: # 输入、输出
        fs:
        ioutil: # （过时）io工具包
            ReadAll():
                ---
                bytes:
            ReadDir(): # 获取文件夹下所有文件名
            ReadFile(): # 文件读取
            NopCloser():
            TempDir():
            TempFile():
            WriteFile(): # 文件写入
        Closer:
            Close():
        EOF: # 读取结束异常符
        LimitedReader:
            N:
            R:
        PipeReader: # 管道输入器
        PipeWriter: # 管道写出器
        Reader: # 读取器接口（字节）
            Read():
        ReaderAt: # 随机读取器接口
        ReaderFrom():
            ReadFrom():
        ReadWriter:
            Reader:
            Writer:
        SectionReader:
            Size():
        Seeker:
            Seek():
        Writer: # 写入器接口（字节）
            Write():
        Copy(): # 流数据拷贝
        CopyBuffer():
        CopyN():
        LimitReader():
        MultiReader():
        MultiWriter():
        NewSectionReader():
        Pipe(): # 创建输入输出管道
        ReadAll():
        ReadAtLeast():
        ReadFull():
        WriteString(): # 写入字符串
            length:
    iter:
    log: # 日志
        Logger: # 日志器
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
    maps: # 映射工具包
        Clone(): # 拷贝
        Delete(): # 删除key
        Equal(): # 内部元素相等判断
        Keys(): # 获取所有key
        Merge(): # 合并map
        Map(): # 映射转换
        Values(): # 获取所有value
    math: # 数学
        big:
        complx:
        rand: # 随机数
            Int():
            Int31():
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
    mime: # 多媒体类型
        multipart:
        ParseMediaType(): # 返回字符串
        TypeByExtension():
    net: # 网络
        http: # HTTP
            Client: # 请求客户端
                Timeout:
                Do(): # 发起请求Request
            Request: # 请求对象
                Body:
                Header:
            Response: # 响应对象
                Body: # 响应体
                    Close():
                ContentLength:
                Status:
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
            NewRequest(): # 新建请求
            Post():
            PostForm():
        mail:
        netip:
        rpc:
        smtp:
        textproto:
        url: # URL
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
        Conn: # 连接对象
            Close(): # 关闭连接
            Read(): # 读取字节数据
            RemoteAddr():
            Write(): # 写入字节数据
        Listener:
            Accept(): # 接收socket连接
            Close(): # 关闭连接
        UDPAddr:
            IP:
            Port:
            Zone:
        UDPConn: # UDP连接
            Close():
            ReadFromUDP():
            WriteToUDP():
        Dial(): # TCP请求连接
        DialUDP(): # UDP请求连接
        Listen(): # 端口监听
        ListenUDP(): # 端口监听
    os: # 操作系统相关
        exec: # 命令行
            Command: # 命令类
                Stdin: # 命令输入
                CombinedOutput(): # 命令的标准输出和标准错误输出的合并内容
                Output(): # 获取命令输出
                Run():
                Start():
                StdoutPipe(): # 输出管道
                Wait():
        signal:
        user:
        Args: # 命令行参数
        DirEntry: # 文件条目
            IsDir(): # 判断是否是目录
            Name(): # 文件名
        File: # 文件流对象
            Close(): # 关闭文件
            Read():
            ReadAt():
            ReadDir(): # 读取所有文件条目 os.DirEntry
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
        Signal: # 进程信号
        Stdin: # 标准输入
        Stdout: # 标准输出
        O_APPEND:
        O_CREATE:
        O_RDWR:
        O_TRUNC:
        O_WRONLY:
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
        Getenv(): # 获取系统环境变量
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
        ReadDir(): # 获取所有文件条目
        ReadFile(): # 获取文件内容、字节数据
        Remove(): # 删除文件
        RemoveAll(): # 删除所有文件
        Rename():
        Setenv(): # 设置环境变量
        StartProcess(): # 开启子进程
        TempDir():
    path: # 文件路径，适用于Unix风格路径
        filepath: # 适用于文件系统路径，可以在 Windows 和 Linux 上正确处理路径分隔符
            Abs(): # 获取绝对路径
            Base(): # 获取文件名
            Dir(): # 获取目录名
            Ext(): # 获取文件后缀
            IsAbs(): # 是否绝对亮晶晶
            Join(): # 路径合并
            WalkDir(): # 文件遍历（深度遍历）
    plugin:
    reflect: # 反射
        rtype:
        Float32:
        Int32:
        Method: # 字段方法
            Name:
            Type:
            Call(): # 调用方法，需要Value作为参数
        StructField: # 字段结构
            Name: # 字段名称
            Tag: # 字段标签
                Get():
            Type:
            Interface(): # 字段值
        StructTag: # tag标签
        Type: # 类型
            Elem(): #  获取类型指针所指向的元素类型
            Field(): # 根据index获取字段
            FieldByName(): # 根据名称查找字段
            Implements(): # 判断接口实现
            Kind(): # 类型种类
            Method(): # 根据index获取方法
            MethodByName():
            Name(): # 类型名
            NumField(): # 字段个数
            NumMethod():
        Value: # 值，常传指针
            Elem(): # 根据指针取值、解引用
                SetBool():
                SetInt():
                SetString():
            FieldByName():
            Float():
            Int():
            IsNil():
            Kind(): # 变量类型
            MapIndex():
            MethodByName():
            NumField(): # 字段个数
            SetInt():
        TypeOf(): # 获取变量类型Type
        ValueOf(): # 获取变量值Value
    regexp: # 正则表达式(查找、替换、分隔)（索引、字符串、匹配组）
        syntax:
        Regexp: # 正则表达式对象
            Find():
            FindAll(): 
            FindAllString(): # 查找所有字符串
            FindAllStringIndex(): # 
            FindIndex():
            FindString(): # 查找
            FindStringSubmatch(): # 获取子匹配组
            FindStringSubmatchIndex():
            Match():
            MatchString(): # 匹配
            ReplaceAllString():
            ReplaceAllStringFunc():
            Split(): # 分隔
            String():
        Compile(): # 编译
        MatchString(): # 正则匹配
        MustCompile():
    runtime: # 系统运行时
        cgo:
        coverage:
        debug:
        metrics:
        pprof:
        race:
        trace:
        Caller(): # 获取当前函数调用栈信息（程序计数器(函数名)、文件名、行号）
        Goexit(): # 退出goroutine
        GOMAXPROCS(): # 调整 CPU 并发
        Gosched(): # 让出CPU时间片、非阻塞
        NumCPU():
    signal: # 信号
        Notify(): # 通道设置信号监听（配合chan）
    slices: # 切片
        Clone():
        Contains(): # 值包含判断
        Copy(): # 切片拷贝
        Equal(): # 切片内部值比较
        Filter(): # 序列过滤
        Index(): # 查找元素索引
        IndexAny():
        IndexFunc():
        Map(): # 序列转换
        Remove(): # 删除元素索引
        Replace(): # 替换元素
        Reverse():
        Sort(): # 排序
        SortFunc(): # 自定义排序
        Unique(): # 序列去重
    sort: # 排序
        Interface: # 自定义排序接口
            Len(): # 长度
            Less(): # 小于定义
            Swap(): # 元素交换
        StringSlice:
        Float64s():
        Ints(): # 整数切片排序
        IsSorted():
        Reverse():
        Search(): # 查找
        SearchInts():
        Slice(): # 切片排序
        Sort():
        Strings(): # 字符串切片排序
    strconv: # 字符串转换
        Itoa():
        ParseFloat(): # 转换浮点型数据
    strings: # 字符串
        Builder:
            String():
            Write(): # 写入
        Reader: # 字符输入流
        NewReader(): # 生成Reader
        Contains(): # 字符串包含
        HasPrefix():
        HasSuffix():
        Index(): # 字符串索引
        LastIndex(): # 倒序索引
        NewReader():
        Replace(): # 字符串替换
        ReplaceAll():
        Split(): # 字符串分隔
        SplitAfter():
        SplitN():
        Title():
        ToUpper():
        Trim():
        TrimSpace():
    structs:
    sync: # 同步
        atomic: # 原子操作
            AddInt64():
            CompareAndSwapInt64():
            LoadInt64():
            StoreInt64():
        Cond: # 条件变量，依赖锁机制
            L: # 持有锁
            Broadcast(): # 唤醒所有
            Signal(): # 随机唤醒一个等待的goroutine
            Wait(): # 等待唤醒，释放锁，被唤醒后直接持有锁
        Map: # 并发安全Map
            Delete():
            Load():
            Range(): # k-v 遍历
            Store():
        Mutex: # 互斥锁
            Lock():
            Unlock():
        Once: # 执行一次
            Do(): # 多个协程，只允许执行某函数一次
        Pool(): # 对象复用池
            New: # 自定义池对象创建
            Get(): # 获取池中对象
            Put(): # 归还池中对象
        RWMutex: # 读写锁，允许同时多读
            Lock(): # 写锁
            RLock():
            RUnlock():
            Unlock():
        WaitGroup: # 等待计数
            Add(): # 计数+1，开启协程时+1
            Done(): # 计数-1，协程结束时-1
            Wait(): # 等待归0
        NewCond(): # 新建条件变量，传入锁
    syscall: # 系统调用
        js:
        SIGINT:
        SIGKILL:
    testing: # 测试
        fstest:
        iotest:
        quick:
        slogtest:
        T: # 结果记录
            Errorf():
            Fatal():
            Log():
            Parallel(): # 并行测试
            Run(): # 运行子测试
            Skip(): # 跳过测试
    text:
        scanner:
        template: # 内置模板引擎 
            New():
                Execute(): # 模板上下文数据传递
                Parse(): # 模板解析
        tabwriter:
            parse():
    time: # 时间
        Date: # 日期
        Duration: # 时间间隔
        Location: # 时区
        Millisecond: # 毫秒
        Month:
        Second: # 秒
        Time: # 时间
            Add():
            After():
            Before():
            Equal():
            Format(): # 时间字符串格式化 2006-01-02 15:04:05
            String(): # 
            Sub():
            Unix(): # 时间戳 秒
            UnixMilli(): # 时间戳 毫秒
            Year():
        After(): # 延时执行 channel
        AfterFunc(): # 延迟执行
        LoadLocation(): # 
        NewTicker():
        NewTimer():
        Now(): # 当前时间
        Parse(): # 日期时间解析(Time): 2006-01-02 15:04:05
        ParseInLocation():
        Sleep(): # 线程睡眠
        Tick(): # 定时器执行 channel
        Unix():
    unique:
    unsafe: # 不安全操作，底层操作
        Sizeof(): # 获取变量内存大小
    weak:
```




### Data Types
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
`.(T)`：类型断言，常用于类型判断
`const itoa`：定义常量枚举（0开始）







#### String
```go
// 字符串声明
var str string = "xxxx"

// 多行字符串
str := `This is a multi-line
It can span multiple lines.`

// 字符串长度
str_len := len(str)

// 转换为字节切片
byteArr := []byte(str)
```

字符串

值传递、不可变
支持加号`+`拼接


#### Pointers
```go
// 声明一个 int 类型的变量
var a int = 58

// 获取变量 a 的指针
var p *int = &a

// 通过指针 p 访问 a 的值（解引用）
fmt.Println(*p) // 输出: 58
```


指针`&`、`*T`、值传递

`nil`空指针




#### Array
```go
// 数组声明、默认值为0
var arr [5]int

// 初始化器声明
arr := [3]int{1, 2, 3}

// 省略长度初始化声明
arr := [...]int{1, 2, 3, 4}
```

`[n]T`

固定长度数组、值传递
对于数组、长度和容量是一样的





#### Slice
```go
// 切片声明
slice := []int{1, 2, 3}

// make创建、动态内存分配
slice := make([]int, 3)

// 添加元素（底层扩容）
 slice = append(slice, 4, 5)
```

切片、动态数组、引用传递
长度、容量

默认长度、容量为0，没有开辟空间
切片截取：左闭右开

使用切片语法进行元素删除操作
支持元素解构...



#### Map
```go
// 字面量声明
m := map[string]int{
    "age":   30,
    "score": 90,
}

// make动态创建
m := make(map[string]int)

// key存在判断
value, exists := m["age"]

// delete()删除key
```

映射：`map[K]V`

引用传递

默认长度、容量为0，没有开辟空间(nil)


#### Channel
```go
// 创建无缓冲通道
ch := make(chan string)

// 启动一个新的 goroutine 发送数据
go func() {
    ch <- "Hello, Go!"
}()

// 从通道接收数据
msg := <-ch


// 创建一个缓冲区大小为 2 的通道
ch := make(chan string, 2)

// 关闭channel、关闭后的通道不能再发送数据，但仍然可以接收数据直到通道为空
close(ch)

// select多路复用
select {
case msg1 := <-ch1:
    fmt.Println(msg1)
case msg2 := <-ch2:
    fmt.Println(msg2)
default:
    fmt.Println("No message received") // 输出: No message received
}
```

- `chan T`: 双向通道
- `chan<- T`: 单向发送通道
- `<-chan T`: 单向接收通道

go通道：`chan T`、引用传递

go协程通信、通道默认无缓存

for...range.. 遍历channel
select 多路复用channel


### Control Flow
```yaml
Control Flow:
    :=: # 初始化声明语句
    const: # 常量声明
    nil: # 空值
    var: # 变量声明
    defer ...: # 延迟处理（在return之后）
    for: # 普通for循环，支持while、死循环实现
    for ... range ...: # 迭代遍历、带索引
    go ...: # goroutine
    if ... else if ... else ...:
    loop ...:
        break:
        continue:
        goto:
    select ... case ...: # channel通道多路复用
    switch ... case ... default ...:
        fallthrough: # 默认不穿透
```


#### Exception Handler
```go
func divide(a, b int) (int, error) {
    if b == 0 {
        // 返回一个错误
        return 0, errors.New("division by zero")
    }
    return a / b, nil
}
```

通过函数的返回值来处理、约定最后一个返回值
`panic()`、`recovery()`
recovery常配合defer处理



#### Select
```go
// select超时控制
select {
case msg := <-ch:
    fmt.Println("收到消息：", msg)
case <-time.After(2 * time.Second):
    fmt.Println("超时了，没有收到数据")
}
```

- select会随机选择一个可执行的case进行执行
- 如果多个case都可执行，Go运行时会随机选择一个
- 如果所有case都不可用，则：
    - 如果有default，执行default，然后立即继续执行后续代码（非阻塞 elect）
    - 如果没有default，则select会阻塞，直到某个case可用


使用场景：
- 多个通道的处理
- 超时控制


select需结合break标签才能跳出外层循环



#### Template
```yaml
html/template:
    {{ xxx }}: # 变量使用
        template:
        define ... end:
```
- text/template
- html/template

内置页面模板引擎









### Function
```golang
// 函数声明
func greet(name string) string {
    return "Hello, " + name
}

// 返回值命名、优化多返回值
func divide(a, b float64) (quotient float64, err error) {
    if b == 0 {
        err = fmt.Errorf("division by zero")
        return
    }
    quotient = a / b
    return
}
```


- 支持多返回值、返回值命名
- 匿名函数、闭包
- 可变参数`...T`


#### Defer

延迟执行函数

#### Generics
```go
// 泛型函数声明
func Print[T any](value T) {
	fmt.Println(value)
}
```
泛型函数

支持泛型参数约束、


### Struct
```go
// 结构体声明
type Person struct {
    Name string
    Age int
}

// 结构体初始化声明
p := Person{"Alice", 25}

// 命名初始化
p := Person{Name: "Alice", Age: 25}

// new创建指针
p := new(Person)
```

结构体、值传递



#### Method
```golang
func (u *Person) myMethod() {
    ...
}
```

方法

指针接收者：
- 方法可以修改结构体的字段
- 避免结构体的复制开销

值接收者：常用于类似toString一类，不需要修改结构体字段的方法中
- 方法会接收到结构体的一个副本
- 不能修改结构体的字段、因为它操作的是结构体的副本




#### Extends
```go
// 父类定义
type Animal struct {
    Name string
}

// 父类方法
func (a Animal) Speak() {
    fmt.Println(a.Name, "makes a sound")
}

// 子类定义
type Dog struct {
    Animal // 继承 Animal
    Breed  string
}

// 子类手动初始化父类，可直接调用父类方法
d := Dog{Animal: Animal{Name: "Buddy"}, Breed: "Labrador"}
d.Speak()
```

默认没有继承、只有组合
通过匿名字段组合实现继承




#### Interface
```go
// 接口声明
type Animal interface {
    myFunc() string
}

// 泛型接口
type Stringer[T any] interface {
	ToString() string
}
```

用于实现多态、隐式接口实现

接口没有实体、用指针接收
接口指针持有真实类型的引用


万能接口：`interface{}`



#### Tag




#### Reflect

反射、Type、Value
- Type:  Go 变量的类型
- Value: Go 变量的值

reflect.Value必须是指针(pointer)，否则无法修改变量，需要调用Elem()取值后修改
reflect.TypeOf(p) 获取的是 *Person 类型，通过 Elem() 获取的是 Person 类型

Type与Value:
- 使用 reflect.Type
    - 只需要检查变量类型，比如 int、struct、map 等。
    - 获取结构体字段名、方法。
- 使用 reflect.Value
    - 需要读取变量的值，比如 v.Int()、v.String()。
    - 需要修改变量的值（必须传指针）。
    - 需要调用方法 v.MethodByName("SayHello").Call(nil)。


#### Generics
```go
// 泛型结构体声明
type Container[T any] struct {
	value T
}

// 泛型方法
func (c *Container[T]) Get() T {
	return c.value
}

// 使用
c := Container[int]{value: 42}
fmt.Println(c.Get()) // 42

```

泛型结构体

`~`: 匹配类型及其别名
`|`: 联合类型



### Module

包、模块

package定义包、主执行包`main`
每个目录只能包含一个包（package）

公共访问：首字母大写

##### init()

`init()`：包初始化函数
常用于数据库驱动注册



### Concurrent

#### GMP

- G：协程
- P：协程调度器（本地队列、全局队列）
- M：线程


#### Goroutine
```go
// 匿名函数启动Goroutine
go func() {
    fmt.Println("Hello from Goroutine!")
}()
```

go协程
- context实现协程管理(关闭)
- sync实现同步
- channel实现通信

Go 运行时会自动调度 Goroutine 到多个线程上运行。默认情况下，它会使用 CPU 核心数 作为最大并行度
main主协程退出，程序结束运行




#### Context
- Background()：根context，一般用作顶层context
- TODO()
- WithCancel(parent)
- WithTimeout(parent, duration)
- WithDeadline(parent, time.Time)
- WithValue(parent, key, value)

多级Goroutine实现通信的一种工具，并发安全
Context上下文树
用于控制Goroutine取消、超时和携带请求范围值

#### Mutex

互斥锁

加锁前的逻辑判断、加锁后要再判断一次


#### WaitGroup

等待计数


#### Cond
```go
var (
	mutex = sync.Mutex{}
	condP = sync.NewCond(&mutex)
	condC = sync.NewCond(&mutex)
	queue = make([]int, 0)
)

// 消费者
func consumer(i int) {
	for {
        mutex.Lock()
        // 空队列，等待唤醒
        for len(queue) == 0 {
            condC.Wait()
        }

        // 消费一条
        fmt.Printf("%d 消费 %d\n", i, queue[0])
        queue = queue[1:]
        time.Sleep(time.Millisecond * 100)

        // 唤醒生产者
        condP.Broadcast()
        mutex.Unlock()
	}
}

// 生产者
func producer(i int) {
	for {
        mutex.Lock()
        // 满队列，等待唤醒
        for len(queue) == 5 {
            condP.Wait()
        }

        // 生产一条
        rn := rand.Intn(10)
        fmt.Printf("%d 生产 %d\n", i, rn)
        queue = append(queue, rn)
        time.Sleep(time.Millisecond * 100)

        // 唤醒消费者
        condC.Broadcast()
        mutex.Unlock()
	}
}

func main() {
	for i := 1; i <= 5; i++ {
		go producer(i)
	}
	for i := 6; i <= 10; i++ {
		go consumer(i)
	}
	time.Sleep(time.Minute * 2)
}
```

条件变量、等待唤醒、依赖持有锁(同意把)保证同步性、一致性
用于线程（Goroutine）间的同步和协调，适用于生产者-消费者模型或等待某个条件满足的场景。Cond依赖于互斥锁（Mutex）或读写锁（RWMutex）来实现线程安全

同一把锁、不同的条件变量


#### Pool

对象复用池



#### Atomic

原子操作



### Test

`testing`

`_test.go`测试文件、`TestXxx`、`BenchmarkXxx`测试函数、大驼峰命名测试函数`testing.T`


#### Tags

测试标签



## 设计模式


### 单例模式
```go
type Singleton struct{}

var instance *Singleton
var once sync.Once

// GetInstance 返回单例对象
func GetInstance() *Singleton {
	once.Do(func() {
		instance = &Singleton{}
	})
	return instance
}
```

`sync.Once`懒汉式创建


### 工厂模式
```go
// 简单工厂模式
// Logger 接口
type Logger interface {
	Log(message string)
}

// ConsoleLogger 具体实现
type ConsoleLogger struct{}

func (c ConsoleLogger) Log(message string) {
	fmt.Println("Console:", message)
}

// FileLogger 具体实现
type FileLogger struct{}

func (f FileLogger) Log(message string) {
	fmt.Println("File:", message)
}

// LoggerFactory 工厂方法
func LoggerFactory(loggerType string) Logger {
	switch loggerType {
	case "console":
		return ConsoleLogger{}
	case "file":
		return FileLogger{}
	default:
		return nil
	}
}
```


### 适配器模式
```go
// 目标接口
type Database interface {
	Query(sql string) string
}

// MySQL 适配器
type MySQL struct{}

func (m *MySQL) Query(sql string) string {
	return "MySQL: " + sql
}

// PostgreSQL 适配器
type PostgreSQL struct{}

func (p *PostgreSQL) Query(sql string) string {
	return "PostgreSQL: " + sql
}

// 统一使用适配器
func ExecuteQuery(db Database, sql string) {
	fmt.Println(db.Query(sql))
}
```


### 装饰器模式
```go
// Logger 基础接口
type Logger interface {
	Log(message string)
}

// BasicLogger 基本日志实现
type BasicLogger struct{}

func (b BasicLogger) Log(message string) {
	fmt.Println("Log:", message)
}

// TimestampLogger 装饰器（添加时间）
type TimestampLogger struct {
	Logger
}

// 方法装饰实现，持有对象调用
func (t TimestampLogger) Log(message string) {
	fmt.Print("[Timestamp] ")
	t.Logger.Log(message)
}

timestampLogger := TimestampLogger{Logger: logger}
timestampLogger.Log("Something went wrong!")
```



### 观察者模式
```go
// 观察者接口
type Observer interface {
	Update(event string)
}

// 具体观察者
type User struct {
	Name string
}

func (u *User) Update(event string) {
	fmt.Println(u.Name, "收到通知:", event)
}

// 事件发布者
type EventPublisher struct {
	observers []Observer
}

func (p *EventPublisher) Subscribe(o Observer) {
	p.observers = append(p.observers, o)
}

func (p *EventPublisher) Notify(event string) {
	for _, observer := range p.observers {
		observer.Update(event)
	}
}


publisher := &EventPublisher{}

user1 := &User{Name: "Alice"}
user2 := &User{Name: "Bob"}

publisher.Subscribe(user1)
publisher.Subscribe(user2)

publisher.Notify("Go 1.22 发布了！")
```


### 策略模式
```go
// PaymentStrategy 支付接口
type PaymentStrategy interface {
	Pay(amount float64)
}

// 支付宝支付
type AliPay struct{}

func (a *AliPay) Pay(amount float64) {
	fmt.Println("使用支付宝支付:", amount)
}

// 微信支付
type WeChatPay struct{}

func (w *WeChatPay) Pay(amount float64) {
	fmt.Println("使用微信支付:", amount)
}

// 订单
type Order struct {
	Payment PaymentStrategy
}

func (o *Order) Checkout(amount float64) {
	o.Payment.Pay(amount)
}

order1 := &Order{Payment: &AliPay{}}
order1.Checkout(100)

order2 := &Order{Payment: &WeChatPay{}}
order2.Checkout(200)
```


和适配器模式一样，持有具体执行对象，只是语义不同

### 原型模式

Clone对象复制


### 建造者模式
```go
// User 复杂对象
type User struct {
	Name  string
	Age   int
	Email string
}

// UserBuilder 建造者
type UserBuilder struct {
	user *User
}

func NewUserBuilder() *UserBuilder {
	return &UserBuilder{user: &User{}}
}

func (b *UserBuilder) SetName(name string) *UserBuilder {
	b.user.Name = name
	return b
}

func (b *UserBuilder) SetAge(age int) *UserBuilder {
	b.user.Age = age
	return b
}

func (b *UserBuilder) SetEmail(email string) *UserBuilder {
	b.user.Email = email
	return b
}

func (b *UserBuilder) Build() *User {
	return b.user
}

user := NewUserBuilder().
    SetName("Alice").
    SetAge(25).
    SetEmail("alice@example.com").
    Build()
```

Builder链式构造


### 命令模式
```go

// 命令接口
type Command interface {
	Execute()
}

// 具体命令（打开电视）
type TV struct{}

func (t *TV) On() {
	fmt.Println("电视已打开")
}

type TVOnCommand struct {
	tv *TV
}

func (c *TVOnCommand) Execute() {
	c.tv.On()
}

// 遥控器
type RemoteControl struct {
	command Command
}

func (r *RemoteControl) SetCommand(command Command) {
	r.command = command
}

func (r *RemoteControl) PressButton() {
	r.command.Execute()
}

tv := &TV{}
onCommand := &TVOnCommand{tv: tv}

remote := &RemoteControl{}
remote.SetCommand(onCommand)
remote.PressButton() // 电视已打开
```


基于中间接口，连接两个对象的操作
类似适配器模式



### 责任链模式
```go
// 处理器接口
type Handler interface {
	SetNext(handler Handler)
	Handle(request string)
}

// 具体处理器
type AuthHandler struct {
	next Handler
}

func (h *AuthHandler) SetNext(next Handler) {
	h.next = next
}

func (h *AuthHandler) Handle(request string) {
	if request == "invalid" {
		fmt.Println("认证失败")
		return
	}
	fmt.Println("认证成功")
	if h.next != nil {
		h.next.Handle(request)
	}
}

// 日志处理器
type LogHandler struct {
	next Handler
}

func (h *LogHandler) SetNext(next Handler) {
	h.next = next
}

func (h *LogHandler) Handle(request string) {
	fmt.Println("记录日志:", request)
	if h.next != nil {
		h.next.Handle(request)
	}
}

func main() {
	auth := &AuthHandler{}
	log := &LogHandler{}

	auth.SetNext(log) // 先认证，再记录日志

	auth.Handle("valid")   // 认证成功 -> 记录日志
	auth.Handle("invalid") // 认证失败
}
```


### 状态模式
```go

// 状态接口
type OrderState interface {
	Handle(order *Order)
}

// 具体状态：待支付
type PendingState struct{}

func (p *PendingState) Handle(order *Order) {
	fmt.Println("订单未支付")
	order.SetState(&PaidState{})
}

// 具体状态：已支付
type PaidState struct{}

func (p *PaidState) Handle(order *Order) {
	fmt.Println("订单已支付")
}

// 订单结构
type Order struct {
	state OrderState
}

func (o *Order) SetState(state OrderState) {
	o.state = state
}

func (o *Order) Process() {
	o.state.Handle(o)
}

order := &Order{state: &PendingState{}}
order.Process() // 订单未支付
order.Process() // 订单已支付
```

小型状态机



### 访问者模式
```go
```