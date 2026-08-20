---
title: "多元常態分配的獨立性與二次形式"
subtitle: "Independence and Quadratic Forms in the Multivariate Normal Distribution"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 4
topic: 29
order: 429
permalink: /lecture-notes/multivariate-normal-independence/
date: 2026-08-15
published: false
excerpt: "多元常態分配之中，零相關與獨立是等價的，推廣到分塊之後即為 $\\mathbf{\\Sigma}_{12}=\\mathbf{0}$ 若且唯若 $\\boldsymbol{X}_1$ 與 $\\boldsymbol{X}_2$ 獨立。本篇先給出這條充要條件，再以它證明常態母體之下樣本平均數與樣本變異數彼此獨立: 作法是把 $\\overline{X}$ 與各個 $X_i-\\overline{X}$ 排成一個仿射變換，算出共變異數矩陣的非對角分塊為零矩陣。接著把這個算法一般化為 $\\mathbf{A}\\mathbf{B}^{\\mathrm{T}}=\\mathbf{0}$ 時 $\\mathbf{A}\\boldsymbol{X}$ 與 $\\mathbf{B}\\boldsymbol{X}$ 獨立，並由此給出冪等矩陣的二次形式服從卡方分配這條定理，自由度為該矩陣的跡，最直接的應用即 $(n-1)S^{2}/\\sigma^{2}$ 的抽樣分配。最後一題以雙重期望值定理處理階層模型的邊際分配。"
---

[上一篇](/lecture-notes/multivariate-normal-distribution/)給出[多元常態分配](/lecture-notes/multivariate-normal-distribution/#def-multivariate-normal)的定義，並依序列出邊際分配、條件分配、仿射變換與二次形式四項性質。本篇處理多元常態分配之中最常被引用的兩條結果: 一是分塊之間零相關與獨立的等價關係，二是冪等矩陣的二次形式所服從的分配。

這兩條結果所補齊的，正是先前談[卡方分配](/lecture-notes/chi-squared-distribution/#def-chi-distribution)與 $t$ 分配時直接引用而沒有證明的兩個前提: 常態母體之下樣本平均數 $\overline{X}$ 與樣本變異數 $S^{2}$ 彼此獨立，以及 $\frac{\,(n-1)S^{2}\,}{\sigma^{2}}$ 服從自由度為 $n-1$ 的卡方分配。前者由分塊獨立的充要條件得到，後者由二次形式的定理得到，兩者的關鍵都在同一個冪等矩陣 $\mathbb{I}_n-\frac{1}{\,n\,}\boldsymbol{1}\boldsymbol{1}^{\mathrm{T}}$ 身上。本篇最後另以一道階層模型的例題收尾，說明條件分配為多元常態時，邊際分配仍為多元常態，只是變異結構多疊了一層。

## 多元常態分配的分塊獨立

<div id="thm-block-independence" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 4.29 (分塊獨立的充要條件, block independence in the multivariate normal)</div>

令

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\boldsymbol{X}=\begin{bmatrix} \boldsymbol{X}_1\\ \boldsymbol{X}_2 \end{bmatrix}\sim\mathcal{MN}\left(\begin{bmatrix} \boldsymbol{\mu}_1\\ \boldsymbol{\mu}_2 \end{bmatrix},\ \begin{bmatrix} \mathbf{\Sigma}_{11} & \mathbf{\Sigma}_{12}\\ \mathbf{\Sigma}_{21} & \mathbf{\Sigma}_{22} \end{bmatrix}\right)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\boldsymbol{X}&=\begin{bmatrix} \boldsymbol{X}_1\\ \boldsymbol{X}_2 \end{bmatrix}\\[0.55em]
&\sim\mathcal{MN}\left(\begin{bmatrix} \boldsymbol{\mu}_1\\ \boldsymbol{\mu}_2 \end{bmatrix},\ \begin{bmatrix} \mathbf{\Sigma}_{11} & \mathbf{\Sigma}_{12}\\ \mathbf{\Sigma}_{21} & \mathbf{\Sigma}_{22} \end{bmatrix}\right)
\end{aligned}
$$

</div>

則 $\mathbf{\Sigma}_{12}=\mathbf{0}$ (即 $\boldsymbol{X}_1$ 與 $\boldsymbol{X}_2$ 零相關) 若且唯若 $\boldsymbol{X}_1$ 與 $\boldsymbol{X}_2$ 獨立，此即

$$
\mathbf{\Sigma}_{12}=\mathbf{0}\qquad\Longleftrightarrow\ \boldsymbol{X}_1\indep\boldsymbol{X}_2
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這一個定理有一個非常重要的應用，就是證明常態母體之下，隨機樣本的樣本平均數與樣本變異數將會獨立，見下列這一題。

</div>

<div id="ex-multivariate-normal-ind-1" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.65</div>

<div lang="en" markdown="1">
Let <span class="text-nowrap">$X_1, \ldots, X_n\overset{\mathrm{iid}}{\sim}\mathcal{N}(\mu, \sigma^{2})$,</span> prove that $\overline{X}=\frac{1}{\,n\,}\sum_{i=1}^{n}X_i\indep S^{2}=\frac{1}{\,n-1\,}\sum_{i=1}^{n}(X_i-\overline{X})^{2}$.
</div>

由 $X_1,\ldots,X_n\overset{\mathrm{iid}}{\sim}\mathcal{N}(\mu,\sigma^{2})$ 可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{bmatrix} X_1\\ \vdots\\ X_n \end{bmatrix}\sim\mathcal{MN}\left(\boldsymbol{\mu}=\begin{bmatrix} \mu\\ \vdots\\ \mu \end{bmatrix},\ \mathbf{\Sigma}=\begin{bmatrix} \sigma^{2} & 0 & \cdots & 0\\ 0 & \sigma^{2} & \cdots & 0\\ \vdots & \vdots & \ddots & \vdots\\ 0 & 0 & \cdots & \sigma^{2} \end{bmatrix}\right)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\begin{bmatrix} X_1\\ \vdots\\ X_n \end{bmatrix}&\sim\mathcal{MN}\left(\boldsymbol{\mu}=\begin{bmatrix} \mu\\ \vdots\\ \mu \end{bmatrix},\right.\\[0.55em]
&\qquad\left.\mathbf{\Sigma}=\begin{bmatrix} \sigma^{2} & 0 & \cdots & 0\\ 0 & \sigma^{2} & \cdots & 0\\ \vdots & \vdots & \ddots & \vdots\\ 0 & 0 & \cdots & \sigma^{2} \end{bmatrix}\right)
\end{aligned}
$$

</div>

由於 $\overline{X}=\frac{1}{\,n\,}\sum_{i=1}^{n}X_i$ 且 $S^{2}=\frac{1}{\,n-1\,}\sum_{i=1}^{n}(X_i-\overline{X})^{2}$ 這兩條式子，故我們可令

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{bmatrix} \frac{1}{\,n\,} & \frac{1}{\,n\,} & \cdots & \frac{1}{\,n\,}\\ 1-\frac{1}{\,n\,} & -\frac{1}{\,n\,} & \cdots & -\frac{1}{\,n\,}\\ -\frac{1}{\,n\,} & 1-\frac{1}{\,n\,} & \cdots & -\frac{1}{\,n\,}\\ \vdots & \vdots & \ddots & \vdots\\ -\frac{1}{\,n\,} & -\frac{1}{\,n\,} & \cdots & 1-\frac{1}{\,n\,} \end{bmatrix}=\begin{bmatrix} \frac{1}{\,n\,}\boldsymbol{1}^{\mathrm{T}}\\ \mathbb{I}_n-\frac{1}{\,n\,}\boldsymbol{1}\boldsymbol{1}^{\mathrm{T}} \end{bmatrix}=\begin{bmatrix} \frac{1}{\,n\,}\boldsymbol{1}^{\mathrm{T}}\\ \mathbb{I}_n-\mathbf{H} \end{bmatrix}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\begin{bmatrix} \frac{1}{\,n\,} & \frac{1}{\,n\,} & \cdots & \frac{1}{\,n\,}\\ 1-\frac{1}{\,n\,} & -\frac{1}{\,n\,} & \cdots & -\frac{1}{\,n\,}\\ -\frac{1}{\,n\,} & 1-\frac{1}{\,n\,} & \cdots & -\frac{1}{\,n\,}\\ \vdots & \vdots & \ddots & \vdots\\ -\frac{1}{\,n\,} & -\frac{1}{\,n\,} & \cdots & 1-\frac{1}{\,n\,} \end{bmatrix}\\[0.55em]
&=\begin{bmatrix} \frac{1}{\,n\,}\boldsymbol{1}^{\mathrm{T}}\\ \mathbb{I}_n-\frac{1}{\,n\,}\boldsymbol{1}\boldsymbol{1}^{\mathrm{T}} \end{bmatrix}=\begin{bmatrix} \frac{1}{\,n\,}\boldsymbol{1}^{\mathrm{T}}\\ \mathbb{I}_n-\mathbf{H} \end{bmatrix}
\end{aligned}
$$

</div>

則可知

$$
\begin{bmatrix} \overline{X}\\ X_1-\overline{X}\\ X_2-\overline{X}\\ \vdots\\ X_n-\overline{X} \end{bmatrix}=\begin{bmatrix} \frac{1}{\,n\,}\boldsymbol{1}^{\mathrm{T}}\\ \mathbb{I}_n-\mathbf{H} \end{bmatrix}\boldsymbol{X}
$$

服從多元常態分配，且期望值為

$$
\begin{bmatrix} \frac{1}{\,n\,}\boldsymbol{1}^{\mathrm{T}}\\ \mathbb{I}_n-\mathbf{H} \end{bmatrix}\boldsymbol{\mu}=\begin{bmatrix} \mu\\ 0\\ \vdots\\ 0 \end{bmatrix}_{(n+1)\times 1}
$$

[共變異數矩陣](/lecture-notes/covariance-matrix/#def-covar-matrix)為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{bmatrix} \frac{1}{\,n\,}\boldsymbol{1}^{\mathrm{T}}\\ \mathbb{I}_n-\mathbf{H} \end{bmatrix}\mathbf{\Sigma}\begin{bmatrix} \frac{1}{\,n\,}\boldsymbol{1}^{\mathrm{T}}\\ \mathbb{I}_n-\mathbf{H} \end{bmatrix}^{\mathrm{T}}=\begin{bmatrix} \frac{1}{\,n\,}\boldsymbol{1}^{\mathrm{T}}\mathbf{\Sigma}(\frac{1}{\,n\,}\boldsymbol{1}^{\mathrm{T}})^{\mathrm{T}} & \frac{1}{\,n\,}\boldsymbol{1}^{\mathrm{T}}\mathbf{\Sigma}(\mathbb{I}_n-\mathbf{H})^{\mathrm{T}}\\ (\mathbb{I}_n-\mathbf{H})\mathbf{\Sigma}(\frac{1}{\,n\,}\boldsymbol{1}^{\mathrm{T}})^{\mathrm{T}} & (\mathbb{I}_n-\mathbf{H})\mathbf{\Sigma}(\mathbb{I}_n-\mathbf{H})^{\mathrm{T}} \end{bmatrix}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\begin{bmatrix} \frac{1}{\,n\,}\boldsymbol{1}^{\mathrm{T}}\\ \mathbb{I}_n-\mathbf{H} \end{bmatrix}\mathbf{\Sigma}\begin{bmatrix} \frac{1}{\,n\,}\boldsymbol{1}^{\mathrm{T}}\\ \mathbb{I}_n-\mathbf{H} \end{bmatrix}^{\mathrm{T}}\\[0.55em]
&=\begin{bmatrix} \frac{1}{\,n\,}\boldsymbol{1}^{\mathrm{T}}\mathbf{\Sigma}(\frac{1}{\,n\,}\boldsymbol{1}^{\mathrm{T}})^{\mathrm{T}} & \frac{1}{\,n\,}\boldsymbol{1}^{\mathrm{T}}\mathbf{\Sigma}(\mathbb{I}_n-\mathbf{H})^{\mathrm{T}}\\ (\mathbb{I}_n-\mathbf{H})\mathbf{\Sigma}(\frac{1}{\,n\,}\boldsymbol{1}^{\mathrm{T}})^{\mathrm{T}} & (\mathbb{I}_n-\mathbf{H})\mathbf{\Sigma}(\mathbb{I}_n-\mathbf{H})^{\mathrm{T}} \end{bmatrix}
\end{aligned}
$$

</div>

其中 $\mathbb{I}_{n}-\mathbf{H}=\mathbb{I}_{n}-\frac{1}{\,n\,}\boldsymbol{1}\boldsymbol{1}^{\mathrm{T}}$ 為一冪等矩陣 <span lang="en">(idempotent matrix)</span>，[^idempotent] 故可知共變異數矩陣為

$$
\begin{bmatrix} \frac{\,\sigma^{2}\,}{n} & \boldsymbol{0}^{\mathrm{T}}\\ \boldsymbol{0} & \sigma^{2}(\mathbb{I}_n-\mathbf{H}) \end{bmatrix}
$$

此即說明

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\overline{X}\indep\lbrace(X_1-\overline{X}),\ (X_2-\overline{X}),\ \ldots,\ (X_n-\overline{X})\rbrace
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\overline{X}\indep\lbrace&(X_1-\overline{X}),\ (X_2-\overline{X}),\\[0.45em]
&\qquad \ldots,\ (X_n-\overline{X})\rbrace
\end{aligned}
$$

</div>

故當然

$$
\overline{X}\indep S^{2}=\frac{1}{\,n-1\,}\sum_{i=1}^{n}(X_i-\overline{X})^{2}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

事實上，在上述的證明中，關於 $\overline{X}$ 與 $\begin{bmatrix} X_1-\overline{X} & \cdots & X_n-\overline{X} \end{bmatrix}^{\mathrm{T}}$ 的共變異數矩陣 (或稱共變異數向量)，是 $\mathrm{Cov}\bigl(\overline{X},\ \begin{bmatrix} X_1-\overline{X} & \cdots & X_n-\overline{X} \end{bmatrix}^{\mathrm{T}}\bigr)$ 這個量，但也可以寫為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Cov}\left(\frac{1}{\,n\,}\boldsymbol{1}^{\mathrm{T}}\boldsymbol{X},\ (\mathbb{I}_{n}-\mathbf{H})\boldsymbol{X}\right)=\frac{1}{\,n\,}\boldsymbol{1}^{\mathrm{T}}\mathbf{\Sigma}(\mathbb{I}_{n}-\mathbf{H})^{\mathrm{T}}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathrm{Cov}\left(\frac{1}{\,n\,}\boldsymbol{1}^{\mathrm{T}}\boldsymbol{X},\ (\mathbb{I}_{n}-\mathbf{H})\boldsymbol{X}\right)\\[0.55em]
&=\frac{1}{\,n\,}\boldsymbol{1}^{\mathrm{T}}\mathbf{\Sigma}(\mathbb{I}_{n}-\mathbf{H})^{\mathrm{T}}
\end{aligned}
$$

</div>

而剛好由於 $\frac{1}{\,n\,}\boldsymbol{1}^{\mathrm{T}}(\mathbb{I}_{n}-\mathbf{H})^{\mathrm{T}}=\boldsymbol{0}^{\mathrm{T}}$ 的緣故，我們可知二者零相關，在多元常態分配中亦等價於二者獨立。

事實上，這可以推廣成一般化的形式，也就是在多元常態分配中，若二矩陣 $\mathbf{A}$ 與 $\mathbf{B}$ 皆可與 $\boldsymbol{X}$ 相乘，且 <span class="text-nowrap">$\mathbf{A}\mathbf{B}^{\mathrm{T}}=\mathbf{0}$，</span>則我們可知

$$
\mathbf{A}\boldsymbol{X}\indep\mathbf{B}\boldsymbol{X}
$$

這其中，我們有

$$
\mathrm{Cov}(\mathbf{A}\boldsymbol{X},\ \mathbf{B}\boldsymbol{X})=\mathbf{A}\mathbf{\Sigma}\mathbf{B}^{\mathrm{T}}
$$

</div>

<!-- ref-point: 下面 Example 4.66 第 (2) 小題所說的「由定理可知」，指的是聯合動差母函數可分解為
     兩個邊際動差母函數之乘積等價於獨立這件事。該敘述目前只出現在第三章第 17 篇
     (交叉動差與聯合動差母函數) 的一則 Note 之中 (_teaching_topics/cross-moments-joint-mgf.md
     第 199 行)，該處沒有 id 可以連。待該篇補上 anchor 之後，把「由定理可知」接上站內連結。
     另，第 (3) 小題的「二元常態分配」待第四章第 26 篇 (書稿 mathstatch4.tex 第 5137 行的
     Definition 4.25，anchor 為 #def-bivariate-normal) 發布後接上連結。 -->

<div id="ex-multivariate-normal-ind-2" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.66</div>

<div lang="en" markdown="1">
Suppose that $X_1,\ldots,X_n$ form a random sample from a normal distribution <span class="text-nowrap">$\mathcal{N}(\mu,\sigma^{2})$.</span>

<ol class="topic-list-paren">
  <li>Suppose that <span class="text-nowrap">$Y=\sum_{i=1}^{n}a_iX_i$,</span> in which every $a_i$ is a real constant. Determine the mgf of <span class="text-nowrap">$Y$,</span> that is, <span class="text-nowrap">$M_{\sssig Y}(t)=\mathbb{E}(e^{tY})$.</span></li>
  <li>Suppose further that <span class="text-nowrap">$Z=\sum_{i=1}^{n}b_iX_i$,</span> in which every $b_i$ is a real constant. Find a condition on the two sets of constants that is at once necessary and sufficient for $Y$ and $Z$ to be independent. (Hint: locate the condition under which $M_{\sssig YZ}(t,s)=\mathbb{E}(e^{tY+sZ})$ factors into <span class="text-nowrap">$M_{\sssig Y}(t)M_{\sssig Z}(s)$,</span> where <span class="text-nowrap">$M_{\sssig Z}(s)=\mathbb{E}(e^{sZ})$.)</span></li>
  <li>Evaluate the covariance of $Y$ and <span class="text-nowrap">$Z$,</span> and state what the two preceding parts together allow you to conclude.</li>
</ol>
</div>

(1) 依題目設定，$X_1,\ldots,X_n\overset{\mathrm{iid}}{\sim}\mathcal{N}(\mu,\sigma^{2})$，且 <span class="text-nowrap">$Y=\sum_{i=1}^{n}a_iX_i$，</span>則
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{\sssig Y}(t)&=\mathbb{E}\bigl(e^{tY}\bigr)=\mathbb{E}\Bigl(e^{t\sum_{i=1}^{n}a_iX_i}\Bigr)=\prod_{i=1}^{n}M_{\sssig X_i}(a_it)\\[0.45em]
&=e^{\sum_{i=1}^{n}a_i\mu t+\frac{1}{2}\sum_{i=1}^{n}a_i^{2}\sigma^{2}t^{2}}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig Y}(t)&=\mathbb{E}\bigl(e^{tY}\bigr)=\mathbb{E}\Bigl(e^{t\sum_{i=1}^{n}a_iX_i}\Bigr)\\[0.45em]
&=\prod_{i=1}^{n}M_{\sssig X_i}(a_it)\\[0.45em]
&=e^{\sum_{i=1}^{n}a_i\mu t+\frac{1}{2}\sum_{i=1}^{n}a_i^{2}\sigma^{2}t^{2}}
\end{aligned}
$$

</div>

(2) 依題目設定，<span class="text-nowrap">$Z=\sum_{i=1}^{n}b_iX_i$，</span>則
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{\sssig YZ}(t,s)&=\mathbb{E}\bigl(e^{tY+sZ}\bigr)=\mathbb{E}\Bigl(e^{t\sum_{i=1}^{n}a_iX_i+s\sum_{i=1}^{n}b_iX_i}\Bigr)=\mathbb{E}\Bigl(e^{\sum_{i=1}^{n}(a_it+b_is)X_i}\Bigr)\\[0.45em]
&=\prod_{i=1}^{n}M_{\sssig X_i}(a_it+b_is)=e^{\mu\sum_{i=1}^{n}(a_it+b_is)+\frac{1}{2}\sigma^{2}\sum_{i=1}^{n}(a_it+b_is)^{2}}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig YZ}(t,s)&=\mathbb{E}\bigl(e^{tY+sZ}\bigr)\\[0.45em]
&=\mathbb{E}\Bigl(e^{t\sum_{i=1}^{n}a_iX_i+s\sum_{i=1}^{n}b_iX_i}\Bigr)\\[0.45em]
&=\mathbb{E}\Bigl(e^{\sum_{i=1}^{n}(a_it+b_is)X_i}\Bigr)\\[0.45em]
&=\prod_{i=1}^{n}M_{\sssig X_i}(a_it+b_is)\\[0.45em]
&=e^{\mu\sum_{i=1}^{n}(a_it+b_is)+\frac{1}{2}\sigma^{2}\sum_{i=1}^{n}(a_it+b_is)^{2}}
\end{aligned}
$$

</div>

又由 (1) 同理可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
M_{\sssig Z}(s)=\mathbb{E}\bigl(e^{sZ}\bigr)=e^{\sum_{i=1}^{n}b_i\mu s+\frac{1}{2}\sum_{i=1}^{n}b_i^{2}\sigma^{2}s^{2}}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig Z}(s)&=\mathbb{E}\bigl(e^{sZ}\bigr)\\[0.45em]
&=e^{\sum_{i=1}^{n}b_i\mu s+\frac{1}{2}\sum_{i=1}^{n}b_i^{2}\sigma^{2}s^{2}}
\end{aligned}
$$

</div>

則由定理可知 $Y\indep Z$ 之充要條件為 <span class="text-nowrap">$M_{\sssig YZ}(t,s)=M_{\sssig Y}(t)M_{\sssig Z}(s)$，</span>此即
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{\sssig YZ}(t,s)&=\prod_{i=1}^{n}M_{\sssig X_i}(a_it+b_is)=e^{\mu\sum_{i=1}^{n}(a_it+b_is)+\frac{1}{2}\sigma^{2}\sum_{i=1}^{n}(a_it+b_is)^{2}}\\[0.45em]
&=e^{\sum_{i=1}^{n}a_i\mu t+\frac{1}{2}\sum_{i=1}^{n}a_i^{2}\sigma^{2}t^{2}}\times e^{\sum_{i=1}^{n}b_i\mu s+\frac{1}{2}\sum_{i=1}^{n}b_i^{2}\sigma^{2}s^{2}}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig YZ}(t,s)&=\prod_{i=1}^{n}M_{\sssig X_i}(a_it+b_is)\\[0.45em]
&=e^{\mu\sum_{i=1}^{n}(a_it+b_is)+\frac{1}{2}\sigma^{2}\sum_{i=1}^{n}(a_it+b_is)^{2}}\\[0.45em]
&=e^{\sum_{i=1}^{n}a_i\mu t+\frac{1}{2}\sum_{i=1}^{n}a_i^{2}\sigma^{2}t^{2}}\\[0.45em]
&\qquad\times e^{\sum_{i=1}^{n}b_i\mu s+\frac{1}{2}\sum_{i=1}^{n}b_i^{2}\sigma^{2}s^{2}}
\end{aligned}
$$

</div>

又上式成立之充要條件為 <span class="text-nowrap">$\sum_{i=1}^{n}a_ib_i=0$，</span>故可知使得 $Y\indep Z$ 之充要條件為
{: .topic-paren-cont}

$$
\sum_{i=1}^{n}a_ib_i=0
$$

(3) 由[共變異數](/lecture-notes/covariance/#def-covariance)的定義可得
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Cov}(Y,Z)=\mathrm{Cov}\left(\sum_{i=1}^{n}a_iX_i,\ \sum_{i=1}^{n}b_iX_i\right)=\sum_{i=1}^{n}a_ib_i\mathrm{Var}(X_i)=\sigma^{2}\sum_{i=1}^{n}a_ib_i
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Cov}(Y,Z)&=\mathrm{Cov}\left(\sum_{i=1}^{n}a_iX_i,\ \sum_{i=1}^{n}b_iX_i\right)\\[0.45em]
&=\sum_{i=1}^{n}a_ib_i\mathrm{Var}(X_i)\\[0.45em]
&=\sigma^{2}\sum_{i=1}^{n}a_ib_i
\end{aligned}
$$

</div>

由於 $X_1,\ldots,X_n$ 可構成一組多元常態分配，且 $Y$ 與 $Z$ 皆為 $X_i$ 之仿射變換 <span lang="en">(affine transformation)</span>，故可知 $Y$ 與 $Z$ 共同形成一二元常態分配，搭配 (2) 與本題前半之結果可知，在二元常態分配中，零相關與獨立為充要條件。
{: .topic-paren-cont}

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

在這個問題中，可以令 $\mathbf{A}=\bigl[\,a_1\ \cdots\ a_n\,\bigr]$ 與 <span class="text-nowrap">$\mathbf{B}=\bigl[\,b_1\ \cdots\ b_n\,\bigr]$，</span>則關於 $Y=\mathbf{A}\boldsymbol{X}$ 與 $Z=\mathbf{B}\boldsymbol{X}$ 之共變異數，可以由前一題所提到的算法計算，此即

$$
\mathbf{A}\sigma^{2}\mathbb{I}_n\mathbf{B}^{\mathrm{T}}=\sigma^{2}\sum_{i=1}^{n}a_ib_i
$$

則二者零相關 (或獨立) 的等價條件為

$$
\mathbf{A}\mathbf{B}^{\mathrm{T}}=\sum_{i=1}^{n}a_ib_i=0
$$

關於上述這個算法，在多元常態分配中有一個重要的衍生性質，見下列定理。

</div>

## 冪等矩陣的二次形式

<div id="thm-idempotent-quadratic-form" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 4.30 (冪等矩陣的二次形式, quadratic forms with an idempotent matrix)</div>

令 <span class="text-nowrap">$\boldsymbol{X}\sim\mathcal{MN}\bigl(\boldsymbol{\mu},\ \sigma^{2}\mathbb{I}_{n}\bigr)$，</span>且 $\mathbf{A}$ 為一冪等矩陣，且 <span class="text-nowrap">$\mathrm{tr}(\mathbf{A})=k$，</span>並滿足 <span class="text-nowrap">$\boldsymbol{\mu}^{\mathrm{T}}\mathbf{A}\boldsymbol{\mu}=0$，</span>則我們有

$$
\boldsymbol{X}^{\mathrm{T}}\mathbf{A}\boldsymbol{X}/\sigma^{2}\sim\chi^{2}(k)
$$

</div>

**實務上的應用**: (說明常態母體下，$S^{2}$ 之抽樣分配)[^application]

<div class="topic-proof" markdown="1">
**Proof.**

令

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
X_1,\ldots,X_n\overset{\mathrm{iid}}{\sim}\mathcal{N}(\mu,\sigma^{2}),\ \overline{X}=\frac{1}{\,n\,}\sum_{i=1}^{n}X_i,\ S^{2}=\frac{1}{\,n-1\,}\sum_{i=1}^{n}(X_i-\overline{X})^{2}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
X_1,\ldots,X_n&\overset{\mathrm{iid}}{\sim}\mathcal{N}(\mu,\sigma^{2}),\\[0.45em]
\overline{X}&=\frac{1}{\,n\,}\sum_{i=1}^{n}X_i,\\[0.45em]
S^{2}&=\frac{1}{\,n-1\,}\sum_{i=1}^{n}(X_i-\overline{X})^{2}
\end{aligned}
$$

</div>

則我們可以透過矩陣變換得知

$$
\frac{\,(n-1)S^{2}\,}{\sigma^{2}}=\boldsymbol{X}^{\mathrm{T}}\left(\mathbb{I}_n-\frac{1}{\,n\,}\boldsymbol{1}\boldsymbol{1}^{\mathrm{T}}\right)\boldsymbol{X}/\sigma^{2}
$$

又 $\mathbb{I}_n-\frac{1}{\,n\,}\boldsymbol{1}\boldsymbol{1}^{\mathrm{T}}$ 具有以下性質

<ol class="topic-list-paren topic-list-paren--math">
  <li>
$$
\mathrm{tr}\left(\mathbb{I}_n-\frac{1}{\,n\,}\boldsymbol{1}\boldsymbol{1}^{\mathrm{T}}\right)=n-1
$$
  </li>
  <li>
$$
\boldsymbol{\mu}^{\mathrm{T}}\left(\mathbb{I}_n-\frac{1}{\,n\,}\boldsymbol{1}\boldsymbol{1}^{\mathrm{T}}\right)\boldsymbol{\mu}=0
$$
  </li>
</ol>

故可由上述定理說明

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\frac{\,(n-1)S^{2}\,}{\sigma^{2}}=\boldsymbol{X}^{\mathrm{T}}\left(\mathbb{I}_n-\frac{1}{\,n\,}\boldsymbol{1}\boldsymbol{1}^{\mathrm{T}}\right)\boldsymbol{X}/\sigma^{2}\sim\chi^{2}(n-1)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\frac{\,(n-1)S^{2}\,}{\sigma^{2}}&=\boldsymbol{X}^{\mathrm{T}}\left(\mathbb{I}_n-\frac{1}{\,n\,}\boldsymbol{1}\boldsymbol{1}^{\mathrm{T}}\right)\boldsymbol{X}/\sigma^{2}\\[0.45em]
&\sim\chi^{2}(n-1)
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div id="ex-multivariate-normal-ind-3" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.67</div>

<div lang="en" markdown="1">
Suppose that $X_1, X_2, X_3, X_4$ are independent and identically distributed standard normal random variables, and set

$$
Q=X_1^{2}+\frac{\,(X_2-X_3)^{2}\,}{2}+X_4^{2},\quad \boldsymbol{X}^{\mathrm{T}}=\bigl[\,X_1, X_2, X_3, X_4\,\bigr]
$$

<ol class="topic-list-paren">
  <li>Find the matrix $\mathbf{A}$ for which $Q$ is the quadratic form <span class="text-nowrap">$\boldsymbol{X}^{\mathrm{T}}\mathbf{A}\boldsymbol{X}$.</span></li>
  <li>Show that $Q$ follows a chi-squared distribution, and determine its degrees of freedom.</li>
</ol>
</div>

(1) 由 $Q$ 的定義可得
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
Q=X_1^{2}+\frac{\,(X_2-X_3)^{2}\,}{2}+X_4^{2}=X_1^{2}+\frac{1}{\,2\,}X_2^{2}+\frac{1}{\,2\,}X_3^{2}+X_4^{2}-X_2X_3
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
Q&=X_1^{2}+\frac{\,(X_2-X_3)^{2}\,}{2}+X_4^{2}\\[0.45em]
&=X_1^{2}+\frac{1}{\,2\,}X_2^{2}+\frac{1}{\,2\,}X_3^{2}+X_4^{2}-X_2X_3
\end{aligned}
$$

</div>

則我們可將 $Q$ 改寫為
{: .topic-paren-cont}

$$
Q=\begin{bmatrix} X_1 & X_2 & X_3 & X_4 \end{bmatrix}\mathbf{A}\begin{bmatrix} X_1\\ X_2\\ X_3\\ X_4 \end{bmatrix}
$$

其中
{: .topic-paren-cont}

$$
\mathbf{A}=\begin{bmatrix} 1 & 0 & 0 & 0\\ 0 & \frac{1}{\,2\,} & -\frac{1}{\,2\,} & 0\\ 0 & -\frac{1}{\,2\,} & \frac{1}{\,2\,} & 0\\ 0 & 0 & 0 & 1 \end{bmatrix}
$$

(2) 由 (1) 可知
{: .topic-paren-item}

$$
\mathbf{A}=\begin{bmatrix} 1 & 0 & 0 & 0\\ 0 & \frac{1}{\,2\,} & -\frac{1}{\,2\,} & 0\\ 0 & -\frac{1}{\,2\,} & \frac{1}{\,2\,} & 0\\ 0 & 0 & 0 & 1 \end{bmatrix}
$$

且 $\mathbf{A}$ 為一冪等矩陣，且具以下性質: $\mathrm{tr}\left(\mathbf{A}\right)=3$ 且 <span class="text-nowrap">$\boldsymbol{\mu}^{\mathrm{T}}\mathbf{A}\boldsymbol{\mu}=0$，</span>又 <span class="text-nowrap">$\bigl[\,X_1, X_2, X_3, X_4\,\bigr]^{\mathrm{T}}\sim\mathcal{MN}\bigl(\boldsymbol{0},\ \mathbb{I}_4\bigr)$，</span>故可知
{: .topic-paren-cont}

$$
Q\sim\chi^{2}(3)
$$

</div>

## 階層模型下的邊際分配

<div id="ex-multivariate-normal-ind-4" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.68</div>

<div lang="en" markdown="1">
Suppose that $\boldsymbol{X}$ and $\boldsymbol{Y}$ are $k$-dimensional random vectors for which the conditional distribution of $\boldsymbol{X}$ given $\boldsymbol{Y}$ is <span class="text-nowrap">$\mathcal{N}_{\sssig k}(\boldsymbol{Y},\mathbf{\Sigma})$,</span> while $\boldsymbol{Y}$ itself has the distribution <span class="text-nowrap">$\mathcal{N}_{\sssig k}(\boldsymbol{\mu},\mathbf{\Lambda})$,</span> where $\boldsymbol{\mu}$ is a constant $k$-dimensional vector and $\mathbf{\Sigma}$ and $\mathbf{\Lambda}$ are both $k\times k$ covariance matrices. Determine the marginal distribution of <span class="text-nowrap">$\boldsymbol{X}$.</span>
</div>

依題意可知 $\mathbb{E}\bigl(e^{\boldsymbol{t}^{\mathrm{T}}\boldsymbol{X}}\bigm|\boldsymbol{Y}=\boldsymbol{y}\bigr)=e^{\boldsymbol{t}^{\mathrm{T}}\boldsymbol{y}+\boldsymbol{t}^{\mathrm{T}}\mathbf{\Sigma}\boldsymbol{t}/2}$ 這條式子，則由[雙重期望值定理](/lecture-notes/double-expectation-theorem/#thm-double-expectation)可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{\sssig \boldsymbol{X}}(\boldsymbol{t})&=\mathbb{E}\Bigl[\mathbb{E}\Bigl(e^{\boldsymbol{t}^{\mathrm{T}}\boldsymbol{X}}\Bigm|\boldsymbol{Y}\Bigr)\Bigr]=\mathbb{E}\Bigl[e^{\boldsymbol{t}^{\mathrm{T}}\boldsymbol{Y}+\boldsymbol{t}^{\mathrm{T}}\mathbf{\Sigma}\boldsymbol{t}/2}\Bigr]=e^{\boldsymbol{t}^{\mathrm{T}}\mathbf{\Sigma}\boldsymbol{t}/2}\times\mathbb{E}\Bigl(e^{\boldsymbol{t}^{\mathrm{T}}\boldsymbol{Y}}\Bigr)\\[0.45em]
&=e^{\boldsymbol{t}^{\mathrm{T}}\mathbf{\Sigma}\boldsymbol{t}/2}\times M_{\sssig \boldsymbol{Y}}(\boldsymbol{t})=e^{\boldsymbol{t}^{\mathrm{T}}\mathbf{\Sigma}\boldsymbol{t}/2}\times e^{\boldsymbol{t}^{\mathrm{T}}\boldsymbol{\mu}+\boldsymbol{t}^{\mathrm{T}}\mathbf{\Lambda}\boldsymbol{t}/2}=e^{\boldsymbol{t}^{\mathrm{T}}\boldsymbol{\mu}+\boldsymbol{t}^{\mathrm{T}}(\mathbf{\Sigma}+\mathbf{\Lambda})\boldsymbol{t}/2},\ \boldsymbol{t}\in\mathbb{R}^{k}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig \boldsymbol{X}}(\boldsymbol{t})&=\mathbb{E}\Bigl[\mathbb{E}\Bigl(e^{\boldsymbol{t}^{\mathrm{T}}\boldsymbol{X}}\Bigm|\boldsymbol{Y}\Bigr)\Bigr]\\[0.45em]
&=\mathbb{E}\Bigl[e^{\boldsymbol{t}^{\mathrm{T}}\boldsymbol{Y}+\boldsymbol{t}^{\mathrm{T}}\mathbf{\Sigma}\boldsymbol{t}/2}\Bigr]\\[0.45em]
&=e^{\boldsymbol{t}^{\mathrm{T}}\mathbf{\Sigma}\boldsymbol{t}/2}\times\mathbb{E}\Bigl(e^{\boldsymbol{t}^{\mathrm{T}}\boldsymbol{Y}}\Bigr)\\[0.45em]
&=e^{\boldsymbol{t}^{\mathrm{T}}\mathbf{\Sigma}\boldsymbol{t}/2}\times M_{\sssig \boldsymbol{Y}}(\boldsymbol{t})\\[0.45em]
&=e^{\boldsymbol{t}^{\mathrm{T}}\mathbf{\Sigma}\boldsymbol{t}/2}\times e^{\boldsymbol{t}^{\mathrm{T}}\boldsymbol{\mu}+\boldsymbol{t}^{\mathrm{T}}\mathbf{\Lambda}\boldsymbol{t}/2}\\[0.45em]
&=e^{\boldsymbol{t}^{\mathrm{T}}\boldsymbol{\mu}+\boldsymbol{t}^{\mathrm{T}}(\mathbf{\Sigma}+\mathbf{\Lambda})\boldsymbol{t}/2},\\[0.45em]
&\qquad\qquad \boldsymbol{t}\in\mathbb{R}^{k}
\end{aligned}
$$

</div>

由 [mgf 唯一性](/lecture-notes/uniqueness-of-the-mgf/#thm-mgf-uniqueness)可知

$$
\boldsymbol{X}\sim\mathcal{N}_{\sssig k}\bigl(\boldsymbol{\mu},\ \mathbf{\Sigma}+\mathbf{\Lambda}\bigr)
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個問題有趣的地方在於，這是一個階層模型 <span lang="en">(hierarchical model)</span>，我們必須先知道 $\boldsymbol{Y}$ 的值，進而以其作為 $\boldsymbol{X}$ 的期望值，那麼如果不先給定 $\boldsymbol{Y}$ 的值呢? 平均而言，$\boldsymbol{X}$ 的值將會以 $\boldsymbol{Y}$ 的期望值作為期望值，但是由於多考慮了一層變異 (即 $\boldsymbol{Y}$ 的變異)，故變異數會疊加，也就是 <span class="text-nowrap">$\mathbf{\Sigma}+\mathbf{\Lambda}$，</span>但不改其分配仍為常態的結果。

我們曾經在[貝塔函數與貝塔分配](/lecture-notes/beta-function-and-distribution/)一篇中提到，貝氏統計學派中，常見的共軛分配中，就有**常態-常態**的選擇，而這題正是這樣的例子，且是一個多元常態分配。

</div>

[^idempotent]: 冪等矩陣又稱自乘不變矩陣，是一種不論自己經過幾次方，永恆都跟自己相等的矩陣。

[^application]: 這個定理最主要的應用，與[科克蘭定理](/lecture-notes/chi-squared-distribution/#thm-cochran-theorem)很相似，可以用來說明樣本變異數 $S^{2}$ 的抽樣分配。當然，這個定理還有許多進階的應用。

## 本篇小結

[Theorem 4.29](#thm-block-independence) 把二元常態分配中「零相關等價於獨立」這件事推廣到分塊的層次: 把 $\boldsymbol{X}$ 切成 $\boldsymbol{X}_1$ 與 $\boldsymbol{X}_2$ 兩塊之後，共變異數矩陣也跟著切成四塊，而非對角的那一塊 $\mathbf{\Sigma}_{12}$ 是否為零矩陣，恰好就決定了兩塊之間獨立與否。這條性質為多元常態分配所獨有，一般的分配只有「獨立可推出零相關」這一個方向。

[Example 4.65](#ex-multivariate-normal-ind-1) 是這條性質最重要的應用。作法是把 $\overline{X}$ 與 $n$ 個離差 $X_i-\overline{X}$ 併成一個 $(n+1)$ 維的隨機向量，並把它寫成 $\begin{bmatrix} \frac{1}{\,n\,}\boldsymbol{1}^{\mathrm{T}}\\ \mathbb{I}_n-\mathbf{H} \end{bmatrix}\boldsymbol{X}$ 這個仿射變換，於是新向量仍為多元常態分配，其共變異數矩陣即 $\mathbf{A}\mathbf{\Sigma}\mathbf{A}^{\mathrm{T}}$ 這個式子。由於 $\frac{1}{\,n\,}\boldsymbol{1}^{\mathrm{T}}(\mathbb{I}_n-\mathbf{H})^{\mathrm{T}}=\boldsymbol{0}^{\mathrm{T}}$ 這條等式，非對角分塊為零，因此 $\overline{X}$ 與全部的離差獨立；$S^{2}$ 只是這些離差的函數，故 $\overline{X}$ 與 $S^{2}$ 獨立。同一段推導也給出了一條一般化的準則: $\mathbf{A}\mathbf{B}^{\mathrm{T}}=\mathbf{0}$ 時 $\mathbf{A}\boldsymbol{X}$ 與 $\mathbf{B}\boldsymbol{X}$ 獨立。

[Example 4.66](#ex-multivariate-normal-ind-2) 換一條路走同一件事。它不動矩陣，改由動差母函數下手: 先算出 $Y=\sum_{i=1}^{n}a_iX_i$ 與 $Z=\sum_{i=1}^{n}b_iX_i$ 的聯合動差母函數，再比對它與兩個邊際動差母函數的乘積，兩者相等的充要條件恰好是 <span class="text-nowrap">$\sum_{i=1}^{n}a_ib_i=0$。</span>第三小題算出 $\mathrm{Cov}(Y,Z)=\sigma^{2}\sum_{i=1}^{n}a_ib_i$ 這個結果，與第二小題合起來看，正是零相關與獨立在二元常態分配中等價的又一個實例。若把兩組係數排成 $\mathbf{A}$ 與 $\mathbf{B}$ 兩個列向量，這個條件就寫成 <span class="text-nowrap">$\mathbf{A}\mathbf{B}^{\mathrm{T}}=0$，</span>與前一題的準則完全一致。

[Theorem 4.30](#thm-idempotent-quadratic-form) 則把矩陣運算用在另一個方向。$\boldsymbol{X}\sim\mathcal{MN}(\boldsymbol{\mu},\sigma^{2}\mathbb{I}_n)$ 而 $\mathbf{A}$ 為冪等矩陣時，二次形式 $\boldsymbol{X}^{\mathrm{T}}\mathbf{A}\boldsymbol{X}/\sigma^{2}$ 服從卡方分配，自由度即 <span class="text-nowrap">$\mathrm{tr}(\mathbf{A})$，</span>條件是 $\boldsymbol{\mu}^{\mathrm{T}}\mathbf{A}\boldsymbol{\mu}=0$ 這一項。把 $\mathbf{A}$ 取為 [Example 4.65](#ex-multivariate-normal-ind-1) 中的同一個冪等矩陣 <span class="text-nowrap">$\mathbb{I}_n-\frac{1}{\,n\,}\boldsymbol{1}\boldsymbol{1}^{\mathrm{T}}$，</span>其跡為 $n-1$ 而 $\boldsymbol{\mu}^{\mathrm{T}}\mathbf{A}\boldsymbol{\mu}=0$ 成立，於是由這條定理即得 <span class="text-nowrap">$\frac{\,(n-1)S^{2}\,}{\sigma^{2}}\sim\chi^{2}(n-1)$。</span>[Example 4.67](#ex-multivariate-normal-ind-3) 是同一條定理的操作演練: 先把 $Q$ 展開並整理成二次形式以求得 $\mathbf{A}$，再驗證它冪等、跡為 $3$ 且 $\boldsymbol{\mu}^{\mathrm{T}}\mathbf{A}\boldsymbol{\mu}=0$，即得 <span class="text-nowrap">$Q\sim\chi^{2}(3)$。</span>

[Example 4.68](#ex-multivariate-normal-ind-4) 收在階層模型上。條件分配與邊際分配都是多元常態時，$\boldsymbol{X}$ 的邊際分配仍為多元常態，期望值取 $\boldsymbol{Y}$ 的期望值 <span class="text-nowrap">$\boldsymbol{\mu}$，</span>共變異數矩陣則是兩層變異相加的 <span class="text-nowrap">$\mathbf{\Sigma}+\mathbf{\Lambda}$。</span>推導只用到雙重期望值定理與動差母函數的唯一性，而 $e^{\boldsymbol{t}^{\mathrm{T}}\mathbf{\Sigma}\boldsymbol{t}/2}$ 與 $\boldsymbol{Y}$ 無關可以提到期望值之外，是整段計算的關鍵一步。

第四章至此結束。全章由伯努利實驗一路走到多元常態分配，把常用的機率模型逐一建立起來。[第五章](/lecture-notes/convergence-in-distribution/)轉入極限分配，處理的是母體分配未知或不屬於常見模型時，統計量的抽樣分配該如何逼近，內容包含分配收斂、機率收斂與其他收斂型態，以及中央極限定理與弱大數法則。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
