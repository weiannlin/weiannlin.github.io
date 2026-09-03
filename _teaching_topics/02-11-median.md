---
title: "中位數"
subtitle: "Median"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 11
order: 211
permalink: /lecture-notes/median/
date: 2026-08-06
published: true
excerpt: "中位數是把一個分配切成前後兩段的量數: 只要 $\\mathbb{P}(X\\leqslant\\eta_{X})$ 與 $\\mathbb{P}(X\\geqslant\\eta_{X})$ 都不小於 $\\frac{1}{2}$，$\\eta_{X}$ 就是 $X$ 的中位數。它可能不唯一，甚至可能不在值域內，取 $\\inf\\lbrace x\\mid F_{X}(x)\\geqslant\\frac{1}{2}\\rbrace$ 可以找到其中一個；若 $F_{X}$ 連續且在值域上嚴格遞增，中位數唯一且等於 $F_{X}^{-1}(\\frac{1}{2})$。衡量離散程度時若把平方換成距離，則使 $\\mathbb{E}(\\lvert X-a\\rvert)$ 達到最小的 $a$ 正是中位數，這與期望值使平方離差的期望值達到最小恰成對照。"
---

[上一篇](/lecture-notes/mode/)介紹[眾數](/lecture-notes/mode/#def-mode)，也就是使機率函數在值域的閉包上取到最大值的那些點。眾數關心的是一個分配的哪一處最可能發生，但要指出一個分配的中央位置，還有另一種常見的作法，找一個點，使它左右兩側的機率各佔一半。

本篇介紹的中位數就是這樣的量數。以下先給出定義，接著說明中位數可能不唯一、如何由[累積分配函數](/lecture-notes/cumulative-distribution-functions/#def-cdf)找到其中一個，以及它把分配切成前後兩段的直觀；然後介紹一個與[期望值](/lecture-notes/expectation/#def-expectation)恰成對照的性質: [期望值使平方離差的期望值達到最小](/lecture-notes/variance-standard-deviation/#thm-mean-minimizes-squared-deviation)，中位數則使絕對離差的期望值達到最小，並附上證明與逐步的說明；最後以一張圖說明中位數的直觀意涵。

<div id="def-median" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.10 (中位數, median)</div>

令 $X$ 為一[隨機變數](/lecture-notes/random-variables-and-pmf/#def-random-variable)，若 $\eta\_{\sssig X}$ 滿足

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X\leqslant\eta_{\sssig X})\geqslant\frac{1}{2}\quad\text{且}\quad\mathbb{P}(X\geqslant\eta_{\sssig X})\geqslant\frac{1}{2}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X\leqslant\eta_{\sssig X})&\geqslant\frac{1}{2}\\[0.45em]
\text{且}\quad\mathbb{P}(X\geqslant\eta_{\sssig X})&\geqslant\frac{1}{2}
\end{aligned}
$$

</div>

則稱 $\eta\_{\sssig X}$ 為 $X$ 的**中位數 (median)**。

</div>

中位數有一些地方需要注意:

(1) 上述定義中的中位數較常被稱為**母體中位數 <span lang="en">(population median)</span>**，用以避免跟敘述統計學中的**樣本中位數 (sample median)** 混淆。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

與眾數相同，中位數亦可能不唯一，或甚至不在值域內。

</div>

(2) 由於中位數未必唯一，我們可以透過下式找到**一個**中位數
{: .topic-paren-item}

$$
\eta_{\sssig X}=\inf\Bigl\lbrace\,x\in\mathbb{R}\,\Big|\,F_{\sssig X}(x)\geqslant\frac{1}{2}\,\Bigr\rbrace
$$

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

在 $F\_{\sssig X}$ 連續且在值域 $\mathcal{R}\_{\sssig X}$ 上嚴格遞增的分配中，此方法所找到的中位數會是下面這個值

$$
\eta_{\sssig X}=F^{-1}_{\sssig X}\left(\frac{1}{2}\right)
$$

而且這也是該分配唯一的中位數。

</div>

(3) 直觀上來說，中位數的意義在於**該點將整個分配分成前後兩半**，這套定義與直觀，能夠直接推廣至[**分位數 <span lang="en">(quantile)</span>**](/lecture-notes/quantiles/#def-quantile) 上，我們稍後會談到。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

由於中位數將整個分配切為前後兩段，故在一個對稱分配上，中位數正好會在整個分配的正中間，特別如果該對稱分配是單峰對稱分配，則中位數的位置，與期望值和眾數會是相同的。

</div>

在 [Theorem 2.14](/lecture-notes/variance-standard-deviation/#thm-mean-minimizes-squared-deviation) 中我們曾提過，$\mathbb{E}\bigl[(X-a)^{2}\bigr]$ 是一種 $X$ 與 $a$ 之間的平均離散程度，但離散程度未必要使用平方作為考量。某些時候我們會使用 $X$ 和 $a$ 的**距離**，也就是 $\lvert X-a\rvert$，作為離散程度的依據，此時我們會有以下定理。

<div id="thm-median-minimizes-absolute-deviation" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.17 (中位數使絕對離差的期望值最小, the median minimizes the mean absolute deviation)</div>

若 $X$ 為一連續型隨機變數，pdf 為 <span class="text-nowrap">$f\_{\sssig X}(x)$，</span>且 <span class="text-nowrap">$\mathbb{E}\bigl(\lvert X\rvert\bigr)<\infty$，</span>令

$$
g(a)=\mathbb{E}\bigl[\lvert X-a\rvert\bigr],\quad\forall a\in\mathbb{R}
$$

則 $X$ 的中位數 $\eta\_{\sssig X}$ 是使得 $g(a)$ 達到最小值的 $a$，此即

$$
g(a)\geqslant g(\eta_{\sssig X}),\quad\forall a\in\mathbb{R}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

[Theorem 2.17](#thm-median-minimizes-absolute-deviation) 的前提限定為連續型，是為了與下面的證明相符，證明中會用到下面這條性質

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\int_{-\infty}^{\eta_{\sssig X}}f_{\sssig X}(x)\,dx=\frac{1}{2}\quad\text{與}\quad\int_{\eta_{\sssig X}}^{\infty}f_{\sssig X}(x)\,dx=\frac{1}{2}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\int_{-\infty}^{\eta_{\sssig X}}f_{\sssig X}(x)\,dx&=\frac{1}{2}\\[0.45em]
\text{與}\quad\int_{\eta_{\sssig X}}^{\infty}f_{\sssig X}(x)\,dx&=\frac{1}{2}
\end{aligned}
$$

</div>

這兩個等式，而 [Definition 2.10](#def-median) 給的是兩個 $\geqslant\frac{1}{2}$ 的不等式，離散型與混合型未必取到等號。事實上，只要 $\mathbb{E}\bigl(\lvert X\rvert\bigr)<\infty$，這個結論對一般的隨機變數都成立，只是證明較繁，須改由累積分配函數著手，本篇不再細談。

</div>

<div class="topic-proof" markdown="1">
**Proof.**

由 [Definition 2.10](#def-median) 與絕對值的分段寫法可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
g(a)&=\mathbb{E}\bigl[\lvert X-a\rvert\bigr]=\int_{-\infty}^{\infty}\lvert x-a\rvert\,f_{\sssig X}(x)\,dx\\[0.45em]
&=\int_{-\infty}^{a}(a-x)\,f_{\sssig X}(x)\,dx+\int_{a}^{\infty}(x-a)\,f_{\sssig X}(x)\,dx\\[0.45em]
&=\int_{-\infty}^{\eta_{\sssig X}}(a-x)\,f_{\sssig X}(x)\,dx+\int_{\eta_{\sssig X}}^{a}(a-x)\,f_{\sssig X}(x)\,dx\\[0.2em]
&\quad+\int_{a}^{\eta_{\sssig X}}(x-a)\,f_{\sssig X}(x)\,dx+\int_{\eta_{\sssig X}}^{\infty}(x-a)\,f_{\sssig X}(x)\,dx\\[0.45em]
&=\int_{-\infty}^{\eta_{\sssig X}}(\eta_{\sssig X}-x)\,f_{\sssig X}(x)\,dx+\int_{\eta_{\sssig X}}^{\infty}(x-\eta_{\sssig X})\,f_{\sssig X}(x)\,dx\\[0.2em]
&\quad+2\int_{a}^{\eta_{\sssig X}}(x-a)\,f_{\sssig X}(x)\,dx\\[0.45em]
&=\mathbb{E}\bigl[\lvert X-\eta_{\sssig X}\rvert\bigr]+2\int_{a}^{\eta_{\sssig X}}(x-a)\,f_{\sssig X}(x)\,dx\\[0.45em]
&\geqslant\mathbb{E}\bigl[\lvert X-\eta_{\sssig X}\rvert\bigr]=g(\eta_{\sssig X})
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
g(a)&=\mathbb{E}\bigl[\lvert X-a\rvert\bigr]\\[0.45em]
&=\int_{-\infty}^{\infty}\lvert x-a\rvert\,f_{\sssig X}(x)\,dx\\[0.45em]
&=\int_{-\infty}^{a}(a-x)\,f_{\sssig X}(x)\,dx\\[0.2em]
&\qquad+\int_{a}^{\infty}(x-a)\,f_{\sssig X}(x)\,dx\\[0.45em]
&=\int_{-\infty}^{\eta_{\sssig X}}(a-x)\,f_{\sssig X}(x)\,dx\\[0.2em]
&\qquad+\int_{\eta_{\sssig X}}^{a}(a-x)\,f_{\sssig X}(x)\,dx\\[0.2em]
&\qquad+\int_{a}^{\eta_{\sssig X}}(x-a)\,f_{\sssig X}(x)\,dx\\[0.2em]
&\qquad+\int_{\eta_{\sssig X}}^{\infty}(x-a)\,f_{\sssig X}(x)\,dx\\[0.45em]
&=\int_{-\infty}^{\eta_{\sssig X}}(\eta_{\sssig X}-x)\,f_{\sssig X}(x)\,dx\\[0.2em]
&\qquad+\int_{\eta_{\sssig X}}^{\infty}(x-\eta_{\sssig X})\,f_{\sssig X}(x)\,dx\\[0.2em]
&\qquad+2\int_{a}^{\eta_{\sssig X}}(x-a)\,f_{\sssig X}(x)\,dx\\[0.45em]
&=\mathbb{E}\bigl[\lvert X-\eta_{\sssig X}\rvert\bigr]\\[0.2em]
&\qquad+2\int_{a}^{\eta_{\sssig X}}(x-a)\,f_{\sssig X}(x)\,dx\\[0.45em]
&\geqslant\mathbb{E}\bigl[\lvert X-\eta_{\sssig X}\rvert\bigr]=g(\eta_{\sssig X})
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

上述的證明中，使用了積分範圍的拆解，其中比較關鍵的地方不少，首先是下面這一步

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\int_{\eta_{\sssig X}}^{a}(a-x)\,f_{\sssig X}(x)\,dx&=-\int_{a}^{\eta_{\sssig X}}(a-x)\,f_{\sssig X}(x)\,dx\\[0.45em]
&=\int_{a}^{\eta_{\sssig X}}(x-a)\,f_{\sssig X}(x)\,dx
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\int_{\eta_{\sssig X}}^{a}(a-x)\,f_{\sssig X}(x)\,dx\\[0.45em]
&=-\int_{a}^{\eta_{\sssig X}}(a-x)\,f_{\sssig X}(x)\,dx\\[0.45em]
&=\int_{a}^{\eta_{\sssig X}}(x-a)\,f_{\sssig X}(x)\,dx
\end{aligned}
$$

</div>

由此可將過程中的其中二項合併，即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
&\int_{\eta_{\sssig X}}^{a}(a-x)\,f_{\sssig X}(x)\,dx+\int_{a}^{\eta_{\sssig X}}(x-a)\,f_{\sssig X}(x)\,dx\\[0.45em]
&\quad=2\int_{a}^{\eta_{\sssig X}}(x-a)\,f_{\sssig X}(x)\,dx
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\int_{\eta_{\sssig X}}^{a}(a-x)\,f_{\sssig X}(x)\,dx\\[0.2em]
&\qquad+\int_{a}^{\eta_{\sssig X}}(x-a)\,f_{\sssig X}(x)\,dx\\[0.45em]
&=2\int_{a}^{\eta_{\sssig X}}(x-a)\,f_{\sssig X}(x)\,dx
\end{aligned}
$$

</div>

再者則是利用了以下的等式

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\int_{-\infty}^{\eta_{\sssig X}}(a-x)\,f_{\sssig X}(x)\,dx&=a\int_{-\infty}^{\eta_{\sssig X}}f_{\sssig X}(x)\,dx-\int_{-\infty}^{\eta_{\sssig X}}x\,f_{\sssig X}(x)\,dx\\[0.45em]
&=a\cdot\frac{1}{2}-\int_{-\infty}^{\eta_{\sssig X}}x\,f_{\sssig X}(x)\,dx
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\int_{-\infty}^{\eta_{\sssig X}}(a-x)\,f_{\sssig X}(x)\,dx\\[0.45em]
&=a\int_{-\infty}^{\eta_{\sssig X}}f_{\sssig X}(x)\,dx-\int_{-\infty}^{\eta_{\sssig X}}x\,f_{\sssig X}(x)\,dx\\[0.45em]
&=a\cdot\frac{1}{2}-\int_{-\infty}^{\eta_{\sssig X}}x\,f_{\sssig X}(x)\,dx
\end{aligned}
$$

</div>

以及

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\int_{\eta_{\sssig X}}^{\infty}(x-a)\,f_{\sssig X}(x)\,dx&=\int_{\eta_{\sssig X}}^{\infty}x\,f_{\sssig X}(x)\,dx-a\int_{\eta_{\sssig X}}^{\infty}f_{\sssig X}(x)\,dx\\[0.45em]
&=\int_{\eta_{\sssig X}}^{\infty}x\,f_{\sssig X}(x)\,dx-a\cdot\frac{1}{2}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\int_{\eta_{\sssig X}}^{\infty}(x-a)\,f_{\sssig X}(x)\,dx\\[0.45em]
&=\int_{\eta_{\sssig X}}^{\infty}x\,f_{\sssig X}(x)\,dx-a\int_{\eta_{\sssig X}}^{\infty}f_{\sssig X}(x)\,dx\\[0.45em]
&=\int_{\eta_{\sssig X}}^{\infty}x\,f_{\sssig X}(x)\,dx-a\cdot\frac{1}{2}
\end{aligned}
$$

</div>

由此可合併得到

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
&\int_{-\infty}^{\eta_{\sssig X}}(a-x)\,f_{\sssig X}(x)\,dx+\int_{\eta_{\sssig X}}^{\infty}(x-a)\,f_{\sssig X}(x)\,dx\\[0.45em]
&\quad=\int_{\eta_{\sssig X}}^{\infty}x\,f_{\sssig X}(x)\,dx-\int_{-\infty}^{\eta_{\sssig X}}x\,f_{\sssig X}(x)\,dx
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\int_{-\infty}^{\eta_{\sssig X}}(a-x)\,f_{\sssig X}(x)\,dx\\[0.2em]
&\qquad+\int_{\eta_{\sssig X}}^{\infty}(x-a)\,f_{\sssig X}(x)\,dx\\[0.45em]
&=\int_{\eta_{\sssig X}}^{\infty}x\,f_{\sssig X}(x)\,dx-\int_{-\infty}^{\eta_{\sssig X}}x\,f_{\sssig X}(x)\,dx
\end{aligned}
$$

</div>

接著利用

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
&\int_{-\infty}^{\eta_{\sssig X}}\eta_{\sssig X}\,f_{\sssig X}(x)\,dx-\int_{\eta_{\sssig X}}^{\infty}\eta_{\sssig X}\,f_{\sssig X}(x)\,dx\\[0.45em]
&\quad=\eta_{\sssig X}\int_{-\infty}^{\eta_{\sssig X}}f_{\sssig X}(x)\,dx-\eta_{\sssig X}\int_{\eta_{\sssig X}}^{\infty}f_{\sssig X}(x)\,dx=0
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\int_{-\infty}^{\eta_{\sssig X}}\eta_{\sssig X}\,f_{\sssig X}(x)\,dx-\int_{\eta_{\sssig X}}^{\infty}\eta_{\sssig X}\,f_{\sssig X}(x)\,dx\\[0.45em]
&=\eta_{\sssig X}\int_{-\infty}^{\eta_{\sssig X}}f_{\sssig X}(x)\,dx-\eta_{\sssig X}\int_{\eta_{\sssig X}}^{\infty}f_{\sssig X}(x)\,dx\\[0.45em]
&=0
\end{aligned}
$$

</div>

與前式合併可得到

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
&\int_{-\infty}^{\eta_{\sssig X}}(a-x)\,f_{\sssig X}(x)\,dx+\int_{\eta_{\sssig X}}^{\infty}(x-a)\,f_{\sssig X}(x)\,dx+0\\[0.45em]
&\quad=\int_{\eta_{\sssig X}}^{\infty}x\,f_{\sssig X}(x)\,dx-\int_{-\infty}^{\eta_{\sssig X}}x\,f_{\sssig X}(x)\,dx\\[0.2em]
&\qquad+\int_{-\infty}^{\eta_{\sssig X}}\eta_{\sssig X}\,f_{\sssig X}(x)\,dx-\int_{\eta_{\sssig X}}^{\infty}\eta_{\sssig X}\,f_{\sssig X}(x)\,dx\\[0.45em]
&\quad=\int_{-\infty}^{\eta_{\sssig X}}(\eta_{\sssig X}-x)\,f_{\sssig X}(x)\,dx+\int_{\eta_{\sssig X}}^{\infty}(x-\eta_{\sssig X})\,f_{\sssig X}(x)\,dx\\[0.45em]
&\quad=\mathbb{E}\bigl[\lvert X-\eta_{\sssig X}\rvert\bigr]
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\int_{-\infty}^{\eta_{\sssig X}}(a-x)\,f_{\sssig X}(x)\,dx\\[0.2em]
&\qquad+\int_{\eta_{\sssig X}}^{\infty}(x-a)\,f_{\sssig X}(x)\,dx+0\\[0.45em]
&=\int_{\eta_{\sssig X}}^{\infty}x\,f_{\sssig X}(x)\,dx\\[0.2em]
&\qquad-\int_{-\infty}^{\eta_{\sssig X}}x\,f_{\sssig X}(x)\,dx\\[0.2em]
&\qquad+\int_{-\infty}^{\eta_{\sssig X}}\eta_{\sssig X}\,f_{\sssig X}(x)\,dx\\[0.2em]
&\qquad-\int_{\eta_{\sssig X}}^{\infty}\eta_{\sssig X}\,f_{\sssig X}(x)\,dx\\[0.45em]
&=\int_{-\infty}^{\eta_{\sssig X}}(\eta_{\sssig X}-x)\,f_{\sssig X}(x)\,dx\\[0.2em]
&\qquad+\int_{\eta_{\sssig X}}^{\infty}(x-\eta_{\sssig X})\,f_{\sssig X}(x)\,dx\\[0.45em]
&=\mathbb{E}\bigl[\lvert X-\eta_{\sssig X}\rvert\bigr]
\end{aligned}
$$

</div>

最後分析 $2\int_{a}^{\eta_{\sssig X}}(x-a)\,f_{\sssig X}(x)\,dx$ 這一項，可分為 $\eta\_{\sssig X}\leqslant a$ 與 $\eta\_{\sssig X}>a$ 討論。

**[ $\eta\_{\sssig X}\leqslant a$ ]**

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
2\int_{a}^{\eta_{\sssig X}}(x-a)\,f_{\sssig X}(x)\,dx=2\int_{\eta_{\sssig X}}^{a}(a-x)\,f_{\sssig X}(x)\,dx\geqslant0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&2\int_{a}^{\eta_{\sssig X}}(x-a)\,f_{\sssig X}(x)\,dx\\[0.45em]
&=2\int_{\eta_{\sssig X}}^{a}(a-x)\,f_{\sssig X}(x)\,dx\geqslant0
\end{aligned}
$$

</div>

**[ $\eta\_{\sssig X}>a$ ]**

$$
2\int_{a}^{\eta_{\sssig X}}(x-a)\,f_{\sssig X}(x)\,dx\geqslant0
$$

故可知道

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
g(a)&=\mathbb{E}\bigl[\lvert X-\eta_{\sssig X}\rvert\bigr]+2\int_{a}^{\eta_{\sssig X}}(x-a)\,f_{\sssig X}(x)\,dx\\[0.45em]
&\geqslant\mathbb{E}\bigl[\lvert X-\eta_{\sssig X}\rvert\bigr]=g(\eta_{\sssig X}),\quad\forall a\in\mathbb{R}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
g(a)&=\mathbb{E}\bigl[\lvert X-\eta_{\sssig X}\rvert\bigr]\\[0.2em]
&\qquad+2\int_{a}^{\eta_{\sssig X}}(x-a)\,f_{\sssig X}(x)\,dx\\[0.45em]
&\geqslant\mathbb{E}\bigl[\lvert X-\eta_{\sssig X}\rvert\bigr]\\[0.2em]
&=g(\eta_{\sssig X}),\quad\forall a\in\mathbb{R}
\end{aligned}
$$

</div>

原式得證。

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

若使用離差的絕對值，作為離散程度的考量，則好處是單位與原本相同，但隨之而來的缺點是絕對值的運算性質並不好。從直觀上而言，這個定理指出**平均來說，所有 $X$ 到中位數 $\eta\_{\sssig X}$ 的距離是最短的**。

</div>

下面就用圖示來理解中位數的直觀意涵。

<figure id="fig-median-intuition" class="topic-figure topic-figure--wide">
  <img src="/images/lecture-notes/median-intuition.svg" alt="一條右偏的機率密度曲線，橫軸為 x，曲線自左端升起、達到峰值之後緩緩落回。曲線下方由一條垂直虛線分成左右兩塊，虛線與橫軸相交處標為 η_X。虛線左側的區域加上陰影並標示二分之一，虛線右側未加陰影，同樣標示二分之一，表示兩塊面積相等。">
  <figcaption><span class="topic-figure__label">Fig. 2.14.</span> 中位數 $\eta_{\sssig X}$ 把密度曲線下方的面積切成相等的兩塊，左右各為 $\frac{1}{2}$，圖中以陰影標出左邊那一塊。</figcaption>
</figure>

## 本篇小結

[Definition 2.10](#def-median) 以 $\mathbb{P}(X\leqslant\eta_{\sssig X})\geqslant\frac{1}{2}$ 與 $\mathbb{P}(X\geqslant\eta_{\sssig X})\geqslant\frac{1}{2}$ 兩個不等式界定中位數 $\eta_{\sssig X}$，指稱時以母體中位數與樣本中位數區別。中位數可能不唯一，甚至可能不在值域內；由累積分配函數取下確界 $\inf\lbrace x\in\mathbb{R}\mid F_{\sssig X}(x)\geqslant\frac{1}{2}\rbrace$ 可以找到其中一個，而在 $F_{\sssig X}$ 連續且於值域上嚴格遞增時，中位數唯一且等於 $F^{-1}_{\sssig X}(\frac{1}{2})$。它把整個分配切成前後兩段的直觀，稍後會直接推廣到分位數；在對稱分配上它落在正中間，若又是單峰對稱分配，則與期望值和眾數同在一點。

[Theorem 2.17](#thm-median-minimizes-absolute-deviation) 與 [Theorem 2.14](/lecture-notes/variance-standard-deviation/#thm-mean-minimizes-squared-deviation) 恰成對照。平均離散程度若以平方衡量，使它最小的是期望值；若改以距離衡量，使 $\mathbb{E}\bigl[\lvert X-a\rvert\bigr]$ 最小的則是中位數。證明的作法是把 $\lvert x-a\rvert$ 的積分依 $a$ 與 $\eta_{\sssig X}$ 拆成四段，合併之後餘下一個非負的項，該項在 $a=\eta_{\sssig X}$ 時為零。[Fig. 2.14](#fig-median-intuition) 則畫出了中位數把密度曲線下方的面積切成相等兩塊的樣子。

[下一篇](/lecture-notes/quantiles/)接著把中位數推廣為分位數，其中的 [Example 2.26](/lecture-notes/quantiles/#ex-nonunique-median) 會給出一個中位數不唯一的具體例子。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Morris H. DeGroot and Mark J. Schervish. 2012. *Probability and Statistics*. 4th ed. Pearson.
- Alexander M. Mood, Franklin A. Graybill, and Duane C. Boes. 1974. *Introduction to the Theory of Statistics*. 3rd ed. McGraw-Hill.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
