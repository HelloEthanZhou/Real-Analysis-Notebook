# 目录

[TOC]



# 零、引言

本章将阐述Lebesgue微积分体系的产生动机。

## 1	Fourier级数

对于定义在$[-\pi,\pi]$上的Riemann可积的函数$f$，其Fourier级数可表示为
$$

$$
其中$a_n$为
$$
a_n=\frac{1}{2\pi}{\int_{-\pi}^{\pi}{f(x)\mathrm{e}^{-inx}\mathrm{d}x}}
$$
由此产生了两个问题：

1. 当我们完备$\mathcal{R}$时，假定的函数$f$到底是什么？
2. 我们如何积分这样的函数$f$？

## 2	连续函数的性质

对于定义在$[0,1]$上的连续函数序列$\{f_n\}$，对任意$x\in[0,1]$
$$
\lim_{n\to\infty}{f_n(x)}=f(x)
$$
若$f_n$一致收敛，那么$f$将连续。但若放弃“一直连续”的性质，$f$的性质将发生微妙的变化。例如，我们可以构造满足如下性质的函数序列$\{f_n\}$：

- $0 \le f_n(x) \le 1$，对于任意$x\in[0,1]$。
- $f_n(x)$随$n$而单调递减。
- $f_n$的极限$f$Riemann不可积。

对于函数序列$\{f_n\}$，若满足前两个条件，则$f_n$存在。那么函数序列$\{f_n\}$要满足什么性质使得成立
$$
\int_{0}^{1}{f(x)\mathrm{d}x}=\lim_{n\to\infty}{\int_{0}^{1}{f_n(x)\mathrm{d}x}}
$$

## 3	曲线的长度

考虑平面上的曲线
$$
\Gamma=\{(x(t),y(t))\},a\le t\le b
$$
选取
$$
a=t_0<t_1<\cdots<t_{n-1}<t_n=b
$$
则曲线的长度定义为
$$
L=\lim_{n\to\infty}{\sum_{k=1}^{n}{\sqrt{(x(t_{k})-x(t_{k-1}))^2+(y(t_{k})-y(t_{k-1}))^2}}}
$$
若曲线的长度有限，则称曲线是**可求长的(rectifiable)**。若$x(t)$和$y(t)$连续可微，则成立
$$
L=\int_{a}^{b}{\sqrt{(x'(t))^2+(y'(t))^2}\mathrm{d}t}
$$
于是自然就有了如下问题：

- $x(t)$和$y(t)$保证$\Gamma$可求长的条件是什么？
- 当满足此条件时，上式是否成立？

## 4	微积分

微积分基本定理
$$
F(b)-F(a)=\int_{a}^{b}{F'(x)\mathrm{d}x}
$$

$$
\frac{\mathrm{d}}{\mathrm{d}x}\int_{0}^{x}{f(y)\mathrm{d}y}=f(x)
$$

- 连续但处处不可微函数的存在性。
- 处处可微但导函数不可积函数的存在性。

## 5	测度论

为解决上述问题，必须理解的根本问题在于**度量**。

我们需要寻找定义在$E\sub\R$上的非负函数$m$，满足以下性质：

- 如果$E=[a,b]$，那么
   $$
   m(E)=b-a
   $$

- 如果
   $$
   E=\bigcup_{n=1}^{\infty}{E_n}
   $$
   且集合$E_n$是互不相交的，那么
   $$
   m(E)=\sum_{n=1}^{\infty}{m(E_n)}
   $$

- 对于任意$h\in\R$，成立
   $$
   m(E+h)=m(E)
   $$

## 年表

1872年 ：Weierstrass构造一个无处可微函数。

1881年：Jordan引入了有界变差函数，后来于1887年与可求长性联系起来。

1883年：Cantor的三元集。

1890年：Peano建造了一条充满空间的曲线。

1898 年：Borel的可测集。

1902年：Lebesgue的测度与积分理论。

1905年：Vitali构造了不可测集。

1906年：Fatou将Lebesgue理论应用于复分析。

# 一、测度论

## 1	前言

### 1.1	点

**点**：$x\in\R^d$
$$
x=(x_1,\cdots,x_d),\quad x_k\in\R,i=1,\cdots,d
$$
**范数(norm)**：
$$
|x|=\sqrt{x_1^2+\cdots+x_d^2}
$$
**距离(distance)**：两点$x,y\in\R^d$的距离
$$
|x-y|
$$
两集合$E,F\in\R^d$的距离
$$
d(E,F)=\inf{|x-y|},\quad x\in E,y\in F
$$
**补集(complementary set)**：$E\in\R^d$的补集记作$E^c$
$$
E^c=\{x\in\R^d:x\not\in E\}
$$
**差集(difference set)**：$E,F\in\R^d$
$$
E-F=\{x\in\R^d:x\in E且x\not\in F\}
$$

### 1.2	开集，闭集和紧集

**开球(open ball)**：
$$
B_r(x)=\{y\in\R^d:|y-x|<r\}
$$
**开集(open set)**：称$E$为开的，如果对于任意$x\in E$，存在$r>0$使得成立$B_r(x)\sub E$。

**闭集(closed set)**：称$E$为闭的，如果其补集为开的。

**有界集(bounded set)**：称$E$为有界的，如果其包含于半径有限的开球中。

**紧集(compact set)**：称$E$为紧致的，如果$E$有界且闭。

>Heine-Borel定理：如果$E$为紧致的，且
>$$
>E\sub\bigcup_{\alpha}{\mathcal{O}_\alpha}
>$$
>其中每一个$\mathcal{O}_{\alpha}$为开的，那么存在有限个开集$\mathcal{O}_{\alpha_1},\cdots,\mathcal{O}_{\alpha_n}$，使得成立
>$$
>E\sub\bigcup_{k=1}^{n}{\mathcal{O}_{\alpha_k}}
>$$

---

**极限点(limit point)**：称$x\in\R^d$为$E$的极限点，如果对于任意$r>0$，使得成立
$$
B_r(x)\cap E\ne \empty
$$
**孤立点(isolated point)**：称$x\in E$为$E$的孤立点，如果存在$r>0$，使得成立
$$
B_r(x)\cap E=\{x\}
$$
**内点(interior point)**：称$x\in E$为$E$的内点，如果存在$r>0$，使得成立
$$
B_r(x)\sub E
$$
**内部(interior)**：$E$的所有内点的集合称为$E$的内部。

**闭包(closure)**：$E$及其极限点构成的集合称为$E$的闭包，记作$\overline{E}$。

**边界(boundary)**：在$E$的闭包中但不在$E$内部的点的集合称为$E$的边界，记作$\part E$。

### 1.3	矩形和立方体

**矩形(rectangl)**：
$$
R=[a_1,b_2]\times\cdots\times[a_d,b_d]
$$
其中$a_k\le b_k$且$a_k,b_k\in\R$，$k=1,\cdots,d$。称$b_1-a_1,\cdots,b_d-a_d$为其**边长(side)**。

**体积(volume)**：
$$
|R|=(b_1-a_1)\cdots(b_d-a_d)
$$

**方体(cube)**：边长相等的矩形。记立方体$Q$的边长为$\mathscr{l}$，那么其体积为
$$
|Q|=\mathscr{l}^d
$$

**几乎不相交(almost disjoint)**：称矩形是几乎不相交的，如果其内部不相交。

---

**引理1.1**：如果
$$
R=\bigcup_{k=1}^{n}{R_k}
$$
且$R_1,\cdots,R_n$几乎处处不相交，那么
$$
|R|=\sum_{k=1}^{n}{|R_k|}
$$

**引理1.2**：如果
$$
R\sub\bigcup_{k=1}^{n}{R_k}
$$
且$R_1,\cdots,R_n$几乎处处不相交，那么
$$
|R|\le\sum_{k=1}^{n}{|R_k|}
$$

**定理1.3**：$\R$的任意开子集$\mathcal{O}$都可表示为且唯一表示为可数个不相交的开区间的并。

**定理1.4**：$\R^d$的任意开子集$\mathcal{O}$都可表示为可数个几乎不相交的闭集的并。

### 1.4	Cantor集

记
$$
\begin{align}
&C_0=[0,1]\\
&C_1=[0,\frac{1}{3}]\cup[\frac{2}{3},1]\\
&C_2=[0,\frac{1}{9}]\cup[\frac{2}{9},\frac{1}{3}]\cup[\frac{2}{3},\frac{7}{9}]\cup[\frac{8}{9},1]\\
&\cdots
\end{align}
$$
即
$$
C_n=\bigcup_{k=1}^{2^n}{[a_{k}^{(n)},b_{k}^{(n)}]}
$$
其中
$$
\begin{cases}
a_1^{(0)}=0,\quad b_1^{(0)}=1\\
b_{m}^{(n)}-a_{m}^{(n)}=\frac{1}{3^n}\\
a_{2m-1}^{(n+1)}=a_{m}^{(n)}\\
b_{2m}^{(n+1)}=b_{m}^{(n)}
\end{cases}
$$

**Cantor集**记作
$$
\mathcal{C}=\bigcap_{k=0}^{\infty}{C_k}=\left\{ x\in[0,1]:x=\sum_{n=1}^{\infty}{\frac{c_n}{3^n}},c_n\in\{0,2\} \right\}
$$

- Cantor集的基数为连续基数。
- Cantor集为Lebesgue零测集。
- Cantor集为紧致集。
- Cantor集为**完美(perfect)**集，即其不存在孤立点。
- Cantor集为**无处稠密集(nowhere dense set)**，即对于任意$(x,y)\sub\R$，存在$(a,b)\sub(x,y)$，使得成立$(a,b)\cap\mathcal{C}=\varnothing$。
- Cantor集为**完全不连通(totally disconnected)**的，即对于任意$x<y\in\mathcal{C}$，存在$z\in(x,y)$，使得成立$z\not\in\mathcal{C}$。

## 2	外测度

### 2.1	外测度的定义

**外测度(The exterior measure)**：对于$E\sub\R^d$，定义外测度为映射
$$
m_*:\mathcal{P}(\R^d)\to [0,\infty]
$$
满足
$$
m_*(E)=\inf{\sum_{k=1}^{\infty}{|Q_k|}}
$$
其中
$$
E\sub\bigcup_{k=1}^{\infty}{Q_k}
$$
由此，$0\le m_*(E) \le +\infty$。同时，对于任意$\varepsilon>0$，存在覆盖$E\sub\bigcup_{k=1}^{\infty}{Q_k}$，使得
$$
\sum_{k=1}^{\infty}{m_*(Q_k)} \le m_*(E)+\varepsilon
$$

- 点的外测度为$0$。
- 闭的立方体的外测度为其体积。
- 开的立方体的外测度为其体积。
- 矩形的外测度为其体积。
- $\R^d$的外测度为$+\infty$。
- Cantor集$\mathcal{C}$的外测度为$0$。

### 2.2	外测度的性质

**性质1	单调性(monotonicity)**：如果$E_1\sub E_2$，那么$m_*(E_1) \le m_*(E_2)$。

**性质2	次可加性(countable sub-additivity)**：如果
$$
E=\bigcup_{k=1}^{\infty}{E_k}
$$
那么
$$
m_*(E)\le\sum_{k=1}^{\infty}{m_*(E_k)}
$$

**性质3**：如果$E\sub\R^d$，那么
$$
m_*(E)=\inf{m_*(\mathcal{O})}
$$
其中
$$
E\sub\mathcal{O}
$$

**性质4**：如果$E=E_1\cup E_2$，且$d(E_1,E_2)>0$，那么
$$
m_*(E)=m_*(E_1)+m_*(E_2)
$$

**性质5**：如果$E$可写成几乎处处不相交的立方体的可数并集
$$
E=\bigcup_{k=1}^{\infty}{Q_k}
$$
那么
$$
m_*(E)=\sum_{k=1}^{\infty}{|Q_k|}
$$

## 3	可测集和Lebesgue测度

### 3.1	可测集和Lebesgue测度

**可测集(measurable set)**：称$E\sub\R^d$为（Lebesgue）可测的，如果对于任意$\varepsilon>0$，存在开集$\mathcal{O}\supset E$，使得成立
$$
m_*(\mathcal{O}-E)\le\varepsilon
$$

$\R^d$上所有可测集构成的集族为$\mathscr{M}$。

**Lebesgue测度(Lebesgue measure)**：Lebegue测度为映射
$$
m=m_*:\mathscr{M}\to[0,\infty]
$$

---

**性质1**：$\R^d$中任意开集是可测的。

**性质2**：对于$E\sub\R^d$，如果$m_*(E)=0$，那么$E$是可测的。特别的，如果$F$为一个外测度为$0$的集合的子集，那么$F$是可测的。

**性质3**：可测集合的可数并是可测的，即对于$E_1,E_2,\cdots\in\mathscr{M}$，那么
$$
\bigcup_{n=1}^{\infty}{E_n}\in\mathscr{M}
$$

**性质4**：$\R^d$中任意闭集是可测的。

**引理3.1**：如果$F$为闭集，$K$为紧集，且$F\cap F=\varnothing$，那么$d(F,K)>0$。

**性质5**：可测集合的补集是可测的。

**性质6**：可测集合的可数交是可测的。

---

**定理3.2	可数可加性**：如果$E_1,E_2,\cdots$是两两无交的可测集，且
$$
E=\bigsqcup_{n=1}^{\infty}{E_n}
$$
那么$E$是可测的，且
$$
m(E)=\sum_{n=1}^{\infty}{m(E_n)}
$$

**推论3.3**：对于$\R^d$中的可测集$E_1,E_2,\cdots$，成立

- **第一单调收敛定理(Continuity from below)**：如果对于任意$n\in\N^*$，$E_n\sub E_{n+1}$，且
  $$
  E=\bigcup_{n=1}^{\infty}{E_n}
  $$
  那么
  $$
  m(E)=\lim_{n\to\infty}{m(E_n)}
  $$

- **第二单调收敛定理(Continuity from above)**：如果对于任意$n\in\N^*$，$E_n\supset E_{n+1}$，且
  $$
  E=\bigcap_{n=1}^{\infty}{E_n}
  $$
  同时存在$n\in\N^*$使得$m(E_n)<\infty$，那么
  $$
  m(E)=\lim_{n\to\infty}{m(E_n)}
  $$

---

**定理3.4**：如果$E\sub\R^d$为可测的，那么对于任意$\varepsilon>0$，成立

- 存在开集$\mathcal{O}\supset E$，使得成立
  $$
  m(\mathcal{O}-E)\le\varepsilon
  $$

- 存在闭集$F\sub E$，使得成立
  $$
  m(E-F)\le\varepsilon
  $$

- 如果$m(E)<\infty$，那么存在紧集$K\sub E$，使得成立
  $$
  m(E-K)\le\varepsilon
  $$

- 如果$m(E)<\infty$，那么存在有限并集
  $$
  F=\bigcup_{k=1}^{n}{Q_k}
  $$
  使得成立
  $$
  m(E\triangle F)\le\varepsilon
  $$
  其中$E\triangle F$为二者**对称差**，即
  $$
  E\triangle F=(E-F)\cup (F-E)
  $$

### 3.2	Lebesgue测度的不变性

**平移不变性(translation-invariance)**：对于任意$E\in\mathscr{M}$，以及任意$h\in\R^d$，成立
$$
m(E+h)=m(E)
$$
其中
$$
E+h=\{ x+h:x\in E \}
$$

**膨胀不变性(dilation-invariance)**：对于任意$E\in\mathscr{M}$，以及任意$\delta>0$，成立
$$
m(\delta E)=\delta^d m(E)
$$
其中
$$
\delta E=\{ \delta x:x\in E \}
$$

**反射不变性(reflection-invariant)**：对于任意$E\in\mathscr{M}$，成立
$$
m(-E)=m(E)
$$
其中
$$
-E=\{ -x:x\in E \}
$$

### 3.3	$\sigma$-代数和Borel集

**$\sigma$-代数($\sigma$-algebra)**：称$\Sigma\sub\mathcal{P}(\R^d)$为$\sigma$-代数，如果满足如下性质：

- **对补集封闭**：如果$A\in\Sigma$，那么$A^c\in\Sigma$。

- **对可数并封闭**：如果$A_1,A_2,\cdots\in\Sigma$，那么
  $$
  \bigcup_{n=1}^{\infty}{A_n}\in\Sigma
  $$

**最小$\sigma$-代数(smallest $\sigma$-algebra)**：对于$A\sub\mathcal{P}(\R^d)$，存在且存在唯一$\sigma$-代数$\Sigma(A)$，使得成立

- $A\sub\Sigma(A)\sub\mathcal{P}(\R^d)$
- 对于任意$\sigma$-代数$\Sigma\sub\mathcal{P}(S)$，如果$A\sub\Sigma$，那么$\Sigma(A)\sub\Sigma$。

称$\Sigma(A)$为$A$的最小$\sigma$-代数。事实上
$$
\Sigma(A)=\bigcap_{A\sub\Sigma(A)\sub\mathcal{P}(\R^d)}{\Sigma}
$$

**Borel $\sigma$-代数(Borel $\sigma$-algebra)**：包含$\R^d$中所有开集的最小$\sigma$-代数称为Borel $\sigma$-代数，记作$\mathcal{B}_{\R^d}$。

**Borel集(Borel set)**：$\mathcal{B}_{\R^d}$中的元素称为Borel集。

**推论3.5**：以下命题等价

- 集合$E\sub\R^d$是可测的。
- 对于开集的可数交集$G_{\delta}$，如果$E=G_{\delta}-N$，那么$m(N)=0$。
- 对于闭集的可数并集$F_{\sigma}$，如果$E=F_{\sigma}\cup N$，那么$m(N)=0$。

### 3.4	不可测集的构造

**定理3.6**：定义等价关系
$$
x\sim y\iff x-y\in\Q
$$
记所有等价类为$\mathcal{E}_\alpha$，从每个$\mathcal{E}_\alpha$选出一个代表元素$x_\alpha$，记
$$
\mathcal{N}=\{ x_\alpha \}
$$
那么$\mathcal{N}$是不可测的。

### 3.5	选择公理

**选择公理(axiom of choice)**：对于集合$E$，$\{ E_\alpha \}$为其非空子集的集合，那么存在**选择函数**$\alpha\to x_\alpha$，使得对于任意$\alpha$，成立$x_\alpha\in E_\alpha$。

**线性有序的(linearly ordered)**：称集合$E$是线性有序的，如果存在二元关系$\le$，使得成立：

- 对于任意$x\in E$，成立$x\le x$。
- 如果$x,y\in E$是不同的，那么$x\le y$和$y \le x$成立且仅成立其一。
- 如果$x\le y$且$y\le z$，那么$x \le z$。

**良序原则(well-ordering principle)**：称集合$E$是良序的，如果其是线性有序的，且对于任意非空集合$A\sub E$，存在$x_0\in A$，使得对于任意$x\in A$，成立$x_0\le x$。

- 任意集合都是良序的。

## 4	可测函数

### 4.1	定义和基本性质

**可测函数(measurable function)**：称定义在可测集$E\sub\R^d$上的函数$f$为可测函数，如果对于任意$a\in\R$，集合
$$
f^{-1}([-\infty,a))=\{ x\in E:f(x)<a \}
$$
是可测集。

给定记号：
$$
\{ f<a \}=\{ x\in E:f(x)<a \}
$$
对于定义在可测集$E\sub\R^d$上的函数$f$，以下命题等价：

- $f$是可测函数。
- 对于任意$a\in\R$，$\{ f<a \}$是可测集。
- 对于任意$a\in\R$，$\{ f>a \}$是可测集。
- 对于任意$a\in\R$，$\{ f\le a \}$是可测集。
- 对于任意$a\in\R$，$\{ f\ge a \}$是可测集。
- 如果$f$是有限值函数，那么对于任意$a<b\in\R$，$\{a<f<b\}$是可测集。
- 如果$f$是有限值函数，那么对于任意$a<b\in\R$，$\{a\le f<b\}$是可测集。
- 如果$f$是有限值函数，那么对于任意$a<b\in\R$，$\{a<f\le b\}$是可测集。
- 如果$f$是有限值函数，那么对于任意$a<b\in\R$，$\{a\le f\le b\}$是可测集。

**性质1**：对于有限值函数$f$，以下命题等价。

- $f$是可测函数。
- 对于任意开集$\mathcal{O}$，集合$f^{-1}(\mathcal{O})$是可测集。
- 对于任意闭集$F$，集合$f^{-1}(F)$是可测集。

**性质2**：如果$f$是连续函数，那么$f$是可测函数。

**性质3**：如果$f$是连续有限值函数，并且$\Phi$是连续函数，那么$\Phi\circ f$是可测函数。

**性质4**：如果$\{ f_n \}_{n\in\N^*}$为可测函数列，那么
$$
\sup_{n}{f_n},\quad \inf_{n}{f_n},\quad \limsup_{n\to\infty}{f_n},\quad \liminf_{n\to\infty}{f_n}
$$
都是可测函数。

**性质5**：如果$\{ f_n \}_{n\in\N^*}$为可测函数列，且
$$
\lim_{n\to\infty}{f_n}=f
$$
那么$f$是可测函数。

**性质6**：如果$f$和$g$是可测函数，那么对于任意$n\in\N^*$，$f^n$是可测函数。

**性质7**：如果$f$和$g$是有限值可测函数，那么$f+g$和$fg$都是可测函数。

---

**几乎处处(almost everywhere)**：称命题$P(x)$几乎处处成立，当且仅当
$$
m(\{ x:P(x)不成立 \})=0
$$

**性质8**：对于可测函数$f$，如果$f=g$几乎处处成立，那么$g$是可测函数。

### 4.2	由简单函数或阶跃函数逼近

**示性函数(indicator function)**：对于$E\sub\R^d$，定义$E$上的示性函数为
$$
\chi_E(x)=\begin{cases}
1,\quad & x\in E\\
0,\quad & x\in\R^d-E
\end{cases}
$$

- $\chi_E$是可测函数，当且仅当$E$是可测集合。

- 如果$A\cap B=\varnothing$，那么
  $$
  \chi_{A\cup B}=\chi_A+\chi_B
  $$

- $$
  \chi_{A\cap B}=\chi_A\chi_B
  $$

---

**简单函数(simple function)**：称$f$是$\R^d$上的简单函数，如果$f$可表示为如下形式
$$
f=\sum_{k=1}^{n}{a_k\chi_{E_k}}
$$
其中$a_1,\cdots,a_n\in\R$，$E_1,\cdots,E_n\in\mathscr{M}$，且对于任意$k=1,\cdots,n$，成立
$$
m(E_k)<\infty
$$

> 简单函数的**标准表示(canonical form)**：简单函数$f$可表示为
> $$
> f=\sum_{k=1}^{n}{a_k\chi_{E_k}}
> $$
> 其中$a_1,\cdots,a_n\in\R$，$E_1,\cdots,E_n\in\mathscr{M}$两两无交，且对于任意$k=1,\cdots,n$，成立
> $$
> m(E_k)<\infty
> $$
>

**阶跃函数(step function)**：称$f$是$\R^d$上的阶跃函数，如果$f$可表示为如下形式
$$
f=\sum_{k=1}^{n}{a_k\chi_{R_k}}
$$
其中$a_1,\cdots,a_n\in\R$，$R_1,\cdots,R_n$为矩形，且对于任意$k=1,\cdots,n$，成立
$$
m(E_k)<\infty
$$

---

**定理4.1**：如果$f:\R^d\to[0,\infty]$是可测函数，那么存在逐点收敛于$f$的递增的非负简单函数序列$\{ \varphi_n \}_{n\in\N^*}$，即
$$
0\le \varphi_1\le\varphi_2\le\cdots\le f
$$
且
$$
\lim_{n\to\infty}{\varphi_n}=f
$$
同时，如果$f$是有界函数，那么$\varphi_n$一致收敛于$f$。

**定理4.2**：如果$f:\R^d\to[-\infty,\infty]$是可测函数，那么存在简单函数序列$\{ \varphi_n \}_{n\in\N^*}$，满足
$$
0\le |\varphi_1|\le|\varphi_2|\le\cdots\le |f|
$$
且
$$
\lim_{n\to\infty}{\varphi_n}=f
$$

**定理4.3**：如果$f:\R^d\to[-\infty,\infty]$是可测函数，那么存在阶跃函数数序列$\{ \psi_n \}_{n\in\N^*}$，满足$\psi_n$几乎处处收敛于$f$。

### 4.3	Littlewood三原则

**Littlewood三原则：**

- 任意可测集合几乎是有限区间的并。
- 任意可测函数几乎是连续的。
- 任意收敛可测函数序列几乎是一致收敛的。

**定理4.4	Egorov定理**：对于定义在可测集合$E$且$m(E)<\infty$的可测函数序列$\{ f_n \}_{n\in\N^*}$，如果$f_n$在$E$上几乎处处收敛于$f$，那么对于任意$\varepsilon>0$，存在闭集$A_\varepsilon\sub E$，使得成立
$$
m(E-A_\varepsilon)\le\varepsilon
$$
且$f_n$在$A_\epsilon$上一致收敛于$f$。

**定理4.5	Lusin定理**：如果$f$是定义在可测集合$E$上的有限值可测函数，其中$m(E)<\infty$，那么对于任意$\varepsilon>0$，存在闭集$F_\varepsilon\sub E$，使得成立
$$
m(E-F_\varepsilon)\le\varepsilon
$$
且$f$在$F_\varepsilon$上是连续的。

## 5	Brunn-Minkowski不等式

**可测集合的加法(the sum of two measurable sets)**：对于可测集合$A$和$B$，定义其加法为
$$
A+B=\{ x'+x'':x'\in A,x''\in B \}
$$

**定理5.1	Brunn-Minkowski不等式(the Brunn-Minkowski inequality)**：对于$\R^d$中的可测集合$A$和$B$，如果$A+B$是可测的，那么成立
$$
m(A+B)^{\frac{1}{d}}\ge m(A)^{\frac{1}{d}}+m(B)^{\frac{1}{d}}
$$

# 二、积分理论

## 1	Lebesgue积分：基本性质和收敛定理

### 1.1	第一步：简单函数

**简单函数的Lebesgue积分(Lebesgue integral of the simple function)**：对于标准形式的简单函数
$$
f=\sum_{k=1}^{n}{a_k\chi_{E_k}}
$$
其中$a_1,\cdots,a_n\in\R$，$E_1,\cdots,E_n\in\mathscr{M}$两两无交，且对于任意$k=1,\cdots,n$，成立
$$
m(E_k)<\infty
$$
定义Lebesgue积分为
$$
\int{\varphi}=\int_{\R^d}{\varphi(x)\mathrm{d}x}=\sum_{k=1}^{n}{a_k m(E_k)}
$$
特别的，如果$E$为可测集合，定义
$$
\int_E{\varphi}=\int_{E}{\varphi(x)\mathrm{d}x}=\int_{\R^d}{\varphi(x)\chi_E(x)\mathrm{d}x}
$$

**命题1.1**：

- **唯一性(independence of the representation)**：对于简单函数的任意表示
  $$
  f=\sum_{k=1}^{n}{a_k\chi_{E_k}}
  $$
  成立
  $$
  \int{\varphi}=\sum_{k=1}^{n}{a_k m(E_k)}
  $$

- **线性(linearity)**：对于简单函数$\varphi$和$\psi$，及任意$a,b\in\R$，成立
  $$
  \int{(a\varphi+b\psi)}=a\int{\varphi}+b\int{\psi}
  $$

- **可加性(additivity)**：对于简单函数$\varphi$和有限测度无交集合$E$和$F$，成立
  $$
  \int_{E\cup F}{\varphi}=\int_E{\varphi}+\int_F{\varphi}
  $$
  
- **单调性(monotonicity)**：对于简单函数$\varphi$和$\psi$，如果
  $$
  \varphi\le \psi
  $$
  那么
  $$
  \int{\varphi}\le\int{\psi}
  $$

- **三角不等式(triangle inequality)**：如果$\varphi$为简单函数，那么$|\varphi|$为简单函数，且
  $$
  \left|\int{\varphi}\right|\le\int{|\varphi|}
  $$

- 如果$\varphi=\psi$几乎处处成立，那么
  $$
  \int{\varphi}=\int{\psi}
  $$

### 1.2	第二步：受有限测度集合上支持的有界函数

**支集(support)**：对于可测函数$f$，定义其支集为
$$
\mathrm{supp}(f)=\{ x:f(x)\ne 0 \}
$$
称$f$受$E$支持，如果对于任意$x\notin E$，成立$f(x)=0$。

**引理1.2**：对于受$E$支持的有限测度有界函数，如果$\{ \varphi_n \}_{n\in\N^*}$是任意在$E$上被支持的一致有界简单函数序列并且几乎处处成立$\varphi_n\to f$，那么

- 极限
  $$
  \lim_{n\to\infty}{\int{\varphi_n}}
  $$
  存在。

- 如果几乎处处成立$f=0$，那么
  $$
  \lim_{n\to\infty}{\int{\varphi_n}}=0
  $$

**受有限测度集合上支持的有界函数的Lebesgue积分(Lebesgue integral of the bounded functions that are supported on sets of finite measure)**：对于受有限测度集合上支持的有界函数$f$，定义其Lebesgue积分为
$$
\int{f}=\lim_{n\to\infty}{\int{\varphi_n}}
$$
其中$\{ \varphi_n \}_{n\in\N^*}$是一致绝对有界且任意$\varphi_n$受$f$支集支持的任意简单函数序列，并且当$n\to\infty$时几乎处处成立$\varphi_n\to f$。

对于$\R^d$上的有限测度集合$E$，以及$f$是有界且支集的测度有限的函数，定义
$$
\int_E{f}=\int{f\chi_E}
$$
**命题1.3**：对于受有限测度集合支持的有界函数$f$和$g$，成立以下命题。

- **线性(linearity)**：对于任意$a,b\in\R$，成立
  $$
  \int(af+bg)=a\int{f}+b\int{g}
  $$

- **可加性(additivity)**：对于无交集合$E$和$F$，成立
  $$
  \int_{E\cup F}{f}=\int_E f+\int_F f
  $$

- **单调性(monotonicity)**：如果$f \le g$，那么
  $$
  \int{f}\le \int{g}
  $$

- **三角不等式(triangle inequality)**：如果$|f|$也是受有限测度集合支持的有界函数，那么
  $$
  \left|\int{f}\right|\le\int{|f|}
  $$
  
---

**定理1.4	有界收敛定理(bounded convergence theorem)**：对于一致有界且受有限测度集合$E$支持的可测函数序列$\{ f_n \}_{n\in\N^*}$，如果当$n\to\infty$时，几乎处处成立$f_n\to f$，那么$f$几乎处处是受$E$支持的有界可测函数，并且当$n\to\infty$时，成立
$$
\int{\left| f_n-f \right|}\to0
$$
因此当$n\to\infty$时，成立
$$
\int{f_n}\to\int{f}
$$

### 1.3	回至Riemann可积函数

**定理1.5**：如果$f$在闭区间$[a,b]$是Riemann可积的，那么$f$是可测的，且
$$
\int_{[a,b]}^{\mathcal{R}}{f(x)\mathrm{d}x}=\int_{[a,b]}^{\mathcal{L}}{f(x)\mathrm{d}x}
$$
其中左边是标准Riemann积分，右边是Lebesgue积分。

### 1.4	第三步：非负函数

如果$f$发散至$\infty$，称其收敛于$\infty$。

**非负函数的Lebesgue积分(Lebesgue integral of the non-negative function)**：对于可测非负函数$f$，定义其Lebesgue积分为
$$
\int{f}=\sup_{g}{\int{g}}
$$
其中$g$是满足$0\le g\le f$的受有限测度集合支持的有界函数。

对于$\R^d$上的任意可测集合$E$，并且$f\ge 0$，定义
$$
\int_E{f}=\int{f\chi_E}
$$

**命题1.6**：

- **线性(linearity)**：如果$f,g\ge0$，那么对于任意$a,b\in\R^+$，成立
  $$
  \int(af+bg)=a\int{f}+b\int{g}
  $$

- **可加性(additivity)**：对于无交集合$E$和$F$，以及非负函数$f$，成立
  $$
  \int_{E\cup F}{f}=\int_E f+\int_F f
  $$

- **单调性(monotonicity)**：如果$0\le f\le g$，那么
  $$
  \int{f}\le \int{g}
  $$

- 如果$g$是可积的且$0\le f\le g$，那么$f$是可积的。

- 如果$f$是可积的，那么对于几乎任意的$x$，成立$f(x)<\infty$。

- 如果$\int{f}=0$，那么对于几乎任意的$x$，成立$f(x)=0$。

---

**引理1.7	Fatou引理**：对于非负可测函数序列$\{ f_n \}_{n\in\N^*}$，如果几乎处处成立
$$
\lim_{n\to\infty}{f_n}=f
$$
那么
$$
\int{f}\le\liminf_{n\to\infty}{\int{f_n}}
$$

**推论1.8**：对于非负可测函数$f$，以及非负可测函数序列$\{ f_n \}_{n\in\N^*}$，如果对于任意$n\in\N^*$，成立$f_n\le f$，且当$n\to\infty$时，几乎处处成立
$$
f_n\to f
$$
那么
$$
\lim_{n\to\infty}{\int{f_n}}=f
$$

**推论1.9	单调收敛定理(monotone convergence theorem)**：对于非负可测函数序列$\{ f_n \}_{n\in\N^*}$，如果$f_n\nearrow f$，那么
$$
\lim_{n\to\infty}{\int{f_n}}=\int{f}
$$
其中$f_n\nearrow f$表示对于任意$n\in\N^*$，几乎处处成立
$$
f_n\le f_{n+1}
$$
以及几乎处处成立
$$
\lim_{n\to\infty}{f_n}=f
$$

**推论1.10**：对于级数$\sum_{n=1}^{\infty}{f_n}$，如果对于任意$n\in\N^*$，$f_n$为非负可测函数，那么
$$
\int{\sum_{n=1}^{\infty}{f_n}}=\sum_{n=1}^{\infty}{\int{f_n}}
$$
并且如果$\sum_{n=1}^{\infty}{\int{f_n}}$收敛，那么级数$\sum_{n=1}^{\infty}{f_n}$几乎处处收敛。

### 1.5	第四步：一般情况

**Lebesgue可积(Lebesgue integrable)**：对于定义在$\R^d$上的实值函数$f$，称$f$是Lebesgue可积的，如果非负函数$|f|$是Lebesgue可积的。

**Lebesgue积分(Lebesgue integral)**：对于定义在$\R^d$上的实值函数$f$，定义其Lebesgue积分为
$$
\int{f}=\int{f^+}-\int{f^-}
$$
其中
$$
f^+=\max(f,0),\qquad f^-=\max(-f,0)
$$

**命题1.11**：Lebesgue积分满足**线性(linear)**，**可加性(additive)**，**单调性(monotonicity)**和**三角不等式(triangle inequality)**。

**命题1.12**：如果$f$是$\R^d$上的可积函数，那么对于任意$\varepsilon>0$，成立

- 存在有限测度集合$B$，使得成立
  $$
  \int_{B^c}{|f|}<\varepsilon
  $$

- **绝对连续性(absolute continuity)**：存在$\delta>0$，使得当$m(E)<\delta$时，成立
  $$
  \int_E{|f|}<\varepsilon
  $$
  

**定理1.13	控制收敛定理(dominated convergence theorem)**：对于可测函数序列$\{ f_n \}_{n\in\N^*}$，如果当$n\to\infty$时，几乎处处成立$f_n\to f$，且存在非负可积函数$g$，使得对于任意$n\in\N^*$，成立$|f_n|\le g$，那么当$n\to\infty$时，成立
$$
\int{\left| f_n-f \right|}\to0
$$
因此当$n\to\infty$时，成立
$$
\int{f_n}\to\int{f}
$$

### 1.6	复值函数

定义在$\R^d$上的复值函数可以写成
$$
f=u+iv
$$

**Lebesgue可积(Lebesgue integrable)**：对于定义在$\R^d$上的复值函数$f=u+iv$，称$f$是Lebesgue可积的，如果实值函数$|f|=\sqrt{u^2+v^2}$是Lebesgue可积的。

**Lebesgue积分(Lebesgue integral)**：对于定义在$\R^d$上的复值值函数$f=u+iv$，定义其Lebesgue积分为
$$
\int{f}=\int{u}+i\int{v}
$$

## 2	可积函数的$L^1$空间

### 2.1	$L^1$空间

**范数(norm)**：对于定义在$\R^d$上的可积函数$f$，定义其范数为
$$
\Vert f \Vert=\int{|f|}
$$
**$L^1$空间	$L^1$ Space**：记等价类$f\sim g$为几乎处处成立$f=g$，那么称具有上述范数的所有可积函数的等价类为$L^1$空间，记作$L^1(\R^d)$。

**命题2.1**：对于$f,g\in L^1(\R^d)$

- 对于任意$z\in\C$，成立$\Vert zf \Vert=|z|\Vert f\Vert$。

- $$
  \Vert f+g\Vert\le\Vert f\Vert+\Vert g\Vert
  $$

- $\Vert f \Vert=0$当且仅当几乎处处成立$f=0$。

- $d(f,g)=\Vert f-g\Vert$定义了$L^1(\R^d)$上的度量。

**定理2.2	Riesz-Fischer定理**：向量空间$L^1$关于度量$d$是完备的，即对于Cauchy序列封闭。

**推论2.3**：如果函数序列$\{ f_n \}_{n\in\N^*}$在$L^1$中收敛于$f$，那么存在子序列$\{ f_{n_k} \}_{k\in\N^*}$，使得几乎处处成立
$$
f_{n_k}\to f
$$

---

**稠密(dense)**：称可积函数族$\mathcal{G}$为稠密的，如果对于任意$f\in L^1$和任意$\varepsilon>0$，存在$g\in\mathcal{G}$，使得成立
$$
\Vert f-g \Vert<\varepsilon
$$
**定理2.4**：下列函数族在$L^1(\R^d)$中是稠密的。

- 简单函数族
- 阶跃函数族
- 受紧集支持的连续函数

### 2.2	不变性

**平移不变性(translation-invariance)**：对于定义在$\R^d$上的函数$f(x)$，如果$f(x)$是可积的，那么对于任意$h\in\R^d$，$f_h(x)=f(x-h)$也是可积的，并且
$$
\int{f(x-h)}=\int{f(x)}
$$

**膨胀不变性(dilation-invariance)**：对于定义在$\R^d$上的函数$f(x)$，如果$f(x)$是可积的，那么对于任意$\delta\in\R^+$，$f(\delta x)$也是可积的，并且
$$
\delta^d\int{f(\delta x)}=\int{f(x)}
$$
**反射不变性(reflection-invariant)**：对于定义在$\R^d$上的函数$f(x)$，如果$f(x)$是可积的，那么$f(-x)$也是可积的，并且
$$
\int{f(-x)}=\int{f(x)}
$$

### 2.3	平移与连续性

**命题2.5**：对于$f\in L^1(\R^d)$，那么当$h\to 0$时，成立
$$
\Vert f_h-f \Vert\to 0
$$

## 3	Fubini定理

**切片(slices)**：对于$x\in\R^{d_1},y\in\R^{d_2}$，称如下为定义在$\R^{d_1}\times\R^{d_2}$上的函数$f$的分别关于$y$和$x$的切片
$$
f^y(x)=f(x,y),\qquad f_x(y)=f(x,y)
$$
同样对于$E\sub\R^{d_2}\times\R^{d_2}$，定义其切片为
$$
E^y=\{ x\in\R^{d_1}:(x,y)\in E \},\qquad E_x=\{ y\in\R^{d_2}:(x,y)\in E \}
$$

### 3.1	定理的陈述和证明

**定理3.1	Fubini定理**：如果$f(x,y)$在$\R^d=\R^{d_1}\times\R^{d_2}$上是可积的，那么对于几乎任意的$y\in\R^{d_2}$，成立

- 切片$f^y$在$\R^{d_1}$上是可积的。

- 函数$\int_{\R^{d_1}}{f^y(x)\mathrm{d}x}$在$\R^{d_2}$上是可积的。

- $$
  \int_{\R^{d_2}}{\left( \int_{\R^{d_1}}{f(x,y)\mathrm{d}x} \right)\mathrm{d}y}=\int_{\R^d}{f}
  $$

### 3.2	Fubini定理的应用

**定理3.2	Tonelli定理**：如果$f(x,y)$在$\R^d=\R^{d_1}\times\R^{d_2}$上是非负可测的，那么对于几乎任意的$y\in\R^{d_2}$，成立

- 切片$f^y$在$\R^{d_1}$上是可测的。

- 函数$\int_{\R^{d_1}}{f^y(x)\mathrm{d}x}$在$\R^{d_2}$上是可测的。

- 在广义实数域$\overline{\R}$上成立
  $$
  \int_{\R^{d_2}}{\left( \int_{\R^{d_1}}{f(x,y)\mathrm{d}x} \right)\mathrm{d}y}=\int_{\R^d}{f(x,y)\mathrm{d}x\mathrm{d}y}
  $$

**推论3.3**：如果$E\sub\R^{d_1}\times\R^{d_2}$是可测的，那么对于几乎任意的$y\in\R^{d_2}$，切片
$$
E^y=\{ x\in\R^{d_1}:(x,y)\in E \}
$$
是$\R^{d_1}$上的可测集合，同时$m(E^y)$是关于$y$的可测函数，并且
$$
m(E)=\int_{\R^{d_2}}{m(E^y)\mathrm{d}y}
$$

---

**命题3.4**：如果$E=E_1\times E_2\sub\R^d$是可测的，且$m_*(E_2)>0$，那么$E_1$是可测的。

**推论3.5**：如果$E_1\sub\R^{d_1}$且$E_2\sub\R^{d_2}$，那么
$$
m_*(E_1\times E_2)\le m_*(E_1)m_*(E_2)
$$

**命题3.6**：如果$E_1\sub\R^{d_1}$和$E_2\sub\R^{d_2}$是可测的，那么$E=E_1\times E_2\sub\R^d$是可测的，并且
$$
m(E_1\times E_2)=m(E_1)m(E_2)
$$

**推论3.7**：如果函数$f$在$\R^{d_1}$上是可测的，那么函数$\tilde{f}(x,y)=f(x)$在$\R^{d_1}\times\R^{d_2}$上是可测的。

**推论3.8**：如果函数$f$在$\R^{d}$上是非负的，且
$$
\mathcal{A}=\{ (x,y)\in\R^{d}:0\le y\le f(x) \}
$$
那么

- $f$在$\R^{d}$上是可测的，当且仅当$\mathcal{A}$在$\R^{d+1}$是可测的。

- 如果$f$在$\R^{d}$上是可测的，那么
  $$
  \int_{\R^{d}}{f(x)\mathrm{d}x}=m(\mathcal{A})
  $$

**命题3.9**：如果函数$f$在$\R^{d}$上是可测的，那么函数$\tilde{f}(x,y)=f(x-y)$在$\R^{d}\times\R^{d}$上是可测的。

## 4	Fourier反演公式

**Fourier反演公式(Fourier inversion formula)**：
$$
\hat{f}(\xi)=\int_{\R^d}{f(x)\mathrm{e}^{-2\pi i  \xi x}\mathrm{d}x}
$$
$$
f(x)=\int_{\R^d}{\hat{f}(\xi)\mathrm{e}^{-2\pi i x \xi}\mathrm{d}\xi}
$$

**命题4.1**：如果$f\in L^1(\R^d)$，那么$\hat{f}$在$\R^d$是连续且有界的。

**定理4.2**：如果$f\in L^1(\R^d)$且$\hat{f}\in L^1(\R^d)$，那么对于任意的$x$，成立
$$
f(x)=\int_{\R^d}{\hat{f}(\xi)\mathrm{e}^{-2\pi i x \xi}\mathrm{d}\xi}
$$

**推论4.3**：如果对于任意$\xi\in\R^{d}$，成立$\hat{f}(\xi)=0$，那么几乎处处成立$f=0$。

**引理4.4**：如果$f,g\in L^1(\R^d)$，那么
$$
\int_{\R^d}{\hat{f}(x)g(x)\mathrm{d}x}=\int_{\R^d}f(x){\hat{g}(x)\mathrm{d}x}
$$

# 三、微分和积分

## 1	积分的微分

### 1.1	Hardy-Littlewood极大函数

**极大函数(maximal function)**：对于定义在$\R^d$上的可积函数$f$，定义其在可测集$B$上的极大函数为
$$
f^*(x)=\sup_{x\in B}{\frac{1}{m(B)}\int_{B}{|f(y)|\mathrm{d}y}}
$$

**定理1.1**：对于定义在$\R^d$上的可积函数$f$，那么

- $f^*$为可积的。

- 对于几乎任意的$x\in\R^d$，成立$f^*(x)<\infty$。

- **弱不等式(weak-type inequality)**：对于任意$\alpha>0$，成立
  $$
  m(\{ x\in\R^d:f^*(x)>\alpha \})\le\frac{3^d}{\alpha}\Vert f \Vert_{L^1(\R^d)}
  $$
  其中
  $$
  \Vert f \Vert_{L^1(\R^d)}=\int_{\R^d}{|f(x)|\mathrm{d}x}
  $$

**引理1.2	Vitali覆盖论证(Vitali covering argument)**：如果$\mathcal{B}=\{ B_1,\cdots,B_n \}$为$\R^d$中的有限开集族，那么存在不相交的子开集$B_{i_1},\cdots,B_{i_k}$，使得成立
$$
m\left( \bigcup_{j=1}^{n}{B_j} \right)\le 3^d\sum_{j=1}^{k}{m(B_{i_j})}
$$

### 1.2	Lebesgue微分定理

**定理1.3	Lebesgue微分定理(The Lebesgue differentiation theorem)**：如果$f\in L^1(\R^d)$，那么对于几乎任意的$x\in\R^d$，成立
$$
\lim_{\substack{m(B)\to0\\x\in B}}{\frac{1}{m(B)}\int_{B}{f(y)\mathrm{d}y}}=f(x)
$$
**局部可积(locally integrable)**：定义在$\R^d$上的函数$f$，称$f$是局部可积的，如果对于任意球$B\in\R^d$，函数$f\chi_{B}$是可积的。

**定理1.4**：如果$f\in L^1_{\mathrm{loc}}(\R^d)$，那么对于几乎任意的$x\in\R^d$，成立
$$
\lim_{\substack{m(B)\to0\\x\in B}}{\frac{1}{m(B)}\int_{B}{f(y)\mathrm{d}y}}=f(x)
$$

**Lebesgue密度点(a point of Lebesgue density)**：对于可测集$E$，称$x\in\R^d$为$E$的Lebesgue密度点，如果成立
$$
\lim_{\substack{m(B)\to0\\x\in B}}{\frac{m(B\cap E)}{m(B)}}=1
$$

**推论1.5**：如果$E\sub\R^d$为可测集，那么

- 对于几乎任意$x\in E$，$x$都是$E$的密度点。
- 对于几乎任意$x\notin E$，$x$都不是$E$的密度点。

**Lebesgue集(Lebesgue set)**：对于$f\in L^1_{\mathrm{loc}}(\R^d)$，$f$的Lebesgue集定义为
$$
\left\{ x\in\R^d:\lim_{\substack{m(B)\to0\\x\in B}}{\frac{1}{m(B)}\int_{B}{|f(y)-f(x)|\mathrm{d}y}}=0 \right\}
$$

- 如果$f$在$x$点处连续，那么$x$在其Lebesgue集中。

- 如果$x$在$f$的Lebesgue集中，那么
  $$
  \lim_{\substack{m(B)\to0\\x\in B}}{\frac{1}{m(B)}\int_{B}{f(y)\mathrm{d}y}}=f(x)
  $$

**推论1.6**：如果$f\in L^1_{\mathrm{loc}}(\R^d)$，那么对于几乎任意的$x\in\R^d$，$x$都在$f$的Lebesgue集中。

---

**规律收缩(shrink regularly)/有限偏心(bounded eccentricity)**：称集族$\{ U_\alpha \}$为规律收缩至$x$点或在$x$点处为有限偏心的，如果存在常数$c>0$，使得对于任意$U_\alpha$，存在球$B$，成立
$$
x\in B,\qquad U_\alpha\sub B,\qquad m(U_\alpha)\ge cm(B)
$$

**推论1.7**：如果$f\in L^1_{\mathrm{loc}}(\R^d)$，并且对于几乎任意的$f$的Lebesgue集中的点$x$，集族$\{ U_\alpha \}$规律收缩至$x$，那么
$$
\lim_{\substack{m(U_\alpha)\to0\\x\in U_\alpha}}{\frac{1}{m(U_\alpha)}\int_{U_\alpha}{f(y)\mathrm{d}y}}=f(x)
$$

## 2	良核和恒等近似

**核函数(kernel)**及其与函数的卷积：对于核$K_\delta$，记其与可积函数$f$的**卷积(convolution)**为
$$
(f* K_\delta)(x)=\int_{\R^d}{f(x-y)K_\delta(y)\mathrm{d}y}
$$

**良核(good kernel)**：称核$K_\delta$为良核，如果其可积，并且对于$\delta>0$，成立

- $$
  \int_{\R^d}{K_\delta(x)\mathrm{d}x}=1
  $$

- 存在与$\delta$有关的常数$A>0$，使得成立
  $$
  \int_{\R^d}{|K_\delta(x)|\mathrm{d}x}\le A
  $$

- 对于任意$\eta>0$，成立
  $$
  \lim_{\delta\to0}{\int_{|x|\ge\eta}{|K_\delta(x)|\mathrm{d}x}}=0
  $$

**良核的性质**：对于有界函数$f$的任意连续点$x$处，成立
$$
\lim_{\delta\to0}{(f* K_\delta)(x)}=f(x)
$$

良核定义的**加强**：称核$K_\delta$为良核，如果其可积，且$\delta>0$，同时成立

- $$
  \int_{\R^d}{K_\delta(x)\mathrm{d}x}=1
  $$

- 存在$A>0$，使得成立
  $$
  |K_\delta(x)|\le A\delta^{-d}
  $$

- 对于任意$x\in\R^d$，存在$A>0$，使得成立
  $$
  |K_\delta(x)|\le\frac{A\delta}{|x|^{d+1}}
  $$
  

---

**恒等近似(approximation to the identity)**：称$K_\delta$为$f$的恒等近似，如果当当$\delta\to0$时，成立
$$
f* K_\delta\to f
$$
此定义来自如下事实：当$\delta\to0$时，映射$f\mapsto f* K_\delta$趋于恒等映射$f\mapsto f$。

**Dirac $\delta$函数**：对于$\delta>0$，定义函数
$$
K_\delta(x)=\begin{cases}
\frac{1}{2\delta},\quad & x\in[-\delta,\delta]\\
0,\quad & x\in(-\infty,-\delta)\cup(\delta,\infty)
\end{cases}
$$
那么（不严格的）定义Dirac $\delta$函数为
$$
\mathcal{D}=\lim_{\delta\to 0^+}{K_\delta}
$$
事实上，Dirac $\delta$函数为
$$
\mathcal{D}(x)=\begin{cases}
\infty,\quad & x=0\\
0,\quad & x\ne0
\end{cases},\qquad
\int_{\R}{\mathcal{D}(x)\mathrm{d}x}=1
$$

**Dirac $\delta$函数的卷积恒等性(the identity for convolutions)**：
$$
f*\mathcal{D}=f
$$

---

**定理2.1**：如果$\{ K_\delta \}_{\delta>0}$是恒等函数的近似，且$f$在$\R^d$上可积，那么当$\delta\to0$时，对于$f$的Lebesgue集中的点（特别的，几乎任意的$\R^d$中的点）处，成立
$$
f* K_\delta\to f
$$

**引理2.2**：如果$f$在$\R^d$上可积，如果对于$f$的Lebesgue集中的点$x$处，令
$$
\mathcal{A}(r)=\frac{1}{r^d}\int_{|y|\le r}{|f(x-y)-f(x)|\mathrm{d}y},\quad r>0
$$
那么$\mathcal{A}$连续且有界，同时
$$
\lim_{r\to0}{\mathcal{A}(r)}=0
$$

**定理2.3**：如果$\{ K_\delta \}_{\delta>0}$是恒等函数的近似，且$f$在$\R^d$上可积，那么卷积$f* K_\delta$是可积的，并且当$\delta\to0$时，成立
$$
\Vert f* K_\delta-f \Vert_{L^1(\R^d)}\to0
$$

## 3	函数的微分

### 3.1	有界变差函数

**划分(partitions)**：对于区间$[a,b]$，称其一个划分为
$$
a=t_0<\cdots<t_n=b,\quad \forall n\in\N^*
$$
区间$[a,b]$的所有划分记为集合$\mathcal{P}[a,b]$。

**可求长的(rectifiable)**：对于$\R^2$上的曲线$\gamma:z(t)=(x(t),y(t))$，其中$t\in[a,b]$且$x(t)$和$y(t)$为在$[a,b]$上的连续实值函数，称曲线$\gamma$为可求长的，如果对于$[a,b]$的任意划分$\mathcal{P}\in\mathcal{P}[a,b]$，存在$M<\infty$，使得成立
$$
\sum_{k=1}^{n}{|z(t_k)-z(t_{k-1})|}\le M
$$

其中对于任意$k\in\{ 1,\cdots,n \}$，$|z(t_k)-z(t_{k-1})|$定义为两点$z(t_k)$和$z(t_{k-1})$的距离。

**曲线长(length)**：如果曲线$\gamma:z(t)=(x(t),y(t))$为可求长的，其中$t\in[a,b]$，定义其曲线长为
$$
\ell(\gamma)=\sup_{\mathcal{P}[a,b]}{\sum_{k=1}^{n}{|z(t_k)-z(t_{k-1})|}}
$$
对于$a\le A\le B\le b$，定义
$$
\ell(A,B)=\sup_{\mathcal{P}[A,B]}{\sum_{k=1}^{n}{|z(t_k)-z(t_{k-1})|}}
$$
容易知道$\ell(A,B)$是连续函数，且关于$A$单调递减，关于$B$单调递增。

**变差(variation)**：对于定义在$[a,b]$上的复值连续函数$F(t)$，定义其关于划分$\mathcal{P}\in\mathcal{P}[a,b]$的变差为
$$
\sum_{k=1}^{n}{|F(t_k)-F(t_{k-1})|}
$$
**有界变差(bounded variation)**：对于定义在$[a,b]$上的复值连续函数$F(t)=x(t)+iy(t)$，称函数$F$为有界变差的，如果对于$[a,b]$的任意划分$\mathcal{P}\in\mathcal{P}[a,b]$，存在$M<\infty$，使得成立
$$
\sum_{k=1}^{n}{|F(t_k)-F(t_{k-1})|}\le M
$$

- 实值单调且有界函数是有界变差的。
- 导函数有界的函数是有界变差的。

**定理3.1**：定义在$[a,b]$上的曲线$(x(t),y(t))$是可求长的，当且仅当$x(t)$和$y(t)$为有界变差的。

---

**总变差(total variation)**：函数$F$定义在$[a,x]\sub[a,b]$上的总变差定义为
$$
T_F(a,x)=\sup_{\mathcal{P}[a,x]}{\sum_{k=1}^{n}{|F(t_k)-F(t_{k-1})|}}
$$

- 如果一个有界变差函数是连续的，那么其总变差也是连续的。

**正变差(positive variation)**：函数$F$定义在$[a,x]\sub[a,b]$上的正变差定义为
$$
P_F(a,x)=\sup_{\mathcal{P}[a,x]}{\sum_{F(t_k)\ge F(t_{k-1})}{F(t_k)-F(t_{k-1})}}
$$

**负变差(negative variation)**：函数$F$定义在$[a,x]\sub[a,b]$上的负变差定义为
$$
N_F(a,x)=\sup_{\mathcal{P}[a,x]}{\sum_{F(t_k)\ge F(t_{k-1})}{F(t_k)-F(t_{k-1})}}
$$

**引理3.2**：如果$F$是定义在$[a,b]$上的实值有界变差函数，那么对于任意$x\in[a,b]$，成立
$$
F(x)-F(a)=P_F(a,x)-N_F(a,x)
$$
$$
T_F(a,x)=P_F(a,x)+N_F(a,x)
$$

**定理3.3**：实值函数$F$在$[a,b]$上是有界变差的，当且仅当$F$是两个单调递增有界函数的差。

---

**定理3.4**：如果$F$在$[a,b]$上是有界变差的，那么$F$几乎处处可微。

**引理3.5	旭日引理(rising sun lemma)**：对于定义在$\R$上的实值连续函数$G$，记
$$
E=\{ x\in\R:G(x+h)>G(x),\quad \exist h=h_x>0 \}
$$
如果$E$非空，那么$E$为开集，于是$E$可以表示为可数个不交有限开集的并
$$
E=\bigcup_{n=1}^{\infty}{(a_n,b_n)}
$$
如果$(a_n,b_n)$为有限开区间，那么
$$
G(a_n)=G(b_n)
$$

**推论3.6**：对于定义在$[a,b]$上的实值连续函数$G$，记
$$
E=\{ x\in\R:G(x+h)>G(x),\quad \exist h>0 \}
$$
那么或$E$为空，或$E$为开。如果$E$为开集，那么$E$可以表示为可数个不交有限开集的并
$$
E=\bigcup_{n=1}^{\infty}{(a_n,b_n)}
$$
那么当$a_n\ne a$时，成立
$$
G(a_n)=G(b_n)
$$
当$a_n=a$时，成立
$$
G(a_n)\le G(b_n)
$$

**Dini导数**：定义
$$
\Delta_hF(x)=\frac{F(x+h)-F(x)}{h}
$$
定义Dini导数为
$$
D^+F(x)=\limsup_{h\to0^+}{\Delta_hF(x)}
$$

$$
D_+F(x)=\liminf_{h\to0^+}{\Delta_hF(x)}
$$

$$
D^-F(x)=\limsup_{h\to0^-}{\Delta_hF(x)}
$$

$$
D_-F(x)=\liminf_{h\to0^-}{\Delta_hF(x)}
$$

**Dini引理**：如果$F$在$[a,b]$上是单调递增的有界连续函数，那么对于几乎任意的$x\in[a,b]$，成立
$$
D^+F(x)<\infty
$$

$$
D^+F(x)\le D_-F(x)\iff D^-F(x)\le D_+F(x)
$$

**推论3.7**：如果$F$单调递增且连续，那么$F$几乎处处可微，同时$F'$可测，且
$$
\int_a^b{F'(x)\mathrm{d}x}\le F(b)-F(a)
$$
特别的，如果$F$在$\R$上有界，那么$F'$在$\R$上可积。

---

**Cantor-Lebesgue函数**：对于Cantor集
$$
\mathcal{C}=\bigcap_{n=1}^{\infty}{C_n}
$$
其中
$$
C_n=\bigcup_{k=1}^{2^n}{[a_{k}^{(n)},b_{k}^{(n)}]}
$$
记
$$
F_n(x)=\begin{cases}
\frac{3^n}{2^n}(x-ka_{k}^{(n)}+(k-1)b_{k}^{(n)}),\quad & x\in[a_{k}^{(n)},b_{k}^{(n)}],1\le k\le 2^n\\
\frac{k}{2^n},\quad & x\in[b_k^{(n)},a_{k+1}^{(n)}],1\le k\le 2^n-1
\end{cases}
$$
定义Cantor-Lebesgue函数为
$$
F=\lim_{n\to\infty}{F_n}
$$

- $$
  F:[0,1]\to[0,1]
  $$

- $$
  F(0)=1,\qquad F(1)=1
  $$

- $F$连续且单调递增。

- 几乎处处成立$F'=0$。

- $F$为有界变差的。

- $$
  \int_a^b{F'(x)\mathrm{d}x}\ne F(b)-F(a)
  $$

### 3.2	绝对连续函数

**绝对连续(absolutely continuous)**：称定义在$[a,b]$上的函数$F$为绝对连续的，如果对于任意$\varepsilon>0$，存在$\delta>0$，使得对于满足
$$
\sum_{k=1}^{n}{(b_k-a_k)}<\delta
$$
的任意不交开区间族$\{(a_k,b_k)\}_{k=1}^{n}$，成立
$$
\sum_{k=1}^{n}{|F(b_k)-F(a_k)|}<\varepsilon
$$

- 绝对连续函数是一致连续的，进而是连续的。

- 有界区间上的绝对连续函数是有界变差的，且其总变差是绝对连续的。

- 对于可积函数$f$，积分函数$F(x)=\int_a^x{f(y)\mathrm{d}y}$是绝对连续的。

**定理3.8**：如果$F$在$[a,b]$上是绝对连续的，那么$F'$几乎处处存在。此外，如果几乎处处成立$F'=0$，那么$F$为常函数。

**Vitali覆盖(Vitali covering)**：称球集族$\mathcal{B}$为集合$E$的Vitali覆盖，如果对于任意$x\in E$以及任意$\eta>0$，存在球$B\in\mathcal{B}$，使得满足$x\in B$且$m(B)<\eta$。

**引理3.9	Vitali覆盖论证(Vitali covering argument)**：如果$E$为有限测度集，且$\mathcal{B}$为$E$的Vitali覆盖，那么对于任意$\delta>0$，存在有限多个不交球$B_1,\cdots,B_n\in\mathcal{B}$，使得成立
$$
\sum_{k=1}^{n}{m(B_k)}\ge m(E)-\delta
$$

**推论3.10**：如果$E$为有限测度集，且$\mathcal{B}$为$E$的Vitali覆盖，那么对于任意$\delta>0$，存在有限多个不交球$B_1,\cdots,B_n\in\mathcal{B}$，使得成立
$$
m(E-\bigcup_{k=1}^{n}{B_k})<2\delta
$$

**定理3.11**：如果$F$是$[a,b]$上的绝对连续函数，那么几乎处处存在$F'$，同时$F'$可积，且对于任意$x\in[a,b]$，成立
$$
F(x)-F(a)=\int_a^x{F'(y)\mathrm{d}y}
$$
反之，如果$f$在$[a,b]$上可积，那么存在绝对连续函数$F$，使得几乎处处成立$F'=f$。事实上，取
$$
F(x)=\int_a^x{F'(y)\mathrm{d}y}
$$

### 3.3	跳跃函数的可微性

**引理3.12**：有界单调函数$F$在闭区间$[a,b]$上存在至多可数个不连续点。

**跳跃函数(jump function)**：对于定义在闭区间$[a,b]$上有界单调递增函数$F$，记其不连续点序列为$\{ x_n \}_{n=1}^{\infty}$，定义
$$
\alpha_n=F(x_n^+)-F(x_n^-)
$$

$$
\theta_n=\frac{F(x_n)-F(x_n^-)}{\alpha_n}\in[0,1]
$$

$$
j_n(x)=\begin{cases}
0,\quad & x<x_n\\
\theta_n,\quad & x=x_n\\
1,\quad & x>x_n
\end{cases}
$$

那么定义与$F$相关的跳跃函数为
$$
J(x)=J_F(x)=\sum_{n=1}^{\infty}{\alpha_n j_n(x)}
$$

- 由于
  $$
  \sum_{n=1}^{\infty}{\alpha_n}\le F(b)-F(a)<\infty
  $$
  因此级数$J$是绝对收敛且一致收敛的。

**引理3.13**：如果$F$在区间$[a,b]$上是有界单调递增的，那么

- $F$和$J$的不连续点相同。
- 差$F-J$是单调递增且连续的。

**定理3.14**：如果$J$是定义在闭区间$[a,b]$上有界单调递增函数$F$的跳跃函数，那么$J'$几乎处处存在，且几乎处处成立$J'=0$。

## 4	可求长曲线与等周不等式

**定理4.1**：对于定义在$[a,b]$上的曲线$\gamma:(x(t),y(t))$，如果$x(t)$和$y(t)$是绝对连续的，那么曲线$\gamma$是可求长的，并且其长为
$$
\ell(\gamma)=\int_a^b{\sqrt{(x'(t))^2+(y'(t))^2}\mathrm{d}t}
$$

**命题4.2**：对于定义在$[a,b]$上的复值函数$F(t)=x(t)+iy(t)$，如果$F$是绝对连续的，那么
$$
T_F(a,b)=\int_a^b{|F'(t)|\mathrm{d}t}
$$

**弧长参数化(arc-length parametrization)**：对于定义在$[a,b]$上的可求长参数化曲线$\gamma:(x(t),y(t))$，考虑弧长参数变换
$$
s=s(t)=L(a,t),\quad s\in[0,L(\gamma)]
$$
那么定义
$$
\tilde{x}(s)=x(t),\qquad \tilde{y}(s)=y(t)
$$

**定理4.3**：对于定义在$[a,b]$上的可求长曲线$\gamma:(x(t),y(t))$，考虑弧长参数化曲线$\gamma:(\tilde{x}(s),\tilde{y}(s))$，那么$\tilde{x}$和$\tilde{y}$是绝对连续的，且几乎处处成立$(\tilde{x}'(s))^2+(\tilde{y}'(s))^2=1$，同时
$$
\ell(\gamma)=\int_0^{L(\gamma)}{\sqrt{(\tilde{x}'(s))^2+(\tilde{y}'(s))^2}\mathrm{d}t}
$$

### 4.1	曲线的Minkowski含量

**简单曲线(simple curve)**：称定义在$[a,b]$上的曲线$\gamma:z(t)=(x(t),y(t))$为简单的，如果对于任意$t\in[a,b)$，映射$t\mapsto z(t)$为单射，且$z(a)=z(b)$。

**准简单曲线(quasi-simple curve)**：称定义在$[a,b]$上的曲线$\gamma:z(t)=(x(t),y(t))$为准简单的，如果对于有限个点外，映射$t\mapsto z(t)$为单射。

**Minkowski含量(Minkowski content)**：对于紧集$K\sub\R^2$，如果存在极限
$$
\lim_{\delta\to 0^+}{\frac{m(K^\delta)}{2\delta}}
$$
那么称该极限为$K$的Minkowski含量，记作$\mathcal{M}(K)$，其中
$$
K^\delta=\{ x\in\R^2:d(x,K)<\delta \}
$$

**定理4.4**：如果定义在$[a,b]$上的曲线$\Gamma:z(t)$为准简单曲线，那么$\Gamma$存在Minkowski含量，当且仅当$\Gamma$是可求长的。在此情况，成立
$$
\mathcal{M}(\Gamma)=\ell(\Gamma)
$$

**命题4.5**：对于定义在$[a,b]$上的准简单曲线$\Gamma:z(t)$，定义
$$
M_*(\Gamma)=\liminf_{\delta\to 0^+}{\frac{m(\Gamma^\delta)}{2\delta}}
$$
如果$M_*(\Gamma)<\infty$，那么$\Gamma$是可求长的，且
$$
\mathcal{M}(\Gamma)\ge \ell(\Gamma)
$$

**引理4.6**：对于任意定义在$[a,b]$上的曲线$\Gamma:z(t)$，如果记$\Delta=|z(b)-z(a)|$，那么$m(\Gamma^\delta)\ge 2\delta\Delta$。

**命题4.7**：如果定义在$[a,b]$上的曲线$\Gamma:z(t)$是可求长的，那么定义
$$
M^*(\Gamma)=\limsup_{\delta\to 0^+}{\frac{m(\Gamma^\delta)}{2\delta}}
$$
成立
$$
\mathcal{M}(\Gamma)\le \ell(\Gamma)
$$

### 4.2	等周不等式

**定理4.8**：如果$\Omega\sub\R^2$为有界开集，且其边界$\overline{\Omega}-\Omega$为可求长曲线$\Gamma$，那么
$$
4\pi m(\Omega)\le\ell(\Gamma)^2
$$
事实上，如果$\Omega\sub\R^2$为有界开集，且其边界$\overline{\Omega}-\Omega$为曲线$\Gamma$，那么
$$
4\pi m(\Omega)\le \mathcal{M}^*(\Gamma)^2
$$

# 四、Hilbert空间：简介

## 1	Hilbert空间$L^2$

**$L^2(\R^d)$空间**：$L^2(\R^d)$空间定义为$\R^2$上**平方可积函数(square integrable functions)**的集合，即
$$
L^2(\R^d)=\left\{ f:\int_{\R^d}{|f|^2}<\infty \right\}
$$

**$L^2(\R^d)$范数(norm)**：$f\in L^2(\R^d)$的范数定义为
$$
\Vert f\Vert_{L^2(\R^d)}=\left(\int_{\R^d}{|f|^2}\right)^{\frac{1}{2}}
$$
本章如无特殊说明，以$\Vert \cdot \Vert$表示$L^2(\R^d)$范数。

**$L^2(\R^d)$内积(inner product)**：$f,g\in L^2(\R^d)$的内积定义为
$$
(f,g)=\int_{\R^d}{f\overline{g}}
$$

**命题1.1	$L^2(\R^d)$空间的性质**：
- $L^2(\R^d)$为向量空间。
- 对于任意$f,g\in L^2(\R^d)$，$f\overline{g}$可积，且成立**Cauchy-Schwarz不等式**
$$
|(f,g)|\le \Vert f\Vert\Vert g\Vert
$$
- 如果固定$g\in L^2(\R^d)$，那么映射$f\mapsto (f,g)$是线性映射，并且$(f,g)=\overline{(g,f)}$
- **三角不等式**：对于任意$f,g\in L^2(\R^d)$，成立
$$
\Vert f+g \Vert\le \Vert f \Vert+\Vert g \Vert
$$

**度量(metric)**：对于$f,g\in L^2(\R^d)$，定义其度量为
$$
d(f,g)=\Vert f-g \Vert_{L^2(\R^d)}
$$

**Cauchy序列(Cauchy sequence)**:称序列$\{ f_n \}\sub L^2(\R^d)$为Cauchy序列，如果
$$
\lim_{n,m\to\infty}{d(f_n,f_m)}=0
$$
而且，称列$\{ f_n \}\sub L^2(\R^d)$收敛于$f$，如果
$$
\lim_{n\to\infty}{d(f_n,f)}=0
$$

**定理1.2**：$L^2(\R^d)$空间是完备的，即对Cauchy序列封闭。

**定理1.3**：$L^2(\R^d)$空间是可分的，即存在可数序列$\{ f_n \}\sub L^2(\R^d)$，使得其张成的线性空间在$L^2(\R^d)$中是稠密的。

## 2	Hilbert空间

**Hilbert空间**：称集合$\mathcal{H}$为Hilbert空间，如果满足

- $\mathcal{H}$是$\C$或$\R$上的**向量空间**。

- $\mathcal{H}$具有**内积**$(\cdot,\cdot)$，使得满足

  - 给定$g\in\mathcal{H}$，映射$f\mapsto(f,g)$在$\mathcal{H}$上是线性映射。
  - $(f,g)=\overline{(g,f)}$
  - $(f,f)\ge 0$

  令$\Vert f \Vert=(f,f)^{\frac{1}{2}}$。

- $\Vert f \Vert =0$，当且仅当$f=0$。

- **Cauchy-Schwarz不等式**：
  $$
  |(f,g)|\le \Vert f\Vert\Vert g\Vert
  $$

- **三角不等式**：
  $$
  \Vert f+g \Vert\le \Vert f \Vert+\Vert g \Vert
  $$

- $\mathcal{H}$关于度量$d(f,g)=\Vert f-g \Vert$是**完备的**。

- $\mathcal{H}$是**可分的**。

### 2.1	正交性

**正交的(orthogonal)或垂直(perpendicular)**：称$f,g\in\mathcal{H}$关于内积$(\cdot,\cdot)$是正交的或垂直的，记作$f\perp g$，如果
$$
(f,g)=0
$$
称$f\in\mathcal{H}$和$\mathcal{H}\sub\mathcal{S}$关于内积$(\cdot,\cdot)$是正交的，记作$f\perp \mathcal{S}$，如果对于任意$g\in\mathcal{S}$，成立
$$
(f,g)=0
$$

**标准正交(orthonormal)**：称至多可数集合$\{ e_n \}\sub\mathcal{H}$为标准正交的，如果
$$
(e_i,e_j)=\begin{cases}
1,\quad & i=j\\
0,\quad & i\ne j
\end{cases}
$$
**Bessel不等式**：对于标准正交集合$\{ e_n \}\sub\mathcal{H}$，以及$f\in\mathcal{H}$，成立
$$
\Vert f \Vert^2\ge\sum_{n=1}^{\infty}{|(f,e_n)|^2}
$$
**标准正交基(orthonormal basis)**：称可数集合$\{ e_n \}_{n=1}^{\infty}\sub\mathcal{H}$为$\mathcal{H}$的标准正交基，如果$\{ e_n \}_{n=1}^{\infty}$的有限张成空间在$\mathcal{H}$上是稠密的。

**维度(dimension)**：称Hilbert空间$\mathcal{H}$中一组标准正交基的个数为$\mathcal{H}$的维度，记作$\dim(\mathcal{H})$。

**命题2.1	 Pythagoras定理**：如果$f\perp g$，那么
$$
\Vert f+g \Vert^2=\Vert f \Vert^2+\Vert g \Vert^2
$$

**命题2.2**：如果$\{ e_n \}\sub\mathcal{H}$是标准正交的，且$f=\sum{a_ne_n}\in\mathcal{H}$，那么
$$
\Vert f\Vert^2=\sum{|a_n|^2}
$$
事实上，对于任意$n\in\N^*$，成立$a_n=(f,e_n)$。

**定理2.3**：以下关于$\mathcal{H}$的标准正交基$\{ e_n \}_{n=1}^{\infty}$的命题等价的。

- $\{ e_n \}_{n=1}^{\infty}$的有限张成空间在$\mathcal{H}$上是稠密的。
- 如果$f\in\mathcal{H}$满足对于任意$n\in\N^*$，成立$(f,e_n)=0$，那么$f=0$。
- 对于$f\in\mathcal{H}$，如果记$S_n(f)=\sum_{k=1}^{n}{(f,e_k)e_k}$，那么
  $$
  \lim_{n\to\infty}{S_n(f)}=f
  $$
- **Parseval等式**：
  $$
  \Vert f \Vert^2=\sum_{n=1}^{\infty}{|(f,e_n)|^2}
  $$

**定理2.4**：任意Hilbert空间存在标准正交基。

### 2.2	酉映射

**酉映射(unitary mapping)**：对于两个Hilbert空间$\mathcal{H}$和$\mathcal{H}'$，定义内积分别为$(\cdot,\cdot)_{\mathcal{H}}$和$(\cdot,\cdot)_{\mathcal{H}'}$，定义范数分别为$\Vert\cdot\Vert_{\mathcal{H}}$和$\Vert\cdot\Vert_{\mathcal{H}'}$，称映射$U:\mathcal{H}\to\mathcal{H}'$为酉映射，如果满足

- 映射$U$是线性的，即$U(\alpha f+\beta g)=\alpha U(f)+\beta U(g)$。
- $U$为双射。
- 对于任意$f\in\mathcal{H}$，成立$\Vert U(f) \Vert_{\mathcal{H}'}=\Vert f \Vert_{\mathcal{H}}$，这等价于对于任意$f,g\in\mathcal{H}$，成立$(U(f),U(g))_{\mathcal{H}'}=(f,g)_{\mathcal{H}}$。

**酉等价(unitarily equivalent)或酉同构(unitarily isomorphic)**：称两个Hilbert空间$\mathcal{H}$和$\mathcal{H}'$是酉等价或酉同构，如果存在酉映射$U:\mathcal{H}\to\mathcal{H}'$。

**推论2.5**：任意两个无限维Hilbert空间是酉等价的。

**推论2.6**：两个有限维Hilbert空间是酉等价的，当且仅当其维度相等。

### 2.3	准Hilbert空间

**准Hilbert空间(pre-Hilbert space)**：称集合$\mathcal{H}_0$为准Hilbert空间，如果满足

- $\mathcal{H}_0$是$\C$或$\R$上的**向量空间**。

- $\mathcal{H}_0$具有**内积**$(\cdot,\cdot)$，使得满足

  - 给定$g\in\mathcal{H}_0$，映射$f\mapsto(f,g)$在$\mathcal{H}$上是线性映射。
  - $(f,g)=\overline{(g,f)}$
  - $(f,f)\ge 0$

  令$\Vert f \Vert=(f,f)^{\frac{1}{2}}$。

- $\Vert f \Vert =0$，当且仅当$f=0$。

- **Cauchy-Schwarz不等式**：
  $$
  |(f,g)|\le \Vert f\Vert\Vert g\Vert
  $$

- **三角不等式**：
  $$
  \Vert f+g \Vert\le \Vert f \Vert+\Vert g \Vert
  $$

- $\mathcal{H}_0$是**可分的**。

**命题2.7**：如果$\mathcal{H}_0$为具有内积$(\cdot,\cdot)_0$的准Hilbert空间，那么存在具有内积$(\cdot,\cdot)$的Hilbert空间$\mathcal{H}$，，使得成立

- $\mathcal{H}_0\sub\mathcal{H}$
- 对于任意$f,g\in\mathcal{H}_0$，成立$(f,g)_0=(f,g)$。
- $\mathcal{H}_0$在$\mathcal{H}$中是稠密的。

$\mathcal{H}$称为$\mathcal{H}_0$的**完备化**。

## 3	Fourier级数和Fatou定理

### 3.1	Fourier级数

**Fourier级数**：对于$f\in L^1([-\pi,\pi])$，定义
$$
a_n=\frac{1}{2\pi}\int_{-\pi}^{\pi}{f(x)\mathrm{e}^{-inx}\mathrm{d}x},\quad n\in\Z
$$
那么$f$的Fourier级数为
$$
f(x)\sim\sum_{n=-\infty}^{\infty}{a_n\mathrm{e}^{inx}}
$$

**定理3.1**：对于在$[-\pi,\pi]$上可积的函数$f$，成立
- 如果对于任意$n\in\Z$，成立$a_n=0$，那么几乎处处成立$f=0$。
- 几乎处处成立
  $$
  \lim_{r\to 1^-}{a_n r^{|n|}\mathrm{e}^{inx}}=f(x)
  $$

**定理3.2**：对于$f\in L^2([-\pi,\pi])$，成立

- **Parseval等式**：
  $$
  \sum_{n=-\infty}^{\infty}{|a_n|^2}=\frac{1}{2\pi}\int_{-\pi}^{\pi}{|f(x)|^2\mathrm{d}x}
  $$
- 映射如下映射为酉映射：
  $$
  \begin{align}
  U:L^2([-\pi,\pi])&\to \ell^2(\Z)\\
  U(f)&\mapsto \{a_n\}
  \end{align}
  $$
- $f$的Fourier级数以$L^2$范数收敛于$f$，即
  $$
  \lim_{n\to\infty}{\frac{1}{2\pi}\int_{-\pi}^{\pi}{|f(x)-S_n(f(x))|^2\mathrm{d}x}}
  $$
  其中
  $$
  S_n(f(x))=\sum_{|k|\le n}{a_n\mathrm{e}^{ikx}}
  $$

### 3.2	Fatou定理

**径向极限(radial limit)**：对于定义在单位开圆盘$\mathbb{D}=\{ z\in\C:|z|<1 \}$上的函数$F$，称$F$在单位圆周上的点$\mathrm{e}^{i\theta}$处存在径向极限，其中$\theta\in[-\pi,\pi]$，如果存在极限
$$
\lim_{r\to 1^-}{F(r\mathrm{e}^{i\theta})}
$$

**Hardy空间**：Hardy空间$H^2(\mathbb{D})$是包含所有单位开圆盘$\mathbb{D}$上全纯的函数$f$，其中$f$满足
$$
\sup_{0\le r\le 1}{\frac{1}{2\pi}\int_{-\pi}^{\pi}{|F(r\mathrm{e}^{i\theta})|^2\mathrm{d}\theta}}<\infty
$$
定义范数为
$$
\Vert F \Vert_{H^2{\mathbb{D}}}=\left(\sup_{0\le r\le 1}{\frac{1}{2\pi}\int_{-\pi}^{\pi}{|F(r\mathrm{e}^{i\theta})|^2\mathrm{d}\theta}}\right)^{\frac{1}{2}}
$$
- $F\in H^2(\mathbb{D})$当且仅当$F$可以写成
  $$
  F=\sum_{n=0}^{\infty}{a_n z^n}
  $$
  其中
  $$
  \sum_{n=0}^{\infty}{|a_n|^2}<\infty
  $$
- $$
  \Vert F \Vert^2_{H^2{\mathbb{D}}}=\sum_{n=0}^{\infty}{|a_n|^2}
  $$
- $$
  H^2(\mathbb{D})\sub\mathcal{H}
  $$

**定理3.3	Fatou定理**：如果函数$F$有界，且$F\in H^2(\mathbb{D})$，那么$F$几乎处处存在径向极限。

## 4	闭子空间和正交投影

**闭的(closed)**：称子空间$\mathcal{S}\sub\mathcal{H}$为闭的，如果对于Cauchy序列封闭。

事实上，有限维Hilbert空间的任意子空间为闭的，且Hilbert空间的任意闭子空间为Hilbert空间。

**引理4.1**：如果$\mathcal{S}\sub\mathcal{H}$为$\mathcal{H}$的闭子空间，且$f\in\mathcal{H}$，那么

- 存在非平凡的$g_0\in\mathcal{S}$，使得成立
  $$
  \Vert f-g_0 \Vert = \inf_{g\in\mathcal{S}}\Vert f-g \Vert
  $$

- 对于此$g_0$，成立$f-g_0\perp\mathcal{S}$

**正交补(orthogonal complement)**：对于子空间$\mathcal{S}\sub\mathcal{H}$，定义其正交补为
$$
\mathcal{S}^{\perp}=\{ f\in\mathcal{H}:f\perp \mathcal{S} \}
$$

**和(sum)**：定义子空间$\mathcal{S},\mathcal{T}\sub\mathcal{H}$的和为
$$
\mathcal{S}+\mathcal{T}=\{ f+g:f\in\mathcal{S},g\in\mathcal{T} \}
$$

**直和(direct sum)**：称子空间$\mathcal{S},\mathcal{T}\sub\mathcal{H}$的和$\mathcal{S}+\mathcal{T}$为直和，如果对于任意$f\in\mathcal{S}+\mathcal{T}$，存在且存在唯一$g\in\mathcal{S}$和$h\in\mathcal{T}$，使得成立$f=g+h$；等价于$\mathcal{S}\cap\mathcal{T}=\{0\}$。记作$\mathcal{S}\oplus\mathcal{T}$

**命题4.2**：对于闭子空间$\mathcal{S}\sub\mathcal{H}$，成立
$$
\mathcal{H}=\mathcal{S}\oplus\mathcal{S}^{\perp}
$$

**正交投影(orthogonal projection)**：对于$\mathcal{H}=\mathcal{S}\oplus\mathcal{S}^{\perp}$，定义$\mathcal{S}$上的正交投影为$P_{\mathcal{S}}(f)=g$，其中$f=g+h$，且$g\in\mathcal{S}$和$h\in\mathcal{S}^{\perp}$。

- $f\mapsto P_{\mathcal{S}}(f)$是线性映射。
- 对于任意$f\in\mathcal{S}$，成立$P_{\mathcal{S}}(f)=f$。
- 对于任意$f\in\mathcal{S}^{\perp}$，成立$P_{\mathcal{S}}(f)=0$。
- 对于任意$f\in\mathcal{H}$，成立$\Vert P_{\mathcal{S}}(f) \Vert\le\Vert f \Vert$。

## 5	线性变换

**线性变换(linear transformation)（线性算子(linear transformation)）**：对于Hilbert空间$\mathcal{H}_0$和$\mathcal{H}$，称映射$T:\mathcal{H}_0\to\mathcal{H}$为线性变换（线性算子），如果满足
$$
T(af+bg)=aT(f)+bT(g)
$$

**有界线性算子(bounded linear operator)**：称线性算子$T:\mathcal{H}_0\to\mathcal{H}$为有界的，如果存在$M>0$，使得对于任意$f\in\mathcal{H}_0$，成立
$$
\Vert T(f) \Vert_{\mathcal{H}}\le M
\Vert f \Vert_{\mathcal{H}_0}
$$

**范数(norm)**：有界线性算子$T:\mathcal{H}_0\to\mathcal{H}$的范数定义为
$$
\Vert T \Vert=\inf\{ M>0:\forall  f\in\mathcal{H}_0,\Vert T(f) \Vert_{\mathcal{H}}\le M
\Vert f \Vert_{\mathcal{H}_0}\}
$$

**引理5.1**：对于有界线性算子$T:\mathcal{H}_0\to\mathcal{H}$，成立
$$
\Vert T \Vert=\sup\{ |(T(f),g)|:\Vert f \Vert\le 1,\Vert g \Vert\le 1 \}
$$

**连续线性算子(continuous linear operator)**：称线性算子$T:\mathcal{H}_0\to\mathcal{H}$为连续的，如果对于任意$f_n\to f$，成立$T(f_n)\to T(f)$。事实上，线性保证了在原点连续即成立在定义域连续。

**命题5.2**：线性算子的有界性和连续性等价。

### 5.1	线性泛函和Riesz表示定理

**线性泛函(linear functional)**：线性变换$\ell:\mathcal{H}\to\C$称为线性泛函。

**定理5.3	Riesz表示定理(Riesz representation theorem)**：如果线性变换$\ell:\mathcal{H}\to\C$为线性泛函，那么存在且存在唯一$g\in\mathcal{H}$，使得对于任意$f\in\mathcal{H}$，成立
$$
\ell(f)=(f,g)
$$
同时
$$
\Vert \ell \Vert=\Vert g \Vert
$$

### 5.3	伴随

**伴随(adjoint)**：称有界线性变换$T^*:\mathcal{H}\to\mathcal{H}$为有界线性变换$T:\mathcal{H}\to\mathcal{H}$的伴随，如果满足

- $$
  (T(f),g)=(f,T^*(g))
  $$

- $$
  \Vert T \Vert=\Vert T^* \Vert
  $$

- $$
  (T^*)^*=T
  $$

**命题5.4**：有界线性变换存在且存在唯一伴随。

事实上，任取$g\in\mathcal{H}$，定义线性泛函
$$
\ell(f)=(T(f),g)
$$
由Riesz表示定理，存在且存在唯一$h\in\mathcal{H}$，使得成立
$$
\ell(f)=(f,g)
$$
定义
$$
T^*:g\mapsto h
$$

**对称线性算子(symmetric linear operator)**：称有界线性变换$T:\mathcal{H}\to\mathcal{H}$为对称的，如果$T=T^*$。

**伴随的性质**：

- 对称线性算子$T:\mathcal{H}\to\mathcal{H}$满足
  $$
  \Vert T \Vert=\sup\{ (T(f),f):\Vert f \Vert = 1\}
  $$

- 对于有界线性算子$T:\mathcal{H}\to\mathcal{H}$和$S:\mathcal{H}\to\mathcal{H}$，定义其积为
  $$
  (TS)(f)=T(S(f))
  $$
  那么
  $$
  (TS)^*=S^*f^*
  $$

### 5.3	例

**特征值(eigenvalue)和特征向量(eigenvector)**：称非零元素$\varphi\in\mathcal{H}$为线性变换$T:\mathcal{H}\to\mathcal{H}$的特征向量，如果存在特征值$\lambda\in \C$，使得成立
$$
T(\varphi)=\lambda\varphi
$$

**对角线性变换(diagonalized linear transformation)**：称线性变换$T:\mathcal{H}\to\mathcal{H}$为对角的，如果对于其标准正交基$\{ \varphi \}_{n=1}^{\infty}\sub\mathcal{H}$，存在$\{ \lambda_n \}_{n=1}^{\infty}\sub\C$，使得对于任意$n\in\N^*$，成立
$$
T(\varphi_n)=\lambda_n \varphi_n
$$
- 如果
  $$
  f\sim \sum_{n=1}^{\infty}{a_n\varphi_n}
  $$
  那么
  $$
  T(f)\sim \sum_{n=1}^{\infty}{a_n\lambda_n\varphi_n}
  $$

- $$
  \Vert T \Vert = \sup_{n\in\N^*}|\lambda_n|
  $$

- $T^*$的特征值序列为$\{ \overline{\lambda}_n \}_{n=1}^{\infty}$。

- $T$为对称的，当且仅当$\{ \lambda_n \}_{n=1}^{\infty}\sub\R$。

- $T$为酉的，当且仅当对于任意$n\in\N^*$，成立$|\lambda_n|=1$。

- $T$为正交投影，当且仅当对于任意$n\in\N^*$，成立$\lambda_n=0$或$\lambda_n=1$。

---

**积分算子(integral operator)（Hilbert-Schmidt算子）**：定义积分算子$T:L^2(\R^d)\to L^2(\R^d)$为
$$
T(f)(x)=\int_{\R^d}{K(x,y)f(y)\mathrm{d}y}
$$
其中$K$为核。

**命题5.5**：对于以$K$为核的Hilbert-Schmidt算子$T:L^2(\R^d)\to L^2(\R^d)$，成立如下命题。

- 如果$f\in L^2(\R^d)$，那么对于几乎任意的$x\in\R^d$，函数$y\mapsto K(x,y)f(y)$是可积的。

- $T$是有界的，且
  $$
  \Vert T \Vert \le \Vert K \Vert_{L^2(\R^d\times\R^d)}
  $$

- $\overline{K(x,y)}$为伴随$T^*$的核。

## 6	紧致算子

**紧致空间(compact space)**：称$X\sub\mathcal{H}$为紧致的，如果对于任意序列$\{f_n\}_{n=1}^{\infty}\sub X$，存在子序列$\{f_{n_k}\}_{k=1}^{\infty}$收敛于$X$。

**紧致线性算子(compact linear operator)**：称线性算子$T:\mathcal{H}\to\mathcal{H}$为紧致的，如果
$$
B=\{ f\in\mathcal{H}:\Vert f \Vert \le 1 \}
$$
的像
$$
T(B)=\{ T(f):f\in B \}
$$
为紧集。等价的，称线性算子$T:\mathcal{H}\to\mathcal{H}$为紧致的，如果对于$\mathcal{H}$中的任意有界序列$\{f_n\}_{n=1}^{\infty}\sub X$，存在收敛子序列。

**命题6.1**：对于有界线性算子$T:\mathcal{H}\to\mathcal{H}$，如下命题成立

- 如果$S$在$\mathcal{H}$上紧致，那么$ST$和$TS$在$\mathcal{H}$上紧致。
- 如果$\{T_n\}_{n=1}^{\infty}$为紧致线性算子序列，且$T_n\to T$，那么$T$为紧致线性算子。
- 如果$T$为紧致线性算子，那么存在有限秩算子序列$\{T_n\}_{n=1}^{\infty}$，使得成立$T_n\to T$。
- $T$是紧致的，当且仅当$T^*$是紧致的。
- 如果$T$为对角线性变换，那么$T$为紧致的，当且仅当$|\lambda_n|\to 0$。
- 任意Hilbert-Schmidt算子为紧致的。

**定理6.2	谱定理(spectral theorem)**：如果$T:\mathcal{H}\to\mathcal{H}$为紧致对称线性算子，那么$T$存在由特征向量组成的标准正交基$\{\varphi_n\}_{n=1}^{\infty}\sub\mathcal{H}$。并且，对应的特征值$\lambda_n\to0$。

**引理6.3**：对于有界对称线性算子$T:\mathcal{H}\to\mathcal{H}$，如下命题成立。

- $T$的特征值为实数。
- $T$的不同特征值对应的特征向量正交。

**引理6.4**：如果$T$为紧致的，且$\lambda\ne0$，那么$T-\lambda I$的零空间是有限维的。同时，$T$的特征值构成至多可数集$\{ \lambda_n \}_{n=1}^{\infty}$，且$\lambda_n\to0$。换言之，对于任意$\varepsilon>0$，$\{\lambda_n:|\lambda_n|>\varepsilon\}$对应的特征向量张成的线性空间为有限维的。

**引理6.5**：如果$T$为非零紧致对称算子，那么$\Vert T \Vert$或$-\Vert T \Vert$为$T$的特征值。

# 五、Hilbert空间：例

## 1	$L^2$上的Fourier变换

**Schwartz类(Schwartz claa)**：Schwartz类$\mathcal{S}(\R^d)$由光滑函数$f$构成，并且对于任意$\alpha$和$\beta$，$x^\alpha\left(\frac{\part }{\part x}\right)^\beta f$在$\R^d$上有界。

**定理1.1**：对于定义在$\mathcal{S}(\R^d)$上的Fourier变换$\mathcal{F}_0$，存在非平凡延拓$\mathcal{F}$，使得$\mathcal{F}:L^2(\R^d)\to L^2(\R^d)$为酉映射。特别的，对于任意$f\in L^2(\R^d)$，成立
$$
\Vert \mathcal{F}(f) \Vert_{L^2(\R^d)} =\Vert f \Vert_{L^2(\R^d)}
$$

**定理1.2**：$\mathcal{S}(\R^d)$在$L^2(\R^d)$上稠密，即对于任意$f\in L^2(\R^d)$，存在$\{f_n\}_{n=1}^{\infty}\sub\mathcal{S}$，使得成立$f_n\to f$。

**引理1.3**：对于分别具有内积$\Vert\cdot\Vert_1$和$\Vert\cdot\Vert_2$的Hilbert空间$\mathcal{H}_1$和$\mathcal{H}_2$，如果$\mathcal{S}$为$\mathcal{H}_1$的稠密子空间，且线性变换$T_0:\mathcal{S}\to\mathcal{H}_2$满足存在$c>0$，使得对于任意$f\in\mathcal{S}$，成立$\Vert T_0(f)\Vert_2\le c\Vert f \Vert_1$，那么$T_0$可延拓为非平凡线性变换$T:\mathcal{H}_1\to\mathcal{H}_2$，满足对于任意$f\in\mathcal{H}_1$，成立$\Vert T(f)\Vert_2\le c\Vert f \Vert_1$。

## 2	上半平面的Hardy空间

**Hardy空间**：对于$\R^2_+=\{ z\in\C:\Im z>0 \}$，定义Hardy空间为
$$
H^2(\R^2_+)\left\{ F:F在\R^2_+上全纯,\sup_{y>0}\int_{\R}{|F(x+iy)|^2\mathrm{d}x}<\infty \right\}
$$
其范数定义为
$$
\Vert F \Vert = \left(\sup_{y>0}\int_{\R}{|F(x+iy)|^2\mathrm{d}x}\right)^{\frac{1}{2}}
$$

**定理2.1**：$H^2(\R^2_+)$中的函数$F$由
$$
F(z)=\int_0^\infty \hat{F}_0(\xi)\mathrm{e}^{2\pi i \xi z}\mathrm{d}\xi,\quad \Im z>0
$$
给出，其中$\hat{F}_0\in L^2(0,\infty)$。同时
$$
\Vert F \Vert_{H^2(\R^2_+)}=\Vert \hat{F}_0 \Vert_{L^2(0,\infty)}
$$

**引理2.2**：如果$F\in H^2(\R^2_+)$，那么对于任意$\delta>0$，$F$在$\{ z\in\C:\Im z\ge\delta \}$有界。

**定理2.3**：如果$F\in H^2(\R^2_+)$，那么极限$\lim_{y\to0}F(x+iy)$在如下两种意义存在。

- 作为$L^2(\R)$范数的极限。
- 作为几乎任意$x$的极限。

## 3	常系数偏微分方程

**常系数偏微分方程(constant coe–cient partial difierential equations)**：
$$
L(u)=f
$$
其中
$$
L=\sum_{|k|\le n}{a_k\left(\frac{\part}{\part x}\right)^k},\quad a_k\in\C
$$

**伴随算子(adjoint operator)**：
$$
L^*=\sum_{|k|\le n}{(-1)^{|k|}\overline{a_k}\left(\frac{\part}{\part x}\right)^k}
$$

### 3.1	弱解

**引理3.1**：$C_0^\infty(\Omega)$以$\Vert\cdot\Vert_{L^2(\Omega)}$范数在$L^2(\Omega)$上稠密。

### 3.2	主定理和关键估计

**定理3.2**：对于有界开集$\Omega\sub\R^d$，如果给定常系数线性偏微分算子$L$，那么在$L^2(\Omega)$上存在有界线性算子$K$，使得对于任意$f\in L^2(\Omega)$，在弱意义上成立
$$
L(Kf)=f
$$
即$u=K(f)$为$L(u)=f$的一个弱解。

**引理3.3**：存在常数$c$，使得对于任意$\psi\in C_0^\infty(\Omega)$，成立
$$
\Vert \psi \Vert_{L^2(\Omega)}\le c
\Vert L^*\psi \Vert_{L^2(\Omega)}
$$

**引理3.4**：对于首一多项式$P$，如果$F$在$\C$上全纯，那么
$$
|F(0)|^2\le\frac{1}{2\pi}\int_0^{2\pi}|P(\mathrm{e}^{i\theta})F(\mathrm{e}^{i\theta})|^2
\mathrm{d}\theta
$$

## 4	Dirichlet原理

**Dirichlet问题(Dirichlet problem)**：如果$\Omega\sub\R^2$为有界开集，$f$在其边界$\part\Omega$上连续，那么找到函数$u(x,y)$，使得成立
$$
\begin{cases}
\Delta u=0,\quad & (x,y)\in\Omega\\
u=f,\quad & (x,y)\in\part\Omega
\end{cases}
$$

**Dirichlet积分**：
$$
\mathcal{D}(U)=\int_\Omega|\nabla U|^2=\int_\Omega\left|\frac{\part U}{\part x}\right|^2+\left|\frac{\part U}{\part y}\right|^2\mathrm{d}x\mathrm{d}y
$$

**命题4.1**：如果存在$u\in C^2(\overline{\Omega})$使得对于任意满足$U|_{\part\Omega}=f$的$U\in C^2(\overline{\Omega})$，成立$\mathcal{D}(u)\le\mathcal{D}(U)$，那么$u$在$\Omega$上调和。

### 4.1	调和函数

**调和函数(harmonic function)**：称定义在开集$\Omega\sub\R^d$上的函数$u$是调和的，如果$u$二阶连续可微，且
$$
\Delta u=\sum_{k=1}^{d}\frac{\part^2 u}{\part x_k^2}=0
$$

**弱调和(weakly harmonic)**：称定义在开集$\Omega\sub\R^d$上的函数$u$是弱调和的，如果对于任意$\psi\in C_0^\infty(\Omega)$，$(u,\Delta \psi)=0$。

**均值性质(mean-value property)**：称定义在开集$\Omega\sub\R^d$上的函数$u$满足均值性质，如果对于任意以$x_0$为心开球$B$满足$\overline{B}\sub\Omega$，成立
$$
u(x_0)=\frac{1}{m(B)}\int_B u(x)\mathrm{d}x
$$

**定理4.2**：如果连续函数$u$在开集$\Omega\sub\R^d$上调和，那么$u$满足均值性质。反之，满足均值性质的连续函数是调和的。

**定理4.3**：对于任意开集$\Omega\sub\R^d$上的弱调和函数$u$，存在在$\Omega$上几乎处处成立$\tilde{u}=u$的$\tilde{u}$，使得成立$\tilde{u}$在$\Omega$上调和。

**推论4.4	极大值原理(maximum principle)**：如果$u$在有界开集$\Omega\sub\R^d$上为连续且调和的，那么
$$
\max_{x\in\overline{\Omega}}|u(x)|=\max_{x\in\part\Omega}|u(x)|
$$

**引理4.5**：
$$
\int_B(v\Delta u-u\Delta v)\eta
=\int_B(u(\nabla v\cdot \nabla \eta)-v(\nabla u\cdot \nabla\eta))
$$
其中
$$
\nabla u=\left( \frac{\part u}{\part x_1} ,\cdots,\frac{\part u}{\part x_d} \right)
$$

**引理4.6**：如果$u$在$\Omega\sub\R^d$上满足均值性质，且闭球$\{ x\in\R^d:|x-x_0|\le r \}\sub\Omega$，那么
$$
u(x_0)=\int_{\R^d}u(x_0-ry)\varphi(y)\mathrm{d}y=\int_{\R^d}u(x_0-y)\varphi_r(y)\mathrm{d}y=(u*\varphi_r)(x_0)
$$
其中$ \varphi_r(y)=r^{-d}\varphi(\frac{y}{r}) $。

**推论4.7**：调和则无穷可微。

**推论4.8**：如果$\Omega$上的调和函数序列$\{ u_n \}_{n=1}^{\infty}$在$\Omega$内闭一致收敛于$u$，那么$u$也是调和的。

### 4.2	边值问题和Dirichlet原理

**推论4.9**：对于有界开集$\Omega\sub\R^d$，如果$v$在$\overline{\Omega}$上连续，且$v(\part\Omega)=\{0\}$，那么
$$
\int_\Omega|v|^2\le c_\Omega\int_\Omega|\nabla v|^2
$$

**推论4.10**：如果$f$在紧集$K\sub\R^d$上连续，那么存在$\R^d$上的光滑函数序列$\{ f_n \}_{n=1}^{\infty}$，使得$f_n$在$K$上一致收敛于$f$。

**引理4.11**：如果$f$在紧集$K\sub\R^d$上连续，那么存在$\R^d$上的连续函数$g$，使得成立$g|_{\part K}=f$。

**定理4.12**：对于满足外三角形条件的有界开集$\Omega\sub\R^2$，如果$f$在$\part \Omega$上连续，那么对于在$\overline{\Omega}$上的连续函数$u$，$u|_{\part \Omega}=f$的边值问题$\Delta u=0$为唯一可解的。

**命题4.13**：对于任意满足外三角形条件的有界开集$\Omega\sub\R^2$，存在常数$c_2<1<c_1$，使得成立：如果$z\in\Omega$到$\part \Omega$的距离为$\delta$，那么对于任意在$\overline{\Omega}$上连续且$v|_{\part\Omega}=0$的$v$，成立
$$
\int_{B_{c_1}{\delta(z)}}|v|^2\le C\delta^2\int_{B_{c_2}\delta(z)\cap \Omega}|\nabla v|^2
$$
其中$C$仅取决于$\Omega$的直径和三角形的参数。

# 6	抽象测度和积分理论

## 1	抽象测度空间

**测度空间(measure space)**：称三元组$(X,\mathcal{M},\mu)$为测度空间，其中

- $\mathcal{M}\sub \mathcal{P}(X)$为$\sigma$-代数，即对补运算和可数并运算封闭的非空子集。

- $\mu:\mathcal{M}\to[0,\infty]$为测度，满足可数可加性，即对于互不相交的可数集$\{ E_n \}_{n=1}^{\infty}\sub\mathcal{M}$，成立
  $$
  \mu\left( \bigcup_{n=1}^{\infty}E_n \right)=\sum_{n=1}^{\infty}\mu(E_n)
  $$

### 1.1	外测度和Caratheodory定理

**外测度(exterior measure or outer measure)**：称映射$\mu_*:\mathcal{P}(X)\to[0,\infty]$为外测度，如果满足如下性质。

- **空集的零测性**：$\mu_*(\varnothing)=0$

- **单调性**：如果$E_1\sub E_2$，那么$\mu_*(E_1)\le \mu_*(E_2)$。

- **次可数可加性**：对于可数集$\{ E_n \}_{n=1}^{\infty}\sub\mathcal{M}$，成立
  $$
  \mu_*\left( \bigcup_{n=1}^{\infty}E_n \right)\le\sum_{n=1}^{\infty}\mu_*(E_n)
  $$

**Caratheodory可测的**：称$E\sub X$是Caratheodory可测的，如果对于任意$F\sub X$，成立
$$
\mu_*(A)=\mu_*(E\cap F)+\mu_*(E^c\cap F)
$$

**定理1.1	Caratheodory定理**：对于集合$X$上的外测度$\mu_*$，满足Caratheodory可测条件的集合构成$\sigma$-代数$\mathcal{M}$，进而定义在$\mathcal{M}$上的$\mu_*$为测度。

**完备(complete)**：测度空间$(X,\mathcal{M},\mu)$是完备的，即对于任意$F\in\mathcal{M}$，如果$\mu(F)=0$且$E\sub F$，那么$E\in\mathcal{M}$。

### 1.2	度量外测度

**度量空间(metric space)**：称二元组$(X,d)$为度量空间，其中度量为$d:X\times X\to[0,\infty)$且满足如下性质。

- **正则性**：当且仅当$x=y$时，$d(x,y)=0$。
- **对称性**：对于任意$x,y\in X$，成立$d(x,y)=d(y,x)$。
- **三角不等式**：对于任意$x,y,z\in X$，成立$d(x,z)\le d(x,y)+d(y,z)$。

**Borel $\sigma$-代数**：Borel $\sigma$-代数$\mathcal{B}_X$为包含测度空间$X$中所有开集的最小生成$\sigma$-代数。

**Borel测度**：称定义在度量空间$X$上的Borel $\sigma$-代数$\mathcal{B}_X$上的测度为Borel测度。

**集合间的距离(distance)**：对于测度空间$(X,d)$中的两个集合$A,B\sub X$，定义其距离为
$$
d(A,B)=\inf\{ d(x,y):x\in A,y\in B \}
$$

**度量外测度(metric exterior measure )**：对于测度空间$X$，称$X$上的外测度$\mu_*$为度量外测度，如果对于任意满足$d(A,B)>0$的$A,B\sub X$，成立
$$
\mu_*(A\cup B)=\mu_*(A)+\mu_*(B)
$$

**定理1.2**：如果$\mu_*$是度量空间$(X,d)$上的度量外测度，那么$X$上的Borel集是可测的；因此，定义在$X$上的Borel $\sigma$-代数$\mathcal{B}_X$上的$\mu_*$为测度。

**命题1.3**：对于Borel $\sigma$-代数$\mathcal{B}_X$上的Borel测度$\mu$，如果对于任意$r<\infty$，成立$\mu(B_r)<\infty$，那么对于任意$\varepsilon>0$和$B\in\mathcal{B}_X$，存在开集$\mathcal{O}\supset B$和闭集$F\sub B$，成立$\mu(\mathcal{O}-B)<\varepsilon$和$\mu(B-F)<\varepsilon$。

### 1.3	延拓定理

**代数(algebra)**：称集族$\mathcal{A}$为代数，如果其对补运算和有限并运算封闭。

**预测度(premeasure)**：对于代数$\mathcal{A}$，称映射$\mu_0:\mathcal{A}\to[0,\infty]$为预测度，如果满足如下性质。

- **空集的零测性**：$\mu_0(\varnothing)=0$

- **可数可加性**：对于互不相交的可数集$\{ E_n \}_{n=1}^{\infty}\sub\mathcal{A}$，如果$\bigcup_{n=1}^{\infty}E_n\in\mathcal{A}$​，那么
  $$
  \mu_0\left( \bigcup_{n=1}^{\infty}E_n \right)=\sum_{n=1}^{\infty}\mu_0(E_n)
  $$

**引理1.4**：如果$\mu_0$为代数$\mathcal{A}\sub\mathcal{P}(X)$上的预测度，那么由$\mu_0$生成的外测度为$\mu_*:X\to[0,\infty]$，其中
$$
\mu_*(E)=\inf\left\{ \sum_{n=1}^{\infty}{\mu_0(E_n)}:\bigcup_{n=1}^{\infty}{E_n}\supset E,E_n\in\mathcal{A} \right\}
$$
且满足如下性质。

- 对于任意$E\in\mathcal{A}$，成立$\mu_*(E)=\mu_0(E)$。
- $\mathcal{A}$中的集合在上述意义下可测。

**定理1.5**：如果$\mu_0$为代数$\mathcal{A}\sub\mathcal{P}(X)$上的预测度，$\mathcal{M}$是由$\mathcal{A}$生成的最小$\sigma$-代数，那么在$\mathcal{M}$上$\mu_0$可延拓为测度$\mu$。

**$\sigma$型集和$\delta$型集**：对于代数$\mathcal{A}$上，定义$\mathcal{A}_\sigma$为$\mathcal{A}$中集合的可数并，$\mathcal{A}_\delta$为$\mathcal{A}$中集合的可数交。

**命题1.6**：对于任意$E\sub X$和$\varepsilon>0$，存在$E_1\in\mathcal{A}_\sigma$和$E_2\in\mathcal{A}_{\sigma\delta}$，满足$E\sub E_1$和$E\sub E_2$，且$\mu_*(E_1)\le \mu_*(E)+\varepsilon$和$\mu_*(E_2)=\mu_*(E)$。

## 测度空间上的积分
