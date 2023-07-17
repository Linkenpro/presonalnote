2023/07/16

Flask入门

> Flask基础
>
> FlaskDemo项目：问答平台

Flask实战

> Flask正规项目：论坛实战（前后端分离）
>
> Flask正规项目：在线聊天系统（前后端分离+Websocket技术）
>
> 新特性：Flask异步开发（协程）

```python
# 从flask包中导入Flask类
from flask import Flask

# 使用Flask类创建一个app对象
# __name__:代表当前app.py这个模块
# 1.出现bug，可以帮助我们快速定位
# 2.对于寻找模板文件，有一个相对路径
app = Flask(__name__)

# 创建一个路由和视图函数的映射
# https://www.baidu.com
# /home/user/xx

@app.route('/')
def hello_world():
    return 'HelloWorld!'

# 如果当前文件作为一个主入口进行运行，则运行以下
if __name__ == '__main__':
    app.run()
```

1. debug模式

```python
  from flask import Flask
  
  app = Flask(__name__)
  
  @app.route('/')
  def hello_world():
      return 'HelloWorld!'
  
  if __name__ == '__main__':
      app.run(debug=True)	# 社区版本：开启方式
```
>
>    开启debug模式后，只要修改代码后保存，就会重新加载，不需要手动重启项目
>
>    开发时，出现bug，再浏览器器上就可以看到出错信息
>

2.修改host

> 主要作用：让其他电脑能访问我电脑上的flask项目
>
> Additional options： --host=0.0.0.0

3.修改port端口号

> Additional options： --host=0.0.0.0 --port=8000

视频05完成