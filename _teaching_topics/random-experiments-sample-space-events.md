---
title: "機率論的起點，隨機實驗、樣本空間與事件"
subtitle: "Random Experiments, Sample Spaces, and Events"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 1
topic: 1
order: 101
permalink: /teaching-topics/random-experiments-sample-space-events/
date: 2026-05-05
excerpt: "機率論不是從公式開始，而是從一個可重複、結果不確定、但所有可能結果可先描述的隨機實驗開始。樣本空間負責收納所有可能結果，事件則是我們真正想詢問的那些結果集合。"
---

機率論 (probability theory) 的第一步不是計算機率，而是先說清楚「我們正在觀察什麼」。如果連可能發生的結果都尚未被整理成一個清楚的集合，那麼後面的機率、公理、條件機率、獨立性與隨機變數都會失去共同語言。

此處先區分**樣本點**、**樣本空間**與**事件**。這三個概念會一路陪我們走到隨機變數、分配理論與極限分配。

## 從現象開始

在日常生活與自然界中，我們所能觀察到的現象 (phenomenon) 通常可先粗略分成兩類。

<div class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.1</div>

**確定現象 (deterministic phenomenon)** 是指在一定條件之下進行，就一定會發生，或者一定不會發生的現象。例如，在一大氣壓之下，將水加熱至 $100^\circ\mathrm{C}$ 便會沸騰。
</div>

<div class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.2</div>

**隨機現象 (random phenomenon)** 是指不能事先知道結果的現象。此種現象具有**不確定性 (uncertainty)**，因此不能被事前預知其結果；但它往往仍伴隨一定程度的規律，使研究者可以度量其發生的**可能性**，也就是**機率 (probability)**。
</div>

確定現象強調「在同樣條件下，結果可以被事前肯定」。隨機現象則強調「單次結果無法事前肯定，但大量重複時可能呈現規律」。機率論研究的正是後者。

## 隨機實驗

要把隨機現象變成數學對象，我們先將觀察過程稱為實驗 (experiment)。如果這個實驗在相同條件下重複操作時仍無法事先預知結果，但其所有可能結果可在實驗開始前描述，則稱為隨機實驗。

<div class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.3</div>

一個**隨機實驗 (random experiment)** 是指具有下列三個性質的實驗。

<ol class="topic-list-paren">
  <li>實驗所有可能的<strong>結果 (outcomes)</strong> 在實驗開始前即已知。</li>
  <li>實驗在未執行前，該實驗會產生何種結果無法事先預知。</li>
  <li>在相同的條件之下，該實驗可以被重複執行。</li>
</ol>
</div>

例如「投擲一顆骰子並觀察其出現的點數」是一個隨機實驗。投擲前我們知道結果必然是 $1,2,3,4,5,6$ 其中之一，但在真正投擲前，無法知道這一次會出現幾點；而且這個實驗可以在相同條件下反覆執行。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

「結果不確定」不代表「什麼都不知道」。隨機實驗要求所有可能結果在事前可被描述，這正是機率論能開始工作的原因。
</div>

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

這裡要特別注意 $\in$ 與 $\subset$ 的差別。$\omega \in S$ 表示「元素屬於集合」，而 $A \subset S$ 表示「集合包含於集合」。這個差異稍後在事件的定義中會立刻出現。

<div class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.1 (Sample Spaces)</div>

考慮下列三個隨機實驗。

<table class="topic-table--sample-spaces" style="width: 100%; max-width: 100%; table-layout: fixed; display: table; box-sizing: border-box;">
  <colgroup>
    <col class="topic-table__experiment" style="width: 68%;">
    <col class="topic-table__sample-space" style="width: 32%;">
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
      <td style="white-space: normal;">每期購買一張樂透彩券，直到中頭獎為止，觀察槓龜次數</td>
      <td>$S=\lbrace0,1,2,3,\ldots\rbrace$</td>
    </tr>
    <tr>
      <td style="white-space: normal;">觀察某一電腦零件之壽命</td>
      <td>$S=\lbrace\,t\mid t\geq 0\,\rbrace$</td>
    </tr>
  </tbody>
</table>
</div>

這三個例子分別代表有限、可數無限與不可數無限的樣本空間。從這裡開始，機率論已經不只是算骰子或硬幣；它需要一套能同時處理離散與連續情形的語言。

## 離散樣本空間與連續樣本空間

樣本空間可以依照其中元素個數的型態做分類。

<div class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.5</div>

**離散樣本空間 (discrete sample space)** 是指樣本空間中之元素個數為**有限 (finite)** 或**可數無限 (countably infinite)** 者。

**連續樣本空間 (continuous sample space)** 是指樣本空間中之元素個數為**不可數無限 (uncountably infinite)** 者。
</div>

可以把分類想成下面這張表。

| 樣本空間型態 | 元素個數 | 典型例子 |
| --- | --- | --- |
| 有限 | finite | 擲一顆骰子，$S=\lbrace1,2,3,4,5,6\rbrace$ |
| 可數無限 | countably infinite | 槓龜次數，$S=\lbrace0,1,2,\ldots\rbrace$ |
| 不可數無限 | uncountably infinite | 壽命時間，$S=[0,\infty)$ |

前兩者通常合稱為離散樣本空間；第三者則是連續樣本空間。連續樣本空間的出現，會讓我們開始面對一個細緻問題。在不可數多個可能結果之中，單一樣本點究竟扮演什麼角色？

<div id="thought-experiment-dart-zero-probability" class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 1.1</div>

想像你在酒吧丟飛鏢，且假設飛鏢的針尖沒有面積。第一次丟擲後，針尖落在靶上的某一個點，將這個點記作樣本點 $\omega_0$ 所在的位置。我將飛鏢拔起交還給你，請你第二次再丟到完全相同的點位。

直觀上，你也許會認為它不可能。但這句話需要更精細地理解。第一次丟擲已經證明 $\omega_0$ 是樣本空間中的一個可能結果；否則它不可能在第一次成為實際觀察到的樣本點。真正困難的是，在連續樣本空間中，若針尖可以落在靶上的不可數多個位置，則「第二次恰好落在指定點 $\omega_0$」這件事，直觀上應該分到多大的機率？

之後我們會正式看到，這類單點事件常常具有

$$
\mathbb{P}(\lbrace\omega_0\rbrace)=0
$$

因此，**機率為 $0$** 與**不可能發生**不是同一句話。前者是機率模型給出的數值；後者則是說該結果根本不在樣本空間之中。
</div>

## 事件與事件的發生

樣本空間收納所有可能結果，但我們真正關心的通常不是單一樣本點，而是某一群結果。例如擲骰子時，我們可能不只關心是否出現 $5$，也可能關心是否出現大於等於 $4$ 的點數。

<div class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.6</div>

**事件 (event)** 是隨機實驗之某些可能的結果所構成之集合，亦為樣本空間之子集合 (subset)。若某次實驗之結果屬於某一事件，則稱此事件**發生 (occur)**。

通常而言，我們以

$$
A\subset S
$$

表達 $A$ 為一事件，並以

$$
\omega\in A
$$

表示 $A$ 發生。
</div>

這裡出現了機率論最基本的三層結構。

| 物件 | 符號 | 意義 |
| --- | --- | --- |
| 樣本點 | $\omega$ | 一次實驗真正出現的結果 |
| 樣本空間 | $S$ 或 $\Omega$ | 所有可能結果所形成的集合 |
| 事件 | $A\subset S$ | 我們關心的一群可能結果 |

<div class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.2 (Events of a Die Roll)</div>

若投擲一顆骰子一次，令

$$
S=\lbrace1,2,3,4,5,6\rbrace
$$

令 $A$ 表示點數大於等於 $4$ 之事件，$B$ 表示點數小於等於 $3$ 之事件，$C$ 表示點數恰巧為 $5$ 之事件，則

$$
A=\lbrace4,5,6\rbrace,\qquad B=\lbrace1,2,3\rbrace,\qquad C=\lbrace5\rbrace
$$

若某次投擲出 $3$ 點，則

$$
3\notin A,\qquad 3\in B,\qquad 3\notin C
$$

因此 $B$ 事件發生，而 $A$ 與 $C$ 事件不發生。
</div>

## 有限樣本空間中的事件數量

若樣本空間只有有限個樣本點，則所有事件都可以直接列舉。這個事實雖然簡單，但它揭示了事件其實是「集合的選擇」。

<div class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Proposition 1.1 (Number of Events)</div>

若樣本空間 $S$ 具有 $n$ 個樣本點，則其可能事件共有 $2^n$ 個。
</div>

<div class="topic-proof" markdown="1">
**Proof.** 對於 $S$ 中的每一個樣本點，形成事件時都有兩種選擇。可以將它放入該事件，也可以不將它放入該事件。因為共有 $n$ 個樣本點，所以所有可能選擇共有

$$
2\times 2\times \cdots \times 2 = 2^n
$$

種。這些選擇正好對應到 $S$ 的所有子集合，因此事件共有 $2^n$ 個。 $\square$
</div>

在這 $2^n$ 個事件中，有兩個特殊事件一定存在。第一個是**確定事件 (certain event)**，也就是整個樣本空間 $S$ 本身。第二個是**虛無事件 (null event)**，也就是空集合 $\varnothing$ 這個事件。空集合 (empty set) 是一個沒有任何元素的集合。

## 測度觀點的第一個伏筆

在有限或可數樣本空間中，我們通常可以把所有子集合都視為事件。但在連續樣本空間中，這個想法會遇到困難，因為並不是每一個任意構造出的子集合都適合被賦予機率。

因此，更完整的機率模型由三個物件構成，分別是樣本空間、事件集合族，以及機率函數。若分別以 $S$、$\mathcal{F}$ 與 $\mathbb{P}$ 記之，這三個物件合在一起，便逐步導向機率空間

$$
(S,\mathcal{F},\mathbb{P})
$$

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

此處先把事件理解為樣本空間的子集合，以便建立第一層直覺。進入測度較完整的版本後，我們會把「事件」修正為「屬於某個 $\sigma$-域 ($\sigma$-field) 的集合」。換句話說，事件仍然是集合，但不是所有集合都必然能成為事件。下一篇將更仔細說明[事件集合族與 $\sigma$-域](/teaching-topics/event-families-sigma-fields/)的角色。
</div>

## 本篇小結

本篇建立的是機率論的第一層語言。

| 問題 | 對應物件 |
| --- | --- |
| 我們做的是什麼觀察？ | 隨機實驗 |
| 所有可能結果有哪些？ | 樣本空間 |
| 單次實驗真正出現什麼？ | 樣本點 |
| 我們關心哪一群結果？ | 事件 |
| 某事件是否發生？ | 檢查實際結果是否屬於該事件 |

等到這些物件都被定義清楚，下一篇將先處理「哪些事件可以被賦予機率」這個問題，也就是[事件集合族與 $\sigma$-域](/teaching-topics/event-families-sigma-fields/)。待事件清單被指定後，才會進一步追問如何把一個介於 $0$ 與 $1$ 之間的數值合理地指定給事件。

## 參考文獻與延伸閱讀

- Sheldon M. Ross, *A First Course in Probability*, chapters on sample spaces, events, and probability axioms.
- Joseph K. Blitzstein and Jessica Hwang, *Introduction to Probability*, chapters on probability spaces and counting.
- Patrick Billingsley, *Probability and Measure*, sections on probability spaces and measurable events.
- Emanuel Parzen, *Modern Probability Theory and Its Applications*, John Wiley & Sons, 1960, overview of probability foundations.
- Michael Woodroofe, *Probability with Applications*, McGraw-Hill, 1975, early chapters on probability spaces and events.
- B. V. Gnedenko, *The Theory of Probability*, English translation, Mir Publishers, 1975.
- R. T. Cox, “Probability, Frequency and Reasonable Expectation”, *American Journal of Physics*, 14(1), 1–13, 1946. [doi:10.1119/1.1990764](https://doi.org/10.1119/1.1990764).
