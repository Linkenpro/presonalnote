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

