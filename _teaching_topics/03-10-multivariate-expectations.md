---
title: "多元隨機變數的期望值"
subtitle: "Expectations of Multivariate Random Variables"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 10
order: 310
permalink: /lecture-notes/multivariate-expectations/
date: 2026-08-12
published: false
excerpt: "本篇把期望值推廣到二元的情形: 離散型以 joint pmf 作雙重加總，連續型以 joint pdf 作二重積分，被加總或被積分的都是實值函數 $g(x,y)$ 的值。把 $g$ 設定為 $X$ 或 $Y$，所得的正是邊際分配的期望值 $\\mathbb{E}(X)$ 與 $\\mathbb{E}(Y)$。線性組合仍然可以與期望值交換，相乘這種非線性的設定則不然，只有在 $X$ 與 $Y$ 獨立時，$\\mathbb{E}\\bigl[g(X)h(Y)\\bigr]$ 才會等於兩個期望值相乘；反過來說並不成立。最後以四道例題求兩個獨立隨機變數乘積的變異數、空盒個數的期望值與變異數，以及以一階泰勒展式求得的變異數近似值。"
---

[上一篇](/lecture-notes/independent-random-variables/)先以 [Theorem 3.3](/lecture-notes/independent-random-variables/#thm-multiplication-rule-r-v) 說明聯合機率函數如何由條件機率函數與邊際機率函數相乘而得，再以 [Definition 3.10](/lecture-notes/independent-random-variables/#def-indep-r-v) 給出[獨立隨機變數](/lecture-notes/independent-random-variables/#def-indep-r-v)的定義。本篇把[期望值](/lecture-notes/expectation/#def-expectation)推廣到二元的情形。

單變數的時候，[Theorem 2.9](/lecture-notes/properties-of-expectation/#thm-expectation-of-function) 說明 $g(X)$ 的期望值如何由 $X$ 的機率函數求得，[Theorem 2.10](/lecture-notes/properties-of-expectation/#thm-expectation-linearity) 則給出期望值與線性組合可以交換的性質。本篇的四個定理依同樣的次序排列。先說明二元的期望值如何由[聯合機率質量函數](/lecture-notes/random-vectors-joint-pmf/#def-joint-pmf)或[聯合機率密度函數](/lecture-notes/joint-probability-density-functions/#def-joint-pdf)求得，再給出線性組合的性質，接著處理相乘這種非線性的設定在兩個變數獨立之下的特例，最後把[變異數](/lecture-notes/variance/#def-variance)的定義一併推廣。

本篇最後有四道例題。前兩道都在求兩個獨立隨機變數乘積的變異數，第三道求 $n$ 個球投入 $r$ 個盒子之後空盒個數的期望值與變異數，第四道則以一階泰勒展式求一個四變數函數的變異數近似值。

<div id="thm-multi-exp" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 3.4 (多元隨機變數的期望值, expectation of multivariate random variables)</div>

令 $(X, Y)$ 為二元**離散型**隨機變數，其值域為 <span class="text-nowrap">$\mathcal{R}\_{\sssig XY}$，</span>joint pmf 為 $p\_{\sssig XY}(x, y)$

若 $g(\cdot, \cdot)$ 為一實值函數且

$$
\mathop{\sum\sum}\limits_{(x, y)\in\mathcal{R}_{\sssig XY}}\lvert g(x, y)\rvert\,p_{\sssig XY}(x,y)<\infty
$$

則

$$
\mathbb{E}\bigl[g(X,Y)\bigr]=\mathop{\sum\sum}\limits_{(x,y)\in\mathcal{R}_{\sssig XY}}g(x,y)\,p_{\sssig XY}(x,y)
$$

令 $(X, Y)$ 為二元**連續型**隨機變數，其值域為 <span class="text-nowrap">$\mathcal{R}\_{\sssig XY}$，</span>joint pdf 為 $f\_{\sssig XY}(x, y)$

若 $g(\cdot, \cdot)$ 為一實值函數且

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\iint_{(x,y)\in\mathcal{R}_{\sssig XY}}\lvert g(x,y)\rvert\,f_{\sssig XY}(x,y)\,dx\,dy<\infty
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\iint_{(x,y)\in\mathcal{R}_{\sssig XY}}\lvert g(x,y)\rvert\,f_{\sssig XY}(x,y)\,dx\,dy\\[0.2em]
&\qquad\qquad\qquad <\infty
\end{aligned}
$$

</div>

則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\bigl[g(X,Y)\bigr]=\iint_{(x,y)\in\mathcal{R}_{\sssig XY}}g(x,y)\,f_{\sssig XY}(x,y)\,dx\,dy
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[g(X,Y)\bigr]&=\iint_{(x,y)\in\mathcal{R}_{\sssig XY}}g(x,y)\,f_{\sssig XY}(x,y)\,dx\,dy
\end{aligned}
$$

</div>

</div>

[Theorem 3.4](#thm-multi-exp) 有一些地方需要注意:

(1) 與 [Theorem 2.9](/lecture-notes/properties-of-expectation/#thm-expectation-of-function) 相同，這裡的 $g(\cdot, \cdot)$ 可以是任意的實值函數，一旦我們設定了 $g(X, Y) = X$ 或 $g(X, Y) = Y$ 這樣的函數，則 [Theorem 3.4](#thm-multi-exp) 的期望值將會變成 $\mathbb{E}(X)$ 與 <span class="text-nowrap">$\mathbb{E}(Y)$。</span>
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

讀者或許會好奇，這樣與邊際分配的期望值 $\mathbb{E}(X)$ 和 $\mathbb{E}(Y)$ 會相同嗎？答案是肯定的，我們將這個特例以連續型隨機變數及 $g(X,Y) = X$ 證明在下方:

<div class="topic-proof" markdown="1">
**Proof.**

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\iint_{(x,y)\in\mathcal{R}_{\sssig XY}}x\,f_{\sssig XY}(x,y)\,dx\,dy\\[0.45em]
&=\iint_{(x,y)\in\mathcal{R}_{\sssig XY}}x\,f_{\sssig XY}(x,y)\,dy\,dx\\[0.45em]
&=\int_{x\in\mathcal{R}_{\sssig X}}x\Biggl[\int_{y\in\mathcal{R}_{\sssig Y}}f_{\sssig XY}(x,y)\,dy\Biggr]\,dx\\[0.45em]
&=\int_{x\in\mathcal{R}_{\sssig X}}x\Bigl[f_{\sssig X}(x)\Bigr]\,dx
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\iint_{(x,y)\in\mathcal{R}_{\sssig XY}}x\,f_{\sssig XY}(x,y)\,dx\,dy\\[0.45em]
&=\iint_{(x,y)\in\mathcal{R}_{\sssig XY}}x\,f_{\sssig XY}(x,y)\,dy\,dx\\[0.45em]
&=\int_{x\in\mathcal{R}_{\sssig X}}x\Biggl[\int_{y\in\mathcal{R}_{\sssig Y}}f_{\sssig XY}(x,y)\,dy\Biggr]\,dx\\[0.45em]
&=\int_{x\in\mathcal{R}_{\sssig X}}x\Bigl[f_{\sssig X}(x)\Bigr]\,dx
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

上列性質的直觀意義在於**與 $X$ 無關的地方可以先行積分，其效果相當於「將 $Y$ 都積分掉」，即相當於「留下 $X$ 的邊際 pdf」**，故當然會等於直接算邊際期望值 <span class="text-nowrap">$\mathbb{E}(X)$。</span>

</div>

(2) 有了多元隨機變數的期望值，我們便能夠進行許多運算，但我們應該先關心的是，如同 [Theorem 2.9](/lecture-notes/properties-of-expectation/#thm-expectation-of-function) 與 [Theorem 2.10](/lecture-notes/properties-of-expectation/#thm-expectation-linearity) 的關係一般，[Theorem 3.4](#thm-multi-exp) 也有類似 [Theorem 2.10](/lecture-notes/properties-of-expectation/#thm-expectation-linearity) 的性質，下面馬上就來看看這個性質。
{: .topic-paren-item}

<div id="thm-multi-exp-proper" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 3.5 (多元隨機變數期望值的性質, properties of expectations of multivariate random variables)</div>

若 $(X, Y)$ 為二元隨機變數，$g_1(\cdot,\cdot),\ldots,g_k(\cdot,\cdot)$ 為實值函數且 $a_1,\ldots,a_k,b$ 為常數，則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\biggl[\sum_{i=1}^{k}a_i\,g_i(X,Y)+b\biggr]=\sum_{i=1}^{k}a_i\,\mathbb{E}\bigl[g_i(X,Y)\bigr]+b
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\biggl[\sum_{i=1}^{k}a_i\,g_i(X,Y)+b\biggr]&=\sum_{i=1}^{k}a_i\,\mathbb{E}\bigl[g_i(X,Y)\bigr]+b
\end{aligned}
$$

</div>

</div>

上述定理只強調了，兩個隨機變數間的線性關係與期望值是可以交換的，卻沒有說到非線性的函數具不具有可以與期望值交換。

在考慮兩個 (或更多) 變數時，$g(\cdot, \cdot)$ 的設定就變得比較複雜，因為可能出現變數之間相乘的情況。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

單變數的時候，不論 $X$ 的函數怎麼相乘，由於只有一個變數，結果都還會是 $X$ 的函數。

</div>

當然，相乘不是線性函數，所以一般的狀況下，我們只能利用 [Theorem 3.5](#thm-multi-exp-proper)，將係數與常數提出去，再利用 [Theorem 3.4](#thm-multi-exp) 計算，但在 $X$ $\indep$ $Y$ 的前提以及特殊的相乘設定之下，這個計算將變得容易許多，詳見下列定理。

<div id="thm-indep-exp" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 3.6 (獨立隨機變數函數乘積的期望值, expectation of a product under independence)</div>

若 $X$ $\indep$ <span class="text-nowrap">$Y$，</span>且 $g(X)$ 與 $h(Y)$ 分別為 $X$ 與 $Y$ 的任意函數轉換，則

$$
\mathbb{E}\bigl[g(X)\,h(Y)\bigr]=\mathbb{E}\bigl[g(X)\bigr]\,\mathbb{E}\bigl[h(Y)\bigr]
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.**

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[g(X)h(Y)\bigr]&=\int_{-\infty}^{\infty}\int_{-\infty}^{\infty}g(x)\,h(y)\,f_{\sssig XY}(x, y)\,dx\,dy\\[0.45em]
&=\int_{-\infty}^{\infty}\int_{-\infty}^{\infty}g(x)\,h(y)\,f_{\sssig X}(x)\,f_{\sssig Y}(y)\,dx\,dy\\[0.45em]
&=\int_{-\infty}^{\infty}g(x)\,f_{\sssig X}(x)\,dx\,\int_{-\infty}^{\infty}h(y)\,f_{\sssig Y}(y)\,dy\\[0.45em]
&=\mathbb{E}\bigl[g(X)\bigr]\,\mathbb{E}\bigl[h(Y)\bigr]
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[&g(X)h(Y)\bigr] =\int_{-\infty}^{\infty}\int_{-\infty}^{\infty}g(x)\,h(y)\,f_{\sssig XY}(x, y)\,dx\,dy\\[0.45em]
&=\int_{-\infty}^{\infty}\int_{-\infty}^{\infty}g(x)\,h(y)\,f_{\sssig X}(x)\,f_{\sssig Y}(y)\,dx\,dy\\[0.45em]
&=\int_{-\infty}^{\infty}g(x)\,f_{\sssig X}(x)\,dx\,\int_{-\infty}^{\infty}h(y)\,f_{\sssig Y}(y)\,dy\\[0.45em]
&=\mathbb{E}\bigl[g(X)\bigr]\,\mathbb{E}\bigl[h(Y)\bigr]
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

讀者應該已經發現，多數需要 $X$ $\indep$ $Y$ 作為前提的定理，其原因大部分都是因為需要 $f_{\sssig XY}(x, y)$ $=$ $f_{\sssig X}(x)\,f_{\sssig Y}(y)$ 的性質。

但需要特別注意的是，「若 $X$ $\indep$ $Y$ 則此性質成立」不表示「若此性質成立則 $X$ $\indep$ <span class="text-nowrap">$Y$」，</span>這個反向敘述在絕大多數時候並不成立。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

稍後我們會看見，$X$ $\indep$ $Y$ $\Longrightarrow$ $\mathbb{E}(XY)$ $=$ <span class="text-nowrap">$\mathbb{E}(X)\mathbb{E}(Y)$，</span>此即 $X$ 與 $Y$ 獨立導致 $X$ 與 $Y$ **[零相關](/lecture-notes/covariance/#def-covariance) <span lang="en">(uncorrelated)</span>**，但這個敘述的逆命題一般而言卻是不對的。

</div>

上述定理常見的用途在於，尋找 $X$ 與 $Y$ 的**[交叉動差](/lecture-notes/cross-moments-joint-mgf/#def-cross-moment) (cross moment)**，即 <span class="text-nowrap">$\mathbb{E}(XY)$，</span>在 $X$ $\indep$ $Y$ 的狀況下，$\mathbb{E}(XY)$ $=$ <span class="text-nowrap">$\mathbb{E}(X)\mathbb{E}(Y)$。</span>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個特例在稍後的小節介紹**[共變異數](/lecture-notes/covariance/#def-covariance) <span lang="en">(covariance)</span>** 的時候會談到。

</div>

<div id="thm-multi-function-var" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 3.7 (多元隨機變數的變異數, variance of multivariate random variables)</div>

若 $(X, Y)$ 為二元隨機變數，$g(\cdot, \cdot)$ 為一實值可測函數，且 $\mathbb{E}\bigl[g^2(X, Y)\bigr]$ $<$ <span class="text-nowrap">$\infty$，</span>則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}\bigl[g(X, Y)\bigr]=\mathbb{E}\Bigl[\bigl(g(X, Y)-\mathbb{E}\bigl[g(X, Y)\bigr]\bigr)^{2}\Bigr]
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}\bigl[g(X, Y)\bigr]&=\mathbb{E}\Bigl[\bigl(g(X, Y)-\mathbb{E}\bigl[g(X, Y)\bigr]\bigr)^{2}\Bigr]
\end{aligned}
$$

</div>

</div>

這個定理事實上就是 [Theorem 2.12](/lecture-notes/variance/#thm-variance-of-function) 的延伸版本。

<div id="ex-independent-product-expectation" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.14</div>

令 $X$ $\indep$ $Y$ 為二獨立隨機變數，$\mathbb{E}\bigl(Y^2\bigr)$ 存在且 $\mathbb{E}(X)$ $=$ $\mathrm{Var}(X)$ $=$ <span class="text-nowrap">$0$，</span>求 $\mathrm{Var}(XY)$ 為何？

由於 $\mathbb{E}(X)$ $=$ $\mathrm{Var}(X)$ $=$ $0$ 且 $X$ $\indep$ $Y$

故

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\bigl(X^2\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}=0\qquad\therefore\, \mathbb{E}\bigl(X^2\bigr)=\mathbb{E}(X)=0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\mathbb{E}\bigl(X^2\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}=0\qquad\therefore\, \mathbb{E}\bigl(X^2\bigr)=\mathbb{E}(X)=0
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(XY)&=\mathbb{E}\bigl[(XY)^2\bigr]-\bigl[\mathbb{E}(XY)\bigr]^{2}=\mathbb{E}\bigl[X^2Y^2\bigr]-\bigl[\mathbb{E}(X)\mathbb{E}(Y)\bigr]^{2}\\[0.45em]
&=\mathbb{E}\bigl(X^2\bigr)\,\mathbb{E}\bigl(Y^2\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}\,\bigl[\mathbb{E}(Y)\bigr]^{2}\\[0.45em]
&=0\times\mathbb{E}\bigl(Y^2\bigr)-0^2\times\bigl[\mathbb{E}(Y)\bigr]^{2}=0
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(XY)&=\mathbb{E}\bigl[(XY)^2\bigr]-\bigl[\mathbb{E}(XY)\bigr]^{2}\\[0.45em]
&=\mathbb{E}\bigl[X^2Y^2\bigr]-\bigl[\mathbb{E}(X)\mathbb{E}(Y)\bigr]^{2}\\[0.45em]
&=\mathbb{E}\bigl(X^2\bigr)\,\mathbb{E}\bigl(Y^2\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}\,\bigl[\mathbb{E}(Y)\bigr]^{2}\\[0.45em]
&=0\times\mathbb{E}\bigl(Y^2\bigr)-0^2\times\bigl[\mathbb{E}(Y)\bigr]^{2}=0
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

在[第二章談變異數的性質](/lecture-notes/variance/#thm-variance-properties)中，我們曾經提過退化隨機變數 <span lang="en">(degenerate random variable)</span>，此處的 $X$ 正是這個概念。直觀上而言，讀者不妨將其視為一個常數 <span class="text-nowrap">$0$，</span>如此一來，這個問題就幾乎等同於在問 <span class="text-nowrap">$\mathrm{Var}(0\,Y)$，</span>其結果便顯得很直觀。

</div>

<div id="ex-exponential-product-expectation" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.15</div>

<div lang="en" markdown="1">
Suppose that $X$ and $Y$ are independent random variables whose expected values are $\mu_1$ and <span class="text-nowrap">$\mu_2$,</span> and whose variances are $\sigma^2_1$ and <span class="text-nowrap">$\sigma^2_2$.</span> Determine $\mathrm{Var}(XY)$ in terms of these four quantities.
</div>

由題意敘述可知 $X$ $\indep$ <span class="text-nowrap">$Y$，</span>故

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\mathbb{E}(XY)=\mathbb{E}(X)\mathbb{E}(Y)=\mu_1\,\mu_2\\[0.45em]
\mathbb{E}\bigl[(XY)^2\bigr]=\mathbb{E}(X^2)\mathbb{E}(Y^2)=(\sigma^2_1+\mu_1^2)(\sigma_2^2+\mu_2^2)
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(XY)&=\mathbb{E}(X)\mathbb{E}(Y)=\mu_1\,\mu_2\\[0.45em]
\mathbb{E}\bigl[(XY)^2\bigr]&=\mathbb{E}(X^2)\mathbb{E}(Y^2)\\[0.2em]
&=(\sigma^2_1+\mu_1^2)(\sigma_2^2+\mu_2^2)
\end{aligned}
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(XY)&=\mathbb{E}\bigl[(XY)^2\bigr]-\bigl[\mathbb{E}(XY)\bigr]^{2}=\mathbb{E}\bigl[X^2Y^2\bigr]-\bigl[\mathbb{E}(X)\mathbb{E}(Y)\bigr]^{2}\\[0.45em]
&=(\sigma^2_1+\mu_1^2)(\sigma_2^2+\mu_2^2)-(\mu_1\,\mu_2)^{2}=\mu_1^2\,\sigma_2^2+\mu_2^2\,\sigma_1^2+\sigma_1^2\,\sigma_2^2
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(XY)&=\mathbb{E}\bigl[(XY)^2\bigr]-\bigl[\mathbb{E}(XY)\bigr]^{2}\\[0.45em]
&=\mathbb{E}\bigl[X^2Y^2\bigr]-\bigl[\mathbb{E}(X)\mathbb{E}(Y)\bigr]^{2}\\[0.45em]
&=(\sigma^2_1+\mu_1^2)(\sigma_2^2+\mu_2^2)-(\mu_1\,\mu_2)^{2}\\[0.45em]
&=\mu_1^2\,\sigma_2^2+\mu_2^2\,\sigma_1^2+\sigma_1^2\,\sigma_2^2
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個結果顯示，即便是在 $X$ $\indep$ $Y$ 的條件下，$\mathrm{Var}(XY)$ 也不會與 $\mathrm{Var}(X)\mathrm{Var}(Y)$ 相等。

</div>

<div id="ex-balls-into-boxes-empty" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.16</div>

<div lang="en" markdown="1">
Suppose that $n$ balls are placed at random into $r$ boxes, and that $X_i$ takes the value $1$ when box $i$ receives no ball and the value $0$ otherwise.

<ol class="topic-list-paren">
  <li>Evaluate <span class="text-nowrap">$\mathbb{E}(X_i)$.</span></li>
  <li>Evaluate $\mathbb{E}(X_i\,X_j)$ for <span class="text-nowrap">$i\neq j$.</span></li>
  <li>Suppose that $S_r$ is the number of boxes that receive no ball, and determine <span class="text-nowrap">$\mathbb{E}(S_r)$.</span></li>
  <li>Determine <span class="text-nowrap">$\mathrm{Var}(S_r)$.</span></li>
</ol>
</div>

(1) 由題意敘述可知
{: .topic-paren-item}

$$
X_i=
\left\lbrace
\begin{array}{c@{\quad}l}
1, & \text{if box $i$ is empty}\\[0.4em]
0, & \text{otherwise}
\end{array}
\right.
$$

故
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(X_i)=1\,\mathbb{P}(X_i=1)+0\,\mathbb{P}(X_i=0)=\mathbb{P}(X_i=1)=\frac{\,(r-1)^n\,}{r^n}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X_i)&=1\,\mathbb{P}(X_i=1)+0\,\mathbb{P}(X_i=0)\\[0.45em]
&=\mathbb{P}(X_i=1)=\frac{\,(r-1)^n\,}{r^n}
\end{aligned}
$$

</div>

(2)
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(X_i\,X_j)=\mathbb{P}(X_i\,X_j=1)=\mathbb{P}(X_i=1,X_j=1)=\frac{\,(r-2)^n\,}{r^n}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X_i\,X_j)&=\mathbb{P}(X_i\,X_j=1)\\[0.45em]
&=\mathbb{P}(X_i=1,X_j=1)=\frac{\,(r-2)^n\,}{r^n}
\end{aligned}
$$

</div>

(3) 依照題目敘述，可令 $S_r=\sum_{i=1}^{r}X_i$ 表示空盒總數，則
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(S_r)=\mathbb{E}(X_1+\cdots+X_r)=r\,\mathbb{E}(X_1)=r\left[\frac{\,(r-1)^n\,}{r^n}\right]=\frac{\,(r-1)^n\,}{r^{n-1}}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(S_r)&=\mathbb{E}(X_1+\cdots+X_r)=r\,\mathbb{E}(X_1)\\[0.45em]
&=r\left[\frac{\,(r-1)^n\,}{r^n}\right]=\frac{\,(r-1)^n\,}{r^{n-1}}
\end{aligned}
$$

</div>

(4) 承上題假設，可以知道
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(S_r^2)&=\mathbb{E}\bigl[(X_1+\cdots+X_r)^2\bigr]=\mathbb{E}\!\left(\sum_{i=1}^{r}X_i^2+\mathop{\sum\sum}\limits_{i\neq j}X_i\,X_j\right)\\[0.45em]
&=\sum_{i=1}^{r}\mathbb{E}(X_i^2)+2\mathop{\sum\sum}\limits_{i<j}\mathbb{E}(X_i\,X_j)\\[0.45em]
&=r\left[\frac{\,(r-1)^n\,}{r^n}\right]+r(r-1)\left[\frac{\,(r-2)^n\,}{r^n}\right]
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(S_r^2)&=\mathbb{E}\bigl[(X_1+\cdots+X_r)^2\bigr]\\[0.45em]
&=\mathbb{E}\!\left(\sum_{i=1}^{r}X_i^2+\mathop{\sum\sum}\limits_{i\neq j}X_i\,X_j\right)\\[0.45em]
&=\sum_{i=1}^{r}\mathbb{E}(X_i^2)+2\mathop{\sum\sum}\limits_{i<j}\mathbb{E}(X_i\,X_j)\\[0.45em]
&=r\left[\frac{\,(r-1)^n\,}{r^n}\right]\\[0.45em]
&\qquad +r(r-1)\left[\frac{\,(r-2)^n\,}{r^n}\right]
\end{aligned}
$$

</div>

故
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(S_r)&=\mathbb{E}(S_r^2)-\bigl[\mathbb{E}(S_r)\bigr]^{2}\\[0.45em]
&=r\left[\frac{\,(r-1)^n\,}{r^n}\right]+r(r-1)\left[\frac{\,(r-2)^n\,}{r^n}\right]-\left[\frac{\,(r-1)^n\,}{r^{n-1}}\right]^{2}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(S_r)&=\mathbb{E}(S_r^2)-\bigl[\mathbb{E}(S_r)\bigr]^{2}\\[0.45em]
&=r\left[\frac{\,(r-1)^n\,}{r^n}\right]\\[0.45em]
&\qquad+r(r-1)\left[\frac{\,(r-2)^n\,}{r^n}\right]\\[0.45em]
&\qquad-\left[\frac{\,(r-1)^n\,}{r^{n-1}}\right]^{2}
\end{aligned}
$$

</div>

</div>

<div id="ex-structure-load-expectation" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.17</div>

<div lang="en" markdown="1">
Suppose that the load-bearing capacity of a structure is written as <span class="text-nowrap">$F=f(X_1,X_2,X_3,X_4)$,</span> where $X_1,X_2,X_3,X_4$ are the parameters under which the structure is produced and are mutually independent random variables.

<ol class="topic-list-paren">
  <li>Determine an approximation of $\mathrm{Var}(F)$ obtained from a first-order Taylor expansion.</li>
  <li>Evaluate $\mathrm{Var}(F)$ for <span class="text-nowrap">$F=X_1X_2X_3^3/4X_4^3$.</span></li>
</ol>
</div>

(1) $F=f(\boldsymbol{X})$ 對 $\boldsymbol{\mu}$ 之一階泰勒展開為
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F\fallingdotseq f(\boldsymbol{\mu})+\sum_{i=1}^{4}\frac{\partial}{\,\partial X_i\,}f(\boldsymbol{X})\biggr\rvert_{\boldsymbol{X}=\boldsymbol{\mu}}(X_i-\mu_{\sssig X_i})
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F&\fallingdotseq f(\boldsymbol{\mu})\\[0.45em]
&\qquad+\sum_{i=1}^{4}\frac{\partial}{\,\partial X_i\,}f(\boldsymbol{X})\biggr\rvert_{\boldsymbol{X}=\boldsymbol{\mu}}(X_i-\mu_{\sssig X_i})
\end{aligned}
$$

</div>

故
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(F)&\fallingdotseq\mathrm{Var}\Biggl[f(\boldsymbol{\mu})+\sum_{i=1}^{4}\frac{\partial}{\,\partial X_i\,}f(\boldsymbol{X})\biggr\rvert_{\boldsymbol{X}=\boldsymbol{\mu}}(X_i-\mu_{\sssig X_i})\Biggr]\\[0.45em]
&=\sum_{i=1}^{4}\Biggl[\frac{\partial}{\,\partial X_i\,}f(\boldsymbol{X})\biggr\rvert_{\boldsymbol{X}=\boldsymbol{\mu}}\Biggr]^{2}\sigma_{\sssig X_i}^{2}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(F)&\fallingdotseq\mathrm{Var}\Biggl[f(\boldsymbol{\mu})\\[0.2em]
&\qquad+\sum_{i=1}^{4}\frac{\partial}{\,\partial X_i\,}f(\boldsymbol{X})\biggr\rvert_{\boldsymbol{X}=\boldsymbol{\mu}}(X_i-\mu_{\sssig X_i})\Biggr]\\[0.45em]
&=\sum_{i=1}^{4}\Biggl[\frac{\partial}{\,\partial X_i\,}f(\boldsymbol{X})\biggr\rvert_{\boldsymbol{X}=\boldsymbol{\mu}}\Biggr]^{2}\sigma_{\sssig X_i}^{2}
\end{aligned}
$$

</div>

(2) 由題意設定 $F=f(\boldsymbol{X})$ $=$ <span class="text-nowrap">$X_1X_2X_3^3/4X_4^3$，</span>可知
{: .topic-paren-item}

$$
\begin{gathered}
\frac{\partial}{\,\partial X_1\,}f(\boldsymbol{X})=\frac{1}{4}X_2X_3^3X_4^{-3}\\[0.45em]
\frac{\partial}{\,\partial X_2\,}f(\boldsymbol{X})=\frac{1}{4}X_1X_3^3X_4^{-3}\\[0.45em]
\frac{\partial}{\,\partial X_3\,}f(\boldsymbol{X})=\frac{3}{4}X_1X_2X_3^2X_4^{-3}\\[0.45em]
\frac{\partial}{\,\partial X_4\,}f(\boldsymbol{X})=\frac{-3}{4}X_1X_2X_3^3X_4^{-4}
\end{gathered}
$$

故知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(F)&\fallingdotseq\Bigl(\frac{1}{4}\mu_{\sssig X_2}\mu_{\sssig X_3}^{3}\mu_{\sssig X_4}^{-3}\Bigr)^{2}\sigma_{\sssig X_1}^{2}+\Bigl(\frac{1}{4}\mu_{\sssig X_1}\mu_{\sssig X_3}^{3}\mu_{\sssig X_4}^{-3}\Bigr)^{2}\sigma_{\sssig X_2}^{2}\\[0.45em]
&\quad +\Bigl(\frac{3}{4}\mu_{\sssig X_1}\mu_{\sssig X_2}\mu_{\sssig X_3}^{2}\mu_{\sssig X_4}^{-3}\Bigr)^{2}\sigma_{\sssig X_3}^{2}+\Bigl(\frac{-3}{4}\mu_{\sssig X_1}\mu_{\sssig X_2}\mu_{\sssig X_3}^{3}\mu_{\sssig X_4}^{-4}\Bigr)^{2}\sigma_{\sssig X_4}^{2}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(F)&\fallingdotseq\Bigl(\frac{1}{4}\mu_{\sssig X_2}\mu_{\sssig X_3}^{3}\mu_{\sssig X_4}^{-3}\Bigr)^{2}\sigma_{\sssig X_1}^{2}\\[0.45em]
&\qquad+\Bigl(\frac{1}{4}\mu_{\sssig X_1}\mu_{\sssig X_3}^{3}\mu_{\sssig X_4}^{-3}\Bigr)^{2}\sigma_{\sssig X_2}^{2}\\[0.45em]
&\qquad+\Bigl(\frac{3}{4}\mu_{\sssig X_1}\mu_{\sssig X_2}\mu_{\sssig X_3}^{2}\mu_{\sssig X_4}^{-3}\Bigr)^{2}\sigma_{\sssig X_3}^{2}\\[0.45em]
&\qquad+\Bigl(\frac{-3}{4}\mu_{\sssig X_1}\mu_{\sssig X_2}\mu_{\sssig X_3}^{3}\mu_{\sssig X_4}^{-4}\Bigr)^{2}\sigma_{\sssig X_4}^{2}
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

上述問題事實上是 [Theorem 2.15](/lecture-notes/variance-standard-deviation/#thm-taylor-approximation) 的延伸，只是此處由於變數變多了，故將微分改為偏微分，其他原理皆相同。

</div>

## 本篇小結

[Theorem 3.4](#thm-multi-exp) 把期望值推廣到二元的情形。離散型是把 $g(x,y)$ 的值以 joint pmf 作雙重加總，連續型是把 $g(x,y)$ 的值以 joint pdf 作二重積分，兩者都要求絕對值的加總或積分為有限。這裡的 $g(\cdot,\cdot)$ 可以是任意的實值函數，一旦設定為 $g(X,Y)=X$ 或 <span class="text-nowrap">$g(X,Y)=Y$，</span>所得的就是邊際分配的期望值 $\mathbb{E}(X)$ 與 <span class="text-nowrap">$\mathbb{E}(Y)$；</span>證明的關鍵在於與 $X$ 無關的地方可以先行積分，把 $Y$ 積分掉之後留下的正是 $X$ 的邊際 pdf。

[Theorem 3.5](#thm-multi-exp-proper) 指出線性組合仍然可以與期望值交換，[Theorem 3.6](#thm-indep-exp) 則處理相乘這種非線性的設定。在兩個變數獨立的前提之下，$g(X)$ 與 $h(Y)$ 乘積的期望值等於兩個期望值相乘，證明所依據的正是聯合 pdf 可以分解成兩個邊際 pdf 相乘。要留意的是這個敘述反過來說並不成立。[Theorem 3.7](#thm-multi-function-var) 把變異數的定義一併推廣到二元的函數上。

四道例題之中，[Example 3.14](#ex-independent-product-expectation) 與 [Example 3.15](#ex-exponential-product-expectation) 都在求兩個獨立隨機變數乘積的變異數，前者的 $X$ 期望值與變異數皆為 $0$ 而使結果為 <span class="text-nowrap">$0$，</span>後者則求得 $\mu_1^2\,\sigma_2^2$ $+$ $\mu_2^2\,\sigma_1^2$ $+$ $\sigma_1^2\,\sigma_2^2$ 這個式子，可見即便兩者獨立，$\mathrm{Var}(XY)$ 也不等於 $\mathrm{Var}(X)$ 與 $\mathrm{Var}(Y)$ 相乘之值。[Example 3.16](#ex-balls-into-boxes-empty) 把空盒總數寫成只取 $0$ 與 $1$ 的變數之和，再以交叉項的期望值求得變異數；[Example 3.17](#ex-structure-load-expectation) 則把一階泰勒展開推廣到四個變數，微分因而改為偏微分。

[下一篇](/lecture-notes/conditional-expectation-and-variance/)把期望值放到條件分配之上，介紹[條件期望值](/lecture-notes/conditional-expectation-and-variance/#def-conditional-expectation)與[條件變異數](/lecture-notes/conditional-expectation-and-variance/#def-conditional-variance)。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
