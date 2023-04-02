##### 常见的反爬技术

- 检测User-Agent
- 检测IP请求频率
- 检测账户请求频率
- 检测Referer
- 设置Cookie钓鱼反爬
- 异步数据加载
- 字体反爬
- 多种网页HTML结构（随机）
- 网页的随机class属性（随机）

##### 爬虫技术

- 设置User-Agent
- 切换代理IP
- 切换账户
- 设置Referer
- 模拟异步数据界都的单请求
- 分布式爬虫技术
- 字体反爬的逆向操作
- 验证码的识别服务
- 简单的数据提取
- 人工智能识别网页

##### 爬虫响应可视化展示函数体

```python
def requests_view(response):
    # 导入浏览器的控制库
    import webbrowser
    request_url = response.url                              # 将响应的url取出，赋值给request_url
    base_url = '<head><base href="%s">'%(request_url)       # 格式化一个字符串， 格式是<head><base href="网页源链接">
    base_url = base_url.encode()                            # 讲网址编码，原因是这里操作的数据格式是字节
    content = response.content.replace(b"<head>", base_url) # 操作爬虫的content二进制内容，将<head>替换成<head><base href="网页源链接">
    # 写入一个本地html文件里
    tem_html = open('tmp.html', 'wb')                       # 打开本地文件，以二进制写的形式
    tem_html.write(content)                                 # 写入二进制的网页内容
    tem_html.close()                                        # 关闭文件
    # 使用浏览器打开页面
    webbrowser.open_new_tab("tmp.html")
```

小测试——百度网页

```python
import requests

url = 'https://www.baidu.com/'

# 函数模块
def requests_view(response):
    # 导入浏览器的控制库
    import webbrowser
    request_url = response.url                              # 将响应的url取出，赋值给request_url
    base_url = '<head><base href="%s">'%(request_url)       # 格式化一个字符串， 格式是<head><base href="网页源链接">
    base_url = base_url.encode()                            # 讲网址编码，原因是这里操作的数据格式是字节
    content = response.content.replace(b"<head>", base_url) # 操作爬虫的content二进制内容，将<head>替换成<head><base href="网页源链接">
    # 写入一个本地html文件里
    tem_html = open('tmp.html', 'wb')                       # 打开本地文件，以二进制写的形式
    tem_html.write(content)                                 # 写入二进制的网页内容
    tem_html.close()                                        # 关闭文件
    # 使用浏览器打开页面
    webbrowser.open_new_tab("tmp.html")

# 请求网页数据
resp = requests.get(url)
# 调用函数
requests_view(resp)
```

爬取boss直聘的数据

```python
import requests
from pprint import pprint

# 请求boss直接聘的json数据
url = 'https://www.zhipin.com/wapi/zpgeek/search/joblist.json'
# 请求头
headers = {
    'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/111.0.0.0 Safari/537.36',
    'referer': 'https://www.zhipin.com/web/geek/job?query=%E5%B7%A5%E4%B8%9A%E8%AE%BE%E8%AE%A1&city=101280100',
    'cookie': 'lastCity=101280100; wd_guid=c9fb1900-6a4b-4e02-b709-d802c407d43e; historyState=state; _bl_uid=9ql5Xf6Uydwne18dbo3L7e865Iey; __g=-; __fid=4289f4bb00c628d398766fe04e55e333; Hm_lvt_194df3105ad7148dcf2b98a91b5e727a=1680394057,1680398146; Hm_lpvt_194df3105ad7148dcf2b98a91b5e727a=1680398173; wt2=D9N6R8kl7ymCExKAg2tTWHo5dTWIAQbtQeYOkGwDM-mI7quRhWrurs8aBw9mV4Av6CKm5_5X_-vu39Y1A_2v_oA~~; wbg=0; __zp_stoken__=b67aeMXw8Zy5NSi4tCytYai4QbTxneks4Il0qMStYAlVjdDciSyklIkF9PDIiI11jHiYJLVFsJCBdYSAEVnxZOwkjWjUkU3VrGmI9S3NoRntFQXMaRjJfSCgTCEI+OXgWXB87ViBEUFhtXSU=; __c=1680398135; __l=l=/www.zhipin.com/web/geek/job?query=%E5%B7%A5%E4%B8%9A%E8%AE%BE%E8%AE%A1&city=101280100&r=&g=&s=3&friend_source=0&s=3&friend_source=0; __a=41838247.1680394057.1680396106.1680398135.13.4.9.13; geek_zp_token=V1R94vGeX00ltgXdNhzxkYKy6z6znXxA~~',
    'zp_token': 'V1R94vGeX00ltgXdNhzxkYKyK17D7SxA~~',
    }
# 参数
payload = {
    'scene': 1,
    'query': '工业设计',
    'city': 101280100,
    'page': 1,
    'pageSize': 30,
    }

# 发送GET请求
resp = requests.get(url, headers=headers, params=payload)
# 打印状态码
pprint(resp.json())

>>>
{'code': 37,
 'message': '您的访问行为异常.',
 'zpData': {'name': '2d9713a7',
            'seed': 'sIDNq3jPKuY1phsICh1LyU4LmBodJczWvQVjipiQ7cY=',
            'ts': 1680402292818}}

# 以上暂时无法解决
```

准备测试2——爬取前程无忧

```
https://cupid.51job.com/open/noauth/search-pc?api_key=51job&timestamp=1680403111&keyword=工业设计&searchType=2&function=&industry=&jobArea=030200&jobArea2=&landmark=&metro=&salary=&workYear=01,06&degree=&companyType=&companySize=&jobType=&issueDate=&sortType=0&pageNum=1&requestId=&pageSize=50&source=1&accountId=&pageCode=sou|sou|soulb
```

