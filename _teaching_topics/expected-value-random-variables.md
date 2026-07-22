---
title: "期望值，隨機變數的平均位置"
subtitle: "Expected Values of Random Variables"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 6
order: 206
permalink: /teaching-topics/expected-value-random-variables/
date: 2026-06-06
published: true
excerpt: "分配說明隨機變數的機率在數線上的分配情形。期望值則依照這些機率作加權平均，給出隨機變數的平均位置。離散型以 pmf 加總，連續型以 pdf 積分。"
---

[上一篇文章](/teaching-topics/mixed-random-variables/)整理了離散、連續與混合型隨機變數。到目前為止，我們已經看過 CDF、pmf 與 pdf。這些函數描述的是隨機變數的機率在數線上的分配情形。

若分配已經指定，接下來常需要整理一個代表整體位置的數值。我們常希望用一個單一數值掌握隨機變數大致多大，而期望值正是最常使用的選擇之一。這個數值稱為**期望值 (expected value)**，也常稱為**平均數 (mean)**。期望值不是指某次實驗最可能出現的結果，也不必然是隨機變數真的可能取到的值；它是依照機率權重所得到的平均位置。

## 離散型期望值

先從離散型隨機變數開始。若 $X$ 的可能取值集合為 $\mathcal{R}_X$，且 pmf 為 $p_X(x)=\mathbb{P}(X=x)$，則期望值就是把每個可能取值乘上該點機率，再全部加總。

<div class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.6</div>

令 $X$ 為離散型隨機變數，可能取值集合為 $\mathcal{R}_X$，pmf 為 $p_X$。若

$$
\sum_{x\in\mathcal{R}_X}|x|p_X(x)<\infty
$$

則稱 $X$ 的期望值存在且有限，並定義

$$
\mathbb{E}(X)
=
\sum_{x\in\mathcal{R}_X}x p_X(x)
$$

</div>

這個公式是加權平均。每個 $x$ 的權重是 $p_X(x)$，所有權重加總為 $1$。因此，期望值可視為此一分配的平均位置。

<div class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 2.5</div>

敘述統計學中的平均數，與離散型期望值其實是同一件事的兩種寫法。設一個母體資料 (population data) 共有 $N=5$ 筆，分別為 $3,3,4,5,5$，其算術平均為 $(3+3+4+5+5)/5=4$。

若先把相同的資料值合併，則 $3$ 出現 $2$ 次，$4$ 出現 $1$ 次，$5$ 出現 $2$ 次。把每個數值出現的比例視為母體機率，便得到

$$
3\cdot\frac{2}{5}
+4\cdot\frac{1}{5}
+5\cdot\frac{2}{5}
=4
$$

這正是此母體機率分配下的期望值。所謂加權平均並沒有離開原本的算術平均；它只是把相同的資料值先作同類項合併，再用出現比例作為權重。
</div>

<div id="example-25" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.7 (Two Balls without Replacement)</div>

延續 [Example 2.2](/teaching-topics/discrete-random-variables-pmf/#example-22) 的抽球例子。箱中有四顆大小形狀完全相同、分別編號 $0,1,2,3$ 的球。從中一次抽取兩顆球，不考慮抽取順序，令 $X$ 表示兩顆球的號碼總和。

該例中 $X$ 的 pmf 為

| $x$ | 1 | 2 | 3 | 4 | 5 |
| --- | --- | --- | --- | --- | --- |
| $p_X(x)$ | $1/6$ | $1/6$ | $1/3$ | $1/6$ | $1/6$ |

因此，期望值為

$$
\mathbb{E}(X)
=
1\cdot\frac{1}{6}
+2\cdot\frac{1}{6}
+3\cdot\frac{1}{3}
+4\cdot\frac{1}{6}
+5\cdot\frac{1}{6}
=3
$$

</div>

<figure class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/expected-value-balance.svg" alt="離散分配的期望值作為平均位置。點 1 到 5 上有不同機率質量，平均位置位於 3。">
  <figcaption><span class="topic-figure__label">Fig. 2.14.</span> 期望值可視為此一分配的平均位置。此例中 $x=3$ 的機率質量較大，左右兩側仍以機率權重平衡在 $\mathbb{E}(X)=3$。</figcaption>
</figure>

<div class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 2.6</div>

期望值不一定是可能取值。投擲一顆公正骰子一次，令 $X$ 表示點數，則

$$
\mathbb{E}(X)
=
1\cdot\frac{1}{6}
+2\cdot\frac{1}{6}
+\cdots
+6\cdot\frac{1}{6}
=
3.5
$$

但骰子不可能擲出 $3.5$ 點。期望值在這裡表示長期重複投擲後的平均點數，而不是單次實驗必然會出現的點數。
</div>

## 連續型期望值

連續型隨機變數沒有可逐一相加的單點機率。若 $X$ 的 pdf 為 $f_X$，則期望值由積分定義。這與離散型的公式相互呼應，只是把加總改為積分，把 pmf 改為 pdf。

<div class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.7</div>

令 $X$ 為連續型隨機變數，pdf 為 $f_X$。若

$$
\int_{-\infty}^{\infty}|x|f_X(x)\,dx<\infty
$$

則稱 $X$ 的期望值存在且有限，並定義

$$
\mathbb{E}(X)
=
\int_{-\infty}^{\infty}x f_X(x)\,dx
$$

</div>

在離散型中，$p_X(x)$ 是各點的權重。在連續型中，$f_X(x)\,dx$ 扮演相應角色，表示 $x$ 附近很短一段區間所分到的機率。因此，連續型期望值仍然是加權平均，只是權重透過密度面積取得。

<div class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.8 (Uniform Distribution on $[0,1]$)</div>

令 $X$ 的 pdf 為

$$
f_X(x)=
\left\{
\begin{array}{c@{\quad}l}
1, & 0<x<1,\\[0.35em]
0, & \text{otherwise}
\end{array}
\right.
$$

則期望值為

$$
\mathbb{E}(X)
=
\int_{-\infty}^{\infty}x f_X(x)\,dx
=
\int_0^1 x\,dx
=
\frac{1}{2}
$$

</div>

這個結果符合直觀。若機率均勻分配在 $0$ 到 $1$ 的區間上，平均位置就在區間中央。

## 混合型期望值

若 $X$ 為[上一篇文章的 Definition 2.5](/teaching-topics/mixed-random-variables/#definition-25)所定義的混合型隨機變數，單點集合為 $A$，連續部分對整體分配的密度為 $f_X^{(c)}$。若

$$
\sum_{x\in A}|x|\mathbb{P}(X=x)
+
\int_{-\infty}^{\infty}|x|f_X^{(c)}(x)\,dx
<
\infty
$$

則其期望值由單點部分與連續部分相加，可寫為

$$
\mathbb{E}(X)
=
\sum_{x\in A}x\mathbb{P}(X=x)
+
\int_{-\infty}^{\infty}x f_X^{(c)}(x)\,dx
$$

## 函數的期望值

後續常需要處理的不只是 $X$ 本身，也可能是 $X$ 的函數。例如下一篇討論變異數時，會遇到 $(X-\mu)^2$。因此，先把函數的期望值公式整理如下。

<div id="proposition-25" class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Proposition 2.5 (Expectation of a Function of $X$)</div>

令 $g:\mathbb{R}\to\mathbb{R}$ 為 Borel 可測函數 (Borel measurable function)。若 $X$ 為離散型隨機變數，且

$$
\sum_{x\in\mathcal{R}_X}|g(x)|p_X(x)<\infty
$$

則期望值存在且可寫為

$$
\mathbb{E}[g(X)]
=
\sum_{x\in\mathcal{R}_X} g(x)p_X(x)
$$

若 $X$ 為具有 pdf $f_X$ 的連續型隨機變數，且

$$
\int_{-\infty}^{\infty}|g(x)|f_X(x)\,dx<\infty
$$

則期望值存在且可寫為

$$
\mathbb{E}[g(X)]
=
\int_{-\infty}^{\infty} g(x)f_X(x)\,dx
$$

若 $X$ 為混合型隨機變數，單點集合為 $A$，連續部分對整體分配的密度為 $f_X^{(c)}$，且

$$
\sum_{x\in A}|g(x)|\mathbb{P}(X=x)
+
\int_{-\infty}^{\infty}|g(x)|f_X^{(c)}(x)\,dx
<
\infty
$$

則期望值存在且可寫為

$$
\mathbb{E}[g(X)]
=
\sum_{x\in A}g(x)\mathbb{P}(X=x)
+
\int_{-\infty}^{\infty}g(x)f_X^{(c)}(x)\,dx
$$

</div>

若只需要計算 $\mathbb{E}[g(X)]$，可直接使用 [Proposition 2.5](#proposition-25)。後面的隨機變數轉換會先求出 $Y=g(X)$ 的分配，再由 $\mathbb{E}(Y)$ 驗算常見情形。若要證明此命題對任意 Borel 可測函數都成立，則須使用 $X$ 所誘導的機率測度及其積分性質，本篇不展開這部分。

楊維哲老師在〈機率一講〉中，曾以記述統計的平均數說明類似想法。計算平均時，不必逐筆慢慢相加，也可先依取值合併，再乘上各取值的相對頻率；他稱這是 Lebesgue 式的想法。放到隨機變數上，若要求 $g(X)$ 的期望值，便可以沿著 $X$ 原本的分配直接加權。取 $g(x)=x$ 時，便回到 $\mathbb{E}(X)$。

<div class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 2.7</div>

看到 $g(X)$ 時，讀者很自然會先想到兩件事。第一，$Y=g(X)$ 是否仍是隨機變數。[Proposition 2.5](#proposition-25) 要求 $g$ 為可測函數，正是為了保證 $g(X)$ 仍是隨機變數。第二，既然 $Y$ 也是隨機變數，是否可以先求出 $Y$ 的分配，再計算 $\mathbb{E}(Y)$？這種作法沒有錯，只是很多時候，求 $Y$ 的分配比沿著 $X$ 原本的分配直接計算更為繁複。

函數期望值公式的用途正在於此。真正先發生的仍是 $X$ 的取值。若 $X=x$，則 $g(X)=g(x)$；若 $X$ 落在 $x$ 附近，則這一小段機率對平均的貢獻就是 $g(x)$ 乘上該處附近的機率。因此，函數期望值不是先把 $g(X)$ 的分配完整求出來，再重新計算一次平均。它是沿著 $X$ 原本的分配，把每個位置 $x$ 轉成 $g(x)$ 後加權。離散型使用 $p_X(x)$ 作權重，連續型則使用 $f_X(x)\,dx$ 作權重。這正是楊老師所說，先依取值合併，再以相對頻率加權的觀點在隨機變數上的延伸。
</div>

## 期望值的線性關係

有了函數期望值後，接著可整理期望值最常使用的計算規則。

<div id="proposition-26" class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Proposition 2.6 (Linearity of Expectation)</div>

令 $X$ 為離散型、具有 pdf 的連續型或混合型隨機變數，$g,h:\mathbb{R}\to\mathbb{R}$ 為 Borel 可測函數。若

$$
\mathbb{E}|g(X)|<\infty,
\qquad
\mathbb{E}|h(X)|<\infty
$$

則對任意 $a,b\in\mathbb{R}$，皆有

$$
\mathbb{E}[a g(X)+b h(X)]
=
a\mathbb{E}[g(X)]+b\mathbb{E}[h(X)]
$$

取 $g(x)=x$ 且 $h(x)=1$，可得

$$
\mathbb{E}(aX+b)
=
a\mathbb{E}(X)+b
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.** 先考慮離散型情形。由 [Proposition 2.5](#proposition-25) 可得

$$
\begin{aligned}
\mathbb{E}[a g(X)+b h(X)]
&=
\sum_{x\in\mathcal{R}_X}[a g(x)+b h(x)]p_X(x) \\[0.45em]
&=
a\sum_{x\in\mathcal{R}_X}g(x)p_X(x)
+b\sum_{x\in\mathcal{R}_X}h(x)p_X(x) \\[0.45em]
&=
a\mathbb{E}[g(X)]+b\mathbb{E}[h(X)]
\end{aligned}
$$

具有 pdf 的連續型情形相同，只是將加總改為積分，並以 $f_X(x)\,dx$ 作為權重。混合型情形則分別對單點加總與連續部分積分使用線性關係，再把兩部分相加。原式得證。$\square$
</div>

這個規則稱為**期望值的線性關係 (linearity of expectation)**。計算變異數時，常會先把平方展開，再使用此關係把期望值拆開處理。

## 期望值與平方誤差

期望值還有一個重要的解釋。若想用常數 $a$ 代表隨機變數 $X$，可以 $(X-a)^2$ 衡量兩者的平方誤差，再以 $\mathbb{E}[(X-a)^2]$ 衡量平均的平方誤差。令 $\mu_X=\mathbb{E}(X)$。當 $\mathbb{E}(X^2)$ 存在時，

$$
\begin{aligned}
\mathbb{E}\big[(X-a)^2\big]
&=
\mathbb{E}\big[(X-\mu_X+\mu_X-a)^2\big] \\[0.35em]
&=
\mathbb{E}\big[(X-\mu_X)^2\big]
+2(\mu_X-a)\mathbb{E}(X-\mu_X)
+(\mu_X-a)^2 \\[0.35em]
&=
\mathbb{E}\big[(X-\mu_X)^2\big]+(\mu_X-a)^2
\end{aligned}
$$

由 $\mathbb{E}(X-\mu_X)=0$，交叉項為 $0$。第一項與 $a$ 無關，第二項在 $a=\mu_X$ 時達到最小，因此期望值是使 $\mathbb{E}[(X-a)^2]$ 最小的常數。

這個性質會自然銜接到下一篇的變異數。變異數正是把 $a$ 選成最合適的代表值 $\mu_X$ 後，所剩下的平均平方離差。

## 期望值可能不存在

期望值雖然常被稱為平均數，但不是每個隨機變數都有有限期望值。若尾端機率下降得太慢，遠處的大數值仍可能對平均造成不可忽略的影響。此時相關的加總或積分可能發散。

因此，定義中的絕對可積條件分別為

$$
\begin{aligned}
\sum_{x\in\mathcal{R}_X}|x|p_X(x) &< \infty, &&\text{若 $X$ 為離散型隨機變數} \\
\int_{-\infty}^{\infty}|x|f_X(x)\,dx &< \infty, &&\text{若 $X$ 具有 pdf $f_X$} \\
\sum_{x\in A}|x|\mathbb{P}(X=x)+\int_{-\infty}^{\infty}|x|f_X^{(c)}(x)\,dx &< \infty, &&\text{若 $X$ 為混合型隨機變數}
\end{aligned}
$$

這個條件並非技術上的多餘限制。它的作用在於確保正負兩側的貢獻能被合理合併，避免出現無法定義的 $\infty-\infty$。

## 本篇小結

期望值是隨機變數在數線上的平均位置。離散型隨機變數以 pmf 作加權平均，即 $\mathbb{E}(X)=\sum_{x\in\mathcal{R}_X}x p_X(x)$；具有 pdf 的連續型隨機變數則以 $\mathbb{E}(X)=\int_{-\infty}^{\infty}x f_X(x)\,dx$ 作積分平均。混合型隨機變數把單點加總與連續部分積分相加。

若需要計算 $X$ 的函數，也可直接使用 $\mathbb{E}[g(X)]$。下一篇[變異數與標準差](/teaching-topics/variance-standard-deviation/)會在期望值的基礎上討論分散程度，說明除了平均位置之外，還需要衡量隨機變數離開期望值的程度。

## 參考文獻與延伸閱讀

- 黃文璋，2003，《機率論》，初版，華泰文化。
- 黃文璋，2003，《數理統計》，初版，華泰文化。
- 楊維哲，1978，〈機率一講〉，《數學傳播》2(3)。
- Patrick Billingsley. 1995. *Probability and Measure*. 3rd ed. Wiley.
- William Feller. 1968. *An Introduction to Probability Theory and Its Applications*. Vol. 1, 3rd ed. Wiley.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Sheldon M. Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Joseph K. Blitzstein and Jessica Hwang. 2019. *Introduction to Probability*. 2nd ed. Chapman and Hall/CRC.
