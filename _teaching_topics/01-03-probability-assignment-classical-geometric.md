---
title: "古典機率、幾何機率、客觀機率與主觀機率"
subtitle: "Classical, Geometric, Objective, and Subjective Probability"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 1
topic: 3
order: 103
permalink: /teaching-topics/probability-assignment-classical-geometric/
date: 2026-05-05
published: true
excerpt: "機率最早是為了解決生活中遇到的隨機問題而發展。本篇介紹古典機率、幾何機率、客觀機率與主觀機率四種指定方式，以及它們各自的假設與限制。"
---

[上一篇](/teaching-topics/event-set-operations/)整理了事件的集合運算。在有了集合及事件的基本關係後，我們便可以正式進入機率的世界，或準確地說，進入「古典機率」的世界。

機率的起源時常被認為是由賭博而來。這個說法當然未必正確，但卻能夠讓我們得知一件事情: 機率最早是為了解決生活中遇到的隨機問題而發展的。讀者應能細細回想生活中遇到的機率問題，例如: 玩撲克牌在五張手牌中拿到一組鐵支 (四條) 的機率、明天某地下雨的機率、罹患某一疾病後痊癒的機率。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

「機率起源於賭博」的說法，可能是因為在數學史上，促使機率論蓬勃發展最廣為人知的事件是: 十七世紀中葉，法國貴族梅雷 (Antoine Gombaud, chevalier de Méré) 向數學家帕斯卡 (Blaise Pascal) 提出賭局中遇到的問題，帕斯卡便與其朋友費馬 (Pierre de Fermat) 以書信進行討論，進而使歐洲的數學家們產生興趣，並以數學工具研究機率理論。
</div>

若讀者進一步仔細思考前述三種機率應如何得出，便可以發現這三種機率事實上是完全不同的三種機率。若以一個相同的定義來解釋這三種機率，未免稍嫌不精準，故數學家便給予這三種類型的機率各自不同的定義。以下就直接以這三種定義來探討。其中，古典機率可再推廣出幾何機率，因此本篇將依序介紹四種指定方式。

## 古典機率

<div id="definition-classical-probability" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.11</div>

令 $A\subseteq S$ 為**有限**樣本空間 $S$ 中之一事件，且假設 $S$ 中每一個樣本點皆為均等可能 <span lang="en">(equally likely)</span>，則 $A$ 之**古典機率 <span lang="en">(classical probability)</span>** 為

$$
\mathbb{P}(A)=\frac{\mathrm{n}(A)}{\mathrm{n}(S)}
$$

其中 $\mathrm{n}(\cdot)$ 為點算集合中元素個數之函數。
</div>

古典機率即是高中數學裡所講的機率，其精神是認為樣本空間 $S$ 中的每一個樣本點都具有同樣的發生機率，此即**均等可能性 <span lang="en">(equally likely)</span>**。例如: 投擲一枚「公正的」骰子，則出現 $1$ 點到 $6$ 點的機率皆相同。如此一來，我們可以用某一事件 $A$ 的樣本點數，相對於樣本空間 $S$ 的樣本點數的比例，作為發生該事件的機率。

從上面的敘述來看，我們便能夠理解為何古典機率的定義需要假定樣本空間 $S$ 為有限的。因為我們必須點算樣本空間中樣本點的個數，若是[無限樣本空間](/teaching-topics/random-experiments-sample-space-events/#離散樣本空間與連續樣本空間) (可數或不可數)，便無法點算。

<div id="example-two-dice" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.5 (Two Dice)</div>

<div lang="en" markdown="1">
A fair die is rolled twice, and the numbers showing on top are recorded as an ordered pair.

(1) List the sample space $S$.
{: .topic-paren-item}

(2) Let $A$ be the event that the two numbers add up to $10$. Find $\mathbb{P}(A)$.
{: .topic-paren-item}
</div>

以下依序求解。

**(1)** 由題目可知考慮點數順序，故

$$
\begin{aligned}
S&=\left\lbrace
\begin{array}{ccc}
(1,1) & \cdots & (1,6)\\
\vdots & \ddots & \vdots\\
(6,1) & \cdots & (6,6)
\end{array}
\right\rbrace\\[0.4em]
&=\lbrace\,(x,y)\mid x,y\in\lbrace1,2,3,4,5,6\rbrace\,\rbrace
\end{aligned}
$$

**(2)** 由 (1) 可知 $\mathrm{n}(S)=6\times 6=36$。又

$$
A=\lbrace(4,6),(5,5),(6,4)\rbrace
$$

故 $\mathrm{n}(A)=3$。由古典機率之定義可知

$$
\mathbb{P}(A)=\frac{\mathrm{n}(A)}{\mathrm{n}(S)}=\frac{3}{36}=\frac{1}{12}\fallingdotseq 0.08333
$$

</div>

<div id="example-straight-flush" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.6 <span lang="en">(Straight Flush)</span></div>

在一副均勻洗牌的 $52$ 張撲克牌中抽取五張牌作為手牌，則此五張牌恰為同花順的機率為何？

令 $A$ 表示同花順之事件。一手同花順可由「選定一種花色」與「選定連續五張點數的起點 (A 至 10，共十種)」完全決定，故

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{n}(A)=\binom{4}{1}\binom{10}{1}=4\times 10=40,\qquad
\mathrm{n}(S)=\binom{52}{5}=2{,}598{,}960
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{n}(A)&=\binom{4}{1}\binom{10}{1}=4\times 10=40,\\[0.4em]
\mathrm{n}(S)&=\binom{52}{5}=2{,}598{,}960
\end{aligned}
$$

</div>

由古典機率之定義可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(A)=\frac{\mathrm{n}(A)}{\mathrm{n}(S)}=\frac{40}{2{,}598{,}960}\fallingdotseq 0.00001539
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(A)&=\frac{\mathrm{n}(A)}{\mathrm{n}(S)}=\frac{40}{2{,}598{,}960}\\[0.4em]
&\fallingdotseq 0.00001539
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

古典機率的核心概念，是計算事件的樣本點個數與有限樣本空間的樣本點個數之比值，並以其作為該事件發生之機率。在此精神之下，我們必須具有均等可能性假設，並且**透過點算樣本點個數來當作衡量該事件大小的工具**。在此概念與假設之下，很自然地需要引入各種能夠點算事件樣本點數的工具，這正是**組合分析 <span lang="en">(combinatorial analysis)</span>** 中排列與組合所扮演的角色。
</div>

## 幾何機率與幾何測度

雖然稍早在 [Definition 1.11](#definition-classical-probability) 中，我們要求樣本空間為有限，但事實上我們可以將這個定義進行推廣，從而成為**幾何機率 <span lang="en">(geometric probability)</span>**。幾何機率的概念，也可以與後面主題將介紹的**[連續均勻分配](/teaching-topics/uniform-distribution-integral-transform/#def-uniform-distribution) <span lang="en">(continuous uniform distribution)</span>** 相呼應。我們來看看其定義。

<div id="definition-geometric-probability" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.12</div>

令樣本空間 $S$ 為一幾何範圍，而 $A\subseteq S$ 為樣本空間 $S$ 中其中一部分 (亦為 $S$ 中之一事件)，則 $A$ 之**幾何機率 <span lang="en">(geometric probability)</span>** 為

$$
\mathbb{P}(A)=\frac{\mathrm{m}(A)}{\mathrm{m}(S)}
$$

其中 $\mathrm{m}(\cdot)$ 為**幾何測度 <span lang="en">(geometric measure)</span>**，且要求 $0<\mathrm{m}(S)<\infty$，使上式的比值有意義。
</div>

事實上，幾何測度大家都很熟悉，例如: 一維空間中的幾何測度為長度、二維空間中的幾何測度為面積、三維空間中的幾何測度為體積。在此理解之下，**幾何機率的意義即為某事件之幾何測度相對於樣本空間的幾何測度的比例**。

當我們有了幾何測度的概念後，回頭來看 [Definition 1.11](#definition-classical-probability)，我們會發現其中的 $\mathrm{n}(\cdot)$ 事實上是一種**計數測度 <span lang="en">(counting measure)</span>**，不過這已經屬於**測度論 <span lang="en">(measure theory)</span>** 的範圍，我們在此不討論。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

各種的**測度 <span lang="en">(measure)</span>** 都是在「度量」某件事的大小。當測度被用在集合上，則代表衡量集合在該測度所關心的面向上的大小，例如: 數量的大小、長度的大小、面積的大小。事實上，後面的文章將正式介紹的[**機率測度 <span lang="en">(probability measure)</span>**](/teaching-topics/event-families-sigma-fields/#機率空間)同樣也屬於一種測度，而機率測度所衡量的，是**事件發生的可能性的大小**。
</div>

<div id="example-bombing-target" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.7 <span lang="en">(Bombing a Circular Target)</span></div>

<div lang="en" markdown="1">
A bomber aims at a target located at the center of a circular region of radius $1$ mile. The bomb lands at a point uniformly distributed over the region, and it destroys everything within $0.5$ miles of its landing point. What is the probability that a single bomb destroys the target?
</div>

由題意知道，炸彈可能掉落的範圍即為樣本空間，並且

$$
S=\lbrace\,(x,y)\mid x^2+y^2\leqslant 1\,\rbrace
$$

又令 $A$ 表示投擲一次炸彈就摧毀目標之事件。目標被摧毀，等價於落點與圓心的距離不超過 $0.5$ 英里，故

$$
A=\lbrace\,(x,y)\mid x^2+y^2\leqslant\frac{1}{4}\,\rbrace
$$

以面積作為幾何測度，則所求為

$$
\mathbb{P}(A)=\frac{\mathrm{m}(A)}{\mathrm{m}(S)}=\frac{(0.5)^{2}\pi}{1^{2}\pi}=\frac{1}{4}
$$

</div>

以上的機率，都還是建立在某種「均勻」的假設下所得到的: 古典機率假設有限樣本空間中的每一個樣本點均等可能；幾何機率則假設落點不偏向 $S$ 中的任何位置，事件的機率只取決於其幾何測度的比例。若是這類假設不成立，則我們會需要其他的機率定義。

## 客觀機率

<div id="definition-objective-probability" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.13</div>

令 $\mathrm{n}_N(A)$ 為 $N$ 次重複之隨機實驗中，事件 $A$ 發生的次數。若下列極限存在，則 $A$ 之**客觀機率 <span lang="en">(objective probability)</span>** 為

$$
\mathbb{P}(A)=\lim_{N\to\infty}\frac{\mathrm{n}_N(A)}{N}
$$

亦被稱為**相對次數機率 <span lang="en">(relative frequency probability)</span>** 或**經驗機率 <span lang="en">(empirical probability)</span>**。
</div>

客觀機率在使用上相較於古典機率，有幾個比較優勢的地方:

(1) 不需要假設樣本空間中之每一個樣本點發生機率皆相同。
{: .topic-paren-item}

(2) 樣本空間可以為無限樣本空間。
{: .topic-paren-item}

然而，其亦有較為劣勢的地方:

(1) 其定義本身牽涉到極限，然而極限僅為一數學上之概念，實務上不可能重複無限多次。
{: .topic-paren-item}

(2) 其定義本身未必具有一穩定收斂的值。
{: .topic-paren-item}

(3) 在不能重複的事件中 (例如: 預測一特定日子的天氣) 並無法使用。
{: .topic-paren-item}

關於相對次數是否隨重複次數增加而逐漸穩定，讀者可以在 Demos 的[蒙提霍爾問題實作](/demos/monty-hall/)中，實際觀察其模擬部分的相對次數變化。蒙提霍爾問題 <span lang="en">(Monty Hall problem)</span> 的完整敘述，會在稍後的[條件機率](/teaching-topics/conditional-probability-information/#example-monty-hall)中提到。

<div id="example-three-point-shooting" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.8 <span lang="en">(Three-Point Shooting)</span></div>

截至 2021 年 5 月 20 日，NBA 籃球員 Stephen Curry 在其生涯 $6540$ 次的三分球出手中，命中了 $2832$ 球，試求其三分球命中的機率。

令 $A$ 表示 Stephen Curry 命中三分球之事件。以其生涯至該日的出手紀錄，作為長期相對次數的近似，可得

$$
\mathbb{P}(A)\fallingdotseq\frac{2832}{6540}\fallingdotseq 0.4330
$$

</div>

客觀機率解決了古典機率定義遇到的最大難題，也就是**樣本空間中的樣本點需假設發生機率相同**；但卻衍伸出新的問題，其中最大的困難點，當屬無法應用在不能重複的事件中。在這樣的情況下，數學家給了第三種機率定義。

## 主觀機率

<div id="definition-subjective-probability" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.14</div>

研究者依照其專業知識或相關證據，主觀地認定事件 $A$ 發生之機率 $\mathbb{P}(A)\in[0,1]$，即為**主觀機率 <span lang="en">(subjective probability)</span>**。
</div>

本篇的開端舉例了幾種不同的機率，但在現實世界中，我們經常使用的機率往往是主觀機率與客觀機率的結合。例如: 明天的降雨機率，事實上是氣象專家**參考了過去相當長時間以來對於該地的氣象觀察**，並且**結合專家個人的專業知識主觀認定**所產生的結果。

## 本篇小結

我們並不難發現，前述的各種機率都有其對應的問題。下表整理四種指定方式，其中幾何機率可視為古典機率的推廣:

| 指定方式 | 依賴的假設或條件 | 主要限制 |
| :---: | :---: | :---: |
| 古典機率 | 有限樣本空間、均等可能性 | 均等可能性未必成立 |
| 幾何機率 | 落點不偏向幾何範圍內任何位置 | 均勻性未必成立 |
| 客觀機率 | 長期重複觀察的極限 | 極限未必存在，且事件須可重複 |
| 主觀機率 | 專業知識與證據 | 因研究者而異 |

如此的特性，導致這幾種機率定義在嚴謹的數學世界中，並無法具有過多的發展。為此，在接下來的文章中，我們將開始介紹**公理化機率系統 <span lang="en">(axiomatized probability system)</span>**，並帶讀者認識現代機率論的根源。它的起點，是先說明哪些集合可以被賦予機率，這正是[下一篇](/teaching-topics/event-families-sigma-fields/)要談的域、$\sigma$-域與機率空間。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- William Feller. 1968. *An Introduction to Probability Theory and Its Applications*. Vol. 1, 3rd ed. Wiley.
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Morris H. DeGroot and Mark J. Schervish. 2012. *Probability and Statistics*. 4th ed. Pearson.
- Emanuel Parzen. 1960. *Modern Probability Theory and Its Applications*. Wiley.
