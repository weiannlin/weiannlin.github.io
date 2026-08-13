---
title: "伽瑪函數與指數分配"
subtitle: "The Gamma Function and the Exponential Distribution"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 4
topic: 10
order: 410
permalink: /teaching-topics/ch4-p10-candidate/
date: 2026-08-12
published: false
excerpt: "伽瑪函數以 $\\int_{0}^{\\infty}x^{\\alpha-1}e^{-x}\\,dx$ 這個積分定義，把階乘推廣到正實數上，它的一個代換變形會在指數分配與伽瑪分配的推導中反覆出現。指數分配記錄的是卜瓦松過程中，等候直到一次偶發事件發生所需的等待時間，機率函數可以寫成 $\\frac{1}{\\beta}e^{-x/\\beta}$ 或 $\\lambda e^{-\\lambda x}$ 兩種形式，期望值為 $\\beta$、變異數為 $\\beta^{2}$，動差母函數則是 $(1-\\beta t)^{-1}$。本篇先給出伽瑪函數與它的四項特性，再給出指數分配的定義與完整推導，並說明指數分配與卜瓦松分配之間的對偶關係，以及乘上一個正數之後仍為指數分配的比例伸縮性質。最後以兩道例題示範同一個問題如何分別由等待時間與發生次數兩個角度求解。"
---

[上一篇](/teaching-topics/ch4-p09-candidate/)以例題演練卜瓦松分配的計算，並給出兩個結果: 兩個獨立的卜瓦松變數相加之後，其中一個在總和給定之下的條件分配為二項分配；以及把偶發事件依固定機率分成兩類之後，兩類的個數各自仍服從卜瓦松分配，而且彼此獨立。這些結果所記錄的，都是一段時間之內偶發事件發生了幾次。本篇改變記錄的對象: 同樣是在[卜瓦松過程](/teaching-topics/ch4-p08-candidate/#def-poisson-process)之中，這一次要看的是等候直到一次偶發事件發生所需的時間。

推導這個等待時間的期望值與變異數時，所要用到的工具是[伽瑪函數](#def-gamma-function)。本篇因而先由這個函數談起，列出它的四項特性，並給出一個經過代換的變形版本，再進入[指數分配](#def-exponential-distribution)的定義與完整推導。其後說明兩項延伸性質，最後以兩道例題作為演練。

## 伽瑪函數

<div id="def-gamma-function" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 4.12 (伽瑪函數, gamma function)</div>

**伽瑪函數 <span lang="en">(gamma function)</span>** 是下列的函數:

$$
\Gamma(\alpha)\equiv\int_{0}^{\infty}x^{\alpha-1}e^{-x}\,dx,\ \alpha>0
$$

</div>

伽瑪函數具有以下的特性:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\Gamma(n)=(n-1)!,\ \text{其中}\ n\in\mathbb{N}\\[0.7em]
\Gamma(\alpha)=(\alpha-1)\Gamma(\alpha-1)\\[0.7em]
\Gamma\Bigl(\frac{1}{\,2\,}\Bigr)=\sqrt{\pi}\\[0.7em]
\Gamma(\alpha+n)=\Gamma(\alpha)\times\alpha\times(\alpha+1)\times(\alpha+2)\times\ldots\times(\alpha+n-1)
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\Gamma(n)=(n-1)!,\ \text{其中}\ n\in\mathbb{N}
$$

$$
\Gamma(\alpha)=(\alpha-1)\Gamma(\alpha-1)
$$

$$
\Gamma\Bigl(\frac{1}{\,2\,}\Bigr)=\sqrt{\pi}
$$

$$
\begin{gathered}
\Gamma(\alpha+n)=\Gamma(\alpha)\times\alpha\times(\alpha+1)\\[0.3em]
\times(\alpha+2)\times\ldots\times(\alpha+n-1)
\end{gathered}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

若令 <span class="text-nowrap">$y=\beta x\ \Longleftrightarrow\ x=\frac{\,y\,}{\beta}$，</span>則可由代換積分得到

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
&\int_{0}^{\infty}y^{\alpha-1}e^{-\frac{y}{\beta}}\,dy\\[0.45em]
&\quad =\int_{0}^{\infty}(\beta x)^{\alpha-1}e^{-x}\,d(\beta x)\\[0.45em]
&\quad =\beta^{\alpha}\int_{0}^{\infty}x^{\alpha-1}e^{-x}\,dx\\[0.45em]
&\quad =\beta^{\alpha}\Gamma(\alpha),\ \alpha,\beta>0
\end{aligned}
$$

</div>

這個變形的版本將在指數分配 <span lang="en">(exponential distribution)</span> 與伽瑪分配 <span lang="en">(gamma distribution)</span> 的證明中發揮很大的用途。

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
\mathbb{E}(X)=\beta=\frac{1}{\,\lambda\,}\\[0.45em]
\mathrm{Var}(X)=\beta^{2}=\frac{1}{\,\lambda^{2}\,}\\[0.45em]
M_{\sssig X}(t)=(1-\beta t)^{-1},\ t<\frac{1}{\,\beta\,}\\[0.45em]
\text{或}\\[0.45em]
M_{\sssig X}(t)=\frac{\lambda}{\,\lambda-t\,},\ t<\lambda
\end{gathered}
$$

</div>

</div>

指數分配有一些地方需要注意:

(1) 我們僅證明參數為 $\beta$ 時的狀況如下，指數分配的機率函數為合法的機率函數與期望值、變異數；參數為 $\lambda$ 的情況則同理可證。
{: .topic-paren-item}

<div class="topic-proof" markdown="1">
**Proof.** 先驗證機率函數的積分為 <span class="text-nowrap">$1$，</span>即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\int_{x\in\mathcal{R}_{\sssig X}}f_{\sssig X}(x)\,dx=\int_{0}^{\infty}\frac{1}{\,\beta\,}e^{-\frac{x}{\beta}}\,dx=\Bigl[-e^{-\frac{x}{\beta}}\Bigr]^{\infty}_{0}=0-(-1)=1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\int_{x\in\mathcal{R}_{\sssig X}}f_{\sssig X}(x)\,dx\\[0.45em]
&\quad =\int_{0}^{\infty}\frac{1}{\,\beta\,}e^{-\frac{x}{\beta}}\,dx=\Bigl[-e^{-\frac{x}{\beta}}\Bigr]^{\infty}_{0}\\[0.45em]
&\quad =0-(-1)=1
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

(2) 由指數分配的定義可以得到以下幾個延伸性質:
{: .topic-paren-item}

第一，指數分配的參數以 $\lambda$ 表示的時候，這個參數的意義，與[卜瓦松分配](/teaching-topics/ch4-p08-candidate/#def-poisson-distribution)的 $\lambda$ 是完全相同的，都代表卜瓦松過程中，偶發事件發生的**頻率**，這導致了指數分配與卜瓦松分配間的**對偶關係 <span lang="en">(dual relationship)</span>**，即
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\text{令 }T\sim\mathrm{Exp}(\lambda)\ \text{且}\ Y\sim\mathrm{Poi}(t\lambda)\text{，則 }\mathbb{P}(T>t)=\mathbb{P}(Y=0)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\text{令 }T\sim\mathrm{Exp}(\lambda)\ \text{且}\ Y\sim\mathrm{Poi}(t\lambda)\\[0.45em]
\text{則 }\mathbb{P}(T>t)=\mathbb{P}(Y=0)
\end{gathered}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個對偶關係的直覺是，我們令了 $T$ 表示直到一次偶發事件發生所需的等待時間，並且我們又令了 $Y$ 代表 $t$ 時長內偶發事件發生的次數，則在此敘述下，$Y=0$ 即代表**在 $t$ 時長內沒有發生任何一次偶發事件**，換句話說，**直到第一次偶發事件發生所需的時間比 $t$ 還要長**，此即 $T>t$ 的事件，因此有此對偶關係。

</div>

這個對偶關係能讓我們證明以下的命題:
{: .topic-paren-cont}

**令單位時間內的偶發事件發生次數服從參數為 $\lambda$ 的卜瓦松分配，則其中直到一次偶發事件發生所需之等待時間，服從參數為 $\lambda$ 的指數分配。**
{: .topic-paren-cont}

<div class="topic-proof" markdown="1">
**Proof.** 由上述的對偶關係可知

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

則由[動差母函數的唯一性](/teaching-topics/uniqueness-of-the-mgf/#thm-mgf-uniqueness)可知

$$
Y\sim\mathrm{Exp}(a\beta)
$$

原式得證。 <span class="topic-qed">$\square$</span>
</div>

這個性質被稱作指數分配的**比例伸縮性質**，並且 $\beta$ 由此被稱作比例參數。[^scale]
{: .topic-paren-cont}

[^scale]: 這個稱呼乃是對應於[伽瑪分配](/teaching-topics/ch4-p12-candidate/#def-gamma-distribution)中的 <span class="text-nowrap">$\beta$，</span>我們將在下一小節看見伽瑪分配與指數分配的高度關聯性。

(3) 讀者應特別注意的是，$\beta=\frac{1}{\,\lambda\,}$ 是一個固定的關係，換言之，$\beta$ 與 $\lambda$ 只要其中一個被決定，另一個也會隨之決定，這只是同一個參數的不同詮釋角度，而不應視為兩個相異的參數。
{: .topic-paren-item}

## 指數分配的例題

<div id="ex-exponential-1" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.26</div>

<div lang="en" markdown="1">
Suppose that businesspeople are interrupted at an average rate of $10$ times per hour, and that the number of interruptions follows a Poisson distribution. What is the probability that more than $6$ minutes elapse between two consecutive interruptions?
</div>

**[ 法一 ]**

由題意可知每小時被打斷的次數服從 $\mathrm{Poi}(\lambda=10)$ 的分配

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

令 $Y$ 表示六分鐘內打斷事件的發生次數，則

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
Suppose that consumers arrive at random at a convenience store at an average rate of $120$ people per hour.

<ol class="topic-list-paren">
  <li>Determine the probability that exactly $2$ consumers arrive during a given $3$-minute period.</li>
  <li>Suppose that a consumer arrives at 10:00 am. What is the probability that the next consumer arrives before 10:02 am?</li>
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

(2) 承上題假設，若令 $Y$ 直到下一位顧客抵達所需的等候時間，單位為分鐘，則
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

[Definition 4.13](#def-exponential-distribution) 的指數分配記錄的是卜瓦松過程中，等候直到一次偶發事件發生所需的等待時間，值域為 <span class="text-nowrap">$\lbrace\,x\mid x\geqslant0\,\rbrace$，</span>機率函數可以寫成 $\frac{1}{\,\beta\,}e^{-\frac{x}{\beta}}$ 或 $\lambda e^{-\lambda x}$ 兩種形式。證明依序驗證機率函數的積分為 <span class="text-nowrap">$1$、</span>求得 <span class="text-nowrap">$\mathbb{E}(X)=\beta$、</span>再由 $\mathbb{E}\bigl(X^{2}\bigr)=2\beta^{2}$ 算出 <span class="text-nowrap">$\mathrm{Var}(X)=\beta^{2}$，</span>最後直接由定義求得 $M_{\sssig X}(t)=(1-\beta t)^{-1}$ 這一式。其中期望值與二階動差都是把 $x^{2-1}$ 與 $x^{3-1}$ 湊成伽瑪函數變形的形式，再分別以 $\Gamma(2)$ 與 $\Gamma(3)$ 求得；動差母函數則要求 $t<\frac{1}{\,\beta\,}$ 才會收斂。

定義之後的三點說明，第一點是上述的完整推導，第二點給出兩項延伸性質。以 $\lambda$ 表示參數時，它與卜瓦松分配的 $\lambda$ 是同一個量，都是偶發事件的發生頻率，因而有 $\mathbb{P}(T>t)=\mathbb{P}(Y=0)$ 這條對偶關係: 等待時間超過 $t$ 與 $t$ 時長內一次都沒有發生，講的是同一件事情。由這條關係算出 $F_{\sssig T}(t)=1-e^{-\lambda t}$ 之後再微分，即證得單位時間內的次數服從卜瓦松分配時，等待時間服從指數分配。比例伸縮性質則只需把 $M_{\sssig X}(t)$ 的引數換成 <span class="text-nowrap">$at$，</span>$\beta$ 隨之變為 <span class="text-nowrap">$a\beta$，</span>$\beta$ 因此被稱作比例參數。第三點提醒 $\beta$ 與 $\lambda$ 只是同一個參數的兩種詮釋，決定其一另一個即隨之決定。

兩道例題示範的正是同一個問題的兩個角度。[Example 4.26](#ex-exponential-1) 的法一以指數分配算間隔時間超過 $\frac{1}{\,10\,}$ 小時的機率，法二以卜瓦松分配算六分鐘內一次都沒有發生的機率，兩者都得到 <span class="text-nowrap">$e^{-1}$，</span>這正是對偶關係的具體演練。[Example 4.27](#ex-exponential-2) 則把兩個角度分成兩小題: 第一小題求 $3$ 分鐘內恰有 $2$ 人抵達的機率，用的是 $\mathrm{Poi}(6)$ 這個分配；第二小題求下一位顧客在 $2$ 分鐘之內抵達的機率，用的是 $\mathrm{Exp}(\lambda=2)$ 這個分配。兩小題的參數換算都以「每分鐘 $2$ 人」為準。

[下一篇](/teaching-topics/ch4-p11-candidate/)證明指數分配的無記憶性，說明它是連續型分配之中唯一具有這個性質的分配，並給出兩個獨立指數變數取極小值與比較先後次序的結果。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
