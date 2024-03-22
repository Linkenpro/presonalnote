###### 主要参数

|        参数         | 说明                                                         |
| :-----------------: | :----------------------------------------------------------- |
|        `-i`         | 设置输入文件名                                               |
|        `-f`         | 设置输出格式                                                 |
|        `-y`         | 若输出文件已存在，则覆盖文件                                 |
|        `-fs`        | 超过指定的文件大小，则结束转换                               |
|        `-t`         | 指定输出文件的持续时间，以秒为单位                           |
|        `-ss`        | 从指定时间开始转换，以秒为单位                               |
| `-ss`和`-t`一起使用 | 代表从`-ss`的时间开始转换持续时间为`-t`的视频，例如：`-ss 00:00:01.00 -t 00:00:10.00`即从`00:00:01.00`开始转换到`00:00:11.00` |
|      `-title`       | 设置标题                                                     |
|    `-timestamp`     | 设置时间戳                                                   |
|      `-vsync`       | 增减Frame使影音同步                                          |
|        `-c`         | 指定输出文件的编码                                           |
|     `-metadata`     | 更改输出文件的元数据                                         |
|       `-help`       | 查看帮助信息                                                 |

###### 视频参数

| 参数              | 说明                                                         |
| ----------------- | ------------------------------------------------------------ |
| `-b:v`            | 设置影像流量，默认为`200Kbit/s`                              |
| `-r`              | 设置帧率值，默认为25                                         |
| `-s`              | 设置画面的宽与高                                             |
| `-aspect`         | 设置画面的比例                                               |
| `-vn`             | 不处理影像，于仅针对声音做处理时使用                         |
| `-vcodec( -c:v )` | 设置影像编解码器，未设置时则使用与输入文件相同之编解码器（手动指定编码器） |

将输出文件的视频比特率设置为`64 kbit/s`

```
ffmpeg -i input.avi -b:v 64k -bufsize 64k output.avi

ffmpeg -i 输入文件 -b:v 比特率 输出文件
```

要将输出文件的帧速率强制为 24 fps：

```
ffmpeg -i input.avi -r 24 output.avi
```

###### 

###### 音频参数

| 参数 | 说明 |
| ---- | ---- |
|      |      |
|      |      |
|      |      |

##### 具体案例

###### `mp4`转 `mov`格式

```
ffmpeg -i input_file.mp4 -acodec copy -vcodec copy -f mov output_file.mov
```

###### `mov`转`mp4`格式

测试1

```
ffmpeg -i  old.mov -vcodec libx264 -s 960x540 -preset fast -crf 22 -y -acodec copy new.mp4
```

测试2(成功)

```
ffmpeg -i input.mov ouput.mp4
```

提取视频缩略图

```
ffmpeg -i input.mp4 -vf "fps=1/10,scale=-2:720" thumbnail-%03d.jpg
```

编码压缩视频

```
ffmpeg -i input.mp4 -c:v libx264 -preset xxxx -crf output.mp4

# —preset 预设值
ultrafast
superfast
veryfast
faster
fast
medium
slow
slower
veryslow

# -crf 控制图像质量 0（无损）-51（最差质量）
# 最常用到 19-28
```

##### 过滤器

```
ffmpeg -i input.mp4 -vf "scale=1280:720,transpose=1" output.mp4

# -vf 指定过滤器

# scale 缩放视频的长宽比
# scale=1280:720 or scale=1280:-1 自动计算

# 旋转视频 transpose

```

###### 查看可用设备的清单

```
ffmpeg -list_devices true -f dshow -i dummy
```

###### 简单合并音频+视频

```
ffmpeg -i 00.mp4 -i 00.mp3 -vcodec copy -acodec copy output.mp4
```

##### 压缩视频到指定大小

```
将视频压缩指定大小

ffmpeg  -i  Desktop/input.mp4  -fs 10MB  Desktop/output.mp4

-fs 10 : 表示文件大小最大值为10MB

——测试
好像参数达到某个极限后无法再继续压缩

```

#### 压缩图片大小

```
ffmpeg -i wfypfa3ha_2K_Albedo.jpg -vf "scale=1024:1024" wfypfa3ha_1K_Albedo.jpg

ffmpeg -i wfypfa3ha_2K_Translucency.jpg -vf "scale=1024:1024" wfypfa3ha_1K_Translucency.jpg
```

