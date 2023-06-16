#### 渲染引擎

渲染是将三维场景转换为二维图像的过程。Blender内置三个各具优势的渲染引擎:

- Eevee 是基于物理的实时渲染器。

- Cycles 是基于物理的光线追踪渲染器。

- 工作台 专为布局，建模和预览而设计的。

使用插件可以添加更多第三方渲染引擎。每个渲染器都有自己的渲染设置来控制渲染质量和性能。

#### Eevee

Eevee是blender的实时渲染引擎，应用 OpenGL 技术来实现，专注于速度和交互性，同时实现了渲染 PBR 材质的目标。Eevee可以在3D视口交互使用，也可以生成高质量的渲染效果。

Eevee并不是光线跟踪引擎。它使用的是通过光栅化的多种算法来估算光线与物体材质作用的方式，并不像cycles基于物理光线跟踪来计算每个光线的反弹。

尽管Eevee在设计上使用 PBR 的着色材质，但它并不完善，并且Cycles渲染器提供物理上更加精确的渲染，因为Eevee使用光栅化渲染所以有很大的限制 。

##### 采样

![](F:\Git\presonalnote\Blender\picture\image-20230415111514258.png)

###### 渲染

在最终渲染中使用的样本数

###### 视图

在3D视图中使用的样本数。当设置样本数为零时，3D视图中将会不断采样。

### Cycles 渲染器，使用GPU渲染

> Preferences  >>  System  >>  Cycles Render Devices，选择*CUDA*、*OptiX*、*HIP*或*Metal*，oneAPI
>
> 场景渲染引擎+GPU计算
>
> 

在

##### 渲染技术支持

###### CUDA——NVDIA显卡

###### OptiX——NVDIA显卡

###### HIP——AMD显卡

###### Metal——苹果（macOS）

###### OneAPI——英特尔显卡

> 利用 oneAPI 并让英特尔 GPU 用于在 Cycles 中进行渲染



#### 渲染灯光

- 点光

- 日光

- 聚光灯

> 可做舞台灯光
![](F:\Git\presonalnote\Blender\picture\渲染舞台灯光.jpg)

- 面光——可设置ies光
