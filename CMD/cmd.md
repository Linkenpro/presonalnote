###### cmd查看命令

```cmd
set /?
rem 查看相关说明
```

###### echo

```cmd
echo hello world

@echo off
rem 默认情况下，批处理文件会在运行时显示其命令。第一条命令的目的是关闭显示。echo off "命令会关闭整个脚本的显示，但 "echo off "命令本身除外。前面的 "at "符号"@"使该命令也适用于它自己。
```

###### set

```cmd
# set /a 等号右边的字符串为被评估的数字表达式,就是表示计算
set /A variable-name=value

# 例子-打印message变量
@echo off 
set message=Hello World 
echo %message%

# 提供一个交互界面 set /p
set /p var=请输入你的名字: 

```

```cmd
@echo off 
SET /A a = 5 
SET /A b = 10 
SET /A c = %a% + %b% 
echo %c% 
SET /A c = %a% - %b% 
echo %c% 
SET /A c = %b% / %a% 
echo %c% 
SET /A c = %b% * %a% 
echo %c%
```

###### pause

```cmd
pause 
rem 暂停
```

###### ping

```cmd

```

###### rem

```cmd
rem 注释
```

###### start

```cmd
start /max d:\

start /min d:\
```

###### call

```
不同程序的调用
```

###### sort

```
排序
```

特殊字符

```
|
&

```

###### shutdown

> 关机

```cmd
/s

/p

rem 定时关机，2个小时后
shutdown /s /t 7200
```

###### telnet

```cmd
查看端口是否开放
```

###### copy

```cmd
rem 复制文件
copy E:\Json\js.json E:\Json\js1.json
copy E:\Json\js.json E:\Json\js2.json
```

###### for

> 循环

```cmd
for in do
```

> 练习
>

```cmd
for /L %%a in (1 1 30) do copy E:\Json\js.json E:\Json\js%%a.json
```

复制文件，按顺序命名

```cmd
@echo off
chcp 65001
echo "复制文件........."  
echo.  
rem 复制文件
for /L %%a in (1 1 30) do copy E:\Json\js.json E:\Json\js%%a.json
pause>nul
```

删除当前目录中的所有文件

```cmd
:: Deletes All files in the Current Directory With Prompts and Warnings
::(Hidden, System, and Read-Only Files are Not Affected)
:: @ECHO OFF
DEL . DR
```

```cmd
:: 删除当前目录中的所有文件
::(隐藏、系统和只读文件不受影响) 
:: 
@ECHO OFF 
DEL . 
DR
```

###### dir

```cmd
@echo off 
Rem 列出 Program files 目录中的所有文件
dir "C:\Program Files" > C:\lists.txt
echo "程序完成！"
pause
```

> 创建空白文件夹

```cmd
@echo off
Rem 序号8-27的文件夹
for /l %%i in (8,1,27) do (
  mkdir "%%i"
)
```

###### rmdir

> 删除文件夹，完整案例

```cmd
@echo off
chcp 65001

echo 删除文件夹......
rmdir /s /q D:\Bilibili_download
rmdir /s /q D:\DiskGenius
rmdir /s /q D:\Kugou
echo 删除完成！
pause
```

- `/s` 表示删除指定目录以及其中的所有子目录和文件。
- `/q` 表示以静默模式执行，即不会询问确认。

> chcp 65001——解决中文显示乱码问题
>
> bat代码如何处理中文目录
>
> 使用——VSCode解决文本编辑生成的中文乱码问题

###### 例子2

```
rmdir /s /q F:\Git
rmdir /s /q D:\F
rmdir /s /q D:\Kugou
rmdir /s /q D:\M3U8
rmdir /s /q D:\m3u8DL
rmdir /s /q D:\Materialize

```

