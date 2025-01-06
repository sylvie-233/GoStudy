# gorm

## 基础介绍

orm框架


## 核心内容
```yaml
gorm:
    _tags:
        gorm:
            default:
            primaryKey:
            unique:  
    Config: # 配置项
    Db: # 数据库
        Error:
        RowsAffected:
        AutoMigrate(): # 自动迁移（传入模型类）
        Create(): # 创建记录
        Db(): # 返回sql.Db对象
        Find(): # 查询
        First():
        Where():
    Model: # 模型
    Open():
```