---
title: "條件機率，資訊進來以後，機率如何改變"
subtitle: "Conditional Probability and the Multiplication Rule"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 1
topic: 5
order: 105
permalink: /teaching-topics/conditional-probability-information/
date: 2026-05-05
excerpt: "條件機率描述在已知某個事件已經發生之後，我們如何重新評估另一個事件的機率。本篇從資訊的意義出發，介紹條件機率、乘法原理與廣義乘法原理。"
---

[上一篇文章](/teaching-topics/probability-rules-from-axioms/)整理了在同一個機率空間中可以使用的基本運算規則。由那些規則可知，一旦機率空間 $(S,\mathcal{F},\mathbb{P})$ 被指定以後，事件之間的聯集、交集、餘事件與大小關係便能轉化為機率運算。

但機率與統計更常處理的是「資訊的變化」。原本我們站在整個樣本空間中評估某事件的機率；一旦知道某個事件 $B$ 已經發生，原先的樣本空間便被縮小成 $B$ 所代表的世界，我們也必須在其中重新評估問題。條件機率 (conditional probability) 描述的就是資訊進來以後，機率如何改變。

以下固定令 $(S,\mathcal{F},\mathbb{P})$ 為一個機率空間。除非特別說明，文中的事件皆是 $\mathcal{F}$ 中的事件。

## 資訊會改變我們看的世界

先不要急著看公式。假設擲一顆公正骰子，令 $A$ 表示「點數至少為 $4$」，也就是 $A=\{4,5,6\}$。在沒有其他資訊時，樣本空間是 $\{1,2,3,4,5,6\}$，因此

$$
\mathbb{P}(A)=\frac{3}{6}=\frac{1}{2}
$$

現在加入一個資訊。點數是偶數。也就是說，我們知道事件 $B$ 發生，其中

$$
B=\{2,4,6\}
$$

此時我們已經不該再把 $1,3,5$ 放進討論裡；真正要看的，是 $B$ 裡面有多少結果也屬於 $A$。

<div class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 1.2</div>

「點數至少為 $4$」這個事件本身沒有改變；改變的是我們知道了「點數是偶數」這件資訊。資訊的作用不是改寫事件，而是改寫我們應該在哪個世界裡判斷事件。
</div>

在這個例子中，$A\cap B=\{4,6\}$。所以在已知 $B$ 發生之下，$A$ 發生的機率應為

$$
\frac{\mathrm{n}(A\cap B)}{\mathrm{n}(B)}
=\frac{2}{3}
$$

這個比例就是條件機率的原型。把「同時屬於 $A$ 與 $B$ 的部分」拿來和「已知會發生的 $B$」相比。

## 條件機率

<div class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.13</div>

令 $A,B\in\mathcal{F}$，且 $\mathbb{P}(B)>0$。則**在給定 $B$ 發生之下，$A$ 發生的條件機率 (conditional probability)** 定義為

$$
\mathbb{P}(A\mid B)=\frac{\mathbb{P}(A\cap B)}{\mathbb{P}(B)}
$$

</div>

這個定義的分子是 $A$ 與 $B$ 同時發生的機率；分母則是我們已經知道會發生的事件 $B$ 的機率。因此 $\mathbb{P}(A\mid B)$ 表示在 $B$ 所代表的新世界裡，$A$ 佔了多少比例。

<figure class="topic-figure topic-figure--medium">
  <img src="/images/teaching-topics/conditional-probability-region.svg" alt="條件機率的集合示意圖。已知 B 發生後，以 B 作為新的參照區域，A 只剩下 A cap B 的部分會被計入。">
  <figcaption><span class="topic-figure__label">Fig. 1.6.</span> 給定 $B$ 發生後，參照範圍縮小為 $B$；此時 $A$ 真正留下來的是 $A\cap B$。</figcaption>
</figure>

這也說明為什麼必須要求 $\mathbb{P}(B)>0$。如果 $B$ 在目前模型下機率為零，我們就無法用 $\mathbb{P}(B)$ 作為分母，把 $B$ 正規化成新的參照世界。這不只是代數上的除以零問題，也是「目前這個機率模型不足以直接回答給定 $B$ 之後如何重新分配機率」的問題。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

一般的非條件機率也可以看成一種條件機率。因為整個樣本空間 $S$ 必然發生，且 $\mathbb{P}(S)=1$，所以

$$
\mathbb{P}(A\mid S)=\frac{\mathbb{P}(A\cap S)}{\mathbb{P}(S)}=\mathbb{P}(A)
$$

因此，非條件機率是在沒有額外資訊時，以整個 $S$ 作為參照世界；條件機率則是在資訊進來後，以某個已知發生的事件作為參照世界。
</div>

## 條件機率仍然是機率

條件機率不是一個全新的規則，而是在新的參照世界中重新定義出的機率。更精確地說，只要固定給定事件 $B$，那麼

$$
A\longmapsto \mathbb{P}(A\mid B)
$$

本身仍然是一個機率測度。

<div class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Theorem 1.7 (Conditional Probability Measure)</div>

令 $B\in\mathcal{F}$，且 $\mathbb{P}(B)>0$。則 $\mathbb{P}(\,\cdot\,\mid B)$ 為一個機率測度。
</div>

<div class="topic-proof" markdown="1">
**Proof.** 對任意 $A\in\mathcal{F}$，因為 $\mathbb{P}(A\cap B)\geq 0$ 且 $\mathbb{P}(B)>0$，所以

$$
\mathbb{P}(A\mid B)\geq 0
$$

此外，樣本空間本身滿足

$$
\mathbb{P}(S\mid B)
=\frac{\mathbb{P}(S\cap B)}{\mathbb{P}(B)}
=\frac{\mathbb{P}(B)}{\mathbb{P}(B)}
=1
$$

最後，若 $A_1,A_2,\ldots$ 兩兩互斥，則 $A_1\cap B,A_2\cap B,\ldots$ 也兩兩互斥。因此

$$
\begin{aligned}
\mathbb{P}\left(\bigcup_{i=1}^{\infty}A_i\,\middle|\,B\right)
&=\frac{\mathbb{P}\left(\left(\bigcup_{i=1}^{\infty}A_i\right)\cap B\right)}{\mathbb{P}(B)}\\[0.45em]
&=\frac{\mathbb{P}\left(\bigcup_{i=1}^{\infty}(A_i\cap B)\right)}{\mathbb{P}(B)}\\[0.45em]
&=\frac{\sum_{i=1}^{\infty}\mathbb{P}(A_i\cap B)}{\mathbb{P}(B)}\\[0.45em]
&=\sum_{i=1}^{\infty}\frac{\mathbb{P}(A_i\cap B)}{\mathbb{P}(B)}
=\sum_{i=1}^{\infty}\mathbb{P}(A_i\mid B)
\end{aligned}
$$

故 $\mathbb{P}(\,\cdot\,\mid B)$ 滿足機率三大公理。 $\square$
</div>

此定理說明，只要條件固定，前面學過的機率規則仍然可以使用。真正需要小心的是，不同條件代表不同參照世界；若一個式子裡的條件改來改去，就不能把它們當成同一個機率空間裡的普通機率直接相加或比較。

<div class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 1.3</div>

固定給定事件 $B$。在 $B$ 這個參照世界裡，事件 $A$ 發生與事件 $A^{\prime}$ 發生仍然是互補的兩種情況，所以

$$
\mathbb{P}(A\mid B)+\mathbb{P}(A^{\prime}\mid B)=1
$$

那麼下面這個式子呢？

$$
\mathbb{P}(A\mid B)+\mathbb{P}(A\mid B^{\prime})
$$

它也會等於 $1$ 嗎？答案通常是否定的。第一項是在 $B$ 的世界裡看 $A$，第二項是在 $B^{\prime}$ 的世界裡看 $A$；兩者的條件不同，參照世界也不同。我有時會戲稱這是「張飛打岳飛問題」。看起來都在談 $A$，但其實時空錯置，條件根本對不上。條件對不上時，就不能套用餘事件公式把兩項湊成 $1$。
</div>

## 乘法原理

條件機率的定義可以直接移項，得到交集機率的一個常用表示法。

<div class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Theorem 1.8 (Multiplication Rule)</div>

令 $A,B\in\mathcal{F}$，且 $\mathbb{P}(B)>0$。則

$$
\mathbb{P}(A\cap B)=\mathbb{P}(A\mid B)\,\mathbb{P}(B)
$$

此性質稱為**乘法原理 (multiplication rule)**。若 $\mathbb{P}(A)>0$，同理也有

$$
\mathbb{P}(A\cap B)=\mathbb{P}(B\mid A)\,\mathbb{P}(A)
$$

</div>

乘法原理的用途在於，當交集機率不好直接算，但條件機率容易描述時，我們可以先算「第一個事件發生的機率」，再乘上「在第一個事件已經發生之下，第二個事件發生的機率」。

<div class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.8 (Two Cards without Replacement)</div>

自一副 $52$ 張撲克牌中連續抽兩張牌，取後不放回。令 $N_1$ 表示第一張不是 King，$N_2$ 表示第二張不是 King。若要求兩張都不是 King 的機率，則

$$
\mathbb{P}(N_1\cap N_2)
=\mathbb{P}(N_1)\,\mathbb{P}(N_2\mid N_1)
=\frac{48}{52}\cdot\frac{47}{51}
$$

第一個分數是在整副牌中沒有抽到 King 的機率；第二個分數則是在第一張已經不是 King 之後，剩下 $51$ 張牌中還有 $47$ 張不是 King 的條件機率。
</div>

這個例子顯示，條件機率經常讓「有順序的隨機過程」變得自然。若事件的發生會改變下一步的狀態，例如不放回抽樣、疾病檢驗後的判斷、或逐步篩選樣本，乘法原理通常比直接列舉整個樣本空間更容易使用。

## 廣義乘法原理

若條件不只一層，乘法原理可以一路推廣。直覺上，我們先計算第一步的機率，再依序乘上每一步在前面資訊已經發生下的條件機率。

<div class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Theorem 1.9 (General Multiplication Rule)</div>

令 $A_1,\ldots,A_n\in\mathcal{F}$。若對每個 $k=1,\ldots,n-1$，前 $k$ 個事件的交集皆有正機率，則

$$
\mathbb{P}\left(\bigcap_{i=1}^{n}A_i\right)
=\mathbb{P}(A_1)\prod_{k=2}^{n}
\mathbb{P}\left(A_k\,\middle|\,\bigcap_{i=1}^{k-1}A_i\right)
$$

此性質稱為**廣義乘法原理 (general multiplication rule)**。
</div>

<div class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.9 (No Kings in Five Cards)</div>

自一副 $52$ 張撲克牌中抽取五張牌，取後不放回，求其中沒有任何 King 的機率。令 $N_i$ 表示第 $i$ 張牌不是 King，則

$$
\begin{aligned}
\mathbb{P}\left(\bigcap_{i=1}^{5}N_i\right)
&=\mathbb{P}(N_1)\,\cdot\,\mathbb{P}(N_2\mid N_1)
\,\cdot\,\mathbb{P}(N_3\mid N_1\cap N_2)\\[0.45em]
&\quad\cdot\,\mathbb{P}(N_4\mid N_1\cap N_2\cap N_3)
\,\cdot\,\mathbb{P}(N_5\mid N_1\cap N_2\cap N_3\cap N_4)\\[0.8em]
&=\frac{48}{52}\cdot\frac{47}{51}\cdot\frac{46}{50}\cdot\frac{45}{49}\cdot\frac{44}{48}
\end{aligned}
$$

如果用組合方法，也可以寫成 $\binom{48}{5}/\binom{52}{5}$。兩種方法給出的結果相同；乘法原理的好處是，它直接跟「依序抽牌、取後不放回」這個實驗流程相吻合。
</div>

<div class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 1.4</div>

如果你用過 Excel 的**樞紐分析表 (PivotTable)**，或旁邊那種按鈕式的**交叉分析篩選器 (slicer)**，那其實你就已經看過乘法原理的影子。每勾選一個欄位條件，資料表就被縮小一次；勾選越多條件，留下來的資料列就必須同時滿足越多要求。

要求 $A\cap B\cap C$ 的機率時，也可以想成要把資料一步一步篩到同時滿足三個條件。若先篩 $A$，再篩 $B$，最後篩 $C$，就會得到

$$
\mathbb{P}(A\cap B\cap C)
=\mathbb{P}(A)\,\mathbb{P}(B\mid A)\,\mathbb{P}(C\mid A\cap B)
$$

也可以先篩 $B$，再篩 $A$，最後篩 $C$。

$$
\mathbb{P}(A\cap B\cap C)
=\mathbb{P}(B)\,\mathbb{P}(A\mid B)\,\mathbb{P}(C\mid A\cap B)
$$

兩條路線最後指向同一個交集，只是每一步的條件機率會跟著篩選順序改變。換句話說，路線可以換，但條件不能亂配；乘法原理不是在說每一步都一樣，而是在說只要每一步的條件接對，就能沿著一條合法路線走到同一個交集事件。
</div>

## 條件不能隨意交換

最後要先提醒一個常見誤解。$\mathbb{P}(A\mid B)$ 與 $\mathbb{P}(B\mid A)$ 通常不是同一件事。前者問的是「在 $B$ 已知發生之下，$A$ 的機率」；後者問的是「在 $A$ 已知發生之下，$B$ 的機率」。兩者的分母不同，參照世界也不同。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

條件機率之所以重要，不只是因為它能計算「已知某事後的機率」，更因為它讓我們可以討論資訊如何改變判斷。當我們之後想由 $\mathbb{P}(B\mid A)$ 推回 $\mathbb{P}(A\mid B)$ 時，就會自然走向貝氏定理 (Bayes' rule)。
</div>

## 本篇小結

本篇將條件機率理解為「資訊進來以後的重新評估」。

| 工具 | 公式 | 重點 |
| --- | --- | --- |
| 條件機率 | $\mathbb{P}(A\mid B)=\mathbb{P}(A\cap B)/\mathbb{P}(B)$ | 在已知 $B$ 發生後重新看 $A$ |
| 條件機率測度 | $A\mapsto\mathbb{P}(A\mid B)$ | 固定條件後仍是機率 |
| 乘法原理 | $\mathbb{P}(A\cap B)=\mathbb{P}(A\mid B)\,\mathbb{P}(B)$ | 用條件機率還原交集機率 |
| 廣義乘法原理 | 依序相乘 | 適合描述逐步加入條件的篩選過程 |

[下一篇文章](/teaching-topics/total-probability-bayes-rule/)將把條件機率與「分類」放在一起。若樣本空間被一組事件分割成互斥且完整的情況，我們就能得到全機率定理。再往後，若想用新資訊反過來修正原先對各種情況的判斷，就會進入貝氏定理。

## 參考文獻與延伸閱讀

- Sheldon M. Ross, *A First Course in Probability*, chapters on conditional probability and multiplication rules.
- Joseph K. Blitzstein and Jessica Hwang, *Introduction to Probability*, chapters on conditioning and Bayes rule.
- Morris H. DeGroot and Mark J. Schervish, *Probability and Statistics*, chapters on conditional probability.
- Michael Woodroofe, *Probability with Applications*, McGraw-Hill, 1975, Chapter 10 on conditional probability.
- Peter J. Bickel and Kjell A. Doksum, *Mathematical Statistics, Basic Ideas and Selected Topics*, Holden-Day, 1977, early sections on conditioning and statistical reasoning.
- Alfréd Rényi, “On Conditional Probability Spaces Generated by a Dimensionally Ordered Set of Measures”, *Theory of Probability and Its Applications*, 1(1), 55–64, 1956. [doi:10.1137/1101005](https://doi.org/10.1137/1101005).
- David Blackwell and Lester E. Dubins, “On Existence and Non-Existence of Proper, Regular, Conditional Distributions”, *The Annals of Probability*, 3(5), 741–752, 1975. [doi:10.1214/aop/1176996261](https://doi.org/10.1214/aop/1176996261).
