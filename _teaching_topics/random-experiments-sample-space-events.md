---
title: "隨機實驗、樣本空間與事件"
subtitle: "Random Experiments, Sample Spaces, and Events"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 1
topic: 1
order: 101
permalink: /teaching-topics/random-experiments-sample-space-events/
date: 2026-05-05
published: true
excerpt: "機率論先由隨機實驗開始，整理實驗所有可能的結果，並以樣本空間、樣本點與事件建立後續機率模型所需的基本定義。"
---

在機率論中，我們先要說明正在觀察的現象、實驗所有可能的結果，以及哪些結果構成我們關心的事件。有了這些基本定義，後續才能為事件指定機率，並建立條件機率、獨立性與隨機變數等內容。

本篇依序介紹隨機實驗、樣本空間、樣本點與事件，並說明這些定義之間的關係。

## 確定現象與隨機現象

在日常生活與自然界中，我們所能觀察到的現象 <span lang="en">(phenomenon)</span> 通常可先粗略分成兩類。

<div class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.1</div>

**確定現象 <span lang="en">(deterministic phenomenon)</span>** 是指在一定條件之下進行，就一定會發生，或者一定不會發生的現象。例如，在一大氣壓之下，將水加熱至 $100^\circ\mathrm{C}$ 便會沸騰。過去我們所學過的諸多自然定律都符合這個現象。
</div>

<div class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.2</div>

**隨機現象 <span lang="en">(random phenomenon)</span>** 是指不能事先知道結果的現象。例如賭博時投擲一顆骰子，並不能夠事前就知道出現的點數，即可視為一種隨機現象。此種現象具有**不確定性 <span lang="en">(uncertainty)</span>**，因此不能被事前預知其結果；但它往往仍伴隨一定程度的規律，使研究者可以度量其發生的**可能性**，也就是**機率 <span lang="en">(probability)</span>**。整個**機率論 <span lang="en">(probability theory)</span>** 就是在探討這樣的規律性。
</div>

確定現象強調「在同樣條件下，結果可以被事前肯定」。隨機現象則強調「單次結果無法事前肯定，但大量重複時可能呈現規律」。機率論研究的正是後者。

## 隨機實驗

要把隨機現象轉成數學上可以討論的問題，我們先將觀察的過程稱為實驗 <span lang="en">(experiment)</span>。如果這個實驗在相同條件下重複操作時，仍無法事先預知結果，則稱為隨機實驗。

<div class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.3</div>

一個**隨機實驗 <span lang="en">(random experiment)</span>** 是指具有下列三個性質的實驗。

<ol class="topic-list-paren">
  <li>實驗所有可能的<strong>結果 <span lang="en">(outcomes)</span></strong> 在實驗開始前即已知。</li>
  <li>實驗在未執行前，該實驗會產生何種結果無法事先預知。</li>
  <li>在相同的條件之下，該實驗可以被重複執行。</li>
</ol>
</div>

例如「投擲一顆骰子並觀察其出現的點數」是一個隨機實驗。投擲前我們知道結果必然是 $1,2,3,4,5,6$ 其中之一，但在真正投擲前，無法知道這一次會出現幾點；而且這個實驗可以在相同條件下反覆執行。

## 樣本空間與樣本點

一旦隨機實驗被指定，下一步就是把所有可能結果收成一個集合。

<div class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.4</div>

隨機實驗之所有可能的結果所形成的集合稱作**樣本空間 (sample space)**，通常以英文字母 $S$ 或希臘字母 $\Omega$ 表示。樣本空間中的元素被稱作**樣本點 (sample point)**，通常以希臘字母 $\omega$ 表示。
</div>

在符號上，若 $\omega$ 是某個可能結果，而 $S$ 是所有可能結果構成的集合，則我們寫成

$$
\omega \in S
$$

這是**集合論 (set theory)** 的表示法，表示 $\omega$ 為 $S$ 中的**元素 <span lang="en">(element)</span>**。這裡要特別注意 $\in$ 與 $\subseteq$ 的差別: $\omega\in S$ 表示元素 $\omega$ 屬於**集合 (set)** <span class="text-nowrap">$S$，</span>是元素對集合的關係；而 $A\subseteq S$ 表示集合 $A$ 是 $S$ 的子集合，是集合對集合的關係。這個差異稍後在事件的定義中會立刻出現，集合的**算子 <span lang="en">(operator)</span>** 也會在後續有較完整的介紹。

<div id="example-sample-spaces" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.1 (Sample Spaces)</div>

考慮下列三個隨機實驗。

<table class="topic-table--sample-spaces" style="width: 100%; max-width: 100%; table-layout: fixed; box-sizing: border-box;">
  <colgroup>
    <col class="topic-table__experiment">
    <col class="topic-table__sample-space">
  </colgroup>
  <thead>
    <tr>
      <th style="white-space: normal;">隨機實驗</th>
      <th>樣本空間</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="white-space: normal;">投擲一硬幣一次，觀察其正反面</td>
      <td>$S=\lbrace\mathrm{H},\mathrm{T}\rbrace$</td>
    </tr>
    <tr>
      <td style="white-space: normal;">每期購買一張樂透彩券，觀察中頭獎以前的槓龜次數</td>
      <td>$S=\lbrace0,1,2,\ldots\rbrace$</td>
    </tr>
    <tr>
      <td style="white-space: normal;">觀察某一電腦零件之壽命</td>
      <td>$S=\lbrace\,t\mid t\geqslant 0\,\rbrace$</td>
    </tr>
  </tbody>
</table>
</div>

## 離散樣本空間與連續樣本空間

上述的例子裡可以發現，樣本空間的型態很多樣，因此可對樣本空間分類。

若將隨機實驗與微積分中的**函數 <span lang="en">(function)</span>** 做聯想，則可以將樣本空間想像成該函數的**對應域 <span lang="en">(codomain)</span>**；依照對應域的不同，函數能被分成**實值函數 <span lang="en">(real-valued function)</span>** 等不同函數。同理，我們也能夠以此為樣本空間進行分類，並將其分為二大類。

<div class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.5</div>

**離散樣本空間 <span lang="en">(discrete sample space)</span>** 是指樣本空間中之元素個數為**有限 (finite)** 或**可數無限 <span lang="en">(countably infinite)</span>** 者。

**連續樣本空間 <span lang="en">(continuous sample space)</span>** 是指樣本空間中之元素個數為**不可數無限 <span lang="en">(uncountably infinite)</span>** 者。
</div>

經過上述的分類以後，回頭來看 [Example 1.1](#example-sample-spaces)，可以發現該題中的三個答案分別對應到此二大類下的三個小類別: 有限樣本空間、可數無限樣本空間及不可數無限樣本空間。

一個無限集合若能與正整數集合 $\mathbb{N}$ 建立一一對應，便稱為可數無限集合。因此，有限集合與可數無限集合都歸入離散樣本空間，不可數無限集合則歸入連續樣本空間。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

前段所說的一一對應，嚴謹的說法如下。一集合為可數即代表其元素個數為有限，或是無限但能與正整數集合 $\mathbb{N}$ **對射 <span lang="en">(bijection)</span>** 的集合；對射是指此對應同時為一對一 (one-to-one) 且映成 (onto)。換言之，該集合的**基數 <span lang="en">(cardinality)</span>** 小於或者等於正整數集合的基數，我們稱此集合為**可數 <span lang="en">(countable)</span>**。

在樣本空間的分類上，不可數無限所對應的正是連續的概念；連續與「極限」的概念密不可分，可視為**微積分 <span lang="en">(calculus)</span>** 之起源。
</div>

可以把分類想成下面這張表。

| 樣本空間型態 | 元素個數 | 典型例子 |
| :---: | :---: | :---: |
| 有限 | finite | 擲一顆骰子，$S=\lbrace1,2,3,4,5,6\rbrace$ |
| 可數無限 | countably infinite | 槓龜次數，$S=\lbrace0,1,2,\ldots\rbrace$ |
| 不可數無限 | uncountably infinite | 壽命時間，$S=[0,\infty)$ |
{: .topic-table--sample-space-types}

前兩者合稱為離散樣本空間；第三者則是連續樣本空間。表中的 $S=[0,\infty)$ 與 [Example 1.1](#example-sample-spaces) 的 $S=\lbrace\,t\mid t\geqslant 0\,\rbrace$ 是同一個集合的兩種寫法。

部分教科書將樣本空間分類成可數與不可數二類，此一分類事實上與上述之離散與連續的二分法相同，其理由在於可數的集合必定也是一個離散的集合，故上述的離散樣本空間事實上可被稱為可數樣本空間，而連續樣本空間則對應到不可數樣本空間。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

本系列第二章談到隨機變數時，會依其值域與機率的表示方式分為離散型與連續型隨機變數。為了與後續章節一致，本系列在樣本空間的分類上使用離散與連續，而不使用可數與不可數。
</div>

## 事件與事件的發生

樣本空間列出所有可能結果，但我們真正關心的通常是一組結果，而非單一樣本點。例如擲骰子時，關心的可以是是否出現 $5$，也可以是是否出現大於等於 $4$ 的點數。

<div class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.6</div>

**事件 (event)** 是隨機實驗之某些可能結果所構成的集合，也是樣本空間的子集合。若某次實驗的結果屬於某一事件，則稱此事件**發生 (occur)**。

因此，以 $A\subseteq S$ 表示 $A$ 是一個事件；若實驗結果為 $\omega$，則以 $\omega\in A$ 表示事件 $A$ 發生。
</div>

這裡出現了機率論最基本的三層結構。

| 名稱 | 符號 | 意義 |
| :---: | :---: | :---: |
| 樣本點 | $\omega$ | 一次實驗真正出現的結果 |
| 樣本空間 | $S$ 或 $\Omega$ | 所有可能結果所形成的集合 |
| 事件 | $A\subseteq S$ | 由樣本點構成的集合 |
{: .topic-table--basic-objects}

<div class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.2 (Events of a Die Roll)</div>

若投擲一顆骰子一次，則樣本空間為

$$
S=\lbrace1,2,3,4,5,6\rbrace
$$

令 $A$ 表示點數大於等於 $4$ 之事件，$B$ 表示點數小於等於 $3$ 之事件，$C$ 表示點數恰巧為 $5$ 之事件，則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
A=\lbrace4,5,6\rbrace,\qquad B=\lbrace1,2,3\rbrace,\qquad C=\lbrace5\rbrace
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
A=\lbrace4,5,6\rbrace\\[0.4em]
B=\lbrace1,2,3\rbrace\\[0.4em]
C=\lbrace5\rbrace
\end{gathered}
$$

</div>

若某次投擲出 $3$ 點，則

$$
3\notin A,\qquad 3\in B,\qquad 3\notin C
$$

因此 $B$ 事件發生，而 $A$ 與 $C$ 事件不發生。
</div>

## 有限樣本空間中的事件數量

若樣本空間 $S$ 具有 $n$ 個樣本點，則每個事件都是 $S$ 的一個子集合。對每個樣本點而言，形成子集合時都有「放入」與「不放入」兩種選擇，因此所有可能的事件共有 $2^n$ 個。

這些子集合所形成的集合稱為**冪集合 (power set)**，記作

$$
2^S=\lbrace\,A\mid A\subseteq S\,\rbrace
$$

事實上，對任意**非空集合 (non-empty set)** 而言，「所有元素都出現」與「所有元素都不出現」所對應的兩個子集合，都是該集合的**顯然子集 <span lang="en">(trivial subset)</span>**；對於一樣本空間而言，此二集合皆為事件。

在這 $2^n$ 個事件中，$S$ 稱為**確定事件 <span lang="en">(certain event)</span>**，$\varnothing$ 稱為**虛無事件 (null event)**。空集合 (empty set) 是沒有任何元素的集合。

## 本篇小結

本篇建立的是機率論的入門基礎，為讀者釐清每一個定義在機率論的角色。

| 問題 | 對應角色 |
| :---: | :---: |
| 我們做的是什麼觀察？ | 隨機實驗 |
| 所有可能結果有哪些？ | 樣本空間 |
| 單次實驗真正出現什麼？ | 樣本點 |
| 我們關心哪一群結果？ | 事件 |
| 某事件是否發生？ | 檢查實際結果是否屬於該事件 |
{: .topic-table--chapter-summary}

等到這些定義都被釐清，[下一篇](/teaching-topics/event-set-operations/)將先介紹事件的聯集、交集、差集、餘集、集合序列與互斥，建立後續機率運算所需的集合工具；之後再討論如何把介於 $0$ 與 $1$ 之間的數值指定給事件。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Joseph K. Blitzstein and Jessica Hwang. 2019. *Introduction to Probability*. 2nd ed. Chapman and Hall/CRC.
- Emanuel Parzen. 1960. *Modern Probability Theory and Its Applications*. Wiley.
