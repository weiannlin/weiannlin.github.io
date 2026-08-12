---
title: "變異數"
subtitle: "Variance"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 8
order: 208
permalink: /teaching-topics/ch2-p208-candidate/
date: 2026-08-06
published: false
excerpt: "變異數是離差平方的期望值，用來衡量一個隨機變數平均的分散程度: 離散型以 pmf 對各個離差平方加權求和，連續型以 pdf 加權積分。實際計算時多改用平方的期望值減期望值的平方，也就是 $\\mathrm{Var}(X)=\\mathbb{E}(X^{2})-[\\mathbb{E}(X)]^{2}$；同一套作法延伸到函數 $g(X)$ 便得到函數變異數。變異數恆為非負，對隨機變數平移一個常數不改變它的值，伸縮 $a$ 倍則使它成為原先的 $a^{2}$ 倍。"
---

[上一篇](/teaching-topics/ch2-p207-candidate/)把期望值的計算推廣到隨機變數的函數 $g(X)$，並給出期望值與線性組合可以交換的性質。期望值指出一個分配的聚集中心，但只有中心並不足以描述一個分配: 兩個期望值完全相同的隨機變數，取值散開的程度可以相差很多。

本篇介紹用來衡量這種分散程度的量數: 變異數。以下先分別對離散型與連續型給出定義，再導出一個便於計算的公式，接著把它延伸到函數 $g(X)$，然後列出變異數的兩項性質，並由其中的複合性質設定出三個常用的子性質，最後以一張比較圖說明變異數的大小在一個分配上的意義，並以兩道例題示範計算。

<div id="def-variance" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.7 (變異數, variance)</div>

若 $X$ 為離散型隨機變數，值域為 $\mathcal{R}\_{\sssig X}$、pmf 為 $p\_{\sssig X}(x)$，二階動差 $\mathbb{E}(\lvert X\rvert^{2})$ 為有限，則以下的量

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\sigma_{\sssig X}^{2}=\mathrm{Var}(X)=\mathbb{E}\bigl[(X-\mu_{\sssig X})^{2}\bigr]=\sum_{x\in\mathcal{R}_{\sssig X}}(x-\mu_{\sssig X})^{2}\,p_{\sssig X}(x)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\sigma_{\sssig X}^{2}=\mathrm{Var}(X)=\mathbb{E}\bigl[(X-\mu_{\sssig X})^{2}\bigr]\\[0.45em]
&\quad =\sum_{x\in\mathcal{R}_{\sssig X}}(x-\mu_{\sssig X})^{2}\,p_{\sssig X}(x)
\end{aligned}
$$

</div>

為 $X$ 的**變異數 <span lang="en">(variance)</span>**。

若 $X$ 為連續型隨機變數，值域為 $\mathcal{R}\_{\sssig X}$、pdf 為 $f\_{\sssig X}(x)$，二階動差 $\mathbb{E}(\lvert X\rvert^{2})$ 為有限，則以下的量

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\sigma_{\sssig X}^{2}=\mathrm{Var}(X)=\mathbb{E}\bigl[(X-\mu_{\sssig X})^{2}\bigr]=\int_{-\infty}^{\infty}(x-\mu_{\sssig X})^{2}f_{\sssig X}(x)\,dx
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\sigma_{\sssig X}^{2}=\mathrm{Var}(X)=\mathbb{E}\bigl[(X-\mu_{\sssig X})^{2}\bigr]\\[0.45em]
&\quad =\int_{-\infty}^{\infty}(x-\mu_{\sssig X})^{2}f_{\sssig X}(x)\,dx
\end{aligned}
$$

</div>

為 $X$ 的**變異數 <span lang="en">(variance)</span>**。

</div>

變異數有一些地方需要注意:

(1) $X$ 的變異數亦常常被記為 $\mathrm{V}(X)$。
{: .topic-paren-item}

(2) 變異數亦是一種期望值，從其定義上來看，變異數是**離差平方的期望值**，而**離差 <span lang="en">(deviation)</span>** 是指隨機變數與其期望值的差，即 $X-\mu_{\sssig X}$，用來指出一個隨機變數的值與其分配中心的距離。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

[期望值](/teaching-topics/ch2-p06-candidate/#def-expectation)是一種加權平均，故我們可將變異數理解為是一個隨機變數**平均的分散程度**或**平均的變異程度**。

衡量一個隨機變數的變異程度，是機率與統計中一個重要的課題，特別是在統計檢定中，變異程度更扮演舉足輕重的地位。

</div>

(3) 我們稱其為母體變異數，避免與具隨機性的樣本變異數搞混，後者定義為
{: .topic-paren-item}

$$
S^{2}=\frac{1}{\,n-1\,}\sum_{i=1}^{n}\bigl(X_{i}-\overline{X}\bigr)^{2}
$$

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

變異數與期望值相同，是一個隨機變數的母數，故其當然是常數而不具隨機性。

</div>

<div id="thm-variance-formula" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.11 (變異數的計算公式, computational formula for the variance)</div>

若 $X$ 為一隨機變數且其變異數存在，則

$$
\mathrm{Var}(X)=\mathbb{E}\bigl(X^{2}\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.** 由 [Definition 2.7](#def-variance) 與 [Theorem 2.10](/teaching-topics/ch2-p207-candidate/#thm-expectation-linearity) 可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(X)&=\mathbb{E}\bigl[(X-\mu_{\sssig X})^{2}\bigr]=\mathbb{E}\bigl(X^{2}-2\mu_{\sssig X}X+\mu_{\sssig X}^{2}\bigr)\\[0.45em]
&=\mathbb{E}\bigl(X^{2}\bigr)-2\mu_{\sssig X}\mathbb{E}(X)+\mu_{\sssig X}^{2}\\[0.45em]
&=\mathbb{E}\bigl(X^{2}\bigr)-2\bigl[\mathbb{E}(X)\bigr]^{2}+\bigl[\mathbb{E}(X)\bigr]^{2}=\mathbb{E}\bigl(X^{2}\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathrm{Var}(X)=\mathbb{E}\bigl[(X-\mu_{\sssig X})^{2}\bigr]\\[0.45em]
&\quad =\mathbb{E}\bigl(X^{2}-2\mu_{\sssig X}X+\mu_{\sssig X}^{2}\bigr)\\[0.45em]
&\quad =\mathbb{E}\bigl(X^{2}\bigr)-2\mu_{\sssig X}\mathbb{E}(X)+\mu_{\sssig X}^{2}\\[0.45em]
&\quad =\mathbb{E}\bigl(X^{2}\bigr)-2\bigl[\mathbb{E}(X)\bigr]^{2}+\bigl[\mathbb{E}(X)\bigr]^{2}\\[0.45em]
&\quad =\mathbb{E}\bigl(X^{2}\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

計算變異數時，如果總是使用原始定義，其實相當不好計算，有了這個公式的協助，將會容易許多，且其有一個簡單好記的口訣，即變異數是**平方的期望值減期望值的平方**。

</div>

<div id="thm-variance-of-function" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.12 (函數變異數, variance of a function)</div>

若 $X$ 為**離散型**隨機變數，$g(\cdot)$ 為一實值可測函數，$\mathbb{E}\bigl[g^{2}(X)\bigr]$ 為有限，則以下的量

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathrm{Var}\bigl[g(X)\bigr]&=\mathbb{E}\Bigl[\bigl(g(X)-\mathbb{E}[g(X)]\bigr)^{2}\Bigr]\\[0.45em]
&=\sum_{x\in\mathcal{R}_{\sssig X}}(g(x)-\mathbb{E}[g(X)])^{2}\,p_{\sssig X}(x)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathrm{Var}\bigl[g(X)\bigr]\\[0.45em]
&\quad =\mathbb{E}\Bigl[\bigl(g(X)-\mathbb{E}[g(X)]\bigr)^{2}\Bigr]\\[0.45em]
&\quad =\sum_{x\in\mathcal{R}_{\sssig X}}(g(x)-\mathbb{E}[g(X)])^{2}\,p_{\sssig X}(x)
\end{aligned}
$$

</div>

若 $X$ 為**連續型**隨機變數，$g(\cdot)$ 為一實值可測函數，$\mathbb{E}\bigl[g^{2}(X)\bigr]$ 為有限，則以下的量

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathrm{Var}\bigl[g(X)\bigr]&=\mathbb{E}\Bigl[\bigl(g(X)-\mathbb{E}[g(X)]\bigr)^{2}\Bigr]\\[0.45em]
&=\int_{-\infty}^{\infty}(g(x)-\mathbb{E}[g(X)])^{2}f_{\sssig X}(x)\,dx
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathrm{Var}\bigl[g(X)\bigr]\\[0.45em]
&\quad =\mathbb{E}\Bigl[\bigl(g(X)-\mathbb{E}[g(X)]\bigr)^{2}\Bigr]\\[0.45em]
&\quad =\int_{-\infty}^{\infty}(g(x)-\mathbb{E}[g(X)])^{2}f_{\sssig X}(x)\,dx
\end{aligned}
$$

</div>

</div>

[Theorem 2.12](#thm-variance-of-function) 與 [Definition 2.7](#def-variance) 之間的關係，就如同 [Theorem 2.9](/teaching-topics/ch2-p207-candidate/#thm-expectation-of-function) 與 [Definition 2.6](/teaching-topics/ch2-p06-candidate/#def-expectation) 之間一樣，是一種延伸的性質，但卻給我們相當程度的方便。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

稍後將會提到[**隨機變數變換 <span lang="en">(transformation of random variable)</span>**](/teaching-topics/ch2-p223-candidate/) 的技巧，在轉換出 $g(X)$ 的分配後，再計算其期望值與變異數。然而，其結果與這裡的延伸性質卻是殊途同歸，屆時更能看出此二個性質給我們的方便之處。

</div>

此外，如果套用了 [Theorem 2.11](#thm-variance-formula)，我們可以將函數變異數用更簡單的方式來計算，即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}\bigl[g(X)\bigr]=\mathbb{E}\Bigl[\bigl[g(X)\bigr]^{2}\Bigr]-\Bigl(\mathbb{E}\bigl[g(X)\bigr]\Bigr)^{2}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathrm{Var}\bigl[g(X)\bigr]\\[0.45em]
&\quad =\mathbb{E}\Bigl[\bigl[g(X)\bigr]^{2}\Bigr]-\Bigl(\mathbb{E}\bigl[g(X)\bigr]\Bigr)^{2}
\end{aligned}
$$

</div>

舉例來說，取 $g(X)=X^{2}$ 便有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}\bigl(X^{2}\bigr)=\mathbb{E}\Bigl[\bigl(X^{2}\bigr)^{2}\Bigr]-\Bigl[\mathbb{E}\bigl(X^{2}\bigr)\Bigr]^{2}=\mathbb{E}\bigl(X^{4}\bigr)-\Bigl[\mathbb{E}\bigl(X^{2}\bigr)\Bigr]^{2}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathrm{Var}\bigl(X^{2}\bigr)=\mathbb{E}\Bigl[\bigl(X^{2}\bigr)^{2}\Bigr]-\Bigl[\mathbb{E}\bigl(X^{2}\bigr)\Bigr]^{2}\\[0.45em]
&\quad =\mathbb{E}\bigl(X^{4}\bigr)-\Bigl[\mathbb{E}\bigl(X^{2}\bigr)\Bigr]^{2}
\end{aligned}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個式子可以將其寫為母數符號的版本，即

$$
\sigma_{\sssig X}^{2}=\mathbb{E}\bigl(X^{2}\bigr)-\mu_{\sssig X}^{2}
$$

經過移項後可以得到下面這個重要的結果。

$$
\mathbb{E}\bigl(X^{2}\bigr)=\sigma_{\sssig X}^{2}+\mu_{\sssig X}^{2}
$$

這個結果在很多統計推論上相當有用，因為許多隨機變數的機率分配雖然母數已知，但其二階原動差並不好算，若有此結果，則我們就能夠繞過繁複的計算。其中，$\mathbb{E}(X^{r})$ 稱作 $X$ 的 $r$ 階原動差，是由卡爾・皮爾森 (Karl Pearson, 1857-1936) 所創立之[**動差系統 (moment system)**](/teaching-topics/ch2-p213-candidate/#def-population-moment) 中的一員，本章稍後介紹[**動差母函數 <span lang="en">(moment generating function, mgf)</span>**](/teaching-topics/ch2-p215-candidate/#def-mgf) 時會對此詳加介紹。

</div>

<div id="thm-variance-properties" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.13 (變異數的性質, variance properties)</div>

若 $X$ 為一隨機變數，$g(\cdot)$ 為一實值可測函數，並且令 $a, b$ 為二常數，且 $\mathbb{E}(\lvert X\rvert^{2})<\infty$ 與 $\mathbb{E}\bigl[g^{2}(X)\bigr]<\infty$，則

<ol class="topic-list-paren">
  <li>
  $$
  \mathrm{Var}(X)\geqslant0
  $$
  </li>
  <li>
  $$
  \mathrm{Var}\bigl[ag(X)+b\bigr]=a^{2}\,\mathrm{Var}\bigl[g(X)\bigr]
  $$
  </li>
</ol>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

[Theorem 2.13](#thm-variance-properties) 的兩項前提分別對應兩個結論。(1) 斷言的是 $\mathrm{Var}(X)\geqslant0$ 這件事，要先有 $\mathrm{Var}(X)$ 存在才談得上非負，故須 $\mathbb{E}(\lvert X\rvert^{2})$ 為有限，也就是 [Definition 2.7](#def-variance) 所要求的條件；(2) 的兩側都是 $g(X)$ 的變異數，故須 $\mathbb{E}[g^{2}(X)]<\infty$，即 [Theorem 2.12](#thm-variance-of-function) 所要求的條件。這兩個期望值一旦發散，對應的變異數就不存在，該款的敘述也就不成立。

</div>

<div class="topic-proof" markdown="1">
**Proof.**

(1) 本處的證明我們同樣僅以離散型作為例子，連續型請讀者自行練習。由於平方項恆為非負，也就是
{: .topic-paren-item}

$$
(x-\mu_{\sssig X})^{2}\geqslant0,\quad\forall x\in\mathbb{R}
$$

故可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}(X)=\mathbb{E}\bigl[(X-\mu_{\sssig X})^{2}\bigr]=\sum_{x\in\mathcal{R}_{\sssig X}}(x-\mu_{\sssig X})^{2}\,p_{\sssig X}(x)\geqslant0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathrm{Var}(X)=\mathbb{E}\bigl[(X-\mu_{\sssig X})^{2}\bigr]\\[0.45em]
&\quad =\sum_{x\in\mathcal{R}_{\sssig X}}(x-\mu_{\sssig X})^{2}\,p_{\sssig X}(x)\geqslant0
\end{aligned}
$$

</div>

(2) 由 [Theorem 2.12](#thm-variance-of-function) 及 [Theorem 2.10](/teaching-topics/ch2-p207-candidate/#thm-expectation-linearity) 可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathrm{Var}\bigl[ag(X)+b\bigr]&=\mathbb{E}\Bigl[\bigl(\bigl[ag(X)+b\bigr]-\mathbb{E}\bigl[ag(X)+b\bigr]\bigr)^{2}\Bigr]\\[0.45em]
&=\mathbb{E}\Bigl[\bigl(\bigl[ag(X)+b\bigr]-\bigl(a\,\mathbb{E}[g(X)]+b\bigr)\bigr)^{2}\Bigr]\\[0.45em]
&=\mathbb{E}\Bigl[\bigl(ag(X)-a\,\mathbb{E}[g(X)]\bigr)^{2}\Bigr]\\[0.45em]
&=\mathbb{E}\Bigl[a^{2}\bigl(g(X)-\mathbb{E}[g(X)]\bigr)^{2}\Bigr]\\[0.45em]
&=a^{2}\,\mathbb{E}\Bigl[\bigl(g(X)-\mathbb{E}[g(X)]\bigr)^{2}\Bigr]=a^{2}\,\mathrm{Var}\bigl[g(X)\bigr]
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathrm{Var}\bigl[ag(X)+b\bigr]\\[0.45em]
&\quad =\mathbb{E}\Bigl[\bigl(\bigl[ag(X)+b\bigr]\\[0.2em]
&\qquad -\mathbb{E}\bigl[ag(X)+b\bigr]\bigr)^{2}\Bigr]\\[0.45em]
&\quad =\mathbb{E}\Bigl[\bigl(\bigl[ag(X)+b\bigr]\\[0.2em]
&\qquad -\bigl(a\,\mathbb{E}[g(X)]+b\bigr)\bigr)^{2}\Bigr]\\[0.45em]
&\quad =\mathbb{E}\Bigl[\bigl(ag(X)-a\,\mathbb{E}[g(X)]\bigr)^{2}\Bigr]\\[0.45em]
&\quad =\mathbb{E}\Bigl[a^{2}\bigl(g(X)-\mathbb{E}[g(X)]\bigr)^{2}\Bigr]\\[0.45em]
&\quad =a^{2}\,\mathbb{E}\Bigl[\bigl(g(X)-\mathbb{E}[g(X)]\bigr)^{2}\Bigr]\\[0.45em]
&\quad =a^{2}\,\mathrm{Var}\bigl[g(X)\bigr]
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
{: .topic-paren-cont}
</div>

[Theorem 2.13](#thm-variance-properties) 中，(1) 被稱為變異數的**非負性**，這個性質相當直觀，因為變異數是用來衡量一個隨機變數的離散程度的母數，故變異數非負是可以想見的。

此外，與 [Theorem 2.10](/teaching-topics/ch2-p207-candidate/#thm-expectation-linearity) 相仿，[Theorem 2.13](#thm-variance-properties) 的 (2) 是一個複合性質的定理，我們可以透過設定 $g(\cdot)$ 與 $a, b$ 的值，來得到許多有用的子性質，見以下設定。

(1) **[ 設定 $a=0$ ]**
{: .topic-paren-item}

$$
\mathrm{Var}(b)=0
$$

此即**常數不具變異性**。
{: .topic-paren-cont}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

常數不具有隨機性，亦沒有分散程度可言，不具備變異的可能是當然的。常數亦被我們稱做**退化隨機變數 <span lang="en">(degenerate random variable)</span>**，即所有的機率都發生在單一質點上的隨機變數。

</div>

(2) **[ 設定 $a=1$，$g(X)=X$ ]**
{: .topic-paren-item}

$$
\mathrm{Var}(X+b)=\mathrm{Var}(X)
$$

此即**平移不變性**。
{: .topic-paren-cont}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

變異數是衡量 $X$ 的離散程度的母數，故對 $X$ 平移一個常數 $b$ 的距離，應不改變其分散程度，亦即其變異數與原本相同。

</div>

(3) **[ 設定 $a\neq0$ 且 $g(X)=X$，$b=0$ ]**
{: .topic-paren-item}

$$
\mathrm{Var}(aX)=a^{2}\,\mathrm{Var}(X)
$$

此即**平方伸縮性**。
{: .topic-paren-cont}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個結果的直觀在於，變異數若考慮單位，則其單位應為 $X$ 之單位的平方，因為變異數所有的運算，都是平方之後的結果，故若將 $X$ 伸縮一個倍數 $a$，則其變異數應變成原先的 $a^{2}$ 倍。

</div>

下面我們便以圖示來理解「變異數的大小」在一個隨機變數的分配上的意義。

<figure id="fig-variance-comparison" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/variance-same-mean-different-spread.svg" alt="兩條機率密度曲線畫在同一組座標軸上，峰位都落在同一點，該點以虛線向下延伸並標為 μ_X。較寬而矮的一條曲線標示變異數較大，在離該點較遠的地方仍有相當的高度；較窄而高的一條曲線標示變異數較小，高度集中在該點附近。">
  <figcaption><span class="topic-figure__label">Fig. 2.11.</span> 二個期望值完全相同的隨機變數之機率分配，共用同一組座標軸: 較寬的一條變異數較大，較窄的一條變異數較小。</figcaption>
</figure>

我們可以從這張圖發現，所謂「變異數較大，表示分配較為離散」的意思是**在 $X$ 離期望值較遠的地方，相較於變異數小的分配而言，變異數大的分配，具有比較大的機率密度**；反之，變異數較小的分配，在離期望值較近的地方，有比較大的機率密度，所以我們可以把變異數較小的分配理解為 **$X$ 大部分集中在期望值的附近**。

<div id="ex-weekly-accidents-variance" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.15 <span lang="en">(Continued)</span></div>

<div lang="en" markdown="1">
Suppose that $X$ denotes the number of accidents occurring in Ankang City in a week, and that the probability distribution of the number of accidents is given in the following table.

| $x$ | $3$ | $4$ | $5$ | $6$ |
|:---:|:---:|:---:|:---:|:---:|
| $\mathbb{P}(X=x)$ | $0.2$ | $0.3$ | $0.3$ | $0.2$ |
{: .topic-table--matrix}

<ol class="topic-list-paren topic-list-paren--start-2">
  <li>Find the variance of this distribution.</li>
</ol>
</div>

(2) 由[前一小題](/teaching-topics/ch2-p06-candidate/#ex-weekly-accidents)已求得 $\mathbb{E}(X)=4.5$，而
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl(X^{2}\bigr)&=\sum_{x=3}^{6}x^{2}\,\mathbb{P}(X=x)=3^{2}\times0.2+4^{2}\times0.3\\[0.45em]
&\quad +5^{2}\times0.3+6^{2}\times0.2=21.3
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}\bigl(X^{2}\bigr)=\sum_{x=3}^{6}x^{2}\,\mathbb{P}(X=x)\\[0.45em]
&\quad =3^{2}\times0.2+4^{2}\times0.3\\[0.2em]
&\qquad +5^{2}\times0.3+6^{2}\times0.2\\[0.45em]
&\quad =21.3
\end{aligned}
$$

</div>

故 $X$ 之變異數為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}(X)=\mathbb{E}\bigl(X^{2}\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}=21.3-(4.5)^{2}=1.05
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathrm{Var}(X)=\mathbb{E}\bigl(X^{2}\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}\\[0.45em]
&\quad =21.3-(4.5)^{2}=1.05
\end{aligned}
$$

</div>

</div>

<div id="ex-power-demand-variance" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.10 <span lang="en">(Continued)</span></div>

<div lang="en" markdown="1">
Suppose that $X$ denotes the growth in demand for electrical power, measured in millions of kilowatt hours, in a certain region over the coming $2$ years, and that the density function of $X$ is

$$
f_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{1}{64}x^{3}, & 0<x<4\\[0.7em]
0, & \text{otherwise}
\end{array}
\right.
$$

<ol class="topic-list-paren topic-list-paren--start-4">
  <li>Find the mean and the variance of the growth in demand.</li>
</ol>
</div>

(4) 承[前三小題](/teaching-topics/ch2-p04-candidate/#ex-power-demand-density)的密度函數，先算出期望值為
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(X)=\int_{0}^{4}x\cdot\frac{1}{64}x^{3}\,dx=\left[\frac{1}{\,320\,}x^{5}\right]_{0}^{4}=\frac{\,16\,}{5}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\int_{0}^{4}x\cdot\frac{1}{64}x^{3}\,dx\\[0.45em]
&=\left[\frac{1}{\,320\,}x^{5}\right]_{0}^{4}=\frac{\,16\,}{5}
\end{aligned}
$$

</div>

再算出平方期望值為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\bigl(X^{2}\bigr)=\int_{0}^{4}x^{2}\cdot\frac{1}{64}x^{3}\,dx=\left[\frac{1}{\,384\,}x^{6}\right]_{0}^{4}=\frac{\,32\,}{3}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl(X^{2}\bigr)&=\int_{0}^{4}x^{2}\cdot\frac{1}{64}x^{3}\,dx\\[0.45em]
&=\left[\frac{1}{\,384\,}x^{6}\right]_{0}^{4}=\frac{\,32\,}{3}
\end{aligned}
$$

</div>

故所求的變異數為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}(X)=\mathbb{E}\bigl(X^{2}\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}=\frac{\,32\,}{3}-\left(\frac{16}{5}\right)^{2}=\frac{\,32\,}{75}\fallingdotseq0.4267
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathrm{Var}(X)=\mathbb{E}\bigl(X^{2}\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}\\[0.45em]
&\quad =\frac{\,32\,}{3}-\left(\frac{16}{5}\right)^{2}\\[0.45em]
&\quad =\frac{\,32\,}{75}\fallingdotseq0.4267
\end{aligned}
$$

</div>

</div>

## 本篇小結

[Definition 2.7](#def-variance) 以 $\mathbb{E}(\lvert X\rvert^{2})<\infty$ 為前提，把變異數 $\sigma_{\sssig X}^{2}=\mathrm{Var}(X)$ 定義為離差平方的期望值: 離散型以 $p_{\sssig X}(x)$ 為權重對 $(x-\mu_{\sssig X})^{2}$ 加總，連續型則以 $f_{\sssig X}(x)$ 為權重積分。它衡量的是一個隨機變數平均的分散程度，是母數而不具隨機性，指稱時以母體變異數與樣本變異數 $S^{2}$ 區別。

直接由定義計算並不方便，[Theorem 2.11](#thm-variance-formula) 給出 $\mathrm{Var}(X)=\mathbb{E}(X^{2})-[\mathbb{E}(X)]^{2}$ 這條公式，也就是平方的期望值減期望值的平方；同一套作法延伸到函數，便得到 [Theorem 2.12](#thm-variance-of-function) 的函數變異數。至於 $\sigma_{\sssig X}^{2}=\mathbb{E}(X^{2})-\mu_{\sssig X}^{2}$ 移項後所得的 $\mathbb{E}(X^{2})=\sigma_{\sssig X}^{2}+\mu_{\sssig X}^{2}$ 這層關係，讓我們得以繞過二階原動差的計算。

[Theorem 2.13](#thm-variance-properties) 的兩項性質，其一是非負性，其二是複合性質 $\mathrm{Var}[ag(X)+b]=a^{2}\mathrm{Var}[g(X)]$ 這一條；由後者設定 $a$、$b$ 與 $g(\cdot)$，依序得到常數不具變異性、平移不變性與平方伸縮性三個子性質。[Fig. 2.11](#fig-variance-comparison) 畫出期望值相同而變異數不同的兩個分配，變異數大者在離期望值較遠處仍有較大的密度。[Example 2.15 <span lang="en">(Continued)</span>](#ex-weekly-accidents-variance) 與 [Example 2.10 <span lang="en">(Continued)</span>](#ex-power-demand-variance) 分別以離散型的加總與連續型的積分示範計算公式的用法。[下一篇](/teaching-topics/ch2-p209-candidate/)繼續以例題示範變異數的求算，並介紹期望值使平方離差的期望值達到最小的性質、泰勒近似，以及標準差。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Morris H. DeGroot and Mark J. Schervish. 2012. *Probability and Statistics*. 4th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
