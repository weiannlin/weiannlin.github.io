---
title: "標準常態的各階原動差與斯泰因引理"
subtitle: "Moments of the Standard Normal and Stein’s Lemma"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 4
topic: 19
order: 419
permalink: /teaching-topics/standard-normal-moments-stein-lemma/
date: 2026-08-15
published: false
excerpt: "本篇先以兩道例題示範標準常態變數的隨機組合: 一是以取值為 $1$ 與 $-1$ 的隨機正負號乘上標準常態變數，所得的變數仍為標準常態分配，與原變數零相關卻不獨立；二是以隨機的權數組合兩個獨立的標準常態變數，由條件分配與條件動差母函數兩種作法都可判定其仍為標準常態分配。接著把 $e^{\\frac{t^{2}}{2}}$ 展成馬克勞林級數並與動差級數比較係數，得到標準常態分配的各階原動差在 $k$ 為偶數時為 $\\frac{k!}{2^{\\frac{k}{2}}(\\frac{k}{2})!}$、在 $k$ 為奇數時為 $0$。一般常態分配的高階動差若循反標準化計算相當繁複，斯泰因引理提供了另一條路: 對 $X\\sim\\mathcal{N}(\\mu,\\sigma^{2})$ 與可微函數 $g$，有 $\\mathbb{E}[g(X)(X-\\mu)]=\\sigma^{2}\\mathbb{E}[g^{\\prime}(X)]$，證明用的是分部積分。最後以 $\\mathbb{E}[Z\\Phi(Z)]$ 與 $\\mathbb{E}[Z^{2}\\Phi(Z)]$ 兩個期望值演練這條引理。"
---

[上一篇](/teaching-topics/normal-probability-computation/)以四道例題演練常態機率的計算。本篇仍以[常態分配](/teaching-topics/normal-distribution/#def-normal)為對象，但把重心由機率的計算轉到動差的求算。

先看兩道例題。第一道把標準常態變數乘上一個取值為 $1$ 與 $-1$ 的隨機正負號，所得的變數仍然是標準常態分配，卻與原變數零相關而不獨立；第二道以隨機的權數把兩個獨立的標準常態變數組合起來，所得的變數同樣是標準常態分配。兩道題的作法都是先固定第三個變數的取值，再由條件分配或條件[動差母函數](/teaching-topics/moment-generating-functions/#def-mgf)還原原來的分配。

接著給出標準常態分配的各階原動差，作法是把動差母函數展成[馬克勞林級數](/teaching-topics/poisson-process-and-distribution/#thm-maclaurin-series)，再與動差級數比較係數。一般常態分配的高階動差雖然可以由此進行反標準化計算，過程卻相當繁複，因此最後給出斯泰因引理: 它把 $g(X)$ 與 $X-\mu$ 相乘的期望值換成 $g^{\prime}(X)$ 的期望值，高階動差便可以逐階遞推。

## 標準常態變數的隨機組合

<div id="ex-normal-moments-1" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.48</div>

<div lang="en" markdown="1">
Suppose that $X$ is a normal random variable with mean $0$ and variance $1$, and that $Z$ is a random variable independent of $X$ with $\mathbb{P}(Z=1)=\frac{1}{\,2\,}$ and <span class="text-nowrap">$\mathbb{P}(Z=-1)=\frac{1}{\,2\,}$.</span> Define <span class="text-nowrap">$Y=Z\cdot X$,</span> so that $Y$ equals $X$ when $Z=1$ and equals $-X$ when <span class="text-nowrap">$Z=-1$.</span>

<ol class="topic-list-paren">
  <li>Determine whether $X$ and $Y$ are independent.</li>
  <li>Determine whether $Z$ and $Y$ are independent.</li>
  <li>Show that $Y$ is a normal random variable with mean $0$ and variance $1$.</li>
  <li>Show that $\operatorname{Cov}(X,Y)=0$.</li>
</ol>
</div>

(1) 先計算一特殊的條件期望值備用
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl(e^{tX+sY}\mid Z=z\bigr)&=\mathbb{E}\bigl(e^{tX+szX}\mid Z=z\bigr)=\mathbb{E}\bigl[e^{(t+sz)X}\bigr]\qquad(\,\because\ X\indep Z\,)\\[0.45em]
&=M_{\sssig X}(t+sz)=e^{\frac{\,(t+sz)^{2}\,}{2}},\ t,s\in\mathbb{R},\ \text{且}\ z=1,-1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl(e^{tX+sY}\mid Z=z\bigr)&=\mathbb{E}\bigl(e^{tX+szX}\mid Z=z\bigr)\\[0.3em]
&=\mathbb{E}\bigl[e^{(t+sz)X}\bigr]\\[0.2em]
&\qquad\qquad(\,\because\ X\indep Z\,)\\[0.3em]
&=M_{\sssig X}(t+sz)=e^{\frac{\,(t+sz)^{2}\,}{2}},\\[0.2em]
&\qquad t,s\in\mathbb{R},\ \text{且}\ z=1,-1
\end{aligned}
$$

</div>

由[雙重期望值定理](/teaching-topics/double-expectation-theorem/#thm-double-expectation)可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{\sssig XY}(t,s)&=\mathbb{E}\Bigl[\mathbb{E}\bigl(e^{tX+sY}\mid Z\bigr)\Bigr]=\mathbb{E}\left[e^{\frac{\,(t+sZ)^{2}\,}{2}}\right]=\frac{1}{\,2\,}e^{\frac{\,(t+s)^{2}\,}{2}}+\frac{1}{\,2\,}e^{\frac{\,(t-s)^{2}\,}{2}}\\[0.45em]
&=\frac{1}{\,2\,}\left[e^{\frac{\,(t+s)^{2}\,}{2}}+e^{\frac{\,(t-s)^{2}\,}{2}}\right],\ t,s\in\mathbb{R}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig XY}(t,s)&=\mathbb{E}\Bigl[\mathbb{E}\bigl(e^{tX+sY}\mid Z\bigr)\Bigr]\\[0.3em]
&=\mathbb{E}\left[e^{\frac{\,(t+sZ)^{2}\,}{2}}\right]\\[0.3em]
&=\frac{1}{\,2\,}e^{\frac{\,(t+s)^{2}\,}{2}}+\frac{1}{\,2\,}e^{\frac{\,(t-s)^{2}\,}{2}}\\[0.3em]
&=\frac{1}{\,2\,}\left[e^{\frac{\,(t+s)^{2}\,}{2}}+e^{\frac{\,(t-s)^{2}\,}{2}}\right],\\[0.2em]
&\qquad t,s\in\mathbb{R}
\end{aligned}
$$

</div>

又由[邊際動差母函數](/teaching-topics/cross-moments-joint-mgf/#thm-marginal-mgf)可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{\sssig X}(t)&=M_{\sssig XY}(t,0)=e^{\frac{\,t^{2}\,}{2}},\ t\in\mathbb{R}\\[0.45em]
M_{\sssig Y}(s)&=M_{\sssig XY}(0,s)=e^{\frac{\,s^{2}\,}{2}},\ s\in\mathbb{R}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig X}(t)&=M_{\sssig XY}(t,0)=e^{\frac{\,t^{2}\,}{2}},\ t\in\mathbb{R}\\[0.45em]
M_{\sssig Y}(s)&=M_{\sssig XY}(0,s)=e^{\frac{\,s^{2}\,}{2}},\ s\in\mathbb{R}
\end{aligned}
$$

</div>

則由 $M_{\sssig XY}(t,s)\neq M_{\sssig X}(t)\,M_{\sssig Y}(s)$ 知
{: .topic-paren-cont}

$$
X\not\indep Y
$$

(2) 先計算一特殊的條件期望值備用
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl(e^{tZ+sY}\mid Z=z\bigr)&=\mathbb{E}\bigl(e^{tz+szX}\mid Z=z\bigr)=e^{tz}\,\mathbb{E}\bigl[e^{szX}\bigr]\qquad(\,\because\ X\indep Z\,)\\[0.45em]
&=e^{tz}M_{\sssig X}(sz)=e^{tz}e^{\frac{\,(sz)^{2}\,}{2}},\ t,s\in\mathbb{R},\ \text{且}\ z=1,-1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl(e^{tZ+sY}\mid Z=z\bigr)&=\mathbb{E}\bigl(e^{tz+szX}\mid Z=z\bigr)\\[0.3em]
&=e^{tz}\,\mathbb{E}\bigl[e^{szX}\bigr]\\[0.2em]
&\qquad\qquad(\,\because\ X\indep Z\,)\\[0.3em]
&=e^{tz}M_{\sssig X}(sz)=e^{tz}e^{\frac{\,(sz)^{2}\,}{2}},\\[0.2em]
&\qquad t,s\in\mathbb{R},\ \text{且}\ z=1,-1
\end{aligned}
$$

</div>

由雙重期望值定理可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{\sssig ZY}(t,s)&=\mathbb{E}\Bigl[\mathbb{E}\bigl(e^{tZ+sY}\mid Z\bigr)\Bigr]=\mathbb{E}\left[e^{tZ}e^{\frac{\,(sZ)^{2}\,}{2}}\right]=\frac{1}{\,2\,}e^{t}e^{\frac{\,s^{2}\,}{2}}+\frac{1}{\,2\,}e^{-t}e^{\frac{\,s^{2}\,}{2}}\\[0.45em]
&=\frac{1}{\,2\,}e^{\frac{\,s^{2}\,}{2}}\left[e^{t}+e^{-t}\right],\ t,s\in\mathbb{R}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig ZY}(t,s)&=\mathbb{E}\Bigl[\mathbb{E}\bigl(e^{tZ+sY}\mid Z\bigr)\Bigr]\\[0.3em]
&=\mathbb{E}\left[e^{tZ}e^{\frac{\,(sZ)^{2}\,}{2}}\right]\\[0.3em]
&=\frac{1}{\,2\,}e^{t}e^{\frac{\,s^{2}\,}{2}}+\frac{1}{\,2\,}e^{-t}e^{\frac{\,s^{2}\,}{2}}\\[0.3em]
&=\frac{1}{\,2\,}e^{\frac{\,s^{2}\,}{2}}\left[e^{t}+e^{-t}\right],\\[0.2em]
&\qquad t,s\in\mathbb{R}
\end{aligned}
$$

</div>

又由邊際動差母函數可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{\sssig Z}(t)&=M_{\sssig ZY}(t,0)=\frac{1}{\,2\,}\left[e^{t}+e^{-t}\right],\ t\in\mathbb{R}\\[0.45em]
M_{\sssig Y}(s)&=M_{\sssig ZY}(0,s)=e^{\frac{\,s^{2}\,}{2}},\ s\in\mathbb{R}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig Z}(t)&=M_{\sssig ZY}(t,0)\\[0.2em]
&=\frac{1}{\,2\,}\left[e^{t}+e^{-t}\right],\ t\in\mathbb{R}\\[0.45em]
M_{\sssig Y}(s)&=M_{\sssig ZY}(0,s)=e^{\frac{\,s^{2}\,}{2}},\ s\in\mathbb{R}
\end{aligned}
$$

</div>

則由 $M_{\sssig ZY}(t,s)=M_{\sssig Z}(t)\,M_{\sssig Y}(s)$ 知
{: .topic-paren-cont}

$$
Z\indep Y
$$

(3) 由前述結果可知 <span class="text-nowrap">$M_{\sssig Y}(s)=M_{\sssig ZY}(0,s)=e^{\frac{\,s^{2}\,}{2}},\ s\in\mathbb{R}$，</span>此即
{: .topic-paren-item}

$$
Y\sim\mathcal{N}(0,1)
$$

(4) 我們有
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\operatorname{Cov}(X,Y)&=\mathbb{E}\bigl[\operatorname{Cov}(X,ZX\mid Z)\bigr]\\[0.45em]
&=\frac{1}{\,2\,}\operatorname{Cov}(X,X\mid Z=1)+\frac{1}{\,2\,}\operatorname{Cov}(X,-X\mid Z=-1)=0
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\operatorname{Cov}(X,Y)&=\mathbb{E}\bigl[\operatorname{Cov}(X,ZX\mid Z)\bigr]\\[0.3em]
&=\frac{1}{\,2\,}\operatorname{Cov}(X,X\mid Z=1)\\[0.2em]
&\qquad+\frac{1}{\,2\,}\operatorname{Cov}(X,-X\mid Z=-1)\\[0.3em]
&=0
\end{aligned}
$$

</div>

**[ 另解 ]**
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(XY)=\mathbb{E}(X\cdot ZX)=\mathbb{E}(Z)\mathbb{E}(X^{2})=0\qquad(\,\because\ Z\indep X\ \text{且}\ \mathbb{E}(Z)=0\,)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(XY)&=\mathbb{E}(X\cdot ZX)=\mathbb{E}(Z)\mathbb{E}(X^{2})=0\\[0.2em]
&\qquad(\,\because\ Z\indep X\ \text{且}\ \mathbb{E}(Z)=0\,)
\end{aligned}
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\operatorname{Cov}(X,Y)=\mathbb{E}(XY)-\mathbb{E}(X)\mathbb{E}(Y)=0\qquad(\,\because\ \mathbb{E}(X)=0\,)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\operatorname{Cov}(X,Y)&=\mathbb{E}(XY)-\mathbb{E}(X)\mathbb{E}(Y)=0\\[0.2em]
&\qquad(\,\because\ \mathbb{E}(X)=0\,)
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

此一問題的設定也是一個「零相關但不獨立」的例子，除了經典的[梅花座](/teaching-topics/covariance/#ex-uncorrelated-not-independent)一例之外，讀者亦可以此例參考。

</div>

<div id="ex-normal-moments-2" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.49</div>

<div lang="en" markdown="1">
Suppose that $X$, $Y$ and $Z$ are independent and identically distributed random variables, each having the $\mathcal{N}(0,1)$ distribution. Determine the distribution of

$$
W=\frac{\,X+YZ\,}{\,\sqrt{1+Z^{2}}\,}
$$

[Hint: work with the conditional distribution of $W$ given <span class="text-nowrap">$Z=z$.]</span>
</div>

令

$$
W=\frac{\,X+YZ\,}{\,\sqrt{1+Z^{2}}\,}
$$

**[ 法一 ]**

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
W\mid(Z=z)=\frac{\,1\cdot X+z\cdot Y\,}{\sqrt{1+z^{2}}}=\frac{1}{\,\sqrt{1+z^{2}}\,}X+\frac{z}{\,\sqrt{1+z^{2}}\,}Y\sim\mathcal{N}(0,1)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
W\mid(Z=z)&=\frac{\,1\cdot X+z\cdot Y\,}{\sqrt{1+z^{2}}}\\[0.3em]
&=\frac{1}{\,\sqrt{1+z^{2}}\,}X+\frac{z}{\,\sqrt{1+z^{2}}\,}Y\\[0.3em]
&\sim\mathcal{N}(0,1)
\end{aligned}
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\left(\because\ \left(\frac{1}{\,\sqrt{1+z^{2}}\,}\right)^{2}+\left(\frac{z}{\,\sqrt{1+z^{2}}\,}\right)^{2}=1,\ \text{且}\ X\indep Y\right)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\Biggl(\because\ &\left(\frac{1}{\,\sqrt{1+z^{2}}\,}\right)^{2}\\[0.2em]
&\qquad+\left(\frac{z}{\,\sqrt{1+z^{2}}\,}\right)^{2}=1,\\[0.3em]
&\text{且}\ X\indep Y\Biggr)
\end{aligned}
$$

</div>

由此可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ f_{\sssig W\mid(Z=z)}(w\mid z)&=\phi(w)\\[0.45em]
\text{且}\ f_{\sssig WZ}(w,z)&=f_{\sssig W\mid(Z=z)}(w\mid z)f_{\sssig Z}(z)=\phi(w)\phi(z)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ f_{\sssig W\mid(Z=z)}(w\mid z)&=\phi(w)\\[0.45em]
\text{且}\ f_{\sssig WZ}(w,z)&=f_{\sssig W\mid(Z=z)}(w\mid z)f_{\sssig Z}(z)\\[0.2em]
&=\phi(w)\phi(z)
\end{aligned}
$$

</div>

由此可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ f_{\sssig W}(w)&=\int_{-\infty}^{\infty}f_{\sssig WZ}(w,z)\,dz=\int_{-\infty}^{\infty}\phi(w)\phi(z)\,dz\\[0.45em]
&=\phi(w)\times\int_{-\infty}^{\infty}\phi(z)\,dz=\phi(w)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ f_{\sssig W}(w)&=\int_{-\infty}^{\infty}f_{\sssig WZ}(w,z)\,dz\\[0.3em]
&=\int_{-\infty}^{\infty}\phi(w)\phi(z)\,dz\\[0.3em]
&=\phi(w)\times\int_{-\infty}^{\infty}\phi(z)\,dz\\[0.3em]
&=\phi(w)
\end{aligned}
$$

</div>

故

$$
W\sim\mathcal{N}(0,1)
$$

**[ 法二 ]**

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
M_{\sssig W}(t)=\mathbb{E}\bigl(e^{tW}\bigr)=\mathbb{E}\left(e^{t\frac{X+YZ}{\sqrt{1+Z^{2}}}}\right)=\mathbb{E}\left[\mathbb{E}\left(e^{t\frac{X+YZ}{\sqrt{1+Z^{2}}}}\Bigm\vert Z\right)\right]
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig W}(t)&=\mathbb{E}\bigl(e^{tW}\bigr)=\mathbb{E}\left(e^{t\frac{X+YZ}{\sqrt{1+Z^{2}}}}\right)\\[0.3em]
&=\mathbb{E}\left[\mathbb{E}\left(e^{t\frac{X+YZ}{\sqrt{1+Z^{2}}}}\Bigm\vert Z\right)\right]
\end{aligned}
$$

</div>

其中

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\left(e^{t\frac{X+YZ}{\sqrt{1+Z^{2}}}}\Bigm\vert Z=z\right)&=\mathbb{E}\left(e^{t\frac{X+Yz}{\sqrt{1+z^{2}}}}\Bigm\vert Z=z\right)=\mathbb{E}\left(e^{t\frac{X+Yz}{\sqrt{1+z^{2}}}}\right)\\[0.45em]
&=\mathbb{E}\left(e^{\frac{t}{\sqrt{1+z^{2}}}X}\right)\mathbb{E}\left(e^{\frac{tz}{\sqrt{1+z^{2}}}Y}\right)=e^{\frac{\frac{t^{2}}{1+z^{2}}}{2}}e^{\frac{\frac{t^{2}z^{2}}{1+z^{2}}}{2}}=e^{\frac{t^{2}}{2}}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\left(e^{t\frac{X+YZ}{\sqrt{1+Z^{2}}}}\Bigm\vert Z=z\right)&=\mathbb{E}\left(e^{t\frac{X+Yz}{\sqrt{1+z^{2}}}}\Bigm\vert Z=z\right)\\[0.3em]
&=\mathbb{E}\left(e^{t\frac{X+Yz}{\sqrt{1+z^{2}}}}\right)\\[0.3em]
&=\mathbb{E}\left(e^{\frac{t}{\sqrt{1+z^{2}}}X}\right)\mathbb{E}\left(e^{\frac{tz}{\sqrt{1+z^{2}}}Y}\right)\\[0.3em]
&=e^{\frac{\frac{t^{2}}{1+z^{2}}}{2}}e^{\frac{\frac{t^{2}z^{2}}{1+z^{2}}}{2}}=e^{\frac{t^{2}}{2}}
\end{aligned}
$$

</div>

故

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
M_{\sssig W}(t)=\mathbb{E}\left[\mathbb{E}\left(e^{t\frac{X+YZ}{\sqrt{1+Z^{2}}}}\Bigm\vert Z\right)\right]=\mathbb{E}\left[e^{\frac{t^{2}}{2}}\right]=e^{\frac{t^{2}}{2}}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig W}(t)&=\mathbb{E}\left[\mathbb{E}\left(e^{t\frac{X+YZ}{\sqrt{1+Z^{2}}}}\Bigm\vert Z\right)\right]\\[0.3em]
&=\mathbb{E}\left[e^{\frac{t^{2}}{2}}\right]=e^{\frac{t^{2}}{2}}
\end{aligned}
$$

</div>

由 [mgf 唯一性](/teaching-topics/uniqueness-of-the-mgf/#thm-mgf-uniqueness)可知

$$
W\sim\mathcal{N}(0,1)
$$

</div>

## 標準常態分配的各階原動差

<div id="thm-standard-normal-moments" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 4.21 (標準常態的各階原動差, moments of the standard normal)</div>

令 <span class="text-nowrap">$Z\sim\mathcal{N}(0,1)$，</span>若且唯若 $Z$ 之各階原動差為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(Z^{k})=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{k!}{\,2^{\frac{k}{2}}\bigl(\frac{k}{2}\bigr)!\,}, & \text{$k$ 為偶數}\\[1.1em]
0, & \text{$k$ 為奇數}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases">
  <div class="topic-cases__lhs">$\mathbb{E}(Z^{k})=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$\dfrac{k!}{\,2^{\frac{k}{2}}\bigl(\frac{k}{2}\bigr)!\,},$</div>
    <div class="topic-cases__cond">$k$ 為偶數</div>
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$k$ 為奇數</div>
  </div>
</div>

</div>

</div>

<div class="topic-proof" markdown="1">
**Proof.**

由 $Z\sim\mathcal{N}(0,1)$ 可知 <span class="text-nowrap">$M_{\sssig Z}(t)=e^{\frac{\,t^{2}\,}{2}},\ t\in\mathbb{R}$，</span>則由馬克勞林級數可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{\sssig Z}(t)&=1+\frac{\,\frac{\,t^{2}\,}{2}\,}{1!}+\frac{\,\bigl(\frac{\,t^{2}\,}{2}\bigr)^{2}\,}{2!}+\frac{\,\bigl(\frac{\,t^{2}\,}{2}\bigr)^{3}\,}{3!}+\cdots\\[0.45em]
&=1+\frac{\,t^{2}\,}{\,2\cdot 1!\,}+\frac{\,t^{4}\,}{\,2^{2}\cdot 2!\,}+\frac{\,t^{6}\,}{\,2^{3}\cdot 3!\,}+\cdots
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig Z}(t)&=1+\frac{\,\frac{\,t^{2}\,}{2}\,}{1!}+\frac{\,\bigl(\frac{\,t^{2}\,}{2}\bigr)^{2}\,}{2!}+\frac{\,\bigl(\frac{\,t^{2}\,}{2}\bigr)^{3}\,}{3!}+\cdots\\[0.45em]
&=1+\frac{\,t^{2}\,}{\,2\cdot 1!\,}+\frac{\,t^{4}\,}{\,2^{2}\cdot 2!\,}+\frac{\,t^{6}\,}{\,2^{3}\cdot 3!\,}+\cdots
\end{aligned}
$$

</div>

又由 [Theorem 2.22](/teaching-topics/moment-generating-functions/#thm-mgf-moment-series) 可知 <span class="text-nowrap">$M_{\sssig Z}(t)=\sum_{k=0}^{\infty}\mathbb{E}(Z^{k})\frac{\,t^{k}\,}{k!}$，</span>由比較係數法可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(Z^{k})=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{k!}{\,2^{\frac{k}{2}}\bigl(\frac{k}{2}\bigr)!\,}, & \text{$k$ 為偶數}\\[1.1em]
0, & \text{$k$ 為奇數}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases">
  <div class="topic-cases__lhs">$\mathbb{E}(Z^{k})=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$\dfrac{k!}{\,2^{\frac{k}{2}}\bigl(\frac{k}{2}\bigr)!\,},$</div>
    <div class="topic-cases__cond">$k$ 為偶數</div>
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$k$ 為奇數</div>
  </div>
</div>

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

事實上，這個性質在 [Example 2.33](/teaching-topics/uniqueness-of-the-mgf/#ex-normal-moments-to-pdf) 中就已經見到過了，在此處就不再重新探究，讀者可以翻回去看看其結果。

</div>

上述定理是一個關於標準常態分配各階原動差的定理，一般的常態分配雖然可以由此進行反標準化計算，然計算過程卻相當不容易。

事實上，由於常態分配的分配核心 (kernel) 的緣故，當牽涉到計算常態分配的動差時，若不經過繁複的運算，求算的過程往往很困難。但所幸，我們可以利用下面將要提到的這個定理，來協助我們進行高階動差的求算。

## 斯泰因引理

<div id="thm-stein-lemma" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 4.22 (斯泰因引理, Stein’s Lemma)</div>

令 <span class="text-nowrap">$X\sim\mathcal{N}(\mu,\sigma^{2})$，</span>且 $g(x)$ 為可微函數，並滿足 <span class="text-nowrap">$\mathbb{E}\bigl[g^{\prime}(X)\bigr]<\infty$，</span>則

$$
\mathbb{E}\bigl[g(X)(X-\mu)\bigr]=\sigma^{2}\,\mathbb{E}\bigl[g^{\prime}(X)\bigr]
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.**

由期望值的定義可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[g(X)(X-\mu)\bigr]&=\int_{-\infty}^{\infty}g(x)(x-\mu)\frac{1}{\,\sqrt{2\pi\sigma^{2}}\,}e^{-\frac{\,(x-\mu)^{2}\,}{2\sigma^{2}}}\,dx\\[0.45em]
&=\frac{-\sigma^{2}}{\,\sqrt{2\pi\sigma^{2}}\,}\int_{-\infty}^{\infty}g(x)\frac{\,-(x-\mu)\,}{\sigma^{2}}e^{-\frac{\,(x-\mu)^{2}\,}{2\sigma^{2}}}\,dx\\[0.45em]
&=\frac{-\sigma^{2}}{\,\sqrt{2\pi\sigma^{2}}\,}\int_{-\infty}^{\infty}g(x)\,d\!\left(e^{-\frac{\,(x-\mu)^{2}\,}{2\sigma^{2}}}\right)\\[0.45em]
&=\left[\frac{-\sigma^{2}}{\,\sqrt{2\pi\sigma^{2}}\,}g(x)e^{-\frac{\,(x-\mu)^{2}\,}{2\sigma^{2}}}\right]^{\infty}_{-\infty}-\frac{-\sigma^{2}}{\,\sqrt{2\pi\sigma^{2}}\,}\int_{-\infty}^{\infty}e^{-\frac{\,(x-\mu)^{2}\,}{2\sigma^{2}}}\,dg(x)\\[0.45em]
&=0+\sigma^{2}\int_{-\infty}^{\infty}g^{\prime}(x)\frac{1}{\,\sqrt{2\pi\sigma^{2}}\,}e^{-\frac{\,(x-\mu)^{2}\,}{2\sigma^{2}}}\,dx\\[0.45em]
&=\sigma^{2}\,\mathbb{E}\bigl[g^{\prime}(X)\bigr]
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[g(X)(X-\mu)\bigr]&=\int_{-\infty}^{\infty}g(x)(x-\mu)\\[0.2em]
&\qquad\frac{1}{\,\sqrt{2\pi\sigma^{2}}\,}e^{-\frac{\,(x-\mu)^{2}\,}{2\sigma^{2}}}\,dx\\[0.45em]
&=\frac{-\sigma^{2}}{\,\sqrt{2\pi\sigma^{2}}\,}\int_{-\infty}^{\infty}g(x)\\[0.2em]
&\qquad\frac{\,-(x-\mu)\,}{\sigma^{2}}e^{-\frac{\,(x-\mu)^{2}\,}{2\sigma^{2}}}\,dx\\[0.45em]
&=\frac{-\sigma^{2}}{\,\sqrt{2\pi\sigma^{2}}\,}\int_{-\infty}^{\infty}g(x)\\[0.2em]
&\qquad\,d\!\left(e^{-\frac{\,(x-\mu)^{2}\,}{2\sigma^{2}}}\right)\\[0.45em]
&=\left[\frac{-\sigma^{2}}{\,\sqrt{2\pi\sigma^{2}}\,}g(x)e^{-\frac{\,(x-\mu)^{2}\,}{2\sigma^{2}}}\right]^{\infty}_{-\infty}\\[0.25em]
&\qquad-\frac{-\sigma^{2}}{\,\sqrt{2\pi\sigma^{2}}\,}\\[0.2em]
&\qquad\qquad\int_{-\infty}^{\infty}e^{-\frac{\,(x-\mu)^{2}\,}{2\sigma^{2}}}\,dg(x)\\[0.45em]
&=0+\sigma^{2}\int_{-\infty}^{\infty}g^{\prime}(x)\\[0.2em]
&\qquad\frac{1}{\,\sqrt{2\pi\sigma^{2}}\,}e^{-\frac{\,(x-\mu)^{2}\,}{2\sigma^{2}}}\,dx\\[0.45em]
&=\sigma^{2}\,\mathbb{E}\bigl[g^{\prime}(X)\bigr]
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<!-- ref-point: 斯泰因估計量在估計理論才出現，目前站上沒有對應的頁面，故下面這則 Note 中的
     這一處只留文字不掛連結。日後該篇寫成之後，回填為指向該篇 anchor 的站內連結。 -->

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

在上述的證明當中，$\mathbb{E}\bigl[g^{\prime}(X)\bigr]<\infty$ 的條件即保證

$$
\lim_{x\to\pm\infty}g(x)e^{-\frac{\,(x-\mu)^{2}\,}{2\sigma^{2}}}=0
$$

故在分部積分的過程中，我們有

$$
\left[\frac{-\sigma^{2}}{\,\sqrt{2\pi\sigma^{2}}\,}g(x)e^{-\frac{\,(x-\mu)^{2}\,}{2\sigma^{2}}}\right]^{\infty}_{-\infty}=0
$$

亦有教科書直接將該條件改為 <span class="text-nowrap">$\lim_{x\to\pm\infty}g(x)e^{-\frac{\,(x-\mu)^{2}\,}{2\sigma^{2}}}=0$。</span>

斯泰因引理 (Stein’s Lemma) 是為了紀念斯泰因 (Charles M. Stein, 1920 - 2016) 而以他的姓氏命名，[^stein-himself] 這個引理在數理統計學中，能夠有效搭配[中央極限定理](/teaching-topics/weak-law-and-central-limit-theorem/#thm-central-limit-theorem)的結果，求算任意隨機變數的近似動差，在投資組合選擇理論、斯泰因估計量 <span lang="en">(Stein’s estimator)</span> 與經驗貝氏法 <span lang="en">(empirical Bayes)</span> 等領域應用極廣。

此處的使用將以常態分配的高階動差為主，例如，若 <span class="text-nowrap">$X\sim\mathcal{N}(\mu,\sigma^{2})$，</span>則

$$
\mathbb{E}\bigl[X^{2}(X-\mu)\bigr]=\sigma^{2}\mathbb{E}(2X)=2\mu\sigma^{2}
$$

又因為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[X^{2}(X-\mu)\bigr]&=\mathbb{E}\bigl(X^{3}-\mu X^{2}\bigr)=\mathbb{E}\bigl(X^{3}\bigr)-\mu\bigl(\sigma^{2}+\mu^{2}\bigr)\\[0.45em]
&=\mathbb{E}\bigl(X^{3}\bigr)-\mu\sigma^{2}-\mu^{3}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[X^{2}(X-\mu)\bigr]&=\mathbb{E}\bigl(X^{3}-\mu X^{2}\bigr)\\[0.3em]
&=\mathbb{E}\bigl(X^{3}\bigr)-\mu\bigl(\sigma^{2}+\mu^{2}\bigr)\\[0.3em]
&=\mathbb{E}\bigl(X^{3}\bigr)-\mu\sigma^{2}-\mu^{3}
\end{aligned}
$$

</div>

可知

$$
2\mu\sigma^{2}=\mathbb{E}\bigl(X^{3}\bigr)-\mu\sigma^{2}-\mu^{3}\qquad\therefore\, \mathbb{E}\bigl(X^{3}\bigr)=3\mu\sigma^{2}+\mu^{3}
$$

</div>

<div id="ex-normal-moments-3" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.50</div>

<div lang="en" markdown="1">
Suppose that $Z\sim\mathcal{N}(0,1)$ and let $\Phi(\cdot)$ denote the cdf of <span class="text-nowrap">$Z$.</span> Evaluate $\mathbb{E}\bigl[Z\Phi(Z)\bigr]$ and <span class="text-nowrap">$\mathbb{E}\bigl[Z^{2}\Phi(Z)\bigr]$.</span>
</div>

由於 <span class="text-nowrap">$\mathbb{E}(Z)=0$，</span>故 $\mathbb{E}\bigl[Z\Phi(Z)\bigr]$ 可改寫為 <span class="text-nowrap">$\mathbb{E}\bigl[\Phi(Z)(Z-0)\bigr]$，</span>則由斯泰因引理知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[Z\Phi(Z)\bigr]&=\mathbb{E}\bigl[\Phi(Z)(Z-0)\bigr]=\mathbb{E}\bigl[\phi(Z)\bigr]\\[0.45em]
&=\int_{-\infty}^{\infty}\frac{1}{\,\sqrt{2\pi}\,}e^{-\frac{z^{2}}{2}}\,\frac{1}{\,\sqrt{2\pi}\,}e^{-\frac{z^{2}}{2}}\,dz=\frac{1}{\,2\pi\,}\int_{-\infty}^{\infty}e^{-z^{2}}\,dz\\[0.45em]
&=\frac{1}{\,2\pi\,}\sqrt{\pi}=\frac{1}{\,2\sqrt{\pi}\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[Z\Phi(Z)\bigr]&=\mathbb{E}\bigl[\Phi(Z)(Z-0)\bigr]\\[0.3em]
&=\mathbb{E}\bigl[\phi(Z)\bigr]\\[0.3em]
&=\int_{-\infty}^{\infty}\frac{1}{\,\sqrt{2\pi}\,}e^{-\frac{z^{2}}{2}}\,\frac{1}{\,\sqrt{2\pi}\,}e^{-\frac{z^{2}}{2}}\,dz\\[0.3em]
&=\frac{1}{\,2\pi\,}\int_{-\infty}^{\infty}e^{-z^{2}}\,dz\\[0.3em]
&=\frac{1}{\,2\pi\,}\sqrt{\pi}=\frac{1}{\,2\sqrt{\pi}\,}
\end{aligned}
$$

</div>

同理可得 <span class="text-nowrap">$\mathbb{E}\bigl[Z^{2}\Phi(Z)\bigr]=\mathbb{E}\bigl[Z\Phi(Z)(Z-0)\bigr]$，</span>由斯泰因引理知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\bigl[Z^{2}\Phi(Z)\bigr]=\mathbb{E}\bigl[Z\Phi(Z)(Z-0)\bigr]=\mathbb{E}\Bigl[\bigl(Z\Phi(Z)\bigr)^{\prime}\Bigr]=\mathbb{E}\bigl[\Phi(Z)+Z\phi(Z)\bigr]
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[Z^{2}\Phi(Z)\bigr]&=\mathbb{E}\bigl[Z\Phi(Z)(Z-0)\bigr]\\[0.3em]
&=\mathbb{E}\Bigl[\bigl(Z\Phi(Z)\bigr)^{\prime}\Bigr]\\[0.3em]
&=\mathbb{E}\bigl[\Phi(Z)+Z\phi(Z)\bigr]
\end{aligned}
$$

</div>

又由[機率積分轉換](/teaching-topics/uniform-distribution-integral-transform/#thm-p-i-t)可知 <span class="text-nowrap">$\Phi(Z)\sim\mathcal{U}(0,1)$，</span>故

$$
\mathbb{E}\bigl[\Phi(Z)\bigr]=\frac{1}{\,2\,}
$$

且由於 $\phi(z)$ 為一偶函數，故知道 $z\phi^{2}(z)$ 為奇函數，可得

$$
\mathbb{E}\bigl[Z\phi(Z)\bigr]=\int_{-\infty}^{\infty}z\phi^{2}(z)\,dz=0
$$

此即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\bigl[Z^{2}\Phi(Z)\bigr]=\mathbb{E}\bigl[\Phi(Z)\bigr]+\mathbb{E}\bigl[Z\phi(Z)\bigr]=\frac{1}{\,2\,}+0=\frac{1}{\,2\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[Z^{2}\Phi(Z)\bigr]&=\mathbb{E}\bigl[\Phi(Z)\bigr]+\mathbb{E}\bigl[Z\phi(Z)\bigr]\\[0.3em]
&=\frac{1}{\,2\,}+0=\frac{1}{\,2\,}
\end{aligned}
$$

</div>

</div>

[^stein-himself]: 有趣的事情是，儘管同樣是為了紀念而以 Stein 的姓氏命名，但與[卜瓦松分配](/teaching-topics/poisson-process-and-distribution/#def-poisson-distribution)不同之處在於，這個定理的作者正是斯泰因本人。

## 本篇小結

[Example 4.48](#ex-normal-moments-1) 把標準常態變數 $X$ 乘上一個取值為 $1$ 與 $-1$ 且與 $X$ 獨立的隨機正負號 <span class="text-nowrap">$Z$，</span>得到 <span class="text-nowrap">$Y=ZX$。</span>四個小題的作法都是先對 $Z$ 取條件再取期望值: 前兩小題各求出一個[聯合動差母函數](/teaching-topics/cross-moments-joint-mgf/#def-joint-mgf)，$M_{\sssig XY}(t,s)$ 不等於兩個邊際動差母函數的乘積，$M_{\sssig ZY}(t,s)$ 卻恰好等於，因此 $X$ 與 $Y$ 不獨立而 $Z$ 與 $Y$ 獨立；第三小題由 $M_{\sssig Y}(s)=e^{\frac{\,s^{2}\,}{2}}$ 認出 $Y$ 仍為標準常態分配；第四小題以條件化與速算公式兩種作法各算一次[共變異數](/teaching-topics/covariance/#def-covariance)，都得到 <span class="text-nowrap">$0$。</span>$X$ 與 $Y$ 零相關卻不獨立，這是繼梅花座之後的另一個例子。

[Example 4.49](#ex-normal-moments-2) 的 $W=\frac{X+YZ}{\sqrt{1+Z^{2}}}$ 也是同一個路數。法一固定 <span class="text-nowrap">$Z=z$，</span>此時 $W$ 是 $X$ 與 $Y$ 的線性組合，兩個係數的平方和恰為 <span class="text-nowrap">$1$，</span>故條件分配為標準常態分配；把條件密度乘上 $Z$ 的邊際密度再對 $z$ 積分，$\phi(w)$ 便可以提到積分外而得到 <span class="text-nowrap">$f_{\sssig W}(w)=\phi(w)$。</span>法二改求動差母函數，條件動差母函數算出來是與 $z$ 無關的 <span class="text-nowrap">$e^{\frac{\,t^{2}\,}{2}}$，</span>再取一次期望值仍是同一個式子。兩種作法的關鍵都在於「條件之後係數的平方和為 $1$」這一件事。

[Theorem 4.21](#thm-standard-normal-moments) 給出標準常態分配的各階原動差。證明把 $M_{\sssig Z}(t)=e^{\frac{\,t^{2}\,}{2}}$ 依馬克勞林級數展開，得到只含 $t$ 的偶次方項的級數，再與 $\sum_{k=0}^{\infty}\mathbb{E}(Z^{k})\frac{t^{k}}{k!}$ 比較係數: 奇次項的係數為 <span class="text-nowrap">$0$，</span>偶次項則給出 <span class="text-nowrap">$\mathbb{E}(Z^{k})=\frac{k!}{\,2^{\frac{k}{2}}(\frac{k}{2})!\,}$。</span>這個結果在 [Example 2.33](/teaching-topics/uniqueness-of-the-mgf/#ex-normal-moments-to-pdf) 中其實已經反過來用過一次。

一般常態分配的高階動差可以由此經反標準化得到，但過程繁複。[Theorem 4.22](#thm-stein-lemma) 的斯泰因引理提供了另一條路: 對 $X\sim\mathcal{N}(\mu,\sigma^{2})$ 與可微函數 <span class="text-nowrap">$g$，</span>$g(X)$ 與 $X-\mu$ 相乘的期望值等於 $\sigma^{2}$ 乘上 $g^{\prime}(X)$ 的期望值。證明的關鍵是把 $\frac{-(x-\mu)}{\sigma^{2}}e^{-\frac{(x-\mu)^{2}}{2\sigma^{2}}}$ 看成 $e^{-\frac{(x-\mu)^{2}}{2\sigma^{2}}}$ 的導數，再作分部積分；$\mathbb{E}\bigl[g^{\prime}(X)\bigr]<\infty$ 這個條件保證了邊界項為 <span class="text-nowrap">$0$。</span>取 $g(x)=x^{2}$ 即由 $\mathbb{E}(X^{2})$ 遞推出 <span class="text-nowrap">$\mathbb{E}(X^{3})=3\mu\sigma^{2}+\mu^{3}$。</span>

[Example 4.50](#ex-normal-moments-3) 是這條引理的兩次演練。取 $g(z)=\Phi(z)$ 得到 <span class="text-nowrap">$\mathbb{E}\bigl[Z\Phi(Z)\bigr]=\mathbb{E}\bigl[\phi(Z)\bigr]$，</span>而 $\phi^{2}$ 的積分可以化為 $e^{-z^{2}}$ 的積分，其值為 <span class="text-nowrap">$\sqrt{\pi}$，</span>故答案為 <span class="text-nowrap">$\frac{1}{\,2\sqrt{\pi}\,}$。</span>取 $g(z)=z\Phi(z)$ 則得到 <span class="text-nowrap">$\mathbb{E}\bigl[Z^{2}\Phi(Z)\bigr]=\mathbb{E}\bigl[\Phi(Z)+Z\phi(Z)\bigr]$，</span>其中 $\mathbb{E}\bigl[\Phi(Z)\bigr]$ 由機率積分轉換得知為 <span class="text-nowrap">$\frac{1}{\,2\,}$，</span>而 $\mathbb{E}\bigl[Z\phi(Z)\bigr]$ 的被積分函數為奇函數，其值為 <span class="text-nowrap">$0$，</span>故答案為 <span class="text-nowrap">$\frac{1}{\,2\,}$。</span>

[下一篇](/teaching-topics/chi-squared-distribution/)轉入卡方分配，先由標準常態變數的平方和給出它的定義與性質，再談科克蘭定理。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Charles M. Stein. 1986. *Approximate Computation of Expectations*. Institute of Mathematical Statistics.
