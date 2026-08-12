---
title: "線性組合的變異數"
subtitle: "The Variance of a Linear Combination"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 19
order: 319
permalink: /teaching-topics/ch3-p19-candidate/
date: 2026-08-13
published: false
excerpt: "共變異數的性質裡，有一款說一個變數與自己的共變異數就是變異數，另一款說常數的伸縮會原封不動地反映在共變異數上；把這兩款整合起來，便得到一組隨機變數線性組合的變異數: 它等於各項變異數的加權和，再加上兩倍的各對共變異數之和。當各項彼此獨立或零相關時，所有的共變異數都是 $0$，式子簡化為 $\\mathrm{Var}\\bigl(\\sum a_iX_i\\bigr)=\\sum a_i^{2}\\mathrm{Var}(X_i)$，這是變異數平方伸縮性的推廣，也是 $\\mathrm{Var}(\\overline{X})=\\sigma_{\\sssig X}^{2}/n$ 的由來。本篇的兩道例題所處理的加總，各項都不是彼此獨立的: 一道給定任兩項同時取值為 $1$ 的機率，另一道是有限母體之下的取後不放回抽樣，其期望值與變異數很像二項分配，只差了一個有限母體校正因子。"
---

[上一篇](/teaching-topics/ch3-p18-candidate/)以 [Definition 3.16](/teaching-topics/ch3-p18-candidate/#def-covariance) 給出共變異數，並以 [Theorem 3.15](/teaching-topics/ch3-p18-candidate/#thm-covar-proper) 列出它的六款性質，其中第 (3) 款說一個變數與自己的共變異數就是變異數，第 (4) 款說常數的伸縮會原封不動地反映在共變異數上。

本篇把這兩款整合起來，得到 [Theorem 3.16](#thm-covar-proper2) 的線性組合的變異數展開式: 一組隨機變數的線性組合，其變異數等於各項變異數的加權和，再加上兩倍的各對共變異數之和。接著說明各項彼此獨立或零相關的時候這個式子如何簡化，並由這個特例得到 $\mathrm{Var}\bigl(\overline{X}\bigr)$ $=$ $\frac{\,\sigma_{\sssig X}^{2}\,}{n}$ 這個往後經常用到的結果。

本篇最後有兩道例題，兩題所加總的各項都不是彼此獨立的。第一道給定任兩項同時取值為 $1$ 的機率，求 $n$ 項加總的變異數，並說明 $X_i-\overline{X}$ 與 $\overline{X}$ 的共變異數為 <span class="text-nowrap">$0$；</span>第二道則是有限母體之下的取後不放回抽樣。

## 線性組合的變異數

<div id="thm-covar-proper2" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 3.16 (線性組合的變異數, variance of a linear combination)</div>

若 $X_1, \ldots, X_n$ 為隨機變數，且 $a_1, \ldots, a_n$ 為常數，則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}\Bigl(\sum_{i=1}^{n}a_i\,X_i\Bigr)=\sum_{i=1}^{n}a_i^{2}\,\mathrm{Var}(X_i)+2\mathop{\sum\sum}\limits_{i<j}a_ia_j\,\operatorname{Cov}(X_i,X_j)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathrm{Var}\Bigl(\sum_{i=1}^{n}a_i\,X_i\Bigr)\\[0.45em]
&\quad =\sum_{i=1}^{n}a_i^{2}\,\mathrm{Var}(X_i)\\[0.2em]
&\qquad +2\mathop{\sum\sum}\limits_{i<j}a_ia_j\,\operatorname{Cov}(X_i,X_j)
\end{aligned}
$$

</div>

</div>

<div class="topic-proof" markdown="1">
**Proof.**

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathrm{Var}\Bigl(\sum_{i=1}^{n}a_i\,X_i\Bigr)&=\operatorname{Cov}\Bigl(\sum_{i=1}^{n}a_i\,X_i,\ \sum_{i=1}^{n}a_i\,X_i\Bigr)\\[0.45em]
&=\sum_{i=1}^{n}\operatorname{Cov}(a_i\,X_i,\,a_i\,X_i)+\mathop{\sum\sum}\limits_{i\neq j}\operatorname{Cov}(a_i\,X_i,\,a_j\,X_j)\\[0.45em]
&=\sum_{i=1}^{n}a_i^{2}\,\mathrm{Var}(X_i)+2\mathop{\sum\sum}\limits_{i<j}a_ia_j\,\operatorname{Cov}(X_i,X_j)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathrm{Var}\Bigl(\sum_{i=1}^{n}a_i\,X_i\Bigr)\\[0.45em]
&\quad =\operatorname{Cov}\Bigl(\sum_{i=1}^{n}a_i\,X_i,\ \sum_{i=1}^{n}a_i\,X_i\Bigr)\\[0.45em]
&\quad =\sum_{i=1}^{n}\operatorname{Cov}(a_i\,X_i,\,a_i\,X_i)\\[0.2em]
&\qquad +\mathop{\sum\sum}\limits_{i\neq j}\operatorname{Cov}(a_i\,X_i,\,a_j\,X_j)\\[0.45em]
&\quad =\sum_{i=1}^{n}a_i^{2}\,\mathrm{Var}(X_i)\\[0.2em]
&\qquad +2\mathop{\sum\sum}\limits_{i<j}a_ia_j\,\operatorname{Cov}(X_i,X_j)
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

讀者應特別注意，當 $X_1, \ldots, X_n$ 彼此皆[獨立](/teaching-topics/ch3-p09-candidate/#def-indep-r-v)或零相關的時候，[上述定理](#thm-covar-proper2)可以簡化成

$$
\mathrm{Var}\Bigl(\sum_{i=1}^{n}a_i\,X_i\Bigr)=\sum_{i=1}^{n}a_i^{2}\,\mathrm{Var}(X_i)
$$

因為 <span class="text-nowrap">$\operatorname{Cov}(X_i,X_j)=0,\ \forall i\neq j$，</span>並且這其實就是變異數的[**平方伸縮性**](/teaching-topics/ch2-p208-candidate/#thm-variance-properties)的推廣。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個特例就是在 [Theorem 3.12](/teaching-topics/ch3-p16-candidate/#thm-wald-identity) 的沃德等式第二式中，$\mathrm{Var}(S_{\sssig N}\mid N=n)$ $=$ $n\sigma_{\sssig X}^{2}$ 的原因。

</div>

而此特例又能衍生出一個非常重要的結果，即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}\bigl(\overline{X}\bigr)=\mathrm{Var}\biggl(\frac{1}{\,n\,}\sum_{i=1}^{n}X_i\biggr)=\frac{1}{\,n^{2}\,}\sum_{i=1}^{n}\mathrm{Var}(X_i)=\frac{\,\sigma_{\sssig X}^{2}\,}{n}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathrm{Var}\bigl(\overline{X}\bigr)=\mathrm{Var}\biggl(\frac{1}{\,n\,}\sum_{i=1}^{n}X_i\biggr)\\[0.45em]
&\quad =\frac{1}{\,n^{2}\,}\sum_{i=1}^{n}\mathrm{Var}(X_i)=\frac{\,\sigma_{\sssig X}^{2}\,}{n}
\end{aligned}
$$

</div>

## 線性組合的變異數在計算上的應用

<div id="ex-bernoulli-sum-covariance" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.39</div>

<div lang="en" markdown="1">
<ol class="topic-list-paren">
  <li>Suppose that $X_1,\ldots,X_n$ are random variables for which $\mathbb{P}(X_i=1)=p$ and $\mathbb{P}(X_i=0)=1-p$, while $\mathbb{P}(X_i=1,X_j=1)=q$ holds for every pair with <span class="text-nowrap">$i\neq j$.</span> Find <span class="text-nowrap">$\mathrm{Var}(X_1+\cdots+X_n)$.</span></li>
  <li>Suppose that $X_1,\ldots,X_n$ are independent and identically distributed random variables with finite variance <span class="text-nowrap">$\sigma^{2}$.</span> Show that <span class="text-nowrap">$\operatorname{Cov}(X_i-\overline{X},\overline{X})=0$.</span></li>
</ol>
</div>

(1)
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}(X_i)=\mathbb{E}(X_i^{2})-\bigl[\mathbb{E}(X_i)\bigr]^{2}=p(1-p)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathrm{Var}(X_i)=\mathbb{E}(X_i^{2})-\bigl[\mathbb{E}(X_i)\bigr]^{2}\\[0.2em]
&\quad =p(1-p)
\end{aligned}
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\operatorname{Cov}(X_i,X_j)=\mathbb{E}(X_iX_j)-\mathbb{E}(X_i)\,\mathbb{E}(X_j)=q-p^{2}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\operatorname{Cov}(X_i,X_j)\\[0.45em]
&\quad =\mathbb{E}(X_iX_j)-\mathbb{E}(X_i)\,\mathbb{E}(X_j)=q-p^{2}
\end{aligned}
$$

</div>

故知道
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(X_1+\cdots+X_n)&=\sum_{i=1}^{n}\mathrm{Var}(X_i)+2\mathop{\sum\sum}\limits_{i<j}\operatorname{Cov}(X_i,X_j)\\[0.45em]
&=n\,p(1-p)+n(n-1)\,(q-p^{2})
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathrm{Var}(X_1+\cdots+X_n)\\[0.45em]
&\quad =\sum_{i=1}^{n}\mathrm{Var}(X_i)\\[0.2em]
&\qquad +2\mathop{\sum\sum}\limits_{i<j}\operatorname{Cov}(X_i,X_j)\\[0.45em]
&\quad =n\,p(1-p)+n(n-1)\,(q-p^{2})
\end{aligned}
$$

</div>

(2) $\operatorname{Cov}(X_i-\overline{X},\overline{X})$ $=$ $\operatorname{Cov}(X_i,\overline{X})$ $-$ <span class="text-nowrap">$\operatorname{Cov}(\overline{X},\overline{X})$，</span>且
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\operatorname{Cov}(X_i,\overline{X})&=\operatorname{Cov}\biggl[\,X_i,\ \frac{1}{\,n\,}(X_1+\cdots+X_n)\,\biggr]\\[0.45em]
&=\frac{1}{\,n\,}\Bigl[\,\operatorname{Cov}(X_i,X_1)+\cdots+\operatorname{Cov}(X_i,X_i)\\[0.2em]
&\qquad\qquad +\cdots+\operatorname{Cov}(X_i,X_n)\,\Bigr]\\[0.45em]
&=\frac{1}{\,n\,}\Bigl[\,0+\cdots+\mathrm{Var}(X_i)+\cdots+0\,\Bigr]=\frac{\,\sigma^{2}\,}{\,n\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\operatorname{Cov}(X_i,\overline{X})\\[0.45em]
&\quad =\operatorname{Cov}\biggl[\,X_i,\ \frac{1}{\,n\,}(X_1+\cdots+X_n)\,\biggr]\\[0.45em]
&\quad =\frac{1}{\,n\,}\Bigl[\,\operatorname{Cov}(X_i,X_1)+\cdots\\[0.2em]
&\qquad\quad +\operatorname{Cov}(X_i,X_i)+\cdots\\[0.2em]
&\qquad\quad +\operatorname{Cov}(X_i,X_n)\,\Bigr]\\[0.45em]
&\quad =\frac{1}{\,n\,}\Bigl[\,0+\cdots+\mathrm{Var}(X_i)+\cdots+0\,\Bigr]\\[0.2em]
&\qquad =\frac{\,\sigma^{2}\,}{\,n\,}
\end{aligned}
$$

</div>

又 $\operatorname{Cov}(\overline{X},\overline{X})$ $=$ $\mathrm{Var}\bigl(\overline{X}\bigr)$ $=$ <span class="text-nowrap">$\frac{\,\sigma^{2}\,}{n}$，</span>故可知
{: .topic-paren-cont}

$$
\operatorname{Cov}(X_i-\overline{X},\overline{X})=\frac{\,\sigma^{2}\,}{\,n\,}-\frac{\,\sigma^{2}\,}{\,n\,}=0
$$

</div>

<div id="ex-hypergeometric-variance" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.40</div>

<div lang="en" markdown="1">
Suppose that a collection of $N$ components includes $M$ that are defective, and that components are drawn one at a time at random without replacement. For each <span class="text-nowrap">$i$,</span> let $X_i$ record the number of defective components obtained on the $i$-th draw. Find the mean and the variance of <span class="text-nowrap">$Y=\sum_{i=1}^{n}X_i$.</span>
</div>

由題意可令

$$
X_i=\left\lbrace
\begin{array}{cl}
1, & \text{第}\ i\ \text{次抽取為不良品}\\[0.3em]
0, & \text{第}\ i\ \text{次抽取為良品}
\end{array}
\right.
$$

則可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\mathbb{E}(X_i)=\mathbb{E}(X_i^{2})=\mathbb{P}(X_i=1)=\frac{\,M\,}{N}\\[0.45em]
\mathrm{Var}(X_i)=\mathbb{E}(X_i^{2})-\bigl[\mathbb{E}(X_i)\bigr]^{2}=\frac{\,M\,}{N}\times\frac{\,(N-M)\,}{N}
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}(X_i)=\mathbb{E}(X_i^{2})=\mathbb{P}(X_i=1)\\[0.2em]
&\quad =\frac{\,M\,}{N}\\[0.45em]
&\mathrm{Var}(X_i)=\mathbb{E}(X_i^{2})-\bigl[\mathbb{E}(X_i)\bigr]^{2}\\[0.2em]
&\quad =\frac{\,M\,}{N}\times\frac{\,(N-M)\,}{N}
\end{aligned}
$$

</div>

且由於取後不放回，我們可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X_i\,X_j)&=\frac{\,M(M-1)\,}{N(N-1)}\\[0.45em]
\Longrightarrow\ \operatorname{Cov}(X_i,X_j)&=\mathbb{E}(X_iX_j)-\mathbb{E}(X_i)\,\mathbb{E}(X_j)\\[0.2em]
&=\frac{\,M(M-1)\,}{N(N-1)}-\frac{\,M^{2}\,}{N^{2}}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}(X_i\,X_j)=\frac{\,M(M-1)\,}{N(N-1)}\\[0.45em]
&\Longrightarrow\ \operatorname{Cov}(X_i,X_j)\\[0.2em]
&\quad =\mathbb{E}(X_iX_j)-\mathbb{E}(X_i)\,\mathbb{E}(X_j)\\[0.2em]
&\quad =\frac{\,M(M-1)\,}{N(N-1)}-\frac{\,M^{2}\,}{N^{2}}
\end{aligned}
$$

</div>

則我們分別有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(Y)=\mathbb{E}\biggl(\sum_{i=1}^{n}X_i\biggr)=\sum_{i=1}^{n}\mathbb{E}(X_i)=n\,\frac{\,M\,}{N}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}(Y)=\mathbb{E}\biggl(\sum_{i=1}^{n}X_i\biggr)\\[0.2em]
&\quad =\sum_{i=1}^{n}\mathbb{E}(X_i)=n\,\frac{\,M\,}{N}
\end{aligned}
$$

</div>

以及

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(Y)&=\mathrm{Var}\biggl(\sum_{i=1}^{n}X_i\biggr)\\[0.2em]
&=\sum_{i=1}^{n}\mathrm{Var}(X_i)+2\mathop{\sum\sum}\limits_{i<j}\operatorname{Cov}(X_i,X_j)\\[0.45em]
&=n\,\frac{\,M\,}{N}\,\frac{\,(N-M)\,}{N}+n(n-1)\,\biggl[\,\frac{\,M(M-1)\,}{N(N-1)}-\frac{\,M^{2}\,}{N^{2}}\,\biggr]\\[0.45em]
&=n\,\frac{\,M\,}{N}-n\,\frac{\,M^{2}\,}{N^{2}}+n(n-1)\,\frac{\,M(M-1)\,}{N(N-1)}\\[0.2em]
&\qquad -n^{2}\,\frac{\,M^{2}\,}{N^{2}}+n\,\frac{\,M^{2}\,}{N^{2}}\\[0.45em]
&=n\,\frac{\,M\,}{N}\,\biggl[1+(n-1)\,\frac{\,(M-1)\,}{(N-1)}-n\,\frac{\,M\,}{N}\biggr]\\[0.45em]
&=n\,\frac{\,M\,}{N}\times\frac{\,N(N-1)+(n-1)N(M-1)-nM(N-1)\,}{N(N-1)}\\[0.45em]
&=n\,\frac{\,M\,}{N}\,\frac{\,N^{2}-MN-nN+nM\,}{N(N-1)}\\[0.45em]
&=n\,\frac{\,M\,}{N}\,\frac{\,(N-M)(N-n)\,}{N(N-1)}\\[0.2em]
&=n\,\frac{\,M\,}{N}\,\biggl(1-\frac{\,M\,}{N}\biggr)\,\biggl(\frac{\,N-n\,}{N-1}\biggr)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathrm{Var}(Y)=\mathrm{Var}\biggl(\sum_{i=1}^{n}X_i\biggr)\\[0.45em]
&\quad =\sum_{i=1}^{n}\mathrm{Var}(X_i)\\[0.2em]
&\qquad +2\mathop{\sum\sum}\limits_{i<j}\operatorname{Cov}(X_i,X_j)\\[0.45em]
&\quad =n\,\frac{\,M\,}{N}\,\frac{\,(N-M)\,}{N}\\[0.2em]
&\qquad +n(n-1)\,\biggl[\,\frac{\,M(M-1)\,}{N(N-1)}\\[0.2em]
&\qquad\qquad -\frac{\,M^{2}\,}{N^{2}}\,\biggr]\\[0.45em]
&\quad =n\,\frac{\,M\,}{N}-n\,\frac{\,M^{2}\,}{N^{2}}\\[0.2em]
&\qquad +n(n-1)\,\frac{\,M(M-1)\,}{N(N-1)}\\[0.2em]
&\qquad -n^{2}\,\frac{\,M^{2}\,}{N^{2}}+n\,\frac{\,M^{2}\,}{N^{2}}\\[0.45em]
&\quad =n\,\frac{\,M\,}{N}\,\biggl[1+(n-1)\,\frac{\,(M-1)\,}{(N-1)}\\[0.2em]
&\qquad\qquad -n\,\frac{\,M\,}{N}\biggr]\\[0.45em]
&\quad =n\,\frac{\,M\,}{N}\times\\[0.2em]
&\quad\ \ \frac{\,\begin{gathered}N(N-1)+(n-1)N(M-1)\\[0.1em] -\,nM(N-1)\end{gathered}\,}{N(N-1)}\\[0.45em]
&\quad =n\,\frac{\,M\,}{N}\,\frac{\,N^{2}-MN-nN+nM\,}{N(N-1)}\\[0.45em]
&\quad =n\,\frac{\,M\,}{N}\,\frac{\,(N-M)(N-n)\,}{N(N-1)}\\[0.45em]
&\quad =n\,\frac{\,M\,}{N}\,\biggl(1-\frac{\,M\,}{N}\biggr)\,\biggl(\frac{\,N-n\,}{N-1}\biggr)
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這一題的情境設計，是**有限母體 <span lang="en">(finite element population)</span>** 下的取後不放回抽樣。

讀者會發現，單看每一個 <span class="text-nowrap">$X_i$，</span>它們都是 $\mathrm{Ber}(p)$ 分配，其中的 <span class="text-nowrap">$p=M/N$，</span>但由於抽樣設計的緣故，每一個 $X_i$ 並沒有彼此獨立，因此無法以稍後會提到的**二項分配可加性**來處理這個問題；儘管如此，讀者仍會發現 $Y=\sum_{i=1}^{n}X_i$ 的期望值與變異數仍然很像二項分配，只是差了一個 <span class="text-nowrap">$(N-n)/(N-1)$，</span>這被稱作**有限母體校正因子 <span lang="en">(finite population correction factor, FPC factor)</span>**。

事實上，這題的結果正是**超幾何分配 <span lang="en">(hypergeometric distribution)</span>**，在稍後的章節會一併談到。

</div>

<!-- ref-point: 待第四章的二項分配與超幾何分配主題發布後，將本則 Note 的「二項分配可加性」與「超幾何分配」改為指向該處的站內連結。 -->

多元隨機變數由於表示上與運算上的複雜度，會隨著變數個數越來越多而越來越複雜，故除了機率論與數理統計外，在多變量分析 <span lang="en">(multivariate analysis)</span> 及迴歸分析 <span lang="en">(regression analysis)</span> 的領域中，我們更常以向量的形式來表示一組多元隨機變數 (即[隨機向量](/teaching-topics/ch3-p01-candidate/#def-random-vector))，並且基於線性代數 <span lang="en">(linear algebra)</span> 性質來操作。

這其中的基礎，當屬隨機向量的**共變異數矩陣 <span lang="en">(covariance matrix)</span>**，見[下列定義](/teaching-topics/ch3-p20-candidate/#def-covar-matrix):

## 本篇小結

[Theorem 3.16](#thm-covar-proper2) 由[共變異數性質](/teaching-topics/ch3-p18-candidate/#thm-covar-proper)的第 (3) 與 (4) 兩款整合而得: 線性組合的變異數，等於各項變異數乘上係數平方之後的加總，再加上兩倍的各對共變異數乘上兩個係數之後的加總。證明的作法是先把變異數寫成同一個線性組合與自己的共變異數，再逐項展開: 兩個指標相同的那 $n$ 項各給出一個 <span class="text-nowrap">$a_i^{2}\mathrm{Var}(X_i)$，</span>指標不同的則兩兩成對，因而是 $i<j$ 之和的兩倍。

當各項彼此[獨立](/teaching-topics/ch3-p09-candidate/#def-indep-r-v)或零相關的時候，所有的共變異數都是 <span class="text-nowrap">$0$，</span>式子簡化為 $\mathrm{Var}\bigl(\sum_{i=1}^{n}a_iX_i\bigr)$ $=$ <span class="text-nowrap">$\sum_{i=1}^{n}a_i^{2}\mathrm{Var}(X_i)$，</span>這正是變異數[平方伸縮性](/teaching-topics/ch2-p208-candidate/#thm-variance-properties)的推廣；[沃德等式](/teaching-topics/ch3-p16-candidate/#thm-wald-identity)第二式在推導過程中所用到的 $\mathrm{Var}(S_{\sssig N}\mid N=n)$ $=$ $n\sigma_{\sssig X}^{2}$ 也由此而來。這個特例又衍生出 $\mathrm{Var}\bigl(\overline{X}\bigr)$ $=$ $\frac{\,\sigma_{\sssig X}^{2}\,}{n}$ 這個往後經常用到的結果。

兩道例題所加總的各項都不是彼此獨立的。[Example 3.39](#ex-bernoulli-sum-covariance) 由 $\mathbb{P}(X_i=1,X_j=1)=q$ 求得每一對的共變異數為 <span class="text-nowrap">$q-p^{2}$，</span>$n$ 項加總的變異數因而是 <span class="text-nowrap">$n\,p(1-p)+n(n-1)(q-p^{2})$；</span>該題的第二小題則說明 $X_i-\overline{X}$ 與 $\overline{X}$ 的共變異數為 <span class="text-nowrap">$0$，</span>關鍵是獨立使 $\operatorname{Cov}(X_i,\overline{X})$ 只留下 $\mathrm{Var}(X_i)$ 這一項，恰好與 $\mathrm{Var}\bigl(\overline{X}\bigr)$ 相消。[Example 3.40](#ex-hypergeometric-variance) 的取後不放回使各次抽取不獨立，變異數因而多出共變異數的部分，整理之後為 <span class="text-nowrap">$n\frac{\,M\,}{N}\bigl(1-\frac{\,M\,}{N}\bigr)\frac{\,N-n\,}{N-1}$，</span>其中的 $\frac{\,N-n\,}{N-1}$ 即有限母體校正因子，而這一題的結果正是超幾何分配。

[下一篇](/teaching-topics/ch3-p20-candidate/)改以向量與矩陣的形式來表示一組多元隨機變數，並由此給出共變異數矩陣的定義。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
