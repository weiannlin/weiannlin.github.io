---
title: "隨機變數，從樣本空間到數線"
subtitle: "Random Variables as Maps from Sample Space to the Real Line"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 1
order: 201
permalink: /teaching-topics/random-variables-from-sample-space-to-real-line/
date: 2026-05-17
published: false
listed: false
excerpt: "隨機變數是定義在樣本空間上的實值函數，把樣本點送到數線，並要求對任意實數 $x$，取值不超過 $x$ 的樣本點所形成的集合都是事件。其定義域為樣本空間、對應域為實數，值域則收集所有可能的取值；離散型由值域中元素的個數界定，連續型則由積分表示界定。"
---

[上一章最後一篇文章](/teaching-topics/bayes-rule-posterior-probability/)完成了分割、全機率定理與貝氏定理的討論。在第一章中，我們介紹了集合上的機率。由於所有的事件都是一個集合，故若想要討論其機率，我們必須討論每個事件所對應的集合。

然而集合論屬於離散數學，其發展事實上較為受限，比較無法應用諸如微積分之類的主流數學工具。為了解決這個問題，我們在此引入**隨機變數 (random variable)** 的概念，將樣本點對應為數值，如此一來，便可以將機率推廣至更深入的境界。

在討論機率時，逐個事件討論是比較沒有效率的，甚至沒有辦法討論完。例如: 令 $\omega_1,\omega_2,\ldots$ 分別表示直到中樂透彩前，需要購買 $1,2,\ldots$ 張樂透彩券的樣本點，這些樣本點逐個來看都很簡單，但卻無法將其全部列完。

雖然我們無法將其全部列完，但這些樣本點的對應卻是有規律的。如果我們能用一套規則進行對應，就算樣本點過多也無妨，甚至我們還能針對基於這套規則的**函數**進行分析。

## 隨機變數的定義

<span id="definition-21"></span>
<div id="def-random-variable" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.1</div>

令 $(S,\mathcal{F},\mathbb{P})$ 為一機率空間。在其上的**隨機變數 (random variable, rv)** $X\colon S\to\mathbb{R}$ 為定義在樣本空間 $S$ 上的實值函數，且對任意 $x\in\mathbb{R}$，皆有

$$
\lbrace\,\omega\mid\omega\in S,\ X(\omega)\leqslant x\,\rbrace\in\mathcal{F}
$$

</div>

隨機變數是一個函數，其有一些特殊的性質需要注意。

(1) 隨機變數 $X(\cdot)$ 是將樣本點對應至實數的函數，此即對任意 $\omega\in S$，皆有
{: .topic-paren-item}

$$
X(\omega)\in\mathbb{R}
$$

(2) $X(\cdot)$ 為一函數，故其應恪守一切函數之基本性質: 其**定義域 (domain)** 是樣本空間 $S$、**對應域 (codomain)** 是實數 $\mathbb{R}$，而**值域 (range)** 記為 $\mathcal{R}_{\sssig X}$，為實數 $\mathbb{R}$ 的子集。其中，特別需要注意的是不可有樣本點對應到多個實數，此即函數不可一對多。
{: .topic-paren-item}

<span id="可能取值集合的型態"></span>
<div id="note-range-and-support" class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

值域是指 $X$ 之所有可能的值形成的集合，記為

$$
\mathcal{R}_{\sssig X}=\lbrace\,X(\omega)\mid\omega\in S\,\rbrace
$$

值域又稱**支撐集 (support)**，本系列一律用值域，並以 $\mathcal{R}_{\sssig X}$ 表示。

</div>

(3) 關於隨機變數必須滿足的條件，也就是對任意 $x\in\mathbb{R}$，皆有
{: .topic-paren-item}

$$
\lbrace\,\omega\mid\omega\in S,\ X(\omega)\leqslant x\,\rbrace\in\mathcal{F}
$$

在部分的教科書上會改用反映射的寫法，以 $X^{-1}(\cdot)$ 定義，其等價的定義為隨機變數 $X\colon S\to\mathbb{R}$ 必須滿足
{: .topic-paren-cont}

$$
X^{-1}\bigl((-\infty,x]\bigr)=\lbrace\,\omega\mid X(\omega)\leqslant x\,\rbrace\in\mathcal{F}
$$

其中 $X^{-1}(A)$ 表示集合 $A$ 在 $X$ 之下的**原像 (preimage)**，並不表示 $X$ 具有反函數。兩種寫法事實上都在說明同一件事情，也就是只要我們有一個實數 $x$，則**能夠使得 $X(\omega)\leqslant x$ 的那些樣本點所收集而成的集合，必須是個能夠被定義機率的事件**。
{: .topic-paren-cont}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

讀者應注意的是，$X^{-1}(\cdot)$ 的定義域是實數的子集 (因為 $X\colon S\to\mathbb{R}$)，其映射回來的結果必須是樣本空間的子集，而這些被映射回來的子集，必須是個可以被定義機率的事件，且這個事件中的樣本點，都具備能使 $X(\omega)\leqslant x$ 的特色。

</div>

(4) 由於隨機變數的定義，我們所關心的「隨機變數值」通常都是一段範圍。但有的時候，我們或許也關心隨機變數 $X(\omega)$ 等於某個數字，此即
{: .topic-paren-item}

$$
X(\omega)=x
$$

而這其實是集合
{: .topic-paren-cont}

$$
\lbrace\,\omega\mid\omega\in S,\ X(\omega)=x\,\rbrace
$$

例如: $X(\omega)=3$ 代表**使得 $X$ 為 $3$ 的樣本點之集合**。為了方便，我們時常簡寫為 <span class="text-nowrap">$X=x$，</span>其中大寫英文字母代表隨機變數本身，小寫英文字母則代表一實數。讀者應特別注意，$X=x$ 為樣本點所形成的集合，故我們當然可將其視為一事件。
{: .topic-paren-cont}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

大寫字母代表的隨機變數具有**隨機性**，而小寫字母則僅為一數字，應不可混淆。往後，本系列亦將以此原則進行書寫。

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

正是因為我們關心的是隨機變數值落在 $(-\infty,x]$ 的範圍中，我們往後會知道，隨機變數的**機率分配 (probability distribution)** 最初是由其累積分配函數 (cdf) 所定義的。

</div>

隨機變數的定義給了許多方便，其中最大的好處是，過去我們需要逐一討論的樣本點與事件，被轉化為實數，我們只要使用這個「變數值」，即可代表相對應的事件；除了討論方便以外，實數給予我們的好處更在於，能使用數學分析工具，來幫助我們進行深入的探討。

在給定隨機變數的定義後，我們即可以隨機變數來討論機率函數的性質。但在正式進入機率函數之前，我們先就隨機變數及其值域的型態進行討論。

## 離散型與連續型隨機變數

<div id="def-support-classification" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.2</div>

令 $X$ 為定義於機率空間 $(S,\mathcal{F},\mathbb{P})$ 上之隨機變數。

(1) 若 $\mathcal{R}_{\sssig X}$ 中之元素個數為有限或可數無限，則稱 $X$ 為**離散型隨機變數 (discrete random variable)**。
{: .topic-paren-item}

(2) 若存在一非負函數 $f_{\sssig X}$，使得對任意 $x\in\mathbb{R}$，皆有
{: .topic-paren-item}

$$
\mathbb{P}(X\leqslant x)=\int_{-\infty}^{x}f_{\sssig X}(t)\,dt
$$

則稱 $X$ 為**連續型隨機變數 (continuous random variable)**。
{: .topic-paren-cont}

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

讀者應可對照第一章[離散樣本空間與連續樣本空間](/teaching-topics/random-experiments-sample-space-events/#離散樣本空間與連續樣本空間)的分類。離散型的判準與離散樣本空間的判準非常相像，兩者都以元素個數為有限或可數無限為準；連續型則不以元素個數為準，改以機率能否寫成積分為準。

</div>

<div id="note-uncountable-not-continuous" class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

值域為不可數無限，並不足以保證 $X$ 為連續型。一種情形是某些單點仍具有正機率，此時 $\mathbb{P}(X\leqslant x)$ 在該點跳躍，無法寫成積分；另一種情形是每一個單點的機率皆為 $0$，卻仍找不到能使 $\mathbb{P}(X\leqslant x)$ 寫成積分的非負函數 $f_{\sssig X}$。因此連續型以積分表示式界定，而不以值域中元素的個數界定。

</div>

<div id="ex-random-variable-ranges" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.1 (Ranges of Three Random Variables)</div>

<ol class="topic-list-paren">
  <li>投擲一硬幣 $1$ 次觀察其結果，令隨機變數 $X$ 表正面出現之次數，則其值域為何？</li>
  <li>假設某人每期皆購買一張樂透彩券，直到中頭獎為止。令隨機變數 $X$ 表直到中頭獎為止所經歷的槓龜次數，則其值域應為何？</li>
  <li>令隨機變數 $X$ 表某一電腦零件之壽命，則其值域應為何？</li>
</ol>

第 (1) 題的正面出現次數只有兩種可能，故

$$
\mathcal{R}_{\sssig X}=\lbrace0,1\rbrace
$$

第 (2) 題的槓龜次數可為任意非負整數，故

$$
\mathcal{R}_{\sssig X}=\lbrace0,1,2,3,\ldots\rbrace
$$

第 (3) 題的壽命為非負實數，故

$$
\mathcal{R}_{\sssig X}=\lbrace\,x\mid x\geqslant0\,\rbrace
$$

</div>

前兩題的值域分別為有限集合與可數無限集合，依 [Definition 2.2](#def-support-classification) 均為離散型隨機變數；第三題的值域為不可數無限集合，此時還須知道機率如何落在這個集合上，才能判定是否為連續型。

由於在離散型隨機變數與連續型隨機變數中，機率函數的運算性質稍有不同，故在正式定義完隨機變數的分類以後，我們方可基於此分類，進行機率函數的定義。

## 本篇小結

第一章把機率定義在事件上。事件是樣本空間的子集合，而機率函數把 $\mathcal{F}$ 中的事件送到 $0$ 與 $1$ 之間的數值。

$$
\mathbb{P}\colon\mathcal{F}\longrightarrow[0,1]
$$

本章則由隨機變數開始，改以一個定義在樣本空間上的實值函數，把樣本點送到數線上。

$$
X\colon S\longrightarrow\mathbb{R}
$$

它必須滿足的條件是，對任意實數 $x$，能使 $X(\omega)\leqslant x$ 的樣本點所形成的集合都是事件，如此才有機率可言。函數的定義域、對應域與值域在此分別是: 樣本空間 $S$、實數 $\mathbb{R}$，以及收集 $X$ 所有可能取值的 $\mathcal{R}_{\sssig X}$。

若 $\mathcal{R}_{\sssig X}$ 中的元素個數為有限或可數無限，則 $X$ 為離散型；若 $\mathbb{P}(X\leqslant x)$ 可由某個非負函數積分表示，則 $X$ 為連續型。兩種型態的機率函數運算性質不同，下一篇[離散型隨機變數與機率質量函數](/teaching-topics/discrete-random-variables-pmf/)便由離散型的機率質量函數談起。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- 黃文璋，2003，《數理統計》，初版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Joseph K. Blitzstein and Jessica Hwang. 2019. *Introduction to Probability*. 2nd ed. Chapman and Hall/CRC.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Patrick Billingsley. 1995. *Probability and Measure*. 3rd ed. Wiley.
