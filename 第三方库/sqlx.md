# sqlx


## 基础介绍


sql查询构造器
`github.com/jmoiron/sqlx`




## 核心内容
```yaml
github.com/jmoiron/sqlx:
    _tag:
        db: # 字段映射
    Conn:
    DB:
        Beginx(): # 开启事务
        Close():
        Get(): # 执行单条查询sql
        MustExec():
        NamedQuery(): # 结构体参数执行query
        NamedExec(): # 结构体参数执行exec（命名参数）
        Ping():
        Select(): # 执行多条查询
    NamedStmt:
    Row:
    Rows:
    Stmt:
    Tx: # 事务
        Commit():
        Exec(): # 
        Get():
    Connect(): # 获取数据库连接DB
```