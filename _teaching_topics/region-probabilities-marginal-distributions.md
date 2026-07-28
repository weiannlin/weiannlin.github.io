---
title: "區域機率與邊際分配"
subtitle: "Region Probabilities and Marginal Distributions"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 4
order: 304
permalink: /teaching-topics/region-probabilities-marginal-distributions/
date: 2026-07-24
published: false
excerpt: "二重積分的上下限由聯合值域與事件共同決定；將聯合 pdf 對另一個變數積分，即可得到邊際 pdf。"
---

[上一篇文章](/teaching-topics/joint-probability-density-functions/)說明，聯合 pdf 在平面區域上方的體積就是該區域的機率。實際計算前，必須先找出聯合值域與目標事件的交集，再依垂直切片或水平切片寫出積分上下限。

若區域可寫成

$$
A
=
\bigl\{
(x,y)
\mid
a<x<b,\ \ell(x)<y<u(x)
\bigr\}
$$

則以垂直切片表示時，其機率為

$$
\mathbb{P}\bigl((X,Y)\in A\bigr)
=
\int_a^b
\int_{\ell(x)}^{u(x)}
f_{XY}(x,y)\,dy\,dx
$$

同一區域也可能改用水平切片表示。交換積分順序時，積分值不會改變，但上下限必須依新的切片方向重新判斷。

例如，若同一區域也可寫成

$$
A
=
\bigl\{
(x,y)
\mid
c<y<d,\ r(y)<x<s(y)
\bigr\}
$$

則以水平切片表示時，其機率為

$$
\mathbb{P}\bigl((X,Y)\in A\bigr)
=
\int_c^d
\int_{r(y)}^{s(y)}
f_{XY}(x,y)\,dx\,dy
$$

由於聯合 pdf 非負，Tonelli 定理 (Tonelli’s theorem) 保證兩種積分次序得到相同的機率。實際計算時，仍須分別依垂直或水平切片判斷上下限。

## 三角形範圍中的區域機率

<div id="example-34" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.4 (A Triangular Joint Range)</div>

令

$$
f_{XY}(x,y)
=
\begin{cases}
k(x+y), & 0\leqslant x\leqslant y\leqslant1,\\
0, & \text{其他}
\end{cases}
$$

先由整個三角形範圍上的積分求 $k$。因固定 $y$ 時，$x$ 的範圍為 $0\leqslant x\leqslant y$，所以

$$
\begin{aligned}
1
&=
\int_0^1\int_0^y k(x+y)\,dx\,dy \\[0.4em]
&=
k\int_0^1
\left[
\frac{x^2}{2}+xy
\right]_{x=0}^{x=y}
dy \\[0.4em]
&=
k\int_0^1\frac{3y^2}{2}\,dy
=
\frac{k}{2}
\end{aligned}
$$

因此，$k=2$。

現在求事件 $\lbrace X+Y\leqslant1\rbrace$ 的機率。在聯合值域內，必須同時滿足 $y\geqslant x$ 與 $y\leqslant1-x$，因此 $0\leqslant x\leqslant1/2$，且對每個固定的 $x$，$y$ 由 $x$ 變到 $1-x$。由此可得

$$
\begin{aligned}
\mathbb{P}(X+Y\leqslant1)
&=
\int_0^{1/2}\int_x^{1-x}
2(x+y)\,dy\,dx \\[0.4em]
&=
\int_0^{1/2}
\left[
2xy+y^2
\right]_{y=x}^{y=1-x}
dx \\[0.4em]
&=
\int_0^{1/2}(1-4x^2)\,dx \\[0.4em]
&=
\left[
x-\frac{4x^3}{3}
\right]_0^{1/2}
=
\frac{1}{3}
\end{aligned}
$$

</div>

<figure id="fig-33" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/triangular-joint-range-slices.svg" alt="左圖在三角形聯合值域中標出 X 加 Y 小於等於 1 的事件區域。右圖在同一三角形中標出固定 x 的垂直切片與固定 y 的水平切片。">
  <figcaption><span class="topic-figure__label">Fig. 3.3.</span> 左圖的深色區域同時滿足 $x\leqslant y$ 與 $x+y\leqslant1$。右圖顯示求邊際 pdf 時使用的兩種切片: 固定 $x=x_0$ 時，$y$ 由 $x_0$ 變到 $1$；固定 $y=y_0$ 時，$x$ 由 $0$ 變到 $y_0$。</figcaption>
</figure>

## 由聯合 pdf 求邊際 pdf

只關心 $X$ 時，對固定的 $x$，要把所有可能與它搭配的 $y$ 都積分進來。只關心 $Y$ 時則反過來處理。

Tonelli 定理保證下列兩個積分函數皆為 Borel 可測函數，且除了某個長度為 $0$ 的例外集合之外皆為有限值:

$$
x\longmapsto
\int_{-\infty}^{\infty}f_{XY}(x,y)\,dy,
\qquad
y\longmapsto
\int_{-\infty}^{\infty}f_{XY}(x,y)\,dx
$$

若右側在例外集合上為 $\infty$，便在該集合上將函數值改定為 $0$，並將所得的有限函數分別記為 $f_X$ 與 $f_Y$。

<div id="definition-36" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 3.6</div>

令 $(X,Y)$ 具有聯合 pdf $f_{XY}$，並令 $f_X$ 與 $f_Y$ 為上述兩個切片積分所決定的有限函數。則稱 $f_X$ 與 $f_Y$ 分別為 $X$ 與 $Y$ 的**邊際機率密度函數 (marginal probability density function, marginal pdf)**。
</div>

這兩個函數確實描述 $X$ 與 $Y$ 各自的機率。以 $X$ 為例，對任意 Borel 集合 (Borel set) $B\subseteq\mathbb{R}$，事件 $X\in B$ 等價於 $(X,Y)\in B\times\mathbb{R}$，因此由 [Definition 3.5](/teaching-topics/joint-probability-density-functions/#definition-35) 與 Tonelli 定理可得

$$
\begin{aligned}
\mathbb{P}(X\in B)
&=
\mathbb{P}\bigl((X,Y)\in B\times\mathbb{R}\bigr) \\[0.4em]
&=
\int_B\int_{-\infty}^{\infty}
f_{XY}(x,y)\,dy\,dx \\[0.4em]
&=
\int_B
\left(
\int_{-\infty}^{\infty}
f_{XY}(x,y)\,dy
\right)dx \\[0.4em]
&=
\int_B f_X(x)\,dx
\end{aligned}
$$

將長度為 $0$ 的例外集合上的函數值改為 $0$，不會改變最後一個積分。由 $f_{XY}$ 的非負性可知 $f_X$ 亦為非負函數；再取 $B=\mathbb{R}$，便可得到

$$
\int_{-\infty}^{\infty}f_X(x)\,dx
=
1
$$

所以 $f_X$ 符合 [Proposition 2.4](/teaching-topics/continuous-random-variables-pdf/#proposition-24) 的兩項條件，並且確實是 $X$ 的 pdf。$f_Y$ 的結果亦同。

回到 [Example 3.4](#example-34)。對固定的 $x\in[0,1]$，聯合值域要求 $x\leqslant y\leqslant1$，因此

$$
\begin{aligned}
f_X(x)
&=
\int_x^1 2(x+y)\,dy \\[0.4em]
&=
\left[
2xy+y^2
\right]_{y=x}^{y=1}
=
1+2x-3x^2
\end{aligned}
$$

對固定的 $y\in[0,1]$，則有 $0\leqslant x\leqslant y$，所以

$$
\begin{aligned}
f_Y(y)
&=
\int_0^y 2(x+y)\,dx \\[0.4em]
&=
\left[
x^2+2xy
\right]_{x=0}^{x=y}
=
3y^2
\end{aligned}
$$

將值域外的密度補成 $0$，完整結果為

$$
f_X(x)
=
\begin{cases}
1+2x-3x^2, & 0\leqslant x\leqslant1,\\
0, & \text{其他}
\end{cases}
$$

以及

$$
f_Y(y)
=
\begin{cases}
3y^2, & 0\leqslant y\leqslant1,\\
0, & \text{其他}
\end{cases}
$$

兩個邊際 pdf 都應各自在實數線上積分為 $1$。直接檢查可得

$$
\int_0^1(1+2x-3x^2)\,dx
=
1,
\qquad
\int_0^1 3y^2\,dy
=
1
$$

求出邊際 pdf 之後，$f_X$ 的表示式與值域都不能殘留 $y$，$f_Y$ 亦不能殘留 $x$。不過，決定積分上下限時，仍必須回到原本的聯合值域。

## 聯合 pdf 的公式與非零範圍

<div id="example-35" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.5 (The Range Still Matters)</div>

令

$$
f_{XY}(x,y)
=
\begin{cases}
e^{-y}, & 0<x<y<\infty,\\
0, & \text{其他}
\end{cases}
$$

這個函數在整個平面的積分為

$$
\int_0^\infty\int_0^y e^{-y}\,dx\,dy
=
\int_0^\infty ye^{-y}\,dy
=
1
$$

因此，它確實是一個聯合 pdf。

雖然範圍內的公式 $e^{-y}$ 沒有出現 $x$，但非零範圍仍含有條件 $0<x<y$，所以這個聯合 pdf 仍同時受到 $x$ 與 $y$ 的限制。

對固定的 $x>0$，$y$ 必須由 $x$ 變到 $\infty$，故

$$
f_X(x)
=
\int_x^\infty e^{-y}\,dy
=
e^{-x}
$$

對固定的 $y>0$，$x$ 則由 $0$ 變到 $y$，所以

$$
f_Y(y)
=
\int_0^y e^{-y}\,dx
=
ye^{-y}
$$

兩個結果在正實數以外皆為 $0$。
</div>

## 由聯合 cdf 求邊際 cdf

第二章已將 $F_X$ 與 $F_Y$ 定義為單一隨機變數的 cdf。在聯合分配的脈絡中，它們也稱為**邊際累積分配函數 (marginal cumulative distribution function, marginal cdf)**。

<div id="definition-37" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 3.7</div>

令 $(X,Y)$ 為二元隨機向量。定義

$$
F_X(x)
=
\mathbb{P}(X\leqslant x),
\qquad
F_Y(y)
=
\mathbb{P}(Y\leqslant y)
$$

則稱 $F_X$ 與 $F_Y$ 分別為 $X$ 與 $Y$ 的邊際 cdf。
</div>

<div id="proposition-34" class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Proposition 3.4 (Recovering Marginal cdfs)</div>

令 $F_{XY}$ 為 $(X,Y)$ 的聯合 cdf。則

$$
F_X(x)
=
\lim_{t\to\infty}F_{XY}(x,t),
\qquad
F_Y(y)
=
\lim_{t\to\infty}F_{XY}(t,y)
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.** 固定 $x$。當 $n\to\infty$ 時，事件 $\lbrace X\leqslant x,Y\leqslant n\rbrace$ 遞增至 $\lbrace X\leqslant x\rbrace$。由機率對遞增事件序列的連續性可得

$$
\lim_{n\to\infty}F_{XY}(x,n)
=
\mathbb{P}(X\leqslant x)
=
F_X(x)
$$

若 $t\to\infty$，令 $n=\lfloor t\rfloor$。由事件的包含關係可得

$$
F_{XY}(x,n)
\leqslant
F_{XY}(x,t)
\leqslant
F_X(x)
$$

因為兩側皆趨近 $F_X(x)$，所以

$$
\lim_{t\to\infty}F_{XY}(x,t)
=
F_X(x)
$$

固定 $y$ 時，事件 $\lbrace X\leqslant n,Y\leqslant y\rbrace$ 遞增至 $\lbrace Y\leqslant y\rbrace$，故

$$
\lim_{n\to\infty}F_{XY}(n,y)
=
F_Y(y)
$$

再由事件的包含關係可得

$$
F_{XY}(n,y)
\leqslant
F_{XY}(t,y)
\leqslant
F_Y(y)
$$

所以

$$
\lim_{t\to\infty}F_{XY}(t,y)
=
F_Y(y)
$$

原式得證。<span class="topic-qed">$\square$</span>
</div>

有時會將 [Proposition 3.4](#proposition-34) 簡寫為 $F_X(x)=F_{XY}(x,\infty)$。這裡的 $\infty$ 代表取極限，並不是聯合 cdf 的實數輸入。

<div id="interlude-33" class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 3.3</div>

邊際分配不能反推出聯合分配。令 $U$ 以相同機率取 $0$ 或 $1$。隨機向量 $(U,U)$ 的兩個邊際分配都與 $U$ 相同，而且兩個座標永遠相等。

另一方面，$(U,1-U)$ 的兩個邊際分配也都與 $U$ 相同，但兩個座標永遠不相等。這兩個隨機向量具有相同的邊際分配，聯合分配卻完全不同。
</div>

## 本篇小結

計算區域機率時，聯合值域與事件範圍必須同時成立。調換二重積分的順序時，必須依新的切片方向重新寫出上下限。

邊際 pdf 可由聯合 pdf 對另一個變數積分得到。邊際 cdf 則可由聯合 cdf 令另一個門檻趨近 $\infty$ 得到。邊際分配只保留單一變數的資訊，通常不足以還原兩個變數的聯合關係。

[下一篇文章](/teaching-topics/conditional-distributions/)會固定其中一個變數的取值，並重新調整該切片上的 pmf 或 pdf，得到條件分配。

## 參考文獻與延伸閱讀

- 黃文璋，2003，《機率論》，初版，華泰文化。
- 黃文璋，2003，《數理統計》，初版，華泰文化。
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Joseph K. Blitzstein and Jessica Hwang. 2019. *Introduction to Probability*. 2nd ed. Chapman and Hall/CRC.
