---
title: "條件分配"
subtitle: "Conditional Distributions"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 5
order: 305
permalink: /teaching-topics/conditional-distributions/
date: 2026-07-24
published: false
listed: false
excerpt: "條件分配固定其中一個變數的取值，再重新調整聯合 pmf 的一列或聯合 pdf 的一個截面，使總量回到 1。"
---

[上一篇文章](/teaching-topics/region-probabilities-marginal-distributions/)把另一個變數的所有可能值加總或積分，得到邊際分配。條件分配採取另一種做法: 固定其中一個變數的取值，再觀察另一個變數如何分配。

對離散型隨機向量，這可直接由第一章的 [條件機率](/teaching-topics/conditional-probability-information/#條件機率) 得到。對具有聯合 pdf 的隨機向量，則取出固定位置的密度截面，再將截面的總量調整為 $1$。

## 條件機率質量函數

<div id="definition-38" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 3.8</div>

令 $(X,Y)$ 為二元離散型隨機向量，聯合 pmf 為 $p_{XY}$，邊際 pmf 為 $p_X$ 與 $p_Y$。

對滿足 $p_Y(y)>0$ 的固定值 $y$，令

$$
\mathcal{R}_{X\mid Y=y}
=
\bigl\{
x\in\mathcal{R}_X
\mid
(x,y)\in\mathcal{R}_{XY}
\bigr\}
$$

並對 $x\in\mathcal{R}_{X\mid Y=y}$ 定義

$$
\begin{aligned}
p_{X\mid Y}(x\mid y)
&=
\mathbb{P}(X=x\mid Y=y)
\\[0.4em]
&=
\frac{
\mathbb{P}\bigl(\lbrace X=x\rbrace\cap\lbrace Y=y\rbrace\bigr)
}{
\mathbb{P}(Y=y)
} \\[0.4em]
&=
\frac{p_{XY}(x,y)}{p_Y(y)}
\end{aligned}
$$

在 $\mathcal{R}\_{X\mid Y=y}$ 以外令 $p\_{X\mid Y}(x\mid y)=0$。則稱 $p\_{X\mid Y}(\,\cdot\mid y)$ 為給定 $Y=y$ 時 $X$ 的**條件機率質量函數 (conditional probability mass function, conditional pmf)**。

對滿足 $p_X(x)>0$ 的固定值 $x$，令

$$
\mathcal{R}_{Y\mid X=x}
=
\bigl\{
y\in\mathcal{R}_Y
\mid
(x,y)\in\mathcal{R}_{XY}
\bigr\}
$$

並對 $y\in\mathcal{R}_{Y\mid X=x}$ 定義

$$
\begin{aligned}
p_{Y\mid X}(y\mid x)
&=
\mathbb{P}(Y=y\mid X=x)
\\[0.4em]
&=
\frac{
\mathbb{P}\bigl(\lbrace Y=y\rbrace\cap\lbrace X=x\rbrace\bigr)
}{
\mathbb{P}(X=x)
} \\[0.4em]
&=
\frac{p_{XY}(x,y)}{p_X(x)}
\end{aligned}
$$

在 $\mathcal{R}\_{Y\mid X=x}$ 以外令 $p\_{Y\mid X}(y\mid x)=0$。則稱 $p\_{Y\mid X}(\,\cdot\mid x)$ 為給定 $X=x$ 時 $Y$ 的條件 pmf。
</div>

由聯合 pmf 的非負性與 $p_Y(y)>0$ 可知，$p_{X\mid Y}(x\mid y)\geqslant0$；另一個方向的條件 pmf 亦同。

在 $p_{X\mid Y}(x\mid y)$ 中，$y$ 是已經固定的條件值，只有 $x$ 是此條件 pmf 的自變數。因此，條件 pmf 的總和可寫為

$$
\begin{aligned}
\sum_{x\in\mathcal{R}_{X\mid Y=y}}
p_{X\mid Y}(x\mid y)
&=
\frac{
\sum_{x\in\mathcal{R}_{X\mid Y=y}}p_{XY}(x,y)
}{
p_Y(y)
} \\[0.4em]
&=
\frac{p_Y(y)}{p_Y(y)}
=
1
\end{aligned}
$$

所以 $p_{X\mid Y}(\,\cdot\mid y)$ 滿足 [Proposition 2.2](/teaching-topics/discrete-random-variables-pmf/#proposition-22) 的非負性與總和條件，確實是一個 pmf。若 $A\subseteq\mathbb{R}$ 為 Borel 集合，則

$$
\mathbb{P}(X\in A\mid Y=y)
=
\sum_{x\in A\cap\mathcal{R}_{X\mid Y=y}}
p_{X\mid Y}(x\mid y)
$$

<div id="example-36" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.6 (Conditioning a Row of a Joint pmf)</div>

延續 [Example 3.1](/teaching-topics/random-vectors-joint-pmf/#example-31)。在 $Y=1$ 這一列中，

$$
p_{XY}(0,1)=\frac{2}{12},
\qquad
p_{XY}(1,1)=\frac{3}{12},
\qquad
p_{XY}(2,1)=0
$$

而 $p_Y(1)=5/12$。將這一列的每一格都除以列和 $5/12$，可得

$$
p_{X\mid Y}(x\mid1)
=
\begin{cases}
2/5, & x=0,\\
3/5, & x=1,\\
0, & \text{其他}
\end{cases}
$$

因此

$$
\mathbb{P}(X\geqslant1\mid Y=1)
=
\frac{3}{5}
$$

</div>

原本 $Y=1$ 這一列的總和是 $5/12$。除以 $5/12$ 之後，列內各格的相對比例不變，但總和成為 $1$，因而形成給定 $Y=1$ 時的完整分配。

若條件本身是一個具有正機率的事件，便可直接使用條件機率的比值。例如，當 $\mathbb{P}(c<Y<d)>0$ 時，

$$
\mathbb{P}(a<X<b\mid c<Y<d)
=
\frac{
\mathbb{P}(a<X<b,\ c<Y<d)
}{
\mathbb{P}(c<Y<d)
}
$$

分子先計算兩項範圍同時成立的機率，分母再把結果調整為已知 $c<Y<d$ 之後的相對比例。

## 條件機率密度函數

對具有聯合 pdf 的隨機向量，每個 $y\in\mathbb{R}$ 都滿足 $\mathbb{P}(Y=y)=0$，所以不能把 $\mathbb{P}(X\in A\mid Y=y)$ 直接寫成兩個事件機率的比值。條件 pdf 使用密度的比值，給出離散型公式在連續情形中的對應方式。

<div id="definition-39" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 3.9</div>

令 $(X,Y)$ 具有聯合 pdf $f_{XY}$，並令 $f_X$ 與 $f_Y$ 為 [Definition 3.6](/teaching-topics/region-probabilities-marginal-distributions/#definition-36) 由 $f_{XY}$ 的切片積分所得的邊際 pdf。

對滿足 $f_Y(y)>0$ 的固定值 $y$，定義

$$
f_{X\mid Y}(x\mid y)
=
\frac{f_{XY}(x,y)}{f_Y(y)}
$$

則稱 $f_{X\mid Y}(\,\cdot\mid y)$ 為給定 $Y=y$ 時 $X$ 的**條件機率密度函數 (conditional probability density function, conditional pdf)**。

對滿足 $f_X(x)>0$ 的固定值 $x$，定義

$$
f_{Y\mid X}(y\mid x)
=
\frac{f_{XY}(x,y)}{f_X(x)}
$$

則稱 $f_{Y\mid X}(\,\cdot\mid x)$ 為給定 $X=x$ 時 $Y$ 的條件 pdf。
</div>

對固定且滿足 $f_Y(y)>0$ 的 $y$，函數 $x\mapsto f_{XY}(x,y)$ 是非負 Borel 可測函數，除以正數 $f_Y(y)$ 後仍然如此；另一個方向的條件 pdf 亦同。

在 $f_{X\mid Y}(x\mid y)$ 中，$y$ 是已經固定的條件值，只有 $x$ 是此條件 pdf 的自變數。對目前選定的聯合 pdf 與條件 pdf 版本，令

$$
D_{X\mid Y=y}
=
\bigl\{
x\in\mathbb{R}
\mid
f_{XY}(x,y)>0
\bigr\}
$$

當 $f_Y(y)>0$ 時，這正是目前這個條件 pdf 版本取正值的範圍。密度可在長度為 $0$ 的集合上改值，因此這個取正值的範圍不是由分配唯一決定。

同理，對目前選定的密度版本，令

$$
D_{Y\mid X=x}
=
\bigl\{
y\in\mathbb{R}
\mid
f_{XY}(x,y)>0
\bigr\}
$$

當 $f_X(x)>0$ 時，這是目前的 $f_{Y\mid X}(\,\cdot\mid x)$ 取正值的範圍；同樣地，這個範圍不是由分配唯一決定。

對固定且滿足 $f_Y(y)>0$ 的 $y$，由 [Definition 3.6](/teaching-topics/region-probabilities-marginal-distributions/#definition-36) 可得

$$
\begin{aligned}
\int_{-\infty}^{\infty}
f_{X\mid Y}(x\mid y)\,dx
&=
\frac{
\int_{-\infty}^{\infty}
f_{XY}(x,y)\,dx
}{
f_Y(y)
} \\[0.4em]
&=
\frac{f_Y(y)}{f_Y(y)}
=
1
\end{aligned}
$$

所以 $f_{X\mid Y}(\,\cdot\mid y)$ 滿足 [Proposition 2.2](/teaching-topics/cdf-and-pdf/#prop-pdf-existence-conditions) 的可測性、非負性與總積分條件，確實是一個 pdf。條件分配只在條件變數的邊際分配下幾乎處處決定。對其中固定的條件值 $y$，條件 pdf 又只在 $x$ 的 Lebesgue 幾乎處處意義下決定。後文涉及條件 pdf 的等式時，均採用這兩層意義。

條件 pdf 的函數值本身不是機率。若 $A\subseteq\mathbb{R}$ 為 Borel 集合，則

$$
\mathbb{P}(X\in A\mid Y=y)
=
\int_A f_{X\mid Y}(x\mid y)\,dx
$$

## 條件 pdf 的截面與正規化

<div id="example-37" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.7 (A Conditional Density Slice)</div>

回到 [Example 3.3](/teaching-topics/joint-probability-density-functions/#example-33) 的聯合 pdf:

$$
f_{XY}(x,y)
=
\begin{cases}
12xy(1-x), & 0<x<1,\ 0<y<1,\\
0, & \text{其他}
\end{cases}
$$

先求 $Y$ 的邊際 pdf。對 $0<y<1$，有

$$
\begin{aligned}
f_Y(y)
&=
\int_0^1 12xy(1-x)\,dx \\[0.4em]
&=
12y
\int_0^1(x-x^2)\,dx
=
2y
\end{aligned}
$$

因此，對每個 $0<y<1$，給定 $Y=y$ 時 $X$ 的條件 pdf 為

$$
\begin{aligned}
f_{X\mid Y}(x\mid y)
&=
\frac{12xy(1-x)}{2y} \\[0.4em]
&=
6x(1-x),
\qquad
0<x<1
\end{aligned}
$$

例如，給定 $Y=1/4$ 時，可得

$$
\begin{aligned}
\mathbb{P}
\left(
X\leqslant\frac{1}{2}
\mid
Y=\frac{1}{4}
\right)
&=
\int_0^{1/2}6x(1-x)\,dx \\[0.4em]
&=
6
\left[
\frac{x^2}{2}-\frac{x^3}{3}
\right]_0^{1/2}
=
\frac{1}{2}
\end{aligned}
$$

</div>

<figure id="fig-34" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/conditional-density-slice.svg" alt="左圖顯示固定 Y 等於四分之一時的密度截面 3x(1-x)，曲線下方面積為二分之一。右圖顯示截面除以二分之一後得到條件密度 6x(1-x)，曲線下方面積為 1。">
  <figcaption><span class="topic-figure__label">Fig. 3.4.</span> 在 <a href="#example-37">Example 3.7</a> 中固定 $Y=1/4$，原始截面為 $f_{XY}(x,1/4)=3x(1-x)$，其曲線下方面積為 $f_Y(1/4)=1/2$。將截面除以 $1/2$ 後，便得到積分為 $1$ 的條件 pdf $6x(1-x)$。</figcaption>
</figure>

在 [Example 3.7](#example-37) 中，條件 pdf 不隨指定的 $y$ 改變，而且恰好等於 $X$ 的邊際 pdf。這表示知道 $Y$ 的值並未改變 $X$ 的分配，下一篇會由此定義獨立性。

## 以事件為條件時的截尾分配

令 $B\subseteq\mathbb{R}$ 為 Borel 集合，且 $\mathbb{P}(X\in B)>0$。若只保留 $X\in B$ 的結果，便會得到一個**截尾分配 (truncated distribution)**。此時，條件分配將 $B$ 之外的機率改為 $0$，再把 $B$ 之內的機率重新調整至總量為 $1$。離散型與具有 pdf 的情形分別可寫為

$$
p_{X\mid X\in B}(x)
=
\frac{p_X(x)\mathbf{1}_B(x)}
{\mathbb{P}(X\in B)}
$$

以及

$$
f_{X\mid X\in B}(x)
=
\frac{f_X(x)\mathbf{1}_B(x)}
{\mathbb{P}(X\in B)}
$$

其中，$\mathbf{1}_B$ 為集合 $B$ 的**指標函數 (indicator function)**。

<div id="example-38" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.8 (A Truncated Uniform Distribution)</div>

令 $X$ 在 $(0,1)$ 上服從均勻分配 (uniform distribution; 參見 [Example 2.14](/teaching-topics/quantiles-and-median/#example-214))。若已知 $X<1/4$，則條件 pdf 為

$$
f_{X\mid X<1/4}(x)
=
\begin{cases}
4, & 0<x<1/4,\\
0, & \text{其他}
\end{cases}
$$

原本 $(0,1/4)$ 上的 pdf 高度為 $1$，曲線下方面積為 $1/4$。除以這個條件事件的機率後，pdf 高度成為 $4$，面積也回到 $1$。因此，

$$
\mathbb{P}\left(X<\frac{1}{8}\mid X<\frac{1}{4}\right)
=
\frac{1/8}{1/4}
=
\frac{1}{2}
$$

</div>

## 本篇小結

離散型條件 pmf 取出聯合 pmf 的一列或一欄，再除以該列或該欄的邊際機率。具有聯合 pdf 時，條件 pdf 則取出密度截面，再除以相應的邊際密度。

兩種情形都必須先確認分母為正。若以具有正機率的事件為條件，則可直接用事件機率的比值；若固定具有 pdf 的隨機變數取值，則改用聯合密度與邊際密度的比值。調整後的 pmf 總和為 $1$，pdf 的積分也為 $1$，所以它們分別形成給定條件下的完整機率分配。

[下一篇文章](/teaching-topics/independent-random-variables/)會討論條件分配與邊際分配一致時所得到的獨立性。離散型情形須逐一考慮邊際機率為正的條件值；具有聯合 pdf 時，則須在幾乎處處的意義下敘述。

## 參考文獻與延伸閱讀

- 黃文璋，2003，《數理統計》，初版，華泰文化。
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Joseph K. Blitzstein and Jessica Hwang. 2019. *Introduction to Probability*. 2nd ed. Chapman and Hall/CRC.
