---
title: "眾數與分配形狀"
subtitle: "Mode and Distribution Shape"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 10
order: 210
permalink: /teaching-topics/mode-and-distribution-shape/
date: 2026-06-20
published: true
excerpt: "眾數描述機率或密度最集中的位置。期望值、中位數與眾數都是中央趨勢量數，但在有偏分配中，三者對尾端與極端值的靈敏程度並不相同。"
---

[上一篇文章](/teaching-topics/quantiles-and-median/)討論分位數與中位數，由累積機率描述分配位置。本篇回到 PMF 與 PDF 本身，討論哪個位置的機率或密度最集中。

本篇討論另一個常見的中央趨勢量數，也就是**眾數 (mode)**。眾數關心的是機率函數或密度函數最高的位置。同時，我們也會開始從中央趨勢量數走向分配形狀的觀察，並為後面討論偏態與峰態作準備。

## 眾數的定義

離散型隨機變數的眾數，是使 PMF 達到最大值的可能取值。若 $X$ 具有 PDF，則眾數是使密度函數達到最大值的位置。

<div id="definition-213" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.13</div>

若 $X$ 為離散型隨機變數，且 $m_o\in\mathcal{R}_X$ 滿足

$$
p_X(m_o)\geqslant p_X(x),
\qquad \forall x\in\mathcal{R}_X
$$

則稱 $m_o$ 為 $X$ 的**眾數 (mode)**。

若 $X$ 具有 PDF $f_X$，且 $m_o\in\mathcal{R}_X$ 滿足

$$
f_X(m_o)\geqslant f_X(x),
\qquad \forall x\in\mathcal{R}_X
$$

則亦稱 $m_o$ 為 $X$ 的眾數。

</div>

這裡的眾數指的是母體眾數 (population mode)，與敘述統計學中的樣本眾數 (sample mode) 不同。樣本眾數由一組實際資料決定；母體眾數則由隨機變數的分配決定。

<div class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 2.12</div>

雖然樣本眾數與母體眾數不是同一個定義，但背後觀念相同。例如一組資料為

$$
2,\ 2,\ 2,\ 3,\ 4
$$

其中 $2$ 出現最多次，所以樣本眾數為 $2$。若把這組資料轉換成經驗機率分配，則

$$
\mathbb{P}(X=2)=\frac{3}{5},
\qquad
\mathbb{P}(X=3)=\frac{1}{5},
\qquad
\mathbb{P}(X=4)=\frac{1}{5}
$$

因此，在這個經驗機率分配中，$2$ 也正是機率最大的點。換句話說，樣本眾數是資料中出現最多次的觀察值；母體眾數則是轉成機率分配後，機率函數或密度函數最高的位置。
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

離散型情形中，眾數可說是最可能取到的值。連續型情形中，單點機率仍為 $0$，所以眾數未必永遠是用機率去選擇，但意義上，它確實是「最有可能」出現的一個點。
</div>

## 眾數未必唯一

眾數和中位數一樣，未必唯一。甚至在某些連續型例子中，若密度函數的最大值沒有在 $\mathcal{R}_X$ 內被達到，眾數也可能不存在。

<div id="example-216" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.16 (Two Modes)</div>

令 $X$ 的 PMF 為

$$
\begin{array}{c|cccc}
x & 1 & 2 & 3 & 4\\
\hline
p_X(x) & 0.10 & 0.40 & 0.40 & 0.10
\end{array}
$$

此時 $p_X(2)=p_X(3)=0.40$，且這兩個值同時達到最大。因此 $2$ 與 $3$ 都是 $X$ 的眾數。
</div>

## 峰的個數

若一個分配只有一個主要高峰，稱為**單峰分配 (unimodal distribution)**。若有兩個高峰，稱為**雙峰分配 (bimodal distribution)**。若有多個高峰，則稱為**多峰分配 (multimodal distribution)**。在這類圖形描述中，所謂高峰通常指的是 PMF 或 PDF 的**局部最大值 (local maximum)**。

這裡要和 [Definition 2.13](#definition-213) 稍作區分。前面的定義是從「哪個位置使 PMF 或 PDF 達到最大」來定義眾數；本節談分配形狀時，所謂高峰則比較接近微積分中的局部最大值。由此來看，雙峰或多峰分配並不要求每個峰的高度完全相同。

<figure class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/mode-distribution-shape.svg?v=multimodal-axis-longer" alt="單峰、雙峰與多峰分配中的高峰個數示意。">
  <figcaption><span class="topic-figure__label">Fig. 2.17.</span> 圖中標示的是高峰的個數。高峰高度不必相同，重點在於分配是否具有一個以上的局部集中位置。</figcaption>
</figure>

## 對稱、右偏與左偏

峰的個數與尾巴方向是兩件不同的事情。單峰分配可以是對稱的，也可以右偏或左偏。這裡的「偏」指的是尾巴延伸的方向，而不是高峰所在的位置。

若分配是單峰且對稱的，期望值、中位數與眾數常會落在同一個位置。常態分配就是最典型的例子。若分配不對稱，三者便可能分開。以常見的單峰右偏分配為例，尾巴向右延伸，期望值會被右尾拉動，中位數也會受到影響，但通常不如期望值明顯；眾數則多半留在主要高峰附近。左偏分配則方向相反。

<figure class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/skewness-shape-preview.svg?v=skew-preview-20260620" alt="右偏、左偏與對稱分配中期望值、中位數與眾數的位置示意。">
  <figcaption><span class="topic-figure__label">Fig. 2.18.</span> 對稱、右偏與左偏描述的是尾巴方向。常見的單峰右偏分配中，眾數、中位數與期望值常依序向右分開；左偏時方向相反。圖中依序為右偏、左偏與對稱分配。</figcaption>
</figure>

## 三個中央趨勢量數

到目前為止，我們已經看過三個常用中央趨勢量數。它們都描述分配的中央趨勢，但各自依據不同。

| 量數 | 記號 | 依據 |
| --- | --- | --- |
| 期望值 | $\mu_X=\mathbb{E}(X)$ | 依機率加權平均 |
| 中位數 | $\eta_X$ | 使左右兩側機率各至少一半 |
| 眾數 | $m_o$ | 使 PMF 或 PDF 達到最高 |

前一節是從圖形上看三者的相對位置。若進一步比較尾端或極端值對中央趨勢量數的影響，期望值通常最敏感，中位數次之，眾數則多半較不受尾端少數值牽動。

<div class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 2.13</div>

設想一個班級中大多數人的收入集中在某個普通範圍，但有少數人的收入非常高。若把所有人的收入視為一個分配，期望值會被這些極端高值往右拉動；中位數只關心排在中間的人，所以變動較小；眾數則看最常出現或最集中的收入區域，通常更貼近主要群體。

因此，若比較的是尾端或極端值對中央趨勢量數的影響，常見的靈敏程度為期望值最大，中位數次之，眾數通常最小。不過，眾數本身也有弱點。若分配有多個高峰，或密度曲線在局部產生細微變化，眾數可能不唯一，甚至不易判定。
</div>

這裡的比較要注意範圍。期望值、中位數與眾數的靈敏程度，是在討論尾端或極端值如何拉動中央趨勢量數；它不是說眾數在任何情形下都最穩定。眾數只看最高處，因此它對分配主峰附近的變化反而可能很敏感。

## 從眾數走向形狀

眾數把我們帶到分配形狀的問題。若一個分配只有一個高峰，三個中央趨勢量數可以共同描述其中央趨勢與集中位置。若分配有長尾，期望值與中位數、眾數會分開。若分配有多個高峰，單一中央趨勢量數甚至可能不足以描述整個分配。

後面討論偏態時，會把尾巴方向轉成可以計算的量數。至於峰態，則會進一步討論分配尾端與集中情況，而不只是看圖形高峰是否尖銳。

## 本篇小結

眾數是使 PMF 或 PDF 達到最高的位置，記作 $m_o$。離散型眾數可解釋為最可能取到的值；連續型眾數則是密度曲線最高的位置。眾數可能不唯一，也可能不存在。

期望值、中位數與眾數分別從加權平均、累積機率與最高密度三個角度描述中央趨勢。在有偏分配中，期望值通常最容易被尾端極端值拉動，中位數次之，眾數則多半反映主要高峰所在。下一篇[偏態與峰態](/teaching-topics/skewness-and-kurtosis/)會把這些圖形觀察轉成可計算的形狀量數。

## 參考文獻與延伸閱讀

- 黃文璋，2003，《機率論》，初版，華泰文化。
- 黃文璋，2003，《數理統計》，初版，華泰文化。
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Sheldon M. Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
