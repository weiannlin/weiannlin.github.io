---
title: "聯合密度的區域機率"
subtitle: "Region Probabilities from a Joint Density"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 5
order: 305
permalink: /teaching-topics/region-probabilities-joint-density/
date: 2026-08-12
published: false
excerpt: "本篇以三道例題說明，聯合機率密度函數已知時，一個事件的機率如何由該事件所在區域上的重積分求得。第一道題的聯合值域是 $y>x>0$ 的楔形，示範邊際密度如何由聯合密度對另一個變數積分而得；接著把前三道例題的聯合值域放在一起比較，並以九宮格與非積空間的兩張分區圖說明聯合累積分配函數為何必須分段。第二道題的兩個變數獨立且各服從 $\\mathcal{N}(0,1)$，所求範圍是單位圓盤與半平面，改用極座標之後兩個積分都可以直接算出。第三道題的三個變數獨立且各服從 $\\mathcal{U}(0,1)$，所求範圍由大小順序決定，除了逐層積分之外，也可以直接取該範圍在值域中的佔比。"
---

[上一篇](/teaching-topics/marginal-probability-density-functions/)把[聯合機率密度函數](/teaching-topics/joint-probability-density-functions/#def-joint-pdf)對其中一個變數積分，給出[邊際機率密度函數](/teaching-topics/marginal-probability-density-functions/#def-marginal-pdf)的定義，並以兩道例題示範常數、邊際 pdf 與 joint cdf 的求法。本篇先接著看第三道同型的例題，再把三道例題放在一起，比較它們的聯合值域各自有什麼特色。

三道例題的差別，全在於聯合值域是不是一個積空間。是積空間的那一題，joint cdf 的積分範圍可以用九宮格把整個平面完全切開；不是積空間的那兩題，分段的方式就要依值域的邊界決定。本篇各取一題畫成分區圖，說明 joint cdf 為何必須分段給出。

本篇最後的兩道例題，把注意力由聯合值域轉到所求的事件本身。兩題的聯合值域都很單純，一個是整個平面，一個是單位正方形與單位立方體，但所求的範圍分別是圓盤、半平面與由大小順序所決定的區域，都不是矩形。處理的辦法都一樣，先把機率寫成該範圍上的重積分，再換一個較容易計算的座標系，或者直接取該範圍在值域中的佔比。

<div id="ex-joint-pdf-exponential-region" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.4</div>

<div lang="en" markdown="1">
Suppose that the random variables $X$ and $Y$ have the joint pdf given by

$$
f_{\sssig XY}(x,y)=
\left\lbrace
\begin{array}{c@{\quad}l}
e^{-y}, & y>x>0\\[0.4em]
0, & \text{o.w.}
\end{array}
\right.
$$

<ol class="topic-list-paren">
  <li>Determine the marginal pdf of <span class="text-nowrap">$X$.</span></li>
</ol>
</div>

(1) 本題所敘述的值域範圍如下圖所示
{: .topic-paren-item}

<figure id="fig-exponential-range-integration" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/exponential-range-integration.svg" alt="第一象限中有一條由原點出發、往右上方延伸的斜線，斜線的右上端標 x 等於 y。斜線與縱軸之間的區域以淡紅色填滿，這一塊往右上方持續延伸。橫軸右端標 x，縱軸上端標 y，兩軸都帶箭頭，圖上沒有畫刻度，也沒有標任何數值。">
  <figcaption><span class="topic-figure__label">Fig. 3.5.</span> 填色的一塊是聯合值域，左界是縱軸，下界是直線 <span class="text-nowrap">$x=y$，</span>因此 $y$ 恆大於 <span class="text-nowrap">$x$。</span></figcaption>
</figure>

故由 [marginal pdf 之定義](/teaching-topics/marginal-probability-density-functions/#def-marginal-pdf)可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X}(x)=\int_{x}^{\infty}e^{-y}\,dy=\Bigl[-e^{-y}\Bigr]_{x}^{\infty}=e^{-x},\quad x>0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig X}(x)&=\int_{x}^{\infty}e^{-y}\,dy=\Bigl[-e^{-y}\Bigr]_{x}^{\infty}\\[0.45em]
&=e^{-x},\quad x>0
\end{aligned}
$$

</div>

由此可得
{: .topic-paren-cont}

$$
f_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
e^{-x}, & x>0\\[0.4em]
0, & \text{o.w.}
\end{array}
\right.
$$

</div>

[Example 3.2](/teaching-topics/marginal-probability-density-functions/#ex-joint-pdf-region-basic) 到 [Example 3.4](#ex-joint-pdf-exponential-region) 各自有幾個小細節。在 [Example 3.2](/teaching-topics/marginal-probability-density-functions/#ex-joint-pdf-region-basic) 中，我們從結果回頭看題目，可以發現該題的 joint pdf，事實上是兩個 marginal pdf 的乘積，且其範圍是由兩個 marginal pdf 各自的範圍，所共同形成的積空間。

這個狀況在稍後的小節中會談到，只要上列二個條件被滿足，則代表這兩個變數彼此是**[獨立隨機變數](/teaching-topics/independent-random-variables/#def-indep-r-v) <span lang="en">(independent random variables)</span>**，而 [Example 3.3](/teaching-topics/marginal-probability-density-functions/#ex-joint-pdf-triangle-region) 與 [Example 3.4](#ex-joint-pdf-exponential-region) 則顯然不獨立。

[Example 3.4](#ex-joint-pdf-exponential-region) 與 [Example 3.3](/teaching-topics/marginal-probability-density-functions/#ex-joint-pdf-triangle-region) 的情況相似，其聯合值域都不是積空間，但 [Example 3.4](#ex-joint-pdf-exponential-region) 的 joint pdf 除了值域範圍之外，並沒有任何的 $x$ 存在，這種情況是有可能發生的，而且其仍然是 $X$ 與 $Y$ 的 joint pdf，而不只是 $Y$ 自己的 marginal pdf，是比較需要特別注意的地方。

而在 [Example 3.2](/teaching-topics/marginal-probability-density-functions/#ex-joint-pdf-region-basic) 與 [Example 3.3](/teaching-topics/marginal-probability-density-functions/#ex-joint-pdf-triangle-region) 中，計算 joint cdf 時，我們更是需要注意目前的積分範圍，因為 **joint cdf 是一個定義在 $\mathbb{R}^{2}$ 空間上的函數，故任何一個 $\mathbb{R}^{2}$ 空間上的點，都需要有對應的函數值**；但是，$\mathbb{R}^{2}$ 空間上的點 $(x,y)$ 在不同範圍的時候，joint cdf 所給的函數值，其形式會長得不太一樣，故讀者應特別注意。

這裡用 [Example 3.2](/teaching-topics/marginal-probability-density-functions/#ex-joint-pdf-region-basic) 為例子，因為其聯合值域是一個二維的積空間，故可以用九宮格的形式完全將其切開，並且進行分類。下面便將其積分範圍轉為圖示:

<figure id="fig-product-space-nine-regions" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/product-space-nine-regions.svg" alt="平面上有一個正方形以淡紅色填滿，即聯合值域。一條縱線沿著正方形的右邊往上延伸，下端標 x 等於 1；一條橫線沿著正方形的上邊往右延伸，左端標 y 等於 1，兩線與兩軸把平面分成九格。正方形之內、正方形右側、正方形上方與圖的右上角各標一個二重積分式，右上角那一個等於 1。左側一行三處與下方一列兩處，共五個位置標 0。橫軸右端標 x，縱軸上端標 y。">
  <figcaption><span class="topic-figure__label">Fig. 3.6.</span> 縱線 $x=1$ 與橫線 $y=1$ 把平面切成九塊，填色的正方形就是聯合值域，每一塊所標的二重積分就是該處的 joint <span class="text-nowrap">cdf，</span>$x<0$ 與 $y<0$ 之處取值皆為 <span class="text-nowrap">$0$。</span></figcaption>
</figure>

這樣區分積分的範圍是有原因的，在 [Fig. 3.1](/teaching-topics/joint-cumulative-distribution-functions/#fig-joint-cdf-quadrants) 我們曾經提過，joint cdf 所指示的積分範圍，是 **$(x,y)$ 的左下方所涵蓋之部分的機率**，故我們應該釐清**目前的 $(x,y)$ 所在的位置為何**，才能夠看出該點的左下角所包含之**有機率的部分**在哪裡。

而 [Example 3.3](/teaching-topics/marginal-probability-density-functions/#ex-joint-pdf-triangle-region) 的情況則稍微複雜一些，如下圖:

<figure id="fig-non-product-space-regions" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/non-product-space-regions.svg" alt="平面上有一個由原點、(1, 1) 與 (0, 1) 三點圍成的三角形，以淡紅色填滿，即聯合值域。一條斜線由原點畫到三角形右上角的頂點；一條橫線由該頂點往右延伸，左端標 y 等於 1；一條縱線由該頂點往上延伸，橫軸下方另有一小段縱線標 x 等於 1。三角形之內、三角形上方、斜線右下方與圖的右上角各標一個二重積分式，右上角那一個等於 1。左側一行三處與下方一列兩處，共五個位置標 0。橫軸右端標 x，縱軸上端標 y。">
  <figcaption><span class="topic-figure__label">Fig. 3.7.</span> 填色的三角形是聯合值域，斜線 <span class="text-nowrap">$x=y$、</span>橫線 $y=1$ 與縱線 $x=1$ 把第一象限分成四塊，每一塊所標的二重積分就是該處的 joint <span class="text-nowrap">cdf，</span>$x<0$ 與 $y<0$ 之處取值皆為 <span class="text-nowrap">$0$。</span></figcaption>
</figure>

上述積分範圍的圖示事實上所對應的就是 **joint cdf 中的範圍**，也正是因為**在這些不同範圍中所包含之有機率的部分不同，其積分式的形式也不同**，才有必要分段，是讀者在操作 joint cdf 時需要特別小心的部分。

<div id="ex-independent-normal-region" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.5</div>

<div lang="en" markdown="1">
Suppose that $X$ and $Y$ are independent random variables, both of which have the normal density <span class="text-nowrap">$\mathcal{N}(0,1)$,</span> that is,

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
X,Y\overset{\mathrm{iid}}{\sim}f_{\sssig X}(x)=\frac{1}{\,\sqrt{2\pi}\,}e^{\frac{\,-x^{2}\,}{2}},\quad -\infty<x<\infty
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
X,Y\overset{\mathrm{iid}}{\sim}f_{\sssig X}(x)&=\frac{1}{\,\sqrt{2\pi}\,}e^{\frac{\,-x^{2}\,}{2}},\\[0.45em]
&\qquad-\infty<x<\infty
\end{aligned}
$$

</div>

<ol class="topic-list-paren">
  <li>What is the probability that <span class="text-nowrap">$X^{2}+Y^{2}\leqslant 1$?</span></li>
  <li>What is the probability that <span class="text-nowrap">$X\geqslant Y$?</span></li>
</ol>
</div>

(1) 由於
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
X,Y\overset{\mathrm{iid}}{\sim}f_{\sssig X}(x)=\frac{1}{\,\sqrt{2\pi}\,}e^{\frac{\,-x^{2}\,}{2}},\quad -\infty<x<\infty
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
X,Y\overset{\mathrm{iid}}{\sim}f_{\sssig X}(x)&=\frac{1}{\,\sqrt{2\pi}\,}e^{\frac{\,-x^{2}\,}{2}},\\[0.45em]
&\qquad-\infty<x<\infty
\end{aligned}
$$

</div>

故知道
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig XY}(x,y)=f_{\sssig X}(x)\,f_{\sssig Y}(y)=\frac{1}{\,2\pi\,}e^{\frac{\,-(x^{2}+y^{2})\,}{2}},\quad x,y\in\mathbb{R}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig XY}(x,y)&=f_{\sssig X}(x)\,f_{\sssig Y}(y)\\[0.45em]
&=\frac{1}{\,2\pi\,}e^{\frac{\,-(x^{2}+y^{2})\,}{2}},\quad x,y\in\mathbb{R}
\end{aligned}
$$

</div>

若令 <span class="text-nowrap">$A=\lbrace\,(x,y)\mid x^{2}+y^{2}\leqslant 1\,\rbrace$，</span>則有
{: .topic-paren-cont}

$$
\mathbb{P}(X^{2}+Y^{2}\leqslant 1)=\iint_{A}f_{\sssig XY}(x,y)\,dx\,dy
$$

又依照極座標轉換 <span lang="en">(polar coordinates transformation)</span>，可令
{: .topic-paren-cont}

$$
\left\lbrace
\begin{array}{l}
x=r\,\cos\theta\\[0.35em]
y=r\,\sin\theta
\end{array}
\right.
$$

則有
{: .topic-paren-cont}

$$
\mathbf{J}=
\left\lvert
\begin{array}{cc}
\dfrac{dx}{dr} & \dfrac{dx}{d\theta}\\[0.8em]
\dfrac{dy}{dr} & \dfrac{dy}{d\theta}
\end{array}
\right\rvert=r
$$

可將 $A$ 以 $(r,\theta)$ 表示為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
A=\lbrace\,(x,y)\mid x^{2}+y^{2}\leqslant 1\,\rbrace=\lbrace\,(r,\theta)\mid 0\leqslant r\leqslant 1,\ 0\leqslant\theta\leqslant 2\pi\,\rbrace
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
A&=\lbrace\,(x,y)\mid x^{2}+y^{2}\leqslant 1\,\rbrace\\[0.45em]
&=\lbrace\,(r,\theta)\mid 0\leqslant r\leqslant 1,\\[0.2em]
&\qquad\quad 0\leqslant\theta\leqslant 2\pi\,\rbrace
\end{aligned}
$$

</div>

故我們有
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X^{2}+Y^{2}\leqslant 1)&=\iint_{A}f_{\sssig XY}(x,y)\,dx\,dy=\int_{0}^{2\pi}\!\!\int_{0}^{1}\frac{1}{\,2\pi\,}e^{\frac{\,-r^{2}\,}{2}}\,r\,dr\,d\theta\\[0.45em]
&=\frac{1}{\,2\pi\,}\left(\int_{0}^{2\pi}d\theta\right)\left(\int_{0}^{1}e^{\frac{\,-r^{2}\,}{2}}\,d\frac{\,r^{2}\,}{2}\right)=1-e^{\frac{\,-1\,}{2}}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X^{2}+Y^{2}\leqslant 1)&=\iint_{A}f_{\sssig XY}(x,y)\,dx\,dy\\[0.45em]
&=\int_{0}^{2\pi}\!\!\int_{0}^{1}\frac{1}{\,2\pi\,}e^{\frac{\,-r^{2}\,}{2}}\,r\,dr\,d\theta\\[0.45em]
&=\frac{1}{\,2\pi\,}\left(\int_{0}^{2\pi}d\theta\right)\left(\int_{0}^{1}e^{\frac{\,-r^{2}\,}{2}}\,d\frac{\,r^{2}\,}{2}\right)\\[0.45em]
&=1-e^{\frac{\,-1\,}{2}}
\end{aligned}
$$

</div>

(2) 令 <span class="text-nowrap">$B=\lbrace\,(x,y)\mid x\geqslant y\,\rbrace$，</span>則有
{: .topic-paren-item}

$$
\mathbb{P}(X\geqslant Y)=\iint_{B}f_{\sssig XY}(x,y)\,dx\,dy
$$

又依照極座標轉換，可令
{: .topic-paren-cont}

$$
\left\lbrace
\begin{array}{l}
x=r\,\cos\theta\\[0.35em]
y=r\,\sin\theta
\end{array}
\right.
$$

則有
{: .topic-paren-cont}

$$
\mathbf{J}=
\left\lvert
\begin{array}{cc}
\dfrac{dx}{dr} & \dfrac{dx}{d\theta}\\[0.8em]
\dfrac{dy}{dr} & \dfrac{dy}{d\theta}
\end{array}
\right\rvert=r
$$

可將 $B$ 以 $(r,\theta)$ 表示為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
B=\lbrace\,(x,y)\mid x\geqslant y\,\rbrace=\lbrace\,(r,\theta)\mid 0\leqslant r\leqslant\infty,\ -\tfrac{3}{4}\pi\leqslant\theta\leqslant\tfrac{1}{4}\pi\,\rbrace
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
B&=\lbrace\,(x,y)\mid x\geqslant y\,\rbrace\\[0.45em]
&=\lbrace\,(r,\theta)\mid 0\leqslant r\leqslant\infty,\\[0.2em]
&\qquad\quad -\tfrac{3}{4}\pi\leqslant\theta\leqslant\tfrac{1}{4}\pi\,\rbrace
\end{aligned}
$$

</div>

故我們有
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X\geqslant Y)&=\iint_{B}f_{\sssig XY}(x,y)\,dx\,dy=\int_{-\frac{3}{4}\pi}^{\frac{1}{4}\pi}\!\!\int_{0}^{\infty}\frac{1}{\,2\pi\,}e^{\frac{\,-r^{2}\,}{2}}\,r\,dr\,d\theta\\[0.45em]
&=\frac{1}{\,2\pi\,}\left(\int_{-\frac{3}{4}\pi}^{\frac{1}{4}\pi}d\theta\right)\left(\int_{0}^{\infty}e^{\frac{\,-r^{2}\,}{2}}\,d\frac{\,r^{2}\,}{2}\right)=\frac{1}{\,2\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X\geqslant Y)&=\iint_{B}f_{\sssig XY}(x,y)\,dx\,dy\\[0.45em]
&=\int_{-\frac{3}{4}\pi}^{\frac{1}{4}\pi}\!\!\int_{0}^{\infty}\frac{1}{\,2\pi\,}e^{\frac{\,-r^{2}\,}{2}}\,r\,dr\,d\theta\\[0.45em]
&=\frac{1}{\,2\pi\,}\left(\int_{-\frac{3}{4}\pi}^{\frac{1}{4}\pi}d\theta\right)\left(\int_{0}^{\infty}e^{\frac{\,-r^{2}\,}{2}}\,d\frac{\,r^{2}\,}{2}\right)\\[0.45em]
&=\frac{1}{\,2\,}
\end{aligned}
$$

</div>

</div>

<div id="ex-three-iid-uniform-order" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.6</div>

令 <span class="text-nowrap">$X_1,X_2,X_3\overset{\mathrm{iid}}{\sim}\mathcal{U}(0,1)$，</span>則回答以下問題:

<ol class="topic-list-paren">
  <li>試求 <span class="text-nowrap">$\mathbb{P}(X_1<X_2)$。</span></li>
  <li>試求 <span class="text-nowrap">$\mathbb{P}(X_1<X_2<X_3)$。</span></li>
  <li>試求 <span class="text-nowrap">$\mathbb{P}(X_1<X_2<X_3<u)$，</span>其中 <span class="text-nowrap">$0<u<1$。</span></li>
</ol>

(1) **[ 法一 ]**
{: .topic-paren-item}

由題意可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X_1X_2}(x_1,x_2)=f_{\sssig X_1}(x_1)\,f_{\sssig X_2}(x_2)=1,\quad 0<x_1,x_2<1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig X_1X_2}(x_1,x_2)&=f_{\sssig X_1}(x_1)\,f_{\sssig X_2}(x_2)=1,\\[0.45em]
&\quad 0<x_1,x_2<1
\end{aligned}
$$

</div>

則有
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X_1<X_2)=\int_{0}^{1}\!\!\int_{0}^{x_2}f_{\sssig X_1X_2}(x_1,x_2)\,dx_1\,dx_2=\int_{0}^{1}\!\!\int_{0}^{x_2}1\,dx_1\,dx_2=\Bigl[\frac{1}{\,2\,}x_2^{2}\Bigr]_{0}^{1}=\frac{1}{\,2\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X_1<X_2)&=\int_{0}^{1}\!\!\int_{0}^{x_2}f_{\sssig X_1X_2}(x_1,x_2)\,dx_1\,dx_2\\[0.45em]
&=\int_{0}^{1}\!\!\int_{0}^{x_2}1\,dx_1\,dx_2\\[0.45em]
&=\Bigl[\frac{1}{\,2\,}x_2^{2}\Bigr]_{0}^{1}=\frac{1}{\,2\,}
\end{aligned}
$$

</div>

**[ 法二 ]**
{: .topic-paren-cont}

本題所求範圍如下圖所示
{: .topic-paren-cont}

<figure id="fig-independent-normal-region" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/independent-normal-region.svg" alt="第一象限中畫一條由原點出發並通過 (1, 1) 的斜線，斜線左上方的三角形以淡紅色填滿。斜線的右上端標 x1 等於 x2。由 (1, 1) 各拉一條虛線到兩軸，橫軸上的虛線端點標 1，縱軸上的虛線端點標 1。橫軸右端標 x1，縱軸上端標 x2。">
  <figcaption><span class="topic-figure__label">Fig. 3.8.</span> 直線 $x_1=x_2$ 把值域切成兩塊，填色的一塊就是 $x_1<x_2$ 所對應的範圍。</figcaption>
</figure>

又由聯合分配為均勻分配可知，機率即為所求範圍在值域中之佔比，即
{: .topic-paren-cont}

$$
\mathbb{P}(X_1<X_2)=1\times 1\times\frac{1}{\,2\,}=\frac{1}{\,2\,}
$$

(2) **[ 法一 ]**
{: .topic-paren-item}

由題意可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X_1X_2X_3}(x_1,x_2,x_3)=f_{\sssig X_1}(x_1)\,f_{\sssig X_2}(x_2)\,f_{\sssig X_3}(x_3)=1,\quad 0<x_1,x_2,x_3<1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig X_1X_2X_3}(x_1,x_2,x_3)&=f_{\sssig X_1}(x_1)\,f_{\sssig X_2}(x_2)\,f_{\sssig X_3}(x_3)=1,\\[0.45em]
&\qquad 0<x_1,x_2,x_3<1
\end{aligned}
$$

</div>

則有
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X_1<X_2<X_3)&=\int_{0}^{1}\!\!\int_{0}^{x_3}\!\!\int_{0}^{x_2}f_{\sssig X_1X_2X_3}(x_1,x_2,x_3)\,dx_1\,dx_2\,dx_3\\[0.45em]
&=\int_{0}^{1}\!\!\int_{0}^{x_3}\!\!\int_{0}^{x_2}1\,dx_1\,dx_2\,dx_3=\Bigl[\frac{1}{\,6\,}x_3^{3}\Bigr]_{0}^{1}=\frac{1}{\,6\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(X_1<X_2<X_3)\\[0.45em]
&\ =\int_{0}^{1}\!\!\int_{0}^{x_3}\!\!\int_{0}^{x_2}f_{\sssig X_1X_2X_3}(x_1,x_2,x_3)\,dx_1\,dx_2\,dx_3\\[0.45em]
&\ =\int_{0}^{1}\!\!\int_{0}^{x_3}\!\!\int_{0}^{x_2}1\,dx_1\,dx_2\,dx_3\\[0.45em]
&\ =\Bigl[\frac{1}{\,6\,}x_3^{3}\Bigr]_{0}^{1}=\frac{1}{\,6\,}
\end{aligned}
$$

</div>

**[ 法二 ]**
{: .topic-paren-cont}

本題所求範圍如下圖所示
{: .topic-paren-cont}

<figure id="fig-three-uniform-region-a" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/three-uniform-region-a.svg" alt="一個以透視方式畫出的立方體線框，三軸分別標 x1、x2 與 x3，每一軸的刻度都是 0、0.5 與 1。立方體之內有一個以淡紅色填滿的四面體，四個頂點分別是原點、(0, 0, 1)、(0, 1, 1) 與 (1, 1, 1)。四面體的稜邊與立方體上面的兩條線以虛線畫出，立方體靠近觀看者的三條稜邊以實線畫出。">
  <figcaption><span class="topic-figure__label">Fig. 3.9.</span> 立方體之中填色的四面體，就是 $x_1<x_2<x_3$ 所對應的範圍。</figcaption>
</figure>

又由聯合分配為均勻分配可知，機率即為所求範圍在值域中之佔比，即
{: .topic-paren-cont}

$$
\mathbb{P}(X_1<X_2<X_3)=1\times 1\times\frac{1}{\,2\,}\times 1\times\frac{1}{\,3\,}=\frac{1}{\,6\,}
$$

(3) **[ 法一 ]**
{: .topic-paren-item}

由題意可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X_1X_2X_3}(x_1,x_2,x_3)=f_{\sssig X_1}(x_1)\,f_{\sssig X_2}(x_2)\,f_{\sssig X_3}(x_3)=1,\quad 0<x_1,x_2,x_3<1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig X_1X_2X_3}(x_1,x_2,x_3)&=f_{\sssig X_1}(x_1)\,f_{\sssig X_2}(x_2)\,f_{\sssig X_3}(x_3)=1,\\[0.45em]
&\qquad 0<x_1,x_2,x_3<1
\end{aligned}
$$

</div>

則有
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X_1<X_2<X_3<u)&=\int_{0}^{u}\!\!\int_{0}^{x_3}\!\!\int_{0}^{x_2}f_{\sssig X_1X_2X_3}(x_1,x_2,x_3)\,dx_1\,dx_2\,dx_3\\[0.45em]
&=\int_{0}^{u}\!\!\int_{0}^{x_3}\!\!\int_{0}^{x_2}1\,dx_1\,dx_2\,dx_3=\Bigl[\frac{1}{\,6\,}x_3^{3}\Bigr]_{0}^{u}=\frac{\,u^{3}\,}{\,6\,},\quad 0<u<1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(X_1<X_2<X_3<u)\\[0.45em]
&\ =\int_{0}^{u}\!\!\int_{0}^{x_3}\!\!\int_{0}^{x_2}f_{\sssig X_1X_2X_3}(x_1,x_2,x_3)\,dx_1\,dx_2\,dx_3\\[0.45em]
&\ =\int_{0}^{u}\!\!\int_{0}^{x_3}\!\!\int_{0}^{x_2}1\,dx_1\,dx_2\,dx_3\\[0.45em]
&\ =\Bigl[\frac{1}{\,6\,}x_3^{3}\Bigr]_{0}^{u}=\frac{\,u^{3}\,}{\,6\,},\quad 0<u<1
\end{aligned}
$$

</div>

**[ 法二 ]**
{: .topic-paren-cont}

本題所求範圍如下圖所示
{: .topic-paren-cont}

<figure id="fig-three-uniform-region-b" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/three-uniform-region-b.svg" alt="與前一張同樣的立方體線框，三軸標 x1、x2 與 x3，刻度改為 0、0.5、u 與 1。立方體之內以淡紅色填滿的四面體縮小，四個頂點分別是原點、(0, 0, u)、(0, u, u) 與 (u, u, u)。另有三條只畫到 u 為止的虛線標出這個四面體所佔的位置。">
  <figcaption><span class="topic-figure__label">Fig. 3.10.</span> 刻度多標一個 <span class="text-nowrap">$u$，</span>填色的四面體隨之縮到以 $u$ 為界，就是 $x_1<x_2<x_3<u$ 所對應的範圍。</figcaption>
</figure>

又由聯合分配為均勻分配可知，機率即為所求範圍在值域中之佔比，即
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X_1<X_2<X_3<u)=u\times u\times\frac{1}{\,2\,}\times u\times\frac{1}{\,3\,}=\frac{\,u^{3}\,}{\,6\,},\quad 0<u<1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X_1<X_2<X_3<u)&=u\times u\times\frac{1}{\,2\,}\times u\times\frac{1}{\,3\,}\\[0.45em]
&=\frac{\,u^{3}\,}{\,6\,},\quad 0<u<1
\end{aligned}
$$

</div>

</div>

## 本篇小結

[Example 3.4](#ex-joint-pdf-exponential-region) 的聯合值域是 $y>x>0$ 這個楔形，joint pdf 在其上等於 $e^{-y}$ 這個式子，對 $y$ 由 $x$ 積到無窮大之後，得到 $X$ 的邊際 pdf 為 <span class="text-nowrap">$e^{-x}$，</span>值域為 <span class="text-nowrap">$x>0$。</span>這一題的 joint pdf 除了值域範圍之外並沒有任何的 <span class="text-nowrap">$x$，</span>但它仍然是 $X$ 與 $Y$ 的 joint pdf，而不只是 $Y$ 自己的 marginal pdf。

把 [Example 3.2](/teaching-topics/marginal-probability-density-functions/#ex-joint-pdf-region-basic)、[Example 3.3](/teaching-topics/marginal-probability-density-functions/#ex-joint-pdf-triangle-region) 與 [Example 3.4](#ex-joint-pdf-exponential-region) 放在一起看，差別在於聯合值域是不是積空間。[Example 3.2](/teaching-topics/marginal-probability-density-functions/#ex-joint-pdf-region-basic) 的 joint pdf 是兩個 marginal pdf 的乘積，值域也是兩個邊際值域所形成的積空間，這兩個條件正是稍後要談的獨立隨機變數；另外兩題則都不是。也因為 joint cdf 是定義在 $\mathbb{R}^{2}$ 上的函數，平面上每一點都要有函數值，值域為積空間的那一題可以用九宮格把平面完全切開，值域不是積空間的那一題則要跟著邊界分段，兩張分區圖把這件事畫了出來。

[Example 3.5](#ex-independent-normal-region) 與 [Example 3.6](#ex-three-iid-uniform-order) 把重點移到所求的事件上。前者的兩個變數獨立且各服從 <span class="text-nowrap">$\mathcal{N}(0,1)$，</span>joint pdf 是兩個密度的乘積，所求的單位圓盤與半平面在直角座標之下都不容易積分，改用極座標之後，兩個積分分別給出 $1-e^{-\frac{1}{2}}$ 與 <span class="text-nowrap">$\frac{1}{2}$。</span>後者的三個變數獨立且各服從 <span class="text-nowrap">$\mathcal{U}(0,1)$，</span>joint pdf 在值域上恆為 <span class="text-nowrap">$1$，</span>逐層積分可得 <span class="text-nowrap">$\frac{1}{2}$、</span>$\frac{1}{6}$ 與 $\frac{u^{3}}{6}$ 三個答案；由於密度恆為 <span class="text-nowrap">$1$，</span>同樣三個答案也可以直接取所求範圍在值域中的佔比得到。

[下一篇](/teaching-topics/marginal-cumulative-distribution-functions/)先以兩道均勻分配序列的例題延續同樣的手法，再回到分配函數本身，介紹[邊際累積分配函數](/teaching-topics/marginal-cumulative-distribution-functions/#def-marginal-cdf)。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
