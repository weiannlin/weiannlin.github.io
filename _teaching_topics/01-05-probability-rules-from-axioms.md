---
title: "機率公理及其推論"
subtitle: "Probability Rules Derived from the Axioms"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 1
topic: 5
order: 105
permalink: /teaching-topics/probability-rules-from-axioms/
date: 2026-05-05
published: true
excerpt: "由柯爾莫哥洛夫三大公理出發，本篇依序推出虛無事件的機率、有限可加性、餘事件公式、全機率定理與加法原理、單調性、廣義加法原理，以及布爾與邦佛洛尼不等式，最後以單調事件序列的機率極限作結。"
---

[上一篇](/teaching-topics/event-families-sigma-fields/)整理了域、$\sigma$-域與機率空間。藉由機率公理，我們能夠衍伸出一些相當有用的機率等式與不等式，下面就從單一事件所構成的一些式子開始說明起。

## 虛無事件的機率

<div id="theorem-null-event" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 1.3 (Null Event)</div>

令 $(S,\mathcal{F},\mathbb{P})$ 為一機率空間，則

$$
\mathbb{P}(\varnothing)=0
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.**

令 $A_1=S$，$A_2=A_3=\cdots=\varnothing$，則 $A_i\in\mathcal{F}$ 對所有 $i\in\mathbb{N}$ 成立，$A_i\cap A_j=\varnothing$ 對所有 $i\neq j$ 成立，且

$$
\bigcup_{i=1}^{\infty}A_i=S\cup\varnothing\cup\varnothing\cup\cdots=S
$$

由可數可加性 (Axiom 3) 可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(S)=\mathbb{P}\left(\bigcup_{i=1}^{\infty}A_i\right)=\sum_{i=1}^{\infty}\mathbb{P}(A_i)=\mathbb{P}(S)+\mathbb{P}(\varnothing)+\mathbb{P}(\varnothing)+\cdots
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(S)&=\mathbb{P}\left(\bigcup_{i=1}^{\infty}A_i\right)=\sum_{i=1}^{\infty}\mathbb{P}(A_i)\\[0.4em]
&=\mathbb{P}(S)+\mathbb{P}(\varnothing)+\mathbb{P}(\varnothing)+\cdots
\end{aligned}
$$

</div>

兩邊消去 $\mathbb{P}(S)$，可得 $\sum_{i=2}^{\infty}\mathbb{P}(\varnothing)=0$；又由 Axiom 1 知 $\mathbb{P}(\varnothing)\geqslant 0$，故

$$
\mathbb{P}(\varnothing)=0
$$

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

在[隨機實驗、樣本空間與事件](/teaching-topics/random-experiments-sample-space-events/#事件與事件的發生)中我們曾經提到，虛無事件 (null event) 是一個一定會出現在任何樣本空間 $S$ 中的事件；事實上，它也一定會出現在任何佈於 $S$ 上的 $\sigma$-域 $\mathcal{F}$ 中。但究其意義，它代表的是「不可能發生的事件」，因為任何樣本空間的樣本點都不會落於其中。這樣的事件其機率為 $0$，相當符合我們的直觀。
</div>

<div id="example-odd-even-faces" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.10 (Odd and Even Faces)</div>

若投擲一公正骰子，令 $A$ 表出現點數為偶數點之事件、$B$ 表出現點數為奇數點之事件，試回答下列問題:

(1) 分別求出 $\mathbb{P}(A)$ 與 $\mathbb{P}(B)$。
{: .topic-paren-item}

(2) 若 $C$ 表示出現點數既為奇數又為偶數之事件，試求 $\mathbb{P}(C)$。
{: .topic-paren-item}

以下依序求解。

**(1)** 樣本空間為 $S=\lbrace1,2,3,4,5,6\rbrace$，由題意知 $A=\lbrace2,4,6\rbrace$，$B=\lbrace1,3,5\rbrace$，且骰子為公正骰子，故依[古典機率之定義](/teaching-topics/probability-assignment-classical-geometric/#definition-classical-probability)可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(A)=\frac{\mathrm{n}(A)}{\mathrm{n}(S)}=\frac{3}{6}=\frac{1}{2},\qquad
\mathbb{P}(B)=\frac{\mathrm{n}(B)}{\mathrm{n}(S)}=\frac{3}{6}=\frac{1}{2}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(A)&=\frac{\mathrm{n}(A)}{\mathrm{n}(S)}=\frac{3}{6}=\frac{1}{2},\\[0.4em]
\mathbb{P}(B)&=\frac{\mathrm{n}(B)}{\mathrm{n}(S)}=\frac{3}{6}=\frac{1}{2}
\end{aligned}
$$

</div>

**(2)** 依題意知 $C=A\cap B=\lbrace\,\rbrace=\varnothing$，故

$$
\mathbb{P}(C)=\mathbb{P}(\varnothing)=0
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

[Example 1.10](#example-odd-even-faces) (1) 使用了古典機率的定義。在[機率空間的定義](/teaching-topics/event-families-sigma-fields/#機率空間)中我們曾提到，公理化機率系統並沒有說明機率應該如何被測度，只說明機率應該具備的性質。這一點顯示，公理化機率並不與古典機率相抵觸，因為古典機率是以如何測度某事件的機率來定義的，二者並沒有衝突。
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

[Example 1.10](#example-odd-even-faces) (2) 的答案，讀者應可不必計算即知道其機率為 $0$，因為這原先就是一個「不可能發生的事件」，故直覺上其發生的機率為 $0$。然而，這個敘述的逆命題卻未必為真，換言之，即「機率為 $0$ 的事件未必不可能發生」。以 [Theorem 1.3](#theorem-null-event) 來思考此一觀點，即為「$\mathbb{P}(\varnothing)=0$，但機率為 $0$ 的事件卻未必是 $\varnothing$」。此一概念在下一章談到[隨機變數](/teaching-topics/random-variables-and-pmf/#def-random-variable)中的連續型變數將會更為清晰，但讀者不妨在此思考一個例子: 有一魔術表演專用的硬幣，有正反二面，但不論如何丟擲，最後都必定會呈現正面朝上，則**丟出反面**的機率是 $0$ (因為必然不會發生)，但**丟出反面的事件**卻不是 $\varnothing$，而是 $\lbrace\mathrm{T}\rbrace$。
</div>

從 [Theorem 1.3](#theorem-null-event) 可以發現，**不可能發生的事件機率一定為 $0$**。除了符合我們的直覺以外，這個定理還能引導出可數可加性的一個比較弱的版本，也就是**有限可加性 <span lang="en">(finite additivity)</span>**。

## 有限可加性

<div id="theorem-finite-additivity" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 1.4 <span lang="en">(Finite Additivity)</span></div>

令 $(S,\mathcal{F},\mathbb{P})$ 為一機率空間，若 $A_1,\ldots,A_n\in\mathcal{F}$，且 $A_i\cap A_j=\varnothing$ 對所有 $i\neq j$ 成立，則

$$
\mathbb{P}\left(\bigcup_{i=1}^{n}A_i\right)=\sum_{i=1}^{n}\mathbb{P}(A_i)
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.**

對所有 $k>n$ 令 $A_k=\varnothing$，即 $A_{n+1}=A_{n+2}=\cdots=\varnothing$，如此一來仍有 $A_i\cap A_j=\varnothing$ 對所有 $i\neq j$ 成立，且

$$
\bigcup_{i=1}^{\infty}A_i=\bigcup_{i=1}^{n}A_i\cup\varnothing\cup\varnothing\cup\cdots=\bigcup_{i=1}^{n}A_i
$$

由可數可加性 (Axiom 3) 與 $\mathbb{P}(\varnothing)=0$ 可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}\left(\bigcup_{i=1}^{n}A_i\right)=\sum_{i=1}^{\infty}\mathbb{P}(A_i)=\sum_{i=1}^{n}\mathbb{P}(A_i)+\sum_{i=n+1}^{\infty}\mathbb{P}(\varnothing)=\sum_{i=1}^{n}\mathbb{P}(A_i)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}\left(\bigcup_{i=1}^{n}A_i\right)&=\sum_{i=1}^{\infty}\mathbb{P}(A_i)\\[0.4em]
&=\sum_{i=1}^{n}\mathbb{P}(A_i)+\sum_{i=n+1}^{\infty}\mathbb{P}(\varnothing)\\[0.4em]
&=\sum_{i=1}^{n}\mathbb{P}(A_i)
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

有限可加性又被稱作**可加性 <span lang="en">(additivity)</span>**，是一個很有用的性質，特別是在探討有限個成對互斥集合間的機率關係時，我們可以不用每次都令一堆多餘的空集合，而只需要關注有限個集合本身的情況。

特別之處在於，我們常常會說有限可加性相較於可數可加性，是一個比較**弱 (weak)** 的性質，其理由正是源於上面的證明，因為可數可加性可以直接導致有限可加性的成立。

此外，如果一隨機實驗的結果只有有限多種 (即 $S$ 有限)，則任一佈於 $S$ 上的域 $\mathcal{F}$ 也會是有限的；此時，機率公理中的 Axiom 3 即使只滿足有限可加性，也足夠應付所有的狀況。

## 機率的範圍與餘事件公式

<div id="theorem-basic-equations" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 1.5 <span lang="en">(Basic Equations)</span></div>

令 $(S,\mathcal{F},\mathbb{P})$ 為一機率空間，$A\in\mathcal{F}$ 為一事件，則

(1) **機率的範圍**:
{: .topic-paren-item}

$$
\mathbb{P}(A)\leqslant 1
$$

(2) **餘事件公式**:
{: .topic-paren-item}

$$
\mathbb{P}(A^{\prime})=1-\mathbb{P}(A)
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.**

**(1)** 由 $A\cup A^{\prime}=S$ 且 $A\cap A^{\prime}=\varnothing$，再由 Axiom 2 與有限可加性可知

$$
\mathbb{P}(S)=\mathbb{P}(A\cup A^{\prime})=\mathbb{P}(A)+\mathbb{P}(A^{\prime})=1
$$

又由 Axiom 1 可知 $\mathbb{P}(A^{\prime})\geqslant 0$，故

$$
\mathbb{P}(A)=1-\mathbb{P}(A^{\prime})\leqslant 1
$$

**(2)** 由 (1) 之證明可知 $\mathbb{P}(A)=1-\mathbb{P}(A^{\prime})$，移項即得

$$
\mathbb{P}(A^{\prime})=1-\mathbb{P}(A)
$$

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

[Theorem 1.5](#theorem-basic-equations) (1) 把一個機率的範圍給了明確的限制。讀者應該記得，機率公理的非負性 (Axiom 1) 只有指出機率不得為負的，卻沒有說「機率至多只能是 $1$」。這是因為公理不需要證明其為真，故數學家通常追求在最少的公理之上建構整套理論，正是因此，機率公理中才沒有寫出這一點。
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

餘事件公式其實相當直觀，用文氏圖可以立刻想通:

<figure class="topic-figure">
  <img src="/images/teaching-topics/probability-rules-complement.svg" alt="餘事件公式的文氏圖。樣本空間的機率分為圓內的 P(A) 與圓外著色區域的 P(A prime) 兩部分。">
  <figcaption><span class="topic-figure__label">Fig. 1.9.</span> 樣本空間的機率被分為 $\mathbb{P}(A)$ 與 $\mathbb{P}(A^{\prime})$ 兩部分。</figcaption>
</figure>

這個概念很簡單，但卻是計算餘事件機率的相當實用的算法，往後我們會經常用到此結果。
</div>

讀者在這個階段會發現，這些關於機率的基礎性質，不過就是基於機率三大公理，以及過往我們所知道的一些集合關係，加以推導而得到的。整個機率論，便是基於這些看似簡單的基礎，透過層層堆疊而得，故讀者更應將基礎的重要性謹記於心。

接下來，我們將探討兩個事件間的機率關係。一如前面使用集合算子，來討論集合與集合間 (事件與事件間) 的關係，我們同樣可以在機率函數上，探討不同事件間的關係。

## 全機率定理與加法原理

<div id="theorem-total-and-addition" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 1.6 <span lang="en">(Law of Total Probability and Addition Rule)</span></div>

令 $(S,\mathcal{F},\mathbb{P})$ 為一機率空間，$A,B\in\mathcal{F}$ 為二事件，則

(1) **全機率定理 <span lang="en">(the law of total probability)</span>**:
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(B-A)=\mathbb{P}(B\cap A^{\prime})=\mathbb{P}(B)-\mathbb{P}(A\cap B)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(B-A)&=\mathbb{P}(B\cap A^{\prime})\\[0.4em]
&=\mathbb{P}(B)-\mathbb{P}(A\cap B)
\end{aligned}
$$

</div>

(2) **加法原理 <span lang="en">(addition rule)</span>**:
{: .topic-paren-item}

$$
\mathbb{P}(A\cup B)=\mathbb{P}(A)+\mathbb{P}(B)-\mathbb{P}(A\cap B)
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.**

**(1)** 由 $B=B\cap S$ 且 $S=A\cup A^{\prime}$，依分配律可知

$$
B=B\cap(A\cup A^{\prime})=(B\cap A)\cup(B\cap A^{\prime})
$$

又由於 $A\cap A^{\prime}=\varnothing$，所以

$$
(B\cap A)\cap(B\cap A^{\prime})=B\cap(A\cap A^{\prime})=\varnothing
$$

由有限可加性可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(B)=\mathbb{P}\big((B\cap A)\cup(B\cap A^{\prime})\big)=\mathbb{P}(B\cap A)+\mathbb{P}(B\cap A^{\prime})
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(B)&=\mathbb{P}\big((B\cap A)\cup(B\cap A^{\prime})\big)\\[0.4em]
&=\mathbb{P}(B\cap A)+\mathbb{P}(B\cap A^{\prime})
\end{aligned}
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

移項即得

$$
\mathbb{P}(B\cap A^{\prime})=\mathbb{P}(B-A)=\mathbb{P}(B)-\mathbb{P}(B\cap A)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

移項即得

$$
\begin{aligned}
\mathbb{P}(B\cap A^{\prime})&=\mathbb{P}(B-A)\\[0.4em]
&=\mathbb{P}(B)-\mathbb{P}(B\cap A)
\end{aligned}
$$

</div>

**(2)** 由 $A\cup B=(A\cap B^{\prime})\cup(A\cap B)\cup(A^{\prime}\cap B)$，且三者兩兩互斥:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
(A\cap B^{\prime})\cap(A\cap B)=(A\cap B)\cap(A^{\prime}\cap B)=(A\cap B^{\prime})\cap(A^{\prime}\cap B)=\varnothing
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&(A\cap B^{\prime})\cap(A\cap B)\\[0.4em]
&\qquad=(A\cap B)\cap(A^{\prime}\cap B)\\[0.4em]
&\qquad=(A\cap B^{\prime})\cap(A^{\prime}\cap B)=\varnothing
\end{aligned}
$$

</div>

由有限可加性可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(A\cup B)&=\mathbb{P}(A\cap B^{\prime})+\mathbb{P}(A\cap B)+\mathbb{P}(A^{\prime}\cap B)\\[0.4em]
&=\Big[\mathbb{P}(A\cap B^{\prime})+\mathbb{P}(A\cap B)\Big]+\Big[\mathbb{P}(A^{\prime}\cap B)+\mathbb{P}(A\cap B)\Big]\\[0.4em]
&\qquad-\mathbb{P}(A\cap B)\\[0.4em]
&=\mathbb{P}(A)+\mathbb{P}(B)-\mathbb{P}(A\cap B)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(A\cup B)&=\mathbb{P}(A\cap B^{\prime})+\mathbb{P}(A\cap B)\\[0.4em]
&\qquad+\mathbb{P}(A^{\prime}\cap B)\\[0.4em]
&=\Big[\mathbb{P}(A\cap B^{\prime})+\mathbb{P}(A\cap B)\Big]\\[0.4em]
&\qquad+\Big[\mathbb{P}(A^{\prime}\cap B)+\mathbb{P}(A\cap B)\Big]\\[0.4em]
&\qquad-\mathbb{P}(A\cap B)\\[0.4em]
&=\mathbb{P}(A)+\mathbb{P}(B)-\mathbb{P}(A\cap B)
\end{aligned}
$$

</div>

其中最後一步由 (1) 可知。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

全機率定理其實更常被寫為 $\mathbb{P}(B)=\mathbb{P}(A\cap B)+\mathbb{P}(A^{\prime}\cap B)$，也就是指，$B$ 的機率被分為有 $A$ 的部分與沒有 $A$ 的部分。這個表示法背後隱含的直覺為「任何事件都可被樣本空間的一組**分割 <span lang="en">(partition)</span>** 切成很多沒有交集的部分」；分割的概念在稍後的文章會有詳盡的介紹，讀者在此可將其想像為一種「各組間不重疊的分類方式」。其概念如下圖:

<figure class="topic-figure">
  <img src="/images/teaching-topics/probability-rules-total-partition.svg" alt="全機率定理的集合示意圖。樣本空間分為 A 與 A prime 兩塊，事件 B 橫跨兩塊，被切成 A 交 B 與 A prime 交 B 兩部分。">
  <figcaption><span class="topic-figure__label">Fig. 1.10.</span> $B$ 的機率被 $A$ 與 $A^{\prime}$ 切成 $\mathbb{P}(A\cap B)$ 與 $\mathbb{P}(A^{\prime}\cap B)$ 兩部分。</figcaption>
</figure>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

加法原理的證明漂亮地使用了全機率定理的結果。但事實上，如果對照[聯集與交集的文氏圖](/teaching-topics/event-set-operations/#聯集交集差集與餘集)，則加法原理本身也有非常直觀的圖例可以使用:

<figure class="topic-figure">
  <img src="/images/teaching-topics/probability-rules-addition-panels.svg" alt="加法原理的四格圖。A 聯集 B 的機率，等於 A 的機率加 B 的機率，再減去 A 交集 B 的機率。">
  <figcaption><span class="topic-figure__label">Fig. 1.11.</span> $\mathbb{P}(A\cup B)=\mathbb{P}(A)+\mathbb{P}(B)-\mathbb{P}(A\cap B)$ 的圖解。</figcaption>
</figure>

這張圖顯示，$A\cup B$ 的機率，事實上可以直接將 $A$ 的機率與 $B$ 的機率相加，再將其重複的部分 (也就是 $A\cap B$ 的機率) 扣除即可。
</div>

加法原理與全機率定理都有其應用上的特例，我們首先從加法原理開始。

注意到，當 $A$ 與 $B$ 互斥 (即 $A\cap B=\varnothing$) 時，由 [Theorem 1.3](#theorem-null-event) 得到 $\mathbb{P}(A\cup B)=\mathbb{P}(A)+\mathbb{P}(B)$，因為交集部分的機率為 $0$。

讀者應該會對這個情況感到熟悉，因為這個情況正好與[加集](/teaching-topics/event-set-operations/#互斥與加集)和有限可加性的前提相同，也就是 $A\cup B=A+B$，則由有限可加性，我們有

$$
\mathbb{P}(A\cup B)=\mathbb{P}(A+B)=\mathbb{P}(A)+\mathbb{P}(B)
$$

這也是[機率空間一篇](/teaching-topics/event-families-sigma-fields/#機率空間)提到的線性的特例。

全機率定理則是在當 $A$ 是 $B$ 的一個子集 (亦即 $A\subseteq B$) 時，會有一較為特殊的結果，這個結果是

$$
\mathbb{P}(B-A)=\mathbb{P}(B)-\mathbb{P}(A)
$$

其理由是，當 $A\subseteq B$ 時，$A\cap B=A$。證明此特例並不困難，讀者應可自行將全機率定理中的 $A\cap B$ 改寫為 $A$ 得到，我們僅以圖形說明此結果。

<figure class="topic-figure">
  <img src="/images/teaching-topics/probability-rules-subset-case.svg" alt="A 包含於 B 時的文氏圖。大圓 B 內含小圓 A，著色環狀區域的機率為 P(A prime 交 B)。">
  <figcaption><span class="topic-figure__label">Fig. 1.12.</span> $A\subseteq B$ 時的兩事件配置: $B$ 之中扣除 $A$ 後，剩下的機率是 $\mathbb{P}(A^{\prime}\cap B)$。</figcaption>
</figure>

上圖可以發現 $A\cap B$ 就是 $A$ 本身，故 $\mathbb{P}(A^{\prime}\cap B)$ 可用 $\mathbb{P}(B)$ 直接扣除 $\mathbb{P}(A)$ 得到。這個結果只是全機率定理的一個小特例，但是我們卻可以從這裡來驗證一個非常直觀的結果，即機率的**單調性 <span lang="en">(monotonicity)</span>**。

## 單調性

<div id="theorem-monotonicity" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 1.7 <span lang="en">(Monotonicity)</span></div>

令 $(S,\mathcal{F},\mathbb{P})$ 為一機率空間，$A,B\in\mathcal{F}$ 且 $A\subseteq B$，則

$$
\mathbb{P}(A)\leqslant\mathbb{P}(B)
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.**

由於 $A\subseteq B$，故 $B=(B-A)\cup A=(B-A)+A$，由有限可加性可知

$$
\mathbb{P}(B)=\mathbb{P}(B-A)+\mathbb{P}(A)
$$

又由 Axiom 1 可知 $\mathbb{P}(B-A)\geqslant 0$，故 $\mathbb{P}(B)\geqslant\mathbb{P}(A)$，即

$$
\mathbb{P}(A)\leqslant\mathbb{P}(B)
$$

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

單調性的直觀意義是，**比較小的集合，機率比較小**。這裡需要特別注意的地方是，我們沒辦法對任意兩個集合比大小，除非這兩個集合有彼此包含的關係，因此可以看出為何單調性需要 $A\subseteq B$ 的前提。
</div>

值得注意的是，我們可以將單調性進行一個簡單的延伸應用: 由 $(A\cap B)\subseteq A$ 與 $(A\cap B)\subseteq B$，可以推知

$$
\mathbb{P}(A\cap B)\leqslant\mathbb{P}(A),\qquad
\mathbb{P}(A\cap B)\leqslant\mathbb{P}(B)
$$

這兩種情況的直觀詮釋為: **對 $A$ (或 $B$) 給了更多限制 (使之與 $B$ (或 $A$) 交集)，只會讓機率變得更小 (頂多維持不變)**。

加法原理與全機率定理皆可推廣至三個以上的集合彼此間的狀況，其中全機率定理的推廣版本是**貝氏定理 (Bayes’ rule)** 的基礎，將在稍後的文章有詳盡的敘述。

## 廣義加法原理與排容原理

<div id="theorem-generalized-addition" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 1.8 <span lang="en">(Generalized Addition Rule)</span></div>

令 $(S,\mathcal{F},\mathbb{P})$ 為一機率空間，$A_1,\ldots,A_n\in\mathcal{F}$，且令

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
S_1=\sum_{i=1}^{n}\mathbb{P}(A_i),\qquad
S_2=\underset{i<j}{\sum\sum}\mathbb{P}(A_i\cap A_j),\\[0.4em]
S_3=\underset{i<j<k}{\sum\sum\sum}\mathbb{P}(A_i\cap A_j\cap A_k),\qquad
\ldots,\qquad
S_n=\mathbb{P}\left(\bigcap_{i=1}^{n}A_i\right)
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
S_1&=\sum_{i=1}^{n}\mathbb{P}(A_i),\\[0.4em]
S_2&=\underset{i<j}{\sum\sum}\mathbb{P}(A_i\cap A_j),\\[0.4em]
\ldots,\qquad
S_n&=\mathbb{P}\left(\bigcap_{i=1}^{n}A_i\right)
\end{aligned}
$$

</div>

一般而言，$S_k$ 是所有「$k$ 個事件交集的機率」之總和。則

(1) 當 $n$ 為奇數:
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}\left(\bigcup_{i=1}^{n}A_i\right)=S_1-S_2+S_3-\cdots-S_{n-1}+S_n
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}\left(\bigcup_{i=1}^{n}A_i\right)\\[0.4em]
&\qquad=S_1-S_2+S_3-\cdots-S_{n-1}+S_n
\end{aligned}
$$

</div>

(2) 當 $n$ 為偶數:
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}\left(\bigcup_{i=1}^{n}A_i\right)=S_1-S_2+S_3-\cdots+S_{n-1}-S_n
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}\left(\bigcup_{i=1}^{n}A_i\right)\\[0.4em]
&\qquad=S_1-S_2+S_3-\cdots+S_{n-1}-S_n
\end{aligned}
$$

</div>

</div>

<div class="topic-proof" markdown="1">
**Proof.**

見黃文璋 (2010)，《機率論》，二版，頁 39。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

在理解此定理時，建議讀者先以 $n=3$ 作為例子，並繪製出三個集合的文氏圖，協助理解其意義。其直觀的精神，仍然在於「扣除重複的部分」，只是三個以上的集合會遇到需要「加回多扣的部分」的狀況。

<figure class="topic-figure">
  <img src="/images/teaching-topics/probability-rules-inclusion-exclusion-three.svg" alt="三事件排容原理的集合示意圖。三個事件互相重疊時，中央共同交集會被多次計算。">
  <figcaption><span class="topic-figure__label">Fig. 1.13.</span> 三事件的情況中，兩兩交集先被扣除，而三者共同交集需要再加回來。</figcaption>
</figure>
</div>

廣義加法原理的內容，與**組合數學 <span lang="en">(combinatorics)</span>** 中的**排容原理 <span lang="en">(inclusion-exclusion principle)</span>** 是相同的，排容原理的機率版本，就是廣義加法原理。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

廣義的組合數學即為**離散數學 <span lang="en">(discrete mathematics)</span>**，其細部的差異在此並不探究。組合數學主要用以研究可數或離散空間中的數學問題，其中幾個著名的問題包含**地圖著色問題**與**渡河問題**；臺灣的高中數學所教授的排列組合，即是組合數學中的一個重要領域。
</div>

在部分機率論專書中，廣義加法原理時常以

$$
\mathbb{P}\left(\bigcup_{i=1}^{n}A_i\right)=\sum_{k=1}^{n}(-1)^{k-1}S_k
$$

的形式出現，並且被稱作**龐加萊 (Poincaré) 公式**。這個版本的寫法與 [Theorem 1.8](#theorem-generalized-addition) 完全相同，但較為簡潔，且對所有 $n\in\mathbb{N}$ 都成立，不需要考慮 $n$ 為奇數或偶數。

經由加法原理，我們可以得到兩個著名的不等式，即**布爾不等式 <span lang="en">(Boole’s inequality)</span>** 及**邦佛洛尼不等式 <span lang="en">(Bonferroni’s inequality)</span>**，以下就將兩個不等式分開討論。

## 布爾不等式

<div id="theorem-boole" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 1.9 <span lang="en">(Boole’s Inequality)</span></div>

令 $(S,\mathcal{F},\mathbb{P})$ 為一機率空間，$A_1,\ldots,A_n\in\mathcal{F}$，則

(1) 兩事件的情況:
{: .topic-paren-item}

$$
\mathbb{P}(A_1\cup A_2)\leqslant\mathbb{P}(A_1)+\mathbb{P}(A_2)
$$

(2) 推廣至 $n$ 個事件:
{: .topic-paren-item}

$$
\mathbb{P}\left(\bigcup_{i=1}^{n}A_i\right)\leqslant\sum_{i=1}^{n}\mathbb{P}(A_i)
$$

</div>

<div class="topic-proof" markdown="1">
<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

**Proof.**

**(1)** 由加法原理知

$$
\mathbb{P}(A_1\cup A_2)=\mathbb{P}(A_1)+\mathbb{P}(A_2)-\mathbb{P}(A_1\cap A_2)
$$

又 $\mathbb{P}(A_1\cap A_2)\geqslant 0$，故

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

**Proof.**

**(1)** 由加法原理知

$$
\begin{aligned}
\mathbb{P}(A_1\cup A_2)&=\mathbb{P}(A_1)+\mathbb{P}(A_2)\\[0.4em]
&\qquad-\mathbb{P}(A_1\cap A_2)
\end{aligned}
$$

又 $\mathbb{P}(A_1\cap A_2)\geqslant 0$，故

</div>

$$
\mathbb{P}(A_1\cup A_2)\leqslant\mathbb{P}(A_1)+\mathbb{P}(A_2)
$$

**(2)** 由 (1) 知道 $n=2$ 時原式顯然成立。又令 $n=k$ 時原式成立，即

$$
\mathbb{P}\left(\bigcup_{i=1}^{k}A_i\right)\leqslant\sum_{i=1}^{k}\mathbb{P}(A_i)
$$

則當 $n=k+1$ 時，由 (1) 可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}\left(\bigcup_{i=1}^{k+1}A_i\right)&=\mathbb{P}\left(\Big(\bigcup_{i=1}^{k}A_i\Big)\cup A_{k+1}\right)\\[0.4em]
&\leqslant\mathbb{P}\left(\bigcup_{i=1}^{k}A_i\right)+\mathbb{P}(A_{k+1})\\[0.4em]
&\leqslant\sum_{i=1}^{k}\mathbb{P}(A_i)+\mathbb{P}(A_{k+1})=\sum_{i=1}^{k+1}\mathbb{P}(A_i)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}\left(\bigcup_{i=1}^{k+1}A_i\right)&=\mathbb{P}\left(\Big(\bigcup_{i=1}^{k}A_i\Big)\cup A_{k+1}\right)\\[0.4em]
&\leqslant\mathbb{P}\left(\bigcup_{i=1}^{k}A_i\right)+\mathbb{P}(A_{k+1})\\[0.4em]
&\leqslant\sum_{i=1}^{k}\mathbb{P}(A_i)+\mathbb{P}(A_{k+1})\\[0.4em]
&=\sum_{i=1}^{k+1}\mathbb{P}(A_i)
\end{aligned}
$$

</div>

由數學歸納法與 (1) 可知，原式對所有 $n\in\mathbb{N}$ 皆成立。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

若將布爾不等式與加法原理相比較，不難發現這個不等式的直觀邏輯在於，「不等式右邊的交集部分的機率沒有被扣除」，所以右式總是會比左式來得大，也就是如下的圖示:

<figure class="topic-figure">
  <img src="/images/teaching-topics/probability-rules-boole-panels.svg" alt="布爾不等式的三格圖。A1 聯集 A2 的機率，小於等於 A1 的機率加 A2 的機率。">
  <figcaption><span class="topic-figure__label">Fig. 1.14.</span> $\mathbb{P}(A_1\cup A_2)\leqslant\mathbb{P}(A_1)+\mathbb{P}(A_2)$ 的圖解: 右側未扣除交集部分。</figcaption>
</figure>

我們只是在加法原理中，不將右側的交集機率扣除而已。其中，等式發生的情況發生在這組事件彼此為互斥事件，而這個情況，正好是加集與有限可加性的前提。
</div>

## 邦佛洛尼不等式

<div id="theorem-bonferroni" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 1.10 <span lang="en">(Bonferroni’s Inequality)</span></div>

令 $(S,\mathcal{F},\mathbb{P})$ 為一機率空間，$A_1,\ldots,A_n\in\mathcal{F}$，則

(1) 兩事件的情況:
{: .topic-paren-item}

$$
\mathbb{P}(A_1\cap A_2)\geqslant\mathbb{P}(A_1)+\mathbb{P}(A_2)-1
$$

(2) 推廣至 $n$ 個事件:
{: .topic-paren-item}

$$
\mathbb{P}\left(\bigcap_{i=1}^{n}A_i\right)\geqslant\sum_{i=1}^{n}\mathbb{P}(A_i)-(n-1)
$$

</div>

<div class="topic-proof" markdown="1">
<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

**Proof.**

**(1)** 由加法原理知

$$
\mathbb{P}(A_1\cup A_2)=\mathbb{P}(A_1)+\mathbb{P}(A_2)-\mathbb{P}(A_1\cap A_2)
$$

移項可得

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

**Proof.**

**(1)** 由加法原理知

$$
\begin{aligned}
\mathbb{P}(A_1\cup A_2)&=\mathbb{P}(A_1)+\mathbb{P}(A_2)\\[0.4em]
&\qquad-\mathbb{P}(A_1\cap A_2)
\end{aligned}
$$

移項可得

</div>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(A_1\cap A_2)=\mathbb{P}(A_1)+\mathbb{P}(A_2)-\mathbb{P}(A_1\cup A_2)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(A_1\cap A_2)&=\mathbb{P}(A_1)+\mathbb{P}(A_2)\\[0.4em]
&\qquad-\mathbb{P}(A_1\cup A_2)
\end{aligned}
$$

</div>

又由 $\mathbb{P}(A_1\cup A_2)\leqslant 1$，故

$$
\mathbb{P}(A_1\cap A_2)\geqslant\mathbb{P}(A_1)+\mathbb{P}(A_2)-1
$$

**(2)** 由 (1) 知道 $n=2$ 時原式顯然成立。又令 $n=k$ 時原式成立，即

$$
\mathbb{P}\left(\bigcap_{i=1}^{k}A_i\right)\geqslant\sum_{i=1}^{k}\mathbb{P}(A_i)-(k-1)
$$

則當 $n=k+1$ 時，由 (1) 可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}\left(\bigcap_{i=1}^{k+1}A_i\right)&=\mathbb{P}\left(\Big(\bigcap_{i=1}^{k}A_i\Big)\cap A_{k+1}\right)\\[0.4em]
&\geqslant\mathbb{P}\left(\bigcap_{i=1}^{k}A_i\right)+\mathbb{P}(A_{k+1})-1\\[0.4em]
&\geqslant\sum_{i=1}^{k}\mathbb{P}(A_i)-(k-1)+\mathbb{P}(A_{k+1})-1\\[0.4em]
&=\sum_{i=1}^{k+1}\mathbb{P}(A_i)-\big[(k+1)-1\big]
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}&\left(\bigcap_{i=1}^{k+1}A_i\right)=\mathbb{P}\left(\Big(\bigcap_{i=1}^{k}A_i\Big)\cap A_{k+1}\right)\\[0.4em]
&\geqslant\mathbb{P}\left(\bigcap_{i=1}^{k}A_i\right)+\mathbb{P}(A_{k+1})-1\\[0.4em]
&\geqslant\sum_{i=1}^{k}\mathbb{P}(A_i)-(k-1)+\mathbb{P}(A_{k+1})-1\\[0.4em]
&=\sum_{i=1}^{k+1}\mathbb{P}(A_i)-\big[(k+1)-1\big]
\end{aligned}
$$

</div>

由數學歸納法與 (1) 可知，原式對所有 $n\in\mathbb{N}$ 皆成立。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

邦佛洛尼不等式的右式，常被改寫為 $1-\sum_{i=1}^{n}\mathbb{P}(A_i^{\prime})$，作法是把每個 $\mathbb{P}(A_i)$ 都改為 $1-\mathbb{P}(A_i^{\prime})$。

這個版本的邦佛洛尼不等式，更容易看出其直觀。以 $n=2$ 為例 (即 [Theorem 1.10](#theorem-bonferroni) 中的 (1) 式)，其直覺在於「不等式右邊的重複部分的機率 (也就是 $\mathbb{P}(A_1^{\prime}\cap A_2^{\prime})$) 被重複扣除了」，如下圖:

<figure class="topic-figure">
  <img src="/images/teaching-topics/probability-rules-bonferroni-panels.svg" alt="邦佛洛尼不等式的四格圖。A1 交集 A2 的機率，大於等於 1 減 A1 補集的機率減 A2 補集的機率。">
  <figcaption><span class="topic-figure__label">Fig. 1.15.</span> $\mathbb{P}(A_1\cap A_2)\geqslant 1-\mathbb{P}(A_1^{\prime})-\mathbb{P}(A_2^{\prime})$ 的圖解: $\mathbb{P}(A_1^{\prime}\cap A_2^{\prime})$ 被重複扣除。</figcaption>
</figure>

其關鍵就在於 $\mathbb{P}(A_1^{\prime}\cap A_2^{\prime})$ 被重複扣除 (且有可能會扣成負的)。而等號成立的條件在於，$A_1$ 與 $A_2$ 沒有同時不成立的部分的時候。這個特例的情況有很多種，但必定是發生在 $A_1$ 與 $A_2$ 的聯集就已經「填滿」樣本空間的情況，也就是 $A_1\cup A_2=S$ 時；而且這個條件與布爾不等式的等號成立條件其實有關係，讀者不妨思考看看。
</div>

## 兩不等式的等價性

事實上我們應可以發現，布爾不等式與邦佛洛尼不等式的出發點同為加法原理，只是一者以聯集為出發，而一者以交集為出發。細心一點的讀者可能在此提問: 這兩個不等式**等價 <span lang="en">(equivalent)</span>** 嗎？這個問題的答案是肯定的，我們在此以狄摩根律證明。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

證明中將使用的**不失一般性 (without loss of generality，或簡稱 WLOG)**，是數學證明中的一種常用表示法，其最主要的目的是用來表示，在這個條件下所假設的東西足以代表一般的所有狀況，而非僅是一個特例。
</div>

<div class="topic-proof" markdown="1">
**Proof.**

令 $(S,\mathcal{F},\mathbb{P})$ 為一機率空間，不失一般性假設 $A_1,\ldots,A_n\in\mathcal{F}$，且令布爾不等式成立，即

$$
\mathbb{P}\left(\bigcup_{i=1}^{n}A_i\right)\leqslant\sum_{i=1}^{n}\mathbb{P}(A_i)
$$

此式成立，若且唯若

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}\left(\bigcap_{i=1}^{n}A_i^{\prime}\right)&=\mathbb{P}\left(\Big(\bigcup_{i=1}^{n}A_i\Big)^{\prime}\right)\\[0.4em]
&=1-\mathbb{P}\left(\bigcup_{i=1}^{n}A_i\right)\\[0.4em]
&\geqslant 1-\sum_{i=1}^{n}\mathbb{P}(A_i)\\[0.4em]
&=1-\sum_{i=1}^{n}\big(1-\mathbb{P}(A_i^{\prime})\big)\\[0.4em]
&=1-\Big(n-\sum_{i=1}^{n}\mathbb{P}(A_i^{\prime})\Big)\\[0.4em]
&=\sum_{i=1}^{n}\mathbb{P}(A_i^{\prime})-(n-1)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}\left(\bigcap_{i=1}^{n}A_i^{\prime}\right)&=\mathbb{P}\left(\Big(\bigcup_{i=1}^{n}A_i\Big)^{\prime}\right)\\[0.4em]
&=1-\mathbb{P}\left(\bigcup_{i=1}^{n}A_i\right)\\[0.4em]
&\geqslant 1-\sum_{i=1}^{n}\mathbb{P}(A_i)\\[0.4em]
&=1-\sum_{i=1}^{n}\big(1-\mathbb{P}(A_i^{\prime})\big)\\[0.4em]
&=1-\Big(n-\sum_{i=1}^{n}\mathbb{P}(A_i^{\prime})\Big)\\[0.4em]
&=\sum_{i=1}^{n}\mathbb{P}(A_i^{\prime})-(n-1)
\end{aligned}
$$

</div>

其中，由 $A_1,\ldots,A_n\in\mathcal{F}$ 知道 $A_1^{\prime},\ldots,A_n^{\prime}\in\mathcal{F}$，且

$$
\mathbb{P}\left(\bigcap_{i=1}^{n}A_i^{\prime}\right)\geqslant\sum_{i=1}^{n}\mathbb{P}(A_i^{\prime})-(n-1)
$$

即邦佛洛尼不等式。故可知道布爾不等式成立，若且唯若邦佛洛尼不等式成立，二者為等價不等式。 <span class="topic-qed">$\square$</span>
</div>

<div id="example-union-covers" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.11 <span lang="en">(Union Covering the Sample Space)</span></div>

<div lang="en" markdown="1">
If the sample space is $S=C_1\cup C_2$ and if $\mathbb{P}(C_1)=0.8$ and $\mathbb{P}(C_2)=0.5$, find $\mathbb{P}(C_1\cap C_2)$.
</div>

由加法原理知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(C_1\cup C_2)=\mathbb{P}(C_1)+\mathbb{P}(C_2)-\mathbb{P}(C_1\cap C_2)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(C_1\cup C_2)&=\mathbb{P}(C_1)+\mathbb{P}(C_2)\\[0.4em]
&\qquad-\mathbb{P}(C_1\cap C_2)
\end{aligned}
$$

</div>

又由 Axiom 2 知 $\mathbb{P}(S)=\mathbb{P}(C_1\cup C_2)=1$，故

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
1=\mathbb{P}(C_1)+\mathbb{P}(C_2)-\mathbb{P}(C_1\cap C_2)=0.8+0.5-\mathbb{P}(C_1\cap C_2)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
1&=\mathbb{P}(C_1)+\mathbb{P}(C_2)-\mathbb{P}(C_1\cap C_2)\\[0.4em]
&=0.8+0.5-\mathbb{P}(C_1\cap C_2)
\end{aligned}
$$

</div>

移項可得

$$
\mathbb{P}(C_1\cap C_2)=0.8+0.5-1=0.3
$$

</div>

<div id="example-disjoint-and-bound" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.12 <span lang="en">(Disjoint Complements and a Lower Bound)</span></div>

<div lang="en" markdown="1">
(1) Suppose that two events $A$ and $B$ cannot occur at the same time. Under what condition is the same true of their complements $A^{\prime}$ and <span class="text-nowrap">$B^{\prime}$?</span>
{: .topic-paren-item}

(2) Suppose that $A_1$, $A_2$, and $A_3$ are events with $\mathbb{P}(A_i)=\frac{1}{4+i}$ for <span class="text-nowrap">$i=1,2,3$.</span> Find a lower bound for the probability that none of the three occurs.
{: .topic-paren-item}
</div>

以下依序求解。

**(1)** 由 $A$ 與 $B$ 互斥可知 $A\cap B=\varnothing$。又 $A^{\prime}$ 與 $B^{\prime}$ 互斥，即要求

$$
A^{\prime}\cap B^{\prime}=(A\cup B)^{\prime}=\varnothing
$$

故所求條件為

$$
A\cup B=S
$$

**(2)** 將邦佛洛尼不等式的改寫形式套用於 $A_1^{\prime},A_2^{\prime},A_3^{\prime}$，可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(A_1^{\prime}\cap A_2^{\prime}\cap A_3^{\prime})&\geqslant 1-\sum_{i=1}^{3}\mathbb{P}\big((A_i^{\prime})^{\prime}\big)=1-\sum_{i=1}^{3}\mathbb{P}(A_i)\\[0.4em]
&=1-\frac{1}{5}-\frac{1}{6}-\frac{1}{7}=\frac{103}{210}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(A_1^{\prime}\cap A_2^{\prime}\cap A_3^{\prime})&\geqslant 1-\sum_{i=1}^{3}\mathbb{P}\big((A_i^{\prime})^{\prime}\big)\\[0.4em]
&=1-\sum_{i=1}^{3}\mathbb{P}(A_i)\\[0.4em]
&=1-\frac{1}{5}-\frac{1}{6}-\frac{1}{7}\\[0.4em]
&=\frac{103}{210}
\end{aligned}
$$

</div>

</div>

## 單調事件序列的機率極限

<div id="theorem-continuity" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 1.11 <span lang="en">(Limits along Monotone Sequences)</span></div>

令 $(S,\mathcal{F},\mathbb{P})$ 為一機率空間，$A_1,A_2,\ldots\in\mathcal{F}$。

(1) 若 $\lbrace A_i\rbrace$ 為非遞減序列，則
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lim_{n\to\infty}\mathbb{P}(A_n)=\mathbb{P}\left(\lim_{n\to\infty}A_n\right)=\mathbb{P}\left(\bigcup_{i=1}^{\infty}A_i\right)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\lim_{n\to\infty}\mathbb{P}(A_n)&=\mathbb{P}\left(\lim_{n\to\infty}A_n\right)\\[0.4em]
&=\mathbb{P}\left(\bigcup_{i=1}^{\infty}A_i\right)
\end{aligned}
$$

</div>

(2) 若 $\lbrace A_i\rbrace$ 為非遞增序列，則
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lim_{n\to\infty}\mathbb{P}(A_n)=\mathbb{P}\left(\lim_{n\to\infty}A_n\right)=\mathbb{P}\left(\bigcap_{i=1}^{\infty}A_i\right)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\lim_{n\to\infty}\mathbb{P}(A_n)&=\mathbb{P}\left(\lim_{n\to\infty}A_n\right)\\[0.4em]
&=\mathbb{P}\left(\bigcap_{i=1}^{\infty}A_i\right)
\end{aligned}
$$

</div>

</div>

<div class="topic-proof" markdown="1">
**Proof.**

**(1)** 由於 $\lbrace A_i\rbrace$ 非遞減，故依[單調集合序列的定義](/teaching-topics/event-set-operations/#單調集合序列與極限)可知

$$
\lim_{n\to\infty}A_n=\bigcup_{i=1}^{\infty}A_i
$$

另外定義 $\lbrace B_i\rbrace$，滿足

$$
B_1=A_1,\qquad B_k=A_k-A_{k-1},\quad k\geqslant 2
$$

則 $\lbrace B_i\rbrace$ 兩兩為互斥事件，且

$$
\begin{gathered}
A_k=\bigcup_{i=1}^{k}B_i\\[0.4em]
\mathbb{P}(B_i)=\mathbb{P}(A_i)-\mathbb{P}(A_{i-1}),\quad i\geqslant 2
\end{gathered}
$$

此外，又因 $\lbrace A_i\rbrace$ 非遞減，可知

$$
\bigcup_{i=1}^{k}A_i=A_k=\bigcup_{i=1}^{k}B_i
$$

由此可得

$$
\bigcup_{i=1}^{\infty}A_i=\lim_{n\to\infty}A_n=\bigcup_{i=1}^{\infty}B_i=\sum_{i=1}^{\infty}B_i
$$

注意此處之 $\lbrace B_i\rbrace$ 兩兩為互斥事件，由可數可加性可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}\left(\lim_{n\to\infty}A_n\right)&=\mathbb{P}\left(\bigcup_{i=1}^{\infty}B_i\right)=\sum_{i=1}^{\infty}\mathbb{P}(B_i)=\lim_{n\to\infty}\sum_{i=1}^{n}\mathbb{P}(B_i)\\[0.4em]
&=\mathbb{P}(A_1)+\lim_{n\to\infty}\sum_{i=2}^{n}\Big[\mathbb{P}(A_i)-\mathbb{P}(A_{i-1})\Big]=\lim_{n\to\infty}\mathbb{P}(A_n)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}\left(\lim_{n\to\infty}A_n\right)=\mathbb{P}\left(\bigcup_{i=1}^{\infty}B_i\right)\\[0.4em]
&=\sum_{i=1}^{\infty}\mathbb{P}(B_i)=\lim_{n\to\infty}\sum_{i=1}^{n}\mathbb{P}(B_i)\\[0.4em]
&=\mathbb{P}(A_1)+\lim_{n\to\infty}\sum_{i=2}^{n}\Big[\mathbb{P}(A_i)-\mathbb{P}(A_{i-1})\Big]\\[0.4em]
&=\lim_{n\to\infty}\mathbb{P}(A_n)
\end{aligned}
$$

</div>

原式得證。

**(2)** 由於 $\lbrace A_i\rbrace$ 非遞增，故依[單調集合序列的定義](/teaching-topics/event-set-operations/#單調集合序列與極限)可知

$$
\lim_{n\to\infty}A_n=\bigcap_{i=1}^{\infty}A_i
$$

此外，$\lbrace A_i^{\prime}\rbrace$ 為非遞減序列。由狄摩根律與非遞減序列的定義可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\left(\lim_{n\to\infty}A_n\right)^{\prime}=\left(\bigcap_{i=1}^{\infty}A_i\right)^{\prime}=\bigcup_{i=1}^{\infty}A_i^{\prime}=\lim_{n\to\infty}A_n^{\prime}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\left(\lim_{n\to\infty}A_n\right)^{\prime}&=\left(\bigcap_{i=1}^{\infty}A_i\right)^{\prime}\\[0.4em]
&=\bigcup_{i=1}^{\infty}A_i^{\prime}=\lim_{n\to\infty}A_n^{\prime}
\end{aligned}
$$

</div>

故合併 (1) 的結果，我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}\left(\lim_{n\to\infty}A_n\right)&=1-\mathbb{P}\left(\Big(\lim_{n\to\infty}A_n\Big)^{\prime}\right)=1-\mathbb{P}\left(\lim_{n\to\infty}A_n^{\prime}\right)\\[0.4em]
&=1-\lim_{n\to\infty}\mathbb{P}(A_n^{\prime})=\lim_{n\to\infty}\Big(1-\mathbb{P}(A_n^{\prime})\Big)=\lim_{n\to\infty}\mathbb{P}(A_n)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}\left(\lim_{n\to\infty}A_n\right)&=1-\mathbb{P}\left(\Big(\lim_{n\to\infty}A_n\Big)^{\prime}\right)\\[0.4em]
&=1-\mathbb{P}\left(\lim_{n\to\infty}A_n^{\prime}\right)\\[0.4em]
&=1-\lim_{n\to\infty}\mathbb{P}(A_n^{\prime})\\[0.4em]
&=\lim_{n\to\infty}\Big(1-\mathbb{P}(A_n^{\prime})\Big)\\[0.4em]
&=\lim_{n\to\infty}\mathbb{P}(A_n)
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

## 本篇小結

本篇由三大公理出發，依序推得下列結果:

| 結果 | 內容 |
| :---: | :---: |
| [Theorem 1.3](#theorem-null-event) | $\mathbb{P}(\varnothing)=0$ |
| [Theorem 1.4](#theorem-finite-additivity) | 有限可加性 |
| [Theorem 1.5](#theorem-basic-equations) | $\mathbb{P}(A)\leqslant 1$ 與餘事件公式 |
| [Theorem 1.6](#theorem-total-and-addition) | 全機率定理與加法原理 |
| [Theorem 1.7](#theorem-monotonicity) | 單調性 |
| [Theorem 1.8](#theorem-generalized-addition) | 廣義加法原理 (排容原理) |
| [Theorem 1.9](#theorem-boole) 與 [Theorem 1.10](#theorem-bonferroni) | 布爾與邦佛洛尼不等式 (等價) |
| [Theorem 1.11](#theorem-continuity) | 單調事件序列的機率極限 |

加法原理與全機率定理皆可推廣至三個以上的集合彼此間的狀況，其中全機率定理的推廣版本是貝氏定理的基礎。[下一篇](/teaching-topics/conditional-probability-information/)要談條件機率與乘法原理，便從「已知某事件發生」如何改變機率談起。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Emanuel Parzen. 1960. *Modern Probability Theory and Its Applications*. Wiley.
- Alan Hájek. 2019. “Interpretations of Probability.” In *The Stanford Encyclopedia of Philosophy*, Fall 2019 ed., edited by Edward N. Zalta.
