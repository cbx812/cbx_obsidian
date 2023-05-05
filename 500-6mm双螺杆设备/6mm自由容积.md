---
title: 6mm自由容积
chapter:
tags: 
 - 螺杆
 - 双螺杆
 - 6mm双螺杆
 - 6mm双螺杆参数计算
aliases:
 - 6mm双螺杆自由容积
 - 自由容积参数计算
center: false
width: 827
height: 1170
---

## 单螺杆

<img src="https://i0.hdslb.com/bfs/album/c38182727a78065d08f6d9670579b10b9379a381.png" style="zoom:60%;" />

从进料口最左端到料筒端距离为$58.5 mm$，料筒直径为$6.5mm$，假设充满状态下容积为
$$
V_{料筒}= \pi \times (\frac{6.5}{2})^2 \times 58.5 = 1941.21 mm^3=1.94 cm^3
$$

<img src="https://i0.hdslb.com/bfs/album/273385cfd6684b9f9108e2e5ded7afd469648770.png" style="zoom:60%;" />

螺杆体积$V_{单螺杆}=901.549 mm^3=0.90 cm^3$




---

## 双螺杆

<img src="https://obsidian0915.oss-cn-chengdu.aliyuncs.com/img/202206121834820.svg" style="zoom:50%;" />

通过Solidworks软件确定截面面积$58.29mm^2$

<img src="https://i0.hdslb.com/bfs/album/72bb98c9c1d23bf407f6a3669a802718ad7eb46d.png" style="zoom:50%;" />

通过几何计算确定截面面积

<img src="https://obsidian0915.oss-cn-chengdu.aliyuncs.com/img/202206122100574.svg" style="zoom:50%;" />

$$
OO' =5.75mm
$$

$$
l_{AB}=\sqrt{(l_{OA})^2-(l_{OB})^2} =\sqrt{3.05^2-(\frac{5.75}{2})^2}=1.02mm
$$

$$
\theta = \arccos \frac{\frac{l_{OO'}}{2}}{l_{OA}}=\arccos \frac{\frac{5.75}{2}}{3.05}= 19.5^{\circ}
$$

$$
S_{\triangle AOC}= \frac{AC \cdot OB}{2} = \frac{2.875 \times 2.02 }{2} = 2.90 mm^2
$$

$$
S_{\overset{\LARGE{\frown}}{AOC}}= \frac{n \pi R^2}{360} = \frac{2 \times 19.5^{\circ} \times \pi \times 3.05^2}{360^{\circ}}=3.17mm^2
$$

$$
S_{\overset{\LARGE{\frown}}{ABC}}=S_{\overset{\LARGE{\frown}}{AOC}}-S_{\triangle AOC}=0.24mm^2
$$


$$
S=2 \cdot (S_O-S_{\overset{\LARGE{\frown}}{ABC}})=2 (\pi \times (\frac{6.1}{2})^2-0.24)=57.97 mm^2
$$

与sw计算误差主要存在两个圆相邻的所做圆角
从液体进料端开始，到底端距离为$87.5mm^2$
![](https://i0.hdslb.com/bfs/album/eba54f588adbb62c865096a32405c00b2d1ba78f.png)

$$
V_{双螺杆料筒}=S \cdot  h= 58.29 \times 87.5 = 5100.38 mm^3 = 5.1 cm^3
$$

