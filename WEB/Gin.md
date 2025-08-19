# Gin

`（完结）Gin官方文档：https://gin-gonic.com/docs/`



## 基础介绍

go web轻量级框架`github.com/gin-gonic/gin`
默认端口：8080
类似nodejs的koa框架

Engine -> RouterGroup -> Context



## 核心内容
```yaml
gin:
    _tags:
        binding: # 字段绑定
            gtfield: # 大于字段
            require:
            uuid:
        form: # 表单参数绑定
        josn:
        time_format: # 时间格式化字符串
        time_utc: # 时间格式化时区
        uri: # path param绑定
        xml:
    binding: # 指定参数绑定来源
        JSON:
        Query:
        Validator:
            Engine():
    Accounts: # 内置认证中间件 用户账户
    AuthUserKey: # 内置认证中间件 用户key，用于获取用户
    Context: # 请求上下文
        Request:
            Host:
            URL:
                Path:
        Writer:
            Pusher():
            Status():
        Abort():
        AbortWithError():
        AbortWithStatusJSON():
        AsciiJSON():
        Bind(): # 参数绑定（必须）
        BindJSON():
        BindQuery():
        BindXML():
        BindYAML():
        Cookie(): # 获取Cookie
        Copy(): # 创建Context副本
        DataFromReader(): # 流式响应
        DefaultPostForm(): # 带默认值的 form 参数
        DefaultQuery(): # 带默认值的 query 参数
        FormFile(): # 获取表单文件
        FullPath():
        Get(): # 获取kv键值对 
        GetHeader(): # 获取请求头
        HandleContext(): # 手动处理（实现请求转发）
        Header(): # 设置响应头
        HTML(): # 模板页面响应
        JSON(): # JSON数据响应
        JSONP(): # JSONP响应
        MustBindWith():
        MustGet():
        MultipartForm(): # 获取form表单参数
            File:
        Next(): # 中间件请求下放
        Param(): # 请求path params
        PostForm(): # form body params
        PostFormMap():
        ProtoBuf():
        PureJSON():
        Query(): # query params
        QueryMap():
        Redirect(): # 重定向
        SaveUploadedFile(): # 保存上传文件
        SecureJSON():
        Set(): # 存储值
        SetCookie(): # 设置Cookie
        ShouldBind(): # 参数绑定
        ShouldBindJSON(): # 参数绑定
        ShouldBindUri():
        ShouldBindWith(): # 手动设置参数绑定源，绑定之前将 body 存储到上下文中
        Status(): # 响应状态
        String(): # 响应字符串
        XML(): # xml数据响应
        YAML(): # yaml 数据响应
    DebugPrintRouteFunc: # debug调试打印函数
    DefaultWriter: # gin默认日志输出Writer
    Engine: # 路由引擎
        MaxMultipartMemory:
        AsciiJSON():
        Delims(): # 自定义模板分隔符
        GET(): # GET请求处理
        Group(): # 新建路由组
        Handler(): # 获取所有路由处理函数
        JSON():
        LoadHTMLFiles(): # 加载模板文件
        LoadHTMLGlob(): # 匹配加载所有模板文件
        Run(): # server服务运行
        ServeHTTP(): # 响应输出到Writer中
        SetFuncMap(): # 注册模板函数
        SetHTMLTemplate(): # 设置模板引擎
        Static(): # 静态文件目录挂载
        StaticFile():
        StaticFS():
        Use(): # 注册中间件
    Error:
    H: # map[string]any 字典（帮助快速创建字典）
    HandlerFunc: # 路由处理函数
    HandlersChain:
    LogFormatter:
    LogFormatterParams: # gin内置日志格式化参数（自定义）
        ClientIP:
        ErrorMessage:
        Latency:
        Method:
        Path:
        Request:
        StatusCode:
        TimeStamp:
    LoggerConfig:
    Params:
    ResponseWriter:
    RouterGroup: # 路由分组（子路由）
        ANY():
        DELETE():
        GET():
        HEAD():
        MATCH():
        OPTIONS():
        PATCH():
        POST(): # POST请求处理
        PUT():
        Use(): # 注册中间件
    BasicAuth(): # gin 内置认证中间件
    Default(): # 默认路由引擎(Logger and Recovery middleware)
    Delims(): # 模板语法分隔符
    Dir():
    DisableBindValidation(): 
    DisableConsoleColor(): # 禁用控制台颜色
    ForceConsoleColor():
    IsDebugging():
    LoggerWithFormatter():
    New(): # 新建路由引擎，没有默认中间件
    Recovery(): # gin 内置异常处理中间件
    SetMode(): # 设置开发模式

gin-contrib: # 官方维护中间件合集
    cors:
    logger:
    prometheus:
    requestid:
    secure:
    sessions:
        cookie:
    static:
    timeout:

validator: # 
    FieldLevel:
        Field():
    Func:
    Validate: # 字段校验器
        RegisterValidation(): # 注册校验函数
```

### 路由


#### 上下文


`gin.Context`上下文，存储请求响应



#### 路由分组


### 中间件
```go
func Logger() gin.HandlerFunc {
	return func(c *gin.Context) {
		t := time.Now()

		// Set example variable
		c.Set("example", "12345")

		// before request
		c.Next()

		// after request
		latency := time.Since(t)
		log.Print(latency)

		// access the status we are sending
		status := c.Writer.Status()
		log.Println(status)
	}
}
```

### 参数绑定



### 参数校验





### 异常处理



### 模板引擎

gin使用go内置模板引擎



### 日志



### 异步任务

简单使用Goruntine协程即可实现



### 认证权限



### 缓存



### ORM


### WebSocket 

### GraphQL

### gRPC


















