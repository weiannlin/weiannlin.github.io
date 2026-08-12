---
title: "累積分配函數"
subtitle: "Cumulative Distribution Functions"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 2
order: 202
permalink: /teaching-topics/ch2-p02-candidate/
date: 2026-08-04
published: false
excerpt: "累積分配函數定義為 $F_{\\sssig X}(x)=\\mathbb{P}(X\\leqslant x)$，定義域為整個實數線，函數值落在 $[0,1]$ 之中，離散型與連續型隨機變數都適用。它必然非遞減、右連續，兩端的極限分別為 $0$ 與 $1$；離散型的累積分配函數為階梯函數，每一階的躍升高度即為該質點的機率，故亦可由累積分配函數回頭求得機率質量函數。"
---

[上一篇](/teaching-topics/ch2-p01-candidate/)以機率質量函數描述離散型隨機變數，把機率逐點記在值域的質點上。但機率質量函數只定義在離散型隨機變數上，[Definition 2.2](/teaching-topics/ch2-p01-candidate/#def-support-classification) 所分出的另一型並不適用。

另一方面，[Definition 2.1](/teaching-topics/ch2-p01-candidate/#def-random-variable) 要求對任意 $x\in\mathbb{R}$，能使 $X(\omega)\leqslant x$ 的樣本點所形成的集合都是事件，故 $\mathbb{P}(X\leqslant x)$ 對每一個實數 $x$ 都有定義。把 $x$ 看成變數，這個機率本身就是一個定義在實數上的函數，且不必事先區分 $X$ 屬於哪一型。

<div id="def-cdf" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.4 (累積分配函數, cumulative distribution function, cdf)</div>

若 $X$ 為定義於機率空間 $(S,\mathcal{F},\mathbb{P})$ 上之隨機變數，則定義函數

$$
F_{\sssig X}(x)=\mathbb{P}(X\leqslant x),\ x\in\mathbb{R}
$$

我們稱 $F_{\sssig X}(x)$ 為 $X$ 的**累積分配函數 <span lang="en">(cumulative distribution function, cdf)</span>** 或簡稱為**分配函數 <span lang="en">(distribution function, df)</span>**。

</div>

累積分配函數有一些地方需要注意:

(1) **累積分配函數** $F_{\sssig X}(x)$ 是一種定義在實數 $\mathbb{R}$ 上的函數，且將其對應到 $[0,1]$ 區間中的函數，可以記為
{: .topic-paren-item}

$$
F\colon\mathbb{R}\to[0,1]
$$

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

有些教科書將 cdf 的定義寫為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig X}(x)=\mathbb{P}(X\leqslant x)=\mathbb{P}\bigl(X^{-1}(-\infty,x]\bigr),\ x\in\mathbb{R}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig X}(x)&=\mathbb{P}(X\leqslant x)\\[0.4em]
&=\mathbb{P}\bigl(X^{-1}(-\infty,x]\bigr),\ x\in\mathbb{R}
\end{aligned}
$$

</div>

這個版本中，如果搭配 $X^{\sssig -1}(\cdot)$ 的定義，我們將更容易看出 cdf 是如何將一個實數範圍上的集合，對應回樣本點進行機率的計算的。

</div>

(2) 累積分配函數的定義中，並不限制 $X$ 是一個離散型隨機變數，或是連續型隨機變數，但是由於 $\mathbb{P}(X\leqslant x)$ 的運算，在離散型隨機變數上是採用累加的方式，故亦有教科書認為應分開定義，且應翻譯為**累加分配函數**。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

連續型隨機變數中的累積分配函數，其運算性質是採用微積分中的**積分 <span lang="en">(integration)</span>**，雖然其本質仍為累加，但由於運算細節有所不同，故許多教科書並不將其認為是一種**加總 <span lang="en">(summation)</span>**。

</div>

<div id="thm-cdf-properties" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.1 (cdf 的性質, properties of a cdf)</div>

若 $F_{\sssig X}(x)$ 為 $X$ 之累積分配函數，則其具以下性質:

<ol class="topic-list-paren">
  <li>
  $$
  0\leqslant F_{\sssig X}(x)\leqslant 1,\ \forall x\in\mathbb{R}
  $$
  </li>
  <li>$F_{\sssig X}(x)$ <strong>非遞減 <span lang="en">(non-decreasing)</span></strong></li>
  <li>$F_{\sssig X}(x)$ <strong>右連續 <span lang="en">(right-continuous)</span></strong></li>
  <li>若 $X$ 為離散型隨機變數，$F_{\sssig X}(x)$ 為一<strong>階梯函數 <span lang="en">(step function)</span></strong></li>
  <li>
  <div class="topic-math-layout topic-math-layout--desktop">
  $$
  \lim_{x\to-\infty}F_{\sssig X}(x)=0,\quad\lim_{x\to\infty}F_{\sssig X}(x)=1
  $$
  </div>
  <div class="topic-math-layout topic-math-layout--mobile">
  $$
  \begin{gathered}
  \lim_{x\to-\infty}F_{\sssig X}(x)=0\\[0.5em]
  \lim_{x\to\infty}F_{\sssig X}(x)=1
  \end{gathered}
  $$
  </div>
  </li>
</ol>

</div>

累積分配函數是一種累積的機率，以離散型隨機變數而言，其定義 $\mathbb{P}(X\leqslant x)$ 代表「小於等於 $x$ 的所有機率總和」，即

$$
\sum_{t\leqslant x}\mathbb{P}(X=t)
$$

故其當然介在 $0$ 至 $1$ 之間。

又因為其機率為累積 (或累加)，隨著 $x$ 的增長，函數值 $F_{\sssig X}(x)$ 只會向上增加或持平，故其累積分配函數當然具有**非遞減**之性質。至於**右連續**，累積本身只保證非遞減，尚須用到機率的連續性: 令 $x_1>x_2>\cdots$ 為任一遞減至 $x$ 的數列，則 $\lbrace X\leqslant x_n\rbrace$ 為一非遞增的事件序列，其極限為 $\lbrace X\leqslant x\rbrace$，故由[單調事件序列的機率極限](/teaching-topics/probability-rules-from-axioms/#theorem-continuity)可得

$$
\lim_{n\to\infty}F_{\sssig X}(x_n)=\mathbb{P}(X\leqslant x)=F_{\sssig X}(x)
$$

此即右連續。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

事實上在連續型隨機變數中 $F_{\sssig X}(x)$ 是一連續函數 (即左連續且右連續)；而僅右連續的狀況發生在離散型隨機變數，或稍後的章節中會談到的[混合型隨機變數](/teaching-topics/ch2-p05-candidate/)中。

</div>

在離散型隨機變數中，$x$ 在累加到具有機率的質點時，其 cdf 會具跳躍式的成長；接著到 $x$ 再累加至具有機率的下一個質點前，由於沒有新的質點，小於等於 $x$ 的機率總和並不會成長，故其函數值會維持水平的狀態，這樣的函數便被稱為**階梯函數**。

<div id="note-step-function-isolated-points" class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

[Theorem 2.1](#thm-cdf-properties) 第 (4) 款尚需一個前提: 值域中的質點在每一個有界區間內都只有有限多個，等價於值域在 $\mathbb{R}$ 中沒有聚點。只要求每一個質點都是孤立點並不夠。取值域為 $\lbrace\,1/n\mid n=1,2,\ldots\,\rbrace$、$p_{\sssig X}(1/n)=2^{-n}$，每一個質點都有一個不含其他質點的鄰域，但 $0$ 的右側任一鄰域內都有無窮多個跳躍，含 $0$ 的區間無法分成有限多段水平線段，$F_{\sssig X}$ 因而不是階梯函數；此時第 (1)、(2)、(3)、(5) 四款仍然成立。

</div>

<div id="ex-two-ball-sum-cdf" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.2 <span lang="en">(Continued)</span></div>

若箱中有四顆大小形狀完全相同、分別編號 $0$ 至 $3$ 的球，若 $X$ 表示隨機從中一次抽取兩顆球的號碼總和，則試列出且畫出其 cdf。

$X$ 的 pmf 已於 [Example 2.2](/teaching-topics/ch2-p01-candidate/#ex-two-ball-sum) 求得: <span class="text-nowrap">$p_{\sssig X}(3)=\frac{2}{6}=\frac{1}{3}$，</span>其餘四個質點 $1,2,4,5$ 的機率各為 $\frac{1}{6}$。$F_{\sssig X}(x)$ 為小於等於 $x$ 的各質點機率之總和，以 pmf 寫出即

$$
F_{\sssig X}(x)=\sum_{t\leqslant x}p_{\sssig X}(t)
$$

五個質點由小至大依序累加，可得

$$
F_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & x<1\\[0.55em]
\dfrac{1}{6}, & 1\leqslant x<2\\[0.55em]
\dfrac{2}{6}, & 2\leqslant x<3\\[0.55em]
\dfrac{4}{6}, & 3\leqslant x<4\\[0.55em]
\dfrac{5}{6}, & 4\leqslant x<5\\[0.55em]
1, & 5\leqslant x
\end{array}
\right.
$$

<figure id="fig-two-ball-sum-cdf" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/two-ball-sum-cdf.svg" alt="四球取兩顆之號碼總和的累積分配函數階梯圖。函數值由 0 開始，在 x 等於 1、2、3、4、5 各躍升一階，躍升之後維持水平，最後停在 1。">
  <figcaption><span class="topic-figure__label">Fig. 2.1.</span> 號碼總和 $X$ 的 cdf。函數在 $x=1,2,3,4,5$ 五個質點上各躍升一階，兩階之間維持水平。縱軸以 $y=3$ 對應機率 $1$，與 <a href="#fig-cdf-to-pmf">Fig. 2.2</a> 的比例尺不同，兩圖的高度不可直接比較。</figcaption>
</figure>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

五個質點 $1,2,3,4,5$ 同時是各段的分界，由於定義取的是小於等於，分界一律歸入右側的那一段: $x=1$ 時 $p_{\sssig X}(1)$ 已計入，<span class="text-nowrap">$F_{\sssig X}(1)=\frac{1}{6}$，</span>與 $x$ 自右側趨近 $1$ 的極限相同，此即 [Theorem 2.1](#thm-cdf-properties) 第 (3) 款右連續在本題的具體情形。最外側的 $x<1$ 與 $5\leqslant x$ 兩段則分別恆為 $0$ 與 $1$，[Theorem 2.1](#thm-cdf-properties) 第 (5) 款的兩個極限在本題即由這兩段給出。

</div>

[上圖](#fig-two-ball-sum-cdf)是典型的離散型 cdf，每一階的跳躍點，都對應到原本的 pmf 中的機率質點，且躍升的高度即是該點的機率，故我們可以由離散型 cdf 轉換為其對應的 pmf，如下圖:

<figure id="fig-cdf-to-pmf" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/cdf-to-pmf.svg" alt="由累積分配函數各階躍升高度還原的機率質量函數點圖。x 等於 1、2、4、5 的點高為六分之一，x 等於 3 的點高為三分之一。">
  <figcaption><span class="topic-figure__label">Fig. 2.2.</span> 由 <a href="#fig-two-ball-sum-cdf">Fig. 2.1</a> 各階的躍升高度還原的 pmf。縱軸以 $y=6$ 對應機率 $1$，與 <a href="#fig-two-ball-sum-cdf">Fig. 2.1</a> 的比例尺不同，兩圖的高度不可直接比較。</figcaption>
</figure>

關於躍升的高度是否恰為該質點的機率，讀者可以在 Demos 的 [From pmf to cdf](/demos/pmf-cdf/) 中改變表中各點的機率值，觀察 cdf 上各階的躍升高度隨之改變；移動當前的 $x$ 逐一掃過各個質點，即可逐點核對。

<div id="ex-geometric-cdf" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.3 <span lang="en">(Continued)</span></div>

<div lang="en" markdown="1">
Suppose that a random variable $X$ has probability mass function

$$
p_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
\left(\dfrac{1}{2}\right)^{x}, & x=1,2,\ldots\\[0.6em]
0, & \text{otherwise}
\end{array}
\right.
$$

<ol class="topic-list-paren topic-list-paren--start-2">
  <li>Determine the cumulative distribution function of $X$.</li>
</ol>
</div>

<ol class="topic-list-paren topic-list-paren--start-2">
  <li>
  <div class="topic-math-layout topic-math-layout--desktop" markdown="1">

  $$
  F_{\sssig X}(x)=
  \left\lbrace
  \begin{array}{c@{\quad}l}
  0, & x<1\\[0.7em]
  \dfrac{\frac{1}{2}\left(1-\left(\frac{1}{2}\right)^{\lfloor x\rfloor}\right)}{1-\frac{1}{2}}
  =1-\left(\dfrac{1}{2}\right)^{[x]}, & x\geqslant 1
  \end{array}
  \right.
  $$

  </div>
  <div class="topic-math-layout topic-math-layout--mobile" markdown="1">

  $$
  F_{\sssig X}(x)=
  \left\lbrace
  \begin{array}{@{}l@{}}
  0,\ \ x<1\\[0.7em]
  \dfrac{\frac{1}{2}\left(1-\left(\frac{1}{2}\right)^{\lfloor x\rfloor}\right)}{1-\frac{1}{2}}\\[0.35em]
  \quad =1-\left(\dfrac{1}{2}\right)^{[x]},\ \ x\geqslant 1
  \end{array}
  \right.
  $$

  </div>
  </li>
</ol>

其中 $\lfloor x\rfloor$ 表**取底函數 <span lang="en">(floor function)</span>**，亦稱為**高斯符號** (記為 $[x]$)，表不大於 $x$ 之最大整數。
{: .topic-paren-cont}

</div>

<div id="ex-degenerate-cdf" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.5</div>

若 $X$ 為一隨機變數，且其 cdf 為

$$
F_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & x<0\\[0.4em]
1, & x\geqslant 0
\end{array}
\right.
$$

則求其 pmf 為何？

<figure id="fig-degenerate-cdf" class="topic-figure topic-figure--narrow">
  <img src="/images/teaching-topics/degenerate-cdf.svg" alt="退化型隨機變數的累積分配函數圖。x 小於 0 時函數值為 0，在 x 等於 0 處躍升至 1，其後維持水平。">
  <figcaption><span class="topic-figure__label">Fig. 2.3.</span> $F_{\sssig X}$ 只在 $x=0$ 處躍升，躍升的高度為 <span class="text-nowrap">$1$。</span></figcaption>
</figure>

$F_{\sssig X}(x)$ 在 $x=0$ 處發生一高度為 $1$ 之跳躍，故可由此得知

$$
p_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
1, & x=0\\[0.4em]
0, & \text{otherwise}
\end{array}
\right.
$$

</div>

## 本篇小結

累積分配函數定義為 $F_{\sssig X}(x)=\mathbb{P}(X\leqslant x)$，定義域是整條實數線，函數值落在 $[0,1]$ 之中。它的定義並不限制 $X$ 的型態，離散型與連續型都適用，這是它與只定義在離散型上的[機率質量函數](/teaching-topics/ch2-p01-candidate/#def-pmf)最大的不同。

[Theorem 2.1](#thm-cdf-properties) 列出五項性質: 函數值介於 $0$ 與 $1$ 之間、非遞減、右連續、$X$ 為離散型時是階梯函數，以及兩端的極限分別為 $0$ 與 $1$。前兩項可由「累積」二字直接看出，右連續另需機率的連續性，第 (4) 款另需質點不聚集的前提。

離散型 cdf 的每一階都對應到一個質點，躍升的高度就是該點的機率，故 pmf 與 cdf 之間可以互推: [Example 2.2 <span lang="en">(Continued)</span>](#ex-two-ball-sum-cdf) 由 pmf 累加得到 cdf，[Example 2.5](#ex-degenerate-cdf) 則由 cdf 的單一跳躍回頭求得 pmf。[下一篇](/teaching-topics/ch2-p03-candidate/)進入連續型隨機變數的機率密度函數。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Morris H. DeGroot and Mark J. Schervish. 2012. *Probability and Statistics*. 4th ed. Pearson.
- Vijay K. Rohatgi and A. K. Md. Ehsanes Saleh. 2015. *An Introduction to Probability and Statistics*. 3rd ed. Wiley.
