---
title: "沃德等式與賭徒破產"
subtitle: "Wald’s Identity and the Gambler’s Ruin"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 16
order: 316
permalink: /teaching-topics/wald-identity-gamblers-ruin/
date: 2026-08-13
published: false
excerpt: "沃德等式處理的是加總的項數本身也是隨機變數的情形: 若 $X_1,X_2,\\ldots$ 為獨立同分配的隨機變數，$N$ 是與它們獨立的非負整數隨機變數，則 $S_{\\sssig N}=\\sum_{i=1}^{N}X_i$ 的期望值是兩個期望值相乘，變異數則由兩項相加而得。它的證明正是雙重期望值定理與變異數分解定理的直接應用。本篇以四道例題示範它的用法: 前兩道處理同一個問題，一道由沃德等式與全機率定理求出每日售出 laptop PC 的期望值、標準差與分配，另一道改以動差母函數確認同一個分配；後兩道是賭徒破產問題，公平賭局的版本可由沃德等式一步得解，不公平賭局的版本則須逐項相減再以等比級數求和。"
---

[上一篇](/teaching-topics/variance-decomposition-theorem/)以 [Theorem 3.11](/teaching-topics/variance-decomposition-theorem/#thm-var-decom-thm) 把一個[隨機變數](/teaching-topics/random-variables-and-pmf/#def-random-variable)的[變異數](/teaching-topics/variance/#def-variance)拆成組內變異與組間變異兩個部分。[雙重期望值定理](/teaching-topics/double-expectation-theorem/#thm-double-expectation)與[變異數分解定理](/teaching-topics/variance-decomposition-theorem/#thm-var-decom-thm)，都是把條件之下的產物依條件變數的機率加權平均，從而得到邊際的產物；這兩條定理還有一個很典型的衍生應用，就是加總的項數本身也是隨機變數的情形。

本篇即由此出發，先給出沃德等式 <span lang="en">(Wald’s identity)</span>，它要求被加總的各項彼此[獨立](/teaching-topics/independent-random-variables/#def-indep-r-v)且具有相同的分配，而加到第幾項則由另一個非負整數隨機變數決定；接著以雙重期望值定理與變異數分解定理完成它的證明，再以四道例題示範它的用法。前兩道例題處理同一個問題，一道由沃德等式與[全機率定理](/teaching-topics/conditional-law-of-total-probability/#thm-law-of-total-prob-r-v)求出每日售出 laptop PC 的期望值、[標準差](/teaching-topics/variance-standard-deviation/#def-standard-deviation)與分配，另一道改以[動差母函數](/teaching-topics/moment-generating-functions/#def-mgf)確認同一個分配。後兩道則是賭徒破產問題，公平賭局的版本可由沃德等式一步得解，不公平賭局的版本則須逐項相減再以等比級數求和。

<div id="thm-wald-identity" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 3.12 (沃德等式, Wald’s identity)</div>

若 $X_1, X_2, \ldots$ 為獨立同分配的隨機變數，$N$ 是一個非負整數隨機變數，且 $N$ 與 $X_1, X_2, \ldots$ 獨立，則若令

$$
S_{\sssig N}=\sum_{i=1}^{N}X_i
$$

我們有

<ol class="topic-list-paren topic-list-paren--math">
  <li>
$$
\mathbb{E}(S_{\sssig N})=\mu_{\sssig X}\mu_{\sssig N}
$$
  </li>
  <li>
$$
\mathrm{Var}(S_{\sssig N})=\sigma_{\sssig X}^{2}\mu_{\sssig N}+\mu_{\sssig X}^{2}\sigma_{\sssig N}^{2}
$$
  </li>
</ol>

其中要求 <span class="text-nowrap">$\sigma_{\sssig X}^{2}$，</span>$\sigma_{\sssig N}^{2}$ 皆存在。

</div>

<div class="topic-proof" markdown="1">
**Proof.**

(1)
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(S_{\sssig N}\mid N=n)=\mathbb{E}\Bigl[\sum_{i=1}^{n}X_i\Bigr]=n\,\mathbb{E}(X_i)=n\mu_{\sssig X}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(S_{\sssig N}\mid N=n)&=\mathbb{E}\Bigl[\sum_{i=1}^{n}X_i\Bigr]\\[0.45em]
&=n\,\mathbb{E}(X_i)=n\mu_{\sssig X}
\end{aligned}
$$

</div>

又由[雙重期望值定理](/teaching-topics/double-expectation-theorem/#thm-double-expectation)可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(S_{\sssig N})=\mathbb{E}\bigl[\mathbb{E}(S_{\sssig N}\mid N)\bigr]=\mathbb{E}\bigl(N\mu_{\sssig X}\bigr)=\mu_{\sssig X}\mathbb{E}(N)=\mu_{\sssig X}\mu_{\sssig N}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(S_{\sssig N})&=\mathbb{E}\bigl[\mathbb{E}(S_{\sssig N}\mid N)\bigr]\\[0.45em]
&=\mathbb{E}\bigl(N\mu_{\sssig X}\bigr)=\mu_{\sssig X}\mathbb{E}(N)\\[0.45em]
&=\mu_{\sssig X}\mu_{\sssig N}
\end{aligned}
$$

</div>

(2) 由[變異數分解定理](/teaching-topics/variance-decomposition-theorem/#thm-var-decom-thm)可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}(S_{\sssig N})=\mathbb{E}\bigl[\mathrm{Var}(S_{\sssig N}\mid N)\bigr]+\mathrm{Var}\bigl[\mathbb{E}(S_{\sssig N}\mid N)\bigr]
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(S_{\sssig N})&=\mathbb{E}\bigl[\mathrm{Var}(S_{\sssig N}\mid N)\bigr]\\[0.45em]
&\qquad+\mathrm{Var}\bigl[\mathbb{E}(S_{\sssig N}\mid N)\bigr]
\end{aligned}
$$

</div>

其中
{: .topic-paren-cont}

$$
\begin{gathered}
\mathbb{E}(S_{\sssig N}\mid N=n)=n\mu_{\sssig X}\\[0.45em]
\mathrm{Var}(S_{\sssig N}\mid N=n)=n\sigma_{\sssig X}^{2}
\end{gathered}
$$

故可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}(S_{\sssig N})=\mathbb{E}\bigl(N\sigma_{\sssig X}^{2}\bigr)+\mathrm{Var}\bigl(N\mu_{\sssig X}\bigr)=\sigma_{\sssig X}^{2}\mu_{\sssig N}+\mu_{\sssig X}^{2}\sigma_{\sssig N}^{2}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(S_{\sssig N})&=\mathbb{E}\bigl(N\sigma_{\sssig X}^{2}\bigr)+\mathrm{Var}\bigl(N\mu_{\sssig X}\bigr)\\[0.45em]
&=\sigma_{\sssig X}^{2}\mu_{\sssig N}+\mu_{\sssig X}^{2}\sigma_{\sssig N}^{2}
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

證明過程中使用到 $\mathrm{Var}(S_{\sssig N}\mid N=n)$ $=$ $n\sigma_{\sssig X}^{2}$ 的結果，我們至此還沒有說明過原因，但讀者可以不用心急，稍後介紹到[共變異數](/teaching-topics/covariance/#def-covariance)的環節時，我們將會學到所有所需的細節。

</div>

<div id="ex-store-laptop-purchases" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.31 <span lang="en">(The random sum problem)</span></div>

<div lang="en" markdown="1">
Suppose that every customer walking into Mova’s store buys a laptop PC with probability <span class="text-nowrap">$p$,</span> and that the count of customers walking in on a single day follows a Poisson distribution whose mean is <span class="text-nowrap">$\lambda$.</span>

<ol class="topic-list-paren">
  <li>Determine the expected number of laptop PCs that Mova’s store sells in a day, and evaluate the standard deviation of that number.</li>
  <li>What is the probability that a whole day goes by without Mova selling a single laptop PC?</li>
  <li>Suppose that $X$ denotes the number of laptop PCs sold in a day at Mova’s store, and determine the probability distribution of <span class="text-nowrap">$X$.</span></li>
</ol>
</div>

(1) 令 $N$ 表示每日進入 Mova 之人數，$Y_1, Y_2, \ldots$ 為第 $i$ 位顧客購買 laptop PC 之數量，$X=\sum_{i=1}^{N}Y_i$ 為購買 laptop PC 之數量，其中
{: .topic-paren-item}

$$
\begin{gathered}
N\sim\mathrm{Poi}(\lambda)\\[0.45em]
Y_i\mid(N=n)\overset{\mathrm{iid}}{\sim}\mathrm{Ber}(p)\\[0.45em]
X\mid(N=n)\sim\mathrm{Bin}(n,p)
\end{gathered}
$$

則
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(N)=\lambda,\ \ \mathrm{Var}(N)=\lambda,\ \ \mathbb{E}(Y_i)=p,\ \ \mathrm{Var}(Y_i)=p(1-p)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(N)&=\lambda,\ \ \mathrm{Var}(N)=\lambda,\\[0.45em]
\mathbb{E}(Y_i)&=p,\ \ \mathrm{Var}(Y_i)=p(1-p)
\end{aligned}
$$

</div>

由[沃德等式](#thm-wald-identity)可知
{: .topic-paren-cont}

$$
\mathbb{E}(X)=\mathbb{E}(N)\,\mathbb{E}(Y_i)=\lambda p
$$

<div class="topic-math-layout topic-math-layout--desktop topic-math-follow-before" markdown="1">

$$
\mathrm{Var}(X)=\mathrm{Var}(Y_i)\,\mathbb{E}(N)+\bigl[\mathbb{E}(Y_i)\bigr]^{2}\,\mathrm{Var}(N)=\lambda p(1-p)+\lambda p^{2}=\lambda p
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile topic-math-follow-before" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(X)&=\mathrm{Var}(Y_i)\,\mathbb{E}(N)\\[0.2em]
&\qquad+\bigl[\mathbb{E}(Y_i)\bigr]^{2}\,\mathrm{Var}(N)\\[0.45em]
&=\lambda p(1-p)+\lambda p^{2}=\lambda p\\[0.4em]
&\qquad\therefore\, \operatorname{SD}(X)=\sqrt{\mathrm{Var}(X)}=\sqrt{\lambda p}
\end{aligned}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

$\mathrm{Poi}(\lambda)$ 是[卜瓦松分配](/teaching-topics/poisson-process-and-distribution/#def-poisson-distribution) <span lang="en">(Poisson distribution)</span>，這種分配我們在之後會談到，期望值與變異數都是 <span class="text-nowrap">$\lambda$，</span>是相當特殊的分配。

</div>

(2) 由[全機率定理](/teaching-topics/conditional-law-of-total-probability/#thm-law-of-total-prob-r-v)可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X=0)&=p_{\sssig X}(0)=\mathbb{E}\bigl[p_{\sssig X\mid N}(0\mid N)\bigr]=\sum_{n=0}^{\infty}p_{\sssig X\mid N}(0\mid n)\,p_{\sssig N}(n)\\[0.45em]
&=\sum_{n=0}^{\infty}\binom{n}{0}p^{0}(1-p)^{n-0}\cdot\frac{\,e^{-\lambda}\lambda^{n}\,}{n!}=e^{-\lambda}\sum_{n=0}^{\infty}\frac{\bigl[\lambda(1-p)\bigr]^{n}}{n!}\\[0.45em]
&=e^{-\lambda}\cdot e^{\lambda(1-p)}=e^{-\lambda p}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X=0)&=p_{\sssig X}(0)=\mathbb{E}\bigl[p_{\sssig X\mid N}(0\mid N)\bigr]\\[0.45em]
&=\sum_{n=0}^{\infty}p_{\sssig X\mid N}(0\mid n)\,p_{\sssig N}(n)\\[0.45em]
&=\sum_{n=0}^{\infty}\binom{n}{0}p^{0}(1-p)^{n-0}\cdot\frac{\,e^{-\lambda}\lambda^{n}\,}{n!}\\[0.45em]
&=e^{-\lambda}\sum_{n=0}^{\infty}\frac{\bigl[\lambda(1-p)\bigr]^{n}}{n!}\\[0.45em]
&=e^{-\lambda}\cdot e^{\lambda(1-p)}=e^{-\lambda p}
\end{aligned}
$$

</div>

(3) 由[全機率定理](/teaching-topics/conditional-law-of-total-probability/#thm-law-of-total-prob-r-v)可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
p_{\sssig X}(x)&=\mathbb{E}\bigl[p_{\sssig X\mid N}(x\mid N)\bigr]=\sum_{n=x}^{\infty}\binom{n}{x}p^{x}(1-p)^{n-x}\cdot\frac{e^{-\lambda}\lambda^{n}}{n!}\\[0.45em]
&=\sum_{n=x}^{\infty}\frac{n!}{x!(n-x)!}\cdot p^{x}(1-p)^{n-x}\cdot\frac{e^{-\lambda}\lambda^{n}}{n!}\\[0.2em]
&\qquad\qquad\bigl[\,\text{令}\ t=n-x\ \Longleftrightarrow\ n=t+x\,\bigr]\\[0.45em]
&=\sum_{t=0}^{\infty}\frac{e^{-\lambda}\lambda^{t+x}}{x!\,t!}p^{x}(1-p)^{t}=\frac{e^{-\lambda}(\lambda p)^{x}}{x!}\sum_{t=0}^{\infty}\frac{\bigl[\lambda(1-p)\bigr]^{t}}{t!}\\[0.45em]
&=\frac{e^{-\lambda}(\lambda p)^{x}}{x!}\cdot e^{\lambda(1-p)}=\frac{e^{-\lambda p}(\lambda p)^{x}}{x!},\ \ x=0,1,\ldots,\infty
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig X}(x)&=\mathbb{E}\bigl[p_{\sssig X\mid N}(x\mid N)\bigr]\\[0.45em]
&=\sum_{n=x}^{\infty}\binom{n}{x}p^{x}(1-p)^{n-x}\cdot\frac{e^{-\lambda}\lambda^{n}}{n!}\\[0.45em]
&=\sum_{n=x}^{\infty}\frac{n!}{x!(n-x)!}\cdot p^{x}(1-p)^{n-x}\\[0.2em]
&\qquad\cdot\frac{e^{-\lambda}\lambda^{n}}{n!}\\[0.2em]
&\quad \bigl[\,\text{令}\ t=n-x\ \Longleftrightarrow\ n=t+x\,\bigr]\\[0.45em]
&=\sum_{t=0}^{\infty}\frac{e^{-\lambda}\lambda^{t+x}}{x!\,t!}p^{x}(1-p)^{t}\\[0.45em]
&=\frac{e^{-\lambda}(\lambda p)^{x}}{x!}\sum_{t=0}^{\infty}\frac{\bigl[\lambda(1-p)\bigr]^{t}}{t!}\\[0.45em]
&=\frac{e^{-\lambda}(\lambda p)^{x}}{x!}\cdot e^{\lambda(1-p)}\\[0.45em]
&=\frac{e^{-\lambda p}(\lambda p)^{x}}{x!},\ \ x=0,1,\ldots,\infty
\end{aligned}
$$

</div>

故可知
{: .topic-paren-cont}

$$
X\sim\mathrm{Poi}(\lambda p)
$$

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

上述的[全機率定理](/teaching-topics/conditional-law-of-total-probability/#thm-law-of-total-prob-r-v)中，之所以 $n$ 的範圍從 $x$ 開始而非從 $0$ 開始，乃是因為其 conditional pmf 的範圍如下

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
&\left\lbrace
\begin{array}{l}
n=0,1,\ldots,\infty\\[0.2em]
x=0,1,\ldots,n
\end{array}
\right.\\[0.9em]
\Longrightarrow\
&\left\lbrace
\begin{array}{l}
0\leqslant x\leqslant n<\infty\\[0.2em]
n\in\lbrace 0\rbrace\cup\mathbb{N}\\[0.2em]
x\in\lbrace 0\rbrace\cup\mathbb{N}
\end{array}
\right.\\[0.9em]
\Longrightarrow\
&\left\lbrace
\begin{array}{l}
x=0,1,\ldots,\infty\\[0.2em]
n=x,x+1,\ldots,\infty
\end{array}
\right.
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\left\lbrace
\begin{array}{l}
n=0,1,\ldots,\infty\\[0.2em]
x=0,1,\ldots,n
\end{array}
\right.\\[0.9em]
\Longrightarrow\
&\left\lbrace
\begin{array}{l}
0\leqslant x\leqslant n<\infty\\[0.2em]
n\in\lbrace 0\rbrace\cup\mathbb{N}\\[0.2em]
x\in\lbrace 0\rbrace\cup\mathbb{N}
\end{array}
\right.\\[0.9em]
\Longrightarrow\
&\left\lbrace
\begin{array}{l}
x=0,1,\ldots,\infty\\[0.2em]
n=x,x+1,\ldots,\infty
\end{array}
\right.
\end{aligned}
$$

</div>

這意味著，雖然是給定了 $N=n$ 且 <span class="text-nowrap">$n\in\lbrace 0\rbrace\cup\mathbb{N}$，</span>但是在固定 $X=x$ 時，$n$ 不可能是一個比 $x$ 還要更小的非負整數，所以在上述的[全機率定理](/teaching-topics/conditional-law-of-total-probability/#thm-law-of-total-prob-r-v)中，加總的起點是 $x$ 而非 <span class="text-nowrap">$0$。</span>

</div>

</div>

<div id="ex-poisson-random-sum" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.32</div>

<div lang="en" markdown="1">
Suppose that $Y,X_1,X_2,\ldots$ are mutually independent random variables, that the distribution of $Y$ is

$$
\mathbb{P}(Y=n)=\frac{\,e^{-\lambda}\lambda^{n}\,}{n!},\ n=0,1,2,\ldots
$$

and that $X_1,X_2,\ldots$ share the common distribution

$$
\mathbb{P}(X=x)=p^{x}(1-p)^{1-x},\ x=0,1
$$

For every real number <span class="text-nowrap">$t$,</span> write

$$
\phi(t,y)=\mathbb{E}\Bigl(e^{t(X_1+X_2+\cdots+X_{\sssig Y})}\Bigm\vert Y=y\Bigr)
$$

<ol class="topic-list-paren">
  <li>Find <span class="text-nowrap">$\phi(t,y)$.</span></li>
  <li>Determine $\mathbb{E}\bigl[\,\phi(t,Y)\,\bigr]$ from the result of the previous part.</li>
</ol>
</div>

(1) 依照題目設定可知 $X_1, X_2, \ldots$ $\overset{\mathrm{iid}}{\sim}$ <span class="text-nowrap">$\mathrm{Ber}(p)$，</span>知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
M_{\sssig X_i}(t)=\mathbb{E}\bigl(e^{tX_i}\bigr)=\bigl[\,pe^{t}+(1-p)\,\bigr],\ t\in\mathbb{R}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig X_i}(t)&=\mathbb{E}\bigl(e^{tX_i}\bigr)\\[0.45em]
&=\bigl[\,pe^{t}+(1-p)\,\bigr],\ t\in\mathbb{R}
\end{aligned}
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\phi(t,y)&=\mathbb{E}\Bigl(e^{t(X_1+X_2+\cdots+X_{\sssig Y})}\Bigm\vert Y=y\Bigr)=\mathbb{E}\Bigl(e^{t(X_1+X_2+\cdots+X_y)}\Bigr)\\[0.45em]
&=\prod_{i=1}^{y}\mathbb{E}\Bigl(e^{tX_i}\Bigr)=\bigl[\,pe^{t}+(1-p)\,\bigr]^{y},\ t\in\mathbb{R}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\phi(t,y)&=\mathbb{E}\Bigl(e^{t(X_1+X_2+\cdots+X_{\sssig Y})}\Bigm\vert Y=y\Bigr)\\[0.45em]
&=\mathbb{E}\Bigl(e^{t(X_1+X_2+\cdots+X_y)}\Bigr)\\[0.45em]
&=\prod_{i=1}^{y}\mathbb{E}\Bigl(e^{tX_i}\Bigr)\\[0.45em]
&=\bigl[\,pe^{t}+(1-p)\,\bigr]^{y},\ t\in\mathbb{R}
\end{aligned}
$$

</div>

(2) 由上題已知
{: .topic-paren-item}

$$
\phi(t,y)=\bigl[\,pe^{t}+(1-p)\,\bigr]^{y},\ t\in\mathbb{R}
$$

則
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[\,\phi(t,Y)\,\bigr]&=\mathbb{E}\Bigl(\bigl[\,pe^{t}+(1-p)\,\bigr]^{Y}\Bigr)=\sum_{y=0}^{\infty}\bigl[\,pe^{t}+(1-p)\,\bigr]^{y}\,\frac{\,e^{-\lambda}\lambda^{y}\,}{y!}\\[0.45em]
&=e^{-\lambda}\sum_{y=0}^{\infty}\frac{\bigl(\lambda\,\bigl[\,pe^{t}+(1-p)\,\bigr]\bigr)^{y}}{y!}=e^{\lambda p(e^{t}-1)},\ t\in\mathbb{R}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[\,\phi(t,Y)\,\bigr]&=\mathbb{E}\Bigl(\bigl[\,pe^{t}+(1-p)\,\bigr]^{Y}\Bigr)\\[0.45em]
&=\sum_{y=0}^{\infty}\bigl[\,pe^{t}+(1-p)\,\bigr]^{y}\,\frac{\,e^{-\lambda}\lambda^{y}\,}{y!}\\[0.45em]
&=e^{-\lambda}\sum_{y=0}^{\infty}\frac{\bigl(\lambda\,\bigl[\,pe^{t}+(1-p)\,\bigr]\bigr)^{y}}{y!}\\[0.45em]
&=e^{\lambda p(e^{t}-1)},\ t\in\mathbb{R}
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

事實上，這題是[上一個問題](#ex-store-laptop-purchases)第 (3) 小題的另一種做法，也就是由 [mgf](/teaching-topics/moment-generating-functions/#def-mgf) 來確認 $\sum_{i=1}^{Y}X_i$ 的分配。

儘管我們還沒有正式講到多元隨機變數的 mgf 以及其衍生的計算方式，但是讀者仍然可以把 $e^{t(X_1+X_2+\cdots+X_{\sssig Y})}$ 當成 $X_1, X_2, \ldots, X_{\sssig Y}$ 的函數，並且利用彼此獨立的性質，改為邊際的 mgf 相乘，從而得到所求結果；而這也是[雙重期望值定理](/teaching-topics/double-expectation-theorem/#thm-double-expectation)的另一個應用，即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\bigl[e^{t(X_1+\cdots+X_{\sssig Y})}\bigr]=\mathbb{E}\Bigl(\mathbb{E}\bigl[e^{t(X_1+\cdots+X_{\sssig Y})}\bigm\vert Y\bigr]\Bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[e^{t(X_1+\cdots+X_{\sssig Y})}\bigr]&=\mathbb{E}\Bigl(\mathbb{E}\bigl[e^{t(X_1+\cdots+X_{\sssig Y})}\bigm\vert Y\bigr]\Bigr)
\end{aligned}
$$

</div>

</div>

<div id="ex-gambler-ruin-fair-coin" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.33 <span lang="en">(The gambler’s ruin problem)</span></div>

<div lang="en" markdown="1">
Suppose that Mr. Adams and Ms. Smith wager on a coin that is tossed again and again. Mr. Adams holds $a$ dollars and Ms. Smith holds $b$ dollars once play begins; after each toss the one who loses hands a single dollar to the one who wins, and play carries on until one of the two has been ruined. Taking as given that the mathematical expectation of either player is zero in an equitable game, find the probability that Mr. Adams takes the $b$ dollars of Ms. Smith before parting with his own $a$ dollars. Please list the steps by which this probability is obtained.
</div>

令 $X_i$ 表示第 $i$ 次賭局，Mr. Adams 增加的資產量，且由題意可知 $\mathbb{E}(X_i)=0$

定義 $S_{\sssig N}=a+\sum_{i=1}^{N}X_i$ 表示第 $N$ 次賭局後 Mr. Adams 的總資產量

又令

$$
T=\min\lbrace\,n\mid S_n=0,\ S_n=a+b\,\rbrace
$$

則由[沃德等式](#thm-wald-identity)可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(S_{\sssig T})=\mathbb{E}\Bigl(a+\sum_{i=1}^{T}X_i\Bigr)=a+\mathbb{E}(T)\,\mathbb{E}(X_i)=a
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(S_{\sssig T})&=\mathbb{E}\Bigl(a+\sum_{i=1}^{T}X_i\Bigr)\\[0.45em]
&=a+\mathbb{E}(T)\,\mathbb{E}(X_i)=a
\end{aligned}
$$

</div>

又由於 $S_{\sssig T}$ 只可能是 $0$ 或是 <span class="text-nowrap">$a+b$，</span>故我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(S_{\sssig T})&=0\times\mathbb{P}(S_{\sssig T}=0)+(a+b)\times\mathbb{P}(S_{\sssig T}=a+b)\\[0.45em]
&=(a+b)\times\mathbb{P}(S_{\sssig T}=a+b)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(S_{\sssig T})&=0\times\mathbb{P}(S_{\sssig T}=0)\\[0.2em]
&\qquad+(a+b)\times\mathbb{P}(S_{\sssig T}=a+b)\\[0.45em]
&=(a+b)\times\mathbb{P}(S_{\sssig T}=a+b)
\end{aligned}
$$

</div>

則所求為

$$
\mathbb{P}(S_{\sssig T}=a+b)=\frac{a}{\,a+b\,}
$$

</div>

<div id="ex-gambler-ruin-biased" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.34</div>

<div lang="en" markdown="1">
Two gamblers, A and B, stake money on a coin that is tossed one time after another. A receives one unit from B whenever a toss shows a head, whereas A hands one unit to B whenever a toss shows a tail, and the play carries on until one of the two has nothing left. Suppose that the tosses are independent of one another and that a head appears on any one toss with probability <span class="text-nowrap">$p$.</span> What is the probability that A finishes holding all of the money, given that A begins with $i$ units and B begins with $N-i$ units?
</div>

令 $E$ 表示 A 最後贏走所有錢的事件、$H$ 表示硬幣出現正面之事件。

另外令 $p_{\sssig i}$ 表示由 A 有 $i$ 元且 B 有 $N-i$ 元的情況下開始遊戲時，最終由 A 贏走所有 $N$ 元的機率，則依題意，我們可知 <span class="text-nowrap">$\mathbb{P}(H)=p$，</span><span class="text-nowrap">$p_{\sssig 0}=0$，</span>$p_{\sssig N}=1$ 且

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
p_{\sssig i}=\mathbb{P}(E)&=\mathbb{P}(E\mid H)\,\mathbb{P}(H)+\mathbb{P}(E\mid H^{\prime})\,\mathbb{P}(H^{\prime})\\[0.45em]
&=p_{\sssig i+1}\times p+p_{\sssig i-1}\times(1-p)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig i}=\mathbb{P}(E)&=\mathbb{P}(E\mid H)\,\mathbb{P}(H)\\[0.2em]
&\qquad+\mathbb{P}(E\mid H^{\prime})\,\mathbb{P}(H^{\prime})\\[0.45em]
&=p_{\sssig i+1}\times p\\[0.2em]
&\qquad+p_{\sssig i-1}\times(1-p)
\end{aligned}
$$

</div>

又令 <span class="text-nowrap">$q=1-p$，</span>則我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
p_{\sssig i}=p\times p_{\sssig i+1}+q\times p_{\sssig i-1},\ \ i=1,2,\ldots,N-1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig i}&=p\times p_{\sssig i+1}+q\times p_{\sssig i-1},\\[0.45em]
&\qquad i=1,2,\ldots,N-1
\end{aligned}
$$

</div>

其中，由於 <span class="text-nowrap">$p+q=p+(1-p)=1$，</span>故我們可將上式改寫為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
p_{\sssig i}(p+q)=p\times p_{\sssig i}+q\times p_{\sssig i}=p\times p_{\sssig i+1}+q\times p_{\sssig i-1},\ \ i=1,2,\ldots,N-1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig i}(p+q)&=p\times p_{\sssig i}+q\times p_{\sssig i}\\[0.45em]
&=p\times p_{\sssig i+1}+q\times p_{\sssig i-1},\\[0.45em]
&\qquad i=1,2,\ldots,N-1
\end{aligned}
$$

</div>

並進一步整理可以得到

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
p_{\sssig i+1}-p_{\sssig i}=\frac{q}{p}(p_{\sssig i}-p_{\sssig i-1}),\ \ i=1,2,\ldots,N-1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig i+1}-p_{\sssig i}&=\frac{q}{p}(p_{\sssig i}-p_{\sssig i-1}),\\[0.45em]
&\qquad i=1,2,\ldots,N-1
\end{aligned}
$$

</div>

再由於 <span class="text-nowrap">$p_{\sssig 0}=0$，</span>我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
p_{\sssig 2}-p_{\sssig 1}&=\frac{q}{p}(p_{\sssig 1}-p_{\sssig 0})=\frac{q}{p}\,p_{\sssig 1}\\[0.45em]
p_{\sssig 3}-p_{\sssig 2}&=\frac{q}{p}(p_{\sssig 2}-p_{\sssig 1})=\Bigl(\frac{q}{p}\Bigr)^{2}\,p_{\sssig 1}\\[0.45em]
&\ \ \vdots\\[0.45em]
p_{\sssig N}-p_{\sssig N-1}&=\frac{q}{p}(p_{\sssig N-1}-p_{\sssig N-2})=\Bigl(\frac{q}{p}\Bigr)^{\sssig N-1}\,p_{\sssig 1}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig 2}-p_{\sssig 1}&=\frac{q}{p}(p_{\sssig 1}-p_{\sssig 0})=\frac{q}{p}\,p_{\sssig 1}\\[0.45em]
p_{\sssig 3}-p_{\sssig 2}&=\frac{q}{p}(p_{\sssig 2}-p_{\sssig 1})=\Bigl(\frac{q}{p}\Bigr)^{2}\,p_{\sssig 1}\\[0.45em]
&\ \ \vdots\\[0.45em]
p_{\sssig N}-p_{\sssig N-1}&=\frac{q}{p}(p_{\sssig N-1}-p_{\sssig N-2})\\[0.2em]
&=\Bigl(\frac{q}{p}\Bigr)^{\sssig N-1}\,p_{\sssig 1}
\end{aligned}
$$

</div>

將前 $i$ 條等式之左式與右式各自加總之後可得

<div class="topic-math-layout topic-math-layout--desktop topic-math-follow-before" markdown="1">

$$
p_{\sssig i}-p_{\sssig 1}=\frac{q}{p}\,p_{\sssig 1}+\Bigl(\frac{q}{p}\Bigr)^{2}\,p_{\sssig 1}+\cdots+\Bigl(\frac{q}{p}\Bigr)^{\sssig i-1}\,p_{\sssig 1}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile topic-math-follow-before" markdown="1">

$$
\begin{aligned}
p_{\sssig i}-p_{\sssig 1}&=\frac{q}{p}\,p_{\sssig 1}+\Bigl(\frac{q}{p}\Bigr)^{2}\,p_{\sssig 1}\\[0.2em]
&\qquad+\cdots+\Bigl(\frac{q}{p}\Bigr)^{\sssig i-1}\,p_{\sssig 1}
\end{aligned}
$$

</div>

<div class="topic-math-follow" markdown="1">

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\Longrightarrow\ \ p_{\sssig i}=p_{\sssig 1}+\frac{q}{p}\,p_{\sssig 1}+\Bigl(\frac{q}{p}\Bigr)^{2}\,p_{\sssig 1}+\cdots+\Bigl(\frac{q}{p}\Bigr)^{\sssig i-1}\,p_{\sssig 1}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ p_{\sssig i}&=p_{\sssig 1}+\frac{q}{p}\,p_{\sssig 1}+\Bigl(\frac{q}{p}\Bigr)^{2}\,p_{\sssig 1}\\[0.2em]
&\qquad+\cdots+\Bigl(\frac{q}{p}\Bigr)^{\sssig i-1}\,p_{\sssig 1}
\end{aligned}
$$

</div>

</div>

由等比級數公式可知

$$
p_{\sssig i}=
\left\lbrace
\begin{array}{cl}
\dfrac{p_{\sssig 1}\Bigl[1-\bigl(\frac{q}{p}\bigr)^{i}\Bigr]}{1-\frac{q}{p}}, & \text{if}\ p\neq\frac{1}{2}\\[1.6em]
i\,p_{\sssig 1}, & \text{if}\ p=\frac{1}{2}
\end{array}
\right.
$$

又由於已知 <span class="text-nowrap">$p_{\sssig N}=1$，</span>故我們有

<div class="topic-math-follow-before" markdown="1">

$$
1=p_{\sssig N}=
\left\lbrace
\begin{array}{cl}
\dfrac{p_{\sssig 1}\Bigl[1-\bigl(\frac{q}{p}\bigr)^{\sssig N}\Bigr]}{1-\frac{q}{p}}, & \text{if}\ p\neq\frac{1}{2}\\[1.6em]
N\,p_{\sssig 1}, & \text{if}\ p=\frac{1}{2}
\end{array}
\right.
$$

</div>

<div class="topic-math-follow" markdown="1">

$$
\Longrightarrow\
p_{\sssig 1}=
\left\lbrace
\begin{array}{cl}
\dfrac{1-\frac{q}{p}}{1-\bigl(\frac{q}{p}\bigr)^{\sssig N}}, & \text{if}\ p\neq\frac{1}{2}\\[1.6em]
\dfrac{1}{N}, & \text{if}\ p=\frac{1}{2}
\end{array}
\right.
$$

</div>

由以上結果可知

$$
p_{\sssig i}=
\left\lbrace
\begin{array}{cl}
\dfrac{1-\bigl(\frac{q}{p}\bigr)^{i}}{1-\bigl(\frac{q}{p}\bigr)^{N}}, & \text{if}\ p\neq\frac{1}{2}\\[1.6em]
\dfrac{i}{N}, & \text{if}\ p=\frac{1}{2}
\end{array}
\right.
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

事實上，[Example 3.34](#ex-gambler-ruin-biased) 是 [Example 3.33](#ex-gambler-ruin-fair-coin) 的一般化類題，但解法卻大相徑庭，這是因為，在不曉得是否為公平賭局的情形下，我們沒有辦法應用資產增加量平均為 $0$ 的設定來規避 $\mathbb{E}(T)$ 的計算，因此應用[沃德等式](#thm-wald-identity)反而會讓解題變得更麻煩。

但是，於 [Example 3.33](#ex-gambler-ruin-fair-coin) 中，若已知

$$
\mathbb{P}(S_{\sssig T}=a+b)=\frac{a}{\,a+b\,}
$$

則我們確實可以反過來計算 <span class="text-nowrap">$\mathbb{E}(T)$，</span>作法如下:

<div class="topic-proof" markdown="1">
**Proof.**

由 [Example 3.33](#ex-gambler-ruin-fair-coin) 已知 $\mathbb{P}(S_{\sssig T}=a+b)$ $=$ $\frac{a}{\,a+b\,}$ 及 $\mathbb{E}(S_{\sssig T})=a$

且由於 $S_{\sssig T}$ 只可能是 $0$ 或 <span class="text-nowrap">$a+b$，</span>故知道

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(S_{\sssig T})&=\mathbb{E}(S_{\sssig T}^{2})-\bigl[\mathbb{E}(S_{\sssig T})\bigr]^{2}\\[0.45em]
&=\Bigl[0^{2}\,\mathbb{P}(S_{\sssig T}=0)+(a+b)^{2}\,\mathbb{P}(S_{\sssig T}=a+b)\Bigr]-a^{2}\\[0.45em]
&=(a+b)^{2}\times\frac{a}{\,a+b\,}-a^{2}=a\,(a+b)-a^{2}=ab
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(S_{\sssig T})&=\mathbb{E}(S_{\sssig T}^{2})-\bigl[\mathbb{E}(S_{\sssig T})\bigr]^{2}\\[0.45em]
&=\Bigl[0^{2}\,\mathbb{P}(S_{\sssig T}=0)\\[0.2em]
&\qquad+(a+b)^{2}\,\mathbb{P}(S_{\sssig T}=a+b)\Bigr]-a^{2}\\[0.45em]
&=(a+b)^{2}\times\frac{a}{\,a+b\,}-a^{2}\\[0.45em]
&=a\,(a+b)-a^{2}=ab
\end{aligned}
$$

</div>

又由[沃德等式](#thm-wald-identity)知

<div class="topic-math-layout topic-math-layout--desktop topic-math-follow-before" markdown="1">

$$
\mathrm{Var}(S_{\sssig T})=\mathrm{Var}(X_i)\,\mathbb{E}(T)+\bigl[\mathbb{E}(X_i)\bigr]^{2}\,\mathrm{Var}(T)=\mathrm{Var}(X)\,\mathbb{E}(T)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile topic-math-follow-before" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(S_{\sssig T})&=\mathrm{Var}(X_i)\,\mathbb{E}(T)\\[0.2em]
&\qquad+\bigl[\mathbb{E}(X_i)\bigr]^{2}\,\mathrm{Var}(T)\\[0.45em]
&=\mathrm{Var}(X)\,\mathbb{E}(T)\\[0.4em]
&\qquad\therefore\, \mathbb{E}(T)=\frac{\,\mathrm{Var}(S_{\sssig T})\,}{\mathrm{Var}(X)}=\frac{ab}{\,\mathrm{Var}(X)\,}
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

其中，雖然已知每回合的財產增量期望值為 $0$ (即 <span class="text-nowrap">$\mathbb{E}(X_i)=0$)，</span>但由於規則可能未必與此處相同，因此財產增量的變異數可能不同。

</div>

至此，我們已經將所有「給定條件下」的情形都看過了，讀者應該已經熟悉在這種情形之下的機率分配及其應用，也能夠以條件分配及其衍生的產物，進行加權平均，從而得到邊際產物 (包含分配、期望值與變異數)。

然而，儘管我們可以有各種方式取得邊際產物，但很多時候，我們並不會單純地只想看見邊際的產物而已，隨機變數之間**共同變化的情況**也會是我們所關注的重點之一，見[下列小節](/teaching-topics/cross-moments-joint-mgf/)。

## 本篇小結

[Theorem 3.12](#thm-wald-identity) 處理的是加總的項數本身也是隨機變數的情形。若 $X_1, X_2, \ldots$ 為獨立同分配的隨機變數，$N$ 是一個與它們獨立的非負整數隨機變數，則 $S_{\sssig N}=\sum_{i=1}^{N}X_i$ 的期望值為 <span class="text-nowrap">$\mu_{\sssig X}\mu_{\sssig N}$，</span>變異數則為 <span class="text-nowrap">$\sigma_{\sssig X}^{2}\mu_{\sssig N}+\mu_{\sssig X}^{2}\sigma_{\sssig N}^{2}$。</span>它的證明分別以[雙重期望值定理](/teaching-topics/double-expectation-theorem/#thm-double-expectation)與[變異數分解定理](/teaching-topics/variance-decomposition-theorem/#thm-var-decom-thm)完成，所需的兩個條件量是 $\mathbb{E}(S_{\sssig N}\mid N=n)$ $=$ $n\mu_{\sssig X}$ 與 $\mathrm{Var}(S_{\sssig N}\mid N=n)$ $=$ $n\sigma_{\sssig X}^{2}$ 這兩條式子。

[Example 3.31](#ex-store-laptop-purchases) 是沃德等式最直接的用法: 每日進入商店的人數為卜瓦松分配，每位顧客購買 laptop PC 之數量則為 <span class="text-nowrap">$\mathrm{Ber}(p)$，</span>兩者合起來得到 $\mathbb{E}(X)=\lambda p$ 與 <span class="text-nowrap">$\operatorname{SD}(X)=\sqrt{\lambda p}$；</span>再以[全機率定理](/teaching-topics/conditional-law-of-total-probability/#thm-law-of-total-prob-r-v)把條件 pmf 依 $N$ 的機率加權，可得 $\mathbb{P}(X=0)$ $=$ $e^{-\lambda p}$ 以及 <span class="text-nowrap">$X\sim\mathrm{Poi}(\lambda p)$。</span>這裡的加總起點之所以是 $x$ 而非 <span class="text-nowrap">$0$，</span>是因為在固定 $X=x$ 之後，$n$ 不可能小於 <span class="text-nowrap">$x$。</span>[Example 3.32](#ex-poisson-random-sum) 改用另一種做法。先求出給定 $Y=y$ 之下的 $\phi(t,y)$ $=$ $\bigl[\,pe^{t}+(1-p)\,\bigr]^{y}$ 這條式子，再對 $Y$ 取一次期望值，得到 <span class="text-nowrap">$e^{\lambda p(e^{t}-1)}$，</span>正是同一個分配的 mgf。

[Example 3.33](#ex-gambler-ruin-fair-coin) 與 [Example 3.34](#ex-gambler-ruin-biased) 是同一個賭徒破產問題的兩種版本。公平賭局之下每回合的資產增量期望值為 <span class="text-nowrap">$0$，</span>沃德等式因而給出 <span class="text-nowrap">$\mathbb{E}(S_{\sssig T})=a$，</span>再配合 $S_{\sssig T}$ 只有 $0$ 與 $a+b$ 兩種取值，即得 $\mathbb{P}(S_{\sssig T}=a+b)$ $=$ <span class="text-nowrap">$\frac{a}{\,a+b\,}$。</span>不公平賭局之下沒有這個設定可用，$\mathbb{E}(T)$ 無法迴避，故改由 $p_{\sssig i}$ $=$ $p\,p_{\sssig i+1}+q\,p_{\sssig i-1}$ 這條關係式逐項相減、再以等比級數求和，得到 $p\neq\frac{1}{2}$ 與 $p=\frac{1}{2}$ 兩種情形的答案。反過來說，公平賭局的版本一旦知道了破產機率，也可以由變異數倒推出 $\mathbb{E}(T)$ $=$ <span class="text-nowrap">$\frac{ab}{\,\mathrm{Var}(X)\,}$。</span>

至此，所有「給定條件下」的情形都已看過。[下一篇](/teaching-topics/cross-moments-joint-mgf/)轉而處理兩個隨機變數共同變化的情況，由交叉動差與[聯合動差母函數](/teaching-topics/cross-moments-joint-mgf/#def-joint-mgf)談起。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
