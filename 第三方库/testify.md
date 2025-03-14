# testify

## 基础介绍

Go单元测试框架`github.com/stretchr/testify`
支持断言(Assert、Require)、测试套件Suite、模拟Mock


## 核心内容
```yaml
testify:
    assert: # 断言
        Assertions: # 断言对象
            Contains():
            Empty():
            Equal(): # 相等判断
            Error():
            False():
            Same():
            True():
            Nil():
            NotEqual():
            NotNil():
        New():
    http:
    mock:
        Anything:
        Arguments: # mock结果
            Error(): # 获取预设异常
            Get():
            String(): # 获取预设字符串
        Call: # mock调用
            Return(): # 调用返回值
            Run(): # 动态返回值、自定义返回
        Mock: # Mock模拟基类
            AssertCalled(): # 断言某个 Mock 方法被调用
            AssertExpectations(): # 断言所有的 Mock 方法都被调用
            AssertNotCalled(): # 断言某个 Mock 方法未被调用
            AssertNumberOfCalls():
            Called(): # 调用内部Mock方法
            On(): # 方法拦截
            WaitUntil():
    require: # 同assert、失败结束测试
        Assertions: # 强制断言
            NoError(): # 
        New():
    suite: # 测试套件
        Suite: # 测试套件基类
            Require(): # require对象
            Run(): #运行子测试
            SetupSuite(): # 所有测试前置操作
            SetupTest(): # 每个前置操作
            T(): # 开启子测试 testing.T，原生子测试
            TearDownSuite(): # 所有后置操作
            TearDownTest(): # 每个后置操作
        Run(): # 运行自定义测试套件
```

### Suite

测试套件

在 Testify 中，测试套件 (suite) 是一个结构体，继承 suite.Suite，并且需要使用 suite.Run(t, &TestSuite{}) 来运行



### Mock



#### Call



#### Argument