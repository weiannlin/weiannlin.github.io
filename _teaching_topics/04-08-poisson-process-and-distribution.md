---
title: "卜瓦松過程與卜瓦松分配"
subtitle: "The Poisson Process and the Poisson Distribution"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 4
topic: 8
order: 408
permalink: /lecture-notes/poisson-process-and-distribution/
date: 2026-08-12
published: false
excerpt: "卜瓦松過程用來描述偶發事件的發生行為，由五個條件界定，其中最要緊的是不重疊時間區間內的發生次數彼此獨立，而且極短區間內幾乎不會發生兩次以上。單位時間內偶發事件的發生次數即服從卜瓦松分配，機率函數為 $\\frac{e^{-\\lambda}\\lambda^{x}}{x!}$ 這個式子，期望值與變異數都等於 $\\lambda$，動差母函數則是 $e^{\\lambda(e^{t}-1)}$。本篇先給出驗證機率函數合法所需要的馬克勞林級數，再完整推導期望值、變異數與動差母函數，並證明兩個獨立的卜瓦松變數相加仍為卜瓦松分配。最後證明二項分配在 $n$ 趨近於無限大、$p$ 趨近於 $0$ 且 $np=\\lambda$ 之下會收斂到卜瓦松分配，這正是實務上以卜瓦松機率近似二項機率的依據。"
---

[上一篇](/lecture-notes/hypergeometric-distribution/)介紹[超幾何分配](/lecture-notes/hypergeometric-distribution/#def-hypergeometric)，至此伯努利實驗相關的機率模型已經全部給出。這一類模型所記錄的，都是在指定次數的實驗之中成功發生了幾次，或者為了取得指定次數的成功而必須做幾次實驗。本篇轉入第二大類的機率模型，也就是由卜瓦松過程所衍生的各個分配。

卜瓦松過程描述的是偶發事件在一段時間之內的發生行為，它所關心的量是一段長度為 $t$ 的時間之內，偶發事件的發生次數。本篇先給出卜瓦松過程的定義，列出它下轄的四個分配，再進入其中最基本的卜瓦松分配；由於驗證卜瓦松分配的機率函數合法時要用到指數函數的馬克勞林級數，這個級數會排在定義之前給出。

## 卜瓦松過程

<div id="def-poisson-process" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 4.10 (卜瓦松過程, Poisson process)</div>

**卜瓦松過程 <span lang="en">(Poisson process)</span>** 是一種用來描述**偶發事件 (rare event)** 之行為的過程，若定義 $N(t)$ 表示區間長度為 $t$ 的時間區間內，偶發事件的發生個數，則其應滿足以下條件:

(1) 時間長度為 $0$ 時，不會有偶發事件，此即
{: .topic-paren-item}

$$
N(0)=0
$$

(2) 偶發事件在該區間內發生的機率與區間起點無關，而只與區間長度有關，此即
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\text{若}\ 0<t_1<t_2,\ 0<t_3<t_4\ \text{且}\ t_2-t_1=t_4-t_3\\[0.45em]
\text{則}\ \mathbb{P}\bigl(N(t_2-t_1)=m\bigr)=\mathbb{P}\bigl(N(t_4-t_3)=m\bigr),\ m=0,1,2,\ldots
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\text{若}\ 0<t_1<t_2,\ 0<t_3<t_4\\[0.3em]
&\text{且}\ t_2-t_1=t_4-t_3\\[0.55em]
&\text{則}\ \mathbb{P}\bigl(N(t_2-t_1)=m\bigr)\\[0.3em]
&=\mathbb{P}\bigl(N(t_4-t_3)=m\bigr),\\[0.3em]
&m=0,1,2,\ldots
\end{aligned}
$$

</div>

(3) 不重疊的時間區間內，偶發事件的發生次數彼此獨立，此即
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\text{若}\ 0<t_1<t_2<t_3<t_4\text{，則}\ N(t_2-t_1)\indep N(t_4-t_3)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\text{若}\ 0<t_1<t_2<t_3<t_4，\\[0.3em]
&\text{則}\ N(t_2-t_1)\indep N(t_4-t_3)
\end{aligned}
$$

</div>

(4) 在極短的時間區間內，偶發事件發生兩次以上的機率趨近於 <span class="text-nowrap">$0$，</span>此即
{: .topic-paren-item}

$$
\lim_{t\to0}\mathbb{P}\bigl(N(t)\geqslant2\bigr)=0
$$

(5) 偶發事件在該區間內發生一次的機率與該區間的長度成正比，此即
{: .topic-paren-item}

$$
\mathbb{P}\bigl(N(t)=1\bigr)=\lambda t,\ \lambda>0
$$

此性質亦被稱作比例伸縮性。
{: .topic-paren-cont}

</div>

卜瓦松過程是以法國數學家 Siméon Denis Poisson (1781-1840) 的姓氏命名。[^poisson-name]

卜瓦松過程有一些地方需要注意:

(1) 偶發事件是指「只有很低的機率發生的事件」，而在卜瓦松過程中，這樣的事件**在同一個瞬間幾乎不會發生兩次以上**，此即上述的 (4) 所指涉的情形。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

在嚴謹的數學定義中我們會特別指出 $\mathbb{P}\bigl(N(t)\geqslant2\bigr)=o(t)$ 這個等式，其中的 $o(\cdot)$ 是小 o 符號 <span lang="en">(little o notation)</span>，[^little-o]但在本系列的範圍中，讀者可以僅理解為 $\lim_{t\to0}\mathbb{P}\bigl(N(t)\geqslant2\bigr)=0$ 即可。

</div>

(2) 卜瓦松過程是一種定義在時間區段的隨機過程，但事實上，我們也可以將其定義的範圍推廣至任意的**正實數區間**或甚至是任意的**有限維度正實數區間**，實務上的例子是任意線段、平面、空間等等的區間，這也給了卜瓦松過程在使用上相當程度的方便。
{: .topic-paren-item}

(3) 上述 (5) 中，$\lambda$ 是卜瓦松過程的參數，代表**平均發生率 <span lang="en">(mean occurrence rate)</span>**。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

事實上，(5) 中所指涉的性質，比較嚴謹的寫法應該是 $\mathbb{P}\bigl(N(t)=1\bigr)=\lambda t+o(t),\ \lambda>0$ 這個式子，但讀者在本系列中同樣可理解為 $\mathbb{P}\bigl(N(t)=1\bigr)=\lambda t,\ \lambda>0$ 即可。

</div>

卜瓦松過程下轄許多重要的分配，這其中包含:

<ol class="topic-list-paren">
  <li>卜瓦松分配 <span lang="en">(Poisson distribution)</span></li>
  <li>指數分配 <span lang="en">(exponential distribution)</span></li>
  <li>伽瑪分配 <span lang="en">(gamma distribution)</span></li>
  <li>韋伯分配 <span lang="en">(Weibull distribution)</span></li>
</ol>

這些分配之間的關係匪淺，以下就分別敘述這些分配，並說明其之間的關係。

## 馬克勞林級數

<div id="thm-maclaurin-series" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 4.9 (馬克勞林級數, Maclaurin series)</div>

針對**指數函數 <span lang="en">(exponential function)</span>** 的**馬克勞林級數 <span lang="en">(Maclaurin series)</span>** 是下列的級數:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
e^{\lambda}=e^{0}\frac{\lambda^{0}}{\,0!\,}+e^{0}\frac{\lambda^{1}}{\,1!\,}+e^{0}\frac{\lambda^{2}}{\,2!\,}+\cdots=\sum_{x=0}^{\infty}\frac{\lambda^{x}}{\,x!\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
e^{\lambda}&=e^{0}\frac{\lambda^{0}}{\,0!\,}+e^{0}\frac{\lambda^{1}}{\,1!\,}+e^{0}\frac{\lambda^{2}}{\,2!\,}+\cdots\\[0.35em]
&=\sum_{x=0}^{\infty}\frac{\lambda^{x}}{\,x!\,}
\end{aligned}
$$

</div>

</div>

馬克勞林級數是泰勒級數 <span lang="en">(Taylor’s series)</span> 的一個特例，專指將函數在 $0$ 展開的泰勒級數。此處的馬克勞林級數便是針對指數函數的馬克勞林級數。

## 卜瓦松分配

<div id="def-poisson-distribution" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 4.11 (卜瓦松分配, Poisson distribution)</div>

**適用範圍**:

令 $X$ 表示在單位時間內，卜瓦松過程中偶發事件發生的次數。

**值域範圍**:

$$
\mathcal{R}_{\sssig X}=\lbrace\,0,1,2,\ldots,\infty\,\rbrace
$$

**表示式**:

$$
X\sim\mathrm{Poi}(\lambda)
$$

**參數與參數範圍**:

$\lambda>0$ 表示單位時間內，偶發事件的平均發生率，也表示偶發事件的期望發生次數。

**機率函數**:

$$
p_{\sssig X}(x)=\frac{e^{-\lambda}\lambda^{x}}{\,x!\,},\ x=0,1,\ldots,\infty
$$

**期望值、變異數、動差母函數**:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\mathbb{E}(X)=\lambda,\quad \mathrm{Var}(X)=\lambda\\[0.45em]
M_{\sssig X}(t)=e^{\lambda(e^{t}-1)},\ t\in\mathbb{R}
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\lambda,\\[0.45em]
\mathrm{Var}(X)&=\lambda\\[0.45em]
M_{\sssig X}(t)&=e^{\lambda(e^{t}-1)},\ t\in\mathbb{R}
\end{aligned}
$$

</div>

</div>

卜瓦松分配有一些地方需要注意:

(1) 我們證明其機率函數為一個合法的機率函數與期望值、變異數與動差母函數如下:
{: .topic-paren-item}

<div class="topic-proof" markdown="1">
**Proof.**

先驗證機率函數的加總為 <span class="text-nowrap">$1$，</span>即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\sum_{x\in\mathcal{R}_{\sssig X}}p_{\sssig X}(x)=\sum_{x=0}^{\infty}\frac{e^{-\lambda}\lambda^{x}}{\,x!\,}=e^{-\lambda}\sum_{x=0}^{\infty}\frac{\lambda^{x}}{\,x!\,}=e^{-\lambda}e^{\lambda}=1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\sum_{x\in\mathcal{R}_{\sssig X}}p_{\sssig X}(x)&=\sum_{x=0}^{\infty}\frac{e^{-\lambda}\lambda^{x}}{\,x!\,}\\[0.4em]
&=e^{-\lambda}\sum_{x=0}^{\infty}\frac{\lambda^{x}}{\,x!\,}\\[0.4em]
&=e^{-\lambda}e^{\lambda}=1
\end{aligned}
$$

</div>

接著求期望值，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\sum_{x=0}^{\infty}x\frac{e^{-\lambda}\lambda^{x}}{\,x!\,}=\sum_{x=1}^{\infty}\frac{e^{-\lambda}\lambda^{x}}{\,(x-1)!\,}=\lambda\sum_{x=1}^{\infty}\frac{e^{-\lambda}\lambda^{x-1}}{\,(x-1)!\,}\\[0.45em]
&=\lambda e^{-\lambda}\sum_{y=0}^{\infty}\frac{\lambda^{y}}{\,y!\,}=\lambda e^{-\lambda}e^{\lambda}=\lambda
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\sum_{x=0}^{\infty}x\frac{e^{-\lambda}\lambda^{x}}{\,x!\,}\\[0.4em]
&=\sum_{x=1}^{\infty}\frac{e^{-\lambda}\lambda^{x}}{\,(x-1)!\,}\\[0.4em]
&=\lambda\sum_{x=1}^{\infty}\frac{e^{-\lambda}\lambda^{x-1}}{\,(x-1)!\,}\\[0.4em]
&=\lambda e^{-\lambda}\sum_{y=0}^{\infty}\frac{\lambda^{y}}{\,y!\,}\\[0.4em]
&=\lambda e^{-\lambda}e^{\lambda}=\lambda
\end{aligned}
$$

</div>

又可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[X(X-1)\bigr]&=\sum_{x=0}^{\infty}x(x-1)\frac{e^{-\lambda}\lambda^{x}}{\,x!\,}=\sum_{x=2}^{\infty}\frac{e^{-\lambda}\lambda^{x}}{\,(x-2)!\,}\\[0.45em]
&=\lambda^{2}\sum_{x=2}^{\infty}\frac{e^{-\lambda}\lambda^{x-2}}{\,(x-2)!\,}=\lambda^{2}e^{-\lambda}\sum_{y=0}^{\infty}\frac{\lambda^{y}}{\,y!\,}=\lambda^{2}e^{-\lambda}e^{\lambda}=\lambda^{2}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[X(X-1)\bigr]&=\sum_{x=0}^{\infty}x(x-1)\frac{e^{-\lambda}\lambda^{x}}{\,x!\,}\\[0.4em]
&=\sum_{x=2}^{\infty}\frac{e^{-\lambda}\lambda^{x}}{\,(x-2)!\,}\\[0.4em]
&=\lambda^{2}\sum_{x=2}^{\infty}\frac{e^{-\lambda}\lambda^{x-2}}{\,(x-2)!\,}\\[0.4em]
&=\lambda^{2}e^{-\lambda}\sum_{y=0}^{\infty}\frac{\lambda^{y}}{\,y!\,}\\[0.4em]
&=\lambda^{2}e^{-\lambda}e^{\lambda}=\lambda^{2}
\end{aligned}
$$

</div>

由此可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\bigl(X^{2}\bigr)=\mathbb{E}\bigl[X(X-1)\bigr]+\mathbb{E}(X)=\lambda^{2}+\lambda
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl(X^{2}\bigr)&=\mathbb{E}\bigl[X(X-1)\bigr]+\mathbb{E}(X)\\[0.4em]
&=\lambda^{2}+\lambda
\end{aligned}
$$

</div>

則變異數為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}(X)=\mathbb{E}\bigl(X^{2}\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}=\lambda^{2}+\lambda-\bigl(\lambda\bigr)^{2}=\lambda
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(X)&=\mathbb{E}\bigl(X^{2}\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}\\[0.4em]
&=\lambda^{2}+\lambda-\bigl(\lambda\bigr)^{2}=\lambda
\end{aligned}
$$

</div>

最後求動差母函數，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{\sssig X}(t)&=\mathbb{E}\bigl(e^{tX}\bigr)=\sum_{x=0}^{\infty}e^{tx}\frac{e^{-\lambda}\lambda^{x}}{\,x!\,}=\sum_{x=0}^{\infty}\frac{e^{-\lambda}\bigl(\lambda e^{t}\bigr)^{x}}{\,x!\,}=e^{-\lambda}\sum_{x=0}^{\infty}\frac{\bigl(\lambda e^{t}\bigr)^{x}}{\,x!\,}\\[0.45em]
&=e^{-\lambda}e^{\lambda e^{t}}=e^{\lambda(e^{t}-1)},\ t\in\mathbb{R}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig X}(t)&=\mathbb{E}\bigl(e^{tX}\bigr)\\[0.4em]
&=\sum_{x=0}^{\infty}e^{tx}\frac{e^{-\lambda}\lambda^{x}}{\,x!\,}\\[0.4em]
&=\sum_{x=0}^{\infty}\frac{e^{-\lambda}\bigl(\lambda e^{t}\bigr)^{x}}{\,x!\,}\\[0.4em]
&=e^{-\lambda}\sum_{x=0}^{\infty}\frac{\bigl(\lambda e^{t}\bigr)^{x}}{\,x!\,}\\[0.4em]
&=e^{-\lambda}e^{\lambda e^{t}}=e^{\lambda(e^{t}-1)},\ t\in\mathbb{R}
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

(2) **卜瓦松分配**的定義可以得到以下幾個延伸性質:
{: .topic-paren-item}

第一，若 $X\sim\mathrm{Poi}(\lambda_1),\ Y\sim\mathrm{Poi}(\lambda_2)$ 且 <span class="text-nowrap">$X\indep Y$，</span>則有
{: .topic-paren-cont}

$$
W=X+Y\sim\mathrm{Poi}(\lambda_1+\lambda_2)
$$

<div class="topic-proof" markdown="1">
**Proof.**

由[獨立隨機變數線性組合的動差母函數之定理](/lecture-notes/mgf-method-transformations/#thm-mgf-two-to-one)可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
M_{\sssig W}(t)=M_{\sssig X}(t)\,M_{\sssig Y}(t)=\Bigl[e^{\lambda_1(e^{t}-1)}\Bigr]\Bigl[e^{\lambda_2(e^{t}-1)}\Bigr]=e^{(\lambda_1+\lambda_2)(e^{t}-1)}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig W}(t)&=M_{\sssig X}(t)\,M_{\sssig Y}(t)\\[0.4em]
&=\Bigl[e^{\lambda_1(e^{t}-1)}\Bigr]\Bigl[e^{\lambda_2(e^{t}-1)}\Bigr]\\[0.4em]
&=e^{(\lambda_1+\lambda_2)(e^{t}-1)}
\end{aligned}
$$

</div>

則由[動差母函數的唯一性](/lecture-notes/uniqueness-of-the-mgf/#thm-mgf-uniqueness)可知

$$
W=X+Y\sim\mathrm{Poi}(\lambda_1+\lambda_2)
$$

原式得證。 <span class="topic-qed">$\square$</span>
</div>

這個性質被稱作卜瓦松分配的**可加性**，其限制是 $X$ 與 $Y$ 必須獨立。
{: .topic-paren-cont}

第二，在[二項分配](/lecture-notes/binomial-distribution/#def-binomial)中，若 $n\to\infty,\ p\to0$ 且 <span class="text-nowrap">$np=\lambda$，</span>則有
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\boxed{\ X\sim\mathrm{Bin}(n,\ p)\ \xrightarrow[n\to\infty,\ p\to0,\ np=\lambda]{\ \mathrm{d}\ }\ W\sim\mathrm{Poi}(\lambda)\ }
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\boxed{
\begin{aligned}
X&\sim\mathrm{Bin}(n,\ p)\\[0.25em]
&\xrightarrow[n\to\infty,\ p\to0,\ np=\lambda]{\ \mathrm{d}\ }\\[0.25em]
W&\sim\mathrm{Poi}(\lambda)
\end{aligned}
}
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.**

令 <span class="text-nowrap">$X\sim\mathrm{Bin}(n,\ p)$，</span>若 $n\to\infty,\ p\to0$ 且 <span class="text-nowrap">$np=\lambda$，</span>則有

$$
p=\frac{\lambda}{\,n\,}
$$

則由[二項分配](/lecture-notes/binomial-distribution/#def-binomial)的 pmf，我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
p_{\sssig X}(x)&=\lim_{n\to\infty}\binom{n}{x}p^{x}(1-p)^{n-x}\\[0.45em]
&=\lim_{n\to\infty}\frac{n!}{\,x!(n-x)!\,}\biggl(\frac{\lambda}{\,n\,}\biggr)^{x}\biggl(1-\frac{\lambda}{\,n\,}\biggr)^{n-x}\\[0.45em]
&=\frac{\lambda^{x}}{\,x!\,}\times\lim_{n\to\infty}\frac{n!}{\,(n-x)!\,}\biggl(\frac{1}{\,n\,}\biggr)^{x}\biggl(1-\frac{\lambda}{\,n\,}\biggr)^{n-x}\\[0.45em]
&=\frac{\lambda^{x}}{\,x!\,}\times\lim_{n\to\infty}\frac{n!}{\,n^{x}(n-x)!\,}\biggl(1-\frac{\lambda}{\,n\,}\biggr)^{n}\biggl(1-\frac{\lambda}{\,n\,}\biggr)^{-x}\\[0.45em]
&=\frac{\lambda^{x}}{\,x!\,}\times\lim_{n\to\infty}\frac{n\times\cdots\times(n-x+1)}{\,n\times\cdots\times n\,}\biggl(1-\frac{\lambda}{\,n\,}\biggr)^{n}\biggl(1-\frac{\lambda}{\,n\,}\biggr)^{-x}\\[0.45em]
&=\frac{\lambda^{x}}{\,x!\,}\times1\times e^{-\lambda}\times1=\frac{e^{-\lambda}\lambda^{x}}{\,x!\,},\ x=0,1,\ldots,\infty
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig X}(x)&=\lim_{n\to\infty}\binom{n}{x}p^{x}(1-p)^{n-x}\\[0.4em]
&=\lim_{n\to\infty}\frac{n!}{\,x!(n-x)!\,}\biggl(\frac{\lambda}{\,n\,}\biggr)^{x}\\[0.25em]
&\qquad\qquad \biggl(1-\frac{\lambda}{\,n\,}\biggr)^{n-x}\\[0.4em]
&=\frac{\lambda^{x}}{\,x!\,}\times\lim_{n\to\infty}\frac{n!}{\,(n-x)!\,}\biggl(\frac{1}{\,n\,}\biggr)^{x}\\[0.25em]
&\qquad\qquad \biggl(1-\frac{\lambda}{\,n\,}\biggr)^{n-x}\\[0.4em]
&=\frac{\lambda^{x}}{\,x!\,}\times\lim_{n\to\infty}\frac{n!}{\,n^{x}(n-x)!\,}\\[0.25em]
&\qquad\qquad \biggl(1-\frac{\lambda}{\,n\,}\biggr)^{n}\biggl(1-\frac{\lambda}{\,n\,}\biggr)^{-x}\\[0.4em]
&=\frac{\lambda^{x}}{\,x!\,}\times\lim_{n\to\infty}\frac{n\times\cdots\times(n-x+1)}{\,n\times\cdots\times n\,}\\[0.25em]
&\qquad\qquad \biggl(1-\frac{\lambda}{\,n\,}\biggr)^{n}\biggl(1-\frac{\lambda}{\,n\,}\biggr)^{-x}\\[0.4em]
&=\frac{\lambda^{x}}{\,x!\,}\times1\times e^{-\lambda}\times1\\[0.25em]
&=\frac{e^{-\lambda}\lambda^{x}}{\,x!\,},\ x=0,1,\ldots,\infty
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個性質是把卜瓦松過程內的每一個瞬間，都考慮成一個偶發事件的伯努利實驗，只有發生與不發生，且這段時間內期望發生的次數是 $np=\lambda$ 次。

當然，這是一個**以有限的瞬間近似真實的時間區間**的狀況，且我們不可能真的執行無限多次成敗實驗，但這個證明確實讓我們在實務上有一個使用法則是**當 $n$ 很大、$p$ 很小而且 $np$ 為一個定值 $\lambda$ 時**[^rule-of-thumb]可以使用卜瓦松分配來「近似求解」二項分配的機率。

</div>

(3) 由於卜瓦松分配是指在**單位時間**內的偶發事件發生次數，故從卜瓦松過程的角度來說，若令 <span class="text-nowrap">$X\sim\mathrm{Poi}(\lambda)$，</span>則有
{: .topic-paren-item}

$$
X\equiv N(1)
$$

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

所謂的**單位時間**可由使用者自行定義，[^unit-time]例如: 以 $15$ 分鐘為一個單位，則 $15$ 分鐘內的偶發事件發生次數同樣服從卜瓦松分配。

此外，與卜瓦松過程相同，我們也可以將其推廣至任意線段、任意平面、任意空間等等的區間，並且同樣具有**不重疊的單位時間內的卜瓦松分配隨機變數會彼此獨立**的特性。

</div>

(4) 卜瓦松分配具**比例伸縮性質**，若 $X$ 表單位時間內偶發事件發生的次數，且 <span class="text-nowrap">$X\sim\mathrm{Poi}(\lambda)$，</span>則若令 $Y$ 表示 $t$ 時長內偶發事件發生的次數，我們可知
{: .topic-paren-item}

$$
Y\sim\mathrm{Poi}(\lambda t)
$$

[^poisson-name]: 一個有趣的事實是，Poisson 本人其實從未研究過這個過程，他研究的是卜瓦松分配。至於為什麼卜瓦松過程以其姓氏命名，是因為此過程被發現，在特定的條件下，其描述偶發事件個數的變數，將服從卜瓦松分配，因而得名。

[^little-o]: 小 o 符號與大 O 符號是用來描述函數的漸近行為的數學符號，以前述等式為例，即代表當 $t$ 趨近於 $0$ 時，$o(t)$ 趨近於 $0$ 的速度將比 $t$ 本身趨近於 $0$ 的速度來得更快。這樣的漸近符號在描述運算複雜度的時候相當有用，但在本系列中並不會使用到太多這類的漸近符號。

[^rule-of-thumb]: 通常的實務法則是 $n\geqslant100$ 且 <span class="text-nowrap">$np\leqslant10$。</span>

[^unit-time]: 此處所謂的「單位」未必是指我們所認知的單位，只要自行定義清楚，則像是 $2.3$ 分鐘這類的不規則時間長同樣可以被當作單位時間，而 $4.6$ 分鐘便代表兩個單位的時間長。

## 本篇小結

[Definition 4.10](#def-poisson-process) 以五個條件界定卜瓦松過程: 長度為 $0$ 的時間區間內不會有偶發事件、發生機率只與區間長度有關而與起點無關、不重疊區間內的發生次數彼此獨立、極短區間內發生兩次以上的機率趨近於 <span class="text-nowrap">$0$，</span>以及發生一次的機率與區間長度成正比，比例常數 $\lambda$ 即為平均發生率。後兩條在嚴謹的寫法中要用小 o 符號表述，本系列取極限的寫法即可。卜瓦松過程雖然定義在時間區段上，其範圍可以推廣到任意的正實數區間，甚至是任意的有限維度正實數區間，它下轄的分配包含卜瓦松分配、指數分配、伽瑪分配與韋伯分配。

[Theorem 4.9](#thm-maclaurin-series) 給出指數函數的馬克勞林級數，也就是把 $e^{\lambda}$ 寫成 $\sum_{x=0}^{\infty}\frac{\lambda^{x}}{\,x!\,}$ 這個級數；它是泰勒級數在 $0$ 展開的特例，而 [Definition 4.11](#def-poisson-distribution) 之後的推導多次靠它把無窮級數化成一個指數函數。卜瓦松分配記錄的是單位時間內偶發事件的發生次數，值域為 <span class="text-nowrap">$\lbrace\,0,1,2,\ldots,\infty\,\rbrace$，</span>機率函數為 $\frac{e^{-\lambda}\lambda^{x}}{\,x!\,}$ 這個式子，參數只有平均發生率 $\lambda$ 一個。證明依序驗證機率函數的加總為 <span class="text-nowrap">$1$、</span>求得 <span class="text-nowrap">$\mathbb{E}(X)=\lambda$、</span>再以階乘動差 $\mathbb{E}\bigl[X(X-1)\bigr]=\lambda^{2}$ 得到 $\mathbb{E}\bigl(X^{2}\bigr)=\lambda^{2}+\lambda$ 進而算出 $\mathrm{Var}(X)=\lambda$ 這個結果，最後直接由定義求得動差母函數 $M_{\sssig X}(t)=e^{\lambda(e^{t}-1)}$ 這一式。期望值與變異數同為 $\lambda$ 是這個分配最好記的特徵。

定義之後的四點說明，前兩點是延伸性質。可加性只需把兩個 mgf 相乘，指數上的 $\lambda_1$ 與 $\lambda_2$ 因而相加，再由[動差母函數的唯一性](/lecture-notes/uniqueness-of-the-mgf/#thm-mgf-uniqueness)辨識出 <span class="text-nowrap">$\mathrm{Poi}(\lambda_1+\lambda_2)$；</span>它的限制只有 $X$ 與 $Y$ 必須獨立。二項分配的極限則把 $p$ 代換成 $\frac{\lambda}{\,n\,}$ 之後取 $n$ 趨近於無限大，三個因子分別趨近於 <span class="text-nowrap">$1$、</span>$e^{-\lambda}$ 與 <span class="text-nowrap">$1$，</span>剩下的正是卜瓦松分配的機率函數；其直觀是把過程中的每一個瞬間都看成一次伯努利實驗，實務上因而可以在 $n$ 很大、$p$ 很小而 $np$ 為定值時，以卜瓦松機率近似二項機率。後兩點回到卜瓦松過程: 卜瓦松分配的 $X$ 就是過程中的 <span class="text-nowrap">$N(1)$，</span>而所謂的單位時間可由使用者自行定義；由比例伸縮性質，$t$ 個單位時長內的發生次數則服從 $\mathrm{Poi}(\lambda t)$ 這個分配。

下一篇以例題演練卜瓦松分配的計算，並進一步給出兩個結果: 兩個獨立卜瓦松變數相加之後，其中一個在總和給定之下的條件分配為二項分配；以及把卜瓦松過程的偶發事件依固定機率分成兩類之後，兩類的個數各自仍服從卜瓦松分配而且彼此獨立。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
