---
title: "變異數與標準差"
subtitle: "Variance and Standard Deviation"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 6
order: 206
permalink: /teaching-topics/variance-standard-deviation/
date: 2026-06-06
published: true
excerpt: "期望值給出隨機變數的平均位置。變異數則衡量隨機變數離開此平均位置的平均程度，標準差再把單位還原回原來的尺度。"
---

[上一篇文章](/teaching-topics/expected-value-random-variables/)討論期望值。期望值給出的是隨機變數的平均位置。不過，只知道平均位置仍然不夠。兩個隨機變數可能具有相同的期望值，卻一個大多集中在平均值附近，另一個常常離平均值很遠。

因此，除了平均位置之外，我們還需要衡量隨機變數在此位置附近的分散程度。這個量數稱為**變異數 (variance)**。

<figure class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/variance-same-mean-different-spread.svg" alt="兩個分佈有相同的期望值，但分散程度不同。">
  <figcaption><span class="topic-figure__label">Fig. 2.14.</span> 兩個分佈可以有相同的期望值，卻有不同的分散程度。紅色曲線較分散，綠色曲線較集中；前者對應的變異數較大。</figcaption>
</figure>

## 離差與平方

令 $\mu_X=\mathbb{E}(X)$。若 $X$ 取到某個數值，則 $X-\mu_X$ 表示此數值離開平均位置的差距。這個差距稱為**離差 (deviation)**。

直接把離差取平均並不能衡量分散程度，因為正離差與負離差會互相抵消。事實上，只要期望值存在，就有

$$
\mathbb{E}(X-\mu_X)=0
$$

因此，若要把「離平均值有多遠」整理成一個非負量，最常見的方式是先取平方，再求期望值。這便導向變異數的定義。

## 變異數

<div class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.7</div>

令 $X$ 為隨機變數，且 $\mu_X=\mathbb{E}(X)$。若 $\mathbb{E}(X^2)<\infty$，則稱

$$
\mathrm{Var}(X)
=
\mathbb{E}\big[(X-\mu_X)^2\big]
$$

為 $X$ 的**變異數 (variance)**。變異數也常記為 $\sigma_X^2$。

若 $X$ 為離散型隨機變數，PMF 為 $p_X$，則

$$
\mathrm{Var}(X)
=
\sum_{x\in\mathcal{R}_X}(x-\mu_X)^2p_X(x)
$$

若 $X$ 為連續型隨機變數，PDF 為 $f_X$，則

$$
\mathrm{Var}(X)
=
\int_{-\infty}^{\infty}(x-\mu_X)^2f_X(x)\,dx
$$

</div>

變異數本身也是一種期望值。它不是直接平均 $X$，而是平均 $(X-\mu_X)^2$。換言之，變異數是**離差平方的期望值**，可用來描述隨機變數平均而言離開期望值的程度。

<div class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 2.8</div>

平方有兩個作用。第一，平方後的離差不會發生正負相消。第二，較大的離差在平方後會被放大，因此變異數對遠離平均值的取值相當敏感。

這個性質有利也有弊。若遠離平均值的結果本來就值得特別注意，平方會把它清楚呈現出來。若資料中存在極端值，變異數也會受到較明顯的影響。這也是後續統計學會另外討論其他分散量數的原因之一。
</div>

<div class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.7 (Same Mean, Different Variance)</div>

令 $X$ 與 $Y$ 為兩個離散型隨機變數，其分佈可寫為

$$
\mathbb{P}(X=0)=\mathbb{P}(X=2)=\frac{1}{2}
$$

以及

$$
\mathbb{P}(Y=0.5)=\mathbb{P}(Y=1.5)=\frac{1}{2}
$$

兩者皆以 $1$ 為對稱中心，所以期望值同為 $1$。然而，$X$ 的取值離 $1$ 較遠，$Y$ 的取值離 $1$ 較近。由定義可得

$$
\mathrm{Var}(X)
=
(0-1)^2\cdot\frac{1}{2}
+(2-1)^2\cdot\frac{1}{2}
=1
$$

而

$$
\mathrm{Var}(Y)
=
(0.5-1)^2\cdot\frac{1}{2}
+(1.5-1)^2\cdot\frac{1}{2}
=\frac{1}{4}
$$

因此，即使兩個隨機變數有相同的期望值，它們也可能有不同的分散程度。
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個例子選用離散型隨機變數，是因為有限個取值能讓計算一眼看清楚。變異數的定義並不侷限於離散型；若 $X$ 為連續型隨機變數，則同樣是計算離差平方的期望值，只是由 PMF 加總改為用 PDF 積分。
</div>

## 變異數的計算公式

由定義直接計算變異數有時不太方便。展開平方後，可得到另一個常用公式。

<div class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Proposition 2.7 (Computing Variance)</div>

若 $X$ 的變異數存在，則

$$
\mathrm{Var}(X)
=
\mathbb{E}(X^2)-[\mathbb{E}(X)]^2
$$

</div>

證明可由定義直接展開。令 $\mu_X=\mathbb{E}(X)$，並使用前一篇整理的[期望值的線性關係](/teaching-topics/expected-value-random-variables/#期望值的線性關係)，則

$$
\begin{aligned}
\mathrm{Var}(X)
&=
\mathbb{E}\big[(X-\mu_X)^2\big] \\[0.45em]
&=
\mathbb{E}(X^2-2\mu_X X+\mu_X^2) \\[0.45em]
&=
\mathbb{E}(X^2)-2\mu_X\mathbb{E}(X)+\mu_X^2 \\[0.45em]
&=
\mathbb{E}(X^2)-[\mathbb{E}(X)]^2
\end{aligned}
$$

這個公式可記為「平方的期望值，減去期望值的平方」。在許多計算中，先求 $\mathbb{E}(X)$ 與 $\mathbb{E}(X^2)$，再相減，往往比直接套用離差平方更簡潔。

<div class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.8 (Variance from $\mathbb{E}(X^2)$)</div>

延續上一篇文章 [Example 2.5 的抽球例子](/teaching-topics/expected-value-random-variables/#example-25)。箱中有四顆編號 $0,1,2,3$ 的球，從中一次抽取兩顆球，不考慮抽取順序，令 $X$ 表示兩顆球的號碼總和。該例中 $\mathbb{E}(X)=3$，且 PMF 為

| $x$ | 1 | 2 | 3 | 4 | 5 |
| --- | --- | --- | --- | --- | --- |
| $p_X(x)$ | $1/6$ | $1/6$ | $1/3$ | $1/6$ | $1/6$ |

由此可先計算

$$
\mathbb{E}(X^2)
=
1^2\cdot\frac{1}{6}
+2^2\cdot\frac{1}{6}
+3^2\cdot\frac{1}{3}
+4^2\cdot\frac{1}{6}
+5^2\cdot\frac{1}{6}
=
\frac{32}{3}
$$

故

$$
\mathrm{Var}(X)
=
\mathbb{E}(X^2)-[\mathbb{E}(X)]^2
=
\frac{32}{3}-9
=
\frac{5}{3}
$$

</div>

## 標準差

變異數採用平方，因此其單位也是原隨機變數單位的平方。例如 $X$ 以公分為單位，$\mathrm{Var}(X)$ 的單位便是平方公分。為了回到原本的尺度，通常會再取平方根，得到**標準差 (standard deviation)**。

<div class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.8</div>

若 $X$ 的變異數存在，則定義 $X$ 的**標準差 (standard deviation)** 為

$$
\sigma_X
=
\sqrt{\mathrm{Var}(X)}
$$

</div>

標準差與 $X$ 有相同的單位，因此在描述實際情境時通常較容易解讀。變異數在代數推導中較方便，標準差則較適合回到原尺度解釋分散程度。

## 平移與伸縮

變異數與標準差有幾個基本性質。這些性質都與「分散程度」的意義相符。

<div class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Proposition 2.8</div>

若 $a,b$ 為常數，且 $X$ 的變異數存在，則

$$
\mathrm{Var}(X)\geq 0
$$

$$
\mathrm{Var}(aX+b)=a^2\mathrm{Var}(X)
$$

因此

$$
\sigma_{aX+b}=|a|\,\sigma_X
$$

</div>

非負性可由定義中的加總或積分形式看出，因為離差平方與機率權重皆非負。至於平移與伸縮，令

$$
Y=aX+b
$$

由期望值的線性關係可知

$$
\mu_Y
=
\mathbb{E}(Y)
=
a\mu_X+b
$$

因此

$$
\begin{aligned}
\mathrm{Var}(aX+b)
&=
\mathbb{E}\big[(Y-\mu_Y)^2\big] \\[0.45em]
&=
\mathbb{E}\big[(aX+b-a\mu_X-b)^2\big] \\[0.45em]
&=
\mathbb{E}\big[a^2(X-\mu_X)^2\big] \\[0.45em]
&=
a^2\mathrm{Var}(X)
\end{aligned}
$$

再由標準差的定義，可得

$$
\sigma_{aX+b}
=
\sqrt{\mathrm{Var}(aX+b)}
=
|a|\,\sigma_X
$$

平移不會改變分散程度。若把每個取值都加上同一個常數 $b$，整個分佈只是往左或往右移動，離平均值的相對距離並未改變。

伸縮則會改變分散程度。若把 $X$ 乘上 $a$，離差也會乘上 $a$，離差平方便會乘上 $a^2$。因此，變異數具有平方伸縮性；標準差取平方根後，則具有絕對伸縮性。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

本篇討論的是隨機變數本身的變異數與標準差，屬於母體層次的量數。之後進入統計推論時，還會遇到樣本變異數與樣本標準差。樣本版本會多出自由度與估計量的討論，屆時再另外處理。
</div>

## 本篇小結

期望值說明隨機變數的平均位置，變異數則衡量隨機變數離開此平均位置的平均程度。若 $\mu_X=\mathbb{E}(X)$，則

$$
\mathrm{Var}(X)
=
\mathbb{E}\big[(X-\mu_X)^2\big]
$$

變異數也可用下式計算。

$$
\mathrm{Var}(X)
=
\mathbb{E}(X^2)-[\mathbb{E}(X)]^2
$$

標準差為

$$
\sigma_X=\sqrt{\mathrm{Var}(X)}
$$

變異數適合代數運算，標準差則把單位還原到與隨機變數相同的尺度。後續處理常見分佈、抽樣分佈與統計推論時，期望值與變異數會是最常使用的兩個量數。

## 參考文獻與延伸閱讀

- 黃文璋，《數理統計》，第 1 章第 6 節「期望值、變異數及拉普拉斯轉換」。
- Patrick Billingsley, *Probability and Measure*, 3rd ed., Wiley, 1995, chapters on integration, expectation, and moments.
- William Feller, *An Introduction to Probability Theory and Its Applications*, Volume I, 3rd ed., Wiley, 1968, chapters on mathematical expectation and variance.
- George Casella and Roger L. Berger, *Statistical Inference*, 2nd ed., Duxbury, 2002, sections on expected values, variances, and moments.
- Sheldon M. Ross, *A First Course in Probability*, 10th ed., Pearson, 2019, chapters on expectation and variance.
- Joseph K. Blitzstein and Jessica Hwang, *Introduction to Probability*, 2nd ed., CRC Press, 2019, chapters on expectation, variance, and standard deviation.
