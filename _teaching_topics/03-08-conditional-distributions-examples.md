---
title: "條件分配的例題"
subtitle: "Examples of Conditional Distributions"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 8
order: 308
permalink: /lecture-notes/conditional-distributions-examples/
date: 2026-08-12
published: false
excerpt: "本篇以五道例題，把條件機率質量函數與條件機率密度函數的定義實際用過一遍。前兩道例題延續先前求過邊際分配的那兩題，改求 $X$ 在給定 $Y=y$ 之下的條件分配，並由此看出兩題在獨立與否上的差別。接著我們把條件由 $Y=y$ 這個薄薄的切片放寬為一個範圍，第三道例題的第二小題更出現條件只牽涉同一個變數的情形，這種分配稱作截尾分配，其形式是把原本的機率函數除以該段的機率總和，並把值域重新限制在該段之中。最後兩道例題即為截尾分配的計算，其中指數分配的那一題會呈現無記憶性。"
---

[上一篇](/lecture-notes/conditional-distributions/)把二元[隨機向量](/lecture-notes/random-vectors-joint-pmf/#def-random-vector)中的一個變數固定成常數，給出[條件機率質量函數](/lecture-notes/conditional-distributions/#def-conditional-pmf)與[條件機率密度函數](/lecture-notes/conditional-distributions/#def-conditional-pdf)的定義，並說明條件分配仍然是一種機率分配。本篇便以五道例題，把這兩個定義實際用過一遍。

前兩道例題延續先前求過[邊際機率密度函數](/lecture-notes/marginal-probability-density-functions/#def-marginal-pdf)的那兩題，改求 $X$ 在給定 $Y=y$ 之下的條件分配。兩題所得的結果在形式上有一個明顯的差別，這個差別與兩個變數獨立與否有關。

接下來我們把條件由 $Y=y$ 這個薄薄的切片放寬為一個範圍，第三道例題的兩個小題便分別示範條件牽涉另一個變數，以及條件只牽涉同一個變數這兩種情形。後者所得到的分配稱作截尾分配，本篇隨後給出它在離散型與連續型的形式，並以兩張圖說明截尾之後為何要除以該段的機率總和；最後兩道例題即為截尾分配的計算。

<div id="ex-joint-pdf-region-basic-conditional" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.2 <span lang="en">(Continued)</span></div>

<div lang="en" markdown="1">
Suppose that a continuous random vector $(X,Y)$ has joint probability density function

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig XY}(x,y)=
\left\lbrace
\begin{array}{c@{\quad}l}
12\,xy(1-x), & 0<x<1,\ 0<y<1\\[0.5em]
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
    <div class="topic-cases__val">$12\,xy(1-x),$</div>
    <div class="topic-cases__cond">$0<x<1$, $0<y<1$</div>
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$\text{o.w.}$</div>
  </div>
</div>

</div>

<ol class="topic-list-paren topic-list-paren--start-4">
  <li>Determine the conditional probability that $0<X<0.5$ given that <span class="text-nowrap">$Y=0.5$.</span></li>
</ol>
</div>

(4) 先算出 $X$ 在給定 $Y=y$ 的條件下的條件分配為:
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f_{\sssig X\mid Y}(x\mid y)&=\frac{\,f_{\sssig XY}(x,y)\,}{f_{\sssig Y}(y)}=\frac{\,12(x-x^{2})y\,}{2y}\\[0.45em]
&=6(x-x^{2}),\ 0<x<1,\ 0<y<1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig X\mid Y}(x\mid y)&=\frac{\,f_{\sssig XY}(x,y)\,}{f_{\sssig Y}(y)}\\[0.45em]
&=\frac{\,12(x-x^{2})y\,}{2y}=6(x-x^{2}),\\[0.25em]
&\qquad 0<x<1,\ 0<y<1
\end{aligned}
$$

</div>

由此可得
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X\mid Y}(x\mid y)=
\left\lbrace
\begin{array}{c@{\quad}l}
6(x-x^{2}), & 0<x<1,\ 0<y<1\\[0.5em]
0, & \text{o.w.}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases">
  <div class="topic-cases__lhs">$f_{\sssig X\mid Y}(x\mid y)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$6(x-x^{2}),$</div>
    <div class="topic-cases__cond">$0<x<1$, $0<y<1$</div>
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$\text{o.w.}$</div>
  </div>
</div>

</div>

若給定 <span class="text-nowrap">$Y=0.5$，</span>則 $X$ 在給定 $Y=0.5$ 的條件分配為
{: .topic-paren-cont}

$$
f_{\sssig X\mid Y}(x\mid 0.5)=
\left\lbrace
\begin{array}{c@{\quad}l}
6(x-x^{2}), & 0<x<1\\[0.5em]
0, & \text{o.w.}
\end{array}
\right.
$$

故所求為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(0<X<0.5\mid Y=0.5)&=\int_{0}^{0.5}f_{\sssig X\mid Y}(x\mid 0.5)\,dx\\[0.45em]
&=\int_{0}^{0.5}6(x-x^{2})\,dx=0.5
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(0<X<0.5\mid Y=0.5)&=\int_{0}^{0.5}f_{\sssig X\mid Y}(x\mid 0.5)\,dx\\[0.45em]
&=\int_{0}^{0.5}6(x-x^{2})\,dx=0.5
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

事實上，在[稍早的段落](/lecture-notes/region-probabilities-joint-density/)裡，我們曾經提過，這題的分配中，$X$ 與 $Y$ 是獨立的，這件事情同樣可以從其條件分配看出一些端倪，稍後我們會有[一個完整的小節](/lecture-notes/independent-random-variables/)，探討這種情況。

</div>

<div id="ex-joint-pdf-triangle-region-conditional" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.3 <span lang="en">(Continued)</span></div>

<div lang="en" markdown="1">
Suppose that a continuous random vector $(X,Y)$ has joint probability density function

$$
f_{\sssig XY}(x,y)=
\left\lbrace
\begin{array}{c@{\quad}l}
2(x+y), & 0\leqslant x\leqslant y\leqslant 1\\[0.5em]
0, & \text{o.w.}
\end{array}
\right.
$$

<ol class="topic-list-paren topic-list-paren--start-4">
  <li>Find the conditional pdf of $X$ given that <span class="text-nowrap">$Y=0.6$.</span></li>
</ol>
</div>

(4) 依照定義，$X$ 在給定 $Y=y$ 的條件下的條件分配為:
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X\mid Y}(x\mid y)=\frac{\,f_{\sssig XY}(x,y)\,}{f_{\sssig Y}(y)}=\frac{2(x+y)}{3y^{2}},\ 0\leqslant x\leqslant y\leqslant 1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig X\mid Y}(x\mid y)&=\frac{\,f_{\sssig XY}(x,y)\,}{f_{\sssig Y}(y)}=\frac{2(x+y)}{3y^{2}},\\[0.45em]
&\quad\ 0\leqslant x\leqslant y\leqslant 1
\end{aligned}
$$

</div>

由此可得
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X\mid Y}(x\mid y)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{\,2(x+y)\,}{3y^{2}}, & 0\leqslant x\leqslant y\leqslant 1\\[0.8em]
0, & \text{o.w.}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases">
  <div class="topic-cases__lhs">$f_{\sssig X\mid Y}(x\mid y)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$\dfrac{\,2(x+y)\,}{3y^{2}},$</div>
    <div class="topic-cases__cond">$0\leqslant x\leqslant y\leqslant 1$</div>
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$\text{o.w.}$</div>
  </div>
</div>

</div>

若給定 <span class="text-nowrap">$Y=0.6$，</span>則 $X$ 在給定 $Y=0.6$ 的條件分配為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X\mid Y}(x\mid 0.6)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{\,2(x+0.6)\,}{3\times(0.6)^{2}}, & 0\leqslant x\leqslant 0.6\\[0.8em]
0, & \text{o.w.}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases topic-cases--stack">
  <div class="topic-cases__lhs">$f_{\sssig X\mid Y}(x\mid 0.6)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$\dfrac{\,2(x+0.6)\,}{3\times(0.6)^{2}},$</div>
    <div class="topic-cases__cond">$0\leqslant x\leqslant 0.6$</div>
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$\text{o.w.}$</div>
  </div>
</div>

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

與前面一題相對，這題的分配中，$X$ 與 $Y$ 是不獨立的。

此外，$X$ 給定 $Y=y$ 條件分配中，雖然還看得見 $y$ 的身影，但讀者應該特別注意，此處的 $y$ 僅是一個常數，在我們確定 $y$ 是何值並代入之後就會消失，只有 $x$ 才是這個 conditional pdf 的主要變數。

</div>

在理解條件的意涵之後，我們便可以進一步放寬 conditional pdf <span lang="en">(conditional pmf)</span> 所指涉的「條件」，我們未必要在 $Y=y$ 這個薄薄的切片所形成的空間上來探討 $X$ 的機率分配。

事實上，有的時候我們可以看到像是 $\mathbb{P}(a<X<b\mid c<Y<d)$ 這樣的條件機率，這樣的條件機率中，$c<Y<d$ 就是「條件空間」，我們當然可以很直觀地，將這個條件機率轉為

$$
\frac{\,\mathbb{P}(a<X<b,\ c<Y<d)\,}{\mathbb{P}(c<Y<d)}
$$

而這個條件機率意義即是代表在 $c<Y<d$ 的空間中，探討 $a<X<b$ 的事件所佔的比例。

<div id="ex-discrete-conditional-table" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.9</div>

<div lang="en" markdown="1">
Suppose that the joint pmf and the marginal pmfs of a two-dimensional discrete random vector $(X_1,X_2)$ are given in the following table.

| $X_1\backslash X_2$ | $0$ | $1$ | $2$ | $p_{\sssig X_1}(x_1)$ |
| :---: | :---: | :---: | :---: | :---: |
| $0$ | $0.2$ | $0.1$ | $0.1$ | $0.4$ |
| $1$ | $0.1$ | $0.2$ | $0.1$ | $0.4$ |
| $2$ | $0.1$ | $0.1$ | $0$ | $0.2$ |
| $p_{\sssig X_2}(x_2)$ | $0.4$ | $0.4$ | $0.2$ | $1$ |
{: .topic-table--joint-pmf}

<ol class="topic-list-paren">
  <li>Find <span class="text-nowrap">$\mathbb{P}(X_1>1\mid X_2\leqslant 1)$.</span></li>
  <li>Find <span class="text-nowrap">$\mathbb{P}(X_1<1.5\mid X_1\geqslant 1)$.</span></li>
</ol>
</div>

(1) 由 [conditional pmf 的定義](/lecture-notes/conditional-distributions/#def-conditional-pmf)可知:
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X_1>1\mid X_2\leqslant 1)&=\frac{\mathbb{P}(X_1>1,\ X_2\leqslant 1)}{\mathbb{P}(X_2\leqslant 1)}\\[0.45em]
&=\frac{\,p_{\sssig X_1X_2}(2,0)+p_{\sssig X_1X_2}(2,1)\,}{p_{\sssig X_2}(0)+p_{\sssig X_2}(1)}=\frac{0.1+0.1}{\,0.4+0.4\,}=0.25
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X_1>1\mid X_2\leqslant 1)&=\frac{\mathbb{P}(X_1>1,\ X_2\leqslant 1)}{\mathbb{P}(X_2\leqslant 1)}\\[0.45em]
&=\frac{\,p_{\sssig X_1X_2}(2,0)+p_{\sssig X_1X_2}(2,1)\,}{p_{\sssig X_2}(0)+p_{\sssig X_2}(1)}\\[0.45em]
&=\frac{0.1+0.1}{\,0.4+0.4\,}=0.25
\end{aligned}
$$

</div>

(2) 由 [conditional pmf 的定義](/lecture-notes/conditional-distributions/#def-conditional-pmf)可知:
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X_1<1.5\mid X_1\geqslant 1)&=\frac{\,\mathbb{P}(X_1\leqslant 1,\ X_1\geqslant 1)\,}{\mathbb{P}(X_1\geqslant 1)}\\[0.45em]
&=\frac{p_{\sssig X_1}(1)}{p_{\sssig X_1}(1)+p_{\sssig X_1}(2)}=\frac{0.4}{\,0.4+0.2\,}=\frac{2}{\,3\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X_1<1.5\mid X_1\geqslant 1)&=\frac{\,\mathbb{P}(X_1\leqslant 1,\ X_1\geqslant 1)\,}{\mathbb{P}(X_1\geqslant 1)}\\[0.45em]
&=\frac{p_{\sssig X_1}(1)}{p_{\sssig X_1}(1)+p_{\sssig X_1}(2)}\\[0.45em]
&=\frac{0.4}{\,0.4+0.2\,}=\frac{2}{\,3\,}
\end{aligned}
$$

</div>

</div>

上述[第 (2) 小題](#ex-discrete-conditional-table)比較特別，該條件與 $X_2$ 沒有關係，是 $X_1$ 的自我限制條件，所求的機率也是 $X_1$ 的範圍。這種分配稱作**截尾分配 <span lang="en">(truncated distribution)</span>**，形式如下:

**[ 離散型 ]**

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
p_{\sssig X}(x\mid a<X<b)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{p_{\sssig X}(x)}{\,\mathbb{P}(a<X<b)\,}, & a<x<b\\[0.8em]
0, & \text{o.w.}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases topic-cases--stack">
  <div class="topic-cases__lhs">$p_{\sssig X}(x\mid a<X<b)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$\dfrac{p_{\sssig X}(x)}{\,\mathbb{P}(a<X<b)\,},$</div>
    <div class="topic-cases__cond">$a<x<b$</div>
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$\text{o.w.}$</div>
  </div>
</div>

</div>

**[ 連續型 ]**

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X}(x\mid a<X<b)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{f_{\sssig X}(x)}{\,\mathbb{P}(a<X<b)\,}, & a<x<b\\[0.8em]
0, & \text{o.w.}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases topic-cases--stack">
  <div class="topic-cases__lhs">$f_{\sssig X}(x\mid a<X<b)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$\dfrac{f_{\sssig X}(x)}{\,\mathbb{P}(a<X<b)\,},$</div>
    <div class="topic-cases__cond">$a<x<b$</div>
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$\text{o.w.}$</div>
  </div>
</div>

</div>

截尾分配發生的範圍如下所示:

<figure id="fig-truncated-range" class="topic-figure topic-figure--wide">
  <img src="/images/lecture-notes/truncated-range.svg" alt="一條鐘形的機率密度曲線，左右兩端都貼近橫軸，峰頂上方標 f_X(x)。曲線之下有兩條虛線界線各自由曲線垂直落到橫軸，落點在橫軸上各畫一小段刻度，軸下由左至右標為 a 與 b，兩條界線並不對稱於峰頂。兩條界線之間、曲線之下到橫軸之間的整塊區域以淡紅色填滿，區塊之內標 P(a 小於 X 小於 b)；界線之外的曲線之下不填色。橫軸右端有箭頭並標 x，圖中沒有鉛直軸。">
  <figcaption><span class="topic-figure__label">Fig. 3.13.</span> 截尾之後所關心的只剩下 $a$ 與 $b$ 之間這一段，填色的區塊即這一段的機率 <span class="text-nowrap">$\mathbb{P}(a<X<b)$。</span>這一塊的面積小於 <span class="text-nowrap">$1$，</span>故單取這一段還不是一個合法的 pdf。</figcaption>
</figure>

與條件分配相同，我們應將這一段未完成品，調整為一個合法的 pdf，也就是除以該段的機率總和 <span class="text-nowrap">$\mathbb{P}(a<X<b)$，</span>並且將 $X$ 的範圍重新限制在 $(a,b)$ 區間中，即

<figure id="fig-truncated-normalized" class="topic-figure topic-figure--wide">
  <img src="/images/lecture-notes/truncated-normalized.svg" alt="同一條鐘形密度曲線只留下 a 與 b 之間的一段，這一段之外不畫曲線。曲線的兩個端點各有一條虛線界線垂直落到橫軸，落點在橫軸上各畫一小段刻度，軸下由左至右標為 a 與 b。這一段曲線比前一張圖的同一段來得高，其下方到橫軸之間的整塊區域以淡紅色填滿，區塊的左右兩側就是那兩條垂直的界線。曲線峰頂上方標 f_X(x | a 小於 X 小於 b)。橫軸右端有箭頭並標 x，圖中沒有鉛直軸。">
  <figcaption><span class="topic-figure__label">Fig. 3.14.</span> 把 $a$ 與 $b$ 之間的那一段除以 <span class="text-nowrap">$\mathbb{P}(a<X<b)$，</span>曲線整體被拉高，$X$ 的範圍也重新限制在 $(a,b)$ 之內，填色區塊的面積因此回到 <span class="text-nowrap">$1$，</span>成為合法的 pdf <span class="text-nowrap">$f_{\sssig X}(x\mid a<X<b)$。</span></figcaption>
</figure>

<div id="ex-uniform-conditional-interval" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.10</div>

<div lang="en" markdown="1">
Suppose that $X$ follows the uniform distribution over the interval <span class="text-nowrap">$(0,1)$.</span> Determine <span class="text-nowrap">$\mathbb{P}\bigl(X<\frac{1}{8}\bigm\vert X<\frac{1}{4}\bigr)$.</span>
</div>

由題目敘述可知

$$
f_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
1, & 0<x<1\\[0.5em]
0, & \text{o.w.}
\end{array}
\right.
$$

且由截尾分配的定義可知

$$
f_{\sssig X}\Bigl(x\Bigm\vert x<\frac{1}{4}\Bigr)=\frac{f_{\sssig X}(x)}{\,\mathbb{P}\bigl(X<\frac{1}{4}\bigr)\,},\ x<\frac{1}{4}
$$

又可求得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}\Bigl(X<\frac{1}{4}\Bigr)=\int_{0}^{\frac{1}{4}}1\,dx=\bigl[x\bigr]_{0}^{\frac{1}{4}}=\frac{1}{4}\qquad\therefore\, f_{\sssig X}\Bigl(x\Bigm\vert x<\frac{1}{4}\Bigr)=4\times 1=4,\ x<\frac{1}{4}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}\Bigl(X<\frac{1}{4}\Bigr)&=\int_{0}^{\frac{1}{4}}1\,dx=\bigl[x\bigr]_{0}^{\frac{1}{4}}=\frac{1}{4}\\[0.45em]
&\qquad\therefore\, f_{\sssig X}\Bigl(x\Bigm\vert x<\frac{1}{4}\Bigr)=4\times 1=4,\\[0.45em]
&\qquad\qquad x<\frac{1}{4}
\end{aligned}
$$

</div>

故所求為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}\Bigl(X<\frac{1}{8}\Bigm\vert X<\frac{1}{4}\Bigr)&=\int_{0}^{\frac{1}{8}}f_{\sssig X}\Bigl(x\Bigm\vert x<\frac{1}{4}\Bigr)\,dx\\[0.45em]
&=\int_{0}^{\frac{1}{8}}4\,dx=\bigl[4x\bigr]_{0}^{\frac{1}{8}}=\frac{1}{\,2\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}\Bigl(X<\frac{1}{8}\Bigm\vert X<\frac{1}{4}\Bigr)&=\int_{0}^{\frac{1}{8}}f_{\sssig X}\Bigl(x\Bigm\vert x<\frac{1}{4}\Bigr)\,dx\\[0.45em]
&=\int_{0}^{\frac{1}{8}}4\,dx=\bigl[4x\bigr]_{0}^{\frac{1}{8}}=\frac{1}{\,2\,}
\end{aligned}
$$

</div>

</div>

<div id="ex-conditional-pdf-from-pdf" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.11</div>

<div lang="en" markdown="1">
Suppose that a random variable $X$ has probability density function

$$
f_{\sssig X}(x)=\frac{1}{20}e^{-\frac{x}{20}},\ 0<x<\infty
$$

Find <span class="text-nowrap">$\mathbb{P}\bigl(X>40\bigm\vert X>10\bigr)$.</span>
</div>

由截尾分配的定義可知

$$
f_{\sssig X}\bigl(x\bigm\vert x>10\bigr)=\frac{f_{\sssig X}(x)}{\,\mathbb{P}(X>10)\,}
$$

又可求得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X>10)=\int_{10}^{\infty}\frac{1}{20}e^{-\frac{x}{20}}\,dx=\left[-e^{-\frac{x}{20}}\right]_{10}^{\infty}=e^{-\frac{1}{2}}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X>10)&=\int_{10}^{\infty}\frac{1}{20}e^{-\frac{x}{20}}\,dx\\[0.45em]
&=\left[-e^{-\frac{x}{20}}\right]_{10}^{\infty}=e^{-\frac{1}{2}}
\end{aligned}
$$

</div>

由此可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X}\bigl(x\bigm\vert x>10\bigr)=\frac{\,f_{\sssig X}(x)\,}{e^{-\frac{1}{2}}}=e^{\frac{1}{2}}\times\frac{1}{20}e^{-\frac{x}{20}}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig X}\bigl(x\bigm\vert x>10\bigr)&=\frac{\,f_{\sssig X}(x)\,}{e^{-\frac{1}{2}}}\\[0.45em]
&=e^{\frac{1}{2}}\times\frac{1}{20}e^{-\frac{x}{20}}
\end{aligned}
$$

</div>

故所求為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}\bigl(X>40\bigm\vert X>10\bigr)&=\int_{40}^{\infty}e^{\frac{1}{2}}\times\frac{1}{20}e^{-\frac{x}{20}}\,dx=e^{\frac{1}{2}}\int_{40}^{\infty}\frac{1}{20}e^{-\frac{x}{20}}\,dx\\[0.45em]
&=e^{\frac{1}{2}}\times\left[-e^{-\frac{x}{20}}\right]_{40}^{\infty}=e^{-\frac{3}{2}}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}\bigl(X>40\bigm\vert X>10\bigr)&=\int_{40}^{\infty}e^{\frac{1}{2}}\times\frac{1}{20}e^{-\frac{x}{20}}\,dx\\[0.45em]
&=e^{\frac{1}{2}}\int_{40}^{\infty}\frac{1}{20}e^{-\frac{x}{20}}\,dx\\[0.45em]
&=e^{\frac{1}{2}}\times\left[-e^{-\frac{x}{20}}\right]_{40}^{\infty}=e^{-\frac{3}{2}}
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

若讀者另外計算了 <span class="text-nowrap">$\mathbb{P}(X>30)$，</span>會意外地發現，這個結果與本題所求的 $\mathbb{P}\bigl(X>40\bigm\vert X>10\bigr)$ 一模一樣。這是因為這題的分配是**[指數分配](/lecture-notes/gamma-function-exponential-distribution/#def-exponential-distribution) <span lang="en">(exponential distribution)</span>**，而指數分配是少數具有**[無記憶性](/lecture-notes/exponential-memoryless-and-minima/#thm-memoryless-exp) <span lang="en">(memoryless property)</span>** 的分配，故有此結果。

</div>

## 本篇小結

[Example 3.2 <span lang="en">(Continued)</span>](#ex-joint-pdf-region-basic-conditional) 與 [Example 3.3 <span lang="en">(Continued)</span>](#ex-joint-pdf-triangle-region-conditional) 的作法完全相同。先把 joint pdf 除以 $Y$ 的 marginal pdf，得到 $X$ 在給定 $Y=y$ 之下的 conditional pdf，再把指定的 $y$ 值代進去。兩題的結果有一個明顯的差別: 前者所得的 $6(x-x^{2})$ 之中已經沒有 $y$ 的身影，這與該題的 $X$ 與 $Y$ 獨立相呼應；後者所得的條件 pdf 之中仍有 <span class="text-nowrap">$y$，</span>但這個 $y$ 只是一個常數，代入之後便會消失，真正的變數只有 <span class="text-nowrap">$x$。</span>

接著我們把「條件」由 $Y=y$ 這個薄薄的切片放寬為 $c<Y<d$ 這樣的範圍，此時的條件機率就是 $a<X<b$ 與 $c<Y<d$ 同時發生的機率除以 $c<Y<d$ 的機率，其意義即為在條件空間之中，所求事件所佔的比例。[Example 3.9](#ex-discrete-conditional-table) 的兩個小題便是這件事在離散型的演練，其中第二小題的條件只牽涉 $X_1$ 自己，屬於自我限制的條件，所得的分配即為截尾分配。離散型是 $p_{\sssig X}(x)$ 除以 <span class="text-nowrap">$\mathbb{P}(a<X<b)$，</span>連續型是 $f_{\sssig X}(x)$ 除以同一個機率，並把值域重新限制在 $(a,b)$ 之中。

[Example 3.10](#ex-uniform-conditional-interval) 與 [Example 3.11](#ex-conditional-pdf-from-pdf) 即為截尾分配的計算: 前者的 $X$ 服從 $(0,1)$ 上的[均勻分配](/lecture-notes/uniform-distribution-integral-transform/#def-uniform-distribution)，截在 $X<\frac{1}{4}$ 之後密度由 $1$ 提高為 <span class="text-nowrap">$4$，</span>所求機率為 <span class="text-nowrap">$\frac{1}{2}$；</span>後者的密度為 $\frac{1}{20}e^{-\frac{x}{20}}$ 這個式子，截在 $X>10$ 之後所求機率為 <span class="text-nowrap">$e^{-\frac{3}{2}}$，</span>而這個值恰好等於 <span class="text-nowrap">$\mathbb{P}(X>30)$，</span>此即指數分配的無記憶性。

[下一篇](/lecture-notes/independent-random-variables/)接著處理本篇兩度提到的獨立。該篇說明兩個[隨機變數](/lecture-notes/random-variables-and-pmf/#def-random-variable)要滿足什麼條件才算獨立，以及獨立時聯合分配、邊際分配與條件分配之間會有什麼樣的關係。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
