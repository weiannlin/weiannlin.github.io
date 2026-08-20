---
title: "動差母函數的唯一性"
subtitle: "Uniqueness of the Moment Generating Function"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 16
order: 216
permalink: /lecture-notes/uniqueness-of-the-mgf/
date: 2026-08-06
published: true
excerpt: "動差母函數的唯一性指出: 兩個隨機變數的 mgf 若存在且相等，則兩者的 pdf (或 pmf) 也會相等。有了這一項性質，只要把各階動差所組成的級數求和，得到一個認得出來的 mgf，就能反過來指出原本的分配是哪一個: 各階原動差皆為 $0.8$ 的是伯努利分配，偶階動差為 $\\frac{(2m)!}{2^{m}m!}$ 而奇階動差為 $0$ 的是標準常態分配。離散型的 mgf 還可以展開成 $p_{1}e^{a_{1}t}+\\cdots+p_{n}e^{a_{n}t}$，由各項的係數與指數直接還原 pmf。"
---

[上一篇](/lecture-notes/moment-generating-functions/)給了[動差母函數](/lecture-notes/moment-generating-functions/#def-mgf)的定義，說明它如何以微分生成各階原動差，也給了它的動差級數展開；三道例題或由已知的分配求出 mgf，或由已知的 mgf 求出動差與[變異數](/lecture-notes/variance/#def-variance)。

本篇處理的是另一個方向的問題。手上先有各階動差，把它們所組成的級數求和之後得到一個 mgf，再由這個 mgf 指出原本的分配是哪一個。這個作法的依據是動差母函數的唯一性。以下先以兩道例題示範如何由各階動差求得 mgf，其中第二題已先用到唯一性；接著給出唯一性定理，再以兩道例題由 mgf 指出所對應的分配；最後說明離散型的 mgf 如何直接還原成 pmf。

<div id="ex-constant-moments-mgf" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.32</div>

<div lang="en" markdown="1">
Suppose that the moments of a random variable $X$ are given by

$$
\mathbb{E}(X^{k})=0.8,\quad k=1,2,3,\ldots
$$

<ol class="topic-list-paren">
  <li>Find the moment generating function of $X$.</li>
</ol>
</div>

(1) 題目並未給 $\mathbb{E}(X^{0})$ 之值，但我們知道對任意的 $X$，我們有 $\mathbb{E}(X^{0})=\mathbb{E}(1)=1$，則
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{\sssig X}(t)&=\sum_{k=0}^{\infty}\mathbb{E}(X^{k})\,\frac{t^{k}}{k!}=1+\sum_{k=1}^{\infty}0.8\times\frac{t^{k}}{k!}\\[0.45em]
&=1+0.8\times\sum_{k=1}^{\infty}\frac{t^{k}}{k!}=1+0.8\,(e^{t}-1)\\[0.45em]
&=0.2+0.8e^{t},\quad t\in\mathbb{R}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig X}(t)&=\sum_{k=0}^{\infty}\mathbb{E}(X^{k})\,\frac{t^{k}}{k!}\\[0.45em]
&=1+\sum_{k=1}^{\infty}0.8\times\frac{t^{k}}{k!}\\[0.45em]
&=1+0.8\times\sum_{k=1}^{\infty}\frac{t^{k}}{k!}\\[0.45em]
&=1+0.8\,(e^{t}-1)\\[0.45em]
&=0.2+0.8e^{t},\quad t\in\mathbb{R}
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

上述問題中使用了一個很有名，且很常被使用的泰勒級數，即指數函數 $e^{t}$ 對 $t=0$ 展開的泰勒級數；在對函數自變數為 $0$ 的點所展開的泰勒級數，又被稱作**馬克勞林級數 <span lang="en">(Maclaurin series)</span>**。由於 $g(t)=e^{t}$ 是一個對 $t$ 無限可微的函數，而不論對其微分了幾次都不會改變該函數的樣子，也就是 $g^{(k)}(0)=e^{0}=1$，$k=0,1,2,\ldots$，所以其對 $t=0$ 的泰勒級數為

$$
e^{t}=\sum_{k=0}^{\infty}g^{(k)}(0)\,\frac{t^{k}}{k!}=\sum_{k=0}^{\infty}\frac{t^{k}}{k!}
$$

</div>

<div id="ex-normal-moments-to-pdf" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.33</div>

<div lang="en" markdown="1">
Suppose that a random variable $X$ has

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(X^{2m})=\frac{(2m)!}{2^{m}\,m!}\quad\text{and}\quad\mathbb{E}(X^{2m-1})=0,\quad m=1,2,3,\ldots
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}(X^{2m})=\frac{(2m)!}{2^{m}\,m!}\\[0.45em]
\text{and}\quad&\mathbb{E}(X^{2m-1})=0,\quad m=1,2,3,\ldots
\end{aligned}
$$

</div>

Determine the mgf of $X$ and the pdf of $X$.
</div>

由 [Theorem 2.22](/lecture-notes/moment-generating-functions/#thm-mgf-moment-series) 可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{\sssig X}(t)&=\mathbb{E}\bigl(e^{tX}\bigr)=\sum_{r=0}^{\infty}\mathbb{E}(X^{r})\,\frac{t^{r}}{r!}\\[0.45em]
&=1+\sum_{m=1}^{\infty}\mathbb{E}(X^{2m-1})\,\frac{t^{2m-1}}{(2m-1)!}+\sum_{n=1}^{\infty}\mathbb{E}(X^{2n})\,\frac{t^{2n}}{(2n)!}\\[0.45em]
&=1+\sum_{n=1}^{\infty}\frac{(2n)!}{2^{n}\,n!}\cdot\frac{t^{2n}}{(2n)!}=\sum_{n=0}^{\infty}\frac{(2n)!}{2^{n}\,n!}\cdot\frac{t^{2n}}{(2n)!}\\[0.45em]
&=\sum_{n=0}^{\infty}\frac{1}{n!}\left(\frac{t^{2}}{2}\right)^{n}=e^{\frac{t^{2}}{2}},\quad t\in\mathbb{R}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig X}&(t)=\mathbb{E}\bigl(e^{tX}\bigr)=\sum_{r=0}^{\infty}\mathbb{E}(X^{r})\,\frac{t^{r}}{r!}\\[0.45em]
&=1+\sum_{m=1}^{\infty}\mathbb{E}(X^{2m-1})\,\frac{t^{2m-1}}{(2m-1)!}\\[0.2em]
&\qquad +\sum_{n=1}^{\infty}\mathbb{E}(X^{2n})\,\frac{t^{2n}}{(2n)!}\\[0.45em]
&=1+\sum_{n=1}^{\infty}\frac{(2n)!}{2^{n}\,n!}\cdot\frac{t^{2n}}{(2n)!}\\[0.45em]
&=\sum_{n=0}^{\infty}\frac{(2n)!}{2^{n}\,n!}\cdot\frac{t^{2n}}{(2n)!}\\[0.45em]
&=\sum_{n=0}^{\infty}\frac{1}{n!}\left(\frac{t^{2}}{2}\right)^{n}\\[0.45em]
&=e^{\frac{t^{2}}{2}},\quad t\in\mathbb{R}
\end{aligned}
$$

</div>

由[動差母函數的唯一性](#thm-mgf-uniqueness)可知

$$
X\sim\mathcal{N}(0,1)
$$

故 pdf 為

$$
f_{\sssig X}(x)=\frac{1}{\,\sqrt{2\pi}\,}\,e^{-\frac{1}{2}x^{2}},\quad x\in\mathbb{R}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

上面這題中，我們之所以能直接由 mgf 看出該分配的 pdf，是使用了[下面這個定理](#thm-mgf-uniqueness)，事實上，這也是動差母函數在被創立之後，意外被發現的、比生成動差更有用的功能。

</div>

<div id="thm-mgf-uniqueness" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.23 (動差母函數的唯一性, uniqueness of mgf)</div>

若 $X, Y$ 為二[隨機變數](/lecture-notes/random-variables-and-pmf/#def-random-variable)，且二者之動差母函數 $M\_{\sssig X}(t), M\_{\sssig Y}(t)$ 存在且相等，若且唯若二者之 pdf (或 pmf) 亦會相等，即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
M_{\sssig X}(t)=M_{\sssig Y}(t)\Longleftrightarrow{}f_{\sssig X}(s)=f_{\sssig Y}(s)\quad\text{(或 }p_{\sssig X}(s)=p_{\sssig Y}(s)\text{)}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig X}(t)=M_{\sssig Y}(t)\Longleftrightarrow{}&f_{\sssig X}(s)=f_{\sssig Y}(s)\\[0.45em]
&\text{(或 }p_{\sssig X}(s)=p_{\sssig Y}(s)\text{)}
\end{aligned}
$$

</div>

</div>

<div class="topic-proof" markdown="1">
**Proof.**

見 Billingsley (1995)，*Probability and Measure*，3rd ed.，頁 388 至 390。 <span class="topic-qed">$\square$</span>
</div>

<div id="ex-constant-moments-bernoulli" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.32 <span lang="en">(Continued)</span></div>

<div lang="en" markdown="1">
Suppose that the moments of a random variable $X$ are given by

$$
\mathbb{E}(X^{k})=0.8,\quad k=1,2,3,\ldots
$$

<ol class="topic-list-paren topic-list-paren--start-2">
  <li>Determine the probability distribution of $X$.</li>
</ol>
</div>

(2) 由[第 (1) 小題](#ex-constant-moments-mgf)已求得
{: .topic-paren-item}

$$
M_{\sssig X}(t)=0.2+0.8e^{t},\quad t\in\mathbb{R}
$$

由[動差母函數的唯一性](#thm-mgf-uniqueness)得知
{: .topic-paren-cont}

$$
X\sim\mathrm{Ber}(p=0.8)
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

[Example 2.32 <span lang="en">(Continued)</span>](#ex-constant-moments-bernoulli) 為**伯努利分配 <span lang="en">(Bernoulli distribution)</span>**，是**成敗實驗族**中的核心分配之一，我們在後面，將介紹這些常用的機率模型，並且介紹其動差母函數以便辨認。

</div>

<div id="ex-factorial-moments-to-mgf" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.34</div>

<div lang="en" markdown="1">
Suppose that a random variable $X$ satisfies

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(X^{m})=(m+1)!\,2^{m},\quad m=1,2,3,\ldots
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X^{m})&=(m+1)!\,2^{m}, m=1,2,3,\ldots
\end{aligned}
$$

</div>

Find the mgf of $X$ and the distribution of $X$.
</div>

由 [Theorem 2.22](/lecture-notes/moment-generating-functions/#thm-mgf-moment-series) 可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
&M_{\sssig X}(t)=\mathbb{E}\bigl(e^{tX}\bigr)=\sum_{r=0}^{\infty}\mathbb{E}(X^{r})\,\frac{t^{r}}{r!}=1+\sum_{m=1}^{\infty}\mathbb{E}(X^{m})\,\frac{t^{m}}{m!}\\[0.45em]
&=1+\sum_{m=1}^{\infty}\frac{(m+1)!\,(2t)^{m}}{m!}=\sum_{m=0}^{\infty}\frac{(m+1)!\,(2t)^{m}}{m!}\\[0.45em]
&=\sum_{m=0}^{\infty}\left.\left(\frac{d}{\,du\,}\,u^{m+1}\right)\right\rvert_{u=2t}=\left.\frac{d}{\,du\,}\left(\sum_{m=0}^{\infty}u^{m+1}\right)\right\rvert_{u=2t}\\[0.45em]
&=\left.\frac{d}{\,du\,}\left(\frac{u}{\,1-u\,}\right)\right\rvert_{u=2t}=\left.\frac{1}{\,(1-u)^{2}\,}\right\rvert_{u=2t}\\[0.45em]
&=(1-2t)^{-2},\quad\lvert2t\rvert<1\Longleftrightarrow-\frac{1}{\,2\,}<t<\frac{1}{\,2\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig X}(t)&=\mathbb{E}\bigl(e^{tX}\bigr)=\sum_{r=0}^{\infty}\mathbb{E}(X^{r})\,\frac{t^{r}}{r!}\\[0.45em]
&=1+\sum_{m=1}^{\infty}\mathbb{E}(X^{m})\,\frac{t^{m}}{m!}\\[0.45em]
&=1+\sum_{m=1}^{\infty}\frac{(m+1)!\,(2t)^{m}}{m!}\\[0.45em]
&=\sum_{m=0}^{\infty}\frac{(m+1)!\,(2t)^{m}}{m!}\\[0.45em]
&=\sum_{m=0}^{\infty}\left.\left(\frac{d}{\,du\,}\,u^{m+1}\right)\right\rvert_{u=2t}\\[0.45em]
&=\left.\frac{d}{\,du\,}\left(\sum_{m=0}^{\infty}u^{m+1}\right)\right\rvert_{u=2t}\\[0.45em]
&=\left.\frac{d}{\,du\,}\left(\frac{u}{\,1-u\,}\right)\right\rvert_{u=2t}\\[0.45em]
&=\left.\frac{1}{\,(1-u)^{2}\,}\right\rvert_{u=2t}=(1-2t)^{-2},\\[0.45em]
&\qquad \lvert2t\rvert<1\Longleftrightarrow-\frac{1}{\,2\,}<t<\frac{1}{\,2\,}
\end{aligned}
$$

</div>

由[動差母函數的唯一性](#thm-mgf-uniqueness)可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
X\sim\mathrm{Gamma}(\alpha=2,\beta=2)\quad\text{即}\quad X\sim\chi^{2}(4)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
X&\sim\mathrm{Gamma}(\alpha=2,\beta=2)\\[0.45em]
\text{即}\quad X&\sim\chi^{2}(4)
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

我們在 [Example 2.3 <span lang="en">(Continued)</span>](/lecture-notes/expectation/#ex-geometric-expectation) 中有用過一樣的技巧，即改變加總與微分的順序，讓我們能夠運用幾何級數。

此處的分配是伽瑪分配 <span lang="en">(gamma distribution)</span>，利用 [mgf 的唯一性](#thm-mgf-uniqueness)可以輕鬆判斷，但值得注意的是，這個分配同時也是卡方分配 <span lang="en">(chi-square distribution)</span>，在後面的機率模型章節中，我們會詳述這些關係。

</div>

由於 mgf 的定義，在離散型分配上是採用加總的方式，即

$$
M_{\sssig X}(t)=\sum_{x\in\mathcal{R}_{\sssig X}}e^{tx}\,p_{\sssig X}(x)
$$

故我們其實可以將 $X$ 的動差母函數展開成下面的形式

$$
p_{\sssig 1}e^{a_{1}\,t}+p_{\sssig 2}e^{a_{2}\,t}+\cdots+p_{\sssig n}e^{a_{n}\,t}
$$

若未來我們看見如前述形式的 mgf，則我們可以馬上轉化為其原本的離散分配，也就是下面的對應

$$
p_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
p_{\sssig 1}, & x=a_{1}\\[0.4em]
\vdots & \quad\vdots\\[0.4em]
p_{\sssig n}, & x=a_{n}
\end{array}
\right.
$$

譬如 [Example 2.30](/lecture-notes/moment-generating-functions/#ex-discrete-mgf-variance) 的 mgf 為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
M_{\sssig X}(t)=\frac{1}{5}\,e^{1\,t}+\frac{2}{5}\,e^{4\,t}+\frac{2}{5}\,e^{8\,t},\quad t\in\mathbb{R}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig X}(t)&=\frac{1}{5}\,e^{1\,t}+\frac{2}{5}\,e^{4\,t}+\frac{2}{5}\,e^{8\,t}, ~t\in\mathbb{R}
\end{aligned}
$$

</div>

其原本的 pmf 即為

$$
p_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{1}{5}, & x=1\\[0.7em]
\dfrac{2}{5}, & x=4\ \text{或}\ 8
\end{array}
\right.
$$

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

當然，[動差母函數的唯一性](#thm-mgf-uniqueness)，在連續分配並不能這樣使用，我們在機率模型的章節中，介紹常見機率模型時，便會看見許多連續型的例子。

</div>

## 本篇小結

[Theorem 2.23](#thm-mgf-uniqueness) 使 mgf 不只能生成動差，還能用來辨認分配。只要把手上各階動差所組成的級數求和，得到一個認得出來的 mgf，原本的分配是哪一個也就跟著確定了。本篇的例題正是這樣做的，[Example 2.32](#ex-constant-moments-mgf) 由各階原動差皆為 $0.8$ 求得 $M_{\sssig X}(t)=0.2+0.8e^{t}$，[Example 2.32 <span lang="en">(Continued)</span>](#ex-constant-moments-bernoulli) 再由這個 mgf 得知 $X$ 為伯努利分配；[Example 2.33](#ex-normal-moments-to-pdf) 由偶階與奇階動差求得 $M_{\sssig X}(t)=e^{t^{2}/2}$，因而得知 $X$ 為標準常態分配；[Example 2.34](#ex-factorial-moments-to-mgf) 則以改變加總與微分順序的技巧求得 $M_{\sssig X}(t)=(1-2t)^{-2}$，因而得知 $X$ 為伽瑪分配，也就是自由度為 $4$ 的卡方分配。

離散型的 mgf 還有一項更直接的用法。這一型的 mgf 可以展開成 $p_{\sssig 1}e^{a_{1}t}+\cdots+p_{\sssig n}e^{a_{n}t}$，各項的指數 $a_{i}$ 就是 $X$ 的各個取值，係數 $p_{\sssig i}$ 就是各個取值的機率，因此看見這種形式的 mgf 便能立刻寫出它的 pmf；連續型的 mgf 沒有這種對應，要由 mgf 認出連續型的分配，仍須回到各個常見機率模型的 mgf 逐一比對。動差母函數之外，還有其他的母函數各自生成不同的量，[下一篇](/lecture-notes/probability-cumulant-generating-functions/)就要介紹生成機率的[機率母函數](/lecture-notes/probability-cumulant-generating-functions/#def-pgf)，以及生成累積量的[累積量母函數](/lecture-notes/probability-cumulant-generating-functions/#def-cgf)。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Patrick Billingsley. 1995. *Probability and Measure*. 3rd ed. Wiley.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- J. H. Curtiss. 1942. “A Note on the Theory of Moment Generating Functions.” *The Annals of Mathematical Statistics* 13 (4): 430–433.
