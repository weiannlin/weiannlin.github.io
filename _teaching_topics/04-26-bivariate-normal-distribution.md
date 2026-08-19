---
title: "二元常態分配的定義與性質"
subtitle: "The Bivariate Normal Distribution: Definition and Properties"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 4
topic: 26
order: 426
permalink: /teaching-topics/bivariate-normal-distribution/
date: 2026-08-15
published: false
excerpt: "二元常態分配由兩個常態隨機變數所組成，五個參數分別是兩個期望值、兩個變異數與一個相關係數，其機率函數建立在一個二次形式 $Q(x,y)$ 之上，因而具有立體鐘形的結構。本篇先給出定義，再依序給出五項性質，其中四項各附證明: 把 $Q(x,y)$ 配成完全平方之後對 $y$ 積分，可知邊際分配均為常態分配；聯合機率密度函數除以邊際機率密度函數，可知條件分配均為常態分配，而其條件期望值正是母體線性迴歸方程式、條件變異數則為 $\\sigma_1^{2}(1-\\rho^{2})$；當 $\\rho=0$ 時聯合機率密度函數恰好拆成兩個邊際機率密度函數的乘積，故在二元常態分配之中零相關與獨立等價；最後由聯合動差母函數可知任意線性組合 $aX+bY$ 仍為常態分配，其變異數為 $a^{2}\\sigma_1^{2}+b^{2}\\sigma_2^{2}+2ab\\rho\\sigma_1\\sigma_2$。文中並以立體圖與俯瞰圖說明機率密度的橢圓形趨勢。"
---

[上一篇](/teaching-topics/sampling-distribution-examples/)以兩道例題演練常用抽樣分配之間的關係，至此由[常態分配](/teaching-topics/normal-distribution/#def-normal)所衍生的卡方分配、$t$ 分配與 $\mathcal{F}$ 分配，以及三者在常態母體之下的抽樣分配都已經給出。本篇轉向另一個方向，把常態分配由單一的隨機變數推廣到一對隨機變數，也就是**二元常態分配 <span lang="en">(bivariate normal distribution)</span>**。

二元常態分配的機率密度函數建立在一個二次形式 $Q(x,y)$ 之上，五個參數分別是 $X$ 與 $Y$ 各自的期望值、各自的變異數，以及兩者之間的[相關係數](/teaching-topics/correlation-coefficient/#def-corr)。本篇先給出它的定義，再依序處理五項性質: [邊際分配](/teaching-topics/marginal-probability-density-functions/#def-marginal-pdf)均為常態分配、[條件分配](/teaching-topics/conditional-distributions/#def-conditional-pdf)均為常態分配、機率密度呈立體鐘形而俯瞰圖呈橢圓形、零相關與[獨立](/teaching-topics/independent-random-variables/#def-indep-r-v)在此等價，以及任意線性組合仍為常態分配。其中條件分配那一項所給出的條件期望值，正好是先前的母體線性迴歸方程式；零相關與獨立等價那一項則是二元常態分配特有的結果，一般的機率分配並不成立。

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

$\mu_1,\mu_2$ 分別為 $X$ 與 $Y$ 的期望值、$\sigma^{2}_1,\sigma^{2}_2>0$ 分別為 $X$ 與 $Y$ 的變異數、$\rho$ 為 $X$ 與 $Y$ 間的相關係數。

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
Q(x,y)=\frac{1}{\,1-\rho^{2}\,}\left[\left(\frac{x-\mu_1}{\sigma_1}\right)^{2}-2\rho\left(\frac{x-\mu_1}{\sigma_1}\right)\left(\frac{y-\mu_2}{\sigma_2}\right)+\left(\frac{y-\mu_2}{\sigma_2}\right)^{2}\right]
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
\begin{aligned}
\mathbb{E}(X)&=\mu_1,\quad\mathbb{E}(Y)=\mu_2,\quad\mathrm{Var}(X)=\sigma^{2}_1,\quad\mathrm{Var}(Y)=\sigma^{2}_2\\[0.45em]
M_{\sssig XY}(t_1,t_2)&=e^{\mu_1t_1+\mu_2t_2+\frac{1}{2}(\sigma^{2}_1t_1^{2}+2\rho\sigma_1\sigma_2t_1t_2+\sigma^{2}_2t_2^{2})},\ t_1,t_2\in\mathbb{R}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\mu_1,\quad\mathbb{E}(Y)=\mu_2,\\[0.45em]
\mathrm{Var}(X)&=\sigma^{2}_1,\quad\mathrm{Var}(Y)=\sigma^{2}_2\\[0.45em]
M_{\sssig XY}(t_1,t_2)&=e^{\mu_1t_1+\mu_2t_2+\frac{1}{2}(\sigma^{2}_1t_1^{2}+2\rho\sigma_1\sigma_2t_1t_2+\sigma^{2}_2t_2^{2})},\\[0.25em]
&\qquad t_1,t_2\in\mathbb{R}
\end{aligned}
$$

</div>

</div>

二元常態分配有一些地方需要注意:

(1) 二元常態分配的邊際分配均為常態分配，此即
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
Q(x,y)&=\frac{1}{\,1-\rho^{2}\,}\left[\left(\frac{x-\mu_1}{\sigma_1}\right)^{2}-2\rho\left(\frac{x-\mu_1}{\sigma_1}\right)\left(\frac{y-\mu_2}{\sigma_2}\right)+\left(\frac{y-\mu_2}{\sigma_2}\right)^{2}\right]\\[0.45em]
&=\frac{1}{\,1-\rho^{2}\,}\left[\left(\frac{y-\mu_2}{\sigma_2}-\rho\frac{x-\mu_1}{\sigma_1}\right)^{2}+(1-\rho^{2})\left(\frac{x-\mu_1}{\sigma_1}\right)^{2}\right]\\[0.45em]
&=\frac{1}{\,1-\rho^{2}\,}\left[\left(\frac{y-\bigl[\mu_2+\rho\frac{\sigma_2}{\sigma_1}(x-\mu_1)\bigr]}{\sigma_2}\right)^{2}+(1-\rho^{2})\left(\frac{x-\mu_1}{\sigma_1}\right)^{2}\right]
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
Q(x,y)&=\frac{1}{\,1-\rho^{2}\,}\Biggl[\left(\frac{x-\mu_1}{\sigma_1}\right)^{2}\\[0.25em]
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

讀者應該注意到的是，雖然二元常態分配的邊際分配均為常態分配，但任意兩個常態分配，卻不見得能組成一個二元常態分配，這種情況發生在此二個常態分配不獨立的時候，[Example 4.48](/teaching-topics/standard-normal-moments-stein-lemma/#ex-normal-moments-1) 中的 $X$ 與 $Y$ 就是一個很好的例子，稍後我們也會看到其他經典的反例。

</div>

(2) 二元常態分配的條件分配均為常態分配，此即
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
X\mid(Y=y)&\sim\mathcal{N}\left(\mu_1+\rho\frac{\sigma_1}{\sigma_2}(y-\mu_2),\ \sigma_1^{2}(1-\rho^{2})\right)\\[0.45em]
Y\mid(X=x)&\sim\mathcal{N}\left(\mu_2+\rho\frac{\sigma_2}{\sigma_1}(x-\mu_1),\ \sigma_2^{2}(1-\rho^{2})\right)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
X\mid(Y=y)&\sim\mathcal{N}\biggl(\mu_1+\rho\frac{\sigma_1}{\sigma_2}(y-\mu_2),\\[0.25em]
&\qquad\qquad \sigma_1^{2}(1-\rho^{2})\biggr)\\[0.45em]
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
f_{\sssig X\mid Y}(x\mid y)&=\frac{\,f_{\sssig XY}(x,y)\,}{f_{\sssig Y}(y)}\\[0.45em]
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

讀者應特別注意，這個性質指出

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X\mid Y=y)&=\mu_1+\rho\frac{\sigma_1}{\sigma_2}(y-\mu_2),\quad\mathrm{Var}(X\mid Y=y)=\sigma_1^{2}(1-\rho^{2})\\[0.45em]
\mathbb{E}(Y\mid X=x)&=\mu_2+\rho\frac{\sigma_2}{\sigma_1}(x-\mu_1),\quad\mathrm{Var}(Y\mid X=x)=\sigma_2^{2}(1-\rho^{2})
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X\mid Y=y)&=\mu_1+\rho\frac{\sigma_1}{\sigma_2}(y-\mu_2),\\[0.45em]
\mathrm{Var}(X\mid Y=y)&=\sigma_1^{2}(1-\rho^{2})\\[0.45em]
\mathbb{E}(Y\mid X=x)&=\mu_2+\rho\frac{\sigma_2}{\sigma_1}(x-\mu_1),\\[0.45em]
\mathrm{Var}(Y\mid X=x)&=\sigma_2^{2}(1-\rho^{2})
\end{aligned}
$$

</div>

這個結果讀者應該感到相當熟悉，因為條件期望值的部分正好是先前提到的[母體線性迴歸方程式](/teaching-topics/population-linear-regression/#thm-popu-reg) <span lang="en">(population linear regression equation)</span>。[^econometrics]

此外，透過這個結果，我們也可以搭配母體線性迴歸方程式中的正逆迴歸，證明相關係數確實為 <span class="text-nowrap">$\rho$。</span>

</div>

(3) 二元常態分配具立體鐘形的機率密度結構，我們將兩種不同相關係數的二元常態分配繪製在下方:
{: .topic-paren-item}

<figure id="fig-bivariate-normal-surface" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/bivariate-normal-surface.svg" alt="左右並排的兩個面板，各畫一個立體曲面。曲面之下鋪著一片方形的網格底面，底面的兩條邊分別標為 x 與 y，高度方向標為 f_XY(x, y)，兩個面板都沒有畫座標軸線，也沒有標任何刻度數值。左面板的曲面自底面中央隆起成一個鐘形，四面八方的坡度看起來一致，越往邊緣越平，貼著底面；面板正下方標 (ρ = 0)。右面板的曲面同樣自中央隆起，但隆起的部分明顯較窄較陡，並沿著 x 增大而 y 減小的方向拉成一道長脊，長脊兩側的坡面陡峭，兩端則緩緩降到底面；面板正下方標 (ρ = −0.8)。">
  <figcaption><span class="topic-figure__label">Fig. 4.15.</span> 兩個面板各畫一個聯合機率密度的曲面，底面的兩軸標為 $x$ 與 <span class="text-nowrap">$y$，</span>高度方向標為 <span class="text-nowrap">$f_{\sssig XY}(x,y)$，</span>曲面越高的地方機率密度越大。左面板所標的 $\rho$ 為零，曲面自中央隆起，各個方向的坡度一致；右面板所標的 $\rho$ 為負，隆起的部分較窄較陡，並沿 $x$ 增大而 $y$ 減小的方向拉成一道長脊。<span class="text-nowrap">$\lvert\rho\rvert$</span> 越大，機率密度就越集中在一條斜直線的附近。</figcaption>
</figure>

同時，我們也將它們各自的俯瞰圖繪製在下方，可以發現，其機率密度大致上有一個橢圓形的趨勢。
{: .topic-paren-cont}

<figure id="fig-bivariate-normal-contours" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/bivariate-normal-contours.svg" alt="左右並排的兩個面板，各是一個正方形的網格區塊，由正上方俯瞰而得。方塊之內以墨色的濃淡填滿，越深表示該處的高度越高，方塊外緣則接近全白。兩個面板都沒有畫座標軸線，也沒有標任何刻度數值，橫軸標為 x，其下另標一行，縱軸標為 y。左面板的深色集中在方塊正中央，由中心往外一圈一圈變淡，整團的輪廓是正圓形；橫軸下方那一行標 (ρ = 0)。右面板的深色被拉成一條由左上往右下傾斜的長條，中央一段最深，兩端漸淡，整團的輪廓是狹長的橢圓形；橫軸下方那一行標 (ρ = −0.8)。">
  <figcaption><span class="topic-figure__label">Fig. 4.16.</span> 由正上方俯瞰 <a href="#fig-bivariate-normal-surface">Fig. 4.15</a> 的兩個曲面，橫軸標為 <span class="text-nowrap">$x$、</span>縱軸標為 <span class="text-nowrap">$y$，</span>墨色越深的地方機率密度越大。左面板所標的 $\rho$ 為零，深色的一團是正圓形；右面板所標的 $\rho$ 為負，同一團被拉成一個由左上往右下傾斜的橢圓形。<span class="text-nowrap">$\lvert\rho\rvert$</span> 越大，橢圓就越狹長。</figcaption>
</figure>

上述圖形可以發現，二元常態形狀的結果相當受到參數設定的影響，尤其是相關係數，但整體而言，相關係數的絕對值越大，$X$ 與 $Y$ 的分配就越接近一條直線。[^scatter]
{: .topic-paren-cont}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

二元常態呈橢圓形的趨勢，是受到其 pdf 指數項上的二次形式的影響。事實上，二次形式 $Q(x,y)$ 本身就是一個斜橢圓的函數，隨著每一個點以斜橢圓的方式遠離橢圓中心，其機率密度會以指數的平方倍快速下降，因此俯瞰圖顯示，中間大致在一個橢圓形的內部，具有比較高的機率密度。

此外，橢圓的軸線斜率除了受到相關係數的影響以外，更受到 $X$ 與 $Y$ 各自標準差的影響，這一點與母體線性迴歸方程式有關，讀者不妨觀察看看其中的奧秘。

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

由此可知二元常態中

$$
\rho=0\qquad\Longleftrightarrow\ X\indep Y
$$

原式得證。 <span class="topic-qed">$\square$</span>
</div>

(5) 二元常態分配中，兩個隨機變數的任意線性組合還會是常態分配，此即
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
aX+bY\sim\mathcal{N}\bigl(a\mu_1+b\mu_2,\ a^{2}\sigma_1^{2}+b^{2}\sigma_2^{2}+2ab\rho\sigma_1\sigma_2\bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
aX+bY\sim\mathcal{N}\bigl(&a\mu_1+b\mu_2,\\[0.25em]
&a^{2}\sigma_1^{2}+b^{2}\sigma_2^{2}+2ab\rho\sigma_1\sigma_2\bigr)
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

由 [mgf 唯一性](/teaching-topics/uniqueness-of-the-mgf/#thm-mgf-uniqueness)可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
W=aX+bY\sim\mathcal{N}\bigl(a\mu_1+b\mu_2,\ a^{2}\sigma_1^{2}+b^{2}\sigma_2^{2}+2ab\rho\sigma_1\sigma_2\bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
W=aX+bY\sim\mathcal{N}\bigl(&a\mu_1+b\mu_2,\\[0.25em]
&a^{2}\sigma_1^{2}+b^{2}\sigma_2^{2}+2ab\rho\sigma_1\sigma_2\bigr)
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

在先前的筆記中，我們曾經提過，常態分配的任意線性組合，其結果都是常態分配，這是常態分配特有的**仿射變換 <span lang="en">(affine transformation)</span>** 性質，在多元常態的矩陣運算中特別有用，而這個性質雖不是矩陣運算的版本，但確實與當時提到的仿射變換是同一個性質。

<!-- ref-point: 書稿此處以「頁 \pageref{affineFirst} 中的筆記」指向書稿 mathstatch3.tex
     第 4825 行的註記 (第三章 3.3.2 小節，落在第三章第 25 篇「多對一與動差母函數法」，
     slug 為 mgf-method-transformations)。該篇尚未定出這一則註記的 anchor，
     anchor 定出之後，把上一段的「在先前的筆記中」改為指向該 anchor 的連結。 -->

</div>

(6) 二元常態分配可以推廣至更多常態分配的情況，也就是**[多元常態分配](/teaching-topics/multivariate-normal-distribution/#def-multivariate-normal) <span lang="en">(multivariate normal distribution)</span>**，稍後我們馬上就會看到。
{: .topic-paren-item}

[^econometrics]: 事實上，這個結果格外重要，因為在諸如計量經濟學 <span lang="en">(econometrics)</span> 等領域，並不會將線性迴歸中的自變數視為常數，而是視為隨機變數之一，故如果有自變數 $X$ 與反應變數 $Y$ 共同服從二元 (或是多元) 常態分配的話，則我們還是可以透過給定 $X$ 的方式重新獲得線性迴歸模型的所有好處。

[^scatter]: 事實上，[Fig. 3.18](/teaching-topics/correlation-coefficient/#fig-correlation-strength-scatter) 的相關係數圖，正是由抽自二元常態分配的樣本所繪製而成，讀者不妨與此處的結論互相對照。

## 本篇小結

[Definition 4.25](#def-bivariate-normal) 的二元常態分配以五個參數界定: $\mu_1$ 與 $\mu_2$ 是兩個期望值、$\sigma_1^{2}$ 與 $\sigma_2^{2}$ 是兩個變異數、$\rho$ 是兩者之間的相關係數，值域為整個平面。它的機率密度函數是 $\frac{1}{2\pi\sigma_1\sigma_2\sqrt{1-\rho^{2}}}e^{-\frac{Q(x,y)}{2}}$ 這個式子，其中 $Q(x,y)$ 是一個把 $\frac{x-\mu_1}{\sigma_1}$ 與 $\frac{y-\mu_2}{\sigma_2}$ 兩項標準化變數配起來的二次形式，[聯合動差母函數](/teaching-topics/cross-moments-joint-mgf/#def-joint-mgf)則是 $e^{\mu_1t_1+\mu_2t_2+\frac{1}{2}(\sigma^{2}_1t_1^{2}+2\rho\sigma_1\sigma_2t_1t_2+\sigma^{2}_2t_2^{2})}$ 這個函數。

定義之後的六點說明，前五點各給一項性質。第一點是邊際分配: 把 $Q(x,y)$ 對 $y$ 配成完全平方，剩下的一項恰好只含 <span class="text-nowrap">$x$，</span>對 $y$ 積分之後那個常態核心給出 <span class="text-nowrap">$\sqrt{2\pi\sigma_2^{2}(1-\rho^{2})}$，</span>與前面的常數相約之後正好剩下 $\mathcal{N}(\mu_1,\sigma_1^{2})$ 的機率密度函數。要留意的是反過來並不成立: 兩個常態分配未必能組成一個二元常態分配，不獨立的時候尤其如此。

第二點是條件分配。把聯合機率密度函數除以邊際機率密度函數，指數上兩個 $(y-\mu_2)^{2}$ 的項相消，剩下的正是以 $\mu_1+\rho\frac{\sigma_1}{\sigma_2}(y-\mu_2)$ 為期望值、以 $\sigma_1^{2}(1-\rho^{2})$ 為變異數的常態機率密度函數。這裡的條件期望值就是[母體線性迴歸方程式](/teaching-topics/population-linear-regression/#thm-popu-reg)，而條件變異數不隨 $y$ 改變，$\lvert\rho\rvert$ 越大則條件變異數越小。

第三點回到圖形。機率密度呈立體鐘形，由正上方俯瞰則呈橢圓形，這是因為 $Q(x,y)$ 本身就是一個斜橢圓的函數，離橢圓中心越遠，機率密度下降得越快；橢圓軸線的斜率不只受相關係數影響，也受兩個標準差影響。第四點是二元常態分配特有的結果: 令 $\rho=0$ 之後機率密度函數恰好拆成兩個邊際機率密度函數的乘積，故在二元常態分配之中零相關與獨立等價，這件事在一般的機率分配並不成立。第五點則由聯合動差母函數直接得到 <span class="text-nowrap">$M_{\sssig W}(t)=M_{\sssig XY}(at,bt)$，</span>代入之後仍是常態分配的動差母函數形式，因而任意線性組合 $aX+bY$ 服從 <span class="text-nowrap">$\mathcal{N}\bigl(a\mu_1+b\mu_2,\ a^{2}\sigma_1^{2}+b^{2}\sigma_2^{2}+2ab\rho\sigma_1\sigma_2\bigr)$，</span>其變異數比獨立時多出 $2ab\rho\sigma_1\sigma_2$ 這一項。第六點預告了後文的多元常態分配。

[下一篇](/teaching-topics/bivariate-normal-examples/)以三道例題演練二元常態分配，依序處理由條件分配的機率反求相關係數並求線性組合的分配、邊際皆為常態而聯合並非二元常態的反例，以及由機率密度函數的核辨認五個參數再求條件期望值。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
