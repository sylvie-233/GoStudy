# promptui

## 基础介绍

go命令行交互工具库


### ANSI转义码
```yaml
ANSI:
    \033:
        [A: # 光标上移一行
        [B: # 光标下移一行
        [C: # 光标右移一列
        [D: # 光标左移一列
        [H: # 将光标移到屏幕的左上角（第 1 行第 1 列）
        [?25h: # 显示光标
        [0J: # 清除光标之后的屏幕内容
        [2J: # 清除屏幕（清除终端所有内容）
        [K: # 清除光标所在的当前行的内容
        [1K: # 清除光标所在行的前半部分
        [?25l: # 隐藏光标
        [0m: # 重置所有属性（颜色、样式）
        [1m: # 文本属性 粗体
        [5m: # 文本属性 闪烁
        [9m: # 文本属性 删除线
        [30m: # 文本颜色黑色
        [31m: # 文本颜色红色
        [40m: # 背景颜色黑色
        [_r;_c: # 将光标移动到指定行列 (row 和 col 代表行列位置)
```


## 核心内容
```yaml
promptui:
    Cursor:
    Prompt: # 单行输入
        AllowEdit:
        Default: # 默认值
        HideEntered: # 输入完隐藏
        IsConfirm: # 确认框
        Label: # 输入提示
        Mask: # 输入显示隐藏
        Pointer:
        Stdin:
        Stdout:
        Validate: # 自定义输入校验
        Run(): # 运行、返回输入结果
    Select: # 多行输入
        CursorPos:
        Items:
        Keys:
        Label: # 输入提示：
        Size: # 显示条目数，默认5
        Run(): # 运行、返回索引、结果
    SelectKeys:
    SelectTemplates: # 自定义选择模板
        Active:
        Inactive:
        Selected:
        Label:
    SelectWithAdd:
        AddLabel:
        Items:
        Label:
        Run():
    ValidateFunc:
```


### Prompt
```go
// 定义输入
prompt := promptui.Prompt{
    Label:       "请输入姓名",
    // 关闭回显
    HideEntered: true,
}

// 运行
name, _ := prompt.Run()

// 打印结果
fmt.Println("\033[32mI \033[0m你的姓名为：" + name)
```

单行输入



### Select
```go
// 定义选择列表
sel := promptui.Select{
    Label:        "Select Day",
    HideSelected: true,
    Items: []string{"Monday", "Tuesday", "Wednesday"},
}

// 运行
index, result, _ := sel.Run()

// 打印结果
fmt.Printf("You choose %d %q\n", index, result)
```

选择列表