# The HydroColor App

## Abstract

HydroColor 是一款移动应用程序，它利用智能手机的摄像头和辅助传感器来测量天然水体的遥感反射率。 HydroColor 使用智能手机的数码相机作为三波段辐射计。应用程序指示用户收集一系列三张图像。这些图像用于计算红色、绿色和蓝色宽波段的遥感反射率。与卫星测量一样，反射率可以反演来估计水中吸收和散射物质的浓度，这些物质主要由悬浮沉积物、叶绿素和溶解的有机物组成。本出版物介绍了测量方法，并研究了 HydroColor 的反射率和浊度估计值与商业仪器相比的精度。结果表明，HydroColor 可以将遥感反射率测量到精密辐射计的26% 以内，浊度测量在便携式浊度计的 24% 以内。 HydroColor 与其他水质相机方法的区别在于其操作基于辐射测量而不是图像颜色。 HydroColor 是少数使用智能手机作为完全客观传感器的移动应用程序之一，这与使用人眼的主观用户观察或颜色匹配相反。这使得 HydroColor 成为众包水生光学数据的强大工具。

## 1. Introduction

- 在海洋学和湖泊学界，使用大众科学作为数据收集方法还未确立。原因是：
  - 缺乏强大且便携易用的工具
  - 低成本工具需要大量初始时间投入（例如，建造防水外壳、建造 Secchi 盘、焊接电气元件等）
- 本文成果 HydroColor 应用程序使用智能手机数码相机作为三波段辐射计，在一系列三幅图像中测量的光强度用于计算相机红、绿和蓝色通道中的遥感反射率，进而估计水的浊度。
- HydroColor 的特点：
  - 使用成本低
  - 易用且测量结果精度高
  - 通过测量辐射量（遥感反射率）估计浊度
- 基于反射率的测量的优点是与其他遥感平台常规进行的测量具有直接的可比性，特别是卫星遥感测量。HydroColor 可以通过提供可比较的地面测量来补充这些测量。

## 2. Materials and Methods

- HydroColor 应用程序需要 现代智能手机、18%反射率的灰卡（可使用其他已知反射率的表面代替）、光学深水。
- 现代智能手机标准配置的作用：
  - 数码彩色相机：感知环境，收集图像
  - 指南针、陀螺仪：为拍摄图像找到正确位置和角度
  - GPS、数据通信：自动获取经纬度，用于确定太阳位置以确定角度进行图像采集

### 2.1. Image Capture

图像采集方法与计算水上遥感反射率的公式有很大关系：

$$\displaystyle R_{rs} = \frac{L_t- \rho L_s}{\frac{\pi}{R_{ref}}\cdot L_c}$$

其中，$L_t$ 是来自水面的辐射率，$L_s$ 是天空辐射率，$R_{ref}$ 是反射率标准的辐照度反射率（0.18，对应此处使用的18% 灰卡），$L_c$ 是反射率标准表面的辐射率，$\rho$ 是海面反射系数。

- HydroColor 能够在无需校准相机来测量辐射度的情况下测量遥感反射率的关键: 任何比例因子或乘法误差都会在该式中抵消。
- ρ 的值是使用 HydroLight 确定的，具体值随环境条件（天空条件）和观察角度（视角）而变化
- 所以我们必须获得三个图像：
  - 一张灰卡的图像来确定反射率标准的辐射率（$L_c$）
  - 一张天空的图像来确定天空辐射率（$L_s$）
  - 一张水的图像来确定来自水面的辐射率（$L_t$）
- 避免捕获被船、码头或任何其他结构遮蔽的水或灰卡图像

![](C:\Users\86134\AppData\Roaming\Typora\typora-user-images\image-20220504215659506.png)

<center>Fig 1. - Example of three images collected with HydroColor and the optical features captured in each image. The gray card image is captured at 40° from nadir and 135° from the sun. The sky image is captured at 130° from nadir and 135° degrees from the plane of the sun. The water image is captured at 40° from nadir and 135° degrees from the plane of the sun.</center>

- 拍摄角度由现代智能手机配置中的 GPS、指南针、陀螺仪等辅助确定。

### 2.2. Extracting Radiance from Images

- 受限于普通智能手机相机的标准应用程序API，HydroColor 处理的是压缩后的图像并非原始图像。但是，图像压缩并不会对光辐射测量造成很大影响。
- HydroColor 

### 2.3. Calculation of Remote Sensing Reflectance



### 2.4. Measuring SPM from Remote Sensing Reflectance



### 2.5. Field Tests



## 3. Results



### 3.1. Camera Spectral Sensitivity



### 3.2. Validation of Reflectance Measurement



### 3.3. Validation of Turbidity Measurement



### 3.4. Validation of Citizen Collected Data



## 4. Discussion



