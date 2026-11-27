---
title: "雙重期望值定理"
subtitle: "The Double Expectation Theorem"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 12
order: 312
permalink: /lecture-notes/double-expectation-theorem/
date: 2026-08-13
published: true
excerpt: "將條件期望值視為條件變數 $Y$ 的函數，在 $\\mathbb{E}(X)$ 存在下對 $Y$ 再取一次期望值，即得雙重期望值定理 $\\mathbb{E}[\\mathbb{E}(X\\mid Y)]=\\mathbb{E}(X)$ 這條恆等式。本篇介紹迴歸函數的概念，證明此定理及其函數推廣形式，並說明分層加權平均的直觀意義。"
---

[上一篇](/lecture-notes/conditional-expectation-and-variance/)以 [Definition 3.11](/lecture-notes/conditional-expectation-and-variance/#def-conditional-expectation) 與 [Definition 3.13](/lecture-notes/conditional-expectation-and-variance/#def-conditional-variance) 給出[條件期望值](/lecture-notes/conditional-expectation-and-variance/#def-conditional-expectation)與[條件變異數](/lecture-notes/conditional-expectation-and-variance/#def-conditional-variance)，並在最後指出條件期望值是「給定的條件」的函數。

本篇先列出把條件當成常數所得到的三個特例，再以 [Theorem 3.8](#thm-regression-function) 為「條件期望值是條件的函數」中的那個函數取名為迴歸函數，接著討論條件本身是隨機的情形，並由此得到 [Theorem 3.9](#thm-double-expectation) 的雙重期望值定理，最後以一張立體圖說明這條定理背後的加權平均。

[上一篇](/lecture-notes/conditional-expectation-and-variance/)曾指出，一旦給定條件 $Y=y$ (或 <span class="text-nowrap">$X=x$</span>)，在該條件期望值的運算中，$Y=y$ (或 <span class="text-nowrap">$X=x$</span>) 即**被視為常數**。結合[第二章期望值](/lecture-notes/expectation/#def-expectation)與變異數的基本性質，常數的期望值即該常數本身，常數的變異數則恆為 <span class="text-nowrap">$0$，</span>由此可直接得到以下三個常用特例:

- $\mathbb{E}(X\mid X=x)$ $=$ $\mathbb{E}(x\mid X=x)$ $=$ $x\mathbb{E}(1\mid X=x)$ $=$ $x$
- $\mathrm{Var}(X\mid X=x)$ $=$ $\mathrm{Var}(x\mid X=x)$ $=$ $0$
- $\mathbb{E}(XY\mid X=x)$ $=$ $\mathbb{E}(xY\mid X=x)$ $=$ $x\mathbb{E}(Y\mid X=x)$

只要掌握「在給定 $X=x$ 下把 $X$ 當成常數」的原則，上述三式便一目了然。這類隨給定條件而變的條件期望值函數，在統計學中有專門的稱呼。

## 迴歸函數

<div id="thm-regression-function" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 3.8 (迴歸函數, regression function)</div>

條件期望值是條件的函數，即 $\mathbb{E}(X\mid Y=y)$ $=$ $g(y)$ (或 $\mathbb{E}(Y\mid X=x)$ $=$ <span class="text-nowrap">$g(x)$)，</span>我們稱其為 $X$ 對 $Y$ (或 $Y$ 對 $X$) 的迴歸函數 <span lang="en">(regression function of $X$ on $Y$ ($Y$ on $X$))</span>。

</div>

<div class="topic-proof" markdown="1">
**Proof.**

我們僅以連續型證明第一個情況，第二個情況與離散型同理可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X\mid Y=y)&=\int_{x\in\mathcal{R}_{\sssig X}}x\,f_{\sssig X\mid Y}(x\mid y)\,dx=\int_{x\in\mathcal{R}_{\sssig X}}x\frac{f_{\sssig XY}(x,y)}{f_{\sssig Y}(y)}\,dx\\[0.45em]
&=\frac{1}{f_{\sssig Y}(y)}\int_{x\in\mathcal{R}_{\sssig X}}x\,f_{\sssig XY}(x,y)\,dx=g(y)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X\mid Y=y)&=\int_{x\in\mathcal{R}_{\sssig X}}x\,f_{\sssig X\mid Y}(x\mid y)\,dx\\[0.45em]
&=\int_{x\in\mathcal{R}_{\sssig X}}x\frac{f_{\sssig XY}(x,y)}{f_{\sssig Y}(y)}\,dx\\[0.45em]
&=\frac{1}{f_{\sssig Y}(y)}\int_{x\in\mathcal{R}_{\sssig X}}x\,f_{\sssig XY}(x,y)\,dx=g(y)
\end{aligned}
$$

</div>

其中 $g(y)$ 是 $y$ 的函數。

原式得證。 <span class="topic-qed">$\square$</span>
</div>

[Theorem 3.8](#thm-regression-function) 建立了條件值 $y$ 與條件期望值之間的對應關係，每給定一個實數值 <span class="text-nowrap">$y$，</span>即可由迴歸函數 $g(y)$ 確定對應的 <span class="text-nowrap">$\mathbb{E}(X\mid Y=y)$。</span>然而在推導與應用中，我們更常看到不指定特定數值的 $\mathbb{E}(X\mid Y)$ 記法，此時最大的差異在於**條件本身是隨機的**，亦即在期望值內部運算時雖將 $Y$ 視為固定條件，但在期望值外側並未預先指定 $Y$ 落在哪一個數值。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

比較兩種記號可知，$\mathbb{E}(X\mid Y=y)=g(y)$ 代入固定實數 $y$ 後只是一個數字；而 $\mathbb{E}(X\mid Y)=g(Y)$ 則是隨 $Y$ 取值變動的**[隨機變數](/lecture-notes/random-variables-and-pmf/#def-random-variable)**。因此**當條件變數 $Y$ 被提出條件期望值外側時，$Y$ 仍然具有隨機性而須維持大寫** (例如 <span class="text-nowrap">$\mathbb{E}(XY\mid Y)=Y\,\mathbb{E}(X\mid Y)$</span>)。

</div>

## 雙重期望值定理

當條件本身為隨機時，[Theorem 3.8](#thm-regression-function) 即寫成隨機變數形式 <span class="text-nowrap">$\mathbb{E}(X\mid Y)=g(Y)$，</span>其值隨 $Y$ 的取值變化而變動。既然 $\mathbb{E}(X\mid Y)$ 是 $Y$ 的函數，自然可進一步探討它的期望值 <span class="text-nowrap">$\mathbb{E}\bigl[\mathbb{E}(X\mid Y)\bigr]$，</span>由此即得**雙重期望值定理 <span lang="en">(double expectation theorem)</span>**。

<div id="thm-double-expectation" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 3.9 (雙重期望值定理, double expectation theorem)</div>

若 $\mathbb{E}(X\mid Y)$ 為 $X$ 對 $Y$ 之條件期望值，且 $\mathbb{E}(X)$ 存在，則

$$
\mathbb{E}\bigl[\mathbb{E}(X\mid Y)\bigr]=\mathbb{E}(X)
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.**

我們以連續型證明如下，離散型同理即可

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[\mathbb{E}(X\mid Y)\bigr]&=\int_{y\in\mathcal{R}_{\sssig Y}}\mathbb{E}(X\mid Y=y)\,f_{\sssig Y}(y)\,dy\\[0.45em]
&=\int_{y\in\mathcal{R}_{\sssig Y}}\biggl[\int_{x\in\mathcal{R}_{\sssig X}}x\,f_{\sssig X\mid Y}(x\mid y)\,dx\biggr]\,f_{\sssig Y}(y)\,dy\\[0.45em]
&=\int_{y\in\mathcal{R}_{\sssig Y}}\biggl[\int_{x\in\mathcal{R}_{\sssig X}}x\,\frac{f_{\sssig XY}(x,y)}{f_{\sssig Y}(y)}\,dx\biggr]\,f_{\sssig Y}(y)\,dy\\[0.45em]
&=\int_{y\in\mathcal{R}_{\sssig Y}}\int_{x\in\mathcal{R}_{\sssig X}}x\,\frac{f_{\sssig XY}(x,y)}{f_{\sssig Y}(y)}\\[0.2em]
&\qquad\times f_{\sssig Y}(y)\,dx\,dy\\[0.45em]
&=\int_{y\in\mathcal{R}_{\sssig Y}}\int_{x\in\mathcal{R}_{\sssig X}}x\,f_{\sssig XY}(x,y)\,dx\,dy=\mathbb{E}(X)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[\mathbb{E}(X\mid Y)\bigr]&=\int_{y\in\mathcal{R}_{\sssig Y}}\mathbb{E}(X\mid Y=y)\,f_{\sssig Y}(y)\,dy\\[0.45em]
&=\int_{y\in\mathcal{R}_{\sssig Y}}\biggl[\int_{x\in\mathcal{R}_{\sssig X}}x\,f_{\sssig X\mid Y}(x\mid y)\,dx\biggr]\\[0.2em]
&\qquad\times f_{\sssig Y}(y)\,dy\\[0.45em]
&=\int_{y\in\mathcal{R}_{\sssig Y}}\biggl[\int_{x\in\mathcal{R}_{\sssig X}}x\,\frac{f_{\sssig XY}(x,y)}{f_{\sssig Y}(y)}\,dx\biggr]\\[0.2em]
&\qquad\times f_{\sssig Y}(y)\,dy\\[0.45em]
&=\int_{y\in\mathcal{R}_{\sssig Y}}\int_{x\in\mathcal{R}_{\sssig X}}x\,\frac{f_{\sssig XY}(x,y)}{f_{\sssig Y}(y)}\\[0.2em]
&\qquad\times f_{\sssig Y}(y)\,dx\,dy\\[0.45em]
&=\int_{y\in\mathcal{R}_{\sssig Y}}\int_{x\in\mathcal{R}_{\sssig X}}x\,f_{\sssig XY}(x,y)\,dx\,dy\\[0.45em]
&=\mathbb{E}(X)
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

在 $\mathbb{E}\bigl[g(X)\bigr]$ 存在的條件下，[雙重期望值定理](#thm-double-expectation)可推廣至 $X$ 的函數條件期望值形式

$$
\mathbb{E}\Bigl(\mathbb{E}\bigl[g(X)\mid Y\bigr]\Bigr)=\mathbb{E}\bigl[g(X)\bigr]
$$

例如計算二階動差時常用的特例為

$$
\mathbb{E}\Bigl[\mathbb{E}\bigl(X^{2}\mid Y\bigr)\Bigr]=\mathbb{E}\bigl(X^{2}\bigr)
$$

</div>

[雙重期望值定理](#thm-double-expectation)指出，將條件期望值 $\mathbb{E}(X\mid Y)=g(Y)$ 對 $Y$ 再取一次期望值，**結果恰等於 $X$ 的邊際期望值**。這項性質背後的直觀意義即是「加權平均」。計算隨機變數函數 $g(Y)$ 的期望值時，是以邊際密度 $f\_{\sssig Y}(y)$ 為權重對 $g(y)$ 加權積分；因此對 $\mathbb{E}(X\mid Y)$ 取外層期望值時，同樣須乘上 $Y$ 的機率函數 <span class="text-nowrap">$f\_{\sssig Y}(y)$，</span>如上列證明第一步所示。此一加權機制可圖解如下:

<figure id="fig-regression-function-surface" class="topic-figure topic-figure--wide">
  <img src="/images/lecture-notes/regression-function-surface.svg" alt="一個三維曲面圖。曲面在中央隆起成鐘形，四周向外遞減趨近於零，底面兩軸分別標 x 與 y，鉛直軸標聯合機率密度函數的函數值。y 軸上依序標出 y_1、y_2 與 y_n 三個位置，每一處各有一片沿 x 方向的截面立在曲面上，截面的輪廓以深色曲線描出，其下以淡紅色填滿。三片截面的高低不同，位在 y_2 的那一片最高，位在 y_1 的那一片最矮。">
  <figcaption><span class="topic-figure__label">Fig. 3.16.</span> joint pdf 的曲面沿 $y$ 切成薄片，圖中在 <span class="text-nowrap">$y_1$、</span>$y_2$ 與 $y_n$ 三處各切出一片，每一片的形狀就是 $X$ 給定 $Y=y$ 的條件分配，其重心即 <span class="text-nowrap">$\mathbb{E}(X\mid Y=y)$。</span>三片的高低不同，正是加權平均中各片權重不同的來源。</figcaption>
</figure>

如 [Fig. 3.16](#fig-regression-function-surface) 所示，整個原始空間可先依給定不同的 $Y=y$ 切割成一片片薄切片，每個薄片標準化後各自形成條件分配 <span class="text-nowrap">$f\_{\sssig X\mid Y}(x\mid y)$。</span>我們先在各個條件分配切片上找出 $X$ 的局部重心 <span class="text-nowrap">$\mathbb{E}(X\mid Y=y)$，</span>再依各切片發生的相對可能性 $f\_{\sssig Y}(y)$ 為權重對這些局部重心作加權平均，最終合成的整體重心即為原始空間中 $X$ 的邊際期望值 <span class="text-nowrap">$\mathbb{E}(X)$。</span>

一般二元分配的迴歸函數隨條件變化的軌跡未必為直線，也不必貼著聯合密度曲面的山脊行進。讀者可對照互動展示 [One-Way Linear Regression and Hyperbolic-Tangent S-Curves](/demos/asymmetric-regression-mixture/) 與 [Nonlinear Regression and Valley Centroids on a Bifurcating Ridge](/demos/bimodal-fork-regression/)，前者呈現一個方向的迴歸函數為直線、反方向卻經[貝氏定理](/lecture-notes/bayes-rule-posterior-probability/#theorem-bayes-rule)加權而彎曲成雙曲正切曲線的情形，後者則展示曲面山脊分岔為雙峰時，各切片重心 $\mathbb{E}(Y\mid X=x)$ 落在雙峰之間的低谷，而以邊際密度加權平均後仍回到邊際期望值 <span class="text-nowrap">$\mathbb{E}(Y)$。</span>

## 本篇小結

把條件當成常數，馬上可以得到三個有用的特例。其中 $\mathbb{E}(X\mid X=x)$ $=$ $x$ 與 $\mathrm{Var}(X\mid X=x)$ $=$ $0$ 這兩條，說的是給定之後 $X$ 已經沒有隨機性；$\mathbb{E}(XY\mid X=x)$ $=$ $x\mathbb{E}(Y\mid X=x)$ 這一條，說的是給定的那個值可以像常數一樣提到期望值的外面。[Theorem 3.8](#thm-regression-function) 則為這個函數取了名字。條件期望值是條件的函數，即 $\mathbb{E}(X\mid Y=y)$ $=$ <span class="text-nowrap">$g(y)$，</span>我們稱其為 $X$ 對 $Y$ 的迴歸函數。證明只用到[條件機率密度函數](/lecture-notes/conditional-distributions/#def-conditional-pdf)的定義，把 $f_{\sssig Y}(y)$ 提到積分之外，剩下的積分便只與 $y$ 有關。

若把條件本身看成隨機的，$\mathbb{E}(X\mid Y)$ $=$ $g(Y)$ 就是 $Y$ 的函數，也是一個隨機變數，因此還可以再取一次期望值。[Theorem 3.9](#thm-double-expectation) 的雙重期望值定理指出，這一次期望值恰好等於 $X$ 的邊際期望值，即 $\mathbb{E}\bigl[\mathbb{E}(X\mid Y)\bigr]$ $=$ <span class="text-nowrap">$\mathbb{E}(X)$。</span>證明的關鍵一步是把 $\mathbb{E}(X\mid Y=y)$ 乘上 $f_{\sssig Y}(y)$ 之後，$f_{\sssig X\mid Y}(x\mid y)$ 分母上的 $f_{\sssig Y}(y)$ 恰好被消掉，只剩下 $X$ 與 $Y$ 的[聯合機率密度函數](/lecture-notes/joint-probability-density-functions/#def-joint-pdf)。這條定理另有 $g(X)$ 的版本，其中 $\mathbb{E}\bigl[\mathbb{E}(X^{2}\mid Y)\bigr]$ $=$ $\mathbb{E}(X^{2})$ 這個特例後續會經常用到。

這條定理背後的直觀就是加權平均。本篇的立體圖把整個原始空間依 $Y$ 的取值切成不同的薄片，每一片都是 $X$ 給定 $Y=y$ 的條件分配；先在每一片上找到重心 $\mathbb{E}(X\mid Y=y)$ 這個值，再以該片自己發生的可能性 $f_{\sssig Y}(y)$ 為權重把這些重心平均起來，所得的就是原始空間中 $X$ 的重心 $\mathbb{E}(X)$ 這個值。乘上 $f_{\sssig Y}(y)$ 這一步之所以是關鍵，正是因為它同時扮演了定義所要求的機率函數與加權平均所要求的權重。

[下一篇](/lecture-notes/double-expectation-examples/)以五道例題示範這條定理怎麼用，其中包含期望值不存在時等式不成立的例子，以及讓所求的期望值在等式兩側同時出現、解一條方程式即可求得的作法。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
