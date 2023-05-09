##### 从交易所获取ohlcv数据，计算MA20均线

```python
import ccxt
from pprint import pprint
from config import apiKey, apiSecret

exchange_id = 'bybit'
exchange_class = getattr(ccxt, exchange_id)
exchange = exchange_class({
    'apiKey': apiKey,
    'secret': apiSecret,
    'timeout': 10000,
    'enableRateLimit': True,
    'proxies': {'http': '127.0.0.1:7890', 'https': '127.0.0.1:7890'}        # 代理
})

# K线
ohlcv = exchange.fetch_ohlcv(symbol='BTCUSD', timeframe='1d')

# 定义了一个名为sma的函数,接受两个参数：data和period
def sma(data, period):
    """计算简单移动平均线"""
    sma_values = []
    """通过一个for循环遍历data列表中的每个元素，计算出从当前元素向前period个元素的收盘价的平均值，得到一个SMA值。然后，将所有计算出来的SMA值保存在sma_values列表中，并最终将这个列表作为函数的返回值"""
    for i in range(period, len(data) + 1):
        sma_value = sum(data[i - period:i]) / period
        sma_values.append(sma_value)
    return sma_values

sma_values = sma([x[4] for x in ohlcv], 20)

pprint(sma_values)
```

好的，你想在之前的代码基础上加上双均线策略

```python
import ccxt
import numpy as np
import talib

from config import apiKey, apiSecret

# 获取交易所数据
exchange_id = 'bybit'
exchange_class = getattr(ccxt, exchange_id)
exchange = exchange_class({
    'apiKey': apiKey,
    'secret': apiSecret,
    'timeout': 10000,
    'enableRateLimit': True,
    'proxies': {'http': '127.0.0.1:7890', 'https': '127.0.0.1:7890'}        # 代理
})
symbol = 'BTCUSD'
timeframe = '1d'
limit = 200

# 获取 K 线数据
ohlcvs = exchange.fetch_ohlcv(symbol=symbol, timeframe=timeframe, limit=limit)

# 根据收盘价计算简单移动平均线（SMA）
closes = np.array([ohlcv[4] for ohlcv in ohlcvs])
sma10 = talib.SMA(closes, timeperiod=10)
sma20 = talib.SMA(closes, timeperiod=20)

# 判断交叉点
if sma10[-1] > sma20[-1] and sma10[-2] < sma20[-2]:
    print("发生了金叉信号！")
elif sma10[-1] < sma20[-1] and sma10[-2] > sma20[-2]:
    print("发生了死叉信号！")
else:
    print("没有发生交叉信号。")

# 输出简单移动平均线
print(f"SMA10: {sma10[-1]}")
print(f"SMA20: {sma20[-1]}")

>>>

```

###### 将ccxt数据导入pandas，并计算sma20

```python
import ccxt
import pandas as pd
from config import apiKey, apiSecret
# import matplotlib

exchange_id = 'bybit'
exchange_class = getattr(ccxt, exchange_id)
exchange = exchange_class({
    'apiKey': apiKey,
    'secret': apiSecret,
    'timeout': 10000,
    'enableRateLimit': True,
    'proxies': {'http': '127.0.0.1:7890', 'https': '127.0.0.1:7890'}    # 代理服务
})

# 获取BTCUSD的每日K线
ohlcv = exchange.fetch_ohlcv(symbol='BTCUSD', timeframe='1d')

# 将OHLCV数据转换为pandas DataFrame
df = pd.DataFrame(ohlcv, columns=['timestamp', 'open', 'high', 'low', 'close', 'volume'])

# 计算简单移动平均线
sma20 = df['close'].rolling(window=20).mean()

# 绘制简单移动平均线
sma20.plot()
```

可以，下面是一个用 Python 找出黄昏之星的示例代码：

```python
import pandas as pd
import numpy as np
import talib

# 获取数据，这里假设已经从交易所获取了 ohlcv 数据并存储到了 pandas DataFrame 中
ohlcv = pd.read_csv('your_file.csv')

# 计算黄昏之星指标
doji = talib.CDLDOJI(ohlcv['open'], ohlcv['high'], ohlcv['low'], ohlcv['close'])
engulfing = talib.CDLENGULFING(ohlcv['open'], ohlcv['high'], ohlcv['low'], ohlcv['close'])
evening_star = talib.CDLEVENINGSTAR(ohlcv['open'], ohlcv['high'], ohlcv['low'], ohlcv['close'])

# 将指标结果添加到 DataFrame 中
ohlcv['doji'] = doji
ohlcv['engulfing'] = engulfing
ohlcv['evening_star'] = evening_star

# 找出黄昏之星
evening_star_indices = np.where(ohlcv['evening_star'] > 0)[0]

```

以下是一个简单的示例代码，该策略使用了前文提到的 `find_bearish_engulfing` 和 `find_bullish_engulfing` 函数，以及 `find_pregnant` 函数，同时也使用了前文提到的 `sma` 函数来计算20日简单移动平均线。该策略使用 `bybit` 交易所的 `BTC/USD` 交易对的日线K线数据进行回测。

```python
import ccxt
from pprint import pprint
from config import apiKey, apiSecret
import pandas as pd

# 定义三个函数，用于寻找特定的K线形态
def find_bearish_engulfing(ohlcv):
    return ohlcv[-2][4] > ohlcv[-2][1] and ohlcv[-2][4] > ohlcv[-1][4] and ohlcv[-2][1] < ohlcv[-1][1]

def find_bullish_engulfing(ohlcv):
    return ohlcv[-2][1] > ohlcv[-2][4] and ohlcv[-2][1] > ohlcv[-1][1] and ohlcv[-2][4] < ohlcv[-1][4]

def find_pregnant(ohlcv):
    return ohlcv[-3][1] > ohlcv[-3][4] and ohlcv[-2][4] > ohlcv[-3][1] and ohlcv[-2][1] < ohlcv[-3][4] and ohlcv[-1][4] < ohlcv[-2][1]

# 定义计算20日简单移动平均线的函数
def sma(data, period):
    sma_values = []
    for i in range(period, len(data) + 1):
        sma_value = sum(data[i - period:i]) / period
        sma_values.append(sma_value)
    return sma_values

# 初始化交易所对象
exchange_id = 'bybit'
exchange_class = getattr(ccxt, exchange_id)
exchange = exchange_class({
    'apiKey': apiKey,
    'secret': apiSecret,
    'timeout': 10000,
    'enableRateLimit': True,
    'proxies': {'http': '127.0.0.1:7890', 'https': '127.0.0.1:7890'}        # 代理
})

# 获取日线K线数据并转换为DataFrame格式
ohlcv = exchange.fetch_ohlcv(symbol='BTCUSD', timeframe='1d')
df = pd.DataFrame(ohlcv, columns=['timestamp', 'open', 'high', 'low', 'close', 'volume'])
df['timestamp'] = pd.to_datetime(df['timestamp'], unit='ms')
df.set_index('timestamp', inplace=True)

# 计算20日简单移动平均线
sma20 = sma(df['close'], 20)
df['sma20'] = sma20

# 初始化变量
position = None
entry_price = None

# 遍历K线数据，进行策略回测
for i, row in df.iterrows():
    if i < pd.to_datetime('2022-01-01'):     # 只回测2022年以后的K线数据
        continue

    if position is None:     # 如果

```

##### 2023-05-08

字体网站：

1. https://freefontsfamily.com/
2. https://www.dafont.com/

###### 这里能否找到免费的电子书籍下载网站呢

我了解到有一些提供免费电子书籍下载的网站，您可以尝试访问以下网站：

1. Project Gutenberg（https://www.gutenberg.org/）：该网站提供了超过60,000本公有领域的电子书籍，包括文学、历史、科学等各个领域。所有的电子书籍都可以免费下载，并且可以在多种格式（如EPUB、MOBI、PDF等）之间选择。
2. ManyBooks（https://manybooks.net/）：该网站提供了超过50,000本免费电子书籍下载，包括各种不同的类别和主题，如小说、科幻、传记等。电子书籍也可以在多种格式之间选择，并且网站还提供了一些方便的筛选和搜索工具。
3. Free-eBooks（https://www.free-ebooks.net/）：该网站提供了超过10,000本免费电子书籍下载，包括小说、非小说、教育、科学等各个领域。用户可以在网站上注册账户后免费下载电子书籍，并且还可以参与社区和评论。
4. Feedbooks（https://www.feedbooks.com/）：该网站提供了数千本免费电子书籍下载，包括经典作品、小说、教育、科学等各种类别。电子书籍可以在多种格式之间选择，并且网站还提供了一些方便的筛选和排序工具。

请注意，在下载和使用免费电子书籍时，需要注意版权问题，避免侵犯他人的权益。建议尽可能选择公有领域或者授权免费下载的电子书籍。



###### 您能推荐一些字体下载网站吗



当然可以！以下是一些可以下载字体的网站：

1. Google Fonts（https://fonts.google.com/）：Google Fonts是一个由Google提供的免费字体库，其中包括了大量的优质字体供用户选择，可以直接在网站上在线使用，也可以下载到本地使用。
2. DaFont（https://www.dafont.com/）：DaFont是一个非常受欢迎的免费字体下载网站，拥有数量众多、种类丰富的字体资源，可以按照字体分类或者字体风格进行检索和下载。
3. Font Squirrel（https://www.fontsquirrel.com/）：Font Squirrel是一个提供高质量商业字体和免费字体下载的网站，拥有数量丰富的字体资源，提供多种格式的字体下载，方便用户在不同的设备和软件上使用。
4. 1001 Fonts（https://www.1001fonts.com/）：1001 Fonts是一个拥有超过10000种字体资源的免费字体下载网站，提供了多种字体分类和检索方式，用户可以根据自己的需求和喜好进行选择和下载。
5. FontSpace（https://www.fontspace.com/）：FontSpace是一个非常简洁、易用的免费字体下载网站，提供了大量的字体资源，可以按照字体分类、风格、流派等方式进行检索和下载。

希望这些网站能够帮助您找到喜欢的字体并丰富您的设计资源库。









