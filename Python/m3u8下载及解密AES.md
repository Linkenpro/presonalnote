###### 抓取代码1

```python
import requests
import re
# 导入序列化模块
import json
from pprint import pprint
# 导入AES
from Cryptodome.Cipher import AES
# 导入进度条模块
from tqdm import tqdm


def get_response(html):
    """
    模拟浏览器，发送请求函数
    """
    #请求头
    headers = {
        'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.0.0 Safari/537.36'
        }

    # 发送请求，获取响应对象
    response = requests.get(url=html, headers=headers)

    # 返回值
    return response

def get_m3u8(html):
    """获取m3u8链接"""
    html_data = get_response(html=html).text
    # 解析提取标题/ m3u8链接
    title = re.findall(pattern:'')
    info = re.findall(pattern:'')
    # 转换成字典
    json_data = json.loads(info)
    # m3u8地址
    m3u8_url = json_data['url']
    # 获取m3u8的数据
    m3u8_data = get_response(html=m3u8_url).text
    # 返回值
    return m3u8_url, m3u8_data, title

def get_ts(m3u8_url, data, title):
    """获取ts文件，并且解密"""

    # 提取ts的链接
    ts_list = re.sub(pattern:'#E.*', repl:'', data).split()
    # 密钥 https://s.xlzys.com/play/QeZpzYJb/enc.key
    key1 = re.findall('URI="(.*?)"', data)[0]
    # 密钥id
    key_id = m3u8_url.split('/')[-2]
    # 密钥链接
    key_url = f'https://s.xlzys.com/play/{key_id}/{key1}'
    # 获取密钥
    key = get_response(html=key_url).content
    # 解码器
    ci = AES.new(key, AES.MODE_CBC)

    # 提取解码
    for ts in tqdm(ts_list):
        # 获取视频内容
        ts_content = get_response(html=ts).content
        # 解密数据
        content = ci.decrypt(ts_content)
        with open(f'{title}.mp4', mode='ab') ad f:
            f.write(content)
    
# 网页地址
networkUrl = 'https://study.163.com/course/courseMain.htm?courseId=1209509824&share=1&shareId=1386467372'

# 函数入口，当你的文件被当作模块调用时，下面的代码不会执行
if __name__ == '__main__':
    # 调用函数
    m3u8_url, m3u8_data, title = get_m3u8(html='')
    get_ts(m3u8_url=m3u8_url, data=m3u8_data, title=title)
```

拆解网易云视频加密

```python
import requests
import time
from pprint import pprint

# m3u8链接
m3u8_url = 'https://jdvodluwytr3t.stu.126.net/nos/ept/hls/2019/10/16/1215248188_df4533024e9a40038e06527d8e589f84_eshd.m3u8'

# 获取13位时间1699838244691时间戳
ms_time = int(time.time()*1000)

# 请求头
headers = {
    'User-Agent': "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.0.0 Safari/537.36"
    }
# 传参
payload = {
    'ak': '7909bff134372bffca53cdc2c17adc27a4c38c6336120510aea1ae1790819de8ed33ac9c43dd73f6e19b71b0095261b51b81a1c5ef77158d30bdc2bacde682c67141b504489213a8ca8e47eaee23303f108dcfb9efdcac0300df2ae8173c01bae5eb0b27efe9e27051e5a0754075b88de6fc2ae2e15a00d5fd833ea365cf99f418ee2acb0c2e4fb41b82eb269fcd0d4e',
    'token': 'https://vod.study.163.com/eds/api/v1/vod/hls/key?id=1215248188&token=190764619a66db0b9c75100023c9128577544b9cb025a2743e81ca002f942eeb4b36cc5724c9b7af612f72e8ceea9f16276da52cd244a7c03654bf366305208498290cc470eebbf5133633b8d84ac9205eddf2cddc3736f9d4b14f470f2de509671e1bf5f8aa9769ad15bef447b747e37a42404d535868f94a5b4533c2e69801',
    't': ms_time
    }


# 获取请求
resp = requests.get(m3u8_url, headers=headers, params=payload)
# 获取m3u8的数据
m3u8_data = resp.text

# 检测点
pprint(m3u8_data)
```

m3u8data

```
#EXTM3U
#EXT-X-VERSION:3
#EXT-X-TARGETDURATION:10
#EXT-X-MEDIA-SEQUENCE:0
#EXT-X-KEY:METHOD=AES-128,URI="https://vod.study.163.com/eds/api/v1/vod/hls/key?id=1215248188&token=d658862b093276615580310b6ea01f6cb0f811d0660fda101f03f9bd8b1bf9994b36cc5724c9b7af612f72e8ceea9f16146e6158d1398dade9962548580dcae3e80b8ea9a6e87587ab3001ff95d38a71142652ae694430971c0801bb2cdae5a3671e1bf5f8aa9769ad15bef447b747e37a42404d535868f94a5b4533c2e69801"
#EXT-CUSTOM-YUNXIN:ntsversion=0,ntsprivatedata=8b72b2cf9b478ef83c526808dc91669ec9df8cc9
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd0.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd1.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd2.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd3.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd4.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd5.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd6.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd7.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd8.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd9.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd10.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd11.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd12.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd13.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd14.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd15.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd16.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd17.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd18.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd19.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd20.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd21.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd22.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd23.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd24.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd25.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd26.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd27.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd28.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd29.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd30.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd31.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd32.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd33.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd34.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd35.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd36.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd37.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd38.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd39.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd40.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd41.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd42.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd43.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd44.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd45.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd46.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd47.ts
#EXTINF:10.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd48.ts
#EXTINF:2.000000,
1215248188_df4533024e9a40038e06527d8e589f84_eshd49.ts
#EXT-X-ENDLIST
```

```
token='d658862b093276615580310b6ea01f6cb0f811d0660fda101f03f9bd8b1bf9994b36cc5724c9b7af612f72e8ceea9f16146e6158d1398dade9962548580dcae3e80b8ea9a6e87587ab3001ff95d38a71142652ae694430971c0801bb2cdae5a3671e1bf5f8aa9769ad15bef447b747e37a42404d535868f94a5b4533c2e69801'
```

错误版本

```python
import requests
import time
import re
from pprint import pprint
# 导入AES
from Crypto.Cipher import AES
# 导入进度条模块
from tqdm import tqdm

# m3u8链接
m3u8_url = 'https://jdvodluwytr3t.stu.126.net/nos/ept/hls/2019/10/16/1215248188_df4533024e9a40038e06527d8e589f84_eshd.m3u8'
# 网页长参数
ak = '7909bff134372bffca53cdc2c17adc27a4c38c6336120510aea1ae1790819de8ed33ac9c43dd73f6e19b71b0095261b51b81a1c5ef77158d30bdc2bacde682c67141b504489213a8ca8e47eaee23303f108dcfb9efdcac0300df2ae8173c01bae5eb0b27efe9e27051e5a0754075b88de6fc2ae2e15a00d5fd833ea365cf99f418ee2acb0c2e4fb41b82eb269fcd0d4e'
token = 'https://vod.study.163.com/eds/api/v1/vod/hls/key?id=1215248188&token=190764619a66db0b9c75100023c9128577544b9cb025a2743e81ca002f942eeb4b36cc5724c9b7af612f72e8ceea9f16276da52cd244a7c03654bf366305208498290cc470eebbf5133633b8d84ac9205eddf2cddc3736f9d4b14f470f2de509671e1bf5f8aa9769ad15bef447b747e37a42404d535868f94a5b4533c2e69801'
# 视频标题
title = 'out'

# 默认请求头
headers = {
    'User-Agent': "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.0.0 Safari/537.36"
    }

def get_m3u8(m3u8_url):
    # 获取13位时间戳
    ms_time = int(time.time()*1000)
    # 传参
    payload = {
        'ak': ak,
        'token': token,
        't': ms_time
        }
    # 获取请求
    resp = requests.get(m3u8_url, headers=headers, params=payload)
    # 获取m3u8的数据
    m3u8_data = resp.text
    return m3u8_data

def get_ts(data, title):
    # 提取ts的链接
    ts_list = re.sub(pattern='#E.*', repl='', string=data).split()
    # URI密钥
    keyURI = re.findall('URI="(.*?)"', data)[0]
    # 密钥链接
    key_url = f'https://jdvodluwytr3t.stu.126.net/nos/ept/hls/2019/10/16/{keyURI}'
    # 获取密钥
    key = requests.get(key_url, headers=headers).content
    # 解码器
    ci = AES.new(key, AES.MODE_CBC)

    # 提取ts并解码
    for ts in tqdm(ts_list):
        # 获取视频内容
        ts_content = requests.get(ts, headers=headers).content
        # 解密数据
        content = ci.decrypt(ts_content)
        # 保存文件
        with open(f'{title}.mp4', mode='ab') as f:
            f.write(content)
        # 写入完成
        print('完成！')
            
# 调用函数
if __name__ == '__main__':
    # 保存m3u8的数据
    data = get_m3u8(m3u8_url)
    get_ts(data,title)
    

```

错误4

> 这个错误表明密钥的长度为 256 字节，但是 `Crypto.Cipher.AES.new` 函数期望的是合法的 AES 密钥长度。AES 密钥的合法长度应该是 16、24 或 32 字节（对应 128、192 或 256 位）。
>
> 在你的代码中，请确保你提供给 `AES.new` 函数的密钥长度是符合这些规格的。如果你的密钥是字符串形式，可以使用以下方式生成合法长度的密钥：

```python
import requests
import time
import re
from pprint import pprint
# 导入AES
from Crypto.Cipher import AES
# 导入进度条模块
from tqdm import tqdm

# m3u8链接
m3u8_url = 'https://jdvodluwytr3t.stu.126.net/nos/ept/hls/2019/10/16/1215248188_df4533024e9a40038e06527d8e589f84_eshd.m3u8'
# 网页长参数
ak = '7909bff134372bffca53cdc2c17adc27a4c38c6336120510aea1ae1790819de8ed33ac9c43dd73f6e19b71b0095261b51b81a1c5ef77158d30bdc2bacde682c67141b504489213a8ca8e47eaee23303f108dcfb9efdcac0300df2ae8173c01bae5eb0b27efe9e27051e5a0754075b88de6fc2ae2e15a00d5fd833ea365cf99f418ee2acb0c2e4fb41b82eb269fcd0d4e'
token = 'https://vod.study.163.com/eds/api/v1/vod/hls/key?id=1215248188&token=190764619a66db0b9c75100023c9128577544b9cb025a2743e81ca002f942eeb4b36cc5724c9b7af612f72e8ceea9f16276da52cd244a7c03654bf366305208498290cc470eebbf5133633b8d84ac9205eddf2cddc3736f9d4b14f470f2de509671e1bf5f8aa9769ad15bef447b747e37a42404d535868f94a5b4533c2e69801'
# 视频标题
title = 'out'

# 默认请求头
headers = {
    'User-Agent': "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.0.0 Safari/537.36"
    }

def get_m3u8(m3u8_url):
    # 获取13位时间戳
    ms_time = int(time.time()*1000)
    # 传参
    payload = {
        'ak': ak,
        'token': token,
        't': ms_time
        }
    # 获取请求
    resp = requests.get(m3u8_url, headers=headers, params=payload)
    # 获取m3u8的数据
    m3u8_data = resp.text
    return m3u8_data

def get_ts(data, title):
    # 提取ts的链接
    ts_list = re.sub(pattern='#E.*', repl='', string=data).split()
    # 去出URI密钥
    keyURI = re.findall('URI="(.*?)"', data)[0]
    # 使用正则表达式提取 token
    match = re.search(r'token=([^&]+)', keyURI)
    if match:
        key = match.group(1)
        print(len(key))
    else:
        print("Token not found.")
        
    # 解码器
    ci = AES.new(key, AES.MODE_CBC)

    # 提取ts并解码
    for ts in tqdm(ts_list):
        # 获取视频内容
        ts_content = requests.get(ts, headers=headers).content
        # 解密数据
        content = ci.decrypt(ts_content)
        # 保存文件
        with open(f'{title}.mp4', mode='ab') as f:
            f.write(content)
        # 写入完成
        print('完成！')
            
# 调用函数
if __name__ == '__main__':
    # 保存m3u8的数据
    data = get_m3u8(m3u8_url)
    get_ts(data,title)
    
```

###### 错误5

```python
import requests
import time
import re
from pprint import pprint
# 导入AES
from Crypto.Cipher import AES
# 导入进度条模块
from tqdm import tqdm

# m3u8链接
m3u8_url = 'https://jdvodluwytr3t.stu.126.net/nos/ept/hls/2019/10/16/1215248188_df4533024e9a40038e06527d8e589f84_eshd.m3u8'
# 网页长参数
ak = '7909bff134372bffca53cdc2c17adc27a4c38c6336120510aea1ae1790819de8ed33ac9c43dd73f6e19b71b0095261b51b81a1c5ef77158d30bdc2bacde682c67141b504489213a8ca8e47eaee23303f108dcfb9efdcac0300df2ae8173c01bae5eb0b27efe9e27051e5a0754075b88de6fc2ae2e15a00d5fd833ea365cf99f418ee2acb0c2e4fb41b82eb269fcd0d4e'
token = 'https://vod.study.163.com/eds/api/v1/vod/hls/key?id=1215248188&token=190764619a66db0b9c75100023c9128577544b9cb025a2743e81ca002f942eeb4b36cc5724c9b7af612f72e8ceea9f16276da52cd244a7c03654bf366305208498290cc470eebbf5133633b8d84ac9205eddf2cddc3736f9d4b14f470f2de509671e1bf5f8aa9769ad15bef447b747e37a42404d535868f94a5b4533c2e69801'
# 视频标题
title = 'out'

"""处理token"""
# 密钥网址
key_url = re.search(r'https://[^?]+', token).group()
# ID头
t_id = re.search(r'id=(\d+)', token).group(1)
# token解钥
token2 =re.search(r'token=([^&]+)', token).group(1)

# token_payload 的参数
t_payload = {
    'id': t_id,
    'token': token2
    }

# 默认请求头
headers = {
    'User-Agent': "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.0.0 Safari/537.36"
    }

def get_m3u8(m3u8_url):
    # 获取13位时间戳
    ms_time = int(time.time()*1000)
    # 传参
    payload = {
        'ak': ak,
        'token': token,
        't': ms_time
        }
    # 获取请求
    resp = requests.get(m3u8_url, headers=headers, params=payload)
    # 获取m3u8的数据
    m3u8_data = resp.text
    return m3u8_data

def get_ts(data, title, key_url, t_payload):
    # 提取ts的链接
    ts_list = re.sub(pattern='#E.*', repl='', string=data).split()
    # 去出URI密钥
    keyURI = re.findall('URI="(.*?)"', data)[0]
    # 获取密钥
    key = requests.get(key_url, headers=headers, params=t_payload).content
        
    # 解码器
    ci = AES.new(key, AES.MODE_CBC)

    # 提取ts并解码
    for ts in tqdm(ts_list):
        # 获取视频内容
        ts_content = requests.get(ts, headers=headers).content
        # 解密数据
        content = ci.decrypt(ts_content)
        # 保存文件
        with open(f'{title}.mp4', mode='ab') as f:
            f.write(content)
        # 写入完成
        print('完成！')
            
# 调用函数
if __name__ == '__main__':
    # 保存m3u8的数据
    data = get_m3u8(m3u8_url)
    get_ts(data, title, key_url, t_payload)
    
```

单独测试

```python
import requests

url = 'https://vod.study.163.com/eds/api/v1/vod/hls/key'

params = {
    'id': 1215248188,
    'token': 'd658862b093276615580310b6ea01f6cb0f811d0660fda101f03f9bd8b1bf9994b36cc5724c9b7af612f72e8ceea9f16146e6158d1398dade9962548580dcae3e80b8ea9a6e87587ab3001ff95d38a71142652ae694430971c0801bb2cdae5a3671e1bf5f8aa9769ad15bef447b747e37a42404d535868f94a5b4533c2e69801'}

headers = {
    'Origin': 'https://study.163.com',
    'Referer': 'https://study.163.com/',
    'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.0.0 Safari/537.36'
    }
resp = requests.get(url, headers=headers, params=params)

print(resp.content)
```

###### 错误6

```python
import requests
import time
import re
from pprint import pprint
# 导入AES
from Crypto.Cipher import AES
# 导入进度条模块
from tqdm import tqdm

# m3u8链接
m3u8_url = 'https://jdvodluwytr3t.stu.126.net/nos/ept/hls/2019/10/16/1215248188_df4533024e9a40038e06527d8e589f84_eshd.m3u8'
# 网页长参数
ak = '7909bff134372bffca53cdc2c17adc27a4c38c6336120510aea1ae1790819de8ed33ac9c43dd73f6e19b71b0095261b51b81a1c5ef77158d30bdc2bacde682c67141b504489213a8ca8e47eaee23303f108dcfb9efdcac0300df2ae8173c01bae5eb0b27efe9e27051e5a0754075b88de6fc2ae2e15a00d5fd833ea365cf99f418ee2acb0c2e4fb41b82eb269fcd0d4e'
token = 'https://vod.study.163.com/eds/api/v1/vod/hls/key?id=1215248188&token=190764619a66db0b9c75100023c9128577544b9cb025a2743e81ca002f942eeb4b36cc5724c9b7af612f72e8ceea9f16276da52cd244a7c03654bf366305208498290cc470eebbf5133633b8d84ac9205eddf2cddc3736f9d4b14f470f2de509671e1bf5f8aa9769ad15bef447b747e37a42404d535868f94a5b4533c2e69801'
# 视频标题
title = 'out'

"""处理token"""
# token解钥
token2 =re.search(r'token=([^&]+)', token).group(1)


# 默认请求头
headers = {
    'User-Agent': "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.0.0 Safari/537.36"
    }

def get_m3u8(m3u8_url):
    # 获取13位时间戳
    ms_time = int(time.time()*1000)
    # 传参
    payload = {
        'ak': ak,
        'token': token,
        't': ms_time
        }
    # 获取请求
    resp = requests.get(m3u8_url, headers=headers, params=payload)
    # 获取m3u8的数据
    m3u8_data = resp.text
    return m3u8_data

def get_ts(data, title):
    # 提取ts的链接
    ts_list = re.sub(pattern='#E.*', repl='', string=data).split()
    # 去出URI密钥
    keyURI = re.findall('URI="(.*?)"', data)[0]
    # 将token2转换为bytes类型
    key = token2.encode()      
    # 解码器
    ci = AES.new(key, AES.MODE_CBC)

    # 提取ts并解码
    for ts in tqdm(ts_list):
        # 获取视频内容
        ts_content = requests.get(ts, headers=headers).content
        # 解密数据
        content = ci.decrypt(ts_content)
        # 保存文件
        with open(f'{title}.mp4', mode='ab') as f:
            f.write(content)
        # 写入完成
        print('完成！')
            
# 调用函数
if __name__ == '__main__':
    # 保存m3u8的数据
    data = get_m3u8(m3u8_url)
    get_ts(data, title)
```

###### 寻找解决方法失败

```
from Crypto.Cipher import AES
import requests

# 从 URI 获取密钥
key_uri = "https://vod.study.163.com/eds/api/v1/vod/hls/key?id=1215248188&token=190764619a66db0b9c75100023c9128577544b9cb025a2743e81ca002f942eeb4b36cc5724c9b7af612f72e8ceea9f16276da52cd244a7c03654bf366305208498290cc470eebbf5133633b8d84ac9205eddf2cddc3736f9d4b14f470f2de509671e1bf5f8aa9769ad15bef447b747e37a42404d535868f94a5b4533c2e69801"
response = requests.get(key_uri)
key = response.content

# 加密的数据
encrypted_data = b'190764619a66db0b9c75100023c9128577544b9cb025a2743e81ca002f942eeb4b36cc5724c9b7af612f72e8ceea9f16276da52cd244a7c03654bf366305208498290cc470eebbf5133633b8d84ac9205eddf2cddc3736f9d4b14f470f2de509671e1bf5f8aa9769ad15bef447b747e37a42404d535868f94a5b4533c2e69801'  # 你的加密数据

# 使用密钥进行解密
cipher = AES.new(key, AES.MODE_CBC, iv=b'\0' * 16)  # 注意：这里使用了 CBC 模式和一个零向量作为初始向量
decrypted_data = cipher.decrypt(encrypted_data)

print("Decrypted Data:", decrypted_data)

```

ffmpeg下载视频

```
ffmpeg.exe -user_agent "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/119.0.0.0 Safari/537.36" -i https://jdvodluwytr3t.stu.126.net/nos/ept/hls/2019/10/02/1215197861_a4ba13766c73473da1a3eaf3e190fee4_eshd.m3u8 -c copy -bsf:a aac_adtstoasc -movflags +faststart download1.mp4
```

> 遇到403报错的加一个 浏览器伪装就可以解决了

执行以下命令解密M3U8文件

```
ffmpeg -i input.m3u8 -c copy -bsf:a aac_adtstoasc -hls_key_info_file key_info.keyinfo output.mp4
```

```
# 输入密钥网址
ffmpeg -i https://jdvodluwytr3t.stu.126.net/nos/ept/hls/2019/10/02/1215197861_a4ba13766c73473da1a3eaf3e190fee4_eshd.m3u8 -c copy -bsf:a aac_adtstoasc -hls_key_info_file <(echo "<key><uri>https://vod.study.163.com/eds/api/v1/vod/hls/key?id=1215197861&token=05fb375cf80232f24caf09eb34de6df0c1d15aca0647fad9aff9f3a2cccdb70cca02fff9199a5fdf19f0213738b6af603e269e35c2262e666e4986a28a4f554953dba6799bbecee1bf90934c7457b178d5962ba63ecf57de47ce5cfa456fbccb671e1bf5f8aa9769ad15bef447b747e37a42404d535868f94a5b4533c2e69801</uri></key>") output.mp4

```



