---
title: "變異數分解定理"
subtitle: "The Variance Decomposition Theorem"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 15
order: 315
permalink: /lecture-notes/variance-decomposition-theorem/
date: 2026-08-13
published: false
excerpt: "變異數分解定理將 $\\mathrm{Var}(X)$ 拆解為條件變異數的期望值 $\\mathbb{E}[\\mathrm{Var}(X\\mid Y)]$ 與條件期望值的變異數 $\\mathrm{Var}[\\mathbb{E}(X\\mid Y)]$ 之和，分別對應組內變異與組間變異。本篇給出證明並以階層模型例題示範應用。"
---

[上一篇](/lecture-notes/conditional-law-of-total-probability/)把全機率定理改寫成[隨機變數](/lecture-notes/random-variables-and-pmf/#def-random-variable)的版本，說明邊際的機率函數，可以由條件的機率函數以另一個變數的機率函數加權而得。這一條與[雙重期望值定理](/lecture-notes/double-expectation-theorem/#thm-double-expectation)的作法相同，先給定條件把問題簡化，再對條件本身取一次期望值，把條件的作用消掉。

至於[變異數](/lecture-notes/variance/#def-variance)，[條件變異數](/lecture-notes/conditional-expectation-and-variance/#def-conditional-variance)稍早已經定義過，一個自然的問題是，$X$ 自己的變異數與條件變異數之間，有沒有類似的關係？**變異數分解定理 <span lang="en">(variance decomposition theorem)</span>** 所給出的答案是肯定的，只是單取條件變異數的期望值並不足夠，還要再加上[條件期望值](/lecture-notes/conditional-expectation-and-variance/#def-conditional-expectation)的變異數。本篇先給出這條定理與它的證明，說明所分解出來的兩項各自對應到什麼，再以兩道例題示範它的用法。

<div id="thm-var-decom-thm" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 3.11 (變異數分解定理, variance decomposition theorem)</div>

若 $X$ 與 $Y$ 為二個隨機變數，則

<ol class="topic-list-paren topic-list-paren--math">
  <li>
<div class="topic-math-layout topic-math-layout--desktop">
$$
\mathrm{Var}(X)=\mathbb{E}\bigl[\mathrm{Var}(X\mid Y)\bigr]+\mathrm{Var}\bigl[\mathbb{E}(X\mid Y)\bigr]
$$
</div>
<div class="topic-math-layout topic-math-layout--mobile">
$$
\begin{aligned}
\mathrm{Var}(X)&=\mathbb{E}\bigl[\mathrm{Var}(X\mid Y)\bigr]\\[0.2em]
&\qquad+\mathrm{Var}\bigl[\mathbb{E}(X\mid Y)\bigr]
\end{aligned}
$$
</div>
  </li>
  <li>
<div class="topic-math-layout topic-math-layout--desktop">
$$
\mathrm{Var}(Y)=\mathbb{E}\bigl[\mathrm{Var}(Y\mid X)\bigr]+\mathrm{Var}\bigl[\mathbb{E}(Y\mid X)\bigr]
$$
</div>
<div class="topic-math-layout topic-math-layout--mobile">
$$
\begin{aligned}
\mathrm{Var}(Y)&=\mathbb{E}\bigl[\mathrm{Var}(Y\mid X)\bigr]\\[0.2em]
&\qquad+\mathrm{Var}\bigl[\mathbb{E}(Y\mid X)\bigr]
\end{aligned}
$$
</div>
  </li>
</ol>

</div>

<div class="topic-proof" markdown="1">
**Proof.**

我們僅以連續型證明 (1) 的狀況，(2) 的狀況與離散型同理可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[&\mathrm{Var}(X\mid Y)\bigr]+\mathrm{Var}\bigl[\mathbb{E}(X\mid Y)\bigr]\\[0.45em]
&=\mathbb{E}\Bigl[\mathbb{E}\bigl(X^{2}\mid Y\bigr)-\bigl[\mathbb{E}(X\mid Y)\bigr]^{2}\Bigr]\\[0.2em]
&\qquad +\mathbb{E}\Bigl(\bigl[\mathbb{E}(X\mid Y)\bigr]^{2}\Bigr)-\Bigl(\mathbb{E}\bigl[\mathbb{E}(X\mid Y)\bigr]\Bigr)^{2}\\[0.45em]
&=\mathbb{E}\Bigl[\mathbb{E}\bigl(X^{2}\mid Y\bigr)\Bigr]-\mathbb{E}\Bigl(\bigl[\mathbb{E}(X\mid Y)\bigr]^{2}\Bigr)\\[0.2em]
&\qquad +\mathbb{E}\Bigl(\bigl[\mathbb{E}(X\mid Y)\bigr]^{2}\Bigr)-\Bigl(\mathbb{E}\bigl[\mathbb{E}(X\mid Y)\bigr]\Bigr)^{2}\\[0.45em]
&=\mathbb{E}\bigl(X^{2}\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}=\mathrm{Var}(X)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[&\mathrm{Var}(X\mid Y)\bigr]+\mathrm{Var}\bigl[\mathbb{E}(X\mid Y)\bigr]\\[0.3em]
&=\mathbb{E}\Bigl[\mathbb{E}\bigl(X^{2}\mid Y\bigr)-\bigl[\mathbb{E}(X\mid Y)\bigr]^{2}\Bigr]\\[0.2em]
&\qquad+\mathbb{E}\Bigl(\bigl[\mathbb{E}(X\mid Y)\bigr]^{2}\Bigr)\\[0.2em]
&\qquad-\Bigl(\mathbb{E}\bigl[\mathbb{E}(X\mid Y)\bigr]\Bigr)^{2}\\[0.45em]
&=\mathbb{E}\Bigl[\mathbb{E}\bigl(X^{2}\mid Y\bigr)\Bigr]\\[0.2em]
&\qquad-\mathbb{E}\Bigl(\bigl[\mathbb{E}(X\mid Y)\bigr]^{2}\Bigr)\\[0.2em]
&\qquad+\mathbb{E}\Bigl(\bigl[\mathbb{E}(X\mid Y)\bigr]^{2}\Bigr)\\[0.2em]
&\qquad-\Bigl(\mathbb{E}\bigl[\mathbb{E}(X\mid Y)\bigr]\Bigr)^{2}\\[0.45em]
&=\mathbb{E}\bigl(X^{2}\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}=\mathrm{Var}(X)
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

[此定理](#thm-var-decom-thm)將 $X$ 的總變異數拆解為兩個部分。若將條件變數 $Y$ 的不同取值視為不同組別，第一項 $\mathbb{E}\bigl[\mathrm{Var}(X\mid Y)\bigr]$ 是各組內部離散程度的平均，對應**組內變異**；第二項 $\mathrm{Var}\bigl[\mathbb{E}(X\mid Y)\bigr]$ 則是各組條件期望值之間的變異程度，對應**組間變異**。在實驗設計 <span lang="en">(experimental design)</span> 與變異數分析 <span lang="en">(analysis of variance, ANOVA)</span> 中，總變異分解為組內變異與組間變異的架構即與此定理完全對應。

</div>

<div id="ex-variance-decomposition-basic" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.29</div>

<div lang="en" markdown="1">
Let $X$ and $Y$ be two random variables such that <span class="text-nowrap">$\mathbb{E}(X\mid Y=y)=5y$,</span> <span class="text-nowrap">$\mathrm{Var}(X\mid Y=y)=8y$,</span> <span class="text-nowrap">$\mathbb{E}(Y)=2$,</span> and <span class="text-nowrap">$\mathrm{Var}(Y)=6$.</span> Find $\mathbb{E}(X)$ and <span class="text-nowrap">$\mathrm{Var}(X)$.</span>
</div>

由[雙重期望值定理](/lecture-notes/double-expectation-theorem/#thm-double-expectation)可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(X)=\mathbb{E}\bigl[\mathbb{E}(X\mid Y)\bigr]=\mathbb{E}(5Y)=5\,\mathbb{E}(Y)=10
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\mathbb{E}\bigl[\mathbb{E}(X\mid Y)\bigr]\\[0.45em]
&=\mathbb{E}(5Y)=5\,\mathbb{E}(Y)=10
\end{aligned}
$$

</div>

由[變異數分解定理](#thm-var-decom-thm)可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(X)&=\mathbb{E}\bigl[\mathrm{Var}(X\mid Y)\bigr]+\mathrm{Var}\bigl[\mathbb{E}(X\mid Y)\bigr]=\mathbb{E}(8Y)+\mathrm{Var}(5Y)\\[0.45em]
&=8\times\mathbb{E}(Y)+5^{2}\times\mathrm{Var}(Y)=8\times 2+5^{2}\times 6=166
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(X)&=\mathbb{E}\bigl[\mathrm{Var}(X\mid Y)\bigr]\\[0.2em]
&\qquad+\mathrm{Var}\bigl[\mathbb{E}(X\mid Y)\bigr]\\[0.45em]
&=\mathbb{E}(8Y)+\mathrm{Var}(5Y)\\[0.45em]
&=8\times\mathbb{E}(Y)+5^{2}\times\mathrm{Var}(Y)\\[0.45em]
&=8\times 2+5^{2}\times 6=166
\end{aligned}
$$

</div>

</div>

<div id="ex-uniform-p-binomial" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.30</div>

<div lang="en" markdown="1">
Let $P$ be a random variable uniformly distributed over <span class="text-nowrap">$(0,1)$,</span> so that $f_{\sssig P}(p)=1$ for <span class="text-nowrap">$0<p<1$.</span> Assume that the conditional distribution of $X$ given $P=p$ is binomial with parameters $n$ and <span class="text-nowrap">$p$,</span> i.e.,

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
p_{\sssig X\mid P}(x\mid p)=
\left\lbrace
\begin{array}{c@{\quad}l}
\binom{n}{x}p^{x}(1-p)^{(n-x)}, & x=0,1,\ldots,n\\[0.8em]
0, & \text{o.w.}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&p_{\sssig X\mid P}(x\mid p)\\[0.45em]
&=\left\lbrace
\begin{array}{c@{}l}
\binom{n}{x}p^{x}(1-p)^{(n-x)}, & x=0,1,\ldots,n\\[0.8em]
0, & \text{o.w.}
\end{array}
\right.
\end{aligned}
$$

</div>

<ol class="topic-list-paren">
  <li>Find <span class="text-nowrap">$\mathbb{E}(X)$.</span></li>
  <li>Find <span class="text-nowrap">$\mathrm{Var}(X)$.</span></li>
  <li>Find the distribution of <span class="text-nowrap">$X$.</span></li>
</ol>
</div>

(1) 依題意可知 $X\mid(P=p)$ $\sim$ <span class="text-nowrap">$\mathrm{Bin}(n,p)$，</span>由雙重期望值定理可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(X)=\mathbb{E}\bigl[\mathbb{E}(X\mid P)\bigr]=\mathbb{E}(nP)=n\,\mathbb{E}(P)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\mathbb{E}\bigl[\mathbb{E}(X\mid P)\bigr]\\[0.45em]
&=\mathbb{E}(nP)=n\,\mathbb{E}(P)
\end{aligned}
$$

</div>

又 $P\sim\mathcal{U}(0,1)$ 故所求為
{: .topic-paren-cont}

$$
\mathbb{E}(X)=n\,\mathbb{E}(P)=\frac{n}{\,2\,}
$$

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

此處用到的 $\mathrm{Bin}(n,p)$ 為後文將介紹的[二項分配](/lecture-notes/binomial-distribution/#def-binomial) <span lang="en">(binomial distribution)</span>，其期望值為 <span class="text-nowrap">$np$、</span>變異數為 <span class="text-nowrap">$np(1-p)$；</span>而[標準均勻分配](/lecture-notes/uniform-distribution-integral-transform/#def-uniform-distribution) <span lang="en">(standard uniform distribution)</span> $\mathcal{U}(0,1)$ 的期望值為 <span class="text-nowrap">$\frac{\,1+0\,}{2}=\frac{1}{\,2\,}$、</span>變異數為 <span class="text-nowrap">$\frac{\,(1-0)^{2}\,}{12}=\frac{1}{\,12\,}$。</span>

</div>

(2)
{: .topic-paren-item}

<div class="topic-math-follow-before" markdown="1">

$$
\mathrm{Var}(P)=\mathbb{E}\bigl(P^{2}\bigr)-\bigl[\mathbb{E}(P)\bigr]^{2}=\frac{1}{\,12\,}
$$

</div>

<div class="topic-math-follow" markdown="1">

$$
\Longrightarrow\ \ \mathbb{E}\bigl(P^{2}\bigr)=\frac{1}{12}+\Bigl(\frac{1}{2}\Bigr)^{2}=\frac{1}{\,3\,}
$$

</div>

又由[變異數分解定理](#thm-var-decom-thm)可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(X)&=\mathbb{E}\bigl[\mathrm{Var}(X\mid P)\bigr]+\mathrm{Var}\bigl[\mathbb{E}(X\mid P)\bigr]\\[0.45em]
&=\mathbb{E}\bigl[nP(1-P)\bigr]+\mathrm{Var}\bigl(nP\bigr)\\[0.45em]
&=n\Bigl[\mathbb{E}(P)-\mathbb{E}\bigl(P^{2}\bigr)\Bigr]+n^{2}\,\mathrm{Var}(P)\\[0.45em]
&=n\Bigl(\frac{1}{2}-\frac{1}{3}\Bigr)+n^{2}\times\frac{1}{12}=\frac{\,2n+n^{2}\,}{12}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(X)&=\mathbb{E}\bigl[\mathrm{Var}(X\mid P)\bigr]\\[0.2em]
&\qquad+\mathrm{Var}\bigl[\mathbb{E}(X\mid P)\bigr]\\[0.45em]
&=\mathbb{E}\bigl[nP(1-P)\bigr]+\mathrm{Var}\bigl(nP\bigr)\\[0.45em]
&=n\Bigl[\mathbb{E}(P)-\mathbb{E}\bigl(P^{2}\bigr)\Bigr]\\[0.2em]
&\qquad+n^{2}\,\mathrm{Var}(P)\\[0.45em]
&=n\Bigl(\frac{1}{2}-\frac{1}{3}\Bigr)+n^{2}\times\frac{1}{12}\\[0.45em]
&=\frac{\,2n+n^{2}\,}{12}
\end{aligned}
$$

</div>

(3) 由[全機率定理](/lecture-notes/conditional-law-of-total-probability/#thm-law-of-total-prob-r-v)可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
p_{\sssig X}(x)&=\mathbb{E}\bigl[p_{\sssig X\mid P}(x\mid P)\bigr]=\int_{0}^{1}p_{\sssig X\mid P}(x\mid p)\,f_{\sssig P}(p)\,dp\\[0.45em]
&=\int_{0}^{1}\binom{n}{x}p^{x}(1-p)^{(n-x)}\,dp=\binom{n}{x}\int_{0}^{1}p^{x}(1-p)^{(n-x)}\,dp\\[0.45em]
&=\binom{n}{x}\frac{\Gamma(x+1)\Gamma(n-x+1)}{\Gamma(n+2)}\\[0.45em]
&=\frac{n!}{x!(n-x)!}\frac{x!(n-x)!}{(n+1)!}=\frac{1}{n+1},\ x=0,1,\ldots,n
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig X}(x)&=\mathbb{E}\bigl[p_{\sssig X\mid P}(x\mid P)\bigr]\\[0.45em]
&=\int_{0}^{1}p_{\sssig X\mid P}(x\mid p)\,f_{\sssig P}(p)\,dp\\[0.45em]
&=\int_{0}^{1}\binom{n}{x}p^{x}(1-p)^{(n-x)}\,dp\\[0.45em]
&=\binom{n}{x}\int_{0}^{1}p^{x}(1-p)^{(n-x)}\,dp\\[0.45em]
&=\binom{n}{x}\frac{\Gamma(x+1)\Gamma(n-x+1)}{\Gamma(n+2)}\\[0.45em]
&=\frac{n!}{x!(n-x)!}\frac{x!(n-x)!}{(n+1)!}\\[0.45em]
&=\frac{1}{n+1},\ x=0,1,\ldots,n
\end{aligned}
$$

</div>

</div>

<div id="note-hierarchical-model" class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

在[這道題目](#ex-uniform-p-binomial)中，$X$ 服從一個**參數為隨機變數的分配**，亦即**須先給定參數 $P=p$ 的值，$X$ 才回到我們熟悉的二項分配**。面對此類由條件分配與參數邊際分配分層建構的**階層模型 <span lang="en">(hierarchical model)</span>**，雙重期望值定理、全機率定理與[變異數分解定理](#thm-var-decom-thm)正是推導邊際期望值、邊際分配與邊際變異數的標準工具。

</div>

雙重期望值定理與[變異數分解定理](#thm-var-decom-thm)還可進一步用於處理隨機個數之和的問題，此即下一篇要介紹的定理。

## 本篇小結

[Theorem 3.11](#thm-var-decom-thm) 把 $X$ 的變異數分解成兩個部分，一個是條件變異數的期望值 <span class="text-nowrap">$\mathbb{E}\bigl[\mathrm{Var}(X\mid Y)\bigr]$，</span>另一個是條件期望值的變異數 $\mathrm{Var}\bigl[\mathbb{E}(X\mid Y)\bigr]$ 這一項。前者對應到的是組內變異，後者則是組間變異，這兩者與變異數分析中的組內變異、組間變異完全對應。證明的作法是把條件變異數與條件期望值各自以速算公式展開，$\mathbb{E}\bigl(\bigl[\mathbb{E}(X\mid Y)\bigr]^{2}\bigr)$ 這一項一負一正相消之後，剩下的正好是平方的期望值減去期望值的平方。

[Example 3.29](#ex-variance-decomposition-basic) 是這條定理最直接的用法。題目給的 $\mathbb{E}(X\mid Y=y)$ 與 $\mathrm{Var}(X\mid Y=y)$ 都是 $y$ 的函數，把 $y$ 換回 $Y$ 之後便得到兩個隨機變數，再依定理各取一次期望值與變異數，得到 $\mathbb{E}(X)=10$ 與 <span class="text-nowrap">$\mathrm{Var}(X)=166$。</span>

[Example 3.30](#ex-uniform-p-binomial) 的 $X$ 則是一個參數為隨機變數的分配。二項分配的成功機率 $P$ 本身是一個服從標準均勻分配的隨機變數，必須先給定 <span class="text-nowrap">$P=p$，</span>$X$ 才是我們所認知的二項分配。這種狀況正是[雙重期望值定理](/lecture-notes/double-expectation-theorem/#thm-double-expectation)、[全機率定理](/lecture-notes/conditional-law-of-total-probability/#thm-law-of-total-prob-r-v)與[變異數分解定理](#thm-var-decom-thm)的最佳使用時機，三個小題依序求得 $\mathbb{E}(X)$ $=$ <span class="text-nowrap">$\frac{n}{2}$、</span>$\mathrm{Var}(X)$ $=$ $\frac{\,2n+n^{2}\,}{12}$ 與 $p_{\sssig X}(x)$ $=$ $\frac{1}{\,n+1\,}$ 這三個答案，最後一個答案指出 $X$ 取 $0,1,\ldots,n$ 之中每一個值的機率都相同。同樣的層層設定在階層模型中必然會出現，讀者不妨在此先把這個觀念熟悉。

[下一篇](/lecture-notes/wald-identity-gamblers-ruin/)接著介紹[雙重期望值定理](/lecture-notes/double-expectation-theorem/#thm-double-expectation)與[變異數分解定理](#thm-var-decom-thm)所衍生的特殊應用，也就是隨機個數之和的期望值與變異數。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
