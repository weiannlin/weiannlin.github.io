---
title: "抽樣分配關係的例題"
subtitle: "Examples on the Relationships among Sampling Distributions"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 4
topic: 25
order: 425
permalink: /teaching-topics/sampling-distribution-examples/
date: 2026-08-15
published: false
excerpt: "本篇以兩道例題演練前面幾篇所建立的抽樣分配關係。第一題由自由度為 $p$ 的 $t$ 分配出發: 先以 Jacobian 法把值域分成 $X\\geqslant0$ 與 $X<0$ 兩段，各自轉換之後相加，得到 $Y=X^{2}$ 服從自由度為 $1$ 與 $p$ 的 $\\mathcal{F}$ 分配；再以史特靈公式把式中的兩個伽瑪函數換成初等函數，逐項取極限，得到 $t$ 分配的機率函數在自由度趨於無窮時收斂至標準常態分配的機率函數。第二題表面上是單邊的尾機率，實際上問的是兩獨立樣本變異數比值的雙尾機率: 先把取極小值的事件改寫為 $k\\leqslant\\frac{W_1}{W_2}\\leqslant\\frac{1}{k}$ 這個區間，再由分子自由度與分母自由度相同時 $\\mathcal{F}$ 分配取倒數之後仍為同一個分配，得到 $k=\\mathcal{F}_{0.95}(5,5)$ 這個答案。"
---

[上一篇](/teaching-topics/sampling-distribution-tail-points/)把常用抽樣分配之間的尾點關係逐條證明出來，本篇則以兩道例題演練這些關係的用法。兩題都不再引入新的定義，而是把前面幾篇所建立的分配關係與尾點關係實際用在計算上。

第一題處理 [$t$ 分配](/teaching-topics/student-t-distribution/#def-t-distribution)與 [$\mathcal{F}$ 分配](/teaching-topics/snedecor-f-distribution/#def-f-distribution)之間的關係。$Y=X^{2}$ 不是一對一的轉換，因此要依[非一對一的函數轉換](/teaching-topics/many-to-one-transformations/)的作法，把 $X$ 的值域分成 $X\geqslant0$ 與 $X<0$ 兩段，兩段各自以 [Jacobian 法](/teaching-topics/one-to-one-transformations/#prop-jacobian-method)轉換之後再相加。該題第二小題則要把兩個[伽瑪函數](/teaching-topics/gamma-function-exponential-distribution/#def-gamma-function)的比值化為初等函數，所依據的是題目所給的近似式，也就是該題之後那則註記所說的史特靈公式。

第二題所求的是一個常數，使兩個樣本變異數之比值與其倒數之中較小者小於該常數的機率等於 $0.10$ 這個數值。表面上這是單邊的尾機率，把事件改寫之後會發現，問的其實是雙尾的機率，而分子自由度與分母自由度相同這個條件，正是能夠以 $k$ 與 $\frac{1}{\,k\,}$ 兩者表示兩個端點的原因。

## $t$ 分配的平方與其極限分配

<div id="ex-sampling-ex-1" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.58</div>

<div lang="en" markdown="1">
Suppose that $X$ is a random variable whose distribution is Student’s $t$ with $p$ degrees of freedom, so that its pdf is

$$
f(x\mid p)=\frac{\Gamma\bigl(\frac{p+1}{2}\bigr)}{\,\Gamma\bigl(\frac{p}{2}\bigr)\sqrt{\pi p}\,}\biggl(1+\frac{\,x^{2}\,}{p}\biggr)^{-\frac{p+1}{2}},\quad-\infty<x<\infty
$$

Throughout, the Gamma function is $\Gamma(a)=\int_{0}^{\infty}t^{a-1}e^{-t}\,dt$, and the identities $\Gamma(a+1)=a\Gamma(a)$ for <span class="text-nowrap">$a>0$,</span> $\Gamma(1)=1$ and $\Gamma\bigl(\frac{1}{2}\bigr)=\sqrt{\pi}$ are available, together with the approximation $\Gamma(a+1)\fallingdotseq\sqrt{2\pi}\,a^{a+\frac{1}{2}}e^{-a}$ for large <span class="text-nowrap">$a$.</span>

(1) Show that $Y=X^{2}$ carries an $\mathcal{F}$ distribution with $1$ and $p$ degrees of freedom, that is,
{: .topic-paren-item}

$$
h(y\mid p)=\frac{\Gamma\bigl(\frac{p+1}{2}\bigr)}{\,\Gamma\bigl(\frac{p}{2}\bigr)\Gamma\bigl(\frac{1}{2}\bigr)\,}\frac{1}{\,\sqrt{p}\,}\frac{y^{-\frac{1}{2}}}{\,\bigl(1+\frac{y}{p}\bigr)^{\frac{p+1}{2}}\,},\ y\geqslant0
$$

(2) Show that $\lim_{p\to\infty}f(x\mid p)=\frac{1}{\,\sqrt{2\pi}\,}e^{-\frac{x^{2}}{2}}$ for <span class="text-nowrap">$-\infty<x<\infty$,</span> and hence that $X$ converges in distribution to an $\mathcal{N}(0,1)$ random variable as <span class="text-nowrap">$p\to\infty$.</span>
{: .topic-paren-item}
</div>

(1) **[ Jacobian 法 ]**
{: .topic-paren-item}

<div class="topic-math-follow-before" markdown="1">

$$
[\,X\geqslant0\,]\quad Y=X^{2}
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop topic-math-follow" markdown="1">

$$
\Longrightarrow\ X=\sqrt{Y}\ \text{且}\ \mathbf{J}=\frac{\,dx\,}{dy}=\frac{1}{\,2\sqrt{y}\,},\ y\geqslant0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile topic-math-follow" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ X&=\sqrt{Y}\\[0.35em]
\text{且}\ \mathbf{J}&=\frac{\,dx\,}{dy}=\frac{1}{\,2\sqrt{y}\,},\ y\geqslant0
\end{aligned}
$$

</div>

知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
h^{*}(y\mid p)&=f(\sqrt{y}\mid p)\left\lvert\frac{1}{\,2\sqrt{y}\,}\right\rvert\\[0.45em]
&=\frac{\Gamma\bigl(\frac{p+1}{2}\bigr)}{\,\Gamma\bigl(\frac{p}{2}\bigr)\sqrt{\pi p}\,}\biggl(1+\frac{\,y\,}{p}\biggr)^{-\frac{p+1}{2}}\times\frac{1}{\,2\sqrt{y}\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
h^{*}(y\mid p)&=f(\sqrt{y}\mid p)\left\lvert\frac{1}{\,2\sqrt{y}\,}\right\rvert\\[0.3em]
&=\frac{\Gamma\bigl(\frac{p+1}{2}\bigr)}{\,\Gamma\bigl(\frac{p}{2}\bigr)\sqrt{\pi p}\,}\biggl(1+\frac{\,y\,}{p}\biggr)^{-\frac{p+1}{2}}\\[0.3em]
&\qquad\times\frac{1}{\,2\sqrt{y}\,}
\end{aligned}
$$

</div>

<div class="topic-math-follow-before" markdown="1">

$$
[\,X<0\,]\quad Y=X^{2}
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop topic-math-follow" markdown="1">

$$
\Longrightarrow\ X=-\sqrt{Y}\ \text{且}\ \mathbf{J}=\frac{\,dx\,}{dy}=\frac{-1}{\,2\sqrt{y}\,},\ y\geqslant0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile topic-math-follow" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ X&=-\sqrt{Y}\\[0.35em]
\text{且}\ \mathbf{J}&=\frac{\,dx\,}{dy}=\frac{-1}{\,2\sqrt{y}\,},\ y\geqslant0
\end{aligned}
$$

</div>

知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
h^{**}(y\mid p)&=f(\sqrt{y}\mid p)\left\lvert\frac{-1}{\,2\sqrt{y}\,}\right\rvert\\[0.45em]
&=\frac{\Gamma\bigl(\frac{p+1}{2}\bigr)}{\,\Gamma\bigl(\frac{p}{2}\bigr)\sqrt{\pi p}\,}\biggl(1+\frac{\,y\,}{p}\biggr)^{-\frac{p+1}{2}}\times\frac{1}{\,2\sqrt{y}\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
h^{**}(y\mid p)&=f(\sqrt{y}\mid p)\left\lvert\frac{-1}{\,2\sqrt{y}\,}\right\rvert\\[0.3em]
&=\frac{\Gamma\bigl(\frac{p+1}{2}\bigr)}{\,\Gamma\bigl(\frac{p}{2}\bigr)\sqrt{\pi p}\,}\biggl(1+\frac{\,y\,}{p}\biggr)^{-\frac{p+1}{2}}\\[0.3em]
&\qquad\times\frac{1}{\,2\sqrt{y}\,}
\end{aligned}
$$

</div>

則
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
h(y\mid p)&=h^{*}(y\mid p)+h^{**}(y\mid p)\\[0.45em]
&=\frac{\Gamma\bigl(\frac{p+1}{2}\bigr)}{\,\Gamma\bigl(\frac{p}{2}\bigr)\Gamma\bigl(\frac{1}{2}\bigr)\,}\frac{1}{\,\sqrt{p}\,}\frac{y^{-\frac{1}{2}}}{\,\bigl(1+\frac{y}{p}\bigr)^{\frac{p+1}{2}}\,},\ y\geqslant0
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
h(y\mid p)&=h^{*}(y\mid p)+h^{**}(y\mid p)\\[0.3em]
&=\frac{\Gamma\bigl(\frac{p+1}{2}\bigr)}{\,\Gamma\bigl(\frac{p}{2}\bigr)\Gamma\bigl(\frac{1}{2}\bigr)\,}\frac{1}{\,\sqrt{p}\,}\\[0.3em]
&\qquad\frac{y^{-\frac{1}{2}}}{\,\bigl(1+\frac{y}{p}\bigr)^{\frac{p+1}{2}}\,},\ y\geqslant0
\end{aligned}
$$

</div>

(2) 由題意知，當 $a$ 很大時，我們有 $\Gamma(a+1)\fallingdotseq\sqrt{2\pi}a^{a+\frac{1}{2}}e^{-a}$ 的結果，故知當 $p$ 很大時
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\Gamma\biggl(\frac{p+1}{2}\biggr)&=\Gamma\biggl(\frac{p-1}{2}+1\biggr)\fallingdotseq\sqrt{2\pi}\biggl(\frac{p-1}{2}\biggr)^{\frac{p}{2}}e^{-\frac{p-1}{2}}\\[0.45em]
\Gamma\biggl(\frac{p}{2}\biggr)&=\Gamma\biggl(\frac{p-2}{2}+1\biggr)\fallingdotseq\sqrt{2\pi}\biggl(\frac{p-2}{2}\biggr)^{\frac{p-1}{2}}e^{-\frac{p-2}{2}}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\Gamma\biggl(\frac{p+1}{2}\biggr)&=\Gamma\biggl(\frac{p-1}{2}+1\biggr)\\[0.3em]
&\fallingdotseq\sqrt{2\pi}\biggl(\frac{p-1}{2}\biggr)^{\frac{p}{2}}e^{-\frac{p-1}{2}}\\[0.6em]
\Gamma\biggl(\frac{p}{2}\biggr)&=\Gamma\biggl(\frac{p-2}{2}+1\biggr)\\[0.3em]
&\fallingdotseq\sqrt{2\pi}\biggl(\frac{p-2}{2}\biggr)^{\frac{p-1}{2}}e^{-\frac{p-2}{2}}
\end{aligned}
$$

</div>

故可知道，當 $p$ 很大時，此時我們有
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f(x\mid p)&=\frac{\Gamma\bigl(\frac{p+1}{2}\bigr)}{\,\Gamma\bigl(\frac{p}{2}\bigr)\sqrt{\pi p}\,}\biggl(1+\frac{\,x^{2}\,}{p}\biggr)^{-\frac{p+1}{2}}\\[0.45em]
&=\frac{\sqrt{2\pi}\bigl(\frac{p-1}{2}\bigr)^{\frac{p}{2}}e^{-\frac{p-1}{2}}}{\,\sqrt{2\pi}\bigl(\frac{p-2}{2}\bigr)^{\frac{p-1}{2}}e^{-\frac{p-2}{2}}\,}\frac{1}{\,\sqrt{\pi p}\,}\biggl(1+\frac{x^{2}}{p}\biggr)^{-\frac{p+1}{2}}\\[0.45em]
&=\frac{e^{-\frac{1}{2}}}{\,\sqrt{2\pi}\,}\biggl(\frac{p-1}{p-2}\biggr)^{\frac{p-1}{2}}\frac{\,\sqrt{p-1}\,}{\sqrt{p}}\biggl(1+\frac{x^{2}}{p}\biggr)^{-\frac{p}{2}}\biggl(1+\frac{x^{2}}{p}\biggr)^{-\frac{1}{2}}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f(x\mid p)&=\frac{\Gamma\bigl(\frac{p+1}{2}\bigr)}{\,\Gamma\bigl(\frac{p}{2}\bigr)\sqrt{\pi p}\,}\biggl(1+\frac{\,x^{2}\,}{p}\biggr)^{-\frac{p+1}{2}}\\[0.3em]
&=\frac{\sqrt{2\pi}\bigl(\frac{p-1}{2}\bigr)^{\frac{p}{2}}e^{-\frac{p-1}{2}}}{\,\sqrt{2\pi}\bigl(\frac{p-2}{2}\bigr)^{\frac{p-1}{2}}e^{-\frac{p-2}{2}}\,}\\[0.3em]
&\qquad\frac{1}{\,\sqrt{\pi p}\,}\biggl(1+\frac{x^{2}}{p}\biggr)^{-\frac{p+1}{2}}\\[0.3em]
&=\frac{e^{-\frac{1}{2}}}{\,\sqrt{2\pi}\,}\biggl(\frac{p-1}{p-2}\biggr)^{\frac{p-1}{2}}\frac{\,\sqrt{p-1}\,}{\sqrt{p}}\\[0.3em]
&\qquad\biggl(1+\frac{x^{2}}{p}\biggr)^{-\frac{p}{2}}\biggl(1+\frac{x^{2}}{p}\biggr)^{-\frac{1}{2}}
\end{aligned}
$$

</div>

又由於
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\lim_{p\to\infty}\biggl(\frac{p-1}{p-2}\biggr)^{\frac{p-1}{2}}&=\lim_{p\to\infty}\biggl[\biggl(1+\frac{1}{\,p-2\,}\biggr)^{\frac{p-2}{2}}\times\biggl(1+\frac{1}{\,p-2\,}\biggr)^{\frac{1}{2}}\biggr]\\[0.45em]
&=\lim_{k\to\infty}\biggl[\biggl(1+\frac{1}{\,k\,}\biggr)^{k}\biggr]^{\frac{1}{2}}\times\lim_{p\to\infty}\biggl(1+\frac{1}{\,p-2\,}\biggr)^{\frac{1}{2}}\\[0.45em]
&=\bigl(e^{1}\bigr)^{\frac{1}{2}}\times1=e^{\frac{1}{2}}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\lim_{p\to\infty}\biggl(\frac{p-1}{p-2}\biggr)^{\frac{p-1}{2}}&=\lim_{p\to\infty}\biggl[\biggl(1+\frac{1}{\,p-2\,}\biggr)^{\frac{p-2}{2}}\\[0.3em]
&\qquad\times\biggl(1+\frac{1}{\,p-2\,}\biggr)^{\frac{1}{2}}\biggr]\\[0.3em]
&=\lim_{k\to\infty}\biggl[\biggl(1+\frac{1}{\,k\,}\biggr)^{k}\biggr]^{\frac{1}{2}}\\[0.3em]
&\qquad\times\lim_{p\to\infty}\biggl(1+\frac{1}{\,p-2\,}\biggr)^{\frac{1}{2}}\\[0.3em]
&=\bigl(e^{1}\bigr)^{\frac{1}{2}}\times1=e^{\frac{1}{2}}
\end{aligned}
$$

</div>

且
{: .topic-paren-cont}

$$
\begin{aligned}
\lim_{p\to\infty}\frac{\,\sqrt{p-1}\,}{\sqrt{p}}&=1\\[0.45em]
\lim_{p\to\infty}\biggl(1+\frac{x^{2}}{p}\biggr)^{-\frac{p}{2}}&=e^{-\frac{x^{2}}{2}}\\[0.45em]
\lim_{p\to\infty}\biggl(1+\frac{x^{2}}{p}\biggr)^{-\frac{1}{2}}&=1
\end{aligned}
$$

可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lim_{p\to\infty}f(x\mid p)=\frac{1}{\,\sqrt{2\pi}\,}e^{-\frac{x^{2}}{2}},\ -\infty<x<\infty
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\lim_{p\to\infty}f(x\mid p)&=\frac{1}{\,\sqrt{2\pi}\,}e^{-\frac{x^{2}}{2}},\\[0.3em]
&\qquad-\infty<x<\infty
\end{aligned}
$$

</div>

此即若 <span class="text-nowrap">$T\sim t(p)$，</span>則有
{: .topic-paren-cont}

$$
T\xrightarrow[~p\to\infty~]{\ \mathrm{d}\ }Z\sim\mathcal{N}(0,1)
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

事實上，上述提到關於當 $a$ 很大時，$\Gamma(a+1)\fallingdotseq\sqrt{2\pi}a^{a+\frac{1}{2}}e^{-a}$ 的結果，被稱為**史特靈公式 <span lang="en">(Stirling’s formula)</span>**，也經常被寫為

$$
\Gamma(n+1)\fallingdotseq\sqrt{2\pi n}\biggl(\frac{n}{\,e\,}\biggr)^{n}
$$

當 $n\in\mathbb{N}$ 且 $n$ 很大時。

這是一個經常用來求取 $n!$ 近似值的公式。由於當 $n$ 相當大時，由於階乘的運算量相當巨大，這個公式能夠節省相當多的計算功夫，而且雖然上面提到史特靈公式在 $n$ 很大時才能運作，但其實當 $n$ 很小的時候，史特靈公式的近似效果仍然相當不錯。

</div>

## 兩獨立樣本變異數比值的雙尾機率

<div id="ex-sampling-ex-2" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.59</div>

<div lang="en" markdown="1">
Suppose that two independent random samples, each of size <span class="text-nowrap">$6$,</span> are drawn from normal populations sharing a common variance <span class="text-nowrap">$\sigma^{2}$,</span> and let $W_1$ and $W_2$ denote the sample variances of the first and of the second sample respectively. Find the constant $k$ for which

$$
\mathbb{P}\biggl(\min\biggl\lbrace\frac{\,W_1\,}{W_2},\ \frac{\,W_2\,}{W_1}\biggr\rbrace<k\biggr)=0.10
$$
</div>

由題意可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}\biggl(\min\biggl\lbrace\frac{\,W_1\,}{W_2},\ \frac{\,W_2\,}{W_1}\biggr\rbrace<k\biggr)&=1-\mathbb{P}\biggl(\min\biggl\lbrace\frac{\,W_1\,}{W_2},\ \frac{\,W_2\,}{W_1}\biggr\rbrace\geqslant k\biggr)\\[0.45em]
&=1-\mathbb{P}\biggl(\frac{\,W_1\,}{W_2}\geqslant k,\ \frac{\,W_2\,}{W_1}\geqslant k\biggr)\\[0.45em]
&=1-\mathbb{P}\biggl(k\leqslant\frac{\,W_1\,}{W_2}\leqslant\frac{1}{\,k\,}\biggr)=0.1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}\biggl(&\min\biggl\lbrace\frac{\,W_1\,}{W_2},\ \frac{\,W_2\,}{W_1}\biggr\rbrace<k\biggr)\\[0.3em]
&=1-\mathbb{P}\biggl(\min\biggl\lbrace\frac{\,W_1\,}{W_2},\ \frac{\,W_2\,}{W_1}\biggr\rbrace\geqslant k\biggr)\\[0.3em]
&=1-\mathbb{P}\biggl(\frac{\,W_1\,}{W_2}\geqslant k,\ \frac{\,W_2\,}{W_1}\geqslant k\biggr)\\[0.3em]
&=1-\mathbb{P}\biggl(k\leqslant\frac{\,W_1\,}{W_2}\leqslant\frac{1}{\,k\,}\biggr)=0.1
\end{aligned}
$$

</div>

此即

$$
\mathbb{P}\biggl(k\leqslant\frac{\,W_1\,}{W_2}\leqslant\frac{1}{\,k\,}\biggr)=0.9
$$

且依照題意，$\frac{W_1}{\,W_2\,}\sim\mathcal{F}(5,5)$ [這個關係](/teaching-topics/snedecor-f-distribution/#thm-s-sq-ratio-samp-dist)成立，可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}\biggl(\mathcal{F}_{\sssig 0.95}(5,5)\leqslant\frac{\,W_1\,}{W_2}\leqslant\mathcal{F}_{\sssig 0.05}(5,5)\biggr)=0.9
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}\biggl(\mathcal{F}_{\sssig 0.95}(5,5)&\leqslant\frac{\,W_1\,}{W_2}\\[0.3em]
&\leqslant\mathcal{F}_{\sssig 0.05}(5,5)\biggr)=0.9
\end{aligned}
$$

</div>

又 $\mathcal{F}_{\sssig 0.05}(5,5)=\frac{1}{\,\mathcal{F}_{\sssig 0.95}(5,5)\,}$ [這個關係](/teaching-topics/sampling-distribution-tail-points/#thm-sampling-tail-relations)成立，故可知

$$
k=\mathcal{F}_{\sssig 0.95}(5,5)
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個問題有意思的地方在於，雖然表面上是單邊的尾機率，但事實上這個問題在問的問題是一個雙尾的機率；但要注意的是，由於分子自由度與分母自由度相同，這個問題中的 $\mathcal{F}$ 分配即使經過倒數也會是一樣的分配，因此才能夠用 $k$ 與 $\frac{1}{\,k\,}$ 來表示。

然而，雖然分子自由度與分母自由度不同時，我們不能如上表示，但若將上題改為 <span class="text-nowrap">$F=\frac{\,W_1\,}{W_2}\sim\mathcal{F}(\nu_1,\nu_2)$，</span>則考慮

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
&\mathbb{P}\bigl(\mathcal{F}_{\sssig 1-\frac{\alpha}{2}}(\nu_1,\nu_2)<F<\mathcal{F}_{\sssig \frac{\alpha}{2}}(\nu_1,\nu_2)\bigr)\\[0.45em]
&\mathbb{P}\biggl(\mathcal{F}_{\sssig 1-\frac{\alpha}{2}}(\nu_2,\nu_1)<\frac{1}{\,F\,}<\mathcal{F}_{\sssig \frac{\alpha}{2}}(\nu_2,\nu_1)\biggr)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}\bigl(&\mathcal{F}_{\sssig 1-\frac{\alpha}{2}}(\nu_1,\nu_2)\\[0.3em]
&<F<\mathcal{F}_{\sssig \frac{\alpha}{2}}(\nu_1,\nu_2)\bigr)\\[0.6em]
\mathbb{P}\biggl(&\mathcal{F}_{\sssig 1-\frac{\alpha}{2}}(\nu_2,\nu_1)\\[0.3em]
&<\frac{1}{\,F\,}<\mathcal{F}_{\sssig \frac{\alpha}{2}}(\nu_2,\nu_1)\biggr)
\end{aligned}
$$

</div>

兩者。由於 $\mathcal{F}$ 尾點的倒數關係，這兩個機率式事實上具有一模一樣的機率，範圍也完全等價，因此在進行應用統計學中，兩獨立母體變異數比值的雙尾 $\mathcal{F}$ 檢定時，部分教科書會指出，將兩個樣本變異數以較大的除以較小的作為檢定統計量，並永遠考慮右尾拒絕即可，這事實上是因為不論到時候得到的檢定統計量是誰除以誰，這個準則指出的範圍永遠可以對應到不指定大小時的雙尾範圍，因此在範圍等價的情況下會形成等價檢定。

</div>

## 本篇小結

[Example 4.58](#ex-sampling-ex-1) 把 $t$ 分配與 $\mathcal{F}$ 分配之間的關係，由機率函數的層次直接算了一次。第一小題的轉換 $Y=X^{2}$ 不是一對一，因此把 $X$ 的值域分成 $X\geqslant0$ 與 $X<0$ 兩段，兩段各自以 Jacobian 法轉換之後得到 $h^{*}(y\mid p)$ 與 <span class="text-nowrap">$h^{**}(y\mid p)$，</span>兩者相加即為 $Y$ 的機率函數。由於 $t$ 分配的機率函數只透過 $x^{2}$ 依賴 <span class="text-nowrap">$x$，</span>兩段所得到的結果完全相同，相加之後恰好把 $\sqrt{\pi p}$ 中的 $\sqrt{\pi}$ 併成 <span class="text-nowrap">$\Gamma\bigl(\frac{1}{2}\bigr)$，</span>得到的正是第一自由度為 $1$、第二自由度為 $p$ 的 $\mathcal{F}$ 分配之機率函數。

第二小題處理的是自由度趨於無窮時的情形。作法是先以史特靈公式把 $\Gamma\bigl(\frac{p+1}{2}\bigr)$ 與 $\Gamma\bigl(\frac{p}{2}\bigr)$ 兩者換成初等函數，整理之後 $f(x\mid p)$ 成為四個因子的乘積: $\bigl(\frac{p-1}{p-2}\bigr)^{\frac{p-1}{2}}$ 這個因子的極限由 $\bigl(1+\frac{1}{k}\bigr)^{k}\to e$ 得到 <span class="text-nowrap">$e^{\frac{1}{2}}$，</span>恰與前面的 $e^{-\frac{1}{2}}$ 相消；$\frac{\sqrt{p-1}}{\sqrt{p}}$ 與 $\bigl(1+\frac{x^{2}}{p}\bigr)^{-\frac{1}{2}}$ 兩者的極限都是 <span class="text-nowrap">$1$；</span>只有 $\bigl(1+\frac{x^{2}}{p}\bigr)^{-\frac{p}{2}}$ 留下 $e^{-\frac{x^{2}}{2}}$ 這一項。四個因子的極限與 $\frac{1}{\,\sqrt{2\pi}\,}$ 這個常數合起來，正是[標準常態分配](/teaching-topics/normal-distribution/#def-normal)的機率函數，此即 $t$ 分配在自由度趨於無窮時[分配收斂](/teaching-topics/convergence-in-distribution/#def-converge-in-distribution) <span lang="en">(convergence in distribution)</span> 至標準常態分配。

[Example 4.59](#ex-sampling-ex-2) 的關鍵在於把事件寫對。$\min\bigl\lbrace\frac{W_1}{W_2},\frac{W_2}{W_1}\bigr\rbrace\geqslant k$ 這個事件等價於兩個比值都不小於 <span class="text-nowrap">$k$，</span>也就是 $k\leqslant\frac{W_1}{W_2}\leqslant\frac{1}{k}$ 這一段區間，因此表面上的單邊尾機率其實是雙尾機率。兩個樣本各有 $6$ 個觀測值，兩個樣本變異數的比值因而服從 $\mathcal{F}(5,5)$ 這個分配，而區間的兩個端點又互為倒數，正好對上 $\mathcal{F}$ 尾點的倒數關係，所求的常數即為 <span class="text-nowrap">$\mathcal{F}_{\sssig 0.95}(5,5)$。</span>之後那則註記進一步指出，分子自由度與分母自由度不同時雖然不能再以 $k$ 與 $\frac{1}{k}$ 兩者表示兩個端點，但同一條倒數關係仍然使兩種寫法的範圍完全等價，這正是應用統計學在做兩獨立母體變異數比值的檢定時，可以永遠把較大的樣本變異數放在分子而只看右尾的原因。

常用抽樣分配的部分至此告一段落。[下一篇](/teaching-topics/bivariate-normal-distribution/)轉入二元常態分配，由兩個常態隨機變數組成的聯合分配開始，給出它的定義與各項性質。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
