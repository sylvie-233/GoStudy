# casbin



## 基础介绍

认证权限框架
`github.com/casbin/casbin`

Casbin是Golang中一个强大的权限管理库，支持多种访问控制模型:
- RBAC（基于角色的访问控制）
- ABAC（基于属性的访问控制）
- ACL（访问控制列表）

Casbin 主要特性
- 支持多种权限控制模型（RBAC/ABAC/ACL）
- 支持数据库存储策略（MySQL/PostgreSQL/Redis）
- 支持动态修改权限规则
- 兼容 RESTful API、GraphQL、gRPC、微服务架构
- 跨语言支持（Go、Java、Python、Node.js 等）




User -> Role -> Policy


### model.conf
```yaml
model.conf:
    request_definition: # 请求认证定义
        r: # Enforce手动传入
            sub:
            obj:
            act:
    policy_definition: # 授权定义
        p: # p, admin, data, read   给admin角色授权data的read权限
            sub:
            obj:
            act:
    role_definition: # 角色定义
        g: # g = _, _    g, alice, admin 给alice赋予admin角色
    policy_effect: # 认证通过策略 （什么时候才通过）
        some(): # 只要至少有一个allow规则匹配，则允许访问
            where():
    matchers: # 权限匹配规则（如何才算通过）
        g():
        keyMatch():
        regexMatch():
```

- 请求定义
- 权限策略定义
- 角色继承
- 规则生效策略
- 访问匹配规则


认证模型策略定义
每个部分只能包含一个定义项
一个model.conf就只包含一种类型校验、可利用多model.conf实现多类型校验


## 核心内容
```yaml
casbin/v3:
    config:
    effect:
    errors:
    log:
    gorm-adapter:
        NewAdapterByDB(): # gorm数据库存储策略
    model:
        FunctionMap:
        Model: # 权限模型基类
            AddDef(): # 添加定义
        PolicyOp:
        NewModel():
    persist: # 数据存储策略
        file-adapter:
            NewAdapter(): # 文件系统存储策略
    rbac:
    util:
    CachedEnforcer:
    Enforcer: # 认证执行器
        AddPolicy(): # 给角色添加策略
        AddRoleForUser(): # 给用户添加角色
        Enforce(): # 执行认证
    SyncedEnforcer:
```


### Enforcer

认证执行器、依赖认证模型Model、数据存储策略Adapter
可以使用多个Enforcer来实现，不同类型的权限校验




### Model


权限定义，model.conf



### Adaper
```go
// 自定义adaper，实现casbin.Adapter接口
type MemoryAdapter struct {
	policies [][]string
}

func NewMemoryAdapter() *MemoryAdapter {
	return &MemoryAdapter{
		policies: make([][]string, 0),
	}
}

func (m *MemoryAdapter) LoadPolicy() error {
	fmt.Println("Loading policies from memory...")
	return nil
}

func (m *MemoryAdapter) SavePolicy() error {
	fmt.Println("Saving policies to memory:")
	for _, policy := range m.policies {
		fmt.Println(policy)
	}
	return nil
}

func (m *MemoryAdapter) AddPolicy(params ...interface{}) error {
	m.policies = append(m.policies, toStringSlice(params))
	fmt.Println("Added policy:", params)
	return nil
}

func (m *MemoryAdapter) RemovePolicy(params ...interface{}) error {
	for i, policy := range m.policies {
		if equalPolicies(policy, toStringSlice(params)) {
			m.policies = append(m.policies[:i], m.policies[i+1:]...)
			fmt.Println("Removed policy:", params)
			return nil
		}
	}
	return fmt.Errorf("policy not found")
}

func (m *MemoryAdapter) RemoveFilteredPolicy(fieldIndex int, fieldValues ...interface{}) error {
	var newPolicies [][]string
	for _, policy := range m.policies {
		if policy[fieldIndex] != fieldValues[0].(string) {
			newPolicies = append(newPolicies, policy)
		}
	}
	m.policies = newPolicies
	return nil
}

func toStringSlice(params []interface{}) []string {
	var result []string
	for _, param := range params {
		result = append(result, fmt.Sprintf("%v", param))
	}
	return result
}

func equalPolicies(p1, p2 []string) bool {
	if len(p1) != len(p2) {
		return false
	}
	for i := range p1 {
		if p1[i] != p2[i] {
			return false
		}
	}
	return true
}

func main() {
	// 创建自定义的内存适配器
	adapter := NewMemoryAdapter()

	// 创建 Casbin 的 Enforcer，使用自定义适配器
	e, _ := casbin.NewEnforcer("model.conf", adapter)

	// 添加策略
	e.AddPolicy("admin", "data1", "read")
	e.AddPolicy("user", "data2", "write")

	// 保存策略
	e.SavePolicy()

	// 移除策略
	e.RemovePolicy("user", "data2", "write")
	e.SavePolicy()
}
```

数据存储策略

自定义adaper，实现casbin.Adapter接口
- LoadPolicy() error：从存储中加载策略，初始化加载
- SavePolicy() error：将策略保存到存储中：Enforcer.SavePolicy()
- AddPolicy() error：添加一条策略：Enforcer.AddPolicy()
- RemovePolicy() error：移除一条策略：Enforcer.RemovePolicy()
- RemoveFilteredPolicy() error：根据过滤条件移除策略：Enforcer.RemovePolicy()