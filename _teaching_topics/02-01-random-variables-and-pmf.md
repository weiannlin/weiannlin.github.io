---
title: "隨機變數與機率質量函數"
subtitle: "Random Variables and Probability Mass Functions"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 1
order: 201
permalink: /lecture-notes/random-variables-and-pmf/
date: 2026-08-04
published: true
excerpt: "隨機變數是定義在樣本空間上的實值函數，要求各個實數門檻以下的原像皆為事件。本篇區分離散型與連續型隨機變數，並介紹離散型的機率質量函數及其基本性質。"
---

[上一章最後一篇](/lecture-notes/bayes-rule-posterior-probability/)完成了分割、全機率定理與貝氏定理的討論。第一章的機率都定義在事件上，而事件是樣本空間的子集合，討論時必須逐個事件處理。

集合論屬於離散數學，較難直接運用微積分等分析方法。本章引入隨機變數，將樣本點對應到實數，使事件得以透過變數值表示，後續的推導便能結合數學分析的工具。

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

隨機變數是一個函數 <span lang="en">(function)</span>，有幾項性質需要特別留意。

(1) 隨機變數 $X(\cdot)$ 是將樣本點對應至實數的函數，此即對任意樣本點 $\omega\in S$ 而言，都有下面的對應關係
{: .topic-paren-item}

$$
X(\omega)\in\mathbb{R}
$$

(2) 由於 $X(\cdot)$ 為一函數，自然應遵守函數的基本性質，其**定義域 (domain)** 是樣本空間 <span class="text-nowrap">$S$，</span>而**對應域 <span lang="en">(codomain)</span>** 是實數集 <span class="text-nowrap">$\mathbb{R}$，</span>至於**值域 (range)** 則記為 $\mathcal{R}_{\sssig X}$ 並為 $\mathbb{R}$ 的子集。特別需要注意的是，同一個樣本點不可對應到多個實數，亦即函數不可一對多。
{: .topic-paren-item}

<span id="可能取值集合的型態"></span>
<div id="note-range-and-support" class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

值域是指隨機變數 $X$ 之所有可能的值形成的集合，記為

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

在部分的教科書上會以其**反映射 <span lang="en">(inverse image)</span>** $X^{-1}(\cdot)$ 定義，等價定義為隨機變數 $X\colon S\to\mathbb{R}$ 必須滿足
{: .topic-paren-cont}

$$
X^{-1}\bigl((-\infty,x]\bigr)=\lbrace\,\omega\mid X(\omega)\leqslant x\,\rbrace\in\mathcal{F}
$$

事實上都在說明同一件事情，也就是只要給定一個實數 $x$，**能夠使 $X(\omega)\leqslant x$ 成立的那些樣本點所收集而成的集合，就必須是個能夠被定義機率的事件**。
{: .topic-paren-cont}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

由於函數對應方向為 <span class="text-nowrap">$X\colon S\to\mathbb{R}$，</span>上式中 $X^{-1}(\cdot)$ 的定義域為 $\mathbb{R}$ 的子集族，映射所得則是樣本空間 $S$ 的子集，且區間 $(-\infty,x]$ 映射回來的樣本點集合須屬於 <span class="text-nowrap">$\mathcal{F}$。</span>此處 $X^{-1}(A)$ 指集合 $A$ 在 $X$ 下的**原像 <span lang="en">(preimage)</span>**，亦即將 $A$ 對應回來的樣本點集合，並不表示 $X$ 具有反函數。

</div>

(4) 隨機變數的定義以區間 $(-\infty,x]$ 為基礎，我們所關心的「隨機變數值」通常是一段範圍；往後也會看到，隨機變數的**機率分配 <span lang="en">(probability distribution)</span>** 最初即由[累積分配函數 <span lang="en">(cumulative distribution function, cdf)</span>](/lecture-notes/cumulative-distribution-functions/#def-cdf) 所界定。但有時我們也關心隨機變數 $X(\omega)$ 等於某個定值，此即
{: .topic-paren-item}

$$
X(\omega)=x
$$

而這其實是集合
{: .topic-paren-cont}

$$
\lbrace\,\omega\mid\omega\in S,\ \text{且}\ X(\omega)=x\,\rbrace
$$

舉例而言，<span class="text-nowrap">$X(\omega)=3$</span> 代表**使得 $X$ 取值為 $3$ 的樣本點集合**。為了書寫簡便，常簡記為 $X=x$ 的形式；由於 $X=x$ 本質上仍是樣本點所形成的集合，故可將其視為一個事件。式中的大寫英文字母代表隨機變數本身，小寫英文字母則代表實數。
{: .topic-paren-cont}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

大寫字母代表的隨機變數具有**隨機性**，而小寫字母僅代表一個固定的實數，兩者不可混淆。往後各篇均依此原則書寫。

</div>

引入隨機變數帶來許多便利，最大的好處是將過去需要逐一討論的樣本點與事件轉化為實數，只要透過變數值便能代表對應的事件；除了討論方便之外，轉化為實數更能讓我們運用微積分等數學分析工具作深入的探討。

給定隨機變數的定義之後，便可進一步討論機率函數的性質。在正式進入機率函數之前，我們先說明隨機變數及其值域的型態。

<div id="def-support-classification" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.2 (隨機變數的分類)</div>

令 $X$ 為定義於機率空間 $(S,\mathcal{F},\mathbb{P})$ 上之隨機變數。

(1) 若值域 $\mathcal{R}_{\sssig X}$ 中之元素個數為有限或可數地無限，則稱 $X$ 為**離散型隨機變數 <span lang="en">(discrete random variable)</span>**。
{: .topic-paren-item}

(2) 若存在非負可積函數 $f_{\sssig X}\colon\mathbb{R}\to[0,\infty)$ 使任意 $x\in\mathbb{R}$ 滿足
{: .topic-paren-item}

$$
\mathbb{P}(X\leqslant x)=\int_{-\infty}^{x}f_{\sssig X}(t)\,dt
$$

則稱 $X$ 為**連續型隨機變數 <span lang="en">(continuous random variable)</span>**。
{: .topic-paren-cont}

</div>

<div id="note-continuous-criterion" class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

將此處定義與第一章的[離散樣本空間與連續樣本空間](/lecture-notes/random-experiments-sample-space-events/#離散樣本空間與連續樣本空間)對照，離散型隨機變數與離散樣本空間同樣以「元素個數為有限或可數無限」作為判準；連續型隨機變數則未沿用「值域元素個數為不可數無限」的說法，而是改以累積機率能否寫成某個非負可積函數的積分來界定。

原因在於值域不可數無限僅為必要條件，並不足以保證累積機率能表為積分。例如後文[混合型隨機變數](/lecture-notes/mixed-random-variables/)一篇中，有些隨機變數的值域雖包含整段連續區間，卻在特定單點上具有正機率，使 $\mathbb{P}(X\leqslant x)$ 在該點發生跳躍而無法單靠積分表示；在高等機率論中，甚至存在每個單點機率皆為 <span class="text-nowrap">$0$、</span>卻仍找不到密度函數 $f_{\sssig X}$ 將累積機率寫成積分的奇異分配。因此，直接以積分表示式界定連續型隨機變數才是嚴謹的做法。

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

若 $X$ 為定義於機率空間 $(S,\mathcal{F},\mathbb{P})$ 上之**離散型**隨機變數，且其值域記為 <span class="text-nowrap">$\mathcal{R}_{\sssig X}$，</span>則我們可定義函數

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

在**機率質量函數**的定義中，$\mathbb{P}(X=x)$ 嚴格而言應寫為 $\mathbb{P}\bigl(\lbrace X(\omega)=x\rbrace\bigr)$ 或 $\mathbb{P}\bigl(\lbrace\,\omega\mid X(\omega)=x\,\rbrace\bigr)$ 這類集合記法，因為機率函數定義於事件集合上，而 $\lbrace\,\omega\mid X(\omega)=x\,\rbrace$ 才是樣本點集合；為求記號簡潔，通例皆簡記為 <span class="text-nowrap">$\mathbb{P}(X=x)$。</span>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

許多教科書亦將 $p_{\sssig X}(x)$ 記為 <span class="text-nowrap">$f_{\sssig X}(x)$，</span>與連續型隨機變數的[機率密度函數](/lecture-notes/probability-density-functions/#def-pdf) <span lang="en">(probability density function, pdf)</span> 共用同一符號，並統稱為**機率函數 <span lang="en">(probability function)</span>**。此處「機率函數」指 pmf 與 pdf，與第一章用來[指稱集合函數 $\mathbb{P}(\cdot)$ 的機率函數](/lecture-notes/event-families-sigma-fields/#term-probability-function)不同，閱讀時須加以區分。

</div>

此外，$\mathbb{P}(X=x)$ **本身就是機率**，故自然滿足[機率三大公理](/lecture-notes/event-families-sigma-fields/#definition-probability-space)，分別對應 [Definition 2.3](#def-pmf) 中的三項性質。機率質量函數僅在值域中的點上具有正機率，如同質量集中在特定位置一般，因此稱為機率質量函數，值域中的這些點亦稱為「質點」。

讀者也可以打開 [From pmf to cdf](/demos/pmf-cdf/)，自行增刪質點、改變各點的機率值，觀察各點的高度如何變化，以及機率總和是否為 $1$。展示的另一半是累積分配函數，[下一篇](/lecture-notes/cumulative-distribution-functions/)才會正式介紹。

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
\begin{gathered}
p_{\sssig X}(1)=\mathbb{P}(X=1)=\mathbb{P}\bigl(\lbrace(0,1)\rbrace\bigr)=\frac{1}{6}\\[0.4em]
p_{\sssig X}(2)=\mathbb{P}(X=2)=\mathbb{P}\bigl(\lbrace(0,2)\rbrace\bigr)=\frac{1}{6}\\[0.4em]
p_{\sssig X}(3)=\mathbb{P}(X=3)=\mathbb{P}\bigl(\lbrace(0,3),(1,2)\rbrace\bigr)=\frac{2}{6}=\frac{1}{3}\\[0.4em]
p_{\sssig X}(4)=\mathbb{P}(X=4)=\mathbb{P}\bigl(\lbrace(1,3)\rbrace\bigr)=\frac{1}{6}\\[0.4em]
p_{\sssig X}(5)=\mathbb{P}(X=5)=\mathbb{P}\bigl(\lbrace(2,3)\rbrace\bigr)=\frac{1}{6}
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig X}(1)&=\mathbb{P}(X=1)\\[0.3em]
&=\mathbb{P}\bigl(\lbrace(0,1)\rbrace\bigr)=\frac{1}{6}
\end{aligned}
$$

$$
\begin{aligned}
p_{\sssig X}(2)&=\mathbb{P}(X=2)\\[0.3em]
&=\mathbb{P}\bigl(\lbrace(0,2)\rbrace\bigr)=\frac{1}{6}
\end{aligned}
$$

$$
\begin{aligned}
p_{\sssig X}(3)&=\mathbb{P}(X=3)\\[0.3em]
&=\mathbb{P}\bigl(\lbrace(0,3),(1,2)\rbrace\bigr)\\[0.3em]
&=\frac{2}{6}=\frac{1}{3}
\end{aligned}
$$

$$
\begin{aligned}
p_{\sssig X}(4)&=\mathbb{P}(X=4)\\[0.3em]
&=\mathbb{P}\bigl(\lbrace(1,3)\rbrace\bigr)=\frac{1}{6}
\end{aligned}
$$

$$
\begin{aligned}
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

本題刻意先列出樣本空間，以銜接第一章的古典機率；熟悉對應關係後，後續例題可直接求取各質點機率，不必逐一列出樣本點。

<div id="ex-geometric-pmf" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.3</div>

<div lang="en" markdown="1">
Let $X$ be a random variable with probability mass function

$$
p_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
c\left(\dfrac{1}{2}\right)^{x}, & x=1,2,\ldots\\[0.6em]
0, & \text{otherwise}
\end{array}
\right.
$$

where $c$ is a constant.

<ol class="topic-list-paren">
  <li>Find the constant $c$ and evaluate <span class="text-nowrap">$\mathbb{P}(X=5)$.</span></li>
</ol>
</div>

由 pmf 之性質知道

<div class="topic-math-follow-before" markdown="1">

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
1=\sum_{x=1}^{\infty}c\left(\frac{1}{2}\right)^{x}
=c\sum_{x=1}^{\infty}\left(\frac{1}{2}\right)^{x}
=c\times\frac{\frac{1}{2}}{1-\frac{1}{2}}
=c
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
1&=\sum_{x=1}^{\infty}c\left(\frac{1}{2}\right)^{x}
=c\sum_{x=1}^{\infty}\left(\frac{1}{2}\right)^{x}\\[0.4em]
&=c\times\frac{\frac{1}{2}}{1-\frac{1}{2}}=c
\end{aligned}
$$

</div>

</div>

<div class="topic-math-follow" markdown="1">

$$
\Longrightarrow\ c=1
$$

</div>

又當 $c=1>0$ 時，$p_{\sssig X}(x)\geqslant0$ 對所有正整數 $x$ 顯然成立，符合 pmf 的非負性要求，以此可計算

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

題幹僅提及 $X$ 的分配與參數 $\theta$ 有關，未明言 $\theta$ 的範圍，此條件可由 pmf 的非負性推得。由遞迴關係 $p_{\sssig X}(1)=\theta\,\mathbb{P}(X=0)$ 與 $\mathbb{P}(X=0)=e^{-\theta}>0$ 可知，機率非負要求 $\theta\geqslant0$ 成立；而當 $\theta=0$ 時，$\mathbb{P}(X=0)=1$ 使 $X$ 退化為常數 $0$ 而失去隨機性，故實務上討論此分配 (即後文將介紹的卜瓦松分配) 時，通常將參數範圍定為 <span class="text-nowrap">$\theta>0$。</span>

</div>

## 本篇小結

第一章把機率定義在事件上。本篇改由隨機變數出發，以定義在樣本空間上的實值函數，把樣本點對應到實數；它必須滿足的條件是對任意實數 $x$ 而言，能使 $X(\omega)\leqslant x$ 成立的樣本點集合都是事件。值域中元素個數為有限或可數無限者為離散型；累積機率可寫成某個非負可積函數之積分者為連續型。

離散型的機率質量函數以 $p_{\sssig X}(x)=\mathbb{P}(X=x)$ 記錄值域中每一個點的單點機率，在值域之外則取 $0$。由於 $\mathbb{P}(X=x)$ 本身就是機率，其三項性質分別對應機率的三大公理。

[下一篇](/lecture-notes/cumulative-distribution-functions/)改由 $\mathbb{P}(X\leqslant x)$ 出發，介紹對兩種型態都適用的累積分配函數。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Joseph K. Blitzstein and Jessica Hwang. 2019. *Introduction to Probability*. 2nd ed. Chapman and Hall/CRC.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
