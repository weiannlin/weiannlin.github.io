---
title: "機率收斂"
subtitle: "Convergence in Probability"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 5
topic: 3
order: 503
permalink: /lecture-notes/convergence-in-probability/
date: 2026-08-15
published: true
excerpt: "機率收斂要求隨機變數序列 $X_n$ 與 $X$ 偏離超過任意正數 $\\varepsilon$ 的機率隨 $n\\to\\infty$ 趨於零。本篇證明機率收斂必導致分配收斂而反之不成立，並證明當極限對象為常數時兩種收斂互為充要條件。"
---

[上一篇](/lecture-notes/levy-continuity-theorem/)以列維連續性定理把[分配收斂](/lecture-notes/convergence-in-distribution/#def-converge-in-distribution)的判定改由動差母函數的極限來處理，五道例題都不必先求出極限 cdf。本篇接下來轉入機率收斂這種收斂型態。

這兩種收斂型態關心的不是同一件事情。分配收斂比較的是兩個 cdf，只要極限 cdf 與收斂對象的 cdf 在連續點上相等即可，兩個[隨機變數](/lecture-notes/random-variables-and-pmf/#def-random-variable)的取值可以毫不相干；機率收斂比較的則是取值本身，它要求 $X_n$ 與 $X$ 的隨機變數值任意地接近。本篇先給出機率收斂的定義與它的直觀，再給出兩條把這兩種收斂型態接起來的定理，一條說機率收斂必然導致分配收斂而反之不然，另一條說收斂對象若是一個常數，兩者反而等價。最後以三道例題示範這兩條定理怎麼用來求機率極限。

## 機率收斂的定義

<div id="def-converge-in-probability" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 5.2 (機率收斂, converge in probability)</div>

令 $\lbrace X_n\rbrace_{n=1}^{\infty}$ 為一定義在[機率空間](/lecture-notes/event-families-sigma-fields/#definition-probability-space)上之隨機變數序列，若 $X$ 為定義在相同機率空間中之隨機變數，且滿足

$$
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_n-X\rvert<\varepsilon\bigr)=1,\ \forall\,\varepsilon>0
$$

則稱 $X_n$ 機率收斂至 <span class="text-nowrap">$X$，</span>記為 <span class="text-nowrap">$X_n\pconv X$，</span>也可記為 $\underset{n\to\infty}{\mathrm{plim}}\,X_n=X$ 這個式子，此時 $X$ 稱為 $X_n$ 的**機率極限 <span lang="en">(probability limit)</span>**。

</div>

不同於分配收斂僅比較機率分配，機率收斂直接衡量隨機變數取值之間的距離，要求當 $n\to\infty$ 時，$X_n$ 與 $X$ 的取值落在任意微小誤差範圍內的機率趨近於 <span class="text-nowrap">$1$。</span>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

定義中之所以要求收斂對象 $X$ 與序列 $\lbrace X_n\rbrace_{n=1}^{\infty}$ 定義在同一個機率空間上，是因為必須對同一個樣本點 $\omega\in S$ 計算差值 <span class="text-nowrap">$X_n(\omega)-X(\omega)$，</span>事件 $\lbrace\omega\in S\mid\lvert X_n(\omega)-X(\omega)\rvert<\varepsilon\rbrace$ 方有明確定義。此外，對任意給定的正數 <span class="text-nowrap">$\varepsilon>0$，</span>機率收斂僅要求該事件發生的機率在 $n\to\infty$ 時趨於 <span class="text-nowrap">$1$，</span>並非要求對所有樣本點皆必然成立 (一如前文所述，機率為 $1$ 的事件未必必然發生，機率為 $0$ 的事件亦未必不可能發生)。

</div>

## 機率收斂與分配收斂的強弱關係

既然機率收斂規範的是隨機變數取值本身的接近程度，而分配收斂僅比較 cdf，兩者之間便有明確的強弱蘊含關係，見下列定理。

<div id="thm-pconv-implies-dconv" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 5.2 (機率收斂導致分配收斂)</div>

若 <span class="text-nowrap">$X_n\pconv X$，</span>則有

$$
X_n\dconv X
$$

反之未必成立。

</div>

<div class="topic-proof" markdown="1">
**Proof.**

令 $x$ 為 $F_{\sssig X}$ 的任一個連續點，取任意的 <span class="text-nowrap">$\varepsilon>0$，</span>並令

$$
A_n=\lbrace\lvert X_n-X\rvert<\varepsilon\rbrace
$$

則由 $X_n\pconv X$ 可知

$$
\lim_{n\to\infty}\mathbb{P}(A_n)=1,\quad\lim_{n\to\infty}\mathbb{P}(A_n^{\prime})=0
$$

接著把事件 $\lbrace X_n\leqslant x\rbrace$ 依 $A_n$ 發生與否切成兩塊，由 [Theorem 1.6](/lecture-notes/probability-rules-from-axioms/#theorem-total-and-addition) 可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig X_n}(x)=\mathbb{P}\bigl(\lbrace X_n\leqslant x\rbrace\cap A_n\bigr)+\mathbb{P}\bigl(\lbrace X_n\leqslant x\rbrace\cap A_n^{\prime}\bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig X_n}(x)&=\mathbb{P}\bigl(\lbrace X_n\leqslant x\rbrace\cap A_n\bigr)\\[0.45em]
&\qquad+\mathbb{P}\bigl(\lbrace X_n\leqslant x\rbrace\cap A_n^{\prime}\bigr)
\end{aligned}
$$

</div>

其中第一塊之內同時有 $X_n\leqslant x$ 與 $X<X_n+\varepsilon$ 這兩個不等式，故該塊落在 $\lbrace X\leqslant x+\varepsilon\rbrace$ 之內；第二塊則整個落在 $A_n^{\prime}$ 之內。故由 [Theorem 1.7](/lecture-notes/probability-rules-from-axioms/#theorem-monotonicity) 的單調性可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig X_n}(x)\leqslant\mathbb{P}(X\leqslant x+\varepsilon)+\mathbb{P}(A_n^{\prime})=F_{\sssig X}(x+\varepsilon)+\mathbb{P}(A_n^{\prime})
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig X_n}(x)&\leqslant\mathbb{P}(X\leqslant x+\varepsilon)+\mathbb{P}(A_n^{\prime})\\[0.45em]
&=F_{\sssig X}(x+\varepsilon)+\mathbb{P}(A_n^{\prime})
\end{aligned}
$$

</div>

同樣的作法用在 $\lbrace X\leqslant x-\varepsilon\rbrace$ 上。此時第一塊之內同時有 $X\leqslant x-\varepsilon$ 與 $X_n<X+\varepsilon$ 這兩個不等式，故該塊落在 $\lbrace X_n\leqslant x\rbrace$ 之內，同理亦可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig X}(x-\varepsilon)\leqslant\mathbb{P}(X_n\leqslant x)+\mathbb{P}(A_n^{\prime})=F_{\sssig X_n}(x)+\mathbb{P}(A_n^{\prime})
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig X}(x-\varepsilon)&\leqslant\mathbb{P}(X_n\leqslant x)+\mathbb{P}(A_n^{\prime})\\[0.45em]
&=F_{\sssig X_n}(x)+\mathbb{P}(A_n^{\prime})
\end{aligned}
$$

</div>

把兩式併起來，對每一個 $n$ 皆有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig X}(x-\varepsilon)-\mathbb{P}(A_n^{\prime})\leqslant F_{\sssig X_n}(x)\leqslant F_{\sssig X}(x+\varepsilon)+\mathbb{P}(A_n^{\prime})
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig X}(x-\varepsilon)-\mathbb{P}(A_n^{\prime})&\leqslant F_{\sssig X_n}(x)\\[0.45em]
&\leqslant F_{\sssig X}(x+\varepsilon)+\mathbb{P}(A_n^{\prime})
\end{aligned}
$$

</div>

最後說明左右兩側都可以任意接近 $F_{\sssig X}(x)$ 這個值。任取 <span class="text-nowrap">$\eta>0$，</span>由於 $x$ 是 $F_{\sssig X}$ 的連續點，可取一個夠小的 <span class="text-nowrap">$\varepsilon>0$，</span>使得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig X}(x+\varepsilon)-F_{\sssig X}(x)<\frac{\eta}{\,2\,},\quad F_{\sssig X}(x)-F_{\sssig X}(x-\varepsilon)<\frac{\eta}{\,2\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
F_{\sssig X}(x+\varepsilon)-F_{\sssig X}(x)<\frac{\eta}{\,2\,},\\[0.45em]
F_{\sssig X}(x)-F_{\sssig X}(x-\varepsilon)<\frac{\eta}{\,2\,}
\end{gathered}
$$

</div>

又由 $\mathbb{P}(A_n^{\prime})\to0$ 這個結果，可取一個夠大的 <span class="text-nowrap">$N$，</span>使得 $n\geqslant N$ 時 $\mathbb{P}(A_n^{\prime})<\frac{\eta}{\,2\,}$ 這個不等式成立。把這兩件事代回上式可知，$n\geqslant N$ 時

$$
F_{\sssig X}(x)-\eta<F_{\sssig X_n}(x)<F_{\sssig X}(x)+\eta
$$

由於 $\eta>0$ 可以任意小，故

$$
\lim_{n\to\infty}F_{\sssig X_n}(x)=F_{\sssig X}(x),\ \forall\,x\in C(F_{\sssig X})
$$

此即

$$
X_n\dconv X
$$

至於反向的敘述並不成立，[Example 5.11](#ex-dconv-without-pconv) 即給出一個分配收斂而不機率收斂的序列。原式得證。 <span class="topic-qed">$\square$</span>
</div>

本證明的作法取自 Hogg, McKean and Craig (2019) 第 332 頁，Chung (2001) 第 96 至 97 頁另有一套證明。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

直觀而言，若當 $n\to\infty$ 時 $X_n$ 與 $X$ 任意接近的機率趨於 <span class="text-nowrap">$1$，</span>兩者的取值行為在極限下幾乎一致，其對應的機率分配自然也會趨於相同。反之則不然；兩個隨機變數即便服從完全相同的機率分配 (從而具有相同的 cdf)，各自的實際取值仍可能毫無關聯。例如一組獨立同分配的隨機樣本，各觀測值雖有相同的邊際分配，彼此的實現值卻未必相等或接近，故分配收斂不足以保證機率收斂。

</div>

<div id="ex-dconv-without-pconv" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.11</div>

<div lang="en" markdown="1">
For each <span class="text-nowrap">$n=1,2,\ldots$,</span> let the joint pmf of $(X_n,X)$ be

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
p_{\sssig X_nX}(x_n,x)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{1}{\,3\,}, & (x_n,x)=(1,2),(2,3),(3,1)\\[0.8em]
0, & \text{o.w.}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases">
  <div class="topic-cases__lhs">$p_{\sssig X_nX}(x_n,x)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$\dfrac{1}{\,3\,},$</div>
    <div class="topic-cases__cond">$(x_n,x)=(1,2),(2,3),(3,1)$</div>
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$\text{o.w.}$</div>
  </div>
</div>

</div>

Show that $X_n$ converges to $X$ in distribution but not in probability.
</div>

可先計算 $X_n$ 與 $X$ 之[邊際分配](/lecture-notes/random-vectors-joint-pmf/#def-marginal-pmf)如下

$$
\begin{gathered}
p_{\sssig X_n}(x)=\frac{1}{\,3\,},\ x=1,2,3\\[0.45em]
p_{\sssig X}(x)=\frac{1}{\,3\,},\ x=1,2,3
\end{gathered}
$$

故 $X_n$ 與 $X$ 的 [cdf](/lecture-notes/cumulative-distribution-functions/#def-cdf) 分別為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig X_n}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & x<1\\[0.6em]
\dfrac{1}{\,3\,}, & 1\leqslant x<2\\[0.8em]
\dfrac{2}{\,3\,}, & 2\leqslant x<3\\[0.8em]
1, & x\geqslant3
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases">
  <div class="topic-cases__lhs">$F_{\sssig X_n}(x)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$x<1$</div>
    <div class="topic-cases__val">$\dfrac{1}{\,3\,},$</div>
    <div class="topic-cases__cond">$1\leqslant x<2$</div>
    <div class="topic-cases__val">$\dfrac{2}{\,3\,},$</div>
    <div class="topic-cases__cond">$2\leqslant x<3$</div>
    <div class="topic-cases__val">$1,$</div>
    <div class="topic-cases__cond">$x\geqslant3$</div>
  </div>
</div>

</div>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & x<1\\[0.6em]
\dfrac{1}{\,3\,}, & 1\leqslant x<2\\[0.8em]
\dfrac{2}{\,3\,}, & 2\leqslant x<3\\[0.8em]
1, & x\geqslant3
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases">
  <div class="topic-cases__lhs">$F_{\sssig X}(x)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$x<1$</div>
    <div class="topic-cases__val">$\dfrac{1}{\,3\,},$</div>
    <div class="topic-cases__cond">$1\leqslant x<2$</div>
    <div class="topic-cases__val">$\dfrac{2}{\,3\,},$</div>
    <div class="topic-cases__cond">$2\leqslant x<3$</div>
    <div class="topic-cases__val">$1,$</div>
    <div class="topic-cases__cond">$x\geqslant3$</div>
  </div>
</div>

</div>

由此可得

$$
\lim_{n\to\infty}F_{\sssig X_n}(x)=F_{\sssig X}(x)
$$

此即

$$
X_n\dconv X
$$

但若令 <span class="text-nowrap">$\varepsilon=0.5$，</span>則有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}\bigl(\lvert X_n-X\rvert<\varepsilon\bigr)=\mathbb{P}\bigl((X_n,X)=(1,1),(2,2),(3,3)\bigr)=0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}\bigl(\lvert X_n-X\rvert<\varepsilon\bigr)\\[0.45em]
&=\mathbb{P}\bigl((X_n,X)=(1,1),(2,2),(3,3)\bigr)=0
\end{aligned}
$$

</div>

故可知道

$$
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_n-X\rvert<\varepsilon\bigr)\neq1,\ \exists\,\varepsilon>0
$$

可知 $X_n$ 並沒有機率收斂至 <span class="text-nowrap">$X$。</span>

</div>

由於機率收斂要求對「所有」正數 $\varepsilon>0$ 皆滿足極限機率為 <span class="text-nowrap">$1$，</span>在論證序列不具備機率收斂時，只需如上題般具體指出某一個特定的 <span class="text-nowrap">$\varepsilon>0$，</span>使得

$$
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_n-X\rvert<\varepsilon\bigr)\neq1
$$

(或該極限不存在)，即可否定機率收斂。

## 收斂對象為常數時的等價關係

機率收斂雖強於分配收斂，但當收斂對象退化為一個常數時，分配收斂亦足以反推機率收斂，兩種收斂型態在此等價，見下列定理。

<div id="thm-pconv-iff-dconv" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 5.3 (收斂至常數時兩種收斂等價)</div>

$$
X_n\pconv c\ \text{若且唯若}\ X_n\dconv X\equiv c
$$

其中 $c$ 表示一常數。

</div>

<div class="topic-proof" markdown="1">
**Proof.**

$(\Longrightarrow)$ 由已知條件可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_n-c\rvert<\varepsilon\bigr)=\lim_{n\to\infty}\mathbb{P}(c-\varepsilon<X_n<c+\varepsilon)=1,\ \forall\,\varepsilon>0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_n-c\rvert<\varepsilon\bigr)\\[0.45em]
&=\lim_{n\to\infty}\mathbb{P}(c-\varepsilon<X_n<c+\varepsilon)\\[0.45em]
&=1,\ \forall\,\varepsilon>0
\end{aligned}
$$

</div>

由此可得

$$
\lim_{n\to\infty}\Bigl[F_{\sssig X_n}(c+\varepsilon)^{-}-F_{\sssig X_n}(c-\varepsilon)\Bigr]=1,\ \forall\,\varepsilon>0
$$

又由於 $0\leqslant F_{\sssig X_n}(x)\leqslant1$ 這個範圍，可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lim_{n\to\infty}F_{\sssig X_n}(c+\varepsilon)^{-}=1,\ \lim_{n\to\infty}F_{\sssig X_n}(c-\varepsilon)=0,\ \forall\,\varepsilon>0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\lim_{n\to\infty}F_{\sssig X_n}(c+\varepsilon)^{-}=1,\\[0.45em]
\lim_{n\to\infty}F_{\sssig X_n}(c-\varepsilon)=0,\ \forall\,\varepsilon>0
\end{gathered}
$$

</div>

也就是

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lim_{n\to\infty}F_{\sssig X_n}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & x<c\\[0.6em]
1, & x>c
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases">
  <div class="topic-cases__lhs">$\lim_{n\to\infty}F_{\sssig X_n}(x)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$x<c$</div>
    <div class="topic-cases__val">$1,$</div>
    <div class="topic-cases__cond">$x>c$</div>
  </div>
</div>

</div>

又 <span class="text-nowrap">$X\equiv c$，</span>可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & x<c\\[0.6em]
1, & x\geqslant c
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases">
  <div class="topic-cases__lhs">$F_{\sssig X}(x)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$x<c$</div>
    <div class="topic-cases__val">$1,$</div>
    <div class="topic-cases__cond">$x\geqslant c$</div>
  </div>
</div>

</div>

此即

$$
\lim_{n\to\infty}F_{\sssig X_n}(x)=F_{\sssig X}(x),\ \forall\,x\in C(F_{\sssig X})
$$

可知

$$
X_n\dconv X\equiv c
$$

$(\Longleftarrow)$ 由已知條件可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lim_{n\to\infty}F_{\sssig X_n}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
0, & x<c\\[0.6em]
1, & x>c
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases">
  <div class="topic-cases__lhs">$\lim_{n\to\infty}F_{\sssig X_n}(x)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$x<c$</div>
    <div class="topic-cases__val">$1,$</div>
    <div class="topic-cases__cond">$x>c$</div>
  </div>
</div>

</div>

又

<div class="topic-math-follow-before" markdown="1">
<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}\bigl(\lvert X_n-c\rvert<\varepsilon\bigr)=\mathbb{P}(c-\varepsilon<X_n<c+\varepsilon)=F_{\sssig X_n}(c+\varepsilon)^{-}-F_{\sssig X_n}(c-\varepsilon)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}\bigl(\lvert X_n-c\rvert<\varepsilon\bigr)&=\mathbb{P}(c-\varepsilon<X_n<c+\varepsilon)\\[0.45em]
&=F_{\sssig X_n}(c+\varepsilon)^{-}-F_{\sssig X_n}(c-\varepsilon)
\end{aligned}
$$

</div>
</div>
<div class="topic-math-follow" markdown="1">
<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\Longrightarrow\ \lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_n-c\rvert<\varepsilon\bigr)=\lim_{n\to\infty}\Bigl[F_{\sssig X_n}(c+\varepsilon)^{-}-F_{\sssig X_n}(c-\varepsilon)\Bigr]=1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ &\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_n-c\rvert<\varepsilon\bigr)\\[0.45em]
&=\lim_{n\to\infty}\Bigl[F_{\sssig X_n}(c+\varepsilon)^{-}-F_{\sssig X_n}(c-\varepsilon)\Bigr]\\[0.45em]
&=1
\end{aligned}
$$

</div>
</div>

故可知

$$
X_n\pconv c
$$

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

一般情形下分配收斂之所以無法保證機率收斂，是因為兩個同分配的隨機變數仍可能各自隨機變動而取值相異。一旦極限對象為常數 $c$ (即[退化的隨機變數](/lecture-notes/variance/#thm-variance-properties))，極限分配的全部機率質量皆集中於單點 <span class="text-nowrap">$c$；</span>隨 $n\to\infty$ 序列 $X_n$ 的隨機性逐漸退化，其取值落在 $c$ 任意鄰域內的機率必趨於 <span class="text-nowrap">$1$，</span>故自然滿足機率收斂。

</div>

<div id="ex-gamma-degenerating-to-one" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.12</div>

<div lang="en" markdown="1">
Let $X_1,X_2,X_3,\ldots$ be independent random variables such that $X_n$ has pdf

$$
f_n(x)=\frac{\,n^{n}x^{n-1}e^{-nx}\,}{\Gamma(n)},\ x>0,\ n=1,2,3,\ldots
$$

<ol class="topic-list-paren">
  <li>Does $X_n$ converge in distribution? If so, find its limiting distribution.</li>
  <li>Does $X_n$ converge in probability? Justify your answer.</li>
</ol>
</div>

(1) 由題意可知
{: .topic-paren-item}

$$
X_n\sim\mathrm{Gamma}\Bigl(\alpha=n,\ \beta=\frac{1}{\,n\,}\Bigr)
$$

故可知其[動差母函數](/lecture-notes/moment-generating-functions/#def-mgf)為
{: .topic-paren-cont}

<div class="topic-math-follow-before" markdown="1">

$$
M_{\sssig X_n}(t)=\Bigl(1-\frac{t}{\,n\,}\Bigr)^{-n},\ t<n
$$

</div>
<div class="topic-math-follow" markdown="1">
<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\Longrightarrow\ \lim_{n\to\infty}M_{\sssig X_n}(t)=\lim_{n\to\infty}\Bigl(1-\frac{t}{\,n\,}\Bigr)^{-n}=(e^{-t})^{-1}=e^{t},\ t\in\mathbb{R}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ \lim_{n\to\infty}M_{\sssig X_n}(t)&=\lim_{n\to\infty}\Bigl(1-\frac{t}{\,n\,}\Bigr)^{-n}\\[0.45em]
&=(e^{-t})^{-1}=e^{t},\ t\in\mathbb{R}
\end{aligned}
$$

</div>
</div>

令 $X\equiv1$ 具 mgf $M_{\sssig X}(t)=e^{t},\ t\in\mathbb{R}$ 這個函數，則有
{: .topic-paren-cont}

$$
\lim_{n\to\infty}M_{\sssig X_n}(t)=M_{\sssig X}(t),\ t\in\mathbb{R}
$$

由[列維連續性定理](/lecture-notes/levy-continuity-theorem/#thm-levys-continuity-thm)可知
{: .topic-paren-cont}

$$
X_n\dconv X\equiv1
$$

(2) 由於 $X_n\dconv X\equiv1$ 成立，故可知
{: .topic-paren-item}

$$
X_n\pconv1
$$

</div>

## 樣本平均數與樣本變異數的機率極限

<div id="ex-xbar-probability-limit" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.9 ($\overline{X}$ 的一致性, <span lang="en">Continued</span>)</div>

<div lang="en" markdown="1">
Let $X_1,\ldots,X_n\iidto\mathcal{N}(\mu,\sigma^{2})$, and let $\overline{X}=\frac{1}{\,n\,}\sum_{i=1}^{n}X_i$ be the sample mean. Find the probability limit of <span class="text-nowrap">$\overline{X}$.</span>
</div>

**[法一]**

由於[前一篇已求得](/lecture-notes/levy-continuity-theorem/#ex-xbar-consistency-mgf) $\overline{X}\dconv W\equiv\mu$ 這個結果，故可知

$$
\overline{X}\pconv\mu
$$

**[法二]**

由[柴比雪夫不等式](/lecture-notes/probability-inequalities/#thm-chebyshev)可知

$$
\mathbb{P}\bigl(\lvert\overline{X}-\mu\rvert\geqslant\varepsilon\bigr)\leqslant\frac{\sigma^{2}}{\,n\varepsilon^{2}\,},\ \varepsilon>0
$$

則有

$$
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert\overline{X}-\mu\rvert\geqslant\varepsilon\bigr)=0,\ \varepsilon>0
$$

此即

$$
\overline{X}\pconv\mu
$$

</div>

上述 [法二] 直接以柴比雪夫不等式搭配 $\mathrm{Var}(\overline{X})=\sigma^{2}/n$ 證明機率收斂，無須動用常態母體的抽樣分配；後文證明**弱大數法則 <span lang="en">(Weak Law of Large Numbers)</span>** 時，亦將沿用同一推導結構。

<div id="ex-s-squared-probability-limit" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.10 ($S^{2}$ 的一致性, <span lang="en">Continued</span>)</div>

<div lang="en" markdown="1">
Let $X_1,\ldots,X_n\iidto\mathcal{N}(\mu,\sigma^{2})$, and let $S^{2}=\frac{1}{\,n-1\,}\sum_{i=1}^{n}(X_i-\overline{X})^{2}$ be the sample variance. Find the probability limit of <span class="text-nowrap">$S^{2}$.</span>
</div>

**[法一]**

由於[前一篇已求得](/lecture-notes/levy-continuity-theorem/#ex-s-squared-consistency-mgf) $S^{2}\dconv W\equiv\sigma^{2}$ 這個結果，故可知

$$
S^{2}\pconv\sigma^{2}
$$

</div>

分配收斂與機率收斂在後續大樣本理論中各有重要的應用；後文介紹的[弱大數法則](/lecture-notes/weak-law-and-central-limit-theorem/#thm-weak-law-of-large-numbers)本質上即為樣本平均數的機率收斂，而[中央極限定理](/lecture-notes/weak-law-and-central-limit-theorem/#thm-central-limit-theorem) <span lang="en">(Central Limit Theorem)</span> 則刻畫標準化樣本平均數的分配收斂，屆時會有更多應用。在此之前，我們先探討另外兩種收斂型態。

## 本篇小結

[Definition 5.2](#def-converge-in-probability) 把機率收斂寫成 $\lim_{n\to\infty}\mathbb{P}(\lvert X_n-X\rvert<\varepsilon)=1$ 這條對任意 $\varepsilon>0$ 都要成立的等式，比的是 $X_n$ 與 $X$ 的取值而不是兩者的分配，因此它要求 $X$ 與整個序列定義在同一個機率空間之上，否則 $X_n(\omega)-X(\omega)$ 這個差根本寫不出來。滿足這條等式時，$X$ 稱為 $X_n$ 的機率極限。

[Theorem 5.2](#thm-pconv-implies-dconv) 給出兩種收斂型態的強弱關係，說明機率收斂導致分配收斂，反之不成立。[Example 5.11](#ex-dconv-without-pconv) 就是反向不成立的反例，該題的[聯合 pmf](/lecture-notes/random-vectors-joint-pmf/#def-joint-pmf) 把機率平均放在 <span class="text-nowrap">$(1,2)$、</span>$(2,3)$ 與 $(3,1)$ 三個點上，兩個邊際 pmf 都是 <span class="text-nowrap">$\frac{1}{\,3\,}$、</span>cdf 因而完全相同，可是 $X_n$ 與 $X$ 的取值永遠差一個單位以上，取 $\varepsilon=0.5$ 即得 $\mathbb{P}(\lvert X_n-X\rvert<\varepsilon)=0$ 成立。要否定機率收斂，找到一個這樣的 $\varepsilon$ 即可。

[Theorem 5.3](#thm-pconv-iff-dconv) 則指出，收斂對象若是一個常數 <span class="text-nowrap">$c$，</span>兩種收斂型態反而等價。證明的關鍵是把 $\mathbb{P}(\lvert X_n-c\rvert<\varepsilon)$ 改寫成 $F_{\sssig X_n}(c+\varepsilon)^{-}-F_{\sssig X_n}(c-\varepsilon)$ 這個差，再配合 $0\leqslant F_{\sssig X_n}(x)\leqslant1$ 這個範圍，兩個方向都由這條恆等式讀得出來。[Example 5.12](#ex-gamma-degenerating-to-one) 是這條定理的直接應用，$\mathrm{Gamma}\bigl(n,\frac{1}{\,n\,}\bigr)$ 的 mgf 在 $n\to\infty$ 時趨於 <span class="text-nowrap">$e^{t}$，</span>也就是退化在 $1$ 上的隨機變數之 mgf，於是分配收斂與機率收斂同時成立。[Example 5.9](#ex-xbar-probability-limit) 與 [Example 5.10](#ex-s-squared-probability-limit) 把同一條定理用在常態隨機樣本上，分別得到 $\overline{X}\pconv\mu$ 與 $S^{2}\pconv\sigma^{2}$ 這兩個結果，這正是這兩個統計量具備一致性的意思；$\overline{X}$ 的部分另有一條不經過分配收斂的路，直接由柴比雪夫不等式配合 $\mathrm{Var}(\overline{X})=\frac{\sigma^{2}}{\,n\,}$ 得到，這條路稍後會再出現於弱大數法則的證明之中。

[下一篇](/lecture-notes/convergence-in-mean-and-almost-sure/)接著給出 $r$ 次均方收斂與幾乎確信收斂這兩種收斂型態，並說明它們與機率收斂之間的蘊含關係。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Kai Lai Chung. 2001. *A Course in Probability Theory*. 3rd ed. Academic Press.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
