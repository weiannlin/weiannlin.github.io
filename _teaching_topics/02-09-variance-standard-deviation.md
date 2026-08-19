---
title: "變異數的求算與標準差"
subtitle: "Computing the Variance and the Standard Deviation"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 9
order: 209
permalink: /teaching-topics/variance-standard-deviation/
date: 2026-08-06
published: true
excerpt: "三道例題示範變異數的求算: 線性關係下直接套用平方伸縮性，分段定義的密度以分段積分求出期望值與平方期望值，混合型則把離散部分與連續部分分開計算。期望值另有一項重要特性: 在所有實數之中，期望值使平方離差的期望值達到最小。若只知道期望值與變異數，$g(X)$ 的期望值與變異數仍可由泰勒級數展開求得近似值。標準差是變異數開根號後的量數，單位與期望值相同，性質由變異數承接而來，只是平方伸縮性在標準差中改為絕對伸縮性。"
---

[上一篇](/teaching-topics/variance/)給出[變異數](/teaching-topics/variance/#def-variance)的定義、計算公式、函數變異數與兩項性質，並以兩道例題示範計算。本篇接著看三道例題。一道是[隨機變數](/teaching-topics/random-variables-and-pmf/#def-random-variable)之間的線性關係，一道的密度函數分段定義，一道則是混合型隨機變數。

三道例題之後，我們回頭補上[期望值](/teaching-topics/expectation/#def-expectation)的一項重要特性。在所有的實數之中，期望值是使平方離差的期望值達到最小的那一個。接著討論在只知道期望值與變異數的情形下，如何以泰勒級數展開求出 $g(X)$ 的期望值與變異數的近似值。最後介紹標準差。它是變異數開根號之後的量數，單位與期望值相同，性質可以直接由變異數的性質承接而來。

<div id="ex-income-linear-variance" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.19</div>

<div lang="en" markdown="1">
Suppose that $X$ denotes the number of customer visits recorded in a study of visits and income, and that the variance of $X$ is $0.81$. The income associated with the number of visits is $W=449+0.25X$.

<ol class="topic-list-paren">
  <li>Find the variance of the income $W$.</li>
</ol>
</div>

(1) 由 [Theorem 2.13](/teaching-topics/variance/#thm-variance-properties) 的平移不變性與平方伸縮性可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(W)&=\mathrm{Var}(449+0.25X)=0.25^{2}\times\mathrm{Var}(X)\\[0.45em]
&=0.0625\times0.81=0.050625
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(W)&=\mathrm{Var}(449+0.25X)\\[0.45em]
&=0.25^{2}\times\mathrm{Var}(X)\\[0.45em]
&=0.0625\times0.81=0.050625
\end{aligned}
$$

</div>

</div>

<div id="ex-piecewise-density-variance" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.20</div>

令隨機變數 $X$ 的 pdf 為

$$
f_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & x<0\\[0.4em]
x, & 0\leqslant x<1\\[0.4em]
\dfrac{1}{2}, & 1\leqslant x<2\\[0.6em]
0, & x\geqslant2
\end{array}
\right.
$$

求 $X$ 之期望值與變異數。

先算出期望值為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\int_{-\infty}^{\infty}x\,f_{\sssig X}(x)\,dx=\int_{0}^{1}x\cdot x\,dx+\int_{1}^{2}x\cdot\frac{1}{\,2\,}\,dx\\[0.45em]
&=\left[\frac{x^{3}}{3}\right]_{0}^{1}+\left[\frac{x^{2}}{4}\right]_{1}^{2}=\left[\frac{1^{3}}{3}-\frac{0^{3}}{3}\right]+\left[\frac{2^{2}}{4}-\frac{1^{2}}{4}\right]=\frac{\,13\,}{12}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}&(X)=\int_{-\infty}^{\infty}x\,f_{\sssig X}(x)\,dx\\[0.45em]
&=\int_{0}^{1}x\cdot x\,dx+\int_{1}^{2}x\cdot\frac{1}{\,2\,}\,dx\\[0.45em]
&=\left[\frac{x^{3}}{3}\right]_{0}^{1}+\left[\frac{x^{2}}{4}\right]_{1}^{2}\\[0.45em]
&=\left[\frac{1^{3}}{3}-\frac{0^{3}}{3}\right]+\left[\frac{2^{2}}{4}-\frac{1^{2}}{4}\right]\\[0.45em]
&=\frac{\,13\,}{12}
\end{aligned}
$$

</div>

再算出平方期望值為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl(X^{2}\bigr)&=\int_{-\infty}^{\infty}x^{2}\,f_{\sssig X}(x)\,dx=\int_{0}^{1}x^{2}\cdot x\,dx+\int_{1}^{2}x^{2}\cdot\frac{1}{\,2\,}\,dx\\[0.45em]
&=\left[\frac{x^{4}}{4}\right]_{0}^{1}+\left[\frac{x^{3}}{6}\right]_{1}^{2}=\left[\frac{1^{4}}{4}-\frac{0^{4}}{4}\right]+\left[\frac{2^{3}}{6}-\frac{1^{3}}{6}\right]=\frac{\,17\,}{12}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}&\bigl(X^{2}\bigr)=\int_{-\infty}^{\infty}x^{2}\,f_{\sssig X}(x)\,dx\\[0.45em]
&=\int_{0}^{1}x^{2}\cdot x\,dx+\int_{1}^{2}x^{2}\cdot\frac{1}{\,2\,}\,dx\\[0.45em]
&=\left[\frac{x^{4}}{4}\right]_{0}^{1}+\left[\frac{x^{3}}{6}\right]_{1}^{2}\\[0.45em]
&=\left[\frac{1^{4}}{4}-\frac{0^{4}}{4}\right]+\left[\frac{2^{3}}{6}-\frac{1^{3}}{6}\right]\\[0.45em]
&=\frac{\,17\,}{12}
\end{aligned}
$$

</div>

故所求的變異數為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}(X)=\mathbb{E}\bigl(X^{2}\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}=\frac{\,17\,}{12}-\left(\frac{13}{12}\right)^{2}=\frac{\,35\,}{144}\fallingdotseq0.2431
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(X)&=\mathbb{E}\bigl(X^{2}\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}\\[0.45em]
&=\frac{\,17\,}{12}-\left(\frac{13}{12}\right)^{2}\\[0.45em]
&=\frac{\,35\,}{144}\fallingdotseq0.2431
\end{aligned}
$$

</div>

</div>

<div id="ex-component-lifetime-variance" class="topic-box topic-box--example" markdown="1">
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

<ol class="topic-list-paren topic-list-paren--start-3">
  <li>Find the variance of $Y$.</li>
</ol>
</div>

(3) 由[第 (1) 小題](/teaching-topics/mixed-random-variables/#ex-component-lifetime)已知 $Y$ 為混合型隨機變數，其分配為
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

壽命 $Y$ 的平方期望值為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl(Y^{2}\bigr)&=0^{2}\times\frac{1}{4}+\int_{0}^{\infty}y^{2}\,\frac{3}{4}e^{-y}\,dy=\frac{3}{4}\int_{0}^{\infty}y^{3-1}e^{-\frac{y}{1}}\,dy\\[0.45em]
&=\frac{3}{4}\times1^{3}\times\Gamma(3)=\frac{3}{4}\times(3-1)!=\frac{3}{2}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl(Y^{2}\bigr)&=0^{2}\times\frac{1}{4}+\int_{0}^{\infty}y^{2}\,\frac{3}{4}e^{-y}\,dy\\[0.45em]
&=\frac{3}{4}\int_{0}^{\infty}y^{3-1}e^{-\frac{y}{1}}\,dy\\[0.45em]
&=\frac{3}{4}\times1^{3}\times\Gamma(3)\\[0.45em]
&=\frac{3}{4}\times(3-1)!=\frac{3}{2}
\end{aligned}
$$

</div>

故所求的變異數為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}(Y)=\mathbb{E}\bigl(Y^{2}\bigr)-\bigl[\mathbb{E}(Y)\bigr]^{2}=\frac{3}{2}-\left[\frac{3}{4}\right]^{2}=0.9375
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(Y)&=\mathbb{E}\bigl(Y^{2}\bigr)-\bigl[\mathbb{E}(Y)\bigr]^{2}\\[0.45em]
&=\frac{3}{2}-\left[\frac{3}{4}\right]^{2}=0.9375
\end{aligned}
$$

</div>

</div>

<div id="thm-mean-minimizes-squared-deviation" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.14 (期望值使平方離差的期望值最小, the mean minimizes mean squared deviation)</div>

若 $X$ 為一隨機變數，且 $\mathbb{E}(X^{2})<\infty$，並令

$$
g(a)=\mathbb{E}\bigl[(X-a)^{2}\bigr],\quad\forall\,a\in\mathbb{R}
$$

則 $X$ 的期望值 $\mu_{\sssig X}$ 是使得 $g(a)$ 達到最小值的 $a$，此即

$$
g(a)\geqslant g(\mu_{\sssig X}),\quad\forall\,a\in\mathbb{R}
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.**

把 $X-a$ 分解成 $(X-\mu_{\sssig X})+(\mu_{\sssig X}-a)$，再由 [Theorem 2.10](/teaching-topics/properties-of-expectation/#thm-expectation-linearity) 可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
g(a)&=\mathbb{E}\bigl[(X-a)^{2}\bigr]=\mathbb{E}\Bigl[\bigl[(X-\mu_{\sssig X})+(\mu_{\sssig X}-a)\bigr]^{2}\Bigr]\\[0.45em]
&=\mathbb{E}\bigl[(X-\mu_{\sssig X})^{2}+2(\mu_{\sssig X}-a)(X-\mu_{\sssig X})+(\mu_{\sssig X}-a)^{2}\bigr]\\[0.45em]
&=\mathbb{E}\bigl[(X-\mu_{\sssig X})^{2}\bigr]+2(\mu_{\sssig X}-a)\,\mathbb{E}\bigl(X-\mu_{\sssig X}\bigr)+(\mu_{\sssig X}-a)^{2}\\[0.45em]
&=g(\mu_{\sssig X})+(\mu_{\sssig X}-a)^{2}\geqslant g(\mu_{\sssig X})
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
g(a)&=\mathbb{E}\bigl[(X-a)^{2}\bigr]\\[0.45em]
&=\mathbb{E}\Bigl[\bigl[(X-\mu_{\sssig X})+(\mu_{\sssig X}-a)\bigr]^{2}\Bigr]\\[0.45em]
&=\mathbb{E}\bigl[(X-\mu_{\sssig X})^{2}\\[0.2em]
&\qquad\qquad+2(\mu_{\sssig X}-a)(X-\mu_{\sssig X})\\[0.2em]
&\qquad\qquad\qquad+(\mu_{\sssig X}-a)^{2}\bigr]\\[0.45em]
&=\mathbb{E}\bigl[(X-\mu_{\sssig X})^{2}\bigr]\\[0.2em]
&\qquad\qquad+2(\mu_{\sssig X}-a)\,\mathbb{E}\bigl(X-\mu_{\sssig X}\bigr)\\[0.2em]
&\qquad\qquad\qquad+(\mu_{\sssig X}-a)^{2}\\[0.45em]
&=g(\mu_{\sssig X})+(\mu_{\sssig X}-a)^{2}\\[0.45em]
&\geqslant g(\mu_{\sssig X})
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個性質在 [Definition 2.6](/teaching-topics/expectation/#def-expectation) 之後的說明中就已經提過，是期望值的一個重要特性。由於期望值可以簡單視為分配的中心，故任意的位置與期望值所構成的離差 <span lang="en">(deviation)</span> 平方的平均，將是最小的。

這個定理的證明過程使用一個技巧，將 $X-a$ 分解為互相正交的兩個部分，分別是 $X-\mu_{\sssig X}$ 與 $\mu_{\sssig X}-a$，我們則借其意，將此方法稱為**正交分解 <span lang="en">(orthogonal decomposition)</span>**，在往後的推導過程中，我們將經常使用這個技巧。

</div>

<div id="thm-taylor-approximation" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.15 (期望值與變異數的泰勒近似, Taylor approximation of the mean and the variance)</div>

若 $X$ 為一隨機變數，且 $\mu_{\sssig X}=\mathbb{E}(X)$、$\sigma_{\sssig X}^{2}=\mathrm{Var}(X)$ 皆為有限，$g(\cdot)$ 為一二階可微且可測之函數，則

<ol class="topic-list-paren topic-list-paren--math">
  <li>
  $$
  \mathbb{E}\bigl[g(X)\bigr]\fallingdotseq g(\mu_{\sssig X})+\frac{\,g^{\prime\prime}(\mu_{\sssig X})\,}{2}\,\sigma_{\sssig X}^{2}
  $$
  </li>
  <li>
  $$
  \mathrm{Var}\bigl[g(X)\bigr]\fallingdotseq\bigl[g^{\prime}(\mu_{\sssig X})\bigr]^{2}\sigma_{\sssig X}^{2}
  $$
  </li>
</ol>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

[Theorem 2.15](#thm-taylor-approximation) 的 (1) 用到 $g^{\prime\prime}(\mu_{\sssig X})$，(2) 用到 $g^{\prime}(\mu_{\sssig X})$，故前提要求 $g(\cdot)$ 二階可微；只有一階可微時，(1) 所寫的 $g^{\prime\prime}(\mu_{\sssig X})$ 並不存在。下面的推導把 $g(X)$ 在 $\mu_{\sssig X}$ 處展開到第三項，用到的也正是二階導數。至於捨去第三項之後的誤差有多大，須另加更強的條件才估計得出來，本篇只取近似值，不再細談。

</div>

許多時候我們並不知道隨機變數 $X$ 的機率函數 $f_{\sssig X}(x)$，只知道期望值 $\mu_{\sssig X}$ 與變異數 $\sigma_{\sssig X}^{2}$。在這種有限的資訊之下，我們仍然可以利用這些資訊，求出隨機變數 $X$ 之某函數轉換 $g(X)$ 的期望值與變異數近似值，步驟如下:

(1) 先將 $g(X)$ 在 $X=\mu_{\sssig X}$ 處作**泰勒級數 (Taylor series)** 展開，可得
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
g(X)&=g(\mu_{\sssig X})+\frac{g^{\prime}(\mu_{\sssig X})}{1!}(X-\mu_{\sssig X})^{1}+\frac{g^{\prime\prime}(\mu_{\sssig X})}{2!}(X-\mu_{\sssig X})^{2}+\cdots\\[0.45em]
&=g(\mu_{\sssig X})+g^{\prime}(\mu_{\sssig X})(X-\mu_{\sssig X})+\frac{1}{2}\,g^{\prime\prime}(\mu_{\sssig X})(X-\mu_{\sssig X})^{2}+\cdots
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
g(X)&=g(\mu_{\sssig X})+\frac{g^{\prime}(\mu_{\sssig X})}{1!}(X-\mu_{\sssig X})^{1}\\[0.45em]
&\qquad\qquad+\frac{g^{\prime\prime}(\mu_{\sssig X})}{2!}(X-\mu_{\sssig X})^{2}+\cdots\\[0.45em]
&=g(\mu_{\sssig X})+g^{\prime}(\mu_{\sssig X})(X-\mu_{\sssig X})\\[0.45em]
&\qquad\qquad+\frac{1}{2}\,g^{\prime\prime}(\mu_{\sssig X})(X-\mu_{\sssig X})^{2}+\cdots
\end{aligned}
$$

</div>

(2) 採用前三項取其期望值，可得
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[g(X)\bigr]&\fallingdotseq\mathbb{E}\bigl[g(\mu_{\sssig X})\bigr]+g^{\prime}(\mu_{\sssig X})\,\mathbb{E}\bigl(X-\mu_{\sssig X}\bigr)+\frac{1}{2}\,g^{\prime\prime}(\mu_{\sssig X})\,\mathbb{E}\bigl[(X-\mu_{\sssig X})^{2}\bigr]\\[0.45em]
&=g(\mu_{\sssig X})+\frac{1}{2}\,g^{\prime\prime}(\mu_{\sssig X})\,\sigma_{\sssig X}^{2}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[g(X)\bigr]&\fallingdotseq\mathbb{E}\bigl[g(\mu_{\sssig X})\bigr]+g^{\prime}(\mu_{\sssig X})\,\mathbb{E}\bigl(X-\mu_{\sssig X}\bigr)\\[0.45em]
&\qquad\qquad+\frac{1}{2}\,g^{\prime\prime}(\mu_{\sssig X})\,\mathbb{E}\bigl[(X-\mu_{\sssig X})^{2}\bigr]\\[0.45em]
&=g(\mu_{\sssig X})+\frac{1}{2}\,g^{\prime\prime}(\mu_{\sssig X})\,\sigma_{\sssig X}^{2}
\end{aligned}
$$

</div>

(3) 採用前兩項取其變異數，可得
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}\bigl[g(X)\bigr]\fallingdotseq\mathrm{Var}\bigl[g(\mu_{\sssig X})\bigr]+\bigl[g^{\prime}(\mu_{\sssig X})\bigr]^{2}\,\mathrm{Var}\bigl(X-\mu_{\sssig X}\bigr)=\bigl[g^{\prime}(\mu_{\sssig X})\bigr]^{2}\sigma_{\sssig X}^{2}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathrm{Var}\bigl[g(X)\bigr]\\[0.45em]
&~~\fallingdotseq\mathrm{Var}\bigl[g(\mu_{\sssig X})\bigr]+\bigl[g^{\prime}(\mu_{\sssig X})\bigr]^{2}\,\mathrm{Var}\bigl(X-\mu_{\sssig X}\bigr)\\[0.45em]
&~~=\bigl[g^{\prime}(\mu_{\sssig X})\bigr]^{2}\sigma_{\sssig X}^{2}
\end{aligned}
$$

</div>

<div id="ex-log-taylor-approximation" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.21</div>

<div lang="en" markdown="1">
Let $X$ be a positive-valued random variable. If $\mathbb{E}(X)=9$ and $\mathrm{Var}(X)=100$, please calculate the approximate mean and variance of $\ln X$.
</div>

令 $g(X)=\ln X$，則有

$$
g^{\prime}(X)=\frac{1}{X}\quad\text{且}\quad g^{\prime\prime}(X)=\frac{-1}{X^{2}}
$$

將 $\ln X$ 在 $X=\mu_{\sssig X}$ 處作泰勒級數展開至第三項，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\ln X\fallingdotseq\ln\mu_{\sssig X}+\frac{1}{\mu_{\sssig X}}(X-\mu_{\sssig X})+\frac{1}{2}\cdot\frac{-1}{\mu_{\sssig X}^{2}}(X-\mu_{\sssig X})^{2}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\ln X&\fallingdotseq\ln\mu_{\sssig X}+\frac{1}{\mu_{\sssig X}}(X-\mu_{\sssig X})\\[0.45em]
&\qquad+\frac{1}{2}\cdot\frac{-1}{\mu_{\sssig X}^{2}}(X-\mu_{\sssig X})^{2}
\end{aligned}
$$

</div>

故 $\ln X$ 的近似期望值為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(\ln X)\fallingdotseq\ln\mu_{\sssig X}+\frac{1}{2}\cdot\frac{-1}{\mu_{\sssig X}^{2}}\,\sigma_{\sssig X}^{2}=\ln9-\frac{100}{2\times9^{2}}\fallingdotseq1.580
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(\ln X)&\fallingdotseq\ln\mu_{\sssig X}+\frac{1}{2}\cdot\frac{-1}{\mu_{\sssig X}^{2}}\,\sigma_{\sssig X}^{2}\\[0.45em]
&=\ln9-\frac{100}{2\times9^{2}}\fallingdotseq1.580
\end{aligned}
$$

</div>

而其近似變異數為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}(\ln X)\fallingdotseq\frac{1}{\mu_{\sssig X}^{2}}\,\sigma_{\sssig X}^{2}=\frac{100}{9^{2}}\fallingdotseq1.235
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(\ln X)&\fallingdotseq\frac{1}{\mu_{\sssig X}^{2}}\,\sigma_{\sssig X}^{2}=\frac{100}{9^{2}}\fallingdotseq1.235
\end{aligned}
$$

</div>

</div>

## 標準差

<div id="def-standard-deviation" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.8 (標準差, standard deviation)</div>

若 $X$ 為一隨機變數，其變異數存在且為 $\sigma_{\sssig X}^{2}$，則

$$
\sigma_{\sssig X}=\operatorname{SD}(X)=\sqrt{\sigma_{\sssig X}^{2}}
$$

為其**標準差 <span lang="en">(standard deviation)</span>**。

</div>

標準差有一些地方需要注意:

(1) 標準差的單位是變異數的單位再開根號，與期望值是相同的。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

雖然標準差的計算多了一道程序，而且因為根號的緣故，較難以推論，但由於單位與原始單位相同，大多數的資料分析，在呈現上還是比較常用標準差。

</div>

(2) 我們稱其為母體標準差，避免與具有隨機性的樣本標準差搞混，後者的定義如下
{: .topic-paren-item}

$$
S=\sqrt{\frac{1}{\,n-1\,}\sum_{i=1}^{n}\bigl(X_{i}-\overline{X}\bigr)^{2}}
$$

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

與變異數相同，標準差是用來衡量一個隨機變數離散程度的母數，不具隨機性。

</div>

(3) $X$ 的函數標準差為
{: .topic-paren-item}

$$
\operatorname{SD}\bigl[g(X)\bigr]=\sqrt{\mathrm{Var}\bigl[g(X)\bigr]}
$$

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

事實上，不論如何，在計算標準差的時候，我們總是都先計算變異數，再行開根號。

</div>

<div id="thm-standard-deviation-properties" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.16 (標準差的性質, standard deviation properties)</div>

若 $X$ 為一隨機變數，$g(\cdot)$ 為一實值可測函數，$a, b$ 為二常數，則

<ol class="topic-list-paren topic-list-paren--math">
  <li>
  $$
  \operatorname{SD}(X)\geqslant0
  $$
  </li>
  <li>
  $$
  \operatorname{SD}\bigl[ag(X)+b\bigr]=\lvert a\rvert\,\operatorname{SD}\bigl[g(X)\bigr]
  $$
  </li>
</ol>

</div>

<div class="topic-proof" markdown="1">
**Proof.**

本處的證明我們承接 [Theorem 2.13](/teaching-topics/variance/#thm-variance-properties) 的變異數性質接續證明。

(1) 由變異數的非負性可知
{: .topic-paren-item}

$$
\mathrm{Var}(X)\geqslant0\qquad\therefore\,\operatorname{SD}(X)\geqslant0
$$

(2) 由 [Definition 2.8](#def-standard-deviation) 與變異數的平方伸縮性可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\operatorname{SD}\bigl[ag(X)+b\bigr]&=\sqrt{\mathrm{Var}\bigl[ag(X)+b\bigr]}=\sqrt{a^{2}\,\mathrm{Var}\bigl[g(X)\bigr]}\\[0.45em]
&=\lvert a\rvert\,\operatorname{SD}\bigl[g(X)\bigr]
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\operatorname{SD}\bigl[ag(X)+b\bigr]&=\sqrt{\mathrm{Var}\bigl[ag(X)+b\bigr]}\\[0.45em]
&=\sqrt{a^{2}\,\mathrm{Var}\bigl[g(X)\bigr]}\\[0.45em]
&=\lvert a\rvert\,\operatorname{SD}\bigl[g(X)\bigr]
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
{: .topic-paren-cont}
</div>

[Theorem 2.16](#thm-standard-deviation-properties) 中，(1) 是承接了變異數的**非負性**。(2) 的部分則是可以仿照 [Theorem 2.13](/teaching-topics/variance/#thm-variance-properties)，透過設定 $g(\cdot)$ 與 $a, b$ 的值，來得到許多有用的子性質，並將之與 [Theorem 2.13](/teaching-topics/variance/#thm-variance-properties) 比較，見以下設定。

(1) **[ 設定 $a=0$ ]**
{: .topic-paren-item}

$$
\operatorname{SD}(b)=0
$$

此即**常數不具變異性**。
{: .topic-paren-cont}

(2) **[ 設定 $a=1$，$g(X)=X$ ]**
{: .topic-paren-item}

$$
\operatorname{SD}(X+b)=\operatorname{SD}(X)
$$

此即**平移不變性**。
{: .topic-paren-cont}

(3) **[ 設定 $a\neq0$ 且 $g(X)=X$，$b=0$ ]**
{: .topic-paren-item}

$$
\operatorname{SD}(aX)=\lvert a\rvert\,\operatorname{SD}(X)
$$

此即**絕對伸縮性**。
{: .topic-paren-cont}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

變異數的**平方伸縮性**，在標準差中不復存在，取而代之的是**絕對伸縮性**。絕對伸縮性的直觀，在於標準差的單位與期望值相同，故若把原隨機變數乘上 $a$ 倍，則其單位尺度應隨之改變，然而因為標準差具有非負性，所以在標準差的單位尺度上，原先應該跟著伸縮 $a$ 倍的變異程度，則隨之改為 $\lvert a\rvert$ 倍。

</div>

<div id="ex-income-standard-deviation" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.19 <span lang="en">(Continued)</span></div>

<div lang="en" markdown="1">
Suppose that $X$ denotes the number of customer visits recorded in a study of visits and income, and that the variance of $X$ is $0.81$. The income associated with the number of visits is $W=449+0.25X$.

<ol class="topic-list-paren topic-list-paren--start-2">
  <li>Determine the standard deviation of the income $W$.</li>
</ol>
</div>

(2) 由[前一小題](#ex-income-linear-variance)已求得
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(W)&=\mathrm{Var}(449+0.25X)=0.25^{2}\times\mathrm{Var}(X)\\[0.45em]
&=0.0625\times0.81=0.050625
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(W)&=\mathrm{Var}(449+0.25X)\\[0.45em]
&=0.25^{2}\times\mathrm{Var}(X)\\[0.45em]
&=0.0625\times0.81=0.050625
\end{aligned}
$$

</div>

故由 [Theorem 2.16](#thm-standard-deviation-properties) 的絕對伸縮性可得
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\operatorname{SD}(W)=\sqrt{\mathrm{Var}(W)}=\lvert 0.25\rvert\times\sqrt{\mathrm{Var}(X)}=0.225
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\operatorname{SD}(W)&=\sqrt{\mathrm{Var}(W)}\\[0.45em]
&=\lvert 0.25\rvert\times\sqrt{\mathrm{Var}(X)}=0.225
\end{aligned}
$$

</div>

</div>

## 本篇小結

三道例題示範了變異數的三種求算情境。[Example 2.19](#ex-income-linear-variance) 只知道 $X$ 的變異數與 $W$ 對 $X$ 的線性關係，直接套用平移不變性與平方伸縮性即可；[Example 2.20](#ex-piecewise-density-variance) 的密度函數分段定義，期望值與平方期望值都要分段積分，再代入計算公式；[Example 2.14 <span lang="en">(Continued)</span>](#ex-component-lifetime-variance) 是混合型隨機變數，離散部分以質點加權、連續部分以密度積分，兩者分開計算之後合併。

[Theorem 2.14](#thm-mean-minimizes-squared-deviation) 指出，在所有的實數 $a$ 之中，$\mathbb{E}[(X-a)^{2}]$ 在 $a=\mu_{\sssig X}$ 處達到最小，證明的關鍵是把 $X-a$ 拆成 $(X-\mu_{\sssig X})+(\mu_{\sssig X}-a)$ 的正交分解。[Theorem 2.15](#thm-taylor-approximation) 則處理只知道 $\mu_{\sssig X}$ 與 $\sigma_{\sssig X}^{2}$ 的情形。把 $g(X)$ 在 $\mu_{\sssig X}$ 處作泰勒級數展開，取前三項求期望值、取前兩項求變異數，便得到 $g(X)$ 的期望值與變異數的近似值，[Example 2.21](#ex-log-taylor-approximation) 即以 $g(X)=\ln X$ 示範。

[Definition 2.8](#def-standard-deviation) 把標準差定義為變異數的平方根，它的單位與期望值相同，因此資料分析在呈現上多用標準差；指稱時同樣以母體標準差與樣本標準差 $S$ 區別，計算上則一律先求變異數再開根號。[Theorem 2.16](#thm-standard-deviation-properties) 的兩項性質都由 [Theorem 2.13](/teaching-topics/variance/#thm-variance-properties) 承接而來，其中的複合性質經設定後得到常數不具變異性、平移不變性與絕對伸縮性三個子性質，[Example 2.19 <span lang="en">(Continued)</span>](#ex-income-standard-deviation) 便是絕對伸縮性的直接應用。變異數的平方伸縮性在標準差中改為絕對伸縮性，是兩者性質唯一不同之處。[下一篇](/teaching-topics/mode/)離開離散程度的量數，改談指出分配位置的另一個量數，[眾數](/teaching-topics/mode/#def-mode)。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Morris H. DeGroot and Mark J. Schervish. 2012. *Probability and Statistics*. 4th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Alexander M. Mood, Franklin A. Graybill, and Duane C. Boes. 1974. *Introduction to the Theory of Statistics*. 3rd ed. McGraw-Hill.
