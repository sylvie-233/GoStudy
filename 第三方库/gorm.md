# gorm

## 基础介绍

orm框架


## 核心内容
```yaml
gorm:
    _tags:
        binding:
            require:
        gorm:
            unique:  
    Config: # 配置项
    Db: # 数据库
        Error:
        RowsAffected:
        AutoMigrate(): # 自动迁移
        Create(): # 创建记录
        Db(): # 返回sql.Db对象
        Find():
        First():
        Where():
    Model: # 模型
    Open():
```