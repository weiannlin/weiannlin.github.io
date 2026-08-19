---
title: "斯內德克 F 分配與變異數比值的抽樣分配"
subtitle: "Snedecor’s F Distribution and the Sampling Distribution of a Variance Ratio"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 4
topic: 22
order: 422
permalink: /teaching-topics/snedecor-f-distribution/
date: 2026-08-15
published: false
excerpt: "斯內德克 $\\mathcal{F}$ 分配正比於兩個獨立卡方分配的比值，因此常被當作變異數相關之檢定的抽樣分配。本篇先給出它的定義，說明由兩個獨立卡方變數各除以自身自由度再相除的建構方式，並證明其期望值為 $\\frac{\\nu_2}{\\nu_2-2}$。接著轉入常態母體之下統計量的抽樣分配，證明兩組獨立常態隨機樣本的樣本變異數比值除以母體變異數比值服從 $\\mathcal{F}(n_1-1,\\ n_2-1)$ 分配，並附上母體期望值皆已知時的對應版本。其後給出 $\\mathcal{F}$ 分配與貝塔分配的關係，指出 $\\frac{1}{1+\\frac{\\nu_1}{\\nu_2}F}$ 與 $\\frac{\\frac{\\nu_1}{\\nu_2}F}{1+\\frac{\\nu_1}{\\nu_2}F}$ 分別服從兩個參數互換的貝塔分配。最後以三道例題演練，依序處理卡方與 $\\mathcal{F}$ 分配的辨識、常態母體之下 $t$ 與 $\\mathcal{F}$ 的抽樣分配，以及以貝塔分配求算兩段長度比較的機率。"
---

[上一篇](/teaching-topics/student-t-distribution/)給出[司徒頓 $t$ 分配](/teaching-topics/student-t-distribution/#def-t-distribution)的定義，並在常態母體之下推導了樣本平均數 $\overline{X}$ 在母體變異數未知時的抽樣分配。四大常用抽樣分配之中，只剩下斯內德克 $\mathcal{F}$ 分配尚未介紹，本篇處理的就是這一個分配。

$\mathcal{F}$ 分配的建構方式與司徒頓 $t$ 分配相似，都是由標準常態分配與[卡方分配](/teaching-topics/chi-squared-distribution/#def-chi-distribution)這兩塊材料組合而成，差別在於 $t$ 分配取的是一個標準常態變數與一個卡方變數的比值，而 $\mathcal{F}$ 分配取的是兩個卡方變數各自除以自身自由度之後的比值。這個建構方式直接對應到統計推論的需求: 兩個常態母體的分散程度都是非負的量，比較兩者時用的是比值而不是差。

本篇先給出 $\mathcal{F}$ 分配的定義，說明其建構方式並證明其期望值，再轉入常態母體之下統計量的抽樣分配，證明兩獨立樣本的變異數比值所服從的分配。其後給出 $\mathcal{F}$ 分配與[貝塔分配](/teaching-topics/beta-function-and-distribution/#def-beta-distribution)之間的關係，這項關係所依據的正是 [Theorem 4.19](/teaching-topics/gamma-beta-relationship/#thm-gamma-to-beta) 獨立[伽瑪分配](/teaching-topics/gamma-distribution/#def-gamma-distribution)的比值與和。全篇另有三道例題作為演練。

## 斯內德克 $\mathcal{F}$ 分配

<div id="def-f-distribution" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 4.24 (斯內德克 $\mathcal{F}$ 分配, Snedecor’s $\mathcal{F}$ distribution)</div>

**適用範圍**:

斯內德克 $\mathcal{F}$ 分配 <span lang="en">(Snedecor’s $\mathcal{F}$ distribution)</span> 正比於兩個獨立的卡方分配的比值，因此時常被當作變異數相關之檢定的抽樣分配。

**值域範圍**:

$$
\mathcal{R}_{\sssig F}=\lbrace\,f\mid f>0\,\rbrace
$$

**表示式**:

$$
F\sim\mathcal{F}(\nu_1,\nu_2)
$$

**自由度**:

$\nu_1,\nu_2>0$ 為斯內德克 $\mathcal{F}$ 分配的分子與分母自由度，通常設為正整數，但不限於此。

**機率函數**:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f_{\sssig F}(f)&=\frac{\Gamma\bigl(\frac{\nu_1+\nu_2}{2}\bigr)}{\,\Gamma\bigl(\frac{\nu_1}{2}\bigr)\Gamma\bigl(\frac{\nu_2}{2}\bigr)\,}\biggl(\frac{\nu_1}{\nu_2}\biggr)^{\frac{\nu_1}{2}}f^{(\nu_1/2)-1}\biggl(1+\frac{\nu_1}{\nu_2}f\biggr)^{-(\nu_1+\nu_2)/2},\ f>0\\[0.45em]
&=\frac{1}{\,\mathcal{B}\bigl(\frac{\nu_1}{2},\frac{\nu_2}{2}\bigr)\,}\biggl(\frac{\nu_1}{\nu_2}\biggr)^{\frac{\nu_1}{2}}f^{(\nu_1/2)-1}\biggl(1+\frac{\nu_1}{\nu_2}f\biggr)^{-(\nu_1+\nu_2)/2},\ f>0
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig F}(f)&=\frac{\Gamma\bigl(\frac{\nu_1+\nu_2}{2}\bigr)}{\,\Gamma\bigl(\frac{\nu_1}{2}\bigr)\Gamma\bigl(\frac{\nu_2}{2}\bigr)\,}\biggl(\frac{\nu_1}{\nu_2}\biggr)^{\frac{\nu_1}{2}}\\[0.25em]
&\qquad f^{(\nu_1/2)-1}\\[0.25em]
&\qquad\biggl(1+\frac{\nu_1}{\nu_2}f\biggr)^{-(\nu_1+\nu_2)/2},\\[0.25em]
&\qquad\qquad f>0\\[0.5em]
&=\frac{1}{\,\mathcal{B}\bigl(\frac{\nu_1}{2},\frac{\nu_2}{2}\bigr)\,}\biggl(\frac{\nu_1}{\nu_2}\biggr)^{\frac{\nu_1}{2}}\\[0.25em]
&\qquad f^{(\nu_1/2)-1}\\[0.25em]
&\qquad\biggl(1+\frac{\nu_1}{\nu_2}f\biggr)^{-(\nu_1+\nu_2)/2},\\[0.25em]
&\qquad\qquad f>0
\end{aligned}
$$

</div>

**期望值、變異數**:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(F)&=\frac{\nu_2}{\,\nu_2-2\,}\quad(\,\nu_2\leqslant2\ \text{時期望值發散}\,)\\[0.45em]
\mathrm{Var}(F)&=\frac{\,2\nu_2^{2}(\nu_1+\nu_2-2)\,}{\nu_1(\nu_2-2)^{2}(\nu_2-4)}\quad(\,\nu_2\leqslant4\ \text{時變異數發散}\,)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(F)&=\frac{\nu_2}{\,\nu_2-2\,}\\[0.25em]
&\qquad(\,\nu_2\leqslant2\ \text{時期望值發散}\,)\\[0.5em]
\mathrm{Var}(F)&=\frac{\,2\nu_2^{2}(\nu_1+\nu_2-2)\,}{\nu_1(\nu_2-2)^{2}(\nu_2-4)}\\[0.25em]
&\qquad(\,\nu_2\leqslant4\ \text{時變異數發散}\,)
\end{aligned}
$$

</div>

</div>

斯內德克 $\mathcal{F}$ 分配有一些地方需要注意:

(1) $\mathcal{F}$ 分配的建構有賴於獨立的兩個卡方分配，構造如下:
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\text{令}\ X_1&\sim\chi^{2}(\nu_1)\indep X_2\sim\chi^{2}(\nu_2)\text{，定義}\ F=\frac{\,X_1/\nu_1\,}{\,X_2/\nu_2\,}\\[0.45em]
\text{則}\ F&\sim\mathcal{F}(\nu_1,\nu_2)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\text{令}\ X_1&\sim\chi^{2}(\nu_1)\indep X_2\sim\chi^{2}(\nu_2)\text{，}\\[0.45em]
\text{定義}\ F&=\frac{\,X_1/\nu_1\,}{\,X_2/\nu_2\,}\\[0.45em]
\text{則}\ F&\sim\mathcal{F}(\nu_1,\nu_2)
\end{aligned}
$$

</div>

其中，分子自由度 <span class="text-nowrap">$\nu_1$，</span>正是 $X_1$ 的自由度 <span class="text-nowrap">$\nu_1$；</span>分母自由度 <span class="text-nowrap">$\nu_2$，</span>正是 $X_2$ 的自由度 <span class="text-nowrap">$\nu_2$。</span>
{: .topic-paren-cont}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

在兩個獨立常態母體的推論中，我們想比較的事情，除了期望值之外，通常會是這兩個母體的分散程度，然而分散程度是一個非負的值，因此二者的比較並不是互相加減，而是應該用分散程度的比值來推論，這也是建構 $\mathcal{F}$ 分配的基礎。

</div>

(2) 我們僅證明斯內德克 $\mathcal{F}$ 分配的期望值，並借助 $X_1\indep X_2$ 的特性來完成。證明如下:
{: .topic-paren-item}

<div class="topic-proof" markdown="1">
**Proof.**

由 $X_1\indep X_2$ 可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(F)&=\mathbb{E}\biggl(\frac{\,X_1/\nu_1\,}{\,X_2/\nu_2\,}\biggr)=\frac{\,\nu_2\,}{\,\nu_1\,}\mathbb{E}(X_1)\mathbb{E}\biggl(\frac{1}{\,X_2\,}\biggr)\\[0.45em]
&=\frac{\,\nu_2\,}{\,\nu_1\,}\times\nu_1\times\frac{1}{\,\nu_2-2\,}=\frac{\nu_2}{\,\nu_2-2\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(F)&=\mathbb{E}\biggl(\frac{\,X_1/\nu_1\,}{\,X_2/\nu_2\,}\biggr)\\[0.45em]
&=\frac{\,\nu_2\,}{\,\nu_1\,}\mathbb{E}(X_1)\mathbb{E}\biggl(\frac{1}{\,X_2\,}\biggr)\\[0.45em]
&=\frac{\,\nu_2\,}{\,\nu_1\,}\times\nu_1\times\frac{1}{\,\nu_2-2\,}\\[0.45em]
&=\frac{\nu_2}{\,\nu_2-2\,}
\end{aligned}
$$

</div>

其中，$\mathbb{E}\bigl(\frac{1}{\,X_2\,}\bigr)$ 在 $\nu_2\leqslant2$ 時並不存在，故此時期望值 $\mathbb{E}(F)$ 不存在。原式得證。 <span class="topic-qed">$\square$</span>
</div>

(3) 斯內德克 $\mathcal{F}$ 分配在不同自由度的組合時，圖形差異頗大。下面便將幾個不同參數的 $\mathcal{F}$ 分配的機率密度函數繪製在下方:
{: .topic-paren-item}

<figure id="fig-snedecor-f-density-family" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/snedecor-f-density-family.svg" alt="一條向右延伸的水平座標軸，軸上有五個刻度，由左至右標為 0、1、2、3、4，軸的右端標 f。座標軸上方有四條密度曲線。一條實線與一條點線都貼著座標軸的左端急速上升並穿出圖的上緣，之後一路下降，尾部貼著座標軸向右延伸，點線的下降比實線快。一條虛線由原點附近升起，在 0 與 1 之間形成一個又低又寬的隆起，之後緩緩下降，是右端最高的一條。另一條較粗的實線也由原點附近升起，在 1 附近形成一個又高又窄的尖峰，兩側迅速落回座標軸。圖的右上角有一個圖例，四段短線由上而下依序標為花體 F 括號 ν 下標 1 等於 1 逗號 ν 下標 2 等於 1、花體 F 括號 ν 下標 1 等於 1 逗號 ν 下標 2 等於 100、花體 F 括號 ν 下標 1 等於 100 逗號 ν 下標 2 等於 1，以及花體 F 括號 ν 下標 1 等於 100 逗號 ν 下標 2 等於 100。">
  <figcaption><span class="topic-figure__label">Fig. 4.9.</span> 四條密度曲線畫在同一組座標軸上，圖例標出各條的分子自由度 $\nu_1$ 與分母自由度 <span class="text-nowrap">$\nu_2$。</span>$\nu_1$ 小的兩條在靠近 $0$ 的一端往上發散，$\nu_1$ 大的兩條則由 $0$ 升起而成單峰，其中 $\nu_2$ 大的那一條的峰又高又窄。</figcaption>
</figure>

## 兩獨立樣本變異數比值的抽樣分配

以下轉入常態母體之下統計量的抽樣分配。下列定理談的是兩組獨立的隨機樣本各自來自[常態分配](/teaching-topics/normal-distribution/#def-normal)時，其樣本變異數的比值所服從的分配，層次與上面所談 $\mathcal{F}$ 分配自身的性質不同。

<div id="thm-s-sq-ratio-samp-dist" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 4.25 (兩獨立樣本變異數比值的抽樣分配, 兩母體期望值皆未知)</div>

若

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
X_1,X_2,\ldots,X_{n_1}\overset{\mathrm{iid}}{\sim}\mathcal{N}(\mu_1,\sigma_1^{2})\indep Y_1,Y_2,\ldots,Y_{n_2}\overset{\mathrm{iid}}{\sim}\mathcal{N}(\mu_2,\sigma_2^{2})
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
X_1,X_2,\ldots,X_{n_1}&\overset{\mathrm{iid}}{\sim}\mathcal{N}(\mu_1,\sigma_1^{2})\\[0.45em]
\indep\ Y_1,Y_2,\ldots,Y_{n_2}&\overset{\mathrm{iid}}{\sim}\mathcal{N}(\mu_2,\sigma_2^{2})
\end{aligned}
$$

</div>

其中 $\sigma_1^{2},\sigma_2^{2}$ 為待估參數，且 $\mu_1,\mu_2$ 皆未知，則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F=\frac{\,S_1^{2}/S_2^{2}\,}{\sigma_1^{2}/\sigma_2^{2}}=\frac{\dfrac{\frac{\,(n_1-1)S_1^{2}\,}{\sigma_1^{2}}}{n_1-1}}{\,\dfrac{\frac{\,(n_2-1)S_2^{2}\,}{\sigma_2^{2}}}{n_2-1}\,}\sim\mathcal{F}(n_1-1,\ n_2-1)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F&=\frac{\,S_1^{2}/S_2^{2}\,}{\sigma_1^{2}/\sigma_2^{2}}\\[0.45em]
&=\frac{\dfrac{\frac{\,(n_1-1)S_1^{2}\,}{\sigma_1^{2}}}{n_1-1}}{\,\dfrac{\frac{\,(n_2-1)S_2^{2}\,}{\sigma_2^{2}}}{n_2-1}\,}\\[0.45em]
&\sim\mathcal{F}(n_1-1,\ n_2-1)
\end{aligned}
$$

</div>

其中

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
S_1^{2}=\frac{1}{\,n_1-1\,}\sum_{i=1}^{n_1}(X_i-\overline{X})^{2},\quad S_2^{2}=\frac{1}{\,n_2-1\,}\sum_{i=1}^{n_2}(Y_i-\overline{Y})^{2}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
S_1^{2}&=\frac{1}{\,n_1-1\,}\sum_{i=1}^{n_1}(X_i-\overline{X})^{2},\\[0.45em]
S_2^{2}&=\frac{1}{\,n_2-1\,}\sum_{i=1}^{n_2}(Y_i-\overline{Y})^{2}
\end{aligned}
$$

</div>

</div>

<div class="topic-proof" markdown="1">
**Proof.**

由於

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
X_1,X_2,\ldots,X_{n_1}\overset{\mathrm{iid}}{\sim}\mathcal{N}(\mu_1,\sigma_1^{2})\indep Y_1,Y_2,\ldots,Y_{n_2}\overset{\mathrm{iid}}{\sim}\mathcal{N}(\mu_2,\sigma_2^{2})
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
X_1,X_2,\ldots,X_{n_1}&\overset{\mathrm{iid}}{\sim}\mathcal{N}(\mu_1,\sigma_1^{2})\\[0.45em]
\indep\ Y_1,Y_2,\ldots,Y_{n_2}&\overset{\mathrm{iid}}{\sim}\mathcal{N}(\mu_2,\sigma_2^{2})
\end{aligned}
$$

</div>

故可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\frac{\,(n_1-1)S_1^{2}\,}{\sigma_1^{2}}\sim\chi^{2}(n_1-1)\indep\frac{\,(n_2-1)S_2^{2}\,}{\sigma_2^{2}}\sim\chi^{2}(n_2-1)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\frac{\,(n_1-1)S_1^{2}\,}{\sigma_1^{2}}&\sim\chi^{2}(n_1-1)\\[0.45em]
\indep\ \frac{\,(n_2-1)S_2^{2}\,}{\sigma_2^{2}}&\sim\chi^{2}(n_2-1)
\end{aligned}
$$

</div>

若令

$$
F=\frac{\dfrac{\frac{\,(n_1-1)S_1^{2}\,}{\sigma_1^{2}}}{n_1-1}}{\,\dfrac{\frac{\,(n_2-1)S_2^{2}\,}{\sigma_2^{2}}}{n_2-1}\,}
$$

則有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F=\frac{S_1^{2}/S_2^{2}}{\,\sigma_1^{2}/\sigma_2^{2}\,}=\frac{\dfrac{\,S_1^{2}\,}{\sigma_1^{2}}}{\,\dfrac{\,S_2^{2}\,}{\sigma_2^{2}}\,}=\frac{\dfrac{\frac{\,(n_1-1)S_1^{2}\,}{\sigma_1^{2}}}{n_1-1}}{\,\dfrac{\frac{\,(n_2-1)S_2^{2}\,}{\sigma_2^{2}}}{n_2-1}\,}\sim\mathcal{F}(n_1-1,\ n_2-1)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F&=\frac{S_1^{2}/S_2^{2}}{\,\sigma_1^{2}/\sigma_2^{2}\,}=\frac{\dfrac{\,S_1^{2}\,}{\sigma_1^{2}}}{\,\dfrac{\,S_2^{2}\,}{\sigma_2^{2}}\,}\\[0.45em]
&=\frac{\dfrac{\frac{\,(n_1-1)S_1^{2}\,}{\sigma_1^{2}}}{n_1-1}}{\,\dfrac{\frac{\,(n_2-1)S_2^{2}\,}{\sigma_2^{2}}}{n_2-1}\,}\\[0.45em]
&\sim\mathcal{F}(n_1-1,\ n_2-1)
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

當然，這裡也有一個在實務上不會使用的版本如下:

**兩獨立樣本變異數比值 $S_1^{\prime2}/S_2^{\prime2}$ 的抽樣分配 ($\mu_1,\mu_2$ 皆已知)**:

若

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
X_1,X_2,\ldots,X_{n_1}\overset{\mathrm{iid}}{\sim}\mathcal{N}(\mu_1,\sigma_1^{2})\indep Y_1,Y_2,\ldots,Y_{n_2}\overset{\mathrm{iid}}{\sim}\mathcal{N}(\mu_2,\sigma_2^{2})
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
X_1,X_2,\ldots,X_{n_1}&\overset{\mathrm{iid}}{\sim}\mathcal{N}(\mu_1,\sigma_1^{2})\\[0.45em]
\indep\ Y_1,Y_2,\ldots,Y_{n_2}&\overset{\mathrm{iid}}{\sim}\mathcal{N}(\mu_2,\sigma_2^{2})
\end{aligned}
$$

</div>

其中 $\sigma_1^{2},\sigma_2^{2}$ 為待估參數，且 $\mu_1,\mu_2$ 皆已知，則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F=\frac{\,S_1^{\prime2}/S_2^{\prime2}\,}{\sigma_1^{2}/\sigma_2^{2}}=\frac{\dfrac{\frac{\,n_1S_1^{\prime2}\,}{\sigma_1^{2}}}{n_1}}{\,\dfrac{\frac{\,n_2S_2^{\prime2}\,}{\sigma_2^{2}}}{n_2}\,}\sim\mathcal{F}(n_1,\ n_2)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F&=\frac{\,S_1^{\prime2}/S_2^{\prime2}\,}{\sigma_1^{2}/\sigma_2^{2}}\\[0.45em]
&=\frac{\dfrac{\frac{\,n_1S_1^{\prime2}\,}{\sigma_1^{2}}}{n_1}}{\,\dfrac{\frac{\,n_2S_2^{\prime2}\,}{\sigma_2^{2}}}{n_2}\,}\\[0.45em]
&\sim\mathcal{F}(n_1,\ n_2)
\end{aligned}
$$

</div>

其中

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
S_1^{\prime2}=\frac{1}{\,n_1\,}\sum_{i=1}^{n_1}(X_i-\mu_1)^{2},\quad S_2^{\prime2}=\frac{1}{\,n_2\,}\sum_{i=1}^{n_2}(Y_i-\mu_2)^{2}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
S_1^{\prime2}&=\frac{1}{\,n_1\,}\sum_{i=1}^{n_1}(X_i-\mu_1)^{2},\\[0.45em]
S_2^{\prime2}&=\frac{1}{\,n_2\,}\sum_{i=1}^{n_2}(Y_i-\mu_2)^{2}
\end{aligned}
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.**

由於

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
X_1,X_2,\ldots,X_{n_1}\overset{\mathrm{iid}}{\sim}\mathcal{N}(\mu_1,\sigma_1^{2})\indep Y_1,Y_2,\ldots,Y_{n_2}\overset{\mathrm{iid}}{\sim}\mathcal{N}(\mu_2,\sigma_2^{2})
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
X_1,X_2,\ldots,X_{n_1}&\overset{\mathrm{iid}}{\sim}\mathcal{N}(\mu_1,\sigma_1^{2})\\[0.45em]
\indep\ Y_1,Y_2,\ldots,Y_{n_2}&\overset{\mathrm{iid}}{\sim}\mathcal{N}(\mu_2,\sigma_2^{2})
\end{aligned}
$$

</div>

故可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\frac{\,n_1S_1^{\prime2}\,}{\sigma_1^{2}}\sim\chi^{2}(n_1)\indep\frac{\,n_2S_2^{\prime2}\,}{\sigma_2^{2}}\sim\chi^{2}(n_2)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\frac{\,n_1S_1^{\prime2}\,}{\sigma_1^{2}}&\sim\chi^{2}(n_1)\\[0.45em]
\indep\ \frac{\,n_2S_2^{\prime2}\,}{\sigma_2^{2}}&\sim\chi^{2}(n_2)
\end{aligned}
$$

</div>

若令

$$
F=\frac{\dfrac{\frac{\,n_1S_1^{\prime2}\,}{\sigma_1^{2}}}{n_1}}{\,\dfrac{\frac{\,n_2S_2^{\prime2}\,}{\sigma_2^{2}}}{n_2}\,}
$$

則有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F=\frac{S_1^{\prime2}/S_2^{\prime2}}{\,\sigma_1^{2}/\sigma_2^{2}\,}=\frac{\dfrac{\,S_1^{\prime2}\,}{\sigma_1^{2}}}{\,\dfrac{\,S_2^{\prime2}\,}{\sigma_2^{2}}\,}=\frac{\dfrac{\frac{\,n_1S_1^{\prime2}\,}{\sigma_1^{2}}}{n_1}}{\,\dfrac{\frac{\,n_2S_2^{\prime2}\,}{\sigma_2^{2}}}{n_2}\,}\sim\mathcal{F}(n_1,\ n_2)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F&=\frac{S_1^{\prime2}/S_2^{\prime2}}{\,\sigma_1^{2}/\sigma_2^{2}\,}=\frac{\dfrac{\,S_1^{\prime2}\,}{\sigma_1^{2}}}{\,\dfrac{\,S_2^{\prime2}\,}{\sigma_2^{2}}\,}\\[0.45em]
&=\frac{\dfrac{\frac{\,n_1S_1^{\prime2}\,}{\sigma_1^{2}}}{n_1}}{\,\dfrac{\frac{\,n_2S_2^{\prime2}\,}{\sigma_2^{2}}}{n_2}\,}\\[0.45em]
&\sim\mathcal{F}(n_1,\ n_2)
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

</div>

## 斯內德克 $\mathcal{F}$ 分配的例題

<div id="ex-snedecor-f-1" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.55</div>

<div lang="en" markdown="1">
Suppose that $X_1,\ldots,X_{20}$ are independent random variables, each following the standard normal distribution, and put

$$
W_1=\sum_{i=1}^{10}X_i^{2},\qquad W_2=\sum_{i=11}^{20}X_i^{2}
$$

Determine which one of the following statements is false.

(A) $W_1$ follows the $\chi^{2}(10)$ distribution.
{: .topic-paren-item}

(B) $W_2$ follows the $\chi^{2}(10)$ distribution.
{: .topic-paren-item}

(C) $W_1+W_2$ follows the $\chi^{2}(20)$ distribution.
{: .topic-paren-item}

(D) $W_1/W_2$ follows the $\mathcal{F}(10,10)$ distribution.
{: .topic-paren-item}

(E) $X_1^{2}/W_2$ follows the $\mathcal{F}(1,10)$ distribution.
{: .topic-paren-item}
</div>

由題意可知 <span class="text-nowrap">$X_1,\ldots,X_{20}\overset{\mathrm{iid}}{\sim}\mathcal{N}(0,1)$，</span>則

<div class="topic-math-follow-before" markdown="1">

$$
X_1^{2},\ldots,X_{20}^{2}\overset{\mathrm{iid}}{\sim}\chi^{2}(1)
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop topic-math-follow" markdown="1">

$$
\Longrightarrow\ W_1=\sum_{i=1}^{10}X_i^{2}\sim\chi^{2}(10)\indep W_2=\sum_{i=11}^{20}X_i^{2}\sim\chi^{2}(10)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile topic-math-follow" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ W_1&=\sum_{i=1}^{10}X_i^{2}\sim\chi^{2}(10)\\[0.45em]
\indep\ W_2&=\sum_{i=11}^{20}X_i^{2}\sim\chi^{2}(10)
\end{aligned}
$$

</div>

故答案選 (E)，因為雖然 <span class="text-nowrap">$X_1^{2}\indep W_2$，</span>但 $\frac{X_1^{2}/1}{W_2/10}$ 的分配才是 <span class="text-nowrap">$\mathcal{F}(1,10)$，</span>而非 <span class="text-nowrap">$\frac{X_1^{2}}{W_2}$。</span>

</div>

<div id="ex-snedecor-f-2" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.56</div>

<div lang="en" markdown="1">
Suppose that $X_1,\ldots,X_5$ form a random sample of size $5$ drawn from the $\mathcal{N}(\mu,\sigma^{2})$ distribution, and let

$$
\overline{X}=\frac{1}{\,5\,}\sum_{i=1}^{5}X_i,\qquad S^{2}=\frac{1}{\,4\,}\sum_{i=1}^{5}(X_i-\overline{X})^{2}
$$

denote the sample mean and the sample variance, respectively. Determine which of the following statements are true.

(A) $\sqrt{5}(\overline{X}-\mu)/S$ follows the standard normal distribution.
{: .topic-paren-item}

(B) $\sqrt{5}(\overline{X}-\mu)/S$ follows the $t(5)$ distribution.
{: .topic-paren-item}

(C) $\sqrt{5}(\overline{X}-\mu)/S$ follows the $t(4)$ distribution.
{: .topic-paren-item}

(D) $5(\overline{X}-\mu)^{2}/S^{2}$ follows the $\mathcal{F}(5,1)$ distribution.
{: .topic-paren-item}

(E) $5(\overline{X}-\mu)^{2}/S^{2}$ follows the $\mathcal{F}(1,4)$ distribution.
{: .topic-paren-item}
</div>

由 $X_1,\ldots,X_5\overset{\mathrm{iid}}{\sim}\mathcal{N}(\mu,\sigma^{2})$ 可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\Longrightarrow\ \frac{\sqrt{5}(\overline{X}-\mu)}{S}=\frac{\,\overline{X}-\mu\,}{\dfrac{S}{\sqrt{5}}}\sim t(4)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ \frac{\sqrt{5}(\overline{X}-\mu)}{S}&=\frac{\,\overline{X}-\mu\,}{\dfrac{S}{\sqrt{5}}}\\[0.45em]
&\sim t(4)
\end{aligned}
$$

</div>

又由[科克蘭定理](/teaching-topics/chi-squared-distribution/#thm-cochran-theorem)知道

<div class="topic-math-layout topic-math-layout--desktop topic-math-follow-before" markdown="1">

$$
\frac{\,5(\overline{X}-\mu)^{2}\,}{\sigma^{2}}\sim\chi^{2}(1)\indep\frac{\,(5-1)S^{2}\,}{\sigma^{2}}\sim\chi^{2}(4)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile topic-math-follow-before" markdown="1">

$$
\begin{aligned}
\frac{\,5(\overline{X}-\mu)^{2}\,}{\sigma^{2}}&\sim\chi^{2}(1)\\[0.45em]
\indep\ \frac{\,(5-1)S^{2}\,}{\sigma^{2}}&\sim\chi^{2}(4)
\end{aligned}
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop topic-math-follow" markdown="1">

$$
\Longrightarrow\ \frac{\,5(\overline{X}-\mu)^{2}\,}{S^{2}}=\frac{\,\dfrac{\,5(\overline{X}-\mu)^{2}\,}{\sigma^{2}}\big/1\,}{\dfrac{\,(5-1)S^{2}\,}{\sigma^{2}}\big/(5-1)}\sim\mathcal{F}(1,4)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile topic-math-follow" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ \frac{\,5(\overline{X}-\mu)^{2}\,}{S^{2}}&=\frac{\,\dfrac{\,5(\overline{X}-\mu)^{2}\,}{\sigma^{2}}\big/1\,}{\dfrac{\,(5-1)S^{2}\,}{\sigma^{2}}\big/(5-1)}\\[0.45em]
&\sim\mathcal{F}(1,4)
\end{aligned}
$$

</div>

答案選 (C)、(E)。

</div>

## $\mathcal{F}$ 分配與貝塔分配的關係

<div id="thm-f-to-beta" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 4.26 ($\mathcal{F}$ 分配與貝塔分配的關係, relationship between the F and beta distributions)</div>

令 <span class="text-nowrap">$F\sim\mathcal{F}(\nu_1,\nu_2)$，</span>則可知

(1)
{: .topic-paren-item}

$$
\frac{1}{\,1+\frac{\nu_1}{\nu_2}F\,}\sim\mathrm{Beta}\left(\frac{\,\nu_2\,}{2},\frac{\,\nu_1\,}{2}\right)
$$

(2)
{: .topic-paren-item}

$$
\frac{\frac{\nu_1}{\nu_2}F}{\,1+\frac{\nu_1}{\nu_2}F\,}\sim\mathrm{Beta}\left(\frac{\,\nu_1\,}{2},\frac{\,\nu_2\,}{2}\right)
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.**

由於 <span class="text-nowrap">$F\sim\mathcal{F}(\nu_1,\nu_2)$，</span>可令

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
X_1\sim\chi^{2}(\nu_1)\indep X_2\sim\chi^{2}(\nu_2),\ \text{且}\ F=\frac{\,X_1/\nu_1\,}{\,X_2/\nu_2\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
X_1&\sim\chi^{2}(\nu_1)\indep X_2\sim\chi^{2}(\nu_2),\\[0.45em]
\text{且}\ F&=\frac{\,X_1/\nu_1\,}{\,X_2/\nu_2\,}
\end{aligned}
$$

</div>

則

$$
\frac{1}{\,1+\frac{\nu_1}{\nu_2}F\,}=\frac{X_2}{\,X_1+X_2\,}
$$

又

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
X_1\sim\mathrm{Gamma}\Bigl(\alpha=\frac{\nu_1}{2},\ \beta=2\Bigr),\quad X_2\sim\mathrm{Gamma}\Bigl(\alpha=\frac{\nu_2}{2},\ \beta=2\Bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
X_1&\sim\mathrm{Gamma}\Bigl(\alpha=\frac{\nu_1}{2},\ \beta=2\Bigr),\\[0.45em]
X_2&\sim\mathrm{Gamma}\Bigl(\alpha=\frac{\nu_2}{2},\ \beta=2\Bigr)
\end{aligned}
$$

</div>

可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\frac{1}{\,1+\frac{\nu_1}{\nu_2}F\,}=\frac{X_2}{\,X_1+X_2\,}\sim\mathrm{Beta}\left(\frac{\,\nu_2\,}{2},\frac{\,\nu_1\,}{2}\right)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\frac{1}{\,1+\frac{\nu_1}{\nu_2}F\,}&=\frac{X_2}{\,X_1+X_2\,}\\[0.45em]
&\sim\mathrm{Beta}\left(\frac{\,\nu_2\,}{2},\frac{\,\nu_1\,}{2}\right)
\end{aligned}
$$

</div>

又

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\frac{\frac{\nu_1}{\nu_2}F}{\,1+\frac{\nu_1}{\nu_2}F\,}=1-\frac{1}{\,1+\frac{\nu_1}{\nu_2}F\,}=\frac{X_1}{\,X_1+X_2\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\frac{\frac{\nu_1}{\nu_2}F}{\,1+\frac{\nu_1}{\nu_2}F\,}&=1-\frac{1}{\,1+\frac{\nu_1}{\nu_2}F\,}\\[0.45em]
&=\frac{X_1}{\,X_1+X_2\,}
\end{aligned}
$$

</div>

故知道

$$
\frac{\frac{\nu_1}{\nu_2}F}{\,1+\frac{\nu_1}{\nu_2}F\,}\sim\mathrm{Beta}\left(\frac{\,\nu_1\,}{2},\frac{\,\nu_2\,}{2}\right)
$$

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div id="ex-snedecor-f-3" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.57</div>

<div lang="en" markdown="1">
Suppose that $X_1,X_2,X_3,X_4$ are independent random variables, each following the $\mathcal{N}(0,1)$ distribution, and put

$$
Y_1=\sqrt{X_1^{2}+X_2^{2}},\qquad Y_2=2\sqrt{X_3^{2}+X_4^{2}}
$$

Find $\mathbb{P}(Y_1>Y_2)$.
</div>

所求為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(Y_1>Y_2)=\mathbb{P}(Y_1^{2}>Y_2^{2})=\mathbb{P}\bigl(X_1^{2}+X_2^{2}>4(X_3^{2}+X_4^{2})\bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(Y_1>Y_2)&=\mathbb{P}(Y_1^{2}>Y_2^{2})\\[0.45em]
&=\mathbb{P}\bigl(X_1^{2}+X_2^{2}>4(X_3^{2}+X_4^{2})\bigr)
\end{aligned}
$$

</div>

又由 $X_1,X_2,X_3,X_4\overset{\mathrm{iid}}{\sim}\mathcal{N}(0,1)$ 可知

<div class="topic-math-layout topic-math-layout--desktop topic-math-follow-before" markdown="1">

$$
\begin{aligned}
X_1^{2}+X_2^{2}&\sim\chi^{2}(2)\sim\mathrm{Gamma}\Bigl(\alpha=\frac{2}{\,2\,},\ \beta=2\Bigr)\\[0.45em]
\indep\ X_3^{2}+X_4^{2}&\sim\chi^{2}(2)\sim\mathrm{Gamma}\Bigl(\alpha=\frac{2}{\,2\,},\ \beta=2\Bigr)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile topic-math-follow-before" markdown="1">

$$
\begin{aligned}
X_1^{2}+X_2^{2}&\sim\chi^{2}(2)\\[0.45em]
&\sim\mathrm{Gamma}\Bigl(\alpha=\frac{2}{\,2\,},\ \beta=2\Bigr)\\[0.5em]
\indep\ X_3^{2}+X_4^{2}&\sim\chi^{2}(2)\\[0.45em]
&\sim\mathrm{Gamma}\Bigl(\alpha=\frac{2}{\,2\,},\ \beta=2\Bigr)
\end{aligned}
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop topic-math-follow" markdown="1">

$$
\Longrightarrow\ \frac{\,X_1^{2}+X_2^{2}\,}{\,X_1^{2}+X_2^{2}+X_3^{2}+X_4^{2}\,}\sim\mathrm{Beta}\Bigl(\frac{2}{\,2\,},\ \frac{2}{\,2\,}\Bigr)\sim\mathcal{U}(0,\ 1)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile topic-math-follow" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ \frac{\,X_1^{2}+X_2^{2}\,}{\,X_1^{2}+X_2^{2}+X_3^{2}+X_4^{2}\,}&\sim\mathrm{Beta}\Bigl(\frac{2}{\,2\,},\ \frac{2}{\,2\,}\Bigr)\\[0.45em]
&\sim\mathcal{U}(0,\ 1)
\end{aligned}
$$

</div>

故所求可改寫為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(Y_1>Y_2)&=\mathbb{P}\left(\frac{\,X_1^{2}+X_2^{2}\,}{X_3^{2}+X_4^{2}}>4\right)=\mathbb{P}\left(\frac{\,X_1^{2}+X_2^{2}+X_3^{2}+X_4^{2}\,}{X_3^{2}+X_4^{2}}>5\right)\\[0.45em]
&=\mathbb{P}\left(\frac{X_3^{2}+X_4^{2}}{\,X_1^{2}+X_2^{2}+X_3^{2}+X_4^{2}\,}<\frac{1}{\,5\,}\right)=\frac{1}{\,5\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(Y_1>Y_2)&=\mathbb{P}\left(\frac{\,X_1^{2}+X_2^{2}\,}{X_3^{2}+X_4^{2}}>4\right)\\[0.45em]
&=\mathbb{P}\left(\frac{\,X_1^{2}+X_2^{2}+X_3^{2}+X_4^{2}\,}{X_3^{2}+X_4^{2}}>5\right)\\[0.45em]
&=\mathbb{P}\left(\frac{X_3^{2}+X_4^{2}}{\,X_1^{2}+X_2^{2}+X_3^{2}+X_4^{2}\,}<\frac{1}{\,5\,}\right)\\[0.45em]
&=\frac{1}{\,5\,}
\end{aligned}
$$

</div>

</div>

在上列的幾個問題中，我們不斷使用到分配與分配之間的關係，來協助我們求解各種問題。這樣的技巧不只好用，很多時候更有助於我們判斷幾個不同的統計檢定是不是彼此互為「等價檢定」。

但是，要具備這樣的能力，我們至少要在常見的四大抽樣分配中，完全摸清楚彼此的關係，以下我們便開一個小節來討論這些等價關係。

## 本篇小結

[Definition 4.24](#def-f-distribution) 的斯內德克 $\mathcal{F}$ 分配以分子自由度 $\nu_1$ 與分母自由度 $\nu_2$ 兩個自由度界定，值域為正實數線，機率函數可以寫成伽瑪函數的形式，也可以寫成[貝塔函數](/teaching-topics/beta-function-and-distribution/#def-beta-function)的形式。它的期望值為 <span class="text-nowrap">$\frac{\nu_2}{\,\nu_2-2\,}$，</span>在 $\nu_2\leqslant2$ 時發散；變異數為 <span class="text-nowrap">$\frac{\,2\nu_2^{2}(\nu_1+\nu_2-2)\,}{\nu_1(\nu_2-2)^{2}(\nu_2-4)}$，</span>在 $\nu_2\leqslant4$ 時發散。與貝塔分配、司徒頓 $t$ 分配相同，這個定義沒有列出動差母函數。

定義之後的三點說明，第一點交代建構方式: 取兩個獨立的卡方變數，各自除以自身的自由度之後再相除，得到的即為 $\mathcal{F}$ 分配，分子與分母的自由度分別承襲兩個卡方變數的自由度。這個建構方式對應到兩個獨立常態母體的推論需求，因為分散程度是非負的量，比較時用的是比值而不是差。第二點只證明期望值，作法是先由獨立性把 $\mathbb{E}\bigl(\frac{X_1}{X_2}\bigr)$ 拆成 $\mathbb{E}(X_1)$ 與 $\mathbb{E}\bigl(\frac{1}{X_2}\bigr)$ 的乘積，再代入卡方分配的期望值與其倒數的期望值，同時看出 $\nu_2\leqslant2$ 時後者不存在。第三點則以密度曲線圖說明不同自由度組合之下圖形的差異。

[Theorem 4.25](#thm-s-sq-ratio-samp-dist) 轉入常態母體之下統計量的抽樣分配。兩組獨立的常態隨機樣本，其樣本變異數的比值 $S_1^{2}/S_2^{2}$ 除以母體變異數的比值 $\sigma_1^{2}/\sigma_2^{2}$ 之後，服從 $\mathcal{F}(n_1-1,\ n_2-1)$ 分配。證明的關鍵只有一步: 兩個 $\frac{(n_i-1)S_i^{2}}{\sigma_i^{2}}$ 各自服從自由度為 $n_i-1$ 的卡方分配而且彼此獨立，再把它們各除以自身自由度並相除，恰好把 $\sigma_1^{2}$ 與 $\sigma_2^{2}$ 留在該留的位置上。隨後的 Note 給出母體期望值皆已知時的對應版本，此時分母改除以 $n_i$ 而不是 <span class="text-nowrap">$n_i-1$，</span>自由度也隨之改為 $n_1$ 與 <span class="text-nowrap">$n_2$，</span>這個版本在實務上不會用到。

[Theorem 4.26](#thm-f-to-beta) 給出 $\mathcal{F}$ 分配與貝塔分配的關係。把 $F$ 寫回兩個獨立卡方變數的比值之後，$\frac{1}{1+\frac{\nu_1}{\nu_2}F}$ 恰好等於 $\frac{X_2}{X_1+X_2}$ 這個比例，而 $X_1$ 與 $X_2$ 分別是形狀參數為 $\frac{\nu_1}{2}$ 與 $\frac{\nu_2}{2}$、比例參數同為 $2$ 的獨立伽瑪變數，因此由 [Theorem 4.19](/teaching-topics/gamma-beta-relationship/#thm-gamma-to-beta) 可知該比例服從 $\mathrm{Beta}\bigl(\frac{\nu_2}{2},\frac{\nu_1}{2}\bigr)$ 分配。另一項只要取 $1$ 減去它，即得參數互換的 $\mathrm{Beta}\bigl(\frac{\nu_1}{2},\frac{\nu_2}{2}\bigr)$ 分配。

三道例題各自演練一個方向。[Example 4.55](#ex-snedecor-f-1) 檢查的是 $\mathcal{F}$ 分配定義中「各除以自身自由度」這件事有沒有被漏掉: $\frac{X_1^{2}}{W_2}$ 與 $\frac{X_1^{2}/1}{W_2/10}$ 差了一個 $10$ 倍，前者並不服從 $\mathcal{F}(1,10)$ 分配。[Example 4.56](#ex-snedecor-f-2) 同時用到 $t$ 與 $\mathcal{F}$ 兩條抽樣分配: 樣本平均數標準化之後除以樣本標準差得到的是 $t(4)$ 而不是 $t(5)$，其平方則為 $\mathcal{F}(1,4)$ 分配。[Example 4.57](#ex-snedecor-f-3) 表面上是兩段長度的比較，實際上把兩邊平方之後就是兩個獨立卡方變數的比較，再由上述的貝塔關係化為[標準均勻分配](/teaching-topics/uniform-distribution-integral-transform/#def-uniform-distribution)的機率，答案為 <span class="text-nowrap">$\frac{1}{\,5\,}$。</span>

至此，標準常態分配、卡方分配、司徒頓 $t$ 分配與斯內德克 $\mathcal{F}$ 分配這四大常用抽樣分配都已經介紹完畢。[下一篇](/teaching-topics/sampling-distribution-relationships/)把這四個分配之間的關係集中整理成一條定理，並定出各分配右尾點的寫法。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
