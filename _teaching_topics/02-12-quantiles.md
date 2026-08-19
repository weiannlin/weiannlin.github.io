---
title: "分位數"
subtitle: "Quantiles"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 12
order: 212
permalink: /teaching-topics/quantiles/
date: 2026-08-06
published: true
excerpt: "分位數把中位數的想法推廣到任意比例: 給定一個介於 $0$ 與 $1$ 之間的 $p$，同時滿足 $\\mathbb{P}(X\\leqslant x_{p})\\geqslant p$ 與 $\\mathbb{P}(X\\geqslant x_{p})\\geqslant1-p$ 的 $x_{p}$ 稱為 $p$-分位數，直觀上它把整個分配切成前後兩段，前段佔全部的 $p$、後段佔全部的 $1-p$。換一個角度來看，$q-1$ 個分位數可以把一個分配均分為 $q$ 個等份，第 $k$ 個分界點記為 $q_{k}$；取 $q=4$、$q=10$ 與 $q=100$，便分別得到四分位數、十分位數與百分位數。"
---

[上一篇](/teaching-topics/median/)介紹[中位數](/teaching-topics/median/#def-median)，它把一個分配切成機率各佔一半的前後兩段。這一刀切在正中央，但正中央並不是唯一值得關心的位置。我們也常想知道有四分之一的機率落在哪一個點以下，或是把一個分配均分成十份、一百份之後，各個分界點分別落在哪裡。

本篇介紹的分位數，就是把中位數的想法推廣到任意的比例。以下先給出分位數的兩種定義，說明如何由 cdf 找到其中一個分位數，再以兩張圖分別呈現兩種定義的直觀意涵，接著看四分位數、十分位數與百分位數這三種常見的設定，最後以五道例題示範離散型、連續型與混合型的求算。

<div id="def-quantile" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.11 (分位數, quantile)</div>

令 $X$ 為一[隨機變數](/teaching-topics/random-variables-and-pmf/#def-random-variable)且 $0<p<1$，若 $x\_{\sssig p}\in\mathbb{R}$ 滿足

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X\leqslant x_{\sssig p})\geqslant p\quad\text{且}\quad\mathbb{P}(X\geqslant x_{\sssig p})\geqslant1-p
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(X\leqslant x_{\sssig p})\geqslant p\ \text{且}\\[0.45em]
&\mathbb{P}(X\geqslant x_{\sssig p})\geqslant1-p
\end{aligned}
$$

</div>

則稱 $x\_{\sssig p}$ 為 $X$ 的 **$p$-分位數 ($p$-quantile)**。

又若在上述條件中，$k, q\in\mathbb{N}$ 且 $1\leqslant k\leqslant q-1$、$q\_{\sssig k}\in\mathbb{R}$ 滿足

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X\leqslant q_{\sssig k})\geqslant\frac{k}{\,q\,}\quad\text{且}\quad\mathbb{P}(X\geqslant q_{\sssig k})\geqslant1-\frac{k}{\,q\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(X\leqslant q_{\sssig k})\geqslant\frac{k}{\,q\,}\ \text{且}\\[0.45em]
&\mathbb{P}(X\geqslant q_{\sssig k})\geqslant1-\frac{k}{\,q\,}
\end{aligned}
$$

</div>

則稱 $q\_{\sssig k}$ 為 $X$ 的**第 $k$ 個 $q$-分位數 ($k$-th $q$-quantile)**。

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

[Definition 2.11](#def-quantile) 的第二種定義以 $\frac{k}{q}$ 取代第一種定義中的 $p$，而第一種定義要求 $0<p<1$，故 $k$ 的範圍寫成 $1\leqslant k\leqslant q-1$，兩端都要排除: $k=0$ 給出 $\frac{k}{q}=0$，$k=q$ 給出 $\frac{k}{q}=1$，都落在 $0<p<1$ 之外。這也與下面 $q=4$ 時取 $k=1, 2, 3$、$q=10$ 時取 $k=1, \ldots, 9$ 的用法一致。

</div>

分位數 <span lang="en">(quantile)</span> 有一些地方需要注意:

(1) 上述定義中的分位數較常被稱為**母體分位數 <span lang="en">(population quantile)</span>**，用以避免與敘述統計學中的**樣本分位數 <span lang="en">(sample quantile)</span>** 混淆。
{: .topic-paren-item}

(2) $p$-分位數 (第 $k$ 個 $q$-分位數) 也同樣未必唯一，但我們可以分別透過下面兩個式子，找到其中一個 $p$-分位數與第 $k$ 個 $q$-分位數
{: #quantile-function .topic-paren-item}

$$
\begin{gathered}
x_{\sssig p}=\inf\lbrace x\in\mathbb{R}\mid F_{\sssig X}(x)\geqslant p\rbrace\\[0.7em]
q_{\sssig k}=\inf\left\lbrace x\in\mathbb{R}\;\middle|\;F_{\sssig X}(x)\geqslant\frac{k}{\,q\,}\right\rbrace
\end{gathered}
$$

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

與中位數相同，若 $F\_{\sssig X}$ 連續且於值域上嚴格遞增，則前述的找法所找到的分位數，會是

$$
\begin{gathered}
x_{\sssig p}=F^{-1}_{\sssig X}(p)\\[0.7em]
q_{\sssig k}=F^{-1}_{\sssig X}\!\left(\frac{k}{\,q\,}\right)
\end{gathered}
$$

這個值也是該分配唯一的 $p$-分位數 (第 $k$ 個 $q$-分位數)。

</div>

(3) 與中位數相似，直觀上來說，$p$-分位數 (第 $k$ 個 $q$-分位數) 的意義在於**該點將整個分配切成前後兩段，前面一段佔全部的 $p$ (或 $\frac{k}{q}$)、後面一段佔全部的 $1-p$ (或 $1-\frac{k}{q}$)**。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

在第二種定義中，這組共 $q-1$ 個的分位數，**將整個分配均分為 $q$ 個等份，$q\_{\sssig k}$ 是其中的第 $k$ 份與第 $k+1$ 份的分界點**。

</div>

下面就用圖示來理解 $p$-分位數的直觀意涵。

<figure id="fig-quantile-intuition" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/quantile-intuition.svg" alt="一條右偏的機率密度曲線，橫軸為 x。曲線下方有一條虛線界線自曲線垂直落到橫軸，軸下標為 x_p。界線左側到曲線起點之間的面積畫上淡色陰影並標為 p，界線右側到曲線右端之間的面積標為 1 減 p。">
  <figcaption><span class="topic-figure__label">Fig. 2.15.</span> $p$-分位數 $x_{\sssig p}$ 把分配切成前後兩段: 界線左側的面積為 $p$、右側的面積為 $1-p$。</figcaption>
</figure>

或是以第二種定義來理解第 $k$ 個 $q$-分位數的直觀意涵。

<figure id="fig-kth-q-quantile" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/quartiles-equal-areas.svg" alt="一條右偏的機率密度曲線，橫軸為 x。曲線下方有三條虛線界線自曲線垂直落到橫軸，軸下由左至右標為 q1、q2、q3。三條界線把曲線下的面積分成四塊，四塊深淺交替上色，每一塊各標四分之一。四塊的寬度並不相等，最左一塊最窄，最右一塊一路延伸到曲線的右端。">
  <figcaption><span class="topic-figure__label">Fig. 2.16.</span> 取 $q=4$ 時，三個分位數 $q_{1}$、$q_{2}$、$q_{3}$ 把整個分配均分為四個等份，每一份的機率各為 $\frac{1}{4}$。</figcaption>
</figure>

[Definition 2.11](#def-quantile) 中，若我們設定第二種定義的 $q$ 是以下幾個特殊的自然數，則其定義就成為我們常見的幾種分位數，以下就以不同的 $q$ 討論。

(1) **四分位數 <span lang="en">(quartile)</span>**: 若 $q=4$，則 $q\_{\sssig k}, k=1, 2, 3$ 為我們常見的四分位數，更常被記為 $Q\_{\sssig k}, k=1, 2, 3$，其中
{: .topic-paren-item}

$$
Q_2=\eta_{\sssig X}
$$

(2) **十分位數 (decile)**: 若 $q=10$，則 $q\_{\sssig k}, k=1, \ldots, 9$ 為我們常見的十分位數，更常被記為 $D\_{\sssig k}, k=1, \ldots, 9$，其中
{: .topic-paren-item}

$$
D_5=Q_2=\eta_{\sssig X}
$$

(3) **百分位數 <span lang="en">(percentile)</span>**: 若 $q=100$，則 $q\_{\sssig k}, k=1, \ldots, 99$ 為我們常見的百分位數，更常被記為 $P\_{\sssig r}, r=1, \ldots, 99$，其中
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
P_{50}=D_5=Q_2=\eta_{\sssig X}\qquad P_{25}=Q_1\qquad P_{75}=Q_3
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
P_{50}&=D_5=Q_2=\eta_{\sssig X}\\[0.45em]
P_{25}&=Q_1\\[0.45em]
P_{75}&=Q_3
\end{aligned}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

百分位數正是早前臺灣國中的基本學力測驗所採用的「PR 值」。

</div>

<div id="ex-discrete-percentile" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.23</div>

假設 $X$ 有機率分配

$$
p_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{x}{10}, & x=1, 2, 3, 4\\[0.7em]
0, & \text{otherwise}
\end{array}
\right.
$$

試求其第 $15$ 百分位數為何？

由 [Definition 2.11](#def-quantile) 可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X\leqslant2)=\frac{1}{10}+\frac{2}{10}=\frac{3}{10}\geqslant\frac{15}{100}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X\leqslant2)&=\frac{1}{10}+\frac{2}{10}\\[0.45em]
&=\frac{3}{10}\geqslant\frac{15}{100}
\end{aligned}
$$

</div>

且

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X\geqslant2)=\frac{2}{10}+\frac{3}{10}+\frac{4}{10}=\frac{9}{10}\geqslant\frac{85}{100}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X\geqslant2)&=\frac{2}{10}+\frac{3}{10}+\frac{4}{10}\\[0.45em]
&=\frac{9}{10}\geqslant\frac{85}{100}
\end{aligned}
$$

</div>

故所求為

$$
P_{15}=2
$$

</div>

<div id="ex-uniform-upper-quartile" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.24</div>

假設 $X$ 有機率分配

$$
f_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{1}{4}, & 0<x<4\\[0.7em]
0, & \text{otherwise}
\end{array}
\right.
$$

試求其上四分位數為何？

先求出 $X$ 的 cdf 為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig X}(x)=\int_{-\infty}^{x}f_{\sssig X}(t)\,dt=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & x\leqslant0\\[0.5em]
\dfrac{x}{4}, & 0<x<4\\[0.7em]
1, & x\geqslant4
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig X}(x)&=\int_{-\infty}^{x}f_{\sssig X}(t)\,dt\\[0.5em]
&=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & x\leqslant0\\[0.5em]
\dfrac{x}{4}, & 0<x<4\\[0.7em]
1, & x\geqslant4
\end{array}
\right.
\end{aligned}
$$

</div>

再由 [Definition 2.11](#def-quantile) 可知

$$
F_{\sssig X}(Q_3)=\frac{Q_3}{4}=\frac{3}{4}
$$

故所求為

$$
Q_3=3
$$

</div>

<div id="ex-exponential-decile" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.25</div>

<div lang="en" markdown="1">
Let $X$ be a continuous random variable with pdf

$$
f_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
e^{-x}, & x>0\\[0.4em]
0, & \text{elsewhere}
\end{array}
\right.
$$

Find the 9-th decile of $X$.
</div>

先求出 $X$ 的 cdf 為

$$
F_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & x<0\\[0.4em]
1-e^{-x}, & x\geqslant0
\end{array}
\right.
$$

再由 [Definition 2.11](#def-quantile) 可知

$$
F_{\sssig X}(D_9)=1-e^{-D_9}=0.9
$$

故所求為

$$
D_9=-\ln0.1=\ln10
$$

</div>

[Definition 2.10](/teaching-topics/median/#def-median) 提過中位數未必唯一，下面就是一個中位數不唯一的例子。

<div id="ex-nonunique-median" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.26</div>

假設 $X$ 有機率分配

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{1}{4}, & 0<x<2\ \text{或}\ 4<x<6\\[0.7em]
0, & \text{otherwise}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases">
  <div class="topic-cases__lhs">$f_{\sssig X}(x)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$\dfrac{1}{4},$</div>
    <div class="topic-cases__cond">$0<x<2$ 或 $4<x<6$</div>
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$\text{otherwise}$</div>
  </div>
</div>

</div>

試求其母體中位數為何？

若 $a\in[2, 4]$，則可以發現

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X\leqslant a)=F_{\sssig X}(a)=F_{\sssig X}(2)=\int_{0}^{2}\frac{1}{\,4\,}\,dx=\frac{1}{\,2\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X\leqslant a)&=F_{\sssig X}(a)=F_{\sssig X}(2)\\[0.45em]
&=\int_{0}^{2}\frac{1}{\,4\,}\,dx=\frac{1}{\,2\,}
\end{aligned}
$$

</div>

且

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X\geqslant a)&=\mathbb{P}(X>a)=1-F_{\sssig X}(a)\\[0.45em]
&=1-F_{\sssig X}(2)=\int_{4}^{6}\frac{1}{\,4\,}\,dx=\frac{1}{\,2\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X\geqslant a)&=\mathbb{P}(X>a)\\[0.45em]
&=1-F_{\sssig X}(a)=1-F_{\sssig X}(2)\\[0.45em]
&=\int_{4}^{6}\frac{1}{\,4\,}\,dx=\frac{1}{\,2\,}
\end{aligned}
$$

</div>

故 $[2, 4]$ 之間的任意實數皆為 $X$ 之母體中位數。

</div>

<div id="ex-component-lifetime-first-quartile" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.14 <span lang="en">(Continued)</span></div>

<div lang="en" markdown="1">
Let $Y$ denote the length of life <span lang="en">(in hundreds of hours)</span> of electronic components. These components frequently fail immediately upon insertion into a system. It has been observed that the probability of immediate failure is $\frac{1}{4}$. If a component does not fail immediately, the distribution for its length of life has the exponential density function

$$
g(y)=
\left\lbrace
\begin{array}{c@{\quad}l}
e^{-y}, & y>0\\[0.4em]
0, & \text{elsewhere}
\end{array}
\right.
$$

<ol class="topic-list-paren topic-list-paren--start-4">
  <li>Find the first quartile of $Y$.</li>
</ol>
</div>

(4) 由[第 (1) 小題](/teaching-topics/mixed-random-variables/#ex-component-lifetime)已求得 $Y$ 的 cdf 為
{: .topic-paren-item}

$$
F_{\sssig Y}(y)=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & y<0\\[0.5em]
1-\dfrac{3}{4}e^{-y}, & y\geqslant0
\end{array}
\right.
$$

再由 [Definition 2.11](#def-quantile) 可知
{: .topic-paren-cont}

$$
F_{\sssig Y}(Q_1)=1-\frac{3}{4}e^{-Q_1}=\frac{1}{4}
$$

故所求為
{: .topic-paren-cont}

$$
Q_1=0
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

上面以解方程式 $F_{\sssig Y}(Q_1)=\frac{1}{4}$ 求第一四分位數，這個作法對混合型並不通用。$Y$ 在 $y=0$ 有一個機率為 $\frac{1}{4}$ 的質點，$F_{\sssig Y}$ 在該處由 $0$ 跳到 $\frac{1}{4}$；cdf 一有跳躍，$F_{\sssig Y}(y)=p$ 這個方程式就未必有解，即使有解也未必唯一。一般的作法是回到 [Definition 2.11](#def-quantile) 的兩個不等式，或改用[前面 (2) 所給的找法](#quantile-function)，此即

$$
Q_1=\inf\left\lbrace y\in\mathbb{R}\;\middle|\;F_{\sssig Y}(y)\geqslant\frac{1}{4}\right\rbrace
$$

本題的跳躍恰好停在 $\frac{1}{4}$ 這個高度上，方程式的唯一解與上式的下確界因而同為 $Q_1=0$，兩種作法給出相同的答案。

</div>

<span id="example-214"></span>

## 本篇小結

[Definition 2.11](#def-quantile) 給了分位數的兩種定義。第一種以比例 $p$ 為準，若 $x_{\sssig p}$ 同時滿足 $\mathbb{P}(X\leqslant x_{\sssig p})\geqslant p$ 與 $\mathbb{P}(X\geqslant x_{\sssig p})\geqslant1-p$，則稱它為 $p$-分位數；第二種以等分數 $q$ 為準，把 $p$ 換成 $\frac{k}{q}$，所得的 $q_{\sssig k}$ 稱為第 $k$ 個 $q$-分位數。分位數與中位數一樣未必唯一，取 $\inf\lbrace x\in\mathbb{R}\mid F_{\sssig X}(x)\geqslant p\rbrace$ 可以找到其中一個；若 $F\_{\sssig X}$ 連續且於值域上嚴格遞增，這個值就是 $F^{-1}\_{\sssig X}(p)$，而且是唯一的一個。

兩種定義各有一個直觀意涵。[Fig. 2.15](#fig-quantile-intuition) 對應第一種。分位數把分配切成前後兩段，前段佔全部的 $p$、後段佔全部的 $1-p$。[Fig. 2.16](#fig-kth-q-quantile) 對應第二種。$q-1$ 個分位數把分配均分為 $q$ 個等份，$q_{\sssig k}$ 是第 $k$ 份與第 $k+1$ 份的分界點。設定 <span class="text-nowrap">$q=4$、</span><span class="text-nowrap">$q=10$ 與</span><span class="text-nowrap">$q=100$，</span>便分別得到四分位數 $Q_{\sssig k}$、十分位數 $D_{\sssig k}$ 與百分位數 $P_{\sssig r}$，三者在 $P_{50}=D_5=Q_2=\eta_{\sssig X}$ 這一點上會合。

五道例題涵蓋三種型態: [Example 2.23](#ex-discrete-percentile) 是離散型，直接由定義的兩個不等式驗證；[Example 2.24](#ex-uniform-upper-quartile) 與 [Example 2.25](#ex-exponential-decile) 是連續型，先求 cdf 再解方程式；[Example 2.26](#ex-nonunique-median) 的密度在 $[2, 4]$ 上為零，該區間內的每一個實數都是中位數，是中位數不唯一的實例；[Example 2.14 <span lang="en">(Continued)</span>](#ex-component-lifetime-first-quartile) 則是混合型，第一四分位數落在質點 $0$ 上。至此，[期望值](/teaching-topics/expectation/#def-expectation)、[變異數](/teaching-topics/variance/#def-variance)、[標準差](/teaching-topics/variance-standard-deviation/#def-standard-deviation)、[眾數](/teaching-topics/mode/#def-mode)、中位數與分位數這幾個量數都已介紹完畢，[下一節](/teaching-topics/moment-system/)要把其中的期望值與變異數收進同一套架構之下，也就是動差系統。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Morris H. DeGroot and Mark J. Schervish. 2012. *Probability and Statistics*. 4th ed. Pearson.
- Alexander M. Mood, Franklin A. Graybill, and Duane C. Boes. 1974. *Introduction to the Theory of Statistics*. 3rd ed. McGraw-Hill.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
