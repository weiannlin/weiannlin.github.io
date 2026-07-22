---
title: "機率母函數與累積量母函數"
subtitle: "Probability-Generating and Cumulant-Generating Functions"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 13
order: 213
permalink: /teaching-topics/probability-cumulant-generating-functions/
date: 2026-07-13
published: true
excerpt: '機率母函數 (PGF) 以冪級數整理非負整數值隨機變數的機率與階乘動差；累積量母函數 (CGF) 則對 MGF 取對數，由微分得到期望值、變異數與高階累積量。'
---

[上一篇文章](/teaching-topics/moment-generating-functions/)介紹動差母函數 (moment-generating function, MGF)，說明如何由 $M_X(t)=\mathbb{E}(e^{tX})$ 生成各階原動差。本篇再整理兩種母函數。**機率母函數 (probability-generating function, PGF)** 適用於非負整數值隨機變數，可生成各點機率與**階乘動差 (factorial moment)**；**累積量母函數 (cumulant-generating function, CGF)** 則由 MGF 取對數而得，可生成**累積量 (cumulant)**。

三種母函數使用的函數形式不同，微分後代入的點也不同。MGF 在 $t=0$ 生成原動差；PGF 在 $s=1$ 生成階乘動差，並在 $s=0$ 取回各點機率；CGF 在 $t=0$ 生成累積量。

## 機率母函數

令 $X$ 只取 $0,1,2,\ldots$ 等非負整數值，並以 $p_X(k)=\mathbb{P}(X=k)$ 表示其 pmf。此時可把各點機率排成一個以 $s$ 為變數的冪級數。

<div id="definition-218" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.18</div>

若 $X$ 為非負整數值隨機變數，則定義

$$
G_X(s)
=
\mathbb{E}(s^X)
=
\sum_{k=0}^{\infty}s^k p_X(k)
$$

為 $X$ 的**機率母函數 (probability-generating function, PGF)**。上式對所有使級數絕對收斂的 $s$ 有意義；至少對每個滿足 $\lvert s\rvert\leqslant 1$ 的實數 $s$ 皆存在。

</div>

因為 $\sum_{k=0}^{\infty}p_X(k)=1$，所以

$$
G_X(1)=1
$$

而 $G_X(0)=p_X(0)$。PGF 是 $s$ 的函數，不再是隨機變數。非負整數值的條件也不能省略，因為冪級數中 $s^k$ 的係數正是 $\mathbb{P}(X=k)$；一般實值或連續型隨機變數的 $\mathbb{E}(s^X)$ 不稱為 PGF。

<div id="note-pgf-domain" class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

PGF 在 $\lvert s\rvert\leqslant 1$ 必定存在，但未必能延伸到所有實數。例如某些分配的 PGF 在 $s>1$ 會發散。後續微分或代入 $s=e^t$ 時，仍須檢查對應的收斂範圍。
</div>

## PGF 生成階乘動差

對冪次 $s^k$ 微分一次會產生 $k s^{k-1}$；連續微分 $r$ 次，則會產生由 $k$ 向下相乘的係數。對正整數 $r$，令

$$
(X)_r
=
X(X-1)\cdots(X-r+1)
$$

若 $\mathbb{E}[(X)_r]<\infty$，則稱這個期望值為 $X$ 的 $r$ 階**階乘動差 (factorial moment)**。

<div id="proposition-212" class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Proposition 2.12 (Generating Factorial Moments)</div>

令 $X$ 為非負整數值隨機變數，$r$ 為正整數。若

$$
\mathbb{E}[(X)_r]<\infty
$$

則 PGF 在 $s=1$ 的 $r$ 階左導數滿足

$$
G_X^{(r)}(1-)
=
\mathbb{E}[(X)_r]
$$

若 $G_X$ 在包含 $1$ 的開區間內有限，則可寫成普通導數

$$
G_X^{(r)}(1)
=
\mathbb{E}[(X)_r]
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.** 對 $0\leqslant s<1$，可在冪級數的收斂區間內逐項微分，得到

$$
G_X^{(r)}(s)
=
\sum_{k=r}^{\infty}
k(k-1)\cdots(k-r+1)s^{k-r}p_X(k)
$$

令 $s$ 由左側趨近 $1$。各項皆非負，且隨 $s$ 單調增加，因此由單調收斂定理可得

$$
\begin{aligned}
G_X^{(r)}(1-)
&=
\sum_{k=r}^{\infty}
k(k-1)\cdots(k-r+1)p_X(k) \\[0.35em]
&=
\mathbb{E}\big[X(X-1)\cdots(X-r+1)\big]
\end{aligned}
$$

原式得證。$\square$
</div>

前兩階的結果為

$$
G_X'(1-)=\mathbb{E}(X),
\qquad
G_X''(1-)=\mathbb{E}[X(X-1)]
$$

由 $X^2=X(X-1)+X$ 可得

$$
\mathbb{E}(X^2)=G_X''(1-)+G_X'(1-)
$$

將前兩階導數代入變異數的計算公式，可得

$$
\mathrm{Var}(X)
=
G_X''(1-)+G_X'(1-)-[G_X'(1-)]^2
$$

## PGF 取回各點機率

PGF 的另一項功能，是從冪級數係數取回 pmf。對 $G_X(s)$ 微分 $k$ 次後，次方低於 $k$ 的項消失；再代入 $s=0$，只有原來的 $s^k$ 項會留下。

<div id="proposition-213" class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Proposition 2.13 (Recovering the pmf)</div>

若 $X$ 為非負整數值隨機變數，則對每個非負整數 $k$，皆有

$$
\mathbb{P}(X=k)
=
\frac{G_X^{(k)}(0)}{k!}
$$

其中 $G_X^{(0)}(0)=G_X(0)$。

</div>

<div class="topic-proof" markdown="1">
**Proof.** 當 $k\geqslant 1$ 時，逐項微分可得

$$
\begin{aligned}
G_X^{(k)}(s)
&=
k!p_X(k) \\
&\quad+
\sum_{j=k+1}^{\infty}
j(j-1)\cdots(j-k+1)s^{j-k}p_X(j)
\end{aligned}
$$

代入 $s=0$ 後，第二行的每一項都含有正次方的 $s$，故

$$
G_X^{(k)}(0)=k!p_X(k)
$$

除以 $k!$ 即得所求。$k=0$ 時則由 $G_X(0)=p_X(0)$ 直接成立。原式得證。$\square$
</div>

## 累積量母函數

MGF 把原動差放進同一個函數。若再對 MGF 取自然對數，微分後所得的係數稱為累積量。

<div id="definition-219" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.19</div>

若 $X$ 的 MGF $M_X(t)=\mathbb{E}(e^{tX})$ 在某個包含 $0$ 的開區間內有限，則定義

$$
K_X(t)=\log M_X(t)
$$

為 $X$ 的**累積量母函數 (cumulant-generating function, CGF)**。對正整數 $r$，定義

$$
\kappa_r=K_X^{(r)}(0)
$$

為 $X$ 的 $r$ 階**累積量 (cumulant)**。

</div>

因為 $M_X(t)>0$ 且 $M_X(0)=1$，所以 CGF 在 MGF 有限的區間內有定義，並且

$$
K_X(0)=\log 1=0
$$

CGF 的前兩階導數為

$$
K_X'(t)=\frac{M_X'(t)}{M_X(t)}
$$

再對 $t$ 微分一次，可得

$$
K_X''(t)
=
\frac{M_X''(t)M_X(t)-[M_X'(t)]^2}{[M_X(t)]^2}
$$

令 $t=0$，並使用 $M_X(0)=1$、$M_X'(0)=\mathbb{E}(X)$ 與 $M_X''(0)=\mathbb{E}(X^2)$，可得

$$
\kappa_1=\mathbb{E}(X)
$$

第二階累積量則為

$$
\begin{aligned}
\kappa_2
&=
\mathbb{E}(X^2)-[\mathbb{E}(X)]^2 \\[0.35em]
&=
\mathrm{Var}(X)
\end{aligned}
$$

繼續微分可得

$$
\kappa_3
=
\mathbb{E}\big[(X-\mu_X)^3\big]
$$

第四階累積量則為

$$
\kappa_4
=
\mathbb{E}\big[(X-\mu_X)^4\big]
-3[\mathrm{Var}(X)]^2
$$

因此，前三階累積量依序對應期望值、變異數與三階主動差；第四階累積量則是四階主動差減去三倍變異數平方。

<div id="note-cgf-existence" class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

CGF 的定義以 MGF 在某個包含 $0$ 的開區間內有限為前提。各階動差全都存在，仍不足以保證 MGF 或 CGF 在 $0$ 附近存在。因此，不能只由動差存在便直接寫出 CGF 的泰勒展開。
</div>

## PGF、MGF 與 CGF 的關係

若 $X$ 為非負整數值隨機變數，則在兩側期望值皆有限的範圍內，代入 $s=e^t$ 可得

$$
\begin{aligned}
M_X(t)
&=
\mathbb{E}(e^{tX}) \\[0.35em]
&=
\mathbb{E}[(e^t)^X] \\[0.35em]
&=
G_X(e^t)
\end{aligned}
$$

反過來，若 $s>0$ 且兩側皆有限，則

$$
G_X(s)=M_X(\log s)
$$

CGF 也可寫成

$$
K_X(t)
=
\log M_X(t)
=
\log G_X(e^t)
$$

這些等式都帶有定義域條件。$G_X(s)$ 在 $\lvert s\rvert\leqslant 1$ 必定存在，但當 $t>0$ 時，$e^t>1$，而 $G_X(e^t)$ 未必有限。這正是 $M_X(t)=G_X(e^t)$ 可能發散的原因。

<div id="example-220" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.20 (Waiting for the First Head)</div>

重複投擲一枚硬幣，每次出現正面的機率為 $p$，其中 $0<p\leqslant 1$。令 $Y$ 表第一次出現正面所需的投擲次數，並令 $q=1-p$。則

$$
\mathbb{P}(Y=y)=p q^{y-1},
\qquad y=1,2,3,\ldots
$$

由 PGF 的定義可得

$$
\begin{aligned}
G_Y(s)
&=
\sum_{y=1}^{\infty}s^y p q^{y-1} \\[0.35em]
&=
ps\sum_{y=1}^{\infty}(qs)^{y-1} \\[0.35em]
&=
\frac{ps}{1-qs}
\end{aligned}
$$

當 $0<p<1$ 時，幾何級數的收斂條件為

$$
\lvert qs\rvert<1
$$

若 $p=1$，則 $\mathbb{P}(Y=1)=1$，且 $G_Y(s)=s$。對 $0<p<1$ 微分可得

$$
G_Y'(s)=\frac{p}{(1-qs)^2},
\qquad
G_Y''(s)=\frac{2pq}{(1-qs)^3}
$$

將 $s=1$ 代入前兩階導數，可得 $\mathbb{E}(Y)=G_Y'(1)=1/p$。此外，二階階乘動差為

$$
\mathbb{E}[Y(Y-1)]
=
G_Y''(1)
=
\frac{2q}{p^2}
$$

由此可得

$$
\begin{aligned}
\mathrm{Var}(Y)
&=
G_Y''(1)+G_Y'(1)-[G_Y'(1)]^2 \\[0.35em]
&=
\frac{2q}{p^2}+\frac{1}{p}-\frac{1}{p^2} \\[0.35em]
&=
\frac{1-p}{p^2}
\end{aligned}
$$

同一個 PGF 也能給出 MGF 與 CGF。當 $0<p<1$ 且 $t<-\log q$ 時，

$$
M_Y(t)
=
G_Y(e^t)
=
\frac{pe^t}{1-qe^t}
$$

再取自然對數，可得

$$
K_Y(t)
=
\log p+t-\log(1-qe^t)
$$

其前兩階導數在 $t=0$ 的值為

$$
K_Y'(0)=\frac{1}{p},
\qquad
K_Y''(0)=\frac{1-p}{p^2}
$$

分別與 $\mathbb{E}(Y)$ 及 $\mathrm{Var}(Y)$ 相同。

</div>

## 本篇小結

若 $X$ 為非負整數值隨機變數，其 PGF 為

$$
G_X(s)=\mathbb{E}(s^X)
$$

PGF 在 $s=1$ 的左導數生成階乘動差，在 $s=0$ 的各階導數則取回 pmf 的係數。使用 $s=1$ 的導數時，必須確認對應的階乘動差有限。

若 MGF 在某個包含 $0$ 的開區間內有限，則 CGF 定義為

$$
K_X(t)=\log M_X(t)
$$

其前兩階累積量分別是期望值與變異數。對非負整數值隨機變數，$M_X(t)=G_X(e^t)$ 與 $G_X(s)=M_X(\log s)$ 只在兩側皆有限的範圍內成立。

[下一篇文章](/teaching-topics/characteristic-functions/)會介紹特徵函數 (characteristic function, CF)。把同一個 PGF 冪級數延伸到複數單位圓，並令 $s=e^{it}$，可得 $\varphi_X(t)=G_X(e^{it})$；其複指數項的絕對值恆為 $1$，因此 CF 對每個實值隨機變數都存在。

## 參考文獻與延伸閱讀

- 黃文璋，2003，《機率論》，初版，華泰文化。
- 黃文璋，2003，《數理統計》，初版，華泰文化。
- Patrick Billingsley. 1995. *Probability and Measure*. 3rd ed. Wiley.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Sheldon M. Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
