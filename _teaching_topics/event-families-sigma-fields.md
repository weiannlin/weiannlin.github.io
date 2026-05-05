---
title: '哪些集合可以被賦予機率：事件集合族與 $\sigma$-域'
subtitle: "Event Families, Sigma-Fields, and Measurable Spaces"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 1
topic: 2
order: 102
permalink: /teaching-topics/event-families-sigma-fields/
date: 2026-05-05
excerpt: '樣本空間只說明隨機實驗的所有可能結果；事件集合族則說明哪些由結果構成的集合值得被賦予機率。本文以 $\sigma$-域作為可測事件的清單，說明可測空間與機率空間的第一層結構。'
---

[上一篇文章](/teaching-topics/random-experiments-sample-space-events/)先把**事件 (event)** 理解為樣本空間的子集合。這個說法非常適合建立直覺：樣本空間收納所有可能結果，而事件則是我們真正想詢問的一群結果。

不過，一旦樣本空間變成連續型，這句話就需要修正。機率函數不一定需要、也不一定能夠，對樣本空間的每一個任意子集合都賦予機率。於是，我們需要先指定一份「值得被賦予機率的事件之清單」。這份清單在機率論中通常用 $\mathcal{F}$ 表示。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">閱讀提示</div>

本文是測度觀點的第一個入口。若暫時只需要在有限或可數樣本空間中進行機率計算，可以先掌握「$\mathcal{F}$ 是可被賦予機率的事件清單」這個直覺；若要理解連續機率模型，則需要進一步理解為什麼這份清單必須滿足 $\sigma$-域的封閉性。
</div>

## 從事件到事件集合族

若 $S$ 是樣本空間，則 $S$ 的任一子集合 $A\subset S$ 都可以被直覺地稱為事件。但在建立機率模型時，我們其實還需要回答另一個問題：哪些事件要被納入模型，並且允許機率函數作用在其上？

因此，我們引入一個由 $S$ 的部分子集合所構成的集合，並以 $\mathcal{F}$ 表示這份清單。這裡要小心兩層集合的差異：

| 物件 | 符號 | 意義 |
| --- | --- | --- |
| 樣本點 | $\omega$ | 一次隨機實驗的可能結果 |
| 事件 | $A\subset S$ | 由樣本點構成的一個集合 |
| 事件集合族 | $\mathcal{F}$ | 由許多事件所構成的集合 |

換句話說，$A\in\mathcal{F}$ 表示 $A$ 是一個被納入清單中的事件，也就是一個將來可以被賦予機率的事件。

## 清單不能隨便列

事件集合族不是任意列一串事件就好。原因很簡單：如果某一事件 $A$ 是我們願意討論的事件，那麼「$A$ 沒有發生」也應該是我們願意討論的事件；如果 $A$ 與 $B$ 都是我們願意討論的事件，那麼「$A$ 或 $B$ 發生」以及「$A$ 且 $B$ 發生」也應該是我們願意討論的事件。

這些要求可被整理成一組封閉性條件。

<div class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.7</div>

令 $S$ 為一非空集合，$\mathcal{F}$ 為一個由 $S$ 的部分子集所構成之集合，且滿足以下三點：

<ol class="topic-list-paren">
  <li>虛無事件 $\varnothing$ 被納入清單；等價地，樣本空間 $S$ 也被納入清單。</li>
  <li>若 $A\in\mathcal{F}$，則其餘事件 $A^{\prime}$ 也被納入清單。</li>
  <li>若 $A_1,\ldots,A_n\in\mathcal{F}$，則其有限聯集 $\bigcup_{i=1}^n A_i$ 也被納入清單。</li>
</ol>

則稱 $\mathcal{F}$ 為佈於 $S$ 上的一個**域 (field)**，或譯為**體**。有些教科書也會使用 algebra 一詞。
</div>

在這個定義中，條件 (2) 表示事件集合族對餘事件封閉；條件 (3) 表示它對有限聯集封閉。再搭配狄摩根律 (DeMorgan's law)，也可以推出它對有限交集封閉。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

域的直覺是：只要一個事件被放入清單，它自然衍生出的基本事件也要被放入清單。若 $A$ 可以被討論，則 $A^{\prime}$ 也應該可以被討論；若 $A$ 與 $B$ 可以被討論，則 $A\cup B$ 與 $A\cap B$ 也應該可以被討論。
</div>

## 為什麼還需要 $\sigma$-域

若樣本空間是有限的，域通常已經足夠。但在許多機率模型中，樣本空間可能是無窮，甚至不可數無窮。例如，觀察某零件壽命時，常把 $[0,\infty)$ 作為樣本空間。觀察飛鏢落點時，樣本空間則可能是平面上的一塊區域。

這時候，機率模型經常需要處理可數多個事件的聯集。例如，若 $A_1,A_2,\ldots$ 分別表示某些可觀察條件，則「至少有一個 $A_i$ 發生」會自然寫成

$$
\bigcup_{i=1}^{\infty}A_i
$$

因此，事件集合族需要比域更強的封閉性。

<div class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.8</div>

令 $S$ 為一非空集合，$\mathcal{F}$ 為一個由 $S$ 的部分子集所構成之集合，且滿足以下三點：

<ol class="topic-list-paren">
  <li>虛無事件 $\varnothing$ 被納入清單；等價地，樣本空間 $S$ 也被納入清單。</li>
  <li>若 $A\in\mathcal{F}$，則其餘事件 $A^{\prime}$ 也被納入清單。</li>
  <li>若 $A_1,A_2,\ldots\in\mathcal{F}$，則其可數聯集 $\bigcup_{i=1}^{\infty}A_i$ 也被納入清單。</li>
</ol>

則稱 $\mathcal{F}$ 為佈於 $S$ 上的一個 **$\sigma$-域 ($\sigma$-field)**，或譯為 **$\sigma$-體**，亦稱為 **$\sigma$-代數 ($\sigma$-algebra)**。
</div>

由狄摩根律可知，若 $\mathcal{F}$ 對餘集與可數聯集封閉，則 $\mathcal{F}$ 也會對可數交集封閉。也就是說，若 $A_1,A_2,\ldots\in\mathcal{F}$，則

$$
\bigcap_{i=1}^{\infty}A_i\in\mathcal{F}
$$

<div class="topic-proof" markdown="1">
**Proof.** 由 $A_i\in\mathcal{F}$ 可知其餘事件 $A_i^{\prime}$ 也被納入清單。再由可數聯集封閉性可知，可數聯集 $\bigcup_{i=1}^{\infty}A_i^{\prime}$ 仍在清單中。最後再取餘集，得到

$$
\left(\bigcup_{i=1}^{\infty}A_i^{\prime}\right)^{\prime} \in \mathcal{F}
$$

由狄摩根律可得

$$
\left(\bigcup_{i=1}^{\infty}A_i^{\prime}\right)^{\prime}=\bigcap_{i=1}^{\infty}A_i
$$

因此可數交集 $\bigcap_{i=1}^{\infty}A_i$ 也被納入清單。 $\square$
</div>

## 最小與最大的事件清單

對同一個樣本空間 $S$ 而言，$\sigma$-域不一定唯一。最小的選擇是只包含虛無事件與確定事件：

$$
\mathcal{F}_{\min}=\lbrace\varnothing,S\rbrace
$$

最大的選擇是將 $S$ 的所有子集合全部納入，也就是冪集合 (power set)：

$$
\mathcal{F}_{\max}=2^S=\lbrace\,A\mid A\subset S\,\rbrace
$$

介於兩者之間，還有許多不同的 $\sigma$-域。這表示我們在建立機率模型時，不只是在指定樣本空間，也是在指定哪些事件值得被機率函數處理。

<div class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.3 (Generated Sigma-Field)</div>

考慮投擲一顆六面骰一次，令

$$
S=\lbrace1,2,3,4,5,6\rbrace,\qquad A=\lbrace5\rbrace
$$

若事件清單中包含 $A$，則因為 $\sigma$-域必須對餘集封閉，它也必須包含

$$
A^{\prime}=\lbrace1,2,3,4,6\rbrace
$$

因此，包含 $A$ 的最小 $\sigma$-域為

$$
\mathcal{F}_A=\lbrace\varnothing,S,A,A^{\prime}\rbrace
$$

這個例子說明了一件事：只要把一個事件放進事件集合族，就會被迫連同它所衍生出的基本事件一起放進去。
</div>

## 可測空間

$\sigma$-域的角色，是刻畫樣本空間中哪些事件可以被衡量機率。當樣本空間與其上的 $\sigma$-域一起被指定時，我們得到的是可測空間。

<div class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.9</div>

令 $S$ 為一個非空集合，而 $\mathcal{F}$ 為佈於 $S$ 上的一個 $\sigma$-域。由它們形成的序對 $(S,\mathcal{F})$ 稱為**可測空間 (measurable space)**。對 $A\in\mathcal{F}$ 這樣的集合，稱 $A$ 為**可測集合 (measurable set)**。
</div>

換句話說，可測集合就是被 $\mathcal{F}$ 收納的那些由樣本點構成的集合。在機率論中，可測集合就是能夠被賦予機率的隨機事件 (random event)。因此，可測空間 $(S,\mathcal{F})$ 的意義是：$S$ 說明隨機實驗的所有可能結果，$\mathcal{F}$ 說明在這些結果之中，哪些由結果構成的集合可以被機率模型處理。

## 機率空間

有了可測空間後，才輪到機率函數登場。機率函數不是定義在所有可能子集合上，而是定義在 $\mathcal{F}$ 上。

<div class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.10</div>

令 $S$ 為某隨機實驗的樣本空間，$\mathcal{F}$ 為佈於 $S$ 上的一個 $\sigma$-域。若函數

$$
\mathbb{P}:\mathcal{F}\longrightarrow\mathbb{R}
$$

滿足以下三點：

<ol class="topic-list-paren">
  <li><strong>非負性 (non-negativity)</strong>：對任意 $A\in\mathcal{F}$，皆有
  $$
  \mathbb{P}(A)\geq 0
  $$</li>
  <li><strong>歸一性 (normalization)</strong>：樣本空間本身滿足
  $$
  \mathbb{P}(S)=1
  $$</li>
  <li><strong>可數可加性 (countable additivity)</strong>：若 $A_1,A_2,\ldots\in\mathcal{F}$ 且兩兩互斥，則有
  $$
  \mathbb{P}\left(\bigcup_{i=1}^{\infty}A_i\right)=\sum_{i=1}^{\infty}\mathbb{P}(A_i)
  $$</li>
</ol>

則稱 $\mathbb{P}$ 為**機率測度 (probability measure)**，而三元組 $(S,\mathcal{F},\mathbb{P})$ 構成一個**機率空間 (probability space)**。
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

柯爾莫哥洛夫機率公理 (Kolmogorov axioms) 並不說明某個事件的機率應該如何被計算，而是說明一個機率函數至少應該滿足哪些條件。古典機率、幾何機率或其他模型可以提供不同的計算方式；公理化機率則提供共同的數學骨架。
</div>

## 本篇小結

主題一將事件暫時理解為樣本空間的子集合；主題二則把這句話修正得更精確：

| 層次 | 物件 | 角色 |
| --- | --- | --- |
| 樣本空間 | $S$ | 所有可能結果 |
| 事件集合族 | $\mathcal{F}$ | 可被賦予機率的事件清單 |
| 可測空間 | $(S,\mathcal{F})$ | 指定可能結果與可測事件 |
| 機率空間 | $(S,\mathcal{F},\mathbb{P})$ | 再加入機率函數 |

因此，嚴格地說，事件不是任意子集合，而是屬於 $\mathcal{F}$ 的子集合。這個觀點在有限樣本空間中常常可以被簡化；但在連續樣本空間與極限操作中，$\sigma$-域正是讓機率模型能夠穩定運作的關鍵。下一篇將回到一個更直接的問題：[機率如何被指定](/teaching-topics/probability-assignment-classical-geometric/)？
