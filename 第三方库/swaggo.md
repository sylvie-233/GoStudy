# swaggo


## 基础介绍

API 文档生成工具
通过注释自动生成符合 OpenAPI 规范的 Swagger 文档



### swag
```yaml
swag:
    init: # 生成docs/docs.go、docs/swagger.json
```


## 核心内容
```yaml
github.com/swaggo:
    /files:
        swaggerFiles:
            Handler:
    /gin-swagger:
        ginSwagger:
            WrapHandler():
```


### 注释
```yaml
swagger:
    @Accept:
    @Description:
    @Failure:
    @Param:
    @Produce:
    @Router:
    @Security:
    @Success:
    @Summary:
    @Tags:
```