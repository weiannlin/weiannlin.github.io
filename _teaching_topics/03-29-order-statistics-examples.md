---
title: "順序統計量的例題"
subtitle: "Examples of Order Statistics"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 29
order: 329
permalink: /teaching-topics/order-statistics-examples/
date: 2026-08-13
published: false
excerpt: "標準均勻分配的五個順序統計量，其聯合 pdf 恆為 $120$ 這個常數，但值域限定在 $0<y_1<y_2<y_3<y_4<y_5<1$ 之上，因此彼此並不獨立；最小值與最大值分別服從 $\\mathrm{Beta}(1,5)$ 與 $\\mathrm{Beta}(5,1)$，全距 $R=Y_5-Y_1$ 則服從 $\\mathrm{Beta}(4,2)$。順序統計量還可以定義出樣本全距與樣本中位數等統計量，而指數分配的隨機樣本，其最小值與最大值的分配則可以直接由事件的定義求出 cdf 再微分而得。本篇並給出順序統計量的抽樣分配 cdf，其中第 $i$ 個順序統計量的 cdf 是一組二項機率之和，最小值與最大值的聯合 cdf 則由兩個機率相減而得。最後兩道例題把同一套作法用在離散型之上，一題求取值為 $1$ 至 $6$、機率均為 $\\frac{1}{6}$ 的分配之中五個觀測值最小者的 pmf，一題證明非負整數型隨機樣本最小值的期望值可以寫成尾機率的 $m$ 次方之和。"
---

[上一篇](/teaching-topics/order-statistics-distributions/)以 [Theorem 3.24](/teaching-topics/order-statistics-distributions/#thm-order-stat-samp-dist-pdf) 給出隨機樣本之[順序統計量](/teaching-topics/order-statistics/#def-order-stat)的抽樣分配 pdf，並以幾張圖說明其中的排列組合是怎麼數出來的，最後指出標準均勻分配的順序統計量都是[貝塔分配](/teaching-topics/beta-function-and-distribution/#def-beta-distribution)。

本篇先以 [Example 3.63](#ex-uniform-order-statistics-five) 把這五款公式在標準均勻分配上實際用過一遍，一併求出全距的分配，並在其後說明順序統計量還可以定義出樣本全距與樣本[中位數](/teaching-topics/median/#def-median)這一類的統計量；接著以 [Example 3.64](#ex-three-iid-order-pdf) 由[指數分配](/teaching-topics/gamma-function-exponential-distribution/#def-exponential-distribution)的隨機樣本求最小值與最大值的分配。之後以 [Theorem 3.25](#thm-order-stat-samp-dist-cdf) 給出順序統計量的抽樣分配 cdf 並證明之，最後以 [Example 3.65](#ex-discrete-order-statistics-die) 與 [Example 3.66](#ex-order-statistics-minimum) 兩道離散型的例題作結。

## 均勻分配的順序統計量與全距的分配

<div id="ex-uniform-order-statistics-five" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.63</div>

<div lang="en" markdown="1">
Suppose that $\lbrace X_i\rbrace_{i=1}^{5}$ is a random sample drawn from the uniform distribution <span class="text-nowrap">$\mathcal{U}(0,1)$,</span> and let <span class="text-nowrap">$Y_i$,</span> <span class="text-nowrap">$i=1,2,3,4,5$,</span> denote the $i$-th smallest order statistic.

<ol class="topic-list-paren">
  <li>Find the joint pdf of <span class="text-nowrap">$(Y_1,Y_2,Y_3,Y_4,Y_5)$,</span> and determine whether $Y_1,Y_2,Y_3,Y_4,Y_5$ are independent of one another.</li>
  <li>Find the marginal pdf of $Y_1$ and the marginal pdf of <span class="text-nowrap">$Y_5$,</span> and determine the name and the parameters of each of the two distributions.</li>
  <li>Let the range be <span class="text-nowrap">$R=Y_5-Y_1$.</span><br>
  (i) Find the pdf of <span class="text-nowrap">$R$,</span> and determine the name and the parameters of its distribution.<br>
  (ii) Evaluate the expectation $\mathbb{E}(R)$ and the variance <span class="text-nowrap">$\mathrm{Var}(R)$.</span></li>
</ol>
</div>

(1) 依題意可知
{: .topic-paren-item}

$$
X_1,X_2,X_3,X_4,X_5\overset{\mathrm{iid}}{\sim}\mathcal{U}(0,1)
$$

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
1, & 0<x<1\\[0.5em]
0, & \text{o.w.}
\end{array}
\right.
,\qquad
F_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & x<0\\[0.5em]
x, & 0\leqslant x<1\\[0.5em]
1, & x\geqslant 1
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig X}(x)&=
\left\lbrace
\begin{array}{c@{\quad}l}
1, & 0<x<1\\[0.5em]
0, & \text{o.w.}
\end{array}
\right.,\\[1em]
F_{\sssig X}(x)&=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & x<0\\[0.5em]
x, & 0\leqslant x<1\\[0.5em]
1, & x\geqslant 1
\end{array}
\right.
\end{aligned}
$$

</div>

<div class="topic-math-follow" markdown="1">

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\Longrightarrow f_{\sssig Y_1\cdots Y_5}(y_1,y_2,y_3,y_4,y_5)&=5!\times f_{\sssig X}(y_1)\times f_{\sssig X}(y_2)\times f_{\sssig X}(y_3)\\[0.45em]
&\quad\times f_{\sssig X}(y_4)\times f_{\sssig X}(y_5)\\[0.45em]
&=5!\times 1^{5}=120,\ \ 0<y_1<y_2<y_3<y_4<y_5<1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\Longrightarrow f_{\sssig Y_1\cdots Y_5}(&y_1,y_2,y_3,y_4,y_5) =5!\times f_{\sssig X}(y_1)\times f_{\sssig X}(y_2)\\[0.2em]
&\qquad\times f_{\sssig X}(y_3)\times f_{\sssig X}(y_4)\times f_{\sssig X}(y_5)\\[0.45em]
&=5!\times 1^{5}=120,\\[0.45em]
&\quad 0<y_1<y_2<y_3<y_4<y_5<1
\end{aligned}
$$

</div>

</div>

$\Longrightarrow$ $(Y_1,Y_2,Y_3,Y_4,Y_5)$ 彼此並不獨立
{: .topic-paren-cont}

(2) 最小者的邊際 pdf 為
{: .topic-paren-item}

<!-- errata-pending: 書稿第 5484 與 5486 行把 $Y_1$ 與 $Y_n$ 邊際 pdf 的係數印成 $5!$，
     但同兩行的下一步就寫成 $5(1-y_1)^4$ 與 $5y_n^4$，可見 $5!$ 為誤植。
     依 Theorem 3.24 (1) 與 (2)，$n=5$ 時的係數是 $n=5$ 而非 $5!=120$
     (若照 Theorem 3.24 (3) 的一般式寫則為 $\frac{5!}{(1-1)!(5-1)!}=5$)。
     網頁均改為 $5$: 兩式各兩處，桌面與手機版面各一份，共八處。
     待作者裁定後登錄 ERRATA.md。 -->

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f_{\sssig Y_1}(y_1)&=5\,f_{\sssig X}(y_1)\bigl[1-F_{\sssig X}(y_1)\bigr]^{5-1}\\[0.45em]
&=5\times 1\times\bigl[1-y_1\bigr]^{4}=5(1-y_1)^{4},\ \ 0<y_1<1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig Y_1}(y_1)&=5\,f_{\sssig X}(y_1)\bigl[1-F_{\sssig X}(y_1)\bigr]^{5-1}\\[0.45em]
&=5\times 1\times\bigl[1-y_1\bigr]^{4}\\[0.45em]
&=5(1-y_1)^{4},\ \ 0<y_1<1
\end{aligned}
$$

</div>

故可知
{: .topic-paren-cont}

$$
Y_1\sim\mathrm{Beta}(1,5)
$$

最大者的邊際 pdf 為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f_{\sssig Y_n}(y_n)&=5\,f_{\sssig X}(y_n)\bigl[F_{\sssig X}(y_n)\bigr]^{5-1}\\[0.45em]
&=5\times 1\times\bigl[y_n\bigr]^{4}=5y_n^{4},\ \ 0<y_n<1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig Y_n}(y_n)&=5\,f_{\sssig X}(y_n)\bigl[F_{\sssig X}(y_n)\bigr]^{5-1}\\[0.45em]
&=5\times 1\times\bigl[y_n\bigr]^{4}\\[0.45em]
&=5y_n^{4},\ \ 0<y_n<1
\end{aligned}
$$

</div>

故可知
{: .topic-paren-cont}

$$
Y_n\sim\mathrm{Beta}(5,1)
$$

(3) 首先先算出 $Y_1$ 與 $Y_5$ 的聯合 pdf 為
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f_{\sssig Y_1Y_5}(y_1,y_5)&=\frac{5!}{(5-2)!}f_{\sssig X}(y_1)f_{\sssig X}(y_5)\bigl[F_{\sssig X}(y_5)-F_{\sssig X}(y_1)\bigr]^{3}\\[0.45em]
&=20(y_5-y_1)^{3},\ \ 0<y_1<y_5<1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig Y_1Y_5}(y_1,y_5)&=\frac{5!}{(5-2)!}f_{\sssig X}(y_1)f_{\sssig X}(y_5)\\[0.2em]
&\qquad\bigl[F_{\sssig X}(y_5)-F_{\sssig X}(y_1)\bigr]^{3}\\[0.45em]
&=20(y_5-y_1)^{3},\ \ 0<y_1<y_5<1
\end{aligned}
$$

</div>

接著令 $W$ $=$ <span class="text-nowrap">$Y_1$，</span>$R$ $=$ <span class="text-nowrap">$Y_5-Y_1$，</span>則
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f_{\sssig WR}(w,r)&=f_{\sssig Y_1Y_5}(w,w+r)\lvert\mathbf{J}\rvert\\[0.45em]
&=20(w+r-w)^{3}=20r^{3},\ \ 0<w<w+r<1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig WR}(w,r)&=f_{\sssig Y_1Y_5}(w,w+r)\lvert\mathbf{J}\rvert\\[0.45em]
&=20(w+r-w)^{3}=20r^{3},\\[0.45em]
&\quad 0<w<w+r<1
\end{aligned}
$$

</div>

其中
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbf{J}=
\left\lvert
\begin{array}{cc}
\dfrac{dw}{dw} & \dfrac{dw}{dr}\\[0.9em]
\dfrac{d(w+r)}{dw} & \dfrac{d(w+r)}{dr}
\end{array}
\right\rvert=
\left\lvert
\begin{array}{cc}
1 & 0\\[0.35em]
1 & 1
\end{array}
\right\rvert=1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbf{J}&=
\left\lvert
\begin{array}{cc}
\dfrac{dw}{dw} & \dfrac{dw}{dr}\\[0.9em]
\dfrac{d(w+r)}{dw} & \dfrac{d(w+r)}{dr}
\end{array}
\right\rvert\\[0.8em]
&=
\left\lvert
\begin{array}{cc}
1 & 0\\[0.35em]
1 & 1
\end{array}
\right\rvert=1
\end{aligned}
$$

</div>

<div class="topic-math-follow" markdown="1">

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\Longrightarrow f_{\sssig R}(r)=\int_{0}^{1-r}20r^{3}\,dw=\bigl[20r^{3}w\bigr]_{0}^{1-r}=20r^{3}(1-r),\ \ 0<r<1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\Longrightarrow f_{\sssig R}(r)&=\int_{0}^{1-r}20r^{3}\,dw\\[0.45em]
&=\bigl[20r^{3}w\bigr]_{0}^{1-r}\\[0.45em]
&=20r^{3}(1-r),\ \ 0<r<1
\end{aligned}
$$

</div>

</div>

<div class="topic-math-follow" markdown="1">

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\Longrightarrow R\sim\mathrm{Beta}(4,2)\\[0.6em]
\mathbb{E}(R)=\frac{4}{\,4+2\,}=\frac{2}{\,3\,},\qquad\mathrm{Var}(R)=\frac{4\times 2}{\,(4+2)^{2}(4+2+1)\,}=\frac{2}{\,63\,}
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\Longrightarrow R&\sim\mathrm{Beta}(4,2)\\[0.6em]
\mathbb{E}(R)&=\frac{4}{\,4+2\,}=\frac{2}{\,3\,},\\[0.6em]
\mathrm{Var}(R)&=\frac{4\times 2}{\,(4+2)^{2}(4+2+1)\,}=\frac{2}{\,63\,}
\end{aligned}
$$

</div>

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

事實上，由順序統計量可加以定義的統計量相當多元，樣本全距 (sample range) 即是一個很好的例子，即

$$
R=Y_n-Y_1
$$

另一個例子是樣本中位數 (sample median)，即

<!-- errata-pending: 書稿第 5506 行的樣本中位數，兩個分支都寫「當 $n$ 為奇數」，
     第二個分支 $\frac{1}{2}(Y_{\frac{n}{2}}+Y_{\frac{n}{2}+1})$ 顯然是 $n$ 為偶數的情形。
     網頁改為「當 $n$ 為偶數」。待作者裁定後登錄 ERRATA.md。 -->

$$
m_{\sssig e}=
\left\lbrace
\begin{array}{c@{\quad}l}
Y_{\sssig \frac{n+1}{2}}, & \text{當 }n\text{ 為奇數}\\[1em]
\frac{1}{\,2\,}\bigl(Y_{\sssig \frac{n}{2}}+Y_{\sssig \frac{n}{2}+1}\bigr), & \text{當 }n\text{ 為偶數}
\end{array}
\right.
$$

</div>

## 指數分配的最小值與最大值

<div id="ex-three-iid-order-pdf" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.64</div>

<div lang="en" markdown="1">
Suppose that <span class="text-nowrap">$X_1$,</span> $X_2$ and $X_3$ are independent and identically distributed random variables whose common pdf is

$$
f_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
e^{-x}, & 0<x<\infty\\[0.5em]
0, & \text{otherwise}
\end{array}
\right.
$$

<ol class="topic-list-paren">
  <li>Determine the distribution of <span class="text-nowrap">$Y=\min\lbrace X_1,X_2,X_3\rbrace$.</span></li>
  <li>Determine the distribution of <span class="text-nowrap">$Y=\max\lbrace X_1,X_2,X_3\rbrace$.</span></li>
</ol>
</div>

(1) 我們首先計算 $X_i,\ i=1,2,3$ 的 cdf 如下
{: .topic-paren-item}

$$
F_{\sssig X_i}(x_i)=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & x_i\leqslant 0\\[0.6em]
\displaystyle\int_{0}^{x_i}e^{-t}\,dt=1-e^{-x_i}, & 0<x_i<\infty
\end{array}
\right.
$$

則由於 $Y=\min\lbrace X_1,X_2,X_3\rbrace$ 為 $X_1, X_2, X_3$ 中最小者，故我們有
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
F_{\sssig Y}(y)&=\mathbb{P}(Y\leqslant y)=1-\mathbb{P}(Y>y)\\[0.45em]
&=1-\mathbb{P}(X_1>y,X_2>y,X_3>y)\\[0.45em]
&=1-\mathbb{P}(X_1>y)\mathbb{P}(X_2>y)\mathbb{P}(X_3>y)\\[0.45em]
&=1-\bigl[1-\mathbb{P}(X_1\leqslant y)\bigr]^{3}=1-\bigl[1-F_{\sssig X_1}(y)\bigr]^{3}\\[0.45em]
&=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & y\leqslant 0\\[0.5em]
1-[e^{-y}]^{3}=1-e^{-3y}, & 0<y<\infty
\end{array}
\right.
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig Y}(y)&=\mathbb{P}(Y\leqslant y)=1-\mathbb{P}(Y>y)\\[0.45em]
&=1-\mathbb{P}(X_1>y,X_2>y,X_3>y)\\[0.45em]
&=1-\mathbb{P}(X_1>y)\mathbb{P}(X_2>y)\mathbb{P}(X_3>y)\\[0.45em]
&=1-\bigl[1-\mathbb{P}(X_1\leqslant y)\bigr]^{3}\\[0.45em]
&=1-\bigl[1-F_{\sssig X_1}(y)\bigr]^{3}\\[0.45em]
&=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & y\leqslant 0\\[0.5em]
1-[e^{-y}]^{3}=1-e^{-3y}, & 0<y<\infty
\end{array}
\right.
\end{aligned}
$$

</div>

故可知
{: .topic-paren-cont}

$$
f_{\sssig Y}(y)=\frac{\,d\,F_{\sssig Y}(y)\,}{d\,y}=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & y\leqslant 0\\[0.5em]
3e^{-3y}, & 0<y<\infty
\end{array}
\right.
$$

此即
{: .topic-paren-cont}

$$
Y=\min\lbrace X_1,X_2,X_3\rbrace\sim\mathrm{Exp}\Bigl(\beta=\frac{1}{\,3\,}\Bigr)
$$

(2) 由於 $Y=\max\lbrace X_1,X_2,X_3\rbrace$ 為 $X_1, X_2, X_3$ 中最大者，故我們有
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
F_{\sssig Y}(y)&=\mathbb{P}(Y\leqslant y)=\mathbb{P}(X_1\leqslant y,X_2\leqslant y,X_3\leqslant y)\\[0.45em]
&=\mathbb{P}(X_1\leqslant y)\mathbb{P}(X_2\leqslant y)\mathbb{P}(X_3\leqslant y)\\[0.45em]
&=\bigl[\mathbb{P}(X_1\leqslant y)\bigr]^{3}=\bigl[F_{\sssig X_1}(y)\bigr]^{3}\\[0.45em]
&=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & y\leqslant 0\\[0.5em]
\bigl[1-e^{-y}\bigr]^{3}, & 0<y<\infty
\end{array}
\right.
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig Y}(y)&=\mathbb{P}(Y\leqslant y)\\[0.45em]
&=\mathbb{P}(X_1\leqslant y,X_2\leqslant y,X_3\leqslant y)\\[0.45em]
&=\mathbb{P}(X_1\leqslant y)\mathbb{P}(X_2\leqslant y)\mathbb{P}(X_3\leqslant y)\\[0.45em]
&=\bigl[\mathbb{P}(X_1\leqslant y)\bigr]^{3}=\bigl[F_{\sssig X_1}(y)\bigr]^{3}\\[0.45em]
&=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & y\leqslant 0\\[0.5em]
\bigl[1-e^{-y}\bigr]^{3}, & 0<y<\infty
\end{array}
\right.
\end{aligned}
$$

</div>

故可知
{: .topic-paren-cont}

$$
f_{\sssig Y}(y)=\frac{\,d\,F_{\sssig Y}(y)\,}{d\,y}=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & y\leqslant 0\\[0.5em]
3[1-e^{-y}]^{2}(e^{-y}), & 0<y<\infty
\end{array}
\right.
$$

</div>

## 順序統計量的抽樣分配 cdf

<div id="thm-order-stat-samp-dist-cdf" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 3.25 (隨機樣本之順序統計量的抽樣分配 cdf, cdf of the sampling distribution of order statistics)</div>

令 $Y_1$ $\leqslant\cdots\leqslant$ $Y_n$ 為隨機樣本 $X_1,\ldots,X_n$ 之順序統計量，則

<ol class="topic-list-paren topic-list-paren--math">
  <li>
$$
F_{\sssig Y_1}(y_1)=1-\bigl[1-F_{\sssig X}(y_1)\bigr]^{n}
$$
  </li>
  <li>
$$
F_{\sssig Y_n}(y_n)=\bigl[F_{\sssig X}(y_n)\bigr]^{n}
$$
  </li>
  <li>
<div class="topic-math-layout topic-math-layout--desktop">
$$
F_{\sssig Y_i}(y_i)=\sum_{k=i}^{n}\binom{n}{k}\bigl[F_{\sssig X}(y_i)\bigr]^{k}\bigl[1-F_{\sssig X}(y_i)\bigr]^{n-k}
$$
</div>
<div class="topic-math-layout topic-math-layout--mobile">
$$
\begin{aligned}
F_{\sssig Y_i}(y_i)&=\sum_{k=i}^{n}\binom{n}{k}\bigl[F_{\sssig X}(y_i)\bigr]^{k}\\[0.2em]
&\qquad\bigl[1-F_{\sssig X}(y_i)\bigr]^{n-k}
\end{aligned}
$$
</div>
  </li>
  <li>
<div class="topic-math-layout topic-math-layout--desktop">
$$
F_{\sssig Y_1Y_n}(y_1,y_n)=\bigl[F_{\sssig X}(y_n)\bigr]^{n}-\bigl[F_{\sssig X}(y_n)-F_{\sssig X}(y_1)\bigr]^{n}
$$
</div>
<div class="topic-math-layout topic-math-layout--mobile">
$$
\begin{aligned}
F_{\sssig Y_1Y_n}(y_1,y_n)&=\bigl[F_{\sssig X}(y_n)\bigr]^{n}\\[0.45em]
&\qquad-\bigl[F_{\sssig X}(y_n)-F_{\sssig X}(y_1)\bigr]^{n}
\end{aligned}
$$
</div>
  </li>
</ol>

</div>

<div class="topic-proof" markdown="1">
**Proof.**

(1) 與 (2) 的證明請見 [Theorem 3.24](/teaching-topics/order-statistics-distributions/#thm-order-stat-samp-dist-pdf) 的 (1) 與 (2) 之證明。

(3) 由於 $Y_i$ 為順序統計量第 $i$ 小者，故
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
F_{\sssig Y_i}(y_i)&=\mathbb{P}(Y_i\leqslant y_i)=\mathbb{P}(\text{至少 }i\text{ 個 }X\text{ 比 }y_i\text{ 小})\\[0.45em]
&=\sum_{k=i}^{n}\binom{n}{k}\bigl[F_{\sssig X}(y_i)\bigr]^{k}\bigl[1-F_{\sssig X}(y_i)\bigr]^{n-k}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig Y_i}(y_i)&=\mathbb{P}(Y_i\leqslant y_i)\\[0.45em]
&=\mathbb{P}(\text{至少 }i\text{ 個 }X\text{ 比 }y_i\text{ 小})\\[0.45em]
&=\sum_{k=i}^{n}\binom{n}{k}\bigl[F_{\sssig X}(y_i)\bigr]^{k}\\[0.2em]
&\qquad\bigl[1-F_{\sssig X}(y_i)\bigr]^{n-k}
\end{aligned}
$$

</div>

(4) 依照 joint cdf 及順序統計量之定義，我們有
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
F_{\sssig Y_1Y_n}(y_1,y_n)&=\mathbb{P}(Y_1\leqslant y_1,Y_n\leqslant y_n)\\[0.45em]
&=\mathbb{P}(Y_n\leqslant y_n)-\mathbb{P}(Y_1>y_1,Y_n\leqslant y_n)\\[0.45em]
&=\bigl[F_{\sssig X}(y_n)\bigr]^{n}-\bigl[F_{\sssig X}(y_n)-F_{\sssig X}(y_1)\bigr]^{n}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig Y_1Y_n}(y_1,y_n)&=\mathbb{P}(Y_1\leqslant y_1,Y_n\leqslant y_n)\\[0.45em]
&=\mathbb{P}(Y_n\leqslant y_n)-\mathbb{P}(Y_1>y_1,Y_n\leqslant y_n)\\[0.45em]
&=\bigl[F_{\sssig X}(y_n)\bigr]^{n}\\[0.45em]
&\qquad-\bigl[F_{\sssig X}(y_n)-F_{\sssig X}(y_1)\bigr]^{n}
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

## 最小順序統計量的 pmf 與[期望值](/teaching-topics/expectation/#def-expectation)

<div id="ex-discrete-order-statistics-die" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.65</div>

<div lang="en" markdown="1">
Suppose that a distribution has the pmf <span class="text-nowrap">$f_{\sssig X}(x)=\frac{1}{\,6\,}$,</span> <span class="text-nowrap">$x=1,2,3,4,5,6$.</span> Find the pmf of the smallest observation in a random sample of size $5$ drawn from this distribution.
</div>

依題意可令 $Y_1$ $=$ <span class="text-nowrap">$\min(X_1,\ldots,X_5)$，</span>則

$$
F_{\sssig X_i}(x_i)=\frac{\,x_i\,}{6},\ x_i=1,2,3,4,5,6
$$

且可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig Y_1}(y_1)=1-\bigl[1-F_{\sssig X_1}(y_1)\bigr]^{5}=1-\left(\frac{\,6-y_1\,}{6}\right)^{5},\ y_1=1,2,3,4,5,6
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig Y_1}(y_1)&=1-\bigl[1-F_{\sssig X_1}(y_1)\bigr]^{5}\\[0.45em]
&=1-\left(\frac{\,6-y_1\,}{6}\right)^{5},\\[0.45em]
&\quad y_1=1,2,3,4,5,6
\end{aligned}
$$

</div>

由此可計算 pmf 為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
p_{\sssig Y_1}(y_1)&=F_{\sssig Y_1}(y_1)-F_{\sssig Y_1}(y_1-1)\\[0.45em]
&=\left(\frac{\,7-y_1\,}{6}\right)^{5}-\left(\frac{\,6-y_1\,}{6}\right)^{5},\ y_1=1,2,3,4,5,6
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig Y_1}(y_1)&=F_{\sssig Y_1}(y_1)-F_{\sssig Y_1}(y_1-1)\\[0.45em]
&=\left(\frac{\,7-y_1\,}{6}\right)^{5}-\left(\frac{\,6-y_1\,}{6}\right)^{5},\\[0.45em]
&\quad y_1=1,2,3,4,5,6
\end{aligned}
$$

</div>

</div>

<div id="ex-order-statistics-minimum" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.66</div>

<div lang="en" markdown="1">
Suppose that $X_1,X_2,\ldots,X_m$ are $m$ independent random variables taking non-negative integer values, all of them sharing the common distribution <span class="text-nowrap">$\mathbb{P}(X=k)=p_{\sssig k}$,</span> and let <span class="text-nowrap">$r_{\sssig n}=\sum_{k=n}^{\infty}p_{\sssig k}$.</span> Show that

$$
\mathbb{E}\bigl[\min(X_1,\ldots,X_m)\bigr]=\sum_{n=1}^{\infty}r_{\sssig n}^{m}
$$
</div>

令 $Y$ $=$ <span class="text-nowrap">$\min(X_1,\ldots,X_m)$，</span>則由 [Theorem 2.8](/teaching-topics/expectation/#thm-expectation-tail-sum) 可知

$$
\mathbb{E}(Y)=\sum_{k=1}^{\infty}\mathbb{P}(Y\geqslant k)
$$

其中

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(Y\geqslant k)&=\mathbb{P}\bigl(\min(X_1,\ldots,X_m)\geqslant k\bigr)\\[0.45em]
&=\mathbb{P}(X_1\geqslant k,\ldots,X_m\geqslant k)\\[0.45em]
&=\mathbb{P}(X_1\geqslant k)\cdots\mathbb{P}(X_m\geqslant k)=\bigl[\mathbb{P}(X_1\geqslant k)\bigr]^{m}\\[0.45em]
&=\left[\sum_{s=k}^{\infty}\mathbb{P}(X_1=s)\right]^{m}=r_{\sssig k}^{m}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(Y\geqslant k)&=\mathbb{P}\bigl(\min(X_1,\ldots,X_m)\geqslant k\bigr)\\[0.45em]
&=\mathbb{P}(X_1\geqslant k,\ldots,X_m\geqslant k)\\[0.45em]
&=\mathbb{P}(X_1\geqslant k)\cdots\mathbb{P}(X_m\geqslant k)\\[0.45em]
&=\bigl[\mathbb{P}(X_1\geqslant k)\bigr]^{m}\\[0.45em]
&=\left[\sum_{s=k}^{\infty}\mathbb{P}(X_1=s)\right]^{m}=r_{\sssig k}^{m}
\end{aligned}
$$

</div>

則可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\bigl[\min(X_1,\ldots,X_m)\bigr]=\sum_{k=1}^{\infty}\mathbb{P}(Y\geqslant k)=\sum_{k=1}^{\infty}r_{\sssig k}^{m}=\sum_{n=1}^{\infty}r_{\sssig n}^{m}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[\min(X_1,\ldots,X_m)\bigr]&=\sum_{k=1}^{\infty}\mathbb{P}(Y\geqslant k)\\[0.45em]
&=\sum_{k=1}^{\infty}r_{\sssig k}^{m}=\sum_{n=1}^{\infty}r_{\sssig n}^{m}
\end{aligned}
$$

</div>

</div>

## 本篇小結

[Example 3.63](#ex-uniform-order-statistics-five) 把 [Theorem 3.24](/teaching-topics/order-statistics-distributions/#thm-order-stat-samp-dist-pdf) 的公式在標準均勻分配上實際用過一遍。由於這個分配的 pdf 在 $0<x<1$ 之上恆為 <span class="text-nowrap">$1$、</span>cdf 恰好是 <span class="text-nowrap">$x$，</span>整組順序統計量的聯合 pdf 因而是 $5!$ 這個常數，也就是 <span class="text-nowrap">$120$；</span>但它的值域限定在 $0<y_1<y_2<y_3<y_4<y_5<1$ 之上，五個變數的取值互相牽制，因此彼此並不獨立。最小者與最大者的邊際 pdf 分別為 $5(1-y_1)^{4}$ 與 $5y_n^{4}$ 這兩個式子，即 $\mathrm{Beta}(1,5)$ 與 <span class="text-nowrap">$\mathrm{Beta}(5,1)$。</span>全距 $R=Y_5-Y_1$ 的分配則要先求出 $Y_1$ 與 $Y_5$ 的聯合 <span class="text-nowrap">pdf，</span>再令 $W=Y_1$ 湊足維度、以 Jacobian 法轉到 $(W,R)$ 之上，最後把 $W$ 積分掉，所得的 $20r^{3}(1-r)$ 即 <span class="text-nowrap">$\mathrm{Beta}(4,2)$，</span>期望值與[變異數](/teaching-topics/variance/#def-variance)分別是 $\frac{2}{\,3\,}$ 與 <span class="text-nowrap">$\frac{2}{\,63\,}$。</span>

由順序統計量所定義出來的統計量相當多元，樣本全距與樣本中位數都是很好的例子，後者在 $n$ 為奇數時取正中間的那一個順序統計量，$n$ 為偶數時取中間兩個的平均。[Example 3.64](#ex-three-iid-order-pdf) 換成指數分配的隨機樣本，作法則回到事件本身。最小者大於 $y$ 這件事等於三個變數都大於 <span class="text-nowrap">$y$，</span>最大者小於等於 $y$ 這件事等於三個變數都小於等於 <span class="text-nowrap">$y$，</span>各以獨立性拆成三個機率相乘之後即得 <span class="text-nowrap">cdf，</span>再對 $y$ 微分就是 pdf。最小者的 pdf 是 <span class="text-nowrap">$3e^{-3y}$，</span>仍為指數分配，只是平均數縮成原本的三分之一；最大者的 pdf 則是 <span class="text-nowrap">$3[1-e^{-y}]^{2}(e^{-y})$，</span>已經不是指數分配。

[Theorem 3.25](#thm-order-stat-samp-dist-cdf) 把同一組結果改寫成 cdf 的形式。最小者與最大者的 cdf 分別是 $1-\bigl[1-F_{\sssig X}(y_1)\bigr]^{n}$ 與 $\bigl[F_{\sssig X}(y_n)\bigr]^{n}$ 這兩個式子，證明與 [Theorem 3.24](/teaching-topics/order-statistics-distributions/#thm-order-stat-samp-dist-pdf) 的前兩款相同。第 $i$ 個順序統計量的 cdf 則換一個角度來數。$Y_i\leqslant y_i$ 這件事等於至少有 $i$ 個樣本比 $y_i$ 小，而每一個樣本比 $y_i$ 小的機率都是 <span class="text-nowrap">$F_{\sssig X}(y_i)$，</span>因此所求就是一組二項機率由 $k=i$ 加到 $k=n$ 的和。最小者與最大者的聯合 cdf 則以相減求得。先取 $Y_n\leqslant y_n$ 的機率，再扣掉其中 $Y_1>y_1$ 的那一部分，後者表示所有樣本都落在 $y_1$ 與 $y_n$ 之間，機率為 $\bigl[F_{\sssig X}(y_n)-F_{\sssig X}(y_1)\bigr]^{n}$ 這個式子。

最後兩道例題把同一套作法用在離散型之上。[Example 3.65](#ex-discrete-order-statistics-die) 的 cdf 是 <span class="text-nowrap">$\frac{\,x_i\,}{6}$，</span>代入 [Theorem 3.25](#thm-order-stat-samp-dist-cdf) 的第一款即得最小者的 <span class="text-nowrap">cdf，</span>離散型的 pmf 再由相鄰兩個 cdf 相減求得。[Example 3.66](#ex-order-statistics-minimum) 求的是最小者的期望值，非負整數型[隨機變數](/teaching-topics/random-variables-and-pmf/#def-random-variable)的期望值可以寫成尾機率之和，而 $Y\geqslant k$ 這件事等於每一個樣本都大於等於 <span class="text-nowrap">$k$，</span>機率因而是 $r_{\sssig k}$ 的 $m$ 次方，加總之後即得所求。這兩題所用的都是同一個觀點，最小者的事件可以拆成 $m$ 個獨立事件的交集。

第三章到此結束。全章先以[隨機向量與聯合 pmf](/teaching-topics/random-vectors-joint-pmf/) 把討論的對象由一個隨機變數推廣到多個，再依序給出[聯合 cdf](/teaching-topics/joint-cumulative-distribution-functions/)、[聯合 pdf](/teaching-topics/joint-probability-density-functions/) 與[邊際 pdf](/teaching-topics/marginal-probability-density-functions/)，並以[區域機率](/teaching-topics/region-probabilities-joint-density/)與[序列型例題](/teaching-topics/marginal-cumulative-distribution-functions/)示範聯合密度的積分怎麼算。接著是[條件分配](/teaching-topics/conditional-distributions/)與[它的例題](/teaching-topics/conditional-distributions-examples/)，以及聯合分配可以拆成兩個邊際分配相乘的[獨立隨機變數](/teaching-topics/independent-random-variables/)。有了這些之後，[多元隨機變數的期望值](/teaching-topics/multivariate-expectations/)、[條件期望值與條件變異數](/teaching-topics/conditional-expectation-and-variance/)各自把單變數的量數推廣到多變數，[雙重期望值定理](/teaching-topics/double-expectation-theorem/)、[它的例題](/teaching-topics/double-expectation-examples/)、[條件版全機率定理](/teaching-topics/conditional-law-of-total-probability/)、[變異數分解定理](/teaching-topics/variance-decomposition-theorem/)與[沃德等式](/teaching-topics/wald-identity-gamblers-ruin/)則圍繞著同一個加權平均的想法展開。[交叉動差與聯合 mgf](/teaching-topics/cross-moments-joint-mgf/) 之後進入兩個變數之間的關聯: [共變異數](/teaching-topics/covariance/)、[線性組合的變異數](/teaching-topics/variance-of-linear-combination/)、[共變異數矩陣](/teaching-topics/covariance-matrix/)、[相關係數](/teaching-topics/correlation-coefficient/)、[相關矩陣](/teaching-topics/correlation-properties-and-matrix/)與[母體線性迴歸式](/teaching-topics/population-linear-regression/)。全章最後處理的是多變數的函數轉換與排序: [多對多](/teaching-topics/many-to-many-transformations/)、[多對一與動差母函數法](/teaching-topics/mgf-method-transformations/)、[動差母函數法的例題](/teaching-topics/mgf-method-examples/)，以及[順序統計量的定義](/teaching-topics/order-statistics/)、[它的抽樣分配](/teaching-topics/order-statistics-distributions/)與本篇的例題。

<!-- ref-point: 待第四章各篇發布後，在此補一句銜接下一章的話並指向第四章第一篇。 -->

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
