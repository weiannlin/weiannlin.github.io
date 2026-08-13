---
title: "共變異數矩陣"
subtitle: "The Covariance Matrix"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 20
order: 320
permalink: /teaching-topics/covariance-matrix/
date: 2026-08-13
published: false
excerpt: "把一組隨機變數兩兩之間的變異數與共變異數收在同一個矩陣裡，就是共變異數矩陣；它的主對角線是各個變數自己的變異數，而由共變異數的對稱性可知它必為對稱矩陣。若改以隨機向量的形式書寫，同一個矩陣可以寫成 $\\mathbf{\\Sigma}=\\mathbb{E}\\bigl[(\\boldsymbol{X}-\\boldsymbol{\\mu})(\\boldsymbol{X}-\\boldsymbol{\\mu})^{\\mathrm{T}}\\bigr]$ 這一條式子，也就是隨機向量的變異數，兩個定義事實上是同一件事情。本篇接著介紹隨機向量在向量與矩陣上的運算: 常數向量與隨機向量相乘之後，期望值為 $\\boldsymbol{a}^{\\mathrm{T}}\\boldsymbol{\\mu}$ 這個純量，變異數則為 $\\boldsymbol{a}^{\\mathrm{T}}\\mathbf{\\Sigma}\\boldsymbol{a}$ 這個二次形式，後者恰好可以用來證明共變異數矩陣必為正半定；把常數向量換成常數矩陣之後，所得的結果則是一個維度比 $1$ 還高的隨機向量。最後以一道二元常態的例題示範這些結果在計算上的用法。"
---

[上一篇](/teaching-topics/variance-of-linear-combination/)以 [Theorem 3.16](/teaching-topics/variance-of-linear-combination/#thm-covar-proper2) 給出線性組合的[變異數](/teaching-topics/variance/#def-variance)展開式，並在最後指出，多元[隨機變數](/teaching-topics/random-variables-and-pmf/#def-random-variable)的表示與運算會隨著變數個數增加而越來越複雜，因此在多變量分析與迴歸分析的領域中，我們更常改以向量的形式來處理一組多元隨機變數。

本篇即由此出發，先以 [Definition 3.17](#def-covar-matrix) 把所有變數之間的變異數與[共變異數](/teaching-topics/covariance/#def-covariance)收在同一個矩陣裡，再以 [Definition 3.18](#def-var-of-r-vvec) 說明這個矩陣其實就是[隨機向量](/teaching-topics/random-vectors-joint-pmf/#def-random-vector)的變異數，兩者事實上是同一件事情。接著介紹隨機向量在向量與矩陣上的運算: [Theorem 3.17](#thm-vector-operation) 處理常數向量與隨機向量的乘積，其中變異數的結果稱為二次形式，並由此證明共變異數矩陣必為正半定矩陣；[Theorem 3.18](#thm-matrix-operation) 則把常數向量換成常數矩陣，所得的結果是一個維度比 $1$ 還高的隨機向量。最後以一道二元常態的例題示範這些結果在計算上的用法。

## 共變異數矩陣

<div id="def-covar-matrix" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 3.17 (共變異數矩陣, covariance matrix)</div>

若 $X, Y, Z$ 為三隨機變數，則定義三者的**共變異數矩陣 <span lang="en">(covariance matrix)</span>** 為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbf{\Sigma}=
\begin{bmatrix}
\operatorname{Cov}(X,X) & \operatorname{Cov}(X,Y) & \operatorname{Cov}(X,Z)\\
\operatorname{Cov}(Y,X) & \operatorname{Cov}(Y,Y) & \operatorname{Cov}(Y,Z)\\
\operatorname{Cov}(Z,X) & \operatorname{Cov}(Z,Y) & \operatorname{Cov}(Z,Z)
\end{bmatrix}
=
\begin{bmatrix}
\sigma^{2}_{\sssig X} & \sigma_{\sssig XY} & \sigma_{\sssig XZ}\\
\sigma_{\sssig YX} & \sigma^{2}_{\sssig Y} & \sigma_{\sssig YZ}\\
\sigma_{\sssig ZX} & \sigma_{\sssig ZY} & \sigma^{2}_{\sssig Z}
\end{bmatrix}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbf{\Sigma}=
\begin{bmatrix}
\operatorname{Cov}(X,X) & \operatorname{Cov}(X,Y) & \operatorname{Cov}(X,Z)\\
\operatorname{Cov}(Y,X) & \operatorname{Cov}(Y,Y) & \operatorname{Cov}(Y,Z)\\
\operatorname{Cov}(Z,X) & \operatorname{Cov}(Z,Y) & \operatorname{Cov}(Z,Z)
\end{bmatrix}\\[0.55em]
&\quad =
\begin{bmatrix}
\sigma^{2}_{\sssig X} & \sigma_{\sssig XY} & \sigma_{\sssig XZ}\\
\sigma_{\sssig YX} & \sigma^{2}_{\sssig Y} & \sigma_{\sssig YZ}\\
\sigma_{\sssig ZX} & \sigma_{\sssig ZY} & \sigma^{2}_{\sssig Z}
\end{bmatrix}
\end{aligned}
$$

</div>

</div>

共變異數矩陣有一些地方需要注意:

(1) 上述定義中的 $\sigma^{2}_{\sssig X}, \sigma^{2}_{\sssig Y}, \sigma^{2}_{\sssig Z}$ 分別表 $X, Y, Z$ 的變異數；而 $\sigma_{\sssig XY}, \sigma_{\sssig XZ}, \sigma_{\sssig YZ},$ $\sigma_{\sssig YX}, \sigma_{\sssig ZX}, \sigma_{\sssig ZY}$ 則分別表 $X, Y, Z$ 間的共變異數，我們可以透過得知一個共變異數矩陣，得知所有變數間的變異數與共變異數。
{: .topic-paren-item}

(2) 由[共變異數的對稱性](/teaching-topics/covariance/#thm-covar-proper)，我們可以發現其實 $\sigma_{\sssig XY} = \sigma_{\sssig YX},$ $\sigma_{\sssig XZ} = \sigma_{\sssig ZX}$ 及 <span class="text-nowrap">$\sigma_{\sssig YZ} = \sigma_{\sssig ZY}$，</span>換言之，$\mathbf{\Sigma}$ 是一個對稱矩陣 <span lang="en">(symmetric matrix)</span>。
{: .topic-paren-item}

另外，由於我們曾經知道[變異數非負](/teaching-topics/variance/#thm-variance-properties)的特色，故一個合法的共變異數矩陣的主對角線 <span lang="en">(main diagonal)</span> 不應出現負數。例如以下的矩陣即不為合法的共變異數矩陣:
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{bmatrix}
-1 & 2 & 3\\
2 & 1 & 4\\
3 & 4 & 1
\end{bmatrix}
\qquad
\begin{bmatrix}
1 & 2 & 3\\
4 & 2 & 5\\
3 & 6 & 3
\end{bmatrix}
\qquad
\begin{bmatrix}
1 & 2 & 3\\
2 & 1 & 4\\
3 & 4 & 1
\end{bmatrix}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\begin{bmatrix}
-1 & 2 & 3\\
2 & 1 & 4\\
3 & 4 & 1
\end{bmatrix}\\[0.55em]
\begin{bmatrix}
1 & 2 & 3\\
4 & 2 & 5\\
3 & 6 & 3
\end{bmatrix}\\[0.55em]
\begin{bmatrix}
1 & 2 & 3\\
2 & 1 & 4\\
3 & 4 & 1
\end{bmatrix}
\end{gathered}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

讀者或許好奇，前二個矩陣不能當作共變異數矩陣的原因很明顯，但第三個矩陣為何不能作為共變異數矩陣呢？這個原因在稍後我們介紹[**相關係數 <span lang="en">(correlation coefficient)</span>**](/teaching-topics/correlation-coefficient/#def-corr)的時候會談到。

</div>

(3) 上述的定義並不僅限於三個隨機變數，我們可將其推廣至任意 $n$ 個隨機變數，如下定義:
{: .topic-paren-item}

若 $X_1, \ldots, X_n$ 為 $n$ 個隨機變數，則定義其共變異數矩陣為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbf{\Sigma}&=
\begin{bmatrix}
\operatorname{Cov}(X_1, X_1) & \operatorname{Cov}(X_1, X_2) & \cdots & \operatorname{Cov}(X_1, X_n)\\
\operatorname{Cov}(X_2, X_1) & \operatorname{Cov}(X_2, X_2) & \cdots & \operatorname{Cov}(X_2, X_n)\\
\vdots & \vdots & \ddots & \vdots\\
\operatorname{Cov}(X_n, X_1) & \operatorname{Cov}(X_n, X_2) & \cdots & \operatorname{Cov}(X_n, X_n)
\end{bmatrix}\\[0.45em]
&=
\begin{bmatrix}
\sigma^{2}_{1} & \sigma_{12} & \cdots & \sigma_{1n}\\
\sigma_{21} & \sigma^{2}_{2} & \cdots & \sigma_{2n}\\
\vdots & \vdots & \ddots & \vdots\\
\sigma_{n1} & \sigma_{n2} & \cdots & \sigma^{2}_{n}
\end{bmatrix}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbf{\Sigma}=
\begin{bmatrix}
\operatorname{Cov}(X_1, X_1) & \cdots & \operatorname{Cov}(X_1, X_n)\\
\vdots & \ddots & \vdots\\
\operatorname{Cov}(X_n, X_1) & \cdots & \operatorname{Cov}(X_n, X_n)
\end{bmatrix}\\[0.55em]
&\quad =
\begin{bmatrix}
\sigma^{2}_{1} & \sigma_{12} & \cdots & \sigma_{1n}\\
\sigma_{21} & \sigma^{2}_{2} & \cdots & \sigma_{2n}\\
\vdots & \vdots & \ddots & \vdots\\
\sigma_{n1} & \sigma_{n2} & \cdots & \sigma^{2}_{n}
\end{bmatrix}
\end{aligned}
$$

</div>

## 隨機向量的變異數

「共變異數矩陣」在統計上是很通用的稱呼，因為其描述了多元隨機變數間的變異數與共變異數。但實際上，該矩陣其實就是隨機向量的變異數，故有一派說法認為，我們應直接稱其為隨機向量的變異數 <span lang="en">(variance of random vector)</span>。這個說法在向量版本的定義中，將變得非常直觀，見下列定義。

<div id="def-var-of-r-vvec" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 3.18 (隨機向量的變異數, variance of random vector)</div>

隨機向量 $\boldsymbol{X}$ 的**共變異數矩陣**的定義為

$$
\mathbf{\Sigma}=\mathrm{Var}(\boldsymbol{X})=\mathbb{E}\Bigl[\,(\boldsymbol{X}-\boldsymbol{\mu})(\boldsymbol{X}-\boldsymbol{\mu})^{\mathrm{T}}\,\Bigr]
$$

其中

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\boldsymbol{\mu}=\mathbb{E}(\boldsymbol{X})=\mathbb{E}\Biggl(\begin{bmatrix} X_1\\ \vdots\\ X_n \end{bmatrix}\Biggr)=\begin{bmatrix} \mathbb{E}(X_1)\\ \vdots\\ \mathbb{E}(X_n) \end{bmatrix}=\begin{bmatrix} \mu_1\\ \vdots\\ \mu_n \end{bmatrix}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\boldsymbol{\mu}=\mathbb{E}(\boldsymbol{X})=\mathbb{E}\Biggl(\begin{bmatrix} X_1\\ \vdots\\ X_n \end{bmatrix}\Biggr)\\[0.55em]
&\quad =\begin{bmatrix} \mathbb{E}(X_1)\\ \vdots\\ \mathbb{E}(X_n) \end{bmatrix}=\begin{bmatrix} \mu_1\\ \vdots\\ \mu_n \end{bmatrix}
\end{aligned}
$$

</div>

表示 $\boldsymbol{X}$ 的[期望值](/teaching-topics/expectation/#def-expectation)。

</div>

[Definition 3.17](#def-covar-matrix) 與 [Definition 3.18](#def-var-of-r-vvec) 事實上是一樣的，因為針對一個矩陣的期望值，與針對一個向量的期望值，其定義都是「直接對每個元 <span lang="en">(element)</span> 都取期望值」，故有以下結果:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbf{\Sigma}&=\mathbb{E}\Bigl[\,(\boldsymbol{X}-\boldsymbol{\mu})(\boldsymbol{X}-\boldsymbol{\mu})^{\mathrm{T}}\,\Bigr]=\mathbb{E}\begin{bmatrix} (X_1-\mu_1)(X_1-\mu_1) & \cdots & (X_1-\mu_1)(X_n-\mu_n)\\ \vdots & \ddots & \vdots\\ (X_n-\mu_n)(X_1-\mu_1) & \cdots & (X_n-\mu_n)(X_n-\mu_n) \end{bmatrix}\\[0.45em]
&=\begin{bmatrix} \mathbb{E}\bigl[(X_1-\mu_1)(X_1-\mu_1)\bigr] & \cdots & \mathbb{E}\bigl[(X_1-\mu_1)(X_n-\mu_n)\bigr]\\ \vdots & \ddots & \vdots\\ \mathbb{E}\bigl[(X_n-\mu_n)(X_1-\mu_1)\bigr] & \cdots & \mathbb{E}\bigl[(X_n-\mu_n)(X_n-\mu_n)\bigr] \end{bmatrix}\\[0.45em]
&=\begin{bmatrix} \sigma_{1}^{2} & \sigma_{12} & \cdots & \sigma_{1n}\\ \sigma_{21} & \sigma_{2}^{2} & \cdots & \sigma_{2n}\\ \vdots & \vdots & \ddots & \vdots\\ \sigma_{n1} & \sigma_{n2} & \cdots & \sigma_{n}^{2} \end{bmatrix}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbf{\Sigma}=\mathbb{E}\Bigl[\,(\boldsymbol{X}-\boldsymbol{\mu})(\boldsymbol{X}-\boldsymbol{\mu})^{\mathrm{T}}\,\Bigr]\\[0.55em]
&\quad =\mathbb{E}\begin{bmatrix} (X_1-\mu_1)(X_1-\mu_1) & \cdots & (X_1-\mu_1)(X_n-\mu_n)\\ \vdots & \ddots & \vdots\\ (X_n-\mu_n)(X_1-\mu_1) & \cdots & (X_n-\mu_n)(X_n-\mu_n) \end{bmatrix}\\[0.55em]
&\quad =\begin{bmatrix} \mathbb{E}\bigl[(X_1-\mu_1)(X_1-\mu_1)\bigr] & \cdots & \mathbb{E}\bigl[(X_1-\mu_1)(X_n-\mu_n)\bigr]\\ \vdots & \ddots & \vdots\\ \mathbb{E}\bigl[(X_n-\mu_n)(X_1-\mu_1)\bigr] & \cdots & \mathbb{E}\bigl[(X_n-\mu_n)(X_n-\mu_n)\bigr] \end{bmatrix}\\[0.55em]
&\quad =\begin{bmatrix} \sigma_{1}^{2} & \sigma_{12} & \cdots & \sigma_{1n}\\ \sigma_{21} & \sigma_{2}^{2} & \cdots & \sigma_{2n}\\ \vdots & \vdots & \ddots & \vdots\\ \sigma_{n1} & \sigma_{n2} & \cdots & \sigma_{n}^{2} \end{bmatrix}
\end{aligned}
$$

</div>

除了上述性質外，如同變異數有非負性，共變異數矩陣也必須是**正半定 <span lang="en">(positive semi-definite)</span>** 的，但要證明這件事情，我們需要先學會隨機向量在矩陣上的運算。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

通常來說我們希望變異數為正，但至少我們接受變異數為 $0$ 的情況 (雖然這個情況有點無趣)，所以我們通常說變異數非負；同理，我們也未必要求共變異數矩陣一定要是**正定 <span lang="en">(positive definite)</span>** 的，但至少必須是**正半定**的。

</div>

## 常數向量與隨機向量的乘積

讀者在此應該特別注意的地方是，與矩陣相關的運算，都可以算是線性 (linear) 的運算，因此如果我們對隨機向量乘上某個向量 <span class="text-nowrap">$\boldsymbol{a}^{\mathrm{T}}$，</span>則其運算完全可以承襲過去我們所學的隨機變數的線性變換性質，包含[期望值的線性轉換](/teaching-topics/properties-of-expectation/#thm-expectation-linearity)，與[變異數平方擴充](/teaching-topics/variance/#thm-variance-properties)等等特性。我們在此以向量及矩陣的形式呈現。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

當然，其維度必須要可以相乘才行。

</div>

<div id="thm-vector-operation" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 3.17 (常數向量的線性形式, linear forms of a random vector)</div>

令 $\boldsymbol{a} = [\,a_1, \ldots, a_n\,]^{\mathrm{T}}$ 表示 $n \times 1$ 之常數向量，則

<ol class="topic-list-paren">
  <li>
$$
\mathbb{E}(\boldsymbol{a}^{\mathrm{T}}\boldsymbol{X})=\boldsymbol{a}^{\mathrm{T}}\boldsymbol{\mu}
$$
  </li>
  <li>
$$
\mathrm{Var}(\boldsymbol{a}^{\mathrm{T}}\boldsymbol{X})=\boldsymbol{a}^{\mathrm{T}}\,\mathbf{\Sigma}\,\boldsymbol{a}
$$
  </li>
</ol>

</div>

<div class="topic-proof" markdown="1">
**Proof.**

(1)
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(\boldsymbol{a}^{\mathrm{T}}\boldsymbol{X})=\mathbb{E}(a_1X_1 + \ldots + a_nX_n)=a_1\mu_1 + \ldots + a_n\mu_n=\sum_{i=1}^{n}a_i\mu_i=\boldsymbol{a}^{\mathrm{T}}\boldsymbol{\mu}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(\boldsymbol{a}^{\mathrm{T}}\boldsymbol{X})&=\mathbb{E}(a_1X_1 + \ldots + a_nX_n)\\[0.45em]
&=a_1\mu_1 + \ldots + a_n\mu_n\\[0.45em]
&=\sum_{i=1}^{n}a_i\mu_i=\boldsymbol{a}^{\mathrm{T}}\boldsymbol{\mu}
\end{aligned}
$$

</div>

(2)
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(\boldsymbol{a}^{\mathrm{T}}\boldsymbol{X})&=\mathbb{E}\Bigl[\,(\boldsymbol{a}^{\mathrm{T}}\boldsymbol{X}-\boldsymbol{a}^{\mathrm{T}}\boldsymbol{\mu})(\boldsymbol{a}^{\mathrm{T}}\boldsymbol{X}-\boldsymbol{a}^{\mathrm{T}}\boldsymbol{\mu})^{\mathrm{T}}\,\Bigr]=\mathbb{E}\Bigl[\,(\boldsymbol{a}^{\mathrm{T}}\boldsymbol{X}-\boldsymbol{a}^{\mathrm{T}}\boldsymbol{\mu})(\boldsymbol{X}^{\mathrm{T}}\boldsymbol{a}-\boldsymbol{\mu}^{\mathrm{T}}\boldsymbol{a})\,\Bigr]\\[0.45em]
&=\mathbb{E}\Bigl[\,\boldsymbol{a}^{\mathrm{T}}(\boldsymbol{X}-\boldsymbol{\mu})(\boldsymbol{X}^{\mathrm{T}}-\boldsymbol{\mu}^{\mathrm{T}})\,\boldsymbol{a}\,\Bigr]=\mathbb{E}\Bigl[\,\boldsymbol{a}^{\mathrm{T}}(\boldsymbol{X}-\boldsymbol{\mu})(\boldsymbol{X}-\boldsymbol{\mu})^{\mathrm{T}}\boldsymbol{a}\,\Bigr]\\[0.45em]
&=\boldsymbol{a}^{\mathrm{T}}\,\mathbb{E}\Bigl[\,(\boldsymbol{X}-\boldsymbol{\mu})(\boldsymbol{X}-\boldsymbol{\mu})^{\mathrm{T}}\,\Bigr]\boldsymbol{a}=\boldsymbol{a}^{\mathrm{T}}\,\mathbf{\Sigma}\,\boldsymbol{a}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathrm{Var}(\boldsymbol{a}^{\mathrm{T}}\boldsymbol{X})\\[0.45em]
&\quad =\mathbb{E}\Bigl[\,(\boldsymbol{a}^{\mathrm{T}}\boldsymbol{X}-\boldsymbol{a}^{\mathrm{T}}\boldsymbol{\mu})(\boldsymbol{a}^{\mathrm{T}}\boldsymbol{X}-\boldsymbol{a}^{\mathrm{T}}\boldsymbol{\mu})^{\mathrm{T}}\,\Bigr]\\[0.45em]
&\quad =\mathbb{E}\Bigl[\,(\boldsymbol{a}^{\mathrm{T}}\boldsymbol{X}-\boldsymbol{a}^{\mathrm{T}}\boldsymbol{\mu})(\boldsymbol{X}^{\mathrm{T}}\boldsymbol{a}-\boldsymbol{\mu}^{\mathrm{T}}\boldsymbol{a})\,\Bigr]\\[0.45em]
&\quad =\mathbb{E}\Bigl[\,\boldsymbol{a}^{\mathrm{T}}(\boldsymbol{X}-\boldsymbol{\mu})(\boldsymbol{X}^{\mathrm{T}}-\boldsymbol{\mu}^{\mathrm{T}})\,\boldsymbol{a}\,\Bigr]\\[0.45em]
&\quad =\mathbb{E}\Bigl[\,\boldsymbol{a}^{\mathrm{T}}(\boldsymbol{X}-\boldsymbol{\mu})(\boldsymbol{X}-\boldsymbol{\mu})^{\mathrm{T}}\boldsymbol{a}\,\Bigr]\\[0.45em]
&\quad =\boldsymbol{a}^{\mathrm{T}}\,\mathbb{E}\Bigl[\,(\boldsymbol{X}-\boldsymbol{\mu})(\boldsymbol{X}-\boldsymbol{\mu})^{\mathrm{T}}\,\Bigr]\boldsymbol{a}\\[0.45em]
&\quad =\boldsymbol{a}^{\mathrm{T}}\,\mathbf{\Sigma}\,\boldsymbol{a}
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

(2) 的結果稱為 $\boldsymbol{a}$ 的**二次形式 <span lang="en">(quadratic form)</span>**。

事實上，如果我們把變異數的平方擴充性 $\mathrm{Var}(aX) = a^2\mathrm{Var}(X) = a^2\sigma^2$ 改寫為 <span class="text-nowrap">$a^{\mathrm{T}}\sigma^2a$，</span>那這個性質就完全與變異數的平方擴充性相同了，因此也可以理解為向量版本的平方擴充性。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個理解雖然並不精確，但確實有其可類比性。我們以[二次形式](#thm-vector-operation)的角度，將 $\boldsymbol{a}^{\mathrm{T}}\,\mathbf{\Sigma}\,\boldsymbol{a}$ 理解為「$\boldsymbol{a}$ 的平方再乘以 <span class="text-nowrap">$\mathbf{\Sigma}$」；</span>而在單變數的平方擴充性中，$a$ 作為一個純量，永遠等於其自己的轉置，所以故意將 $\sigma^2$ 前方 $a$ 改寫為 <span class="text-nowrap">$a^{\mathrm{T}}$，</span>用以跟二次形式作為類比。

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

讀者可以嘗試令 $\boldsymbol{a} = [\,a_1, a_2\,]^{\mathrm{T}}$ 而 <span class="text-nowrap">$\boldsymbol{X} = \bigl[\,X_1, X_2\,\bigr]^{\mathrm{T}}$，</span>作為最簡單的隨機向量，則我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(\boldsymbol{a}^{\mathrm{T}}\boldsymbol{X})=a_1\mu_1 + a_2\mu_2\quad\text{與}\quad\mathrm{Var}(\boldsymbol{a}^{\mathrm{T}}\boldsymbol{X})=a_1^2\sigma^2_1 + a_2^2\sigma_2^2 + 2a_1a_2\sigma_{12}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{E}(\boldsymbol{a}^{\mathrm{T}}\boldsymbol{X})=a_1\mu_1 + a_2\mu_2\\[0.55em]
\text{與}\quad\mathrm{Var}(\boldsymbol{a}^{\mathrm{T}}\boldsymbol{X})=a_1^2\sigma^2_1 + a_2^2\sigma_2^2 + 2a_1a_2\sigma_{12}
\end{gathered}
$$

</div>

這一結果完全與多元隨機變數裡的結果相同。

</div>

這一點也體現出向量與矩陣的威力，過往在多元隨機變數中，只要隨機變數的數量稍微多了，就會讓人感到相當頭痛；但在向量與矩陣的世界裡，只要是線性的運算，哪怕是維度再高，都可以用一行式子來解決。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

事實上，機率論與統計學會用到的運算多數都是線性的，包含相關性等等的運算，絕大多數都是線性的，因此向量與矩陣在較為高等的統計相關學科中，確實扮演舉足輕重的地位。

</div>

此外，有了二次形式，我們便可以證明共變異數矩陣是正半定矩陣了:

<div class="topic-proof" markdown="1">
**Proof.**

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}(\boldsymbol{a}^{\mathrm{T}}\boldsymbol{X})=\mathrm{Var}\Biggl(\sum_{i=1}^{n}a_iX_i\Biggr)=\boldsymbol{a}^{\mathrm{T}}\,\mathbf{\Sigma}\,\boldsymbol{a}\geqslant 0,\ \forall\,\boldsymbol{a}\in\mathbb{R}^{n}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathrm{Var}(\boldsymbol{a}^{\mathrm{T}}\boldsymbol{X})=\mathrm{Var}\Biggl(\sum_{i=1}^{n}a_iX_i\Biggr)\\[0.45em]
&\quad =\boldsymbol{a}^{\mathrm{T}}\,\mathbf{\Sigma}\,\boldsymbol{a}\geqslant 0,\ \forall\,\boldsymbol{a}\in\mathbb{R}^{n}
\end{aligned}
$$

</div>

$\therefore \mathbf{\Sigma} = \mathrm{Var}(\boldsymbol{X})$ 為正半定矩陣。 <span class="topic-qed">$\square$</span>
</div>

## 常數矩陣與隨機向量的乘積

至此，讀者或許會有點疑惑: 透過常數向量與隨機向量的乘積，我們得到的結果，維度永遠都是 <span class="text-nowrap">$1$，</span>那要如何透過線性組合得到更高維度的結果呢？這個問題的答案是**矩陣**。

<div id="thm-matrix-operation" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 3.18 (矩陣的線性形式, matrix forms of a random vector)</div>

令

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbf{A}=\bigl[\,\boldsymbol{a}_1, \ldots, \boldsymbol{a}_k\,\bigr]^{\mathrm{T}}=\begin{bmatrix} \boldsymbol{a}_1^{\mathrm{T}}\\ \vdots\\ \boldsymbol{a}_{k}^{\mathrm{T}} \end{bmatrix}=\begin{bmatrix} a_{11} & \cdots & a_{1n}\\ \vdots & \ddots & \vdots\\ a_{k1} & \cdots & a_{kn} \end{bmatrix}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbf{A}=\bigl[\,\boldsymbol{a}_1, \ldots, \boldsymbol{a}_k\,\bigr]^{\mathrm{T}}=\begin{bmatrix} \boldsymbol{a}_1^{\mathrm{T}}\\ \vdots\\ \boldsymbol{a}_{k}^{\mathrm{T}} \end{bmatrix}\\[0.55em]
&\quad =\begin{bmatrix} a_{11} & \cdots & a_{1n}\\ \vdots & \ddots & \vdots\\ a_{k1} & \cdots & a_{kn} \end{bmatrix}
\end{aligned}
$$

</div>

表示 $k \times n$ 之常數矩陣，則

<ol class="topic-list-paren">
  <li>
$$
\mathbb{E}(\mathbf{A}\boldsymbol{X})=\mathbf{A}\boldsymbol{\mu}
$$
  </li>
  <li>
$$
\mathrm{Var}(\mathbf{A}\boldsymbol{X})=\mathbf{A}\mathbf{\Sigma}\mathbf{A}^{\mathrm{T}}
$$
  </li>
</ol>

</div>

<div class="topic-proof" markdown="1">
**Proof.**

(1)
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(\mathbf{A}\boldsymbol{X})&=\mathbb{E}\Biggl(\begin{bmatrix} \boldsymbol{a}_1^{\mathrm{T}}\\ \vdots\\ \boldsymbol{a}_{k}^{\mathrm{T}} \end{bmatrix}\boldsymbol{X}\Biggr)=\mathbb{E}\Biggl(\begin{bmatrix} \boldsymbol{a}_1^{\mathrm{T}}\boldsymbol{X}\\ \vdots\\ \boldsymbol{a}_{k}^{\mathrm{T}}\boldsymbol{X} \end{bmatrix}\Biggr)\\[0.45em]
&=\begin{bmatrix} \boldsymbol{a}_1^{\mathrm{T}}\boldsymbol{\mu}\\ \vdots\\ \boldsymbol{a}_{k}^{\mathrm{T}}\boldsymbol{\mu} \end{bmatrix}=\begin{bmatrix} \boldsymbol{a}_1^{\mathrm{T}}\\ \vdots\\ \boldsymbol{a}_{k}^{\mathrm{T}} \end{bmatrix}\boldsymbol{\mu}=\mathbf{A}\boldsymbol{\mu}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}(\mathbf{A}\boldsymbol{X})=\mathbb{E}\Biggl(\begin{bmatrix} \boldsymbol{a}_1^{\mathrm{T}}\\ \vdots\\ \boldsymbol{a}_{k}^{\mathrm{T}} \end{bmatrix}\boldsymbol{X}\Biggr)\\[0.55em]
&\quad =\mathbb{E}\Biggl(\begin{bmatrix} \boldsymbol{a}_1^{\mathrm{T}}\boldsymbol{X}\\ \vdots\\ \boldsymbol{a}_{k}^{\mathrm{T}}\boldsymbol{X} \end{bmatrix}\Biggr)=\begin{bmatrix} \boldsymbol{a}_1^{\mathrm{T}}\boldsymbol{\mu}\\ \vdots\\ \boldsymbol{a}_{k}^{\mathrm{T}}\boldsymbol{\mu} \end{bmatrix}\\[0.55em]
&\quad =\begin{bmatrix} \boldsymbol{a}_1^{\mathrm{T}}\\ \vdots\\ \boldsymbol{a}_{k}^{\mathrm{T}} \end{bmatrix}\boldsymbol{\mu}=\mathbf{A}\boldsymbol{\mu}
\end{aligned}
$$

</div>

(2)
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(\mathbf{A}\boldsymbol{X})&=\mathbb{E}\Bigl[\,(\mathbf{A}\boldsymbol{X}-\mathbf{A}\boldsymbol{\mu})(\mathbf{A}\boldsymbol{X}-\mathbf{A}\boldsymbol{\mu})^{\mathrm{T}}\,\Bigr]=\mathbb{E}\Bigl[\,(\mathbf{A}\boldsymbol{X}-\mathbf{A}\boldsymbol{\mu})(\boldsymbol{X}^{\mathrm{T}}\mathbf{A}^{\mathrm{T}}-\boldsymbol{\mu}^{\mathrm{T}}\mathbf{A}^{\mathrm{T}})\,\Bigr]\\[0.45em]
&=\mathbb{E}\Bigl[\,\mathbf{A}(\boldsymbol{X}-\boldsymbol{\mu})(\boldsymbol{X}^{\mathrm{T}}-\boldsymbol{\mu}^{\mathrm{T}})\mathbf{A}^{\mathrm{T}}\,\Bigr]=\mathbb{E}\Bigl[\,\mathbf{A}(\boldsymbol{X}-\boldsymbol{\mu})(\boldsymbol{X}-\boldsymbol{\mu})^{\mathrm{T}}\mathbf{A}^{\mathrm{T}}\,\Bigr]\\[0.45em]
&=\mathbf{A}\,\mathbb{E}\Bigl[\,(\boldsymbol{X}-\boldsymbol{\mu})(\boldsymbol{X}-\boldsymbol{\mu})^{\mathrm{T}}\,\Bigr]\,\mathbf{A}^{\mathrm{T}}=\mathbf{A}\mathbf{\Sigma}\mathbf{A}^{\mathrm{T}}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathrm{Var}(\mathbf{A}\boldsymbol{X})\\[0.45em]
&\quad =\mathbb{E}\Bigl[\,(\mathbf{A}\boldsymbol{X}-\mathbf{A}\boldsymbol{\mu})(\mathbf{A}\boldsymbol{X}-\mathbf{A}\boldsymbol{\mu})^{\mathrm{T}}\,\Bigr]\\[0.45em]
&\quad =\mathbb{E}\Bigl[\,(\mathbf{A}\boldsymbol{X}-\mathbf{A}\boldsymbol{\mu})(\boldsymbol{X}^{\mathrm{T}}\mathbf{A}^{\mathrm{T}}-\boldsymbol{\mu}^{\mathrm{T}}\mathbf{A}^{\mathrm{T}})\,\Bigr]\\[0.45em]
&\quad =\mathbb{E}\Bigl[\,\mathbf{A}(\boldsymbol{X}-\boldsymbol{\mu})(\boldsymbol{X}^{\mathrm{T}}-\boldsymbol{\mu}^{\mathrm{T}})\mathbf{A}^{\mathrm{T}}\,\Bigr]\\[0.45em]
&\quad =\mathbb{E}\Bigl[\,\mathbf{A}(\boldsymbol{X}-\boldsymbol{\mu})(\boldsymbol{X}-\boldsymbol{\mu})^{\mathrm{T}}\mathbf{A}^{\mathrm{T}}\,\Bigr]\\[0.45em]
&\quad =\mathbf{A}\,\mathbb{E}\Bigl[\,(\boldsymbol{X}-\boldsymbol{\mu})(\boldsymbol{X}-\boldsymbol{\mu})^{\mathrm{T}}\,\Bigr]\,\mathbf{A}^{\mathrm{T}}\\[0.45em]
&\quad =\mathbf{A}\mathbf{\Sigma}\mathbf{A}^{\mathrm{T}}
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

如果我們不注意看，這個定理與證明，好像與 [Theorem 3.17](#thm-vector-operation) 幾乎相同，但事實上，如果讀者注意細究其維度，我們將會發現，$\mathbf{A}\boldsymbol{X}$ 事實上已經是個維度比 $1$ 還高的隨機向量了，這些結果再再說明了向量及矩陣的威力。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

特別需要注意的地方是，我們習慣上喜歡將向量寫成行向量，因此在 [Theorem 3.17](#thm-vector-operation) 中，常數向量 $\boldsymbol{a}$ 與隨機向量 $\boldsymbol{X}$ 相乘時，為了使維度可以相乘，我們會把 $\boldsymbol{a}$ 轉置；但在 [Theorem 3.18](#thm-matrix-operation) 中，常數矩陣 $\mathbf{A}$ 原本就已經可以與 $\boldsymbol{X}$ 相乘了，所以不需要額外轉置。

</div>

## 以共變異數矩陣求線性組合的變異數

<div id="ex-bivariate-normal-covariance" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.41</div>

<div lang="en" markdown="1">
Suppose that the random vector formed by $X$ and $Y$ follows a bivariate normal distribution, that is,

$$
\begin{bmatrix} X\\ Y \end{bmatrix}\sim\mathcal{N}_{2}\Biggl(\begin{bmatrix} 3\\ 5 \end{bmatrix},\ \begin{bmatrix} 4 & 2\\ 2 & 3 \end{bmatrix}\Biggr)
$$

Determine the variance of <span class="text-nowrap">$3X+2Y$.</span>
</div>

**[ 法一 ]**

由 $X$ 與 $Y$ 的共變異數矩陣為

$$
\begin{bmatrix} 4 & 2\\ 2 & 3 \end{bmatrix}
$$

可知

$$
\mathrm{Var}(X)=4,\ \ \mathrm{Var}(Y)=3,\ \ \operatorname{Cov}(X, Y)=2
$$

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\Longrightarrow\ \mathrm{Var}(3X+2Y)=3^{2}\cdot\mathrm{Var}(X) + 2^{2}\cdot\mathrm{Var}(Y) + 2\cdot 3\cdot 2\cdot\operatorname{Cov}(X, Y)=72
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\Longrightarrow\ \mathrm{Var}(3X+2Y)\\[0.45em]
&\quad =3^{2}\cdot\mathrm{Var}(X) + 2^{2}\cdot\mathrm{Var}(Y)\\[0.2em]
&\qquad\quad + 2\cdot 3\cdot 2\cdot\operatorname{Cov}(X, Y)\\[0.45em]
&\quad =72
\end{aligned}
$$

</div>

**[ 法二 ]**

所求為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}(3X+2Y)=\mathrm{Var}\Biggl(\Bigl[\,3\ \ 2\,\Bigr]\begin{bmatrix} X\\ Y \end{bmatrix}\Biggr)=\Bigl[\,3\ \ 2\,\Bigr]\begin{bmatrix} 4 & 2\\ 2 & 3 \end{bmatrix}\begin{bmatrix} 3\\ 2 \end{bmatrix}=72
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathrm{Var}(3X+2Y)=\mathrm{Var}\Biggl(\Bigl[\,3\ \ 2\,\Bigr]\begin{bmatrix} X\\ Y \end{bmatrix}\Biggr)\\[0.55em]
&\quad =\Bigl[\,3\ \ 2\,\Bigr]\begin{bmatrix} 4 & 2\\ 2 & 3 \end{bmatrix}\begin{bmatrix} 3\\ 2 \end{bmatrix}=72
\end{aligned}
$$

</div>

</div>

讀者目前應該已經能夠理解與掌握共變異數，但是，作為刻畫 $X$ 與 $Y$ 共變關係的共變異數，卻沒有範圍上的限制，僅知道共同變化的「方向」，不知道「程度」，這該如何是好呢？為了解決這個問題，我們將會介紹[**相關係數**](/teaching-topics/correlation-coefficient/#def-corr)。

## 本篇小結

[Definition 3.17](#def-covar-matrix) 把三個隨機變數兩兩之間的變異數與共變異數收在同一個矩陣裡，主對角線上的 $\sigma^{2}_{\sssig X}, \sigma^{2}_{\sssig Y}, \sigma^{2}_{\sssig Z}$ 是各個變數自己的變異數，其餘位置則是變數之間的共變異數，因此知道一個共變異數矩陣，就等於知道所有變數之間的變異數與共變異數。由[共變異數的對稱性](/teaching-topics/covariance/#thm-covar-proper)可知 $\mathbf{\Sigma}$ 必為對稱矩陣，又由[變異數非負](/teaching-topics/variance/#thm-variance-properties)可知主對角線不應出現負數，這兩件事各排除了一類不合法的矩陣；至於主對角線為正、又對稱的矩陣為何仍可能不合法，要等到相關係數才能回答。同樣的定義並不限於三個變數，$n$ 個變數的版本只是把矩陣擴充為 $n \times n$ 而已。

[Definition 3.18](#def-var-of-r-vvec) 改以隨機向量書寫同一件事情，也就是 $\mathbf{\Sigma}$ $=$ $\mathrm{Var}(\boldsymbol{X})$ $=$ $\mathbb{E}\bigl[(\boldsymbol{X}-\boldsymbol{\mu})(\boldsymbol{X}-\boldsymbol{\mu})^{\mathrm{T}}\bigr]$ 這一條式子。兩個定義之所以一樣，是因為矩陣與向量的期望值都是「直接對每個元都取期望值」，把定義中兩個向量相乘所得的矩陣逐元取期望值，得到的正是 [Definition 3.17](#def-covar-matrix) 的那個矩陣。共變異數矩陣還必須是正半定的，而要證明這件事，得先學會隨機向量在向量與矩陣上的運算。

[Theorem 3.17](#thm-vector-operation) 處理常數向量與隨機向量的乘積。期望值為 $\boldsymbol{a}^{\mathrm{T}}\boldsymbol{\mu}$ 這個向量版本的線性轉換，變異數則為 $\boldsymbol{a}^{\mathrm{T}}\,\mathbf{\Sigma}\,\boldsymbol{a}$ 這個二次形式，也就是向量版本的平方擴充性。證明的關鍵一步是把轉置拆開之後，$\boldsymbol{a}^{\mathrm{T}}$ 與 $\boldsymbol{a}$ 分別提到期望值的兩側，中間剩下的恰好就是 $\mathbf{\Sigma}$ 的定義。由於變異數必定非負，二次形式對任意 $\boldsymbol{a}$ 都不小於 <span class="text-nowrap">$0$，</span>共變異數矩陣因而是正半定矩陣。[Theorem 3.18](#thm-matrix-operation) 把常數向量換成 $k \times n$ 的常數矩陣，兩式的形狀幾乎相同，但 $\mathbf{A}\boldsymbol{X}$ 已經是維度比 $1$ 還高的隨機向量，其變異數為 <span class="text-nowrap">$\mathbf{A}\mathbf{\Sigma}\mathbf{A}^{\mathrm{T}}$。</span>兩者的差別只在於習慣上向量寫成行向量，故 $\boldsymbol{a}$ 需要轉置，而 $\mathbf{A}$ 本來就可以與 $\boldsymbol{X}$ 相乘。

[Example 3.41](#ex-bivariate-normal-covariance) 以一組二元常態示範上述結果的用法。由共變異數矩陣得到兩個變異數與一個共變異數之後，可以逐項展開求得 $\mathrm{Var}(3X+2Y)$ 這個值，也可以直接把係數排成一個列向量，以二次形式一步算出同樣的 $72$ 這個答案。

[下一篇](/teaching-topics/correlation-coefficient/)將介紹相關係數，它把共變異數除以兩個[標準差](/teaching-topics/variance-standard-deviation/#def-standard-deviation)，使共同變化的「程度」也有範圍上的限制。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
