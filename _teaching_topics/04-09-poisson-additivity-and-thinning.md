---
title: "卜瓦松分配的可加性、條件二項與稀化"
subtitle: "Additivity, Conditional Binomial and Thinning of the Poisson Distribution"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 4
topic: 9
order: 409
permalink: /teaching-topics/poisson-additivity-and-thinning/
date: 2026-08-12
published: false
excerpt: "兩個獨立的卜瓦松變數相加之後仍為卜瓦松分配，平均發生率相加；而在兩者的總和固定為 $n$ 的條件下，其中一個變數的條件分配是二項分配，成功機率為兩個平均發生率的比值。反過來看，若卜瓦松變數所計數的每一次發生都以固定機率 $p$ 被歸入某一類，則該類的個數服從 $\\mathrm{Poi}(\\lambda p)$ 這個分配，另一類的個數服從 $\\mathrm{Poi}\\bigl(\\lambda(1-p)\\bigr)$ 這個分配，而且兩者彼此獨立。本篇完整證明這兩個定理，並以六道例題演練卜瓦松機率的計算、二項機率的卜瓦松近似，以及定義在頁數與體積這一類非時間區段上的卜瓦松分配。"
---

[上一篇](/teaching-topics/poisson-process-and-distribution/)給出[卜瓦松過程](/teaching-topics/poisson-process-and-distribution/#def-poisson-process)與[卜瓦松分配](/teaching-topics/poisson-process-and-distribution/#def-poisson-distribution)的定義，並完整推導了卜瓦松分配的機率函數、期望值、變異數與動差母函數。本篇先以兩道例題演練卜瓦松機率的計算，其中一道用到二項機率的卜瓦松近似。

接著進入兩個定理。第一個定理處理兩個獨立卜瓦松變數的和: 和本身仍是卜瓦松分配，而在總和給定之下，其中一個變數的條件分配是二項分配。第二個定理處理相反的方向: 把一個卜瓦松變數所計數的每一次發生依固定機率分成兩類，兩類的個數各自仍服從卜瓦松分配，並且彼此獨立。最後兩道例題把卜瓦松分配用在頁數與體積這一類非時間的區段上。

## 卜瓦松機率的計算與二項機率的卜瓦松近似

<div id="ex-poisson-sum-1" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.21</div>

<div lang="en" markdown="1">
Suppose that a traffic police officer must patrol the important places of a precinct during every half-hour period. Let $Y$ denote the number of times one particular place is patrolled within half an hour, and suppose that $Y$ follows a Poisson distribution whose mean is one patrol per half hour.

<ol class="topic-list-paren">
  <li>What is the probability that the officer misses that particular place entirely during a given half-hour period?</li>
  <li>What is the probability that the officer patrols that place exactly once?</li>
  <li>What is the probability that the officer patrols that place at least once?</li>
</ol>
</div>

(1) 由題目敘述可知，令 $Y$ 表示該員警每半小時巡視該地點的次數，則 <span class="text-nowrap">$Y\sim\mathrm{Poi}(\lambda=1)$，</span>所求為
{: .topic-paren-item}

$$
\mathbb{P}(Y=0)=\frac{\,e^{-1}1^{0}\,}{0!}=e^{-1}\fallingdotseq0.3679
$$

(2) 承接上題假設，所求為
{: .topic-paren-item}

$$
\mathbb{P}(Y=1)=\frac{\,e^{-1}1^{1}\,}{1!}=e^{-1}\fallingdotseq0.3679
$$

(3) 承接上題假設，所求為
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(Y\geqslant1)=1-\mathbb{P}(Y=0)=1-e^{-1}\fallingdotseq0.6321
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(Y\geqslant1)&=1-\mathbb{P}(Y=0)\\[0.4em]
&=1-e^{-1}\fallingdotseq0.6321
\end{aligned}
$$

</div>

</div>

<div id="ex-binomial-2-continued" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.3 <span lang="en">(Continued)</span></div>

<div lang="en" markdown="1">
Suppose that a newly produced LED lamp fails to work with probability <span class="text-nowrap">$3\%$.</span>

<ol class="topic-list-paren topic-list-paren--start-2">
  <li>Suppose that the quality control department draws $200$ such lamps at random. Find the probability that exactly $7$ of them fail to work, using the Poisson approximation.</li>
</ol>
</div>

(2) 由題意可令 $X$ 表示 LED 燈的壞掉個數，則
{: .topic-paren-item}

$$
X\sim\mathrm{Bin}(n=200,\ p=0.03)
$$

又由二項分配的卜瓦松近似可知，若令
{: .topic-paren-cont}

$$
Y\sim\mathrm{Poi}(\lambda=200\times0.03=6)
$$

則所求為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X=7)\fallingdotseq\mathbb{P}(Y=7)=\frac{e^{-6}6^{7}}{\,7!\,}\fallingdotseq0.1377
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X=7)&\fallingdotseq\mathbb{P}(Y=7)\\[0.4em]
&=\frac{e^{-6}6^{7}}{\,7!\,}\fallingdotseq0.1377
\end{aligned}
$$

</div>

精確解為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X=7)=\binom{200}{7}\bigl(0.03\bigr)^{7}\bigl(0.97\bigr)^{193}\fallingdotseq0.1398
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X=7)&=\binom{200}{7}\bigl(0.03\bigr)^{7}\bigl(0.97\bigr)^{193}\\[0.4em]
&\fallingdotseq0.1398
\end{aligned}
$$

</div>

</div>

## 兩個獨立卜瓦松變數的和與條件二項分配

<div id="thm-poisson-sum-conditional" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 4.10 (卜瓦松分配的和與條件二項, sum of Poisson variables and the conditional binomial)</div>

令 $X\sim\mathrm{Poi}(\lambda=\lambda_1)$ $\indep$ $Y\sim\mathrm{Poi}(\lambda=\lambda_2)$ 成立，則

(1)
{: .topic-paren-item}

$$
X+Y\sim\mathrm{Poi}(\lambda_1+\lambda_2)
$$

(2)
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
X\mid(X+Y=n)\sim\mathrm{Bin}\biggl(n,\ p=\frac{\lambda_1}{\,\lambda_1+\lambda_2\,}\biggr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
X\mid(X+Y=n)&\sim\mathrm{Bin}\biggl(n,\ p=\frac{\lambda_1}{\,\lambda_1+\lambda_2\,}\biggr)
\end{aligned}
$$

</div>

</div>

<div class="topic-proof" markdown="1">
**Proof.**

(1) 由 $X\sim\mathrm{Poi}(\lambda=\lambda_1)\indep Y\sim\mathrm{Poi}(\lambda=\lambda_2)$ 可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
M_{\sssig X}(t)=e^{\lambda_1(e^{t}-1)},\qquad M_{\sssig Y}(t)=e^{\lambda_2(e^{t}-1)}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig X}(t)&=e^{\lambda_1(e^{t}-1)},\\[0.45em]
M_{\sssig Y}(t)&=e^{\lambda_2(e^{t}-1)}
\end{aligned}
$$

</div>

令 <span class="text-nowrap">$W=X+Y$，</span>則
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
M_{\sssig W}(t)=M_{\sssig X}(t)\,M_{\sssig Y}(t)=e^{\lambda_1(e^{t}-1)}\,e^{\lambda_2(e^{t}-1)}=e^{(\lambda_1+\lambda_2)\cdot(e^{t}-1)}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig W}(t)&=M_{\sssig X}(t)\,M_{\sssig Y}(t)\\[0.4em]
&=e^{\lambda_1(e^{t}-1)}\,e^{\lambda_2(e^{t}-1)}\\[0.4em]
&=e^{(\lambda_1+\lambda_2)\cdot(e^{t}-1)}
\end{aligned}
$$

</div>

由[動差母函數的唯一性](/teaching-topics/uniqueness-of-the-mgf/#thm-mgf-uniqueness)可知
{: .topic-paren-cont}

$$
W\sim\mathrm{Poi}(\lambda_1+\lambda_2)
$$

(2) 承 (1)，令 <span class="text-nowrap">$W=X+Y\sim\mathrm{Poi}(\lambda=\lambda_1+\lambda_2)$，</span>由於 <span class="text-nowrap">$X\indep Y$，</span>我們有
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
p_{\sssig X\mid X+Y}(x\mid n)&=\frac{\,p_{\sssig XY}(x=x,\ y=n-x)\,}{p_{\sssig X+Y}(n)}=\frac{\,p_{\sssig X}(x)\,p_{\sssig Y}(n-x)\,}{p_{\sssig W}(n)}\\[0.45em]
&=\frac{\,\frac{\,e^{-\lambda_1}\lambda_1^{x}\,}{x!}\frac{\,e^{-\lambda_2}\lambda_2^{n-x}\,}{(n-x)!}\,}{\frac{\,e^{-(\lambda_1+\lambda_2)}(\lambda_1+\lambda_2)^{n}\,}{n!}}=\frac{n!}{\,x!(n-x)!\,}\frac{\,\lambda_1^{x}\lambda_2^{n-x}\,}{\,(\lambda_1+\lambda_2)^{n}\,}\\[0.45em]
&=\binom{n}{x}\biggl(\frac{\lambda_1}{\,\lambda_1+\lambda_2\,}\biggr)^{x}\biggl(\frac{\lambda_2}{\,\lambda_1+\lambda_2\,}\biggr)^{n-x},\ x=0,1,2,\ldots,n
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig X\mid X+Y}(x\mid n)&=\frac{\,p_{\sssig XY}(x=x,\ y=n-x)\,}{p_{\sssig X+Y}(n)}\\[0.35em]
&=\frac{\,p_{\sssig X}(x)\,p_{\sssig Y}(n-x)\,}{p_{\sssig W}(n)}\\[0.35em]
&=\frac{\,\frac{\,e^{-\lambda_1}\lambda_1^{x}\,}{x!}\frac{\,e^{-\lambda_2}\lambda_2^{n-x}\,}{(n-x)!}\,}{\frac{\,e^{-(\lambda_1+\lambda_2)}(\lambda_1+\lambda_2)^{n}\,}{n!}}\\[0.35em]
&=\frac{n!}{\,x!(n-x)!\,}\frac{\,\lambda_1^{x}\lambda_2^{n-x}\,}{\,(\lambda_1+\lambda_2)^{n}\,}\\[0.35em]
&=\binom{n}{x}\biggl(\frac{\lambda_1}{\,\lambda_1+\lambda_2\,}\biggr)^{x}\\[0.25em]
&\qquad \biggl(\frac{\lambda_2}{\,\lambda_1+\lambda_2\,}\biggr)^{n-x},\\[0.25em]
&\qquad x=0,1,2,\ldots,n
\end{aligned}
$$

</div>

此即
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
X\mid(X+Y=n)\sim\mathrm{Bin}\biggl(n,\ p=\frac{\lambda_1}{\,\lambda_1+\lambda_2\,}\biggr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
X\mid(X+Y=n)&\sim\mathrm{Bin}\biggl(n,\ p=\frac{\lambda_1}{\,\lambda_1+\lambda_2\,}\biggr)
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div id="ex-poisson-sum-2" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.22</div>

<div lang="en" markdown="1">
Suppose that $X$ and $Y$ are independent Poisson random variables whose probability functions are

$$
\begin{gathered}
f(x)=\frac{\,m^{x}e^{-m}\,}{x!},\ x=0,1,2,\ldots\\[0.45em]
\text{and}\ f(y)=\frac{\,n^{y}e^{-n}\,}{y!},\ y=0,1,2,\ldots
\end{gathered}
$$

<ol class="topic-list-paren">
  <li>Find the probability function of <span class="text-nowrap">$X+Y$.</span></li>
  <li>Find the conditional probability function <span class="text-nowrap">$f(x\mid x+y=50)$.</span></li>
</ol>
</div>

(1) 由題意可知
{: .topic-paren-item}

$$
X\sim\mathrm{Poi}(\lambda=m)\indep Y\sim\mathrm{Poi}(\lambda=n)
$$

故
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
M_{\sssig X}(t)=e^{m(e^{t}-1)},\qquad M_{\sssig Y}(t)=e^{n(e^{t}-1)}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig X}(t)&=e^{m(e^{t}-1)},\\[0.45em]
M_{\sssig Y}(t)&=e^{n(e^{t}-1)}
\end{aligned}
$$

</div>

且若令 <span class="text-nowrap">$W=X+Y$，</span>則
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
M_{\sssig W}(t)=M_{\sssig X}(t)\,M_{\sssig Y}(t)=e^{m(e^{t}-1)}\,e^{n(e^{t}-1)}=e^{(m+n)\cdot(e^{t}-1)}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig W}(t)&=M_{\sssig X}(t)\,M_{\sssig Y}(t)\\[0.4em]
&=e^{m(e^{t}-1)}\,e^{n(e^{t}-1)}\\[0.4em]
&=e^{(m+n)\cdot(e^{t}-1)}
\end{aligned}
$$

</div>

由[動差母函數的唯一性](/teaching-topics/uniqueness-of-the-mgf/#thm-mgf-uniqueness)可知 $W\sim\mathrm{Poi}(m+n)$ 這個結果，故
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig W}(w)=\frac{\,e^{-(m+n)}(m+n)^{w}\,}{w!},\ w=0,1,2,\ldots
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig W}(w)&=\frac{\,e^{-(m+n)}(m+n)^{w}\,}{w!},\\[0.25em]
&\qquad w=0,1,2,\ldots
\end{aligned}
$$

</div>

(2) 承上題，令 <span class="text-nowrap">$W=X+Y\sim\mathrm{Poi}(\lambda=m+n)$，</span>由於 <span class="text-nowrap">$X\indep Y$，</span>我們有
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f(x\mid x+y=50)&=\frac{\,f(x=x,\ y=50-x)\,}{f(x+y=50)}=\frac{\,f_{\sssig X}(x)\,f_{\sssig Y}(50-x)\,}{f_{\sssig W}(50)}\\[0.45em]
&=\frac{\,\frac{\,e^{-m}m^{x}\,}{x!}\frac{\,e^{-n}n^{50-x}\,}{(50-x)!}\,}{\frac{\,e^{-(n+m)}(n+m)^{50}\,}{50!}}=\frac{50!}{\,x!(50-x)!\,}\frac{\,m^{x}n^{50-x}\,}{\,(n+m)^{50}\,}\\[0.45em]
&=\binom{50}{x}\biggl(\frac{m}{\,n+m\,}\biggr)^{x}\biggl(\frac{n}{\,n+m\,}\biggr)^{50-x},\\[0.25em]
&\qquad x=0,1,2,\ldots,50
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f(x\mid x+y=50)&=\frac{\,f(x=x,\ y=50-x)\,}{f(x+y=50)}\\[0.35em]
&=\frac{\,f_{\sssig X}(x)\,f_{\sssig Y}(50-x)\,}{f_{\sssig W}(50)}\\[0.35em]
&=\frac{\,\frac{\,e^{-m}m^{x}\,}{x!}\frac{\,e^{-n}n^{50-x}\,}{(50-x)!}\,}{\frac{\,e^{-(n+m)}(n+m)^{50}\,}{50!}}\\[0.35em]
&=\frac{50!}{\,x!(50-x)!\,}\frac{\,m^{x}n^{50-x}\,}{\,(n+m)^{50}\,}\\[0.35em]
&=\binom{50}{x}\biggl(\frac{m}{\,n+m\,}\biggr)^{x}\\[0.25em]
&\qquad \biggl(\frac{n}{\,n+m\,}\biggr)^{50-x},\\[0.25em]
&\qquad x=0,1,2,\ldots,50
\end{aligned}
$$

</div>

此即
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
X\mid(X+Y=50)\sim\mathrm{Bin}\biggl(n=50,\ p=\frac{m}{\,m+n\,}\biggr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
X\mid(X+Y=50)&\sim\mathrm{Bin}\biggl(n=50,\ p=\frac{m}{\,m+n\,}\biggr)
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

二項分配與卜瓦松分配間的特殊關係並不只有上述的這一項，下面這一層關係也很常見。

</div>

## 卜瓦松分配的稀化

<div id="thm-poisson-thinning" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 4.11 (卜瓦松分配的稀化, thinning of a Poisson variable)</div>

令 $X\sim\mathrm{Poi}(\lambda)$ 與 $Y\mid(X=x)\sim\mathrm{Bin}(n=x,\ p)$ 成立，則

(1)
{: .topic-paren-item}

$$
Y\sim\mathrm{Poi}(\lambda\,p)
$$

(2)
{: .topic-paren-item}

$$
X-Y\sim\mathrm{Poi}\bigl(\lambda(1-p)\bigr)
$$

(3)
{: .topic-paren-item}

$$
Y\indep(X-Y)
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.**

(1) 由 $X\sim\mathrm{Poi}(\lambda)$ 與 $Y\mid(X=x)\sim\mathrm{Bin}(n=x,\ p)$ 可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
p_{\sssig X}(x)=\frac{\,e^{-\lambda}\lambda^{x}\,}{x!},\ x=0,1,\ldots\\[0.45em]
\text{與}\ p_{\sssig Y\mid X}(y\mid x)=\binom{x}{y}p^{y}(1-p)^{x-y},\ y=0,1,\ldots,x
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig X}(x)&=\frac{\,e^{-\lambda}\lambda^{x}\,}{x!},\ x=0,1,\ldots\\[0.45em]
\text{與}\ p_{\sssig Y\mid X}(y\mid x)&=\binom{x}{y}p^{y}(1-p)^{x-y},\\[0.25em]
&\qquad y=0,1,\ldots,x
\end{aligned}
$$

</div>

則有
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
p_{\sssig XY}(x,y)&=p_{\sssig Y\mid X}(y\mid x)\,p_{\sssig X}(x)=\frac{\,e^{-\lambda}\lambda^{x}\,}{x!}\frac{x!}{\,y!(x-y)!\,}p^{y}(1-p)^{x-y}\\[0.45em]
&=\frac{e^{-\lambda}}{\,y!(x-y)!\,}\lambda^{x}p^{y}(1-p)^{x-y},\\[0.25em]
&\qquad y=0,1,2,\ldots,\ x=y,y+1,\ldots
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig XY}(x,y)&=p_{\sssig Y\mid X}(y\mid x)\,p_{\sssig X}(x)\\[0.35em]
&=\frac{\,e^{-\lambda}\lambda^{x}\,}{x!}\frac{x!}{\,y!(x-y)!\,}p^{y}(1-p)^{x-y}\\[0.35em]
&=\frac{e^{-\lambda}}{\,y!(x-y)!\,}\lambda^{x}p^{y}(1-p)^{x-y},\\[0.25em]
&\qquad y=0,1,2,\ldots,\ x=y,y+1,\ldots
\end{aligned}
$$

</div>

令 <span class="text-nowrap">$U=Y,\ V=X-Y$，</span>則 <span class="text-nowrap">$X=U+V,\ Y=U$，</span>我們有
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
p_{\sssig UV}(u,v)&=p_{\sssig XY}(u+v,\ u)=\frac{e^{-\lambda}}{\,u!v!\,}\lambda^{u+v}p^{u}(1-p)^{v}\\[0.45em]
&=\frac{e^{-\lambda}}{\,u!v!\,}\bigl[\lambda(1-p)\bigr]^{v}(\lambda p)^{u},\ u=0,1,2,\ldots,\ v=0,1,2,\ldots\\[0.45em]
&=\frac{\,e^{-\lambda p}(\lambda p)^{u}\,}{u!}\frac{\,e^{-\lambda(1-p)}\bigl[\lambda(1-p)\bigr]^{v}\,}{v!},\\[0.25em]
&\qquad u=0,1,2,\ldots,\ v=0,1,2,\ldots
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig UV}(u,v)&=p_{\sssig XY}(u+v,\ u)\\[0.35em]
&=\frac{e^{-\lambda}}{\,u!v!\,}\lambda^{u+v}p^{u}(1-p)^{v}\\[0.35em]
&=\frac{e^{-\lambda}}{\,u!v!\,}\bigl[\lambda(1-p)\bigr]^{v}(\lambda p)^{u},\\[0.25em]
&\qquad u=0,1,2,\ldots,\ v=0,1,2,\ldots\\[0.35em]
&=\frac{\,e^{-\lambda p}(\lambda p)^{u}\,}{u!}\frac{\,e^{-\lambda(1-p)}\bigl[\lambda(1-p)\bigr]^{v}\,}{v!},\\[0.25em]
&\qquad u=0,1,2,\ldots,\ v=0,1,2,\ldots
\end{aligned}
$$

</div>

可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
p_{\sssig U}(u)&=\sum_{v=0}^{\infty}\frac{\,e^{-\lambda p}(\lambda p)^{u}\,}{u!}\frac{\,e^{-\lambda(1-p)}\bigl[\lambda(1-p)\bigr]^{v}\,}{v!}\\[0.45em]
&=\frac{\,e^{-\lambda p}(\lambda p)^{u}\,}{u!},\ u=0,1,2,\ldots
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig U}(u)&=\sum_{v=0}^{\infty}\frac{\,e^{-\lambda p}(\lambda p)^{u}\,}{u!}\frac{\,e^{-\lambda(1-p)}\bigl[\lambda(1-p)\bigr]^{v}\,}{v!}\\[0.35em]
&=\frac{\,e^{-\lambda p}(\lambda p)^{u}\,}{u!},\ u=0,1,2,\ldots
\end{aligned}
$$

</div>

此即
{: .topic-paren-cont}

$$
U=Y\sim\mathrm{Poi}(\lambda p)
$$

(2) 承 (1)，可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
p_{\sssig V}(v)&=\sum_{u=0}^{\infty}\frac{\,e^{-\lambda p}(\lambda p)^{u}\,}{u!}\frac{\,e^{-\lambda(1-p)}\bigl[\lambda(1-p)\bigr]^{v}\,}{v!}\\[0.45em]
&=\frac{\,e^{-\lambda(1-p)}\bigl[\lambda(1-p)\bigr]^{v}\,}{v!},\ v=0,1,2,\ldots
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig V}(v)&=\sum_{u=0}^{\infty}\frac{\,e^{-\lambda p}(\lambda p)^{u}\,}{u!}\frac{\,e^{-\lambda(1-p)}\bigl[\lambda(1-p)\bigr]^{v}\,}{v!}\\[0.35em]
&=\frac{\,e^{-\lambda(1-p)}\bigl[\lambda(1-p)\bigr]^{v}\,}{v!},\ v=0,1,2,\ldots
\end{aligned}
$$

</div>

此即
{: .topic-paren-cont}

$$
V=X-Y\sim\mathrm{Poi}\bigl(\lambda(1-p)\bigr)
$$

(3) 由於 <span class="text-nowrap">$p_{\sssig UV}(u,v)=p_{\sssig U}(u)\,p_{\sssig V}(v)$，</span>故知道
{: .topic-paren-item}

$$
U=Y\indep V=X-Y
$$

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div id="ex-poisson-sum-3" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.23</div>

<div lang="en" markdown="1">
Suppose that $X$ follows a Poisson distribution with parameter <span class="text-nowrap">$\lambda$,</span> that is <span class="text-nowrap">$X\sim\mathrm{Poi}(\lambda)$,</span> and that given $X=x$ the random variable $Y$ follows the binomial distribution <span class="text-nowrap">$\mathrm{Bin}(x,p)$.</span>

<ol class="topic-list-paren">
  <li>Evaluate $\mathbb{E}(Y)$ and <span class="text-nowrap">$\mathrm{Var}(Y)$.</span></li>
  <li>Show that $Y$ and $X-Y$ are independent.</li>
</ol>
</div>

(1) 由題意可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
X\sim\mathrm{Poi}(\lambda),\qquad Y\mid(X=x)\sim\mathrm{Bin}(x,\ p)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
X&\sim\mathrm{Poi}(\lambda),\\[0.45em]
Y\mid(X=x)&\sim\mathrm{Bin}(x,\ p)
\end{aligned}
$$

</div>

故
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(Y)=\mathbb{E}\bigl[\mathbb{E}(Y\mid X)\bigr]=\mathbb{E}(Xp)=p\,\mathbb{E}(X)=p\,\lambda
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(Y)&=\mathbb{E}\bigl[\mathbb{E}(Y\mid X)\bigr]=\mathbb{E}(Xp)\\[0.4em]
&=p\,\mathbb{E}(X)=p\,\lambda
\end{aligned}
$$

</div>

且
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(Y)&=\mathbb{E}\bigl[\mathrm{Var}(Y\mid X)\bigr]+\mathrm{Var}\bigl[\mathbb{E}(Y\mid X)\bigr]\\[0.45em]
&=\mathbb{E}\bigl[Xp(1-p)\bigr]+\mathrm{Var}(Xp)\\[0.45em]
&=p(1-p)\,\lambda+p^{2}\,\lambda=p\,\lambda
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(Y)&=\mathbb{E}\bigl[\mathrm{Var}(Y\mid X)\bigr]\\[0.25em]
&\qquad +\mathrm{Var}\bigl[\mathbb{E}(Y\mid X)\bigr]\\[0.4em]
&=\mathbb{E}\bigl[Xp(1-p)\bigr]+\mathrm{Var}(Xp)\\[0.4em]
&=p(1-p)\,\lambda+p^{2}\,\lambda=p\,\lambda
\end{aligned}
$$

</div>

(2) 由 $X\sim\mathrm{Poi}(\lambda)$ 與 $Y\mid(X=x)\sim\mathrm{Bin}(n=x,\ p)$ 可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
p_{\sssig X}(x)=\frac{\,e^{-\lambda}\lambda^{x}\,}{x!},\ x=0,1,\ldots\\[0.45em]
\text{與}\ p_{\sssig Y\mid X}(y\mid x)=\binom{x}{y}p^{y}(1-p)^{x-y},\ y=0,1,\ldots,x
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig X}(x)&=\frac{\,e^{-\lambda}\lambda^{x}\,}{x!},\ x=0,1,\ldots\\[0.45em]
\text{與}\ p_{\sssig Y\mid X}(y\mid x)&=\binom{x}{y}p^{y}(1-p)^{x-y},\\[0.25em]
&\qquad y=0,1,\ldots,x
\end{aligned}
$$

</div>

則有
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
p_{\sssig XY}(x,y)&=p_{\sssig Y\mid X}(y\mid x)\,p_{\sssig X}(x)=\frac{\,e^{-\lambda}\lambda^{x}\,}{x!}\frac{x!}{\,y!(x-y)!\,}p^{y}(1-p)^{x-y}\\[0.45em]
&=\frac{e^{-\lambda}}{\,y!(x-y)!\,}\lambda^{x}p^{y}(1-p)^{x-y},\\[0.25em]
&\qquad y=0,1,2,\ldots,\ x=y,y+1,\ldots
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig XY}(x,y)&=p_{\sssig Y\mid X}(y\mid x)\,p_{\sssig X}(x)\\[0.35em]
&=\frac{\,e^{-\lambda}\lambda^{x}\,}{x!}\frac{x!}{\,y!(x-y)!\,}p^{y}(1-p)^{x-y}\\[0.35em]
&=\frac{e^{-\lambda}}{\,y!(x-y)!\,}\lambda^{x}p^{y}(1-p)^{x-y},\\[0.25em]
&\qquad y=0,1,2,\ldots,\ x=y,y+1,\ldots
\end{aligned}
$$

</div>

令 <span class="text-nowrap">$U=Y,\ V=X-Y$，</span>則 <span class="text-nowrap">$X=U+V,\ Y=U$，</span>我們有
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
p_{\sssig UV}(u,v)&=p_{\sssig XY}(u+v,\ u)=\frac{e^{-\lambda}}{\,u!v!\,}\lambda^{u+v}p^{u}(1-p)^{v}\\[0.45em]
&=\frac{e^{-\lambda}}{\,u!v!\,}\bigl[\lambda(1-p)\bigr]^{v}(\lambda p)^{u},\ u=0,1,2,\ldots,\ v=0,1,2,\ldots\\[0.45em]
&=\frac{\,e^{-\lambda p}(\lambda p)^{u}\,}{u!}\frac{\,e^{-\lambda(1-p)}\bigl[\lambda(1-p)\bigr]^{v}\,}{v!},\\[0.25em]
&\qquad u=0,1,2,\ldots,\ v=0,1,2,\ldots
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig UV}(u,v)&=p_{\sssig XY}(u+v,\ u)\\[0.35em]
&=\frac{e^{-\lambda}}{\,u!v!\,}\lambda^{u+v}p^{u}(1-p)^{v}\\[0.35em]
&=\frac{e^{-\lambda}}{\,u!v!\,}\bigl[\lambda(1-p)\bigr]^{v}(\lambda p)^{u},\\[0.25em]
&\qquad u=0,1,2,\ldots,\ v=0,1,2,\ldots\\[0.35em]
&=\frac{\,e^{-\lambda p}(\lambda p)^{u}\,}{u!}\frac{\,e^{-\lambda(1-p)}\bigl[\lambda(1-p)\bigr]^{v}\,}{v!},\\[0.25em]
&\qquad u=0,1,2,\ldots,\ v=0,1,2,\ldots
\end{aligned}
$$

</div>

則由於 <span class="text-nowrap">$p_{\sssig UV}(u,v)=p_{\sssig U}(u)\,p_{\sssig V}(v)$，</span>故知道
{: .topic-paren-cont}

$$
U=Y\indep V=X-Y
$$

</div>

## 定義在非時間區段上的卜瓦松分配

<div id="ex-poisson-sum-4" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.24</div>

<div lang="en" markdown="1">
Ellen is enrolled in a typing course, and the task assigned to her is to produce a report of $10$ pages within one hour. Suppose that the number of typing errors she makes in every $10$ pages follows a Poisson distribution whose mean is <span class="text-nowrap">$\lambda=2$.</span>

<ol class="topic-list-paren">
  <li>What is the probability that no typing error at all appears on a single page selected at random?</li>
  <li>What is the probability that a total of $4$ typing errors appear on two pages?</li>
</ol>
</div>

(1) 令 $X$ 表示 Ellen 在一頁內打錯的字數，則由題意可知
{: .topic-paren-item}

$$
X\sim\mathrm{Poi}\Bigl(\lambda=\frac{2}{\,10\,}=0.2\Bigr)
$$

所求為
{: .topic-paren-cont}

$$
\mathbb{P}(X=0)=\frac{\,e^{-0.2}(0.2)^{0}\,}{0!}\fallingdotseq0.8187
$$

(2) 令 $Y$ 表示 Ellen 在兩頁內總共打錯的字數，則由題意可知
{: .topic-paren-item}

$$
Y\sim\mathrm{Poi}\Bigl(\lambda=\frac{2}{\,10\,}\times2=0.4\Bigr)
$$

所求為
{: .topic-paren-cont}

$$
\mathbb{P}(Y=4)=\frac{\,e^{-0.4}(0.4)^{4}\,}{4!}\fallingdotseq0.0007
$$

</div>

<div id="ex-poisson-sum-5" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.25</div>

<div lang="en" markdown="1">
Bacteria of a certain kind are known to occur in water at a rate of three bacteria per cubic centimeter of water. Suppose that this phenomenon obeys the Poisson probability law, and that a sample of two cubic centimeters of water is taken.

<ol class="topic-list-paren">
  <li>Find the probability that the sample contains at most two bacteria.</li>
  <li>Find the probability that the sample contains at least three bacteria.</li>
</ol>
</div>

(1) 依題意可令 $X$ 表兩立方公分的水中細菌的數量，則
{: .topic-paren-item}

$$
X\sim\mathrm{Poi}(\lambda=6)
$$

所求為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X\leqslant2)=\frac{\,e^{-6}6^{0}\,}{0!}+\frac{\,e^{-6}6^{1}\,}{1!}+\frac{\,e^{-6}6^{2}\,}{2!}=25e^{-6}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X\leqslant2)&=\frac{\,e^{-6}6^{0}\,}{0!}+\frac{\,e^{-6}6^{1}\,}{1!}\\[0.25em]
&\qquad +\frac{\,e^{-6}6^{2}\,}{2!}\\[0.4em]
&=25e^{-6}
\end{aligned}
$$

</div>

(2) 所求為
{: .topic-paren-item}

$$
\mathbb{P}(X\geqslant3)=1-\mathbb{P}(X\leqslant2)=1-25e^{-6}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

上述的兩個問題，是應用在非時間區段的例子，我們曾在[上一篇](/teaching-topics/poisson-process-and-distribution/)中提到，卜瓦松過程可以推廣至任意的區間，包含任意線段、平面、空間等等的區間，這當然導致了其上的卜瓦松分配被定義在非時間區段上，但使用的邏輯與定義在時間區段上的卜瓦松分配是完全相同的。

</div>

## 本篇小結

[Example 4.21](#ex-poisson-sum-1) 與 [Example 4.3 <span lang="en">(Continued)</span>](#ex-binomial-2-continued) 是卜瓦松機率的兩種基本用法。前者把每半小時平均巡視一次直接當成 <span class="text-nowrap">$\lambda=1$，</span>三個小題依序求 <span class="text-nowrap">$\mathbb{P}(Y=0)$、</span>$\mathbb{P}(Y=1)$ 與 $\mathbb{P}(Y\geqslant1)$ 這三個機率，最後一項以餘事件計算。後者承接[上一篇](/teaching-topics/poisson-process-and-distribution/)所證的二項分配卜瓦松近似: $n=200$ 很大、$p=0.03$ 很小而 <span class="text-nowrap">$np=6$，</span>以 $\mathrm{Poi}(6)$ 求得的 $0.1377$ 與二項分配的精確值 $0.1398$ 相當接近。

[Theorem 4.10](#thm-poisson-sum-conditional) 給出兩個獨立卜瓦松變數相加之後的兩件事。第一件是可加性，證明只需把兩個動差母函數相乘，指數上的 $\lambda_1$ 與 $\lambda_2$ 因而相加，再由[動差母函數的唯一性](/teaching-topics/uniqueness-of-the-mgf/#thm-mgf-uniqueness)辨識出 $\mathrm{Poi}(\lambda_1+\lambda_2)$ 這個分配。第二件是在總和固定為 $n$ 的條件下，$X$ 的條件分配為二項分配，成功機率是 $\frac{\lambda_1}{\,\lambda_1+\lambda_2\,}$ 這個比值；證明把條件機率函數的分子寫成兩個機率函數的乘積、分母寫成和的機率函數，指數項相消之後剩下的正是二項分配的形式。[Example 4.22](#ex-poisson-sum-2) 把同一組推導在參數為 $m$ 與 $n$ 而總和固定為 $50$ 的情形下再作一次。

[Theorem 4.11](#thm-poisson-thinning) 處理的是相反的方向: 先有一個服從 $\mathrm{Poi}(\lambda)$ 的變數 <span class="text-nowrap">$X$，</span>再在給定 $X=x$ 之下讓 $Y$ 服從 <span class="text-nowrap">$\mathrm{Bin}(x,p)$，</span>也就是把 $X$ 所計數的每一次發生各以機率 $p$ 歸入 $Y$ 這一類。證明先由條件機率函數與邊際機率函數相乘得到聯合機率函數，再取 $U=Y$ 與 $V=X-Y$ 這組轉換，聯合機率函數隨即分解成 $\mathrm{Poi}(\lambda p)$ 與 $\mathrm{Poi}\bigl(\lambda(1-p)\bigr)$ 兩個機率函數的乘積；分解一旦完成，三個結論同時成立，兩類的個數各自服從卜瓦松分配，而且彼此獨立。[Example 4.23](#ex-poisson-sum-3) 的第一小題由條件期望值與條件變異數求出 $\mathbb{E}(Y)=p\lambda$ 與 <span class="text-nowrap">$\mathrm{Var}(Y)=p\lambda$，</span>與 $Y\sim\mathrm{Poi}(\lambda p)$ 的期望值、變異數一致；第二小題則是 [Theorem 4.11](#thm-poisson-thinning) 第三項的完整重述。

最後兩道例題把卜瓦松分配用在非時間的區段上: [Example 4.24](#ex-poisson-sum-4) 以頁數為區段，每 $10$ 頁平均打錯 $2$ 個字，一頁的平均錯字數因而是 <span class="text-nowrap">$0.2$、</span>兩頁是 <span class="text-nowrap">$0.4$；</span>[Example 4.25](#ex-poisson-sum-5) 以體積為區段，每立方公分平均有 $3$ 隻細菌，兩立方公分因而是 <span class="text-nowrap">$\lambda=6$。</span>兩題都直接套用比例伸縮性質，計算的邏輯與定義在時間區段上的卜瓦松分配完全相同。

[下一篇](/teaching-topics/gamma-function-exponential-distribution/)由伽瑪函數談起，接著給出卜瓦松過程下轄的第二個分配，也就是描述偶發事件發生間隔的指數分配。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
