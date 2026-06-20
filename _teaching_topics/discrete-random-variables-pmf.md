---
title: "離散型隨機變數與機率質量函數"
subtitle: "Discrete Random Variables and Probability Mass Functions"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 3
order: 203
permalink: /teaching-topics/discrete-random-variables-pmf/
date: 2026-05-19
published: true
excerpt: "離散型隨機變數的機率集中在有限或可數個取值上。PMF 記錄各單點機率，事件機率則由對應單點機率加總取得。"
---

[上一篇文章](/teaching-topics/probability-accumulates/)已經提過，有些隨機變數的機率是靠「加總」取得的。若隨機變數只會取到有限或可數無限多個值，則事件 $\{X\leqslant x\}$ 的機率，就是把不超過 $x$ 的那些單點機率加起來。

本篇細講這個加總如何被整理成一個函數。這個函數稱為**機率質量函數 (probability mass function, PMF)**。它把離散型隨機變數每一個可能取值上的機率列出來，使許多事件機率都能轉化為加總問題。

## 離散型隨機變數

令 $X$ 為一個隨機變數。若 $X$ 的可能取值集合為有限集合或可數無限集合，則稱 $X$ 為**離散型隨機變數 (discrete random variable)**。這個可能取值集合記為

$$
\mathcal{R}_X=\{X(\omega)\mid \omega\in S\}
$$

此集合也常稱為 $X$ 的**值域 (range)** 或**支撐集 (support)**。這裡的值域與一般數學中函數的值域並無差異，因為隨機變數本來就是定義在樣本空間上的函數。不同之處在於，機率論會進一步在這些可能取值上指定機率。

在離散型的情形中，$\mathcal{R}_X$ 可以逐一列出，例如

$$
\mathcal{R}_X=\{0,1\},\qquad
\mathcal{R}_X=\{1,2,3,4,5,6\},\qquad
\mathcal{R}_X=\{0,1,2,\ldots\}
$$

只要可能取值可以逐項列出，機率就可以逐項相加。

<div class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.3</div>

令 $X$ 為離散型隨機變數，其可能取值集合為 $\mathcal{R}_X$。定義

$$
p_X(x)=\mathbb{P}(X=x),\qquad x\in\mathcal{R}_X
$$

並令 $p_X(x)=0$，若 $x\notin\mathcal{R}_X$。若 $p_X$ 滿足

$$
p_X(x)\geqslant 0,\qquad x\in\mathcal{R}_X
$$

且

$$
\sum_{x\in\mathcal{R}_X}p_X(x)=1
$$

則稱 $p_X$ 為 $X$ 的**機率質量函數 (probability mass function, PMF)**。
</div>

這裡的 $\mathbb{P}(X=x)$ 是簡寫。完整而言，它指的是事件

$$
\{X=x\}=\{\omega\in S\mid X(\omega)=x\}
$$

的機率。換言之，PMF 的每一個函數值都是一個事件機率。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

PMF 之所以稱為「機率質量函數」，是因為離散型隨機變數的機率集中在一個一個單點上。每個可能取值像是一個質點，$p_X(x)$ 則記錄該點具有多少機率質量。
</div>

## 由 PMF 計算事件機率

PMF 不只記錄單點機率，也足以計算所有由 $X$ 所決定的事件機率。若 $A\subset\mathbb{R}$，則

$$
\mathbb{P}(X\in A)
=
\sum_{x\in A\cap\mathcal{R}_X}p_X(x)
$$

這個公式表示，若要計算 $X$ 落在某個集合 $A$ 中的機率，只要找出 $\mathcal{R}_X$ 中同時落在 $A$ 裡的那些點，再把它們的 PMF 值相加。

特別地，若 $A=(-\infty,x]$，則對任意實數 $x$，可得

$$
F_X(x)
=
\mathbb{P}(X\leqslant x)
=
\sum_{t\leqslant x}p_X(t)
$$

這正是前一篇提到的離散型 CDF。CDF 是把門檻左側的機率質量逐步累積起來。

<div class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.2 (Two Balls without Replacement)</div>

箱中有四顆大小形狀完全相同、分別編號 $0,1,2,3$ 的球。從中一次抽取兩顆球，不考慮抽取順序，令 $X$ 表示兩顆球的號碼總和。

此時樣本空間可寫為

$$
S=\{(0,1),(0,2),(0,3),(1,2),(1,3),(2,3)\}
$$

六個結果均等可能。依序計算號碼總和可得

| $x$ | 1 | 2 | 3 | 4 | 5 |
| --- | --- | --- | --- | --- | --- |
| $p_X(x)$ | $1/6$ | $1/6$ | $2/6$ | $1/6$ | $1/6$ |

因此 $X$ 的 PMF 可寫為

$$
p_X(x)=
\left\{
\begin{array}{c@{\quad}l}
1/6, & x=1,2,4,5,\\[0.35em]
1/3, & x=3,\\[0.35em]
0, & \text{otherwise}
\end{array}
\right.
$$

若要求號碼總和為 $3$ 的機率，由 PMF 表可得

$$
\mathbb{P}(X=3)=p_X(3)=\frac{1}{3}
$$

若要求號碼總和不超過 $3$ 的機率，則把 $x=1,2,3$ 的機率相加，此即

$$
F_X(3)
=
\mathbb{P}(X\leqslant 3)
=
p_X(1)+p_X(2)+p_X(3)
=
\frac{1}{6}+\frac{1}{6}+\frac{1}{3}
=
\frac{2}{3}
$$

</div>

<div class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 2.3</div>

在離散型隨機變數中，區間端點是否包含可能改變機率。以上例而言，若不包含左端點 $1$，則

$$
\mathbb{P}(1<X\leqslant 3)=p_X(2)+p_X(3)=\frac{1}{2}
$$

但若我們加入 $1$ 這個單點，則有

$$
\mathbb{P}(1\leqslant X\leqslant 3)=p_X(1)+p_X(2)+p_X(3)=\frac{2}{3}
$$

差異正是左端點 $x=1$ 上的單點機率 $p_X(1)=1/6$。這一點和連續型隨機變數很不一樣。
</div>

## PMF 的基本性質

PMF 有兩個基本要求。每個單點機率不可為負，所有可能取值上的機率總和必須為 $1$。反過來，若一個函數滿足這兩個條件，便可作為某個離散型隨機變數的 PMF。

<div class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Proposition 2.2 (PMF Conditions)</div>

令 $\mathcal{R}_X$ 為有限或可數無限集合。若函數 $p_X:\mathcal{R}_X\to\mathbb{R}$ 滿足

$$
p_X(x)\geqslant 0,\qquad x\in\mathcal{R}_X
$$

且

$$
\sum_{x\in\mathcal{R}_X}p_X(x)=1
$$

則 $p_X$ 可作為某個離散型隨機變數 $X$ 在 $\mathcal{R}_X$ 上的 PMF。
</div>

<div class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.3 (A Geometric Tail)</div>

令

$$
p_X(x)=
\left\{
\begin{array}{c@{\quad}l}
c\left(\frac{1}{2}\right)^x, & x=1,2,\ldots,\\[0.35em]
0, & \text{otherwise}
\end{array}
\right.
$$

其中 $c$ 為常數。若 $p_X$ 是 PMF，則其總和必須為 $1$。

$$
1
=
\sum_{x=1}^{\infty}c\left(\frac{1}{2}\right)^x
=
c\sum_{x=1}^{\infty}\left(\frac{1}{2}\right)^x
=
c
$$

故 $c=1$。由此可計算任意 $x$ 的機率，例如

$$
\mathbb{P}(X=5)=p_X(5)=\left(\frac{1}{2}\right)^5=\frac{1}{32}
$$

</div>

## 由 CDF 求得 PMF

PMF 可以加總成 CDF；反過來，離散型隨機變數的 PMF 也可以由 CDF 的跳躍高度求得。這是離散型隨機變數的基本性質。

未免符號混淆，先將 $F_X$ 在 $a$ 左側的極限記為

$$
F_X(a^-)=\lim_{x\uparrow a}F_X(x)
$$

若 $X$ 為離散型隨機變數，則有下列關係。

<div class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Proposition 2.3 (PMF from CDF Jumps)</div>

對任意 $a\in\mathbb{R}$，皆有

$$
p_X(a)
=
\mathbb{P}(X=a)
=
F_X(a)-F_X(a^-)
$$

</div>

由集合關係可知，事件 $\{X\leqslant a\}$ 比事件 $\{X<a\}$ 多出的部分，正是事件 $\{X=a\}$。因此 CDF 在 $a$ 的跳躍高度，就是 $X=a$ 的單點機率。

<figure class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/cdf-jump-pmf.svg" alt="離散型 CDF 在 a 點的跳躍。空心點表示左側極限，實心點表示函數值，兩者高度差為單點機率。">
  <figcaption><span class="topic-figure__label">Fig. 2.8.</span> 在跳躍點 $a$ 上，空心點表示 $F_X(a^-)$，實心點表示 $F_X(a)$。兩者的高度差正是 $p_X(a)=\mathbb{P}(X=a)$。</figcaption>
</figure>

若 $a$ 不是 $X$ 的可能取值，則 $p_X(a)=0$，此時 CDF 在 $a$ 不會跳躍。換言之，若 $F_X(a)=F_X(a^-)$，左右高度沒有差距，該點就沒有單點機率。若 $a$ 是 $X$ 的可能取值，跳躍高度便等於該點的機率質量。

以 Example 2.2 為例，$x=3$ 的機率質量為 $1/3$。因此 CDF 在 $3$ 的跳躍高度也是 $1/3$。

$$
F_X(3)-F_X(3^-)=p_X(3)=\frac{1}{3}
$$

這個關係也說明，離散型的 CDF 與 PMF 相互決定。只要知道 PMF，就能加總得到 CDF；只要知道 CDF 的每個跳躍高度，也能求得 PMF。

若想親手調整單點機率並觀察 CDF 的跳躍，可以參考互動展示 [From&nbsp;PMF&nbsp;to&nbsp;CDF](/demos/pmf-cdf/)。

## 本篇小結

離散型隨機變數的可能取值可以逐一列出，機率也集中在這些單點上。PMF 記錄每個可能取值的單點機率，可寫為

$$
p_X(x)=\mathbb{P}(X=x)
$$

事件機率則由對應單點機率相加得到。

$$
\mathbb{P}(X\in A)
=
\sum_{x\in A\cap\mathcal{R}_X}p_X(x)
$$

CDF 可由 PMF 加總得到。

$$
F_X(x)=\sum_{t\leqslant x}p_X(t)
$$

PMF 則可由 CDF 的跳躍高度求得。

$$
p_X(a)=F_X(a)-F_X(a^-)
$$

下一篇[連續型隨機變數與機率密度函數](/teaching-topics/continuous-random-variables-pdf/)會轉向連續型隨機變數。當單點不再具有正機率時，機率不再逐點相加，而要改由密度函數在區間上的面積來計算。

## 參考文獻與延伸閱讀

- 黃文璋，2003，《機率論》，初版，華泰文化。
- 黃文璋，2003，《數理統計》，初版，華泰文化。
- Patrick Billingsley. 1995. *Probability and Measure*. 3rd ed. Wiley.
- William Feller. 1968. *An Introduction to Probability Theory and Its Applications*. Vol. 1, 3rd ed. Wiley.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Sheldon M. Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Joseph K. Blitzstein and Jessica Hwang. 2019. *Introduction to Probability*. 2nd ed. Chapman and Hall/CRC.
