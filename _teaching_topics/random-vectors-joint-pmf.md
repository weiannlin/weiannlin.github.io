---
title: "隨機向量與離散型聯合分配"
subtitle: "Random Vectors and Discrete Joint Distributions"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 1
order: 301
permalink: /teaching-topics/random-vectors-joint-pmf/
date: 2026-07-24
published: false
listed: false
excerpt: "隨機向量將同一個樣本點產生的多個數值合在一起；聯合 pmf 給出各組取值同時出現的機率，邊際 pmf 則由聯合 pmf 對另一個變數加總得到。"
---

[第二章最後一篇文章](/teaching-topics/continuous-random-variable-transformations/)討論單一隨機變數的函數轉換。不過，一次隨機試驗常會同時產生多個數值。例如，對同一位受試者記錄身高與體重，或對同一位學生記錄兩次考試的成績，都不能只用一個數值保留全部資訊。

若 $X_1,\ldots,X_n$ 定義在同一個機率空間上，則對同一個樣本點 $\omega$，每個隨機變數 $X_i:S\to\mathbb{R}$ 分別給出一個實數 $X_i(\omega)$。將這些函數值依序合在一起，可寫成

$$
\mathbf{X}(\omega)
=
\bigl(X_1(\omega),\ldots,X_n(\omega)\bigr)
$$

其中，各分量都以同一個 $\omega$ 為輸入，但由不同的 $X_i$ 決定其函數值；這些函數值可以相同，也可以不同。

## 隨機向量

<div id="definition-31" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 3.1</div>

令 $(S,\mathcal{F},\mathbb{P})$ 為一個機率空間，並令

$$
\mathbf{X}
=
(X_1,\ldots,X_n):S\longrightarrow\mathbb{R}^n
$$

為定義在 $S$ 上的函數。若對任意 $x_1,\ldots,x_n\in\mathbb{R}$，皆有

$$
\begin{aligned}
\mathbf{X}^{-1}
\left(
\prod_{i=1}^{n}(-\infty,x_i]
\right)
&=
\bigcap_{i=1}^{n}
\lbrace X_i\leqslant x_i\rbrace
\in\mathcal{F}
\end{aligned}
$$

這個交集中的各項條件都針對同一個樣本點 $\omega$，並分別由座標函數 $X_1,\ldots,X_n$ 決定各座標的函數值。此時稱 $\mathbf{X}$ 為一個 $n$ 維**隨機向量 (random vector)**。
</div>

[Definition 2.1](/teaching-topics/random-variables-from-sample-space-to-real-line/#definition-21) 使用數線上的半直線 $(-\infty,x]$ 定義實值隨機變數。此處則把相同條件推廣至 $\mathbb{R}^n$ 中的左下矩形

$$
\prod_{i=1}^{n}(-\infty,x_i]
$$

這些左下矩形生成 $\mathbb{R}^n$ 上的 Borel $\sigma$-域，因此 [Definition 3.1](#definition-31) 等價於要求 $\mathbf{X}$ 為 Borel 可測函數 (Borel measurable function)。

這個條件也等價於要求每個 $X_i$ 都是定義在同一個機率空間上的實值隨機變數。若每個 $X_i$ 都可測，則定義中的交集是有限個事件的交集，因而屬於 $\mathcal{F}$。反過來，若 $\mathbf{X}$ 為 Borel 可測函數，令

$$
\pi_i:\mathbb{R}^n\longrightarrow\mathbb{R}
$$

表示取出第 $i$ 個座標的投影函數。由於 $\pi_i$ 為 Borel 可測函數，且

$$
X_i
=
\pi_i\circ\mathbf{X}
$$

所以每個 $X_i$ 都是實值隨機變數。

隨機向量 $\mathbf{X}$ 的聯合值域定義為

$$
\mathcal{R}_{\mathbf{X}}
=
\bigl\{\mathbf{X}(\omega)\mid\omega\in S\bigr\}
\subseteq
\mathbb{R}^n
$$

往後先以二元隨機向量 $(X,Y)$ 為主，其聯合值域記為 $\mathcal{R}_{XY}\subseteq\mathbb{R}^2$。

<figure id="fig-31" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/random-vector-map.svg" alt="同一個擲骰子樣本點同時經由 X 與 Y 形成平面上的一個向量。樣本點 (3,4) 對應到點數和 7 與點數差絕對值 1。">
  <figcaption><span class="topic-figure__label">Fig. 3.1.</span> 投擲一顆骰子兩次，令 $X$ 為兩次點數和，$Y$ 為兩次點數差的絕對值。樣本點 $(3,4)$ 會被送到 $(X,Y)=(7,1)$；兩個座標來自同一個樣本點，因此保留了聯合關係。</figcaption>
</figure>

隨機向量不必由相同型態的隨機變數組成。例如，一個座標可以是離散型，另一個座標可以具有 pdf。本章先處理離散型座標組成的向量，以及具有聯合 pdf 的向量，再逐步討論更一般的關係。

## 聯合機率質量函數

二元隨機向量 $(X,Y)$ 的聯合值域為

$$
\mathcal{R}_{XY}
=
\bigl\{(X(\omega),Y(\omega))\mid\omega\in S\bigr\}
\subseteq
\mathbb{R}^2
$$

若 $\mathcal{R}_{XY}$ 為有限集合或可數無限集合，則稱 $(X,Y)$ 為**二元離散型隨機向量 (bivariate discrete random vector)**。

<div id="definition-32" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 3.2</div>

令 $(X,Y)$ 為二元離散型隨機向量，其聯合值域為 $\mathcal{R}\_{XY}$。對 $(x,y)\in\mathcal{R}\_{XY}$，定義

$$
p_{XY}(x,y)
=
\mathbb{P}(X=x,Y=y)
$$

並令 $p\_{XY}(x,y)=0$，若 $(x,y)\notin\mathcal{R}\_{XY}$。由機率的非負性、歸一性與可數可加性，$p\_{XY}$ 必滿足

$$
\begin{gathered}
p_{XY}(x,y)\geqslant0
\quad\bigl((x,y)\in\mathcal{R}_{XY}\bigr) \\[0.8em]
\sum_{(x,y)\in\mathcal{R}_{XY}}p_{XY}(x,y)=1
\end{gathered}
$$

稱 $p\_{XY}$ 為 $(X,Y)$ 的**聯合機率質量函數 (joint probability mass function, joint pmf)**。
</div>

式中的逗號表示兩個條件同時成立，因為

$$
\lbrace X=x,Y=y\rbrace
=
\lbrace X=x\rbrace\cap\lbrace Y=y\rbrace
$$

所以 $p_{XY}(x,y)$ 本身就是一個事件的機率。

聯合 pmf 也足以計算由 $(X,Y)$ 所決定的事件機率。對任意集合 $A\subseteq\mathbb{R}^2$，皆有

$$
\mathbb{P}\bigl((X,Y)\in A\bigr)
=
\sum_{(x,y)\in A\cap\mathcal{R}_{XY}}
p_{XY}(x,y)
$$

單變數的公式對 $A\cap\mathcal{R}\_X$ 中的實數 $x$ 加總；二元公式則對 $A\cap\mathcal{R}\_{XY}$ 中的有序對 $(x,y)$ 加總。此時 $A$ 是 $\mathbb{R}^2$ 中的集合，可以是矩形，也可以是其他平面區域。

與 [單變數的 Proposition 2.2](/teaching-topics/discrete-random-variables-pmf/#proposition-22) 相比，條件的形式沒有改變。差別在於，單變數的每個可能取值是實數 $x$，二元隨機向量的每個可能取值則是有序對 $(x,y)$。反過來，只要定義在有限或可數無限集合上的函數滿足這兩項條件，便可形成相應的聯合 pmf。

<div id="proposition-31" class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Proposition 3.1 (Conditions for a Joint pmf)</div>

令 $\mathcal{R}\_{XY}\subseteq\mathbb{R}^2$ 為有限或可數無限集合。若函數 $p\_{XY}:\mathcal{R}\_{XY}\to\mathbb{R}$ 滿足

$$
\begin{gathered}
p_{XY}(x,y)\geqslant0
\quad\bigl((x,y)\in\mathcal{R}_{XY}\bigr) \\[0.8em]
\sum_{(x,y)\in\mathcal{R}_{XY}}p_{XY}(x,y)=1
\end{gathered}
$$

則 $p\_{XY}$ 可作為某個二元離散型隨機向量 $(X,Y)$ 在 $\mathcal{R}\_{XY}$ 上的聯合 pmf。
</div>

<div class="topic-proof" markdown="1">
**Proof.** 取樣本空間 $S=\mathcal{R}\_{XY}$，並令 $\mathcal{F}=2^S$，也就是由 $S$ 的所有子集合所構成的 $\sigma$-域。對每個 $A\in\mathcal{F}$，定義

$$
\mathbb{P}(A)
=
\sum_{(x,y)\in A}p_{XY}(x,y)
$$

非負性與總和為 $1$ 分別給出 $\mathbb{P}(A)\geqslant0$ 與 $\mathbb{P}(S)=1$。為了檢查可數可加性，任取一列兩兩互斥的集合 $A_1,A_2,\ldots\in\mathcal{F}$。由於這些集合彼此沒有重疊，聯集中的每個 $(x,y)$ 恰好只屬於其中一個 $A_n$。因此，對聯集內所有 $(x,y)$ 的加總，可按照 $(x,y)$ 所屬的 $A_n$ 分組；又因各項皆為非負數，這樣分組不會改變總和。由此可得

$$
\begin{aligned}
\mathbb{P}\left(\bigcup_{n=1}^{\infty}A_n\right)
&=
\sum_{(x,y)\in\bigcup_{n=1}^{\infty}A_n}p_{XY}(x,y) \\[0.4em]
&=
\sum_{n=1}^{\infty}\sum_{(x,y)\in A_n}p_{XY}(x,y) \\[0.4em]
&=
\sum_{n=1}^{\infty}\mathbb{P}(A_n)
\end{aligned}
$$

因此，$\mathbb{P}$ 滿足三項機率公理，是定義在 $\mathcal{F}$ 上的機率函數，而 $(S,\mathcal{F},\mathbb{P})$ 構成一個機率空間。對 $\omega=(u,v)\in S$，令 $X(\omega)=u$ 與 $Y(\omega)=v$，故 $(X,Y)(\omega)=\omega$。對任意 $a,b\in\mathbb{R}$，令

$$
I_{a,b}=(-\infty,a]\times(-\infty,b]
$$

則

$$
\begin{aligned}
\lbrace X\leqslant a,Y\leqslant b\rbrace
&=
(X,Y)^{-1}(I_{a,b}) \\[0.4em]
&=
I_{a,b}\cap S
\in\mathcal{F}
\end{aligned}
$$

因此，$(X,Y):S\to\mathbb{R}^2$ 是二元隨機向量。對每個 $(x,y)\in\mathcal{R}\_{XY}$，皆有 $\mathbb{P}(X=x,Y=y)=\mathbb{P}(\lbrace(x,y)\rbrace)=p\_{XY}(x,y)$。若 $(x,y)\notin\mathcal{R}\_{XY}$，則 $\lbrace X=x,Y=y\rbrace=\varnothing$，故 $\mathbb{P}(X=x,Y=y)=0$。因此，在 $\mathcal{R}\_{XY}$ 之外將 $p\_{XY}$ 定義為 $0$ 後，$p\_{XY}$ 確實可作為 $(X,Y)$ 的聯合 pmf。<span class="topic-qed">$\square$</span>
</div>

## 邊際機率質量函數

若現在只想知道 $X$ 的分配，就要把與同一個 $x$ 搭配的所有 $y$ 都考慮進來。對固定的 $x$，事件 $\lbrace X=x\rbrace$ 可分解為互斥事件

$$
\lbrace X=x\rbrace
=
\bigcup_{y\in\mathcal{R}_Y}
\lbrace X=x,Y=y\rbrace
$$

因此，$\mathbb{P}(X=x)$ 等於這些聯合機率的總和。

<div id="definition-33" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 3.3</div>

令 $(X,Y)$ 為二元離散型隨機向量，聯合 pmf 為 $p_{XY}$。定義

$$
\begin{aligned}
p_X(x)
&=
\sum_{y\in\mathcal{R}_Y}p_{XY}(x,y) \\[0.4em]
p_Y(y)
&=
\sum_{x\in\mathcal{R}_X}p_{XY}(x,y)
\end{aligned}
$$

則稱 $p_X$ 與 $p_Y$ 分別為 $X$ 與 $Y$ 的**邊際機率質量函數 (marginal probability mass function, marginal pmf)**。
</div>

加總後，$p_X$ 只以 $x$ 為自變數，描述 $X$ 自身的分配，與 $y$ 無關；$p_Y$ 亦同。這不表示 $X$ 與 $Y$ 獨立，而只表示此時分別考慮其中一個變數的分配。

## 聯合 pmf 與邊際 pmf 的計算

<div id="example-31" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.1 (A Joint pmf on Five Points)</div>

令聯合值域為

$$
\mathcal{R}_{XY}
=
\lbrace(0,1),(0,2),(1,0),(1,1),(2,0)\rbrace
$$

並在 $\mathcal{R}\_{XY}$ 上定義

$$
p_{XY}(x,y)=c(x+2y)
$$

並令其他位置的函數值為 $0$。先求 $c$，使這個函數成為 $(X,Y)$ 的聯合 pmf；再計算 $\mathbb{P}(X\geqslant1,Y\leqslant1)$，並求出 $X$ 與 $Y$ 的邊際 pmf。

依序將 $\mathcal{R}\_{XY}$ 中的五個有序對代入 $x+2y$，相應的值為 $2,4,1,3,2$。由 [Proposition 3.1](#proposition-31) 的總和條件可得

$$
1
=
\sum_{(x,y)\in\mathcal{R}_{XY}}p_{XY}(x,y)
=
c(2+4+1+3+2)
=
12c
$$

因此，$c=1/12$。此時 $p\_{XY}$ 在五個指定點上的函數值皆為非負，在其他位置的函數值為 $0$，且所有可能取值上的總和為 $1$。由 [Proposition 3.1](#proposition-31) 可知，$p\_{XY}$ 確實可作為 $(X,Y)$ 的聯合 pmf。

令 $A=\lbrace(1,0),(1,1),(2,0)\rbrace$，則事件 $\lbrace X\geqslant1,Y\leqslant1\rbrace$ 等同於 $(X,Y)\in A$。由聯合 pmf 的事件機率公式可得

$$
\mathbb{P}\bigl((X,Y)\in A\bigr)
=
\sum_{(x,y)\in A}p_{XY}(x,y)
=
\frac{1+3+2}{12}
=
\frac{1}{2}
$$

把聯合 pmf 與邊際 pmf 一併列入表中，可得

| $Y\backslash X$ | $0$ | $1$ | $2$ | $p_Y(y)$ |
|:---:|:---:|:---:|:---:|:---:|
| $2$ | $4/12$ | $0$ | $0$ | $4/12$ |
| $1$ | $2/12$ | $3/12$ | $0$ | $5/12$ |
| $0$ | $0$ | $1/12$ | $2/12$ | $3/12$ |
| $p_X(x)$ | $6/12$ | $4/12$ | $2/12$ | $1$ |
{: .topic-table--joint-pmf}

例如，把可與 $X=0$ 搭配的所有 $y$ 值加總，可得

$$
\mathbb{P}(X=0)
=
\sum_{y\in\mathcal{R}_Y}p_{XY}(0,y)
=
\frac{0+2+4}{12}
=
\frac{1}{2}
=
p_X(0)
$$

這個計算同時說明，直接由聯合 pmf 加總與由邊際 pmf 讀取 $p_X(0)$，是同一個計算。

$X$ 的完整邊際 pmf 為

$$
p_X(x)
=
\left\{
\begin{array}{c@{\quad}l}
\frac{1}{2}, & x=0,\\[0.35em]
\frac{1}{3}, & x=1,\\[0.35em]
\frac{1}{6}, & x=2,\\[0.35em]
0, & \text{otherwise}
\end{array}
\right.
$$

而 $Y$ 的完整邊際 pmf 為

$$
p_Y(y)
=
\left\{
\begin{array}{c@{\quad}l}
\frac{1}{4}, & y=0,\\[0.35em]
\frac{5}{12}, & y=1,\\[0.35em]
\frac{1}{3}, & y=2,\\[0.35em]
0, & \text{otherwise}
\end{array}
\right.
$$

</div>

表格內部的每一格記錄 $X$ 與 $Y$ 同時取特定值的機率。最下方與最右側則分別把同一欄或同一列的機率加總，因此稱為邊際分配。

## 本篇小結

隨機向量把同一個樣本點所產生的多個數值放在一起。對二元離散型隨機向量，聯合 pmf 給出每一組 $(x,y)$ 同時出現的機率，而一般事件的機率可由事件範圍內的聯合 pmf 加總得到。

若只關心其中一個變數，則將另一個變數的所有可能值加總，便得到邊際 pmf。邊際分配保留單一變數的機率資訊，但不再保留兩個變數如何搭配。

[下一篇文章](/teaching-topics/joint-cumulative-distribution-functions/)會改由門檻事件 $\lbrace X\leqslant x,Y\leqslant y\rbrace$ 累積機率，定義聯合累積分配函數。

## 參考文獻與延伸閱讀

- 黃文璋，2003，《機率論》，初版，華泰文化。
- 黃文璋，2003，《數理統計》，初版，華泰文化。
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Joseph K. Blitzstein and Jessica Hwang. 2019. *Introduction to Probability*. 2nd ed. Chapman and Hall/CRC.
