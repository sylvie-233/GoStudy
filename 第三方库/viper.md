# viper


## 基础介绍

go配置管理库

`github.com/spf13/viper`


## 核心内容
```yaml
viper:
    AddConfigPath(): # 设置配置文件路径
    AddRemoteProvider():
    AutomaticEnv(): # 读取环境变量
    BindEnv():
    BindPFlag(): # 绑定命令行参数
    GetInt():
    GetString(): # 获取配置值
    OnConfigChange():
    ReadInConfig(): # 读取配置文件
    ReadRemoteConfig():
    SetConfigName(): # 设置配置文件名
    SetConfigType(): # 设置配置文件类型
    SetDefault(): # 设置默认值
    Unmarshal(): # 读取配置到结构体
    WatchConfig():
```