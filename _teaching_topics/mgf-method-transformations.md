---
title: "多對一與動差母函數法"
subtitle: "Many-to-One Transformations and the Moment Generating Function Method"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 25
order: 325
permalink: /teaching-topics/mgf-method-transformations/
date: 2026-08-13
published: false
excerpt: "維度相同的多對多轉換求的是轉換後的聯合分配，但有的時候我們要的只是轉換後其中一個變數的邊際分配。作法是先照樣作一個維度相同的轉換，求出聯合 pdf 之後，再把不需要的那個變數積分掉，本篇的兩道例題即依此求得 $f_{\\sssig Z}(z)$ 與 $f_{\\sssig Y_1}(y_1)$ 這兩個邊際 pdf。若轉換本身是線性的，而且各個變數彼此獨立，另有一條更快的路: $W=\\sum_{i=1}^{n}a_i\\,X_i+b$ 的動差母函數等於 $e^{bt}$ 與各項動差母函數在 $a_i\\,t$ 之處的值連乘，求出來之後再由 mgf 的唯一性認出分配即可。本篇最後兩道例題即以此求出兩個獨立離散變數之和的機率函數，以及三個獨立同分配變數之和的期望值與變異數。"
---

[上一篇](/teaching-topics/many-to-many-transformations/)介紹了維度相同的多對多函數轉換: 離散型以 pmf 法解聯立方程式，把原變數以新變數表示；連續型則以 Jacobian 法把原變數的 pdf 以新變數表示，再乘上體積轉換因子的絕對值。兩者求得的都是轉換後的聯合分配。

本篇處理的是另一種需求，也就是轉換之後我們只要其中一個變數的邊際分配。前半先說明多對一的處理流程，即先作一個維度相同的轉換，再把不需要的變數積分掉，並以兩道例題示範；後半則指出當轉換是線性的，且各個變數彼此獨立時，[Theorem 3.23](#thm-mgf-two-to-one) 可以直接由各項的 mgf 求出線性組合的 mgf，最後以兩道例題示範這條路。

## [隨機變數](/teaching-topics/random-variables-and-pmf/#def-random-variable)的多對一函數轉換

有的時候，我們或許不是要求函數轉換後的聯合分配，而是求函數轉換後的多個變數中，其一的邊際分配。

這個時候比較直觀的作法是，一樣假設多對多 (維度相同) 的函數轉換，如同 [Example 3.51](/teaching-topics/many-to-many-transformations/#ex-integral-one-variable) 一樣，隨後再將轉換完後不需要的變數給積分掉，從而得到這個目標變數單獨的邊際分配。

綜觀來看，這是一個多對一的函數轉換問題，其流程如下:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\boxed{f_{\sssig X_1X_2}(x_1,x_2)}\ \Longrightarrow\ \boxed{f_{\sssig Y_1Y_2}(y_1,y_2)}\ \Longrightarrow\ \boxed{f_{\sssig Y_1}(y_1)}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\boxed{f_{\sssig X_1X_2}(x_1,x_2)}\\[0.55em]
\Longrightarrow\ \boxed{f_{\sssig Y_1Y_2}(y_1,y_2)}\\[0.55em]
\Longrightarrow\ \boxed{f_{\sssig Y_1}(y_1)}
\end{gathered}
$$

</div>

而這個流程所需要使用的技巧我們已經全部學會，見下列例題。

<div id="ex-integral-one-variable-many-to-one" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.51 <span lang="en">(Continued)</span></div>

<div lang="en" markdown="1">
Suppose that $X$ and $Y$ are continuous random variables whose joint probability density function is

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig XY}(x,y)=
\left\lbrace
\begin{array}{c@{\quad}l}
24xy, & 0<x<1,\ 0<y<1,\ x+y<1\\[0.8em]
0, & \text{o.w.}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
f_{\sssig XY}(x,y)=\\[0.45em]
\left\lbrace
\begin{array}{c@{\quad}l}
24xy, & 0<x<1,\ 0<y<1,\\[0.2em]
& x+y<1\\[0.8em]
0, & \text{o.w.}
\end{array}
\right.
\end{gathered}
$$

</div>

<ol class="topic-list-paren topic-list-paren--start-2">
  <li>Determine the marginal probability density function of <span class="text-nowrap">$Z$.</span></li>
</ol>
</div>

(2) 由 (1) 已知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig ZW}(z,w)=24w(z-w)\cdot\bigl\lvert-1\bigr\rvert=24w(z-w),\ 0<w<1,\ 0<z<1,\ w<z
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&f_{\sssig ZW}(z,w)=24w(z-w)\cdot\bigl\lvert-1\bigr\rvert\\[0.45em]
&\quad =24w(z-w),\\[0.2em]
&\qquad\quad 0<w<1,\ 0<z<1,\ w<z
\end{aligned}
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\Longrightarrow\ f_{\sssig Z}(z)=\int_{0}^{z}f_{\sssig ZW}(z,w)\,dw=24\int_{0}^{z}\bigl(zw-w^{2}\bigr)\,dw=4z^{3},\ 0<z<1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\Longrightarrow\ f_{\sssig Z}(z)=\int_{0}^{z}f_{\sssig ZW}(z,w)\,dw\\[0.45em]
&\quad =24\int_{0}^{z}\bigl(zw-w^{2}\bigr)\,dw\\[0.45em]
&\quad =4z^{3},\ 0<z<1
\end{aligned}
$$

</div>

</div>

<div id="ex-iid-sum-transformation" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.54</div>

<div lang="en" markdown="1">
Suppose that $X_1$ and $X_2$ are independent and identically distributed random variables whose common probability density function is

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
e^{-x}, & x>0\\[0.8em]
0, & \text{o.w.}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
f_{\sssig X}(x)=\\[0.45em]
\left\lbrace
\begin{array}{c@{\quad}l}
e^{-x}, & x>0\\[0.8em]
0, & \text{o.w.}
\end{array}
\right.
\end{gathered}
$$

</div>

<ol class="topic-list-paren">
  <li>Setting $Y_1=X_1+X_2$ and <span class="text-nowrap">$Y_2=\frac{X_1}{\,X_1+X_2\,}$,</span> determine the joint pdf of $Y_1$ and <span class="text-nowrap">$Y_2$.</span></li>
  <li>Find the marginal pdf of $Y_1$ and the marginal pdf of <span class="text-nowrap">$Y_2$.</span></li>
</ol>
</div>

(1) 先將轉換式反解，可得
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
Y_1=X_1+X_2,\ \ Y_2=\frac{X_1}{\,X_1+X_2\,}\ \Longrightarrow\ X_1=Y_1Y_2,\ \ X_2=Y_1-Y_1Y_2
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&Y_1=X_1+X_2,\ \ Y_2=\frac{X_1}{\,X_1+X_2\,}\\[0.45em]
&\quad \Longrightarrow\ X_1=Y_1Y_2,\ \ X_2=Y_1-Y_1Y_2
\end{aligned}
$$

</div>

接著依 Jacobian 法可知
{: .topic-paren-cont}

<!-- errata-pending: 下面這一式的括號，書稿 mathstatch3.tex 第 4656 行原文作
     $f_{\sssig X_1X_2}\big(y_1y_2, y_1-y_1y_2)\big)$，左括號只有一個而右括號有兩個，
     網頁補正為一對。待登錄 ERRATA.md，請作者裁定條號。 -->

$$
f_{\sssig Y_1Y_2}(y_1,y_2)=f_{\sssig X_1X_2}\bigl(y_1y_2,\ y_1-y_1y_2\bigr)\bigl\lvert\mathbf{J}\bigr\rvert
$$

其中
{: .topic-paren-cont}

<!-- errata-pending: 下面這個行列式的四個元素，書稿 mathstatch3.tex 第 4657 行原文作
     $\frac{dy_1y_2}{dy_1}$、$\frac{dy_1y_2}{dy_2}$、$\frac{d(y_1-y_1y_2)}{dy_1}$ 與
     $\frac{d(y_1-y_1y_2)}{dy_2}$，用的是全微分的 $d$。此處被微分的 $y_1y_2$ 與
     $y_1-y_1y_2$ 都是 $y_1$ 與 $y_2$ 兩個變數的函數，Jacobian 行列式的元素必須是偏微分，
     故網頁一律改為 $\partial$；書稿第 4363 行的 Jacobian 一般式與第 4466 行 (網頁篇 24)
     本來就寫 $\partial$，只有此處寫成 $d$。另書稿第一列的分子 $dy_1y_2$ 沒有加括號、第二列的 $d(y_1-y_1y_2)$ 卻有，
     網頁一併補齊為 $\partial(y_1y_2)$，使同一個行列式之內的寫法一致。
     待登錄 ERRATA.md，請作者裁定條號。 -->

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbf{J}=
\left\lvert
\begin{array}{cc}
\dfrac{\partial(y_1y_2)}{\partial y_1} & \dfrac{\partial(y_1y_2)}{\partial y_2}\\[0.8em]
\dfrac{\partial(y_1-y_1y_2)}{\partial y_1} & \dfrac{\partial(y_1-y_1y_2)}{\partial y_2}
\end{array}
\right\rvert=
\left\lvert
\begin{array}{cc}
y_2 & y_1\\[0.35em]
1-y_2 & -y_1
\end{array}
\right\rvert=-y_1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbf{J}&=
\left\lvert
\begin{array}{cc}
\dfrac{\partial(y_1y_2)}{\partial y_1} & \dfrac{\partial(y_1y_2)}{\partial y_2}\\[0.8em]
\dfrac{\partial(y_1-y_1y_2)}{\partial y_1} & \dfrac{\partial(y_1-y_1y_2)}{\partial y_2}
\end{array}
\right\rvert\\[0.55em]
&=
\left\lvert
\begin{array}{cc}
y_2 & y_1\\[0.35em]
1-y_2 & -y_1
\end{array}
\right\rvert=-y_1
\end{aligned}
$$

</div>

由此可得
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\Longrightarrow\ f_{\sssig Y_1Y_2}(y_1,y_2)=e^{-y_1y_2}e^{-(y_1-y_1y_2)}\cdot\bigl\lvert-y_1\bigr\rvert=y_1e^{-y_1},\ y_1>0,\ 0<y_2<1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\Longrightarrow\ f_{\sssig Y_1Y_2}(y_1,y_2)\\[0.45em]
&\quad =e^{-y_1y_2}e^{-(y_1-y_1y_2)}\cdot\bigl\lvert-y_1\bigr\rvert\\[0.45em]
&\quad =y_1e^{-y_1},\ y_1>0,\ 0<y_2<1
\end{aligned}
$$

</div>

(2) 由 (1) 已知
{: .topic-paren-item}

<!-- errata-pending: 下面這一式的範圍，書稿 mathstatch3.tex 第 4663 行原文作
     $f_{\sssig Y_1Y_2}(y_1, y_2) = y_1e^{-y_1}, \ 0<w<1, \ y_1>0, \ 0<y_2<1$，
     其中的 $0<w<1$ 是前一道例題 (書稿第 4635 行的 $f_{\sssig ZW}$) 留下來的，
     本題根本沒有 $w$ 這個變數。網頁刪去該段範圍，其餘照書稿原文。
     待登錄 ERRATA.md，請作者裁定條號。 -->

$$
f_{\sssig Y_1Y_2}(y_1,y_2)=y_1e^{-y_1},\ y_1>0,\ 0<y_2<1
$$

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\Longrightarrow\ f_{\sssig Y_1}(y_1)=\int_{0}^{1}f_{\sssig Y_1Y_2}(y_1,y_2)\,dy_2=\int_{0}^{1}y_1e^{-y_1}\,dy_2=y_1e^{-y_1},\ y_1>0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\Longrightarrow\ f_{\sssig Y_1}(y_1)=\int_{0}^{1}f_{\sssig Y_1Y_2}(y_1,y_2)\,dy_2\\[0.45em]
&\quad =\int_{0}^{1}y_1e^{-y_1}\,dy_2=y_1e^{-y_1},\ y_1>0
\end{aligned}
$$

</div>

<!-- 書稿體例不一致: 下面這一式的被積函數，書稿 mathstatch3.tex 第 4666 行寫作
     $f_{Y_1Y_2}(y_1, y_2)$，漏了下標的 \sssig 巨集，與同一題第 4658 行、第 4664 行的
     $f_{\sssig Y_1Y_2}$ 不一致，同一個符號會排成兩種字級，網頁一律補上。
     此處只是巨集漏寫，不涉及數學內容，登錄 ERRATA.md 或 STATUS.md 請作者裁定。 -->

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ f_{\sssig Y_2}(y_2)&=\int_{0}^{\infty}f_{\sssig Y_1Y_2}(y_1,y_2)\,dy_1=\int_{0}^{\infty}y_1^{2-1}e^{-\frac{y_1}{1}}\,dy_1\\[0.45em]
&=1^{2}\,\Gamma(2)=1,\ 0<y_2<1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\Longrightarrow\ f_{\sssig Y_2}(y_2)=\int_{0}^{\infty}f_{\sssig Y_1Y_2}(y_1,y_2)\,dy_1\\[0.45em]
&\quad =\int_{0}^{\infty}y_1^{2-1}e^{-\frac{y_1}{1}}\,dy_1\\[0.45em]
&\quad =1^{2}\,\Gamma(2)=1,\ 0<y_2<1
\end{aligned}
$$

</div>

</div>

## 線性組合的[動差母函數](/teaching-topics/moment-generating-functions/#def-mgf)

多轉一的隨機變數變換問題，如果是線性的變換且變數彼此獨立，我們可以由 mgf 法求得其轉換後的結果，見下列定理。

<div id="thm-mgf-two-to-one" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 3.23 (線性組合的動差母函數, mgf of a linear combination)</div>

若 $X_1, \ldots, X_n$ 為 $n$ 獨立變數，且 $a_1, \ldots, a_n, b$ 為實數，若令 $W$ $=$ <span class="text-nowrap">$\sum_{i=1}^{n}a_i\,X_i+b$，</span>則

$$
M_{\sssig W}(t)=e^{bt}\,\prod_{i=1}^{n}M_{\sssig X_i}(a_i\,t)
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.**

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{\sssig W}(t)&=\mathbb{E}\bigl(e^{tW}\bigr)=\mathbb{E}\Bigl[e^{t\bigl(\sum_{i=1}^{n}a_i\,X_i+b\bigr)}\Bigr]\\[0.45em]
&=\mathbb{E}\Bigl[\,e^{(a_1\,t)X_1+\cdots+(a_n\,t)X_n+bt}\,\Bigr]=\mathbb{E}\Bigl[\,e^{(a_1\,t)X_1}\cdots e^{(a_n\,t)X_n}\,e^{bt}\,\Bigr]\\[0.45em]
&=e^{bt}\,\mathbb{E}\bigl[e^{(a_1\,t)X_1}\bigr]\cdots\mathbb{E}\bigl[e^{(a_n\,t)X_n}\bigr]=e^{bt}\,\prod_{i=1}^{n}M_{\sssig X_i}(a_i\,t)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&M_{\sssig W}(t)=\mathbb{E}\bigl(e^{tW}\bigr)\\[0.45em]
&\quad =\mathbb{E}\Bigl[e^{t\bigl(\sum_{i=1}^{n}a_i\,X_i+b\bigr)}\Bigr]\\[0.45em]
&\quad =\mathbb{E}\Bigl[\,e^{(a_1\,t)X_1+\cdots+(a_n\,t)X_n+bt}\,\Bigr]\\[0.45em]
&\quad =\mathbb{E}\Bigl[\,e^{(a_1\,t)X_1}\cdots e^{(a_n\,t)X_n}\,e^{bt}\,\Bigr]\\[0.45em]
&\quad =e^{bt}\,\mathbb{E}\bigl[e^{(a_1\,t)X_1}\bigr]\cdots\mathbb{E}\bigl[e^{(a_n\,t)X_n}\bigr]\\[0.45em]
&\quad =e^{bt}\,\prod_{i=1}^{n}M_{\sssig X_i}(a_i\,t)
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

事實上，[Theorem 3.23](#thm-mgf-two-to-one) 就是 [Theorem 2.39](/teaching-topics/one-to-one-transformations/#thm-mgf-linear-transformation) 的延伸版本，只不過利用了 $X_1, \ldots, X_n$ 彼此獨立的特性，將分項相乘的[期望值](/teaching-topics/expectation/#def-expectation)，改為先取期望值再相乘，進而變成一個多轉一的方法。

</div>

<div id="ex-mgf-discrete-sum" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.55</div>

<div lang="en" markdown="1">
Suppose that $X$ and $Y$ are independent random variables, that the moment generating function of $X$ is

$$
M_{\sssig X}(t)=\frac{1}{4}\bigl(e^{t}+e^{2t}+e^{3t}+e^{4t}\bigr)
$$

and that the moment generating function of $Y$ is

$$
M_{\sssig Y}(t)=\frac{1}{3}\bigl(e^{t}+e^{2t}+e^{3t}\bigr)
$$

and let <span class="text-nowrap">$W=X+Y$.</span>

<ol class="topic-list-paren">
  <li>Determine the moment generating function of <span class="text-nowrap">$W$.</span></li>
  <li>Find the probability function of <span class="text-nowrap">$W$.</span></li>
</ol>
</div>

(1) 由於 <span class="text-nowrap">$X\indep Y$，</span>故可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{\sssig W}(t)&=M_{\sssig X}(t)\,M_{\sssig Y}(t)=\frac{1}{4}\bigl(e^{t}+e^{2t}+e^{3t}+e^{4t}\bigr)\times\frac{1}{3}\bigl(e^{t}+e^{2t}+e^{3t}\bigr)\\[0.45em]
&=\frac{1}{12}\bigl(e^{2t}+2e^{3t}+3e^{4t}+3e^{5t}+2e^{6t}+e^{7t}\bigr)\\[0.45em]
&=\frac{1}{12}e^{2t}+\frac{2}{12}e^{3t}+\frac{3}{12}e^{4t}+\frac{3}{12}e^{5t}+\frac{2}{12}e^{6t}+\frac{1}{12}e^{7t},\ t\in\mathbb{R}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&M_{\sssig W}(t)=M_{\sssig X}(t)\,M_{\sssig Y}(t)\\[0.45em]
&\quad =\frac{1}{4}\bigl(e^{t}+e^{2t}+e^{3t}+e^{4t}\bigr)\\[0.2em]
&\qquad\quad \times\frac{1}{3}\bigl(e^{t}+e^{2t}+e^{3t}\bigr)\\[0.45em]
&\quad =\frac{1}{12}\bigl(e^{2t}+2e^{3t}+3e^{4t}\\[0.2em]
&\qquad\quad +3e^{5t}+2e^{6t}+e^{7t}\bigr)\\[0.45em]
&\quad =\frac{1}{12}e^{2t}+\frac{2}{12}e^{3t}+\frac{3}{12}e^{4t}\\[0.2em]
&\qquad\quad +\frac{3}{12}e^{5t}+\frac{2}{12}e^{6t}+\frac{1}{12}e^{7t},\\[0.2em]
&\qquad\quad t\in\mathbb{R}
\end{aligned}
$$

</div>

(2) 由 [mgf 的唯一性](/teaching-topics/uniqueness-of-the-mgf/#thm-mgf-uniqueness)可知
{: .topic-paren-item}

$$
p_{\sssig W}(w)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{1}{12}, & w=2,\ 7\\[0.9em]
\dfrac{2}{12}, & w=3,\ 6\\[0.9em]
\dfrac{3}{12}, & w=4,\ 5\\[0.9em]
0, & \text{o.w.}
\end{array}
\right.
$$

</div>

<div id="ex-poisson-mgf-sum" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.56</div>

<div lang="en" markdown="1">
Suppose that <span class="text-nowrap">$X_1$,</span> $X_2$ and $X_3$ are independent and identically distributed random variables whose common moment generating function is $M_{\sssig X}(t)=e^{e^{t}-1}$ for every <span class="text-nowrap">$t\in\mathbb{R}$,</span> and let <span class="text-nowrap">$Y=X_1+X_2+X_3$.</span>

<ol class="topic-list-paren">
  <li>List the probability mass function of <span class="text-nowrap">$X_1$.</span></li>
  <li>Evaluate the probability <span class="text-nowrap">$\mathbb{P}(Y=0)$.</span></li>
  <li>Determine the mean and the variance of <span class="text-nowrap">$Y$.</span></li>
</ol>
</div>

(1) 由 [mgf 的唯一性](/teaching-topics/uniqueness-of-the-mgf/#thm-mgf-uniqueness)可知 $X_1, X_2, X_3$ $\overset{\mathrm{iid}}{\sim}$ <span class="text-nowrap">$\mathrm{Poi}(\lambda=1)$，</span>故
{: .topic-paren-item}

$$
f_{\sssig X_1}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{\,e^{-1}1^{x}\,}{x!}, & x=0,\ 1,\ 2,\ \ldots\\[0.9em]
0, & \text{otherwise}
\end{array}
\right.
$$

<!-- ref-point: 待第四章的卜瓦松分配主題發布後，將本題解答中首次出現的 $\mathrm{Poi}(\lambda)$ 改為指向該篇的站內連結。 -->

(2) $M_{\sssig Y}(t)$ $=$ $M_{\sssig X_1}(t)\,M_{\sssig X_2}(t)\,M_{\sssig X_3}(t)$ $=$ <span class="text-nowrap">$e^{3(e^{t}-1)}$,</span> for all $t\in\mathbb{R}$
{: .topic-paren-item}

由 [mgf 的唯一性](/teaching-topics/uniqueness-of-the-mgf/#thm-mgf-uniqueness)可知 $Y=X_1+X_2+X_3$ $\sim$ <span class="text-nowrap">$\mathrm{Poi}(\lambda=1+1+1=3)$，</span>故可知
{: .topic-paren-cont}

$$
f_{\sssig Y}(y)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{\,e^{-3}3^{y}\,}{y!}, & y=0,\ 1,\ 2,\ \ldots\\[0.9em]
0, & \text{otherwise}
\end{array}
\right.
$$

則所求為
{: .topic-paren-cont}

$$
\mathbb{P}(Y=0)=\frac{\,e^{-3}3^{0}\,}{0!}=e^{-3}
$$

(3) 由 (2) 可知 <span class="text-nowrap">$Y\sim\mathrm{Poi}(\lambda=3)$，</span>則
{: .topic-paren-item}

$$
\mathbb{E}(Y)=\mathrm{Var}(Y)=\lambda=3
$$

</div>

## 本篇小結

多對一的函數轉換並不需要新的工具。作法是先照樣假設一個維度相同的多對多轉換，求出轉換後的聯合 pdf，再把不需要的那個變數積分掉，剩下的就是我們所要的那一個變數的邊際 pdf。[Example 3.51 <span lang="en">(Continued)</span>](#ex-integral-one-variable-many-to-one) 承接前一篇已經求得的 $f_{\sssig ZW}(z,w)$ $=$ <span class="text-nowrap">$24w(z-w)$，</span>把 $w$ 自 $0$ 積到 $z$ 便得到 <span class="text-nowrap">$f_{\sssig Z}(z)=4z^{3}$；</span>[Example 3.54](#ex-iid-sum-transformation) 則先反解出 $X_1=Y_1Y_2$ 與 <span class="text-nowrap">$X_2=Y_1-Y_1Y_2$，</span>算得 Jacobian 為 <span class="text-nowrap">$-y_1$，</span>得到聯合 pdf $y_1e^{-y_1}$ 之後，各積掉另一個變數，分別求得 $f_{\sssig Y_1}(y_1)=y_1e^{-y_1}$ 與 $f_{\sssig Y_2}(y_2)=1$ 這兩個邊際 pdf，其中後者的積分用到了伽瑪函數。

當轉換是線性的，而且各個變數彼此獨立時，另有一條不必動用積分的路。[Theorem 3.23](#thm-mgf-two-to-one) 指出 $W$ $=$ $\sum_{i=1}^{n}a_i\,X_i+b$ 的動差母函數是 $e^{bt}$ <span class="text-nowrap">$\prod_{i=1}^{n}M_{\sssig X_i}(a_i\,t)$，</span>證明只有兩個關鍵步驟。先把指數上的加總拆成各項相乘，再由獨立性把乘積的期望值改寫成期望值的乘積。常數項 $e^{bt}$ 則直接提到外面。它與單變數的 [Theorem 2.39](/teaching-topics/one-to-one-transformations/#thm-mgf-linear-transformation) 是同一件事的延伸版本，差別只在多了「先取期望值再相乘」這一步。

兩道例題示範這條路怎麼走。[Example 3.55](#ex-mgf-discrete-sum) 把兩個獨立變數的 mgf 直接相乘，再把乘開後的六項各自看成一個機率乘上 <span class="text-nowrap">$e^{wt}$，</span>由 [mgf 的唯一性](/teaching-topics/uniqueness-of-the-mgf/#thm-mgf-uniqueness)即可把 $W$ 的機率函數完整寫出來。[Example 3.56](#ex-poisson-mgf-sum) 反過來由 mgf 認出各項的分配，三項相乘之後所得的 $e^{3(e^{t}-1)}$ 仍是同一個分配族的 mgf，只是參數由 $1$ 變成 <span class="text-nowrap">$3$，</span>因而不必再算積分或加總，直接就能寫出 $\mathbb{P}(Y=0)=e^{-3}$ 以及 $Y$ 的期望值與[變異數](/teaching-topics/variance/#def-variance)。兩題所倚靠的都是同一件事，線性組合的 mgf 算得出來，分配就認得出來。

[下一篇](/teaching-topics/mgf-method-examples/)將以三道例題繼續示範 mgf 法在多轉一問題上的用法。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
