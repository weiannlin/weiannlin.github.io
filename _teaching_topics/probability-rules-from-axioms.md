---
title: "由公理推出機率運算：餘事件、單調性與加法原理"
subtitle: "Probability Rules from the Kolmogorov Axioms"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 1
topic: 4
order: 104
permalink: /teaching-topics/probability-rules-from-axioms/
date: 2026-05-05
excerpt: "Kolmogorov 公理本身很短，卻能推出一整套機率運算規則。本文從虛無事件、有限可加性與餘事件公式開始，進一步整理單調性、加法原理、排容原理與常用機率不等式。"
---

[上一篇文章](/teaching-topics/probability-assignment-classical-geometric/)說明了不同情境下如何指定機率函數，也就是 $\mathbb{P}$ 的來源。一旦 $\mathbb{P}$ 被指定，並且滿足 Kolmogorov 公理，我們就可以不再依賴特定模型，而是直接從公理推出一系列共同成立的運算規則。

本文固定令 $(S,\mathcal{F},\mathbb{P})$ 為一個機率空間。除非特別說明，文中的事件皆是 $\mathcal{F}$ 中的事件。

## 第一個推論：虛無事件的機率

Kolmogorov 公理直接指定 $\mathbb{P}(S)=1$，但沒有直接指定虛無事件的機率。若以 $\varnothing$ 表示虛無事件，這件事可以由可數可加性推出。

<div class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Theorem 1.1</div>

在任一機率空間 $(S,\mathcal{F},\mathbb{P})$ 中，虛無事件滿足

$$
\mathbb{P}(\varnothing)=0
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.** 令 $A_1$ 為整個樣本空間，且對所有 $i\geq 2$，令 $A_i$ 為虛無事件。則 $A_1,A_2,\ldots$ 兩兩互斥，且其聯集滿足

$$
\bigcup_{i=1}^{\infty}A_i=S
$$

由可數可加性可知

$$
\mathbb{P}(S)
=\mathbb{P}(S)+\sum_{i=2}^{\infty}\mathbb{P}(\varnothing)
$$

因此 $\sum_{i=2}^{\infty}\mathbb{P}(\varnothing)=0$，也就是後面所有虛無事件機率的總和為零。再由非負性可得虛無事件的機率為 $0$，故得證。 $\square$
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

$\mathbb{P}(\varnothing)=0$ 表示不可能事件的機率必為零。但反過來並不一定成立：機率為 $0$ 的事件未必是不可能事件。這正好呼應[思想實驗 1.1](/teaching-topics/random-experiments-sample-space-events/#thought-experiment-dart-zero-probability)中的飛鏢例子：在以面積指定機率的連續落點模型中，某個特定點可以是樣本空間中的可能結果；若這個單點集合被納入事件集合族，則它的面積為零，機率也為零。換句話說，不可能發生的事件機率必為零，但機率為零的事件未必不可能發生。
</div>

## 有限可加性

可數可加性可以處理可數多個兩兩互斥事件。若只討論有限多個互斥事件，它自然推出一個較常用的版本，稱為有限可加性。

<div class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Theorem 1.2</div>

若 $A_1,\ldots,A_n\in\mathcal{F}$ 且兩兩互斥，則

$$
\mathbb{P}\left(\bigcup_{i=1}^n A_i\right)=\sum_{i=1}^n\mathbb{P}(A_i)
$$

此性質稱為**有限可加性 (finite additivity)**。
</div>

<div class="topic-proof" markdown="1">
**Proof.** 對所有 $k>n$，令 $A_k$ 為虛無事件。則可數聯集等同於前 $n$ 個事件的聯集：

$$
\bigcup_{i=1}^{\infty}A_i=\bigcup_{i=1}^{n}A_i
$$

由可數可加性與 Theorem 1.1 可知

$$
\mathbb{P}\left(\bigcup_{i=1}^{n}A_i\right)
=\sum_{i=1}^{n}\mathbb{P}(A_i)+\sum_{i=n+1}^{\infty}\mathbb{P}(\varnothing)
=\sum_{i=1}^{n}\mathbb{P}(A_i)
$$

因此有限可加性成立。 $\square$
</div>

有限可加性的重點在於「互斥」。若事件彼此沒有重疊，聯集的機率就可以直接相加；若事件之間有重疊，直接相加就會把重疊部分重複計算。

## 餘事件公式

對任意事件 $A$，其餘事件 $A^{\prime}$ 是所有不屬於 $A$ 的樣本點所形成的事件。因此 $A$ 與 $A^{\prime}$ 彼此互斥，且二者合起來正好是整個樣本空間：

$$
S=A\cup A^{\prime}, \qquad A\cap A^{\prime}=\varnothing
$$

<figure class="topic-figure topic-figure--compact">
  <img src="/images/teaching-topics/probability-rules-complement.svg" alt="餘事件 A prime 的集合示意圖：樣本空間 S 中，事件 A 外側的區域為 A prime。">
  <figcaption><span class="topic-figure__label">Fig. 1.1.</span> 餘事件 $A^{\prime}$ 是樣本空間中不屬於 $A$ 的部分。</figcaption>
</figure>

因此，有限可加性立刻給出餘事件公式。

<div class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Theorem 1.3</div>

對任意事件 $A\in\mathcal{F}$，皆有

$$
\mathbb{P}(A^{\prime})=1-\mathbb{P}(A)
$$

同時也有

$$
0\leq \mathbb{P}(A)\leq 1
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.** 因為 $A$ 與 $A^{\prime}$ 互斥，且 $A\cup A^{\prime}=S$，所以

$$
1=\mathbb{P}(S)=\mathbb{P}(A)+\mathbb{P}(A^{\prime})
$$

故可得到餘事件公式。又由非負性可知 $\mathbb{P}(A)\geq 0$ 且 $\mathbb{P}(A^{\prime})\geq 0$，因此 $\mathbb{P}(A)\leq 1$，也就是事件機率至多為一。 $\square$
</div>

<div class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.6</div>

若某製程中，一件產品不良的機率為 $0.03$，則產品合格的機率為

$$
1-0.03=0.97
$$

在許多問題中，直接計算目標事件不容易，但計算它的餘事件比較簡單。此時餘事件公式往往是最省力的做法。
</div>

## 單調性：較小的事件，機率不會較大

若 $A\subset B$，則事件 $A$ 發生時，事件 $B$ 一定發生。直觀上，$B$ 至少包含 $A$ 的所有可能結果，因此 $B$ 的機率不應小於 $A$ 的機率。

<div class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Theorem 1.4</div>

若 $A,B\in\mathcal{F}$ 且 $A\subset B$，則

$$
\mathbb{P}(B-A)=\mathbb{P}(B)-\mathbb{P}(A)
$$

並且滿足

$$
\mathbb{P}(A)\leq \mathbb{P}(B)
$$

後者稱為機率的**單調性 (monotonicity)**。
</div>

<figure class="topic-figure topic-figure--medium">
  <img src="/images/teaching-topics/probability-rules-monotonicity.svg" alt="單調性的集合示意圖：事件 A 包含於事件 B 中，B 比 A 多出的部分是差集 B-A。">
  <figcaption><span class="topic-figure__label">Fig. 1.2.</span> 當 $A\subset B$ 時，$B$ 比 $A$ 多出的部分是 $B-A$，因此 $\mathbb{P}(A)\leq\mathbb{P}(B)$。</figcaption>
</figure>

<div class="topic-proof" markdown="1">
**Proof.** 因為 $A\subset B$，可將 $B$ 拆成兩個互斥部分：

$$
B=A\cup (B-A)
$$

由有限可加性可知

$$
\mathbb{P}(B)=\mathbb{P}(A)+\mathbb{P}(B-A)
$$

故可得到差集公式。再由非負性可知 $\mathbb{P}(B-A)\geq 0$，因此 $\mathbb{P}(A)\leq\mathbb{P}(B)$，也就是機率的單調性。 $\square$
</div>

單調性的使用有一個重要前提：兩個事件必須能比較大小，也就是其中一個事件包含於另一個事件。若 $A$ 與 $B$ 沒有包含關係，單調性本身並不能直接比較它們各自的機率。

## 加法原理：扣除重複的部分

對兩個事件而言，最常用的運算是聯集。若我們想計算 $A\cup B$ 的機率，直覺上會把 $\mathbb{P}(A)$ 與 $\mathbb{P}(B)$ 相加；但若 $A$ 與 $B$ 有重疊，交集 $A\cap B$ 就會被加到兩次，因此需要扣回一次。

<div class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Theorem 1.5</div>

若 $A,B\in\mathcal{F}$，則

$$
\mathbb{P}(A\cup B)
=\mathbb{P}(A)+\mathbb{P}(B)-\mathbb{P}(A\cap B)
$$

此公式稱為**加法原理 (addition rule)**。
</div>

<figure class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/probability-rules-addition-rule.svg" alt="加法原理的集合示意圖：A union B 的機率等於 A 的機率加 B 的機率，再扣掉 A intersection B。">
  <figcaption><span class="topic-figure__label">Fig. 1.3.</span> 加法原理的核心是先相加，再扣除被重複計算的交集。</figcaption>
</figure>

<div class="topic-proof" markdown="1">
**Proof.** 將 $A\cup B$ 拆成三個兩兩互斥的部分：

$$
A\cup B=(A\cap B^{\prime})\cup(A\cap B)\cup(A^{\prime}\cap B)
$$

由有限可加性可得

$$
\mathbb{P}(A\cup B)
=\mathbb{P}(A\cap B^{\prime})+\mathbb{P}(A\cap B)+\mathbb{P}(A^{\prime}\cap B)
$$

另一方面，將 $A$ 與 $B$ 分別拆開可得

$$
\mathbb{P}(A)=\mathbb{P}(A\cap B^{\prime})+\mathbb{P}(A\cap B)
$$

同理可得

$$
\mathbb{P}(B)=\mathbb{P}(A^{\prime}\cap B)+\mathbb{P}(A\cap B)
$$

兩式相加後，交集 $\mathbb{P}(A\cap B)$ 被算了兩次，因此扣掉一次即可得到加法原理。 $\square$
</div>

若 $A$ 與 $B$ 互斥，則 $A\cap B=\varnothing$，所以加法原理退化為

$$
\mathbb{P}(A\cup B)=\mathbb{P}(A)+\mathbb{P}(B)
$$

這正是有限可加性在兩個事件上的情形。

<div class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.7</div>

從一副標準撲克牌中隨機抽一張牌。令 $A$ 表示抽到紅心，$B$ 表示抽到 King。則

$$
\mathbb{P}(A)=\frac{13}{52}, \qquad
\mathbb{P}(B)=\frac{4}{52}, \qquad
\mathbb{P}(A\cap B)=\frac{1}{52}
$$

因此抽到「紅心或 King」的機率為

$$
\mathbb{P}(A\cup B)
=\frac{13}{52}+\frac{4}{52}-\frac{1}{52}
=\frac{16}{52}
=\frac{4}{13}
$$

這裡的 $1/52$ 是紅心 King 被重複計算的部分。
</div>

## 三個事件與排容原理

加法原理可以推廣到三個以上的事件。以三個事件為例，先加上三個單一事件的機率，再扣掉兩兩交集，最後要把三者共同交集加回來：

$$
\begin{aligned}
\mathbb{P}(A\cup B\cup C)
&=\mathbb{P}(A)+\mathbb{P}(B)+\mathbb{P}(C)\\[0.6em]
&\quad-\mathbb{P}(A\cap B)-\mathbb{P}(A\cap C)-\mathbb{P}(B\cap C)\\[0.6em]
&\quad+\mathbb{P}(A\cap B\cap C)
\end{aligned}
$$

<figure class="topic-figure topic-figure--medium">
  <img src="/images/teaching-topics/probability-rules-inclusion-exclusion-three.svg" alt="三事件排容原理的集合示意圖：三個事件互相重疊時，中央共同交集會被多次計算。">
  <figcaption><span class="topic-figure__label">Fig. 1.4.</span> 三事件排容中，兩兩交集先被扣除，而三者共同交集需要再加回來。</figcaption>
</figure>

這個精神稱為**排容原理 (inclusion-exclusion principle)**：先把可能發生的部分都加進來，再逐步修正被重複計算的重疊部分。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

排容原理與排列組合中的排容原理是同一個想法，只是這裡計算的是機率而不是元素個數。若在有限均等可能的古典機率模型中，把兩邊同乘以 $\mathrm{n}(S)$，就會回到集合個數版本的排容原理。
</div>

## 常用不等式：Boole 與 Bonferroni

若交集機率不容易取得，加法原理未必能直接給出精確值。不過它仍然能推出有用的界限。

<div class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Theorem 1.6</div>

若 $A_1,\ldots,A_n\in\mathcal{F}$，則

$$
\mathbb{P}\left(\bigcup_{i=1}^{n}A_i\right)
\leq \sum_{i=1}^{n}\mathbb{P}(A_i)
$$

此不等式稱為**布爾不等式 (Boole's inequality)**。此外，還有下列常用形式，與原形式等價

$$
\mathbb{P}\left(\bigcap_{i=1}^{n}A_i\right)
\geq 1-\sum_{i=1}^{n}\mathbb{P}(A_i^{\prime})
$$

此為**邦佛洛尼不等式 (Bonferroni's inequality)** 的常用形式。
</div>

<figure class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/probability-rules-boole-bound.svg" alt="布爾不等式的集合示意圖：A union B 的機率不超過 A 的機率加 B 的機率。">
  <figcaption><span class="topic-figure__label">Fig. 1.5.</span> 以兩事件為例，右側未扣除重疊部分，因此是上界而非精確值。</figcaption>
</figure>

布爾不等式的直覺是：如果直接把所有 $\mathbb{P}(A_i)$ 相加，重疊部分沒有被扣掉，所以右邊通常會偏大。邦佛洛尼不等式則可看成從餘事件觀點得到的下界：若每個 $A_i$ 失敗的機率都不大，那麼全部 $A_i$ 同時成立的機率就不會太小。

## 本篇小結

本文把 Kolmogorov 公理推出的基本運算整理成一條線：

| 工具 | 公式 | 核心想法 |
| --- | --- | --- |
| 虛無事件 | $\mathbb{P}(\varnothing)=0$ | 不可能事件的機率為 $0$ |
| 有限可加性 | $\mathbb{P}(\bigcup_i A_i)=\sum_i\mathbb{P}(A_i)$ | 互斥事件可以直接相加 |
| 餘事件公式 | $\mathbb{P}(A^{\prime})=1-\mathbb{P}(A)$ | 全部扣掉 $A$ |
| 單調性 | $A\subset B\Rightarrow \mathbb{P}(A)\leq\mathbb{P}(B)$ | 較小的事件，機率不會較大 |
| 加法原理 | $\mathbb{P}(A\cup B)=\mathbb{P}(A)+\mathbb{P}(B)-\mathbb{P}(A\cap B)$ | 扣除重複 |
| 排容原理 | 加、扣、再加回 | 修正多重重疊 |

這些工具仍然是在同一個機率空間中運作。下一步，我們將開始討論「資訊進來以後」機率如何改變，也就是條件機率與乘法原理。
