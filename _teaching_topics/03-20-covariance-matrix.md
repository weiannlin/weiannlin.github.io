---
title: "共變異數矩陣"
subtitle: "The Covariance Matrix"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 20
order: 320
permalink: /lecture-notes/covariance-matrix/
date: 2026-08-13
published: true
excerpt: "共變異數矩陣 $\\mathbf{\\Sigma}$ 將隨機向量各分量的變異數與成對共變異數收錄於同一對稱矩陣。本篇推導常數向量線性形式的二次形式變異數 $\\boldsymbol{a}^{\\mathrm{T}}\\mathbf{\\Sigma}\\boldsymbol{a}$ 以證明 $\\mathbf{\\Sigma}$ 必為正半定，並推廣至常數矩陣轉換下的期望值向量與共變異數矩陣。"
---

[上一篇](/lecture-notes/variance-of-linear-combination/)以 [Theorem 3.16](/lecture-notes/variance-of-linear-combination/#thm-covar-proper2) 給出線性組合的[變異數](/lecture-notes/variance/#def-variance)展開式，並在最後指出，多元[隨機變數](/lecture-notes/random-variables-and-pmf/#def-random-variable)的表示與運算會隨著變數個數增加而越來越複雜，因此在多變量分析與迴歸分析的領域中，我們更常改以向量的形式來處理一組多元隨機變數。

本篇即由此出發，先以 [Definition 3.17](#def-covar-matrix) 把所有變數之間的變異數與[共變異數](/lecture-notes/covariance/#def-covariance)收在同一個矩陣裡，再以 [Definition 3.18](#def-var-of-r-vvec) 說明這個矩陣其實就是[隨機向量](/lecture-notes/random-vectors-joint-pmf/#def-random-vector)的變異數，兩者事實上是同一件事情。接著介紹隨機向量在向量與矩陣上的運算，其中 [Theorem 3.17](#thm-vector-operation) 處理常數向量與隨機向量的乘積，其中變異數的結果稱為二次形式，並由此證明共變異數矩陣必為正半定矩陣；[Theorem 3.18](#thm-matrix-operation) 則把常數向量換成常數矩陣，所得的結果是一個維度比 $1$ 還高的隨機向量。最後以一道二元常態的例題示範這些結果在計算上的用法。

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
\mathbf{\Sigma}&=
\begin{bmatrix}
\operatorname{Cov}(X,X) & \operatorname{Cov}(X,Y) & \operatorname{Cov}(X,Z)\\
\operatorname{Cov}(Y,X) & \operatorname{Cov}(Y,Y) & \operatorname{Cov}(Y,Z)\\
\operatorname{Cov}(Z,X) & \operatorname{Cov}(Z,Y) & \operatorname{Cov}(Z,Z)
\end{bmatrix}\\[0.55em]
&=
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

(1) 上述定義中的 $\sigma^{2}\_{\sssig X}, \sigma^{2}\_{\sssig Y}, \sigma^{2}\_{\sssig Z}$ 分別表 $X, Y, Z$ 的變異數；而 $\sigma\_{\sssig XY}, \sigma\_{\sssig XZ}, \sigma\_{\sssig YZ},$ $\sigma\_{\sssig YX}, \sigma\_{\sssig ZX}, \sigma\_{\sssig ZY}$ 則分別表 $X, Y, Z$ 間的共變異數，故由共變異數矩陣即可一併掌握各變數的變異數與所有成對共變異數。
{: .topic-paren-item}

(2) 由[共變異數的對稱性](/lecture-notes/covariance/#thm-covar-proper)可知 $\sigma\_{\sssig XY} = \sigma\_{\sssig YX},$ $\sigma\_{\sssig XZ} = \sigma\_{\sssig ZX}$ 及 <span class="text-nowrap">$\sigma_{\sssig YZ} = \sigma_{\sssig ZY}$，</span>換言之，$\mathbf{\Sigma}$ 必為對稱矩陣 <span lang="en">(symmetric matrix)</span>。
{: .topic-paren-item}

另外，由[變異數非負](/lecture-notes/variance/#thm-variance-properties)可知，合法的共變異數矩陣其主對角線 <span lang="en">(main diagonal)</span> 不得出現負數。例如以下三個矩陣皆非合法的共變異數矩陣:
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

前兩個矩陣分別因主對角線出現負數與矩陣不對稱而不合法；第三個矩陣雖對稱且主對角線皆為正，但非對角線的共變異數超出合理界限，其具體判準將於後文介紹[**相關係數 <span lang="en">(correlation coefficient)</span>**](/lecture-notes/correlation-coefficient/#def-corr)與變異數-共變異數不等式時說明。

</div>

(3) 上述定義不限於三個隨機變數，可將其推廣至任意 $n$ 個隨機變數如下:
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
\mathbf{\Sigma}&=
\begin{bmatrix}
\operatorname{Cov}(X_1, X_1) & \cdots & \operatorname{Cov}(X_1, X_n)\\
\vdots & \ddots & \vdots\\
\operatorname{Cov}(X_n, X_1) & \cdots & \operatorname{Cov}(X_n, X_n)
\end{bmatrix}\\[0.55em]
&=
\begin{bmatrix}
\sigma^{2}_{1} & \cdots & \sigma_{1n}\\
\vdots & \ddots & \vdots\\
\sigma_{n1} & \cdots & \sigma^{2}_{n}
\end{bmatrix}
\end{aligned}
$$

</div>

## 隨機向量的變異數

「共變異數矩陣」是統計學通用的稱呼，用以統整多元隨機變數各自的變異數與彼此間的共變異數。從隨機向量的觀點來看，此矩陣本身即為**隨機向量的變異數 <span lang="en">(variance of random vector)</span>**，這一點在向量形式的定義中格外清楚，見下列定義。

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
\boldsymbol{\mu}&=\mathbb{E}(\boldsymbol{X})=\mathbb{E}\Biggl(\begin{bmatrix} X_1\\ \vdots\\ X_n \end{bmatrix}\Biggr)\\[0.55em]
&=\begin{bmatrix} \mathbb{E}(X_1)\\ \vdots\\ \mathbb{E}(X_n) \end{bmatrix}=\begin{bmatrix} \mu_1\\ \vdots\\ \mu_n \end{bmatrix}
\end{aligned}
$$

</div>

表示 $\boldsymbol{X}$ 的[期望值](/lecture-notes/expectation/#def-expectation)。

</div>

[Definition 3.17](#def-covar-matrix) 與 [Definition 3.18](#def-var-of-r-vvec) 完全等價。由於矩陣與向量的期望值皆定義為直接對每個元 <span lang="en">(element)</span> 逐一取期望值，展開可得

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
&=\mathbb{E}\begin{bmatrix} (X_1-\mu_1)(X_1-\mu_1) & \cdots & (X_1-\mu_1)(X_n-\mu_n)\\ \vdots & \ddots & \vdots\\ (X_n-\mu_n)(X_1-\mu_1) & \cdots & (X_n-\mu_n)(X_n-\mu_n) \end{bmatrix}\\[0.55em]
&=\begin{bmatrix} \mathbb{E}[(X_1-\mu_1)(X_1-\mu_1)] & \cdots & \mathbb{E}[(X_1-\mu_1)(X_n-\mu_n)]\\ \vdots & \ddots & \vdots\\ \mathbb{E}[(X_n-\mu_n)(X_1-\mu_1)] & \cdots & \mathbb{E}[(X_n-\mu_n)(X_n-\mu_n)] \end{bmatrix}\\[0.55em]
&=\begin{bmatrix} \sigma_{1}^{2} & \sigma_{12} & \cdots & \sigma_{1n}\\ \sigma_{21} & \sigma_{2}^{2} & \cdots & \sigma_{2n}\\ \vdots & \vdots & \ddots & \vdots\\ \sigma_{n1} & \sigma_{n2} & \cdots & \sigma_{n}^{2} \end{bmatrix}
\end{aligned}
$$

</div>

如同單變數變異數允許退化為 $0$ 而僅要求非負，我們亦不強求共變異數矩陣必為**正定 <span lang="en">(positive definite)</span>**，但至少須為**正半定 <span lang="en">(positive semi-definite)</span>**。為證明此性質，以下先建立隨機向量的線性運算規則。

## 常數向量與隨機向量的乘積

向量與矩陣乘法本質上屬於線性 (linear) 運算。在維度相容的前提下，將隨機向量左乘常數列向量 <span class="text-nowrap">$\boldsymbol{a}^{\mathrm{T}}$，</span>其性質直接承襲單變數的線性轉換規則，包含[期望值的線性轉換](/lecture-notes/properties-of-expectation/#thm-expectation-linearity)與[變異數的平方伸縮性](/lecture-notes/variance/#thm-variance-properties)，以向量與矩陣形式表述如下。

<div id="thm-vector-operation" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 3.17 (常數向量的線性形式, linear forms of a random vector)</div>

令 $\boldsymbol{a} = [\,a_1, \ldots, a_n\,]^{\mathrm{T}}$ 表示 $n \times 1$ 之常數向量，則

<ol class="topic-list-paren topic-list-paren--math">
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
\mathbb{E}(\boldsymbol{a}^{\mathrm{T}}\boldsymbol{X})=\mathbb{E}(a_1X_1 + \cdots + a_nX_n)=a_1\mu_1 + \cdots + a_n\mu_n=\sum_{i=1}^{n}a_i\mu_i=\boldsymbol{a}^{\mathrm{T}}\boldsymbol{\mu}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(\boldsymbol{a}^{\mathrm{T}}\boldsymbol{X})&=\mathbb{E}(a_1X_1 + \cdots + a_nX_n)\\[0.45em]
&=a_1\mu_1 + \cdots + a_n\mu_n\\[0.45em]
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
&=\mathbb{E}\Bigl[\,(\boldsymbol{a}^{\mathrm{T}}\boldsymbol{X}-\boldsymbol{a}^{\mathrm{T}}\boldsymbol{\mu})(\boldsymbol{a}^{\mathrm{T}}\boldsymbol{X}-\boldsymbol{a}^{\mathrm{T}}\boldsymbol{\mu})^{\mathrm{T}}\,\Bigr]\\[0.45em]
&=\mathbb{E}\Bigl[\,(\boldsymbol{a}^{\mathrm{T}}\boldsymbol{X}-\boldsymbol{a}^{\mathrm{T}}\boldsymbol{\mu})(\boldsymbol{X}^{\mathrm{T}}\boldsymbol{a}-\boldsymbol{\mu}^{\mathrm{T}}\boldsymbol{a})\,\Bigr]\\[0.45em]
&=\mathbb{E}\Bigl[\,\boldsymbol{a}^{\mathrm{T}}(\boldsymbol{X}-\boldsymbol{\mu})(\boldsymbol{X}^{\mathrm{T}}-\boldsymbol{\mu}^{\mathrm{T}})\,\boldsymbol{a}\,\Bigr]\\[0.45em]
&=\mathbb{E}\Bigl[\,\boldsymbol{a}^{\mathrm{T}}(\boldsymbol{X}-\boldsymbol{\mu})(\boldsymbol{X}-\boldsymbol{\mu})^{\mathrm{T}}\boldsymbol{a}\,\Bigr]\\[0.45em]
&=\boldsymbol{a}^{\mathrm{T}}\,\mathbb{E}\Bigl[\,(\boldsymbol{X}-\boldsymbol{\mu})(\boldsymbol{X}-\boldsymbol{\mu})^{\mathrm{T}}\,\Bigr]\boldsymbol{a}\\[0.45em]
&=\boldsymbol{a}^{\mathrm{T}}\,\mathbf{\Sigma}\,\boldsymbol{a}
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

第 (2) 式的結果 $\boldsymbol{a}^{\mathrm{T}}\,\mathbf{\Sigma}\,\boldsymbol{a}$ 稱為 $\boldsymbol{a}$ 的**二次形式 <span lang="en">(quadratic form)</span>**。在單變數情形中，純量 $a$ 等於其自身的轉置 <span class="text-nowrap">$a^{\mathrm{T}}$，</span>若將變異數的平方伸縮式 $\mathrm{Var}(aX)=a^{2}\sigma^{2}$ 改寫為 <span class="text-nowrap">$a^{\mathrm{T}}\sigma^{2}a$，</span>便與[二次形式](#thm-vector-operation) $\boldsymbol{a}^{\mathrm{T}}\,\mathbf{\Sigma}\,\boldsymbol{a}$ 的結構完全對應，故第 (2) 式可視為向量版本的平方伸縮性。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

以二維情形為例，取 $\boldsymbol{a} = [\,a\_1, a\_2\,]^{\mathrm{T}}$ 與 <span class="text-nowrap">$\boldsymbol{X} = \bigl[\,X_1, X_2\,\bigr]^{\mathrm{T}}$，</span>代入上式即得

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

此結果與前文逐項展開所得的線性組合期望值與變異數公式完全一致。

</div>

由此亦可見向量與矩陣記號的優勢。隨著變數個數增加，逐項加總的展開式會迅速膨脹，而矩陣記號能將任意維度的線性運算濃縮為單一簡潔公式；由於機率論與高等統計學中的核心運算 (如線性組合、共變異與相關結構) 大多具備線性形式，向量與矩陣遂成為多變量統計分析不可或缺的基礎工具。

利用二次形式的變異數表法，即可立即證明共變異數矩陣必為正半定矩陣:

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
\mathrm{Var}(\boldsymbol{a}^{\mathrm{T}}\boldsymbol{X})&=\mathrm{Var}\Biggl(\sum_{i=1}^{n}a_iX_i\Biggr)\\[0.45em]
&=\boldsymbol{a}^{\mathrm{T}}\,\mathbf{\Sigma}\,\boldsymbol{a}\geqslant 0,\ \forall\,\boldsymbol{a}\in\mathbb{R}^{n}
\end{aligned}
$$

</div>

$\therefore \mathbf{\Sigma} = \mathrm{Var}(\boldsymbol{X})$ 為正半定矩陣。 <span class="topic-qed">$\square$</span>
</div>

## 常數矩陣與隨機向量的乘積

常數列向量與隨機向量相乘所得的線性組合恆為純量 (維度為 <span class="text-nowrap">$1$)；</span>若要同時由多組線性組合構成更高維度的隨機向量，只需將常數向量擴充為常數**矩陣**。

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
\mathbf{A}&=\bigl[\,\boldsymbol{a}_1, \ldots, \boldsymbol{a}_k\,\bigr]^{\mathrm{T}}=\begin{bmatrix} \boldsymbol{a}_1^{\mathrm{T}}\\ \vdots\\ \boldsymbol{a}_{k}^{\mathrm{T}} \end{bmatrix}\\[0.55em]
&=\begin{bmatrix} a_{11} & \cdots & a_{1n}\\ \vdots & \ddots & \vdots\\ a_{k1} & \cdots & a_{kn} \end{bmatrix}
\end{aligned}
$$

</div>

表示 $k \times n$ 之常數矩陣，則

<ol class="topic-list-paren topic-list-paren--math">
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
\mathbb{E}(\mathbf{A}\boldsymbol{X})&=\mathbb{E}\Biggl(\begin{bmatrix} \boldsymbol{a}_1^{\mathrm{T}}\\ \vdots\\ \boldsymbol{a}_{k}^{\mathrm{T}} \end{bmatrix}\boldsymbol{X}\Biggr)\\[0.55em]
&=\mathbb{E}\Biggl(\begin{bmatrix} \boldsymbol{a}_1^{\mathrm{T}}\boldsymbol{X}\\ \vdots\\ \boldsymbol{a}_{k}^{\mathrm{T}}\boldsymbol{X} \end{bmatrix}\Biggr)=\begin{bmatrix} \boldsymbol{a}_1^{\mathrm{T}}\boldsymbol{\mu}\\ \vdots\\ \boldsymbol{a}_{k}^{\mathrm{T}}\boldsymbol{\mu} \end{bmatrix}\\[0.55em]
&=\begin{bmatrix} \boldsymbol{a}_1^{\mathrm{T}}\\ \vdots\\ \boldsymbol{a}_{k}^{\mathrm{T}} \end{bmatrix}\boldsymbol{\mu}=\mathbf{A}\boldsymbol{\mu}
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
\mathrm{Var}(&\mathbf{A}\boldsymbol{X}) =\mathbb{E}\Bigl[\,(\mathbf{A}\boldsymbol{X}-\mathbf{A}\boldsymbol{\mu})(\mathbf{A}\boldsymbol{X}-\mathbf{A}\boldsymbol{\mu})^{\mathrm{T}}\,\Bigr]\\[0.45em]
&=\mathbb{E}\Bigl[\,(\mathbf{A}\boldsymbol{X}-\mathbf{A}\boldsymbol{\mu})(\boldsymbol{X}^{\mathrm{T}}\mathbf{A}^{\mathrm{T}}-\boldsymbol{\mu}^{\mathrm{T}}\mathbf{A}^{\mathrm{T}})\,\Bigr]\\[0.45em]
&=\mathbb{E}\Bigl[\,\mathbf{A}(\boldsymbol{X}-\boldsymbol{\mu})(\boldsymbol{X}^{\mathrm{T}}-\boldsymbol{\mu}^{\mathrm{T}})\mathbf{A}^{\mathrm{T}}\,\Bigr]\\[0.45em]
&=\mathbb{E}\Bigl[\,\mathbf{A}(\boldsymbol{X}-\boldsymbol{\mu})(\boldsymbol{X}-\boldsymbol{\mu})^{\mathrm{T}}\mathbf{A}^{\mathrm{T}}\,\Bigr]\\[0.45em]
&=\mathbf{A}\,\mathbb{E}\Bigl[\,(\boldsymbol{X}-\boldsymbol{\mu})(\boldsymbol{X}-\boldsymbol{\mu})^{\mathrm{T}}\,\Bigr]\,\mathbf{A}^{\mathrm{T}}\\[0.45em]
&=\mathbf{A}\mathbf{\Sigma}\mathbf{A}^{\mathrm{T}}
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

[Theorem 3.18](#thm-matrix-operation) 的形式與證明步驟雖與 [Theorem 3.17](#thm-vector-operation) 相似，但兩者的結果維度不同。此處 $\mathbf{A}\boldsymbol{X}$ 為 $k\times 1$ 隨機向量，而 $\mathrm{Var}(\mathbf{A}\boldsymbol{X})=\mathbf{A}\mathbf{\Sigma}\mathbf{A}^{\mathrm{T}}$ 則為階數 $k\times k$ 的共變異數矩陣。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

依慣例我們將向量寫為行向量，故在 [Theorem 3.17](#thm-vector-operation) 中須先將 $n\times 1$ 的常數向量 $\boldsymbol{a}$ 轉置為 $1\times n$ 的 <span class="text-nowrap">$\boldsymbol{a}^{\mathrm{T}}$，</span>方能與 $n\times 1$ 的 $\boldsymbol{X}$ 相乘；而在 [Theorem 3.18](#thm-matrix-operation) 中，$\mathbf{A}$ 本身即為 $k\times n$ 矩陣，可直接左乘 <span class="text-nowrap">$\boldsymbol{X}$，</span>無須額外轉置。

</div>

## 以共變異數矩陣求線性組合的變異數

<div id="ex-bivariate-normal-covariance" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.41</div>

<div lang="en" markdown="1">
Let $(X,Y)^{\mathrm{T}}$ follow a bivariate normal distribution

$$
\begin{bmatrix} X\\ Y \end{bmatrix}\sim\mathcal{N}_{2}\Biggl(\begin{bmatrix} 3\\ 5 \end{bmatrix},\ \begin{bmatrix} 4 & 2\\ 2 & 3 \end{bmatrix}\Biggr)
$$

Find the variance of <span class="text-nowrap">$3X+2Y$.</span>
</div>

**[ 法一 ]**

由 $X$ 與 $Y$ 的共變異數矩陣為

$$
\begin{bmatrix} 4 & 2\\ 2 & 3 \end{bmatrix}
$$

可知

<div class="topic-math-follow-before" markdown="1">

$$
\mathrm{Var}(X)=4,\ \ \mathrm{Var}(Y)=3,\ \ \operatorname{Cov}(X, Y)=2
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop topic-math-follow" markdown="1">

$$
\Longrightarrow\ \mathrm{Var}(3X+2Y)=3^{2}\cdot\mathrm{Var}(X) + 2^{2}\cdot\mathrm{Var}(Y) + 2\cdot 3\cdot 2\cdot\operatorname{Cov}(X, Y)=72
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile topic-math-follow" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ \mathrm{Var}(&3X+2Y)\\[0.45em]
&=3^{2}\cdot\mathrm{Var}(X) + 2^{2}\cdot\mathrm{Var}(Y)\\[0.2em]
&\qquad+ 2\cdot 3\cdot 2\cdot\operatorname{Cov}(X, Y)\\[0.45em]
&=72
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
\mathrm{Var}(3X+2Y)&=\mathrm{Var}\Biggl(\Bigl[\,3\ \ 2\,\Bigr]\begin{bmatrix} X\\ Y \end{bmatrix}\Biggr)\\[0.55em]
&=\Bigl[\,3\ \ 2\,\Bigr]\begin{bmatrix} 4 & 2\\ 2 & 3 \end{bmatrix}\begin{bmatrix} 3\\ 2 \end{bmatrix}=72
\end{aligned}
$$

</div>

</div>

共變異數雖能刻畫兩變數共同變化的「方向」，其數值卻受變數單位影響而無固定上下界，難以直接衡量共同變化的「強弱程度」。為消除尺度影響，[下一篇](/lecture-notes/correlation-coefficient/)將引入[**相關係數**](/lecture-notes/correlation-coefficient/#def-corr)。

## 本篇小結

[Definition 3.17](#def-covar-matrix) 把三個隨機變數兩兩之間的變異數與共變異數收在同一個矩陣裡，主對角線上的 $\sigma^{2}\_{\sssig X}, \sigma^{2}\_{\sssig Y}, \sigma^{2}\_{\sssig Z}$ 是各個變數自己的變異數，其餘位置則是變數之間的共變異數，因此知道一個共變異數矩陣，就等於知道所有變數之間的變異數與共變異數。由[共變異數的對稱性](/lecture-notes/covariance/#thm-covar-proper)可知 $\mathbf{\Sigma}$ 必為對稱矩陣，又由[變異數非負](/lecture-notes/variance/#thm-variance-properties)可知主對角線不應出現負數，這兩件事各排除了一類不合法的矩陣；至於主對角線為正、又對稱的矩陣為何仍可能不合法，要等到相關係數才能回答。同樣的定義並不限於三個變數，$n$ 個變數的版本只是把矩陣擴充為 $n \times n$ 而已。

[Definition 3.18](#def-var-of-r-vvec) 改以隨機向量書寫同一件事情，也就是 $\mathbf{\Sigma}$ $=$ $\mathrm{Var}(\boldsymbol{X})$ $=$ $\mathbb{E}\bigl[(\boldsymbol{X}-\boldsymbol{\mu})(\boldsymbol{X}-\boldsymbol{\mu})^{\mathrm{T}}\bigr]$ 這一條式子。兩個定義之所以一樣，是因為矩陣與向量的期望值都是「直接對每個元都取期望值」，把定義中兩個向量相乘所得的矩陣逐元取期望值，得到的正是 [Definition 3.17](#def-covar-matrix) 的那個矩陣。共變異數矩陣還必須是正半定的，要證明這件事，得先學會隨機向量的向量與矩陣運算。

[Theorem 3.17](#thm-vector-operation) 處理常數向量與隨機向量的乘積。期望值為 $\boldsymbol{a}^{\mathrm{T}}\boldsymbol{\mu}$ 這個向量版本的線性轉換，變異數則為 $\boldsymbol{a}^{\mathrm{T}}\,\mathbf{\Sigma}\,\boldsymbol{a}$ 這個二次形式，也就是向量版本的平方擴充性。證明的關鍵一步是把轉置拆開之後，$\boldsymbol{a}^{\mathrm{T}}$ 與 $\boldsymbol{a}$ 分別提到期望值的兩側，中間剩下的恰好就是 $\mathbf{\Sigma}$ 的定義。由於變異數必定非負，二次形式對任意 $\boldsymbol{a}$ 都不小於 <span class="text-nowrap">$0$，</span>共變異數矩陣因而是正半定矩陣。[Theorem 3.18](#thm-matrix-operation) 把常數向量換成 $k \times n$ 的常數矩陣，兩式的形狀幾乎相同，但 $\mathbf{A}\boldsymbol{X}$ 已經是維度比 $1$ 還高的隨機向量，其變異數為 <span class="text-nowrap">$\mathbf{A}\mathbf{\Sigma}\mathbf{A}^{\mathrm{T}}$。</span>兩者的差別只在於習慣上向量寫成行向量，故 $\boldsymbol{a}$ 需要轉置，而 $\mathbf{A}$ 本來就可以與 $\boldsymbol{X}$ 相乘。

[Example 3.41](#ex-bivariate-normal-covariance) 以一組二元常態示範上述結果的用法。由共變異數矩陣得到兩個變異數與一個共變異數之後，可以逐項展開求得 $\mathrm{Var}(3X+2Y)$ 這個值，也可以直接把係數排成一個列向量，以二次形式一步算出同樣的 $72$ 這個答案。

[下一篇](/lecture-notes/correlation-coefficient/)將介紹相關係數，它把共變異數除以兩個[標準差](/lecture-notes/variance-standard-deviation/#def-standard-deviation)，使共同變化的「程度」也有範圍上的限制。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
