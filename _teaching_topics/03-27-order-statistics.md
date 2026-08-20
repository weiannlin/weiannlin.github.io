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
published: false
excerpt: "把一組隨機變數由小到大重新排列，所得的這一組新的隨機變數即為順序統計量，其中最受關注的是最小的 $Y_1$ 與最大的 $Y_n$ 這兩個。求兩個順序統計量的聯合機率密度函數時，必須先把所有可能的大小順序逐一列出，各自作一次函數轉換，再把各種情況的結果加總起來。而在隨機樣本的情況中，同分配的對稱性會使各種情況的結果完全相同，加總因而只剩下一個與階乘有關的倍數，排序的問題也就成了古典機率中的排列組合問題。本篇以三道例題示範這兩件事，其中最後一題甚至不需要知道共同的分配是哪一個，只憑對稱性即可求得機率。"
---

[上一篇](/lecture-notes/mgf-method-examples/)以三道例題示範了[動差母函數](/lecture-notes/moment-generating-functions/#def-mgf)法的用法，其中最後一道例題的第三小題求的是獨立均勻樣本中最大者的分配，該篇末尾的註記便由此指出，「取排序後最大者」是一種多轉一的轉換。

本篇先以 [Definition 3.21](#def-order-stat) 給出順序統計量，接著以兩道例題示範最小值與最大值的[聯合機率密度函數](/lecture-notes/joint-probability-density-functions/#def-joint-pdf)該怎麼求，說明為什麼必須先把所有可能的大小順序逐一列出，各自以 [Jacobian 法](/lecture-notes/many-to-many-transformations/#連續型的-jacobian-法)轉換之後再行加總，最後以一道例題說明隨機樣本的對稱性如何把排序的問題轉為排列組合的問題。

稍早我們曾經提過，「排序」其實也是一種函數轉換。這個小節所要探討的，便是這種特殊的函數轉換，我們稱之為**順序統計量 <span lang="en">(order statistics)</span>**，並且一併探討順序統計量在特定的母體中所對應的抽樣分配。

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

<!-- errata-pending: 下面這一句，書稿 mathstatch3.tex 第 5142 行原文作
     「順序統計量僅單純針地對一組隨機變數進行排序」，「針地對」三字語序倒置，
     應為「地針對」；網頁作「順序統計量僅單純地針對一組隨機變數進行排序」。
     同型前例為 C1-35 (「需要注意特別的」語序倒置)，屬 (1) 書稿有誤，
     待作者裁定後登錄 ERRATA.md。同一句在 mathstatch3supp.tex 第 5143 行重出。 -->

順序統計量僅單純地針對一組隨機變數進行排序，故其具有大小關係是一定的。

通常，比較重要的順序統計量，是樣本中最小的和最大的，也就是 $Y_1$ $=$ $X_{\sssig (1)}$ $=$ $\min\lbrace X_1,\ldots,X_n\rbrace$ 與 $Y_n$ $=$ $X_{\sssig (n)}$ $=$ $\max\lbrace X_1,\ldots,X_n\rbrace$ 二者，但我們也會關心其中任意兩個順序統計量所組成的聯合分配。下面便來看看這些順序統計量該具有什麼抽樣分配。

## 最小值與最大值的聯合機率密度函數

<div id="ex-order-statistics-joint-pdf" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.60</div>

<div lang="en" markdown="1">
Suppose that the random variables $X$ and $Y$ have the joint probability density function

$$
f_{\sssig XY}(x,y)=\frac{\,12\,}{7}x(x+y),\quad 0<x,y<1
$$

and let $U=\min(X,Y)$ and <span class="text-nowrap">$V=\max(X,Y)$.</span> Determine the joint probability density function of the pair <span class="text-nowrap">$(U,V)$.</span>
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
\dfrac{dx}{du} & \dfrac{dx}{dv}\\[0.8em]
\dfrac{dy}{du} & \dfrac{dy}{dv}
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
\dfrac{dx}{du} & \dfrac{dx}{dv}\\[0.8em]
\dfrac{dy}{du} & \dfrac{dy}{dv}
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
Suppose that $X$ and $Y$ are independent random variables whose probability density functions are

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X}(x)=2x,\ 0<x<1\quad\text{and}\quad f_{\sssig Y}(y)=3y^{2},\ 0<y<1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig X}(x)&=2x,\ 0<x<1\\[0.55em]
\text{and}\quad f_{\sssig Y}(y)&=3y^{2},\ 0<y<1
\end{aligned}
$$

</div>

respectively. Find the joint probability density function of the pair <span class="text-nowrap">$(U,V)$,</span> where $U=\min(X,Y)$ and <span class="text-nowrap">$V=\max(X,Y)$.</span>
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
\dfrac{dx}{du} & \dfrac{dx}{dv}\\[0.8em]
\dfrac{dy}{du} & \dfrac{dy}{dv}
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
\dfrac{dx}{du} & \dfrac{dx}{dv}\\[0.8em]
\dfrac{dy}{du} & \dfrac{dy}{dv}
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

順序統計量的原意是要討論隨機變數間，順序的可能情況，並逐一對應此時的每一個順序統計量，是原本的哪一個隨機變數，這一點在任意聯合分配中都應如此。

在討論所有的可能性後，我們應分列其結果進行轉換，再行加總而得到最後的聯合分配，就好像過去我們所遇到的，所有具有不同來源的情況一樣。

然而，在隨機樣本 (特指獨立且同分配) 的情況中，這些討論的結果，會因為同分配的對稱性而完全變為同一個結果，故再行加總的一步只會變成一定的倍數，而且這個倍數將與階乘 (即排列數) 有關。

事實上，隨機樣本的排序問題，通常都會被轉換為古典機率中的排列組合問題，見[下列這題](#ex-three-iid-order-probability)。

</div>

## 隨機樣本的排序機率

<div id="ex-three-iid-order-probability" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.62</div>

<div lang="en" markdown="1">
Suppose that <span class="text-nowrap">$X_1$,</span> $X_2$ and $X_3$ are independent and identically distributed continuous random variables.

<ol class="topic-list-paren">
  <li>Evaluate <span class="text-nowrap">$\mathbb{P}(X_1>X_2\mid X_1>X_3)$.</span></li>
  <li>Evaluate <span class="text-nowrap">$\mathbb{P}(X_1>X_2\mid X_1<X_3)$.</span></li>
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
\mathbb{P}(X_1>X_2\mid X_1>X_3)&=\frac{\,\mathbb{P}\bigl(\lbrace X_1>X_2\rbrace\cap\lbrace X_1>X_3\rbrace\bigr)\,}{\mathbb{P}(X_1>X_3)}
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
\begin{aligned}
\mathbb{P}\bigl(\lbrace X_1>X_2\rbrace\cap\lbrace X_1>X_3\rbrace\bigr)&=\frac{1}{\,3\,},\\[0.55em]
\mathbb{P}(X_1>X_3)&=\frac{1}{\,2\,}
\end{aligned}
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
\begin{aligned}
\mathbb{P}(X_3>X_1>X_2)&=\frac{1}{\,6\,},\\[0.55em]
\mathbb{P}(X_1<X_3)&=\frac{1}{\,2\,}
\end{aligned}
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

[上述問題](#ex-three-iid-order-probability)中，我們甚至不知道 $X_1, X_2, X_3$ 同分配的分配是何者，但藉由其獨立且同分配的特色，依照其對稱性，將排序的問題轉換為排列組合的問題，從而知道其機率。

這個概念在隨機樣本的順序統計量中格外重要，這是因為，隨機樣本的對稱性將允許我們在計算整套順序統計量的聯合分配時，省略掉非常多討論的步驟，而只需要討論其排列的可能數。

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
