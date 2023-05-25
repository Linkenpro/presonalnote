```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

# 读取OHLCV数据
data = pd.read_csv('ohlc_data.csv')  # 假设数据保存在名为'ohlc_data.csv'的文件中

# 计算价格区间
price_range = np.arange(data['Low'].min(), data['High'].max(), 10)  # 以10为间隔创建价格区间

# 计算每个价格区间内的交易量和持仓量
volume_per_range = np.zeros(len(price_range))
open_interest_per_range = np.zeros(len(price_range))

for i in range(len(price_range)):
    price_min = price_range[i]
    price_max = price_range[i + 1] if i < len(price_range) - 1 else np.inf
    
    # 在价格区间内选择交易数据
    selected_data = data[(data['Low'] >= price_min) & (data['High'] < price_max)]
    
    # 计算交易量和持仓量总和
    volume_per_range[i] = selected_data['Volume'].sum()
    open_interest_per_range[i] = selected_data['Open Interest'].sum()

# 绘制筹码分布图
plt.figure(figsize=(10, 6))
plt.bar(price_range[:-1], volume_per_range, width=10, align='edge', alpha=0.5, label='Volume')
plt.plot(price_range[:-1], open_interest_per_range, color='red', linewidth=2, label='Open Interest')
plt.xlabel('Price')
plt.ylabel('Volume / Open Interest')
plt.title('Chip Distribution Chart')
plt.legend()
plt.grid(True)
plt.show()
```

