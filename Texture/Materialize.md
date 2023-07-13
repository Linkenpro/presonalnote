1.Materialize软件安装

> 在官网下载软件包，解压即可。https://boundingboxsoftware.com/materialize/getkey.php
>
> 需要安装微软VIsual C++,网址：https://www.microsoft.com/en-us/download/details.aspx?id=40784

2.解压的路径不能有中文？但是置入的文件名不能是带有中文名字，否则识别不了文件

![](F:\Git\presonalnote\Texture\png\置入图片.jpg)

3.在Height Map中点击Create，制作高度贴图。

![](F:\Git\presonalnote\Texture\png\调整对比度图.jpg)

> 调整参数，对比度Final Contrast，调高参数，至细节展现。
>
> 确认效果后，点击Set as Height Map

4.制作高度贴图后，Normal Map的Create按钮也可点击了。

![](F:\Git\presonalnote\Texture\png\法线贴图.jpg)

> 取消Shape from Diffuse（Unchecked from Height）——将使用高度贴图创建法向贴图
>
> 调节Angularity Amount，稍微调节即可
>
> 确认效果后，点击Set as Normal Map

5.点击Metallic Map的Create按钮，创建金属度贴图。

![](F:\Git\presonalnote\Texture\png\金属度贴图.jpg)

> 创建的金属度贴图，它基于高度贴图？
>
> 金属度贴图显示的黑色表示光滑亮的，白色表示哑光的——黑色表示是金属，白色则不是金属
>
> 木板不是金属，稍微调整即可
>
> 完成效果调整后，点击Set as Matallic

6.点击Smoothness Map的Create按钮，调出面板

![](F:\Git\presonalnote\Texture\png\光滑度或粗糙度贴图.jpg)

> 光滑度贴图，基本上是粗糙度贴图（PBR材质贴图工作流）
>
> 目前的显示方式与我们想要的相反——白色的地方哑光更哑光，
>
> 调整Final Contrast，稍微调整
>
> 调整High Pass Overlay，高通叠加
>
> 调整High Pass Blur Size，调整模糊大小
>
> 调整Sample Blur Size，调整模糊样本
>
> 调整Base Smoothness，调整基础光泽度
>
> 点击Set as Smoothness，获得光滑度贴图

7.AO Map的Create按钮，

![](F:\Git\presonalnote\Texture\png\AO贴图.jpg)

> 调整Pixel Depth
>
> 调整AO Power