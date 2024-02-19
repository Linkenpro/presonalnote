CSV(Comma-Separated Values, 逗号分割值)是存储表格数据的常用文件格式，

它每一行都用一个换行符分隔，列与列之间用逗号分隔。

Python的csv库可以非常简单地修改csv文件，甚至从零开始创建一个csv文件。

```python
import csv
csvFile = open("../files/test.csv",'w+')
try:
    writer = csv.writer(csvFile)
    writer.writerow(('number','number plus 2','number times 2'))
    for i in range(10):
        writer.writerow((i,i+2,i*2))
finally:
    csvFile.close()
```

##### 构建csv替换文本，程序

```python
import csv

sum_rows = 100      # 要生成的行数
num_columns = 9     # 每行的数字数量
start_num = 115532  # 起始数字

# 生成数据
data = [['num1', 'num2', 'num3', 'num4', 'num5', 'num6', 'num7', 'num8', 'num9']]
for i in range(sum_rows):
    row = list(range(i * num_columns + start_num, (i + 1) * num_columns + start_num))
    data.append(row)

# 指定要创建的CSV文件的名称
csv_file = "number8.csv"

# 打开CSV文件并写入数据
with open(csv_file, mode="w", newline="") as file:
    writer = csv.writer(file)
    writer.writerows(data)

print(f"{csv_file} 创建已并写入成功")

```

```
DA_P
BINANAC
b$YYop609
EP#EPIC@f,$AH:4f*DNYNta
G——go

```

