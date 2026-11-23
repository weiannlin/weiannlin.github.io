---
title: "伽瑪函數與指數分配"
subtitle: "The Gamma Function and the Exponential Distribution"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 4
topic: 10
order: 410
permalink: /lecture-notes/gamma-function-exponential-distribution/
date: 2026-08-12
published: false
excerpt: "本篇先介紹將階乘推廣至正實數的伽瑪函數，再定義卜瓦松過程中首次偶發事件發生前的等待時間分配，即指數分配。文中對照比例參數 $\\beta$ 與頻率參數 $\\lambda$ 兩種寫法，推導動差與動差母函數，並說明與卜瓦松分配的對偶關係。"
---

[上一篇](/lecture-notes/poisson-additivity-and-thinning/)以例題演練卜瓦松分配的計算，並給出兩個結果，其一是兩個獨立的卜瓦松變數相加之後，其中一個在總和給定之下的條件分配為二項分配，其二是把偶發事件依固定機率分成兩類之後，兩類的個數各自仍服從卜瓦松分配，而且彼此獨立。這些結果所記錄的，都是一段時間之內偶發事件發生了幾次。本篇改變記錄的對象。同樣是在[卜瓦松過程](/lecture-notes/poisson-process-and-distribution/#def-poisson-process)之中，這一次要看的是等候直到一次偶發事件發生所需的時間。

推導這個等待時間的期望值與變異數時，所要用到的工具是[伽瑪函數](#def-gamma-function)。本篇因而先由這個函數談起，列出它的四項特性，並給出一個經過代換的變形版本，再進入[指數分配](#def-exponential-distribution)的定義與完整推導。其後說明兩項延伸性質，最後以兩道例題作為演練。

## 伽瑪函數

<div id="def-gamma-function" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 4.12 (伽瑪函數, gamma function)</div>

**伽瑪函數 <span lang="en">(gamma function)</span>** 定義為:

$$
\Gamma(\alpha)\equiv\int_{0}^{\infty}x^{\alpha-1}e^{-x}\,dx,\ \alpha>0
$$

</div>

伽瑪函數具有以下的特性:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\Gamma(n)=(n-1)!,\ \text{其中}\ n\in\mathbb{N}\\[0.7em]
\Gamma(\alpha)=(\alpha-1)\Gamma(\alpha-1),\ \text{其中}\ \alpha>1\\[0.7em]
\Gamma\Bigl(\frac{1}{\,2\,}\Bigr)=\sqrt{\pi}\\[0.7em]
\Gamma(\alpha+n)=\Gamma(\alpha)\times\alpha\times(\alpha+1)\times(\alpha+2)\times\ldots\times(\alpha+n-1),\ \text{其中}\ \alpha>0,\ n\in\mathbb{N}
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\Gamma(n)=(n-1)!,\ \text{其中}\ n\in\mathbb{N}
$$

$$
\Gamma(\alpha)=(\alpha-1)\Gamma(\alpha-1),\ \text{其中}\ \alpha>1
$$

$$
\Gamma\Bigl(\frac{1}{\,2\,}\Bigr)=\sqrt{\pi}
$$

$$
\begin{aligned}
\Gamma(\alpha+n)&=\Gamma(\alpha)\times\alpha\times(\alpha+1)\\[0.3em]
&\qquad\times(\alpha+2)\times\ldots\times(\alpha+n-1),\\[0.3em]
&\qquad \text{其中}\ \alpha>0,\ n\in\mathbb{N}
\end{aligned}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

若令 $y=\beta x\ \Longleftrightarrow\ x=\frac{\,y\,}{\beta}$ 這組關係，則可由代換積分得到

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\int_{0}^{\infty}y^{\alpha-1}e^{-\frac{y}{\beta}}\,dy&=\int_{0}^{\infty}(\beta x)^{\alpha-1}e^{-x}\,d(\beta x)\\[0.45em]
&=\beta^{\alpha}\int_{0}^{\infty}x^{\alpha-1}e^{-x}\,dx=\beta^{\alpha}\Gamma(\alpha),\ \alpha,\beta>0
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\int_{0}^{\infty}y^{\alpha-1}e^{-\frac{y}{\beta}}\,dy&=\int_{0}^{\infty}(\beta x)^{\alpha-1}e^{-x}\,d(\beta x)\\[0.45em]
&=\beta^{\alpha}\int_{0}^{\infty}x^{\alpha-1}e^{-x}\,dx\\[0.45em]
&=\beta^{\alpha}\Gamma(\alpha),\ \alpha,\beta>0
\end{aligned}
$$

</div>

此一變數變換恆等式在後續指數分配 <span lang="en">(exponential distribution)</span> 與伽瑪分配 <span lang="en">(gamma distribution)</span> 的動差推導中經常使用。

</div>

## 指數分配

<div id="def-exponential-distribution" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 4.13 (指數分配, exponential distribution)</div>

**適用範圍**:

令 $X$ 表示卜瓦松過程中，等候直到一次偶發事件發生所需的等待時間。

**值域範圍**:

$$
\mathcal{R}_{\sssig X}=\lbrace\,x\mid x\geqslant0\,\rbrace
$$

**表示式**:

$$
X\sim\mathrm{Exp}(\beta)\quad \text{或}\quad X\sim\mathrm{Exp}(\lambda)
$$

**參數與參數範圍**:

$\beta>0$ 為期望值，而 $\lambda=\frac{1}{\,\beta\,}>0$ 為偶發事件發生的**頻率 (rate)**。

**機率函數**:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X}(x)=\frac{1}{\,\beta\,}e^{-\frac{x}{\beta}},\ x\geqslant0\quad \text{或}\quad f_{\sssig X}(x)=\lambda e^{-\lambda x},\ x\geqslant0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
f_{\sssig X}(x)=\frac{1}{\,\beta\,}e^{-\frac{x}{\beta}},\ x\geqslant0\\[0.45em]
\text{或}\\[0.45em]
f_{\sssig X}(x)=\lambda e^{-\lambda x},\ x\geqslant0
\end{gathered}
$$

</div>

**期望值、變異數、動差母函數**:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\mathbb{E}(X)=\beta=\frac{1}{\,\lambda\,},\quad \mathrm{Var}(X)=\beta^{2}=\frac{1}{\,\lambda^{2}\,}\\[0.7em]
M_{\sssig X}(t)=(1-\beta t)^{-1},\ t<\frac{1}{\,\beta\,}\quad \text{或}\quad M_{\sssig X}(t)=\frac{\lambda}{\,\lambda-t\,},\ t<\lambda
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{E}(X)=\beta=\frac{1}{\,\lambda\,},\\[0.45em]
\mathrm{Var}(X)=\beta^{2}=\frac{1}{\,\lambda^{2}\,}\\[0.45em]
M_{\sssig X}(t)=(1-\beta t)^{-1},\ t<\frac{1}{\,\beta\,}\\[0.45em]
\text{或}\\[0.45em]
M_{\sssig X}(t)=\frac{\lambda}{\,\lambda-t\,},\ t<\lambda
\end{gathered}
$$

</div>

</div>

指數分配有一些地方需要注意:

(1) 以下針對參數為 $\beta$ 的形式，證明指數分配的機率密度函數合法，並推導其期望值、變異數與動差母函數；參數為 $\lambda$ 的表示形式則可同理得證:
{: .topic-paren-item}

<div class="topic-proof" markdown="1">
**Proof.**

先驗證機率函數的積分為 <span class="text-nowrap">$1$，</span>即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\int_{x\in\mathcal{R}_{\sssig X}}f_{\sssig X}(x)\,dx=\int_{0}^{\infty}\frac{1}{\,\beta\,}e^{-\frac{x}{\beta}}\,dx=\Bigl[-e^{-\frac{x}{\beta}}\Bigr]^{\infty}_{0}=0-(-1)=1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\int_{x\in\mathcal{R}_{\sssig X}}f_{\sssig X}(x)\,dx&=\int_{0}^{\infty}\frac{1}{\,\beta\,}e^{-\frac{x}{\beta}}\,dx=\Bigl[-e^{-\frac{x}{\beta}}\Bigr]^{\infty}_{0}\\[0.45em]
&=0-(-1)=1
\end{aligned}
$$

</div>

接著求期望值，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(X)=\int_{x\in\mathcal{R}_{\sssig X}}x\,f_{\sssig X}(x)\,dx=\frac{1}{\,\beta\,}\int_{0}^{\infty}x^{2-1}e^{-\frac{x}{\beta}}\,dx=\frac{1}{\,\beta\,}\times\beta^{2}\Gamma(2)=\beta
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\int_{x\in\mathcal{R}_{\sssig X}}x\,f_{\sssig X}(x)\,dx\\[0.45em]
&=\frac{1}{\,\beta\,}\int_{0}^{\infty}x^{2-1}e^{-\frac{x}{\beta}}\,dx\\[0.45em]
&=\frac{1}{\,\beta\,}\times\beta^{2}\Gamma(2)=\beta
\end{aligned}
$$

</div>

又可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl(X^{2}\bigr)&=\int_{x\in\mathcal{R}_{\sssig X}}x^{2}\,f_{\sssig X}(x)\,dx=\frac{1}{\,\beta\,}\int_{0}^{\infty}x^{3-1}e^{-\frac{x}{\beta}}\,dx\\[0.45em]
&=\frac{1}{\,\beta\,}\times\beta^{3}\Gamma(3)=2\beta^{2}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl(X^{2}\bigr)&=\int_{x\in\mathcal{R}_{\sssig X}}x^{2}\,f_{\sssig X}(x)\,dx\\[0.45em]
&=\frac{1}{\,\beta\,}\int_{0}^{\infty}x^{3-1}e^{-\frac{x}{\beta}}\,dx\\[0.45em]
&=\frac{1}{\,\beta\,}\times\beta^{3}\Gamma(3)=2\beta^{2}
\end{aligned}
$$

</div>

則變異數為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}(X)=\mathbb{E}\bigl(X^{2}\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}=2\beta^{2}-\bigl(\beta\bigr)^{2}=\beta^{2}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(X)&=\mathbb{E}\bigl(X^{2}\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}\\[0.45em]
&=2\beta^{2}-\bigl(\beta\bigr)^{2}=\beta^{2}
\end{aligned}
$$

</div>

最後求動差母函數，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{\sssig X}(t)&=\mathbb{E}\bigl(e^{tX}\bigr)=\int_{0}^{\infty}e^{tx}\frac{1}{\,\beta\,}e^{-\frac{x}{\beta}}\,dx=\int_{0}^{\infty}\frac{1}{\,\beta\,}e^{\bigl(t-\frac{1}{\beta}\bigr)x}\,dx\\[0.45em]
&=\Biggl[\frac{1}{\,\beta\bigl(t-\frac{1}{\beta}\bigr)\,}e^{\bigl(t-\frac{1}{\beta}\bigr)x}\Biggr]^{\infty}_{0}\qquad \Bigl(\text{當}\ t<\frac{1}{\,\beta\,}\ \text{時此積分收斂}\Bigr)\\[0.45em]
&=0-\frac{1}{\,\beta\bigl(t-\frac{1}{\beta}\bigr)\,}=\frac{1}{\,1-\beta t\,},\ t<\frac{1}{\,\beta\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig X}(t)&=\mathbb{E}\bigl(e^{tX}\bigr)=\int_{0}^{\infty}e^{tx}\frac{1}{\,\beta\,}e^{-\frac{x}{\beta}}\,dx\\[0.45em]
&=\int_{0}^{\infty}\frac{1}{\,\beta\,}e^{\bigl(t-\frac{1}{\beta}\bigr)x}\,dx\\[0.45em]
&=\Biggl[\frac{1}{\,\beta\bigl(t-\frac{1}{\beta}\bigr)\,}e^{\bigl(t-\frac{1}{\beta}\bigr)x}\Biggr]^{\infty}_{0}\\[0.25em]
&\qquad \Bigl(\text{當}\ t<\frac{1}{\,\beta\,}\ \text{時此積分收斂}\Bigr)\\[0.45em]
&=0-\frac{1}{\,\beta\bigl(t-\frac{1}{\beta}\bigr)\,}\\[0.45em]
&=\frac{1}{\,1-\beta t\,},\ t<\frac{1}{\,\beta\,}
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

(2) 由指數分配的定義可得以下延伸性質:
{: .topic-paren-item}

第一，當指數分配改以參數 $\lambda$ 表示時，此 $\lambda$ 與[卜瓦松分配](/lecture-notes/poisson-process-and-distribution/#def-poisson-distribution)中的 $\lambda$ 意義完全相同，皆代表卜瓦松過程中偶發事件發生的**頻率**；由此可得指數分配與卜瓦松分配之間的**對偶關係 <span lang="en">(dual relationship)</span>** 如下
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\boxed{\ \text{令 }T\sim\mathrm{Exp}(\lambda)\ \text{且}\ Y\sim\mathrm{Poi}(t\lambda)\ (t>0)\text{，則 }\mathbb{P}(T>t)=\mathbb{P}(Y=0)\ }
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\boxed{
\begin{gathered}
\text{令 }T\sim\mathrm{Exp}(\lambda)\ \text{且}\ Y\sim\mathrm{Poi}(t\lambda)\ (t>0)\text{，}\\[0.45em]
\text{則 }\mathbb{P}(T>t)=\mathbb{P}(Y=0)
\end{gathered}
}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

此對偶關係有直接的事件詮釋。令 $T$ 表示首次偶發事件發生前的等待時間，$Y$ 表示時長 $t$ 內的偶發事件發生次數，則事件 $Y=0$ 代表**在 $t$ 時長內沒有發生任何一次偶發事件**，等價於**直到第一次偶發事件發生所需的時間超過 $t$** (即事件 <span class="text-nowrap">$T>t$</span>)，因此兩個事件的機率相等。

</div>

這個對偶關係能讓我們證明以下的命題:
{: .topic-paren-cont}

**令單位時間內的偶發事件發生次數服從參數為 $\lambda$ 的卜瓦松分配，則其中直到一次偶發事件發生所需之等待時間，服從參數為 $\lambda$ 的指數分配。**
{: .topic-paren-cont}

<div class="topic-proof" markdown="1">
**Proof.**

由上述的對偶關係可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
F_{\sssig T}(t)&=\mathbb{P}(T\leqslant t)=1-\mathbb{P}(T>t)=1-\mathbb{P}(Y=0)\\[0.45em]
&=1-\frac{e^{-\lambda t}(\lambda t)^{0}}{\,0!\,}=1-e^{-\lambda t},\ t>0
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig T}(t)&=\mathbb{P}(T\leqslant t)=1-\mathbb{P}(T>t)\\[0.45em]
&=1-\mathbb{P}(Y=0)=1-\frac{e^{-\lambda t}(\lambda t)^{0}}{\,0!\,}\\[0.45em]
&=1-e^{-\lambda t},\ t>0
\end{aligned}
$$

</div>

由此可得

$$
f_{\sssig T}(t)=\frac{d\,F_{\sssig T}(t)}{d\,t}=\lambda e^{-\lambda t},\ t>0
$$

此即

$$
T\sim\mathrm{Exp}(\lambda)
$$

原式得證。 <span class="topic-qed">$\square$</span>
</div>

第二，令 $X\sim\mathrm{Exp}(\beta)$ 且令 <span class="text-nowrap">$Y=aX,\ a>0$，</span>則
{: .topic-paren-cont}

$$
Y\sim\mathrm{Exp}(a\beta)
$$

<div class="topic-proof" markdown="1">
**Proof.**

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
M_{\sssig Y}(t)=\mathbb{E}\bigl(e^{tY}\bigr)=\mathbb{E}\bigl(e^{taX}\bigr)=M_{\sssig X}(at)=(1-a\beta t)^{-1},\ t<\frac{1}{\,a\beta\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig Y}(t)&=\mathbb{E}\bigl(e^{tY}\bigr)=\mathbb{E}\bigl(e^{taX}\bigr)\\[0.45em]
&=M_{\sssig X}(at)\\[0.45em]
&=(1-a\beta t)^{-1},\ t<\frac{1}{\,a\beta\,}
\end{aligned}
$$

</div>

則由[動差母函數的唯一性](/lecture-notes/uniqueness-of-the-mgf/#thm-mgf-uniqueness)可知

$$
Y\sim\mathrm{Exp}(a\beta)
$$

原式得證。 <span class="topic-qed">$\square$</span>
</div>

此性質稱為指數分配的**比例伸縮性質**，參數 $\beta$ 亦因此稱為比例參數，與後文[伽瑪分配](/lecture-notes/gamma-distribution/#def-gamma-distribution)中的比例參數 $\beta$ 相對應。
{: .topic-paren-cont}

(3) 由於 $\beta=\frac{1}{\,\lambda\,}$ 為一對一的倒數關係，$\beta$ 與 $\lambda$ 只要給定其一，另一個隨即確定；兩者僅是同一個參數的不同詮釋角度，不應視為兩個相異的參數。
{: .topic-paren-item}

## 指數分配的例題

<div id="ex-exponential-1" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.26</div>

<div lang="en" markdown="1">
Businesspeople are interrupted at an average rate of $10$ times per hour. Assuming that the number of interruptions follows a Poisson distribution, what is the probability that more than $6$ minutes elapse between two consecutive interruptions?
</div>

**[ 法一 ]**

由題意可知每小時被打斷的次數服從 $\mathrm{Poi}(\lambda=10)$ 的分配。

若令 $T$ 表示兩次相鄰的打斷事件間之間隔時間，單位為小時，則

$$
T\sim\mathrm{Exp}(\lambda=10)
$$

又 $6$ 分鐘代表 $\frac{1}{\,10\,}$ 小時，故所求為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}\Bigl(T\geqslant\frac{1}{\,10\,}\Bigr)=\int_{\frac{1}{10}}^{\infty}10e^{-10t}\,dt=e^{-10\cdot\frac{1}{10}}=e^{-1}\fallingdotseq0.3679
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}\Bigl(T\geqslant\frac{1}{\,10\,}\Bigr)&=\int_{\frac{1}{10}}^{\infty}10e^{-10t}\,dt\\[0.45em]
&=e^{-10\cdot\frac{1}{10}}=e^{-1}\fallingdotseq0.3679
\end{aligned}
$$

</div>

**[ 法二 ]**

令 $Y$ 表示六分鐘內打斷事件的發生次數，則我們有

$$
Y\sim\mathrm{Poi}\Bigl(\lambda=\frac{10}{\,60\,}\times6=1\Bigr)
$$

所求為

$$
\mathbb{P}(Y=0)=\frac{e^{-1}1^{0}}{\,0!\,}=e^{-1}\fallingdotseq0.3679
$$

</div>

<div id="ex-exponential-2" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.27</div>

<div lang="en" markdown="1">
Consumers arrive at a convenience store at random at a rate of $120$ people per hour.

<ol class="topic-list-paren">
  <li>Find the probability that during any $3$-minute period, the number of consumers arriving at the convenience store is exactly <span class="text-nowrap">$2$.</span></li>
  <li>A consumer arrives at 10:00 am. Find the probability that the next consumer arrives before 10:02 am.</li>
</ol>
</div>

(1) 令 $X$ 表示 $3$ 分鐘之內抵達商店的人數，假設 $X$ 服從卜瓦松分配，則
{: .topic-paren-item}

$$
X\sim\mathrm{Poi}\Bigl(\lambda=\frac{120}{\,60\,}\times3=6\Bigr)
$$

所求為
{: .topic-paren-cont}

$$
\mathbb{P}(X=2)=\frac{e^{-6}6^{2}}{\,2!\,}\fallingdotseq0.04462
$$

(2) 承上題假設，若令 $Y$ 表示直到下一位顧客抵達所需的等候時間，單位為分鐘，則
{: .topic-paren-item}

$$
Y\sim\mathrm{Exp}(\lambda=2)
$$

所求為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(Y<2)=\int_{0}^{2}2e^{-2y}\,dy=1-e^{-4}\fallingdotseq0.9817
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(Y<2)&=\int_{0}^{2}2e^{-2y}\,dy\\[0.45em]
&=1-e^{-4}\fallingdotseq0.9817
\end{aligned}
$$

</div>

</div>

## 本篇小結

[Definition 4.12](#def-gamma-function) 的伽瑪函數由 $\int_{0}^{\infty}x^{\alpha-1}e^{-x}\,dx$ 這個積分界定，參數 $\alpha$ 只要求為正數。它的四項特性之中，$\Gamma(n)=(n-1)!$ 說明它在正整數上就是階乘，$\Gamma(\alpha)=(\alpha-1)\Gamma(\alpha-1)$ 是自變數每次減 $1$ 的遞迴關係，$\Gamma\bigl(\frac{1}{\,2\,}\bigr)=\sqrt{\pi}$ 給出半整數處的值，最後一項則是遞迴關係連用 $n$ 次的結果。緊接著的 Note 把被積函數的指數改成 $-\frac{y}{\beta}$ 這個形式，經代換積分之後得到 $\beta^{\alpha}\Gamma(\alpha)$ 這個值，本篇推導期望值與二階動差時用的正是這個變形。

[Definition 4.13](#def-exponential-distribution) 的指數分配記錄的是卜瓦松過程中，等候直到一次偶發事件發生所需的等待時間，值域為非負實數集合 <span class="text-nowrap">$[0,\infty)$</span> (即 $\lbrace\,x\mid x\geqslant0\,\rbrace$)，機率函數可以寫成 $\frac{1}{\,\beta\,}e^{-\frac{x}{\beta}}$ 或 $\lambda e^{-\lambda x}$ 兩種形式。證明依序驗證機率函數的積分為 <span class="text-nowrap">$1$、</span>求得 <span class="text-nowrap">$\mathbb{E}(X)=\beta$、</span>再由 $\mathbb{E}\bigl(X^{2}\bigr)=2\beta^{2}$ 算出 <span class="text-nowrap">$\mathrm{Var}(X)=\beta^{2}$，</span>最後直接由定義求得 $M_{\sssig X}(t)=(1-\beta t)^{-1}$ 這一式。其中期望值與二階動差都是把 $x^{2-1}$ 與 $x^{3-1}$ 湊成伽瑪函數變形的形式，再分別以 $\Gamma(2)$ 與 $\Gamma(3)$ 求得；動差母函數則要求 $t<\frac{1}{\,\beta\,}$ 才會收斂。

定義之後的三點說明，第一點是上述的完整推導，第二點給出兩項延伸性質。以 $\lambda$ 表示參數時，它與卜瓦松分配的 $\lambda$ 是同一個量，都是偶發事件的發生頻率，因而有 $\mathbb{P}(T>t)=\mathbb{P}(Y=0)$ 這條對偶關係。等待時間超過 $t$ 與 $t$ 時長內一次都沒有發生，講的是同一件事情。由這條關係算出 $F_{\sssig T}(t)=1-e^{-\lambda t}$ 之後再微分，即證得單位時間內的次數服從卜瓦松分配時，等待時間服從指數分配。比例伸縮性質則只需把 $M_{\sssig X}(t)$ 的引數換成 <span class="text-nowrap">$at$，</span>$\beta$ 隨之變為 <span class="text-nowrap">$a\beta$，</span>$\beta$ 因此被稱作比例參數。第三點提醒 $\beta$ 與 $\lambda$ 只是同一個參數的兩種詮釋，決定其一另一個即隨之決定。

兩道例題示範的正是同一個問題的兩個角度。[Example 4.26](#ex-exponential-1) 的法一以指數分配算間隔時間超過 $\frac{1}{\,10\,}$ 小時的機率，法二以卜瓦松分配算六分鐘內一次都沒有發生的機率，兩者都得到 <span class="text-nowrap">$e^{-1}$，</span>這正是對偶關係的具體演練。[Example 4.27](#ex-exponential-2) 則把兩個角度分成兩小題。第一小題求 $3$ 分鐘內恰有 $2$ 人抵達的機率，用的是 $\mathrm{Poi}(6)$ 分配；第二小題求下一位顧客在 $2$ 分鐘內抵達的機率，用的是 $\mathrm{Exp}(\lambda=2)$ 分配。兩小題的參數換算都以「每分鐘 $2$ 人」為準。

[下一篇](/lecture-notes/exponential-memoryless-and-minima/)證明指數分配的無記憶性，說明它是連續型分配之中唯一具有這個性質的分配，並給出兩個獨立指數變數取極小值與比較先後次序的結果。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
