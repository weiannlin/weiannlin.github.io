---
title: "弱大數法則與中央極限定理"
subtitle: "The Weak Law of Large Numbers and the Central Limit Theorem"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 5
topic: 5
order: 505
permalink: /lecture-notes/weak-law-and-central-limit-theorem/
date: 2026-08-15
published: true
excerpt: "在期望值 $\\mu$ 與正且有限的變異數 $\\sigma^{2}$ 存在下，弱大數法則保證獨立同分配樣本平均數 $\\overline{X}$ 機率收斂至 $\\mu$ 這一常數，中央極限定理則指出標準化後的 $\\sqrt{n}(\\overline{X}-\\mu)/\\sigma$ 分配收斂至標準常態分配。本篇給出證明、失效反例與四種等價寫法。"
---

[上一篇](/lecture-notes/convergence-in-mean-and-almost-sure/)把 $r$ 次均方收斂與幾乎確信收斂放在一起，說明這兩種收斂型態彼此並不蘊含，至此四種收斂型態之間的強弱關係已經完整。本篇轉入這些收斂型態最重要的兩個應用，分別是弱大數法則與中央極限定理。

兩條定理的前提相同，都要求 iid 序列的期望值 $\mu$ 與變異數 $\sigma^{2}$ 存在，結論也都是關於樣本平均數 $\overline{X}$ 的極限行為，但收斂的型態並不相同。弱大數法則說 $\overline{X}$ 本身[機率收斂](/lecture-notes/convergence-in-probability/#def-converge-in-probability)到 $\mu$ 這個常數，中央極限定理說 $\overline{X}$ 經標準化之後[分配收斂](/lecture-notes/convergence-in-distribution/#def-converge-in-distribution)到一個服從標準常態分配的隨機變數。本篇先給出弱大數法則與其證明，再由兩道例題看它的延伸用法；其後給出中央極限定理，並以動差母函數的泰勒展開式示範大學部教本常見的證明，以及標準柯西分配這個前提不成立的反例。

## 弱大數法則

<div id="thm-weak-law-of-large-numbers" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 5.7 (弱大數法則, Weak Law of Large Numbers, WLLN)</div>

令 $\lbrace X_n\rbrace_{n=1}^{\infty}$ 為一定義在機率空間上之 iid 隨機變數序列，且期望值 $\mu$ 與[變異數](/lecture-notes/variance/#def-variance) $\sigma^{2}$ 皆存在，則當 $n$ 趨近於無窮大，對於樣本平均數 $\overline{X}=\frac{1}{\,n\,}\sum_{i=1}^{n}X_i$ 而言，我們有

$$
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert\overline{X}-\mu\rvert<\varepsilon\bigr)=1,\ \forall\,\varepsilon>0
$$

此即

$$
\overline{X}\pconv\mu
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.**

由於 $X_1,X_2,\ldots,X_n\iidto(\mu,\sigma^{2})$ 為獨立同分配的隨機變數，我們有

$$
\mathbb{E}\bigl(\overline{X}\bigr)=\mu,\ \ \mathrm{Var}\bigl(\overline{X}\bigr)=\frac{\sigma^{2}}{\,n\,}
$$

故由[柴比雪夫不等式](/lecture-notes/probability-inequalities/#thm-chebyshev)可知

<div class="topic-math-follow-before" markdown="1">

$$
\mathbb{P}\bigl(\lvert\overline{X}-\mu\rvert<\varepsilon\bigr)\geqslant1-\frac{\bigl(\frac{\sigma^{2}}{n}\bigr)}{\varepsilon^{2}}=1-\frac{\sigma^{2}}{\,n\varepsilon^{2}\,},\ \forall\,\varepsilon>0
$$

</div>
<div class="topic-math-follow" markdown="1">
<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\Longrightarrow\ \lim_{n\to\infty}\mathbb{P}\bigl(\lvert\overline{X}-\mu\rvert<\varepsilon\bigr)\geqslant\lim_{n\to\infty}\biggl(1-\frac{\sigma^{2}}{n\varepsilon^{2}}\biggr)=1,\ \forall\,\varepsilon>0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ \lim_{n\to\infty}\mathbb{P}\bigl(\lvert\overline{X}-\mu\rvert<\varepsilon\bigr)&\geqslant\lim_{n\to\infty}\biggl(1-\frac{\sigma^{2}}{n\varepsilon^{2}}\biggr)\\[0.45em]
&=1,\ \forall\,\varepsilon>0
\end{aligned}
$$

</div>
</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

弱大數法則 <span lang="en">(Weak Law of Large Numbers, WLLN)</span> 有一些地方需要注意:

(1) 由樣本平均數 $\overline{X}$ 的期望值恆為 <span class="text-nowrap">$\mu$、</span>變異數為 $\frac{\sigma^{2}}{\,n\,}$ 可見，隨著樣本大小 $n$ 增大，$\mathrm{Var}\bigl(\overline{X}\bigr)$ 逐漸縮小並在 $n\to\infty$ 時趨近於 <span class="text-nowrap">$0$，</span>使 $\overline{X}$ 的抽樣分配退化集中於常數 <span class="text-nowrap">$\mu$。</span>
{: .topic-paren-item}

(2) 上述證明倚賴柴比雪夫不等式，故須同時假設 $\mu$ 與有限變異數 $\sigma^{2}$ 存在；實質上，即使母體變異數 $\sigma^{2}$ 不存在，只要一階動差 $\mu$ 有限，在高等機率論中仍可改以**[特徵函數](/lecture-notes/characteristic-functions/#def-characteristic-function) <span lang="en">(characteristic function, cf)</span>** 證明此定理成立 (相關理論與極限定理可參閱 Athreya and Lahiri, 2006, *Measure Theory and Probability Theory*, 1st ed.)。不過在絕大多數應用情境中，皆可直接假設序列為 iid 且期望值與變異數均存在。
{: .topic-paren-item}

<div id="ex-wlln-second-moment" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.15</div>

<div lang="en" markdown="1">
Let $X_1,\ldots,X_n$ be iid random variables with common pdf

$$
f(x)=\frac{\,x^{\mu-1}e^{-x}\,}{\Gamma(\mu)},\ x>0,\ \mu>0
$$

Find the constant $c$ such that $\frac{1}{\,n\,}(X_1^{2}+X_2^{2}+\cdots+X_n^{2})\pconv c$.
</div>

經題意敘述可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
X_1,\ldots,X_n\iidto\mathrm{Gamma}(\alpha=\mu,\ \beta=1)\qquad\therefore\, \mathbb{E}(X_i)=\mu,\ \mathrm{Var}(X_i)=\mu
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
X_1,\ldots,X_n&\iidto\mathrm{Gamma}(\alpha=\mu,\ \beta=1)\\[0.45em]
&\qquad\therefore\, \mathbb{E}(X_i)=\mu,\ \mathrm{Var}(X_i)=\mu
\end{aligned}
$$

</div>

由弱大數法則可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\frac{1}{\,n\,}(X_1^{2}+X_2^{2}+\cdots+X_n^{2})\pconv\mathbb{E}(X_i^{2})=\mathrm{Var}(X_i)+\bigl[\mathbb{E}(X_i)\bigr]^{2}=\mu+\mu^{2}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\frac{1}{\,n\,}(X_1^{2}+X_2^{2}+\cdots+X_n^{2})&\pconv\mathbb{E}(X_i^{2})\\[0.45em]
&=\mathrm{Var}(X_i)+\bigl[\mathbb{E}(X_i)\bigr]^{2}\\[0.45em]
&=\mu+\mu^{2}
\end{aligned}
$$

</div>

故可知

$$
c=\mu+\mu^{2}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

本題將弱大數法則套用於轉換後的隨機變數序列。令 <span class="text-nowrap">$Y_i=X_i^{2}$，</span>則 $Y_1,\ldots,Y_n$ 仍為獨立同分配序列，且所求平均數即為

$$
\frac{1}{\,n\,}(X_1^{2}+X_2^{2}+\cdots+X_n^{2})=\overline{Y}
$$

故可直接套用 WLLN 得

$$
\overline{Y}\pconv\mathbb{E}(Y_i)=\mathbb{E}(X_i^{2})
$$

</div>

同一技巧亦可推廣至兩組獨立樣本的配對函數平均，見下列例題。

<div id="ex-wlln-paired-difference" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.16</div>

<div lang="en" markdown="1">
Let $X_1,\ldots,X_n,Y_1,\ldots,Y_n$ be $2n$ independent and identically distributed random variables with mean $\mathbb{E}(X_i)=\mathbb{E}(Y_i)=\mu$ and variance <span class="text-nowrap">$\mathrm{Var}(X_i)=\mathrm{Var}(Y_i)=\sigma^{2}$.</span> Define

$$
T=\frac{k}{\,n\,}\sum_{i=1}^{n}(X_i-Y_i)^{2}
$$

Find the constant $k$ such that $T$ is a consistent estimator of $\sigma^{2}$ (i.e., <span class="text-nowrap">$T\pconv\sigma^{2}$),</span> and explain your answer.
</div>

由弱大數法則可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
T=\frac{k}{\,n\,}\sum_{i=1}^{n}(X_i-Y_i)^{2}=\frac{1}{\,n\,}\sum_{i=1}^{n}k(X_i-Y_i)^{2}\pconv\mathbb{E}\bigl[k(X_i-Y_i)^{2}\bigr]
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
T&=\frac{k}{\,n\,}\sum_{i=1}^{n}(X_i-Y_i)^{2}\\[0.45em]
&=\frac{1}{\,n\,}\sum_{i=1}^{n}k(X_i-Y_i)^{2}\\[0.45em]
&\pconv\mathbb{E}\bigl[k(X_i-Y_i)^{2}\bigr]
\end{aligned}
$$

</div>

其中

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\bigl[k(X_i-Y_i)^{2}\bigr]=k\Bigl[\mathrm{Var}(X_i-Y_i)+\bigl[\mathbb{E}(X_i-Y_i)\bigr]^{2}\Bigr]=k\bigl[2\sigma^{2}+0\bigr]=2k\sigma^{2}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[k(X_i-Y_i)^{2}\bigr]&=k\Bigl[\mathrm{Var}(X_i-Y_i)\\[0.2em]
&\qquad+\bigl[\mathbb{E}(X_i-Y_i)\bigr]^{2}\Bigr]\\[0.45em]
&=k\bigl[2\sigma^{2}+0\bigr]=2k\sigma^{2}
\end{aligned}
$$

</div>

故可知

$$
k=\frac{1}{\,2\,}
$$

</div>

## 中央極限定理

以下介紹統計學中最重要的極限定理，即中央極限定理。

<div id="thm-central-limit-theorem" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 5.8 (中央極限定理, Central Limit Theorem, CLT)</div>

令 $\lbrace X_n\rbrace_{n=1}^{\infty}$ 為一定義在機率空間上之 iid 隨機變數序列，且期望值 $\mu$ 與變異數 $\sigma^{2}$ 皆存在，則當 $n$ 趨近於無窮大，我們有

$$
\frac{\,\overline{X}-\mu\,}{\frac{\sigma}{\sqrt{n}}}=\frac{\,\sqrt{n}(\overline{X}-\mu)\,}{\sigma}\dconv Z\sim\mathcal{N}(0,1)
$$

或

$$
\frac{\,\sum_{i=1}^{n}X_i-n\mu\,}{\sqrt{n}\sigma}\dconv Z\sim\mathcal{N}(0,1)
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.**

本證明另外假設 $X_i$ 的 mgf

$$
M(t)=\mathbb{E}\bigl(e^{tX}\bigr)
$$

在 $-h<t<h$ 上存在。令

$$
m(t)=\mathbb{E}\bigl[e^{t(X-\mu)}\bigr]=e^{-\mu t}M(t)
$$

則 $m(t)$ 在同一個區間上也存在，而且它正是 $X-\mu$ 的 mgf，故由 [Theorem 2.21](/lecture-notes/moment-generating-functions/#thm-mgf-generates-moments) 可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
m(0)=1,\quad m^{\prime}(0)=\mathbb{E}(X-\mu)=0,\quad m^{\prime\prime}(0)=\mathbb{E}\bigl[(X-\mu)^{2}\bigr]=\sigma^{2}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
m(0)=1,\\[0.45em]
m^{\prime}(0)=\mathbb{E}(X-\mu)=0,\\[0.45em]
m^{\prime\prime}(0)=\mathbb{E}\bigl[(X-\mu)^{2}\bigr]=\sigma^{2}
\end{gathered}
$$

</div>

對 $m(t)$ 在 $t=0$ 處作帶餘項的泰勒展開，可知存在一個介於 $0$ 與 $t$ 之間的 <span class="text-nowrap">$\xi$，</span>使得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
m(t)=m(0)+m^{\prime}(0)\,t+\frac{\,m^{\prime\prime}(\xi)\,}{2}\,t^{2}=1+\frac{\,m^{\prime\prime}(\xi)\,}{2}\,t^{2}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
m(t)&=m(0)+m^{\prime}(0)\,t+\frac{\,m^{\prime\prime}(\xi)\,}{2}\,t^{2}\\[0.45em]
&=1+\frac{\,m^{\prime\prime}(\xi)\,}{2}\,t^{2}
\end{aligned}
$$

</div>

再把 $\frac{\,\sigma^{2}t^{2}\,}{2}$ 加一次又減一次，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
m(t)=1+\frac{\,\sigma^{2}t^{2}\,}{2}+\frac{\,\bigl[m^{\prime\prime}(\xi)-\sigma^{2}\bigr]t^{2}\,}{2}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
m(t)&=1+\frac{\,\sigma^{2}t^{2}\,}{2}\\[0.45em]
&\qquad+\frac{\,\bigl[m^{\prime\prime}(\xi)-\sigma^{2}\bigr]t^{2}\,}{2}
\end{aligned}
$$

</div>

接著計算

$$
W_n=\frac{\,\sum_{i=1}^{n}X_i-n\mu\,}{\sqrt{n}\,\sigma}
$$

的 mgf。把 $W_n$ 看成 $X_1,X_2,\ldots,X_n$ 的線性組合，由 [Theorem 3.23](/lecture-notes/mgf-method-transformations/#thm-mgf-two-to-one) 與 iid 的前提可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
M_{\sssig W_n}(t)=e^{-\frac{\sqrt{n}\,\mu t}{\sigma}}\prod_{i=1}^{n}M\Bigl(\frac{t}{\sqrt{n}\,\sigma}\Bigr)=\Bigl[m\Bigl(\frac{t}{\sqrt{n}\,\sigma}\Bigr)\Bigr]^{n}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig W_n}(t)&=e^{-\frac{\sqrt{n}\,\mu t}{\sigma}}\prod_{i=1}^{n}M\Bigl(\frac{t}{\sqrt{n}\,\sigma}\Bigr)\\[0.45em]
&=\Bigl[m\Bigl(\frac{t}{\sqrt{n}\,\sigma}\Bigr)\Bigr]^{n}
\end{aligned}
$$

</div>

其中 $-h<\frac{t}{\sqrt{n}\,\sigma}<h$ 成立。把上面 $m(t)$ 的展開式中的 $t$ 換成 $\frac{t}{\sqrt{n}\,\sigma}$ 這個比值，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
m\Bigl(\frac{t}{\sqrt{n}\,\sigma}\Bigr)=1+\frac{t^{2}}{\,2n\,}+\frac{\,\bigl[m^{\prime\prime}(\xi)-\sigma^{2}\bigr]t^{2}\,}{2n\sigma^{2}}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
m\Bigl(\frac{t}{\sqrt{n}\,\sigma}\Bigr)&=1+\frac{t^{2}}{\,2n\,}\\[0.45em]
&\qquad+\frac{\,\bigl[m^{\prime\prime}(\xi)-\sigma^{2}\bigr]t^{2}\,}{2n\sigma^{2}}
\end{aligned}
$$

</div>

此處的 $\xi$ 隨 $n$ 而變，且介於 $0$ 與 $\frac{t}{\sqrt{n}\,\sigma}$ 之間。令

$$
\psi(n)=\frac{\,\bigl[m^{\prime\prime}(\xi)-\sigma^{2}\bigr]t^{2}\,}{2\sigma^{2}}
$$

則 $M_{\sssig W_n}(t)$ 可寫為

$$
M_{\sssig W_n}(t)=\Bigl[1+\frac{\,t^{2}/2\,}{n}+\frac{\,\psi(n)\,}{n}\Bigr]^{n}
$$

由於 $m^{\prime\prime}(t)$ 在 $t=0$ 處連續，而 $n\to\infty$ 時 $\frac{t}{\sqrt{n}\,\sigma}\to0$ 成立，被夾在中間的 $\xi$ 也隨之趨於 <span class="text-nowrap">$0$，</span>由此可得

$$
\lim_{n\to\infty}\psi(n)=0
$$

再由微積分中的極限式

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lim_{n\to\infty}\Bigl(1+\frac{b}{\,n\,}+\frac{\,\psi(n)\,}{n}\Bigr)^{n}=e^{b},\quad\text{其中}\ b\ \text{為常數且}\ \lim_{n\to\infty}\psi(n)=0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\lim_{n\to\infty}\Bigl(1+\frac{b}{\,n\,}+\frac{\,\psi(n)\,}{n}\Bigr)^{n}=e^{b},\\[0.45em]
\text{其中}\ b\ \text{為常數且}\ \lim_{n\to\infty}\psi(n)=0
\end{gathered}
$$

</div>

取 $b=\frac{\,t^{2}\,}{2}$ 可得

$$
\lim_{n\to\infty}M_{\sssig W_n}(t)=e^{\frac{\,t^{2}\,}{2}},\ t\in\mathbb{R}
$$

而 $e^{\frac{\,t^{2}\,}{2}}$ 正是標準常態分配的 mgf，故由 [Theorem 5.1](/lecture-notes/levy-continuity-theorem/#thm-levys-continuity-thm) 可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
W_n=\frac{\,\sum_{i=1}^{n}X_i-n\mu\,}{\sqrt{n}\,\sigma}=\frac{\,\sqrt{n}(\overline{X}-\mu)\,}{\sigma}\dconv Z\sim\mathcal{N}(0,1)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
W_n&=\frac{\,\sum_{i=1}^{n}X_i-n\mu\,}{\sqrt{n}\,\sigma}=\frac{\,\sqrt{n}(\overline{X}-\mu)\,}{\sigma}\\[0.45em]
&\dconv Z\sim\mathcal{N}(0,1)
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

本證明的作法取自 Hogg, McKean and Craig (2019) 第 342 至 343 頁，其中的泰勒展開寫成帶餘項的形式，因此只需要二階動差存在，不必假設 mgf 可以展開成無窮級數；後文以 mgf 搭配列維連續性定理的證明，則另外假設了 mgf 存在，前提比本定理強。

一如弱大數法則的情形，中央極限定理在高等機率論中通常改以特徵函數證明，以免除 mgf 存在的前提；而在大學部的數理統計與機率論教材中，普遍假設序列 $\lbrace X_n\rbrace_{n=1}^{\infty}$ 的 mgf $M_{\sssig X_n}(t)$ 存在，再結合泰勒級數展開與列維連續性定理推導，見下列例題。

<div id="ex-clt-proof-by-mgf" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.17</div>

<div lang="en" markdown="1">
Let $X_1,X_2,\ldots,X_n$ be a random sample from a population with mean $\mu=\mathbb{E}(X)$ and finite variance <span class="text-nowrap">$\sigma^{2}=\mathrm{Var}(X)<\infty$,</span> and define

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
Z_i=\frac{\,X_i-\mu\,}{\sigma},\quad\overline{X}=\frac{1}{\,n\,}\sum_{i=1}^{n}X_i,\quad W_n=\frac{\,\overline{X}-\mu\,}{\frac{\sigma}{\sqrt{n}}}=\frac{\,\sqrt{n}\,(\overline{X}-\mu)\,}{\sigma}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
Z_i=\frac{\,X_i-\mu\,}{\sigma},\quad\overline{X}=\frac{1}{\,n\,}\sum_{i=1}^{n}X_i,\\[0.45em]
W_n=\frac{\,\overline{X}-\mu\,}{\frac{\sigma}{\sqrt{n}}}=\frac{\,\sqrt{n}\,(\overline{X}-\mu)\,}{\sigma}
\end{gathered}
$$

</div>

<ol class="topic-list-paren">
  <li>Write down the Taylor expansion of the moment generating function $M_{\sssig Z}\bigl(\frac{t}{\sqrt{n}}\bigr)$ at <span class="text-nowrap">$t=0$.</span></li>
  <li>Show that the moment generating function of $W_n$ satisfies $M_{\sssig W_n}(t)=\bigl[M_{\sssig Z}\bigl(\frac{t}{\sqrt{n}}\bigr)\bigr]^{n}$.</li>
  <li>Using (1) and <span class="text-nowrap">(2),</span> find <span class="text-nowrap">$\lim_{n\to\infty}M_{\sssig W_n}(t)$.</span></li>
  <li>State and discuss the conclusion that follows from <span class="text-nowrap">(3).</span></li>
</ol>
</div>

(1) 對 $M_{\sssig Z}(t)$ 在 $t=0$ 處作泰勒展開 (也就是 Maclaurin 展開) 可得
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{\sssig Z}(t)&=\frac{M_{\sssig Z}(0)}{0!}t^{0}+\frac{M_{\sssig Z}^{\prime}(0)}{1!}t^{1}+\frac{M_{\sssig Z}^{\prime\prime}(0)}{2!}t^{2}+\frac{M_{\sssig Z}^{\prime\prime\prime}(0)}{3!}t^{3}+\cdots,\ t\in\mathbb{R}\\[0.45em]
&=1+\frac{\,\mathbb{E}(Z)\,}{1!}t^{1}+\frac{\,\mathbb{E}(Z^{2})\,}{2!}t^{2}+\frac{\,\mathbb{E}(Z^{3})\,}{3!}t^{3}+\cdots,\ t\in\mathbb{R}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig Z}(t)&=\frac{M_{\sssig Z}(0)}{0!}t^{0}+\frac{M_{\sssig Z}^{\prime}(0)}{1!}t^{1}\\[0.2em]
&\qquad+\frac{M_{\sssig Z}^{\prime\prime}(0)}{2!}t^{2}\\[0.2em]
&\qquad+\frac{M_{\sssig Z}^{\prime\prime\prime}(0)}{3!}t^{3}+\cdots,\ t\in\mathbb{R}\\[0.45em]
&=1+\frac{\,\mathbb{E}(Z)\,}{1!}t^{1}+\frac{\,\mathbb{E}(Z^{2})\,}{2!}t^{2}\\[0.2em]
&\qquad+\frac{\,\mathbb{E}(Z^{3})\,}{3!}t^{3}+\cdots,\ t\in\mathbb{R}
\end{aligned}
$$

</div>

又由於 $Z_i$ 是由 $X_i$ 標準化而得，故
{: .topic-paren-cont}

$$
\mathbb{E}(Z_i)=0\ \text{且}\ \mathrm{Var}(Z_i)=1
$$

由此可得
{: .topic-paren-cont}

<div class="topic-math-follow-before" markdown="1">

$$
\mathbb{E}(Z_i^{2})=1+0^{2}=1
$$

</div>
<div class="topic-math-follow" markdown="1">
<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ M_{\sssig Z}\biggl(\frac{t}{\sqrt{n}}\biggr)&=1+\frac{\left(\frac{t}{\sqrt{n}}\right)^{2}}{2}+\frac{\left(\frac{t}{\sqrt{n}}\right)^{3}}{6}\,\mathbb{E}(Z^{3})+\cdots\\[0.45em]
&=1+\frac{t^{2}}{\,2n\,}+\frac{t^{3}}{\,6\sqrt{n^{3}}\,}\,\mathbb{E}(Z^{3})+\cdots\\[0.45em]
&=1+\frac{t^{2}}{\,2n\,}+o\!\left(\frac{\,t^{2}\,}{n}\right),\ t\in\mathbb{R}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ M_{\sssig Z}\biggl(\frac{t}{\sqrt{n}}\biggr)&=1+\frac{\left(\frac{t}{\sqrt{n}}\right)^{2}}{2}\\[0.2em]
&\qquad+\frac{\left(\frac{t}{\sqrt{n}}\right)^{3}}{6}\,\mathbb{E}(Z^{3})+\cdots\\[0.45em]
&=1+\frac{t^{2}}{\,2n\,}\\[0.2em]
&\qquad+\frac{t^{3}}{\,6\sqrt{n^{3}}\,}\,\mathbb{E}(Z^{3})+\cdots\\[0.45em]
&=1+\frac{t^{2}}{\,2n\,}+o\!\left(\frac{\,t^{2}\,}{n}\right),\\[0.2em]
&\qquad t\in\mathbb{R}
\end{aligned}
$$

</div>
</div>

(2) 由於
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
W_n=\frac{\sqrt{n}\,(\overline{X}-\mu)}{\sigma}=\frac{1}{\sqrt{n}}\sum_{i=1}^{n}\Bigl(\frac{X_i-\mu}{\sigma}\Bigr)=\frac{1}{\sqrt{n}}\sum_{i=1}^{n}Z_i
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
W_n&=\frac{\sqrt{n}\,(\overline{X}-\mu)}{\sigma}\\[0.45em]
&=\frac{1}{\sqrt{n}}\sum_{i=1}^{n}\Bigl(\frac{X_i-\mu}{\sigma}\Bigr)\\[0.45em]
&=\frac{1}{\sqrt{n}}\sum_{i=1}^{n}Z_i
\end{aligned}
$$

</div>

故可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{\sssig W_n}(t)&=\mathbb{E}\Bigl(e^{tW_n}\Bigr)=\mathbb{E}\biggl[e^{t\left(\frac{\sum_{i=1}^{n}Z_i}{\sqrt{n}}\right)}\biggr]=\mathbb{E}\biggl(e^{\sum_{i=1}^{n}\frac{\,t\,}{\sqrt{n}}Z_i}\biggr)\\[0.45em]
&=\mathbb{E}\biggl(\prod_{i=1}^{n}e^{\frac{\,t\,}{\sqrt{n}}Z_i}\biggr)=\prod_{i=1}^{n}\mathbb{E}\biggl(e^{\frac{\,t\,}{\sqrt{n}}Z_i}\biggr)=\prod_{i=1}^{n}M_{\sssig Z_i}\biggl(\frac{t}{\sqrt{n}}\biggr)\\[0.45em]
&=\left[M_{\sssig Z}\biggl(\frac{t}{\sqrt{n}}\biggr)\right]^{n},\ t\in\mathbb{R}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig W_n}(t)&=\mathbb{E}\Bigl(e^{tW_n}\Bigr)\\[0.45em]
&=\mathbb{E}\biggl[e^{t\left(\frac{\sum_{i=1}^{n}Z_i}{\sqrt{n}}\right)}\biggr]\\[0.45em]
&=\mathbb{E}\biggl(e^{\sum_{i=1}^{n}\frac{\,t\,}{\sqrt{n}}Z_i}\biggr)\\[0.45em]
&=\mathbb{E}\biggl(\prod_{i=1}^{n}e^{\frac{\,t\,}{\sqrt{n}}Z_i}\biggr)\\[0.45em]
&=\prod_{i=1}^{n}\mathbb{E}\biggl(e^{\frac{\,t\,}{\sqrt{n}}Z_i}\biggr)\\[0.45em]
&=\prod_{i=1}^{n}M_{\sssig Z_i}\biggl(\frac{t}{\sqrt{n}}\biggr)\\[0.45em]
&=\left[M_{\sssig Z}\biggl(\frac{t}{\sqrt{n}}\biggr)\right]^{n},\ t\in\mathbb{R}
\end{aligned}
$$

</div>

(3) 由 (1) 與 (2) 的結果可得
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\lim_{n\to\infty}M_{\sssig W_n}(t)&=\lim_{n\to\infty}\left[M_{\sssig Z}\biggl(\frac{t}{\,\sqrt{n}\,}\biggr)\right]^{n}\\[0.45em]
&=\lim_{n\to\infty}\left[1+\frac{t^{2}}{\,2n\,}+o\!\left(\frac{\,t^{2}\,}{n}\right)\right]^{n}=e^{\frac{\,t^{2}\,}{2}},\ t\in\mathbb{R}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\lim_{n\to\infty}M_{\sssig W_n}(t)&=\lim_{n\to\infty}\left[M_{\sssig Z}\biggl(\frac{t}{\,\sqrt{n}\,}\biggr)\right]^{n}\\[0.45em]
&=\lim_{n\to\infty}\left[1+\frac{t^{2}}{\,2n\,}+o\!\left(\frac{\,t^{2}\,}{n}\right)\right]^{n}\\[0.45em]
&=e^{\frac{\,t^{2}\,}{2}},\ t\in\mathbb{R}
\end{aligned}
$$

</div>

(4) 令 $Z\sim\mathcal{N}(0,1)$ 為一具有標準常態分配之隨機變數，我們有
{: .topic-paren-item}

$$
M_{\sssig Z}(t)=e^{\frac{\,t^{2}\,}{2}},\ t\in\mathbb{R}
$$

又由 (3) 的結論知
{: .topic-paren-cont}

$$
\lim_{n\to\infty}M_{\sssig W_n}(t)=e^{\frac{\,t^{2}\,}{2}}=M_{\sssig Z}(t),\ t\in\mathbb{R}
$$

由[列維連續性定理](/lecture-notes/levy-continuity-theorem/#thm-levys-continuity-thm)可知
{: .topic-paren-cont}

$$
W_n=\frac{\,\sqrt{n}\,(\overline{X}-\mu)\,}{\sigma}\dconv Z\sim\mathcal{N}(0,1)
$$

至此得證中央極限定理。
{: .topic-paren-cont}

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

上題藉由假設 $Z_i$ 的 mgf 存在，以泰勒展開證明 $W_n$ 的 mgf 收斂至標準常態分配的 mgf。須留意 **mgf 存在並非 CLT 的必備條件**；即使母體的 mgf 不存在，仍可透過特徵函數證明 CLT 成立。相對地，母體期望值與有限正變異數存在則是不可或缺的前提；一旦此條件不滿足，即便為 iid 序列，CLT 亦可能失效，見下列反例。

</div>

下面這一題的前半段，也就是由特徵函數的唯一性求出 $\overline{X}$ 的分配這一段，曾以 [Example 2.36](/lecture-notes/characteristic-functions/#ex-cauchy-sample-mean-cf) 出現於特徵函數一篇；此處連同中央極限定理失效的部分完整收錄。

<div id="ex-cauchy-clt-fails" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.18</div>

<div lang="en" markdown="1">
By the central limit theorem, for an iid sample $X_1,X_2,\ldots,X_n$ with <span class="text-nowrap">$\mathbb{E}(X_i^{2})<\infty$,</span> $\sqrt{n}\bigl[\overline{X}-\mathbb{E}(X_1)\bigr]$ converges in distribution to $\mathcal{N}\bigl(0,\mathrm{Var}(X_1)\bigr)$. Now suppose $X_1,X_2,\ldots,X_n$ are iid from $\mathrm{Cauchy}(0,1)$ with pdf

$$
f(x)=\frac{1}{\,\pi(1+x^{2})\,},\ x\in\mathbb{R}
$$

and characteristic function $\phi(t)=\mathbb{E}(e^{itX})=e^{-\lvert t\rvert}$. Show that $\overline{X}=\frac{1}{\,n\,}\sum_{i=1}^{n}X_i$ has the same distribution as <span class="text-nowrap">$X_1$,</span> and conclude that the central limit theorem does not apply to the Cauchy distribution.
</div>

依題意可證明 $\overline{X}$ 與 $X_1$ 之特徵函數相等，其推導如下

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\phi_{\sssig\overline{X}}(t)&=\mathbb{E}(e^{it\overline{X}})=\mathbb{E}\bigl(e^{\sum_{i=1}^{n}i\frac{t}{n}X_i}\bigr)=\mathbb{E}\!\left(\prod_{i=1}^{n}e^{i\frac{t}{n}X_i}\right)=\prod_{i=1}^{n}\mathbb{E}\!\left(e^{i\frac{t}{n}X_i}\right)\\[0.45em]
&=\prod_{i=1}^{n}\phi_{\sssig X_i}\Bigl(\frac{t}{\,n\,}\Bigr)=\prod_{i=1}^{n}e^{-\left\lvert\frac{t}{n}\right\rvert}=\left(e^{-\left\lvert\frac{t}{n}\right\rvert}\right)^{n}=e^{-\lvert t\rvert}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\phi_{\sssig\overline{X}}(t)&=\mathbb{E}(e^{it\overline{X}})\\[0.45em]
&=\mathbb{E}\bigl(e^{\sum_{i=1}^{n}i\frac{t}{n}X_i}\bigr)\\[0.45em]
&=\mathbb{E}\!\left(\prod_{i=1}^{n}e^{i\frac{t}{n}X_i}\right)\\[0.45em]
&=\prod_{i=1}^{n}\mathbb{E}\!\left(e^{i\frac{t}{n}X_i}\right)\\[0.45em]
&=\prod_{i=1}^{n}\phi_{\sssig X_i}\Bigl(\frac{t}{\,n\,}\Bigr)\\[0.45em]
&=\prod_{i=1}^{n}e^{-\left\lvert\frac{t}{n}\right\rvert}=\left(e^{-\left\lvert\frac{t}{n}\right\rvert}\right)^{n}\\[0.45em]
&=e^{-\lvert t\rvert}
\end{aligned}
$$

</div>

由 [cf 之唯一性](/lecture-notes/characteristic-functions/#thm-cf-uniqueness)可知，不論 $n$ 多大，$\overline{X}$ 與 $X_1$ 之分配同為 $\mathrm{Cauchy}(0,1)$ 分配，故 CLT 在此失效。

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

特徵函數的運算性質與 mgf 高度相近，差別在於特徵函數需運用複變指數運算。相較於未必處處存在的 mgf，任何機率分配皆必具備特徵函數，且可藉由反演公式 <span lang="en">(inversion formula)</span> 由特徵函數直接還原對應的 pdf，適用範圍比 mgf 廣泛得多。

回到本題，標準柯西分配之所以使 CLT 失效，關鍵即在於其母體期望值與變異數皆不存在，不滿足定理的前提條件。

</div>

中央極限定理 <span lang="en">(Central Limit Theorem)</span> 有一些地方需要注意:

(1) 中央極限定理指出，當樣本大小 $n$ 趨於無窮大時，樣本平均數 $\overline{X}$ **經標準化後**會分配收斂至標準常態分配。
{: .topic-paren-item}

(2) 弱大數法則與中央極限定理皆考慮 $n\to\infty$ 下樣本平均數 $\overline{X}$ 的漸近行為，但刻畫的層次截然不同；$\overline{X}$ 本身機率收斂至常數 <span class="text-nowrap">$\mu$，</span>標準化後的 $\frac{\,\overline{X}-\mu\,}{\frac{\sigma}{\sqrt{n}}}$ 則分配收斂至服從標準常態分配的隨機變數。兩者對照如下:
{: .topic-paren-item}

**弱大數法則**:
{: .topic-paren-cont}

$$
\overline{X}\pconv\mu
$$

**中央極限定理**:
{: .topic-paren-cont}

$$
\frac{\,\overline{X}-\mu\,}{\frac{\sigma}{\sqrt{n}}}\dconv Z\sim\mathcal{N}(0,1)
$$

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

由弱大數法則可知，中央極限定理的分子 $\overline{X}-\mu$ 機率收斂至 <span class="text-nowrap">$0$，</span>其變異數隨 $n$ 增大而逐漸縮小至 <span class="text-nowrap">$0$，</span>隨機性隨之退化。分母除以同樣隨 $n$ 縮小至 $0$ 的標準差 <span class="text-nowrap">$\frac{\sigma}{\sqrt{n}}$，</span>恰好**將分子的隨機性逐漸退化的過程完全抵消**，使標準化後的結構維持非退化的隨機變異，並分配收斂至標準常態分配。

</div>

(3) 前文曾運用[常態分配](/lecture-notes/normal-distribution/#def-normal)的仿射變換性質，推導出[常態樣本平均數的抽樣分配](/lecture-notes/normal-distribution/#prop-normal-linear-combination):
{: .topic-paren-item}

$$
\text{若}\ X_1,X_2,\ldots,X_n\iidto\mathcal{N}(\mu,\sigma^{2})\text{，則}\ \overline{X}\sim\mathcal{N}\biggl(\mu,\frac{\sigma^{2}}{n}\biggr)
$$

將上式標準化即可改寫為:
{: .topic-paren-cont}

$$
\text{若}\ X_1,X_2,\ldots,X_n\iidto\mathcal{N}(\mu,\sigma^{2})\text{，則}\ \frac{\overline{X}-\mu}{\frac{\sigma}{\sqrt{n}}}\sim\mathcal{N}(0,1)
$$

此一確切抽樣分配性質與中央極限定理不同；當隨機樣本抽自常態母體時，無論樣本大小 $n$ 為何，樣本平均數經標準化後皆必確切服從標準常態分配，完全無須令樣本大小趨於無窮大。
{: .topic-paren-cont}

<div id="ex-uniform-wlln-and-clt" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.19</div>

<div lang="en" markdown="1">
Let $X_1,X_2,\ldots,X_n$ be a random sample from <span class="text-nowrap">$\mathcal{U}(0,1)$,</span> and let $\overline{X}\_{n}=\sum\_{i=1}^{n}\frac{\,X_i\,}{n}$.

<ol class="topic-list-paren">
  <li>Find the constant $c$ such that <span class="text-nowrap">$\overline{X}_n\pconv c$.</span></li>
  <li>Use the central limit theorem to find the constant $d$ such that $\frac{\,2\sum_{i=1}^{n}X_i-n\,}{\sqrt{n}}\dconv\mathcal{N}(0,d)$.</li>
</ol>
</div>

(1) 由 $X_1,\ldots,X_n\iidto\mathcal{U}(0,1)$ 可知
{: .topic-paren-item}

$$
\mathbb{E}(X_i)=\frac{1}{\,2\,},\ \mathrm{Var}(X_i)=\frac{1}{\,12\,}
$$

則由 WLLN 可知
{: .topic-paren-cont}

$$
\overline{X}_n\pconv\mathbb{E}(X_i)=\frac{1}{\,2\,}
$$

故可知
{: .topic-paren-cont}

$$
c=\frac{1}{\,2\,}
$$

(2) 由中央極限定理可知
{: .topic-paren-item}

$$
\frac{\,\sum_{i=1}^{n}X_i-\frac{n}{\,2\,}\,}{\sqrt{n}\sqrt{\frac{1}{\,12\,}}}\dconv Z\sim\mathcal{N}(0,1)
$$

故可知道
{: .topic-paren-cont}

$$
\begin{aligned}
\frac{\,2\sum_{i=1}^{n}X_i-n\,}{\sqrt{n}}&=2\sqrt{\frac{1}{12}}\times\frac{\,\sum_{i=1}^{n}X_i-\frac{n}{\,2\,}\,}{\sqrt{n}\sqrt{\frac{1}{\,12\,}}}\\[0.45em]
&\dconv2\sqrt{\frac{1}{12}}\times Z\sim\mathcal{N}\left(0,\frac{1}{\,3\,}\right)
\end{aligned}
$$

故可知
{: .topic-paren-cont}

$$
d=\frac{1}{\,3\,}
$$

</div>

<div id="ex-chi-square-sum-clt" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.20</div>

<div lang="en" markdown="1">
Let $X_1,X_2,\ldots,X_n$ be independent chi-square random variables each with $1$ degree of freedom, and let $Y=\sum_{i=1}^{n}X_i$. Find the limiting distribution of <span class="text-nowrap">$Z=(Y/\sqrt{n}-\sqrt{n})$.</span>
</div>

由 $X_1,X_2,\ldots,X_n\iidto\chi^{2}(\nu=1)$ 可知

$$
\mu=\nu=1,\ \sigma^{2}=2\nu=2
$$

由中央極限定理，我們有

<div class="topic-math-follow-before" markdown="1">

$$
\frac{\sum_{i=1}^{n}X_i-n\mu}{\sqrt{n\sigma^{2}}}=\frac{Y-n}{\sqrt{2n}}\dconv W\sim\mathcal{N}(0,1)
$$

</div>
<div class="topic-math-follow" markdown="1">
<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\Longrightarrow\ Z=\frac{Y}{\sqrt{n}}-\sqrt{n}=\frac{Y-n}{\sqrt{n}}=\sqrt{2}\left(\frac{Y-n}{\sqrt{2n}}\right)\dconv\sqrt{2}\,W\sim\mathcal{N}(0,2)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ Z&=\frac{Y}{\sqrt{n}}-\sqrt{n}=\frac{Y-n}{\sqrt{n}}\\[0.45em]
&=\sqrt{2}\left(\frac{Y-n}{\sqrt{2n}}\right)\\[0.45em]
&\dconv\sqrt{2}\,W\sim\mathcal{N}(0,2)
\end{aligned}
$$

</div>
</div>

</div>

在上述兩道例題中，我們皆將中央極限定理的標準化統計量再乘上一個非零常數；非零常數倍伸縮不會改變常態極限分配的型態，僅會等比例調整極限分配的變異數。據此可整理出中央極限定理常用的四種等價形式如下。

**(中央極限定理的各種變化版本)**

令 $\lbrace X_n\rbrace_{n=1}^{\infty}$ 為一定義在機率空間上之 iid 隨機變數序列，且期望值 $\mu$ 與變異數 $\sigma^{2}$ 皆存在，則當 $n$ 趨近於無窮大，我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
&\diamond\quad\frac{\,\overline{X}-\mu\,}{\frac{\sigma}{\sqrt{n}}}=\frac{\,\sqrt{n}(\overline{X}-\mu)\,}{\sigma}\dconv Z\sim\mathcal{N}(0,1)\\[0.65em]
&\diamond\quad\frac{\,\sum_{i=1}^{n}X_i-n\mu\,}{\sqrt{n}\sigma}\dconv Z\sim\mathcal{N}(0,1)\\[0.65em]
&\diamond\quad\sqrt{n}\,(\overline{X}-\mu)\dconv\sigma Z\sim\mathcal{N}(0,\sigma^{2})\\[0.65em]
&\diamond\quad\frac{\,\sum_{i=1}^{n}X_i-n\mu\,}{\sqrt{n}}\dconv\sigma Z\sim\mathcal{N}(0,\sigma^{2})
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\diamond\quad\frac{\,\overline{X}-\mu\,}{\frac{\sigma}{\sqrt{n}}}=\frac{\,\sqrt{n}(\overline{X}-\mu)\,}{\sigma}\\[0.25em]
&\qquad\qquad\dconv Z\sim\mathcal{N}(0,1)\\[0.6em]
&\diamond\quad\frac{\,\sum_{i=1}^{n}X_i-n\mu\,}{\sqrt{n}\sigma}\dconv Z\sim\mathcal{N}(0,1)\\[0.6em]
&\diamond\quad\sqrt{n}\,(\overline{X}-\mu)\dconv\sigma Z\sim\mathcal{N}(0,\sigma^{2})\\[0.6em]
&\diamond\quad\frac{\,\sum_{i=1}^{n}X_i-n\mu\,}{\sqrt{n}}\dconv\sigma Z\sim\mathcal{N}(0,\sigma^{2})
\end{aligned}
$$

</div>

以上這些版本都能夠稱作中央極限定理。稍後，我們還會再看到基於這些中央極限定理變化版本的一些延伸應用。

## 本篇小結

[Theorem 5.7](#thm-weak-law-of-large-numbers) 的弱大數法則說，iid 序列在期望值 $\mu$ 與變異數 $\sigma^{2}$ 皆存在時，樣本平均數 $\overline{X}$ 機率收斂至常數 <span class="text-nowrap">$\mu$。</span>證明只用到 $\mathrm{Var}\bigl(\overline{X}\bigr)=\frac{\sigma^{2}}{\,n\,}$ 與柴比雪夫不等式，後者把 $\mathbb{P}\bigl(\lvert\overline{X}-\mu\rvert<\varepsilon\bigr)$ 由下界住於 $1-\frac{\sigma^{2}}{\,n\varepsilon^{2}\,}$ 這個值，而這個下界隨 $n$ 趨於 <span class="text-nowrap">$1$。</span>柴比雪夫不等式要求 $\mu$ 與 $\sigma^{2}$ 都存在，但這只是這一條證明路線的條件，變異數不存在時另有別的證明方法。

[Example 5.15](#ex-wlln-second-moment) 與 [Example 5.16](#ex-wlln-paired-difference) 示範同一種延伸用法。弱大數法則講的是 $\overline{X}$ 收斂到期望值 <span class="text-nowrap">$\mathbb{E}(X_i)$，</span>只要把新的隨機變數取為原變數的函數，就能得到別的機率極限。前者取 <span class="text-nowrap">$Y_i=X_i^{2}$，</span>因而 $\frac{1}{\,n\,}\sum_{i=1}^{n}X_i^{2}$ 機率收斂至 $\mathbb{E}(X_i^{2})=\mu+\mu^{2}$ 這一常數；後者取 $k(X_i-Y_i)^{2}$ 這一組合，其期望值為 <span class="text-nowrap">$2k\sigma^{2}$，</span>要它等於 $\sigma^{2}$ 便得到 $k=\frac{1}{\,2\,}$ 這個答案。

[Theorem 5.8](#thm-central-limit-theorem) 的中央極限定理則說標準化之後的 $\frac{\,\sqrt{n}(\overline{X}-\mu)\,}{\sigma}$ 分配收斂至標準常態分配。[Example 5.17](#ex-clt-proof-by-mgf) 給出大學部教本常見的那一條證明路線，先把 $M_{\sssig Z}\bigl(\frac{t}{\sqrt{n}}\bigr)$ 在 $t=0$ 處展開成 $1+\frac{t^{2}}{\,2n\,}+o\bigl(\frac{\,t^{2}\,}{n}\bigr)$ 這個式子，再由獨立性得到 $M_{\sssig W_n}(t)=\bigl[M_{\sssig Z}\bigl(\frac{t}{\sqrt{n}}\bigr)\bigr]^{n}$ 這個關係，取極限即得標準常態的 mgf $e^{\frac{\,t^{2}\,}{2}}$ 這個函數，最後由列維連續性定理把 mgf 的收斂換成分配的收斂。這條路線多假設了 mgf 存在，而中央極限定理本身並不需要這個條件。

[Example 5.18](#ex-cauchy-clt-fails) 則是前提不成立的反例。標準柯西分配沒有期望值也沒有變異數，其特徵函數 $e^{-\lvert t\rvert}$ 使 $\overline{X}$ 的特徵函數仍為 <span class="text-nowrap">$e^{-\lvert t\rvert}$，</span>因此不論樣本大小多大，$\overline{X}$ 與單一觀測值同分配，中央極限定理在此失效。

其後的三點注意事項把兩條定理擺在一起比較，$\overline{X}$ 機率收斂到 $\mu$ 這個常數，而 $\frac{\,\overline{X}-\mu\,}{\frac{\sigma}{\sqrt{n}}}$ 分配收斂到一個隨機變數，兩者的差別在於分母上那個逐漸縮小到 $0$ 的標準差恰好抵消了分子隨機性退化的過程。另一項對照是常態隨機樣本，這時 $\frac{\,\overline{X}-\mu\,}{\frac{\sigma}{\sqrt{n}}}$ 對每一個樣本大小都恰為標準常態分配，不必取極限，與中央極限定理是兩回事。[Example 5.19](#ex-uniform-wlln-and-clt) 與 [Example 5.20](#ex-chi-square-sum-clt) 分別在均勻母體與卡方母體上把兩條定理用過一遍，兩題都在中央極限定理的結論之外再乘上一個常數，這個動作不影響收斂本身，只影響極限分配的變異數，中央極限定理的四種寫法正是由此而來。

[下一篇](/lecture-notes/normal-approximation-continuity-correction/)把中央極限定理用在近似計算上，處理以常態分配近似離散型分配時所需要的連續性校正。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- Krishna B. Athreya and Soumendra N. Lahiri. 2006. *Measure Theory and Probability Theory*. Springer.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
