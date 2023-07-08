##### Eevee引擎渲染玻璃

1. ###### 屏幕空间反射>反射
2. ###### 材质属性>设置>屏幕空间折射
3. ###### 混合模式/阴影模式调节



##### 渲染HDR贴图使用，HDR贴图使用

hdr图下载：https://polyhaven.com/ 

世界环境>表（曲）面>

![img](.\picture\25992384-6506fa965821e956.jpg)

##### 隐藏`HDR`贴图背景，不渲染背景

###### 渲染属性>胶片>透明

### 雕刻&绘制

#### 笔刷控制

- 设置笔刷大小——F
- 设置笔刷强度——Shift-F
- 旋转笔刷纹理——Ctrl-F
- 反转笔划切换——Ctrl

##### Blender ——顶点倒角

> 快捷键    Shift+Ctrl+B

##### 隐藏未选中的面——Shift+H

##### 取消隐藏——Alt+H



##### 材质

清漆，汽车外观使用



> 2023/6/14渲染贴图视频

COL贴图——颜色（漫反射贴图）

BUMP贴图，凹凸贴图

DISP贴图，置换贴图

NRM贴图，法线贴图

GLOSS贴图，光泽反射/粗糙度贴图



Ctrl+J——材质打组



> 制作3d logo

#### 渲染灯光

- 点光

- 日光

- 聚光灯

> 可做舞台灯光
> ![](F:\Git\presonalnote\Blender\picture\渲染舞台灯光.jpg)

- 面光——可设置ies光

### Blender 渲染物体和影子，不要地面

> 1. ###### 切换渲染器为Cycles
>
> 2. ###### 新建一个足够大的平面网格A，用于接受阴影
>
> 3. ###### 选中平面新建的平面网格A，设置物体属性。在物体属性可见性选项卡里勾选遮罩阴影捕捉。

### blender——让物体透明的同时显示来自其他物体的投影

![img](https://i0.hdslb.com/bfs/article/2f5277674cece575a7f9690b5984d1d070343c79.png@942w_377h_progressive.webp)

#### 操作步骤

###### 1：将渲染引擎设置为cycles

![img](https://i0.hdslb.com/bfs/article/a8fce3ae3e5a8676aa439917cae66ed045deda5a.png@942w_347h_progressive.webp)

###### 2选中物体，在【物体属性-可见性】选项中勾选阴影捕捉

![img](https://i0.hdslb.com/bfs/article/7a1d1118a257c6ccf833990efdcc1e48b383d579.png@942w_1095h_progressive.webp)

#### 方法三

针对cycles 物体属性 - 可见性 - 射线可见性 根据情况取消勾选,只要阴影就只勾阴影
eevee时(适用cycles)只要阴影如图

![img](https://tiebapic.baidu.com/forum/pic/item/68d7d7f9d72a60590fc34fce6d34349b013bba6f.jpg?tbpicau=2023-06-21-05_d4ebddddbfb97c087b3f8c187528899a)

#### 实践方法

1.设置渲染属性——渲染引擎选Cycles，胶片选项选【透明】,勾上【透明玻璃】

![](F:\Git\presonalnote\Blender\picture\渲染属性设置1.jpg)

2.设置地面的【物体属性】——【可见性】——【遮罩】——勾选【阴影捕捉】

![](F:\Git\presonalnote\Blender\picture\渲染属性地面设置.jpg)

#### 沿着曲线做模型阵列

> 阵列修改器，固定数量，调节数量
>
> 曲线修改器，调节曲线的方向，法向，原点位置等，确保阵列起点
>
> 调整阵列模型的【旋转】与【位置】，确定阵列效果符合要求

![](F:\Git\presonalnote\Blender\picture\沿着曲线阵列.jpg)

