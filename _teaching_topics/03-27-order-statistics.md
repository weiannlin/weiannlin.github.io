---
title: "順序統計量的定義"
subtitle: "The Definition of Order Statistics"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 27
order: 327
permalink: /lecture-notes/order-statistics/
date: 2026-08-13
published: true
excerpt: "將一組隨機變數依數值由小到大排序所得的序列稱為順序統計量。本篇說明如何由排列對稱性與多對多函數轉換求取順序統計量的聯合分配，並以三道例題演練極值與排序機率的計算。"
---

[上一篇](/lecture-notes/mgf-method-examples/)以三道例題示範了[動差母函數](/lecture-notes/moment-generating-functions/#def-mgf)法的用法，其中最後一道例題的第三小題求的是獨立均勻樣本中最大者的分配，該篇末尾的註記便由此指出，「取排序後最大者」是一種多轉一的轉換。

本篇先以 [Definition 3.21](#def-order-stat) 給出順序統計量，接著以兩道例題示範最小值與最大值的[聯合機率密度函數](/lecture-notes/joint-probability-density-functions/#def-joint-pdf)該怎麼求，說明為什麼必須先把所有可能的大小順序逐一列出，各自以 [Jacobian 法](/lecture-notes/many-to-many-transformations/#連續型的-jacobian-法)轉換之後再行加總，最後以一道例題說明隨機樣本的對稱性如何把排序的問題轉為排列組合的問題。

將一組隨機樣本依數值由小到大重新排列，本身即構成一種函數轉換；轉換後所得的有序隨機變數稱為**順序統計量 <span lang="en">(order statistics)</span>**。

## 順序統計量的定義

<div id="def-order-stat" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 3.21 (順序統計量, order statistics)</div>

假設 $X_1,\ldots,X_n$ 為一組[隨機變數](/lecture-notes/random-variables-and-pmf/#def-random-variable)，且

$$
X_{\sssig (1)}\leqslant X_{\sssig (2)}\leqslant\cdots\leqslant X_{\sssig (n)}
$$

為 $X_1,\ldots,X_n$ 之一組重排，則稱 $X_{\sssig (1)}$ $\leqslant$ $X_{\sssig (2)}$ $\leqslant\cdots\leqslant$ $X_{\sssig (n)}$ 為該組隨機變數的**順序統計量**，通常另訂

$$
Y_1=X_{\sssig (1)},\ Y_2=X_{\sssig (2)},\ \ldots,\ Y_n=X_{\sssig (n)}
$$

表示該組隨機變數的順序統計量。

</div>

順序統計量將一組隨機變數依數值大小重排，故恆滿足遞增的大小關係。實務與推論上最常關注樣本最小值 $Y\_1=X\_{\sssig (1)}=\min\lbrace X\_1,\ldots,X\_n\rbrace$ 與最大值 $Y\_n=X\_{\sssig (n)}=\max\lbrace X\_1,\ldots,X\_n\rbrace$ 這兩個極端值，同時也常需要求取任意兩個順序統計量的聯合分配。以下先透過例題說明其求法。

## 最小值與最大值的聯合機率密度函數

<div id="ex-order-statistics-joint-pdf" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.60</div>

<div lang="en" markdown="1">
Let $X$ and $Y$ have joint probability density function

$$
f_{\sssig XY}(x,y)=\frac{\,12\,}{7}x(x+y),\quad 0<x,y<1
$$

and let $U=\min(X,Y)$ and <span class="text-nowrap">$V=\max(X,Y)$.</span> Find the joint probability density function of <span class="text-nowrap">$(U,V)$.</span>
</div>

樣本排序可分為 $X>Y$ 與 $X<Y$ 兩種狀況，故以下分列之

[$X>Y$]

$$
\left\lbrace
\begin{array}{l}
U=Y\\[0.35em]
V=X
\end{array}
\right.
\Longrightarrow
\left\lbrace
\begin{array}{l}
X=V\\[0.35em]
Y=U
\end{array}
\right.
$$

$$
\text{且}\ \ \mathbf{J}=
\left\lvert
\begin{array}{cc}
\dfrac{\partial x}{\partial u} & \dfrac{\partial x}{\partial v}\\[0.8em]
\dfrac{\partial y}{\partial u} & \dfrac{\partial y}{\partial v}
\end{array}
\right\rvert=
\left\lvert
\begin{array}{cc}
0 & 1\\[0.35em]
1 & 0
\end{array}
\right\rvert=-1
$$

則可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig UV}^{*}(u,v)=f_{\sssig XY}(v,u)\lvert\mathbf{J}\rvert=\frac{\,12\,}{7}v(v+u),\ 0<u<v<1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig UV}^{*}(u,v)&=f_{\sssig XY}(v,u)\lvert\mathbf{J}\rvert\\[0.45em]
&=\frac{\,12\,}{7}v(v+u),\ 0<u<v<1
\end{aligned}
$$

</div>

[$X<Y$]

$$
\left\lbrace
\begin{array}{l}
U=X\\[0.35em]
V=Y
\end{array}
\right.
\Longrightarrow
\left\lbrace
\begin{array}{l}
X=U\\[0.35em]
Y=V
\end{array}
\right.
$$

$$
\text{且}\ \ \mathbf{J}=
\left\lvert
\begin{array}{cc}
\dfrac{\partial x}{\partial u} & \dfrac{\partial x}{\partial v}\\[0.8em]
\dfrac{\partial y}{\partial u} & \dfrac{\partial y}{\partial v}
\end{array}
\right\rvert=
\left\lvert
\begin{array}{cc}
1 & 0\\[0.35em]
0 & 1
\end{array}
\right\rvert=1
$$

則可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig UV}^{**}(u,v)=f_{\sssig XY}(u,v)\lvert\mathbf{J}\rvert=\frac{\,12\,}{7}u(u+v),\ 0<u<v<1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig UV}^{**}(u,v)&=f_{\sssig XY}(u,v)\lvert\mathbf{J}\rvert\\[0.45em]
&=\frac{\,12\,}{7}u(u+v),\ 0<u<v<1
\end{aligned}
$$

</div>

<div class="topic-math-follow" markdown="1">

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\Longrightarrow\ \ f_{\sssig UV}(u,v)=f_{\sssig UV}^{*}(u,v)+f_{\sssig UV}^{**}(u,v)=\frac{\,12\,}{7}(u+v)^{2},\ 0<u<v<1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ \ f_{\sssig UV}(u,v)&=f_{\sssig UV}^{*}(u,v)+f_{\sssig UV}^{**}(u,v)\\[0.45em]
&=\frac{\,12\,}{7}(u+v)^{2},\ 0<u<v<1
\end{aligned}
$$

</div>

</div>

</div>

<div id="ex-order-statistics-independent-pair" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.61</div>

<div lang="en" markdown="1">
Let $X$ and $Y$ be independent random variables with probability density functions

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X}(x)=2x,\ 0<x<1\quad\text{and}\quad f_{\sssig Y}(y)=3y^{2},\ 0<y<1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
f_{\sssig X}(x)=2x,\ 0<x<1\\[0.55em]
\text{and}\quad f_{\sssig Y}(y)=3y^{2},\ 0<y<1
\end{gathered}
$$

</div>

respectively. Find the joint probability density function of <span class="text-nowrap">$(U,V)$,</span> where $U=\min(X,Y)$ and <span class="text-nowrap">$V=\max(X,Y)$.</span>
</div>

由 $X$ $\indep$ $Y$ 可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig XY}(x,y)=f_{\sssig X}(x)\,f_{\sssig Y}(y)=2x\,3y^{2}=6xy^{2},\ 0<x,y<1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig XY}(x,y)&=f_{\sssig X}(x)\,f_{\sssig Y}(y)\\[0.45em]
&=2x\,3y^{2}=6xy^{2},\ 0<x,y<1
\end{aligned}
$$

</div>

又樣本排序可分為 $X>Y$ 與 $X<Y$ 兩種狀況，故以下分列之

[$X>Y$]

$$
\left\lbrace
\begin{array}{l}
U=Y\\[0.35em]
V=X
\end{array}
\right.
\Longrightarrow
\left\lbrace
\begin{array}{l}
X=V\\[0.35em]
Y=U
\end{array}
\right.
$$

$$
\text{且}\ \ \mathbf{J}=
\left\lvert
\begin{array}{cc}
\dfrac{\partial x}{\partial u} & \dfrac{\partial x}{\partial v}\\[0.8em]
\dfrac{\partial y}{\partial u} & \dfrac{\partial y}{\partial v}
\end{array}
\right\rvert=
\left\lvert
\begin{array}{cc}
0 & 1\\[0.35em]
1 & 0
\end{array}
\right\rvert=-1
$$

則可知

$$
f_{\sssig UV}^{*}(u,v)=f_{\sssig XY}(v,u)\lvert\mathbf{J}\rvert=6vu^{2},\ 0<u<v<1
$$

[$X<Y$]

$$
\left\lbrace
\begin{array}{l}
U=X\\[0.35em]
V=Y
\end{array}
\right.
\Longrightarrow
\left\lbrace
\begin{array}{l}
X=U\\[0.35em]
Y=V
\end{array}
\right.
$$

$$
\text{且}\ \ \mathbf{J}=
\left\lvert
\begin{array}{cc}
\dfrac{\partial x}{\partial u} & \dfrac{\partial x}{\partial v}\\[0.8em]
\dfrac{\partial y}{\partial u} & \dfrac{\partial y}{\partial v}
\end{array}
\right\rvert=
\left\lvert
\begin{array}{cc}
1 & 0\\[0.35em]
0 & 1
\end{array}
\right\rvert=1
$$

則可知

$$
f_{\sssig UV}^{**}(u,v)=f_{\sssig XY}(u,v)\lvert\mathbf{J}\rvert=6uv^{2},\ 0<u<v<1
$$

<div class="topic-math-follow" markdown="1">

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\Longrightarrow\ \ f_{\sssig UV}(u,v)=f_{\sssig UV}^{*}(u,v)+f_{\sssig UV}^{**}(u,v)=6uv(u+v),\ 0<u<v<1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ \ f_{\sssig UV}(u,v)&=f_{\sssig UV}^{*}(u,v)+f_{\sssig UV}^{**}(u,v)\\[0.45em]
&=6uv(u+v),\ 0<u<v<1
\end{aligned}
$$

</div>

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

求取一般聯合分配的順序統計量時，須先窮舉原隨機變數之間所有可能的大小順序，在各個順序區間內分別對應反解並套用 Jacobian 法轉換，最後再將各分支所得的機率密度相加。

當 $X\_1,\ldots,X\_n$ 為獨立同分配的隨機樣本時，由同分配的對稱性可知每種排列順序轉換後的密度函數完全相同，加總後僅差一個對應排列數的階乘倍數；隨機樣本的排序機率也因此可直接化為古典機率中的排列組合問題，見[下一題](#ex-three-iid-order-probability)。

</div>

## 隨機樣本的排序機率

<div id="ex-three-iid-order-probability" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.62</div>

<div lang="en" markdown="1">
Let <span class="text-nowrap">$X_1$,</span> <span class="text-nowrap">$X_2$,</span> and $X_3$ be independent and identically distributed continuous random variables.

<ol class="topic-list-paren">
  <li>Find <span class="text-nowrap">$\mathbb{P}(X_1>X_2\mid X_1>X_3)$.</span></li>
  <li>Find <span class="text-nowrap">$\mathbb{P}(X_1>X_2\mid X_1<X_3)$.</span></li>
</ol>
</div>

(1) 依照條件機率之定義，所求為
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X_1>X_2\mid X_1>X_3)=\frac{\,\mathbb{P}\bigl(\lbrace X_1>X_2\rbrace\cap\lbrace X_1>X_3\rbrace\bigr)\,}{\mathbb{P}(X_1>X_3)}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(X_1>X_2\mid X_1>X_3)\\[0.35em]
&=\frac{\,\mathbb{P}\bigl(\lbrace X_1>X_2\rbrace\cap\lbrace X_1>X_3\rbrace\bigr)\,}{\mathbb{P}(X_1>X_3)}
\end{aligned}
$$

</div>

其中，由於 $X_1, X_2, X_3$ 獨立且同分配，故知道
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}\bigl(\lbrace X_1>X_2\rbrace\cap\lbrace X_1>X_3\rbrace\bigr)=\frac{1}{\,3\,},\quad\mathbb{P}(X_1>X_3)=\frac{1}{\,2\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{P}\bigl(\lbrace X_1>X_2\rbrace\cap\lbrace X_1>X_3\rbrace\bigr)=\frac{1}{\,3\,},\\[0.55em]
\mathbb{P}(X_1>X_3)=\frac{1}{\,2\,}
\end{gathered}
$$

</div>

所求為
{: .topic-paren-cont}

$$
\mathbb{P}(X_1>X_2\mid X_1>X_3)=\frac{2}{\,3\,}
$$

(2) 依照條件機率之定義，所求為
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X_1>X_2\mid X_1<X_3)=\frac{\,\mathbb{P}(X_3>X_1>X_2)\,}{\mathbb{P}(X_1<X_3)}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X_1>X_2\mid X_1<X_3)&=\frac{\,\mathbb{P}(X_3>X_1>X_2)\,}{\mathbb{P}(X_1<X_3)}
\end{aligned}
$$

</div>

其中，由於 $X_1, X_2, X_3$ 獨立且同分配，故知道
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X_3>X_1>X_2)=\frac{1}{\,6\,},\quad\mathbb{P}(X_1<X_3)=\frac{1}{\,2\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{P}(X_3>X_1>X_2)=\frac{1}{\,6\,},\\[0.55em]
\mathbb{P}(X_1<X_3)=\frac{1}{\,2\,}
\end{gathered}
$$

</div>

所求為
{: .topic-paren-cont}

$$
\mathbb{P}(X_1>X_2\mid X_1<X_3)=\frac{1}{\,3\,}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

在 [Example 3.62](#ex-three-iid-order-probability) 中，即使未指定 $X\_1, X\_2, X\_3$ 的具體連續分配形式，仍可藉由獨立同分配的對稱性 (連續型隨機變數出現同值的機率為 <span class="text-nowrap">$0$，</span>$3!$ 種嚴格大小順序均等可能)，將排序問題化為排列數之比而求得機率。此對稱性亦使我們在[下一篇](/lecture-notes/order-statistics-distributions/)計算整套順序統計量的聯合分配時，無須逐一分案討論，僅須計入可能的排列數。

</div>

## 本篇小結

[Definition 3.21](#def-order-stat) 把一組隨機變數依大小重新排列。若 $X_{\sssig (1)}$ $\leqslant\cdots\leqslant$ $X_{\sssig (n)}$ 是 $X_1,\ldots,X_n$ 的一組重排，這一組新的隨機變數就是該組隨機變數的順序統計量，通常另以 $Y_1$ 到 $Y_n$ 表示。排序本身只是把大小關係固定下來，因此順序統計量之間的大小關係是一定的；其中最受關注的是最小的 $Y_1$ 與最大的 $Y_n$ 這兩個，但任意兩個順序統計量所組成的聯合分配同樣值得討論。

[Example 3.60](#ex-order-statistics-joint-pdf) 與 [Example 3.61](#ex-order-statistics-independent-pair) 求的都是 $U=\min(X,Y)$ 與 $V=\max(X,Y)$ 的聯合機率密度函數，作法也完全相同。先把 $X>Y$ 與 $X<Y$ 兩種大小順序分別列出，各自由 $U$ 與 $V$ 解回 $X$ 與 <span class="text-nowrap">$Y$、</span>算出 $\mathbf{J}$ 的值，代入 joint pdf 得到兩個轉換後的結果，最後把兩者相加。前一題的答案是 $\frac{\,12\,}{7}(u+v)^{2}$ 這個式子，後一題則先由 $X$ 與 $Y$ 獨立把 joint pdf 寫成兩個 marginal pdf 的乘積，答案是 $6uv(u+v)$ 這個式子，兩者的範圍都是 <span class="text-nowrap">$0<u<v<1$。</span>

兩道例題所示範的，是順序統計量在任意聯合分配之中都該有的作法。先討論順序的所有可能情況，逐一對應此時的每一個順序統計量是原本的哪一個隨機變數，分列轉換之後再行加總。而在隨機樣本的情況中，同分配的對稱性會使各種情況的結果完全變為同一個，加總因而只剩下一個與階乘有關的倍數，排序的問題也就成了古典機率中的排列組合問題。[Example 3.62](#ex-three-iid-order-probability) 正是如此。我們甚至不知道 $X_1, X_2, X_3$ 共同的分配是哪一個，只憑獨立且同分配所帶來的對稱性，就可以知道 $\mathbb{P}(X_1>X_2\mid X_1>X_3)$ 這個機率是 <span class="text-nowrap">$\frac{2}{\,3\,}$，</span>而 $\mathbb{P}(X_1>X_2\mid X_1<X_3)$ 這個機率是 <span class="text-nowrap">$\frac{1}{\,3\,}$。</span>

[下一篇](/lecture-notes/order-statistics-distributions/)便由這個對稱性出發，推導隨機樣本的整套順序統計量所具有的聯合機率密度函數，以及其中第 $i$ 個順序統計量的抽樣分配。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
