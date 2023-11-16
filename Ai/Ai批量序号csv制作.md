###### Version1

> 单列csv文件读取

```python
import csv

# 打开CSV文件
with open('Number.csv', 'r') as file:
    # 创建CSV文件读取器
    csv_reader = csv.reader(file)

    # 创建一个空列表来存储第一列数据
    column_data = []

    # 遍历CSV文件的每一行
    for row in csv_reader:
        # 假设第一列是需要读取的列
        # 如果你要读取其他列，可以使用row[index]，其中index是列的索引
        column_data.append(row[0])

# 现在，column_data 列表包含了CSV文件的第一列数据
# 按六个一组拆分列表

new_data = [column_data[i:i+6] for i in range(0, len(column_data), 6)]

# 打印拆分后的子列表
##for new in new_data:
##    print(new)

# 指定要保存到的CSV文件路径
csv_file = 'output1.csv'

# 打开CSV文件并写入数据
with open(csv_file, 'w', newline='') as file:
    csv_writer = csv.writer(file)
    csv_writer.writerows(new_data)

print(f"数据已写入 {csv_file}")

```

###### Version2

> 读取csv文件中所有的数据

```python
import pandas as pd
import math
import csv

# 读取csv文件
df = pd.read_csv("1109number.csv")

# 获取 DataFrame 的所有数值，展平为一维数组
values_array = df.values.flatten()

# 将 NumPy 数组转换为Python的列表
values_list = values_array.tolist()

# 使用列表推导式剔除NaN值
filter_list = [value for value in values_list if not math.isnan(value)]

# 使用 sorted 函数进行排序
sorted_list = sorted(filter_list)

# 使用列表推导式将浮点数转换为整数
integer_list = [int(x) for x in sorted_list]

# 按六个一组拆分列表
new_data = [integer_list[i:i+6] for i in range(0, len(integer_list), 6)]

# 指定要保存到的CSV文件路径
csv_file = 'output2.csv'

# 定义 CSV 文件的表头
header_name = ['v1', 'v2', 'v3', 'v4', 'v5', 'v6']
    
# 打开CSV文件并写入数据
with open(csv_file, 'w', newline='') as file:
    # 创建csv.writer对象
    csv_writer = csv.writer(file)
    # 写入表头
    csv_writer.writerow(header_name)
    # 写入数据
    csv_writer.writerows(new_data)

print(f"数据已写入 {csv_file}")
```

###### Version3

> 直接读取xlsx文件

```python
import openpyxl
import csv

# 打开需要处理的Excel文件
workbook = openpyxl.load_workbook('绿色超市外卖袋补流水号11月8日.xlsx')

# 选择第一个工作表（如果有多个工作表）
sheet = workbook.active

# 创建空列表
numeric_data = []
# 获取所有行和所有列的数字数据
for row in sheet.iter_rows(min_row=1, values_only=True):
    # 将每一行的数据添加到numeric_data中
    numeric_data.extend(row)

# 去除列表中的 None 值
numeric_data_cleaned = [value for value in numeric_data if value is not None]

# 去除列表中的第一个值
numberList = numeric_data_cleaned[1:]

# 使用 sorted 函数进行排序
sorted_list = sorted(numberList)

# 按六个一组拆分列表
new_data = [sorted_list[i:i+6] for i in range(0, len(sorted_list), 6)]

# 指定要保存到的CSV文件路径
csv_file = 'output4.csv'

# 定义 CSV 文件的表头
header_name = ['v1', 'v2', 'v3', 'v4', 'v5', 'v6']
    
# 打开CSV文件并写入数据
with open(csv_file, 'w', newline='') as file:
    # 创建csv.writer对象
    csv_writer = csv.writer(file)
    # 写入表头
    csv_writer.writerow(header_name)
    # 写入数据
    csv_writer.writerows(new_data)

print(f"数据已写入 {csv_file}！")
```

