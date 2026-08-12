---
title: "機率密度函數"
subtitle: "Probability Density Functions"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 3
order: 203
permalink: /teaching-topics/ch2-p03-candidate/
date: 2026-08-04
published: false
excerpt: "連續型隨機變數的累積分配函數若能寫成某個非負函數由 $-\\infty$ 積到 $x$ 的積分，被積分的那個函數即為機率密度函數。在機率密度函數連續的點上，由微積分基本定理可知它就是累積分配函數的導函數。它是累積機率的變化率而非機率本身，故只要求非負，不必小於 $1$；在整個值域上的積分為 $1$，落在集合 $A$ 中的機率則為 $A$ 與值域交集上的積分。"
---

[上一篇](/teaching-topics/ch2-p02-candidate/)以 $\mathbb{P}(X\leqslant x)$ 定義累積分配函數，離散型與連續型隨機變數都適用。離散型的累積分配函數由機率質量函數逐點加總而得，連續型則無法以同樣的方式加總。

連續型隨機變數的累積分配函數改由積分表示，被積分的那個函數就是機率密度函數。以下先給出它的定義，再由微積分基本定理得到它與累積分配函數之間的微分關係，並列出它應該滿足的各項性質。

<span id="proposition-24"></span><!-- legacy anchor: 不對應任何環境，不得再指派 -->

<span id="definition-24"></span>
<div id="def-pdf" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.5 (機率密度函數, probability density function, pdf)</div>

若 $X$ 為一連續型隨機變數，cdf 為 <span class="text-nowrap">$F_{\sssig X}(x)$，</span>值域為 $\mathcal{R}\_{\sssig X}$。若非負函數 $f_{\sssig X}(\cdot)$ 滿足

$$
F_{\sssig X}(x)=\int_{-\infty}^{x}f_{\sssig X}(t)\,dt,\quad x\in\mathbb{R}
$$

則稱 $f_{\sssig X}(x)$ 為 $X$ 之**機率密度函數 <span lang="en">(probability density function, pdf)</span>**。

</div>

機率密度函數有一些地方需要注意。

(1) 由此定義可以看出，cdf 的定義在離散型與連續型隨機變數其實是相似的，只是前者為「加」而後者為「積」，由此也衍伸出許多[二者間相似但仍有差異的性質](/teaching-topics/ch2-p04-candidate/)，我們稍後會談到。
{: .topic-paren-item}

(2) 我們曾經提過，cdf 是一種累積機率，若由微積分的角度來看，機率密度函數應不是一種機率，而是**累積機率的變化率**，此點與 pmf 本身即是機率不同。
{: .topic-paren-item}

(3) 由此定義再次審視累積分配函數，可以發現連續型隨機變數的累積分配函數事實上是一種**面積**，我們稍後會[細談這個特點](/teaching-topics/ch2-p04-candidate/)，這裡可以先由下圖理解之。
{: .topic-paren-item}

<figure id="fig-cdf-as-area" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/continuous-cdf-area.svg" alt="一條鐘形密度曲線與橫軸之間的區域，自左端到橫軸上的門檻 x 的部分以淡色填滿；曲線上方標示 f_X(t)，填色區域之中標示 F_X(x)，橫軸變數為 t。">
  <figcaption><span class="topic-figure__label">Fig. 2.4.</span> 累積分配函數值 $F_{\sssig X}(x)$ 是密度曲線 $f_{\sssig X}(t)$ 之下，由左側一路累積到 $t=x$ 為止的面積。</figcaption>
</figure>

若以微積分的觀點理解上圖，我們將得到如下的關係式:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
F^{\prime}_{\sssig X}(x)=\dfrac{dF_{\sssig X}(x)}{dx}, & \text{$x$ 是 $\mathcal{R}_{\sssig X}$ 中的可微分點}\\[0.8em]
0, & \text{$x$ 是 $\mathcal{R}_{\sssig X}$ 中的不可微分點或不在 $\mathcal{R}_{\sssig X}$ 中}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
f_{\sssig X}(x)=
\left\lbrace
\begin{array}{l}
F^{\prime}_{\sssig X}(x)=\dfrac{dF_{\sssig X}(x)}{dx},\\[0.3em]
\quad\text{$x$ 是 $\mathcal{R}_{\sssig X}$ 中的可微分點}\\[0.8em]
0,\\[0.3em]
\quad\text{$x$ 是 $\mathcal{R}_{\sssig X}$ 中的不可微分點}\\[0.3em]
\quad\text{或不在 $\mathcal{R}_{\sssig X}$ 中}
\end{array}
\right.
$$

</div>

上式在 $f_{\sssig X}$ 於 $x$ 處連續時，可由**微積分基本定理 <span lang="en">(fundamental theorem of calculus, FTC)</span>** 直接得到。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

微積分基本定理只在 $f_{\sssig X}$ 於 $x$ 處連續時給出 $F^{\prime}\_{\sssig X}(x)=f_{\sssig X}(x)$，$f_{\sssig X}$ 不連續的點不在它的保證範圍內。整體而言仍有一個較弱的結論: [Definition 2.5](#def-pdf) 要求 $F_{\sssig X}$ 能寫成 $f_{\sssig X}$ 的積分，$F_{\sssig X}$ 因而**絕對連續 <span lang="en">(absolutely continuous)</span>**，由 Lebesgue 微分定理可知該等式**幾乎處處 <span lang="en">(almost everywhere, a.e.)</span>** 成立。不成立的點至多構成一個 Lebesgue 測度為零的集合，$f_{\sssig X}$ 在其上的取值不改變任何一個積分，因此不影響任何機率。

絕對連續這個前提不能省: 單憑 $F_{\sssig X}$ 連續且幾乎處處可微，並不足以求得密度。存在連續而不絕對連續的 cdf，其導數幾乎處處為 $0$，積分起來得到 $0$ 而不是 $1$。上式之所以成立，正是因為 [Definition 2.5](#def-pdf) 已經給出積分表示式。

</div>

透過微積分的觀點來理解這些關係，我們能夠進一步引伸出許多性質，下面就介紹機率密度函數所具備的各種性質。

<div id="thm-pdf-properties" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.2 (pdf 的性質, properties of a pdf)</div>

一連續型隨機變數 $X$ 之機率密度函數 $f_{\sssig X}(x)$ 應滿足以下性質:

<ol class="topic-list-paren">
  <li>
$$
f_{\sssig X}(x)\geqslant 0,\quad\forall x\in\mathcal{R}_{\sssig X}
$$
  </li>
  <li>
<div class="topic-math-layout topic-math-layout--desktop">
$$
\mathbb{P}(X\in\mathcal{R}_{\sssig X})=\int_{x\in\mathcal{R}_{\sssig X}}f_{\sssig X}(x)\,dx=\int_{-\infty}^{\infty}f_{\sssig X}(x)\,dx=1
$$
</div>
<div class="topic-math-layout topic-math-layout--mobile">
$$
\begin{aligned}
\mathbb{P}(X\in\mathcal{R}_{\sssig X})&=\int_{x\in\mathcal{R}_{\sssig X}}f_{\sssig X}(x)\,dx\\[0.4em]
&=\int_{-\infty}^{\infty}f_{\sssig X}(x)\,dx=1
\end{aligned}
$$
</div>
  </li>
  <li>對任意波雷爾集合 $A$，皆有
$$
\mathbb{P}(X\in A)=\int_{x\in A\cap\mathcal{R}_{\sssig X}}f_{\sssig X}(x)\,dx
$$
  </li>
</ol>

</div>

連續型隨機變數引入了微積分的概念，機率密度函數更是由積分定義而來。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

許多讀者將 pdf 的定義誤解為由 cdf 微分而來，事實上這是 pdf 的「性質」而非定義。注意到，pdf 本身的定義是「滿足 $F_{\sssig X}(x)=\int_{-\infty}^{x}f_{\sssig X}(t)\,dt$ 的函數 $f_{\sssig X}(x)$」即可稱為 pdf，因此 pdf 事實上是由積分定義的，而非微分。

</div>

性質 (1) 的成立，乃是由機率密度函數實為累積分配函數的**導函數** (即斜率) 而得，我們可以下圖理解之，亦可以與 [Fig. 2.4](#fig-cdf-as-area) 進行比較，二者事實上是機率密度函數本身的積分與其反導函數的微分二種觀點。

<figure id="fig-pdf-as-derivative" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/pdf-as-derivative.svg" alt="累積分配函數的曲線由左下往右上升，逐漸貼近標示為 1 的水平虛線；橫軸上的 a 以虛線連到曲線上的一點，該點畫有一段切線，並由虛線箭頭指向標示 F 撇 X(a) 等於 f_X(a)。">
  <figcaption><span class="topic-figure__label">Fig. 2.5.</span> 累積分配函數 $F_{\sssig X}(x)$ 在 $x=a$ 處的切線斜率 $F^{\prime}_{\sssig X}(a)$，就是機率密度函數在該點的值 $f_{\sssig X}(a)$。</figcaption>
</figure>

如同前述所提，機率密度函數是**累積機率的變化率**，而非機率本身，故在性質 (1) 的部分即與離散型隨機變數不同，沒有保留機率質量函數必須小於等於 $1$ 的性質；其餘的部分與離散型隨機變數則相似，只要將加總的部分改寫為積分即可得到一樣的結論。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

注意到此處的 $f_{\sssig X}(x)$ 已經不若 $p_{\sssig X}(x)$ 就是機率，而是一種變化率 (或斜率)，因此沒有必要小於 $1$；但由於 cdf $F_{\sssig X}(x)$ 非遞減，故 pdf $f_{\sssig X}(x)$ 會隨之非負。

</div>

若想把密度與面積的關係看得更具體，也可以到 Demos 中的 [From pdf to cdf](/demos/pdf-cdf/) 親自操作，選定連續型分配族並調整其參數，觀察密度的高度可以超過 $1$；移動當前的 $x$，該點左側、密度曲線下方的面積始終等於 cdf 在該點的高度。

<div id="ex-quadratic-density" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.6</div>

<div lang="en" markdown="1">
Suppose that the random variable $X$ has the probability density function

$$
f_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
c(4x-2x^{2}), & 0<x<2\\[0.4em]
0, & \text{otherwise}
\end{array}
\right.
$$

<ol class="topic-list-paren">
  <li>Find the value of $c$.</li>
  <li>Find $\mathbb{P}(X>1)$.</li>
</ol>
</div>

(1) 由 pdf 之性質知道
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
1&=\int_{-\infty}^{\infty}f_{\sssig X}(x)\,dx=\int_{0}^{2}c(4x-2x^{2})\,dx\\[0.45em]
&=c\left[2x^{2}-\frac{2}{3}x^{3}\right]_{0}^{2}=\frac{8}{3}c
\quad\Longrightarrow\quad
c=\frac{3}{8}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
1&=\int_{-\infty}^{\infty}f_{\sssig X}(x)\,dx\\[0.4em]
&=\int_{0}^{2}c(4x-2x^{2})\,dx\\[0.4em]
&=c\left[2x^{2}-\frac{2}{3}x^{3}\right]_{0}^{2}=\frac{8}{3}c\\[0.4em]
&\Longrightarrow\ c=\frac{3}{8}
\end{aligned}
$$

</div>

由於 $c=\frac{3}{8}>0$，可知 $f_{\sssig X}(x)\geqslant0$ 對一切 $0<x<2$ 皆成立，[Theorem 2.2](#thm-pdf-properties) 第 (1) 款的非負性得到滿足，故
{: .topic-paren-cont}

$$
c=\frac{3}{8}
$$

(2) 由 $c=\frac{3}{8}$ 可計算
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X>1)=\int_{1}^{2}\frac{3}{8}(4x-2x^{2})\,dx=\left[\frac{3}{4}x^{2}-\frac{1}{4}x^{3}\right]_{1}^{2}=\frac{1}{2}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X>1)&=\int_{1}^{2}\frac{3}{8}(4x-2x^{2})\,dx\\[0.4em]
&=\left[\frac{3}{4}x^{2}-\frac{1}{4}x^{3}\right]_{1}^{2}=\frac{1}{2}
\end{aligned}
$$

</div>

</div>

<div id="ex-uniform-real-roots" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.7</div>

<div lang="en" markdown="1">
Suppose that $Y\sim\mathcal{U}(0,10)$. What is the probability that the quadratic equation <span class="text-nowrap">$g(x)=x^{2}+xY+Y+1=0$</span> has two real roots?
</div>

由 $Y\sim\mathcal{U}(0,10)$ 可知

$$
f_{\sssig Y}(y)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{1}{10}, & 0<y<10\\[0.6em]
0, & \text{otherwise}
\end{array}
\right.
$$

又 $g(x)=x^{2}+xY+Y+1=0$ 具二實根之條件為

$$
Y^{2}-4\cdot1\cdot(Y+1)\geqslant0
$$

此即 $Y\geqslant2+2\sqrt{2}$ 或 $Y\leqslant2-2\sqrt{2}$。由於 $2-2\sqrt{2}<0$，後者在 $Y$ 的值域上不會發生，故所求為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
&\mathbb{P}\bigl(Y\geqslant2+2\sqrt{2}\ \text{or}\ Y\leqslant2-2\sqrt{2}\bigr)=\mathbb{P}\bigl(Y\geqslant2+2\sqrt{2}\bigr)\\[0.4em]
&\quad=\int_{2+2\sqrt{2}}^{10}\frac{1}{10}\,dy=\frac{1}{10}\Bigl[10-\bigl(2+2\sqrt{2}\bigr)\Bigr]=\frac{4}{5}-\frac{1}{5}\sqrt{2}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}\bigl(Y\geqslant2+2\sqrt{2}\ \text{or}\ Y\leqslant2-2\sqrt{2}\bigr)\\[0.4em]
&\quad=\mathbb{P}\bigl(Y\geqslant2+2\sqrt{2}\bigr)\\[0.4em]
&\quad=\int_{2+2\sqrt{2}}^{10}\frac{1}{10}\,dy\\[0.4em]
&\quad=\frac{1}{10}\Bigl[10-\bigl(2+2\sqrt{2}\bigr)\Bigr]\\[0.4em]
&\quad=\frac{4}{5}-\frac{1}{5}\sqrt{2}
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

本題所使用的分配，是**均勻分配 <span lang="en">(uniform distribution)</span>**，在往後介紹常見機率分配模型時，我們將會詳細介紹這個重要的分配。

</div>

<div id="ex-normal-gamma-constants" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.8</div>

<div lang="en" markdown="1">
Find the value of the constant $c$ that makes each of the following functions a probability density function.

<ol class="topic-list-paren">
  <li>$g(x)=c\cdot e^{-\frac{(x-3)^{2}}{12}},\quad x\in\mathbb{R}$</li>
  <li>$h(x)=c\cdot x^{6}e^{-3x},\quad x>0$</li>
</ol>
</div>

(1) 由 pdf 之性質知道
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
1&=\int_{-\infty}^{\infty}g(x)\,dx=\int_{-\infty}^{\infty}c\cdot e^{-\frac{(x-3)^{2}}{12}}\,dx\\[0.45em]
&=c\sqrt{2\pi\cdot6}\int_{-\infty}^{\infty}\frac{1}{\sqrt{2\pi\cdot6}}\,e^{-\frac{(x-3)^{2}}{12}}\,dx\\[0.45em]
&=c\sqrt{2\pi\cdot6}
\quad\Longrightarrow\quad
c=\frac{1}{\sqrt{2\pi\cdot6}}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
1&=\int_{-\infty}^{\infty}g(x)\,dx\\[0.45em]
&=\int_{-\infty}^{\infty}c\cdot e^{-\frac{(x-3)^{2}}{12}}\,dx\\[0.45em]
&=c\sqrt{2\pi\cdot6}\\[0.45em]
&\qquad\cdot\int_{-\infty}^{\infty}\frac{1}{\sqrt{2\pi\cdot6}}\,e^{-\frac{(x-3)^{2}}{12}}\,dx\\[0.45em]
&=c\sqrt{2\pi\cdot6}\ \Longrightarrow\ c=\frac{1}{\sqrt{2\pi\cdot6}}
\end{aligned}
$$

</div>

由於 $c=\frac{1}{\sqrt{2\pi\cdot6}}>0$，可知 $g(x)\geqslant0$ 對一切 $x\in\mathbb{R}$ 皆成立，[Theorem 2.2](#thm-pdf-properties) 第 (1) 款的非負性得到滿足，故
{: .topic-paren-cont}

$$
c=\frac{1}{\sqrt{2\pi\cdot6}}
$$

(2) 由 pdf 之性質知道
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
1&=\int_{0}^{\infty}h(x)\,dx=\int_{0}^{\infty}c\cdot x^{6}e^{-3x}\,dx=c\int_{0}^{\infty}x^{6}e^{-3x}\,dx\\[0.45em]
&=c\left(\frac{1}{3}\right)^{7}\Gamma(7)=c\left(\frac{1}{3}\right)^{7}6!
\quad\Longrightarrow\quad
c=\frac{3^{7}}{6!}=\frac{243}{80}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
1&=\int_{0}^{\infty}h(x)\,dx\\[0.45em]
&=\int_{0}^{\infty}c\cdot x^{6}e^{-3x}\,dx\\[0.45em]
&=c\int_{0}^{\infty}x^{6}e^{-3x}\,dx=c\left(\frac{1}{3}\right)^{7}\Gamma(7)\\[0.45em]
&=c\left(\frac{1}{3}\right)^{7}6!\ \Longrightarrow\ c=\frac{3^{7}}{6!}=\frac{243}{80}
\end{aligned}
$$

</div>

由於 $c=\frac{243}{80}>0$，可知 $h(x)\geqslant0$ 對一切 $x>0$ 皆成立，[Theorem 2.2](#thm-pdf-properties) 第 (1) 款的非負性得到滿足，故
{: .topic-paren-cont}

$$
c=\frac{243}{80}
$$

</div>

<div id="ex-broken-stick-beta" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.9</div>

<div lang="en" markdown="1">
Suppose that a stick of unit length is broken at a single point, and that the position $X$ of the break has the density

$$
f_{\sssig X}(x)=c\,x(1-x),\quad 0<x<1
$$

<ol class="topic-list-paren">
  <li>Find $c$.</li>
</ol>
</div>

(1) 由 pdf 之性質知道
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
1&=\int_{-\infty}^{\infty}f_{\sssig X}(x)\,dx=\int_{0}^{1}c\,x(1-x)\,dx=c\int_{0}^{1}x^{2-1}(1-x)^{2-1}\,dx\\[0.45em]
&=c\cdot\mathcal{B}(2,2)=c\,\frac{\Gamma(2)\Gamma(2)}{\Gamma(2+2)}=c\,\frac{1!\cdot1!}{3!}
\quad\Longrightarrow\quad
c=6
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
1&=\int_{-\infty}^{\infty}f_{\sssig X}(x)\,dx\\[0.45em]
&=\int_{0}^{1}c\,x(1-x)\,dx\\[0.45em]
&=c\int_{0}^{1}x^{2-1}(1-x)^{2-1}\,dx\\[0.45em]
&=c\cdot\mathcal{B}(2,2)=c\,\frac{\Gamma(2)\Gamma(2)}{\Gamma(2+2)}\\[0.45em]
&=c\,\frac{1!\cdot1!}{3!}\ \Longrightarrow\ c=6
\end{aligned}
$$

</div>

由於 $c=6>0$，可知 $f_{\sssig X}(x)\geqslant0$ 對一切 $0<x<1$ 皆成立，[Theorem 2.2](#thm-pdf-properties) 第 (1) 款的非負性得到滿足，故
{: .topic-paren-cont}

$$
c=6
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

上述兩個問題中，分別使用到**高斯積分 <span lang="en">(Gaussian integral)</span>** 的變化型、**伽瑪函數 <span lang="en">(gamma function)</span>** 的變化型與**貝塔函數 <span lang="en">(beta function)</span>**，在稍後的章節，常見機率分配模型將會經常使用這些積分式。

此外，[Example 2.8](#ex-normal-gamma-constants) 中的兩個小題，事實上是常態分配 <span lang="en">(normal distribution)</span> 與伽瑪分配 <span lang="en">(gamma distribution)</span>，而 [Example 2.9](#ex-broken-stick-beta) 的則是貝塔分配 <span lang="en">(beta distribution)</span>，在往後的章節中，我們都會詳述這些分配。

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

伽瑪函數 (或稱伽瑪積分) 亦被稱作歐拉第二型積分 <span lang="en">(Euler integral of the second kind)</span>，與貝塔函數，或稱貝塔積分，亦被稱作歐拉第一型積分 <span lang="en">(Euler integral of the first kind)</span>；此二者與高斯積分，同為機率統計中時常使用的三個積分式。

</div>

## 本篇小結

機率密度函數是由積分定義的: 若非負函數 $f_{\sssig X}$ 能使 $F_{\sssig X}(x)=\int_{-\infty}^{x}f_{\sssig X}(t)\,dt$ 對一切 $x\in\mathbb{R}$ 成立，即稱 $f_{\sssig X}$ 為 $X$ 的機率密度函數。由微積分基本定理，在值域中的可微分點上有 $f_{\sssig X}(x)=F^{\prime}\_{\sssig X}(x)$，其餘各點取 $0$；這是 pdf 的性質，而不是它的定義。

pdf 是累積機率的變化率，不是機率本身，故沒有小於等於 $1$ 的限制，只需非負；它在整個值域上的積分為 $1$，而 $X$ 落在集合 $A$ 中的機率，則是 $f_{\sssig X}$ 在 $A$ 與值域交集上的積分。本篇四道例題之中，[Example 2.6](#ex-quadratic-density)、[Example 2.8](#ex-normal-gamma-constants) 與 [Example 2.9](#ex-broken-stick-beta) 都由「總積分為 $1$」這一項性質定出待求的常數，後兩題另外用到高斯積分、伽瑪函數與貝塔函數三個積分式；[Example 2.7](#ex-uniform-real-roots) 沒有待求的常數，求的是一個二次方程式具有二實根的機率。

[下一篇](/teaching-topics/ch2-p04-candidate/)把機率質量函數、機率密度函數與累積分配函數連結起來，用以計算各種區間的機率。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Joseph K. Blitzstein and Jessica Hwang. 2019. *Introduction to Probability*. 2nd ed. Chapman and Hall/CRC.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
