---
title: "伯努利實驗與伯努利分配"
subtitle: "Bernoulli Trials and the Bernoulli Distribution"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 4
topic: 1
order: 401
permalink: /teaching-topics/ch4-p01-candidate/
date: 2026-08-12
published: false
excerpt: "伯努利實驗是只有成功與失敗兩種結果、成功機率固定，而且各次實驗彼此獨立的隨機實驗，二項、多項、幾何與負二項這幾個分配都由它而來。本篇先給出伯努利實驗的定義，說明成功與失敗只是研究者對兩類出象的稱呼，再進入其中最簡單的伯努利分配: 只進行一次伯努利實驗，並以成功實驗的發生次數作為隨機變數，其機率函數為 $p_{\\sssig X}(x)=p^{x}q^{1-x}$ 這個式子，期望值等於成功機率，變異數則是成功機率與失敗機率的乘積。文中證明這個機率函數為合法的機率函數，並推導其期望值、變異數與動差母函數，說明失敗機率 $q$ 並不是另一個參數，最後指出任意隨機變數是否落在給定範圍的指標函數也服從伯努利分配。"
---

第三章把隨機變數的概念推廣到[隨機向量](/teaching-topics/random-vectors-joint-pmf/#def-random-vector)，處理的是多個隨機變數合在一起時的聯合分配，以及變數與變數之間的關係。第一章到第三章所建立的，都是機率與隨機變數的一般性定義與性質；本章要談的則是幾個特別常見的機率分配模型。

統計學及其相關的學科，大多都是為了解決生活中的問題而生，而在嘗試解決問題時，經常會透過合適的描述，來尋找與問題相符的機率分配，從而幫助我們解決問題。

這其中，部分的機率分配因為太常被使用而知名，另一部分則是因為其模型結構簡單，或具有一些優秀的數學運算性質而知名，當然，其中也不乏二者兼具的模型。

這些常用的知名機率分配模型，會在本章被特別提出來探討，讀者應以熟悉這些機率分配的性質及操作為目標，並且將其作為學習往後章節，以及更進階的相關學科之基礎工具使用。

這其中，可以簡易分成**離散機率分配模型**與**連續機率分配模型**兩種；若以特色區分的話則可以分成**伯努利實驗相關分配**、**卜瓦松過程相關分配**、**貝塔相關分配**及**常態相關分配**幾個大類別。

此外，除了熟悉這些機率分配的機率函數外，讀者亦應該熟悉一個機率分配的分配參數，與其適用的問題類型，甚至是該分配所衍生出的各種特殊性質。然而，其中有不少特殊性質，在稍早的章節中已經提前曝光。

本篇是第四章的第一篇，先給出伯努利實驗的定義與其下轄的各個分配，再進入其中最簡單的伯努利分配。

## 伯努利實驗

<div id="def-ber-trial" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 4.1 (伯努利實驗, Bernoulli trial)</div>

若一隨機實驗滿足以下三點，則我們稱此實驗為**伯努利實驗 <span lang="en">(Bernoulli trial)</span>**:

<ol class="topic-list-paren">
  <li>實驗可能的出象 <span lang="en">(outcomes)</span> 可被分為兩個互斥事件，定義為「成功 <span lang="en">(success)</span>」與「失敗 <span lang="en">(failure)</span>」。</li>
  <li>每次實驗中，成功的機率 $p$ 均為固定值。</li>
  <li>實驗與實驗間，彼此獨立。</li>
</ol>

</div>

伯努利實驗是由伯努利 (Jacob Bernoulli, 1655-1705) 提出，因而以其姓氏命名。由於伯努利實驗僅有成敗二種結果，因此又被稱作成敗實驗。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

事實上，Jacob Bernoulli 的貢獻遠不止如此，作為一個數學家，Bernoulli 的貢獻相當多元，最知名的當屬在處理連續複利問題時，發現尤拉數 $e=\lim_{n\to\infty}\left(1+\frac{1}{\,n\,}\right)^{n}$ 這個常數，並且提出最早的大數法則 (law of large number) 的版本。

</div>

讀者應注意的是，在伯努利實驗中，所謂「成功」與「失敗」二類並無正面與反面的意義，僅將研究者所關心的出象類別定義為成功，而其所較不關心的類別定義為失敗。

基於伯努利實驗的特性，我們可以由此定義出許多重要的分配，下轄的分配包含:

<ol class="topic-list-paren">
  <li>伯努利分配 <span lang="en">(Bernoulli distribution)</span></li>
  <li>二項分配 <span lang="en">(binomial distribution)</span></li>
  <li>多項分配 <span lang="en">(multinomial distribution)</span></li>
  <li>幾何分配 <span lang="en">(geometric distribution)</span></li>
  <li>負二項分配 <span lang="en">(negative binomial distribution)</span></li>
</ol>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

嚴格上來說，上列的多項分配並不屬於伯努利實驗下轄的分配，但其結果能完全由二項分配推廣而來，故仍可列於此處。

</div>

以下分別敘述這些分配，並說明其之間的關係。

## 伯努利分配

<div id="def-bernoulli" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 4.2 (伯努利分配, Bernoulli distribution)</div>

**適用範圍**:

令 $X$ 表僅進行**一次**伯努利實驗中，成功實驗的發生次數。

**值域範圍**:

$$
\mathcal{R}_{\sssig X}=\lbrace\,0,1\,\rbrace
$$

**表示式**:

$$
X\sim\mathrm{Ber}(p)
$$

**參數與參數範圍**:

$0<p<1$ 為伯努利實驗中，成功類的發生機率。

**機率函數**:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
p_{\sssig X}(x)=p^{x}(1-p)^{1-x}=p^{x}q^{1-x},\ x=0,1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig X}(x)&=p^{x}(1-p)^{1-x}\\[0.45em]
&=p^{x}q^{1-x},\ x=0,1
\end{aligned}
$$

</div>

其中，$q=1-p$ 為失敗類發生的機率。

**期望值、變異數、動差母函數**:

$$
\begin{gathered}
\mathbb{E}(X)=p,\ \ \mathrm{Var}(X)=p(1-p)=pq\\[0.45em]
M_{\sssig X}(t)=pe^{t}+(1-p)=pe^{t}+q,\ t\in\mathbb{R}
\end{gathered}
$$

</div>

伯努利分配有一些地方需要注意:

(1) 我們證明其機率函數為一個合法的機率函數與期望值、變異數及動差母函數如下:
{: .topic-paren-item}

<div class="topic-proof" markdown="1">
**Proof.** 先驗證機率函數的加總為 <span class="text-nowrap">$1$，</span>即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\sum_{x\in\mathcal{R}_{\sssig X}}p_{\sssig X}(x)=\sum_{x=0}^{1}p^{x}(1-p)^{1-x}=(1-p)+p=1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\sum_{x\in\mathcal{R}_{\sssig X}}p_{\sssig X}(x)&=\sum_{x=0}^{1}p^{x}(1-p)^{1-x}\\[0.45em]
&=(1-p)+p=1
\end{aligned}
$$

</div>

接著求期望值與二階原動差，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\sum_{x=0}^{1}xp^{x}(1-p)^{1-x}=0\times(1-p)+1\times p=p\\[0.45em]
\mathbb{E}\bigl(X^{2}\bigr)&=\sum_{x=0}^{1}x^{2}p^{x}(1-p)^{1-x}=0^{2}\times(1-p)+1^{2}\times p=p
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\sum_{x=0}^{1}xp^{x}(1-p)^{1-x}\\[0.45em]
&=0\times(1-p)+1\times p=p\\[0.45em]
\mathbb{E}\bigl(X^{2}\bigr)&=\sum_{x=0}^{1}x^{2}p^{x}(1-p)^{1-x}\\[0.45em]
&=0^{2}\times(1-p)+1^{2}\times p=p
\end{aligned}
$$

</div>

由此可得變異數

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}(X)=\mathbb{E}\bigl(X^{2}\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}=p-p^{2}=p(1-p)=pq
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(X)&=\mathbb{E}\bigl(X^{2}\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}\\[0.45em]
&=p-p^{2}=p(1-p)=pq
\end{aligned}
$$

</div>

最後求動差母函數，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{\sssig X}(t)&=\mathbb{E}\bigl(e^{tX}\bigr)=\sum_{x=0}^{1}e^{tx}p^{x}(1-p)^{1-x}=e^{0}\times(1-p)+e^{t}\times p\\[0.45em]
&=pe^{t}+(1-p)=pe^{t}+q,\ t\in\mathbb{R}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig X}(t)&=\mathbb{E}\bigl(e^{tX}\bigr)\\[0.45em]
&=\sum_{x=0}^{1}e^{tx}p^{x}(1-p)^{1-x}\\[0.45em]
&=e^{0}\times(1-p)+e^{t}\times p\\[0.45em]
&=pe^{t}+(1-p)=pe^{t}+q,\ t\in\mathbb{R}
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

事實上，伯努利分配的所有階原動差都是成功機率 <span class="text-nowrap">$p$，</span>並且這一點在 [Example 2.32 <span lang="en">(Continued)</span>](/teaching-topics/uniqueness-of-the-mgf/#ex-constant-moments-bernoulli) 曾出現過。

</div>

(2) 特別需要提的是，一旦成功機率 $p$ 被決定了後，失敗機率 $q=1-p$ 也會隨之決定，這是一體兩面的；換句話說，**$q$ 並不是另一個參數**。
{: .topic-paren-item}

(3) 令 $X$ 為任意隨機變數，$A$ 為一給定的範圍，若我們定義指標函數 <span lang="en">(indicator function)</span>
{: .topic-paren-item}

$$
\mathbb{I}_{\sssig A}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
1, & x\in A\\[0.5em]
0, & x\notin A
\end{array}
\right.
$$

則我們有
{: .topic-paren-cont}

$$
\mathbb{I}_{\sssig A}(X)\sim\mathrm{Ber}(p)
$$

其中 <span class="text-nowrap">$p=\mathbb{P}(X\in A)$。</span>
{: .topic-paren-cont}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

事實上，這個結果是將任意隨機變數 $X$ 給分為二類，分別是「在 $A$ 當中」與「不在 $A$ 當中」，則其結果自然會變為一個伯努利實驗。

</div>

<div id="ex-bernoulli-1" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.1</div>

<div lang="en" markdown="1">
Let the moment-generating function of random variable $X$ be <span class="text-nowrap">$M_{\sssig X}(t)=0.25+0.75e^{t}$,</span> what is the expectation and variance of <span class="text-nowrap">$X$?</span>
</div>

由 [mgf 的唯一性](/teaching-topics/uniqueness-of-the-mgf/#thm-mgf-uniqueness)可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
X\sim\mathrm{Ber}\bigl(p=0.75\bigr)\ \Longrightarrow\ \mathbb{E}(X)=p=0.75\\[0.45em]
\mathrm{Var}(X)=p(1-p)=0.75\times0.25=0.1875
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
X\sim\mathrm{Ber}\bigl(p=0.75\bigr)\\[0.45em]
\Longrightarrow\ \mathbb{E}(X)=p=0.75\\[0.45em]
\mathrm{Var}(X)=p(1-p)\\[0.45em]
=0.75\times0.25=0.1875
\end{gathered}
$$

</div>

</div>

讀者或許會對於伯努利分配的應用情境感覺到些許困惑，為什麼只有成功與失敗的情境下，我們要刻意定義 $X$ 表示伯努利實驗中的「成功次數」呢？這個問題，相信在接下來的二項分配中，能夠為讀者解惑。

## 本篇小結

[Definition 4.1](#def-ber-trial) 以三個條件界定伯努利實驗: 實驗可能的出象分成成功與失敗兩個互斥事件、每次實驗的成功機率 $p$ 均為固定值，以及實驗與實驗之間彼此獨立。這裡的成功與失敗並沒有正面與反面的意義，只是研究者對兩類出象的稱呼。由伯努利實驗可以定義出五個重要的分配，依序是伯努利分配、二項分配、多項分配、幾何分配與負二項分配，其中多項分配嚴格上來說並不屬於伯努利實驗下轄的分配，只是它能完全由二項分配推廣而來。

[Definition 4.2](#def-bernoulli) 給出其中最簡單的伯努利分配: 只進行一次伯努利實驗，並以成功實驗的發生次數作為隨機變數，值域因而只有 $0$ 與 $1$ 兩個點，機率函數為 $p^{x}q^{1-x}$ 這個式子，參數只有成功機率 $p$ 一個。證明分成四個步驟，先驗證機率函數的加總為 $1$ 這件事，再算出期望值與二階原動差都等於成功機率，變異數為 $pq$ 而動差母函數為 $pe^{t}+q$ 這兩個結果。也因為各階原動差都等於成功機率，[Example 4.1](#ex-bernoulli-1) 才能由 mgf 的形式反過來認出這個分配。

另外兩點值得記住: 一是失敗機率 $q=1-p$ 在 $p$ 決定之後就跟著決定，並不是另一個參數；二是對任意隨機變數 $X$ 與任一給定的範圍 $A$ 而言，指標函數 $\mathbb{I}_{\sssig A}(X)$ 都服從成功機率為 $\mathbb{P}(X\in A)$ 的伯努利分配，因為這個做法等於把 $X$ 分成落在 $A$ 之內與之外兩類。

[下一篇](/teaching-topics/ch4-p02-candidate/)介紹二項分配，也就是把同一個伯努利實驗獨立重複 $n$ 次之後，成功次數所服從的分配，屆時也會回答為什麼在只有成敗兩種結果的情境下，要刻意以成功次數定義隨機變數。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
