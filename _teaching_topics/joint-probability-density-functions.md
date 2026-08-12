---
title: "聯合機率密度函數"
subtitle: "Joint Probability Density Functions"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 3
order: 303
permalink: /teaching-topics/joint-probability-density-functions/
date: 2026-07-24
published: false
listed: false
excerpt: "當聯合分配可由二重積分表示時，聯合 pdf 描述平面各處的密度；區域機率則是該區域上方的密度體積。"
---

[上一篇文章](/teaching-topics/joint-cumulative-distribution-functions/)以聯合 cdf 記錄門檻點左下方的累積機率。若這些機率可由某個二變數函數的二重積分表示，便可使用聯合機率密度函數描述分配。

這項前提不能省略。即使 $X$ 與 $Y$ 各自都有 pdf，$(X,Y)$ 的聯合分配仍未必具有二維的 pdf。

## 聯合機率密度函數

<div id="definition-35" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 3.5</div>

令 $(X,Y)$ 為二元隨機向量。若存在 Borel 可測函數 (Borel measurable function) $f_{XY}:\mathbb{R}^2\to[0,\infty)$，使對任意 $(x,y)\in\mathbb{R}^2$，皆有

$$
F_{XY}(x,y)
=
\mathbb{P}(X\leqslant x,Y\leqslant y)
=
\int_{-\infty}^{x}
\int_{-\infty}^{y}
f_{XY}(u,v)\,dv\,du
$$

則稱 $(X,Y)$ 具有**聯合絕對連續分配 (jointly absolutely continuous distribution)**，並稱 $f_{XY}$ 為其**聯合機率密度函數 (joint probability density function, joint pdf)**。
</div>

[Definition 3.5](#definition-35) 與單變數的 [Definition 2.5](/teaching-topics/cdf-and-pdf/#def-pdf) 具有相同的形式。單變數的 cdf 是 pdf 在半直線上的單積分；聯合 cdf 則是 joint pdf 在左下矩形上的二重積分。相應地，密度曲線下方的面積也改為密度曲面下方的體積。

這個定義也可用一般的平面區域表示。令 $\mu$ 表示 $(X,Y)$ 的聯合分配，並對 Borel 集合 (Borel set) $A\subseteq\mathbb{R}^2$ 定義

$$
\nu(A)
=
\iint_A f_{XY}(u,v)\,du\,dv
$$

由 $F_{XY}(n,n)\to1$ 與單調收斂定理可知，$\nu(\mathbb{R}^2)=1$，所以 $\nu$ 是一個機率測度。[Definition 3.5](#definition-35) 表示 $\mu$ 與 $\nu$ 在所有左下矩形上取相同的值。這類矩形構成一個 $\pi$-系統 ($\pi$-system)，並生成 $\mathbb{R}^2$ 上的 Borel $\sigma$-域，因此由機率測度的唯一性可得 $\mu=\nu$。所以，對任意 Borel 集合 $A\subseteq\mathbb{R}^2$，皆有

$$
\mathbb{P}\bigl((X,Y)\in A\bigr)
=
\iint_A f_{XY}(u,v)\,du\,dv
$$

因此，$f_{XY}(x,y)$ 表示密度曲面在 $(x,y)$ 上方的高度，而事件機率是密度在整個事件區域上方所形成的體積。聯合 pdf 的函數值不是單點機率，也可能大於 $1$。

<div id="proposition-33" class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Proposition 3.3 (Conditions for a Joint pdf)</div>

Borel 可測函數 $f_{XY}:\mathbb{R}^2\to\mathbb{R}$ 可作為某個二元隨機向量的聯合 pdf，若且唯若

$$
f_{XY}(x,y)\geqslant0
\quad\bigl((x,y)\in\mathbb{R}^2\bigr),
\qquad
\int_{-\infty}^{\infty}
\int_{-\infty}^{\infty}
f_{XY}(x,y)\,dy\,dx
=
1
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.** 若 $f_{XY}$ 為聯合 pdf，則 [Definition 3.5](#definition-35) 已要求 $f_{XY}$ 非負。再由聯合 cdf 在右上方的極限可得

$$
\int_{-\infty}^{\infty}
\int_{-\infty}^{\infty}
f_{XY}(x,y)\,dy\,dx
=
\lim_{n\to\infty}F_{XY}(n,n)
=
1
$$

反過來，若 Borel 可測函數 $f_{XY}$ 滿足上述兩個條件，可取樣本空間 $S=\mathbb{R}^2$，並令 $\mathcal{F}=\mathcal{B}(\mathbb{R}^2)$。對每個 $A\in\mathcal{F}$，定義

$$
\mathbb{P}(A)
=
\iint_A f_{XY}(x,y)\,dx\,dy
$$

由 $f_{XY}$ 的非負性可得 $\mathbb{P}(A)\geqslant0$，而總積分為 $1$ 給出 $\mathbb{P}(\mathbb{R}^2)=1$。此外，Lebesgue 積分 (Lebesgue integral) 對兩兩互斥的 Borel 集合具有可數可加性。若 $A_1,A_2,\ldots$ 兩兩互斥，則

$$
\begin{aligned}
\mathbb{P}
\left(
\bigcup_{n=1}^{\infty}A_n
\right)
&=
\iint_{\bigcup_{n=1}^{\infty}A_n}
f_{XY}(x,y)\,dx\,dy \\[0.4em]
&=
\sum_{n=1}^{\infty}
\iint_{A_n}
f_{XY}(x,y)\,dx\,dy \\[0.4em]
&=
\sum_{n=1}^{\infty}\mathbb{P}(A_n)
\end{aligned}
$$

因此，$\mathbb{P}$ 滿足機率公理。對樣本點 $\omega=(u,v)\in S$，再令 $X(\omega)=u$ 與 $Y(\omega)=v$。兩者都是 Borel 可測的座標投影函數，所以 $(X,Y)$ 是二元隨機向量。其聯合 cdf 為

$$
\begin{aligned}
F_{XY}(x,y)
&=
\mathbb{P}(X\leqslant x,Y\leqslant y) \\[0.4em]
&=
\int_{-\infty}^{x}
\int_{-\infty}^{y}
f_{XY}(u,v)\,dv\,du
\end{aligned}
$$

故 $f_{XY}$ 可作為 $(X,Y)$ 的聯合 pdf。<span class="topic-qed">$\square$</span>
</div>

## 聯合 pdf 的正規化與區域機率

<div id="example-33" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.3 (Normalizing a Joint Density)</div>

考慮函數

$$
f_{XY}(x,y)
=
\begin{cases}
cxy(1-x), & 0<x<1,\ 0<y<1,\\
0, & \text{其他}
\end{cases}
$$

先求 $c$，使 $f_{XY}$ 成為聯合 pdf。由 [Proposition 3.3](#proposition-33) 可得

$$
\begin{aligned}
1
&=
\int_0^1\int_0^1 cxy(1-x)\,dy\,dx \\[0.4em]
&=
c
\left(
\int_0^1x(1-x)\,dx
\right)
\left(
\int_0^1y\,dy
\right) \\[0.4em]
&=
c\left(\frac{1}{6}\right)
\left(\frac{1}{2}\right)
=
\frac{c}{12}
\end{aligned}
$$

因此，$c=12$。

此時 $f_{XY}$ 在指定範圍內非負，因此確實為聯合 pdf。

再計算矩形

$$
A
=
\left\{
(x,y)
\mid
0<x\leqslant\frac{1}{2},
\ 0<y\leqslant\frac{1}{2}
\right\}
$$

內的機率。依區域範圍設定二重積分，可得

$$
\begin{aligned}
\mathbb{P}\bigl((X,Y)\in A\bigr)
&=
\int_0^{1/2}\int_0^{1/2}
12xy(1-x)\,dy\,dx \\[0.4em]
&=
12
\left(
\int_0^{1/2}x(1-x)\,dx
\right)
\left(
\int_0^{1/2}y\,dy
\right) \\[0.4em]
&=
12\left(\frac{1}{12}\right)
\left(\frac{1}{8}\right)
=
\frac{1}{8}
\end{aligned}
$$

</div>

正規化檢查使用整個聯合值域，事件機率則只在目標區域上積分。兩者都在計算密度曲面下的體積，但積分範圍不同。

## 聯合 cdf 與聯合 pdf 的關係

由 [Definition 3.5](#definition-35) 可知，聯合 cdf 是聯合 pdf 在門檻點左下方的二重積分。反過來，若 $f_{XY}$ 在 $(x,y)$ 連續，便可由小矩形中的平均密度理解 $f_{XY}(x,y)$。

對 $h>0$ 與 $k>0$，矩形 $(x,x+h]\times(y,y+k]$ 的平均密度為

$$
\begin{aligned}
\frac{
F_{XY}(x+h,y+k)-F_{XY}(x,y+k)
-F_{XY}(x+h,y)+F_{XY}(x,y)
}{hk}
&=
\frac{1}{hk}
\int_x^{x+h}\int_y^{y+k}
f_{XY}(u,v)\,dv\,du
\end{aligned}
$$

當 $h\downarrow0$ 且 $k\downarrow0$ 時，若 $f_{XY}$ 在 $(x,y)$ 附近連續，上式會收斂至 $f_{XY}(x,y)$。若聯合 cdf 在該點附近二次連續可微，便可將這個極限寫為

$$
f_{XY}(x,y)
=
\frac{\partial^2F_{XY}(x,y)}
{\partial x\,\partial y}
$$

這個微分關係需要相應的連續與可微條件，不能在聯合 cdf 的每個點直接套用。聯合 pdf 在二維面積為 $0$ 的集合上如何取值，也不會改變任何區域機率。

<div id="interlude-32" class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 3.2</div>

令 $X$ 在 $(0,1)$ 上服從均勻分配 (uniform distribution; 參見 [Example 2.14](/teaching-topics/quantiles-and-median/#example-214))，並令 $Y=X$。此時 $X$ 與 $Y$ 各自都有 pdf，但 $(X,Y)$ 的全部機率都集中在直線 $y=x$ 上。

直線在平面中的二維面積為 $0$。若 $(X,Y)$ 具有 [Definition 3.5](#definition-35) 所定義的聯合 pdf，對這條直線積分所得的機率便應為 $0$，不可能等於 $1$。因此，兩個邊際分配各自具有 pdf，不能保證聯合分配也具有 pdf。
</div>

## 本篇小結

只有當聯合分配可由二重積分表示時，才有 [Definition 3.5](#definition-35) 所定義的聯合 pdf。聯合 pdf 的函數值表示密度高度；在指定區域上積分後，才得到該區域的機率。

若聯合 pdf 在某點連續，可由該點附近的小矩形機率除以矩形面積，得到局部密度。聯合 cdf 的混合偏導數公式則須在相應的可微條件下使用。

[下一篇文章](/teaching-topics/region-probabilities-marginal-distributions/)會進一步處理非矩形區域的積分範圍，並由聯合分配求出單一變數的邊際分配。

## 參考文獻與延伸閱讀

- 黃文璋，2003，《機率論》，初版，華泰文化。
- 黃文璋，2003，《數理統計》，初版，華泰文化。
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Joseph K. Blitzstein and Jessica Hwang. 2019. *Introduction to Probability*. 2nd ed. Chapman and Hall/CRC.
