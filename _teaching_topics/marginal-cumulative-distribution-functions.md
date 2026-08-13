---
title: "序列型例題與邊際累積分配函數"
subtitle: "Sequence Examples and Marginal Cumulative Distribution Functions"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 6
order: 306
permalink: /teaching-topics/marginal-cumulative-distribution-functions/
date: 2026-08-12
published: false
excerpt: "一列 iid 標準均勻分配的隨機變數，可以用「首次滿足特定條件的下標」定出一個隨機的 $N$，再求 $N$ 與序列本身的聯合機率。這一類問題的作法是回到 $N$ 的定義，把所求的事件改寫成一組不等式所界定的範圍，再以重積分求該範圍的體積，本篇的兩道例題分別以首次遞增的下標與部分和首次超過 $1$ 的下標示範這個作法。本篇後半給出邊際累積分配函數: 離散型是邊際 pmf 的加總，連續型是邊際 pdf 的積分。若把這個定義與聯合機率密度函數及邊際機率密度函數的定義相結合，則可以得到 $F_{\\sssig X}(x)=F_{\\sssig XY}(x,\\infty)$ 與 $F_{\\sssig Y}(y)=F_{\\sssig XY}(\\infty,y)$ 這個有用的性質。"
---

[上一篇](/teaching-topics/region-probabilities-joint-density/)以三道例題示範了[聯合機率密度函數](/teaching-topics/joint-probability-density-functions/#def-joint-pdf)在指定區域上的積分，其中最後一題的三個變數都服從標準均勻分配，機率因而等於所求範圍在整個值域中所佔的比例。

本篇分成兩個部分，兩者所處理的對象並不相同。**前半是兩道序列型的例題**: 題目給的是一列 iid <span lang="en">(independent and identically distributed)</span> 標準均勻分配的[隨機變數](/teaching-topics/random-variables-and-pmf/#def-random-variable) $U_1,U_2,\ldots$ 這個序列，並以某個條件首次成立的下標定出一個隨機的 <span class="text-nowrap">$N$，</span>所求則是 $N$ 與序列本身的聯合機率。這兩題所用的工具正是上一篇的重積分，只是積分的維度由三維推廣到 $n$ 維，而題目本身的關鍵，則在於回到 $N$ 的定義去建構所求機率的範圍。**後半回到分配函數本身**: 二元[隨機向量](/teaching-topics/random-vectors-joint-pmf/#def-random-vector)的[聯合累積分配函數](/teaching-topics/joint-cumulative-distribution-functions/#def-joint-cdf)、聯合機率密度函數與[邊際機率密度函數](/teaching-topics/marginal-probability-density-functions/#def-marginal-pdf)都已經定義過，還差邊際的累積分配函數尚未給出，本篇把它補上，並說明它與聯合累積分配函數之間的關係。

## 標準均勻分配序列與首次滿足特定條件的下標

在進入這兩道例題之前，先把上一篇最後一題所用到的那個微積分事實記下來。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

事實上，在微積分中，$\iint_{A}1\,dx\,dy$ 表示 $A$ 區域的面積、$\iiint_{V}1\,dx\,dy\,dz$ 表示 $V$ 區域的體積，以此類推。這個性質在標準均勻分配的隨機變數上特別容易使用，我們可以將求取機率的問題，轉變為求取多維空間中的體積 (或面積)。

</div>

<div id="ex-uniform-sequence-first-rise" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.7</div>

<div lang="en" markdown="1">
Suppose that $U_1,U_2,\ldots$ are iid $\mathcal{U}(0,1)$ random variables, and that $N$ is the first index at which the sequence rises, that is,

$$
N=\min\lbrace\,n\mid n\geqslant 2,\ U_n>U_{n-1}\,\rbrace
$$

Suppose that <span class="text-nowrap">$0<u\leqslant 1$.</span>

<ol class="topic-list-paren">
  <li>Show that
$$
\mathbb{P}(U_1\leqslant u,N=n)=\frac{\,u^{n-1}\,}{\,(n-1)!\,}-\frac{\,u^{n}\,}{\,n!\,},\quad n\geqslant 2
$$
  </li>
  <li>Evaluate
$$
\mathbb{P}(U_1\leqslant u,\ N\ \text{is even})
$$
  </li>
</ol>
</div>

(1) 由題意敘述可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(U_1\leqslant u,N=n)&=\mathbb{P}(U_{n-1}<U_{n-2}<\cdots<U_{1}\leqslant u,\ U_{n}>U_{n-1})\\[0.45em]
&=\mathbb{P}(U_{n-1}<U_{n-2}<\cdots<U_{1}\leqslant u)\\[0.45em]
&\quad -\mathbb{P}(U_{n}<U_{n-1}<U_{n-2}<\cdots<U_{1}\leqslant u)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(U_1\leqslant u,N=n)\\[0.45em]
&\quad =\mathbb{P}(U_{n-1}<U_{n-2}<\cdots<U_{1}\leqslant u,\\[0.2em]
&\qquad\qquad U_{n}>U_{n-1})\\[0.45em]
&\quad =\mathbb{P}(U_{n-1}<U_{n-2}<\cdots<U_{1}\leqslant u)\\[0.45em]
&\qquad -\mathbb{P}(U_{n}<U_{n-1}<U_{n-2}<\cdots<U_{1}\leqslant u)
\end{aligned}
$$

</div>

又因為下式成立
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig U_1\cdots U_n}(u_1,\ldots,u_n)=\prod_{i=1}^{n}f_{\sssig U_i}(u_i)=1,\quad 0<u_1,\ldots,u_n<1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig U_1\cdots U_n}(u_1,\ldots,u_n)&=\prod_{i=1}^{n}f_{\sssig U_i}(u_i)=1,\\[0.45em]
&\quad\ 0<u_1,\ldots,u_n<1
\end{aligned}
$$

</div>

故我們有
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(U_{n}<U_{n-1}<U_{n-2}<\cdots<U_{1}\leqslant u)\\[0.45em]
&\quad =\int_{0}^{u}\int_{0}^{u_1}\int_{0}^{u_2}\cdots\int_{0}^{u_{n-1}}1\,du_{n}\,du_{n-1}\cdots\,du_{1}\\[0.45em]
&\quad =\int_{0}^{u}\int_{0}^{u_1}\int_{0}^{u_2}\cdots\int_{0}^{u_{n-2}}u_{n-1}\,du_{n-1}\,du_{n-2}\cdots\,du_{1}\\[0.45em]
&\quad =\cdots=\int_{0}^{u}\frac{1}{\,(n-1)!\,}u_1^{n-1}\,du_{1}=\frac{\,u^n\,}{\,n!\,},\quad 0<u\leqslant 1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(U_{n}<U_{n-1}<U_{n-2}<\cdots<U_{1}\leqslant u)\\[0.45em]
&\quad =\int_{0}^{u}\int_{0}^{u_1}\int_{0}^{u_2}\cdots\int_{0}^{u_{n-1}}\\[0.2em]
&\qquad\qquad 1\,du_{n}\,du_{n-1}\cdots\,du_{1}\\[0.45em]
&\quad =\int_{0}^{u}\int_{0}^{u_1}\int_{0}^{u_2}\cdots\int_{0}^{u_{n-2}}\\[0.2em]
&\qquad\qquad u_{n-1}\,du_{n-1}\,du_{n-2}\cdots\,du_{1}\\[0.45em]
&\quad =\cdots=\int_{0}^{u}\frac{1}{\,(n-1)!\,}u_1^{n-1}\,du_{1}\\[0.45em]
&\quad =\frac{\,u^n\,}{\,n!\,},\quad 0<u\leqslant 1
\end{aligned}
$$

</div>

同理可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(U_{n-1}<U_{n-2}<\cdots<U_{1}\leqslant u)=\frac{\,u^{n-1}\,}{\,(n-1)!\,},\quad 0<u\leqslant 1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(U_{n-1}<U_{n-2}<\cdots<U_{1}\leqslant u)\\[0.45em]
&\quad =\frac{\,u^{n-1}\,}{\,(n-1)!\,},\quad 0<u\leqslant 1
\end{aligned}
$$

</div>

故所求為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(U_1\leqslant u,N=n)=\frac{\,u^{n-1}\,}{\,(n-1)!\,}-\frac{\,u^{n}\,}{\,n!\,},\quad n\geqslant 2
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(U_1\leqslant u,N=n)\\[0.45em]
&\quad =\frac{\,u^{n-1}\,}{\,(n-1)!\,}-\frac{\,u^{n}\,}{\,n!\,},\quad n\geqslant 2
\end{aligned}
$$

</div>

(2) 由 (1) 可知下式成立
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(U_1\leqslant u,N=n)=\frac{\,u^{n-1}\,}{\,(n-1)!\,}-\frac{\,u^{n}\,}{\,n!\,},\quad n\geqslant 2
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(U_1\leqslant u,N=n)\\[0.45em]
&\quad =\frac{\,u^{n-1}\,}{\,(n-1)!\,}-\frac{\,u^{n}\,}{\,n!\,},\quad n\geqslant 2
\end{aligned}
$$

</div>

故可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(U_1\leqslant u,\ N\ \text{偶數})&=\sum_{k=1}^{\infty}\mathbb{P}(U_1\leqslant u,N=2k)=\sum_{k=1}^{\infty}\left[\frac{\,u^{2k-1}\,}{\,(2k-1)!\,}-\frac{\,u^{2k}\,}{\,(2k)!\,}\right]\\[0.45em]
&=\frac{\,u\,}{1!}-\frac{\,u^2\,}{2!}+\frac{\,u^3\,}{3!}-\frac{\,u^4\,}{4!}+\cdots\\[0.45em]
&=1-\left(1-\frac{\,u\,}{1!}+\frac{\,u^2\,}{2!}-\frac{\,u^3\,}{3!}+\frac{\,u^4\,}{4!}-\cdots\right)\\[0.45em]
&=1-e^{-u},\quad 0<u\leqslant 1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(U_1\leqslant u,\ N\ \text{偶數})\\[0.45em]
&\quad =\sum_{k=1}^{\infty}\mathbb{P}(U_1\leqslant u,N=2k)\\[0.45em]
&\quad =\sum_{k=1}^{\infty}\left[\frac{\,u^{2k-1}\,}{\,(2k-1)!\,}-\frac{\,u^{2k}\,}{\,(2k)!\,}\right]\\[0.45em]
&\quad =\frac{\,u\,}{1!}-\frac{\,u^2\,}{2!}+\frac{\,u^3\,}{3!}-\frac{\,u^4\,}{4!}+\cdots\\[0.45em]
&\quad =1-\biggl(1-\frac{\,u\,}{1!}+\frac{\,u^2\,}{2!}\\[0.2em]
&\qquad\qquad -\frac{\,u^3\,}{3!}+\frac{\,u^4\,}{4!}-\cdots\biggr)\\[0.45em]
&\quad =1-e^{-u},\quad 0<u\leqslant 1
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

在此處中沿用了[前一道題](/teaching-topics/region-probabilities-joint-density/#ex-three-iid-uniform-order)的計算結果，除此之外，讀者應該會對此處的做法感到熟悉，因為在 [Example 2.16](/teaching-topics/properties-of-expectation/#ex-car-offer-waiting-time) 中，我們就曾經依照 $N$ 的定義，以序列計算所求機率，甚至求出[期望值](/teaching-topics/expectation/#def-expectation)。

類似此處定義 $N$ 為「首次滿足特定條件的序列下標」還有很多變化的題型，甚至 $N$ 本身也可以服從常見機率模型，我們將在稍後看到這種情況衍生的特殊等式，但不論如何，我們總是可以利用 $N$ 的定義，反過來建構出指定的機率範圍，如下面這題。

</div>

<div id="ex-uniform-sequence-sum-exceeds-one" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.8</div>

<div lang="en" markdown="1">
Suppose that $U_1,U_2,\ldots$ are independent random numbers drawn from the same $\mathcal{U}(0,1)$ distribution, and that $N$ is defined by

$$
N=\min\Bigl\lbrace\,n\,\Bigm|\,\sum_{i=1}^{n}U_i>1\,\Bigr\rbrace
$$

<ol class="topic-list-paren">
  <li>Show that
$$
\mathbb{P}(N>n)=\frac{1}{\,n!\,}
$$
  </li>
  <li>Evaluate <span class="text-nowrap">$\mathbb{E}(N)$.</span></li>
</ol>
</div>

(1) 由題意敘述可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(N=n)&=\mathbb{P}(U_1+\cdots+U_{n-1}\leqslant 1,\ U_1+\cdots+U_{n-1}+U_n>1)\\[0.45em]
&=\mathbb{P}(U_1+\cdots+U_{n-1}\leqslant 1)-\mathbb{P}(U_1+\cdots+U_{n-1}+U_n\leqslant 1)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(N=n)\\[0.45em]
&\quad =\mathbb{P}(U_1+\cdots+U_{n-1}\leqslant 1,\\[0.2em]
&\qquad\qquad U_1+\cdots+U_{n-1}+U_n>1)\\[0.45em]
&\quad =\mathbb{P}(U_1+\cdots+U_{n-1}\leqslant 1)\\[0.45em]
&\qquad -\mathbb{P}(U_1+\cdots+U_{n-1}+U_n\leqslant 1)
\end{aligned}
$$

</div>

又因為下式成立
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig U_1\cdots U_n}(u_1,\ldots,u_n)=\prod_{i=1}^{n}f_{\sssig U_i}(u_i)=1,\quad 0<u_1,\ldots,u_n<1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig U_1\cdots U_n}(u_1,\ldots,u_n)&=\prod_{i=1}^{n}f_{\sssig U_i}(u_i)=1,\\[0.45em]
&\quad\ 0<u_1,\ldots,u_n<1
\end{aligned}
$$

</div>

故我們有
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(U_1+\cdots+U_{n-1}+U_n\leqslant 1)\\[0.45em]
&\quad =\int_{0}^{1}\int_{0}^{1-u_1}\int_{0}^{1-u_1-u_{2}}\cdots\int_{0}^{1-u_1-\cdots-u_{n-1}}1\,du_{n}\,du_{n-1}\cdots\,du_{1}\\[0.45em]
&\quad =\int_{0}^{1}\int_{0}^{1-u_1}\int_{0}^{1-u_1-u_{2}}\cdots\int_{0}^{1-u_1-\cdots-u_{n-2}}(1-u_1-\cdots-u_{n-1})\,du_{n-1}\,du_{n-2}\cdots\,du_{1}\\[0.45em]
&\quad =\cdots=\int_{0}^{1}\frac{1}{\,(n-1)!\,}(1-u_1)^{n-1}\,du_{1}=\frac{\,1\,}{\,n!\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(U_1+\cdots+U_{n-1}+U_n\leqslant 1)\\[0.45em]
&\quad =\int_{0}^{1}\int_{0}^{1-u_1}\int_{0}^{1-u_1-u_{2}}\cdots\\[0.2em]
&\qquad\quad \int_{0}^{1-u_1-\cdots-u_{n-1}}1\,du_{n}\,du_{n-1}\cdots\,du_{1}\\[0.45em]
&\quad =\int_{0}^{1}\int_{0}^{1-u_1}\int_{0}^{1-u_1-u_{2}}\cdots\\[0.2em]
&\qquad\quad \int_{0}^{1-u_1-\cdots-u_{n-2}}(1-u_1-\cdots-u_{n-1})\\[0.2em]
&\qquad\qquad du_{n-1}\,du_{n-2}\cdots\,du_{1}\\[0.45em]
&\quad =\cdots=\int_{0}^{1}\frac{1}{\,(n-1)!\,}(1-u_1)^{n-1}\,du_{1}\\[0.45em]
&\quad =\frac{\,1\,}{\,n!\,}
\end{aligned}
$$

</div>

同理可知
{: .topic-paren-cont}

$$
\mathbb{P}(U_1+\cdots+U_{n-1}\leqslant 1)=\frac{\,1\,}{\,(n-1)!\,}
$$

故可知道
{: .topic-paren-cont}

$$
\mathbb{P}(N=n)=\frac{\,1\,}{\,(n-1)!\,}-\frac{\,1\,}{\,n!\,}
$$

所求為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(N>n)=\sum_{k=n+1}^{\infty}\mathbb{P}(N=k)=\sum_{k=n+1}^{\infty}\left[\frac{\,1\,}{\,(k-1)!\,}-\frac{\,1\,}{\,k!\,}\right]=\frac{\,1\,}{\,n!\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(N>n)&=\sum_{k=n+1}^{\infty}\mathbb{P}(N=k)\\[0.45em]
&=\sum_{k=n+1}^{\infty}\left[\frac{\,1\,}{\,(k-1)!\,}-\frac{\,1\,}{\,k!\,}\right]\\[0.45em]
&=\frac{\,1\,}{\,n!\,}
\end{aligned}
$$

</div>

(2) 由於 $\mathbb{P}(N>n)=\frac{1}{\,n!\,}$ 成立，故由 [Theorem 2.8](/teaching-topics/expectation/#thm-expectation-tail-sum) 可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(N)=\sum_{n=0}^{\infty}\mathbb{P}(N>n)=\sum_{n=0}^{\infty}\frac{1}{\,n!\,}=e
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(N)&=\sum_{n=0}^{\infty}\mathbb{P}(N>n)\\[0.45em]
&=\sum_{n=0}^{\infty}\frac{1}{\,n!\,}=e
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

我們又一次地利用了 $N$ 的定義，建構出所求機率所對應的機率範圍，是解題的關鍵。

此外，本題的積分雖然都只是多項式積分，但積分範圍與過程卻需要讀者細心思考。

</div>

## 邊際累積分配函數

以上兩題所處理的都是特定範圍上的機率。接下來我們把注意力移回分配函數本身: 二元隨機向量的聯合累積分配函數、聯合機率密度函數與邊際機率密度函數都已經給過定義，還差各個變數自己的累積分配函數尚未定義。

<div id="def-marginal-cdf" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 3.7 (邊際累積分配函數, marginal cdf)</div>

若 $(X,Y)$ 為二元**離散型**隨機變數，其邊際 pmf 分別為 $p_{\sssig X}(x)$ 與 <span class="text-nowrap">$p_{\sssig Y}(y)$，</span>則

$$
F_{\sssig X}(x)=\sum_{t\leqslant x}p_{\sssig X}(t)
$$

為 $X$ 的**邊際累積分配函數 <span lang="en">(marginal cdf)</span>**，而以下的函數

$$
F_{\sssig Y}(y)=\sum_{s\leqslant y}p_{\sssig Y}(s)
$$

為 $Y$ 的**邊際累積分配函數**。

若 $(X,Y)$ 為二元**連續型**隨機變數，其邊際 pdf 分別為 $f_{\sssig X}(x)$ 與 <span class="text-nowrap">$f_{\sssig Y}(y)$，</span>則

$$
F_{\sssig X}(x)=\int_{-\infty}^{x}f_{\sssig X}(t)\,dt
$$

為 $X$ 的**邊際累積分配函數**，而以下的函數

$$
F_{\sssig Y}(y)=\int_{-\infty}^{y}f_{\sssig Y}(s)\,ds
$$

為 $Y$ 的**邊際累積分配函數**。

</div>

這個定義指出邊際 pdf (或 pmf) 的積分 (或加總) 即為邊際 cdf，應是一個相當符合直覺的定義。然而，這個定義若是與 [Definition 3.5](/teaching-topics/joint-probability-density-functions/#def-joint-pdf) 及 [Definition 3.6](/teaching-topics/marginal-probability-density-functions/#def-marginal-pdf) 相結合，則可以得到以下這個有用的性質:

<div id="thm-joint-cdf-prob" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 3.2 (邊際累積分配函數的求法, marginal cdf from a joint cdf)</div>

若 $(X,Y)$ 為二元**離散型**隨機變數，其邊際 pmf 分別為 $p_{\sssig X}(x)$ 與 <span class="text-nowrap">$p_{\sssig Y}(y)$，</span>則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
F_{\sssig X}(x)=\sum_{t\leqslant x}p_{\sssig X}(t)=\sum_{s\in\mathbb{R}}\sum_{t\leqslant x}p_{\sssig XY}(t,s)=F_{\sssig XY}(x,\infty)\\[0.6em]
F_{\sssig Y}(y)=\sum_{s\leqslant y}p_{\sssig Y}(s)=\sum_{s\leqslant y}\sum_{t\in\mathbb{R}}p_{\sssig XY}(t,s)=F_{\sssig XY}(\infty,y)
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig X}(x)&=\sum_{t\leqslant x}p_{\sssig X}(t)\\[0.45em]
&=\sum_{s\in\mathbb{R}}\sum_{t\leqslant x}p_{\sssig XY}(t,s)=F_{\sssig XY}(x,\infty)
\end{aligned}
$$

$$
\begin{aligned}
F_{\sssig Y}(y)&=\sum_{s\leqslant y}p_{\sssig Y}(s)\\[0.45em]
&=\sum_{s\leqslant y}\sum_{t\in\mathbb{R}}p_{\sssig XY}(t,s)=F_{\sssig XY}(\infty,y)
\end{aligned}
$$

</div>

若 $(X,Y)$ 為二元**連續型**隨機變數，其邊際 pdf 分別為 $f_{\sssig X}(x)$ 與 <span class="text-nowrap">$f_{\sssig Y}(y)$，</span>則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
F_{\sssig X}(x)=\int_{-\infty}^{x}f_{\sssig X}(t)\,dt=\int_{-\infty}^{\infty}\int_{-\infty}^{x}f_{\sssig XY}(t,s)\,dt\,ds=F_{\sssig XY}(x,\infty)\\[0.6em]
F_{\sssig Y}(y)=\int_{-\infty}^{y}f_{\sssig Y}(s)\,ds=\int_{-\infty}^{y}\int_{-\infty}^{\infty}f_{\sssig XY}(t,s)\,dt\,ds=F_{\sssig XY}(\infty,y)
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig X}(x)&=\int_{-\infty}^{x}f_{\sssig X}(t)\,dt\\[0.45em]
&=\int_{-\infty}^{\infty}\int_{-\infty}^{x}f_{\sssig XY}(t,s)\,dt\,ds\\[0.45em]
&=F_{\sssig XY}(x,\infty)
\end{aligned}
$$

$$
\begin{aligned}
F_{\sssig Y}(y)&=\int_{-\infty}^{y}f_{\sssig Y}(s)\,ds\\[0.45em]
&=\int_{-\infty}^{y}\int_{-\infty}^{\infty}f_{\sssig XY}(t,s)\,dt\,ds\\[0.45em]
&=F_{\sssig XY}(\infty,y)
\end{aligned}
$$

</div>

</div>

<div class="topic-proof" markdown="1">
**Proof.**

在此僅以連續型 $X$ 的邊際 cdf 為例，其他邊際 cdf 同理可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
F_{\sssig X}(x)&=\int_{-\infty}^{x}f_{\sssig X}(t)\,dt=\int_{-\infty}^{x}\biggl[\int_{-\infty}^{\infty}f_{\sssig XY}(t,s)\,ds\biggr]\,dt\\[0.45em]
&=\int_{-\infty}^{\infty}\int_{-\infty}^{x}f_{\sssig XY}(t,s)\,dt\,ds=F_{\sssig XY}(x,\infty)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig X}(x)&=\int_{-\infty}^{x}f_{\sssig X}(t)\,dt\\[0.45em]
&=\int_{-\infty}^{x}\biggl[\int_{-\infty}^{\infty}f_{\sssig XY}(t,s)\,ds\biggr]\,dt\\[0.45em]
&=\int_{-\infty}^{\infty}\int_{-\infty}^{x}f_{\sssig XY}(t,s)\,dt\,ds\\[0.45em]
&=F_{\sssig XY}(x,\infty)
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

讀者如果確實將 [Example 3.2](/teaching-topics/marginal-probability-density-functions/#ex-joint-pdf-region-basic) 至 [Example 3.4](/teaching-topics/region-probabilities-joint-density/#ex-joint-pdf-exponential-region) 的積分範圍思考透徹，則應該發現，這些範圍上的積分結果，事實上都能夠與 [Theorem 3.2](#thm-joint-cdf-prob) 的結果相呼應。

</div>

## 本篇小結

[Example 3.7](#ex-uniform-sequence-first-rise) 與 [Example 3.8](#ex-uniform-sequence-sum-exceeds-one) 的作法完全相同。先依 $N$ 的定義，把 $\lbrace N=n\rbrace$ 這個事件改寫成一組不等式所界定的範圍，再以兩個範圍的機率相減求得。由於 $U_1,U_2,\ldots$ 為 iid 標準均勻分配，$n$ 個變數的聯合 pdf 在 $0<u_1,\ldots,u_n<1$ 之上恆為 <span class="text-nowrap">$1$，</span>所求機率因而就是那個範圍的體積，而體積由層層相套的定積分算出，前者得到的是 $\frac{\,u^{n-1}\,}{\,(n-1)!\,}-\frac{\,u^{n}\,}{\,n!\,}$ 這個式子，後者得到的是 $\frac{\,1\,}{\,(n-1)!\,}-\frac{\,1\,}{\,n!\,}$ 這個式子。兩題最後都回到級數。前者的交錯級數收斂到 <span class="text-nowrap">$1-e^{-u}$，</span>後者的裂項和給出 $\mathbb{P}(N>n)=\frac{1}{\,n!\,}$ 這條等式，再由非負整數隨機變數的尾機率表示得到 <span class="text-nowrap">$\mathbb{E}(N)=e$。</span>

[Definition 3.7](#def-marginal-cdf) 把累積分配函數推廣到邊際的情形。離散型是邊際 pmf 由左端累加到 <span class="text-nowrap">$x$，</span>連續型是邊際 pdf 由 $-\infty$ 積分到 <span class="text-nowrap">$x$，</span>兩者都與單變數的 cdf 是同一件事。[Theorem 3.2](#thm-joint-cdf-prob) 則把它接回聯合的分配，邊際 cdf 就是把聯合 cdf 的另一個變數放到 <span class="text-nowrap">$\infty$，</span>也就是不對另一個變數作任何限制。證明只需把邊際 pdf 的定義代入，再交換積分的順序。

回顧這一段的脈絡，我們先以 $\mathbb{P}(X\leqslant x,Y\leqslant y)$ 定出聯合累積分配函數，再由二重積分的表示式定出聯合機率密度函數，接著對其中一個變數積分而得到邊際機率密度函數，並以數道例題練習了[各種區域上的機率](/teaching-topics/region-probabilities-joint-density/)如何求取，最後補上邊際累積分配函數，把四個機率函數與兩個分配函數之間的關係補齊。下一篇把隨機向量中的一個或多個變數固定成常數，看看這時候的機率分配會變成什麼樣子，此即條件機率分配。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
