---
title: "均勻分配與機率積分轉換"
subtitle: "The Uniform Distribution and the Probability Integral Transformation"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 4
topic: 14
order: 414
permalink: /teaching-topics/ch4-p14-candidate/
date: 2026-08-12
published: false
excerpt: "均勻分配的機率密度在整個值域上處處相同，它的 cdf 是唯一一條直線，而其中的標準均勻分配 $\\mathcal{U}(0,\\ 1)$ 更把這條直線變成恆等函數，變數值本身就是累積機率。本篇先給出均勻分配的定義，完整推導期望值 $\\frac{a+b}{2}$、變異數 $\\frac{(b-a)^{2}}{12}$ 與動差母函數，再證明任何一個均勻分配都可以由標準均勻分配先伸縮 $b-a$ 倍、再平移 $a$ 而得。由於這個轉換所用的函數正是該均勻分配自己的 cdf，同樣的手法可以推廣到任意的連續分配，這就是機率積分轉換與逆機率積分轉換兩個定理的內容。最後以三道例題演練均勻分配的截尾期望值、以自己的 cdf 轉換之後所得變數的分配，以及如何由標準均勻分配生出指數分配。"
---

[上一篇](/teaching-topics/ch4-p13-candidate/)以[韋伯分配](/teaching-topics/ch4-p13-candidate/#def-weibull-distribution)、[可靠度函數](/teaching-topics/ch4-p13-candidate/#def-reliability-function)與[風險函數](/teaching-topics/ch4-p13-candidate/#def-hazard-function)作結，卜瓦松過程所衍生的各個機率模型至此全部給出。本篇轉入第三大類的機率模型，也就是與貝塔分配相關的一系列分配，而這一類之中最基本的一個，是值域上每一個點都具有相同機率密度的均勻分配。

均勻分配的 cdf 是一條直線，其中的標準均勻分配更把這條直線變成恆等函數，變數值本身就代表累積機率。本篇先給出均勻分配的定義並完整推導其期望值、變異數與動差母函數，再說明所有的均勻分配都可以由標準均勻分配伸縮平移而得。由於這個轉換所用的函數正是該均勻分配自己的 cdf，同樣的手法可以推廣到任意的連續分配，機率積分轉換與逆機率積分轉換兩個定理就是這樣來的；這兩個定理在第二章的 [Proposition 2.4](/teaching-topics/one-to-one-transformations/#prop-probability-integral-transform) 曾經先行敘述，本篇把它們放回均勻分配的脈絡之中。最後以三道例題作為演練。

## 均勻分配

<div id="def-uniform-distribution" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 4.18 (均勻分配, uniform distribution)</div>

**適用範圍**:

令 $X$ 為一個連續隨機變數，其值域中的所有點皆具有相同機率密度。

**值域範圍**:

$$
\mathcal{R}_{\sssig X}=\lbrace\,x\mid a\leqslant x\leqslant b\,\rbrace
$$

**表示式**:

$$
X\sim\mathcal{U}(a,\ b)
$$

**參數與參數範圍**:

$a,b\in\mathbb{R}$ 為位置參數，同時 $a$ 為值域下界、$b$ 為值域上界，且 <span class="text-nowrap">$a<b$。</span>

**機率函數**:

$$
f_{\sssig X}(x)=\frac{1}{\,b-a\,},\ a\leqslant x\leqslant b
$$

**期望值、變異數、動差母函數**:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\mathbb{E}(X)=\frac{\,a+b\,}{2},\qquad \mathrm{Var}(X)=\frac{\,(b-a)^{2}\,}{12}\\[0.7em]
M_{\sssig X}(t)=\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{\,e^{bt}-e^{at}\,}{(b-a)t}, & t\neq0\\[0.9em]
1, & t=0
\end{array}
\right.
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{E}(X)=\frac{\,a+b\,}{2}\\[0.5em]
\mathrm{Var}(X)=\frac{\,(b-a)^{2}\,}{12}\\[0.5em]
M_{\sssig X}(t)=\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{\,e^{bt}-e^{at}\,}{(b-a)t}, & t\neq0\\[0.9em]
1, & t=0
\end{array}
\right.
\end{gathered}
$$

</div>

</div>

均勻分配 <span lang="en">(uniform distribution)</span> 有一些地方需要注意:

(1) 我們證明其機率函數為一個合法的機率函數與期望值、變異數與動差母函數如下:
{: .topic-paren-item}

<div class="topic-proof" markdown="1">
**Proof.** 先驗證機率函數在值域上的積分為 <span class="text-nowrap">$1$，</span>即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\int_{x\in\mathcal{R}_{\sssig X}}f_{\sssig X}(x)\,dx=\int_{a}^{b}\frac{1}{\,b-a\,}dx=\frac{1}{\,b-a\,}\int_{a}^{b}1\,dx=\frac{b-a}{\,b-a\,}=1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\int_{x\in\mathcal{R}_{\sssig X}}f_{\sssig X}(x)\,dx\\[0.45em]
&\quad =\int_{a}^{b}\frac{1}{\,b-a\,}dx=\frac{1}{\,b-a\,}\int_{a}^{b}1\,dx\\[0.45em]
&\quad =\frac{b-a}{\,b-a\,}=1
\end{aligned}
$$

</div>

接著求期望值，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(X)=\int_{x\in\mathcal{R}_{\sssig X}}x\,f_{\sssig X}(x)\,dx=\frac{1}{\,b-a\,}\int_{a}^{b}x\,dx=\left[\frac{x^{2}}{\,2(b-a)\,}\right]^{b}_{a}=\frac{\,a+b\,}{2}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\int_{x\in\mathcal{R}_{\sssig X}}x\,f_{\sssig X}(x)\,dx\\[0.45em]
&=\frac{1}{\,b-a\,}\int_{a}^{b}x\,dx\\[0.45em]
&=\left[\frac{x^{2}}{\,2(b-a)\,}\right]^{b}_{a}=\frac{\,a+b\,}{2}
\end{aligned}
$$

</div>

又可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\bigl(X^{2}\bigr)=\int_{x\in\mathcal{R}_{\sssig X}}x^{2}f_{\sssig X}(x)\,dx=\frac{1}{\,b-a\,}\int_{a}^{b}x^{2}\,dx=\left[\frac{x^{3}}{\,3(b-a)\,}\right]^{b}_{a}=\frac{\,a^{2}+ab+b^{2}\,}{3}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl(X^{2}\bigr)&=\int_{x\in\mathcal{R}_{\sssig X}}x^{2}f_{\sssig X}(x)\,dx\\[0.45em]
&=\frac{1}{\,b-a\,}\int_{a}^{b}x^{2}\,dx\\[0.45em]
&=\left[\frac{x^{3}}{\,3(b-a)\,}\right]^{b}_{a}\\[0.45em]
&=\frac{\,a^{2}+ab+b^{2}\,}{3}
\end{aligned}
$$

</div>

則變異數為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}(X)=\mathbb{E}\bigl(X^{2}\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}=\frac{\,a^{2}+ab+b^{2}\,}{3}-\left(\frac{\,a+b\,}{2}\right)^{2}=\frac{\,(b-a)^{2}\,}{12}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(X)&=\mathbb{E}\bigl(X^{2}\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}\\[0.45em]
&=\frac{\,a^{2}+ab+b^{2}\,}{3}-\left(\frac{\,a+b\,}{2}\right)^{2}\\[0.45em]
&=\frac{\,(b-a)^{2}\,}{12}
\end{aligned}
$$

</div>

最後求動差母函數，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{\sssig X}(t)&=\mathbb{E}\bigl(e^{tX}\bigr)=\int_{a}^{b}e^{tx}\frac{1}{\,b-a\,}dx=\frac{1}{\,b-a\,}\int_{a}^{b}e^{tx}\,dx\\[0.45em]
&=\left\lbrace
\begin{array}{c@{\quad}l}
\left[\dfrac{e^{tx}}{\,(b-a)t\,}\right]^{b}_{a}=\dfrac{\,e^{bt}-e^{at}\,}{(b-a)t}, & t\neq0\\[0.9em]
1, & t=0
\end{array}
\right.
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&M_{\sssig X}(t)=\mathbb{E}\bigl(e^{tX}\bigr)\\[0.45em]
&\quad =\int_{a}^{b}e^{tx}\frac{1}{\,b-a\,}dx=\frac{1}{\,b-a\,}\int_{a}^{b}e^{tx}\,dx\\[0.45em]
&\quad =\left\lbrace
\begin{array}{c@{\ \,}l}
\left[\dfrac{e^{tx}}{\,(b-a)t\,}\right]^{b}_{a}, & t\neq0\\[0.8em]
1, & t=0
\end{array}
\right.\\[0.45em]
&\quad =\left\lbrace
\begin{array}{c@{\ \,}l}
\dfrac{\,e^{bt}-e^{at}\,}{(b-a)t}, & t\neq0\\[0.8em]
1, & t=0
\end{array}
\right.
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

均勻分配的動差母函數在 $t=0$ 處被定義為 $1$ 的原因，是為了滿足對任意的 <span class="text-nowrap">$h>0$，</span>$-h<t<h$ 都應該可微分。

</div>

(2) 令 <span class="text-nowrap">$Y\sim\mathcal{U}(a,\ b)$，</span>則 $Y$ 的 cdf 為
{: .topic-paren-item}

$$
F_{\sssig Y}(y)=\left\lbrace
\begin{array}{c@{\quad}l}
0, & y<a\\[0.5em]
\dfrac{\,y-a\,}{b-a}, & a\leqslant y\leqslant b\\[0.7em]
1, & y>b
\end{array}
\right.
$$

這是**唯一一個線性的 cdf**，而**均勻分配一族是唯一一個具有線性 cdf 的分配族**。
{: .topic-paren-cont}

(3) 眾多均勻分配之中，有一個特例是**標準均勻分配 <span lang="en">(standard uniform distribution)</span>**，有許多和均勻分配有關的特殊性質都是基於這個特例而衍伸出來的，見以下敘述:
{: .topic-paren-item}

**標準均勻分配**是指 <span class="text-nowrap">$U\sim\mathcal{U}(0,\ 1)$，</span>這種均勻分配相當常用，並且其 cdf 為
{: .topic-paren-cont}

$$
F_{\sssig U}(u)=\left\lbrace
\begin{array}{c@{\quad}l}
0, & u<0\\[0.35em]
u, & 0\leqslant u\leqslant1\\[0.35em]
1, & u>1
\end{array}
\right.
$$

這個 cdf 非常特別，除了線性的特色外，在 $u\in[0,1]$ 時是**恆等函數 <span lang="en">(identical function)</span>**，其變數值本身就代表累積機率，這種特色只有標準均勻分配才有。
{: .topic-paren-cont}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

所有均勻分配都可以由標準均勻分配，透過線性轉換 <span lang="en">(linear transformation)</span> 而得，即令

$$
Y=(b-a)U+a
$$

也就是**先伸縮 $b-a$ 倍，再平移 $a$**，我們可以由其 cdf 證明如下:

<div class="topic-proof" markdown="1">
**Proof.** 由 $U\sim\mathcal{U}(0,\ 1)$ 可知

$$
F_{\sssig U}(u)=\left\lbrace
\begin{array}{c@{\quad}l}
0, & u<0\\[0.35em]
u, & 0\leqslant u\leqslant1\\[0.35em]
1, & u>1
\end{array}
\right.
$$

又令 <span class="text-nowrap">$Y=(b-a)U+a$，</span>則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
F_{\sssig Y}(y)&=\mathbb{P}(Y\leqslant y)=\mathbb{P}\bigl((b-a)U+a\leqslant y\bigr)=\mathbb{P}\left(U\leqslant\frac{\,y-a\,}{b-a}\right)\\[0.45em]
&=\left\lbrace
\begin{array}{c@{\quad}l}
0, & y<a\\[0.5em]
\dfrac{\,y-a\,}{b-a}, & a\leqslant y\leqslant b\\[0.7em]
1, & y>b
\end{array}
\right.
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig Y}(y)&=\mathbb{P}(Y\leqslant y)\\[0.45em]
&=\mathbb{P}\bigl((b-a)U+a\leqslant y\bigr)\\[0.45em]
&=\mathbb{P}\left(U\leqslant\frac{\,y-a\,}{b-a}\right)\\[0.45em]
&=\left\lbrace
\begin{array}{c@{\quad}l}
0, & y<a\\[0.5em]
\dfrac{\,y-a\,}{b-a}, & a\leqslant y\leqslant b\\[0.7em]
1, & y>b
\end{array}
\right.
\end{aligned}
$$

</div>

此即

$$
Y\sim\mathcal{U}(a,\ b)
$$

原式得證。 <span class="topic-qed">$\square$</span>
</div>

事實上，標準均勻分配也可以由任意的均勻分配進行伸縮與平移得到，做法恰巧與上述顛倒，是令

$$
U=\frac{\,Y-a\,}{b-a}
$$

讀者可以使用 cdf 法自行證明。

然而，讀者應該也已經發現，從任意均勻分配轉換為標準均勻分配的過程中所使用的函數，事實上正是該均勻分配自己的 cdf，這並不是巧合，甚至在任意非均勻的連續分配中，我們也同樣可以透過這個手法，在任意分配與標準均勻分配間轉換，見[下列定理](#thm-p-i-t)。

</div>

## 機率積分轉換

<div id="thm-p-i-t" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 4.17 (機率積分轉換, probability integral transform)</div>

令 $X$ 為一連續隨機變數，cdf 為 $F\_{\sssig X}(\cdot)$ 且其反函數 $F^{-1}\_{\sssig X}(\cdot)$ 存在，若令 $U=F\_{\sssig X}(X)$ 為 $X$ 的函數轉換，則可知

$$
U\sim\mathcal{U}(0,\ 1)
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.**

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
F_{\sssig U}(u)&=\mathbb{P}(U\leqslant u)=\mathbb{P}\bigl(F_{\sssig X}(X)\leqslant u\bigr)=\mathbb{P}\bigl(X\leqslant F^{-1}_{\sssig X}(u)\bigr)\\[0.45em]
&=F_{\sssig X}\Bigl(F^{-1}_{\sssig X}(u)\Bigr)=u,\ 0\leqslant u\leqslant1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig U}(u)&=\mathbb{P}(U\leqslant u)\\[0.45em]
&=\mathbb{P}\bigl(F_{\sssig X}(X)\leqslant u\bigr)\\[0.45em]
&=\mathbb{P}\bigl(X\leqslant F^{-1}_{\sssig X}(u)\bigr)\\[0.45em]
&=F_{\sssig X}\Bigl(F^{-1}_{\sssig X}(u)\Bigr)\\[0.45em]
&=u,\ 0\leqslant u\leqslant1
\end{aligned}
$$

</div>

此即

$$
U\sim\mathcal{U}(0,\ 1)
$$

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

此定理指出，任意隨機變數以「自己的 cdf」進行轉換[^pure-function]後會變為標準均勻分配，且其證明有賴以下兩點:

(1) $F\_{\sssig X}(\cdot)$ 是一個非遞減函數，故若 $F^{-1}\_{\sssig X}(\cdot)$ 存在，則 $F^{-1}\_{\sssig X}(\cdot)$ 也會是一個非遞減函數。
{: .topic-paren-item}

(2) 標準均勻分配是唯一一個 cdf 在 $[0,1]$ 區間內為恆等函數的分配。
{: .topic-paren-item}

</div>

[^pure-function]: 這裡要注意的是，我們是將 $F_{\sssig X}(\cdot)$ 當成一個純粹的函數，而令 $U=F_{\sssig X}(X)$ 為 $X$ 的一個函數轉換。例如: 若 <span class="text-nowrap">$X\sim\mathrm{Exp}(\beta=1)$，</span>則我們是將其在 $[0,\infty)$ 區間內的部分 $F_{\sssig X}(x)=1-e^{-x},\ 0\leqslant x<\infty$ 當成一個純粹的函數，而令 $U=F_{\sssig X}(X)=1-e^{-X}$ 為 $X$ 的函數轉換，而後求取 $U$ 的 cdf。

## 逆機率積分轉換

<div id="thm-i-p-i-t" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 4.18 (逆機率積分轉換, inverse probability integral transform)</div>

令 $U\sim\mathcal{U}(0,\ 1)$ 為一標準均勻分配，$0\leqslant g(\cdot)\leqslant1$ 為一非遞減函數，且其反函數 $g^{-1}(\cdot)$ 存在，若令 $X=g^{-1}(U)$ 為 $U$ 的函數轉換，則 $g(\cdot)$ 為 $X$ 的 cdf，此即

$$
F_{\sssig X}(x)=g(x)
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.**

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
F_{\sssig X}(x)&=\mathbb{P}(X\leqslant x)=\mathbb{P}\bigl(g^{-1}(U)\leqslant x\bigr)=\mathbb{P}\bigl(U\leqslant g(x)\bigr)\\[0.45em]
&=F_{\sssig U}\Bigl(g(x)\Bigr)=g(x),\ 0\leqslant g(x)\leqslant1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig X}(x)&=\mathbb{P}(X\leqslant x)\\[0.45em]
&=\mathbb{P}\bigl(g^{-1}(U)\leqslant x\bigr)\\[0.45em]
&=\mathbb{P}\bigl(U\leqslant g(x)\bigr)\\[0.45em]
&=F_{\sssig U}\Bigl(g(x)\Bigr)\\[0.45em]
&=g(x),\ 0\leqslant g(x)\leqslant1
\end{aligned}
$$

</div>

此即

$$
F_{\sssig X}(x)=g(x)
$$

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個定理也被稱作逆抽樣轉換，其內容事實上是第一部分的反敘述。我們對標準均勻分配以 $g^{-1}(\cdot)$ 進行函數轉換，則轉換後變數的 cdf 就是 $g(\cdot)$ 這個函數，換句話說，若以「欲求取之分配的 cdf 的反函數」對標準均勻分配進行函數轉換，則轉換後的分配即是欲求取的分配。

這個性質在實務上的用途非常廣泛，因為在較底層的運算系統中，所謂的「隨機數」就是標準均勻分配的隨機變數，也就是 $0$ 到 $1$ 之間的隨機亂數，若要以這個僅有的隨機系統生出具有各式分配的「隨機變數」，便要借助此定理來達成。

</div>

機率積分轉換 <span lang="en">(probability integral transformation)</span> 與逆機率積分轉換 <span lang="en">(inverse probability integral transformation)</span> 事實上使用了同一組關係式，只是表示法不相同，此即

$$
\boxed{\ U=F_{\sssig X}(X)\ \ \Longleftrightarrow\ \ X=F^{-1}_{\sssig X}(U)\ }
$$

至於為什麼是以 $X$ 的 cdf $F_{\sssig X}(\cdot)$ 作為 $\mathcal{U}(0,\ 1)$ 分配與任意 $X$ 的分配間聯繫的橋樑，其實是因為 $X$ 的 cdf $F_{\sssig X}(\cdot)$ 記錄了關於 $X$ 的所有特殊的資訊，其中包含關於伸縮回恆等函數所需要的訊息，都被完整地記錄下來，其概念可以由下方的兩張圖理解:

<!-- fig-pending: uniform-cdf-identity
     Fig. 4.2，兩個面板，對應書稿 mathstatch4.tex 第 2766 行與第 2792 行的兩個 tikzpicture
     (書稿把它們分別放在 .4\textwidth 與 .55\textwidth 的兩個 minipage 內，橫排成一列;
     網頁桌面版維持左右並排，390 px 改為上下堆疊，左面板在上、右面板在下)。
     左面板 (書稿第 2766 至 2790 行，畫的是標準均勻分配的 cdf):
       座標軸為兩條帶箭頭的實線，x 軸自 (0,0) 到 (3.2,0)，y 軸自 (0,0) 到 (0,3)。
       主線是自 (0,0) 到 (3,3) 的直線段，即 [0,1] 上的恆等函數。
       y 軸兩個刻度: y=1 標 $F_{\sssig U}(a)=a$，y=2 標 $F_{\sssig U}(b)=b$，標示置於軸的左側。
       x 軸兩個刻度: x=1 標 $a$，x=2 標 $b$，標示置於軸的下方。
       四段虛線: (0,2) 到 (2,2)、(2,2) 到 (2,0)、(0,1) 到 (1,1)、(1,1) 到 (1,0)。
       兩處文字標示: (3.5,3.3) 的下方寫 $F_{\sssig U}(u)$，(3.5,0.15) 的下方寫 $u$。
     右面板 (書稿第 2792 至 2839 行，畫的是一般連續分配的 cdf):
       座標軸為兩條帶箭頭的實線，x 軸自 (0,0) 到 (6.2,0)，y 軸自 (0,0) 到 (0,3)。
       主線是書稿以 \def\normaltwo{\x,{2.7*exp(2*(\x-3))/(1+exp(2*(\x-3)))}} 定義的
       S 形遞增曲線，繪製區間 domain 0:6、samples 200，上方水平漸近線為 y=2.7。
       y 軸兩個刻度: y=0.956728 標 $F_{\sssig X}(a)$，y=2.317002 標 $F_{\sssig X}(b)$。
       x 軸兩個刻度: x=2.7 標 $a$，x=3.9 標 $b$。
       四段虛線: (0,2.317002) 到 (3.9,2.317002)、(3.9,2.317002) 到 (3.9,0)、
       (0,0.956728) 到 (2.7,0.956728)、(2.7,0.956728) 到 (2.7,0)。
       兩處文字標示: (6.75,3) 的下方寫 $F_{\sssig X}(x)$，(6.5,0.15) 的下方寫 $x$。
     書稿在右面板中被註解掉的兩項不畫: 由 (3.9,2.317002) 彎向 (5,1.5) 的虛線箭頭，
     以及 $F^{\prime}_{\sssig X}(a)=f_{\sssig X}(a)$ 這一行說明文字。
     兩個面板都不畫刻度數值，也不另寫軸名，軸名由上述文字標示代替。
     兩個面板的 y 軸尺度不同 (左面板到 3、右面板的曲線漸近於 2.7)，照書稿保留，
     不為了對齊而統一，變更須先報作者裁定。
     檔名 uniform-cdf-identity.svg，anchor 取 #fig-uniform-cdf-identity，
     caption 起首為 Fig. 4.2.，內容說明左面板的 cdf 在 [0,1] 上是恆等函數、
     右面板是一般分配的 cdf，兩者在 a 與 b 兩點的 cdf 值互相對照。
     圖畫好之後，上一段末的「由下方的兩張圖理解」之後補上指向該 anchor 的 Fig. 4.2 連結。 -->

左側是標準均勻分配的 cdf <span class="text-nowrap">$F_{\sssig U}(u)$，</span>在 $[0,1]$ 的範圍內是恆等函數，不論給任何的 $a$ 與 <span class="text-nowrap">$b$，</span>我們總是可以得到恰好一樣的 cdf 值 $F_{\sssig U}(a)=a$ 與 <span class="text-nowrap">$F_{\sssig U}(b)=b$，</span>一般任意的分配如果要得到這種結果，要將 $U$ 經過妥善的「拉伸」，才能夠從右側的一般化圖示，變成左側的標準均勻分配。

然而，每個隨機變數的分配各有特色，我們一般很難知道該怎麼「拉伸」才能夠從右側漂亮地變到左側，但所幸這個資訊被完整地刻劃在 $X$ 的 cdf $F_{\sssig X}(x)$ 當中，所以選用這個 cdf 當作這個橋樑，便能夠很漂亮地得到這個結果；而機率積分轉換與逆機率積分轉換則分別只是這組關係式在方向上的不同而已。

## 均勻分配與機率積分轉換的例題

<div id="ex-uniform-1" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.38</div>

<div lang="en" markdown="1">
Suppose that $X$ follows the uniform distribution on the interval <span class="text-nowrap">$(0,1)$.</span> Evaluate the conditional expectation <span class="text-nowrap">$\mathbb{E}\left[X\,\middle|\,X<\frac{1}{\,4\,}\right]$.</span>
</div>

<!-- ref-point: 待第三章第 8 篇 (條件分配的例題; 截尾分配的定義在書稿 mathstatch3.tex
     第 1506 至 1513 行的註記，該註記給出離散型與連續型兩式，網頁 anchor 於該篇撰寫時
     依 CH3_NUMBERING.md 定案) 發布後，將下一句的「截尾分配的定義」改為指向該 anchor
     的站內連結。 -->

由截尾分配的定義可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f_{\sssig X}\left(x\,\middle|\,x<\frac{1}{\,4\,}\right)&=\frac{f_{\sssig X}(x)}{\,\mathbb{P}\left(X<\frac{1}{\,4\,}\right)\,}=\frac{1}{\int_{0}^{1/4}f_{\sssig X}(x)\,dx}\\[0.45em]
&=\frac{1}{\,1/4\,}=4,\ 0<x<\frac{1}{\,4\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&f_{\sssig X}\left(x\,\middle|\,x<\frac{1}{\,4\,}\right)\\[0.45em]
&\quad =\frac{f_{\sssig X}(x)}{\,\mathbb{P}\left(X<\frac{1}{\,4\,}\right)\,}=\frac{1}{\int_{0}^{1/4}f_{\sssig X}(x)\,dx}\\[0.45em]
&\quad =\frac{1}{\,1/4\,}=4,\ 0<x<\frac{1}{\,4\,}
\end{aligned}
$$

</div>

所求為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\left[X\,\middle|\,X<\frac{1}{\,4\,}\right]&=\int_{0}^{1/4}x\,f_{\sssig X}\left(x\,\middle|\,x<\frac{1}{\,4\,}\right)dx\\[0.45em]
&=\int_{0}^{1/4}4x\,dx=\Bigl[2x^{2}\Bigr]^{\frac{1}{4}}_{0}=\frac{1}{\,8\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}\left[X\,\middle|\,X<\frac{1}{\,4\,}\right]\\[0.45em]
&\quad =\int_{0}^{1/4}x\,f_{\sssig X}\left(x\,\middle|\,x<\frac{1}{\,4\,}\right)dx\\[0.45em]
&\quad =\int_{0}^{1/4}4x\,dx=\Bigl[2x^{2}\Bigr]^{\frac{1}{4}}_{0}=\frac{1}{\,8\,}
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

一個有趣的事實是，均勻分配的截尾分配必定還是均勻分配，但這事實上也很容易理解，因為我們只是針對某個均勻分配進行範圍上的限制，並沒有改變該分配在此範圍內的「形狀」，而在這個範圍內，每個點的機率密度仍然相同，因此必定還是均勻分配。

</div>

<div id="ex-uniform-2" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.39</div>

<div lang="en" markdown="1">
Suppose that $X$ is a continuous random variable whose cumulative distribution function is <span class="text-nowrap">$F_{\sssig X}(x)$,</span> and let $Y$ denote the transformed variable <span class="text-nowrap">$Y=F_{\sssig X}(X)$.</span> Determine the probability density function of <span class="text-nowrap">$Y$,</span> and evaluate its variance.
</div>

由 cdf 之定義可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
F_{\sssig Y}(y)&=\mathbb{P}(Y\leqslant y)=\mathbb{P}\bigl(F_{\sssig X}(X)\leqslant y\bigr)=\mathbb{P}\bigl(X\leqslant F^{-1}_{\sssig X}(y)\bigr)\\[0.45em]
&=F_{\sssig X}\Bigl(F^{-1}_{\sssig X}(y)\Bigr)=y,\ 0\leqslant y\leqslant1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig Y}(y)&=\mathbb{P}(Y\leqslant y)\\[0.45em]
&=\mathbb{P}\bigl(F_{\sssig X}(X)\leqslant y\bigr)\\[0.45em]
&=\mathbb{P}\bigl(X\leqslant F^{-1}_{\sssig X}(y)\bigr)\\[0.45em]
&=F_{\sssig X}\Bigl(F^{-1}_{\sssig X}(y)\Bigr)\\[0.45em]
&=y,\ 0\leqslant y\leqslant1
\end{aligned}
$$

</div>

所求為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
Y\sim\mathcal{U}(0,\ 1),\qquad f_{\sssig Y}(y)=\left\lbrace
\begin{array}{c@{\quad}l}
1, & 0<y<1\\[0.35em]
0, & \text{o.w.}
\end{array}
\right.,\qquad \sigma^{2}_{\sssig Y}=\frac{\,(1-0)^{2}\,}{12}=\frac{1}{\,12\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
Y\sim\mathcal{U}(0,\ 1)\\[0.6em]
f_{\sssig Y}(y)=\left\lbrace
\begin{array}{c@{\quad}l}
1, & 0<y<1\\[0.35em]
0, & \text{o.w.}
\end{array}
\right.\\[0.6em]
\sigma^{2}_{\sssig Y}=\frac{\,(1-0)^{2}\,}{12}=\frac{1}{\,12\,}
\end{gathered}
$$

</div>

</div>

<div id="ex-uniform-3" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.40</div>

<div lang="en" markdown="1">
Suppose that $X$ follows an exponential distribution whose probability density function is $f(x)=\frac{1}{\,\lambda\,}e^{-\frac{x}{\lambda}}$ for <span class="text-nowrap">$x\geqslant0$.</span>

<ol class="topic-list-paren">
  <li>Find a function $g(x)$ for which the transformed variable $Y=g(X)$ is uniformly distributed on <span class="text-nowrap">$(0,1)$.</span></li>
  <li>Find a function $h(u)$ for which, given a variable $U$ that is uniformly distributed on <span class="text-nowrap">$(0,1)$,</span> the transformed variable $X=h(U)$ has the density $f(x)=\frac{1}{\,\lambda\,}e^{-\frac{x}{\lambda}}$ for <span class="text-nowrap">$x\geqslant0$.</span></li>
</ol>
</div>

(1) 由題意敘述可知，$X$ 之 cdf 為
{: .topic-paren-item}

$$
F_{\sssig X}(x)=\left\lbrace
\begin{array}{c@{\quad}l}
0, & x<0\\[0.5em]
1-e^{-\frac{x}{\lambda}}, & x\geqslant0
\end{array}
\right.
$$

則若令
{: .topic-paren-cont}

$$
g(x)=F_{\sssig X}(x)=1-e^{-\frac{x}{\lambda}},\ x\geqslant0
$$

可由 cdf 之定義知 $Y=g(X)$ 之 cdf 為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig Y}(y)=\mathbb{P}\bigl(g(X)\leqslant y\bigr)=\mathbb{P}\bigl(X\leqslant g^{-1}(y)\bigr)=F_{\sssig X}\bigl(F^{-1}_{\sssig X}(y)\bigr)=y,\ 0<y<1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig Y}(y)&=\mathbb{P}\bigl(g(X)\leqslant y\bigr)\\[0.45em]
&=\mathbb{P}\bigl(X\leqslant g^{-1}(y)\bigr)\\[0.45em]
&=F_{\sssig X}\bigl(F^{-1}_{\sssig X}(y)\bigr)\\[0.45em]
&=y,\ 0<y<1
\end{aligned}
$$

</div>

此即
{: .topic-paren-cont}

$$
Y\sim\mathcal{U}(0,\ 1)
$$

(2) 由上題結果可知，若 <span class="text-nowrap">$U\sim\mathcal{U}(0,\ 1)$，</span>則可令 $U=F_{\sssig X}(X)$ 為 $X$ 之函數轉換，其中 <span class="text-nowrap">$X\sim\mathrm{Exp}(\beta=\lambda)$，</span>且 $F_{\sssig X}(x)=1-e^{-\frac{x}{\lambda}},\ x\geqslant0$ 為 $X$ 之 cdf。
{: .topic-paren-item}

則由 $U=F_{\sssig X}(X)=1-e^{-\frac{X}{\lambda}}$ 的關係反解可知
{: .topic-paren-cont}

$$
X=F^{-1}_{\sssig X}(U)=-\lambda\ln(1-U)
$$

且因為 <span class="text-nowrap">$X\sim\mathrm{Exp}(\beta=\lambda)$，</span>可知所求之
{: .topic-paren-cont}

$$
h(u)=F^{-1}_{\sssig X}(u),\ 0<u<1
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

在操作逆機率積分轉換時，讀者要特別注意，我們在操作流程上，必須先求取「目標分配的 cdf」，如此才能夠知道要透過怎樣的變換，將 $\mathcal{U}(0,\ 1)$ 轉換為該分配，因此以本題而言，我們儘管一看就知道目標分配是 $\mathrm{Exp}(\beta=\lambda)$ 這個分配，仍然需要以這個資訊先行求取其 cdf <span class="text-nowrap">$F_{\sssig X}(x)$。</span>

</div>

## 本篇小結

[Definition 4.18](#def-uniform-distribution) 的均勻分配由「值域中的所有點皆具有相同機率密度」界定，值域為 <span class="text-nowrap">$\lbrace\,x\mid a\leqslant x\leqslant b\,\rbrace$，</span>機率函數因而是常數 <span class="text-nowrap">$\frac{1}{\,b-a\,}$，</span>兩個參數 $a$ 與 $b$ 都是位置參數，分別是值域的下界與上界。證明的四個步驟依序是: 直接積分驗證機率函數的積分為 <span class="text-nowrap">$1$、</span>求得 <span class="text-nowrap">$\mathbb{E}(X)=\frac{\,a+b\,}{2}$、</span>再由 $\mathbb{E}\bigl(X^{2}\bigr)=\frac{\,a^{2}+ab+b^{2}\,}{3}$ 相減得到 <span class="text-nowrap">$\mathrm{Var}(X)=\frac{\,(b-a)^{2}\,}{12}$，</span>最後由定義求得動差母函數。動差母函數在 $t=0$ 處另行定義為 <span class="text-nowrap">$1$，</span>是為了讓它在原點的一個鄰域內都可微分。

均勻分配的 cdf 在 $a$ 與 $b$ 之間是一次式，這是唯一一個線性的 cdf；其中 $a=0$ 且 $b=1$ 的特例即標準均勻分配，它的 cdf 在 $[0,1]$ 上是恆等函數，變數值本身就是累積機率。由 $Y=(b-a)U+a$ 這個先伸縮再平移的轉換，可以由標準均勻分配得到任何一個均勻分配；反過來走則是 <span class="text-nowrap">$U=\frac{\,Y-a\,}{b-a}$，</span>而這個反向的函數恰好就是 $Y$ 自己的 cdf。

把上一段最後這件事推廣到任意的連續分配，就是 [Theorem 4.17](#thm-p-i-t) 與 [Theorem 4.18](#thm-i-p-i-t)。前者說明以 $X$ 自己的 cdf 作轉換所得的 $U=F_{\sssig X}(X)$ 服從標準均勻分配，證明只用到 cdf 非遞減、以及標準均勻分配是唯一一個 cdf 在 $[0,1]$ 上為恆等函數的分配這兩點；後者是它的反敘述，以非遞減函數 $g(\cdot)$ 的反函數轉換標準均勻分配，所得變數的 cdf 就是 $g(\cdot)$ 這個函數。兩者其實是同一組關係式的兩個方向，也就是 $U=F\_{\sssig X}(X)$ 與 $X=F^{-1}\_{\sssig X}(U)$ 這兩個寫法；之所以能夠以 cdf 當作橋樑，是因為把一般的 cdf「拉伸」回恆等函數所需要的資訊，本來就完整地記錄在 cdf 之中。逆機率積分轉換在實務上的用途極廣，因為運算系統所能提供的隨機來源只有 $0$ 到 $1$ 之間的亂數，各式分配的隨機變數都要靠它生出來。

三道例題各練一種用法。[Example 4.38](#ex-uniform-1) 先由截尾分配的定義求出條件密度為常數 <span class="text-nowrap">$4$，</span>再積分得到 <span class="text-nowrap">$\frac{1}{\,8\,}$；</span>由於限制範圍並不改變密度在該範圍內的形狀，均勻分配的截尾分配必定還是均勻分配。[Example 4.39](#ex-uniform-2) 正是機率積分轉換的直接應用，$Y=F_{\sssig X}(X)$ 服從 <span class="text-nowrap">$\mathcal{U}(0,\ 1)$，</span>密度在 $(0,1)$ 上恆為 <span class="text-nowrap">$1$，</span>變異數為 <span class="text-nowrap">$\frac{1}{\,12\,}$。</span>[Example 4.40](#ex-uniform-3) 則把兩個方向各走一次: 先取 $g$ 為[指數分配](/teaching-topics/ch4-p10-candidate/#def-exponential-distribution)自己的 cdf 而得到標準均勻分配，再反解出 $X=-\lambda\ln(1-U)$ 這個式子，由標準均勻分配生回指數分配；操作逆機率積分轉換時，一定要先求出目標分配的 cdf，才知道該用哪一個反函數。

[下一篇](/teaching-topics/ch4-p15-candidate/)介紹貝塔函數與貝塔分配，貝塔分配的值域同樣落在 $0$ 與 $1$ 之間，而標準均勻分配正是它的一個特例。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
