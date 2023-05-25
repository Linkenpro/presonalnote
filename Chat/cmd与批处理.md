```
# 打印文件夹内,png结尾的文件

for /r g:\产品设计Alan\平面素材\ %i in (*.png) do echo %i
```

bat脚本

```
@echo off
for /r f:\ %%i in (*.txt) do echo %%i
pause > nul
```

内部命令

外部命令，内部命令的功能拓展

打开远程桌面

```sh
mstsc

>通过调用C盘>Windows>System32>mstsc.exe
```

设置变量set

```
查看帮助信息
set /?

显示当前环境变量及其值
set

设置变量
set name=xxx

set xx 如下：打印name
set name

删除变量(等于空即删除)
set name=

表达式运算——set /a
set /a 5+7
set /a 5*7

接受用户输入信息——set /p
set /p c=""

```

###### 脚本文件__算术

```
REM 关闭回显

@echo off
set /a var=4*5
echo %var%
pause >nul

```

###### 脚本文件——接受用户输入脚本

```
@echo off
set /p var=请输入一个数字：
echo 您输入的数字是：%var%
pause >nul
```

###### 自定义窗口

```
title cmd demo 

改变窗口大小
mode  80,40

改变背景色
color /?

>>>
    0 = 黑色       8 = 灰色
    1 = 蓝色       9 = 淡蓝色
    2 = 绿色       A = 淡绿色
    3 = 浅绿色     B = 淡浅绿色
    4 = 红色       C = 淡红色
    5 = 紫色       D = 淡紫色
    6 = 黄色       E = 淡黄色
    7 = 白色       F = 亮白色
>>>

color 0E
color 7E

```

###### Ping命令

```
ping icmp icmp echo

获取ping延迟
ping www.baidu.com

ping网关
ping 192.168.1.1

持续不断的ping某主机
ping -t 主机名
Ctrl+C 退出

-n count 要发送的回显请求数

-l size 发送缓冲区大小

-a 解析地址为主机名
ping -a 192.168.1.1

hostname 主机名

-w timeout 等待每次回复的超时时间（毫秒）

-i TTL 生存时间
```

###### 实战——修复网络故障

- TCP/IP协议出错
- TCP/IP配置出错
- 物理故障
- 中毒等

检查

```
检查本地TCP/IP协议是否安装正常
ping 127.0.0.1(localhost)

检查网关连接是否畅通
ping 192.168.1.1

检查电脑与外部网络连接是否畅通
ping www.baidu.com

网关信息
ip config  
```

###### exit 跳出命令/rem注释

```
@echo off
rem 以下是主体代码，不会运行
echo hello world
exit  rem 直接跳出窗口
pause
```

###### goto跳转命令

```
@echo off
rem 以下是主体代码，不会运行
echo hello world
goto part1

:part1
echo i am ready to exit

pause
```

###### start运行命令

```
查看start命令的帮助 
start /?

打开文件夹（盘符）
start f:

添加参数
start /max f: 
start /min g:

打开文件
start f:\1.txt

注意路径空格
start D:\"Program Files (x86)"\Apowersoft\ApowerMirror\xxx.exe
```

拓展

```
创建文件夹
md f:\"aa bc"

打开文件目录
start "aa bc"

正确写法
start "" "aa bc"
```

###### 程序的互相调用——call

```
@echo off

rem 文件必须在同一个文件路径下才可以引用
call demo.bat

rem 写入完整路径才可
call f:\demo.bat

echo 引用完成
pause
```

###### 排序命令——sort
