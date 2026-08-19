---
title: "聯合累積分配函數"
subtitle: "Joint Cumulative Distribution Functions"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 2
order: 302
permalink: /teaching-topics/joint-cumulative-distribution-functions/
date: 2026-08-12
published: false
excerpt: "二元隨機向量的聯合累積分配函數定義為 $F_{\\sssig XY}(x,y)=\\mathbb{P}(X\\leqslant x,Y\\leqslant y)$ 這個機率，定義域是二維實數平面，函數值落在 $[0,1]$ 之中。它所取的機率，來自使 $X(\\omega)\\leqslant x$ 且 $Y(\\omega)\\leqslant y$ 的那些樣本點所構成的集合，故處理聯合 cdf 時最要緊的事情就是弄清楚目前的加總或積分範圍。二元離散型的情形以雙重加總寫出，把橫向不超過 $x$ 且縱向不超過 $y$ 的各個質點機率相加即可。本篇並以機率列聯表示範指定位置上的 cdf 值如何求得。"
---

[上一篇](/teaching-topics/random-vectors-joint-pmf/)由[隨機向量](/teaching-topics/random-vectors-joint-pmf/#def-random-vector)的定義出發，介紹了二元離散型隨機向量的[聯合機率質量函數](/teaching-topics/random-vectors-joint-pmf/#def-joint-pmf)與[邊際機率質量函數](/teaching-topics/random-vectors-joint-pmf/#def-marginal-pmf)。聯合機率質量函數只定義在離散型的隨機向量上，而第二章的[累積分配函數](/teaching-topics/cumulative-distribution-functions/#def-cdf)則是由 $\mathbb{P}(X\leqslant x)$ 出發，離散型與連續型都適用。

二元的情形同樣可以這樣做。[Definition 3.1](/teaching-topics/random-vectors-joint-pmf/#def-random-vector) 要求對任意實數 $x_1,x_2,\ldots,x_n$ 而言，能使 $X_i(\omega)\leqslant x_i$ 對每一個 $i$ 都成立的那些樣本點所構成的集合是事件，故在 $n=2$ 的情況中，$\mathbb{P}(X\leqslant x,Y\leqslant y)$ 這個機率對平面上每一個點 $(x,y)$ 都有定義。把 $(x,y)$ 看成變數，這個機率本身就是一個定義在二維實數平面上的函數。

<div id="def-joint-cdf" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 3.4 (聯合累積分配函數, joint cdf)</div>

若 $(X,Y)$ 為一二元隨機向量，且定義函數

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig XY}(x,y)=\mathbb{P}(X\leqslant x,Y\leqslant y),\ \forall (x,y)\in\mathbb{R}^{2}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig XY}(x,y)&=\mathbb{P}(X\leqslant x,Y\leqslant y),\\[0.45em]
&\forall (x,y)\in\mathbb{R}^{2}
\end{aligned}
$$

</div>

我們稱 $F_{\sssig XY}(x,y)$ 為 $(X,Y)$ 的**聯合累積分配函數 <span lang="en">(joint cumulative distribution function, joint cdf)</span>** 或簡稱為**聯合分配函數 (joint df)**。

</div>

聯合累積分配函數有一些地方需要注意:

(1) **聯合累積分配函數** $F_{\sssig XY}(x,y)$ 是一種定義在二維實數平面 $\mathbb{R}^{2}$ 上的函數，且將其對應到 $[0,1]$ 區間中的函數，可以記為
{: .topic-paren-item}

$$
F\colon\mathbb{R}^{2}\to[0,1]
$$

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

當然，在更高維度的狀況中，$F_{\sssig \boldsymbol{X}}(\boldsymbol{x})$ 的定義域將是高維實數空間 <span class="text-nowrap">$\mathbb{R}^{n}$。</span>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

cdf 的定義可搭配隨機向量的定義寫為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig XY}(x,y)=\mathbb{P}(X\leqslant x,Y\leqslant y)=\mathbb{P}\bigl(\lbrace\,\omega\mid X(\omega)\leqslant x,Y(\omega)\leqslant y\,\rbrace\bigr),\ x,y\in\mathbb{R}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig XY}(x,y)&=\mathbb{P}(X\leqslant x,Y\leqslant y)\\[0.45em]
&=\mathbb{P}\bigl(\lbrace\,\omega\mid X(\omega)\leqslant x,\\[0.2em]
&\qquad Y(\omega)\leqslant y\,\rbrace\bigr),\ x,y\in\mathbb{R}
\end{aligned}
$$

</div>

也就是對使得 $X(\omega)\leqslant x$ 且 $Y(\omega)\leqslant y$ 的 $\omega$ 所構成的集合取機率，其範圍如下圖所示:

<figure id="fig-joint-cdf-quadrants" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/joint-cdf-quadrants.svg" alt="以點 (x, y) 為分割點，一條縱線與一條橫線把平面切成四塊。左下一塊標示 X 小於等於 x 且 Y 小於等於 y，以淡紅色填滿，即聯合累積分配函數所取的範圍；右下標示 X 大於 x 且 Y 小於等於 y；左上標示 X 小於等於 x 且 Y 大於 y；右上標示 X 大於 x 且 Y 大於 y。橫軸右端標 X，縱軸上端標 Y，縱線下端標 X 等於 x，橫線左端標 Y 等於 y，交點畫一個實心圓點。">
  <figcaption><span class="topic-figure__label">Fig. 3.1.</span> 兩條分界線 $X=x$ 與 $Y=y$ 把平面切成四塊，左下角填色的一塊即 $F_{\sssig XY}(x,y)$ 所取的範圍。</figcaption>
</figure>

事實上，這也是在處理 joint cdf 時，最重要的事情，也就是**弄清楚目前的積分 (或加總) 範圍**。

</div>

(2) 以二元離散型的例子而言，joint cdf 即為
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig XY}(x,y)=\mathbb{P}(X\leqslant x,Y\leqslant y)=\sum_{t\leqslant x}\sum_{s\leqslant y}p_{\sssig XY}(t,s),\ \forall (x,y)\in\mathbb{R}^{2}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig XY}(x,y)&=\mathbb{P}(X\leqslant x,Y\leqslant y)\\[0.45em]
&=\sum_{t\leqslant x}\sum_{s\leqslant y}p_{\sssig XY}(t,s),\\[0.2em]
&\qquad\forall (x,y)\in\mathbb{R}^{2}
\end{aligned}
$$

</div>

讀者或許已經發現，上列這些性質，事實上與單變數 cdf 相去不遠，很多部分甚至一樣，則我們是不是能夠用與單變數時相同的手法，從而定義二元連續型[隨機變數](/teaching-topics/random-variables-and-pmf/#def-random-variable)的**[聯合機率密度函數](/teaching-topics/joint-probability-density-functions/#def-joint-pdf) (joint pdf)** 呢？

這個答案當然是肯定的，我們稍後便會看到這樣的定義，但在此之前我們先來看一些 joint cdf 的例子。

<div id="ex-joint-pmf-constant-cdf" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.1 <span lang="en">(Continued)</span></div>

<div lang="en" markdown="1">
Suppose that the joint pmf of a two-dimensional discrete random vector $(X,Y)$ is

$$
p_{\sssig XY}(x,y)=\frac{\,x+2y\,}{12},\quad (x,y)\in\lbrace(0,1),(0,2),(1,0),(1,1),(2,0)\rbrace
$$

<ol class="topic-list-paren topic-list-paren--start-4">
  <li>Suppose that $F_{\sssig XY}(x,y)$ is the joint cdf of <span class="text-nowrap">$(X,Y)$.</span> Evaluate $F_{\sssig XY}(1,1)$ and <span class="text-nowrap">$F_{\sssig XY}(1.5,0.3)$.</span></li>
</ol>
</div>

(4) 由 joint cdf 的[定義](#def-joint-cdf)可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
F_{\sssig XY}(1,1)&=\mathbb{P}(X\leqslant 1,Y\leqslant 1)=p_{\sssig XY}(0,1)+p_{\sssig XY}(1,0)+p_{\sssig XY}(1,1)\\[0.45em]
&=\frac{2}{\,12\,}+\frac{1}{\,12\,}+\frac{3}{\,12\,}=\frac{1}{2}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig XY}(1,1)&=\mathbb{P}(X\leqslant 1,Y\leqslant 1)\\[0.45em]
&=p_{\sssig XY}(0,1)+p_{\sssig XY}(1,0)\\[0.2em]
&\qquad +p_{\sssig XY}(1,1)\\[0.45em]
&=\frac{2}{\,12\,}+\frac{1}{\,12\,}+\frac{3}{\,12\,}=\frac{1}{2}
\end{aligned}
$$

</div>

同樣由 joint cdf 的定義可得
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig XY}(1.5,0.3)=\mathbb{P}(X\leqslant 1.5,Y\leqslant 0.3)=\mathbb{P}(X\leqslant 1,Y\leqslant 0)=p_{\sssig XY}(1,0)=\frac{1}{\,12\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig XY}(1.5,0.3)&=\mathbb{P}(X\leqslant 1.5,Y\leqslant 0.3)\\[0.45em]
&=\mathbb{P}(X\leqslant 1,Y\leqslant 0)\\[0.45em]
&=p_{\sssig XY}(1,0)=\frac{1}{\,12\,}
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

讀者會發現，依照 joint cdf 的定義，如果僅是想要求取指定位置上的 cdf 值時，原問題都將被轉換回**求取一個範圍上的聯合機率**，事實上並不困難。

另外，在二維的情況下，求取 cdf 的機率可以機率列聯表搭配 [Fig. 3.1](#fig-joint-cdf-quadrants) 中的 cdf 範圍示意圖完成，以前述小題的 $F_{\sssig XY}(1,1)$ 為例，此即求取 $X\leqslant 1$ 且 $Y\leqslant 1$ 之範圍內的機率總和，故透過將列聯表進行二維座標的對應，我們有以下的圖例:

<table class="topic-table--matrix">
  <thead>
    <tr>
      <th style="text-align: center;">$Y\backslash X$</th>
      <th style="text-align: center;">$0$</th>
      <th style="text-align: center;">$1$</th>
      <th style="text-align: center;">$2$</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align: center;">$2$</td>
      <td style="text-align: center;">$4/12$</td>
      <td style="text-align: center;">$0$</td>
      <td style="text-align: center;">$0$</td>
    </tr>
    <tr>
      <td style="text-align: center;">$1$</td>
      <td style="text-align: center; background: var(--journal-accent-soft);">$2/12$</td>
      <td style="text-align: center; background: var(--journal-accent-soft);">$3/12$</td>
      <td style="text-align: center;">$0$</td>
    </tr>
    <tr>
      <td style="text-align: center;">$0$</td>
      <td style="text-align: center; background: var(--journal-accent-soft);">$0$</td>
      <td style="text-align: center; background: var(--journal-accent-soft);">$1/12$</td>
      <td style="text-align: center;">$2/12$</td>
    </tr>
  </tbody>
</table>

這種半圖示的計算方式，在二維離散變數的值域相對簡單時，是一個好用的解題技巧之一；但讀者也不妨也藉此思考及理解 joint cdf 的定義，與其本質究竟為何。

</div>

## 本篇小結

[Definition 3.4](#def-joint-cdf) 把累積分配函數推廣到二元的情形，定義為 $F_{\sssig XY}(x,y)=\mathbb{P}(X\leqslant x,Y\leqslant y)$ 這個機率，定義域是二維實數平面，函數值落在 $[0,1]$ 之中。它所取的是使 $X(\omega)\leqslant x$ 且 $Y(\omega)\leqslant y$ 的那些樣本點所構成的集合之機率，[Fig. 3.1](#fig-joint-cdf-quadrants) 把這個範圍畫在平面上；處理 joint cdf 時最重要的事情，就是弄清楚目前的積分或加總範圍。

二元離散型的 joint cdf 以雙重加總寫出，把橫向不超過 $x$ 且縱向不超過 $y$ 的各個質點機率相加即可。[Example 3.1 <span lang="en">(Continued)</span>](#ex-joint-pmf-constant-cdf) 依此求得 $F_{\sssig XY}(1,1)=\frac{1}{2}$ 與 $F_{\sssig XY}(1.5,0.3)=\frac{1}{12}$ 兩個值，其中後者示範了指定位置不是質點時，cdf 值如何退回到兩個座標都不超過該位置的質點；把聯合 pmf 排成機率列聯表，再對應到二維座標，同一個總和也可以半圖示的方式求得。

這些性質與單變數的 cdf 相去不遠，故我們也能用與單變數時相同的手法，定義二元連續型隨機變數的聯合機率密度函數。[下一篇](/teaching-topics/joint-probability-density-functions/)便由聯合機率密度函數的定義開始，並說明它與聯合累積分配函數之間的關係。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Morris H. DeGroot and Mark J. Schervish. 2012. *Probability and Statistics*. 4th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
