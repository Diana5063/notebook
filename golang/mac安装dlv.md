#Mac安装Go语言调试工具dlv
环境：macOS Big Sur(版本：11.6)

##1、安装(根据官网指导：https://github.com/go-delve/delve)

go install github.com/go-delve/delve/cmd/dlv@latest

在终端输入dlv,出现如下反馈消息,说明dlv工具安装成功

Delve is a source level debugger for Go programs.

Delve enables you to interact with your program by controlling the execution of the process,
evaluating variables, and providing information of thread / goroutine state, CPU register state and more.

The goal of this tool is to provide a simple yet powerful interface for debugging Go programs.
...


##2、配置goland
在goland打开go项目，在右上角点击Edit Configurations，在弹出的配置框中填写信息
![goland_dlv配置](./images/goland_dlv配置.png)

##3、调试
![goland_debug](./images/goland_debug.png)

在代码需要调试的位置打断点，如图中红色圆点所示，然后点击绿色的三角形，选择Debug...选项进行调试，可得到调试结果。