---
title: "負二項分配"
subtitle: "The Negative Binomial Distribution"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 4
topic: 6
order: 406
permalink: /lecture-notes/negative-binomial-distribution/
date: 2026-08-12
published: false
excerpt: "負二項分配描述獨立伯努利實驗直到累計第 $r$ 次成功所需的實驗次數。本篇藉負二項級數推導其期望值 $r/p$ 與變異數 $rq/p^{2}$ 及動差母函數，說明它作為獨立同參數幾何變數之和的可加性及與二項分配的對偶關係。"
---

[上一篇](/lecture-notes/geometric-distribution-examples/)以六道例題演練[幾何分配](/lecture-notes/geometric-distribution-memoryless/#def-geometric)的計算，其中的隨機變數記錄的都是進行伯努利實驗，直到出現第一次成功實驗所需要的實驗次數。若把「第一次成功」換成「第 $r$ 次成功」，所需要的實驗次數所服從的分配，就是本篇所要介紹的負二項分配。

驗證幾何分配的機率函數合法時，我們用的是[幾何級數](/lecture-notes/geometric-distribution-memoryless/#thm-geometric-series)；把成功次數由一次推到 $r$ 次，所需要的工具則是[負二項級數](#thm-negative-binomial-series)。本篇因而先由這個級數談起，再給出負二項分配的定義，完整證明其機率函數為一個合法的機率函數，以及期望值、變異數與動差母函數的公式。接著說明幾項延伸性質，並給出二項分配與負二項分配之間的對偶關係，最後以三道例題作為演練。

## 負二項級數

<div id="thm-negative-binomial-series" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 4.7 (負二項級數, negative binomial series)</div>

**負二項級數 <span lang="en">(negative binomial series)</span>** 是下列的級數:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
(1-q)^{-r}=\sum_{k=0}^{\infty}\binom{k+r-1}{k}q^{k}=\sum_{k=0}^{\infty}\binom{k+r-1}{r-1}q^{k}=\sum_{k=0}^{\infty}\binom{-r}{k}(-q)^{k}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
(1-q)^{-r}&=\sum_{k=0}^{\infty}\binom{k+r-1}{k}q^{k}\\[0.45em]
&=\sum_{k=0}^{\infty}\binom{k+r-1}{r-1}q^{k}\\[0.45em]
&=\sum_{k=0}^{\infty}\binom{-r}{k}(-q)^{k}
\end{aligned}
$$

</div>

上式中，我們要求 <span class="text-nowrap">$\lvert q\rvert<1$，</span>同時 $r$ 為任意一個正整數。

</div>

<div class="topic-proof" markdown="1">
**Proof.**

若令函數 <span class="text-nowrap">$g(q)=(1-q)^{-r}$，</span>則對 $g(q)$ 進行馬克勞林展開，我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
(1-q)^{-r}&=\frac{(1-0)^{-r}}{0!}q^{0}+\frac{r(1-0)^{-r-1}}{1!}q^{1}+\frac{r(r+1)(1-0)^{-r-2}}{2!}q^{2}+\cdots\\[0.45em]
&=\frac{1}{0!}q^{0}+\frac{r}{1!}q^{1}+\frac{(r+1)r}{2!}q^{2}+\frac{(r+2)(r+1)r}{3!}q^{3}+\cdots\\[0.45em]
&=\sum_{k=0}^{\infty}\frac{P^{k+r-1}_{k}}{k!}\,q^{k}=\sum_{k=0}^{\infty}\binom{k+r-1}{k}q^{k}=\sum_{k=0}^{\infty}\binom{k+r-1}{r-1}q^{k}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
(1-q)^{-r}&=\frac{(1-0)^{-r}}{0!}q^{0}+\frac{r(1-0)^{-r-1}}{1!}q^{1}\\[0.25em]
&\qquad +\frac{r(r+1)(1-0)^{-r-2}}{2!}q^{2}+\cdots\\[0.45em]
&=\frac{1}{0!}q^{0}+\frac{r}{1!}q^{1}+\frac{(r+1)r}{2!}q^{2}\\[0.25em]
&\qquad +\frac{(r+2)(r+1)r}{3!}q^{3}+\cdots\\[0.45em]
&=\sum_{k=0}^{\infty}\frac{P^{k+r-1}_{k}}{k!}\,q^{k}\\[0.25em]
&=\sum_{k=0}^{\infty}\binom{k+r-1}{k}q^{k}\\[0.25em]
&=\sum_{k=0}^{\infty}\binom{k+r-1}{r-1}q^{k}
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

[上述定理](#thm-negative-binomial-series)末式中的廣義組合數定義為

$$
\binom{-r}{k}=\frac{\,(-r)(-r-1)\cdots(-r-k+1)\,}{k!}
$$

由此定義可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\binom{k+r-1}{k}&=\frac{\,(k+r-1)(k+r-2)\cdots(r+1)r(r-1)\cdots1\,}{(r-1)!\,k!}\\[0.45em]
&=\frac{\,(k+r-1)(k+r-2)\cdots(r+1)r\,}{k!}\\[0.45em]
&=(-1)^{k}\frac{\,(-k-r+1)(-k-r+2)\cdots(-r-1)(-r)\,}{k!}\\[0.45em]
&=(-1)^{k}\binom{-r}{k}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\binom{k+r-1}{k}&=\Bigl((k+r-1)(k+r-2)\cdots\\[0.4em]
&\qquad (r+1)r(r-1)\cdots1\Bigr)\\[0.4em]
&\qquad\Big/\bigl((r-1)!\,k!\bigr)\\[0.4em]
&=\frac{\,(k+r-1)(k+r-2)\cdots(r+1)r\,}{k!}\\[0.4em]
&=(-1)^{k}\Bigl((-k-r+1)(-k-r+2)\cdots\\[0.4em]
&\qquad (-r-1)(-r)\Bigr)\Big/k!\\[0.4em]
&=(-1)^{k}\binom{-r}{k}
\end{aligned}
$$

</div>

將級數改寫為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
(1-q)^{-r}=\sum_{k=0}^{\infty}\binom{-r}{k}(-q)^{k}=\sum_{k=0}^{\infty}\binom{-r}{k}1^{-r-k}(-q)^{k}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
(1-q)^{-r}&=\sum_{k=0}^{\infty}\binom{-r}{k}(-q)^{k}\\[0.45em]
&=\sum_{k=0}^{\infty}\binom{-r}{k}1^{-r-k}(-q)^{k}
\end{aligned}
$$

</div>

其形式與[二項式定理](/lecture-notes/moment-system/#thm-binomial)相對應，差別在於次方改為負整數 $-r$ 且加總延伸至無窮項，故稱為**負二項級數**。雖然負二項級數因形式類比二項式定理而得名，其對應的負二項分配在實驗結構上實為幾何分配的推廣，下文隨即說明。

</div>

## 負二項分配

<div id="def-negative-binomial" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 4.7 (負二項分配, negative binomial distribution)</div>

**適用範圍**:

令 $X$ 表進行伯努利實驗，直到出現第 $r$ 次成功實驗所需要的**實驗次數**。

**值域範圍**:

$$
\mathcal{R}_{\sssig X}=\lbrace\,r,r+1,\ldots,\infty\,\rbrace
$$

**表示式**:

$$
X\sim\mathcal{NB}(r,\ p)
$$

**參數與參數範圍**:

$0<p<1$ 為伯努利實驗中，成功類的發生機率；$r\in\mathbb{N}$ 為成功類發生的次數。

**機率函數**:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
p_{\sssig X}(x)=\binom{x-1}{r-1}p^{r}\,(1-p)^{x-r}=\binom{x-1}{r-1}p^{r}\,q^{x-r},\ x=r,r+1,\ldots,\infty
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig X}(x)&=\binom{x-1}{r-1}p^{r}\,(1-p)^{x-r}\\[0.45em]
&=\binom{x-1}{r-1}p^{r}\,q^{x-r},\\[0.25em]
&\qquad x=r,r+1,\ldots,\infty
\end{aligned}
$$

</div>

其中，$q=1-p$ 為失敗類發生的機率。

**期望值、變異數、動差母函數**:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\mathbb{E}(X)=\frac{r}{\,p\,},\qquad \mathrm{Var}(X)=\frac{\,r(1-p)\,}{p^{2}}=\frac{rq}{\,p^{2}\,}\\[0.6em]
M_{\sssig X}(t)=\biggl[\frac{pe^{t}}{\,1-(1-p)e^{t}\,}\biggr]^{r}=\biggl(\frac{pe^{t}}{\,1-qe^{t}\,}\biggr)^{r},\ t<-\ln q
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{E}(X)=\frac{r}{\,p\,},\\[0.5em]
\mathrm{Var}(X)=\frac{\,r(1-p)\,}{p^{2}}=\frac{rq}{\,p^{2}\,}
\end{gathered}
$$

$$
\begin{aligned}
M_{\sssig X}(t)&=\biggl[\frac{pe^{t}}{\,1-(1-p)e^{t}\,}\biggr]^{r}\\[0.3em]
&=\biggl(\frac{pe^{t}}{\,1-qe^{t}\,}\biggr)^{r},\ t<-\ln q
\end{aligned}
$$

</div>

</div>

負二項分配 <span lang="en">(negative binomial distribution)</span> 有一些地方需要注意:

(1) 我們證明其機率函數為一個合法的機率函數與期望值、變異數及動差母函數如下:
{: .topic-paren-item}

<div class="topic-proof" markdown="1">
**Proof.**

先驗證機率函數的加總為 <span class="text-nowrap">$1$，</span>即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\sum_{x\in\mathcal{R}_{\sssig X}}p_{\sssig X}(x)&=\sum_{x=r}^{\infty}\binom{x-1}{r-1}p^{r}q^{x-r}=p^{r}\sum_{k=0}^{\infty}\binom{k+r-1}{r-1}q^{k}\\[0.45em]
&=p^{r}(1-q)^{-r}=p^{r}p^{-r}=1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\sum_{x\in\mathcal{R}_{\sssig X}}p_{\sssig X}(x)&=\sum_{x=r}^{\infty}\binom{x-1}{r-1}p^{r}q^{x-r}\\[0.25em]
&=p^{r}\sum_{k=0}^{\infty}\binom{k+r-1}{r-1}q^{k}\\[0.25em]
&=p^{r}(1-q)^{-r}=p^{r}p^{-r}=1
\end{aligned}
$$

</div>

接著求期望值，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\sum_{x=r}^{\infty}x\binom{x-1}{r-1}p^{r}q^{x-r}=\sum_{x=r}^{\infty}x\frac{(x-1)!}{\,(x-r)!(r-1)!\,}p^{r}q^{x-r}\\[0.45em]
&=\frac{r}{p}\sum_{x=r}^{\infty}\frac{x!}{\,(x-r)!\,r!\,}p^{r+1}q^{x-r}=\frac{r}{p}\sum_{x=r}^{\infty}\binom{x}{r}p^{r+1}q^{x-r}\\[0.45em]
&=\frac{r}{p}\sum_{s=t}^{\infty}\binom{s-1}{t-1}p^{t}q^{s-t}=\frac{r}{p}\\[0.45em]
&\qquad\qquad [\text{令 }x=s-1,\ r=t-1]
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\sum_{x=r}^{\infty}x\binom{x-1}{r-1}p^{r}q^{x-r}\\[0.45em]
&=\sum_{x=r}^{\infty}x\frac{(x-1)!}{\,(x-r)!(r-1)!\,}p^{r}q^{x-r}\\[0.45em]
&=\frac{r}{p}\sum_{x=r}^{\infty}\frac{x!}{\,(x-r)!\,r!\,}p^{r+1}q^{x-r}\\[0.45em]
&=\frac{r}{p}\sum_{x=r}^{\infty}\binom{x}{r}p^{r+1}q^{x-r}\\[0.45em]
&=\frac{r}{p}\sum_{s=t}^{\infty}\binom{s-1}{t-1}p^{t}q^{s-t}=\frac{r}{p}\\[0.45em]
&\quad [\text{令 }x=s-1,\ r=t-1]
\end{aligned}
$$

</div>

又可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[(X+1)X\bigr]&=\sum_{x=r}^{\infty}(x+1)x\binom{x-1}{r-1}p^{r}q^{x-r}\\[0.45em]
&=\sum_{x=r}^{\infty}(x+1)x\frac{(x-1)!}{\,(x-r)!(r-1)!\,}p^{r}q^{x-r}\\[0.45em]
&=\frac{\,(r+1)r\,}{p^{2}}\sum_{x=r}^{\infty}\frac{(x+1)!}{\,(x-r)!\,(r+1)!\,}p^{r+2}q^{x-r}\\[0.45em]
&=\frac{\,(r+1)r\,}{p^{2}}\sum_{x=r}^{\infty}\binom{x+1}{r+1}p^{r+2}q^{x-r}\\[0.45em]
&=\frac{\,(r+1)r\,}{p^{2}}\sum_{s=t}^{\infty}\binom{s-1}{t-1}p^{t}q^{s-t}=\frac{\,(r+1)r\,}{p^{2}}\\[0.45em]
&\qquad\qquad [\text{令 }x=s-2,\ r=t-2]
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}\bigl[(X+1)X\bigr]\\[0.3em]
&=\sum_{x=r}^{\infty}(x+1)x\binom{x-1}{r-1}p^{r}q^{x-r}\\[0.25em]
&=\sum_{x=r}^{\infty}(x+1)x\frac{(x-1)!}{\,(x-r)!(r-1)!\,}p^{r}q^{x-r}\\[0.25em]
&=\frac{\,(r+1)r\,}{p^{2}}\sum_{x=r}^{\infty}\frac{(x+1)!}{\,(x-r)!\,(r+1)!\,}p^{r+2}q^{x-r}\\[0.25em]
&=\frac{\,(r+1)r\,}{p^{2}}\sum_{x=r}^{\infty}\binom{x+1}{r+1}p^{r+2}q^{x-r}\\[0.25em]
&=\frac{\,(r+1)r\,}{p^{2}}\sum_{s=t}^{\infty}\binom{s-1}{t-1}p^{t}q^{s-t}\\[0.25em]
&=\frac{\,(r+1)r\,}{p^{2}}\\[0.25em]
&\quad\ \ [\text{令 }x=s-2,\ r=t-2]
\end{aligned}
$$

</div>

由此可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\bigl(X^{2}\bigr)=\mathbb{E}\bigl[(X+1)X\bigr]-\mathbb{E}(X)=\frac{\,r^{2}+r-rp\,}{p^{2}}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl(X^{2}\bigr)&=\mathbb{E}\bigl[(X+1)X\bigr]-\mathbb{E}(X)\\[0.45em]
&=\frac{\,r^{2}+r-rp\,}{p^{2}}
\end{aligned}
$$

</div>

則變異數為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}(X)=\mathbb{E}\bigl(X^{2}\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}=\frac{r^{2}+r-rp}{p^{2}}-\biggl(\frac{r}{p}\biggr)^{2}=\frac{\,r(1-p)\,}{p^{2}}=\frac{\,rq\,}{p^{2}}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(X)&=\mathbb{E}\bigl(X^{2}\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}\\[0.45em]
&=\frac{r^{2}+r-rp}{p^{2}}-\biggl(\frac{r}{p}\biggr)^{2}\\[0.45em]
&=\frac{\,r(1-p)\,}{p^{2}}=\frac{\,rq\,}{p^{2}}
\end{aligned}
$$

</div>

最後求動差母函數，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{\sssig X}(t)&=\mathbb{E}\bigl(e^{tX}\bigr)=\sum_{x=r}^{\infty}e^{tx}\binom{x-1}{r-1}p^{r}q^{x-r}\\[0.45em]
&=\bigl(pe^{t}\bigr)^{r}\sum_{x=r}^{\infty}\binom{x-1}{r-1}e^{t(x-r)}q^{x-r}=\bigl(pe^{t}\bigr)^{r}\sum_{x=r}^{\infty}\binom{x-1}{r-1}\bigl(qe^{t}\bigr)^{x-r}\\[0.45em]
&=\bigl(pe^{t}\bigr)^{r}\cdot\bigl(1-qe^{t}\bigr)^{-r}=\biggl(\frac{pe^{t}}{1-qe^{t}}\biggr)^{r},\ t<-\ln q
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig X}(t)&=\mathbb{E}\bigl(e^{tX}\bigr)\\[0.45em]
&=\sum_{x=r}^{\infty}e^{tx}\binom{x-1}{r-1}p^{r}q^{x-r}\\[0.45em]
&=\bigl(pe^{t}\bigr)^{r}\sum_{x=r}^{\infty}\binom{x-1}{r-1}e^{t(x-r)}q^{x-r}\\[0.45em]
&=\bigl(pe^{t}\bigr)^{r}\sum_{x=r}^{\infty}\binom{x-1}{r-1}\bigl(qe^{t}\bigr)^{x-r}\\[0.45em]
&=\bigl(pe^{t}\bigr)^{r}\cdot\bigl(1-qe^{t}\bigr)^{-r}\\[0.45em]
&=\biggl(\frac{pe^{t}}{1-qe^{t}}\biggr)^{r},\ t<-\ln q
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

(2) 由負二項分配的定義可得以下延伸性質:
{: .topic-paren-item}

第一，我們有
{: .topic-paren-cont}

$$
\mathrm{Geo}(p)=\mathcal{NB}(r=1,\ p)
$$

當 $r=1$ 時，負二項分配記錄的即是直到第一次成功實驗出現所需的實驗次數，與幾何分配的定義完全一致。
{: .topic-paren-cont}

第二，若 $X\sim\mathcal{NB}(r_1,\ p),\ Y\sim\mathcal{NB}(r_2,\ p)$ 且 <span class="text-nowrap">$X\indep Y$，</span>則
{: .topic-paren-cont}

$$
W=X+Y\sim\mathcal{NB}(r_1+r_2,\ p)
$$

<div class="topic-proof" markdown="1">
**Proof.**

由[獨立隨機變數線性組合的動差母函數之定理](/lecture-notes/mgf-method-transformations/#thm-mgf-two-to-one)可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{\sssig W}(t)&=M_{\sssig X}(t)\,M_{\sssig Y}(t)\\[0.45em]
&=\biggl(\frac{pe^{t}}{\,1-qe^{t}\,}\biggr)^{r_1}\,\biggl(\frac{pe^{t}}{\,1-qe^{t}\,}\biggr)^{r_2}=\biggl(\frac{pe^{t}}{\,1-qe^{t}\,}\biggr)^{r_1+r_2},\ t<-\ln q
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig W}(t)&=M_{\sssig X}(t)\,M_{\sssig Y}(t)\\[0.45em]
&=\biggl(\frac{pe^{t}}{\,1-qe^{t}\,}\biggr)^{r_1}\,\biggl(\frac{pe^{t}}{\,1-qe^{t}\,}\biggr)^{r_2}\\[0.45em]
&=\biggl(\frac{pe^{t}}{\,1-qe^{t}\,}\biggr)^{r_1+r_2},\ t<-\ln q
\end{aligned}
$$

</div>

則由[動差母函數的唯一性](/lecture-notes/uniqueness-of-the-mgf/#thm-mgf-uniqueness)可知

$$
W=X+Y\sim\mathcal{NB}(r_1+r_2,\ p)
$$

原式得證。 <span class="topic-qed">$\square$</span>
</div>

這個性質被稱作負二項分配的可加性，其限制是 $X$ 與 $Y$ 必須獨立，而且**成功機率必須相同**。
{: .topic-paren-cont}

第三，若 $X\sim\mathrm{Geo}(p)\indep Y\sim\mathrm{Geo}(p)$ 成立，則
{: .topic-paren-cont}

$$
W=X+Y\sim\mathcal{NB}(r=2,\ p)
$$

結合前兩項性質即可推得上式，此處不再另證。進一步推廣至 $r$ 個獨立同分配的幾何變數之和，若 $X_1,\ldots,X_r\overset{\mathrm{iid}}{\sim}\mathrm{Geo}(p)$ 成立，則
{: .topic-paren-cont}

$$
W=\sum_{i=1}^{r}X_i\sim\mathcal{NB}(r,\ p)
$$

第四，既然負二項分配可以視為 $r$ 個獨立幾何分配的和，那麼與幾何分配相同，負二項分配也將有兩種定義，分別是**實驗負二項**與**失敗負二項**。
{: .topic-paren-cont}

若令 $X$ 與 $Y$ 分別表示進行伯努利實驗，直到出現第 $r$ 次成功實驗所需要的**實驗次數**與**失敗次數**，則 <span class="text-nowrap">$Y=X-r$。</span>失敗負二項 $Y$ 的特徵與實驗負二項 $X$ 略有不同:
{: .topic-paren-cont}

$$
\mathcal{R}_{\sssig Y}=\lbrace\,0,1,\ldots,\infty\,\rbrace
$$

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
p_{\sssig Y}(y)=\binom{y+r-1}{r-1}p^{r}(1-p)^{y}=\binom{-r}{y}p^{r}(p-1)^{y},\ y=0,1,\ldots,\infty
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig Y}(y)&=\binom{y+r-1}{r-1}p^{r}(1-p)^{y}\\[0.45em]
&=\binom{-r}{y}p^{r}(p-1)^{y},\\[0.25em]
&\qquad y=0,1,\ldots,\infty
\end{aligned}
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(Y)=\mathbb{E}(X-r)=\mathbb{E}(X)-r=\frac{r}{\,p\,}-\frac{\,pr\,}{p}=\frac{\,r(1-p)\,}{p}=\frac{\,rq\,}{p}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(Y)&=\mathbb{E}(X-r)=\mathbb{E}(X)-r\\[0.45em]
&=\frac{r}{\,p\,}-\frac{\,pr\,}{p}=\frac{\,r(1-p)\,}{p}=\frac{\,rq\,}{p}
\end{aligned}
$$

</div>

$$
\mathrm{Var}(Y)=\mathrm{Var}(X-r)=\mathrm{Var}(X)
$$

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
M_{\sssig Y}(t)=\mathbb{E}\bigl(e^{tY}\bigr)=\mathbb{E}\bigl[e^{t(X-r)}\bigr]=\mathbb{E}\bigl(e^{tX}\bigr)e^{-rt}=\biggl(\frac{p}{\,1-qe^{t}\,}\biggr)^{r},\ t<-\ln q
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig Y}(t)&=\mathbb{E}\bigl(e^{tY}\bigr)=\mathbb{E}\bigl[e^{t(X-r)}\bigr]\\[0.45em]
&=\mathbb{E}\bigl(e^{tX}\bigr)e^{-rt}\\[0.45em]
&=\biggl(\frac{p}{\,1-qe^{t}\,}\biggr)^{r},\ t<-\ln q
\end{aligned}
$$

</div>

(3) 負二項分配之於幾何分配的關係，恰如[二項分配](/lecture-notes/binomial-distribution/#def-binomial)之於[伯努利分配](/lecture-notes/bernoulli-trials-and-distribution/#def-bernoulli)的關係；由此可推得二項分配與負二項分配之間的**對偶關係 <span lang="en">(dual relationship)</span>**，可敘述如下
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\boxed{\ \text{令 }X\sim\mathrm{Bin}(n,\ p)\ \text{且}\ Y\sim\mathcal{NB}(r,\ p)\text{，則 }\mathbb{P}(X<r)=\mathbb{P}(Y>n)\ }
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\boxed{
\begin{gathered}
\text{令 }X\sim\mathrm{Bin}(n,\ p)\ \text{且}\ Y\sim\mathcal{NB}(r,\ p)\text{，}\\[0.45em]
\text{則 }\mathbb{P}(X<r)=\mathbb{P}(Y>n)
\end{gathered}
}
$$

</div>

上式的直觀意義在於，「前 $n$ 次實驗中成功不到 $r$ 次」($X<r$) 與「第 $r$ 次成功所需的實驗次數超過 $n$ 次」($Y>n$) 描述的是同一個事件。
{: .topic-paren-cont}

(4) 負二項分配與幾何分配的最後一次實驗皆必為成功實驗；差別在於除最後一次外，幾何分配的前 $x-1$ 次皆為失敗，而負二項分配的前 $x-1$ 次中恰有 $r-1$ 次成功與 $x-r$ 次失敗。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

前 $x-1$ 次實驗中的 $r-1$ 次成功可落在任意位置，故機率函數須乘上組合數 <span class="text-nowrap">$\binom{x-1}{r-1}$；</span>也因為此組合因子隨 $x$ 改變，當 $r\geqslant2$ 時相鄰兩項 $p\_{\sssig X}(a)$ 與 $p\_{\sssig X}(a+1)$ 的比值不再固定，故**負二項分配不再具有[無記憶性](/lecture-notes/geometric-distribution-memoryless/#thm-memoryless)**。

</div>

## 負二項分配的例題

<div id="ex-negative-binomial-1" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.16</div>

<div lang="en" markdown="1">
An expert sharpshooter misses the target, on average, $5\%$ of the time.

<ol class="topic-list-paren">
  <li>What is the probability that in $20$ shots, the sharpshooter will hit the target $18$ or more times?</li>
  <li>What is the probability that the sharpshooter will need $10$ shots until missing the target for the first time?</li>
  <li>What is the probability that the sharpshooter will miss the target for the second time on the <span class="text-nowrap">$25^{\text{th}}$</span> shot?</li>
</ol>
</div>

(1) 由題意可知，每次射擊皆為成功機率 $p=0.95$ 的伯努利實驗，則若令 $X$ 表 $20$ 次射擊中的擊中次數，可得
{: .topic-paren-item}

$$
X\sim\mathrm{Bin}(20,\ 0.95)
$$

所求為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X\geqslant18)=\sum_{x=18}^{20}\binom{20}{x}(0.95)^{x}(0.05)^{20-x}\fallingdotseq0.9245
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X\geqslant18)&=\sum_{x=18}^{20}\binom{20}{x}(0.95)^{x}(0.05)^{20-x}\\[0.45em]
&\fallingdotseq0.9245
\end{aligned}
$$

</div>

(2) 令 $Y$ 表直到第一次沒有擊中目標為止所需的擊發次數，則
{: .topic-paren-item}

$$
Y\sim\mathrm{Geo}(p=0.05)
$$

故所求為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(Y=10)=(1-0.05)^{10-1}(0.05)^{1}\fallingdotseq0.03151
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(Y=10)&=(1-0.05)^{10-1}(0.05)^{1}\\[0.45em]
&\fallingdotseq0.03151
\end{aligned}
$$

</div>

(3) 令 $W$ 表直到第二次沒有擊中目標為止所需的擊發次數，則
{: .topic-paren-item}

$$
W\sim\mathcal{NB}(r=2,\ p=0.05)
$$

故所求為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(W=25)=\binom{25-1}{2-1}(1-0.05)^{25-2}(0.05)^{2}\fallingdotseq0.01844
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(W=25)&=\binom{25-1}{2-1}(1-0.05)^{25-2}(0.05)^{2}\\[0.25em]
&\fallingdotseq0.01844
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

本題組的關鍵在於各小題對「成功」事件的界定不同。第 (1) 小題以擊中目標為成功 (<span class="text-nowrap">$p=0.95$</span>)；第 (2)、(3) 小題關注未擊中的累積次數，故改將「未擊中目標」定義為伯努利實驗中的成功事件 (<span class="text-nowrap">$p=0.05$</span>)。

</div>

<div id="ex-negative-binomial-2" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.17</div>

<div lang="en" markdown="1">
In a championship series, the first team to win five games out of at most nine wins the title. Suppose that team $A$ has probability $0.6$ of winning any single game against team $B$ when both teams face each other in the championship series.

<ol class="topic-list-paren">
  <li>What is the probability that team $A$ will win the series within seven games?</li>
  <li>What is the probability that team $A$ will win the championship series?</li>
  <li>If both teams instead face each other in a best-of-five playoff series (where the first team to win three games wins), what is the probability that team $A$ will win the playoff series?</li>
</ol>
</div>

(1) 題目所要求之條件為 $7$ 場內贏得系列賽，代表贏得 $5$ 場比賽所需場次不超過 $7$ 場，則可令 $X$ 表 $A$ 隊直到第 $5$ 次勝利所需要的比賽場次，由此可得
{: .topic-paren-item}

$$
X\sim\mathcal{NB}(5,\ 0.6)
$$

所求即為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X\leqslant7)=\sum_{x=5}^{7}\binom{x-1}{5-1}(0.4)^{x-5}(0.6)^{5}\fallingdotseq0.4199
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X\leqslant7)&=\sum_{x=5}^{7}\binom{x-1}{5-1}(0.4)^{x-5}(0.6)^{5}\\[0.45em]
&\fallingdotseq0.4199
\end{aligned}
$$

</div>

(2) 承上題假設，所求為取得 $5$ 場勝利所需場次不超過上限之 $9$ 場之機率，故所求為
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X\leqslant9)=\sum_{x=5}^{9}\binom{x-1}{5-1}(0.4)^{x-5}(0.6)^{5}\fallingdotseq0.7334
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X\leqslant9)&=\sum_{x=5}^{9}\binom{x-1}{5-1}(0.4)^{x-5}(0.6)^{5}\\[0.45em]
&\fallingdotseq0.7334
\end{aligned}
$$

</div>

(3) 本題改為上限 $5$ 場的系列賽，勝利條件是取得 $3$ 場勝利所需場次不超過上限之 $5$ 場，則假設 $Y$ 表 $A$ 隊直到第 $3$ 次勝利所需要的比賽場次，可得
{: .topic-paren-item}

$$
Y\sim\mathcal{NB}(3,\ 0.6)
$$

所求即為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(Y\leqslant5)=\sum_{x=3}^{5}\binom{x-1}{3-1}(0.4)^{x-3}(0.6)^{3}=0.68256
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(Y\leqslant5)&=\sum_{x=3}^{5}\binom{x-1}{3-1}(0.4)^{x-3}(0.6)^{3}\\[0.45em]
&=0.68256
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

運動賽事常見的 BO $9$ 賽制 (Best of $9$ games，即 $9$ 戰 $5$ 勝制；一般奇數 $k$ 戰制由先取得 $(k+1)/2$ 勝者勝出，常見如 BO $5$ 與 BO $7$ 賽制) 至多進行 $9$ 場比賽，何以仍可用值域延伸至無窮大的負二項分配計算勝率？我們可設想即使 $B$ 隊已先取得 $5$ 勝而贏得系列賽，兩隊仍繼續對戰直到 $A$ 隊累計滿 $5$ 勝為止。在此延伸實驗下，「$A$ 隊贏得 $9$ 戰 $5$ 勝系列賽」與「$A$ 隊於第 $9$ 場以內取得第 $5$ 勝」(<span class="text-nowrap">$X\leqslant9$</span>) 為完全等價的事件；至於 $X>9$ 的所有結果，無論落在第幾場，皆對應 $A$ 隊已於前 $9$ 場內輸掉系列賽的情形，不影響勝率計算。

</div>

<div id="ex-negative-binomial-3" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.18</div>

<div lang="en" markdown="1">
Let $X_1,X_2,\ldots$ be a sequence of i.i.d. random variables with

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X_i=1)=p,\quad \mathbb{P}(X_i=0)=1-p,\quad \text{where}\ 0<p<1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{P}(X_i=1)=p,\quad \mathbb{P}(X_i=0)=1-p,\\[0.45em]
\text{where}\ 0<p<1
\end{gathered}
$$

</div>

Let $S_n=\sum_{i=1}^{n}X_i$ and $T_k=\min\lbrace n\mid S_n=k\rbrace$ for <span class="text-nowrap">$k\in\mathbb{N}$.</span> Find the distribution of <span class="text-nowrap">$T_k$.</span>
</div>

依照題目設定可知，若 <span class="text-nowrap">$T_{k}=t$，</span>則表示第 $t$ 次伯努利實驗必定為第 $k$ 次成功，此即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(T_{k}=t)=\mathbb{P}(S_{t-1}=k-1,\ X_t=1)=\mathbb{P}(S_{t-1}=k-1)\,\mathbb{P}(X_t=1)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(T_{k}=t)&=\mathbb{P}(S_{t-1}=k-1,\ X_t=1)\\[0.45em]
&=\mathbb{P}(S_{t-1}=k-1)\,\mathbb{P}(X_t=1)
\end{aligned}
$$

</div>

又由於 $S_{t-1}=\sum_{i=1}^{t-1}X_{i}\sim\mathrm{Bin}(t-1,\ p)$ 成立，故可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(S_{t-1}=k-1)\,\mathbb{P}(X_t=1)&=\binom{t-1}{k-1}p^{k-1}(1-p)^{t-k}\times p\\[0.45em]
&=\binom{t-1}{k-1}p^{k}(1-p)^{t-k},\ t=k,k+1,\ldots
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(S_{t-1}=k-1)\,\mathbb{P}(X_t=1)&=\binom{t-1}{k-1}p^{k-1}(1-p)^{t-k}\\[0.25em]
&\qquad\times p\\[0.25em]
&=\binom{t-1}{k-1}p^{k}(1-p)^{t-k},\\[0.25em]
&\qquad\qquad t=k,k+1,\ldots
\end{aligned}
$$

</div>

此即

<div class="topic-math-layout topic-math-layout--desktop topic-math-follow-before" markdown="1">

$$
p_{\sssig T_k}(t)=\binom{t-1}{k-1}p^{k}(1-p)^{t-k},\ t=k,k+1,\ldots\qquad\therefore\, T_{k}\sim\mathcal{NB}(k,\ p)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile topic-math-follow-before" markdown="1">

$$
\begin{aligned}
p_{\sssig T_k}(t)&=\binom{t-1}{k-1}p^{k}(1-p)^{t-k},\\[0.25em]
&\qquad\qquad t=k,k+1,\ldots\\[0.4em]
&\qquad\therefore\, T_{k}\sim\mathcal{NB}(k,\ p)
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

本題定義的 $T\_{k}=\min\lbrace n\mid S\_{n}=k\rbrace$ 為累積和首次達到 $k$ 的實驗次數。事件 $T\_{k}=t$ 發生，代表第 $t$ 次實驗必為成功 (<span class="text-nowrap">$X\_{t}=1$</span>)，且前 $t-1$ 次實驗中恰有 $k-1$ 次成功 (<span class="text-nowrap">$S\_{t-1}=k-1$</span>)。由於各次伯努利實驗獨立同分配，可將最後一次實驗分離出來，前 $t-1$ 次的成功總數服從 <span class="text-nowrap">$\mathrm{Bin}(t-1,\ p)$，</span>兩者機率相乘即得負二項分配的機率函數。

</div>

## 本篇小結

[Theorem 4.7](#thm-negative-binomial-series) 的負二項級數把 $(1-q)^{-r}$ 展開成 $q$ 的冪級數，係數是 $\binom{k+r-1}{k}$ 這個組合數，成立的條件為 <span class="text-nowrap">$\lvert q\rvert<1$。</span>證明的作法是直接對 $(1-q)^{-r}$ 作馬克勞林展開，逐項的係數即為排列數除以階乘。把組合數改寫成 $(-1)^{k}\binom{-r}{k}$ 之後，整個式子的形式與 [Theorem 2.18](/lecture-notes/moment-system/#thm-binomial) 的二項式定理相同，只是次方變成負的，這也是這個級數名稱的由來。

[Definition 4.7](#def-negative-binomial) 的負二項分配記錄的是進行伯努利實驗，直到出現第 $r$ 次成功實驗所需要的實驗次數，值域自 $r$ 起算，機率函數為 $\binom{x-1}{r-1}p^{r}q^{x-r}$ 這個式子，其中的組合數對應「前 $x-1$ 次之中哪 $r-1$ 次成功」的選法。證明的四個步驟依序為以負二項級數驗證機率函數的加總為 <span class="text-nowrap">$1$、</span>把 $x\binom{x-1}{r-1}$ 改寫成 $r\binom{x}{r}$ 這個形式，把加總湊成另一個負二項分配的機率函數而求得 <span class="text-nowrap">$\mathbb{E}(X)=\frac{r}{\,p\,}$、</span>再以 $\mathbb{E}\bigl[(X+1)X\bigr]$ 得到 $\mathbb{E}\bigl(X^{2}\bigr)$ 進而算出變異數 <span class="text-nowrap">$\frac{\,rq\,}{p^{2}}$，</span>最後直接由定義求得動差母函數。

定義之後的幾點說明依序涵蓋 $r=1$ 時負二項分配即為幾何分配、成功機率相同且彼此獨立的兩個負二項變數相加仍為負二項分配 (可加性)、$r$ 個獨立且成功機率相同的幾何變數相加即為負二項分配，以及實驗負二項與失敗負二項兩種定義的差別，後者記錄的是失敗次數 <span class="text-nowrap">$Y=X-r$，</span>值域自 $0$ 起算，期望值少了 $r$ 而變異數不變。可加性的證明只需把兩個動差母函數相乘，指數因而相加，再由動差母函數的唯一性辨識出結果。

負二項分配之於幾何分配的關係，與二項分配之於伯努利分配的關係相同，兩者因而有對偶關係。「$n$ 次實驗中成功不到 $r$ 次」與「第 $r$ 次成功所需的實驗次數超過 $n$ 次」講的是同一件事情。另一方面，負二項分配與幾何分配的最後一次實驗都一定是成功實驗，差別在於前面的 $x-1$ 次之中還有 $r-1$ 次成功，其位置不固定，因而引入了組合數，也因為這個組合數，相鄰兩個機率值不再成等比，負二項分配於是不再具有無記憶性。

三道例題各有側重。[Example 4.16](#ex-negative-binomial-1) 在同一個題組中把「成功」的定義換了兩次，前一小題以擊中為成功而用二項分配，後兩小題改以擊丟為成功而分別用幾何分配與負二項分配。[Example 4.17](#ex-negative-binomial-2) 把系列賽的勝負改寫成「取得第 $5$ 勝所需的場次不超過上限」，因而以負二項分配的累積機率計算，值域到無窮大並不妨礙，因為超出上限的場次都代表已經輸掉系列賽。[Example 4.18](#ex-negative-binomial-3) 則由首次達到第 $k$ 次成功的定義出發，把最後一次實驗分離出去，前面的 $n-1$ 次以二項分配計算，兩者相乘之後得到的正是負二項分配的機率函數。

[下一篇](/lecture-notes/hypergeometric-distribution/)把抽樣方式由取後放回改為取後不放回，先給出汎德蒙等式，再依序介紹超幾何實驗與超幾何分配。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
