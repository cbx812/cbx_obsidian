---
tags: 流变学 
aliases: Cox-Merz 定律
---
流变学中所说的，不加限定和修饰的黏度，一般指样品的剪切黏度。剪切黏度需要在流变仪的稳态模式中进行测量。而在动态模式中获得的黏度，是样品的复数黏度 (complex viscosity)，一般需要特别说明。

复数黏度的计算公式来自样品的模量：  

$$
\left.\eta^{*}=\frac{G^{*}}{\omega}=\left[\left(\frac{G^{\prime}}{\omega}\right)^{2}+\left(\frac{G^{\prime \prime}}{\omega}\right)^{2}\right)\right]^{\frac{1}{2}}
$$


复数黏度与剪切黏度在一定的条件下可通过经验公式 Cox-Merz 定律进行互换。Cox-Merz 定律被定义为：

$$
\eta (\dot{\gamma })=\eta^* (\omega)
$$


该定律的来源是 Cox 与 Merz 在 1958 年发表在 Journal of Polymer Science 的文章：“Correlation of Dynamic and Steady Flow Viscosities”。在原文中，作者对两个聚苯乙烯样品进行了表征。作者采用自制的同心圆筒流变仪 ("elastoviscometer") 测量了样品的复数黏度，并采用毛细管流变仪测量了样品的表观黏度。作者发现两种方式得到了类似的黏度("similarity")。将测得得到的$\eta (\dot{\gamma })$和$\eta^* (\omega)$数据放入同一个双对数坐标系内，作者发现这些数据点可以连为一条连续光滑的曲线("smooth continuation")。

通过动态剪切试验代替稳态剪切试验，可以拓宽可获得的剪切速率范围。在动态剪切中，我们可以在避免相变的前提下，通过时间-温度叠加多个温度下的频率扫描数据，得到样品跨越 6~8 个数量级频率的黏弹性数据。即使不进行时温叠加，我们也可以在短时间内获得 628 ~ 0.00628 rad/s (100 ~ 0.001 Hz) 的频率扫描数据。而即便是 628 rad/s 所对应的剪切速率，也远远超过了稳态模式下可获得的剪切速率上限。

在稳态测量中，由于聚合物熔体的黏度较大，在剪切速率超过一定范围后（0.1~10 ，取决于分子量），会出现熔体破裂现象 (melt fracture，图 1)。在这一过程中样品从线速度最大的边缘位置开始，从测量间隙中被挤出。缺少样品的测量间隙内出现空隙，导致流变仪测得的扭矩偏低并汇报响应偏低的黏度结果（图 2）。而在动态测试中，流变仪始终保持小振幅剪切进行往复运动，在整数个周期后总应变为 0，可避免由于持续旋转造成的测量误差。同时动态测试的非线性程度可以通过[傅里叶转变流变](http://mp.weixin.qq.com/s?__biz=MzUxMjAwNzgyMQ==&mid=2247483758&idx=1&sn=1c03f3b7d1679eca89864467cae4ecec&chksm=f96a4a8cce1dc39a2663f2b2a6ad13544e0b26d552c75b7e22738fdcc165fb089781b1945cd9&scene=21#wechat_redirect)进行监测，而在稳态条件下这是难以量化的。

![](https://mmbiz.qpic.cn/mmbiz_png/NvBLgXv0icYZLicWXwOLavBH6QmYndicszhdEyagPbMEkoYiaviah0cFDFFjx5KCkSJ4GjJIAY4H5jLd4x2VtS6QGLA/640?wx_fmt=png "图 1：熔体破裂会导致样品在高剪切速率下离开测量间隙，造成测量结果不准确。")

![](https://mmbiz.qpic.cn/mmbiz_png/NvBLgXv0icYYsLxqRliciaSZgQticUpBJIUQOEiaKVnf4icbyVTBZ3uicNtPcRuobKNBygZpICVqm3XUJx0DuQcY3xDfQ/640?wx_fmt=png "图 2：相对于准确的复数黏度数据，剪切黏度在速率超过 2 后受到熔体破裂的影响，出现了错误的下降。第一牛顿区内两次测量结果重合，Cox-Merz 定律对该样品是有效的。测量系统为 25mm 直径平行板，样品为 LLDPE。  ")

至此，我们讨论了 Cox-Merz Rule 的背景与该公式在聚合物熔体上的典型应用。Cox-Merz Rule 的理论背景仅经过非常有限的验证，一般仅对未填充、无交联、线性聚合物的熔体以及聚合物的中、高浓度溶液有效。如果不加区分的将 Cox-Merz Rule 用于分析含有填料的聚合物，或含有固体颗粒的悬浮液，可能导致黏度值在报道上有偏差。

![](https://mmbiz.qpic.cn/mmbiz_png/NvBLgXv0icYZLicWXwOLavBH6QmYndicszhp4dMhsk5KF7nD4GWOwKRS3eZm4l0U7Nj2NLyyvqiaWFyJmqNwfvKNdg/640?wx_fmt=png "")

图 3：涂料样品的的剪切黏度与复数黏度差别较大（超过一个数量级）。样品作为典型的分散体系不能简单套用 Cox-Merz 公式。

涂料中含有助剂，使得该样品在低剪切区未出现平台。这一点可以通过样品的频率扫描得到验证：样品的损耗因子随频率降低逐渐降低并趋于稳定。

![](https://mmbiz.qpic.cn/mmbiz_png/NvBLgXv0icYZLicWXwOLavBH6QmYndicszhiaGrceu15IQqRRWNOsUvQJXpuQD510fKkKvqtH4po6D14KibHwYHgldQ/640?wx_fmt=png "")

图 4：涂料样品的频率扫描数据。样品在低频区储能模量占主导，损耗因子 。

这些流变助剂通过在分散体系内部形成缔合网络，帮助涂料获得低剪切下抗流挂；而高剪切下这些可逆的缔合网络被破坏，促进涂料的加工与流平。在稳态剪切过程中，总应变不断上升，缔合网络能够如同在使用过程中一样被临时破坏；而在小振幅动态剪切中，样品处于线性黏弹区内，缔合网络始终被维持。这种条件下，Cox-Merz 定律就失效了。

因此，在使用 Cox-Merz 转换时，需要客观认识到剪切黏度与复数黏度的区别。若受到到客观条件限制，必须通过复数黏度解决实际工艺问题，则有必要对剪切黏度与复数黏度的差别进行定量。

附：

Cox, W.P. and Merz, E.H. (1958), Correlation of dynamic and steady flow viscosities. J. Polym. Sci., 28: 619-622. 

doi:10.1002/pol.1958.1202811812

[https://mp.weixin.qq.com/s/cwuqYzzGkpT79IXu00zeJg](https://mp.weixin.qq.com/s/cwuqYzzGkpT79IXu00zeJg)