# Gin

`Gin官方文档：https://gin-gonic.com/docs/`



## 基础介绍

go web轻量级框架`github.com/gin-gonic/gin`
默认端口：8080



## 核心内容
```yaml
gin:
    _tags:
        binding:
            gtfield: # 大于字段
            require:
            uuid:
        form: # 表单参数绑定
        josn:
        time_format: # 时间格式化字符串
        time_utc: # 时间格式化时区
        uri: # path param绑定
        xml:
    binding: # 参数绑定
        JSON:
        Query:
        Validator:
            Engine():
    Accounts:
    AuthUserKey:
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
        Cookie(): # Cookie
        Copy(): # 创建Context副本
        DataFromReader(): # 流式响应
        DefaultPostForm():
        DefaultQuery():
        FormFile(): # 获取表单文件
        FullPath():
        Get(): # 获取kv键值对 
        GetHeader(): # 获取请求头
        HandleContext(): # 手动处理（实现请求转发）
        Header(): # 设置响应头
        HTML():
        JSON(): # JSON数据响应
        JSONP():
        MustBindWith():
        MultipartForm():
            File:
        Next(): # 中间件请求下放
        Param(): # path params
        PostForm(): # form body params
        PostFormMap():
        ProtoBuf():
        PureJSON():
        Query(): # query params
        QueryMap():
        Redirect(): # 重定向
        SaveUploadedFile(): # 保存文件
        SecureJSON():
        Set(): # 存储值
        SetCookie():
        ShouldBind(): # 参数绑定
        ShouldBindJSON(): # 参数绑定
        ShouldBindUri():
        ShouldBindWith(): # 手动设置参数绑定源
        Status(): # 响应状态
        String(): # 响应字符串
        XML():
        YAML():
    DebugPrintRouteFunc: # debug调试打印函数
    DefaultWriter: # gin默认日志输出
    Engine: # 路由引擎
        MaxMultipartMemory:
        GET(): # GET请求处理
        Handler(): # 获取所有路由处理函数
        JSON():
        LoadHTMLFiles(): # 加载静态文件
        LoadHTMLGlob(): # 匹配加载所有模板文件
        Run(): # server服务运行
        SetFuncMap(): # 注册模板函数
        SetHTMLTemplate():
        Static(): # 静态文件目录挂载
        StaticFile():
        StaticFS():
        Use(): # 注册中间件
    Group: # 路由分组（子路由）
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
    H: # map[string]any 字典（帮助快速创建字典）
    HandlerFunc: # 路由处理函数
    LogFormatterParams: # gin内置日志格式化参数（自定义）
        ClientIP:
        ErrorMessage:
        Latency:
        Method:
        Path:
        Request:
        StatusCode:
        TimeStamp:
    BasicAuth(): # gin 内置认证中间件
    Default(): # 默认路由引擎(Logger and Recovery middleware)
    Delims(): # 模板语法分隔符
    DisableConsoleColor():
    ForceConsoleColor():
    LoggerWithFormatter():
    New(): # 新建路由引擎
    Recovery(): # gin 内置异常处理中间件
    SetMode(): # 设置开发模式

validator:
    FieldLevel:
        Field():
    Func:
    Validate: # 字段校验器
        RegisterValidation(): # 注册校验函数
```

### 路由

#### 请求


#### 响应


#### 上下文



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


#### JWT


#### CORS


### ORM



### 模板引擎

gin使用go内置模板引擎



### 配置文件


### 异常处理


### 参数绑定

`ctx.ShouldBindJson(&obj)`

tags:
- form


### 热重载


## 项目实战


### 