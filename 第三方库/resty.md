# resty


## 基础介绍


golang 网络请求库


## 核心内容
```yaml
github.com/go-resty/resty/v2:
    Client: # 请求客户端
        New():
        OnBeforeRequest(): # 请求前Hook
        OnAfterResponse(): # 响应后Hook
        R():
        SetCookie():
        SetHeader():
        SetHostURL():
        SetRetryCount():
        SetRetryMaxWaitTime():
        SetRetryWaitTime():
        SetTimeout():
        SetTLSClientConfig():
    Request: # 请求
        Get():
        Post():
        SetBody():
        SetFile():
        SetFormData():
        SetHeader():
        SetOutput():
        SetQueryParam():
        SetResult():
    Response: # 响应
        Header():
        Status():
        StatusCode():
        String():
```