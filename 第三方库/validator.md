# validator

## 基础介绍

数据校验库
基于tag的结构体校验工具


## 核心内容
```yaml
validator:
    _tag:
        validate:
            email:
            gte:
            len:
            lte:
            required:
    FieldLevel:
        Field():
    Validate: # 校验器类
        RegisterValidation(): # 注册自定义校验函数
        Struct(): # 结构体校验
        Var(): # 单个变量校验
    ValidationErrors: # 校验异常
        Field():
        Tag():
    New():
```