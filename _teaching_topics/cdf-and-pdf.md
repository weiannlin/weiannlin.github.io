---
title: "累積分配函數與機率密度函數"
subtitle: "Cumulative Distribution Functions and Probability Density Functions"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 3
order: 203
permalink: /teaching-topics/cdf-and-pdf/
redirect_from:
  - /teaching-topics/probability-accumulates/
  - /teaching-topics/continuous-random-variables-pdf/
date: 2026-06-06
published: false
listed: false
excerpt: "累積分配函數定義為 $F_{\\sssig X}(x)=\\mathbb{P}(X\\leqslant x)$，對離散型與連續型都適用，並具有值域介於 $0$ 與 $1$、非遞減、右連續、離散型為階梯函數，以及兩端極限分別為 $0$ 與 $1$ 五項性質。連續型的累積分配函數可寫成一個非負函數的積分，該函數即機率密度函數；它由積分定義而來，本身不是機率，而是累積機率的變化率。有了這兩個函數，各種區間的機率都能以累積分配函數表示: 連續型的單點機率為 $0$，端點的等號可以互換；離散型因具有單點機率，等號不可任意省略。"
---

[上一篇文章](/teaching-topics/discrete-random-variables-pmf/)以機率質量函數記錄離散型隨機變數在每一個質點上的單點機率。pmf 只適用於離散型；本篇改由 $\mathbb{P}(X\leqslant x)$ 出發，先給出對兩種型態都適用的累積分配函數，再回到連續型，介紹以積分定義的機率密度函數，最後說明如何以累積分配函數計算各種區間的機率。

## 累積分配函數的定義

<div id="def-cdf" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.4</div>

若 $X$ 為定義於機率空間 $(S,\mathcal{F},\mathbb{P})$ 上之隨機變數，則定義函數

$$
F_{\sssig X}(x)=\mathbb{P}(X\leqslant x),\ x\in\mathbb{R}
$$

我們稱 $F_{\sssig X}(x)$ 為 $X$ 的**累積分配函數 (cumulative distribution function, cdf)** 或簡稱為**分配函數 (distribution function, df)**。

</div>

累積分配函數 (cumulative distribution function, cdf) 有一些地方需要注意:

(1) **累積分配函數 (cumulative distribution function, cdf)** $F_{\sssig X}(x)$ 是一種定義在實數 $\mathbb{R}$ 上的函數，且將其對應到 $[0,1]$ 區間中的函數，可以記為
{: .topic-paren-item}

$$
F\colon\mathbb{R}\to[0,1]
$$

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

有些教科書將 cdf 的定義寫為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig X}(x)=\mathbb{P}(X\leqslant x)=\mathbb{P}\bigl(\,X^{-1}(-\infty,x]\,\bigr),\ x\in\mathbb{R}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig X}(x)&=\mathbb{P}(X\leqslant x)\\[0.4em]
&=\mathbb{P}\bigl(\,X^{-1}(-\infty,x]\,\bigr),\ x\in\mathbb{R}
\end{aligned}
$$

</div>

這個版本中，如果搭配 $X^{\sssig -1}(\cdot)$ 的定義，我們將更容易看出 cdf 是如何將一個實數範圍上的集合，對應回樣本點進行機率的計算的。

</div>

(2) 累積分配函數的定義中，並不限制 $X$ 是一個離散型隨機變數，或是連續型隨機變數，但是由於 $\mathbb{P}(X\leqslant x)$ 的運算，在離散型隨機變數上是採用累加的方式，故亦有教科書認為應分開定義，且應翻譯為**累加分配函數**。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

連續型隨機變數中的累積分配函數，其運算性質是採用微積分中的**積分 (integration)**，雖然其本質仍為累加，但由於運算細節有所不同，故許多教科書並不將其認為是一種**加總 (summation)**。

</div>

由定義可知，$F_{\sssig X}(x)$ 記錄的是門檻 $x$ 左側所累積的機率。門檻由 $x_1$ 移到較大的 $x_2$ 時，原本已落在門檻左側的樣本點仍然保留，只會再納入新的樣本點。

<figure id="fig-cdf-nested-thresholds" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/cdf-nested-thresholds.svg" alt="兩條平行數線展示 x1 小於等於 x2 時，事件 X 小於等於 x1 被包含於事件 X 小於等於 x2。">
  <figcaption><span class="topic-figure__label">Fig. 2.2.</span> 若 $x_1\leqslant x_2$，則所有滿足 $X(\omega)\leqslant x_1$ 的樣本點，也必定滿足 $X(\omega)\leqslant x_2$。大小關係發生在 $X(\omega)$ 的數值上，事件之間因此形成包含關係。</figcaption>
</figure>

由圖可見，兩個門檻所對應的事件形成包含關係。這個包含關係，正是下列各項性質的來源。

## 累積分配函數的性質

<div id="thm-cdf-properties" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.1 (Properties of a cdf)</div>

若 $F_{\sssig X}(x)$ 為 $X$ 之累積分配函數，則其具以下性質:

(1) 對任意 $x\in\mathbb{R}$，皆有
{: .topic-paren-item}

$$
0\leqslant F_{\sssig X}(x)\leqslant1
$$

(2) $F_{\sssig X}(x)$ **非遞減 (non-decreasing)**。
{: .topic-paren-item}

(3) $F_{\sssig X}(x)$ **右連續 (right-continuous)**。
{: .topic-paren-item}

(4) 若 $X$ 為離散型隨機變數，$F_{\sssig X}(x)$ 為一**階梯函數 (step function)**。
{: .topic-paren-item}

(5) $F_{\sssig X}(x)$ 在兩端的極限為
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lim_{x\to-\infty}F_{\sssig X}(x)=0,\qquad\lim_{x\to\infty}F_{\sssig X}(x)=1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\lim_{x\to-\infty}F_{\sssig X}(x)=0\\[0.5em]
\lim_{x\to\infty}F_{\sssig X}(x)=1
\end{gathered}
$$

</div>

</div>

<div class="topic-proof" markdown="1">
**Proof.** 若 $x_1\leqslant x_2$，則 $\lbrace X\leqslant x_1\rbrace\subseteq\lbrace X\leqslant x_2\rbrace$，故由[單調性](/teaching-topics/probability-rules-from-axioms/#theorem-monotonicity)可得 <span class="text-nowrap">$F_{\sssig X}(x_1)\leqslant F_{\sssig X}(x_2)$，</span>此即第 (2) 項；又 $F_{\sssig X}(x)$ 本身是一個事件的機率，故 <span class="text-nowrap">$0\leqslant F_{\sssig X}(x)\leqslant1$，</span>此即第 (1) 項。

其次，令 $n\to\infty$，則 $\lbrace X\leqslant -n\rbrace$ 為非遞增序列且極限為空集合，$\lbrace X\leqslant n\rbrace$ 為非遞減序列且極限為樣本空間。由[單調事件序列的機率極限](/teaching-topics/probability-rules-from-axioms/#theorem-continuity)可得 $F_{\sssig X}(-n)\to0$ 與 <span class="text-nowrap">$F_{\sssig X}(n)\to1$，</span>再配合第 (2) 項的非遞減，即得第 (5) 項的兩個極限。

再者，若 $x_n\downarrow x$，則 $\lbrace X\leqslant x_n\rbrace$ 為非遞增序列且極限為 <span class="text-nowrap">$\lbrace X\leqslant x\rbrace$。</span>再用一次單調事件序列的機率極限，可得 <span class="text-nowrap">$F_{\sssig X}(x_n)\to F_{\sssig X}(x)$，</span>此即第 (3) 項的右連續。

最後看第 (4) 項。這一項須補上一個前提: 值域 $\mathcal R_{\sssig X}$ 中的質點在每一個有界區間內都只有有限多個 (詳見下方的 Note)。任取 $a<b$，落在 $[a,b]$ 中的質點依大小記為 <span class="text-nowrap">$t_1<t_2<\cdots<t_k$。</span>若 $t_i\leqslant x<t_{i+1}$，則 $\lbrace X\leqslant x\rbrace$ 與 <span class="text-nowrap">$\lbrace X\leqslant t_i\rbrace$</span> 是同一個事件，故 $F_{\sssig X}$ 在 <span class="text-nowrap">$[t_i,t_{i+1})$</span> 上為常數。另一方面，取 <span class="text-nowrap">$x_n\uparrow t_i$，</span>則 $\lbrace X\leqslant x_n\rbrace$ 為非遞減序列且極限為 <span class="text-nowrap">$\lbrace X<t_i\rbrace$，</span>故由單調事件序列的機率極限可得 <span class="text-nowrap">$F_{\sssig X}(t_i^{-})=\mathbb{P}(X<t_i)$，</span>因而

$$
F_{\sssig X}(t_i)-F_{\sssig X}(t_i^{-})=p_{\sssig X}(t_i)>0
$$

也就是說，$F_{\sssig X}$ 在任意有界區間上都只分成有限多段水平線段，並在各段之間跳躍，此即階梯函數。<span class="topic-qed">$\square$</span>
</div>

<div id="note-step-function-isolated-points" class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

第 (4) 項要成立，須有一個前提: 值域中的質點在每一個有界區間內都只有有限多個，這等價於值域在 $\mathbb{R}$ 中沒有聚點。本章所遇到的離散型隨機變數都合乎這個前提，此時 $F_{\sssig X}$ 在相鄰兩個質點之間保持水平，並在每一個質點處跳躍。

只要求每一個質點都是孤立點並不夠。取值域為 $\lbrace 1/n:n=1,2,\ldots\rbrace$、$p_{\sssig X}(1/n)=2^{-n}$，每一個質點都有一個不含其他質點的鄰域，但 $0$ 的右側任一鄰域內都有無窮多個跳躍，含 $0$ 的區間無法分成有限多段水平線段，$F_{\sssig X}$ 也就不是階梯函數。此時 $F_{\sssig X}$ 仍為非遞減且右連續，第 (1)、(2)、(3)、(5) 四項不受影響。

</div>

累積分配函數是一種累積的機率，以離散型隨機變數而言，其定義 $\mathbb{P}(X\leqslant x)$ 代表「小於等於 $x$ 的所有機率總和」，即 $\sum_{t\leqslant x}\mathbb{P}(X=t)$，故其當然介在 $0$ 至 $1$ 之間。

以投擲一顆公正骰子為例，要累加的就是門檻左側的那些機率質量。

<figure id="fig-dice-pmf-threshold" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/dice-pmf-threshold.svg" alt="公正骰子的 pmf 棒棒糖圖。點數 1, 2, 3 的機率質量被標成紅色，門檻 x=3.4 位於 3 與 4 之間。">
  <figcaption><span class="topic-figure__label">Fig. 2.3.</span> 公正骰子的六個點數各具機率 <span class="text-nowrap">$1/6$。</span>即使門檻 $x=3.4$ 不是骰子點數，門檻左側仍只有點數 $1,2,3$，故 <span class="text-nowrap">$F_{\sssig X}(3.4)=3/6$。</span></figcaption>
</figure>

又因為其機率為累積 (或累加)，隨著 $x$ 的增長，函數值 $F_{\sssig X}(x)$ 只會向上增加或持平，故其累積分配函數當然具有**非遞減**之性質，且**右連續**。

<figure id="fig-dice-cdf-jump" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/dice-cdf-jump.svg" alt="公正骰子的 cdf 階梯圖。每個整數點都有高度 1/6 的跳躍。">
  <figcaption><span class="topic-figure__label">Fig. 2.4.</span> 公正骰子的 cdf 在每一個點數處跳躍 $1/6$，其餘各段保持水平，這正是第 (4) 項所說的階梯函數。在 $x=3.4$ 處，函數值為 <span class="text-nowrap">$3/6$。</span></figcaption>
</figure>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

事實上在連續型隨機變數中 $F_{\sssig X}(x)$ 是一連續函數 (即左連續且右連續)；而僅右連續的狀況發生在離散型隨機變數，或稍後的章節中會談到的[混合型隨機變數](/teaching-topics/mixed-random-variables/)中。

</div>

<div id="ex-two-ball-sum-cdf" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.2 (continued)</div>

若箱中有四顆大小形狀完全相同、分別編號 $0$ 至 $3$ 的球，若 $X$ 表示隨機從中一次抽取兩顆球的號碼總和，則試列出且畫出其 cdf。

前一篇的 [Example 2.2](/teaching-topics/discrete-random-variables-pmf/#ex-two-ball-sum) 已求得 $X$ 的 pmf 為 $p_{\sssig X}(1)=p_{\sssig X}(2)=p_{\sssig X}(4)=p_{\sssig X}(5)=\frac{1}{6}$ 與 $p_{\sssig X}(3)=\frac{1}{3}$，依序累加可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & x<1\\[0.5em]
0+p_{\sssig X}(1)=\frac{1}{6}, & 1\leqslant x<2\\[0.5em]
0+p_{\sssig X}(1)+p_{\sssig X}(2)=\frac{2}{6}, & 2\leqslant x<3\\[0.5em]
0+p_{\sssig X}(1)+p_{\sssig X}(2)+p_{\sssig X}(3)=\frac{4}{6}, & 3\leqslant x<4\\[0.5em]
\begin{gathered}0+p_{\sssig X}(1)+p_{\sssig X}(2)+p_{\sssig X}(3)\\[0.2em]+p_{\sssig X}(4)=\frac{5}{6},\end{gathered} & 4\leqslant x<5\\[0.5em]
\begin{gathered}0+p_{\sssig X}(1)+p_{\sssig X}(2)+p_{\sssig X}(3)\\[0.2em]+p_{\sssig X}(4)+p_{\sssig X}(5)=\frac{6}{6}=1,\end{gathered} & 5\leqslant x
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&x<1:\quad F_{\sssig X}(x)=0\\[0.6em]
&1\leqslant x<2:\\
&\quad F_{\sssig X}(x)=0+p_{\sssig X}(1)=\frac{1}{6}\\[0.6em]
&2\leqslant x<3:\\
&\quad F_{\sssig X}(x)=0+p_{\sssig X}(1)+p_{\sssig X}(2)\\
&\qquad =\frac{2}{6}\\[0.6em]
&3\leqslant x<4:\\
&\quad F_{\sssig X}(x)=0+p_{\sssig X}(1)+p_{\sssig X}(2)\\
&\qquad +p_{\sssig X}(3)=\frac{4}{6}\\[0.6em]
&4\leqslant x<5:\\
&\quad F_{\sssig X}(x)=0+p_{\sssig X}(1)+p_{\sssig X}(2)\\
&\qquad +p_{\sssig X}(3)+p_{\sssig X}(4)=\frac{5}{6}\\[0.6em]
&5\leqslant x:\\
&\quad F_{\sssig X}(x)=0+p_{\sssig X}(1)+p_{\sssig X}(2)\\
&\qquad +p_{\sssig X}(3)+p_{\sssig X}(4)+p_{\sssig X}(5)\\
&\qquad =\frac{6}{6}=1
\end{aligned}
$$

</div>

</div>

<figure id="fig-two-ball-sum-cdf" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/two-ball-sum-cdf.svg" alt="四球取兩顆之號碼總和的 cdf 階梯圖。函數在 x 小於 1 時為 0，並在 x 等於 1, 2, 3, 4, 5 處依序跳躍 1/6、1/6、2/6、1/6、1/6，於 x 大於等於 5 之後維持在 1。">
  <figcaption><span class="topic-figure__label">Fig. 2.5.</span> Example 2.2 的 cdf: 五個跳躍分別發生在 $x=1,2,3,4,5$，高度依序為 <span class="text-nowrap">$1/6$、</span><span class="text-nowrap">$1/6$、</span><span class="text-nowrap">$2/6$、</span><span class="text-nowrap">$1/6$、</span><span class="text-nowrap">$1/6$。</span>本圖的縱軸以 $1$ 為滿刻度，與 Fig. 2.6 的縱軸比例尺不同，兩圖的高度不可直接比較。</figcaption>
</figure>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

本題同樣是為了協助讀者建立離散型 cdf 的操作，才將解答寫得這麼繁瑣，爾後的答案將會寫得比較簡潔。

</div>

上圖是典型的離散型 cdf，每一階的跳躍點，都對應到原本的 pmf 中的機率質點，且躍升的高度即是該點的機率，故我們可以由離散型 cdf 轉換為其對應的 pmf，如下圖 (其嚴謹敘述見後面的 [Theorem 2.6](#thm-discrete-interval-probability))。

<figure id="fig-cdf-to-pmf" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/cdf-to-pmf.svg" alt="由前一張 cdf 階梯圖的跳躍高度還原而得的 pmf 點圖。x 等於 1, 2, 4, 5 處的點高為 1/6，x 等於 3 處的點高為 1/3。">
  <figcaption><span class="topic-figure__label">Fig. 2.6.</span> 由 Fig. 2.5 各階的躍升高度還原而得的 pmf: <span class="text-nowrap">$p_{\sssig X}(1)=p_{\sssig X}(2)=p_{\sssig X}(4)=p_{\sssig X}(5)=1/6$，</span><span class="text-nowrap">$p_{\sssig X}(3)=1/3$。</span>本圖的縱軸以 $1/2$ 為最高刻度，與 Fig. 2.5 的縱軸比例尺不同，兩圖的高度不可直接比較。</figcaption>
</figure>

<div id="ex-geometric-cdf" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.3 (continued)</div>

<div lang="en" markdown="1">
Suppose that the probability mass function of a random variable $X$ is

$$
p_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
\left(\dfrac{1}{2}\right)^{x}, & x=1,2,\ldots\\[0.6em]
0, & \text{otherwise}
\end{array}
\right.
$$

Find the cumulative distribution function of <span class="text-nowrap">$X$.</span>
</div>

前一篇的 [Example 2.3](/teaching-topics/discrete-random-variables-pmf/#ex-geometric-pmf) 已求得該 pmf 的常數為 $1$。對 $x\geqslant1$，把不超過 $x$ 的各項等比級數相加，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & x<1\\[0.8em]
\dfrac{\dfrac{1}{2}\left(1-\left(\dfrac{1}{2}\right)^{\lfloor x\rfloor}\right)}{1-\dfrac{1}{2}}=1-\left(\dfrac{1}{2}\right)^{[x]}, & x\geqslant1
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&x<1:\\
&\quad F_{\sssig X}(x)=0\\[0.7em]
&x\geqslant1:\\
&\quad F_{\sssig X}(x)=\frac{\frac{1}{2}\left(1-\left(\frac{1}{2}\right)^{\lfloor x\rfloor}\right)}{1-\frac{1}{2}}\\[0.4em]
&\qquad\qquad =1-\left(\frac{1}{2}\right)^{[x]}
\end{aligned}
$$

</div>

其中 $\lfloor x\rfloor$ 表**取底函數 (floor function)**，亦稱為**高斯符號** (記為 $[x]$)，表不大於 $x$ 之最大整數。

</div>

<div id="ex-degenerate-cdf" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.5 (Recovering a pmf from a cdf)</div>

若 $X$ 為一隨機變數，且其 cdf 為

$$
F_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & x<0\\[0.4em]
1, & x\geqslant0
\end{array}
\right.
$$

則求其 pmf 為何？

<figure id="fig-degenerate-cdf" class="topic-figure topic-figure--narrow">
  <img src="/images/teaching-topics/degenerate-cdf.svg" alt="退化型隨機變數的 cdf 階梯圖。函數在 x 小於 0 時為 0，於 x 等於 0 處由 0 跳到 1，其後維持在 1。">
  <figcaption><span class="topic-figure__label">Fig. 2.7.</span> Example 2.5 的 cdf: 全部的機率集中在 $x=0$ 一點上，函數在該處由 $0$ <span class="text-nowrap">跳到 $1$，</span>跳躍高度為 <span class="text-nowrap">$1$。</span></figcaption>
</figure>

$F_{\sssig X}(x)$ 在 $x=0$ 處發生一高度為 $1$ 之跳躍，故可由此得知

$$
p_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
1, & x=0\\[0.4em]
0, & \text{otherwise}
\end{array}
\right.
$$

</div>

至此，我們已經看到累積分配函數如何以累加的方式，記錄離散型隨機變數的機率。接下來我們轉向連續型，看看同一個 $F_{\sssig X}(x)$ 在連續型隨機變數上是由什麼函數積分而來。

離散型隨機變數的累積分配函數 $F_{\sssig X}(x)=\mathbb{P}(X\leqslant x)$ 是以累加得到的。連續型隨機變數沒有單點機率可以累加，其累積分配函數改由一個非負函數的積分而來；以下就從這個非負函數的定義談起。

## 機率密度函數的定義

<span id="definition-24"></span>
<div id="def-pdf" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.5</div>

若 $X$ 為一連續型隨機變數，cdf 為 <span class="text-nowrap">$F_{\sssig X}(x)$，</span>值域為 <span class="text-nowrap">$\mathcal R_{\sssig X}$。</span>若非負函數 $f_{\sssig X}(\cdot)$ 滿足

$$
F_{\sssig X}(x)=\int_{-\infty}^{x}f_{\sssig X}(t)\,dt,\ x\in\mathbb{R}
$$

則稱 $f_{\sssig X}(x)$ 為 $X$ 之**機率密度函數 (probability density function, pdf)**。

</div>

機率密度函數 (probability density function, pdf) 有一些地方需要注意:

(1) 由此定義可以看出，cdf 的定義在離散型與連續型隨機變數其實是相似的，只是前者為「加」而後者為「積」，由此也衍伸出許多二者間相似但仍有差異的性質，我們稍後會談到。
{: .topic-paren-item}

(2) 我們曾經提過，cdf 是一種累積機率，若由微積分的角度來看，機率密度函數應不是一種機率，而是**累積機率的變化率**，此點與 pmf 本身即是機率不同。
{: .topic-paren-item}

(3) 由此定義再次審視累積分配函數，可以發現連續型隨機變數的累積分配函數事實上是一種**面積**，我們稍後會細談這個特點，這裡可以先由下圖理解之。
{: .topic-paren-item}

<figure id="fig-cdf-as-area" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/continuous-cdf-area.svg" alt="連續型隨機變數的 cdf 可由密度曲線左側面積表示。">
  <figcaption><span class="topic-figure__label">Fig. 2.8.</span> 對連續型隨機變數而言，$F_{\sssig X}(x)$ 就是密度函數在 $(-\infty,x]$ 上所圍出的面積。</figcaption>
</figure>

若以微積分的觀點理解上圖，我們將得到如下的關係式:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
F^{\prime}_{\sssig X}(x)=\dfrac{dF_{\sssig X}(x)}{dx}, & x\text{ 是 }\mathcal{R}_{\sssig X}\text{ 中的可微分點}\\[0.8em]
0, & x\text{ 是 }\mathcal{R}_{\sssig X}\text{ 中的不可微分點或不在 }\mathcal{R}_{\sssig X}\text{ 中}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&x\text{ 是 }\mathcal{R}_{\sssig X}\text{ 中的可微分點}:\\
&\quad f_{\sssig X}(x)=F^{\prime}_{\sssig X}(x)=\frac{dF_{\sssig X}(x)}{dx}\\[0.7em]
&x\text{ 是 }\mathcal{R}_{\sssig X}\text{ 中的不可微分點}\\
&\text{或不在 }\mathcal{R}_{\sssig X}\text{ 中}:\\
&\quad f_{\sssig X}(x)=0
\end{aligned}
$$

</div>

上式可由**微積分基本定理 (fundamental theorem of calculus, FTC)** 直接得到。透過微積分的觀點來理解這些關係，我們能夠進一步引伸出許多性質，下面就介紹機率密度函數所具備的各種性質。

## 機率密度函數的性質

<div id="thm-pdf-properties" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.2 (Properties of a pdf)</div>

一連續型隨機變數 $X$ 之機率密度函數 $f_{\sssig X}(x)$ 應滿足以下性質:

(1) 對任意 $x\in\mathcal R_{\sssig X}$，皆有
{: .topic-paren-item}

$$
f_{\sssig X}(x)\geqslant0
$$

(2) $X$ 的取值落在值域中的機率為
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X\in\mathcal{R}_{\sssig X})=\int_{x\in\mathcal{R}_{\sssig X}}f_{\sssig X}(x)\,dx=\int_{-\infty}^{\infty}f_{\sssig X}(x)\,dx=1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X\in\mathcal{R}_{\sssig X})&=\int_{x\in\mathcal{R}_{\sssig X}}f_{\sssig X}(x)\,dx\\[0.4em]
&=\int_{-\infty}^{\infty}f_{\sssig X}(x)\,dx=1
\end{aligned}
$$

</div>

(3) 對任意波雷爾集合 $A$，皆有
{: .topic-paren-item}

$$
\mathbb{P}(X\in A)=\int_{x\in A\cap\mathcal{R}_{\sssig X}}f_{\sssig X}(x)\,dx
$$

</div>

連續型隨機變數引入了微積分的概念，機率密度函數更是由積分定義而來。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

許多同學將 pdf 的定義誤解為由 cdf 微分而來，事實上這是 pdf 的「性質」而非定義。注意到，pdf 本身的定義是「滿足 $F_{\sssig X}(x)=\int_{-\infty}^{x}f_{\sssig X}(t)\,dt$ 的函數 $f_{\sssig X}(x)$」即可稱為 pdf，因此 pdf 事實上是由積分定義的，而非微分。

</div>

性質 (1) 的成立，乃是由機率密度函數實為累積分配函數的**導函數** (即斜率) 而得，我們可以下圖理解之，亦可以與 [Fig. 2.8](#fig-cdf-as-area) 進行比較，二者事實上是機率密度函數本身的積分與其反導函數的微分二種觀點。

<figure id="fig-pdf-as-derivative" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/pdf-as-derivative.svg" alt="連續型隨機變數的 cdf 曲線，其在 x 等於 a 處的切線斜率即為該點的密度值。圖中以虛線標出 a 與 F_X(a) 的位置，並以箭頭指向切線斜率等於 f_X(a) 的說明。">
  <figcaption><span class="topic-figure__label">Fig. 2.9.</span> 同一個分配的 cdf: 曲線在 $a$ 處的切線斜率即 $F^{\prime}_{\sssig X}(a)=f_{\sssig X}(a)$。Fig. 2.8 由密度看面積，本圖則由分配函數看斜率，二者互為反向。</figcaption>
</figure>

如同前述所提，機率密度函數是**累積機率的變化率**，而非機率本身，故在性質 (1) 的部分即與離散型隨機變數不同，沒有保留機率質量函數必須小於等於 $1$ 的性質；其餘的部分與離散型隨機變數則相似，只要將加總的部分改寫為積分即可得到一樣的結論。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

注意到此處的 $f_{\sssig X}(x)$ 已經不若 $p_{\sssig X}(x)$ 就是機率，而是一種變化率 (或斜率)，因此沒有必要小於 $1$；但由於 cdf $F_{\sssig X}(x)$ 非遞減，故 pdf $f_{\sssig X}(x)$ 會隨之非負。

</div>

把變化率的說法放到圖上，就是把門檻由 $x$ 往右推進一小段 $\Delta x$，並看 cdf 增加了多少。

<figure id="fig-small-interval-area" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/continuous-small-interval-area.svg" alt="連續型隨機變數在 x 到 x 加 Delta x 之間的局部區間面積。">
  <figcaption><span class="topic-figure__label">Fig. 2.10.</span> 門檻由 $x$ 推進到 $x+\Delta x$ 時，cdf 增加的量就是這一小段區間上的密度面積。當 $\Delta x$ 很小而 $f_{\sssig X}$ 在該處變化不大時，這塊面積約為 $f_{\sssig X}(x)\Delta x$，故 $f_{\sssig X}(x)$ 度量的是累積機率增加的快慢。</figcaption>
</figure>

<span id="proposition-24"></span>
<div id="prop-pdf-existence-conditions" class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Proposition 2.2 (Conditions for a pdf)</div>

令 $f\colon\mathbb{R}\to\mathbb{R}$ 為一**波雷爾可測函數 (Borel measurable function)**。若 $f$ 滿足

$$
\begin{gathered}
f(x)\geqslant0,\quad\forall x\in\mathbb{R}\\[0.7em]
\int_{-\infty}^{\infty}f(x)\,dx=1
\end{gathered}
$$

則存在一個連續型隨機變數 $X$，使 $f$ 為 $X$ 的 pdf。

</div>

<div class="topic-proof" markdown="1">
**Proof.** 在 $\bigl(\mathbb{R},\mathcal{B}(\mathbb{R})\bigr)$ 上定義

$$
\mathbb{P}(A)=\int_{A}f(x)\,dx
$$

其中 $\mathcal{B}(\mathbb{R})$ 為實數線上的[波雷爾 $\sigma$-域](/teaching-topics/event-families-sigma-fields/#實數線上的-borel-sigma-域)。由 $f$ 的非負性可得 $\mathbb{P}(A)\geqslant0$，而總積分為 $1$ 給出 $\mathbb{P}(\mathbb{R})=1$。此外，Lebesgue 積分對兩兩互斥的波雷爾集合具有可數可加性，故若 $A_1,A_2,\ldots$ 兩兩互斥，則

$$
\begin{aligned}
\mathbb{P}\left(\bigcup_{n=1}^{\infty}A_n\right)
&=\int_{\bigcup_{n=1}^{\infty}A_n}f(x)\,dx\\[0.4em]
&=\sum_{n=1}^{\infty}\int_{A_n}f(x)\,dx\\[0.4em]
&=\sum_{n=1}^{\infty}\mathbb{P}(A_n)
\end{aligned}
$$

因此 $\mathbb{P}$ 滿足[機率三大公理](/teaching-topics/event-families-sigma-fields/#definition-probability-space)，$\bigl(\mathbb{R},\mathcal{B}(\mathbb{R}),\mathbb{P}\bigr)$ 構成一個機率空間。再令 $X(\omega)=\omega$，則對任意 $x\in\mathbb{R}$，皆有 $X^{-1}\bigl((-\infty,x]\bigr)=(-\infty,x]\in\mathcal{B}(\mathbb{R})$，故 $X$ 依 [Definition 2.1](/teaching-topics/random-variables-from-sample-space-to-real-line/#def-random-variable) 為一隨機變數，且其 cdf 為

$$
F_{\sssig X}(x)=\mathbb{P}(X\leqslant x)=\int_{-\infty}^{x}f(t)\,dt
$$

依 [Definition 2.2](/teaching-topics/random-variables-from-sample-space-to-real-line/#def-support-classification) 可知 $X$ 為連續型，且依 [Definition 2.5](#def-pdf)，$f$ 確為 $X$ 的 pdf。<span class="topic-qed">$\square$</span>
</div>

[Theorem 2.2](#thm-pdf-properties) 是由 $X$ 出發的: 先有連續型隨機變數，才有它的 pdf。[Proposition 2.2](#prop-pdf-existence-conditions) 則是反過來說: 只要一個函數非負且總積分為 $1$，它就可以作為某個連續型隨機變數的 pdf。下面幾道題目多半用得到這個方向，因為題目給的只是一個帶有未知常數的函數，必須先由總積分為 $1$ 定出常數，再由非負性確認它確實是一個 pdf。

## 由機率密度函數求常數與機率

<div id="ex-quadratic-density" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.6 (A Density with an Unknown Constant)</div>

<div lang="en" markdown="1">
Suppose that a random variable $X$ has the probability density function

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
c\,(4x-2x^{2}), & 0<x<2\\[0.4em]
0, & \text{otherwise}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\left\lbrace
\begin{array}{l}
f_{\sssig X}(x)=c\,(4x-2x^{2}),\\[0.3em]
\qquad 0<x<2\\[0.6em]
f_{\sssig X}(x)=0,\quad\text{otherwise}
\end{array}
\right.
$$

</div>

<ol class="topic-list-paren">
  <li>Find the value of <span class="text-nowrap">$c$.</span></li>
  <li>Find <span class="text-nowrap">$\mathbb{P}(X>1)$.</span></li>
</ol>
</div>

(1) 由 pdf 之性質知道
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
1=\int_{-\infty}^{\infty}f_{\sssig X}(x)\,dx=\int_{0}^{2}c(4x-2x^{2})\,dx
=c\left[2x^{2}-\frac{2}{3}x^{3}\right]_{0}^{2}=\frac{8}{3}c
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
1&=\int_{-\infty}^{\infty}f_{\sssig X}(x)\,dx\\[0.4em]
&=\int_{0}^{2}c(4x-2x^{2})\,dx\\[0.4em]
&=c\left[2x^{2}-\frac{2}{3}x^{3}\right]_{0}^{2}=\frac{8}{3}c
\end{aligned}
$$

</div>

故 $c=\frac{3}{8}$。由於 $c=\frac{3}{8}>0$，可知 $f_{\sssig X}(x)\geqslant0$ 對一切 $0<x<2$ 皆成立，[Proposition 2.2](#prop-pdf-existence-conditions) 的兩項條件都得到滿足，故 $f_{\sssig X}$ 確實是一個 pdf。
{: .topic-paren-cont}

(2) 由 $c=\frac{3}{8}$ 可計算
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X>1)=\int_{1}^{2}\frac{3}{8}(4x-2x^{2})\,dx
=\left[\frac{3}{4}x^{2}-\frac{1}{4}x^{3}\right]_{1}^{2}=\frac{1}{2}
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
<div class="topic-box__label">Example 2.7 (Real Roots of a Quadratic Equation)</div>

<div lang="en" markdown="1">
Suppose that $Y\sim U(0,10)$. Find the probability that both roots of the equation <span class="text-nowrap">$g(x)=x^{2}+xY+Y+1=0$</span> are real.
</div>

由 $Y\sim U(0,10)$ 可知

$$
f_{\sssig Y}(y)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{1}{10}, & 0<y<10\\[0.6em]
0, & \text{otherwise}
\end{array}
\right.
$$

又 $g(x)=x^{2}+xY+Y+1=0$ 具二實根之條件為 $Y^{2}-4\cdot1\cdot(Y+1)\geqslant0$，此即 $Y\geqslant2+2\sqrt{2}$ 或 $Y\leqslant2-2\sqrt{2}$。由於 $2-2\sqrt{2}<0$，後者在 $Y$ 的值域上不會發生，故所求為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}\bigl(Y\geqslant2+2\sqrt{2}\ \text{ 或 }\ Y\leqslant2-2\sqrt{2}\bigr)
&=\mathbb{P}\bigl(Y\geqslant2+2\sqrt{2}\bigr)\\[0.4em]
&=\int_{2+2\sqrt{2}}^{10}\frac{1}{10}\,dy\\[0.4em]
&=\frac{1}{10}\Bigl[10-\bigl(2+2\sqrt{2}\bigr)\Bigr]\\[0.4em]
&=\frac{4}{5}-\frac{1}{5}\sqrt{2}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}\bigl(Y\geqslant2+2\sqrt{2}\ \text{ 或 }\\
&\qquad\quad Y\leqslant2-2\sqrt{2}\bigr)\\[0.4em]
&=\mathbb{P}\bigl(Y\geqslant2+2\sqrt{2}\bigr)\\[0.4em]
&=\int_{2+2\sqrt{2}}^{10}\frac{1}{10}\,dy\\[0.4em]
&=\frac{1}{10}\Bigl[10-\bigl(2+2\sqrt{2}\bigr)\Bigr]\\[0.4em]
&=\frac{4}{5}-\frac{1}{5}\sqrt{2}
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

本題所使用的分配，是**均勻分配 (uniform distribution)**，在往後介紹常見機率分配模型時，我們將會詳細介紹這個重要的分配。

</div>

<div id="ex-normal-gamma-constants" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.8 (Normalizing Constants of Two Densities)</div>

<div lang="en" markdown="1">
Suppose that each of the following functions is a probability density function. Find the constant $c$ in each case.

<ol class="topic-list-paren">
  <li>$g(x)=c\cdot e^{-\frac{(x-3)^{2}}{12}},\ x\in\mathbb{R}$</li>
  <li>$h(x)=c\cdot x^{6}e^{-3x},\ x>0$</li>
</ol>
</div>

(1) 由 pdf 之性質知道
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
1&=\int_{-\infty}^{\infty}g(x)\,dx=\int_{-\infty}^{\infty}c\cdot e^{-\frac{(x-3)^{2}}{12}}\,dx\\[0.4em]
&=c\sqrt{2\pi\cdot6}\int_{-\infty}^{\infty}\frac{1}{\sqrt{2\pi\cdot6}}\,e^{-\frac{(x-3)^{2}}{12}}\,dx\\[0.4em]
&=c\sqrt{2\pi\cdot6}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
1&=\int_{-\infty}^{\infty}g(x)\,dx\\[0.4em]
&=\int_{-\infty}^{\infty}c\cdot e^{-\frac{(x-3)^{2}}{12}}\,dx\\[0.4em]
&=c\sqrt{2\pi\cdot6}\int_{-\infty}^{\infty}\frac{e^{-\frac{(x-3)^{2}}{12}}}{\sqrt{2\pi\cdot6}}\,dx\\[0.4em]
&=c\sqrt{2\pi\cdot6}
\end{aligned}
$$

</div>

故 $c=\frac{1}{\sqrt{2\pi\cdot6}}$。由於 $c>0$，可知 $g(x)\geqslant0$ 對一切 $x\in\mathbb{R}$ 皆成立，[Proposition 2.2](#prop-pdf-existence-conditions) 的兩項條件都得到滿足，故 $g$ 確實是一個 pdf。
{: .topic-paren-cont}

(2) 由 pdf 之性質知道
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
1&=\int_{0}^{\infty}h(x)\,dx=\int_{0}^{\infty}c\cdot x^{6}e^{-3x}\,dx
=c\int_{0}^{\infty}x^{6}e^{-3x}\,dx\\[0.4em]
&=c\left(\frac{1}{3}\right)^{7}\Gamma(7)=c\left(\frac{1}{3}\right)^{7}6!
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
1&=\int_{0}^{\infty}h(x)\,dx\\[0.4em]
&=\int_{0}^{\infty}c\cdot x^{6}e^{-3x}\,dx\\[0.4em]
&=c\int_{0}^{\infty}x^{6}e^{-3x}\,dx\\[0.4em]
&=c\left(\frac{1}{3}\right)^{7}\Gamma(7)=c\left(\frac{1}{3}\right)^{7}6!
\end{aligned}
$$

</div>

故 $c=\frac{3^{7}}{6!}=\frac{243}{80}$。由於 $c>0$，可知 $h(x)\geqslant0$ 對一切 $x>0$ 皆成立，[Proposition 2.2](#prop-pdf-existence-conditions) 的兩項條件都得到滿足，故 $h$ 確實是一個 pdf。
{: .topic-paren-cont}

</div>

<div id="ex-broken-stick-beta" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.9 (Breaking a Stick at a Random Point)</div>

<div lang="en" markdown="1">
Suppose that a stick of unit length is broken at a random position $X$, and that the probability density function of $X$ is

$$
f_{\sssig X}(x)=c\,x(1-x),\quad 0<x<1
$$

Find <span class="text-nowrap">$c$.</span>
</div>

由 pdf 之性質知道

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
1&=\int_{-\infty}^{\infty}f_{\sssig X}(x)\,dx=\int_{0}^{1}c\,x(1-x)\,dx
=c\int_{0}^{1}x^{2-1}(1-x)^{2-1}\,dx\\[0.4em]
&=c\cdot\mathcal{B}(2,2)=c\,\frac{\Gamma(2)\Gamma(2)}{\Gamma(2+2)}=c\,\frac{1!\cdot1!}{3!}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
1&=\int_{-\infty}^{\infty}f_{\sssig X}(x)\,dx\\[0.4em]
&=\int_{0}^{1}c\,x(1-x)\,dx\\[0.4em]
&=c\int_{0}^{1}x^{2-1}(1-x)^{2-1}\,dx\\[0.4em]
&=c\cdot\mathcal{B}(2,2)=c\,\frac{\Gamma(2)\Gamma(2)}{\Gamma(2+2)}\\[0.4em]
&=c\,\frac{1!\cdot1!}{3!}
\end{aligned}
$$

</div>

故 $c=6$。由於 $c=6>0$，可知 $f_{\sssig X}(x)\geqslant0$ 對一切 $0<x<1$ 皆成立，[Proposition 2.2](#prop-pdf-existence-conditions) 的兩項條件都得到滿足，故 $f_{\sssig X}$ 確實是一個 pdf。

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

上述兩個問題中，分別使用到**高斯積分 (Gaussian integral)** 的變化型、**伽瑪函數 (gamma function)** 的變化型與**貝塔函數 (beta function)**，在稍後的章節，常見機率分配模型將會經常使用這些積分式。

此外，[Example 2.8](#ex-normal-gamma-constants) 中的兩個小題，事實上是常態分配 (normal distribution) 與伽瑪分配 (gamma distribution)，而 [Example 2.9](#ex-broken-stick-beta) 的則是貝塔分配 (beta distribution)，在往後的章節中，我們都會詳述這些分配。

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

伽瑪函數 (gamma function, 或稱伽瑪積分) 亦被稱作歐拉第二型積分 (Euler integral of the second kind)，與貝塔函數 (beta function)，或稱貝塔積分，亦被稱作歐拉第一型積分 (Euler integral of the first kind)；此二者與高斯積分，同為機率統計中時常使用的三個積分式。

</div>

至此，離散型的 pmf 與連續型的 pdf 都已就位，兩者又都與同一個累積分配函數相連。接下來就把這三個函數擺在一起比較，看看區間的機率如何以累積分配函數表示。

累積分配函數 $F_{\sssig X}(x)=\mathbb{P}(X\leqslant x)$、離散型的機率質量函數 $p_{\sssig X}(x)$ 與連續型的機率密度函數 $f_{\sssig X}(x)$ 都已就位。以下處理的是: 已知 $F_{\sssig X}$ 之後，各種區間的機率該怎麼算。

由於機率質量函數與機率密度函數的相似性，我們可將其性質進行比較，且與累積分配函數進行連結，從而得到一些有用的運算性質。

## 區間機率與累積分配函數

<div id="thm-interval-probability" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.3 (Interval Probabilities from a cdf)</div>

若 $X$ 為一隨機變數，且 <span class="text-nowrap">$a<b,\ a,b\in\mathbb{R}$，</span>我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(a<X\leqslant b)&=F_{\sssig X}(b)-F_{\sssig X}(a)\\[0.4em]
&=\sum_{a<x\leqslant b}p_{\sssig X}(x)\quad(\text{當 }X\text{ 為離散型隨機變數})\\[0.4em]
&=\int_{a}^{b}f_{\sssig X}(x)\,dx\quad(\text{當 }X\text{ 為連續型隨機變數})
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(a<X\leqslant b)&=F_{\sssig X}(b)-F_{\sssig X}(a)\\[0.5em]
&=\sum_{a<x\leqslant b}p_{\sssig X}(x)\\
&\quad(\text{當 }X\text{ 為離散型})\\[0.5em]
&=\int_{a}^{b}f_{\sssig X}(x)\,dx\\
&\quad(\text{當 }X\text{ 為連續型})
\end{aligned}
$$

</div>

</div>

<div class="topic-proof" markdown="1">
**Proof.** 由於 $a<b$，我們可知 $\lbrace X\leqslant a\rbrace$ 為 $\lbrace X\leqslant b\rbrace$ 的一個子集，故由[全機率定理](/teaching-topics/probability-rules-from-axioms/#theorem-total-and-addition)之特例知道

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(a<X\leqslant b)&=\mathbb{P}\bigl(\lbrace X\leqslant b\rbrace-\lbrace X\leqslant a\rbrace\bigr)\\[0.4em]
&=\mathbb{P}(X\leqslant b)-\mathbb{P}(X\leqslant a)=F_{\sssig X}(b)-F_{\sssig X}(a)\\[0.4em]
&=\sum_{a<x\leqslant b}p_{\sssig X}(x)\quad(\text{當 }X\text{ 為離散型隨機變數})\\[0.4em]
&=\int_{a}^{b}f_{\sssig X}(x)\,dx\quad(\text{當 }X\text{ 為連續型隨機變數})
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(a<X\leqslant b)\\[0.4em]
&=\mathbb{P}\bigl(\lbrace X\leqslant b\rbrace-\lbrace X\leqslant a\rbrace\bigr)\\[0.4em]
&=\mathbb{P}(X\leqslant b)-\mathbb{P}(X\leqslant a)\\[0.4em]
&=F_{\sssig X}(b)-F_{\sssig X}(a)\\[0.5em]
&=\sum_{a<x\leqslant b}p_{\sssig X}(x)\\
&\quad(\text{當 }X\text{ 為離散型})\\[0.5em]
&=\int_{a}^{b}f_{\sssig X}(x)\,dx\\
&\quad(\text{當 }X\text{ 為連續型})
\end{aligned}
$$

</div>

<span class="topic-qed">$\square$</span>
</div>

在連續型隨機變數中，上述的機率可以用下圖來理解:

<figure id="fig-interval-area" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/continuous-interval-area.svg" alt="連續型隨機變數落在 a 到 b 之間的機率由密度曲線下方區間面積表示。">
  <figcaption><span class="topic-figure__label">Fig. 2.11.</span> 區間機率 $\mathbb{P}(a<X\leqslant b)$ 就是密度曲線在 $a$ 與 $b$ 之間所圍出的面積，也就是 $F_{\sssig X}(b)-F_{\sssig X}(a)$。</figcaption>
</figure>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

在面積的運算中，任意連續函數的單點定積分恆為 $0$，因為我們可將單點積分理解為，面積的底邊為一個單點 (長度為 $0$)，因此我們能夠由此得到以下的重要性質: **連續型隨機變數的單點機率為 $0$**，即 [Theorem 2.4](#thm-point-probability-zero)。

</div>

## 連續型的單點機率與端點等號

<div id="thm-point-probability-zero" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.4 (Zero Probability at a Single Point)</div>

若 $X$ 為一連續型隨機變數，則 <span class="text-nowrap">$\forall a\in\mathbb{R}$，</span>我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X=a)=\int_{a}^{a}f_{\sssig X}(x)\,dx=F_{\sssig X}(a)-F_{\sssig X}(a)=0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X=a)&=\int_{a}^{a}f_{\sssig X}(x)\,dx\\[0.4em]
&=F_{\sssig X}(a)-F_{\sssig X}(a)=0
\end{aligned}
$$

</div>

</div>

[Theorem 2.4](#thm-point-probability-zero) 可以說是連續型隨機變數，與離散型隨機變數間最大的區別，因為離散型隨機變數本身，即是在特定的單點上具有機率，然而連續型隨機變數在特定的單點上，皆不具有機率，我們**必須要在一段範圍中積分**才有面積，也才有機率。

我們可以用下圖來理解上面的定理:

<figure id="fig-single-point-zero" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/continuous-point-zero.svg" alt="連續型隨機變數在單點 a 上沒有面積，因此單點機率為零。">
  <figcaption><span class="topic-figure__label">Fig. 2.12.</span> 單點 $a$ 沒有寬度，故密度曲線在 $a$ 到 $a$ 之間沒有面積，此即 $\mathbb{P}(X=a)=\int_{a}^{a}f_{\sssig X}(x)\,dx=0$。</figcaption>
</figure>

基於 [Theorem 2.4](#thm-point-probability-zero)，我們可以由此得到以下這個方便且重要的性質:

<div id="thm-continuous-interval-endpoints" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.5 (Interchangeable Endpoints in the Continuous Case)</div>

若 $X$ 為一連續型隨機變數，且 <span class="text-nowrap">$a<b,\ a,b\in\mathbb{R}$，</span>我們有

(1) 四種區間的機率相等，此即
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(a<X\leqslant b)=\mathbb{P}(a<X<b)=\mathbb{P}(a\leqslant X<b)=\mathbb{P}(a\leqslant X\leqslant b)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{P}(a<X\leqslant b)=\mathbb{P}(a<X<b)\\[0.4em]
=\mathbb{P}(a\leqslant X<b)=\mathbb{P}(a\leqslant X\leqslant b)
\end{gathered}
$$

</div>

(2) 分配函數亦可寫成嚴格不等式的形式，此即
{: .topic-paren-item}

$$
F_{\sssig X}(x)=\mathbb{P}(X\leqslant x)=\mathbb{P}(X<x)
$$

</div>

上述定理僅限於連續型隨機變數，離散型隨機變數並不具有這樣的性質。

與之相對，**離散型隨機變數相當講究某個單點上是否具有等號**，其原因當然是因為離散型隨機變數本身具有單點機率，故若隨意忽略單點機率則會發生嚴重的問題。

上述定理的好處在於，我們可以忽略掉端點的單點機率，而將各種區間的機率轉為 cdf 的形式，在 cdf 已知的情況下，這將會是比較簡便的做法。下面就來看一個這樣的例子。

<div id="ex-power-demand-density" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.10 (Increase in Demand for Electrical Power)</div>

<div lang="en" markdown="1">
Suppose that the increase in demand for electrical power in a particular area over the next $2$ years, in millions of kilowatt hours, is a random variable $X$ whose density is

$$
f_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{1}{64}x^{3}, & 0<x<4\\[0.6em]
0, & \text{otherwise}
\end{array}
\right.
$$

<ol class="topic-list-paren">
  <li>Show that $f_{\sssig X}$ is a valid density.</li>
  <li>Find the distribution function of <span class="text-nowrap">$X$.</span></li>
  <li>Suppose that the area is able to generate only $3$ million additional kilowatt hours. What is the probability that demand will exceed supply?</li>
</ol>
</div>

(1) <span class="text-nowrap">$f_{\sssig X}(x)\geqslant0,\ \forall\,0<x<4$，</span>且
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\int_{0}^{4}\frac{1}{64}x^{3}\,dx=\left[\frac{1}{256}x^{4}\right]_{0}^{4}=\frac{1}{256}\bigl(4^{4}-0^{4}\bigr)=1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\int_{0}^{4}\frac{1}{64}x^{3}\,dx&=\left[\frac{1}{256}x^{4}\right]_{0}^{4}\\[0.4em]
&=\frac{1}{256}\bigl(4^{4}-0^{4}\bigr)=1
\end{aligned}
$$

</div>

故 $f_{\sssig X}(x)$ 確實為一機率密度函數。
{: .topic-paren-cont}

(2) 依 [Definition 2.5](#def-pdf) 逐段積分，可得
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & x\leqslant0\\[0.6em]
\displaystyle\int_{0}^{x}\frac{1}{64}t^{3}\,dt=\frac{1}{256}x^{4}, & 0<x<4\\[0.8em]
1, & x\geqslant4
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&x\leqslant0:\quad F_{\sssig X}(x)=0\\[0.6em]
&0<x<4:\\
&\quad F_{\sssig X}(x)=\int_{0}^{x}\frac{1}{64}t^{3}\,dt=\frac{1}{256}x^{4}\\[0.6em]
&x\geqslant4:\quad F_{\sssig X}(x)=1
\end{aligned}
$$

</div>

(3) 依照題意敘述，需求超過供給的狀況即為 $3<X<4$，故所求為
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(3<X<4)&=\mathbb{P}(3<X\leqslant4)=F_{\sssig X}(4)-F_{\sssig X}(3)\\[0.4em]
&=\frac{1}{256}\bigl(4^{4}-3^{4}\bigr)\fallingdotseq0.6836
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(3<X<4)&=\mathbb{P}(3<X\leqslant4)\\[0.4em]
&=F_{\sssig X}(4)-F_{\sssig X}(3)\\[0.4em]
&=\frac{1}{256}\bigl(4^{4}-3^{4}\bigr)\\[0.4em]
&\fallingdotseq0.6836
\end{aligned}
$$

</div>

其中第一個等號用的正是 [Theorem 2.5](#thm-continuous-interval-endpoints)，把端點的等號補上並不改變機率。
{: .topic-paren-cont}

</div>

<div id="ex-cubic-cdf" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.11 (A Distribution Function on the Unit Interval)</div>

<div lang="en" markdown="1">
Let $Y$ be a continuous random variable with distribution function given by

$$
F_{\sssig Y}(y)=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & y\leqslant0\\[0.4em]
y^{3}, & 0<y<1\\[0.4em]
1, & 1\leqslant y
\end{array}
\right.
$$

<ol class="topic-list-paren">
  <li>Find the density function of <span class="text-nowrap">$Y$.</span></li>
  <li>Find <span class="text-nowrap">$\mathbb{P}\bigl(Y\geqslant\frac{1}{4}\bigr)$.</span></li>
</ol>
</div>

(1) 在可微分處取導數，可得
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig Y}(y)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{d\,F_{\sssig Y}(y)}{dy}=\dfrac{d\,y^{3}}{dy}=3y^{2}, & 0<y<1\\[0.8em]
0, & \text{elsewhere}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&0<y<1:\\
&\quad f_{\sssig Y}(y)=\frac{d\,F_{\sssig Y}(y)}{dy}=\frac{d\,y^{3}}{dy}=3y^{2}\\[0.6em]
&\text{elsewhere}:\quad f_{\sssig Y}(y)=0
\end{aligned}
$$

</div>

(2) 由 [Theorem 2.5](#thm-continuous-interval-endpoints) 可將所求轉為 cdf 的形式
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}\left(Y\geqslant\frac{1}{4}\right)&=1-\mathbb{P}\left(Y<\frac{1}{4}\right)=1-F_{\sssig Y}\left(\frac{1}{4}\right)\\[0.4em]
&=1-\left(\frac{1}{4}\right)^{3}=\frac{63}{64}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}\left(Y\geqslant\frac{1}{4}\right)&=1-\mathbb{P}\left(Y<\frac{1}{4}\right)\\[0.4em]
&=1-F_{\sssig Y}\left(\frac{1}{4}\right)\\[0.4em]
&=1-\left(\frac{1}{4}\right)^{3}=\frac{63}{64}
\end{aligned}
$$

</div>

</div>

## 離散型的機率質量函數與累積分配函數

離散型分配由於具單點機率，故其範圍的等號不可任意省略，其 pmf 與 cdf 的關聯，請見下列定理。

<div id="thm-discrete-interval-probability" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.6 (pmf and cdf in the Discrete Case)</div>

若 $X$ 為一離散型隨機變數，且 $a<b,\ a,b\in\mathbb{R}$ 為具有機率的質點，我們有

(1) 單點機率為 cdf 在該點的躍升高度，此即
{: .topic-paren-item}

$$
p_{\sssig X}(a)=F_{\sssig X}(a)-F_{\sssig X}(a^{-})
$$

(2) cdf 可拆為嚴格不等式的部分與單點機率，此即
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig X}(a)=\mathbb{P}(X\leqslant a)=\mathbb{P}(X<a)+p_{\sssig X}(a)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig X}(a)&=\mathbb{P}(X\leqslant a)\\[0.3em]
&=\mathbb{P}(X<a)+p_{\sssig X}(a)
\end{aligned}
$$

</div>

(3) 兩端都不含的區間機率為
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(a<X<b)=F_{\sssig X}(b)-F_{\sssig X}(a)-p_{\sssig X}(b)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(a<X<b)=\ &F_{\sssig X}(b)-F_{\sssig X}(a)\\
&-p_{\sssig X}(b)
\end{aligned}
$$

</div>

(4) 只含左端點的區間機率為
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(a\leqslant X<b)=F_{\sssig X}(b)-F_{\sssig X}(a)-p_{\sssig X}(b)+p_{\sssig X}(a)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(a\leqslant X<b)=\ &F_{\sssig X}(b)-F_{\sssig X}(a)\\
&-p_{\sssig X}(b)+p_{\sssig X}(a)
\end{aligned}
$$

</div>

(5) 兩端都含的區間機率為
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(a\leqslant X\leqslant b)=F_{\sssig X}(b)-F_{\sssig X}(a)+p_{\sssig X}(a)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(a\leqslant X\leqslant b)=\ &F_{\sssig X}(b)-F_{\sssig X}(a)\\
&+p_{\sssig X}(a)
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

上述定理中 (1) 的直觀意義，是「$X=a$ 的單點機率即為 $F_{\sssig X}(x)$ 在 $a$ 躍升的高度」，且由 (1) 可以相當直觀地得到 (2) 至 (5)，我們便由此將離散型隨機變數的 pmf 與其 cdf 進行連結。

</div>

<figure id="fig-cdf-jump-pmf" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/cdf-jump-pmf.svg" alt="離散型 cdf 在某一質點處的跳躍，圖中以雙向箭頭標出跳躍高度，並註明其等於該點的單點機率。">
  <figcaption><span class="topic-figure__label">Fig. 2.13.</span> 離散型 cdf 在質點 $a$ 處的躍升高度，就是該點的單點機率 <span class="text-nowrap">$p_{\sssig X}(a)=F_{\sssig X}(a)-F_{\sssig X}(a^{-})$，</span>其中 $F_{\sssig X}(a^{-})$ 為 $F_{\sssig X}$ 在 $a$ 的左極限。</figcaption>
</figure>

在點算離散型隨機變數的機率時，可以透過其已知的 cdf，來幫助我們更簡便地得到答案。下面就來看一個這樣的例子。

<div id="ex-geometric-interval-probability" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.3 (continued)</div>

<div lang="en" markdown="1">
Suppose that the probability mass function of a random variable $X$ is

$$
p_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
\left(\dfrac{1}{2}\right)^{x}, & x=1,2,\ldots\\[0.6em]
0, & \text{otherwise}
\end{array}
\right.
$$

Find <span class="text-nowrap">$\mathbb{P}(2.3\leqslant X<5)$.</span>
</div>

本篇的 [Example 2.3](#ex-geometric-cdf) 已求得 $F_{\sssig X}(x)=1-\left(\frac{1}{2}\right)^{[x]}$，$x\geqslant1$。由於 $X$ 的值域為正整數，$\lbrace2.3\leqslant X<5\rbrace$ 與 $\lbrace2<X\leqslant4\rbrace$ 是同一個事件，故由 [Theorem 2.3](#thm-interval-probability) 可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(2.3\leqslant X<5)&=\mathbb{P}(2<X\leqslant4)=F_{\sssig X}(4)-F_{\sssig X}(2)\\[0.4em]
&=\frac{1}{4}-\frac{1}{16}=0.1875
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(2.3\leqslant X<5)\\[0.4em]
&=\mathbb{P}(2<X\leqslant4)\\[0.4em]
&=F_{\sssig X}(4)-F_{\sssig X}(2)\\[0.4em]
&=\frac{1}{4}-\frac{1}{16}=0.1875
\end{aligned}
$$

</div>

</div>

<div id="ex-basketball-binomial" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.12 (Shots Made by a Basketball Player)</div>

<div lang="en" markdown="1">
Suppose that a basketball player takes $4$ shots from the field during a game, and that $X$, the number of shots this player hits, has the probability mass function

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
p_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
\binom{4}{x}\left(\dfrac{1}{4}\right)^{x}\left(\dfrac{3}{4}\right)^{4-x}, & x=0,1,2,3,4\\[0.8em]
0, & \text{otherwise}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\left\lbrace
\begin{array}{l}
p_{\sssig X}(x)=\binom{4}{x}\left(\frac{1}{4}\right)^{x}\left(\frac{3}{4}\right)^{4-x},\\[0.3em]
\qquad x=0,1,2,3,4\\[0.6em]
p_{\sssig X}(x)=0,\quad\text{otherwise}
\end{array}
\right.
$$

</div>

<ol class="topic-list-paren">
  <li>What is the probability that this player hits exactly $3$ of the shots?</li>
  <li>What is the probability that this player hits fewer than $3$ of the shots?</li>
</ol>
</div>

(1) 所求為單點機率，故
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X=3)=p_{\sssig X}(3)=\binom{4}{3}\left(\frac{1}{4}\right)^{3}\left(\frac{3}{4}\right)^{4-3}=0.046875
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X=3)&=p_{\sssig X}(3)\\[0.4em]
&=\binom{4}{3}\left(\frac{1}{4}\right)^{3}\left(\frac{3}{4}\right)^{4-3}\\[0.4em]
&=0.046875
\end{aligned}
$$

</div>

(2) 由於該變數的值域皆為整數，故
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X<3)&=\mathbb{P}(X\leqslant2)=p_{\sssig X}(0)+p_{\sssig X}(1)+p_{\sssig X}(2)\\[0.4em]
&=\sum_{x=0}^{2}\binom{4}{x}\left(\frac{1}{4}\right)^{x}\left(\frac{3}{4}\right)^{4-x}\\[0.4em]
&=\binom{4}{0}\left(\frac{1}{4}\right)^{0}\left(\frac{3}{4}\right)^{4-0}
+\binom{4}{1}\left(\frac{1}{4}\right)^{1}\left(\frac{3}{4}\right)^{4-1}\\[0.4em]
&\quad +\binom{4}{2}\left(\frac{1}{4}\right)^{2}\left(\frac{3}{4}\right)^{4-2}\\[0.4em]
&=\frac{243}{256}\fallingdotseq0.9492
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(X<3)=\mathbb{P}(X\leqslant2)\\[0.4em]
&=p_{\sssig X}(0)+p_{\sssig X}(1)+p_{\sssig X}(2)\\[0.4em]
&=\sum_{x=0}^{2}\binom{4}{x}\left(\frac{1}{4}\right)^{x}\left(\frac{3}{4}\right)^{4-x}\\[0.4em]
&=\binom{4}{0}\left(\frac{1}{4}\right)^{0}\left(\frac{3}{4}\right)^{4}\\[0.3em]
&\quad +\binom{4}{1}\left(\frac{1}{4}\right)^{1}\left(\frac{3}{4}\right)^{3}\\[0.3em]
&\quad +\binom{4}{2}\left(\frac{1}{4}\right)^{2}\left(\frac{3}{4}\right)^{2}\\[0.4em]
&=\frac{243}{256}\fallingdotseq0.9492
\end{aligned}
$$

</div>

</div>

## 本篇小結

累積分配函數以同一個式子涵蓋兩種型態，

$$
F_{\sssig X}(x)=\mathbb{P}(X\leqslant x),\ x\in\mathbb{R}
$$

它把實數線送到 $[0,1]$，非遞減、右連續，兩端的極限分別是 $0$ 與 $1$；離散型的 $F_{\sssig X}$ 是階梯函數，每一階的躍升高度就是該質點的機率。

連續型的 $F_{\sssig X}$ 則可寫成一個非負函數的積分，

$$
F_{\sssig X}(x)=\int_{-\infty}^{x}f_{\sssig X}(t)\,dt
$$

這個非負函數就是機率密度函數。它由積分定義而來，而不是由 cdf 微分定義的；由微積分基本定理可知，在可微分處有 <span class="text-nowrap">$f_{\sssig X}(x)=F^{\prime}\_{\sssig X}(x)$，</span>故 pdf 是累積機率的變化率，本身不是機率，也沒有必要小於 $1$。

有了這兩個函數，區間的機率都能以累積分配函數表示。對兩種型態都有 $\mathbb{P}(a<X\leqslant b)=F_{\sssig X}(b)-F_{\sssig X}(a)$；連續型的單點機率為 $0$，四種區間的機率因而相等，端點的等號可以互換；離散型則因單點具有正機率，等號不可任意省略，故 [Theorem 2.6](#thm-discrete-interval-probability) 逐項列出各種區間該如何加減單點機率。

下一篇[混合型隨機變數](/teaching-topics/mixed-random-variables/)處理兩種型態同時出現的情形: cdf 在某些單點上跳躍，其餘部分則連續累積，其機率函數也就同時含有單點機率與密度。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- 黃文璋，2003，《數理統計》，初版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Joseph K. Blitzstein and Jessica Hwang. 2019. *Introduction to Probability*. 2nd ed. Chapman and Hall/CRC.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Patrick Billingsley. 1995. *Probability and Measure*. 3rd ed. Wiley.
