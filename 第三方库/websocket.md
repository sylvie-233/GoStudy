# websocket


## 基础介绍

Websocket库
`github.com/gorilla/websocket`


依赖HTTP服务


## 核心内容
```yaml
websocket:
    Conn: # websocket连接
        Close(): # 关闭连接
        EnableWriteCompression():
        ReadMessage(): # 读取消息
        SetPongHandler():
        SetReadDeadline():
        WriteMessage(): # 发送消息
    DefaultDialer: # 默认请求客服端Dialer
    Dialer: # 请求客户端
        Dial():
        DialContext():
    Upgrader: # WebSocket 升级器
        Upgrade(): # 升级http协议，创建Conn连接
    JoinMessages():
    NewClient():
    ReadJson():
    Upgrade(): # 
    WriteJson():
```