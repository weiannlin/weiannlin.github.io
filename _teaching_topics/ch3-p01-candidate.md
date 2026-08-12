---
title: "隨機向量與聯合機率質量函數"
subtitle: "Random Vectors and Joint Probability Mass Functions"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 1
order: 301
permalink: /teaching-topics/ch3-p01-candidate/
date: 2026-08-12
published: false
excerpt: "隨機變數的概念並不限於一維。把定義在同一個機率空間上的 $n$ 個隨機變數合起來看成一個向量函數，並要求對任意實數 $x_1,x_2,\\ldots,x_n$ 而言，能使各個 $X_i(\\omega)\\leqslant x_i$ 同時成立的樣本點所形成的集合都是事件，這樣的向量函數即為隨機向量。二元離散型的聯合機率質量函數在聯合值域上記錄 $\\mathbb{P}(X=x,Y=y)$ 這個機率，並滿足三項性質；把其中一個變數的所有可能取值加總，便得到另一個變數的邊際機率質量函數。本篇最後以一道例題示範常數的求法、事件機率的計算與邊際 pmf 的求取。"
---

[上一篇](/teaching-topics/ch2-p224-candidate/)以三道例題處理了非一對一的函數轉換，第二章到此告一段落。第二章所討論的隨機變數 <span lang="en">(random variable)</span> 都只有一維，但這個概念當然不僅限於一維，我們可以將其擴展至二維以上的多維空間，代表的意義也會隨之不同。

在第一章，我們曾經探討過，若是我們有兩個事件，則我們可以就其關係歸納出[互斥、獨立](/teaching-topics/independence-and-conditional-independence/#互斥與獨立)等觀念；又於第二章，我們曾說過，所謂[隨機變數](/teaching-topics/ch2-p01-candidate/#def-random-variable)事實上是將樣本空間內的元素，映射到實數上的函數，故在此，我們當然可以將樣本空間分別映射至不同的兩個實數上，此概念即為二元隨機變數。

當然，一旦具有二元乃至多元隨機變數的概念，則與複數個事件相同，我們可以探討事件與事件間的關係，在此當然也可以探討變數與變數間的關係，諸如此類的定義與性質，與單元隨機變數相同，我們都需要從二元 (多元) 隨機變數的定義開始出發。

這其中，當我們手上具有許多個隨機變數所構成的向量，我們特稱之為**隨機向量**，以下就來看看隨機向量與單一的隨機變數，在定義上有何不同。

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
\begin{gathered}
I=\bigl\lbrace\,(\,t_1,t_2,\ldots,t_n\,)\mid\\[0.35em]
-\infty<t_i\leqslant x_i,\ x_i\in\mathbb{R},\\[0.35em]
i=1,2,\ldots,n\,\bigr\rbrace
\end{gathered}
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

事實上，這二個等價定義都在說明同一件事情，也就是，只要我們有實數 $x_1,x_2,\ldots,x_n$ 這 $n$ 個數，則**能夠使得 $X_1(\omega)\leqslant x_1,X_2(\omega)\leqslant x_2,\ldots,X_n(\omega)\leqslant x_n$ 的那些樣本點所收集而成的集合，必須是個能夠被定義機率的事件**。
{: .topic-paren-cont}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

讀者應該還記得，在[隨機變數](/teaching-topics/ch2-p01-candidate/#def-random-variable)的等價定義中，我們曾經提過，對於一個隨機變數 <span class="text-nowrap">$X_i$，</span>依其定義，我們有下式

$$
X^{-1}\bigl((-\infty,x_i]\bigr)=\lbrace\,\omega\mid X_i(\omega)\leqslant x_i\,\rbrace\in\mathcal{F},\quad i=1,2,\ldots,n
$$

又由 $\mathcal{F}$ 的定義可知，若 $A_i\in\mathcal{F}$ 對 $i=1,2,\ldots,n$ 都成立，我們有下式

$$
\bigcap_{i=1}^{n}A_i\in\mathcal{F}
$$

故由此定義可以看出，只要 $X_1,X_2,\ldots,X_n$ 都是定義於 $(S,\mathcal{F},\mathbb{P})$ 上之隨機變數，則其所構成的向量

$$
\boldsymbol{X}=\bigl(\,X_1(\omega),X_2(\omega),\ldots,X_n(\omega)\,\bigr)
$$

就是一個隨機向量。

</div>

(2) $\boldsymbol{X}$ 為一函數，定義域 (domain) 是樣本空間 <span class="text-nowrap">$S$、</span>對應域 <span lang="en">(codomain)</span> 是 $n$ 維實數空間 <span class="text-nowrap">$\mathbb{R}^{n}$，</span>而**聯合值域 (joint range)** 記為 <span class="text-nowrap">$\mathcal{R}\_{\boldsymbol{X}}$，</span>為 $n$ 維實數空間 $\mathbb{R}^{n}$ 的子集。
{: .topic-paren-item}

(3) 在本系列往後的各篇中，我們多半只關注 $n=2$ 的情況，並可能稱其為多元隨機變數。
{: .topic-paren-item}

為了與第二章接軌，我們在隨機向量 (或稱多元隨機變數) 中，仍分離散型隨機向量與連續型隨機向量，探討其機率函數與分配函數的定義。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

儘管如此，讀者仍應謹記，一般的隨機向量中，並不是只能離散與離散搭配、連續與連續搭配，離散變數與連續變數混搭而成的隨機向量是符合定義的，只是便於介紹，我們特以離散與離散、連續與連續的情況來介紹。

</div>

## 聯合、邊際機率質量函數

<div id="def-joint-pmf" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 3.2 (聯合機率質量函數, joint pmf)</div>

若 $(X,Y)$ 為定義於機率空間 $(S,\mathcal{F},\mathbb{P})$ 上之二元**離散型**隨機向量，其聯合值域為 <span class="text-nowrap">$\mathcal{R}\_{\sssig XY}$，</span>則定義函數

$$
p_{\sssig XY}(x,y)=
\left\lbrace
\begin{array}{c@{\quad}l}
\mathbb{P}(X=x,Y=y), & \forall (x,y)\in\mathcal{R}_{\sssig XY}\\[0.4em]
0, & \forall (x,y)\notin\mathcal{R}_{\sssig XY}
\end{array}
\right.
$$

若 $p\_{\sssig XY}(x,y)$ 滿足以下性質，則稱 $p\_{\sssig XY}(x,y)$ 為 $(X,Y)$ 的**聯合機率質量函數 <span lang="en">(joint probability mass function, joint pmf)</span>**:

<ol class="topic-list-paren">
  <li>對任意 $(x,y)\in\mathcal{R}_{\sssig XY}$，皆有
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
  &\mathbb{P}\bigl((X,Y)\in\mathcal{R}_{\sssig XY}\bigr)\\[0.45em]
  &\quad =\mathop{\sum\sum}\limits_{(x,y)\in\mathcal{R}_{\sssig XY}}p_{\sssig XY}(x,y)=1
  \end{aligned}
  $$
  </div></li>
  <li>對任意集合 $A$，皆有
  $$
  \mathbb{P}\bigl((X,Y)\in A\bigr)=\mathop{\sum\sum}\limits_{(x,y)\in A}p_{\sssig XY}(x,y)
  $$</li>
</ol>

</div>

聯合機率質量函數有一些地方需要注意。

(1) 與單元的 pmf 相同，$\mathbb{P}(X=x,Y=y)$ **就是機率**。
{: .topic-paren-item}

(2) 很多時候一個二元離散向量 $(X,Y)$ 的聯合值域 $\mathcal{R}\_{\sssig XY}$ 是有限集合，這種時候我們常常將其聯合機率函數窮舉為表格的形式，其型態與第一章我們所談到的[列聯表](/teaching-topics/independence-and-conditional-independence/#互斥與獨立)非常相似，二者的本質也是相同的，下面我們便來看看這樣的例子:
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

上表的解讀方式與第一章的機率列聯表幾乎完全相同，差異只在當時我們所使用的是集合事件，而這裡我們使用隨機變數，但本質上都是完全相同的。
{: .topic-paren-cont}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

讀者應該記得，不論是 $X=x$ 或 <span class="text-nowrap">$Y=y$，</span>其實都分別表示一個事件，因此上表的理解理應與過去我們所知道的機率列聯表完全相同；而表內的交集事件原先應為 $\lbrace X=x\rbrace\cap\lbrace Y=y\rbrace$ 這樣的形式，但在隨機向量中，我們一般以逗號代替交集符號，因此改為 <span class="text-nowrap">$X=x,Y=y$。</span>

</div>

另外，上表中原先在表邊的總和機率在這邊變成了**邊際機率 <span lang="en">(marginal probability)</span>**，這種機率所構成的機率分配，仍然是一種正規的機率分配，其直觀意義與當時相同，仍是應用了[全機率定理](/teaching-topics/total-probability-bayes-rule/#theorem-law-of-total-probability)。關於這種機率分配的定義與其性質，我們馬上便會看見。
{: .topic-paren-cont}

<div id="def-marginal-pmf" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 3.3 (邊際機率質量函數, marginal pmf)</div>

若 $(X,Y)$ 為一二元**離散型**隨機向量，其聯合機率質量函數為 <span class="text-nowrap">$p\_{\sssig XY}(x,y)$，</span>則稱以下的函數

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

讀者應特別注意的是，邊際機率質量函數仍然是一種機率質量函數，例如: $X$ 的邊際機率質量函數便可以視為是 $X$ 自己的機率函數，**而與 $Y$ 完全無關**。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個概念與微積分中，將一個雙變數函數的其中一個變數積分過後，剩下來的單變數函數亦被稱為邊際函數，是完全相同的，且該邊際函數亦與被積分的變數完全無關。我們將在二元連續隨機變數中看到這樣的例子。

</div>

<div id="ex-joint-pmf-constant" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.1</div>

<div lang="en" markdown="1">
Suppose that a discrete random vector $(X,Y)$ has joint probability mass function

$$
p_{\sssig XY}(x,y)=c(x+2y)
$$

on the set $\lbrace(0,1),(0,2),(1,0),(1,1),(2,0)\rbrace$, where $c$ is a constant.

<ol class="topic-list-paren">
  <li>Determine the value of <span class="text-nowrap">$c$.</span></li>
  <li>Evaluate $\mathbb{P}(X\geqslant 1,Y\leqslant 1)$ and <span class="text-nowrap">$\mathbb{P}(X=0)$.</span></li>
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

由此可以得到 <span class="text-nowrap">$c=\frac{1}{\,12\,}$，</span>又 $0\leqslant p\_{\sssig XY}(x,y)\leqslant1$ 對聯合值域中的五個點 $(0,1)$、$(0,2)$、$(1,0)$、$(1,1)$ 與 $(2,0)$ 皆成立，故知道所求為
{: .topic-paren-cont}

$$
c=\frac{1}{\,12\,}
$$

(2) 令 $A=\lbrace(1,0),(1,1),(2,0)\rbrace$，則有
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X\geqslant1,Y\leqslant1)=\mathop{\sum\sum}\limits_{(x,y)\in A}p_{\sssig XY}(x,y)=\frac{\,1+2\cdot0\,}{12}+\frac{\,1+2\cdot1\,}{12}+\frac{\,2+2\cdot0\,}{12}=\frac{1}{\,2\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(X\geqslant1,Y\leqslant1)=\mathop{\sum\sum}\limits_{(x,y)\in A}p_{\sssig XY}(x,y)\\[0.45em]
&\quad =\frac{\,1+2\cdot0\,}{12}+\frac{\,1+2\cdot1\,}{12}+\frac{\,2+2\cdot0\,}{12}\\[0.45em]
&\quad =\frac{1}{\,2\,}
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
0, & \text{otherwise}
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
\begin{array}{c@{\quad}l}
\dfrac{1}{\,2\,}, & x=0\\[0.6em]
\dfrac{1}{\,3\,}, & x=1\\[0.6em]
\dfrac{1}{\,6\,}, & x=2\\[0.6em]
0, & \text{otherwise}
\end{array}
\right.
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

事實上，上述求取邊際 pmf 的做法，也可以窮舉的方式完成，亦即將題目的敘述轉化為以下的列聯表:

| $Y\backslash X$ | $0$ | $1$ | $2$ | $p_{\sssig Y}(y)$ |
| :---: | :---: | :---: | :---: | :---: |
| $0$ | $0$ | $1/12$ | $2/12$ | $3/12$ |
| $1$ | $2/12$ | $3/12$ | $0$ | $5/12$ |
| $2$ | $4/12$ | $0$ | $0$ | $4/12$ |
| $p_{\sssig X}(x)$ | $6/12$ | $4/12$ | $2/12$ | $1$ |
{: .topic-table--joint-pmf}

則由上表同樣可以知道 $X$ 的邊際分配。

值得注意的是，第二小題中的 <span class="text-nowrap">$\mathbb{P}(X=0)$，</span>我們是採用正規的聯合機率計算，利用純粹只說 $X=0$ 時，表示 $Y$ 可以是任意值的結果求算；但事實上，這個結果會直接等價於，先計算 $X$ 的邊際分配，再利用邊際分配求算 <span class="text-nowrap">$\mathbb{P}(X=0)$，</span>而且二者的原理其實完全相同，讀者可以思考看看為何。

</div>

## 本篇小結

[Definition 3.1](#def-random-vector) 把隨機變數的概念推廣到多維: 令 $X_1,X_2,\ldots,X_n$ 為定義在同一個機率空間上的隨機變數，由它們所構成的向量函數 $\boldsymbol{X}(\omega)$ 若滿足對任意實數 $x_1,x_2,\ldots,x_n$ 而言，能使各個 $X_i(\omega)\leqslant x_i$ 同時成立的樣本點所形成的集合都是事件，則稱之為隨機向量。這個條件與單變數的要求相同，差別只在於它同時對 $n$ 個座標提出要求，而所要求的集合正是 $n$ 個事件的交集。$\boldsymbol{X}$ 的定義域是樣本空間、對應域是 <span class="text-nowrap">$\mathbb{R}^{n}$，</span>聯合值域 $\mathcal{R}\_{\boldsymbol{X}}$ 則是 $\mathbb{R}^{n}$ 的子集。

回到離散型，[Definition 3.2](#def-joint-pmf) 的聯合機率質量函數在聯合值域上記錄 $\mathbb{P}(X=x,Y=y)$ 這個機率，在聯合值域之外則取 <span class="text-nowrap">$0$，</span>並滿足介於 $0$ 與 $1$ 之間、在聯合值域上加總為 <span class="text-nowrap">$1$，</span>以及任一事件的機率為該事件上之雙重加總這三項性質。聯合值域為有限集合時，聯合機率質量函數可以窮舉成列聯表的形式，表邊的總和機率即為邊際機率。[Definition 3.3](#def-marginal-pmf) 把這件事寫成定義: 對另一個變數的所有可能取值加總，所得的 $p\_{\sssig X}(x)$ 與 $p\_{\sssig Y}(y)$ 分別是 $X$ 與 $Y$ 的邊際機率質量函數，它們各自仍是一個機率質量函數。

[Example 3.1](#ex-joint-pmf-constant) 以一組五個質點的聯合機率質量函數示範三件事: 由加總為 $1$ 求出常數 <span class="text-nowrap">$c$、</span>把事件寫成質點的集合再加總以求得事件機率，以及對 $y$ 加總求出 $X$ 的邊際機率質量函數。同一題若先把聯合機率窮舉成列聯表，邊際分配可以直接由表邊得到，兩種算法的原理完全相同。[下一篇](/teaching-topics/ch3-p02-candidate/)改以累積的機率描述二元隨機向量的分配，介紹聯合累積分配函數。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
