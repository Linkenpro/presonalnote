> 项目地址：
>
> ```
> https://gitee.com/g1879/DrissionPage
> ```
>
> 安装
>
> ```
> pip install DrissionPage
> ```

设置浏览器

```python
from DrissionPage.easy_set import set_paths

set_paths(browser_path=r'C:\Program Files\Google\Chrome\Application\chrome.exe')
```

开始案例

```python
from DrissionPage import ChromiumPage

page = ChromiumPage()
page.get('https://www.baidu.com')
```

##### 对比selenium

###### 案例一：用显性等待方式查找第一个文本包含 some text 的元素。

```python
# 使用 selenium：
element = WebDriverWait(driver).until(ec.presence_of_element_located((By.XPATH, '//*[contains(text(), "some text")]')))

# 使用 DrissionPage：
element = page('some text')
```

###### #案例二：跳转到第一个标签页

```python
# 使用 selenium：
driver.switch_to.window(driver.window_handles[0])

# 使用 DrissionPage：
page.to_tab(0)
```

###### # 案例三：拖拽一个元素

```python
# 使用 selenium：
ActionChains(driver).drag_and_drop(ele1, ele2).perform()

# 使用 DrissionPage：
ele1.drag_to(ele2)
```

##### 对比requests

###### 案例一：获取元素内容

```python
url = 'https://baike.baidu.com/item/python'

# 使用 requests：
from lxml import etree
headers = {'User-Agent':'Mozilla/5.0 (Windows NT 6.3; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/41.0.2272.118 Safari/537.36'}

response = requests.get(url, headers = headers)
html = etree.HTML(response.text)
element = html.xpath('//h1')[0]
title = element.text

# 使用 DrissionPage：
page = WebPage('s')
page.get(url)
title = page('tag:h1').text

```

##### DrissionPage不同模式切换

> 用浏览器登录网站，然后切换到 requests 读取网页。两者会共享登录信息。

```python
from DrissionPage import WebPage
from time import sleep

# 创建页面对象，默认 d 模式
page = WebPage()  
# 访问个人中心页面（未登录，重定向到登录页面）
page.get('https://gitee.com/profile')  

# 使用 selenium 输入账号密码登录
page.ele('@id:user_login').input('your_user_name')  
page.ele('@id:user_password').input('your_password\n')
sleep(1)

# 切换到 s 模式
page.change_mode()  
# 登录后 session 模式的输出
print('登录后title：', page.title, '\n')  

```

————入门

###### 案例——在百度搜搜“Drissionpage”，并打印结果。

```python
# 导入
from DrissionPage import ChromiumPage

# 创建对象
page = ChromiumPage()

# 访问网页
page.get('https://www.baidu.com')
# 输入文本
page('#kw').input('DrissionPage')
# 点击按钮
page('#su').click()

# 等待页面跳转
page.wait.load_start()

# 获取所有结果
links = page.eles('tag:h3')
# 遍历并打印结果
for link in links:
    print(link.text)

#例子——等待3秒后，点击下一页
time.sleep(3)
page('.n').click()
```

例题——点击下一页

> .是class的简化写法

```

```

