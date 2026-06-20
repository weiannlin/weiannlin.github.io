---
title: "連續型隨機變數與機率密度函數"
subtitle: "Continuous Random Variables and Probability Density Functions"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 4
order: 204
permalink: /teaching-topics/continuous-random-variables-pdf/
date: 2026-06-06
published: true
excerpt: "連續型隨機變數的單點不具有正機率，事件機率改由密度函數在區間上的面積計算。PDF 可視為 CDF 的變化率，區間機率則由積分取得。"
---

[上一篇文章](/teaching-topics/discrete-random-variables-pmf/)細講離散型隨機變數。離散型的機率集中在可逐一列出的單點上，因此事件機率可由 PMF 加總取得。若單點不具有正機率，機率便不再逐點相加，而要改由區間上的面積計算。

本篇先討論其中最常用的情形。若一個隨機變數的累積分配函數可由某個非負函數積分而成，該非負函數稱為**機率密度函數 (probability density function, PDF)**。這類隨機變數可由 PDF 描述，之後的區間機率便可透過積分計算。

## 由累積分配函數到密度

令 $X$ 為隨機變數，$F_X$ 為其累積分配函數。

$$
F_X(x)=\mathbb{P}(X\leqslant x)
$$

若存在非負函數 $f_X$，使得對任意 $x\in\mathbb{R}$ 皆有

$$
F_X(x)=\int_{-\infty}^{x} f_X(t)\,dt
$$

則 $F_X(x)$ 可被視為密度函數從 $-\infty$ 到 $x$ 的累積面積。

<figure class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/continuous-cdf-area.svg" alt="連續型隨機變數的累積分配函數由密度曲線左側面積表示。">
  <figcaption><span class="topic-figure__label">Fig. 2.9.</span> 對可由 PDF 描述的連續型隨機變數而言，$F_X(x)$ 是密度函數在 $(-\infty,x]$ 上累積的面積。</figcaption>
</figure>

<div class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.4</div>

令 $X$ 為隨機變數。若存在非負函數 $f_X$，使得對任意 $x\in\mathbb{R}$ 皆有

$$
F_X(x)=\mathbb{P}(X\leqslant x)=\int_{-\infty}^{x} f_X(t)\,dt
$$

則稱 $f_X$ 為 $X$ 的**機率密度函數 (probability density function, PDF)**。本篇所討論的是可由 PDF 描述的連續型隨機變數。
</div>

這裡的 PDF 並不是單點機率。$f_X(x)$ 描述的是機率在 $x$ 附近累積的快慢，而真正的機率仍然來自面積。因此 $f_X(x)$ 可以大於 $1$，只要整條曲線下方的總面積等於 $1$。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

嚴格而言，並非所有連續的 CDF 都能由一般 PDF 積分表示。測度論中還有更細緻的分解。本章先採統計課程中最常使用的情形，也就是可由密度函數描述的連續型情形。
</div>

## PDF 的基本性質

PDF 必須滿足兩個基本條件。第一，密度不可為負。第二，整條實數線下方的總面積必須為 $1$。

<div class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Proposition 2.4 (PDF Conditions)</div>

若 $f_X$ 為隨機變數 $X$ 的 PDF，則

$$
f_X(x)\geqslant 0,\qquad x\in\mathbb{R}
$$

且

$$
\int_{-\infty}^{\infty} f_X(x)\,dx=1
$$

</div>

反過來，若一個非負函數在整條實數線上的積分為 $1$，則它可以作為某個可由密度描述的隨機變數的 PDF。這一點和 PMF 的條件十分相似。離散型把所有單點機率加總為 $1$，PDF 則把整條密度曲線下方的面積積分為 $1$。

## 區間機率

對可由 PDF 描述的連續型隨機變數而言，事件機率通常以區間為單位計算。若 $a<b$，則

$$
\mathbb{P}(a<X\leqslant b)
=
F_X(b)-F_X(a)
=
\int_a^b f_X(t)\,dt
$$

<figure class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/continuous-interval-area.svg" alt="連續型隨機變數落在 a 到 b 之間的機率由密度曲線下方區間面積表示。">
  <figcaption><span class="topic-figure__label">Fig. 2.10.</span> 區間機率 $\mathbb{P}(a<X\leqslant b)$ 是 $a$ 到 $b$ 之間的密度面積，也就是 $F_X(b)-F_X(a)$。</figcaption>
</figure>

這個公式說明，PDF 不直接給出單點機率，而是透過積分給出區間機率。接下來若只看 $x$ 附近的一小段區間，就可把一般的端點 $a,b$ 改寫成 $x$ 與 $x+\Delta x$。這裡的 $\Delta x$ 表示沿著數線往右推進的一段很短距離。

<figure class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/continuous-small-interval-area.svg" alt="連續型隨機變數在 x 到 x 加 Delta x 之間的局部區間面積。">
  <figcaption><span class="topic-figure__label">Fig. 2.11.</span> 將一般區間縮小為 $x$ 到 $x+\Delta x$ 後，紅色面積就是 CDF 從 $x$ 推進到 $x+\Delta x$ 時增加的機率。</figcaption>
</figure>

若區間很短，且 $f_X$ 在該處變化不大，則

$$
\mathbb{P}(x<X\leqslant x+\Delta x)
=
\int_x^{x+\Delta x} f_X(t)\,dt
\approx
f_X(x)\Delta x
$$

因此 $f_X(x)$ 可視為單位長度附近所累積的機率量。真正具有機率意義的是 $f_X(x)$ 乘上寬度後所形成的面積。

## 由 CDF 求得 PDF

離散型的 PMF 可由 CDF 的跳躍高度求得。連續型也有相應的關係，只是這裡看的不是跳躍高度，而是 CDF 的局部變化率。回到 Fig. 2.11，當門檻由 $x$ 推進到 $x+\Delta x$ 時，CDF 的增加量為

$$
\Delta F
=
F_X(x+\Delta x)-F_X(x)
=
\mathbb{P}(x<X\leqslant x+\Delta x)
$$

若 $\Delta x$ 很小，則這個面積近似於

$$
\Delta F\approx f_X(x)\Delta x
$$

將兩邊同除以 $\Delta x$，可得

$$
\frac{\Delta F}{\Delta x}\approx f_X(x)
$$

若令這段寬度越來越小，也就是令 $\Delta x\downarrow 0$，則上式左側會逐漸逼近 $F_X$ 在 $x$ 的變化率。若 $F_X$ 在 $x$ 可微，則這個極限就是導數。

$$
\lim_{\Delta x\downarrow 0}
\frac{F_X(x+\Delta x)-F_X(x)}{\Delta x}
=
F_X'(x)
$$

若 $f_X$ 在 $x$ 附近連續，則由微積分基本定理可知

$$
f_X(x)=F_X'(x)
$$

也就是說，在這些通常可處理的點上，PDF 可視為 CDF 在該點的斜率。反過來由 CDF 求 PDF 時，只能在適當的可微點取導數；端點或有限多點上的密度值如何指定，並不會改變任何區間機率。CDF 給出的是 $X$ 落在 $(-\infty,x]$ 中的機率；PDF 則描述當位置在 $x$ 附近微小推進時，這個機率增加得多快。

<div class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 2.4</div>

由前面的面積圖可知，連續型隨機變數的機率來自密度曲線下方的面積。若只看一個單點 $x$，這個點無法形成一段區間長，自然也就構不成面積。

這正是連續型隨機變數與離散型隨機變數最大的差異之一。離散型可以在某個點上具有正機率；連續型則必須透過一段區間累積機率。
</div>

## 單點機率為零

對任意實數 $a$，若 $X$ 可由 PDF 描述，則

$$
\mathbb{P}(X=a)=\int_a^a f_X(t)\,dt=0
$$

<figure class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/continuous-point-zero.svg" alt="連續型隨機變數在單點 a 上沒有面積，因此單點機率為零。">
  <figcaption><span class="topic-figure__label">Fig. 2.12.</span> 單點 $a$ 沒有寬度，因此 $a$ 到 $a$ 之間的密度面積為 $0$。</figcaption>
</figure>

這不表示 $a$ 不可能成為觀測值，而是說單點在連續模型中不具有正機率。這一點延續了第一章中[飛鏢落點的直覺校準](/teaching-topics/random-experiments-sample-space-events/#thought-experiment-dart-zero-probability)。因此，對連續型隨機變數而言，端點是否包含通常不會改變區間機率。

$$
\mathbb{P}(a<X\leqslant b)
=
\mathbb{P}(a\leqslant X\leqslant b)
=
\mathbb{P}(a<X<b)
=
\mathbb{P}(a\leqslant X<b)
$$

這些式子在離散型情形中通常不可任意互換，因為離散型可能在端點上具有正機率。

<div class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.4 (Uniform Distribution on $[0,1]$)</div>

令 $X$ 的 PDF 為

$$
f_X(x)=
\left\{
\begin{array}{c@{\quad}l}
1, & 0<x<1,\\[0.35em]
0, & \text{otherwise}
\end{array}
\right.
$$

由於 $f_X(x)\geqslant 0$，且

$$
\int_{-\infty}^{\infty} f_X(x)\,dx
=
\int_0^1 1\,dx
=
1
$$

故 $f_X$ 可作為 PDF。其 CDF 為

$$
F_X(x)=
\left\{
\begin{array}{c@{\quad}l}
0, & x\leqslant 0,\\[0.35em]
x, & 0<x<1,\\[0.35em]
1, & x\geqslant 1
\end{array}
\right.
$$

若要求 $X$ 落在 $0.2$ 到 $0.7$ 之間的機率，則由區間面積可得

$$
\mathbb{P}(0.2<X\leqslant 0.7)
=
\int_{0.2}^{0.7}1\,dt
=
0.5
$$

</div>

這個例子也說明，均勻分配的密度曲線是平的，但機率並不在單點上。機率來自區間長度，區間越長，累積到的面積越大。

若想調整密度圖形並觀察面積如何形成 CDF，可以參考互動展示 [From&nbsp;PDF&nbsp;to&nbsp;CDF](/demos/pdf-cdf/)。

## 本篇小結

連續型隨機變數的機率不以單點相加計算，而是以密度函數的面積計算。PDF 滿足

$$
f_X(x)\geqslant 0,\qquad
\int_{-\infty}^{\infty} f_X(x)\,dx=1
$$

區間機率由積分求得。

$$
\mathbb{P}(a<X\leqslant b)
=
\int_a^b f_X(t)\,dt
$$

若 CDF 在某點可微，PDF 也可由 CDF 的斜率求得。

$$
f_X(x)=F_X'(x)
$$

離散型與連續型使用同一個 CDF 定義，差異在於計算事件機率的方式。離散型以 PMF 加總，連續型以 PDF 積分。下一篇[期望值，隨機變數的平均位置](/teaching-topics/expected-value-random-variables/)會開始討論如何用這些機率函數計算分配的代表數值。

## 參考文獻與延伸閱讀

- Patrick Billingsley. 1995. *Probability and Measure*. 3rd ed. Wiley.
- William Feller. 1968. *An Introduction to Probability Theory and Its Applications*. Vol. 1, 3rd ed. Wiley.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Sheldon M. Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Joseph K. Blitzstein and Jessica Hwang. 2019. *Introduction to Probability*. 2nd ed. Chapman and Hall/CRC.
