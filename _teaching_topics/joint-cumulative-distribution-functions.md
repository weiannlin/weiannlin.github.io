---
title: "聯合累積分配函數"
subtitle: "Joint Cumulative Distribution Functions"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 2
order: 302
permalink: /teaching-topics/joint-cumulative-distribution-functions/
date: 2026-07-24
published: false
excerpt: "聯合 cdf 記錄兩個隨機變數同時不超過指定門檻的機率；離散型情形可由左下方的單點機率加總得到。"
---

[上一篇文章](/teaching-topics/random-vectors-joint-pmf/)以聯合 pmf 記錄二元離散型隨機向量的單點機率。現在改由兩個門檻 $x$ 與 $y$ 出發，計算 $X$ 與 $Y$ 同時不超過這兩個門檻的機率。

這個作法不只適用於離散型隨機向量。無論聯合分配是否具有 pmf 或 pdf，門檻事件 $\lbrace X\leqslant x,Y\leqslant y\rbrace$ 都有意義。

## 聯合累積分配函數

<div id="definition-34" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 3.4</div>

令 $(X,Y)$ 為二元隨機向量。對任意 $(x,y)\in\mathbb{R}^2$，定義

$$
F_{XY}(x,y)
=
\mathbb{P}(X\leqslant x,Y\leqslant y)
$$

則稱 $F_{XY}$ 為 $(X,Y)$ 的**聯合累積分配函數 (joint cumulative distribution function, joint cdf)**，也簡稱為聯合分配函數。
</div>

若回到樣本空間，則 [Definition 3.4](#definition-34) 也可寫為

$$
F_{XY}(x,y)
=
\mathbb{P}\bigl(\lbrace\omega\in S\mid X(\omega)\leqslant x,\ Y(\omega)\leqslant y\rbrace\bigr)
$$

也就是對同時滿足 $X(\omega)\leqslant x$ 與 $Y(\omega)\leqslant y$ 的樣本點取機率。

[Definition 3.4](#definition-34) 累積的是平面中

$$
(-\infty,x]\times(-\infty,y]
$$

此一左下方區域的機率。門檻 $x$ 與 $y$ 可為任意實數，不必是 $X$ 或 $Y$ 的可能取值。

<figure id="fig-32" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/joint-cdf-region.svg" alt="聯合 cdf 在門檻點 (x,y) 左下方累積的淡紅區域，暗紅虛線標出此區域的上邊界與右邊界。">
  <figcaption><span class="topic-figure__label">Fig. 3.2.</span> 淡紅區域為 $F_{XY}(x,y)$ 所累積的範圍；暗紅虛線標出門檻 $x$ 與 $y$ 所形成的右邊界與上邊界。</figcaption>
</figure>

## 聯合 cdf 的定義域與離散型表示

<div id="proposition-32" class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Proposition 3.2</div>

令 $F_{XY}$ 為 $(X,Y)$ 的聯合 cdf。則有下列兩項性質。

(1) $F_{XY}$ 是由 $\mathbb{R}^2$ 對應至 $[0,1]$ 的函數，可記為

$$
F_{XY}:\mathbb{R}^2\longrightarrow[0,1]
$$

(2) 若 $(X,Y)$ 為離散型，則對任意 $(x,y)\in\mathbb{R}^2$，皆有

$$
F_{XY}(x,y)
=
\sum_{\substack{(u,v)\in\mathcal{R}_{XY}\\u\leqslant x,\ v\leqslant y}}
p_{XY}(u,v)
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.** $F_{XY}$ 的輸入 $(x,y)$ 可為任意實數有序對，而其輸出是事件機率，因此介於 $0$ 與 $1$ 之間。這便得到性質 (1)。

若 $(X,Y)$ 為離散型，則事件 $\lbrace X\leqslant x,Y\leqslant y\rbrace$ 可寫成互斥聯集

$$
\lbrace X\leqslant x,Y\leqslant y\rbrace
=
\bigsqcup_{\substack{(u,v)\in\mathcal{R}_{XY}\\u\leqslant x,\ v\leqslant y}}
\lbrace X=u,Y=v\rbrace
$$

由可數可加性，將聯集中的單點機率相加，即得性質 (2)。<span class="topic-qed">$\square$</span>
</div>

## 由聯合 pmf 計算聯合 cdf

<div id="example-32" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.2 (A Joint cdf from a Joint pmf)</div>

延續 [上一篇的 Example 3.1](/teaching-topics/random-vectors-joint-pmf/#example-31)。非零的聯合 pmf 為

$$
p_{XY}(x,y)
=
\frac{x+2y}{12},
\qquad
(x,y)\in
\lbrace(0,1),(0,2),(1,0),(1,1),(2,0)\rbrace
$$

先求 $F_{XY}(1,1)$。門檻左下方具有正機率的點為 $(0,1)$、$(1,0)$ 與 $(1,1)$，所以

$$
\begin{aligned}
F_{XY}(1,1)
&=
p_{XY}(0,1)+p_{XY}(1,0)+p_{XY}(1,1) \\[0.4em]
&=
\frac{2+1+3}{12}
=
\frac{1}{2}
\end{aligned}
$$

再考慮門檻 $(1.5,0.3)$。因為 $X$ 的可能取值只有 $0,1,2$，而 $Y$ 的可能取值只有 $0,1,2$，所以

$$
\begin{aligned}
F_{XY}(1.5,0.3)
&=
\mathbb{P}(X\leqslant1.5,Y\leqslant0.3) \\[0.4em]
&=
\mathbb{P}(X\leqslant1,Y\leqslant0) \\[0.4em]
&=
p_{XY}(1,0)
=
\frac{1}{12}
\end{aligned}
$$

這項計算也說明，聯合 cdf 的輸入可為任意實數。門檻本身不必屬於聯合值域；只須找出門檻左下方有哪些可能取值。
</div>

## 本篇小結

聯合 cdf 記錄門檻點 $(x,y)$ 左下方的累積機率。對離散型隨機向量，可把左下方所有單點的聯合 pmf 加總；對其他型態的聯合分配，[Definition 3.4](#definition-34) 仍然適用。

[下一篇文章](/teaching-topics/joint-probability-density-functions/)會考慮可由二重積分表示的聯合分配，並以聯合 pdf 描述平面區域上方的機率。

## 參考文獻與延伸閱讀

- 黃文璋，2003，《機率論》，初版，華泰文化。
- 黃文璋，2003，《數理統計》，初版，華泰文化。
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
