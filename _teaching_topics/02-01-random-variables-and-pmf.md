---
title: "隨機變數與機率質量函數"
subtitle: "Random Variables and Probability Mass Functions"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 1
order: 201
permalink: /teaching-topics/random-variables-and-pmf/
date: 2026-08-04
published: true
excerpt: "隨機變數是定義在樣本空間上的實值函數，把樣本點對應到實數，並要求對任意實數 $x$，能使 $X(\\omega)\\leqslant x$ 的樣本點所形成的集合都是事件。值域中元素個數為有限或可數無限者為離散型；累積機率可寫成非負函數之積分者為連續型。離散型的機率質量函數在值域上記錄每一個點的單點機率，在值域之外為 $0$，並滿足三項性質。"
---

[上一章最後一篇文章](/teaching-topics/bayes-rule-posterior-probability/)完成了分割、全機率定理與貝氏定理的討論。第一章的機率都定義在事件上，而事件是樣本空間的子集合，討論時必須逐個事件處理。

集合論屬於離散數學，比較無法應用微積分之類的數學工具。本章引入隨機變數，把樣本點對應到實數，事件因而能以變數值表示，後續的分析也就能借助數學分析的工具。

<span id="proposition-22"></span><!-- legacy anchor: 不對應任何環境，不得再指派 -->

## 隨機變數的定義

<span id="definition-21"></span>
<div id="def-random-variable" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.1 (隨機變數, random variable)</div>

令 $(S,\mathcal{F},\mathbb{P})$ 為一機率空間，在其上的**隨機變數 <span lang="en">(random variable, rv)</span>** $X\colon S\to\mathbb{R}$ 為定義在樣本空間 $S$ 上的實值函數，且滿足對任意實數 $x$，下面的集合都是事件

$$
\lbrace\,\omega\mid\omega\in S,\ X(\omega)\leqslant x\,\rbrace\in\mathcal{F}
$$

</div>

隨機變數是一個函數 <span lang="en">(function)</span>，其有一些特殊的性質需要注意。

(1) 隨機變數 $X(\cdot)$ 是將樣本點對應至實數的函數，此即對任意樣本點 $\omega\in S$，都有下面的對應
{: .topic-paren-item}

$$
X(\omega)\in\mathbb{R}
$$

(2) $X(\cdot)$ 為一函數，故其應恪守一切函數之基本性質，其**定義域 (domain)** 是樣本空間 $S$、**對應域 <span lang="en">(codomain)</span>** 是實數 $\mathbb{R}$，而**值域 (range)** 記為 $\mathcal{R}_{\sssig X}$，為實數 $\mathbb{R}$ 的子集。其中，特別需要注意的是不可有樣本點對應到多個實數，此即函數不可一對多。
{: .topic-paren-item}

<span id="可能取值集合的型態"></span>
<div id="note-range-and-support" class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

值域是指 $X$ 之所有可能的值形成的集合，記為

$$
\mathcal{R}_{\sssig X}=\lbrace\,X(\omega)\mid\omega\in S\,\rbrace
$$

值域又稱**支撐集 <span lang="en">(support)</span>**，本系列一律用值域，並以 $\mathcal{R}_{\sssig X}$ 表示。

</div>

(3) 關於隨機變數必須滿足對任意 $x\in\mathbb{R}$，皆有
{: .topic-paren-item}

$$
\lbrace\,\omega\mid\omega\in S,\ X(\omega)\leqslant x\,\rbrace\in\mathcal{F}
$$

在部分的教科書上會改用反映射的寫法，以 $X^{-1}(\cdot)$ 定義，則等價定義為隨機變數 $X\colon S\to\mathbb{R}$ 必須滿足
{: .topic-paren-cont}

$$
X^{-1}\bigl((-\infty,x]\bigr)=\lbrace\,\omega\mid X(\omega)\leqslant x\,\rbrace\in\mathcal{F}
$$

事實上都在說明同一件事情，也就是只要我們有一個實數 $x$，則**能夠使得 $X(\omega)\leqslant x$ 的那些樣本點所收集而成的集合，必須是個能夠被定義機率的事件**。上式中的 $X^{-1}$ 取的是集合的**原像 <span lang="en">(preimage)</span>**，對任意實數集合 $A$，$X^{-1}(A)$ 表示 $A$ 在 $X$ 之下的原像，並不表示 $X$ 具有反函數。
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
\lbrace\,\omega\mid\omega\in S,\ \text{且}\ X(\omega)=x\,\rbrace
$$

例如: $X(\omega)=3$ 代表**使得 $X$ 為 $3$ 的樣本點之集合**。為了方便，我們時常簡寫為 <span class="text-nowrap">$X=x$，</span>其中大寫英文字母代表隨機變數本身，小寫英文字母則代表一實數。
{: .topic-paren-cont}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

正是因為我們關心的是隨機變數值在 $(-\infty,x]$ 的範圍中，我們往後會知道，隨機變數的**機率分配 <span lang="en">(probability distribution)</span>** 最初是由其[累積分配函數 <span lang="en">(cumulative distribution function, cdf)</span>](/teaching-topics/cumulative-distribution-functions/#def-cdf) 所定義的。

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

讀者應特別注意，$X=x$ 為樣本點所形成的集合，故我們當然可將其視為一事件。

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

大寫字母代表的隨機變數具有**隨機性**，而小寫字母則僅為一數字，應不可混淆。往後，本系列亦將以此原則進行書寫。

</div>

隨機變數的定義給了許多方便，其中最大的好處是，過去我們需要逐一討論的樣本點與事件，被轉化為實數，我們只要使用這個「變數值」，即可代表相對應的事件；除了討論方便以外，實數給予我們的好處更在於，能使用數學分析工具，來幫助我們進行深入的探討。

在給定隨機變數的定義後，我們即可以隨機變數來討論機率函數的性質。但在正式進入機率函數之前，我們先就隨機變數及其值域的型態進行討論。

<div id="def-support-classification" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.2 (隨機變數的分類)</div>

令 $X$ 為定義於機率空間 $(S,\mathcal{F},\mathbb{P})$ 上之隨機變數。

(1) 若值域 $\mathcal{R}_{\sssig X}$ 中之元素個數為有限或可數地無限，則稱 $X$ 為**離散型隨機變數 <span lang="en">(discrete random variable)</span>**。
{: .topic-paren-item}

(2) 若存在一非負且可積分的函數 $f_{\sssig X}\colon\mathbb{R}\to[0,\infty)$，使得對任意 $x\in\mathbb{R}$，皆有
{: .topic-paren-item}

$$
\mathbb{P}(X\leqslant x)=\int_{-\infty}^{x}f_{\sssig X}(t)\,dt
$$

則稱 $X$ 為**連續型隨機變數 <span lang="en">(continuous random variable)</span>**。
{: .topic-paren-cont}

</div>

<div id="note-continuous-criterion" class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

第 (2) 款以積分表示式界定連續型，而不以值域中元素的個數界定。元素個數只是必要條件，不是充分條件: 值域為不可數無限的隨機變數，未必能把 $\mathbb{P}(X\leqslant x)$ 寫成積分。一種情形是某些單點仍具有正機率，此時 $\mathbb{P}(X\leqslant x)$ 在該點跳躍，積分式不成立；另一種情形是每一個單點的機率皆為 $0$，卻仍找不到能使 $\mathbb{P}(X\leqslant x)$ 寫成積分的非負函數 $f_{\sssig X}$。

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

讀者應可對照第一章[離散樣本空間與連續樣本空間](/teaching-topics/random-experiments-sample-space-events/#離散樣本空間與連續樣本空間)的分類。離散型的判準與離散樣本空間的判準非常相像，兩者都以元素個數為有限或可數無限為準；連續型則不以元素個數為準，改以機率能否寫成積分為準。

</div>

<div id="ex-ranges" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.1</div>

<ol class="topic-list-paren">
  <li>投擲一硬幣 $1$ 次觀察其結果，令隨機變數 $X$ 表正面出現之次數，則其值域為何？</li>
  <li>假設某人每期皆購買一張樂透彩券，直到中頭獎為止。令隨機變數 $X$ 表直到中頭獎為止所經歷的槓龜次數，則其值域應為何？</li>
  <li>令隨機變數 $X$ 表某一電腦零件之壽命，則其值域應為何？</li>
</ol>

<ol class="topic-list-paren">
  <li>
  $$
  \mathcal{R}_{\sssig X}=\lbrace0,1\rbrace
  $$
  </li>
  <li>
  $$
  \mathcal{R}_{\sssig X}=\lbrace0,1,2,3,\ldots\rbrace
  $$
  </li>
  <li>
  $$
  \mathcal{R}_{\sssig X}=\lbrace\,x\mid x\geqslant0\,\rbrace
  $$
  </li>
</ol>

</div>

由於在離散型隨機變數與連續型隨機變數中，機率函數的運算性質稍有不同，故在正式定義完隨機變數的分類以後，我們方可基於此分類，進行機率函數的定義。

## 機率質量函數

<div id="def-pmf" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.3 (機率質量函數, probability mass function, pmf)</div>

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

若 $p_{\sssig X}(x)$ 滿足以下性質，則稱 $p_{\sssig X}(x)$ 為 $X$ 的**機率質量函數 <span lang="en">(probability mass function, pmf)</span>**:

<ol class="topic-list-paren">
  <li>對任意 $x\in\mathcal{R}_{\sssig X}$，皆有
  $$
  0\leqslant p_{\sssig X}(x)\leqslant 1
  $$</li>
  <li>$X$ 的取值落在值域中的機率為
  $$
  \mathbb{P}(X\in\mathcal{R}_{\sssig X})=\sum_{x\in\mathcal{R}_{\sssig X}}p_{\sssig X}(x)=1
  $$</li>
  <li>對任意集合 $A$，皆有
  $$
  \mathbb{P}(X\in A)=\sum_{x\in A\cap\mathcal{R}_{\sssig X}}p_{\sssig X}(x)
  $$</li>
</ol>

</div>

在**機率質量函數**的定義中，$\mathbb{P}(X=x)$ 的部分事實上應寫為 $\mathbb{P}\bigl(\lbrace X(\omega)=x\rbrace\bigr)$ 或是 $\mathbb{P}\bigl(\lbrace\,\omega\mid X(\omega)=x\,\rbrace\bigr)$ 較為完整，其理由如同前述，因為機率函數是被定義在集合上的函數，且 $\lbrace\,\omega\mid X(\omega)=x\,\rbrace$ 的表示法才是一個集合。然而為了方便書寫及表示，將其簡寫為 $\mathbb{P}(X=x)$ 亦是被普遍接受的。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

許多教科書中亦將 $p_{\sssig X}(x)$ 寫成 $f_{\sssig X}(x)$，這樣的寫法可以與連續型變數的[機率密度函數](/teaching-topics/probability-density-functions/#def-pdf) <span lang="en">(probability density function, pdf)</span> 共通，通稱為機率函數 <span lang="en">(probability function)</span>。此處的機率函數是 pmf 與 pdf 的統稱，與第一章[指稱 $\mathbb{P}(\cdot)$ 的機率函數](/teaching-topics/event-families-sigma-fields/#term-probability-function)所指不同。

</div>

另一個需要注意的點是，$\mathbb{P}(X=x)$ **就是機率**。我們可以將其理解為，機率質量函數只有在其值域的點上才有機率，這個概念就好像在特定的點上才有「質量」一般，故被稱作機率質量函數，而值域的點亦被稱作「質點」。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

由於其定義就是機率，故當然應滿足[機率三大公理](/teaching-topics/event-families-sigma-fields/#definition-probability-space)，即分別對應到上述定義中的三點性質。

</div>

讀者也可以打開 [From pmf to cdf](/demos/pmf-cdf/)，自行增刪質點、改變各點的機率值，觀察各點的高度如何變化，以及機率總和是否為 $1$。展示的另一半是累積分配函數，[下一篇](/teaching-topics/cumulative-distribution-functions/)才會正式介紹。

<div id="ex-two-ball-sum" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.2</div>

若箱中有四顆大小形狀完全相同、分別編號 $0$ 至 $3$ 的球，若 $X$ 表示隨機從中一次抽取兩顆球的號碼總和，則試列出其機率質量函數，並求其號碼的總和為 $3$ 的機率為何？

可先列出樣本空間

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
S=\lbrace(0,1),(0,2),(0,3),(1,2),(1,3),(2,3)\rbrace
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
S=\lbrace&(0,1),(0,2),(0,3),\\[0.4em]
&(1,2),(1,3),(2,3)\rbrace
\end{aligned}
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

故 $X$ 的 pmf 可寫為

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

所求的機率為

$$
p_{\sssig X}(3)=\frac{1}{3}\fallingdotseq0.3333
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這題的解法是為了協助讀者將 pmf 與過去所學的古典機率結合，但事實上並不需要每次都這麼麻煩地從樣本空間開始列起。爾後的題目我們將寫得比較簡潔。

</div>

<div id="ex-geometric-pmf" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.3</div>

<div lang="en" markdown="1">
Suppose that a random variable $X$ has probability mass function

$$
p_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
c\left(\dfrac{1}{2}\right)^{x}, & x=1,2,\ldots\\[0.6em]
0, & \text{otherwise}
\end{array}
\right.
$$

for some constant $c$.

<ol class="topic-list-paren">
  <li>Determine the value of $c$, and evaluate <span class="text-nowrap">$\mathbb{P}(X=5)$.</span></li>
</ol>
</div>

由 pmf 之性質知道

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
1=\sum_{x=1}^{\infty}c\left(\frac{1}{2}\right)^{x}
=c\sum_{x=1}^{\infty}\left(\frac{1}{2}\right)^{x}
=c\times\frac{\frac{1}{2}}{1-\frac{1}{2}}
=c
\quad\Longrightarrow\quad
c=1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
1&=\sum_{x=1}^{\infty}c\left(\frac{1}{2}\right)^{x}
=c\sum_{x=1}^{\infty}\left(\frac{1}{2}\right)^{x}\\[0.4em]
&=c\times\frac{\frac{1}{2}}{1-\frac{1}{2}}=c\\[0.4em]
&\!\!\Longrightarrow\ c=1
\end{aligned}
$$

</div>

由於 $c=1>0$，可知 $p_{\sssig X}(x)\geqslant0$ 對一切 $x=1,2,\ldots$ 皆成立，[Definition 2.3](#def-pmf) 第 (1) 款的非負性得到滿足，以此可計算

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
<div class="topic-box__label">Example 2.4</div>

<div lang="en" markdown="1">
Let $X$ be a random variable whose distribution involves a parameter $\theta$, and whose possible values form the set <span class="text-nowrap">$\lbrace0,1,2,3,\ldots\rbrace$.</span> If the recursion <span class="text-nowrap">$\mathbb{P}(X=x)=\frac{\theta}{x}\mathbb{P}(X=x-1)$</span> holds for every <span class="text-nowrap">$x=1,2,3,\ldots$,</span> find the probability mass function of <span class="text-nowrap">$X$.</span>
</div>

由題意之遞迴 <span lang="en">(recursion)</span> 性質可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X=x)&=\frac{\theta}{x}\,\mathbb{P}(X=x-1)
=\frac{\theta}{x}\cdot\frac{\theta}{x-1}\,\mathbb{P}(X=x-2)\\[0.4em]
&=\cdots=\frac{\theta^{x}}{x!}\,\mathbb{P}(X=0)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(&X=x) =\frac{\theta}{x}\,\mathbb{P}(X=x-1)\\[0.4em]
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
1&=\sum_{x\in\mathcal{R}_{\sssig X}}p_{\sssig X}(x)\\[0.4em]
&=\sum_{x=0}^{\infty}\mathbb{P}(X=x)\\[0.4em]
&=\sum_{x=0}^{\infty}\frac{\theta^{x}}{x!}\,\mathbb{P}(X=0)\\[0.4em]
&=\mathbb{P}(X=0)\sum_{x=0}^{\infty}\frac{\theta^{x}}{x!}\\[0.4em]
&=\mathbb{P}(X=0)\,e^{\theta}
\end{aligned}
$$

</div>

故 $\mathbb{P}(X=0)=e^{-\theta}$，因此

$$
p_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{e^{-\theta}\theta^{x}}{x!}, & x=0,1,2,\ldots\\[0.7em]
0, & \text{otherwise}
\end{array}
\right.
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

題目只設 $X$ 的分配帶有參數 $\theta$，並未指明 $\theta$ 的範圍；這一點可由 pmf 的非負性補足。由題意之遞迴性質可得 $p_{\sssig X}(1)=\theta\,\mathbb{P}(X=0)$，而 $\mathbb{P}(X=0)=e^{-\theta}>0$，非負性因而要求 $\theta\geqslant0$。$\theta=0$ 是這個範圍的邊界情形，非負性並未將它排除: 此時 $\mathbb{P}(X=0)=1$，$X$ 退化為恆取 $0$ 的隨機變數，已不具有隨機性。本題的參數範圍取 <span class="text-nowrap">$\theta>0$，</span>不含這個退化的情形。

</div>

## 本篇小結

第一章把機率定義在事件上。本篇改由隨機變數出發，以一個定義在樣本空間上的實值函數，把樣本點對應到實數；它必須滿足的條件是，對任意實數 $x$，能使 $X(\omega)\leqslant x$ 的樣本點所形成的集合都是事件。值域中元素個數為有限或可數無限者為離散型；累積機率可寫成某個非負函數之積分者為連續型。

離散型的機率質量函數以 $p_{\sssig X}(x)=\mathbb{P}(X=x)$ 記錄值域中每一個點的單點機率，在值域之外則取 $0$。由於 $\mathbb{P}(X=x)$ 本身就是機率，其三項性質分別對應機率的三大公理。

[下一篇](/teaching-topics/cumulative-distribution-functions/)改由 $\mathbb{P}(X\leqslant x)$ 出發，介紹對兩種型態都適用的累積分配函數。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Joseph K. Blitzstein and Jessica Hwang. 2019. *Introduction to Probability*. 2nd ed. Chapman and Hall/CRC.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
