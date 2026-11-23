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
published: true
excerpt: "卜瓦松過程以獨立增量與極短區間內單次發生等五項條件刻畫偶發事件，單位時間內的發生次數即服從卜瓦松分配。本篇推導其期望值與變異數皆為 $\\lambda$ 的性質、動差母函數與可加性，並證明二項分配在 $n\\to\\infty$ 與 $p\\to 0$ 且 $np=\\lambda$ 固定下收斂至卜瓦松分配。"
---

[上一篇](/lecture-notes/hypergeometric-distribution/)介紹[超幾何分配](/lecture-notes/hypergeometric-distribution/#def-hypergeometric)，至此伯努利實驗相關的機率模型已經全部給出。這一類模型所記錄的，都是在指定次數的實驗之中成功發生了幾次，或者為了取得指定次數的成功而必須做幾次實驗。本篇轉入第二大類的機率模型，也就是由卜瓦松過程所衍生的各個分配。

卜瓦松過程描述的是偶發事件在一段時間之內的發生行為，它所關心的量是一段長度為 $t$ 的時間之內，偶發事件的發生次數。本篇先給出卜瓦松過程的定義，列出它下轄的四個分配，再進入其中最基本的卜瓦松分配；由於驗證卜瓦松分配的機率函數合法時要用到指數函數的馬克勞林級數，因此這個級數會排在分配定義之前給出。

## 卜瓦松過程

<div id="def-poisson-process" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 4.10 (卜瓦松過程, Poisson process)</div>

**卜瓦松過程 <span lang="en">(Poisson process)</span>** 是一種用來描述**偶發事件 (rare event)** 之行為的過程，若定義 $N(t)$ 表示在時間區間 $(0,t]$ 內偶發事件的累積發生個數 (對 <span class="text-nowrap">$t\geqslant0$</span>)，則其應滿足以下條件:

(1) 在時間起點 $0$ 時，尚未發生任何偶發事件，此即
{: .topic-paren-item}

$$
N(0)=0
$$

(2) 偶發事件在任一時間區間內發生的機率與該區間的起點無關，而只與該區間的長度有關，此即
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\text{若}\ 0\leqslant t_1<t_2,\ 0\leqslant t_3<t_4\ \text{且}\ t_2-t_1=t_4-t_3\\[0.45em]
\text{則}\ \mathbb{P}\bigl(N(t_2)-N(t_1)=m\bigr)=\mathbb{P}\bigl(N(t_4)-N(t_3)=m\bigr),\ m=0,1,2,\ldots
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\text{若}\ 0\leqslant t_1<t_2,\ 0\leqslant t_3<t_4\\[0.3em]
\text{且}\ t_2-t_1=t_4-t_3
\end{gathered}
$$

<div class="topic-math-follow" markdown="1">

$$
\begin{aligned}
\text{則}\ \mathbb{P}\bigl(&N(t_2)-N(t_1)=m\bigr)\\[0.3em]
&=\mathbb{P}\bigl(N(t_4)-N(t_3)=m\bigr),\\[0.3em]
&\qquad m=0,1,2,\ldots
\end{aligned}
$$

</div>

</div>

(3) 不重疊的時間區間內，偶發事件的發生次數彼此獨立，此即
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\text{若}\ 0\leqslant t_1<t_2\leqslant t_3<t_4\text{，則}\ \bigl[N(t_2)-N(t_1)\bigr]\indep\bigl[N(t_4)-N(t_3)\bigr]
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\text{若}\ 0\leqslant t_1<t_2\leqslant t_3<t_4\text{，}\\[0.3em]
\text{則}\ \bigl[N(t_2)-N(t_1)\bigr]\indep\bigl[N(t_4)-N(t_3)\bigr]
\end{gathered}
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

卜瓦松過程以法國數學家 Siméon Denis Poisson (1781-1840) 的姓氏命名。Poisson 本人當年研究的其實是卜瓦松分配而非此隨機過程；後人發現滿足上述條件的計數過程，其區間發生次數恰服從卜瓦松分配，遂以同一姓氏稱之。

卜瓦松過程有一些地方需要注意:

(1) 偶發事件是指發生機率極低的事件；在卜瓦松過程中，此類事件**在同一個瞬間幾乎不會發生兩次以上**，這也就是上述條件 (4) 所刻畫的情形。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

在嚴謹的隨機過程定義中，條件 (4) 會寫為 <span class="text-nowrap">$\mathbb{P}\bigl(N(t)\geqslant2\bigr)=o(t)$，</span>其中 $o(\cdot)$ 為小 o 符號 <span lang="en">(little o notation)</span>。小 o 與大 O 符號皆用於刻畫函數的漸近行為；此處 $o(t)$ 代表當 $t\to0$ 時，該項趨近於 $0$ 的速度快於 $t$ 本身 (即 <span class="text-nowrap">$\lim_{t\to0}o(t)/t=0$</span>)。本系列不深入使用這類漸近符號，初學階段先由極限式 $\lim_{t\to0}\mathbb{P}\bigl(N(t)\geqslant2\bigr)=0$ 掌握其涵義即可。

</div>

(2) 卜瓦松過程雖以時間區段定義，其定義範圍亦可推廣至任意**正實數區間**或**有限維度正實數區間**，例如線段、平面或立體空間中的區域，因此在實務應用上相當靈活。
{: .topic-paren-item}

(3) 上述條件 (5) 中，$\lambda$ 為卜瓦松過程的參數，代表**平均發生率 <span lang="en">(mean occurrence rate)</span>**；該條件嚴謹的漸近寫法為 $\mathbb{P}\bigl(N(t)=1\bigr)=\lambda t+o(t)$ (<span class="text-nowrap">$\lambda>0$</span>)，本系列簡記為極短區間下的線性關係 <span class="text-nowrap">$\mathbb{P}\bigl(N(t)=1\bigr)=\lambda t$。</span>
{: .topic-paren-item}

卜瓦松過程下轄許多重要的分配，包含:

<ol class="topic-list-paren">
  <li>卜瓦松分配 <span lang="en">(Poisson distribution)</span></li>
  <li>指數分配 <span lang="en">(exponential distribution)</span></li>
  <li>伽瑪分配 <span lang="en">(gamma distribution)</span></li>
  <li>韋伯分配 <span lang="en">(Weibull distribution)</span></li>
</ol>

這些分配關係密切，以下依序介紹各分配及其間的關聯。

## 馬克勞林級數

<div id="thm-maclaurin-series" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 4.9 (馬克勞林級數, Maclaurin series)</div>

針對**指數函數 <span lang="en">(exponential function)</span>** 的**馬克勞林級數 <span lang="en">(Maclaurin series)</span>** 可表示為下列的無窮級數:

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

馬克勞林級數是泰勒級數 (Taylor’s series) 的一個特例，專指將函數在 $0$ 展開的泰勒級數。此處的馬克勞林級數便是針對指數函數的馬克勞林級數。

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

$\lambda>0$ 表示單位時間內，偶發事件的平均發生率，也表示單位時間內偶發事件的期望發生次數。

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
\begin{gathered}
\mathbb{E}(X)=\lambda,\\[0.45em]
\mathrm{Var}(X)=\lambda\\[0.45em]
M_{\sssig X}(t)=e^{\lambda(e^{t}-1)},\ t\in\mathbb{R}
\end{gathered}
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

(2) 由**卜瓦松分配**的定義可得以下延伸性質:
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
\begin{gathered}
X\sim\mathrm{Bin}(n,\ p)\\[0.25em]
\xrightarrow[n\to\infty,\ p\to0,\ np=\lambda]{\ \mathrm{d}\ }\\[0.25em]
W\sim\mathrm{Poi}(\lambda)
\end{gathered}
}
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.**

令 <span class="text-nowrap">$X\sim\mathrm{Bin}(n,\ p)$，</span>若 $n\to\infty,\ p\to0$ 且 <span class="text-nowrap">$np=\lambda$，</span>則有

$$
p=\frac{\lambda}{\,n\,}
$$

則由二項分配的 pmf，我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\lim_{n\to\infty}p_{\sssig X}(x)&=\lim_{n\to\infty}\binom{n}{x}p^{x}(1-p)^{n-x}\\[0.45em]
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
\lim_{n\to\infty}p_{\sssig X}(x)&=\lim_{n\to\infty}\binom{n}{x}p^{x}(1-p)^{n-x}\\[0.4em]
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

此極限性質可直觀理解為將單位時間細分為極多個微小區間，把每個微小區間視為一次僅有「發生」或「不發生」的伯努利實驗，並維持期望發生次數為定值 <span class="text-nowrap">$np=\lambda$。</span>在實務計算二項分配機率時，**當 $n$ 很大、$p$ 很小且乘積 $np=\lambda$ 固定** (常見經驗法則為 $n\geqslant100$ 且 <span class="text-nowrap">$np\leqslant10$</span>)，即可用卜瓦松分配 $\mathrm{Poi}(\lambda)$ 近似求解二項分配 $\mathrm{Bin}(n,\ p)$ 所對應的機率。

</div>

(3) 由於卜瓦松分配記錄**單位時間**內的偶發事件發生次數，從卜瓦松過程的角度來看，若 <span class="text-nowrap">$X\sim\mathrm{Poi}(\lambda)$，</span>則有
{: .topic-paren-item}

$$
X\equiv N(1)
$$

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

此處的**單位時間**可依問題需求自行設定，無須受限於標準時間單位；例如可將 $15$ 分鐘定為一個單位，甚至以 $2.3$ 分鐘等不規則時長作為單一單位 (此時 $4.6$ 分鐘即對應兩個單位)。此外，承接卜瓦松過程的推廣，卜瓦松分配亦可定義於線段、平面或立體空間等非時間區段上，且同樣具備**不重疊區段內的卜瓦松隨機變數彼此獨立**的性質。

</div>

(4) 卜瓦松分配具**比例伸縮性質**，若 $X$ 表單位時間內偶發事件發生的次數，且 <span class="text-nowrap">$X\sim\mathrm{Poi}(\lambda)$，</span>則若令 $Y$ 表示 $t$ 時長內偶發事件發生的次數，我們可知
{: .topic-paren-item}

$$
Y\sim\mathrm{Poi}(\lambda t)
$$

## 本篇小結

[Definition 4.10](#def-poisson-process) 以五個條件界定卜瓦松過程，分別是時間起點 $0$ 時累積次數為 <span class="text-nowrap">$0$、</span>發生機率只與區間長度有關而與起點無關、不重疊區間內的發生次數彼此獨立、極短區間內發生兩次以上的機率趨近於 <span class="text-nowrap">$0$，</span>以及發生一次的機率與區間長度成正比，比例常數 $\lambda$ 即為平均發生率。後兩條在嚴謹的寫法中要用小 o 符號表述，本系列取極限的寫法即可。卜瓦松過程雖然定義在時間區段上，其範圍可以推廣到任意的正實數區間，甚至是任意的有限維度正實數區間，它下轄的分配包含卜瓦松分配、指數分配、伽瑪分配與韋伯分配。

[Theorem 4.9](#thm-maclaurin-series) 給出指數函數的馬克勞林級數，也就是把 $e^{\lambda}$ 寫成 $\sum_{x=0}^{\infty}\frac{\lambda^{x}}{\,x!\,}$ 這個級數；它是泰勒級數在 $0$ 展開的特例，而 [Definition 4.11](#def-poisson-distribution) 之後的推導多次靠它把無窮級數化成一個指數函數。卜瓦松分配記錄的是單位時間內偶發事件的發生次數，值域為全體非負整數 $\lbrace\,0,1,2,\ldots,\infty\,\rbrace$ 這一集合，機率函數為 $\frac{e^{-\lambda}\lambda^{x}}{\,x!\,}$ 這個式子，參數只有平均發生率 $\lambda$ 一個。證明依序驗證機率函數的加總為 <span class="text-nowrap">$1$、</span>求得 <span class="text-nowrap">$\mathbb{E}(X)=\lambda$、</span>再以階乘動差 $\mathbb{E}\bigl[X(X-1)\bigr]=\lambda^{2}$ 得到 $\mathbb{E}\bigl(X^{2}\bigr)=\lambda^{2}+\lambda$ 進而算出 $\mathrm{Var}(X)=\lambda$ 這個結果，最後直接由定義求得動差母函數 $M_{\sssig X}(t)=e^{\lambda(e^{t}-1)}$ 這一式。期望值與變異數同為 $\lambda$ 是這個分配最好記的特徵。

定義之後的四點說明，前兩點是延伸性質。可加性只需把兩個 mgf 相乘，指數上的 $\lambda_1$ 與 $\lambda_2$ 因而相加，再由動差母函數的唯一性辨識出參數相加的 <span class="text-nowrap">$\mathrm{Poi}(\lambda_1+\lambda_2)$；</span>它的限制只有 $X$ 與 $Y$ 必須獨立。二項分配的極限則把 $p$ 代換成 $\frac{\lambda}{\,n\,}$ 之後取 $n$ 趨近於無限大，三個因子分別趨近於 <span class="text-nowrap">$1$、</span>$e^{-\lambda}$ 與 <span class="text-nowrap">$1$，</span>剩下的正是卜瓦松分配的機率函數；其直觀是把過程中的每一個瞬間都看成一次伯努利實驗，實務上因而可以在 $n$ 很大、$p$ 很小而 $np$ 為定值時，以卜瓦松機率近似二項機率。後兩點回到卜瓦松過程。卜瓦松分配的 $X$ 就是過程中的 <span class="text-nowrap">$N(1)$，</span>而所謂的單位時間可由使用者自行定義；由比例伸縮性質，$t$ 個單位時長內的發生次數則服從 $\mathrm{Poi}(\lambda t)$ 這個分配。

[下一篇](/lecture-notes/poisson-additivity-and-thinning/)以例題演練卜瓦松分配的計算，並進一步給出兩個結果，其一是兩個獨立卜瓦松變數相加之後，其中一個在總和給定之下的條件分配為二項分配，其二是把卜瓦松過程的偶發事件依固定機率分成兩類之後，兩類的個數各自仍服從卜瓦松分配而且彼此獨立。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
