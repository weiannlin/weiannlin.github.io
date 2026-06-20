---
title: "分位數、百分位數與中位數"
subtitle: "Quantiles, Percentiles and Median"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 9
order: 209
permalink: /teaching-topics/quantiles-and-median/
date: 2026-06-13
published: true
excerpt: "標準化描述個體離平均位置幾個標準差。分位數與百分位數則從 CDF 出發，找出使累積機率達到指定比例的位置。中位數是其中最常用的特例。"
---

[上一篇文章](/teaching-topics/linear-transformations-standardization/)討論標準化與 z-score。z-score 處理的是單一觀察值相對於其所屬分配的位置，說明該觀察值離平均位置幾個標準差。

本篇改從整個分配來看位置。若想知道一個分配的下方四分之一、中央位置或上方四分之一落在哪裡，就需要使用**分位數 (quantile)**。若將比例改用百分比表示，便得到常見的**百分位數 (percentile)**。分位數不是先固定一個 $x$ 再求機率，而是先固定一個機率比例，再回頭找出對應的數線位置。

## 累積機率與分位數

累積分配函數定義為

$$
F_X(x)=\mathbb{P}(X\leqslant x)
$$

因此，$F_X(x)$ 說明的是「累積到 $x$ 為止」已有多少機率。分位數要描述的，是當累積比例被指定後，哪些數線位置可以把機率分成相應的左右兩側。給定一個比例 $p$，我們希望找出一個位置，使得左側累積機率至少達到 $p$，而右側機率也至少保留 $1-p$。

<div id="definition-211" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.11</div>

令 $0<p<1$。若實數 $q$ 滿足

$$
\mathbb{P}(X\leqslant q)\geqslant p
$$

且

$$
\mathbb{P}(X\geqslant q)\geqslant 1-p
$$

則稱 $q$ 為 $X$ 的 **$p$ 分位數 ($p$-quantile)**。

</div>

<div class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 2.10</div>

令 $X$ 的可能取值為 $0,1,4,5$，且各自機率皆為 $1/4$。若取 $p=1/2$，則任何 $q\in[1,4]$ 都滿足

$$
\mathbb{P}(X\leqslant q)\geqslant \frac{1}{2}
$$

且

$$
\mathbb{P}(X\geqslant q)\geqslant \frac{1}{2}
$$

因此，$[1,4]$ 中的每一個點都可作為 $1/2$ 分位數。特別地，$2$ 與 $3$ 並不是 $X$ 的可能取值，仍然可以是這個意義下的分位數。分位數描述的是把機率分在左右兩側的位置，不必然要求該位置本身是隨機變數實際可能取到的值。若採用下方的分位函數作為代表值，則此例會選到左端點 $x_{0.5}=1$。
</div>

由此可知，分位數未必唯一。為了指定一個明確的代表值，常採用分位函數

$$
x_p=F_X^{-1}(p)=\inf\{x\in\mathbb{R}\mid F_X(x)\geqslant p\}
$$

這裡的 $F_X^{-1}$ 稱為分位函數，並不是一般意義下必須一對一才存在的反函數。這個 $x_p$ 會選取第一個使 CDF 達到或超過 $p$ 的位置。若 $F_X$ 是連續且嚴格遞增的函數，則 $x_p$ 就是使

$$
F_X(x)=p
$$

成立的那個 $x$。若 $F_X$ 有平坦區段或跳躍，分位函數仍提供一個固定且明確的選取方式。

若比例寫成 $p=k/r$，則相應的位置也可稱為第 $k$ 個 $r$ 分位數，記作 $q_k$。四分位數、十分位數與百分位數都屬於這個說法的特例。

<figure class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/quantile-from-cdf.svg?v=xp-notation" alt="從 CDF 取得分位函數。先固定累積機率 p，再找出數線上的 x_p。">
  <figcaption><span class="topic-figure__label">Fig. 2.16.</span> 分位函數是從 CDF 反向取得的位置。先固定累積機率 $p$，再找出第一個使 $F_X(x)\geqslant p$ 的位置 $x_p=F_X^{-1}(p)$。</figcaption>
</figure>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這裡討論的是分配本身的分位數。若手上只有一組樣本資料，則會牽涉到樣本分位數的估計方法。不同軟體對樣本分位數可能採用不同插值規則，這屬於統計計算上的問題，這裡先不處理。
</div>

## 分位數與百分位數

幾個分位數特別常用。若 $p=0.25$，則 $x_{0.25}$ 稱為第一四分位數，常記為 $Q_1$；若 $p=0.5$，則 $x_{0.5}$ 可作為中位數的一個明確代表，常記為 $Q_2$；若 $p=0.75$，則 $x_{0.75}$ 稱為第三四分位數，常記為 $Q_3$。若中位數唯一，則 $Q_2=\eta_X$。

| 名稱 | 記號 | 說明 |
|---|:---:|---|
| 第一四分位數 | $Q_1=x_{0.25}$ | 累積機率達到四分之一的位置 |
| 中位數的一個代表 | $Q_2=x_{0.5}$ | 第一個使累積機率達到二分之一的位置 |
| 第三四分位數 | $Q_3=x_{0.75}$ | 累積機率達到四分之三的位置 |

同一個位置若以百分比表示，則稱為第 $100p$ 百分位數。例如 $x_{0.9}$ 可稱為第 $90$ 百分位數，也可記為 $P_{90}$。百分位數在解釋測驗成績、身高體重常模或大型資料摘要時很常見，因為它直接說明一個數值在整體分配中大約位於哪個比例位置。

臺灣國中會考與相關模擬測驗、升學落點討論中常見的 **PR 值**，指的是 **percentile rank**，中文常稱為百分等級。若某次數學測驗的成績為 $s$，且其 PR 值約為 $90$，意思是以同次測驗的考生作為參照群體時，約有九成考生的成績不高於 $s$。用本節的記號來看，若令 $X$ 表示該群考生成績，則 PR $90$ 對應到第 $90$ 百分位數附近，也就是 $s$ 約位於 $P_{90}=x_{0.9}$。

換句話說，百分位數是從比例回推數線位置；PR 值則是拿一個已知成績，回頭表示它在群體中的累積比例。實際成績通常是離散的，且同分人數可能很多，因此 PR 值會依考試單位採用的同分與取整規則計算。

同理，十分位數常記為 $D_k$，百分位數常記為 $P_r$。例如在唯一的情形下，$P_{50}=D_5=Q_2=\eta_X$。

<div id="example-214" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.14 (Uniform Distribution)</div>
<!-- ref-point: probability-integral-transform should cross-reference example-214. -->

令 $X$ 在 $(0,1)$ 上服從均勻分配。此時

$$
F_X(x)=x,
\qquad 0<x<1
$$

因此，對任意 $0<p<1$，皆有

$$
x_p=F_X^{-1}(p)=p
$$

特別地，

$$
Q_1=x_{0.25}=0.25,
\qquad
Q_2=x_{0.5}=0.5,
\qquad
Q_3=x_{0.75}=0.75
$$

這個例子最單純。累積機率與位置本身相同，所以分位數也直接等於該比例。
</div>

## 中位數

中位數是最常見的位置量數之一。直觀上，中位數把分配切成左右兩半，使得至少一半的機率落在它左側，也至少一半的機率落在它右側。

<div id="definition-212" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.12</div>

若實數 $\eta_X$ 滿足

$$
\mathbb{P}(X\leqslant \eta_X)\geqslant\frac{1}{2}
$$

且

$$
\mathbb{P}(X\geqslant \eta_X)\geqslant\frac{1}{2}
$$

則稱 $\eta_X$ 為 $X$ 的**中位數 (median)**。

</div>

若中位數唯一，通常可直接寫作

$$
\eta_X=x_{0.5}=F_X^{-1}(1/2)
$$

不過，在離散型分配中，中位數未必唯一。此時 $x_{0.5}$ 是一個常用且明確的選擇，因為它選取第一個使累積機率達到 $1/2$ 的位置。

<div id="example-215" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.15 (A Fair Die)</div>

令 $X$ 表示投擲一顆公平骰子所得點數。則

$$
\mathbb{P}(X=k)=\frac{1}{6},
\qquad k=1,2,\ldots,6
$$

由 CDF 可得

$$
Q_1=x_{0.25}=2,
\qquad
Q_2=x_{0.5}=3,
\qquad
Q_3=x_{0.75}=5
$$

以 $p=0.5$ 為例，依分位函數定義可得

$$
\{x\in\mathbb{R}\mid F_X(x)\geqslant 1/2\}=[3,\infty)
$$

因此

$$
x_{0.5}=\inf[3,\infty)=3
$$

另一方面，若把 $[3,4]$ 之間的任何一個數代入中位數定義，都會得到

$$
\mathbb{P}(X\leqslant \eta_X)\geqslant \frac{1}{2},
\qquad
\mathbb{P}(X\geqslant \eta_X)\geqslant \frac{1}{2}
$$

因此任何 $\eta_X\in[3,4]$ 都可視為中位數。由此可再次印證，分位數與中位數都可能面臨不唯一的情況，透過分位函數 $x_{0.5}$ 所找到的中位數只不過是「其中一個」而已。
</div>

## 中位數與平均數

中位數與期望值都可用來描述分配的位置，但兩者並不相同。期望值是依機率權重計算出來的平均位置；中位數則只看累積機率何時達到一半。

<div class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 2.11</div>

令 $X$ 滿足

$$
\mathbb{P}(X=0)=0.99,
\qquad
\mathbb{P}(X=1000)=0.01
$$

則

$$
\mathbb{E}(X)=0(0.99)+1000(0.01)=10
$$

但其中位數為 $0$。原因是 $X=0$ 這個點已經累積了 $99\%$ 的機率，因此累積機率達到一半的位置早已在 $0$。

這個例子說明，平均數會受到少數很大的數值影響；中位數則更直接反映「有一半機率落在何處之前」。
</div>

## 本篇小結

給定 $0<p<1$，若 $q$ 使 $\mathbb{P}(X\leqslant q)\geqslant p$ 且 $\mathbb{P}(X\geqslant q)\geqslant 1-p$，則 $q$ 稱為 $X$ 的 $p$ 分位數。分位數可能不唯一，因此常用下列方式指定一個明確代表值。

$$
x_p=F_X^{-1}(p)=\inf\{x\in\mathbb{R}\mid F_X(x)\geqslant p\}
$$

中位數是最常用的分位數之一，常以 $\eta_X$ 表示。它描述分配的中央位置，但不一定等於期望值。期望值依機率權重作平均，中位數則依累積機率把分配切成兩半。

標準化把單一觀察值轉成離平均位置幾個標準差；分位數與百分位數則描述整個分配在不同累積比例下的位置。常用記號包括四分位數 $Q_1,Q_2,Q_3$、十分位數 $D_k$、百分位數 $P_r$ 與中位數 $\eta_X$。

第一四分位數與第三四分位數也會引出四分位距與盒鬚圖。不過，盒鬚圖主要用於整理樣本資料，屬於敘述統計的範圍。這裡先留作伏筆；日後討論敘述統計時，可再回頭比較機率分配中的分位數與樣本資料中的分位數。

## 參考文獻與延伸閱讀

- 黃文璋，2003，《數理統計》，初版，華泰文化。
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Sheldon M. Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Patrick Billingsley. 1995. *Probability and Measure*. 3rd ed. Wiley.
- Rob J. Hyndman and Yanan Fan. 1996. “Sample Quantiles in Statistical Packages.” *The American Statistician* 50 (4): 361–365.
