cmd

```cmd
set /?
```

echo

```cmd
echo hello world

@echo off
```

pause

```cmd

```

ping

```cmd

```

rem

```cmd
rem 注释
```

start

```cmd
start /max d:\

start /min d:\
```

call

```
不同程序的调用
```

sort

```
排序
```

特殊字符

```
|
&

```

shutdown

```
/s

/p
```

telnet

```cmd
查看端口是否开放
```

copy

```cmd
rem 复制文件
copy E:\Json\js.json E:\Json\js1.json
copy E:\Json\js.json E:\Json\js2.json
```

for循环

```cmd
for in do
```

模仿

```cmd
for /L %%a in (1 1 30) do copy E:\Json\js.json E:\Json\js%%a.json
```

复制文件，按顺序命名

```cmd
@echo off  
echo "复制文件........."  
echo.  
rem 复制文件
for /L %%a in (1 1 30) do copy E:\Json\js.json E:\Json\js%%a.json
pause>nul
```

