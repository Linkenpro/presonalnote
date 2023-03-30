# Params（参数）

###### 插件安装

Grasshopper的插件扩展名：

- 绿色图标，扩展名为`.gha`

`.gha`的是`C++、C#、VB`语言编写并编的

- 橙色图标，扩展名为`.ghuser`

`.ghuser`为各种语言编写的未编译插件，有些可以从其中看到编写源代码，或者是一种打包 电池组
 `.ghuser`插件则心须安装在 `C:\USERS\电脑用户\AppData\Roaming\Grasshopper\UserObjects`下

- 无图标，扩展名为`.hpy`

`.ghpy`的是Python语言编写并编译的独有文件格式，看不到源代码。

## Geometry（几何）

### **Point-点**

存储点数据，可以右键点击拾取Rhino场景中的点。

`鼠标右键`>>>Set one Point

如果你的点是通过拾取得到的，那么当你选择点运算器时，视窗中会出现操作轴，你可以直接拖动操作轴来修改点的位置。

自己绘制的点，和拾取Rhino中的点输出的内容是不一致的。

- 自己绘制的点接Panel的时候输出的是点坐标，

- 拾取Rhino中的点输出的是reference point

点的三维坐标

![img](http://www.rhinostudio.cn/files/course/2019/01-03/160457946ce4482103.jpg)

### **Vector-矢量**

矢量（vector）是一种既有大小又有方向的量，又称为向量

不过这个运算器使用很简单，如果你想指定矢量的话，右键-set one/mutiple vectors，就可以在rhino中指定一个点，指定一个点就行，GH默认用原点和你指定的点组成一个矢量。

![img](http://www.rhinostudio.cn/files/course/2019/01-03/1554295a3ba0539834.jpg)

但是这样不太好用，因为有可能模型并不在原点，这么指定矢量就会很麻烦，那怎么办？不用担心，你想到的，GH开发者也会想到，只不过很多人不晓得。

比如你可以直接把Line接给Vector，因为直线本身就是两点连线构成的，正好符合矢量构成要求，矢量就可以直接根据Line的起点和终点构建。如下图。

![img](http://www.rhinostudio.cn/files/course/2019/01-03/161038ef3246542487.jpg)

除了Line，我们也可以直接把point接给Vector，也可以直接构建矢量，原理相信不用说你也晓得了：

![img](http://www.rhinostudio.cn/files/course/2019/01-03/1933586b3b05585465.jpg)

除此之外，关于vector还有个小技巧就是，可以直接把平面接给vector，直接获得其法线方向，注意只能是平面，空间曲面不行：

![img](http://www.rhinostudio.cn/files/course/2020/04-09/005417943160528206.png) 其实不用面，只要是平面线就可以，上面只是帮你省略了一步：

![img](http://www.rhinostudio.cn/files/course/2020/04-09/005404c271bc921354.png)

### **Circle 圆**

只接受绘制圆，不接受拾取Rhino当中现有的圆

![img](http://www.rhinostudio.cn/files/course/2018/12-27/204813dd2d19087817.jpg)

可以把曲线接给circle，看是否爆红来快速判断曲线是否是标准圆

![img](http://www.rhinostudio.cn/files/course/2019/01-03/170755b585cc450486.jpg)

### **Circular Arc圆弧**

![img](http://www.rhinostudio.cn/files/course/2018/12-27/204850218443363036.jpg)

和圆一样，只能自己画，不接受拾取Rhino中现存的圆弧。

### **Curve 曲线**

![img](http://www.rhinostudio.cn/files/course/2018/12-27/204931ba5372555305.jpg)

只能拾取Rhino中存在的曲线或接其他运算器的输出端，不能自己绘制。

直线，圆弧，圆都是曲线的子集，所以都可以拾取，不过反过来就不一定了。

另外curve有个小技巧，就是直接接曲面的话，可以直接获取曲面边缘线，咱经常用它来快速提取边缘线：
![img](https://img.kancloud.cn/02/d3/02d3934f015dc0e53ecf7977f6dd5036_1723x720.png)

### **Line-直线**

![img](http://www.rhinostudio.cn/files/course/2018/12-27/204951fac06d933917.jpg)

不支持拾取Rhino中现有的直线，只能接其他输入端或者自己绘制。可直接接Vector从而被识别为矢量。
![img](https://img.kancloud.cn/dc/a1/dca1cd69e8635f30521ef72cc5a71dc1_316x182.png)

### **Plane-工作平面**

工作平面是所有三维建模软件中最基础的内容，工作平面并不是个物件，它是一个无限平面。

Rhino中，所有物件的绘制都是基于工作平面的，Rhino有相当多而全的命令来操作工作平面。

![img](http://www.rhinostudio.cn/files/course/2019/01-03/1721448ca998246385.jpg)

由于Plane不是个具体物件，所以不能拾取，只能自己点击三点来确认工作平面（三点必定共面）

![img](http://www.rhinostudio.cn/files/course/2019/01-03/173005da8062879156.gif)

直接把一个点接给plane，那么就会默认生成一个以这个点为原点的工作平面，所以很多时候我们会直接把点接给运算器的plane端，因为我们知道我们要的就是xy平面。

![img](http://www.rhinostudio.cn/files/course/2019/01-03/172604c87735677719.jpg)

![img](http://www.rhinostudio.cn/files/course/2019/01-03/172741d4e0e3182733.jpg)

工作平面直接决定物件所处的位置。![img](http://www.rhinostudio.cn/files/course/2019/01-03/172459bf04b4849589.jpg)

### **Rectangle-矩形**

![img](http://www.rhinostudio.cn/files/course/2018/12-27/2050400f2c60762179.jpg)

只能自己绘制矩形，不能拾取Rhino中现有的矩形，矩形位置以当前激活视窗的工作平面为准。

### **Box-盒子**

![img](http://www.rhinostudio.cn/files/course/2018/12-27/2050593e256f002517.jpg)

只能绘制盒子，不能拾取rhino中现存的Box，注意标准立方体Box是只有八个顶点的，不是随便拿六个面组合过来就行的。

### **Brep-多重曲面**

![img](http://www.rhinostudio.cn/files/course/2018/12-27/2051186e6a9d436176.jpg)

rhino中所有的面，多重曲面，都是Brep，所以它既可以拾取曲面，也可以拾取多重曲面。

### **Mesh-网格**

![img](https://www.rhinostudio.cn/files/course/2018/12-27/2051379e89ea022176.jpg)

拾取网格

### **Mesh Face-网格面序**

![img](http://www.rhinostudio.cn/files/course/2018/12-27/205155b9a5f4646692.jpg)

网格面构建规律，简单说就是连接指定点成网格的顺序，有固定的格式，如下图Q{0;1;2;3}，意思就是值按照序号0 1 2 3的顺序连接点成网格，因为网格只有三角形和四边形两种（Ngon暂不讨论），所以一般也就三四个数值

![img](http://www.rhinostudio.cn/files/course/2019/01-03/181251329aa7087566.jpg)

![img](http://www.rhinostudio.cn/files/course/2019/01-03/181440076e4d977404.jpg)

### **PlanktonMesh-抽离网格线框**

专门用来抽离网格线框的，尤其是`Ngon`网格。

一般的网格建模都是基于三角形或者四边形的，最小单元都是三角形或者四边形，`Ngon`可以实现多边形的网格。

![img](http://www.rhinostudio.cn/files/course/2019/01-03/1824033dd7a9942748.jpg)

在GH中这个运算器效果如下图，点击bake的话，只能得到线框

![img](http://www.rhinostudio.cn/files/course/2019/01-03/191922ae4125789656.jpg)

### Surface-曲面

![img](https://www.rhinostudio.cn/files/course/2018/12-27/205229d4ca81372357.jpg)

拾取Rhino当中的曲面。

- 曲面属于brep，但brep不一定是曲面，这个运算器不能拾取多重曲面，只能拾取单一曲面。
- 如果你直接把曲线输入给surface，如果曲线是平面曲线，它会自动帮你封面，如果是空间曲线，则会直接报错。

![img](http://www.rhinostudio.cn/files/course/2019/01-03/1923517d4b78721939.jpg)

### **Twisted Box-扭曲立方体**

![img](http://www.rhinostudio.cn/files/course/2018/12-27/205247f1100e930904.jpg)

是相较于Box的物件，八个顶点扭曲不规则排列，可以根据box到TwistedBox的变化对物体进行变形

![img](http://www.rhinostudio.cn/files/course/2019/01-03/1925459ca498243094.jpg)

![img](http://www.rhinostudio.cn/files/course/2019/01-03/192756c2dcdd083576.jpg)

### **Field-磁场**

我们可以利用磁场做特定的图案详细的大家可以看咱们犀流堂的课程

[磁力图案小教程](http://www.rhinostudio.cn/my/course/1224)

![img](http://www.rhinostudio.cn/files/course/2019/01-03/192949d03a90748608.jpg)

### **Geometry-几何物件**

![img](http://www.rhinostudio.cn/files/course/2018/12-27/2053288a0eec790867.jpg)

可以拾取几乎一切物件，曲面，点，线·······有人可能会想全都用这个挺好，但是这是极不推荐的，因为会让你的电池图数据一片混乱，导致没法有效辨认数据。

### **Geometry Cache-几何缓存**

![img](http://www.rhinostudio.cn/files/course/2019/07-14/2136171a6e0c035186.gif)

几何缓存简单说，你可以把gh当中的物体先bake到rhino当中，利用rhino手工对物体进行一定操作之后再重新拾取回GH当中继续深化处理。毕竟有的时候rhino当中操作要比gh直接操作方便很多。

当然，你rhino手工做的操作不能是炸开，修剪分割之类的破坏物体的操作，这样是没办法拾取回GH的。

![img](http://www.rhinostudio.cn/files/course/2019/07-14/21365352befd926413.png)

### **Geometry Pipeline 链接图层物件**

这个运算器很好用，是用来自动拾取rhino对应图层中的物体的。

如下图，你可以看到，当我在layer输入对应图层名称后，双击激活曲线和brep图标，运算器自动拾取了图层中对应类型的物体，好处就是不用来回拾取了，rhino中物件改变，gh中就即时发生改变。

不过可拾取类型只有点，线，brep，网格，文字啊，注解之类的拾取不了，想拾取还得依靠插件。

![img](http://www.rhinostudio.cn/files/course/2019/01-03/1938328a4cbf242722.jpg)

而如果你要拾取子图层，那也很简单，只要加个双冒号就行，注意用英文输入法输入"::"

![img](http://www.rhinostudio.cn/files/course/2019/12-08/10374376a97b231415.png)

### **Group-群组**

![img](http://www.rhinostudio.cn/files/course/2018/12-27/212041979823940021.jpg)

这里的Gruop不能拾取，也不能绘制任何物件，它仅仅是用来成组的。不过一般也不用他，直接就用Group的运算器

![img](http://www.rhinostudio.cn/files/course/2019/01-03/194409940554572812.gif)

### **Transform 变形**

大部分Transform标签下的运算器输出端都有一个端口（transform），专门用来记录旋转缩放变形等一系列变形数据。

<img src="http://www.rhinostudio.cn/files/course/2019/01-03/194723bc6eae430746.jpg" alt="img" style="zoom:33%;" />

![img](http://www.rhinostudio.cn/files/course/2019/01-03/194732402955912460.jpg)

比如，你想把一个物件移动并缩放并旋转，正常呢你需要这样才能得到最终的结果，如果有别的物件也想这么来一下，就得再连一次

![img](http://www.rhinostudio.cn/files/course/2019/01-03/195332c3b947188844.jpg)

利用Transform，你可以如下图这样，所有的变形数据整合在一起，想给谁就给谁。

![img](http://www.rhinostudio.cn/files/course/2019/01-03/195223747995221323.jpg)

话是这么说，然而我用的还是不是很多。一般都是GH动画里要做一些动态特效的时候才会用
![img](http://www.rhinostudio.cn/files/course/2019/11-13/223334e4accd797922.png)

![img](http://www.rhinostudio.cn/files/course/2019/11-13/2239059352f5689286.gif)

### **SubD-细分**

rhino7.0新增运算器

- 可以直接拾取Rhino中的subd细分物件
- 可以直接将SubD连接给Brep或者Mesh来转换成Nurbs物件或SubD的原始mesh
  ![img](https://img.kancloud.cn/a8/6e/a86e74d1ee8dbd6d028c20a7a9b01e0e_879x445.png)
  ![img](https://img.kancloud.cn/da/d0/dad072768683ea2974d0d6c9f6a4bd65_888x458.png)

## Primitive（原始数据）

- 数据、参数

- 区间

- 布尔

- 文字

### Boolean-布尔

![img](https://www.rhinostudio.cn/files/course/2019/01-04/101538a1e846931908.jpg)

布尔值只有两个值，True和False，对应1和0，是计算机最原始的语言，经常被我们用来判断。

- GH中所有非0的数，都会被判定为True。

![img](http://www.rhinostudio.cn/files/course/2019/01-04/1017575c5b49148185.jpg)

### **Integer-整数**

*整数*（integer）就是像-3,-2,-1,0,1,2,3,10等这样的数。需要注意的是它自带四舍五入功能，

![img](http://www.rhinostudio.cn/files/course/2019/01-04/102147bf1196550945.jpg)

### **Number-双精度浮点数**

![img](https://www.rhinostudio.cn/files/course/2019/01-04/1022499b9952740896.jpg)

是计算机使用的一种数据类型，使用 64 位（8字节） 来存储一个浮点数。 它可以表示十进制的15或16位有效数字，其可以表示的数字的绝对值范围大约是：2.23x10-308 ~ 1.79x10308

对于我们····就是小数啦。

### **Text-文字**

![img](http://www.rhinostudio.cn/files/course/2019/01-04/102706ae4f7b596133.jpg)

可以输入文字，如果包含数值的文字可以直接被其他运算器识别。

![img](http://www.rhinostudio.cn/files/course/2019/01-04/102847f10257391855.jpg)

### **Colour-颜色**

![img](http://www.rhinostudio.cn/files/course/2019/01-04/103004cc6c9c095363.jpg)

可以在右键设置rgb值。

![img](http://www.rhinostudio.cn/files/course/2019/01-04/10400118fa55888796.jpg)

### **Complex parameter-复数**

![img](http://www.rhinostudio.cn/files/course/2019/01-04/104758eab281184887.jpg)

我们把形如z=a+bi（a,b均为实数）的数称为复数，其中a称为实部，b称为虚部，i称为虚数单位。emmmm，完全看不懂，日常我也完全没用到的量，但是作用非常大。

### **Culture-文化国家**

![img](http://www.rhinostudio.cn/files/course/2019/01-04/173650206095698383.jpg)

这个运算器储存了全世界所有国家的名称，可以右键通过不同方式来选择。比如国家，语言，区域来选择不同的国家。

![img](http://www.rhinostudio.cn/files/course/2019/01-04/173747bca4ed482901.jpg)

### **Domain-区间**

![img](http://www.rhinostudio.cn/files/course/2019/01-04/1740342daec9730762.jpg)

区间是数集的一种表示形式，简单说就是范围，格式为A to B，比如0 to 1，在每个区间内都有无数个数。区间对于我们是非常重要的，毕竟我们需要经常指定范围，比如建筑高度在10-100之间，缩放值在0.5-1.5之间等等。

### **Domian²-二维区间**

![img](https://www.rhinostudio.cn/files/course/2019/01-04/17451284031b462813.jpg)

想象一下，一根直线，起点是0终点是1，在0 to 1的范围内有无数个点，所以这个直线上的点我们可以通过一维区间来表示。

那，一个面呢？那就需要二维了，所以这里的区间有两个，你可以参照xy坐标来理解，而且uv是nurbs理论的基础，所有的nurbs曲面都是一个空间二维坐标系，用uv表示两个轴。

### **Guid-全局唯一标识符**

![img](http://www.rhinostudio.cn/files/course/2019/01-04/175544035556514467.jpg)

每一个物件，虽然你没给起过名字，但是都有一个唯一的身份证，这就是全局唯一标识符，用来标记这个物件的唯一身份标识，这就好像古日本大家都叫太郎二郎政府就没法玩了，唯一性很重要。你可以右键运算器来选择任意物件获得其唯一标识符，形式是一串看起来乱七八糟的代码。

![img](http://www.rhinostudio.cn/files/course/2019/01-04/175737106349254657.jpg)

当然你也可以在rhino中点击详细数据来查看

![img](http://www.rhinostudio.cn/files/course/2019/01-04/1759280cad05447252.jpg)

在GH中，我们经常可以看到插件利用GUID来拾取物件从而在gh拾取其本身不能拾取的一些物件，比如vermseh，比如block，比如text等，比如下面这个

[Skatter for Rhino（伪）](http://www.rhinostudio.cn/course/1340)

![img](http://www.rhinostudio.cn/files/course/2019/01-04/18010519ed6d961815.jpg)

### **Matrix-矩阵**

![img](http://www.rhinostudio.cn/files/course/2019/01-04/180253db5be7893704.jpg)

在数学中，矩阵（Matrix）是一个按照长方阵列排列的复数或实数集合 ，最早来自于方程组的系数及常数所构成的方阵——由19世纪英国数学家凯利首先提出。
矩阵是高等代数学中的常见工具，也常见于统计分析等应用数学学科中。

在物理学中，矩阵于电路学、力学、光学和量子物理中都有应用；计算机科学中，三维动画制作也需要用到矩阵。 

矩阵的运算是数值分析领域的重要问题。将矩阵分解为简单矩阵的组合可以在理论和实际应用上简化矩阵的运算。对一些应用广泛而形式特殊的矩阵，例如稀疏矩阵和准对角矩阵，有特定的快速运算算法。关于矩阵相关理论的发展和应用，请参考矩阵理论。在天体物理、量子力学等领域，也会出现无穷维的矩阵，是矩阵的一种推广。
emmm和复数一样，看的人云里雾里，我也从没用过，但是不代表人家不重要，如果你转行程序员的话说不定就得补上了。多少转程序员的建筑师都后悔当年高数没有好好学······

### **Time-时间**

![img](http://www.rhinostudio.cn/files/course/2019/01-04/1806179c678e527591.jpg)

储存时间数据，日期，时分秒都行

![img](http://www.rhinostudio.cn/files/course/2019/01-04/180707bd7ded459061.jpg)

如何获取当前时间：

![img](http://www.rhinostudio.cn/files/course/2019/08-15/095909d1b3fd833259.png)

### **Data-数据**

![img](http://www.rhinostudio.cn/files/course/2019/01-04/181330ac3c0f825102.jpg)

参照运算器geometry，data可以储存所有的数据，反而咱们不大用它，会让我们分不清我们数据类型。

### **Data Path-数据路径**

![img](http://www.rhinostudio.cn/files/course/2019/01-04/1815462a84a7683191.jpg)

储存GH的数据结构路径名称，如果你不知道什么是数据结构的话，还是那句话，请先去看一下官方第三版教程，补全一下基础。

数据结构路径的格式为{A；B；C}。需要注意的是，如果你接入满足格式的数值或者文字的话，它会自动帮你补全大括号。

![img](http://www.rhinostudio.cn/files/course/2019/01-04/182028c4fbd5664252.jpg)

### **File Path文件路径**

![img](http://www.rhinostudio.cn/files/course/2019/01-04/1822571485ad848160.jpg)

右键获取文件路径。你可以右键选择一个文件，一个路径，也可以是一个文件夹，需要注意的是，右键可以勾选synchronise，意思是文件一旦发生更新，gh也会实时更新。

![img](http://www.rhinostudio.cn/files/course/2019/01-06/21113795dac1475725.png)

### **Shader着色器**

![img](http://www.rhinostudio.cn/files/course/2019/01-04/1824513ec69d756966.jpg)

就是材质，右键可以直接选取rhino中默认存在的材质。

![img](http://www.rhinostudio.cn/files/course/2019/01-04/1827015f1fae385005.jpg)

![img](http://www.rhinostudio.cn/files/course/2019/01-04/182711f5b6f5461577.jpg)

## Input（输入）

![img](http://www.rhinostudio.cn/files/course/2019/01-06/20252226e325357485.png)

这一组运算器都是用来作为输入端的，可以输出各种各样的数据，时间，颜色，日期等等。

### **Slider-数据拉杆**

![img](http://www.rhinostudio.cn/files/course/2019/01-04/191820ca80bf077930.jpg)

极其重要和常用的运算器，几乎无处不在，最常用的输入数值的运算器。直接双击就可以弹出编辑面板

![img](http://www.rhinostudio.cn/files/course/2019/01-04/200010b0026b675040.jpg)

其中显示样式有三种，根据需要选择即可，一般没人闲着没事儿调这个。

![img](http://www.rhinostudio.cn/files/course/2019/01-04/2001139f0d8e119623.jpg)

除此之外，你也可以直接在slider上右键来修改数值，这个比双击点开更方便点。

![img](http://www.rhinostudio.cn/files/course/2019/01-04/2004226a4fa0336656.jpg)

但是比较麻烦的是，运算器默认区间是0-1，如果想要别的区间就必须手动修改，很烦人，但是按照GH这么人性化的软件不可能让大家做这么低效率的事情，所以设置了一个快捷输入方法：直接双击空白处然后输入就可以，比如输入1.5 你就可以得到一个0.0-10.0的区间，如果你输入11.100就会得到0.000-100.000的区间，范围和小数点尾数根据你输入的数值来定

![img](http://www.rhinostudio.cn/files/course/2019/01-04/2005139e3430651838.jpg)

那，如果我想输入得到一个负值呢？

![img](http://www.rhinostudio.cn/files/course/2019/01-04/20075289623a461355.jpg)

![img](http://www.rhinostudio.cn/files/course/2019/01-04/200810a6a81e651107.jpg)

是不是很方便？但是还不够方便，因为有的时候我想得到特定区间，而不是默认生成的0-10n次方区间，比如我想输入天数，那么就是需要0-365的区间，那怎么办？如下:

![img](http://www.rhinostudio.cn/files/course/2019/01-04/2009117a102a467727.jpg)

![img](http://www.rhinostudio.cn/files/course/2019/01-04/2009360c66c2724172.jpg)

所以咱们GH还是很人性化的，就是比较闷骚，不告诉你。你以为到这里就完了么？还有一个大头：Animate

![img](http://www.rhinostudio.cn/files/course/2019/01-04/201104810dee231151.jpg)

![img](http://www.rhinostudio.cn/files/course/2019/01-04/202147be360e377417.jpg)

需要注意的有两点，首先文件格式可以改后缀名，比如.bmp改成.png，然后是帧数，过高可以裁，过低那就没戏了，所以做之前自己大概估计一下，比如你要做三秒，每秒30帧，那么就是90帧，Frame count设置成90即可。最终输出的成果是帧序列，需要通过软件合成，具体做法请参考：

[如何做帅呆甲方的GH动画](http://www.rhinostudio.cn/course/1205)

![img](http://www.rhinostudio.cn/files/course/2019/01-04/2024397f3b24524508.gif)

最后还有一个：publish to remote panel

![img](http://www.rhinostudio.cn/files/course/2019/01-04/202727f59419590042.jpg)

这个功能官方第三版教程里讲的听清楚的，简单说就是可以把当前slider发到：

![img](http://www.rhinostudio.cn/files/course/2019/01-04/203038eb13e1598362.jpg)

好处当然很明显了，当你需要给别人展示修改参数调整模型时，尤其是汇报时，你就不需要开着gh了，直接在grasshopper面板里随便拖一拖就ok了~相信看过第三版教程的你一定对这个很熟悉~

补充一个，请各位输入数值的时候尽量使用slider，一个是快捷输入也不麻烦，一个是可以pubulish to remote panel，做动画，还有一个是，只有它和gene pool两个运算器支持遗传算法运算器Galapagos，至于这个是啥，我们后面说。

### **panel-便签**

![img](http://www.rhinostudio.cn/files/course/2019/01-04/203943f89081161449.jpg)

其实本质就是文本输入框，经常用来输入数据，数字，文字等。右键点击edit note就可以打开下面的对话框。

![img](http://www.rhinostudio.cn/files/course/2019/01-04/20474847e7e9415523.jpg)

四周的这一堆按钮除了双击出来的面板里可以改之外，也可以右击panel在弹出菜单里改。

![img](http://www.rhinostudio.cn/files/course/2019/01-04/204931b5336e037776.jpg)

上部，左右两边的按钮很简单，大家试一下就知道了，下面这一排三个的按钮就需要说一下了。这三个按钮对应的就是右键当中的这三个。

![img](http://www.rhinostudio.cn/files/course/2019/01-05/08503178e9ad264554.jpg)

第一个，Multiline Data，只有取消这个选项，你才能得到有数据结构的多个数据，不然就是个多行文字，所以在我们要输入多个数据的时候，第一个要干的事情，就是取消勾选Multiline Data。

![img](http://www.rhinostudio.cn/files/course/2019/01-05/08514841cd76648631.jpg)

![img](http://www.rhinostudio.cn/files/course/2019/01-06/002356cbd60a123102.jpg)

第二个，Wrap Items，便签宽度不够时，是否自动换行。

![img](http://www.rhinostudio.cn/files/course/2019/01-06/0007164b759e598657.jpg)

第三个，Special Codes,当panel中存在特定字符时，自动转化成对应格式。

![img](http://www.rhinostudio.cn/files/course/2019/01-06/000914a84c71510711.jpg)

![img](http://www.rhinostudio.cn/files/course/2019/01-06/00114520113b567572.jpg)

然后你还可以把panel中的数据保存成txt用以其他用途，或者单独复制panel中的数据，都可以。其中，Stream Contents是保存panel中的数据，Stream Destination是设置保存目录，这样每次你点击Stream Contents就会自动更新指定目录的文件了。同样的，panel也和slider一样支持publish to remote panel，从而可以直接在标签页里修改来达到不打开gh界面就可以修改数值的目的。

![img](http://www.rhinostudio.cn/files/course/2019/01-06/001621579fb3471689.jpg)

最后呢，还有一个问题，就是这个运算器和slider一样都有点不方便调出，如果直接调取运算器之后再输入值就感觉比较慢，所以开发者依然给了个快捷用法，就是在你要输入的值前加上//或者“，就是这么方便。

![img](http://www.rhinostudio.cn/files/course/2019/01-06/001907bad9d9294752.jpg)

![img](http://www.rhinostudio.cn/files/course/2019/01-06/001932440a73011389.jpg)

另外，当panel放大到一定程度的时候，你就可以看到这些小按钮，可以方便的直接点击来修改。

![img](http://www.rhinostudio.cn/files/course/2019/01-12/12222842d7fe702421.png)

### **Boolean Toggle-布尔开关**

![img](http://www.rhinostudio.cn/files/course/2019/01-06/002614664914696002.jpg)

可以输出布尔值，双击切换，只有两个值，支持右键Publish To Remote Panel

![img](http://www.rhinostudio.cn/files/course/2019/01-06/0027506c2f3f851175.jpg)

### **Button-布尔按钮**

![img](http://www.rhinostudio.cn/files/course/2019/01-06/00341244bb54236802.jpg)

和前者双击切换不同的是，它点击才会切换，松开就还原。用于那种只需要瞬时状态改变布尔值的情况，比如，点一下才能bake。你可以设置默认状态和点击状态。

![img](http://www.rhinostudio.cn/files/course/2019/01-06/003700cb70ad568122.jpg)

### **Control Knob-控制旋钮**

![img](http://www.rhinostudio.cn/files/course/2019/01-06/004042a5056b913475.jpg)

类似于保险柜那个旋钮来控制输出值·····emmm很有意思，但是没什么卵用。谁没事这么转圈输，属于逗逼运算器。双击可以进入编辑范围数值，slider简化版，不赘述了。

![img](http://www.rhinostudio.cn/files/course/2019/01-06/0044215932b1413262.jpg)

### **Digit Scroller-数字卷轴**

![img](http://www.rhinostudio.cn/files/course/2019/01-06/0054124ae109981985.jpg)

这个输入用的运算器是真心好用，直接拖动小数点改变位数，上下拖动改变大小，没那么多设置。

除了不能pubulish tu remote panel

不能做动画

不支持遗传算法运算器Galapagos······

emmmm所以，还是别用了，老老实实用slider吧。

### **MD slider-多维滑块**

![img](http://www.rhinostudio.cn/files/course/2019/01-06/014219b4f61b197408.jpg)

默认是一个 0 to 1 0 to 1的二维区间，如所示可以直接输出z为0的三维坐标值，其实就是二维坐标。双击进去就可以修改区间范围，但是并没有办法激活三维选项，所以这就是给你看着玩的。偶尔用来作为uv坐标在指定面上取点。

![img](http://www.rhinostudio.cn/files/course/2019/01-06/01445465a368177717.jpg)

### **Value List-数据列表**

![img](http://www.rhinostudio.cn/files/course/2019/01-06/171359719c21027689.jpg)

自由定制的数据列表，具体数据右键单击选edit编辑。

![img](http://www.rhinostudio.cn/files/course/2019/01-06/171812450f54788170.jpg)

默认的列表数值如下，就是为了告诉你，你可以输入特定的表达式，它会自动帮你计算，通过这个运算器，你可以给出一些默认的常用的选项数值或者文字，方便选择。这里的表达式都是常见的一些函数用法，比如开放sqrt（），转化弧度radins（），以及再熟悉不过的sin（） cos（） tan（）之类，这就另说了。

![img](http://www.rhinostudio.cn/files/course/2019/01-06/171839f50e92805434.jpg)

运算器样式有四类，根据需要选择：Check List；Dropdown List；Value Sequence；Value Cycle

![img](http://www.rhinostudio.cn/files/course/2019/01-06/172912892e8c069934.jpg)

### **Calendar-日历**

可以提供日期。在年或月份上按住鼠标滑动就可以切换日期。

![img](http://www.rhinostudio.cn/files/course/2019/01-06/1730273d324e500296.jpg)

### **Clock-时钟**

![img](http://www.rhinostudio.cn/files/course/2019/01-06/173348cb1287273425.jpg)

可以直接像表盘一样修改时分秒针来获取时间。可以右键来选择是否包含秒针。

![img](http://www.rhinostudio.cn/files/course/2019/01-06/173523beb4ba251533.jpg)

但是呢，Clock和calendar一样，输出的是静态数据，如果我们就想要当前时刻并且实时更新怎么办？巧了，GH开发者早就知道你想干嘛，但是就是不告诉你，等你去发现。

![img](http://www.rhinostudio.cn/files/course/2019/01-06/17400223856b651586.jpg)

![img](https://www.rhinostudio.cn/files/course/2019/01-06/174150e20606242072.gif)

### **Colour Pick-颜色选择器**

提供一个HSV（色调，饱和度，明度）颜色值构成的三维空间，很方便选择想要的颜色，但是这个运算器太占地方了，所以我们还是习惯用别的运算器。

![img](http://www.rhinostudio.cn/files/course/2019/01-06/1742593c5eb7989537.jpg)

### **Colour Swatch-颜色采样器**

![img](http://www.rhinostudio.cn/files/course/2019/01-06/174530a9ffc1570927.jpg)

是的，我刚才说的别的运算器就是它，直接右键就可以选择颜色，不沾地，是最常用的赋予颜色运算器。

### **Colour Wheel-色轮**

![img](http://www.rhinostudio.cn/files/course/2019/01-06/174739bc9913240260.jpg)

GH当中颜值最高的运算器之一，也是很多人会忽视的运算器，其实挺好用的，虽然看起来挺吓人的。先来简单介绍一下这个界面，背景盘是一个色轮，只不过我们ps里比较常见的是方形的，都是一种颜色空间表达方式。

![img](http://www.rhinostudio.cn/files/course/2019/01-06/1811120efa39139949.jpg)

然后表盘上的sat是saturability，饱和度Lum是亮度luminance，用法如下图，其实就是color wheel里圈定一个或者多个颜色范围，然后输入你想要的颜色个数，那么CW就会给你在你指定的范围里随机给与指定数量的数值。

![img](http://www.rhinostudio.cn/files/course/2019/01-06/181258a22d7e294588.jpg)

首先，通过调整sat和lum的范围，可以调整输出颜色的饱和度，明度的范围。

![img](http://www.rhinostudio.cn/files/course/2019/01-06/1818328f27a4337085.gif)

然后，你可以调整颜色范围和数量，然后你可以右键选择需要几个颜色区间1-4，图标做成花瓣状，多讲究。

![img](http://www.rhinostudio.cn/files/course/2019/01-06/18212229e576470645.png)

![img](http://www.rhinostudio.cn/files/course/2019/01-06/182548c3e7a8134840.png)

![img](http://www.rhinostudio.cn/files/course/2019/01-06/182618a53e79286824.png)

![img](http://www.rhinostudio.cn/files/course/2019/01-06/1827484e28b5585075.gif)

所以呢，colour wheel是一个很好的得到随机颜色的运算器，，逼格也够高，不知道的人拿到你的运算年起一定一脸懵逼，所以大家平常需要随机颜色的时候就可以搞起来了。

### **Gradient-渐变**

![img](http://www.rhinostudio.cn/files/course/2019/01-06/1832259ac767344498.png)

刚才咱们不是说color wheel用的很少么，就是因为gradient用的太多了，很重要很常用的一个运算器，专门负责提供渐变色。先看一下下图了解一下用法，这个运算器拢共三个输入端，lower limit下限，upper limit上限，parameter参数，简单说，这就是个颜色采样器，默认0-1的区间，你参数给0就是粉红，给1那就是深红，给0.5那就是取渐变中间色，也就是下图的颜色。所以要想看效果，一个球肯定不够。

![img](http://www.rhinostudio.cn/files/course/2019/01-06/1834295a4e15188057.png)

所以我们来尝试增加数量看看，这样你就可以看出渐变在哪里了。

![img](http://www.rhinostudio.cn/files/course/2019/01-06/1838466cc5b0292866.png)

然后我们再来修改颜色渐变看看，gradient有很多自带的渐变色，可以直接选用。

![img](http://www.rhinostudio.cn/files/course/2019/01-06/183956c1c204102641.png)

你也可以很方便的添加自己想要的颜色，组建自己想要的区间。

![img](http://www.rhinostudio.cn/files/course/2019/01-06/184147b7cbf1674057.gif)

所以你现在应该已经知道大概的用法了，给定上下限，再给定上下限组成区间内的数值，就可以在其渐变色区间里采色。这是一个非常常用的运算器，很多数据可视化的案例都需要用到它，比如：

[地形建模专题篇](http://www.rhinostudio.cn/course/561)

![img](http://www.rhinostudio.cn/files/course/2019/01-06/184428c4aabf236514.png)

[Mosquito矢量地图信息获取](http://www.rhinostudio.cn/course/842)

![img](http://www.rhinostudio.cn/files/course/2019/01-06/1845200e901d550488.jpg)

### **Graph Mapper-图形映射器**

![img](http://www.rhinostudio.cn/files/course/2019/01-06/184725dada11668996.png)

GH中很重要的一个运算器，用好了会有神级效果，改数据趋势，甚至用来构造曲线，运算器默认的其实就是个定义域和值域都是0 to 1的函数，而且自带函数有很多种，我们熟悉的sin cos 等函数都有。

![img](http://www.rhinostudio.cn/files/course/2019/01-06/185101566a6b581177.png)

通过对曲线的调整，就可以改变输入数值的趋势，你可以这么想，这个运算器就是个y=k（x）的函数，输入端输入定义域进行采样，根据函数输出采样的结果，也就是值。

![img](http://www.rhinostudio.cn/files/course/2019/01-06/195531316d09747861.png)

它自带十一钟函数如下，各位根据实际需要自己选择即可。

![img](http://www.rhinostudio.cn/files/course/2019/01-06/20000223a10f683070.png)

不过有个比较不太方便的地方是，定义域，值域我们不能随便改动，只能双击进去才能改动，所以我们一般不去修改它的值域定义域，而是去修改输入数值的区间。

![img](http://www.rhinostudio.cn/files/course/2019/01-06/200118e9409d917319.jpg)

![img](http://www.rhinostudio.cn/files/course/2019/01-06/200500c7501e963038.png)

通过Remap对区间映射到0-1来配合曲线控制器使用。这样我就不用担心数值范围的变化导致图形映射器失效了，不过还有个问题，这个运算器自带了很多函数，这些函数大部分情况下都可以满足使用需求，但是呢，并不能满足所有的需求，有的时候我需要一些特别自由的曲线时该怎么办？这个运算器就做不到了，不过没关系，秉承我们一贯的宗旨，没有rh&gh不能做的，只有我们不知道的。so，这个时候就需要我们自己去人为搭建一个图形映射器了。如下图做法，人为在rhino中绘制1*1矩形，自己绘制曲线作为函数曲线，然后通过直线相交的方式获得y值。从而得到想要的结果。

![img](http://www.rhinostudio.cn/files/course/2019/01-06/2015539f0d87545279.png)

偷偷告诉你，我们的z神，就是用这个运算器，硬生生把扎哈的阿利耶夫文化艺术中心用GH全参做出来了！

### **Image samper-图像采样器**

![img](http://www.rhinostudio.cn/files/course/2019/01-06/2028077cf5f4792305.png)

无数的立面都是靠着这个运算器，最早好像是BIG起的头，废话不多说，直接看视频吧：

[图片干扰专题](http://www.rhinostudio.cn/course/912)

![img](http://www.rhinostudio.cn/files/course/2019/01-06/20305604037d046497.png)

![img](http://www.rhinostudio.cn/files/course/2019/01-06/2030560d93d1097854.png)

这里强调一下，不要！不要！不要！用这个图像把女朋友的头像激光雕刻出来!非常像遗像！非常low！因为我就这么干过!感谢媳妇不杀之恩！你自己感受一下.....
![img](https://img.kancloud.cn/d6/5d/d65d1e7317521c8c4914524c7e002b84_709x921.png)

这里额外说一点，如果不想每次都设置image samper的像素大小和图片一致的话，直接像下面这么做就行了：

![img](http://www.rhinostudio.cn/files/course/2019/09-20/1152237c5c42057115.png)

### **File-文件路径**

### **Import PDB-导入PDB文件**

### **Atom Data-原子数据**

![img](http://www.rhinostudio.cn/files/course/2019/01-06/210120014fd7859566.png)

这三个我们放在一起讲吧，正好可以凑个例子。File很简单，右键拾取文件路径，可以选一个文件，也可以选一个文件夹。

![img](http://www.rhinostudio.cn/files/course/2019/01-06/2103059c0db5407648.png)

import PDB是用来导入PDB文件的，而所谓的PDB文件全名Protein Data Bank，蛋白质数据银行，文件格式为pdb，网上随便一搜就有了，你可以在这个网站下载pdb文件，然后载入pdb文件。

![img](http://www.rhinostudio.cn/files/course/2019/01-06/2105084f0e9d467106.jpg)

![img](http://www.rhinostudio.cn/files/course/2019/01-06/210702691cfb389482.jpg)

再接到Atom Data，就可以获取这个蛋白质信息了，然后，emmm就是另一个领域的事情了，大家就看看就好，除非，万一，你做个蛋白质博物馆，然后想从这里找灵感·······

![img](http://www.rhinostudio.cn/files/course/2019/01-06/210740c83221190969.jpg)

### **Import 3DM-导入3DM文件**

![img](http://www.rhinostudio.cn/files/course/2019/01-06/2116397cd4c0108696.png)

指定路径，可以导入指定路径的rhino文件，如果指定layer以及name的话还可以导入指定rhino指定图层甚至名称的物体，不过材质会丢失。

### **Import Coordinates-导入坐标**

![img](http://www.rhinostudio.cn/files/course/2019/01-06/213402a1d4ec778815.png)

从指定的txt文件当中导入坐标，需要注意的是对txt文件有一定要求，不能有多余字符，如下图

![img](http://www.rhinostudio.cn/files/course/2019/01-06/213523b4b04d441273.png)

不要有（）大括号，运算器会在“，”位置帮你把xyz坐标分开。xyz index三个输入端决定坐标位置。有的时候文件里的xy坐标是反过来的，这时候就可以对调下。

![img](http://www.rhinostudio.cn/files/course/2019/01-06/2136193ec540210376.png)

### **Import Image-导入图像**

![img](http://www.rhinostudio.cn/files/course/2019/01-06/214026a15450187626.png)

之前有同学在群里说image samper，也就是图像采样器没办法打包，因为没有文件路径输入端，那么这个运算器就可以满足你的要求，它可以导入指定路径的图片，在gh中生成一个着色网格。需要注意的是，默认的xy sample采样值是图像分辨率，所以如果你的图像分辨率很高的话就得小心了，可能会卡飞了，用来做干扰什么的话分辨率没必要那么高，反正最终也不需要很清楚。

### **Import Shp-导入Shp文件**

![img](http://www.rhinostudio.cn/files/course/2019/01-06/224004416921026362.png)

导入GIS的Shp文件，不过我使用的 时候出现了这个错误，说是缺了个什么库，后来百度了下。

![img](http://www.rhinostudio.cn/files/course/2019/01-06/223001974ab6955862.png)

链接：https://share.weiyun.com/5w7dVz0密码：aqa2n3

大家把这个文件下载安装下就可以正常使用了。只要导入shp文件就ok~你看，大北京的矢量图分分钟就出来了是不是很开心不过呢，这个数据量就听天由命了。哪天百度地图也能随便就扒下来就好了。

![img](http://www.rhinostudio.cn/files/course/2019/01-06/2243219835f5235550.png)

![img](http://www.rhinostudio.cn/files/course/2019/01-06/225212cdb0e3908261.png)

现在的问题就是，这个shp文件怎么来呢？大家可以看一下下面的这个帖子，或者使用gis。

[世界地图矢量文件shp格式获取/下载方法](https://blog.csdn.net/dyxcome/article/details/83065426)

我是在这个地址下载的北京shp文件。

https://download.bbbike.org/osm/bbbike/

详细的内容大家可以看这个课程：

[分分钟生成国内城市建筑地图](http://www.rhinostudio.cn/course/1385)

![img](http://www.rhinostudio.cn/files/course/2019/01-12/113405d4bb46103620.png)

### **Object Details-物件详细信息**

![img](http://www.rhinostudio.cn/files/course/2019/01-06/2212579a4084700579.png)

可以获得拾取物件的图层，名称颜色等各种信息。

### **Read File-读取文件**

![img](http://www.rhinostudio.cn/files/course/2019/01-06/221526ec01b0549162.png)

基本上就等于把所有文件后缀改成txt然后打开，所以啥文件都能读，读出乱码呗。

## Util（实用工具、插件）

![img](http://www.rhinostudio.cn/files/course/2019/01-07/090444c64ec2221891.png)

### **Bifocals-双光眼睛**

注意，这是个插件，不是GH原生运算器，不过是个很有用的插件，咱就顺带给讲了，因为很多同学问我运算器上是怎么有名字的小标签的，其实只要你拖出这个运算器就ok了

![img](http://www.rhinostudio.cn/files/course/2019/01-07/090815fc78eb277926.png)

这个插件你可以在food4rhino下载，也可以在咱们的GH常用插件汇总里下载：

[常用Gh插件资源汇总](http://www.rhinostudio.cn/course/706)

![img](http://www.rhinostudio.cn/files/course/2019/01-07/090740c56612834046.png)

### **Cherry Picker-数据选择器**

![img](http://www.rhinostudio.cn/files/course/2019/01-07/09102403291b894234.png)

emmm，摘樱桃?大概是想形象的告诉你，你可以在指定的数据结构里任意选取你想要的果实（樱桃）吧，毕竟樱桃长在数（据）端。

![img](http://www.rhinostudio.cn/files/course/2019/01-07/091555b306b6167733.png)

分别设置好数据结构路径以及序号Index就可以筛选指定的数据了。

### **Jump-跳转**

![img](http://www.rhinostudio.cn/files/course/2019/01-07/09200119d69c158376.png)

视窗跳跃，双击之后能够从一端跳到另一端，尤其适用于运算器连的特别多的时候，从一端刷的跳到另一端，我觉得叫传送门比较合适。你阔以考虑多整几个，可以实现preizi那种到处缩放跳跃的效果。

![img](http://www.rhinostudio.cn/files/course/2019/01-07/1002284d509a415748.gif)

### **Param Viewer-数据结构查看器**

![img](http://www.rhinostudio.cn/files/course/2019/01-07/145749de5b71619313.png)

GH中非常重要的运算器，学会了数据结构，你才算真正入门了GH，而它，就是专门用来查看数据结构的，相关内容在官方第三版教程里有详细讲解，其实这个东西没那么多人想的那么复杂，你想啊，参数化的前提就是数据量比较大，普通人处理不过来，才借助电脑，那么，数据量大就不能一股脑上处理，得处理，得分化，就好像军队，得成建制，有分区，各个军区，方面军，集团军，军，师，旅，团，营，连，排，班····

GH也一样，很多时候数据多了，我们就得分组处理，分组处理就得有分组的规则，在GH中规则就是{A；B；C}的命名方式。如下图的数据结构，就是分了四组，每组数据量不同

数据结构查看器有两种形态，一种是文字，一种是图形，图形形象的表述了数据结构的形态，双击就可以切换，数据结构查看器输出端输出的是数据结构的名称。

![img](http://www.rhinostudio.cn/files/course/2019/01-07/150251bac0e6439257.png)

这个运算器很简单，但是数据结构就有点费脑子了，这个就看大家的练习量了，有一种诅咒叫知识的诅咒，就是你一旦学会了某种知识，就再也不能体会到不会的人的状态和心情了，所以我现在也只能说，大家加油，如果你觉得难，就多练习，然后突然有一天你就会顿悟了。

### **Scribble-标注**

![img](http://www.rhinostudio.cn/files/course/2019/01-08/1429211ce889940331.png)

本身就是个文字标注，双击修改文字内容，用来对你的电池进行标注。

![img](http://www.rhinostudio.cn/files/course/2019/01-08/143314a3dadc970677.png)

### **Data Dam-数据流控制器**

![img](http://www.rhinostudio.cn/files/course/2019/01-08/1434008e6df3609347.png)

Dam有大坝的意思，很形象，因为这个运算器专门用来控制数据通过的。一旦数据发生变化，就会停止数据传输，除非你点击播放键。

![img](http://www.rhinostudio.cn/files/course/2019/01-08/143647fd896e646752.gif)

这就的好处就是防止电池图运算量太大，修改数据导致的文件崩溃。所以如果你的电池太长太多，计算量太大，记得分区域设置几个dam，只有点击播放键才能让数据通过，可以缓解计算压力。

### **Data Recorder-数据记录器**

![img](http://www.rhinostudio.cn/files/course/2019/01-08/1453062be931964252.png)

专门用来记录数据变化。左边的红球点击可以关闭或开启记录，右边的×可以删除现有记录。你可以右键单击在菜单里修改记录数据的数量。

![img](http://www.rhinostudio.cn/files/course/2019/01-08/145432828075407336.png)

![img](http://www.rhinostudio.cn/files/course/2019/01-08/145613db0722201879.gif)

犀流堂里这节课里用到了这个运算器，大家可以看一下：

[ANEMONE详解--文字升高度](http://www.rhinostudio.cn/course/574)

![img](http://www.rhinostudio.cn/files/course/2019/01-08/145731b6e126078052.jpg)

### **Relay-中继运算器**

![img](http://www.rhinostudio.cn/files/course/2019/01-08/145915375550418279.png)

6.0新增加的一个功能，我很喜欢的，解决了一个电池图连线的痛点，让电池图越来越整洁，一般我们并不会直接拖出这个运算器，而是直接在连线上双击，就可以直接添加一个Relay运算器。这样你就可以通过中继，回避那些线遮挡，线相交的情况。

![img](http://www.rhinostudio.cn/files/course/2019/01-08/150239f4aad3564072.gif)

最重要的是，让电池图里的线笔直笔直的，不好意思我强迫症暴露了，举个例子：

![img](http://www.rhinostudio.cn/files/course/2019/01-08/150428c3ee4c936801.png)

不过需要注意的是，由于这个运算器是6.0新增的，如果你用5.0的gh打开，那就会报错，丢失，所以如果你还要和5.0的朋友协同合作的话，那就一边鄙视他不愿接受新事物一边删掉这个运算器吧。

### **Suirify-简化数据结构**

![img](http://www.rhinostudio.cn/files/course/2019/01-08/1509437ada7b440643.png)

这个运算器试simplify运算器的强化版，之所以要出这个运算器是因为有的时候simplify运算器不是很满足要求，尤其是在单组数据的时候，经常不给你简化，这就有可能导致后面数据结构不对应出现错误。

![img](http://www.rhinostudio.cn/files/course/2020/03-15/1242488a12b7963882.png)

多组数据的话，一般没什么区别。

![img](http://www.rhinostudio.cn/files/course/2019/01-08/151348cdff67882289.png)

### Timer-计时器

![img](http://www.rhinostudio.cn/files/course/2019/01-08/1514411b9814015572.png)

![img](https://img.kancloud.cn/fd/2b/fd2b6040cb4814e84302186653815e27_658x266.png)

还记得我们之前讲实时显示时间的时候提到过它么。你可以理解为没指定时间刷新一次。你可以双击Timer来启动或者禁用它。7.0当中变更为Trigger运算器，但使用方法大致一致。

![img](http://www.rhinostudio.cn/files/course/2019/01-08/151524c697e4927394.jpg)

![img](http://www.rhinostudio.cn/files/course/2019/01-08/151524c52e03697977.gif)

![img](https://img.kancloud.cn/77/a2/77a240f5bc7c15bd77adb6860fa5716e_950x506.gif)

你还可以右键设置刷新时间，在旧版的Kangaroo里极其常用。

![img](http://www.rhinostudio.cn/files/course/2019/01-08/15164089022b699212.png)

![img](https://img.kancloud.cn/16/be/16bece8990cbea86b03d678b2b36a931_1017x713.png)

你还可以搭配counter做个计数器，在[如何做帅呆甲方的GH动画](http://www.rhinostudio.cn/course/1205)这节课里，我就利用这个做了个自动播放器，来自动播放动画。所以这个运算器还是很好用的。

![img](http://www.rhinostudio.cn/files/course/2019/01-08/151837de8b52570168.gif)

另外，当你启动了Timer之后，你就可以在右下角状态栏看到一个勾，在这里双击就可以关闭Timer，以防止gh因为开启timer之后计算量太大未响应，无法关闭停止，毕竟每秒甚至没毫秒计算一次，这计算量必须蹭蹭往上涨，稍微数据结构错点就都毁了。所以这里特意设置了一个外部开关，与gh脱开，控制timer的关闭开启。

![img](http://www.rhinostudio.cn/files/course/2019/01-08/15203200de42848141.png)

### **Cluster Input & Cluster Output-打包输入/输出端**

![img](http://www.rhinostudio.cn/files/course/2019/01-08/15231421c86d430206.png)

这两咱放到一起来讲，因为都是一家人。这个涉及到GH当中一个功能，叫打包运算器，简单说，有一些电池的功能比较常用，你不想每次都连这么多，或者每次都打开电池图复制进来，这时候你就可以使用打包运算器。比如我连了个栏杆的电池，以后肯定会经常用，总共四个输入端，一个输出端，那我就可以考虑给打包个cluster。

![img](http://www.rhinostudio.cn/files/course/2019/01-08/153840056d81154473.png)

![img](http://www.rhinostudio.cn/files/course/2019/01-08/15412119de10787105.png)

![img](http://www.rhinostudio.cn/files/course/2019/01-08/154151fe990f967980.png)

![img](http://www.rhinostudio.cn/files/course/2019/01-08/15431427d1ee470417.png)

最好把输入输出端改一下名字，这样方便识别。

![img](http://www.rhinostudio.cn/files/course/2019/01-08/154332480214817469.png)

不过这个方法太麻烦了，还要替换输出输入端，所以gh提供了一种更加简介的方法，直接框选，然后中键打组就行了，简单直观。

![img](http://www.rhinostudio.cn/files/course/2019/01-08/154514a42572074053.gif)

打包的运算器鼠标放上去会显示电池图的缩略图

![img](http://www.rhinostudio.cn/files/course/2019/01-08/1546477799fe366027.png)

你可以随时右键点击Explode Cluster炸开Cluster来还原成初始状态

![img](http://www.rhinostudio.cn/files/course/2019/01-08/1547335727bd866227.png)

你也可以双击进入打包运算器内部进行一些微调，或者继续深化。搞定之后点击左上角的图标，保存退出即可。

![img](http://www.rhinostudio.cn/files/course/2019/01-08/154901d388a0491871.png)

你还可以添加密码，输入信息。

![img](http://www.rhinostudio.cn/files/course/2019/01-08/170236c30f6f592040.jpg)

然后在file-create user objet后，就可以在菜单栏看到自己的运算器了。

![img](http://www.rhinostudio.cn/files/course/2019/01-08/171427313995606694.jpg)

![img](http://www.rhinostudio.cn/files/course/2019/01-08/1715291f11d9812097.png)

### **Data Input & Data Output-数据输入/输出器**

![img](http://www.rhinostudio.cn/files/course/2019/01-08/171937928547666007.png)

这俩也是rhino6.0新增的运算器，可以把GH当中的包含数据结构的数据作为文件形式输出，然后再读取进gh，适合多人之间配合使用，比如你把建筑日照数据给人就行了，人家不需要全部电池，只需要数据，你就可以这么干。具体使用方法为：

![img](http://www.rhinostudio.cn/files/course/2019/01-08/172355b20328277155.gif)

挺适合协同的俩运算器了，优秀。

### **Fitness Landscape-适应度景观**

![img](http://www.rhinostudio.cn/files/course/2019/01-08/173647f757af047330.png)

专门用来分析景观地形的运算器。高度，坡度，都可以分析，自动生成等高线，就是颜色比较难看不好改，所以我们还是习惯自己连，或者用插件。

![img](http://www.rhinostudio.cn/files/course/2019/01-08/173909dac0f9458986.png)

比如：[地形建模专题篇](http://www.rhinostudio.cn/course/561)

![img](http://www.rhinostudio.cn/files/course/2019/01-08/174032068a14787201.png)

右键里可以修改分析类型，挺多的，主要高度坡度用的多，大家看需要选把。

![img](http://www.rhinostudio.cn/files/course/2019/01-08/174103f9d749006260.png)

### **Gene Pool基因池&Galapagos-遗传算法运算器**

![img](http://www.rhinostudio.cn/files/course/2019/01-08/17422403e86b425590.png)

看颜色你就知道这俩是一路货色，所以放到一起说，这么妖艳的运算器不多了，但是也正因为人家强大，所以才要彰显我就是我，是不一样的烟火。这运算器就不是几句话说得清楚的了，大家直接看下面的视频教程吧：

[遗传算法专题篇：Galapagos运算器详解](http://www.rhinostudio.cn/course/1351/tasks)

[遗传算法视线回避布置景观座椅](http://www.rhinostudio.cn/course/709)

### Grasshopper Player-运算器组

![img](https://img.kancloud.cn/a2/81/a28147a95b265c764ae3b845943f7001_446x142.png)

这一组运算器要放到一起来看，这是7.0新增的功能Grasshopper player相关的运算器，不太好单独介绍运算器，所以我们放到一起来说。咱们举个例子你就能很直接的了解这些运算器的作用了，以下，为一个再简单不过的电池组了，做了一个曲线圆管栏杆，对于我们会GH的人来说，这太简单了，但是对于不会GH的人来说，想要使用这个电池就非常困难了，他们设置不知道怎么打开这个gh文件，怎么bake都不知道，要是电池稍微复杂点，那就直接扑街了。那，有没有什么办法能让不懂GH的人，也能很方便快捷的使用我们写好的电池呢？这就是Grasshopper player的作用了。
![img](https://img.kancloud.cn/f2/50/f250899148a220d294ed10e8e5189581_2556x1180.png)
首先，我们要给每个需要修改的变量插入对应的运算器，曲线，就插入get geometry，数字就插入get number，最后要输出bake的pipe运输器后面接个context bake：
![img](https://img.kancloud.cn/f6/e6/f6e61562ed6c5f3628f2adedbc6098c3_2556x1180.png)
你可以在Get Geometry运算器上右键，只选择Curve，也就是只允许拾取曲线物件，以及Delete input after solve，是否在操作结束后删除输入物件：
![img](https://img.kancloud.cn/1d/4f/1d4f38769e22e7c2379544c97bf865fd_512x390.png)
右键Prompt，设置一下提示信息：
![img](https://img.kancloud.cn/88/21/8821fcbf736574e8712e27aaf95d0655_719x297.png)
![img](https://img.kancloud.cn/ae/92/ae92f6332f3dc852707bd98ac6a1486a_645x288.png)
![img](https://img.kancloud.cn/98/ec/98ec474ce730737fba5acdcca622b2c7_976x218.png)
![img](https://img.kancloud.cn/67/51/6751f039e231058dc9f358a15b14d7ad_964x232.png)
![img](https://img.kancloud.cn/5b/da/5bda1749fee3806e16b871155d8b52c6_957x261.png)
然后保存一下GH文件，接下来就可以开始我们的表演了：
![img](https://img.kancloud.cn/98/ef/98efbf2807e5359afc52303cdf537637_1251x702.gif)
如你所见，我们就可以直接通过Grasshopper player命令打开GH文件，然后输入参数来生成目标物件，从而让不会gh的人也可以大大降低使用门槛。所以这些运算器的作用，各位就应该已经很清楚了：
![img](https://img.kancloud.cn/14/78/1478b76eb1df702a283979f4b279ae48_1126x520.png)
左边用于获取数据，右边用于输出数据。

# Maths（数学）

## Domain（区间）

![img](http://www.rhinostudio.cn/files/course/2019/01-10/09085574fab7516999.png)

这一组的运算器都是和区间有关的，而区间是什么?我们在Params里提到过，区间是一个实数集合，每个区间里都有无数个数。

### **Construct Domain-构建区间**

![img](http://www.rhinostudio.cn/files/course/2019/01-10/0911153adbcb212832.png)

用两个值组成一个区间。

![img](http://www.rhinostudio.cn/files/course/2019/01-10/091325572434629615.png)

### **Deconstruct Domain-拆解区间**

![img](http://www.rhinostudio.cn/files/course/2019/01-10/091515369360984896.png)

拆分得到区间的大小值。

### **Bounds-范围**

![img](http://www.rhinostudio.cn/files/course/2019/01-10/091644c03c06481743.png)

获取一组数的区间范围，配合deconstruct domain可以很容易的得到一组数的最大最小值。

![img](http://www.rhinostudio.cn/files/course/2019/01-10/091911f81199897155.png)

### **Consecutive Domains-连续区间**

![img](http://www.rhinostudio.cn/files/course/2019/01-10/092002215dbb235320.png)

可以把一组数列组合成多个区间，Additive端通过布尔值决定数值是否要依次相加。

![img](http://www.rhinostudio.cn/files/course/2019/01-10/092149d1f086321392.png)

### **Divide Domain-等分区间**

![img](http://www.rhinostudio.cn/files/course/2019/01-10/09233462d1e8918189.png)

将一个区间等分成多个小区间。

### **Find Domain-查找区间**

![img](http://www.rhinostudio.cn/files/course/2019/01-10/093037d37fd7088954.png)

查找数值所在的区间并返回区间对应的序号。

输入端Strict，是否执行严格判定，True则数值只能在区间内，不能等于区间极值。如果不存在包含数值的区间，则返回序号-1。这里大家看下图，你会发现number=0.6明明同时在0.4 to 0.6和0.6 to 0.8两个区间内，却只返回了0.4 to 0.6的序号。这是这个运算器只会返回第一个包含指定数值的区间，其他的就呵呵了。

![img](http://www.rhinostudio.cn/files/course/2019/01-10/093157d58cc3222558.png)

看下图你会体会的更深点：

![img](http://www.rhinostudio.cn/files/course/2019/01-10/09381248faf7501292.png)

另外我们可以利用这个运算器来进行数据的规格化，把给定的一系列数据规格化成几种：

![img](http://www.rhinostudio.cn/files/course/2020/02-07/1320419ce6f3020497.png)

### **Includes-区间包含**

![img](http://www.rhinostudio.cn/files/course/2019/01-10/09403868749b537284.png)

判断一个数值，是否在指定区间内，返回布尔值以及数值与区间的差值，也就是如果区间不在，那着这个数值距离和区间极值的差值

点赞

### **Remap Numbers-区间映射**

![img](http://www.rhinostudio.cn/files/course/2019/01-10/09441710a986556445.png)

非常重要的一个运算器，经常被我们用来映射区间，映射听着你可能有点迷糊，虽然不太准确，但是说缩放估计你就能比较好的理解了。

![img](http://www.rhinostudio.cn/files/course/2019/01-11/2324248db596651855.png)

咱们经常在曲线干扰的时候用到remap：

![img](https://www.rhinostudio.cn/files/course/2019/01-11/233405d0bb6a700599.png)

![img](http://www.rhinostudio.cn/files/course/2019/01-11/233404cb5f7f486058.png)

![img](http://www.rhinostudio.cn/files/course/2019/01-11/233404c641ca255937.png)

[曲线干扰菱形表皮](http://www.rhinostudio.cn/course/1113)

![img](http://www.rhinostudio.cn/files/course/2019/01-11/233541d3efc7594695.png)
需要注意的是Mapped和Clipped输出端的区别，当Value数值超出指定的Source端区间的时候，Clipped输出端会将超出的数值统一设置为Target区间的极值而不是对应的获取超出区间外的值，说起来比较拗口，你看下演示就知道啥意思了
![img](https://img.kancloud.cn/0b/1b/0b1b454b829a35fc47886ad7569744d0_1202x794.png)

### **Construct Domian²-构建二维区间**

![img](http://www.rhinostudio.cn/files/course/2019/01-11/234029d98c94389349.png)

上下两个运算器其实干的都是一件事儿，通过输入四个值或两个一维区间，构建一个二维区间

### **Deconstruct Domain²-拆解二维区间**

![img](http://www.rhinostudio.cn/files/course/2019/01-11/23424887149f552701.png)

拆解二维区间成四个极值或者两个区间。

### **Bounds 2D-点集二维区间**

![img](http://www.rhinostudio.cn/files/course/2019/01-11/23500804bdd6305728.png)

用来返回给定一堆点所占x和y范围所组成的区间。简单说就是给这堆点来个bounding box，然后看这个box在空间的区间范围。

### **Divide Domain²-等分二维区间**

![img](http://www.rhinostudio.cn/files/course/2019/01-11/23520770302d370129.png)

这个运算器很很好理解，就是将一个二维区间等分成很多个小的二维区间。我们倒是经常配合isotrim对曲面进行细分，因为你懂的，nurbs曲面本身就是一个空间二维坐标系，而uv就是它的坐标系，类似于xy，那么我们自然可以通过uv定位点，uv区间定位区域了。这些内容大家看了第三版官方教程应该已经都很熟悉了。

![img](http://www.rhinostudio.cn/files/course/2019/01-12/000544858a1f281705.png)

## **Matrix（矩阵）**

![img](http://www.rhinostudio.cn/files/course/2019/01-12/112028c72069562659.png)

根据度娘的解释：

在数学中，矩阵（[Matrix](https://baike.baidu.com/item/Matrix/3543921)）是一个按照长方阵列排列的[复数](https://baike.baidu.com/item/复数/254365)或[实数](https://baike.baidu.com/item/实数/296419)集合 [1] ，最早来自于[方程组](https://baike.baidu.com/item/方程组/5695032)的[系数](https://baike.baidu.com/item/系数/101536)及[常数](https://baike.baidu.com/item/常数/2215683)所构成的[方阵](https://baike.baidu.com/item/方阵/7362108)。这一概念由19世纪英国数学家[凯利](https://baike.baidu.com/item/凯利/34600)首先提出。

矩阵是高等代[数学](https://baike.baidu.com/item/数学/107037)中的常见工具，也常见于统计分析等应用数学学科中。 [2] 在物理学中，矩阵于电路学、[力学](https://baike.baidu.com/item/力学/648839)、光学和[量子物理](https://baike.baidu.com/item/量子物理/7052617)中都有应用；[计算机科学](https://baike.baidu.com/item/计算机科学/9132)中，[三维动画](https://baike.baidu.com/item/三维动画)制作也需要用到矩阵。 矩阵的运算是[数值分析](https://baike.baidu.com/item/数值分析/3781)领域的重要问题。将[矩阵分解](https://baike.baidu.com/item/矩阵分解/4035386)为简单矩阵的组合可以在理论和实际应用上简化矩阵的运算。对一些应用广泛而形式特殊的矩阵，例如[稀疏矩阵](https://baike.baidu.com/item/稀疏矩阵/3249303)和准对角矩阵，有特定的快速运算[算法](https://baike.baidu.com/item/算法/209025)。关于矩阵相关理论的发展和应用，请参考[矩阵理论](https://baike.baidu.com/item/矩阵理论/5694289)。在[天体物理](https://baike.baidu.com/item/天体物理/8083093)、[量子力学](https://baike.baidu.com/item/量子力学/131692)等领域，也会出现[无穷](https://baike.baidu.com/item/无穷/8284883)维的矩阵，是矩阵的一种推广。

数值分析的主要分支致力于开发矩阵计算的有效算法，这是一个几个世纪以来的课题，是一个不断扩大的研究领域。 矩阵分解方法简化了理论和实际的计算。 针对特定矩阵结构（如稀疏矩阵和近角矩阵）定制的算法在有限元方法和其他计算中加快了计算。 无限矩阵发生在行星理论和原子理论中。 无限矩阵的一个简单例子是代表一个函数的[泰勒级数](https://baike.baidu.com/item/泰勒级数/7289427)的导数算子的矩阵 [3]

看不懂？看不懂就对了，我也看不懂，都是高等代数的常见工具了，自然看不懂。另一方面也确实说明咱们建筑的数理教育非常落后，只能老是去扯文脉搞玄学。那么，具体这玩意能干嘛?至少目前为止我水平有限，没有用过，不过我在dEEP的前辈asnoopy专门写了一篇文章来介绍矩阵，各位可以看一下：

[GH中Matrix矩阵最逗b的解释与最黑科技的运用](https://mp.weixin.qq.com/s?__biz=MzI5MjA3Njk1Ng==&mid=2653361863&idx=1&sn=e6a4f102dbf9c6bef5b10e3bf97373f4&chksm=f7d55a34c0a2d32287de16c070d79e404d344dff79dcd351616895da33f4b6c7a85db299e288&token=1263628675&lang=zh_CN#rd)

## Operators（运算符）

![img](http://www.rhinostudio.cn/files/course/2019/01-12/1214168bf983412478.png)

这一组里的运算器都是我们很熟悉的数学运算符，加减乘除

### **Addition-加法**

![img](http://www.rhinostudio.cn/files/course/2019/01-12/12175314c29b437870.png)

需要注意的是，这个运算器放大到一定大小可以手工添加输入端个数。你会在输入端看到输入端的加减号，就是用来增减输入端。

![img](http://www.rhinostudio.cn/files/course/2019/01-12/1219175e030a721764.png)

### **Division-除法**

![img](http://www.rhinostudio.cn/files/course/2019/01-12/1225520591aa680358.png)

### **Multiplication-乘法**

![img](http://www.rhinostudio.cn/files/course/2019/01-12/122709d8f9c6182035.png)

乘法也是可以增加输入端的

![img](http://www.rhinostudio.cn/files/course/2019/01-13/1946135cf290078605.png)

### **Negative-负值**

![img](http://www.rhinostudio.cn/files/course/2019/01-13/192935f39e2d651506.png)

### **Power-次方**

![img](http://www.rhinostudio.cn/files/course/2019/01-13/19310154a425114440.png)

### **Subtraction-减法**

![img](http://www.rhinostudio.cn/files/course/2019/01-13/194724c27fe4311060.png)

### **Absolute-绝对值**

![img](http://www.rhinostudio.cn/files/course/2019/01-13/194827bd6c55361106.png)

### **Factorial-阶乘**

![img](http://www.rhinostudio.cn/files/course/2019/01-13/195207708727818337.png)

阶乘，即n!=1×2×3×...×n

### **Integer Division-整数除法**

![img](http://www.rhinostudio.cn/files/course/2019/01-13/20031200b434337979.png)

### **Modulus-余数**

![img](http://www.rhinostudio.cn/files/course/2019/01-13/200511795d22912658.png)

### **Mass Addition-叠加**

![img](http://www.rhinostudio.cn/files/course/2019/01-13/200950e23514921837.png)

### **Mass Multiplication-叠乘**

![img](http://www.rhinostudio.cn/files/course/2019/01-13/212755b940f8837256.png)

### **Relative Differences-相对差值**

![img](http://www.rhinostudio.cn/files/course/2019/01-13/213523b53f81043281.png)

其实就是计算前后数据之间的差值，一直用后一个数减去前一个数。

### **Equality-相等**

![img](http://www.rhinostudio.cn/files/course/2019/01-13/213731b6f09c045483.png)

判断两个数值是否相等，输出布尔值。

### **Larger Than-大于**

![img](https://www.rhinostudio.cn/files/course/2019/01-13/214052412128985755.png)

判断一个数值是否大于另一个数值，输出布尔值。输出端分别为大于还是大于等于，

### **Similarity-相似**

![img](http://www.rhinostudio.cn/files/course/2019/01-13/214548c884af344534.png)

判断两个数之是否相似，输入端Threshold值为百分比，如上，误差在百分之30内，则判断为相似，输出为True。输出端 Absolute difference输出的是数值之间的差值。

### **Smalller Than-小于**

![img](http://www.rhinostudio.cn/files/course/2019/01-13/2202273daec1357807.png)

判断一个数值是否小于另一个数值，输出小于和小于等于的布尔值。

### Gate And/Not/Or/Xor

![img](http://www.rhinostudio.cn/files/course/2019/11-15/222737999d0f713235.jpg)

这几个我们放到一起说，因为都是一类的，是不是感觉很熟悉？高中有一段时间好像经常出现在考试的第一题，来帮大家复习一下：

首先我们知道True 和False对应数字1和0

与门你可以把它看成乘法只要有0都为0 （1与0为0，0与0为0，1与1为1）

或门你可以把它看成加法只要有1都为1 （1或0为1，0或0为0，1或1为1）

非门你可以把它看成倒数（0的时候为1，1的时候为0 ）。

### Gate Majority+Nand+Nor+Xnor

![img](http://www.rhinostudio.cn/files/course/2019/01-13/22390157b066681164.png)

这四个我们也放到一起来，是前面四个的升级

**多与门：**三个里超过两个为True才输出True，否则都输出False

**与非门：**其实就是与门+个非门

**或非门：**或门+个非门

**逆异或门：**只有两个输入端相同才会输出True

## Polynomials（多项式）

### **Cube-立方 & Cube Root-立方根**

![img](http://www.rhinostudio.cn/files/course/2019/01-14/093231f5fb6b267730.png)

### **Square-平方 & Square-Root 平方根**

![img](http://www.rhinostudio.cn/files/course/2019/01-14/093333d29abb830228.png)

### **One Over X（-1次方）**

![img](http://www.rhinostudio.cn/files/course/2019/01-14/093451b2bddc270166.png)

同时也是倒数。

### **Power-幂**

![img](http://www.rhinostudio.cn/files/course/2019/01-14/0936259e882b028826.png)

10的几次方。

### **Power of 2（2的几次方）**

![img](http://www.rhinostudio.cn/files/course/2019/01-14/1109106f1a1d097164.png)

### **Power of e（e的几次方）**

![img](http://www.rhinostudio.cn/files/course/2019/01-14/115414630c7c690783.png)

e，自然常数，是数学中一个常数,是一个无限不循环小数，且为超越数,其值约为2.71828.同时，e也是一个成熟的细胞的平均分裂周期。

### Log N & Logarithm &Natrue Logarithm

![img](http://www.rhinostudio.cn/files/course/2019/01-14/1158582d5f4e056660.png)

这三个运算器都是求对数的，对数么····高中大家都学过：

在数学中，对数是对求幂的逆运算，正如除法是乘法的倒数，反之亦然。 这意味着一个数字的对数是必须产生另一个固定数字（基数）的指数。 在简单的情况下，乘数中的对数计数因子。更一般来说，乘幂允许将任何正实数提高到任何实际功率，总是产生正的结果，因此可以对于b不等于1的任何两个正实数b和x计算对数。
如果a的x次方等于N（a>0，且a不等于1），那么数x叫做以a为底N的对数（logarithm），记作x=logaN。其中，a叫做对数的底数，N叫做真数。

## Script（脚本插件）

![img](http://www.rhinostudio.cn/files/course/2019/01-17/234725d5c997592413.png)

GH的特点是静态数据，虽然优点是直观，不用写代码，但是缺点就是不能做循环运算等动态数据处理，而且GH默认运算器并不是很全，有的rhino当中很好用的命令，GH中并没有对应的运算器，这时候就可以借助代码编写来实现。更别提你想开发特殊用途的插件时，就必须使用代码了，而这个组内的运算器就提供了你在gh中码代码的可能。

### **Evaluate-表达式**

![img](http://www.rhinostudio.cn/files/course/2019/01-17/2352204e93ed668231.png)

通过输入表达式来对一系列数据进行处理。不过呢，要注意一个情况，如果你遇到输入表达式之后仍然报错的情况，一定要查看下输入端名称是否和你表达式设置的一致，如下:

![img](http://www.rhinostudio.cn/files/course/2019/01-17/235909d95135328687.gif)

![img](http://www.rhinostudio.cn/files/course/2019/01-18/000117dc17f1908551.gif)

除了我们自己随便设置的运算法则之外，我们还可以调用很多内置的函数，比如经常会有同学问的一个问题：如何修改小数点后的尾数？

![img](http://www.rhinostudio.cn/files/course/2019/01-18/00092225518e209703.png)

除此之外，Evaluate还有很多用法， 比如再一个很多人会问的问题，如何得到指定数据的所有序号？需要注意的是，这个函数只认text，直接输入数字是会报错的，必须先接给panel。

![img](http://www.rhinostudio.cn/files/course/2019/01-18/09370847b42e254526.png)

### **Expression-表达式**

![img](http://www.rhinostudio.cn/files/course/2019/01-18/100458a42aca003511.png)

和上一个运算器一样的名称，但是是升级版，双击可以打开编辑界面，然后你就可以看出两个运算器差在哪里了。常见的各种运算符都有，可以非常方便的编辑你想要的表达式，点击右上角的 图标，就可以查看可以调用的各种函数。

![img](http://www.rhinostudio.cn/files/course/2019/01-20/232447fdb23e289060.png)

你还可以写一些简单的判断来输出布尔值。

![img](http://www.rhinostudio.cn/files/course/2019/01-20/23345823db30880770.png)

或者，设定判断条件，比如，当x>5的时候x=0，否则，x不变：

![img](http://www.rhinostudio.cn/files/course/2019/12-12/124556474606970030.png)

还可以使用Format语法，也就是你直接拖出这个运算器时显示的格式，和python中format格式化函数一个作用，可以用输入端的数据替换format｛｝中的指定的位置：

![img](https://www.rhinostudio.cn/files/course/2020/03-28/14521607fd9b411695.png)

![img](http://www.rhinostudio.cn/files/course/2020/03-26/220325d5af11567100.png)

![img](http://www.rhinostudio.cn/files/course/2020/03-26/220419394e28626884.png)

### C# & VB & Python

![img](http://www.rhinostudio.cn/files/course/2019/01-20/233610a1ce08350428.png)

能用到这几个运算器的话，我估计你也没必要看我的运算器教程了。从左到右分别对应C#，VB，Python三种代码语言

## Time（时间）

![img](http://www.rhinostudio.cn/files/course/2019/01-20/234739b0cb8b227166.png)

这一组里的运算器都是和构建时间有关的，不是很重要。

### **Construct Date-构建日期时间**

![img](http://www.rhinostudio.cn/files/course/2019/01-21/235939b93452249956.png)

![img](http://www.rhinostudio.cn/files/course/2019/01-22/000515be7651452301.png)

### **Construct Exotic Date-构建农历**

![img](http://www.rhinostudio.cn/files/course/2019/01-22/212141570729291357.png)

![img](http://www.rhinostudio.cn/files/course/2019/01-23/2021448537a9719404.png)

可以选择各个国家的农历····貌似是这样，没大弄懂，你可以右键选择特定国家的历法，每个国家都不一样。

### **Construct Smooth Time-构建时间段**

![img](http://www.rhinostudio.cn/files/course/2019/01-23/202428c1567c678134.png)

### **Construct Time-构建当前时间**

![img](http://www.rhinostudio.cn/files/course/2019/01-23/2026317cc4d6790793.png)

构建时间，可以设置当前时间。

### **Deconstruct Date-拆解时间**

![img](http://www.rhinostudio.cn/files/course/2019/01-23/2028546a8a19856671.png)

### **Date Range-等分时间区间**

![img](http://www.rhinostudio.cn/files/course/2019/01-23/203542e9a15f440090.png)

等分时间区间，返回对应时间点。

### **Interpolate Date**

Interpolation 输入端对应的应该是DateA-DataB差值的份数，即

如下图所示

DateA-DataB=1:30:30；
Interpolation 为1时，Date 输出值为 02:00:00+1×1:30:30=03:30:30；
Interpolation 为2时，Date 输出值为 02:00:00+2×1:30:30=05:01:00；
Interpolation 为3时，Date 输出值为 02:00:00+3×1:30:30=06:31:30；
以此类推。

![img](http://www.rhinostudio.cn/files/default/2020/06-05/21255533f95e653920.png)

## Trig（三角）

### Cosine & Sinc & Sine & Tangent

![img](http://www.rhinostudio.cn/files/course/2019/01-31/095007ff3656676025.png)

**Cosine：**返回某一角度的余弦值

**Sinc：**sinc函数，又称辛格函数，用sinc(x)表示。

![img](http://www.rhinostudio.cn/files/course/2019/01-31/10291179e52c841390.jpg)

**Sine：**sin（x）函数，即正弦函数

**Tangent：**正切函数

![img](http://www.rhinostudio.cn/files/course/2019/01-31/103019ba2889008221.jpg)

三角函数在咱们建筑当中应用还是挺多的，比如螺旋线本质上就是sin+cos函数

![img](http://www.rhinostudio.cn/files/course/2019/01-31/104428c4bef6820797.png)

再比如big的大蚊香，本质上就是:

![img](http://www.rhinostudio.cn/files/course/2019/01-31/104919f2b98c014313.png)![img](http://www.rhinostudio.cn/files/course/2019/01-31/105013504a65868480.png)

![img](http://www.rhinostudio.cn/files/course/2019/01-31/1050124b1c48602986.jpg)

又或者，用graph mapper里的三角函数来个干扰：

可以参照课程《[曲线干扰菱形表皮](http://www.rhinostudio.cn/course/1113)》来学习下图

![img](http://www.rhinostudio.cn/files/course/2019/01-31/1055015d3fc0378242.png)

总之用法挺多的，大家可以慢慢发掘。

### ArcCosine & ArcSine & ArcTangent & CoSecant & CoTangent &Secant

![img](http://www.rhinostudio.cn/files/course/2019/01-31/1101299dd2e2153525.png)

这几个都是求反函数的，这个我个人用的就不多了，或者说压根没用过。希望用过的同学或者有用过的案例可以分享给我，我给加上。

**ArcCosine：**反余弦函数

![img](http://www.rhinostudio.cn/files/course/2019/01-31/1111495b3d30744437.jpg)

**ArcSine：**反正弦函数

![img](http://www.rhinostudio.cn/files/course/2019/01-31/111243b5b60a580293.jpg)

**ArcTangent：**反正切函数

![img](http://www.rhinostudio.cn/files/course/2019/01-31/111301ddd809592571.jpg)

**CoSecant：**直角三角形某个锐角的斜边与对边的比，叫做该锐角的余割，用 csc（角）表示 。

![img](http://www.rhinostudio.cn/files/course/2019/01-31/111331b17275397482.jpg)

**CoTangent：***Cotangent* 简写 cot 定义 某锐角的相邻直角边和对边的比

![img](http://www.rhinostudio.cn/files/course/2019/01-31/111348cef025621710.jpg)

**Secant：**某直角三角形中，一个锐角的斜边与其邻边的比（即角A斜边比邻边）,叫做该锐角的正割，用 sec（角）表示

![img](http://www.rhinostudio.cn/files/course/2019/01-31/111411358bde137650.jpg)

### **Degrees & Radians-角度弧度转换**

![img](http://www.rhinostudio.cn/files/course/2019/01-31/111644c8c0e7456320.png)

用于在弧度和角度之间转化的运算器。主要是因为GH当中所有涉及旋转的运算器都是弧度制的，不过某一个版本开始，这些运算器增加了一个选项：

![img](http://www.rhinostudio.cn/files/course/2019/01-31/11181025f367067966.png)

### **Right Trigonometry & Triangle Trigonometry**

![img](http://www.rhinostudio.cn/files/course/2019/01-31/150221d8f93f577145.png)

这两个运算器都是用来生成三角形的，不过一个是直角一个是任意三角形，输入端输入足够构建三角形的数量后（比如一条边两个角度），那么剩余的其他数据这俩运算器都会帮你算出来。不过需要注意的是，这两运算器都是默认弧度制的。

### **Centroid-重心**

![img](http://www.rhinostudio.cn/files/course/2019/01-31/151239775932338683.png)

求三角形重心，顺带输出三个角点和对应边中点连线。三角形重心是三角形三条中线的交点。当几何体为匀质物体时,重心与形心重合。

### **Circumcentre-三角形外接圆圆心**

![img](http://www.rhinostudio.cn/files/course/2019/01-31/15213827b66f914092.png)

求三角形的外心。输出端的Bisector 为每边中点和外心连线的延长线。外心是指三角形三条边的垂直平分线也称中垂线的相交点。用这个点做圆心可以画三角形的外接圆。

### **Incentre-三角形内切圆圆心**

![img](http://www.rhinostudio.cn/files/course/2019/01-31/152652c930a4091572.png)

求三角形的内切圆圆心，顺带输出ABC三个教的角中心线。三角形三条内角平分线的交点叫三角形的*内心*。即内切圆的圆心。

### **Orthocentre-垂心**

![img](http://www.rhinostudio.cn/files/course/2019/01-31/15295869bb98941910.png)

求三角形的垂心，三角形的三条高线的交点叫做三角形的垂心。锐角三角形的垂心在三角形内；直角三角形的垂心在直角顶点上；钝角三角形的垂心在三角形外.

## Util（通用工具）

![img](http://www.rhinostudio.cn/files/course/2019/01-30/233610a6a413910626.png)

Util 好像应该翻译成通用工具吧，除了复数运算的一堆运算器之外，还是有很多很有用的运算器的。

### Epsilon & Golden Ratio & Natural logarithm & Pi

![img](http://www.rhinostudio.cn/files/course/2019/01-30/23403200bfd0068987.png)

这四个都是常数，我们就拿到一起来说了：

**Epsilon**：Epsilon是希腊语第五个字母艾普西隆的小写，写作ϵ或ε，常用于数学参数等的命名。

**Golden Ratio**：无人不知无人不晓的黄金比例，又称黄金分割点，一般应用时取值0.618：1，表达式为（√5－1）/2，黄金分割奇妙之处，在于其比例与其倒数是一样的。例如：1.618的倒数是0.618，而1.618:1与1:0.618是一样的。广泛应用于各种设计行业，尤其是构图：

![img](http://www.rhinostudio.cn/files/course/2019/01-31/00000337c401328549.jpg)

不好意思放错了：

![img](http://www.rhinostudio.cn/files/course/2019/01-31/00000335c548532589.jpg)

![img](http://www.rhinostudio.cn/files/course/2019/01-31/00000339b6ec686105.jpg)

**Natural logarithm**：自然对数 e，以无理数e(e=2.71828...)为底的对数称为自然对数(natural logarithm),并记为ln。

**Pi**：无人不知无人不晓的圆周率，圆的周长与直径的比值，是精确计算圆周长、圆面积、球体积等几何形状的关键值。

### **Extremes-极值**

![img](http://www.rhinostudio.cn/files/course/2019/01-31/001242a5a690447952.png)

对比两组或者多组数据，求对应数据的极小值和极大值

### **Maximum & Minimum-最大值&最小值**

![img](http://www.rhinostudio.cn/files/course/2019/01-31/1717575e957c212201.png)

取大值 和 取小值，对比AB两个输入端，然后返回较大或较小值。比较老的教程里经常用来在干扰的时候控制数值区间。比如max就可以理解为A的数值最小不小于B（if AB,A=B）。

### **Round-四舍五入**

![img](http://www.rhinostudio.cn/files/course/2019/01-31/17442489cc46792946.png)

四舍五入，输出端floor是不大于这个数值的最大值，Ceiling是不小于这个数值的最小值，用地板和天花板两个单词来表示还是比较形象的，不过呢，如果你单纯的想做四舍五入的话，直接接给Integr整数即可。

![img](http://www.rhinostudio.cn/files/course/2019/01-31/174652c84f49176435.png)

不过我们比较常见的用法是用来控制小数点后尾数：

![img](http://www.rhinostudio.cn/files/course/2019/01-31/1748557959f7175079.png)

当然，我们在前面讲表达式的时候讲过一个更简单的用法：

![img](http://www.rhinostudio.cn/files/course/2019/01-31/17492667c891770319.png)

### **Average-求均值**

![img](http://www.rhinostudio.cn/files/course/2019/01-31/1751037382ae779751.png)

数值可以加，点也可以，这个方式可以快速求中心点：

![img](http://www.rhinostudio.cn/files/course/2019/01-31/175314a556dc593079.png)

### **Blur Numbers-模糊数列**

![img](http://www.rhinostudio.cn/files/course/2019/01-31/180327f3374c080151.png)

你可以通过这个运算器讲数列之间的趋势抹平

### **Interpolate data-插入数据**

![img](http://www.rhinostudio.cn/files/course/2019/01-31/21224994dff8645772.png)

自动补齐给定数列之间的数据，然后根据Parameter（0-1）输入的数值，输出对应的数据。

![img](http://www.rhinostudio.cn/files/course/2019/01-31/2156259ad860196426.gif)

并且右键可以设置不同的类型

![img](http://www.rhinostudio.cn/files/course/2019/01-31/2200386bedce800043.png)

咱们用几个点作为案例来演示一下几种选项的区别：

![img](http://www.rhinostudio.cn/files/course/2019/01-31/2208320dae29063060.gif)

![img](http://www.rhinostudio.cn/files/course/2019/01-31/220833115810820404.gif)

![img](http://www.rhinostudio.cn/files/course/2019/01-31/2208331403f8275172.gif)

![img](http://www.rhinostudio.cn/files/course/2019/01-31/220833161e32210885.gif)

### **Smooth Numbers-平滑数据**

![img](http://www.rhinostudio.cn/files/course/2019/01-31/221005dcfa6f319562.png)



柔滑数据过度，当你修改数值时，这个运算器会在你指定的时间内将原有数值变化到你指定的数值。

![img](http://www.rhinostudio.cn/files/course/2019/01-31/22111311e1d8976671.png)

![img](http://www.rhinostudio.cn/files/course/2019/01-31/22115282f534230252.gif)

再哪个曲线试一试，你就更能理解这个是干什么的了

![img](http://www.rhinostudio.cn/files/course/2019/01-31/2214262d54a9847703.gif)

再用个摄像机控制的例子来演示下，你会发现我们来回切换数值的时候，摄像机过度的很顺化，没有突变的感觉，有点云台的感觉。

![img](http://www.rhinostudio.cn/files/course/2019/01-31/22283867b220777814.gif)

### **Truncate-截短**

![img](http://www.rhinostudio.cn/files/course/2019/01-31/230300478cc5150569.png)

按照Truncation factor输入端的数值换算成百分比删除首尾数值。

### **Weighted Average-加权平均值**

![img](http://www.rhinostudio.cn/files/course/2019/01-31/2314328dc0c9678407.png)

![img](http://www.rhinostudio.cn/files/course/2020/05-07/120018228ee6422417.png)

加权平均数的算法应该是原数列的数值 乘以 所占比重 ，并不需要除数列的长度  ，但是要求比重的 总和 必须为1，如果不是1 ，就会自动将其映射到0-1区间 ，等同与将其结果 除 比重的总和

### Complex-复数运算

![img](http://www.rhinostudio.cn/files/course/2019/01-31/231613d53c29767313.jpg)

# Sets（组/系列）

## List（列表）

![img](http://www.rhinostudio.cn/files/course/2019/01-31/231820cb2783585529.png)

List列表，GH中非常重要的内容。不熟悉的，还请认真看一下官方教程，再次强调我们的运算器详解是词典性质的东西，不涉及语法。

### **Insert Items-插入数据**

![img](http://www.rhinostudio.cn/files/course/2019/02-05/225644c860f1880778.png)

在指定列表的指定序号位置插入指定的数据。Wrap端为布尔值，决定如果Indices序号打入list列表总数量是否循环取值。

![img](http://www.rhinostudio.cn/files/course/2019/02-05/2258400919d7275386.png)

### **Item Index-数据序号**

![img](http://www.rhinostudio.cn/files/course/2019/02-05/232010a67374519727.png)

范围list列表中特定数据的序号。注意item端输入的一定要是列表中取出的物体，不然就会返回-1:

![img](http://www.rhinostudio.cn/files/course/2019/02-05/232146a1841d611190.png)

这个运算器只能返回特定数据特定序号，即便这个数据在list列表中有多个重复值，它也会不为所动，只返回一个值。

![img](http://www.rhinostudio.cn/files/course/2019/02-05/232706a95b02938301.png)

emmm怎么说呢，老版本里我是觉得他挺智障的，我都能抽出物件了，还要找啥序号，而且为什么我看起来都是一样的数据，却不能识别？后来看到老外的解答觉得比较有道理：

![img](http://www.rhinostudio.cn/files/course/2019/03-19/20002487dc2b886290.png)

BY火神：诠释：不是数字重复返回其中一个，而是比如当你看到两个1的时候，其实他们的内存位置是不同的，你抽取其中一个其实也带上了内存位置，所以返回的是当初的序号，这个电池只能配合打乱，筛选，排序类的电池使用，起到找回原有序号的作用！

（补充：因为上述电池实际不改变内存地址，了解计算机的朋友就知道你删除一个文件他只是在那段磁盘上标记了空间可用，格式化一块硬盘的时候其实他只是在表头写上了已被格式化，同样的这类行为就是在内存位置上标记了序号，只是找回原来的序号而已）

![img](https://img.kancloud.cn/3c/09/3c09833320e6cfa6db5717c4f5e7862e_658x765.jpg)

### **List Item（取出指定列表序号的数据）**

![img](http://www.rhinostudio.cn/files/course/2019/02-05/232829d484c2764509.png)

取出list列表中指定序号的数据，Wrap为布尔值，决定当序号大于list列表总数时，是否循环取值。

![img](http://www.rhinostudio.cn/files/course/2019/02-05/233529152a53357235.png)

而有时候你想取列表list最后一个值的话，可以直接序号输入-1.

![img](http://www.rhinostudio.cn/files/course/2019/02-10/22532889b952657123.png)

### **List Length-返回列表长度**

![img](http://www.rhinostudio.cn/files/course/2019/02-05/233615f33a5a671924.png)

### **Partition List-列表分组**

![img](http://www.rhinostudio.cn/files/course/2019/02-05/233819bc3f79658209.png)

将List列表按照制定数量size分组。

### **Replace Items-替换列表数据**

![img](http://www.rhinostudio.cn/files/course/2019/02-05/2340215121d6679831.png)

替换List列表中指定序号Indices的数据为指定item的运算器。Wrap和之前一个意思。

### **Reverse List-反转列表**

![img](http://www.rhinostudio.cn/files/course/2019/02-05/234312013170526837.png)

翻转列表list。由于比较常用，所以内置在输入端右键里了。

![img](http://www.rhinostudio.cn/files/course/2019/02-05/2344364a51ab218962.png)

### **Shift List-偏移列表**

![img](http://www.rhinostudio.cn/files/course/2019/02-05/23455648d4d4478011.png)

![img](http://www.rhinostudio.cn/files/course/2019/02-05/2347186664b2777941.png)

偏移数列，按照指定shift偏移数量堆数据进行错位偏移。Wrap决定是删除偏移的数据还是移动到开头。

### **Sort List**-排序列表

![img](http://www.rhinostudio.cn/files/course/2019/02-06/111802a97068240474.png)

排序列表。对keys端的数据进行从小到大的排序，并根据排序规则对Values A端的数据进行重新排序。很常用的运算器，比如我想将点按照高度排序，或者根据线长短进行排序等等。

![img](http://www.rhinostudio.cn/files/course/2019/02-06/113156cc20ed217625.png)

![img](http://www.rhinostudio.cn/files/course/2019/02-06/113543fca640291660.png)

另外，Sort list运算器是可以任意增减输入端的，方便你对多组数据进行排序。

![img](http://www.rhinostudio.cn/files/course/2019/02-06/1139495da1e5500028.png)

### **Split list-分割列表**

![img](http://www.rhinostudio.cn/files/course/2019/02-06/113855f1caaf882702.png)

在指定序号Index处将列表一分为二。

### **Sub List**-抽取指定区间序号数据

![img](http://www.rhinostudio.cn/files/course/2019/02-06/115004ccf3f4388595.png)

列表中抽取指定区间序号的数据及其序号。Wrap端同上。但这会导致一个问题，如果两个区间进行取值，区间数值不能一样，不然就就会有重复取值

![img](https://img.kancloud.cn/f2/a9/f2a9ec19ca068e17d62db0bb555a1b8c_1229x694.png)
所以需要对取值用的区间进行一下处理：
![img](https://img.kancloud.cn/4a/f2/4af28bf24fcf5b3d7efe184004617917_1788x943.png)

### **Dispatch-分流/组**

![img](http://www.rhinostudio.cn/files/course/2019/02-06/115325542db0814690.png)

根据pattern端输入的布尔值将数据分成两组，True到A输出端，False到B输出端。

![img](http://www.rhinostudio.cn/files/course/2019/02-06/11551979b574672638.png)

比如，我们想把列表中过小的数据筛选出来，就可以使用dispatch：

![img](http://www.rhinostudio.cn/files/course/2020/02-07/133733d6b0e8048538.png)

### **Null Item-非法值**

![img](http://www.rhinostudio.cn/files/course/2019/02-06/1200011c2684974047.png)

判断list列表中的Null值和Invalid非法值并返回布尔值，可以结课dispatch用来筛选出错误数据。

![img](http://www.rhinostudio.cn/files/course/2019/02-06/120150ea763e862273.png)

### **Pick'n'Choose-规则抽取**

![img](http://www.rhinostudio.cn/files/course/2019/02-06/1208331897cb500378.png)

根据Pattern端输入的规则决定如何依次抽取对应输入端的数据。比如pattern端输入0 1 0，就是先来stream 0的数据再来stream 1，再来stream 0。还剩的数据怎么办都不要了！

![img](http://www.rhinostudio.cn/files/course/2019/02-06/120857943f61864917.png)

### **Replace Nulls-**Null值替换

![img](http://www.rhinostudio.cn/files/course/2019/02-06/12114842c8c1091016.png)

将list列表中所有Null值替换成指定数据，并返回null值的数量。

### **Weave-编织数据**

![img](http://www.rhinostudio.cn/files/course/2019/02-06/121341580d34022615.png)

编织数据，根据Pattern输入端指定的规则编制stream的数据端数据，我们倒是经常和dispatch搭配使用。Weave的输入端可以任意增加，但是dispatch只能分成两列。

![img](http://www.rhinostudio.cn/files/course/2019/02-06/12151868bb1a637278.png)

我们经常会利用dispatch将数据先分离出来，处理好其中一部分数据后，再通过weave编织成原来的数据顺序，如下。其中。需要注意的是，之所以我们可以直接把Boolean值输入给需要输入整数Integer端，是因为布尔值是可以对应数字的。0 和 1嘛。

![img](http://www.rhinostudio.cn/files/course/2019/02-06/122027b7cacb600128.png)

![img](http://www.rhinostudio.cn/files/course/2019/02-06/122130a2a829309344.png)

当然，weave本身要比dispatch负责，dispatch只能通过布尔值进行数据拆分，所以只能分成两组，但是weave是可以对多组数据进行处理的：

![img](https://img.kancloud.cn/b1/ac/b1acb87028fab95087cc3e0e9b2e77ef_1916x823.png)

### **Combine Data-合并数据**

![img](http://www.rhinostudio.cn/files/course/2019/02-06/123749db58df149845.png)

合并几个输入端的数据，目标就为了一个：消除Null值。如上图，你可以看到0输入端列表中null值，都被1输入端对应序号的物体替换了，而且超出的数据会依次排列在下放。

### **Sift Pattern-**替换数据为null

![img](http://www.rhinostudio.cn/files/course/2019/02-06/1451219bc12e892987.png)

有点类似于dispatch，只不过根据sift pattern端输入的值替换数据为null。另外，输出端可以自由增加数量。

![img](http://www.rhinostudio.cn/files/course/2019/02-06/145439f39fa6568193.png)

### **Cross Reference-数据交叉处理**

![img](http://www.rhinostudio.cn/files/course/2019/02-06/21240224b619284818.png)

数据交叉处理。当两组或多组数据之间，列表list数量不等时，如何处理数据之间的运算。而Cross Reference就是最暴力的处理方式，所有列表中的所有数据都互相进行运算。数据量会暴增。通过 graft对数据成组也可以实现相同的效果。

![img](http://www.rhinostudio.cn/files/course/2019/02-06/212101dc8b63940258.png)

另外，右键可以选择不同的交叉运算方法，一般默认的都是**Holistic**，也就是全部交叉运算：

![img](http://www.rhinostudio.cn/files/course/2019/02-06/211926eca39f486279.png)

**Diagonal**（交叉运算但不包括对角线位置的数据运算，如下）

![img](http://www.rhinostudio.cn/files/course/2019/02-06/215452c8e6b3206469.png)

**Coincident**（消除重复数据，因为每个数据都会和其他数据进行运算，意味着肯定会有重复的数据，这种交叉算法就是删除那些重复数据，如下）

![img](http://www.rhinostudio.cn/files/course/2019/02-06/21551318749e435456.png)

**Lower Triangle**

![img](http://www.rhinostudio.cn/files/course/2019/02-06/215538a593ef054396.png)

**Lower Triangle（Strict）**

![img](http://www.rhinostudio.cn/files/course/2019/02-06/215557d86054002321.png)

**Upper Triangle**

![img](http://www.rhinostudio.cn/files/course/2019/02-06/21562042276a548939.png)

**Upper Triangle（Strict）**

![img](http://www.rhinostudio.cn/files/course/2019/02-06/21565242983d209005.png)

最后，Cross Reference运算器也可以任意增减输入端数量。

![img](http://www.rhinostudio.cn/files/course/2019/02-06/2147484ce2cb871903.png)

### **Longest List-长排数据**

![img](http://www.rhinostudio.cn/files/course/2019/02-06/2205051a3107046984.png)

长排法，一一对应数据处理，数量多的列表多处的数据全都和数据少的列表的最后一个数据运算。右键可以选择不同的算法，默认的是repeat last，也就是重复运算最后一个数据，而GH中的所有列表的运算方法都是默认Longest list。

![img](http://www.rhinostudio.cn/files/course/2019/02-06/220900c35175567766.png)

**Repeat First**

![img](http://www.rhinostudio.cn/files/course/2019/02-06/2210339452f5091733.png)

**Interpolate**

![img](http://www.rhinostudio.cn/files/course/2019/02-06/221056021144919871.png)

![img](http://www.rhinostudio.cn/files/course/2019/06-20/094643321c4c184795.png)

**Wrap**

![img](http://www.rhinostudio.cn/files/course/2019/02-06/2211142c439b671320.png)

**Flip**

![img](http://www.rhinostudio.cn/files/course/2019/02-06/221137954c58346151.png)

将多出的数据翻转循环，举个例子大家感受下：

![img](http://www.rhinostudio.cn/files/course/2019/06-20/094253dd5807203738.png)

最后，Longest List运算器也可以任意增减输入端数量。

![img](http://www.rhinostudio.cn/files/course/2019/02-06/2212204c7346084567.png)

### **Shortest List-短排数据**

![img](http://www.rhinostudio.cn/files/course/2019/02-06/221435bdd2ea735096.png)

短排法，数量多的列表list，多处的数据直接删除。这个短排法算法比较少，就三个：

![img](http://www.rhinostudio.cn/files/course/2019/02-06/221555b78db4380432.png)

**Trim Start **

![img](http://www.rhinostudio.cn/files/course/2019/02-06/221624896276410850.png)

**Interpolate **

![img](http://www.rhinostudio.cn/files/course/2019/02-06/22164193f053416305.png)

依然可以增减输入端数量。

![img](http://www.rhinostudio.cn/files/course/2019/02-06/2217051ba2c4162704.png)

## Sequence

### **Cull Index-删除指定序号数据**

![img](http://www.rhinostudio.cn/files/course/2019/02-06/22471421138d787399.png)

删除指定序号位置的数据，Wrap输入布尔值，控制当序号大于list列表总数时是否循环删除。

![img](http://www.rhinostudio.cn/files/course/2019/02-06/2248375622b5481976.png)

如果想删除最后一个数的话有两个快捷的办法：

![img](http://www.rhinostudio.cn/files/course/2019/02-10/2251313734ff722282.png)

### **Cull Nth-删除指定数值倍数个体**

![img](http://www.rhinostudio.cn/files/course/2019/02-10/225909dbff8e003359.png)

删除指定数值（Cull frequency端）倍数个数，注意不是序号的物体，比如输入2那就是删除第2个，第4个，第6个，第8个.....，对应的序号是1 3 5 7，因为从零开始计数嘛。

### **Cull Pattern**

![img](http://www.rhinostudio.cn/files/course/2019/02-10/23082377e1cc946016.png)

根据Cull pattern端输入的布尔值进行删除，Ture就保留，False就删除。是真的删除，所以还不如用dispatch，至少被删除的数据我们可以保留，指不定什么时候就用到了。

### **Random Reduce-随机删减**

![img](http://www.rhinostudio.cn/files/course/2019/02-10/23110379e6b4998928.png)

根据Reduction指定的删除数量（Integer）随机进行删除，删除规则按照Seed端执行。分分钟做一个随机删减的表皮。

![img](http://www.rhinostudio.cn/files/course/2019/02-10/232038692988186311.png)

那么问题来了，这个Seed端，到底是什么意思，如何作用？这就得叨叨两句了。这个运算器叫随机删除，那么这个Seed端肯定就和随机有关了，那怎么个有关系法？
建议看之前先看一下差评君关于随机的讲解视频：
https://www.bilibili.com/video/BV18p4y167BE?t=207
![img](https://img.kancloud.cn/f2/5c/f25c25f14075322dc8ac705557c99616_1108x817.png)
然后，我们先来做个尝试：

![img](http://www.rhinostudio.cn/files/course/2019/02-28/232437540698829156.gif)

如上图，我任意的修改Seed，你可以看到被删除的数列也在不停的改变，但是，当我滑动了一波之后，重新把Seed的数值设置为150时，后面的结果一模一样。什么意思？就是说每个Seed值对应的随机方式都是一样的，也就是说这个运算器并不是真随机，是伪随机，伪随机什么意思？首先Seed只能是整数，如果你给定slider区间只有0-100，那就意味着你最多，只能得到一百个随机结果。

事实上，现实生活中，大部分所谓的随机，都是伪随机，比如我们最常见的一种随机，随机播放，你有遇过哪怕一次，一首歌连续听了两遍么？哪怕你的歌单只有十首歌，也不可能出现一首歌连续听两遍的情况，按理说这个概率绝对不是零。所以，这个随时就是伪随机。那么我们就大概知道了，其实伪随机，就是用确定性的算法计算出的均匀分布的数序列。

真随机和伪随机，最大的区别在于概率，伪随机，举个例子：一个班有50位同学抓阄抽奖，纸条总计50个，其中10个有有奖，40个没奖。可以确定，按理说每个人平均都有20％的中奖可能。一旦第一位同学没有抽到，那么剩下同学平均中奖的可能性就会从20％提高到20.40％，以此类推，如果前10位同学都没有中奖，那么剩下同学中奖概率将提高到平均25％。但是不管谁中谁没中，最后横竖只有20％的人中奖。这就是20％的中奖概率。再比如，大家经常遇到的游戏抽卡包，抽ssr，十抽如果不中，下次必中，之类的，都是伪随机，你以为真的是你运气好中的么？想多了，程序一开始就计算好了，你的一切的一切，都不过是安排好的表演，为了让你掏钱。

所以，其实伪随机，都是有规律的，你只要能掌握规律，你就可以战无不胜。比如：

[赌场老千与老虎机的故事：伪随机数如何打败赌场](https://www.sohu.com/a/165164345_117959)

老师说的没错，学好数理化，走遍天下都不怕！

真随机，指的是几率，比如17％的几率，意味着你这次触发特殊事件是17％的可能性，下次也是，每一次都是。如果你这次失败，下次依然保持在17％的可能性。。同样使用上面抽奖的例子，这次把20％概率换成20％的几率，那么就成了这样了：50个同学，每人会得到一个装着50张纸条的盒子，其中有10张有奖，40张不中奖，每人可以抽10张纸条。那么这时候，大家抽奖就是个抽各的，互不影响。你抽中了不会导致别人中或者不中，这就是几率，意味着事件之间毫无联系，说不定50个人总计可以抽到1000张全部奖品，或者50人全部空手而回。虽然同样是20％的可能性，概率是所有事件相互影响，总体可能性保持在20％，而几率是所有事件相互独立，单次可能性保持在20％，但总体中奖分布则在0到100％之间浮动。

so~之后如果我们在建模的时候遇到明明使用了随机运算器，但是结果却呈现明显规律性的情况，就是这里的Seed作怪了。

### Char Sequence-创建文本字符序列

![img](http://www.rhinostudio.cn/files/course/2019/02-28/235138adb496924898.png)

CharPool为文字字符，运算器会根据你的字符逐个排列并组合。emmm不晓得能用来干嘛。

### **Duplicate Data-复制数据**

![img](http://www.rhinostudio.cn/files/course/2019/03-01/1007495a1642095664.png)

复制数据，Number是复制数量，Order为布尔值，控制是否整体复制还是逐个复制。

### **Fibonacci斐波那契数列**

![img](http://www.rhinostudio.cn/files/course/2019/03-01/101353130f28764680.png)

斐波那契数列（Fibonacci sequence），又称黄金分割数列、因数学家列昂纳多·斐波那契（Leonardoda Fibonacci）以兔子繁殖为例子而引入，故又称为“兔子数列”，指的是这样一个数列：1、1、2、3、5、8、13、21、34、……在数学上，斐波纳契数列以如下被以递推的方法定义：F(1)=1，F(2)=1, F(n)=F(n-1)+F(n-2)（n>=3，n∈N*）在现代物理、准晶体结构、化学等领域，斐波纳契数列都有直接的应用，为此，美国数学会从1963年起出版了以《斐波纳契数列季刊》为名的一份数学杂志，用于专门刊载这方面的研究成果。

有趣的是，这样一个完全是自然数的数列，通项公式却是用无理数来表达的。而且当n趋向于无穷大时，前一项与后一项的比值越来越逼近黄金分割0.618（或者说后一项与前一项的比值小数部分越来越逼近0.618）。 1÷1=1，1÷2=0.5，2÷3=0.666...，3÷5=0.6，5÷8=0.625…………，55÷89=0.617977……………144÷233=0.618025…46368÷75025=0.6180339886…... 越到后面，这些比值越接近黄金比.

那，在我们设计中到底有什么用咧。斐波那契数列中的斐波那契数会经常出现在我们的眼前——比如松果、凤梨、树叶的排列、某些花朵的花瓣数（典型的有向日葵花瓣），蜂巢，蜻蜓翅膀，超越数e（可以推出更多），黄金矩形、黄金分割、等角螺线，十二平均律等。

就说个大家最常见的：

[斐波拉契魔咒再现](https://zhuanlan.zhihu.com/p/40706915)

![img](http://www.rhinostudio.cn/files/course/2019/03-01/102115b86624357065.jpg)

来，留个思考题给大家~

![img](http://www.rhinostudio.cn/files/course/2019/03-01/12300084e90e170069.png)

![img](http://www.rhinostudio.cn/files/course/2019/03-01/1230008e326b910631.png)

### **Range-等分区间得数**

![img](http://www.rhinostudio.cn/files/course/2019/03-01/1520546d67fa191855.png)

等分区间得数。

### Repeat Data-指定复制数据

![img](http://www.rhinostudio.cn/files/course/2019/03-01/1523324730b1523191.png)

根据指定列表长度来逐个复制列表数据。

### **Sequence-指定规则生成数列**

![img](http://www.rhinostudio.cn/files/course/2019/03-01/15280447c755333041.png)

根据指定规则，生成一组指定长度的数列，默认的[N-1]+[N-2]其实就是说下一个数等于前两个数的和，也就是斐波拉契数列，你可以根据需要自己指定规则。

### Series-等差数列

![img](http://www.rhinostudio.cn/files/course/2019/03-01/1533393ca6f0384340.png)

生成一组等差数列，最常用的运算器之一咧。start是起始值，step为步差，count为步数。

### **Stack Data-逐个复制**

![img](http://www.rhinostudio.cn/files/course/2019/03-01/153545107ccb347030.png)

根据Stack端指定的复制数量对data端的数据逐个进行复制。

### **Jitter-震荡**

![img](http://www.rhinostudio.cn/files/course/2019/03-01/15380911e31f033015.png)

讲数列进行打乱，Jitterd端为震荡程度，0为不打乱，1为完全打乱。Seed端为随机种子，和random reduce的是一样的。那么，既然我们说到了random reduce，我们当时做了一个随机删减的表皮，但是可能我要的并不是随机删选呢？我要的是随机分成两组怎么办？random reduce就不能满足我们了，因为这个运算器并不能保留被删除的数据。那这时候我们就可以用jitter来做。

![img](http://www.rhinostudio.cn/files/course/2019/03-01/15461795d9ec979830.png)

如果你有lunchbox插件的话，可以使用random split运算器实现一样的效果，再复杂一丢丢的，你可以看一下这节课：

![img](http://www.rhinostudio.cn/files/course/2019/03-01/1547451a2ef5324780.png)

### Random-随机

![img](http://www.rhinostudio.cn/files/course/2019/03-01/1549426e4ef7319821.png)

随机，在指定区间内生成指定数量的随机数，Seed端和所有的种子一样作用，只要给个整数就行。需要注意的是，这里的随机是可以重复的，也就是说，是可能得到多个相同的数值的。还有你可以右键运算器选择Integers来保证输出的随机值都是整数，或者你在后面接个四舍五入的运算器也是阔以的。

举个例子，我们可以给一堆随机高度来挤出，形成错综复杂的效果。

![img](http://www.rhinostudio.cn/files/course/2019/03-01/155644c6a61b203276.png)

不过呢，实际项目不大可能让你尺寸都这么随机，一般都会进行一定程度的规格化，比如下图，简单操作就可以控制随机挤出的规格种类固定：

![img](http://www.rhinostudio.cn/files/course/2019/03-01/16003977adcb950328.png)
那开头咱们说了，random运算器在区间内获得的随机数是可能重复的，那如果我想百分百获得一串完全不同的随机数该怎么办呢？首先，如果你用random运算器在区间内取随机小数，那一般不会出现这个情况，小数点位数那么多位，一般是不会出现重复取值的情况的，一般都是在你设置了random右键，取整数值的时候：
![img](https://img.kancloud.cn/9b/2f/9b2f94d746874aa75ef22b43c52a4153_840x389.png)
那这时候用random就有点小麻烦了，还不如直接整个列表，然后jitter震荡得了
![img](https://img.kancloud.cn/e8/c6/e8c695eb2bc05d35ec1f6937c9b13718_1432x461.png)

## Sets

### Create Set-合并同类

![img](http://www.rhinostudio.cn/files/course/2019/03-01/161607790c89419181.png)

合并同类项咧，合并所有相同的数据，并返回相同数据的序号。注意List端输入的为数据类型，也就是说除了数字，还可以是矢量，布尔值等。

### Set Difference

![img](http://www.rhinostudio.cn/files/course/2019/03-01/1637128f301e840154.png)

返回AB两组数列中A有而B没有的数据。

### **Set Difference（s）**

![img](http://www.rhinostudio.cn/files/course/2019/03-01/17215318ec8a209405.png)

返回AB两组数据中只在A或只在B列表中存在的数据。

### **Set Intersection-交集**

![img](http://www.rhinostudio.cn/files/course/2019/03-01/172519f5e670981667.png)

返回AB两组数据中都存在的数据。

### **Set Majority**

![img](http://www.rhinostudio.cn/files/course/2019/03-01/172359f77ded144572.png)

返回ABC三组数据中出现超过一次的数据。

### **Set Union-并集**

![img](http://www.rhinostudio.cn/files/course/2019/03-01/1726560bbcf7938542.png)

返回AB两组数据中出现过的所有的数据。

### **Carthesian Product**

![img](http://www.rhinostudio.cn/files/course/2019/03-01/175300c6e9e3451723.png)

讲AB两组数据相同序号的数据放到一组内，要求AB两组数据数量一致。

### **Disjoint**

![img](http://www.rhinostudio.cn/files/course/2019/03-01/175807f40dd0668022.png)

判断AB两组数据是不是没有相同元素。如果没有相同数据，就返回True，有相同数据，就返回False。

### Member Index

![img](http://www.rhinostudio.cn/files/course/2019/03-01/181446696fd3649678.png)

返回Member端数据在Set端数据里的出现的序号，以及数量，经常配合Create set配合用来把所有相同数据分组。话说有小伙伴问，为什么像下图中下面的连法就会查找失败?

![img](http://www.rhinostudio.cn/files/course/2020/01-15/145802aed040014519.png)

原因很简单： 因为下面的连法，set是number，member是text，不是一个数据类型。

### Replace Members

![img](http://www.rhinostudio.cn/files/course/2019/03-01/18172770be10765252.png)

查找Set端数据中指定的数据并替换。需要注意的是，你需要确保用来查找和匹配的数据都是一样类型的，gh中经常出现的错误就是以为panel是数字，其实panel里的数据类型是文字，所以如果你在处理的时候要注意保证输入端的数据类型一样，不然就会出问题：
![img](https://img.kancloud.cn/b7/4d/b74d431a2670cea733b957b67608d811_1151x688.png)
![img](https://img.kancloud.cn/06/78/0678d535005fc08aef28ae8c8ae75005_1125x695.png)
![img](https://img.kancloud.cn/c3/4c/c34c22779674527b2f3a5cf492af7af5_1103x681.png)

### **SubSet-包含子集**

![img](http://www.rhinostudio.cn/files/course/2019/03-01/18184668641a637266.png)

判断两组数据是够包含，也就是判断是否是另一个的子集。

### **Delete Consecutive-删除重复数据**

![img](http://www.rhinostudio.cn/files/course/2019/03-01/1821128e2306265768.png)

删除临近的重复的数据，并返回最大的重复值。

### **Find similar member-查找相近数据**

![img](https://img.kancloud.cn/ac/0a/ac0afc57a1e9c1b9d2315e41687b81ac_1060x705.png)

在Set端中查找于Data端数据最接近的数据并替换，也可以用来做尺寸规格化哟~注意，不能把数据连给panel，不然就会出现如下的错误，猜测可能是因为panel数据类型为text导致的错误，总之注意就是了，感谢“-S-G-”的提醒指正：
![img](https://img.kancloud.cn/dd/6a/dd6a33be6496b5e1724d097606d3b9ad_794x287.png)

### **Key/Value Search-键值对**

![img](http://www.rhinostudio.cn/files/course/2019/03-01/1829542b9400360449.png)

首先Keys端和value端数据一一对应，通过serch端输入对应的key值调取对应的数据。其实每一个list都是这个意思，给每一个数据一个序号，这个序号，就是每个数据（value）的key了。在6.0中，我们已经可以给模型插入key/value的数据了，这以前得靠elephant等插件，从而实现BIM，建筑信息模型的效果。

![img](http://www.rhinostudio.cn/files/course/2019/03-01/1833106eda48453679.png)

## Text

### **Characters-拆解字符**

![img](http://www.rhinostudio.cn/files/course/2019/03-01/22411289a9e4685919.png)

拆解文字为单个的字符，并返回每个字符的Unicode，Unicode(统一码、万国码、单一码)是计算机科学领域里的一项业界标准，包括字符集、编码方案等。Unicode 是为了解决传统的字符编码方案的局限而产生的，它为每种语言中的每个字符设定了统一并且唯一的二进制编码，以满足跨语言、跨平台进行文本转换、处理的要求。1990年开始研发，1994年正式公布。

### **Concatenate-合并字符**

![img](http://www.rhinostudio.cn/files/course/2019/03-01/224359fe6824386330.png)

合并字符，输入端可以增加

![img](http://www.rhinostudio.cn/files/course/2019/03-01/224445e014d5891980.png)

### **Text Join-文本组合**

![img](http://www.rhinostudio.cn/files/course/2019/03-01/224724c3d6cc787715.png)

文字组合，讲多个字符或者文字组合成一个文字。你可以设置组合的分隔符。

![img](http://www.rhinostudio.cn/files/course/2019/03-01/22475179ee3b056564.png)

如果J端输入回车的话，就可以得到多行文字。

![img](https://img.kancloud.cn/93/ab/93abf2e33a75545e57e9d024f0ffb99b_677x376.png)



### **Text Length-文字长度**

![img](http://www.rhinostudio.cn/files/course/2019/03-01/2249586a2e9d972913.png)

返回文字长度。

### **Text Split-字符分割**

![img](http://www.rhinostudio.cn/files/course/2019/03-01/22510042de5d612892.png)

讲文字在指定字符处断开。

### **Format-格式化函数**

![img](http://www.rhinostudio.cn/files/course/2019/03-01/231156cd9bef280949.png)

format格式化函数，可以参考python中的函数用法，用data 0&1 输入端的数据代替掉Format端中｛｝内的内容：

![img](http://www.rhinostudio.cn/files/course/2020/03-28/144944889a78420203.png)

![img](http://www.rhinostudio.cn/files/course/2020/03-28/1447346506fe785535.png)

输入端可以不断增加。就是这个Culture改了半天好像没啥区别。

![img](http://www.rhinostudio.cn/files/course/2020/03-28/145018a83478701245.png)

注意：Format中的｛0｝一定要用英文输入法输入，不然会出错。

by火神：规则符要英文舒服法输入的，比如冒号引号逗号这些，为了全面的展示使用效果，我再给出一个案例![img](https://img.kancloud.cn/54/f8/54f80947c2a78b6fd0163986a2ad9112_1196x584.png)

by白菜：补充当你想在文本中使用{}作为字符时，请使用{{和}}，如图：
![img](https://img.kancloud.cn/e2/c5/e2c59c6eb018d7abd59984f4ed988264_1127x320.png)

### **Text Case**-字符切换

![img](http://www.rhinostudio.cn/files/course/2019/03-02/2140022b711e155601.png)

大小写转换。

### **Text Fragment-抽取指定长度**

![img](http://www.rhinostudio.cn/files/course/2019/03-02/2142433a601b171282.png)

抽取指定文字指定位置开始的指定长度的片段。

### **Text Trim-删除空格**

![img](http://www.rhinostudio.cn/files/course/2019/03-02/214727f29dab105969.png)

虽然名字里带了trim，但是其实是用来删除空格的，控制是否删除文字首尾的空格。

### Match Text-匹配文本

![img](http://www.rhinostudio.cn/files/course/2019/03-02/233055fb2974679677.png)

查看text输入端中是否和Pattern端输入的字符相符，输出布尔值。

### Replace Text—查找替换指定文本

![img](http://www.rhinostudio.cn/files/course/2019/03-04/182013d90ef3053978.png)

### Sort Text—排序文字

![img](http://www.rhinostudio.cn/files/course/2019/03-04/1824033ab894196181.png)

你也可以通过Keys输入端文字的排序来重新排序Values端的数据

![img](http://www.rhinostudio.cn/files/course/2019/03-04/1827164b1fa5935239.png)

### Text Distance-字符距离

![img](http://www.rhinostudio.cn/files/course/2019/03-04/2027506534f9880547.png)

计算两个字符串之间的**Levenshtein Distance，**Levenshtein Distance 算法，又叫 Edit Distance 算法，是指两个字符串之间，由一个转成另一个所需的最少编辑操作次数。许可的编辑操作包括将一个字符替换成另一个字符，插入一个字符，删除一个字符。一般来说，编辑距离越小，两个串的相似度越大。

## Tree(数据结构)

![img](http://www.rhinostudio.cn/files/course/2019/01-31/232046e4f701398871.png)

这一部分，是很重要的一部分，因为这部分的运算器涉及的都是GH中最核心也是最难的一部分，数据结构。之前很多人觉得数据结构很难，我要说的是，说不难是假的，但还没难到吓人的地步。只要你知道原理，多去用，就能很快掌握。数据结构的本质，就是组织，就是分组。这就好像一个学校，要分几个年级，年级里要分几个班级，班级里可能还分几个组。就是为了方便管理，不然难道所有学生一起授课么？再比如中国的军队，这么多人，不可能不去分组，不过名字不一样，叫编制，一个班大约10人，一个排三个班，一个连3个排，加上炊事班等等勤务保障兵，大约有100人，一个营三个连，一个团三个营，一个师三个团，一个军三个师，这样算下来个师有一万多人，一个军4万接近5万人。所以，GH里也一样，因为数据多了，很多时候不能一股脑上，一股脑处理，所以要分组，要区分，才好管理，才好运算，这才有了数据结构。

比如说，矩形阵列运算器Square输出的cells和points都是自带数据结构的，我们用Param Viewer来查看，就可以看到如下图，其中{0；0；0}就是这一支数据的名称，N=5就是指这一支数据里包含的数据个数。你说为什么叫{0；0；0}？这就好像小区为什么叫区，班级为什么叫班级，年级为什么叫年级？没多少为什么，就是这么定的。这就是规则。那我们可以看到{0；0；0}一直到{0；0；4}总共有5组数据（从0开始计数），每一组都有五个数据。这就是cells输出端的数据结构，简单说就是分了五组，每组五个数据。那{0；0；0}-{0；0；4}前面的“0；0”有什么意义么？都是一样的，为啥还有“0；0”？为啥不直接叫{0}-{4}？

![img](http://www.rhinostudio.cn/files/course/2019/03-04/22010953c5ef675747.png)

没错，就当前来说，确实没什么意义，都是重复的。我们完全可以反手就是一个simplify tree给他简化掉。如下图，但是呢，这个“0；0”虽然目前是多余的，不代表是没用的。

![img](http://www.rhinostudio.cn/files/course/2019/03-04/220915b49bcf644304.png)

这就好像你已经到了你朋友家楼下了，你朋友只需要告诉你303房间即可，但是这时候他告诉你我家在2号楼4门303，你说错了么？没错，需要吗？当前不需要，但如果有朋友还在小区外甚至离得很远，就需要了。这里的“0；0”差不多就一个意思，目前不需要，但是并不是没有意义的。尤其是在merge数据的时候，虽然结构都一样，下面的两组都是五组，五个数据，但是merge不到一起去，因为名称不一致，一个，是0大组，0二组，5小组，五个数据，另一个是五大组，五个数，没了，你说，怎么合到一起？

![img](http://www.rhinostudio.cn/files/course/2019/03-04/2211539d8f3c464747.png)

![img](http://www.rhinostudio.cn/files/course/2019/03-04/2212524c2f25435510.png)

所以，你得尽量保证数据结构一直，数据结构的名称也尽量一致。

再比如，我们有一堆线，我想隔一个成一个面，就需要去分组。

![img](http://www.rhinostudio.cn/files/course/2019/03-04/22200222f97d577794.png)

![img](http://www.rhinostudio.cn/files/course/2019/03-04/22200223eaa9156182.png)

那我这个时候就可以两两分到一组，去loft，因为所有的运算器，只会去计算组内的数据。

![img](http://www.rhinostudio.cn/files/course/2019/03-04/22212448d618397731.png)

这些呢，也仅仅是举了些简单的例子，让大家有一定的了解，实际应用的时候可能会比这个复杂的多，但是也没大家想的那么复杂，你看起来复杂，大多数时候仅仅是因为数据量多，看起来复杂，所以我们经常习惯在调试阶段先把数据量调少，等逻辑确立了，再调大数据量。ok~让我们进入正题吧。

### Clean Tree—删除数据中的空集

根据你设定的布尔值来删除数据结构中的空集或Nulls值或非法值

![img](http://www.rhinostudio.cn/files/course/2019/03-04/2232171cff79242031.png)

### Flatten Tree—拍平数据

![img](http://www.rhinostudio.cn/files/course/2019/03-04/2242284ac243641637.png)

拍平数据结构，数据结构处理中最暴力的运算器，图标也很暴力，仿佛在告诉你，flatten出征，寸草不生，砍掉所有的所有的数据结构，放到一个组内，path端可以控制拍平后数据结构名称。打个比方就好像原来五个房间，每个房间人数从0-4都不同，现在你，咔一下，全推平了，所有人放到一个房间内，嗯，差不多就这意思。由于这个运算器太过常用，所以被内置到几乎所有输出输入端的右键菜单里了。

![img](http://www.rhinostudio.cn/files/course/2019/03-04/224327f7a3b4973151.png)

### Graft Tree升组

![img](http://www.rhinostudio.cn/files/course/2019/03-04/22443975c3f8876567.png)

将现有数据结构中的每个数据再单独成组，会增加一级数据结构。如上图，原来是五组数据，每组数据数量不同，现在也在编程五大组，n小组，每组一个数据。打个比方就是，本来有五个房间，每个房间住着不同数量的人，现在graft之后，给五个房间按照房间内人数划分单间，保证一人一个房间。

Graft的目的，在于给每个数据放到一组内，比如下图，square运算器输出端cells的数据结构为五组，每组三个数据，也就是说有五组矩形，每一组三个矩形，我现在希望这五组矩形每组高度都递增，那我就需要给五组高度值，而不是一组数据五个高度值，这样五组矩形，和五组高度才能一一对应。这时候我们就需要graft，如果不进行graft，那就是五组数据，和一组数据的运算，每一组矩形里的三个矩形都会和五个高度值进行运算，于是每一组的第三个矩形就被重复挤出了两次，因为多出了两个数据，只能和最后一个矩形最后一个数据计算。这就不是我们想要的结果了。

![img](http://www.rhinostudio.cn/files/course/2019/03-05/174003331e1e555820.png)

![img](http://www.rhinostudio.cn/files/course/2019/03-05/17404199a54e034070.png)

诸如此类，graft是一个挺常用的运算器，我们graft的目的就是方便发想要的数据放到一组内，因为运算器运算的只能是组内数据。

### Prune Tree输出数据

![img](http://www.rhinostudio.cn/files/course/2019/03-05/175340405b80108116.png)

输出数据支，删除指定长度外的数据结构

### Simplify tree简化数据结构

![img](http://www.rhinostudio.cn/files/course/2019/03-05/181959fe0382413610.png)

把冗余的数据结构路径名称简化。

### Tree Statistics数据统计

![img](http://www.rhinostudio.cn/files/course/2019/03-05/18200660767a641595.png)

返回数据结构的数据路径名称（Paths），每一支数据路径内数据的个数（Length），以及总数据支个数（count）。

### Trim Tree—修剪树

![img](http://www.rhinostudio.cn/files/course/2019/03-05/182306a644c1891059.png)

修剪数据结构，根据指定的层级Depth来修剪数据结构，比如1，那就修剪一级，本来是{A；B；C}三级，修剪完之后就变成了{A；B}两级，然后原来C数据支上的数据都被放到了上一级也就是B上。

### Unflatten Tree—数据结构拍回去

![img](http://www.rhinostudio.cn/files/course/2019/03-05/184516c337f9395429.png)

我们之前说flateen是最暴力的运算器，但并不是无可挽回的，这个Unflatten Tree就可以把你拍平的数据结构拍回去，不过得输入之前的数据结构作为Guide指导。

### Entwine缠绕

![img](http://www.rhinostudio.cn/files/course/2019/03-05/19020913d401819602.png)

拍平并按照输入端指定的路径名称组合输入数据。默认会拍平所有输入端的数据。当然你也可以右键取消拍平。这样的话，entwine运算器就会在输入端数据的基础上增加数据结构，如下图。

![img](http://www.rhinostudio.cn/files/course/2019/03-05/19324088a558734054.png)

![img](http://www.rhinostudio.cn/files/course/2019/03-05/1932226c4519679418.png)

### Explode Tree爆炸树

![img](http://www.rhinostudio.cn/files/course/2019/03-05/1935324ba315494883.png)

炸开数据结构。不过你需要右键选择Match outputs来让输出端匹配数据结构的数量。

![img](http://www.rhinostudio.cn/files/course/2019/03-05/193623716fef748160.png)

### Flip Matrix翻转数据结构

![img](http://www.rhinostudio.cn/files/course/2019/03-05/1938091187fe964512.png)

如上图，把原来的六大组，每组四个数据，翻转成四大组，每组六个数据。

翻转前：

![img](https://www.rhinostudio.cn/files/course/2019/03-05/194114a68768150125.png)

翻转后：

![img](http://www.rhinostudio.cn/files/course/2019/03-05/19412226fe9e982307.png)

不过Flip matrix仅限于这种简单的数据结构，当数据结构有多个级别的时候就不行了。

### Merge合并

![img](http://www.rhinostudio.cn/files/course/2019/03-05/2121073c72e3449406.png)

合并相同路径下得数据。注意这个合并，必须是相同的路径。注意这里的相同是完全相同，{0；0}和{0}是不一样的数据结构，切记。

![img](http://www.rhinostudio.cn/files/course/2019/03-05/213300c0c881720003.png)

![img](http://www.rhinostudio.cn/files/course/2019/03-05/214026aec80c947757.png)

所以，我一般习惯在用它的时候，习惯性simplify。

### Match Tree数据结构的名称匹配成另一组

![img](http://www.rhinostudio.cn/files/course/2019/03-05/215715b77c80937403.png)

将一组数据结构的名称匹配成另一组。两组的数据结构数量应当一致，否则会报错。

### Path Mapper数据结构编辑器

![img](http://www.rhinostudio.cn/files/course/2019/03-05/220109568ac2653018.png)

数据结构编辑器，GH当中，最强的数据结构处理运算器，没有之一。可以做很多事情。我们可以直接右键点击，选择一些已经预设好的功能。

![img](http://www.rhinostudio.cn/files/course/2019/03-07/224122296837498648.png)

**Create Null Mapping**

NUll嘛，自然就是什么都不操作呗，之前什么样，之后还什么样。但是你可以看到Path Mapper运算器上显示了文字{A；B；C}，而这个就是输入端的数据结构格式。意思是有三级路径，只不过实际上前两组是冗余的{0；0}。

![img](http://www.rhinostudio.cn/files/course/2019/03-07/224533d7d3be494972.png)

**Create Flatten Mapping**

即我们前面刚讲的运算器flatten，flatten的本质嘛，不就是砍掉所有数据结构，把所有数据按顺序放在{0}或者你指定的其他路径内嘛，所以你学了path mapper应该是对数据结构有了更深的理解。

![img](http://www.rhinostudio.cn/files/course/2019/03-07/224914aaae28506352.png)

所以这时你完全可以双击path mapper打开编辑窗口，修改Target路径名称，想怎么改就怎么改。

![img](http://www.rhinostudio.cn/files/course/2019/03-07/2252022565d0834818.png)

**Creat Graft Mapping**

即Graft，给数据单独成组，那你可以看到，Path Mapper上显示{A;B;C}(i)到{A;B;C;i}，也就是说，本来三级路径，i是数据个数，现在，编程四级数据，多了一级“i”，也就是根据数据个数，再分组。这就是Graft的本质。

![img](http://www.rhinostudio.cn/files/course/2019/03-07/225852c0bd99917633.png)

**Create Trim Mapping **

即，Trim Tree，修剪数据，网上砍了一级，Path Mapper上显示{A;B;C}到{A;B}，C哪去了？被砍了呗，所以C级路径上的所有数据都被放到{0；0}里了，而{0；0}本身只有一支，所以所有数据都被放到一起了。

![img](http://www.rhinostudio.cn/files/course/2020/04-17/102950eb62e3151137.png)

那要是想砍两级咧？简单：

**Create Reverse Mapping**

即运算器revers list，翻转数列，不就是把前面的数据放到后面，后面的放到前面，所以你可以看到path mapper变成了，{A;B;C}(i)到{A;B;C}(item_count - 1 - i)，而item_count就是用来求列表长度的，-1是因为列表从0开始计数，-i那就是翻转数列咧~是不是清晰了呢~？

![img](http://www.rhinostudio.cn/files/course/2019/03-08/000100c85cfd667163.png)

**Create Renumber Mapping**

无视原数据结构分级，讲所有数据结构分支逐个排列。管你之前十几大组几小组，现在统统01234挨个排列数据结构。而这里的path_index，其实就是用路径名称的序号来代替原数据结构。

![img](http://www.rhinostudio.cn/files/course/2019/03-08/000547ba0fe9912532.png)

![img](http://www.rhinostudio.cn/files/course/2019/03-09/12075178b0e0448640.png)

经过上面的默认功能的介绍，相信你已经知道Path Mapper是一个多么强大的运算器了，别急，还没结束，我们再来看看path mapper还可以干什么~比如：

{A}(i)-{i}(A)，就是flip matrix，翻转数据结构的本质。

![img](http://www.rhinostudio.cn/files/course/2019/03-09/1105404a2356053786.png)

ok~升级一下难度~变成三组数据结构，这时候flip matrix就失效了，flip matrix处理不了复杂数据结构，这时候你就必须依赖Path mapper了。

![img](http://www.rhinostudio.cn/files/course/2019/03-09/11083752f929453284.png)

你也可以~再进一步~使得上下可以连线。总之，你可以随心所欲的修改其分组方式。

![img](http://www.rhinostudio.cn/files/course/2019/03-09/11094261094f651394.png)

再比如呢：{A;B}(i)--{A;B;floor(i/(item_count/4))},把数据分成四组，不论数据到底有多少个，统统分成四组。不过我估计大家会有点迷糊，看不大懂是什么意思，没事，我来给大家解读一下。

![img](http://www.rhinostudio.cn/files/course/2019/03-09/1124375a5401265692.png) 首先，你在输入的时候不要使用中文输入法，可能会出错，然后呢，我们来看item_count求得就是当前分支内list的数量，求出来应该是10，因为咱们之前的series等差数列总共就十个数嘛，然后/4,这里需要注意一下“/”“\”这俩是不一样的，区别就是：

![img](http://www.rhinostudio.cn/files/course/2019/03-09/112855791a46680477.png)

所以在使用的时候千万别用错了。所以item_count求出10再除以4得到2.5，然后是i/(item_count/4)，那么我们知道，i其实是list里的序号，那我们简单列举几个你就知道了，

i=0也就是序号为0的时候，0/2.5=0

i=1也就是序号为1的时候，1/2.5=0.4

i=2也就是序号为2的时候，2/2.5=0.8

i=3也就是序号为3的时候，3/2.5=1.2

i=4也就是序号为4的时候，4/2.5=1.6

i=5也就是序号为5的时候，5/2.5=2

i=6也就是序号为5的时候，6/2.5=2.4

......

依次类推，会得到十个值是不，那再看前面还有一个flooor（x）的函数，这是啥？其实你之前就接触过，简单说，就是返回不大于x的最大的整数。

![img](http://www.rhinostudio.cn/files/course/2019/03-09/113730a73181505797.png)

所以呢

i=0也就是序号为0的时候，floor（0/2.5）=0

i=1也就是序号为1的时候，floor（1/2.5）=0

i=2也就是序号为2的时候，floor（2/2.5）=0

i=3也就是序号为3的时候，floor（3/2.5）=1

i=4也就是序号为4的时候，floor（4/2.5）=1

i=5也就是序号为5的时候，floor（5/2.5）=2

i=6也就是序号为6的时候，floor（6/2.5）=2

......

![img](http://www.rhinostudio.cn/files/course/2019/03-09/114216862a89397791.png)

懂了不~这样就把整个列表分成了四组，自动去求每一个数据该分到哪一组，所以才会有上图这样每组数量还不一样的情况出现。但是不论你数据量是多少，永远给你分成四组。

![img](http://www.rhinostudio.cn/files/course/2019/03-09/11432191b037321928.png)

所以，拓展一下，如果你改成ceiling（x）会怎么样？

![img](http://www.rhinostudio.cn/files/course/2019/03-09/114710e1ee79364230.png)

那，如果是四舍五入的round（x）呢？不过比较尴尬的是没有输入端，如果我想改组数我还得双击进来改，而不能和slider等运算器联动。

![img](http://www.rhinostudio.cn/files/course/2019/03-09/114757d410fa923971.png)

所以，path mapper是一个自由度很大的数据结构处理运算器。再比如把所有B级路径=2的数据支分到一组，其余的分到另一组：

![img](http://www.rhinostudio.cn/files/course/2019/03-09/121455fdee0a542928.png)

再比如，讲数据结构两两合并

![img](http://www.rhinostudio.cn/files/course/2019/03-09/130901dab5f4516102.png)

再比如，讲列表中的数据两两分组，作用上等于Partition List。

![img](http://www.rhinostudio.cn/files/course/2019/03-09/131215f40f86943794.png)

再比如，讲数据结构按照奇偶的路径分成两组数据。

![img](http://www.rhinostudio.cn/files/course/2019/03-09/15095428ee0a504086.png)

翻转数据结构：

诸如此类，用法其实很多，完全看你需要，单单这一个运算器我们就已经说的足够多了，虽然即便如此还没有全部囊括，有时间遇到了再补充吧， 不过好处是，大部分情况下，你都不会遇到这么复杂的数据处理的情况，但是这个东西对于帮助你理解数据结构来说还是很有用的。

### Shift Paths

![img](http://www.rhinostudio.cn/files/course/2019/03-09/132618a80d4d923141.png)

偏移数据结构，功能有点像trim tree，不过一个是正，一个是负，shift paths设置为-1那就是砍掉最后一级数据结构，然后第二级所有相同路径的数据放到一起。

![img](http://www.rhinostudio.cn/files/course/2019/03-09/13335979e0a2103672.png)

### Split Tree分割数据

![img](http://www.rhinostudio.cn/files/course/2019/03-09/133625999127007693.png)

分割数据结构，将指定路径名称的数据支和其他数据支分离出来。除了直接输入路径名称之外，还有一些特殊操作，比如输入

{0,2,...}
{1,3,...}

：那就是单独摘出偶数路径和奇数路径

![img](http://www.rhinostudio.cn/files/course/2019/09-08/2330444ce933831689.png)

![img](http://www.rhinostudio.cn/files/course/2019/09-08/233229d752be691200.png)

这还没完，还可以像下面这么写，这样就是提取奇数数据支中的偶数序号数据

![img](http://www.rhinostudio.cn/files/course/2019/09-08/233438e6a0a4189178.png)

那要是这么写呢：

![img](http://www.rhinostudio.cn/files/course/2019/09-08/233525d49144079732.png)

这么写就是抽离出偶数数据支中的奇数项，和奇数数据支的偶数项咯。是不是很简单。

还有一种写法{*;1} {0;*}，可以只提取指定路径数值的路径：

![img](http://www.rhinostudio.cn/files/course/2020/03-21/23191649394b403216.png)

![img](http://www.rhinostudio.cn/files/course/2020/03-21/23184776be04681617.png)

### Stream Filter数据流过滤器

![img](http://www.rhinostudio.cn/files/course/2019/03-09/133815729b07588990.png)

根据Gate端输入的数值控制输出哪一个数据端。你可以放大之后任意增加输入端。

![img](http://www.rhinostudio.cn/files/course/2019/03-09/1339473c0a04284854.png)

### Stream Gate数据流闸门

![img](http://www.rhinostudio.cn/files/course/2019/03-09/134408880b48843645.png)

控制你的数据输出到哪个输出端。

我曾经模仿cad的一个插件写了一个快速布置房间的小程序，很大程度上就是依赖上面两个运算器来做判断。有兴趣的同学可以自己研究一下~~~

![](http://www.rhinostudio.cn/files/course/2019/03-09/134607fb5294510789.gif)

![img](http://www.rhinostudio.cn/files/course/2019/03-09/134837534bd1255289.gif)

### Relative Item相关项目

老外视频原网址，英语好的可以看一下

[Grasshopper Masterclass With David Rutten](https://vimeopro.com/rhino/grasshopper-masterclass-with-david-rutten/video/79914764)

首先，如下图，这是我们的初始数据，七大组，每组五个数据，如果直接polyline连线，就是七根竖线。

![img](http://www.rhinostudio.cn/files/course/2019/03-09/153927f91c11494535.png)

那么如果我想斜方向连线怎么办？如下图，我们要做的就是对角相连，也就是说{0；0；0}0和{0；0；1}1连线，每一根线其实由{0；0；+1}（+1）的前后两个数据相连来得到的。

![img](http://www.rhinostudio.cn/files/course/2019/03-09/155446626adf197041.png)

所以我们回过头来看看咱们开始的图，下图，你就知道这个运算器在干什么了。

![img](http://www.rhinostudio.cn/files/course/2019/03-09/1557128a4615371867.png)

ok~这样的话，下面这个你也就应该知道在干啥了~

![img](http://www.rhinostudio.cn/files/course/2019/03-09/155854ee5d68884414.png)

这个时候，我们回过头来看看lunchbox插件里的几个运算器~你就知道，其实很多事gh自己就可以做，大多数插件只是让它变简单了

![img](http://www.rhinostudio.cn/files/course/2019/03-09/1604364d12bc325709.png)

### Relative Items

![img](http://www.rhinostudio.cn/files/course/2019/03-09/1602146d9f62253186.png)

刚才的是一组数据内自己计算，现在是两组数据计算，逻辑一样

### Tree Branch抽取指定路径的数据

![img](http://www.rhinostudio.cn/files/course/2019/03-09/135243b71c13823934.png)

根据数据路径名称抽取指定路径的数据。

### Tree Item

![img](http://www.rhinostudio.cn/files/course/2019/03-09/151127fb89e9398867.png)

根据指定的路径path和徐海index抽取指定数据路径中指定序号的物体。

### Deconstruct Path&Construct Path

![img](http://www.rhinostudio.cn/files/course/2019/03-09/1501106dd661169545.png)

讲路径名称拆解成多个数字&讲多个数字组合成数据路径名称

### Path Compare

![img](http://www.rhinostudio.cn/files/course/2019/03-09/1514593567fa364816.png)

比较path端中的数据路径是否和mask的路径名称一致，返回布尔值

### Replace Paths

![img](http://www.rhinostudio.cn/files/course/2019/03-09/1517371d58e1502939.png)

替换search端指定路径为你设置的路径Replace端，如上图，我们把数据结构中的{0；0；2}替换成{0；0；3}，这样的话数据结构中的{0；0；2}的数据就和{0；0；3}合并成一个了，并且数据结构中少了{0；0；2}的这一组。

# Vector向量

## Field磁场

这个组里的运算器都是用来模拟磁场效果的， 关于这部分运算器的用法，详细的，请看犀流堂的《磁力图案小教程》这节课，有详细的用法，这里仅做单个运算器的讲解：

![img](http://www.rhinostudio.cn/files/course/2018/10-08/11220806cc9a981160.jpg)

### Line Charge

![img](http://www.rhinostudio.cn/files/course/2019/03-19/2105586e90ca686869.png)

生成一个直线力场，Line端输入直线，Charge端控制场力大小，Bounds端虽然数据类型是box，但是直接输入矩形也没有问题，这样生成的就是平面的磁场。但是如果你给的是box，那么就可以得到的一个空间磁场。如下图，可以看你到每个采样点处的磁力方向都是不一样的。

![img](http://www.rhinostudio.cn/files/course/2019/03-19/2112204e3234217457.png)

###  Tensor Display

磁场矢量方向预览运算器。field端：输入磁力Section端：输入预览界面，只能是矩形界面，所以想预览空间力场的话，就多给几个截面呗。Samples是采样点数量，运算器会自动细分你输入的矩形生成采样点。

### Point Charge

![img](http://www.rhinostudio.cn/files/course/2019/03-19/220306a1fb3a083671.png)

根据点生成一个磁场力，Charge端控制场力大小，Decay控制衰弱强度，Bounds同上。

### Scalar Display

Tensor Display只能显示磁场中采样点力的方向，并不能看出来力的大小，这时候就需要scalar display了，它可以用来显示磁场强度变化的运算器，你可以很明显的在上图看到颜色的衰减，由于衰减值设置的比较大，所以黄色很快渐变成红色。如下图，减小衰减值，可以看到黄色区域也就是点磁场力的影响区域急剧变大。

![img](http://www.rhinostudio.cn/files/course/2019/03-19/220533d94ae7633930.png)

### Spin Force

![img](http://www.rhinostudio.cn/files/course/2019/03-19/2222091150cf511655.png)

螺旋磁场力，Radisu控制场力半径，其他的都一样。

### Vector Force

![img](http://www.rhinostudio.cn/files/course/2019/03-20/191851b9d9ac111833.png)

根据指定的Line生成一个以次直线起始点形成的矢量的磁场力。和Line Charge不一样，Vector Force是整体都朝着一个方向的场力。

### Merge Fields & Break Field

![img](http://www.rhinostudio.cn/files/course/2019/03-20/192415fa364a055631.png)

磁场力是需要通过merge filed来合并才能形成一个复杂的磁场的，即便你给了多个数据，在merge field之前都是分开的单独的磁场，那么break field你就应该知道是干嘛的了。

### Evaluate Field

![img](http://www.rhinostudio.cn/files/course/2019/03-20/193019b9c426892856.png)

测量磁场内point端指定点的场力方向和大小。

### Field Line

![img](http://www.rhinostudio.cn/files/course/2019/03-20/19562375f0e8910692.png)

根据给定磁场Field，生成场线。采样数越高，精度越高，曲线精度值越小，精度越高，Method端控制的是生成曲线阶数，默认就好，一般都不改。

### Perpendicular Display

![img](http://www.rhinostudio.cn/files/course/2019/03-20/20333934dd49712930.png)

之前咱们说了，所有场力的Bounds都是BOX，但是你输入矩形也没问题，照样可以生成，但是不代表磁场力是平面的，实际上场力都是空间的，这个运算器，就是用来判断空间当中场力的方向是垂直向上，还是垂直向下。默认向上是白色，向下是黑色，从而可以快速判断磁场中的力方向。

### Scalar Display

![img](http://www.rhinostudio.cn/files/course/2019/03-20/204134e082e7802589.png)

通过颜色来显示当前磁场中场力大小，只能看出大小，不能看出方向。

### Direction Display

![img](https://img.kancloud.cn/99/fe/99fe7afda6f90221944093d6a9d52a94_1307x724.png)

显示磁场中力的方向。

## Grid图形阵列运算器

很多都会作为我们表皮的开始，对于建筑来说，还是比较常用的，由于很多人学习GH都是从表皮开始，所以这一组运算器算是大家的启蒙运算器了，那我们来一起看一下吧

### Hexagonal六边形图形阵列

![img](http://www.rhinostudio.cn/files/course/2019/04-01/222310e9d8f1753386.png)

### Radial蜘蛛网阵列图案

![img](http://www.rhinostudio.cn/files/course/2019/04-01/222747344f50859617.png)

### Rectangular矩形阵列图案

![img](http://www.rhinostudio.cn/files/course/2019/04-01/223124c1f1c7004191.png)

### Square正方形图形阵列

![img](http://www.rhinostudio.cn/files/course/2019/04-01/223422e9f066541898.png)

### Triangular三角形图形阵列

![img](http://www.rhinostudio.cn/files/course/2019/04-01/2235324a3792282661.png)

### Populate 2D

![img](http://www.rhinostudio.cn/files/course/2019/04-01/2237360bf857888320.png)

在矩形范围内随机生成指定数量的点，这里的Seed种子和之前的一个意思，就不赘述了。需要注意的是，你可以在points端提前输入点，这样随机生成的点就不会出现在你指定的点的位置。基于这个，咱们做过一个东京空余立面的例子

![img](http://www.rhinostudio.cn/files/course/2018/08-04/0128022dcc63332066.jpg)

### Populate 3D

![img](http://www.rhinostudio.cn/files/course/2019/04-01/224115b76101001568.png)

上一个是在矩形范围生成，这一个是在box内生成，二维升三维，升维打击

### Populate Geometry

在任意物体表面生成指定数量随机点。

![img](http://www.rhinostudio.cn/files/course/2019/04-01/224554223276967454.png)

## Plane

### Deconstruct Plane

拆分工作平面得到工作平面的原点即xyz轴

![img](http://www.rhinostudio.cn/files/course/2019/04-15/234859b416c4775655.png)

### XY plane & XZPlane & YZ Plane

![img](http://www.rhinostudio.cn/files/course/2019/04-15/235703fcb9e2192363.png)

三个最基本的工作平面，也是我们最常用的工作平面，正好对应我们的Top视图，Front视图，Right视图的默认工作平面。

### Construct Plane

![img](http://www.rhinostudio.cn/files/course/2019/04-16/233430673f37895477.png)

​	根据原点，x，y两个矢量构建一个工作平面，而由于直线可以直接拾取为矢量，你也可以这么干：

![img](http://www.rhinostudio.cn/files/course/2019/04-16/233753186717229050.png)

那，如果两根线或者两个矢量不是九十度呢？那y轴矢量就会像x轴做投影，所以，理所应当的，如果两个矢量平行，是不会生成有效的工作平面的：

![img](http://www.rhinostudio.cn/files/course/2019/04-16/2340055313cb483025.png)

### Line + Line两线构面

![img](http://www.rhinostudio.cn/files/course/2019/04-16/2341095098dc448656.png)

线的方向也会对结果有影响，具体原理参照矢量平行四边形原则

### Line + Pt

![img](http://www.rhinostudio.cn/files/course/2019/04-16/23434843eb61982624.png)

根据一根直线和一个点来确定一个工作平面，会以直线起点作为工作平面的原点，这个其实很好理解，直线起点终点加上我们指定的点，三点共面嘛，自然确定一个工作平面了。

### Plane 3Pt

![img](http://www.rhinostudio.cn/files/course/2019/04-16/2348546b074a696649.png)

你看，刚说的三点共面，这就来现成运算器了，其实嘛，AB两点一条线，AC两点一条线，就和上面line+line运算器一样了

### Plane Fit

![img](http://www.rhinostudio.cn/files/course/2019/04-17/001211b7e226260844.png)

根据输入的一对点适配一个最合适的工作平面，比较神奇的是工作平面原点距离输入点经常会很远，表示不解，按照我的理解工作平面应该原点是输入点的中心点。不过工作平面本身就是一个无限平面，所以原点不原点的无所谓。另外除了返回工作平面之外，还会返回最远点的距离Deviation。

### Plane Normal

![img](https://img.kancloud.cn/ae/ca/aeca87b9c1f377a8fceeb5ed4362a0c0_1258x401.png)

以指定点为原点，指定矢量为z轴生成工作平面。那聪明的你可能会问，这样的话xy轴方向不是不确定么？所以这时候，我们就可以结合align plane来对齐平面确保x轴一直朝上。

![img](https://img.kancloud.cn/25/3f/253f49c4044d6986c0af7bdf83eab821_1477x437.png)

### Plane Offset

![img](http://www.rhinostudio.cn/files/course/2019/04-17/091931369d51120614.png)

平面也是可以偏移的，就是沿着平面z轴方向移动呗。

### Plane Origin

![img](http://www.rhinostudio.cn/files/course/2019/04-17/092202a9ec75222332.png)

修改工作平面原点到指定的点。

### Adjust Plane

![img](http://www.rhinostudio.cn/files/course/2019/04-17/09244918e0db320340.png)

根据指定z轴方向调整原有平面，其实就是给原来平面改了下z轴方向。

### Align Plane

![img](http://www.rhinostudio.cn/files/course/2019/04-17/092825930d1f621483.png)

以工作平面z轴旋转工作平面直到工作平面x和指定矢量方向夹角最小。我晓得这么说你肯定不是很理解，么事，咱们来看个雨水路径模拟的课程：

Anemone雨水路径模拟

### Align Planes

![img](http://www.rhinostudio.cn/files/course/2019/04-23/1139302d7364808290.gif)

对齐多个工作平面使得工作平面和Master端指定工作平面夹角最小。如果Master端未指定工作平面，则以输入工作平面中的第一个为对齐用平面。

### Flip Plane

![img](http://www.rhinostudio.cn/files/course/2019/04-23/1133553632a7497196.gif)

翻转平面轴向或者对调xy轴。

### Plane Closest Point

![img](http://www.rhinostudio.cn/files/course/2019/04-23/11423398099e199549.png)

求点到指定平面的最近点及其各项属性

### Plane Coordinates

![img](http://www.rhinostudio.cn/files/course/2019/04-23/114932cbb282490952.png)

求点在指定工作平面的坐标

### Rotate Plane

![img](http://www.rhinostudio.cn/files/course/2019/05-02/1516033af329486502.png)

将工作平面绕着其z轴进行旋转。

## Point

### Construct Point & Deconstruct

![img](http://www.rhinostudio.cn/files/course/2019/05-02/203507b97468358677.png)

根据指定的xyz三轴坐标值构建一个坐标点 & 拆解一个坐标点，获得其xyz坐标值

### Numbers to Points

![img](http://www.rhinostudio.cn/files/course/2019/05-02/204234a0a31b593902.png)![img](http://www.rhinostudio.cn/files/course/2019/05-02/2043517931a6184810.png)

将一个数字列表转化成点，numbers端输入的数字个数需要时三的倍数，不然会报错

### Points to Numbers

![img](http://www.rhinostudio.cn/files/course/2019/05-02/204459b8e1d4929004.png)

将点根据Mask端，拆解成数字列表，和上一个运算器相反。

### Barycentric

![img](http://www.rhinostudio.cn/files/course/2019/05-02/210830ec9da6150799.png)

三角形重心坐标系运算器，首先根据指定的ABC三个点构建三角形，然后根据重心坐标系获得三角形当中的点，至于什么是重心坐标系·····嘛，反正我没用过，不过貌似在计算机图形学里挺普遍的，反正我看不大懂就是了····。

![img](http://www.rhinostudio.cn/files/course/2019/05-02/210655f3c16e695816.png)![img](http://www.rhinostudio.cn/files/course/2019/05-02/2110113a6319060407.png)

### Distance

![img](http://www.rhinostudio.cn/files/course/2019/05-02/2111368c766f783802.png)

测量AB两点之间的距离。

### Point Cylindrical

![img](http://www.rhinostudio.cn/files/course/2019/05-02/2127379d3a34742033.png)

点圆柱坐标系，这么给各位看，应该就很清楚了~，根据角度，半径长度和高度来定位点，是区别于xyz坐标系的另一种空间点定位系统。就是···我没怎么用过就是了。

![img](http://www.rhinostudio.cn/files/course/2019/05-02/212858aed7ff721238.png)

### Point Oriented

![img](http://www.rhinostudio.cn/files/course/2019/05-02/213540ccaa68669968.png)

根据指定工作平面的坐标系来生成指定工作平面上的点。

### Point Polar

![img](http://www.rhinostudio.cn/files/course/2019/05-03/100808888d3f709888.png)

极点坐标系。根据xy平面角度，与z轴角度，和距离平面原点长度来定位空间当中任意一个点。看一下下面这个图，你可能会更加直观这个坐标系在实际当中的应用

### To Polar

![img](http://www.rhinostudio.cn/files/course/2019/06-20/09270487e0bd191234.png)

获得指定点在指定平面上的极坐标系坐标，即其平面角，垂直角和距离平面原点的长度。另外，这个运算器可以右键弹出菜单，选择【pole down angles】，那这时获得的就是垂直角的补角了。

![img](http://www.rhinostudio.cn/files/course/2019/06-20/09273023b90a973646.png)

![img](http://www.rhinostudio.cn/files/course/2019/06-20/0927208db258579799.png)

### Closest Point

![img](http://www.rhinostudio.cn/files/course/2019/05-03/101421dedb22353346.png)

找到指定点（point）在一堆指定点集（Cloud）中的最近点，并返回各项相关数据。

### Cull Duplicates

![img](http://www.rhinostudio.cn/files/course/2019/05-03/120605dbaa74487842.gif)

删除指定公差内的重复点并保留重复点的合并点（重复点xyz值的平均值）。其中Indices输出的是未被删除的点的额序号，删除的都会合并成序号-1。Valence输出的是合并的位置由多少个重复点。

### Point Groups

![img](http://www.rhinostudio.cn/files/course/2019/05-03/123613d7e659230405.png)

判断点与点之间的距离是否满足设顶的距离distance值，小于这个数值的，将被划分到同一个数据支内，并返回每组内点的序号Indices

### Project Point

![img](http://www.rhinostudio.cn/files/course/2019/05-03/144757d313b3044871.png)

将点（point）按照指定矢量方向（Direction）投影到指定物体（Geometry）上，如果物体有复数个，则只投影到最近物体上，并返回投影点，以及被投影物体的序号。通过它，你可以筛选出最接近指定点的物体。

### Pull Point

![img](http://www.rhinostudio.cn/files/course/2019/05-03/173242a0dae5782014.png)

这个运算器简直不要太常用，由于干扰类表皮很普遍，很容易，而这个又是干扰最常用的运算器之一，所以我们经常会使用它

![img](http://www.rhinostudio.cn/files/course/2019/05-03/173435b4731e891773.jpg)

需要注意的是，后面大家还会学到一个运算器，叫 Curve Closest Point，但是这俩运算器是不一样的。

![img](http://www.rhinostudio.cn/files/course/2019/12-11/112428cced33200995.png)

Pull Point是求点在多个物件之间的投影点，然后保留最近的点，但是Curve Closest Point不是，这个运算器是会根据list运算规则，一一对应运算的。找个例子一对比你就知道了，pull point输入端俩个点，最后求得的当然就只有两个点。但是Curve Closest Point由于是一一对应运算，那多数来的数据也会运算，这仅仅是在求点和对应曲线的最近点，而不是所有曲线的最近点，所以曲线干扰我们不用这个运算器。

![img](http://www.rhinostudio.cn/files/course/2019/12-11/11280887ae11064770.png)

### Sort Along Curve

![img](http://www.rhinostudio.cn/files/course/2019/05-03/173701d60f85152976.png)

根据曲线对点重新进行排序。

### Sort Points

![img](http://www.rhinostudio.cn/files/course/2019/05-03/173827400d9b459525.png)

将点根据xyz坐标进行排序，先比较x坐标大小，再比较y最后再比较z

## Vector

这一组的运算器主要是和矢量相关的，而矢量，是高中数学当中的内容，所谓的矢量，就是一种既有大小又有方向的量，又称为向量 。矢量可以加减，矢量有平行四边形原则等，是不是有点想起来了？以后你会极其经常的用到矢量

### Deconstruct Vector

![img](http://www.rhinostudio.cn/files/course/2019/05-03/185347b62f81561432.png)

拆解矢量为xyz三轴投影长度，因为矢量的平行四边形法则，所有矢量都可以随便移动到原点，毕竟，矢量只规定方向和大小，而没有规定位置。

### Vector XYZ

![img](http://www.rhinostudio.cn/files/course/2019/05-03/1855528349b2078198.png)

根据XYZ三轴长度来定义一个矢量（Vector）。同时返回矢量长度（Length）

### Unit Vector

![img](http://www.rhinostudio.cn/files/course/2019/05-03/18590265e99a090242.png)

将向量单位长度化，即不改变矢量方向，改变矢量长度为1

### Unit X Y Z

![img](http://www.rhinostudio.cn/files/course/2019/05-04/102439755631363579.png)

单位向量X Y Z，基础运算器。通过Factor端数值，可以控制向量长度。

### Amplitude

![img](http://www.rhinostudio.cn/files/course/2019/05-04/102903fb7cd1443051.png)

修改指定向量（Vector）的向量长度为指定数值（Amplitude）

### **Angle**

![img](http://www.rhinostudio.cn/files/course/2019/05-04/10341133cd48492036.png)

判断两个矢量之间的夹角，首先，矢量可以位移，所以如果两个矢量不在同一处，可以移动两个矢量到同一个端点处，其次，矢量是有方向的，所以如果两个矢量方向相反，比如下面的两个矢量：

![img](http://www.rhinostudio.cn/files/course/2019/05-04/1036535962dd943781.png)

那么，这两个矢量的夹角就应该是：

![img](http://www.rhinostudio.cn/files/course/2019/05-04/10385827aa2e772169.png)

输出端Angle为夹角，输出端Reflex为反角。需要注意的是，两个矢量的顺序也会影响角度结果。举个栗子，我们先把plane端的xy平面删了，然后看一下：

![img](http://www.rhinostudio.cn/files/course/2019/05-04/1044535c9d55297684.png)

ok，这个时候我们调转一下A和B矢量，你会发现，角度依然是133，并没有变，这是因为没有给定工作平面，所以依然按照两个之间的最小角来判断，也就是说，如果你不给定plane的话，两个矢量夹角永远不可能大于180，这显然是不对的，因为有的时候我们就是需要判断超过180的角度。

![img](http://www.rhinostudio.cn/files/course/2019/05-04/104848013643285544.png)

所以这时候，我们加上限定平面xy平面，结果就显示正确了，运算器按照逆时针，判断A到B矢量的夹角。这样，才会出现超过180度的情况。

![img](http://www.rhinostudio.cn/files/course/2019/05-04/105108c5af6c395149.png)

### **Cross Product**

![img](http://www.rhinostudio.cn/files/course/2020/02-24/234326e81c34562457.png)

向量积，数学中又称外积、叉积，物理中称矢积、叉乘，是一种在向量空间中向量的二元运算。与点积不同，它的运算结果是一个向量而不是一个标量。并且两个向量的叉积与这两个向量和垂直。简单说，就是用来求两个矢量组成工作平面的垂直方向，即z轴。

![img](http://www.rhinostudio.cn/files/course/2020/02-24/234654e54008460168.png)

![img](http://www.rhinostudio.cn/files/course/2020/02-24/2348320d6597162673.png)

### Dot Product

![img](http://www.rhinostudio.cn/files/course/2019/05-04/111245d3f2de176156.png)

求向量点积，而向量点积其实就是两个矢量xyz值乘积的和，而向量有什么意义呢？事实上，向量的点积结果和两个向量之间的角度有关。

![img](http://www.rhinostudio.cn/files/course/2019/05-04/114742e44cb8848546.png)

### **Reverse**

![img](http://www.rhinostudio.cn/files/course/2019/05-04/11470593cdfe219267.png)

翻转矢量方向。

### **Rotate**

![img](http://www.rhinostudio.cn/files/course/2019/05-04/115803b352ad510109.png)

将指定矢量（Vector）以指定轴向（Axix）旋转指定角度（Angle）。

### **Vector 2Pt**

![img](http://www.rhinostudio.cn/files/course/2019/05-04/120022614813152546.png)

根据两个点生成矢量（Vector），并返回矢量长度（Length）。

### **Vector Length**

![img](http://www.rhinostudio.cn/files/course/2019/05-04/1201266ad7a3294632.png)

返回矢量长度。

# Curve

![img](http://www.rhinostudio.cn/files/course/2019/08-08/221538a6d772554584.png)

Curve组当中的运算器都是和曲线处理相关的，基本上都很常用。

## Analysis分析

### **Control Points**

![img](http://www.rhinostudio.cn/files/course/2019/05-04/1624204676d6424486.png)

提取曲线控制点（Points），以及曲线控制点权重（Weights），Konts为节点向量大小，后两个输出端我从没有用过。

### **Curve Middle**

![img](http://www.rhinostudio.cn/files/course/2019/08-08/221658a8db9a339458.png)

获取曲线中点。

### **Control Polygon**

![img](http://www.rhinostudio.cn/files/course/2019/05-04/1750488d2352154526.png)

获取曲线控制点并连接成多段线。

### **Deconstruct Arc**

![img](http://www.rhinostudio.cn/files/course/2019/05-04/1807335306c6988459.png)

分解圆弧，获得其圆心，半径，和角度范围。

### **Deconstuct Rectangle**

![img](http://www.rhinostudio.cn/files/course/2019/05-04/181300cae453363908.png)

分解矩形，返回矩形中心点工作平面以及长宽，即xy interval，用区间表示矩形长款。上图的长宽为3 和 4。

### **End Points**

![img](http://www.rhinostudio.cn/files/course/2019/05-04/181701d2ba8c700554.png)

获取曲线起点和终点。如果曲线是封闭曲线，那么起点和终点都是同一个点。

### **Polygon Center**

![img](http://www.rhinostudio.cn/files/course/2019/05-04/192311fc019c727148.png)

求多边形中心点，输出端有三个，对应三种算法。以控制点还是以边还是以面积为基准，算出来的中心点如果是规则形状是一样的，如果是不规则形状（如上图）是不一样的。但是，如果我们自己提取多边形的控制点，然后求平均值的话，会发现和Polygon Center求的不一样，这是为什么呢？

![img](http://www.rhinostudio.cn/files/course/2019/05-04/192935fc0e1b187492.png)

原因很简单，因为封闭曲线，起点和终点重合，所以点数多一个，多算了一次，删除起点或者终点就可以了，比如下图，我们删除了序号0的点也就是起点之后就ok了。

![img](http://www.rhinostudio.cn/files/course/2019/05-04/19313794e73d179891.png)

所以如果要求多边形中心点，也可以直接提取控制点求平均值来做。而第二个输出端Center（E），是以边缘为基准。其实就是按长度等分边缘，然后求平均值。

![img](http://www.rhinostudio.cn/files/course/2019/05-04/20034730fb4e725730.png)

第三个输出端Center（A），面积中心，可以用Area来求，但是不建议，虽然6.0中的Area运算器已经支持多线程，但是由于同时要求面积area，所以计算速度会慢很多，运算量比较大的时候不建议使用Area运算器求中心点，。

![img](http://www.rhinostudio.cn/files/course/2019/05-04/1936342a88e2906355.png)

### **Closed**

![img](https://img.kancloud.cn/1d/e7/1de788a761d572fd132db92c7197b1bf_1535x522.png)

判断曲线是否为闭合曲线或周期曲线。至于什么是周期化，Rhino里有个命令，就是用来修改曲线是否周期化的，这么说你可能不理解。

![img](http://www.rhinostudio.cn/files/course/2019/05-04/20144883f74a441710.png)

给你演示下你就知道了，点击右键非周期化：

![img](http://www.rhinostudio.cn/files/course/2019/05-04/201654643fb0158909.gif)

所以，即便是封闭曲线，也是分非周期和周期两种的。

### **Curvature Graph**

![img](http://www.rhinostudio.cn/files/course/2019/05-04/2042422e76f7972534.png)

曲率图形查看运算器。至于什么是曲率，这个运算器是干嘛的，各位可以参考Rhino帮助文件当中的解释：

![img](http://www.rhinostudio.cn/files/course/2019/05-04/2053531ba732117671.png)

![img](http://www.rhinostudio.cn/files/course/2019/05-04/2052215b9d1d092639.png)

![img](http://www.rhinostudio.cn/files/course/2019/05-04/205319f2ae36585278.png)

### **Curve Closest Point**

![img](http://www.rhinostudio.cn/files/course/2019/05-04/205732c37509701402.png)

求点到曲线最近点（Point），并返回点在曲线上的t值（Parameter），以及距离（Distance）。这里稍微解释一下t值。简单说，你可以理解为t值就是曲线的一维坐标系。可以通过t值定义曲线上的任意一点。比如t值如果区间是0-1，那么t=0则对应曲线起点，t=1则对应曲线终点。但是需要注意的是，曲线t值和曲线有关，t=0.5，并不对应曲线中点。除非是直线这种简单曲线。应用来说，知道这么多就差不多了，后面还会有很多运算器会用到t值。那么如果你想深入了解的话，可以看一下youtube的这个视频，深入了解下：

[Parameterize Curve 2 - What's a Parameter?](https://www.youtube.com/watch?v=RN-IaW_G4p0)

有同学询问curve closest point和pull poin的区别，如果仅仅是一个曲线的话，两者是一样的，区别在曲线为复数数量的时候：

![img](http://www.rhinostudio.cn/files/course/2020/03-25/203828452ac5118004.png)

![img](http://www.rhinostudio.cn/files/course/2020/03-25/203834a6e14b642128.png)

curve closest point是按照给定list，逐一精心运算，也就是超出数量的点和最后一根曲线计算最近点，而pull point是求所有目标曲线中的最近点，求最值。另外pull point本身除了曲线还可以是点，曲面等。

### **Curve Nearest Object**

![img](http://www.rhinostudio.cn/files/course/2019/05-04/2152353ab8e3894480.png)

查找曲线附近距离曲线最近的物件。

### **Curve Proximity**

![img](http://www.rhinostudio.cn/files/course/2019/05-04/22000222b40d988768.png)

查找两个曲线之间的最接近点。

### **Curve Side**

![img](http://www.rhinostudio.cn/files/course/2019/05-04/2210284d4424779511.png)

判断点在曲线的哪一侧。

### **Discontinuity**

![img](http://www.rhinostudio.cn/files/course/2019/05-05/110429d59525964621.png)

根据Level端，判断曲线不连续点。其中Level端输入1为不满足正且连续G2，2为不满足曲率连续G3，3=Cinfinite，即G3以上所有的连续性。至于什么是曲线连续性·····如果你不知道，那真的是rhino手工没学好，别信什么不学rhino直接学GH的鬼话，扎扎实实先学好Rhino，了解基础概念，对GH会有莫大帮助，更重要的是，实际工作当中，Rhino手工的比重，远远大于GH。这里姑且还是加上官方对连续性的解释吧。正常建筑满足正切连续就ok了。在国内施工质量面前，高了也没用，更何况再高的曲率，对于建筑来说最终都是要划分成一块一块嵌板的。

![img](http://www.rhinostudio.cn/files/course/2019/05-05/111228c3e903340672.png)

![img](http://www.rhinostudio.cn/files/course/2019/05-05/1112386af393996536.png)

### **Extremes**——判断最高最低点

![img](http://www.rhinostudio.cn/files/course/2019/05-05/1128331c766b715514.png)

判断曲线相对于指定平面的最高最低点。需要注意的是，这个运算器是计算曲线在指定工作平面z轴方向上的最高和最低点。所以呢，工作平面不能乱设置，一个xy平面的线指定xy平面作为参照平面那自然算不出来最高最低点。

![img](http://www.rhinostudio.cn/files/course/2019/12-11/11155289be65107058.png)

不过经犀流堂aomao同学提醒，发现这个运算器对圆弧处理有bug，并不能求得正确的最高最低点。

![img](http://www.rhinostudio.cn/files/course/2019/12-11/111916471102948467.png)

### **Planar**

![img](http://www.rhinostudio.cn/files/course/2019/05-05/11431202230e114513.png)

判断曲线是否为平面曲线。输出布尔值以及平面所在工作平面，以及曲线平面偏差值，而所谓曲线平面偏差值就是描述曲线有多不平。越不平，值越大，平面曲线，值为0。

### **Curvature**

![img](http://www.rhinostudio.cn/files/course/2019/05-05/115246ecf8cd068064.png)

根据曲线t值，求曲线对应点及其曲率。而曲率我们在前面给大家讲了，就是曲线对应点正切圆半径倒数。如果单纯建模不需要了解太过深入的知识，大多时候，这个运算器就是我们用来求点的。比较需要注意的，依然是这里的t值即Parameter端。

![img](http://www.rhinostudio.cn/files/course/2019/05-04/2052215b9d1d092639.png)

首先，一旦涉及到曲线的t值，和去边的uv坐标值，我们都会不管三七二十一先在曲线或曲面端右键点击，在下拉菜单中，点选Reparameterize，目的就是把曲线的t值区间重新参数化，即设置到0-1之间，因为大多数情况下，曲线的t值范围都不在0-1之间，重新参数化之后方便我们进一步操作。比如t=0，那可以得到曲线起点，t=1，得到曲线终点，但是前面也提到了，t=0.5不一定等于中点，除非你控制点均匀。这个是需要注意的。

![img](http://www.rhinostudio.cn/files/course/2019/05-05/1156364c7d9b265069.png)

### **Curve Frame**

![img](http://www.rhinostudio.cn/files/course/2019/05-05/142314238a37923316.png)

返回曲线指定t值位置处的工作平面，这个工作平面由曲线t值对应位置点在曲线上的切线方向为x轴，垂直方向为y轴构建，这个y轴，其实就是上一个运算器的曲率方向。

### **Derivatives**

![img](http://www.rhinostudio.cn/files/course/2019/05-05/145055f163f9698699.png)

返回曲线t值位置处的各种衍生属性，默认输出端为point和First Derivative（Derivatives）即速率。速率是标量，只有大小没有方向。速率是瞬时速度的大小或者等价于路程的变化率。速率是物体经过的路程 △S 和通过这一路程所用时间 △t 的比值。另外，你可以放大之后增加输出端，最多增加到六个。

![img](http://www.rhinostudio.cn/files/course/2019/05-05/1458240b47b7421612.png)

emmmm，各位看看就好，反正我到现在位置从没用过这个运算器。

### **Evaluate Curve**

![img](http://www.rhinostudio.cn/files/course/2019/05-05/151554aa0f58073238.png)

测量曲线t值位置处的点及其切线矢量方向。输出端Angle用处不明，也没怎么用过。经常有同学想做疏密变化的栅格什么的，利用下面几个运算器可以很容易的做到。

### **Horizontal Frame**

![img](http://www.rhinostudio.cn/files/course/2019/05-05/15485357b7f9765072.png)

返回曲线指定t值位置的平行于xy平面的平面，这个平面以曲线切线方向为平面x轴。所以可以很容易的做出下面这样的与曲线相切的截面来做诸如栏杆之类的物件。不过依然需要注意，由于t值和曲线距离没直接关系，所以等分t值得到的点，并不是等分的

![img](http://www.rhinostudio.cn/files/course/2019/05-05/155314aa941d291855.png)

除非你的线是直线，或者控制点均匀，你看我重建曲线之后，等分点就和t值取的点一致了：

![img](http://www.rhinostudio.cn/files/course/2019/05-05/1558240e5705778617.png)

### **Perp Frame**

![img](http://www.rhinostudio.cn/files/course/2019/05-05/160606e500c1011483.png)

返回曲线t值位置垂直平面。我经常用这个运算器来单轨做方管或其他异形截面管。

![img](http://www.rhinostudio.cn/files/course/2019/05-05/1609128db1c4519020.png)

### **Point On Curve**

![img](http://www.rhinostudio.cn/files/course/2019/05-05/16120558b8cf603268.png)

求曲线上点的运算器。你可以右键来选具体位置。

![img](http://www.rhinostudio.cn/files/course/2019/05-05/16191975594d292192.png)

需要特别注意的是，这里的取点和t值不同，是按照距离等分的。所以不用担心不准的问题。

![img](http://www.rhinostudio.cn/files/course/2019/05-05/162142682179923182.png)

### **Torsion**——扭力大小

![img](http://www.rhinostudio.cn/files/course/2019/05-05/1630091366b8403126.png)

返回曲线在t值位置处的点和扭力大小。但是····求了只能干嘛呢？我暂时没有用过。

### **Curve Domain**

![img](http://www.rhinostudio.cn/files/course/2019/05-06/091615f58a49242387.png)

测量并设置曲线区间。输入端的Domain为你想设置的曲线t值区间，输出端的Domain为原来曲线的t值区间。你可以看到后面被我修改过后的曲线，t=0.2的时候对应的是曲线的起点，就是因为曲线区间被我改成0.2-0.6了。

### **Evaluate Length**

![img](http://www.rhinostudio.cn/files/course/2019/05-06/091956c2f466792768.png)

根据曲线长度来返回曲线上的点。Normalized输入端如果为True，那就会重新参数化曲线，Length端输入0-1的值才行，那我要他有何用。就是冲着实际距离来的。那么我们有时候会遇到想要在曲线上两个距离间隔着求点，就可以利用这个运算器来做，比如点之间距离为0.5 1 0.5 1 0.5 1.......这样子，那具体该怎么做呢？？很简单，稍微活用一下前面的运算器，如下图：

![img](http://www.rhinostudio.cn/files/course/2019/05-06/093718eab055356776.png)
不等距的来分割点也是一样的做法
![img](https://img.kancloud.cn/a7/b9/a7b96e2cda31cdc84a3227cd45fa42f9_2365x890.png)

### **Length**

![img](http://www.rhinostudio.cn/files/course/2019/05-06/0937553e1623744355.png)

返回曲线长度。

### **Length Domain**

![img](http://www.rhinostudio.cn/files/course/2019/05-06/09393134bfee055116.png)

返回曲线指定t值区间范围内长度。

### **Length Parameter**

![img](http://www.rhinostudio.cn/files/course/2019/05-06/09441937f8b5397974.png)

返回曲线t值位置点分割成的前后两根线的距离。

### **Segment Lengths**

![img](https://www.rhinostudio.cn/files/course/2019/05-06/0953371a5f4c153577.png)

返回多重曲线当中最短和最长的一段线，以及其t值区间。

### Point In Curve

![img](http://www.rhinostudio.cn/files/course/2019/05-06/095548450740256188.png)

判断点（Point）是否在指定封闭曲线（Curve）内，输出端Relationship返回结果，点在曲线外则返回0，点在曲线上，则返回1，点在曲线内则返回2。所以我们就可以通过输出值是否等于2来筛选点。Point输出端为入股哦点不在曲线所在平面，则投影上去。

### Point in Curves

![img](http://www.rhinostudio.cn/files/course/2019/05-06/100204c82ae5004243.png)

判断点和多个曲线的包含关系。可以利用这个运算器来对图形根据所在曲线内进行分组。

![img](https://img.kancloud.cn/72/b5/72b557ff55a1f09310ac7a86a290b1bc_1287x435.png)

## Division

![img](http://www.rhinostudio.cn/files/course/2019/05-04/120505168727171800.png)

这一组里的运算器基本上都是涉及等分的，只是方式不同，结果不同，有的是点，有的是平面等，都挺常用的。

