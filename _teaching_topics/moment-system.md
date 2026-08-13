---
title: "動差系統"
subtitle: "Moment System"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 13
order: 213
permalink: /teaching-topics/moment-system/
date: 2026-08-06
published: true
excerpt: "母體動差以一個基準點 $c$ 與一個階數 $r$ 界定為 $\\mathbb{E}[(X-c)^{r}]$: 取 $c=0$ 得到原動差 $\\mu_{r}^{\\prime}=\\mathbb{E}(X^{r})$，取 $c=\\mu_{X}$ 得到主動差 $\\mu_{r}=\\mathbb{E}[(X-\\mu_{X})^{r}]$，改取絕對值則得到絕對動差。一階原動差就是期望值，二階主動差就是變異數。兩種動差可以經由二項式定理互相表示，而高階絕對動差存在時，低階絕對動差同樣存在。"
---

[上一篇](/teaching-topics/quantiles/)介紹[分位數](/teaching-topics/quantiles/#def-quantile)，把[中位數](/teaching-topics/median/#def-median)的想法推廣到任意的比例。到這裡為止，[期望值](/teaching-topics/expectation/#def-expectation)、[變異數](/teaching-topics/variance/#def-variance)、[標準差](/teaching-topics/variance-standard-deviation/#def-standard-deviation)、[眾數](/teaching-topics/mode/#def-mode)、中位數與分位數都已經看過，它們各自描述一個分配的某一個面向，彼此之間看起來並沒有共同的來源。

動差系統與[動差母函數](/teaching-topics/moment-generating-functions/#def-mgf)這一節，就是把其中幾個量數收進同一套架構之下: 選定一個基準點 $c$ 與一個階數 $r$ 之後，$\mathbb{E}[(X-c)^{r}]$ 就是一個母體動差，期望值與變異數分別是取 $c=0$、$r=1$ 與 $c=\mu_{\sssig X}$、$r=2$ 的結果。本篇先給出母體動差的定義，並依基準點與函數形式分出原動差、主動差與絕對動差；接著介紹兩種動差互相轉換時所需要的二項式定理，並證明兩者確實可以互相表示；最後說明高階絕對動差存在時，低階絕對動差同樣存在。

<div id="def-population-moment" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.12 (母體動差, population moment)</div>

若 $X$ 為一[隨機變數](/teaching-topics/random-variables-and-pmf/#def-random-variable)，且 $\mathbb{E}(\lvert X-c\rvert^{r})<\infty$，則稱

$$
\mu_{\sssig r}=\mathbb{E}\bigl[(X-c)^{r}\bigr]
$$

為 $X$ **相對於 $c$ 的母體 $r$ 階動差 (population $r$-th moment about $c$)**。

</div>

在前述定義中，特別地，透過設定不同的 $c$ 以及函數形式，我們可以得到不同的動差如下:

(1) $\mu_{\sssig r}^{\prime}=\mathbb{E}(X^{r})$ 為 $X$ 的**母體 $r$ 階原動差 (population $r$-th raw moment)**。
{: .topic-paren-item}

(2) $\mu_{\sssig r}=\mathbb{E}\bigl[(X-\mu_{\sssig X})^{r}\bigr]$ 為 $X$ 的**母體 $r$ 階主動差 (population $r$-th central moment)**。
{: .topic-paren-item}

(3) $\mathbb{E}\bigl[\lvert X\rvert^{r}\bigr]$ 為 $X$ 的**母體 $r$ 階絕對動差 (population $r$-th absolute moment)**。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

[Definition 2.12](#def-population-moment) 的 $\mu_{\sssig r}$ 是相對於基準點 $c$ 的動差，要先取定 $c$ 才有確定的值；上面三項則各自取定了基準點與函數形式。其中原動差固定取 <span class="text-nowrap">$c=0$、</span>主動差固定取 $c=\mu_{\sssig X}$，故本篇其後出現的 $\mu_{\sssig r}$ 與 $\mu_{\sssig k}$ 一律指主動差，$\mu_{\sssig r}^{\prime}$ 與 $\mu_{\sssig k}^{\prime}$ 一律指原動差。

</div>

母體動差 <span lang="en">(population moment)</span> 有一些地方需要注意:

(1) 上述定義中可以發現，母體一階原動差即為期望值；而母體二階主動差即為變異數。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

原動差與主動差又分別被稱作**原點動差 (origin moment)** 和**中央動差 <span lang="en">(central moment)</span>**。事實上，我們可以在任何一點建立動差，但若不是 $0$ 或 $\mu_{\sssig X}$，則較不具有實務上的意義。

</div>

(2) 各階動差都包含描述母體分配的資訊，但我們目前僅知道前四階動差能夠「有實務意義地」描述一個分配。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

讀者應該記得，期望值與變異數，在稍早曾被用來分別描述分配的中央趨勢與分散趨勢，這也是動差的功能之一。

</div>

(3) 稍後我們會看到[**動差母函數 <span lang="en">(moment generating function, mgf)</span>**](/teaching-topics/moment-generating-functions/#def-mgf)，這是一個能夠生成任意 $r$ 階**原動差**的函數。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

實務上而言，主動差才是最重要的動差，但由於主動差與原動差之間可以彼此轉換，故原動差亦經常被使用。這些轉換的技巧，我們馬上將會談到，但在此之前，我們要先知道[**二項式定理 <span lang="en">(binomial theorem)</span>**](#thm-binomial)。

</div>

<div id="thm-binomial" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.18 (二項式定理, binomial theorem)</div>

$$
(a+b)^{n}=\sum_{x=0}^{n}\binom{n}{x}a^{x}\,b^{n-x}
$$

其中 $a, b\in\mathbb{R}$，$n\in\mathbb{N}$。

</div>

[二項式定理](#thm-binomial)在原動差與主動差的轉換間，扮演重要的角色，並且在往後的章節中提到**二項式分配 <span lang="en">(binomial distribution)</span>** 時，也將扮演核心的角色。

<div id="ex-discrete-uniform-binomial-moment" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.27</div>

<div lang="en" markdown="1">
Suppose that a random variable $X$ has the probability mass function

$$
p_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{1}{\,n\,}, & x=1, 2, \ldots, n\\[0.7em]
0, & \text{elsewhere}
\end{array}
\right.
$$

Show that

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\Biggl[kX^{k-1}+\binom{k}{2}X^{k-2}+\cdots+1\Biggr]=\frac{\,(n+1)^{k}-1\,}{n}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}\Biggl[kX^{k-1}+\binom{k}{2}X^{k-2}\\[0.2em]
&\qquad +\cdots+1\Biggr]=\frac{\,(n+1)^{k}-1\,}{n}
\end{aligned}
$$

</div>
</div>

由 [Theorem 2.18](#thm-binomial) 可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
kX^{k-1}+\binom{k}{2}X^{k-2}+\cdots+1&=\sum_{j=1}^{k}\binom{k}{j}1^{j}X^{k-j}\\[0.45em]
&=\sum_{j=0}^{k}\binom{k}{j}1^{j}X^{k-j}-X^{k}\\[0.45em]
&=(1+X)^{k}-X^{k}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&kX^{k-1}+\binom{k}{2}X^{k-2}+\cdots+1\\[0.45em]
&\quad =\sum_{j=1}^{k}\binom{k}{j}1^{j}X^{k-j}\\[0.45em]
&\quad =\sum_{j=0}^{k}\binom{k}{j}1^{j}X^{k-j}-X^{k}\\[0.45em]
&\quad =(1+X)^{k}-X^{k}
\end{aligned}
$$

</div>

則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\Biggl[kX^{k-1}+\binom{k}{2}X^{k-2}+\cdots+1\Biggr]&=\mathbb{E}\bigl[(1+X)^{k}-X^{k}\bigr]\\[0.45em]
&=\mathbb{E}\bigl[(1+X)^{k}\bigr]-\mathbb{E}(X^{k})
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}\Biggl[kX^{k-1}+\binom{k}{2}X^{k-2}\\[0.2em]
&\qquad +\cdots+1\Biggr]\\[0.45em]
&\quad =\mathbb{E}\bigl[(1+X)^{k}-X^{k}\bigr]\\[0.45em]
&\quad =\mathbb{E}\bigl[(1+X)^{k}\bigr]-\mathbb{E}(X^{k})
\end{aligned}
$$

</div>

又

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[(1+X)^{k}\bigr]&=\sum_{x=1}^{n}(1+x)^{k}\cdot\frac{1}{\,n\,}\\[0.45em]
&=\frac{1}{\,n\,}\bigl[2^{k}+3^{k}+\cdots+(1+n)^{k}\bigr]\\[0.7em]
\mathbb{E}(X^{k})&=\sum_{x=1}^{n}x^{k}\cdot\frac{1}{\,n\,}\\[0.45em]
&=\frac{1}{\,n\,}\bigl(1^{k}+2^{k}+\cdots+n^{k}\bigr)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}\bigl[(1+X)^{k}\bigr]=\sum_{x=1}^{n}(1+x)^{k}\cdot\frac{1}{\,n\,}\\[0.45em]
&\quad =\frac{1}{\,n\,}\bigl[2^{k}+3^{k}+\cdots\\[0.2em]
&\qquad +(1+n)^{k}\bigr]\\[0.7em]
&\mathbb{E}(X^{k})=\sum_{x=1}^{n}x^{k}\cdot\frac{1}{\,n\,}\\[0.45em]
&\quad =\frac{1}{\,n\,}\bigl(1^{k}+2^{k}+\cdots+n^{k}\bigr)
\end{aligned}
$$

</div>

故可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
&\mathbb{E}\Biggl[kX^{k-1}+\binom{k}{2}X^{k-2}+\cdots+1\Biggr]=\mathbb{E}\bigl[(1+X)^{k}\bigr]-\mathbb{E}(X^{k})\\[0.45em]
&\quad =\frac{1}{\,n\,}\bigl[2^{k}+3^{k}+\cdots+(1+n)^{k}\bigr]-\frac{1}{\,n\,}\bigl(1^{k}+2^{k}+\cdots+n^{k}\bigr)\\[0.45em]
&\quad =\frac{\,(n+1)^{k}-1\,}{n}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}\Biggl[kX^{k-1}+\binom{k}{2}X^{k-2}\\[0.2em]
&\qquad +\cdots+1\Biggr]\\[0.45em]
&\quad =\mathbb{E}\bigl[(1+X)^{k}\bigr]-\mathbb{E}(X^{k})\\[0.45em]
&\quad =\frac{1}{\,n\,}\bigl[2^{k}+3^{k}+\cdots\\[0.2em]
&\qquad +(1+n)^{k}\bigr]\\[0.2em]
&\qquad -\frac{1}{\,n\,}\bigl(1^{k}+2^{k}+\cdots+n^{k}\bigr)\\[0.45em]
&\quad =\frac{\,(n+1)^{k}-1\,}{n}
\end{aligned}
$$

</div>

原式得證。

</div>

<div id="thm-raw-central-moment-conversion" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.19 (原動差與主動差的互換, conversion between raw and central moments)</div>

令 $X$ 為一隨機變數，且 $r$ 階動差存在，則

<ol class="topic-list-paren">
  <li>
  $$
  \mu_{\sssig r}=\sum_{k=0}^{r}\binom{r}{k}\mu_{\sssig k}^{\prime}\,(-\mu_{\sssig X})^{r-k}
  $$
  </li>
  <li>
  $$
  \mu_{\sssig r}^{\prime}=\sum_{k=0}^{r}\binom{r}{k}\mu_{\sssig k}\,\mu_{\sssig X}^{r-k}
  $$
  </li>
</ol>

</div>

<div class="topic-proof" markdown="1">
**Proof.**

(1) 由 [Definition 2.12](#def-population-moment) 及 [Theorem 2.18](#thm-binomial) 可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mu_{\sssig r}&=\mathbb{E}\bigl[(X-\mu_{\sssig X})^{r}\bigr]=\mathbb{E}\Bigl[\bigl[X+(-\mu_{\sssig X})\bigr]^{r}\Bigr]\\[0.45em]
&=\mathbb{E}\left[\sum_{k=0}^{r}\binom{r}{k}X^{k}\,(-\mu_{\sssig X})^{r-k}\right]\\[0.45em]
&=\sum_{k=0}^{r}\binom{r}{k}\mathbb{E}(X^{k})\,(-\mu_{\sssig X})^{r-k}=\sum_{k=0}^{r}\binom{r}{k}\mu_{\sssig k}^{\prime}\,(-\mu_{\sssig X})^{r-k}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mu_{\sssig r}=\mathbb{E}\bigl[(X-\mu_{\sssig X})^{r}\bigr]\\[0.45em]
&\quad =\mathbb{E}\Bigl[\bigl[X+(-\mu_{\sssig X})\bigr]^{r}\Bigr]\\[0.45em]
&\quad =\mathbb{E}\left[\sum_{k=0}^{r}\binom{r}{k}X^{k}\,(-\mu_{\sssig X})^{r-k}\right]\\[0.45em]
&\quad =\sum_{k=0}^{r}\binom{r}{k}\mathbb{E}(X^{k})\,(-\mu_{\sssig X})^{r-k}\\[0.45em]
&\quad =\sum_{k=0}^{r}\binom{r}{k}\mu_{\sssig k}^{\prime}\,(-\mu_{\sssig X})^{r-k}
\end{aligned}
$$

</div>

(2) 由 (1) 同理可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mu_{\sssig r}^{\prime}&=\mathbb{E}(X^{r})=\mathbb{E}\Bigl[\bigl[(X-\mu_{\sssig X})+\mu_{\sssig X}\bigr]^{r}\Bigr]\\[0.45em]
&=\mathbb{E}\left[\sum_{k=0}^{r}\binom{r}{k}(X-\mu_{\sssig X})^{k}\,\mu_{\sssig X}^{r-k}\right]\\[0.45em]
&=\sum_{k=0}^{r}\binom{r}{k}\mathbb{E}\bigl[(X-\mu_{\sssig X})^{k}\bigr]\,\mu_{\sssig X}^{r-k}=\sum_{k=0}^{r}\binom{r}{k}\mu_{\sssig k}\,\mu_{\sssig X}^{r-k}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mu_{\sssig r}^{\prime}=\mathbb{E}(X^{r})\\[0.45em]
&\quad =\mathbb{E}\Bigl[\bigl[(X-\mu_{\sssig X})+\mu_{\sssig X}\bigr]^{r}\Bigr]\\[0.45em]
&\quad =\mathbb{E}\left[\sum_{k=0}^{r}\binom{r}{k}(X-\mu_{\sssig X})^{k}\,\mu_{\sssig X}^{r-k}\right]\\[0.45em]
&\quad =\sum_{k=0}^{r}\binom{r}{k}\mathbb{E}\bigl[(X-\mu_{\sssig X})^{k}\bigr]\,\mu_{\sssig X}^{r-k}\\[0.45em]
&\quad =\sum_{k=0}^{r}\binom{r}{k}\mu_{\sssig k}\,\mu_{\sssig X}^{r-k}
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
{: .topic-paren-cont}
</div>

[Theorem 2.19](#thm-raw-central-moment-conversion) 指出，原動差與主動差可以互相轉換。此外，由於動差母函數可以輕易生成各階的原動差，故即便我們比較常使用主動差來描述分配，但原動差仍佔有一席之地，因為此二種動差之間能夠輕易地轉換。

<div id="thm-lower-order-moment-existence" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.20 (高階動差存在則低階動差存在, existence of lower-order moments)</div>

令 $X$ 為一隨機變數，且 $\mathbb{E}\bigl[\lvert X\rvert^{r}\bigr]<\infty$，則

$$
\mathbb{E}\bigl[\lvert X\rvert^{s}\bigr]<\infty
$$

其中 $0<s<r$。

</div>

<div class="topic-proof" markdown="1">
**Proof.** 在此僅以連續型隨機變數證明，離散型同理可證。

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[\lvert X\rvert^{s}\bigr]&=\int_{-\infty}^{\infty}\lvert x\rvert^{s}f_{\sssig X}(x)\,dx\\[0.45em]
&=\int_{\lvert x\rvert\leqslant1}\lvert x\rvert^{s}f_{\sssig X}(x)\,dx+\int_{\lvert x\rvert>1}\lvert x\rvert^{s}f_{\sssig X}(x)\,dx\\[0.45em]
&\leqslant\int_{\lvert x\rvert\leqslant1}1^{s}f_{\sssig X}(x)\,dx+\int_{\lvert x\rvert>1}\lvert x\rvert^{r}f_{\sssig X}(x)\,dx\\[0.45em]
&\leqslant\int_{-\infty}^{\infty}f_{\sssig X}(x)\,dx+\int_{-\infty}^{\infty}\lvert x\rvert^{r}f_{\sssig X}(x)\,dx\\[0.45em]
&\leqslant1+\mathbb{E}\bigl[\lvert X\rvert^{r}\bigr]<\infty
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}\bigl[\lvert X\rvert^{s}\bigr]=\int_{-\infty}^{\infty}\lvert x\rvert^{s}f_{\sssig X}(x)\,dx\\[0.45em]
&\quad =\int_{\lvert x\rvert\leqslant1}\lvert x\rvert^{s}f_{\sssig X}(x)\,dx\\[0.2em]
&\qquad +\int_{\lvert x\rvert>1}\lvert x\rvert^{s}f_{\sssig X}(x)\,dx\\[0.45em]
&\quad \leqslant\int_{\lvert x\rvert\leqslant1}1^{s}f_{\sssig X}(x)\,dx\\[0.2em]
&\qquad +\int_{\lvert x\rvert>1}\lvert x\rvert^{r}f_{\sssig X}(x)\,dx\\[0.45em]
&\quad \leqslant\int_{-\infty}^{\infty}f_{\sssig X}(x)\,dx\\[0.2em]
&\qquad +\int_{-\infty}^{\infty}\lvert x\rvert^{r}f_{\sssig X}(x)\,dx\\[0.45em]
&\quad \leqslant1+\mathbb{E}\bigl[\lvert X\rvert^{r}\bigr]<\infty
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個定理說明了**高階動差存在的話，將保證低階動差同樣存在**，但這個敘述反過來卻是未必正確的，確實可能會有低階動差存在，但高階動差卻不存在的情形；而低階動差不存在，就直接導致所有更高階的動差都不存在。

</div>

<div id="ex-first-moment-without-second" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.28</div>

<div lang="en" markdown="1">
Find a random variable whose first moment is finite while its second moment does not exist.
</div>

令連續型隨機變數 $X$ 具有 pdf 如下:

$$
f_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{2}{\,x^{3}\,}, & x\geqslant1\\[0.7em]
0, & \text{otherwise}
\end{array}
\right.
$$

則可知道

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[\lvert X\rvert\bigr]&=\int_{1}^{\infty}\lvert x\rvert\,f_{\sssig X}(x)\,dx=\int_{1}^{\infty}x\,f_{\sssig X}(x)\,dx\\[0.45em]
&=\int_{1}^{\infty}x\cdot\frac{2}{\,x^{3}\,}\,dx=2<\infty
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}\bigl[\lvert X\rvert\bigr]=\int_{1}^{\infty}\lvert x\rvert\,f_{\sssig X}(x)\,dx\\[0.45em]
&\quad =\int_{1}^{\infty}x\,f_{\sssig X}(x)\,dx\\[0.45em]
&\quad =\int_{1}^{\infty}x\cdot\frac{2}{\,x^{3}\,}\,dx=2<\infty
\end{aligned}
$$

</div>

以及

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[\lvert X\rvert^{2}\bigr]&=\int_{1}^{\infty}\lvert x\rvert^{2}f_{\sssig X}(x)\,dx=\int_{1}^{\infty}x^{2}f_{\sssig X}(x)\,dx\\[0.45em]
&=\int_{1}^{\infty}x^{2}\cdot\frac{2}{\,x^{3}\,}\,dx=\infty
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}\bigl[\lvert X\rvert^{2}\bigr]=\int_{1}^{\infty}\lvert x\rvert^{2}f_{\sssig X}(x)\,dx\\[0.45em]
&\quad =\int_{1}^{\infty}x^{2}f_{\sssig X}(x)\,dx\\[0.45em]
&\quad =\int_{1}^{\infty}x^{2}\cdot\frac{2}{\,x^{3}\,}\,dx=\infty
\end{aligned}
$$

</div>

</div>

## 本篇小結

[Definition 2.12](#def-population-moment) 以一個基準點 $c$ 與一個階數 $r$ 界定母體動差 $\mathbb{E}[(X-c)^{r}]$，前提是 $\mathbb{E}(\lvert X-c\rvert^{r})<\infty$。取 $c=0$ 得到原動差 $\mu_{\sssig r}^{\prime}=\mathbb{E}(X^{r})$，取 $c=\mu_{\sssig X}$ 得到主動差 $\mu_{\sssig r}=\mathbb{E}[(X-\mu_{\sssig X})^{r}]$，改對絕對值取期望值則得到絕對動差 $\mathbb{E}[\lvert X\rvert^{r}]$。其中一階原動差就是期望值、二階主動差就是變異數，中央趨勢與分散趨勢因而都是動差系統之下的成員。

[Theorem 2.18](#thm-binomial) 的二項式定理是兩種動差互相轉換的工具。[Theorem 2.19](#thm-raw-central-moment-conversion) 據此把 $r$ 階主動差寫成各階原動差的組合，也把 $r$ 階原動差寫成各階主動差的組合，兩者因而可以互相求得。實務上描述分配時較常使用主動差，但動差母函數能夠直接生成各階原動差，這個互換的結果讓原動差同樣派得上用場。[Example 2.27](#ex-discrete-uniform-binomial-moment) 以離散均勻分配示範二項式定理在動差計算上的用法，關鍵是把整串含二項式係數的式子併成 $(1+X)^{k}-X^{k}$ 之後再分別求期望值。

[Theorem 2.20](#thm-lower-order-moment-existence) 則處理各階動差之間的存在性。只要高階絕對動差存在，低階絕對動差就必定存在，證明的作法是以 $\lvert x\rvert\leqslant1$ 與 $\lvert x\rvert>1$ 分段放大。反過來並不成立，[Example 2.28](#ex-first-moment-without-second) 的 $f_{\sssig X}(x)=\frac{2}{x^{3}}$ 就是一階動差存在而二階動差不存在的例子。[下一篇](/teaching-topics/measures-of-shape/)以三階與四階主動差為材料，介紹描述分配形狀的偏態係數與[峰態係數](/teaching-topics/measures-of-shape/#def-kurtosis)。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- Patrick Billingsley. 1995. *Probability and Measure*. 3rd ed. Wiley.
