---
title: "動差母函數"
subtitle: "Moment-Generating Functions"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 12
order: 212
permalink: /teaching-topics/moment-generating-functions/
date: 2026-06-21
published: true
excerpt: '動差母函數 $M_X(t)=\mathbb{E}(e^{tX})$ 把各階原動差收進同一個函數。若它在 $0$ 附近存在，對 $t$ 微分並令 $t=0$，即可得到 $\mathbb{E}(X^r)$。'
---

[上一篇文章](/teaching-topics/skewness-and-kurtosis/)用三階與四階標準化動差 (standardized moments) 描述偏態與峰態。到這裡，動差已經不只是單一量數，而是一整串能描述分配位置、分散程度與形狀的數值。

若只需要前幾階動差，可以直接由定義計算。不過，一旦需要系統地處理許多階原動差 (raw moments)，逐階加總或逐階積分便不夠有效。**動差母函數 (moment-generating function, MGF)** 正是為了把這些原動差放進同一個函數中處理。

## 由原動差到函數

令 $X$ 為隨機變數。對每個正整數 $r$，若 $\mathbb{E}(X^r)$ 存在，則稱它為 $X$ 的 $r$ 階原動差。動差母函數的作法，是先考慮指數函數 $e^{tX}$ 的期望值。

<div id="definition-217" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.17</div>

若存在某個 $h>0$，使得 $\mathbb{E}(e^{tX})$ 對所有 $t\in(-h,h)$ 皆存在，則定義

$$
M_X(t)=\mathbb{E}(e^{tX})
$$

為 $X$ 的**動差母函數 (moment-generating function, MGF)**，亦稱**動差生成函數**。

若 $X$ 為離散型隨機變數，機率質量函數 (probability mass function, PMF) 為 $p_X$，則

$$
M_X(t)
=
\sum_{x\in\mathcal{R}_X} e^{tx}p_X(x)
$$

若 $X$ 為連續型隨機變數，機率密度函數 (probability density function, PDF) 為 $f_X$，則

$$
M_X(t)
=
\int_{-\infty}^{\infty}e^{tx}f_X(x)\,dx
$$

</div>

定義中的 $t$ 是一個普通實數變數。加總或積分完成後，$M_X(t)$ 是 $t$ 的函數，不再是隨機變數。代入 $t=0$，可得

$$
M_X(0)=\mathbb{E}(e^0)=1
$$

因此，MGF 若要用來生成動差，至少必須在 $0$ 附近有定義。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

MGF 不一定對所有 $t$ 存在，也不一定對所有隨機變數存在。例如若 $X$ 的 PDF 為

$$
f_X(x)=\lambda e^{-\lambda x},
\qquad x>0,\quad \lambda>0
$$

則

$$
M_X(t)
=
\int_0^\infty e^{tx}\lambda e^{-\lambda x}\,dx
=
\frac{\lambda}{\lambda-t},
\qquad t<\lambda
$$

當 $t\geqslant \lambda$ 時，這個積分不再有限。這個例子說明，寫出 MGF 時必須同時標明它的存在範圍。
</div>

## 微分生成原動差

MGF 之所以稱為母函數 (generating function)，是因為它能用微分產生各階原動差。若把 $e^{tX}$ 對 $t$ 微分 $r$ 次，會得到 $X^r e^{tX}$；再令 $t=0$，便留下 $X^r$。

<div id="proposition-211" class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Proposition 2.11 (Generating Raw Moments)</div>

若 $M_X(t)$ 在 $0$ 附近存在，則對每個正整數 $r$，皆有

$$
M_X^{(r)}(0)
=
\left.
\frac{d^r}{dt^r}M_X(t)
\right|_{t=0}
=
\mathbb{E}(X^r)
$$

也就是

$$
M_X^{(r)}(0)=\mu_r'
$$

其中 $\mu_r'=\mathbb{E}(X^r)$ 為 $r$ 階原動差。

</div>

以連續型情形來看，證明的骨架如下。MGF 在 $0$ 附近存在時，可在適當條件下交換微分與積分順序，因此

$$
\begin{aligned}
\left.
\frac{d^r}{dt^r}M_X(t)
\right|_{t=0}
&=
\left.
\frac{d^r}{dt^r}
\int_{-\infty}^{\infty}e^{tx}f_X(x)\,dx
\right|_{t=0} \\[0.45em]
&=
\left.
\int_{-\infty}^{\infty}\frac{\partial^r}{\partial t^r}e^{tx}f_X(x)\,dx
\right|_{t=0} \\[0.45em]
&=
\left.
\int_{-\infty}^{\infty}x^r e^{tx}f_X(x)\,dx
\right|_{t=0} \\[0.45em]
&=
\int_{-\infty}^{\infty}x^r f_X(x)\,dx
=
\mathbb{E}(X^r)
\end{aligned}
$$

離散型情形則把積分換成加總即可。

<div id="example-217" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.17 (A Discrete MGF)</div>

令 $Y$ 的 PMF 為

$$
p_Y(y)=2^{-y},
\qquad y=1,2,3,\ldots
$$

因為

$$
\sum_{y=1}^{\infty}2^{-y}=1
$$

這確實定義了一個離散型隨機變數。由 MGF 的定義可得

$$
\begin{aligned}
M_Y(t)
&=
\sum_{y=1}^{\infty}e^{ty}2^{-y} \\[0.35em]
&=
\sum_{y=1}^{\infty}\left(\frac{e^t}{2}\right)^y \\[0.35em]
&=
\frac{e^t}{2-e^t},
\qquad t<\ln 2
\end{aligned}
$$

接著微分

$$
M_Y'(t)=\frac{2e^t}{(2-e^t)^2},
\qquad
M_Y''(t)=\frac{2e^t(2+e^t)}{(2-e^t)^3}
$$

故

$$
\mathbb{E}(Y)=M_Y'(0)=2,
\qquad
\mathbb{E}(Y^2)=M_Y''(0)=6
$$

由此可得

$$
\mathrm{Var}(Y)
=
\mathbb{E}(Y^2)-[\mathbb{E}(Y)]^2
=
6-2^2
=
2
$$

</div>

這個例子呈現 MGF 的基本用法。先把 PMF 加總成 $t$ 的函數，再透過微分取得原動差。若直接計算 $\mathbb{E}(Y)$ 與 $\mathbb{E}(Y^2)$，也會得到相同結果；MGF 的優點在於它把多階原動差放進同一套計算中。

## 泰勒展開

若 $M_X(t)$ 在 $0$ 附近存在，則它在 $t=0$ 的泰勒展開 (Taylor expansion) 可寫為

$$
M_X(t)
=
\sum_{r=0}^{\infty}
M_X^{(r)}(0)\frac{t^r}{r!}
=
\sum_{r=0}^{\infty}
\mathbb{E}(X^r)\frac{t^r}{r!}
$$

這個式子把 MGF 與所有原動差連在一起。第一項是 $\mathbb{E}(X^0)=1$；後面依序放入 $\mathbb{E}(X)$、$\mathbb{E}(X^2)$、$\mathbb{E}(X^3)$ 等。

要注意的是，若 MGF 已知在 $0$ 附近存在，則它會保證各階原動差存在，並且上述泰勒係數正是這些原動差。反過來說，單憑各階動差存在，不足以直接保證 MGF 一定在 $0$ 附近存在。後續使用泰勒展開反推 MGF 時，必須確認該級數確實在 $0$ 附近代表一個有限的 MGF。

<div id="mgf-function-transformations"></div>

## MGF 與函數轉換

若 $Y=g(X)$ 且 $Y$ 的 MGF 存在，則由定義可得

$$
M_Y(t)
=
\mathbb{E}(e^{tY})
=
\mathbb{E}\bigl(e^{t g(X)}\bigr)
$$

對[線性轉換](/teaching-topics/linear-transformations-standardization/) $Y=aX+b$，其中 $a,b\in\mathbb{R}$，上式可進一步寫成

$$
\begin{aligned}
M_Y(t)
&=
\mathbb{E}\bigl[e^{t(aX+b)}\bigr] \\[0.35em]
&=
e^{bt}\mathbb{E}(e^{(at)X}) \\[0.35em]
&=
e^{bt}M_X(at)
\end{aligned}
$$

這個關係式對所有使 $M_X(at)$ 有限的 $t$ 成立。常數 $b$ 產生乘數 $e^{bt}$，係數 $a$ 則把 MGF 的參數由 $t$ 改為 $at$。後續介紹特徵函數時，會比較同一個線性轉換在複指數下所得的公式。

## 由 MGF 辨認分配

MGF 起初用來生成動差，但它還有另一個常用性質。若兩個隨機變數的 MGF 在 $0$ 附近相同，則兩者的機率分配相同。

<div id="theorem-21" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.1 (Uniqueness of MGF)</div>

若 $X$ 與 $Y$ 的 MGF 在同一個含 $0$ 的開區間上存在，且該區間內皆滿足

$$
M_X(t)=M_Y(t)
$$

則 $X$ 與 $Y$ 具有相同機率分配。

</div>

這個唯一性定理常由拉普拉斯轉換 (Laplace transform) 的唯一性證明。此處只需先掌握結論；後續介紹常見分配與極限定理時，MGF 常用來辨認某個隨機變數屬於哪一種分配。

<div id="example-218" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.18 (A Finite MGF)</div>

設 $X$ 的 MGF 為

$$
M_X(t)
=
\frac{e^t}{5}
+\frac{2e^{4t}}{5}
+\frac{2e^{8t}}{5},
\qquad -\infty<t<\infty
$$

對 $t$ 微分可得

$$
M_X'(t)
=
\frac{e^t}{5}
+\frac{8e^{4t}}{5}
+\frac{16e^{8t}}{5}
$$

所以

$$
\mathbb{E}(X)=M_X'(0)=5
$$

再微分一次可得

$$
M_X''(t)
=
\frac{e^t}{5}
+\frac{32e^{4t}}{5}
+\frac{128e^{8t}}{5}
$$

因此

$$
\mathbb{E}(X^2)=M_X''(0)=\frac{161}{5}
$$

由變異數計算公式可得

$$
\mathrm{Var}(X)
=
\frac{161}{5}-5^2
=
\frac{36}{5}
$$

此外，因為離散型 MGF 中的 $p e^{at}$ 對應到 $X=a$ 且機率為 $p$，這個 MGF 也表示 $X$ 在 $1,4,8$ 三點上分別具有機率 $1/5,2/5,2/5$。
</div>

<div id="example-219" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.19 (Moments to a Distribution)</div>

假設 $X$ 的 MGF 在 $0$ 附近存在，且其正整數階原動差滿足

$$
\mathbb{E}(X^r)=0.8,
\qquad r=1,2,3,\ldots
$$

由於 $\mathbb{E}(X^0)=1$，MGF 在 $0$ 附近的泰勒展開為

$$
\begin{aligned}
M_X(t)
&=
\sum_{r=0}^{\infty}\mathbb{E}(X^r)\frac{t^r}{r!} \\[0.35em]
&=
1+0.8\sum_{r=1}^{\infty}\frac{t^r}{r!} \\[0.35em]
&=
1+0.8(e^t-1) \\[0.35em]
&=
0.2+0.8e^t
\end{aligned}
$$

而只在 $0$ 與 $1$ 取值、且

$$
\mathbb{P}(X=0)=0.2,
\qquad
\mathbb{P}(X=1)=0.8
$$

的隨機變數，其 MGF 正是 $0.2+0.8e^t$。由 MGF 的唯一性可知，這些動差所對應的分配就是後面會正式介紹的**伯努利分配 (Bernoulli distribution)**，參數為 $p=0.8$。
</div>

## 本篇小結

動差母函數定義為

$$
M_X(t)=\mathbb{E}(e^{tX})
$$

若它在 $0$ 附近存在，則 $M_X^{(r)}(0)=\mathbb{E}(X^r)$，因此可透過微分取得各階原動差。對離散型與連續型隨機變數而言，MGF 分別由 PMF 加總與 PDF 積分得到。若 $Y=aX+b$，則在兩側皆有限的範圍內有 $M_Y(t)=e^{bt}M_X(at)$。

MGF 不一定存在，即使存在，也可能只在某個 $t$ 的範圍內有限。使用 MGF 時，應同時留意存在區間。若兩個隨機變數的 MGF 在 $0$ 附近相同，則兩者有相同機率分配，這便是 MGF 的唯一性。

後續介紹常見分配時，MGF 會成為整理期望值、變異數與分配辨認的常用工具。[下一篇文章](/teaching-topics/probability-cumulant-generating-functions/)會討論機率母函數 (probability generating function, PGF)、階乘動差與累積量母函數 (cumulant generating function, CGF)。再下一篇則介紹[特徵函數](/teaching-topics/characteristic-functions/)，說明複指數轉換如何在 MGF 不存在時仍然描述一個機率分配。

## 參考文獻與延伸閱讀

- 黃文璋，2003，《機率論》，初版，華泰文化。
- 黃文璋，2003，《數理統計》，初版，華泰文化。
- Patrick Billingsley. 1995. *Probability and Measure*. 3rd ed. Wiley.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Sheldon M. Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
