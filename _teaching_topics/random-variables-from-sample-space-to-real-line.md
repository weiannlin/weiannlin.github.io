---
title: "隨機變數，從樣本空間到數線"
subtitle: "Random Variables as Maps from Sample Space to the Real Line"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 1
order: 201
permalink: /teaching-topics/random-variables-from-sample-space-to-real-line/
date: 2026-05-17
published: true
excerpt: "事件機率把事件送到機率數值；隨機變數則先把樣本點送到實數，使我們可以用數線、函數與微積分方法描述機率。"
---

[上一章最後一篇文章](/teaching-topics/independence-and-conditional-independence/)說明了獨立性。到那裡為止，我們討論的主要對象仍是事件。事件是樣本空間的子集合，而機率函數把可測事件送到 $0$ 與 $1$ 之間的數值。

$$
\mathbb{P}:\mathcal{F}\longrightarrow [0,1]
$$

第一章建立的是集合上的機率。由於事件本身就是集合，若要討論事件機率，便必須處理這些集合之間的關係。只是，若始終停留在集合運算，微積分、函數分析與極限方法就不容易直接使用。因此，下一步仍以事件為基礎，先把樣本空間中的結果轉成實數。

隨機變數用來完成這個轉換。它把每個樣本點 $\omega$ 送到一個實數 $X(\omega)$，使我們可以把「結果」放到數線上，再討論數值與機率之間的關係。

<figure class="topic-figure topic-figure--medium">
  <img src="/images/teaching-topics/random-variable-map.svg" alt="隨機變數把樣本空間中的樣本點映到實數線。數線上的區間 (-infinity, x] 會對應回樣本空間中的事件。">
  <figcaption><span class="topic-figure__label">Fig. 2.1.</span> 隨機變數 $X$ 把樣本點送到實數。數線上的區間 $(-\infty,x]$ 會被 $X$ 拉回樣本空間中的事件 $\{X\leqslant x\}$。</figcaption>
</figure>

## 隨機變數不是隨機的數

隨機變數 (random&nbsp;variable) 的名稱容易讓人誤會。隨機的是實驗結果 $\omega$；$X$ 本身則是定義在樣本空間上的函數。一旦 $\omega$ 確定，$X(\omega)$ 就是確定的實數。

以下定義先採用半直線版本。這個寫法與稍後的累積分配函數直接相連，也最容易看出隨機變數如何把數線上的門檻拉回樣本空間。

<div class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.1</div>

令 $(S,\mathcal{F},\mathbb{P})$ 為一個機率空間。若 $X:S\to\mathbb{R}$ 為定義在樣本空間 $S$ 上的實值函數，且對任意 $x\in\mathbb{R}$，皆有

$$
\{\omega\in S\mid X(\omega)\leqslant x\}\in\mathcal{F}
$$

則稱 $X$ 為定義於 $(S,\mathcal{F},\mathbb{P})$ 上的**隨機變數 (random&nbsp;variable)**。
</div>

有些教科書會採用反映射版本。這個寫法需要實數線上的 Borel $\sigma$-域 $\mathcal{B}(\mathbb{R})$，若需要回顧，可先參考[事件集合族與 $\sigma$-域](/teaching-topics/event-families-sigma-fields/#實數線上的-borel-sigma-域)。對任意 $B\in\mathcal{B}(\mathbb{R})$，要求

$$
X^{-1}(B)=\{\omega\in S\mid X(\omega)\in B\}\in\mathcal{F}
$$

半直線版本與反映射版本在實值情形中等價，因為 $(-\infty,x]$ 這類半直線會生成 $\mathcal{B}(\mathbb{R})$。半直線版本和接下來的 CDF 定義相連；反映射版本則直接說明可測性的來源。

這個條件的用途很明確。對每一個實數 $x$，所有滿足 $X(\omega)\leqslant x$ 的樣本點必須形成 $\mathcal{F}$ 中的事件，如此才可以賦予其機率。

## 從樣本點到數值

投擲一顆公正骰子一次。為了先把樣本點與數值分開，將六個可能結果記作

$$
S=\{\omega_1,\omega_2,\omega_3,\omega_4,\omega_5,\omega_6\}
$$

其中 $\omega_i$ 表示擲出點數 $i$ 的樣本點。定義點數隨機變數 $X$ 為

$$
X(\omega_i)=i,\qquad i=1,\ldots,6
$$

則 $X$ 就是觀察點數本身。此時

$$
\{X\leqslant 3\}=\{\omega_1,\omega_2,\omega_3\}
$$

公正骰子有六個均等可能的樣本點，其中三個落在這個事件中，故機率為

$$
\mathbb{P}(X\leqslant 3)=\frac{3}{6}=\frac{1}{2}
$$

同一個樣本空間也可以對應到不同的隨機變數。例如，定義另一個隨機變數 $Y$ 為

$$
Y(\omega_i)=
\begin{cases}
1, & i \text{ 為偶數},\\[0.35em]
0, & i \text{ 為奇數}
\end{cases}
$$

則 $Y$ 只記錄點數是否為偶數。它捨去點數細節，只保留奇偶性；所有偶數結果都送到 $1$，所有奇數結果都送到 $0$。

<div class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 2.1</div>

請分辨下列三個層次。$X$ 是一個函數，$x$ 是一個實數，而 $X=x$ 是一個事件。

$$
\{X=x\}=\{\omega\in S\mid X(\omega)=x\}
$$

所以 $\mathbb{P}(X=x)$ 的機率對象，是由 $X$ 定出的事件 $\{X=x\}$；數字 $x$ 只是用來指定這個事件的取值。
</div>

## 由門檻事件定義累積分配函數

隨機變數把樣本點送到數線上後，可以固定一個門檻 $x$，回頭審視哪些樣本點滿足 $X(\omega)\leqslant x$。這些樣本點形成事件 $\{X\leqslant x\}$，其機率即為**累積分配函數 (cumulative distribution function, CDF)**。在本講義中，CDF 也簡稱為**分配函數 (distribution function, DF)**。

<div class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.2</div>

令 $X$ 為一個隨機變數。定義

$$
F_X(x)=\mathbb{P}(X\leqslant x),\qquad x\in\mathbb{R}
$$

則稱 $F_X$ 為 $X$ 的**累積分配函數 (cumulative distribution function, CDF)**，也稱為**分配函數 (distribution function, DF)**。
</div>

若把 $\{X\leqslant x\}$ 完整寫回樣本空間，CDF 計算的是

$$
F_X(x)
=
\mathbb{P}\bigl(\{\omega\in S\mid X(\omega)\leqslant x\}\bigr)
$$

因此，CDF 是一個由實數到機率的函數。輸入是實數 $x$，輸出是機率 $F_X(x)$。隨機變數把樣本點轉成實數後，便能在機率論中討論函數圖形、單調性、極限、微分與積分。

## 同一個定義涵蓋不同型態

CDF 的定義比單純列出幾個機率更抽象。對每一個門檻 $x$，它都給出事件 $\{X\leqslant x\}$ 的機率。

這個定義先不區分型態。無論 $X$ 之後屬於離散型或連續型，只要 $X$ 是實值隨機變數，事件 $\{X\leqslant x\}$ 都有意義，函數 $F_X$ 也都可以被定義。下一篇[累積分配函數如何累積機率](/teaching-topics/probability-accumulates/)會從離散型與連續型開始，說明同一個 $F_X$ 如何呈現機率資訊。

## 本篇小結

第一章建立事件機率。事件 $A$ 是樣本空間中的可測集合，機率函數 $\mathbb{P}$ 將事件送到 $[0,1]$。

$$
\mathbb{P}:\mathcal{F}\longrightarrow [0,1]
$$

第二章開始，我們把樣本空間中的結果透過隨機變數送到數線上。

$$
X:S\longrightarrow \mathbb{R}
$$

隨機變數定義後，便可固定門檻 $x$，回頭審視並計算 $\{X\leqslant x\}$ 此一事件的機率。這就是累積分配函數的起點。

$$
F_X(x)=\mathbb{P}(X\leqslant x)
$$

這一步使機率論不只停留在集合運算，也開始進入函數觀點。下一篇[累積分配函數如何累積機率](/teaching-topics/probability-accumulates/)會進一步說明 CDF 如何累積機率，並由此區分離散型與連續型隨機變數。

## 參考文獻與延伸閱讀

- Patrick Billingsley. 1995. *Probability and Measure*. 3rd ed. Wiley.
- William Feller. 1968. *An Introduction to Probability Theory and Its Applications*. Vol. 1, 3rd ed. Wiley.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Sheldon M. Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Joseph K. Blitzstein and Jessica Hwang. 2019. *Introduction to Probability*. 2nd ed. Chapman and Hall/CRC.
