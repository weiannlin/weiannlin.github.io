---
title: "貝氏定理"
subtitle: "Bayes’ Rule and Updating Information"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 1
topic: 10
order: 110
permalink: /teaching-topics/bayes-rule-posterior-probability/
date: 2026-05-06
published: true
excerpt: "貝氏定理的分母即是全機率定理，它把事前機率與條件機率轉化為事後機率。本篇介紹貝氏定理、事前與事後機率的意義、計算流程的樹狀圖，以及由觀察結果反推來源的例題。"
---

[上一篇](/teaching-topics/group-mixing-simpsons-paradox/)說明，分組內的比較方向與混合後的比較方向未必相同。本篇回到全機率定理，並把它反過來讀: 全機率定理由各個來源 $A_i$ 的機率與條件機率合成事件 $B$ 的機率；貝氏定理則在 $B$ 已經發生的條件下，回頭計算 $B$ 來自各個來源的機率。

## 貝氏定理

<div id="theorem-bayes-rule" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 1.17 (Bayes’ Rule)</div>

令 $(S,\mathcal{F},\mathbb{P})$ 為一機率空間，且令 $A_1,A_2,\ldots,A_n\in\mathcal{F}$ 為 $S$ 的一組[分割](/teaching-topics/total-probability-bayes-rule/#definition-partition)，$B\in\mathcal{F}$ 為一事件。若 $\mathbb{P}(B)>0$ 且 $\mathbb{P}(A_i)>0$，$i=1,2,\ldots,n$，則對任意 $i=1,2,\ldots,n$，皆有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(A_i\mid B)&=\frac{\mathbb{P}(A_i\cap B)}{\mathbb{P}(B)}=\frac{\mathbb{P}(B\cap A_i)}{\sum_{j=1}^{n}\mathbb{P}(B\cap A_j)}\\[0.4em]
&=\frac{\mathbb{P}(B\mid A_i)\,\mathbb{P}(A_i)}{\sum_{j=1}^{n}\mathbb{P}(B\mid A_j)\,\mathbb{P}(A_j)}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(A_i\mid B)&=\frac{\mathbb{P}(A_i\cap B)}{\mathbb{P}(B)}\\[0.4em]
&=\frac{\mathbb{P}(B\cap A_i)}{\sum_{j=1}^{n}\mathbb{P}(B\cap A_j)}\\[0.4em]
&=\frac{\mathbb{P}(B\mid A_i)\,\mathbb{P}(A_i)}{\sum_{j=1}^{n}\mathbb{P}(B\mid A_j)\,\mathbb{P}(A_j)}
\end{aligned}
$$

</div>

此性質稱為**貝氏定理 (Bayes’ rule)**。
</div>

<div class="topic-proof" markdown="1">
**Proof.** 第一個等號即[條件機率](/teaching-topics/conditional-probability-information/#definition-conditional-probability)的定義。由於 $A_1,A_2,\ldots,A_n$ 為 $S$ 的一組分割，由[全機率定理](/teaching-topics/total-probability-bayes-rule/#theorem-law-of-total-probability)可知

$$
\mathbb{P}(B)=\sum_{j=1}^{n}\mathbb{P}(B\cap A_j)
$$

將其代入分母，並將分子依交換律改寫為 $\mathbb{P}(B\cap A_i)$，即得第二個等號。最後對分子與分母中的每一個交集機率套用[乘法原理](/teaching-topics/conditional-probability-information/#theorem-18)，即

$$
\mathbb{P}(B\cap A_j)=\mathbb{P}(B\mid A_j)\,\mathbb{P}(A_j)
$$

便得第三個等號。原式得證。 <span class="topic-qed">$\square$</span>
</div>

上述定理中有幾個特別需要注意的地方:

<ol class="topic-list-paren">
  <li>$\mathbb{P}(A_i)$，$i=1,2,\ldots,n$，稱作<strong class="text-nowrap">事前機率 <span lang="en">(prior probability)</span></strong>，或稱先驗機率。</li>
  <li>$\mathbb{P}(A_i\mid B)$，$i=1,2,\ldots,n$，稱作<strong class="text-nowrap">事後機率 <span lang="en">(posterior probability)</span></strong>，或稱後驗機率。</li>
  <li>$\mathbb{P}(B\mid A_i)$，$i=1,2,\ldots,n$，為在 $A_i$ 發生的條件下 $B$ 的條件機率。</li>
</ol>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

所謂的「事前」與「事後」，都是**相對於事件 $B$ 而言**，即「$B$ 發生前」與「$B$ 發生後」。
</div>

事實上，貝氏定理的計算本身並不困難，其分母的部分即是[全機率定理](/teaching-topics/total-probability-bayes-rule/#theorem-law-of-total-probability)，但其結果卻相當漂亮，簡潔地將事前機率與條件機率轉化為事後機率，並且帶出了**$B$ 事件如何影響研究者認知 $A_i$ 事件**的關係。

## 事前機率、條件機率與交集機率的關係

貝氏定理的概念及計算流程可以使用**樹狀圖 <span lang="en">(tree diagram)</span>** 來輔助。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

樹狀圖又稱作樹形圖，是一種具階層式構造的圖形，而其擴散出去的分支形象有如一棵倒過來或橫躺的樹，故得此名。在**圖論 (graph theory)** 與集合論中，樹狀圖是相當重要的討論工具。
</div>

其計算流程可以由下圖理解:

<figure id="fig-bayes-flow" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/bayes-rule-flow.svg" alt="樣本空間 S 的矩形被切成 A_1、A_2 到 A_n 等直條，事件 B 為橫跨各直條的橫帶。上方由 prior probability 方框分出三條箭頭指向各直條，分別標示 P(A_1)、P(A_2) 與 P(A_n)；下方由各直條分出三條箭頭，分別標示 P(B 給定 A_1)、P(B 給定 A_2) 與 P(B 給定 A_n)，箭頭末端為 P(B 交 A_1)、P(B 交 A_2) 與 P(B 交 A_n)。下方三條箭頭之間另有 conditional probability 方框，與上方的 prior probability 方框相對。">
  <figcaption><span class="topic-figure__label">Fig. 1.25.</span> 事前機率 $\mathbb{P}(A_i)$ 先決定樣本空間落在哪一個 $A_i$，條件機率 $\mathbb{P}(B\mid A_i)$ 再決定該條件下 $B$ 是否發生，兩者相乘即為交集機率 $\mathbb{P}(B\cap A_i)$。</figcaption>
</figure>

上圖中，事前機率 $\mathbb{P}(A_i)$ 是指，在沒有任何事件發生下，發生 $A_i$ 事件的機率；而一旦發生 $A_i$ 事件後，樣本空間應縮小至 $A_i$ 內，此時條件機率 $\mathbb{P}(B\mid A_i)$ 是指，在已發生了 $A_i$ 的條件下，再發生 $B$ 事件的機率；若將此二者用[乘法原理](/teaching-topics/conditional-probability-information/#theorem-18)相乘，則可得到 $B\cap A_i$ 的交集機率。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

(1) 讀者可以回憶，我們曾經在[乘法原理](/teaching-topics/conditional-probability-information/#theorem-18)中提過對條件機率的理解，若將其套用在此處，則條件機率可以視為 $A_i$ 中 $B$ 所佔的比例。
{: .topic-paren-item}

(2) 乘法原理將條件機率還原回非條件機率 (即交集機率) 的過程，實際上也是在將樣本空間還原回 $S$，故此處交集機率的樣本空間應為 $S$，而不是再限縮於 $A_i$ 內。
{: .topic-paren-item}
</div>

## 貝氏定理的應用

<div id="example-symptoms-and-diseases-continued" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.25 <span lang="en">(Continued)</span></div>

<div lang="en" markdown="1">
Suppose that a patient examined at a hospital is free of any disease with probability $0.99$, is affected by Disease $B$ with probability $0.001$, and is affected by Disease $C$ with probability $0.009$. These three states are the only possibilities. Symptom $A$ is observed with probability $0.001$ in a patient free of any disease, and with probability $0.9$ in each of the two diseased states. Given that a patient shows Symptom $A$, what is the probability that this patient is affected by Disease $C$?
</div>

令 $A$ 表有 $A$ 症狀、$B$ 表感染 $B$ 疾病、$C$ 表感染 $C$ 疾病、$N$ 表沒有感染疾病之事件。前一篇的 [Example 1.25](/teaching-topics/total-probability-bayes-rule/#example-symptoms-and-diseases) 已由[乘法原理](/teaching-topics/conditional-probability-information/#theorem-18)求得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(N\cap A)=0.00099,\quad\mathbb{P}(B\cap A)=0.0009,\quad\mathbb{P}(C\cap A)=0.0081
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{P}(N\cap A)=0.00099\\[0.4em]
\mathbb{P}(B\cap A)=0.0009\\[0.4em]
\mathbb{P}(C\cap A)=0.0081
\end{gathered}
$$

</div>

且

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

故由[貝氏定理](#theorem-bayes-rule)可知，所求為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(C\mid A)=\frac{\mathbb{P}(C\cap A)}{\mathbb{P}(A)}=\frac{0.0081}{0.00999}\fallingdotseq 0.8108
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(C\mid A)&=\frac{\mathbb{P}(C\cap A)}{\mathbb{P}(A)}\\[0.4em]
&=\frac{0.0081}{0.00999}\fallingdotseq 0.8108
\end{aligned}
$$

</div>

</div>

<div id="example-115" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.26 <span lang="en">(Continued)</span></div>

<div lang="en" markdown="1">
Three machines $A$, $B$, and $C$ produce the same item and account for $20\%$, $30\%$, and $50\%$ of the total output, respectively. Of the items made by $A$, $B$, and $C$, $5\%$, $4\%$, and $2\%$ are defective, respectively. One item is drawn at random from the combined output and turns out to be defective. What is the probability that this item was made by machine $A$?
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

前一篇的 [Example 1.26](/teaching-topics/total-probability-bayes-rule/#example-111) 已由[全機率定理](/teaching-topics/total-probability-bayes-rule/#theorem-law-of-total-probability)求得

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

故由[貝氏定理](#theorem-bayes-rule)可知，所求為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(A\mid R)=\frac{\mathbb{P}(A\cap R)}{\mathbb{P}(R)}=\frac{\mathbb{P}(R\mid A)\,\mathbb{P}(A)}{\mathbb{P}(R)}=\frac{0.05\times 0.2}{0.032}=0.3125
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(A\mid R)&=\frac{\mathbb{P}(A\cap R)}{\mathbb{P}(R)}\\[0.4em]
&=\frac{\mathbb{P}(R\mid A)\,\mathbb{P}(A)}{\mathbb{P}(R)}\\[0.4em]
&=\frac{0.05\times 0.2}{0.032}=0.3125
\end{aligned}
$$

</div>

</div>

<div id="example-five-bowls" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.28 (Five Bowls)</div>

<div lang="en" markdown="1">
Five identical bowls are labeled $1$, $2$, $3$, $4$, and $5$. Bowl $i$ contains $i$ white and $5-i$ black balls, for $i=1,2,\ldots,5$. A bowl is randomly selected and a ball is randomly selected from the contents of the bowl.

(1) What is the probability that the ball selected is white?
{: .topic-paren-item}

(2) Given that the ball selected is white, what is the probability that bowl $1$ was selected?
{: .topic-paren-item}
</div>

令 $A_i$ 表示選到第 $i$ 個碗的事件，$W$ 表示選到白球的事件。由於每個碗都有 $5$ 顆球，其中第 $i$ 個碗有 $i$ 顆白球，故對 $i=1,2,\ldots,5$，皆有

$$
\mathbb{P}(A_i)=\frac{1}{5},\qquad\mathbb{P}(W\mid A_i)=\frac{i}{5}
$$

以下依序求解。

(1) 由於 $A_1,A_2,\ldots,A_5$ 為樣本空間的一組[分割](/teaching-topics/total-probability-bayes-rule/#definition-partition)，故由[全機率定理](/teaching-topics/total-probability-bayes-rule/#theorem-law-of-total-probability)可得
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(W)=\sum_{i=1}^{5}\mathbb{P}(W\mid A_i)\,\mathbb{P}(A_i)=\frac{1}{5}\sum_{i=1}^{5}\frac{i}{5}=\frac{3}{5}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(W)&=\sum_{i=1}^{5}\mathbb{P}(W\mid A_i)\,\mathbb{P}(A_i)\\[0.4em]
&=\frac{1}{5}\sum_{i=1}^{5}\frac{i}{5}=\frac{3}{5}
\end{aligned}
$$

</div>

(2) 由[貝氏定理](#theorem-bayes-rule)可得
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(A_1\mid W)=\frac{\mathbb{P}(W\mid A_1)\,\mathbb{P}(A_1)}{\mathbb{P}(W)}=\frac{(1/5)\times(1/5)}{3/5}=\frac{1}{15}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(A_1\mid W)&=\frac{\mathbb{P}(W\mid A_1)\,\mathbb{P}(A_1)}{\mathbb{P}(W)}\\[0.4em]
&=\frac{(1/5)\times(1/5)}{3/5}=\frac{1}{15}
\end{aligned}
$$

</div>

</div>

<div id="example-116" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.29 <span lang="en">(Missing Plane Problem)</span></div>

<div lang="en" markdown="1">
A plane is missing and is presumed to have equal probability of going down in any of three regions. If a plane is actually down in region $i$, let $1-p_i$ denote the probability that the plane will be found upon a search of the $i$-th region, $i=1,2,3$. What is the posterior probability that the plane is in region $3$, given that the search of region $1$ was unsuccessful?
</div>

令 $A_i$，$i=1,2,3$，表示飛機於區域 $i$ 失事的事件，$F_1$ 表示在區域 $1$ 發現該飛機的事件。則由題目敘述可知

$$
\mathbb{P}(A_1)=\mathbb{P}(A_2)=\mathbb{P}(A_3)=\frac{1}{3}
$$

且

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(F_1\mid A_1)=1-p_1,\qquad\mathbb{P}(F_1\mid A_2)=0,\qquad\mathbb{P}(F_1\mid A_3)=0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{P}(F_1\mid A_1)=1-p_1\\[0.4em]
\mathbb{P}(F_1\mid A_2)=0\\[0.4em]
\mathbb{P}(F_1\mid A_3)=0
\end{gathered}
$$

</div>

「搜尋區域 $1$ 而未發現飛機」即為 $F_1$ 的餘事件 $F_1^{\prime}$。由於在給定 $A_i$ 之下的條件機率[仍為一個機率測度](/teaching-topics/conditional-probability-information/#theorem-conditional-probability-measure)，故可用餘事件公式求得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(F_1^{\prime}\mid A_1)=1-(1-p_1)=p_1,\qquad\mathbb{P}(F_1^{\prime}\mid A_2)=\mathbb{P}(F_1^{\prime}\mid A_3)=1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{P}(F_1^{\prime}\mid A_1)=1-(1-p_1)=p_1\\[0.4em]
\mathbb{P}(F_1^{\prime}\mid A_2)=\mathbb{P}(F_1^{\prime}\mid A_3)=1
\end{gathered}
$$

</div>

故由[貝氏定理](#theorem-bayes-rule)可知，所求為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(A_3\mid F_1^{\prime})&=\frac{\mathbb{P}(F_1^{\prime}\mid A_3)\,\mathbb{P}(A_3)}{\sum_{i=1}^{3}\mathbb{P}(F_1^{\prime}\mid A_i)\,\mathbb{P}(A_i)}\\[0.4em]
&=\frac{1\times(1/3)}{p_1\times(1/3)+1\times(1/3)+1\times(1/3)}=\frac{1}{2+p_1}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(A_3\mid F_1^{\prime})\\[0.4em]
&=\frac{\mathbb{P}(F_1^{\prime}\mid A_3)\,\mathbb{P}(A_3)}{\sum_{i=1}^{3}\mathbb{P}(F_1^{\prime}\mid A_i)\,\mathbb{P}(A_i)}\\[0.4em]
&=\frac{1\times(1/3)}{(p_1+1+1)\times(1/3)}=\frac{1}{2+p_1}
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

[Example 1.29](#example-116) 為**失蹤飛機問題 <span lang="en">(missing plane problem)</span>**，是貝氏定理中一個著名的問題。其問題的關鍵在於，如果該飛機事實上並沒有在區域 $i$，則在該區域進行搜救是不可能會找到的；但即便飛機真的在<span class="text-nowrap">區域 $i$，</span>在該區域搜救也未必就會找到。由於這個原因，我們可以從某次搜救的結果得到一些資訊，針對「飛機可能在哪個區域」的機率進行調整，是一個事後機率的典型例子。
</div>

<div id="interlude-information-updates" class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 1.4</div>

在[失蹤飛機問題](#example-116)裡，搜尋區域 $1$ 而沒有找到飛機，究竟改變了什麼？飛機落在哪一個區域，早已是確定的事實，搜尋的結果並不改變飛機的真實位置，改變的是我們掌握的資訊，因而也改變了我們對三個區域的機率評估。

保險中的風險類別、醫療中的疾病狀態與搜尋問題中的真實位置，都是這種尚未被完全知道的狀態。貝氏定理提供的，正是新的觀察進來以後，重新分配這些狀態機率的規則。
</div>

## 敏感度、特異度與事後機率

貝氏定理在醫學檢驗上的一個常見應用，是由檢驗結果回頭評估受檢者是否罹病。令 $D$ 表示罹病之事件，$+$ 與 $-$ 分別表示檢驗結果呈陽性與呈陰性之事件。醫學上以<strong class="text-nowrap">敏感度 <span lang="en">(sensitivity)</span></strong> 表示 $\mathbb{P}(+\mid D)$，即真陽性率；以<strong class="text-nowrap">特異度 <span lang="en">(specificity)</span></strong> 表示 $\mathbb{P}(-\mid D^{\prime})$，即真陰性率。由餘事件可知，偽陽性率 $\mathbb{P}(+\mid D^{\prime})$ 為 $1$ 減去特異度，偽陰性率 $\mathbb{P}(-\mid D)$ 則為 $1$ 減去敏感度。

例如某疾病在一個族群中的盛行率為 $\mathbb{P}(D)=0.01$，某檢驗的敏感度為 $0.99$，特異度為 $0.95$，故偽陽性率為 $0.05$。若某人的檢驗結果呈陽性，則由[貝氏定理](#theorem-bayes-rule)可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(D\mid +)&=\frac{\mathbb{P}(+\mid D)\,\mathbb{P}(D)}{\mathbb{P}(+\mid D)\,\mathbb{P}(D)+\mathbb{P}(+\mid D^{\prime})\,\mathbb{P}(D^{\prime})}\\[0.4em]
&=\frac{0.99\times 0.01}{0.99\times 0.01+0.05\times 0.99}\fallingdotseq 0.1667
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(D\mid +)\\[0.4em]
&=\frac{\mathbb{P}(+\mid D)\,\mathbb{P}(D)}{\mathbb{P}(+\mid D)\,\mathbb{P}(D)+\mathbb{P}(+\mid D^{\prime})\,\mathbb{P}(D^{\prime})}\\[0.4em]
&=\frac{0.99\times 0.01}{0.99\times 0.01+0.05\times 0.99}\fallingdotseq 0.1667
\end{aligned}
$$

</div>

即使檢驗的敏感度高達 $0.99$，陽性結果之後真正罹病的機率仍然只有大約 $16.67\%$。其原因在於罹病者在族群中原本就很少；未罹病者雖然只有 $5\%$ 呈偽陽性，但乘上人數龐大的未罹病者以後，仍然構成陽性結果的主要來源。這說明事後機率同時取決於檢驗表現與事前機率，只看其中一項並不足以判斷。

讀者也可以打開 [Rapid Test Bayesian Updating Lab](/demos/bayesian-updating/)，自行調整盛行率、敏感度與特異度，觀察一次陽性或陰性的檢驗結果如何把事前機率更新為事後機率。

## 本篇小結

本篇由全機率定理的反向讀法出發，依序整理下列結果:

| 結果 | 內容 |
| :---: | :---: |
| [Theorem 1.17](#theorem-bayes-rule) | 貝氏定理與事前、事後機率的名稱 |
| [Example 1.25 <span lang="en">(Continued)</span>](#example-symptoms-and-diseases-continued) | 由症狀回頭計算感染某一疾病的機率 |
| [Example 1.26 <span lang="en">(Continued)</span>](#example-115) | 由不良品回頭計算來自某一機台的機率 |
| [Example 1.28](#example-five-bowls) | 五碗問題與白球來自某一碗的機率 |
| [Example 1.29](#example-116) | 失蹤飛機問題與搜救結果所帶來的資訊 |
| [直覺校準 1.4](#interlude-information-updates) | 搜尋結果改變的是資訊而非飛機的位置 |

條件機率、獨立、分割、全機率定理與貝氏定理合起來，構成第一章處理事件機率的主要工具。到目前為止，我們討論的對象仍然是事件。[下一章](/teaching-topics/random-variables-and-pmf/)將由[隨機變數](/teaching-topics/random-variables-and-pmf/#def-random-variable)與[機率質量函數](/teaching-topics/random-variables-and-pmf/#def-pmf)開始，把樣本空間中的結果對應到實數線上，使函數、[期望值](/teaching-topics/expectation/#def-expectation)與分配函數等工具能夠進入機率論。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Joseph K. Blitzstein and Jessica Hwang. 2019. *Introduction to Probability*. 2nd ed. Chapman and Hall/CRC.
- Morris H. DeGroot and Mark J. Schervish. 2012. *Probability and Statistics*. 4th ed. Pearson.
