---
title: "r 次均方收斂與幾乎確信收斂"
subtitle: "Convergence in r-th Mean and Almost Sure Convergence"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 5
topic: 4
order: 504
permalink: /lecture-notes/convergence-in-mean-and-almost-sure/
date: 2026-08-15
published: false
excerpt: "$r$ 次均方收斂要求 $\\mathbb{E}\\bigl[\\lvert X_n-X\\rvert^{r}\\bigr]$ 在 $n\\to\\infty$ 時趨於零，幾乎確信收斂則要求那些不收斂的樣本點所構成的例外集合，其發生機率必須是零。本篇先給出這兩個定義，再以馬可夫不等式證明 $r$ 次均方收斂導致機率收斂，並由此推得只要期望值收斂至常數 $c$ 且變異數趨於零，序列就二次均方收斂至 $c$，這正是數理統計中均方一致性的由來。例題方面，取值為 $0$ 與 $n$ 而機率分別為 $1-\\frac{1}{n}$ 與 $\\frac{1}{n}$ 的序列機率收斂至零卻不一次均方收斂；逐段指標序列機率收斂卻不幾乎確信收斂；把機率改為 $\\frac{1}{n^{2}}$ 或把取值改為 $1$ 之後，兩種收斂又各自一成一敗，可見這兩個收斂型態之間並沒有強弱關係。"
---

[上一篇](/lecture-notes/convergence-in-probability/)給出[機率收斂](/lecture-notes/convergence-in-probability/#def-converge-in-probability)的定義，並說明它與[分配收斂](/lecture-notes/convergence-in-distribution/#def-converge-in-distribution)之間的強弱關係。本篇接著給出另外兩種收斂型態: [Definition 5.3](#def-converge-in-r-mean) 的 $r$ 次均方收斂以「距離的 $r$ 次方的期望值是否趨於零」來界定，[Definition 5.4](#def-converge-almost-surely) 的幾乎確信收斂則轉而探討那些不收斂的樣本點所構成的例外集合，要求這個集合的發生機率必須是零。

這兩種收斂都比機率收斂強。[Theorem 5.4](#thm-rconv-implies-pconv) 由[馬可夫不等式](/lecture-notes/probability-inequalities/#thm-markov)證明 $r$ 次均方收斂導致機率收斂，[Theorem 5.5](#thm-2conv-implies-pconv) 再把這件事用在二次均方收斂上，給出一條只要檢查期望值與變異數就能判定機率收斂的判準；[Theorem 5.6](#thm-asconv-implies-pconv) 則交代幾乎確信收斂同樣導致機率收斂。四道例題分別說明機率收斂不足以保證一次均方收斂、二次均方收斂如何用來求機率極限、機率收斂不足以保證幾乎確信收斂，以及 $r$ 次均方收斂與幾乎確信收斂之間並沒有互相導致的關係。

## $r$ 次均方收斂

<div id="def-converge-in-r-mean" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 5.3 ($r$ 次均方收斂, converge in $r$-th mean)</div>

令 $\lbrace X_n\rbrace_{n=1}^{\infty}$ 為一定義在機率空間上之隨機變數序列，且 <span class="text-nowrap">$\mathbb{E}\bigl[\lvert X_n\rvert^{r}\bigr]<\infty$，</span>若 $X$ 為一隨機變數，且滿足

$$
\lim_{n\to\infty}\mathbb{E}\bigl[\lvert X_n-X\rvert^{r}\bigr]=0,\ r>0
$$

則稱 $X_n$ $r$ 次均方收斂至 <span class="text-nowrap">$X$，</span>記為

$$
X_n\rconv X
$$

</div>

$r$ 次均方收斂是以「隨機變數值之間距離 $r$ 次方的期望值」來定義的，這是一種不同於機率收斂與分配收斂的另一種型態的收斂型態。此外，$r$ 次均方收斂是一個比機率收斂還要強的收斂性質。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這種收斂型態，有一個比較簡單的思考方式是指，這些 $X_n$ 與 $X$ 間距離的 $r$ 次方「平均來說是 $0$」。

讀者應該特別注意的是，我們並不是要求 $X_n$ 與 $X$ 間距離永遠都是 <span class="text-nowrap">$0$，</span>但是由於距離是非負的，要使得期望值為 $0$ 的話，在那些距離不為 $0$ 的地方，機率 (或機率密度) 必須要能夠將其距離「抵銷」為 <span class="text-nowrap">$0$，</span>[^offset] 才能夠使得期望值為 $0$。

這個「抵銷」的概念正是 $r$ 次均方收斂比機率收斂要強的地方，因為機率收斂本身只要求距離大於等於某個正數 $\varepsilon$ 的地方，機率必須收斂至 <span class="text-nowrap">$0$，</span>但 $r$ 次均方收斂的機率卻還要負擔把 $\lvert X_n-X\rvert^{r}$ 給抵銷至 $0$ 的工作，因此其收斂至 $0$ 的程度要比機率收斂強多了，可見下列的定理與證明。

</div>

## $r$ 次均方收斂導致機率收斂

<div id="thm-rconv-implies-pconv" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 5.4 ($r$ 次均方收斂導致機率收斂, convergence in $r$-th mean implies convergence in probability)</div>

若 <span class="text-nowrap">$X_n\rconv X$，</span>則有

$$
X_n\pconv X
$$

反之未必成立。

</div>

<div class="topic-proof" markdown="1">
**Proof.**

由馬可夫不等式可知

$$
\mathbb{P}\bigl(\lvert X_n-X\rvert\geqslant\varepsilon\bigr)\leqslant\frac{\,\mathbb{E}\bigl[\lvert X_n-X\rvert^{r}\bigr]\,}{\varepsilon^{r}},\ \varepsilon>0
$$

又由 $r$ 次均方收斂的定義可知

$$
\lim_{n\to\infty}\mathbb{E}\bigl[\lvert X_n-X\rvert^{r}\bigr]=0
$$

故可知道，若 <span class="text-nowrap">$X_n\rconv X$，</span>則我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_n-X\rvert\geqslant\varepsilon\bigr)\leqslant\lim_{n\to\infty}\frac{\,\mathbb{E}\bigl[\lvert X_n-X\rvert^{r}\bigr]\,}{\varepsilon^{r}}=0,\ \varepsilon>0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_n-X\rvert\geqslant\varepsilon\bigr)&\leqslant\lim_{n\to\infty}\frac{\,\mathbb{E}\bigl[\lvert X_n-X\rvert^{r}\bigr]\,}{\varepsilon^{r}}\\[0.45em]
&=0,\ \varepsilon>0
\end{aligned}
$$

</div>

由此可得

$$
\Longrightarrow\ \lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_n-X\rvert<\varepsilon\bigr)=1,\ \varepsilon>0
$$

此即

$$
X_n\pconv X
$$

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div id="ex-pconv-without-first-mean" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.13</div>

<div lang="en" markdown="1">
Suppose that $X_1,X_2,\ldots$ are independent discrete random variables in which $X_n$ carries the pmf $f_n$ given by

$$
f_n(0)=1-\frac{1}{\,n\,},\quad f_n(n)=\frac{1}{\,n\,},\quad n=1,2,3,\ldots
$$

<ol class="topic-list-paren">
  <li>Show that $X_n$ converges to $0$ in probability.</li>
  <li>Find $\mathbb{E}(X_n)$ and <span class="text-nowrap">$\mathrm{Var}(X_n)$.</span></li>
  <li>Show that $X_n$ does not converge to $0$ in $r$-th mean when <span class="text-nowrap">$r=1$.</span></li>
</ol>
</div>

(1) 依題意可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}\bigl(\lvert X_n-0\rvert<\varepsilon\bigr)=\mathbb{P}(X_n=0)=1-\frac{1}{\,n\,},\ \varepsilon>0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}\bigl(\lvert X_n-0\rvert<\varepsilon\bigr)&=\mathbb{P}(X_n=0)\\[0.45em]
&=1-\frac{1}{\,n\,},\ \varepsilon>0
\end{aligned}
$$

</div>

由此可得
{: .topic-paren-cont}

$$
\Longrightarrow\ \lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_n-0\rvert<\varepsilon\bigr)=1,\ \forall\varepsilon>0
$$

此即
{: .topic-paren-cont}

$$
X_n\pconv0
$$

(2) 依題意可得
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\mathbb{E}(X_n)=0\times\Bigl(1-\frac{1}{\,n\,}\Bigr)+n\times\frac{1}{\,n\,}=1\\[0.55em]
\mathrm{Var}(X_n)=\mathbb{E}\bigl(X_n^{2}\bigr)-1^{2}=0^{2}\times\Bigl(1-\frac{1}{\,n\,}\Bigr)+n^{2}\times\frac{1}{\,n\,}-1=n-1
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X_n)&=0\times\Bigl(1-\frac{1}{\,n\,}\Bigr)+n\times\frac{1}{\,n\,}\\[0.45em]
&=1\\[0.55em]
\mathrm{Var}(X_n)&=\mathbb{E}\bigl(X_n^{2}\bigr)-1^{2}\\[0.45em]
&=0^{2}\times\Bigl(1-\frac{1}{\,n\,}\Bigr)\\[0.45em]
&\qquad+n^{2}\times\frac{1}{\,n\,}-1\\[0.45em]
&=n-1
\end{aligned}
$$

</div>

(3) 依題意可得
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\bigl[\lvert X_n-0\rvert\bigr]=\lvert0\rvert\times\Bigl(1-\frac{1}{\,n\,}\Bigr)+\lvert n\rvert\times\frac{1}{\,n\,}=1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[\lvert X_n-0\rvert\bigr]&=\lvert0\rvert\times\Bigl(1-\frac{1}{\,n\,}\Bigr)\\[0.45em]
&\qquad+\lvert n\rvert\times\frac{1}{\,n\,}\\[0.45em]
&=1
\end{aligned}
$$

</div>

故可知
{: .topic-paren-cont}

$$
\lim_{n\to\infty}\mathbb{E}\bigl[\lvert X_n-0\rvert\bigr]=1\neq0
$$

此即 $X_n$ 沒有 $1$ 次均方收斂至 $0$。
{: .topic-paren-cont}

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

上面這個問題能夠很直接地看出，儘管 $f_n(x)$ 在 $x\neq0$ 處的機率能夠收斂至 <span class="text-nowrap">$0$，</span>但是這個收斂的速度，並不足以將 $\lvert X_n-0\rvert$ 也一併抵銷至 <span class="text-nowrap">$0$，</span>因此雖然 <span class="text-nowrap">$X_n\pconv0$，</span>但卻沒有使得 $X_n$ $1$ 次均方收斂至 $0$。

當然，這個問題是經過刻意設計的，因為其在 $x\neq0$ 處的機率，隨著 $n$ 成長而收斂至 $0$ 的速度，恰巧與 $\lvert X_n-0\rvert$ 隨著 $n$ 成長的速度一樣快，因此無法抵銷；讀者可以試試看，將這個問題的機率分配改為

$$
f_n(0)=1-\frac{1}{\,n^{m}\,},\quad f_n(n)=\frac{1}{\,n^{m}\,}
$$

則此時將無法 $m$ 次均方收斂至 <span class="text-nowrap">$0$，</span>但對於 <span class="text-nowrap">$0<r<m$，</span>卻是可以 $r$ 次均方收斂至 $0$ 的。

</div>

## 二次均方收斂與均方一致性

在眾多的 $r$-次均方收斂中，有一種較為特別，就是 $2$-次均方收斂，見下列定理。

<div id="thm-2conv-implies-pconv" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 5.5 (期望值收斂且變異數趨零則二次均方收斂, convergence in second mean from the mean and the variance)</div>

令 $\lbrace X_n\rbrace_{n=1}^{\infty}$ 為一定義在機率空間上之隨機變數序列，且

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lim_{n\to\infty}\mathbb{E}(X_n)=c,\quad\lim_{n\to\infty}\mathrm{Var}(X_n)=0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\lim_{n\to\infty}\mathbb{E}(X_n)&=c,\\[0.45em]
\lim_{n\to\infty}\mathrm{Var}(X_n)&=0
\end{aligned}
$$

</div>

則可知

$$
X_n\xrightarrow{~~2~~}c
$$

並且

$$
X_n\pconv c
$$

其中 $c$ 為一個常數。

</div>

<div class="topic-proof" markdown="1">
**Proof.**

由於

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[\lvert X_n-c\rvert^{2}\bigr]&=\mathbb{E}\bigl[(X_n-c)^{2}\bigr]=\mathbb{E}\bigl[X_n^{2}-2cX_n+c^{2}\bigr]=\mathbb{E}\bigl(X_n^{2}\bigr)-2c\,\mathbb{E}(X_n)+c^{2}\\[0.45em]
&=\mathrm{Var}(X_n)+\bigl[\mathbb{E}(X_n)\bigr]^{2}-2c\,\mathbb{E}(X_n)+c^{2}=\mathrm{Var}(X_n)+\bigl[\mathbb{E}(X_n)-c\bigr]^{2}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[\lvert X_n-c\rvert^{2}\bigr]&=\mathbb{E}\bigl[(X_n-c)^{2}\bigr]\\[0.45em]
&=\mathbb{E}\bigl[X_n^{2}-2cX_n+c^{2}\bigr]\\[0.45em]
&=\mathbb{E}\bigl(X_n^{2}\bigr)-2c\,\mathbb{E}(X_n)+c^{2}\\[0.45em]
&=\mathrm{Var}(X_n)+\bigl[\mathbb{E}(X_n)\bigr]^{2}\\[0.45em]
&\qquad-2c\,\mathbb{E}(X_n)+c^{2}\\[0.45em]
&=\mathrm{Var}(X_n)+\bigl[\mathbb{E}(X_n)-c\bigr]^{2}
\end{aligned}
$$

</div>

若 <span class="text-nowrap">$\lim_{n\to\infty}\mathbb{E}(X_n)=c$，</span><span class="text-nowrap">$\lim_{n\to\infty}\mathrm{Var}(X_n)=0$，</span>則我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lim_{n\to\infty}\mathbb{E}\bigl[\lvert X_n-c\rvert^{2}\bigr]=\lim_{n\to\infty}\Bigl(\mathrm{Var}(X_n)+\bigl[\mathbb{E}(X_n)-c\bigr]^{2}\Bigr)=0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\lim_{n\to\infty}\mathbb{E}\bigl[\lvert X_n-c\rvert^{2}\bigr]&=\lim_{n\to\infty}\Bigl(\mathrm{Var}(X_n)\\[0.45em]
&\qquad+\bigl[\mathbb{E}(X_n)-c\bigr]^{2}\Bigr)\\[0.45em]
&=0
\end{aligned}
$$

</div>

此即

$$
X_n\xrightarrow{~~2~~}c
$$

又由 [Theorem 5.4](#thm-rconv-implies-pconv) 可知

$$
X_n\pconv c
$$

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個定理雖然只是 [Theorem 5.4](#thm-rconv-implies-pconv) 衍生而來的小定理，但是在使用上卻給了我們很大的方便，爾後我們只要確認一個序列的期望值為 <span class="text-nowrap">$c$，</span>並確認其變異數收斂至 <span class="text-nowrap">$0$，</span>則這個序列就直接能夠機率收斂至 <span class="text-nowrap">$c$，</span>在數理統計的環節中將看得到許多的好處。

事實上，在數理統計的章節中，我們會談到，二次均方收斂至母體參數 $\theta$ 的隨機序列，也稱其具有**均方一致性 <span lang="en">(mean square consistency)</span>** (也就是其平均平方誤差 <span lang="en">(mean square error, MSE)</span> 收斂至 $0$)，相較於一般的一致性 (<span lang="en">consistency</span>，或稱為**簡單一致性 <span lang="en">(simple consistency)</span>**) 是採用機率收斂的定義，具有均方一致性的序列一定具有一致性，但僅具有一致性的序列卻不一定具備均方一致性。

</div>

<div id="ex-s-squared-mean-square-consistency" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.10 ($S^{2}$ 的一致性, <span lang="en">Continued</span>)</div>

<div lang="en" markdown="1">
Suppose that <span class="text-nowrap">$X_1,\ldots,X_n\iidto\mathcal{N}(\mu,\sigma^{2})$,</span> and let $S^{2}=\frac{1}{\,n-1\,}\sum_{i=1}^{n}\bigl(X_i-\overline{X}\bigr)^{2}$ be the sample variance. Find the probability limit of <span class="text-nowrap">$S^{2}$.</span>
</div>

**[ 法二 ]**

由於

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
S^{2}\sim\mathrm{Gamma}\Bigl(\alpha=\frac{\,n-1\,}{2},\ \beta=\frac{2\sigma^{2}}{\,n-1\,}\Bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
S^{2}\sim\mathrm{Gamma}\Bigl(&\alpha=\frac{\,n-1\,}{2},\\[0.45em]
&\beta=\frac{2\sigma^{2}}{\,n-1\,}\Bigr)
\end{aligned}
$$

</div>

故可知

<div class="topic-math-follow-before" markdown="1">
<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\mathbb{E}\bigl(S^{2}\bigr)=\frac{\,n-1\,}{2}\times\frac{2\sigma^{2}}{\,n-1\,}=\sigma^{2}\\[0.55em]
\mathrm{Var}\bigl(S^{2}\bigr)=\frac{\,n-1\,}{2}\times\Bigl(\frac{2\sigma^{2}}{\,n-1\,}\Bigr)^{2}=\frac{2\sigma^{4}}{\,n-1\,}
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl(S^{2}\bigr)&=\frac{\,n-1\,}{2}\times\frac{2\sigma^{2}}{\,n-1\,}=\sigma^{2}\\[0.55em]
\mathrm{Var}\bigl(S^{2}\bigr)&=\frac{\,n-1\,}{2}\times\Bigl(\frac{2\sigma^{2}}{\,n-1\,}\Bigr)^{2}\\[0.45em]
&=\frac{2\sigma^{4}}{\,n-1\,}
\end{aligned}
$$

</div>
</div>
<div class="topic-math-follow" markdown="1">
<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\Longrightarrow\ \lim_{n\to\infty}\mathbb{E}\bigl(S^{2}\bigr)=\sigma^{2},\quad\lim_{n\to\infty}\mathrm{Var}\bigl(S^{2}\bigr)=0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ \lim_{n\to\infty}\mathbb{E}\bigl(S^{2}\bigr)&=\sigma^{2},\\[0.45em]
\lim_{n\to\infty}\mathrm{Var}\bigl(S^{2}\bigr)&=0
\end{aligned}
$$

</div>
</div>

則可知

$$
S^{2}\pconv\sigma^{2}
$$

</div>

## 幾乎確信收斂

<div id="def-converge-almost-surely" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 5.4 (幾乎確信收斂, converge almost surely)</div>

令 $\lbrace X_n\rbrace_{n=1}^{\infty}$ 為一定義在機率空間上之隨機變數序列，若 $X$ 為定義在相同機率空間中之隨機變數，且滿足

$$
\mathbb{P}\Bigl(\lim_{n\to\infty}\bigl\lvert X_n-X\bigr\rvert<\varepsilon\Bigr)=1,\ \forall\varepsilon>0
$$

則稱 $X_n$ 幾乎確信收斂至 <span class="text-nowrap">$X$，</span>記為

$$
X_n\asconv X
$$

</div>

幾乎確信收斂與機率收斂的概念非常容易被搞混，因為他們都是關於隨機變數值之間的收斂關係。但是，幾乎確信收斂更著重於探討那些不收斂的隨機變數值，其背後的樣本點所構成的集合，而機率收斂僅就機率的收斂上進行描述。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

此二個定義的不同之處在於，機率收斂允許 $X_n$ 和 $X$ 到處都「長得不一樣」 (或精確地說，距離不小於 <span class="text-nowrap">$\varepsilon>0$)，</span>只是這個「不一樣」發生的機率在 $n\to\infty$ 時，必須能隨著 $n$ 的成長而收斂至 $0$。[^pconv-tolerance]

另一方面，幾乎確信收斂的概念是，對於每一個位於樣本空間中的樣本點 <span class="text-nowrap">$\omega\in S$，</span>我們並不希望 $\lim_{n\to\infty}X_n(\omega)$ 與 $X(\omega)$ 長得不一樣，如果有這樣的 $\omega\in S$ 使得 $\lim_{n\to\infty}X_n(\omega)$ 與 $X(\omega)$ 的距離不小於 <span class="text-nowrap">$\varepsilon$，</span>那這樣的 $\omega$ 收集而成的「例外集合」，其發生機率必須是 $0$；相對於機率收斂允許這樣的集合機率不是 <span class="text-nowrap">$0$，</span>只是必須慢慢趨近於 $0$ 來說，是一個明顯比較強的收斂性質。

</div>

幾乎確信收斂也被稱為**強收斂 <span lang="en">(convergence strongly)</span>**、**以機率 $1$ 收斂 <span lang="en">(converge with probability 1)</span>**、**幾乎處處收斂 <span lang="en">(converge almost everywhere)</span>**。此外，上述定義有一個等價的定義如下:

$$
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_k-X\rvert<\varepsilon,\ \forall k\geqslant n\bigr)=1,\ \forall\varepsilon>0
$$

## 幾乎確信收斂導致機率收斂

<div id="thm-asconv-implies-pconv" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 5.6 (幾乎確信收斂導致機率收斂, almost sure convergence implies convergence in probability)</div>

若 <span class="text-nowrap">$X_n\asconv X$，</span>則有

$$
X_n\pconv X
$$

反之未必成立。

</div>

<div class="topic-proof" markdown="1">
**Proof.**

取任意的 $\varepsilon>0$，並令

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
A_n=\lbrace\lvert X_k-X\rvert<\varepsilon,\ \forall k\geqslant n\rbrace=\bigcap_{k=n}^{\infty}\lbrace\lvert X_k-X\rvert<\varepsilon\rbrace
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
A_n&=\lbrace\lvert X_k-X\rvert<\varepsilon,\ \forall k\geqslant n\rbrace\\[0.45em]
&=\bigcap_{k=n}^{\infty}\lbrace\lvert X_k-X\rvert<\varepsilon\rbrace
\end{aligned}
$$

</div>

則由 [Definition 5.4](#def-converge-almost-surely) 之後所列的那一個等價敘述可知

$$
\lim_{n\to\infty}\mathbb{P}(A_n)=1
$$

另一方面，$A_n$ 要求 $k\geqslant n$ 的每一項都與 $X$ 相差不到 $\varepsilon$，其中 $k=n$ 這一項本身即為 $\lbrace\lvert X_n-X\rvert<\varepsilon\rbrace$，故

$$
A_n\subseteq\lbrace\lvert X_n-X\rvert<\varepsilon\rbrace
$$

由 [Theorem 1.7](/lecture-notes/probability-rules-from-axioms/#theorem-monotonicity) 的單調性可得

$$
\mathbb{P}(A_n)\leqslant\mathbb{P}\bigl(\lvert X_n-X\rvert<\varepsilon\bigr)\leqslant1
$$

令 $n\to\infty$，上式最左側趨於 $1$、最右側恆為 $1$，夾在中間的機率因而也必須趨於 $1$，也就是

$$
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_n-X\rvert<\varepsilon\bigr)=1,\ \forall\varepsilon>0
$$

此即

$$
X_n\pconv X
$$

至於反向的敘述並不成立，[Example 5.14](#ex-indicator-block-sequence) 即給出一個機率收斂而不幾乎確信收斂的序列。原式得證。 <span class="topic-qed">$\square$</span>
</div>

本證明只用到 Definition 5.4 之後所列的等價敘述與機率的單調性；Chung (2001) 第 70 頁另有一套證明。

<div id="ex-indicator-block-sequence" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.14</div>

<div lang="en" markdown="1">
Suppose that <span class="text-nowrap">$X\sim\mathcal{U}(0,1)$,</span> and let the sequence $X_1,X_2,\ldots$ be built from $X$ by

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
&X_1=X+\mathbb{I}_{[0,1]}(X), &&X_2=X+\mathbb{I}_{[0,\frac{1}{2}]}(X), &&X_3=X+\mathbb{I}_{[\frac{1}{2},1]}(X),\\[0.45em]
&X_4=X+\mathbb{I}_{[0,\frac{1}{3}]}(X), &&X_5=X+\mathbb{I}_{[\frac{1}{3},\frac{2}{3}]}(X), &&X_6=X+\mathbb{I}_{[\frac{2}{3},1]}(X),\ \ldots
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
X_1&=X+\mathbb{I}_{[0,1]}(X),\\[0.45em]
X_2&=X+\mathbb{I}_{[0,\frac{1}{2}]}(X),\\[0.45em]
X_3&=X+\mathbb{I}_{[\frac{1}{2},1]}(X),\\[0.45em]
X_4&=X+\mathbb{I}_{[0,\frac{1}{3}]}(X),\\[0.45em]
X_5&=X+\mathbb{I}_{[\frac{1}{3},\frac{2}{3}]}(X),\\[0.45em]
X_6&=X+\mathbb{I}_{[\frac{2}{3},1]}(X),\ \ldots
\end{aligned}
$$

</div>

Show that this sequence converges to $X$ in probability, yet it fails to converge to $X$ almost surely.[^casella-source]
</div>

事實上，題目之設定可以改寫為

$$
X_n=X+\mathbb{I}_{[\frac{k-1}{m},\frac{k}{m}]}(X)
$$

其中 $m=1,2,3,\ldots,$ 而 <span class="text-nowrap">$k=1,2,\ldots,m$，</span>且

$$
n=\Bigl[\sum_{t=0}^{m-1}t\Bigr]+k
$$

則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}\bigl(\lvert X_n-X\rvert\geqslant\varepsilon\bigr)=\mathbb{P}\bigl(\mathbb{I}_{[\frac{k-1}{m},\frac{k}{m}]}(X)=1\bigr)=\mathbb{P}\Bigl(X\in\Bigl[\frac{k-1}{m},\frac{k}{m}\Bigr]\Bigr)=\frac{1}{\,m\,},\ m=1,2,3,\ldots
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}\bigl(\lvert X_n-X\rvert\geqslant\varepsilon\bigr)&=\mathbb{P}\bigl(\mathbb{I}_{[\frac{k-1}{m},\frac{k}{m}]}(X)=1\bigr)\\[0.45em]
&=\mathbb{P}\Bigl(X\in\Bigl[\frac{k-1}{m},\frac{k}{m}\Bigr]\Bigr)\\[0.45em]
&=\frac{1}{\,m\,},\ m=1,2,3,\ldots
\end{aligned}
$$

</div>

當 <span class="text-nowrap">$n\to\infty$，</span>此時 $m$ 也將趨近無窮大，故可知

$$
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_n-X\rvert\geqslant\varepsilon\bigr)=\lim_{m\to\infty}\frac{1}{\,m\,}=0
$$

此即

$$
X_n\pconv X
$$

又依題目之定義可知，$\lim_{n\to\infty}X_n$ 並不存在，舉例而言，當 $X=\frac{3}{\,8\,}$ 時 $X_n,\ n=1,2,\ldots$ 之值並不會是一個固定的值，可能是 $\frac{3}{\,8\,}$ 也有可能是 <span class="text-nowrap">$1+\frac{3}{\,8\,}$，</span>故極限不存在。

事實上，對於 $X\in[0,1]$ 而言，$\lim_{n\to\infty}X_n$ 都不存在，因此可知 $X_n$ 並沒有幾乎確信收斂至 $X$。

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

也許有讀者會疑惑，這個收斂型態看起來已經非常強大了，為什麼其名字卻仍有點保留地說是「幾乎確信」或「幾乎處處」呢? 這是因為，幾乎確信收斂雖然要求 $X_n$ 在 $n\to\infty$ 的情況下不可以與 $X$ 有所不同，但畢竟只是定義這種情況發生的機率是 <span class="text-nowrap">$1$，</span>我們只能說此二者「幾乎不會有不同的狀況產生」。

另一方面，在其上還有一個**確信收斂 <span lang="en">(converge surely)</span>**，也就是

$$
\lim_{n\to\infty}X_n(\omega)=X(\omega),\ \forall\omega\in S
$$

這個收斂型態已經沒有機率的陳述了，當然也就不會有幾乎確信收斂中「例外集合」的問題，等價於實分析中的點態收斂 <span lang="en">(converge pointwisely)</span>。

</div>

## $r$ 次均方收斂與幾乎確信收斂互不蘊含

$r$-次均方收斂與幾乎確信收斂都是很強的收斂型態，但是這兩個收斂型態之間卻沒有互相導致的關係，見下列這題。

<div id="ex-r-mean-and-almost-sure-are-independent" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.13 <span lang="en">(Continued)</span></div>

<div lang="en" markdown="1">
Suppose that $X_1,X_2,\ldots$ are the independent discrete random variables introduced above, so that $X_n$ carries the pmf

$$
f_n(0)=1-\frac{1}{\,n\,},\quad f_n(n)=\frac{1}{\,n\,},\quad n=1,2,3,\ldots
$$

<ol class="topic-list-paren topic-list-paren--start-4">
  <li>Show that $X_n$ does not converge to $0$ almost surely.</li>
  <li>Suppose that the pmf of $X_n$ is replaced by <span class="text-nowrap">$f_n(0)=1-\frac{1}{\,n^{2}\,}$</span> and <span class="text-nowrap">$f_n(n)=\frac{1}{\,n^{2}\,}$,</span> <span class="text-nowrap">$n=1,2,3,\ldots$</span> Show that <span class="text-nowrap">$X_n\asconv0$</span> while $X_n$ does not converge to $0$ in $2$-nd mean.</li>
  <li>Suppose instead that the pmf of $X_n$ is replaced by <span class="text-nowrap">$f_n(0)=1-\frac{1}{\,n\,}$</span> and <span class="text-nowrap">$f_n(1)=\frac{1}{\,n\,}$,</span> <span class="text-nowrap">$n=1,2,3,\ldots$</span> Show that <span class="text-nowrap">$X_n\xrightarrow{~~2~~}0$</span> while $X_n$ does not converge to $0$ almost surely.</li>
</ol>
</div>

(4) 依題意可得
{: .topic-paren-item}

<!-- errata-pending: 書稿 mathstatch5.tex 第 859 行把這一列的連乘寫成
     \prod_{k=n}^{\infty}\left(1-\frac{1}{\,n\,}\right)，分母應為 k 而非 n:
     該列前一步已寫明 \prod_{k=n}^{\infty}\P(X_k=0)，而 \P(X_k=0)=1-\frac{1}{k}。
     同一份書稿第 880 行 (本篇第 (6) 小題) 的對應寫法即為 1-\frac{1}{\,k\,}，可為佐證。
     依 SITE_STYLE_CANON 第〇節第 5 點，網頁採正確寫法，待作者裁定後登錄 ERRATA.md。 -->

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}\bigl(\lvert X_k-0\rvert<\varepsilon,\ \forall k\geqslant n\bigr)=\mathbb{P}\bigl(X_k=0,\ \forall k\geqslant n\bigr)=\prod_{k=n}^{\infty}\mathbb{P}(X_k=0)=\prod_{k=n}^{\infty}\Bigl(1-\frac{1}{\,k\,}\Bigr)=0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}\bigl(\lvert X_k-0\rvert<\varepsilon,\ \forall k\geqslant n\bigr)&=\mathbb{P}\bigl(X_k=0,\ \forall k\geqslant n\bigr)\\[0.45em]
&=\prod_{k=n}^{\infty}\mathbb{P}(X_k=0)\\[0.45em]
&=\prod_{k=n}^{\infty}\Bigl(1-\frac{1}{\,k\,}\Bigr)=0
\end{aligned}
$$

</div>

故由幾乎確信收斂之等價定義可知
{: .topic-paren-cont}

$$
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_k-0\rvert<\varepsilon,\ \forall k\geqslant n\bigr)=0\neq1
$$

此即 $X_n$ 並沒有幾乎確信收斂至 $0$。
{: .topic-paren-cont}

(5) 依題意可得
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}\bigl(\lvert X_k-0\rvert<\varepsilon,\ \forall k\geqslant n\bigr)=\mathbb{P}\bigl(X_k=0,\ \forall k\geqslant n\bigr)=\prod_{k=n}^{\infty}\mathbb{P}(X_k=0)=\prod_{k=n}^{\infty}\Bigl(1-\frac{1}{\,k^{2}\,}\Bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}\bigl(\lvert X_k-0\rvert<\varepsilon,\ \forall k\geqslant n\bigr)&=\mathbb{P}\bigl(X_k=0,\ \forall k\geqslant n\bigr)\\[0.45em]
&=\prod_{k=n}^{\infty}\mathbb{P}(X_k=0)\\[0.45em]
&=\prod_{k=n}^{\infty}\Bigl(1-\frac{1}{\,k^{2}\,}\Bigr)
\end{aligned}
$$

</div>

其中
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\prod_{k=n}^{\infty}\Bigl(1-\frac{1}{\,k^{2}\,}\Bigr)=e^{\ln\prod_{k=n}^{\infty}\left(1-\frac{1}{k^{2}}\right)}=e^{\sum_{k=n}^{\infty}\ln\left(1-\frac{1}{k^{2}}\right)},\ \forall n\in\mathbb{N}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\prod_{k=n}^{\infty}\Bigl(1-\frac{1}{\,k^{2}\,}\Bigr)&=e^{\ln\prod_{k=n}^{\infty}\left(1-\frac{1}{k^{2}}\right)}\\[0.45em]
&=e^{\sum_{k=n}^{\infty}\ln\left(1-\frac{1}{k^{2}}\right)},\\[0.45em]
&\qquad\forall n\in\mathbb{N}
\end{aligned}
$$

</div>

又因
{: .topic-paren-cont}

$$
\int_{1}^{\infty}\Bigl\lvert\ln\Bigl(1-\frac{1}{\,x^{2}\,}\Bigr)\Bigr\rvert\,dx=\ln4<\infty
$$

故由積分審斂法可知 $\sum_{k=2}^{\infty}\bigl\lvert\ln\bigl(1-\frac{1}{k^{2}}\bigr)\bigr\rvert$ 收斂，此即
{: .topic-paren-cont}

$$
\lim_{n\to\infty}\sum_{k=n}^{\infty}\Bigl\lvert\ln\Bigl(1-\frac{1}{\,k^{2}\,}\Bigr)\Bigr\rvert=0\qquad\therefore\, \lim_{n\to\infty}\sum_{k=n}^{\infty}\ln\Bigl(1-\frac{1}{\,k^{2}\,}\Bigr)=0
$$

由此可得
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_k-0\rvert<\varepsilon,\ \forall k\geqslant n\bigr)=\lim_{n\to\infty}e^{\sum_{k=n}^{\infty}\ln\left(1-\frac{1}{k^{2}}\right)}=e^{\lim\limits_{n\to\infty}\sum_{k=n}^{\infty}\ln\left(1-\frac{1}{k^{2}}\right)}=e^{0}=1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_k-0\rvert<\varepsilon,\ \forall k\geqslant n\bigr)&=\lim_{n\to\infty}e^{\sum_{k=n}^{\infty}\ln\left(1-\frac{1}{k^{2}}\right)}\\[0.45em]
&=e^{\lim\limits_{n\to\infty}\sum_{k=n}^{\infty}\ln\left(1-\frac{1}{k^{2}}\right)}\\[0.45em]
&=e^{0}=1
\end{aligned}
$$

</div>

由幾乎確信收斂之等價定義可知
{: .topic-paren-cont}

$$
X_n\asconv0
$$

然而，由於
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\bigl[\lvert X_n-0\rvert^{2}\bigr]=\mathbb{E}\bigl[\lvert X_n\rvert^{2}\bigr]=\lvert0\rvert^{2}\times\Bigl(1-\frac{1}{\,n^{2}\,}\Bigr)+\lvert n\rvert^{2}\times\frac{1}{\,n^{2}\,}=1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[\lvert X_n-0\rvert^{2}\bigr]&=\mathbb{E}\bigl[\lvert X_n\rvert^{2}\bigr]\\[0.45em]
&=\lvert0\rvert^{2}\times\Bigl(1-\frac{1}{\,n^{2}\,}\Bigr)\\[0.45em]
&\qquad+\lvert n\rvert^{2}\times\frac{1}{\,n^{2}\,}\\[0.45em]
&=1
\end{aligned}
$$

</div>

故可知
{: .topic-paren-cont}

$$
\lim_{n\to\infty}\mathbb{E}\bigl[\lvert X_n-0\rvert^{2}\bigr]=1\neq0
$$

此即 $X_n$ 沒有 $2$ 次均方收斂至 $0$。
{: .topic-paren-cont}

(6) 依題意可得
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\bigl[\lvert X_n-0\rvert^{2}\bigr]=\mathbb{E}\bigl[\lvert X_n\rvert^{2}\bigr]=\lvert0\rvert^{2}\times\Bigl(1-\frac{1}{\,n\,}\Bigr)+\lvert1\rvert^{2}\times\frac{1}{\,n\,}=\frac{1}{\,n\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[\lvert X_n-0\rvert^{2}\bigr]&=\mathbb{E}\bigl[\lvert X_n\rvert^{2}\bigr]\\[0.45em]
&=\lvert0\rvert^{2}\times\Bigl(1-\frac{1}{\,n\,}\Bigr)\\[0.45em]
&\qquad+\lvert1\rvert^{2}\times\frac{1}{\,n\,}\\[0.45em]
&=\frac{1}{\,n\,}
\end{aligned}
$$

</div>

故可知
{: .topic-paren-cont}

$$
\lim_{n\to\infty}\mathbb{E}\bigl[\lvert X_n-0\rvert^{2}\bigr]=0
$$

此即
{: .topic-paren-cont}

$$
X_n\xrightarrow{~~2~~}0
$$

然而，與 (4) 同理，由於 $\lvert X_k-0\rvert<\varepsilon,\ \varepsilon>0$ 之事件等價於 <span class="text-nowrap">$X_n=0$，</span>故我們有
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}\bigl(\lvert X_k-0\rvert<\varepsilon,\ \forall k\geqslant n\bigr)=\mathbb{P}\bigl(X_k=0,\ \forall k\geqslant n\bigr)=\prod_{k=n}^{\infty}\mathbb{P}(X_k=0)=\prod_{k=n}^{\infty}\Bigl(1-\frac{1}{\,k\,}\Bigr)=0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}\bigl(\lvert X_k-0\rvert<\varepsilon,\ \forall k\geqslant n\bigr)&=\mathbb{P}\bigl(X_k=0,\ \forall k\geqslant n\bigr)\\[0.45em]
&=\prod_{k=n}^{\infty}\mathbb{P}(X_k=0)\\[0.45em]
&=\prod_{k=n}^{\infty}\Bigl(1-\frac{1}{\,k\,}\Bigr)=0
\end{aligned}
$$

</div>

故由幾乎確信收斂之等價定義可知
{: .topic-paren-cont}

$$
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_k-0\rvert<\varepsilon,\ \forall k\geqslant n\bigr)=0\neq1
$$

此即 $X_n$ 並沒有幾乎確信收斂至 $0$。
{: .topic-paren-cont}

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個問題可以很清楚地看出，$r$ 次均方收斂與幾乎確信收斂之間，並沒有強弱的關係，在不同的機率分配之下，不同的收斂概念中，會有不同的結果。

</div>

至此，我們已經看過不少收斂的型態與例子，現在就讓我們來看看統計中相當實用的兩個與收斂有關係的定理，分別是**[弱大數法則](/lecture-notes/weak-law-and-central-limit-theorem/#thm-weak-law-of-large-numbers) <span lang="en">(Weak Law of Large Numbers, WLLN)</span>** 與**[中央極限定理](/lecture-notes/weak-law-and-central-limit-theorem/#thm-central-limit-theorem) <span lang="en">(Central Limit Theorem, CLT)</span>**。

[^offset]: 我們並不是在此要求機率或機率密度為 <span class="text-nowrap">$0$，</span>而是要求 $\lvert X_n-X\rvert^{r}$ 必須被機率密度「抵銷」，這其中的條件也包含了 <span class="text-nowrap">$n\to\infty$，</span>因此，即便距離不為 $0$ 的地方，機率密度不是 <span class="text-nowrap">$0$，</span>只要當 $n\to\infty$ 時可以收斂至 <span class="text-nowrap">$0$，</span>那也同樣沒有問題。

[^pconv-tolerance]: 特別注意的是，即使 $X_n$ 與 $X$ 再怎樣都可能發生距離不小於 $\varepsilon>0$ 的事件 (甚至當 $n\to\infty$ 都還會持續發生也無所謂)，只要這個機率能夠漸漸收斂至 <span class="text-nowrap">$0$，</span>都滿足機率收斂的定義。

[^casella-source]: 本題修改自 Casella and Berger (2002)，*Statistical Inference*，2nd ed.，頁 234。

## 本篇小結

[Definition 5.3](#def-converge-in-r-mean) 的 $r$ 次均方收斂以 $\mathbb{E}\bigl[\lvert X_n-X\rvert^{r}\bigr]$ 是否趨於零來界定。由於距離的 $r$ 次方是非負的，要讓這個期望值趨於零，機率或機率密度就必須把那些距離不為零的地方「抵銷」掉；機率收斂只要求距離不小於 $\varepsilon$ 的那些地方機率趨於零，並不必負擔抵銷的工作，兩者的強弱之別正在於此。[Theorem 5.4](#thm-rconv-implies-pconv) 把這件事寫成定理，證明只用到馬可夫不等式給出的 $\mathbb{P}(\lvert X_n-X\rvert\geqslant\varepsilon)\leqslant\frac{\mathbb{E}[\lvert X_n-X\rvert^{r}]}{\varepsilon^{r}}$ 這條界限，再讓 $n\to\infty$ 即可。

[Example 5.13](#ex-pconv-without-first-mean) 說明反方向不成立: 取值為 $0$ 與 $n$ 而機率分別為 $1-\frac{1}{\,n\,}$ 與 $\frac{1}{\,n\,}$ 的序列，機率收斂至零，但 $\mathbb{E}\bigl[\lvert X_n-0\rvert\bigr]$ 恆等於 <span class="text-nowrap">$1$，</span>不會趨於零。這一題是刻意設計的: 取值隨 $n$ 成長的速度，恰好與機率隨 $n$ 遞減的速度一樣快，兩者相乘之後不隨 $n$ 改變。把機率改成 $\frac{1}{\,n^{m}\,}$ 之後，$m$ 次均方收斂仍然失敗，但一切 $0<r<m$ 的 $r$ 次均方收斂都成立。

[Theorem 5.5](#thm-2conv-implies-pconv) 把 $r=2$ 的情形單獨拿出來: 只要期望值收斂至常數 $c$ 而變異數收斂至零，序列就二次均方收斂至 <span class="text-nowrap">$c$，</span>因而也機率收斂至 <span class="text-nowrap">$c$。</span>證明的作法是把 $\mathbb{E}\bigl[(X_n-c)^{2}\bigr]$ 展開，再以 [Theorem 2.11](/lecture-notes/variance/#thm-variance-formula) 的 $\mathrm{Var}(X)=\mathbb{E}(X^{2})-[\mathbb{E}(X)]^{2}$ 這條公式把二階原動差換掉，湊成 $\mathrm{Var}(X_n)+\bigl[\mathbb{E}(X_n)-c\bigr]^{2}$ 這個形式，兩項各自趨於零。二次均方收斂至母體參數的序列在數理統計中另有均方一致性這個名字，它比一般的一致性強。[Example 5.10 <span lang="en">(Continued)</span>](#ex-s-squared-mean-square-consistency) 即以這條判準重解一次 $S^{2}$ 的機率極限: 在[常態分配](/lecture-notes/normal-distribution/#def-normal)的母體之下，由[伽瑪分配](/lecture-notes/gamma-distribution/#def-gamma-distribution)算出 $\mathbb{E}\bigl(S^{2}\bigr)=\sigma^{2}$ 與 <span class="text-nowrap">$\mathrm{Var}\bigl(S^{2}\bigr)=\frac{2\sigma^{4}}{\,n-1\,}$，</span>後者在 $n\to\infty$ 時趨於零，故 <span class="text-nowrap">$S^{2}\pconv\sigma^{2}$。</span>其中 $S^{2}$ 的伽瑪分配來自 [Theorem 4.23](/lecture-notes/chi-squared-distribution/#thm-cochran-theorem) 的 <span class="text-nowrap">$\frac{(n-1)S^{2}}{\sigma^{2}}\sim\chi^{2}(n-1)$。</span>

[Definition 5.4](#def-converge-almost-surely) 的幾乎確信收斂換一個角度: 它不看機率本身怎麼變化，而是看那些使 $\lim_{n\to\infty}X_n(\omega)$ 與 $X(\omega)$ 不相等的樣本點 $\omega$ 收集而成的「例外集合」，要求這個集合的發生機率是零。[Theorem 5.6](#thm-asconv-implies-pconv) 指出它同樣導致機率收斂。[Example 5.14](#ex-indicator-block-sequence) 給出反方向的反例: 以[均勻分配](/lecture-notes/uniform-distribution-integral-transform/#def-uniform-distribution)的 $X$ 加上一段一段往右移動的指標函數，每一段的長度為 <span class="text-nowrap">$\frac{1}{\,m\,}$，</span>因此 $\mathbb{P}(\lvert X_n-X\rvert\geqslant\varepsilon)=\frac{1}{\,m\,}$ 會趨於零，機率收斂成立；但每一個 $X\in[0,1]$ 都會被無窮多段掃到，$\lim_{n\to\infty}X_n$ 根本不存在，幾乎確信收斂因而不成立。

最後，[Example 5.13 <span lang="en">(Continued)</span>](#ex-r-mean-and-almost-sure-are-independent) 把 $r$ 次均方收斂與幾乎確信收斂擺在一起比較。同一個序列既不幾乎確信收斂至零，也不一次均方收斂至零；把機率改為 $\frac{1}{\,n^{2}\,}$ 之後，$\prod_{k=n}^{\infty}\bigl(1-\frac{1}{k^{2}}\bigr)$ 的極限為 <span class="text-nowrap">$1$，</span>幾乎確信收斂成立，二次均方收斂卻失敗；把取值由 $n$ 改為 $1$ 之後，二次均方收斂成立，幾乎確信收斂又失敗。可見這兩個收斂型態之間並沒有互相導致的關係。

至此，四種收斂型態與它們之間的關係都已經給齊。[下一篇](/lecture-notes/weak-law-and-central-limit-theorem/)轉入兩條直接用得上的極限定理，分別是弱大數法則與中央極限定理，前者說的是樣本平均數機率收斂至母體期望值，後者說的是標準化之後的樣本平均數分配收斂至標準常態分配。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Kai Lai Chung. 2001. *A Course in Probability Theory*. 3rd ed. Academic Press.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
