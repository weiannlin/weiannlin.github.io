---
title: "分割與全機率定理，從分類到加總"
subtitle: "Partitions and the Law of Total Probability"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 1
topic: 8
order: 108
permalink: /teaching-topics/total-probability-bayes-rule/
date: 2026-05-05
published: true
excerpt: "樣本空間的分割由一組互斥且周延的事件構成。本篇介紹分割的定義、全機率定理及其條件機率版本，並說明兩組分割彼此交集而成的二元分割與列聯表。"
---

[上一篇文章](/teaching-topics/independence-and-conditional-independence/)在介紹列聯表時曾經提到，表內的聯合機率與表邊的邊際機率，與分割及全機率定理有非常高度的相關。本篇便由樣本空間的分割談起，說明一個事件如何依一組分割被切成數個互斥的部分，再逐一加總回來。

## 樣本空間的分割

<div id="definition-partition" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.23</div>

令 $(S,\mathcal{F},\mathbb{P})$ 為一機率空間，$A_1,A_2,\ldots,A_n\in\mathcal{F}$，若其滿足以下條件，則稱 $A_1,A_2,\ldots,A_n$ 為 $S$ 的一組**分割 (partition)**:

(1) **互斥 (mutually exclusive)**:

$$
A_i\cap A_j=\varnothing,\ \forall i\neq j
$$

(2) **周延 (collectively exhaustive)**:

$$
\bigcup_{i=1}^{n}A_i=S
$$

</div>

分割的定義，即是把樣本空間「分割成數個不重複的事件」，故其應滿足兩兩**互斥**與彼此**周延**的條件，其中**周延**是指各個事件的聯集等於樣本空間者。

分割的概念可以由以下的圖示來理解:

<figure class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/total-probability-partition-strips.svg" alt="樣本空間 S 的矩形被垂直分線切成 A_1、A_2 到 A_n 等互不重疊的直條。">
  <figcaption><span class="topic-figure__label">Fig. 1.23.</span> 樣本空間 $S$ 被 $A_1,A_2,\ldots,A_n$ 切成數個互不重疊的部分，而這些事件的聯集恰為整個樣本空間。</figcaption>
</figure>

## 全機率定理

<div id="theorem-law-of-total-probability" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 1.16 (The Law of Total Probability)</div>

令 $(S,\mathcal{F},\mathbb{P})$ 為一機率空間，且令 $A_1,A_2,\ldots,A_n\in\mathcal{F}$ 為 $S$ 的一組[分割](#definition-partition)，$B\in\mathcal{F}$ 為一事件，則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(B)=\mathbb{P}\left(\bigcup_{i=1}^{n}(B\cap A_i)\right)=\sum_{i=1}^{n}\mathbb{P}(B\cap A_i)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(B)&=\mathbb{P}\left(\bigcup_{i=1}^{n}(B\cap A_i)\right)\\[0.4em]
&=\sum_{i=1}^{n}\mathbb{P}(B\cap A_i)
\end{aligned}
$$

</div>

</div>

<div class="topic-proof" markdown="1">
**Proof.** 由於 $A_1,A_2,\ldots,A_n$ 為 $S$ 的一組分割，故

$$
A_i\cap A_j=\varnothing,\ \forall i\neq j
$$

且

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
B=B\cap S=B\cap\left(\bigcup_{i=1}^{n}A_i\right)=\bigcup_{i=1}^{n}(B\cap A_i)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
B&=B\cap S=B\cap\left(\bigcup_{i=1}^{n}A_i\right)\\[0.4em]
&=\bigcup_{i=1}^{n}(B\cap A_i)
\end{aligned}
$$

</div>

此外，$B\cap A_1,B\cap A_2,\ldots,B\cap A_n$ 兩兩互斥，故由[有限可加性](/teaching-topics/probability-rules-from-axioms/#theorem-finite-additivity)可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(B)=\mathbb{P}\left(\bigcup_{i=1}^{n}(B\cap A_i)\right)=\sum_{i=1}^{n}\mathbb{P}(B\cap A_i)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(B)&=\mathbb{P}\left(\bigcup_{i=1}^{n}(B\cap A_i)\right)\\[0.4em]
&=\sum_{i=1}^{n}\mathbb{P}(B\cap A_i)
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

**全機率定理 (the law of total probability)** 的概念，我們在[兩事件版本的全機率定理](/teaching-topics/probability-rules-from-axioms/#theorem-total-and-addition)中即曾經提過；這裡的全機率定理，是將該定理由 $A$ 與 $A^{\prime}$ 這組特別的分割，推廣至一般的 $n$ 個事件所構成的分割，其概念可以由下圖理解:

<figure class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/total-probability-partition.svg" alt="樣本空間 S 的矩形被切成 A_1、A_2 到 A_n 等直條，事件 B 為橫跨各直條的圓角橫帶，並被分線切成 B 交 A_1 到 B 交 A_n 等區塊。">
  <figcaption><span class="topic-figure__label">Fig. 1.24.</span> 事件 $B$ 橫跨分割中的各個事件，因而被切成 $B\cap A_1,B\cap A_2,\ldots,B\cap A_n$ 這些互斥的部分。</figcaption>
</figure>

上圖中，$B$ 被這組分割交集成 $n$ 個互斥的集合 <span class="text-nowrap">$B\cap A_1,B\cap A_2,\ldots,B\cap A_n$，</span>其聯集即為 $B$ 本身，故由機率的[有限可加性](/teaching-topics/probability-rules-from-axioms/#theorem-finite-additivity)應可以推得上述的結果，且此結果之直觀意義，仍與[兩事件版本的全機率定理](/teaching-topics/probability-rules-from-axioms/#theorem-total-and-addition)所提到的直觀意義完全一致。

特別值得注意的一點是，全機率定理是許多交集機率的總和，故當然可以套用[乘法原理](/teaching-topics/conditional-probability-information/#theorem-18)，將交集機率改寫為以條件機率表示的版本。若進一步假設 $\mathbb{P}(A_i)>0$，$i=1,2,\ldots,n$，則有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(B)=\mathbb{P}\left(\bigcup_{i=1}^{n}(B\cap A_i)\right)=\sum_{i=1}^{n}\mathbb{P}(B\cap A_i)=\sum_{i=1}^{n}\mathbb{P}(B\mid A_i)\,\mathbb{P}(A_i)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(B)&=\mathbb{P}\left(\bigcup_{i=1}^{n}(B\cap A_i)\right)\\[0.4em]
&=\sum_{i=1}^{n}\mathbb{P}(B\cap A_i)\\[0.4em]
&=\sum_{i=1}^{n}\mathbb{P}(B\mid A_i)\,\mathbb{P}(A_i)
\end{aligned}
$$

</div>

這個表示式與乘法原理的好處相同，在某些僅知道條件機率的時候相當有用。

## 二元分割與列聯表

分割的概念可以推廣至兩組分割彼此的交集，我們稱為**二元分割**。二元分割的概念即為上一篇文章中的[列聯表](/teaching-topics/independence-and-conditional-independence/#互斥與獨立)，如下表:

| | $A_1$ | $\cdots$ | $A_n$ | 總和 |
| :---: | :---: | :---: | :---: | :---: |
| $B_1$ | $\mathbb{P}(A_1\cap B_1)$ | $\cdots$ | $\mathbb{P}(A_n\cap B_1)$ | $\mathbb{P}(B_1)$ |
| $\vdots$ | $\vdots$ | $\ddots$ | $\vdots$ | $\vdots$ |
| $B_m$ | $\mathbb{P}(A_1\cap B_m)$ | $\cdots$ | $\mathbb{P}(A_n\cap B_m)$ | $\mathbb{P}(B_m)$ |
| 總和 | $\mathbb{P}(A_1)$ | $\cdots$ | $\mathbb{P}(A_n)$ | $1$ |
{: .topic-table--joint-pmf}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

讀者應不難發現，聯合機率所對應的集合，如 $A_1\cap B_1$、$A_1\cap B_2$ 等，皆為彼此互斥的集合，其理由在於 $A_1,A_2,\ldots,A_n$ 與 $B_1,B_2,\ldots,B_m$ 分別是樣本空間 $S$ 中的兩組分割，故其彼此交集後的集合應仍為互斥集合。

進一步我們可以驗證，聯合機率的所有集合之聯集即是樣本空間，即

$$
\bigcup_{i=1}^{n}\bigcup_{j=1}^{m}(A_i\cap B_j)=S
$$

故這些集合應仍為一組分割，我們稱其為二元分割。
</div>

## 全機率定理的應用

<div id="example-symptoms-and-diseases" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.25 (Symptoms and Diseases)</div>

<div lang="en" markdown="1">
Suppose that a patient examined at a hospital is free of any disease with probability $0.99$, is affected by Disease $B$ with probability $0.001$, and is affected by Disease $C$ with probability $0.009$. These three states are the only possibilities. Symptom $A$ is observed with probability $0.001$ in a patient free of any disease, and with probability $0.9$ in each of the two diseased states. What is the probability that a patient chosen at random shows Symptom $A$?
</div>

令 $A$ 表有 $A$ 症狀、$B$ 表感染 $B$ 疾病、$C$ 表感染 $C$ 疾病、$N$ 表沒有感染疾病之事件。依題目敘述可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(A\mid N)=0.001,\qquad\mathbb{P}(A\mid B)=0.9,\qquad\mathbb{P}(A\mid C)=0.9
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{P}(A\mid N)=0.001\\[0.4em]
\mathbb{P}(A\mid B)=0.9\\[0.4em]
\mathbb{P}(A\mid C)=0.9
\end{gathered}
$$

</div>

且

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(N)=0.99,\qquad\mathbb{P}(B)=0.001,\qquad\mathbb{P}(C)=0.009
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{P}(N)=0.99\\[0.4em]
\mathbb{P}(B)=0.001\\[0.4em]
\mathbb{P}(C)=0.009
\end{gathered}
$$

</div>

由[乘法原理](/teaching-topics/conditional-probability-information/#theorem-18)可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\mathbb{P}(N\cap A)=\mathbb{P}(A\mid N)\,\mathbb{P}(N)=0.001\times 0.99=0.00099\\[0.4em]
\mathbb{P}(B\cap A)=\mathbb{P}(A\mid B)\,\mathbb{P}(B)=0.9\times 0.001=0.0009\\[0.4em]
\mathbb{P}(C\cap A)=\mathbb{P}(A\mid C)\,\mathbb{P}(C)=0.9\times 0.009=0.0081
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\begin{aligned}
\mathbb{P}(N\cap A)&=\mathbb{P}(A\mid N)\,\mathbb{P}(N)\\[0.4em]
&=0.001\times 0.99=0.00099
\end{aligned}\\[0.6em]
\begin{aligned}
\mathbb{P}(B\cap A)&=\mathbb{P}(A\mid B)\,\mathbb{P}(B)\\[0.4em]
&=0.9\times 0.001=0.0009
\end{aligned}\\[0.6em]
\begin{aligned}
\mathbb{P}(C\cap A)&=\mathbb{P}(A\mid C)\,\mathbb{P}(C)\\[0.4em]
&=0.9\times 0.009=0.0081
\end{aligned}
\end{gathered}
$$

</div>

由於 $N$、$B$、$C$ 兩兩互斥，且三者的聯集為整個樣本空間，故此三個事件為 $S$ 的一組[分割](#definition-partition)，因此由[全機率定理](#theorem-law-of-total-probability)可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(A)=\mathbb{P}(N\cap A)+\mathbb{P}(B\cap A)+\mathbb{P}(C\cap A)=0.00999
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(A)&=\mathbb{P}(N\cap A)+\mathbb{P}(B\cap A)\\[0.4em]
&\quad+\mathbb{P}(C\cap A)=0.00999
\end{aligned}
$$

</div>

</div>

<div id="example-111" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.26 (Manufacturing Defects)</div>

<div lang="en" markdown="1">
Three machines $A$, $B$, and $C$ produce the same item and account for $20\%$, $30\%$, and $50\%$ of the total output, respectively. Of the items made by $A$, $B$, and $C$, $5\%$, $4\%$, and $2\%$ are defective, respectively. One item is drawn at random from the combined output and inspected. What is the probability that the item drawn is defective?
</div>

令 $A$、$B$、$C$ 分別表示該產品來自 <span class="text-nowrap">$A$、$B$、$C$</span> 機台之事件，$R$ 表示不良品之事件。則由題意可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(A)=0.2,\qquad\mathbb{P}(B)=0.3,\qquad\mathbb{P}(C)=0.5
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{P}(A)=0.2\\[0.4em]
\mathbb{P}(B)=0.3\\[0.4em]
\mathbb{P}(C)=0.5
\end{gathered}
$$

</div>

且

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(R\mid A)=0.05,\qquad\mathbb{P}(R\mid B)=0.04,\qquad\mathbb{P}(R\mid C)=0.02
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{P}(R\mid A)=0.05\\[0.4em]
\mathbb{P}(R\mid B)=0.04\\[0.4em]
\mathbb{P}(R\mid C)=0.02
\end{gathered}
$$

</div>

由於抽出的產品必來自 $A$、$B$、$C$ 三台機器之一，此三個事件恰為樣本空間的一組[分割](#definition-partition)，故由[全機率定理](#theorem-law-of-total-probability)可知，所求為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(R)&=\mathbb{P}(R\mid A)\,\mathbb{P}(A)+\mathbb{P}(R\mid B)\,\mathbb{P}(B)+\mathbb{P}(R\mid C)\,\mathbb{P}(C)\\[0.4em]
&=0.05\times 0.2+0.04\times 0.3+0.02\times 0.5=0.032
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(R)=\mathbb{P}(R\mid A)\,\mathbb{P}(A)\\[0.4em]
&\hphantom{\mathbb{P}(R)=}+\mathbb{P}(R\mid B)\,\mathbb{P}(B)\\[0.4em]
&\hphantom{\mathbb{P}(R)=}+\mathbb{P}(R\mid C)\,\mathbb{P}(C)\\[0.4em]
&=0.05\times 0.2+0.04\times 0.3+0.02\times 0.5\\[0.4em]
&=0.032
\end{aligned}
$$

</div>

</div>

## 本篇小結

本篇由樣本空間的分割出發，依序整理下列結果:

| 結果 | 內容 |
| :---: | :---: |
| [Definition 1.23](#definition-partition) | 分割的互斥與周延條件 |
| [Theorem 1.16](#theorem-law-of-total-probability) | 全機率定理與其條件機率版本 |
| [二元分割](#二元分割與列聯表) | 兩組分割彼此交集所構成的列聯表 |

全機率定理把 $\mathbb{P}(B)$ 寫成各個條件機率 $\mathbb{P}(B\mid A_i)$ 以 $\mathbb{P}(A_i)$ 為權重的加權平均。既然整體機率由各組的條件機率混合而成，接下來自然要問，分組之後的比較方向與混合之後的比較方向是否一定相同。這會導向[分組、混合與辛普森悖論](/teaching-topics/group-mixing-simpsons-paradox/)。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Joseph K. Blitzstein and Jessica Hwang. 2019. *Introduction to Probability*. 2nd ed. Chapman and Hall/CRC.
