---
title: "混合型隨機變數"
subtitle: "Mixed Random Variables"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 4
order: 204
permalink: /teaching-topics/mixed-random-variables/
date: 2026-06-08
published: false
listed: false
excerpt: "混合型隨機變數在某些單點上具有正機率，其餘部分則以密度累積機率。本篇由一個在原點跳躍的 cdf 求出其機率函數，再介紹分解定理: 任一 cdf 都可以寫成一個離散型 cdf 與一個連續型 cdf 的線性組合，其係數即離散質點的機率總和；當兩個部分都不退化時，這樣的分解是唯一的。"
---

[上一篇文章](/teaching-topics/cdf-and-pdf/)介紹了累積分配函數與機率密度函數。離散型的 cdf 呈階梯狀，在每一個質點上跳躍；連續型的 cdf 則連續而沒有跳躍。

有一部分隨機變數，並不純粹是離散型隨機變數，亦不純粹是連續型隨機變數。其同時具備離散型隨機變數中具有單點機率，及連續型隨機變數中機率函數不是機率，這兩種重要的特性。我們將這種隨機變數稱作**混合型隨機變數 (mixed random variable)**。

我們在[隨機變數，從樣本空間到數線](/teaching-topics/random-variables-from-sample-space-to-real-line/#note-uncountable-not-continuous)曾經提過，值域為不可數無限並不足以保證 $X$ 為連續型，其中一種情形是某些單點仍具有正機率。混合型正是這樣的例子。

<span id="example-29"></span>
<span id="definition-25"></span>

## 由 cdf 的跳躍與導數求機率函數

混合型的機率函數同樣可以由 cdf 求得: 跳躍的高度給出單點機率，可微部分的導數給出密度。下面這道例題便是這樣的計算。

<div id="ex-mixed-cdf-density" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.13 (A Distribution with a Jump)</div>

<div lang="en" markdown="1">
A random variable $X$ has the distribution function

$$
F_{\sssig X}(x)=
\left\{
\begin{array}{c@{\quad}l}
0, & x<0\\[0.35em]
1-0.8e^{-x}, & x\geqslant 0
\end{array}
\right.
$$

Obtain the density function of $X$.
</div>

依 cdf 的定義，$F_{\sssig X}(0)=\mathbb{P}(X\leqslant 0)$ 而 $F_{\sssig X}(0^{-})=\mathbb{P}(X<0)$，兩者相減即為 $X=0$ 的單點機率，也就是 cdf 在該點跳躍的高度。此處 $F_{\sssig X}(0)=1-0.8=0.2$ 而 <span class="text-nowrap">$F_{\sssig X}(0^{-})=0$，故</span>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X=0)=F_{\sssig X}(0)-F_{\sssig X}(0^{-})=1-0.8e^{0}-0=0.2
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X=0)&=F_{\sssig X}(0)-F_{\sssig X}(0^{-})\\[0.45em]
&=1-0.8e^{0}-0=0.2
\end{aligned}
$$

</div>

當 $x>0$ 時，$F_{\sssig X}(x)=1-0.8e^{-x}$ 可微，其導數 $F_{\sssig X}^{\prime}(x)=0.8e^{-x}$ 即 $f_{\sssig X}$ 在 $x>0$ 的值。故所求為

$$
f_{\sssig X}(x)=
\left\{
\begin{array}{c@{\quad}l}
0.2, & x=0\\[0.35em]
0.8e^{-x}, & x>0\\[0.35em]
0, & \text{otherwise}
\end{array}
\right.
$$

</div>

<div id="note-mixed-density-meaning" class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

上式的 $f_{\sssig X}$ 在 $x=0$ 取的值 $0.2$ 是一個機率，在 $x>0$ 取的值 $0.8e^{-x}$ 則是一個密度，兩者不是同一件事情。這正是混合型同時具備的兩個特性: 離散部分具有單點機率，連續部分的機率函數不是機率。要計算事件機率時，落在單點上的部分用加總，落在區間上的部分用積分。

</div>

<figure id="fig-mixed-cdf" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/mixed-random-variable-cdf.svg" alt="混合型隨機變數的 cdf。函數在 x 小於 0 時為 0，在 x 等於 0 處由 0 跳到 0.2，圖中以雙向箭頭標出這段跳躍，並註明其高度即 X 等於 0 的機率 0.2；其後沿 1 減 0.8 乘 e 的負 x 次方連續上升，並以 1 為水平漸近線。">
  <figcaption><span class="topic-figure__label">Fig. 2.14.</span> Example 2.13 的 cdf: 在 $x=0$ 由 $0$ <span class="text-nowrap">跳到 $0.2$，</span>跳躍高度即單點機率 <span class="text-nowrap">$\mathbb{P}(X=0)=0.2$；</span>其後沿 $1-0.8e^{-x}$ 連續上升，並以 $1$ 為水平漸近線。</figcaption>
</figure>

由圖可見，$x=0$ 的跳躍高度就是單點機率 <span class="text-nowrap">$0.2$，</span>而 $x>0$ 的連續上升則來自密度 $0.8e^{-x}$ 的累積。

## 分解定理

混合型隨機變數，可以看成是由一個完整的離散型隨機變數，與一個完整的連續型隨機變數，經由線性組合而得，這一點不論在 pdf 或是 cdf 都通用。以 [Example 2.13](#ex-mixed-cdf-density) 而言，我們可以將其 cdf 寫為

$$
F_{\sssig X}(x)=0.2\,F_{\sssig d}(x)+0.8\,F_{\sssig c}(x)
$$

其中，離散部分的 cdf 為

$$
F_{\sssig d}(x)=
\left\{
\begin{array}{c@{\quad}l}
0, & x<0\\[0.35em]
1, & x\geqslant 0
\end{array}
\right.
$$

連續部分的 cdf 則為

$$
F_{\sssig c}(x)=
\left\{
\begin{array}{c@{\quad}l}
0, & x<0\\[0.35em]
1-e^{-x}, & x\geqslant 0
\end{array}
\right.
$$

在上面的拆解中，可以發現 $F_{\sssig d}(x)$ 與 $F_{\sssig c}(x)$ 分別是正規的離散型 cdf 與連續型 cdf。事實上，這裡的離散 cdf 與連續 cdf，及其線性組合的係數都是唯一的，此即下列的**分解定理 (decomposition theorem)**。

<div id="thm-decomposition" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.7 (Decomposition Theorem)</div>

若 $X$ 為一隨機變數，且 $F_{\sssig X}(x)$ 為其 cdf，則其可分解為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig X}(x)=\alpha F_{\sssig d}(x)+(1-\alpha)F_{\sssig c}(x),\qquad 0\leqslant\alpha\leqslant 1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
F_{\sssig X}(x)=\alpha F_{\sssig d}(x)+(1-\alpha)F_{\sssig c}(x)\\[0.4em]
0\leqslant\alpha\leqslant 1
\end{gathered}
$$

</div>

其中，$F_{\sssig d}(x)$ 表一離散隨機變數的 cdf，$F_{\sssig c}(x)$ 表一連續隨機變數的 cdf；當 $0<\alpha<1$ 時，此分解必定唯一。

</div>

在進行分解的過程中，可先尋找線性組合的係數 $\alpha$，這個係數將等於離散質點的機率總和。在 [Example 2.13](#ex-mixed-cdf-density) 中即為

$$
\alpha=0.2
$$

整體而言，尋找 $\alpha$、$F_{\sssig d}(x)$ 與 $F_{\sssig c}(x)$ 的步驟如下:

(1) 令 $x_1<x_2<\cdots<x_k$ 表該分配之所有離散質點，對應之機率分別為 $p_1,\ldots,p_k$，則
{: .topic-paren-item}

$$
\alpha=\sum_{i=1}^{k}p_i
$$

並令
{: .topic-paren-cont}

$$
F_{\sssig 1}(x)=
\left\{
\begin{array}{c@{\quad}l}
0, & x<x_1\\[0.35em]
p_1, & x_1\leqslant x<x_2\\[0.35em]
p_1+p_2, & x_2\leqslant x<x_3\\[0.35em]
\vdots & \\[0.35em]
\sum\limits_{i=1}^{k}p_i, & x\geqslant x_k
\end{array}
\right.
$$

(2) $F_{\sssig 1}(x)$ 未必為一 cdf，則可令
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig d}(x)=\frac{1}{\alpha}F_{\sssig 1}(x)=
\left\{
\begin{array}{c@{\quad}l}
0, & x<x_1\\[0.35em]
\dfrac{p_1}{\alpha}, & x_1\leqslant x<x_2\\[0.35em]
\vdots & \\[0.35em]
1, & x\geqslant x_k
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig d}(x)&=\frac{1}{\alpha}F_{\sssig 1}(x)\\[0.45em]
&=
\left\{
\begin{array}{c@{\quad}l}
0, & x<x_1\\[0.35em]
\dfrac{p_1}{\alpha}, & x_1\leqslant x<x_2\\[0.35em]
\vdots & \\[0.35em]
1, & x\geqslant x_k
\end{array}
\right.
\end{aligned}
$$

</div>

此即離散型 cdf。
{: .topic-paren-cont}

(3) 令 $F_{\sssig 2}(x)=F_{\sssig X}(x)-F_{\sssig 1}(x)$，則 $F_{\sssig 2}(x)$ 未必為一 cdf，可令
{: .topic-paren-item}

$$
F_{\sssig c}(x)=\frac{1}{\,1-\alpha\,}F_{\sssig 2}(x)
$$

此即連續型 cdf。
{: .topic-paren-cont}

事實上，讀者將會發現，實際上在拆解的流程，並不是先知道 $F_{\sssig d}(x)$ 與 $F_{\sssig c}(x)$ 為何，而是先尋找 $\alpha$，再將 $F_{\sssig 1}(x)$ 與 $F_{\sssig 2}(x)$ 這二個未必是 cdf 的函數，進行修正而得。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

讀者應該沒有忘記，[Theorem 2.1](/teaching-topics/cdf-and-pdf/#thm-cdf-properties) 中指出，任何的 cdf (不論離散或連續)，其函數值都是從 $0$ 開始，而以 $1$ 結尾，因此需要進行修正，才能夠將其變為正規的 cdf。

</div>

<div id="note-decomposition-special-cases" class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這其中的特例如下:

**[當 $\alpha=0$ 時]**

$$
F_{\sssig X}(x)=F_{\sssig c}(x)
$$

此即 $X$ 為一個純粹的連續型隨機變數。

**[當 $\alpha=1$ 時]**

$$
F_{\sssig X}(x)=F_{\sssig d}(x)
$$

此即 $X$ 為一個純粹的離散型隨機變數。

上列三個步驟中，第 (2) 步除以 $\alpha$、第 (3) 步除以 $1-\alpha$，故三個步驟以 $0<\alpha<1$ 為前提。$\alpha=0$ 與 $\alpha=1$ 這兩個特例，直接由本則的兩個等式得到。

</div>

## pdf 的分解

分解定理的概念，並不僅限於 cdf 的分解，其同樣適用於混合型 pdf 的分解，下面我們就來看一個這樣的例子。

<div id="ex-component-lifetime" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.14 (Length of Life of Electronic Components)</div>

<div lang="en" markdown="1">
Let $Y$ denote the length of life (in hundreds of hours) of electronic components. These components frequently fail immediately upon insertion into a system. It has been observed that the probability of immediate failure is $\frac{1}{4}$. If a component does not fail immediately, the distribution for its length of life has the exponential density function

$$
g(y)=
\left\{
\begin{array}{c@{\quad}l}
e^{-y}, & y>0\\[0.35em]
0, & \text{elsewhere}
\end{array}
\right.
$$

(1) Find the pdf and cdf of $Y$, also evaluate $\mathbb{P}(Y>1)$.
{: .topic-paren-item}
</div>

**(1)** 由於元件有 $\frac{1}{4}$ 的機率在裝上系統時馬上就壞掉，故我們可以假設馬上壞掉的元件，其壽命分配的 pmf 為

$$
f_{\sssig d}(y)=
\left\{
\begin{array}{c@{\quad}l}
1, & y=0\\[0.35em]
0, & \text{elsewhere}
\end{array}
\right.
$$

此即離散部分。並且由題意知道，不會馬上壞掉的元件，其壽命分配的 pdf 為

$$
f_{\sssig c}(y)=g(y)=
\left\{
\begin{array}{c@{\quad}l}
e^{-y}, & y>0\\[0.35em]
0, & \text{elsewhere}
\end{array}
\right.
$$

此即連續部分。則整體元件的壽命分配可以視為二種分配的線性組合，且混合比例為 $\frac{1}{4}$，此即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig Y}(y)=\frac{1}{4}f_{\sssig d}(y)+\frac{3}{4}f_{\sssig c}(y)=
\left\{
\begin{array}{c@{\quad}l}
\dfrac{1}{4}, & y=0\\[0.5em]
\dfrac{3}{4}e^{-y}, & y>0\\[0.5em]
0, & \text{elsewhere}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig Y}(y)&=\frac{1}{4}f_{\sssig d}(y)+\frac{3}{4}f_{\sssig c}(y)\\[0.45em]
&=
\left\{
\begin{array}{c@{\quad}l}
\dfrac{1}{4}, & y=0\\[0.5em]
\dfrac{3}{4}e^{-y}, & y>0\\[0.5em]
0, & \text{elsewhere}
\end{array}
\right.
\end{aligned}
$$

</div>

cdf 亦可以用二種類型的 cdf 經由線性組合得到，故先算出離散部分的 cdf

$$
F_{\sssig d}(y)=
\left\{
\begin{array}{c@{\quad}l}
0, & y<0\\[0.35em]
1, & y\geqslant 0
\end{array}
\right.
$$

與連續部分的 cdf

$$
F_{\sssig c}(y)=
\left\{
\begin{array}{c@{\quad}l}
0, & y<0\\[0.35em]
1-e^{-y}, & y\geqslant 0
\end{array}
\right.
$$

且以此進行線性組合得到

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig Y}(y)=\frac{1}{4}F_{\sssig d}(y)+\frac{3}{4}F_{\sssig c}(y)=
\left\{
\begin{array}{c@{\quad}l}
0, & y<0\\[0.5em]
1-\dfrac{3}{4}e^{-y}, & y\geqslant 0
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig Y}(y)&=\frac{1}{4}F_{\sssig d}(y)+\frac{3}{4}F_{\sssig c}(y)\\[0.45em]
&=
\left\{
\begin{array}{c@{\quad}l}
0, & y<0\\[0.5em]
1-\dfrac{3}{4}e^{-y}, & y\geqslant 0
\end{array}
\right.
\end{aligned}
$$

</div>

則所求為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(Y>1)=1-F_{\sssig Y}(1)=1-\left(1-\frac{3}{4}e^{-1}\right)\fallingdotseq 0.2759
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(Y>1)&=1-F_{\sssig Y}(1)\\[0.45em]
&=1-\left(1-\frac{3}{4}e^{-1}\right)\\[0.45em]
&\fallingdotseq 0.2759
\end{aligned}
$$

</div>

</div>

## 本篇小結

混合型隨機變數同時具備兩種特性: 像離散型一樣，某些單點具有正機率；像連續型一樣，機率函數在其餘部分不是機率而是密度。

[分解定理](#thm-decomposition)指出，任一隨機變數的 cdf 都可以寫成

$$
F_{\sssig X}(x)=\alpha F_{\sssig d}(x)+(1-\alpha)F_{\sssig c}(x)
$$

其中 $F_{\sssig d}$ 為一離散型 cdf、$F_{\sssig c}$ 為一連續型 cdf，而 $\alpha$ 為離散質點的機率總和，且當 $0<\alpha<1$ 時這樣的分解必定唯一。$\alpha=0$ 時 $X$ 為純粹的連續型隨機變數，$\alpha=1$ 時 $X$ 為純粹的離散型隨機變數。

同一個線性組合也適用於 pdf。把離散部分的 pmf 與連續部分的 pdf 依混合比例組合，即得混合型的機率函數，[Example 2.14](#ex-component-lifetime) 的電子元件壽命便是這樣的例子。

至此，隨機變數的三種型態都已介紹完畢。下一篇[期望值，隨機變數的平均位置](/teaching-topics/expected-value-random-variables/)開始討論如何以機率為權重，整理出描述一個分配的量數。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- 黃文璋，2003，《數理統計》，初版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Joseph K. Blitzstein and Jessica Hwang. 2019. *Introduction to Probability*. 2nd ed. Chapman and Hall/CRC.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Patrick Billingsley. 1995. *Probability and Measure*. 3rd ed. Wiley.
