---
title: "相關係數的性質與相關矩陣"
subtitle: "Properties of the Correlation Coefficient and the Correlation Matrix"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 22
order: 322
permalink: /teaching-topics/correlation-properties-and-matrix/
date: 2026-08-13
published: false
excerpt: "相關係數恆落在 $-1$ 與 $1$ 之間，把這個範圍乘回兩個標準差，馬上得到變異數-共變異數不等式，也就是共變異數必定界在 $-\\sigma_{\\sssig X}\\sigma_{\\sssig Y}$ 與 $\\sigma_{\\sssig X}\\sigma_{\\sssig Y}$ 之間。在了解相關係數以後，共變異數矩陣也可以改寫為相關矩陣: 它同樣是對稱矩陣，但主對角線元素必定為 $1$，非對角線元素為相關係數而界在 $-1$ 到 $1$ 之間，因此主對角線不為 $1$、兩側不對稱或元素超出範圍的矩陣都不是合法的相關矩陣。若另外定義由各個標準差構成的對角矩陣 $\\mathbf{D}$，相關矩陣可以寫成 $\\mathbf{C}=\\mathbf{D}^{-1}\\mathbf{\\Sigma}\\mathbf{D}^{-1}$ 這條式子，這正是對角矩陣的左乘與右乘分別作用在列與行上的結果。本篇的四道例題依序處理最大值期望值的上界、由共變異數建構相關矩陣、旋轉之後兩個新變數的相關係數，以及線性組合之間的相關係數，最後說明即使不算出整個共變異數矩陣，也可以用 $\\boldsymbol{a}^{\\mathrm{T}}\\mathrm{Var}(\\boldsymbol{X})\\boldsymbol{b}$ 求得任意兩個線性組合的共變異數。"
---

[上一篇](/teaching-topics/correlation-coefficient/)以 [Definition 3.19](/teaching-topics/correlation-coefficient/#def-corr) 給出[相關係數](/teaching-topics/correlation-coefficient/#def-corr)，並以 [Theorem 3.19](/teaching-topics/correlation-coefficient/#thm-corr-proper) 證明它的六款性質，其中最後一款是相關係數恆落在 $-1$ 與 $1$ 之間。

本篇先把這個範圍改寫成[共變異數](/teaching-topics/covariance/#def-covariance)的界限，也就是 [Theorem 3.20](#thm-var-cov-ineq) 的變異數-共變異數不等式，並以一道例題示範它在求上界時的用法；接著把[共變異數矩陣](/teaching-topics/covariance-matrix/#def-covar-matrix)改寫為 [Definition 3.20](#def-corr-matrix) 的相關矩陣，說明合法的相關矩陣應具備的條件、推廣到 $n$ 個變數的寫法，以及相關矩陣與共變異數矩陣之間的關係式，最後以三道例題示範相關矩陣的計算。

## 變異數-共變異數不等式

<div id="thm-var-cov-ineq" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 3.20 (變異數-共變異數不等式, variance-covariance inequality)</div>

若 $X$ 與 $Y$ 為二[隨機變數](/teaching-topics/random-variables-and-pmf/#def-random-variable)，則

$$
-\sigma_{\sssig X}\sigma_{\sssig Y}\leqslant\sigma_{\sssig XY}\leqslant \sigma_{\sssig X}\sigma_{\sssig Y}
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.**

由 [Theorem 3.19](/teaching-topics/correlation-coefficient/#thm-corr-proper) 可知 $-1\leqslant\rho_{\sssig XY}\leqslant 1$ 這個範圍，又 $\rho_{\sssig XY}$ $=$ $\frac{\sigma_{\sssig XY}}{\sqrt{\sigma_{\sssig X}^{2}\,\sigma_{\sssig Y}^{2}}}$ 這條等式，故可知

$$
-\sigma_{\sssig X}\sigma_{\sssig Y}\leqslant\sigma_{\sssig XY}\leqslant \sigma_{\sssig X}\sigma_{\sssig Y}
$$

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div id="ex-correlation-bound-example" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.42</div>

<div lang="en" markdown="1">
Suppose that $X$ and $Y$ are two dependent random variables sharing a common mean $0$ and a common variance <span class="text-nowrap">$1$,</span> and let $\rho$ be their correlation coefficient. Show that

$$
\mathbb{E}\bigl[\max(X^{2}, Y^{2})\bigr]\leqslant 1+\sqrt{1-\rho^{2}}
$$

[hint: the identity $\max(a, b)=\frac{1}{\,2\,}\bigl(\lvert a+b\rvert+\lvert a-b\rvert\bigr)$ holds for every <span class="text-nowrap">$a, b\geqslant 0$;</span> apply it together with the Cauchy-Schwarz inequality.]
</div>

由於 $\max(a, b)$ $=$ $\frac{1}{\,2\,}\bigl(\lvert a+b\rvert+\lvert a-b\rvert\bigr)$ 這條等式在 $a, b \geqslant 0$ 之下成立，故知道

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[\max(X^{2}, Y^{2})\bigr]&=\mathbb{E}\Bigl[\frac{1}{\,2\,}\bigl(\lvert X^{2}+Y^{2}\rvert+\lvert X^{2}-Y^{2}\rvert\bigr)\Bigr]=\frac{1}{\,2\,}\mathbb{E}\bigl[\lvert X^{2}+Y^{2}\rvert\bigr]+\frac{1}{\,2\,}\mathbb{E}\bigl[\lvert X^{2}-Y^{2}\rvert\bigr]\\[0.45em]
&=\frac{1}{\,2\,}\mathbb{E}(X^{2}+Y^{2})+\frac{1}{\,2\,}\mathbb{E}\bigl[\lvert (X+Y)(X-Y)\rvert\bigr]
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[\max(X^{2}, Y^{2})\bigr]&=\mathbb{E}\Bigl[\frac{1}{\,2\,}\bigl(\lvert X^{2}+Y^{2}\rvert+\lvert X^{2}-Y^{2}\rvert\bigr)\Bigr]\\[0.45em]
&=\frac{1}{\,2\,}\mathbb{E}\bigl[\lvert X^{2}+Y^{2}\rvert\bigr]+\frac{1}{\,2\,}\mathbb{E}\bigl[\lvert X^{2}-Y^{2}\rvert\bigr]\\[0.45em]
&=\frac{1}{\,2\,}\mathbb{E}(X^{2}+Y^{2})+\frac{1}{\,2\,}\mathbb{E}\bigl[\lvert (X+Y)(X-Y)\rvert\bigr]
\end{aligned}
$$

</div>

由於 $\mathbb{E}(X)$ $=$ $\mathbb{E}(Y)$ $=$ $0$ 且 $\mathrm{Var}(X)$ $=$ $\mathrm{Var}(Y)$ $=$ <span class="text-nowrap">$1$，</span>故 <span class="text-nowrap">$\mathbb{E}(X^{2})=\mathbb{E}(Y^{2})=1$。</span>

可知 $\frac{1}{\,2\,}\mathbb{E}(X^{2}+Y^{2})$ $=$ $\frac{1}{\,2\,}\bigl[\mathbb{E}(X^{2})+\mathbb{E}(Y^{2})\bigr]$ $=$ <span class="text-nowrap">$1$，</span>並由柯西不等式可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\Bigl(\mathbb{E}\bigl[\lvert (X+Y)(X-Y)\rvert\bigr]\Bigr)^{2}\leqslant\mathbb{E}\bigl[\lvert X+Y\rvert^{2}\bigr]\mathbb{E}\bigl[\lvert X-Y\rvert^{2}\bigr]=\mathbb{E}\bigl[(X+Y)^{2}\bigr]\mathbb{E}\bigl[(X-Y)^{2}\bigr]
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\Bigl(\mathbb{E}\bigl[\lvert (X+Y)(X-Y)\rvert\bigr]\Bigr)^{2}&\leqslant\mathbb{E}\bigl[\lvert X+Y\rvert^{2}\bigr]\mathbb{E}\bigl[\lvert X-Y\rvert^{2}\bigr]\\[0.45em]
&=\mathbb{E}\bigl[(X+Y)^{2}\bigr]\mathbb{E}\bigl[(X-Y)^{2}\bigr]
\end{aligned}
$$

</div>

又可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\mathbb{E}\bigl[(X+Y)^{2}\bigr]=\mathbb{E}(X^{2}+Y^{2}+2XY)=2+2\rho\\[0.45em]
\mathbb{E}\bigl[(X-Y)^{2}\bigr]=2-2\rho\\[0.45em]
\Bigl(\because\ \mathrm{Var}(X)=\mathrm{Var}(Y)=1\\[0.45em]
\Longrightarrow\ \mathbb{E}(XY)=\frac{\mathbb{E}(XY)}{\sqrt{\mathrm{Var}(X)\mathrm{Var}(Y)}}=\rho\Bigr)
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[(X+Y)^{2}\bigr]&=\mathbb{E}(X^{2}+Y^{2}+2XY)\\[0.45em]
&=2+2\rho\\[0.45em]
\mathbb{E}\bigl[(X-Y)^{2}\bigr]&=2-2\rho\\[0.45em]
\Bigl(\because\ \mathrm{Var}(X)&=\mathrm{Var}(Y)=1\\[0.45em]
\Longrightarrow\ \mathbb{E}(XY)&=\frac{\mathbb{E}(XY)}{\sqrt{\mathrm{Var}(X)\mathrm{Var}(Y)}}=\rho\Bigr)
\end{aligned}
$$

</div>

此即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\bigl[\lvert (X+Y)(X-Y)\rvert\bigr]\leqslant\sqrt{(2+2\rho)(2-2\rho)}=2\sqrt{1-\rho^{2}}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[\lvert (X+Y)(X-Y)\rvert\bigr]&\leqslant\sqrt{(2+2\rho)(2-2\rho)}=2\sqrt{1-\rho^{2}}
\end{aligned}
$$

</div>

故可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\bigl[\max(X^{2}, Y^{2})\bigr]=\frac{1}{\,2\,}\mathbb{E}(X^{2}+Y^{2})+\frac{1}{\,2\,}\mathbb{E}\bigl[\lvert (X+Y)(X-Y)\rvert\bigr]\leqslant 1+\sqrt{1-\rho^{2}}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[\max(X^{2}, Y^{2})\bigr]&=\frac{1}{\,2\,}\mathbb{E}(X^{2}+Y^{2})+\frac{1}{\,2\,}\mathbb{E}\bigl[\lvert (X+Y)(X-Y)\rvert\bigr]\\[0.45em]
&\leqslant 1+\sqrt{1-\rho^{2}}
\end{aligned}
$$

</div>

</div>

## 相關矩陣

<div id="def-corr-matrix" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 3.20 (相關矩陣, correlation matrix)</div>

若 $X, Y, Z$ 為隨機變數，則定義三者的**相關矩陣 <span lang="en">(correlation matrix)</span>** 為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbf{C}=
\begin{bmatrix}
\operatorname{Corr}(X,X) & \operatorname{Corr}(X,Y) & \operatorname{Corr}(X,Z)\\
\operatorname{Corr}(Y,X) & \operatorname{Corr}(Y,Y) & \operatorname{Corr}(Y,Z)\\
\operatorname{Corr}(Z,X) & \operatorname{Corr}(Z,Y) & \operatorname{Corr}(Z,Z)
\end{bmatrix}
=
\begin{bmatrix}
1 & \rho_{\sssig XY} & \rho_{\sssig XZ}\\
\rho_{\sssig YX} & 1 & \rho_{\sssig YZ}\\
\rho_{\sssig ZX} & \rho_{\sssig ZY} & 1
\end{bmatrix}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbf{C}&=
\begin{bmatrix}
\operatorname{Corr}(X,X) & \operatorname{Corr}(X,Y) & \operatorname{Corr}(X,Z)\\
\operatorname{Corr}(Y,X) & \operatorname{Corr}(Y,Y) & \operatorname{Corr}(Y,Z)\\
\operatorname{Corr}(Z,X) & \operatorname{Corr}(Z,Y) & \operatorname{Corr}(Z,Z)
\end{bmatrix}\\[0.55em]
&=
\begin{bmatrix}
1 & \rho_{\sssig XY} & \rho_{\sssig XZ}\\
\rho_{\sssig YX} & 1 & \rho_{\sssig YZ}\\
\rho_{\sssig ZX} & \rho_{\sssig ZY} & 1
\end{bmatrix}
\end{aligned}
$$

</div>

</div>

相關矩陣有一些地方需要注意:

(1) 上述定義中的 $\rho_{\sssig XY}, \rho_{\sssig XZ}, \rho_{\sssig YZ},$ $\rho_{\sssig YX}, \rho_{\sssig ZX}, \rho_{\sssig ZY}$ 分別表 $X, Y, Z$ 間的相關係數，且由[相關係數的對稱性](/teaching-topics/correlation-coefficient/#thm-corr-proper)，我們可以發現其實 $\rho_{\sssig XY} = \rho_{\sssig YX},$ $\rho_{\sssig XZ} = \rho_{\sssig ZX}$ 及 <span class="text-nowrap">$\rho_{\sssig YZ} = \rho_{\sssig ZY}$。</span>
{: .topic-paren-item}

與共變異數矩陣相同，相關矩陣是一個對稱矩陣，但主對角線元素必定為 <span class="text-nowrap">$1$，</span>且由於非對角線元素 <span lang="en">(off-diagonal element)</span> 為相關係數，故其應界在 $-1$ 到 $1$ 之間。
{: .topic-paren-cont}

幾個不合法的相關矩陣可見下面的例子:
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{bmatrix}
2 & 0.2 & 0.3\\
0.2 & 2 & 0.4\\
0.3 & 0.4 & 3
\end{bmatrix}
\qquad
\begin{bmatrix}
1 & 0.2 & 0.7\\
0.2 & 1 & 0.5\\
0.7 & 0.3 & 1
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
\begin{aligned}
&\begin{bmatrix}
2 & 0.2 & 0.3\\
0.2 & 2 & 0.4\\
0.3 & 0.4 & 3
\end{bmatrix}\\[0.55em]
&\begin{bmatrix}
1 & 0.2 & 0.7\\
0.2 & 1 & 0.5\\
0.7 & 0.3 & 1
\end{bmatrix}\\[0.55em]
&\begin{bmatrix}
1 & 2 & 3\\
2 & 1 & 4\\
3 & 4 & 1
\end{bmatrix}
\end{aligned}
$$

</div>

(2) 當然，上述的定義也不僅限於三個變數，我們可將其推廣至任意 $n$ 個變數，如下定義:
{: .topic-paren-item}

若 $X_1, \ldots, X_n$ 為 $n$ 個隨機變數，則定義其相關矩陣為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbf{C}&=
\begin{bmatrix}
\operatorname{Corr}(X_1, X_1) & \operatorname{Corr}(X_1, X_2) & \cdots & \operatorname{Corr}(X_1, X_n)\\
\operatorname{Corr}(X_2, X_1) & \operatorname{Corr}(X_2, X_2) & \cdots & \operatorname{Corr}(X_2, X_n)\\
\vdots & \vdots & \ddots & \vdots\\
\operatorname{Corr}(X_n, X_1) & \operatorname{Corr}(X_n, X_2) & \cdots & \operatorname{Corr}(X_n, X_n)
\end{bmatrix}\\[0.45em]
&=
\begin{bmatrix}
1 & \rho_{\sssig 12} & \cdots & \rho_{\sssig 1n}\\
\rho_{\sssig 21} & 1 & \cdots & \rho_{\sssig 2n}\\
\vdots & \vdots & \ddots & \vdots\\
\rho_{\sssig n1} & \rho_{\sssig n2} & \cdots & 1
\end{bmatrix}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbf{C}&=\begin{bmatrix}
\operatorname{Corr}(X_1, X_1) & \cdots & \operatorname{Corr}(X_1, X_n)\\
\vdots & \ddots & \vdots\\
\operatorname{Corr}(X_n, X_1) & \cdots & \operatorname{Corr}(X_n, X_n)
\end{bmatrix}\\[0.55em]
&=
\begin{bmatrix}
1 & \rho_{\sssig 12} & \cdots & \rho_{\sssig 1n}\\
\rho_{\sssig 21} & 1 & \cdots & \rho_{\sssig 2n}\\
\vdots & \vdots & \ddots & \vdots\\
\rho_{\sssig n1} & \rho_{\sssig n2} & \cdots & 1
\end{bmatrix}
\end{aligned}
$$

</div>

(3) 事實上，基於相關矩陣與共變異數矩陣的相似性，我們可以額外定義矩陣
{: .topic-paren-item}

$$
\mathbf{D}=\sqrt{\mathrm{diag}(\mathbf{\Sigma})}=
\begin{bmatrix}
\sigma_1 & 0 & \cdots & 0\\
0 & \sigma_2 & \cdots & 0\\
\vdots & \vdots & \ddots & \vdots\\
0 & 0 & \cdots & \sigma_n
\end{bmatrix}
$$

則相關矩陣 $\mathbf{C}$ 可以被表示為
{: .topic-paren-cont}

$$
\mathbf{C}=\mathbf{D}^{-1}\mathbf{\Sigma}\mathbf{D}^{-1}
$$

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

事實上這是利用了對角矩陣 <span lang="en">(diagonal matrix)</span> 的左乘 <span lang="en">(left product)</span> 與右乘 <span lang="en">(right product)</span>，分別會讓矩陣的列與行對應乘上指定倍數的功能，再搭配對角矩陣的反矩陣即是對角元素各自的倒數構成的對角矩陣的性質，所得到的做法。雖然看似平淡無奇，但這種寫法在程式語言中卻能發揮奇大的作用。

</div>

## 相關矩陣的計算

<div id="ex-four-dimensional-normal-correlation" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.43</div>

<div lang="en" markdown="1">
Suppose that $\boldsymbol{X}=\bigl[\,X_1, X_2, X_3, X_4\,\bigr]^{\mathrm{T}}$ follows a 4-dimensional normal distribution whose means are <span class="text-nowrap">$\mathbb{E}(X_1)=2$,</span> <span class="text-nowrap">$\mathbb{E}(X_2)=1$,</span> $\mathbb{E}(X_3)=3$ and <span class="text-nowrap">$\mathbb{E}(X_4)=6$,</span> whose variances are <span class="text-nowrap">$\mathrm{Var}(X_1)=1$,</span> <span class="text-nowrap">$\mathrm{Var}(X_2)=2$,</span> $\mathrm{Var}(X_3)=3$ and <span class="text-nowrap">$\mathrm{Var}(X_4)=4$,</span> and whose covariances satisfy $\operatorname{Cov}(X_i,\,X_j)=1$ for every <span class="text-nowrap">$i\neq j$.</span> Find the correlation matrix of <span class="text-nowrap">$\boldsymbol{X}$.</span>
</div>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\rho_{12}=\frac{\sigma_{12}}{\sigma_1\sigma_2}=\frac{1}{\sqrt{2}},\ \rho_{13}=\frac{\sigma_{13}}{\sigma_1\sigma_3}=\frac{1}{\sqrt{3}},\ \rho_{14}=\frac{\sigma_{14}}{\sigma_1\sigma_4}=\frac{1}{\sqrt{4}}\\[0.55em]
\rho_{23}=\frac{\sigma_{23}}{\sigma_2\sigma_3}=\frac{1}{\sqrt{6}},\ \rho_{24}=\frac{\sigma_{24}}{\sigma_2\sigma_4}=\frac{1}{\sqrt{8}},\ \rho_{34}=\frac{\sigma_{34}}{\sigma_3\sigma_4}=\frac{1}{\sqrt{12}}
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\rho_{12}&=\frac{\sigma_{12}}{\sigma_1\sigma_2}=\frac{1}{\sqrt{2}},\ \rho_{13}=\frac{\sigma_{13}}{\sigma_1\sigma_3}=\frac{1}{\sqrt{3}}\\[0.55em]
\rho_{14}&=\frac{\sigma_{14}}{\sigma_1\sigma_4}=\frac{1}{\sqrt{4}},\ \rho_{23}=\frac{\sigma_{23}}{\sigma_2\sigma_3}=\frac{1}{\sqrt{6}}\\[0.55em]
\rho_{24}&=\frac{\sigma_{24}}{\sigma_2\sigma_4}=\frac{1}{\sqrt{8}},\ \rho_{34}=\frac{\sigma_{34}}{\sigma_3\sigma_4}=\frac{1}{\sqrt{12}}
\end{aligned}
$$

</div>

則由[相關矩陣的定義](#def-corr-matrix)可知

$$
\mathbf{C}=
\begin{bmatrix}
1 & \frac{1}{\sqrt{2}} & \frac{1}{\sqrt{3}} & \frac{1}{\sqrt{4}}\\[0.35em]
\frac{1}{\sqrt{2}} & 1 & \frac{1}{\sqrt{6}} & \frac{1}{\sqrt{8}}\\[0.35em]
\frac{1}{\sqrt{3}} & \frac{1}{\sqrt{6}} & 1 & \frac{1}{\sqrt{12}}\\[0.35em]
\frac{1}{\sqrt{4}} & \frac{1}{\sqrt{8}} & \frac{1}{\sqrt{12}} & 1
\end{bmatrix}
$$

</div>

<div id="ex-linear-combination-correlation" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.44</div>

<div lang="en" markdown="1">
Suppose that $X_1$ and $X_2$ are independently distributed with mean $\mu_i$ and variance $\sigma_{i}^{2}$ for <span class="text-nowrap">$i=1, 2$,</span> and define

$$
\left\lbrace\begin{array}{l} Z_1 = X_1\cos\theta + X_2\sin\theta\\ Z_2 = X_2\cos\theta-X_1\sin\theta\end{array}\right.
$$

Find the correlation coefficient $\rho$ of $Z_1$ and <span class="text-nowrap">$Z_2$,</span> and show that

$$
0 \leqslant \rho^{2} \leqslant \biggl(\frac{\sigma_1^{2}-\sigma_2^{2}}{\sigma_1^{2}+\sigma_2^{2}}\biggr)^{2}
$$

</div>

由題意可知

$$
\begin{bmatrix} X_1\\ X_2 \end{bmatrix}\sim\Biggl(\begin{bmatrix} \mu_1\\ \mu_2 \end{bmatrix},\ \begin{bmatrix} \sigma_1^{2} & 0\\ 0 & \sigma_{2}^{2} \end{bmatrix}\Biggr)
$$

且可令

$$
\boldsymbol{Z}=\begin{bmatrix} Z_1\\ Z_2 \end{bmatrix}=\begin{bmatrix} \cos\theta & \sin\theta\\ -\sin\theta & \cos\theta \end{bmatrix}\begin{bmatrix} X_1\\ X_2 \end{bmatrix}
$$

則可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(\boldsymbol{Z})&=\mathrm{Var}\Biggl(\begin{bmatrix} \cos\theta & \sin\theta\\ -\sin\theta & \cos\theta \end{bmatrix}\begin{bmatrix} X_1\\ X_2 \end{bmatrix}\Biggr)\\[0.45em]
&=\begin{bmatrix} \cos\theta & \sin\theta\\ -\sin\theta & \cos\theta \end{bmatrix}\begin{bmatrix} \sigma_1^{2} & 0\\ 0 & \sigma_{2}^{2} \end{bmatrix}\begin{bmatrix} \cos\theta & \sin\theta\\ -\sin\theta & \cos\theta \end{bmatrix}^{\mathrm{T}}\\[0.45em]
&=\begin{bmatrix} \cos^{2}\theta\sigma_1^{2}+\sin^{2}\theta\sigma_2^{2} & -\cos\theta\sin\theta(\sigma_1^{2}-\sigma_2^{2})\\ -\cos\theta\sin\theta(\sigma_1^{2}-\sigma_2^{2}) & \sin^{2}\theta\sigma_1^{2}+\cos^{2}\theta\sigma_2^{2} \end{bmatrix}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(\boldsymbol{Z})&=\mathrm{Var}\Biggl(\begin{bmatrix} \cos\theta & \sin\theta\\ -\sin\theta & \cos\theta \end{bmatrix}\begin{bmatrix} X_1\\ X_2 \end{bmatrix}\Biggr)\\[0.45em]
&=\begin{bmatrix} \cos\theta & \sin\theta\\ -\sin\theta & \cos\theta \end{bmatrix}\begin{bmatrix} \sigma_1^{2} & 0\\ 0 & \sigma_{2}^{2} \end{bmatrix}\begin{bmatrix} \cos\theta & \sin\theta\\ -\sin\theta & \cos\theta \end{bmatrix}^{\mathrm{T}}\\[0.45em]
&=\begin{bmatrix} \cos^{2}\theta\sigma_1^{2}+\sin^{2}\theta\sigma_2^{2} & -\cos\theta\sin\theta(\sigma_1^{2}-\sigma_2^{2})\\ -\cos\theta\sin\theta(\sigma_1^{2}-\sigma_2^{2}) & \sin^{2}\theta\sigma_1^{2}+\cos^{2}\theta\sigma_2^{2} \end{bmatrix}
\end{aligned}
$$

</div>

又令

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbf{D}=\sqrt{\mathrm{diag}\bigl[\mathrm{Var}(\boldsymbol{Z})\bigr]}=\begin{bmatrix} \sqrt{\cos^{2}\theta\sigma_1^{2}+\sin^{2}\theta\sigma_2^{2}} & 0\\ 0 & \sqrt{\sin^{2}\theta\sigma_1^{2}+\cos^{2}\theta\sigma_2^{2}} \end{bmatrix}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbf{D}&=\sqrt{\mathrm{diag}\bigl[\mathrm{Var}(\boldsymbol{Z})\bigr]}\\[0.55em]
&=\begin{bmatrix} \sqrt{\cos^{2}\theta\sigma_1^{2}+\sin^{2}\theta\sigma_2^{2}} & 0\\ 0 & \sqrt{\sin^{2}\theta\sigma_1^{2}+\cos^{2}\theta\sigma_2^{2}} \end{bmatrix}
\end{aligned}
$$

</div>

則可知 $\boldsymbol{Z}$ 之相關矩陣為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbf{C}_{\sssig \boldsymbol{Z}}&=\mathbf{D}^{-1}\begin{bmatrix} \cos^{2}\theta\sigma_1^{2}+\sin^{2}\theta\sigma_2^{2} & -\cos\theta\sin\theta(\sigma_1^{2}-\sigma_2^{2})\\ -\cos\theta\sin\theta(\sigma_1^{2}-\sigma_2^{2}) & \sin^{2}\theta\sigma_1^{2}+\cos^{2}\theta\sigma_2^{2} \end{bmatrix}\mathbf{D}^{-1}\\[0.45em]
&=\begin{bmatrix} 1 & \frac{-\cos\theta\sin\theta(\sigma_1^{2}-\sigma_2^{2})}{\sqrt{\begin{array}{c}(\cos^{2}\theta\sigma_1^{2}+\sin^{2}\theta\sigma_2^{2})\\ (\sin^{2}\theta\sigma_1^{2}+\cos^{2}\theta\sigma_2^{2})\end{array}}}\\[1.2em] \frac{-\cos\theta\sin\theta(\sigma_1^{2}-\sigma_2^{2})}{\sqrt{\begin{array}{c}(\cos^{2}\theta\sigma_1^{2}+\sin^{2}\theta\sigma_2^{2})\\ (\sin^{2}\theta\sigma_1^{2}+\cos^{2}\theta\sigma_2^{2})\end{array}}} & 1 \end{bmatrix}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbf{C}_{\sssig \boldsymbol{Z}}&=\mathbf{D}^{-1}\begin{bmatrix} \cos^{2}\theta\sigma_1^{2}+\sin^{2}\theta\sigma_2^{2} & -\cos\theta\sin\theta(\sigma_1^{2}-\sigma_2^{2})\\ -\cos\theta\sin\theta(\sigma_1^{2}-\sigma_2^{2}) & \sin^{2}\theta\sigma_1^{2}+\cos^{2}\theta\sigma_2^{2} \end{bmatrix}\mathbf{D}^{-1}\\[0.55em]
&=\begin{bmatrix} 1 & \frac{-\cos\theta\sin\theta(\sigma_1^{2}-\sigma_2^{2})}{\sqrt{\begin{array}{c}(\cos^{2}\theta\sigma_1^{2}+\sin^{2}\theta\sigma_2^{2})\\ (\sin^{2}\theta\sigma_1^{2}+\cos^{2}\theta\sigma_2^{2})\end{array}}}\\[1.2em] \frac{-\cos\theta\sin\theta(\sigma_1^{2}-\sigma_2^{2})}{\sqrt{\begin{array}{c}(\cos^{2}\theta\sigma_1^{2}+\sin^{2}\theta\sigma_2^{2})\\ (\sin^{2}\theta\sigma_1^{2}+\cos^{2}\theta\sigma_2^{2})\end{array}}} & 1 \end{bmatrix}
\end{aligned}
$$

</div>

此即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\rho=\frac{-\cos\theta\sin\theta(\sigma_1^{2}-\sigma_2^{2})}{\sqrt{(\cos^{2}\theta\sigma_1^{2}+\sin^{2}\theta\sigma_2^{2})(\sin^{2}\theta\sigma_1^{2}+\cos^{2}\theta\sigma_2^{2})}}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\rho=\frac{-\cos\theta\sin\theta(\sigma_1^{2}-\sigma_2^{2})}{\sqrt{\begin{array}{c}(\cos^{2}\theta\sigma_1^{2}+\sin^{2}\theta\sigma_2^{2})\\ (\sin^{2}\theta\sigma_1^{2}+\cos^{2}\theta\sigma_2^{2})\end{array}}}
$$

</div>

則有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\rho^{2}&=\frac{\cos^{2}\theta\sin^{2}\theta(\sigma_1^{2}-\sigma_2^{2})^{2}}{(\cos^{2}\theta\sigma_1^{2}+\sin^{2}\theta\sigma_2^{2})(\sin^{2}\theta\sigma_1^{2}+\cos^{2}\theta\sigma_2^{2})}\\[0.45em]
&=\frac{\cos^{2}\theta\sin^{2}\theta(\sigma_1^{2}-\sigma_2^{2})^{2}}{(\cos^{2}\theta\sin^{2}\theta\sigma_1^{4}+(\cos^{4}\theta+\sin^{4}\theta)\sigma_1^{2}\sigma_2^{2}+\cos^{2}\theta\sin^{2}\theta\sigma_2^{4})}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\rho^{2}&=\frac{\cos^{2}\theta\sin^{2}\theta(\sigma_1^{2}-\sigma_2^{2})^{2}}{\begin{array}{c}(\cos^{2}\theta\sigma_1^{2}+\sin^{2}\theta\sigma_2^{2})\\ (\sin^{2}\theta\sigma_1^{2}+\cos^{2}\theta\sigma_2^{2})\end{array}}\\[0.45em]
&=\frac{\cos^{2}\theta\sin^{2}\theta(\sigma_1^{2}-\sigma_2^{2})^{2}}{\begin{array}{c}(\cos^{2}\theta\sin^{2}\theta\sigma_1^{4}+(\cos^{4}\theta+\sin^{4}\theta)\sigma_1^{2}\sigma_2^{2}\\ +\cos^{2}\theta\sin^{2}\theta\sigma_2^{4})\end{array}}
\end{aligned}
$$

</div>

又可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
1=(\sin^{2}\theta+\cos^{2}\theta)^{2}=\sin^{4}\theta+2\sin^{2}\theta\cos^{2}\theta+\cos^{4}\theta\qquad\therefore\, \sin^{4}\theta+\cos^{4}\theta=1-2\sin^{2}\theta\cos^{2}\theta
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

<div class="topic-math-follow-before" markdown="1">

$$
\begin{aligned}
1&=(\sin^{2}\theta+\cos^{2}\theta)^{2}\\[0.45em]
&=\sin^{4}\theta+2\sin^{2}\theta\cos^{2}\theta+\cos^{4}\theta\\[0.4em]
&\qquad\therefore\, \sin^{4}\theta+\cos^{4}\theta=1-2\sin^{2}\theta\cos^{2}\theta
\end{aligned}
$$

</div>

</div>

且可知

$$
\sin^{2}(2\theta)=4\sin^{2}\theta\cos^{2}\theta\leqslant 1\qquad\therefore\, 1-2\cos^{2}\theta\sin^{2}\theta\geqslant 2\cos^{2}\theta\sin^{2}\theta
$$

故可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\rho^{2}&=\frac{\cos^{2}\theta\sin^{2}\theta(\sigma_1^{2}-\sigma_2^{2})^{2}}{(\cos^{2}\theta\sin^{2}\theta\sigma_1^{4}+(\cos^{4}\theta+\sin^{4}\theta)\sigma_1^{2}\sigma_2^{2}+\cos^{2}\theta\sin^{2}\theta\sigma_2^{4})}\\[0.45em]
&=\frac{\cos^{2}\theta\sin^{2}\theta(\sigma_1^{2}-\sigma_2^{2})^{2}}{(\cos^{2}\theta\sin^{2}\theta\sigma_1^{4}+(1-2\cos^{2}\theta\sin^{2}\theta)\sigma_1^{2}\sigma_2^{2}+\cos^{2}\theta\sin^{2}\theta\sigma_2^{4})}\\[0.45em]
&\leqslant\frac{\cos^{2}\theta\sin^{2}\theta(\sigma_1^{2}-\sigma_2^{2})^{2}}{(\cos^{2}\theta\sin^{2}\theta\sigma_1^{4}+2\sin^{2}\theta\cos^{2}\theta\sigma_1^{2}\sigma_2^{2}+\cos^{2}\theta\sin^{2}\theta\sigma_2^{4})}\\[0.45em]
&=\frac{(\sigma_1^{2}-\sigma_2^{2})^{2}}{(\sigma_1^{4}+2\sigma_1^{2}\sigma_2^{2}+\sigma_2^{4})}=\biggl(\frac{\sigma_1^{2}-\sigma_2^{2}}{\sigma_1^{2}+\sigma_2^{2}}\biggr)^{2}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\rho^{2}&=\frac{\cos^{2}\theta\sin^{2}\theta(\sigma_1^{2}-\sigma_2^{2})^{2}}{\begin{array}{c}(\cos^{2}\theta\sin^{2}\theta\sigma_1^{4}+(\cos^{4}\theta+\sin^{4}\theta)\sigma_1^{2}\sigma_2^{2}\\ +\cos^{2}\theta\sin^{2}\theta\sigma_2^{4})\end{array}}\\[0.45em]
&=\frac{\cos^{2}\theta\sin^{2}\theta(\sigma_1^{2}-\sigma_2^{2})^{2}}{\begin{array}{c}(\cos^{2}\theta\sin^{2}\theta\sigma_1^{4}+(1-2\cos^{2}\theta\sin^{2}\theta)\sigma_1^{2}\sigma_2^{2}\\ +\cos^{2}\theta\sin^{2}\theta\sigma_2^{4})\end{array}}\\[0.45em]
&\leqslant\frac{\cos^{2}\theta\sin^{2}\theta(\sigma_1^{2}-\sigma_2^{2})^{2}}{\begin{array}{c}(\cos^{2}\theta\sin^{2}\theta\sigma_1^{4}+2\sin^{2}\theta\cos^{2}\theta\sigma_1^{2}\sigma_2^{2}\\ +\cos^{2}\theta\sin^{2}\theta\sigma_2^{4})\end{array}}\\[0.45em]
&=\frac{(\sigma_1^{2}-\sigma_2^{2})^{2}}{(\sigma_1^{4}+2\sigma_1^{2}\sigma_2^{2}+\sigma_2^{4})}=\biggl(\frac{\sigma_1^{2}-\sigma_2^{2}}{\sigma_1^{2}+\sigma_2^{2}}\biggr)^{2}
\end{aligned}
$$

</div>

此即

$$
0\leqslant \rho^{2} \leqslant \biggl(\frac{\sigma_1^{2}-\sigma_2^{2}}{\sigma_1^{2}+\sigma_2^{2}}\biggr)^{2}
$$

</div>

<div id="ex-uncorrelated-equal-variance" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.45</div>

<div lang="en" markdown="1">
Suppose that <span class="text-nowrap">$X_1$,</span> $X_2$ and $X_3$ are uncorrelated random variables whose common variance is <span class="text-nowrap">$\sigma^{2}$.</span> Determine the correlation between $X_1 + X_2$ and <span class="text-nowrap">$X_2 + X_3$.</span>
</div>

**[ 法一 ]**

<div class="topic-math-follow-before" markdown="1">

$$
\begin{gathered}
\operatorname{Cov}(X_1+X_2, X_2+X_3)=\mathrm{Var}(X_2)=\sigma^{2}\\[0.45em]
\mathrm{Var}(X_1+X_2)=\mathrm{Var}(X_1)+\mathrm{Var}(X_2)=2\sigma^{2}\\[0.45em]
\mathrm{Var}(X_2+X_3)=\mathrm{Var}(X_2)+\mathrm{Var}(X_3)=2\sigma^{2}
\end{gathered}
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop topic-math-follow" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ \operatorname{Corr}(X_1+X_2, X_2+X_3)&=\frac{\operatorname{Cov}(X_1+X_2, X_2+X_3)}{\sqrt{\mathrm{Var}(X_1+X_2)\mathrm{Var}(X_2+X_3)}}\\[0.45em]
&=\frac{\sigma^{2}}{\sqrt{2\sigma^{2}\cdot 2\sigma^{2}}}=\frac{1}{\,2\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile topic-math-follow" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ \operatorname{Corr}(&X_1+X_2, X_2+X_3)\\[0.45em]
&=\frac{\operatorname{Cov}(X_1+X_2, X_2+X_3)}{\sqrt{\mathrm{Var}(X_1+X_2)\mathrm{Var}(X_2+X_3)}}\\[0.45em]
&=\frac{\sigma^{2}}{\sqrt{2\sigma^{2}\cdot 2\sigma^{2}}}=\frac{1}{\,2\,}
\end{aligned}
$$

</div>

<!-- errata-pending: 上一組數式的分母，書稿 mathstatch3.tex 第 4189 行原文作
     \frac{\cov(X_1+X_2, X_2+X_3)}{\,\V(X_1+X_2)\V(X_2+X_3)\,}，少了根號；
     網頁改為 \sqrt{\mathrm{Var}(X_1+X_2)\mathrm{Var}(X_2+X_3)}。
     依據: 一、相關係數的定義 (mathstatch3.tex 第 3675 行的 Definition 3.19) 分母
     是兩個標準差之積，即兩個變異數之積開平方根。二、書稿自己的下一步即寫成
     \frac{\sigma^2}{\,\sqrt{2\sigma^2\cdot2\sigma^2}\,}，已帶根號，故原式的漏根號
     是排版時的脫字，非另一種寫法。屬 SITE_STYLE_CANON.md 第〇節第 3 點第 (1) 類
     (書稿數學有誤)，待作者裁定後登錄 ERRATA.md。
-->

**[ 法二 ]**

依題意可令

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\boldsymbol{X}=\begin{bmatrix} X_1\\ X_2\\ X_3 \end{bmatrix},\ \text{則}\ \mathrm{Var}(\boldsymbol{X})=\begin{bmatrix} \sigma^{2} & 0 & 0\\ 0 & \sigma^{2} & 0\\ 0 & 0 & \sigma^{2} \end{bmatrix},\ \text{又令}\ \mathbf{A}=\begin{bmatrix} 1 & 1 & 0\\ 0 & 1 & 1 \end{bmatrix}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\boldsymbol{X}&=\begin{bmatrix} X_1\\ X_2\\ X_3 \end{bmatrix},\ \text{則}\ \mathrm{Var}(\boldsymbol{X})=\begin{bmatrix} \sigma^{2} & 0 & 0\\ 0 & \sigma^{2} & 0\\ 0 & 0 & \sigma^{2} \end{bmatrix},\\[0.55em]
\text{又令}\ \mathbf{A}&=\begin{bmatrix} 1 & 1 & 0\\ 0 & 1 & 1 \end{bmatrix}
\end{aligned}
$$

</div>

可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(\mathbf{A}\boldsymbol{X})&=\mathbf{A}\,\mathrm{Var}(\boldsymbol{X})\,\mathbf{A}^{\mathrm{T}}\\[0.45em]
&=\begin{bmatrix} 1 & 1 & 0\\ 0 & 1 & 1 \end{bmatrix}\begin{bmatrix} \sigma^{2} & 0 & 0\\ 0 & \sigma^{2} & 0\\ 0 & 0 & \sigma^{2} \end{bmatrix}\begin{bmatrix} 1 & 1 & 0\\ 0 & 1 & 1 \end{bmatrix}^{\mathrm{T}}=\begin{bmatrix} 2\sigma^{2} & \sigma^{2}\\ \sigma^{2} & 2\sigma^{2} \end{bmatrix}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(\mathbf{A}\boldsymbol{X})&=\mathbf{A}\,\mathrm{Var}(\boldsymbol{X})\,\mathbf{A}^{\mathrm{T}}\\[0.45em]
&=\begin{bmatrix} 1 & 1 & 0\\ 0 & 1 & 1 \end{bmatrix}\begin{bmatrix} \sigma^{2} & 0 & 0\\ 0 & \sigma^{2} & 0\\ 0 & 0 & \sigma^{2} \end{bmatrix}\begin{bmatrix} 1 & 1 & 0\\ 0 & 1 & 1 \end{bmatrix}^{\mathrm{T}}\\[0.45em]
&=\begin{bmatrix} 2\sigma^{2} & \sigma^{2}\\ \sigma^{2} & 2\sigma^{2} \end{bmatrix}
\end{aligned}
$$

</div>

又若令

$$
\mathbf{D}=\sqrt{\mathrm{diag}\bigl[\mathrm{Var}(\mathbf{A}\boldsymbol{X})\bigr]}=\begin{bmatrix} \sqrt{2}\sigma & 0\\ 0 & \sqrt{2}\sigma \end{bmatrix}
$$

則可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbf{C}_{\sssig \mathbf{A}\boldsymbol{X}}=\mathbf{D}^{-1}\mathrm{Var}(\mathbf{A}\boldsymbol{X})\mathbf{D}^{-1}=\begin{bmatrix} 1 & \frac{1}{\,2\,}\\[0.35em] \frac{1}{\,2\,} & 1 \end{bmatrix}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbf{C}_{\sssig \mathbf{A}\boldsymbol{X}}&=\mathbf{D}^{-1}\mathrm{Var}(\mathbf{A}\boldsymbol{X})\mathbf{D}^{-1}\\[0.55em]
&=\begin{bmatrix} 1 & \frac{1}{\,2\,}\\[0.35em] \frac{1}{\,2\,} & 1 \end{bmatrix}
\end{aligned}
$$

</div>

此即

$$
\operatorname{Corr}(X_1+X_2, X_2+X_3)=\frac{1}{\,2\,}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

至此，讀者應該很自然地會在計算 $\operatorname{Cov}(X_1+X_2, X_2+X_3)$ 時，先利用線性組合的性質，將 $X_1+X_2$ 與 <span class="text-nowrap">$X_2+X_3$，</span>由 $\boldsymbol{X} = \begin{bmatrix} X_1 & X_2 & X_3 \end{bmatrix}^{\mathrm{T}}$ 與矩陣 $\mathbf{A} = \begin{bmatrix} 1 & 1 & 0\\ 0 & 1 & 1 \end{bmatrix}$ 生成出來，進而觀察非對角項，也就是共變異數。

然而，若讀者在計算矩陣時多留心，應該會發現，事實上，即使不計算整個共變異數矩陣，我們還是可以用矩陣的方式求解共變異數。

舉例如下:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\operatorname{Cov}(X_1+X_2, X_2+X_3)&=\operatorname{Cov}\Bigl(\begin{bmatrix} 1 & 1 & 0 \end{bmatrix}\boldsymbol{X},\ \begin{bmatrix} 0 & 1 & 1 \end{bmatrix}\boldsymbol{X}\Bigr)\\[0.45em]
&=\begin{bmatrix} 1 & 1 & 0 \end{bmatrix}\begin{bmatrix} \sigma^{2} & 0 & 0\\ 0 & \sigma^{2} & 0\\ 0 & 0 & \sigma^{2} \end{bmatrix}\begin{bmatrix} 0\\ 1\\ 1 \end{bmatrix}=\sigma^{2}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\operatorname{Cov}(X_1+X_2, X_2+X_3)&=\operatorname{Cov}\Bigl(\begin{bmatrix} 1 & 1 & 0 \end{bmatrix}\boldsymbol{X},\ \begin{bmatrix} 0 & 1 & 1 \end{bmatrix}\boldsymbol{X}\Bigr)\\[0.45em]
&=\begin{bmatrix} 1 & 1 & 0 \end{bmatrix}\begin{bmatrix} \sigma^{2} & 0 & 0\\ 0 & \sigma^{2} & 0\\ 0 & 0 & \sigma^{2} \end{bmatrix}\begin{bmatrix} 0\\ 1\\ 1 \end{bmatrix}=\sigma^{2}
\end{aligned}
$$

</div>

事實上，這並不是巧合，讀者如果仔細觀察將會發現，這事實上就是計算整個共變異數矩陣中的其中一個步驟而已，而且其對應的正好是非對角項，我們將其一般化的形式寫在下方:

$$
\operatorname{Cov}(\boldsymbol{a}^{\mathrm{T}}\boldsymbol{X},\ \boldsymbol{b}^{\mathrm{T}}\boldsymbol{X})=\boldsymbol{a}^{\mathrm{T}}\mathrm{Var}(\boldsymbol{X})\boldsymbol{b}
$$

這個做法提供我們一個關於[隨機向量](/teaching-topics/random-vectors-joint-pmf/#def-random-vector)的各式線性組合間的共變異數的方便算法，而且完全可以對照 $\mathrm{Var}(\boldsymbol{a}^{\mathrm{T}}\boldsymbol{X})$ 的結構，如同我們在 [Theorem 3.15](/teaching-topics/covariance/#thm-covar-proper) 中的性質 (3) 與 (4)，將共變異數與變異數對照的想法一樣。

</div>

## 本篇小結

[Theorem 3.20](#thm-var-cov-ineq) 的變異數-共變異數不等式，是把[相關係數的範圍](/teaching-topics/correlation-coefficient/#thm-corr-proper)乘回兩個[標準差](/teaching-topics/variance-standard-deviation/#def-standard-deviation)所得的結果。相關係數是共變異數除以兩個標準差之積，既然它落在 $-1$ 與 $1$ 之間，共變異數也就必定界在 $-\sigma_{\sssig X}\sigma_{\sssig Y}$ 與 $\sigma_{\sssig X}\sigma_{\sssig Y}$ 之間。[Example 3.42](#ex-correlation-bound-example) 求的是 $\mathbb{E}\bigl[\max(X^{2}, Y^{2})\bigr]$ 的上界。該題先以 $\max(a, b)$ 的絕對值表示式把最大值化為兩項[期望值](/teaching-topics/expectation/#def-expectation)之和，再對 $\mathbb{E}\bigl[\lvert (X+Y)(X-Y)\rvert\bigr]$ 這一項套用柯西不等式，即得 $1+\sqrt{1-\rho^{2}}$ 這個上界。

[Definition 3.20](#def-corr-matrix) 把共變異數矩陣改寫為相關矩陣，其中每一個元素都是兩個變數之間的相關係數。它與共變異數矩陣同為對稱矩陣，但多了兩項限制。主對角線元素必定為 <span class="text-nowrap">$1$，</span>非對角線元素則界在 $-1$ 到 $1$ 之間，因此本篇所列的三個矩陣分別因為主對角線不為 <span class="text-nowrap">$1$、</span>兩側不對稱以及元素超出範圍而不合法。相關矩陣同樣可以推廣到 $n$ 個變數；若把各個標準差排成對角矩陣 <span class="text-nowrap">$\mathbf{D}$，</span>相關矩陣即 $\mathbf{C}=\mathbf{D}^{-1}\mathbf{\Sigma}\mathbf{D}^{-1}$ 這條式子，用的是對角矩陣左乘與右乘分別讓矩陣的列與行乘上指定倍數的功能。

三道例題示範相關矩陣的計算。[Example 3.43](#ex-four-dimensional-normal-correlation) 由各個變異數與共變異數逐一算出六個相關係數，再依定義填成一個四階的相關矩陣。[Example 3.44](#ex-linear-combination-correlation) 先把旋轉寫成矩陣乘上隨機向量，求出 $\boldsymbol{Z}$ 的共變異數矩陣，再以 $\mathbf{D}^{-1}\mathbf{\Sigma}\mathbf{D}^{-1}$ 取得相關矩陣，其非對角項即 $\rho$ 這個值，最後以 $\sin^{4}\theta+\cos^{4}\theta$ $=$ $1-2\sin^{2}\theta\cos^{2}\theta$ 與 $\sin^{2}(2\theta)\leqslant 1$ 兩式把分母放大，得到 $\rho^{2}$ 的上界。[Example 3.45](#ex-uncorrelated-equal-variance) 則給出兩種做法，一種直接由共變異數與變異數代入定義，另一種先以矩陣 $\mathbf{A}$ 生成兩個線性組合，再求其相關矩陣。

本篇最後的 Note 指出，即使不計算整個共變異數矩陣，也可以用 $\boldsymbol{a}^{\mathrm{T}}\mathrm{Var}(\boldsymbol{X})\boldsymbol{b}$ 求得任意兩個線性組合之間的共變異數，它正是計算共變異數矩陣時的其中一個步驟，對應的恰好是非對角項。這個寫法可以與 $\mathrm{Var}(\boldsymbol{a}^{\mathrm{T}}\boldsymbol{X})$ 的結構互相對照，如同 [Theorem 3.15](/teaching-topics/covariance/#thm-covar-proper) 的性質 (3) 與 (4) 把共變異數與變異數對照起來一樣。

[下一篇](/teaching-topics/population-linear-regression/)將由相關係數出發，導出以一個變數預測另一個變數的母體線性迴歸式。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
