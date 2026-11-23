---
title: "域、σ-域與機率空間"
subtitle: "Fields, Sigma-Fields, and Probability Spaces"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 1
topic: 4
order: 104
permalink: /lecture-notes/event-families-sigma-fields/
date: 2026-05-05
published: true
excerpt: "機率公理要建立在哪裡？本篇依序介紹域、$\\sigma$-域、可測空間與機率空間，說明哪些事件可以賦予機率，以及機率測度應滿足的三大公理。"
---

[上一篇](/lecture-notes/probability-assignment-classical-geometric/)說明了古典機率、幾何機率、客觀機率與主觀機率等指定方式，也看到這些定義各有其對應的問題，因此無法作為一個嚴謹的數學學科而有較深入的發展。俄羅斯數學家柯爾莫哥洛夫 (Andrey N. Kolmogorov) 便由此提出**機率公理 <span lang="en">(probability axioms)</span>** 作為機率論的基石，他曾指出，「機率論作為數學學科，可以、而且應該，從公理開始建設，和幾何、代數的路一樣。」

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

數學中的**公理 (axiom)** 是推導該領域所有**定理 <span lang="en">(theorem)</span>** 的起點，本身不加證明而直接採納為前提。機率論中的各項定理追本溯源皆奠基於柯爾莫哥洛夫的三大機率公理；正因這套嚴謹的公理化架構，機率論得以確立為現代數學的主要分支之一。
</div>

機率公理規範了機率必須滿足的基本性質；但在寫下公理之前，須先釐清公理建立在何處，即**機率空間 <span lang="en">(probability space)</span>**。為此，我們先從幾類特殊的事件集合族談起，界定哪些集合能夠賦予機率。

## 域

<div id="definition-field" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.15</div>

令 $S$ 為一非空集合，$\mathcal{F}$ 為一個由 $S$ 的部分子集所構成之集合，且滿足以下三點:

<ol class="topic-list-paren">
  <li>
  $$
  \varnothing\in\mathcal{F}\quad(\text{或 }S\in\mathcal{F})
  $$</li>
  <li>若 $A\subseteq S$ 且 $A\in\mathcal{F}$，則
  $$
  A^{\prime}\in\mathcal{F}
  $$</li>
  <li>若 $A_1,\ldots,A_n\subseteq S$ 且 $A_1,\ldots,A_n\in\mathcal{F}$，則
  $$
  \bigcup_{i=1}^{n}A_i\in\mathcal{F}
  $$</li>
</ol>

則稱 $\mathcal{F}$ 為佈於 $S$ 上的**域 (field)**，或譯為**體**，亦稱**代數 <span lang="en">(algebra)</span>**。
</div>

[Definition 1.15](#definition-field) 在定義機率公理方面，有幾個意義與需要注意的事情:

(1) 如[隨機實驗、樣本空間與事件](/lecture-notes/random-experiments-sample-space-events/#事件與事件的發生)所述，事件即樣本空間的子集合，因此域是由一族事件所構成的集合。在建構機率公理之前，必須先界定哪些事件可以衡量機率，並規範這些事件彼此的運算關係，這正是定義域的目的。
{: .topic-paren-item}

(2) 通常而言，$S$ 就是樣本空間，故條件 (2) 中的 $A^{\prime}$ 不需要特別定義；否則 $A^{\prime}=S-A$。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

條件 (2) 要求域對餘集運算具有封閉性。就事件而言，若我們關心事件 $A$ **是否發生** (即 <span class="text-nowrap">$A\in\mathcal{F}$)，</span>自然也需要考慮 $A$ **不發生**的情形，故其餘事件 $A^{\prime}$ 亦須屬於 <span class="text-nowrap">$\mathcal{F}$。</span>
</div>

(3) 在條件 (2) 成立下，條件 (1) 中的 $\varnothing\in\mathcal{F}$ 與 $S\in\mathcal{F}$ 其實等價，且由條件 (1) 可知 $\mathcal{F}$ 顯然非空。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

條件 (1) 雖直接保證 $\mathcal{F}$ 非空，但定義上只需假設 $\mathcal{F}$ 非空即可推出條件 (1)。任取 $A\in\mathcal{F}$ 後，由條件 (2) 知 $A^{\prime}\in\mathcal{F}$ 成立，再結合條件 (3) 可得

$$
A\cup A^{\prime}=S\in\mathcal{F}
$$

進而再由條件 (2) 可得

$$
\varnothing\in\mathcal{F}
$$

</div>

(4) 對一個非空集合 $S$ 而言，滿足 [Definition 1.15](#definition-field) 的 $\mathcal{F}$ 可能不是唯一的。其中最小與最大的選擇分別為
{: .topic-paren-item}

$$
\begin{gathered}
\mathcal{F}=\lbrace\varnothing,S\rbrace\\[0.4em]
\mathcal{F}=2^{S}=\lbrace\,A\mid A\subseteq S\,\rbrace
\end{gathered}
$$

如前文[有限樣本空間中的事件數量](/lecture-notes/random-experiments-sample-space-events/#有限樣本空間中的事件數量)所述，$2^{S}$ 代表 $S$ 的**冪集合 (power set)**，即由 $S$ 的所有可能子集所構成的集合。
{: .topic-paren-cont}

(5) 由條件 (2)、(3) 再搭配[狄摩根律](/lecture-notes/event-set-operations/#狄摩根律)，可知域對有限交集也具有封閉性。當 $A_1,\ldots,A_n\in\mathcal{F}$ 時，皆有 $A_1^{\prime},\ldots,A_n^{\prime}\in\mathcal{F}$ 成立，故
{: .topic-paren-item}

$$
\bigcup_{i=1}^{n}A_i^{\prime}\in\mathcal{F}\qquad\therefore\, \left(\bigcup_{i=1}^{n}A_i^{\prime}\right)^{\prime}=\bigcap_{i=1}^{n}A_i\in\mathcal{F}
$$

換言之，若 $A_1,\ldots,A_n\in\mathcal{F}$，則
{: .topic-paren-cont}

$$
\bigcap_{i=1}^{n}A_i\in\mathcal{F}
$$

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

條件 (3) 與第 (5) 點共同保證域對有限聯集與有限交集皆具封閉性。以兩個事件為例，若我們關心 $A$ 與 $B$ 是否發生，往往也會關心「$A$ 或 $B$」以及「$A$ 且 $B$」是否發生；因此當 $A,B\in\mathcal{F}$ 時，自然要求

$$
A\cup B\in\mathcal{F}\quad\text{且}\quad A\cap B\in\mathcal{F}
$$

</div>

(6) 若 $S$ 為有限樣本空間，佈於其上最大的域 $\mathcal{F}=2^{S}$ 亦為有限集合，此時僅考慮有限個集合的運算已足以應付所有情況。然而如[離散樣本空間與連續樣本空間](/lecture-notes/random-experiments-sample-space-events/#離散樣本空間與連續樣本空間)所示，樣本空間可能是無窮集合；此時僅考慮有限聯集與有限交集往往不足以包含所需的事件，故須將條件 (3) 推廣至可數聯集，引出下列定義。
{: .topic-paren-item}

## $\sigma$-域

<div id="definition-sigma-field" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.16</div>

令 $S$ 為一非空集合，$\mathcal{F}$ 為一個由 $S$ 的部分子集所構成的集合，且滿足以下三點:

<ol class="topic-list-paren">
  <li>
  $$
  \varnothing\in\mathcal{F}\quad(\text{或 }S\in\mathcal{F})
  $$</li>
  <li>若 $A\subseteq S$ 且 $A\in\mathcal{F}$，則
  $$
  A^{\prime}\in\mathcal{F}
  $$</li>
  <li>若 $A_1,A_2,\ldots\subseteq S$ 且 $A_1,A_2,\ldots\in\mathcal{F}$ 皆成立，則
  $$
  \bigcup_{i=1}^{\infty}A_i\in\mathcal{F}
  $$</li>
</ol>

則稱 $\mathcal{F}$ 為佈於 $S$ 上的一個 **$\sigma$-域 ($\sigma$-field)**，或譯為 **$\sigma$-體**，亦稱為 **$\sigma$-代數 <span lang="en">($\sigma$-algebra)</span>**。
</div>

[Definition 1.16](#definition-sigma-field) 可延伸出底下幾點:

(1) $\sigma$-域可視為域的強化版本，且**一個 $\sigma$-域必定也是一個域**；驗證時只需在條件 (3) 中對所有 $k>n$ 令 <span class="text-nowrap">$A_k=\varnothing$，</span>即可由可數聯集的封閉性退化得有限聯集的封閉性。
{: .topic-paren-item}

(2) 前面說過，對一個樣本空間 $S$ 而言，最小的域是 $\mathcal{F}=\lbrace\varnothing,S\rbrace$，而最大的域是 <span class="text-nowrap">$\mathcal{F}=2^{S}$，</span>這一點在 $\sigma$-域也同樣成立。
{: .topic-paren-item}

<div id="example-die-sigma-fields" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.9 (Sigma-Fields for a Die Roll)</div>

考慮投擲一六面骰一次的隨機實驗，試回答以下問題:

(1) 列出樣本空間 $S$、出現 $5$ 點之事件 $A$ 與出現偶數點之事件 $B$。
{: .topic-paren-item}

(2) 列出佈於 $S$ 之上，包含 $A$ 之兩個不同的 $\sigma$-域 $\mathcal{F}_1$ 與 $\mathcal{F}_2$。
{: .topic-paren-item}

(3) 列出佈於 $S$ 之上，包含 $A$ 與 $B$ 之最小 $\sigma$-域 $\mathcal{F}_3$。
{: .topic-paren-item}

以下依序求解。

**(1)** 由題意可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
S=\lbrace1,2,3,4,5,6\rbrace,\qquad A=\lbrace5\rbrace,\qquad B=\lbrace2,4,6\rbrace
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
S=\lbrace1,2,3,4,5,6\rbrace,\\[0.4em]
A=\lbrace5\rbrace,\qquad B=\lbrace2,4,6\rbrace
\end{gathered}
$$

</div>

**(2)** 依 $\sigma$-域之定義，包含 $A=\lbrace5\rbrace$ 的 $\sigma$-域必亦包含 $A^{\prime}=\lbrace1,2,3,4,6\rbrace$，則可令

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathcal{F}_1&=\lbrace\varnothing,S,A,A^{\prime}\rbrace\\[0.4em]
&=\big\lbrace\lbrace\,\rbrace,\lbrace1,2,3,4,5,6\rbrace,\lbrace5\rbrace,\lbrace1,2,3,4,6\rbrace\big\rbrace
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathcal{F}_1&=\lbrace\varnothing,S,A,A^{\prime}\rbrace\\[0.4em]
&=\big\lbrace\lbrace\,\rbrace,\lbrace1,2,3,4,5,6\rbrace,\\[0.4em]
&\qquad\lbrace5\rbrace,\lbrace1,2,3,4,6\rbrace\big\rbrace
\end{aligned}
$$

</div>

除了 $A$ 之外，也可以把 $B$ 一併放入。考慮 $A,B\in\mathcal{F}_2$，則 <span class="text-nowrap">$A\cup B\in\mathcal{F}_2$，</span>進而 $A^{\prime}\cap B^{\prime}\in\mathcal{F}_2$，故可令

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathcal{F}_2&=\lbrace\varnothing,S,A,A^{\prime},B,B^{\prime},A\cup B,A^{\prime}\cap B^{\prime}\rbrace\\[0.4em]
&=\big\lbrace\lbrace\,\rbrace,\lbrace1,2,3,4,5,6\rbrace,\lbrace5\rbrace,\lbrace1,2,3,4,6\rbrace,\\[0.4em]
&\qquad\lbrace2,4,6\rbrace,\lbrace1,3,5\rbrace,\lbrace2,4,5,6\rbrace,\lbrace1,3\rbrace\big\rbrace
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathcal{F}_2&=\lbrace\varnothing,S,A,A^{\prime},B,B^{\prime},\\[0.4em]
&\qquad A\cup B,A^{\prime}\cap B^{\prime}\rbrace\\[0.4em]
&=\big\lbrace\lbrace\,\rbrace,\lbrace1,2,3,4,5,6\rbrace,\\[0.4em]
&\qquad\lbrace5\rbrace,\lbrace1,2,3,4,6\rbrace,\\[0.4em]
&\qquad\lbrace2,4,6\rbrace,\lbrace1,3,5\rbrace,\\[0.4em]
&\qquad\lbrace2,4,5,6\rbrace,\lbrace1,3\rbrace\big\rbrace
\end{aligned}
$$

</div>

**(3)** 所求為

$$
\mathcal{F}_3=\mathcal{F}_2
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

建構包含特定事件的最小 $\sigma$-域時，除納入指定事件本身外，亦須將其餘集與彼此間衍生的聯集、交集一併補齊以滿足封閉性；但不得額外加入無關的事件，方能維持「最小」的性質。
</div>

## 實數線上的波雷爾 $\sigma$-域 {#實數線上的-borel-sigma-域}

在眾多的樣本空間中，我們可能會遇到不可數無窮的樣本空間，例如實數空間 $\mathbb{R}$ 上，樣本空間的子集合往往是一段範圍或區間。值得注意的是，由樣本空間 $S$ 中所有**開集合 (open sets)** 所生成的 $\sigma$-域，也就是包含所有開集合的最小 $\sigma$-域，稱作**波雷爾 $\sigma$-域 (Borel $\sigma$-field)**。

實數線 $\mathbb{R}$ 上的波雷爾 $\sigma$-域記作 $\mathcal{B}(\mathbb{R})$，它也可以由所有開區間，或由所有半直線 $(-\infty,x]$ 生成。開區間、閉區間、半開區間、可數集合，以及它們經由可數聯集與可數交集形成的集合，都包含在其中。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

波雷爾 $\sigma$-域得名自法國數學家埃米爾・波雷爾 (Émile Borel, 1871-1956)，使實數線上各類區間皆能納入機率測度的定義域。波雷爾亦曾介紹著名的**無限猴子定理 <span lang="en">(infinite monkey theorem)</span>**，其背後的極限法則後來成為**高等機率論 <span lang="en">(advanced probability theory)</span>** 的重要結果。
</div>

## 可測空間

如同前面所說，$\sigma$-域的建構是為了刻畫「在樣本空間 $S$ 中可以被衡量機率的事件」。在建構機率公理的路上，$S$ 與佈於其上的 $\sigma$-域 $\mathcal{F}$ 共同構築了一個舉足輕重的空間，如下定義。

<div id="definition-measurable-space" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.17</div>

令 $S$ 為一個非空集合，而 $\mathcal{F}$ 為佈於其上的 $\sigma$-域，則**序對 <span lang="en">(ordered pair)</span>** $(S,\mathcal{F})$ 構成一個**可測空間 <span lang="en">(measurable space)</span>**，其中 $A\in\mathcal{F}$ 稱為**可測集合 <span lang="en">(measurable sets)</span>**。
</div>

[Definition 1.17](#definition-measurable-space) 的直觀意義如下:

(1) 可測空間 $(S,\mathcal{F})$ 明確指出隨機實驗的所有可能結果 (即 $S$)，以及在這其中，哪些事件是可以被測度機率的 (即 $\mathcal{F}$)，因此才共同構築成一個「可被測度機率的空間」。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

樣本空間 $S$ 雖包含隨機實驗的所有樣本點，但由樣本點構成的子集合未必每一個都有賦予機率的必要。例如某些明顯不會發生的集合，既可納入 $\mathcal{F}$ 並賦予機率 <span class="text-nowrap">$0$，</span>亦可一開始便排除在可測集合之外；因此佈於同一樣本空間 $S$ 上的 $\sigma$-域並非唯一。
</div>

(2) 前述定義中的可測集合，在機率論中就是我們所熟知的**隨機事件 (random events)**，亦即可以被測度機率的事件。
{: .topic-paren-item}

## 機率空間

至此，我們終於知道哪裡可以測度機率，也終於可以開始定義機率的**測度 <span lang="en">(measure)</span>** 應該符合怎樣的特性，這就是所謂機率的公理。

<div id="definition-probability-space" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.18</div>

令 $S$ 為某隨機實驗的樣本空間，$\mathcal{F}$ 為佈於 $S$ 上的 $\sigma$-域，函數 $\mathbb{P}(\cdot):\mathcal{F}\longrightarrow\mathbb{R}$ 為定義於 $\mathcal{F}$ 上的實值函數，且滿足以下三點:

<ol class="topic-list-paren">
  <li><strong>Axiom 1 (非負性, <span lang="en">non-negativity</span>)</strong>: 對任意 $A\in\mathcal{F}$，皆有
  $$
  \mathbb{P}(A)\geqslant 0
  $$</li>
  <li><strong>Axiom 2 (歸一性, <span lang="en">normalization</span>)</strong>: 樣本空間本身滿足
  $$
  \mathbb{P}(S)=1
  $$</li>
  <li><strong>Axiom 3 (可數可加性, <span lang="en">countable additivity</span>)</strong>: 若 $A_1,A_2,\ldots\in\mathcal{F}$，且 $A_i\cap A_j=\varnothing$ 對所有 $i\neq j$ 成立，則
  $$
  \mathbb{P}\left(\bigcup_{i=1}^{\infty}A_i\right)=\sum_{i=1}^{\infty}\mathbb{P}(A_i)
  $$</li>
</ol>

此時我們稱函數 $\mathbb{P}(\cdot)$ 為**機率測度 <span lang="en">(probability measure)</span>**，且三元組 $(S,\mathcal{F},\mathbb{P})$ 構成一個**機率空間**。
</div>

針對 [Definition 1.18](#definition-probability-space)，我們補充幾點:

(1) 定義中提到的三點性質，正是由柯爾莫哥洛夫所提出的**柯爾莫哥洛夫機率三大公理 <span lang="en">(Kolmogorov axioms)</span>**。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

柯爾莫哥洛夫三大公理**並未指定機率的計算公式，而是規範機率測度必須滿足的基本性質**。這與古典機率等明定計算式的作法截然不同，卻足以建立整套機率論。
</div>

(2) 機率測度是比較正式的機率論與測度論用詞，其意義是衡量出「事件發生的可能性的大小」，一如數量、長度、面積等等的度量值一樣。但在一般的統計學與數理統計學中，通常會稱其為**機率集合函數 <span lang="en">(probability set function)</span>**，或直接簡稱為**機率函數 <span lang="en">(probability function)</span>**。後續各篇在指稱 $\mathbb{P}(\cdot)$ 時，將以機率函數為主，但其他用詞亦可能混用。
{: .topic-paren-item #term-probability-function}

(3) 三元組 $(S,\mathcal{F},\mathbb{P})$ 除了被稱作機率空間外，又稱**機率三要素 <span lang="en">(probability triple)</span>**，在建構機率及其衍生性質的過程中，具有非常重要的地位。爾後在探討由機率公理所衍生出的各種性質前，我們只需要說明 $(S,\mathcal{F},\mathbb{P})$ 為一個機率空間，讀者便會明白 $S$ 是樣本空間、$\mathcal{F}$ 是佈於 $S$ 上的一個 $\sigma$-域，而 $\mathbb{P}(\cdot)$ 是定義在 $\mathcal{F}$ 上的機率函數。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

回顧建構機率模型的脈絡，由隨機實驗出發，先以樣本空間 $S$ 收集所有可能結果，再以 $\sigma$-域 $\mathcal{F}$ 界定可衡量機率的事件範圍，最後以機率函數 $\mathbb{P}(\cdot)$ 賦予各事件機率值。三元組 $(S,\mathcal{F},\mathbb{P})$ 完整串聯這三個層次，故稱為「機率空間」或「機率三要素」。
</div>

(4) 如前篇[互斥與加集](/lecture-notes/event-set-operations/#互斥與加集)所述，Axiom 3 中兩兩互斥的前提恰與可數加集的定義一致。因此當 $A_1,A_2,\ldots\in\mathcal{F}$ 且對所有 $i\neq j$ 皆有 $A_i\cap A_j=\varnothing$ 時，Axiom 3 亦可寫為
{: .topic-paren-item}

$$
\mathbb{P}\left(\bigcup_{i=1}^{\infty}A_i\right)=\mathbb{P}\left(\sum_{i=1}^{\infty}A_i\right)=\sum_{i=1}^{\infty}\mathbb{P}(A_i)
$$

其中 $\mathbb{P}\left(\sum_{i=1}^{\infty}A_i\right)=\sum_{i=1}^{\infty}\mathbb{P}(A_i)$ 滿足**線性函數 <span lang="en">(linear function)</span>** 的特性，故 Axiom 3 的可數可加性在部分教科書中又稱**線性 <span lang="en">(linearity)</span>**。此外，可數可加性亦稱 **$\sigma$-可加性 <span lang="en">($\sigma$-additivity)</span>**，名稱與 $\sigma$-域相對應；下一篇介紹的**有限可加性 <span lang="en">(finite additivity)</span>** 則對應一般的域。
{: .topic-paren-cont}

## 本篇小結

本篇由域出發，經 $\sigma$-域與可測空間，並以三大公理定義機率測度與機率空間:

| 層次 | 符號 | 角色 |
| :---: | :---: | :---: |
| 樣本空間 | $S$ | 隨機實驗的所有可能結果 |
| $\sigma$-域 | $\mathcal{F}$ | 由可被測度機率的事件所構成 |
| 可測空間 | $(S,\mathcal{F})$ | 指出在哪裡測度機率 |
| 機率空間 | $(S,\mathcal{F},\mathbb{P})$ | 加入滿足三大公理的機率測度 |

藉由機率公理，我們能夠衍生出許多實用的機率等式與不等式。[下一篇](/lecture-notes/probability-rules-from-axioms/)將進入機率公理及其推論，先由單一事件的基本性質談起。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Andrey N. Kolmogorov. 1956. *Foundations of the Theory of Probability*. 2nd English ed. Translated by Nathan Morrison. Chelsea Publishing Company.
- Patrick Billingsley. 1995. *Probability and Measure*. 3rd ed. Wiley.
