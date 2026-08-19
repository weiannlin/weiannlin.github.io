---
title: "史拉斯基定理與 Delta 法"
subtitle: "Slutsky's Theorem and the Delta Method"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 5
topic: 8
order: 508
permalink: /teaching-topics/slutsky-and-delta-method/
date: 2026-08-15
published: false
excerpt: "上一篇的定理都是為機率收斂而生的，本篇把其中一個序列改為分配收斂，得到史拉斯基定理: 若 $X_n\\pconv c$ 且 $Y_n\\dconv W$，則和、積與商仍然分配收斂，極限分別為 $c+W$、$cW$ 與 $\\frac{W}{c}$。三道例題依序處理兩組樣本的比值、標準常態樣本的比值，以及 $t$ 統計量分配收斂至標準常態這件事，並由最後一題得知自由度趨於無窮時 $t$ 分配的極限分配就是標準常態分配。其後給出 Delta 法，把 $\\sqrt{n}\\,(X_n-\\theta)$ 的極限分配推廣到 $\\sqrt{n}\\,[g(X_n)-g(\\theta)]$，變異數多乘一個 $[g^{\\prime}(\\theta)]^{2}$。四道例題分別取 $g(x)=x^{2}$、$g(x)=e^{x}$、$g(x)=\\frac{x-1}{x^{2}}$ 與 $g(x)=\\sqrt{x}$，用來求樣本平均數平方、均勻樣本乘積、幾何母體樣本與卡方變數平方根的極限分配。"
---

[上一篇](/teaching-topics/continuous-mapping-theorem/)給出[機率收斂的運算性質與連續映射定理](/teaching-topics/continuous-mapping-theorem/#thm-pconv-related)，其中每一條的前提都是[機率收斂](/teaching-topics/convergence-in-probability/#def-converge-in-probability)。本篇把其中一個序列的前提換成[分配收斂](/teaching-topics/convergence-in-distribution/#def-converge-in-distribution)，這些運算性質的結論會隨之改變。

本篇有兩個定理。第一個是史拉斯基定理，處理的是一個序列機率收斂到常數、另一個序列分配收斂到隨機變數時，兩者的和、積與商各自收斂到什麼；三道例題依序求兩組樣本的比值、標準常態樣本的比值，以及 $t$ 統計量的極限分配。第二個是 Delta 法，處理的是一般化的函數轉換: 已知 $\sqrt{n}\,(X_n-\theta)$ 的極限分配，要求 $\sqrt{n}\,[g(X_n)-g(\theta)]$ 的極限分配；四道例題分別取平方、指數、有理函數與平方根四種 $g$ 來演練。

## 史拉斯基定理

前述定理包含連續映射定理在內，主要是針對機率收斂而生的定理，然而，如果同時考慮了分配收斂，則這些收斂的結果將稍有變化，而這個結果，正是鼎鼎大名的**史拉斯基定理 <span lang="en">(Slutsky's theorem)</span>**，見下列敘述。

<div id="thm-slutsky" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 5.11 (史拉斯基定理, Slutsky's theorem)</div>

若 $X_n\pconv c$ 且 <span class="text-nowrap">$Y_n\dconv W$，</span>其中 $c$ 為常數、$W$ 為隨機變數，則我們有

(1)
{: .topic-paren-item}

$$
X_n+Y_n\dconv c+W
$$

(2)
{: .topic-paren-item}

$$
X_nY_n\dconv cW
$$

(3)
{: .topic-paren-item}

$$
\frac{Y_n}{X_n}\dconv\frac{\,W\,}{c}
$$

其中 $c\neq0$。
{: .topic-paren-cont}

</div>

<div id="ex-slutsky-uniform-ratio" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.30</div>

<div lang="en" markdown="1">
Suppose that $X_1,\ldots,X_n$ is a random sample drawn from the uniform distribution $\mathcal{U}(0,\ 1)$, and that $Y_1,\ldots,Y_n$ is a random sample drawn from an unspecified distribution for which $\mathbb{E}(Y_1)=0$ and $\mathrm{Var}(Y_1)=1$. Put

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
Z_n=\frac{X_1+X_2+\cdots+X_n}{X_1^{2}+X_2^{2}+\cdots+X_n^{2}},\qquad W_n=\frac{\sqrt{n}\,(Y_1+Y_2+\cdots+Y_n)}{X_1^{2}+X_2^{2}+\cdots+X_n^{2}}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
Z_n&=\frac{X_1+X_2+\cdots+X_n}{X_1^{2}+X_2^{2}+\cdots+X_n^{2}},\\[0.45em]
W_n&=\frac{\sqrt{n}\,(Y_1+Y_2+\cdots+Y_n)}{X_1^{2}+X_2^{2}+\cdots+X_n^{2}}
\end{aligned}
$$

</div>

<ol class="topic-list-paren">
  <li>Suppose that $Z_n$ converges in probability to a constant $c$. Determine the value of $c$.</li>
  <li>Find the limiting distribution of $W_n$.</li>
</ol>
</div>

(1) 由於 <span class="text-nowrap">$X_1,\ldots,X_n\iidto\mathcal{U}(0,\ 1)$，</span>由[均勻分配](/teaching-topics/uniform-distribution-integral-transform/#def-uniform-distribution)的期望值與變異數可得
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(X_i)=\frac{\,1\,}{2},\quad\mathrm{Var}(X_i)=\frac{\,1\,}{12},\quad\mathbb{E}(X_i^{2})=\Bigl(\frac{1}{\,2\,}\Bigr)^{2}+\frac{\,1\,}{12}=\frac{1}{\,3\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X_i)&=\frac{\,1\,}{2},\quad\mathrm{Var}(X_i)=\frac{\,1\,}{12},\\[0.45em]
\mathbb{E}(X_i^{2})&=\Bigl(\frac{1}{\,2\,}\Bigr)^{2}+\frac{\,1\,}{12}=\frac{1}{\,3\,}
\end{aligned}
$$

</div>

由[弱大數法則](/teaching-topics/weak-law-and-central-limit-theorem/#thm-weak-law-of-large-numbers)可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\frac{\,1\,}{n}\sum_{i=1}^{n}X_i\pconv\mathbb{E}(X_i)=\frac{\,1\,}{2},\quad\frac{\,1\,}{n}\sum_{i=1}^{n}X_i^{2}\pconv\mathbb{E}(X^{2})=\frac{1}{\,3\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\frac{\,1\,}{n}\sum_{i=1}^{n}X_i&\pconv\mathbb{E}(X_i)=\frac{\,1\,}{2},\\[0.45em]
\frac{\,1\,}{n}\sum_{i=1}^{n}X_i^{2}&\pconv\mathbb{E}(X^{2})=\frac{1}{\,3\,}
\end{aligned}
$$

</div>

故所求為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
Z_n=\frac{\sum_{i=1}^{n}X_i}{\sum_{i=1}^{n}X_i^{2}}=\frac{\,\sum_{i=1}^{n}X_i/n\,}{\sum_{i=1}^{n}X_i^{2}/n}\pconv\frac{\,1/2\,}{1/3}=\frac{\,3\,}{2}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
Z_n&=\frac{\sum_{i=1}^{n}X_i}{\sum_{i=1}^{n}X_i^{2}}=\frac{\,\sum_{i=1}^{n}X_i/n\,}{\sum_{i=1}^{n}X_i^{2}/n}\\[0.45em]
&\pconv\frac{\,1/2\,}{1/3}=\frac{\,3\,}{2}
\end{aligned}
$$

</div>

(2) 由於 <span class="text-nowrap">$Y_1,\ldots,Y_n\iidto(0,\ 1)$，</span>由[中央極限定理](/teaching-topics/weak-law-and-central-limit-theorem/#thm-central-limit-theorem)可知
{: .topic-paren-item}

$$
\frac{\,\sqrt{n}\,(\overline{Y}-0)\,}{1}=\sqrt{n}\,\overline{Y}\dconv Z\sim\mathcal{N}(0,\ 1)
$$

又由弱大數法則可知
{: .topic-paren-cont}

$$
\frac{\,1\,}{n}\sum_{i=1}^{n}X_i^{2}\pconv\mathbb{E}(X^{2})=\frac{1}{\,3\,}
$$

則由史拉斯基定理，我們有
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
W_n&=\frac{\sqrt{n}\,\sum_{i=1}^{n}Y_i}{\sum_{i=1}^{n}X_i^{2}}=\frac{\,\sqrt{n}\,\bigl(\sum_{i=1}^{n}Y_i/n\bigr)\,}{\sum_{i=1}^{n}X_i^{2}/n}=\frac{\,\sqrt{n}\,\overline{Y}\,}{\,\sum_{i=1}^{n}X_i^{2}/n\,}\\[0.45em]
&\dconv\frac{\,Z\,}{\,1/3\,}=3Z\sim\mathcal{N}(0,\ 9)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
W_n&=\frac{\sqrt{n}\,\sum_{i=1}^{n}Y_i}{\sum_{i=1}^{n}X_i^{2}}\\[0.45em]
&=\frac{\,\sqrt{n}\,\bigl(\sum_{i=1}^{n}Y_i/n\bigr)\,}{\sum_{i=1}^{n}X_i^{2}/n}\\[0.45em]
&=\frac{\,\sqrt{n}\,\overline{Y}\,}{\,\sum_{i=1}^{n}X_i^{2}/n\,}\\[0.45em]
&\dconv\frac{\,Z\,}{\,1/3\,}=3Z\sim\mathcal{N}(0,\ 9)
\end{aligned}
$$

</div>

</div>

<div id="ex-slutsky-normal-ratio" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.31</div>

<div lang="en" markdown="1">
Suppose that $X_1,\ldots,X_n$ are iid $\mathcal{N}(0,\ 1)$ random variables, where <span class="text-nowrap">$n\geqslant1$,</span> and put

$$
U_n=\frac{\sqrt{n}\,(X_1+X_2+\cdots+X_n)}{X_1^{2}+X_2^{2}+\cdots+X_n^{2}}
$$

Show that the limiting distribution of $U_n$ is the standard normal distribution.
</div>

由中央極限定理可知

$$
\frac{\,\sqrt{n}\,(\overline{X}-0)\,}{1}=\sqrt{n}\,\overline{X}\dconv Z\sim\mathcal{N}(0,\ 1)
$$

又由弱大數法則可知

$$
\frac{1}{\,n\,}\sum_{i=1}^{n}X_i^{2}\pconv\mathbb{E}(X_i^{2})=1
$$

故由史拉斯基定理可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
U_n&=\frac{\sqrt{n}\,(X_1+X_2+\cdots+X_n)}{X_1^{2}+X_2^{2}+\cdots+X_n^{2}}=\frac{\,\sqrt{n}\,(X_1+X_2+\cdots+X_n)/n\,}{(X_1^{2}+X_2^{2}+\cdots+X_n^{2})/n}\\[0.45em]
&\dconv\frac{\,Z\,}{1}\sim\mathcal{N}(0,\ 1)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
U_n&=\frac{\sqrt{n}\,(X_1+X_2+\cdots+X_n)}{X_1^{2}+X_2^{2}+\cdots+X_n^{2}}\\[0.45em]
&=\frac{\,\sqrt{n}\,(X_1+X_2+\cdots+X_n)/n\,}{(X_1^{2}+X_2^{2}+\cdots+X_n^{2})/n}\\[0.45em]
&\dconv\frac{\,Z\,}{1}\sim\mathcal{N}(0,\ 1)
\end{aligned}
$$

</div>

</div>

<div id="ex-t-statistic-to-standard-normal" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.32</div>

<div lang="en" markdown="1">
Suppose that $X_1,\ldots,X_n$ is a random sample taken from a normal distribution whose mean is $\mu$ and whose variance $\sigma^{2}$ is finite, and put

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\overline{X}=\frac{1}{\,n\,}\sum_{i=1}^{n}X_i,\qquad S_n^{2}=\frac{1}{\,n-1\,}\sum_{i=1}^{n}(X_i-\overline{X})^{2}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\overline{X}&=\frac{1}{\,n\,}\sum_{i=1}^{n}X_i,\\[0.45em]
S_n^{2}&=\frac{1}{\,n-1\,}\sum_{i=1}^{n}(X_i-\overline{X})^{2}
\end{aligned}
$$

</div>

Show that $T=\frac{\,\overline{X}-\mu\,}{S_n/\sqrt{n}}$ converges in distribution to <span class="text-nowrap">$\mathcal{N}(0,\ 1)$.</span>
</div>

令

$$
Z=\frac{\,\overline{X}-\mu\,}{\frac{\sigma}{\sqrt{n}}}
$$

則由[常態分配的線性組合可加性](/teaching-topics/normal-distribution/#prop-normal-linear-combination)可知，不論 $n$ 多大，我們都有

$$
Z\sim\mathcal{N}(0,\ 1)
$$

又由於 <span class="text-nowrap">$S_n^{2}\pconv\sigma^{2}$，</span>由連續映射定理可知

$$
\frac{\sigma^{2}}{\,S_n^{2}\,}\pconv1
$$

且可令 $g(x)=\sqrt{x}$ 在 $x>0$ 上連續，則

$$
g\Bigl(\frac{\sigma^{2}}{\,S_n^{2}\,}\Bigr)=\sqrt{\frac{\,\sigma^{2}\,}{\,S_n^{2}\,}}\pconv g(1)=1
$$

則由史拉斯基定理，可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
T=\frac{\,\overline{X}-\mu\,}{\frac{S_n}{\sqrt{n}}}=\sqrt{\frac{\sigma^{2}}{\,S_n^{2}\,}}\times\frac{\,\overline{X}-\mu\,}{\frac{\sigma}{\sqrt{n}}}\dconv1\times Z\sim\mathcal{N}(0,\ 1)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
T&=\frac{\,\overline{X}-\mu\,}{\frac{S_n}{\sqrt{n}}}=\sqrt{\frac{\sigma^{2}}{\,S_n^{2}\,}}\times\frac{\,\overline{X}-\mu\,}{\frac{\sigma}{\sqrt{n}}}\\[0.45em]
&\dconv1\times Z\sim\mathcal{N}(0,\ 1)
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

上面這一題說明了一個很重要的事實，也就是當自由度趨近無窮大時，[司徒頓 $t$ 分配](/teaching-topics/student-t-distribution/#def-t-distribution)將會分配收斂至標準常態分配，也就是指，若 <span class="text-nowrap">$T_n\sim t(n)$，</span>則 $T_n$ 之極限分配就是標準常態分配。

</div>

讀者應該會發現，相較於 [Theorem 5.10](/teaching-topics/continuous-mapping-theorem/#thm-pconv-related)，將其中一個序列的收斂改為分配收斂至某個隨機變數後，史拉斯基定理的結果，原則上與 Theorem 5.10 的內容相呼應，只是其結果由機率收斂改為分配收斂。

然而，這個結果獨漏了一般化的函數轉換，那麼，一般化的函數轉換，其分配收斂的狀況又如何呢? 這個問題的結果，是馬上將要談到的 **Delta 法 (Delta method)**。

## Delta 法

<div id="thm-delta-method" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 5.12 (Delta 法, Delta method)</div>

若隨機數列 $\lbrace X_n\rbrace_{n=1}^{\infty}$ 具有極限分配

$$
\sqrt{n}\,(X_n-\theta)\dconv W\sim\mathcal{N}(0,\ \sigma^{2})
$$

則我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\sqrt{n}\,\bigl[g(X_n)-g(\theta)\bigr]\dconv g^{\prime}(\theta)\,W\sim\mathcal{N}\bigl(0,\ [g^{\prime}(\theta)]^{2}\sigma^{2}\bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\sqrt{n}\,\bigl[g(X_n)-g(\theta)\bigr]&\dconv g^{\prime}(\theta)\,W\\[0.45em]
&\sim\mathcal{N}\bigl(0,\ [g^{\prime}(\theta)]^{2}\sigma^{2}\bigr)
\end{aligned}
$$

</div>

其中 $g(\cdot)$ 為任意連續函數，$g^{\prime}(\theta)\neq0$ 且存在。

</div>

<div class="topic-proof" markdown="1">
**Proof.**

先說明 $X_n$ 本身機率收斂至 $\theta$。由於

$$
X_n-\theta=\frac{1}{\sqrt{n}}\times\sqrt{n}\,(X_n-\theta)
$$

其中 $\frac{1}{\sqrt{n}}$ 是一個收斂至 $0$ 的常數序列，而 $\sqrt{n}\,(X_n-\theta)\dconv W$，故由 [Theorem 5.11](#thm-slutsky) 的第 (2) 款可得

$$
X_n-\theta\dconv0\times W\equiv0
$$

收斂的對象是一個常數，故由 [Theorem 5.3](/teaching-topics/convergence-in-probability/#thm-pconv-iff-dconv) 可知

$$
X_n\pconv\theta
$$

接著處理泰勒展開的餘項。由於 $g$ 在 $\theta$ 上可微，令

$$
h(x)=\frac{\,g(x)-g(\theta)\,}{x-\theta}-g^{\prime}(\theta),\ x\neq\theta
$$

並補上 $h(\theta)=0$，則 $h$ 在 $\theta$ 上連續，且對每一個 $x$ 皆有

$$
g(x)-g(\theta)=\bigl[g^{\prime}(\theta)+h(x)\bigr](x-\theta)
$$

把 $x$ 換成 $X_n$ 並在兩側同乘 $\sqrt{n}$，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\sqrt{n}\,\bigl[g(X_n)-g(\theta)\bigr]=g^{\prime}(\theta)\,\sqrt{n}\,(X_n-\theta)+h(X_n)\,\sqrt{n}\,(X_n-\theta)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\sqrt{n}\,\bigl[g(X_n)-g(\theta)\bigr]\\[0.45em]
&=g^{\prime}(\theta)\,\sqrt{n}\,(X_n-\theta)\\[0.45em]
&\qquad+h(X_n)\,\sqrt{n}\,(X_n-\theta)
\end{aligned}
$$

</div>

右側第一項把非零常數 $g^{\prime}(\theta)$ 看成一個機率收斂至自身的常數序列，由 [Theorem 5.11](#thm-slutsky) 的第 (2) 款可得

$$
g^{\prime}(\theta)\,\sqrt{n}\,(X_n-\theta)\dconv g^{\prime}(\theta)\,W
$$

右側第二項則由 $h$ 在 $\theta$ 上連續與 $X_n\pconv\theta$，依 [Theorem 5.10](/teaching-topics/continuous-mapping-theorem/#thm-pconv-related) 的連續映射定理可得

$$
h(X_n)\pconv h(\theta)=0
$$

再由 [Theorem 5.11](#thm-slutsky) 的第 (2) 款與 [Theorem 5.3](/teaching-topics/convergence-in-probability/#thm-pconv-iff-dconv) 可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
h(X_n)\,\sqrt{n}\,(X_n-\theta)\dconv0\times W\equiv0,\quad\text{也就是}\quad h(X_n)\,\sqrt{n}\,(X_n-\theta)\pconv0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
h(X_n)\,\sqrt{n}\,(X_n-\theta)&\dconv0\times W\equiv0,\\[0.45em]
\text{也就是}\quad h(X_n)\,\sqrt{n}\,(X_n-\theta)&\pconv0
\end{aligned}
$$

</div>

最後把機率收斂至 $0$ 的第二項與分配收斂至 $g^{\prime}(\theta)\,W$ 的第一項相加，由 [Theorem 5.11](#thm-slutsky) 的第 (1) 款可得

$$
\sqrt{n}\,\bigl[g(X_n)-g(\theta)\bigr]\dconv g^{\prime}(\theta)\,W
$$

又由常態分配的線性組合可加性，$W\sim\mathcal{N}(0,\ \sigma^{2})$ 乘上非零常數 $g^{\prime}(\theta)$ 之後仍為常態分配，此即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\sqrt{n}\,\bigl[g(X_n)-g(\theta)\bigr]\dconv g^{\prime}(\theta)\,W\sim\mathcal{N}\bigl(0,\ [g^{\prime}(\theta)]^{2}\sigma^{2}\bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\sqrt{n}\,\bigl[g(X_n)-g(\theta)\bigr]&\dconv g^{\prime}(\theta)\,W\\[0.45em]
&\sim\mathcal{N}\bigl(0,\ [g^{\prime}(\theta)]^{2}\sigma^{2}\bigr)
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

本證明的作法取自 Casella and Berger (2002) 第 240 至 243 頁。

<div id="ex-delta-method-squared-mean" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.33</div>

<div lang="en" markdown="1">
Suppose that $\overline{X}_n$ is the sample mean of a random sample of size $n$ taken from a distribution whose mean is $\mu$ and whose variance is <span class="text-nowrap">$\sigma^{2}$.</span> Find the limiting distribution of <span class="text-nowrap">$n^{1/2}\bigl(\overline{X}_n^{2}-\mu^{2}\bigr)$.</span>
</div>

由中央極限定理知

$$
\sqrt{n}\,(\overline{X}_n-\mu)\dconv W\sim\mathcal{N}(0,\ \sigma^{2})
$$

取 <span class="text-nowrap">$g(x)=x^{2}$，</span>則 <span class="text-nowrap">$g^{\prime}(\mu)=2\mu$，</span>由 Delta 法知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\sqrt{n}\,\bigl[g(\overline{X}_n)-g(\mu)\bigr]\dconv g^{\prime}(\mu)\,W\sim\mathcal{N}\bigl(0,\ [g^{\prime}(\mu)]^{2}\sigma^{2}\bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\sqrt{n}\,\bigl[g(\overline{X}_n)-g(\mu)\bigr]&\dconv g^{\prime}(\mu)\,W\\[0.45em]
&\sim\mathcal{N}\bigl(0,\ [g^{\prime}(\mu)]^{2}\sigma^{2}\bigr)
\end{aligned}
$$

</div>

此即

$$
\sqrt{n}\,\bigl(\overline{X}_n^{2}-\mu^{2}\bigr)\dconv Y\sim\mathcal{N}(0,\ 4\mu^{2}\sigma^{2})
$$

</div>

<div id="ex-delta-method-product-of-uniforms" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.34</div>

<div lang="en" markdown="1">
Suppose that $X_1,X_2,\ldots,X_n$ are iid random variables having the uniform distribution on <span class="text-nowrap">$(0,\ 1)$,</span> and put <span class="text-nowrap">$Y_n=\bigl(\prod_{i=1}^{n}X_i\bigr)^{-\frac{1}{n}}$.</span> Show that $\sqrt{n}\,(Y_n-e)$ converges in distribution to <span class="text-nowrap">$\mathcal{N}(0,\ e^{2})$.</span>
</div>

令 <span class="text-nowrap">$W_i=-\ln X_i$，</span>則由 [cdf 法](/teaching-topics/one-to-one-transformations/#prop-cdf-method)可得

$$
\begin{aligned}
F_{\sssig W}(w)&=\mathbb{P}(W\leqslant w)=\mathbb{P}(-\ln X\leqslant w)=\mathbb{P}(X\geqslant e^{-w})\\[0.45em]
&=1-\mathbb{P}(X<e^{-w})=1-e^{-w},\ w>0
\end{aligned}
$$

此即

$$
W_i\iidto\mathrm{Exp}(\beta=1),\ i=1,\ldots,n
$$

也就是說 $W_i$ 服從[指數分配](/teaching-topics/gamma-function-exponential-distribution/#def-exponential-distribution)。則由中央極限定理可知

$$
\sqrt{n}\,(\overline{W}-1)\dconv Z\sim\mathcal{N}(0,\ 1)
$$

取 <span class="text-nowrap">$g(x)=e^{x}$，</span>則 <span class="text-nowrap">$g^{\prime}(1)=e^{1}=e$，</span>由 Delta 法知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\sqrt{n}\,(Y_n-e)=\sqrt{n}\,\bigl[g(\overline{W})-g(1)\bigr]\dconv g^{\prime}(1)\,Z\sim\mathcal{N}\bigl(0,\ [g^{\prime}(1)]^{2}\bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\sqrt{n}\,(Y_n-e)&=\sqrt{n}\,\bigl[g(\overline{W})-g(1)\bigr]\\[0.45em]
&\dconv g^{\prime}(1)\,Z\sim\mathcal{N}\bigl(0,\ [g^{\prime}(1)]^{2}\bigr)
\end{aligned}
$$

</div>

此即

$$
\sqrt{n}\,(Y_n-e)\dconv Y\sim\mathcal{N}(0,\ e^{2})
$$

</div>

<div id="ex-delta-method-geometric-distribution" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.35</div>

<div lang="en" markdown="1">
Suppose that a random sample of size $n$ is taken from a population whose probability function is

$$
f(x)=(1-p)^{x-1}\,p,\ 0<p<1,\ x=1,2,3,\ldots
$$

Determine the asymptotic distribution of <span class="text-nowrap">$\frac{\,\overline{X}_n-1\,}{\overline{X}_n^{2}}$.</span>
</div>

由題意可知樣本抽自[幾何分配](/teaching-topics/geometric-distribution-memoryless/#def-geometric)，也就是

$$
X_1,\ldots,X_n\iidto\mathrm{Geo}(p),\ x=1,2,3,\ldots
$$

故可得

$$
\mathbb{E}(X_i)=\frac{1}{\,p\,},\quad\mathrm{Var}(X_i)=\frac{\,1-p\,}{p^{2}}
$$

由中央極限定理知道

$$
\sqrt{n}\Bigl(\overline{X}_n-\frac{1}{\,p\,}\Bigr)\dconv V\sim\mathcal{N}\Bigl(0,\ \frac{\,1-p\,}{p^{2}}\Bigr)
$$

令 <span class="text-nowrap">$g(x)=\frac{\,x-1\,}{x^{2}},\ x>0$，</span>則

$$
g^{\prime}(x)=\frac{\,-1\,}{x^{2}}+\frac{2}{\,x^{3}\,},\ x>0
$$

由 Delta 法可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\sqrt{n}\Bigl[g(\overline{X}_n)-g\Bigl(\frac{1}{\,p\,}\Bigr)\Bigr]\dconv W\sim\mathcal{N}\biggl(0,\ \Bigl[g^{\prime}\Bigl(\frac{1}{\,p\,}\Bigr)\Bigr]^{2}\frac{\,1-p\,}{p^{2}}\biggr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\sqrt{n}\Bigl[g(\overline{X}_n)-g\Bigl(\frac{1}{\,p\,}\Bigr)\Bigr]&\dconv W\\[0.45em]
&\sim\mathcal{N}\biggl(0,\ \Bigl[g^{\prime}\Bigl(\frac{1}{\,p\,}\Bigr)\Bigr]^{2}\frac{\,1-p\,}{p^{2}}\biggr)
\end{aligned}
$$

</div>

其中

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
g(\overline{X}_n)=\frac{\,\overline{X}_n-1\,}{\overline{X}_n^{2}},\quad g\Bigl(\frac{1}{\,p\,}\Bigr)=\frac{\,\frac{1}{p}-1\,}{\bigl(\frac{1}{p}\bigr)^{2}}=p(1-p),\quad\Bigl[g^{\prime}\Bigl(\frac{1}{\,p\,}\Bigr)\Bigr]^{2}=p^{4}(1-2p)^{2}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
g(\overline{X}_n)&=\frac{\,\overline{X}_n-1\,}{\overline{X}_n^{2}},\\[0.45em]
g\Bigl(\frac{1}{\,p\,}\Bigr)&=\frac{\,\frac{1}{p}-1\,}{\bigl(\frac{1}{p}\bigr)^{2}}=p(1-p),\\[0.45em]
\Bigl[g^{\prime}\Bigl(\frac{1}{\,p\,}\Bigr)\Bigr]^{2}&=p^{4}(1-2p)^{2}
\end{aligned}
$$

</div>

故知道

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\sqrt{n}\biggl[\frac{\,\overline{X}_n-1\,}{\overline{X}_n^{2}}-p(1-p)\biggr]\dconv W\sim\mathcal{N}\bigl(0,\ p^{2}(1-2p)^{2}(1-p)\bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\sqrt{n}\biggl[\frac{\,\overline{X}_n-1\,}{\overline{X}_n^{2}}-p(1-p)\biggr]&\dconv W\\[0.45em]
&\sim\mathcal{N}\bigl(0,\ p^{2}(1-2p)^{2}(1-p)\bigr)
\end{aligned}
$$

</div>

在 $n$ 足夠大但仍有限時，我們有 $\frac{\,\overline{X}_n-1\,}{\overline{X}_n^{2}}$ 的**漸近分配 <span lang="en">(asymptotic distribution)</span>**

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\frac{\,\overline{X}_n-1\,}{\overline{X}_n^{2}}\aconv\mathcal{N}\biggl(p(1-p),\ \frac{\,p^{2}(1-2p)^{2}(1-p)\,}{n}\biggr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\frac{\,\overline{X}_n-1\,}{\overline{X}_n^{2}}&\aconv\mathcal{N}\biggl(p(1-p),\\[0.45em]
&\qquad\qquad\frac{\,p^{2}(1-2p)^{2}(1-p)\,}{n}\biggr)
\end{aligned}
$$

</div>

</div>

<div id="ex-delta-method-chi-square-root" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.36</div>

<div lang="en" markdown="1">
Suppose that the random variable $Y$ has a chi-squared distribution with $n$ degrees of freedom. Find the limiting distribution of <span class="text-nowrap">$\sqrt{Y}-\sqrt{n}$.</span>
</div>

由[卡方分配](/teaching-topics/chi-squared-distribution/#def-chi-distribution)的可加性，可令

$$
Y=\sum_{i=1}^{n}X_i
$$

其中

$$
\lbrace X_i\rbrace_{i=1}^{n}\iidto\chi^{2}(\nu=1),\ i=1,\ldots,n
$$

則由中央極限定理可知

$$
\sqrt{n}\,(\overline{X}-1)\dconv W\sim\mathcal{N}(0,\ 2)
$$

取 <span class="text-nowrap">$g(x)=\sqrt{x}$，</span>則 <span class="text-nowrap">$g^{\prime}(1)=\frac{1}{\,2\,}$，</span>由 Delta 法知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\sqrt{n}\,\bigl(\sqrt{\overline{X}}-\sqrt{1}\bigr)=\sqrt{n}\,\bigl[g(\overline{X})-g(1)\bigr]\dconv g^{\prime}(1)\,W\sim\mathcal{N}\bigl(0,\ [g^{\prime}(1)]^{2}\times2\bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\sqrt{n}\,\bigl(\sqrt{\overline{X}}-\sqrt{1}\bigr)&=\sqrt{n}\,\bigl[g(\overline{X})-g(1)\bigr]\\[0.45em]
&\dconv g^{\prime}(1)\,W\sim\mathcal{N}\bigl(0,\ [g^{\prime}(1)]^{2}\times2\bigr)
\end{aligned}
$$

</div>

此即

$$
\sqrt{Y}-\sqrt{n}\dconv V\sim\mathcal{N}\Bigl(0,\ \frac{1}{\,2\,}\Bigr)
$$

</div>

## 本篇小結

[Theorem 5.11](#thm-slutsky) 的前提是一個序列機率收斂到常數、另一個序列分配收斂到隨機變數，結論則是兩者的和、積與商各自分配收斂到 $c+W$、$cW$ 與 <span class="text-nowrap">$\frac{\,W\,}{c}$，</span>其中商的部分另外要求 <span class="text-nowrap">$c\neq0$。</span>這與 [Theorem 5.10](/teaching-topics/continuous-mapping-theorem/#thm-pconv-related) 的各條相呼應，差別只在結論由機率收斂改為分配收斂。

三道例題的作法一致: 先把整個統計量拆成「分配收斂的部分」與「機率收斂到常數的部分」，再各自處理。[Example 5.30](#ex-slutsky-uniform-ratio) 的兩小題都靠這一步，第一小題把 $Z_n$ 的分子分母同除以 <span class="text-nowrap">$n$，</span>兩者各自由弱大數法則得到機率極限 $\frac{\,1\,}{2}$ 與 <span class="text-nowrap">$\frac{1}{\,3\,}$；</span>第二小題的分子由中央極限定理得到 <span class="text-nowrap">$\sqrt{n}\,\overline{Y}\dconv Z$，</span>分母機率收斂到 <span class="text-nowrap">$\frac{1}{\,3\,}$，</span>兩者相除得到 <span class="text-nowrap">$3Z\sim\mathcal{N}(0,\ 9)$。</span>[Example 5.31](#ex-slutsky-normal-ratio) 是同一個作法，分母的機率極限為 <span class="text-nowrap">$1$，</span>因此極限分配就是標準常態分配本身。

[Example 5.32](#ex-t-statistic-to-standard-normal) 把 $t$ 統計量寫成 $\sqrt{\frac{\sigma^{2}}{\,S_n^{2}\,}}$ 與 $\frac{\,\overline{X}-\mu\,}{\sigma/\sqrt{n}}$ 的乘積，前者由連續映射定理機率收斂到 <span class="text-nowrap">$1$，</span>後者不論 $n$ 多大都是標準常態分配，因此 $T$ 分配收斂至標準常態分配。換句話說，自由度趨於無窮時，$t$ 分配的極限分配就是標準常態分配。

[Theorem 5.12](#thm-delta-method) 處理的是史拉斯基定理沒有涵蓋的一般化函數轉換: 已知 <span class="text-nowrap">$\sqrt{n}\,(X_n-\theta)\dconv W\sim\mathcal{N}(0,\ \sigma^{2})$，</span>則 $\sqrt{n}\,[g(X_n)-g(\theta)]$ 的極限分配仍是常態分配，變異數多乘一個 <span class="text-nowrap">$[g^{\prime}(\theta)]^{2}$。</span>四道例題的差別只在 $g$ 取什麼: [Example 5.33](#ex-delta-method-squared-mean) 取 <span class="text-nowrap">$g(x)=x^{2}$，</span>得到 <span class="text-nowrap">$\mathcal{N}(0,\ 4\mu^{2}\sigma^{2})$；</span>[Example 5.34](#ex-delta-method-product-of-uniforms) 先令 $W_i=-\ln X_i$ 把均勻樣本的乘積化為指數樣本的平均數，再取 <span class="text-nowrap">$g(x)=e^{x}$；</span>[Example 5.35](#ex-delta-method-geometric-distribution) 取 <span class="text-nowrap">$g(x)=\frac{\,x-1\,}{x^{2}}$，</span>並在最後把極限分配改寫為 $n$ 有限時的漸近分配；[Example 5.36](#ex-delta-method-chi-square-root) 取 <span class="text-nowrap">$g(x)=\sqrt{x}$，</span>並把自由度為 $n$ 的卡方變數看成 $n$ 個自由度為 $1$ 的卡方變數之和，才有辦法套用中央極限定理。

機率論的部分至此告一段落。讀者已經具備足夠的基礎，可以進入數理統計的內容。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury. (Delta 法的證明見頁 240)
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
