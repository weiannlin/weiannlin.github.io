---
title: "獨立隨機變數"
subtitle: "Independent Random Variables"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 9
order: 309
permalink: /teaching-topics/independent-random-variables/
date: 2026-08-12
published: false
excerpt: "把條件機率密度函數的定義移項，就得到乘法原理的機率函數版本，也就是聯合機率密度函數等於條件機率密度函數與邊際機率密度函數的乘積。若條件機率密度函數與邊際機率密度函數相同，也就是一個變數的取值不影響另一個變數，則稱這兩個隨機變數獨立，記為 $X\\indep Y$ 這個符號，其等價寫法是聯合機率密度函數等於兩個邊際機率密度函數的乘積。實務上另有一個快速的判斷法: 聯合值域為積空間，且聯合機率密度函數可以拆成一個只含 $x$ 的函數與一個只含 $y$ 的函數之乘積，兩個條件同時滿足才與獨立等價。本篇以五道例題示範獨立與否的判定，最後一題並利用三個變數中兩組的獨立性，把條件機率化為一個面積佔比。"
---

[上一篇](/teaching-topics/conditional-distributions-examples/)以五道例題示範了[條件機率質量函數](/teaching-topics/conditional-distributions/#def-conditional-pmf)與[條件機率密度函數](/teaching-topics/conditional-distributions/#def-conditional-pdf)的求法，並把條件放寬到一整段範圍，得到截尾分配。這些例題所處理的，都是在另一個變數取定某個值或落在某個範圍之後，這個變數的機率分配會變成什麼樣子。

本篇處理的則是相反的情形。若這個條件完全沒有改變原本的機率分配，也就是條件機率密度函數與[邊際機率密度函數](/teaching-topics/marginal-probability-density-functions/#def-marginal-pdf)一模一樣，那會是什麼狀況。這正是第一章[事件的獨立](/teaching-topics/independence-and-conditional-independence/#definition-117)推廣到[隨機變數](/teaching-topics/random-variables-and-pmf/#def-random-variable)之後的樣子。在進入獨立的定義之前，我們先把條件機率密度函數的定義移項，得到乘法原理的機率函數版本。

## 乘法原理

<div id="thm-multiplication-rule-r-v" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 3.3 (乘法原理, multiplication rule)</div>

若 $(X,Y)$ 為二元隨機變數，joint pdf 為 <span class="text-nowrap">$f_{\sssig XY}(x,y)$，</span>且 conditional pdf 為 $f_{\sssig X\mid Y}(x\mid y)$ 及 <span class="text-nowrap">$f_{\sssig Y\mid X}(y\mid x)$，</span>marginal pdf 為 $f_{\sssig X}(x)$ 及 <span class="text-nowrap">$f_{\sssig Y}(y)$，</span>則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig XY}(x,y)=f_{\sssig X\mid Y}(x\mid y)\,f_{\sssig Y}(y)=f_{\sssig Y\mid X}(y\mid x)\,f_{\sssig X}(x)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig XY}(x,y)&=f_{\sssig X\mid Y}(x\mid y)\,f_{\sssig Y}(y)\\[0.45em]
&=f_{\sssig Y\mid X}(y\mid x)\,f_{\sssig X}(x)
\end{aligned}
$$

</div>

</div>

離散版本只要將其改為 pmf 即可。

這個定理即是第一章的 [Theorem 1.13](/teaching-topics/conditional-probability-information/#theorem-18) 的機率函數版本，二者的本質是一模一樣的，是由條件機率及條件機率函數的定義所轉化過來。

## 獨立隨機變數

<div id="def-indep-r-v" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 3.10 (獨立隨機變數, independent random variables)</div>

$X$ 與 $Y$ 是二個隨機變數，**$X$ 與 $Y$ 獨立 <span lang="en">(independent)</span>** 記為 <span class="text-nowrap">$X\indep Y$，</span>與以下等價:

<ol class="topic-list-paren topic-list-paren--math">
  <li>
$$
f_{\sssig X\mid Y}(x\mid y)=f_{\sssig X}(x),\ \forall (x,y)\in\mathcal{R}_{\sssig XY}
$$
  </li>
  <li>
$$
f_{\sssig Y\mid X}(y\mid x)=f_{\sssig Y}(y),\ \forall (x,y)\in\mathcal{R}_{\sssig XY}
$$
  </li>
  <li>
$$
f_{\sssig XY}(x,y)=f_{\sssig X}(x)\,f_{\sssig Y}(y),\ \forall (x,y)\in\mathcal{R}_{\sssig XY}
$$
  </li>
</ol>

</div>

獨立隨機變數有一些地方需要注意:

(1) 離散版本只要將其改為 pmf 即可。
{: .topic-paren-item}

(2) 在第一章探討[事件的獨立](/teaching-topics/independence-and-conditional-independence/#definition-117)時，我們曾理解為 **$A$ 的發生並不影響 $B$ 發生的機率**，推廣到隨機變數時，其直觀意義為 **$X$ (或 $Y$) 的值為多少並不影響 $Y$ (或 $X$) 的值**。
{: .topic-paren-item}

(3) 若事件 $\lbrace\,(X,Y)\in A\,\rbrace$ 可以拆解為 $\lbrace\,X\in A_{\sssig X}\,\rbrace$ $\times$ $\lbrace\,Y\in A_{\sssig Y}\,\rbrace$ 這樣的形式，且 <span class="text-nowrap">$X\indep Y$，</span>則
{: .topic-paren-item}

$$
\mathbb{P}\bigl((X,Y)\in A\bigr)=\mathbb{P}(X\in A_{\sssig X})\,\mathbb{P}(Y\in A_{\sssig Y})
$$

簡單的例子如下:
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(a<X<b,\ c<Y<d)&=\int_{c}^{d}\!\!\int_{a}^{b}f_{\sssig XY}(x,y)\,dx\,dy\\[0.45em]
&=\int_{c}^{d}\!\!\int_{a}^{b}f_{\sssig X}(x)\,f_{\sssig Y}(y)\,dx\,dy\\[0.45em]
&=\int_{a}^{b}f_{\sssig X}(x)\,dx\int_{c}^{d}f_{\sssig Y}(y)\,dy\\[0.45em]
&=\mathbb{P}(a<X<b)\,\mathbb{P}(c<Y<d)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(a<X<b,\ c<Y<d)&=\int_{c}^{d}\!\!\int_{a}^{b}f_{\sssig XY}(x,y)\,dx\,dy\\[0.45em]
&=\int_{c}^{d}\!\!\int_{a}^{b}f_{\sssig X}(x)\,f_{\sssig Y}(y)\,dx\,dy\\[0.45em]
&=\int_{a}^{b}f_{\sssig X}(x)\,dx\int_{c}^{d}f_{\sssig Y}(y)\,dy\\[0.45em]
&=\mathbb{P}(a<X<b)\,\mathbb{P}(c<Y<d)
\end{aligned}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

離散型隨機變數中，**機率列聯表的「每一格」若都等於該行與該列所在的邊際機率的乘積**，則該二個隨機變數為獨立，這個性質可以直接由上列定義推衍而得到。

機率列聯表中，每一格都是 <span class="text-nowrap">$p_{\sssig XY}(x,y)$，</span>而該格所對應的邊際機率應為 $p_{\sssig X}(x)$ 與 <span class="text-nowrap">$p_{\sssig Y}(y)$，</span>故由上列定義可知，若對所有 $(x,y)\in\mathcal{R}\_{\sssig XY}$ 皆有

$$
p_{\sssig XY}(x,y)=p_{\sssig X}(x)\,p_{\sssig Y}(y)
$$

則 <span class="text-nowrap">$X\indep Y$。</span>

</div>

(4) 我們可將上述定義擴展至 $n$ 個變數的獨立，即若 $X_1,X_2,\ldots,X_n$ 互相獨立，若且唯若
{: .topic-paren-item}

$$
f_{\sssig X_1\cdots X_n}(x_1,\ldots,x_n)=\prod_{i=1}^{n}f_{\sssig X_i}(x_i)
$$

(5) 事實上，我們可以快速判斷一組隨機變數是否獨立。即同時滿足以下條件，若且唯若 <span class="text-nowrap">$X\indep Y$:</span>
{: .topic-paren-item}

- 聯合值域 $\mathcal{R}\_{\sssig XY}$ 為積空間 (即二維矩形)
- <span class="text-nowrap">$f\_{\sssig XY}(x,y)=g(x)\,h(y)$，</span>其中 $g(x)$ 是僅有 $x$ 的函數、$h(y)$ 是僅有 $y$ 的函數。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

特別需要注意的是，在此 $g(x)$ 與 $h(y)$ 不必分別是 $X$ 與 $Y$ 的 pdf，只要分別是僅包含 $x$ 與 $y$ 的函數即可。

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個判斷法的使用情境是「若此二條件同時成立若且唯若 $X$ $\indep$ <span class="text-nowrap">$Y$」，</span>換句話說「其中任一條件不滿足，若且唯若 $X$ $\not\indep$ <span class="text-nowrap">$Y$」，</span>反過來說，已知 $X$ $\not\indep$ <span class="text-nowrap">$Y$，</span>若且唯若至少任一條件不滿足。

</div>

<div id="ex-joint-pdf-region-basic-independence" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.2 <span lang="en">(Continued)</span></div>

<div lang="en" markdown="1">
Suppose that a continuous random vector $(X,Y)$ has joint probability density function

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig XY}(x,y)=
\left\lbrace
\begin{array}{c@{\quad}l}
12\,xy(1-x), & 0<x<1,\ 0<y<1\\[0.5em]
0, & \text{o.w.}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases">
  <div class="topic-cases__lhs">$f_{\sssig XY}(x,y)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$12\,xy(1-x),$</div>
    <div class="topic-cases__cond">$0<x<1$, $0<y<1$</div>
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$\text{o.w.}$</div>
  </div>
</div>

</div>

<ol class="topic-list-paren topic-list-paren--start-5">
  <li>Determine whether $X$ and $Y$ are independent.</li>
</ol>
</div>

(5) 由[獨立隨機變數](#def-indep-r-v)的快速判斷法可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig XY}(x,y)=12(x-x^{2})y=6(x-x^{2})\times 2y=f_{\sssig X}(x)\,f_{\sssig Y}(y)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig XY}(x,y)&=12(x-x^{2})y\\[0.45em]
&=6(x-x^{2})\times 2y\\[0.45em]
&=f_{\sssig X}(x)\,f_{\sssig Y}(y)
\end{aligned}
$$

</div>

且 $0<x<1,\ 0<y<1$ 確實是一個積空間，此即
{: .topic-paren-cont}

$$
X\indep Y
$$

</div>

<div id="ex-joint-pdf-triangle-region-independence" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.3 <span lang="en">(Continued)</span></div>

<div lang="en" markdown="1">
Suppose that a continuous random vector $(X,Y)$ has joint probability density function

$$
f_{\sssig XY}(x,y)=
\left\lbrace
\begin{array}{c@{\quad}l}
2(x+y), & 0\leqslant x\leqslant y\leqslant 1\\[0.5em]
0, & \text{o.w.}
\end{array}
\right.
$$

<ol class="topic-list-paren topic-list-paren--start-5">
  <li>Determine whether $X$ and $Y$ are independent.</li>
</ol>
</div>

(5) 由[獨立隨機變數的定義](#def-indep-r-v)可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig XY}(x,y)\neq f_{\sssig X}(x)\,f_{\sssig Y}(y)\qquad\Longleftrightarrow\ X\not\indep Y
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
f_{\sssig XY}(x,y)\neq f_{\sssig X}(x)\,f_{\sssig Y}(y)\qquad\Longleftrightarrow\ X\not\indep Y
$$

</div>

</div>

<div id="ex-discrete-conditional-table-independence" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.9 <span lang="en">(Continued)</span></div>

<div lang="en" markdown="1">
Suppose that the joint pmf and the marginal pmfs of a two-dimensional discrete random vector $(X_1,X_2)$ are given in the following table.

| $X_1\backslash X_2$ | $0$ | $1$ | $2$ | $p_{\sssig X_1}(x_1)$ |
| :---: | :---: | :---: | :---: | :---: |
| $0$ | $0.2$ | $0.1$ | $0.1$ | $0.4$ |
| $1$ | $0.1$ | $0.2$ | $0.1$ | $0.4$ |
| $2$ | $0.1$ | $0.1$ | $0$ | $0.2$ |
| $p_{\sssig X_2}(x_2)$ | $0.4$ | $0.4$ | $0.2$ | $1$ |
{: .topic-table--joint-pmf}

<ol class="topic-list-paren topic-list-paren--start-3">
  <li>Determine whether $X_1$ and $X_2$ are independent.</li>
</ol>
</div>

(3) 由[獨立隨機變數之定義](#def-indep-r-v)可驗證
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

<div class="topic-math-follow-before" markdown="1">

$$
p_{\sssig X_1X_2}(1,1)=0.2\neq p_{\sssig X_1}(1)\,p_{\sssig X_2}(1)=0.4\times 0.4=0.16
$$

</div>

<div class="topic-math-follow" markdown="1">

$$
\Longleftrightarrow\ X_1\not\indep X_2
$$

</div>

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

<div class="topic-math-follow-before" markdown="1">

$$
\begin{aligned}
p_{\sssig X_1X_2}(1,1)&=0.2\\[0.45em]
&\neq p_{\sssig X_1}(1)\,p_{\sssig X_2}(1)=0.4\times 0.4=0.16
\end{aligned}
$$

</div>

<div class="topic-math-follow" markdown="1">

$$
\Longleftrightarrow\ X_1\not\indep X_2
$$

</div>

</div>

</div>

<div id="ex-binary-independence-check" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.12</div>

<div lang="en" markdown="1">
Suppose that $X$ and $Y$ are two binary random variables, and that $\mathbb{P}(Y=j\mid X=i)$ denotes a conditional probability with <span class="text-nowrap">$i,j=0,1$.</span> Define

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\alpha=\frac{\,\mathbb{P}(Y=1\mid X=1)\,}{\,\mathbb{P}(Y=0\mid X=1)\,},\quad \beta=\frac{\,\mathbb{P}(Y=1\mid X=0)\,}{\,\mathbb{P}(Y=0\mid X=0)\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\alpha&=\frac{\,\mathbb{P}(Y=1\mid X=1)\,}{\,\mathbb{P}(Y=0\mid X=1)\,},\\[0.45em]
\beta&=\frac{\,\mathbb{P}(Y=1\mid X=0)\,}{\,\mathbb{P}(Y=0\mid X=0)\,}
\end{aligned}
$$

</div>

and let <span class="text-nowrap">$\theta=\frac{\,\alpha\,}{\,\beta\,}$.</span>

<ol class="topic-list-paren">
  <li>Show that $\theta=1$ whenever $X$ and $Y$ are independent.</li>
  <li>Show that $\theta$ can also be written as
$$
\frac{\,\mathbb{P}(X=1\mid Y=1)\,\mathbb{P}(X=0\mid Y=0)\,}{\,\mathbb{P}(X=0\mid Y=1)\,\mathbb{P}(X=1\mid Y=0)\,}
$$
  </li>
  <li>Determine whether $\theta=1$ implies that $X$ and $Y$ are independent.</li>
</ol>
</div>

(1) 若 <span class="text-nowrap">$X\indep Y$，</span>則可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(Y=j\mid X=i)=\mathbb{P}(Y=j),\ \forall i,j=0,1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(Y=j\mid X=i)&=\mathbb{P}(Y=j),\\[0.45em]
&\forall i,j=0,1
\end{aligned}
$$

</div>

故有
{: .topic-paren-cont}

$$
\begin{gathered}
\alpha=\frac{\,\mathbb{P}(Y=1\mid X=1)\,}{\,\mathbb{P}(Y=0\mid X=1)\,}=\frac{\,\mathbb{P}(Y=1)\,}{\,\mathbb{P}(Y=0)\,}\\[0.45em]
\beta=\frac{\,\mathbb{P}(Y=1\mid X=0)\,}{\,\mathbb{P}(Y=0\mid X=0)\,}=\frac{\,\mathbb{P}(Y=1)\,}{\,\mathbb{P}(Y=0)\,}
\end{gathered}
$$

此即
{: .topic-paren-cont}

$$
\alpha=\beta\qquad\therefore\, \theta=\frac{\,\alpha\,}{\,\beta\,}=1
$$

(2) 依題意設定可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\theta&=\frac{\,\alpha\,}{\,\beta\,}=\frac{\,\mathbb{P}(Y=1\mid X=1)\,\mathbb{P}(Y=0\mid X=0)\,}{\,\mathbb{P}(Y=0\mid X=1)\,\mathbb{P}(Y=1\mid X=0)\,}\\[0.55em]
&=\frac{\,\dfrac{\,\mathbb{P}(Y=1,X=1)\,}{\mathbb{P}(X=1)}\,\dfrac{\,\mathbb{P}(Y=0,X=0)\,}{\mathbb{P}(X=0)}\,}{\,\dfrac{\,\mathbb{P}(Y=0,X=1)\,}{\mathbb{P}(X=1)}\,\dfrac{\,\mathbb{P}(Y=1,X=0)\,}{\mathbb{P}(X=0)}\,}\\[0.55em]
&=\frac{\,\mathbb{P}(X=1,Y=1)\,\mathbb{P}(X=0,Y=0)\,}{\,\mathbb{P}(X=1,Y=0)\,\mathbb{P}(X=0,Y=1)\,}\\[0.55em]
&=\frac{\,\dfrac{\,\mathbb{P}(X=1,Y=1)\,}{\mathbb{P}(Y=1)}\,\dfrac{\,\mathbb{P}(X=0,Y=0)\,}{\mathbb{P}(Y=0)}\,}{\,\dfrac{\,\mathbb{P}(X=1,Y=0)\,}{\mathbb{P}(Y=0)}\,\dfrac{\,\mathbb{P}(X=0,Y=1)\,}{\mathbb{P}(Y=1)}\,}\\[0.55em]
&=\frac{\,\mathbb{P}(X=1\mid Y=1)\,\mathbb{P}(X=0\mid Y=0)\,}{\,\mathbb{P}(X=0\mid Y=1)\,\mathbb{P}(X=1\mid Y=0)\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\theta&=\frac{\,\alpha\,}{\,\beta\,}\\[0.55em]
&=\frac{\mathbb{P}(Y=1\mid X=1)\,\mathbb{P}(Y=0\mid X=0)}{\mathbb{P}(Y=0\mid X=1)\,\mathbb{P}(Y=1\mid X=0)}\\[0.55em]
&=\frac{\dfrac{\mathbb{P}(Y=1,X=1)}{\mathbb{P}(X=1)}\,\dfrac{\mathbb{P}(Y=0,X=0)}{\mathbb{P}(X=0)}}{\dfrac{\mathbb{P}(Y=0,X=1)}{\mathbb{P}(X=1)}\,\dfrac{\mathbb{P}(Y=1,X=0)}{\mathbb{P}(X=0)}}\\[0.55em]
&=\frac{\mathbb{P}(X=1,Y=1)\,\mathbb{P}(X=0,Y=0)}{\mathbb{P}(X=1,Y=0)\,\mathbb{P}(X=0,Y=1)}\\[0.55em]
&=\frac{\dfrac{\mathbb{P}(X=1,Y=1)}{\mathbb{P}(Y=1)}\,\dfrac{\mathbb{P}(X=0,Y=0)}{\mathbb{P}(Y=0)}}{\dfrac{\mathbb{P}(X=1,Y=0)}{\mathbb{P}(Y=0)}\,\dfrac{\mathbb{P}(X=0,Y=1)}{\mathbb{P}(Y=1)}}\\[0.55em]
&=\frac{\mathbb{P}(X=1\mid Y=1)\,\mathbb{P}(X=0\mid Y=0)}{\mathbb{P}(X=0\mid Y=1)\,\mathbb{P}(X=1\mid Y=0)}
\end{aligned}
$$

</div>

(3) 令以下三個記號分別表示聯合機率與兩個邊際機率
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
p_{ij}=\mathbb{P}(X=i,Y=j),\quad p_{i\bullet}=\mathbb{P}(X=i),\quad p_{\bullet j}=\mathbb{P}(Y=j)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{ij}&=\mathbb{P}(X=i,Y=j),\\[0.45em]
p_{i\bullet}&=\mathbb{P}(X=i),\quad p_{\bullet j}=\mathbb{P}(Y=j)
\end{aligned}
$$

</div>

由 (2) 可以知道，若 $\theta=1$ 可推得 $p_{11}\,p_{00}=p_{10}\,p_{01}$ 這條等式，則有
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
p_{1\bullet}\,p_{\bullet 1}&=(p_{10}+p_{11})(p_{01}+p_{11})\\[0.45em]
&=p_{10}\,p_{01}+p_{10}\,p_{11}+p_{11}\,p_{01}+p_{11}\,p_{11}\\[0.45em]
&=p_{11}\,p_{00}+p_{10}\,p_{11}+p_{11}\,p_{01}+p_{11}\,p_{11}\\[0.45em]
&=p_{11}\,(p_{00}+p_{10}+p_{01}+p_{11})=p_{11}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{1\bullet}\,p_{\bullet 1}&=(p_{10}+p_{11})(p_{01}+p_{11})\\[0.45em]
&=p_{10}\,p_{01}+p_{10}\,p_{11}\\[0.45em]
&\qquad +p_{11}\,p_{01}+p_{11}\,p_{11}\\[0.45em]
&=p_{11}\,p_{00}+p_{10}\,p_{11}\\[0.45em]
&\qquad +p_{11}\,p_{01}+p_{11}\,p_{11}\\[0.45em]
&=p_{11}\,(p_{00}+p_{10}+p_{01}+p_{11})=p_{11}
\end{aligned}
$$

</div>

且同理可知 $p_{i\bullet}\,p_{\bullet j}=p_{ij}$ 對 $i,j=0,1$ 皆成立，故可知，若 $\theta=1$ 則有
{: .topic-paren-cont}

$$
X\indep Y
$$

</div>

<div id="ex-three-variable-independence" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.13</div>

<div lang="en" markdown="1">
Suppose that the random variables <span class="text-nowrap">$X$,</span> $Y$ and $Z$ have the following probability density function

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig XYZ}(x,y,z)=
\left\lbrace
\begin{array}{c@{\quad}l}
1, & 0<x<y<1,\ 0<z<2\\[0.5em]
0, & \text{o.w.}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases">
  <div class="topic-cases__lhs">$f_{\sssig XYZ}(x,y,z)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$1,$</div>
    <div class="topic-cases__cond">$0<x<y<1$, $0<z<2$</div>
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$\text{o.w.}$</div>
  </div>
</div>

</div>

Find <span class="text-nowrap">$\mathbb{P}(4X>Y\mid 4Z<2)$.</span>
</div>

令 <span class="text-nowrap">$g(x,y)=2$，</span><span class="text-nowrap">$h(z)=\frac{1}{\,2\,}$，</span>由 $f_{\sssig XYZ}(x,y,z)=g(x,y)\,h(z)$ 以及下面的集合分解

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
&\lbrace\,(x,y,z)\mid 0<x<y<1,\ 0<z<2\,\rbrace\\[0.45em]
&\quad =\lbrace\,(x,y)\mid 0<x<y<1\,\rbrace\times\lbrace\,z\mid 0<z<2\,\rbrace
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\lbrace\,&(x,y,z)\mid 0<x<y<1,\ 0<z<2\,\rbrace\\[0.45em]
&=\lbrace\,(x,y)\mid 0<x<y<1\,\rbrace\\[0.45em]
&\qquad \times\lbrace\,z\mid 0<z<2\,\rbrace
\end{aligned}
$$

</div>

可知 <span class="text-nowrap">$(X,Y)\indep Z$，</span>則有

$$
\mathbb{P}(4X>Y\mid 4Z<2)=\mathbb{P}(4X>Y)
$$

又由於

$$
f_{\sssig XY}(x,y)=
\left\lbrace
\begin{array}{c@{\quad}l}
2, & 0<x<y<1\\[0.5em]
0, & \text{o.w.}
\end{array}
\right.
$$

為一種[均勻分配](/teaching-topics/uniform-distribution-integral-transform/#def-uniform-distribution) <span lang="en">(uniform distribution)</span>，故可知 $\mathbb{P}(4X>Y)$ 即為下圖範圍在值域中的面積佔比

<figure id="fig-independence-range" class="topic-figure topic-figure--narrow">
  <img src="/images/teaching-topics/independence-range.svg" alt="第一象限中有兩條由原點出發的斜線與一條水平虛線。斜率較小的一條標 x 等於 y，斜率較大的一條標 4x 等於 y，水平虛線自兩條斜線的上端往左畫到縱軸，左端標 y 等於 1。斜率較小的斜線、水平虛線與縱軸圍成一個三角形，這個三角形被斜率較大的斜線切成兩塊，右下方較大的一塊以淡紅色填滿，左上方靠著縱軸的細長一塊沒有填色。橫軸右端標 x，縱軸上端標 y，兩軸都帶箭頭。">
  <figcaption><span class="topic-figure__label">Fig. 3.15.</span> 聯合值域是斜線 <span class="text-nowrap">$x=y$、</span>虛線 $y=1$ 與縱軸所圍成的三角形，斜線 $4x=y$ 再把它切成兩塊，填色的一塊即 $4x>y$ 的範圍。</figcaption>
</figure>

即

$$
\mathbb{P}(4X>Y)=\frac{3}{\,4\,}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這題的分配雖然不是常見機率模型，但其實仍是一種均勻分配。事實上，只要在指定範圍之內，機率密度都是常數，都能算是均勻分配，只是其範圍未必規則，且構成的變數間也未必獨立。

與過去的均勻分配不同的地方在於，過去的均勻分配之所以直接以所求範圍的面積作為機率，是因為機率密度為 <span class="text-nowrap">$1$，</span>因此體積與底面積相等；此處則因為機率密度不為 $1$ (但仍是常數)，因此計算體積的問題，只能等價於底面積在值域總面積的佔比。

</div>

## 本篇小結

[Theorem 3.3](#thm-multiplication-rule-r-v) 把第一章的乘法原理改寫成機率函數的版本。聯合 pdf 等於條件 pdf 乘上邊際 pdf，離散版本只要把 pdf 改成 pmf 即可。[Definition 3.10](#def-indep-r-v) 接著以三個等價條件界定獨立，條件 pdf 等於邊際 pdf，兩個方向各一條，以及聯合 pdf 等於兩個邊際 pdf 的乘積。第一章把獨立理解成一個事件的發生不影響另一個事件的機率，這裡則是一個變數的值不影響另一個變數的值。獨立成立時，一個事件若可以拆解成兩個一維事件的乘積，其機率也隨之拆成兩個機率的乘積；$n$ 個變數的獨立則寫成聯合 pdf 等於 $n$ 個邊際 pdf 的連乘。

實際判斷時另有一個快速的作法。聯合值域為積空間，且聯合 pdf 可以拆成一個只含 $x$ 的函數與一個只含 $y$ 的函數之乘積，兩個條件同時滿足才與獨立等價，其中的兩個函數不必分別是 $X$ 與 $Y$ 的 pdf。[Example 3.2 <span lang="en">(Continued)</span>](#ex-joint-pdf-region-basic-independence) 的值域是正方形且 joint pdf 可以拆開，故兩變數獨立；[Example 3.3 <span lang="en">(Continued)</span>](#ex-joint-pdf-triangle-region-independence) 的值域是三角形，joint pdf 不等於兩個 marginal pdf 的乘積，故不獨立；[Example 3.9 <span lang="en">(Continued)</span>](#ex-discrete-conditional-table-independence) 則以列聯表中的一格不等於兩個邊際機率的乘積，判定離散型的兩個變數不獨立。

[Example 3.12](#ex-binary-independence-check) 由兩個二元變數的條件機率之比值定義出 <span class="text-nowrap">$\theta$，</span>先證明獨立可推得 <span class="text-nowrap">$\theta=1$，</span>再把 $\theta$ 改寫成四個聯合機率的比值，並由這個形式反過來證明 $\theta=1$ 也可推得獨立，故兩者其實等價。[Example 3.13](#ex-three-variable-independence) 則示範獨立可以發生在成組的變數之間。$(X,Y)$ 與 $Z$ 的值域可以拆成兩塊的乘積，密度也可以拆成兩個函數的乘積，故 $Z$ 的條件不影響 $(X,Y)$ 的機率，所求因而降回二維，再以面積佔比求得。

[下一篇](/teaching-topics/multivariate-expectations/)把[期望值](/teaching-topics/expectation/#def-expectation)推廣到多元隨機變數，並說明兩個隨機變數獨立時，其函數乘積的期望值可以拆成兩個期望值的乘積。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
