---
title: "伯努利實驗與伯努利分配"
subtitle: "Bernoulli Trials and the Bernoulli Distribution"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 4
topic: 1
order: 401
permalink: /lecture-notes/bernoulli-trials-and-distribution/
date: 2026-08-12
published: false
excerpt: "伯努利實驗是僅有成功與失敗兩種出象、成功機率固定且各次獨立的隨機實驗。本篇介紹單次實驗對應的伯努利分配，推導其期望值 $p$ 與變異數 $pq$ 及動差母函數，並說明它與事件指標函數的對應。"
---

[上一篇](/lecture-notes/order-statistics-examples/)以四道例題演練順序統計量的分配，並給出其抽樣分配的 cdf，第三章到此結束。第三章把隨機變數的概念推廣到[隨機向量](/lecture-notes/random-vectors-joint-pmf/#def-random-vector)，處理的是多個隨機變數合在一起時的聯合分配，以及變數與變數之間的關係。第一章到第三章所建立的，都是機率與隨機變數的一般性定義與性質；本章要談的則是幾個特別常見的機率分配模型。

統計學與相關學科在處理實際問題時，常依問題特性選取相符的機率分配建立模型。本章介紹的常見機率分配模型，或因應用廣泛，或因結構簡潔、運算性質良好，皆是學習後續章節與進階統計課程的基礎工具。

依隨機變數型態，這些模型可分為**離散機率分配模型**與**連續機率分配模型**；若依模型結構與推導脈絡區分，則可歸為**伯努利實驗相關分配**、**卜瓦松過程相關分配**、**貝塔相關分配**及**常態相關分配**四大類別。學習各分配時，除機率函數外，亦應掌握其參數意義、適用情境與衍生性質，其中部分性質已在前幾章先行出現。

本篇是第四章的第一篇，先給出伯努利實驗的定義與其下轄的各個分配，再進入其中最簡單的伯努利分配。

## 伯努利實驗

<div id="def-ber-trial" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 4.1 (伯努利實驗, Bernoulli trial)</div>

若一隨機實驗滿足以下三點，則我們稱此實驗為**伯努利實驗 <span lang="en">(Bernoulli trial)</span>**:

<ol class="topic-list-paren">
  <li>實驗可能的出象 <span lang="en">(outcomes)</span> 可被分為兩個互斥事件，定義為「成功 <span lang="en">(success)</span>」與「失敗 <span lang="en">(failure)</span>」。</li>
  <li>每次實驗的成功機率 $p$ 皆固定。</li>
  <li>實驗與實驗間，彼此獨立。</li>
</ol>

</div>

伯努利實驗由伯努利 (Jacob Bernoulli, 1655-1705) 提出並以其姓氏命名；他在研究連續複利問題時亦發現尤拉數 $e=\lim_{n\to\infty}\left(1+\frac{1}{\,n\,}\right)^{n}$ 這個常數，並提出最早版本的大數法則 <span lang="en">(law of large numbers)</span>。由於每次實驗僅有成敗兩種結果，伯努利實驗又稱為成敗實驗。此處所謂「成功」與「失敗」並無正反或褒貶涵義，僅將研究者關心的出象類別稱為成功，其餘類別稱為失敗。

基於伯努利實驗的特性，可進一步定義出下列常見分配:

<ol class="topic-list-paren">
  <li>伯努利分配 <span lang="en">(Bernoulli distribution)</span></li>
  <li>二項分配 <span lang="en">(binomial distribution)</span></li>
  <li>多項分配 <span lang="en">(multinomial distribution)</span></li>
  <li>幾何分配 <span lang="en">(geometric distribution)</span></li>
  <li>負二項分配 <span lang="en">(negative binomial distribution)</span></li>
</ol>

嚴格而言，多項分配並非直接建立在伯努利實驗之上，但因完全可由二項分配推廣而來，故一併列於此處。以下依序介紹這些分配及其間的關係。

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

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\mathbb{E}(X)=p,\ \ \mathrm{Var}(X)=p(1-p)=pq\\[0.45em]
M_{\sssig X}(t)=pe^{t}+(1-p)=pe^{t}+q,\ t\in\mathbb{R}
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{E}(X)=p,\\[0.35em]
\mathrm{Var}(X)=p(1-p)=pq,\\[0.35em]
M_{\sssig X}(t)=pe^{t}+(1-p)=pe^{t}+q,\ t\in\mathbb{R}
\end{gathered}
$$

</div>

</div>

伯努利分配有一些地方需要注意:

(1) 我們證明其機率函數為一個合法的機率函數與期望值、變異數及動差母函數如下:
{: .topic-paren-item}

<div class="topic-proof" markdown="1">
**Proof.**

先驗證機率函數的加總為 <span class="text-nowrap">$1$，</span>即

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
\begin{gathered}
\mathbb{E}(X)=\sum_{x=0}^{1}xp^{x}(1-p)^{1-x}=0\times(1-p)+1\times p=p\\[0.45em]
\mathbb{E}\bigl(X^{2}\bigr)=\sum_{x=0}^{1}x^{2}p^{x}(1-p)^{1-x}=0^{2}\times(1-p)+1^{2}\times p=p
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\sum_{x=0}^{1}xp^{x}(1-p)^{1-x}\\[0.45em]
&=0\times(1-p)+1\times p=p
\end{aligned}
$$

$$
\begin{aligned}
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

由於 $X$ 僅取值 $0$ 與 <span class="text-nowrap">$1$，</span>對任意正整數 $k$ 皆有 <span class="text-nowrap">$X^{k}=X$，</span>故伯努利分配的所有階原動差皆等於成功機率 <span class="text-nowrap">$p$；</span>此性質亦曾於 [Example 2.32 <span lang="en">(Continued)</span>](/lecture-notes/uniqueness-of-the-mgf/#ex-constant-moments-bernoulli) 出現。

</div>

(2) 一旦成功機率 $p$ 的值確定，失敗機率 $q=1-p$ 亦隨之完全決定；換言之，**$q$ 並不是另一個參數**。
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

將任意隨機變數 $X$ 依其取值落於集合 $A$ 內或外歸為兩類，即構成一次以「<span class="text-nowrap">$X\in A$</span>」為成功事件的伯努利實驗，指標函數 $\mathbb{I}_{\sssig A}(X)$ 正對應此實驗的成功次數。

</div>

<div id="ex-bernoulli-1" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.1</div>

<div lang="en" markdown="1">
Let the moment-generating function of a random variable $X$ be <span class="text-nowrap">$M_{\sssig X}(t)=0.25+0.75e^{t}$.</span> What are the expectation and variance of <span class="text-nowrap">$X$?</span>
</div>

由 [mgf 的唯一性](/lecture-notes/uniqueness-of-the-mgf/#thm-mgf-uniqueness)可知

<div class="topic-math-follow-before" markdown="1">

$$
X\sim\mathrm{Ber}\bigl(p=0.75\bigr)
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop topic-math-follow" markdown="1">

$$
\begin{aligned}
&\Longrightarrow\ \mathbb{E}(X)=p=0.75\\[0.45em]
&\Longrightarrow\ \mathrm{Var}(X)=p(1-p)=0.75\times0.25=0.1875
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile topic-math-follow" markdown="1">

$$
\begin{aligned}
&\Longrightarrow\ \mathbb{E}(X)=p=0.75\\[0.5em]
&\Longrightarrow\ \begin{aligned}[t]
\mathrm{Var}(X)&=p(1-p)\\[0.35em]
&=0.75\times0.25=0.1875
\end{aligned}
\end{aligned}
$$

</div>

</div>

單次實驗僅有成功與失敗兩種結果，何以仍刻意將 $X$ 定義為伯努利實驗中的「成功次數」？此一定義旨在銜接重複多次實驗的情境，接下來的二項分配便會給出解答。

## 本篇小結

[Definition 4.1](#def-ber-trial) 以三個條件界定伯努利實驗，要求實驗可能的出象分成成功與失敗兩個互斥事件、每次實驗的成功機率 $p$ 均為固定值，以及實驗與實驗之間彼此獨立。這裡的成功與失敗並沒有正面與反面的意義，只是研究者對兩類出象的稱呼。由伯努利實驗可以定義出五個重要的分配，依序是伯努利分配、二項分配、多項分配、幾何分配與負二項分配，其中多項分配嚴格上來說並不屬於伯努利實驗下轄的分配，只是它能完全由二項分配推廣而來。

[Definition 4.2](#def-bernoulli) 給出其中最簡單的伯努利分配，也就是只進行一次伯努利實驗，並以成功實驗的發生次數作為隨機變數，值域因而只有 $0$ 與 $1$ 兩個點，機率函數為 $p^{x}q^{1-x}$ 這個式子，參數只有成功機率 $p$ 一個。證明分成四個步驟，先驗證機率函數的加總為 $1$ 這件事，再算出期望值與二階原動差都等於成功機率，變異數為 $pq$ 而動差母函數為 $pe^{t}+q$ 這兩個結果。也因為各階原動差都等於成功機率，[Example 4.1](#ex-bernoulli-1) 才能由 mgf 形式反推此分配。

另外兩點也值得留意，其一是失敗機率 $q=1-p$ 在 $p$ 決定之後就跟著決定，並不是另一個參數；其二是對任意隨機變數 $X$ 與任一給定的範圍 $A$ 而言，指標函數 $\mathbb{I}_{\sssig A}(X)$ 都服從成功機率為 $\mathbb{P}(X\in A)$ 的伯努利分配，因為這個做法等於把 $X$ 分成落在 $A$ 之內與之外兩類。

[下一篇](/lecture-notes/binomial-distribution/)介紹二項分配，也就是把同一伯努利實驗獨立重複 $n$ 次後，成功次數所服從的分配，屆時也會回答為什麼在只有成敗兩種結果時，要刻意以成功次數定義隨機變數。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
