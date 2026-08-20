---
title: "伽瑪分配"
subtitle: "The Gamma Distribution"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 4
topic: 12
order: 412
permalink: /lecture-notes/gamma-distribution/
date: 2026-08-12
published: false
excerpt: "伽瑪分配在形狀參數 $\\alpha=n$ 為正整數時，描述的是卜瓦松過程中直到第 $n$ 次偶發事件發生為止的等待時間。本篇先給出定義，並完整證明其機率函數為一個合法的機率函數，以及期望值 $\\alpha\\beta$、變異數 $\\alpha\\beta^{2}$ 與動差母函數 $(1-\\beta t)^{-\\alpha}$ 三者的公式，另外求出 $k$ 階原動差的公式。接著依序給出四項延伸性質: 伽瑪分配與卜瓦松分配的對偶關係、形狀參數為 $1$ 時即為指數分配、比例參數相同且彼此獨立的兩個伽瑪變數相加仍為伽瑪分配，以及比例伸縮性質。最後以四道例題演練對偶關係的兩種寫法，以及個數為隨機的指數變數之和的動差母函數。"
---

[上一篇](/lecture-notes/exponential-memoryless-and-minima/)談的是指數分配的無記憶性，以及兩個獨立指數分配的極小值與先後次序。指數分配所描述的，是[卜瓦松過程](/lecture-notes/poisson-process-and-distribution/#def-poisson-process)中等候直到一次偶發事件發生所需的等待時間；若把「一次」換成「$n$ 次」，這段等待時間所服從的分配，就是本篇的伽瑪分配。

本篇先給出伽瑪分配的定義，並完整證明其機率函數為一個合法的機率函數，以及期望值、變異數與動差母函數的公式，另外再求出 $k$ 階原動差的公式。接著依序說明四項延伸性質: 伽瑪分配與[卜瓦松分配](/lecture-notes/poisson-process-and-distribution/#def-poisson-distribution)的對偶關係、形狀參數為 $1$ 時即為[指數分配](/lecture-notes/gamma-function-exponential-distribution/#def-exponential-distribution)、比例參數相同且彼此獨立的兩個伽瑪變數相加仍為伽瑪分配，以及比例伸縮性質。最後以四道例題作為演練。

<div id="def-gamma-distribution" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 4.14 (伽瑪分配, gamma distribution)</div>

**適用範圍**:

令 $X$ 為一個非負連續隨機變數，在形狀參數 $\alpha=n\in\mathbb{N}$ 時，經常被用來描述卜瓦松過程中，直到 $n$ 次偶發事件發生為止的等待時間。

**值域範圍**:

$$
\mathcal{R}_{\sssig X}=\lbrace\,x\mid x\geqslant0\,\rbrace
$$

**表示式**:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
X\sim\mathrm{Gamma}(\alpha,\ \beta)\ \text{或}\ X\sim\mathrm{Gamma}(\alpha,\ \lambda)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
X&\sim\mathrm{Gamma}(\alpha,\ \beta)\\[0.5em]
&\text{或}\\[0.5em]
X&\sim\mathrm{Gamma}(\alpha,\ \lambda)
\end{aligned}
$$

</div>

**參數與參數範圍**:

$\alpha>0$ 為形狀參數；$\beta>0$ 為比例參數；$\lambda=\frac{1}{\,\beta\,}>0$ 為頻率參數。

**機率函數**:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
f_{\sssig X}(x)=\frac{1}{\,\beta^{\alpha}\Gamma(\alpha)\,}x^{\alpha-1}e^{-\frac{x}{\,\beta\,}},\ x\geqslant0\\[0.5em]
\text{或}\ \ f_{\sssig X}(x)=\frac{\lambda^{\alpha}}{\,\Gamma(\alpha)\,}x^{\alpha-1}e^{-\lambda x},\ x\geqslant0
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig X}(x)&=\frac{1}{\,\beta^{\alpha}\Gamma(\alpha)\,}x^{\alpha-1}e^{-\frac{x}{\,\beta\,}},\ x\geqslant0\\[0.5em]
&\text{或}\\[0.5em]
f_{\sssig X}(x)&=\frac{\lambda^{\alpha}}{\,\Gamma(\alpha)\,}x^{\alpha-1}e^{-\lambda x},\ x\geqslant0
\end{aligned}
$$

</div>

**期望值、變異數、動差母函數**:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\mathbb{E}(X)=\alpha\beta=\frac{\alpha}{\,\lambda\,},\quad \mathrm{Var}(X)=\alpha\beta^{2}=\frac{\alpha}{\,\lambda^{2}\,}\\[0.6em]
M_{\sssig X}(t)=(1-\beta t)^{-\alpha},\ t<\frac{1}{\,\beta\,}\ \text{ 或 }\ M_{\sssig X}(t)=\biggl(\frac{\lambda}{\,\lambda-t\,}\biggr)^{\alpha},\ t<\lambda
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\alpha\beta=\frac{\alpha}{\,\lambda\,},\\[0.5em]
\mathrm{Var}(X)&=\alpha\beta^{2}=\frac{\alpha}{\,\lambda^{2}\,}\\[0.5em]
M_{\sssig X}(t)&=(1-\beta t)^{-\alpha},\ t<\frac{1}{\,\beta\,}\\[0.5em]
&\text{或}\\[0.5em]
M_{\sssig X}(t)&=\biggl(\frac{\lambda}{\,\lambda-t\,}\biggr)^{\alpha},\ t<\lambda
\end{aligned}
$$

</div>

</div>

伽瑪分配 <span lang="en">(gamma distribution)</span> 有一些地方需要注意:

(1) 我們僅證明參數為 $\alpha,\beta$ 時的狀況如下；參數為 $\alpha,\lambda$ 的情況則同理可證。
{: .topic-paren-item}

<div class="topic-proof" markdown="1">
**Proof.**

先驗證機率函數在值域上的積分為 <span class="text-nowrap">$1$，</span>即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\int_{x\in\mathcal{R}_{\sssig X}}f_{\sssig X}(x)\,dx=\int_{0}^{\infty}\frac{1}{\,\beta^{\alpha}\Gamma(\alpha)\,}x^{\alpha-1}e^{-\frac{x}{\,\beta\,}}\,dx=\frac{\,\beta^{\alpha}\Gamma(\alpha)\,}{\beta^{\alpha}\Gamma(\alpha)}=1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\int_{x\in\mathcal{R}_{\sssig X}}f_{\sssig X}(x)\,dx&=\int_{0}^{\infty}\frac{1}{\,\beta^{\alpha}\Gamma(\alpha)\,}x^{\alpha-1}e^{-\frac{x}{\,\beta\,}}\,dx\\[0.45em]
&=\frac{\,\beta^{\alpha}\Gamma(\alpha)\,}{\beta^{\alpha}\Gamma(\alpha)}=1
\end{aligned}
$$

</div>

接著求期望值，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(X)=\mathbb{E}\bigl(X^{1}\bigr)=\beta^{1}\frac{\,\Gamma(\alpha+1)\,}{\Gamma(\alpha)}=\beta\frac{\,\alpha\,\Gamma(\alpha)\,}{\,\Gamma(\alpha)\,}=\alpha\beta
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\mathbb{E}\bigl(X^{1}\bigr)=\beta^{1}\frac{\,\Gamma(\alpha+1)\,}{\Gamma(\alpha)}\\[0.45em]
&=\beta\frac{\,\alpha\,\Gamma(\alpha)\,}{\,\Gamma(\alpha)\,}=\alpha\beta
\end{aligned}
$$

</div>

又可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\bigl(X^{2}\bigr)=\beta^{2}\frac{\,\Gamma(\alpha+2)\,}{\Gamma(\alpha)}=\beta^{2}\frac{\,\Gamma(\alpha)\,\alpha(\alpha+1)\,}{\Gamma(\alpha)}=(\alpha+1)\alpha\beta^{2}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl(X^{2}\bigr)&=\beta^{2}\frac{\,\Gamma(\alpha+2)\,}{\Gamma(\alpha)}\\[0.45em]
&=\beta^{2}\frac{\,\Gamma(\alpha)\,\alpha(\alpha+1)\,}{\Gamma(\alpha)}\\[0.45em]
&=(\alpha+1)\alpha\beta^{2}
\end{aligned}
$$

</div>

則變異數為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}(X)=\mathbb{E}\bigl(X^{2}\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}=(\alpha+1)\alpha\beta^{2}-\bigl(\alpha\beta\bigr)^{2}=\alpha\beta^{2}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(X)&=\mathbb{E}\bigl(X^{2}\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}\\[0.45em]
&=(\alpha+1)\alpha\beta^{2}-\bigl(\alpha\beta\bigr)^{2}\\[0.45em]
&=\alpha\beta^{2}
\end{aligned}
$$

</div>

最後求動差母函數，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{\sssig X}(t)&=\mathbb{E}\bigl(e^{tX}\bigr)=\int_{0}^{\infty}e^{tx}\frac{1}{\,\beta^{\alpha}\Gamma(\alpha)\,}x^{\alpha-1}e^{-\frac{x}{\beta}}\,dx\\[0.45em]
&=\int_{0}^{\infty}\frac{1}{\,\beta^{\alpha}\Gamma(\alpha)\,}x^{\alpha-1}e^{\bigl(t-\frac{1}{\beta}\bigr)x}\,dx\\[0.45em]
&=\frac{1}{\,\beta^{\alpha}\Gamma(\alpha)\,}\int_{0}^{\infty}x^{\alpha-1}e^{-\frac{x}{\bigl(\frac{\beta}{1-\beta t}\bigr)}}\,dx\qquad\Bigl(\text{當 }t<\frac{1}{\,\beta\,}\text{ 時此積分收斂}\Bigr)\\[0.45em]
&=\frac{1}{\,\beta^{\alpha}\Gamma(\alpha)\,}\biggl(\frac{\beta}{\,1-\beta t\,}\biggr)^{\alpha}\Gamma(\alpha)=\biggl(\frac{1}{\,1-\beta t\,}\biggr)^{\alpha}\\[0.45em]
&=(1-\beta t)^{-\alpha},\ t<\frac{1}{\,\beta\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig X}(t)&=\mathbb{E}\bigl(e^{tX}\bigr)\\[0.45em]
&=\int_{0}^{\infty}e^{tx}\frac{1}{\,\beta^{\alpha}\Gamma(\alpha)\,}x^{\alpha-1}e^{-\frac{x}{\beta}}\,dx\\[0.45em]
&=\int_{0}^{\infty}\frac{1}{\,\beta^{\alpha}\Gamma(\alpha)\,}x^{\alpha-1}e^{\bigl(t-\frac{1}{\beta}\bigr)x}\,dx\\[0.45em]
&=\frac{1}{\,\beta^{\alpha}\Gamma(\alpha)\,}\int_{0}^{\infty}x^{\alpha-1}e^{-\frac{x}{\bigl(\frac{\beta}{1-\beta t}\bigr)}}\,dx\\[0.25em]
&\qquad \Bigl(\text{當 }t<\frac{1}{\,\beta\,}\text{ 時此積分收斂}\Bigr)\\[0.45em]
&=\frac{1}{\,\beta^{\alpha}\Gamma(\alpha)\,}\biggl(\frac{\beta}{\,1-\beta t\,}\biggr)^{\alpha}\Gamma(\alpha)\\[0.45em]
&=\biggl(\frac{1}{\,1-\beta t\,}\biggr)^{\alpha}\\[0.25em]
&=(1-\beta t)^{-\alpha},\ t<\frac{1}{\,\beta\,}
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

在上述的證明中，我們不妨先證明伽瑪分配的 $k$ 階原動差:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\bigl(X^{k}\bigr)=\beta^{k}\frac{\,\Gamma(\alpha+k)\,}{\Gamma(\alpha)},\ \alpha,\beta>0,\ k\in\bigl(\lbrace0\rbrace\cup\mathbb{N}\bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl(X^{k}\bigr)&=\beta^{k}\frac{\,\Gamma(\alpha+k)\,}{\Gamma(\alpha)},\\[0.35em]
&\qquad \alpha,\beta>0,\ k\in\bigl(\lbrace0\rbrace\cup\mathbb{N}\bigr)
\end{aligned}
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.**

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl(X^{k}\bigr)&=\int_{0}^{\infty}x^{k}\cdot\frac{1}{\,\beta^{\alpha}\Gamma(\alpha)\,}x^{\alpha-1}e^{-\frac{x}{\beta}}\,dx\\[0.45em]
&=\frac{1}{\,\beta^{\alpha}\Gamma(\alpha)\,}\int_{0}^{\infty}x^{\alpha+k-1}e^{-\frac{x}{\beta}}\,dx=\frac{1}{\,\beta^{\alpha}\Gamma(\alpha)\,}\beta^{\alpha+k}\Gamma(\alpha+k)\\[0.45em]
&=\beta^{k}\frac{\,\Gamma(\alpha+k)\,}{\Gamma(\alpha)},\ \alpha,\beta>0,\ k\in\bigl(\lbrace0\rbrace\cup\mathbb{N}\bigr)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl(X^{k}\bigr)&=\int_{0}^{\infty}x^{k}\cdot\frac{1}{\,\beta^{\alpha}\Gamma(\alpha)\,}x^{\alpha-1}e^{-\frac{x}{\beta}}\,dx\\[0.45em]
&=\frac{1}{\,\beta^{\alpha}\Gamma(\alpha)\,}\int_{0}^{\infty}x^{\alpha+k-1}e^{-\frac{x}{\beta}}\,dx\\[0.45em]
&=\frac{1}{\,\beta^{\alpha}\Gamma(\alpha)\,}\beta^{\alpha+k}\Gamma(\alpha+k)\\[0.45em]
&=\beta^{k}\frac{\,\Gamma(\alpha+k)\,}{\Gamma(\alpha)},\\[0.25em]
&\qquad\ \ \alpha,\beta>0,\ k\in\bigl(\lbrace0\rbrace\cup\mathbb{N}\bigr)
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

若有此結果，要證明伽瑪分配的期望值與變異數，將會容易許多。

</div>

(2) **伽瑪分配**的定義可以得到以下幾個延伸性質:
{: .topic-paren-item}

第一，在 $\alpha=n\in\mathbb{N}$ 時，此分配可用來描述卜瓦松過程中，直到 $n$ 個偶發事件發生為止的等待時間，這導致伽瑪分配與卜瓦松分配間的對偶關係 <span lang="en">(dual relationship)</span>，即
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\text{令 }T\sim\mathrm{Gamma}(n,\lambda)\ \text{且}\ Y\sim\mathrm{Poi}(t\lambda)\text{，則 }\mathbb{P}(T>t)=\mathbb{P}(Y<n)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\text{令 }T\sim\mathrm{Gamma}(n,\lambda)\ \text{且}\ Y\sim\mathrm{Poi}(t\lambda)，\\[0.45em]
&\text{則 }\mathbb{P}(T>t)=\mathbb{P}(Y<n)
\end{aligned}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

伽瑪分配的頻率參數 $\lambda$ 與卜瓦松分配的 $\lambda$ 意義是完全相同的，都代表卜瓦松過程中，偶發事件發生的頻率 (rate)，只不過卜瓦松分配所描述的，是單位時間內偶發事件發生的次數。

這個對偶關係，與指數分配和卜瓦松分配的對偶關係相同，我們令了 $T$ 表示直到第 $n$ 次偶發事件發生所需要的時間，並且我們又令了 $Y$ 代表 $t$ 時長內偶發事件發生的次數，則在此敘述下，$Y<n$ 即代表**在 $t$ 時長內偶發事件發生的次數不到 $n$ 次**，換句話說，**直到第 $n$ 次偶發事件發生所需的時間比 $t$ 還要長**，這當然與 $T>t$ 的事件等價，因此有此對偶關係。

</div>

這個對偶關係能讓我們證明以下的命題:
{: .topic-paren-cont}

**令單位時間內的偶發事件發生次數服從參數為 $\lambda$ 的卜瓦松分配，則其中直到 $n$ 次偶發事件發生所需之等待時間，服從參數為 $n$ 與 $\lambda$ 的伽瑪分配。**
{: .topic-paren-cont}

<div class="topic-proof" markdown="1">
**Proof.**

先由對偶關係求出分配函數，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
F_{\sssig T}(t)&=\mathbb{P}(T\leqslant t)=1-\mathbb{P}(T>t)=1-\mathbb{P}(Y<n)\\[0.45em]
&=1-\sum_{y=0}^{n-1}\frac{\,e^{-\lambda t}(\lambda t)^{y}\,}{y!},\ t>0
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig T}(t)&=\mathbb{P}(T\leqslant t)=1-\mathbb{P}(T>t)\\[0.45em]
&=1-\mathbb{P}(Y<n)\\[0.45em]
&=1-\sum_{y=0}^{n-1}\frac{\,e^{-\lambda t}(\lambda t)^{y}\,}{y!},\ t>0
\end{aligned}
$$

</div>

則微分之後可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f_{\sssig T}(t)&=\frac{d\,F_{\sssig T}(t)}{d\,t}=\frac{d}{d\,t}\left[1-e^{-\lambda t}-\sum_{y=1}^{n-1}\frac{e^{-\lambda t}(\lambda t)^{y}}{y!}\right]\\[0.45em]
&=\lambda e^{-\lambda t}-\sum_{y=1}^{n-1}\left[\frac{d}{d\,t}\left(\frac{e^{-\lambda t}(\lambda t)^{y}}{y!}\right)\right]\\[0.45em]
&=\lambda e^{-\lambda t}-\sum_{y=1}^{n-1}\left[\frac{\,-\lambda e^{-\lambda t}(\lambda t)^{y}\,}{y!}+\frac{\,e^{-\lambda t}\,y\,(\lambda t)^{y-1}\,\lambda\,}{y!}\right]\\[0.45em]
&=\lambda e^{-\lambda t}+\lambda\sum_{y=1}^{n-1}\frac{\,e^{-\lambda t}(\lambda t)^{y}\,}{y!}-\lambda\sum_{y=1}^{n-1}\frac{\,e^{-\lambda t}\,(\lambda t)^{y-1}\,}{(y-1)!}\\[0.45em]
&=\lambda e^{-\lambda t}+\lambda\sum_{y=1}^{n-1}\frac{\,e^{-\lambda t}(\lambda t)^{y}\,}{y!}-\lambda\sum_{k=0}^{n-2}\frac{\,e^{-\lambda t}\,(\lambda t)^{k}\,}{k!}\\[0.25em]
&\qquad\qquad\qquad\qquad\qquad\qquad (\,\text{令}\ k=y-1\,)\\[0.45em]
&=\lambda\frac{\,e^{-\lambda t}(\lambda t)^{n-1}\,}{(n-1)!}=\frac{\lambda^{n}}{\,\Gamma(n)\,}t^{n-1}e^{-\lambda t},\ t>0
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig T}(t)&=\frac{d\,F_{\sssig T}(t)}{d\,t}\\[0.45em]
&=\frac{d}{d\,t}\left[1-e^{-\lambda t}-\sum_{y=1}^{n-1}\frac{e^{-\lambda t}(\lambda t)^{y}}{y!}\right]\\[0.45em]
&=\lambda e^{-\lambda t}\\[0.25em]
&\qquad-\sum_{y=1}^{n-1}\left[\frac{d}{d\,t}\left(\frac{e^{-\lambda t}(\lambda t)^{y}}{y!}\right)\right]\\[0.45em]
&=\lambda e^{-\lambda t}\\[0.25em]
&\qquad-\sum_{y=1}^{n-1}\left[\frac{\,-\lambda e^{-\lambda t}(\lambda t)^{y}\,}{y!}\right.\\[0.25em]
&\qquad\qquad\left.+\frac{\,e^{-\lambda t}\,y\,(\lambda t)^{y-1}\,\lambda\,}{y!}\right]\\[0.45em]
&=\lambda e^{-\lambda t}+\lambda\sum_{y=1}^{n-1}\frac{\,e^{-\lambda t}(\lambda t)^{y}\,}{y!}\\[0.25em]
&\qquad-\lambda\sum_{y=1}^{n-1}\frac{\,e^{-\lambda t}\,(\lambda t)^{y-1}\,}{(y-1)!}\\[0.45em]
&=\lambda e^{-\lambda t}+\lambda\sum_{y=1}^{n-1}\frac{\,e^{-\lambda t}(\lambda t)^{y}\,}{y!}\\[0.25em]
&\qquad-\lambda\sum_{k=0}^{n-2}\frac{\,e^{-\lambda t}\,(\lambda t)^{k}\,}{k!}\\[0.25em]
&\qquad (\,\text{令}\ k=y-1\,)\\[0.45em]
&=\lambda\frac{\,e^{-\lambda t}(\lambda t)^{n-1}\,}{(n-1)!}\\[0.25em]
&=\frac{\lambda^{n}}{\,\Gamma(n)\,}t^{n-1}e^{-\lambda t},\ t>0
\end{aligned}
$$

</div>

故可知

$$
T\sim\mathrm{Gamma}(\alpha=n,\ \lambda)
$$

原式得證。 <span class="topic-qed">$\square$</span>
</div>

第二，令 $X\sim\mathrm{Gamma}(\alpha,\ \beta)$ 且 <span class="text-nowrap">$\alpha=1$，</span>則
{: .topic-paren-cont}

$$
X\sim\mathrm{Exp}(\beta)
$$

<div class="topic-proof" markdown="1">
**Proof.**

由 $X\sim\mathrm{Gamma}(\alpha,\ \beta)$ 可知

$$
M_{\sssig X}(t)=(1-\beta t)^{-\alpha},\ t<\frac{1}{\,\beta\,}
$$

若 <span class="text-nowrap">$\alpha=1$，</span>則

$$
M_{\sssig X}(t)=(1-\beta t)^{-1},\ t<\frac{1}{\,\beta\,}\qquad\therefore\, X\sim\mathrm{Exp}(\beta)
$$

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個性質指出，指數分配只是伽瑪分配在 $\alpha=1$ 的特例。

</div>

第三，若 $X\sim\mathrm{Gamma}(\alpha_1,\ \beta)$ 與 $Y\sim\mathrm{Gamma}(\alpha_2,\ \beta)$ 滿足 <span class="text-nowrap">$X\indep Y$，</span>且令 <span class="text-nowrap">$W=X+Y$，</span>則
{: .topic-paren-cont}

$$
W\sim\mathrm{Gamma}(\alpha_1+\alpha_2,\ \beta)
$$

<div class="topic-proof" markdown="1">
**Proof.**

由[獨立隨機變數線性組合的動差母函數之定理](/lecture-notes/mgf-method-transformations/#thm-mgf-two-to-one)可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{\sssig W}(t)&=M_{\sssig X}(t)\,M_{\sssig Y}(t)\\[0.45em]
&=\Bigl[(1-\beta t)^{-\alpha_1}\Bigr]\,\Bigl[(1-\beta t)^{-\alpha_2}\Bigr]=(1-\beta t)^{-(\alpha_1+\alpha_2)}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig W}(t)&=M_{\sssig X}(t)\,M_{\sssig Y}(t)\\[0.45em]
&=\Bigl[(1-\beta t)^{-\alpha_1}\Bigr]\,\Bigl[(1-\beta t)^{-\alpha_2}\Bigr]\\[0.45em]
&=(1-\beta t)^{-(\alpha_1+\alpha_2)}
\end{aligned}
$$

</div>

則由[動差母函數的唯一性](/lecture-notes/uniqueness-of-the-mgf/#thm-mgf-uniqueness)可知

$$
W=X+Y\sim\mathrm{Gamma}(\alpha_1+\alpha_2,\ \beta)
$$

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個性質被稱作伽瑪分配的**可加性**，其限制是 $X$ 與 $Y$ 必須獨立，且比例參數 $\beta$ (或頻率參數 $\lambda$) 必須相等。值得一提的是，若 <span class="text-nowrap">$\alpha_1=\alpha_2=1$，</span>則可以得到 **iid 的指數分配相加會變成伽瑪分配**的結論。

</div>

第四，若 <span class="text-nowrap">$X\sim\mathrm{Gamma}(\alpha,\ \beta)$，</span>且令 <span class="text-nowrap">$Y=aX$，</span>則
{: .topic-paren-cont}

$$
Y\sim\mathrm{Gamma}(\alpha,\ a\beta)
$$

<div class="topic-proof" markdown="1">
**Proof.**

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
M_{\sssig Y}(t)=\mathbb{E}\bigl(e^{tY}\bigr)=\mathbb{E}\bigl(e^{taX}\bigr)=M_{\sssig X}(at)=(1-a\beta t)^{-\alpha}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig Y}(t)&=\mathbb{E}\bigl(e^{tY}\bigr)=\mathbb{E}\bigl(e^{taX}\bigr)\\[0.45em]
&=M_{\sssig X}(at)=(1-a\beta t)^{-\alpha}
\end{aligned}
$$

</div>

則由[動差母函數的唯一性](/lecture-notes/uniqueness-of-the-mgf/#thm-mgf-uniqueness)可知

$$
Y\sim\mathrm{Gamma}(\alpha,\ a\beta)
$$

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個性質指出，**比例伸縮性質**不僅是只有指數分配才有，伽瑪分配同樣也有。

</div>

(3) 由於指數分配只是伽瑪分配的一個特例，故讀者應特別注意，$\beta$ 與 $\lambda$ 不應視為兩個相異的參數，其理由與指數分配完全相同。
{: .topic-paren-item}

## 伽瑪分配的例題

<div id="ex-gamma-1" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.31</div>

<div lang="en" markdown="1">
Suppose that $X$ has the distribution <span class="text-nowrap">$\mathrm{Gamma}(\alpha,\ \beta)$,</span> where $\alpha$ is a positive integer, and that, for a fixed <span class="text-nowrap">$x>0$,</span> the random variable $Y$ has the Poisson distribution with parameter <span class="text-nowrap">$x/\beta$.</span> Show that

$$
\mathbb{P}(X\leqslant x)=\mathbb{P}(Y\geqslant\alpha)
$$

</div>

我們令

$$
h(\alpha)=\int_{0}^{x}\frac{\,t^{\alpha-1}e^{\frac{-t}{\beta}}\,}{\,\beta^{\alpha}\Gamma(\alpha)\,}\,dt
$$

則由分部積分可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X\leqslant x)&=h(\alpha)=\int_{0}^{x}\frac{\,t^{\alpha-1}e^{\frac{-t}{\beta}}\,}{\,\beta^{\alpha}\Gamma(\alpha)\,}\,dt=\frac{1}{\,\beta^{\alpha}\Gamma(\alpha)\,}\int_{0}^{x}t^{\alpha-1}e^{\frac{-t}{\beta}}\,dt\\[0.45em]
&=\frac{1}{\,\beta^{\alpha}\alpha\Gamma(\alpha)\,}\int_{0}^{x}e^{\frac{-t}{\beta}}\,d\bigl(t^{\alpha}\bigr)\\[0.45em]
&=\frac{1}{\,\beta^{\alpha}\Gamma(\alpha+1)\,}\left[\Bigl(e^{\frac{-t}{\beta}}t^{\alpha}\Bigr)\Big|^{x}_{0}-\int_{0}^{x}t^{\alpha}\,d\bigl(e^{\frac{-t}{\beta}}\bigr)\right]\\[0.45em]
&=\frac{\,e^{\frac{-x}{\beta}}\bigl(\frac{x}{\beta}\bigr)^{\alpha}\,}{\,\alpha!\,}-\frac{1}{\,\beta^{\alpha}\Gamma(\alpha+1)\,}\int_{0}^{x}t^{\alpha}\Bigl(\frac{-1}{\beta}\Bigr)e^{\frac{-t}{\beta}}\,dt\\[0.45em]
&=\frac{\,e^{\frac{-x}{\beta}}\bigl(\frac{x}{\beta}\bigr)^{\alpha}\,}{\,\alpha!\,}+\int_{0}^{x}\frac{\,t^{(\alpha+1)-1}e^{\frac{-t}{\beta}}\,}{\,\beta^{\alpha+1}\Gamma\bigl(\alpha+1\bigr)\,}\,dt\\[0.45em]
&=\frac{\,e^{\frac{-x}{\beta}}\bigl(\frac{x}{\beta}\bigr)^{\alpha}\,}{\,\alpha!\,}+h(\alpha+1)\\[0.45em]
&=\frac{\,e^{\frac{-x}{\beta}}\bigl(\frac{x}{\beta}\bigr)^{\alpha}\,}{\,\alpha!\,}+\frac{\,e^{\frac{-x}{\beta}}\bigl(\frac{x}{\beta}\bigr)^{\alpha+1}\,}{\,(\alpha+1)!\,}+h(\alpha+2)=\ldots\\[0.45em]
&=\sum_{y=\alpha}^{\infty}\frac{\,e^{\frac{-x}{\beta}}\bigl(\frac{x}{\beta}\bigr)^{y}\,}{\,y!\,}=\mathbb{P}(Y\geqslant\alpha)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X\leqslant x)&=h(\alpha)\\[0.35em]
&=\int_{0}^{x}\frac{\,t^{\alpha-1}e^{\frac{-t}{\beta}}\,}{\,\beta^{\alpha}\Gamma(\alpha)\,}\,dt\\[0.45em]
&=\frac{1}{\,\beta^{\alpha}\Gamma(\alpha)\,}\int_{0}^{x}t^{\alpha-1}e^{\frac{-t}{\beta}}\,dt\\[0.45em]
&=\frac{1}{\,\beta^{\alpha}\alpha\Gamma(\alpha)\,}\int_{0}^{x}e^{\frac{-t}{\beta}}\,d\bigl(t^{\alpha}\bigr)\\[0.45em]
&=\frac{1}{\,\beta^{\alpha}\Gamma(\alpha+1)\,}\Bigl[\Bigl(e^{\frac{-t}{\beta}}t^{\alpha}\Bigr)\Big|^{x}_{0}\\[0.25em]
&\qquad\qquad -\int_{0}^{x}t^{\alpha}\,d\bigl(e^{\frac{-t}{\beta}}\bigr)\Bigr]\\[0.45em]
&=\frac{\,e^{\frac{-x}{\beta}}\bigl(\frac{x}{\beta}\bigr)^{\alpha}\,}{\,\alpha!\,}\\[0.25em]
&\qquad -\frac{1}{\,\beta^{\alpha}\Gamma(\alpha+1)\,}\int_{0}^{x}t^{\alpha}\Bigl(\frac{-1}{\beta}\Bigr)e^{\frac{-t}{\beta}}\,dt\\[0.45em]
&=\frac{\,e^{\frac{-x}{\beta}}\bigl(\frac{x}{\beta}\bigr)^{\alpha}\,}{\,\alpha!\,}\\[0.25em]
&\qquad +\int_{0}^{x}\frac{\,t^{(\alpha+1)-1}e^{\frac{-t}{\beta}}\,}{\,\beta^{\alpha+1}\Gamma\bigl(\alpha+1\bigr)\,}\,dt\\[0.45em]
&=\frac{\,e^{\frac{-x}{\beta}}\bigl(\frac{x}{\beta}\bigr)^{\alpha}\,}{\,\alpha!\,}+h(\alpha+1)\\[0.45em]
&=\frac{\,e^{\frac{-x}{\beta}}\bigl(\frac{x}{\beta}\bigr)^{\alpha}\,}{\,\alpha!\,}+\frac{\,e^{\frac{-x}{\beta}}\bigl(\frac{x}{\beta}\bigr)^{\alpha+1}\,}{\,(\alpha+1)!\,}\\[0.25em]
&\qquad +h(\alpha+2)=\ldots\\[0.45em]
&=\sum_{y=\alpha}^{\infty}\frac{\,e^{\frac{-x}{\beta}}\bigl(\frac{x}{\beta}\bigr)^{y}\,}{\,y!\,}=\mathbb{P}(Y\geqslant\alpha)
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

在這個問題裡，我們事實上是以另外一個角度證明了伽瑪分配與卜瓦松分配的對偶關係，這個版本是本篇前面所提之對偶關係的餘事件。

直觀而言，這個版本的理解是**直到第 $\alpha$ 次偶發事件發生所需的時間至多是 $x$ 這麼長**，換句話說，**在 $x$ 時長內偶發事件發生的次數至少有 $\alpha$ 次**。

</div>

<div id="ex-gamma-2" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.32</div>

<div lang="en" markdown="1">
Suppose that $X_1$ and $X_2$ are independent random variables, each having the exponential distribution with parameter <span class="text-nowrap">$\lambda$,</span> so that both density functions are given by <span class="text-nowrap">$f(x)=\lambda e^{-\lambda x},\ x>0$.</span>

<ol class="topic-list-paren">
  <li>Find <span class="text-nowrap">$\mathbb{P}(X_1\leqslant10)$.</span></li>
  <li>Find <span class="text-nowrap">$\mathbb{P}(X_1+X_2\leqslant10)$.</span></li>
</ol>
</div>

(1) 依照題目敘述可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X_1\leqslant10)=\int_{0}^{10}\lambda e^{-\lambda x_1}\,dx_1=\biggl[-e^{-\lambda x_1}\biggr]^{10}_{0}=1-e^{-10\lambda}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X_1\leqslant10)&=\int_{0}^{10}\lambda e^{-\lambda x_1}\,dx_1\\[0.45em]
&=\biggl[-e^{-\lambda x_1}\biggr]^{10}_{0}=1-e^{-10\lambda}
\end{aligned}
$$

</div>

(2) 由伽瑪分配可加性可知 <span class="text-nowrap">$X_1+X_2\sim\mathrm{Gamma}(\alpha=2,\ \lambda)$，</span>又令 $Y\equiv N(10)$ 表示 $10$ 單位時間內之偶發事件發生個數，則 <span class="text-nowrap">$Y\sim\mathrm{Poi}(10\lambda)$，</span>由伽瑪分配與卜瓦松分配的對偶性知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X_1+X_2\leqslant10)&=\mathbb{P}(Y\geqslant2)=1-\mathbb{P}(Y=0)-\mathbb{P}(Y=1)\\[0.45em]
&=1-(1+10\lambda)e^{-10\lambda}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X_1+X_2\leqslant10)&=\mathbb{P}(Y\geqslant2)\\[0.45em]
&=1-\mathbb{P}(Y=0)-\mathbb{P}(Y=1)\\[0.45em]
&=1-(1+10\lambda)e^{-10\lambda}
\end{aligned}
$$

</div>

</div>

<div id="ex-gamma-3" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.33</div>

<div lang="en" markdown="1">
Suppose that $\lbrace N_t\rbrace_{t>0}$ is a Poisson process of rate <span class="text-nowrap">$\lambda>0$,</span> so that $N_t$ has the Poisson distribution <span class="text-nowrap">$\mathrm{Poi}(\lambda t)$,</span> and let $T_k\equiv\inf\lbrace t\mid N_t=k\rbrace$ be the time of the $k$-th arrival, where <span class="text-nowrap">$k\in\mathbb{N}$.</span> Determine the pdf of <span class="text-nowrap">$T_k$.</span>
</div>

先由對偶關係求出分配函數，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
F_{\sssig T_k}(t)&=\mathbb{P}(T_k\leqslant t)=1-\mathbb{P}(T_k>t)=1-\mathbb{P}(N_t<k)\\[0.45em]
&=1-\sum_{y=0}^{k-1}\frac{\,e^{-\lambda t}(\lambda t)^{y}\,}{y!},\ t>0
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig T_k}(t)&=\mathbb{P}(T_k\leqslant t)=1-\mathbb{P}(T_k>t)\\[0.45em]
&=1-\mathbb{P}(N_t<k)\\[0.45em]
&=1-\sum_{y=0}^{k-1}\frac{\,e^{-\lambda t}(\lambda t)^{y}\,}{y!},\ t>0
\end{aligned}
$$

</div>

則微分之後可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f_{\sssig T_k}(t)&=\frac{d\,F_{\sssig T_k}(t)}{d\,t}=\frac{d}{d\,t}\left[1-e^{-\lambda t}-\sum_{y=1}^{k-1}\frac{e^{-\lambda t}(\lambda t)^{y}}{y!}\right]\\[0.45em]
&=\lambda e^{-\lambda t}-\sum_{y=1}^{k-1}\left[\frac{d}{d\,t}\left(\frac{e^{-\lambda t}(\lambda t)^{y}}{y!}\right)\right]\\[0.45em]
&=\lambda e^{-\lambda t}-\sum_{y=1}^{k-1}\left[\frac{\,-\lambda e^{-\lambda t}(\lambda t)^{y}\,}{y!}+\frac{\,e^{-\lambda t}\,y\,(\lambda t)^{y-1}\,\lambda\,}{y!}\right]\\[0.45em]
&=\lambda e^{-\lambda t}+\lambda\sum_{y=1}^{k-1}\frac{\,e^{-\lambda t}(\lambda t)^{y}\,}{y!}-\lambda\sum_{y=1}^{k-1}\frac{\,e^{-\lambda t}\,(\lambda t)^{y-1}\,}{(y-1)!}\\[0.45em]
&=\lambda e^{-\lambda t}+\lambda\sum_{y=1}^{k-1}\frac{\,e^{-\lambda t}(\lambda t)^{y}\,}{y!}-\lambda\sum_{j=0}^{k-2}\frac{\,e^{-\lambda t}\,(\lambda t)^{j}\,}{j!}\\[0.25em]
&\qquad\qquad\qquad\qquad\qquad\qquad (\,\text{令}\ j=y-1\,)\\[0.45em]
&=\lambda\frac{\,e^{-\lambda t}(\lambda t)^{k-1}\,}{(k-1)!}=\frac{\lambda^{k}}{\,\Gamma(k)\,}t^{k-1}e^{-\lambda t},\ t>0
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig T_k}(t)&=\frac{d\,F_{\sssig T_k}(t)}{d\,t}\\[0.45em]
&=\frac{d}{d\,t}\left[1-e^{-\lambda t}\right.\\[0.25em]
&\qquad\qquad\left.-\sum_{y=1}^{k-1}\frac{e^{-\lambda t}(\lambda t)^{y}}{y!}\right]\\[0.45em]
&=\lambda e^{-\lambda t}\\[0.25em]
&\qquad-\sum_{y=1}^{k-1}\left[\frac{d}{d\,t}\left(\frac{e^{-\lambda t}(\lambda t)^{y}}{y!}\right)\right]\\[0.45em]
&=\lambda e^{-\lambda t}\\[0.25em]
&\qquad-\sum_{y=1}^{k-1}\left[\frac{\,-\lambda e^{-\lambda t}(\lambda t)^{y}\,}{y!}\right.\\[0.25em]
&\qquad\qquad\left.+\frac{\,e^{-\lambda t}\,y\,(\lambda t)^{y-1}\,\lambda\,}{y!}\right]\\[0.45em]
&=\lambda e^{-\lambda t}+\lambda\sum_{y=1}^{k-1}\frac{\,e^{-\lambda t}(\lambda t)^{y}\,}{y!}\\[0.25em]
&\qquad-\lambda\sum_{y=1}^{k-1}\frac{\,e^{-\lambda t}\,(\lambda t)^{y-1}\,}{(y-1)!}\\[0.45em]
&=\lambda e^{-\lambda t}+\lambda\sum_{y=1}^{k-1}\frac{\,e^{-\lambda t}(\lambda t)^{y}\,}{y!}\\[0.25em]
&\qquad-\lambda\sum_{j=0}^{k-2}\frac{\,e^{-\lambda t}\,(\lambda t)^{j}\,}{j!}\\[0.25em]
&\qquad (\,\text{令}\ j=y-1\,)\\[0.45em]
&=\lambda\frac{\,e^{-\lambda t}(\lambda t)^{k-1}\,}{(k-1)!}\\[0.25em]
&=\frac{\lambda^{k}}{\,\Gamma(k)\,}t^{k-1}e^{-\lambda t},\ t>0
\end{aligned}
$$

</div>

</div>

<div id="ex-gamma-4" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.34</div>

<div lang="en" markdown="1">
Suppose that $\lbrace X_i\rbrace_{i=1}^{\infty}$ are iid random variables with the exponential distribution <span class="text-nowrap">$\mathrm{Exp}(\theta)$,</span> where $\theta$ is measured in units of time, and let <span class="text-nowrap">$S_{\sssig N}=\sum_{i=1}^{N}X_i$.</span>

<ol class="topic-list-paren">
  <li>Suppose that $N=n$ is a constant with <span class="text-nowrap">$n\in\mathbb{N}$.</span> Determine the moment-generating function of $S_{\sssig N}$ and identify the distribution of <span class="text-nowrap">$S_{\sssig N}$,</span> stating the name of the distribution together with its parameters.</li>
  <li>Suppose that $N\sim\mathrm{Geo}(p)$ and that $\lbrace X_i\rbrace_{i=1}^{\infty}$ is independent of <span class="text-nowrap">$N$.</span> Determine the moment-generating function of $S_{\sssig N}$ and identify the distribution of <span class="text-nowrap">$S_{\sssig N}$,</span> stating the name of the distribution together with its parameters.</li>
</ol>
</div>

(1) 由於 $\theta$ 之單位為時間，故可知 $\lbrace X_i\rbrace_{i=1}^{N}\overset{\mathrm{iid}}{\sim}\mathrm{Exp}(\beta=\theta)$ 成立，又由獨立隨機變數線性組合的動差母函數之定理可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{S_{\sssig N}}(t)&=\mathbb{E}\Bigl(e^{tS_{\sssig N}}\Bigr)=\mathbb{E}\Bigl(e^{t\sum_{i=1}^{n}X_i}\Bigr)=\prod_{i=1}^{n}\mathbb{E}\bigl(e^{tX_i}\bigr)\\[0.45em]
&=\mathbb{E}\bigl(e^{tX_1}\bigr)\cdots\mathbb{E}\bigl(e^{tX_n}\bigr)\\[0.45em]
&=\underbrace{\biggl(\frac{1}{\,1-\theta t\,}\biggr)\cdots\biggl(\frac{1}{\,1-\theta t\,}\biggr)}_{n\ \text{個}}\\[0.45em]
&=\biggl(\frac{1}{\,1-\theta t\,}\biggr)^{n}=(1-\theta t)^{-n},\ t<\frac{1}{\,\theta\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{S_{\sssig N}}(t)&=\mathbb{E}\Bigl(e^{tS_{\sssig N}}\Bigr)=\mathbb{E}\Bigl(e^{t\sum_{i=1}^{n}X_i}\Bigr)\\[0.45em]
&=\prod_{i=1}^{n}\mathbb{E}\bigl(e^{tX_i}\bigr)\\[0.45em]
&=\mathbb{E}\bigl(e^{tX_1}\bigr)\cdots\mathbb{E}\bigl(e^{tX_n}\bigr)\\[0.45em]
&=\underbrace{\biggl(\frac{1}{\,1-\theta t\,}\biggr)\cdots\biggl(\frac{1}{\,1-\theta t\,}\biggr)}_{n\ \text{個}}\\[0.45em]
&=\biggl(\frac{1}{\,1-\theta t\,}\biggr)^{n}\\[0.25em]
&=(1-\theta t)^{-n},\ t<\frac{1}{\,\theta\,}
\end{aligned}
$$

</div>

由 mgf 的唯一性可知
{: .topic-paren-cont}

$$
S_{\sssig N}\sim\mathrm{Gamma}(\alpha=n,\ \beta=\theta)
$$

(2) 由獨立隨機變數線性組合的動差母函數之定理可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{S_{\sssig N}}(t)&=\mathbb{E}\Bigl(e^{tS_{\sssig N}}\Bigr)=\mathbb{E}\Bigl[\mathbb{E}\bigl(e^{tS_{\sssig N}}\mid N\bigr)\Bigr]=\mathbb{E}\bigl[(1-\theta t)^{-N}\bigr]\\[0.45em]
&=\sum_{n=1}^{\infty}(1-\theta t)^{-n}\,p(1-p)^{n-1}=\frac{p}{\,1-\theta t\,}\,\sum_{n=1}^{\infty}\left(\frac{1-p}{\,1-\theta t\,}\right)^{n-1}\\[0.45em]
&=\frac{p}{\,1-\theta t\,}\times\frac{1}{\,1-\frac{1-p}{\,1-\theta t\,}\,}=\frac{p}{\,1-\theta t\,}\times\frac{1-\theta t}{\,p-\theta t\,}\\[0.45em]
&=\frac{p}{\,p-\theta t\,}=\Bigl(1-\frac{\theta}{\,p\,}t\Bigr)^{-1},\ t<\frac{\,p\,}{\theta}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{S_{\sssig N}}(t)&=\mathbb{E}\Bigl(e^{tS_{\sssig N}}\Bigr)\\[0.45em]
&=\mathbb{E}\Bigl[\mathbb{E}\bigl(e^{tS_{\sssig N}}\mid N\bigr)\Bigr]\\[0.45em]
&=\mathbb{E}\bigl[(1-\theta t)^{-N}\bigr]\\[0.45em]
&=\sum_{n=1}^{\infty}(1-\theta t)^{-n}\,p(1-p)^{n-1}\\[0.45em]
&=\frac{p}{\,1-\theta t\,}\,\sum_{n=1}^{\infty}\left(\frac{1-p}{\,1-\theta t\,}\right)^{n-1}\\[0.45em]
&=\frac{p}{\,1-\theta t\,}\times\frac{1}{\,1-\frac{1-p}{\,1-\theta t\,}\,}\\[0.45em]
&=\frac{p}{\,1-\theta t\,}\times\frac{1-\theta t}{\,p-\theta t\,}\\[0.45em]
&=\frac{p}{\,p-\theta t\,}\\[0.45em]
&=\Bigl(1-\frac{\theta}{\,p\,}t\Bigr)^{-1},\ t<\frac{\,p\,}{\theta}
\end{aligned}
$$

</div>

由 mgf 的唯一性可知
{: .topic-paren-cont}

$$
S_{\sssig N}\sim\mathrm{Exp}(\beta=\theta/p)
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

上述問題中，收斂條件的由來是因為等比級數的公比 $\frac{1-p}{\,1-\theta t\,}$ 必須小於 <span class="text-nowrap">$1$，</span>由此整理而得。

此外，本題特別註明參數的單位是時間，意指 $\theta$ 是期望值。但若以頻率參數來思考本題，會發現一個有趣的結果，也就是 <span class="text-nowrap">$S_{\sssig N}\sim\mathrm{Exp}(\lambda=p/\theta)$，</span>這個結果可以思考成，如果我們在眾多偶發事件中尋找某類特定的偶發事件，則直到尋找到該類偶發事件為止所需要的等待時間，其頻率將降低 (平均等待時間將提高)，但仍然服從指數分配，而不會因為加總而變成伽瑪分配。

</div>

## 本篇小結

[Definition 4.14](#def-gamma-distribution) 的伽瑪分配以兩個參數界定: $\alpha$ 為形狀參數、$\beta$ 為比例參數，而頻率參數 $\lambda$ 就是 $\beta$ 的倒數，兩者只是同一個參數的兩種寫法。機率函數的分母是 $\beta^{\alpha}\Gamma(\alpha)$ 這個常數，其中的[伽瑪函數](/lecture-notes/gamma-function-exponential-distribution/#def-gamma-function)正是讓整條密度在值域上的積分等於 $1$ 的關鍵。證明的四個步驟依序驗證積分為 <span class="text-nowrap">$1$、</span>求得 <span class="text-nowrap">$\mathbb{E}(X)=\alpha\beta$、</span>再由二階原動差得到 <span class="text-nowrap">$\mathrm{Var}(X)=\alpha\beta^{2}$，</span>最後直接由定義求得 <span class="text-nowrap">$M_{\sssig X}(t)=(1-\beta t)^{-\alpha}$。</span>若先求出 $k$ 階原動差的公式，期望值與變異數都只是它在 $k=1$ 與 $k=2$ 的兩個特例。

定義之後的四項延伸性質，第一項是伽瑪分配與卜瓦松分配的對偶關係: $\alpha=n$ 為正整數時，$T>t$ 這個事件說的是「直到第 $n$ 次偶發事件發生所需的時間比 $t$ 還要長」，換句話說，$t$ 時長內的發生次數不到 $n$ 次，兩者是同一件事情，因而有 $\mathbb{P}(T>t)=\mathbb{P}(Y<n)$ 這條等式。由這條等式對 $t$ 微分，加總的兩項彼此相消之後只剩一項，得到的正是伽瑪分配的密度。第二項指出 $\alpha=1$ 時伽瑪分配即為[指數分配](/lecture-notes/gamma-function-exponential-distribution/#def-exponential-distribution)。第三項是可加性: 兩個 mgf 相乘使指數上的 $\alpha_1$ 與 $\alpha_2$ 相加，前提是兩個變數獨立且比例參數相同；$\alpha_1=\alpha_2=1$ 時，它說的就是兩個 iid 的指數變數相加會變成伽瑪分配。第四項是比例伸縮性質，$Y=aX$ 只把比例參數乘上 <span class="text-nowrap">$a$，</span>形狀參數不變。

四道例題分成兩組。[Example 4.31](#ex-gamma-1) 以分部積分把 $h(\alpha)$ 一層一層往上遞推，得到 $\mathbb{P}(X\leqslant x)=\mathbb{P}(Y\geqslant\alpha)$ 這條等式，這是前面對偶關係的餘事件版本；[Example 4.33](#ex-gamma-3) 則把卜瓦松過程中第 $k$ 次到達的時刻寫成 <span class="text-nowrap">$T_k$，</span>其密度的求法與對偶關係的證明完全相同。[Example 4.32](#ex-gamma-2) 把兩個獨立的指數變數相加，先由可加性認出伽瑪分配，再由對偶關係換成卜瓦松機率來計算。[Example 4.34](#ex-gamma-4) 的兩個小題則把相加的個數本身當成隨機的: 個數固定為 $n$ 時，$n$ 個 iid 的指數變數之和是伽瑪分配；個數服從幾何分配時，等比級數加總之後所得到的 mgf 仍是指數分配的形式，只是平均等待時間由 $\theta$ 變為 $\theta/p$ 這個值。

[下一篇](/lecture-notes/weibull-reliability-and-hazard/)介紹韋伯分配，並依序給出可靠度函數與風險函數的定義。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
