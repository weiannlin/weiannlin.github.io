---
title: "機率如何被指定，古典機率、計數測度與幾何機率"
subtitle: "Classical Probability, Counting Measure, and Geometric Probability"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 1
topic: 3
order: 103
permalink: /teaching-topics/probability-assignment-classical-geometric/
date: 2026-05-05
excerpt: "公理化機率給出合法機率函數的條件，卻不直接說明機率應該怎麼算。本文以古典機率、計數測度、幾何機率、客觀機率與主觀機率說明不同的指定方式。"
---

[上一篇文章](/teaching-topics/event-families-sigma-fields/)建立了由 $(S,\mathcal{F},\mathbb{P})$ 描述的機率空間。其中 $S$ 說明所有可能結果，$\mathcal{F}$ 說明哪些事件可以被賦予機率，而 $\mathbb{P}$ 則把每個可測事件送到一個數值。

但這裡有一個很自然的問題：$\mathbb{P}$ 到底怎麼來？

柯爾莫哥洛夫機率公理 (Kolmogorov axioms) 並沒有說明機率應該如何被計算。它說的是：不論你用什麼方式指定機率，最後得到的函數都必須滿足非負性、歸一性與可數可加性。換句話說，公理像是驗收規格；真正的建模工作，還需要說明機率數值從哪裡來。

## 公理與計算模型

在建立機率模型時，可以把問題拆成兩層。

| 問題 | 對應物件 | 角色 |
| --- | --- | --- |
| 哪些結果可能發生？ | $S$ | 樣本空間 |
| 哪些事件可以被討論？ | $\mathcal{F}$ | 事件集合族 |
| 每個事件的可能性多大？ | $\mathbb{P}$ | 機率函數 |

主題二處理的是前兩層與合法性條件。本文處理第三層：在不同情境下，我們如何指定機率函數 $\mathbb{P}$ 的數值。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">閱讀提示</div>

本文不是要把所有排列組合技巧一次講完，而是先說明它們在機率論中的位置。排列、組合、長度、面積、相對次數或主觀判斷，都可以是指定機率的來源；但指定完成後，它們仍必須回到 Kolmogorov 公理之下，成為一個合法的機率函數。
</div>

## 古典機率：有限且均等可能

最熟悉的機率計算通常出現在有限樣本空間中。若每個樣本點都被視為均等可能，則事件的機率可以用「有利結果數」除以「所有可能結果數」來計算。

<div class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.11</div>

令 $S$ 為一個有限樣本空間，且假設 $S$ 中每一個樣本點皆為均等可能 (equally likely)。若 $A$ 為 $S$ 中之一事件，則 $A$ 的**古典機率 (classical probability)** 定義為

$$
\mathbb{P}(A)=\frac{\mathrm{n}(A)}{\mathrm{n}(S)}
$$

其中 $\mathrm{n}(\cdot)$ 為點算集合中元素個數之函數。
</div>

這個定義的關鍵不是分數本身，而是**均等可能性 (equally likely)**。如果骰子是公正的，六個點數可以被視為均等可能；如果骰子被動過手腳，則同一個公式就不再適合直接使用。

從測度觀點來看，$\mathrm{n}(\cdot)$ 其實是在衡量集合中有多少個樣本點，因此可視為一種**計數測度 (counting measure)**。古典機率就是把計數測度正規化，使整個樣本空間的總機率變成一。

## 排列組合扮演什麼角色

在古典機率中，真正要算的是 $\mathrm{n}(A)$ 與 $\mathrm{n}(S)$ 這兩個數量。當樣本空間很小時，我們可以直接列出所有樣本點；當樣本空間很大時，就需要排列組合來幫忙點算。

<div class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.4 (Two Dice)</div>

投擲一顆公正骰子兩次，觀察兩次出現的點數，且考慮順序。此時

$$
S=\lbrace\,(x,y)\mid x,y\in\lbrace1,2,3,4,5,6\rbrace\,\rbrace
$$

因此

$$
\mathrm{n}(S)=6\times 6=36
$$

若 $A$ 表示兩次點數和為 $10$ 之事件，則

$$
A=\lbrace(4,6),(5,5),(6,4)\rbrace
$$

所以

$$
\mathbb{P}(A)
=\frac{\mathrm{n}(A)}{\mathrm{n}(S)}
=\frac{3}{36}
=\frac{1}{12}
$$

</div>

這個例子還可以直接列舉；但若問題改成「一副撲克牌抽出五張，恰為同花順的機率」，我們就不會真的列出所有手牌，而會用組合數計算

$$
\mathrm{n}(S)=\binom{52}{5}
$$

因此，排列組合不是另一套機率理論，而是古典機率裡用來點算樣本點數的工具。

## 幾何機率：用幾何測度取代點數

若樣本空間不再是有限集合，而是一段區間、一塊平面區域或一個立體範圍，就不能再用樣本點個數來計算比例。這時候可以把「點數」替換成長度、面積、體積或其他幾何測度。

<div class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.12</div>

令樣本空間 $S$ 為一幾何範圍，而 $A$ 為 $S$ 中之一可測事件。若 $m(\cdot)$ 為適當的**幾何測度 (geometric measure)**，且 $0<m(S)<\infty$，則 $A$ 的**幾何機率 (geometric probability)** 定義為

$$
\mathbb{P}(A)=\frac{m(A)}{m(S)}
$$

</div>

在一維中，$m(\cdot)$ 可以是長度；在二維中，可以是面積；在三維中，可以是體積。它背後仍然是一個「均勻」的想法：如果落點在整個區域中沒有偏向任何特定位置，事件的機率就由該事件所佔的幾何比例決定。

<div class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.5 (Geometric Probability by Area)</div>

假設炸彈會隨機落在半徑為 $1$ 的圓形區域內，且若落點距離圓心不超過 $0.5$，就能摧毀目標。令

$$
S=\lbrace\,(x,y)\mid x^2+y^2\leq 1\,\rbrace
$$

而 $A$ 為落在半徑 $0.5$ 之圓內的事件。若以面積作為幾何測度，則

$$
\mathbb{P}(A)=\frac{m(A)}{m(S)}
=\frac{\pi(0.5)^2}{\pi(1)^2}
=\frac{1}{4}
$$

</div>

幾何機率可以看成古典機率的連續版本：古典機率用計數測度衡量集合大小；幾何機率則用長度、面積或體積衡量集合大小。

## 客觀機率與主觀機率

古典機率與幾何機率都依賴某種均等可能或均勻性假設。但許多真實問題並沒有明顯的均等可能樣本點，也不一定能用幾何比例描述。這時候，機率可能來自長期重複觀察，也可能來自研究者根據證據與專業知識所做的判斷。

<div class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.13</div>

令 $\mathrm{n}_N(A)$ 為 $N$ 次重複之隨機實驗中，事件 $A$ 發生的次數。若極限存在，則可定義

$$
\mathbb{P}(A)=\lim_{N\to\infty}\frac{\mathrm{n}_N(A)}{N}
$$

稱為 $A$ 的**客觀機率 (objective probability)**，亦稱為**相對次數機率 (relative frequency probability)** 或**經驗機率 (empirical probability)**。
</div>

例如一位籃球員過去大量三分球出手中的命中比例，可以作為估計下一次命中機率的經驗依據。這個想法不需要假設所有樣本點均等可能，但它需要大量可重複觀察，而且極限是否穩定也需要被檢查。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">後續伏筆</div>

客觀機率把機率理解為長期相對次數的極限。之後討論**弱大數法則 (Weak Law of Large Numbers, WLLN)** 時，我們會從另一個方向回到這個直覺：在一個已經指定的機率模型中，相對次數會以機率的方式靠近它的理論機率。

換句話說，客觀機率提供「機率可以來自長期頻率」的建模直覺；弱大數法則則說明，當機率模型已經成立時，長期頻率在什麼意義下會靠近模型給出的機率。讀者若已學過蒙提霍爾問題 (Monty Hall problem)，也可以參考 Demos 中的[蒙提霍爾問題實作](/demos/monty-hall/)；其中的模擬部分正好展示相對次數如何隨重複次數增加而逐漸穩定。
</div>

<div class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.14</div>

研究者依照其專業知識或相關證據，主觀地認定事件 $A$ 發生之機率

$$
\mathbb{P}(A)\in[0,1]
$$

此種機率稱為**主觀機率 (subjective probability)**。
</div>

主觀機率不是隨意猜測，而是一種把證據、經驗與模型判斷轉換成機率數值的方式。例如降雨機率往往結合歷史資料、物理模型與氣象專家的判斷。即使來源較主觀，最後形成的機率指定仍應避免違反機率公理。

## 回到 Kolmogorov 公理

這幾種機率看起來來源不同，但它們在現代機率論中扮演的是同一個角色：提供一個候選的機率函數。

<div class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Proposition 1.2 (Normalized Counting Measure)</div>

若 $S$ 為有限非空集合，且對任意 $A\subset S$ 定義

$$
\mathbb{P}(A)=\frac{\mathrm{n}(A)}{\mathrm{n}(S)}
$$

則 $\mathbb{P}$ 是 $2^S$ 上的一個機率函數。
</div>

<div class="topic-proof" markdown="1">
**Proof.** 對任意 $A\subset S$，$\mathrm{n}(A)\geq 0$，所以其機率非負。又因為 $\mathrm{n}(S)/\mathrm{n}(S)=1$，所以樣本空間的機率為一。

若 $A_1,A_2,\ldots$ 兩兩互斥，且皆為 $S$ 的子集合，則因為 $S$ 為有限集合，其中至多只有有限多個 $A_i$ 非空。由計數的可加性可得

$$
\mathrm{n}\left(\bigcup_{i=1}^{\infty}A_i\right)=\sum_{i=1}^{\infty}\mathrm{n}(A_i)
$$

兩邊同除以 $\mathrm{n}(S)$，即可得到可數可加性。因此 $\mathbb{P}$ 滿足 Kolmogorov 公理。 $\square$
</div>

同樣地，若 $m(\cdot)$ 本身是一個定義在 $\mathcal{F}$ 上的測度，且 $0<m(S)<\infty$，則

$$
\mathbb{P}(A)=\frac{m(A)}{m(S)}
$$

也會形成一個機率函數。這就是為什麼「用面積除以總面積」不只是直覺公式，而是可以被放回公理化機率系統中的合法模型。

## 本篇小結

Kolmogorov 公理不告訴我們機率要怎麼算；它告訴我們算出來的東西必須像一個機率函數。不同情境下，指定 $\mathbb{P}$ 的方式可能不同：

| 指定方式 | 核心想法 | 典型工具 |
| --- | --- | --- |
| 古典機率 | 有限均等可能樣本點 | 計數測度、排列組合 |
| 幾何機率 | 均勻落在幾何範圍中 | 長度、面積、體積 |
| 客觀機率 | 長期重複觀察的相對次數 | 極限、經驗資料 |
| 主觀機率 | 根據證據與專業知識判斷 | 模型、經驗、信念更新 |

因此，機率計算並不是單一公式，而是一個建模選擇。選定模型後，[下一篇](/teaching-topics/probability-rules-from-axioms/)將進一步研究這個 $\mathbb{P}$ 會推出哪些基本性質，例如虛無事件機率、有限可加性、餘事件公式與加法原理。
