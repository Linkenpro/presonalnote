Diffuse Map——反射贴图（颜色贴图）

- 高分辨率（2K或以上）
- 无缝贴图



PS制作无缝贴图

1.素材图，调整画板大小

![](F:\Git\presonalnote\Texture\png\调整画板.jpg)

2.复制4份素材，并绘制中间参考线

![](F:\Git\presonalnote\Texture\png\做参考线.jpg)

3.使用修复画笔工具，快捷键`]`对中间部分进行修复，然后Ctrl+J获取中间部分，导出为PNG图，此为Color贴图，即为Diffuse贴图

4.制作法向贴图，滤镜>>>3D>>>生成法线图

![](F:\Git\presonalnote\Texture\png\滤镜3D生成法向贴图0.jpg)

5.如下参数设置，模糊为0，细节缩放100%，低中高均为100%

![](F:\Git\presonalnote\Texture\png\生成法向图参数设置.jpg)

6.点击确认即可导出生成的法线贴图

7.制作凹凸贴图——Bump，复制一层，在图像>>>调整>>>色相/饱和度（`Ctrl+U`）

![](F:\Git\presonalnote\Texture\png\色相饱和度.jpg)

8.参数设置如下，将饱和度将为0，确认

![](F:\Git\presonalnote\Texture\png\凹凸贴图1.jpg)

9.选中更改后的图层，Ctrl+I，将颜色反转，得到Bump凹凸贴图。

![](F:\Git\presonalnote\Texture\png\凹凸贴图，反转颜色.jpg)

10.制作Height高度贴图，Ctrl+U打开色相/饱和度面板，将饱和度将为0，明度拉高，完成高度图并可导出

![](F:\Git\presonalnote\Texture\png\高度贴图，明度调整未知.jpg)

11制作粗糙度贴图，复制上方高度图的图层，Ctrl+L调整滑块如下，得到粗糙度贴图，并导出。

![](F:\Git\presonalnote\Texture\png\粗糙度贴图.jpg)