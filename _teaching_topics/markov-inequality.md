---
title: "馬可夫不等式與機率上界"
subtitle: "Markov's Inequality and Probability Bounds"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 15
order: 215
permalink: /teaching-topics/markov-inequality/
date: 2026-07-13
published: true
excerpt: '馬可夫不等式只使用非負性與期望值，便能給出尾端機率的上界。它不需要知道完整分配，也是柴比雪夫不等式與其他動差界限的起點。'
---

[上一篇文章](/teaching-topics/characteristic-functions/)使用 CF 完整描述一個機率分配。本篇改從資訊較少的情形出發。即使不知道 pmf、pdf 或 CDF，只知道某個非負隨機變數的期望值，仍可對其超過門檻的機率給出上界。

這類上界通常不會求出精確機率，而是說明在既有條件下，尾端機率至多能有多大。最基本的結果先從隨機變數的非負函數開始。

## 非負函數的機率上界

<div id="theorem-23" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.3 (A Bound for Nonnegative Functions)</div>

令 $X$ 為實值隨機變數，$h:\mathbb{R}\to[0,\infty)$ 為 **Borel 可測函數 (Borel measurable function)**。若 $k>0$ 且 $\mathbb{E}[h(X)]<\infty$，則

$$
\mathbb{P}(h(X)\geqslant k)
\leqslant
\frac{\mathbb{E}[h(X)]}{k}
$$

</div>

若需回顧實數線上的 Borel $\sigma$-域，可參考[事件集合族與 $\sigma$-域](/teaching-topics/event-families-sigma-fields/#實數線上的-borel-sigma-域)。

<div class="topic-proof" markdown="1">
**Proof.** 令 $A=\lbrace h(X)\geqslant k\rbrace$，並以 $\mathbf{1}_A$ 表示事件 $A$ 的指標函數。由 $h$ 的 Borel 可測性可知，$A$ 為事件。

在 $A$ 上，$h(X)\geqslant k=k\mathbf{1}_A$；在 $A^{\prime}$ 上，$h(X)\geqslant 0=k\mathbf{1}_A$。故 $h(X)\geqslant k\mathbf{1}_A$。

兩側取期望值可得

$$
\begin{aligned}
\mathbb{E}[h(X)]
&\geqslant
\mathbb{E}(k\mathbf{1}_A) \\[0.35em]
&=
k\mathbb{P}(A) \\[0.35em]
&=
k\mathbb{P}(h(X)\geqslant k)
\end{aligned}
$$

因為 $k>0$，兩側除以 $k$ 即得定理結論。原式得證。 $\square$
</div>

這個證明同時適用於離散型、連續型與混合型隨機變數。

## 馬可夫不等式

在 [Theorem 2.3](#theorem-23) 中取 $h(x)=x_+=\max\lbrace x,0\rbrace$。此函數連續且非負，因此為 Borel 可測函數。若再假設 $X\geqslant 0$，便有 $h(X)=X$，由此可得馬可夫不等式 (Markov's inequality)。此處使用 $x_+$，是為了讓 $h$ 在整條實數線上保持非負；套用到非負隨機變數 $X$ 時，其值仍與 $X$ 相同。

<div id="theorem-24" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.4 (Markov's Inequality)</div>

若 $X$ 為非負隨機變數，且 $\mathbb{E}(X)<\infty$，則對每個 $k>0$，皆有

$$
\mathbb{P}(X\geqslant k)
\leqslant
\frac{\mathbb{E}(X)}{k}
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.** 對 $h(x)=x_+$ 套用 [Theorem 2.3](#theorem-23)。因為 $X\geqslant 0$，所以 $h(X)=X$，由此可得

$$
\mathbb{P}(X\geqslant k)
=
\mathbb{P}(h(X)\geqslant k)
\leqslant
\frac{\mathbb{E}[h(X)]}{k}
=
\frac{\mathbb{E}(X)}{k}
$$

原式得證。 $\square$
</div>

<div id="note-markov-assumptions" class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

非負性、有限期望值與正門檻都是定理的前提。若 $X$ 可能取負值，負值部分可能抵銷正值部分，使 $\mathbb{E}(X)$ 很小，卻不限制右尾機率。此時不能直接對 $X$ 套用馬可夫不等式，但可改對 $\lvert X\rvert$、$(X-c)^2$ 或其他非負函數使用 [Theorem 2.3](#theorem-23)。
</div>

<div id="interlude-217" class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 2.17</div>

令 $p=\mathbb{P}(X\geqslant k)$。若 $X\geqslant 0$，則至少有機率 $p$ 落在 $k$ 或更大的取值上。光是這部分對期望值的貢獻便不小於 $pk$，所以 $\mathbb{E}(X)\geqslant pk$，亦即 $p\leqslant\mathbb{E}(X)/k$。

這正是馬可夫不等式。它只考慮到事件 $\lbrace X\geqslant k\rbrace$ 至少造成的平均貢獻，並捨去其餘非負部分，因此通常給出保守上界。
</div>

## 以期望值倍數表示門檻

若 $0<\mathbb{E}(X)<\infty$，可令 $k=a\mathbb{E}(X)$，其中 $a>0$。

代入馬可夫不等式可得

$$
\begin{aligned}
\mathbb{P}(X\geqslant a\mathbb{E}(X))
&\leqslant
\frac{\mathbb{E}(X)}{a\mathbb{E}(X)} \\[0.35em]
&=
\frac{1}{a}
\end{aligned}
$$

當 $a>1$ 時，右側小於 $1$，這個上界才有意義。若 $0<a\leqslant 1$，則 $1/a\geqslant 1$，不等式仍然成立，但不會比機率本來就不超過 $1$ 提供更多資訊。

若 $\mathbb{E}(X)=0$，因為 $X\geqslant 0$，可知 $\mathbb{P}(X=0)=1$。此時不能用 $a\mathbb{E}(X)$ 的形式約去期望值，而應直接處理這個退化情形。

<div id="example-222" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.22 (An Income Bound)</div>

令 $X$ 表某地區家庭的年所得，並假設 $X\geqslant 0$。若平均年所得為 $100{,}000$ 個貨幣單位，則在不知道所得分配形式的情形下，可求出年所得不低於 $500{,}000$ 的家庭比例上界。

由馬可夫不等式可得

$$
\begin{aligned}
\mathbb{P}(X\geqslant 500{,}000)
&\leqslant
\frac{\mathbb{E}(X)}{500{,}000} \\[0.35em]
&=
\frac{100{,}000}{500{,}000} \\[0.35em]
&=
0.2
\end{aligned}
$$

因此，年所得不低於 $500{,}000$ 的家庭比例不超過 $20\%$。這是條件所保證的上界，不是對實際比例的**點估計 (point estimate)**。若另外知道所得的變異數或標準差，便能使用下一篇的不等式取得較小的上界。

</div>

## 高階動差版本

[Theorem 2.3](#theorem-23) 也能利用高階動差。若 $X\geqslant 0$、$r>0$、$k>0$，且 $\mathbb{E}(X^r)<\infty$，則 $x\mapsto x^r$ 在非負實數上遞增，所以 $\lbrace X\geqslant k\rbrace=\lbrace X^r\geqslant k^r\rbrace$。

對非負隨機變數 $X^r$ 使用馬可夫不等式，可得

$$
\begin{aligned}
\mathbb{P}(X\geqslant k)
&=
\mathbb{P}(X^r\geqslant k^r) \\[0.35em]
&\leqslant
\frac{\mathbb{E}(X^r)}{k^r}
\end{aligned}
$$

這個形式仍需 $X\geqslant 0$。若 $r$ 不是整數，對可能為負的 $X$ 而言，$X^r$ 甚至未必是實數。處理任意實值隨機變數時，可改用 $\lvert X\rvert^r$ 等非負函數。

馬可夫不等式也能作用在平方離差上。若 $X$ 具有有限二階動差，令 $\mu_X=\mathbb{E}(X)$，並取 $h(x)=(x-\mu_X)^2$。則 $h(X)$ 必為非負，且其期望值正是變異數。這個選擇會導出下一篇的柴比雪夫不等式。

## 本篇小結

若 $h(X)\geqslant 0$、$\mathbb{E}[h(X)]<\infty$ 且 $k>0$，則

$$
\mathbb{P}(h(X)\geqslant k)
\leqslant
\frac{\mathbb{E}[h(X)]}{k}
$$

取 $h(x)=x_+$；對非負 $X$ 有 $h(X)=X$，便得到馬可夫不等式

$$
\mathbb{P}(X\geqslant k)
\leqslant
\frac{\mathbb{E}(X)}{k}
$$

其中 $X$ 必須非負。當門檻不大於期望值時，上界可能不小於 $1$ 而缺乏資訊；當門檻是期望值的 $a>1$ 倍時，可得 $1/a$ 的上界。選擇不同的非負函數 $h$，則可把高階動差或平方離差納入界限。

[下一篇文章](/teaching-topics/chebyshev-cantelli-inequalities/)會介紹柴比雪夫不等式與坎特利不等式。前者對平方離差使用 [Theorem 2.4](#theorem-24)，後者則利用期望值與變異數給出單邊機率上界。

## 參考文獻與延伸閱讀

- 黃文璋，2003，《機率論》，初版，華泰文化。
- 黃文璋，2003，《數理統計》，初版，華泰文化。
- Patrick Billingsley. 1995. *Probability and Measure*. 3rd ed. Wiley.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Sheldon M. Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
