---
title: "條件期望值與條件變異數"
subtitle: "Conditional Expectation and Conditional Variance"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 11
order: 311
permalink: /teaching-topics/conditional-expectation-and-variance/
date: 2026-08-12
published: false
excerpt: "條件分配還是一個分配，而且是單變數的分配，這種分配的期望值便稱為條件期望值: 離散型以條件機率質量函數對各個取值加權求和，連續型則以條件機率密度函數加權積分，同一套作法套在 $g(X)$ 上便得到函數的條件期望值。條件期望值本質上仍是一種期望值，故期望值所具有的各種性質它都順勢繼承，其中也包含變異數，這種變異數即為條件變異數，同樣有平方的條件期望值減去條件期望值的平方這一條速算公式。條件期望值有一個一般期望值沒有的特色，就是它是「給定的條件」的函數。本篇並以三道例題示範離散型與連續型的計算。"
---

[上一篇](/teaching-topics/multivariate-expectations/)把[期望值](/teaching-topics/expectation/#def-expectation)與[變異數](/teaching-topics/variance/#def-variance)推廣到二元[隨機變數](/teaching-topics/random-variables-and-pmf/#def-random-variable)的函數 <span class="text-nowrap">$g(X,Y)$，</span>其中所使用的機率分配是聯合分配。但在[條件機率質量函數](/teaching-topics/conditional-distributions/#def-conditional-pmf)與[條件機率密度函數](/teaching-topics/conditional-distributions/#def-conditional-pdf)之中，我們已經看過另一種機率分配。它就是把其中一個變數固定成常數之後所得到的條件分配。

既然條件分配仍然是一種機率分配，我們當然也可以談它的期望值與變異數。本篇便由此出發，先分別對離散與連續的情形給出條件期望值的定義，再把它推廣到函數 $g(X)$ 的條件期望值，接著給出條件變異數並導出它的速算公式，最後以三道例題示範離散型與連續型的計算。

## 條件期望值

<div id="def-conditional-expectation" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 3.11 (條件期望值, conditional expectation)</div>

令 $(X,Y)$ 為二元**離散**隨機變數，且 conditional pmf 為 $p_{\sssig X\mid Y}(x\mid y)$ 及 <span class="text-nowrap">$p_{\sssig Y\mid X}(y\mid x)$，</span>則稱

$$
\mathbb{E}(X\mid Y=y)=\sum_{x\in\mathcal{R}_{\sssig X}}x\,p_{\sssig X\mid Y}(x\mid y)
$$

為 $X$ 給定 $Y=y$ 的**條件期望值**，並稱

$$
\mathbb{E}(Y\mid X=x)=\sum_{y\in\mathcal{R}_{\sssig Y}}y\,p_{\sssig Y\mid X}(y\mid x)
$$

為 $Y$ 給定 $X=x$ 的**條件期望值**。

令 $(X,Y)$ 為二元**連續**隨機變數，且 conditional pdf 為 $f_{\sssig X\mid Y}(x\mid y)$ 及 <span class="text-nowrap">$f_{\sssig Y\mid X}(y\mid x)$，</span>則稱

$$
\mathbb{E}(X\mid Y=y)=\int_{x\in\mathcal{R}_{\sssig X}}x\,f_{\sssig X\mid Y}(x\mid y)\,dx
$$

為 $X$ 給定 $Y=y$ 的**條件期望值**，並稱

$$
\mathbb{E}(Y\mid X=x)=\int_{y\in\mathcal{R}_{\sssig Y}}y\,f_{\sssig Y\mid X}(y\mid x)\,dy
$$

為 $Y$ 給定 $X=x$ 的**條件期望值**。

</div>

稍早我們曾提過，**條件分配還是一個分配**，而且是單變數的分配，這種分配的期望值便稱為**條件期望值**。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

我們曾經提過，條件分配的直觀意義是**將樣本空間縮小至 $Y=y$ (或 $X=x$) 的空間**，且期望值的直觀意義是**一個機率分配的重心**，若由此二觀點而言，條件期望值的直觀意義便是**在 $Y=y$ (或 $X=x$) 的空間中的重心**。

</div>

<div id="def-conditional-expectation-of-function" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 3.12 (函數的條件期望值, conditional expectation of a function)</div>

令 $(X,Y)$ 為二元**離散**隨機變數，且 conditional pmf 為 $p_{\sssig X\mid Y}(x\mid y)$ 及 <span class="text-nowrap">$p_{\sssig Y\mid X}(y\mid x)$，</span>則稱

$$
\mathbb{E}\bigl[g(X)\mid Y=y\bigr]=\sum_{x\in\mathcal{R}_{\sssig X}}g(x)\,p_{\sssig X\mid Y}(x\mid y)
$$

為 $g(X)$ 給定 $Y=y$ 的**條件期望值**，並稱

$$
\mathbb{E}\bigl[g(Y)\mid X=x\bigr]=\sum_{y\in\mathcal{R}_{\sssig Y}}g(y)\,p_{\sssig Y\mid X}(y\mid x)
$$

為 $g(Y)$ 給定 $X=x$ 的**條件期望值**。

令 $(X,Y)$ 為二元**連續**隨機變數，且 conditional pdf 為 $f_{\sssig X\mid Y}(x\mid y)$ 及 <span class="text-nowrap">$f_{\sssig Y\mid X}(y\mid x)$，</span>則稱

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\bigl[g(X)\mid Y=y\bigr]=\int_{x\in\mathcal{R}_{\sssig X}}g(x)\,f_{\sssig X\mid Y}(x\mid y)\,dx
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[g(X)\mid Y=y\bigr]&=\int_{x\in\mathcal{R}_{\sssig X}}g(x)\,f_{\sssig X\mid Y}(x\mid y)\,dx
\end{aligned}
$$

</div>

為 $g(X)$ 給定 $Y=y$ 的**條件期望值**，並稱

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\bigl[g(Y)\mid X=x\bigr]=\int_{y\in\mathcal{R}_{\sssig Y}}g(y)\,f_{\sssig Y\mid X}(y\mid x)\,dy
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[g(Y)\mid X=x\bigr]&=\int_{y\in\mathcal{R}_{\sssig Y}}g(y)\,f_{\sssig Y\mid X}(y\mid x)\,dy
\end{aligned}
$$

</div>

為 $g(Y)$ 給定 $X=x$ 的**條件期望值**。

</div>

條件期望值與函數的條件期望值有一些地方需要注意:

(1) 條件期望值只不過是**使用了條件分配作為機率分配**而得到的期望值，本質上而言還是一種期望值，故期望值所具有的各種性質，條件期望值都應順勢繼承。
{: .topic-paren-item}

(2) 由於條件期望值繼承了期望值的所有性質，這當中是否包含我們曾提過的特殊期望值，也就是**變異數**呢？這是當然的，這種變異數稱作**條件變異數**，我們馬上會看到[其定義](#def-conditional-variance)。
{: .topic-paren-item}

(3) 條件期望值有一個一般期望值沒有的特色，是**條件期望值是「給定的條件」的函數**，這一點在稍後提到**[雙重期望值定理](/teaching-topics/double-expectation-theorem/#thm-double-expectation) <span lang="en">(double expectation theorem)</span>** 時我們會有更詳細的了解。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

事實上我們在處理 $X$ (或 $Y$) 的條件分配時，如果機率函數中還有給定的 $Y=y$ (或 $X=x$)，我們會將此處的 $y$ (或 $x$) 當成一個常數，而條件期望值的運算**只把 $X$ (或 $Y$) 當成隨機變數**，在條件期望值算完後，$Y=y$ (或 $X=x$) 會被留下來，所以我們會說**條件期望值是「給定的條件」的函數**。

</div>

## 條件變異數

<div id="def-conditional-variance" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 3.13 (條件變異數, conditional variance)</div>

令 $(X,Y)$ 為二元隨機變數，且條件期望值分別為 $\mathbb{E}(X\mid Y=y)$ 及 <span class="text-nowrap">$\mathbb{E}(Y\mid X=x)$，</span>則稱

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}(X\mid Y=y)=\mathbb{E}\Bigl(\bigl[X-\mathbb{E}(X\mid Y=y)\bigr]^{2}\Bigm\vert Y=y\Bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(X\mid Y=y)&=\mathbb{E}\Bigl(\bigl[X-\mathbb{E}(X\mid Y=y)\bigr]^{2}\Bigm\vert Y=y\Bigr)
\end{aligned}
$$

</div>

為 $X$ 給定 $Y=y$ 的**條件變異數**，並稱

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}(Y\mid X=x)=\mathbb{E}\Bigl(\bigl[Y-\mathbb{E}(Y\mid X=x)\bigr]^{2}\Bigm\vert X=x\Bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(Y\mid X=x)&=\mathbb{E}\Bigl(\bigl[Y-\mathbb{E}(Y\mid X=x)\bigr]^{2}\Bigm\vert X=x\Bigr)
\end{aligned}
$$

</div>

為 $Y$ 給定 $X=x$ 的**條件變異數**。

</div>

條件變異數有一些地方需要注意:

(1) 條件變異數的直觀意義，是**在 $Y=y$ (或 $X=x$) 的空間中的離散程度**。
{: .topic-paren-item}

(2) 變異數有[速算公式](/teaching-topics/variance/#thm-variance-formula):
{: .topic-paren-item}

$$
\mathrm{Var}(X)=\mathbb{E}\bigl(X^{2}\bigr)-\bigl(\mathbb{E}(X)\bigr)^{2}
$$

而條件變異數也有同樣的公式如下:
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(X\mid Y=y)&=\mathbb{E}\Bigl(\bigl[X-\mathbb{E}(X\mid Y=y)\bigr]^{2}\Bigm\vert Y=y\Bigr)\\[0.45em]
&=\mathbb{E}\Bigl(X^{2}-2X\,\mathbb{E}(X\mid Y=y)+\bigl[\mathbb{E}(X\mid Y=y)\bigr]^{2}\Bigm\vert Y=y\Bigr)\\[0.45em]
&=\mathbb{E}\bigl(X^{2}\mid Y=y\bigr)-2\,\mathbb{E}(X\mid Y=y)\,\mathbb{E}(X\mid Y=y)\\[0.2em]
&\qquad +\bigl[\mathbb{E}(X\mid Y=y)\bigr]^{2}\\[0.45em]
&=\mathbb{E}\bigl(X^{2}\mid Y=y\bigr)-\bigl[\mathbb{E}(X\mid Y=y)\bigr]^{2}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(X\mid Y=y)&=\mathbb{E}\Bigl(\bigl[X-\mathbb{E}(X\mid Y=y)\bigr]^{2}\Bigm\vert Y=y\Bigr)\\[0.45em]
&=\mathbb{E}\Bigl(X^{2}-2X\,\mathbb{E}(X\mid Y=y)\\[0.2em]
&\qquad+\bigl[\mathbb{E}(X\mid Y=y)\bigr]^{2}\Bigm\vert Y=y\Bigr)\\[0.45em]
&=\mathbb{E}\bigl(X^{2}\mid Y=y\bigr)\\[0.2em]
&\qquad-2\,\mathbb{E}(X\mid Y=y)\,\mathbb{E}(X\mid Y=y)\\[0.2em]
&\qquad+\bigl[\mathbb{E}(X\mid Y=y)\bigr]^{2}\\[0.45em]
&=\mathbb{E}\bigl(X^{2}\mid Y=y\bigr)-\bigl[\mathbb{E}(X\mid Y=y)\bigr]^{2}
\end{aligned}
$$

</div>

此即**平方的條件期望值減去條件期望值的平方**。
{: .topic-paren-cont}

## 條件期望值與條件變異數的計算

<div id="ex-price-quantity-joint-table" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.18</div>

<div lang="en" markdown="1">
Suppose that $X$ is the amount by which the price of a certain product rises, that $Y$ is the amount by which the quantity sold falls, and that the joint probability distribution of $X$ and $Y$ is the one recorded in the table below.

| $X\backslash Y$ | $10$ | $20$ | $30$ |
| :---: | :---: | :---: | :---: |
| $5$ | $0.1$ | $0.2$ | $0.1$ |
| $10$ | $0.1$ | $0.1$ | $0.1$ |
| $15$ | $0.1$ | $0.1$ | $0.1$ |
{: .topic-table--matrix}

<ol class="topic-list-paren">
  <li>Determine whether $X$ and $Y$ are independent.</li>
  <li>Evaluate $\mathbb{E}(X\mid Y=20)$ and <span class="text-nowrap">$\mathrm{Var}(X\mid Y=20)$.</span></li>
</ol>
</div>

(1) 首先先將邊際分配算出來，如下:
{: .topic-paren-item}

| $X\backslash Y$ | $10$ | $20$ | $30$ | $p_{\sssig X}(x)$ |
| :---: | :---: | :---: | :---: | :---: |
| $5$ | $0.1$ | $0.2$ | $0.1$ | $0.4$ |
| $10$ | $0.1$ | $0.1$ | $0.1$ | $0.3$ |
| $15$ | $0.1$ | $0.1$ | $0.1$ | $0.3$ |
| $p_{\sssig Y}(y)$ | $0.3$ | $0.4$ | $0.3$ | $1$ |
{: .topic-table--joint-pmf}

則由上表可得
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
p_{\sssig XY}(5,10)&=0.1\neq p_{\sssig X}(5)\,p_{\sssig Y}(10)=0.4\times 0.3=0.12\qquad\therefore\, X\not\indep Y
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig XY}(5,10)&=0.1\neq p_{\sssig X}(5)\,p_{\sssig Y}(10)\\[0.45em]
&=0.4\times 0.3=0.12\qquad\therefore\, X\not\indep Y
\end{aligned}
$$

</div>

(2) 由 (1) 可以得到 $X$ 在給定 $Y=20$ 下的條件分配為:
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
p_{\sssig X\mid Y}(x\mid 20)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{0.2}{0.4}=0.5, & x=5\\[0.8em]
\dfrac{0.1}{0.4}=0.25, & x=10\ \text{or}\ 15\\[0.8em]
0, & \text{o.w.}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases">
  <div class="topic-cases__lhs">$p_{\sssig X\mid Y}(x\mid 20)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$\dfrac{0.2}{0.4}=0.5,$</div>
    <div class="topic-cases__cond">$x=5$</div>
    <div class="topic-cases__val">$\dfrac{0.1}{0.4}=0.25,$</div>
    <div class="topic-cases__cond">$x=10\ \text{or}\ 15$</div>
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$\text{o.w.}$</div>
  </div>
</div>

</div>

由此可得
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ &\mathbb{E}(X\mid Y=20)=5\times 0.5+10\times 0.25+15\times 0.25=8.75\\[0.45em]
&\mathbb{E}\bigl(X^{2}\mid Y=20\bigr)=5^{2}\times 0.5+10^{2}\times 0.25+15^{2}\times 0.25=93.75
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ \mathbb{E}(X\mid Y=20)&=5\times 0.5+10\times 0.25\\[0.2em]
&\qquad+15\times 0.25=8.75\\[0.45em]
\mathbb{E}\bigl(X^{2}\mid Y=20\bigr)&=5^{2}\times 0.5+10^{2}\times 0.25\\[0.2em]
&\qquad+15^{2}\times 0.25=93.75
\end{aligned}
$$

</div>

故所求為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ \mathrm{Var}(X\mid Y=20)&=\mathbb{E}\bigl(X^{2}\mid Y=20\bigr)-\bigl[\mathbb{E}(X\mid Y=20)\bigr]^{2}\\[0.45em]
&=93.75-(8.75)^{2}=17.1875
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ \mathrm{Var}(X\mid Y=20)&=\mathbb{E}\bigl(X^{2}\mid Y=20\bigr)\\[0.2em]
&\qquad-\bigl[\mathbb{E}(X\mid Y=20)\bigr]^{2}\\[0.45em]
&=93.75-(8.75)^{2}=17.1875
\end{aligned}
$$

</div>

</div>

<div id="ex-joint-pdf-product-expectation" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.19</div>

<div lang="en" markdown="1">
Suppose that the joint probability density function of $X$ and $Y$ is

$$
f_{\sssig XY}(x,y)=
\left\lbrace
\begin{array}{c@{\quad}l}
c\,y, & 0<y<x<2\\[0.5em]
0, & \text{o.w.}
\end{array}
\right.
$$

<ol class="topic-list-paren">
  <li>Determine the constant $c$ for which $f_{\sssig XY}(x,y)$ is a legitimate pdf.</li>
  <li>Evaluate $\mathbb{E}(Y\mid X=1)$ and <span class="text-nowrap">$\mathbb{E}(X\mid Y=1)$.</span></li>
</ol>
</div>

(1) 由 joint pdf 積分為 $1$ 可知:
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
1&=\int_{0}^{2}\int_{0}^{x}cy\,dy\,dx=\int_{0}^{2}\Bigl[\frac{c}{2}y^{2}\Bigr]_{0}^{x}\,dx=\int_{0}^{2}\frac{c}{2}x^{2}\,dx\\[0.45em]
&=\Bigl[\frac{c}{6}x^{3}\Bigr]_{0}^{2}=\frac{4}{3}c
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
1&=\int_{0}^{2}\int_{0}^{x}cy\,dy\,dx\\[0.45em]
&=\int_{0}^{2}\Bigl[\frac{c}{2}y^{2}\Bigr]_{0}^{x}\,dx\\[0.45em]
&=\int_{0}^{2}\frac{c}{2}x^{2}\,dx=\Bigl[\frac{c}{6}x^{3}\Bigr]_{0}^{2}=\frac{4}{3}c
\end{aligned}
$$

</div>

故可知
{: .topic-paren-cont}

$$
c=\frac{3}{\,4\,}
$$

且
{: .topic-paren-cont}

$$
f_{\sssig XY}(x,y)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{3}{\,4\,}y, & 0<y<x<2\\[0.8em]
0, & \text{o.w.}
\end{array}
\right.
$$

確實為合法的 pdf。
{: .topic-paren-cont}

(2) 由 (1) 可先算出 $X$ 與 $Y$ 的 marginal pdf 為:
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
f_{\sssig X}(x)=\int_{0}^{x}\frac{3}{\,4\,}y\,dy=\Bigl[\frac{3}{\,8\,}y^{2}\Bigr]_{0}^{x}=\frac{3}{\,8\,}x^{2},\ 0<x<2\\[0.55em]
f_{\sssig Y}(y)=\int_{y}^{2}\frac{3}{\,4\,}y\,dx=\Bigl[\frac{3}{\,4\,}xy\Bigr]_{y}^{2}=\frac{3}{\,2\,}y-\frac{3}{\,4\,}y^{2},\ 0<y<2
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig X}(x)&=\int_{0}^{x}\frac{3}{\,4\,}y\,dy=\Bigl[\frac{3}{\,8\,}y^{2}\Bigr]_{0}^{x}\\[0.45em]
&=\frac{3}{\,8\,}x^{2},\ 0<x<2\\[0.9em]
f_{\sssig Y}(y)&=\int_{y}^{2}\frac{3}{\,4\,}y\,dx=\Bigl[\frac{3}{\,4\,}xy\Bigr]_{y}^{2}\\[0.45em]
&=\frac{3}{\,2\,}y-\frac{3}{\,4\,}y^{2},\ 0<y<2
\end{aligned}
$$

</div>

接著可以算出二種 conditional pdf 分別為:
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
f_{\sssig X\mid Y}(x\mid y)=\frac{\,f_{\sssig XY}(x,y)\,}{f_{\sssig Y}(y)}=\frac{\frac{3}{\,4\,}y}{\,\frac{3}{\,2\,}y-\frac{3}{4}y^{2}\,}=\frac{1}{\,2-y\,},\ 0<y<x<2\\[0.55em]
f_{\sssig Y\mid X}(y\mid x)=\frac{\,f_{\sssig XY}(x,y)\,}{f_{\sssig X}(x)}=\frac{\frac{3}{\,4\,}y}{\,\frac{3}{\,8\,}x^{2}\,}=\frac{2y}{\,x^{2}\,},\ 0<y<x<2
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig X\mid Y}(x\mid y)&=\frac{\,f_{\sssig XY}(x,y)\,}{f_{\sssig Y}(y)}=\frac{\frac{3}{\,4\,}y}{\,\frac{3}{\,2\,}y-\frac{3}{4}y^{2}\,}\\[0.45em]
&=\frac{1}{\,2-y\,},\ 0<y<x<2\\[0.9em]
f_{\sssig Y\mid X}(y\mid x)&=\frac{\,f_{\sssig XY}(x,y)\,}{f_{\sssig X}(x)}=\frac{\frac{3}{\,4\,}y}{\,\frac{3}{\,8\,}x^{2}\,}\\[0.45em]
&=\frac{2y}{\,x^{2}\,},\ 0<y<x<2
\end{aligned}
$$

</div>

則所求為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\mathbb{E}(Y\mid X=1)=\int_{0}^{1}y\,\frac{2y}{1^{2}}\,dy=\Bigl[\frac{2}{3}y^{3}\Bigr]_{0}^{1}=\frac{2}{\,3\,}\\[0.55em]
\mathbb{E}(X\mid Y=1)=\int_{1}^{2}x\,\frac{1}{2-1}\,dx=\Bigl[\frac{1}{2}x^{2}\Bigr]_{1}^{2}=\frac{3}{\,2\,}
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(Y\mid X=1)&=\int_{0}^{1}y\,\frac{2y}{1^{2}}\,dy\\[0.45em]
&=\Bigl[\frac{2}{3}y^{3}\Bigr]_{0}^{1}=\frac{2}{\,3\,}\\[0.9em]
\mathbb{E}(X\mid Y=1)&=\int_{1}^{2}x\,\frac{1}{2-1}\,dx\\[0.45em]
&=\Bigl[\frac{1}{2}x^{2}\Bigr]_{1}^{2}=\frac{3}{\,2\,}
\end{aligned}
$$

</div>

</div>

<div id="ex-joint-pdf-variance-of-sum" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.20</div>

<div lang="en" markdown="1">
Suppose that a continuous random vector $(X,Y)$ has the joint pdf

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig XY}(x,y)=
\left\lbrace
\begin{array}{c@{\quad}l}
x+y, & 0\leqslant x\leqslant 1,\ 0\leqslant y\leqslant 1\\[0.5em]
0, & \text{o.w.}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases">
  <div class="topic-cases__lhs">$f_{\sssig XY}(x,y)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$x+y,$</div>
    <div class="topic-cases__cond">$0\leqslant x\leqslant 1$, $0\leqslant y\leqslant 1$</div>
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$\text{o.w.}$</div>
  </div>
</div>

</div>

<ol class="topic-list-paren">
  <li>Evaluate the conditional variance <span class="text-nowrap">$\mathrm{Var}(Y\mid X=x)$.</span></li>
  <li>Evaluate the conditional variance <span class="text-nowrap">$\mathrm{Var}(2Y+3X+4\mid X=x)$.</span></li>
</ol>
</div>

(1) 先算出 $X$ 的 marginal pdf 為:
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X}(x)=\int_{0}^{1}(x+y)\,dy=x+\frac{1}{\,2\,},\ 0\leqslant x\leqslant 1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig X}(x)&=\int_{0}^{1}(x+y)\,dy\\[0.45em]
&=x+\frac{1}{\,2\,},\ 0\leqslant x\leqslant 1
\end{aligned}
$$

</div>

故可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig Y\mid X}(y\mid x)=\frac{\,f_{\sssig XY}(x,y)\,}{f_{\sssig X}(x)}=\frac{x+y}{\,x+\frac{1}{2}\,},\ 0\leqslant x\leqslant 1,\ 0\leqslant y\leqslant 1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig Y\mid X}(y\mid x)&=\frac{\,f_{\sssig XY}(x,y)\,}{f_{\sssig X}(x)}=\frac{x+y}{\,x+\frac{1}{2}\,},\\[0.45em]
&\quad 0\leqslant x\leqslant 1,\ 0\leqslant y\leqslant 1
\end{aligned}
$$

</div>

接著可以算出
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\mathbb{E}(Y\mid X=x)=\int_{0}^{1}y\,\frac{x+y}{\,x+\frac{1}{2}\,}\,dy=\frac{\,\frac{x}{2}+\frac{1}{3}\,}{x+\frac{1}{2}},\ 0\leqslant x\leqslant 1\\[0.55em]
\mathbb{E}\bigl(Y^{2}\mid X=x\bigr)=\int_{0}^{1}y^{2}\,\frac{x+y}{\,x+\frac{1}{2}\,}\,dy=\frac{\,\frac{x}{3}+\frac{1}{4}\,}{x+\frac{1}{2}},\ 0\leqslant x\leqslant 1
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(Y\mid X=x)&=\int_{0}^{1}y\,\frac{x+y}{\,x+\frac{1}{2}\,}\,dy\\[0.45em]
&=\frac{\,\frac{x}{2}+\frac{1}{3}\,}{x+\frac{1}{2}},\ 0\leqslant x\leqslant 1\\[0.9em]
\mathbb{E}\bigl(Y^{2}\mid X=x\bigr)&=\int_{0}^{1}y^{2}\,\frac{x+y}{\,x+\frac{1}{2}\,}\,dy\\[0.45em]
&=\frac{\,\frac{x}{3}+\frac{1}{4}\,}{x+\frac{1}{2}},\ 0\leqslant x\leqslant 1
\end{aligned}
$$

</div>

則所求為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(Y\mid X=x)&=\mathbb{E}\bigl(Y^{2}\mid X=x\bigr)-\bigl[\mathbb{E}(Y\mid X=x)\bigr]^{2}\\[0.45em]
&=\frac{\,6x^{2}+6x+1\,}{18(2x+1)^{2}},\ 0\leqslant x\leqslant 1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(Y\mid X=x)&=\mathbb{E}\bigl(Y^{2}\mid X=x\bigr)-\bigl[\mathbb{E}(Y\mid X=x)\bigr]^{2}\\[0.45em]
&=\frac{\,6x^{2}+6x+1\,}{18(2x+1)^{2}},\ 0\leqslant x\leqslant 1
\end{aligned}
$$

</div>

(2)
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(2Y+3X+4\mid X=x)&=4\,\mathrm{Var}(Y\mid X=x)\\[0.45em]
&=\frac{\,12x^{2}+12x+2\,}{9(2x+1)^{2}},\ 0\leqslant x\leqslant 1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(2Y+3X+4\mid X=x)&=4\,\mathrm{Var}(Y\mid X=x)\\[0.45em]
&=\frac{\,12x^{2}+12x+2\,}{9(2x+1)^{2}},\ 0\leqslant x\leqslant 1
\end{aligned}
$$

</div>

</div>

## 本篇小結

[Definition 3.11](#def-conditional-expectation) 把期望值的定義搬到條件分配上。離散型以 conditional pmf 對 $X$ 的各個取值加權求和，連續型則以 conditional pdf 加權積分，所得的 $\mathbb{E}(X\mid Y=y)$ 與 $\mathbb{E}(Y\mid X=x)$ 即為條件期望值。條件分配還是一個分配，而且是單變數的分配，條件期望值即為這種分配的期望值；若把樣本空間縮小至 $Y=y$ 的空間，再取這個分配的重心，所得的就是條件期望值。[Definition 3.12](#def-conditional-expectation-of-function) 把加權的對象由 $x$ 換成 <span class="text-nowrap">$g(x)$，</span>便得到函數的條件期望值。

條件期望值本質上仍是一種期望值，只是所使用的機率分配換成了條件分配，故期望值的各種性質它都順勢繼承，其中也包含變異數。[Definition 3.13](#def-conditional-variance) 即以離差平方的條件期望值給出條件變異數，其直觀意義是在 $Y=y$ 的空間中的離散程度；展開之後同樣得到平方的條件期望值減去條件期望值的平方這一條速算公式。條件期望值另有一個一般期望值沒有的特色。條件中的 $y$ 在運算時視為常數，算完之後會被留下來，因此條件期望值是「給定的條件」的函數。

[Example 3.18](#ex-price-quantity-joint-table) 由一張三乘三的聯合機率表出發，先由邊際分配判定兩個變數並不獨立，再取 $Y=20$ 的那一行求出條件分配，並依速算公式求得條件期望值 $8.75$ 與條件變異數 $17.1875$ 兩個結果。[Example 3.19](#ex-joint-pdf-product-expectation) 這一題的聯合值域為 <span class="text-nowrap">$0<y<x<2$，</span>先由積分為 $1$ 求得 <span class="text-nowrap">$c=\frac{3}{4}$，</span>再依序求出兩個 marginal pdf 與兩個 conditional pdf，最後求得 $\mathbb{E}(Y\mid X=1)$ 與 $\mathbb{E}(X\mid Y=1)$ 分別為 $\frac{2}{3}$ 與 $\frac{3}{2}$ 兩個值。[Example 3.20](#ex-joint-pdf-variance-of-sum) 則示範條件變異數的求法，並在第二小題中把變異數的性質用在條件變異數上。給定 $X=x$ 之後 $3X+4$ 已是常數，只有 $2Y$ 這一項有作用，故所求的條件變異數是 $\mathrm{Var}(Y\mid X=x)$ 的四倍。

[下一篇](/teaching-topics/double-expectation-theorem/)將由條件期望值是「給定的條件」的函數這一點出發，介紹雙重期望值定理。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
