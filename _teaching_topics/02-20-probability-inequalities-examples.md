---
title: "機率不等式的例題"
subtitle: "Examples of Probability Inequalities"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 20
order: 220
permalink: /teaching-topics/probability-inequalities-examples/
date: 2026-08-06
published: true
excerpt: "八道例題演練同一系列機率不等式的用法。前兩道不套現成的不等式，改由密度或機率函數本身的單調性造出不等關係，一道用積分、一道用等差級數的和。第三道由非負函數的機率界限取 $h(x)=(x-\\mu_{X})^{2}$ 直接導出柴比雪夫不等式，第四道反過來由兩個尾機率求變異數的下界。第五道比較同一個上界在均勻分配與三點分配之下的鬆緊，第六道把柴比雪夫不等式代入卜瓦松分配。第七道以同一題的兩個小問對照馬可夫不等式與單邊柴比雪夫不等式，看出動差訊息愈多、上界愈精確。最後一道是車諾夫不等式的完整示範，代入卜瓦松分配的動差母函數之後，以一階與二階條件求出使上界最小的 $t^{*}$。"
---

[上一篇](/teaching-topics/probability-inequalities/)由一條以非負函數界定機率的定理出發，依序導出[馬可夫不等式](/teaching-topics/probability-inequalities/#thm-markov)、[柴比雪夫不等式](/teaching-topics/probability-inequalities/#thm-chebyshev)、[單邊柴比雪夫不等式](/teaching-topics/probability-inequalities/#thm-one-tailed-chebyshev)與[車諾夫不等式](/teaching-topics/probability-inequalities/#thm-chernoff)。五條不等式的形式各不相同，用上的動差訊息也有多有少，實際遇到一道題目時該挑哪一條、又該怎麼代入，仍要靠例題才看得清楚。

本篇以八道例題演練這一系列不等式的用法。前兩道不套現成的不等式，改由密度或機率函數本身的單調性造出不等關係；第三道由[非負函數的機率界限](/teaching-topics/probability-inequalities/#thm-nonnegative-function-bound)直接導出柴比雪夫不等式；其後三道分別由尾機率反求[變異數](/teaching-topics/variance/#def-variance)的下界、檢驗柴比雪夫上界的鬆緊，以及把柴比雪夫不等式代入卜瓦松分配；第七道以同一題的兩個小問對照馬可夫不等式與單邊柴比雪夫不等式；最後一道則是車諾夫不等式的完整示範。


<div id="ex-decreasing-density-bound" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.36</div>

<div lang="en" markdown="1">
Suppose that $X$ is a continuous random variable taking only positive values, and that its probability density function $f_{\sssig X}(x)$ is non-increasing on <span class="text-nowrap">$x>0$.</span> Show that

$$
x^{2}f_{\sssig X}(x)\leqslant2\,\mathbb{E}(X),\quad x>0
$$

</div>

由於 $f_{\sssig X}(x)$ 在 $x>0$ 的範圍內為 $x$ 之非遞增函數，故可知 <span class="text-nowrap">$f_{\sssig X}(t)\geqslant f_{\sssig X}(x)$，</span>$\forall\,0<t<x$，則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\int_{0}^{\infty}t\,f_{\sssig X}(t)\,dt\geqslant\int_{0}^{x}t\,f_{\sssig X}(t)\,dt\geqslant\int_{0}^{x}t\,f_{\sssig X}(x)\,dt\\[0.45em]
&=f_{\sssig X}(x)\int_{0}^{x}t\,dt=\frac{\,x^{2}\,}{2}\,f_{\sssig X}(x),\quad\forall\,x>0
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\int_{0}^{\infty}t\,f_{\sssig X}(t)\,dt\\[0.45em]
&\geqslant\int_{0}^{x}t\,f_{\sssig X}(t)\,dt\\[.45em]
&\geqslant\int_{0}^{x}t\,f_{\sssig X}(x)\,dt\\[0.45em]
&=f_{\sssig X}(x)\int_{0}^{x}t\,dt\\[0.45em]
&=\frac{\,x^{2}\,}{2}\,f_{\sssig X}(x),\quad\forall\,x>0
\end{aligned}
$$

</div>

此即

$$
x^{2}f_{\sssig X}(x)\leqslant2\,\mathbb{E}(X),\quad x>0
$$

原式得證。

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

在處理不等式問題的時候，很重要的技巧是考慮函數或範圍本身的大小關係，進而利用這些性質「創造」出不等式中的大小關係，但這些技巧往往需要許多經驗，需要讀者熟悉。

</div>

<div id="ex-decreasing-pmf-bound" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.37</div>

<div lang="en" markdown="1">
Suppose that $X$ takes values in the positive integers and that $\mathbb{P}(X=a)$ is a decreasing function of <span class="text-nowrap">$a$.</span> Show that

$$
\mathbb{P}(X=a)\leqslant\frac{\,2\,\mathbb{E}(X)\,}{a^{2}}
$$

</div>

由於 $\mathbb{P}(X=a)$ 為 $a$ 之遞減函數，故可知 $\mathbb{P}(X=n)\geqslant\mathbb{P}(X=a)$，$\forall\,0<n<a$，$n, a\in\mathbb{N}$，則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\sum_{n=1}^{\infty}n\,\mathbb{P}(X=n)\geqslant\sum_{n=1}^{a}n\,\mathbb{P}(X=n)\\[0.45em]
&\geqslant\sum_{n=1}^{a}n\,\mathbb{P}(X=a)=\mathbb{P}(X=a)\sum_{n=1}^{a}n\\[0.45em]
&=\mathbb{P}(X=a)\,\frac{\,a\,(a+1)\,}{2}\geqslant\mathbb{P}(X=a)\,\frac{\,a^{2}\,}{2},\quad\forall\,a\in\mathbb{N}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\sum_{n=1}^{\infty}n\,\mathbb{P}(X=n)\\[0.45em]
&\geqslant\sum_{n=1}^{a}n\,\mathbb{P}(X=n)\\[0.45em]
&\geqslant\sum_{n=1}^{a}n\,\mathbb{P}(X=a)\\[0.45em]
&=\mathbb{P}(X=a)\sum_{n=1}^{a}n\\[0.45em]
&=\mathbb{P}(X=a)\,\frac{\,a\,(a+1)\,}{2}\\[0.45em]
&\geqslant\mathbb{P}(X=a)\,\frac{\,a^{2}\,}{2},\quad\forall\,a\in\mathbb{N}
\end{aligned}
$$

</div>

此即

$$
\mathbb{P}(X=a)\leqslant\frac{\,2\,\mathbb{E}(X)\,}{a^{2}}
$$

原式得證。

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這題中，除了應用了等差級數的和之外，其實基本的想法與概念 (甚至是結論) 都與 [Example 2.36](#ex-decreasing-density-bound) 完全相同，讀者不妨細細品味其中的奧妙。

</div>

<div id="ex-general-markov-to-chebyshev" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.38</div>

<div lang="en" markdown="1">
Suppose that $X$ is a random variable with $\mathbb{E}(X)=\mu_{\sssig X}$ and $\mathrm{Var}(X)=\sigma_{\sssig X}^{2}$, that $h(x)$ is a non-negative real-valued function, and that $c$ is a positive constant.

(1) Show that
{: .topic-paren-item}

$$
\mathbb{P}\bigl(h(X)\geqslant c\bigr)\leqslant\frac{\,\mathbb{E}\bigl[h(X)\bigr]\,}{c}
$$

(2) Using the result of (1), show that Chebyshev’s inequality
{: .topic-paren-item}

$$
\mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert\geqslant k\,\sigma_{\sssig X}\bigr)\leqslant\frac{1}{\,k^{2}\,}
$$

holds for every $k>0$, provided that <span class="text-nowrap">$\sigma_{\sssig X}>0$.</span>
{: .topic-paren-cont}

</div>

(1) 這一小題即 [Theorem 2.31](/teaching-topics/probability-inequalities/#thm-nonnegative-function-bound) 的敘述。我們在此以連續型為例證明，並令 $A=\lbrace\,x\mid h(x)\geqslant c\,\rbrace$，則
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[h(X)\bigr]&=\int_{-\infty}^{\infty}h(x)\,f_{\sssig X}(x)\,dx\\[0.45em]
&=\int_{A}h(x)\,f_{\sssig X}(x)\,dx+\int_{A^{\prime}}h(x)\,f_{\sssig X}(x)\,dx\\[0.45em]
&\geqslant\int_{A}h(x)\,f_{\sssig X}(x)\,dx\geqslant\int_{A}c\,f_{\sssig X}(x)\,dx\\[0.45em]
&=c\int_{A}f_{\sssig X}(x)\,dx=c\,\mathbb{P}(X\in A)=c\,\mathbb{P}\bigl(h(X)\geqslant c\bigr)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[h(X)\bigr]&=\int_{-\infty}^{\infty}h(x)\,f_{\sssig X}(x)\,dx\\[0.45em]
&=\int_{A}h(x)\,f_{\sssig X}(x)\,dx\\[.2em]
&\qquad\quad+\int_{A^{\prime}}h(x)\,f_{\sssig X}(x)\,dx\\[0.45em]
&\geqslant\int_{A}h(x)\,f_{\sssig X}(x)\,dx\\[0.45em]
&\geqslant\int_{A}c\,f_{\sssig X}(x)\,dx\\[.45em]
&=c\int_{A}f_{\sssig X}(x)\,dx\\[0.45em]
&=c\,\mathbb{P}(X\in A)\\[.45em]
&=c\,\mathbb{P}\bigl(h(X)\geqslant c\bigr)
\end{aligned}
$$

</div>

此即
{: .topic-paren-cont}

$$
\mathbb{P}\bigl(h(X)\geqslant c\bigr)\leqslant\frac{\,\mathbb{E}\bigl[h(X)\bigr]\,}{c}
$$

(2) 令 $h(x)=(x-\mu_{\sssig X})^{2}$，則根據 (1) 可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert\geqslant k\,\sigma_{\sssig X}\bigr)&=\mathbb{P}\bigl(h(X)=(X-\mu_{\sssig X})^{2}\geqslant k^{2}\,\sigma_{\sssig X}^{2}\bigr)\\[0.45em]
&\leqslant\frac{\,\mathbb{E}\bigl[(X-\mu_{\sssig X})^{2}\bigr]\,}{k^{2}\,\sigma_{\sssig X}^{2}}=\frac{\,\sigma_{\sssig X}^{2}\,}{\,k^{2}\,\sigma_{\sssig X}^{2}\,}=\frac{1}{\,k^{2}\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert\geqslant k\,\sigma_{\sssig X}\bigr)\\[.45em]
&=\mathbb{P}\bigl(h(X)=(X-\mu_{\sssig X})^{2}\geqslant k^{2}\,\sigma_{\sssig X}^{2}\bigr)\\[0.45em]
&\leqslant\frac{\,\mathbb{E}\bigl[(X-\mu_{\sssig X})^{2}\bigr]\,}{k^{2}\,\sigma_{\sssig X}^{2}}\\[0.45em]
&=\frac{\,\sigma_{\sssig X}^{2}\,}{\,k^{2}\,\sigma_{\sssig X}^{2}\,}=\frac{1}{\,k^{2}\,}
\end{aligned}
$$

</div>

原式得證。
{: .topic-paren-cont}

</div>

<div id="ex-variance-lower-bound" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.39</div>

<div lang="en" markdown="1">
Suppose that a random variable $X$ satisfies $\mathbb{E}(X)=15$, $\mathbb{P}(X\geqslant20)=0.5$ and <span class="text-nowrap">$\mathbb{P}(X\leqslant10)=0.2$.</span> Determine a lower bound for <span class="text-nowrap">$\mathrm{Var}(X)$.</span>
</div>

由題意可知 $\mathbb{E}(X)=15$、$\mathbb{P}(X\geqslant20)=0.5$ 與 $\mathbb{P}(X\leqslant10)=0.2$，則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(10<X<20)&=1-\mathbb{P}(X\leqslant10)-\mathbb{P}(X\geqslant20)\\[0.45em]
&=1-0.2-0.5=0.3
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(10<X<20)\\[.45em]
&=1-\mathbb{P}(X\leqslant10)-\mathbb{P}(X\geqslant20)\\[0.45em]
&=1-0.2-0.5=0.3
\end{aligned}
$$

</div>

又由[柴比雪夫不等式](/teaching-topics/probability-inequalities/#thm-chebyshev)可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(10<X<20)&=\mathbb{P}(15-5<X<15+5)\\[0.45em]
&=\mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert<5\bigr)\geqslant1-\frac{\,\sigma_{\sssig X}^{2}\,}{5^{2}}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(10<X<20)\\[.45em]
&=\mathbb{P}(15-5<X<15+5)\\[0.45em]
&=\mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert<5\bigr)\\[.45em]
&\geqslant1-\frac{\,\sigma_{\sssig X}^{2}\,}{5^{2}}
\end{aligned}
$$

</div>

則

$$
0.3\geqslant1-\frac{\,\sigma_{\sssig X}^{2}\,}{25}
$$

所求為

$$
\sigma_{\sssig X}^{2}\geqslant17.5
$$

</div>

<div id="ex-chebyshev-sharpness" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.40</div>

<div lang="en" markdown="1">
Suppose that a random variable $X$ has mean $\mu_{\sssig X}$ and variance <span class="text-nowrap">$0<\sigma_{\sssig X}^{2}<\infty$.</span> Chebyshev’s inequality states that

$$
\mathbb{P}(\lvert X-\mu_{\sssig X}\rvert\geqslant k\,\sigma_{\sssig X})\leqslant\frac{1}{\,k^{2}\,},\quad k>0
$$

(1) Show that the upper bound above is not close to the true probability when $X$ is uniformly distributed on <span class="text-nowrap">$(0,1)$.</span>
{: .topic-paren-item}

(2) Show that the upper bound above cannot be improved when $X$ has the probability mass function
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X=x)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{1}{\,2k^{2}\,}, & x=-1, 1\\[0.8em]
1-\dfrac{1}{\,k^{2}\,}, & x=0\\[0.8em]
0, & \text{elsewhere}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\mathbb{P}(X=x)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{1}{\,2k^{2}\,}, &  x=-1, 1\\[0.7em]
1-\dfrac{1}{\,k^{2}\,}, &  x=0\\[0.7em]
0, & \text{elsewhere}
\end{array}
\right.
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

題目給的範圍只有 $k>0$，並未再對 $k$ 加上其他限制。第 (2) 小題要說明的是[柴比雪夫不等式](/teaching-topics/probability-inequalities/#thm-chebyshev)所提供的上界不可改進，而這件事要先有一個機率分配才有意義，所給的 $\mathbb{P}(X=x)$ 卻要在 $k\geqslant1$ 時才是機率分配: $0<k<1$ 時 $\frac{1}{\,k^{2}\,}>1$，$x=0$ 之處的 $1-\frac{1}{\,k^{2}\,}$ 為負，而機率不能為負。$k=1$ 時 $1-\frac{1}{\,k^{2}\,}=0$，$X$ 以各 $\frac{1}{\,2\,}$ 的機率取 $-1$ 與 $1$，仍是一個機率分配。故第 (2) 小題以下另設 $k\geqslant1$。

</div>

(1) 若已知 $X\sim\mathcal{U}(0,1)$，則 <span class="text-nowrap">$\mathbb{E}(X)=\frac{1}{\,2\,}$，</span>$\mathrm{Var}(X)=\frac{1}{\,12\,}$，故
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert\geqslant k\,\sigma_{\sssig X}\bigr)=\mathbb{P}\biggl(\Bigl\lvert X-\frac{1}{\,2\,}\Bigr\rvert\geqslant k\,\sqrt{\frac{1}{\,12\,}}\biggr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert\geqslant k\,\sigma_{\sssig X}\bigr)\\[.45em]
&=\mathbb{P}\biggl(\Bigl\lvert X-\frac{1}{\,2\,}\Bigr\rvert\geqslant k\,\sqrt{\frac{1}{\,12\,}}\biggr)
\end{aligned}
$$

</div>

則若取 $k=\sqrt{3}$，我們有
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}\biggl(\Bigl\lvert X-\frac{1}{\,2\,}\Bigr\rvert\geqslant\sqrt{3}\cdot\sqrt{\frac{1}{\,12\,}}\biggr)&=\mathbb{P}\biggl(\Bigl\lvert X-\frac{1}{\,2\,}\Bigr\rvert\geqslant\frac{1}{\,2\,}\biggr)\\[0.45em]
&=\mathbb{P}(X\leqslant0\ \text{或}\ X\geqslant1)=0
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}\biggl(\Bigl\lvert X-\frac{1}{\,2\,}\Bigr\rvert\geqslant\sqrt{3}\cdot\sqrt{\frac{1}{\,12\,}}\biggr)\\[.45em]
&=\mathbb{P}\biggl(\Bigl\lvert X-\frac{1}{\,2\,}\Bigr\rvert\geqslant\frac{1}{\,2\,}\biggr)\\[0.45em]
&=\mathbb{P}(X\leqslant0\ \text{或}\ X\geqslant1)=0
\end{aligned}
$$

</div>

又[柴比雪夫不等式](/teaching-topics/probability-inequalities/#thm-chebyshev)可提供之機率上界為
{: .topic-paren-cont}

$$
\mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert\geqslant\sqrt{3}\,\sigma_{\sssig X}\bigr)\leqslant\frac{1}{\,3\,}
$$

則可知[柴比雪夫不等式](/teaching-topics/probability-inequalities/#thm-chebyshev)可提供之機率上界，在此例中並不好。
{: .topic-paren-cont}

(2) 由 $X$ 之分配可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=-1\cdot\frac{1}{\,2k^{2}\,}+0\cdot\Bigl(1-\frac{1}{\,k^{2}\,}\Bigr)+1\cdot\frac{1}{\,2k^{2}\,}=0\\[0.7em]
\mathbb{E}(X^{2})&=(-1)^{2}\cdot\frac{1}{\,2k^{2}\,}+0^{2}\cdot\Bigl(1-\frac{1}{\,k^{2}\,}\Bigr)+1^{2}\cdot\frac{1}{\,2k^{2}\,}=\frac{1}{\,k^{2}\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}(X)=0\qquad \mathbb{E}(X^{2})=\frac{1}{\,k^{2}\,}
\end{aligned}
$$

</div>

則
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}(X)=\mathbb{E}(X^{2})-\bigl[\mathbb{E}(X)\bigr]^{2}=\frac{1}{\,k^{2}\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(X)&=\mathbb{E}(X^{2})-\bigl[\mathbb{E}(X)\bigr]^{2}=\frac{1}{\,k^{2}\,}
\end{aligned}
$$

</div>

故可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert\geqslant k\,\sigma_{\sssig X}\bigr)=\mathbb{P}\biggl(\lvert X\rvert\geqslant k\,\sqrt{\frac{1}{\,k^{2}\,}}\biggr)=\mathbb{P}\bigl(\lvert X\rvert\geqslant1\bigr)=\frac{1}{\,k^{2}\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert\geqslant k\,\sigma_{\sssig X}\bigr)\\[.45em]
&=\mathbb{P}\biggl(\lvert X\rvert\geqslant k\,\sqrt{\frac{1}{\,k^{2}\,}}\biggr)\\[0.45em]
&=\mathbb{P}\bigl(\lvert X\rvert\geqslant1\bigr)=\frac{1}{\,k^{2}\,}
\end{aligned}
$$

</div>

又[柴比雪夫不等式](/teaching-topics/probability-inequalities/#thm-chebyshev)可提供之機率上界為
{: .topic-paren-cont}

$$
\mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert\geqslant k\,\sigma_{\sssig X}\bigr)\leqslant\frac{1}{\,k^{2}\,}
$$

則可知[柴比雪夫不等式](/teaching-topics/probability-inequalities/#thm-chebyshev)可提供之機率上界，在此例中不可改進。
{: .topic-paren-cont}

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

在這題中所謂的「不好」或是「不可改進」，其實都是在指這個上界是不是「貼近」真實的機率，故我們的證明策略在第一小題中，是尋找是否有存在某個 <span class="text-nowrap">$k>0$，</span>使得[柴比雪夫不等式](/teaching-topics/probability-inequalities/#thm-chebyshev)提供之上界無法貼近同範圍之真實機率；反之，如果要說明其不可改進，便是說明對任何的 $k\geqslant1$ 而言，[柴比雪夫不等式](/teaching-topics/probability-inequalities/#thm-chebyshev)提供之上界都恰巧是同範圍之真實機率。

</div>

<div id="ex-poisson-chebyshev" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.41</div>

<div lang="en" markdown="1">
Suppose that $X$ has a Poisson distribution with parameter <span class="text-nowrap">$\lambda$.</span> Using Chebyshev’s inequality, show that

$$
\mathbb{P}\Bigl(X\leqslant\frac{\,\lambda\,}{2}\Bigr)\leqslant\frac{4}{\,\lambda\,}
$$

</div>

由 $X\sim\mathrm{Poi}(\lambda)$ 可知 $\mathbb{E}(X)=\mathrm{Var}(X)=\lambda$，則依[柴比雪夫不等式](/teaching-topics/probability-inequalities/#thm-chebyshev)可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}\Bigl(X\leqslant\frac{\,\lambda\,}{2}\Bigr)&=\mathbb{P}\Bigl(X-\lambda\leqslant-\frac{\,\lambda\,}{2}\Bigr)\leqslant\mathbb{P}\Bigl(\lvert X-\lambda\rvert\geqslant\frac{\,\lambda\,}{2}\Bigr)\\[0.45em]
&\leqslant\frac{\lambda}{\,\bigl(\frac{\,\lambda\,}{2}\bigr)^{2}\,}=\frac{4}{\,\lambda\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}\Bigl(X\leqslant\frac{\,\lambda\,}{2}\Bigr)&=\mathbb{P}\Bigl(X-\lambda\leqslant-\frac{\,\lambda\,}{2}\Bigr)\\[0.45em]
&\leqslant\mathbb{P}\Bigl(\lvert X-\lambda\rvert\geqslant\frac{\,\lambda\,}{2}\Bigr)\\[0.45em]
&\leqslant\frac{\lambda}{\,\bigl(\frac{\,\lambda\,}{2}\bigr)^{2}\,}=\frac{4}{\,\lambda\,}
\end{aligned}
$$

</div>

原式得證。

</div>

<div id="ex-household-income-bounds" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.42</div>

<div lang="en" markdown="1">
Suppose that families in a certain area have an average income of <span class="text-nowrap">$100{,}000$.</span>

<ol class="topic-list-paren">
  <li>Find an upper bound for the fraction of those families whose income exceeds <span class="text-nowrap">$500{,}000$.</span></li>
  <li>Given in addition that the standard deviation of family income is <span class="text-nowrap">$80{,}000$,</span> find an upper bound smaller than the one obtained in (1).</li>
</ol>
</div>

(1) 令 $X$ 為該地區的家庭所得，則 $X$ 為非負[隨機變數](/teaching-topics/random-variables-and-pmf/#def-random-variable)，故由[馬可夫不等式](/teaching-topics/probability-inequalities/#thm-markov)可以得到下面的界限
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X\geqslant500{,}000)\leqslant\frac{\mathbb{E}(X)}{\,500{,}000\,}=\frac{100{,}000}{\,500{,}000\,}=0.2
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X\geqslant500{,}000)&\leqslant\frac{\mathbb{E}(X)}{\,500{,}000\,}\\[0.45em]
&=\frac{100{,}000}{\,500{,}000\,}\\[.45em]
&=0.2
\end{aligned}
$$

</div>

(2) 若已知 $\sigma_{\sssig X}=80{,}000$，且 $500{,}000-\mathbb{E}(X)=400{,}000$，則可由[單邊柴比雪夫不等式 (坎特利不等式)](/teaching-topics/probability-inequalities/#thm-one-tailed-chebyshev)知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X\geqslant500{,}000)&=\mathbb{P}\bigl(X-\mathbb{E}(X)\geqslant500{,}000-\mathbb{E}(X)\bigr)\\[0.45em]
&\leqslant\frac{80{,}000^{2}}{\,80{,}000^{2}+400{,}000^{2}\,}\fallingdotseq0.03846
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(X\geqslant500{,}000)\\[.45em]
&=\mathbb{P}\bigl(X-\mathbb{E}(X)\geqslant500{,}000-\mathbb{E}(X)\bigr)\\[0.45em]
&\leqslant\frac{80{,}000^{2}}{\,80{,}000^{2}+400{,}000^{2}\,}\\[0.2em]
&\fallingdotseq0.03846
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這一個問題是一個很好的範例，說明了在計算機率的大致範圍時，如果我們知道更多的動差訊息，我們可以做出一個更好 (更精確) 的機率區間。

</div>

<div id="ex-poisson-chernoff-tail" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.43</div>

<div lang="en" markdown="1">
Suppose that $X$ has a Poisson distribution with parameter $\lambda$, and let $a$ be a positive integer with <span class="text-nowrap">$a>\lambda$.</span> Using the Chernoff inequality, show that

$$
\mathbb{P}(X\geqslant a)\leqslant\frac{\,e^{-\lambda}(e\,\lambda)^{a}\,}{a!}
$$

</div>

若 $X\sim\mathrm{Poi}(\lambda)$，則可知 $M_{\sssig X}(t)=e^{\lambda(e^{t}-1)}$，且對一切 $t\in\mathbb{R}$ 皆存在，[Theorem 2.35](/teaching-topics/probability-inequalities/#thm-chernoff) 中的 $h$ 因而可取任意正數。依照[車諾夫不等式](/teaching-topics/probability-inequalities/#thm-chernoff)可知

$$
\mathbb{P}(X\geqslant a)\leqslant e^{-ta}\,M_{\sssig X}(t),\quad\forall\,t>0
$$

此即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X\geqslant a)\leqslant\inf_{t>0}\,e^{-ta}\,M_{\sssig X}(t)=\inf_{t>0}\,e^{-ta}\,e^{\lambda(e^{t}-1)}=e^{-\lambda}\cdot\inf_{t>0}\,e^{\lambda e^{t}-ta}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X\geqslant a)&\leqslant\inf_{t>0}\,e^{-ta}\,M_{\sssig X}(t)\\[0.45em]
&=\inf_{t>0}\,e^{-ta}\,e^{\lambda(e^{t}-1)}\\[0.45em]
&=e^{-\lambda}\cdot\inf_{t>0}\,e^{\lambda e^{t}-ta}
\end{aligned}
$$

</div>

可令 $g(t)=e^{\lambda e^{t}-ta}$，$t>0$，則由一階條件可得

<div class="topic-math-follow-before" markdown="1">

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\frac{d}{\,d\,t\,}g(t)=e^{\lambda e^{t}-ta}\bigl(\lambda e^{t}-a\bigr)=0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\frac{d}{\,d\,t\,}g(t)=e^{\lambda e^{t}-ta}\bigl(\lambda e^{t}-a\bigr)=0
$$

</div>

</div>

又由二階條件可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\frac{d^{2}}{\,d\,t^{2}\,}g(t)\biggr\rvert_{t=t^{*}}&=\biggl[e^{\lambda e^{t}-ta}\bigl(\lambda e^{t}-a\bigr)^{2}+e^{\lambda e^{t}-ta}\,\lambda e^{t}\biggr]_{t=\ln\frac{a}{\,\lambda\,}}\\[0.45em]
&=e^{a}\Bigl(\frac{\,\lambda\,}{a}\Bigr)^{a}a>0
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\frac{d^{2}}{\,d\,t^{2}\,}g(t)\biggr\rvert_{t=t^{*}}\\[.45em]
&=\biggl[e^{\lambda e^{t}-ta}\bigl(\lambda e^{t}-a\bigr)^{2}+e^{\lambda e^{t}-ta}\,\lambda e^{t}\biggr]_{t=\ln\frac{a}{\,\lambda\,}}\\[0.45em]
&=e^{a}\Bigl(\frac{\,\lambda\,}{a}\Bigr)^{a}a>0
\end{aligned}
$$

</div>

此即 $g(t)$ 在 $t=\ln\frac{a}{\,\lambda\,}$ 具有最小值

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
g\Bigl(\ln\frac{a}{\,\lambda\,}\Bigr)=e^{a-a\ln(\frac{a}{\,\lambda\,})}=e^{a}\,e^{\ln(\frac{a}{\,\lambda\,})^{-a}}=\frac{\,(e\,\lambda)^{a}\,}{a^{a}}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
g\Bigl(\ln\frac{a}{\,\lambda\,}\Bigr)&=e^{a-a\ln(\frac{a}{\,\lambda\,})}\\[0.45em]
&=e^{a}\,e^{\ln(\frac{a}{\,\lambda\,})^{-a}}\\[.45em]
&=\frac{\,(e\,\lambda)^{a}\,}{a^{a}}
\end{aligned}
$$

</div>

則可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X\geqslant a)\leqslant e^{-\lambda}\cdot\inf_{t>0}\,e^{\lambda e^{t}-ta}=e^{-\lambda}\,\frac{\,(e\,\lambda)^{a}\,}{a^{a}}\leqslant\frac{\,e^{-\lambda}(e\,\lambda)^{a}\,}{a!}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X\geqslant a)&\leqslant e^{-\lambda}\cdot\inf_{t>0}\,e^{\lambda e^{t}-ta}\\[0.45em]
&=e^{-\lambda}\,\frac{\,(e\,\lambda)^{a}\,}{a^{a}}\\[.45em]
&\leqslant\frac{\,e^{-\lambda}(e\,\lambda)^{a}\,}{a!}
\end{aligned}
$$

</div>

原式得證。

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這題當中使用到了卜瓦松分配的 mgf，讀者在此可以先接受其結果，到後面的章節中再來探討為何卜瓦松分配的 mgf 如此；但事實上，讀者若已知卜瓦松分配的 pmf，亦可以自己計算其 mgf。此外，本題當中利用了 $a^{a}\geqslant a!$ 的結果，這也是證明過程中很常使用的一個性質，讀者不妨在理解後將其記起來。

</div>

## 本篇小結

八道例題演練的是同一系列不等式的各種用法。[Example 2.36](#ex-decreasing-density-bound) 與 [Example 2.37](#ex-decreasing-pmf-bound) 靠密度或機率函數本身的單調性創造出不等關係，一個用積分、一個用等差級數的和，想法與結論完全相同。[Example 2.38](#ex-general-markov-to-chebyshev) 由[非負函數的機率界限](/teaching-topics/probability-inequalities/#thm-nonnegative-function-bound)出發，取 $h(x)=(x-\mu_{\sssig X})^{2}$ 便導出[柴比雪夫不等式](/teaching-topics/probability-inequalities/#thm-chebyshev)，[Example 2.39](#ex-variance-lower-bound) 則反過來由兩個尾機率求變異數的下界。

[Example 2.40](#ex-chebyshev-sharpness) 說明同一個上界在 $\mathcal{U}(0,1)$ 之下離真實機率甚遠，在三點分配之下卻恰好相等，[Example 2.41](#ex-poisson-chebyshev) 示範[柴比雪夫不等式](/teaching-topics/probability-inequalities/#thm-chebyshev)在卜瓦松分配上的代入。[Example 2.42](#ex-household-income-bounds) 先以[馬可夫不等式](/teaching-topics/probability-inequalities/#thm-markov)只用[期望值](/teaching-topics/expectation/#def-expectation)求得一個上界，再以[單邊柴比雪夫不等式](/teaching-topics/probability-inequalities/#thm-one-tailed-chebyshev)加入[標準差](/teaching-topics/variance-standard-deviation/#def-standard-deviation)求得更小的上界，同一題的兩個小問正好對照出動差訊息愈多、機率上界愈精確。

[Example 2.43](#ex-poisson-chernoff-tail) 是[車諾夫不等式](/teaching-topics/probability-inequalities/#thm-chernoff)的完整示範。代入卜瓦松分配的 mgf 之後，以一階與二階條件求出使上界最小的 $t^{*}=\ln\frac{a}{\,\lambda\,}$，再由 $a^{a}\geqslant a!$ 得到 $\mathbb{P}(X\geqslant a)\leqslant\frac{\,e^{-\lambda}(e\,\lambda)^{a}\,}{a!}$。[下一篇](/teaching-topics/convexity-jensen-inequality/)轉向另一種不等式。它比較的不再是尾機率與動差，而是 $\mathbb{E}[g(X)]$ 與 $g[\mathbb{E}(X)]$ 的大小，[凸函數與凹函數](/teaching-topics/convexity-jensen-inequality/#def-convex-concave)的性質正是其中的關鍵。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Herman Chernoff. 1952. “A Measure of Asymptotic Efficiency for Tests of a Hypothesis Based on the Sum of Observations.” *The Annals of Mathematical Statistics* 23 (4): 493–507.
- Stéphane Boucheron, Gábor Lugosi, and Pascal Massart. 2013. *Concentration Inequalities: A Nonasymptotic Theory of Independence*. Oxford University Press.
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
