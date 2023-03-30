提取md文件中的url

下载url位置里的图片

替换md文件中文件的img链接为本地文件

保存文件

###### 源代码

```python
import re

# 将文件内容读入字符串列表
with open('GH运算器.md', mode='r', encoding='utf-8') as file:
    lines = file.readlines()

# 遍历字符串列表
for line in lines:
    # 使用正则表达式提取 URL
    #urls = re.findall('http[s]?://(?:[a-zA-Z]|[0-9]|[$-_@.&+]|[!*\(\),]|(?:%[0-9a-fA-F][0-9a-fA-F]))+', line)
    # 正则匹配括号内的内容
    urls = re.findall(r"(?<=\()[^)]+(?=\))", line)
    # 遍历 URL 列表并提取网页内容
    for url in urls:
        print(url)

```

