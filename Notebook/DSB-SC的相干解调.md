[DSB-SC的相干解调](file://C:/Users/cheda/Videos/14830409/33/14830409_33_0.mp4)
# 相干解调和非相干解调
## 相干解调

- ![[Pasted image 20211111161006.png]]
- 特点：
	1. 解调器需要有和发送信号同步的载波——标称频率
	2. 相位是随机变量，无法保证相位差为恒定
- 载波同步：——DSB-SC 解调为 $m(t)$
	![[Pasted image 20211111161102.png]]
	解调——乘以载波 cos、接低通滤波器——载波乘以 cos，回归基带信号、更高频率的信号——低通过滤掉高频率信号
- 解调器输出的是复包络的实部![[Pasted image 20211111224728.png]]
	- $$\text { 输出 }=I(t)=\operatorname{Re}\left\{r_{\mathrm{L}}(t)\right\}$$
	- 这里实部就是 $m(t)$，本身就是实信号
- 载波不同步：——有相位干扰
	![[Pasted image 20211111161150.png]]
		-	用复数理解：
			-	解调：频谱搬回基带（$s_L(t)=z(t)e^{-j2\pi f_ct}$）
			-	调制：频谱从基带搬到频带 ($z(t)=s_L(t)e^{j2\pi f_ct}$)
			-	不同频率，不同相位：$$\begin{aligned}
带通信号 z (t) &=s_{\mathrm{L}}(t) \mathrm{e}^{\mathrm{j}\left (2 \pi f_{1} t+\theta\right)} \\
带通信号解调
& \rightarrow z(t) \mathrm{e}^{-\mathrm{j}\left(2 \pi f_{2} t+\varphi\right)} \rightarrow s_{\mathrm{L}}(t) \mathrm{e}^{\mathrm{j}\left(2 \pi\left(f_{1}-f_{2}\right) t+\theta-\varphi\right)}
\end{aligned}$$
- ![[Pasted image 20211112003831.png]]
- ![[Pasted image 20211112003928.png]]
- 这里的确实有虚部
**DSB-SC 相干解调的实质是取出接收带通信号复包络的同相分量——实部**
# DSB-SC 只能相干解调
- 相干解调的本质是取出复包络的实部
## DSB-SC 的实质是取出接收带通信号复包络的同相分量——实部
## 实现相干解调的一种方法——发送端插入导频
- 发端添加一个所用的载波 $a\cdot c(t),c(t)为本信号所用的载波$
$$s(t)=m(t) \cdot c(t)+{\color{Red} a \cdot c(t)} =[{\color{Red} a} +m(t)] \cdot c(t)$$
	-	$a \cdot c(t)$ ——导频
- 若$$c(t)=\cos(2\pi f_ct)$$
	$$\begin{array}{c}
s(t)=m(t) \cdot c(t)+a \cdot c(t)=[a+m(t)] \cdot c(t) \\
S(f)=\frac{1}{2} M\left(f-f_{\mathrm{c}}\right)+\frac{1}{2} M\left(f+f_{\mathrm{c}}\right)+\frac{a}{2} \delta\left(f-f_{\mathrm{c}}\right)+\frac{a}{2} \delta\left(f+f_{\mathrm{c}}\right)
\end{array}$$
	-	![[Pasted image 20211111165637.png]]
- 理解：
	- 时域：调制信号 $m(t)$ 上添加直流
	- 频域：位于载频 $f_c$ 的冲激——不再是**抑制载波**的 DSB 信号
- 接收端解调
	- ![[Pasted image 20211111170135.png]]
	- 自己解调自己、提取基带信号 $a+m(t)$ ->隔直 $a$
	- 当然提取出来的同步载波不一定只有实部，有可能有相位，也能提取出来——只不过图画不出来