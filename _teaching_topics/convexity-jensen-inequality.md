---
title: "凸函數與延森不等式"
subtitle: "Convexity and Jensen's Inequality"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 18
order: 218
permalink: /teaching-topics/convexity-jensen-inequality/
date: 2026-07-13
published: true
excerpt: '凸性比較先取函數值再平均與先平均再取函數值的大小。延森不等式把這項幾何性質推廣至期望值，並導出平均數關係與 KL 訊息數非負性。'
---

[上一篇文章](/teaching-topics/chernoff-inequality/)先對隨機變數作指數轉換，再利用期望值建立尾端機率界限。若要有系統地比較 $\mathbb{E}[g(X)]$ 與 $g(\mathbb{E}(X))$，則需要先確認函數 $g$ 的形狀。

凸函數 (convex function) 的圖形位於任兩點所連成的弦線下方；凹函數 (concave function) 則位於弦線上方。[延森不等式 (Jensen's inequality)](#theorem-28) 把這項兩點之間的性質推廣到隨機變數的期望值。

## 凸函數與凹函數

凸組合 (convex combination) $tx+(1-t)y$ 必須仍在函數的定義域中，因此定義域要取為一個區間。更高維度的版本則把區間換成凸集合。

<div id="definition-221" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.21</div>

令 $I\subseteq\mathbb{R}$ 為一個區間，且 $f:I\to\mathbb{R}$。

若對所有 $x,y\in I$ 與 $t\in[0,1]$，皆有

$$
f\bigl(tx+(1-t)y\bigr)
\leqslant
tf(x)+(1-t)f(y)
$$

則稱 $f$ 為**凸函數 (convex function)**。

若對所有 $x,y\in I$ 與 $t\in[0,1]$，皆有

$$
f\bigl(tx+(1-t)y\bigr)
\geqslant
tf(x)+(1-t)f(y)
$$

則稱 $f$ 為**凹函數 (concave function)**。

若 $x\ne y$ 且 $0<t<1$ 時，凸函數定義中的不等式必為嚴格小於，則稱 $f$ 為**嚴格凸函數 (strictly convex function)**。若凹函數定義中的不等式必為嚴格大於，則稱 $f$ 為**嚴格凹函數 (strictly concave function)**。

</div>

嚴格凸與嚴格凹的條件不能把 $x=y$ 或 $t\in\lbrace 0,1\rbrace$ 納入。這些情況下，等式兩側本來就完全相同。

例如 $f(x)=x^2$ 在 $\mathbb{R}$ 上為嚴格凸函數，$g(x)=\ln x$ 在 $(0,\infty)$ 上為嚴格凹函數，而 $h(x)=-\ln x$ 在 $(0,\infty)$ 上為嚴格凸函數。若函數二次可微，則 $f^{\prime\prime}(x)\geqslant0$ 可用來判定凸性，$f^{\prime\prime}(x)\leqslant0$ 可用來判定凹性；若二階導數在整個區間內嚴格為正或嚴格為負，便可得到對應的嚴格性。

## 弦線與支撐直線

[Definition 2.21](#definition-221) 中不等式的右側 $tf(x)+(1-t)f(y)$，是弦線上對應於 $tx+(1-t)y$ 的高度。因此凸函數圖形位於弦線下方，凹函數圖形則位於弦線上方。

凸函數還具有另一項性質。若 $m$ 是區間內點，則可選取一個實數 $s$，使所有 $x\in I$ 都滿足

$$
f(x)
\geqslant
f(m)+s(x-m)
$$

右側是一條通過 $(m,f(m))$ 且位於函數圖形下方的**支撐直線 (supporting line)**。若 $f$ 在 $m$ 可微，可取 $s=f^{\prime}(m)$，此時支撐直線就是切線。凹函數的支撐直線位於函數圖形上方，不等號方向也隨之反轉。

兩種直線與凸函數圖形的相對位置可參考 [Fig. 2.21](#fig-221)。

<figure id="fig-221" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/convexity-chord-supporting-line.svg" alt="凸函數的弦線與支撐直線示意圖。第一幅圖中，連接曲線上兩點的弦線位於兩點之間的曲線上方；第二幅圖中，通過曲線上一點的支撐直線位於曲線下方。">
  <figcaption><span class="topic-figure__label">Fig. 2.21.</span> 對凸函數而言，(a) 若 $0<t<1$ 且 $m=tx_1+(1-t)x_2$，則弦線在 $m$ 的高度 $tf(x_1)+(1-t)f(x_2)$ 不小於 $f(m)$；(b) 通過 $(m,f(m))$ 的支撐直線位於函數圖形下方。凹函數的兩項位置關係都反轉。</figcaption>
</figure>

<div id="interlude-220" class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 2.20</div>

[Definition 2.21](#definition-221) 比較兩種次序。把 $x$ 與 $y$ 依權重 $t$、$1-t$ 平均後再代入 $f$，得到 $f\bigl(tx+(1-t)y\bigr)$；先計算 $f(x)$、$f(y)$ 再依相同權重平均，則得到 $tf(x)+(1-t)f(y)$。

凸函數使前者不大於後者，凹函數則使前者不小於後者。期望值也是依機率作加權平均，[Theorem 2.8](#theorem-28) 正是把這個比較推廣到整個機率分配。
</div>

## 延森不等式

使用 [Theorem 2.8](#theorem-28) 前，須先確認 $X$ 可積且以機率 $1$ 取值於函數的定義區間內，並確認函數轉換也可積。此外，也須確認所使用的函數為凸函數或凹函數，因為兩者的不等號方向相反。

<div id="theorem-28" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.8 (Jensen's Inequality)</div>

令 $I\subseteq\mathbb{R}$ 為一個區間，$X$ 為滿足

$$
\mathbb{P}(X\in I)=1,
\qquad
\mathbb{E}(\lvert X\rvert)<\infty
$$

的隨機變數。

若 $g:I\to\mathbb{R}$ 為凸函數，且 $\mathbb{E}(\lvert g(X)\rvert)<\infty$，則

$$
g\bigl(\mathbb{E}(X)\bigr)
\leqslant
\mathbb{E}\bigl[g(X)\bigr]
$$

若 $h:I\to\mathbb{R}$ 為凹函數，且 $\mathbb{E}(\lvert h(X)\rvert)<\infty$，則

$$
h\bigl(\mathbb{E}(X)\bigr)
\geqslant
\mathbb{E}\bigl[h(X)\bigr]
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.** 先處理凸函數 $g$，並令 $m=\mathbb{E}(X)$。若 $m$ 是 $I$ 的下端點，則 $X-m\geqslant0$ 且 $\mathbb{E}(X-m)=0$，所以 $\mathbb{P}(X=m)=1$。若 $m$ 是 $I$ 的上端點，對 $m-X$ 作相同推導也可得到這項結論。因此，$m$ 位於端點時，不等式直接取等號。

若 $m$ 是區間內點，取一條通過 $(m,g(m))$ 的支撐直線。存在某個斜率 $s$，使得

$$
g(x)
\geqslant
g(m)+s(x-m),
\qquad
x\in I
$$

將 $x$ 換成 $X$ 並取期望值，可得

$$
\begin{aligned}
\mathbb{E}\bigl[g(X)\bigr]
&\geqslant
\mathbb{E}\bigl[g(m)+s(X-m)\bigr] \\[0.35em]
&=
g(m)+s\bigl(\mathbb{E}(X)-m\bigr) \\[0.35em]
&=
g(m) \\[0.35em]
&=
g\bigl(\mathbb{E}(X)\bigr)
\end{aligned}
$$

若 $h$ 為凹函數，則 $-h$ 為凸函數。把前述結果套用在 $-h$，即可得到凹函數版本。$\square$
</div>

這個證明使用支撐直線，不要求函數在 $m$ 可微。若 $g$ 可微，才可把斜率 $s$ 直接寫成 $g^{\prime}(m)$。

[Theorem 2.8](#theorem-28) 的等號條件也可由支撐直線看出。若 $m$ 是 $I$ 的端點，由前述證明可知 $\mathbb{P}(X=m)=1$。以下考慮 $m$ 為區間內點的情形，並令 $\ell(x)=g(m)+s(x-m)$ 為通過 $(m,g(m))$ 的支撐直線。由期望值的線性關係與 $\mathbb{E}[\ell(X)]=\ell(m)=g(m)$ 可得 $\mathbb{E}[g(X)]-g(m)=\mathbb{E}[g(X)-\ell(X)]$。因為 $g(x)-\ell(x)\geqslant0$，此期望值非負。

因此，凸函數版本的等號成立若且唯若

$$
\mathbb{P}\bigl(g(X)=\ell(X)\bigr)=1
$$

凹函數版本的條件相同，只需改用位於函數圖形上方的支撐直線。若 $g$ 嚴格凸，支撐直線只在 $m$ 接觸函數圖形，所以等號成立若且唯若 $\mathbb{P}(X=m)=1$。嚴格凹函數也有相同的等號條件。

## 三種平均數的大小關係

延森不等式可以用來比較不同形式的平均數。以下把一組正數視為隨機變數的可能取值，再由凹函數 $\ln x$ 推導算術平均數、幾何平均數與調和平均數的大小關係。

<div id="example-225" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.25 (Arithmetic, Geometric, and Harmonic Means)</div>

令 $a_1,\ldots,a_n>0$。算術平均數、幾何平均數與調和平均數分別定義如下。

$$
\begin{aligned}
A
&=
\frac{1}{n}\sum_{i=1}^n a_i \\[0.35em]
G
&=
\left(\prod_{i=1}^n a_i\right)^{1/n} \\[0.35em]
H
&=
\left(\frac{1}{n}\sum_{i=1}^n\frac{1}{a_i}\right)^{-1}
\end{aligned}
$$

令隨機變數 $X$ 以相同機率 $1/n$ 取值 $a_1,\ldots,a_n$。由期望值的定義可得

$$
\begin{aligned}
\mathbb{E}(X)
&=
\sum_{i=1}^n a_i\cdot\frac{1}{n} \\[0.35em]
&=
\frac{1}{n}\sum_{i=1}^n a_i
=
A
\end{aligned}
$$

函數 $\ln x$ 在 $(0,\infty)$ 上為凹函數，因此 [Theorem 2.8](#theorem-28) 給出

$$
\begin{aligned}
\frac{1}{n}\sum_{i=1}^n\ln a_i
&=
\mathbb{E}(\ln X) \\[0.35em]
&\leqslant
\ln\bigl(\mathbb{E}(X)\bigr) \\[0.35em]
&=
\ln A
\end{aligned}
$$

左側等於 $\ln G$。指數函數嚴格遞增，因此 $G\leqslant A$。

把剛得到的算幾不等式套用在 $1/a_1,\ldots,1/a_n$，可得

$$
\begin{aligned}
\frac{1}{H}
&=
\frac{1}{n}\sum_{i=1}^n\frac{1}{a_i} \\[0.35em]
&\geqslant
\left(\prod_{i=1}^n\frac{1}{a_i}\right)^{1/n} \\[0.35em]
&=
\frac{1}{G}
\end{aligned}
$$

因為 $G,H>0$，故 $G\geqslant H$。合併兩個結果可得

$$
A\geqslant G\geqslant H
$$

函數 $\ln x$ 為嚴格凹函數，因此第一個等號成立若且唯若 $a_1=\cdots=a_n$。同一條件也使第二個等號成立，所以

$$
A=G=H
\quad\Longleftrightarrow\quad
a_1=\cdots=a_n
$$

</div>

## 期望值與中位數相距多遠

延森不等式也可用來比較期望值與中位數的位置。以下分別使用絕對值函數的凸性與平方根函數的凹性，說明兩者之間的距離為何不會超過一個標準差。

<div id="example-226" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.26 (The Distance Between Mean and Median)</div>

令 $X$ 滿足 $\mathbb{E}(X^2)<\infty$，期望值為 $\mu_X$，標準差為 $\sigma_X$，並令 $\eta_X$ 為 $X$ 的任一中位數。則

$$
\lvert\mu_X-\eta_X\rvert
\leqslant
\sigma_X
$$

先以初等不等式 $\lvert t\rvert\leqslant(1+t^2)/2$ 處理期望值的有限性。由 $\mathbb{E}(X^2)<\infty$ 可知，對每個 $a\in\mathbb{R}$，都有

$$
\mathbb{E}(\lvert X-a\rvert)
\leqslant
\frac{1+\mathbb{E}\bigl[(X-a)^2\bigr]}{2}
<
\infty
$$

若令 $Y=(X-a)^2$，則函數 $\sqrt{y}$ 在 $[0,\infty)$ 上為凹函數。由 [Theorem 2.8](#theorem-28) 可得較精確的上界

$$
\mathbb{E}(\lvert X-a\rvert)
\leqslant
\sqrt{\smash[b]{\mathbb{E}[(X-a)^2]}}
$$

由上述不等式可知，$\mathbb{E}(\lvert X-a\rvert)$ 對每個 $a\in\mathbb{R}$ 都是有限值。為了比較期望值與中位數的距離，我們先證明中位數的一項極小化性質。對任意 $a\in\mathbb{R}$，中位數 $\eta_X$ 使**平均絕對離差 (mean absolute deviation)** 達到最小值，因此

$$
\mathbb{E}\bigl[\lvert X-\eta_X\rvert\bigr]
\leqslant
\mathbb{E}\bigl[\lvert X-a\rvert\bigr]
$$

這項性質可直接由中位數定義驗證。對集合或事件 $A$，令 $\mathbf{1}_A$ 表示 $A$ 的指標函數 (indicator function)。若 $a>\eta_X$，則對每個實數 $x$，皆有

$$
\lvert x-a\rvert-\lvert x-\eta_X\rvert
\geqslant
(a-\eta_X)
\bigl(\mathbf{1}_{\lbrace x\leqslant\eta_X\rbrace}
-\mathbf{1}_{\lbrace x>\eta_X\rbrace}\bigr)
$$

取期望值後，利用 $\mathbb{P}(X\leqslant\eta_X)\geqslant1/2$，可得

$$
\begin{aligned}
\mathbb{E}\bigl[\lvert X-a\rvert-\lvert X-\eta_X\rvert\bigr]
&\geqslant
(a-\eta_X)
\bigl(\mathbb{P}(X\leqslant\eta_X)-\mathbb{P}(X>\eta_X)\bigr) \\[0.35em]
&\geqslant
0
\end{aligned}
$$

若 $a<\eta_X$，則對每個實數 $x$，皆有

$$
\lvert x-a\rvert-\lvert x-\eta_X\rvert
\geqslant
(\eta_X-a)
\bigl(\mathbf{1}_{\lbrace x\geqslant\eta_X\rbrace}
-\mathbf{1}_{\lbrace x<\eta_X\rbrace}\bigr)
$$

取期望值後，再利用 $\mathbb{P}(X\geqslant\eta_X)\geqslant1/2$，同樣可得非負的下界。故中位數的極小化性質對離散型、連續型與混合型分配皆成立。

函數 $g(x)=\lvert x-\eta_X\rvert$ 為凸函數，因此由 [Theorem 2.8](#theorem-28) 可知，先對 $X$ 取期望值再代入 $g$ 所得的數值不大於先作函數轉換再取期望值的結果。在中位數的極小化性質中令 $a=\mu_X$，又可知以 $\eta_X$ 為中心的平均絕對離差不大於以 $\mu_X$ 為中心的平均絕對離差。合併兩個結果可得

$$
\begin{aligned}
\lvert\mu_X-\eta_X\rvert
&=
\bigl\lvert\mathbb{E}(X)-\eta_X\bigr\rvert \\[0.35em]
&\leqslant
\mathbb{E}\bigl[\lvert X-\eta_X\rvert\bigr] \\[0.35em]
&\leqslant
\mathbb{E}\bigl[\lvert X-\mu_X\rvert\bigr]
\end{aligned}
$$

最後令 $Y=(X-\mu_X)^2$。由前段可知 $\mathbb{E}(\sqrt{Y})=\mathbb{E}(\lvert X-\mu_X\rvert)<\infty$。函數 $\sqrt{y}$ 在 $[0,\infty)$ 上為凹函數，再次使用 [Theorem 2.8](#theorem-28) 可得

$$
\begin{aligned}
\mathbb{E}\bigl[\lvert X-\mu_X\rvert\bigr]
&=
\mathbb{E}(\sqrt{Y}) \\[0.35em]
&\leqslant
\sqrt{\mathbb{E}(Y)} \\[0.35em]
&=
\sqrt{\mathrm{Var}(X)} \\[0.35em]
&=
\sigma_X
\end{aligned}
$$

合併兩段不等式，即得 $\lvert\mu_X-\eta_X\rvert\leqslant\sigma_X$。
</div>

## KL 訊息數不會是負數

延森不等式也可用來處理機率分配之間的比較。以下考慮描述訊息損失的 KL 訊息數，並利用 $-\ln x$ 的凸性說明它為何不會是負數。

<div id="example-227" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.27 (Nonnegativity of KL Information)</div>

令 $f_0$ 與 $f_1$ 為具有共同**支撐集 (common support)** $S$ 的兩個機率密度函數，並假設

$$
f_0(x)>0,
\qquad
f_1(x)>0,
\qquad
x\in S
$$

以下以 $\mathbb{E}_0$ 與 $\mathbb{P}_0$ 分別表示依密度 $f_0$ 計算的期望值與機率。再假設

$$
\mathbb{E}_0
\left[
\left\lvert
\ln\frac{f_0(X)}{f_1(X)}
\right\rvert
\right]
<\infty
$$

定義 $f_0$ 相對於 $f_1$ 的 **KL 訊息數 (Kullback-Leibler information)** 如下。

$$
K(f_0,f_1)
=
\mathbb{E}_0
\left[
\ln\frac{f_0(X)}{f_1(X)}
\right]
$$

令 $W=f_1(X)/f_0(X)$。由 $S$ 上的正值條件可知 $\mathbb{P}_0(W>0)=1$。由 $f_1$ 為機率密度函數可得

$$
\begin{aligned}
\mathbb{E}_0(W)
&=
\int_S
\frac{f_1(x)}{f_0(x)}f_0(x)\,dx \\[0.35em]
&=
\int_S f_1(x)\,dx \\[0.35em]
&=
1
\end{aligned}
$$

因為 $g(w)=-\ln w$ 在 $(0,\infty)$ 上為嚴格凸函數，[Theorem 2.8](#theorem-28) 給出

$$
\begin{aligned}
K(f_0,f_1)
&=
\mathbb{E}_0(-\ln W) \\[0.35em]
&\geqslant
-\ln\bigl(\mathbb{E}_0(W)\bigr) \\[0.35em]
&=
-\ln 1 \\[0.35em]
&=
0
\end{aligned}
$$

因此 KL 訊息數必為非負。由 [Theorem 2.8](#theorem-28) 的嚴格凸函數等號條件可知，等號成立若且唯若

$$
\mathbb{P}_0(W=1)=1
$$

在 $S$ 上的正值條件下，這也等價於 $f_0$ 與 $f_1$ 對 **Lebesgue 測度 (Lebesgue measure)** 幾乎處處 (almost everywhere) 相同。亦即

$$
K(f_0,f_1)=0
\quad\Longleftrightarrow\quad
f_0(x)=f_1(x)
\text{ 對 }S\text{ 上的 Lebesgue 測度幾乎處處成立}
$$

這裡假設 $f_0$ 與 $f_1$ 在 $S$ 上皆為正且對數比值可積，使每一個期望值都為有限值。更一般的定義允許 KL 訊息數等於 $+\infty$。若存在一個具有正 $f_0$ 機率的集合，使 $f_1=0$，則直接定義 $K(f_0,f_1)=+\infty$，非負性仍然成立。
</div>

KL 訊息數衡量以 $f_1$ 代替 $f_0$ 時的平均訊息損失。它通常不具對稱性，也不必滿足距離函數的三角不等式，因此不能只因其非負就把它當成一般距離。

## 本篇小結

凸函數位於弦線下方，凹函數位於弦線上方。若 $X$ 與函數轉換都可積，[Theorem 2.8](#theorem-28) 給出

$$
g\bigl(\mathbb{E}(X)\bigr)
\leqslant
\mathbb{E}\bigl[g(X)\bigr]
$$

其中 $g$ 為凸函數；凹函數則反轉不等號。當 $\mathbb{E}(X)$ 位於區間內部時，一般等號條件要求點 $\bigl(X,g(X)\bigr)$ 以機率 $1$ 落在通過 $\bigl(\mathbb{E}(X),g(\mathbb{E}(X))\bigr)$ 的支撐直線上。若函數嚴格凸或嚴格凹，則等號成立若且唯若存在 $c\in I$ 使 $\mathbb{P}(X=c)=1$。

[Example 2.25](#example-225)、[Example 2.26](#example-226) 與 [Example 2.27](#example-227) 分別說明三種平均數的關係、期望值與中位數的距離，以及 KL 訊息數的非負性。使用 [Theorem 2.8](#theorem-28) 前，必須檢查函數的區間、隨機變數的取值範圍與相關期望值是否存在。

[下一篇文章](/teaching-topics/empirical-rule-bell-shaped-distributions/)會以常態分配為基準，說明鐘形外觀本身為何不足以保證[經驗法則](/teaching-topics/empirical-rule-bell-shaped-distributions/#empirical-rule-68-95-997)，並比較常態分配的中央區間機率與[柴比雪夫下界](/teaching-topics/chebyshev-cantelli-inequalities/#theorem-25)。

## 參考文獻與延伸閱讀

- 黃文璋，2003，《機率論》，初版，華泰文化。
- 黃文璋，2003，《數理統計》，初版，華泰文化。
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Thomas M. Cover and Joy A. Thomas. 2006. *Elements of Information Theory*. 2nd ed. Wiley.
- Sheldon M. Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
