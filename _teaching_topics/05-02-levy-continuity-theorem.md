---
title: "列維連續性定理與極限動差母函數"
subtitle: "Levy's Continuity Theorem and the Limiting Moment Generating Function"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 5
topic: 2
order: 502
permalink: /lecture-notes/levy-continuity-theorem/
date: 2026-08-15
published: false
excerpt: "上一篇以 cdf 求極限分配，本篇改用動差母函數。列維連續性定理指出，若隨機變數序列的動差母函數在原點的一個鄰域上逐點收斂至某個隨機變數的動差母函數，則該序列即分配收斂至該隨機變數，這個極限稱為極限動差母函數。五道例題全部依這一條定理施作: 伯努利樣本和在 $np=\\lambda$ 固定而 $p\\to0$ 之下趨於卜瓦松分配；同一組樣本標準化之後，以泰勒展開式把動差母函數併成 $\\bigl[1+\\frac{t^{2}}{2n}+o(\\frac{1}{n})\\bigr]^{n}$ 這個形式，因而趨於標準常態分配，不用中央極限定理；負二項分配在 $r\\to\\infty$、$p\\to1$ 且 $r(1-p)=\\lambda$ 之下同樣趨於卜瓦松分配。最後兩題的極限是常數: 常態隨機樣本的樣本平均數與樣本變異數，其動差母函數分別收斂至 $e^{\\mu t}$ 與 $e^{\\sigma^{2}t}$，也就是退化在 $\\mu$ 與 $\\sigma^{2}$ 兩點上，這正是兩者的一致性。"
---

[上一篇](/lecture-notes/convergence-in-distribution/)給出[分配收斂](/lecture-notes/convergence-in-distribution/#def-converge-in-distribution)的定義，其中的五道例題一律以 cdf 求極限分配。本篇改用另一項工具，也就是[動差母函數](/lecture-notes/moment-generating-functions/#def-mgf)。

本篇先給出列維連續性定理: 只要隨機變數序列的 mgf 逐點收斂至某個隨機變數的 mgf，分配收斂就跟著成立，而這個極限的 mgf 稱為極限動差母函數。其後五道例題全部依這一條定理施作，前三道處理常見分配之間的極限關係，後兩道的極限則是一個常數。

## 列維連續性定理

至此為止，讀者應該已經稍微熟悉分配收斂的操作與特性。然而，細心一點的讀者可能會想到，能決定分配的，並不只有 cdf 而已，與機率分配具有對應關係的 mgf，是不是也能在此處發揮功用呢？這個答案是肯定的，也就是如下定理。

<div id="thm-levys-continuity-thm" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 5.1 (列維連續性定理, Levy's continuity theorem)</div>

令 $\lbrace X_n\rbrace_{n=1}^{\infty}$ 為一定義在機率空間上之隨機變數序列，而對應的 cdf 序列為 <span class="text-nowrap">$\lbrace F_n\rbrace_{n=1}^{\infty}$、</span>對應的 mgf 序列為 $\lbrace M_n(t)\rbrace_{n=1}^{\infty},\ \forall -h<t<h,\ h>0$ 這一列函數。

若一隨機變數 $X$ 之 cdf 為 <span class="text-nowrap">$F_{\sssig X}$、</span>mgf 為 $M_{\sssig X}(t),\ \forall -h<t<h,\ h>0$ 這個函數，且

$$
\lim_{n\to\infty}M_{n}(t)=M_{\sssig X}(t),\ \forall -h<t<h,\ h>0
$$

則對 $F_{\sssig X}$ 的所有連續點，將有 $\lim_{n\to\infty}F_{n}(x)=F_{\sssig X}(x)$ 的結果，此即

$$
X_n\dconv X
$$

其中，$M_{\sssig X}(t)$ 稱為 $\lbrace M_n(t)\rbrace_{n=1}^{\infty}$ 之**極限動差母函數 <span lang="en">(limiting moment generating function, limiting mgf)</span>**。

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個定理的核心想法很單純，只要序列的 mgf 能夠收斂至某個隨機變數的 mgf，則從利用 mgf 與分配間對應的[唯一性](/lecture-notes/uniqueness-of-the-mgf/#thm-mgf-uniqueness)，我們不難想像到，這個序列的極限分配就會是該隨機變數所服從的分配。

利用這個定理，我們可以發現一些常見分配之間的關係，見下列問題。

</div>

## 常見分配之間的極限關係

<div id="ex-binomial-to-poisson" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.6</div>

<div lang="en" markdown="1">
Suppose that $X_1,X_2,\ldots,X_n$ form a random sample from a Bernoulli distribution with success probability <span class="text-nowrap">$p$,</span> and put <span class="text-nowrap">$Y_n=\sum_{i=1}^{n}X_i$.</span> Let $p$ tend to $0$ as $n$ grows without bound, in such a manner that $np$ stays equal to a fixed constant <span class="text-nowrap">$\lambda>0$.</span> Show that the limiting distribution of $Y_n$ is a Poisson distribution whose mean equals <span class="text-nowrap">$\lambda$.</span>
</div>

由[伯努利分配](/lecture-notes/bernoulli-trials-and-distribution/#def-bernoulli)之可加性知

<div class="topic-math-follow-before" markdown="1">

$$
Y_n=\sum_{i=1}^{n}X_i\sim\mathrm{Bin}(n,p)
$$

</div>
<div class="topic-math-follow" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ M_{\sssig Y_n}(t)&=\bigl[pe^{t}+(1-p)\bigr]^{n}=\biggl(\frac{\,\lambda e^{t}\,}{n}+1-\frac{\,\lambda\,}{n}\biggr)^{n}\\[0.45em]
&=\biggl[1+\frac{\,\lambda(e^{t}-1)\,}{n}\biggr]^{n}
\end{aligned}
$$

</div>

故

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lim_{n\to\infty}M_{\sssig Y_n}(t)=\lim_{n\to\infty}\biggl[1+\frac{\,\lambda(e^{t}-1)\,}{n}\biggr]^{n}=e^{\lambda(e^{t}-1)},\ t\in\mathbb{R}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\lim_{n\to\infty}M_{\sssig Y_n}(t)&=\lim_{n\to\infty}\biggl[1+\frac{\,\lambda(e^{t}-1)\,}{n}\biggr]^{n}\\[0.3em]
&=e^{\lambda(e^{t}-1)},\ t\in\mathbb{R}
\end{aligned}
$$

</div>

又令 <span class="text-nowrap">$W\sim\mathrm{Poi}(\lambda)$，</span>其 mgf 為 <span class="text-nowrap">$M_{\sssig W}(t)=e^{\lambda(e^{t}-1)},\ t\in\mathbb{R}$，</span>我們有

$$
\lim_{n\to\infty}M_{\sssig Y_n}(t)=M_{\sssig W}(t),\ \forall t\in\mathbb{R}
$$

由列維連續性定理知

$$
Y_n\dconv W\sim\mathrm{Poi}(\lambda)
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

本題能夠收斂的關鍵在於，當 $n\to\infty$ 時，$p$ 將趨近於 $0$ 而 $np=\lambda>0$ 為一個定值，有此要件，我們才能夠完成此收斂。

這個收斂的結果可以被想像為，在[卜瓦松過程](/lecture-notes/poisson-process-and-distribution/#def-poisson-process)的每一個「瞬間」，我們都進行一次成敗實驗，則基於卜瓦松過程的假設，每次的實驗中，成功機率都趨近於 $0$；由於單位時間是一段時間，當中包含無窮多個「瞬間」，因此需要 $n\to\infty$ 而 <span class="text-nowrap">$p\to0$，</span>並且此過程的期望值就是 <span class="text-nowrap">$np=\lambda$。</span>

然而，由於 $n\to\infty$ 僅僅是存在於數學中的概念，在實務上，我們會認為只要 $n$ 足夠大，而 $np$ 是某個定值，則我們可以將這個過程中的總成功次數的機率值，由原先的[二項分配](/lecture-notes/binomial-distribution/#def-binomial)機率值，以[卜瓦松分配](/lecture-notes/poisson-process-and-distribution/#def-poisson-distribution)的機率值「近似」求算，二者的結果不會相差太遠。

</div>

<div id="ex-standardized-bernoulli-sum-to-normal" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.7</div>

<div lang="en" markdown="1">
Suppose that $X_1,X_2,\ldots,X_n$ is a random sample drawn from <span class="text-nowrap">$\mathrm{Bin}(1,p)$.</span> Working with the moment generating function, show that

$$
\frac{\,\sum_{i=1}^{n}X_i-np\,}{\,\sqrt{np(1-p)}\,}\dconv Z\sim\mathcal{N}(0,1)
$$

Note that the central limit theorem is not available for this argument.
</div>

令

$$
Z_n=\frac{\,\sum_{i=1}^{n}X_i-np\,}{\,\sqrt{np(1-p)}\,}
$$

則我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{\sssig Z_n}(t)&=\mathbb{E}\bigl(e^{tZ_n}\bigr)=\mathbb{E}\Bigl[e^{t\frac{\,\sum_{i=1}^{n}X_i-np\,}{\,\sqrt{np(1-p)}\,}}\Bigr]=e^{\frac{-npt}{\,\sqrt{np(1-p)}\,}}\,\mathbb{E}\Bigl[e^{\sum_{i=1}^{n}\frac{t}{\sqrt{np(1-p)}}X_i}\Bigr]\\[0.45em]
&=e^{\frac{-npt}{\,\sqrt{np(1-p)}\,}}\prod_{i=1}^{n}\mathbb{E}\Bigl[e^{\frac{t}{\sqrt{np(1-p)}}X_i}\Bigr]=e^{\frac{-npt}{\,\sqrt{np(1-p)}\,}}\Bigl[p\,e^{\frac{t}{\sqrt{np(1-p)}}}+(1-p)\Bigr]^{n}\\[0.45em]
&=\Bigl(e^{\frac{-pt}{\,\sqrt{np(1-p)}\,}}\Bigl[p\,e^{\frac{t}{\sqrt{np(1-p)}}}+(1-p)\Bigr]\Bigr)^{n}\\[0.45em]
&=\Bigl[p\,e^{\frac{(1-p)t}{\sqrt{np(1-p)}}}+(1-p)\,e^{\frac{-pt}{\sqrt{np(1-p)}}}\Bigr]^{n}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig Z_n}(t)&=\mathbb{E}\bigl(e^{tZ_n}\bigr)\\[0.3em]
&=\mathbb{E}\Bigl[e^{t\frac{\,\sum_{i=1}^{n}X_i-np\,}{\,\sqrt{np(1-p)}\,}}\Bigr]\\[0.3em]
&=e^{\frac{-npt}{\,\sqrt{np(1-p)}\,}}\,\mathbb{E}\Bigl[e^{\sum_{i=1}^{n}\frac{t}{\sqrt{np(1-p)}}X_i}\Bigr]\\[0.3em]
&=e^{\frac{-npt}{\,\sqrt{np(1-p)}\,}}\prod_{i=1}^{n}\mathbb{E}\Bigl[e^{\frac{t}{\sqrt{np(1-p)}}X_i}\Bigr]\\[0.3em]
&=e^{\frac{-npt}{\,\sqrt{np(1-p)}\,}}\Bigl[p\,e^{\frac{t}{\sqrt{np(1-p)}}}+(1-p)\Bigr]^{n}\\[0.3em]
&=\Bigl(e^{\frac{-pt}{\,\sqrt{np(1-p)}\,}}\Bigl[p\,e^{\frac{t}{\sqrt{np(1-p)}}}+(1-p)\Bigr]\Bigr)^{n}\\[0.3em]
&=\Bigl[p\,e^{\frac{(1-p)t}{\sqrt{np(1-p)}}}+(1-p)\,e^{\frac{-pt}{\sqrt{np(1-p)}}}\Bigr]^{n}
\end{aligned}
$$

</div>

其中

$$
\begin{aligned}
e^{\frac{(1-p)t}{\sqrt{np(1-p)}}}&=1+\frac{(1-p)t}{\sqrt{np(1-p)}}+\frac{(1-p)^{2}t^{2}}{2np(1-p)}+o\Bigl(\frac{1}{\,n\,}\Bigr)\\[0.45em]
e^{\frac{-pt}{\sqrt{np(1-p)}}}&=1-\frac{pt}{\sqrt{np(1-p)}}+\frac{p^{2}t^{2}}{2np(1-p)}+o\Bigl(\frac{1}{\,n\,}\Bigr)
\end{aligned}
$$

則將上二式代入 <span class="text-nowrap">$M_{\sssig Z_n}(t)$，</span>可以改寫為

<div class="topic-math-follow-before" markdown="1">

$$
\begin{aligned}
M_{\sssig Z_n}(t)&=\Bigl[p\,e^{\frac{(1-p)t}{\sqrt{np(1-p)}}}+(1-p)\,e^{\frac{-pt}{\sqrt{np(1-p)}}}\Bigr]^{n}\\[0.45em]
&=\biggl[1+\frac{t^{2}}{\,2n\,}+o\Bigl(\frac{1}{\,n\,}\Bigr)\biggr]^{n}
\end{aligned}
$$

</div>
<div class="topic-math-follow" markdown="1">
<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ \lim_{n\to\infty}M_{\sssig Z_n}(t)&=\lim_{n\to\infty}\biggl[1+\frac{t^{2}}{\,2n\,}+o\Bigl(\frac{1}{\,n\,}\Bigr)\biggr]^{n}=e^{\frac{\,t^{2}\,}{2}},\ t\in\mathbb{R}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ \lim_{n\to\infty}M_{\sssig Z_n}(t)&=\lim_{n\to\infty}\biggl[1+\frac{t^{2}}{\,2n\,}+o\Bigl(\frac{1}{\,n\,}\Bigr)\biggr]^{n}\\[0.3em]
&=e^{\frac{\,t^{2}\,}{2}},\ t\in\mathbb{R}
\end{aligned}
$$

</div>
</div>

可令 <span class="text-nowrap">$Z\sim\mathcal{N}(0,1)$，</span>其 mgf 為 <span class="text-nowrap">$M_{\sssig Z}(t)=e^{\frac{\,t^{2}\,}{2}},\ t\in\mathbb{R}$，</span>我們有

$$
\lim_{n\to\infty}M_{\sssig Z_n}(t)=M_{\sssig Z}(t),\ \forall t\in\mathbb{R}
$$

由列維連續性定理知

$$
Z_n=\frac{\,\sum_{i=1}^{n}X_i-np\,}{\,\sqrt{np(1-p)}\,}\dconv Z\sim\mathcal{N}(0,1)
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

上述問題使用到了泰勒展開式，將 $e^{\frac{(1-p)t}{\sqrt{np(1-p)}}}$ 與 $e^{\frac{-pt}{\sqrt{np(1-p)}}}$ 分別都對 $0$ 展開，並將三次方以後的項合併為 $1/n$ 的小 o 函數，用以表示當 $n\to\infty$ 時，此項將會先 $1/n$ 一步趨近於 $0$；此外，小 o 函數在我們常見的 $\lim_{n\to\infty}\bigl(1+\frac{\,a\,}{n}\bigr)^{n}=e^{a}$ 中也是允許出現的，同樣因為當 $n\to\infty$ 時，$o\bigl(\frac{1}{\,n\,}\bigr)$ 相較於前面的 $1$ 與 <span class="text-nowrap">$\frac{a}{\,n\,}$，</span>早就先一步消失為 $0$ 了，因此不影響結果，此即

$$
\lim_{n\to\infty}\biggl[1+\frac{\,a\,}{n}+o\Bigl(\frac{1}{\,n\,}\Bigr)\biggr]^{n}=e^{a}
$$

另外，這個問題也可以由中央極限定理 <span lang="en">(central limit theorem)</span> 來求解，稍後我們會談到這個統計學中最重要的定理。

</div>

<div id="ex-negative-binomial-to-poisson" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.8</div>

<div lang="en" markdown="1">
Suppose that <span class="text-nowrap">$X\sim\mathcal{NB}(r,p)$</span> takes the values <span class="text-nowrap">$x=0,1,\ldots,\infty$.</span> Determine the conditions under which $X$ converges in distribution to a Poisson distribution, and show that the convergence does hold once those conditions are imposed.
</div>

若 <span class="text-nowrap">$r\to\infty$、</span>$p\to1$ 且 $r(1-p)=\lambda>0$ 為一定值，則 $X$ 可分配收斂至 <span class="text-nowrap">$W\sim\mathrm{Poi}(\lambda)$，</span>證明如下。

由於 <span class="text-nowrap">$r(1-p)=\lambda\Longleftrightarrow(1-p)=\frac{\,\lambda\,}{r}$，</span>也就是 <span class="text-nowrap">$p=1-\frac{\,\lambda\,}{r}$，</span>則 $X$ 之 mgf 可改寫為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{\sssig X}(t)&=\biggl[\frac{p}{\,1-(1-p)e^{t}\,}\biggr]^{r}=\Biggl[\frac{\,1-\frac{\,\lambda\,}{r}\,}{\,1-\frac{\,\lambda\,}{r}e^{t}\,}\Biggr]^{r}\\[0.45em]
&=\biggl[1-\frac{\,\lambda\,}{r}\biggr]^{r}\biggl[1-\frac{\,\lambda e^{t}\,}{r}\biggr]^{-r},\ t<-\ln(1-p)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig X}(t)&=\biggl[\frac{p}{\,1-(1-p)e^{t}\,}\biggr]^{r}\\[0.3em]
&=\Biggl[\frac{\,1-\frac{\,\lambda\,}{r}\,}{\,1-\frac{\,\lambda\,}{r}e^{t}\,}\Biggr]^{r}\\[0.3em]
&=\biggl[1-\frac{\,\lambda\,}{r}\biggr]^{r}\biggl[1-\frac{\,\lambda e^{t}\,}{r}\biggr]^{-r},\ t<-\ln(1-p)
\end{aligned}
$$

</div>

由於 <span class="text-nowrap">$r\to\infty$，</span>我們有

$$
\begin{aligned}
\lim_{r\to\infty}\biggl[1-\frac{\,\lambda\,}{r}\biggr]^{r}&=e^{-\lambda}\\[0.45em]
\lim_{r\to\infty}\biggl[1-\frac{\,\lambda e^{t}\,}{r}\biggr]^{-r}&=e^{\lambda e^{t}},\ t<-\ln(1-p)
\end{aligned}
$$

則有

$$
\begin{aligned}
\lim_{r\to\infty}M_{\sssig X}(t)&=\lim_{r\to\infty}\biggl[1-\frac{\,\lambda\,}{r}\biggr]^{r}\lim_{r\to\infty}\biggl[1-\frac{\,\lambda e^{t}\,}{r}\biggr]^{-r}\\[0.45em]
&=e^{-\lambda}e^{\lambda e^{t}}=e^{\lambda(e^{t}-1)},\ t<-\ln(1-p)
\end{aligned}
$$

又由於 <span class="text-nowrap">$p\to1$，</span>故

$$
\lim_{r\to\infty}M_{\sssig X}(t)=e^{\lambda(e^{t}-1)},\ t\in\mathbb{R}
$$

則令 <span class="text-nowrap">$W\sim\mathrm{Poi}(\lambda)$，</span>其 mgf 為 <span class="text-nowrap">$M_{\sssig W}(t)=e^{\lambda(e^{t}-1)},\ t\in\mathbb{R}$，</span>我們有

$$
\lim_{r\to\infty}M_{\sssig X}(t)=M_{\sssig W}(t),\ \forall t\in\mathbb{R}
$$

由列維連續性定理知

$$
X\dconv W\sim\mathrm{Poi}(\lambda)
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

由於 $X$ 表示一系列的伯努利實驗中，直到第 $r$ 次成功為止，所需要的失敗次數，故當 $r\to\infty$ 時，這個近似的結果可以想像成進行了無窮多次的伯努利實驗，[^infinitely-many-trials] 觀察其中的失敗次數。

讀者應該會發現，這個想法非常接近於 [Example 5.6](#ex-binomial-to-poisson) 中的想法，只不過關注的事件從成功的事件變成失敗的事件了，因此對於分配收斂的先決條件，也從 $p\to0$ 變成了 <span class="text-nowrap">$p\to1$，</span>就是為了確保「失敗」這個事件發生的機率幾乎為 <span class="text-nowrap">$0$，</span>就好像當時的「成功」事件發生機率必須幾乎為 $0$ 一樣；而此處的要求變為 <span class="text-nowrap">$r(1-p)=\lambda$，</span>也呼應 [Example 5.6](#ex-binomial-to-poisson) 中的 <span class="text-nowrap">$np=\lambda$。</span>

</div>

讀者應該會發現，透過這些證明，我們可以得知，在特定條件下，許多分配間都具有近似關係。事實上，在稍後的中央極限定理中，我們會看見更多這樣的應用與關係。

## 極限分配為一個常數的統計量

但在此之前，我們先來關心一些有趣的結果，是關於統計量分配收斂的對象，[^consistency] 是一個常數的時候，見以下問題。

<div id="ex-xbar-consistency-mgf" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.9 ($\overline{X}$ 的一致性)</div>

<div lang="en" markdown="1">
Suppose that <span class="text-nowrap">$X_1,\ldots,X_n\iidto\mathcal{N}(\mu,\sigma^{2})$,</span> and let $\overline{X}=\frac{1}{\,n\,}\sum_{i=1}^{n}X_i$ denote the sample mean. Determine the limiting distribution of <span class="text-nowrap">$\overline{X}$.</span>
</div>

由 $X_1,\ldots,X_n\iidto\mathcal{N}(\mu,\sigma^{2})$ 可知 <span class="text-nowrap">$M_{\sssig X_i}(t)=e^{\mu t+\frac{\sigma^{2}}{2}t^{2}},\ t\in\mathbb{R}$，</span>則我們有

<div class="topic-math-follow-before" markdown="1">
<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{\sssig \overline{X}}(t)&=\mathbb{E}\bigl(e^{t\overline{X}}\bigr)=\prod_{i=1}^{n}\mathbb{E}\bigl(e^{\frac{t}{n}X_i}\bigr)=\prod_{i=1}^{n}M_{\sssig X_i}\Bigl(\frac{t}{n}\Bigr)\\[0.45em]
&=\Bigl[e^{\frac{\mu}{n}t+\frac{\sigma^{2}}{2}\frac{t^{2}}{n^{2}}}\Bigr]^{n}=e^{\mu t+\frac{\sigma^{2}}{2}\frac{t^{2}}{n}},\ t\in\mathbb{R}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig \overline{X}}(t)&=\mathbb{E}\bigl(e^{t\overline{X}}\bigr)=\prod_{i=1}^{n}\mathbb{E}\bigl(e^{\frac{t}{n}X_i}\bigr)\\[0.3em]
&=\prod_{i=1}^{n}M_{\sssig X_i}\Bigl(\frac{t}{n}\Bigr)\\[0.3em]
&=\Bigl[e^{\frac{\mu}{n}t+\frac{\sigma^{2}}{2}\frac{t^{2}}{n^{2}}}\Bigr]^{n}=e^{\mu t+\frac{\sigma^{2}}{2}\frac{t^{2}}{n}},\ t\in\mathbb{R}
\end{aligned}
$$

</div>
</div>
<div class="topic-math-follow" markdown="1">

$$
\Longrightarrow\ \lim_{n\to\infty}M_{\sssig \overline{X}}(t)=\lim_{n\to\infty}e^{\mu t+\frac{\sigma^{2}}{2}\frac{t^{2}}{n}}=e^{\mu t},\ t\in\mathbb{R}
$$

</div>

令 $W\equiv\mu$ 為一退化隨機變數，具 mgf <span class="text-nowrap">$M_{\sssig W}(t)=e^{\mu t},\ t\in\mathbb{R}$，</span>我們有

$$
\lim_{n\to\infty}M_{\sssig \overline{X}}(t)=M_{\sssig W}(t),\ t\in\mathbb{R}
$$

由列維連續性定理知

$$
\overline{X}=\frac{1}{\,n\,}\sum_{i=1}^{n}X_i\dconv W\equiv\mu
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個問題牽涉到 $\overline{X}$ 的一致性，此即保證，對於用以推論 $\mu$ 的統計量 <span class="text-nowrap">$\overline{X}$，</span>只要可以取得一組無窮大的樣本，這時的樣本平均必定就是母體平均。事實上，即便 $X_1,\ldots,X_n$ 並不是來自[常態母體](/lecture-notes/normal-distribution/#def-normal)，只要期望值與變異數存在，$\overline{X}$ 仍具備一致性，在數理統計的章節中，我們將會談到這一點。

與 $\overline{X}$ 相對，另一個常見的統計量是樣本變異數 <span class="text-nowrap">$S^{2}$，</span>用以推論 <span class="text-nowrap">$\sigma^{2}$，</span>其實也具備一致性，見下列這題。

</div>

<div id="ex-s-squared-consistency-mgf" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.10 ($S^{2}$ 的一致性)</div>

<div lang="en" markdown="1">
Suppose that <span class="text-nowrap">$X_1,\ldots,X_n\iidto\mathcal{N}(\mu,\sigma^{2})$,</span> and let $S^{2}=\frac{1}{\,n-1\,}\sum_{i=1}^{n}(X_i-\overline{X})^{2}$ denote the sample variance. Determine the limiting distribution of <span class="text-nowrap">$S^{2}$.</span>
</div>

由 $X_1,\ldots,X_n\iidto\mathcal{N}(\mu,\sigma^{2})$ 可知

$$
\frac{\,(n-1)S^{2}\,}{\sigma^{2}}\sim\chi^{2}(n-1)
$$

則我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
S^{2}=\frac{\sigma^{2}}{\,n-1\,}\times\frac{\,(n-1)S^{2}\,}{\sigma^{2}}\sim\mathrm{Gamma}\biggl(\alpha=\frac{n-1}{2},\ \beta=\frac{2\sigma^{2}}{\,n-1\,}\biggr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
S^{2}&=\frac{\sigma^{2}}{\,n-1\,}\times\frac{\,(n-1)S^{2}\,}{\sigma^{2}}\\[0.3em]
&\sim\mathrm{Gamma}\biggl(\alpha=\frac{n-1}{2},\ \beta=\frac{2\sigma^{2}}{\,n-1\,}\biggr)
\end{aligned}
$$

</div>

可知 $S^{2}$ 之 mgf 為

<div class="topic-math-follow-before" markdown="1">

$$
M_{\sssig S^{2}}(t)=\biggl[1-\biggl(\frac{2\sigma^{2}}{\,n-1\,}\biggr)t\biggr]^{-\frac{n-1}{2}},\ t<\frac{\,n-1\,}{2\sigma^{2}}
$$

</div>
<div class="topic-math-follow" markdown="1">
<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ \lim_{n\to\infty}M_{\sssig S^{2}}(t)&=\lim_{n\to\infty}\biggl[1-\biggl(\frac{2\sigma^{2}}{\,n-1\,}\biggr)t\biggr]^{-\frac{n-1}{2}}\\[0.45em]
&=\lim_{n-1\to\infty}\biggl[1-\biggl(\frac{2\sigma^{2}}{\,n-1\,}\biggr)t\biggr]^{-\frac{n-1}{2}}\\[0.45em]
&=\lim_{m\to\infty}\biggl[1+\frac{\,-2\sigma^{2}t\,}{\,m\,}\biggr]^{-\frac{m}{2}}\qquad(\,\text{令}\ m=n-1\,)\\[0.45em]
&=\bigl(e^{-2\sigma^{2}t}\bigr)^{-\frac{1}{2}}=e^{\sigma^{2}t},\ t\in\mathbb{R}\qquad\Bigl(\,\because\ \lim_{n\to\infty}\frac{\,n-1\,}{2\sigma^{2}}=\infty\,\Bigr)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ \lim_{n\to\infty}M_{\sssig S^{2}}(t)&=\lim_{n\to\infty}\biggl[1-\biggl(\frac{2\sigma^{2}}{\,n-1\,}\biggr)t\biggr]^{-\frac{n-1}{2}}\\[0.3em]
&=\lim_{n-1\to\infty}\biggl[1-\biggl(\frac{2\sigma^{2}}{\,n-1\,}\biggr)t\biggr]^{-\frac{n-1}{2}}\\[0.3em]
&=\lim_{m\to\infty}\biggl[1+\frac{\,-2\sigma^{2}t\,}{\,m\,}\biggr]^{-\frac{m}{2}}\\[0.2em]
&\qquad\qquad(\,\text{令}\ m=n-1\,)\\[0.3em]
&=\bigl(e^{-2\sigma^{2}t}\bigr)^{-\frac{1}{2}}=e^{\sigma^{2}t},\ t\in\mathbb{R}\\[0.2em]
&\qquad\Bigl(\,\because\ \lim_{n\to\infty}\frac{\,n-1\,}{2\sigma^{2}}=\infty\,\Bigr)
\end{aligned}
$$

</div>
</div>

令 $W\equiv\sigma^{2}$ 為一退化隨機變數，具 mgf <span class="text-nowrap">$M_{\sssig W}(t)=e^{\sigma^{2}t},\ t\in\mathbb{R}$，</span>我們有

$$
\lim_{n\to\infty}M_{\sssig S^{2}}(t)=M_{\sssig W}(t),\ t\in\mathbb{R}
$$

由列維連續性定理知

$$
S^{2}=\frac{1}{\,n-1\,}\sum_{i=1}^{n}(X_i-\overline{X})^{2}\dconv W\equiv\sigma^{2}
$$

</div>

[^infinitely-many-trials]: 這是當然的，要得到無窮多次的成功，必定需要無窮多次的實驗。

[^consistency]: 讀者可能在此有一點納悶，統計量明明具有隨機性呀，怎麼會分配收斂到一個常數去呢？這一個概念事實上正是**一致性 <span lang="en">(consistency)</span>**，我們將在數理統計的環節中詳談。

## 本篇小結

[Theorem 5.1](#thm-levys-continuity-thm) 把求極限分配的工具由 cdf 換成 mgf: 若 $\lbrace X_n\rbrace_{n=1}^{\infty}$ 的 mgf 在 $-h<t<h$ 這一段區間上逐點收斂至某個隨機變數 $X$ 的 mgf，則在 $F_{\sssig X}$ 的每一個連續點上 $F_n$ 都收斂至 <span class="text-nowrap">$F_{\sssig X}$，</span>也就是 <span class="text-nowrap">$X_n\dconv X$，</span>而這個極限的 mgf 稱為極限動差母函數。之所以能這樣做，靠的是 mgf 與分配之間的一一對應。

前三道例題示範的是常見分配之間的極限關係。[Example 5.6](#ex-binomial-to-poisson) 由伯努利分配的可加性得到 <span class="text-nowrap">$Y_n\sim\mathrm{Bin}(n,p)$，</span>再把 $p$ 代換為 $\frac{\lambda}{\,n\,}$ 而湊出 $\bigl[1+\frac{\lambda(e^{t}-1)}{n}\bigr]^{n}$ 這個形式，取極限即得卜瓦松分配的 mgf。[Example 5.8](#ex-negative-binomial-to-poisson) 的結構相同，只是把條件由 $p\to0$ 與 $np=\lambda$ 換成 $p\to1$ 與 <span class="text-nowrap">$r(1-p)=\lambda$，</span>因為負二項分配在這裡記錄的是失敗次數而非成功次數。[Example 5.7](#ex-standardized-bernoulli-sum-to-normal) 則是把伯努利樣本和標準化: 先由[線性組合的動差母函數](/lecture-notes/mgf-method-transformations/#thm-mgf-two-to-one)把期望值拆成連乘，再對兩個指數項各作一次泰勒展開，三次方以後的項一律併入 <span class="text-nowrap">$o\bigl(\frac{1}{\,n\,}\bigr)$，</span>整條式子因而收成 $\bigl[1+\frac{t^{2}}{2n}+o\bigl(\frac{1}{\,n\,}\bigr)\bigr]^{n}$ 這個形式，極限為 $e^{\frac{t^{2}}{2}}$ 而得標準常態分配。這一題不用中央極限定理，靠的全是 mgf 的計算。

後兩道例題的極限不是一個分配，而是一個常數。[Example 5.9](#ex-xbar-consistency-mgf) 由常態分配的 mgf 求得 <span class="text-nowrap">$M_{\sssig \overline{X}}(t)=e^{\mu t+\frac{\sigma^{2}}{2}\frac{t^{2}}{n}}$，</span>其中的 $\frac{t^{2}}{\,n\,}$ 這一項隨 $n$ 消去，極限 $e^{\mu t}$ 正是退化在 $\mu$ 這一點上的隨機變數的 mgf。[Example 5.10](#ex-s-squared-consistency-mgf) 的作法一樣，先由[科克蘭定理](/lecture-notes/chi-squared-distribution/#thm-cochran-theorem)得到 <span class="text-nowrap">$\frac{(n-1)S^{2}}{\sigma^{2}}\sim\chi^{2}(n-1)$，</span>改寫為[伽瑪分配](/lecture-notes/gamma-distribution/#def-gamma-distribution)之後取其 mgf，以 $m=n-1$ 代換再取極限，得到 $e^{\sigma^{2}t}$ 這個結果。兩者分別是 $\overline{X}$ 與 $S^{2}$ 的一致性: 樣本大到無窮時，這兩個統計量的隨機性完全消失，各自退化為它們所要推論的母體參數。

[下一篇](/lecture-notes/convergence-in-probability/)轉入機率收斂，那是一種比分配收斂更強的收斂型態，並會說明兩者之間的蘊含關係，以及極限為常數時兩者何以等價。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
