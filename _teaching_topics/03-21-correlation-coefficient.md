---
title: "相關係數"
subtitle: "The Correlation Coefficient"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 21
order: 321
permalink: /lecture-notes/correlation-coefficient/
date: 2026-08-13
published: false
excerpt: "共變異數的正負號說明了兩個變數共同變化的方向，卻沒有範圍限制，因而看不出相關程度的上限，也無法比較兩組不同的二元分配何者的相關程度比較高。相關係數把 $X$ 與 $Y$ 各自的變異程度先行消除，形成一個標準化的形式，所衡量的是線性相關的強度，也就是 $X$ 與 $Y$ 之間的關係有多接近直線，其值恆落在 $-1$ 與 $1$ 之間。由定義可以整理出 $\\rho_{\\sssig XY}$ 等於共變異數除以兩個標準差相乘的簡易表示式，並依取值把相關程度分成完全正相關、正相關、零相關、負相關與完全負相關五類；零相關只表示沒有直線關係，二次曲線那樣明顯的關係仍然可能是零相關。本篇最後證明相關係數的六款性質，其中範圍落在 $-1$ 與 $1$ 之間這一款用到隨機變數版本的柯西-舒瓦茲不等式，並說明相關係數的幾何意義就是兩個隨機變數在變數空間中夾角的餘弦值。"
---

[上一篇](/lecture-notes/covariance-matrix/)把[共變異數](/lecture-notes/covariance/#def-covariance)推廣到[隨機向量](/lecture-notes/random-vectors-joint-pmf/#def-random-vector)之上，以 [Definition 3.17](/lecture-notes/covariance-matrix/#def-covar-matrix) 的[共變異數矩陣](/lecture-notes/covariance-matrix/#def-covar-matrix)收納各個分量兩兩之間的共變異數，並整理了常數向量與矩陣作用在隨機向量上時，[期望值](/lecture-notes/expectation/#def-expectation)與共變異數矩陣的算法。

共變異數的正負號說明了 $X$ 與 $Y$ 共同變化的方向，但它沒有範圍限制，因此看不出相關程度的上限，也無法用來比較兩組不同的二元分配間，哪一組的相關程度比較高。本篇要介紹的相關係數即是為此而設，它在共變異數之外，額外把 $X$ 與 $Y$ 各自的變異程度消除掉。本篇先給出定義與一條比較簡易的表示式，再依相關係數的取值把相關程度分成五類並以散佈圖圖示，接著證明相關係數的六款性質，最後說明相關係數的幾何意義。

## 相關係數的定義與相關程度的分類

<div id="def-corr" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 3.19 (相關係數, correlation coefficient)</div>

若 $X$ 與 $Y$ 為二[隨機變數](/lecture-notes/random-variables-and-pmf/#def-random-variable)，且期望值分別為 $\mu_{\sssig X}$ 與 <span class="text-nowrap">$\mu_{\sssig Y}$，</span>變異數分別為 <span class="text-nowrap">$\sigma_{\sssig X}^{2}, \sigma_{\sssig Y}^{2}$，</span>則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\rho_{\sssig XY}=\operatorname{Corr}(X,Y)=\mathbb{E}\Biggl[\biggl(\frac{X-\mu_{\sssig X}}{\sigma_{\sssig X}}\biggr)\biggl(\frac{Y-\mu_{\sssig Y}}{\sigma_{\sssig Y}}\biggr)\Biggr]
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\rho_{\sssig XY}&=\operatorname{Corr}(X,Y)\\[0.45em]
&=\mathbb{E}\Biggl[\biggl(\frac{X-\mu_{\sssig X}}{\sigma_{\sssig X}}\biggr)\biggl(\frac{Y-\mu_{\sssig Y}}{\sigma_{\sssig Y}}\biggr)\Biggr]
\end{aligned}
$$

</div>

為 $X$ 與 $Y$ 的**相關係數 <span lang="en">(correlation coefficient)</span>**

</div>

相關係數有一些地方需要注意:

(1) 相關係數與共變異數相當類似，只是相關係數額外將 $X$ 與 $Y$ 的變異程度給消除掉，形成一個**標準化 <span lang="en">(standardized)</span>** 的形式，如此便限制了相關係數的範圍必須在 $1$ 與 $-1$ 之間，稍後我們會詳述此性質。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

事實上，$\frac{X-\mu_{\sssig X}}{\sigma_{\sssig X}}$ 與 $\frac{Y-\mu_{\sssig Y}}{\sigma_{\sssig Y}}$ 即是對 $X$ 與 $Y$ 標準化，而標準化隨機變數具有期望值是 $0$ 且變異數是 $1$ 的特色，且上述定義可改為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\rho_{\sssig XY}=\operatorname{Cov}\biggl(\frac{X-\mu_{\sssig X}}{\sigma_{\sssig X}},\ \frac{Y-\mu_{\sssig Y}}{\sigma_{\sssig Y}}\biggr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\rho_{\sssig XY}&=\operatorname{Cov}\biggl(\frac{X-\mu_{\sssig X}}{\sigma_{\sssig X}},\ \frac{Y-\mu_{\sssig Y}}{\sigma_{\sssig Y}}\biggr)
\end{aligned}
$$

</div>

這個寫法更具直觀意義。

</div>

(2) 相關係數所衡量的相關性，是指線性相關 <span lang="en">(linear correlation)</span> 的強度，換句話說就是 **$X$ 與 $Y$ 之間的關係有多接近直線**。
{: .topic-paren-item}

線性相關程度，是指相關係數的數值 (即 <span class="text-nowrap">$\lvert\rho_{\sssig XY}\rvert$)，</span>其值越大 (表示 $\rho_{\sssig XY}$ 越接近 $1$ 或 <span class="text-nowrap">$-1$)，</span>則觀察值的散佈情形越接近一條直線；反之，其值越小 (越接近 <span class="text-nowrap">$0$)，</span>則越不具直線關係。
{: .topic-paren-cont}

下圖是 $\rho_{\sssig XY}=0.6$ 與 $\rho_{\sssig XY}=0.99$ 的聯合分配抽取樣本形成的散佈圖 <span lang="en">(scatter plot)</span>:
{: .topic-paren-cont}

<figure id="fig-correlation-strength-scatter" class="topic-figure topic-figure--wide">
  <img src="/images/lecture-notes/correlation-strength-scatter.svg" alt="左右並排的兩個面板，共用同一組座標範圍與同一個比例尺。每個面板各有一條橫軸與一條縱軸交於原點，橫軸末端標為 x、縱軸末端標為 y，兩軸各標出 −2、−1、1、2 四個刻度。每個面板畫了數百個小圓點，另有一條通過原點、由左下往右上的直線。左面板的點散成一團橢圓形的雲，沿著那條直線的方向拉長，離線較遠的點不少，面板下方標 ρ_XY = 0.6。右面板的點幾乎都貼著那條直線，排成一條窄帶，面板下方標 ρ_XY = 0.99。">
  <figcaption><span class="topic-figure__label">Fig. 3.18.</span> 左右兩個面板共用同一組座標範圍與同一個比例尺，各畫一批樣本的散佈，並附同一條斜率為正的參考直線。左面板所標的 $\rho_{\sssig XY}$ 較小，點散得開，離參考直線遠的不少；右面板所標的 <span class="text-nowrap">$\rho_{\sssig XY}$</span> 接近 <span class="text-nowrap">$1$，</span>點幾乎都貼著參考直線排成一條窄帶。<span class="text-nowrap">$\lvert\rho_{\sssig XY}\rvert$</span> 越大，點的散佈就越接近一條直線，這正是相關係數所衡量的線性相關強度。</figcaption>
</figure>

上面二張圖中，左圖是由相關係數 $0.6$ 的聯合分配所抽出來的，而右圖是由相關係數高達 $0.99$ 的聯合分配中所抽出來的，其散佈情況相當接近一條斜直線。
{: .topic-paren-cont}

(3) 由相關係數的定義，我們可以得到一個比較簡易的表示式，即
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\operatorname{Corr}(X,Y)&=\frac{1}{\sigma_{\sssig X}\,\sigma_{\sssig Y}}\mathbb{E}\Bigl[(X-\mu_{\sssig X})(Y-\mu_{\sssig Y})\Bigr]\\[0.45em]
&=\frac{\sigma_{\sssig XY}}{\sigma_{\sssig X}\,\sigma_{\sssig Y}}=\frac{\operatorname{Cov}(X,Y)}{\sqrt{\mathrm{Var}(X)\,\mathrm{Var}(Y)}}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\operatorname{Corr}(X,Y)&=\frac{1}{\sigma_{\sssig X}\,\sigma_{\sssig Y}}\mathbb{E}\Bigl[(X-\mu_{\sssig X})(Y-\mu_{\sssig Y})\Bigr]\\[0.45em]
&=\frac{\sigma_{\sssig XY}}{\sigma_{\sssig X}\,\sigma_{\sssig Y}}=\frac{\operatorname{Cov}(X,Y)}{\sqrt{\mathrm{Var}(X)\,\mathrm{Var}(Y)}}
\end{aligned}
$$

</div>

(4) 相關係數與共變異數相同之處在於，相關係數的正負號分別對應了正相關及負相關，也對應到上圖中直線斜率的符號；而若相關係數為 $0$ 則代表零相關。但是讀者應特別注意一點，雖然相關係數的符號與斜率的符號會相同，但**相關係數的數值大小與斜率的數值大小沒有關係**。
{: .topic-paren-item}

(5) 相關係數與共變異數最大的不同在有範圍限制，因此我們可以看出相關程度的上限，也能夠以此比較兩組不同的二元分配間，哪一組的相關程度比較高，這都是共變異數所做不到的地方，也正因此，我們可以將其分類如下:
{: .topic-paren-item}

- 若 <span class="text-nowrap">$\rho_{\sssig XY}=1$，</span>則稱 $X$ 與 $Y$ **完全正相關 <span lang="en">(perfect positive correlated)</span>**
- 若 <span class="text-nowrap">$0<\rho_{\sssig XY}<1$，</span>則稱 $X$ 與 $Y$ **正相關 <span lang="en">(positive correlated)</span>**
- 若 <span class="text-nowrap">$\rho_{\sssig XY}=0$，</span>則稱 $X$ 與 $Y$ **零相關 <span lang="en">(uncorrelated)</span>**
- 若 <span class="text-nowrap">$-1<\rho_{\sssig XY}<0$，</span>則稱 $X$ 與 $Y$ **負相關 <span lang="en">(negative correlated)</span>**
- 若 <span class="text-nowrap">$\rho_{\sssig XY}=-1$，</span>則稱 $X$ 與 $Y$ **完全負相關 <span lang="en">(perfect negative correlated)</span>**

(6) 下面我們便將以上的五種分類情況圖示如下:
{: .topic-paren-item}

<figure id="fig-correlation-types-scatter" class="topic-figure topic-figure--wide">
  <img src="/images/lecture-notes/correlation-types-scatter.svg" alt="六個面板排成三列，每列兩個，共用同一組座標範圍與同一個比例尺。每個面板各有一條橫軸與一條縱軸交於原點，橫軸末端標為 x、縱軸末端標為 y，兩軸都標出整數刻度，面板下方各標一行相關係數的式子。第一列左邊的點全部落在一條由左下往右上的直線上，標 ρ_XY = 1；右邊的點散成一團沿同一方向拉長的橢圓形雲，標 0 &lt; ρ_XY &lt; 1。第二列左邊的點全部落在一條由左上往右下的直線上，標 ρ_XY = −1；右邊的點散成一團沿該方向拉長的橢圓形雲，標 −1 &lt; ρ_XY &lt; 0。這四個面板另各畫一條與點的走向相同的直線。第三列左邊的點散成一團沒有特定方向的圓形雲，標 ρ_XY = 0；右邊的點排成一條開口向上、頂點落在原點的曲線，縱軸只取正值，同樣標 ρ_XY = 0。第三列的兩個面板都沒有那條參考直線。">
  <figcaption><span class="topic-figure__label">Fig. 3.19.</span> 六個面板排成三列，每列兩個，畫出五種相關型態，最後一個面板另外畫零相關卻不獨立的情形。第一列左邊是完全正相關，點全落在同一條上升的直線上；右邊是正相關，點散成一團沿上升方向拉長的雲。第二列的方向相反，左邊是完全負相關，右邊是負相關。第三列左邊是零相關，點沒有方向可言。第三列右邊的點排成一條開口向上的二次曲線，$X$ 與 $Y$ 顯然有關係，<span class="text-nowrap">$\rho_{\sssig XY}$</span> 卻與左邊一樣是 <span class="text-nowrap">$0$，</span>因為相關係數只衡量線性的那一部分。前四個面板各附一條與該型態同號的參考直線，後兩個面板沒有參考直線。</figcaption>
</figure>

讀者或許好奇，最後一張圖中，$X$ 與 $Y$ 是二次函數的關係應是非常明顯的，但為何這樣還會說是零相關呢？這個原因在於，**相關性只用來衡量線性相關**。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

一個稍嫌不嚴謹但相對簡單的想法是，這裡的相關性指的是 $X$ 與 $Y$ 之間有沒有「$X$ 變大則 $Y$ 跟著變大」或「$X$ 變小則 $Y$ 跟著變小」的趨勢，而二次曲線在極值的左右兩側成長的趨勢正好相反，這會導致整體而言，$X$ 與 $Y$ 的相關趨勢互相抵銷而變為零相關。

</div>

## 相關係數的性質

<div id="thm-corr-proper" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 3.19 (相關係數的性質, correlation properties)</div>

若 $X$ 與 $Y$ 為二隨機變數，$a, b, c, d$ 為任意常數，則

<ol class="topic-list-paren">
  <li>
  若 $X$ $\indep$ <span class="text-nowrap">$Y$，</span>則
  $$
  \operatorname{Corr}(X,Y)=0
  $$
  </li>
  <li>
  $$
  \operatorname{Corr}(X,a)=0
  $$
  </li>
  <li>
  $$
  \operatorname{Corr}(X,X)=1
  $$
  </li>
  <li>
  <div class="topic-math-layout topic-math-layout--desktop">
  $$
  \operatorname{Corr}\bigl(aX+c,\,bY+d\bigr)=\operatorname{sgn}(ab)\cdot\operatorname{Corr}\bigl(X,Y\bigr)
  $$
  </div>
  <div class="topic-math-layout topic-math-layout--mobile">
  $$
  \begin{aligned}
  \operatorname{Corr}\bigl(&aX+c,\,bY+d\bigr)\\[0.45em]
  &=\operatorname{sgn}(ab)\cdot\operatorname{Corr}\bigl(X,Y\bigr)
  \end{aligned}
  $$
  </div>
  其中 $\operatorname{sgn}(\cdot)$ 表示符號函數
  </li>
  <li>
  $$
  \operatorname{Corr}(X,Y)=\operatorname{Corr}(Y,X)
  $$
  </li>
  <li>
  $$
  -1\leqslant\operatorname{Corr}(X,Y)\leqslant1
  $$
  </li>
</ol>

</div>

<div class="topic-proof" markdown="1">
**Proof.**

(1) 若 $X$ $\indep$ <span class="text-nowrap">$Y$，</span>則
{: .topic-paren-item}

$$
\operatorname{Cov}(X,Y)=0\qquad\therefore\, \operatorname{Corr}(X,Y)=0
$$

(2)
{: .topic-paren-item}

$$
\operatorname{Cov}(X,a)=0\qquad\therefore\, \operatorname{Corr}(X,a)=0
$$

(3)
{: .topic-paren-item}

<div class="topic-math-follow-before" markdown="1">

$$
\operatorname{Cov}(X,X)=\mathrm{Var}(X)
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop topic-math-follow" markdown="1">

$$
\Longrightarrow\ \operatorname{Corr}(X,X)=\frac{\operatorname{Cov}(X,X)}{\sqrt{\mathrm{Var}(X)\,\mathrm{Var}(X)}}=1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile topic-math-follow" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ \operatorname{Corr}(X,X)&=\frac{\operatorname{Cov}(X,X)}{\sqrt{\mathrm{Var}(X)\,\mathrm{Var}(X)}}\\[0.2em]
&=1
\end{aligned}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個性質顯示，自己與自己的相關性，永恆是 <span class="text-nowrap">$1$。</span>

</div>

(4)
{: .topic-paren-item}

$$
\operatorname{Cov}\bigl(aX+c,\,bY+d\bigr)=ab\,\operatorname{Cov}(X,Y)
$$

由[變異數的性質](/lecture-notes/variance/#thm-variance-properties)可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop topic-math-follow-before" markdown="1">

$$
\mathrm{Var}(aX+c)=a^{2}\,\mathrm{Var}(X),\quad \mathrm{Var}(bY+d)=b^{2}\,\mathrm{Var}(Y)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile topic-math-follow-before" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(aX+c)&=a^{2}\,\mathrm{Var}(X),\\[0.45em]
\mathrm{Var}(bY+d)&=b^{2}\,\mathrm{Var}(Y)
\end{aligned}
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop topic-math-follow" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ \operatorname{Corr}\bigl(aX+c,\,bY+d\bigr)&=\frac{\operatorname{Cov}\bigl(aX+c,\,bY+d\bigr)}{\sqrt{\mathrm{Var}(aX+c)\,\mathrm{Var}(bY+d)}}\\[0.45em]
&=\frac{ab\,\operatorname{Cov}(X,Y)}{\lvert ab\rvert\sqrt{\mathrm{Var}(X)\,\mathrm{Var}(Y)}}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile topic-math-follow" markdown="1">

$$
\begin{aligned}
&\Longrightarrow\ \operatorname{Corr}\bigl(aX+c,\,bY+d\bigr)\\[0.45em]
&=\frac{\operatorname{Cov}\bigl(aX+c,\,bY+d\bigr)}{\sqrt{\mathrm{Var}(aX+c)\,\mathrm{Var}(bY+d)}}\\[0.45em]
&=\frac{ab\,\operatorname{Cov}(X,Y)}{\lvert ab\rvert\sqrt{\mathrm{Var}(X)\,\mathrm{Var}(Y)}}
\end{aligned}
$$

</div>

且由於
{: .topic-paren-cont}

<div class="topic-math-follow-before" markdown="1">

$$
\frac{ab}{\lvert ab\rvert}=\operatorname{sgn}(ab)=\left\lbrace
\begin{array}{c@{\quad}l}
1, & \text{if } ab>0\\[0.6em]
-1, & \text{if } ab<0
\end{array}
\right.
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop topic-math-follow" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ \operatorname{Corr}\bigl(aX+c,\,bY+d\bigr)&=\left\lbrace
\begin{array}{c@{\quad}l}
\operatorname{Corr}(X,Y), & \text{if } ab>0\\[0.6em]
-\operatorname{Corr}(X,Y), & \text{if } ab<0
\end{array}
\right.\\[0.45em]
&=\operatorname{sgn}(ab)\cdot\operatorname{Corr}\bigl(X,Y\bigr)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile topic-math-follow" markdown="1">

$$
\begin{aligned}
&\Longrightarrow\ \operatorname{Corr}\bigl(aX+c,\,bY+d\bigr)\\[0.45em]
&=\left\lbrace
\begin{array}{c@{\quad}l}
\operatorname{Corr}(X,Y), & \text{if } ab>0\\[0.6em]
-\operatorname{Corr}(X,Y), & \text{if } ab<0
\end{array}
\right.\\[0.45em]
&=\operatorname{sgn}(ab)\cdot\operatorname{Corr}\bigl(X,Y\bigr)
\end{aligned}
$$

</div>

(5)
{: .topic-paren-item}

<div class="topic-math-follow-before" markdown="1">

$$
\operatorname{Cov}(X,Y)=\operatorname{Cov}(Y,X)
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop topic-math-follow" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ \operatorname{Corr}(X,Y)&=\frac{\operatorname{Cov}(X,Y)}{\sqrt{\mathrm{Var}(X)\,\mathrm{Var}(Y)}}\\[0.45em]
&=\frac{\operatorname{Cov}(Y,X)}{\sqrt{\mathrm{Var}(Y)\,\mathrm{Var}(X)}}=\operatorname{Corr}(Y,X)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile topic-math-follow" markdown="1">

$$
\begin{aligned}
&\Longrightarrow\ \operatorname{Corr}(X,Y)=\frac{\operatorname{Cov}(X,Y)}{\sqrt{\mathrm{Var}(X)\,\mathrm{Var}(Y)}}\\[0.45em]
&=\frac{\operatorname{Cov}(Y,X)}{\sqrt{\mathrm{Var}(Y)\,\mathrm{Var}(X)}}=\operatorname{Corr}(Y,X)
\end{aligned}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

相關性並沒有可伸縮的性質，不論是平方或是絕對值皆然；但相關性的方向卻會受係數的影響，這是因為相關係數在定義時，已經將單位尺度消除，故即使對隨機變數伸縮，相關係數也不會受到伸縮影響，僅需要考慮其方向 (即符號)。

</div>

<!-- errata-pending: 上一則 Note 的兩處，書稿 mathstatch3.tex 第 3965 行原文有誤，網頁改正。
     一、書稿作「但相關性的方向卻會係數的影響」，漏一個「受」字，句子沒有動詞；
     網頁作「但相關性的方向卻會受係數的影響」。
     二、書稿作「僅需要考慮考慮其方向 (即符號)」，「考慮」二字重出；
     網頁作「僅需要考慮其方向 (即符號)」。
     兩處均屬 ERRATA.md 欄位說明所列的 (3) 用詞與體例類，同型前例為 C2-84 (贅字)
     與 C2-108 (漏字誤植)，待作者裁定後登錄 ERRATA.md。
-->

(6) 令
{: .topic-paren-item}

$$
U=\frac{X-\mu_{\sssig X}}{\sigma_{\sssig X}},\quad V=\frac{Y-\mu_{\sssig Y}}{\sigma_{\sssig Y}}
$$

考慮 $\mathbb{E}\bigl[(U+t\,V)^{2}\bigr]$ 這個式子，其中 <span class="text-nowrap">$t\in\mathbb{R}$，</span>則
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[(U+t\,V)^{2}\bigr]&=\mathbb{E}\bigl(U^{2}+2t\,UV+t^{2}\,V^{2}\bigr)\\[0.45em]
&=\mathbb{E}\bigl(U^{2}\bigr)+2\,\mathbb{E}(UV)\,t+\mathbb{E}\bigl(V^{2}\bigr)\,t^{2}\geqslant0
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[(U+t\,V)^{2}\bigr]&=\mathbb{E}\bigl(U^{2}+2t\,UV+t^{2}\,V^{2}\bigr)\\[0.45em]
&=\mathbb{E}\bigl(U^{2}\bigr)+2\,\mathbb{E}(UV)\,t\\[0.2em]
&\qquad+\mathbb{E}\bigl(V^{2}\bigr)\,t^{2}\geqslant0
\end{aligned}
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\bigl(\because(U+t\,V)^{2}&\geqslant0\\[0.45em]
&\!\!\Longrightarrow\ \mathbb{E}\bigl[(U+tV)^{2}\bigr]\geqslant0\bigr)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\bigl(\because(U+t\,V)^{2}&\geqslant0\\[0.2em]
&\!\!\Longrightarrow\ \mathbb{E}\bigl[(U+tV)^{2}\bigr]\geqslant0\bigr)
\end{aligned}
$$

</div>

若將 $\mathbb{E}\bigl[(U+tV)^{2}\bigr]$ $=$ $\mathbb{E}\bigl(U^{2}\bigr)$ $+\,2\,\mathbb{E}(UV)\,t$ $+\,\mathbb{E}\bigl(V^{2}\bigr)\,t^{2}$ 視為 $t$ 的二次式，則可知
{: .topic-paren-cont}

$$
\begin{aligned}
&\Longrightarrow\ \bigl[2\,\mathbb{E}(UV)\bigr]^{2}-4\,\mathbb{E}\bigl(U^{2}\bigr)\mathbb{E}\bigl(V^{2}\bigr)\leqslant0\\[0.45em]
&\Longrightarrow\ \bigl[\mathbb{E}(UV)\bigr]^{2}\leqslant\mathbb{E}\bigl(U^{2}\bigr)\mathbb{E}\bigl(V^{2}\bigr)
\end{aligned}
$$

此不等式即隨機變數版本的**柯西-舒瓦茲不等式 <span lang="en">(Cauchy-Schwarz inequality)</span>**。
{: .topic-paren-cont}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

**柯西-舒瓦茲不等式**的一般形式是指以下的不等式: 若令 $U_1, \ldots, U_n,$ $V_1, \ldots, V_n$ 為實數，則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\biggl(\sum_{i=1}^{n}U_iV_i\biggr)^{2}\leqslant\biggl(\sum_{i=1}^{n}U_i^{2}\biggr)\biggl(\sum_{i=1}^{n}V_i^{2}\biggr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\biggl(&\sum_{i=1}^{n}U_iV_i\biggr)^{2}\\[0.45em]
&\leqslant\biggl(\sum_{i=1}^{n}U_i^{2}\biggr)\biggl(\sum_{i=1}^{n}V_i^{2}\biggr)
\end{aligned}
$$

</div>

其中，將上式改寫為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\biggl(\frac{1}{\,n\,}\sum_{i=1}^{n}U_iV_i\biggr)^{2}\leqslant\biggl(\frac{1}{\,n\,}\sum_{i=1}^{n}U_i^{2}\biggr)\biggl(\frac{1}{\,n\,}\sum_{i=1}^{n}V_i^{2}\biggr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\biggl(&\frac{1}{\,n\,}\sum_{i=1}^{n}U_iV_i\biggr)^{2}\\[0.45em]
&\leqslant\biggl(\frac{1}{\,n\,}\sum_{i=1}^{n}U_i^{2}\biggr)\biggl(\frac{1}{\,n\,}\sum_{i=1}^{n}V_i^{2}\biggr)
\end{aligned}
$$

</div>

則可與期望值類比，其與隨機變數版本的關聯即變得很清楚且容易理解。

</div>

由上述結果可以得到
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\bigl[\mathbb{E}(UV)\bigr]^{2}&=\Biggl(\mathbb{E}\biggl[\Bigl(\frac{X-\mu_{\sssig X}}{\sigma_{\sssig X}}\Bigr)\Bigl(\frac{Y-\mu_{\sssig Y}}{\sigma_{\sssig Y}}\Bigr)\biggr]\Biggr)^{2}=\rho_{\sssig XY}^{2}\\[0.45em]
&\leqslant\mathbb{E}\bigl(U^{2}\bigr)\mathbb{E}\bigl(V^{2}\bigr)\\[0.45em]
&=\mathbb{E}\biggl[\Bigl(\frac{X-\mu_{\sssig X}}{\sigma_{\sssig X}}\Bigr)^{2}\biggr]\,\mathbb{E}\biggl[\Bigl(\frac{Y-\mu_{\sssig Y}}{\sigma_{\sssig Y}}\Bigr)^{2}\biggr]=1\qquad\therefore\, -1\leqslant\rho_{\sssig XY}\leqslant1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\bigl[\mathbb{E}(UV)\bigr]^{2}&=\Biggl(\mathbb{E}\biggl[\Bigl(\frac{X-\mu_{\sssig X}}{\sigma_{\sssig X}}\Bigr)\Bigl(\frac{Y-\mu_{\sssig Y}}{\sigma_{\sssig Y}}\Bigr)\biggr]\Biggr)^{2}\\[0.2em]
&=\rho_{\sssig XY}^{2}\\[0.45em]
&\leqslant\mathbb{E}\bigl(U^{2}\bigr)\mathbb{E}\bigl(V^{2}\bigr)\\[0.2em]
&=\mathbb{E}\biggl[\Bigl(\frac{X-\mu_{\sssig X}}{\sigma_{\sssig X}}\Bigr)^{2}\biggr]\,\mathbb{E}\biggl[\Bigl(\frac{Y-\mu_{\sssig Y}}{\sigma_{\sssig Y}}\Bigr)^{2}\biggr]\\[0.2em]
&=1\qquad\therefore\, -1\leqslant\rho_{\sssig XY}\leqslant1
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
{: .topic-paren-cont}
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

在上述證明中，如果令存在唯一的 <span class="text-nowrap">$t\in\mathbb{R}$，</span>使得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\bigl[(U+tV)^{2}\bigr]=\mathbb{E}\bigl(U^{2}\bigr)+2\,\mathbb{E}(UV)\,t+\mathbb{E}\bigl(V^{2}\bigr)\,t^{2}=0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[(U+tV)^{2}\bigr]&=\mathbb{E}\bigl(U^{2}\bigr)+2\,\mathbb{E}(UV)\,t\\[0.2em]
&\qquad+\mathbb{E}\bigl(V^{2}\bigr)\,t^{2}=0
\end{aligned}
$$

</div>

則透過二次式的判別式，我們有 $\bigl[\mathbb{E}(UV)\bigr]^{2}$ $=$ $\mathbb{E}\bigl(U^{2}\bigr)\mathbb{E}\bigl(V^{2}\bigr)$ 的結論，此即 <span class="text-nowrap">$\rho_{\sssig XY}^{2}=1$。</span>

另一方面，<span class="text-nowrap">$\forall t\in\mathbb{R}$，</span>$U+tV$ 皆為一隨機變數，故由 $\mathbb{E}\bigl[(U+tV)^{2}\bigr]$ <span class="text-nowrap">$=0$，</span>$\forall t\in\mathbb{R}$ 可知 $\mathbb{P}(U+tV=0)$ <span class="text-nowrap">$=1$，</span>此即對任意數對 <span class="text-nowrap">$(U,V)$，</span>其觀察值在一直線上的機率為 <span class="text-nowrap">$1$，</span>符合 $\rho_{\sssig XY}^{2}=1$ 之結論。

一個簡單的例子是，令某分配為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}\bigl((X,Y)=(a_i,b_i)\bigr)=\frac{1}{\,n\,},\quad i=1,\ldots,n
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}\bigl((X,Y)=(a_i,b_i)\bigr)&=\frac{1}{\,n\,},\\[0.45em]
i&=1,\ldots,n
\end{aligned}
$$

</div>

則我們有

$$
\begin{gathered}
\mathbb{E}\bigl(X^{2}\bigr)=\frac{1}{\,n\,}\bigl(a_1^{2}+\cdots+a_n^{2}\bigr),\\[0.45em]
\mathbb{E}\bigl(Y^{2}\bigr)=\frac{1}{\,n\,}\bigl(b_1^{2}+\cdots+b_n^{2}\bigr),\\[0.45em]
\mathbb{E}(XY)=\frac{1}{\,n\,}\bigl(a_1b_1+\cdots+a_nb_n\bigr)
\end{gathered}
$$

由實數版本的柯西不等式可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl(X^{2}\bigr)\mathbb{E}\bigl(Y^{2}\bigr)&=\frac{1}{\,n\,}\bigl(a_1^{2}+\cdots+a_n^{2}\bigr)\,\frac{1}{\,n\,}\bigl(b_1^{2}+\cdots+b_n^{2}\bigr)\\[0.45em]
&\geqslant\Bigl[\frac{1}{\,n\,}\bigl(a_1b_1+\cdots+a_nb_n\bigr)\Bigr]^{2}=\bigl[\mathbb{E}(XY)\bigr]^{2}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl(X^{2}\bigr)\mathbb{E}\bigl(Y^{2}\bigr)&=\frac{1}{\,n\,}\bigl(a_1^{2}+\cdots+a_n^{2}\bigr)\\[0.2em]
&\qquad \frac{1}{\,n\,}\bigl(b_1^{2}+\cdots+b_n^{2}\bigr)\\[0.45em]
&\geqslant\Bigl[\frac{1}{\,n\,}\bigl(a_1b_1+\cdots+a_nb_n\bigr)\Bigr]^{2}\\[0.2em]
&=\bigl[\mathbb{E}(XY)\bigr]^{2}
\end{aligned}
$$

</div>

並且等號成立於

$$
a_i=t\,b_i,\quad i=1,\ldots,n,\ \exists t
$$

</div>

## 相關係數的幾何意義

事實上，相關係數另有幾何意義，即兩個隨機變數在變數空間中之「夾角的餘弦值」。

我們時常使用兩個向量夾角的餘弦值，取代直接說明其角度，並且當餘弦值為 $1$ 時，表示該二個向量夾角為 <span class="text-nowrap">$0$，</span>即「同向」；反之，餘弦值為 $-1$ 時則表示該二向量夾角為 <span class="text-nowrap">$\pi$，</span>即「反向」；又當餘弦值為 $0$ 時，表示該二個向量「垂直」，呼應了相關係數為 $1$ 代表完全正相關、相關係數為 $-1$ 代表完全負相關、而相關係數為 $0$ 則代表零相關的意義。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這些幾何意義不只在此處互相呼應，在線性代數、線性模型或是實驗設計的領域，我們亦常常把獨立的概念與垂直 (或譯直交 <span lang="en">(orthogonal)</span>) 的概念互相連結。

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這層意義在剛剛的簡例中更容易明白，我們可令 $\boldsymbol{a}$ $=$ $[a_1,\ldots,a_n]^{\mathrm{T}}$ 與 $\boldsymbol{b}$ $=$ <span class="text-nowrap">$[b_1,\ldots,b_n]^{\mathrm{T}}$，</span>則可得到

$$
\bigl(\lVert\boldsymbol{a}\rVert^{2}\,\lVert\boldsymbol{b}\rVert^{2}\bigr)\geqslant\bigl(\,\boldsymbol{a}^{\mathrm{T}}\,\boldsymbol{b}\,\bigr)^{2}
$$

此即

$$
-1\leqslant\cos(\boldsymbol{a},\boldsymbol{b})\leqslant1
$$

並且等號成立於

$$
a_i=t\,b_i,\quad i=1,\ldots,n,\ \exists t
$$

然讀者或許有些疑惑，這上述的 $\cos(\boldsymbol{a},\boldsymbol{b})$ 分明是對應到 <span class="text-nowrap">$\frac{\mathbb{E}(XY)}{\sqrt{\mathbb{E}(X^{2})\,\mathbb{E}(Y^{2})}}$，</span>如何能說是 $\rho_{\sssig XY}$ 呢？這其實是利用了向量平移不改變夾角的原理，才使得二者相等；而這一點亦可呼應相關係數的平移不變。

</div>

<!-- errata-pending: 上一段的分式，書稿 mathstatch3.tex 第 4006 行原文作
     \frac{\cov(X, Y)}{\,\E(X^2)\,\E(Y^2)\,}，網頁改為
     \frac{\mathbb{E}(XY)}{\sqrt{\mathbb{E}(X^{2})\,\mathbb{E}(Y^{2})}}。
     兩處更動的依據: 一、以該段自己的簡例代入，
     \cos(a, b) = a^T b / (||a|| ||b||)，而 E(XY) = (1/n) a^T b、
     E(X^2) = (1/n)||a||^2、E(Y^2) = (1/n)||b||^2，故分子應為 E(XY)、
     分母應開平方根。二、該段的設問是「這個由沒有先減去期望值的動差算出來的量，
     為何可以說成 rho」，若分子寫成 cov 就已經減去了期望值，設問本身不成立。
     屬 SITE_STYLE_CANON.md 第〇節第 3 點第 (1) 類 (書稿數學有誤)，
     待作者裁定後登錄 ERRATA.md。
-->

## 本篇小結

[Definition 3.19](#def-corr) 把共變異數往前推一步。先把 $X$ 與 $Y$ 分別標準化，再求兩者相乘的期望值，所得即 $X$ 與 $Y$ 的相關係數。由定義可以整理出 $\rho_{\sssig XY}$ 等於共變異數除以兩個[標準差](/lecture-notes/variance-standard-deviation/#def-standard-deviation)相乘的簡易表示式，也就是 $\operatorname{Corr}(X,Y)$ $=$ $\frac{\operatorname{Cov}(X,Y)}{\sqrt{\mathrm{Var}(X)\,\mathrm{Var}(Y)}}$ 這個式子。相關係數所衡量的是線性相關的強度，$\lvert\rho_{\sssig XY}\rvert$ 越大則觀察值的散佈情形越接近一條直線；要留意的是它的正負號雖然與直線斜率的符號一致，數值大小卻與斜率的數值大小沒有關係。

相關係數與共變異數最大的不同在有範圍限制，因此可以看出相關程度的上限，也能夠比較兩組不同的二元分配間哪一組的相關程度比較高，並依 $\rho_{\sssig XY}$ 的取值分成完全正相關、正相關、零相關、負相關與完全負相關五類。本篇的六面板散佈圖除了這五類之外，另畫了一組排成碗形的觀察值。$X$ 與 $Y$ 明明是二次函數的關係，相關係數卻是 <span class="text-nowrap">$0$，</span>因為二次曲線在極值左右兩側的成長趨勢正好相反，整體而言互相抵銷，而相關性只用來衡量線性相關。

[Theorem 3.19](#thm-corr-proper) 的六款性質，前五款都由[共變異數的對應性質](/lecture-notes/covariance/#thm-covar-proper)除以標準差之積而得，其中第四款顯示對 $X$ 與 $Y$ 作伸縮平移之後，相關係數至多只改變正負號，改變與否由 $\operatorname{sgn}(ab)$ 決定，這正是單位尺度已在定義時被消除的結果。第六款的範圍則另有一套作法。把兩個標準化變數的線性組合平方之後取期望值，得到 $t$ 的一個非負二次式，再由判別式非正推出隨機變數版本的柯西-舒瓦茲不等式，最後代回標準化變數即得 $-1\leqslant\rho_{\sssig XY}\leqslant1$ 這個範圍。等號成立的情形對應到觀察值全部落在一條直線上的機率為 $1$ 這件事。

相關係數另有幾何意義，即兩個隨機變數在變數空間中夾角的餘弦值: 餘弦值為 $1$ 表示同向、為 $-1$ 表示反向、為 $0$ 則表示垂直，恰好呼應完全正相關、完全負相關與零相關。這個餘弦值是由沒有先減去期望值的動差算出來的，之所以仍然等於 <span class="text-nowrap">$\rho_{\sssig XY}$，</span>靠的是向量平移不改變夾角這一點，這也再一次呼應相關係數的平移不變。

[下一篇](/lecture-notes/correlation-properties-and-matrix/)接著證明變異數-共變異數不等式，並把相關係數的想法推廣到隨機向量上，成為[相關矩陣](/lecture-notes/correlation-properties-and-matrix/#def-corr-matrix)。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
