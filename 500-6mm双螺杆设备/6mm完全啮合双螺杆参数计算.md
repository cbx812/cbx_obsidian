---
title: 6mm完全啮合双螺杆参数计算
chapter:
tags: 
 - 螺杆
 - 双螺杆
 - 6mm双螺杆
 - 6mm双螺杆参数计算
aliases:
 - 6mm完全啮合双螺杆
center: false
width: 827
height: 1170
---
[[2008_徐贤发_全啮合同向双螺杆挤出_KEY-GUGSWWGH]]
为满足齿轮模数，单个双螺杆螺杆齿轮齿数为$23$，模数为$0.25$，以满足$23 \times 0.25=5.75$，为满足齿轮传动和减小齿轮箱体积。将中心距确定为$5.75 {mm}$

中心距根据齿轮确定

通过完全啮合型齿轮设计基本螺杆参数

![|500](D:\obsidian\900-附件\6mm完全啮合双螺杆参数计算_1.jpg)

完全啮合型中心距$A$、螺杆外径$D$和螺杆根直径$D_r$的关系：
$$
A=\frac{D}{2}+\frac{D_r}{2}
$$

$$
D_r=2A-D=2 \times 5.75 - 6 = 5.5
$$


同时中心距$A$与螺杆外径$D$确定后决定了啮合区角$2 \phi $、啮合高度$I_h$和螺杆深度$H$。

啮合区半角$ \phi $：
$$
\cos \phi=\frac{A}{D}=\frac{5.75\mathrm{mm}}{6\mathrm{mm}}=0.958
$$
啮合高度$I_h$：
$$
I_h=\frac{1}{2}D \cdot \sin \phi=\frac{1}{2}D \cdot \sqrt{1-\cos^2 \phi}=\frac{1}{2}D \cdot \sqrt{1- \left ( \frac{A}{D}  \right )^2 }=\frac{1}{2} \times 6  \times  \sqrt{1-\left ( \frac{5.75}{6} \right ) ^2  } = 0.857\mathrm{mm}
$$



螺杆深度$H$：

$$
\frac{H}{D}=1-\frac{A}{D}
$$

$$
H=\left ( 1-\frac{A}{D}  \right ) \cdot D = 0.25
$$

当中心距增加时螺槽深度减小，

增加中心距将减小螺杆的输送能力

## 端面啮合曲线的形成

![端面曲线的形成_1](D:\obsidian\900-附件\端面曲线的形成_1.svg)

设 B 为螺杆 2 螺棱上的任意一点，为论述方便我们取动坐标系下的图：则B在${X_2O_2Y_2}$中的坐标为：
$$
\left\{\begin{array}{l}X_{B_2}=\frac{D}{2} \cos \alpha \\ Y_{B_2}=\frac{D}{2} \sin \alpha\end{array}\right.
$$
其中，$\alpha$为$O_2B$与$X_2$轴的夹角。

假设螺杆 1 不动，要使螺杆 1、2 正确啮合，即满足式![[6mm完全啮合双螺杆参数计算#^xpoqqj]]，则坐标系${X_2O_2Y_2}$ 相对于${X_1O_1Y_1}$ 作圆形平移运动，当坐标系${X_2O_2Y_2}$ 平移到任意时刻的某一位置时， B 点在坐标系${X_1O_1Y_1}$ 的坐标为：
$$
\left\{\begin{array}{l}X_{B_1}=X_{B_2}+ A \cos \theta \\ Y_{B_1}=Y_{B_{2}}+A \sin \theta\end{array}\right.
$$
其中，$\theta$为$O_1O_2$与$X_1$轴的夹角。
将上式代入得
$$
\left\{\begin{array}{l}X_{B_1}=\frac{D}{2} \cos \alpha+ A \cos \theta \\ Y_{B_1}=\frac{D}{2} \sin \alpha+A \sin \theta\end{array}\right.
$$
转化为圆的方程得
$$
(X_{B_1}-\frac{D}{2} \cos \alpha)^2+(Y_{B_1}-\frac{D}{2} \sin \alpha)^2=A^2
$$
对于螺棱上的任意一点 B ， $O_1B$与$X_2$轴的夹角$\alpha$ 也相应的确定了，故 B 点的运动轨迹在${X_1O_1Y_1}$坐标系下为圆心在某点 $(\frac{D}{2} \cos \alpha,\frac{D}{2} \sin \alpha)$，半径为${A}$的圆。为使 B 点轨迹的圆方程意义明显，任意给定的点 B 在 ${X_1O_1Y_1}$坐标系下的圆心可以转化为$(\frac{D}{2} \cos \alpha,\frac{D}{2} \sin \alpha)$，设圆心为 K ，并且点 K 在螺杆1的外圆上，如图 2-4 所示， B 点轨迹的圆心为 K 。

![端面曲线的形成_2](D:\obsidian\900-附件\端面曲线的形成_2.svg) ^mbbfkv

有以上的分析可以这样描述图[[6mm完全啮合双螺杆参数计算#^mbbfkv]]右侧圆盘C上任意一点B的相对运动轨迹的圆心K：过B做圆心${O_1}$、${O_2}$连线的平行线，与圆C的交点K就是B点作圆周运动的圆心，并且B的运动轨迹的半径为${\overline{KB}=\overline{O_1O_2}=A}$。另外，由圆的方程可以转化为
$$
(X_{B_1}-\frac{D}{2} \cos \alpha)^2+(Y_{B_1}-\frac{D}{2} \sin \alpha)^2=A^2
$$
$$
X_{B_1}^2+Y_{B_1}^2=\left ( \frac{D}{2}  \right ) ^{2} +A^2+2\cdot\frac{D}{2} \cdot A \cos \left ( \alpha -\theta  \right ) 
$$
由于在动坐标系中，图 2-3 中的右侧圆盘 1 C 随左侧圆盘 C 做圆形平动，即坐标系${X_2O_2Y_2}$绕坐标系${X_1O_1Y_1}$做圆形平动，所以$\alpha$ 在$0 \sim 360 ^{\circ}$范围内变化， 因此，必有一点满足方程：
$$
\left | \alpha -\theta  \right | =\pi 
$$
代入可得

$$
X_{B_1}^2+Y_{B_1}^2=\left ( \frac{D}{2}  \right ) ^{2} +A^2-2\cdot\frac{D}{2} \cdot A = \left ( A-\frac{D}{2} \right ) ^2
$$
又由于
$$
X_{B_1}^2+Y_{B_1}^2=\left ( \frac{D}{2}  \right ) ^{2}
$$
可以得知，B点的轨迹必然有与螺杆1基圆相切的一点。

如下图所示[[6mm完全啮合双螺杆参数计算#^s4resh]]，假设B点的运动轨迹与螺杆1基圆相切于一点$C_B$，并且与圆盘C交于${J_{B1}}$、${J_{B2}}$，则${J_{B1}}{J_{B2}}$弧段是点B在相对运动过程中与左侧圆盘C相接触形成的啮合曲线。

![端面曲线的形成_3](D:\obsidian\900-附件\端面曲线的形成_3.jpg) ^s4resh

${J_{B1}}{J_{B2}}$弧段的半径为${A}$，圆心为${K}$，在${J_{B1}}{J_{B2}}$弧段上任意取点${F}$，${\rho = O_1F}$，则在${ \triangle KFO }$中，由余弦定理可以得到：
$$
C_{L}^{2}=\left ( \frac{D}{2}  \right ) ^{2}+\rho^{2}-2 \cdot \frac{D}{2}\cdot \rho \cdot \cos (\pi-\beta)
$$

其中$\beta$为${O_1F}$与${O_1K}$的夹角

式（2-11）为圆盘1C边缘上的任意一点B与圆盘C相对运动接触后，形成的啮合曲线方程。

## 端面啮合曲线的数学模型

对于给定的已知螺杆外圆半径 R 、中心距${A}$、螺纹头数为 n 的无间隙 的全啮合双螺杆，由于每根螺杆的螺棱在旋转的过程中都要与另一根螺杆的螺棱 相啮合，因此根据螺杆简化为两圆盘后的相对运动可以求出其端面的形状以及其 数学方程。

![](https://i0.hdslb.com/bfs/album/5e1066eafa4f7d32ea6709a07623ecdf2bd35226.png)

由 2.1 节的啮合原理，研究了相对运动中端面曲线的形成过程（如 2.2 节）。 下面根据前两节的研究，建立单头、双头、三头全啮合同向双螺杆的端面啮合线的数学模型，并研究螺杆外圆直径${D}$、中心距${A}$ 、螺纹头数 n 之间的关系。

![端面啮合曲线的数学模型_1](D:\obsidian\900-附件\端面啮合曲线的数学模型_1.jpg)

在图2-7-a与图2-7-b中，设${P}$、${Q}$为螺杆2边缘上夹角为$\alpha$的弧段，介于${P}{Q}$弧段间的每一个点的运动轨迹都是一条圆心在螺杆1的边缘上，以${A}$为半径的圆弧。P点的轨迹与圆C边缘相交于${J_{P1}}$、${J_{P2}}$，与螺杆1的基圆相切于${C_P}$；Q点的轨迹与圆C边缘相交于${J_{Q1}}$、${J_{Q2}}$，与螺杆1的基圆相切于${C_Q}$。按照全啮合理论，螺杆1上的端面曲线应是螺杆2螺棱上所有点相对运动轨迹的包络线，类似于图2-6的情形。如图2-7a、2-7-b，若${P}$、${Q}$分别是螺杆2端面上螺棱的端点，那么整个螺棱${P}{Q}$弧段上扫过螺杆1外圆盘C上的区域是一个月牙形，其包络线由三段圆弧组成，弧段${J_{P1}C_P}$、弧段${C_P}{C_Q}$、弧段${C_Q}J_{Q2}$；根据以上分析，螺杆的端面应有弧段$J_{P1}M_QM_PJ_{Q2}$、弧段${J_{P1}C_P}$、弧段${C_P}{C_Q}$、弧段$C_QJ_{Q2}$组成，存在以下几何关系：

（a）在图 2-7-a 与图 2-7-b 中，延长线段$\overline{M_PC_p}$与左侧圆盘 C 的边缘相交于点E ，在直角 $\triangle M_PJ_{p1}E$中

$$
\cos \phi=\frac{\overline{J_{P 1} M_{P}}}{2 R}=\frac{C_{L}}{2 R}
$$

$$
\phi=\arccos \left ( \frac{A}{2}  \right )
$$
由于圆心角$\angle J_{P1}O_1C_P$等于圆周角$\angle J_{P1}M_PC_P$的二倍，可得$\angle J_{P1}O_1C_{P}= 2\phi$，同理，可得$\angle C_{Q}O_1J_{Q2}= 2\phi$。

（b）齿顶角是圆盘上的边缘弧段的两端点与其圆心所形成的圆心角，如$\angle PO_{2}Q = \alpha$；齿根角是圆盘基圆弧段的两端点与其圆心所形成的圆心角，如$\angle C_PO_{1}C_Q = \beta$。在实际设计中，两螺杆具有完全相同的截面形状，为保证正常啮合，螺杆1的端面上应与螺杆2的端面上具有相同的齿顶角$\alpha$与根圆角$\beta$，也就是说应使螺杆端面的齿顶角$\alpha$与其根圆角$\beta$相等，即$\alpha=\beta$。如图2-7-a与图2-7-b中所示，左边螺杆的端面螺棱部分$J_{Q 2} M_{P} M_{Q} J_{P 1}$所对应得中心角为齿顶角，大小为$\alpha=\beta$。
$$
\angle J_{P 1} o J_{Q_{2}}=\angle J_{P 1} o C_{P}+\angle C_{Q} o J_{Q_{2}}+\angle C_{Q} o J_{Q_{2}}=2 \phi+\beta+2 \phi
$$

又弧段$J_{Q 2} M_{P} M_{Q} J_{P 1}$对应的中心角为$\alpha$，所以

$$
(2 \phi+\beta+2 \phi)+\alpha=(2 \phi+\alpha+2 \phi)+\alpha=4 \phi+2 \alpha=2 \pi
$$
---
双头螺杆的端面啮合曲线（ n=2）

![端面啮合曲线的数学模型_2](D:\obsidian\900-附件\端面啮合曲线的数学模型_2.jpg)

如图2-8，为研究方便，使$P$、$Q$两点关于X轴对称，选择弧段$C_PC_Q$、弧段$C_PJ_{P1}$、弧段$J_{P1}J'_{P1}$为研究对象，端面曲线用极坐标表示，$\theta$的转角从$X$轴开始表示极角，$\rho \left ( \theta  \right )$ 表示极半径，则：

1. 在弧段$C_PC_Q$上：

$$
\rho \left ( \theta  \right ) =\frac{D_r}{2}
$$


2. 在弧段1PPJC上：其在圆心为$\left ( x_{0},y_{0}   \right )$ ，半径为$A$的圆周上，该圆周的方程为

$$\left ( x-x_{0} \right )^{2}  + \left ( y-y_{0} \right )^{2} =A^{2} $$ ^qo23n9

其中

$$
\left\{\begin{array}{l}x_{Q}=-\frac{D}{2} \cos \left(\frac{\alpha}{2}\right) \\ y_{Q}=-\frac{D}{2} \sin \left(\frac{\alpha}{2}\right)\end{array}\right.
$$

下面把满足式[[6mm完全啮合双螺杆参数计算#^qo23n9]]的弧段用极坐标表示：该弧段上的任意一点$M$、点$O_1$、点$M_Q$三点构成$\triangle MO_1M_Q$，$\left | M_QO_1 \right |=\frac{D}{2}$，$\left | O_1M   \right | = \rho \left ( \theta  \right )$，$\left | M_QM \right | =A$存在下面关系：

$$
\begin{aligned} A^{2} &=\rho^{2}(\theta)+R^{2}-2 \rho(\theta) R \cos \left[\pi-\left(\theta-\frac{\alpha}{2}\right)\right] \\ &=\rho^{2}(\theta)+R^{2}+2 \rho(\theta) R \cos \left(\theta-\frac{\alpha}{2}\right) \end{aligned}
$$

等价于$\rho^{2}(\theta)+2 \rho(\theta) R \cos \left(\theta-\frac{\alpha}{2}\right)+R^{2}-C_{L}^{2}=0$


$$
\rho(\theta)=-R \cos \left(\theta-\frac{\alpha}{2}\right) \pm \sqrt{R^{2} \cos ^{2}\left(\theta-\frac{\alpha}{2}\right)-\left(R^{2}-C_{L}^{2}\right)}
$$

显然$\rho \left ( \theta  \right ) > 0$

所以：

$$
\rho(\theta)=-R \cos \left(\theta-\frac{\alpha}{2}\right) + \sqrt{R^{2} \cos ^{2}\left(\theta-\frac{\alpha}{2}\right)-\left(R^{2}-C_{L}^{2}\right)}
$$

3. 在弧段$J_{P1}J'_{P1}$上，$\rho \left ( \theta  \right ) = R$

同理可以计算弧段其他各段对应得曲线极坐标方程。可得：

$$
\rho(\theta)=\left\{\begin{array}{ll}r & -\frac{\alpha}{2}<\theta \leq \frac{\alpha}{2} 
\\ & \text { 或 } \frac{3 \alpha}{2}+4 \phi<\theta \leq \frac{5}{2} \alpha+4 \phi \\ R & \frac{\alpha}{2}+2 \phi<\theta \leq \frac{3 \alpha}{2}+2 \phi \\ & \text { 或 } \frac{5 \alpha}{2}+6 \phi<\theta \leq \frac{7 \alpha}{2}+6 \phi \\ -R \cos \left(\theta-\frac{\alpha}{2}\right)+\sqrt{C_{L}^{2}-R^{2} \sin ^{2}\left(\theta-\frac{\alpha}{2}\right)} & \frac{\alpha}{2}<\theta \leq \frac{\alpha}{2}+2 \phi \\ R \cos \left(\theta+\frac{\alpha}{2}\right)+\sqrt{C_{L}^{2}-R^{2} \sin ^{2}\left(\theta+\frac{\alpha}{2}\right)} & \frac{3 \alpha}{2}+2 \phi<\theta \leq \frac{3 \alpha}{2}+4 \phi \\ R \cos \left(\theta-\frac{\alpha}{2}\right)+\sqrt{C_{L}^{2}-R^{2} \sin ^{2}\left(\theta-\frac{\alpha}{2}\right)} & \frac{5}{2} \alpha+4 \phi<\theta \leq \frac{5 \alpha}{2}+6 \phi \\ -R \cos \left(2 \pi-\theta-\frac{\alpha}{2}\right)+\sqrt{C_{L}^{2}-R^{2} \sin ^{2}\left(2 \pi-\theta-\frac{\alpha}{2}\right)} & \frac{7 \alpha}{2}+6 \phi<\theta \leq \frac{7 \alpha}{2}+8 \phi\end{array}\right.
$$