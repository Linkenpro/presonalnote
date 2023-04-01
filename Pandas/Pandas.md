# Pandas 教程

![img](https://www.runoob.com/wp-content/uploads/2021/04/pandas.png)

`Pandas`是`Python`语言的一个扩展程序库，用于数据分析。

Pandas 是一个开放源码、BSD 许可的库，提供高性能、易于使用的数据结构和数据分析工具。

Pandas 名字衍生自术语 "panel data"（面板数据）和 "Python data analysis"（Python 数据分析）。

Pandas 一个强大的分析结构化数据的工具集，基础是`Numpy`（提供高性能的矩阵运算）。

Pandas 可以从各种文件格式比如 CSV、JSON、SQL、Microsoft Excel 导入数据。

Pandas 可以对各种数据进行运算操作，比如归并、再成形、选择，还有数据清洗和数据加工特征。

Pandas 广泛应用在学术、金融、统计学等各个数据分析领域。

### Pandas 应用

Pandas 的主要数据结构是 Series （一维数据）与 DataFrame（二维数据），这两种数据结构足以处理金融、统计、社会科学、工程等领域里的大多数典型用例。

------

### 数据结构

**[Series](https://www.runoob.com/pandas/pandas-series.html)** 是一种类似于一维数组的对象，它由一组数据（各种Numpy数据类型）以及一组与之相关的数据标签（即索引）组成。

**DataFrame** 是一个表格型的数据结构，它含有一组有序的列，每列可以是不同的值类型（数值、字符串、布尔型值）。DataFrame 既有行索引也有列索引，它可以被看做由 Series 组成的字典（共同用一个索引）。

------

### 相关链接

- Pandas 官网 https://pandas.pydata.org/
- Pandas 源代码：https://github.com/pandas-dev/pandas

# Pandas 安装

安装 pandas 需要基础环境是 Python，开始前我们假定你已经安装了 Python 和 Pip。

使用 pip 安装 pandas:

```
pip install pandas
```

安装成功后，我们就可以导入 pandas 包使用：

```python
# 导入 pandas 包使用
import pandas

# 查看 pandas 版本
pandas.__version__

# 导入 pandas 一般使用别名 pd 来代替
import pandas as pd


```

##### 实例

```python
import pandas as pd

mydataset = {
  'sites': ["Google", "Runoob", "Wiki"],
  'number': [1, 2, 3]
}

myvar = pd.DataFrame(mydataset)

print(myvar)
```

执行以上代码，输出结果为：

![img](https://www.runoob.com/wp-content/uploads/2021/04/0332CA88-50C3-4BF6-BACC-D9963BE0F724.jpg)

# Pandas 数据结构 - Series

Pandas Series 类似表格中的一个列（column），类似于一维数组，可以保存任何数据类型。

Series 由索引（index）和列组成，函数如下：

```
pandas.Series( data, index, dtype, name, copy)
```

参数说明：

- **data**：一组数据(ndarray 类型)。
- **index**：数据索引标签，如果不指定，默认从 0 开始。
- **dtype**：数据类型，默认会自己判断。
- **name**：设置名称。
- **copy**：拷贝数据，默认为 False。

创建一个简单的 Series 实例：

```python
import pandas as pd

a = [1, 2, 3]

myvar = pd.Series(a)

print(myvar)
```

输出结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/04/FD659034-1715-4020-A6BF-400FAC9CE849.jpg)

从上图可知，如果没有指定索引，索引值就从 0 开始，我们可以根据索引值读取数据：

```python
import pandas as pd

a = [1, 2, 3]

myvar = pd.Series(a)

print(myvar[1])

>>>
2
```

我们可以指定索引值，如下实例：

```python
import pandas as pd

a = ["Google", "Runoob", "Wiki"]

myvar = pd.Series(a, index = ["x", "y", "z"])

print(myvar)
```

输出结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/04/32B49FA4-ED68-446A-9EBF-C52FCB6D0CD6.jpg)

根据索引值读取数据:

```python
import pandas as pd

a = ["Google", "Runoob", "Wiki"]

myvar = pd.Series(a, index = ["x", "y", "z"])

print(myvar["y"])

>>>
Runoob
```

我们也可以使用 key/value 对象，类似字典来创建 Series：

```python
import pandas as pd

sites = {1: "Google", 2: "Runoob", 3: "Wiki"}

myvar = pd.Series(sites)

print(myvar)
```

输出结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/04/C01F8A55-5D06-4FAD-BE34-A569A8B05E2C.jpg)

从上图可知，字典的 key 变成了索引值。

如果我们只需要字典中的一部分数据，只需要指定需要数据的索引即可，如下实例：

```python
import pandas as pd

sites = {1: "Google", 2: "Runoob", 3: "Wiki"}

myvar = pd.Series(sites, index = [1, 2])

print(myvar)
```

输出结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/04/6CC2CFBA-3CC5-459D-8FE0-D89C1EE1AEB9.jpg)

设置 Series 名称参数：

```python
import pandas as pd

sites = {1: "Google", 2: "Runoob", 3: "Wiki"}

myvar = pd.Series(sites, index = [1, 2], name="RUNOOB-Series-TEST" )

print(myvar)
```

![img](https://www.runoob.com/wp-content/uploads/2021/04/1FB6D419-06D7-4229-9148-1F4E79DE6ACF.jpg)

# Pandas 数据结构 - DataFrame

DataFrame 是一个表格型的数据结构，它含有一组有序的列，每列可以是不同的值类型（数值、字符串、布尔型值）。DataFrame 既有行索引也有列索引，它可以被看做由 Series 组成的字典（共同用一个索引）。

![img](https://www.runoob.com/wp-content/uploads/2021/04/pandas-DataStructure.png)

![img](https://www.runoob.com/wp-content/uploads/2021/04/df-dp.png)

DataFrame 构造方法如下：

```
pandas.DataFrame(data, index, columns, dtype, copy)
```

参数说明：

- **data**：一组数据(ndarray、series, map, lists, dict 等类型)。
- **index**：索引值，或者可以称为行标签。
- **columns**：列标签，默认为 RangeIndex (0, 1, 2, …, n) 。
- **dtype**：数据类型。
- **copy**：拷贝数据，默认为 False。

Pandas DataFrame 是一个二维的数组结构，类似二维数组。

### 使用列表创建

```python
import pandas as pd

data = [['Google',10],['Runoob',12],['Wiki',13]]

df = pd.DataFrame(data,columns=['Site','Age'],dtype=float)

print(df)
```

输出结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/04/BE773E8F-DEC2-4434-8630-91E660A1DFC0.jpg)

以下实例使用 ndarrays 创建，ndarray 的长度必须相同， 如果传递了 index，则索引的长度应等于数组的长度。如果没有传递索引，则默认情况下，索引将是range(n)，其中n是数组长度。

ndarrays 可以参考：[NumPy Ndarray 对象](https://www.runoob.com/numpy/numpy-ndarray-object.html)

### 使用 ndarrays 创建

```python
import pandas as pd

data = {'Site':['Google', 'Runoob', 'Wiki'], 'Age':[10, 12, 13]}

df = pd.DataFrame(data)

print (df)
```

输出结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/04/BE773E8F-DEC2-4434-8630-91E660A1DFC0.jpg)

从以上输出结果可以知道， DataFrame 数据类型一个表格，包含 rows（行） 和 columns（列）：

![img](https://www.runoob.com/wp-content/uploads/2021/04/rows-cloumns.png)

还可以使用字典（key/value），其中字典的 key 为列名:

### 使用字典创建

```python
import pandas as pd

data = [{'a': 1, 'b': 2},{'a': 5, 'b': 10, 'c': 20}]

df = pd.DataFrame(data)

print (df)

>>>
   a   b     c
0  1   2   NaN
1  5  10  20.0
```

没有对应的部分数据为 **NaN**。

Pandas 可以使用 **loc** 属性返回指定行的数据，如果没有设置索引，第一行索引为 **0**，第二行索引为 **1**，以此类推：

```python
import pandas as pd

data = {
  "calories": [420, 380, 390],
  "duration": [50, 40, 45]
}

# 数据载入到 DataFrame 对象
df = pd.DataFrame(data)

# 返回第一行
print(df.loc[0])
# 返回第二行
print(df.loc[1])

>>>
calories    420
duration     50
Name: 0, dtype: int64
calories    380
duration     40
Name: 1, dtype: int64
```

**注意：**返回结果其实就是一个 Pandas Series 数据。

### 也可以返回多行数据

使用 **[[ ... ]]** 格式，**...** 为各行的索引，以逗号隔开：

```python
import pandas as pd

data = {
  "calories": [420, 380, 390],
  "duration": [50, 40, 45]
}

# 数据载入到 DataFrame 对象
df = pd.DataFrame(data)

# 返回第一行和第二行
print(df.loc[[0, 1]])

>>>
   calories  duration
0       420        50
1       380        40
```

**注意：**返回结果其实就是一个 Pandas DataFrame 数据。

我们可以指定索引值，如下实例：

```python
import pandas as pd

data = {
  "calories": [420, 380, 390],
  "duration": [50, 40, 45]
}

df = pd.DataFrame(data, index = ["day1", "day2", "day3"])

print(df)

>>>
      calories  duration
day1       420        50
day2       380        40
day3       390        45
```

Pandas 可以使用 **loc** 属性返回指定索引对应到某一行：

```python
import pandas as pd

data = {
  "calories": [420, 380, 390],
  "duration": [50, 40, 45]
}

df = pd.DataFrame(data, index = ["day1", "day2", "day3"])

# 指定索引
print(df.loc["day2"])

>>>
calories    380
duration     40
Name: day2, dtype: int64
```

# Pandas CSV 文件

CSV（Comma-Separated Values，逗号分隔值，有时也称为字符分隔值，因为分隔字符也可以不是逗号），其文件以纯文本形式存储表格数据（数字和文本）。

CSV 是一种通用的、相对简单的文件格式，被用户、商业和科学广泛应用。

Pandas 可以很方便的处理 CSV 文件，本文以 [nba.csv](https://static.runoob.com/download/nba.csv) 为例，你可以[下载 nba.csv](https://static.runoob.com/download/nba.csv) 或[打开 nba.csv](https://static.runoob.com/download/nba.csv.txt) 查看。

```python
import pandas as pd

df = pd.read_csv('nba.csv')

# 返回 DataFrame 类型的数据
print(df.to_string())
```

**to_string()** 用于返回 DataFrame 类型的数据，如果不使用该函数，则输出结果为数据的前面 5 行和末尾 5 行，中间部分以 **...** 代替。

```python
import pandas as pd

df = pd.read_csv('nba.csv')

print(df)

>>>
              Name            Team  Number Position   Age Height  Weight            College     Salary
0    Avery Bradley  Boston Celtics     0.0       PG  25.0    6-2   180.0              Texas  7730337.0
1      Jae Crowder  Boston Celtics    99.0       SF  25.0    6-6   235.0          Marquette  6796117.0
2     John Holland  Boston Celtics    30.0       SG  27.0    6-5   205.0  Boston University        NaN
3      R.J. Hunter  Boston Celtics    28.0       SG  22.0    6-5   185.0      Georgia State  1148640.0
4    Jonas Jerebko  Boston Celtics     8.0       PF  29.0   6-10   231.0                NaN  5000000.0
..             ...             ...     ...      ...   ...    ...     ...                ...        ...
453   Shelvin Mack       Utah Jazz     8.0       PG  26.0    6-3   203.0             Butler  2433333.0
454      Raul Neto       Utah Jazz    25.0       PG  24.0    6-1   179.0                NaN   900000.0
455   Tibor Pleiss       Utah Jazz    21.0        C  26.0    7-3   256.0                NaN  2900000.0
456    Jeff Withey       Utah Jazz    24.0        C  26.0    7-0   231.0             Kansas   947276.0
457            NaN             NaN     NaN      NaN   NaN    NaN     NaN                NaN        NaN
```

##### 我们也可以使用 **to_csv()** 方法将 DataFrame 存储为 csv 文件：

```python
import pandas as pd
   
# 三个字段 name, site, age
nme = ["Google", "Runoob", "Taobao", "Wiki"]
st = ["www.google.com", "www.runoob.com", "www.taobao.com", "www.wikipedia.org"]
ag = [90, 40, 80, 98]
   
# 字典
dict = {'name': nme, 'site': st, 'age': ag}
     
df = pd.DataFrame(dict)
 
# 保存 dataframe
df.to_csv('site.csv')
```

执行成功后，我们打开 site.csv 文件，显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/05/9758194A-0D8E-4C53-95A0-157C690614E6.jpg)

## 数据处理

### head()

**head( \*n\* )** 方法用于读取前面的 n 行，如果不填参数 n ，默认返回 5 行。

```python
import pandas as pd

df = pd.read_csv('nba.csv')

print(df.head())

>>>
            Name            Team  Number Position   Age Height  Weight            College     Salary
0  Avery Bradley  Boston Celtics     0.0       PG  25.0    6-2   180.0              Texas  7730337.0
1    Jae Crowder  Boston Celtics    99.0       SF  25.0    6-6   235.0          Marquette  6796117.0
2   John Holland  Boston Celtics    30.0       SG  27.0    6-5   205.0  Boston University        NaN
3    R.J. Hunter  Boston Celtics    28.0       SG  22.0    6-5   185.0      Georgia State  1148640.0
4  Jonas Jerebko  Boston Celtics     8.0       PF  29.0   6-10   231.0                NaN  5000000.0
```

### 实例 - 读取前面 10 行

```python
import pandas as pd

df = pd.read_csv('nba.csv')

print(df.head(10))

>>>
            Name            Team  Number Position   Age Height  Weight            College      Salary
0  Avery Bradley  Boston Celtics     0.0       PG  25.0    6-2   180.0              Texas   7730337.0
1    Jae Crowder  Boston Celtics    99.0       SF  25.0    6-6   235.0          Marquette   6796117.0
2   John Holland  Boston Celtics    30.0       SG  27.0    6-5   205.0  Boston University         NaN
3    R.J. Hunter  Boston Celtics    28.0       SG  22.0    6-5   185.0      Georgia State   1148640.0
4  Jonas Jerebko  Boston Celtics     8.0       PF  29.0   6-10   231.0                NaN   5000000.0
5   Amir Johnson  Boston Celtics    90.0       PF  29.0    6-9   240.0                NaN  12000000.0
6  Jordan Mickey  Boston Celtics    55.0       PF  21.0    6-8   235.0                LSU   1170960.0
7   Kelly Olynyk  Boston Celtics    41.0        C  25.0    7-0   238.0            Gonzaga   2165160.0
8   Terry Rozier  Boston Celtics    12.0       PG  22.0    6-2   190.0         Louisville   1824360.0
9   Marcus Smart  Boston Celtics    36.0       PG  22.0    6-4   220.0     Oklahoma State   3431040.0
```

### tail()

**tail( n )** 方法用于读取尾部的 n 行，如果不填参数 n ，默认返回 5 行，空行各个字段的值返回 **NaN**。

### 实例 - 读取末尾 5 行

```python
import pandas as pd

df = pd.read_csv('nba.csv')

print(df.tail())

>>>
             Name       Team  Number Position   Age Height  Weight College     Salary
453  Shelvin Mack  Utah Jazz     8.0       PG  26.0    6-3   203.0  Butler  2433333.0
454     Raul Neto  Utah Jazz    25.0       PG  24.0    6-1   179.0     NaN   900000.0
455  Tibor Pleiss  Utah Jazz    21.0        C  26.0    7-3   256.0     NaN  2900000.0
456   Jeff Withey  Utah Jazz    24.0        C  26.0    7-0   231.0  Kansas   947276.0
457           NaN        NaN     NaN      NaN   NaN    NaN     NaN     NaN        NaN
```

### 实例 - 读取末尾 10 行

```python
import pandas as pd

df = pd.read_csv('nba.csv')

print(df.tail(10))

>>>
               Name       Team  Number Position   Age Height  Weight   College      Salary
448  Gordon Hayward  Utah Jazz    20.0       SF  26.0    6-8   226.0    Butler  15409570.0
449     Rodney Hood  Utah Jazz     5.0       SG  23.0    6-8   206.0      Duke   1348440.0
450      Joe Ingles  Utah Jazz     2.0       SF  28.0    6-8   226.0       NaN   2050000.0
451   Chris Johnson  Utah Jazz    23.0       SF  26.0    6-6   206.0    Dayton    981348.0
452      Trey Lyles  Utah Jazz    41.0       PF  20.0   6-10   234.0  Kentucky   2239800.0
453    Shelvin Mack  Utah Jazz     8.0       PG  26.0    6-3   203.0    Butler   2433333.0
454       Raul Neto  Utah Jazz    25.0       PG  24.0    6-1   179.0       NaN    900000.0
455    Tibor Pleiss  Utah Jazz    21.0        C  26.0    7-3   256.0       NaN   2900000.0
456     Jeff Withey  Utah Jazz    24.0        C  26.0    7-0   231.0    Kansas    947276.0
457             NaN        NaN     NaN      NaN   NaN    NaN     NaN       NaN         NaN
```

### info()返回表格的一些基本信息

```python
import pandas as pd

df = pd.read_csv('nba.csv')

print(df.info())

>>>
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 458 entries, 0 to 457          # 行数，458 行，第一行编号为 0
Data columns (total 9 columns):            # 列数，9列
 #   Column    Non-Null Count  Dtype       # 各列的数据类型
---  ------    --------------  -----  
 0   Name      457 non-null    object 
 1   Team      457 non-null    object 
 2   Number    457 non-null    float64
 3   Position  457 non-null    object 
 4   Age       457 non-null    float64
 5   Height    457 non-null    object 
 6   Weight    457 non-null    float64
 7   College   373 non-null    object         # non-null，意思为非空的数据    
 8   Salary    446 non-null    float64
dtypes: float64(4), object(5)                 # 类型
```

non-null 为非空数据，我们可以看到上面的信息中，总共 458 行，College 字段的空值最多。

# Pandas JSON

JSON（**J**ava**S**cript **O**bject **N**otation，JavaScript 对象表示法），是存储和交换文本信息的语法，类似 XML。

JSON 比 XML 更小、更快，更易解析，更多 JSON 内容可以参考 [JSON 教程](https://www.runoob.com/json/json-tutorial.html)。

Pandas 可以很方便的处理 JSON 数据，本文以 [sites.json](https://static.runoob.com/download/sites.json) 为例，内容如下：

### 实例——JSON

```json
[
   {
   "id": "A001",
   "name": "菜鸟教程",
   "url": "www.runoob.com",
   "likes": 61
   },
   {
   "id": "A002",
   "name": "Google",
   "url": "www.google.com",
   "likes": 124
   },
   {
   "id": "A003",
   "name": "淘宝",
   "url": "www.taobao.com",
   "likes": 45
   }
]
```

### 实例——

```python
import pandas as pd

df = pd.read_json('sites.json')
   
print(df.to_string())
```

**to_string()** 用于返回 DataFrame 类型的数据，我们也可以直接处理 JSON 字符串。

```python
import pandas as pd

data =[
    {
      "id": "A001",
      "name": "菜鸟教程",
      "url": "www.runoob.com",
      "likes": 61
    },
    {
      "id": "A002",
      "name": "Google",
      "url": "www.google.com",
      "likes": 124
    },
    {
      "id": "A003",
      "name": "淘宝",
      "url": "www.taobao.com",
      "likes": 45
    }
]
df = pd.DataFrame(data)

print(df)

>>>
     id    name             url  likes
0  A001    菜鸟教程  www.runoob.com     61
1  A002  Google  www.google.com    124
2  A003      淘宝  www.taobao.com     45
```

JSON 对象与 Python 字典具有相同的格式，所以我们可以直接将 Python 字典转化为 DataFrame 数据：

```python
import pandas as pd


# 字典格式的 JSON                                                                                              
s = {
    "col1":{"row1":1,"row2":2,"row3":3},
    "col2":{"row1":"x","row2":"y","row3":"z"}
}

# 读取 JSON 转为 DataFrame                                                                                          
df = pd.DataFrame(s)
print(df)

>>>
      col1 col2
row1     1    x
row2     2    y
row3     3    z
```

从 URL 中读取 JSON 数据：

```python
import pandas as pd

URL = 'https://static.runoob.com/download/sites.json'
df = pd.read_json(URL)
print(df)

>>>
     id    name             url  likes
0  A001    菜鸟教程  www.runoob.com     61
1  A002  Google  www.google.com    124
2  A003      淘宝  www.taobao.com     45
```

### 内嵌的 JSON 数据

假设有一组内嵌的 JSON 数据文件 **nested_list.json** ：

```json
{
    "school_name": "ABC primary school",
    "class": "Year 1",
    "students": [
    {
        "id": "A001",
        "name": "Tom",
        "math": 60,
        "physics": 66,
        "chemistry": 61
    },
    {
        "id": "A002",
        "name": "James",
        "math": 89,
        "physics": 76,
        "chemistry": 51
    },
    {
        "id": "A003",
        "name": "Jenny",
        "math": 79,
        "physics": 90,
        "chemistry": 78
    }]
}
```

### 使用以下代码格式化完整内容：

```python
import pandas as pd

df = pd.read_json('nested_list.json')

print(df)

>>>
          school_name   class                                           students
0  ABC primary school  Year 1  {'id': 'A001', 'name': 'Tom', 'math': 60, 'phy...
1  ABC primary school  Year 1  {'id': 'A002', 'name': 'James', 'math': 89, 'p...
2  ABC primary school  Year 1  {'id': 'A003', 'name': 'Jenny', 'math': 79, 'p...
```

### **json_normalize()** 方法将内嵌的数据完整的解析出来：

```python
import pandas as pd
import json

# 使用 Python JSON 模块载入数据
with open('nested_list.json','r') as f:
    data = json.loads(f.read())

# 展平数据
df_nested_list = pd.json_normalize(data, record_path =['students'])
print(df_nested_list)

>>>
     id   name  math  physics  chemistry
0  A001    Tom    60       66         61
1  A002  James    89       76         51
2  A003  Jenny    79       90         78
```

**data = json.loads(f.read())** 使用 Python JSON 模块载入数据。

**json_normalize()** 使用了参数 **record_path** 并设置为 **['students']** 用于展开内嵌的 JSON 数据 **students**。

显示结果还没有包含 school_name 和 class 元素，如果需要展示出来可以使用 meta 参数来显示这些元数据：

```python
import pandas as pd
import json

# 使用 Python JSON 模块载入数据
with open('nested_list.json','r') as f:
    data = json.loads(f.read())

# 展平数据
df_nested_list = pd.json_normalize(
    data,
    record_path =['students'],
    meta=['school_name', 'class']
)
print(df_nested_list)

>>>
     id   name  math  physics  chemistry         school_name   class
0  A001    Tom    60       66         61  ABC primary school  Year 1
1  A002  James    89       76         51  ABC primary school  Year 1
2  A003  Jenny    79       90         78  ABC primary school  Year 1
```

接下来，让我们尝试读取更复杂的 JSON 数据，该数据嵌套了列表和字典，数据文件 **nested_mix.json** 如下：

nested_mix.json 文件内容

```json
{
    "school_name": "local primary school",
    "class": "Year 1",
    "info": {
      "president": "John Kasich",
      "address": "ABC road, London, UK",
      "contacts": {
        "email": "admin@e.com",
        "tel": "123456789"
      }
    },
    "students": [
    {
        "id": "A001",
        "name": "Tom",
        "math": 60,
        "physics": 66,
        "chemistry": 61
    },
    {
        "id": "A002",
        "name": "James",
        "math": 89,
        "physics": 76,
        "chemistry": 51
    },
    {
        "id": "A003",
        "name": "Jenny",
        "math": 79,
        "physics": 90,
        "chemistry": 78
    }]
}
```

### nested_mix.json 文件转换为 DataFrame：

```python
import pandas as pd
import json

# 使用 Python JSON 模块载入数据
with open('nested_mix.json','r') as f:
    data = json.loads(f.read())
   
df = pd.json_normalize(
    data,
    record_path =['students'],
    meta=[
        'class',
        ['info', 'president'],
        ['info', 'contacts', 'tel']
    ]
)

print(df)

>>>
     id   name  math  physics  chemistry   class info.president info.contacts.tel
0  A001    Tom    60       66         61  Year 1    John Kasich         123456789
1  A002  James    89       76         51  Year 1    John Kasich         123456789
2  A003  Jenny    79       90         78  Year 1    John Kasich         123456789
```

### 读取内嵌数据中的一组数据

以下是实例文件 **nested_deep.json**，我们只读取内嵌中的 **math** 字段：

```json
{
    "school_name": "local primary school",
    "class": "Year 1",
    "students": [
    {
        "id": "A001",
        "name": "Tom",
        "grade": {
            "math": 60,
            "physics": 66,
            "chemistry": 61
        }
 
    },
    {
        "id": "A002",
        "name": "James",
        "grade": {
            "math": 89,
            "physics": 76,
            "chemistry": 51
        }
       
    },
    {
        "id": "A003",
        "name": "Jenny",
        "grade": {
            "math": 79,
            "physics": 90,
            "chemistry": 78
        }
    }]
}
```

这里我们需要使用到 **glom** 模块来处理数据套嵌，**glom** 模块允许我们使用 **.** 来访问内嵌对象的属性。

第一次使用我们需要安装 glom：

```
pip3 install glom
```

### 实例

```python
import pandas as pd
from glom import glom

df = pd.read_json('nested_deep.json')

data = df['students'].apply(lambda row: glom(row, 'grade.math'))
print(data)

>>>
0    60
1    89
2    79
Name: students, dtype: int64
```

# Pandas 数据清洗

数据清洗是对一些没有用的数据进行处理的过程。

很多数据集存在数据缺失、数据格式错误、错误数据或重复数据的情况，如果要对使数据分析更加准确，就需要对这些没有用的数据进行处理。

在这个教程中，我们将利用 Pandas包来进行数据清洗。

本文使用到的测试数据 [property-data.csv](https://static.runoob.com/download/property-data.csv) 如下：

![img](https://www.runoob.com/wp-content/uploads/2021/06/6A6DE9DA-E0EE-4001-8C21-1D6A8EBF70FF.jpeg)

上表包含了四种空数据：

# Pandas 数据清洗

数据清洗是对一些没有用的数据进行处理的过程。

很多数据集存在数据缺失、数据格式错误、错误数据或重复数据的情况，如果要对使数据分析更加准确，就需要对这些没有用的数据进行处理。

在这个教程中，我们将利用 Pandas包来进行数据清洗。

本文使用到的测试数据 [property-data.csv](https://static.runoob.com/download/property-data.csv) 如下：

![img](https://www.runoob.com/wp-content/uploads/2021/06/6A6DE9DA-E0EE-4001-8C21-1D6A8EBF70FF.jpeg)

上表包含了四种空数据：

- n/a
- NA
- —
- na

## Pandas 清洗空值

如果我们要删除包含空字段的行，可以使用 **dropna()** 方法，语法格式如下：

```
DataFrame.dropna(axis=0, how='any', thresh=None, subset=None, inplace=False)
```

**参数说明：**

- axis：默认为 **0**，表示逢空值剔除整行，如果设置参数 **axis＝1** 表示逢空值去掉整列。
- how：默认为 **'any'** 如果一行（或一列）里任何一个数据有出现 NA 就去掉整行，如果设置 **how='all'** 一行（或列）都是 NA 才去掉这整行。
- thresh：设置需要多少非空值的数据才可以保留下来的。
- subset：设置想要检查的列。如果是多个列，可以使用列名的 list 作为参数。
- inplace：如果设置 True，将计算得到的值直接覆盖之前的值并返回 None，修改的是源数据。

我们可以通过 **isnull()** 判断各个单元格是否为空。

```python
import pandas as pd

df = pd.read_csv('property-data.csv')

print (df['NUM_BEDROOMS'])
print (df['NUM_BEDROOMS'].isnull())

>>>
```

以上实例输出结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/06/2A5B93BC-E0A3-4864-98B7-7DAE0E92C5F2.jpg)

以上例子中我们看到 Pandas 把 n/a 和 NA 当作空数据，na 不是空数据，不符合我们要求，我们可以指定空数据类型：

```python
import pandas as pd

missing_values = ["n/a", "na", "--"]
df = pd.read_csv('property-data.csv', na_values = missing_values)

print (df['NUM_BEDROOMS'])
print (df['NUM_BEDROOMS'].isnull())
```

以上实例输出结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/06/FCE8C077-C981-4764-ACBC-CB129304F831.jpg)

#### 接下来的实例演示了删除包含空数据的行。

```python
import pandas as pd

df = pd.read_csv('property-data.csv')

new_df = df.dropna()

print(new_df.to_string())
```

以上实例输出结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/06/4744B204-1527-49DE-B749-E39D6C7DFE01.jpg)

**注意：**默认情况下，dropna() 方法返回一个新的 DataFrame，不会修改源数据。

如果你要修改源数据 DataFrame, 可以使用 **inplace = True** 参数:

```python
import pandas as pd

df = pd.read_csv('property-data.csv')

df.dropna(inplace = True)

print(df.to_string())
```

以上实例输出结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/06/4744B204-1527-49DE-B749-E39D6C7DFE01.jpg)

我们也可以移除指定列有空值的行：

```python
# 实例
# 移除 ST_NUM 列中字段值为空的行：

import pandas as pd

df = pd.read_csv('property-data.csv')

df.dropna(subset=['ST_NUM'], inplace = True)

print(df.to_string())
```

以上实例输出结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/06/C83C70BC-5E47-4397-938D-7445104BE551.jpg)

我们也可以 **fillna()** 方法来替换一些空字段：

```python
# 使用 12345 替换空字段：

import pandas as pd

df = pd.read_csv('property-data.csv')

df.fillna(12345, inplace = True)

print(df.to_string())
```

以上实例输出结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/06/5033AA75-BC7D-4192-9428-221765EA3C58.jpg)

我们也可以指定某一个列来替换数据：

## 实例

使用 12345 替换 PID 为空数据：

```python
import pandas as pd

df = pd.read_csv('property-data.csv')

df['PID'].fillna(12345, inplace = True)

print(df.to_string())

>>>
```

以上实例输出结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/06/2F955E95-8C4C-4E7C-B788-5714B2C898C2.jpg)

替换空单元格的常用方法是计算列的均值、中位数值或众数。

Pandas使用 **mean()**、**median()** 和 **mode()** 方法计算列的均值（所有值加起来的平均值）、中位数值（排序后排在中间的数）和众数（出现频率最高的数）。

###### 使用 mean() 方法计算列的均值并替换空单元格：

```python
import pandas as pd

df = pd.read_csv('property-data.csv')

x = df["ST_NUM"].mean()

df["ST_NUM"].fillna(x, inplace = True)

print(df.to_string())

>>>

```

以上实例输出结果如下，红框为计算的均值替换来空单元格：

![img](https://www.runoob.com/wp-content/uploads/2021/06/6A758363-02FA-4F6E-9F30-7A3E4489639A.jpg)

## 实例

使用 median() 方法计算列的中位数并替换空单元格：

```python
import pandas as pd

df = pd.read_csv('property-data.csv')

x = df["ST_NUM"].median()

df["ST_NUM"].fillna(x, inplace = True)

print(df.to_string())

>>>

```

以上实例输出结果如下，红框为计算的中位数替换来空单元格：

![img](https://www.runoob.com/wp-content/uploads/2021/06/551B8875-D393-4003-BB68-695EBEDBB0FE.jpg)

## 实例

使用 mode() 方法计算列的众数并替换空单元格：

```python
import pandas as pd

df = pd.read_csv('property-data.csv')

x = df["ST_NUM"].mode()

df["ST_NUM"].fillna(x, inplace = True)

print(df.to_string())
```

以上实例输出结果如下，红框为计算的众数替换来空单元格：

![img](https://www.runoob.com/wp-content/uploads/2021/06/40F6D1C2-CFD7-4C53-B887-86695F486E6D.jpg)

------

## Pandas 清洗格式错误数据

数据格式错误的单元格会使数据分析变得困难，甚至不可能。

我们可以通过包含空单元格的行，或者将列中的所有单元格转换为相同格式的数据。

以下实例会格式化日期：

```python
import pandas as pd

# 第三个日期格式错误
data = {
  "Date": ['2020/12/01', '2020/12/02' , '20201226'],
  "duration": [50, 40, 45]
}

df = pd.DataFrame(data, index = ["day1", "day2", "day3"])

df['Date'] = pd.to_datetime(df['Date'])

print(df.to_string())

>>>
以上实例输出结果如下：

           Date  duration
day1 2020-12-01        50
day2 2020-12-02        40
day3 2020-12-26        45
```

## Pandas 清洗错误数据

数据错误也是很常见的情况，我们可以对错误的数据进行替换或移除。

以下实例会替换错误年龄的数据：

```python
import pandas as pd

person = {
  "name": ['Google', 'Runoob' , 'Taobao'],
  "age": [50, 40, 12345]    # 12345 年龄数据是错误的
}

df = pd.DataFrame(person)

df.loc[2, 'age'] = 30 # 修改数据

print(df.to_string())

>>>
     name  age
0  Google   50
1  Runoob   40
2  Taobao   30
```

也可以设置条件语句：

## 实例

将 age 大于 120 的设置为 120:

```python
import pandas as pd

person = {
  "name": ['Google', 'Runoob' , 'Taobao'],
  "age": [50, 200, 12345]    
}

df = pd.DataFrame(person)

for x in df.index:
  if df.loc[x, "age"] > 120:
    df.loc[x, "age"] = 120

print(df.to_string())

>>>
     name  age
0  Google   50
1  Runoob  120
2  Taobao  120
```

也可以将错误数据的行删除：

## 实例

将 age 大于 120 的删除:

```python
import pandas as pd

person = {
  "name": ['Google', 'Runoob' , 'Taobao'],
  "age": [50, 40, 12345]    # 12345 年龄数据是错误的
}

df = pd.DataFrame(person)

for x in df.index:
  if df.loc[x, "age"] > 120:
    df.drop(x, inplace = True)

print(df.to_string())

>>>
     name  age
0  Google   50
1  Runoob   40
```

## Pandas 清洗重复数据

如果我们要清洗重复数据，可以使用 **duplicated()** 和 **drop_duplicates()** 方法。

如果对应的数据是重复的，**duplicated()** 会返回 True，否则返回 False。

## 实例

```python
import pandas as pd

person = {
  "name": ['Google', 'Runoob', 'Runoob', 'Taobao'],
  "age": [50, 40, 40, 23]  
}
df = pd.DataFrame(person)

print(df.duplicated())

>>>
0    False
1    False
2     True
3    False
dtype: bool
```

删除重复数据，可以直接使用**drop_duplicates()** 方法。

## 实例

```python
import pandas as pd

persons = {
  "name": ['Google', 'Runoob', 'Runoob', 'Taobao'],
  "age": [50, 40, 40, 23]  
}

df = pd.DataFrame(persons)

df.drop_duplicates(inplace = True)
print(df)

>>>
     name  age
0  Google   50
1  Runoob   40
3  Taobao   23
```

# Pandas 常用函数

以下列出了 Pandas 常用的一些函数及使用实例：

## 读取数据

| 函数                                  | 说明                       |
| :------------------------------------ | :------------------------- |
| pd.read_csv(filename)                 | 读取 CSV 文件；            |
| pd.read_excel(filename)               | 读取 Excel 文件；          |
| pd.read_sql(query, connection_object) | 从 SQL 数据库读取数据；    |
| pd.read_json(json_string)             | 从 JSON 字符串中读取数据； |
| pd.read_html(url)                     | 从 HTML 页面中读取数据。   |

## 实例

```python
import pandas as pd

# 从 CSV 文件中读取数据
df = pd.read_csv('data.csv')

# 从 Excel 文件中读取数据
df = pd.read_excel('data.xlsx')

# 从 SQL 数据库中读取数据
import sqlite3
conn = sqlite3.connect('database.db')
df = pd.read_sql('SELECT * FROM table_name', conn)

# 从 JSON 字符串中读取数据
json_string = '{"name": "John", "age": 30, "city": "New York"}'
df = pd.read_json(json_string)

# 从 HTML 页面中读取数据
url = 'https://www.runoob.com'
dfs = pd.read_html(url)
df = dfs[0] # 选择第一个数据框
```

## 查看数据

| 函数          | 说明                                                       |
| :------------ | :--------------------------------------------------------- |
| df.head(n)    | 显示前 n 行数据；                                          |
| df.tail(n)    | 显示后 n 行数据；                                          |
| df.info()     | 显示数据的信息，包括列名、数据类型、缺失值等；             |
| df.describe() | 显示数据的基本统计信息，包括均值、方差、最大值、最小值等； |
| df.shape      | 显示数据的行数和列数。                                     |

## 实例

```python
# 显示前五行数据
df.head()

# 显示后五行数据
df.tail()

# 显示数据信息
df.info()

# 显示基本统计信息
df.describe()

# 显示数据的行数和列数
df.shape
```

## 实例

```python
import pandas as pd

data = [
    {"name": "Google", "likes": 25, "url": "https://www.google.com"},
    {"name": "Runoob", "likes": 30, "url": "https://www.runoob.com"},
    {"name": "Taobao", "likes": 35, "url": "https://www.taobao.com"}
]

df = pd.DataFrame(data)
# 显示前两行数据
print(df.head(2))
# 显示前最后一行数据
print(df.tail(1))

>>>
     name  likes                     url
0  Google     25  https://www.google.com
1  Runoob     30  https://www.runoob.com
     name  likes                     url
2  Taobao     35  https://www.taobao.com
```

## 数据清洗

| 函数                             | 说明                     |
| :------------------------------- | :----------------------- |
| df.dropna()                      | 删除包含缺失值的行或列； |
| df.fillna(value)                 | 将缺失值替换为指定的值； |
| df.replace(old_value, new_value) | 将指定值替换为新值；     |
| df.duplicated()                  | 检查是否有重复的数据；   |
| df.drop_duplicates()             | 删除重复的数据。         |

## 实例

```python
# 删除包含缺失值的行或列
df.dropna()

# 将缺失值替换为指定的值
df.fillna(0)

# 将指定值替换为新值
df.replace('old_value', 'new_value')

# 检查是否有重复的数据
df.duplicated()

# 删除重复的数据
df.drop_duplicates()
```

## 数据选择和切片

| 函数                                          | 说明                         |
| :-------------------------------------------- | :--------------------------- |
| df[column_name]                               | 选择指定的列；               |
| df.loc[row_index, column_name]                | 通过标签选择数据；           |
| df.iloc[row_index, column_index]              | 通过位置选择数据；           |
| df.ix[row_index, column_name]                 | 通过标签或位置选择数据；     |
| df.filter(items=[column_name1, column_name2]) | 选择指定的列；               |
| df.filter(regex='regex')                      | 选择列名匹配正则表达式的列； |
| df.sample(n)                                  | 随机选择 n 行数据。          |

### 实例

```python
# 选择指定的列
df['column_name']

# 通过标签选择数据
df.loc[row_index, column_name]

# 通过位置选择数据
df.iloc[row_index, column_index]

# 通过标签或位置选择数据
df.ix[row_index, column_name]

# 选择指定的列
df.filter(items=['column_name1', 'column_name2'])

# 选择列名匹配正则表达式的列
df.filter(regex='regex')

# 随机选择 n 行数据
df.sample(n=5)
```

## 数据排序

| 函数                                                         | 说明                 |
| :----------------------------------------------------------- | :------------------- |
| df.sort_values(column_name)                                  | 按照指定列的值排序； |
| df.sort_values([column_name1, column_name2], ascending=[True, False]) | 按照多个列的值排序； |
| df.sort_index()                                              | 按照索引排序。       |

## 实例

```python
# 按照指定列的值排序
df.sort_values('column_name')

# 按照多个列的值排序
df.sort_values(['column_name1', 'column_name2'], ascending=[True, False])

# 按照索引排序
df.sort_index()
```

## 数据分组和聚合

| 函数                                            | 说明                         |
| :---------------------------------------------- | :--------------------------- |
| df.groupby(column_name)                         | 按照指定列进行分组；         |
| df.aggregate(function_name)                     | 对分组后的数据进行聚合操作； |
| df.pivot_table(values, index, columns, aggfunc) | 生成透视表。                 |

## 实例

```python
# 按照指定列进行分组
df.groupby('column_name')

# 对分组后的数据进行聚合操作
df.aggregate('function_name')

# 生成透视表
df.pivot_table(values='value', index='index_column', columns='column_name', aggfunc='function_name')
```

## 数据合并

| 函数                               | 说明                             |
| :--------------------------------- | :------------------------------- |
| pd.concat([df1, df2])              | 将多个数据框按照行或列进行合并； |
| pd.merge(df1, df2, on=column_name) | 按照指定列将两个数据框进行合并。 |

## 实例

```python
# 将多个数据框按照行或列进行合并
df = pd.concat([df1, df2])

# 按照指定列将两个数据框进行合并
df = pd.merge(df1, df2, on='column_name')
```

## 数据选择和过滤

| 函数                                 | 说明                                   |
| :----------------------------------- | :------------------------------------- |
| df.loc[row_indexer, column_indexer]  | 按标签选择行和列。                     |
| df.iloc[row_indexer, column_indexer] | 按位置选择行和列。                     |
| df[df['column_name'] > value]        | 选择列中满足条件的行。                 |
| df.query('column_name > value')      | 使用字符串表达式选择列中满足条件的行。 |

------

## 数据统计和描述

| 函数          | 说明                                                 |
| :------------ | :--------------------------------------------------- |
| df.describe() | 计算基本统计信息，如均值、标准差、最小值、最大值等。 |
| df.mean()     | 计算每列的平均值。                                   |
| df.median()   | 计算每列的中位数。                                   |
| df.mode()     | 计算每列的众数。                                     |
| df.count()    | 计算每列非缺失值的数量。                             |

------

## 实例

假设我们有如下的 JSON 数据，数据保存到 **data.json** 文件：

## data.json 文件

```json
[
  {
    "name": "Alice",
    "age": 25,
    "gender": "female",
    "score": 80
  },
  {
    "name": "Bob",
    "age": null,
    "gender": "male",
    "score": 90
  },
  {
    "name": "Charlie",
    "age": 30,
    "gender": "male",
    "score": null
  },
  {
    "name": "David",
    "age": 35,
    "gender": "male",
    "score": 70
  }
]
```

我们可以使用 Pandas 读取 JSON 数据，并进行数据清洗和处理、数据选择和过滤、数据统计和描述等操作，具体如下：

```python
import pandas as pd

# 读取 JSON 数据
df = pd.read_json('data.json')

# 删除缺失值
df = df.dropna()

# 用指定的值填充缺失值
df = df.fillna({'age': 0, 'score': 0})

# 重命名列名
df = df.rename(columns={'name': '姓名', 'age': '年龄', 'gender': '性别', 'score': '成绩'})

# 按成绩排序
df = df.sort_values(by='成绩', ascending=False)

# 按性别分组并计算平均年龄和成绩
grouped = df.groupby('性别').agg({'年龄': 'mean', '成绩': 'mean'})

# 选择成绩大于等于90的行，并只保留姓名和成绩两列
df = df.loc[df['成绩'] >= 90, ['姓名', '成绩']]

# 计算每列的基本统计信息
stats = df.describe()

# 计算每列的平均值
mean = df.mean()

# 计算每列的中位数
median = df.median()

# 计算每列的众数
mode = df.mode()

# 计算每列非缺失值的数量
count = df.count()
```

输出结果如下：

```
# df
   姓名  年龄 性别  成绩
1  Bob   0  male  90

# grouped
             年龄  成绩
性别                
female  25.000000  80
male    27.500000  80

# stats
         成绩
count   1.0
mean   90.0
std     NaN
min    90.0
25%    90.0
50%    90.0
75%    90.0
max    90.0

# mean
成绩    90.0
dtype: float64

# median
成绩    90.0
dtype: float64

# mode
    姓名    成绩
0  Bob  90.0

# count
姓名    1
成绩    1
dtype: int64
```
