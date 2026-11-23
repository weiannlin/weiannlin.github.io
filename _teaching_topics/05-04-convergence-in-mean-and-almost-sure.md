---
title: "r 次均方收斂與幾乎確信收斂"
subtitle: "Convergence in r-th Mean and Almost Sure Convergence"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 5
topic: 4
order: 504
permalink: /lecture-notes/convergence-in-mean-and-almost-sure/
date: 2026-08-15
published: false
excerpt: "對正數 $r$ 而言，$r$ 次均方收斂要求 $\\mathbb{E}(\\lvert X_n-X\\rvert^{r})$ 隨 $n\\to\\infty$ 趨於零，幾乎確信收斂則要求序列不收斂之例外事件的機率為零。本篇證明兩者皆強於機率收斂、介紹二次均方收斂判準，並以反例說明均方收斂與幾乎確信收斂之間沒有強弱關係。"
---

[上一篇](/lecture-notes/convergence-in-probability/)給出[機率收斂](/lecture-notes/convergence-in-probability/#def-converge-in-probability)的定義，並說明它與[分配收斂](/lecture-notes/convergence-in-distribution/#def-converge-in-distribution)之間的強弱關係。本篇接著給出另外兩種收斂型態。[Definition 5.3](#def-converge-in-r-mean) 的 $r$ 次均方收斂以「距離的 $r$ 次方的期望值是否趨於零」來界定，[Definition 5.4](#def-converge-almost-surely) 的幾乎確信收斂則轉而探討那些不收斂的樣本點所構成的例外集合，要求這個集合的發生機率必須是零。

這兩種收斂都比機率收斂強。[Theorem 5.4](#thm-rconv-implies-pconv) 由[馬可夫不等式](/lecture-notes/probability-inequalities/#thm-markov)證明 $r$ 次均方收斂導致機率收斂，[Theorem 5.5](#thm-2conv-implies-pconv) 再把這件事用在二次均方收斂上，給出一條只要檢查期望值與變異數就能判定機率收斂的判準；[Theorem 5.6](#thm-asconv-implies-pconv) 則交代幾乎確信收斂同樣導致機率收斂。四道例題分別說明機率收斂不足以保證一次均方收斂、二次均方收斂如何用來求機率極限、機率收斂不足以保證幾乎確信收斂，以及 $r$ 次均方收斂與幾乎確信收斂之間並沒有互相導致的關係。

## $r$ 次均方收斂

<div id="def-converge-in-r-mean" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 5.3 ($r$ 次均方收斂, converge in $r$-th mean)</div>

令 $\lbrace X_n\rbrace_{n=1}^{\infty}$ 為一定義在機率空間上之隨機變數序列，且滿足 $\mathbb{E}\bigl[\lvert X_n\rvert^{r}\bigr]<\infty$ 這個條件，若 $X$ 為一隨機變數，且滿足

$$
\lim_{n\to\infty}\mathbb{E}\bigl[\lvert X_n-X\rvert^{r}\bigr]=0,\ r>0
$$

則稱 $X_n$ $r$ 次均方收斂至 <span class="text-nowrap">$X$，</span>記為

$$
X_n\rconv X
$$

</div>

$r$ 次均方收斂以隨機變數取值距離之 $r$ 次方的期望值定義收斂，是強度高於機率收斂與分配收斂的另一種收斂型態。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

直觀上，$r$ 次均方收斂要求當 $n\to\infty$ 時，$X_n$ 與 $X$ 距離的 $r$ 次方在期望值意義下趨近於 <span class="text-nowrap">$0$。</span>這並非要求每個樣本點上的距離皆為 <span class="text-nowrap">$0$，</span>而是由於 $\lvert X_n-X\rvert^{r}\geqslant0$ 恆為非負，凡是距離不為 $0$ (甚至隨 $n$ 增大) 的取值區域，其對應的機率或機率密度在 $n\to\infty$ 時皆須以足夠快的速率趨於 <span class="text-nowrap">$0$，</span>方能將距離項 $\lvert X_n-X\rvert^{r}$ 的貢獻「抵銷」，使期望值收斂至 <span class="text-nowrap">$0$。</span>

這項「抵銷」要求正是 $r$ 次均方收斂強於機率收斂的原因。機率收斂僅要求事件 $\lbrace\lvert X_n-X\rvert\geqslant\varepsilon\rbrace$ 的尾機率趨於 <span class="text-nowrap">$0$，</span>不計較偏離發生時 $\lvert X_n-X\rvert^{r}$ 的數值有多大；$r$ 次均方收斂則進一步要求尾機率衰減的速率足以壓過 $\lvert X_n-X\rvert^{r}$ 的成長，見下列定理與後續反例。

</div>

## $r$ 次均方收斂導致機率收斂

<div id="thm-rconv-implies-pconv" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 5.4 ($r$ 次均方收斂導致機率收斂)</div>

若 <span class="text-nowrap">$X_n\rconv X$，</span>則有

$$
X_n\pconv X
$$

反之未必成立。

</div>

<div class="topic-proof" markdown="1">
**Proof.**

由馬可夫不等式可知

$$
\mathbb{P}\bigl(\lvert X_n-X\rvert\geqslant\varepsilon\bigr)\leqslant\frac{\,\mathbb{E}\bigl[\lvert X_n-X\rvert^{r}\bigr]\,}{\varepsilon^{r}},\ \varepsilon>0
$$

又由 $r$ 次均方收斂的定義可知

$$
\lim_{n\to\infty}\mathbb{E}\bigl[\lvert X_n-X\rvert^{r}\bigr]=0
$$

故可知道，若 <span class="text-nowrap">$X_n\rconv X$，</span>則我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_n-X\rvert\geqslant\varepsilon\bigr)\leqslant\lim_{n\to\infty}\frac{\,\mathbb{E}\bigl[\lvert X_n-X\rvert^{r}\bigr]\,}{\varepsilon^{r}}=0,\ \varepsilon>0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_n-X\rvert\geqslant\varepsilon\bigr)&\leqslant\lim_{n\to\infty}\frac{\,\mathbb{E}\bigl[\lvert X_n-X\rvert^{r}\bigr]\,}{\varepsilon^{r}}\\[0.45em]
&=0,\ \varepsilon>0
\end{aligned}
$$

</div>

由此可得

$$
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_n-X\rvert<\varepsilon\bigr)=1,\ \varepsilon>0
$$

此即

$$
X_n\pconv X
$$

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div id="ex-pconv-without-first-mean" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.13</div>

<div lang="en" markdown="1">
Let $X_1,X_2,\ldots$ be a sequence of independent discrete random variables such that $X_n$ has pmf $f_n$ given by

$$
f_n(0)=1-\frac{1}{\,n\,},\quad f_n(n)=\frac{1}{\,n\,},\quad n=1,2,3,\ldots
$$

<ol class="topic-list-paren">
  <li>Show that <span class="text-nowrap">$X_n\pconv0$.</span></li>
  <li>Find $\mathbb{E}(X_n)$ and <span class="text-nowrap">$\mathrm{Var}(X_n)$.</span></li>
  <li>Show that $X_n$ does not converge to $0$ in $r$-th mean for <span class="text-nowrap">$r=1$.</span></li>
</ol>
</div>

(1) 依題意可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}\bigl(\lvert X_n-0\rvert<\varepsilon\bigr)=\mathbb{P}(X_n=0)=1-\frac{1}{\,n\,},\ \varepsilon>0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}\bigl(\lvert X_n-0\rvert<\varepsilon\bigr)&=\mathbb{P}(X_n=0)\\[0.45em]
&=1-\frac{1}{\,n\,},\ \varepsilon>0
\end{aligned}
$$

</div>

由此可得
{: .topic-paren-cont}

$$
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_n-0\rvert<\varepsilon\bigr)=1,\ \forall\,\varepsilon>0
$$

此即
{: .topic-paren-cont}

$$
X_n\pconv0
$$

(2) 依題意可得
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\mathbb{E}(X_n)=0\times\Bigl(1-\frac{1}{\,n\,}\Bigr)+n\times\frac{1}{\,n\,}=1\\[0.55em]
\mathrm{Var}(X_n)=\mathbb{E}\bigl(X_n^{2}\bigr)-1^{2}=0^{2}\times\Bigl(1-\frac{1}{\,n\,}\Bigr)+n^{2}\times\frac{1}{\,n\,}-1=n-1
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X_n)&=0\times\Bigl(1-\frac{1}{\,n\,}\Bigr)+n\times\frac{1}{\,n\,}\\[0.45em]
&=1
\end{aligned}
$$

$$
\begin{aligned}
\mathrm{Var}(X_n)&=\mathbb{E}\bigl(X_n^{2}\bigr)-1^{2}\\[0.45em]
&=0^{2}\times\Bigl(1-\frac{1}{\,n\,}\Bigr)\\[0.45em]
&\qquad+n^{2}\times\frac{1}{\,n\,}-1\\[0.45em]
&=n-1
\end{aligned}
$$

</div>

(3) 依題意可得
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\bigl[\lvert X_n-0\rvert\bigr]=\lvert0\rvert\times\Bigl(1-\frac{1}{\,n\,}\Bigr)+\lvert n\rvert\times\frac{1}{\,n\,}=1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[\lvert X_n-0\rvert\bigr]&=\lvert0\rvert\times\Bigl(1-\frac{1}{\,n\,}\Bigr)\\[0.45em]
&\qquad+\lvert n\rvert\times\frac{1}{\,n\,}\\[0.45em]
&=1
\end{aligned}
$$

</div>

故可知
{: .topic-paren-cont}

$$
\lim_{n\to\infty}\mathbb{E}\bigl[\lvert X_n-0\rvert\bigr]=1\neq0
$$

此即 $X_n$ 沒有 $1$ 次均方收斂至 <span class="text-nowrap">$0$。</span>
{: .topic-paren-cont}

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

本題具體呈現尾機率衰減速率與距離成長速率的抗衡；在 $x=n$ 處，機率 $\frac{1}{\,n\,}$ 趨近於 $0$ 的速率恰與距離 $\lvert X_n-0\rvert=n$ 發散的速率相互抵消，乘積恆為 <span class="text-nowrap">$1$，</span>導致 $X_n\pconv0$ 成立卻不具備一次均方收斂。一般而言，設常數 <span class="text-nowrap">$m>0$，</span>若將上題 pmf 改設為

$$
f_n(0)=1-\frac{1}{\,n^{m}\,},\quad f_n(n)=\frac{1}{\,n^{m}\,}
$$

讀者可自行驗證，此時對任意 $0<r<m$ 皆滿足 <span class="text-nowrap">$X_n\rconv0$，</span>而當 $r\geqslant m$ 時則因機率衰減速率不足以壓過 $n^{r}$ 而無法達成 $r$ 次均方收斂。

</div>

## 二次均方收斂與均方一致性

在各階 $r$ 次均方收斂中，實務與推論上最常使用的是 $r=2$ 的二次均方收斂，見下列定理。

<div id="thm-2conv-implies-pconv" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 5.5 (期望值收斂且變異數趨零則二次均方收斂)</div>

令 $\lbrace X_n\rbrace_{n=1}^{\infty}$ 為一定義在機率空間上之隨機變數序列，且

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lim_{n\to\infty}\mathbb{E}(X_n)=c,\quad\lim_{n\to\infty}\mathrm{Var}(X_n)=0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\lim_{n\to\infty}\mathbb{E}(X_n)=c,\\[0.45em]
\lim_{n\to\infty}\mathrm{Var}(X_n)=0
\end{gathered}
$$

</div>

則可知

$$
X_n\xrightarrow{~~2~~}c
$$

並且

$$
X_n\pconv c
$$

其中 $c$ 為一個常數。

</div>

<div class="topic-proof" markdown="1">
**Proof.**

由於

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[\lvert X_n-c\rvert^{2}\bigr]&=\mathbb{E}\bigl[(X_n-c)^{2}\bigr]=\mathbb{E}\bigl[X_n^{2}-2cX_n+c^{2}\bigr]=\mathbb{E}\bigl(X_n^{2}\bigr)-2c\,\mathbb{E}(X_n)+c^{2}\\[0.45em]
&=\mathrm{Var}(X_n)+\bigl[\mathbb{E}(X_n)\bigr]^{2}-2c\,\mathbb{E}(X_n)+c^{2}=\mathrm{Var}(X_n)+\bigl[\mathbb{E}(X_n)-c\bigr]^{2}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[\lvert X_n-c\rvert^{2}\bigr]&=\mathbb{E}\bigl[(X_n-c)^{2}\bigr]\\[0.45em]
&=\mathbb{E}\bigl[X_n^{2}-2cX_n+c^{2}\bigr]\\[0.45em]
&=\mathbb{E}\bigl(X_n^{2}\bigr)-2c\,\mathbb{E}(X_n)+c^{2}\\[0.45em]
&=\mathrm{Var}(X_n)+\bigl[\mathbb{E}(X_n)\bigr]^{2}\\[0.45em]
&\qquad-2c\,\mathbb{E}(X_n)+c^{2}\\[0.45em]
&=\mathrm{Var}(X_n)+\bigl[\mathbb{E}(X_n)-c\bigr]^{2}
\end{aligned}
$$

</div>

若 $\lim_{n\to\infty}\mathbb{E}(X_n)=c$ 且 $\lim_{n\to\infty}\mathrm{Var}(X_n)=0$ 皆成立，則我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lim_{n\to\infty}\mathbb{E}\bigl[\lvert X_n-c\rvert^{2}\bigr]=\lim_{n\to\infty}\Bigl(\mathrm{Var}(X_n)+\bigl[\mathbb{E}(X_n)-c\bigr]^{2}\Bigr)=0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\lim_{n\to\infty}\mathbb{E}\bigl[\lvert X_n-c\rvert^{2}\bigr]&=\lim_{n\to\infty}\Bigl(\mathrm{Var}(X_n)\\[0.45em]
&\qquad+\bigl[\mathbb{E}(X_n)-c\bigr]^{2}\Bigr)\\[0.45em]
&=0
\end{aligned}
$$

</div>

此即

$$
X_n\xrightarrow{~~2~~}c
$$

又由 [Theorem 5.4](#thm-rconv-implies-pconv) 可知

$$
X_n\pconv c
$$

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

上述定理雖為 [Theorem 5.4](#thm-rconv-implies-pconv) 在 $r=2$ 時的推論，實務上卻極為便利；欲證隨機變數序列機率收斂至常數 <span class="text-nowrap">$c$，</span>只需驗證其期望值收斂至 $c$ 且變異數收斂至 $0$ 即可。

在數理統計學中，若估計量序列二次均方收斂至母體參數 <span class="text-nowrap">$\theta$，</span>亦即其平均平方誤差 (mean square error, MSE) 隨 $n\to\infty$ 收斂至 <span class="text-nowrap">$0$，</span>則稱該序列具備**均方一致性 <span lang="en">(mean square consistency)</span>**。以機率收斂定義的一致性 <span lang="en">(consistency)</span> 亦稱**簡單一致性 <span lang="en">(simple consistency)</span>**；相較之下，具備均方一致性的估計量必具備一致性，反之則未必成立。

</div>

<div id="ex-s-squared-mean-square-consistency" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.10 ($S^{2}$ 的一致性, <span lang="en">Continued</span>)</div>

<div lang="en" markdown="1">
Let $X_1,\ldots,X_n\iidto\mathcal{N}(\mu,\sigma^{2})$, and let $S^{2}=\frac{1}{\,n-1\,}\sum_{i=1}^{n}(X_i-\overline{X})^{2}$ be the sample variance. Find the probability limit of <span class="text-nowrap">$S^{2}$.</span>
</div>

**[法二]**

由於

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
S^{2}\sim\mathrm{Gamma}\Bigl(\alpha=\frac{\,n-1\,}{2},\ \beta=\frac{2\sigma^{2}}{\,n-1\,}\Bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
S^{2}&\sim\mathrm{Gamma}\Bigl(\alpha=\frac{\,n-1\,}{2},\\[0.35em]
&\qquad\beta=\frac{2\sigma^{2}}{\,n-1\,}\Bigr)
\end{aligned}
$$

</div>

故可知

<div class="topic-math-follow-before" markdown="1">
<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\mathbb{E}\bigl(S^{2}\bigr)=\frac{\,n-1\,}{2}\times\frac{2\sigma^{2}}{\,n-1\,}=\sigma^{2}\\[0.55em]
\mathrm{Var}\bigl(S^{2}\bigr)=\frac{\,n-1\,}{2}\times\Bigl(\frac{2\sigma^{2}}{\,n-1\,}\Bigr)^{2}=\frac{2\sigma^{4}}{\,n-1\,}
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\mathbb{E}\bigl(S^{2}\bigr)=\frac{\,n-1\,}{2}\times\frac{2\sigma^{2}}{\,n-1\,}=\sigma^{2}
$$

$$
\begin{aligned}
\mathrm{Var}\bigl(S^{2}\bigr)&=\frac{\,n-1\,}{2}\times\Bigl(\frac{2\sigma^{2}}{\,n-1\,}\Bigr)^{2}\\[0.45em]
&=\frac{2\sigma^{4}}{\,n-1\,}
\end{aligned}
$$

</div>
</div>
<div class="topic-math-follow" markdown="1">
<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\Longrightarrow\ \lim_{n\to\infty}\mathbb{E}\bigl(S^{2}\bigr)=\sigma^{2},\quad\lim_{n\to\infty}\mathrm{Var}\bigl(S^{2}\bigr)=0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ &\lim_{n\to\infty}\mathbb{E}\bigl(S^{2}\bigr)=\sigma^{2},\\[0.45em]
&\lim_{n\to\infty}\mathrm{Var}\bigl(S^{2}\bigr)=0
\end{aligned}
$$

</div>
</div>

則可知

$$
S^{2}\pconv\sigma^{2}
$$

</div>

## 幾乎確信收斂

<div id="def-converge-almost-surely" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 5.4 (幾乎確信收斂, converge almost surely)</div>

令 $\lbrace X_n\rbrace_{n=1}^{\infty}$ 為一定義在機率空間上之隨機變數序列，若 $X$ 為定義在相同機率空間中之隨機變數，且滿足

$$
\mathbb{P}\Bigl(\lim_{n\to\infty}\bigl\lvert X_n-X\bigr\rvert<\varepsilon\Bigr)=1,\ \forall\,\varepsilon>0
$$

則稱 $X_n$ 幾乎確信收斂至 <span class="text-nowrap">$X$，</span>記為

$$
X_n\asconv X
$$

</div>

幾乎確信收斂與機率收斂同屬隨機變數取值之間的收斂關係，但著眼點不同；機率收斂僅檢視各個有限 $n$ 下的偏離機率是否趨於 <span class="text-nowrap">$0$，</span>幾乎確信收斂則直接檢視樣本點層級上極限不收斂之例外集合的機率。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

兩者的關鍵差異在於極限號放置的位置。機率收斂將極限置於機率之外，僅要求單期偏離事件 $\lbrace\lvert X_n-X\rvert\geqslant\varepsilon\rbrace$ 的機率隨 $n\to\infty$ 趨於 <span class="text-nowrap">$0$；</span>即便對同一個樣本點 $\omega$ 而言，當 $n$ 無限增大時仍不斷反覆出現 $\lvert X_n(\omega)-X(\omega)\rvert\geqslant\varepsilon$ 的情形，只要各期偏離事件的機率趨於 <span class="text-nowrap">$0$，</span>依然滿足機率收斂 ([Example 5.14](#ex-indicator-block-sequence) 即屬此例)。

幾乎確信收斂則將極限置於機率之內，針對每一個樣本點 $\omega\in S$ 檢視實數數列 $X_n(\omega)$ 是否收斂至 <span class="text-nowrap">$X(\omega)$；</span>所有使 $\lim_{n\to\infty}X_n(\omega)=X(\omega)$ 不成立的樣本點所構成的「例外集合」，其發生機率必須嚴格等於 <span class="text-nowrap">$0$，</span>故條件明顯強於機率收斂。

</div>

幾乎確信收斂也被稱為**強收斂 <span lang="en">(converge strongly)</span>**、**以機率 $1$ 收斂 <span lang="en">(converge with probability $1$)</span>**、**幾乎處處收斂 <span lang="en">(converge almost everywhere)</span>**。此外，上述定義有一個等價的定義如下:

$$
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_k-X\rvert<\varepsilon,\ \forall\,k\geqslant n\bigr)=1,\ \forall\,\varepsilon>0
$$

## 幾乎確信收斂導致機率收斂

<div id="thm-asconv-implies-pconv" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 5.6 (幾乎確信收斂導致機率收斂)</div>

若 <span class="text-nowrap">$X_n\asconv X$，</span>則有

$$
X_n\pconv X
$$

反之未必成立。

</div>

<div class="topic-proof" markdown="1">
**Proof.**

取任意的 <span class="text-nowrap">$\varepsilon>0$，</span>並令

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
A_n=\lbrace\lvert X_k-X\rvert<\varepsilon,\ \forall\,k\geqslant n\rbrace=\bigcap_{k=n}^{\infty}\lbrace\lvert X_k-X\rvert<\varepsilon\rbrace
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
A_n&=\lbrace\lvert X_k-X\rvert<\varepsilon,\ \forall\,k\geqslant n\rbrace\\[0.45em]
&=\bigcap_{k=n}^{\infty}\lbrace\lvert X_k-X\rvert<\varepsilon\rbrace
\end{aligned}
$$

</div>

則由 [Definition 5.4](#def-converge-almost-surely) 之後所列的那一個等價敘述可知

$$
\lim_{n\to\infty}\mathbb{P}(A_n)=1
$$

另一方面，$A_n$ 要求 $k\geqslant n$ 的每一項都與 $X$ 相差不到 <span class="text-nowrap">$\varepsilon$，</span>其中 $k=n$ 這一項本身即為 $\lbrace\lvert X_n-X\rvert<\varepsilon\rbrace$ 這個事件，故

$$
A_n\subseteq\lbrace\lvert X_n-X\rvert<\varepsilon\rbrace
$$

由 [Theorem 1.7](/lecture-notes/probability-rules-from-axioms/#theorem-monotonicity) 的單調性可得

$$
\mathbb{P}(A_n)\leqslant\mathbb{P}\bigl(\lvert X_n-X\rvert<\varepsilon\bigr)\leqslant1
$$

令 <span class="text-nowrap">$n\to\infty$，</span>上式最左側趨於 <span class="text-nowrap">$1$、</span>最右側恆為 <span class="text-nowrap">$1$，</span>夾在中間的機率因而也必須趨於 <span class="text-nowrap">$1$，</span>寫成極限式即為

$$
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_n-X\rvert<\varepsilon\bigr)=1,\ \forall\,\varepsilon>0
$$

此即

$$
X_n\pconv X
$$

至於反向的敘述並不成立，[Example 5.14](#ex-indicator-block-sequence) 即給出一個機率收斂而不幾乎確信收斂的序列。原式得證。 <span class="topic-qed">$\square$</span>
</div>

本證明只用到 Definition 5.4 之後所列的等價敘述與機率的單調性；Chung (2001) 第 70 頁另有一套證明。

<div id="ex-indicator-block-sequence" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.14</div>

<div lang="en" markdown="1">
Let <span class="text-nowrap">$X\sim\mathcal{U}(0,1)$,</span> and define the sequence $X_1,X_2,\ldots$ as follows:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
X_1=X+\mathbb{I}_{[0,1]}(X),\qquad X_2=X+\mathbb{I}_{[0,\frac{1}{2}]}(X),\qquad X_3=X+\mathbb{I}_{[\frac{1}{2},1]}(X),\\[0.45em]
X_4=X+\mathbb{I}_{[0,\frac{1}{3}]}(X),\qquad X_5=X+\mathbb{I}_{[\frac{1}{3},\frac{2}{3}]}(X),\qquad X_6=X+\mathbb{I}_{[\frac{2}{3},1]}(X),\ \ldots
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
X_1=X+\mathbb{I}_{[0,1]}(X),\\[0.45em]
X_2=X+\mathbb{I}_{[0,\frac{1}{2}]}(X),\\[0.45em]
X_3=X+\mathbb{I}_{[\frac{1}{2},1]}(X),\\[0.45em]
X_4=X+\mathbb{I}_{[0,\frac{1}{3}]}(X),\\[0.45em]
X_5=X+\mathbb{I}_{[\frac{1}{3},\frac{2}{3}]}(X),\\[0.45em]
X_6=X+\mathbb{I}_{[\frac{2}{3},1]}(X),\ \ldots
\end{gathered}
$$

</div>

Show that $X_n$ converges to $X$ in probability but not almost surely.
</div>

題目之設定可統一改寫為

$$
X_n=X+\mathbb{I}_{[\frac{k-1}{m},\frac{k}{m}]}(X)
$$

其中 $m=1,2,3,\ldots,$ 而 <span class="text-nowrap">$k=1,2,\ldots,m$，</span>且

$$
n=\Bigl[\sum_{t=0}^{m-1}t\Bigr]+k
$$

則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}\bigl(\lvert X_n-X\rvert\geqslant\varepsilon\bigr)=\mathbb{P}\bigl(\mathbb{I}_{[\frac{k-1}{m},\frac{k}{m}]}(X)=1\bigr)=\mathbb{P}\Bigl(X\in\Bigl[\frac{k-1}{m},\frac{k}{m}\Bigr]\Bigr)=\frac{1}{\,m\,},\ m=1,2,3,\ldots
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}\bigl(\lvert X_n-X\rvert\geqslant\varepsilon\bigr)&=\mathbb{P}\bigl(\mathbb{I}_{[\frac{k-1}{m},\frac{k}{m}]}(X)=1\bigr)\\[0.45em]
&=\mathbb{P}\Bigl(X\in\Bigl[\frac{k-1}{m},\frac{k}{m}\Bigr]\Bigr)\\[0.45em]
&=\frac{1}{\,m\,},\ m=1,2,3,\ldots
\end{aligned}
$$

</div>

當 $n\to\infty$ 時，$m$ 也趨於無窮大，故知

$$
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_n-X\rvert\geqslant\varepsilon\bigr)=\lim_{m\to\infty}\frac{1}{\,m\,}=0
$$

此即

$$
X_n\pconv X
$$

又依題目之定義可知，$\lim_{n\to\infty}X_n$ 並不存在，舉例而言，當 $X=\frac{3}{\,8\,}$ 時 $X_n,\ n=1,2,\ldots$ 之值並不會是一個固定的值，可能是 $\frac{3}{\,8\,}$ 也有可能是 <span class="text-nowrap">$1+\frac{3}{\,8\,}$，</span>故極限不存在。

事實上，對於 $X\in[0,1]$ 而言，$\lim_{n\to\infty}X_n$ 都不存在，因此可知 $X_n$ 並沒有幾乎確信收斂至 <span class="text-nowrap">$X$。</span>

</div>

本題修改自 Casella and Berger (2002)，*Statistical Inference*，2nd ed.，頁 234。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

之所以在名稱中加上「幾乎」二字，是因為幾乎確信收斂僅要求收斂事件的機率為 <span class="text-nowrap">$1$，</span>仍容許一個機率為 $0$ 的非空例外集合存在。若進一步要求對樣本空間中的每一個樣本點皆無例外地收斂，亦即

$$
\lim_{n\to\infty}X_n(\omega)=X(\omega),\ \forall\,\omega\in S
$$

則稱為**確信收斂 <span lang="en">(converge surely)</span>**；此一定義完全不涉及機率測度，等價於實分析中的點態收斂 <span lang="en">(converge pointwisely)</span>。

</div>

## $r$ 次均方收斂與幾乎確信收斂互不蘊含

$r$ 次均方收斂與幾乎確信收斂都是很強的收斂型態，但是這兩個收斂型態之間卻沒有互相導致的關係，見下列這題。

<div id="ex-r-mean-and-almost-sure-are-independent" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.13 <span lang="en">(Continued)</span></div>

<div lang="en" markdown="1">
Let $X_1,X_2,\ldots$ be a sequence of independent discrete random variables such that $X_n$ has pmf

$$
f_n(0)=1-\frac{1}{\,n\,},\quad f_n(n)=\frac{1}{\,n\,},\quad n=1,2,3,\ldots
$$

<ol class="topic-list-paren topic-list-paren--start-4">
  <li>Show that $X_n$ does not converge to $0$ almost surely.</li>
  <li>If the pmf of $X_n$ is modified to $f_n(0)=1-\frac{1}{\,n^{2}\,}$, $f_n(n)=\frac{1}{\,n^{2}\,}$, <span class="text-nowrap">$n=1,2,3,\ldots$,</span> show that <span class="text-nowrap">$X_n\asconv0$</span> but $X_n$ does not converge to $0$ in $2$-nd mean.</li>
  <li>If the pmf of $X_n$ is modified to $f_n(0)=1-\frac{1}{\,n\,}$, $f_n(1)=\frac{1}{\,n\,}$, <span class="text-nowrap">$n=1,2,3,\ldots$,</span> show that $X_n\xrightarrow{~~2~~}0$ but $X_n$ does not converge to $0$ almost surely.</li>
</ol>
</div>

(4) 依題意可得
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}\bigl(\lvert X_k-0\rvert<\varepsilon,\ \forall\,k\geqslant n\bigr)=\mathbb{P}\bigl(X_k=0,\ \forall\,k\geqslant n\bigr)=\prod_{k=n}^{\infty}\mathbb{P}(X_k=0)=\prod_{k=n}^{\infty}\Bigl(1-\frac{1}{\,k\,}\Bigr)=0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}\bigl(\lvert X_k-0\rvert<\varepsilon,\ \forall\,k\geqslant n\bigr)&=\mathbb{P}\bigl(X_k=0,\ \forall\,k\geqslant n\bigr)\\[0.45em]
&=\prod_{k=n}^{\infty}\mathbb{P}(X_k=0)\\[0.45em]
&=\prod_{k=n}^{\infty}\Bigl(1-\frac{1}{\,k\,}\Bigr)=0
\end{aligned}
$$

</div>

故由幾乎確信收斂之等價定義可知
{: .topic-paren-cont}

$$
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_k-0\rvert<\varepsilon,\ \forall\,k\geqslant n\bigr)=0\neq1
$$

此即 $X_n$ 並沒有幾乎確信收斂至 <span class="text-nowrap">$0$。</span>
{: .topic-paren-cont}

(5) 依題意可得
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}\bigl(\lvert X_k-0\rvert<\varepsilon,\ \forall\,k\geqslant n\bigr)=\mathbb{P}\bigl(X_k=0,\ \forall\,k\geqslant n\bigr)=\prod_{k=n}^{\infty}\mathbb{P}(X_k=0)=\prod_{k=n}^{\infty}\Bigl(1-\frac{1}{\,k^{2}\,}\Bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}\bigl(\lvert X_k-0\rvert<\varepsilon,\ \forall\,k\geqslant n\bigr)&=\mathbb{P}\bigl(X_k=0,\ \forall\,k\geqslant n\bigr)\\[0.45em]
&=\prod_{k=n}^{\infty}\mathbb{P}(X_k=0)\\[0.45em]
&=\prod_{k=n}^{\infty}\Bigl(1-\frac{1}{\,k^{2}\,}\Bigr)
\end{aligned}
$$

</div>

其中
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\prod_{k=n}^{\infty}\Bigl(1-\frac{1}{\,k^{2}\,}\Bigr)=e^{\ln\prod_{k=n}^{\infty}\left(1-\frac{1}{k^{2}}\right)}=e^{\sum_{k=n}^{\infty}\ln\left(1-\frac{1}{k^{2}}\right)},\ \forall\,n\in\mathbb{N}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\prod_{k=n}^{\infty}\Bigl(1-\frac{1}{\,k^{2}\,}\Bigr)&=e^{\ln\prod_{k=n}^{\infty}\left(1-\frac{1}{k^{2}}\right)}\\[0.45em]
&=e^{\sum_{k=n}^{\infty}\ln\left(1-\frac{1}{k^{2}}\right)},\\[0.45em]
&\qquad\forall\,n\in\mathbb{N}
\end{aligned}
$$

</div>

又因
{: .topic-paren-cont}

$$
\int_{1}^{\infty}\Bigl\lvert\ln\Bigl(1-\frac{1}{\,x^{2}\,}\Bigr)\Bigr\rvert\,dx=\ln4<\infty
$$

故由積分審斂法可知 $\sum_{k=2}^{\infty}\bigl\lvert\ln\bigl(1-\frac{1}{k^{2}}\bigr)\bigr\rvert$ 收斂，此即
{: .topic-paren-cont}

$$
\lim_{n\to\infty}\sum_{k=n}^{\infty}\Bigl\lvert\ln\Bigl(1-\frac{1}{\,k^{2}\,}\Bigr)\Bigr\rvert=0
$$

故可知
{: .topic-paren-cont}

$$
\lim_{n\to\infty}\sum_{k=n}^{\infty}\ln\Bigl(1-\frac{1}{\,k^{2}\,}\Bigr)=0
$$

由此可得
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_k-0\rvert<\varepsilon,\ \forall\,k\geqslant n\bigr)=\lim_{n\to\infty}e^{\sum_{k=n}^{\infty}\ln\left(1-\frac{1}{k^{2}}\right)}=e^{\lim\limits_{n\to\infty}\sum_{k=n}^{\infty}\ln\left(1-\frac{1}{k^{2}}\right)}=e^{0}=1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_k-0\rvert<\varepsilon,\ \forall\,k\geqslant n\bigr)&=\lim_{n\to\infty}e^{\sum_{k=n}^{\infty}\ln\left(1-\frac{1}{k^{2}}\right)}\\[0.45em]
&=e^{\lim\limits_{n\to\infty}\sum_{k=n}^{\infty}\ln\left(1-\frac{1}{k^{2}}\right)}\\[0.45em]
&=e^{0}=1
\end{aligned}
$$

</div>

由幾乎確信收斂之等價定義可知
{: .topic-paren-cont}

$$
X_n\asconv0
$$

然而，由於
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\bigl[\lvert X_n-0\rvert^{2}\bigr]=\mathbb{E}\bigl[\lvert X_n\rvert^{2}\bigr]=\lvert0\rvert^{2}\times\Bigl(1-\frac{1}{\,n^{2}\,}\Bigr)+\lvert n\rvert^{2}\times\frac{1}{\,n^{2}\,}=1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[\lvert X_n-0\rvert^{2}\bigr]&=\mathbb{E}\bigl[\lvert X_n\rvert^{2}\bigr]\\[0.45em]
&=\lvert0\rvert^{2}\times\Bigl(1-\frac{1}{\,n^{2}\,}\Bigr)\\[0.45em]
&\qquad+\lvert n\rvert^{2}\times\frac{1}{\,n^{2}\,}\\[0.45em]
&=1
\end{aligned}
$$

</div>

故可知
{: .topic-paren-cont}

$$
\lim_{n\to\infty}\mathbb{E}\bigl[\lvert X_n-0\rvert^{2}\bigr]=1\neq0
$$

此即 $X_n$ 沒有 $2$ 次均方收斂至 <span class="text-nowrap">$0$。</span>
{: .topic-paren-cont}

(6) 依題意可得
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\bigl[\lvert X_n-0\rvert^{2}\bigr]=\mathbb{E}\bigl[\lvert X_n\rvert^{2}\bigr]=\lvert0\rvert^{2}\times\Bigl(1-\frac{1}{\,n\,}\Bigr)+\lvert1\rvert^{2}\times\frac{1}{\,n\,}=\frac{1}{\,n\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[\lvert X_n-0\rvert^{2}\bigr]&=\mathbb{E}\bigl[\lvert X_n\rvert^{2}\bigr]\\[0.45em]
&=\lvert0\rvert^{2}\times\Bigl(1-\frac{1}{\,n\,}\Bigr)\\[0.45em]
&\qquad+\lvert1\rvert^{2}\times\frac{1}{\,n\,}\\[0.45em]
&=\frac{1}{\,n\,}
\end{aligned}
$$

</div>

故可知
{: .topic-paren-cont}

$$
\lim_{n\to\infty}\mathbb{E}\bigl[\lvert X_n-0\rvert^{2}\bigr]=0
$$

此即
{: .topic-paren-cont}

$$
X_n\xrightarrow{~~2~~}0
$$

然而，若取 <span class="text-nowrap">$0<\varepsilon\leqslant1$，</span>則與 (4) 同理，由於此時 $\lvert X_k-0\rvert<\varepsilon$ 之事件等價於 <span class="text-nowrap">$X_k=0$，</span>故我們有
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}\bigl(\lvert X_k-0\rvert<\varepsilon,\ \forall\,k\geqslant n\bigr)=\mathbb{P}\bigl(X_k=0,\ \forall\,k\geqslant n\bigr)=\prod_{k=n}^{\infty}\mathbb{P}(X_k=0)=\prod_{k=n}^{\infty}\Bigl(1-\frac{1}{\,k\,}\Bigr)=0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}\bigl(\lvert X_k-0\rvert<\varepsilon,\ \forall\,k\geqslant n\bigr)&=\mathbb{P}\bigl(X_k=0,\ \forall\,k\geqslant n\bigr)\\[0.45em]
&=\prod_{k=n}^{\infty}\mathbb{P}(X_k=0)\\[0.45em]
&=\prod_{k=n}^{\infty}\Bigl(1-\frac{1}{\,k\,}\Bigr)=0
\end{aligned}
$$

</div>

故由幾乎確信收斂之等價定義可知
{: .topic-paren-cont}

$$
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_k-0\rvert<\varepsilon,\ \forall\,k\geqslant n\bigr)=0\neq1
$$

此即 $X_n$ 並沒有幾乎確信收斂至 <span class="text-nowrap">$0$。</span>
{: .topic-paren-cont}

</div>

由本題 (5)、(6) 兩小題可見，$r$ 次均方收斂與幾乎確信收斂之間並無強弱蘊含關係，何者成立取決於偏離值的成長幅度與尾機率可加性之間的消長。至此四種收斂型態及其關係已建立完畢，後續內容將介紹統計推論中最核心的兩條極限定理，分別是**[弱大數法則](/lecture-notes/weak-law-and-central-limit-theorem/#thm-weak-law-of-large-numbers) <span lang="en">(Weak Law of Large Numbers, WLLN)</span>** 與**[中央極限定理](/lecture-notes/weak-law-and-central-limit-theorem/#thm-central-limit-theorem) <span lang="en">(Central Limit Theorem, CLT)</span>**。

## 本篇小結

[Definition 5.3](#def-converge-in-r-mean) 的 $r$ 次均方收斂以 $\mathbb{E}\bigl[\lvert X_n-X\rvert^{r}\bigr]$ 是否趨於零來界定。由於距離的 $r$ 次方是非負的，要讓這個期望值趨於零，機率或機率密度就必須把那些距離不為零的地方「抵銷」掉；機率收斂只要求距離不小於 $\varepsilon$ 的那些地方機率趨於零，並不必負擔抵銷的工作，兩者的強弱之別正在於此。[Theorem 5.4](#thm-rconv-implies-pconv) 把這件事寫成定理，證明只用到馬可夫不等式給出的 $\mathbb{P}(\lvert X_n-X\rvert\geqslant\varepsilon)\leqslant\frac{\mathbb{E}[\lvert X_n-X\rvert^{r}]}{\varepsilon^{r}}$ 這條界限，再讓 $n\to\infty$ 即可。

[Example 5.13](#ex-pconv-without-first-mean) 說明反方向不成立，取值為 $0$ 與 $n$ 而機率分別為 $1-\frac{1}{\,n\,}$ 與 $\frac{1}{\,n\,}$ 的序列雖然機率收斂至零，但 $\mathbb{E}\bigl[\lvert X_n-0\rvert\bigr]$ 恆等於 <span class="text-nowrap">$1$，</span>不會趨於零。這一題是刻意設計的，因為取值隨 $n$ 成長的速度，恰好與機率隨 $n$ 遞減的速度一樣快，兩者相乘之後不隨 $n$ 改變。把機率改成 $\frac{1}{\,n^{m}\,}$ 之後，$m$ 次均方收斂仍然失敗，但一切 $0<r<m$ 的 $r$ 次均方收斂都成立。

[Theorem 5.5](#thm-2conv-implies-pconv) 把 $r=2$ 的情形單獨拿出來討論，只要期望值收斂至常數 $c$ 而變異數收斂至零，序列就二次均方收斂至 <span class="text-nowrap">$c$，</span>因而也機率收斂至 <span class="text-nowrap">$c$。</span>證明的作法是把 $\mathbb{E}\bigl[(X_n-c)^{2}\bigr]$ 展開，再以 [Theorem 2.11](/lecture-notes/variance/#thm-variance-formula) 的 $\mathrm{Var}(X)=\mathbb{E}(X^{2})-[\mathbb{E}(X)]^{2}$ 這條公式把二階原動差換掉，湊成 $\mathrm{Var}(X_n)+\bigl[\mathbb{E}(X_n)-c\bigr]^{2}$ 這個形式，兩項各自趨於零。二次均方收斂至母體參數的序列在數理統計中另有均方一致性這個名字，它比一般的一致性強。[Example 5.10 <span lang="en">(Continued)</span>](#ex-s-squared-mean-square-consistency) 即以這條判準重解一次 $S^{2}$ 的機率極限。在[常態分配](/lecture-notes/normal-distribution/#def-normal)的母體之下，由[伽瑪分配](/lecture-notes/gamma-distribution/#def-gamma-distribution)算出 $\mathbb{E}\bigl(S^{2}\bigr)=\sigma^{2}$ 與 $\mathrm{Var}\bigl(S^{2}\bigr)=\frac{2\sigma^{4}}{\,n-1\,}$ 這兩個量，後者在 $n\to\infty$ 時趨於零，故 <span class="text-nowrap">$S^{2}\pconv\sigma^{2}$。</span>其中 $S^{2}$ 的伽瑪分配來自 [Theorem 4.23](/lecture-notes/chi-squared-distribution/#thm-cochran-theorem) 的 $\frac{(n-1)S^{2}}{\sigma^{2}}\sim\chi^{2}(n-1)$ 這一抽樣分配結果。

[Definition 5.4](#def-converge-almost-surely) 的幾乎確信收斂換一個角度，它不看機率本身怎麼變化，而是看那些使 $\lim_{n\to\infty}X_n(\omega)$ 與 $X(\omega)$ 不相等的樣本點 $\omega$ 收集而成的「例外集合」，要求這個集合的發生機率是零。[Theorem 5.6](#thm-asconv-implies-pconv) 指出它同樣導致機率收斂。[Example 5.14](#ex-indicator-block-sequence) 給出反方向的反例，以[均勻分配](/lecture-notes/uniform-distribution-integral-transform/#def-uniform-distribution)的 $X$ 加上一段一段往右移動的指標函數，每一段的長度為 <span class="text-nowrap">$\frac{1}{\,m\,}$，</span>因此 $\mathbb{P}(\lvert X_n-X\rvert\geqslant\varepsilon)=\frac{1}{\,m\,}$ 會趨於零，機率收斂成立；但每一個 $X\in[0,1]$ 都會被無窮多段掃到，$\lim_{n\to\infty}X_n$ 根本不存在，幾乎確信收斂因而不成立。

最後，[Example 5.13 <span lang="en">(Continued)</span>](#ex-r-mean-and-almost-sure-are-independent) 把 $r$ 次均方收斂與幾乎確信收斂擺在一起比較。同一個序列既不幾乎確信收斂至零，也不一次均方收斂至零；把機率改為 $\frac{1}{\,n^{2}\,}$ 之後，$\prod_{k=n}^{\infty}\bigl(1-\frac{1}{k^{2}}\bigr)$ 的極限為 <span class="text-nowrap">$1$，</span>幾乎確信收斂成立，二次均方收斂卻失敗；把取值由 $n$ 改為 $1$ 之後，二次均方收斂成立，幾乎確信收斂又失敗。可見這兩個收斂型態之間並沒有互相導致的關係。

至此，四種收斂型態與它們之間的關係都已經給齊。[下一篇](/lecture-notes/weak-law-and-central-limit-theorem/)轉入兩條直接用得上的極限定理，分別是弱大數法則與中央極限定理，前者說的是樣本平均數機率收斂至母體期望值，後者說的是標準化之後的樣本平均數分配收斂至標準常態分配。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Kai Lai Chung. 2001. *A Course in Probability Theory*. 3rd ed. Academic Press.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
