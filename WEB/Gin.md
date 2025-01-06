# Gin

## 基础介绍


## 核心内容
```yaml
gin:
    _tags:
        binding:
            require:
    Context: # 请求上下文
        Request:
            URL:
        Abort():
        DefaultPostForm():
        FormFile(): # 获取表单文件
        FullPath():
        GetHeader(): # 获取请求头
        JSON(): # JSON响应
        MultipartForm():
        Next(): # 请求下放
        Param(): # path params
        PostForm(): # form body params
        Query(): # query params
        Redirect(): # 重定向
        SaveUploadedFile(): # 保存文件
        Set(): # 存储值
        ShouldBindJSON(): # 参数绑定
        String(): # 响应字符串
    Engine: # 路由引擎
        GET(): # GET请求处理
        JSON():
        LoadHTMLFiles(): # 加载静态文件
        LoadHTMLGlob():
        Run(): # 服务运行
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
    Default(): # 默认路由引擎
```

### 路由

#### 请求


#### 响应



#### 路由分组


### 中间件


#### JWT校验


#### CORS


### ORM




### 配置文件


### 异常处理


### 参数绑定

`ctx.ShouldBindJson(&obj)`


### 热重载



### 常用工具箱

#### 加密



#### JWT
