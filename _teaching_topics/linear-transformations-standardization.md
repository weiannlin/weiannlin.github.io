---
title: "線性轉換與標準化"
subtitle: "Linear Transformations and Standardization"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 8
order: 208
permalink: /teaching-topics/linear-transformations-standardization/
date: 2026-06-12
published: true
excerpt: "線性轉換會平移或伸縮隨機變數的尺度。標準化則先扣掉平均位置，再除以標準差，使不同尺度下的數值可以用 z-score 比較相對位置。"
---

[上一篇文章](/teaching-topics/variance-standard-deviation/)討論變異數與標準差。期望值描述分配的平均位置，標準差描述分配的變異程度。有了這兩個量，便能進一步討論一個常見問題。

若一名學生的數學成績為 $60$ 分，自然成績為 $80$ 分，哪一科的相對表現較高？只看原始分數時，自然成績比較高。不過，若數學考試整體偏難，而自然考試整體偏易，這個判斷就未必恰當。此時需要知道各科成績分配的平均位置與變異程度，才能把兩個不同尺度下的數值放在同一個基準上比較。

這個過程稱為**標準化 (standardization)**。在正式定義之前，我們先整理線性轉換對期望值與標準差的影響。

## 線性轉換

令 $X$ 為隨機變數，並考慮

$$
Y=aX+b
$$

其中 $a,b$ 為常數。這種形式稱為 $X$ 的**線性轉換 (linear transformation)**。其中 $b$ 會造成平移，$a$ 會造成伸縮。若 $a<0$，數線方向還會左右反轉。

<div id="proposition-210" class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Proposition 2.10</div>

若 $X$ 的期望值與變異數皆存在，且 $Y=aX+b$，則有以下關係

$$
\begin{aligned}
\mathbb{E}(Y)
&=
a\mathbb{E}(X)+b,\\[0.45em]
\mathrm{Var}(Y)
&=
a^2\mathrm{Var}(X),\\[0.45em]
\mathrm{SD}(Y)
&=
\lvert a\rvert\,\mathrm{SD}(X)
\end{aligned}
$$

</div>

第一個式子是 [Proposition 2.6](/teaching-topics/expected-value-random-variables/#期望值的線性關係) 的直接應用。第二個與第三個式子則承接 [Proposition 2.8](/teaching-topics/variance-standard-deviation/#平移與伸縮)。

直觀上，平移只會把整個分配往左或往右搬動，不改變分散程度；伸縮則會同步改變所有離差，因此標準差也會依伸縮倍數的絕對值改變。

<div class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.11 (Changing Units)</div>

設 $X$ 表示攝氏溫度，並令 $Y$ 表示華氏溫度。兩者關係為

$$
Y=\frac{9}{5}X+32
$$

若 $\mathbb{E}(X)=20$ 且 $\mathrm{SD}(X)=3$，則

$$
\mathbb{E}(Y)
=
\frac{9}{5}\cdot 20+32
=
68
$$

而

$$
\mathrm{SD}(Y)
=
\left\lvert\frac{9}{5}\right\rvert\mathrm{SD}(X)
=
\frac{27}{5}
=
5.4
$$

華氏溫度的平均位置受到平移與伸縮同時影響，但標準差只受到伸縮倍數影響。這正是因為標準差處理的是離平均位置的距離，而不是平均位置本身。
</div>

## 標準化

若 $X$ 的期望值為 $\mu_X$，標準差為 $\sigma_X>0$，則可將 $X$ 轉換為

$$
Z=\frac{X-\mu_X}{\sigma_X}
$$

這個轉換先扣掉平均位置，再除以標準差。前者使平均位置移到 $0$，後者使一個標準差成為新的單位。至於標準化後的數值如何解讀，等到後面討論常態分配與經驗法則時，再配合圖形說明會更自然。現階段，讀者只需先知道，標準化是把原始數值改寫成以標準差為單位的相對位置。

<div class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.10</div>

令 $X$ 為隨機變數，且 $\mathbb{E}(X)=\mu_X$、$\mathrm{SD}(X)=\sigma_X>0$。隨機變數

$$
Z=\frac{X-\mu_X}{\sigma_X}
$$

稱為 $X$ 的**標準化隨機變數 (standardized random variable)**。

若觀察到 $X=x$，則

$$
z=\frac{x-\mu_X}{\sigma_X}
$$

稱為此觀察值的 **z-score**。
</div>

標準化後的隨機變數有很簡單的期望值與標準差。

<div class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Proposition 2.11</div>

若

$$
Z=\frac{X-\mu_X}{\sigma_X}
$$

其中 $\sigma_X>0$，則

$$
\mathbb{E}(Z)=0,
\qquad
\mathrm{Var}(Z)=1,
\qquad
\mathrm{SD}(Z)=1
$$

</div>

這是 [Proposition 2.10](#proposition-210) 的直接應用。因為

$$
Z
=
\frac{1}{\sigma_X}X
-
\frac{\mu_X}{\sigma_X}
$$

所以

$$
\mathbb{E}(Z)
=
\frac{1}{\sigma_X}\mathbb{E}(X)
-
\frac{\mu_X}{\sigma_X}
=0
$$

且

$$
\mathrm{Var}(Z)
=
\frac{1}{\sigma_X^2}\mathrm{Var}(X)
=1
$$

## z-score 的意義

z-score 的重點在於，它把原始數值改寫成「離平均位置幾個標準差」。若 $z=2$，表示該觀察值高於平均位置 $2$ 個標準差；若 $z=-1.5$，表示該觀察值低於平均位置 $1.5$ 個標準差。

<div class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.12 (Comparing Two Exam Scores)</div>

某學生數學成績為 $60$ 分，自然成績為 $80$ 分。假設數學成績的平均數為 $50$，標準差為 $5$；自然成績的平均數為 $70$，標準差為 $20$。

若只看原始分數，自然成績 $80$ 分高於數學成績 $60$ 分。不過，若計算 z-score，則數學成績對應

$$
z_{\mathrm{math}}
=
\frac{60-50}{5}
=2
$$

自然成績對應

$$
z_{\mathrm{science}}
=
\frac{80-70}{20}
=0.5
$$

因此，若比較的是各自群體中的相對位置，數學成績反而較高。原始分數說明的是同一尺度上的大小；z-score 說明的是相對於各自分配的位置。
</div>

<div class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 2.9</div>

標準化處理的是單一觀察值在其所屬分配中的位置。它要做的事情很單純，先把平均位置設為新的原點，再把標準差設為新的單位。經過這個轉換後，z-score 便能說明該觀察值離平均位置有幾個標準差。

這也說明了為何 z-score 適合比較不同尺度下的個體位置。身高、考試成績、收入、壽命等變數本來有不同單位與不同分散程度。若直接比較原始數字，往往會把單位與尺度混在一起。標準化後，我們比較的是離平均位置有幾個標準差。
</div>

## 反標準化

標準化並沒有丟掉原始尺度的資訊。若

$$
Z=\frac{X-\mu_X}{\sigma_X}
$$

則可移項得到

$$
X=\mu_X+\sigma_X Z
$$

這個式子稱為**反標準化 (inverse standardizing)**。它說明若知道一個位置的 z-score，也知道原分配的平均位置與標準差，便可回到原始尺度。

<div class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.13 (Back to the Original Scale)</div>

某科考試成績的平均數為 $70$，標準差為 $8$。若某學生的 z-score 為 $1.5$，則其原始分數為

$$
x
=
70+8(1.5)
=82
$$

這個計算表示，該學生的成績高於平均數 $1.5$ 個標準差，換回原尺度後即為 $82$ 分。
</div>

## 本篇小結

線性轉換 $Y=aX+b$ 會改變隨機變數的平均位置與尺度。期望值會隨著平移與伸縮改變，標準差則只受到伸縮倍數影響。

標準化是線性轉換的一個特別重要的例子。

$$
Z=\frac{X-\mu_X}{\sigma_X}
$$

它先扣掉平均位置，再除以標準差，使得標準化後的隨機變數滿足

$$
\mathbb{E}(Z)=0,
\qquad
\mathrm{SD}(Z)=1
$$

z-score 適合用來描述個體在所屬分配中的相對位置。[下一篇文章](/teaching-topics/quantiles-and-median/)會改從 CDF 出發，討論分位數、百分位數與中位數如何描述分配位置。

## 參考文獻與延伸閱讀

- 黃文璋，2003，《機率論》，初版，華泰文化。
- 黃文璋，2003，《數理統計》，初版，華泰文化。
- William Feller. 1968. *An Introduction to Probability Theory and Its Applications*. Vol. 1, 3rd ed. Wiley.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Sheldon M. Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Joseph K. Blitzstein and Jessica Hwang. 2019. *Introduction to Probability*. 2nd ed. Chapman and Hall/CRC.
