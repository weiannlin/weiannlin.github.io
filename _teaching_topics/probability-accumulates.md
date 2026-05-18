---
title: "累積分配函數如何累積機率"
subtitle: "How Distribution Functions Accumulate Probability"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 2
order: 202
permalink: /teaching-topics/probability-accumulates/
date: 2026-05-17
published: true
excerpt: "CDF 描述隨機變數不超過門檻 x 的事件機率；離散型靠單點機率加總，連續型靠密度面積積分。"
---

[上一篇文章](/teaching-topics/random-variables-from-sample-space-to-real-line/)把隨機變數定義為從樣本空間到實數線的函數。一旦有了這個對應，便可固定一個門檻 $x$，計算映射過去的數字落在 $x$ 以下的總機率。

這個累積量稱為累積分配函數 (cumulative distribution function, CDF)，也簡稱為分配函數 (distribution function, DF)。

$$
F_X(x)=\mathbb{P}(X\leq x)
$$

以下各節都以此定義為準。離散型與連續型的差別，不在於 CDF 的定義改變，而在於事件 $\lbrace X\leq x\rbrace$ 的機率如何被計算與表示。

## 累積分配函數的基本性質

先從函數觀點看 $F_X$。輸入是實數 $x$，輸出是事件 $\lbrace X\leq x\rbrace$ 的機率。下圖以兩條平行數線表示此關係。每個點的位置代表 $X(\omega_i)$ 的數值；當門檻由 $x_1$ 移到 $x_2$，紅色區段變長，原本已被收入的樣本點仍然保留，只會額外納入新的樣本點。

<figure class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/cdf-nested-thresholds.svg" alt="兩條平行數線展示 x1 小於等於 x2 時，事件 X 小於等於 x1 被包含於事件 X 小於等於 x2。">
  <figcaption><span class="topic-figure__label">Fig. 2.2.</span> 若 $x_1\leq x_2$，則所有滿足 $X(\omega)\leq x_1$ 的樣本點，也必定滿足 $X(\omega)\leq x_2$。大小關係發生在 $X(\omega)$ 的數值上，事件之間因此形成包含關係。</figcaption>
</figure>

由事件的包含關係可知，若 $x_1\leq x_2$，則

$$
\lbrace X\leq x_1\rbrace\subset \lbrace X\leq x_2\rbrace
$$

故 $F_X$ 不會隨 $x$ 增大而下降。

<div class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Proposition 2.1 (Basic Properties of a CDF)</div>

令 $X$ 為一個隨機變數，$F_X(x)=\mathbb{P}(X\leq x)$。則 $F_X$ 滿足下列性質。

(1) $F_X$ 為單調不減函數。

(2) 對任意 $x\in\mathbb{R}$，皆有

$$
0\leq F_X(x)\leq 1
$$

(3) $F_X$ 滿足

$$
\lim_{x\to -\infty}F_X(x)=0,\qquad
\lim_{x\to \infty}F_X(x)=1
$$

(4) $F_X$ 右連續。
</div>

前三點由機率性質直接得到。第四點是 CDF 的標準正則性條件，也是後續用 CDF 描述分佈時不可缺少的性質。

## 離散型，靠單點機率加總

若 $X$ 的可能取值至多可數，且所有機率都集中在這些取值上，則稱 $X$ 為**離散型隨機變數 (discrete random variable)**。此時定義

$$
p_X(t)=\mathbb{P}(X=t)
$$

並稱 $p_X$ 為**機率質量函數**，英文全名為 probability mass function，常簡記為 PMF。

對離散型隨機變數而言，事件 $\lbrace X\leq x\rbrace$ 是由所有不超過 $x$ 的單點事件合併而成。因此

$$
F_X(x)
=
\mathbb{P}(X\leq x)
=
\sum_{t\leq x}p_X(t)
$$

此加總只取 $X$ 可能取到且不超過 $x$ 的那些 $t$。離散型 CDF 因而是門檻左側單點機率的累積。

<div class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.1 (A Die Roll)</div>

投擲一顆公正骰子一次，令 $X$ 表示點數。則

$$
\mathbb{P}(X=t)=\frac{1}{6},\qquad t=1,\ldots,6
$$

若 $x=3$，則 $\lbrace X\leq 3\rbrace=\lbrace 1,2,3\rbrace$，故

$$
F_X(3)
=
\mathbb{P}(X\leq 3)
=
\frac{1}{6}+\frac{1}{6}+\frac{1}{6}
=
\frac{1}{2}
$$

若 $3<x<4$，門檻雖然變大，但沒有新增任何可能點數，因此 $F_X(x)$ 仍等於 $1/2$。這也是離散型 CDF 呈現階梯狀的原因。
</div>

<div class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 2.2</div>

在 Example 2.1 中，$X$ 只能取 $1,2,\ldots,6$。這個集合是 $X$ 的**值域 (range)**。但 CDF 的輸入 $x$ 是數線上的門檻，可以是任意實數，而不必剛好等於骰子點數。

例如 $F_X(3.4)$ 仍然有意義。此時

$$
\lbrace X\leq 3.4\rbrace=\lbrace 1,2,3\rbrace
$$

所以

$$
F_X(3.4)=\mathbb{P}(X\leq 3.4)=\frac{1}{2}
$$

只有當門檻跨過下一個可能取值，例如從 $3.9$ 移到 $4$，CDF 才會往上跳。
</div>

<figure class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/dice-pmf-threshold.svg" alt="公正骰子的 PMF 棒棒糖圖。點數 1, 2, 3 的機率質量被標成紅色，門檻 x=3.4 位於 3 與 4 之間。">
  <figcaption><span class="topic-figure__label">Fig. 2.3.</span> 即使門檻 $x=3.4$ 不是骰子點數，它仍然只收入點數 $1,2,3$ 的機率質量，因此 $F_X(3.4)=1/2$。</figcaption>
</figure>

離散型 CDF 的跳躍高度正是該點的機率質量。以公正骰子為例，每個點數的機率質量都是 $1/6$，所以 CDF 每次跨過一個整數點，便往上跳 $1/6$。

<figure class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/dice-cdf-jump.svg" alt="公正骰子的 CDF 階梯圖。每個整數點都有高度 1/6 的跳躍。">
  <figcaption><span class="topic-figure__label">Fig. 2.4.</span> 公正骰子的 CDF 在每個可能取值處都跳躍 $1/6$。在 $x=3.4$ 時，CDF 讀到的高度是 $3/6$。</figcaption>
</figure>

若想親手改變單點機率並觀察階梯如何累積，可以參考互動展示 [From&nbsp;PMF&nbsp;to&nbsp;CDF](/demos/pmf-cdf/)。

## 連續型，靠密度積分

另一種常見情形中，單點本身不具有正機率，機率沿著區間連續累積。若存在非負函數 $f_X$，使得對任意 $x\in\mathbb{R}$ 皆有

$$
F_X(x)=\int_{-\infty}^{x} f_X(t)\,dt
$$

則稱 $X$ 為**連續型隨機變數 (continuous random variable)**。此時 $f_X$ 稱為**機率密度函數**，英文全名為 probability density function，常簡記為 PDF。

此時事件 $\lbrace X\leq x\rbrace$ 的機率改由密度函數在 $(-\infty,x]$ 上的面積累積，而不採單點相加。

<figure class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/continuous-cdf-area.svg" alt="連續型隨機變數的 CDF 可由密度曲線左側面積表示。">
  <figcaption><span class="topic-figure__label">Fig. 2.5.</span> 對連續型隨機變數而言，$F_X(x)$ 是密度函數在 $(-\infty,x]$ 上的面積。</figcaption>
</figure>

若 $a<b$，則區間機率可由兩個累積面積相減得到。

$$
\mathbb{P}(a<X\leq b)
=
F_X(b)-F_X(a)
=
\int_a^b f_X(t)\,dt
$$

<figure class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/continuous-interval-area.svg" alt="連續型隨機變數落在 a 到 b 之間的機率由密度曲線下方區間面積表示。">
  <figcaption><span class="topic-figure__label">Fig. 2.6.</span> 區間機率 $\mathbb{P}(a<X\leq b)$ 是 $a$ 到 $b$ 之間的密度面積，也就是 $F_X(b)-F_X(a)$。</figcaption>
</figure>

密度 $f_X(t)$ 不是單點機率。它描述機率在數線附近累積的速率，因此 $f_X(t)$ 可以大於 $1$。實際的機率來自面積，而不是某一點的函數值。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

嚴格地說，CDF 連續不必然代表可由一般密度函數積分表示。測度論中還有更細的分解，例如奇異連續分配。本章先採統計課程中最常用的版本，也就是可由 PDF 描述的連續型隨機變數。
</div>

此外，連續型隨機變數在單點上的機率為零。對任意實數 $a$，

$$
\mathbb{P}(X=a)=\int_a^a f_X(t)\,dt=0
$$

<figure class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/continuous-point-zero.svg" alt="連續型隨機變數在單點 a 上沒有面積，因此單點機率為零。">
  <figcaption><span class="topic-figure__label">Fig. 2.7.</span> 單點 $a$ 沒有寬度，故密度曲線在 $a$ 到 $a$ 之間沒有面積。</figcaption>
</figure>

這不表示 $a$ 不可能成為觀測值，而是說單點在連續模型中沒有面積，故不具有正機率。這一點延續了第一章中[飛鏢落點的直覺校準](/teaching-topics/random-experiments-sample-space-events/#thought-experiment-dart-zero-probability)。也因此，對連續型隨機變數而言，端點是否包含通常不會改變區間機率。

若想調整密度圖形並觀察面積如何變成 CDF，可以參考互動展示 [From&nbsp;PDF&nbsp;to&nbsp;CDF](/demos/pdf-cdf/)。

有些分配同時具有單點機率與連續密度。這類情形需要同時使用加總與積分，較適合在熟悉 PMF、PDF 與期望值、變異數等計算後再討論。

## 本篇小結

無論 $X$ 是離散型或連續型，$F_X(x)$ 都來自同一個事件。

$$
F_X(x)=\mathbb{P}(X\leq x)
$$

差別只在計算方式。

| 型態 | $\lbrace X\leq x\rbrace$ 的機率如何計算 | CDF 的形狀 |
| --- | --- | --- |
| 離散型 | **加總**不超過 $x$ 的單點機率 | 階梯狀，有跳躍 |
| 連續型 | **積分** $(-\infty,x]$ 上的密度 | 通常平滑累積 |

PMF 與 PDF 分別記錄離散型與連續型的計算方式。前者記錄單點機率，後者記錄累積機率的變化率；二者最後都回到同一個累積分配函數。

CDF 仍以事件機率為本，並把隨機變數的討論帶到實數線上的函數討論之中。離散型把門檻左側的單點機率相加；連續型把門檻左側的密度面積積分。

因此，隨機變數不只是樣本點的重新命名；函數、極限、微分、積分與分佈形狀都能納入討論，後續的常見分配、期望值與極限定理也由此展開。下一篇[離散型隨機變數與機率質量函數](/teaching-topics/discrete-random-variables-pmf/)會先細講離散型情形，說明 PMF 如何記錄單點機率，以及它如何與 CDF 的跳躍相互對應。

## 參考文獻與延伸閱讀

- Patrick Billingsley, *Probability and Measure*, 3rd ed., Wiley, 1995, chapters on distribution functions and probability measures.
- William Feller, *An Introduction to Probability Theory and Its Applications*, Volume I, 3rd ed., Wiley, 1968, chapters on distribution functions.
- George Casella and Roger L. Berger, *Statistical Inference*, 2nd ed., Duxbury, 2002, sections on random variables and distribution functions.
- Sheldon M. Ross, *A First Course in Probability*, 10th ed., Pearson, 2019, chapters on discrete and continuous random variables.
- Joseph K. Blitzstein and Jessica Hwang, *Introduction to Probability*, 2nd ed., CRC Press, 2019, chapters on CDFs, PMFs, and PDFs.
- Lawrence M. Leemis, “Relationships among Common Univariate Distributions”, *The American Statistician*, 40(2), 143–146, 1986. [DOI 10.1080/00031305.1986.10475379](https://doi.org/10.1080/00031305.1986.10475379).
