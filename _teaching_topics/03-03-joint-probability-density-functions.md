---
title: "聯合機率密度函數"
subtitle: "Joint Probability Density Functions"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 3
order: 303
permalink: /lecture-notes/joint-probability-density-functions/
date: 2026-08-12
published: false
excerpt: "二元連續型隨機向量的聯合累積分配函數若可表為非負函數由 $-\\infty$ 積至 $x$ 與 $y$ 的二重積分，該被積函數即為聯合機率密度函數。本篇說明曲面下體積的機率詮釋、二階混合偏導數與聯合 pdf 的關係及三項基本性質。"
---

[上一篇](/lecture-notes/joint-cumulative-distribution-functions/)以 $\mathbb{P}(X\leqslant x,Y\leqslant y)$ 定義了[聯合累積分配函數](/lecture-notes/joint-cumulative-distribution-functions/#def-joint-cdf)，並說明二元離散型[隨機向量](/lecture-notes/random-vectors-joint-pmf/#def-random-vector)的聯合累積分配函數，是把[聯合機率質量函數](/lecture-notes/random-vectors-joint-pmf/#def-joint-pmf)在指定範圍中做兩重的加總。二元連續型隨機向量無法以加總處理，須如同單變數時改用積分。

本篇即由這個積分表示式給出聯合機率密度函數的定義，說明它與聯合累積分配函數之間的積分與偏微分關係，再列出它應該滿足的三項性質，最後就克萊羅定理、單面機率、積空間與富比尼定理四點加以補充。

<div id="def-joint-pdf" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 3.5 (聯合機率密度函數, joint pdf)</div>

若 $(X,Y)$ 為二元**連續型**隨機向量，joint cdf 為 <span class="text-nowrap">$F_{\sssig XY}(x,y)$，</span>聯合值域為 <span class="text-nowrap">$\mathcal{R}\_{\sssig XY}$，</span>若非負函數 $f_{\sssig XY}(\cdot,\cdot)$ 滿足

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig XY}(x,y)=\int_{-\infty}^{y}\int_{-\infty}^{x}f_{\sssig XY}(t,s)\,dt\,ds,\quad (x,y)\in\mathbb{R}^{2}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig XY}(x,y)&=\int_{-\infty}^{y}\int_{-\infty}^{x}f_{\sssig XY}(t,s)\,dt\,ds,\\[0.45em]
&\quad\ (x,y)\in\mathbb{R}^{2}
\end{aligned}
$$

</div>

則稱 $f_{\sssig XY}(x,y)$ 為 $(X,Y)$ 之**聯合機率密度函數 <span lang="en">(joint probability density function, joint pdf)</span>**。

</div>

joint pdf 的定義是將[單變數的 pdf](/lecture-notes/probability-density-functions/#def-pdf) 推廣至雙變數函數，故單變數 pdf 的基本特性在此依然成立，尤其須謹記 **joint pdf 本身並不是機率**。

joint pdf 與 joint cdf 之間同樣互為微分與積分關係，差別在於維度提升後的幾何意義。**單變數 cdf 是在 $X\leqslant x$ 範圍中，$f\_{\sssig X}(x)$ 下方所夾的面積**；而 **joint cdf 則是在 $X\leqslant x$ 且 $Y\leqslant y$ 範圍中，$f\_{\sssig XY}(x,y)$ 下方所夾的體積**。下圖繪出一個典型的鐘形 joint pdf 曲面:

<figure id="fig-joint-pdf-surface" class="topic-figure topic-figure--wide">
  <img src="/images/lecture-notes/joint-pdf-surface.svg" alt="一個聯合機率密度函數的曲面，中央隆起成鐘形，四周向外遞減趨近於零。底面兩軸分別標 x 與 y，縱軸標聯合機率密度函數的函數值。">
  <figcaption><span class="topic-figure__label">Fig. 3.2.</span> 一個很經典的 joint pdf。曲面在中央隆起，四周遞減；曲面之下所夾的體積即機率。</figcaption>
</figure>

對照前一頁的區域圖可知，$F_{\sssig XY}(x,y)$ 即為在 [Fig. 3.1](/lecture-notes/joint-cumulative-distribution-functions/#fig-joint-cdf-quadrants) 左下角區域內，[Fig. 3.2](#fig-joint-pdf-surface) 曲面下方所圍出的**體積**。比照單變數 [Fig. 2.4](/lecture-notes/probability-density-functions/#fig-cdf-as-area) 的微積分觀點，對二元積分式先後取兩變數的偏導數，可得以下的關係式:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig XY}(x,y)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{\partial^{2}F_{\sssig XY}(x,y)}{\partial x\,\partial y}, & \text{$(x,y)$ 是 $\mathcal{R}_{\sssig XY}$ 中的可微分點}\\[0.8em]
0, & \text{$(x,y)$ 是 $\mathcal{R}_{\sssig XY}$ 中的不可微分點或不在 $\mathcal{R}_{\sssig XY}$ 中}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile">

<div class="topic-cases topic-cases--stack">
  <div class="topic-cases__lhs">$f_{\sssig XY}(x,y)=$</div>
  <div class="topic-cases__brace" aria-hidden="true">
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 11 0.8 C 7.6 0.8 6 2.4 6 5.2 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 3.4 C 6 5 4.6 6 1 6 C 4.6 6 6 7 6 8.6 L 6 12" vector-effect="non-scaling-stroke"/></svg>
    <span class="topic-cases__brace-bar"></span>
    <svg viewBox="0 0 12 12" preserveAspectRatio="none"><path d="M 6 0 L 6 6.8 C 6 9.6 7.6 11.2 11 11.2" vector-effect="non-scaling-stroke"/></svg>
  </div>
  <div class="topic-cases__rows">
    <div class="topic-cases__val">$\dfrac{\partial^{2}F_{\sssig XY}(x,y)}{\partial x\,\partial y},$</div>
    <div class="topic-cases__cond">$(x,y)$ 是 $\mathcal{R}_{\sssig XY}$ 中的可微分點</div>
    <div class="topic-cases__val">$0,$</div>
    <div class="topic-cases__cond">$(x,y)$ 是 $\mathcal{R}_{\sssig XY}$ 中的不可微分點或不在 $\mathcal{R}_{\sssig XY}$ 中</div>
  </div>
</div>

</div>

由於自變數增加為兩個 (或更多)，求導時須指明微分的對象，故微分符號由單變數的常導數改為二階混合偏導數。以下整理 joint pdf 應具備的基本性質。

<div id="thm-joint-pdf-proper" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 3.1 (joint pdf 的性質, properties of a joint pdf)</div>

一二元連續型隨機向量 $(X,Y)$ 之**聯合機率密度函數** $f_{\sssig XY}(x,y)$ 應滿足以下性質:

<ol class="topic-list-paren">
  <li>
$$
f_{\sssig XY}(x,y)\geqslant 0,\quad\forall\,(x,y)\in\mathcal{R}_{\sssig XY}
$$
  </li>
  <li>
$$
\begin{aligned}
\mathbb{P}\bigl((X,Y)\in\mathcal{R}_{\sssig XY}\bigr)&=\iint_{(x,y)\in\mathcal{R}_{\sssig XY}}f_{\sssig XY}(x,y)\,dx\,dy\\[0.45em]
&=\int_{-\infty}^{\infty}\int_{-\infty}^{\infty}f_{\sssig XY}(x,y)\,dx\,dy=1
\end{aligned}
$$
  </li>
  <li>對任意波雷爾集合 <span class="text-nowrap">$A$，</span>皆有
$$
\mathbb{P}\bigl((X,Y)\in A\bigr)=\iint_{(x,y)\in A\cap\mathcal{R}_{\sssig XY}}f_{\sssig XY}(x,y)\,dx\,dy
$$
  </li>
</ol>

</div>

[Theorem 3.1](#thm-joint-pdf-proper) 中有幾個比較關鍵的地方需要特別注意:

(1) 由**克萊羅定理 <span lang="en">(Clairaut’s theorem)</span>** 可以保證一個相當有用的衍生性質:
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig XY}(x,y)=\frac{\partial^{2}F_{\sssig XY}(x,y)}{\partial x\,\partial y}=\frac{\partial^{2}F_{\sssig XY}(x,y)}{\partial y\,\partial x}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig XY}(x,y)&=\frac{\partial^{2}F_{\sssig XY}(x,y)}{\partial x\,\partial y}\\[0.45em]
&=\frac{\partial^{2}F_{\sssig XY}(x,y)}{\partial y\,\partial x}
\end{aligned}
$$

</div>

換言之，即偏微分的順序可交換，並不影響結果。
{: .topic-paren-cont}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

克萊羅定理又稱楊氏定理 <span lang="en">(Young’s theorem)</span> 或舒瓦茲定理 <span lang="en">(Schwarz’s theorem)</span>。若函數在某點滿足舒瓦茲可積分條件 <span lang="en">(Schwarz integrability condition)</span>，亦即具有連續的二階偏導數，則該點上的偏微分順序可以交換，此即二階導數的對稱性 <span lang="en">(symmetry of second derivatives)</span>，在求取海森矩陣 <span lang="en">(Hessian matrix)</span> 時相當有用。應用於此處，即不論先對 $x$ 或先對 $y$ 偏微分，皆會得到相同的 joint pdf。

</div>

(2) 性質 (1) 與 (2) 繼承了[單變數 pdf 的性質](/lecture-notes/probability-density-functions/#thm-pdf-properties)，其中性質 (2) 的幾何意義由曲線下的面積總和為 $1$ 轉為**曲面下的體積總和為 $1$**；此外，**積分範圍是否包含邊界點不影響結果**以及**單點積分仍為 $0$** 等性質亦與單變數相同。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

除單點機率為 $0$ 外，joint pdf 還具有**單面機率亦為 $0$** 的特性。這與幾何上「點沒有長度、線沒有面積、面沒有體積」的道理一致，嚴謹而言皆源於低維集合在高維空間中的機率測度 <span lang="en">(probability measure)</span> 為 <span class="text-nowrap">$0$。</span>對照單變數的 [Fig. 2.7](/lecture-notes/computing-probabilities-from-cdf/#fig-single-point-zero)，當時事件 $\lbrace X=a\rbrace$ 對應一條無面積的鉛直線段，故積分為 <span class="text-nowrap">$0$；</span>此處則是將同一概念向高一維度推廣，使單一截面不具任何體積。

</div>

(3) 在多變數的情況下，性質 (3) 中的區域 $A$ 未必是**積空間 <span lang="en">(product space)</span>**；此時機率的計算便回到微積分的**重積分 <span lang="en">(double integral)</span>**，求取該區域上方的曲面下體積。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

積空間即「多維度的矩形」。以二維平面為例，矩形 $\lbrace a\leqslant x\leqslant b,\ c\leqslant y\leqslant d\rbrace$ 可寫成兩個實數區間的乘積 <span class="text-nowrap">$[a,b]\times[c,d]$，</span>其特色是各維度變數的取值範圍互不影響，整個實數平面 $\mathbb{R}^{2}$ 亦屬積空間；此一表示法可自然推廣至更高維度的空間。

</div>

若區域 $A$ 為積空間，積分範圍即可寫為 $\lbrace a\leqslant x\leqslant b,\ c\leqslant y\leqslant d\rbrace$ 的形式，此時重積分有以下特例:
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}\bigl((X,Y)\in A\bigr)&=\mathbb{P}\bigl(a\leqslant X\leqslant b,\ c\leqslant Y\leqslant d\bigr)\\[0.45em]
&=\int_{c}^{d}\int_{a}^{b}f_{\sssig XY}(x,y)\,dx\,dy=\int_{a}^{b}\int_{c}^{d}f_{\sssig XY}(x,y)\,dy\,dx
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}\bigl((X,Y)\in A\bigr)&=\mathbb{P}\bigl(a\leqslant X\leqslant b,\ c\leqslant Y\leqslant d\bigr)\\[0.45em]
&=\int_{c}^{d}\int_{a}^{b}f_{\sssig XY}(x,y)\,dx\,dy\\[0.45em]
&=\int_{a}^{b}\int_{c}^{d}f_{\sssig XY}(x,y)\,dy\,dx
\end{aligned}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

無論區域 $A$ 是否為積空間，在被積函數非負 (或絕對可積) 下，**富比尼定理 <span lang="en">(Fubini’s theorem)</span>** 皆保證雙重積分的順序可以調換；但**當 $A$ 不是積空間時，內外層積分上下限彼此相依，調換積分順序時務必隨之改寫對應的積分範圍**。

</div>

## 本篇小結

[Definition 3.5](#def-joint-pdf) 以積分給出聯合機率密度函數。二元連續型隨機向量 $(X,Y)$ 的 joint cdf 若能寫成某個非負函數 $f_{\sssig XY}$ 由 $-\infty$ 積到 $x$ 與 $y$ 的二重積分，該非負函數即為 $(X,Y)$ 的 joint pdf。它與單變數的 pdf 一樣不是機率，而是累積機率的變化率；差別在於 joint cdf 取的是曲面下所夾的體積，單變數的 cdf 取的則是曲線下所夾的面積。在 $\mathcal{R}\_{\sssig XY}$ 中的可微分點上，joint pdf 是 joint cdf 先後對兩個變數微分所得的二階偏導數，其餘各點取 <span class="text-nowrap">$0$。</span>

[Theorem 3.1](#thm-joint-pdf-proper) 列出 joint pdf 的三項性質，包含非負、在整個聯合值域上的二重積分為 <span class="text-nowrap">$1$，</span>以及對任意波雷爾集合 <span class="text-nowrap">$A$，</span>$(X,Y)$ 落在 $A$ 中的機率等於 $f_{\sssig XY}$ 在 $A\cap\mathcal{R}_{\sssig XY}$ 上的二重積分。由克萊羅定理可知 joint cdf 的偏微分順序永遠可以交換；單點機率與單面機率都是 <span class="text-nowrap">$0$；</span>集合 $A$ 若不是積空間，第三項性質便回到微積分的重積分，若是積空間則可寫成在兩個區間上依序積分的形式。不論是否為積空間，富比尼定理都保證積分順序可以調換，只是調換之後要留意積分的範圍是否需要修改。

[下一篇](/lecture-notes/marginal-probability-density-functions/)由聯合機率密度函數出發，介紹[邊際機率密度函數](/lecture-notes/marginal-probability-density-functions/#def-marginal-pdf)。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
