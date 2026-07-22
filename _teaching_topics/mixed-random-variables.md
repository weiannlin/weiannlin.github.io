---
title: "混合型隨機變數"
subtitle: "Mixed Random Variables"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 5
order: 205
permalink: /teaching-topics/mixed-random-variables/
date: 2026-06-08
published: true
excerpt: "混合型隨機變數同時具有單點機率與連續密度。CDF 可同時呈現跳躍與連續累積，計算時則把離散部分加總、連續部分積分。"
---

[上一篇文章](/teaching-topics/continuous-random-variables-pdf/)討論了連續型隨機變數與 pdf。到目前為止，我們已經分別處理離散型與連續型隨機變數。離散型的機率集中在單點上，事件機率由 pmf 加總取得；連續型的單點不具有正機率，事件機率由 pdf 的面積取得。

實際建模時，兩種情形可能同時出現。以每日降雨量為例，某一天完全沒有下雨時，降雨量正好等於 $0$，這是一個單點事件；若當天有下雨，降雨量則可能在某個區間內連續變動。這樣的隨機變數便稱為**混合型隨機變數 (mixed random variable)**。

## CDF 同時記錄跳躍與連續累積

混合型隨機變數最適合先從 CDF 觀察。若某個點具有正機率，CDF 會在該點發生跳躍。若某段區間上的機率由密度面積取得，CDF 會在該區間上連續上升。

<figure class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/mixed-random-variable-cdf.svg" alt="混合型隨機變數的 CDF 在 0 發生跳躍，並在 0 到 1 之間連續上升。">
  <figcaption><span class="topic-figure__label">Fig. 2.13.</span> 混合型隨機變數的 CDF 可能同時具有跳躍與連續上升。圖中 $x=0$ 的跳躍高度為 $\mathbb{P}(X=0)=1/3$，而 $0<x<1$ 的上升來自連續密度的累積。</figcaption>
</figure>

<div id="definition-25" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.5</div>

令 $X$ 為隨機變數，並令

$$
A=\lbrace x\in\mathbb{R}\mid \mathbb{P}(X=x)>0\rbrace,
\qquad
\alpha=\sum_{x\in A}\mathbb{P}(X=x)
$$

集合 $A$ 至多可數。這是因為對每個正整數 $m$，滿足 $\mathbb{P}(X=x)\geqslant 1/m$ 的 $x$ 至多只有 $m$ 個，而 $A$ 是這些有限集合的可數聯集。

若 $0<\alpha<1$，且其餘機率在正規化後可由 pdf $f_c$ 描述，令連續部分對整體分配的密度為 $f_X^{(c)}(x)=(1-\alpha)f_c(x)$。若對任意 Borel 集合 $B$，皆有

$$
\mathbb{P}(X\in B)
=
\sum_{x\in A\cap B}\mathbb{P}(X=x)
+
\int_B f_X^{(c)}(x)\,dx
$$

則稱 $X$ 為**混合型隨機變數 (mixed random variable)**。將單點部分與連續部分各自正規化後，其 CDF 可唯一寫成

$$
F_X(x)=\alpha F_d(x)+(1-\alpha)F_c(x),
\qquad x\in\mathbb{R}
$$

其中 $F_d$ 與 $F_c$ 分別是正規化後的離散型與連續型 CDF。若 $\alpha=0$，分配為純連續型；若 $\alpha=1$，分配為純離散型，這兩種情形都不稱為混合型。

</div>

此時只寫 pmf 或只寫 pdf 都不足以描述整個分配。pmf 只能記錄單點機率，pdf 的面積只能記錄連續部分。CDF 則仍可完整呈現兩者。

<div id="example-25-mixed" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.5 (A CDF with a Jump at Zero)</div>

令 $X$ 的 CDF 為

$$
F_X(x)=
\left\{
\begin{array}{c@{\quad}l}
0, & x<0,\\[0.35em]
1-0.8e^{-x}, & x\geqslant 0
\end{array}
\right.
$$

這個 CDF 在 $x=0$ 的函數值為 $F_X(0)=1-0.8=0.2$，左極限為 $F_X(0^-)=0$，因此 $\mathbb{P}(X=0)=0.2$。當 $x>0$ 時，CDF 的導數為 $0.8e^{-x}$，這是連續部分對整體分配的密度。對任意 Borel 集合 $B$，完整分配可寫為

$$
\mathbb{P}(X\in B)
=
0.2\,\mathbf{1}_B(0)
+
\int_{B\cap(0,\infty)}0.8e^{-x}\,dx
$$

其中 $\mathbf{1}_B(0)$ 為指標函數 (indicator function)；若 $0\in B$，其值為 $1$，否則為 $0$。若將連續部分正規化為總面積等於 $1$ 的分配，其 pdf 為 $f_c(x)=e^{-x}$，$x>0$，而該部分在整體分配中的比例為 $0.8$。因此，單點機率與連續密度須分開表示。
</div>

## 一個簡化的降雨量模型

令 $X$ 表示某日降雨量，單位為公分。假設該日不下雨的機率為 $1/3$，因此 $\mathbb{P}(X=0)=1/3$。

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

這個 CDF 在 $x=0$ 有跳躍，並在 $0<x<1$ 上連續上升。若已知當天有下雨，連續部分正規化後的 pdf 為

$$
f_c(x)=
\left\{
\begin{array}{c@{\quad}l}
1, & 0<x<1,\\[0.35em]
0, & \text{otherwise}
\end{array}
\right.
$$

連續部分對整體分配的密度為 $f_X^{(c)}(x)=(2/3)f_c(x)$。因此，對任意 Borel 集合 $B$，完整分配可寫為

$$
\mathbb{P}(X\in B)
=
\frac{1}{3}\mathbf{1}_B(0)
+
\frac{2}{3}\int_{B\cap(0,1)}1\,dx
$$

第一項是 $x=0$ 的單點機率，第二項是連續區間的密度面積，兩者在計算事件機率時相加。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

若從條件分配的角度描述，下雨時的降雨量可視為在 $(0,1)$ 上的均勻分配，其 pdf $f_c$ 的總面積為 $1$。乘上下雨的機率 $2/3$ 後，$f_X^{(c)}$ 的總面積才是連續部分在整體分配中所占的機率 $2/3$。
</div>

## 離散加總與連續積分一起使用

混合型隨機變數的計算方式很直接。若事件包含某個具有正機率的單點，就把該點機率加進來；若事件包含某段連續區間，就再加上該區間的密度面積。

<div id="example-29" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.6 (A Mixed Rainfall Model)</div>

延續上面的降雨量模型。若要求 $X\leqslant 1/2$ 的機率，事件可拆成兩部分。第一部分是完全沒下雨，也就是 $X=0$；第二部分是有下雨，且降雨量落在 $(0,1/2]$。

依上述兩部分拆分，所求機率為

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

這個例子同時使用了離散型的加總與連續型的積分。
</div>

## 後續量數仍使用相同拆分原則

後續定義期望值、變異數與標準差時，仍會把單點部分加總、把連續部分積分，再依各自的混合比例合併。因此，混合型隨機變數並非使用第三套計算方法，而是要求我們同時保留單點機率與連續密度。

## 本篇小結

混合型隨機變數同時具有單點機率與連續密度。其 CDF 會在單點機率處發生跳躍，並在連續部分依密度面積向上累積。

若事件同時包含單點與連續區間，便把相應的單點機率與連續密度積分相加。後續計算期望值、變異數與標準差時，也會沿用相同的拆分原則。

下一篇[期望值，隨機變數的平均位置](/teaching-topics/expected-value-random-variables/)會開始討論如何用機率權重整理一個代表分配位置的數值。

## 參考文獻與延伸閱讀

- 黃文璋，2003，《機率論》，初版，華泰文化。
- 黃文璋，2003，《數理統計》，初版，華泰文化。
- Patrick Billingsley. 1995. *Probability and Measure*. 3rd ed. Wiley.
- William Feller. 1968. *An Introduction to Probability Theory and Its Applications*. Vol. 1, 3rd ed. Wiley.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Sheldon M. Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
