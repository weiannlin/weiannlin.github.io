---
title: "二元常態分配的定義與性質"
subtitle: "The Bivariate Normal Distribution: Definition and Properties"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 4
topic: 26
order: 426
permalink: /lecture-notes/bivariate-normal-distribution/
date: 2026-08-15
published: true
excerpt: "二元常態分配以兩個期望值、兩個變異數與相關係數 $\\rho$ 共五個參數刻畫二維聯合鐘形密度。本篇證明其邊際與條件分配皆為常態分配、條件期望值即母體線性迴歸式、零相關與獨立等價，以及任意線性組合仍為常態分配。"
---

[上一篇](/lecture-notes/sampling-distribution-examples/)以兩道例題演練常用抽樣分配之間的關係，至此由[常態分配](/lecture-notes/normal-distribution/#def-normal)所衍生的卡方分配、$t$ 分配與 $\mathcal{F}$ 分配，以及三者在常態母體之下的抽樣分配都已經給出。本篇轉向另一個方向，把常態分配由單一的隨機變數推廣到一對隨機變數，也就是**二元常態分配 <span lang="en">(bivariate normal distribution)</span>**。

二元常態分配的機率密度函數建立在一個二次形式 $Q(x,y)$ 之上，五個參數分別是 $X$ 與 $Y$ 各自的期望值、各自的變異數，以及兩者之間的[相關係數](/lecture-notes/correlation-coefficient/#def-corr)。本篇先給出它的定義，再依序處理五項性質，包括[邊際分配](/lecture-notes/marginal-probability-density-functions/#def-marginal-pdf)均為常態分配、[條件分配](/lecture-notes/conditional-distributions/#def-conditional-pdf)均為常態分配、機率密度呈立體鐘形而俯瞰圖呈橢圓形、零相關與[獨立](/lecture-notes/independent-random-variables/#def-indep-r-v)在此等價，以及任意線性組合仍為常態分配。其中條件分配那一項所給出的條件期望值，正好是先前的母體線性迴歸方程式；零相關與獨立等價那一項則是二元常態分配特有的結果，一般的機率分配並不成立。

## 二元常態分配

<div id="def-bivariate-normal" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 4.25 (二元常態分配, bivariate normal distribution)</div>

**適用範圍**:

由兩個常態分配隨機變數 $X,Y$ 所組成，又稱**二元高斯分配 <span lang="en">(bivariate Gaussian distribution)</span>**，具立體鐘形結構。

**值域範圍**:

$$
\mathcal{R}_{\sssig XY}=\lbrace\,(x,y)\mid-\infty<x,y<\infty\,\rbrace
$$

**表示式**:

$$
(X,Y)\sim\mathcal{BN}\bigl(\mu_1,\mu_2,\sigma^{2}_1,\sigma^{2}_2,\rho\bigr)
$$

**參數與參數範圍**:

$\mu_1,\mu_2\in\mathbb{R}$ 分別為 $X$ 與 $Y$ 的期望值、$\sigma^{2}_1,\sigma^{2}_2>0$ 分別為 $X$ 與 $Y$ 的變異數、$-1<\rho<1$ 為 $X$ 與 $Y$ 間的相關係數。

**機率函數**:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig XY}(x,y)=\frac{1}{\,2\pi\sigma_1\sigma_2\sqrt{1-\rho^{2}}\,}e^{-\frac{\,Q(x,y)\,}{2}},\ -\infty<x,y<\infty
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig XY}(x,y)&=\frac{1}{\,2\pi\sigma_1\sigma_2\sqrt{1-\rho^{2}}\,}e^{-\frac{\,Q(x,y)\,}{2}},\\[0.25em]
&\qquad-\infty<x,y<\infty
\end{aligned}
$$

</div>

其中

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
Q(x,y)&=\frac{1}{\,1-\rho^{2}\,}\Biggl[\left(\frac{x-\mu_1}{\sigma_1}\right)^{2}-2\rho\left(\frac{x-\mu_1}{\sigma_1}\right)\left(\frac{y-\mu_2}{\sigma_2}\right)\\[0.25em]
&\qquad+\left(\frac{y-\mu_2}{\sigma_2}\right)^{2}\Biggr]
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
Q(x,y)&=\frac{1}{\,1-\rho^{2}\,}\Biggl[\left(\frac{x-\mu_1}{\sigma_1}\right)^{2}\\[0.25em]
&\qquad-2\rho\left(\frac{x-\mu_1}{\sigma_1}\right)\left(\frac{y-\mu_2}{\sigma_2}\right)\\[0.25em]
&\qquad+\left(\frac{y-\mu_2}{\sigma_2}\right)^{2}\Biggr]
\end{aligned}
$$

</div>

**期望值、變異數、動差母函數**:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\mathbb{E}(X)=\mu_1,\quad\mathbb{E}(Y)=\mu_2,\quad\mathrm{Var}(X)=\sigma^{2}_1,\quad\mathrm{Var}(Y)=\sigma^{2}_2\\[0.6em]
M_{\sssig XY}(t_1,t_2)=e^{\mu_1t_1+\mu_2t_2+\frac{1}{2}(\sigma^{2}_1t_1^{2}+2\rho\sigma_1\sigma_2t_1t_2+\sigma^{2}_2t_2^{2})},\ t_1,t_2\in\mathbb{R}
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{E}(X)=\mu_1,\quad\mathbb{E}(Y)=\mu_2,\\[0.45em]
\mathrm{Var}(X)=\sigma^{2}_1,\quad\mathrm{Var}(Y)=\sigma^{2}_2
\end{gathered}
$$

$$
\begin{aligned}
&M_{\sssig XY}(t_1,t_2)\\[0.25em]
&=e^{\mu_1t_1+\mu_2t_2+\frac{1}{2}(\sigma^{2}_1t_1^{2}+2\rho\sigma_1\sigma_2t_1t_2+\sigma^{2}_2t_2^{2})},\\[0.25em]
&\qquad t_1,t_2\in\mathbb{R}
\end{aligned}
$$

</div>

</div>

二元常態分配有一些地方需要注意:

(1) 二元常態分配中，兩個邊際分配均為常態分配，此即
{: .topic-paren-item}

$$
X\sim\mathcal{N}(\mu_{1},\sigma_1^{2}),\quad Y\sim\mathcal{N}(\mu_{2},\sigma_2^{2})
$$

不失一般性，我們證明 $X$ 的情況如下，$Y$ 則同理可證。
{: .topic-paren-cont}

<div class="topic-proof" markdown="1">
**Proof.**

首先透過整理，我們可將 $Q(x,y)$ 改寫如下

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
Q(x,y)&=\frac{1}{\,1-\rho^{2}\,}\Biggl[\left(\frac{x-\mu_1}{\sigma_1}\right)^{2}-2\rho\left(\frac{x-\mu_1}{\sigma_1}\right)\left(\frac{y-\mu_2}{\sigma_2}\right)\\[0.25em]
&\qquad+\left(\frac{y-\mu_2}{\sigma_2}\right)^{2}\Biggr]\\[0.45em]
&=\frac{1}{\,1-\rho^{2}\,}\left[\left(\frac{y-\mu_2}{\sigma_2}-\rho\frac{x-\mu_1}{\sigma_1}\right)^{2}+(1-\rho^{2})\left(\frac{x-\mu_1}{\sigma_1}\right)^{2}\right]\\[0.45em]
&=\frac{1}{\,1-\rho^{2}\,}\left[\left(\frac{y-\bigl[\mu_2+\rho\frac{\sigma_2}{\sigma_1}(x-\mu_1)\bigr]}{\sigma_2}\right)^{2}+(1-\rho^{2})\left(\frac{x-\mu_1}{\sigma_1}\right)^{2}\right]
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&Q(x,y)\\[0.25em]
&=\frac{1}{\,1-\rho^{2}\,}\Biggl[\left(\frac{x-\mu_1}{\sigma_1}\right)^{2}\\[0.25em]
&\qquad-2\rho\left(\frac{x-\mu_1}{\sigma_1}\right)\left(\frac{y-\mu_2}{\sigma_2}\right)\\[0.25em]
&\qquad+\left(\frac{y-\mu_2}{\sigma_2}\right)^{2}\Biggr]\\[0.45em]
&=\frac{1}{\,1-\rho^{2}\,}\Biggl[\left(\frac{y-\mu_2}{\sigma_2}-\rho\frac{x-\mu_1}{\sigma_1}\right)^{2}\\[0.25em]
&\qquad+(1-\rho^{2})\left(\frac{x-\mu_1}{\sigma_1}\right)^{2}\Biggr]\\[0.45em]
&=\frac{1}{\,1-\rho^{2}\,}\Biggl[\left(\frac{y-\bigl[\mu_2+\rho\frac{\sigma_2}{\sigma_1}(x-\mu_1)\bigr]}{\sigma_2}\right)^{2}\\[0.25em]
&\qquad+(1-\rho^{2})\left(\frac{x-\mu_1}{\sigma_1}\right)^{2}\Biggr]
\end{aligned}
$$

</div>

故我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f_{\sssig X}(x)&=\int_{-\infty}^{\infty}f_{\sssig XY}(x,y)\,dy=\int_{-\infty}^{\infty}\frac{1}{\,2\pi\sigma_1\sigma_2\sqrt{1-\rho^{2}}\,}e^{-\frac{\,Q(x,y)\,}{2}}\,dy\\[0.45em]
&=\frac{\,e^{-\frac{\,(x-\mu_1)^{2}\,}{2\sigma_1^{2}}}\,}{\,2\pi\sigma_1\sigma_2\sqrt{1-\rho^{2}}\,}\int_{-\infty}^{\infty}e^{-\frac{\bigl(y-\bigl[\mu_2+\rho\frac{\sigma_2}{\sigma_1}(x-\mu_1)\bigr]\bigr)^{2}}{2\sigma_2^{2}(1-\rho^{2})}}\,dy\\[0.45em]
&=\frac{\,e^{-\frac{\,(x-\mu_1)^{2}\,}{2\sigma_1^{2}}}\,}{\,2\pi\sigma_1\sigma_2\sqrt{1-\rho^{2}}\,}\sqrt{2\pi\sigma_2^{2}(1-\rho^{2})}=\frac{1}{\,\sqrt{2\pi\sigma^{2}_1}\,}e^{-\frac{\,(x-\mu_1)^{2}\,}{2\sigma_1^{2}}},\ -\infty<x<\infty
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig X}(x)&=\int_{-\infty}^{\infty}f_{\sssig XY}(x,y)\,dy\\[0.45em]
&=\int_{-\infty}^{\infty}\frac{1}{\,2\pi\sigma_1\sigma_2\sqrt{1-\rho^{2}}\,}e^{-\frac{\,Q(x,y)\,}{2}}\,dy\\[0.45em]
&=\frac{\,e^{-\frac{\,(x-\mu_1)^{2}\,}{2\sigma_1^{2}}}\,}{\,2\pi\sigma_1\sigma_2\sqrt{1-\rho^{2}}\,}\\[0.25em]
&\qquad\int_{-\infty}^{\infty}e^{-\frac{\bigl(y-\bigl[\mu_2+\rho\frac{\sigma_2}{\sigma_1}(x-\mu_1)\bigr]\bigr)^{2}}{2\sigma_2^{2}(1-\rho^{2})}}\,dy\\[0.45em]
&=\frac{\,e^{-\frac{\,(x-\mu_1)^{2}\,}{2\sigma_1^{2}}}\,}{\,2\pi\sigma_1\sigma_2\sqrt{1-\rho^{2}}\,}\sqrt{2\pi\sigma_2^{2}(1-\rho^{2})}\\[0.45em]
&=\frac{1}{\,\sqrt{2\pi\sigma^{2}_1}\,}e^{-\frac{\,(x-\mu_1)^{2}\,}{2\sigma_1^{2}}},\\[0.25em]
&\qquad-\infty<x<\infty
\end{aligned}
$$

</div>

此即

$$
X\sim\mathcal{N}(\mu_1,\sigma_1^{2})
$$

而 $Y$ 同理可得。原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

反之則不成立。兩個邊際皆為常態分配的隨機變數，其聯合分配未必為二元常態分配；當兩者不獨立時便可能出現此種情形，前文的 [Example 4.48](/lecture-notes/standard-normal-moments-stein-lemma/#ex-normal-moments-1) 即為一例，下一篇亦將給出其他經典反例。

</div>

(2) 二元常態分配中，兩個條件分配均為常態分配，此即
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
X\mid(Y=y)\sim\mathcal{N}\left(\mu_1+\rho\frac{\sigma_1}{\sigma_2}(y-\mu_2),\ \sigma_1^{2}(1-\rho^{2})\right)\\[0.45em]
Y\mid(X=x)\sim\mathcal{N}\left(\mu_2+\rho\frac{\sigma_2}{\sigma_1}(x-\mu_1),\ \sigma_2^{2}(1-\rho^{2})\right)
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
X\mid(Y=y)&\sim\mathcal{N}\biggl(\mu_1+\rho\frac{\sigma_1}{\sigma_2}(y-\mu_2),\\[0.25em]
&\qquad\qquad \sigma_1^{2}(1-\rho^{2})\biggr)
\end{aligned}
$$

$$
\begin{aligned}
Y\mid(X=x)&\sim\mathcal{N}\biggl(\mu_2+\rho\frac{\sigma_2}{\sigma_1}(x-\mu_1),\\[0.25em]
&\qquad\qquad \sigma_2^{2}(1-\rho^{2})\biggr)
\end{aligned}
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.**

由條件機率密度函數的定義可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f_{\sssig X\mid Y}(x\mid y)&=\frac{\,f_{\sssig XY}(x,y)\,}{f_{\sssig Y}(y)}=\frac{\,\frac{\,e^{-\frac{\,(y-\mu_2)^{2}\,}{2\sigma_2^{2}}}\,}{\,2\pi\sigma_1\sigma_2\sqrt{1-\rho^{2}}\,}e^{-\frac{\bigl(x-\bigl[\mu_1+\rho\frac{\sigma_1}{\sigma_2}(y-\mu_2)\bigr]\bigr)^{2}}{2\sigma_1^{2}(1-\rho^{2})}}\,}{\frac{1}{\,\sqrt{2\pi\sigma^{2}_2}\,}e^{-\frac{\,(y-\mu_2)^{2}\,}{2\sigma_2^{2}}}}\\[0.45em]
&=\frac{1}{\,\sqrt{2\pi\sigma_1^{2}(1-\rho^{2})}\,}e^{-\frac{\bigl(x-\bigl[\mu_1+\rho\frac{\sigma_1}{\sigma_2}(y-\mu_2)\bigr]\bigr)^{2}}{2\sigma_1^{2}(1-\rho^{2})}},\ -\infty<x<\infty
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&f_{\sssig X\mid Y}(x\mid y)=\frac{\,f_{\sssig XY}(x,y)\,}{f_{\sssig Y}(y)}\\[0.45em]
&=\frac{\,\frac{\,e^{-\frac{\,(y-\mu_2)^{2}\,}{2\sigma_2^{2}}}\,}{\,2\pi\sigma_1\sigma_2\sqrt{1-\rho^{2}}\,}e^{-\frac{\bigl(x-\bigl[\mu_1+\rho\frac{\sigma_1}{\sigma_2}(y-\mu_2)\bigr]\bigr)^{2}}{2\sigma_1^{2}(1-\rho^{2})}}\,}{\frac{1}{\,\sqrt{2\pi\sigma^{2}_2}\,}e^{-\frac{\,(y-\mu_2)^{2}\,}{2\sigma_2^{2}}}}\\[0.45em]
&=\frac{1}{\,\sqrt{2\pi\sigma_1^{2}(1-\rho^{2})}\,}e^{-\frac{\bigl(x-\bigl[\mu_1+\rho\frac{\sigma_1}{\sigma_2}(y-\mu_2)\bigr]\bigr)^{2}}{2\sigma_1^{2}(1-\rho^{2})}},\\[0.25em]
&\qquad-\infty<x<\infty
\end{aligned}
$$

</div>

此即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
X\mid(Y=y)\sim\mathcal{N}\left(\mu_1+\rho\frac{\sigma_1}{\sigma_2}(y-\mu_2),\ \sigma_1^{2}(1-\rho^{2})\right)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
X\mid(Y=y)&\sim\mathcal{N}\biggl(\mu_1+\rho\frac{\sigma_1}{\sigma_2}(y-\mu_2),\\[0.25em]
&\qquad\qquad \sigma_1^{2}(1-\rho^{2})\biggr)
\end{aligned}
$$

</div>

而 $Y\mid(X=x)$ 同理可得。原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

由上述條件分配可直接寫出條件期望值與條件變異數如下

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\mathbb{E}(X\mid Y=y)=\mu_1+\rho\frac{\sigma_1}{\sigma_2}(y-\mu_2),\quad\mathrm{Var}(X\mid Y=y)=\sigma_1^{2}(1-\rho^{2})\\[0.45em]
\mathbb{E}(Y\mid X=x)=\mu_2+\rho\frac{\sigma_2}{\sigma_1}(x-\mu_1),\quad\mathrm{Var}(Y\mid X=x)=\sigma_2^{2}(1-\rho^{2})
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{E}(X\mid Y=y)=\mu_1+\rho\frac{\sigma_1}{\sigma_2}(y-\mu_2),\\[0.45em]
\mathrm{Var}(X\mid Y=y)=\sigma_1^{2}(1-\rho^{2})\\[0.45em]
\mathbb{E}(Y\mid X=x)=\mu_2+\rho\frac{\sigma_2}{\sigma_1}(x-\mu_1),\\[0.45em]
\mathrm{Var}(Y\mid X=x)=\sigma_2^{2}(1-\rho^{2})
\end{gathered}
$$

</div>

其中條件期望值恰為前文的[母體線性迴歸方程式](/lecture-notes/population-linear-regression/#thm-popu-reg) <span lang="en">(population linear regression equation)</span>；由正、逆迴歸斜率的乘積，亦可驗證 $X$ 與 $Y$ 的相關係數為 <span class="text-nowrap">$\rho$。</span>

在計量經濟學 <span lang="en">(econometrics)</span> 等領域中，線性迴歸的自變數 $X$ 常視為隨機變數而非固定常數。若 $(X,Y)$ 服從二元 (或多元) 常態分配，給定 $X=x$ 後條件期望值仍為 $x$ 的線性函數，且條件變異數 $\sigma_2^{2}(1-\rho^{2})$ 不隨 $x$ 改變，故仍具備古典線性迴歸的核心條件結構。

</div>

(3) 二元常態分配具立體鐘形的機率密度結構，我們將兩種不同相關係數的二元常態分配繪製在下方:
{: .topic-paren-item}

<figure id="fig-bivariate-normal-surface" class="topic-figure topic-figure--wide">
  <img src="/images/lecture-notes/bivariate-normal-surface.svg" alt="左右並排的兩個面板，各畫一個立體曲面。曲面之下鋪著一片方形的網格底面，底面的兩條邊分別標為 x 與 y，高度方向標為 f_XY(x, y)，兩個面板都沒有畫座標軸線，也沒有標任何刻度數值。左面板的曲面自底面中央隆起成一個鐘形，四面八方的坡度看起來一致，越往邊緣越平，貼著底面；面板正下方標 (ρ = 0)。右面板的曲面同樣自中央隆起，但隆起的部分明顯較窄較陡，並沿著 x 增大而 y 減小的方向拉成一道長脊，長脊兩側的坡面陡峭，兩端則緩緩降到底面；面板正下方標 (ρ = −0.8)。">
  <figcaption><span class="topic-figure__label">Fig. 4.15.</span> 兩個面板各畫一個聯合機率密度的曲面，底面的兩軸標為 $x$ 與 <span class="text-nowrap">$y$，</span>高度方向標為 <span class="text-nowrap">$f_{\sssig XY}(x,y)$，</span>曲面越高的地方機率密度越大。左面板所標的 $\rho$ 為零，曲面自中央隆起，各個方向的坡度一致；右面板所標的 $\rho$ 為負，隆起的部分較窄較陡，並沿 $x$ 增大而 $y$ 減小的方向拉成一道長脊。<span class="text-nowrap">$\lvert\rho\rvert$</span> 越大，機率密度就越集中在一條斜直線的附近。</figcaption>
</figure>

下圖進一步給出對應的俯瞰圖，可見機率密度的等高輪廓呈橢圓形。
{: .topic-paren-cont}

<figure id="fig-bivariate-normal-contours" class="topic-figure topic-figure--wide">
  <img src="/images/lecture-notes/bivariate-normal-contours.svg" alt="左右並排的兩個面板，各是一個正方形的網格區塊，由正上方俯瞰而得。方塊之內以墨色的濃淡填滿，越深表示該處的高度越高，方塊外緣則接近全白。兩個面板都沒有畫座標軸線，也沒有標任何刻度數值，橫軸標為 x，其下另標一行，縱軸標為 y。左面板的深色集中在方塊正中央，由中心往外一圈一圈變淡，整團的輪廓是正圓形；橫軸下方那一行標 (ρ = 0)。右面板的深色被拉成一條由左上往右下傾斜的長條，中央一段最深，兩端漸淡，整團的輪廓是狹長的橢圓形；橫軸下方那一行標 (ρ = −0.8)。">
  <figcaption><span class="topic-figure__label">Fig. 4.16.</span> 由正上方俯瞰 <a href="#fig-bivariate-normal-surface">Fig. 4.15</a> 的兩個曲面，橫軸標為 <span class="text-nowrap">$x$、</span>縱軸標為 <span class="text-nowrap">$y$，</span>墨色越深的地方機率密度越大。左面板所標的 $\rho$ 為零，深色的一團是正圓形；右面板所標的 $\rho$ 為負，同一團被拉成一個由左上往右下傾斜的橢圓形。<span class="text-nowrap">$\lvert\rho\rvert$</span> 越大，橢圓就越狹長。</figcaption>
</figure>

由圖可見，聯合密度的幾何形狀受相關係數影響顯著；當 $\lvert\rho\rvert$ 越大時，$(X,Y)$ 的機率密度越集中於一條斜直線附近。前文 [Fig. 3.18](/lecture-notes/correlation-coefficient/#fig-correlation-strength-scatter) 展示的不同相關係數散佈圖，即是由二元常態分配抽樣繪製而成，可與此處的理論輪廓互相對照。
{: .topic-paren-cont}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

俯瞰圖之所以呈橢圓形，源於指數項中的二次形式 <span class="text-nowrap">$Q(x,y)$。</span>固定 $Q(x,y)=c>0$ 在平面上界定出一族同心橢圓 (當 $\rho\neq0$ 時為斜橢圓)；當點 $(x,y)$ 往外遠離中心 $(\mu_1,\mu_2)$ 時，機率密度隨二次距離呈指數衰減，高密度區域遂集中在橢圓內部。此外，橢圓主軸的傾斜方向不僅取決於相關係數 <span class="text-nowrap">$\rho$，</span>亦受兩變數各自的標準差 $\sigma_1,\sigma_2$ 影響，這與母體線性迴歸斜率同時取決於 $\rho$ 與標準差比值相呼應。

</div>

(4) 二元常態分配中，$X$ 與 $Y$ 零相關等價於 $X$ 與 $Y$ 獨立，此即
{: .topic-paren-item}

$$
X\indep Y\qquad\Longleftrightarrow\ \rho=0
$$

<div class="topic-proof" markdown="1">
**Proof.**

當 $\rho=0$ 時，我們可以得到

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f_{\sssig XY}(x,y)&=\frac{1}{\,2\pi\sigma_1\sigma_2\,}e^{\frac{-1}{2}\left[\left(\frac{x-\mu_1}{\sigma_1}\right)^{2}+\left(\frac{y-\mu_2}{\sigma_2}\right)^{2}\right]}\\[0.45em]
&=\left[\frac{1}{\,\sqrt{2\pi\sigma_1^{2}}\,}\,e^{\frac{-1}{2}\left(\frac{x-\mu_1}{\sigma_1}\right)^{2}}\right]\left[\frac{1}{\,\sqrt{2\pi\sigma_2^{2}}\,}\,e^{\frac{-1}{2}\left(\frac{y-\mu_2}{\sigma_2}\right)^{2}}\right]=f_{\sssig X}(x)f_{\sssig Y}(y)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig XY}(x,y)&=\frac{1}{\,2\pi\sigma_1\sigma_2\,}e^{\frac{-1}{2}\left[\left(\frac{x-\mu_1}{\sigma_1}\right)^{2}+\left(\frac{y-\mu_2}{\sigma_2}\right)^{2}\right]}\\[0.45em]
&=\left[\frac{1}{\,\sqrt{2\pi\sigma_1^{2}}\,}\,e^{\frac{-1}{2}\left(\frac{x-\mu_1}{\sigma_1}\right)^{2}}\right]\\[0.25em]
&\qquad\left[\frac{1}{\,\sqrt{2\pi\sigma_2^{2}}\,}\,e^{\frac{-1}{2}\left(\frac{y-\mu_2}{\sigma_2}\right)^{2}}\right]\\[0.45em]
&=f_{\sssig X}(x)f_{\sssig Y}(y)
\end{aligned}
$$

</div>

反之，若 <span class="text-nowrap">$X\indep Y$，</span>則由獨立隨機變數共變異數為 $0$ 的性質立得 <span class="text-nowrap">$\rho=\mathrm{Corr}(X,Y)=0$。</span>由此可知二元常態中

$$
\rho=0\qquad\Longleftrightarrow\ X\indep Y
$$

原式得證。 <span class="topic-qed">$\square$</span>
</div>

(5) 二元常態分配中，對任意不全為 $0$ 的常數 <span class="text-nowrap">$a,b$，</span>兩個隨機變數的線性組合仍服從常態分配，此即
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
aX+bY\sim\mathcal{N}\bigl(a\mu_1+b\mu_2,\ a^{2}\sigma_1^{2}+b^{2}\sigma_2^{2}+2ab\rho\sigma_1\sigma_2\bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&aX+bY\sim\mathcal{N}\bigl(a\mu_1+b\mu_2,\\[0.25em]
&\qquad\quad a^{2}\sigma_1^{2}+b^{2}\sigma_2^{2}+2ab\rho\sigma_1\sigma_2\bigr)
\end{aligned}
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.**

令 <span class="text-nowrap">$W=aX+bY$，</span>則我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{\sssig W}(t)&=\mathbb{E}(e^{tW})=\mathbb{E}\bigl[e^{t(aX+bY)}\bigr]=\mathbb{E}\bigl[e^{(at)X+(bt)Y}\bigr]=M_{\sssig XY}(at,bt)\\[0.45em]
&=e^{(a\mu_1+b\mu_2)\,t+\frac{1}{2}(a^{2}\sigma_1^{2}+b^{2}\sigma_2^{2}+2ab\rho\sigma_1\sigma_2)\,t^{2}},\ t\in\mathbb{R}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig W}(t)&=\mathbb{E}(e^{tW})=\mathbb{E}\bigl[e^{t(aX+bY)}\bigr]\\[0.45em]
&=\mathbb{E}\bigl[e^{(at)X+(bt)Y}\bigr]=M_{\sssig XY}(at,bt)\\[0.45em]
&=e^{(a\mu_1+b\mu_2)\,t+\frac{1}{2}(a^{2}\sigma_1^{2}+b^{2}\sigma_2^{2}+2ab\rho\sigma_1\sigma_2)\,t^{2}},\\[0.25em]
&\qquad t\in\mathbb{R}
\end{aligned}
$$

</div>

由 [mgf 唯一性](/lecture-notes/uniqueness-of-the-mgf/#thm-mgf-uniqueness)可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
W=aX+bY\sim\mathcal{N}\bigl(a\mu_1+b\mu_2,\ a^{2}\sigma_1^{2}+b^{2}\sigma_2^{2}+2ab\rho\sigma_1\sigma_2\bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
W&=aX+bY\\[0.25em]
&\sim\mathcal{N}\bigl(a\mu_1+b\mu_2,\\[0.25em]
&\qquad\quad a^{2}\sigma_1^{2}+b^{2}\sigma_2^{2}+2ab\rho\sigma_1\sigma_2\bigr)
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div id="note-affine-transformation" class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

如[前文](/lecture-notes/mgf-method-examples/#note-affine-transformation)所述，聯合常態 (或獨立常態) 隨機變數經非退化線性組合後仍維持常態分配，此即常態分配特有的**仿射變換 <span lang="en">(affine transformation)</span>** 性質；本性質為其二元純量形式，後文將進一步推廣至多元常態向量的矩陣線性轉換。

</div>

(6) 將二元常態分配推廣至任意維度的隨機向量，即得後文介紹的**[多元常態分配](/lecture-notes/multivariate-normal-distribution/#def-multivariate-normal) <span lang="en">(multivariate normal distribution)</span>**。
{: .topic-paren-item}

## 本篇小結

[Definition 4.25](#def-bivariate-normal) 的二元常態分配以五個參數界定，其中 $\mu_1$ 與 $\mu_2$ 是兩個期望值、$\sigma_1^{2}$ 與 $\sigma_2^{2}$ 是兩個變異數、$\rho$ (<span class="text-nowrap">$-1<\rho<1$</span>) 是兩者之間的相關係數，值域為整個平面。它的機率密度函數是 $\frac{1}{2\pi\sigma_1\sigma_2\sqrt{1-\rho^{2}}}e^{-\frac{Q(x,y)}{2}}$ 這個式子，其中 $Q(x,y)$ 是一個把 $\frac{x-\mu_1}{\sigma_1}$ 與 $\frac{y-\mu_2}{\sigma_2}$ 兩項標準化變數配起來的二次形式，[聯合動差母函數](/lecture-notes/cross-moments-joint-mgf/#def-joint-mgf)則是 $e^{\mu_1t_1+\mu_2t_2+\frac{1}{2}(\sigma^{2}_1t_1^{2}+2\rho\sigma_1\sigma_2t_1t_2+\sigma^{2}_2t_2^{2})}$ 這個函數。

定義之後的六點說明，前五點各給一項性質。第一點是邊際分配。把 $Q(x,y)$ 對 $y$ 配成完全平方，剩下的一項恰好只含 <span class="text-nowrap">$x$，</span>對 $y$ 積分之後那個常態核心給出積分值 $\sqrt{2\pi\sigma_2^{2}(1-\rho^{2})}$ 這一因子，與前面的常數相約之後正好剩下 $\mathcal{N}(\mu_1,\sigma_1^{2})$ 的機率密度函數。要留意的是反過來並不成立。兩個常態分配未必能組成一個二元常態分配，不獨立的時候尤其如此。

第二點是條件分配。把聯合機率密度函數除以邊際機率密度函數，指數上兩個 $(y-\mu_2)^{2}$ 的項相消，剩下的正是以 $\mu_1+\rho\frac{\sigma_1}{\sigma_2}(y-\mu_2)$ 為期望值、以 $\sigma_1^{2}(1-\rho^{2})$ 為變異數的常態機率密度函數。這裡的條件期望值就是母體線性迴歸方程式，而條件變異數不隨 $y$ 改變，$\lvert\rho\rvert$ 越大則條件變異數越小。

第三點回到圖形。機率密度呈立體鐘形，由正上方俯瞰則呈橢圓形，這是因為 $Q(x,y)$ 本身就是一個斜橢圓的函數，離橢圓中心越遠，機率密度下降得越快；橢圓軸線的斜率不只受相關係數影響，也受兩個標準差影響。第四點是二元常態分配特有的結果。令 $\rho=0$ 之後機率密度函數恰好拆成兩個邊際機率密度函數的乘積，故在二元常態分配之中零相關與獨立等價，這件事在一般的機率分配並不成立。第五點則由聯合動差母函數直接得到 $M_{\sssig W}(t)=M_{\sssig XY}(at,bt)$ 這條關係式，代入之後仍是常態分配的動差母函數形式，因而任意線性組合 $aX+bY$ 服從 $\mathcal{N}\bigl(a\mu_1+b\mu_2,\ a^{2}\sigma_1^{2}+b^{2}\sigma_2^{2}+2ab\rho\sigma_1\sigma_2\bigr)$ 這個分配，其變異數比獨立時多出 $2ab\rho\sigma_1\sigma_2$ 這一項。第六點預告了後文的多元常態分配。

[下一篇](/lecture-notes/bivariate-normal-examples/)以三道例題演練二元常態分配，依序處理由條件分配的機率反求相關係數並求線性組合的分配、邊際皆為常態而聯合並非二元常態的反例，以及由機率密度函數的核辨認五個參數再求條件期望值。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
