---
title: "期望值的性質與函數期望值"
subtitle: "Properties of Expectation and Expectation of a Function"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 7
order: 207
permalink: /lecture-notes/properties-of-expectation/
date: 2026-08-06
published: true
excerpt: "函數期望值定理允許直接以原變數的機率函數求算 $g(X)$ 的期望值，無須先求轉換後的分配。本篇並推導期望值對線性組合的可交換性與平移、伸縮性質。"
---

[上一篇](/lecture-notes/expectation/)給出[期望值](/lecture-notes/expectation/#def-expectation)的定義，並以非負[隨機變數](/lecture-notes/random-variables-and-pmf/#def-random-variable)的尾機率表示作結。

本篇分為三個部分。首先介紹期望值的特殊算法，有些隨機變數不必先寫出 pmf 或 pdf 再逐項加總，改由尾機率的加總或 cdf 的積分反而容易計算；本篇前兩道例題分別示範非負整數型與連續型的做法，前者順帶說明期望值可能發散，後者則將尾機率表示式推廣到一般的連續型隨機變數。接著討論函數期望值，若我們關心的不是 $X$ 本身，而是經過函數轉換後的 $g(X)$，其期望值不必先求出 $g(X)$ 的分配，直接以 $X$ 的 pmf 或 pdf 對 $g(x)$ 加權即可。最後說明期望值的線性可交換性質，並藉由設定各常數導出三個常用的子性質。

<div id="ex-car-offer-waiting-time" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.16</div>

<div lang="en" markdown="1">
Suppose you are selling a car, and let $X_{0},X_{1},X_{2},\ldots$ be the successive offers received at times $0,1,2,\ldots$, assumed to be independent and identically distributed. Let

$$
N=\min\lbrace n\mid X_{n}>X_{0}\rbrace
$$

be the first time an offer exceeds the initial offer $X_{0}$ at time $0$. Show that $\mathbb{E}(N)=\infty$.
</div>

由於 $N=\min\lbrace n\mid X_n>X_0\rbrace$，故對任意 $N=k$ 之事件而言，在 $X_0,X_1,\ldots,X_{k-1},X_k$ 之中，$X_k$ 為此 $k+1$ 個隨機變數中最大者，且 $X_0$ 為此 $k+1$ 個隨機變數中第二大者。

又設各次出價 $X_0,X_1,X_2,\ldots$ 為 iid <span lang="en">(independent and identically distributed)</span> 的連續型隨機變數 (因此出價金額完全相同的機率為零)，故 $X_0,X_1,\ldots,X_k$ 這 $k+1$ 個變數的大小順序共有 $(k+1)!$ 種排法，每一種排法的機率均等，滿足 $N=k$ 之事件機率因而為

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

又 $N$ 為非負整數隨機變數，故由 [Theorem 2.8](/lecture-notes/expectation/#thm-expectation-tail-sum) 可得

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

iid 將於[下一章](/lecture-notes/independent-random-variables/)正式定義，指多個隨機變數彼此獨立 <span lang="en">(independent)</span> 且同分配 <span lang="en">(identically distributed)</span>；現階段可先視為各次出價互不影響，且遵循相同的機率分配。此外，題幹雖未明言出價金額為連續型分配，解答中補充連續型的假設，是為確保任意兩次出價金額相同的機率為零，使 $k+1$ 個變數具有嚴格大小順序且 $(k+1)!$ 種排列機率均等 (若為可能出現平手的離散型分配，$\mathbb{E}(N)=\infty$ 的結論依然成立，僅推導時須另行處理平手事件)。

本題求和運用三項技巧。其一是以 iid 對稱性將隨機變數問題化為古典機率排列計數；其二是利用**裂項和 <span lang="en">(telescoping sum)</span>** (高中數學亦稱「分項對消法」)，將 $\frac{1}{k(k+1)}$ 拆為 $\frac{1}{k}-\frac{1}{k+1}$ 求得內層級數；其三是利用**調和級數 <span lang="en">(harmonic series)</span>** 的發散性，證得期望值為無限大。

</div>

<div id="ex-expectation-tail-formula" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.17</div>

<div lang="en" markdown="1">
Let $X$ be a continuous random variable with probability density function $f_{\sssig X}(x)$ and cumulative distribution function $F_{\sssig X}(x)$, and suppose that $\mathbb{E}\lvert X\rvert<\infty$. Show that

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

由期望值定義，將積分範圍以 $0$ 為界拆成兩段，把 $x$ 寫成 $\int_{0}^{x}1\,dy$ 後交換積分順序，最後於後一項令 <span class="text-nowrap">$x=-y$，</span>可得

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

[Theorem 2.8](/lecture-notes/expectation/#thm-expectation-tail-sum) 的連續型公式在工業可靠度分析中常用以計算產品的故障前平均時間 <span lang="en">(mean time to failure, MTTF)</span>。MTTF 在數學上即壽命隨機變數的期望值，對於一旦失效便無法修復的系統而言，是衡量產品平均壽命的重要指標。

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

[Theorem 2.9](#thm-expectation-of-function) 背後的嚴謹證明牽涉本章末節介紹的[隨機變數變換 <span lang="en">(transformation of random variable)</span>](/lecture-notes/one-to-one-transformations/)，現階段直接依上述加權公式計算即可。由於即使尚未深究證明細節亦能順利套用，楊維哲教授曾在〈機率一講〉一文中將此定理稱為「不知亦能行的公式」<span lang="en">(law of unconscious statistician)</span>。

<div id="ex-broken-stick-expected-length" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.9 <span lang="en">(Continued)</span></div>

<div lang="en" markdown="1">
Suppose we break a stick of unit length at a point $X$ whose position has the density

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

上題將較長那一段的長度表為分段函數 <span class="text-nowrap">$Y=g(X)$，</span>無須先求 $Y$ 本身的機率密度函數，即可直接由 $\mathbb{E}(Y)=\mathbb{E}\bigl[g(X)\bigr]$ 對 $f_{\sssig X}(x)$ 積分求得期望值。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

延續 [Definition 2.6](/lecture-notes/expectation/#def-expectation) 後的質心類比，若將離散取值 $x$ 視為質點位置、機率 $p_{\sssig X}(x)$ 視為該點質量，則 $\mathbb{E}(X)$ 為原位置的質心；當各質點位置經實值可測函數 $g(\cdot)$ 映射至 $g(x)$ 而質量 $p_{\sssig X}(x)$ 維持不變時，函數期望值 $\mathbb{E}\bigl[g(X)\bigr]$ 即為轉換後新位置的質心。

</div>

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
&=\sum_{i=1}^{k}a_i\,\mathbb{E}\bigl[g_i(X)\bigr]+b
\end{aligned}
$$

</div>

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

上述定理說明了「期望值對線性函數具有可交換性」，亦即期望值內若為線性組合的形式，可**先各自取期望值再做線性組合**；至於非線性函數的部分 (如各個 $g_i(X)$ 項) 則運用 [Theorem 2.9](#thm-expectation-of-function) 計算。

定理前提要求每個 $g_i(X)$ 的期望值皆存在 (即絕對收斂)，因證明中須將單一無窮級數 (或瑕積分) 拆為 $k+1$ 項並分別提出常數；唯有各項各自絕對收斂時拆項才成立，亦能避免出現 $\infty-\infty$ 等不定型。

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

此一性質說明**隨機變數的平移期望值是期望值的平移**。
{: .topic-paren-cont}

(3) 設定 $k=1$ 且 $g_1(X)=X$、$b=0$，則有
{: .topic-paren-item}

$$
\mathbb{E}(a_1X)=a_1\,\mathbb{E}(X)
$$

此即**隨機變數的倍數期望值是期望值的倍數**；這一點與後文**[變異數](/lecture-notes/variance/#def-variance) <span lang="en">(variance)</span>** 的[**平方伸縮**](/lecture-notes/variance/#thm-variance-properties)性質不同，屆時將一併對照。
{: .topic-paren-cont}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

此外，若實值可測函數 $g(\cdot)$ 為非負 (或非正)，且 $\mathbb{E}\bigl[g(X)\bigr]$ 存在，則 $\mathbb{E}\bigl[g(X)\bigr]$ 亦必為非負 (或非正)。原因在於 $p_{\sssig X}(x)$ 與 $f_{\sssig X}(x)$ 皆恆非負，故 $g(x)$ 與機率函數相乘後保持原正負號，加總或積分後亦同。

</div>

<div id="ex-shifted-linear-density-expectation" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.18</div>

<div lang="en" markdown="1">
Suppose that

$$
f_{\sssig X}(x)=\frac{x+2}{6},\quad 0<x<2
$$

is the pdf of a random variable $X$. Find $\mathbb{E}\bigl[(X+2)^{2}\bigr]$.
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

[Example 2.16](#ex-car-offer-waiting-time) 與 [Example 2.17](#ex-expectation-tail-formula) 是期望值定義的兩個延伸。前者以尾機率加總求得的期望值為無限大，說明期望值不必然有限；後者把非負隨機變數的尾機率表示推廣到一般的連續型隨機變數，將期望值寫成 $1-F_{\sssig X}(x)$ 在正半軸的積分減去 $F_{\sssig X}(x)$ 在負半軸的積分，這正是工業上計算故障前平均時間的依據。

[Theorem 2.9](#thm-expectation-of-function) 給出函數期望值。在絕對可加總或絕對可積分的前提下，$\mathbb{E}[g(X)]$ 是以 $X$ 的 pmf 或 pdf 對 $g(x)$ 加權求和或積分，不必先求出 $g(X)$ 的分配。以質點的類比來說，這是把質點的位置經過 $g(\cdot)$ 轉換之後的質心。[Example 2.9 <span lang="en">(Continued)</span>](#ex-broken-stick-expected-length) 即以此求出折棒後含中點那一段的期望長度 $\frac{11}{16}$。

[Theorem 2.10](#thm-expectation-linearity) 則說明期望值對線性函數具有可交換性，線性的部分可以先取期望值再做線性函數，非線性的部分交由 [Theorem 2.9](#thm-expectation-of-function) 處理。它是一個複合性質的定理，設定各常數之後可以得到常數的期望值還是自己本身、平移的期望值是期望值的平移、倍數的期望值是期望值的倍數三個子性質，另外還可以知道非負 (或非正) 函數的期望值亦為非負 (或非正)。[Example 2.18](#ex-shifted-linear-density-expectation) 則是函數期望值的直接計算。[下一篇](/lecture-notes/variance/)討論隨機變數的變異數。

## 參考文獻與延伸閱讀

- 楊維哲，1978，〈機率一講〉，《數學傳播》，2 卷 3 期。
- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Joseph K. Blitzstein and Jessica Hwang. 2019. *Introduction to Probability*. 2nd ed. Chapman and Hall/CRC.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
