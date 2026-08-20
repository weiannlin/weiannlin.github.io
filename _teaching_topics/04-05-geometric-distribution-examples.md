---
title: "幾何分配的例題"
subtitle: "Examples of the Geometric Distribution"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 4
topic: 5
order: 405
permalink: /lecture-notes/geometric-distribution-examples/
date: 2026-08-12
published: false
excerpt: "本篇以六道例題演練幾何分配。前兩道直接由實驗幾何分配的機率函數求期望值、變異數與指定事件的機率，其中「投擲硬幣直到第一次出現正面，所需次數為奇數」的機率，正好由無窮等比級數求得 $\\frac{1}{\\,2-p\\,}$ 這個結果。接下來兩道把「等到出現若干個不同結果」的總次數寫成一串成功機率遞減的幾何變數之和，期望值即為各項倒數相加。最後兩道分別以輔助變數搭配雙重期望值定理、全機率定理與變異數分解定理求算，以及由失敗幾何分配說明無記憶性。"
---

[上一篇](/lecture-notes/geometric-distribution-memoryless/)由幾何級數出發，給出[幾何分配](/lecture-notes/geometric-distribution-memoryless/#def-geometric)的定義，證明了機率函數的合法性與期望值、變異數及動差母函數，接著給出[無記憶性](/lecture-notes/geometric-distribution-memoryless/#thm-memoryless)及其逆敘述，最後說明兩個獨立幾何變數取極小值之後仍為幾何分配。本篇不再新增性質，改以六道例題演練上述結果。

六道例題依序處理四件事: 先直接由實驗幾何分配的機率函數求期望值、變異數與指定事件的機率，再把「等到出現若干個不同結果」的總次數寫成一串幾何變數之和，接著以一個輔助變數把問題化為條件分配之下的計算，最後回到失敗幾何分配，看無記憶性在題目中如何呈現。

## 實驗幾何分配的機率、期望值與變異數

<div id="ex-geometric-ex-1" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.10</div>

<div lang="en" markdown="1">
Suppose that a box contains $6$ Hello Kitty stickers and $4$ One Piece stickers. Stickers are drawn from the box one at a time at random, and each sticker is put back into the box after it has been examined. Let $Y$ denote the number of draws made up to and including the first Hello Kitty sticker.

<ol class="topic-list-paren">
  <li>Determine the distribution of <span class="text-nowrap">$Y$.</span></li>
  <li>Evaluate $\mathbb{E}(Y)$ and <span class="text-nowrap">$\mathrm{Var}(Y)$.</span></li>
  <li>What is the probability that at least $2$ draws are needed to obtain a Hello Kitty sticker?</li>
</ol>
</div>

(1) 依照題意敘述，此題為實驗幾何分配，故
{: .topic-paren-item}

$$
Y\sim\mathrm{Geo}(p=0.6),\ y=1,2,\ldots
$$

(2) 由[實驗幾何分配](/lecture-notes/geometric-distribution-memoryless/#def-geometric)的性質可知
{: .topic-paren-item}

$$
\begin{gathered}
\mathbb{E}(Y)=\frac{1}{\,p\,}=\frac{1}{\,0.6\,}\fallingdotseq1.6667\\[0.5em]
\mathrm{Var}(Y)=\frac{\,1-p\,}{p^{2}}=\frac{\,1-0.6\,}{0.6^{2}}\fallingdotseq1.1111
\end{gathered}
$$

(3) 所求為
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(Y\geqslant2)&=1-\mathbb{P}(Y=1)=1-p_{\sssig Y}(1)\\[0.45em]
&=1-0.6\times(1-0.6)^{1-1}=0.4
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(Y\geqslant2)&=1-\mathbb{P}(Y=1)=1-p_{\sssig Y}(1)\\[0.3em]
&=1-0.6\times(1-0.6)^{1-1}=0.4
\end{aligned}
$$

</div>

</div>

<div id="ex-geometric-ex-2" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.11</div>

<div lang="en" markdown="1">
Suppose that a coin is tossed repeatedly, that a head occurs on each toss with probability <span class="text-nowrap">$p$,</span> and that a tail occurs with probability <span class="text-nowrap">$1-p$.</span> The tossing stops as soon as the first head is obtained. What is the probability that the number of tosses required is an odd number?
</div>

依題意可令 $X$ 表示直到第一次出現正面所需之投擲次數，則 $X\sim\mathrm{Geo}(p)$ 為實驗幾何分配，所求為 <span class="text-nowrap">$\mathbb{P}(X\ \text{為奇數})$，</span>即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
p_{\sssig X}(1)+p_{\sssig X}(3)+p_{\sssig X}(5)+\cdots&=p+p(1-p)^{2}+p(1-p)^{4}+\cdots\\[0.45em]
&=\frac{p}{\,1-(1-p)^{2}\,}=\frac{1}{\,2-p\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig X}(1)+p_{\sssig X}(3)+p_{\sssig X}(5)+\cdots&=p+p(1-p)^{2}+p(1-p)^{4}+\cdots\\[0.3em]
&=\frac{p}{\,1-(1-p)^{2}\,}=\frac{1}{\,2-p\,}
\end{aligned}
$$

</div>

</div>

## 等待多個不同結果所需次數的期望值

<div id="ex-geometric-ex-3" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.12</div>

<div lang="en" markdown="1">
Suppose that a fair die is rolled repeatedly until each of its $6$ faces has appeared at least once. Determine the expected number of rolls required.
</div>

依題意可令 $X_i,\ i=1,\ldots,6$ 表示首次擲出第 $i$ 個不曾出現的面所需的投擲次數，則

$$
X_i\sim\mathrm{Geo}\Bigl(p=\frac{\,7-i\,}{6}\Bigr),\ i=1,\ldots,6
$$

所求為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(X_1+\cdots+X_6)=\sum_{i=1}^{6}\mathbb{E}(X_i)=\sum_{i=1}^{6}\frac{6}{\,7-i\,}=14.7
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X_1+\cdots+X_6)&=\sum_{i=1}^{6}\mathbb{E}(X_i)\\[0.3em]
&=\sum_{i=1}^{6}\frac{6}{\,7-i\,}=14.7
\end{aligned}
$$

</div>

</div>

<div id="ex-geometric-ex-4" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.13</div>

<div lang="en" markdown="1">
Suppose that a bag contains $r$ balls, numbered <span class="text-nowrap">$1,2,\ldots,r$.</span> Balls are drawn one at a time with replacement, so that on each draw a ball is taken out, its number is recorded, and the ball is then returned to the bag. The procedure is repeated until $k$ distinct numbers have been recorded, where $k$ is an integer smaller than <span class="text-nowrap">$r$.</span> Let $S_k$ denote the number of draws required. Find <span class="text-nowrap">$\mathbb{E}(S_k)$.</span>
</div>

依題意可令 $X_i,\ i=1,\ldots,k$ 表示得到第 $i$ 個不同的號碼所需的抽樣次數，則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
X_i\sim\mathrm{Geo}\Bigl(p=\frac{\,r+1-i\,}{r}\Bigr),\ i=1,\ldots,k
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
X_i&\sim\mathrm{Geo}\Bigl(p=\frac{\,r+1-i\,}{r}\Bigr),\\[0.45em]
&\quad\ i=1,\ldots,k
\end{aligned}
$$

</div>

所求為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(X_1+\cdots+X_k)=\sum_{i=1}^{k}\mathbb{E}(X_i)=\sum_{i=1}^{k}\frac{r}{\,r+1-i\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X_1+\cdots+X_k)&=\sum_{i=1}^{k}\mathbb{E}(X_i)\\[0.3em]
&=\sum_{i=1}^{k}\frac{r}{\,r+1-i\,}
\end{aligned}
$$

</div>

</div>

## 條件分配之下的期望值、機率與變異數

<div id="ex-geometric-ex-5" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.14</div>

<div lang="en" markdown="1">
Suppose that in a certain school the ratio of male students to female students is $2$ to <span class="text-nowrap">$1$.</span> In order to estimate the average height of the students, individuals are sampled at random one at a time, and the sampling stops as soon as the sample contains at least one male student and at least one female student. Let $N$ denote the number of students sampled.

<ol class="topic-list-paren">
  <li>Evaluate <span class="text-nowrap">$\mathbb{E}(N)$.</span></li>
  <li>Find <span class="text-nowrap">$\mathbb{P}(N=4)$.</span></li>
  <li>Evaluate <span class="text-nowrap">$\mathrm{Var}(N)$.</span></li>
</ol>
</div>

(1) 依題意可令一輔助變數 $X$ 如下
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
X=\left\lbrace
\begin{array}{c@{\quad}l}
0, & \text{第一個樣本為女生}\\[0.5em]
1, & \text{第一個樣本為男生}
\end{array}
\right.
$$

<div class="topic-math-follow" markdown="1">

$$
\Longrightarrow\ p_{\sssig X}(x)=\left\lbrace
\begin{array}{c@{\quad}l}
\frac{1}{\,3\,}, & x=0\\[0.5em]
\frac{2}{\,3\,}, & x=1\\[0.5em]
0, & \text{o.w.}
\end{array}
\right.
$$

</div>

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
X=\left\lbrace
\begin{array}{c@{}l}
0, & \text{第一個樣本為女生}\\[0.4em]
1, & \text{第一個樣本為男生}
\end{array}
\right.
$$

<div class="topic-math-follow" markdown="1">

$$
\Longrightarrow\ p_{\sssig X}(x)=\left\lbrace
\begin{array}{c@{}l}
\frac{1}{\,3\,}, & x=0\\[0.4em]
\frac{2}{\,3\,}, & x=1\\[0.4em]
0, & \text{o.w.}
\end{array}
\right.
$$

</div>

</div>

依照題意敘述，可以知道
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
(N-1\mid X=0)\sim\mathrm{Geo}\Bigl(p=\frac{2}{\,3\,}\Bigr)
$$

<div class="topic-math-follow" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ \mathbb{E}(N-1\mid X=0)&=\frac{3}{\,2\,}\\[0.35em]
\Longrightarrow\ \mathbb{E}(N\mid X=0)&=\frac{\,5\,}{2}
\end{aligned}
$$

</div>

$$
(N-1\mid X=1)\sim\mathrm{Geo}\Bigl(p=\frac{1}{\,3\,}\Bigr)
$$

<div class="topic-math-follow" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ \mathbb{E}(N-1\mid X=1)&=3\\[0.35em]
\Longrightarrow\ \mathbb{E}(N\mid X=1)&=4
\end{aligned}
$$

</div>

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
(N-1\mid X=0)\sim\mathrm{Geo}\Bigl(p=\frac{2}{\,3\,}\Bigr)
$$

<div class="topic-math-follow" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ \mathbb{E}(N-1\mid X=0)&=\frac{3}{\,2\,}\\[0.3em]
\Longrightarrow\ \mathbb{E}(N\mid X=0)&=\frac{\,5\,}{2}
\end{aligned}
$$

</div>

$$
(N-1\mid X=1)\sim\mathrm{Geo}\Bigl(p=\frac{1}{\,3\,}\Bigr)
$$

<div class="topic-math-follow" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ \mathbb{E}(N-1\mid X=1)&=3\\[0.3em]
\Longrightarrow\ \mathbb{E}(N\mid X=1)&=4
\end{aligned}
$$

</div>

</div>

則由[雙重期望值](/lecture-notes/double-expectation-theorem/#thm-double-expectation)可知，所求為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(N)&=\mathbb{E}\bigl[\mathbb{E}(N\mid X)\bigr]\\[0.45em]
&=\mathbb{E}(N\mid X=0)\,\mathbb{P}(X=0)+\mathbb{E}(N\mid X=1)\,\mathbb{P}(X=1)\\[0.45em]
&=\frac{\,5\,}{2}\times\frac{1}{\,3\,}+4\times\frac{2}{\,3\,}=\frac{\,7\,}{2}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(N)&=\mathbb{E}\bigl[\mathbb{E}(N\mid X)\bigr]\\[0.3em]
&=\mathbb{E}(N\mid X=0)\,\mathbb{P}(X=0)\\[0.3em]
&\qquad+\mathbb{E}(N\mid X=1)\,\mathbb{P}(X=1)\\[0.3em]
&=\frac{\,5\,}{2}\times\frac{1}{\,3\,}+4\times\frac{2}{\,3\,}=\frac{\,7\,}{2}
\end{aligned}
$$

</div>

(2) 由[全機率定理](/lecture-notes/conditional-law-of-total-probability/#thm-law-of-total-prob-r-v)可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(N=4)&=\sum_{x=0}^{1}\mathbb{P}(N=4,\ X=x)\\[0.45em]
&=\sum_{x=0}^{1}\mathbb{P}(N=4\mid X=x)\,\mathbb{P}(X=x)\\[0.45em]
&=\mathbb{P}(N=4\mid X=0)\,\mathbb{P}(X=0)\\[0.45em]
&\quad +\mathbb{P}(N=4\mid X=1)\,\mathbb{P}(X=1)\\[0.45em]
&=\Bigl(\frac{1}{\,3\,}\Bigr)^{2}\Bigl(\frac{2}{\,3\,}\Bigr)\times\frac{1}{\,3\,}+\Bigl(\frac{2}{\,3\,}\Bigr)^{2}\Bigl(\frac{1}{\,3\,}\Bigr)\times\frac{2}{\,3\,}=\frac{10}{\,81\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(N=4)&=\sum_{x=0}^{1}\mathbb{P}(N=4,\ X=x)\\[0.3em]
&=\sum_{x=0}^{1}\mathbb{P}(N=4\mid X=x)\,\mathbb{P}(X=x)\\[0.3em]
&=\mathbb{P}(N=4\mid X=0)\,\mathbb{P}(X=0)\\[0.3em]
&\qquad +\mathbb{P}(N=4\mid X=1)\,\mathbb{P}(X=1)\\[0.3em]
&=\Bigl(\frac{1}{\,3\,}\Bigr)^{2}\Bigl(\frac{2}{\,3\,}\Bigr)\times\frac{1}{\,3\,}\\[0.3em]
&\qquad +\Bigl(\frac{2}{\,3\,}\Bigr)^{2}\Bigl(\frac{1}{\,3\,}\Bigr)\times\frac{2}{\,3\,}=\frac{10}{\,81\,}
\end{aligned}
$$

</div>

(3) 由[變異數分解定理](/lecture-notes/variance-decomposition-theorem/#thm-var-decom-thm)可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(N)&=\mathbb{E}\bigl[\mathrm{Var}(N\mid X)\bigr]+\mathrm{Var}\bigl[\mathbb{E}(N\mid X)\bigr]\\[0.45em]
&=\mathrm{Var}(N\mid X=0)\,\mathbb{P}(X=0)+\mathrm{Var}(N\mid X=1)\,\mathbb{P}(X=1)\\[0.45em]
&\quad +\mathrm{Var}\bigl[\mathbb{E}(N\mid X)\bigr]\\[0.45em]
&=\frac{\frac{1}{\,3\,}}{\,\bigl(\frac{2}{\,3\,}\bigr)^{2}\,}\times\frac{1}{\,3\,}+\frac{\frac{2}{\,3\,}}{\,\bigl(\frac{1}{\,3\,}\bigr)^{2}\,}\times\frac{2}{\,3\,}\\[0.45em]
&\quad +\biggl[\Bigl(\frac{\,5\,}{2}\Bigr)^{2}\times\frac{1}{\,3\,}+4^{2}\times\frac{2}{\,3\,}\biggr]-\Bigl(\frac{\,7\,}{2}\Bigr)^{2}=\frac{\,19\,}{4}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(N)&=\mathbb{E}\bigl[\mathrm{Var}(N\mid X)\bigr]+\mathrm{Var}\bigl[\mathbb{E}(N\mid X)\bigr]\\[0.3em]
&=\mathrm{Var}(N\mid X=0)\,\mathbb{P}(X=0)\\[0.3em]
&\qquad +\mathrm{Var}(N\mid X=1)\,\mathbb{P}(X=1)\\[0.3em]
&\qquad +\mathrm{Var}\bigl[\mathbb{E}(N\mid X)\bigr]\\[0.3em]
&=\frac{\frac{1}{\,3\,}}{\,\bigl(\frac{2}{\,3\,}\bigr)^{2}\,}\times\frac{1}{\,3\,}+\frac{\frac{2}{\,3\,}}{\,\bigl(\frac{1}{\,3\,}\bigr)^{2}\,}\times\frac{2}{\,3\,}\\[0.3em]
&\qquad +\biggl[\Bigl(\frac{\,5\,}{2}\Bigr)^{2}\times\frac{1}{\,3\,}+4^{2}\times\frac{2}{\,3\,}\biggr]\\[0.3em]
&\qquad -\Bigl(\frac{\,7\,}{2}\Bigr)^{2}=\frac{\,19\,}{4}
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

上述 (2) 當中所計算的 <span class="text-nowrap">$\mathbb{P}(N=4\mid X=x),\ x=0,1$，</span>若讀者感到稍微陌生，不妨思考看看此時已知的分配為何，可以得到 <span class="text-nowrap">$\mathbb{P}(N-1=4-1\mid X=x),\ x=0,1$，</span>如此一來便可計算其機率。

而在 (3) 中，我們利用了 $\mathrm{Var}(N\mid X=x)=\mathrm{Var}(N-1\mid X=x)$ 的特性，快速地得到[條件變異數](/lecture-notes/conditional-expectation-and-variance/#def-conditional-variance)，並計算條件變異數的期望值；再由 (1) 所計算的[條件期望值](/lecture-notes/conditional-expectation-and-variance/#def-conditional-expectation)，計算條件期望值的變異數，從而完成變異數分解定理。

</div>

## 失敗幾何分配與無記憶性

<div id="ex-geometric-ex-6" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.15</div>

<div lang="en" markdown="1">
Suppose that, during the Second World War, a bomber of the British Air Force is sent on a sequence of missions against targets in Germany. Each mission is dangerous: the bomber comes back safely from any single mission with probability <span class="text-nowrap">$p_s$,</span> and this probability does not depend on how many missions it has already completed safely. All missions are independent of one another. Let $X$ denote the number of missions that the bomber completes safely before it is shot down.

<ol class="topic-list-paren">
  <li>Determine the name of the distribution of <span class="text-nowrap">$X$,</span> and find <span class="text-nowrap">$\mathbb{P}(X=x)$.</span></li>
  <li>Suppose that the bomber has already completed $k$ missions safely, and let $Y$ denote the number of further missions that it completes safely before being shot down. Find <span class="text-nowrap">$\mathbb{P}(Y=y)$.</span></li>
  <li>Determine how the distributions of $X$ and $Y$ are related, and find the property of this kind of distribution that accounts for this relationship.</li>
</ol>
</div>

(1) 依題意可知 <span class="text-nowrap">$X\sim\mathrm{Geo}(p=1-p_s)$，</span>且可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X=x)=\left\lbrace
\begin{array}{c@{\quad}l}
(1-p_s)\,p_s^{x}, & x=0,1,2,\ldots\\[0.5em]
0, & \text{o.w.}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases">
  <div class="topic-cases__lhs">$\mathbb{P}(X=x)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$(1-p_s)\,p_s^{x},$</div>
    <div class="topic-cases__cond">$x=0,1,2,\ldots$</div>
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$\text{o.w.}$</div>
  </div>
</div>

</div>

(2) <span class="text-nowrap">$Y\sim\mathrm{Geo}(p=1-p_s)$，</span>且可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(Y=y)=\left\lbrace
\begin{array}{c@{\quad}l}
(1-p_s)\,p_s^{y}, & y=0,1,2,\ldots\\[0.5em]
0, & \text{o.w.}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases">
  <div class="topic-cases__lhs">$\mathbb{P}(Y=y)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$(1-p_s)\,p_s^{y},$</div>
    <div class="topic-cases__cond">$y=0,1,2,\ldots$</div>
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$\text{o.w.}$</div>
  </div>
</div>

</div>

(3) $X$ 與 $Y$ 的分配同為幾何分配，且參數皆為 <span class="text-nowrap">$p=1-p_s$，</span>此類分配不因過去曾成功完成的任務數 $k$ 而改變，稱為[無記憶性](/lecture-notes/geometric-distribution-memoryless/#thm-memoryless)。
{: .topic-paren-item}

</div>

## 本篇小結

[Example 4.10](#ex-geometric-ex-1) 與 [Example 4.11](#ex-geometric-ex-2) 是實驗幾何分配的直接計算。前者的成功機率為 <span class="text-nowrap">$0.6$，</span>期望值 $\frac{1}{\,p\,}$ 與變異數 $\frac{\,1-p\,}{p^{2}}$ 代入即得，而「至少需抽取 $2$ 次」由餘事件處理，只要扣掉第一次就抽中的機率。後者所求的是「所需次數為奇數」的機率，把 $p_{\sssig X}(1),\ p_{\sssig X}(3),\ p_{\sssig X}(5),\ldots$ 逐項相加，得到的是首項為 $p$ 而公比為 $(1-p)^{2}$ 的無窮等比級數，總和為 $\frac{1}{\,2-p\,}$ 這個結果。

[Example 4.12](#ex-geometric-ex-3) 與 [Example 4.13](#ex-geometric-ex-4) 用的是同一個手法: 「等到出現 $6$ 個不同的面」或「等到記錄下 $k$ 個不同的號碼」，都可以把總次數切成一段一段，每一段是「從已經出現 $i-1$ 個不同結果，到出現第 $i$ 個不同結果」所需的次數。每一段各自服從一個幾何分配，成功機率是尚未出現的結果所佔的比例，因而隨著 $i$ 遞減；總期望值就是各段期望值相加，也就是一串倒數之和。擲公正骰子的情形算出來是 $14.7$ 次，$r$ 個球取到 $k$ 個不同號碼的情形則是 $k$ 個形如 $\frac{r}{\,r+1-i\,}$ 的分數相加。

[Example 4.14](#ex-geometric-ex-5) 的抽樣要抽到男女都出現才停止，本身不是幾何分配，但只要引入一個輔助變數 $X$ 記錄第一個樣本的性別，在給定 $X$ 之後，剩下要抽的人數 $N-1$ 就是一個幾何變數: 第一個抽到女生時還要等一個男生，成功機率為 <span class="text-nowrap">$\frac{2}{\,3\,}$；</span>第一個抽到男生時還要等一個女生，成功機率為 <span class="text-nowrap">$\frac{1}{\,3\,}$。</span>三個小題因而分別由雙重期望值、全機率定理與變異數分解定理完成，答案依序是 <span class="text-nowrap">$\frac{\,7\,}{2}$、</span>$\frac{10}{\,81\,}$ 與 <span class="text-nowrap">$\frac{\,19\,}{4}$。</span>其中變異數的計算用到 $\mathrm{Var}(N\mid X=x)=\mathrm{Var}(N-1\mid X=x)$ 這個關係，因為兩者只差一個常數。

[Example 4.15](#ex-geometric-ex-6) 記錄的是被擊落之前所能安全完成的任務數，值域自 $0$ 起算，屬於失敗幾何分配。已經安全完成 $k$ 次之後還能再完成幾次，其分配與一開始的 $X$ 完全相同，這正是[無記憶性](/lecture-notes/geometric-distribution-memoryless/#thm-memoryless)所述的性質。

[下一篇](/lecture-notes/negative-binomial-distribution/)把「做到第一次成功為止」改成「做到第 $r$ 次成功為止」，所需要的實驗次數即服從負二項分配；該篇先給出驗證機率函數時所需要的負二項級數。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
