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

##4、远程调试
###4.1 创建软链
ln -s $HOME/go/bin/dlv /usr/local/bin/dlv

###4.2 查看dlv信息
dlv version

Delve Debugger
Version: 1.8.0
Build: $Id: 6a6c9c332d5354ddf1f8a2da3cc477bd18d2be53

###4.3 配置Goland远程调试
在goland打开go项目，在右上角点击Edit Configurations，在弹出的配置框中左上角点击 + ，选择Go Remote
Host改成服务器ip，如127.0.0.1
Port改成服务器端口，如9100
![goland_remote](./images/goland_remote.png)
保存 后 Debug go remote

###4.4 终止dlv和go程序
dlv不终止, 则 go程序也无法终止 而dlv只能通过终止进程的方式终止掉
kill -9 `ps -ef | grep "dlv|test" -E | awk '{print $2}'`