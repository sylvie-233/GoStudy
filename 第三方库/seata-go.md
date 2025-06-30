# seata-go



## 基础介绍


官方提供的Go客户端 SDK，用于与 Seata Server 通讯



跨服务通过请求头传递xid



### seata.yaml
```yaml
seata.yaml:
    applicationID:
    txServiceGroup:
    seata:
        application-id: # 应用名
        tx-service-group: # 组名
        enabled:
        client: # 客户端配置
            rm:
                report-retry-count: 
            tm:
                commit-retry-count:
                rollback-retry-count:
        service: # 服务端配置
            grouplist: # seata服务连接地址
            vgroup-mapping: # 组名映射
        config:
        registry:
            type:
                file:
            file:
                name: # seata服务连接配置文件
        transport:
            type:
```

#### registre.yaml
```yaml
registry.yml:
    file:
        server:
            default:
                addr: # 连接地址
                type:
        service:
            vgroupMapping: # seata组映射
                seata-go-tx-group:
    registry:
        type:
        file:
    
```

连接seata server配置


## 核心内容
```yaml
github.com/seata/seata-go/pkg:
    /client:
        client: # 事务客户端
            InitPath(): # seata.yaml配置文件
    /common:
        /context:
            /seata:
                seata: # Seata管理
                    NewSeataContext():
                    WithXID():
    /datasource:
        /sql:
            /mysql:
                mysql: # mysql数据源
                    DBProxy:
                        ExecContext():
                    NewDBProxy(): # 创建数据库代理
    /rm:
        /tcc:
            tcc: # TCC
                BusinessActionContext:
                    XID:
                Get(): # 获取TCC服务，用于执行操作
                Register(): # 注册TCC服务
    /tm:
        tm: # 全局事务管理器
            GtxConfig: # 全局事务配置
                Name:
                Timeout:
            TCC:
            GlobalTransaction(): # 手动管理全局事务 
                Begin():
                Commit():
            GetGlobalTx(): # 获取全局事务
                RegisterBranch(): # 注册分支事务    
            GetXID(): # 获取全局事务ID
            NewRootContext(): # 居于xid全局事务ID创建管理上下文
            WithGlobalTx():
```


### TM

全局事务管理器
```go
tm.WithGlobalTx(func(ctx context.Context) error {
    fmt.Println("XID:", tm.GetXID(ctx))
    ...
})
```





### XA




### TCC

定义三接口：
- Try()/Prepare()s:
- Confirm():
- Cancel():

需手动处理：幂等 + 空回滚 + 异常重试
- 幂等性	同一个 XID 的 confirm/cancel 可能被多次调用
- 空回滚	cancel 被调用时 try 根本没执行，需要判断
- 异常重试	网络抖动/宕机等，Seata 会自动重试 commit/cancel


### SAGA



### AT


AT模式执行流程：
1. 启动全局事务，向 Seata Server 注册（Begin）
2. 上下文中设置 XID
3. 数据库操作被代理记录（undo_log）
4. 执行成功，向 Seata Server 发送 commit 请求
   - Seata Server 再向所有分支发出 commit
5. 如果失败，Seata Server 发送 rollback 到所有分支
