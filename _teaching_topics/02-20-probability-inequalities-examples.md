---
title: "機率不等式的例題"
subtitle: "Examples of Probability Inequalities"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 20
order: 220
permalink: /lecture-notes/probability-inequalities-examples/
date: 2026-08-06
published: true
excerpt: "本篇以八道例題演練各類機率不等式的推導與應用，比較不同動差條件下機率上界的鬆緊程度，並示範如何由車諾夫不等式極小化指數上界。"
---

[上一篇](/lecture-notes/probability-inequalities/)由一條以非負函數界定機率的定理出發，依序導出[馬可夫不等式](/lecture-notes/probability-inequalities/#thm-markov)、[柴比雪夫不等式](/lecture-notes/probability-inequalities/#thm-chebyshev)、[單邊柴比雪夫不等式](/lecture-notes/probability-inequalities/#thm-one-tailed-chebyshev)與[車諾夫不等式](/lecture-notes/probability-inequalities/#thm-chernoff)。五條不等式的形式各不相同，用上的動差訊息也有多有少，實際遇到一道題目時該挑哪一條、又該怎麼代入，仍要靠例題才看得清楚。

本篇以八道例題演練這一系列不等式的用法。前兩道不套現成的不等式，改由密度或機率函數本身的單調性造出不等關係；第三道由[非負函數的機率界限](/lecture-notes/probability-inequalities/#thm-nonnegative-function-bound)直接導出柴比雪夫不等式；其後三道分別由尾機率反求[變異數](/lecture-notes/variance/#def-variance)的下界、檢驗柴比雪夫上界的鬆緊，以及把柴比雪夫不等式代入卜瓦松分配；第七道以同一題的兩個小問對照馬可夫不等式與單邊柴比雪夫不等式；最後一道則是車諾夫不等式的完整示範。


<div id="ex-decreasing-density-bound" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.37</div>

<div lang="en" markdown="1">
Assume that $X$ is a positive continuous random variable having a non-increasing probability density function $f_{\sssig X}(x)$ for <span class="text-nowrap">$x>0$.</span> Show that

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

推導此類不等式的常用手法，是結合積分區間的縮減與被積函數的單調性來建立大小關係。本題先將 $(0,\infty)$ 上的積分縮小至子區間 <span class="text-nowrap">$(0,x)$，</span>再利用 $f\_{\sssig X}(t)$ 在 $(0,x)$ 上不小於端點值 $f\_{\sssig X}(x)$ 的非遞增性質將密度提出積分號外，從而導出目標上界。

</div>

<div id="ex-decreasing-pmf-bound" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.38</div>

<div lang="en" markdown="1">
Let $X$ be a positive-integer-valued random variable such that $\mathbb{P}(X=a)$ is a decreasing function of <span class="text-nowrap">$a$.</span> Prove that

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

本題為 [Example 2.37](#ex-decreasing-density-bound) 的離散對應版本。推導時先將無窮級數截斷至前 $a$ 項，再利用機率質量函數的遞減性質提出 <span class="text-nowrap">$\mathbb{P}(X=a)$，</span>搭配等差級數求和公式 $\sum_{n=1}^{a}n=\frac{a(a+1)}{2}\geqslant\frac{a^{2}}{2}$ 即得形式完全對稱的上界。

</div>

<div id="ex-general-markov-to-chebyshev" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.39</div>

<div lang="en" markdown="1">
Let $X$ be a random variable with $\mathbb{E}(X)=\mu_{\sssig X}$ and $\mathrm{Var}(X)=\sigma_{\sssig X}^{2}$, $h(x)$ be a non-negative real-valued function, and $c$ be a positive constant.

(1) Prove that
{: .topic-paren-item}

$$
\mathbb{P}\bigl(h(X)\geqslant c\bigr)\leqslant\frac{\,\mathbb{E}\bigl[h(X)\bigr]\,}{c}
$$

(2) Use the result in (1) to prove Chebyshev’s inequality
{: .topic-paren-item}

$$
\mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert\geqslant k\,\sigma_{\sssig X}\bigr)\leqslant\frac{1}{\,k^{2}\,}
$$

for any $k>0$, provided that <span class="text-nowrap">$\sigma_{\sssig X}>0$.</span>
{: .topic-paren-cont}

</div>

(1) 這一小題即 [Theorem 2.31](/lecture-notes/probability-inequalities/#thm-nonnegative-function-bound) 的敘述。我們在此以連續型為例證明，並令 $A=\lbrace\,x\mid h(x)\geqslant c\,\rbrace$，則
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
<div class="topic-box__label">Example 2.40</div>

<div lang="en" markdown="1">
Let $X$ be a random variable with $\mathbb{E}(X)=15$, $\mathbb{P}(X\geqslant20)=0.5$, and <span class="text-nowrap">$\mathbb{P}(X\leqslant10)=0.2$.</span> Find a lower bound for <span class="text-nowrap">$\mathrm{Var}(X)$.</span>
</div>

由題意可知 $\mathbb{E}(X)=15$、$\mathbb{P}(X\geqslant20)=0.5$ 與 $\mathbb{P}(X\leqslant10)=0.2$ 三項條件，故可得

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

又由[柴比雪夫不等式](/lecture-notes/probability-inequalities/#thm-chebyshev)可知

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
<div class="topic-box__label">Example 2.41</div>

<div lang="en" markdown="1">
Let $X$ be a random variable with mean $\mu_{\sssig X}$ and variance <span class="text-nowrap">$0<\sigma_{\sssig X}^{2}<\infty$.</span> Consider Chebyshev’s inequality

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

又[柴比雪夫不等式](/lecture-notes/probability-inequalities/#thm-chebyshev)提供之上界為
{: .topic-paren-cont}

$$
\mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert\geqslant\sqrt{3}\,\sigma_{\sssig X}\bigr)\leqslant\frac{1}{\,3\,}
$$

則可知[柴比雪夫不等式](/lecture-notes/probability-inequalities/#thm-chebyshev)可提供之機率上界，在此例中並不好。
{: .topic-paren-cont}

(2) 為使題目所給的 $\mathbb{P}(X=x)$ 滿足機率非負性 (即 $1-\frac{1}{\,k^{2}\,}\geqslant0$ 成立)，我們考慮 $k\geqslant1$ 的情形。由 $X$ 之分配可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\mathbb{E}(X)=-1\cdot\frac{1}{\,2k^{2}\,}+0\cdot\Bigl(1-\frac{1}{\,k^{2}\,}\Bigr)+1\cdot\frac{1}{\,2k^{2}\,}=0\\[0.7em]
\mathbb{E}(X^{2})=(-1)^{2}\cdot\frac{1}{\,2k^{2}\,}+0^{2}\cdot\Bigl(1-\frac{1}{\,k^{2}\,}\Bigr)+1^{2}\cdot\frac{1}{\,2k^{2}\,}=\frac{1}{\,k^{2}\,}
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=-1\cdot\frac{1}{\,2k^{2}\,}+0\cdot\Bigl(1-\frac{1}{\,k^{2}\,}\Bigr)+1\cdot\frac{1}{\,2k^{2}\,}\\[0.35em]
&=0
\end{aligned}
$$

$$
\begin{aligned}
\mathbb{E}(X^{2})&=(-1)^{2}\cdot\frac{1}{\,2k^{2}\,}+0^{2}\cdot\Bigl(1-\frac{1}{\,k^{2}\,}\Bigr)+1^{2}\cdot\frac{1}{\,2k^{2}\,}\\[0.35em]
&=\frac{1}{\,k^{2}\,}
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

又[柴比雪夫不等式](/lecture-notes/probability-inequalities/#thm-chebyshev)提供之上界為
{: .topic-paren-cont}

$$
\mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert\geqslant k\,\sigma_{\sssig X}\bigr)\leqslant\frac{1}{\,k^{2}\,}
$$

則可知[柴比雪夫不等式](/lecture-notes/probability-inequalities/#thm-chebyshev)可提供之機率上界，在此例中不可改進。
{: .topic-paren-cont}

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

評估機率不等式上界的鬆緊程度，關鍵在於比較上界與真實尾端機率的差距。第 (1) 小題針對 $\mathcal{U}(0,1)$ 取 <span class="text-nowrap">$k=\sqrt{3}$，</span>真實尾端機率已為 $0$ 而[柴比雪夫不等式](/lecture-notes/probability-inequalities/#thm-chebyshev)仍給出上界 <span class="text-nowrap">$\frac{1}{\,3\,}$，</span>顯示該界限在此分配下相當寬鬆；第 (2) 小題的三點對稱分配則對任意 $k\geqslant1$ 皆使真實尾端機率恰好等於上界 <span class="text-nowrap">$\frac{1}{\,k^{2}\,}$，</span>證實僅憑一、二階動差無法將此普適上界進一步壓低 (至於 $0<k<1$ 時，上界 $\frac{1}{\,k^{2}\,}>1$ 本不具實質約束力，且 $1-\frac{1}{\,k^{2}\,}<0$ 亦不構成合法的 pmf)。

</div>

<div id="ex-poisson-chebyshev" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.42</div>

<div lang="en" markdown="1">
Assume that a random variable $X$ follows a Poisson distribution with parameter <span class="text-nowrap">$\lambda$.</span> Using Chebyshev’s inequality, verify that

$$
\mathbb{P}\Bigl(X\leqslant\frac{\,\lambda\,}{2}\Bigr)\leqslant\frac{4}{\,\lambda\,}
$$

</div>

由 $X\sim\mathrm{Poi}(\lambda)$ 可知 $\mathbb{E}(X)=\mathrm{Var}(X)=\lambda$，則依[柴比雪夫不等式](/lecture-notes/probability-inequalities/#thm-chebyshev)可知

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
<div class="topic-box__label">Example 2.43</div>

<div lang="en" markdown="1">
Suppose that families in a certain area have an average income of <span class="text-nowrap">$100{,}000$.</span>

<ol class="topic-list-paren">
  <li>Find an upper bound for the fraction of those families whose income exceeds <span class="text-nowrap">$500{,}000$.</span></li>
  <li>Given in addition that the standard deviation of family income is <span class="text-nowrap">$80{,}000$,</span> find an upper bound smaller than the one obtained in (1).</li>
</ol>
</div>

(1) 令 $X$ 為該地區的家庭所得，則 $X$ 為非負[隨機變數](/lecture-notes/random-variables-and-pmf/#def-random-variable)，故由[馬可夫不等式](/lecture-notes/probability-inequalities/#thm-markov)可以得到下面的界限
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

(2) 若已知 $\sigma_{\sssig X}=80{,}000$，且 $500{,}000-\mathbb{E}(X)=400{,}000$，則可由[單邊柴比雪夫不等式 (坎特利不等式)](/lecture-notes/probability-inequalities/#thm-one-tailed-chebyshev)知
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

比較本題兩小題的結果，僅使用一階動差 (平均所得) 時，馬可夫不等式僅能給出 $0.2$ 的上界；一旦進一步納入二階動差 (標準差) 並改用單邊柴比雪夫不等式，同一尾端事件的上界即大幅收緊至約 <span class="text-nowrap">$0.03846$，</span>具體展現出掌握的動差資訊愈多、機率界限愈緊密的關係。

</div>

<div id="ex-poisson-chernoff-tail" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.44</div>

<div lang="en" markdown="1">
Let $X$ be a Poisson random variable with parameter $\lambda$, and let $a$ be a positive integer with <span class="text-nowrap">$a>\lambda$.</span> Using the Chernoff inequality, show that

$$
\mathbb{P}(X\geqslant a)\leqslant\frac{\,e^{-\lambda}(e\,\lambda)^{a}\,}{a!}
$$

</div>

若 $X\sim\mathrm{Poi}(\lambda)$，則可知 $M_{\sssig X}(t)=e^{\lambda(e^{t}-1)}$ 在所有實數 $t\in\mathbb{R}$ 上皆存在，[Theorem 2.35](/lecture-notes/probability-inequalities/#thm-chernoff) 中的 $h$ 因而可取任意正數。依照[車諾夫不等式](/lecture-notes/probability-inequalities/#thm-chernoff)可知

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

$$
\frac{d}{\,d\,t\,}g(t)=e^{\lambda e^{t}-ta}\bigl(\lambda e^{t}-a\bigr)=0
$$

</div>

<div class="topic-math-follow" markdown="1">

$$
\Longrightarrow\ t^{*}=\ln\frac{a}{\,\lambda\,}
$$

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

本題直接引用了卜瓦松分配的動差母函數 <span class="text-nowrap">$M_{\sssig X}(t)=e^{\lambda(e^{t}-1)}$，</span>其推導將於後續機率模型章節詳述 (亦可直接由其 pmf 搭配指數函數的泰勒級數求得)。此外，最後一步利用了正整數的不等式 <span class="text-nowrap">$a^{a}\geqslant a!$；</span>因 $a^{a}$ 與 $a!$ 皆為 $a$ 個正整數相乘，且逐項滿足 $a\geqslant k$ (<span class="text-nowrap">$k=1,2,\ldots,a$</span>)，故分母由 $a^{a}$ 換為 $a!$ 後不等號方向維持不變。

</div>

## 本篇小結

八道例題演練的是同一系列不等式的各種用法。[Example 2.37](#ex-decreasing-density-bound) 與 [Example 2.38](#ex-decreasing-pmf-bound) 靠密度或機率函數本身的單調性創造出不等關係，一個用積分、一個用等差級數的和，想法與結論完全相同。[Example 2.39](#ex-general-markov-to-chebyshev) 由[非負函數的機率界限](/lecture-notes/probability-inequalities/#thm-nonnegative-function-bound)出發，取 $h(x)=(x-\mu_{\sssig X})^{2}$ 便導出[柴比雪夫不等式](/lecture-notes/probability-inequalities/#thm-chebyshev)，[Example 2.40](#ex-variance-lower-bound) 則反過來由兩個尾機率求變異數的下界。

[Example 2.41](#ex-chebyshev-sharpness) 說明同一個上界在 $\mathcal{U}(0,1)$ 之下離真實機率甚遠，在三點分配之下卻恰好相等，[Example 2.42](#ex-poisson-chebyshev) 示範[柴比雪夫不等式](/lecture-notes/probability-inequalities/#thm-chebyshev)在卜瓦松分配上的代入。[Example 2.43](#ex-household-income-bounds) 先以[馬可夫不等式](/lecture-notes/probability-inequalities/#thm-markov)只用[期望值](/lecture-notes/expectation/#def-expectation)求得一個上界，再以[單邊柴比雪夫不等式](/lecture-notes/probability-inequalities/#thm-one-tailed-chebyshev)加入[標準差](/lecture-notes/variance-standard-deviation/#def-standard-deviation)求得更小的上界，同一題的兩個小問正好對照出動差訊息愈多、機率上界愈精確。

[Example 2.44](#ex-poisson-chernoff-tail) 是[車諾夫不等式](/lecture-notes/probability-inequalities/#thm-chernoff)的完整示範。代入卜瓦松分配的 mgf 之後，以一階與二階條件求出使上界最小的 $t^{*}=\ln\frac{a}{\,\lambda\,}$，再由 $a^{a}\geqslant a!$ 得到 $\mathbb{P}(X\geqslant a)\leqslant\frac{\,e^{-\lambda}(e\,\lambda)^{a}\,}{a!}$。[下一篇](/lecture-notes/convexity-jensen-inequality/)轉向另一種不等式。它比較的不再是尾機率與動差，而是 $\mathbb{E}[g(X)]$ 與 $g[\mathbb{E}(X)]$ 兩者的大小，[凸函數與凹函數](/lecture-notes/convexity-jensen-inequality/#def-convex-concave)的幾何性質正是其中的關鍵。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Herman Chernoff. 1952. “A Measure of Asymptotic Efficiency for Tests of a Hypothesis Based on the Sum of Observations.” *The Annals of Mathematical Statistics* 23 (4): 493–507.
- Stéphane Boucheron, Gábor Lugosi, and Pascal Massart. 2013. *Concentration Inequalities: A Nonasymptotic Theory of Independence*. Oxford University Press.
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
