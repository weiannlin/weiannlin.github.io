---
title: "凸性與延森不等式"
subtitle: "Convexity and Jensen’s Inequality"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 21
order: 221
permalink: /teaching-topics/ch2-p221-candidate/
date: 2026-08-06
published: false
excerpt: "凸函數的定義是: 函數在任兩點所連之弦上的值，不低於同一位置的函數值；凹函數則恰好相反。延森不等式據此比較兩個動差: 若 $g$ 為凸函數則 $\\mathbb{E}[g(X)]\\geqslant g[\\mathbb{E}(X)]$，若 $h$ 為凹函數則 $\\mathbb{E}[h(X)]\\leqslant h[\\mathbb{E}(X)]$，兩邊都是動差，不再是尾機率的上界。由它可以直接得到算術平均數不小於幾何平均數、幾何平均數不小於調和平均數，期望值與中位數的距離不超過一個標準差，以及 KL 訊息數非負這三個結果。"
---

[上一篇](/teaching-topics/ch2-p220-candidate/)介紹車諾夫不等式，以[動差母函數](/teaching-topics/ch2-p215-candidate/#def-mgf)為工具，替尾機率取得比[柴比雪夫不等式](/teaching-topics/ch2-p219-candidate/#thm-chebyshev)更緊的上界。從[馬可夫不等式](/teaching-topics/ch2-p219-candidate/#thm-markov)一路看下來，這幾篇的不等式都在做同一件事: 由少量的動差資訊出發，替一個尾機率找出上界。

本篇的延森不等式換了一個比較的對象: 它比較的是 $\mathbb{E}\bigl[g(X)\bigr]$ 與 $g\bigl[\mathbb{E}(X)\bigr]$，兩邊都是動差，不再是尾機率的上界，而決定這兩者大小的，是函數 $g$ 的凸性或凹性。以下先給出凸函數與凹函數的定義，再以圖示說明凸函數的切線落在函數下方、凹函數的切線落在函數上方；接著給出延森不等式與其證明，並說明它與「先平均再取函數值」和「先取函數值再平均」誰大誰小的關係；最後以三道例題示範它在算術幾何調和三種平均數、期望值與中位數之距離，以及 KL 訊息數非負這三個問題上的用法。

<div id="def-convex-concave" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.20 (凸函數與凹函數, convex and concave function)</div>

(1) 若實值函數 $f(\cdot)$ 的定義域為一**凸集合 (convex set)**，在單變數的情形即為一個區間，且對其定義域中任兩點 $x, y$ 及 $t\in[0,1]$ 都具有
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f\bigl(t\,x+(1-t)\,y\bigr)\leqslant t\,f(x)+(1-t)\,f(y)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&f\bigl(t\,x+(1-t)\,y\bigr)\\[0.45em]
&\quad \leqslant t\,f(x)+(1-t)\,f(y)
\end{aligned}
$$

</div>

則 $f(\cdot)$ 為一個**凸函數 <span lang="en">(convex function)</span>**。
{: .topic-paren-cont}

(2) 若實值函數 $h(\cdot)$ 的定義域為一凸集合，且對其定義域中任兩點 $x, y$ 及 $t\in[0,1]$ 都具有
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
h\bigl(t\,x+(1-t)\,y\bigr)\geqslant t\,h(x)+(1-t)\,h(y)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&h\bigl(t\,x+(1-t)\,y\bigr)\\[0.45em]
&\quad \geqslant t\,h(x)+(1-t)\,h(y)
\end{aligned}
$$

</div>

則稱 $h(\cdot)$ 為一個**凹函數 <span lang="en">(concave function)</span>**。
{: .topic-paren-cont}

</div>

所謂凸函數是指「凸向下的函數」，我們可以將其簡化理解為「凹向上」或「凸向下」的函數；而凹函數則與之相反，是指「凹向下的函數」。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

在部分中國大陸的數學教材中，函數的凸與凹和其他中文教材的凸與凹是相反的，建議讀者在閱讀中文教科書的時候，可以參考原文輔助，比較不會混淆。

</div>

上述定義中，$f(\cdot)$ 若改為對其定義域中任兩相異點 $x\neq y$ 及 $t\in(0,1)$ 都具有

$$
f\bigl(t\,x+(1-t)\,y\bigr)<t\,f(x)+(1-t)\,f(y)
$$

則 $f(\cdot)$ 稱為**嚴格凸函數 <span lang="en">(strictly convex function)</span>**。

同理，$h(\cdot)$ 若改為對其定義域中任兩相異點 $x\neq y$ 及 $t\in(0,1)$ 都具有

$$
h\bigl(t\,x+(1-t)\,y\bigr)>t\,h(x)+(1-t)\,h(y)
$$

則 $h(\cdot)$ 稱為**嚴格凹函數 <span lang="en">(strictly concave function)</span>**。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

凸函數具有一個特別的性質，即**凸函數上任一點，其切線必定在該函數下方**，而凹函數則與之相反，即**凹函數上任一點，其切線必定在該函數上方**，這兩個性質我們以 [Fig. 2.21](#fig-convexity-tangent) 的上下兩個面板理解之。

<figure id="fig-convexity-tangent" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/convexity-tangent-lines.svg" alt="上下並排的兩個面板，共用同一段橫軸範圍與同一個縱向比例尺，每個面板只畫一條橫軸，橫軸末端標為 x，沒有縱軸。上面的面板有一條開口向上的曲線，末端標為 g(x)；曲線上有一個實心點，標為 (a, g(a))，通過該點另有一條直線，標為 ℓ(x)，這條直線只在該實心點與曲線相接，其餘各處都在曲線下方。下面的面板有一條開口向下的曲線，末端標為 h(x)；曲線上有一個實心點，標為 (a, h(a))，通過該點的直線同樣標為 ℓ(x)，這條直線只在該實心點與曲線相接，其餘各處都在曲線上方。">
  <figcaption><span class="topic-figure__label">Fig. 2.21.</span> 上下兩個面板共用同一段橫軸範圍與同一個縱向比例尺。上面的面板為凸函數 <span class="text-nowrap">$g(x)=0.0784(x-2.3)^{2}+1$，</span>切點取 <span class="text-nowrap">$a=4.1$、</span><span class="text-nowrap">$g(a)=1.254016$，</span>切線 $\ell(x)=g^{\prime}(a)(x-a)+g(a)$ 的斜率為 <span class="text-nowrap">$g^{\prime}(4.1)=0.28224$，</span>整條切線都在曲線下方；下面的面板為凹函數 <span class="text-nowrap">$h(x)=2.8-0.0784(x-2.3)^{2}$，</span>切點同樣取 <span class="text-nowrap">$a=4.1$、</span><span class="text-nowrap">$h(a)=2.545984$，</span>切線 $\ell(x)=h^{\prime}(a)(x-a)+h(a)$ 的斜率為 <span class="text-nowrap">$h^{\prime}(4.1)=-0.28224$，</span>整條切線都在曲線上方。</figcaption>
</figure>

我們能夠看到，上面的面板中對 $\bigl(a, g(a)\bigr)$ 來說，通過該點的切線 $g^{\prime}(a)\bigl(x-a\bigr)+g(a)$ 是完全在函數 $g(x)$ 的下方的；而下面的面板中對 $\bigl(a, h(a)\bigr)$ 來說，通過該點的切線 $h^{\prime}(a)\bigl(x-a\bigr)+h(a)$ 完全在函數 $h(x)$ 的上方。所謂在其下方，指的意思是對所有的 $x$，$g(x)$ 都不小於其切線上同一個 $x$ 所對應的點 $g^{\prime}(a)(x-a)+g(a)$，而在其上方的意思便恰巧反過來。

</div>

凸函數與凹函數是特殊的函數，在機率不等式具有許多應用，見[下列定理](#thm-jensen)。

<div id="thm-jensen" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.36 (延森不等式, Jensen’s inequality)</div>

若 $X$ 為一隨機變數，且 $\mathbb{E}(X)$ 為有限，則有以下二個性質:

(1) 若令 $g(\cdot)$ 為一凸函數，則有
{: .topic-paren-item}

$$
\mathbb{E}\bigl[g(X)\bigr]\geqslant g\bigl[\mathbb{E}(X)\bigr]
$$

(2) 若令 $h(\cdot)$ 為一凹函數，則有
{: .topic-paren-item}

$$
\mathbb{E}\bigl[h(X)\bigr]\leqslant h\bigl[\mathbb{E}(X)\bigr]
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.**

(1) 令 $g(\cdot)$ 為一個凸函數。依 [Definition 2.20](#def-convex-concave)，$g$ 的定義域為一個區間，記為 $D$；$g(X)$ 要有定義，$X$ 必須以機率 $1$ 落在 $D$ 之內，因此 $\mathbb{E}(X)$ 只可能是 $D$ 的端點或內點。若 $\mathbb{E}(X)$ 恰為 $D$ 的端點，則 $X-\mathbb{E}(X)$ 以機率 $1$ 不改變正負號，故 $\lvert X-\mathbb{E}(X)\rvert$ 為非負隨機變數而其期望值為 $0$，對任意 $\varepsilon>0$ 由[馬可夫不等式](/teaching-topics/ch2-p219-candidate/#thm-markov)可得 $\mathbb{P}\bigl(\lvert X-\mathbb{E}(X)\rvert\geqslant\varepsilon\bigr)=0$，故 $X$ 以機率 $1$ 等於 $\mathbb{E}(X)$，不等式兩側相等；以下設 $\mathbb{E}(X)$ 落在 $D$ 的內部。
{: .topic-paren-item}

[Fig. 2.21](#fig-convexity-tangent) 畫的是可微的情形，凸函數卻未必處處可微，以下改用不要求可微的支撐直線。凸函數在其定義域的內部，每一點 $a$ 都有一條**支撐直線 <span lang="en">(supporting line)</span>**，也就是通過 $\bigl(a,\,g(a)\bigr)$ 而在整個 $D$ 上都不高於 $g$ 的直線。取通過 $\bigl(\mathbb{E}(X),\,g[\mathbb{E}(X)]\bigr)$ 的支撐直線，並記其斜率為 $s$，則有
{: .topic-paren-cont}

$$
g(X)\geqslant s\,\bigl(X-\mathbb{E}(X)\bigr)+g\bigl[\mathbb{E}(X)\bigr]
$$

其中 $g$ 於 $\mathbb{E}(X)$ 可微時 $s=g^{\prime}\bigl[\mathbb{E}(X)\bigr]$，這條支撐直線就是切線，與 [Fig. 2.21](#fig-convexity-tangent) 上面的面板所畫的同型，只是切點取在 $\mathbb{E}(X)$。兩側同取期望值 (期望值 $\mathbb{E}\bigl[g(X)\bigr]$ 必定有意義，理由見證明之後的 [Note](#note-jensen-supporting-line))，可得
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[g(X)\bigr]&\geqslant\mathbb{E}\Bigl[s\,\bigl(X-\mathbb{E}(X)\bigr)+g\bigl[\mathbb{E}(X)\bigr]\Bigr]\\[0.45em]
&=s\,\mathbb{E}\bigl[X-\mathbb{E}(X)\bigr]+g\bigl[\mathbb{E}(X)\bigr]\\[0.45em]
&=g\bigl[\mathbb{E}(X)\bigr]
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}\bigl[g(X)\bigr]\\[0.2em]
&\quad \geqslant\mathbb{E}\Bigl[s\,\bigl(X-\mathbb{E}(X)\bigr)+g\bigl[\mathbb{E}(X)\bigr]\Bigr]\\[0.45em]
&\quad =s\,\mathbb{E}\bigl[X-\mathbb{E}(X)\bigr]+g\bigl[\mathbb{E}(X)\bigr]\\[0.45em]
&\quad =g\bigl[\mathbb{E}(X)\bigr]
\end{aligned}
$$

</div>

故可知
{: .topic-paren-cont}

$$
\mathbb{E}\bigl[g(X)\bigr]\geqslant g\bigl[\mathbb{E}(X)\bigr]
$$

(2) 令 $h(\cdot)$ 為一個凹函數，其定義域同樣為一個區間 $D$，且 $X$ 以機率 $1$ 落在 $D$ 之內；$\mathbb{E}(X)$ 恰為 $D$ 的端點時同第 (1) 款，以下設它落在 $D$ 的內部。此時 $-h$ 為凸函數，故 $h$ 在 $D$ 的內部每一點也都有一條支撐直線，只是這條直線在 $D$ 上都不低於 $h$。取通過 $\bigl(\mathbb{E}(X),\,h[\mathbb{E}(X)]\bigr)$ 的支撐直線，並記其斜率為 $s$，則有
{: .topic-paren-item}

$$
h(X)\leqslant s\,\bigl(X-\mathbb{E}(X)\bigr)+h\bigl[\mathbb{E}(X)\bigr]
$$

其中 $h$ 於 $\mathbb{E}(X)$ 可微時 $s=h^{\prime}\bigl[\mathbb{E}(X)\bigr]$，這條支撐直線就是切線，與 [Fig. 2.21](#fig-convexity-tangent) 下面的面板所畫的同型，只是切點取在 $\mathbb{E}(X)$。兩側同取期望值，可得
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[h(X)\bigr]&\leqslant\mathbb{E}\Bigl[s\,\bigl(X-\mathbb{E}(X)\bigr)+h\bigl[\mathbb{E}(X)\bigr]\Bigr]\\[0.45em]
&=s\,\mathbb{E}\bigl[X-\mathbb{E}(X)\bigr]+h\bigl[\mathbb{E}(X)\bigr]\\[0.45em]
&=h\bigl[\mathbb{E}(X)\bigr]
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}\bigl[h(X)\bigr]\\[0.2em]
&\quad \leqslant\mathbb{E}\Bigl[s\,\bigl(X-\mathbb{E}(X)\bigr)+h\bigl[\mathbb{E}(X)\bigr]\Bigr]\\[0.45em]
&\quad =s\,\mathbb{E}\bigl[X-\mathbb{E}(X)\bigr]+h\bigl[\mathbb{E}(X)\bigr]\\[0.45em]
&\quad =h\bigl[\mathbb{E}(X)\bigr]
\end{aligned}
$$

</div>

故可知
{: .topic-paren-cont}

$$
\mathbb{E}\bigl[h(X)\bigr]\leqslant h\bigl[\mathbb{E}(X)\bigr]
$$

原式得證。 <span class="topic-qed">$\square$</span>
{: .topic-paren-cont}
</div>

<div id="note-jensen-supporting-line" class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

凸函數未必處處可微，例如 $g(x)=\lvert x-c\rvert$ 在 $x=c$ 便不可微，其中 $c$ 為任一常數。上述證明只用到支撐直線，沒有用到 $g$ 或 $h$ 可微，因此這一類函數也在 [Theorem 2.36](#thm-jensen) 的適用範圍之內，[Example 2.45](#ex-mean-median-distance) 用的正是這樣的一個函數。[Fig. 2.21](#fig-convexity-tangent) 與其前後的說明以可微的凸函數與凹函數為例；在不可微之處，取代切線的正是支撐直線，而且這樣的直線不只一條，任取一條即可。支撐直線的存在，可由凸函數的差商 $\frac{g(x)-g(y)}{x-y}$ 在固定 $y$ 之下對 $x$ 非遞減這個性質導出，讀者應可自行驗證，本篇不另證明。

[Theorem 2.36](#thm-jensen) 也沒有另外要求 $\mathbb{E}\bigl[g(X)\bigr]$ 存在，這是因為在定理的前提與證明中所設的條件之下，它必定有意義。前提要求 $\mathbb{E}(X)$ 為有限，否則 $g\bigl[\mathbb{E}(X)\bigr]$ 無從定義；此時 $\mathbb{E}\bigl(\lvert X\rvert\bigr)$ 亦為有限，這是[期望值](/teaching-topics/ch2-p06-candidate/#def-expectation)存在的等價條件。令 $\ell(x)=s\,\bigl(x-\mathbb{E}(X)\bigr)+g\bigl[\mathbb{E}(X)\bigr]$ 為證明中所取的支撐直線，則 $\mathbb{E}\bigl[\lvert\ell(X)\rvert\bigr]$ 為有限；又 $g(X)\geqslant\ell(X)$，故 $\max\lbrace-g(X),\,0\rbrace\leqslant\max\lbrace-\ell(X),\,0\rbrace$，也就是 $g(X)$ 取負值的那一部分，其期望值必為有限。因此 $\mathbb{E}\bigl[g(X)\bigr]$ 必定是 $(-\infty,+\infty]$ 之中一個確定的值: 若它等於 $+\infty$，不等式成為 $+\infty\geqslant g\bigl[\mathbb{E}(X)\bigr]$，自動成立，定理依然為真，只是沒有給出有用的界限。凹函數的情形對稱，$\mathbb{E}\bigl[h(X)\bigr]$ 必定是 $[-\infty,+\infty)$ 之中一個確定的值。

</div>

若參照 [Definition 2.20](#def-convex-concave)，我們可以發現，凸函數跟凹函數，事實上是在**探討一個函數的兩個點「先平均再取函數值」與「先取函數值再平均」誰大誰小**，這個直觀意義，在 $t=\frac{1}{\,2\,}$ 時特別明顯，因為當 $t$ 與 $1-t$ 都是 $\frac{1}{2}$ 時，$t\,x+(1-t)\,y=\frac{1}{\,2\,}(x+y)$，這時候便完全與前述的直觀相同，而凸 (凹) 函數的定義則指出「先平均再取函數值，比先取函數值再平均小 (大)」。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

我們再三提到，期望值事實上也是一種平均，與上述的直觀意義比較，則是將 $t\,x+(1-t)\,y$ 這個動作類比至期望值，而再與一個凸 (凹) 函數進行比較。由此來看，延森不等式確實是必然的結果。

</div>

[Fig. 2.22](#fig-jensen-convex) 的上下兩個面板便將上述的直觀化約成圖形來理解。

<figure id="fig-jensen-convex" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/jensen-inequality.svg" alt="上下並排的兩個面板，各畫一條橫軸，末端標為 x，沒有縱軸，軸上三個刻度由左至右標為 X_1、E(X) 與 X_2。上面的面板有一條開口向上的曲線，右端標為 g(x)，曲線上三個實心點由左至右標為 (X_1, g(X_1))、(E(X), g[E(X)]) 與 (X_2, g(X_2))；最左與最右兩點間的直線除兩端外都在曲線上方，直線上另有一個實心點，標為 (E(X), E[g(X)])，高於曲線上的中間那一點，兩者以一段垂直虛線相連。下面的面板結構相同，曲線開口向下、右端標為 h(x)，各點標示改用 h，直線除兩端外都在曲線下方，直線上那一點低於曲線上的中間那一點，兩者同樣以垂直虛線相連。">
  <figcaption><span class="topic-figure__label">Fig. 2.22.</span> 上下兩個面板共用同一段橫軸範圍與同一個縱向比例尺，圖示對應的是 $\mathbb{P}(X=X_1)=\mathbb{P}(X=X_2)=\frac{1}{2}$ 的兩點分配，其中 <span class="text-nowrap">$X_1=0.6$、</span><span class="text-nowrap">$X_2=7.6$，</span>故 $\mathbb{E}(X)=4.1$ 落在兩點的正中間。上面的面板為凸函數 <span class="text-nowrap">$g(x)=0.0784(x-2.3)^{2}+0.5$，</span>$\mathbb{E}[g(X)]=1.714416$ 恰為連接 $(X_1, g(X_1))$ 與 $(X_2, g(X_2))$ 之弦的中點，$g[\mathbb{E}(X)]=0.754016$ 則落在曲線上；下面的面板為凹函數 <span class="text-nowrap">$h(x)=2.8-0.0784(x-2.3)^{2}$，</span>此時弦的中點 $\mathbb{E}[h(X)]=1.585584$ 落在曲線上的 $h[\mathbb{E}(X)]=2.545984$ 之下，不等號的方向與上面的面板相反。兩個面板的落差同為 <span class="text-nowrap">$0.9604$，</span>上面的面板是 <span class="text-nowrap">$\mathbb{E}[g(X)]-g[\mathbb{E}(X)]$，</span>下面的面板是 <span class="text-nowrap">$h[\mathbb{E}(X)]-\mathbb{E}[h(X)]$，</span>都是圖中垂直虛線的長度。</figcaption>
</figure>

<div id="ex-am-gm-hm" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.44</div>

<div lang="en" markdown="1">
Suppose that $a_{1},\ldots,a_{n}$ are positive numbers whose arithmetic, geometric and harmonic means are $m_{\sssig A}$, $m_{\sssig G}$ and $m_{\sssig H}$. Using Jensen’s inequality, show that $m_{\sssig A}\geqslant m_{\sssig G}\geqslant m_{\sssig H}$.
</div>

令隨機變數 $X$ 滿足 $\mathbb{P}(X=a_i)=\frac{1}{\,n\,}$，$i=1,\ldots,n$，且令 <span class="text-nowrap">$h(x)=\ln x$，</span><span class="text-nowrap">$x>0$，</span>則 $h(x)$ 為一個凹函數，依[延森不等式](#thm-jensen)可知

$$
\mathbb{E}(\ln X)\leqslant\ln\bigl(\mathbb{E}(X)\bigr)
$$

而上式兩側分別為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl(\ln X\bigr)&=\frac{1}{\,n\,}(\ln a_1+\cdots+\ln a_n)=\ln m_{\sssig G}\\[0.45em]
\ln\bigl(\mathbb{E}(X)\bigr)&=\ln\Bigl[\frac{1}{\,n\,}\bigl(a_1+\cdots+a_n\bigr)\Bigr]=\ln m_{\sssig A}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}\bigl(\ln X\bigr)=\frac{1}{\,n\,}(\ln a_1+\cdots+\ln a_n)\\[0.2em]
&\quad =\ln m_{\sssig G}\\[0.7em]
&\ln\bigl(\mathbb{E}(X)\bigr)=\ln\Bigl[\frac{1}{\,n\,}\bigl(a_1+\cdots+a_n\bigr)\Bigr]\\[0.2em]
&\quad =\ln m_{\sssig A}
\end{aligned}
$$

</div>

故可知 $\ln m_{\sssig G}\leqslant\ln m_{\sssig A}$，即

$$
m_{\sssig A}\geqslant m_{\sssig G}
$$

此即**算幾不等式 <span lang="en">(AM-GM inequality)</span>**。又依調和平均數之定義可知

$$
\frac{1}{\,m_{\sssig H}\,}=\frac{1}{\,n\,}\sum_{i=1}^{n}\frac{1}{\,a_i\,}
$$

則由算幾不等式可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\frac{1}{\,m_{\sssig H}\,}=\frac{1}{\,n\,}\sum_{i=1}^{n}\frac{1}{\,a_i\,}\geqslant\biggl(\prod_{i=1}^{n}\frac{1}{\,a_i\,}\biggr)^{\frac{1}{\,n\,}}=\frac{1}{\,\bigl(\prod_{i=1}^{n}a_i\bigr)^{\frac{1}{\,n\,}}\,}=\frac{1}{\,m_{\sssig G}\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\frac{1}{\,m_{\sssig H}\,}&=\frac{1}{\,n\,}\sum_{i=1}^{n}\frac{1}{\,a_i\,}\\[0.45em]
&\geqslant\biggl(\prod_{i=1}^{n}\frac{1}{\,a_i\,}\biggr)^{\frac{1}{\,n\,}}\\[0.45em]
&=\frac{1}{\,\bigl(\prod_{i=1}^{n}a_i\bigr)^{\frac{1}{\,n\,}}\,}=\frac{1}{\,m_{\sssig G}\,}
\end{aligned}
$$

</div>

即 $m_{\sssig G}\geqslant m_{\sssig H}$，故合併算幾不等式可知

$$
m_{\sssig A}\geqslant m_{\sssig G}\geqslant m_{\sssig H}
$$

</div>

<div id="ex-mean-median-distance" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.45</div>

<div lang="en" markdown="1">
Suppose that $X$ is a continuous random variable whose mean, median and standard deviation are $\mu$, $m$ and $\sigma$. Show that the distance between the mean and the median is at most one standard deviation, that is, $\lvert\mu-m\rvert\leqslant\sigma$.
</div>

令 $g(x)=\lvert x-m\rvert$，$\forall x\in\mathbb{R}$，則 $g(x)$ 為一個凸函數，由[延森不等式](#thm-jensen)可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lvert\mu-m\rvert=\bigl\lvert\mathbb{E}(X)-m\bigr\rvert\leqslant\mathbb{E}\bigl[\lvert X-m\rvert\bigr]\leqslant\mathbb{E}\bigl[\lvert X-\mu\rvert\bigr]
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\lvert\mu-m\rvert&=\bigl\lvert\mathbb{E}(X)-m\bigr\rvert\\[0.45em]
&\leqslant\mathbb{E}\bigl[\lvert X-m\rvert\bigr]\\[0.45em]
&\leqslant\mathbb{E}\bigl[\lvert X-\mu\rvert\bigr]
\end{aligned}
$$

</div>

又令 $h(x)=\sqrt{x}$，$\forall x\geqslant0$，則 $h(x)$ 為一個凹函數，再次由[延森不等式](#thm-jensen)可以得到下式

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\bigl[\lvert X-\mu\rvert\bigr]=\mathbb{E}\Bigl[\sqrt{(X-\mu)^{2}}\Bigr]\leqslant\sqrt{\mathbb{E}\bigl[(X-\mu)^{2}\bigr]}=\sqrt{\sigma^{2}}=\sigma
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[\lvert X-\mu\rvert\bigr]&=\mathbb{E}\Bigl[\sqrt{(X-\mu)^{2}}\Bigr]\\[0.45em]
&\leqslant\sqrt{\mathbb{E}\bigl[(X-\mu)^{2}\bigr]}\\[0.45em]
&=\sqrt{\sigma^{2}}=\sigma
\end{aligned}
$$

</div>

故可知

$$
\lvert\mu-m\rvert\leqslant\sigma
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

讀者應該還記得，在[坎特利不等式的筆記](/teaching-topics/ch2-p219-candidate/#note-median-mean-distance)中，我們便曾提過這個性質，即一個機率分配的中位數與期望值之距離，並不會超過一個標準差；此外，這題的證明中，還使用到 [Theorem 2.17](/teaching-topics/ch2-p211-candidate/#thm-median-minimizes-absolute-deviation) 的性質，即中位數是使得 $\mathbb{E}\bigl[\lvert X-a\rvert\bigr]$ 達到最小值之 $a$ 值，是一個非常有意思的題目。

</div>

<div id="ex-kullback-leibler-nonnegative" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.46</div>

<div lang="en" markdown="1">
Suppose that $f_{0}$ and $f_{1}$ are probability density functions. The Kullback-Leibler information number is defined as

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
K(f_{0}, f_{1})=\mathbb{E}_{0}\biggl[\ln\frac{\,f_{0}(X)\,}{f_{1}(X)}\biggr]=\int_{\lbrace f_{0}>0\rbrace}\ln\frac{\,f_{0}(x)\,}{f_{1}(x)}\,f_{0}(x)\,dx
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&K(f_{0}, f_{1})=\mathbb{E}_{0}\biggl[\ln\frac{\,f_{0}(X)\,}{f_{1}(X)}\biggr]\\[0.45em]
&\quad =\int_{\lbrace f_{0}>0\rbrace}\ln\frac{\,f_{0}(x)\,}{f_{1}(x)}\,f_{0}(x)\,dx
\end{aligned}
$$

</div>

Show that $K(f_{0}, f_{1})\geqslant0$.
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

題目只說 $f_{0}$ 與 $f_{1}$ 是兩個機率密度函數，並未說明兩者取正值的範圍之間有什麼關係。上面的積分範圍寫成 $\lbrace f_{0}>0\rbrace$，是因為在 $f_{0}(x)=0$ 之處，被積函數帶有 $f_{0}(x)$ 這個為零的因子，依慣例整項取 $0$，這些位置對積分沒有貢獻。

下面的解答令 $W=\frac{\,f_{1}(X)\,}{\,f_{0}(X)\,}$，再對凸函數 $g(y)=-\ln y$ 使用 [Theorem 2.36](#thm-jensen)。依 [Definition 2.20](#def-convex-concave)，凸函數的定義域為一個區間，而 $g$ 的定義域是 $(0,\infty)$；要把定理用在 $W$ 之上，$W$ 必須以機率 $1$ 落在這個區間之內。若 $f_{1}$ 在 $\lbrace f_{0}>0\rbrace$ 之中某一塊區域上為零，而該區域在 $f_{0}$ 之下的機率為正，$W$ 便以正機率取到 $0$，$g(W)$ 在該處沒有定義，這條定理便無從引用。故以下另設在 $f_{0}(x)>0$ 之處皆有 $f_{1}(x)>0$。有了這個前提，$W>0$ 以機率 $1$ 成立，<span class="text-nowrap">$\mathbb{E}\_{0}(W)>0$，</span>$-\ln\bigl[\mathbb{E}\_{0}(W)\bigr]$ 才有定義；而 $\mathbb{E}\_{0}(W)$ 等於 $\int_{\lbrace f_{0}>0\rbrace}f_{1}(x)\,dx$，不超過 $1$，本來就為有限，正是 [Theorem 2.36](#thm-jensen) 前提所要求的期望值為有限。

要證的 $K(f_{0}, f_{1})\geqslant0$ 本身則不需要這個前提。少了它時，$\ln\frac{\,f_{0}(x)\,}{f_{1}(x)}$ 在上述那塊區域上依慣例取 $+\infty$；而被積函數取負值的那一部分，其積分必為有限: 在那一部分上 $\ln\frac{\,f_{1}(x)\,}{f_{0}(x)}$ 為正，由 $\ln t\leqslant t-1$ 可得它不超過 $\frac{\,f_{1}(x)\,}{f_{0}(x)}$，故這一部分乘上 $f_{0}(x)$ 之後的積分不超過 $\int_{\lbrace f_{0}>0\rbrace}f_{1}(x)\,dx$，也就是不超過 $1$。

$K(f_{0}, f_{1})$ 因此必定是 $(-\infty,+\infty]$ 之中一個確定的值，而在上述情形之下它等於 $+\infty$，$K(f_{0}, f_{1})\geqslant0$ 自動成立，只是沒有給出有用的資訊。這與 [Theorem 2.36](#thm-jensen) 之後那則 [Note](#note-jensen-supporting-line) 所談的是同一類情形，期望值容許取 $+\infty$ 時，不等式依然為真。補上前提不是為了讓結論成立，而是為了讓下面每一步都有定義。

</div>

令 $W=\frac{\,f_{1}(X)\,}{\,f_{0}(X)\,}$，則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
K(f_{0}, f_{1})=\mathbb{E}_{0}\biggl[\ln\frac{\,f_{0}(X)\,}{f_{1}(X)}\biggr]=\mathbb{E}_{0}\biggl(\ln\frac{1}{\,W\,}\biggr)=\mathbb{E}_{0}\bigl(-\ln W\bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&K(f_{0}, f_{1})=\mathbb{E}_{0}\biggl[\ln\frac{\,f_{0}(X)\,}{f_{1}(X)}\biggr]\\[0.45em]
&\quad =\mathbb{E}_{0}\biggl(\ln\frac{1}{\,W\,}\biggr)=\mathbb{E}_{0}\bigl(-\ln W\bigr)
\end{aligned}
$$

</div>

若令 $g(y)=-\ln y$，則 $g(y)$ 為一個凸函數，由[延森不等式](#thm-jensen)可以得到下式

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}_{0}(-\ln W)&\geqslant-\ln\bigl[\mathbb{E}_{0}(W)\bigr]=-\ln\biggl[\int_{\lbrace f_{0}>0\rbrace}\frac{\,f_{1}(x)\,}{\,f_{0}(x)\,}\,f_{0}(x)\,dx\biggr]\\[0.45em]
&=-\ln\biggl[\int_{\lbrace f_{0}>0\rbrace}f_{1}(x)\,dx\biggr]
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}_{0}(-\ln W)\geqslant-\ln\bigl[\mathbb{E}_{0}(W)\bigr]\\[0.45em]
&\quad =-\ln\biggl[\int_{\lbrace f_{0}>0\rbrace}\frac{\,f_{1}(x)\,}{\,f_{0}(x)\,}\,f_{0}(x)\,dx\biggr]\\[0.45em]
&\quad =-\ln\biggl[\int_{\lbrace f_{0}>0\rbrace}f_{1}(x)\,dx\biggr]
\end{aligned}
$$

</div>

又 $f_{1}$ 為機率密度函數，其在 $\lbrace f_{0}>0\rbrace$ 上的積分不會超過在整條實數線上的積分，即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\int_{\lbrace f_{0}>0\rbrace}f_{1}(x)\,dx\leqslant\int_{-\infty}^{\infty}f_{1}(x)\,dx=1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\int_{\lbrace f_{0}>0\rbrace}f_{1}(x)\,dx\\[0.45em]
&\quad \leqslant\int_{-\infty}^{\infty}f_{1}(x)\,dx=1
\end{aligned}
$$

</div>

而 $-\ln(\cdot)$ 為遞減函數，故可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
K(f_{0}, f_{1})=\mathbb{E}_{0}(-\ln W)\geqslant-\ln1=0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&K(f_{0}, f_{1})=\mathbb{E}_{0}(-\ln W)\\[0.45em]
&\quad \geqslant-\ln1=0
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

本題當中的 Kullback-Leibler information (KL 訊息數) 也被稱作 Kullback-Leibler divergence (KL 散度)，亦被稱作相對熵 <span lang="en">(relative entropy)</span>，在機率統計領域被用來描述 $f_{1}$ 分配相對於 $f_{0}$ 分配的訊息損失，在數理統計中，其概念有點類似於概似比檢定 <span lang="en">(likelihood ratio test, LRT)</span>。

事實上，大多數的解釋裡，KL 訊息數會用來描述兩個分配的「差異性」，然而，「差異性」一詞稍嫌不夠精準，因為 KL 訊息數對於 $f_{0}$ 與 $f_{1}$ 而言並不是對稱的，因此比較好的說法是 $f_{1}$ 分配相對於 $f_{0}$ 分配的差異；但更好的說法是訊息損失，因為 KL 訊息數原先就是用來衡量這件事情的。

實用的情境是，當現實情況的機率分配過於複雜，而我們希望使用較便於計算 (或相對簡單) 的機率模型 (即 $f_{1}$) 近似其 (即 $f_{0}$) 表現時，我們可以用 KL 訊息數來衡量這樣的近似是不是會損失太多資訊。這個問題在機器學習的神經網路模型中特別重要，因為神經網路模型的參數量十分巨大，從機率模型的觀點而言，這是一個非常巨大而複雜的模型，而我們能透過 KL 訊息數來衡量簡化過後的模型，是不是一定程度上仍具有與原模型相近的能力。

這個問題的證明，也說明了 KL 訊息數非負，亦即，使用更簡單的機率模型近似一個複雜的機率分配時，我們只可能損失訊息，而不會增加訊息。

另外，在這個證明當中，$\mathbb{E}\_{0}(\cdot)$ 指的是以 $f\_{0}$ 作為機率分配，針對其中的東西計算 (函數) 期望值；而 $f\_{0}(X)$ 與 $f\_{1}(X)$，則分別是以 $f\_{0}$ 與 $f\_{1}$ 當作一個函數 (忽略其 pdf 的意義)，將 $X$ 進行函數轉換，形成一個新的隨機變數。我們馬上就會看到，一個隨機變數的函數轉換也是隨機變數，且其機率分配是能夠被計算的。

</div>

## 本篇小結

[Definition 2.20](#def-convex-concave) 以任兩點的加權平均界定凸函數與凹函數: 在定義域這個凸集合中任取兩點 $x, y$ 與權重 $t\in[0,1]$，若 $f(t\,x+(1-t)\,y)$ 不超過 $t\,f(x)+(1-t)\,f(y)$ 則 $f$ 為凸函數，不等號反向則為凹函數；兩式各自改為嚴格不等式，並把兩點限為相異、權重限為 $t\in(0,1)$，就是嚴格凸函數與嚴格凹函數。[Fig. 2.21](#fig-convexity-tangent) 以可微的情形畫出這個定義的一個特別的性質: 凸函數上任一點的切線都在函數下方，凹函數上任一點的切線都在函數上方。

[Theorem 2.36](#thm-jensen) 的延森不等式，把上述性質由兩點的加權平均推廣到期望值: 凸函數滿足 $\mathbb{E}[g(X)]\geqslant g[\mathbb{E}(X)]$，凹函數滿足 $\mathbb{E}[h(X)]\leqslant h[\mathbb{E}(X)]$。它與前面幾篇的不等式不同之處在於，兩側比較的都是動差，而不是尾機率的上界。證明的作法是在 $(\mathbb{E}(X), g[\mathbb{E}(X)])$ 這一點取支撐直線，先把 $g(X)$ 縮小 (或放大) 為一條直線，再對整條直線取期望值，此時一次項因 $\mathbb{E}[X-\mathbb{E}(X)]=0$ 而消去，只留下常數項；證明只用到支撐直線，不要求 $g$ 可微，而 $g$ 於該點可微時，這條支撐直線就是切線。[Fig. 2.22](#fig-jensen-convex) 的上下兩個面板則以兩點分配畫出這個落差，弦的中點就是 $\mathbb{E}[g(X)]$，曲線上的點就是 $g[\mathbb{E}(X)]$。

三道例題示範了它的用法。[Example 2.44](#ex-am-gm-hm) 對取值機率均等的隨機變數用凹函數 $\ln x$，一次得到算幾不等式，再把算幾不等式用到 $\frac{1}{a_i}$ 上便補上調和平均數；[Example 2.45](#ex-mean-median-distance) 先用凸函數 $\lvert x-m\rvert$，再用凹函數 $\sqrt{x}$，兩次延森加上中位數使絕對離差期望值最小的性質，得到期望值與中位數相距不超過一個標準差；[Example 2.46](#ex-kullback-leibler-nonnegative) 令 $W=f_{1}(X)/f_{0}(X)$ 之後對凸函數 $-\ln$ 用延森，證得 KL 訊息數非負。機率不等式在只有少量動差資訊時能給出大致的機率範圍，[下一篇](/teaching-topics/ch2-p222-candidate/)轉而介紹另一種來自經驗的判斷方式，也就是經驗法則。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- R. Tyrrell Rockafellar. 1970. *Convex Analysis*. Princeton University Press.
