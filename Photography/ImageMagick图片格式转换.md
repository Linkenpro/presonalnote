###### 图片转换ImageMagick

```cmd
magick input.avif output.jpg
```

> ImageMagick 包括一组命令行工具来操作图片，安装好 ImageMagick 后，终端就可以使用如下命令了。
>

magick: 创建、编辑图像，转换图像格式，以及调整图像大小、模糊、裁切、除去杂点、抖动 ( dither )、绘图、翻转、合并、重新采样等。

convert: 等同于 magick 命令。

identify: 输出一个或多个图像文件的格式和特征信息，如分辨率、大小、尺寸、色彩空间等。

mogrify: 与 magick 功能一样，不过不需要指定输出文件，自动覆盖原始图像文件。

composite: 将一个图片或多个图片组合成新图片。

montage: 组合多个独立的图像来创建合成图像。每个图像都可以用边框，透明度等特性进行装饰。

compare: 从数学和视觉角度比较源图像与重建图像之间的差异。

display: 在任何 X server 上显示一个图像或图像序列。

animate: 在任何 X server 上显示图像序列。

import: 保存 X server 上的任何可见窗口并把它作为图像文件输出。可以捕捉单个窗口，整个屏幕或屏幕的任意矩形部分。

conjure: 解释并执行 MSL ( Magick Scripting Language ) 写的脚本。

stream: 一个轻量级工具，用于将图像或部分图像的一个或多个像素组件流式传输到存储设备。在处理大图像或原始像素组件时很有用。

