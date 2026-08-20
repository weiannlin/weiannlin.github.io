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
published: false
excerpt: "機率收斂要求的是兩個隨機變數的取值任意接近，而不是兩個機率分配趨於一致: 若對任意的 $\\varepsilon>0$ 都有 $\\lim_{n\\to\\infty}\\mathbb{P}(\\lvert X_n-X\\rvert\\lt \\varepsilon)=1$，則稱 $X_n$ 機率收斂至 $X$，並稱 $X$ 為 $X_n$ 的機率極限。本篇先說明這個定義為什麼要求 $X$ 與整個序列落在同一個機率空間，再給出機率收斂與分配收斂之間的兩條關係。第一條是機率收斂必然導致分配收斂而反之不然，反例取一組把機率平均放在 $(1,2)$、$(2,3)$ 與 $(3,1)$ 三點的聯合 pmf，兩個邊際分配完全相同，取值卻永遠不相等。第二條是收斂對象若為一常數則兩者等價，證明的作法是把 $\\mathbb{P}(\\lvert X_n-c\\rvert\\lt \\varepsilon)$ 寫成兩個 cdf 值之差。最後以伽瑪分配退化至 $1$ 的例題，以及常態隨機樣本的樣本平均數與樣本變異數，示範這條等價關係怎麼用來求機率極限。"
---

[上一篇](/lecture-notes/levy-continuity-theorem/)以列維連續性定理把[分配收斂](/lecture-notes/convergence-in-distribution/#def-converge-in-distribution)的判定改由動差母函數的極限來處理，五道例題都不必先求出極限 cdf。本篇轉入另一種收斂型態: 機率收斂。

這兩種收斂型態關心的不是同一件事情。分配收斂比較的是兩個 cdf，只要極限 cdf 與收斂對象的 cdf 在連續點上相等即可，兩個[隨機變數](/lecture-notes/random-variables-and-pmf/#def-random-variable)的取值可以毫不相干；機率收斂比較的則是取值本身，它要求 $X_n$ 與 $X$ 的隨機變數值任意地接近。本篇先給出機率收斂的定義與它的直觀，再給出兩條把這兩種收斂型態接起來的定理: 一條說機率收斂必然導致分配收斂而反之不然，另一條說收斂對象若是一個常數，兩者反而等價。最後以三道例題示範這兩條定理怎麼用來求機率極限。

## 機率收斂的定義

<div id="def-converge-in-probability" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 5.2 (機率收斂, converge in probability)</div>

令 $\lbrace X_n\rbrace_{n=1}^{\infty}$ 為一定義在[機率空間](/lecture-notes/event-families-sigma-fields/#definition-probability-space)上之隨機變數序列，若 $X$ 為定義在相同機率空間中之隨機變數，且滿足

$$
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_n-X\rvert<\varepsilon\bigr)=1,\ \forall\varepsilon>0
$$

則稱 $X_n$ 機率收斂至 $X$，記為 $X_n\pconv X$，也可記為 $\underset{n\to\infty}{\mathrm{plim}}\,X_n=X$，此時 $X$ 稱為 $X_n$ 的**機率極限 <span lang="en">(probability limit)</span>**。

</div>

機率收斂的概念是，這個隨機變數的序列，其「隨機變數值」收斂至「$X$ 的隨機變數值」，屬於隨機變數值與隨機變數值之間的關係。與分配收斂不相同的地方是，我們並沒有要求關於機率分配是否要收斂，只要求這兩個隨機變數的數值要「任意地接近」。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

讀者可以思考看看，為什麼機率收斂的定義，要刻意要求作為收斂對象的 $X$，必須與 $\lbrace X_i\rbrace_{i=1}^{\infty}$ 在同一個機率空間中呢？

這是因為，機率收斂的定義，事實上是在要求，對於樣本空間中的每一個樣本點 $\omega\in S$ 而言，$X_n(\omega)$ 與 $X(\omega)$ 所對應的「隨機變數值」必須要非常接近，至於有多接近呢？ 這是一個 $\varepsilon-\delta$ 的定義，也就是，「要多接近就有多接近」，但我們也沒有要求這個「要多接近就有多接近」的事件一定發生，只是要求這件事情發生的機率，在 $n\to\infty$ 時必須為 $1$。[^prob-one] 因此，機率收斂的概念是，這個隨機變數的序列，在 $n\to\infty$ 時，其隨機變數值與 $X$ 的隨機變數值「任意地接近」的機率為 $1$。

另一方面，讀者可以思考看看，機率收斂與分配收斂的定義，是哪一個比較強、哪一個比較弱呢？ 有沒有誰成立導致誰成立的關係呢？ 見下列這個定理。

</div>

## 機率收斂與分配收斂的強弱關係

<div id="thm-pconv-implies-dconv" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 5.2 (機率收斂導致分配收斂, convergence in probability implies convergence in distribution)</div>

若 $X_n\pconv X$，則有

$$
X_n\dconv X
$$

反之未必成立。

</div>

<div class="topic-proof" markdown="1">
**Proof.**

令 $x$ 為 $F_{\sssig X}$ 的任一個連續點，取任意的 $\varepsilon>0$，並令

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

其中第一塊之內同時有 $X_n\leqslant x$ 與 $X<X_n+\varepsilon$，故該塊落在 $\lbrace X\leqslant x+\varepsilon\rbrace$ 之內；第二塊則整個落在 $A_n^{\prime}$ 之內。故由 [Theorem 1.7](/lecture-notes/probability-rules-from-axioms/#theorem-monotonicity) 的單調性可得

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

同樣的作法用在 $\lbrace X\leqslant x-\varepsilon\rbrace$ 上。此時第一塊之內同時有 $X\leqslant x-\varepsilon$ 與 $X_n<X+\varepsilon$，故該塊落在 $\lbrace X_n\leqslant x\rbrace$ 之內，可得

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

最後說明左右兩側都可以任意接近 $F_{\sssig X}(x)$ 這個值。任取 $\eta>0$，由於 $x$ 是 $F_{\sssig X}$ 的連續點，可取一個夠小的 $\varepsilon>0$，使得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig X}(x+\varepsilon)-F_{\sssig X}(x)<\frac{\eta}{\,2\,},\quad F_{\sssig X}(x)-F_{\sssig X}(x-\varepsilon)<\frac{\eta}{\,2\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig X}(x+\varepsilon)-F_{\sssig X}(x)&<\frac{\eta}{\,2\,},\\[0.45em]
F_{\sssig X}(x)-F_{\sssig X}(x-\varepsilon)&<\frac{\eta}{\,2\,}
\end{aligned}
$$

</div>

又由 $\mathbb{P}(A_n^{\prime})\to0$，可取一個夠大的 $N$，使得 $n\geqslant N$ 時 $\mathbb{P}(A_n^{\prime})<\frac{\eta}{\,2\,}$ 這個不等式成立。把這兩件事代回上式可知，$n\geqslant N$ 時

$$
F_{\sssig X}(x)-\eta<F_{\sssig X_n}(x)<F_{\sssig X}(x)+\eta
$$

由於 $\eta>0$ 可以任意小，故

$$
\lim_{n\to\infty}F_{\sssig X_n}(x)=F_{\sssig X}(x),\ \forall x\in C(F_{\sssig X})
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

這個概念其實並不難理解，因為，如果 $X_n$ 與 $X$ 在 $n\to\infty$ 時任意接近的機率為 $1$，那不管 $X$ 去哪裡了，$X_n$ 總是會跟它形影不離，從機率分配的角度上來看，這二者的機率分配當然應該要是一樣的才對；但反之，即便我們有兩個機率分配一模一樣的隨機變數，我們也不能保證他們的「值」是一樣的，因此機率收斂可以導致分配收斂，但分配收斂卻未必能導致機率收斂。[^same-distribution]

</div>

<div id="ex-dconv-without-pconv" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.11</div>

<div lang="en" markdown="1">
Suppose that for each $n=1,2,\ldots$ the pair $(X_n,X)$ has the joint pmf

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

Show that $X_n$ converges in distribution to <span class="text-nowrap">$X$,</span> but that it does not converge in probability to <span class="text-nowrap">$X$.</span>
</div>

可先計算 $X_n$ 與 $X$ 之[邊際分配](/lecture-notes/random-vectors-joint-pmf/#def-marginal-pmf)如下

$$
\begin{aligned}
p_{\sssig X_n}(x)&=\frac{1}{\,3\,},\ x=1,2,3\\[0.45em]
p_{\sssig X}(x)&=\frac{1}{\,3\,},\ x=1,2,3
\end{aligned}
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

但若令 $\varepsilon=0.5$，則有

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

可知 $X_n$ 並沒有機率收斂至 $X$。

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

在這個問題中，要說明 $X_n$ 並沒有機率收斂至 $X$，我們只需要找一個反例來說明，存在這樣的 $\varepsilon>0$，使得

$$
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_n-X\rvert<\varepsilon\bigr)\neq1
$$

這樣就能夠說明 $X_n$ 並沒有機率收斂至 $X$ 了。

</div>

## 收斂對象為常數時的等價關係

雖然機率收斂是一個比分配收斂要更強的性質，但有的時候，分配收斂還是可以導致機率收斂的，見下列這一個定理。

<div id="thm-pconv-iff-dconv" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 5.3 (收斂至常數時兩種收斂等價, equivalence of the two modes when the limit is a constant)</div>

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
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_n-c\rvert<\varepsilon\bigr)=\lim_{n\to\infty}\mathbb{P}(c-\varepsilon<X_n<c+\varepsilon)=1,\ \forall\varepsilon>0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_n-c\rvert<\varepsilon\bigr)\\[0.45em]
&=\lim_{n\to\infty}\mathbb{P}(c-\varepsilon<X_n<c+\varepsilon)\\[0.45em]
&=1,\ \forall\varepsilon>0
\end{aligned}
$$

</div>

由此可得

$$
\lim_{n\to\infty}\Bigl[F_{\sssig X_n}(c+\varepsilon)^{-}-F_{\sssig X_n}(c-\varepsilon)\Bigr]=1,\ \forall\varepsilon>0
$$

又由於 $0\leqslant F_{\sssig X_n}(x)\leqslant1$，可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lim_{n\to\infty}F_{\sssig X_n}(c+\varepsilon)^{-}=1,\ \lim_{n\to\infty}F_{\sssig X_n}(c-\varepsilon)=0,\ \forall\varepsilon>0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\lim_{n\to\infty}F_{\sssig X_n}(c+\varepsilon)^{-}&=1,\\[0.45em]
\lim_{n\to\infty}F_{\sssig X_n}(c-\varepsilon)&=0,\ \forall\varepsilon>0
\end{aligned}
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
  <div class="topic-cases__lhs">$\lim\limits_{n\to\infty}F_{\sssig X_n}(x)=$</div>
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

又 $X\equiv c$，可知

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
\lim_{n\to\infty}F_{\sssig X_n}(x)=F_{\sssig X}(x),\ \forall x\in C(F_{\sssig X})
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
  <div class="topic-cases__lhs">$\lim\limits_{n\to\infty}F_{\sssig X_n}(x)=$</div>
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
&\Longrightarrow\ \lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_n-c\rvert<\varepsilon\bigr)\\[0.45em]
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

這個定理其實很容易理解，稍早我們提過機率收斂與分配收斂最大的不同在於，機率收斂要求隨機變數序列的值，要與收斂對象的值「任意地接近」，那麼如果收斂的對象是一個常數，也就能反過來說，當 $n\to\infty$，則 $X_n$ 幾乎就是一個常數，代表其隨機性已經退化掉了；反之，若知道 $X_n$ 分配收斂至某個常數 (或[退化的隨機變數](/lecture-notes/variance/#thm-variance-properties))，則此時，不僅是分配相同，由於隨機性退化的緣故，$X_n$ 的值也會幾乎永遠都與該常數任意地接近 (甚至相同)，當然也就導致了機率收斂的結果。

</div>

<div id="ex-gamma-degenerating-to-one" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.12</div>

<div lang="en" markdown="1">
Suppose that $X_1,X_2,X_3,\ldots$ are independent random variables and that the pdf of $X_n$ is given by

$$
f_n(x)=\frac{\,n^{n}x^{n-1}e^{-nx}\,}{\Gamma(n)},\ x>0,\ n=1,2,3,\ldots
$$

<ol class="topic-list-paren">
  <li>Determine whether $X_n$ converges in distribution, and find the limiting distribution if it does.</li>
  <li>Determine whether $X_n$ converges in probability, and give the reason for your answer.</li>
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

令 $X\equiv1$ 具 mgf $M_{\sssig X}(t)=e^{t},\ t\in\mathbb{R}$，則有
{: .topic-paren-cont}

$$
\lim_{n\to\infty}M_{\sssig X_n}(t)=M_{\sssig X}(t),\ t\in\mathbb{R}
$$

由[列維連續性定理](/lecture-notes/levy-continuity-theorem/#thm-levys-continuity-thm)可知
{: .topic-paren-cont}

$$
X_n\dconv X\equiv1
$$

(2) 由於 $X_n\dconv X\equiv1$，故可知
{: .topic-paren-item}

$$
X_n\pconv1
$$

</div>

## 樣本平均數與樣本變異數的機率極限

<div id="ex-xbar-probability-limit" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.9 ($\overline{X}$ 的一致性, <span lang="en">Continued</span>)</div>

<div lang="en" markdown="1">
Suppose that $X_1,\ldots,X_n\iidto\mathcal{N}(\mu,\sigma^{2})$ and let $\overline{X}=\frac{1}{\,n\,}\sum_{i=1}^{n}X_i$ denote the sample mean. Find the probability limit of <span class="text-nowrap">$\overline{X}$.</span>
</div>

**[法一]**

由於[前一篇已求得](/lecture-notes/levy-continuity-theorem/#ex-xbar-consistency-mgf) $\overline{X}\dconv W\equiv\mu$，故可知

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

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

稍後談到**弱大數法則 <span lang="en">(Weak Law of Large Numbers)</span>** 時，我們還會再看到與這題非常類似的結構。

</div>

<div id="ex-s-squared-probability-limit" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.10 ($S^{2}$ 的一致性, <span lang="en">Continued</span>)</div>

<div lang="en" markdown="1">
Suppose that $X_1,\ldots,X_n\iidto\mathcal{N}(\mu,\sigma^{2})$ and let $S^{2}=\frac{1}{\,n-1\,}\sum_{i=1}^{n}(X_i-\overline{X})^{2}$ denote the sample variance. Find the probability limit of <span class="text-nowrap">$S^{2}$.</span>
</div>

**[法一]**

由於[前一篇已求得](/lecture-notes/levy-continuity-theorem/#ex-s-squared-consistency-mgf) $S^{2}\dconv W\equiv\sigma^{2}$，故可知

$$
S^{2}\pconv\sigma^{2}
$$

</div>

關於分配收斂與機率收斂的一些衍生特性，我們將在後續講到[中央極限定理](/lecture-notes/weak-law-and-central-limit-theorem/#thm-central-limit-theorem) <span lang="en">(Central Limit Theorem)</span> 與[弱大數法則](/lecture-notes/weak-law-and-central-limit-theorem/#thm-weak-law-of-large-numbers)時再次談到，屆時會有更多的搭配應用。[^clt-and-wlln]

接下來，讓我們來看一下其他型態的收斂。

## 本篇小結

[Definition 5.2](#def-converge-in-probability) 把機率收斂寫成 $\lim_{n\to\infty}\mathbb{P}(\lvert X_n-X\rvert<\varepsilon)=1$ 這條對任意 $\varepsilon>0$ 都要成立的等式，比的是 $X_n$ 與 $X$ 的取值而不是兩者的分配，因此它要求 $X$ 與整個序列定義在同一個機率空間之上，否則 $X_n(\omega)-X(\omega)$ 這個差根本寫不出來。滿足這條等式時，$X$ 稱為 $X_n$ 的機率極限。

[Theorem 5.2](#thm-pconv-implies-dconv) 給出兩種收斂型態的強弱: 機率收斂導致分配收斂，反之不成立。[Example 5.11](#ex-dconv-without-pconv) 就是反向不成立的反例，該題的[聯合 pmf](/lecture-notes/random-vectors-joint-pmf/#def-joint-pmf) 把機率平均放在 $(1,2)$、$(2,3)$ 與 $(3,1)$ 三個點上，兩個邊際 pmf 都是 $\frac{1}{\,3\,}$、cdf 因而完全相同，可是 $X_n$ 與 $X$ 的取值永遠差一個單位以上，取 $\varepsilon=0.5$ 即得 $\mathbb{P}(\lvert X_n-X\rvert<\varepsilon)=0$。要否定機率收斂，找到一個這樣的 $\varepsilon$ 就足夠了。

[Theorem 5.3](#thm-pconv-iff-dconv) 則指出，收斂對象若是一個常數 $c$，兩種收斂型態反而等價。證明的關鍵是把 $\mathbb{P}(\lvert X_n-c\rvert<\varepsilon)$ 改寫成 $F_{\sssig X_n}(c+\varepsilon)^{-}-F_{\sssig X_n}(c-\varepsilon)$ 這個差，再配合 $0\leqslant F_{\sssig X_n}(x)\leqslant1$，兩個方向都由這條恆等式讀得出來。[Example 5.12](#ex-gamma-degenerating-to-one) 是這條定理的直接應用: $\mathrm{Gamma}\bigl(n,\frac{1}{\,n\,}\bigr)$ 的 mgf 在 $n\to\infty$ 時趨於 $e^{t}$，也就是退化在 $1$ 上的隨機變數之 mgf，於是分配收斂與機率收斂同時成立。[Example 5.9](#ex-xbar-probability-limit) 與 [Example 5.10](#ex-s-squared-probability-limit) 把同一條定理用在常態隨機樣本上，分別得到 $\overline{X}\pconv\mu$ 與 $S^{2}\pconv\sigma^{2}$，這正是這兩個統計量具備一致性的意思；$\overline{X}$ 的部分另有一條不經過分配收斂的路，直接由柴比雪夫不等式配合 $\mathrm{Var}(\overline{X})=\frac{\sigma^{2}}{\,n\,}$ 得到，這條路稍後會再出現於弱大數法則的證明之中。

[下一篇](/lecture-notes/convergence-in-mean-and-almost-sure/)接著給出 $r$ 次均方收斂與幾乎確信收斂這兩種收斂型態，並說明它們與機率收斂之間的蘊含關係。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Kai Lai Chung. 2001. *A Course in Probability Theory*. 3rd ed. Academic Press.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.

[^prob-one]: 讀者應該還記得，機率為 $0$ 的事件不一定不會發生，而機率為 $1$ 的事件也不一定必然發生。

[^same-distribution]: 最簡單的例子就是一組隨機樣本，他們的機率分配是相同的，故 cdf 肯定是一樣的，但是隨機樣本的每一個值卻沒有被保證一定一樣。

[^clt-and-wlln]: 事實上，中央極限定理本身就是分配收斂的概念，而弱大數法則則是機率收斂的概念，稍後詳談。
