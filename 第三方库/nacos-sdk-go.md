# nacos-sdk-go



## 基础介绍


Nacos服务注册中心SDK


## 核心内容
```yaml
github.com/alibaba/nacos-sdk-go/v2:
    /clients:
        /config_client:
            config_client: # 配置客户端
                IConfigClient:
                    GetConfig(): # 获取配置
                    ListenConfig(): # 监听配置
        /nacos_client:
        /naming_client:
            naming_client: # 服务注册与发现客户端
                INamingClient:
                    RegisterInstance(): # 注册服务实例
                    SelectAllInstances(): # 获取所有服务实例
        clients: # 客户端
            CreateConfigClient(): # 创建配置中心客户端
                clientConfig:
                serverConfigs:
            CreateNamingClient(): # 创建服务注册、发现客户端
                clientConfig:
                serverConfigs:  
    /common:
        /constant: 
            constant: # 常量配置
                ClientConfig: # 客户端配置
                    LogLevel:
                    NamespaceId: # 命名空间 默认 ""
                    NotLoadCacheAtStart:
                    TimeoutMs:
                ServerConfig: # 服务端配置
                    IpAddr:
                    Port:
    /vo:
        ConfigParam: # 配置参数
            DataId:
            Group:
            OnChange:
        RegisterInstanceParam: # 服务注册参数
            Ephemeral:
            Enable:
            GroupName:
            Healthy:
            Ip:
            Port:
            ServiceName:
            Weight:
        SelectAllInstancesParam: # 获取所有服务实例参数
            GroupName:
            ServiceName:
```