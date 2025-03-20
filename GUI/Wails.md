# Wails


## 基础介绍

webview GUI库
目前最新v3，稳定版仍旧v2



Wails2不支持多窗口、Wails3支持



### 项目结构
```yaml
项目结构:
    /build:
    /frontend:
        /dist:
        /src:
        /wailsjs: # go生成代码目录
            /go:
            /runtime:
        /index.html:
        tsconfig.json:
        tsconfig.node.json:
        vite.config.ts:
    app.go:
    go.mod:
    main.go:
    wails.json:
```


#### wails
```yaml
wails:
    dev: # 开发运行
    doctor:
    init:
        -n:
        -t:
```


#### wails.json
```yaml
wails.json:
    $schema:
    author:
    frontend:build:
    frontend:dev:serverUrl:
    frontend:dev:watcher:
    frontend:install:
    name:
    outputfilename:
```


### v3项目结构
```yaml
项目结构:
    /build:
        /darwin:
        /linux:
        /windows:
            /nsis:
                project.nsi:
            Taskfile.yml:
            wails.exe.manifest:
        appicon.png:
        config.yml:
        Taskfile.yml:
    /frontend: # 前端项目
        /bindings: # 绑定生成代码
            /changeme:
        /node_modules:
        /public:
        index.html:
        main.js:
        package.json:
    go.mod:
    main.go:
    Taskfile.yml:
```

#### wails3
```yaml
wails:
    build:
    dev:
    init:
        -n:
    package:
    version:
```


#### Taskfile.yml
```yaml
Taskfile.yml:
    
```










## 核心内容
```yaml
wails/v2:
    cmd:
        wails:
            Run(): # 运行应用
    pkg:
        applicatioin:
            Application:
                Bind():
                Quit():
                Run():
            New():
            NewWithOptions():
        assetserver:
            AssetServer: # 资源服务
            Options:
                Assets:
        menu:
            Menu: # 菜单类
            MenuItem:
            TrayMenu:
        options:
            App: # 应用类
                AssetServer:
                BackgroundColour:
                Bind: # 函数绑定
                Height:
                Menu: # 菜单
                OnStartUp:
                Title:
                Width:
        runtime:
            DialogType:
            FileFilter:
            OpenDialogOptions:
            Screen:
            BrowserOpenURL():
            ClipboardGetText():
            ClipboardSetText():
            EventsEmit(): # 触发事件
            EventsOff(): # 
            EventsOffAll(): # 
            EventsOn(): # 事件监听
            EventsOnce(): # 
            Hide():
            LogDebug():
            MenuSetApplicatioinMenu():
            MenuUpdateApplicationMenu():
            MessageDialog():
            OnFileDrop():
            OnFileDropOff():
            OpenFileDialog():
            OpenMultipleFilesDialog():
            Quit():
            SaveFileDialog():
            Show():
            WindowExecJs(): # 执行js代码
            WindowFullscreen():
            WindowHide(): # 隐藏窗口
            WindowReload():
            WindowShow(): # 显示窗口
            WindowSetTitle():
wailsjs:
    go:
    runtime:
        EventsEmit(): # 触发事件
        


wails/v3/pkg/application:
    App: # 应用类
        BrowserOpenFile():
        BrowserOpenURL():
        Clipboard():
        CurrentWindow():
        EmitEvent(): # 发送事件
        Environment():
        GetPrimaryScreen():
        GetScreens():
        GetWindowByName():
        NewMenu():
        OnApplicationEvent():
    ApplicationEvent: # 应用事件
    ApplicationEventContext:
    Button:
    Clipboard:
    CustomEvent:
    EventListener:
    EventProcessor:
    MacOptions:
    Menu: # 菜单类
    MenuItem:
    MessageDialog:
    Middleware:
    Options: # 应用配置类
        Assets: 
        Description:
        Name:
        Services: # 绑定服务
    Path:
    QueryParams:
    Screen:
    Service: # 绑定服务函数
    SystemTray: # 系统托盘类
    Theme:
    ThemeSettings:
    WebviewWindow: # 浏览器窗口类
        SetURL():
    WebviewWindowOptions:
        BackgroundColour:
        Height:
        Title:
        URL:
        Width:
    Window: # 窗口类
    WindowEvent:
    New():
    NewRGB:
    NewService(): # 新建服务函数
    NewSystemTray():
    NewWebviewWindow():
    NewWebviewWindowWithOptions():
@wailsio/runtime:
    Call:
    Create:
    Events:
        On():
```


### Service

通过绑定服务，前端可调用go语言函数



### Event

事件通信机制