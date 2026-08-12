---
title: "獨立隨機變數"
subtitle: "Independent Random Variables"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 6
order: 306
permalink: /teaching-topics/independent-random-variables/
date: 2026-07-24
published: false
listed: false
excerpt: "若一個變數的取值不改變另一個變數的分配，兩者便獨立；聯合 cdf、pmf 或 pdf 也會分解為兩個邊際函數的乘積。"
---

[上一篇文章](/teaching-topics/conditional-distributions/)固定其中一個變數的取值，再觀察另一個變數的條件分配。在 [Example 3.7](/teaching-topics/conditional-distributions/#example-37) 中，$f_{X\mid Y}(x\mid y)=6x(1-x)$ 不隨 $y$ 改變，而且正好等於 $X$ 的邊際 pdf。這表示知道 $Y$ 的值，並沒有改變 $X$ 的分配。

在正式定義獨立性之前，先把聯合分配、條件分配與邊際分配之間的關係寫清楚。

## 乘法原理

<div id="theorem-31" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 3.1 (Multiplication Rule)</div>

令 $(X,Y)$ 為二元離散型隨機向量。對滿足 $p_Y(y)>0$ 的 $y$，以及任意 $x\in\mathcal{R}_X$，皆有

$$
p_{XY}(x,y)
=
p_{X\mid Y}(x\mid y)\,p_Y(y)
$$

對滿足 $p_X(x)>0$ 的 $x$，以及任意 $y\in\mathcal{R}_Y$，皆有

$$
p_{XY}(x,y)
=
p_{Y\mid X}(y\mid x)\,p_X(x)
$$

若 $(X,Y)$ 具有聯合 pdf，則對滿足 $f_Y(y)>0$ 的固定值 $y$，以及任意 <span class="text-nowrap">$x\in\mathbb{R}$，</span>皆有

$$
f_{XY}(x,y)
=
f_{X\mid Y}(x\mid y)\,f_Y(y)
$$

對滿足 $f_X(x)>0$ 的固定值 $x$，以及任意 $y\in\mathbb{R}$，則有

$$
f_{XY}(x,y)
=
f_{Y\mid X}(y\mid x)\,f_X(x)
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.** 離散型的兩個等式由 [Definition 3.8](/teaching-topics/conditional-distributions/#definition-38) 直接移項得到；具有聯合 pdf 時的兩個等式則由 [Definition 3.9](/teaching-topics/conditional-distributions/#definition-39) 直接移項得到。<span class="topic-qed">$\square$</span>
</div>

[Theorem 3.1](#theorem-31) 將第一章 [Theorem 1.13](/teaching-topics/conditional-probability-information/#theorem-18) 的乘法原理分別寫成聯合 pmf 與聯合 pdf 的形式。若條件 pmf 或條件 pdf 與相應的邊際函數相同，聯合 pmf 或聯合 pdf 便可進一步寫成兩個邊際函數的乘積。

## 獨立性的定義

<div id="definition-310" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 3.10</div>

令 $X$ 與 $Y$ 為定義在同一個機率空間上的兩個隨機變數。若對任意 Borel 集合 (Borel set) $A,B\subseteq\mathbb{R}$，皆有

$$
\mathbb{P}(X\in A,Y\in B)
=
\mathbb{P}(X\in A)\,
\mathbb{P}(Y\in B)
$$

則稱 $X$ 與 $Y$ 為**獨立隨機變數 (independent random variables)**，記為 $X\indep Y$。
</div>

[Definition 3.10](#definition-310) 把第一章的 [Definition 1.20](/teaching-topics/independence-and-conditional-independence/#definition-117) 推廣到隨機變數。它要求所有只由 $X$ 形成的事件，都與所有只由 $Y$ 形成的事件獨立，而不是只檢查一組特定取值。

<div id="proposition-35" class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Proposition 3.5 (Equivalent Conditions for Independence)</div>

對定義在同一個機率空間上的任意兩個隨機變數 $X$ 與 $Y$，下列兩項等價:

(1) $X\indep Y$。
{: .topic-paren-item}

(2) 對任意 $x,y\in\mathbb{R}$，皆有
{: .topic-paren-item}

$$
F_{XY}(x,y)
=
F_X(x)\,F_Y(y)
$$

若 $(X,Y)$ 為二元離散型隨機向量，則上述兩項也與下列三項等價:

(3) 對任意 $x\in\mathcal{R}_X$ 與 $y\in\mathcal{R}_Y$，皆有
{: .topic-paren-item}

$$
p_{XY}(x,y)
=
p_X(x)\,p_Y(y)
$$

(4) 對每個滿足 $p_Y(y)>0$ 的 $y$，以及每個 $x\in\mathcal{R}_X$，皆有
{: .topic-paren-item}

$$
p_{X\mid Y}(x\mid y)
=
p_X(x)
$$

(5) 對每個滿足 $p_X(x)>0$ 的 $x$，以及每個 $y\in\mathcal{R}_Y$，皆有
{: .topic-paren-item}

$$
p_{Y\mid X}(y\mid x)
=
p_Y(y)
$$

以下的幾乎處處 (almost everywhere, a.e.) 均是相對於相應的 Lebesgue 測度而言。若 $(X,Y)$ 具有聯合 pdf，則上述兩項也與下列三項等價:

(6) 對 $\mathbb{R}^2$ 中幾乎每個 $(x,y)$，皆有
{: .topic-paren-item}

$$
f_{XY}(x,y)
=
f_X(x)\,f_Y(y)
$$

(7) 對幾乎每個滿足 $f_Y(y)>0$ 的 $y$，皆有
{: .topic-paren-item}

$$
f_{X\mid Y}(x\mid y)
=
f_X(x)
$$

且此等式對幾乎每個 $x$ 成立。
{: .topic-paren-cont}

(8) 對幾乎每個滿足 $f_X(x)>0$ 的 $x$，皆有
{: .topic-paren-item}

$$
f_{Y\mid X}(y\mid x)
=
f_Y(y)
$$

且此等式對幾乎每個 $y$ 成立。
{: .topic-paren-cont}
</div>

<div class="topic-proof" markdown="1">
**Proof.** 若 $X\indep Y$，在 [Definition 3.10](#definition-310) 中取 $A=(-\infty,x]$ 與 <span class="text-nowrap">$B=(-\infty,y]$，</span>便得到 (2)。

反過來，令 $\mu$ 表示 $(X,Y)$ 的聯合分配，$\nu$ 表示 $X$ 與 $Y$ 的邊際分配所形成的乘積分配 (product distribution)。條件 (2) 表示 $\mu$ 與 $\nu$ 在所有左下矩形 $(-\infty,x]\times(-\infty,y]$ 上取相同的值。這些矩形形成一個 $\pi$-系統 ($\pi$-system)，並生成 $\mathbb{R}^2$ 上的 Borel $\sigma$-域，所以機率測度的唯一性給出 $\mu=\nu$。因此 (2) 推出 $X\indep Y$。

若 $(X,Y)$ 為離散型，由 [Definition 3.10](#definition-310) 對單點事件取 $A=\lbrace x\rbrace$ 與 $B=\lbrace y\rbrace$，即可由獨立性得到 (3)。反過來，若 (3) 成立，對任意 Borel 集合 $A,B\subseteq\mathbb{R}$，皆有

$$
\begin{aligned}
\mathbb{P}(X\in A,Y\in B)
&=
\sum_{\substack{x\in A\cap\mathcal{R}_X\\y\in B\cap\mathcal{R}_Y}}
p_{XY}(x,y) \\[0.4em]
&=
\sum_{\substack{x\in A\cap\mathcal{R}_X\\y\in B\cap\mathcal{R}_Y}}
p_X(x)\,p_Y(y) \\[0.4em]
&=
\left(
\sum_{x\in A\cap\mathcal{R}_X}p_X(x)
\right)
\left(
\sum_{y\in B\cap\mathcal{R}_Y}p_Y(y)
\right) \\[0.4em]
&=
\mathbb{P}(X\in A)\,
\mathbb{P}(Y\in B)
\end{aligned}
$$

因此 (3) 推出獨立性。將 (3) 除以正的 $p_Y(y)$ 或 $p_X(x)$，可分別得到 (4) 與 (5)。

反過來，若 (4) 成立，對 $p_Y(y)>0$ 的 $y$，由 [Theorem 3.1](#theorem-31) 可得

$$
p_{XY}(x,y)
=
p_X(x)\,p_Y(y)
$$

若 $p_Y(y)=0$，則

$$
\sum_{x\in\mathcal{R}_X}p_{XY}(x,y)
=
0
$$

由聯合 pmf 的非負性可知，每個 $p_{XY}(x,y)$ 都等於 $0$，而 $p_X(x)\,p_Y(y)$ 也等於 $0$。因此 (4) 推出 (3)。由 (5) 推出 (3) 的證明只須交換 $X$ 與 $Y$。

若 $(X,Y)$ 具有聯合 pdf，且 $X\indep Y$，則乘積分配具有聯合 pdf $f_X(x)\,f_Y(y)$。由聯合 pdf 在 Lebesgue 幾乎處處意義下的唯一性，可得 (6)。

反過來，若 (6) 成立，對任意 Borel 集合 $A,B\subseteq\mathbb{R}$，皆有

$$
\begin{aligned}
\mathbb{P}(X\in A,Y\in B)
&=
\int_A\int_B
f_X(x)\,f_Y(y)\,dy\,dx \\[0.4em]
&=
\left(
\int_A f_X(x)\,dx
\right)
\left(
\int_B f_Y(y)\,dy
\right) \\[0.4em]
&=
\mathbb{P}(X\in A)\,
\mathbb{P}(Y\in B)
\end{aligned}
$$

所以 $X\indep Y$。

再由 Fubini 定理 (Fubini’s theorem) 可知，若 (6) 成立，則對幾乎每個 $y$，密度乘積公式對幾乎每個 $x$ 成立。對其中滿足 $f_Y(y)>0$ 的 $y$，將該公式除以 $f_Y(y)$，便得到 (7)。交換 $X$ 與 $Y$，即可得到 (8)。

反過來，若 (7) 成立，令

$$
\begin{aligned}
m_Y(y)
&=
\int_{-\infty}^{\infty}f_{XY}(x,y)\,dx
\\[0.4em]
E_Y
&=
\bigl\{
y\in\mathbb{R}
\mid
f_Y(y)\neq m_Y(y)
\bigr\}
\end{aligned}
$$

依 [Definition 3.6](/teaching-topics/region-probabilities-marginal-distributions/#definition-36)，$E_Y$ 的長度為 $0$。再令 $G_Y$ 為條件 (7) 所允許的 $y$ 例外集合，則 $G_Y$ 的長度也為 $0$。

對每個 $y\notin E_Y\cup G_Y$，若 $f_Y(y)>0$，則由 [Theorem 3.1](#theorem-31) 與條件 (7) 可得

$$
f_{XY}(x,y)
=
f_X(x)\,f_Y(y)
$$

對幾乎每個 $x$ 成立。若 $f_Y(y)=0$，則

$$
\int_{-\infty}^{\infty}f_{XY}(x,y)\,dx
=
m_Y(y)
=
f_Y(y)
=
0
$$

由 $f_{XY}\geqslant0$ 可知，$f_{XY}(x,y)=0=f_X(x)\,f_Y(y)$ 對幾乎每個 $x$ 成立。

令

$$
N
=
\bigl\{
(x,y)\in\mathbb{R}^2
\mid
f_{XY}(x,y)\neq f_X(x)\,f_Y(y)
\bigr\}
$$

對每個 $y\notin E_Y\cup G_Y$，截面 $N_y=\lbrace x\in\mathbb{R}\mid(x,y)\in N\rbrace$ 的長度皆為 $0$。令 $\lambda_1$ 與 $\lambda_2$ 分別表示一維長度與二維面積。由 Tonelli 定理 (Tonelli’s theorem) 可得

$$
\lambda_2(N)
=
\int_{\mathbb{R}}\lambda_1(N_y)\,dy
=
0
$$

因此 (6) 成立。

若 (8) 成立，則令

$$
\begin{aligned}
m_X(x)
&=
\int_{-\infty}^{\infty}f_{XY}(x,y)\,dy
\\[0.4em]
E_X
&=
\bigl\{
x\in\mathbb{R}
\mid
f_X(x)\neq m_X(x)
\bigr\}
\end{aligned}
$$

依 [Definition 3.6](/teaching-topics/region-probabilities-marginal-distributions/#definition-36)，$E_X$ 的長度為 $0$。再排除條件 (8) 所允許的 $x$ 例外集合，並對集合 $N$ 的水平截面重複上一段的 Tonelli 論證，即可由 (8) 得到 (6)。<span class="topic-qed">$\square$</span>
</div>

在離散型情形中，只要找到一組 $(x,y)$ 不滿足 $p_{XY}(x,y)=p_X(x)\,p_Y(y)$，便可判定 $X$ 與 $Y$ 不獨立；若要證明獨立，則必須檢查所有可能配對。這種單點檢查可以成立，是因為一般事件的機率可由單點機率加總得到。

具有聯合 pdf 時，每個單點的機率都是 $0$，所以逐一檢查單點事件不能分辨是否獨立。此時必須比較聯合 pdf 與邊際 pdf 的乘積是否在二維幾乎處處相等，或直接回到聯合 cdf 與事件機率的定義。

對明確給定的聯合 pdf，可使用以下充分條件證明獨立。以 $\mathbf{1}_D$ 表示集合 $D$ 的**指標函數 (indicator function)**，即輸入屬於 $D$ 時函數值為 $1$，否則為 $0$。若存在 Borel 集合 $D_X,D_Y\subseteq\mathbb{R}$ 與非負 Borel 可測函數 $g,h$，且下列等式除了某個二維面積為 $0$ 的集合之外皆成立，便可由此證明獨立性。

$$
f_{XY}(x,y)
=
g(x)\,h(y)\,
\mathbf{1}_{D_X}(x)\,
\mathbf{1}_{D_Y}(y)
$$

令

$$
a
=
\int_{D_X}g(x)\,dx,
\qquad
b
=
\int_{D_Y}h(y)\,dy
$$

由 Tonelli 定理與聯合 pdf 的總積分為 $1$，可知 $0<a,b<\infty$，且 $ab=1$。對幾乎每個 $x\in\mathbb{R}$ 與幾乎每個 $y\in\mathbb{R}$，分別有

$$
\begin{aligned}
f_X(x)
&=
bg(x)\mathbf{1}_{D_X}(x)
\\[0.4em]
f_Y(y)
&=
ah(y)\mathbf{1}_{D_Y}(y)
\end{aligned}
$$

所以

$$
\begin{aligned}
f_X(x)\,f_Y(y)
&=
ab\,g(x)\,h(y)\,
\mathbf{1}_{D_X}(x)\,
\mathbf{1}_{D_Y}(y) \\[0.4em]
&=
f_{XY}(x,y)
\end{aligned}
$$

在二維幾乎處處成立。因此，由 [Proposition 3.5](#proposition-35) 可知 <span class="text-nowrap">$X\indep Y$。</span>這是一項方便使用的充分條件；若聯合 pdf 無法直接寫成此形式，不能只憑這一點判定不獨立，仍須比較 $f_{XY}$ 與 <span class="text-nowrap">$f_X\,f_Y$。</span>

## 聯合 pdf 的分解與非零範圍

<div id="example-39" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.9 (Factorization and the Nonzero Region)</div>

先考慮 [Example 3.3](/teaching-topics/joint-probability-density-functions/#example-33) 的聯合 pdf:

$$
f_{XY}(x,y)
=
12xy(1-x),
\qquad
0<x<1,\ 0<y<1
$$

由 [Example 3.7](/teaching-topics/conditional-distributions/#example-37) 已知 $f_Y(y)=2y$。同理可得

$$
f_X(x)
=
\int_0^1 12xy(1-x)\,dy
=
6x(1-x)
$$

因此在矩形範圍 $(0,1)\times(0,1)$ 內，

$$
f_{XY}(x,y)
=
\bigl[6x(1-x)\bigr](2y)
=
f_X(x)\,f_Y(y)
$$

範圍外的聯合 pdf 與兩個邊際 pdf 的乘積也都為 $0$，所以由 [Proposition 3.5](#proposition-35) 可知 $X\indep Y$。

接著令 $(U,V)$ 具有聯合 pdf

$$
f_{UV}(u,v)
=
\begin{cases}
24uv, & u>0,\ v>0,\ u+v<1,\\
0, & \text{其他}
\end{cases}
$$

先檢查整個三角形範圍上的積分，可得

$$
\int_0^1\int_0^{1-u}24uv\,dv\,du
=
12\int_0^1u(1-u)^2\,du
=
1
$$

因此，$f_{UV}$ 確實是一個聯合 pdf。

在三角形內，$24uv$ 可拆成一個只含 $u$ 的函數與一個只含 $v$ 的函數。不過，完整的聯合 pdf 還包含條件 $u+v<1$，而這個非零範圍不能寫成兩個單變數範圍的乘積。

由積分可得

$$
f_U(u)
=
\begin{cases}
12u(1-u)^2, & 0<u<1,\\
0, & \text{其他}
\end{cases}
$$

以及

$$
f_V(v)
=
\begin{cases}
12v(1-v)^2, & 0<v<1,\\
0, & \text{其他}
\end{cases}
$$

考慮 $0<u<1$、$0<v<1$ 且 $u+v>1$ 的右上三角形。在這個正面積區域上，$f_{UV}(u,v)=0$，但 $f_U(u)\,f_V(v)>0$。因此，聯合 pdf 與邊際 pdf 的乘積並非只在面積為 $0$ 的集合上不同，由 [Proposition 3.5](#proposition-35) 可知 $U$ 與 $V$ 不獨立。
</div>

第二個例子說明，只看範圍內顯示的代數式並不夠。完整的聯合 pdf 應連同非零範圍一起檢查。

## 多個隨機變數的獨立

<div id="definition-311" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 3.11</div>

令 $n\geqslant2$，且令 $X_1,\ldots,X_n$ 為定義在同一個機率空間上的隨機變數。若對任意 Borel 集合 $A_1,\ldots,A_n\subseteq\mathbb{R}$，皆有

$$
\mathbb{P}
\left(
\bigcap_{i=1}^{n}
\lbrace X_i\in A_i\rbrace
\right)
=
\prod_{i=1}^{n}
\mathbb{P}(X_i\in A_i)
$$

則稱 $X_1,\ldots,X_n$ 為**完全獨立 (mutually independent)**。
</div>

這項定義與第一章的 [Definition 1.21](/teaching-topics/independence-and-conditional-independence/#definition-118) 一致。若只想檢查某個子群，可令其餘指標所對應的 $A_i=\mathbb{R}$；這些項在交集內不增加限制，在乘積中則提供因子 $\mathbb{P}(X_i\in\mathbb{R})=1$。因此，[Definition 3.11](#definition-311) 同時包含所有子群的獨立條件。

只檢查任意兩個變數，得到的是**成對獨立 (pairwise independent)**。成對獨立一般不能推出完全獨立，第一章的 [Example 1.22](/teaching-topics/independence-and-conditional-independence/#example-pairwise-not-mutual) 已說明這項差異。

## 本篇小結

獨立性表示，一個變數所形成的事件不會改變另一個變數所形成事件的機率。對聯合 cdf，這等價於 $F_{XY}=F_XF_Y$；在離散型與具有聯合 pdf 的情形中，則分別對應 pmf 與 pdf 的乘積分解。

檢查聯合 pdf 時，必須同時查看代數式與非零範圍。若非零範圍是兩個 Borel 集合的乘積，且密度可依兩個座標分解，便可使用前述充分條件證明獨立；若非零範圍本身使 $x$ 與 $y$ 彼此限制，即使範圍內的公式看似可以拆開，也不能據此判定獨立。

下一篇會在聯合分配下定義多元隨機變數的期望值，並比較獨立性如何使乘積函數的期望值進一步分解。

## 參考文獻與延伸閱讀

- 黃文璋，2003，《數理統計》，初版，華泰文化。
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Joseph K. Blitzstein and Jessica Hwang. 2019. *Introduction to Probability*. 2nd ed. Chapman and Hall/CRC.
