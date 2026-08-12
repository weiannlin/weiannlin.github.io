---
title: "域、σ-域與機率空間"
subtitle: "Fields, Sigma-Fields, and Probability Spaces"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 1
topic: 4
order: 104
permalink: /teaching-topics/event-families-sigma-fields/
date: 2026-05-05
published: true
excerpt: '機率公理要建立在哪裡？本篇依序介紹域、$\sigma$-域、可測空間與機率空間，說明哪些事件可以被測度機率，以及一個機率測度至少應滿足的三大公理。'
---

[上一篇](/teaching-topics/probability-assignment-classical-geometric/)說明了古典機率、幾何機率、客觀機率與主觀機率等指定方式，也看到這些定義各有其對應的問題，因此無法作為一個嚴謹的數學學科而有較深入的發展。俄羅斯數學家柯爾莫哥洛夫 (Andrey N. Kolmogorov) 便由此提出**機率公理 <span lang="en">(probability axioms)</span>** 作為機率論的基石，他曾說: 「機率論作為數學學科，可以、而且應該，從公理開始建設，和幾何、代數的路一樣。」

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

**公理 (axiom)** 被作為該領域所有**定理 <span lang="en">(theorem)</span>** 的源頭，不需證明其為真。以機率論為例，所有機率的定理若追本溯源，都可以發現其源頭為 Kolmogorov 的三大機率公理；藉由這些嚴謹的數學定義，機率論得以成為一個正式的數學領域，甚至至今已成為數學的幾個主要分支中的其中一支。
</div>

事實上，機率公理就是機率必須滿足的一些基礎特性。但在建立機率公理之前，我們需要了解我們要**在哪裡建立**機率公理，也就是**機率空間 <span lang="en">(probability space)</span>**。開始說明機率公理之前，我們首先注意到一些特殊的集合，這些特殊的集合將有助於我們釐清機率公理建構的範圍。

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

則稱 $\mathcal{F}$ 為佈於 $S$ 上的一個**域 (field)**，或譯為**體**，亦稱為**代數 <span lang="en">(algebra)</span>**。
</div>

[Definition 1.15](#definition-field) 在定義機率公理方面，有幾個意義與需要注意的事情:

(1) 在[隨機實驗、樣本空間與事件](/teaching-topics/random-experiments-sample-space-events/#事件與事件的發生)中我們曾經提過，所謂事件就是指樣本空間的子集合。從這個角度切入可以發現，所謂的域，事實上就是由各式各樣的事件所構成的集合。換言之，這個特殊的集合刻畫了可能發生的各種事件。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

在了解何謂機率以及建構機率公理之前，我們更可能關心的是，到底哪些東西可以衡量機率，以及這些東西 (即事件) 之間的關係，而域的定義正好在規範這些事情。
</div>

(2) 通常而言，$S$ 就是樣本空間，故條件 (2) 中的 $A^{\prime}$ 不需要特別定義；否則 $A^{\prime}=S-A$。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個性質規範了域對於事件與餘事件具有封閉性。其直觀意義在於，如果某一事件**可能發生** (即 $A\in\mathcal{F}$)，則該事件也**可能不發生**，因此必須將 $A^{\prime}$ 納入考量之中，故此時必須有 $A^{\prime}\in\mathcal{F}$ 的結果。
</div>

(3) 在條件 (2) 成立下，條件 (1) 中的 $\varnothing\in\mathcal{F}$ 與 $S\in\mathcal{F}$ 其實等價，且由條件 (1) 可知 $\mathcal{F}$ 顯然非空。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

事實上，雖然條件 (1) 保證了域的非空性，但卻不一定需要這樣定義。我們可以只定義 $\mathcal{F}$ 非空: 任取 $A\in\mathcal{F}$，由條件 (2) 可知 $A^{\prime}\in\mathcal{F}$；又由 $A,A^{\prime}\in\mathcal{F}$ 與條件 (3) 可得

$$
A\cup A^{\prime}=S\in\mathcal{F}
$$

再由條件 (2) 可得

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

在[有限樣本空間中的事件數量](/teaching-topics/random-experiments-sample-space-events/#有限樣本空間中的事件數量)中我們曾經提過，這個符號代表的是 $S$ 的**冪集合 (power set)**，也就是由 $S$ 的所有可能子集所構成的集合。
{: .topic-paren-cont}

(5) 由條件 (2)、(3) 再搭配[狄摩根律](/teaching-topics/event-set-operations/#狄摩根律)，可知域對有限交集也具有封閉性: 若 <span class="text-nowrap">$A_1,\ldots,A_n\in\mathcal{F}$，</span>則 $A_1^{\prime},\ldots,A_n^{\prime}\in\mathcal{F}$，故
{: .topic-paren-item}

$$
\bigcup_{i=1}^{n}A_i^{\prime}\in\mathcal{F}
\quad\Longrightarrow\quad
\left(\bigcup_{i=1}^{n}A_i^{\prime}\right)^{\prime}=\bigcap_{i=1}^{n}A_i\in\mathcal{F}
$$

換言之，若 $A_1,\ldots,A_n\in\mathcal{F}$，則
{: .topic-paren-cont}

$$
\bigcap_{i=1}^{n}A_i\in\mathcal{F}
$$

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個性質規範了域對於事件與事件間的聯集與交集皆具有封閉性。承接之前的直觀，我們可以注意到一個簡單的特例: 如果我們關心 $A$ 與 $B$ 兩事件是否發生，則我們應該也可能關心「$A$ 或 $B$」是否發生，還有「$A$ 且 $B$」是否發生，故我們當然需要把 $A\cup B$ 與 $A\cap B$ 也納入考量當中。也就是說，若 $A,B\in\mathcal{F}$，則

$$
A\cup B\in\mathcal{F}\quad\text{且}\quad A\cap B\in\mathcal{F}
$$

</div>

(6) 若 $S$ 為有限樣本空間，佈於其上最大可能的域 $\mathcal{F}=2^{S}$ 也必定是有限的。此時 [Definition 1.15](#definition-field) 中的域已經相當夠用，因為我們只需要考慮至多有限個集合的情況。但在[離散樣本空間與連續樣本空間](/teaching-topics/random-experiments-sample-space-events/#離散樣本空間與連續樣本空間)中我們已經很清楚地看見，樣本空間可能是無窮的。這種時候，僅考慮有限聯集與有限交集的話，$\mathcal{F}$ 很可能不足以涵蓋所有可能的情況，因此我們要將條件 (3) 的性質進行推廣，而成底下的定義。
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
  <li>若 $A_1,A_2,\ldots\subseteq S$ 且 <span class="text-nowrap">$A_1,A_2,\ldots\in\mathcal{F}$，</span>則
  $$
  \bigcup_{i=1}^{\infty}A_i\in\mathcal{F}
  $$</li>
</ol>

則稱 $\mathcal{F}$ 為佈於 $S$ 上的一個 **$\sigma$-域 ($\sigma$-field)**，或譯為 **$\sigma$-體**，亦稱為 **$\sigma$-代數 ($\sigma$-algebra)**。
</div>

[Definition 1.16](#definition-sigma-field) 可延伸出底下幾點:

(1) $\sigma$-域可以被視為域的強化版本，且**一個 $\sigma$-域必定也是一個域**。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個證明相當簡單，讀者可以自己嘗試: 只要對所有 $k>n$ 令 $A_k=\varnothing$ 就可以了。
</div>

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
S=\lbrace1,2,3,4,5,6\rbrace\\[0.4em]
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

在尋找最小 $\sigma$-域時，我們除了將要求的事件算進去之外，還要考慮它們的餘集，以及它們可能衍生的有限聯集與交集；但除此之外就不可以再多放事件進去了，否則就不是最小 $\sigma$-域了。
</div>

## 實數線上的波雷爾 $\sigma$-域 {#實數線上的-borel-sigma-域}

在眾多的樣本空間中，我們可能會遇到不可數無窮的樣本空間，例如: 實數空間 $\mathbb{R}$，這時候樣本空間的子集合可能是一段範圍或一段區間。值得注意的是，由樣本空間 $S$ 中所有**開集合 (open sets)** 所生成的 $\sigma$-域，也就是包含所有開集合的最小 $\sigma$-域，稱作**波雷爾 $\sigma$-域 (Borel $\sigma$-field)**。

實數線 $\mathbb{R}$ 上的波雷爾 $\sigma$-域記作 $\mathcal{B}(\mathbb{R})$，它也可以由所有開區間，或由所有半直線 $(-\infty,x]$ 生成。開區間、閉區間、半開區間、可數集合，以及它們經由可數聯集與可數交集形成的集合，都包含在其中。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個特殊的 $\sigma$-域是以法國數學家埃米爾・波雷爾 (Émile Borel, 1871–1956) 的名字所命名的，其最大的貢獻在於，使得實數上的區間也能夠被測度機率。波雷爾生平最有名的故事是介紹了**無限猴子定理 <span lang="en">(infinite monkey theorem)</span>**，這個定理後來也成為**高等機率論 <span lang="en">(advanced probability theory)</span>** 中一個相當重要的定理。
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

讀者應該記得，樣本空間 $S$ 包含隨機實驗的所有可能結果 (也就是樣本點)，而由樣本點構成的所有可能集合 (也就是事件)，並不是每一個都有被測度機率的必要。很直觀的想法是，有些事件明顯永遠不會發生，我們可以將這樣的事件納入 $\mathcal{F}$，再賦予其機率為 $0$；但當然也可以從一開始，就將其排除在可測度的集合之外。正是因此，佈於 $S$ 之上的 $\sigma$-域才會如此多樣。
</div>

(2) 前述定義中的可測集合，在機率論中就是我們所熟知的**隨機事件 (random events)**，亦即可以被測度機率的事件。
{: .topic-paren-item}

## 機率空間

至此，我們終於知道哪裡可以測度機率，也終於可以開始定義機率的**測度 <span lang="en">(measure)</span>** 應該符合怎樣的特性，這就是所謂機率的公理。

<div id="definition-probability-space" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.18</div>

令 $S$ 為某隨機實驗的樣本空間，$\mathcal{F}$ 為佈於 $S$ 上的一個 $\sigma$-域，函數 $\mathbb{P}(\cdot):\mathcal{F}\longrightarrow\mathbb{R}$ 為一個定義於 $\mathcal{F}$ 上的實值函數，且滿足以下三點:

<ol class="topic-list-paren">
  <li><strong>Axiom 1 (非負性, non-negativity)</strong>: 對任意 $A\in\mathcal{F}$，皆有
  $$
  \mathbb{P}(A)\geqslant 0
  $$</li>
  <li><strong>Axiom 2 (歸一性, normalization)</strong>: 樣本空間本身滿足
  $$
  \mathbb{P}(S)=1
  $$</li>
  <li><strong>Axiom 3 (可數可加性, countable additivity)</strong>: 若 $A_1,A_2,\ldots\in\mathcal{F}$，且 $A_i\cap A_j=\varnothing$ 對所有 $i\neq j$ 成立，則
  $$
  \mathbb{P}\left(\bigcup_{i=1}^{\infty}A_i\right)=\sum_{i=1}^{\infty}\mathbb{P}(A_i)
  $$</li>
</ol>

我們稱 $\mathbb{P}(\cdot)$ 為**機率測度 <span lang="en">(probability measure)</span>**，且三元組 $(S,\mathcal{F},\mathbb{P})$ 構成一個**機率空間 <span lang="en">(probability space)</span>**。
</div>

針對 [Definition 1.18](#definition-probability-space)，我們補充幾點:

(1) 定義中提到的三點性質，正是由柯爾莫哥洛夫所提出的**柯爾莫哥洛夫機率三大公理 <span lang="en">(Kolmogorov axioms)</span>**。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

讀者應該特別注意的是，柯爾莫哥洛夫機率三大公理**並沒有說明如何測度機率，只說明一個機率測度應該滿足怎樣的條件**。這一點與古典機率中的各種定義都不同: 我們並沒有在此規範機率應該**如何被測度**，只說明其**至少應滿足的特性**，但這樣就已足夠建立起整個浩瀚的機率論。
</div>

(2) 機率測度是比較正式的機率論與測度論用詞，其意義是衡量出「事件發生的可能性的大小」，一如數量、長度、面積等等的度量值一樣。但在一般的統計學與數理統計學中，通常會稱其為**機率集合函數 <span lang="en">(probability set function)</span>**，或直接簡稱為**機率函數 <span lang="en">(probability function)</span>**。後續文章在指稱 $\mathbb{P}(\cdot)$ 時，將以機率函數為主，但其他用詞亦可能混用。
{: .topic-paren-item #term-probability-function}

(3) 三元組 $(S,\mathcal{F},\mathbb{P})$ 除了被稱作機率空間外，又稱**機率三要素 <span lang="en">(probability triple)</span>**，在建構機率及其衍生性質的過程中，具有非常重要的地位。爾後在探討由機率公理所衍生出的各種性質前，我們只需要說明 $(S,\mathcal{F},\mathbb{P})$ 為一個機率空間，讀者便會明白 $S$ 是樣本空間、$\mathcal{F}$ 是佈於 $S$ 上的一個 $\sigma$-域，而 $\mathbb{P}(\cdot)$ 是定義在 $\mathcal{F}$ 上的機率函數。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

事實上，探討何謂機率，要從隨機實驗本身講起；隨之而來，便會想到隨機實驗的可能結果，也就是樣本空間 $S$；再來是想到在這些結果中，誰需要被測度機率，也就是 $\mathcal{F}$；最後是測度機率的方式，或是測度機率的結果，也就是 $\mathbb{P}(\cdot)$。從這裡來思考就會發現，$(S,\mathcal{F},\mathbb{P})$ 構築出整套機率的前因後果，因此才被稱為「機率空間」或「機率三要素」。
</div>

(4) 讀者應該記得，在[互斥與加集](/teaching-topics/event-set-operations/#互斥與加集)中，我們曾經提過有限加集與可數加集，而 Axiom 3 的前提正好與之相同，故 Axiom 3 可以寫為: 若 <span class="text-nowrap">$A_1,A_2,\ldots\in\mathcal{F}$，</span>且 $A_i\cap A_j=\varnothing$ 對所有 $i\neq j$ 成立，則
{: .topic-paren-item}

$$
\mathbb{P}\left(\bigcup_{i=1}^{\infty}A_i\right)=\mathbb{P}\left(\sum_{i=1}^{\infty}A_i\right)=\sum_{i=1}^{\infty}\mathbb{P}(A_i)
$$

其中 $\mathbb{P}\left(\sum_{i=1}^{\infty}A_i\right)=\sum_{i=1}^{\infty}\mathbb{P}(A_i)$ 滿足**線性函數 <span lang="en">(linear function)</span>** 的特性，故 Axiom 3 的可數可加性，在部分教科書中又被稱作**線性 <span lang="en">(linearity)</span>**。除此之外，可數可加性也被稱作 **$\sigma$-可加性 ($\sigma$-additivity)**；這個名字源於 $\sigma$-域，稍後我們會看見的**有限可加性 <span lang="en">(finite additivity)</span>** 則是對應到一般的域。
{: .topic-paren-cont}

## 本篇小結

本篇由域出發，經 $\sigma$-域與可測空間，最後以三大公理定義出機率測度與機率空間:

| 層次 | 符號 | 角色 |
| :---: | :---: | :---: |
| 樣本空間 | $S$ | 隨機實驗的所有可能結果 |
| $\sigma$-域 | $\mathcal{F}$ | 由可被測度機率的事件所構成 |
| 可測空間 | $(S,\mathcal{F})$ | 指出在哪裡測度機率 |
| 機率空間 | $(S,\mathcal{F},\mathbb{P})$ | 加入滿足三大公理的機率測度 |

藉由機率公理，我們能夠衍伸出一些相當有用的機率等式與不等式。[下一篇](/teaching-topics/probability-rules-from-axioms/)要談機率公理及其推論，便從單一事件所構成的一些式子開始說明起。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Andrey N. Kolmogorov. 1956. *Foundations of the Theory of Probability*. 2nd English ed. Translated by Nathan Morrison. Chelsea Publishing Company.
- Patrick Billingsley. 1995. *Probability and Measure*. 3rd ed. Wiley.
