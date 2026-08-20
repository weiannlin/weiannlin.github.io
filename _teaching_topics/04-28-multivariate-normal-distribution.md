---
title: "多元常態分配的定義與性質"
subtitle: "The Multivariate Normal Distribution: Definition and Properties"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 4
topic: 28
order: 428
permalink: /lecture-notes/multivariate-normal-distribution/
date: 2026-08-15
published: false
excerpt: "多元常態分配把常態分配推廣到 $n$ 維，以期望值向量 $\\boldsymbol{\\mu}$ 與共變異數矩陣 $\\mathbf{\\Sigma}$ 兩個參數界定，動差母函數為 $e^{\\boldsymbol{\\mu}^{\\mathrm{T}}\\boldsymbol{t}+\\frac{1}{2}\\boldsymbol{t}^{\\mathrm{T}}\\mathbf{\\Sigma}\\boldsymbol{t}}$ 這個式子。本篇先給出定義的六個欄位，再依序說明四項性質: 邊際分配均為常態分配，把向量分塊之後每一塊也仍是多元常態分配；條件分配的期望值與變異數可以由分塊後的 $\\mathbf{\\Sigma}$ 直接寫出，其形式與二元常態的結果完全對得起來；任意多個線性組合經仿射變換之後仍為多元常態分配，其等價敘述是任一個多元常態向量都可以由獨立的標準常態向量經 $\\boldsymbol{X}=\\mathbf{D}\\boldsymbol{Z}+\\boldsymbol{\\mu}$ 生成；二次形式 $(\\boldsymbol{X}-\\boldsymbol{\\mu})^{\\mathrm{T}}\\mathbf{\\Sigma}^{-1}(\\boldsymbol{X}-\\boldsymbol{\\mu})$ 服從自由度為 $n$ 的卡方分配，開根號之後即為馬氏距離。最後以三道例題演練仿射變換的用法。"
---

[上一篇](/lecture-notes/bivariate-normal-examples/)以三道例題演練[二元常態分配](/lecture-notes/bivariate-normal-distribution/#def-bivariate-normal)的性質，其中最後一題的註記曾經提到，該題另有一種以矩陣求解的作法，只是那需要先具備處理矩陣版本的能力。本篇處理的正是這個矩陣版本，也就是[常態分配](/lecture-notes/normal-distribution/#def-normal)在 $n$ 維空間中的推廣: 多元常態分配。

多元常態分配以期望值向量 $\boldsymbol{\mu}$ 與[共變異數矩陣](/lecture-notes/covariance-matrix/#def-covar-matrix) $\mathbf{\Sigma}$ 這兩個參數界定，機率函數之中的 $(\boldsymbol{x}-\boldsymbol{\mu})^{\mathrm{T}}\mathbf{\Sigma}^{-1}(\boldsymbol{x}-\boldsymbol{\mu})$ 這個式子，恰好就是單變數常態分配指數上 $\frac{(x-\mu)^{2}}{\sigma^{2}}$ 的矩陣版本。

本篇先給出定義，再依序說明四項性質: 邊際分配均為常態分配，而且把向量分塊之後每一塊也仍是多元常態分配；條件分配的期望值與變異數可以由分塊後的 $\mathbf{\Sigma}$ 直接寫出；任意多個線性組合經仿射變換之後仍為多元常態分配；二次形式服從[卡方分配](/lecture-notes/chi-squared-distribution/#def-chi-distribution)，其開根號之值即為馬氏距離。最後以三道例題演練這些性質在計算上的用法。

## 多元常態分配

<div id="def-multivariate-normal" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 4.26 (多元常態分配, multivariate normal distribution)</div>

**適用範圍**:

由多個常態分配隨機變數 $X_1,\ldots,X_n$ 所組成，又稱**多元高斯分配 <span lang="en">(multivariate Gaussian distribution)</span>**。

**值域範圍**:

$$
\mathcal{R}_{\sssig \boldsymbol{X}}=\lbrace\,\boldsymbol{x}\mid\boldsymbol{x}\in\mathbb{R}^{n}\,\rbrace
$$

**表示式**:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\boldsymbol{X}=\begin{bmatrix} X_1 & \cdots & X_n \end{bmatrix}^{\mathrm{T}}=\begin{bmatrix} X_1\\ \vdots\\ X_n \end{bmatrix}\sim\mathcal{MN}\bigl(\boldsymbol{\mu},\mathbf{\Sigma}\bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\boldsymbol{X}&=\begin{bmatrix} X_1 & \cdots & X_n \end{bmatrix}^{\mathrm{T}}\\[0.45em]
&=\begin{bmatrix} X_1\\ \vdots\\ X_n \end{bmatrix}\sim\mathcal{MN}\bigl(\boldsymbol{\mu},\mathbf{\Sigma}\bigr)
\end{aligned}
$$

</div>

**參數與參數範圍**:

$\boldsymbol{\mu}\in\mathbb{R}^{n}$ 為 $\boldsymbol{X}$ 的期望值、$\mathbf{\Sigma}$ 為 $\boldsymbol{X}$ 的共變異數矩陣，為對稱 <span lang="en">(symmetric)</span> 且半正定 <span lang="en">(positive semi-definite)</span> 之 $n\times n$ 方陣。

**機率函數**:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig \boldsymbol{X}}(\boldsymbol{x})=\frac{1}{\,\sqrt{(2\pi)^{n}\lvert\mathbf{\Sigma}\rvert}\,}\,e^{-\frac{1}{\,2\,}(\boldsymbol{x}-\boldsymbol{\mu})^{\mathrm{T}}\mathbf{\Sigma}^{-1}(\boldsymbol{x}-\boldsymbol{\mu})},\ \boldsymbol{x}\in\mathbb{R}^{n}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig \boldsymbol{X}}(\boldsymbol{x})&=\frac{1}{\,\sqrt{(2\pi)^{n}\lvert\mathbf{\Sigma}\rvert}\,}\\[0.45em]
&\qquad e^{-\frac{1}{\,2\,}(\boldsymbol{x}-\boldsymbol{\mu})^{\mathrm{T}}\mathbf{\Sigma}^{-1}(\boldsymbol{x}-\boldsymbol{\mu})},\\[0.45em]
&\qquad\qquad \boldsymbol{x}\in\mathbb{R}^{n}
\end{aligned}
$$

</div>

其中 $\lvert\mathbf{\Sigma}\rvert$ 代表 $\mathbf{\Sigma}$ 之行列式值。

**期望值、變異數、動差母函數**:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(\boldsymbol{X})=\boldsymbol{\mu},\quad \mathrm{Var}(\boldsymbol{X})=\mathbf{\Sigma},\quad M_{\sssig \boldsymbol{X}}(\boldsymbol{t})=e^{\boldsymbol{\mu}^{\mathrm{T}}\boldsymbol{t}+\frac{1}{\,2\,}\boldsymbol{t}^{\mathrm{T}}\mathbf{\Sigma}\boldsymbol{t}},\ \boldsymbol{t}\in\mathbb{R}^{n}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(\boldsymbol{X})&=\boldsymbol{\mu},\quad \mathrm{Var}(\boldsymbol{X})=\mathbf{\Sigma},\\[0.45em]
M_{\sssig \boldsymbol{X}}(\boldsymbol{t})&=e^{\boldsymbol{\mu}^{\mathrm{T}}\boldsymbol{t}+\frac{1}{\,2\,}\boldsymbol{t}^{\mathrm{T}}\mathbf{\Sigma}\boldsymbol{t}},\ \boldsymbol{t}\in\mathbb{R}^{n}
\end{aligned}
$$

</div>

</div>

多元常態分配 <span lang="en">(multivariate normal distribution)</span> 有一些地方需要注意:

(1) 多元常態分配的邊際分配均為常態分配:
{: .topic-paren-item}

$$
X_i\sim\mathcal{N}(\mu_{\sssig i},\sigma_{\sssig i}^{2}),\ i=1,\ldots,n
$$

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

如同我們過去所提到，二元常態分配的邊際分配均為常態分配，但任意兩個「不獨立」的常態分配，卻不見得能組成一個二元常態分配；多元常態分配的邊際分配雖均為常態分配，任意 $n$ 個「不獨立」的常態分配，卻不見得能組成一個多元常態分配。

但是，任意多個「獨立」的常態分配，必能組成一個共變異數矩陣為對角矩陣 <span lang="en">(diagonal matrix)</span> 的多元常態分配，[^diagonal] 且若此些常態分配的變異數同為 <span class="text-nowrap">$\sigma^{2}$，</span>則其共變異數矩陣為 <span class="text-nowrap">$\sigma^{2}\mathbb{I}_n$，</span>其中 $\mathbb{I}_n$ 為 $n\times n$ 的單位矩陣 <span lang="en">(identity matrix)</span>。

</div>

除此之外，多元常態分配的其中幾個變數亦會形成多元常態分配，此即: 令
{: .topic-paren-cont}

$$
\boldsymbol{X}=\begin{bmatrix} \boldsymbol{X}_1\\ \boldsymbol{X}_2 \end{bmatrix}
$$

其中
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\boldsymbol{X}_1=\bigl[\,X_1,\ldots,X_q\,\bigr]^{\mathrm{T}},\quad \boldsymbol{X}_2=\bigl[\,X_{q+1},\ldots,X_n\,\bigr]^{\mathrm{T}},\quad q<n
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\boldsymbol{X}_1&=\bigl[\,X_1,\ldots,X_q\,\bigr]^{\mathrm{T}},\\[0.45em]
\boldsymbol{X}_2&=\bigl[\,X_{q+1},\ldots,X_n\,\bigr]^{\mathrm{T}},\quad q<n
\end{aligned}
$$

</div>

則
{: .topic-paren-cont}

$$
\boldsymbol{X}=\begin{bmatrix} \boldsymbol{X}_1\\ \boldsymbol{X}_2 \end{bmatrix}\sim\mathcal{MN}\left(\begin{bmatrix} \boldsymbol{\mu}_1\\ \boldsymbol{\mu}_2 \end{bmatrix},\ \begin{bmatrix} \mathbf{\Sigma}_{11} & \mathbf{\Sigma}_{12}\\ \mathbf{\Sigma}_{21} & \mathbf{\Sigma}_{22} \end{bmatrix}\right)
$$

且其中我們有
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\boldsymbol{X}_1\sim\mathcal{MN}\bigl(\boldsymbol{\mu}_1,\mathbf{\Sigma}_{11}\bigr),\quad \boldsymbol{X}_2\sim\mathcal{MN}\bigl(\boldsymbol{\mu}_2,\mathbf{\Sigma}_{22}\bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\boldsymbol{X}_1&\sim\mathcal{MN}\bigl(\boldsymbol{\mu}_1,\mathbf{\Sigma}_{11}\bigr),\\[0.45em]
\boldsymbol{X}_2&\sim\mathcal{MN}\bigl(\boldsymbol{\mu}_2,\mathbf{\Sigma}_{22}\bigr)
\end{aligned}
$$

</div>

(2) 多元常態分配的條件分配均為多元 (或單元) 常態分配:
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\boldsymbol{X}_1\bigm|(\boldsymbol{X}_2=\boldsymbol{x}_2)&\sim\mathcal{MN}\Bigl(\boldsymbol{\mu}_1+\mathbf{\Sigma}_{12}\mathbf{\Sigma}_{22}^{-1}\bigl(\boldsymbol{x}_2-\boldsymbol{\mu}_2\bigr),\ \mathbf{\Sigma}_{11}-\mathbf{\Sigma}_{12}\mathbf{\Sigma}_{22}^{-1}\mathbf{\Sigma}_{21}\Bigr)\\[0.45em]
\boldsymbol{X}_2\bigm|(\boldsymbol{X}_1=\boldsymbol{x}_1)&\sim\mathcal{MN}\Bigl(\boldsymbol{\mu}_2+\mathbf{\Sigma}_{21}\mathbf{\Sigma}_{11}^{-1}\bigl(\boldsymbol{x}_1-\boldsymbol{\mu}_1\bigr),\ \mathbf{\Sigma}_{22}-\mathbf{\Sigma}_{21}\mathbf{\Sigma}_{11}^{-1}\mathbf{\Sigma}_{12}\Bigr)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\boldsymbol{X}_1\bigm|(\boldsymbol{X}_2=\boldsymbol{x}_2)&\sim\mathcal{MN}\Bigl(\boldsymbol{\mu}_1+\mathbf{\Sigma}_{12}\mathbf{\Sigma}_{22}^{-1}\bigl(\boldsymbol{x}_2-\boldsymbol{\mu}_2\bigr),\\[0.3em]
&\qquad\qquad \mathbf{\Sigma}_{11}-\mathbf{\Sigma}_{12}\mathbf{\Sigma}_{22}^{-1}\mathbf{\Sigma}_{21}\Bigr)
\end{aligned}
$$

$$
\begin{aligned}
\boldsymbol{X}_2\bigm|(\boldsymbol{X}_1=\boldsymbol{x}_1)&\sim\mathcal{MN}\Bigl(\boldsymbol{\mu}_2+\mathbf{\Sigma}_{21}\mathbf{\Sigma}_{11}^{-1}\bigl(\boldsymbol{x}_1-\boldsymbol{\mu}_1\bigr),\\[0.3em]
&\qquad\qquad \mathbf{\Sigma}_{22}-\mathbf{\Sigma}_{21}\mathbf{\Sigma}_{11}^{-1}\mathbf{\Sigma}_{12}\Bigr)
\end{aligned}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

我們可將二元常態分配之條件分配的性質改寫為以下:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
X\mid(Y=y)&\sim\mathcal{N}\left(\mu_1+\sigma_{12}\frac{1}{\,\sigma_2^{2}\,}(y-\mu_2),\ \sigma_1^{2}-\sigma_{12}\frac{1}{\,\sigma_2^{2}\,}\sigma_{21}\right)\\[0.45em]
Y\mid(X=x)&\sim\mathcal{N}\left(\mu_2+\sigma_{21}\frac{1}{\,\sigma_1^{2}\,}(x-\mu_1),\ \sigma_2^{2}-\sigma_{21}\frac{1}{\,\sigma_1^{2}\,}\sigma_{12}\right)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
X\mid(Y=y)&\sim\mathcal{N}\left(\mu_1+\sigma_{12}\frac{1}{\,\sigma_2^{2}\,}(y-\mu_2),\right.\\[0.3em]
&\qquad\qquad \left.\sigma_1^{2}-\sigma_{12}\frac{1}{\,\sigma_2^{2}\,}\sigma_{21}\right)
\end{aligned}
$$

$$
\begin{aligned}
Y\mid(X=x)&\sim\mathcal{N}\left(\mu_2+\sigma_{21}\frac{1}{\,\sigma_1^{2}\,}(x-\mu_1),\right.\\[0.3em]
&\qquad\qquad \left.\sigma_2^{2}-\sigma_{21}\frac{1}{\,\sigma_1^{2}\,}\sigma_{12}\right)
\end{aligned}
$$

</div>

則上列這個性質完全可以跟二元的情況作對照，二者間具有驚人的相似性。

</div>

<!-- ref-point: 「仿射變換」一詞首見於第四章第 26 篇 (二元常態分配的定義與性質，書稿
     mathstatch4.tex 第 5472 行的註記，該處沒有 label)。該篇發布後把下面第 (3) 點的
     「仿射變換」回填為指向該處的站內連結。 -->

(3) 多元常態分配隨機變數之間的任意「多個」線性組合仍為多元常態分配。這與稍早我們所談到的仿射變換 <span lang="en">(affine transformation)</span> 是同樣的性質，[^affine-scope] 我們表示如下:
{: .topic-paren-item}

$$
\boldsymbol{X}\sim\mathcal{MN}(\boldsymbol{\mu},\mathbf{\Sigma})\qquad\therefore\, \boldsymbol{Y}=\mathbf{B}\boldsymbol{X}+\boldsymbol{c}\sim\mathcal{MN}\bigl(\mathbf{B}\boldsymbol{\mu}+\boldsymbol{c},\ \mathbf{B}\mathbf{\Sigma}\mathbf{B}^{\mathrm{T}}\bigr)
$$

其中 $\mathbf{B}$ 為一個 $k\times n$ 的常數矩陣，而 $\boldsymbol{c}$ 為一個常數向量，[^matrix-operation] 此即
{: .topic-paren-cont}

$$
\boldsymbol{c}=\bigl[\,c_1,\ldots,c_k\,\bigr]^{\mathrm{T}}=\begin{bmatrix} c_1\\ \vdots\\ c_k \end{bmatrix}
$$

仿射變換也等價於底下的這個性質: 令
{: .topic-paren-cont}

$$
\boldsymbol{Z}=\bigl[\,Z_1,\ldots,Z_m\,\bigr]^{\mathrm{T}}=\begin{bmatrix} Z_1\\ \vdots\\ Z_m \end{bmatrix}
$$

表示由 $m$ 個獨立的標準常態分配所構成的多元常態分配隨機向量，則必存在一個 $n\times m$ 的常數矩陣 <span class="text-nowrap">$\mathbf{D}$，</span>使得
{: .topic-paren-cont}

$$
\boldsymbol{X}=\mathbf{D}\boldsymbol{Z}+\boldsymbol{\mu}\sim\mathcal{MN}(\boldsymbol{\mu},\mathbf{\Sigma})
$$

其中
{: .topic-paren-cont}

$$
\mathbf{\Sigma}=\mathbf{D}\mathbb{I}_m\mathbf{D}^{\mathrm{T}}=\mathbf{D}\mathbf{D}^{\mathrm{T}}
$$

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

讀者可能會覺得，上述兩個等價性質，好像與單變數常態分配的線性組合可加性與反標準化的性質有所呼應，事實上這麼理解是沒有問題的，差別只在於，在多元常態的情況下，我們不再僅限於多轉一或是一轉一的結果，多轉多在此也是可行的。

</div>

(4) 多元常態分配的[二次形式](/lecture-notes/covariance-matrix/#thm-vector-operation) <span lang="en">(quadratic form)</span> 為卡方分配:
{: .topic-paren-item}

若令 $\boldsymbol{X}\sim\mathcal{MN}(\boldsymbol{\mu},\mathbf{\Sigma})$ 表示 $n$ 維的多元常態分配，則我們有
{: .topic-paren-cont}

$$
(\boldsymbol{X}-\boldsymbol{\mu})^{\mathrm{T}}\mathbf{\Sigma}^{-1}(\boldsymbol{X}-\boldsymbol{\mu})\sim\chi^{2}(n)
$$

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

讀者應該記得我們曾經提過，二次形式事實上可以類比為「平方」，除此之外，向量的二次形式事實上是有類似於內積 <span lang="en">(inner product)</span> 的功用的，所以除了「平方」之外還有「和」的功能；而中間的 $\mathbf{\Sigma}^{-1}$ 可以類比為「變異數的倒數」，這麼一來，這個結果就相當於「平方和除以變異數」，因此有卡方分配的結果是很自然的，其自由度跟隨向量的維度。

此外，多維度空間中，一個點 $\boldsymbol{X}$ 與 $\boldsymbol{\mu}$ 的距離，可以用 $\bigl[(\boldsymbol{X}-\boldsymbol{\mu})^{\mathrm{T}}\mathbf{\Sigma}^{-1}(\boldsymbol{X}-\boldsymbol{\mu})\bigr]^{\frac{1}{2}}$ 來衡量，這被稱作**馬氏距離 <span lang="en">(Mahalanobis distance)</span>**，也就是二次形式開根號之值，搭配多元常態之二次形式為卡方分配的結果，我們可以用機率分配來描述一個點離期望值有多遠。[^statistical-distance]

</div>

## 多元常態分配的例題

<div id="ex-multivariate-normal-1" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.63</div>

<div lang="en" markdown="1">
Suppose that $X_1$, $X_2$ and $X_3$ are independent random variables, each having the standard normal distribution. Find the joint pdf of $Y_1=X_1+X_2$ and <span class="text-nowrap">$Y_2=X_2+X_3$.</span>
</div>

由於 <span class="text-nowrap">$X_1,X_2,X_3\overset{\mathrm{iid}}{\sim}\mathcal{N}(0,1)$，</span>故可知

$$
\boldsymbol{X}=\begin{bmatrix} X_1 & X_2 & X_3 \end{bmatrix}^{\mathrm{T}}\sim\mathcal{MN}\bigl(\boldsymbol{0},\ \mathbb{I}_3\bigr)
$$

由題意可知

$$
\boldsymbol{Y}=\begin{bmatrix} X_1+X_2\\ X_2+X_3 \end{bmatrix}
$$

可令

$$
\mathbf{A}=\begin{bmatrix} 1 & 1 & 0\\ 0 & 1 & 1 \end{bmatrix}
$$

則由多元常態分配仿射變換的性質可知

$$
\boldsymbol{Y}=\mathbf{A}\boldsymbol{X}\sim\mathcal{BN}\bigl(\mathbf{A}\boldsymbol{0},\ \mathbf{A}\mathbb{I}_3\mathbf{A}^{\mathrm{T}}\bigr)
$$

其中

$$
\mathbf{A}\boldsymbol{0}=\begin{bmatrix} 0 & 0 \end{bmatrix}^{\mathrm{T}},\quad \mathbf{A}\mathbb{I}_3\mathbf{A}^{\mathrm{T}}=\begin{bmatrix} 2 & 1\\ 1 & 2 \end{bmatrix}
$$

則可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mu_1=\mu_2=0,\quad \sigma_1^{2}=\sigma_2^{2}=2,\quad \rho=\frac{1}{\,\sqrt{2\times2}\,}=\frac{1}{\,2\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mu_1&=\mu_2=0,\quad \sigma_1^{2}=\sigma_2^{2}=2,\\[0.45em]
\rho&=\frac{1}{\,\sqrt{2\times2}\,}=\frac{1}{\,2\,}
\end{aligned}
$$

</div>

由此可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig Y_1Y_2}(y_1,y_2)=\frac{1}{\,2\sqrt{3}\pi\,}e^{-\frac{\,y_1^{2}-y_1y_2+y_2^{2}\,}{3}},\ -\infty<y_1,y_2<\infty
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig Y_1Y_2}(y_1,y_2)&=\frac{1}{\,2\sqrt{3}\pi\,}e^{-\frac{\,y_1^{2}-y_1y_2+y_2^{2}\,}{3}},\\[0.3em]
&\qquad\qquad -\infty<y_1,y_2<\infty
\end{aligned}
$$

</div>

</div>

<div id="ex-bivariate-normal-ex-1-continued" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.60 <span lang="en">(Continued)</span></div>

<div lang="en" markdown="1">
Suppose that the random vector $\begin{bmatrix} X\\ Y \end{bmatrix}$ has a multivariate normal distribution whose mean vector and covariance matrix are

$$
\boldsymbol{\mu}=\begin{bmatrix} 5\\ 10 \end{bmatrix},\quad \mathbf{\Sigma}=\begin{bmatrix} 1 & 5\rho\\ 5\rho & 25 \end{bmatrix}
$$

where $\rho>0$ and <span class="text-nowrap">$\mathbb{P}(6<Y<14\mid X=5)=0.6827$.</span> It is also given that $\mathbb{P}(Z<1)=0.8413$ for <span class="text-nowrap">$Z\sim\mathcal{N}(0,1)$.</span>

<ol class="topic-list-paren topic-list-paren--start-4">
  <li>Suppose further that $U=5X+Y$ and <span class="text-nowrap">$V=5X-Y$.</span> Determine whether $U$ and $V$ are independent.</li>
</ol>
</div>

(4) 由題意可令
{: .topic-paren-item}

$$
\mathbf{A}=\begin{bmatrix} 5 & 1\\ 5 & -1 \end{bmatrix}
$$

則依照多元常態分配之仿射變換性質可知
{: .topic-paren-cont}

$$
\begin{bmatrix} U\\ V \end{bmatrix}=\mathbf{A}\begin{bmatrix} X\\ Y \end{bmatrix}\sim\mathcal{BN}\bigl(\mathbf{A}\boldsymbol{\mu},\ \mathbf{A}\mathbf{\Sigma}\mathbf{A}^{\mathrm{T}}\bigr)
$$

其中
{: .topic-paren-cont}

$$
\mathbf{A}\boldsymbol{\mu}=\begin{bmatrix} 5 & 1\\ 5 & -1 \end{bmatrix}\begin{bmatrix} 5\\ 10 \end{bmatrix}=\begin{bmatrix} 35\\ 15 \end{bmatrix}
$$

又由[前面的小題](/lecture-notes/bivariate-normal-examples/#ex-bivariate-normal-ex-1)已求得 <span class="text-nowrap">$\rho=\frac{3}{\,5\,}$，</span>代入之後可知
{: .topic-paren-cont}

$$
\mathbf{\Sigma}=\begin{bmatrix} 1 & 3\\ 3 & 25 \end{bmatrix}
$$

由此可得
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbf{A}\mathbf{\Sigma}\mathbf{A}^{\mathrm{T}}=\begin{bmatrix} 5 & 1\\ 5 & -1 \end{bmatrix}\begin{bmatrix} 1 & 3\\ 3 & 25 \end{bmatrix}\begin{bmatrix} 5 & 1\\ 5 & -1 \end{bmatrix}^{\mathrm{T}}=\begin{bmatrix} 80 & 0\\ 0 & 20 \end{bmatrix}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbf{A}\mathbf{\Sigma}\mathbf{A}^{\mathrm{T}}&=\begin{bmatrix} 5 & 1\\ 5 & -1 \end{bmatrix}\begin{bmatrix} 1 & 3\\ 3 & 25 \end{bmatrix}\\[0.45em]
&\qquad\begin{bmatrix} 5 & 1\\ 5 & -1 \end{bmatrix}^{\mathrm{T}}\\[0.45em]
&=\begin{bmatrix} 80 & 0\\ 0 & 20 \end{bmatrix}
\end{aligned}
$$

</div>

由於 $\begin{bmatrix} U & V \end{bmatrix}^{\mathrm{T}}$ 為二元常態分配且 <span class="text-nowrap">$\mathrm{Cov}(U,V)=0$，</span>故可知
{: .topic-paren-cont}

$$
U\indep V
$$

</div>

<div id="ex-multivariate-normal-2" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.64</div>

<div lang="en" markdown="1">
Suppose that $Y_1$ and $Y_2$ are independent, each having the standard normal distribution. Find the distribution of each of the random variables below.

<ol class="topic-list-paren topic-list-paren--math">
  <li>
$$
\frac{\,(Y_1-Y_2)\,}{\sqrt{2}}
$$
  </li>
  <li>
$$
\frac{\,(Y_1+Y_2)^{2}\,}{(Y_1-Y_2)^{2}}
$$
  </li>
  <li>
$$
\frac{Y_1+Y_2}{\,\sqrt{(Y_1-Y_2)^{2}}\,}
$$
  </li>
</ol>
</div>

(1) 由 $Y_1,Y_2\overset{\mathrm{iid}}{\sim}\mathcal{N}(0,1)$ 可知
{: .topic-paren-item}

$$
\begin{bmatrix} Y_1\\ Y_2 \end{bmatrix}\sim\mathcal{BN}\left(\begin{bmatrix} 0\\ 0 \end{bmatrix},\ \begin{bmatrix} 1 & 0\\ 0 & 1 \end{bmatrix}\right)
$$

可令
{: .topic-paren-cont}

$$
\mathbf{A}=\begin{bmatrix} 1 & 1\\ 1 & -1 \end{bmatrix}
$$

且
{: .topic-paren-cont}

$$
\begin{bmatrix} Y_1+Y_2\\ Y_1-Y_2 \end{bmatrix}=\mathbf{A}\begin{bmatrix} Y_1\\ Y_2 \end{bmatrix}
$$

則我們有
{: .topic-paren-cont}

$$
\begin{bmatrix} Y_1+Y_2\\ Y_1-Y_2 \end{bmatrix}\sim\mathcal{BN}\left(\begin{bmatrix} 0\\ 0 \end{bmatrix},\ \begin{bmatrix} 2 & 0\\ 0 & 2 \end{bmatrix}\right)
$$

可知
{: .topic-paren-cont}

$$
(Y_1+Y_2)\sim\mathcal{N}(0,2)\ \indep\ (Y_1-Y_2)\sim\mathcal{N}(0,2)
$$

則
{: .topic-paren-cont}

$$
\frac{\,(Y_1-Y_2)\,}{\sqrt{2}}\sim\mathcal{N}(0,1)
$$

(2) 由
{: .topic-paren-item}

$$
(Y_1+Y_2)\sim\mathcal{N}(0,2)\ \indep\ (Y_1-Y_2)\sim\mathcal{N}(0,2)
$$

可知
{: .topic-paren-cont}

$$
\left(\frac{\,Y_1+Y_2\,}{\sqrt{2}}\right)^{2}\sim\chi^{2}(1)\ \indep\ \left(\frac{\,Y_1-Y_2\,}{\sqrt{2}}\right)^{2}\sim\chi^{2}(1)
$$

故
{: .topic-paren-cont}

$$
\frac{\,(Y_1+Y_2)^{2}\,}{(Y_1-Y_2)^{2}}=\frac{\,(Y_1+Y_2)^{2}/2\,}{(Y_1-Y_2)^{2}/2}\sim\mathcal{F}(1,1)
$$

(3) 由前兩小題的結果可得
{: .topic-paren-item}

$$
\frac{Y_1+Y_2}{\,\sqrt{(Y_1-Y_2)^{2}}\,}=\frac{\,\frac{\,Y_1+Y_2\,}{\sqrt{2}}\,}{\,\sqrt{\frac{\,\frac{\,(Y_1-Y_2)^{2}\,}{2}\,}{1}}\,}\sim t(1)
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

上述兩個問題，事實上都使用了**二元常態分配中，零相關等價於獨立**這個性質。這個性質事實上能夠推廣至多元常態分配，其中，我們甚至可以將其一個服從多元常態分配的向量分成幾個部分，這些部分間的共變異數 (矩陣) 若是 $0$ (或是零矩陣)，則他們也會獨立，見[下一篇的定理](/lecture-notes/multivariate-normal-independence/#thm-block-independence)。

</div>

[^diagonal]: 共變異數矩陣是一個對角矩陣時，說明這一些隨機變數彼此零相關，而在多元常態中，這更等價於彼此獨立。

[^affine-scope]: 事實上，仿射變換原先就不僅限於多維轉一維，多個線性組合共同構成的情況同樣稱為仿射變換。

[^matrix-operation]: 其實由 [Theorem 3.18](/lecture-notes/covariance-matrix/#thm-matrix-operation)，我們已經可以知道期望值向量與共變異數矩陣的數值了，只不過多元常態分配的仿射變換性質，保證了在期望值向量與共變異數矩陣已知的基礎上，確保這時候的線性組合結果仍為多元常態分配。

[^statistical-distance]: 事實上，這個概念也被叫做**統計距離**，也就是透過機率分配來描述「多遠」、「差多少」之類的概念，這也是統計檢定的核心精神。

## 本篇小結

[Definition 4.26](#def-multivariate-normal) 的多元常態分配以期望值向量 $\boldsymbol{\mu}$ 與共變異數矩陣 $\mathbf{\Sigma}$ 兩個參數界定，值域為整個 <span class="text-nowrap">$\mathbb{R}^{n}$，</span>機率函數為 $\frac{1}{\,\sqrt{(2\pi)^{n}\lvert\mathbf{\Sigma}\rvert}\,}e^{-\frac{1}{2}(\boldsymbol{x}-\boldsymbol{\mu})^{\mathrm{T}}\mathbf{\Sigma}^{-1}(\boldsymbol{x}-\boldsymbol{\mu})}$ 這個式子，動差母函數則為 <span class="text-nowrap">$e^{\boldsymbol{\mu}^{\mathrm{T}}\boldsymbol{t}+\frac{1}{2}\boldsymbol{t}^{\mathrm{T}}\mathbf{\Sigma}\boldsymbol{t}}$。</span>其中 $\mathbf{\Sigma}$ 必須是對稱且半正定的 $n\times n$ 方陣，這正是共變異數矩陣本來就具備的兩項性質。

四項性質之中，前兩項處理的是把向量拆開來看的結果。邊際分配均為常態分配，而且把 $\boldsymbol{X}$ 分成 $\boldsymbol{X}_1$ 與 $\boldsymbol{X}_2$ 兩塊之後，每一塊各自服從以對應的 $\boldsymbol{\mu}_i$ 與 $\mathbf{\Sigma}_{ii}$ 為參數的多元常態分配。條件分配同樣是多元 (或單元) 常態分配，期望值為 $\boldsymbol{\mu}_1+\mathbf{\Sigma}_{12}\mathbf{\Sigma}_{22}^{-1}(\boldsymbol{x}_2-\boldsymbol{\mu}_2)$ 這個式子、變異數為 <span class="text-nowrap">$\mathbf{\Sigma}_{11}-\mathbf{\Sigma}_{12}\mathbf{\Sigma}_{22}^{-1}\mathbf{\Sigma}_{21}$，</span>把矩陣換成純量之後，兩者恰好就是二元常態分配的條件期望值與條件變異數。要留意的是，邊際分配為常態分配這件事並不能反過來說: 任意 $n$ 個「不獨立」的常態分配未必能組成一個多元常態分配，但任意多個「獨立」的常態分配則必能組成一個共變異數矩陣為對角矩陣的多元常態分配。

後兩項性質處理的是整個向量的轉換。仿射變換保證 $\boldsymbol{Y}=\mathbf{B}\boldsymbol{X}+\boldsymbol{c}$ 仍為多元常態分配，期望值向量與共變異數矩陣分別是 $\mathbf{B}\boldsymbol{\mu}+\boldsymbol{c}$ 與 <span class="text-nowrap">$\mathbf{B}\mathbf{\Sigma}\mathbf{B}^{\mathrm{T}}$；</span>它的等價敘述是任一個多元常態向量都可以寫成 <span class="text-nowrap">$\boldsymbol{X}=\mathbf{D}\boldsymbol{Z}+\boldsymbol{\mu}$，</span>其中 $\boldsymbol{Z}$ 由獨立的標準常態分配構成而 <span class="text-nowrap">$\mathbf{\Sigma}=\mathbf{D}\mathbf{D}^{\mathrm{T}}$。</span>這兩件事正是單變數的線性組合可加性與反標準化的矩陣版本，差別只在於多轉多在此也是可行的。二次形式 $(\boldsymbol{X}-\boldsymbol{\mu})^{\mathrm{T}}\mathbf{\Sigma}^{-1}(\boldsymbol{X}-\boldsymbol{\mu})$ 則服從自由度為 $n$ 的卡方分配，把它理解為「平方和除以變異數」便不難接受這個結果，而它開根號之值即為馬氏距離。

三道例題都是仿射變換的演練。[Example 4.63](#ex-multivariate-normal-1) 把三個獨立標準常態變數排成 <span class="text-nowrap">$\boldsymbol{X}\sim\mathcal{MN}(\boldsymbol{0},\mathbb{I}_3)$，</span>再以 $\mathbf{A}=\begin{bmatrix} 1 & 1 & 0\\ 0 & 1 & 1 \end{bmatrix}$ 這個矩陣取出 $Y_1$ 與 <span class="text-nowrap">$Y_2$，</span>由 $\mathbf{A}\mathbb{I}_3\mathbf{A}^{\mathrm{T}}$ 讀得兩個變異數皆為 $2$ 而共變異數為 <span class="text-nowrap">$1$，</span>相關係數因而是 <span class="text-nowrap">$\frac{1}{\,2\,}$，</span>代回二元常態的機率函數即得所求。[Example 4.60 <span lang="en">(Continued)</span>](#ex-bivariate-normal-ex-1-continued) 則以 $\mathbf{A}=\begin{bmatrix} 5 & 1\\ 5 & -1 \end{bmatrix}$ 同時取得 $U$ 與 <span class="text-nowrap">$V$，</span>算出的 $\mathbf{A}\mathbf{\Sigma}\mathbf{A}^{\mathrm{T}}$ 是一個對角矩陣，兩者零相關；由於它們出自同一個二元常態分配，零相關便等價於獨立。[Example 4.64](#ex-multivariate-normal-2) 的三個小題共用同一個作法: 先由 $\mathbf{A}=\begin{bmatrix} 1 & 1\\ 1 & -1 \end{bmatrix}$ 得知 $Y_1+Y_2$ 與 $Y_1-Y_2$ 各自服從 $\mathcal{N}(0,2)$ 且彼此獨立。第一個統計量本身就是標準常態變數，第二個是兩個獨立卡方變數的比值，第三個則是標準常態變數除以獨立卡方變數開根號之後的比值，答案依序為 <span class="text-nowrap">$\mathcal{N}(0,1)$、</span>$\mathcal{F}(1,1)$ 與 <span class="text-nowrap">$t(1)$。</span>

最後兩道例題都用到二元常態分配中零相關等價於獨立這個性質。[下一篇](/lecture-notes/multivariate-normal-independence/)把這個性質推廣到多元常態分配的分塊之上，並以它證明常態母體之下樣本平均數與樣本變異數彼此獨立。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
