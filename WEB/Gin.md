# Gin

## 基础介绍


## 核心内容
```yaml
gin:
    Context: # 请求上下文
        Abort():
        GetHeader(): # 获取请求头
        Next(): # 请求下放
        Set(): # 存储值
        ShouldBindJSON(): # 参数绑定
    Engine: # 路由引擎
        GET():
        JSON():
        Run(): # 服务运行
        Use(): # 注册中间件
    Group: # 路由分组
        POST():
    H: # map[string]any 字典
    HandlerFunc: # 路由处理函数
    Default(): # 默认路由引擎
```

### 路由

#### 请求


#### 响应



#### 路由分组


### 中间件


#### JWT校验


### ORM




### 配置文件


### 异常处理


### 参数绑定

`ctx.ShouldBindJson(&obj)`


### 热重载



### 常用工具箱

#### 加密



#### JWT
