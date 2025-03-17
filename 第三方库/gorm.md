# gorm

``

## 基础介绍

orm框架

Db -> Session -> Model
基于Db对象进行操作

GORM默认使用 目标表名+ID 作为外键
利用外键`foreignKey`，外键依赖`references`



## 核心内容
```yaml
gorm:
    _tags:
        gorm:
            column: # 字段映射
            comment:
            default: # 默认值
            embedded: # 嵌套字段
            embeddedPrefix:
            foreignKey: # 外键字段、定义、一对一查询
            joinForeignKey: # 关联表外键字段
            joinReferences: # 关联表外键依赖字段
            many2many: # 多对多关联表名
            not null: # 非空
            primaryKey: # 主键
            references: # 外键依赖字段，默认ID
            size:
            type:
            unique:  
            uniqueIndex: # 唯一索引
    logger:
        Default:
            LogMode():
        Info:
        Interface:
        Logger:
    schema:
        NamingStrategy:
    Association: # 关联对象操作，操作关联关系，常用于多对多操作中间表,
        Append(): # 添加中间表记录
        clear():
        Delete(): # 删除中间表记录
        Find():
    Session:
        Logger:
    Config: # 数据库配置
        Logger:
        NamingStrategy:
            NoLowerCase:
            SignularTable:
            TablePrefix:
        SkipDefaultTransaction:
    Db: # 数据库对象
        Error:
        RowsAffected:
        Association(): # 关联模型
            Append(): # 关联模型添加
            Delete(): # 关联模型删除
            Replace():
        AutoMigrate(): # 自动迁移（传入模型类），创建数据库表
        Begin(): # 开启事务
        Create(): # 插入数据，创建模型（接收Model指针）
            Error:
        Commit():
        Db(): # 返回sql.Db对象
        Debug():
        Delete(): # 删除数据
        Exec(): # 执行原生SQL
        Find(): # 条件查询（默认主键）&数据绑定
            Error:
            RowAffected:
        First(): # 第一条记录（id排序），可传入查询条件，默认id
        Last():
        Model(): # 指定操作模型
        Preload(): # 关联模型预加载
        Raw(): # 执行原生SQL，query
        Rollback(): # 事务回滚
        Save(): # 更新模型
        Scan():
        Scope(): # 引用SQL片段
        Session(): # 创建Session
        SetupJoinTable(): # 多对多查询手动设置中间表
        Table():
        Take(): # 查询一条记录
        Unscoped():
        Update(): # 更新模型
        Updates(): # 更新模型
        Where(): # 查询条件
            Distinct():
            Group():
            Limit(): # 限制
            Not():
            Offset(): # 偏移
            Or(): # || 或逻辑，默认 && 与逻辑
            Order():
            Select(): # 字段选择
    ErrRecordNotFound:
    Model: # 模型基类
        AfterCreate(): # Hook
        AfterUpdate(): # Hook
        BeforeCreate(): # Hook 
        BeforeUpdate(): # Hook 
        MarshalJSON():
        Scan():
        String():
        Value():
    Open(): # 连接数据库、获取Db实例

mysql:
    Open():
```


### Model

`Model`数据库模型基类
默认提供ID、创建时间、更新时间、软删除时间



### 数据库迁移

`Db.AutoMigrate()`




### 关联查询

默认关联外键字段：`XXXId`

SetupJoinTable

Preload、Association



#### 一对一
```go
// 用户类定义
type User struct {
	ID       uint   `gorm:"primaryKey"`
	Name     string `gorm:"size:100;not null"`
	Age      int
}

// 用户信息类定义
type Profile struct {
	ID     uint
	UserID uint
	Phone  string
	User   User `gorm:"foreignKey:UserID"`
}
```

foreignKey(自己) -> references(对方)



#### 一对多
```go
// 用户类定义
type User struct {
	ID       uint   `gorm:"primaryKey"`
	Name     string `gorm:"size:100;not null"`
	Age      int
    Orders   []Order `gorm:"foreignKey:UserID"`
}

// 用户订单定义
type Order struct {
	ID     uint
	UserID uint
	Amount float64
}
```

`Belongs To`、`Has Many`

foreignKey(自己) -> references(对方)
查询预加载



#### 多对多
```go
type Post struct {
    ID      uint
    Title   string
    Tags    []Tag `gorm:"many2many:post_tags;foreignKey:PostID;joinForeignKey:PostRef;References:TagID;joinReferences:TagRef"`
}

type Tag struct {
    ID    uint
    Name  string
    Posts []Post `gorm:"many2many:post_tags;foreignKey:TagID;joinForeignKey:TagRef;References:PostID;joinReferences:PostRef"`
}
```

- many2many：多对多关联中间表、表名
- foreignKey：自己类中的外键字段名
- joinForeignKey：中间表中的外键字段
- joinReferences：中间表中的外键依赖字段
- references：外表中的外键依赖字段

foreignKey -> joinForeignKey -> joinReferences -> references



### Hook
- AfterCreate():
- AfterUpdate():
- BeforeCreate(): 
- BeforeUpdate(): 


模型操作拦截AOP


### Transaction
- Db.Begin()
- Db.Rollback()
- Db.Commit()