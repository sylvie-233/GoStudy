# logrus


## 基础介绍

go日志库

## 核心内容
```yaml
logrus:
    AllLevels:
    Entry: # 自定义Formatter、Hook
        Buffer:
        Caller:
            File:
            Func:
            Line:
        Data: # 字段传值
        Level:
        Message: # 日志内容
        Time:
        String():
    Fields:
    Formatter:
        Format:
    Hook:
        Levels(): # Hook绑定的日志级别
        Fire():
    JSONFormatter:
        Format():
    TextFormatter:
    WarningLevel:
    AddHook():
    Debug():
    Error():
    Info():
    Println():
    SetFormatter():
    SetLevel():
    SetOutput():
    SetReportCaller():
    Warning():
    WithField(): # 字段传值
    WithFields(): # 字段传值
```


### 日志等级

Level



### Formatter

日志格式化器


### Output

日志输出

利用io的MultiWriter可实现多路输出


#### 日志分割      

自定义Writer实现（也可借助Hook实现）



### Hook

钩子函数、日志级别绑定