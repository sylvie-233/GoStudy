# gorm

``

## 基础介绍

orm框架

Db -> Session -> Model


## 核心内容
```yaml
gorm:
    _tags:
        gorm:
            column:
            comment:
            default:
            embedded: # 嵌套字段
            embeddedPrefix:
            foreignKey: # 外键
            joinForeignKey:
            joinReferences:
            many2many: # 多对多关联
            not null:
            primaryKey:
            references: # 外键引用字段
            size:
            type:
            unique:  
    logger:
        Default:
            LogMode():
        Info:
        Interface:
        Logger:
    schema:
        NamingStrategy:
    Session:
        Logger:
    Config: # 配置项
        Logger:
        NamingStrategy:
            NoLowerCase:
            SignularTable:
            TablePrefix:
        SkipDefaultTransaction:
    Db: # 数据库
        Error:
        RowsAffected:
        Association(): # 关联模型
            Append(): # 关联模型添加
            Delete(): # 关联模型删除
            Replace():
        AutoMigrate(): # 自动迁移（传入模型类）
        Create(): # 创建模型（接收Model指针）
            Error:
        Db(): # 返回sql.Db对象
        Debug():
        Delete(): # 删除值
        Find(): # 条件查询（默认主键）
            Error:
            RowAffected:
        First(): # 第一条记录（id排序）
        Last():
        Model(): # 指定操作模型
        Preload(): # 预加载
        Raw(): # 执行原生SQL
        Save(): # 更新模型
        Scan():
        Scope(): # 引用SQL片段
        Session(): # 创建Session
        SetupJoinTable(): # 多对多查询手动设置中间表
        Table():
        Take(): # 查询一条记录
        Update(): # 更新模型
        Updates(): # 更新模型
        Where(): # 查询条件
            Distinct():
            Group():
            Limit():
            Not():
            Offset():
            Or():
            Order():
            Select(): # 字段选择
    ErrRecordNotFound:
    Model: # 模型基类
        BeforeCreate(): # Hook 
        MarshalJSON():
        Scan():
        String():
        Value():
    Open(): # 连接数据库、获取Db实例
mysql:
    Open():
```


### Model

数据库模型



### 数据库迁移




### 关联查询

默认关联外键字段：`XXXId`

SetupJoinTable

Preload、Association



#### 一对一





#### 一对多

`Belongs To`、`Has Many`


查询预加载



#### 多对多

joinForeignKey、joinReferences、many2many




### Hook

模型操作拦截AOP


### 事务管理