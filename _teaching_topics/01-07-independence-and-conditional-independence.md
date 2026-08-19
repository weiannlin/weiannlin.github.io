---
title: "獨立性與條件獨立"
subtitle: "Independence and Conditional Independence"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 1
topic: 7
order: 107
permalink: /teaching-topics/independence-and-conditional-independence/
date: 2026-05-17
published: true
excerpt: "獨立性描述資訊進來後機率仍然不變的情形。本篇依序介紹獨立事件、互斥與獨立的關係、列聯表、完全獨立與成對獨立，以及可靠度的串聯與並聯系統，最後補充條件獨立。"
---

[上一篇](/teaching-topics/conditional-probability-information/)的結尾提到，資訊的流入對某件事情發生的機率，影響可能為正、也可能為負；而比較特別的情況，是某一事件的資訊流入對另一事件毫無影響，這種狀況便是兩事件彼此獨立。本篇就從這個概念的正式定義說起。

## 獨立事件

<div id="definition-117" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.20</div>

令 $(S,\mathcal{F},\mathbb{P})$ 為一機率空間，$A,B\in\mathcal{F}$。**$A$ 與 $B$ 獨立 <span lang="en">(independent)</span>**，記為 $A\indep B$，與以下條件等價:

(1) 在 $\mathbb{P}(A)>0$ 之下，皆有
{: .topic-paren-item}

$$
\mathbb{P}(B\mid A)=\mathbb{P}(B)
$$

(2) 在 $\mathbb{P}(B)>0$ 之下，皆有
{: .topic-paren-item}

$$
\mathbb{P}(A\mid B)=\mathbb{P}(A)
$$

(3) 皆有
{: .topic-paren-item}

$$
\mathbb{P}(A\cap B)=\mathbb{P}(A)\,\mathbb{P}(B)
$$

</div>

上述的條件其實都是在說，給定發生 $A$ (或 $B$) 的條件之下，發生 $B$ (或 $A$) 的條件機率，與沒有給定此條件時相同；換言之，即**發生 $A$ <span class="text-nowrap">(或 $B$)</span> 並不影響 $B$ <span class="text-nowrap">(或 $A$)</span> 發生的機率**，這個概念即為二者**獨立**。

由[條件機率的定義](/teaching-topics/conditional-probability-information/#definition-conditional-probability)及[乘法原理](/teaching-topics/conditional-probability-information/#theorem-18)可知，若 (1) 或 (2) 成立，我們當然能夠順勢得到 (3)。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

事實上，我們後續在判斷兩事件是否為**獨立事件 <span lang="en">(independent events)</span>** 時，較常使用的等價定義為 (3)，因為 (1) 與 (2) 要求 $\mathbb{P}(A)>0$ 或 $\mathbb{P}(B)>0$ (為了使條件機率 $\mathbb{P}(B\mid A)$ 或 $\mathbb{P}(A\mid B)$ 有定義)，而 (3) 則完全避免了條件機率的出現，故即使 $\mathbb{P}(A)=\mathbb{P}(B)=0$，我們仍然可以用其作為判斷是否獨立的依據。
</div>

<div id="example-computer-ownership" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.18 <span lang="en">(Computer Ownership)</span></div>

<div lang="en" markdown="1">
In a survey on computer ownership, $73.4\%$ of the respondents said they own a PC, $21.8\%$ said they own both a PC and a Mac, and $80.1\%$ said they own at least one of the two. Let $P$ be the event that a randomly chosen respondent owns a PC, and let $M$ be the event that the respondent owns a Mac.

(1) What is the probability that a respondent owns a Mac?
{: .topic-paren-item}

(2) Are $P$ and $M$ mutually exclusive? Justify your answer with probabilities.
{: .topic-paren-item}

(3) Given that a respondent owns a PC, what is the conditional probability that the respondent also owns a Mac?
{: .topic-paren-item}

(4) Are $P$ and $M$ independent? Justify your answer with probabilities.
{: .topic-paren-item}
</div>

以下依序求解。

**(1)** 依題意知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(P)=0.734,\qquad \mathbb{P}(P\cap M)=0.218,\qquad \mathbb{P}(P\cup M)=0.801
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(P)&=0.734,\\[0.4em]
\mathbb{P}(P\cap M)&=0.218,\\[0.4em]
\mathbb{P}(P\cup M)&=0.801
\end{aligned}
$$

</div>

則由[加法原理](/teaching-topics/probability-rules-from-axioms/#theorem-total-and-addition)可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(P\cup M)=\mathbb{P}(P)+\mathbb{P}(M)-\mathbb{P}(P\cap M)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(P\cup M)&=\mathbb{P}(P)+\mathbb{P}(M)\\[0.4em]
&\qquad-\mathbb{P}(P\cap M)
\end{aligned}
$$

</div>

移項可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(M)&=\mathbb{P}(P\cup M)+\mathbb{P}(P\cap M)-\mathbb{P}(P)\\[0.4em]
&=0.801+0.218-0.734=0.285
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(M)&=\mathbb{P}(P\cup M)+\mathbb{P}(P\cap M)\\[0.4em]
&\qquad-\mathbb{P}(P)\\[0.4em]
&=0.801+0.218-0.734\\[0.4em]
&=0.285
\end{aligned}
$$

</div>

**(2)** 由 $\mathbb{P}(P\cap M)=0.218\neq 0$ 可知 $P\cap M\neq\varnothing$，故 $P$ 與 $M$ 不為互斥事件。

**(3)** 所求為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(M\mid P)=\frac{\mathbb{P}(P\cap M)}{\mathbb{P}(P)}=\frac{0.218}{0.734}\fallingdotseq 0.2970
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(M\mid P)&=\frac{\mathbb{P}(P\cap M)}{\mathbb{P}(P)}\\[0.4em]
&=\frac{0.218}{0.734}\fallingdotseq 0.2970
\end{aligned}
$$

</div>

**(4)** 由 (1) 已知 $\mathbb{P}(M)=0.285$，故

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(P\cap M)=0.218\neq\mathbb{P}(P)\,\mathbb{P}(M)=0.734\times 0.285\fallingdotseq 0.2092
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(P\cap M)=0.218\\[0.4em]
\neq\;&\mathbb{P}(P)\,\mathbb{P}(M)=0.734\times 0.285\fallingdotseq 0.2092
\end{aligned}
$$

</div>

故 $P$ 與 $M$ 不獨立。
</div>

<div id="example-independence-true-false" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.19 (True or False)</div>

令 $\mathbb{P}(A)=0.2$、$\mathbb{P}(B)=0.5$、$\mathbb{P}(A\cup B)=0.5$，則以下敘述何者為真？

<div class="topic-grid-options" markdown="1">
(1) $A\indep B$。

(2) $A$ 與 $B$ 互斥。

(3) $A\indep S$。

(4) $B\indep\varnothing$。

(5) $B$ 與 $S$ 互斥。

(6) $S\indep\varnothing$。
</div>

以下依序求解。

**(1)** 由[加法原理](/teaching-topics/probability-rules-from-axioms/#theorem-total-and-addition)可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(A\cap B)=\mathbb{P}(A)+\mathbb{P}(B)-\mathbb{P}(A\cup B)=0.2+0.5-0.5=0.2
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(A\cap B)&=\mathbb{P}(A)+\mathbb{P}(B)-\mathbb{P}(A\cup B)\\[0.4em]
&=0.2+0.5-0.5=0.2
\end{aligned}
$$

</div>

且 $\mathbb{P}(A)\,\mathbb{P}(B)=0.1$，故 $\mathbb{P}(A\cap B)\neq\mathbb{P}(A)\,\mathbb{P}(B)$，$A$ 與 $B$ 不獨立，此敘述為假。

**(2)** 由 $\mathbb{P}(A\cap B)=0.2\neq 0$ 可知 $A\cap B\neq\varnothing$，故 $A$ 與 $B$ 不互斥，此敘述為假。

**(3)** 由

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(A\cap S)=\mathbb{P}(A)=\mathbb{P}(A)\times 1=\mathbb{P}(A)\,\mathbb{P}(S)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(A\cap S)&=\mathbb{P}(A)=\mathbb{P}(A)\times 1\\[0.4em]
&=\mathbb{P}(A)\,\mathbb{P}(S)
\end{aligned}
$$

</div>

可知 $A$ 與 $S$ 獨立，此敘述為真。

**(4)** 由

$$
\mathbb{P}(B\cap\varnothing)=\mathbb{P}(\varnothing)=0=\mathbb{P}(B)\,\mathbb{P}(\varnothing)
$$

可知 $B$ 與 $\varnothing$ 獨立，此敘述為真。

**(5)** 由 $B\cap S=B\neq\varnothing$ 可知 $B$ 與 $S$ 不互斥，此敘述為假。

**(6)** 由

$$
\mathbb{P}(S\cap\varnothing)=\mathbb{P}(\varnothing)=0=\mathbb{P}(S)\,\mathbb{P}(\varnothing)
$$

可知 $S$ 與 $\varnothing$ 獨立，此敘述為真。
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

在 [Example 1.19](#example-independence-true-false) 中我們可以發現，**任何樣本空間的兩個顯然事件 $S$ 與 $\varnothing$ 都與所有事件獨立**，這件事情的原因並不難想像，因為 $S$ 和 $\varnothing$ 這兩個事件不能給我們帶來任何資訊，所以當然與任何事件都獨立。
</div>

## 互斥與獨立

我們在稍早[介紹互斥](/teaching-topics/event-set-operations/#definition-disjoint-events)時曾經提過，獨立與互斥實為兩個不同的定義，因為獨立需要使用機率，而互斥僅是就集合的角度在探討兩者的關係。

事實上，大部分的時候，互斥的事件都不獨立，其直觀意義亦很容易理解，因為兩事件若互斥，則可將其視為**必定不會同時發生**，這在機率上應該是一個很強的互相影響關係。

但是，並不是任何時候，彼此互斥的事件，都不可能互相獨立。我們在此整理互斥與獨立的關係，及其對應的情況如下:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

| 情況 | $A\cap B=\varnothing$，即 $\mathbb{P}(A\cap B)=0$ | $A\cap B\neq\varnothing$，即 $\mathbb{P}(A\cap B)\geqslant 0$ |
| :---: | :---: | :---: |
| $\mathbb{P}(A)>0$ 且 $\mathbb{P}(B)>0$ | $A$ 與 $B$ 不獨立 | 若 $\mathbb{P}(A\cap B)=\mathbb{P}(A)\,\mathbb{P}(B)$<br>則獨立，否則不獨立 |
| $\mathbb{P}(A)=0$ 或 $\mathbb{P}(B)=0$ | $A$ 與 $B$ 獨立 | $A$ 與 $B$ 獨立<br>(因為 $\mathbb{P}(A\cap B)=0$) |
{: .topic-table--matrix}

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

- **當 $\mathbb{P}(A)>0$ 且 $\mathbb{P}(B)>0$**:<br>若 $A\cap B=\varnothing$，則 $A$ 與 $B$ 不獨立；若 $A\cap B\neq\varnothing$，則視 $\mathbb{P}(A\cap B)=\mathbb{P}(A)\,\mathbb{P}(B)$ 是否成立，判斷獨立與否。
- **當 $\mathbb{P}(A)=0$ 或 $\mathbb{P}(B)=0$**:<br>無論兩事件是否互斥，$A$ 與 $B$ 皆獨立，因為此時必有 $\mathbb{P}(A\cap B)=0$。

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

此表格出自 Mittelhammer (1996) 頁 31，完整書目見文末參考文獻。
</div>

<div id="example-independent-vs-exclusive" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.20 <span lang="en">(Independence versus Exclusiveness)</span></div>

<div lang="en" markdown="1">
Prove the following two statements, assuming that every conditioning event has positive probability.

(1) If $\mathbb{P}(B)=1$, then $\mathbb{P}(A\mid B)=\mathbb{P}(A)$ for every event $A$.
{: .topic-paren-item}

(2) Suppose that $\mathbb{P}(A)>0$ and $\mathbb{P}(B)>0$. If $A$ and $B$ are independent, then they cannot be mutually exclusive. Conversely, if they are mutually exclusive, then they cannot be independent.
{: .topic-paren-item}
</div>

以下依序求解。

**(1)** 由[全機率定理](/teaching-topics/probability-rules-from-axioms/#theorem-total-and-addition)可知

$$
\mathbb{P}(A\cap B)=\mathbb{P}(A)-\mathbb{P}(A\cap B^{\prime})
$$

且由於 $\mathbb{P}(B)=1$，故知 $\mathbb{P}(B^{\prime})=1-\mathbb{P}(B)=0$。由[單調性](/teaching-topics/probability-rules-from-axioms/#theorem-monotonicity)可知

$$
\mathbb{P}(A\cap B^{\prime})\leqslant\mathbb{P}(B^{\prime})=0
$$

故知 $\mathbb{P}(A\cap B^{\prime})=0$，因此

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(A\cap B)=\mathbb{P}(A)-\mathbb{P}(A\cap B^{\prime})=\mathbb{P}(A)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(A\cap B)&=\mathbb{P}(A)-\mathbb{P}(A\cap B^{\prime})\\[0.4em]
&=\mathbb{P}(A)
\end{aligned}
$$

</div>

又由[條件機率之定義](/teaching-topics/conditional-probability-information/#definition-conditional-probability)可知，對所有 $A\in\mathcal{F}$ 皆有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(A\mid B)=\frac{\mathbb{P}(A\cap B)}{\mathbb{P}(B)}=\frac{\mathbb{P}(A)}{1}=\mathbb{P}(A)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(A\mid B)&=\frac{\mathbb{P}(A\cap B)}{\mathbb{P}(B)}\\[0.4em]
&=\frac{\mathbb{P}(A)}{1}=\mathbb{P}(A)
\end{aligned}
$$

</div>

**(2)** 由 $\mathbb{P}(A)>0$ 及 $\mathbb{P}(B)>0$，分兩個方向證明。

若 $A$ 與 $B$ 獨立，則可知

$$
\mathbb{P}(A\cap B)=\mathbb{P}(A)\,\mathbb{P}(B)>0
$$

故 $A\cap B\neq\varnothing$，即 $A$ 與 $B$ 不互斥。

若 $A\cap B=\varnothing$，則可知

$$
\mathbb{P}(A\cap B)=0\neq\mathbb{P}(A)\,\mathbb{P}(B)>0
$$

故 $A$ 與 $B$ 不獨立。
</div>

<div id="example-fungus-beetles" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.21 <span lang="en">(Fungus Beetles)</span></div>

<div lang="en" markdown="1">
On a field trip to Guatemala, you study a population of handsome fungus beetles. Females make up $70\%$ of the population and males $30\%$. The population also has two color morphs, with $60\%$ of the beetles dull brown and $40\%$ bronze. Half of all the beetles are dull brown females. Is the event that a beetle is male independent of the event that a beetle is dull brown?
</div>

令 $A$ 表其顏色為 dull brown 之事件，$M$ 表其性別為 male 之事件，由題目敘述可以列出以下之機率列聯表:

| | $A$ | $A^{\prime}$ | 總和 |
| :---: | :---: | :---: | :---: |
| $M$ | $0.1$ | $0.2$ | $0.3$ |
| $M^{\prime}$ | $0.5$ | $0.2$ | $0.7$ |
| 總和 | $0.6$ | $0.4$ | $1$ |
{: .topic-table--joint-pmf}

因此

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(A\cap M)=0.1\neq\mathbb{P}(A)\,\mathbb{P}(M)=0.6\times 0.3=0.18
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(A\cap M)=0.1\\[0.4em]
\neq\;&\mathbb{P}(A)\,\mathbb{P}(M)=0.6\times 0.3=0.18
\end{aligned}
$$

</div>

故 $A$ 與 $M$ 不獨立，其顏色為 dull brown 與其性別為 male 此二事件不獨立。
</div>

[Example 1.21](#example-fungus-beetles) 中，我們將昆蟲群體依照其**顏色**與**性別**兩組互斥且合起來涵蓋整個母體的分類方式 (即稍後將正式介紹的**分割 <span lang="en">(partition)</span>**) 進行分類，並列成表格，這種表格稱為**列聯表 <span lang="en">(contingency table)</span>**。其型態如下表:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

| | $A_1$ | $A_2$ | $A_3$ | 總和 |
| :---: | :---: | :---: | :---: | :---: |
| $B_1$ | $\mathbb{P}(A_1\cap B_1)$ | $\mathbb{P}(A_2\cap B_1)$ | $\mathbb{P}(A_3\cap B_1)$ | $\mathbb{P}(B_1)$ |
| $B_2$ | $\mathbb{P}(A_1\cap B_2)$ | $\mathbb{P}(A_2\cap B_2)$ | $\mathbb{P}(A_3\cap B_2)$ | $\mathbb{P}(B_2)$ |
| $B_3$ | $\mathbb{P}(A_1\cap B_3)$ | $\mathbb{P}(A_2\cap B_3)$ | $\mathbb{P}(A_3\cap B_3)$ | $\mathbb{P}(B_3)$ |
| 總和 | $\mathbb{P}(A_1)$ | $\mathbb{P}(A_2)$ | $\mathbb{P}(A_3)$ | $1$ |
{: .topic-table--joint-pmf}

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

| | $A_1$ | $A_2$ | 總和 |
| :---: | :---: | :---: | :---: |
| $B_1$ | $\mathbb{P}(A_1\cap B_1)$ | $\mathbb{P}(A_2\cap B_1)$ | $\mathbb{P}(B_1)$ |
| $B_2$ | $\mathbb{P}(A_1\cap B_2)$ | $\mathbb{P}(A_2\cap B_2)$ | $\mathbb{P}(B_2)$ |
| 總和 | $\mathbb{P}(A_1)$ | $\mathbb{P}(A_2)$ | $1$ |
{: .topic-table--joint-pmf}

</div>

在上述表格中，表內的機率如 $\mathbb{P}(A_1\cap B_1)$ 等，稱作**聯合機率 <span lang="en">(joint probability)</span>**，而表邊的機率如 $\mathbb{P}(A_1)$ 等，稱作**邊際機率 <span lang="en">(marginal probability)</span>**，這二者的概念與分割及全機率定理具有非常高度的相關，我們將在[下一篇](/teaching-topics/total-probability-bayes-rule/)與後續章節詳細介紹。

## 獨立事件的餘事件

<div id="theorem-independence-complements" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 1.15 <span lang="en">(Independence and Complements)</span></div>

令 $(S,\mathcal{F},\mathbb{P})$ 為一機率空間，$A,B\in\mathcal{F}$，且 $A\indep B$，則以下敘述亦成立:

<div class="topic-grid-options topic-grid-options--equal" markdown="1">
(1) $A\indep B^{\prime}$

(2) $A^{\prime}\indep B$

(3) $A^{\prime}\indep B^{\prime}$
</div>
</div>

<div class="topic-proof" markdown="1">
**Proof.**

**(1)** 由 $A\indep B$ 可知 $\mathbb{P}(A\cap B)=\mathbb{P}(A)\,\mathbb{P}(B)$ 成立。

又由[全機率定理](/teaching-topics/probability-rules-from-axioms/#theorem-total-and-addition)可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(A\cap B^{\prime})&=\mathbb{P}(A)-\mathbb{P}(A\cap B)\\[0.4em]
&=\mathbb{P}(A)-\mathbb{P}(A)\,\mathbb{P}(B)=\mathbb{P}(A)\big(1-\mathbb{P}(B)\big)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(A\cap B^{\prime})&=\mathbb{P}(A)-\mathbb{P}(A\cap B)\\[0.4em]
&=\mathbb{P}(A)-\mathbb{P}(A)\,\mathbb{P}(B)\\[0.4em]
&=\mathbb{P}(A)\big(1-\mathbb{P}(B)\big)
\end{aligned}
$$

</div>

且由 $\mathbb{P}(B^{\prime})=1-\mathbb{P}(B)$ 知 $\mathbb{P}(A\cap B^{\prime})=\mathbb{P}(A)\,\mathbb{P}(B^{\prime})$，故 $A\indep B^{\prime}$。

**(2)** 由 $A\indep B$ 可知 $\mathbb{P}(A\cap B)=\mathbb{P}(A)\,\mathbb{P}(B)$ 成立。

又由全機率定理可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(A^{\prime}\cap B)&=\mathbb{P}(B)-\mathbb{P}(A\cap B)\\[0.4em]
&=\mathbb{P}(B)-\mathbb{P}(A)\,\mathbb{P}(B)=\mathbb{P}(B)\big(1-\mathbb{P}(A)\big)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(A^{\prime}\cap B)&=\mathbb{P}(B)-\mathbb{P}(A\cap B)\\[0.4em]
&=\mathbb{P}(B)-\mathbb{P}(A)\,\mathbb{P}(B)\\[0.4em]
&=\mathbb{P}(B)\big(1-\mathbb{P}(A)\big)
\end{aligned}
$$

</div>

且由 $\mathbb{P}(A^{\prime})=1-\mathbb{P}(A)$ 知 $\mathbb{P}(A^{\prime}\cap B)=\mathbb{P}(A^{\prime})\,\mathbb{P}(B)$，故 $A^{\prime}\indep B$。

**(3)** 由 $A\indep B$ 可知 $\mathbb{P}(A\cap B)=\mathbb{P}(A)\,\mathbb{P}(B)$ 成立。

又由[狄摩根律](/teaching-topics/event-set-operations/#theorem-de-morgan)與餘事件公式可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(A^{\prime}\cap B^{\prime})&=1-\mathbb{P}(A\cup B)=1-\big[\mathbb{P}(A)+\mathbb{P}(B)-\mathbb{P}(A\cap B)\big]\\[0.4em]
&=1-\mathbb{P}(A)-\mathbb{P}(B)+\mathbb{P}(A)\,\mathbb{P}(B)\\[0.4em]
&=\big[1-\mathbb{P}(A)\big]\big[1-\mathbb{P}(B)\big]=\mathbb{P}(A^{\prime})\,\mathbb{P}(B^{\prime})
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(A^{\prime}\cap B^{\prime})&=1-\mathbb{P}(A\cup B)\\[0.4em]
&=1-\big[\mathbb{P}(A)+\mathbb{P}(B)-\mathbb{P}(A\cap B)\big]\\[0.4em]
&=1-\mathbb{P}(A)-\mathbb{P}(B)+\mathbb{P}(A)\,\mathbb{P}(B)\\[0.4em]
&=\big[1-\mathbb{P}(A)\big]\big[1-\mathbb{P}(B)\big]\\[0.4em]
&=\mathbb{P}(A^{\prime})\,\mathbb{P}(B^{\prime})
\end{aligned}
$$

</div>

故 $A^{\prime}\indep B^{\prime}$。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個定理指出，如果某事件發生與否，並不能給另一事件帶來任何資訊，那這件事「是否**不發生**」，也同樣不能帶給另一事件任何資訊，因為知道某件事情「發生」或「不發生」，此二敘述的資訊其實是等價的。
</div>

## 完全獨立與成對獨立

<div id="definition-118" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.21</div>

令 $(S,\mathcal{F},\mathbb{P})$ 為一機率空間。若 $A,B,C\in\mathcal{F}$ 滿足以下條件，則稱 **$A,B,C$ 完全獨立 <span lang="en">(mutually independent)</span>**:

(1) 三事件兩兩獨立，即
{: .topic-paren-item}

$$
\begin{gathered}
\mathbb{P}(A\cap B)=\mathbb{P}(A)\,\mathbb{P}(B)\\[0.4em]
\mathbb{P}(B\cap C)=\mathbb{P}(B)\,\mathbb{P}(C)\\[0.4em]
\mathbb{P}(A\cap C)=\mathbb{P}(A)\,\mathbb{P}(C)
\end{gathered}
$$

(2) 交集機率等於各自機率相乘，即
{: .topic-paren-item}

$$
\mathbb{P}(A\cap B\cap C)=\mathbb{P}(A)\,\mathbb{P}(B)\,\mathbb{P}(C)
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

**完全獨立 <span lang="en">(mutually independent)</span>** 除了單純將「交集的機率等於各自機率相乘」推廣至三個事件的版本外，還多了「兩兩事件彼此也要獨立」的條件。若僅滿足 (1) 而沒有滿足 (2) 的話，我們稱之為**成對獨立 <span lang="en">(pairwise independent)</span>**。

事實上，這個定義若要推廣到任意 $n$ 個事件的話，需要在這 $n$ 個事件中任意取 $k$ 個事件 (其中 $k=2,3,\ldots,n$)，彼此都滿足「交集機率等於各自機率相乘」。若以四個事件而言，則其中任意兩個、三個事件及全部四個事件都要滿足這個條件。
</div>

事實上，讀者應該記得，獨立的定義原先是由「條件機率等於邊際機率」而來，說明了事件之間，並沒有互相影響的關係。在三個或以上的事件時，這個概念仍然適用，而且相當直觀。讀者可見以下的等價定義:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\left\{
\begin{array}{l}
\mathbb{P}(A\mid B,C)=\mathbb{P}(A\mid B)=\mathbb{P}(A\mid C)=\mathbb{P}(A)\\[0.4em]
\mathbb{P}(B\mid A,C)=\mathbb{P}(B\mid A)=\mathbb{P}(B\mid C)=\mathbb{P}(B)\\[0.4em]
\mathbb{P}(C\mid A,B)=\mathbb{P}(C\mid A)=\mathbb{P}(C\mid B)=\mathbb{P}(C)
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(A\mid B,C)&=\mathbb{P}(A\mid B)\\[0.4em]
&=\mathbb{P}(A\mid C)=\mathbb{P}(A)\\[0.4em]
\mathbb{P}(B\mid A,C)&=\mathbb{P}(B\mid A)\\[0.4em]
&=\mathbb{P}(B\mid C)=\mathbb{P}(B)\\[0.4em]
\mathbb{P}(C\mid A,B)&=\mathbb{P}(C\mid A)\\[0.4em]
&=\mathbb{P}(C\mid B)=\mathbb{P}(C)
\end{aligned}
$$

</div>

其中

$$
\begin{gathered}
\mathbb{P}(A\mid B,C)=\mathbb{P}(A\mid B\cap C)\\[0.4em]
\mathbb{P}(B\mid A,C)=\mathbb{P}(B\mid A\cap C)\\[0.4em]
\mathbb{P}(C\mid A,B)=\mathbb{P}(C\mid A\cap B)
\end{gathered}
$$

且 $\mathbb{P}(A)$、$\mathbb{P}(B)$、$\mathbb{P}(C)$、$\mathbb{P}(A\cap B)$、$\mathbb{P}(A\cap C)$、$\mathbb{P}(B\cap C)$ 皆大於 $0$。

上式與 [Definition 1.21](#definition-118) 完全等價。但讀者要注意的是，若上式成立，將導致 [Definition 1.21](#definition-118) 中的 (1) 與 (2) 同時成立；反之，[Definition 1.21](#definition-118) 中的 (1) 與 (2) 必須同時成立，才能導致上式成立。

<div id="example-pairwise-not-mutual" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.22 <span lang="en">(Pairwise but Not Mutual)</span></div>

<div lang="en" markdown="1">
Four cards are labeled with the numbers $1$, $2$, $3$, and $123$, one number per card. One card is drawn at random, and for $i=1,2,3$ let $A_i$ be the event that the number on the drawn card contains the digit $i$. Show that the three events $A_1,A_2,A_3$ are pairwise independent but not mutually independent.
</div>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

依題意可知 $A_1=\lbrace 1,123\rbrace$、$A_2=\lbrace 2,123\rbrace$、$A_3=\lbrace 3,123\rbrace$，則

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

依題意可知

$$
\begin{aligned}
A_1&=\lbrace 1,123\rbrace\\[0.4em]
A_2&=\lbrace 2,123\rbrace\\[0.4em]
A_3&=\lbrace 3,123\rbrace
\end{aligned}
$$

則

</div>

$$
\mathbb{P}(A_1)=\mathbb{P}(A_2)=\mathbb{P}(A_3)=\frac{2}{4}=\frac{1}{2}
$$

又由

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
A_1\cap A_2=\lbrace 123\rbrace,\qquad\mathbb{P}(A_1\cap A_2)=\frac{1}{4}=\mathbb{P}(A_1)\,\mathbb{P}(A_2)\\[0.4em]
A_1\cap A_3=\lbrace 123\rbrace,\qquad\mathbb{P}(A_1\cap A_3)=\frac{1}{4}=\mathbb{P}(A_1)\,\mathbb{P}(A_3)\\[0.4em]
A_2\cap A_3=\lbrace 123\rbrace,\qquad\mathbb{P}(A_2\cap A_3)=\frac{1}{4}=\mathbb{P}(A_2)\,\mathbb{P}(A_3)
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
A_1\cap A_2&=\lbrace 123\rbrace\\[0.4em]
\Longrightarrow\mathbb{P}(A_1\cap A_2)&=\frac{1}{4}=\mathbb{P}(A_1)\,\mathbb{P}(A_2)\\[0.7em]
A_1\cap A_3&=\lbrace 123\rbrace\\[0.4em]
\Longrightarrow\mathbb{P}(A_1\cap A_3)&=\frac{1}{4}=\mathbb{P}(A_1)\,\mathbb{P}(A_3)\\[0.7em]
A_2\cap A_3&=\lbrace 123\rbrace\\[0.4em]
\Longrightarrow\mathbb{P}(A_2\cap A_3)&=\frac{1}{4}=\mathbb{P}(A_2)\,\mathbb{P}(A_3)
\end{aligned}
$$

</div>

可知 $A_1,A_2,A_3$ 為成對獨立事件，然而

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
A_1\cap A_2\cap A_3=\lbrace 123\rbrace\\[0.4em]
\mathbb{P}(A_1\cap A_2\cap A_3)=\frac{1}{4}\neq\mathbb{P}(A_1)\,\mathbb{P}(A_2)\,\mathbb{P}(A_3)=\frac{1}{8}
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
A_1\cap A_2\cap A_3&=\lbrace 123\rbrace\\[0.4em]
\Longrightarrow\mathbb{P}(A_1\cap A_2\cap A_3)&=\frac{1}{4}\\[0.4em]
\neq\mathbb{P}(A_1)\,\mathbb{P}(A_2)\,\mathbb{P}(A_3)&=\frac{1}{8}
\end{aligned}
$$

</div>

故知道 $A_1,A_2,A_3$ 為成對獨立事件但不為完全獨立之事件。
</div>

## 可靠度與串並聯系統

獨立的情況下可以很輕鬆地解決很多問題，例如眾多考試經常出現的「可靠度問題」。

正因為其容易操作的特性，現實世界中的複雜問題，往往會先簡化假設至彼此獨立的狀況，以便進行初步的分析，這也是獨立的觀念之所以重要的原因。

系統的**可靠度 <span lang="en">(reliability)</span>** 就其字面上的意思為**系統可靠的程度**，顧名思義是指系統「可以成功運作的機率」。所有的可靠度問題，都可以經由**子系統拆解**，簡化為最簡單的兩種系統: **串聯**與**並聯**。首先假設兩個獨立的元件，並且 $A$ 與 $B$ 分別是第一個與第二個元件能順利運作的事件，則我們分別探討下列兩種系統的可靠度。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

可靠度問題實際上是在計算系統壽命，故又稱為「系統壽命問題」。
</div>

**串聯系統**:

<figure class="topic-figure topic-figure--compact">
  <img src="/images/teaching-topics/independence-series-system.svg" alt="串聯系統示意圖。元件 1 與元件 2 沿同一條線路前後相接。">
  <figcaption><span class="topic-figure__label">Fig. 1.18.</span> 兩個元件的串聯系統。</figcaption>
</figure>

這種系統若要成功運作，表示兩個元件皆必須要可以運作，即 $A$ 事件與 $B$ 事件之交集，故整個系統的可靠度為

$$
\mathbb{P}(A\cap B)=\mathbb{P}(A)\,\mathbb{P}(B)
$$

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

若推廣至 $n$ 個元件的串聯系統，則可靠度為

$$
\mathbb{P}\left(\bigcap_{i=1}^{n}A_i\right)=\prod_{i=1}^{n}\mathbb{P}(A_i)
$$

</div>

**並聯系統**:

<figure class="topic-figure topic-figure--compact">
  <img src="/images/teaching-topics/independence-parallel-system.svg" alt="並聯系統示意圖。線路分成上下兩條支線，分別通過元件 1 與元件 2 後再會合。">
  <figcaption><span class="topic-figure__label">Fig. 1.19.</span> 兩個元件的並聯系統。</figcaption>
</figure>

這種系統若要成功運作，表示兩個元件有其一可以運作即可，即 $A$ 事件與 $B$ 事件之聯集，故整個系統的可靠度為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(A\cup B)=\mathbb{P}(A)+\mathbb{P}(B)-\mathbb{P}(A)\,\mathbb{P}(B)=1-\big(1-\mathbb{P}(A)\big)\big(1-\mathbb{P}(B)\big)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(A\cup B)&=\mathbb{P}(A)+\mathbb{P}(B)-\mathbb{P}(A)\,\mathbb{P}(B)\\[0.4em]
&=1-\big(1-\mathbb{P}(A)\big)\big(1-\mathbb{P}(B)\big)
\end{aligned}
$$

</div>

此可靠度亦即**全部機率扣掉兩個元件都不運作之機率**。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

若推廣至 $n$ 個元件的並聯系統，則可靠度為

$$
\mathbb{P}\left(\bigcup_{i=1}^{n}A_i\right)=1-\prod_{i=1}^{n}\big(1-\mathbb{P}(A_i)\big)
$$

</div>

<div id="example-three-component-reliability" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.23 <span lang="en">(A Three-Component System)</span></div>

<div lang="en" markdown="1">
A system consists of three components $1$, $2$, and $3$, arranged as in the figure below. Each component fails with probability $0.1$.
</div>

<figure class="topic-figure topic-figure--medium">
  <img src="/images/teaching-topics/independence-three-component-system.svg" alt="三元件系統示意圖。元件 1 位於上方支線，元件 2 與 3 串接於下方支線，兩條支線並聯。">
  <figcaption><span class="topic-figure__label">Fig. 1.20.</span> 元件 $2$ 與 $3$ 串聯後，再與元件 $1$ 並聯。</figcaption>
</figure>

<div lang="en" markdown="1">
(1) If the three components work independently, what is the probability that the system works?
{: .topic-paren-item}

(2) Suppose instead that component $1$ works independently of components $2$ and $3$, and that the conditional probability that component $2$ fails given that component $3$ fails is $0.4$, and vice versa. What is the probability that the system works?
{: .topic-paren-item}
</div>

以下依序求解。

**(1)** 令 $A_i$，$i=1,2,3$ 表示元件 $i$ 可以順利運作的事件。元件 $2$ 與 $3$ 可視為一簡單串聯子系統，由 $A_2\indep A_3$ 可知其順利運作之機率為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(A_2\cap A_3)=\mathbb{P}(A_2)\,\mathbb{P}(A_3)=0.9\times 0.9=0.81
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(A_2\cap A_3)&=\mathbb{P}(A_2)\,\mathbb{P}(A_3)\\[0.4em]
&=0.9\times 0.9=0.81
\end{aligned}
$$

</div>

又該子系統與元件 $1$ 並聯，故整個系統順利運作的機率為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}\big(A_1\cup(A_2\cap A_3)\big)&=1-\mathbb{P}(A_1^{\prime})\big(1-\mathbb{P}(A_2\cap A_3)\big)\\[0.4em]
&=1-0.1\times(1-0.81)=0.981
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}\big(A_1\cup(A_2\cap A_3)\big)&=1-\mathbb{P}(A_1^{\prime})\big(1-\mathbb{P}(A_2\cap A_3)\big)\\[0.4em]
&=1-0.1\times(1-0.81)=0.981
\end{aligned}
$$

</div>

**(2)** 由題目敘述可知 $\mathbb{P}(A_2^{\prime}\mid A_3^{\prime})=\mathbb{P}(A_3^{\prime}\mid A_2^{\prime})=0.4$，則由[乘法原理](/teaching-topics/conditional-probability-information/#theorem-18)可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(A_2^{\prime}\cap A_3^{\prime})=\mathbb{P}(A_2^{\prime}\mid A_3^{\prime})\,\mathbb{P}(A_3^{\prime})=0.4\times 0.1=0.04
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(A_2^{\prime}\cap A_3^{\prime})&=\mathbb{P}(A_2^{\prime}\mid A_3^{\prime})\,\mathbb{P}(A_3^{\prime})\\[0.4em]
&=0.4\times 0.1=0.04
\end{aligned}
$$

</div>

再由[狄摩根律](/teaching-topics/event-set-operations/#theorem-de-morgan)可知

$$
\mathbb{P}(A_2\cup A_3)=1-\mathbb{P}(A_2^{\prime}\cap A_3^{\prime})=0.96
$$

且由[加法原理](/teaching-topics/probability-rules-from-axioms/#theorem-total-and-addition)可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(A_2\cap A_3)&=\mathbb{P}(A_2)+\mathbb{P}(A_3)-\mathbb{P}(A_2\cup A_3)\\[0.4em]
&=0.9+0.9-0.96=0.84
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(A_2\cap A_3)&=\mathbb{P}(A_2)+\mathbb{P}(A_3)-\mathbb{P}(A_2\cup A_3)\\[0.4em]
&=0.9+0.9-0.96=0.84
\end{aligned}
$$

</div>

又元件 $1$ 與元件 $2$ 及元件 $3$ 皆獨立，故整個系統的可靠度為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}\big(A_1\cup(A_2\cap A_3)\big)&=1-\mathbb{P}(A_1^{\prime})\big(1-\mathbb{P}(A_2\cap A_3)\big)\\[0.4em]
&=1-0.1\times(1-0.84)=0.984
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}\big(A_1\cup(A_2\cap A_3)\big)&=1-\mathbb{P}(A_1^{\prime})\big(1-\mathbb{P}(A_2\cap A_3)\big)\\[0.4em]
&=1-0.1\times(1-0.84)=0.984
\end{aligned}
$$

</div>

</div>

<div id="example-power-transmission" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.24 <span lang="en">(A Power Transmission System)</span></div>

<div lang="en" markdown="1">
Consider the power transmission system composed of the components shown in the figure below, where the number in each block is the probability that the component operates. Find the probability that the whole system operates.
</div>

<figure class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/independence-power-grid-system.svg" alt="電力傳輸系統示意圖。0.8 元件先串聯，接著兩個 0.9 元件並聯，最後 0.9、0.7、0.8 三個元件並聯。">
  <figcaption><span class="topic-figure__label">Fig. 1.21.</span> 電力傳輸系統，方塊內的數字為各元件正常運作的機率。</figcaption>
</figure>

假設本題中，所有元件之可運作事件彼此獨立。由圖可知，題目為三個子系統的串聯，分別為

<figure class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/independence-power-grid-subsystems.svg" alt="三個子系統示意圖。第一個為單一 0.8 元件，第二個為兩個 0.9 元件並聯，第三個為 0.9、0.7、0.8 三個元件並聯。">
  <figcaption><span class="topic-figure__label">Fig. 1.22.</span> 依串並聯結構拆解出的三個子系統。</figcaption>
</figure>

此三個子系統可運作的事件分別令為 $E_1,E_2,E_3$，則可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\mathbb{P}(E_1)=0.8\\[0.4em]
\mathbb{P}(E_2)=1-(1-0.9)(1-0.9)=0.99\\[0.4em]
\mathbb{P}(E_3)=1-(1-0.9)(1-0.7)(1-0.8)=0.994
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(E_1)&=0.8\\[0.4em]
\mathbb{P}(E_2)&=1-(1-0.9)(1-0.9)\\[0.4em]
&=0.99\\[0.4em]
\mathbb{P}(E_3)&=1-(1-0.9)(1-0.7)\\[0.4em]
&\qquad(1-0.8)\\[0.4em]
&=0.994
\end{aligned}
$$

</div>

所求為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(E_1)\,\mathbb{P}(E_2)\,\mathbb{P}(E_3)=0.8\times 0.99\times 0.994\fallingdotseq 0.7872
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(E_1)\,\mathbb{P}(E_2)\,\mathbb{P}(E_3)&=0.8\times 0.99\times 0.994\\[0.4em]
&\fallingdotseq 0.7872
\end{aligned}
$$

</div>

</div>

## 條件獨立

在貝氏定理與分割模型中，我們常會先固定某個狀態，再討論事件之間是否獨立。這稱為條件獨立。

<div id="definition-conditional-independence" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.22</div>

令 $A,B,C\in\mathcal{F}$，且 $\mathbb{P}(C)>0$。若

$$
\mathbb{P}(A\cap B\mid C)
=\mathbb{P}(A\mid C)\,\mathbb{P}(B\mid C)
$$

則稱 $A$ 與 $B$ 在給定 $C$ 後**條件獨立 <span lang="en">(conditionally independent)</span>**。
</div>

條件獨立的重點在於先固定條件 $C$。固定在 $C$ 所代表的參照世界後，$A$ 的發生不再改變 $B$ 的機率，$B$ 的發生也不再改變 $A$ 的機率。

快篩檢測正是很好的例子。令 $D$ 表示真實罹病狀態，令 $T_1,T_2$ 表示兩次檢測都呈陽性的事件。若我們假設在真實狀態固定後，每次檢測誤差近似獨立，則有

$$
\mathbb{P}(T_1\cap T_2\mid D)
=\mathbb{P}(T_1\mid D)\,\mathbb{P}(T_2\mid D)
$$

也有

$$
\mathbb{P}(T_1\cap T_2\mid D^{\prime})
=\mathbb{P}(T_1\mid D^{\prime})\,\mathbb{P}(T_2\mid D^{\prime})
$$

但這不代表 $T_1$ 與 $T_2$ 在未給定真實狀態時獨立。第一次陽性會提高我們對罹病狀態的機率評估，而罹病狀態又會提高第二次陽性的機率。因此，未給定 $D$ 或 $D^{\prime}$ 時，兩次陽性結果通常會彼此相關。

<div class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 1.2</div>

若固定每一種條件狀態後，$A$ 與 $B$ 都條件獨立，能不能推出 $A$ 與 $B$ 本身獨立？答案是否定的。

令 $C_1$ 與 $C_2$ 互斥且 $C_1\cup C_2=S$，且

$$
\mathbb{P}(C_1)=\mathbb{P}(C_2)=\frac{1}{2}
$$

假設在 $C_1$ 下，$A$ 與 $B$ 各自發生的條件機率都是 $9/10$；在 $C_2$ 下，$A$ 與 $B$ 各自發生的條件機率都是 $1/10$。再假設在 $C_1$ 與 $C_2$ 下，$A$ 與 $B$ 都條件獨立。

於是由[全機率定理](/teaching-topics/probability-rules-from-axioms/#theorem-total-and-addition)可得

$$
\mathbb{P}(A)=\mathbb{P}(B)
=
\frac{1}{2}\cdot\frac{9}{10}
+
\frac{1}{2}\cdot\frac{1}{10}
=
\frac{1}{2}
$$

但若要計算 $A\cap B$ 的機率，同樣要先把它拆成兩塊。

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(A\cap B)
=
\mathbb{P}(A\cap B\cap C_1)
+
\mathbb{P}(A\cap B\cap C_2)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(A\cap B)&=\mathbb{P}(A\cap B\cap C_1)\\[0.4em]
&\qquad+\mathbb{P}(A\cap B\cap C_2)
\end{aligned}
$$

</div>

再由[乘法原理](/teaching-topics/conditional-probability-information/#theorem-18)與條件獨立性可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(A\cap B)
&=
\mathbb{P}(A\cap B\mid C_1)\,\mathbb{P}(C_1)
+
\mathbb{P}(A\cap B\mid C_2)\,\mathbb{P}(C_2) \\[0.4em]
&=
\mathbb{P}(A\mid C_1)\,\mathbb{P}(B\mid C_1)\,\mathbb{P}(C_1)
+
\mathbb{P}(A\mid C_2)\,\mathbb{P}(B\mid C_2)\,\mathbb{P}(C_2) \\[0.4em]
&=
\frac{1}{2}\left(\frac{9}{10}\right)^2
+
\frac{1}{2}\left(\frac{1}{10}\right)^2
=
\frac{41}{100}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(A\cap B)&=
\mathbb{P}(A\cap B\mid C_1)\,\mathbb{P}(C_1)\\[0.4em]
&\qquad+
\mathbb{P}(A\cap B\mid C_2)\,\mathbb{P}(C_2) \\[0.4em]
&=
\mathbb{P}(A\mid C_1)\,\mathbb{P}(B\mid C_1)\,\mathbb{P}(C_1)\\[0.4em]
&\qquad+
\mathbb{P}(A\mid C_2)\,\mathbb{P}(B\mid C_2)\,\mathbb{P}(C_2) \\[0.4em]
&=
\frac{1}{2}\left(\frac{9}{10}\right)^2
+
\frac{1}{2}\left(\frac{1}{10}\right)^2
=
\frac{41}{100}
\end{aligned}
$$

</div>

而

$$
\mathbb{P}(A)\,\mathbb{P}(B)=\frac{1}{4}
$$

因此 $A$ 與 $B$ 在每種條件狀態下都條件獨立，混合回整體後卻不獨立。原因是未給定條件狀態時，$A$ 的發生會改變我們對目前落在 $C_1$ 或 $C_2$ 的判斷；而 $B$ 的發生機率也會隨之改變。這種共同來源會在整體中留下關聯。
</div>

這個例子也提醒我們，條件獨立與整體獨立不能互相替代。條件資訊若沒有被明確放進模型，混合後的整體關係可能完全不同。

<!-- Future extension, hidden until a machine-learning or classification topic exists:
Naive Bayes 分類法常用條件獨立近似。給定類別 $C_k$ 後，若可把觀察變數 $x_1,\ldots,x_m$ 近似看成條件獨立，便能把許多條件機率相乘。References to preserve for that future extension:
- Christopher M. Bishop. 2006. Pattern Recognition and Machine Learning. Springer New York.
- Judea Pearl, Madelyn Glymour, and Nicholas P. Jewell. 2016. Causal Inference in Statistics: A Primer. Wiley.
-->

## 本篇小結

本篇由獨立的定義出發，依序整理下列結果:

| 結果 | 內容 |
| :---: | :---: |
| [Definition 1.20](#definition-117) | 獨立事件 (三個等價條件) |
| [Theorem 1.15](#theorem-independence-complements) | 獨立事件之餘事件仍獨立 |
| [Definition 1.21](#definition-118) | 完全獨立與成對獨立 |
| [可靠度](#可靠度與串並聯系統) | 串聯與並聯系統的成功機率 |
| [Definition 1.22](#definition-conditional-independence) | 條件獨立 |

接著若樣本空間被一組互斥且沒有遺漏的事件切開，便可把整體事件拆成幾個來源來加總。這會導向[分割與全機率定理](/teaching-topics/total-probability-bayes-rule/)。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Joseph K. Blitzstein and Jessica Hwang. 2019. *Introduction to Probability*. 2nd ed. Chapman and Hall/CRC.
- Morris H. DeGroot and Mark J. Schervish. 2012. *Probability and Statistics*. 4th ed. Pearson.
- Ron C. Mittelhammer. 1996. *Mathematical Statistics for Economics and Business*. Springer New York.
- A. Philip Dawid. 1979. “Conditional Independence in Statistical Theory.” *Journal of the Royal Statistical Society, Series B* 41 (1): 1–15.
