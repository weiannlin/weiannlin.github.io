---
title: "常態機率的計算與偏斜函數的例題"
subtitle: "Computing Normal Probabilities and the Skewing Function"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 4
topic: 18
order: 418
permalink: /lecture-notes/normal-probability-computation/
date: 2026-08-12
published: false
excerpt: "上一篇給出常態分配的定義、標準化與線性組合可加性，本篇接著以四道例題演練常態機率的實際計算。前三題的作法一致: 先把常態變數標準化，再把所求化為標準常態的機率，分別處理裝瓶容量的不合格率、兩支股票年報酬的比較，以及以 $\\Phi(\\cdot)$ 表達一段區間的機率。最後一題換一個方向，先驗證 $2\\,\\phi(z)\\Phi(\\lambda z)$ 是一個合法的 pdf，再以 cdf 法與 Jacobian 法兩種作法證明其平方服從 $\\chi^{2}(1)$ 分配。過程中會看到滿足 $h(x)+h(-x)=1$ 的偏斜函數，以及標準常態的對稱關係在其中的用處。"
---

[上一篇](/lecture-notes/normal-distribution/)給出[常態分配](/lecture-notes/normal-distribution/#def-normal)的定義，並依序說明標準常態分配、標準化、反標準化與線性組合可加性這幾項性質。本篇不再增加新的定義，而是把這些性質用在實際的機率計算上。

前三道例題的作法一致: 先把常態變數減去期望值再除以標準差，化為標準常態變數 <span class="text-nowrap">$Z$，</span>所求的機率便可以由標準常態的機率表達，其中第二題另外用到兩個獨立常態變數相減之後仍為常態分配這一項性質。第四道例題則換一個方向，給定 $f_{\sssig Z}(z)=2\,\phi(z)\Phi(\lambda z)$ 這個函數，先驗證它是一個合法的 pdf，再以 [cdf 法](/lecture-notes/one-to-one-transformations/#prop-cdf-method)與 [Jacobian 法](/lecture-notes/one-to-one-transformations/#prop-jacobian-method)各證明一次 $Y=Z^{2}$ 服從 $\chi^{2}(1)$ 分配；兩處的關鍵都是 $\phi$ 為偶函數以及 $\Phi(-z)=1-\Phi(z)$ 這兩件事。

## 常態機率的計算

<div id="ex-normal-prob-1" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.44</div>

<div lang="en" markdown="1">
Suppose that the content filled by a bottling process is normally distributed with a mean of $600$ cc and a standard deviation of $2$ cc, and that the customer accepts a bottle only when its content lies within $600\pm5$ cc.

<ol class="topic-list-paren">
  <li>Determine the percentage of defective bottles that this process produces.</li>
  <li>Suppose that a quality engineer intends to bring that percentage down to $1\%$ by reducing the variation alone. Find the standard deviation that this requires.</li>
</ol>
</div>

(1) 由題意可知，若令 $X$ 表示裝填過程中所裝填的實際容量，則有
{: .topic-paren-item}

$$
X\sim\mathcal{N}(\mu=600,\ \sigma=2)
$$

又題目敘述中表示，不合格的情況為 $X>605$ 或 <span class="text-nowrap">$X<595$，</span>則不合格的機率為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X>605)+\mathbb{P}(X<595)&=\mathbb{P}\biggl(\frac{X-600}{2}>\frac{605-600}{2}\biggr)\\[0.45em]
&\quad +\mathbb{P}\biggl(\frac{X-600}{2}<\frac{595-600}{2}\biggr)\\[0.45em]
&=\mathbb{P}(Z>2.5)+\mathbb{P}(Z<-2.5)\\[0.45em]
&=0.0062+0.0062=0.0124
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(X>605)+\mathbb{P}(X<595)\\[0.3em]
&=\mathbb{P}\biggl(\frac{X-600}{2}>\frac{605-600}{2}\biggr)\\[0.3em]
&\qquad+\mathbb{P}\biggl(\frac{X-600}{2}<\frac{595-600}{2}\biggr)\\[0.3em]
&=\mathbb{P}(Z>2.5)+\mathbb{P}(Z<-2.5)\\[0.3em]
&=0.0062+0.0062=0.0124
\end{aligned}
$$

</div>

(2) 題目的敘述是求取標準差 $\sigma$ 使不合格事件 $X>605$ 或 $X<595$ 的事件機率下降至 <span class="text-nowrap">$1\%$，</span>此即令 $X\sim\mathcal{N}(600,\ \sigma)$ 這個分配，並且使得
{: .topic-paren-item}

$$
\mathbb{P}(X>605)+\mathbb{P}(X<595)=0.01
$$

由此可得
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X>605)+\mathbb{P}(X<595)&=\mathbb{P}\biggl(Z>\frac{605-600}{\sigma}\biggr)\\[0.45em]
&\quad +\mathbb{P}\biggl(Z<\frac{595-600}{\sigma}\biggr)=0.01
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(X>605)+\mathbb{P}(X<595)\\[0.3em]
&=\mathbb{P}\biggl(Z>\frac{605-600}{\sigma}\biggr)\\[0.3em]
&\qquad+\mathbb{P}\biggl(Z<\frac{595-600}{\sigma}\biggr)=0.01
\end{aligned}
$$

</div>

又由標準常態的對稱性可知
{: .topic-paren-cont}

$$
\mathbb{P}\biggl(Z>\frac{5}{\,\sigma\,}\biggr)=\mathbb{P}\biggl(Z<\frac{\,-5\,}{\sigma}\biggr)=0.005
$$

由此可得
{: .topic-paren-cont}

$$
\frac{5}{\,\sigma\,}=2.575\qquad\therefore\,\sigma=1.9418
$$

</div>

<div id="ex-normal-prob-2" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.45</div>

<div lang="en" markdown="1">
Suppose that an analyst on Wall Street treats the annual return on the stock of Company A and the annual return on the stock of Company B each as an observation from a normal distribution, the two means being $\mu_{\sssig A}=8.0\%$ and $\mu_{\sssig B}=9.5\%$ and the two standard deviations being $\sigma_{\sssig A}=1.5\%$ and <span class="text-nowrap">$\sigma_{\sssig B}=2.0\%$.</span> In making an investment decision the analyst counts a return above $5\%$ as “satisfactory” and a return above $10\%$ as “excellent”.

<ol class="topic-list-paren">
  <li>What is the probability that the stock of Company A turns out to be “unsatisfactory”?</li>
  <li>Suppose further that the two annual returns are independent of each other. What is the probability that the stock of Company B does better than the stock of Company A?</li>
  <li>Given that the stock of Company A is “satisfactory”, what is the probability that the stocks of both companies are “satisfactory”?</li>
</ol>
</div>

(1) 依題意敘述可令 $X$ 表示 A 公司的年報酬，則有
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
X\sim\mathcal{N}(\mu=\mu_{\sssig A}=0.08,\ \sigma=\sigma_{\sssig A}=0.015)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
X\sim\mathcal{N}\bigl(&\mu=\mu_{\sssig A}=0.08,\\[0.3em]
&\sigma=\sigma_{\sssig A}=0.015\bigr)
\end{aligned}
$$

</div>

則所求為「不滿意」的機率，即
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X<0.05)=\mathbb{P}\biggl(Z<\frac{\,0.05-0.08\,}{0.015}=-2\biggr)=0.0228
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X<0.05)&=\mathbb{P}\biggl(Z<\frac{\,0.05-0.08\,}{0.015}=-2\biggr)\\[0.3em]
&=0.0228
\end{aligned}
$$

</div>

(2) 承接上題假設，並令
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
Y\sim\mathcal{N}(\mu=\mu_{\sssig B}=0.095,\ \sigma=\sigma_{\sssig B}=0.02)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
Y\sim\mathcal{N}\bigl(&\mu=\mu_{\sssig B}=0.095,\\[0.3em]
&\sigma=\sigma_{\sssig B}=0.02\bigr)
\end{aligned}
$$

</div>

所求為 B 公司的年報酬比 A 公司的年報酬高的機率，此即
{: .topic-paren-cont}

$$
\mathbb{P}(Y>X)=\mathbb{P}(Y-X>0)
$$

又因題目假設 A 公司與 B 公司的年報酬彼此獨立，故可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
Y-X\sim\mathcal{N}\bigl(\mu=\mu_{\sssig B}-\mu_{\sssig A}=0.015,\ \sigma^{2}=\sigma^{2}_{\sssig A}+\sigma^{2}_{\sssig B}=0.000625\bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
Y-X\sim\mathcal{N}\bigl(&\mu=\mu_{\sssig B}-\mu_{\sssig A}=0.015,\\[0.3em]
&\sigma^{2}=\sigma^{2}_{\sssig A}+\sigma^{2}_{\sssig B}=0.000625\bigr)
\end{aligned}
$$

</div>

由此可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(Y>X)=\mathbb{P}(Y-X>0)&=\mathbb{P}\biggl(Z>\frac{0-0.015}{\sqrt{0.000625}}\biggr)\\[0.45em]
&=\mathbb{P}(Z>-0.6)=0.7257
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(Y>X)&=\mathbb{P}(Y-X>0)\\[0.3em]
&=\mathbb{P}\biggl(Z>\frac{0-0.015}{\sqrt{0.000625}}\biggr)\\[0.3em]
&=\mathbb{P}(Z>-0.6)=0.7257
\end{aligned}
$$

</div>

(3) 題目所求為，在給定 $0.05<X\leqslant0.10$ 的條件下 $0.05<Y\leqslant0.10$ 的機率，此即
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}\bigl(\,&\lbrace0.05<Y\leqslant0.10\rbrace\mid 0.05<X\leqslant0.10\,\bigr)\\[0.45em]
&=\frac{\mathbb{P}\bigl(\,\lbrace0.05<X\leqslant0.10\rbrace\ \cap\ \lbrace0.05<Y\leqslant0.10\rbrace\,\bigr)}{\mathbb{P}(\,0.05<X\leqslant0.10\,)}\\[0.45em]
&=\frac{\mathbb{P}(\,0.05<X\leqslant0.10\,)\times\mathbb{P}(\,0.05<Y\leqslant0.10\,)}{\mathbb{P}(\,0.05<X\leqslant0.10\,)}\qquad(\,\because\ X\indep Y\,)\\[0.45em]
&=\mathbb{P}(\,0.05<Y\leqslant0.10\,)=\mathbb{P}\biggl(\frac{\,0.05-0.095\,}{0.02}<Z<\frac{\,0.1-0.095\,}{0.02}\biggr)\\[0.45em]
&=\mathbb{P}(-2.25<Z<0.25)=0.5865
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}\bigl(\,\lbrace0.05<Y\leqslant0.10\rbrace\\[0.2em]
&\qquad\ \mid 0.05<X\leqslant0.10\,\bigr)\\[0.3em]
&=\mathbb{P}\bigl(\,\lbrace0.05<X\leqslant0.10\rbrace\\[0.3em]
&\qquad \cap\ \lbrace0.05<Y\leqslant0.10\rbrace\,\bigr)\\[0.3em]
&\qquad\Big/\mathbb{P}(\,0.05<X\leqslant0.10\,)\\[0.3em]
&=\Bigl(\mathbb{P}(\,0.05<X\leqslant0.10\,)\\[0.3em]
&\qquad \times\ \mathbb{P}(\,0.05<Y\leqslant0.10\,)\Bigr)\\[0.3em]
&\qquad\Big/\mathbb{P}(\,0.05<X\leqslant0.10\,)\\[0.3em]
&\qquad\qquad (\,\because\ X\indep Y\,)\\[0.3em]
&=\mathbb{P}(\,0.05<Y\leqslant0.10\,)\\[0.3em]
&=\mathbb{P}\biggl(\frac{\,0.05-0.095\,}{0.02}<Z\\[0.2em]
&\qquad\qquad <\frac{\,0.1-0.095\,}{0.02}\biggr)\\[0.3em]
&=\mathbb{P}(-2.25<Z<0.25)=0.5865
\end{aligned}
$$

</div>

</div>

<div id="ex-normal-prob-3" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.46</div>

<div lang="en" markdown="1">
Suppose that $Y$ has the distribution <span class="text-nowrap">$\mathcal{N}(2,4)$.</span> Determine $\mathbb{P}(1\leqslant Y\leqslant4)$ in terms of <span class="text-nowrap">$\Phi(\cdot)$,</span> the cdf of the standard normal distribution.
</div>

由題目敘述可知 <span class="text-nowrap">$Y\sim\mathcal{N}(2,4)$，</span>則所求為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(1\leqslant Y\leqslant4)&=\mathbb{P}(1<Y\leqslant4)=\mathbb{P}\biggl(\frac{\,1-2\,}{\sqrt{4}}<Z\leqslant\frac{\,4-2\,}{\sqrt{4}}\biggr)\\[0.45em]
&=\mathbb{P}(-0.5<Z\leqslant1)=\mathbb{P}(Z\leqslant1)-\mathbb{P}(Z\leqslant-0.5)\\[0.45em]
&=\Phi(1)-\Phi(-0.5)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(1\leqslant Y\leqslant4)&=\mathbb{P}(1<Y\leqslant4)\\[0.3em]
&=\mathbb{P}\biggl(\frac{\,1-2\,}{\sqrt{4}}<Z\leqslant\frac{\,4-2\,}{\sqrt{4}}\biggr)\\[0.3em]
&=\mathbb{P}(-0.5<Z\leqslant1)\\[0.3em]
&=\mathbb{P}(Z\leqslant1)-\mathbb{P}(Z\leqslant-0.5)\\[0.3em]
&=\Phi(1)-\Phi(-0.5)
\end{aligned}
$$

</div>

</div>

## 偏斜函數與卡方分配

<div id="ex-normal-prob-4" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.47</div>

<div lang="en" markdown="1">
Let <span class="text-nowrap">$f_{\sssig Z}(z)=2\,\phi(z)\Phi(\lambda z),\ z\in\mathbb{R}$,</span> and $\lambda\in\mathbb{R}$ is a constant, where $\phi(z)$ and $\Phi(z)$ are the pdf and cdf of standard normal distribution, respectively. Show that

<ol class="topic-list-paren">
  <li>$f_{\sssig Z}(z)$ is a valid pdf.</li>
  <li>if <span class="text-nowrap">$Z\sim f_{\sssig Z}(z)$,</span> then $Y=Z^{2}$ has $\chi^{2}(1)$ distribution.</li>
</ol>
</div>

(1) 由於 $\phi(z)$ 與 $\Phi(z)$ 分別是標準常態分配之 pdf 與 cdf，故知道 $\phi(z)\geqslant0$ 與 <span class="text-nowrap">$\Phi(z)\geqslant0$，</span>可知
{: .topic-paren-item}

$$
f_{\sssig Z}(z)=2\,\phi(z)\Phi(\lambda z)\geqslant0,\ \forall z\in\mathbb{R}
$$

又可得
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\int_{-\infty}^{\infty}f_{\sssig Z}(z)\,dz&=\int_{-\infty}^{0}f_{\sssig Z}(z)\,dz+\int_{0}^{\infty}f_{\sssig Z}(z)\,dz\\[0.45em]
&=\int_{-\infty}^{0}2\,\phi(z)\Phi(\lambda z)\,dz+\int_{0}^{\infty}2\,\phi(z)\Phi(\lambda z)\,dz\\[0.45em]
&=\int_{\infty}^{0}2\,\phi(-t)\Phi(-\lambda t)\,d(-t)+\int_{0}^{\infty}2\,\phi(z)\Phi(\lambda z)\,dz\\[0.45em]
&\qquad\qquad (\,\text{令}\ z=-t\,)\\[0.45em]
&=\int^{\infty}_{0}2\,\phi(t)\bigl[1-\Phi(\lambda t)\bigr]\,dt+\int_{0}^{\infty}2\,\phi(z)\Phi(\lambda z)\,dz\\[0.45em]
&=\int_{0}^{\infty}2\,\phi(z)\bigl[\bigl(1-\Phi(\lambda z)\bigr)+\Phi(\lambda z)\bigr]\,dz\\[0.45em]
&=2\int_{0}^{\infty}\phi(z)\,dz=2\times\frac{1}{\,2\,}=1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\int_{-\infty}^{\infty}f_{\sssig Z}(z)\,dz\\[0.3em]
&=\int_{-\infty}^{0}f_{\sssig Z}(z)\,dz+\int_{0}^{\infty}f_{\sssig Z}(z)\,dz\\[0.3em]
&=\int_{-\infty}^{0}2\,\phi(z)\Phi(\lambda z)\,dz\\[0.2em]
&\qquad+\int_{0}^{\infty}2\,\phi(z)\Phi(\lambda z)\,dz\\[0.3em]
&=\int_{\infty}^{0}2\,\phi(-t)\Phi(-\lambda t)\,d(-t)\\[0.2em]
&\qquad+\int_{0}^{\infty}2\,\phi(z)\Phi(\lambda z)\,dz\\[0.2em]
&\qquad\qquad (\,\text{令}\ z=-t\,)\\[0.3em]
&=\int^{\infty}_{0}2\,\phi(t)\bigl[1-\Phi(\lambda t)\bigr]\,dt\\[0.2em]
&\qquad+\int_{0}^{\infty}2\,\phi(z)\Phi(\lambda z)\,dz\\[0.3em]
&=\int_{0}^{\infty}2\,\phi(z)\bigl[\bigl(1-\Phi(\lambda z)\bigr)\\[0.2em]
&\qquad\qquad +\Phi(\lambda z)\bigr]\,dz\\[0.3em]
&=2\int_{0}^{\infty}\phi(z)\,dz=2\times\frac{1}{\,2\,}=1
\end{aligned}
$$

</div>

故知道 $f_{\sssig Z}(z)=2\,\phi(z)\Phi(\lambda z),\ z\in\mathbb{R}$ 為一個合法之 pdf。
{: .topic-paren-cont}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

上述做法中，利用了 $\phi(z)$ 為一個偶函數 (即 $\phi(z)=\phi(-z),\ \forall z\in\mathbb{R}$) 的特性，將積分範圍考慮為 $(-\infty,0]$ 與 $(0,\infty)$ 兩段，並且利用 $\Phi(-z)=1-\Phi(z)$ 的性質完成此證明。事實上，凡滿足 <span class="text-nowrap">$h(x)+h(-x)=1$，</span>且 $0\leqslant h(x)\leqslant1$ 之函數，皆被稱作**偏斜函數 <span lang="en">(skewing function)</span>**，這種函數在許多特殊的問題上皆能看見，而 $\Phi(z)$ 正是此類的函數之一。

</div>

(2) **[ cdf 法 ]**
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
F_{\sssig Y}(y)&=\mathbb{P}(Y\leqslant y)=\mathbb{P}(Z^{2}\leqslant y)=\mathbb{P}(-\sqrt{y}\leqslant Z\leqslant\sqrt{y})\\[0.45em]
&=\int_{-\sqrt{y}}^{\sqrt{y}}2\,\phi(z)\Phi(\lambda z)\,dz\\[0.45em]
&=\int_{-\sqrt{y}}^{0}2\,\phi(z)\Phi(\lambda z)\,dz+\int_{0}^{\sqrt{y}}2\,\phi(z)\Phi(\lambda z)\,dz\\[0.45em]
&=\int_{\sqrt{y}}^{0}2\,\phi(-t)\Phi(-\lambda t)\,d(-t)+\int_{0}^{\sqrt{y}}2\,\phi(z)\Phi(\lambda z)\,dz\\[0.45em]
&\qquad\qquad (\,\text{令}\ z=-t\,)\\[0.45em]
&=\int^{\sqrt{y}}_{0}2\,\phi(t)\bigl[1-\Phi(\lambda t)\bigr]\,dt+\int_{0}^{\sqrt{y}}2\,\phi(z)\Phi(\lambda z)\,dz\\[0.45em]
&=2\int_{0}^{\sqrt{y}}\phi(z)\,dz
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig Y}(y)&=\mathbb{P}(Y\leqslant y)=\mathbb{P}(Z^{2}\leqslant y)\\[0.3em]
&=\mathbb{P}(-\sqrt{y}\leqslant Z\leqslant\sqrt{y})\\[0.3em]
&=\int_{-\sqrt{y}}^{\sqrt{y}}2\,\phi(z)\Phi(\lambda z)\,dz\\[0.3em]
&=\int_{-\sqrt{y}}^{0}2\,\phi(z)\Phi(\lambda z)\,dz\\[0.2em]
&\qquad+\int_{0}^{\sqrt{y}}2\,\phi(z)\Phi(\lambda z)\,dz\\[0.3em]
&=\int_{\sqrt{y}}^{0}2\,\phi(-t)\Phi(-\lambda t)\,d(-t)\\[0.2em]
&\qquad+\int_{0}^{\sqrt{y}}2\,\phi(z)\Phi(\lambda z)\,dz\\[0.2em]
&\qquad (\,\text{令}\ z=-t\,)\\[0.3em]
&=\int^{\sqrt{y}}_{0}2\,\phi(t)\bigl[1-\Phi(\lambda t)\bigr]\,dt\\[0.2em]
&\qquad+\int_{0}^{\sqrt{y}}2\,\phi(z)\Phi(\lambda z)\,dz\\[0.3em]
&=2\int_{0}^{\sqrt{y}}\phi(z)\,dz
\end{aligned}
$$

</div>

由此可得
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f_{\sssig Y}(y)&=\frac{\,d\,F_{\sssig Y}(y)\,}{d\,y}=\frac{d}{\,d\,y\,}\left(2\int_{0}^{\sqrt{y}}\phi(z)\,dz\right)\\[0.45em]
&=\frac{d}{\,d\,\sqrt{y}\,}\left(2\int_{0}^{\sqrt{y}}\phi(z)\,dz\right)\times\frac{\,d\,\sqrt{y}\,}{d\,y}\\[0.45em]
&=2\phi(\sqrt{y})\times\frac{1}{\,2\sqrt{y}\,}=2\,\frac{1}{\,\sqrt{2\pi}\,}e^{-\frac{\,(\sqrt{y})^{2}\,}{2}}\times\frac{1}{\,2\sqrt{y}\,}\\[0.45em]
&=\frac{\,y^{-\frac{1}{2}}e^{-\frac{y}{2}}\,}{\sqrt{2\pi}}=\frac{\,y^{\frac{1}{2}-1}e^{-\frac{y}{2}}\,}{2^{\frac{1}{2}}\Gamma\bigl(\frac{1}{2}\bigr)},\ y\geqslant0
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig Y}(y)&=\frac{\,d\,F_{\sssig Y}(y)\,}{d\,y}\\[0.3em]
&=\frac{d}{\,d\,y\,}\left(2\int_{0}^{\sqrt{y}}\phi(z)\,dz\right)\\[0.3em]
&=\frac{d}{\,d\,\sqrt{y}\,}\left(2\int_{0}^{\sqrt{y}}\phi(z)\,dz\right)\\[0.2em]
&\qquad\times\frac{\,d\,\sqrt{y}\,}{d\,y}\\[0.3em]
&=2\phi(\sqrt{y})\times\frac{1}{\,2\sqrt{y}\,}\\[0.3em]
&=2\,\frac{1}{\,\sqrt{2\pi}\,}e^{-\frac{\,(\sqrt{y})^{2}\,}{2}}\times\frac{1}{\,2\sqrt{y}\,}\\[0.3em]
&=\frac{\,y^{-\frac{1}{2}}e^{-\frac{y}{2}}\,}{\sqrt{2\pi}}=\frac{\,y^{\frac{1}{2}-1}e^{-\frac{y}{2}}\,}{2^{\frac{1}{2}}\Gamma\bigl(\frac{1}{2}\bigr)},\\[0.3em]
&\qquad\qquad y\geqslant0
\end{aligned}
$$

</div>

故知道
{: .topic-paren-cont}

$$
Y=Z^{2}\sim\mathrm{Gamma}\Bigl(\alpha=\frac{1}{\,2\,},\ \beta=2\Bigr)
$$

此即
{: .topic-paren-cont}

$$
Y\sim\chi^{2}(\nu=1)
$$

**[ Jacobian 法 ]**
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
[\,Z\geqslant0\,]\quad Y=Z^{2}\qquad\therefore\, Z=\sqrt{Y}\ \text{且}\ \mathbf{J}=\frac{\,d\,z\,}{\,d\,y\,}=\frac{1}{\,\sqrt{2y}\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
[\,Z\geqslant0\,]\quad Y&=Z^{2}\\[0.35em]
&\qquad\therefore\, Z=\sqrt{Y}\\[0.35em]
&\qquad\text{且}\ \mathbf{J}=\frac{\,d\,z\,}{\,d\,y\,}=\frac{1}{\,\sqrt{2y}\,}
\end{aligned}
$$

</div>

可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig Y}^{*}(y)=f_{\sssig Z}(\sqrt{y})\left\lvert\frac{1}{\,\sqrt{2y}\,}\right\rvert=2\,\phi(\sqrt{y})\Phi(\lambda\sqrt{y})\,\frac{1}{\,2\sqrt{y}\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig Y}^{*}(y)&=f_{\sssig Z}(\sqrt{y})\left\lvert\frac{1}{\,\sqrt{2y}\,}\right\rvert\\[0.3em]
&=2\,\phi(\sqrt{y})\Phi(\lambda\sqrt{y})\,\frac{1}{\,2\sqrt{y}\,}
\end{aligned}
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
[\,Z<0\,]\quad Y=Z^{2}\qquad\therefore\, Z=-\sqrt{Y}\ \text{且}\ \mathbf{J}=\frac{\,d\,z\,}{\,d\,y\,}=\frac{-1}{\,\sqrt{2y}\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
[\,Z<0\,]\quad Y&=Z^{2}\\[0.35em]
&\qquad\therefore\, Z=-\sqrt{Y}\\[0.35em]
&\qquad\text{且}\ \mathbf{J}=\frac{\,d\,z\,}{\,d\,y\,}=\frac{-1}{\,\sqrt{2y}\,}
\end{aligned}
$$

</div>

可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f_{\sssig Y}^{**}(y)&=f_{\sssig Z}(-\sqrt{y})\left\lvert\frac{-1}{\,\sqrt{2y}\,}\right\rvert=2\,\phi(-\sqrt{y})\Phi(-\lambda\sqrt{y})\,\frac{1}{\,2\sqrt{y}\,}\\[0.45em]
&=2\,\phi(\sqrt{y})\bigl[1-\Phi(\lambda\sqrt{y})\bigr]\,\frac{1}{\,2\sqrt{y}\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig Y}^{**}(y)&=f_{\sssig Z}(-\sqrt{y})\left\lvert\frac{-1}{\,\sqrt{2y}\,}\right\rvert\\[0.3em]
&=2\,\phi(-\sqrt{y})\Phi(-\lambda\sqrt{y})\,\frac{1}{\,2\sqrt{y}\,}\\[0.3em]
&=2\,\phi(\sqrt{y})\bigl[1-\Phi(\lambda\sqrt{y})\bigr]\,\frac{1}{\,2\sqrt{y}\,}
\end{aligned}
$$

</div>

則有
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f_{\sssig Y}(y)&=f_{\sssig Y}^{*}(y)+f_{\sssig Y}^{**}(y)=2\,\phi(\sqrt{y})\,\frac{1}{\,2\sqrt{y}\,}\\[0.45em]
&=\frac{\,y^{\frac{1}{2}-1}e^{-\frac{y}{2}}\,}{2^{\frac{1}{2}}\Gamma\bigl(\frac{1}{2}\bigr)},\ y\geqslant0
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig Y}(y)&=f_{\sssig Y}^{*}(y)+f_{\sssig Y}^{**}(y)\\[0.3em]
&=2\,\phi(\sqrt{y})\,\frac{1}{\,2\sqrt{y}\,}\\[0.3em]
&=\frac{\,y^{\frac{1}{2}-1}e^{-\frac{y}{2}}\,}{2^{\frac{1}{2}}\Gamma\bigl(\frac{1}{2}\bigr)},\ y\geqslant0
\end{aligned}
$$

</div>

故知道
{: .topic-paren-cont}

$$
Y=Z^{2}\sim\mathrm{Gamma}\Bigl(\alpha=\frac{1}{\,2\,},\ \beta=2\Bigr)
$$

此即
{: .topic-paren-cont}

$$
Y\sim\chi^{2}(\nu=1)
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

$\mathrm{Gamma}\bigl(\alpha=\frac{1}{\,2\,},\ \beta=2\bigr)$ 分配事實上就是 $\chi^{2}(\nu=1)$ 分配，這是一個固定且重要的結果，在稍後卡方分配的小節中，我們一定會看到這個重要的關係。此外，未來我們會學到，標準常態分配的平方也服從 $\chi^{2}(\nu=1)$ 分配，但這題中的分配不是標準常態分配，卻同樣具備這個性質，這也是由 $\Phi(-z)=1-\Phi(z)$ 導致的。

</div>

## 本篇小結

[Example 4.44](#ex-normal-prob-1) 到 [Example 4.46](#ex-normal-prob-3) 三題的作法一致: 把常態變數減去期望值再除以標準差，化為標準常態變數 <span class="text-nowrap">$Z$，</span>所求的機率便可以由標準常態的機率表達。[Example 4.44](#ex-normal-prob-1) 的第一小題把「不合格」寫成 $X>605$ 或 $X<595$ 這兩個互斥事件，標準化之後兩側各得 <span class="text-nowrap">$0.0062$，</span>合計為 <span class="text-nowrap">$0.0124$；</span>第二小題反過來，把不合格的機率固定為 <span class="text-nowrap">$1\%$，</span>由對稱性得到單側機率為 <span class="text-nowrap">$0.005$，</span>再由 $\frac{5}{\,\sigma\,}=2.575$ 這條等式解出所需要的標準差。

[Example 4.45](#ex-normal-prob-2) 的第一小題只是單一常態變數的機率計算。第二小題要比較兩支股票的年報酬，作法是把 $\mathbb{P}(Y>X)$ 改寫成 $\mathbb{P}(Y-X>0)$ 這個形式，再由[上一篇](/lecture-notes/normal-distribution/)的線性組合可加性得知 $Y-X$ 仍為常態分配，其期望值為兩者的期望值之差、變異數為兩者的變異數之和。第三小題則先以條件機率的定義展開，再由獨立性把分子拆成兩個機率相乘，與分母約去之後只剩下 B 公司的那一項。[Example 4.46](#ex-normal-prob-3) 要求以 $\Phi(\cdot)$ 表達答案，因此標準化之後把結果留在 $\Phi(1)-\Phi(-0.5)$ 這個差，不再換算為數值。

[Example 4.47](#ex-normal-prob-4) 換一個方向。第一小題驗證 $2\,\phi(z)\Phi(\lambda z)$ 是一個合法的 pdf: 非負性由 $\phi$ 與 $\Phi$ 的非負性直接得到，積分為 $1$ 則是把積分範圍拆成負半線與正半線兩段，在負半線上代換 <span class="text-nowrap">$z=-t$，</span>再利用 $\phi$ 為偶函數以及 $\Phi(-\lambda t)=1-\Phi(\lambda t)$ 這條關係，使兩段的被積分函數合併為 <span class="text-nowrap">$2\,\phi(z)$，</span>其在正半線上的積分正好是 <span class="text-nowrap">$1$。</span>第二小題給了兩種作法: cdf 法先把 $F_{\sssig Y}(y)$ 化為 $2\int_{0}^{\sqrt{y}}\phi(z)\,dz$ 這個式子，再對 $y$ 微分；Jacobian 法則把 $Z\geqslant0$ 與 $Z<0$ 兩段各自轉換，兩個密度相加之後 $\Phi(\lambda\sqrt{y})$ 與 $1-\Phi(\lambda\sqrt{y})$ 恰好相消。兩種作法所得到的密度相同，都是 $\mathrm{Gamma}\bigl(\alpha=\frac{1}{\,2\,},\ \beta=2\bigr)$ 這個分配，也就是 $\chi^{2}(\nu=1)$ 分配。

值得留意的是，讓 $\lambda$ 完全消失的關鍵在於 $\Phi(-z)=1-\Phi(z)$ 這條關係。凡滿足 $h(x)+h(-x)=1$ 且 $0\leqslant h(x)\leqslant1$ 的函數都具有這項性質，這種函數稱作偏斜函數。也因為如此，[Example 4.47](#ex-normal-prob-4) 中的分配並不是標準常態分配，其平方卻同樣服從 $\chi^{2}(1)$ 分配。

下一篇回到標準常態分配本身，先求出它的各階原動差，再由此給出斯泰因引理。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
