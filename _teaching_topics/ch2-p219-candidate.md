---
title: "馬可夫、柴比雪夫與坎特利不等式"
subtitle: "Markov’s, Chebyshev’s, and Cantelli’s Inequalities"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 19
order: 219
permalink: /teaching-topics/ch2-p219-candidate/
date: 2026-08-06
published: false
excerpt: "在不知道機率分配形式、只掌握低階動差的情況下，機率仍然可以被界定: 若 $h(\\cdot)$ 為非負可測實值函數且 $\\mathbb{E}[h(X)]$ 有限，則 $\\mathbb{P}(h(X)\\geqslant a)\\leqslant\\mathbb{E}[h(X)]/a$。在這條定理中取 $h(x)=x_{+}$ 得到馬可夫不等式，取 $h(x)=x^{2}$ 並施於 $\\lvert X-\\mu_{X}\\rvert$ 得到柴比雪夫不等式 $\\mathbb{P}(\\lvert X-\\mu_{X}\\rvert\\geqslant a)\\leqslant\\sigma_{X}^{2}/a^{2}$，取 $h(y)=(y+c)^{2}$ 再對 $c$ 取下確界則得到單邊柴比雪夫不等式，亦即坎特利不等式。三者用到的動差都不超過一階與二階。"
---

[上一篇](/teaching-topics/ch2-p218-candidate/)介紹特徵函數，它與[動差母函數](/teaching-topics/ch2-p215-candidate/#def-mgf)同樣以一個函數表示整個機率分配。從[動差](/teaching-topics/ch2-p213-candidate/#def-population-moment)系統到各種母函數，我們一路上處理的都是分配本身的描述；然而實務上經常遇到另一種處境: 分配的形式並不清楚，手上只有[期望值](/teaching-topics/ch2-p06-candidate/#def-expectation)，或再加上一個[變異數](/teaching-topics/ch2-p208-candidate/#def-variance)。

機率不等式及相關法則這一節處理的正是這種處境: 在僅知道低階動差的條件下，為機率給出一個可用的範圍。本篇先給出一條以非負函數界定機率的定理，再由它挑選不同的 $h(\cdot)$，依序導出馬可夫不等式、柴比雪夫不等式與單邊柴比雪夫不等式 (亦即坎特利不等式)，並以兩張圖說明前兩者的直觀意義。三個不等式所用到的動差訊息，都不超過一階與二階。

## 機率不等式

<div id="thm-nonnegative-function-bound" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.31 (非負函數的機率界限, a bound for nonnegative functions)</div>

令 $h(\cdot)$ 為一非負可測實值函數，$X$ 為一隨機變數，$a>0$ 為一常數且 $\mathbb{E}\bigl[h(X)\bigr]<\infty$，則

$$
\mathbb{P}\bigl(h(X)\geqslant a\bigr)\leqslant\frac{\,\mathbb{E}\bigl[h(X)\bigr]\,}{a}
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.** 我們在此僅以連續型為例證明，並令 $A=\lbrace\,x\mid h(x)\geqslant a\,\rbrace$，則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[h(X)\bigr]&=\int_{-\infty}^{\infty}h(x)\,f_{\sssig X}(x)\,dx\\[0.45em]
&=\int_{A}h(x)\,f_{\sssig X}(x)\,dx+\int_{A^{\prime}}h(x)\,f_{\sssig X}(x)\,dx\\[0.45em]
&\geqslant\int_{A}h(x)\,f_{\sssig X}(x)\,dx\geqslant\int_{A}a\,f_{\sssig X}(x)\,dx\\[0.45em]
&=a\int_{A}f_{\sssig X}(x)\,dx=a\,\mathbb{P}(X\in A)=a\,\mathbb{P}\bigl(h(X)\geqslant a\bigr)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}\bigl[h(X)\bigr]=\int_{-\infty}^{\infty}h(x)\,f_{\sssig X}(x)\,dx\\[0.45em]
&\quad =\int_{A}h(x)\,f_{\sssig X}(x)\,dx\\[0.2em]
&\qquad +\int_{A^{\prime}}h(x)\,f_{\sssig X}(x)\,dx\\[0.45em]
&\quad \geqslant\int_{A}h(x)\,f_{\sssig X}(x)\,dx\\[0.45em]
&\quad \geqslant\int_{A}a\,f_{\sssig X}(x)\,dx=a\int_{A}f_{\sssig X}(x)\,dx\\[0.45em]
&\quad =a\,\mathbb{P}(X\in A)=a\,\mathbb{P}\bigl(h(X)\geqslant a\bigr)
\end{aligned}
$$

</div>

故可得

$$
\mathbb{P}\bigl(h(X)\geqslant a\bigr)\leqslant\frac{\,\mathbb{E}\bigl[h(X)\bigr]\,}{a}
$$

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

前述證明中，特別之處在於 $h(\cdot)$ 是非負的，故 $\mathbb{E}[h(X)]$ 的定義中，任意分段積分都是非負的，因此我們捨棄掉在 $A^{\prime}$ 上的積分，讓不等號出現；又因為 $X\in A\Longleftrightarrow h(X)\geqslant a$，故我們有 $\mathbb{P}(X\in A)=\mathbb{P}(h(X)\geqslant a)$。

事實上，[Theorem 2.31](#thm-nonnegative-function-bound) 能衍生出許多有用的不等式，如下敘述。

</div>

<div id="thm-markov" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.32 (馬可夫不等式, Markov’s inequality)</div>

若 $X$ 為一非負隨機變數，$a>0$ 為一常數且 $\mathbb{E}(\lvert X\rvert)<\infty$，則

$$
\mathbb{P}(X\geqslant a)\leqslant\frac{\,\mathbb{E}(X)\,}{a}
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.** 在 [Theorem 2.31](#thm-nonnegative-function-bound) 中，可設定 $h(x)=x_{+}=\max\lbrace x,0\rbrace$，此函數連續且非負，因而符合該定理對 $h(\cdot)$ 的要求；又 $X$ 為非負隨機變數，故 $h(X)=X$，可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}\bigl(h(X)\geqslant a\bigr)=\mathbb{P}(X\geqslant a)\leqslant\frac{\,\mathbb{E}\bigl[h(X)\bigr]\,}{a}=\frac{\,\mathbb{E}(X)\,}{a}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}\bigl(h(X)\geqslant a\bigr)=\mathbb{P}(X\geqslant a)\\[0.45em]
&\quad \leqslant\frac{\,\mathbb{E}\bigl[h(X)\bigr]\,}{a}=\frac{\,\mathbb{E}(X)\,}{a}
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

馬可夫不等式 <span lang="en">(Markov’s inequality)</span> 有一些地方需要注意:

(1) 除了要求 $X$ 是非負的之外，馬可夫不等式僅要求其期望值存在，故在**僅知道期望值 (一階動差) 而完全不知道其機率分配形式，但必須求取機率範圍**的時候，特別好用。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

儘管如此，實用上來說，這個不等式在 $a\leqslant\mathbb{E}(X)$ 的時候並無法給你任何資訊，因為此時不等式右側的 $\frac{\mathbb{E}(X)}{a}$ 不小於 $1$。

</div>

<div id="note-markov-extended" class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

若在 [Theorem 2.31](#thm-nonnegative-function-bound) 中令 $h(x)=(x_{+})^{r}=\bigl[\max\lbrace x,0\rbrace\bigr]^{r}$，其中 $r>0$，且已知 $\mathbb{E}(\lvert X\rvert^{r})<\infty$，則馬可夫不等式可以進一步擴展為

$$
\mathbb{P}(X\geqslant a)\leqslant\frac{\,\mathbb{E}(X^{r})\,}{a^{r}}
$$

此處的 $h(x)=(x_{+})^{r}$ 在整條實數線上連續且非負，因而符合該定理對 $h(\cdot)$ 的要求；又 $X$ 為非負隨機變數，故 $h(X)=X^{r}$。我們證明如下:

<div class="topic-proof" markdown="1">
**Proof.** 在 [Theorem 2.31](#thm-nonnegative-function-bound) 中把門檻常數取為 $a^{r}$，則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}\bigl(h(X)\geqslant a^{r}\bigr)&=\mathbb{P}(X^{r}\geqslant a^{r})=\mathbb{P}(X\geqslant a)\\[0.45em]
&\leqslant\frac{\,\mathbb{E}\bigl[h(X)\bigr]\,}{a^{r}}=\frac{\,\mathbb{E}(X^{r})\,}{a^{r}}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}\bigl(h(X)\geqslant a^{r}\bigr)=\mathbb{P}(X^{r}\geqslant a^{r})\\[0.45em]
&\quad =\mathbb{P}(X\geqslant a)\leqslant\frac{\,\mathbb{E}\bigl[h(X)\bigr]\,}{a^{r}}\\[0.45em]
&\quad =\frac{\,\mathbb{E}(X^{r})\,}{a^{r}}
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

在上述版本的證明中，要刻意將 [Theorem 2.31](#thm-nonnegative-function-bound) 中的 $a$ 設定為 $a^{r}$，如此才能透過 $h(x)=(x_{+})^{r}$ 得到

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}\bigl(h(X)\geqslant a^{r}\bigr)=\mathbb{P}(X^{r}\geqslant a^{r})\leqslant\frac{\,\mathbb{E}(X^{r})\,}{a^{r}}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}\bigl(h(X)\geqslant a^{r}\bigr)=\mathbb{P}(X^{r}\geqslant a^{r})\\[0.45em]
&\quad \leqslant\frac{\,\mathbb{E}(X^{r})\,}{a^{r}}
\end{aligned}
$$

</div>

再利用

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lbrace\,x\mid x^{r}\geqslant a^{r},\ x\geqslant0\,\rbrace=\lbrace\,x\mid x\geqslant a,\ x\geqslant0\,\rbrace
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\lbrace\,x\mid x^{r}\geqslant a^{r},\ x\geqslant0\,\rbrace\\[0.45em]
&\quad =\lbrace\,x\mid x\geqslant a,\ x\geqslant0\,\rbrace
\end{aligned}
$$

</div>

可知 $\mathbb{P}(X^{r}\geqslant a^{r})=\mathbb{P}(X\geqslant a)$，得證。

這個版本的馬可夫不等式，可以在稍後要提到的[**柴比雪夫不等式 <span lang="en">(Chebyshev’s inequality)</span>**](#thm-chebyshev) 之證明中，發揮很大的功用。

</div>

(2) 馬可夫不等式將隨機變數的機率，與其期望值產生了連結，其核心想法是**期望值是分配的聚集中心，正常狀況下，大多數 $X$ 應在其附近**，我們便由此衡量「一個非負隨機變數，大於等於某個值」的**機率上界**。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個直觀意義，在其變化版本中，更能夠看出來。若 $k>0$ 且 <span class="text-nowrap">$\mathbb{E}(X)>0$，</span>該版本為

$$
\mathbb{P}\bigl(X\geqslant k\,\mathbb{E}(X)\bigr)\leqslant\frac{\mathbb{E}(X)}{\,k\,\mathbb{E}(X)\,}=\frac{1}{\,k\,}
$$

也就是衡量「$X$ 不小於 $k$ 倍期望值」的機率，而且此不等式指出，這樣的機率應「不超過 $\frac{1}{k}$」。在原本的不等式中，只要將 $a$ 這個常數替換為 $k$ 倍的期望值 (即 $k\,\mathbb{E}(X)$) 即可得到這個版本。讀者不應忘記 $\mathbb{E}(X)$ 只是一個常數。

一個實際上應用的例子如: 所得不小於世界人均所得十倍的人，並不超過世界人口的十分之一。

</div>

若我們用圖示來理解馬可夫不等式，則可以把上述提到的直觀意義化約成下面這張圖:

<figure id="fig-markov-intuition" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/markov-inequality-tail-bound.svg" alt="一條右偏的機率密度曲線畫在一條橫軸之上，曲線旁標為 f_X(x)。曲線上有兩個點各以一條虛線垂直落到橫軸，左邊那條的軸下標為 E(X)，右邊那條的軸下標為 k E(X)。右邊虛線以右、曲線以下的右尾區域填上陰影，一條彎曲的虛線箭頭由該陰影區域指向右上方的標示，標示內容為小於等於 1 除以 k。橫軸末端標為 x，原點標為 0。">
  <figcaption><span class="topic-figure__label">Fig. 2.19.</span> 馬可夫不等式的圖示。曲線為伽瑪分配 <span class="text-nowrap">$\mathrm{Gamma}(4,1.7)$</span> 的機率密度，期望值 <span class="text-nowrap">$\mathbb{E}(X)\fallingdotseq2.353$；</span>取 <span class="text-nowrap">$k=1.7$，</span>右側界線落在 <span class="text-nowrap">$k\,\mathbb{E}(X)=4$。</span>加上陰影的右尾是事件 <span class="text-nowrap">$X\geqslant k\,\mathbb{E}(X)$，</span>其機率不超過 <span class="text-nowrap">$\frac{1}{k}\fallingdotseq0.5882$。</span></figcaption>
</figure>

<div id="thm-chebyshev" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.33 (柴比雪夫不等式, Chebyshev’s inequality)</div>

若 $X$ 為一隨機變數，$a>0$ 為一常數且 $\mathbb{E}(X)=\mu_{\sssig X}$ 與 $\mathrm{Var}(X)=\sigma_{\sssig X}^{2}$ 皆為有限，則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert\geqslant a\bigr)\leqslant\frac{\,\sigma_{\sssig X}^{2}\,}{a^{2}}\quad\text{且}\quad\mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert<a\bigr)\geqslant1-\frac{\,\sigma_{\sssig X}^{2}\,}{a^{2}}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert\geqslant a\bigr)\leqslant\frac{\,\sigma_{\sssig X}^{2}\,}{a^{2}}\\[0.45em]
\text{且}\quad\mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert<a\bigr)\geqslant1-\frac{\,\sigma_{\sssig X}^{2}\,}{a^{2}}
\end{gathered}
$$

</div>

</div>

<div class="topic-proof" markdown="1">
**Proof.** 我們在此以[馬可夫不等式之擴展版本](#note-markov-extended)證明之，令 $h(x)=x^{2}$，則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert\geqslant a\bigr)&=\mathbb{P}\bigl(h(\lvert X-\mu_{\sssig X}\rvert)\geqslant h(a)\bigr)\\[0.45em]
&=\mathbb{P}\bigl((X-\mu_{\sssig X})^{2}\geqslant a^{2}\bigr)\\[0.45em]
&\leqslant\frac{\,\mathbb{E}\bigl[(X-\mu_{\sssig X})^{2}\bigr]\,}{a^{2}}=\frac{\,\sigma_{\sssig X}^{2}\,}{a^{2}}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert\geqslant a\bigr)\\[0.45em]
&\quad =\mathbb{P}\bigl(h(\lvert X-\mu_{\sssig X}\rvert)\geqslant h(a)\bigr)\\[0.45em]
&\quad =\mathbb{P}\bigl((X-\mu_{\sssig X})^{2}\geqslant a^{2}\bigr)\\[0.45em]
&\quad \leqslant\frac{\,\mathbb{E}\bigl[(X-\mu_{\sssig X})^{2}\bigr]\,}{a^{2}}=\frac{\,\sigma_{\sssig X}^{2}\,}{a^{2}}
\end{aligned}
$$

</div>

又餘事件的機率為 $1$ 減去該事件的機率，故可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert<a\bigr)&=1-\mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert\geqslant a\bigr)\\[0.45em]
&\geqslant1-\frac{\,\sigma_{\sssig X}^{2}\,}{a^{2}}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert<a\bigr)\\[0.45em]
&\quad =1-\mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert\geqslant a\bigr)\\[0.45em]
&\quad \geqslant1-\frac{\,\sigma_{\sssig X}^{2}\,}{a^{2}}
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

柴比雪夫不等式有一些地方需要注意:

(1) 與[馬可夫不等式](#thm-markov)相比，$X$ 不限定於非負的隨機變數，但多要求了變異數必須存在。在**僅知道期望值與變異數 (一二階動差) 而完全不知道其機率分配形式，但必須求取機率範圍**的時候，是很好用的手段。
{: .topic-paren-item}

(2) 柴比雪夫不等式的概念，類似於馬可夫不等式，只是柴比雪夫不等式是衡量「一個隨機變數，與離其期望值的距離不小於某個值」的**機率上界**或「一個隨機變數，與離其期望值的距離小於某個值」的**機率下界**。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這兩個敘述，事實上是相同的，也對應到柴比雪夫不等式的兩個式子。讀者應該可以透過解析其事件範圍，得到二者敘述等價的結論。特別注意的地方是，在連續分配中，是否包含分界點並不重要，但離散分配中卻要特別講究。

</div>

<div id="note-meaning-of-chebyshev" class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

柴比雪夫不等式將隨機變數的機率，與期望值和變異數同時產生了連結，其核心與馬可夫不等式完全相同，都在於**期望值是分配的聚集中心，正常狀況下大多數 $X$ 應在其附近**，只是柴比雪夫不等式使用變異數 (或[標準差](/teaching-topics/ch2-p209-candidate/#def-standard-deviation))，來衡量隨機變數與期望值的距離，並且透過這樣的距離及對應的機率範圍，來衡量「所謂的近是多近、所謂的遠是多遠」。

用標準差來衡量某個點與一個變數之間的距離，被稱作**統計距離**或是**馬氏距離 <span lang="en">(Mahalanobis distance)</span>**，其概念的直觀，在於將單位所造成的尺度差異消除掉，用以衡量「統計上的遠近」。

</div>

(3) 與馬可夫不等式相同，柴比雪夫不等式亦有另一個版本。若 $k>0$ 且 $\sigma_{\sssig X}>0$，則
{: #chebyshev-standard-deviation-form .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert\geqslant k\,\sigma_{\sssig X}\bigr)\leqslant\frac{1}{\,k^{2}\,}\quad\text{且}\quad\mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert<k\,\sigma_{\sssig X}\bigr)\geqslant1-\frac{1}{\,k^{2}\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert\geqslant k\,\sigma_{\sssig X}\bigr)\leqslant\frac{1}{\,k^{2}\,}\\[0.45em]
\text{且}\quad\mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert<k\,\sigma_{\sssig X}\bigr)\geqslant1-\frac{1}{\,k^{2}\,}
\end{gathered}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個版本的作法，與馬可夫不等式的變化版本完全相同，是將原式中的 $a$ 替換為 $k$ 倍的標準差 (即 $k\,\sigma_{\sssig X}$) 而得。

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

從這裡重新詮釋 [Note](#note-meaning-of-chebyshev) 的意義，可以得知，其給的直觀是**與期望值相距不小於 $k$ 個標準差的範圍內，至多有 $\frac{1}{k^{2}}$ 的機率**或是**與期望值相距不到 $k$ 個標準差的範圍內，至少有 $1-\frac{1}{k^{2}}$ 的機率**。

這個直觀意義相當重要，因為實務上，很多時候我們僅有一些經過彙整的資料 <span lang="en">(summarized data)</span>，例如僅有期望值或標準差，但卻需要給一個關於這組資料的機率時，便會需要使用此不等式。

</div>

(4) 此不等式**無法再被改進**。這句話意思是，在**僅知道期望值與變異數**的狀況下，柴比雪夫不等式所給的機率範圍，在給定的隨機變數範圍中，是最精確的，我們無法在僅知道一二階動差的狀況下，對同一個區間給出更精確的機率範圍。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

稍後的小節我們會談到[**鐘形分配經驗法則 <span lang="en">(empirical rule of bell-shaped distribution)</span>**](/teaching-topics/ch2-p222-candidate/#thm-empirical-rule)，這個經驗法則同樣也談到概略的機率值，但相較於此卻精確得多，甚至是給出一個大約的數字而非一個區間。這個原因是**鐘形分配 <span lang="en">(bell-shaped distribution)</span>** 本身所給的資訊含量，比起只知道一二階動差的隨機變數要來得多很多。

事實上，如果我們知道關於分配的更多訊息，柴比雪夫不等式與馬可夫不等式都能夠被改進，詳見[後面的例題](/teaching-topics/ch2-p220-candidate/)。

</div>

(5) 事實上柴比雪夫不等式未必要透過馬可夫不等式來證明，亦可直接經由變異數的定義直接證明。我們便順勢將上述[第 (3) 點](#chebyshev-standard-deviation-form)中所提到的另一個版本，直接證明如下:
{: .topic-paren-item}

<div class="topic-proof" markdown="1">
**Proof.** 由變異數的定義展開，並將積分區間依 $\mu_{\sssig X}\pm k\,\sigma_{\sssig X}$ 拆成三段，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\sigma_{\sssig X}^{2}&=\mathbb{E}\bigl[(X-\mu_{\sssig X})^{2}\bigr]=\int_{-\infty}^{\infty}(x-\mu_{\sssig X})^{2}f_{\sssig X}(x)\,dx\\[0.45em]
&=\int_{-\infty}^{\mu_{\sssig X}-k\,\sigma_{\sssig X}}(x-\mu_{\sssig X})^{2}f_{\sssig X}(x)\,dx+\int_{\mu_{\sssig X}-k\,\sigma_{\sssig X}}^{\mu_{\sssig X}+k\,\sigma_{\sssig X}}(x-\mu_{\sssig X})^{2}f_{\sssig X}(x)\,dx\\[0.2em]
&\quad +\int_{\mu_{\sssig X}+k\,\sigma_{\sssig X}}^{\infty}(x-\mu_{\sssig X})^{2}f_{\sssig X}(x)\,dx\\[0.45em]
&\geqslant\int_{-\infty}^{\mu_{\sssig X}-k\,\sigma_{\sssig X}}(x-\mu_{\sssig X})^{2}f_{\sssig X}(x)\,dx+\int_{\mu_{\sssig X}+k\,\sigma_{\sssig X}}^{\infty}(x-\mu_{\sssig X})^{2}f_{\sssig X}(x)\,dx\\[0.45em]
&\geqslant\int_{-\infty}^{\mu_{\sssig X}-k\,\sigma_{\sssig X}}k^{2}\sigma_{\sssig X}^{2}\,f_{\sssig X}(x)\,dx+\int_{\mu_{\sssig X}+k\,\sigma_{\sssig X}}^{\infty}k^{2}\sigma_{\sssig X}^{2}\,f_{\sssig X}(x)\,dx
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\sigma_{\sssig X}^{2}=\mathbb{E}\bigl[(X-\mu_{\sssig X})^{2}\bigr]\\[0.45em]
&\quad =\int_{-\infty}^{\infty}(x-\mu_{\sssig X})^{2}f_{\sssig X}(x)\,dx\\[0.45em]
&\quad =\int_{-\infty}^{\mu_{\sssig X}-k\,\sigma_{\sssig X}}(x-\mu_{\sssig X})^{2}f_{\sssig X}(x)\,dx\\[0.2em]
&\qquad +\int_{\mu_{\sssig X}-k\,\sigma_{\sssig X}}^{\mu_{\sssig X}+k\,\sigma_{\sssig X}}(x-\mu_{\sssig X})^{2}f_{\sssig X}(x)\,dx\\[0.2em]
&\qquad +\int_{\mu_{\sssig X}+k\,\sigma_{\sssig X}}^{\infty}(x-\mu_{\sssig X})^{2}f_{\sssig X}(x)\,dx\\[0.45em]
&\quad \geqslant\int_{-\infty}^{\mu_{\sssig X}-k\,\sigma_{\sssig X}}(x-\mu_{\sssig X})^{2}f_{\sssig X}(x)\,dx\\[0.2em]
&\qquad +\int_{\mu_{\sssig X}+k\,\sigma_{\sssig X}}^{\infty}(x-\mu_{\sssig X})^{2}f_{\sssig X}(x)\,dx\\[0.45em]
&\quad \geqslant\int_{-\infty}^{\mu_{\sssig X}-k\,\sigma_{\sssig X}}k^{2}\sigma_{\sssig X}^{2}\,f_{\sssig X}(x)\,dx\\[0.2em]
&\qquad +\int_{\mu_{\sssig X}+k\,\sigma_{\sssig X}}^{\infty}k^{2}\sigma_{\sssig X}^{2}\,f_{\sssig X}(x)\,dx
\end{aligned}
$$

</div>

其中第二個不等號是因為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
k^{2}\sigma_{\sssig X}^{2}=\bigl[(\mu_{\sssig X}+k\,\sigma_{\sssig X})-\mu_{\sssig X}\bigr]^{2}=\bigl[(\mu_{\sssig X}-k\,\sigma_{\sssig X})-\mu_{\sssig X}\bigr]^{2}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
k^{2}\sigma_{\sssig X}^{2}&=\bigl[(\mu_{\sssig X}+k\,\sigma_{\sssig X})-\mu_{\sssig X}\bigr]^{2}\\[0.45em]
&=\bigl[(\mu_{\sssig X}-k\,\sigma_{\sssig X})-\mu_{\sssig X}\bigr]^{2}
\end{aligned}
$$

</div>

而兩段積分區域上的 $(x-\mu_{\sssig X})^{2}$ 皆不小於 $k^{2}\sigma_{\sssig X}^{2}$。故可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\sigma_{\sssig X}^{2}&\geqslant k^{2}\sigma_{\sssig X}^{2}\left(\int_{-\infty}^{\mu_{\sssig X}-k\,\sigma_{\sssig X}}f_{\sssig X}(x)\,dx+\int_{\mu_{\sssig X}+k\,\sigma_{\sssig X}}^{\infty}f_{\sssig X}(x)\,dx\right)\\[0.45em]
&=k^{2}\sigma_{\sssig X}^{2}\times\mathbb{P}\bigl(X\leqslant\mu_{\sssig X}-k\,\sigma_{\sssig X}\ \text{或}\ X\geqslant\mu_{\sssig X}+k\,\sigma_{\sssig X}\bigr)\\[0.45em]
&=k^{2}\sigma_{\sssig X}^{2}\times\mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert\geqslant k\,\sigma_{\sssig X}\bigr)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\sigma_{\sssig X}^{2}\geqslant k^{2}\sigma_{\sssig X}^{2}\Biggl(\int_{-\infty}^{\mu_{\sssig X}-k\,\sigma_{\sssig X}}f_{\sssig X}(x)\,dx\\[0.2em]
&\qquad +\int_{\mu_{\sssig X}+k\,\sigma_{\sssig X}}^{\infty}f_{\sssig X}(x)\,dx\Biggr)\\[0.45em]
&\quad =k^{2}\sigma_{\sssig X}^{2}\\[0.2em]
&\qquad \times\mathbb{P}\bigl(X\leqslant\mu_{\sssig X}-k\,\sigma_{\sssig X}\\[0.2em]
&\qquad\quad \ \text{或}\ X\geqslant\mu_{\sssig X}+k\,\sigma_{\sssig X}\bigr)\\[0.45em]
&\quad =k^{2}\sigma_{\sssig X}^{2}\times\mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert\geqslant k\,\sigma_{\sssig X}\bigr)
\end{aligned}
$$

</div>

由 $k>0$ 與 $\sigma_{\sssig X}>0$ 可知 $k^{2}\sigma_{\sssig X}^{2}>0$，兩側同除以 $k^{2}\sigma_{\sssig X}^{2}$，即為

$$
\mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert\geqslant k\,\sigma_{\sssig X}\bigr)\leqslant\frac{\sigma_{\sssig X}^{2}}{\,k^{2}\sigma_{\sssig X}^{2}\,}=\frac{1}{\,k^{2}\,}
$$

原式得證。 <span class="topic-qed">$\square$</span>
</div>

我們同樣透過圖示，來理解柴比雪夫不等式背後的直觀意義，如下圖:

<figure id="fig-chebyshev-intuition" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/chebyshev-inequality-central-interval.svg" alt="一條雙峰的機率密度曲線畫在一條橫軸之上，曲線旁標為 f_X(x)。曲線上有三個點各以一條虛線垂直落到橫軸，三條虛線的軸下標由左至右分別為 μ_X 減 k σ_X、μ_X、μ_X 加 k σ_X。左右兩條虛線之間、曲線以下的中央區域填上陰影，區域內標有 P(·) 表示該區域所對應的機率，一條彎曲的虛線箭頭由該陰影區域指向右上方的標示，標示內容為大於等於 1 減去 1 除以 k 平方。橫軸末端標為 x。">
  <figcaption><span class="topic-figure__label">Fig. 2.20.</span> 柴比雪夫不等式的圖示。曲線為兩個常態密度的混合 <span class="text-nowrap">$0.6\,f_{1}(x)+0.4\,f_{2}(x)$，</span>其中 $f_{1}$ 為 <span class="text-nowrap">$\mathcal{N}(2,0.6^{2})$</span> 的密度、$f_{2}$ 為 <span class="text-nowrap">$\mathcal{N}(4,0.45^{2})$</span> 的密度，期望值 <span class="text-nowrap">$\mu_{\sssig X}=2.8$、</span>標準差 <span class="text-nowrap">$\sigma_{\sssig X}\fallingdotseq1.121$；</span>取 <span class="text-nowrap">$k=1.3$，</span>陰影部分為事件 <span class="text-nowrap">$\lvert X-\mu_{\sssig X}\rvert<k\,\sigma_{\sssig X}$，</span>其機率至少為 <span class="text-nowrap">$1-\frac{1}{k^{2}}\fallingdotseq0.4083$。</span></figcaption>
</figure>

上圖明白地呈現了「與期望值相距不到 $k$ 個標準差的範圍 (陰影部分)，至少有 $1-\frac{1}{k^{2}}$ 的機率」；而與其等價的另一段敘述「與期望值相距不小於 $k$ 個標準差的範圍 (未加陰影的部分)，至多有 $\frac{1}{k^{2}}$ 的機率」，亦能夠在圖上看出來。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

若讀者較不習慣使用統計距離來理解柴比雪夫不等式，亦可將上圖的 $k\,\sigma_{\sssig X}$ 改寫為 <span class="text-nowrap">$a$，</span>則其表示式便會對應到 [Theorem 2.33](#thm-chebyshev) 中的原始版本。此外，雖然這個版本的柴比雪夫不等式對 $k$ 只要求 $k>0$，但在實務上，$k\leqslant1$ 時 $\frac{1}{k^{2}}$ 不小於 $1$，是無法提供任何資訊的，因為一個機率本來就要介在 $0$ 到 $1$ 之間。

</div>

儘管上圖是以連續型分配作為圖例，但讀者仍不應忘記，柴比雪夫不等式對**任意具有期望值與變異數**的分配，皆可以使用，其中當然也包含離散型分配，因此在分界點上，等號的方向歸屬應當特別釐清。

<div id="thm-one-tailed-chebyshev" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.34 (單邊柴比雪夫不等式, one-tailed Chebyshev’s inequality)</div>

若 $X$ 為一隨機變數，$a>0$ 為一常數且 $\mathbb{E}(X)=\mu_{\sssig X}$ 與 $\mathrm{Var}(X)=\sigma_{\sssig X}^{2}$ 皆為有限，則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}\bigl(X-\mu_{\sssig X}\geqslant a\bigr)\leqslant\frac{\,\sigma_{\sssig X}^{2}\,}{\,\sigma_{\sssig X}^{2}+a^{2}\,}\quad\text{且}\quad\mathbb{P}\bigl(X-\mu_{\sssig X}\leqslant-a\bigr)\leqslant\frac{\,\sigma_{\sssig X}^{2}\,}{\,\sigma_{\sssig X}^{2}+a^{2}\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{P}\bigl(X-\mu_{\sssig X}\geqslant a\bigr)\leqslant\frac{\,\sigma_{\sssig X}^{2}\,}{\,\sigma_{\sssig X}^{2}+a^{2}\,}\\[0.45em]
\text{且}\quad\mathbb{P}\bigl(X-\mu_{\sssig X}\leqslant-a\bigr)\leqslant\frac{\,\sigma_{\sssig X}^{2}\,}{\,\sigma_{\sssig X}^{2}+a^{2}\,}
\end{gathered}
$$

</div>

</div>

<div class="topic-proof" markdown="1">
**Proof.** 若 $\sigma_{\sssig X}=0$，則 $\mathbb{P}(X=\mu_{\sssig X})=1$，兩個不等式的左右兩側皆為 $0$，結論成立；以下設 $\sigma_{\sssig X}>0$。令 $Y=X-\mu_{\sssig X}$，則我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(Y)=\mathbb{E}(X-\mu_{\sssig X})=0,\quad\mathrm{Var}(Y)=\mathbb{E}(Y^{2})=\mathrm{Var}(X)=\sigma_{\sssig X}^{2}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{E}(Y)=\mathbb{E}(X-\mu_{\sssig X})=0\\[0.45em]
\mathrm{Var}(Y)=\mathbb{E}(Y^{2})=\mathrm{Var}(X)=\sigma_{\sssig X}^{2}
\end{gathered}
$$

</div>

令 $h(y)=(y+c)^{2}$，其中 $c>0$，則對於 $Y=X-\mu_{\sssig X}\geqslant a>0$，有 $h(Y)=h(X-\mu_{\sssig X})\geqslant h(a)$。由 [Theorem 2.31](#thm-nonnegative-function-bound) 可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}\bigl(X-\mu_{\sssig X}\geqslant a\bigr)&=\mathbb{P}(Y\geqslant a)\leqslant\mathbb{P}\bigl(h(Y)\geqslant h(a)\bigr)\\[0.45em]
&\leqslant\frac{\,\mathbb{E}\bigl[h(Y)\bigr]\,}{h(a)}=\frac{\,\mathbb{E}\bigl[(Y+c)^{2}\bigr]\,}{(a+c)^{2}},\quad c>0
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}\bigl(X-\mu_{\sssig X}\geqslant a\bigr)=\mathbb{P}(Y\geqslant a)\\[0.45em]
&\quad \leqslant\mathbb{P}\bigl(h(Y)\geqslant h(a)\bigr)\leqslant\frac{\,\mathbb{E}\bigl[h(Y)\bigr]\,}{h(a)}\\[0.45em]
&\quad =\frac{\,\mathbb{E}\bigl[(Y+c)^{2}\bigr]\,}{(a+c)^{2}},\quad c>0
\end{aligned}
$$

</div>

此式對每一個 $c>0$ 都成立，此即

$$
\mathbb{P}\bigl(X-\mu_{\sssig X}\geqslant a\bigr)\leqslant\inf_{c>0}\frac{\,\mathbb{E}\bigl[(Y+c)^{2}\bigr]\,}{(a+c)^{2}}
$$

又由 $\mathbb{E}(Y)=0$ 可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\bigl[(Y+c)^{2}\bigr]=\mathbb{E}\bigl[Y^{2}+2cY+c^{2}\bigr]=\mathbb{E}(Y^{2})+c^{2}=\sigma_{\sssig X}^{2}+c^{2}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[(Y+c)^{2}\bigr]&=\mathbb{E}\bigl[Y^{2}+2cY+c^{2}\bigr]\\[0.45em]
&=\mathbb{E}(Y^{2})+c^{2}=\sigma_{\sssig X}^{2}+c^{2}
\end{aligned}
$$

</div>

故可知

$$
\inf_{c>0}\frac{\,\mathbb{E}\bigl[(Y+c)^{2}\bigr]\,}{(a+c)^{2}}=\inf_{c>0}\frac{\,\sigma_{\sssig X}^{2}+c^{2}\,}{(a+c)^{2}}
$$

並可令 $g(c)=\frac{\,\sigma_{\sssig X}^{2}+c^{2}\,}{(a+c)^{2}}$，則由微積分可知，一階條件 <span lang="en">(first-order condition, f.o.c.)</span> 為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
g^{\prime}(c)=\frac{\,2ca-2\sigma_{\sssig X}^{2}\,}{(a+c)^{3}}=0\ \Longrightarrow\ c=\frac{\,\sigma_{\sssig X}^{2}\,}{a}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
g^{\prime}(c)&=\frac{\,2ca-2\sigma_{\sssig X}^{2}\,}{(a+c)^{3}}=0\\[0.45em]
&\Longrightarrow\ c=\frac{\,\sigma_{\sssig X}^{2}\,}{a}
\end{aligned}
$$

</div>

二階條件 <span lang="en">(second-order condition, s.o.c.)</span> 請讀者自行驗證。將 $c$ 代回，則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\inf_{c>0}\frac{\,\sigma_{\sssig X}^{2}+c^{2}\,}{(a+c)^{2}}&=\frac{\,\sigma_{\sssig X}^{2}+c^{2}\,}{(a+c)^{2}}\Bigg|_{c=\frac{\sigma_{\sssig X}^{2}}{a}}=\frac{\,\sigma_{\sssig X}^{2}+\bigl(\frac{\sigma_{\sssig X}^{2}}{a}\bigr)^{2}\,}{\bigl(a+\frac{\sigma_{\sssig X}^{2}}{a}\bigr)^{2}}\\[0.45em]
&=\frac{\,\sigma_{\sssig X}^{2}\bigl(1+\frac{\sigma_{\sssig X}^{2}}{a^{2}}\bigr)\,}{a^{2}\bigl(1+\frac{\sigma_{\sssig X}^{2}}{a^{2}}\bigr)^{2}}=\frac{\sigma_{\sssig X}^{2}}{\,a^{2}+\sigma_{\sssig X}^{2}\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\inf_{c>0}\frac{\,\sigma_{\sssig X}^{2}+c^{2}\,}{(a+c)^{2}}=\frac{\,\sigma_{\sssig X}^{2}+c^{2}\,}{(a+c)^{2}}\Bigg|_{c=\frac{\sigma_{\sssig X}^{2}}{a}}\\[0.45em]
&\quad =\frac{\,\sigma_{\sssig X}^{2}+\bigl(\frac{\sigma_{\sssig X}^{2}}{a}\bigr)^{2}\,}{\bigl(a+\frac{\sigma_{\sssig X}^{2}}{a}\bigr)^{2}}=\frac{\,\sigma_{\sssig X}^{2}\bigl(1+\frac{\sigma_{\sssig X}^{2}}{a^{2}}\bigr)\,}{a^{2}\bigl(1+\frac{\sigma_{\sssig X}^{2}}{a^{2}}\bigr)^{2}}\\[0.45em]
&\quad =\frac{\sigma_{\sssig X}^{2}}{\,a^{2}+\sigma_{\sssig X}^{2}\,}
\end{aligned}
$$

</div>

故可知

$$
\mathbb{P}\bigl(X-\mu_{\sssig X}\geqslant a\bigr)\leqslant\frac{\,\sigma_{\sssig X}^{2}\,}{\,a^{2}+\sigma_{\sssig X}^{2}\,}
$$

另一部分同理可證。原式得證。 <span class="topic-qed">$\square$</span>
</div>

單邊柴比雪夫不等式 <span lang="en">(one-tailed Chebyshev’s inequality)</span> 有一些地方需要注意:

(1) 此不等式又被稱作**坎特利不等式 <span lang="en">(Cantelli’s inequality)</span>**，與[馬可夫不等式](#thm-markov)及[柴比雪夫不等式](#thm-chebyshev)相似，是由 [Theorem 2.31](#thm-nonnegative-function-bound)，經由挑選特殊的函數 $h(\cdot)$ 所衍生而來。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

此不等式與柴比雪夫不等式的密切關係不言可喻，如果我們同時將這個不等式的兩個部分合併，則我們可以得到

$$
\mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert\geqslant a\bigr)\leqslant\frac{\,2\,\sigma_{\sssig X}^{2}\,}{\,\sigma_{\sssig X}^{2}+a^{2}\,}
$$

這個版本被稱作**弱版**的柴比雪夫不等式。

雖然坎特利不等式，看起來像是弱化過的柴比雪夫不等式，但事實上，坎特利不等式卻是強化版的馬可夫不等式，其理由是我們應用了更多關於分配的訊息 (即二階動差)，即我們以更多的分配資訊來「改進」其機率上界。稍後我們將看到[車諾夫不等式 <span lang="en">(Chernoff inequality)</span>](/teaching-topics/ch2-p220-candidate/#thm-chernoff)，其與馬可夫不等式的關係，亦是運用了更多動差資訊來改進其機率上界。

</div>

(2) 與馬可夫不等式、柴比雪夫不等式相仿，坎特利不等式同樣具有另一個版本。若 $k>0$ 且 $\sigma_{\sssig X}>0$，則
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}\bigl(X-\mu_{\sssig X}\geqslant k\,\sigma_{\sssig X}\bigr)\leqslant\frac{1}{\,1+k^{2}\,}\quad\text{且}\quad\mathbb{P}\bigl(X-\mu_{\sssig X}\leqslant-k\,\sigma_{\sssig X}\bigr)\leqslant\frac{1}{\,1+k^{2}\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{P}\bigl(X-\mu_{\sssig X}\geqslant k\,\sigma_{\sssig X}\bigr)\leqslant\frac{1}{\,1+k^{2}\,}\\[0.45em]
\text{且}\quad\mathbb{P}\bigl(X-\mu_{\sssig X}\leqslant-k\,\sigma_{\sssig X}\bigr)\leqslant\frac{1}{\,1+k^{2}\,}
\end{gathered}
$$

</div>

<div id="note-median-mean-distance" class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

在這個版本中，我們可以設定 $k=1$，則我們將得到一個有趣的結果，即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X\geqslant\mu_{\sssig X}+\sigma_{\sssig X})\leqslant\frac{1}{\,2\,}\quad\text{且}\quad\mathbb{P}(X\leqslant\mu_{\sssig X}-\sigma_{\sssig X})\leqslant\frac{1}{\,2\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{P}(X\geqslant\mu_{\sssig X}+\sigma_{\sssig X})\leqslant\frac{1}{\,2\,}\\[0.45em]
\text{且}\quad\mathbb{P}(X\leqslant\mu_{\sssig X}-\sigma_{\sssig X})\leqslant\frac{1}{\,2\,}
\end{gathered}
$$

</div>

這個結果指出，**對任意分配而言，[中位數](/teaching-topics/ch2-p211-candidate/#def-median) $\eta_{\sssig X}$ 與期望值 $\mu_{\sssig X}$ 位置的差距，前後應不超過一個標準差**。

</div>

## 本篇小結

[Theorem 2.31](#thm-nonnegative-function-bound) 是本篇三個不等式共同的起點: 對非負可測實值函數 $h(\cdot)$ 與常數 $a>0$，只要 $\mathbb{E}[h(X)]<\infty$，就有 $\mathbb{P}(h(X)\geqslant a)\leqslant\frac{\mathbb{E}[h(X)]}{a}$ 這條界限。證明的關鍵有二: 一是把 $\mathbb{E}[h(X)]$ 的積分拆成 $A=\lbrace x\mid h(x)\geqslant a\rbrace$ 與 $A^{\prime}$ 兩段，由 $h(\cdot)$ 非負而捨去 $A^{\prime}$ 上的積分；二是在 $A$ 之上以 $a$ 取代 $h(x)$，再由 $X\in A\Longleftrightarrow h(X)\geqslant a$ 把積分換回機率。

在這條定理中取 $h(x)=x_{+}$，對非負隨機變數即得[馬可夫不等式](#thm-markov) $\mathbb{P}(X\geqslant a)\leqslant\frac{\mathbb{E}(X)}{a}$，它只用到一階動差；取 $h(x)=(x_{+})^{r}$ 得到[擴展版](#note-markov-extended)，再以 $r=2$ 施於 $\lvert X-\mu_{\sssig X}\rvert$，便得到[柴比雪夫不等式](#thm-chebyshev) $\mathbb{P}(\lvert X-\mu_{\sssig X}\rvert\geqslant a)\leqslant\frac{\sigma_{\sssig X}^{2}}{a^{2}}$，它多用了二階動差，因而不再要求隨機變數非負。兩者都另有以 $k$ 倍期望值或 $k$ 倍標準差表示的版本，兩個版本都要求 $k>0$，前者另需 $\mathbb{E}(X)>0$、後者另需 $\sigma_{\sssig X}>0$，其直觀分別呈現在 [Fig. 2.19](#fig-markov-intuition) 與 [Fig. 2.20](#fig-chebyshev-intuition): 前者是右尾的機率不超過 <span class="text-nowrap">$\frac{1}{k}$，</span>後者是中央區間的機率至少為 $1-\frac{1}{k^{2}}$。柴比雪夫不等式也可以不經由馬可夫不等式，直接由變異數的定義分段放大而得。

[Theorem 2.34](#thm-one-tailed-chebyshev) 的單邊柴比雪夫不等式，亦即坎特利不等式，改取 $h(y)=(y+c)^{2}$ 之後對 $c>0$ 取下確界，把單側的機率界定在 $\frac{\sigma_{\sssig X}^{2}}{\sigma_{\sssig X}^{2}+a^{2}}$ 之內；兩側合併得到的是弱版的柴比雪夫不等式，而在 $\sigma_{\sssig X}>0$ 之下取 $k=1$，則得到[中位數與期望值相距不超過一個標準差](#note-median-mean-distance)的結果。三個不等式所用的動差訊息都只到二階，[下一篇](/teaching-topics/ch2-p220-candidate/)改以動差母函數界定尾機率，也就是車諾夫不等式。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
