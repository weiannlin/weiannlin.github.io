---
title: "離散型隨機變數的函數轉換"
subtitle: "Transformations of Discrete Random Variables"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 20
order: 220
permalink: /teaching-topics/discrete-random-variable-transformations/
date: 2026-07-13
published: true
excerpt: "已知離散型隨機變數 $X$ 的 pmf 與 $Y=g(X)$ 後，$Y$ 在每個轉換後取值的機率等於所有映到該值的原取值機率總和。一對一反函數式是這項公式的特例，MGF 則提供另一種辨認分配的方法。"
---

[上一篇文章](/teaching-topics/empirical-rule-bell-shaped-distributions/)利用期望值與標準差描述常態分配的中央區間。本篇改以函數關係產生新的隨機變數，並求取轉換後的完整分配。

[函數期望值](/teaching-topics/expected-value-random-variables/#函數的期望值)已經處理過 $\mathbb{E}[g(X)]$。若只需要一個期望值，可以沿著 $X$ 原有的 pmf 直接加權；若需要知道 $Y=g(X)$ 的 pmf、CDF 或其他分配性質，便須進一步整理 $X$ 的每個可能值會被 $g$ 送到哪裡。

## 函數作用後仍是隨機變數

令 $(S,\mathcal{F},\mathbb{P})$ 為機率空間。前面的函數期望值一節針對常見可積函數建立計算方式；從可測性來看，還要要求 $g$ 為 **Borel 可測函數 (Borel measurable function)**。這表示每個 Borel 集合在 $g$ 下的**原像 (preimage)** 仍是 Borel 集合。這項可測性條件保證合成函數仍是隨機變數。

<div id="theorem-29" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.9 (Measurable Transformations)</div>

若 $X$ 為實值隨機變數，且 $g:\mathbb{R}\to\mathbb{R}$ 為 Borel 可測函數，則 $Y=g(X)$ 仍為實值隨機變數。

</div>

若需回顧實數線上的 Borel $\sigma$-域，可參考[事件集合族與 $\sigma$-域](/teaching-topics/event-families-sigma-fields/#實數線上的-borel-sigma-域)。

<div class="topic-proof" markdown="1">
**Proof.** 對任意 Borel 集合 $A\subseteq\mathbb{R}$，事件可寫為

$$
\lbrace Y\in A\rbrace
=
\lbrace g(X)\in A\rbrace
=
\lbrace X\in g^{-1}(A)\rbrace
$$

其中，$g^{-1}(A)=\lbrace x\in\mathbb{R}\mid g(x)\in A\rbrace$ 稱為 $A$ 在 $g$ 下的原像。這個記號不要求 $g$ 一對一。

因為 $g$ 為 Borel 可測函數，所以 $g^{-1}(A)$ 是 Borel 集合；又因 $X$ 為隨機變數，故 $\lbrace X\in g^{-1}(A)\rbrace\in\mathcal{F}$。因此 $Y$ 為實值隨機變數。$\square$
</div>

[Theorem 2.9](#theorem-29) 中的函數合成關係如 [Fig. 2.23](#fig-223) 所示。

<figure id="fig-223" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/measurable-transformation-composition.svg" alt="樣本空間中的樣本點 ω 先由 X 映到實數 X(ω)，再由 g 映到實數 Y(ω)=g(X(ω))。">
  <figcaption><span class="topic-figure__label">Fig. 2.23.</span> 樣本點 $\omega\in S$ 先經 $X$ 映到 $X(\omega)\in\mathbb{R}$，再經 $g$ 映到 $Y(\omega)=g\bigl(X(\omega)\bigr)\in\mathbb{R}$；兩段映射合起來就是 $Y=g\circ X$。</figcaption>
</figure>

在 [Fig. 2.23](#fig-223) 中，映射的起點為樣本點 $\omega\in S$；$\mathcal{F}$ 則是事件所成的 $\sigma$-域，不是樣本點所在的集合。合成後的 $Y$ 是由樣本空間 $S$ 映到 $\mathbb{R}$ 的實值函數，因此從取值如何轉換來看，會自然預期 $Y$ 仍是一個隨機變數。

不過，由 $S$ 映到 $\mathbb{R}$ 的實值函數未必是隨機變數，仍須符合可測性。定理要求 $g$ 為 Borel 可測函數，正是為了保證對每個 Borel 集合 $A$，事件 $\lbrace Y\in A\rbrace$ 仍屬於 $\mathcal{F}$。前面的證明驗證，在此條件下，合成函數仍具有隨機變數所要求的可測性。

## pmf 的原像加總公式

令 $X$ 為離散型隨機變數，pmf 為 $p_X$。其可能取值集合定義為 $\mathcal{R}_X=\lbrace X(\omega)\mid\omega\in S\rbrace$，與[隨機變數一文的值域記號](/teaching-topics/random-variables-from-sample-space-to-real-line/#可能取值集合的型態)一致。若 $Y=g(X)$，則 $Y$ 的可能取值集合為 $\mathcal{R}_Y=g(\mathcal{R}_X)$。

每個 $y\in\mathcal{R}_Y$ 可能只有一個原像，也可能由多個不同的 $x$ 映到同一位置。白話來說，對每一個 $y\in\mathcal{R}_Y$，我們可以回頭尋找哪些 $x\in\mathcal{R}_X$ 會被 $g$ 映到 $y$。這些 $x$ 都滿足 $g(x)=y$，可能有一個，也可能有多個。

<div id="proposition-215" class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Proposition 2.15 (pmf of a Discrete Transformation)</div>

令 $X$ 為離散型隨機變數，pmf 為 $p_X$。若 $Y=g(X)$，則

$$
p_Y(y)
=
\mathbb{P}(Y=y)
=
\sum_{\substack{x\in\mathcal{R}_X\\g(x)=y}}p_X(x)
$$

對 $y\notin\mathcal{R}_Y$，則有 $p_Y(y)=0$。

</div>

<div class="topic-proof" markdown="1">
**Proof.** 對固定的 $y$，事件可分割為

$$
\lbrace Y=y\rbrace
=
\bigcup_{\substack{x\in\mathcal{R}_X\\g(x)=y}}
\lbrace X=x\rbrace
$$

右側各事件彼此互斥，因此可數可加性給出

$$
\mathbb{P}(Y=y)
=
\sum_{\substack{x\in\mathcal{R}_X\\g(x)=y}}
\mathbb{P}(X=x)
$$

若 $y\notin\mathcal{R}_Y$，則不存在滿足 $g(x)=y$ 的 $x\in\mathcal{R}_X$，故 $p_Y(y)=0$。$\square$
</div>

[Proposition 2.15](#proposition-215) 同時涵蓋有限與可數無限的可能取值集合。有限情形可直接列表；可數無限情形則依公式加總所有原像。

## 直接列表與機率合併

直接列表時，可先列出每個 $x\in\mathcal{R}_X$、轉換後的 $g(x)$ 與原機率 $p_X(x)$，再依相同的 $g(x)$ 分組。若多個 $x$ 對應到同一個 $y$，它們的機率必須相加。

<div id="example-229" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.29 (One-to-One and Many-to-One Transformations)</div>

令 $X$ 的 pmf 為

| $x$ | $0$ | $1$ | $2$ | $3$ | $4$ |
| :---: | :---: | :---: | :---: | :---: | :---: |
| $p_X(x)$ | $0.15$ | $0.20$ | $0.20$ | $0.15$ | $0.30$ |

先令 $Y=X^2$。因為 $X$ 只取非負值，$x\mapsto x^2$ 在 $\mathcal{R}_X$ 上一對一，所以

| $x$ | $0$ | $1$ | $2$ | $3$ | $4$ |
| :---: | :---: | :---: | :---: | :---: | :---: |
| $y=x^2$ | $0$ | $1$ | $4$ | $9$ | $16$ |
| 機率 | $0.15$ | $0.20$ | $0.20$ | $0.15$ | $0.30$ |

由此可得

$$
p_Y(y)
=
\left\{
\begin{array}{c@{\quad}l}
0.15, & y=0 \\[0.35em]
0.20, & y=1 \\[0.35em]
0.20, & y=4 \\[0.35em]
0.15, & y=9 \\[0.35em]
0.30, & y=16 \\[0.35em]
0, & \text{otherwise}
\end{array}
\right.
$$

再令 $Z=(X-2)^2$。此時

| $x$ | $0$ | $1$ | $2$ | $3$ | $4$ |
| :---: | :---: | :---: | :---: | :---: | :---: |
| $z=(x-2)^2$ | $4$ | $1$ | $0$ | $1$ | $4$ |
| 機率 | $0.15$ | $0.20$ | $0.20$ | $0.15$ | $0.30$ |

$X=1$ 與 $X=3$ 都對應到 $Z=1$，所以 $\mathbb{P}(Z=1)=p_X(1)+p_X(3)=0.35$。同理，$X=0$ 與 $X=4$ 都對應到 $Z=4$，所以 $\mathbb{P}(Z=4)=p_X(0)+p_X(4)=0.45$。合併各原像後，$Z$ 的 pmf 為

$$
p_Z(z)
=
\left\{
\begin{array}{c@{\quad}l}
0.20, & z=0 \\[0.35em]
0.35, & z=1 \\[0.35em]
0.45, & z=4 \\[0.35em]
0, & \text{otherwise}
\end{array}
\right.
$$

</div>

<div id="interlude-222" class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 2.22</div>

函數轉換可能把 $X$ 的不同取值映到同一個轉換後取值，此時必須合併各原像事件的機率。若 $X=1$ 與 $X=3$ 經轉換後都得到 $Z=1$，則事件 $\lbrace Z=1\rbrace$ 正是兩個互斥事件 $\lbrace X=1\rbrace$ 與 $\lbrace X=3\rbrace$ 的聯集。

因此，離散型轉換只須將各原像的機率相加，不需要使用反函數導數的絕對值。下一篇會處理連續型密度的轉換公式。
</div>

## 一對一轉換的反函數式

若 $g$ 在 $\mathcal{R}_X$ 上一對一，則每個 $y\in\mathcal{R}_Y$ 只有一個原像。此時可把 [Proposition 2.15](#proposition-215) 簡化為

$$
p_Y(y)
=
p_X\bigl(g^{-1}(y)\bigr)
$$

此處 $g^{-1}$ 表示將 $g$ 的定義域限制為 $\mathcal{R}_X$ 後所得的反函數。

一對一只須在 $X$ 的可能取值集合上成立，不必要求 $g$ 在整條實數線上都一對一。[Example 2.29](#example-229) 中的 $g(x)=x^2$ 在 $\mathbb{R}$ 上不是一對一，但在 $\mathcal{R}_X=\lbrace 0,1,2,3,4\rbrace$ 上是一對一，所以反函數式仍可使用。

若原像不只一個，$g^{-1}(\lbrace y\rbrace)$ 是一個集合，不能把它當成單一數值代入 $p_X$。此時必須回到 [Proposition 2.15](#proposition-215) 的原像加總公式。

## MGF 法與線性轉換

[動差母函數一文](/teaching-topics/moment-generating-functions/#mgf-function-transformations)已先說明 MGF 在函數轉換下的寫法。本節把這項關係用於辨認離散型隨機變數經轉換後的分配。

若 $Y=g(X)$ 的 MGF 存在，則

$$
M_Y(t)
=
\mathbb{E}(e^{tY})
=
\mathbb{E}\bigl(e^{t g(X)}\bigr)
$$

對**線性轉換 (linear transformation)** $Y=aX+b$，可進一步整理為

$$
\begin{aligned}
M_Y(t)
&=
\mathbb{E}\bigl(e^{t(aX+b)}\bigr) \\[0.35em]
&=
e^{bt}\mathbb{E}(e^{(at)X})
=
e^{bt}M_X(at)
\end{aligned}
$$

<div id="note-affine-mgf-domain" class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

關係式 $M_Y(t)=e^{bt}M_X(at)$ 在 $M_X(at)$ 有限的 $t$ 上成立。若要依 [MGF 唯一性定理](/teaching-topics/moment-generating-functions/#theorem-21)辨認 $Y$ 的分配，所比較的 MGF 必須在同一個含 $0$ 的開區間上存在並相等。

若 $a=0$，則 $Y=0\cdot X+b=b$，不論 $X$ 取何值，$Y$ 都等於 $b$。因此 $Y$ 的 pmf 為

$$
p_Y(y)
=
\left\{
\begin{array}{c@{\quad}l}
1, & y=b \\[0.35em]
0, & y\neq b
\end{array}
\right.
$$

此外，由 $M_X(0)=1$ 可得

$$
M_Y(t)
=
e^{bt}M_X(0)
=
e^{bt}
$$

所以線性轉換的 MGF 公式仍可使用。若 $\mathcal{R}_X$ 至少含有兩個值，所有 $x\in\mathcal{R}_X$ 都映到同一個 $b$，因此 $x\mapsto ax+b$ 在 $\mathcal{R}_X$ 上不是一對一。此時 $\lbrace x\in\mathcal{R}_X\mid g(x)=b\rbrace=\mathcal{R}_X$；這個原像是整個可能取值集合，而不是能代入 $p_X$ 的單一數值，故不能使用一對一反函數式。應回到 [Proposition 2.15](#proposition-215) 的原像加總公式，得到

$$
p_Y(b)
=
\sum_{x\in\mathcal{R}_X}p_X(x)
=
1
$$

</div>

<div id="example-230" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.30 (Three Methods for a Linear Transformation)</div>

令 $X$ 的 pmf 為

$$
p_X(x)
=
\frac{x}{10},
\qquad
x=1,2,3,4
$$

並令 $Y=2X+1$。

直接列表可得

| $x$ | $1$ | $2$ | $3$ | $4$ |
| :---: | :---: | :---: | :---: | :---: |
| $y=2x+1$ | $3$ | $5$ | $7$ | $9$ |
| 機率 | $1/10$ | $2/10$ | $3/10$ | $4/10$ |

由表中的對應關係可得 $Y$ 的 pmf 為

$$
p_Y(y)
=
\left\{
\begin{array}{c@{\quad}l}
\dfrac{y-1}{20}, & y=3,5,7,9 \\[0.35em]
0, & \text{otherwise}
\end{array}
\right.
$$

因為 $x\mapsto 2x+1$ 在 $\mathcal{R}_X$ 上一對一，所以對每個 $y\in\lbrace 3,5,7,9\rbrace$，都可由 $X=(Y-1)/2$ 得到

$$
p_Y(y)
=
p_X\left(\frac{y-1}{2}\right)
=
\frac{y-1}{20}
$$

最後使用 MGF。由 $X$ 的值域有限可知 $M_X(t)$ 對所有實數 $t$ 皆存在，且

$$
M_X(t)
=
\frac{1}{10}e^t
+
\frac{2}{10}e^{2t}
+
\frac{3}{10}e^{3t}
+
\frac{4}{10}e^{4t}
$$

利用線性轉換的 MGF 公式，可得

$$
\begin{aligned}
M_Y(t)
&=
e^tM_X(2t) \\[0.35em]
&=
\frac{1}{10}e^{3t}
+
\frac{2}{10}e^{5t}
+
\frac{3}{10}e^{7t}
+
\frac{4}{10}e^{9t}
\end{aligned}
$$

這個 MGF 同樣顯示 $Y$ 在 $3,5,7,9$ 四點上分別具有機率 $1/10,2/10,3/10,4/10$。
</div>

## 方法的適用情形

| 方法 | 主要條件 | 作法 |
| :---: | :---: | :---: |
| 直接列表 | 可能取值有限或容易列出 | 列出 $x$、$g(x)$ 與 $p_X(x)$，再合併相同的轉換後取值 |
| pmf 原像加總 | 任意離散型轉換 | 對所有滿足 $g(x)=y$ 的 $x$ 加總 $p_X(x)$ |
| 一對一反函數 | $g$ 在 $\mathcal{R}_X$ 上一對一 | 使用 $p_Y(y)=p_X(g^{-1}(y))$ |
| MGF | 所需區間內的 MGF 存在 | 計算 $M_Y(t)=\mathbb{E}(e^{t g(X)})$，再依唯一性辨認分配 |

直接列表與一對一反函數都來自 pmf 原像加總公式。MGF 則以另一種函數形式刻畫分配，而且同時適用於離散型與連續型隨機變數。已知 MGF 的形式或處理線性轉換時，MGF 法特別方便。

## 本篇小結

[Theorem 2.9](#theorem-29) 說明，若 $X$ 為隨機變數，且 $g$ 為 Borel 可測函數，則 $Y=g(X)$ 仍為隨機變數。對離散型 $X$，轉換後的 pmf 可寫為

$$
p_Y(y)
=
\sum_{\substack{x\in\mathcal{R}_X\\g(x)=y}}p_X(x)
$$

多個 $x$ 映到同一個 $y$ 時，必須把所有原像的機率相加。若 $g$ 在 $X$ 的可能取值集合上一對一，公式才可簡化為 $p_Y(y)=p_X(g^{-1}(y))$。

線性轉換 $Y=aX+b$ 的 MGF 滿足 $M_Y(t)=e^{bt}M_X(at)$，但使用 MGF 辨認分配時仍須確認它在 $0$ 附近存在。

[下一篇文章](/teaching-topics/continuous-random-variable-transformations/)將處理連續型隨機變數的函數轉換。離散型分配合併機率質量；連續型分配則須由 CDF 或 [Jacobian 公式](/teaching-topics/continuous-random-variable-transformations/#proposition-217)整理轉換後的密度。

## 參考文獻與延伸閱讀

- 黃文璋，2003，《機率論》，初版，華泰文化。
- 黃文璋，2003，《數理統計》，初版，華泰文化。
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Sheldon M. Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
