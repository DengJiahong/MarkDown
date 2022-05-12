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
  - 通过测量辐射量（计算遥感反射率）估计浊度
- 基于反射率的测量的优点是与其他遥感平台常规进行的测量具有直接的可比性，特别是卫星遥感测量。HydroColor 可以通过提供可比较的地面测量来补充这些测量。

## 2. Materials and Methods

- HydroColor 应用程序需要 现代智能手机、18%反射率的灰卡（可使用其他已知反射率的表面代替）、光学深水。
- 现代智能手机标准配置的作用：
  - 数码彩色相机：感知环境，收集图像
  - 指南针、陀螺仪：为拍摄图像找到正确位置和角度
  - GPS、数据通信：自动获取经纬度，用于确定太阳位置以确定角度进行图像采集

### 2.1. Image Capture

图像采集方法与计算水上遥感反射率的公式有很大关系：

$$\displaystyle R_{rs} = \frac{L_t- \rho L_s}{\frac{\pi}{R_{ref}}\cdot L_c} \tag{1}\ \ \ \ (1)$$

其中，$L_t$ 是来自水面的辐射率，$L_s$ 是天空辐射率，$R_{ref}$ 是反射率标准的辐照度反射率（0.18，对应此处使用的18% 灰卡），$L_c$ 是反射率标准表面的辐射率，$\rho$ 是海面反射系数（本研究中固定为 0.028）。

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

- 受限于普通智能手机相机的标准应用程序API，HydroColor 处理的是压缩后的图像并非原始图像。但是，图像压缩并不会对光辐射测量造成很大影响（图 2）。

- HydroColor 使用以下公式测量相对光辐射：

  $$\displaystyle L_{rel} = \frac{DN}{\alpha \cdot S} \tag{2}\ \ \ \ (2)$$

  其中，$DN$ 是红色、绿色或蓝色通道的像素值（0 - 255），$\alpha$ 是曝光时间，$S$ 是 ISO 速度。该式分别应用于每个 RGB 通道以确定三个通道中每个通道的相对辐射度。

  ![image-20220505141457235](C:\Users\86134\AppData\Roaming\Typora\typora-user-images\image-20220505141457235.png)

<center>Fig 2. - Camera response as a function of radiance. Measurements were made by gradually attenuating a white light source while collecting images with an Apple iPod touch.Relative radiancewas calculated using Equation (2). The true radiance was measured using a Satlantic HyperPro radiometer. The response in the: red (a) ; green (b); and blue (c) color channels are shown. This figure is meant to show the linear relationship between the camera's measure of relative radiance and the true radiance; it is not meant to provide an absolute calibration for measuring radiance.</center>

- 要比较来自不同设备的 HydroColor 测量值，设备之间的 RGB 通道的光谱灵敏度必须相似。使用特定程序在智能手机上记录数字像素值，使用 20 nm 运行平均值对生成的像素值进行平滑处理，然后通过每个通道中的最大记录值进行归一化。

### 2.3. Calculation of Remote Sensing Reflectance

- 为了减少测量的不确定性，对图像中心 200 x 200 像素区域的 RGB 像素值进行平均。
- 使用这些平均值和公式（2）计算相对辐射度。
- 使用相对辐射度和公式（1）计算遥感反射率。
- 公式（1）已表明相机无需绝对校准。实际辐射度与相机的相对辐射度测量值之间的比例可能会随着镜头的清洁度、使用年限、温度和设备制造商而改变。但是，由于这三幅图像都是在短时间内（通常不到一分钟）使用同一设备拍摄的，因此这些误差在公式（1）的计算中被抵消了。

### 2.4. Measuring SPM from Remote Sensing Reflectance

- SPM （悬浮颗粒物）对反射率有直接影响。
- **红色**通道反射率主要受 SPM 浓度（通过散射）控制。
- 在 HydroColor $R_{rs}$ 红色通道中可以检测到与 SPM 浓度增加相关的反射率变化。

### 2.5. Field Tests

通过三个活动收集实地数据：

	1. 将 HydroColor 测量结果与精密辐射计和浊度计进行比较
	2. HydroColor 测量结果收集
	3. 对来自 Android 和 Apple 设备的 HydroColor 测量结果的简要比较

**将 HydroColor 测量结果与精密辐射计和浊度计进行比较：**

- 在三个地点，一定环境条件和设备条件下测量比较。
- HydroColor 的数据和辐射计、浊度计同时收集。
- HydroColor 和标准辐射计WISP使用相同方法测量计算$R_{rs}$ ，并作比较。
- 需使用图 3 中的光谱灵敏度曲线作为权重对 WISP 光谱进行平均，然后与HydroColor 测量结果进行比较：

$$\displaystyle R_{rs}(i) = \frac{\int_{400}^{700}R_{rs}(\lambda)w_i(\lambda)d\lambda}{\int_{400}^{700}w_i(\lambda)d\lambda} \tag{3} \ \ \ (3)$$

其中，$R_{rs}(\lambda)$ 是WISP 在波长$\lambda$ 处测量的$R_{rs}$值，$w_i(\lambda)$ 是在波长 $\lambda$ 处颜色通道 $i$ 的相对相机灵敏度（来自图 3），$R_{rs}(i)$ 是若WISP与颜色通道 $i$ 具有相同光谱灵敏度得到的结果。

- 使用比浊法浊度单位 (NTU) 测量的浊度作为 SPM 浓度的代表。

**HydroColor 测量结果收集:**

- 旧金山湾国家河口研究保护区成员于 2014 年 7 月 24 日组织志愿者收集 HydroColor 测量值和水样。通过过滤和重量分析测量收集的水样的 SPM 浓度。
- 展示了 HydroColor 作为大众科学工具的潜力。

**对来自 Android 和 Apple 设备的 HydroColor 测量结果的简要比较：**

- 所有测量都使用同一张灰卡。比较每个设备测量的反射率和浊度值。

![image-20220505210600352](C:\Users\86134\AppData\Roaming\Typora\typora-user-images\image-20220505210600352.png)

<center>Fig 3. - Spectral sensitivity curves for a variety of smartphone cameras.The red, green, and blue curves correspond to the red, green, or blue color channels of the camera. Each curve was smoothed using a 20 nm moving average, and then normalized by the highest recorded value.
</center>

## 3. Results

### 3.1. Camera Spectral Sensitivity

- 各设备的光谱灵敏度曲线如图3所示。
- 绿色通道中 490 nm 附近的峰值似乎是一个伪影。可能是由绿色和蓝色像素之间的串扰引起的。
- 除了绿色曲线中的伪影外，所有六个相机之间的光谱响应非常相似。重要结论：我们可以假设光谱灵敏度与设备无关。

### 3.2. Validation of Reflectance Measurement

- 使用最小二乘线性回归拟合 WISP 和 HydroColor 测量的$R_{rs}$，结果显示，二者的测量结果十分接近（图 4 ）
- 异常数据可能来源于测量过程中光照和天空条件发生的变化

![image-20220505215855373](C:\Users\86134\AppData\Roaming\Typora\typora-user-images\image-20220505215855373.png)

<center>Fig 4. - Comparison of HydroColor Rrs with WISP Rrs. The three plots show the Rrs comparison for each color channel. To show a meaningful comparison, the WISP spectra were averaged using the camera spectral sensitivity curves as weights Equation (3). For replicate measurements, error bars display the standard error. The dashed line shows the one-to-one line and the solid line shows the results of a type-l linear regression. The data are broken out by location: Columbia River (blue triangles), Georgia (green circles), Maine (red squares). The data points in boxes were identified as outliers (using an objective procedure) and were not included in the regression.
</center>

- 进一步研究测量的准确性，比较 WISP 和 HydroColor 测量的公式（1）中各量（$E_d, L_s, L_t$），如图5：

![image-20220505222039269](C:\Users\86134\AppData\Roaming\Typora\typora-user-images\image-20220505222039269.png)

<center>Fig 5. - Comparison of HydroColor and WISP measurements of Ed,Ls, and Lt. This figure shows data from the: red (a-c); green (d-f); and blue(g-i) color channels of the camera. Statistics are listed in Table 2. The data are broken down by device: iPod (green circles), iPhone 4 (red squares), and iPhone 5(blue diamonds).
</center>

- $E_d$ 测量值变化更大的原因：
  - 灰卡总是放置在相对于相机较低的区域，可能会导致拍摄图像的人遮住部分天空。而WISP 辐照度传感器通常位于视线水平。
  - 灰卡反射率的变化（灰卡使用时间、长期日晒对灰卡的影响）

- 使用多个 Apple 和 Android 设备收集的数据进行比较，每个研究地点的每个设备测量的反射率和浊度如 图6 所示。

![image-20220505225353754](C:\Users\86134\AppData\Roaming\Typora\typora-user-images\image-20220505225353754.png)

<center>Fig 6. - Comparison of the measured reflectance and turbidity from several smartphones at the same study sites. Bars show the mean of three measurements. Error bars show the standard deviation. No error bars present indicates the standard deviation between replicates was zero.
</center>

- 结果表明：所测试的六个设备之间的反射率和浊度只有很小的变化。没有一个设备显示出大于 HydroColor 测量不确定性的一致偏差。

### 3.3. Validation of Turbidity Measurement

- 浊度和 HydroColor测量的红色通道中的 $R_{rs}$ 关系如图 7 ，二者的转化关系：$turbitity = 22.57R_{rs}(Red) / (0.044 - R_{rs}(Red)) $

![image-20220506093848357](C:\Users\86134\AppData\Roaming\Typora\typora-user-images\image-20220506093848357.png)

<center>Fig 7. - Relationship between turbidity and HydroColor Rrs(Red). The plot on the right is a close r view of the lower turbidity values in the left plot. Error bars display the standard error (when replicate measurements were available).The single boxed data point identifies an outlier that was not included in the fitting of the radiance model or regression line. The solid lines and dash lines show the fitted relationships described in the validation section. The radiance model and regression line are on top of each another in the right plot. For the solid line R2 =0.93 and RMSE = 0.003 sr-1.
</center>

- 中值百分比误差为24%，与其他测量浊度的方法相比，该测量准确度已足够有效。

### 3.4. Validation of Citizen Collected Data

- 通过图 7 展示的关系，志愿者收集的浊度通过 $R_{rs}$ (Red) 计算得来。收集的水样的 SPM 与 HydroColor 报告的浊度关系如图 8 ：

![image-20220506100059671](C:\Users\86134\AppData\Roaming\Typora\typora-user-images\image-20220506100059671.png)

<center>Fig 8. - Comparison of volunteer collected HydroColor measurements and SPM in San Francisco Bay. SPM was derived from volunteer collected water samples. Red line and embedded statistics show a type-Il linear regression.
</center>

- 误差来源：
  - 测量方法导致的误差
  - 海湾不同位置沉积物的吸收或散射特性的差异
- 尽管测量的浊度和 SPM 的相关性不是特别强，结果仍表明，大众科学能使用 HydroColor 观测环境。

## 4. Discussion

- 本研究展示了如何将数码相机用作水生遥感设备。
- 本研究利用 HydroColor 测量的$R_{rs}$ 值估计浊度，用户可能根据$R_{rs}$ 开发自己的算法，估计其他环境测量值。
- HydroColor 准确测量反射率的能力取决于环境条件。HydroColor 没有考虑有关风速和海况的信息。本研究的测量是在环境平静条件下进行 （如：完全晴朗或稳定阴天的情况），$\rho$ 值固定为 0.028。
- 一些可能的改进（对应用程序的重大改进将是对不确定性的更好估计）：
  - 检查图像或一系列图像中的可变性可以提供有关气象条件（云量，水面粗糙程度）的更多信息，这可用于在条件不适合 HydroColor 测量时提醒用户。
  - 使海面反射系数 ($\rho$) 动态化，该值可以根据图像处理结果或通过手机数据连接收集的天气数据进行调整。
  - 使用原始相机数据而不是压缩数据，这将提高 HydroColor 测量相对辐射度的能力。
  - 使用固定区域而不是固定数量的像素，这有助于确保相机的视野在设备之间是相同的。
- HydroColor 有可能对科学和教育界产生巨大影响：
  - 为大众科学提供简单且低成本的测量水质数据的工具。
  - 与其他水质测量工具结合使用，相互补充。
  - 测量工具和方法在全球范围内实现标准化，因为全球智能手机硬件配置相似，若正确使用 HydroColor，测量方法将具有高度的一致性。
  - 许多学生拥有智能手机，HydroColor 非常适合作为环境监测、海洋学、湖泊学等课程的教学工具。

