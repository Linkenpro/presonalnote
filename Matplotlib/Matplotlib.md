# Matplotlib 教程

![img](https://www.runoob.com/wp-content/uploads/2021/06/Matplotlib.png)

Matplotlib 是 Python 的绘图库，它能让使用者很轻松地将数据图形化，并且提供多样化的输出格式。

Matplotlib 可以用来绘制各种静态，动态，交互式的图表。

Matplotlib 是一个非常强大的 Python 画图工具，我们可以使用该工具将很多数据通过图表的形式更直观的呈现出来。

Matplotlib 可以绘制线图、散点图、等高线图、条形图、柱状图、3D 图形、甚至是图形动画等等。

------

## 学习本教程前你需要了解

在开学习 Matplotlib 教程之前，我们需要具备基本的 Python 基础，如果你对 Python 还不了解，可以阅读我们的教程：

- Python 3.x 教程
- Numpy 教程

------

## Matplotlib 应用

Matplotlib 通常与 NumPy 和 SciPy（Scientific Python）一起使用， 这种组合广泛用于替代 MatLab，是一个强大的科学计算环境，有助于我们通过 Python 学习数据科学或者机器学习。

SciPy 是一个开源的 Python 算法库和数学工具包。

SciPy 包含的模块有最优化、线性代数、积分、插值、特殊函数、快速傅里叶变换、信号处理和图像处理、常微分方程求解和其他科学与工程中常用的计算。

------

## 相关链接

- NumPy 官网 http://www.numpy.org/
- NumPy 源代码：https://github.com/numpy/numpy
- SciPy 官网：https://www.scipy.org/
- SciPy 源代码：https://github.com/scipy/scipy
- Matplotlib 官网：https://matplotlib.org/
- Matplotlib 源代码：https://github.com/matplotlib/matplotlib
- pandas visualization官方文档：https://pandas.pydata.org/docs/user_guide/visualization.html

# Matplotlib 安装

本章节，我们使用 pip 工具来安装 Matplotlib 库，如果还未安装该工具，可以参考 [Python pip 安装与使用](https://www.runoob.com/w3cnote/python-pip-install-usage.html)。

升级 pip：

```python
python3 -m pip install -U pip
```

安装 matplotlib 库：

```python
python3 -m pip install -U matplotlib
```

安装完成后，我们就可以通过 import 来导入 matplotlib 库：

```
import matplotlib
```

以下实例，我们通过导入 matplotlib 库，然后查看 matplotlib 库的版本号：

## 实例

```python
import matplotlib

print(matplotlib.__version__)
```

执行以上代码，输出结果如下：

```python
3.4.2
```

# Matplotlib Pyplot

Pyplot 是 Matplotlib 的子库，提供了和 MATLAB 类似的绘图 API。

Pyplot 是常用的绘图模块，能很方便让用户绘制 2D 图表。

Pyplot 包含一系列绘图函数的相关函数，每个函数会对当前的图像进行一些修改，例如：给图像加上标记，生新的图像，在图像中产生新的绘图区域等等。

使用的时候，我们可以使用 import 导入 pyplot 库，并设置一个别名 **plt**：

```python
import matplotlib.pyplot as plt
```

这样我们就可以使用 **plt** 来引用 Pyplot 包的方法。

以下是一些常用的 pyplot 函数：

- `plot()`：用于绘制线图和散点图
- `scatter()`：用于绘制散点图
- `bar()`：用于绘制垂直条形图和水平条形图
- `hist()`：用于绘制直方图
- `pie()`：用于绘制饼图
- `imshow()`：用于绘制图像
- `subplots()`：用于创建子图

除了这些基本的函数，pyplot 还提供了很多其他的函数，例如用于设置图表属性的函数、用于添加文本和注释的函数、用于保存图表到文件的函数等等。

以下实例，我们通过两个坐标 **(0,0)** 到 **(6,100)** 来绘制一条线:

```python
import matplotlib.pyplot as plt
import numpy as np

xpoints = np.array([0, 6])
ypoints = np.array([0, 100])

plt.plot(xpoints, ypoints)
plt.show()
```

输出结果如下所示：

![img](https://www.runoob.com/wp-content/uploads/2021/06/A8A7DE3A-DFF7-41DC-95BC-FD987E3E8CE2.jpg)

以上实例中我们使用了 Pyplot 的 **plot()** 函数， **plot()** 函数是绘制二维图形的最基本函数。

**plot()** 用于画图它可以绘制点和线，语法格式如下：

```python
# 画单条线
plot([x], y, [fmt], *, data=None, **kwargs)
# 画多条线
plot([x], y, [fmt], [x2], y2, [fmt2], ..., **kwargs)
```

参数说明：

- **x, y：**点或线的节点，x 为 x 轴数据，y 为 y 轴数据，数据可以列表或数组。
- **fmt：**可选，定义基本格式（如颜色、标记和线条样式）。
- ***\*kwargs：**可选，用在二维平面图上，设置指定属性，如标签，线的宽度等。

```py
>>> plot(x, y)        # 创建 y 中数据与 x 中对应值的二维线图，使用默认样式
>>> plot(x, y, 'bo')  # 创建 y 中数据与 x 中对应值的二维线图，使用蓝色实心圈绘制
>>> plot(y)           # x 的值为 0..N-1
>>> plot(y, 'r+')     # 使用红色 + 号
```

**颜色字符：**'b' 蓝色，'m' 洋红色，'g' 绿色，'y' 黄色，'r' 红色，'k' 黑色，'w' 白色，'c' 青绿色，'#008000' RGB 颜色符串。多条曲线不指定颜色时，会自动选择不同颜色。

**线型参数：**'‐' 实线，'‐‐' 破折线，'‐.' 点划线，':' 虚线。

**标记字符：**'.' 点标记，',' 像素标记(极小点)，'o' 实心圈标记，'v' 倒三角标记，'^' 上三角标记，'>' 右三角标记，'<' 左三角标记...等等。

如果我们要绘制坐标 (1, 3) 到 (8, 10) 的线，我们就需要传递两个数组 [1, 8] 和 [3, 10] 给 **plot** 函数：

```py
import matplotlib.pyplot as plt
import numpy as np

xpoints = np.array([1, 8])
ypoints = np.array([3, 10])

plt.plot(xpoints, ypoints)
plt.show()
```

以上代码输出结果为：

![img](https://www.runoob.com/wp-content/uploads/2021/06/img_matplotlib_plotting1.png)

如果我们只想绘制两个坐标点，而不是一条线，可以使用 **o** 参数，表示一个实心圈的标记：

###### 绘制坐标 (1, 3) 和 (8, 10) 的两个点

```py
import matplotlib.pyplot as plt
import numpy as np

xpoints = np.array([1, 8])
ypoints = np.array([3, 10])

plt.plot(xpoints, ypoints, 'o')
plt.show()
```

以上代码输出结果为：

![img](https://www.runoob.com/wp-content/uploads/2021/06/img_matplotlib_plot_o.png)

我们也可以绘制任意数量的点，只需确保两个轴上的点数相同即可。

绘制一条不规则线，坐标为 (1, 3) 、 (2, 8) 、(6, 1) 、(8, 10)，对应的两个数组为：[1, 2, 6, 8] 与 [3, 8, 1, 10]。

```python
import matplotlib.pyplot as plt
import numpy as np

xpoints = np.array([1, 2, 6, 8])
ypoints = np.array([3, 8, 1, 10])

plt.plot(xpoints, ypoints)
plt.show()
```

以上代码输出结果为：

![img](https://www.runoob.com/wp-content/uploads/2021/06/img_matplotlib_plotting2.png)

如果我们不指定 x 轴上的点，则 x 会根据 y 的值来设置为 **0, 1, 2, 3..N-1**。

```py
import matplotlib.pyplot as plt
import numpy as np

ypoints = np.array([3, 10])

plt.plot(ypoints)
plt.show()
```

以上代码输出结果为：

![img](https://www.runoob.com/wp-content/uploads/2021/06/matplot-1.png)

从上图可以看出 x 的值默认设置为 **[0, 1]**。

再看一个有更多值的实例：

```py
import matplotlib.pyplot as plt
import numpy as np

ypoints = np.array([3, 8, 1, 10, 5, 7])

plt.plot(ypoints)
plt.show()
```

以上代码输出结果为：

![img](https://www.runoob.com/wp-content/uploads/2021/06/img_matplotlib_plotting4.png)

从上图可以看出 **x** 的值默认设置为 **[0, 1, 2, 3, 4, 5]**。

以下实例我们绘制一个正弦和余弦图，在 plt.plot() 参数中包含两对 **x,y** 值，第一对是 **x,y**，这对应于正弦函数，第二对是 **x,z**，这对应于余弦函数。

```py
import matplotlib.pyplot as plt
import numpy as np

x = np.arange(0,4*np.pi,0.1)    # start,stop,step
y = np.sin(x)
z = np.cos(x)
plt.plot(x,y,x,z)
plt.show()
```

![img](https://www.runoob.com/wp-content/uploads/2021/06/pl-sin-cos.png)

# Matplotlib 绘图标记

绘图过程如果我们想要给坐标自定义一些不一样的标记，就可以使用 **plot()** 方法的 **marker** 参数来定义。

以下实例定义了实心圆标记：

```py
import matplotlib.pyplot as plt
import numpy as np

ypoints = np.array([1,3,4,5,8,9,6,1,3,4,5,2,4])

plt.plot(ypoints, marker = 'o')
plt.show()
```



显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl_marker01.png)

**marker** 可以定义的符号如下：

**marker** 可以定义的符号如下：

| 标记               | 符号                                          | 描述                                         |
| :----------------- | :-------------------------------------------- | :------------------------------------------- |
| "."                | ![m00](https://www.runoob.com/images/m00.png) | 点                                           |
| ","                | ![m01](https://www.runoob.com/images/m01.png) | 像素点                                       |
| "o"                | ![m02](https://www.runoob.com/images/m02.png) | 实心圆                                       |
| "v"                | ![m03](https://www.runoob.com/images/m03.png) | 下三角                                       |
| "^"                | ![m04](https://www.runoob.com/images/m04.png) | 上三角                                       |
| "<"                | ![m05](https://www.runoob.com/images/m05.png) | 左三角                                       |
| ">"                | ![m06](https://www.runoob.com/images/m06.png) | 右三角                                       |
| "1"                | ![m07](https://www.runoob.com/images/m07.png) | 下三叉                                       |
| "2"                | ![m08](https://www.runoob.com/images/m08.png) | 上三叉                                       |
| "3"                | ![m09](https://www.runoob.com/images/m09.png) | 左三叉                                       |
| "4"                | ![m10](https://www.runoob.com/images/m10.png) | 右三叉                                       |
| "8"                | ![m11](https://www.runoob.com/images/m11.png) | 八角形                                       |
| "s"                | ![m12](https://www.runoob.com/images/m12.png) | 正方形                                       |
| "p"                | ![m13](https://www.runoob.com/images/m13.png) | 五边形                                       |
| "P"                | ![m23](https://www.runoob.com/images/m23.png) | 加号（填充）                                 |
| "*"                | ![m14](https://www.runoob.com/images/m14.png) | 星号                                         |
| "h"                | ![m15](https://www.runoob.com/images/m15.png) | 六边形 1                                     |
| "H"                | ![m16](https://www.runoob.com/images/m16.png) | 六边形 2                                     |
| "+"                | ![m17](https://www.runoob.com/images/m17.png) | 加号                                         |
| "x"                | ![m18](https://www.runoob.com/images/m18.png) | 乘号 x                                       |
| "X"                | ![m24](https://www.runoob.com/images/m24.png) | 乘号 x (填充)                                |
| "D"                | ![m19](https://www.runoob.com/images/m19.png) | 菱形                                         |
| "d"                | ![m20](https://www.runoob.com/images/m20.png) | 瘦菱形                                       |
| "\|"               | ![m21](https://www.runoob.com/images/m21.png) | 竖线                                         |
| "_"                | ![m22](https://www.runoob.com/images/m22.png) | 横线                                         |
| 0 (TICKLEFT)       | ![m25](https://www.runoob.com/images/m25.png) | 左横线                                       |
| 1 (TICKRIGHT)      | ![m26](https://www.runoob.com/images/m26.png) | 右横线                                       |
| 2 (TICKUP)         | ![m27](https://www.runoob.com/images/m27.png) | 上竖线                                       |
| 3 (TICKDOWN)       | ![m28](https://www.runoob.com/images/m28.png) | 下竖线                                       |
| 4 (CARETLEFT)      | ![m29](https://www.runoob.com/images/m29.png) | 左箭头                                       |
| 5 (CARETRIGHT)     | ![m30](https://www.runoob.com/images/m30.png) | 右箭头                                       |
| 6 (CARETUP)        | ![m31](https://www.runoob.com/images/m31.png) | 上箭头                                       |
| 7 (CARETDOWN)      | ![m32](https://www.runoob.com/images/m32.png) | 下箭头                                       |
| 8 (CARETLEFTBASE)  | ![m33](https://www.runoob.com/images/m33.png) | 左箭头 (中间点为基准)                        |
| 9 (CARETRIGHTBASE) | ![m34](https://www.runoob.com/images/m34.png) | 右箭头 (中间点为基准)                        |
| 10 (CARETUPBASE)   | ![m35](https://www.runoob.com/images/m35.png) | 上箭头 (中间点为基准)                        |
| 11 (CARETDOWNBASE) | ![m36](https://www.runoob.com/images/m36.png) | 下箭头 (中间点为基准)                        |
| "None", " " or ""  |                                               | 没有任何标记                                 |
| '$...$'            | ![m37](https://www.runoob.com/images/m37.png) | 渲染指定的字符。例如 "$f$" 以字母 f 为标记。 |

以下实例定义了 ***** 标记：

```py
import matplotlib.pyplot as plt
import numpy as np

ypoints = np.array([1,3,4,5,8,9,6,1,3,4,5,2,4])

plt.plot(ypoints, marker = '*')
plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl_marker-1.png)

以下实例定义了下箭头：

```py
import matplotlib.pyplot as plt
import matplotlib.markers

plt.plot([1, 2, 3], marker=matplotlib.markers.CARETDOWNBASE)
plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl_marker_2.png)

### fmt 参数——标记样式，线条样式与颜色

fmt 参数定义了基本格式，如标记、线条样式和颜色。

```
fmt = '[marker][line][color]'
```

例如 **o:r**，**o** 表示实心圆标记，**:** 表示虚线，**r** 表示颜色为红色

```py
import matplotlib.pyplot as plt
import numpy as np

ypoints = np.array([6, 2, 13, 10])

plt.plot(ypoints, 'o:r')
plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl_marker-3.png)

线类型：

| 线类型标记 | 描述   |
| :--------- | :----- |
| '-'        | 实线   |
| ':'        | 虚线   |
| '--'       | 破折线 |
| '-.'       | 点划线 |

颜色类型：（rgb，cmyk，white）7种

| 颜色标记 | 描述 |
| :------- | :--- |
| 'r'      | 红色 |
| 'g'      | 绿色 |
| 'b'      | 蓝色 |
| 'c'      | 青色 |
| 'm'      | 品红 |
| 'y'      | 黄色 |
| 'k'      | 黑色 |
| 'w'      | 白色 |

### 标记大小与颜色

我们可以自定义标记的大小与颜色，使用的参数分别是：

- markersize，简写为 **ms**：定义标记的大小。
- markerfacecolor，简写为 **mfc**：定义标记内部的颜色。
- markeredgecolor，简写为 **mec**：定义标记边框的颜色。

设置标记大小：

```py
import matplotlib.pyplot as plt
import numpy as np

ypoints = np.array([6, 2, 13, 10])

plt.plot(ypoints, marker = 'o', ms = 20)
plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl_marker-5.png)

设置标记外边框颜色：

```py
import matplotlib.pyplot as plt
import numpy as np

ypoints = np.array([6, 2, 13, 10])

plt.plot(ypoints, marker = 'o', ms = 20, mec = 'r')
plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl_marker-6.png)

设置标记内部颜色：

```py
import matplotlib.pyplot as plt
import numpy as np

ypoints = np.array([6, 2, 13, 10])

plt.plot(ypoints, marker = 'o', ms = 20, mfc = 'r')
plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl_marker-7.png)

自定义标记内部与边框的颜色：

```py
import matplotlib.pyplot as plt
import numpy as np

ypoints = np.array([6, 2, 13, 10])
plt.plot(ypoints, marker = 'o', ms = 20, mec = '#4CAF50', mfc = '#4CAF50')
plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl_marker-8.png)

# Matplotlib 绘图线

绘图过程如果我们自定义线的样式，包括线的类型、颜色和大小等。

### 线的类型

线的类型可以使用 **linestyle** 参数来定义，简写为 **ls**。

| 类型           | 简写      | 说明   |
| :------------- | :-------- | :----- |
| 'solid' (默认) | '-'       | 实线   |
| 'dotted'       | ':'       | 点虚线 |
| 'dashed'       | '--'      | 破折线 |
| 'dashdot'      | '-.'      | 点划线 |
| 'None'         | '' 或 ' ' | 不画线 |

```py
import matplotlib.pyplot as plt
import numpy as np

ypoints = np.array([6, 2, 13, 10])

plt.plot(ypoints, linestyle = 'dotted')
plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl_line-1.png)

使用简写：

```py
import matplotlib.pyplot as plt
import numpy as np

ypoints = np.array([6, 2, 13, 10])

plt.plot(ypoints, ls = '-.')
plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl_line-2.png)

### 线的颜色

线的颜色可以使用 **color** 参数来定义，简写为 **c**。

颜色类型：

| 颜色标记 | 描述 |
| :------- | :--- |
| 'r'      | 红色 |
| 'g'      | 绿色 |
| 'b'      | 蓝色 |
| 'c'      | 青色 |
| 'm'      | 品红 |
| 'y'      | 黄色 |
| 'k'      | 黑色 |
| 'w'      | 白色 |

当然也可以自定义颜色类型，例如：**SeaGreen、#8FBC8F** 等，完整样式可以参考**HTML 颜色值**。

```py
import matplotlib.pyplot as plt
import numpy as np

ypoints = np.array([6, 2, 13, 10])

plt.plot(ypoints, color = 'r')
plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl_line-3.png)

```py
import matplotlib.pyplot as plt
import numpy as np

ypoints = np.array([6, 2, 13, 10])

plt.plot(ypoints, c = '#8FBC8F')
plt.show()
```

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl_line-4.png)

```py
import matplotlib.pyplot as plt
import numpy as np

ypoints = np.array([6, 2, 13, 10])

plt.plot(ypoints, c = 'SeaGreen')
plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl_line-5.png)

### 线的宽度

线的宽度可以使用 **linewidth** 参数来定义，简写为 **lw**，值可以是浮点数，如：**1**、**2.0**、**5.67** 等。

```py
import matplotlib.pyplot as plt
import numpy as np

ypoints = np.array([6, 2, 13, 10])

plt.plot(ypoints, linewidth = '12.5')
plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl_line-6.png)

### 多条线

plot() 方法中可以包含多对 x,y 值来绘制多条线。

```py
import matplotlib.pyplot as plt
import numpy as np

y1 = np.array([3, 7, 5, 9])
y2 = np.array([6, 2, 13, 10])

plt.plot(y1)
plt.plot(y2)

plt.show()
```

从上图可以看出 **x** 的值默认设置为 **[0, 1, 2, 3]**。

显示结果如下：

我们也可以自己设置 x 坐标等值：

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl_line-7.png)

```py
import matplotlib.pyplot as plt
import numpy as np

x1 = np.array([0, 1, 2, 3])
y1 = np.array([3, 7, 5, 9])
x2 = np.array([0, 1, 2, 3])
y2 = np.array([6, 2, 13, 10])

plt.plot(x1, y1, x2, y2)
plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl_line-8.png)

# Matplotlib 轴标签和标题

我们可以使用 **xlabel()** 和 **ylabel()** 方法来设置 x 轴和 y 轴的标签。

```py
import numpy as np
import matplotlib.pyplot as plt

x = np.array([1, 2, 3, 4])
y = np.array([1, 4, 9, 16])
plt.plot(x, y)

plt.xlabel("x - label")     # 横坐标标签
plt.ylabel("y - label")     # 纵坐标标签

plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl_label-1.png)

### 标题

我们可以使用 **title()** 方法来设置标题。

```py
import numpy as np
import matplotlib.pyplot as plt

x = np.array([1, 2, 3, 4])
y = np.array([1, 4, 9, 16])
plt.plot(x, y)

plt.title("RUNOOB TEST TITLE")	# 顶部标题
plt.xlabel("x - label")
plt.ylabel("y - label")

plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl_title-1.png)

### 图形中文显示

Matplotlib 默认情况不支持中文，我们可以使用以下简单的方法来解决。

这里我们使用思源黑体，思源黑体是 Adobe 与 Google 推出的一款开源字体。

官网：https://source.typekit.com/source-han-serif/cn/

GitHub 地址：https://github.com/adobe-fonts/source-han-sans/tree/release/OTF/SimplifiedChinese

打开链接后，在里面选一个就好了：

![img](https://www.runoob.com/wp-content/uploads/2020/07/134652C4-1164-466B-ACA2-ECE8B7E6F2AF.jpg)

你也可以在网盘下载: https://pan.baidu.com/s/10-w1JbXZSnx3Tm6uGpPGOw，提取码：**yxqu**。

可以下载个 OTF 字体，比如 SourceHanSansSC-Bold.otf，将该文件文件放在当前执行的代码文件中：

SourceHanSansSC-Bold.otf 文件放在当前执行的代码文件中：

```py
import numpy as np 
from matplotlib import pyplot as plt 
import matplotlib
 
# fname 为 你下载的字体库路径，注意 SourceHanSansSC-Bold.otf 字体的路径
zhfont1 = matplotlib.font_manager.FontProperties(fname="SourceHanSansSC-Bold.otf") 
 
x = np.arange(1,11) 
y =  2  * x +  5 
plt.title("菜鸟教程 - 测试", fontproperties=zhfont1) 
 
# fontproperties 设置中文显示，fontsize 设置字体大小
plt.xlabel("x 轴", fontproperties=zhfont1)
plt.ylabel("y 轴", fontproperties=zhfont1)
plt.plot(x,y) 
plt.show()
```

![img](https://www.runoob.com/wp-content/uploads/2018/10/246E0137-BFFA-40D1-B6E1-8D4A2789B12F.jpg)

*此外，我们还可以使用系统的字体：*

```py
from matplotlib import pyplot as plt
import matplotlib
a=sorted([f.name for f in matplotlib.font_manager.fontManager.ttflist])

for i in a:
    print(i)
    
# 打印出你的 font_manager 的 ttflist 中所有注册的名字，找一个看中文字体例如：STFangsong(仿宋）,然后添加以下代码即可：

plt.rcParams['font.family']=['STFangsong']
```

此外我们还可以自定义字体的样式：

```py
import numpy as np 
from matplotlib import pyplot as plt 
import matplotlib
 
# fname 为 你下载的字体库路径，注意 SourceHanSansSC-Bold.otf 字体的路径，size 参数设置字体大小
zhfont1 = matplotlib.font_manager.FontProperties(fname="SourceHanSansSC-Bold.otf", size=18) 
font1 = {'color':'blue','size':20}
font2 = {'color':'darkred','size':15}
x = np.arange(1,11) 
y =  2  * x +  5 

# fontdict 可以使用 css 来设置字体样式
plt.title("菜鸟教程 - 测试", fontproperties=zhfont1, fontdict = font1) 
 
# fontproperties 设置中文显示，fontsize 设置字体大小
plt.xlabel("x 轴", fontproperties=zhfont1)
plt.ylabel("y 轴", fontproperties=zhfont1)
plt.plot(x,y) 
plt.show()
```

输出结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/x-label-2.png)

### 标题与标签的定位

**title()** 方法提供了 **loc** 参数来设置标题显示的位置，可以设置为: **'left', 'right', 和 'center'， 默认值为 'center'**。

**xlabel()** 方法提供了 **loc** 参数来设置 x 轴显示的位置，可以设置为: **'left', 'right', 和 'center'， 默认值为 'center'**。

**ylabel()** 方法提供了 **loc** 参数来设置 y 轴显示的位置，可以设置为: **'bottom', 'top', 和 'center'， 默认值为 'center'**。

```py
import numpy as np 
from matplotlib import pyplot as plt 
import matplotlib
 
# fname 为 你下载的字体库路径，注意 SourceHanSansSC-Bold.otf 字体的路径，size 参数设置字体大小
zhfont1 = matplotlib.font_manager.FontProperties(fname="SourceHanSansSC-Bold.otf", size=18) 
font1 = {'color':'blue','size':20}
font2 = {'color':'darkred','size':15}
x = np.arange(1,11) 
y =  2  * x +  5 

# fontdict 可以使用 css 来设置字体样式
plt.title("菜鸟教程 - 测试", fontproperties=zhfont1, fontdict = font1, loc="left") 
 
# fontproperties 设置中文显示，fontsize 设置字体大小
plt.xlabel("x 轴", fontproperties=zhfont1, loc="left")
plt.ylabel("y 轴", fontproperties=zhfont1, loc="top")
plt.plot(x,y) 
plt.show()
```

输出结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl_label-3.png)

# Matplotlib 网格线

我们可以使用 pyplot 中的 grid() 方法来设置图表中的网格线。

grid() 方法语法格式如下：

```
matplotlib.pyplot.grid(b=None, which='major', axis='both', )
```

**参数说明：**

- **b**：可选，默认为 None，可以设置布尔值，true 为显示网格线，false 为不显示，如果设置 **kwargs 参数，则值为 true。
- **which**：可选，可选值有 'major'、'minor' 和 'both'，默认为 'major'，表示应用更改的网格线。
- **axis**：可选，设置显示哪个方向的网格线，可以是取 'both'（默认），'x' 或 'y'，分别表示两个方向，x 轴方向或 y 轴方向。
- ***\*kwargs**：可选，设置网格样式，可以是 color='r', linestyle='-' 和 linewidth=2，分别表示网格线的颜色，样式和宽度。

以下实例添加一个简单的网格线，参数使用默认值：

```py
import numpy as np
import matplotlib.pyplot as plt

x = np.array([1, 2, 3, 4])
y = np.array([1, 4, 9, 16])


plt.title("RUNOOB grid() Test")
plt.xlabel("x - label")
plt.ylabel("y - label")

plt.plot(x, y)

plt.grid() # 设置默认网格线

plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl_grid-1.png)

以下实例添加一个简单的网格线，axis 参数使用 x，设置 x 轴方向显示网格线：

```py
import numpy as np
import matplotlib.pyplot as plt

x = np.array([1, 2, 3, 4])
y = np.array([1, 4, 9, 16])


plt.title("RUNOOB grid() Test")
plt.xlabel("x - label")
plt.ylabel("y - label")

plt.plot(x, y)

plt.grid(axis='x') # 设置 y 就在轴方向显示网格线

plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl_grid-2.png)

以下实例添加一个简单的网格线，并设置网格线的样式，格式如下：

```
grid(color = 'color', linestyle = 'linestyle', linewidth = number)
```

**参数说明：**

**color：**'b' 蓝色，'m' 洋红色，'g' 绿色，'y' 黄色，'r' 红色，'k' 黑色，'w' 白色，'c' 青绿色，'#008000' RGB 颜色符串。

**linestyle：**'‐' 实线，'‐‐' 破折线，'‐.' 点划线，':' 虚线。

**linewidth**：设置线的宽度，可以设置一个数字。

```py
import numpy as np
import matplotlib.pyplot as plt

x = np.array([1, 2, 3, 4])
y = np.array([1, 4, 9, 16])


plt.title("RUNOOB grid() Test")
plt.xlabel("x - label")
plt.ylabel("y - label")

plt.plot(x, y)

plt.grid(color = 'r', linestyle = '--', linewidth = 0.5)

plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl_grid-3.png)

# Matplotlib 绘制多图

我们可以使用 pyplot 中的 **subplot()** 和 **subplots()** 方法来绘制多个子图。

**subplot()** 方法在绘图时需要指定位置，**subplots()** 方法可以一次生成多个，在调用时只需要调用生成对象的 ax 即可。

### subplot

```py
subplot(nrows, ncols, index, **kwargs)
subplot(pos, **kwargs)
subplot(**kwargs)
subplot(ax)
```

以上函数将整个绘图区域分成 nrows 行和 ncols 列，然后从左到右，从上到下的顺序对每个子区域进行编号 **1...N** ，左上的子区域的编号为 1、右下的区域编号为 N，编号可以通过参数 **index** 来设置。

设置 numRows ＝ 1，numCols ＝ 2，就是将图表绘制成 1x2 的图片区域, 对应的坐标为：

```
(1, 1), (1, 2)
```

**plotNum ＝ 1**, 表示的坐标为(1, 1), 即第一行第一列的子图。

**plotNum ＝ 2**, 表示的坐标为(1, 2), 即第一行第二列的子图。

```py
import matplotlib.pyplot as plt
import numpy as np

#plot 1:
xpoints = np.array([0, 6])
ypoints = np.array([0, 100])

plt.subplot(1, 2, 1)
plt.plot(xpoints,ypoints)
plt.title("plot 1")

#plot 2:
x = np.array([1, 2, 3, 4])
y = np.array([1, 4, 9, 16])

plt.subplot(1, 2, 2)
plt.plot(x,y)
plt.title("plot 2")

plt.suptitle("RUNOOB subplot Test")
plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl_subplot-1.png)

设置 numRows ＝ 2，numCols ＝ 2，就是将图表绘制成 2x2 的图片区域, 对应的坐标为：

```
(1, 1), (1, 2)
(2, 1), (2, 2)
```

**plotNum ＝ 1**, 表示的坐标为(1, 1), 即第一行第一列的子图。

**plotNum ＝ 2**, 表示的坐标为(1, 2), 即第一行第二列的子图。

**plotNum ＝ 3**, 表示的坐标为(2, 1), 即第二行第一列的子图。

**plotNum ＝ 4**, 表示的坐标为(2, 2), 即第二行第二列的子图。

```py
import matplotlib.pyplot as plt
import numpy as np

#plot 1:
x = np.array([0, 6])
y = np.array([0, 100])

plt.subplot(2, 2, 1)
plt.plot(x,y)
plt.title("plot 1")

#plot 2:
x = np.array([1, 2, 3, 4])
y = np.array([1, 4, 9, 16])

plt.subplot(2, 2, 2)
plt.plot(x,y)
plt.title("plot 2")

#plot 3:
x = np.array([1, 2, 3, 4])
y = np.array([3, 5, 7, 9])

plt.subplot(2, 2, 3)
plt.plot(x,y)
plt.title("plot 3")

#plot 4:
x = np.array([1, 2, 3, 4])
y = np.array([4, 5, 6, 7])

plt.subplot(2, 2, 4)
plt.plot(x,y)
plt.title("plot 4")

plt.suptitle("RUNOOB subplot Test")
plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl_subplot-2.png)

### subplots()

subplots() 方法语法格式如下：

```
matplotlib.pyplot.subplots(nrows=1, ncols=1, *, sharex=False, sharey=False, squeeze=True, subplot_kw=None, gridspec_kw=None, **fig_kw)
```

**参数说明：**

- **nrows**：默认为 1，设置图表的行数。
- **ncols**：默认为 1，设置图表的列数。
- 
- **sharex、sharey**：设置 x、y 轴是否共享属性，默认为 false，可设置为 'none'、'all'、'row' 或 'col'。 False 或 none 每个子图的 x 轴或 y 轴都是独立的，True 或 'all'：所有子图共享 x 轴或 y 轴，'row' 设置每个子图行共享一个 x 轴或 y 轴，'col'：设置每个子图列共享一个 x 轴或 y 轴。
- **squeeze**：布尔值，默认为 True，表示额外的维度从返回的 Axes(轴)对象中挤出，对于 N*1 或 1*N 个子图，返回一个 1 维数组，对于 N*M，N>1 和 M>1 返回一个 2 维数组。如果设置为 False，则不进行挤压操作，返回一个元素为 Axes 实例的2维数组，即使它最终是1x1。
- **subplot_kw**：可选，字典类型。把字典的关键字传递给 add_subplot() 来创建每个子图。
- **gridspec_kw**：可选，字典类型。把字典的关键字传递给 GridSpec 构造函数创建子图放在网格里(grid)。
- ***\*fig_kw**：把详细的关键字参数传给 figure() 函数。

实例

```py
import matplotlib.pyplot as plt
import numpy as np

# 创建一些测试数据 -- 图1
x = np.linspace(0, 2*np.pi, 400)
y = np.sin(x**2)

# 创建一个画像和子图 -- 图2
fig, ax = plt.subplots()
ax.plot(x, y)
ax.set_title('Simple plot')

# 创建两个子图 -- 图3
f, (ax1, ax2) = plt.subplots(1, 2, sharey=True)
ax1.plot(x, y)
ax1.set_title('Sharing Y axis')
ax2.scatter(x, y)

# 创建四个子图 -- 图4
fig, axs = plt.subplots(2, 2, subplot_kw=dict(projection="polar"))
axs[0, 0].plot(x, y)
axs[1, 1].scatter(x, y)

# 共享 x 轴
plt.subplots(2, 2, sharex='col')

# 共享 y 轴
plt.subplots(2, 2, sharey='row')

# 共享 x 轴和 y 轴
plt.subplots(2, 2, sharex='all', sharey='all')

# 这个也是共享 x 轴和 y 轴
plt.subplots(2, 2, sharex=True, sharey=True)

# 创建标识为 10 的图，已经存在的则删除
fig, ax = plt.subplots(num=10, clear=True)

plt.show()
```

部分图表显示结果如下：

**图1**

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl-subplots-1.png)

**图2**

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl_subplots-2.png)

**图3**

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl-subplots-3.png)

**图4**

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl_subplots-4.png)

# Matplotlib 散点图

我们可以使用 pyplot 中的 scatter() 方法来绘制散点图。

scatter() 方法语法格式如下：

```py
matplotlib.pyplot.scatter(x, y, s=None, c=None, marker=None, cmap=None, norm=None, vmin=None, vmax=None, alpha=None, linewidths=None, *, edgecolors=None, plotnonfinite=False, data=None, **kwargs)
```

**参数说明：**

**x，y**：长度相同的数组，也就是我们即将绘制散点图的数据点，输入数据。

**s**：点的大小，默认 20，也可以是个数组，数组每个参数为对应点的大小。

**c**：点的颜色，默认蓝色 'b'，也可以是个 RGB 或 RGBA 二维行数组。

**marker**：点的样式，默认小圆圈 'o'。

**cmap**：Colormap，默认 None，标量或者是一个 colormap 的名字，只有 c 是一个浮点数数组的时才使用。如果没有申明就是 image.cmap。

**norm**：Normalize，默认 None，数据亮度在 0-1 之间，只有 c 是一个浮点数的数组的时才使用。

**vmin，vmax：**：亮度设置，在 norm 参数存在时会忽略。

**alpha：**：透明度设置，0-1 之间，默认 None，即不透明。

**linewidths：**：标记点的长度。

**edgecolors：**：颜色或颜色序列，默认为 'face'，可选值有 'face', 'none', None。

**plotnonfinite：**：布尔值，设置是否使用非限定的 c ( inf, -inf 或 nan) 绘制点。

***\*kwargs：**：其他参数。

以下实例 scatter() 函数接收长度相同的数组参数，一个用于 x 轴的值，另一个用于 y 轴上的值：

```py
import matplotlib.pyplot as plt
import numpy as np

x = np.array([1, 2, 3, 4, 5, 6, 7, 8])
y = np.array([1, 4, 9, 16, 7, 11, 23, 18])

plt.scatter(x, y)
plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl_scatter-1.png)

设置图标大小：

```py
import matplotlib.pyplot as plt
import numpy as np

x = np.array([1, 2, 3, 4, 5, 6, 7, 8])
y = np.array([1, 4, 9, 16, 7, 11, 23, 18])
sizes = np.array([20,50,100,200,500,1000,60,90])
plt.scatter(x, y, s=sizes)
plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl-scatter-5.png)

自定义点的颜色：

```py
import matplotlib.pyplot as plt
import numpy as np

x = np.array([1, 2, 3, 4, 5, 6, 7, 8])
y = np.array([1, 4, 9, 16, 7, 11, 23, 18])
colors = np.array(["red","green","black","orange","purple","beige","cyan","magenta"])

plt.scatter(x, y, c=colors)
plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl-scatter-2.png)

设置两组散点图：

```py
import matplotlib.pyplot as plt
import numpy as np

x = np.array([5,7,8,7,2,17,2,9,4,11,12,9,6])
y = np.array([99,86,87,88,111,86,103,87,94,78,77,85,86])
plt.scatter(x, y, color = 'hotpink')

x = np.array([2,2,8,1,15,8,12,9,7,3,11,4,7,14,12])
y = np.array([100,105,84,105,90,99,90,95,94,100,79,112,91,80,85])
plt.scatter(x, y, color = '#88c999')

plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/img_matplotlib_scatter_color.png)

使用随机数来设置散点图：

```py
import numpy as np
import matplotlib.pyplot as plt

# 随机数生成器的种子
np.random.seed(19680801)


N = 50
x = np.random.rand(N)
y = np.random.rand(N)
colors = np.random.rand(N)
area = (30 * np.random.rand(N))**2  # 0 to 15 point radii

plt.scatter(x, y, s=area, c=colors, alpha=0.5) # 设置颜色及透明度

plt.title("RUNOOB Scatter Test") # 设置标题

plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl-scatter-3.png)

### 颜色条 Colormap

Matplotlib 模块提供了很多可用的颜色条。

颜色条就像一个颜色列表，其中每种颜色都有一个范围从 0 到 100 的值。

下面是一个颜色条的例子：

![img](https://www.runoob.com/wp-content/uploads/2021/07/img_colorbar.png)

设置颜色条需要使用 cmap 参数，默认值为 'viridis'，之后颜色值设置为 0 到 100 的数组。

```py
import matplotlib.pyplot as plt
import numpy as np

x = np.array([5,7,8,7,2,17,2,9,4,11,12,9,6])
y = np.array([99,86,87,88,111,86,103,87,94,78,77,85,86])
colors = np.array([0, 10, 20, 30, 40, 45, 50, 55, 60, 70, 80, 90, 100])

plt.scatter(x, y, c=colors, cmap='viridis')

plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/img_matplotlib_scatter_colormap1.png)

如果要显示颜色条，需要使用 **plt.colorbar()** 方法：

```py
import matplotlib.pyplot as plt
import numpy as np

x = np.array([5,7,8,7,2,17,2,9,4,11,12,9,6])
y = np.array([99,86,87,88,111,86,103,87,94,78,77,85,86])
colors = np.array([0, 10, 20, 30, 40, 45, 50, 55, 60, 70, 80, 90, 100])

plt.scatter(x, y, c=colors, cmap='viridis')

plt.colorbar()

plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/img_matplotlib_scatter_colormap2.png)

换个颜色条参数， cmap 设置为 **afmhot_r**：

```py
import matplotlib.pyplot as plt
import numpy as np

x = np.array([5,7,8,7,2,17,2,9,4,11,12,9,6])
y = np.array([99,86,87,88,111,86,103,87,94,78,77,85,86])
colors = np.array([0, 10, 20, 30, 40, 45, 50, 55, 60, 70, 80, 90, 100])

plt.scatter(x, y, c=colors, cmap='afmhot_r')
plt.colorbar()
plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/xssss-pl-scatter.png)

颜色条参数值可以是以下值：

| 颜色名称         |      | 保留关键字         |
| :--------------- | :--- | :----------------- |
| Accent           |      | Accent_r           |
| Blues            |      | Blues_r            |
| BrBG             |      | BrBG_r             |
| BuGn             |      | BuGn_r             |
| BuPu             |      | BuPu_r             |
| CMRmap           |      | CMRmap_r           |
| Dark2            |      | Dark2_r            |
| GnBu             |      | GnBu_r             |
| Greens           |      | Greens_r           |
| Greys            |      | Greys_r            |
| OrRd             |      | OrRd_r             |
| Oranges          |      | Oranges_r          |
| PRGn             |      | PRGn_r             |
| Paired           |      | Paired_r           |
| Pastel1          |      | Pastel1_r          |
| Pastel2          |      | Pastel2_r          |
| PiYG             |      | PiYG_r             |
| PuBu             |      | PuBu_r             |
| PuBuGn           |      | PuBuGn_r           |
| PuOr             |      | PuOr_r             |
| PuRd             |      | PuRd_r             |
| Purples          |      | Purples_r          |
| RdBu             |      | RdBu_r             |
| RdGy             |      | RdGy_r             |
| RdPu             |      | RdPu_r             |
| RdYlBu           |      | RdYlBu_r           |
| RdYlGn           |      | RdYlGn_r           |
| Reds             |      | Reds_r             |
| Set1             |      | Set1_r             |
| Set2             |      | Set2_r             |
| Set3             |      | Set3_r             |
| Spectral         |      | Spectral_r         |
| Wistia           |      | Wistia_r           |
| YlGn             |      | YlGn_r             |
| YlGnBu           |      | YlGnBu_r           |
| YlOrBr           |      | YlOrBr_r           |
| YlOrRd           |      | YlOrRd_r           |
| afmhot           |      | afmhot_r           |
| autumn           |      | autumn_r           |
| binary           |      | binary_r           |
| bone             |      | bone_r             |
| brg              |      | brg_r              |
| bwr              |      | bwr_r              |
| cividis          |      | cividis_r          |
| cool             |      | cool_r             |
| coolwarm         |      | coolwarm_r         |
| copper           |      | copper_r           |
| cubehelix        |      | cubehelix_r        |
| flag             |      | flag_r             |
| gist_earth       |      | gist_earth_r       |
| gist_gray        |      | gist_gray_r        |
| gist_heat        |      | gist_heat_r        |
| gist_ncar        |      | gist_ncar_r        |
| gist_rainbow     |      | gist_rainbow_r     |
| gist_stern       |      | gist_stern_r       |
| gist_yarg        |      | gist_yarg_r        |
| gnuplot          |      | gnuplot_r          |
| gnuplot2         |      | gnuplot2_r         |
| gray             |      | gray_r             |
| hot              |      | hot_r              |
| hsv              |      | hsv_r              |
| inferno          |      | inferno_r          |
| jet              |      | jet_r              |
| magma            |      | magma_r            |
| nipy_spectral    |      | nipy_spectral_r    |
| ocean            |      | ocean_r            |
| pink             |      | pink_r             |
| plasma           |      | plasma_r           |
| prism            |      | prism_r            |
| rainbow          |      | rainbow_r          |
| seismic          |      | seismic_r          |
| spring           |      | spring_r           |
| summer           |      | summer_r           |
| tab10            |      | tab10_r            |
| tab20            |      | tab20_r            |
| tab20b           |      | tab20b_r           |
| tab20c           |      | tab20c_r           |
| terrain          |      | terrain_r          |
| twilight         |      | twilight_r         |
| twilight_shifted |      | twilight_shifted_r |
| viridis          |      | viridis_r          |
| winter           |      | winter_r           |

![img](https://www.runoob.com/wp-content/uploads/2021/07/sphx_glr_colormaps_001.webp)

![img](https://www.runoob.com/wp-content/uploads/2021/07/sphx_glr_colormaps_002.webp)

![img](https://www.runoob.com/wp-content/uploads/2021/07/sphx_glr_colormaps_003.webp)

![img](https://www.runoob.com/wp-content/uploads/2021/07/sphx_glr_colormaps_004.webp)

![img](https://www.runoob.com/wp-content/uploads/2021/07/sphx_glr_colormaps_005.webp)

![img](https://www.runoob.com/wp-content/uploads/2021/07/sphx_glr_colormaps_006.webp)

![img](https://www.runoob.com/wp-content/uploads/2021/07/sphx_glr_colormaps_007.webp)

# Matplotlib 柱形图

我们可以使用 pyplot 中的 bar() 方法来绘制柱形图。

bar() 方法语法格式如下：

```
matplotlib.pyplot.bar(x, height, width=0.8, bottom=None, *, align='center', data=None, **kwargs)
```

**参数说明：**

**x**：浮点型数组，柱形图的 x 轴数据。

**height**：浮点型数组，柱形图的高度。

**width**：浮点型数组，柱形图的宽度。

**bottom**：浮点型数组，底座的 y 坐标，默认 0。

**align**：柱形图与 x 坐标的对齐方式，'center' 以 x 位置为中心，这是默认值。 'edge'：将柱形图的左边缘与 x 位置对齐。要对齐右边缘的条形，可以传递负数的宽度值及 align='edge'。

***\*kwargs：**：其他参数。

以下实例我们简单实用 bar() 来创建一个柱形图:

```py
import matplotlib.pyplot as plt
import numpy as np

x = np.array(["Runoob-1", "Runoob-2", "Runoob-3", "C-RUNOOB"])
y = np.array([12, 22, 6, 18])

plt.bar(x,y)
plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl-bar-1.png)

垂直方向的柱形图可以使用 **barh()** 方法来设置：

```py
import matplotlib.pyplot as plt
import numpy as np

x = np.array(["Runoob-1", "Runoob-2", "Runoob-3", "C-RUNOOB"])
y = np.array([12, 22, 6, 18])

plt.barh(x,y)
plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl-bar-2.png)

设置柱形图颜色：

##### 实例

```py
import matplotlib.pyplot as plt
import numpy as np

x = np.array(["Runoob-1", "Runoob-2", "Runoob-3", "C-RUNOOB"])
y = np.array([12, 22, 6, 18])

plt.bar(x, y, color = "#4CAF50")
plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl-bar-3.png)

自定义各个柱形的颜色：

```py
import matplotlib.pyplot as plt
import numpy as np

x = np.array(["Runoob-1", "Runoob-2", "Runoob-3", "C-RUNOOB"])
y = np.array([12, 22, 6, 18])

plt.bar(x, y,  color = ["#4CAF50","red","hotpink","#556B2F"])
plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl-bar-6.png)

设置柱形图宽度，**bar()** 方法使用 **width** 设置，**barh()** 方法使用 **height** 设置 height

```py
import matplotlib.pyplot as plt
import numpy as np

x = np.array(["Runoob-1", "Runoob-2", "Runoob-3", "C-RUNOOB"])
y = np.array([12, 22, 6, 18])

plt.bar(x, y, width = 0.1)
plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl-bar-4.png)

实例

```py
import matplotlib.pyplot as plt
import numpy as np

x = np.array(["Runoob-1", "Runoob-2", "Runoob-3", "C-RUNOOB"])
y = np.array([12, 22, 6, 18])

plt.barh(x, y, height = 0.1)
plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl-bar-5.png)

# Matplotlib 饼图

饼图（Pie Chart）是一种常用的数据可视化图形，用来展示各类别在总体中所占的比例。

我们可以使用 pyplot 中的 **pie()** 方法来绘制饼图。

pie() 方法语法格式如下：

```
matplotlib.pyplot.pie(x, explode=None, labels=None, colors=None, autopct=None, pctdistance=0.6, shadow=False, labeldistance=1.1, startangle=0, radius=1, counterclock=True, wedgeprops=None, textprops=None, center=0, 0, frame=False, rotatelabels=False, *, normalize=None, data=None)[source]
```

**参数说明：**

> x：浮点型数组或列表，用于绘制饼图的数据，表示每个扇形的面积。
>
> explode：数组，表示各个扇形之间的间隔，默认值为0。
>
> labels：列表，各个扇形的标签，默认值为 None。
>
> colors：数组，表示各个扇形的颜色，默认值为 None。
>
> autopct：设置饼图内各个扇形百分比显示格式，%d%% 整数百分比，%0.1f 一位小数， %0.1f%% 一位小数百分比， %0.2f%% 两位小数百分比。
>
> labeldistance：标签标记的绘制位置，相对于半径的比例，默认值为 1.1，如 <1则绘制在饼图内侧。
>
> pctdistance：：类似于 labeldistance，指定 autopct 的位置刻度，默认值为 0.6。
>
> shadow：：布尔值 True 或 False，设置饼图的阴影，默认为 False，不设置阴影。
>
> radius：：设置饼图的半径，默认为 1。
>
> startangle：：用于指定饼图的起始角度，默认为从 x 轴正方向逆时针画起，如设定 =90 则从 y 轴正方向画起。
>
> counterclock：布尔值，用于指定是否逆时针绘制扇形，默认为 True，即逆时针绘制，False 为顺时针。
>
> wedgeprops ：字典类型，默认值 None。用于指定扇形的属性，比如边框线颜色、边框线宽度等。例如：wedgeprops={'linewidth':5} 设置 wedge 线宽为5。
> textprops ：字典类型，用于指定文本标签的属性，比如字体大小、字体颜色等，默认值为 None。
> center ：浮点类型的列表，用于指定饼图的中心位置，默认值：(0,0)。
> frame ：布尔类型，用于指定是否绘制饼图的边框，默认值：False。如果是 True，绘制带有表的轴框架。
> rotatelabels ：布尔类型，用于指定是否旋转文本标签，默认为 False。如果为 True，旋转每个 label 到指定的角度。
> data：用于指定数据。如果设置了 data 参数，则可以直接使用数据框中的列作为 x、labels 等参数的值，无需再次传递。

除此之外，pie() 函数还可以返回三个参数：

- `wedges`：一个包含扇形对象的列表。
- `texts`：一个包含文本标签对象的列表。
- `autotexts`：一个包含自动生成的文本标签对象的列表。

以下实例我们简单实用 pie() 来创建一个饼图:

```py
import matplotlib.pyplot as plt
import numpy as np

y = np.array([35, 25, 25, 15])

plt.pie(y)
plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/img_matplotlib_pie1.png)

设置饼图各个扇形的标签与颜色：

```py
import matplotlib.pyplot as plt
import numpy as np

y = np.array([35, 25, 25, 15])

plt.pie(y,
        labels=['A','B','C','D'], # 设置饼图标签
        colors=["#d5695d", "#5d8ca8", "#65a479", "#a564c9"], # 设置饼图颜色
       )
plt.title("RUNOOB Pie Test") # 设置标题
plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl-pie-2.png)

突出显示第二个扇形，并格式化输出百分比：

```py
import matplotlib.pyplot as plt

# 数据
sizes = [15, 30, 45, 10]

# 饼图的标签
labels = ['A', 'B', 'C', 'D']

# 饼图的颜色
colors = ['yellowgreen', 'gold', 'lightskyblue', 'lightcoral']

# 突出显示第二个扇形
explode = (0, 0.1, 0, 0)

# 绘制饼图
plt.pie(sizes, explode=explode, labels=labels, colors=colors,
        autopct='%1.1f%%', shadow=True, startangle=90)

# 标题
plt.title("RUNOOB Pie Test")

# 显示图形
plt.show()
```

我们定义了一个包含 4 个元素的列表 sizes，它表示各个类别在总体中所占的比例。然后，我们定义了一个包含 4 个元素的列表 labels，它表示各个类别的标签。接下来，我们定义了一个包含 4 个元素的列表 colors，它表示每个类别的颜色。然后，我们定义了一个包含 4 个元素的元组 explode，它用来指定是否突出某个扇形。接着，我们调用 plt.pie 函数来绘制饼图，其中传入了上述参数。最后，我们添加了一个标题，并调用 plt.show() 来显示图形。

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2021/07/runoob-pie-test-1.png)

实例

```py
import matplotlib.pyplot as plt
import numpy as np

y = np.array([35, 25, 25, 15])

plt.pie(y,
        labels=['A','B','C','D'], # 设置饼图标签
        colors=["#d5695d", "#5d8ca8", "#65a479", "#a564c9"], # 设置饼图颜色
        explode=(0, 0.2, 0, 0), # 第二部分突出显示，值越大，距离中心越远
        autopct='%.2f%%', # 格式化输出百分比
       )
plt.title("RUNOOB Pie Test")
plt.show()
```

![img](https://www.runoob.com/wp-content/uploads/2021/07/pl_pie-3.png)

> **注意：***默认情况下，第一个扇形的绘制是从 x 轴开始并逆时针移动：*

![img](https://www.runoob.com/wp-content/uploads/2021/07/03D59143-B345-4B36-A7CD-53F698AB5284.jpg)

# Matplotlib 直方图

我们可以使用 pyplot 中的 hist() 方法来绘制直方图。

hist() 方法是 Matplotlib 库中的 pyplot 子库中的一种用于绘制直方图的函数。

hist() 方法可以用于可视化数据的分布情况，例如观察数据的中心趋势、偏态和异常值等。

hist() 方法语法格式如下：

```
matplotlib.pyplot.hist(x, bins=None, range=None, density=False, weights=None, cumulative=False, bottom=None, histtype='bar', align='mid', orientation='vertical', rwidth=None, log=False, color=None, label=None, stacked=False, **kwargs)
```

**参数说明：**

- `x`：表示要绘制直方图的数据，可以是一个一维数组或列表。
- `bins`：可选参数，表示直方图的箱数。默认为10。
- `range`：可选参数，表示直方图的值域范围，可以是一个二元组或列表。默认为None，即使用数据中的最小值和最大值。
- `density`：可选参数，表示是否将直方图归一化。默认为False，即直方图的高度为每个箱子内的样本数，而不是频率或概率密度。
- `weights`：可选参数，表示每个数据点的权重。默认为None。
- `cumulative`：可选参数，表示是否绘制累积分布图。默认为False。
- `bottom`：可选参数，表示直方图的起始高度。默认为None。
- `histtype`：可选参数，表示直方图的类型，可以是'bar'、'barstacked'、'step'、'stepfilled'等。默认为'bar'。
- `align`：可选参数，表示直方图箱子的对齐方式，可以是'left'、'mid'、'right'。默认为'mid'。
- `orientation`：可选参数，表示直方图的方向，可以是'vertical'、'horizontal'。默认为'vertical'。
- `rwidth`：可选参数，表示每个箱子的宽度。默认为None。
- `log`：可选参数，表示是否在y轴上使用对数刻度。默认为False。
- `color`：可选参数，表示直方图的颜色。
- `label`：可选参数，表示直方图的标签。
- `stacked`：可选参数，表示是否堆叠不同的直方图。默认为False。
- `**kwargs`：可选参数，表示其他绘图参数。

以下实例我们简单实用 hist() 来创建一个直方图:

```py
import matplotlib.pyplot as plt
import numpy as np

# 生成一组随机数据
data = np.random.randn(1000)

# 绘制直方图
plt.hist(data, bins=30, color='skyblue', alpha=0.8)

# 设置图表属性
plt.title('RUNOOB hist() Test')
plt.xlabel('Value')
plt.ylabel('Frequency')

# 显示图表
plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2023/04/runoob-test-hist.png)

以下实例演示了如何使用 hist() 函数绘制多个数据组的直方图，并进行比较：

```py
import matplotlib.pyplot as plt
import numpy as np

# 生成三组随机数据
data1 = np.random.normal(0, 1, 1000)
data2 = np.random.normal(2, 1, 1000)
data3 = np.random.normal(-2, 1, 1000)

# 绘制直方图
plt.hist(data1, bins=30, alpha=0.5, label='Data 1')
plt.hist(data2, bins=30, alpha=0.5, label='Data 2')
plt.hist(data3, bins=30, alpha=0.5, label='Data 3')

# 设置图表属性
plt.title('RUNOOB hist() TEST')
plt.xlabel('Value')
plt.ylabel('Frequency')
plt.legend()

# 显示图表
plt.show()
```

以上实例中我们生成了三组不同的随机数据，并使用 hist() 函数绘制了它们的直方图。通过设置不同的均值和标准差，我们可以生成具有不同分布特征的随机数据。

我们设置了 bins 参数为 30，这意味着将数据范围分成 30 个等宽的区间，然后统计每个区间内数据的频数。

我们设置了 alpha 参数为 0.5，这意味着每个直方图的颜色透明度为 50%。

我们使用 label 参数设置了每个直方图的标签，以便在图例中显示。

然后使用 legend() 函数显示图例。最后，我们使用 title()、xlabel() 和 ylabel() 函数设置了图表的标题和坐标轴标签。

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2023/04/runoob-test-hist-2.png)

从上图中我们可以清晰地看出这三组数据的分布情况，其中 data1 和 data2 分布接近正态分布，而 data3 分布偏态。

这种比较直方图的方式可以帮助我们分析和比较不同数据组的分布情况。

##### 结合 Pandas

以下实例我们结合 Pandas 来绘制直方图：

```py
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
 
# 使用 NumPy 生成随机数
random_data = np.random.normal(170, 10, 250)
 
# 将数据转换为 Pandas DataFrame
dataframe = pd.DataFrame(random_data)
 
# 使用 Pandas hist() 方法绘制直方图
dataframe.hist()

# 设置图表属性
plt.title('RUNOOB hist() Test')
plt.xlabel('X-Value')
plt.ylabel('Y-Value')

# 显示图表
plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2023/04/hist-pandas.png)

除了数据框之外，您还可以使用 Pandas 中的 Series 对象绘制直方图。只需将数据框中的列替换为 Series 对象即可。

```py
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

# 生成随机数据
data = pd.Series(np.random.normal(size=100))

# 绘制直方图
# bins 参数指定了直方图中的柱子数量
plt.hist(data, bins=10)

# 设置图形标题和坐标轴标签
plt.title('RUNOOB hist() Tes')
plt.xlabel('X-Values')
plt.ylabel('Y-Values')

# 显示图形
plt.show()
```

![img](https://www.runoob.com/wp-content/uploads/2023/04/af3ddff7580ee52a9ee24d7368ab1dbc.png)

# Matplotlib imshow() 方法

imshow() 函数是 Matplotlib 库中的一个函数，用于显示图像。

imshow() 函数常用于绘制二维的灰度图像或彩色图像。

imshow() 函数可用于绘制矩阵、热力图、地图等。

imshow() 方法语法格式如下：

```
imshow(X, cmap=None, norm=None, aspect=None, interpolation=None, alpha=None, vmin=None, vmax=None, origin=None, extent=None, shape=None, filternorm=1, filterrad=4.0, imlim=None, resample=None, url=None, *, data=None, **kwargs)
```

**参数说明：**

- `X`：输入数据。可以是二维数组、三维数组、PIL图像对象、matplotlib路径对象等。
- `cmap`：颜色映射。用于控制图像中不同数值所对应的颜色。可以选择内置的颜色映射，如`gray`、`hot`、`jet`等，也可以自定义颜色映射。
- `norm`：用于控制数值的归一化方式。可以选择`Normalize`、`LogNorm`等归一化方法。
- `aspect`：控制图像纵横比（aspect ratio）。可以设置为`auto`或一个数字。
- `interpolation`：插值方法。用于控制图像的平滑程度和细节程度。可以选择`nearest`、`bilinear`、`bicubic`等插值方法。
- `alpha`：图像透明度。取值范围为0~1。
- `origin`：坐标轴原点的位置。可以设置为`upper`或`lower`。
- `extent`：控制显示的数据范围。可以设置为`[xmin, xmax, ymin, ymax]`。
- `vmin`、`vmax`：控制颜色映射的值域范围。
- `filternorm 和 filterrad`：用于图像滤波的对象。可以设置为`None`、`antigrain`、`freetype`等。
- `imlim`： 用于指定图像显示范围。
- `resample`：用于指定图像重采样方式。
- `url`：用于指定图像链接。

以下是一些 imshow() 函数的使用实例。

##### 显示灰度图像

```py
import matplotlib.pyplot as plt
import numpy as np

# 生成一个二维随机数组
img = np.random.rand(10, 10)

# 绘制灰度图像
plt.imshow(img, cmap='gray')

# 显示图像
plt.show()
```

以上实例中我们生成了一个 10x10 的随机数组，并使用 imshow() 函数将其显示为一张灰度图像。

我们设置了 cmap 参数为 gray，这意味着将使用灰度颜色映射显示图像。

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2023/04/runoob-test-imshow-1.png)

##### 显示彩色图像

```py
import matplotlib.pyplot as plt
import numpy as np

# 生成一个随机的彩色图像
img = np.random.rand(10, 10, 3)

# 绘制彩色图像
plt.imshow(img)

# 显示图像
plt.show()
```

以上实例中我们生成了一个 10x10 的随机彩色图像，并使用 imshow() 函数将其显示出来。

由于彩色图像是三维数组，因此不需要设置 cmap 参数。

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2023/04/runoob-test-imshow-2.png)

##### 显示热力图

```py
import matplotlib.pyplot as plt
import numpy as np

# 生成一个二维随机数组
data = np.random.rand(10, 10)

# 绘制热力图
plt.imshow(data, cmap='hot')

# 显示图像
plt.colorbar()
plt.show()
```

以上实例中我们生成了一个 10x10 的随机数组，并使用 imshow() 函数将其显示为热力图。

我们设置了 cmap 参数为 hot，这意味着将使用热度颜色映射显示图像。

此外，我们还添加了一个颜色条（colorbar），以便查看数据的值与颜色之间的关系。

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2023/04/runoob-test-imshow-3.png)

##### 显示地图

```py
import matplotlib.pyplot as plt
import numpy as np
from PIL import Image

# 加载地图图像, 下载地址：https://static.runoob.com/images/demo/map.jpeg
img = Image.open('map.jpg')

# 转换为数组
data = np.array(img)

# 绘制地图
plt.imshow(data)

# 隐藏坐标轴
plt.axis('off')

# 显示图像
plt.show()
```

以上实例中我们加载了一张地图图像，并将其转换为数组。

然后，我们使用 imshow() 函数将其显示出来，并使用 **axis('off')** 函数隐藏了坐标轴，以便更好地查看地图。

显示结果如下：

![img](https://static.runoob.com/images/demo/map.jpeg)

##### 显示矩阵

```py
import matplotlib.pyplot as plt
import numpy as np

# 生成一个随机矩阵
data = np.random.rand(10, 10)

# 绘制矩阵
plt.imshow(data)

# 显示图像
plt.show()
```

以上实例中我们生成了一个随机矩阵，并使用 imshow() 函数将其显示为一张图像。

由于矩阵也是二维数组，因此可以使用 imshow() 函数将其显示出来。

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2023/04/runoob-test-imshow-5.png)

------

更多实例

以下创建了一个 4x4 的二维 numpy 数组，并对其进行了三种不同的 imshow 图像展示。

- 第一张展示了灰度的色彩映射方式，并且没有进行颜色的混合（blending）。
- 第二张展示了使用viridis颜色映射的图像，同样没有进行颜色的混合。
- 第三张展示了使用viridis颜色映射的图像，并且使用了双立方插值方法进行颜色混合。

```py
import matplotlib.pyplot as plt
import numpy as np

n = 4

# 创建一个 n x n 的二维numpy数组
a = np.reshape(np.linspace(0,1,n**2), (n,n))

plt.figure(figsize=(12,4.5))

# 第一张图展示灰度的色彩映射方式，并且没有进行颜色的混合
plt.subplot(131)
plt.imshow(a, cmap='gray', interpolation='nearest')
plt.xticks(range(n))
plt.yticks(range(n))
# 灰度映射，无混合
plt.title('Gray color map, no blending', y=1.02, fontsize=12)

# 第二张图展示使用viridis颜色映射的图像，同样没有进行颜色的混合
plt.subplot(132)
plt.imshow(a, cmap='viridis', interpolation='nearest')
plt.yticks([])
plt.xticks(range(n))
# Viridis映射，无混合
plt.title('Viridis color map, no blending', y=1.02, fontsize=12)

# 第三张图展示使用viridis颜色映射的图像，并且使用了双立方插值方法进行颜色混合
plt.subplot(133)
plt.imshow(a, cmap='viridis', interpolation='bicubic')
plt.yticks([])
plt.xticks(range(n))
# Viridis 映射，双立方混合
plt.title('Viridis color map, bicubic blending', y=1.02, fontsize=12)

plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2023/04/runoob-test-imshow-6.png)

# Matplotlib imsave() 方法

imsave() 方法是 Matplotlib 库中用于将图像数据保存到磁盘上的函数。

通过 imsave() 方法我们可以轻松将生成的图像保存到我们指定的目录中。

imsave() 方法保存图片支持多种图像格式，例如 PNG、JPEG、BMP 等。

imsave() 方法的语法如下：

```
matplotlib.pyplot.imsave(fname, arr, **kwargs)
```

**参数说明：**

- `fname`：保存图像的文件名，可以是相对路径或绝对路径。
- `arr`：表示图像的NumPy数组。
- `kwargs`：可选参数，用于指定保存的图像格式以及图像质量等参数。

以下是一个使用 imsave() 方法保存图像的简单实例：

```py
import matplotlib.pyplot as plt
import numpy as np

# 创建一个二维的图像数据
img_data = np.random.random((100, 100))

# 显示图像
plt.imshow(img_data)

# 保存图像到磁盘上
plt.imsave('runoob-test.png', img_data)
```

以上实例我们使用 imsave() 方法将这个图像保存到了当前目录下，文件名为 **runoob-test.png**。

由于没有指定图像格式，Matplotlib 库默认将其保存为 PNG 格式的文件。

打开当前目录，会发现一个 **runoob-test.png** 文件，如下所示：

![img](https://www.runoob.com/wp-content/uploads/2023/04/runoob-test.png)

以下实例演示了如何使用 imsave() 方法将一个灰度图像和一幅彩色图像保存到当前目录上：

```py
import matplotlib.pyplot as plt
import numpy as np

# 创建一幅灰度图像
img_gray = np.random.random((100, 100))

# 创建一幅彩色图像
img_color = np.zeros((100, 100, 3))
img_color[:, :, 0] = np.random.random((100, 100))
img_color[:, :, 1] = np.random.random((100, 100))
img_color[:, :, 2] = np.random.random((100, 100))

# 显示灰度图像
plt.imshow(img_gray, cmap='gray')

# 保存灰度图像到磁盘上
plt.imsave('test_gray.png', img_gray, cmap='gray')

# 显示彩色图像
plt.imshow(img_color)

# 保存彩色图像到磁盘上
plt.imsave('test_color.jpg', img_color)
```

以上实例中我们使用了 **numpy.random** 模块分别创建了一幅灰度图像和一幅彩色图像，然后分别使用 imshow() 方法显示这两幅图像。

接着，我们使用 imsave() 函数将这两幅图像分别保存到了当前目录傻姑娘，文件名分别为 **test_gray.png** 和 **test_color.jpg**。

在保存灰度图像时，我们使用了 cmap 参数将其保存为灰度图像格式。

在保存彩色图像时，我们没有指定图像格式，Matplotlib 库默认将其保存为 JPEG 格式的文件。

# Matplotlib imread() 方法

imread() 方法是 Matplotlib 库中的一个函数，用于从图像文件中读取图像数据。

imread() 方法返回一个 numpy.ndarray 对象，其形状是 **(nrows, ncols, nchannels)**，表示读取的图像的行数、列数和通道数：

- 如果图像是灰度图像，则 nchannels 为 1。
- 如果是彩色图像，则 nchannels 为 3 或 4，分别表示红、绿、蓝三个颜色通道和一个 alpha 通道。

imread() 方法的语法如下：

```
matplotlib.pyplot.imread(fname, format=None)
```

**参数说明：**

- `fname`：指定了要读取的图像文件的文件名或文件路径，可以是相对路径或绝对路径。
- `format `：参数指定了图像文件的格式，如果不指定，则默认根据文件后缀名来自动识别格式。

以下实例演示了如何使用 imread 函数从一张图像文件中读取图像数据，并将其显示出来：

```py
import matplotlib.pyplot as plt

# 读取图像文件，下载地址：https://static.runoob.com/images/demo/map.jpeg
img = plt.imread('map.jpeg')

# 显示图像
plt.imshow(img)
plt.show()
```

以上实例中我们首先使用 imread() 方法从名为 map.jpeg 的图像文件中读取了图像数据，并将其存储在 img 变量中。

然后我们使用imshow() 方法显示了这张图像。

注意：我们在显示图像时没有指定颜色映射，这是因为 imread() 方法已经将图像数据按照正确的颜色映射转换成了 RGB 格式，因此我们可以直接使用默认的颜色映射来显示图像。

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2023/04/runoob-imread-1.png)

我们可以通过更改 numpy 数组来修改图像。

例如，如果我们将数组乘以一个数 **0≤≤1**，我们将图像变暗：

```py
import matplotlib.pyplot as plt

# 读取图像文件，下载地址：https://static.runoob.com/images/mix/tiger.jpeg
img_array = plt.imread('tiger.jpeg')
tiger = img_array/255
#print(tiger)

# 显示图像
plt.figure(figsize=(10,6))

for i in range(1,5):
    plt.subplot(2,2,i)
    x = 1 - 0.2*(i-1)
    plt.axis('off') #hide coordinate axes
    plt.title('x={:.1f}'.format(x))
    plt.imshow(tiger*x)

plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2023/04/ccfa3b47cfa040d43b899cad1acbd6bf-1.png)

以下实例用于裁剪图像：

```py
import matplotlib.pyplot as plt

# 读取图像文件，下载地址：https://static.runoob.com/images/mix/tiger.jpeg
img_array = plt.imread('tiger.jpeg')
tiger = img_array/255
#print(tiger)

# 显示图像
plt.figure(figsize=(6,6))
plt.imshow(tiger[:300,100:400,:])
plt.axis('off')
plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2023/04/readimg-crop.png)

如果我们将 RGB 颜色的绿色和蓝色坐标的数组元素设置为 0，我们将得到红色的图像：

```py
import matplotlib.pyplot as plt

# 读取图像文件，下载地址：https://static.runoob.com/images/mix/tiger.jpeg
img_array = plt.imread('tiger.jpeg')
tiger = img_array/255
#print(tiger)

# 显示图像
red_tiger = tiger.copy()

red_tiger[:, :,[1,2]] = 0

plt.figure(figsize=(10,10))
plt.imshow(red_tiger)
plt.axis('off')
plt.show()
```

显示结果如下：

![img](https://www.runoob.com/wp-content/uploads/2023/04/readimg-red.png)
