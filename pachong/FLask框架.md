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

2023/7/17

```python
from flask import Flask, request
  
app = Flask(__name__)
    
# url: http[80]/https[443]://www.baidu.com:443(浏览器自动补齐端口)/path
# url与视图： path与视图
  
@app.route('/')
def hello_world():
    return 'HelloWorld!'

@app.route("/profile")
def profile():
    return "我是个人中心！"

@app.route("/blog/list")
def blog_list():
    return "我是博客列表！"

@app.route("/blog/<blog_id>")
# @app.route("/blog/<int:blog_id>")
def blog_detail(blog_id):
    return "您访问的博客是：%s" % blog_id

# 除了定义int类型，还有string，float，path，uuid，any

# /book/list: 会给我返回第一页的数据
# /book/list?page=2: 获取第二页的数据
@app.route("/book/list")
def book_list():
    # arguments: 参数
    # request.args: 类字典类型
    page = request.args.get("page", default=1, type=int)
    return f"您获取的是第{page}的图书列表！"

if __name__ == '__main__':
    app.run(debug=True)	# 社区版本：开启方式
```

Jinja2

```python
from flask import Flask, render_template
  
app = Flask(__name__)
  
@app.route('/')
def hello_world():
    return render_template("index.html")

@app.route("/blog/<blog_id>")
def blog_detail(blog_id):
    return render_template("blog_detail.html", blog_id=blog_id, username="知了")

# <h1>您访问的博客详情是：{{blog_id}}</h1>
  
if __name__ == '__main__':
    app.run(debug=True)	# 社区版本：开启方式
```

```
templates
>>>
	index.html
	blog_detail.html
```

08课补充

Jinja2

```python
from flask import Flask, render_template
  
app = Flask(__name__)

class User:
    def __init__(self,username,email):
        self.username = username
        self.email = email
  
@app.route('/')
def hello_world():
    user = User(username="知了", email="xx@qq.com")
    person = {
        "username": "张三"，
        "email": "zhangsan@qq.com"
    }
    return render_template("index.html", user=user)

@app.route("/blog/<blog_id>")
def blog_detail(blog_id):
    return render_template("blog_detail.html", blog_id=blog_id, username="知了")

# <div> {{ user.username }} / {{ user.username }} </div>
# <div> {{ person['username'] }} / {{ person.username }} </div>
  
if __name__ == '__main__':
    app.run(debug=True)	# 社区版本：开启方式
```

Jinja2过滤器

```python
from flask import Flask, render_template
from datetime import datetime
  
app = Flask(__name__)

# 自定义过滤器
# format="%Y年%m月%d日 %H:%M"
def date_formate(value, format="%Y-%d-%m %H:%M"):
    return value.strftime(format)

app.add_template_filter(datetime_format, "dformat")

class User:
    def __init__(self,username,email):
        self.username = username
        self.email = email
  
@app.route('/')
def hello_world():
    user = User(username="知了", email="xx@qq.com")
    person = {
        "username": "张三"，
        "email": "zhangsan@qq.com"
    }
    return render_template("index.html", user=user)

@app.route("/blog/<blog_id>")
def blog_detail(blog_id):
    return render_template("blog_detail.html", blog_id=blog_id, username="知了")

@app.route("/filter")
def filter_demo():
    user = User(username="知了", email="xx@qq.com")
    mytime = datetime.now()
    return render_template("filter.html", user=user, mytime=mytime)
    
if __name__ == '__main__':
    app.run(debug=True)	# 社区版本：开启方式
```

filter.html——过滤器的使用

```html
<body>
<div> {{ user.username}}-{{ user.username|length }} </div>
/过滤器/
<div> {{ user.username|length }} </div>
</body>
```

09节完成