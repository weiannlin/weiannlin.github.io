---
title: "條件版全機率定理"
subtitle: "A Conditional Version of the Law of Total Probability"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 14
order: 314
permalink: /teaching-topics/conditional-law-of-total-probability/
date: 2026-08-13
published: false
excerpt: "雙重期望值定理是以條件變數的分配對條件期望值加權平均，得到邊際的期望值；同樣的加權方式也可以直接用在機率函數上，這就是隨機變數版本的全機率定理: 邊際 pmf 是條件 pmf 對條件變數取期望值所得的結果，邊際 pdf 亦然。它與第一章事件版本的全機率定理互相對照，當時是先以 $A_i$ 分割整個樣本空間，此處則是以條件變數 $Y$ 分割值域空間。這條定理寫成 $\\mathbb{P}(Z\\leqslant Y^{2})=\\mathbb{E}\\bigl[\\mathbb{P}(Z\\leqslant Y^{2}\\mid Y)\\bigr]$ 這種形式之後，許多機率的計算都可以先給定一部分的變數，再以該部分的分配加權求得。本篇的三道例題，第一道求一元二次方程式有實根的機率，另外兩道求一個均勻分配的變數大於另外兩個變數乘積的機率，其中最後一題說明條件的選擇完全可以依照計算的方便來決定。"
---

[上一篇](/teaching-topics/double-expectation-examples/)以五道例題示範了[雙重期望值定理](/teaching-topics/double-expectation-theorem/#thm-double-expectation)的用法，其中的共同手法是先給定一個變數、求出[條件期望值](/teaching-topics/conditional-expectation-and-variance/#def-conditional-expectation)，再以該變數的分配對條件期望值加權平均，得到邊際的期望值。

既然加權平均可以由條件期望值得到邊際期望值，同樣的做法能不能直接用在分配本身上呢？本篇的定理給出肯定的回答，邊際的 pmf 與 pdf 都可以寫成條件 pmf 與條件 pdf 的期望值，這就是[隨機變數](/teaching-topics/random-variables-and-pmf/#def-random-variable)版本的全機率定理。本篇先給出這條定理與它的證明，說明它與第一章事件版本的全機率定理如何對照，再以三道例題示範它在機率計算上的用法，並說明條件的選擇可以依照計算的方便來決定。

## 隨機變數版本的全機率定理

<div id="thm-law-of-total-prob-r-v" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 3.10 (全機率定理, the law of total probability)</div>

若 $X$ 與 $Y$ 之條件 pmf 為 $p_{\sssig X\mid Y}(x\mid y)$ 與 <span class="text-nowrap">$p_{\sssig Y\mid X}(y\mid x)$，</span>邊際 pmf 為 $p_{\sssig X}(x)$ 與 $p_{\sssig Y}(y)$ 則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
p_{\sssig X}(x)=\mathbb{E}\Bigl[p_{\sssig X\mid Y}(x\mid Y)\Bigr]\quad\text{及}\quad p_{\sssig Y}(y)=\mathbb{E}\Bigl[p_{\sssig Y\mid X}(y\mid X)\Bigr]
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
p_{\sssig X}(x)=\mathbb{E}\Bigl[p_{\sssig X\mid Y}(x\mid Y)\Bigr]\\[0.55em]
\text{及}\quad p_{\sssig Y}(y)=\mathbb{E}\Bigl[p_{\sssig Y\mid X}(y\mid X)\Bigr]
\end{gathered}
$$

</div>

若 $X$ 與 $Y$ 之 conditional pdf 為 $f_{\sssig X\mid Y}(x\mid y)$ 與 <span class="text-nowrap">$f_{\sssig Y\mid X}(y\mid x)$，</span>邊際 pdf 為 $f_{\sssig X}(x)$ 與 $f_{\sssig Y}(y)$ 則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X}(x)=\mathbb{E}\Bigl[f_{\sssig X\mid Y}(x\mid Y)\Bigr]\quad\text{及}\quad f_{\sssig Y}(y)=\mathbb{E}\Bigl[f_{\sssig Y\mid X}(y\mid X)\Bigr]
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
f_{\sssig X}(x)=\mathbb{E}\Bigl[f_{\sssig X\mid Y}(x\mid Y)\Bigr]\\[0.55em]
\text{及}\quad f_{\sssig Y}(y)=\mathbb{E}\Bigl[f_{\sssig Y\mid X}(y\mid X)\Bigr]
\end{gathered}
$$

</div>

</div>

<div class="topic-proof" markdown="1">
**Proof.**

我們僅以連續型證明 $X$ 邊際的狀況，其餘狀況同理可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\Bigl[f_{\sssig X\mid Y}(x\mid Y)\Bigr]&=\int_{y\in\mathcal{R}_{\sssig Y}}\biggl[f_{\sssig X\mid Y}(x\mid y)\biggr]\,f_{\sssig Y}(y)\,dy\\[0.45em]
&=\int_{y\in\mathcal{R}_{\sssig Y}}f_{\sssig XY}(x,y)\,dy=f_{\sssig X}(x)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}\Bigl[f_{\sssig X\mid Y}(x\mid Y)\Bigr]\\[0.45em]
&\quad =\int_{y\in\mathcal{R}_{\sssig Y}}\biggl[f_{\sssig X\mid Y}(x\mid y)\biggr]\,f_{\sssig Y}(y)\,dy\\[0.45em]
&\quad =\int_{y\in\mathcal{R}_{\sssig Y}}f_{\sssig XY}(x,y)\,dy=f_{\sssig X}(x)
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

上述全機率定理，與第一章 [Theorem 1.16](/teaching-topics/total-probability-bayes-rule/#theorem-law-of-total-probability) 所敘述的全機率定理的連結是，當時 $\mathbb{P}(B\mid A_i)$ 是以 $\mathbb{P}(A_i)$ 為權重進行加權，從而得到 <span class="text-nowrap">$\mathbb{P}(B)$；</span>而此處，$f_{\sssig X\mid Y}(x\mid y)$ 則是以 $f_{\sssig Y}(y)$ 為權重進行加權，從而得到 <span class="text-nowrap">$f_{\sssig X}(x)$。</span>

此二者的相像之處在於，事件版本的全機率定理，是以 $A_i$ 先行分割整個樣本空間；而隨機變數版本的全機率定理，是以條件變數 $Y$ 分割值域空間。

</div>

## 全機率定理在機率計算上的應用

<div id="ex-quadratic-real-root-probability" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.26</div>

<div lang="en" markdown="1">
Suppose that $Y$ and $Z$ are two independent random variables sharing a common distribution, namely the standard uniform distribution <span class="text-nowrap">$\mathcal{U}(0,1)$.</span> What is the probability that the quadratic equation $x^{2}+2xY+Z=0$ has a real root?
</div>

$x^{2}+2xY+Z=0$ 有實根表示 <span class="text-nowrap">$(2Y)^{2}-4\times 1\times Z\geqslant 0$，</span>則所求為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}\bigl(Z\leqslant Y^{2}\bigr)&=\int_{0}^{1}\mathbb{P}\bigl(Z\leqslant Y^{2}\bigm\vert Y=y\bigr)\,f_{\sssig Y}(y)\,dy\\[0.45em]
&=\int_{0}^{1}\mathbb{P}\bigl(Z\leqslant y^{2}\bigm\vert Y=y\bigr)\,f_{\sssig Y}(y)\,dy\\[0.45em]
&=\int_{0}^{1}\biggl[\int_{0}^{y^{2}}1\,dz\biggr]\times 1\,dy=\int_{0}^{1}y^{2}\,dy=\frac{1}{\,3\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}\bigl(Z\leqslant Y^{2}\bigr)\\[0.45em]
&\quad =\int_{0}^{1}\mathbb{P}\bigl(Z\leqslant Y^{2}\bigm\vert Y=y\bigr)\,f_{\sssig Y}(y)\,dy\\[0.45em]
&\quad =\int_{0}^{1}\mathbb{P}\bigl(Z\leqslant y^{2}\bigm\vert Y=y\bigr)\,f_{\sssig Y}(y)\,dy\\[0.45em]
&\quad =\int_{0}^{1}\biggl[\int_{0}^{y^{2}}1\,dz\biggr]\times 1\,dy\\[0.45em]
&\quad =\int_{0}^{1}y^{2}\,dy=\frac{1}{\,3\,}
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

事實上，上述的做法也可以寫成 $\mathbb{P}\bigl(Z\leqslant Y^{2}\bigr)$ $=$ <span class="text-nowrap">$\mathbb{E}\bigl[\mathbb{P}(Z\leqslant Y^{2}\mid Y)\bigr]$，</span>而這正是全機率定理的應用，甚至可以說，這才是真正的全「機率」定理。

</div>

<div id="ex-three-uniform-comparison" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.27</div>

<div lang="en" markdown="1">
Suppose that <span class="text-nowrap">$X$,</span> $Y$ and $Z$ are independent random variables, each of which is uniformly distributed over the interval <span class="text-nowrap">$(0,1)$.</span> Evaluate <span class="text-nowrap">$\mathbb{P}(X\geqslant YZ)$.</span>
</div>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X\geqslant YZ)&=\mathbb{E}\bigl[\mathbb{P}(X\geqslant YZ\mid Y,Z)\bigr]\\[0.45em]
&=\int_{0}^{1}\int_{0}^{1}\mathbb{P}(X\geqslant YZ\mid Y=y,Z=z)\,f_{\sssig YZ}(y,z)\,dy\,dz\\[0.45em]
&=\int_{0}^{1}\int_{0}^{1}\mathbb{P}(X\geqslant yz)\,f_{\sssig YZ}(y,z)\,dy\,dz\\[0.45em]
&=\int_{0}^{1}\int_{0}^{1}\biggl[\int_{yz}^{1}f_{\sssig X\mid YZ}(x\mid y,z)\,dx\biggr]\,f_{\sssig YZ}(y,z)\,dy\,dz\\[0.45em]
&=\int_{0}^{1}\int_{0}^{1}\biggl[\int_{yz}^{1}1\,dx\biggr]\,f_{\sssig YZ}(y,z)\,dy\,dz\\[0.45em]
&=\int_{0}^{1}\int_{0}^{1}(1-yz)\,dy\,dz=\int_{0}^{1}\Bigl(1-\frac{1}{2}z\Bigr)\,dz=\frac{3}{\,4\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(X\geqslant YZ)\\[0.45em]
&\quad =\mathbb{E}\bigl[\mathbb{P}(X\geqslant YZ\mid Y,Z)\bigr]\\[0.45em]
&\quad =\int_{0}^{1}\int_{0}^{1}\mathbb{P}(X\geqslant YZ\mid Y=y,Z=z)\\[0.2em]
&\qquad\quad f_{\sssig YZ}(y,z)\,dy\,dz\\[0.45em]
&\quad =\int_{0}^{1}\int_{0}^{1}\mathbb{P}(X\geqslant yz)\,f_{\sssig YZ}(y,z)\,dy\,dz\\[0.45em]
&\quad =\int_{0}^{1}\int_{0}^{1}\biggl[\int_{yz}^{1}f_{\sssig X\mid YZ}(x\mid y,z)\,dx\biggr]\\[0.2em]
&\qquad\quad f_{\sssig YZ}(y,z)\,dy\,dz\\[0.45em]
&\quad =\int_{0}^{1}\int_{0}^{1}\biggl[\int_{yz}^{1}1\,dx\biggr]\,f_{\sssig YZ}(y,z)\,dy\,dz\\[0.45em]
&\quad =\int_{0}^{1}\int_{0}^{1}(1-yz)\,dy\,dz\\[0.45em]
&\quad =\int_{0}^{1}\Bigl(1-\frac{1}{2}z\Bigr)\,dz=\frac{3}{\,4\,}
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

上述的過程有兩個重點，其一是，條件可以擺上多於一個的變數，只是要注意的是，其條件分配的分母，是 $Y$ 與 $Z$ 的聯合分配，因為它們是「一起被給定」的，所以外層期望值的計算自然地會使用聯合分配。

第二個重點是，讀者可能在本章稍早計算機率的過程中，採用直接計算的方式計算類似本題的機率，亦即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X\geqslant YZ)=\int_{0}^{1}\int_{0}^{1}\int_{yz}^{1}f_{\sssig XYZ}(x,y,z)\,dx\,dy\,dz
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(X\geqslant YZ)\\[0.45em]
&\quad =\int_{0}^{1}\int_{0}^{1}\int_{yz}^{1}f_{\sssig XYZ}(x,y,z)\,dx\,dy\,dz
\end{aligned}
$$

</div>

事實上，這個算法與全機率定理是等價的，微小的差別在於，過去我們是先行得知 joint pdf <span class="text-nowrap">$f_{\sssig XYZ}(x,y,z)$，</span>從而計算機率 (當然，獨立的情況是很容易知道 joint pdf 的)，而有些情況則是比較容易知道 conditional pdf，此時則是使用全機率定理較為方便；而此處則更為特別，因為三個變數都是獨立的，所以 conditional pdf $f_{\sssig X\mid YZ}(x\mid y,z)$ 就是 <span class="text-nowrap">$f_{\sssig X}(x)$。</span>

</div>

<div id="ex-three-uniform-product-inequality" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.28</div>

<div lang="en" markdown="1">
Suppose that <span class="text-nowrap">$X$,</span> $Y$ and $Z$ are continuous random variables that are independent and identically distributed, their common distribution being the uniform distribution over <span class="text-nowrap">$(0,1)$.</span> Find <span class="text-nowrap">$\mathbb{P}(X\geqslant 3YZ)$.</span>
</div>

所求為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\bigl[\mathbb{P}(X\geqslant 3YZ\mid Z)\bigr]=\int_{0}^{1}\mathbb{P}(X\geqslant 3YZ\mid Z=z)\,f_{\sssig Z}(z)\,dz
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}\bigl[\mathbb{P}(X\geqslant 3YZ\mid Z)\bigr]\\[0.45em]
&\quad =\int_{0}^{1}\mathbb{P}(X\geqslant 3YZ\mid Z=z)\,f_{\sssig Z}(z)\,dz
\end{aligned}
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\text{又}\ \ \mathbb{P}(X\geqslant 3YZ\mid Z=z)&=\mathbb{P}(X\geqslant 3Yz\mid Z=z)=\mathbb{P}(X\geqslant 3Yz)\\[0.45em]
&=\left\lbrace
\begin{array}{c@{\quad}l}
1-\frac{3}{\,2\,}z, & 0<z\leqslant\frac{1}{\,3\,}\\[0.8em]
\frac{1}{\,6z\,}, & \frac{1}{\,3\,}<z<1
\end{array}
\right.
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\text{又}\ \ \mathbb{P}(X\geqslant 3YZ\mid Z=z)\\[0.45em]
&\quad =\mathbb{P}(X\geqslant 3Yz\mid Z=z)\\[0.45em]
&\quad =\mathbb{P}(X\geqslant 3Yz)\\[0.45em]
&\quad =\left\lbrace
\begin{array}{c@{\quad}l}
1-\frac{3}{\,2\,}z, & 0<z\leqslant\frac{1}{\,3\,}\\[0.8em]
\frac{1}{\,6z\,}, & \frac{1}{\,3\,}<z<1
\end{array}
\right.
\end{aligned}
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\text{故}\ \ \mathbb{P}(X\geqslant 3YZ)&=\mathbb{E}\bigl[\mathbb{P}(X\geqslant 3YZ\mid Z)\bigr]\\[0.45em]
&=\int_{0}^{\frac{1}{3}}\Bigl(1-\frac{3}{\,2\,}z\Bigr)\,dz+\int_{\frac{1}{3}}^{1}\frac{1}{\,6z\,}\,dz=\frac{1}{\,4\,}+\frac{1}{\,6\,}\ln 3
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\text{故}\ \ \mathbb{P}(X\geqslant 3YZ)\\[0.45em]
&\quad =\mathbb{E}\bigl[\mathbb{P}(X\geqslant 3YZ\mid Z)\bigr]\\[0.45em]
&\quad =\int_{0}^{\frac{1}{3}}\Bigl(1-\frac{3}{\,2\,}z\Bigr)\,dz+\int_{\frac{1}{3}}^{1}\frac{1}{\,6z\,}\,dz\\[0.45em]
&\quad =\frac{1}{\,4\,}+\frac{1}{\,6\,}\ln 3
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

讀者當然可以像[上一題](#ex-three-uniform-comparison)一樣，將 $Y, Z$ 都給定，再來計算機率，但由於此處多了三倍的緣故，因此範圍變得需要討論，同時給定 $Y, Z$ 反而會變得比較難計算，因此此處只給定其一來討論。

此外，在給定 $Z=z$ 的情況下，依照 $z$ 的範圍，積分範圍將有以下兩種:

<!-- fig-pending: total-probability-regions
     Fig. 3.17，對應書稿 mathstatch3.tex 第 2603 至 2641 行 (左面板) 與第 2645 至 2685 行
     (右面板) 的兩個 tikzpicture。兩者同在第 2601 至 2687 行的 center 之內，各放在一個
     .45\textwidth 的 minipage 裡並排；網頁併為一張兩面板的圖 (桌面左右並排，手機改為
     上下排列)，此即 CH3_FIGURE_SPECS.md 第二節所定的「兩面板」區域圖。

     兩面板共通的部分:
       座標軸為兩條帶箭頭的直線，橫軸自原點畫到 (3.2, 0)、縱軸自原點畫到 (0, 3.2)，
       兩軸都沒有刻度也沒有數值。橫軸右端外側標 $x$ (書稿放在 (3.5, 0.15) 的下方)，
       縱軸上端標 $y$ (書稿放在 (0, 3.8) 的下方)。
       兩條輔助虛線: 一條自 (3, 3) 畫到 (3, 0)，下端標 $x=1$；一條自 (3, 3) 畫到 (0, 3)，
       左端標 $y=1$。也就是圖上的 (3, 3) 就是單位正方形的右上角。
       填色書稿用 gray、opacity 0.2，網頁改 journalaccent、透明度 0.15。

     左面板 ($0<z\leqslant\frac{1}{3}$ 的情形):
       一條實線自原點沿 $y=2x$ 畫到 (1.6, 3.2)，在 (1.6, 3.1) 的上方標 $x=3zy$。
       填色區域為 (0, 0)、(1.5, 3)、(3, 3)、(3, 0) 四點所圍的四邊形，
       即單位正方形之中 $x\geqslant 3zy$ 的部分；此時直線與正方形的上邊相交。
       面板下方在 (1.6, -0.5) 標 $0<z\leqslant\frac{1}{\,3\,}$。

     右面板 ($\frac{1}{3}<z<1$ 的情形):
       一條實線自原點沿 $y=0.5x$ 畫到 (3.1, 1.55)，在 (3.1, 1.6) 的右側標 $x=3zy$。
       填色區域為 (0, 0)、(3, 1.5)、(3, 0) 三點所圍的三角形，
       即單位正方形之中 $x\geqslant 3zy$ 的部分；此時直線與正方形的右邊相交。
       面板下方在 (1.6, -0.5) 標 $\frac{1}{\,3\,}<z<1$。

     繪圖時要裁定的一點: 兩面板的實線都畫到略微超出兩條虛線所界定的單位正方形
     (左面板到 (1.6, 3.2)、右面板到 (3.1, 1.55) 之後還有標示)，可比照 Fig. 3.1 的
     既有處置把線收在單位正方形之內，屬圖形類的刻意改正，若採用須併入勘誤登錄。

     檔名 total-probability-regions.svg，anchor 取 #fig-total-probability-regions。
     圖畫好之後，本段的「以下兩種」改為指向該 anchor 的 Fig. 3.17 連結，並補上 caption。
-->

並利用 $X$ 與 $Y$ 是獨立均勻分配的特色，將機率的計算轉化為面積的計算。

讀者應該可以發現，全機率定理的應用非常廣泛，特別是在條件的選擇上，完全可以依照計算上的方便來進行選擇，是很靈活的定理。

</div>

## 本篇小結

[Theorem 3.10](#thm-law-of-total-prob-r-v) 把加權平均的做法由期望值移到機率函數本身。邊際 pmf 是條件 pmf 以條件變數的分配加權所得，即 $p_{\sssig X}(x)$ $=$ $\mathbb{E}\bigl[p_{\sssig X\mid Y}(x\mid Y)\bigr]$ 這一條等式，連續型的邊際 pdf 亦然。證明只需把外層的期望值寫成對 $y$ 的積分，被積分的兩項相乘正是 <span class="text-nowrap">$f_{\sssig XY}(x,y)$，</span>再對 $y$ 積分就得到 <span class="text-nowrap">$f_{\sssig X}(x)$。</span>這條定理與第一章 [Theorem 1.16](/teaching-topics/total-probability-bayes-rule/#theorem-law-of-total-probability) 的對照相當清楚: 當時是以 $A_i$ 先行分割整個樣本空間、以 $\mathbb{P}(A_i)$ 為權重，此處則是以條件變數 $Y$ 分割值域空間、以 $f_{\sssig Y}(y)$ 為權重。

三道例題示範這條定理在機率計算上的用法。[Example 3.26](#ex-quadratic-real-root-probability) 先把「有實根」化為判別式非負的條件，所求機率因而是 <span class="text-nowrap">$\mathbb{P}(Z\leqslant Y^{2})$，</span>給定 $Y=y$ 之後再對 $y$ 加權積分，得到 <span class="text-nowrap">$\frac{1}{3}$；</span>這個做法寫成 $\mathbb{E}\bigl[\mathbb{P}(Z\leqslant Y^{2}\mid Y)\bigr]$ 之後，就是全機率定理本身。[Example 3.27](#ex-three-uniform-comparison) 說明條件可以同時擺上多於一個的變數，此時外層的期望值使用的是 $Y$ 與 $Z$ 的聯合分配，答案為 <span class="text-nowrap">$\frac{3}{4}$；</span>這個算法與直接以三重積分計算是等價的，差別只在先知道的是 joint pdf 還是 conditional pdf。

[Example 3.28](#ex-three-uniform-product-inequality) 的三倍使積分範圍需要分段討論，若把 $Y$ 與 $Z$ 都給定反而更難算，因此只給定 <span class="text-nowrap">$Z$，</span>並依 $z$ 落在 $0<z\leqslant\frac{1}{3}$ 或 $\frac{1}{3}<z<1$ 分成兩種範圍，各以面積求得條件機率，最後加權積分得到 $\frac{1}{4}+\frac{1}{6}\ln 3$ 這個值。由此可見全機率定理在條件的選擇上相當靈活，完全可以依照計算上的方便來決定。

[下一篇](/teaching-topics/variance-decomposition-theorem/)將把同樣的加權做法用在[變異數](/teaching-topics/variance/#def-variance)上，介紹變異數分解定理。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
