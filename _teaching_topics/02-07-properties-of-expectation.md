---
title: "期望值的性質與函數期望值"
subtitle: "Properties of Expectation and Expectation of a Function"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 7
order: 207
permalink: /teaching-topics/properties-of-expectation/
date: 2026-08-06
published: true
excerpt: "函數期望值定理指出，$g(X)$ 的期望值不必先求出 $g(X)$ 的分配，只要以 $X$ 的 pmf 或 pdf 對 $g(x)$ 加權求和或積分即可。期望值對線性組合具有可交換性: 期望值內若是線性函數的形式，可以先取期望值再做線性函數，非線性的部分則交由函數期望值定理處理。由這個複合性質設定各常數，可以得到常數的期望值還是自己本身、平移的期望值是期望值的平移、倍數的期望值是期望值的倍數三個子性質。本篇另有兩道例題，說明期望值可能發散，以及期望值如何改寫成累積分配函數的積分。"
---

[上一篇](/teaching-topics/expectation/)給出[期望值](/teaching-topics/expectation/#def-expectation)的定義，並以非負[隨機變數](/teaching-topics/random-variables-and-pmf/#def-random-variable)的尾機率表示作結。

本篇分三個部分。**先看期望值的特殊算法**: 有些隨機變數不必先寫出 pmf 或 pdf 再逐項加總，改以尾機率的加總或 cdf 的積分反而好算；兩道例題分別示範非負整數型與連續型的作法，前者順帶說明期望值可能發散，後者把尾機率的表示推廣到一般的連續型隨機變數。**再看函數期望值**: 若我們關心的不是 $X$ 本身，而是 $X$ 經過某個函數轉換之後的 $g(X)$，它的期望值不必先求出 $g(X)$ 的分配，直接以 $X$ 的 pmf 或 pdf 對 $g(x)$ 加權即可。**最後說明期望值的性質**: 期望值對線性組合可以交換，由這個複合性質設定各常數，還能得到三個常用的子性質。

<div id="ex-car-offer-waiting-time" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.16</div>

<div lang="en" markdown="1">
Suppose that a car is put up for sale, and that the successive offers received at times $0,1,2,\ldots$ are $X_{0},X_{1},X_{2},\ldots$, which are random, independent, and identically distributed. Let

$$
N=\min\lbrace n\mid X_{n}>X_{0}\rbrace
$$

be the first time at which an offer exceeds the initial offer $X_{0}$ received at time $0$. Show that $\mathbb{E}(N)=\infty$.
</div>

由於 $N=\min\lbrace n\mid X_n>X_0\rbrace$，故對任意 $N=k$ 之事件而言，在 $X_0,X_1,\ldots,X_{k-1},X_k$ 之中，$X_k$ 為此 $k+1$ 個隨機變數中最大者，且 $X_0$ 為此 $k+1$ 個隨機變數中第二大者。

又因為 $X_0,X_1,X_2,\ldots$ 為 iid <span lang="en">(independent and identically distributed)</span>，且另設其共同的分配為連續型，故 $X_0,X_1,\ldots,X_k$ 這 $k+1$ 個變數的大小順序共有 $(k+1)!$ 種排法，每一種的機率均等，滿足 $N=k$ 之事件機率因而為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(N=k)=\frac{\bigl((k+1)-2\bigr)!}{(k+1)!}=\frac{1}{k(k+1)},\quad k\in\mathbb{N}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(N=k)&=\frac{\bigl((k+1)-2\bigr)!}{(k+1)!}\\[0.45em]
&=\frac{1}{k(k+1)},\quad k\in\mathbb{N}
\end{aligned}
$$

</div>

又 $N$ 為非負整數隨機變數，故由 [Theorem 2.8](/teaching-topics/expectation/#thm-expectation-tail-sum) 可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(N)&=\sum_{n=1}^{\infty}\mathbb{P}(N\geqslant n)=\sum_{n=1}^{\infty}\sum_{k=n}^{\infty}\mathbb{P}(N=k)\\[0.45em]
&=\sum_{n=1}^{\infty}\sum_{k=n}^{\infty}\frac{1}{k(k+1)}=\sum_{n=1}^{\infty}\sum_{k=n}^{\infty}\left(\frac{1}{k}-\frac{1}{k+1}\right)\\[0.45em]
&=\sum_{n=1}^{\infty}\frac{1}{n}=\infty
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(N)&=\sum_{n=1}^{\infty}\mathbb{P}(N\geqslant n)\\[0.45em]
&=\sum_{n=1}^{\infty}\sum_{k=n}^{\infty}\mathbb{P}(N=k)\\[0.45em]
&=\sum_{n=1}^{\infty}\sum_{k=n}^{\infty}\frac{1}{k(k+1)}\\[0.45em]
&=\sum_{n=1}^{\infty}\sum_{k=n}^{\infty}\left(\frac{1}{k}-\frac{1}{k+1}\right)\\[0.45em]
&=\sum_{n=1}^{\infty}\frac{1}{n}=\infty
\end{aligned}
$$

</div>

原式得證。

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

iid 是我們在[下一章](/teaching-topics/independent-random-variables/)才會提到的性質，是多個隨機變數彼此獨立 <span lang="en">(independent)</span> 且同分配 <span lang="en">(identically distributed)</span> 的意思，在此階段讀者不妨想像成，每個隨機變數不互相影響，且客觀條件皆相同。

在這題的加總當中，使用了三個技巧。第一個是藉由 iid 的設定，將隨機變數的問題變回古典機率的問題；第二個是**裂項和 <span lang="en">(telescoping sum)</span>**，將 $\frac{1}{k(k+1)}$ 分解成 $\frac{1}{k}-\frac{1}{k+1}$ 從而完成第一個級數，這個技巧在高中數學中被稱作「分項對消法」，是計算級數的技巧之一；最後一個則是**調和級數 <span lang="en">(harmonic series)</span>**，而調和級數正是這題中，期望值發散的原因。

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

題目只設 $X_0,X_1,X_2,\ldots$ 彼此獨立且同分配，並未指明共同的分配屬於哪一型。上面計算 $\mathbb{P}(N=k)$ 時，用到的是<span class="text-nowrap">「$X_0,X_1,\ldots,X_k$</span> 這 $k+1$ 個變數的大小順序共有 $(k+1)!$ 種排法，每一種的機率均等」這件事，而這要在任兩個變數不會取到相同值時才成立，故解答中另設共同的分配為連續型，任兩個變數取到相同值的機率為零。

若共同的分配為離散型，兩個變數就可能取到相同的值，機率均等的排列論證便不成立。例如令 $X_0,X_1,X_2,\ldots$ 彼此獨立且同分配，各自以 $\frac{1}{2}$ 的機率取值 $0$、以 $\frac{1}{2}$ 的機率取值 $1$。此時 $N=1$ 即 <span class="text-nowrap">$X_1>X_0$，</span>也就是 $X_0=0$ 且 $X_1=1$，則有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(N=1)=\mathbb{P}(X_0=0,\,X_1=1)=\frac{1}{2}\cdot\frac{1}{2}=\frac{1}{4}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(N=1)&=\mathbb{P}(X_0=0,\,X_1=1)\\[0.45em]
&=\frac{1}{2}\cdot\frac{1}{2}=\frac{1}{4}
\end{aligned}
$$

</div>

而上面 $\mathbb{P}(N=k)$ 的表示式在 $k=1$ 給出的是 $\frac{1}{2}$，兩者不等。

要證的 $\mathbb{E}(N)=\infty$ 本身則不需要這個前提。$N\geqslant n$ 等價於 $X_0$ 為 $X_0,X_1,\ldots,X_{n-1}$ 之中最大者，而這 $n$ 個變數獨立且同分配，各自為最大者的機率相同，其中又至少有一個為最大者，這 $n$ 個事件因而必有一個發生。由[布爾不等式](/teaching-topics/probability-rules-from-axioms/#theorem-boole)可得 $1\leqslant n\,\mathbb{P}(N\geqslant n)$，即 $\mathbb{P}(N\geqslant n)\geqslant\frac{1}{n}$，這些下界的加總發散。

離散型之下還可能沒有任何一個 $X_n$ 超過 $X_0$，此時 $N$ 取不到有限值，只要這件事發生的機率為正，$\mathbb{E}(N)=\infty$ 自然成立；在剛才那個離散型的例子裡，這個機率就是 $\mathbb{P}(X_0=1)=\frac{1}{2}$。共同的分配為連續型時 $\sum_{k=1}^{\infty}\frac{1}{k(k+1)}=1$，$N$ 取到有限值的機率為 $1$，解答中才能直接引用 [Theorem 2.8](/teaching-topics/expectation/#thm-expectation-tail-sum)。

</div>

<div id="ex-expectation-tail-formula" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.17</div>

<div lang="en" markdown="1">
Suppose that $X$ is a continuous random variable whose probability density function is $f_{\sssig X}(x)$ and whose cumulative distribution function is $F_{\sssig X}(x)$, and that $\mathbb{E}\lvert X\rvert<\infty$. Show that

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(X)=\int_{0}^{\infty}\bigl[1-F_{\sssig X}(x)\bigr]\,dx-\int_{-\infty}^{0}F_{\sssig X}(x)\,dx
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\int_{0}^{\infty}\bigl[1-F_{\sssig X}(x)\bigr]\,dx\\[0.45em]
&\qquad\qquad-\int_{-\infty}^{0}F_{\sssig X}(x)\,dx
\end{aligned}
$$

</div>
</div>

由期望值的定義，將積分範圍以 $0$ 為界拆成兩段，再把 $x$ 寫成 $\int_{0}^{x}1\,dy$ 之後交換積分順序，最後在後一項中令 $x=-y$，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\int_{-\infty}^{\infty}xf_{\sssig X}(x)\,dx=\int_{0}^{\infty}xf_{\sssig X}(x)\,dx+\int_{-\infty}^{0}xf_{\sssig X}(x)\,dx\\[0.45em]
&=\int_{0}^{\infty}\left(\int_{0}^{x}1\,dy\right)f_{\sssig X}(x)\,dx-\int_{-\infty}^{0}\left(\int_{0}^{-x}1\,dy\right)f_{\sssig X}(x)\,dx\\[0.45em]
&=\int_{0}^{\infty}\int_{0}^{x}f_{\sssig X}(x)\,dy\,dx-\int_{-\infty}^{0}\int_{0}^{-x}f_{\sssig X}(x)\,dy\,dx\\[0.45em]
&=\int_{0}^{\infty}\int_{y}^{\infty}f_{\sssig X}(x)\,dx\,dy-\int_{0}^{\infty}\int_{-\infty}^{-y}f_{\sssig X}(x)\,dx\,dy\\[0.45em]
&=\int_{0}^{\infty}\bigl[1-F_{\sssig X}(y)\bigr]\,dy-\int_{0}^{\infty}\bigl[F_{\sssig X}(-y)-0\bigr]\,dy\\[0.45em]
&=\int_{0}^{\infty}\bigl[1-F_{\sssig X}(y)\bigr]\,dy-\int_{-\infty}^{0}F_{\sssig X}(x)\,dx
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}&(X)=\int_{-\infty}^{\infty}xf_{\sssig X}(x)\,dx\\[0.45em]
&=\int_{0}^{\infty}xf_{\sssig X}(x)\,dx+\int_{-\infty}^{0}xf_{\sssig X}(x)\,dx\\[0.45em]
&=\int_{0}^{\infty}\left(\int_{0}^{x}1\,dy\right)f_{\sssig X}(x)\,dx\\[0.2em]
&\qquad\qquad-\int_{-\infty}^{0}\left(\int_{0}^{-x}1\,dy\right)f_{\sssig X}(x)\,dx\\[0.45em]
&=\int_{0}^{\infty}\int_{0}^{x}f_{\sssig X}(x)\,dy\,dx\\[0.2em]
&\qquad\qquad-\int_{-\infty}^{0}\int_{0}^{-x}f_{\sssig X}(x)\,dy\,dx\\[0.45em]
&=\int_{0}^{\infty}\int_{y}^{\infty}f_{\sssig X}(x)\,dx\,dy\\[0.2em]
&\qquad\qquad-\int_{0}^{\infty}\int_{-\infty}^{-y}f_{\sssig X}(x)\,dx\,dy\\[0.45em]
&=\int_{0}^{\infty}\bigl[1-F_{\sssig X}(y)\bigr]\,dy\\[0.2em]
&\qquad\qquad-\int_{0}^{\infty}\bigl[F_{\sssig X}(-y)-0\bigr]\,dy\\[0.45em]
&=\int_{0}^{\infty}\bigl[1-F_{\sssig X}(y)\bigr]\,dy-\int_{-\infty}^{0}F_{\sssig X}(x)\,dx
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

[Theorem 2.8](/teaching-topics/expectation/#thm-expectation-tail-sum) 的連續型版本，在工業領域經常被用來計算產品的故障前平均時間 <span lang="en">(mean time to failure, MTTF)</span>，這個特別的數字其實就是期望值，但在只能失效一次且不可修復的系統中，這個指標具有極重要的意義，多數用於計算產品的平均壽命。

</div>

<div id="thm-expectation-of-function" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.9 (函數期望值, expectation of a function)</div>

若 $X$ 為離散型隨機變數，$g(\cdot)$ 為一實值可測函數，且

$$
\sum_{x\in\mathbb{R}}\lvert g(x)\rvert\,p_{\sssig X}(x)<\infty
$$

則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\bigl[g(X)\bigr]=\sum_{x\in\mathbb{R}}g(x)\,p_{\sssig X}(x)=\sum_{x\in\mathcal{R}_{\sssig X}}g(x)\,p_{\sssig X}(x)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[g(X)\bigr]&=\sum_{x\in\mathbb{R}}g(x)\,p_{\sssig X}(x)\\[0.45em]
&=\sum_{x\in\mathcal{R}_{\sssig X}}g(x)\,p_{\sssig X}(x)
\end{aligned}
$$

</div>

若 $X$ 為連續型隨機變數，$g(\cdot)$ 為一實值可測函數，且

$$
\int_{x\in\mathbb{R}}\lvert g(x)\rvert f_{\sssig X}(x)\,dx<\infty
$$

則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\bigl[g(X)\bigr]=\int_{-\infty}^{\infty}g(x)\,f_{\sssig X}(x)\,dx=\int_{x\in\mathcal{R}_{\sssig X}}g(x)\,f_{\sssig X}(x)\,dx
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[g(X)\bigr]&=\int_{-\infty}^{\infty}g(x)\,f_{\sssig X}(x)\,dx\\[0.45em]
&=\int_{x\in\mathcal{R}_{\sssig X}}g(x)\,f_{\sssig X}(x)\,dx
\end{aligned}
$$

</div>

</div>

這個定理的計算細節，並不若我們的直覺這麼簡單，其牽涉到[隨機變數變換 <span lang="en">(transformation of random variable)</span>](/teaching-topics/one-to-one-transformations/)，我們將在本章的最後詳談，讀者在此可以直覺地直接計算即可。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

事實上，這個定理即使不知道如何證明，在使用上也毫無窒礙，因此，台大數學系的教授楊維哲，便曾在〈機率一講〉一文中提到:「這是個『不知亦能行的公式』<span lang="en">(law of unconscious statistician)</span>!」

</div>

<div id="ex-broken-stick-expected-length" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.9 <span lang="en">(Continued)</span></div>

<div lang="en" markdown="1">
Suppose that a stick of unit length is broken at a single point, and that the position $X$ of the break has the density

$$
f_{\sssig X}(x)=6\,x(1-x),\quad 0<x<1
$$

<ol class="topic-list-paren topic-list-paren--start-2">
  <li>Find the expected length of the piece that contains the midpoint.</li>
</ol>
</div>

(2) 含中點端之半邊必定為較長之半邊，故可令 $Y$ 表示較長端之長度，即
{: .topic-paren-item}

$$
Y=
\left\lbrace
\begin{array}{c@{\quad}l}
1-X, & 0<X\leqslant\dfrac{1}{2}\\[0.7em]
X, & \dfrac{1}{2}<X<1
\end{array}
\right.
$$

則所求為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(Y)=\int_{0}^{1/2}(1-x)\cdot6\,x(1-x)\,dx+\int_{1/2}^{1}x\cdot6\,x(1-x)\,dx=\frac{11}{16}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(Y)&=\int_{0}^{1/2}(1-x)\cdot6\,x(1-x)\,dx\\[0.45em]
&\qquad\qquad+\int_{1/2}^{1}x\cdot6\,x(1-x)\,dx\\[0.45em]
&=\frac{11}{16}
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

在這個問題中，我們很直觀地令 $Y=g(X)$，表示 $Y$ 是 $X$ 經過某個函數轉換後的結果，這個結果當然是一個隨機變數，並且其期望值的計算，很單純地就是

$$
\mathbb{E}(Y)=\mathbb{E}\bigl[g(X)\bigr]
$$

</div>

在操作的過程中，讀者應該隱約感覺到這個定理的威力。

事實上，我們曾在 [Definition 2.6](/teaching-topics/expectation/#def-expectation) 之後提到，期望值 (特別是離散型) 的概念中，可以將 $x$ 類比為位置，而 $p_{\sssig X}(x)$ 類比為該點的質量，則期望值就是質心；這個想法若沿用至此，質點的位置經過實值可測函數 $g(\cdot)$ 的轉換之後，函數期望值就是轉換過後的質心位置，由此來思考這個定理，便會容易許多。

<div id="thm-expectation-linearity" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.10 (期望值的性質, properties of expectation)</div>

若 $X$ 為隨機變數，$g_1(\cdot),\ldots,g_k(\cdot)$ 為實值可測函數，$a_1,\ldots,a_k,b$ 為常數，且對每一個 $i=1,\ldots,k$，$g_i(X)$ 的期望值皆存在，即 $X$ 為離散型時

$$
\sum_{x\in\mathbb{R}}\lvert g_i(x)\rvert\,p_{\sssig X}(x)<\infty
$$

$X$ 為連續型時

$$
\int_{x\in\mathbb{R}}\lvert g_i(x)\rvert f_{\sssig X}(x)\,dx<\infty
$$

則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\left[\sum_{i=1}^{k}a_i\,g_i(X)+b\right]=\sum_{i=1}^{k}a_i\,\mathbb{E}\bigl[g_i(X)\bigr]+b
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}\left[\sum_{i=1}^{k}a_i\,g_i(X)+b\right]\\[0.45em]
=&\sum_{i=1}^{k}a_i\,\mathbb{E}\bigl[g_i(X)\bigr]+b
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

[Theorem 2.10](#thm-expectation-linearity) 之所以要求各 $g_i(X)$ 的期望值存在，是因為結論的右側逐項寫出了 $\mathbb{E}[g_i(X)]$: 少了絕對可加總或絕對可積分的前提，這些期望值未必存在，右側的線性組合便無從定義。下面的證明把一個加總拆成 $k+1$ 個加總、再逐項把常數提到加總之外，這一步也要在每一個加總都收斂時才成立。這個前提與 [Theorem 2.9](#thm-expectation-of-function) 所要求的完全相同，只是逐一施加在 $g_1(\cdot),\ldots,g_k(\cdot)$ 之上。

</div>

<div class="topic-proof" markdown="1">
**Proof.**

我們在此以離散型變數為例，連續型變數可將加總改為積分，同理可得。

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\left[\sum_{i=1}^{k}a_i\,g_i(X)+b\right]&=\sum_{x\in\mathcal{R}_{\sssig X}}\left[\left(\sum_{i=1}^{k}a_i\,g_i(x)+b\right)p_{\sssig X}(x)\right]\\[0.45em]
&=\sum_{x\in\mathcal{R}_{\sssig X}}\left[\sum_{i=1}^{k}a_i\,g_i(x)\,p_{\sssig X}(x)+b\,p_{\sssig X}(x)\right]\\[0.45em]
&=\sum_{i=1}^{k}a_i\left[\sum_{x\in\mathcal{R}_{\sssig X}}g_i(x)\,p_{\sssig X}(x)\right]+b\sum_{x\in\mathcal{R}_{\sssig X}}p_{\sssig X}(x)\\[0.45em]
&=\sum_{i=1}^{k}a_i\,\mathbb{E}\bigl[g_i(X)\bigr]+b
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}\left[\sum_{i=1}^{k}a_i\,g_i(X)+b\right]\\[0.45em]
&=\sum_{x\in\mathcal{R}_{\sssig X}}\left[\left(\sum_{i=1}^{k}a_i\,g_i(x)+b\right)p_{\sssig X}(x)\right]\\[0.45em]
&=\sum_{x\in\mathcal{R}_{\sssig X}}\left[\sum_{i=1}^{k}a_i\,g_i(x)\,p_{\sssig X}(x)+b\,p_{\sssig X}(x)\right]\\[0.45em]
&=\sum_{i=1}^{k}a_i\left[\sum_{x\in\mathcal{R}_{\sssig X}}g_i(x)\,p_{\sssig X}(x)\right]+b\sum_{x\in\mathcal{R}_{\sssig X}}p_{\sssig X}(x)\\[0.45em]
&=\sum_{i=1}^{k}a_i\,\mathbb{E}\bigl[g_i(X)\bigr]+b
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

上述定理即說明了「期望值對線性函數具有可交換性」，意思是指期望值內若是線性函數的形式，則我們可以**先取期望值再做線性函數**；而非線性函數的部分 (如 $g_i(X)$) 則運用 [Theorem 2.9](#thm-expectation-of-function) 來進行運算。

</div>

[Theorem 2.10](#thm-expectation-linearity) 是一個複合性質的定理，我們可以透過設定 $g_i(\cdot)$ 與各常數的值，來得到許多有用的子性質，見以下設定。

(1) 設定 $a_1=\cdots=a_k=0$，則有
{: .topic-paren-item}

$$
\mathbb{E}(b)=b
$$

此即**常數的期望值還是自己本身**。
{: .topic-paren-cont}

(2) 設定 $k=1$ 且 $a_1=1$、$g_1(X)=X$，則有
{: .topic-paren-item}

$$
\mathbb{E}(X+b)=\mathbb{E}(X)+b
$$

此即**隨機變數的平移期望值是期望值的平移**。
{: .topic-paren-cont}

(3) 設定 $k=1$ 且 $g_1(X)=X$、$b=0$，則有
{: .topic-paren-item}

$$
\mathbb{E}(a_1X)=a_1\,\mathbb{E}(X)
$$

此即**隨機變數的倍數期望值是期望值的倍數**。
{: .topic-paren-cont}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個性質與後續要提到的**[變異數](/teaching-topics/variance/#def-variance) <span lang="en">(variance)</span>** 的[**平方伸縮 (scaled by square)**](/teaching-topics/variance/#thm-variance-properties) 性質具有很大的區別，我們將在介紹變異數時一併詳談。

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

值得注意的是，若所設定的 $g(\cdot)$ 為非負 (或非正) 函數，則其期望值 $\mathbb{E}\bigl[g(X)\bigr]$ 亦為非負 (或非正)。其理由是 pmf $p_{\sssig X}(x)$ 或 pdf $f_{\sssig X}(x)$ 都是非負函數，故依照期望值的定義，若 $g(X)$ 具有非負 (或非正) 的性質，其乘積亦具有非負 (或非正) 的性質，則進行加總或積分後仍具有非負 (或非正) 的性質。

</div>

<div id="ex-shifted-linear-density-expectation" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.18</div>

<div lang="en" markdown="1">
Suppose that the random variable $X$ has the probability density function

$$
f_{\sssig X}(x)=\frac{x+2}{6},\quad 0<x<2
$$

Find $\mathbb{E}\bigl[(X+2)^{2}\bigr]$.
</div>

所求為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[(X+2)^{2}\bigr]&=\int_{0}^{2}(x+2)^{2}\times\frac{x+2}{6}\,dx=\frac{1}{6}\int_{0}^{2}(x+2)^{3}\,dx\\[0.45em]
&=\frac{1}{6}\int_{0}^{2}(x+2)^{3}\,d(x+2)=\frac{1}{6}\times\left[\frac{(x+2)^{4}}{4}\right]_{0}^{2}\\[0.45em]
&=\frac{256}{24}-\frac{16}{24}=10
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[(X+2)^{2}\bigr]&=\int_{0}^{2}(x+2)^{2}\times\frac{x+2}{6}\,dx\\[0.45em]
&=\frac{1}{6}\int_{0}^{2}(x+2)^{3}\,dx\\[0.45em]
&=\frac{1}{6}\int_{0}^{2}(x+2)^{3}\,d(x+2)\\[0.45em]
&=\frac{1}{6}\times\left[\frac{(x+2)^{4}}{4}\right]_{0}^{2}\\[0.45em]
&=\frac{256}{24}-\frac{16}{24}=10
\end{aligned}
$$

</div>

</div>

## 本篇小結

[Example 2.16](#ex-car-offer-waiting-time) 與 [Example 2.17](#ex-expectation-tail-formula) 是期望值定義的兩個延伸: 前者以尾機率加總求得的期望值為無限大，說明期望值不必然是有限的；後者把非負隨機變數的尾機率表示推廣到一般的連續型隨機變數，期望值可以寫成 $1-F_{\sssig X}(x)$ 在正半軸的積分減去 $F_{\sssig X}(x)$ 在負半軸的積分，這正是工業上計算故障前平均時間的依據。

[Theorem 2.9](#thm-expectation-of-function) 給出函數期望值。在絕對可加總或絕對可積分的前提下，$\mathbb{E}[g(X)]$ 是以 $X$ 的 pmf 或 pdf 對 $g(x)$ 加權求和或積分，不必先求出 $g(X)$ 的分配。以質點的類比來說，這是把質點的位置經過 $g(\cdot)$ 轉換之後的質心。[Example 2.9 <span lang="en">(Continued)</span>](#ex-broken-stick-expected-length) 即以此求出折棒後含中點那一段的期望長度 $\frac{11}{16}$。

[Theorem 2.10](#thm-expectation-linearity) 則說明期望值對線性函數具有可交換性，線性的部分可以先取期望值再做線性函數，非線性的部分交由 [Theorem 2.9](#thm-expectation-of-function) 處理。它是一個複合性質的定理，設定各常數之後可以得到常數的期望值還是自己本身、平移的期望值是期望值的平移、倍數的期望值是期望值的倍數三個子性質，另外還可以知道非負 (或非正) 函數的期望值亦為非負 (或非正)。[Example 2.18](#ex-shifted-linear-density-expectation) 則是函數期望值的直接計算。[下一篇](/teaching-topics/variance/)討論隨機變數的變異數。

## 參考文獻與延伸閱讀

- 楊維哲，1978，〈機率一講〉，《數學傳播》，2 卷 3 期。
- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Joseph K. Blitzstein and Jessica Hwang. 2019. *Introduction to Probability*. 2nd ed. Chapman and Hall/CRC.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
