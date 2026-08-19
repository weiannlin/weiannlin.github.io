---
title: "二元常態分配的例題"
subtitle: "Examples of the Bivariate Normal Distribution"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 4
topic: 27
order: 427
permalink: /teaching-topics/bivariate-normal-examples/
date: 2026-08-15
published: false
excerpt: "本篇以三道例題演練二元常態分配的性質。第一題由期望值向量與共變異數矩陣得到 $X$ 的邊際分配，再以條件分配 $Y\\mid(X=x)\\sim\\mathcal{N}\\bigl(\\mu_2+\\rho\\frac{\\sigma_2}{\\sigma_1}(x-\\mu_1),\\ (1-\\rho^{2})\\sigma_2^{2}\\bigr)$ 把 $6$ 與 $14$ 認作條件期望值左右各一個條件標準差的位置，反解出 $\\rho=\\frac{3}{5}$，最後由線性組合仍為常態分配求出 $5X+Y$ 與 $5X-Y$ 的分配。第二題給一個兩個邊際都是標準常態、聯合卻不是二元常態的機率密度函數，多出來的那一項在積分時因奇函數而消失，用來說明邊際為常態並不足以保證聯合為二元常態。第三題反過來，由機率函數的 kernel 比對二次形式的係數，解出 $\\sigma_1^{2}=\\sigma_2^{2}=\\frac{2}{3}$ 與 $\\rho=\\frac{1}{2}$，再求得常數 $c$ 與條件期望值 $\\mathbb{E}(Y\\mid X=3)$。"
---

[上一篇](/teaching-topics/bivariate-normal-distribution/)給出[二元常態分配](/teaching-topics/bivariate-normal-distribution/#def-bivariate-normal) <span lang="en">(bivariate normal distribution)</span> 的定義，並依序說明其邊際分配均為[常態分配](/teaching-topics/normal-distribution/#def-normal)、條件分配均為常態分配、零相關與[獨立](/teaching-topics/independent-random-variables/#def-indep-r-v)在此等價，以及兩個變數的任意線性組合仍為常態分配這幾項性質。本篇不再增加新的性質，改以三道例題演練上述結果。

第一道例題給定期望值向量與共變異數矩陣，先由邊際分配得到 $X$ 的分配，再以條件分配把題目所給的條件機率化為條件期望值與條件標準差之間的關係，反解出[相關係數](/teaching-topics/correlation-coefficient/#def-corr)，最後由線性組合仍為常態分配求出兩個線性組合的分配；這一項性質就是常態分配特有的仿射變換 <span lang="en">(affine transformation)</span>。第二道例題給一個兩個邊際都是標準常態、聯合卻不是二元常態的機率密度函數，用來說明「邊際為常態」並不足以保證「聯合為二元常態」。第三道例題反過來，由機率函數的 kernel 比對二次形式的係數，解出兩個變異數與相關係數，再求得機率函數的常數與條件期望值。

## 二元常態的條件分配與線性組合

<div id="ex-bivariate-normal-ex-1" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.60</div>

<div lang="en" markdown="1">
Suppose that the random vector $(X,Y)$ follows a multivariate normal distribution whose mean vector and covariance matrix are

$$
\boldsymbol{\mu}=\begin{bmatrix} 5\\ 10 \end{bmatrix},\quad
\mathbf{\Sigma}=\begin{bmatrix} 1 & 5\rho\\ 5\rho & 25 \end{bmatrix}
$$

where $\rho>0$, and that <span class="text-nowrap">$\mathbb{P}(6<Y<14\mid X=5)=0.6827$.</span> In addition, $\mathbb{P}(Z<1)=0.8413$ holds for a standard normal variable <span class="text-nowrap">$Z$.</span>

<ol class="topic-list-paren">
  <li>Find the distribution of <span class="text-nowrap">$X$.</span></li>
  <li>Determine the value of <span class="text-nowrap">$\rho$.</span></li>
  <li>Let $U=5X+Y$ and <span class="text-nowrap">$V=5X-Y$.</span> Find the distribution of $U$ and that of <span class="text-nowrap">$V$.</span></li>
</ol>
</div>

(1) 由二元常態分配的性質可知
{: .topic-paren-item}

$$
X\sim\mathcal{N}\bigl(\mu_{\sssig X}=5,\ \sigma^{2}_{\sssig X}=1\bigr)
$$

(2) 由二元常態分配的性質可知
{: .topic-paren-item}

$$
Y\mid(X=x)\sim\mathcal{N}\Bigl(\mu_{\sssig Y}+\rho\frac{\sigma_{\sssig Y}}{\sigma_{\sssig X}}(x-\mu_{\sssig X}),\ (1-\rho^{2})\sigma^{2}_{\sssig Y}\Bigr)
$$

其中
{: .topic-paren-cont}

$$
\mu_{\sssig X}=5,\quad \mu_{\sssig Y}=10,\quad \sigma^{2}_{\sssig X}=1,\quad \sigma^{2}_{\sssig Y}=25
$$

由題意可知 <span class="text-nowrap">$\mathbb{P}(6<Y<14\mid X=5)=0.6827$，</span>故知道
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
6=\mathbb{E}(Y\mid X=5)-\sqrt{(1-\rho^{2})\sigma^{2}_{\sssig Y}},\quad 14=\mathbb{E}(Y\mid X=5)+\sqrt{(1-\rho^{2})\sigma^{2}_{\sssig Y}}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
6&=\mathbb{E}(Y\mid X=5)-\sqrt{(1-\rho^{2})\sigma^{2}_{\sssig Y}},\\[0.3em]
14&=\mathbb{E}(Y\mid X=5)+\sqrt{(1-\rho^{2})\sigma^{2}_{\sssig Y}}
\end{aligned}
$$

</div>

又 <span class="text-nowrap">$\mathbb{E}(Y\mid X=5)=\mu_{\sssig Y}=10$，</span>可知
{: .topic-paren-cont}

$$
\sqrt{(1-\rho^{2})\sigma^{2}_{\sssig Y}}=4\qquad\therefore\, \rho=\pm\frac{3}{\,5\,}
$$

但由題目已知 <span class="text-nowrap">$\rho>0$，</span>故知道
{: .topic-paren-cont}

$$
\rho=\frac{3}{\,5\,}
$$

(3) 由二元常態分配的仿射變換性質可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
U=5X+Y\sim\mathcal{N}\bigl(\mu=5\times5+10=35,\ \sigma^{2}=5^{2}\cdot1+1^{2}\cdot25+2\cdot5\cdot1\cdot5\rho=80\bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
U=5X+Y\sim\mathcal{N}\bigl(&\mu=5\times5+10=35,\\[0.3em]
&\sigma^{2}=5^{2}\cdot1+1^{2}\cdot25+2\cdot5\cdot1\cdot5\rho=80\bigr)
\end{aligned}
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
V=5X-Y\sim\mathcal{N}\bigl(\mu=5\times5-10=15,\ \sigma^{2}=5^{2}\cdot1+(-1)^{2}\cdot25-2\cdot5\cdot1\cdot5\rho=20\bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
V=5X-Y\sim\mathcal{N}\bigl(&\mu=5\times5-10=15,\\[0.3em]
&\sigma^{2}=5^{2}\cdot1+(-1)^{2}\cdot25-2\cdot5\cdot1\cdot5\rho=20\bigr)
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個問題巧妙地利用了鐘形分配的經驗法則 (或是常態分配的機率法則)，讓 $6$ 與 $14$ 分別是條件期望值左右各一個條件標準差的值，由此反解相關係數。

然而，讀者即便不知道鐘形分配的經驗法則，事實上也可以從題目所給的 $\mathbb{P}(Z<1)=0.8413$ 得知 $0.6827$ 這個機率是指 <span class="text-nowrap">$\mathbb{P}(-1<Z<1)$。</span>

</div>

## 邊際為常態而聯合不是二元常態

<div id="ex-bivariate-normal-ex-2" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.61</div>

<div lang="en" markdown="1">
Suppose that two random variables $X$ and $Y$ have the joint probability density function

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f(x,y)=\frac{1}{2\pi}\exp\Bigl[-\frac{1}{2}(x^{2}+y^{2})\Bigr]\Bigl\lbrace1+xy\exp\Bigl[-\frac{1}{2}(x^{2}+y^{2}-2)\Bigr]\Bigr\rbrace
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f(x,y)&=\frac{1}{2\pi}\exp\Bigl[-\frac{1}{2}(x^{2}+y^{2})\Bigr]\\[0.25em]
&\qquad\Bigl\lbrace1+xy\exp\Bigl[-\frac{1}{2}(x^{2}+y^{2}-2)\Bigr]\Bigr\rbrace
\end{aligned}
$$

</div>

for $-\infty<x<\infty$ and <span class="text-nowrap">$-\infty<y<\infty$.</span>

<ol class="topic-list-paren">
  <li>Find the marginal pdf of $X$ and the marginal pdf of <span class="text-nowrap">$Y$.</span></li>
  <li>Determine whether the assertion “a joint pdf whose two marginal pdfs are both normal has to be bivariate normal” is correct, giving your reasons in terms of the answers to (1) and the given form of <span class="text-nowrap">$f(x,y)$.</span></li>
</ol>
</div>

(1) 由 [marginal pdf 的性質](/teaching-topics/marginal-probability-density-functions/#def-marginal-pdf)可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f_{\sssig X}(x)&=\int_{-\infty}^{\infty}\frac{1}{2\pi}\exp\Bigl[-\frac{1}{2}(x^{2}+y^{2})\Bigr]\Bigl\lbrace1+xy\exp\Bigl[-\frac{1}{2}(x^{2}+y^{2}-2)\Bigr]\Bigr\rbrace\,dy\\[0.45em]
&=\int_{-\infty}^{\infty}\Bigl\lbrace\frac{1}{2\pi}\exp\Bigl[-\frac{1}{2}(x^{2}+y^{2})\Bigr]+\frac{xy}{2\pi}\exp\bigl[-(x^{2}+y^{2})+1\bigr]\Bigr\rbrace\,dy\\[0.45em]
&=\frac{1}{2\pi}e^{\frac{-x^{2}}{2}}\int_{-\infty}^{\infty}e^{\frac{-y^{2}}{2}}\,dy+\frac{x}{2\pi}e^{1-x^{2}}\int_{-\infty}^{\infty}ye^{-y^{2}}\,dy\\[0.45em]
&=\frac{1}{2\pi}e^{\frac{-x^{2}}{2}}\sqrt{2\pi}+\frac{x}{2\pi}e^{1-x^{2}}\Bigl[\frac{-1}{\,2\,}e^{-y^{2}}\Bigr]_{-\infty}^{\infty}\\[0.45em]
&=\frac{1}{\,\sqrt{2\pi}\,}e^{\frac{-x^{2}}{2}},\ -\infty<x<\infty
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig X}(x)&=\int_{-\infty}^{\infty}\frac{1}{2\pi}\exp\Bigl[-\frac{1}{2}(x^{2}+y^{2})\Bigr]\\[0.25em]
&\qquad\Bigl\lbrace1+xy\exp\Bigl[-\frac{1}{2}(x^{2}+y^{2}-2)\Bigr]\Bigr\rbrace\,dy\\[0.45em]
&=\int_{-\infty}^{\infty}\Bigl\lbrace\frac{1}{2\pi}\exp\Bigl[-\frac{1}{2}(x^{2}+y^{2})\Bigr]\\[0.25em]
&\qquad+\frac{xy}{2\pi}\exp\bigl[-(x^{2}+y^{2})+1\bigr]\Bigr\rbrace\,dy\\[0.45em]
&=\frac{1}{2\pi}e^{\frac{-x^{2}}{2}}\int_{-\infty}^{\infty}e^{\frac{-y^{2}}{2}}\,dy\\[0.25em]
&\qquad+\frac{x}{2\pi}e^{1-x^{2}}\int_{-\infty}^{\infty}ye^{-y^{2}}\,dy\\[0.45em]
&=\frac{1}{2\pi}e^{\frac{-x^{2}}{2}}\sqrt{2\pi}+\frac{x}{2\pi}e^{1-x^{2}}\Bigl[\frac{-1}{\,2\,}e^{-y^{2}}\Bigr]_{-\infty}^{\infty}\\[0.45em]
&=\frac{1}{\,\sqrt{2\pi}\,}e^{\frac{-x^{2}}{2}},\ -\infty<x<\infty
\end{aligned}
$$

</div>

同理可得
{: .topic-paren-cont}

$$
f_{\sssig Y}(y)=\frac{1}{\,\sqrt{2\pi}\,}e^{\frac{-y^{2}}{2}},\ -\infty<y<\infty
$$

(2) 由 (1) 之結果可知 $X\sim\mathcal{N}(0,1)$ 且 <span class="text-nowrap">$Y\sim\mathcal{N}(0,1)$，</span>但由 $(X,Y)$ 之 joint pdf 明顯可知 $(X,Y)$ 並非二元常態分配，故「兩隨機變數邊際分配為常態分配下，其聯合分配必是二元常態分配」的陳述應為錯誤陳述。
{: .topic-paren-item}

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

關於「邊際是常態分配但聯合不是二元常態」的反例有非常非常多，在許多數統的經典教科書中均有提及，這其中有不少同時身兼「零相關但是不獨立」的反例，譬如 [Example 4.48](/teaching-topics/standard-normal-moments-stein-lemma/#ex-normal-moments-1)。

讀者應特別注意的是，儘管這樣的反例很多，但他們一定都發生在「二者不獨立」時，如果我們找來的兩個常態分配是獨立的，則此時這兩個常態分配必定能夠形成相關係數 $\rho=0$ 的二元常態分配。這個性質可以協助我們證明常態母體下，樣本平均數 $\overline{X}$ 與樣本變異數 $S^{2}$ 獨立，稍後在[多元常態分配](/teaching-topics/multivariate-normal-independence/)的章節中會談到。

</div>

## 由 kernel 辨認二元常態分配的參數

<div id="ex-bivariate-normal-ex-3" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.62</div>

<div lang="en" markdown="1">
Suppose that the joint probability density function of $X$ and $Y$ is

$$
f(x,y)=c\,\exp\lbrace-x^{2}+xy-y^{2}\rbrace,\ x,y\in\mathbb{R}
$$

<ol class="topic-list-paren">
  <li>Find the value of <span class="text-nowrap">$c$.</span></li>
  <li>Find the correlation coefficient between $X$ and <span class="text-nowrap">$Y$.</span></li>
  <li>Evaluate <span class="text-nowrap">$\mathbb{E}(Y\mid X=3)$.</span></li>
</ol>
</div>

(1) 透過辨認 $f(x,y)$ 之 kernel (即 $\exp\lbrace-x^{2}+xy-y^{2}\rbrace$)，可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\frac{1}{\,2(1-\rho^{2})\sigma_1^{2}\,}=1,\quad \frac{1}{\,2(1-\rho^{2})\sigma_2^{2}\,}=1,\quad \frac{\rho}{\,(1-\rho^{2})\sigma_1\sigma_2\,}=1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\frac{1}{\,2(1-\rho^{2})\sigma_1^{2}\,}&=1,\\[0.3em]
\frac{1}{\,2(1-\rho^{2})\sigma_2^{2}\,}&=1,\\[0.3em]
\frac{\rho}{\,(1-\rho^{2})\sigma_1\sigma_2\,}&=1
\end{aligned}
$$

</div>

由此可得
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\Longrightarrow\ \sigma_1^{2}=\sigma_2^{2}=\frac{1}{\,2(1-\rho^{2})\,},\quad \frac{\rho}{\,1-\rho^{2}\,}=\sigma_1\sigma_2=\frac{1}{\,2(1-\rho^{2})\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ \sigma_1^{2}&=\sigma_2^{2}=\frac{1}{\,2(1-\rho^{2})\,},\\[0.3em]
\frac{\rho}{\,1-\rho^{2}\,}&=\sigma_1\sigma_2=\frac{1}{\,2(1-\rho^{2})\,}
\end{aligned}
$$

</div>

由此可知
{: .topic-paren-cont}

$$
\Longrightarrow\ \rho=\frac{1}{\,2\,},\quad \sigma_1^{2}=\sigma_2^{2}=\frac{2}{\,3\,}
$$

故知道
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\therefore\ (X,Y)\sim\mathcal{BN}\Bigl(\mu_1=0,\ \mu_2=0,\ \sigma_1^{2}=\frac{2}{\,3\,},\ \sigma_2^{2}=\frac{2}{\,3\,},\ \rho=\frac{1}{\,2\,}\Bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\therefore\ (X,Y)\sim\mathcal{BN}\Bigl(&\mu_1=0,\ \mu_2=0,\\[0.3em]
&\sigma_1^{2}=\frac{2}{\,3\,},\ \sigma_2^{2}=\frac{2}{\,3\,},\\[0.3em]
&\rho=\frac{1}{\,2\,}\Bigr)
\end{aligned}
$$

</div>

則可知
{: .topic-paren-cont}

$$
c=\frac{1}{\,2\pi\sigma_1\sigma_2\sqrt{1-\rho^{2}}\,}=\frac{\sqrt{3}}{\,2\pi\,}
$$

(2) 由前一小題可知
{: .topic-paren-item}

$$
\rho=\frac{1}{\,2\,}
$$

(3) 由二元常態分配的性質可知
{: .topic-paren-item}

$$
Y\mid(X=x)\sim\mathcal{N}\Bigl(\mu_2+\rho\frac{\sigma_2}{\sigma_1}(x-\mu_1),\ (1-\rho^{2})\sigma^{2}_2\Bigr)
$$

其中
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mu_1=0,\quad \mu_2=0,\quad \sigma^{2}_1=\frac{2}{\,3\,},\quad \sigma^{2}_2=\frac{2}{\,3\,},\quad \rho=\frac{1}{\,2\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mu_1&=0,\quad \mu_2=0,\\[0.3em]
\sigma^{2}_1&=\frac{2}{\,3\,},\quad \sigma^{2}_2=\frac{2}{\,3\,},\\[0.3em]
\rho&=\frac{1}{\,2\,}
\end{aligned}
$$

</div>

故知道
{: .topic-paren-cont}

$$
\mathbb{E}(Y\mid X=3)=0+\frac{1}{\,2\,}\frac{\,\sqrt{\frac{2}{\,3\,}}\,}{\,\sqrt{\frac{2}{\,3\,}}\,}(3-0)=\frac{\,3\,}{2}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個問題亦有矩陣求解方式，但我們需要先具備處理矩陣版本的多元常態分配 <span lang="en">(multivariate normal distribution)</span> 的能力，見[下一篇](/teaching-topics/multivariate-normal-distribution/)。

</div>

## 本篇小結

[Example 4.60](#ex-bivariate-normal-ex-1) 的三個小題各用一項性質。第一小題只需要邊際分配為常態分配這一項，由期望值向量與共變異數矩陣的第一個對角元素即得 <span class="text-nowrap">$X\sim\mathcal{N}(5,1)$。</span>第二小題的關鍵在於認出題目所給的 $0.6827$ 是一個標準差以內的機率: 由條件分配可知 $\mathbb{E}(Y\mid X=5)=\mu_{\sssig Y}=10$ 而條件變異數為 $(1-\rho^{2})\sigma^{2}_{\sssig Y}$ 這個式子，因此 $6$ 與 $14$ 分別是條件期望值減去與加上一個條件標準差的位置，由 $\sqrt{(1-\rho^{2})\times25}=4$ 這條等式解得 <span class="text-nowrap">$\rho=\pm\frac{3}{\,5\,}$，</span>再由題目給定的 $\rho>0$ 取正根。第三小題用的是線性組合仍為常態分配這一項，兩個線性組合的變異數只差在 $2ab\rho\sigma_1\sigma_2$ 這一項的正負號，因此 $U=5X+Y$ 的變異數為 $80$ 而 $V=5X-Y$ 的變異數為 <span class="text-nowrap">$20$。</span>

[Example 4.61](#ex-bivariate-normal-ex-2) 的作用是給出一個反例。所給的機率密度函數是一個標準二元常態密度乘上 $1+xy\exp\bigl[-\frac{1}{2}(x^{2}+y^{2}-2)\bigr]$ 這個因子，把它展開之後多出來的那一項含有 $y\,e^{-y^{2}}$ 這個奇函數，對 $y$ 在整條實數線上積分之後為 <span class="text-nowrap">$0$，</span>剩下的正是標準常態的密度，$f_{\sssig Y}(y)$ 同理。兩個邊際都是 $\mathcal{N}(0,1)$ 而聯合的機率密度函數並不是二元常態的形式，因此「兩個邊際為常態則聯合必為二元常態」這個陳述並不成立。反過來說，若兩個常態變數彼此獨立，其聯合分配必定是相關係數為 $0$ 的二元常態分配，這一點在證明常態母體下樣本平均數與樣本變異數獨立時會用到。

[Example 4.62](#ex-bivariate-normal-ex-3) 走的是相反的方向: 題目只給機率函數的形狀，要由它反推參數。作法是把 $\exp\lbrace-x^{2}+xy-y^{2}\rbrace$ 與二元常態密度的指數項逐項比對，$x^{2}$、$y^{2}$ 與 $xy$ 三個係數各給一條方程式，解得 $\rho=\frac{1}{\,2\,}$ 與 $\sigma_1^{2}=\sigma_2^{2}=\frac{2}{\,3\,}$ 這兩組值；指數項中沒有一次項，因此兩個期望值都是 <span class="text-nowrap">$0$。</span>參數確定之後，常數 $c$ 就是二元常態密度前面的那一個係數 $\frac{1}{2\pi\sigma_1\sigma_2\sqrt{1-\rho^{2}}}$ 這個式子，算得 <span class="text-nowrap">$\frac{\sqrt{3}}{\,2\pi\,}$；</span>條件期望值則直接代入條件分配的期望值公式，得到 <span class="text-nowrap">$\frac{\,3\,}{2}$。</span>這一題另有以矩陣書寫的解法，要等到多元常態分配的矩陣形式建立之後才能使用。

[下一篇](/teaching-topics/multivariate-normal-distribution/)把二元常態分配推廣到 $n$ 個變數，以期望值向量與共變異數矩陣書寫多元常態分配的機率函數，並給出相應的性質與例題。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
