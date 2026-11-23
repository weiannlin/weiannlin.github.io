---
title: "列維連續性定理與極限動差母函數"
subtitle: "Levy’s Continuity Theorem and the Limiting Moment Generating Function"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 5
topic: 2
order: 502
permalink: /lecture-notes/levy-continuity-theorem/
date: 2026-08-15
published: true
excerpt: "列維連續性定理指出，若隨機變數序列的動差母函數在原點鄰域逐點收斂至某個隨機變數的動差母函數，則該序列分配收斂至該極限分配。本篇以二項與負二項趨於卜瓦松、標準化伯努利和趨於標準常態等五道例題示範應用。"
---

[上一篇](/lecture-notes/convergence-in-distribution/)給出[分配收斂](/lecture-notes/convergence-in-distribution/#def-converge-in-distribution)的定義，其中的五道例題一律以 cdf 求極限分配。本篇改用另一項工具，也就是[動差母函數](/lecture-notes/moment-generating-functions/#def-mgf)。

本篇先給出列維連續性定理，說明只要隨機變數序列的 mgf 逐點收斂至某個隨機變數的 mgf，分配收斂就跟著成立，而這個極限的 mgf 稱為極限動差母函數。其後五道例題全部依這一條定理施作，前三道處理常見分配之間的極限關係，後兩道的極限則是一個常數。

## 列維連續性定理

除了 cdf 之外，在原點鄰域存在的 mgf 同樣能唯一決定機率分配；那麼，能否改由 mgf 序列的極限來判定分配收斂？答案是肯定的，見下列定理。

<div id="thm-levys-continuity-thm" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 5.1 (列維連續性定理, Levy’s continuity theorem)</div>

令 $\lbrace X_n\rbrace_{n=1}^{\infty}$ 為一定義在機率空間上之隨機變數序列，而對應的 cdf 序列為 $\lbrace F_n\rbrace_{n=1}^{\infty}$ 這一列函數、對應的 mgf 序列為 $\lbrace M_n(t)\rbrace_{n=1}^{\infty},\ \forall\,-h<t<h,\ h>0$ 這一列函數。

若一隨機變數 $X$ 之 cdf 為 <span class="text-nowrap">$F_{\sssig X}$、</span>mgf 為 $M_{\sssig X}(t),\ \forall\,-h<t<h,\ h>0$ 這個函數，且

$$
\lim_{n\to\infty}M_{n}(t)=M_{\sssig X}(t),\ \forall\,-h<t<h,\ h>0
$$

則對 $F_{\sssig X}$ 的所有連續點，將有 $\lim_{n\to\infty}F_{n}(x)=F_{\sssig X}(x)$ 的結果，此即

$$
X_n\dconv X
$$

其中，$M_{\sssig X}(t)$ 稱為 $\lbrace M_n(t)\rbrace_{n=1}^{\infty}$ 之**極限動差母函數 <span lang="en">(limiting moment generating function, limiting mgf)</span>**。

</div>

上述定理與 mgf 的[唯一性](/lecture-notes/uniqueness-of-the-mgf/#thm-mgf-uniqueness)相呼應；既然原點鄰域內的 mgf 能唯一決定機率分配，當序列的 mgf 逐點收斂至某個隨機變數的 mgf 時，其對應的機率分配亦隨之收斂至該隨機變數的分配。利用此一定理，即可直接推導常見分配之間的極限關係，見下列例題。

## 常見分配之間的極限關係

<div id="ex-binomial-to-poisson" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.6</div>

<div lang="en" markdown="1">
Let $X_1,X_2,\ldots,X_n$ be a random sample from a Bernoulli distribution, and consider $Y_n=\sum_{i=1}^{n}X_i$. Let $p\to0$ as $n\to\infty$ in such a way that <span class="text-nowrap">$np=\lambda$,</span> for fixed <span class="text-nowrap">$\lambda>0$.</span> Show that the limiting distribution of $Y_n$ is a Poisson distribution with mean <span class="text-nowrap">$\lambda$.</span>
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

又令 $W\sim\mathrm{Poi}(\lambda)$ 服從卜瓦松分配，其 mgf 為 $M_{\sssig W}(t)=e^{\lambda(e^{t}-1)},\ t\in\mathbb{R}$ 這個函數，我們有

$$
\lim_{n\to\infty}M_{\sssig Y_n}(t)=M_{\sssig W}(t),\ \forall\,t\in\mathbb{R}
$$

由列維連續性定理知

$$
Y_n\dconv W\sim\mathrm{Poi}(\lambda)
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

本題極限成立的關鍵，在於 $n\to\infty$ 的同時 $p\to0$ 且乘積 $np=\lambda>0$ 維持定值。此一極限可由[卜瓦松過程](/lecture-notes/poisson-process-and-distribution/#def-poisson-process)的架構詮釋；將單位時間細分為 $n$ 個極短子區間並各觀察一次成敗實驗，當 $n\to\infty$ 時，單次實驗的成功機率 $p$ 趨近於 <span class="text-nowrap">$0$，</span>而單位時間內的期望成功次數則維持為 <span class="text-nowrap">$np=\lambda$。</span>

實務上樣本大小 $n$ 必為有限值；當 $n$ 足夠大、$p$ 很小且 $np$ 適中時，常以參數為 $\lambda=np$ 的[卜瓦松分配](/lecture-notes/poisson-process-and-distribution/#def-poisson-distribution)近似求算[二項分配](/lecture-notes/binomial-distribution/#def-binomial)的機率值。

</div>

<div id="ex-standardized-bernoulli-sum-to-normal" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.7</div>

<div lang="en" markdown="1">
Let $X_1,X_2,\ldots,X_n$ be a random sample from <span class="text-nowrap">$\mathrm{Bin}(1,p)$.</span> Use the moment generating function to show that

$$
\frac{\,\sum_{i=1}^{n}X_i-np\,}{\,\sqrt{np(1-p)}\,}\dconv Z\sim\mathcal{N}(0,1)
$$

without invoking the central limit theorem.
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
\begin{gathered}
e^{\frac{(1-p)t}{\sqrt{np(1-p)}}}=1+\frac{(1-p)t}{\sqrt{np(1-p)}}+\frac{(1-p)^{2}t^{2}}{2np(1-p)}+o\Bigl(\frac{1}{\,n\,}\Bigr)\\[0.45em]
e^{\frac{-pt}{\sqrt{np(1-p)}}}=1-\frac{pt}{\sqrt{np(1-p)}}+\frac{p^{2}t^{2}}{2np(1-p)}+o\Bigl(\frac{1}{\,n\,}\Bigr)
\end{gathered}
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

可令 $Z\sim\mathcal{N}(0,1)$ 服從標準常態分配，其 mgf 為 $M_{\sssig Z}(t)=e^{\frac{\,t^{2}\,}{2}},\ t\in\mathbb{R}$ 這個函數，對照上式即得

$$
\lim_{n\to\infty}M_{\sssig Z_n}(t)=M_{\sssig Z}(t),\ \forall\,t\in\mathbb{R}
$$

由列維連續性定理知

$$
Z_n=\frac{\,\sum_{i=1}^{n}X_i-np\,}{\,\sqrt{np(1-p)}\,}\dconv Z\sim\mathcal{N}(0,1)
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

上述推導將 $e^{\frac{(1-p)t}{\sqrt{np(1-p)}}}$ 與 $e^{\frac{-pt}{\sqrt{np(1-p)}}}$ 分別在 $0$ 處作泰勒展開，並將三次以上的高階項合併記為小 o 符號 <span class="text-nowrap">$o\bigl(\frac{1}{\,n\,}\bigr)$，</span>表示該餘項與 $1/n$ 的比值在 $n\to\infty$ 時趨近於 <span class="text-nowrap">$0$。</span>由於 $o\bigl(\frac{1}{\,n\,}\bigr)$ 收斂至 $0$ 的速率快於 <span class="text-nowrap">$\frac{\,a\,}{n}$，</span>故加入該餘項並不影響指數極限值，此即

$$
\lim_{n\to\infty}\biggl[1+\frac{\,a\,}{n}+o\Bigl(\frac{1}{\,n\,}\Bigr)\biggr]^{n}=e^{a}
$$

此外，本題亦可視為後文中央極限定理 <span lang="en">(central limit theorem)</span> 在伯努利母體下的特例，屆時可直接引用該定理求得同一極限分配。

</div>

<div id="ex-negative-binomial-to-poisson" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.8</div>

<div lang="en" markdown="1">
Let <span class="text-nowrap">$X\sim\mathcal{NB}(r,p)$,</span> <span class="text-nowrap">$x=0,1,\ldots$</span> State the conditions under which $X$ converges in distribution to a Poisson distribution, and prove the convergence under those conditions.
</div>

若 <span class="text-nowrap">$r\to\infty$、</span>$p\to1$ 且 $r(1-p)=\lambda>0$ 為一定值，則 $X$ 可分配收斂至 $W\sim\mathrm{Poi}(\lambda)$ 這個分配，證明如下。

由於 $r(1-p)=\lambda\Longleftrightarrow(1-p)=\frac{\,\lambda\,}{r}$ 成立，也就是 $p=1-\frac{\,\lambda\,}{r}$ 這層關係，則 $X$ 之 mgf 可改寫為

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
\begin{gathered}
\lim_{r\to\infty}\biggl[1-\frac{\,\lambda\,}{r}\biggr]^{r}=e^{-\lambda}\\[0.45em]
\lim_{r\to\infty}\biggl[1-\frac{\,\lambda e^{t}\,}{r}\biggr]^{-r}=e^{\lambda e^{t}},\ t<-\ln(1-p)
\end{gathered}
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

則令 $W\sim\mathrm{Poi}(\lambda)$ 服從卜瓦松分配，其 mgf 為 $M_{\sssig W}(t)=e^{\lambda(e^{t}-1)},\ t\in\mathbb{R}$ 這個函數，我們有

$$
\lim_{r\to\infty}M_{\sssig X}(t)=M_{\sssig W}(t),\ \forall\,t\in\mathbb{R}
$$

由列維連續性定理知

$$
X\dconv W\sim\mathrm{Poi}(\lambda)
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

此處 $X$ 記錄一系列伯努利實驗中累積至第 $r$ 次成功前的失敗次數；當 $r\to\infty$ 時，實驗總次數亦隨之趨於無窮大。此一極限機制與 [Example 5.6](#ex-binomial-to-poisson) 完全對稱，差別僅在於計數對象由「成功次數」換成「失敗次數」，故收斂條件由 $p\to0$ 改為 $p\to1$ (即單次失敗機率 <span class="text-nowrap">$1-p\to0$)，</span>而參數乘積定值條件 $r(1-p)=\lambda$ 亦對應前題的 <span class="text-nowrap">$np=\lambda$。</span>

</div>

上述三例顯示，許多常見分配在特定的參數極限條件下具有漸近對應關係；後文介紹中央極限定理時，還將進一步建立更廣泛的常態近似關係。

## 極限分配為一個常數的統計量

統計量本身雖具有隨機性，隨著樣本大小 $n\to\infty$ 卻可能分配收斂至一個固定常數 (即退化隨機變數)；此一性質正是數理統計學中的**一致性 <span lang="en">(consistency)</span>**，以下先透過兩道常見統計量的例題觀察此現象。

<div id="ex-xbar-consistency-mgf" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.9 ($\overline{X}$ 的一致性)</div>

<div lang="en" markdown="1">
Let $X_1,\ldots,X_n\iidto\mathcal{N}(\mu,\sigma^{2})$, and let $\overline{X}=\frac{1}{\,n\,}\sum_{i=1}^{n}X_i$ be the sample mean. Find the limiting distribution of <span class="text-nowrap">$\overline{X}$.</span>
</div>

由 $X_1,\ldots,X_n\iidto\mathcal{N}(\mu,\sigma^{2})$ 可知其 mgf 為 $M_{\sssig X_i}(t)=e^{\mu t+\frac{\sigma^{2}}{2}t^{2}},\ t\in\mathbb{R}$ 這個函數，再由獨立性可得

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

令 $W\equiv\mu$ 為一退化隨機變數，具 mgf $M_{\sssig W}(t)=e^{\mu t},\ t\in\mathbb{R}$ 這個函數，我們有

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

本題反映出樣本平均數 $\overline{X}$ 作為 $\mu$ 的估計量所具備的一致性；當樣本大小趨於無窮大時，$\overline{X}$ 的抽樣分配退化集中於母體期望值 <span class="text-nowrap">$\mu$。</span>此外，即便樣本 $X_1,\ldots,X_n$ 並非抽自[常態母體](/lecture-notes/normal-distribution/#def-normal)，只要母體期望值與有限變異數存在，後文的弱大數法則仍保證 $\overline{X}$ 具備此一性質。

</div>

與樣本平均數 $\overline{X}$ 相對應，用以推論母體變異數 $\sigma^{2}$ 的樣本變異數 $S^{2}$ 同樣具備一致性，見下列例題。

<div id="ex-s-squared-consistency-mgf" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.10 ($S^{2}$ 的一致性)</div>

<div lang="en" markdown="1">
Let $X_1,\ldots,X_n\iidto\mathcal{N}(\mu,\sigma^{2})$, and let $S^{2}=\frac{1}{\,n-1\,}\sum_{i=1}^{n}(X_i-\overline{X})^{2}$ be the sample variance. Find the limiting distribution of <span class="text-nowrap">$S^{2}$.</span>
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

令 $W\equiv\sigma^{2}$ 為一退化隨機變數，具 mgf $M_{\sssig W}(t)=e^{\sigma^{2}t},\ t\in\mathbb{R}$ 這個函數，我們有

$$
\lim_{n\to\infty}M_{\sssig S^{2}}(t)=M_{\sssig W}(t),\ t\in\mathbb{R}
$$

由列維連續性定理知

$$
S^{2}=\frac{1}{\,n-1\,}\sum_{i=1}^{n}(X_i-\overline{X})^{2}\dconv W\equiv\sigma^{2}
$$

</div>

## 本篇小結

[Theorem 5.1](#thm-levys-continuity-thm) 把求極限分配的工具由 cdf 換成 mgf。若 $\lbrace X_n\rbrace_{n=1}^{\infty}$ 的 mgf 在 $-h<t<h$ 這一段區間上逐點收斂至某個隨機變數 $X$ 的 mgf，則在 $F_{\sssig X}$ 的每一個連續點上 $F_n$ 都收斂至 <span class="text-nowrap">$F_{\sssig X}$，</span>也就是 <span class="text-nowrap">$X_n\dconv X$，</span>而這個極限的 mgf 稱為極限動差母函數。之所以能這樣做，靠的是 mgf 與分配之間的一一對應。

前三道例題示範的是常見分配之間的極限關係。[Example 5.6](#ex-binomial-to-poisson) 由伯努利分配的可加性得到 $Y_n\sim\mathrm{Bin}(n,p)$ 這個結果，再把 $p$ 代換為 $\frac{\lambda}{\,n\,}$ 而湊出 $\bigl[1+\frac{\lambda(e^{t}-1)}{n}\bigr]^{n}$ 這個形式，取極限即得卜瓦松分配的 mgf。[Example 5.8](#ex-negative-binomial-to-poisson) 的結構相同，只是把條件由 $p\to0$ 與 $np=\lambda$ 換成 $p\to1$ 與 <span class="text-nowrap">$r(1-p)=\lambda$，</span>因為負二項分配在這裡記錄的是失敗次數而非成功次數。[Example 5.7](#ex-standardized-bernoulli-sum-to-normal) 則是把伯努利樣本和標準化，先由[線性組合的動差母函數](/lecture-notes/mgf-method-transformations/#thm-mgf-two-to-one)把期望值拆成連乘，再對兩個指數項各作一次泰勒展開，三次方以後的項一律併入 $o\bigl(\frac{1}{\,n\,}\bigr)$ 這一項，整條式子因而收成 $\bigl[1+\frac{t^{2}}{2n}+o\bigl(\frac{1}{\,n\,}\bigr)\bigr]^{n}$ 這個形式，極限為 $e^{\frac{t^{2}}{2}}$ 而得標準常態分配。這一題不用中央極限定理，靠的全是 mgf 的計算。

後兩道例題的極限不是一個分配，而是一個常數。[Example 5.9](#ex-xbar-consistency-mgf) 由常態分配的 mgf 求得 $M_{\sssig \overline{X}}(t)=e^{\mu t+\frac{\sigma^{2}}{2}\frac{t^{2}}{n}}$ 這個式子，其中的 $\frac{t^{2}}{\,n\,}$ 這一項隨 $n$ 消去，極限 $e^{\mu t}$ 正是退化在 $\mu$ 這一點上的隨機變數的 mgf。[Example 5.10](#ex-s-squared-consistency-mgf) 的作法一樣，先由[科克蘭定理](/lecture-notes/chi-squared-distribution/#thm-cochran-theorem)得到 $\frac{(n-1)S^{2}}{\sigma^{2}}\sim\chi^{2}(n-1)$ 這個結果，改寫為[伽瑪分配](/lecture-notes/gamma-distribution/#def-gamma-distribution)之後取其 mgf，以 $m=n-1$ 代換再取極限，得到 $e^{\sigma^{2}t}$ 這個結果。兩者分別對應 $\overline{X}$ 與 $S^{2}$ 的一致性，當樣本大到無窮時，這兩個統計量的隨機性完全消失，各自退化為它們所要推論的母體參數。

[下一篇](/lecture-notes/convergence-in-probability/)轉入機率收斂，那是一種比分配收斂更強的收斂型態，並會說明兩者之間的蘊含關係，以及極限為常數時兩者何以等價。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
