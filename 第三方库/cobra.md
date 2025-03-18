# Cobra

## 基础介绍

go 命令行工具库
`github.com/spf13/cobra`

- 支持多层级的子命令
- 支持命令行参数、标志和自动帮助文档
- 具有自动化的命令行解析和命令行帮助信息



## 核心内容
```yaml
cobra:
    Command: # 命令类
        Args: # 获取参数
        Long: # 长描述
        Short: # 简短描述
        Use: # 命令定义
        AddCommand(): # 添加子级命令
        Execute(): # 命令运行
        Flags(): # 返回标志 flag.FlagSet
            String(): # 添加标志
        Run(): # 命令执行逻辑 
    NoArgs:
    PositionalArgs:
    ExactArgs(): # 参数个数限制
    MaximumNArgs():
    MinimumNArgs():
    RangeArgs():
```