# sqlx


## 基础介绍


sql查询构造器
`github.com/jmoiron/sqlx`




## 核心内容
```yaml
sqlx:
    _tag:
        db: # 字段映射
    Conn:
    DB:
        Beginx(): # 开启事务
        Close():
        Get(): # 执行单条查询sql
        NamedQuery(): # 结构体参数执行query
        NamedExec(): # 结构体参数执行exec
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