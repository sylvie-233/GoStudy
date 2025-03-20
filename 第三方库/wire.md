# wire

## 基础介绍

go依赖注入包、基于代码生成实现
Wire生成器命令、Wire运行时包
- Provider：表示如何创建一个对象的函数，它是 Wire 的核心。你可以用一个func来定义如何生成某个对象
- Injector：Wire 会生成一个注入器函数，自动将依赖项传递给你的对象


1. 定义构造函数(NewXxx())，构造函数参数形成依赖
    - New<类型名> 作为构造函数名。
    - 通常返回类型为 *<类型> 和 error
2. wire.Build()定义依赖关系



### wire
```yaml
wire:
    -v:
    check:
    commands:
    diff:
    flags:
    help:
    gen:
        -header_file:
        -output_file_prefix:
    show:
```

wire依赖注入代码生成



## 核心内容
```yaml
wire:
    Build(): # 构造依赖
```


### Provider

NewXxx():构造函数


### Injector


InitializeXxx(): 实例注入生成（依赖构造函数）