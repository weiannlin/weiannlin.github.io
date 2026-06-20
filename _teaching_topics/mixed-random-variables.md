---
title: "混合型隨機變數"
subtitle: "Mixed Random Variables"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 7
order: 207
permalink: /teaching-topics/mixed-random-variables/
date: 2026-06-08
published: true
excerpt: "混合型隨機變數同時具有單點機率與連續密度。CDF 可同時呈現跳躍與連續累積，計算時則把離散部分加總、連續部分積分。"
---

[上一篇文章](/teaching-topics/variance-standard-deviation/)討論期望值、變異數與標準差。到目前為止，我們已經分別處理離散型與連續型隨機變數。離散型的機率集中在單點上，事件機率由 PMF 加總取得；連續型的單點不具有正機率，事件機率由 PDF 的面積取得。

實際建模時，兩種情形可能同時出現。以每日降雨量為例，某一天完全沒有下雨時，降雨量正好等於 $0$，這是一個單點事件；若當天有下雨，降雨量則可能在某個區間內連續變動。這樣的隨機變數便稱為**混合型隨機變數 (mixed random variable)**。

## CDF 同時記錄跳躍與連續累積

混合型隨機變數最適合先從 CDF 觀察。若某個點具有正機率，CDF 會在該點發生跳躍。若某段區間上的機率由密度面積取得，CDF 會在該區間上連續上升。

<figure class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/mixed-random-variable-cdf.svg" alt="混合型隨機變數的 CDF 在 0 發生跳躍，並在 0 到 1 之間連續上升。">
  <figcaption><span class="topic-figure__label">Fig. 2.15.</span> 混合型隨機變數的 CDF 可能同時具有跳躍與連續上升。圖中 $x=0$ 的跳躍高度為 $\mathbb{P}(X=0)=1/3$，而 $0<x<1$ 的上升來自連續密度的累積。</figcaption>
</figure>

<div class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.9</div>

若隨機變數 $X$ 的機率分配可拆成離散部分與連續部分，亦即對某些點 $x_i$ 有

$$
\mathbb{P}(X=x_i)>0
$$

且在某些區間上的機率由密度函數積分取得，則稱 $X$ 為**混合型隨機變數 (mixed random variable)**。

較完整地說，其 CDF 可唯一寫成

$$
F_X(x)=\alpha F_d(x)+(1-\alpha)F_c(x),
\qquad 0\leqslant\alpha\leqslant 1
$$

其中 $F_d$ 與 $F_c$ 分別是正規化後的離散型與連續型 CDF，而 $\alpha$ 表示全部離散質點所佔的總機率。

</div>

此時只寫 PMF 或只寫 PDF 都不足以描述整個分配。PMF 只能記錄單點機率，PDF 的面積只能記錄連續部分。CDF 則仍可完整呈現兩者。

## 一個簡化的降雨量模型

令 $X$ 表示某日降雨量，單位為公分。假設該日不下雨的機率為 $1/3$，因此

$$
\mathbb{P}(X=0)=\frac{1}{3}
$$

若該日有下雨，則降雨量落在 $0$ 到 $1$ 公分之間，且在此區間上均勻分配。若要寫出整體 CDF，可先把離散部分與連續部分各自寫成正規的分配函數。

離散部分是完全沒下雨所造成的單點分配，記為 $F_d$，則

$$
F_d(x)=
\left\{
\begin{array}{c@{\quad}l}
0, & x<0,\\[0.35em]
1, & x\geqslant 0
\end{array}
\right.
$$

連續部分是已知當天有下雨後的降雨量分配，記為 $F_c$。在本例中，它是 $(0,1)$ 上的均勻分配，因此

$$
F_c(x)=
\left\{
\begin{array}{c@{\quad}l}
0, & x\leqslant 0,\\[0.35em]
x, & 0<x<1,\\[0.35em]
1, & x\geqslant 1
\end{array}
\right.
$$

整體分配由這兩個 CDF 按照發生比例混合。由於不下雨的機率為 $1/3$，下雨的機率為 $2/3$，故

$$
F_X(x)
=
\frac{1}{3}F_d(x)
+
\frac{2}{3}F_c(x)
$$

將 $F_d$ 與 $F_c$ 代入後，可得

$$
F_X(x)=
\left\{
\begin{array}{c@{\quad}l}
0, & x<0,\\[0.35em]
\frac{1}{3}+\frac{2}{3}x, & 0\leqslant x<1,\\[0.35em]
1, & x\geqslant 1
\end{array}
\right.
$$

這個 CDF 在 $x=0$ 有跳躍，並在 $0<x<1$ 上連續上升。若改從密度的角度描述，連續部分本身的 PDF 為

$$
f_c(x)=
\left\{
\begin{array}{c@{\quad}l}
1, & 0<x<1,\\[0.35em]
0, & \text{otherwise}
\end{array}
\right.
$$

而離散部分本身的 PMF 可記為

$$
f_d(x)=
\left\{
\begin{array}{c@{\quad}l}
1, & x=0,\\[0.35em]
0, & \text{otherwise}
\end{array}
\right.
$$

若要把兩部分並列成混合型機率函數，可寫成

$$
f_X(x)
=
\frac{1}{3}f_d(x)
+
\frac{2}{3}f_c(x)
$$

在本例中也就是

$$
f_X(x)=
\left\{
\begin{array}{c@{\quad}l}
\frac{1}{3}, & x=0,\\[0.35em]
\frac{2}{3}, & 0<x<1,\\[0.35em]
0, & \text{otherwise}
\end{array}
\right.
$$

這裡的 $f_X$ 是混合型分配的記法，不作純連續型 PDF 使用。特別地，$\frac{1}{3}$ 是 $x=0$ 的單點機率，而 $\frac{2}{3}$ 是 $0<x<1$ 上的機率密度，二者不可混為一談。換句話說，$f_c$ 仍是正規 PDF，權重 $2/3$ 放在外面。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

若從條件分配的角度描述，下雨時的降雨量可視為在 $(0,1)$ 上的均勻分配，其密度為 $1$。因此，$f_c$ 的總面積仍為 $1$。真正進入整體分配時，才乘上下雨的機率 $2/3$。
</div>

## 兩種算法一起使用

混合型隨機變數的計算方式很直接。若事件包含某個具有正機率的單點，就把該點機率加進來；若事件包含某段連續區間，就再加上該區間的密度面積。

<div id="example-29" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.9 (A Mixed Rainfall Model)</div>

延續上面的降雨量模型。若要求 $X\leqslant 1/2$ 的機率，事件可拆成兩部分。第一部分是完全沒下雨，也就是 $X=0$；第二部分是有下雨，且降雨量落在 $(0,1/2]$。

因此

$$
\begin{aligned}
\mathbb{P}\left(X\leqslant\frac{1}{2}\right)
&=
\mathbb{P}(X=0)
+\mathbb{P}\left(0<X\leqslant\frac{1}{2}\right) \\[0.45em]
&=
\frac{1}{3}
+\frac{2}{3}\int_0^{1/2}1\,dx \\[0.45em]
&=
\frac{1}{3}+\frac{1}{3}
=
\frac{2}{3}
\end{aligned}
$$

這個例子同時使用了離散型的加總與連續型的積分。混合型隨機變數的計算並不是第三套全新的方法，而是把前面兩套方法放在同一個分配中使用。
</div>

## 期望值與變異數

函數期望值也可以用相同方式拆開。若

$$
F_X(x)=\alpha F_d(x)+(1-\alpha)F_c(x)
$$

其中 $0\leqslant\alpha\leqslant 1$，$F_d$ 是正規化後的離散部分 CDF，對應的離散機率函數為 $f_d$。$F_c$ 是正規化後的連續部分 CDF，對應 PDF 為 $f_c$，則

<div class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Proposition 2.9 (Mixed Calculation Rule)</div>

在相關加總與積分皆收斂時，

$$
\mathbb{E}[g(X)]
=
\alpha\sum_i g(x_i)f_d(x_i)
+(1-\alpha)\int_{-\infty}^{\infty}g(x)f_c(x)\,dx
$$

</div>

取 $g(x)=x$ 時，可得到期望值；取 $g(x)=x^2$ 時，可先求 $\mathbb{E}(X^2)$，再用變異數的計算公式求得 $\mathrm{Var}(X)$。

<div class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.10 (Mean and Variance of the Mixed Rainfall Model)</div>

延續 [Example 2.9 的降雨量模型](#example-29)。由混合型的計算規則可得

$$
\mathbb{E}(X)
=
\frac{1}{3}\cdot 0
+\frac{2}{3}\int_0^1 x\cdot 1\,dx
=
\frac{1}{3}
$$

接著計算二次方的期望值。

$$
\mathbb{E}(X^2)
=
\frac{1}{3}\cdot 0^2
+\frac{2}{3}\int_0^1 x^2\cdot 1\,dx
=
\frac{2}{9}
$$

因此

$$
\mathrm{Var}(X)
=
\mathbb{E}(X^2)-[\mathbb{E}(X)]^2
=
\frac{2}{9}-\left(\frac{1}{3}\right)^2
=
\frac{1}{9}
$$

標準差為變異數開根號而得，因此

$$
\mathrm{SD}(X)
=
\sqrt{\mathrm{Var}(X)}
=
\frac{1}{3}
$$

標準差的定義只依賴變異數，與隨機變數屬於離散型、連續型或混合型無關。

</div>

## 本篇小結

混合型隨機變數同時具有單點機率與連續密度。其 CDF 會在單點機率處發生跳躍，並在連續部分依密度面積向上累積。

若事件同時包含單點與連續區間，機率便分兩部分計算。

$$
\text{單點機率加總}
\quad+\quad
\text{連續密度積分}
$$

期望值、變異數與標準差也使用相同原則。混合型隨機變數把兩種算法放在同一個模型中，也讓離散型與連續型的計算方式在同一篇文章中重新整理一次。

期望值描述了一個分配的「重心位置」所在，而標準差則說明這個分配的「變異程度」。這給我們一個自然的方向。當我們想要比較某些個體在不同群體中的數值高低，譬如一名學生在考試中取得數學成績 $60$ 分與自然成績 $80$ 分，哪個表現較為優異，便需要用到方才回顧的群體重心位置以及變異程度。這會帶出[下一篇文章](/teaching-topics/linear-transformations-standardization/)中的統計標準化。

## 參考文獻與延伸閱讀

- 黃文璋，2003，《數理統計》，初版，華泰文化。
- Patrick Billingsley. 1995. *Probability and Measure*. 3rd ed. Wiley.
- William Feller. 1968. *An Introduction to Probability Theory and Its Applications*. Vol. 1, 3rd ed. Wiley.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Sheldon M. Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
