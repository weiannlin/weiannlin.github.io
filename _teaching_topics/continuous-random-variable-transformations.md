---
title: "連續型隨機變數的函數轉換"
subtitle: "Transformations of Continuous Random Variables"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 21
order: 221
permalink: /teaching-topics/continuous-random-variable-transformations/
date: 2026-07-13
published: true
excerpt: "連續型隨機變數經函數轉換後，可先由事件原像求 CDF；在一對一、連續可微且導數不為 $0$ 等條件下，也可使用 Jacobian 法求 pdf。多對一轉換則須分段並加總各原像分支。"
---

[上一篇文章](/teaching-topics/discrete-random-variable-transformations/)說明離散型轉換的 pmf 來自**原像 (preimage)** 的機率加總。轉換後事件的機率由該事件在 $X$ 下的原像決定。對離散型隨機變數，可加總各原像的 pmf；對連續型隨機變數，因為單點機率皆為 $0$，必須改由累積分配函數處理，或在適當條件下使用 **Jacobian 法 (Jacobian method)**，亦稱亞可比法，轉換機率密度函數。

以下令 $X$ 為具有 pdf $f_X$ 與 CDF $F_X$ 的連續型隨機變數，並令 $Y=g(X)$，其中 $g$ 為 **Borel 可測函數 (Borel measurable function)**；其可測性條件可回顧[上一篇的 Theorem 2.9](/teaching-topics/discrete-random-variable-transformations/#theorem-29)。

若轉換後的 MGF 在 $0$ 附近存在，[上一篇介紹的 MGF 法](/teaching-topics/discrete-random-variable-transformations/#mgf-法與線性轉換)也可用來辨認分配，而且不受離散型或連續型的限制。本篇集中整理 CDF 法與 Jacobian 法。

## CDF 法

CDF 法把事件 $\lbrace g(X)\leqslant y\rbrace$ 改寫為以 $X$ 表示的等價事件，再找出所有滿足 $g(x)\leqslant y$ 的 $x$ 所形成的範圍。這個作法不要求 $g$ 一對一，也不要求 $g$ 可微。以下以 $\mathcal{R}_X$ 表示 $X$ 的**值域 (range)**。

<div id="proposition-216" class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Proposition 2.16 (CDF Method)</div>

對任意 $y\in\mathbb{R}$，令

$$
\begin{aligned}
A_y
&=
g^{-1}\bigl((-\infty,y]\bigr)
\\[0.35em]
&=
\lbrace x\in\mathbb{R}\mid g(x)\leqslant y\rbrace
\end{aligned}
$$

記號 $g^{-1}\bigl((-\infty,y]\bigr)$ 表示集合 $(-\infty,y]$ 在 $g$ 下的原像，不要求 $g$ 具有反函數。因為 $\lbrace Y\leqslant y\rbrace$、$\lbrace g(X)\leqslant y\rbrace$ 與 $\lbrace X\in A_y\rbrace$ 是同一個事件，所以

$$
F_Y(y)
=
\mathbb{P}(X\in A_y)
=
\int_{A_y}f_X(x)\,dx
$$

若對固定的 $y$，$A_y$ 可寫成有限個互不相交區間的聯集，令 $m$ 表示區間個數，並令 $I_j(y)$ 表示其中第 $j$ 個區間，$j=1,\ldots,m$。此時 $A_y$ 可寫為

$$
A_y
=
\bigcup_{j=1}^{m}I_j(y)
$$

由積分的可加性可得

$$
F_Y(y)
=
\sum_{j=1}^{m}\int_{I_j(y)}f_X(x)\,dx
$$

以下進一步考慮一般 CDF 公式的兩個特例，分別是 $g$ 在 $X$ 的值域上嚴格遞增與嚴格遞減。令 $D=\mathcal{R}_X$。若 $g$ 在 $D$ 上嚴格單調，則限制函數 $g\vert_D:D\to g(D)$ 具有反函數。以下的 $g^{-1}(y)$ 專指此反函數在 $y$ 的值。對每個 $y\in g(D)$，若 $g$ 在 $D$ 上嚴格遞增，則

$$
F_Y(y)
=
F_X\bigl(g^{-1}(y)\bigr)
$$

若 $g$ 在 $D$ 上嚴格遞減，則

$$
F_Y(y)
=
1-F_X\bigl(g^{-1}(y)-\bigr)
$$

其中 $F_X(a-)$ 表示 $F_X$ 在 $a$ 的左極限。因 $F_X$ 連續，亦可寫成 $F_Y(y)=1-F_X(g^{-1}(y))$。

</div>

<div class="topic-proof" markdown="1">
**Proof.** 由 $g$ 的 Borel 可測性可知，$A_y$ 為 Borel 集合。再由事件原像可得

$$
\lbrace Y\leqslant y\rbrace
=
\lbrace g(X)\leqslant y\rbrace
=
\lbrace X\in A_y\rbrace
$$

因此

$$
F_Y(y)
=
\mathbb{P}(X\in A_y)
=
\int_{A_y}f_X(x)\,dx
$$

若 $A_y$ 是互不相交區間 $I_1(y),\ldots,I_m(y)$ 的聯集，積分的可加性便給出各區間積分的總和。

若 $g$ 在 $D$ 上嚴格遞增，則在 $X\in D$ 的情況下，$g(X)\leqslant y$ 等價於 $X\leqslant g^{-1}(y)$。由 $\mathbb{P}(X\in D)=1$ 可得

$$
F_Y(y)
=
F_X\bigl(g^{-1}(y)\bigr)
$$

若 $g$ 在 $D$ 上嚴格遞減，則在 $X\in D$ 的情況下，$g(X)\leqslant y$ 等價於 $X\geqslant g^{-1}(y)$。由 $\mathbb{P}(X\in D)=1$ 可得

$$
F_Y(y)
=
1-F_X\bigl(g^{-1}(y)-\bigr)
$$

因 $F_X$ 連續，後一式可化為 $F_Y(y)=1-F_X\bigl(g^{-1}(y)\bigr)$。$\square$
</div>

當 $g$ 在 $\mathcal{R}_X$ 上不是一對一時，不能把 $X$ 寫成單一的 $g^{-1}(Y)$。對每個 $y$，應先解不等式 $g(x)\leqslant y$，找出所有滿足此不等式的 $x$；這些 $x$ 所形成的集合就是 $A_y$，接著在 $A_y$ 上積分即可。[Example 2.32](#example-232) 中的 $Y=X^2$ 會實際使用這個方法。

反函數式只在 $Y$ 的值域內使用。若 $y$ 小於 $Y$ 的所有可能取值，則 $F_Y(y)=0$；若 $y$ 大於或等於所有可能取值，則 $F_Y(y)=1$。求 CDF 時應先決定轉換後的取值範圍，再分段處理。

<div id="interlude-223" class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 2.23</div>

連續型 $X$ 經函數轉換後，$Y=g(X)$ 未必仍是連續型。若 $g$ 在一段具有正機率的區間上為常數，那一整段機率會集中到 $Y$ 的單一取值。

例如令 $X$ 為關於 $0$ 對稱的連續型隨機變數，並令 $Y=\mathbf{1}_{\lbrace X>0\rbrace}$。則 $Y$ 只取 $0$ 與 $1$，而且兩者機率皆為 $1/2$。因此，由 $F_Y$ 微分取得 pdf 之前，必須先確認轉換後的分配確實為**絕對連續 (absolutely continuous)**。
</div>

## 一對一轉換與 Jacobian

在 [Proposition 2.17](#proposition-217) 的條件下，可以由 CDF 公式微分，得到轉換後的 pdf。微分時出現的反函數導數絕對值，就是一維 Jacobian。

這與微積分的變數代換公式相同。在該公式中，Jacobian 行列式的絕對值是體積轉換因子，用來調整長度、面積或體積的變化；本篇是一維情形，所調整的就是區間長度。若 $\Delta x$ 與 $\Delta y$ 分別表示在 $x$ 與 $y=g(x)$ 附近相互對應的小區間長度，則局部有

$$
\Delta y
\approx
\lvert g^{\prime}(x)\rvert\,\Delta x,
\qquad
\Delta x
\approx
\left\lvert
\frac{d}{dy}g^{-1}(y)
\right\rvert\,\Delta y
$$

函數 $g$ 的導數絕對值把 $x$ 軸上的長度轉成 $y$ 軸上的長度；反函數 $g^{-1}$ 的導數絕對值則把 $y$ 軸上的長度換回原像在 $x$ 軸上的長度。密度轉換使用後者，因為 $Y$ 落在 $y$ 軸小區間內的機率，等於 $X$ 落在該區間原像內的機率。

<div id="proposition-217" class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Proposition 2.17 (One-to-One Jacobian Formula)</div>

令 $X$ 的 pdf 為 $f_X$，且 $\mathbb{P}(X\in D)=1$，其中 $D$ 為一個開區間。假設 $f_X$ 在 $D$ 上連續，$g$ 在 $D$ 上嚴格單調且連續可微，並滿足

$$
g^{\prime}(x)\neq 0,
\qquad
x\in D
$$

令 $E=g(D)$。若 $Y=g(X)$，則 $Y$ 的 pdf 為

$$
f_Y(y)
=
f_X\bigl(g^{-1}(y)\bigr)
\left\lvert
\frac{d}{dy}g^{-1}(y)
\right\rvert,
\qquad
y\in E
$$

對 $y\notin E$，可取 $f_Y(y)=0$。

</div>

<div class="topic-proof" markdown="1">
**Proof.** 若 $g$ 嚴格遞增，則由 [Proposition 2.16](#proposition-216) 可得

$$
F_Y(y)=F_X\bigl(g^{-1}(y)\bigr)
$$

對 $y$ 微分可得

$$
f_Y(y)
=
f_X\bigl(g^{-1}(y)\bigr)
\frac{d}{dy}g^{-1}(y)
$$

此時反函數導數為正。若 $g$ 嚴格遞減，CDF 公式前方會出現 $1-$，反函數導數則為負；兩個負號相消，最後同樣得到導數的絕對值。又由 $\mathbb{P}(X\in D)=1$ 及 $E=g(D)$ 可知 $\mathbb{P}(Y\in E)=1$，所以在 $E$ 以外可取 $f_Y(y)=0$。$\square$
</div>

因此，Jacobian 的絕對值不可省略。它調整局部區間長度的變化，使轉換後密度的積分仍為 $1$。

## 多對一轉換與單調分支

若 $g$ 在 $\mathcal{R}_X$ 上不是一對一，同一個 $y$ 可能有多個原像。此時可將 $\mathcal{R}_X$ 分成若干單調分支，先在每個分支上使用 [Proposition 2.17](#proposition-217)，再將各分支所得的密度相加。

具體而言，可取有限個互不相交的開區間 $D_1,\ldots,D_m$，使 $\mathbb{P}(X\in D_1\cup\cdots\cup D_m)=1$。再假設 $f_X$ 在每個 $D_j$ 上連續，且 $g$ 在每個 $D_j$ 上嚴格單調、連續可微且導數不為 $0$。令 $g_j=g\vert_{D_j}$，且 $E_j=g(D_j)$。

若 $y\in E_1\cup\cdots\cup E_m$，則轉換後密度為

$$
f_Y(y)
=
\sum_{\substack{1\leqslant j\leqslant m\\y\in E_j}}
f_X\bigl(g_j^{-1}(y)\bigr)
\left\lvert
\frac{d}{dy}g_j^{-1}(y)
\right\rvert
$$

對 $y\notin E_1\cup\cdots\cup E_m$，可取 $f_Y(y)=0$。由反函數微分公式，若 $x=g_j^{-1}(y)$，則

$$
\left\lvert
\frac{d}{dy}g_j^{-1}(y)
\right\rvert
=
\frac{1}{\lvert g^{\prime}(x)\rvert}
$$

因此，若方程式 $g(x)=y$ 只有有限個根，且每個根都滿足 $g^{\prime}(x)\neq 0$，也可寫成

$$
f_Y(y)
=
\sum_{\substack{x\in D_1\cup\cdots\cup D_m\\g(x)=y}}
\frac{f_X(x)}{\lvert g^{\prime}(x)\rvert}
$$

<div id="note-piecewise-jacobian" class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

多對一公式加總的是所有滿足 $y\in E_j$ 的原像分支。不同分支的值域可能不同，所以原像數量也可能隨 $y$ 改變。

若某個原像 $x$ 滿足 $g^{\prime}(x)=0$，依方程式 $g(x)=y$ 的各根加總之公式便不能在該處直接使用。轉換後密度可能在臨界值附近趨向無窮，但 pdf 在單一點的取值不影響機率分配。此時可先用 CDF 法求出分配，再在可微區間內求導數。
</div>

## 一對一遞減轉換

<div id="example-231" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.31 (A Reciprocal Transformation)</div>

令 $X$ 的 pdf 為

$$
f_X(x)
=
\left\{
\begin{array}{c@{\quad}l}
2x, & 0<x<1 \\[0.35em]
0, & \text{otherwise}
\end{array}
\right.
$$

並令 $Y=1/X$。

由 $\mathbb{P}(0<X<1)=1$ 可知 $\mathbb{P}(Y>1)=1$。先用 CDF 法。對 $y\leqslant 1$，有 $F_Y(y)=0$；對 $y>1$，由 $x\mapsto 1/x$ 嚴格遞減可得

$$
\begin{aligned}
F_Y(y)
&=
\mathbb{P}\left(\frac{1}{X}\leqslant y\right) \\[0.35em]
&=
\mathbb{P}\left(X\geqslant\frac{1}{y}\right) \\[0.35em]
&=
1-F_X\left(\frac{1}{y}\right)
\end{aligned}
$$

在 $0<x<1$ 上，$X$ 的 CDF 可寫為

$$
F_X(x)
=
\int_0^x 2t\,dt
=
x^2
$$

將 $F_X(1/y)=1/y^2$ 代回，可得

$$
F_Y(y)
=
\left\{
\begin{array}{c@{\quad}l}
0, & y\leqslant 1 \\[0.35em]
1-\dfrac{1}{y^2}, & y>1
\end{array}
\right.
$$

在 $y>1$ 上微分可得

$$
f_Y(y)
=
\frac{2}{y^3}
$$

再使用 [Proposition 2.17](#proposition-217) 檢查。反函數與導數分別為 $x=g^{-1}(y)=1/y$ 與 $dx/dy=-1/y^2$。因 $y>1$，所以 $1/y\in(0,1)$，可代入 $f_X(x)=2x$。因此

$$
\begin{aligned}
f_Y(y)
&=
f_X\left(\frac{1}{y}\right)
\left\lvert-\frac{1}{y^2}\right\rvert \\[0.35em]
&=
\frac{2}{y}\frac{1}{y^2}
=
\frac{2}{y^3}
\end{aligned}
$$

這個例子也可與函數期望值公式比較。直接沿著 $X$ 的 pdf 計算可得

$$
\mathbb{E}\left(\frac{1}{X}\right)
=
\int_0^1\frac{1}{x}2x\,dx
=
2
$$

沿著 $Y$ 的 pdf 計算則有

$$
\mathbb{E}(Y)
=
\int_1^\infty y\frac{2}{y^3}\,dy
=
2
$$

</div>

## 原像數量改變的多對一轉換

<div id="example-232" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.32 (A Piecewise Square Transformation)</div>

令 $X\sim\mathcal{U}(-2,1)$，亦即 $X$ 在 $(-2,1)$ 上服從均勻分配。因此

$$
f_X(x)
=
\left\{
\begin{array}{c@{\quad}l}
\dfrac{1}{3}, & -2<x<1 \\[0.35em]
0, & \text{otherwise}
\end{array}
\right.
$$

令 $Y=X^2$。由 $\mathbb{P}(-2<X<1)=1$ 可知 $\mathbb{P}(0\leqslant Y<4)=1$。函數 $x\mapsto x^2$ 在 $(-2,1)$ 上不是一對一。以下先把事件 $\lbrace X^2\leqslant y\rbrace$ 改寫為等價的 $X$ 取值範圍，再對該範圍積分。

當 $0\leqslant y<1$ 時，正、負平方根都落在 $X$ 的取值範圍內，所以

$$
\begin{aligned}
F_Y(y)
&=
\mathbb{P}(X^2\leqslant y) \\[0.35em]
&=
\mathbb{P}(-\sqrt{y}\leqslant X\leqslant\sqrt{y}) \\[0.35em]
&=
\int_{-\sqrt{y}}^{\sqrt{y}}\frac{1}{3}\,dx
=
\frac{2\sqrt{y}}{3}
\end{aligned}
$$

當 $1\leqslant y<4$ 時，正平方根 $\sqrt{y}$ 已不落在 $-2<X<1$ 的範圍內，所以

$$
\begin{aligned}
F_Y(y)
&=
\mathbb{P}(X^2\leqslant y) \\[0.35em]
&=
\mathbb{P}(-\sqrt{y}\leqslant X<1) \\[0.35em]
&=
\int_{-\sqrt{y}}^{1}\frac{1}{3}\,dx
=
\frac{1+\sqrt{y}}{3}
\end{aligned}
$$

合併各區間後，$Y$ 的 CDF 為

$$
F_Y(y)
=
\left\{
\begin{array}{c@{\quad}l}
0, & y<0 \\[0.35em]
\dfrac{2\sqrt{y}}{3}, & 0\leqslant y<1 \\[0.35em]
\dfrac{1+\sqrt{y}}{3}, & 1\leqslant y<4 \\[0.35em]
1, & y\geqslant 4
\end{array}
\right.
$$

在各可微區間求導數可得

$$
f_Y(y)
=
\left\{
\begin{array}{c@{\quad}l}
\dfrac{1}{3\sqrt{y}}, & 0<y<1 \\[0.35em]
\dfrac{1}{6\sqrt{y}}, & 1<y<4 \\[0.35em]
0, & \text{otherwise}
\end{array}
\right.
$$

Jacobian 法會得到相同結果。正分支 $x=\sqrt{y}$ 只在 $0<y<1$ 存在，貢獻為

$$
f_X(\sqrt{y})
\left\lvert
\frac{d\sqrt{y}}{dy}
\right\rvert
=
\frac{1}{6\sqrt{y}}
$$

負分支 $x=-\sqrt{y}$ 在 $0<y<4$ 存在，貢獻為

$$
f_X(-\sqrt{y})
\left\lvert
\frac{d(-\sqrt{y})}{dy}
\right\rvert
=
\frac{1}{6\sqrt{y}}
$$

因此，$0<y<1$ 時兩個分支相加，得到 $1/(3\sqrt{y})$；$1<y<4$ 時只有負分支，得到 $1/(6\sqrt{y})$。

在 $y=0$ 時，上式含有 $1/\sqrt{y}$，不能直接代入；在 $y=1$ 時，CDF 的左右導數不同。pdf 在這兩個單點取任何有限值都不會改變任何區間機率，因此可把公式限定在上列開區間。
</div>

## 機率積分轉換

以下結果稱為**機率積分轉換 (probability integral transform)**。

均勻分配 (uniform distribution) 將在後面的主題中另行介紹。此處只先使用其中的標準均勻分配 (standard uniform distribution)。若 $U\sim\mathcal{U}(0,1)$，則當 $0\leqslant u\leqslant 1$ 時，其 CDF 滿足 $F_U(u)=u$。

<!-- ref-point: 待均勻分配主題發布後，將「後面的主題」改為指向該篇文章的站內連結。 -->

<div id="proposition-218" class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Proposition 2.18 (Probability Integral Transform)</div>

若 $F_X$ 連續，令 $U=F_X(X)$，則 $U\sim\mathcal{U}(0,1)$。

反過來，令 $F$ 為任意 CDF，且 $U\sim\mathcal{U}(0,1)$。其中 $F^{-1}$ 為[廣義分位函數](/teaching-topics/quantiles-and-median/#累積機率與分位數)，對 $0<u<1$ 定義為

$$
F^{-1}(u)
=
\inf\lbrace x\in\mathbb{R}\mid F(x)\geqslant u\rbrace
$$

上式不直接定義 $u=0$ 與 $u=1$。當 $u=0$ 時，每個 CDF 都滿足 $F(x)\geqslant 0$，因此定義集合是 $\mathbb{R}$，其下確界為 $-\infty$。當 $u=1$ 時，若 $F(x)$ 只在 $x\to\infty$ 時趨近於 $1$，定義集合便是空集合；在這兩種情況下，公式都不能得到有限的實數值。為使 $F^{-1}$ 在 $[0,1]$ 上都有實數值，可另為 $F^{-1}(0)$ 與 $F^{-1}(1)$ 指定任意有限值。由於 $\mathbb{P}\bigl(U\in\lbrace 0,1\rbrace\bigr)=0$，這兩個指定值不影響 $F^{-1}(U)$ 的分配。

令 $Y=F^{-1}(U)$，則 $Y$ 的 CDF 為 $F$。

</div>

<div class="topic-proof" markdown="1">
**Proof.** 先證明第一個方向。對 $0<u<1$，令

$$
q_u
=
F_X^{-1}(u)
=
\inf\lbrace x\in\mathbb{R}\mid F_X(x)\geqslant u\rbrace
$$

令 $A_u=\lbrace x\in\mathbb{R}\mid F_X(x)\geqslant u\rbrace$，則 $q_u=\inf A_u$。若 $x<q_u$，則 $x\notin A_u$，所以 $F_X(x)<u$。另一方面，對每個正整數 $n$，由下確界的定義可取 $x_n\in A_u$，使 $q_u\leqslant x_n<q_u+1/n$。由 $F_X$ 的單調性可得

$$
F_X(q_u+1/n)
\geqslant
F_X(x_n)
\geqslant
u
$$

由 $x<q_u$ 時 $F_X(x)<u$ 可得 $F_X(q_u-)\leqslant u$；令 $n\to\infty$，再利用 $F_X$ 的連續性，可由上式得到 $F_X(q_u)\geqslant u$。因為 $F_X(q_u-)=F_X(q_u)$，所以兩者都等於 $u$。因此，$F_X(x)<u$ 若且唯若 $x<q_u$，也就是 $\lbrace F_X(X)<u\rbrace=\lbrace X<q_u\rbrace$。由此可得

$$
\begin{aligned}
\mathbb{P}(U<u)
&=
\mathbb{P}(X<q_u) \\[0.35em]
&=
F_X(q_u-) \\[0.35em]
&=
u
\end{aligned}
$$

取正整數 $N$，使 $u+1/N<1$。對每個 $n\geqslant N$，考慮事件 $\lbrace U<u+1/n\rbrace$；當 $n\to\infty$ 時，這些事件遞減至 $\lbrace U\leqslant u\rbrace$。由機率的連續性可得

$$
\begin{aligned}
\mathbb{P}(U\leqslant u)
&=
\lim_{n\to\infty}\mathbb{P}(U<u+1/n) \\[0.35em]
&=
\lim_{n\to\infty}(u+1/n) \\[0.35em]
&=
u
\end{aligned}
$$

又因為 $U\in[0,1]$，所以 $U\sim\mathcal{U}(0,1)$。

反過來，$F^{-1}$ 在 $(0,1)$ 上為非遞減函數，所以是 Borel 可測函數；在端點任意指定有限值仍保持可測性。因此，$Y=F^{-1}(U)$ 為隨機變數。又因為 $\mathbb{P}(0<U<1)=1$，所以端點取值不影響 $Y$ 的分配。

對 $0<u<1$，若 $u\leqslant F(y)$，則 $y$ 位於 $F^{-1}(u)$ 的定義集合內，所以 $F^{-1}(u)\leqslant y$。反過來，令 $q=F^{-1}(u)$，並假設 $q\leqslant y$。由下確界的定義，對每個正整數 $n$ 都可取 $x_n$，使

$$
q
\leqslant
x_n
<
q+1/n,
\qquad
F(x_n)
\geqslant
u
$$

若 $q<y$，可取足夠大的 $n$，使 $x_n<y$，再由單調性得到 $u\leqslant F(y)$。若 $q=y$，則令 $n\to\infty$，並利用 $F$ 的右連續性，同樣可得 $u\leqslant F(y)$。因此，對每個 $0<u<1$，皆有

$$
F^{-1}(u)\leqslant y
\quad\Longleftrightarrow\quad
u\leqslant F(y)
$$

由上述事件的等價關係可得

$$
\mathbb{P}(Y\leqslant y)
=
\mathbb{P}(U\leqslant F(y))
=
F(y)
$$

因此，$F^{-1}(U)$ 具有 CDF $F$。$\square$
</div>

[Proposition 2.18](#proposition-218) 把不同分配與標準均勻分配連結起來。第一個方向可將具有連續 CDF 的隨機變數轉換為 $\mathcal{U}(0,1)$；第二個方向則由 $\mathcal{U}(0,1)$ 生成具有任意指定 CDF 的實值隨機變數。

這個性質可用來模擬隨機變數。一般的亂數產生器 (random number generator) 通常先提供 $0$ 與 $1$ 之間的均勻亂數。若目標分配的 CDF 為 $F$，則將每個均勻亂數 $u$ 轉換為 $F^{-1}(u)$；反覆進行後，即可得到來自該分配的一組模擬值。對有單點機率的分配，CDF 的跳躍會使一整段 $u$ 對應到同一個值，因此也能生成相應的單點機率。若 $F^{-1}$ 沒有簡單公式，則可用數值方法求出所需的分位數。

第二個方向可與[均勻分配的分位數例題](/teaching-topics/quantiles-and-median/#example-214)對照。

## 本篇小結

[Proposition 2.16](#proposition-216) 說明，對任意 Borel 可測函數 $g$，CDF 法都可由事件原像求得

$$
F_Y(y)
=
\mathbb{P}(g(X)\leqslant y)
$$

這個方法不要求 $g$ 一對一或可微。若轉換後分配為絕對連續，再對 $F_Y$ 的可微區間求導數，便可得到 pdf。

若 [Proposition 2.17](#proposition-217) 的條件成立，也就是 $\mathbb{P}(X\in D)=1$、$f_X$ 在開區間 $D$ 上連續，且 $g$ 在 $D$ 上嚴格單調、連續可微及導數不為 $0$，則可使用 Jacobian 公式

$$
f_Y(y)
=
f_X\bigl(g^{-1}(y)\bigr)
\left\lvert
\frac{d}{dy}g^{-1}(y)
\right\rvert
$$

多對一轉換須把 $\mathcal{R}_X$ 分成單調分支，並加總所有滿足 $y\in E_j$ 的原像分支。不同分支的值域可能不同，所以密度常須分段書寫。

[Proposition 2.18](#proposition-218) 進一步說明，連續 CDF 可把隨機變數轉換為均勻分配，而廣義分位函數可由均勻分配產生指定的 CDF。

至此已建立單一隨機變數的 CDF、pmf、pdf、期望值、變異數、母函數、特徵函數、機率界限與函數轉換，第二章也在此告一段落。下一章會把單一隨機變數推廣為隨機向量，進一步討論聯合分配、邊際分配及多個隨機變數之間的關係。

## 參考文獻與延伸閱讀

- 黃文璋，2003，《機率論》，初版，華泰文化。
- 黃文璋，2003，《數理統計》，初版，華泰文化。
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Sheldon M. Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
