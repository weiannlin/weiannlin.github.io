---
title: "離散型隨機變數與機率質量函數"
subtitle: "Discrete Random Variables and Probability Mass Functions"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 2
order: 202
permalink: /teaching-topics/discrete-random-variables-pmf/
date: 2026-05-19
published: false
listed: false
excerpt: "離散型隨機變數的機率質量函數在值域上記錄每一個點的單點機率，在值域之外一律為 $0$。它須滿足三項性質: 函數值介於 $0$ 與 $1$ 之間、在值域上的總和為 $1$，以及 $X$ 落在任一集合中的機率等於該集合與值域交集上各單點機率之和。這三項性質恰好對應機率的三大公理。反過來，Proposition 2.1 說明非負且總和為 $1$ 的函數便可作為某個離散型隨機變數的 pmf。"
---

[上一篇文章](/teaching-topics/random-variables-from-sample-space-to-real-line/)以隨機變數把樣本點送到數線上，並依值域中元素的個數與機率的表示方式，把隨機變數分為離散型與連續型兩類。本篇處理離散型，並由 $\mathbb{P}(X=x)$ 這個單點機率談起。

離散型隨機變數的值域可以逐一列出，機率也就落在這些點上。只要把值域中每一個點上的機率記下來，$X$ 落在任一集合中的機率都能寫成加總。見下列定義。

## 機率質量函數的定義

<span id="definition-23"></span>
<div id="def-pmf" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.3</div>

若 $X$ 為定義於機率空間 $(S,\mathcal{F},\mathbb{P})$ 上之**離散型**隨機變數，其值域為 $\mathcal{R}_{\sssig X}$，則定義函數

$$
p_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
\mathbb{P}(X=x), & \forall x\in\mathcal{R}_{\sssig X}\\[0.4em]
0, & \forall x\notin\mathcal{R}_{\sssig X}
\end{array}
\right.
$$

若 $p_{\sssig X}(x)$ 滿足以下性質，則稱 $p_{\sssig X}(x)$ 為 $X$ 的**機率質量函數 (probability mass function, pmf)**:

<ol class="topic-list-paren">
  <li>對任意 $x\in\mathcal{R}_{\sssig X}$，皆有
  $$
  0\leqslant p_{\sssig X}(x)\leqslant 1
  $$</li>
  <li>$X$ 的取值落在值域中的機率為
  $$
  \mathbb{P}(X\in\mathcal{R}_{\sssig X})=\sum_{x\in\mathcal{R}_{\sssig X}}p_{\sssig X}(x)=1
  $$</li>
  <li>對任意 $A\subseteq\mathbb{R}$，皆有
  $$
  \mathbb{P}(X\in A)=\sum_{x\in A\cap\mathcal{R}_{\sssig X}}p_{\sssig X}(x)
  $$</li>
</ol>

</div>

在**機率質量函數 (probability mass function)** 的定義中，$\mathbb{P}(X=x)$ 的部分事實上應寫為 $\mathbb{P}\bigl(\lbrace X(\omega)=x\rbrace\bigr)$ 或是 $\mathbb{P}\bigl(\lbrace\,\omega\mid X(\omega)=x\,\rbrace\bigr)$ 較為完整，其理由如同前述，因為機率函數是被定義在集合上的函數，且 $\lbrace\,\omega\mid X(\omega)=x\,\rbrace$ 的表示法才是一個集合。然而為了方便書寫及表示，將其簡寫為 $\mathbb{P}(X=x)$ 亦是被普遍接受的。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

許多教科書中亦將 $p_{\sssig X}(x)$ 寫成 $f_{\sssig X}(x)$，這樣的寫法可以與連續型變數的機率密度函數 (probability density function, pdf) 共通，通稱為機率函數 (probability function)。此處的機率函數是 pmf 與 pdf 的統稱，與第一章[指稱 $\mathbb{P}(\cdot)$ 的機率函數](/teaching-topics/event-families-sigma-fields/#term-probability-function)所指不同。

</div>

另一個需要注意的點是，$\mathbb{P}(X=x)$ **就是機率**。我們可以將其理解為，機率質量函數只有在其值域的點上才有機率，這個概念就好像在特定的點上才有「質量」一般，故被稱作機率質量函數，而值域的點亦被稱作「質點」。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

由於其定義就是機率，故當然應滿足[機率三大公理](/teaching-topics/event-families-sigma-fields/#definition-probability-space)，即分別對應到上述定義中的三點性質。

</div>

<span id="example-22"></span>
<div id="ex-two-ball-sum" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.2 (Sum of the Numbers on Two Drawn Balls)</div>

若箱中有四顆大小形狀完全相同、分別編號 $0$ 至 $3$ 的球，若 $X$ 表示隨機從中一次抽取兩顆球的號碼總和，則試列出其機率質量函數，並求其號碼的總和為 $3$ 的機率為何？

可先列出樣本空間

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
S=\lbrace(0,1),(0,2),(0,3),(1,2),(1,3),(2,3)\rbrace
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
S=\lbrace(0,1),(0,2),(0,3),\\[0.4em]
(1,2),(1,3),(2,3)\rbrace
\end{gathered}
$$

</div>

及 $X$ 之值域

$$
\mathcal{R}_{\sssig X}=\lbrace1,2,3,4,5\rbrace
$$

依題意可知抽到任一球之機率應相等，故樣本空間有均等可能性假設，則其 pmf 為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
p_{\sssig X}(1)&=\mathbb{P}(X=1)=\mathbb{P}\bigl(\lbrace(0,1)\rbrace\bigr)=\frac{1}{6}\\[0.4em]
p_{\sssig X}(2)&=\mathbb{P}(X=2)=\mathbb{P}\bigl(\lbrace(0,2)\rbrace\bigr)=\frac{1}{6}\\[0.4em]
p_{\sssig X}(3)&=\mathbb{P}(X=3)=\mathbb{P}\bigl(\lbrace(0,3),(1,2)\rbrace\bigr)=\frac{2}{6}=\frac{1}{3}\\[0.4em]
p_{\sssig X}(4)&=\mathbb{P}(X=4)=\mathbb{P}\bigl(\lbrace(1,3)\rbrace\bigr)=\frac{1}{6}\\[0.4em]
p_{\sssig X}(5)&=\mathbb{P}(X=5)=\mathbb{P}\bigl(\lbrace(2,3)\rbrace\bigr)=\frac{1}{6}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig X}(1)&=\mathbb{P}(X=1)\\[0.3em]
&=\mathbb{P}\bigl(\lbrace(0,1)\rbrace\bigr)=\frac{1}{6}\\[0.7em]
p_{\sssig X}(2)&=\mathbb{P}(X=2)\\[0.3em]
&=\mathbb{P}\bigl(\lbrace(0,2)\rbrace\bigr)=\frac{1}{6}\\[0.7em]
p_{\sssig X}(3)&=\mathbb{P}(X=3)\\[0.3em]
&=\mathbb{P}\bigl(\lbrace(0,3),(1,2)\rbrace\bigr)\\[0.3em]
&=\frac{2}{6}=\frac{1}{3}\\[0.7em]
p_{\sssig X}(4)&=\mathbb{P}(X=4)\\[0.3em]
&=\mathbb{P}\bigl(\lbrace(1,3)\rbrace\bigr)=\frac{1}{6}\\[0.7em]
p_{\sssig X}(5)&=\mathbb{P}(X=5)\\[0.3em]
&=\mathbb{P}\bigl(\lbrace(2,3)\rbrace\bigr)=\frac{1}{6}
\end{aligned}
$$

</div>

故 $X$ 的 pmf 為

$$
p_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{1}{6}, & x=1,2,4,5\\[0.6em]
\dfrac{1}{3}, & x=3\\[0.6em]
0, & \text{otherwise}
\end{array}
\right.
$$

所求的號碼總和為 $3$ 的機率即

$$
p_{\sssig X}(3)=\frac{1}{3}\fallingdotseq0.3333
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這題的解法是為了協助讀者將 pmf 與過去所學的古典機率結合，但事實上並不需要每次都這麼麻煩地從樣本空間開始列起。爾後的題目我們將寫得比較簡潔。

</div>

## 由非負性與總和條件判定 pmf

[Definition 2.3](#def-pmf) 是由 $X$ 出發的: 先有隨機變數，才有它的 pmf，定義中所列的三項性質都是 pmf 必須滿足的條件。反過來看，若已知一個定義在有限或可數無限集合上的函數，且它非負、總和為 $1$，則這個函數便可作為某個離散型隨機變數的 pmf。

<span id="proposition-22"></span>
<div id="prop-pmf-existence-conditions" class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Proposition 2.1 (Conditions for a pmf)</div>

令 $\mathcal{R}\subseteq\mathbb{R}$ 為有限或可數無限集合。若函數 $p\colon\mathcal{R}\to\mathbb{R}$ 滿足

$$
\begin{gathered}
p(x)\geqslant0,\quad\forall x\in\mathcal{R}\\[0.7em]
\sum_{x\in\mathcal{R}}p(x)=1
\end{gathered}
$$

則存在一個離散型隨機變數 $X$，其值域為 $\mathcal{R}$，且 $p$ 在 $\mathcal{R}$ 之外補以 $0$ 後即為 $X$ 的 pmf。

</div>

<div class="topic-proof" markdown="1">
**Proof.** 取樣本空間 $S=\mathcal{R}$，並令 $\mathcal{F}=2^{S}$，也就是由 $S$ 的所有子集合所構成的 $\sigma$-域。對每個 $A\in\mathcal{F}$，定義

$$
\mathbb{P}(A)=\sum_{x\in A}p(x)
$$

非負性與總和為 $1$ 分別給出 $\mathbb{P}(A)\geqslant0$ 與 $\mathbb{P}(S)=1$。為了檢查可數可加性，任取一列兩兩互斥的集合 $A_1,A_2,\ldots\in\mathcal{F}$。由於這些集合彼此沒有重疊，聯集中的每個 $x$ 恰好只屬於其中一個 $A_n$；又因各項皆為非負數，依 $x$ 所屬的 $A_n$ 分組不會改變總和。由此可得

$$
\begin{aligned}
\mathbb{P}\left(\bigcup_{n=1}^{\infty}A_n\right)
&=\sum_{x\in\bigcup_{n=1}^{\infty}A_n}p(x)\\[0.4em]
&=\sum_{n=1}^{\infty}\sum_{x\in A_n}p(x)\\[0.4em]
&=\sum_{n=1}^{\infty}\mathbb{P}(A_n)
\end{aligned}
$$

因此 $\mathbb{P}$ 滿足[機率三大公理](/teaching-topics/event-families-sigma-fields/#definition-probability-space)，是定義在 $\mathcal{F}$ 上的機率函數，而 $(S,\mathcal{F},\mathbb{P})$ 構成一個機率空間。再令 $X(\omega)=\omega$，則對任意 $t\in\mathbb{R}$，皆有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lbrace X\leqslant t\rbrace=X^{-1}\bigl((-\infty,t]\bigr)=(-\infty,t]\cap S\in\mathcal{F}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\lbrace X\leqslant t\rbrace&=X^{-1}\bigl((-\infty,t]\bigr)\\[0.4em]
&=(-\infty,t]\cap S\in\mathcal{F}
\end{aligned}
$$

</div>

故 $X\colon S\to\mathbb{R}$ 依 [Definition 2.1](/teaching-topics/random-variables-from-sample-space-to-real-line/#def-random-variable) 為一隨機變數，其值域為 $\mathcal{R}$，且因 $\mathcal{R}$ 為有限或可數無限集合，依 [Definition 2.2](/teaching-topics/random-variables-from-sample-space-to-real-line/#def-support-classification) 可知 $X$ 為離散型。對每個 $x\in\mathcal{R}$，皆有 $\mathbb{P}(X=x)=\mathbb{P}(\lbrace x\rbrace)=p(x)$；若 $x\notin\mathcal{R}$，則 $\lbrace X=x\rbrace=\varnothing$，故 $\mathbb{P}(X=x)=0$。因此在 $\mathcal{R}$ 之外補以 $0$ 之後，$p$ 確為 $X$ 的 pmf。[Definition 2.3](#def-pmf) 所列的三項性質也都成立: 由 $p(x)\geqslant0$ 與 $p(x)=\mathbb{P}(\lbrace x\rbrace)\leqslant\mathbb{P}(S)=1$ 得第 (1) 項；由 $\sum_{x\in\mathcal{R}}p(x)=1$ 得第 (2) 項；而對任意 $A\subseteq\mathbb{R}$，皆有 $\mathbb{P}(X\in A)=\mathbb{P}(A\cap S)=\sum_{x\in A\cap\mathcal{R}}p(x)$，此即第 (3) 項。<span class="topic-qed">$\square$</span>
</div>

<div id="ex-geometric-pmf" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.3 (A pmf with an Unknown Constant)</div>

<div lang="en" markdown="1">
Suppose that the probability mass function of a random variable $X$ is

$$
p_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
c\left(\dfrac{1}{2}\right)^{x}, & x=1,2,\ldots\\[0.6em]
0, & \text{otherwise}
\end{array}
\right.
$$

where $c$ is a constant. Find $c$ and the probability <span class="text-nowrap">$\mathbb{P}(X=5)$.</span>
</div>

由 pmf 之性質知道

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
1=\sum_{x=1}^{\infty}c\left(\frac{1}{2}\right)^{x}
=c\sum_{x=1}^{\infty}\left(\frac{1}{2}\right)^{x}
=c\cdot\frac{\frac{1}{2}}{1-\frac{1}{2}}
=c
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
1&=\sum_{x=1}^{\infty}c\left(\frac{1}{2}\right)^{x}
=c\sum_{x=1}^{\infty}\left(\frac{1}{2}\right)^{x}\\[0.4em]
&=c\cdot\frac{\frac{1}{2}}{1-\frac{1}{2}}=c
\end{aligned}
$$

</div>

故 $c=1$。由於 $c=1>0$，可知 $p_{\sssig X}(x)\geqslant0$ 對一切 $x=1,2,\ldots$ 皆成立，[Proposition 2.1](#prop-pmf-existence-conditions) 的兩項條件都得到滿足，故 $p_{\sssig X}$ 確實是一個 pmf。以此可計算

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X=5)=p_{\sssig X}(5)=\frac{1}{2^{5}}=\frac{1}{32}=0.03125
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X=5)&=p_{\sssig X}(5)=\frac{1}{2^{5}}\\[0.4em]
&=\frac{1}{32}=0.03125
\end{aligned}
$$

</div>

</div>

<div id="ex-recursive-pmf" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.4 (A pmf Determined by a Recursion)</div>

<div lang="en" markdown="1">
Suppose that a random variable $X$ takes values in $\lbrace0,1,2,3,\ldots\rbrace$ and that its distribution depends on a parameter $\theta$. Suppose further that for $x=1,2,3,\ldots$ its probabilities satisfy the recursion relationship <span class="text-nowrap">$\mathbb{P}(X=x)=\frac{\theta}{x}\mathbb{P}(X=x-1)$.</span> Find the probability mass function of <span class="text-nowrap">$X$.</span>
</div>

由題意之遞迴 (recursion) 性質可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X=x)&=\frac{\theta}{x}\,\mathbb{P}(X=x-1)\\[0.4em]
&=\frac{\theta}{x}\cdot\frac{\theta}{x-1}\,\mathbb{P}(X=x-2)\\[0.4em]
&=\cdots=\frac{\theta^{x}}{x!}\,\mathbb{P}(X=0)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(X=x)=\frac{\theta}{x}\,\mathbb{P}(X=x-1)\\[0.4em]
&=\frac{\theta}{x}\cdot\frac{\theta}{x-1}\,\mathbb{P}(X=x-2)\\[0.4em]
&=\cdots=\frac{\theta^{x}}{x!}\,\mathbb{P}(X=0)
\end{aligned}
$$

</div>

且由 pmf 之性質可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
1&=\sum_{x\in\mathcal{R}_{\sssig X}}p_{\sssig X}(x)
=\sum_{x=0}^{\infty}\mathbb{P}(X=x)
=\sum_{x=0}^{\infty}\frac{\theta^{x}}{x!}\,\mathbb{P}(X=0)\\[0.4em]
&=\mathbb{P}(X=0)\sum_{x=0}^{\infty}\frac{\theta^{x}}{x!}
=\mathbb{P}(X=0)\,e^{\theta}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
1&=\sum_{x\in\mathcal{R}_{\sssig X}}p_{\sssig X}(x)=\sum_{x=0}^{\infty}\mathbb{P}(X=x)\\[0.4em]
&=\sum_{x=0}^{\infty}\frac{\theta^{x}}{x!}\,\mathbb{P}(X=0)\\[0.4em]
&=\mathbb{P}(X=0)\sum_{x=0}^{\infty}\frac{\theta^{x}}{x!}\\[0.4em]
&=\mathbb{P}(X=0)\,e^{\theta}
\end{aligned}
$$

</div>

故 $\mathbb{P}(X=0)=e^{-\theta}$，代回上式可得 $X$ 的 pmf 為

$$
p_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{e^{-\theta}\theta^{x}}{x!}, & x=0,1,2,\ldots\\[0.7em]
0, & \text{otherwise}
\end{array}
\right.
$$

題幹並未指定 $\theta$ 的範圍，這一點可由 pmf 的非負性補出。由 $\mathbb{P}(X=0)=e^{-\theta}>0$ 與 $p_{\sssig X}(1)=\theta e^{-\theta}\geqslant0$ 可得 $\theta\geqslant0$；而 $\theta=0$ 時 $\mathbb{P}(X=0)=1$，$X$ 退化為恆取 $0$ 的隨機變數。故本題的參數範圍為 <span class="text-nowrap">$\theta>0$。</span>

</div>

## 本篇小結

離散型隨機變數的值域可以逐一列出，機率也集中在這些點上。pmf 以 $p_{\sssig X}(x)=\mathbb{P}(X=x)$ 記錄值域中每一個點的單點機率，在值域之外則取 $0$。它的三項性質分別是: 函數值介於 $0$ 與 $1$ 之間、在值域上的總和為 $1$，以及

$$
\mathbb{P}(X\in A)=\sum_{x\in A\cap\mathcal{R}_{\sssig X}}p_{\sssig X}(x)
$$

由於 $\mathbb{P}(X=x)$ 本身就是機率，這三項性質恰好對應機率的三大公理。反過來，一個定義在有限或可數無限集合上的函數，只要非負且總和為 $1$，便可作為某個離散型隨機變數的 pmf。

pmf 只適用於離散型隨機變數。下一篇[累積分配函數與機率密度函數](/teaching-topics/cdf-and-pdf/)改由 $\mathbb{P}(X\leqslant x)$ 出發，先給出對兩種型態都適用的累積分配函數，再回到連續型，說明機率如何由密度函數在區間上的積分取得。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- 黃文璋，2003，《數理統計》，初版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Joseph K. Blitzstein and Jessica Hwang. 2019. *Introduction to Probability*. 2nd ed. Chapman and Hall/CRC.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Patrick Billingsley. 1995. *Probability and Measure*. 3rd ed. Wiley.
