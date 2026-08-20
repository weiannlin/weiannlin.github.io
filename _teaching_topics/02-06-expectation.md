---
title: "期望值"
subtitle: "Expectation"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 6
order: 206
permalink: /lecture-notes/expectation/
date: 2026-08-05
published: true
excerpt: "期望值是隨機變數的加權平均: 離散型以機率質量函數對各個取值加權求和，連續型以機率密度函數對取值加權積分，兩者都以絕對收斂為存在的條件。它是一個分配的聚集中心，在質點的類比之下即為物理學的質心，也是使平方離差的期望值達到最小的那個位置，故亦稱為母體平均數。若隨機變數非負，期望值還可以改由尾機率求得，離散型加總 $\\mathbb{P}(X\\geqslant x)$，連續型則積分 $\\mathbb{P}(X>x)$。"
---

[上一篇](/lecture-notes/mixed-random-variables/)談混合型[隨機變數](/lecture-notes/random-variables-and-pmf/#def-random-variable)與分解定理。至此，離散型、連續型與混合型的機率函數都已經介紹完畢，一個隨機變數的分配可以由 pmf、pdf 或 cdf 完整描述。

完整的分配包含了全部的資訊，但在許多場合，我們只需要幾個數字就能掌握一個分配的主要特色。本篇介紹其中最基本的一個，期望值。以下先分別給出離散型與連續型的定義，說明它作為加權平均與分配聚集中心的意義，接著以四個例題示範計算，最後介紹非負隨機變數的期望值如何改由尾機率求得。

<div id="def-expectation" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.6 (期望值, expectation)</div>

若 $X$ 為離散型隨機變數，值域為 $\mathcal{R}\_{\sssig X}$、pmf 為 $p\_{\sssig X}(x)$，且

$$
\sum_{x\in\mathbb{R}}\lvert x\rvert\,p_{\sssig X}(x)<\infty
$$

則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mu_{\sssig X}=\mathbb{E}(X)=\sum_{x\in\mathbb{R}}x\,p_{\sssig X}(x)=\sum_{x\in\mathcal{R}_{\sssig X}}x\,p_{\sssig X}(x)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mu_{\sssig X}&=\mathbb{E}(X)=\sum_{x\in\mathbb{R}}x\,p_{\sssig X}(x)\\[0.45em]
&=\sum_{x\in\mathcal{R}_{\sssig X}}x\,p_{\sssig X}(x)
\end{aligned}
$$

</div>

為 $X$ 的**期望值 <span lang="en">(expectation)</span>**。

若 $X$ 為連續型隨機變數，值域為 $\mathcal{R}\_{\sssig X}$、pdf 為 $f\_{\sssig X}(x)$，且

$$
\int_{x\in\mathbb{R}}\lvert x\rvert f_{\sssig X}(x)\,dx<\infty
$$

則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mu_{\sssig X}=\mathbb{E}(X)=\int_{-\infty}^{\infty}xf_{\sssig X}(x)\,dx=\int_{x\in\mathcal{R}_{\sssig X}}xf_{\sssig X}(x)\,dx
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mu_{\sssig X}&=\mathbb{E}(X)=\int_{-\infty}^{\infty}xf_{\sssig X}(x)\,dx\\[0.45em]
&=\int_{x\in\mathcal{R}_{\sssig X}}xf_{\sssig X}(x)\,dx
\end{aligned}
$$

</div>

為 $X$ 的**期望值**。

</div>

期望值有一些地方需要注意:

(1) 期望值存在的等價條件是 $\mathbb{E}(\lvert X\rvert)$ 為有限 (或存在)，這個性質被稱作**絕對收斂 <span lang="en">(absolute convergent)</span>**。
{: .topic-paren-item}

(2) 期望值事實上是一種**加權平均**，可以理解為一個隨機變數的**分配中心**或是**聚集中心**。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

若以離散型作為例子，則 $x$ 的機率 $p_{\sssig X}(x)$ 可以視為是 $x$ 的權重，則上述定義即成為加權平均。

由質點的概念理解之，則 $x$ 可類比為位置，而 $p_{\sssig X}(x)$ 則類比為 $x$ 的質量，故進行加權平均後得到的期望值可以類比為物理學的「質心」。

而若是連續型，則可將積分與離散型的加總進行類比，同樣可以視為是一種加權平均。

</div>

(3) 由於期望值為隨機變數 $X$ 的平均，故期望值有時候也被稱為 $X$ 的**平均數 (mean)**。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

期望值是一個隨機變數的母數，故其必定是一個常數 (不具備隨機性)，但這個用字與後面的章節會介紹的統計量 (具有隨機性)**樣本平均 (sample mean)** 卻相當類似，故若要使用平均稱呼期望值，我們通常會以母體平均指稱之，而以樣本平均指稱樣本的平均數。

</div>

(4) 期望值 $\mu_{\sssig X}$ 是使得 $\mathbb{E}\bigl[(X-a)^{2}\bigr]$ 達到最小的實數 $a$。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

在稍後[**變異數 <span lang="en">(variance)</span>**](/lecture-notes/variance/#def-variance) 的小節我們可以知道，前述的這種期望值是衡量 $X$ 與 $a$ 這個位置的平均離散程度，然而由於期望值是一個隨機變數的**聚集中心**，故直觀意義上來說，**平均而言所有 $X$ 與期望值 $\mu_{\sssig X}$ 以平方衡量的離散程度是最小的**。

</div>

<div id="ex-weekly-accidents" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.15</div>

<div lang="en" markdown="1">
Suppose that $X$ denotes the number of accidents occurring in Ankang City in a week, and that the probability distribution of the number of accidents is given in the following table.

| $x$ | $3$ | $4$ | $5$ | $6$ |
|:---:|:---:|:---:|:---:|:---:|
| $\mathbb{P}(X=x)$ | $0.2$ | $0.3$ | $0.3$ | $0.2$ |
{: .topic-table--matrix}

<ol class="topic-list-paren">
  <li>Find the expected value of this distribution.</li>
</ol>
</div>

$X$ 之期望值為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\sum_{x=3}^{6}x\,\mathbb{P}(X=x)\\[0.45em]
&=3\times0.2+4\times0.3+5\times0.3+6\times0.2\\[0.45em]
&=4.5
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\sum_{x=3}^{6}x\,\mathbb{P}(X=x)\\[0.45em]
&=3\times0.2+4\times0.3\\[0.2em]
&\qquad\quad+5\times0.3+6\times0.2\\[0.45em]
&=4.5
\end{aligned}
$$

</div>

</div>

<div id="ex-geometric-expectation" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.3 <span lang="en">(Continued)</span></div>

<div lang="en" markdown="1">
Suppose that a random variable $X$ has probability mass function

$$
p_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
\left(\dfrac{1}{2}\right)^{x}, & x=1,2,\ldots\\[0.7em]
0, & \text{otherwise}
\end{array}
\right.
$$

<ol class="topic-list-paren topic-list-paren--start-4">
  <li>Evaluate the mean of $X$.</li>
</ol>
</div>

(4)
{: .topic-paren-item}

**[ 法一 ]**

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(X)=\sum_{x=1}^{\infty}x\,p_{\sssig X}(x)=\sum_{x=1}^{\infty}x\left(\frac{1}{2}\right)^{x}=1\cdot\left(\frac{1}{2}\right)^{1}+2\cdot\left(\frac{1}{2}\right)^{2}+\cdots
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\sum_{x=1}^{\infty}x\,p_{\sssig X}(x)=\sum_{x=1}^{\infty}x\left(\frac{1}{2}\right)^{x}\\[0.45em]
&=1\cdot\left(\frac{1}{2}\right)^{1}+2\cdot\left(\frac{1}{2}\right)^{2}+\cdots
\end{aligned}
$$

</div>

又

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\frac{1}{2}\,\mathbb{E}(X)=1\cdot\left(\frac{1}{2}\right)^{2}+2\cdot\left(\frac{1}{2}\right)^{3}+\cdots
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\frac{1}{2}\,\mathbb{E}(X)&=1\cdot\left(\frac{1}{2}\right)^{2}+2\cdot\left(\frac{1}{2}\right)^{3}+\cdots
\end{aligned}
$$

</div>

則可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\frac{1}{2}\,\mathbb{E}(X)&=\mathbb{E}(X)-\frac{1}{2}\,\mathbb{E}(X)\\[0.45em]
&=1\cdot\left(\frac{1}{2}\right)^{1}+(2-1)\cdot\left(\frac{1}{2}\right)^{2}+(3-2)\cdot\left(\frac{1}{2}\right)^{3}+\cdots\\[0.45em]
&=\left(\frac{1}{2}\right)^{1}+\left(\frac{1}{2}\right)^{2}+\left(\frac{1}{2}\right)^{3}+\cdots=\frac{\frac{1}{2}}{1-\frac{1}{2}}=1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\frac{1}{2}\,&\mathbb{E}(X)=\mathbb{E}(X)-\frac{1}{2}\,\mathbb{E}(X)\\[0.45em]
&=1\cdot\left(\frac{1}{2}\right)^{1}+(2-1)\cdot\left(\frac{1}{2}\right)^{2}\\[0.2em]
&\qquad\qquad+(3-2)\cdot\left(\frac{1}{2}\right)^{3}+\cdots\\[0.45em]
&=\left(\frac{1}{2}\right)^{1}+\left(\frac{1}{2}\right)^{2}+\left(\frac{1}{2}\right)^{3}+\cdots\\[0.45em]
&=\frac{\frac{1}{2}}{1-\frac{1}{2}}=1
\end{aligned}
$$

</div>

故

$$
\mathbb{E}(X)=2
$$

**[ 法二 ]**

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\sum_{x=1}^{\infty}x\left(\frac{1}{2}\right)^{x}=\frac{1}{2}\sum_{x=1}^{\infty}x\left(\frac{1}{2}\right)^{x-1}
=\frac{1}{2}\sum_{x=1}^{\infty}\left.\frac{d}{dq}q^{x}\right\rvert_{q=\frac{1}{2}}\\[0.45em]
&=\frac{1}{2}\left.\frac{d}{dq}\left(\sum_{x=1}^{\infty}q^{x}\right)\right\rvert_{q=\frac{1}{2}}
=\frac{1}{2}\left.\frac{d}{dq}\left(\frac{q}{1-q}\right)\right\rvert_{q=\frac{1}{2}}\\[0.45em]
&=\frac{1}{2}\left.\frac{1}{(1-q)^{2}}\right\rvert_{q=\frac{1}{2}}=\frac{1}{2}\cdot\frac{1}{\left(1-\frac{1}{2}\right)^{2}}=2
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\sum_{x=1}^{\infty}x\left(\frac{1}{2}\right)^{x}\\[0.45em]
&=\frac{1}{2}\sum_{x=1}^{\infty}x\left(\frac{1}{2}\right)^{x-1}\\[0.45em]
&=\frac{1}{2}\sum_{x=1}^{\infty}\left.\frac{d}{dq}q^{x}\right\rvert_{q=\frac{1}{2}}\\[0.45em]
&=\frac{1}{2}\left.\frac{d}{dq}\left(\sum_{x=1}^{\infty}q^{x}\right)\right\rvert_{q=\frac{1}{2}}\\[0.45em]
&=\frac{1}{2}\left.\frac{d}{dq}\left(\frac{q}{1-q}\right)\right\rvert_{q=\frac{1}{2}}\\[0.45em]
&=\frac{1}{2}\left.\frac{1}{(1-q)^{2}}\right\rvert_{q=\frac{1}{2}}\\[0.45em]
&=\frac{1}{2}\cdot\frac{1}{\left(1-\frac{1}{2}\right)^{2}}=2
\end{aligned}
$$

</div>

**[ 法三 ]**

由於 $X$ 為一非負整數隨機變數，故可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X\geqslant x)=\sum_{k=x}^{\infty}\mathbb{P}(X=k)=\sum_{k=x}^{\infty}\left(\frac{1}{2}\right)^{k}=\frac{\left(\frac{1}{2}\right)^{x}}{1-\frac{1}{2}}=\left(\frac{1}{2}\right)^{x-1}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X\geqslant x)&=\sum_{k=x}^{\infty}\mathbb{P}(X=k)\\[0.45em]
&=\sum_{k=x}^{\infty}\left(\frac{1}{2}\right)^{k}\\[0.45em]
&=\frac{\left(\frac{1}{2}\right)^{x}}{1-\frac{1}{2}}\\[0.45em]
&=\left(\frac{1}{2}\right)^{x-1}
\end{aligned}
$$

</div>

則由 [Theorem 2.8](#thm-expectation-tail-sum) 可知期望值為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(X)=\sum_{x=1}^{\infty}\mathbb{P}(X\geqslant x)=\sum_{x=1}^{\infty}\left(\frac{1}{2}\right)^{x-1}=\frac{1}{1-\frac{1}{2}}=2
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\sum_{x=1}^{\infty}\mathbb{P}(X\geqslant x)\\[0.45em]
&=\sum_{x=1}^{\infty}\left(\frac{1}{2}\right)^{x-1}\\[0.45em]
&=\frac{1}{1-\frac{1}{2}}=2
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

上述法一是高中數學常見的級數求和手法，將其轉為無窮等比級數進行計算；而法二則是運用了微分與加總，在對象不互相為函數的情況下可以交換的性質，巧妙地將這個級數轉回等比級數計算。事實上，這兩個做法本質上是一樣的做法，微積分造詣相當不錯的讀者，不妨思考看看為何。

此外，本題的分配事實上是幾何分配 <span lang="en">(geometric distribution)</span>，而調換加總與微分的順序，正是幾何分配求取期望值的一個重要技巧，我們在稍後的章節詳述。

</div>

<div id="ex-quadratic-density-expectation" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.6 <span lang="en">(Continued)</span></div>

<div lang="en" markdown="1">
Suppose that the random variable $X$ has the probability density function

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{3}{8}(4x-2x^{2}), & 0<x<2\\[0.7em]
0, & \text{otherwise}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
f_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{3}{8}(4x-2x^{2}), & 0<x<2\\[0.6em]
0, & \text{otherwise}
\end{array}
\right.
$$

</div>

<ol class="topic-list-paren topic-list-paren--start-3">
  <li>Find the expected value of $X$.</li>
</ol>
</div>

(3) $X$ 之期望值為
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\int_{-\infty}^{\infty}xf_{\sssig X}(x)\,dx=\int_{0}^{2}x\cdot\frac{3}{8}(4x-2x^{2})\,dx\\[0.45em]
&=\left[\frac{1}{2}x^{3}-\frac{3}{16}x^{4}\right]_{0}^{2}=1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\int_{-\infty}^{\infty}xf_{\sssig X}(x)\,dx\\[0.45em]
&=\int_{0}^{2}x\cdot\frac{3}{8}(4x-2x^{2})\,dx\\[0.45em]
&=\left[\frac{1}{2}x^{3}-\frac{3}{16}x^{4}\right]_{0}^{2}=1
\end{aligned}
$$

</div>

</div>

<div id="ex-component-lifetime-expectation" class="topic-box topic-box--example" markdown="1">
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

<ol class="topic-list-paren topic-list-paren--start-2">
  <li>Find the mean of $Y$.</li>
</ol>
</div>

(2) 由[第 (1) 小題](/lecture-notes/mixed-random-variables/#ex-component-lifetime)已知 $Y$ 為混合型隨機變數，其分配為
{: .topic-paren-item}

$$
f_{\sssig Y}(y)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{1}{4}, & y=0\\[0.6em]
\dfrac{3}{4}e^{-y}, & y>0\\[0.6em]
0, & \text{elsewhere}
\end{array}
\right.
$$

則其壽命 $Y$ 的期望值為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(Y)&=0\times\frac{1}{4}+\int_{0}^{\infty}y\,\frac{3}{4}e^{-y}\,dy=\frac{3}{4}\int_{0}^{\infty}y^{2-1}e^{-\frac{y}{1}}\,dy\\[0.45em]
&=\frac{3}{4}\times1^{2}\times\Gamma(2)=\frac{3}{4}\times(2-1)!=\frac{3}{4}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(Y)&=0\times\frac{1}{4}+\int_{0}^{\infty}y\,\frac{3}{4}e^{-y}\,dy\\[0.45em]
&=\frac{3}{4}\int_{0}^{\infty}y^{2-1}e^{-\frac{y}{1}}\,dy\\[0.45em]
&=\frac{3}{4}\times1^{2}\times\Gamma(2)\\[0.45em]
&=\frac{3}{4}\times(2-1)!=\frac{3}{4}
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

[混合型隨機變數](/lecture-notes/mixed-random-variables/)的期望值計算，便是很直覺地將離散部分與連續部分分開計算即可；但事實上，混合型隨機變數的期望值，亦會是離散部分的隨機變數期望值 <span class="text-nowrap">$\mu_{\sssig d}$，</span>與連續部分的隨機變數期望值 $\mu_{\sssig c}$ 之加權平均，權重正好是 $\alpha$ 與 $1-\alpha$，此即

$$
\mu_{\sssig X}=\alpha\,\mu_{\sssig d}+(1-\alpha)\,\mu_{\sssig c}
$$

</div>

<div id="thm-expectation-tail-sum" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.8 (非負隨機變數的尾機率表示, tail-sum formula for a non-negative random variable)</div>

若 $X$ 為非負整數隨機變數，則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(X)=\sum_{x=0}^{\infty}\mathbb{P}(X>x)=\sum_{x=1}^{\infty}\mathbb{P}(X\geqslant x)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\sum_{x=0}^{\infty}\mathbb{P}(X>x)\\[0.45em]
&=\sum_{x=1}^{\infty}\mathbb{P}(X\geqslant x)
\end{aligned}
$$

</div>

若 $X$ 為非負連續隨機變數，則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(X)=\int_{0}^{\infty}\mathbb{P}(X>x)\,dx=\int_{0}^{\infty}\bigl[1-F_{\sssig X}(x)\bigr]\,dx
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\int_{0}^{\infty}\mathbb{P}(X>x)\,dx\\[0.45em]
&=\int_{0}^{\infty}\bigl[1-F_{\sssig X}(x)\bigr]\,dx
\end{aligned}
$$

</div>

</div>

<div class="topic-proof" markdown="1">
**Proof.**

(1) 由於 $X$ 為一非負整數隨機變數，故可知 $\mathbb{P}(X\geqslant x)=\sum_{k=x}^{\infty}\mathbb{P}(X=k)$ 成立，則原式右側為
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\sum_{x=1}^{\infty}\sum_{k=x}^{\infty}\mathbb{P}(X=k)&=\sum_{k=1}^{\infty}\sum_{x=1}^{k}\mathbb{P}(X=k)=\sum_{k=1}^{\infty}k\,\mathbb{P}(X=k)\\[0.45em]
&=\sum_{x=1}^{\infty}x\,\mathbb{P}(X=x)=\mathbb{E}(X)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&~~~~~\sum_{x=1}^{\infty}\sum_{k=x}^{\infty}\mathbb{P}(X=k)\\[0.45em]
&=\sum_{k=1}^{\infty}\sum_{x=1}^{k}\mathbb{P}(X=k)\\[0.45em]
&=\sum_{k=1}^{\infty}k\,\mathbb{P}(X=k)\\[0.45em]
&=\sum_{x=1}^{\infty}x\,\mathbb{P}(X=x)\\[0.45em]
&=\mathbb{E}(X)
\end{aligned}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

上式的加總順序交換，會導致**下標 (index)** 的範圍隨之更動。原本的加總方式如下。

$$
\sum_{x=1}^{\infty}\,\sum_{k=x}^{\infty}\,\mathbb{P}(X=k)
$$

我們是先將 $\mathbb{P}(X=k)$ 沿著 $k$ 軸，從 $k=x$ 開始加總至 $\infty$，再沿著 $x$ 軸，從 $1$ 開始加總至 $\infty$，從圖形上而言，可以[如下](#fig-double-sum-original-order)理解。

<figure id="fig-double-sum-original-order" class="topic-figure topic-figure--wide">
  <img src="/images/lecture-notes/double-sum-original-order.svg" alt="雙重加總的示意圖。橫軸為 k、縱軸為 x，圖中的黑點是滿足 k 大於等於 x 的整數數對，斜的虛線 k 等於 x 是它們的邊界。每一列都有一支由 k 等於 x 出發向右延伸的實線箭頭，表示先沿 k 軸加總；圖形右側另有一支向上的虛線箭頭，表示再沿 x 軸由 1 加總至無窮大。">
  <figcaption><span class="topic-figure__label">Fig. 2.9.</span> 雙重加總 $\sum_{x=1}^{\infty}\sum_{k=x}^{\infty}\mathbb{P}(X=k)$ 的加總順序: 先固定 $x$，沿 $k$ 軸由 $k=x$ 加總至 $\infty$，再沿 $x$ 軸由 $1$ 加總至 $\infty$。圖中的實線箭頭是內層的 $\sum_{k=x}^{\infty}$，虛線箭頭是外層的 $\sum_{x=1}^{\infty}$。</figcaption>
</figure>

[上圖](#fig-double-sum-original-order)中的黑點部分，代表在該雙重加總中，需要被加總的 $(k,x)$ 數對，而每一個點對應的機率 $\mathbb{P}(X=k)$ 都只與其 $k$ 座標有關。如果將加總的變數順序調換之後，會變成如下。

$$
\sum_{k=1}^{\infty}\,\sum_{x=1}^{k}\,\mathbb{P}(X=k)
$$

其加總順序則對應到[下圖](#fig-double-sum-swapped-order)，沿 $x$ 軸先開始加總，從 $x=1$ 到 $x=k$，再來才沿 $k$ 軸進行加總，從 $k=1$ 到 $\infty$。

<figure id="fig-double-sum-swapped-order" class="topic-figure topic-figure--wide">
  <img src="/images/lecture-notes/double-sum-swapped-order.svg" alt="換序後的雙重加總示意圖。橫軸為 k、縱軸為 x，黑點與前一張圖相同，斜的虛線 x 等於 k 是它們的邊界。每一行都有一支由 x 等於 1 向上延伸至 x 等於 k 的實線箭頭，表示先沿 x 軸加總；圖形下方另有一支向右的虛線箭頭，表示再沿 k 軸由 1 加總至無窮大。">
  <figcaption><span class="topic-figure__label">Fig. 2.10.</span> 換序後的加總 $\sum_{k=1}^{\infty}\sum_{x=1}^{k}\mathbb{P}(X=k)$: 先固定 $k$，沿 $x$ 軸由 $1$ 加總至 $k$，再沿 $k$ 軸由 $1$ 加總至 $\infty$。圖中的實線箭頭是內層的 $\sum_{x=1}^{k}$，虛線箭頭是外層的 <span class="text-nowrap">$\sum_{k=1}^{\infty}$。</span>所加總的黑點與 <a href="#fig-double-sum-original-order">Fig. 2.9</a> 完全相同。</figcaption>
</figure>

這種調換加總順序的技巧，也能對應到連續型的積分，其範圍的轉換原理是相同的，見下列證明。

</div>

(2) 由於 $X$ 為一非負連續隨機變數，故可知 $\mathbb{P}(X>x)=\int_{x}^{\infty}f_{\sssig X}(t)\,dt$，則原式右側為
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\int_{0}^{\infty}\int_{x}^{\infty}f_{\sssig X}(t)\,dt\,dx&=\int_{0}^{\infty}\int_{0}^{t}f_{\sssig X}(t)\,dx\,dt=\int_{0}^{\infty}\left(\int_{0}^{t}1\,dx\right)f_{\sssig X}(t)\,dt\\[0.45em]
&=\int_{0}^{\infty}t\,f_{\sssig X}(t)\,dt=\int_{0}^{\infty}x\,f_{\sssig X}(x)\,dx=\mathbb{E}(X)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\int_{0}^{\infty}&\int_{x}^{\infty}f_{\sssig X}(t)\,dt\,dx\\[0.45em]
&=\int_{0}^{\infty}\int_{0}^{t}f_{\sssig X}(t)\,dx\,dt\\[0.45em]
&=\int_{0}^{\infty}\left(\int_{0}^{t}1\,dx\right)f_{\sssig X}(t)\,dt\\[0.45em]
&=\int_{0}^{\infty}t\,f_{\sssig X}(t)\,dt\\[0.45em]
&=\int_{0}^{\infty}x\,f_{\sssig X}(x)\,dx\\[0.45em]
&=\mathbb{E}(X)
\end{aligned}
$$

</div>

又由 $\mathbb{P}(X>x)=1-\mathbb{P}(X\leqslant x)=\;$<wbr>$1-F_{\sssig X}(x)$，原式得證。 <span class="topic-qed">$\square$</span>
{: .topic-paren-cont}
</div>

## 本篇小結

[Definition 2.6](#def-expectation) 以絕對收斂為前提，分別對離散型與連續型給出期望值 $\mu_{\sssig X}=\mathbb{E}(X)$。離散型是以 $p_{\sssig X}(x)$ 為權重對各個取值加總，連續型則是以 $f_{\sssig X}(x)$ 為權重對取值積分。兩者都是加權平均，也就是一個分配的聚集中心；在質點的類比之下，取值是位置、機率是質量，期望值就是質心。期望值也是使 $\mathbb{E}\bigl[(X-a)^{2}\bigr]$ 達到最小的實數 $a$，故亦被稱為 $X$ 的平均數，指稱時以母體平均與樣本平均區別。

四個例題示範了不同型態的計算。[Example 2.15](#ex-weekly-accidents) 是有限個質點的直接加權，[Example 2.3 <span lang="en">(Continued)</span>](#ex-geometric-expectation) 是無窮級數，並列出級數錯位相減、微分與加總交換，以及尾機率三種做法，[Example 2.6 <span lang="en">(Continued)</span>](#ex-quadratic-density-expectation) 是連續型的積分，[Example 2.14 <span lang="en">(Continued)</span>](#ex-component-lifetime-expectation) 則是混合型，把離散部分與連續部分分開計算，其結果亦為 $\mu_{\sssig d}$ 與 $\mu_{\sssig c}$ 以 $\alpha$ 與 $1-\alpha$ 為權重的加權平均。

[Theorem 2.8](#thm-expectation-tail-sum) 給出非負隨機變數期望值的另一種表示，離散型為尾機率 $\mathbb{P}(X\geqslant x)$ 的加總，連續型為 $1-F_{\sssig X}(x)$ 的積分。它的證明是把雙重加總與二重積分的順序交換，[Fig. 2.9](#fig-double-sum-original-order) 與 [Fig. 2.10](#fig-double-sum-swapped-order) 畫出了交換前後所加總的同一組數對。[下一篇](/lecture-notes/properties-of-expectation/)討論隨機變數之函數的期望值，以及期望值本身的性質。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Joseph K. Blitzstein and Jessica Hwang. 2019. *Introduction to Probability*. 2nd ed. Chapman and Hall/CRC.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
