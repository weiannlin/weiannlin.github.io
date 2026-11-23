---
title: "分配收斂的定義與極限分配的求法"
subtitle: "Convergence in Distribution and Limiting Distributions"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 5
topic: 1
order: 501
permalink: /lecture-notes/convergence-in-distribution/
date: 2026-08-15
published: false
excerpt: "當母體分配未知或難以求得抽樣分配時，大樣本極限理論提供了漸近推論的基礎。本篇定義分配收斂，說明為何僅要求 cdf 序列在極限 cdf 的連續點上逐點收斂，並以五道例題演練極限分配的求法。"
---

[上一篇](/lecture-notes/multivariate-normal-independence/)以多元常態分配的獨立性與二次形式為第四章作結，至此常用的機率模型已經逐一建立完畢。本章要處理的是母體分配不屬於這些常見模型時，統計量的抽樣分配該怎麼掌握。

前幾章介紹的常見機率模型雖然便於分析，卻未必契合真實情況；實務上最常見的限制在於無法直接假設母體服從常態分配，一旦誤設便會影響推論的正確性。在母體機率分配未知或不屬於常見模型的情況下，隨機樣本 $X_1,\ldots,X_n$ 與其構成的統計量 $\hat{\theta}(X_1,\ldots,X_n)$ 的確切抽樣分配往往難以求得。

儘管如此，隨機樣本仍攜帶關於母體的訊息 (其中最重要的是母體分配中參數的資訊，將於後續**數理統計學**的部分探討)，且所含訊息隨樣本大小增加而累積，因此當母體機率分配難以掌握時，統計推論往往仰賴大樣本進行。然而，單憑訊息量增加並不足以保證有效推論；大樣本推論之所以可行，關鍵在於統計量的抽樣分配在大樣本下常呈現特定的極限特性，例如收斂至某個常見分配，或收斂至某個固定常數，以下將逐一介紹。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

概念上，**大樣本 (large sample)** 指**樣本大小 (sample size)** 趨於無窮大 <span class="text-nowrap">($n\to\infty$)，</span>實務上則是指樣本大小「足夠大」。至於樣本要多大才算足夠大、「大」與「小」的分界應設於何處，學界與實務上並無單一標準，可參閱管中閔 (2004)，《統計學：觀念與方法》，二版，頁 213 至 220 與頁 227 至 233 的討論。

</div>

本篇先給出分配收斂的定義，再以五道例題演練由 [cdf](/lecture-notes/cumulative-distribution-functions/#def-cdf) 求極限分配的作法。五道題的路徑一致，皆先求出 $F_{\sssig X_n}$ 這一列 cdf，再讓 $n$ 趨於無窮大取逐點極限，最後找一個隨機變數，使其 cdf 在自己的連續點上與該極限相等。

## 分配收斂

<div id="def-converge-in-distribution" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 5.1 (分配收斂, converge in distribution)</div>

令 $\lbrace X_n\rbrace_{n=1}^{\infty}$ 為一定義在機率空間上之[隨機變數](/lecture-notes/random-variables-and-pmf/#def-random-variable)序列，對應的 cdf 序列為 $\lbrace F_n\rbrace_{n=1}^{\infty}$ 這列函數。若一隨機變數 $X$ 之 cdf 為 <span class="text-nowrap">$F_{\sssig X}$，</span>且對於所有 $F_{\sssig X}$ 的連續點皆有

$$
\lim_{n\to\infty}F_{n}(x)=F_{\sssig X}(x)
$$

則稱 $X_n$ **分配收斂 <span lang="en">(converge in distribution)</span>** 至 <span class="text-nowrap">$X$，</span>記為

$$
X_n\dconv X
$$

</div>

分配收斂刻畫的是機率分配之間的收斂關係，亦即序列 $X_n$ 的機率分配趨近於 $X$ 的機率分配；記號上雖寫為 $X_n$ 收斂至某一個隨機變數 <span class="text-nowrap">$X$，</span>實質上僅代表兩者的機率分配收斂，此時 $X$ 的機率分配稱為 $X_n$ 的**極限分配 <span lang="en">(limiting distribution)</span>**。此外，分配收斂亦稱為**弱收斂 <span lang="en">(converge weakly)</span>** 或**律收斂 <span lang="en">(converge in law)</span>**。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

由於隨機變數的機率分配由 cdf 唯一決定，分配收斂遂透過 cdf 序列的收斂行為加以定義。上述定義僅要求在 $F_{\sssig X}$ 的所有連續點上滿足 $\lim_{n\to\infty}F_{n}(x)=F_{\sssig X}(x)$ 這一等式，而非要求對所有實數 $x$ 皆成立；這一點源於第一章所討論的[集合的極限](/lecture-notes/event-set-operations/#definition-monotone-set-sequences)，下文例題將具體說明其原因。部分教科書亦將此條件記為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lim_{n\to\infty}F_{n}(x)=F_{\sssig X}(x),\ \forall\,x\in C(F_{\sssig X})
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\lim_{n\to\infty}F_{n}(x)&=F_{\sssig X}(x),\\[0.45em]
&\qquad\forall\,x\in C(F_{\sssig X})
\end{aligned}
$$

</div>

其中 $C(F_{\sssig X})$ 表示所有 $F_{\sssig X}$ 的連續點所構成的集合。

</div>

## 離散型序列的極限 cdf

<div id="ex-point-mass-shift" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.1</div>

<div lang="en" markdown="1">
For each positive integer <span class="text-nowrap">$n$,</span> let the discrete random variable $X_n$ have pmf

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X_n}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
1, & \text{if }x=2+\frac{1}{\,n\,}\\[0.6em]
0, & \text{o.w.}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases">
  <div class="topic-cases__lhs">$f_{\sssig X_n}(x)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$1,$</div>
    <div class="topic-cases__cond">$\text{if }x=2+\frac{1}{\,n\,}$</div>
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$\text{o.w.}$</div>
  </div>
</div>

</div>

Find the limiting distribution of <span class="text-nowrap">$X_n$.</span>
</div>

首先計算 $X_n$ 之 cdf。依 $F_{\sssig X_n}(x)=\mathbb{P}(X_n\leqslant x)$ 這個定義可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig X_n}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & x<2+\frac{1}{\,n\,}\\[0.6em]
1, & x\geqslant2+\frac{1}{\,n\,}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases">
  <div class="topic-cases__lhs">$F_{\sssig X_n}(x)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$x<2+\frac{1}{\,n\,}$</div>
    <div class="topic-cases__val">$1,$</div>
    <div class="topic-cases__cond">$x\geqslant2+\frac{1}{\,n\,}$</div>
  </div>
</div>

</div>

則若 <span class="text-nowrap">$n\to\infty$，</span>我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lim_{n\to\infty}F_{\sssig X_n}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & x\leqslant2\\[0.6em]
1, & x>2
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases">
  <div class="topic-cases__lhs">$\lim_{n\to\infty}F_{\sssig X_n}(x)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$x\leqslant2$</div>
    <div class="topic-cases__val">$1,$</div>
    <div class="topic-cases__cond">$x>2$</div>
  </div>
</div>

</div>

可定義

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & x<2\\[0.6em]
1, & x\geqslant2
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases">
  <div class="topic-cases__lhs">$F_{\sssig X}(x)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$x<2$</div>
    <div class="topic-cases__val">$1,$</div>
    <div class="topic-cases__cond">$x\geqslant2$</div>
  </div>
</div>

</div>

則我們可發現，$\lim_{n\to\infty}F_{\sssig X_n}(x)$ 與 $F_{\sssig X}(x)$ 在所有 $F_{\sssig X}$ 的連續點上皆相等，此即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lim_{n\to\infty}F_{\sssig X_n}(x)=F_{\sssig X}(x),\ \forall\,x\in C(F_{\sssig X})
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\lim_{n\to\infty}F_{\sssig X_n}(x)&=F_{\sssig X}(x),\\[0.45em]
&\qquad\forall\,x\in C(F_{\sssig X})
\end{aligned}
$$

</div>

故可知

$$
X_n\dconv X,\quad\text{其中 }X\equiv2
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

本題中，由於區間序列滿足 $\lim_{n\to\infty}\bigl(-\infty,\,2+\frac{1}{\,n\,}\bigr)=(-\infty,2]$ 這一極限關係，逐點極限 $\lim_{n\to\infty}F_{\sssig X_n}(x)$ 在 $x=2$ 處並非[右連續](/lecture-notes/cumulative-distribution-functions/#thm-cdf-properties) <span lang="en">(right-continuous)</span>，故其本身不是合法的 cdf (不論離散或連續隨機變數，其 cdf 皆須為右連續函數)。這正是分配收斂僅要求極限在 $F_{\sssig X}$ 的連續點上與 $F_{\sssig X}(x)$ 相等、而不要求在跳躍點 $x=2$ 處亦相等的原因。

</div>

<div id="ex-three-point-pmf-limit" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.2</div>

<div lang="en" markdown="1">
For <span class="text-nowrap">$n\geqslant5$,</span> let $X_n$ be a random variable with

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X_n=0)=\frac{1}{\,n\,},\quad
\mathbb{P}(X_n=1)=\frac{1}{\,2\,}+\frac{1}{\,n\,},\quad
\mathbb{P}(X_n=2)=\frac{1}{\,2\,}-\frac{2}{\,n\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{P}(X_n=0)=\frac{1}{\,n\,},\\[0.45em]
\mathbb{P}(X_n=1)=\frac{1}{\,2\,}+\frac{1}{\,n\,},\\[0.45em]
\mathbb{P}(X_n=2)=\frac{1}{\,2\,}-\frac{2}{\,n\,}
\end{gathered}
$$

</div>

and let $F_{\sssig X_n}(x)=\mathbb{P}(X_n\leqslant x)$ for <span class="text-nowrap">$x\in\mathbb{R}$.</span>

<ol class="topic-list-paren">
  <li>Find $F_{\sssig X_n}(x)$ for <span class="text-nowrap">$x\in\mathbb{R}$.</span></li>
  <li>Find a distribution function <span class="text-nowrap">$F(x)$,</span> <span class="text-nowrap">$x\in\mathbb{R}$,</span> such that $\lim_{n\to\infty}F_{\sssig X_n}(x)=F(x)$ at every continuity point of <span class="text-nowrap">$F$.</span></li>
  <li>Find a random variable $X$ with distribution function $F$ from <span class="text-nowrap">(2).</span></li>
</ol>
</div>

(1) 依題目對 $F_{\sssig X_n}(x)$ 之定義，我們有
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig X_n}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & x<0\\[0.6em]
\frac{1}{\,n\,}, & 0\leqslant x<1\\[0.6em]
\frac{1}{\,2\,}+\frac{2}{\,n\,}, & 1\leqslant x<2\\[0.6em]
1, & x\geqslant2
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases">
  <div class="topic-cases__lhs">$F_{\sssig X_n}(x)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$x<0$</div>
    <div class="topic-cases__val">$\frac{1}{\,n\,},$</div>
    <div class="topic-cases__cond">$0\leqslant x<1$</div>
    <div class="topic-cases__val">$\frac{1}{\,2\,}+\frac{2}{\,n\,},$</div>
    <div class="topic-cases__cond">$1\leqslant x<2$</div>
    <div class="topic-cases__val">$1,$</div>
    <div class="topic-cases__cond">$x\geqslant2$</div>
  </div>
</div>

</div>

(2) 當 $n\to\infty$ 時，我們有
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lim_{n\to\infty}F_{\sssig X_n}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & x<1\\[0.6em]
\frac{1}{\,2\,}, & 1\leqslant x<2\\[0.6em]
1, & x\geqslant2
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases">
  <div class="topic-cases__lhs">$\lim_{n\to\infty}F_{\sssig X_n}(x)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$x<1$</div>
    <div class="topic-cases__val">$\frac{1}{\,2\,},$</div>
    <div class="topic-cases__cond">$1\leqslant x<2$</div>
    <div class="topic-cases__val">$1,$</div>
    <div class="topic-cases__cond">$x\geqslant2$</div>
  </div>
</div>

</div>

故可令
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & x<1\\[0.6em]
\frac{1}{\,2\,}, & 1\leqslant x<2\\[0.6em]
1, & x\geqslant2
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases">
  <div class="topic-cases__lhs">$F_{\sssig X}(x)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$x<1$</div>
    <div class="topic-cases__val">$\frac{1}{\,2\,},$</div>
    <div class="topic-cases__cond">$1\leqslant x<2$</div>
    <div class="topic-cases__val">$1,$</div>
    <div class="topic-cases__cond">$x\geqslant2$</div>
  </div>
</div>

</div>

則在 $F_{\sssig X}$ 的所有連續點上皆有 $\lim_{n\to\infty}F_{\sssig X_n}(x)=F(x)$ 成立。
{: .topic-paren-cont}

(3) 令隨機變數 $X$ 具 pmf
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
p_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
\frac{1}{\,2\,}, & x=1,2\\[0.6em]
0, & \text{o.w.}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases">
  <div class="topic-cases__lhs">$p_{\sssig X}(x)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$\frac{1}{\,2\,},$</div>
    <div class="topic-cases__cond">$x=1,2$</div>
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$\text{o.w.}$</div>
  </div>
</div>

</div>

則可知 $X$ 的 cdf 就是
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & x<1\\[0.6em]
\frac{1}{\,2\,}, & 1\leqslant x<2\\[0.6em]
1, & x\geqslant2
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases">
  <div class="topic-cases__lhs">$F_{\sssig X}(x)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$x<1$</div>
    <div class="topic-cases__val">$\frac{1}{\,2\,},$</div>
    <div class="topic-cases__cond">$1\leqslant x<2$</div>
    <div class="topic-cases__val">$1,$</div>
    <div class="topic-cases__cond">$x\geqslant2$</div>
  </div>
</div>

</div>

又搭配 (1) 與 (2) 的結果，可知 <span class="text-nowrap">$X_n\dconv X$。</span>
{: .topic-paren-cont}

</div>

## 統計量的抽樣分配與其極限分配

分配收斂雖針對一般隨機變數序列 $\lbrace X_n\rbrace_{n=1}^{\infty}$ 定義，但在統計應用中，序列項通常取為由樣本構成的統計量 <span lang="en">(statistic)</span> $T_n(X_1,\ldots,X_n)$ 的形式；隨著樣本大小 $n$ 增大，該統計量的抽樣分配 <span lang="en">(sampling distribution)</span> 便可能收斂至某個極限分配，見下列例題。

<div id="ex-max-order-statistic-to-exponential" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.3</div>

<div lang="en" markdown="1">
Let $Y_n$ denote the $n$-th order statistic of a random sample of size $n$ from a continuous distribution with cdf $F(x)$ and pdf <span class="text-nowrap">$f(x)=F^{\prime}(x)$.</span> Find the limiting distribution of $Z_n=n\bigl[1-F(Y_n)\bigr]$.
</div>

依 $Y_n$ 為[順序統計量](/lecture-notes/order-statistics/#def-order-stat)之中的最大者這一點，並引用 [Theorem 3.25](/lecture-notes/order-statistics-examples/#thm-order-stat-samp-dist-cdf) 所給的最大順序統計量抽樣分配 cdf，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(Z_n\leqslant z)&=\mathbb{P}\bigl(n[1-F(Y_n)]\leqslant z\bigr)=\mathbb{P}\biggl(1-F(Y_n)\leqslant\frac{z}{\,n\,}\biggr)\\[0.45em]
&=\mathbb{P}\biggl(F(Y_n)\geqslant1-\frac{z}{\,n\,}\biggr)=\mathbb{P}\biggl(Y_n\geqslant F^{-1}\Bigl(1-\frac{z}{\,n\,}\Bigr)\biggr)\\[0.45em]
&=1-\mathbb{P}\biggl(Y_n<F^{-1}\Bigl(1-\frac{z}{\,n\,}\Bigr)\biggr)=1-F_{\sssig Y_n}\biggl(F^{-1}\Bigl(1-\frac{z}{\,n\,}\Bigr)\biggr)\\[0.45em]
&=1-\biggl[F\biggl(F^{-1}\Bigl(1-\frac{z}{\,n\,}\Bigr)\biggr)\biggr]^{n}=1-\Bigl(1-\frac{z}{\,n\,}\Bigr)^{n},\ 0<z<n
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(Z_n\leqslant z)&=\mathbb{P}\bigl(n[1-F(Y_n)]\leqslant z\bigr)\\[0.45em]
&=\mathbb{P}\biggl(1-F(Y_n)\leqslant\frac{z}{\,n\,}\biggr)\\[0.45em]
&=\mathbb{P}\biggl(F(Y_n)\geqslant1-\frac{z}{\,n\,}\biggr)\\[0.45em]
&=\mathbb{P}\biggl(Y_n\geqslant F^{-1}\Bigl(1-\frac{z}{\,n\,}\Bigr)\biggr)\\[0.45em]
&=1-\mathbb{P}\biggl(Y_n<F^{-1}\Bigl(1-\frac{z}{\,n\,}\Bigr)\biggr)\\[0.45em]
&=1-F_{\sssig Y_n}\biggl(F^{-1}\Bigl(1-\frac{z}{\,n\,}\Bigr)\biggr)\\[0.45em]
&=1-\biggl[F\biggl(F^{-1}\Bigl(1-\frac{z}{\,n\,}\Bigr)\biggr)\biggr]^{n}\\[0.45em]
&=1-\Bigl(1-\frac{z}{\,n\,}\Bigr)^{n},\ 0<z<n
\end{aligned}
$$

</div>

由此可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig Z_n}(z)=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & z<0\\[0.6em]
1-\left(1-\frac{z}{\,n\,}\right)^{n}, & 0\leqslant z<n\\[0.6em]
1, & z\geqslant n
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases topic-cases--stack">
  <div class="topic-cases__lhs">$F_{\sssig Z_n}(z)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$z<0$</div>
    <div class="topic-cases__val">$1-\left(1-\frac{z}{\,n\,}\right)^{n},$</div>
    <div class="topic-cases__cond">$0\leqslant z<n$</div>
    <div class="topic-cases__val">$1,$</div>
    <div class="topic-cases__cond">$z\geqslant n$</div>
  </div>
</div>

</div>

又由於

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lim_{n\to\infty}\left[1-\Bigl(1-\frac{z}{\,n\,}\Bigr)^{n}\right]=1-\lim_{n\to\infty}\Bigl(1-\frac{z}{\,n\,}\Bigr)^{n}=1-e^{-z}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\lim_{n\to\infty}\left[1-\Bigl(1-\frac{z}{\,n\,}\Bigr)^{n}\right]&=1-\lim_{n\to\infty}\Bigl(1-\frac{z}{\,n\,}\Bigr)^{n}\\[0.45em]
&=1-e^{-z}
\end{aligned}
$$

</div>

則可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lim_{n\to\infty}F_{\sssig Z_n}(z)=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & z<0\\[0.6em]
1-e^{-z}, & 0\leqslant z<\infty
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases">
  <div class="topic-cases__lhs">$\lim_{n\to\infty}F_{\sssig Z_n}(z)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$z<0$</div>
    <div class="topic-cases__val">$1-e^{-z},$</div>
    <div class="topic-cases__cond">$0\leqslant z<\infty$</div>
  </div>
</div>

</div>

可令 $X$ 具 cdf

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & x<0\\[0.6em]
1-e^{-x}, & x\geqslant0
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases">
  <div class="topic-cases__lhs">$F_{\sssig X}(x)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$x<0$</div>
    <div class="topic-cases__val">$1-e^{-x},$</div>
    <div class="topic-cases__cond">$x\geqslant0$</div>
  </div>
</div>

</div>

此即 $X$ 服從[指數分配](/lecture-notes/gamma-function-exponential-distribution/#def-exponential-distribution) $\mathrm{Exp}(\beta=1)$ 這個分配。又在 $F_{\sssig X}$ 之連續點上，皆有 $\lim_{n\to\infty}F_{\sssig Z_n}(x)=F_{\sssig X}(x)$ 成立，故可知

$$
Z_n\dconv X\sim\mathrm{Exp}(\beta=1)
$$

此即，$Z_n$ 之極限分配為 $\mathrm{Exp}(\beta=1)$ 這個分配。

</div>

## [均勻分配](/lecture-notes/uniform-distribution-integral-transform/#def-uniform-distribution)的極大值與極小值

<div id="ex-uniform-max-and-min-limit" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.4</div>

<div lang="en" markdown="1">
Let $X_1,X_2,\ldots,X_n$ be iid $\mathcal{U}(0,\theta)$ random variables with common pdf $f(x\mid\theta)=\frac{1}{\,\theta\,}\,\mathbb{I}_{(0<x<\theta)}$, and let $Y_1=\min\lbrace X_1,X_2,\ldots,X_n\rbrace$ and $Y_n=\max\lbrace X_1,X_2,\ldots,X_n\rbrace$.

<ol class="topic-list-paren">
  <li>Find the limiting distribution of $Y_n$ as <span class="text-nowrap">$n\to\infty$.</span></li>
  <li>Find the limiting distribution of $Z_n=nY_1$ as <span class="text-nowrap">$n\to\infty$.</span></li>
</ol>
</div>

(1) 由極大值的事件可以拆成 $n$ 個獨立事件的交集這一點，可得
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(Y_n\leqslant y)&=\mathbb{P}(X_{(n)}\leqslant y)=\mathbb{P}(X_1\leqslant y,X_2\leqslant y,\ldots,X_n\leqslant y)\\[0.45em]
&=[\mathbb{P}(X_1\leqslant y)]^{n}=\left(\int_{0}^{y}\frac{1}{\,\theta\,}\,dx\right)^{n}=\left(\left[\frac{1}{\,\theta\,}x\right]_{0}^{y}\right)^{n}\\[0.45em]
&=\left(\frac{\,y\,}{\theta}\right)^{n},\ 0<y<\theta
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(Y_n\leqslant y)&=\mathbb{P}(X_{(n)}\leqslant y)\\[0.45em]
&=\mathbb{P}(X_1\leqslant y,X_2\leqslant y,\\[0.45em]
&\qquad\ldots,X_n\leqslant y)\\[0.45em]
&=[\mathbb{P}(X_1\leqslant y)]^{n}\\[0.45em]
&=\left(\int_{0}^{y}\frac{1}{\,\theta\,}\,dx\right)^{n}\\[0.45em]
&=\left(\left[\frac{1}{\,\theta\,}x\right]_{0}^{y}\right)^{n}\\[0.45em]
&=\left(\frac{\,y\,}{\theta}\right)^{n},\ 0<y<\theta
\end{aligned}
$$

</div>

可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig Y_n}(y)=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & y\leqslant0\\[0.6em]
\left(\frac{\,y\,}{\theta}\right)^{n}, & 0<y<\theta\\[0.6em]
1, & y\geqslant\theta
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases">
  <div class="topic-cases__lhs">$F_{\sssig Y_n}(y)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$y\leqslant0$</div>
    <div class="topic-cases__val">$\left(\frac{\,y\,}{\theta}\right)^{n},$</div>
    <div class="topic-cases__cond">$0<y<\theta$</div>
    <div class="topic-cases__val">$1,$</div>
    <div class="topic-cases__cond">$y\geqslant\theta$</div>
  </div>
</div>

</div>

由此可得
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lim_{n\to\infty}F_{\sssig Y_n}(y)=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & y<\theta\\[0.6em]
1, & y\geqslant\theta
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases">
  <div class="topic-cases__lhs">$\lim_{n\to\infty}F_{\sssig Y_n}(y)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$y<\theta$</div>
    <div class="topic-cases__val">$1,$</div>
    <div class="topic-cases__cond">$y\geqslant\theta$</div>
  </div>
</div>

</div>

可令 $Y\equiv\theta$ 表一退化隨機變數 <span lang="en">(degenerate random variable)</span>，具 cdf
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig Y}(y)=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & y<\theta\\[0.6em]
1, & y\geqslant\theta
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases">
  <div class="topic-cases__lhs">$F_{\sssig Y}(y)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$y<\theta$</div>
    <div class="topic-cases__val">$1,$</div>
    <div class="topic-cases__cond">$y\geqslant\theta$</div>
  </div>
</div>

</div>

在 $F_{\sssig Y}$ 之所有連續點上皆有 $\lim_{n\to\infty}F_{\sssig Y_n}(y)=F_{\sssig Y}(y)$ 成立，故知
{: .topic-paren-cont}

$$
Y_n\dconv Y\equiv\theta
$$

(2) 極小值事件由尾機率下手，可得
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(Z_n\leqslant z)&=\mathbb{P}(nY_1\leqslant z)=\mathbb{P}\left(Y_1\leqslant\frac{\,z\,}{n}\right)=1-\mathbb{P}\left(Y_1>\frac{\,z\,}{n}\right)\\[0.45em]
&=1-\mathbb{P}\left(X_1>\frac{\,z\,}{n},X_2>\frac{\,z\,}{n},\ldots,X_n>\frac{\,z\,}{n}\right)\\[0.45em]
&=1-\left[\mathbb{P}\left(X_1>\frac{\,z\,}{n}\right)\right]^{n}=1-\left(\int_{z/n}^{\theta}\frac{1}{\,\theta\,}\,dx\right)^{n}\\[0.45em]
&=1-\left(\left[\frac{1}{\,\theta\,}x\right]_{z/n}^{\theta}\right)^{n}=1-\left(1-\frac{\,z\,}{\,n\theta\,}\right)^{n},\ 0<z<n\theta
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(Z_n\leqslant z)&=\mathbb{P}(nY_1\leqslant z)\\[0.45em]
&=\mathbb{P}\left(Y_1\leqslant\frac{\,z\,}{n}\right)\\[0.45em]
&=1-\mathbb{P}\left(Y_1>\frac{\,z\,}{n}\right)\\[0.45em]
&=1-\mathbb{P}\left(X_1>\frac{\,z\,}{n},X_2>\frac{\,z\,}{n},\right.\\[0.45em]
&\qquad\left.\ldots,X_n>\frac{\,z\,}{n}\right)\\[0.45em]
&=1-\left[\mathbb{P}\left(X_1>\frac{\,z\,}{n}\right)\right]^{n}\\[0.45em]
&=1-\left(\int_{z/n}^{\theta}\frac{1}{\,\theta\,}\,dx\right)^{n}\\[0.45em]
&=1-\left(\left[\frac{1}{\,\theta\,}x\right]_{z/n}^{\theta}\right)^{n}\\[0.45em]
&=1-\left(1-\frac{\,z\,}{\,n\theta\,}\right)^{n},\ 0<z<n\theta
\end{aligned}
$$

</div>

由此可得
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig Z_n}(z)=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & z\leqslant0\\[0.6em]
1-\left(1-\frac{\,z\,}{\,n\theta\,}\right)^{n}, & 0<z<n\theta\\[0.6em]
1, & z\geqslant n\theta
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases topic-cases--stack">
  <div class="topic-cases__lhs">$F_{\sssig Z_n}(z)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$z\leqslant0$</div>
    <div class="topic-cases__val">$1-\left(1-\frac{\,z\,}{\,n\theta\,}\right)^{n},$</div>
    <div class="topic-cases__cond">$0<z<n\theta$</div>
    <div class="topic-cases__val">$1,$</div>
    <div class="topic-cases__cond">$z\geqslant n\theta$</div>
  </div>
</div>

</div>

又
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\lim_{n\to\infty}\left[1-\left(1-\frac{\,z\,}{\,n\theta\,}\right)^{n}\right]&=\lim_{n\to\infty}\left[1-\left(1+\frac{\,\Bigl(-\frac{z}{\,\theta\,}\Bigr)\,}{n}\right)^{n}\right]\\[0.45em]
&=1-e^{-\frac{z}{\,\theta\,}}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\lim_{n\to\infty}\left[1-\left(1-\frac{\,z\,}{\,n\theta\,}\right)^{n}\right]\\[0.45em]
&=\lim_{n\to\infty}\left[1-\left(1+\frac{\,\Bigl(-\frac{z}{\,\theta\,}\Bigr)\,}{n}\right)^{n}\right]\\[0.45em]
&=1-e^{-\frac{z}{\,\theta\,}}
\end{aligned}
$$

</div>

由此可得
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lim_{n\to\infty}F_{\sssig Z_n}(z)=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & z\leqslant0\\[0.6em]
1-e^{-\frac{z}{\,\theta\,}}, & z>0
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases">
  <div class="topic-cases__lhs">$\lim_{n\to\infty}F_{\sssig Z_n}(z)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$z\leqslant0$</div>
    <div class="topic-cases__val">$1-e^{-\frac{z}{\,\theta\,}},$</div>
    <div class="topic-cases__cond">$z>0$</div>
  </div>
</div>

</div>

可令 $Z\sim\mathrm{Exp}(\beta=\theta)$ 服從指數分配，具 cdf
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig Z}(z)=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & z<0\\[0.6em]
1-e^{-\frac{z}{\,\theta\,}}, & z\geqslant0
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases">
  <div class="topic-cases__lhs">$F_{\sssig Z}(z)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$z<0$</div>
    <div class="topic-cases__val">$1-e^{-\frac{z}{\,\theta\,}},$</div>
    <div class="topic-cases__cond">$z\geqslant0$</div>
  </div>
</div>

</div>

在 $F_{\sssig Z}$ 之連續點上，皆有 $\lim_{n\to\infty}F_{\sssig Z_n}(z)=F_{\sssig Z}(z)$ 成立，故知
{: .topic-paren-cont}

$$
Z_n=nY_1\dconv Z\sim\mathrm{Exp}(\beta=\theta)
$$

</div>

## 指數母體極大值的平移與其極限 cdf

<div id="ex-exponential-max-shifted-by-log-n" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.5</div>

<div lang="en" markdown="1">
Let $X_1,X_2,\ldots,X_n$ be a random sample from an exponential distribution with cdf $F_{\sssig X}(x)=1-e^{-x}$ for $x\geqslant0$ and $0$ otherwise, and let $X_{(n)}=\max\lbrace X_1,X_2,\ldots,X_n\rbrace$ and <span class="text-nowrap">$Y_n=X_{(n)}-\ln n$.</span>

<ol class="topic-list-paren">
  <li>Find the distribution function $F_{\sssig X_{(n)}}(x)$.</li>
  <li>Find the distribution function <span class="text-nowrap">$F_{\sssig Y_n}(y)$.</span></li>
  <li>Using <span class="text-nowrap">(2),</span> find $\lim_{n\to\infty}F_{\sssig Y_n}(y)$.<br>
  (Hint: $\lim_{n\to\infty}\bigl(1-\frac{a}{n}\bigr)^{n}=e^{-a}$ for any real number <span class="text-nowrap">$a$.)</span></li>
</ol>
</div>

(1) 極大值不超過 $x$ 等於 $n$ 個觀測值都不超過 <span class="text-nowrap">$x$，</span>故
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X_{(n)}\leqslant x)&=\mathbb{P}(\max\lbrace X_1,X_2,\ldots,X_n\rbrace\leqslant x)\\[0.45em]
&=\mathbb{P}(X_1\leqslant x,X_2\leqslant x,\ldots,X_n\leqslant x)=\prod_{i=1}^{n}\mathbb{P}(X_i\leqslant x)\\[0.45em]
&=[\mathbb{P}(X_1\leqslant x)]^{n}=[F_{\sssig X}(x)]^{n}=(1-e^{-x})^{n},\ x\geqslant0
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X_{(n)}\leqslant x)&=\mathbb{P}(\max\lbrace X_1,X_2,\ldots,X_n\rbrace\leqslant x)\\[0.45em]
&=\mathbb{P}(X_1\leqslant x,X_2\leqslant x,\\[0.45em]
&\qquad\ldots,X_n\leqslant x)\\[0.45em]
&=\prod_{i=1}^{n}\mathbb{P}(X_i\leqslant x)\\[0.45em]
&=[\mathbb{P}(X_1\leqslant x)]^{n}\\[0.45em]
&=[F_{\sssig X}(x)]^{n}\\[0.45em]
&=(1-e^{-x})^{n},\ x\geqslant0
\end{aligned}
$$

</div>

由此可得
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig X_{(n)}}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & x<0\\[0.6em]
(1-e^{-x})^{n}, & x\geqslant0
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases">
  <div class="topic-cases__lhs">$F_{\sssig X_{(n)}}(x)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$x<0$</div>
    <div class="topic-cases__val">$(1-e^{-x})^{n},$</div>
    <div class="topic-cases__cond">$x\geqslant0$</div>
  </div>
</div>

</div>

(2) 把 $Y_n\leqslant y$ 這個事件改寫為 $X_{(n)}\leqslant y+\ln n$ 之後，即可引用 (1) 的結果，可得
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(Y_n\leqslant y)&=\mathbb{P}(X_{(n)}-\ln n\leqslant y)=\mathbb{P}(X_{(n)}\leqslant y+\ln n)\\[0.45em]
&=[1-e^{-(y+\ln n)}]^{n}=(1-e^{-y}e^{-\ln n})^{n}=(1-e^{-y}n^{-1})^{n}\\[0.45em]
&=\left(1-\frac{e^{-y}}{n}\right)^{n},\ y\geqslant-\ln n
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(Y_n\leqslant y)&=\mathbb{P}(X_{(n)}-\ln n\leqslant y)\\[0.45em]
&=\mathbb{P}(X_{(n)}\leqslant y+\ln n)\\[0.45em]
&=[1-e^{-(y+\ln n)}]^{n}\\[0.45em]
&=(1-e^{-y}e^{-\ln n})^{n}\\[0.45em]
&=(1-e^{-y}n^{-1})^{n}\\[0.45em]
&=\left(1-\frac{e^{-y}}{n}\right)^{n},\ y\geqslant-\ln n
\end{aligned}
$$

</div>

由此可得
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig Y_n}(y)=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & y<-\ln n\\[0.6em]
\left(1-\frac{e^{-y}}{n}\right)^{n}, & y\geqslant-\ln n
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases topic-cases--stack">
  <div class="topic-cases__lhs">$F_{\sssig Y_n}(y)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$y<-\ln n$</div>
    <div class="topic-cases__val">$\left(1-\frac{e^{-y}}{n}\right)^{n},$</div>
    <div class="topic-cases__cond">$y\geqslant-\ln n$</div>
  </div>
</div>

</div>

(3) 引用題目所給的提示，可得
{: .topic-paren-item}

<div class="topic-math-follow-before" markdown="1">

$$
\lim_{n\to\infty}\left(1-\frac{e^{-y}}{n}\right)^{n}=e^{-e^{-y}}
$$

</div>
<div class="topic-math-follow" markdown="1">
<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\Longrightarrow\ \lim_{n\to\infty}F_{\sssig Y_n}(y)=e^{-e^{-y}},\ y\in\mathbb{R}\qquad(\,\because\ \lim_{n\to\infty}(-\ln n)=-\infty\,)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ \lim_{n\to\infty}F_{\sssig Y_n}(y)&=e^{-e^{-y}},\ y\in\mathbb{R}\\[0.45em]
&\qquad(\,\because\ \lim_{n\to\infty}(-\ln n)=-\infty\,)
\end{aligned}
$$

</div>
</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

經適當尺度調整或標準化的統計量，其極限分配有時會落在前幾章介紹過的常見分配族中，但亦常出現不屬於上述常見模型的極限分配，本題即為一例。即便如此，只要令隨機變數 $Y$ 具有 cdf

$$
F_{\sssig Y}(y)=e^{-e^{-y}},\ y\in\mathbb{R}
$$

則在 $F_{\sssig Y}$ 的所有連續點上皆滿足 $\lim_{n\to\infty}F_{\sssig Y_n}(y)=F_{\sssig Y}(y)$ 這一條件；依定義仍有 $Y_n\dconv Y\sim F_{\sssig Y}(y)$ 成立，僅是此處極限變數 $Y$ 的機率分配並不屬於前幾章所介紹的常見分配。

</div>

## 本篇小結

[Definition 5.1](#def-converge-in-distribution) 把收斂這件事放在 cdf 上，$X_n\dconv X$ 的意思是 $F_{\sssig X_n}$ 這一列函數逐點趨近於 <span class="text-nowrap">$F_{\sssig X}$，</span>而且只在 $F_{\sssig X}$ 自己的連續點上要求相等。這個放寬不是為了方便，[Example 5.1](#ex-point-mass-shift) 就是理由。機率全部集中在 $2+\frac{1}{\,n\,}$ 這個單點上時，逐點極限在 $x=2$ 處取值為 <span class="text-nowrap">$0$，</span>右極限卻是 <span class="text-nowrap">$1$，</span>它本身並不右連續，因而不是任何隨機變數的 cdf。若要求處處相等，這個再自然不過的序列就不會收斂到 <span class="text-nowrap">$X\equiv2$。</span>[Example 5.2](#ex-three-point-pmf-limit) 是同一件事的離散型版本，三個取值點的機率隨 $n$ 變動，$x=0$ 上的機率 $\frac{1}{\,n\,}$ 在極限時消失，剩下的兩個點各分得 <span class="text-nowrap">$\frac{1}{\,2\,}$。</span>

其餘三題的序列都是統計量。[Example 5.3](#ex-max-order-statistic-to-exponential) 的作法是把 $\mathbb{P}(Z_n\leqslant z)$ 一路化為 $Y_n$ 的事件，再引用最大順序統計量的抽樣分配 cdf 為 $[F(y)]^{n}$ 這個結果，於是 $F_{\sssig Z_n}(z)=1-\bigl(1-\frac{z}{\,n\,}\bigr)^{n}$ 這個式子與母體分配 $F$ 完全無關，取極限即得 $\mathrm{Exp}(\beta=1)$ 這個分配。[Example 5.4](#ex-uniform-max-and-min-limit) 的兩個小題方向相反。極大值 $Y_n$ 的 cdf 是 $\bigl(\frac{\,y\,}{\theta}\bigr)^{n}$ 這個式子，$n$ 增大時它在 $[0,\theta)$ 上被壓成 <span class="text-nowrap">$0$，</span>極限因而是退化在 $\theta$ 上的隨機變數；極小值本身也會退化到 <span class="text-nowrap">$0$，</span>但乘上 $n$ 之後尺度剛好抵銷，$Z_n=nY_1$ 收斂至 $\mathrm{Exp}(\beta=\theta)$ 這個分配。兩題合起來說明，同一個統計量乘上一個隨 $n$ 變動的倍數，得到的極限分配可以完全不同。

[Example 5.5](#ex-exponential-max-shifted-by-log-n) 走的則是平移而不是伸縮。指數母體的極大值 $X_{(n)}$ 本身會趨於無窮大，減去 $\ln n$ 之後才穩得住，極限 cdf 為 $e^{-e^{-y}}$ 這個式子，定義域是整條實數線。這個分配不是前面幾章介紹過的任何一個常見分配，卻仍然完全合乎 [Definition 5.1](#def-converge-in-distribution) 的要求，這也正是最後一則 Note 所指出的，極限分配不保證漂亮，能寫出一個合法的 cdf 並在其連續點上取到極限，分配收斂就成立了。

五道題都是先求 <span class="text-nowrap">$F_{\sssig X_n}$、</span>取逐點極限，再找一個 cdf 與這個極限在連續點上相等。這套作法的限制在於統計量一旦複雜起來，$F_{\sssig X_n}$ 往往寫不出來。[下一篇](/lecture-notes/levy-continuity-theorem/)改由動差母函數下手，以列維連續性定理把「動差母函數收斂」轉譯為「分配收斂」，同樣的五道例題型態便不必再碰 cdf。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- 管中閔，2004，《統計學：觀念與方法》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
