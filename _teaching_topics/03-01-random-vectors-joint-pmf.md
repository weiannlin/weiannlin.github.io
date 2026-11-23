---
title: "隨機向量與聯合機率質量函數"
subtitle: "Random Vectors and Joint Probability Mass Functions"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 1
order: 301
permalink: /lecture-notes/random-vectors-joint-pmf/
date: 2026-08-12
published: true
excerpt: "把定義在同一機率空間上的 $n$ 個隨機變數合為向量函數，即構成隨機向量。本篇介紹隨機向量的定義，以及二元離散型的聯合機率質量函數、三項基本性質與邊際機率質量函數的求法。"
---

[上一篇](/lecture-notes/many-to-one-transformations/)以三道例題處理了非一對一的函數轉換，第二章到此告一段落。第二章所討論的[隨機變數](/lecture-notes/random-variables-and-pmf/#def-random-variable) <span lang="en">(random variable)</span> 都只有一維，但這個概念當然不僅限於一維 <span lang="en">($1$-dimension)</span>，我們可以將其擴展至二維 <span lang="en">($2$-dimension)</span> 以上的多維 <span lang="en">(multi-dimension)</span> 空間，代表的意義也會隨之不同。

第一章討論兩個事件時，可依其關係歸納出[互斥、獨立](/lecture-notes/independence-and-conditional-independence/#互斥與獨立)等觀念；第二章則將隨機變數定義為樣本空間映射到實數的函數。若將同一個樣本點分別映射至兩個實數，即構成二元隨機變數；推廣至多個隨機變數後，我們便能如同分析多個事件一般，進一步討論隨機變數之間的關係。由多個隨機變數構成的向量稱為**隨機向量**，其定義如下。

## 隨機向量

<div id="def-random-vector" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 3.1 (隨機向量, random vector)</div>

令 $(S,\mathcal{F},\mathbb{P})$ 為一機率空間，$X_1,X_2,\ldots,X_n$ 為定義在同一機率空間中的隨機變數，而下面的向量函數 <span lang="en">(vector function)</span>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\boldsymbol{X}(\omega)=\bigl(\,X_1(\omega),X_2(\omega),\ldots,X_n(\omega)\,\bigr)\colon S\to\mathbb{R}^{n}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\boldsymbol{X}(\omega)=\bigl(\,X_1(\omega),X_2(\omega),\ldots,X_n(\omega)\,\bigr)\\[0.45em]
\boldsymbol{X}\colon S\to\mathbb{R}^{n}
\end{gathered}
$$

</div>

為由 $X_1,X_2,\ldots,X_n$ 所構成，且滿足對任意 $x_1,x_2,\ldots,x_n\in\mathbb{R}$ 而言，下面的集合都是事件

$$
\lbrace\,\omega\mid\omega\in S,\ X_i(\omega)\leqslant x_i,\ i=1,2,\ldots,n\,\rbrace\in\mathcal{F}
$$

則稱 $\boldsymbol{X}$ 為一個定義於 $S$ 的**隨機向量 (random vector)**。

</div>

隨機向量是一個向量函數，其有一些特殊的性質需要注意。

(1) 在部分的教科書上，隨機向量 $\boldsymbol{X}$ 會以其反映射 <span lang="en">(inverse mapping)</span> $\boldsymbol{X}^{-1}(\cdot)$ 定義，並定義以下的集合
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
I=\bigl\lbrace\,(\,t_1,t_2,\ldots,t_n\,)\mid-\infty<t_i\leqslant x_i,\ x_i\in\mathbb{R},\ i=1,2,\ldots,n\,\bigr\rbrace
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
I=\bigl\lbrace\,&(\,t_1,t_2,\ldots,t_n\,)\mid\\[0.35em]
&\qquad-\infty<t_i\leqslant x_i,\ x_i\in\mathbb{R},\\[0.35em]
&i=1,2,\ldots,n\,\bigr\rbrace
\end{aligned}
$$

</div>

則 $\boldsymbol{X}\colon S\to\mathbb{R}^{n}$ 滿足下式
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\boldsymbol{X}^{-1}(I)=\lbrace\,\omega\mid X_i(\omega)\leqslant x_i,\ i=1,2,\ldots,n\,\rbrace=\bigcap_{i=1}^{n}\lbrace\,\omega\mid X_i(\omega)\leqslant x_i\,\rbrace\in\mathcal{F}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\boldsymbol{X}^{-1}(I)&=\lbrace\,\omega\mid X_i(\omega)\leqslant x_i,\\[0.2em]
&\qquad i=1,2,\ldots,n\,\rbrace\\[0.45em]
&=\bigcap_{i=1}^{n}\lbrace\,\omega\mid X_i(\omega)\leqslant x_i\,\rbrace\in\mathcal{F}
\end{aligned}
$$

</div>

這兩個等價定義都在說明同一件事情，亦即對任意實數組 $x_1,x_2,\ldots,x_n$ 而言，**使 $X_1(\omega)\leqslant x_1,X_2(\omega)\leqslant x_2,\ldots,X_n(\omega)\leqslant x_n$ 同時成立的樣本點集合，必須是可定義機率的事件**。
{: .topic-paren-cont}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

依單一隨機變數的原像等價定義，對每個隨機變數 $X_i$ 皆有下式

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
X_i^{-1}\bigl((-\infty,x_i]\bigr)=\lbrace\,\omega\mid X_i(\omega)\leqslant x_i\,\rbrace\in\mathcal{F},\quad i=1,2,\ldots,n
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
X_i^{-1}\bigl((-\infty,x_i]\bigr)&=\lbrace\,\omega\mid X_i(\omega)\leqslant x_i\,\rbrace\in\mathcal{F},\\[0.35em]
&\qquad i=1,2,\ldots,n
\end{aligned}
$$

</div>

因 $\sigma$-域 $\mathcal{F}$ 對交集封閉，若 $A_i\in\mathcal{F}$ 對 $i=1,2,\ldots,n$ 皆成立，則有

$$
\bigcap_{i=1}^{n}A_i\in\mathcal{F}
$$

因此只要 $X_1,X_2,\ldots,X_n$ 皆為定義於同一機率空間 $(S,\mathcal{F},\mathbb{P})$ 上的隨機變數，其所構成的向量

$$
\boldsymbol{X}=\bigl(\,X_1(\omega),X_2(\omega),\ldots,X_n(\omega)\,\bigr)
$$

即必為隨機向量。

</div>

(2) $\boldsymbol{X}$ 為一函數，定義域 (domain) 是樣本空間 <span class="text-nowrap">$S$、</span>對應域 <span lang="en">(codomain)</span> 是 $n$ 維實數空間 <span class="text-nowrap">$\mathbb{R}^{n}$，</span>而**聯合值域 (joint range)** 記為 <span class="text-nowrap">$\mathcal{R}\_{\boldsymbol{X}}$，</span>為 $n$ 維實數空間 $\mathbb{R}^{n}$ 的子集。
{: .topic-paren-item}

(3) 本系列往後多半只關注 $n=2$ 的情況，並可能稱其為多元隨機變數。
{: .topic-paren-item}

為銜接第二章的架構，我們在隨機向量 (或稱多元隨機變數) 中仍分離散型與連續型兩類，分別探討其機率函數與分配函數的定義；不過一般的隨機向量並非只能由同型變數組成，離散型與連續型變數混合構成的隨機向量同樣符合定義，此處僅為介紹方便而分開討論。

## 聯合、邊際機率質量函數

<div id="def-joint-pmf" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 3.2 (聯合機率質量函數, joint pmf)</div>

若 $(X,Y)$ 為定義於機率空間 $(S,\mathcal{F},\mathbb{P})$ 上之二元**離散型**隨機向量，其聯合值域為 <span class="text-nowrap">$\mathcal{R}\_{\sssig XY}$，</span>則定義函數

$$
p_{\sssig XY}(x,y)=
\left\lbrace
\begin{array}{c@{\quad}l}
\mathbb{P}(X=x,Y=y), & \forall\,(x,y)\in\mathcal{R}_{\sssig XY}\\[0.4em]
0, & \forall\,(x,y)\notin\mathcal{R}_{\sssig XY}
\end{array}
\right.
$$

若 $p\_{\sssig XY}(x,y)$ 滿足以下性質，則稱 $p\_{\sssig XY}(x,y)$ 為 $(X,Y)$ 的**聯合機率質量函數 <span lang="en">(joint probability mass function, joint pmf)</span>**:

<ol class="topic-list-paren">
  <li>對任意點 $(x,y)\in\mathcal{R}_{\sssig XY}$ 而言，皆有
  $$
  0\leqslant p_{\sssig XY}(x,y)\leqslant 1
  $$</li>
  <li>$(X,Y)$ 的取值落在聯合值域中的機率會是下式
  <div class="topic-math-layout topic-math-layout--desktop">
  $$
  \mathbb{P}\bigl((X,Y)\in\mathcal{R}_{\sssig XY}\bigr)=\mathop{\sum\sum}\limits_{(x,y)\in\mathcal{R}_{\sssig XY}}p_{\sssig XY}(x,y)=1
  $$
  </div>
  <div class="topic-math-layout topic-math-layout--mobile">
  $$
  \begin{aligned}
  \mathbb{P}\bigl((X,Y)\in\mathcal{R}_{\sssig XY}\bigr) &=\mathop{\sum\sum}\limits_{(x,y)\in\mathcal{R}_{\sssig XY}}p_{\sssig XY}(x,y)=1
  \end{aligned}
  $$
  </div></li>
  <li>對任意集合 <span class="text-nowrap">$A$，</span>皆有
  $$
  \mathbb{P}\bigl((X,Y)\in A\bigr)=\mathop{\sum\sum}\limits_{(x,y)\in A\cap\mathcal{R}_{\sssig XY}}p_{\sssig XY}(x,y)
  $$</li>
</ol>

</div>

聯合機率質量函數有一些地方需要注意。

(1) 與單元的 pmf 相同，$\mathbb{P}(X=x,Y=y)$ **就是機率**。
{: .topic-paren-item}

(2) 當二元離散向量 $(X,Y)$ 的聯合值域 $\mathcal{R}\_{\sssig XY}$ 為有限集合時，常將其聯合機率質量函數窮舉為表格，形式與本質皆與第一章的[列聯表](/lecture-notes/independence-and-conditional-independence/#互斥與獨立)相同，舉例如下:
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

| $Y\backslash X$ | $0$ | $1$ | $2$ | 邊際 |
| :---: | :---: | :---: | :---: | :---: |
| $0$ | $\mathbb{P}(X=0,Y=0)$ | $\mathbb{P}(X=1,Y=0)$ | $\mathbb{P}(X=2,Y=0)$ | $\mathbb{P}(Y=0)$ |
| $1$ | $\mathbb{P}(X=0,Y=1)$ | $\mathbb{P}(X=1,Y=1)$ | $\mathbb{P}(X=2,Y=1)$ | $\mathbb{P}(Y=1)$ |
| $2$ | $\mathbb{P}(X=0,Y=2)$ | $\mathbb{P}(X=1,Y=2)$ | $\mathbb{P}(X=2,Y=2)$ | $\mathbb{P}(Y=2)$ |
| 邊際 | $\mathbb{P}(X=0)$ | $\mathbb{P}(X=1)$ | $\mathbb{P}(X=2)$ | $1$ |
{: .topic-table--joint-pmf}

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

| $Y\backslash X$ | $0$ | $1$ | $2$ | 邊際 |
| :---: | :---: | :---: | :---: | :---: |
| $0$ | $\mathbb{P}(X=0,$<br>$Y=0)$ | $\mathbb{P}(X=1,$<br>$Y=0)$ | $\mathbb{P}(X=2,$<br>$Y=0)$ | $\mathbb{P}(Y=0)$ |
| $1$ | $\mathbb{P}(X=0,$<br>$Y=1)$ | $\mathbb{P}(X=1,$<br>$Y=1)$ | $\mathbb{P}(X=2,$<br>$Y=1)$ | $\mathbb{P}(Y=1)$ |
| $2$ | $\mathbb{P}(X=0,$<br>$Y=2)$ | $\mathbb{P}(X=1,$<br>$Y=2)$ | $\mathbb{P}(X=2,$<br>$Y=2)$ | $\mathbb{P}(Y=2)$ |
| 邊際 | $\mathbb{P}(X=0)$ | $\mathbb{P}(X=1)$ | $\mathbb{P}(X=2)$ | $1$ |
{: .topic-table--joint-pmf}

</div>

上表的解讀方式與第一章的機率列聯表完全相同。由於 $X=x$ 與 $Y=y$ 各自代表一個事件，表內的交集事件 $\lbrace X=x\rbrace\cap\lbrace Y=y\rbrace$ 在隨機向量中慣以逗號代替交集符號，簡記為 <span class="text-nowrap">$X=x,Y=y$。</span>表邊的總和機率在此稱為**邊際機率 <span lang="en">(marginal probability)</span>**，其背後同樣應用了[全機率定理](/lecture-notes/total-probability-bayes-rule/#theorem-law-of-total-probability)，所構成的分配仍為正規的機率分配。
{: .topic-paren-cont}

<div id="def-marginal-pmf" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 3.3 (邊際機率質量函數, marginal pmf)</div>

若 $(X,Y)$ 為一二元**離散型**隨機向量，其聯合機率質量函數為 <span class="text-nowrap">$p\_{\sssig XY}(x,y)$，</span>則稱下式所定義的函數

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
p_{\sssig X}(x)=\sum_{y\in\mathcal{R}_{\sssig Y}}p_{\sssig XY}(x,y)=\sum_{y\in\mathcal{R}_{\sssig Y}}\mathbb{P}(X=x,Y=y)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig X}(x)&=\sum_{y\in\mathcal{R}_{\sssig Y}}p_{\sssig XY}(x,y)\\[0.45em]
&=\sum_{y\in\mathcal{R}_{\sssig Y}}\mathbb{P}(X=x,Y=y)
\end{aligned}
$$

</div>

為 $X$ 的**邊際機率質量函數 <span lang="en">(marginal pmf)</span>**，並稱以下的函數

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
p_{\sssig Y}(y)=\sum_{x\in\mathcal{R}_{\sssig X}}p_{\sssig XY}(x,y)=\sum_{x\in\mathcal{R}_{\sssig X}}\mathbb{P}(X=x,Y=y)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig Y}(y)&=\sum_{x\in\mathcal{R}_{\sssig X}}p_{\sssig XY}(x,y)\\[0.45em]
&=\sum_{x\in\mathcal{R}_{\sssig X}}\mathbb{P}(X=x,Y=y)
\end{aligned}
$$

</div>

為 $Y$ 的**邊際機率質量函數**。

</div>

邊際機率質量函數本身仍是一種[機率質量函數](/lecture-notes/random-variables-and-pmf/#def-pmf)；以 $p_{\sssig X}(x)$ 為例，將 $Y$ 的所有可能取值加總後，所得即為 $X$ 自身的機率函數，**與 $Y$ 完全無關**。這與微積分中雙變數函數對其中一個變數積分後，所得單變數函數不再依賴被積分變數的道理相同，後文討論二元連續型隨機變數時亦將見到對應的積分形式。

<div id="ex-joint-pmf-constant" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.1</div>

<div lang="en" markdown="1">
Let $(X,Y)$ be a discrete random vector with joint pmf $p_{\sssig XY}(x,y)=c(x+2y)$ for $(x,y)\in\lbrace(0,1),(0,2),(1,0),(1,1),(2,0)\rbrace$, where $c$ is a constant.

<ol class="topic-list-paren">
  <li>Find <span class="text-nowrap">$c$.</span></li>
  <li>Find $\mathbb{P}(X\geqslant 1,Y\leqslant 1)$ and <span class="text-nowrap">$\mathbb{P}(X=0)$.</span></li>
  <li>Find the marginal pmf of <span class="text-nowrap">$X$.</span></li>
</ol>
</div>

(1) 由 joint pmf 之性質知道
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
1&=\mathop{\sum\sum}\limits_{(x,y)\in\mathcal{R}_{\sssig XY}}p_{\sssig XY}(x,y)\\[0.45em]
&=c\,\bigl[(0+2\cdot1)+(0+2\cdot2)+(1+2\cdot0)+(1+2\cdot1)+(2+2\cdot0)\bigr]=c\times12
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
1&=\mathop{\sum\sum}\limits_{(x,y)\in\mathcal{R}_{\sssig XY}}p_{\sssig XY}(x,y)\\[0.45em]
&=c\,\bigl[(0+2\cdot1)+(0+2\cdot2)\\[0.2em]
&\qquad +(1+2\cdot0)+(1+2\cdot1)\\[0.2em]
&\qquad +(2+2\cdot0)\bigr]\\[0.45em]
&=c\times12
\end{aligned}
$$

</div>

由此可以得到 <span class="text-nowrap">$c=\frac{1}{\,12\,}$，</span>又 $0\leqslant p\_{\sssig XY}(x,y)\leqslant1$ 對聯合值域中的五個點 <span class="text-nowrap">$(0,1)$、</span><span class="text-nowrap">$(0,2)$、</span><span class="text-nowrap">$(1,0)$、</span><span class="text-nowrap">$(1,1)$</span> 與 $(2,0)$ 皆成立，故知道所求為
{: .topic-paren-cont}

$$
c=\frac{1}{\,12\,}
$$

(2) 令 $A=\lbrace(1,0),(1,1),(2,0)\rbrace$ 這個集合，則有
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X\geqslant1,Y\leqslant1)=\mathop{\sum\sum}\limits_{(x,y)\in A}p_{\sssig XY}(x,y)=\frac{\,1+2\cdot0\,}{12}+\frac{\,1+2\cdot1\,}{12}+\frac{\,2+2\cdot0\,}{12}=\frac{1}{\,2\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X\geqslant1,Y\leqslant1)&=\mathop{\sum\sum}\limits_{(x,y)\in A}p_{\sssig XY}(x,y)\\[0.45em]
&=\frac{\,1+2\cdot0\,}{12}+\frac{\,1+2\cdot1\,}{12}+\frac{\,2+2\cdot0\,}{12}\\[0.45em]
&=\frac{1}{\,2\,}
\end{aligned}
$$

</div>

另一個所求為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X=0)=p_{\sssig XY}(0,1)+p_{\sssig XY}(0,2)=\frac{\,0+2\cdot1\,}{12}+\frac{\,0+2\cdot2\,}{12}=\frac{1}{\,2\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X=0)&=p_{\sssig XY}(0,1)+p_{\sssig XY}(0,2)\\[0.45em]
&=\frac{\,0+2\cdot1\,}{12}+\frac{\,0+2\cdot2\,}{12}=\frac{1}{\,2\,}
\end{aligned}
$$

</div>

(3) $X$ 的邊際機率質量函數為
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
p_{\sssig X}(x)=\sum_{y\in\mathcal{R}_{\sssig Y}}p_{\sssig XY}(x,y)=\sum_{y=0}^{2}p_{\sssig XY}(x,y)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{1}{\,2\,}, & x=0\\[0.6em]
\dfrac{1}{\,3\,}, & x=1\\[0.6em]
\dfrac{1}{\,6\,}, & x=2\\[0.6em]
0, & \text{o.w.}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig X}(x)&=\sum_{y\in\mathcal{R}_{\sssig Y}}p_{\sssig XY}(x,y)=\sum_{y=0}^{2}p_{\sssig XY}(x,y)\\[0.45em]
&=
\left\lbrace
\begin{array}{c@{}l}
\dfrac{1}{\,2\,}, & x=0\\[0.6em]
\dfrac{1}{\,3\,}, & x=1\\[0.6em]
\dfrac{1}{\,6\,}, & x=2\\[0.6em]
0, & \text{o.w.}
\end{array}
\right.
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

上述邊際 pmf 亦可透過窮舉列聯表求得，將聯合機率整理如下表:

| $Y\backslash X$ | $0$ | $1$ | $2$ | $p_{\sssig Y}(y)$ |
| :---: | :---: | :---: | :---: | :---: |
| $0$ | $0$ | $1/12$ | $2/12$ | $3/12$ |
| $1$ | $2/12$ | $3/12$ | $0$ | $5/12$ |
| $2$ | $4/12$ | $0$ | $0$ | $4/12$ |
| $p_{\sssig X}(x)$ | $6/12$ | $4/12$ | $2/12$ | $1$ |
{: .topic-table--joint-pmf}

由表邊的行列加總即可直接得到 $X$ 與 $Y$ 的邊際分配。

此外，第 (2) 小題計算 $\mathbb{P}(X=0)$ 時，是依事件 $\lbrace X=0\rbrace$ 不限制 $Y$ 取值的意義，將所有滿足 $x=0$ 的聯合機率相加；這與先求出邊際機率質量函數 $p_{\sssig X}(x)$ 再代入 $x=0$ 完全等價，兩者本質上皆是對 $Y$ 的所有可能取值作加總。

</div>

## 本篇小結

[Definition 3.1](#def-random-vector) 把隨機變數的概念推廣到多維。令 $X_1,X_2,\ldots,X_n$ 為定義在同一個機率空間上的隨機變數，由它們所構成的向量函數 $\boldsymbol{X}(\omega)$ 若滿足對任意實數 $x_1,x_2,\ldots,x_n$ 而言，能使各個 $X_i(\omega)\leqslant x_i$ 同時成立的樣本點所形成的集合都是事件，則稱之為隨機向量。這個條件與單變數的要求相同，差別只在於它同時對 $n$ 個座標提出要求，而所要求的集合正是 $n$ 個事件的交集。$\boldsymbol{X}$ 的定義域是樣本空間、對應域是 <span class="text-nowrap">$\mathbb{R}^{n}$，</span>聯合值域 $\mathcal{R}\_{\boldsymbol{X}}$ 則是 $\mathbb{R}^{n}$ 的子集。

回到離散型，[Definition 3.2](#def-joint-pmf) 的聯合機率質量函數在聯合值域上記錄 $\mathbb{P}(X=x,Y=y)$ 這個機率，在聯合值域之外則取 <span class="text-nowrap">$0$，</span>並滿足介於 $0$ 與 $1$ 之間、在聯合值域上加總為 <span class="text-nowrap">$1$，</span>以及任一事件 $A$ 的機率為 $A\cap\mathcal{R}_{\sssig XY}$ 上之雙重加總這三項性質。聯合值域為有限集合時，聯合機率質量函數可以窮舉成列聯表的形式，表邊的總和機率即為邊際機率。[Definition 3.3](#def-marginal-pmf) 把這件事寫成定義。對另一個變數的所有可能取值加總，所得的 $p\_{\sssig X}(x)$ 與 $p\_{\sssig Y}(y)$ 分別是 $X$ 與 $Y$ 的邊際機率質量函數，它們各自仍是一個機率質量函數。

[Example 3.1](#ex-joint-pmf-constant) 以一組五個質點的聯合機率質量函數依序示範三件事，包含由加總為 $1$ 求出常數 <span class="text-nowrap">$c$、</span>把事件寫成質點的集合再加總以求得事件機率，以及對 $y$ 加總求出 $X$ 的邊際機率質量函數。同一題若先把聯合機率窮舉成列聯表，邊際分配可以直接由表邊得到，兩種算法的原理完全相同。[下一篇](/lecture-notes/joint-cumulative-distribution-functions/)改以累積的機率描述二元隨機向量的分配，介紹[聯合累積分配函數](/lecture-notes/joint-cumulative-distribution-functions/#def-joint-cdf)。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
