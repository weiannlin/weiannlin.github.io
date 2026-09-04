---
title: "隨機變數的函數轉換: 一對一的情形"
subtitle: "Transformations of a Random Variable: The One-to-One Case"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 23
order: 223
permalink: /lecture-notes/one-to-one-transformations/
date: 2026-08-06
published: true
excerpt: "已知 $X$ 的機率分配，令 $Y=g(X)$，要如何求出 $Y$ 的機率分配？只要 $g(\\cdot)$ 是定義在實數上的實值可測函數，$Y$ 便仍然是一個隨機變數。離散型有直接列表法、pmf 法與 mgf 法三種做法；連續型無法列表，改以 cdf 法由累積的機率相等下手，或以 Jacobian 法把原變數的 pdf 以新變數表示後再乘上導數的絕對值，而 mgf 法離散與連續通用。本篇例題所出現的轉換，其 $g(\\cdot)$ 都是一對一函數，反函數直接存在；最後把取 $g$ 為 $X$ 自身 cdf 的情形寫成機率積分轉換。"
---

[上一篇](/lecture-notes/empirical-rule-bell-shaped-distributions/)以鐘形分配的經驗法則，直接說出[期望值](/lecture-notes/expectation/#def-expectation)左右一個、兩個與三個[標準差](/lecture-notes/variance-standard-deviation/#def-standard-deviation)之內各涵蓋多少機率。到這裡為止，我們處理的都是同一個[隨機變數](/lecture-notes/random-variables-and-pmf/#def-random-variable)自身的機率與量數。

本篇要看的是另一件事情。已知 $X$ 的機率分配，令 $Y=g(X)$，$Y$ 的機率分配是什麼？我們先說明 $Y$ 在什麼條件之下仍然是一個隨機變數，接著分離散型與連續型兩節，各介紹三種求法，並以四道例題示範。這幾道例題所出現的轉換，其 $g(\cdot)$ 都是一對一函數，反函數直接存在；反函數不存在時的做法留到[下一篇](/lecture-notes/many-to-one-transformations/)。

我們在處理機率問題時，時常會遇到需要將隨機變數取一個函數而進行轉換的情況，若僅是要計算其轉換後的期望值，則 [Theorem 2.9](/lecture-notes/properties-of-expectation/#thm-expectation-of-function) 便已足矣；但若我們進一步地想知道其機率分配，則我們便需要使用這個小節的內容。

整體而言，隨機變數的函數轉換之形式如下:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{array}{ccccc}
\boxed{\text{已知}} & \Longrightarrow & \boxed{\text{函數關係}} & \Longrightarrow & \boxed{\text{所求}}\\[0.55em]
X\sim f_{\sssig X}(x) & & \text{令 }Y=g(X) & & Y\sim f_{\sssig Y}(y)
\end{array}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{array}{c}
\boxed{\text{已知}}\\[0.3em]
X\sim f_{\sssig X}(x)\\[0.55em]
\Downarrow\\[0.55em]
\boxed{\text{函數關係}}\\[0.3em]
\text{令 }Y=g(X)\\[0.55em]
\Downarrow\\[0.55em]
\boxed{\text{所求}}\\[0.3em]
Y\sim f_{\sssig Y}(y)
\end{array}
$$

</div>

不難想像，$Y=g(X)$ 在此也將是一個隨機變數，此即以下定理。

<div id="thm-measurable-transformation" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.38 (可測函數轉換後仍為隨機變數, measurable transformations preserve randomness)</div>

若 $X$ 為一隨機變數，且函數 $g(\cdot)$ 為一定義在實數上的實值可測函數，則 $Y=g(X)$ 亦為隨機變數。

</div>

計算 $Y$ 的機率分配之方法眾多，以下分列之。

## 離散型的函數轉換

在隨機變數為離散的時候，我們有以下的幾種做法:

(1) **直接列表法**
{: .topic-paren-item}

利用 $Y=g(X)$ 列出與每個 $X$ 對應的 $Y$ 值來看出機率，形式如下
{: .topic-paren-cont}

| $X$ | $Y=g(X)$ | 機率 |
|:---:|:---:|:---:|
| $x\_1$ | $y\_1=g(x\_1)$ | $\mathbb{P}(X=x\_1)$ |
| $\vdots$ | $\vdots$ | $\vdots$ |
| $x\_n$ | $y\_n=g(x\_n)$ | $\mathbb{P}(X=x\_n)$ |

再把轉換後位置相同的質點合併，即得
{: .topic-paren-cont}

| $Y$ | 機率 |
|:---:|:---:|
| $y\_1$ | $\mathbb{P}(Y=y\_1)$ |
| $\vdots$ | $\vdots$ |
| $y\_n$ | $\mathbb{P}(Y=y\_n)$ |

**直接列表法適用於質點數量有限，即使窮舉也能輕鬆列出所有的機率時**。
{: .topic-paren-cont}

這個做法的正式定義，可以寫為如下:
{: .topic-paren-cont}

$$
\mathbb{P}(Y=y)=\sum_{t\,:\,g(t)=y}\mathbb{P}(X=t)
$$

<div class="topic-proof" markdown="1">
**Proof.**

由於

$$
\lbrace Y=y\rbrace=\bigcup_{t\,:\,g(t)=y}\lbrace X=t\rbrace
$$

且右側各個事件 $\lbrace X=t\rbrace$ 兩兩互斥，故由機率的可加性可以得到下式

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(Y=y)=\mathbb{P}\Biggl(\bigcup_{t\,:\,g(t)=y}\lbrace X=t\rbrace\Biggr)=\sum_{t\,:\,g(t)=y}\mathbb{P}(X=t)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(Y=y)&=\mathbb{P}\Biggl(\bigcup_{t\,:\,g(t)=y}\lbrace X=t\rbrace\Biggr)\\[0.45em]
&=\sum_{t\,:\,g(t)=y}\mathbb{P}(X=t)
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

其原理是利用離散分配在每個質點上，都有對應的機率，直接列出所有轉換後對應的質點，並且合併轉換後位置相同的質點，得到對應轉換後的質點機率。
{: .topic-paren-cont}

(2) **pmf 法**
{: .topic-paren-item}

<div id="prop-discrete-transformation-pmf" class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Proposition 2.1 (離散型函數轉換的 pmf 公式, pmf of a discrete transformation)</div>

令 $X$ 為離散型隨機變數，其 pmf 為 $p\_{\sssig X}(x)$，且 $g(\cdot)$ 在 $X$ 的值域 $\mathcal{R}\_{\sssig X}$ 上為一對一函數，若令 $Y=g(X)$，則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
p_{\sssig Y}(y)&=\mathbb{P}(Y=y)=\mathbb{P}\bigl(g(X)=y\bigr)\\[0.45em]
&=\mathbb{P}\bigl(X=g^{-1}(y)\bigr)=p_{\sssig X}\bigl(g^{-1}(y)\bigr)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig Y}(y)&=\mathbb{P}(Y=y)\\[.45em]
&=\mathbb{P}\bigl(g(X)=y\bigr)\\[0.45em]
&=\mathbb{P}\bigl(X=g^{-1}(y)\bigr)\\[0.45em]
&=p_{\sssig X}\bigl(g^{-1}(y)\bigr)
\end{aligned}
$$

</div>

</div>

**pmf 法適用於無法窮舉列完所有機率，但彼此間的函數轉換是一一對應，且可輕鬆得到反函數關係的時候**。
{: .topic-paren-cont}

與直接列表法的原理事實上相同，只是在 $g(\cdot)$ 是一對一函數時，利用 $Y=g(X)$ 的函數關係直接反求得到 $X=g^{-1}(Y)$ 的關係，並且**因為 $g(\cdot)$ 本身一一對應，二者為等價事件，機率必定相等**，從而得到 $Y$ 的 pmf。
{: .topic-paren-cont}

也因為此方法乃是操作 $Y=g(X)$ 的方程式關係，因此亦被稱作**方程式解**。
{: .topic-paren-cont}

(3) **mgf 法**
{: .topic-paren-item}

令 $Y=g(X)$，並且求出 $M\_{\sssig Y}(t)=\mathbb{E}\bigl(e^{tY}\bigr)=\mathbb{E}\bigl(e^{t\,g(X)}\bigr)$，再從 [mgf 的唯一性](/lecture-notes/uniqueness-of-the-mgf/#thm-mgf-uniqueness)得知 $Y$ 的機率分配。然而，欲透過此方法得知 $Y$ 的機率分配，我們必須熟知隨機變數之函數轉換的 mgf，見下列定理。
{: .topic-paren-cont}

<div id="thm-mgf-linear-transformation" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.39 (線性轉換的 mgf, mgf of a linear transformation)</div>

令 $X$ 為一隨機變數，其 mgf 為 $M\_{\sssig X}(t)$，且 $a, b$ 為實數，若令 $Y=aX+b$，則

$$
M_{\sssig Y}(t)=e^{bt}\,M_{\sssig X}(at)
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.**

由 [mgf 的定義](/lecture-notes/moment-generating-functions/#def-mgf)可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{\sssig Y}(t)&=\mathbb{E}\bigl(e^{tY}\bigr)=\mathbb{E}\bigl[e^{t\,(aX+b)}\bigr]=\mathbb{E}\bigl[e^{(at)X}\,e^{bt}\bigr]\\[0.45em]
&=e^{bt}\,\mathbb{E}\bigl[e^{(at)X}\bigr]=e^{bt}\,M_{\sssig X}(at)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig Y}(t)&=\mathbb{E}\bigl(e^{tY}\bigr)\\[.45em]
&=\mathbb{E}\bigl[e^{t\,(aX+b)}\bigr]\\[0.45em]
&=\mathbb{E}\bigl[e^{(at)X}\,e^{bt}\bigr]\\[0.45em]
&=e^{bt}\,\mathbb{E}\bigl[e^{(at)X}\bigr]\\[.45em]
&=e^{bt}\,M_{\sssig X}(at)
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div id="ex-linear-transform-pmf" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.48</div>

令 $X$ 為一離散型隨機變數，且 pmf 為

$$
p_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{x}{10}, & x=1, 2, 3, 4\\[0.7em]
0, & \text{o.w.}
\end{array}
\right.
$$

若令 $Y=2X+1$，則求 $Y$ 之機率分配。

**直接列表法**

| $X$ | $Y=2X+1$ | 機率 |
|:---:|:---:|:---:|
| $1$ | $3$ | $\frac{1}{10}$ |
| $2$ | $5$ | $\frac{2}{10}$ |
| $3$ | $7$ | $\frac{3}{10}$ |
| $4$ | $9$ | $\frac{4}{10}$ |

由此可得

$$
p_{\sssig Y}(y)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{\,y-1\,}{20}, & y=3, 5, 7, 9\\[0.7em]
0, & \text{o.w.}
\end{array}
\right.
$$

**pmf 法**

由 [Proposition 2.1](#prop-discrete-transformation-pmf) 可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(Y=y)&=\mathbb{P}\bigl(g(X)=y\bigr)=\mathbb{P}(2X+1=y)=\mathbb{P}\Bigl(X=\frac{\,y-1\,}{2}\Bigr)\\[0.45em]
&=p_{\sssig X}\Bigl(\frac{\,y-1\,}{2}\Bigr)=\frac{\frac{\,y-1\,}{2}}{10}=\frac{\,y-1\,}{20},\quad y=3, 5, 7, 9
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(Y=y)&=\mathbb{P}\bigl(g(X)=y\bigr)\\[0.45em]
&=\mathbb{P}(2X+1=y)\\[0.45em]
&=\mathbb{P}\Bigl(X=\frac{\,y-1\,}{2}\Bigr)\\[0.45em]
&=p_{\sssig X}\Bigl(\frac{\,y-1\,}{2}\Bigr)\\[.45em]
&=\frac{\frac{\,y-1\,}{2}}{10}\\[0.45em]
&=\frac{\,y-1\,}{20},\quad y=3, 5, 7, 9
\end{aligned}
$$

</div>

由此可得

$$
p_{\sssig Y}(y)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{\,y-1\,}{20}, & y=3, 5, 7, 9\\[0.7em]
0, & \text{o.w.}
\end{array}
\right.
$$

**mgf 法**

由 [mgf 的定義](/lecture-notes/moment-generating-functions/#def-mgf)可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{\sssig Y}(t)&=\mathbb{E}\bigl(e^{tY}\bigr)=\mathbb{E}\bigl[e^{t(2X+1)}\bigr]=\mathbb{E}\bigl[e^{(2t)X}e^{t}\bigr]\\[0.45em]
&=e^{t}\,\mathbb{E}\bigl[e^{(2t)X}\bigr]=e^{t}\,M_{\sssig X}(2t)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig Y}(t)&=\mathbb{E}\bigl(e^{tY}\bigr)=\mathbb{E}\bigl[e^{t(2X+1)}\bigr]\\[0.45em]
&=\mathbb{E}\bigl[e^{(2t)X}e^{t}\bigr]=e^{t}\,\mathbb{E}\bigl[e^{(2t)X}\bigr]\\[0.45em]
&=e^{t}\,M_{\sssig X}(2t)
\end{aligned}
$$

</div>

又 $X$ 的 mgf 為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{\sssig X}(t)&=\mathbb{E}\bigl(e^{tX}\bigr)=\sum_{x=1}^{4}e^{tx}\cdot\frac{x}{\,10\,}\\[0.45em]
&=\frac{1}{10}e^{t}+\frac{2}{10}e^{2t}+\frac{3}{10}e^{3t}+\frac{4}{10}e^{4t},\quad t\in\mathbb{R}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig X}(t)&=\mathbb{E}\bigl(e^{tX}\bigr)=\sum_{x=1}^{4}e^{tx}\cdot\frac{x}{\,10\,}\\[0.45em]
&=\frac{1}{10}e^{t}+\frac{2}{10}e^{2t}\\[0.45em]
&\qquad+\frac{3}{10}e^{3t}+\frac{4}{10}e^{4t},\quad t\in\mathbb{R}
\end{aligned}
$$

</div>

故

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{\sssig Y}(t)&=e^{t}\,M_{\sssig X}(2t)\\[0.45em]
&=e^{t}\Bigl[\frac{1}{10}e^{(2t)}+\frac{2}{10}e^{2\cdot(2t)}+\frac{3}{10}e^{3\cdot(2t)}+\frac{4}{10}e^{4\cdot(2t)}\Bigr]\\[0.45em]
&=\frac{1}{10}e^{3t}+\frac{2}{10}e^{5t}+\frac{3}{10}e^{7t}+\frac{4}{10}e^{9t},\quad t\in\mathbb{R}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig Y}(t)&=e^{t}\,M_{\sssig X}(2t)\\[0.45em]
&=e^{t}\Bigl[\frac{1}{10}e^{(2t)}+\frac{2}{10}e^{2\cdot(2t)}\\[0.2em]
&\qquad\quad +\frac{3}{10}e^{3\cdot(2t)}+\frac{4}{10}e^{4\cdot(2t)}\Bigr]\\[0.45em]
&=\frac{1}{10}e^{3t}+\frac{2}{10}e^{5t}\\[0.45em]
&\qquad+\frac{3}{10}e^{7t}+\frac{4}{10}e^{9t},\quad t\in\mathbb{R}
\end{aligned}
$$

</div>

則由 [mgf 的唯一性](/lecture-notes/uniqueness-of-the-mgf/#thm-mgf-uniqueness)可知 $Y$ 的 pmf 為

$$
p_{\sssig Y}(y)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{\,y-1\,}{20}, & y=3, 5, 7, 9\\[0.7em]
0, & \text{o.w.}
\end{array}
\right.
$$

</div>

<div id="ex-chip-parity-mgf" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.49</div>

<div lang="en" markdown="1">
An urn contains five chips numbered $1$ through $5$. Suppose that two of the chips are selected at random and without replacement, and let $X=5$ when the sum of the two numbers drawn is even and $X=-3$ when that sum is odd. Determine the moment generating function of $X$.
</div>

我們將所有的可能號碼組合與機率，及其所對應的 $X$ 值列在下方:

| 號碼 | 機率 | $X$ |
|:---:|:---:|:---:|
| $(1, 2)$ | $1/10$ | $-3$ |
| $(1, 3)$ | $1/10$ | $5$ |
| $(1, 4)$ | $1/10$ | $-3$ |
| $(1, 5)$ | $1/10$ | $5$ |
| $(2, 3)$ | $1/10$ | $-3$ |
| $(2, 4)$ | $1/10$ | $5$ |
| $(2, 5)$ | $1/10$ | $-3$ |
| $(3, 4)$ | $1/10$ | $-3$ |
| $(3, 5)$ | $1/10$ | $5$ |
| $(4, 5)$ | $1/10$ | $-3$ |

則可以整理出 $X$ 的機率分配為

$$
p_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{3}{5}, & x=-3\\[0.7em]
\dfrac{2}{5}, & x=5\\[0.7em]
0, & \text{o.w.}
\end{array}
\right.
$$

由此可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
M_{\sssig X}(t)=\mathbb{E}\bigl(e^{tX}\bigr)=\frac{3}{\,5\,}\,e^{-3t}+\frac{2}{\,5\,}\,e^{5t},\quad t\in\mathbb{R}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig X}(t)&=\mathbb{E}\bigl(e^{tX}\bigr)\\[0.45em]
&=\frac{3}{\,5\,}\,e^{-3t}+\frac{2}{\,5\,}\,e^{5t},\quad t\in\mathbb{R}
\end{aligned}
$$

</div>

</div>

## 連續型的函數轉換

與離散變數相似，連續變數的情況我們有以下幾種做法:

(1) **cdf 法**
{: .topic-paren-item}

由於連續變數無法像離散變數一樣列表，故我們只能從函數關係的方程式下手，但又因為方程式解法乃是**基於等式兩側機率相等**所得到的結果，故我們在此是採用 cdf 累積的機率相等，而不是與離散分配使用 pmf。其形式如下:
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\boxed{\ \text{以 }Y=g(X)\text{ 求出 }Y\text{ 的 cdf}\ }\quad\Longrightarrow\quad\boxed{\ \frac{d\,F_{\sssig Y}(y)}{d\,y}=f_{\sssig Y}(y)\ }
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{array}{c}
\boxed{\ \text{以 }Y=g(X)\text{ 求出 }Y\text{ 的 cdf}\ }\\[0.55em]
\Downarrow\\[0.55em]
\boxed{\ \dfrac{d\,F_{\sssig Y}(y)}{d\,y}=f_{\sssig Y}(y)\ }
\end{array}
$$

</div>

上述的形式若寫為數學步驟則如下列步驟所示:
{: .topic-paren-cont}

<div id="prop-cdf-method" class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Proposition 2.2 (cdf 法, the cdf method)</div>

令 $X$ 為連續型隨機變數，其 cdf 為 <span class="text-nowrap">$F\_{\sssig X}(x)$，</span>且 $g(\cdot)$ 在 $X$ 的值域 $\mathcal{R}\_{\sssig X}$ 上為嚴格單調函數，若令 $Y=g(X)$，則第一個步驟為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
F_{\sssig Y}(y)&=\mathbb{P}(Y\leqslant y)=\mathbb{P}\bigl(g(X)\leqslant y\bigr)\\[0.45em]
&=\left\lbrace
\begin{array}{c@{\quad}l}
\mathbb{P}\bigl(X\leqslant g^{-1}(y)\bigr)=F_{\sssig X}\bigl(g^{-1}(y)\bigr), & \text{當 }g(\cdot)\text{ 為保序函數}\\[0.5em]
\mathbb{P}\bigl(X\geqslant g^{-1}(y)\bigr)=1-F_{\sssig X}\bigl(g^{-1}(y)\bigr), & \text{當 }g(\cdot)\text{ 為反序函數}
\end{array}
\right.
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&F_{\sssig Y}(y)=\mathbb{P}(Y\leqslant y)=\mathbb{P}\bigl(g(X)\leqslant y\bigr)\\[0.45em]
&=\left\lbrace
\begin{array}{@{}l@{}}
\mathbb{P}\bigl(X\leqslant g^{-1}(y)\bigr)=F_{\sssig X}\bigl(g^{-1}(y)\bigr),\\[0.25em]
\qquad\qquad\qquad\ \ \text{當 }g(\cdot)\text{ 為保序函數}\\[0.6em]
\mathbb{P}\bigl(X\geqslant g^{-1}(y)\bigr)=1-F_{\sssig X}\bigl(g^{-1}(y)\bigr),\\[0.25em]
\qquad\qquad\qquad\ \ \text{當 }g(\cdot)\text{ 為反序函數}
\end{array}
\right.
\end{aligned}
$$

</div>

第二個步驟為

$$
\frac{d\,F_{\sssig Y}(y)}{d\,y}=f_{\sssig Y}(y)
$$

</div>

第一個步驟最後的條件分為**保序函數 <span lang="en">(order-preserving function)</span>** 和**反序函數 <span lang="en">(order-reversing function)</span>** 二種，對應到在 $g(X)\leqslant y$ 兩側同時取反函數 $g^{-1}(\cdot)$ 的步驟時，此二種函數的特性將使得反函數存在，並且取反函數後的結果便分別為 $X\leqslant g^{-1}(y)$ 及 $X\geqslant g^{-1}(y)$ 二種。保序函數可以簡單理解為遞增函數，而反序函數則可理解為遞減函數。
{: .topic-paren-cont}

(2) **Jacobian 法**
{: .topic-paren-item}

**Jacobian 法**被譯為**亞可比法**，這個方法就是微積分中變數代換的章節中所使用的 Jacobian 法，二者並無二致，是將隨機變數的 pdf 視為一個單純的函數時應具有的自然性質。方法如下:
{: .topic-paren-cont}

<div id="prop-jacobian-method" class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Proposition 2.3 (一對一變換的 Jacobian 公式, the Jacobian method)</div>

令 $X$ 為連續型隨機變數，其 pdf 為 <span class="text-nowrap">$f\_{\sssig X}(x)$，</span>且 $g(\cdot)$ 在 $X$ 的值域 $\mathcal{R}\_{\sssig X}$ 上為一對一函數，即反函數 $g^{-1}(\cdot)$ 存在，並要求 $g^{-1}(\cdot)$ 連續可微且導數處處不為零，若令 $Y=g(X)$，則第一個步驟為由 $Y=g(X)$ 反求得 $X=g^{-1}(Y)$，第二個步驟為

$$
f_{\sssig Y}(y)=f_{\sssig X}\bigl(g^{-1}(y)\bigr)\,\bigl\lvert\mathbf{J}\bigr\rvert
$$

其中

$$
\mathbf{J}=\frac{d\,g^{-1}(y)}{d\,y}
$$

</div>

上述的 $\lvert\cdot\rvert$ 為絕對值，我們可以將這個方法的流程理解為**將原變數的 pdf 以新變數表示，再乘上原變數對新變數微分的絕對值**。
{: .topic-paren-cont}

然而很多時候 $g(\cdot)$ 的反函數不存在，這時也不用太擔心，我們只需將原先的隨機變數分段，直到該段中 $g(\cdot)$ 的反函數存在，分段轉換為新變數的 pdf 後，再以分段隨機變數的概念將各段連接起來即可。
{: .topic-paren-cont}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個概念被稱為**分治法 <span lang="en">(divide-and-conquer)</span>**，在電腦科學中是非常常使用的手段，特別是當子問題明顯地比原問題容易解決時，我們常常傾向分別解決多個子問題，而非一個困難的原問題；在這裡的情況則是分段求取新的 pdf 後，再行合併得到所求。

</div>

(3) **mgf 法**
{: .topic-paren-item}

此處的 mgf 法與離散變數的 mgf 法並無不同。事實上，我們在離散變數時也沒有限定該 mgf 所對應的隨機變數必須是離散或是連續，就連 [Theorem 2.39](#thm-mgf-linear-transformation) 也沒有限制離散或連續，故這是一個離散與連續通用的方法。
{: .topic-paren-cont}

<div id="ex-reciprocal-transformation" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.50</div>

<div lang="en" markdown="1">
Let

$$
f_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
2x, & \text{if }0<x<1\\[0.4em]
0, & \text{elsewhere}
\end{array}
\right.
$$

be the pdf of $X$.

<ol class="topic-list-paren">
  <li>Compute $\mathbb{E}\left(\frac{1}{X}\right)$.</li>
  <li>Find the cdf and the pdf of $Y=\frac{1}{X}$.</li>
  <li>Compute $\mathbb{E}(Y)$ and compare this result with the answer obtained in (1).</li>
</ol>
</div>

(1) 由[函數期望值](/lecture-notes/properties-of-expectation/#thm-expectation-of-function)可知
{: .topic-paren-item}

$$
\mathbb{E}\Bigl(\frac{1}{X}\Bigr)=\int_{0}^{1}\frac{1}{x}\,2x\,dx=\bigl[2x\bigr]_{0}^{1}=2
$$

(2) 由 $Y=\frac{1}{X}$ 可反求得 $X=\frac{1}{Y}$，故
{: .topic-paren-item}

$$
\mathbf{J}=\frac{d\,x}{d\,y}=\frac{-1}{\,y^{2}\,}
$$

由 [Proposition 2.3](#prop-jacobian-method) 可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig Y}(y)=f_{\sssig X}\Bigl(\frac{1}{y}\Bigr)\bigl\lvert\mathbf{J}\bigr\rvert=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{2}{y}\times\dfrac{1}{y^{2}}, & y>1\\[0.7em]
0, & \text{o.w.}
\end{array}
\right.
=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{2}{y^{3}}, & y>1\\[0.7em]
0, & \text{o.w.}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig Y}(y)&=f_{\sssig X}\Bigl(\frac{1}{y}\Bigr)\bigl\lvert\mathbf{J}\bigr\rvert\\[0.45em]
&=\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{2}{y}\times\dfrac{1}{y^{2}}, & y>1\\[0.7em]
0, & \text{o.w.}
\end{array}
\right.\\[0.45em]
&=\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{2}{y^{3}}, & y>1\\[0.7em]
0, & \text{o.w.}
\end{array}
\right.
\end{aligned}
$$

</div>

並可由 [cdf 之定義](/lecture-notes/cumulative-distribution-functions/#def-cdf)可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig Y}(y)=\mathbb{P}(Y\leqslant y)=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & y<1\\[0.5em]
\displaystyle\int_{1}^{y}2t^{-3}\,dt, & y\geqslant1
\end{array}
\right.
=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & y<1\\[0.7em]
1-\dfrac{1}{y^{2}}, & y\geqslant1
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig Y}(y)&=\mathbb{P}(Y\leqslant y)\\[0.45em]
&=\left\lbrace
\begin{array}{c@{\quad}l}
0, & y<1\\[0.5em]
\displaystyle\int_{1}^{y}2t^{-3}\,dt, & y\geqslant1
\end{array}
\right.\\[0.45em]
&=\left\lbrace
\begin{array}{c@{\quad}l}
0, & y<1\\[0.7em]
1-\dfrac{1}{y^{2}}, & y\geqslant1
\end{array}
\right.
\end{aligned}
$$

</div>

(3) 所求為
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(Y)=\int_{1}^{\infty}y\,\frac{2}{y^{3}}\,dy=\bigl[-2y^{-1}\bigr]_{1}^{\infty}=2=\mathbb{E}\Bigl(\frac{1}{X}\Bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(Y)&=\int_{1}^{\infty}y\,\frac{2}{y^{3}}\,dy\\[0.45em]
&=\bigl[-2y^{-1}\bigr]_{1}^{\infty}=2=\mathbb{E}\Bigl(\frac{1}{X}\Bigr)
\end{aligned}
$$

</div>

</div>

下面這一題承接 [Example 2.31](/lecture-notes/moment-generating-functions/#ex-logistic-cdf) 的邏輯斯分配。

<div id="ex-logistic-to-uniform" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.31 <span lang="en">(Continued)</span></div>

<div lang="en" markdown="1">
Suppose that $X$ has the logistic pdf

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X}(x)=\frac{e^{-x}}{\,(1+e^{-x})^{2}\,},\quad -\infty<x<\infty
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig X}(x)&=\frac{e^{-x}}{\,(1+e^{-x})^{2}\,}, ~-\infty<x<\infty
\end{aligned}
$$

</div>

<ol class="topic-list-paren topic-list-paren--start-4">
  <li>Determine the distribution of $$Y=(1+e^{-X})^{-1}.$$</li>
</ol>
</div>

(4) **cdf 法**
{: .topic-paren-item}

由 [cdf 之定義](/lecture-notes/cumulative-distribution-functions/#def-cdf)與 [Example 2.31](/lecture-notes/moment-generating-functions/#ex-logistic-cdf) 第 (1) 小題已求得的 $F\_{\sssig X}(x)=\frac{1}{\,1+e^{-x}\,}$ 可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
F_{\sssig Y}(y)&=\mathbb{P}(Y\leqslant y)=\mathbb{P}\Bigl(\frac{1}{\,1+e^{-X}\,}\leqslant y\Bigr)\\[0.45em]
&=\mathbb{P}\bigl(X\leqslant\ln y-\ln(1-y)\bigr)=F_{\sssig X}\bigl(\ln y-\ln(1-y)\bigr)\\[0.45em]
&=\frac{1}{\,1+e^{-(\ln y-\ln(1-y))}\,}=y,\quad 0<y<1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig Y}(y)&=\mathbb{P}(Y\leqslant y)\\[0.45em]
&=\mathbb{P}\Bigl(\frac{1}{\,1+e^{-X}\,}\leqslant y\Bigr)\\[0.45em]
&=\mathbb{P}\bigl(X\leqslant\ln y-\ln(1-y)\bigr)\\[0.45em]
&=F_{\sssig X}\bigl(\ln y-\ln(1-y)\bigr)\\[0.45em]
&=\frac{1}{\,1+e^{-(\ln y-\ln(1-y))}\,}\\[0.45em]
&=y,\quad 0<y<1
\end{aligned}
$$

</div>

又在 $y\leqslant0$ 時 $F\_{\sssig Y}(y)=0$、在 $y\geqslant1$ 時 $F\_{\sssig Y}(y)=1$，故
{: .topic-paren-cont}

$$
Y\sim\mathcal{U}(0, 1)
$$

**Jacobian 法**
{: .topic-paren-cont}

由 $Y=\frac{1}{\,1+e^{-X}\,}$ 可反求得 $X=\ln Y-\ln(1-Y)$，故
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbf{J}=\frac{\,d\,x\,}{\,d\,y\,}=\frac{1}{\,y\,}+\frac{1}{\,1-y\,}=\frac{1}{\,y(1-y)\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbf{J}&=\frac{\,d\,x\,}{\,d\,y\,}\\[.45em]
&=\frac{1}{\,y\,}+\frac{1}{\,1-y\,}\\[0.45em]
&=\frac{1}{\,y(1-y)\,}
\end{aligned}
$$

</div>

則由 [Proposition 2.3](#prop-jacobian-method) 可知 $Y$ 之 pdf 為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f_{\sssig Y}(y)&=f_{\sssig X}\bigl(\ln y-\ln(1-y)\bigr)\,\bigl\lvert\mathbf{J}\bigr\rvert\\[0.45em]
&=\frac{e^{-(\ln y-\ln(1-y))}}{\,\bigl(1+e^{-(\ln y-\ln(1-y))}\bigr)^{2}\,}\cdot\frac{1}{\,y(1-y)\,}=1,\quad 0<y<1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&f_{\sssig Y}(y)=f_{\sssig X}\bigl(\ln y-\ln(1-y)\bigr)\,\bigl\lvert\mathbf{J}\bigr\rvert\\[0.45em]
&=\frac{e^{-(\ln y-\ln(1-y))}}{\,\bigl(1+e^{-(\ln y-\ln(1-y))}\bigr)^{2}\,}\cdot\frac{1}{\,y(1-y)\,}\\[0.45em]
&=1,\quad 0<y<1
\end{aligned}
$$

</div>

故
{: .topic-paren-cont}

$$
Y\sim\mathcal{U}(0, 1)
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這題使用的函數 $g(\cdot)$ 比較特殊，是 $X$ 本身的 cdf (捨棄了 cdf 的意義而直接當成一個函數)，這時候得到的結果必定會是 $\mathcal{U}(0, 1)$ 分配。這個性質我們將在均勻分配的小節中提到，是一個特殊的機率性質。

</div>

這個性質對任何連續型隨機變數都成立，反過來走也可以由 $\mathcal{U}(0, 1)$ 回到原來的分配，正式的敘述如下。

<span id="proposition-218"></span>
<div id="prop-probability-integral-transform" class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Proposition 2.4 (機率積分轉換, probability integral transform)</div>

若 $X$ 為連續型隨機變數，其 cdf 為 <span class="text-nowrap">$F\_{\sssig X}(\cdot)$，</span>並依[分位函數](/lecture-notes/quantiles/#quantile-function)的取法令

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F^{-1}_{\sssig X}(u)=\inf\lbrace x\in\mathbb{R}\mid F_{\sssig X}(x)\geqslant u\rbrace,\quad 0<u<1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F^{-1}_{\sssig X}(u)=\inf\lbrace x\in\mathbb{R}\mid F_{\sssig X}(x)&\geqslant u\rbrace,\\[0.45em]
&0<u<1
\end{aligned}
$$

</div>

則

(1) $U=F\_{\sssig X}(X)$ 服從 $\mathcal{U}(0, 1)$。
{: .topic-paren-item}

(2) 若 $U$ 服從 $\mathcal{U}(0, 1)$，則 $F^{-1}\_{\sssig X}(U)$ 的 cdf 為 $F\_{\sssig X}$。
{: .topic-paren-item}

其中 $u=0$ 與 $u=1$ 兩個端點的機率為 <span class="text-nowrap">$0$，</span>因此 $F^{-1}\_{\sssig X}$ 在這兩點上如何取值，都不會改變 $F^{-1}\_{\sssig X}(U)$ 的分配。

</div>

<div class="topic-proof" markdown="1">
**Proof.**

(1) 取定 $0<u<1$ 並令 $x\_{\sssig u}=F^{-1}\_{\sssig X}(u)$。由 $F\_{\sssig X}$ 連續可知 $F\_{\sssig X}(x\_{\sssig u})=u$。$X\leqslant x\_{\sssig u}$ 時由 $F\_{\sssig X}$ 遞增可得 $F\_{\sssig X}(X)\leqslant u$；反之 $X>x\_{\sssig u}$ 而 $F\_{\sssig X}(X)\leqslant u$ 時，由 $F\_{\sssig X}$ 遞增可得 $F\_{\sssig X}(X)\geqslant F\_{\sssig X}(x\_{\sssig u})=u$，故必有 $F\_{\sssig X}(X)=u$，即 $X$ 落在 $(x\_{\sssig u}, b]$ 之內，其中 $b=\sup\lbrace x\in\mathbb{R}\mid F\_{\sssig X}(x)=u\rbrace$，而 $F\_{\sssig X}$ 在該區間上恆為 $u$，此時
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(x_{\sssig u}<X\leqslant b)=F_{\sssig X}(b)-F_{\sssig X}(x_{\sssig u})=u-u=0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(x_{\sssig u}<X\leqslant b)&=F_{\sssig X}(b)-F_{\sssig X}(x_{\sssig u})\\[.45em]
&=u-u=0
\end{aligned}
$$

</div>

因此 $\lbrace U\leqslant u\rbrace$ 與 $\lbrace X\leqslant x\_{\sssig u}\rbrace$ 至多相差一個機率為 $0$ 的事件，由此可得
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(U\leqslant u)=\mathbb{P}(X\leqslant x_{\sssig u})=F_{\sssig X}(x_{\sssig u})=u,\quad 0<u<1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(U\leqslant u)&=\mathbb{P}(X\leqslant x_{\sssig u})\\[0.45em]
&=F_{\sssig X}(x_{\sssig u})=u,\quad 0<u<1
\end{aligned}
$$

</div>

此即 $\mathcal{U}(0, 1)$ 的 cdf。
{: .topic-paren-cont}

(2) 先證對任一 $x\in\mathbb{R}$ 與 $0<u<1$，$F^{-1}\_{\sssig X}(u)\leqslant x$ 若且唯若 $u\leqslant F\_{\sssig X}(x)$。若 $u\leqslant F\_{\sssig X}(x)$，則 $x$ 屬於 $\lbrace t\in\mathbb{R}\mid F\_{\sssig X}(t)\geqslant u\rbrace$，由下確界的定義可得 $F^{-1}\_{\sssig X}(u)\leqslant x$；反之若 $F^{-1}\_{\sssig X}(u)\leqslant x$，由 $F\_{\sssig X}$ 右連續可知該下確界本身也滿足 $F\_{\sssig X}\bigl(F^{-1}\_{\sssig X}(u)\bigr)\geqslant u$，再由 $F\_{\sssig X}$ 遞增可得 $F\_{\sssig X}(x)\geqslant u$。故
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}\bigl(F^{-1}_{\sssig X}(U)\leqslant x\bigr)=\mathbb{P}\bigl(U\leqslant F_{\sssig X}(x)\bigr)=F_{\sssig X}(x)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}\bigl(F^{-1}_{\sssig X}(U)\leqslant x\bigr)&=\mathbb{P}\bigl(U\leqslant F_{\sssig X}(x)\bigr)\\[0.45em]
&=F_{\sssig X}(x)
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
{: .topic-paren-cont}
</div>

若想實際操作這兩個方向，可以在互動展示 [Probability Integral Transform and Inverse Transform Sampling](/demos/probability-integral-transform/) 中調整 $u$，觀察標準柯西分配 <span lang="en">(standard Cauchy distribution)</span> 的 $F^{-1}\_{\sssig X}$ 與 $F\_{\sssig X}$ 接連作用之後如何回到 $u$，並比較 $\mathcal{U}(0, 1)$ 樣本轉換前後的直方圖。

## 本篇小結

本篇處理的是已知 $X$ 的機率分配之後，如何求出 $Y=g(X)$ 的機率分配。[Theorem 2.38](#thm-measurable-transformation) 先確定了 $Y$ 的身分，只要 $g(\cdot)$ 是定義在實數上的實值可測函數，$Y$ 就仍然是一個隨機變數。

離散型有三種做法。直接列表法把每個質點轉換後的位置列出來，再把落在同一位置者合併，適用於質點數量有限的時候；[Proposition 2.1](#prop-discrete-transformation-pmf) 的 pmf 法則在 $g(\cdot)$ 一對一時，直接以 $p\_{\sssig Y}(y)=p\_{\sssig X}(g^{-1}(y))$ 求得，因為 $\lbrace Y=y\rbrace$ 與 $\lbrace X=g^{-1}(y)\rbrace$ 是等價事件；mgf 法先求出 $M\_{\sssig Y}(t)$ 再由唯一性認出分配，[Theorem 2.39](#thm-mgf-linear-transformation) 的 $M\_{\sssig Y}(t)=e^{bt}M\_{\sssig X}(at)$ 正是線性轉換時所需的工具。[Example 2.48](#ex-linear-transform-pmf) 以同一題並陳三種做法，[Example 2.49](#ex-chip-parity-mgf) 則由列表求出 pmf 之後直接寫出 mgf。

連續型無法列表。[Proposition 2.2](#prop-cdf-method) 的 cdf 法改由累積的機率相等下手，先依 $g(\cdot)$ 是保序或反序寫出 $F\_{\sssig Y}(y)$，再微分得到 $f\_{\sssig Y}(y)$；[Proposition 2.3](#prop-jacobian-method) 的 Jacobian 法則把原變數的 pdf 以新變數表示，再乘上 $\lvert\mathbf{J}\rvert$。mgf 法在兩型之間並無不同。[Example 2.50](#ex-reciprocal-transformation) 與 [Example 2.31 <span lang="en">(Continued)</span>](#ex-logistic-to-uniform) 各示範一次，後者取 $g$ 為 $X$ 自身的 cdf，結果是 $\mathcal{U}(0, 1)$，這個現象由 [Proposition 2.4](#prop-probability-integral-transform) 的機率積分轉換正式敘述，它同時給出反方向的走法。由 $\mathcal{U}(0, 1)$ 出發，經分位函數即可回到原來的分配。

本篇所處理的 $Y=2X+1$、$Y=\frac{1}{X}$ 與 $Y=\bigl(1+e^{-X}\bigr)^{-1}$，其中的 $g(\cdot)$ 都是一對一函數，反函數直接存在，套上公式即可。[下一篇](/lecture-notes/many-to-one-transformations/)處理反函數不存在的情形，作法正是前面提過的分段。先把值域分成若干段，使 $g(\cdot)$ 在各段上一對一，分別求出各段的密度之後再合併起來。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- Walter Rudin. 1976. *Principles of Mathematical Analysis*. 3rd ed. McGraw-Hill.
- Luc Devroye. 1986. *Non-Uniform Random Variate Generation*. Springer.
