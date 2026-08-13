---
title: "常態分配的定義、標準化與線性組合可加性"
subtitle: "The Normal Distribution: Definition, Standardization and Additivity"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 4
topic: 17
order: 417
permalink: /teaching-topics/ch4-p17-candidate/
date: 2026-08-12
published: false
excerpt: "常態分配的機率函數為 $\\frac{1}{\\sqrt{2\\pi\\sigma^{2}}}e^{-\\frac{(x-\\mu)^{2}}{2\\sigma^{2}}}$ 這個式子，期望值為 $\\mu$、變異數為 $\\sigma^{2}$，動差母函數則是 $e^{\\mu t+\\frac{1}{2}\\sigma^{2}t^{2}}$。本篇先給出驗證機率函數合法所需要的高斯積分，再由動差母函數回頭求得期望值與變異數。接著證明標準化與反標準化這一對互逆的轉換，以及常態分配的線性組合可加性，後者保證常態隨機樣本的樣本平均數仍然是常態分配。最後由密度曲線的圖形回顧鐘形分配經驗法則，並定出標準常態分配的右尾點。"
---

[上一篇](/teaching-topics/ch4-p16-candidate/)談伽瑪分配與貝塔分配之間的關係，至此貝塔相關的機率模型已經全部給出。本篇轉入第四大類的機率模型，也就是常態相關的機率模型。

常態分配相關的機率模型，在統計學中的地位主要用於統計量 <span lang="en">(statistic)</span> 的**抽樣分配 <span lang="en">(sampling distribution)</span>**。基於隨機樣本來自常態分配的前提，我們可以針對母體參數進行許多有用的推論。[^statistic]

要知道，統計的核心是處理資料 (data)，將其轉換為有用的資訊 <span lang="en">(information)</span>。在這個過程中，受限於成本等各種考量，我們通常無法得到母體資料，此時將會需要針對由母體分配 <span lang="en">(population distribution)</span> 經抽樣 <span lang="en">(sampling)</span> 所得到的樣本 (sample) 進行處理，因此探討統計量所具有的抽樣分配便是相當重要的事情，最關鍵的理由乃是因為，我們能夠透過這個機率分配，評估我們推論的成效如何。

然而，常態相關的機率模型仍然是一種機率分配，因此在數理統計學中，我們仍會將這些機率分配以「機率模型」的角度進行介紹，但讀者應特別注意其建構的方式，以及這些分配之間的關係，以便熟悉日後的應用。

本篇先給出驗證常態分配的機率函數合法時所需要的高斯積分，再進入常態分配的定義，並依序證明機率函數合法、動差母函數、期望值與變異數。其後談常態分配的幾項延伸性質，包含標準常態分配、標準化、反標準化與線性組合可加性，最後由密度曲線的圖形回顧鐘形分配經驗法則，並給出常態分配常用尾點的定義方式。

## 高斯積分

<div id="thm-gaussian-integral" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 4.20 (高斯積分, the Gaussian integral)</div>

$$
\int_{-\infty}^{\infty}e^{-\frac{1}{2}x^{2}}\,dx=\sqrt{2\pi}
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.** 令

$$
I=\int_{-\infty}^{\infty}e^{-\frac{1}{2}x^{2}}\,dx
$$

則我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
I^{2}&=\int_{-\infty}^{\infty}e^{-\frac{1}{2}x^{2}}\,dx\int_{-\infty}^{\infty}e^{-\frac{1}{2}x^{2}}\,dx=\int_{-\infty}^{\infty}e^{-\frac{1}{2}x^{2}}\,dx\int_{-\infty}^{\infty}e^{-\frac{1}{2}y^{2}}\,dy\\[0.45em]
&=\int_{-\infty}^{\infty}\int_{-\infty}^{\infty}e^{-\left(\frac{1}{2}x^{2}+\frac{1}{2}y^{2}\right)}\,dx\,dy
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
I^{2}&=\int_{-\infty}^{\infty}e^{-\frac{1}{2}x^{2}}\,dx\int_{-\infty}^{\infty}e^{-\frac{1}{2}x^{2}}\,dx\\[0.45em]
&=\int_{-\infty}^{\infty}e^{-\frac{1}{2}x^{2}}\,dx\int_{-\infty}^{\infty}e^{-\frac{1}{2}y^{2}}\,dy\\[0.45em]
&=\int_{-\infty}^{\infty}\int_{-\infty}^{\infty}e^{-\left(\frac{1}{2}x^{2}+\frac{1}{2}y^{2}\right)}\,dx\,dy
\end{aligned}
$$

</div>

則由極座標轉換 <span lang="en">(polar-coordinate transformation)</span>，可令

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{cases} x=r\cos\theta\\ y=r\sin\theta \end{cases}\Longrightarrow\ \mathbf{J}=\left\lvert\begin{array}{cc} \dfrac{\partial x}{\partial r} & \dfrac{\partial x}{\partial\theta}\\[0.7em] \dfrac{\partial y}{\partial r} & \dfrac{\partial y}{\partial\theta}\end{array}\right\rvert=r
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\begin{cases} x=r\cos\theta\\ y=r\sin\theta \end{cases}\\[0.55em]
\Longrightarrow\ \mathbf{J}=\left\lvert\begin{array}{cc} \dfrac{\partial x}{\partial r} & \dfrac{\partial x}{\partial\theta}\\[0.7em] \dfrac{\partial y}{\partial r} & \dfrac{\partial y}{\partial\theta}\end{array}\right\rvert=r
\end{gathered}
$$

</div>

則

$$
I^{2}=\int_{0}^{2\pi}\int_{0}^{\infty}e^{-\frac{1}{2}r^{2}}\,r\,dr\,d\theta=2\pi
$$

故

$$
I=\sqrt{2\pi}
$$

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

上述的積分有時候被稱作高斯積分，但通常來說，高斯積分是特別指高斯函數 <span lang="en">(Gaussian function)</span> $e^{-x^{2}}$ 在整個實數域上的定積分，也就是

$$
\int_{-\infty}^{\infty}e^{-x^{2}}\,dx=\sqrt{\pi}
$$

在常態分配相關的證明中，我們基於一些方便，由這個標準的積分式進一步推得上列結果。

</div>

## 常態分配

<div id="def-normal" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 4.21 (常態分配, Normal distribution)</div>

**適用範圍**:

常態分配在自然界中經常被發現，能夠用來描述許多自然界中的現象，諸如智力或身高的分配情形等。

**值域範圍**:

$$
\mathcal{R}_{\sssig X}=\lbrace\,x\mid-\infty<x<\infty\,\rbrace
$$

**表示式**:

$$
X\sim\mathcal{N}\bigl(\mu,\sigma^{2}\bigr)
$$

**參數與參數範圍**:

$\mu$ 為該分配的期望值、$\sigma^{2}>0$ 為該分配的變異數。

**機率函數**:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X}(x)=\frac{1}{\,\sqrt{2\pi\sigma^{2}}\,}e^{-\frac{(x-\mu)^{2}}{2\sigma^{2}}},\ -\infty<x<\infty
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
f_{\sssig X}(x)=\frac{1}{\,\sqrt{2\pi\sigma^{2}}\,}e^{-\frac{(x-\mu)^{2}}{2\sigma^{2}}},\\[0.45em]
-\infty<x<\infty
\end{gathered}
$$

</div>

**期望值、變異數、動差母函數**:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(X)=\mu,\quad \mathrm{Var}(X)=\sigma^{2},\quad M_{\sssig X}(t)=e^{\mu t+\frac{1}{2}\sigma^{2}t^{2}},\ t\in\mathbb{R}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{E}(X)=\mu,\quad \mathrm{Var}(X)=\sigma^{2}\\[0.45em]
M_{\sssig X}(t)=e^{\mu t+\frac{1}{2}\sigma^{2}t^{2}},\ t\in\mathbb{R}
\end{gathered}
$$

</div>

</div>

常態分配 <span lang="en">(Normal distribution)</span> 有一些地方需要注意:

(1) 我們證明其機率函數為一個合法的機率函數與期望值、變異數與動差母函數如下:
{: .topic-paren-item}

<div class="topic-proof" markdown="1">
**Proof.** 先驗證機率函數的積分為 <span class="text-nowrap">$1$，</span>即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\int_{x\in\mathcal{R}_{\sssig X}}f_{\sssig X}(x)\,dx&=\int_{-\infty}^{\infty}\frac{1}{\sqrt{2\pi\sigma^{2}}}e^{-\frac{(x-\mu)^{2}}{2\sigma^{2}}}\,dx=\frac{1}{\sqrt{2\pi}}\int_{-\infty}^{\infty}e^{-\frac{1}{2}u^{2}}\,du\\[0.25em]
&\qquad\qquad\qquad\qquad\qquad\qquad\Bigl[\,\text{令}\ u=\frac{x-\mu}{\sigma}\,\Bigr]\\[0.45em]
&=\frac{1}{\sqrt{2\pi}}\times\sqrt{2\pi}=1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\int_{x\in\mathcal{R}_{\sssig X}}f_{\sssig X}(x)\,dx\\[0.45em]
&\quad =\int_{-\infty}^{\infty}\frac{1}{\sqrt{2\pi\sigma^{2}}}e^{-\frac{(x-\mu)^{2}}{2\sigma^{2}}}\,dx\\[0.45em]
&\quad =\frac{1}{\sqrt{2\pi}}\int_{-\infty}^{\infty}e^{-\frac{1}{2}u^{2}}\,du\\[0.25em]
&\qquad\qquad \Bigl[\,\text{令}\ u=\frac{x-\mu}{\sigma}\,\Bigr]\\[0.45em]
&\quad =\frac{1}{\sqrt{2\pi}}\times\sqrt{2\pi}=1
\end{aligned}
$$

</div>

接著求動差母函數，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{\sssig X}(t)&=\int_{-\infty}^{\infty}e^{tx}\frac{1}{\sqrt{2\pi\sigma^{2}}}e^{-\frac{(x-\mu)^{2}}{2\sigma^{2}}}\,dx=\int_{-\infty}^{\infty}\frac{1}{\sqrt{2\pi\sigma^{2}}}e^{-\frac{x^{2}-2(\mu+\sigma^{2}t)x+\mu^{2}}{2\sigma^{2}}}\,dx\\[0.45em]
&=e^{\frac{2\mu\sigma^{2}t+(\sigma^{2}t)^{2}}{2\sigma^{2}}}\int_{-\infty}^{\infty}\frac{1}{\sqrt{2\pi\sigma^{2}}}e^{-\frac{\bigl[x-(\mu+\sigma^{2}t)\bigr]^{2}}{2\sigma^{2}}}\,dx=e^{\mu t+\frac{1}{2}\sigma^{2}t^{2}},\ t\in\mathbb{R}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&M_{\sssig X}(t)\\[0.45em]
&\quad =\int_{-\infty}^{\infty}e^{tx}\frac{1}{\sqrt{2\pi\sigma^{2}}}e^{-\frac{(x-\mu)^{2}}{2\sigma^{2}}}\,dx\\[0.45em]
&\quad =\int_{-\infty}^{\infty}\frac{1}{\sqrt{2\pi\sigma^{2}}}e^{-\frac{x^{2}-2(\mu+\sigma^{2}t)x+\mu^{2}}{2\sigma^{2}}}\,dx\\[0.45em]
&\quad =e^{\frac{2\mu\sigma^{2}t+(\sigma^{2}t)^{2}}{2\sigma^{2}}}\\[0.25em]
&\qquad \times\int_{-\infty}^{\infty}\frac{1}{\sqrt{2\pi\sigma^{2}}}e^{-\frac{\bigl[x-(\mu+\sigma^{2}t)\bigr]^{2}}{2\sigma^{2}}}\,dx\\[0.45em]
&\quad =e^{\mu t+\frac{1}{2}\sigma^{2}t^{2}},\ t\in\mathbb{R}
\end{aligned}
$$

</div>

再由動差母函數的一階與二階導數在 $t=0$ 的值可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=M_{\sssig X}^{\prime}(t)\Big|_{t=0}=\biggl[e^{\mu t+\frac{1}{2}\sigma^{2}t^{2}}\bigl(\mu+\sigma^{2}t\bigr)\biggr]_{t=0}=\mu\\[0.45em]
\mathbb{E}\bigl(X^{2}\bigr)&=M_{\sssig X}^{\prime\prime}(t)\Big|_{t=0}=\biggl[e^{\mu t+\frac{1}{2}\sigma^{2}t^{2}}\bigl(\mu+\sigma^{2}t\bigr)^{2}+e^{\mu t+\frac{1}{2}\sigma^{2}t^{2}}\bigl(\sigma^{2}\bigr)\biggr]_{t=0}\\[0.25em]
&=\mu^{2}+\sigma^{2}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=M_{\sssig X}^{\prime}(t)\Big|_{t=0}\\[0.45em]
&=\biggl[e^{\mu t+\frac{1}{2}\sigma^{2}t^{2}}\bigl(\mu+\sigma^{2}t\bigr)\biggr]_{t=0}\\[0.45em]
&=\mu\\[0.55em]
\mathbb{E}\bigl(X^{2}\bigr)&=M_{\sssig X}^{\prime\prime}(t)\Big|_{t=0}\\[0.45em]
&=\biggl[e^{\mu t+\frac{1}{2}\sigma^{2}t^{2}}\bigl(\mu+\sigma^{2}t\bigr)^{2}\\[0.25em]
&\qquad +e^{\mu t+\frac{1}{2}\sigma^{2}t^{2}}\bigl(\sigma^{2}\bigr)\biggr]_{t=0}\\[0.45em]
&=\mu^{2}+\sigma^{2}
\end{aligned}
$$

</div>

最後可得變異數為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}(X)=\mathbb{E}\bigl(X^{2}\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}=\mu^{2}+\sigma^{2}-\mu^{2}=\sigma^{2}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(X)&=\mathbb{E}\bigl(X^{2}\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}\\[0.45em]
&=\mu^{2}+\sigma^{2}-\mu^{2}=\sigma^{2}
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

在期望值、變異數與動差母函數的部分，由於積分過程的繁複，我們採用的方式是**先計算出動差母函數，再由動差母函數來計算期望值與變異數**。

</div>

(2) 常態分配的定義可以得到以下幾個延伸性質:
{: .topic-paren-item}

第一，常態分配的各種參數組合中，若將 $\mu$ 設為 $0$ 且將 $\sigma^{2}$ 設為 <span class="text-nowrap">$1$，</span>也就是 <span class="text-nowrap">$Z\sim\mathcal{N}(0,1)$，</span>則這種常態分配被我們稱為**標準常態分配 <span lang="en">(standard normal distribution)</span>**，我們將其一些特色列在下方:
{: .topic-paren-cont}

- 表示式: $Z\sim\mathcal{N}(0,1)$
- 機率密度函數: $\phi(z)=\frac{1}{\sqrt{2\pi}}e^{-\frac{1}{2}z^{2}},\ -\infty<z<\infty$
- 累積機率函數: $\Phi(z)=\int_{-\infty}^{z}\phi(t)\,dt,\ z\in\mathbb{R}$
- $\mathbb{E}(Z)=0$
- $\mathrm{Var}(Z)=1$
- $M_{\sssig Z}(t)=e^{\frac{1}{2}t^{2}}$

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這種特殊的常態分配的用途非常廣，稍後會見到許多基於常態分配延伸的機率分配，也都是由這個特例出發的。另外，因為這種常態分配被大量使用的緣故，我們對此種常態分配訂有專屬的 pdf $\phi(z)$ 及 cdf <span class="text-nowrap">$\Phi(z)$，</span>其中 $\Phi(z)$ 是以積分式存在的函數，並不存在解析解。

</div>

第二，**標準化 <span lang="en">(standardizing)</span>**:
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\text{若}\ X\sim\mathcal{N}(\mu,\sigma^{2})\text{，令}\ Z=\frac{\,X-\mu\,}{\sigma}\text{，則}\ Z\sim\mathcal{N}(0,1)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\text{若}\ X\sim\mathcal{N}(\mu,\sigma^{2})\text{，令}\ Z=\frac{\,X-\mu\,}{\sigma}\\[0.45em]
\text{則}\ Z\sim\mathcal{N}(0,1)
\end{gathered}
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.** 由於

$$
Z=\frac{\,X-\mu\,}{\sigma}=\frac{1}{\,\sigma\,}X-\frac{\mu}{\,\sigma\,}
$$

由 [Theorem 2.39](/teaching-topics/one-to-one-transformations/#thm-mgf-linear-transformation) 可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
M_{\sssig Z}(t)=e^{-\frac{\mu}{\sigma}t}M_{\sssig X}\Bigl(\frac{1}{\sigma}t\Bigr)=e^{-\frac{\mu}{\sigma}t}e^{\frac{\mu}{\sigma}t+\frac{1}{2}\sigma^{2}\left(\frac{1}{\sigma}t\right)^{2}}=e^{\frac{1}{2}t^{2}}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig Z}(t)&=e^{-\frac{\mu}{\sigma}t}M_{\sssig X}\Bigl(\frac{1}{\sigma}t\Bigr)\\[0.45em]
&=e^{-\frac{\mu}{\sigma}t}e^{\frac{\mu}{\sigma}t+\frac{1}{2}\sigma^{2}\left(\frac{1}{\sigma}t\right)^{2}}\\[0.45em]
&=e^{\frac{1}{2}t^{2}}
\end{aligned}
$$

</div>

由 [mgf 的唯一性](/teaching-topics/uniqueness-of-the-mgf/#thm-mgf-uniqueness)可知

$$
Z\sim\mathcal{N}(0,1)
$$

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

上述假設的 $\frac{\,X-\mu\,}{\sigma}$ 被稱作**標準化 <span lang="en">(standardizing)</span>**。[^standardizing] 我們可以將一個任意的常態分配，經由標準化轉為標準常態分配，當然也能反過來，將標準常態分配轉為任意期望值與變異數的常態分配，如下列性質。

</div>

第三，**反標準化 <span lang="en">(inverse standardizing)</span>**:
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\text{若}\ Z\sim\mathcal{N}(0,1)\text{，令}\ X=\sigma Z+\mu\text{，則}\ X\sim\mathcal{N}(\mu,\sigma^{2})
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\text{若}\ Z\sim\mathcal{N}(0,1)\text{，令}\ X=\sigma Z+\mu\\[0.45em]
\text{則}\ X\sim\mathcal{N}(\mu,\sigma^{2})
\end{gathered}
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.** 由於 <span class="text-nowrap">$X=\sigma Z+\mu$，</span>由 [Theorem 2.39](/teaching-topics/one-to-one-transformations/#thm-mgf-linear-transformation) 可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
M_{\sssig X}(t)=e^{\mu t}M_{\sssig Z}(\sigma t)=e^{\mu t}e^{\frac{1}{2}(\sigma t)^{2}}=e^{\mu t+\frac{1}{2}\sigma^{2}t^{2}},\ t\in\mathbb{R}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig X}(t)&=e^{\mu t}M_{\sssig Z}(\sigma t)=e^{\mu t}e^{\frac{1}{2}(\sigma t)^{2}}\\[0.45em]
&=e^{\mu t+\frac{1}{2}\sigma^{2}t^{2}},\ t\in\mathbb{R}
\end{aligned}
$$

</div>

由 [mgf 的唯一性](/teaching-topics/uniqueness-of-the-mgf/#thm-mgf-uniqueness)可知

$$
X\sim\mathcal{N}(\mu,\sigma^{2})
$$

原式得證。 <span class="topic-qed">$\square$</span>
</div>

第四，事實上，經過標準化或反標準化後還會與原分配為同一種分配的隨機變數並不多，常態分配便是其一。進一步而言，常態分配除了具有**線性可轉換** <span lang="en">(**linear-transformable**)</span> 的性質，也就是經過線性轉換的常態分配仍是一個常態分配外，更具有常態分配之間的**線性組合可加性**，見下列敘述:
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\text{若}\ X_1,X_2,\ldots,X_n\overset{\mathrm{ind}}{\sim}\mathcal{N}(\mu_i,\sigma^{2}_i)\text{，令}\ Y=\sum_{i=1}^{n}a_iX_i+b\\[0.45em]
\text{則}\ Y\sim\mathcal{N}\Bigl(\sum_{i=1}^{n}a_i\mu_i+b,\ \sum_{i=1}^{n}a_i^{2}\sigma_i^{2}\Bigr)
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\text{若}\ X_1,X_2,\ldots,X_n\overset{\mathrm{ind}}{\sim}\mathcal{N}(\mu_i,\sigma^{2}_i)\\[0.3em]
\text{令}\ Y=\sum_{i=1}^{n}a_iX_i+b\\[0.55em]
\text{則}\ Y\sim\mathcal{N}\Bigl(\sum_{i=1}^{n}a_i\mu_i+b,\ \sum_{i=1}^{n}a_i^{2}\sigma_i^{2}\Bigr)
\end{gathered}
$$

</div>

<!-- ref-point: 待第三章第 25 篇 (獨立隨機變數的線性組合之動差母函數，書稿 mathstatch3.tex
     第 4674 行的 Theorem 3.23，anchor 為 #thm-mgf-two-to-one) 發布後，將下面證明中的
     「獨立隨機變數線性組合的動差母函數之定理」改為指向該 anchor 的站內連結。 -->

<div class="topic-proof" markdown="1">
**Proof.** 由於

$$
X_1,X_2,\ldots,X_n\overset{\mathrm{ind}}{\sim}\mathcal{N}(\mu_i,\sigma^{2}_i)
$$

由獨立隨機變數線性組合的動差母函數之定理與 [Theorem 2.39](/teaching-topics/one-to-one-transformations/#thm-mgf-linear-transformation) 的合併推廣可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{\sssig Y}(t)&=e^{bt}\prod_{i=1}^{n}M_{X_i}(a_it)=e^{bt}\prod_{i=1}^{n}e^{\mu_ia_it+\frac{1}{2}\sigma^{2}_i(a_it)^{2}}\\[0.45em]
&=e^{\left(\sum_{i=1}^{n}a_i\mu_i+b\right)t+\frac{1}{2}\left(\sum_{i=1}^{n}a_i^{2}\sigma_i^{2}\right)t^{2}},\ t\in\mathbb{R}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig Y}(t)&=e^{bt}\prod_{i=1}^{n}M_{X_i}(a_it)\\[0.45em]
&=e^{bt}\prod_{i=1}^{n}e^{\mu_ia_it+\frac{1}{2}\sigma^{2}_i(a_it)^{2}}\\[0.45em]
&=e^{\left(\sum_{i=1}^{n}a_i\mu_i+b\right)t+\frac{1}{2}\left(\sum_{i=1}^{n}a_i^{2}\sigma_i^{2}\right)t^{2}},\\[0.25em]
&\qquad\qquad t\in\mathbb{R}
\end{aligned}
$$

</div>

由 [mgf 的唯一性](/teaching-topics/uniqueness-of-the-mgf/#thm-mgf-uniqueness)可知

$$
Y\sim\mathcal{N}\Bigl(\sum_{i=1}^{n}a_i\mu_i+b,\ \sum_{i=1}^{n}a_i^{2}\sigma_i^{2}\Bigr)
$$

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

常態分配的線性組合可加性，在樣本平均數 $\overline{X}$ 身上有著重要的意義。對任意分配的一組隨機樣本 $X_1,X_2,\ldots,X_n$ 而言，若其共同的期望值 $\mu$ 與變異數 $\sigma^{2}$ 存在，則樣本平均數 $\overline{X}$ 必定具有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\mathbb{E}(\overline{X})=\mathbb{E}\biggl(\frac{\sum_{i=1}^{n}X_i}{n}\biggr)=\frac{1}{n}\sum_{i=1}^{n}\mathbb{E}(X_i)=\frac{1}{n}\times n\mu=\mu\\[0.55em]
\mathrm{Var}(\overline{X})=\mathrm{Var}\biggl(\frac{\sum_{i=1}^{n}X_i}{n}\biggr)=\frac{1}{n^{2}}\sum_{i=1}^{n}\mathrm{Var}(X_i)=\frac{1}{n^{2}}\times n\sigma^{2}=\frac{\sigma^{2}}{n}
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(\overline{X})&=\mathbb{E}\biggl(\frac{\sum_{i=1}^{n}X_i}{n}\biggr)\\[0.45em]
&=\frac{1}{n}\sum_{i=1}^{n}\mathbb{E}(X_i)\\[0.45em]
&=\frac{1}{n}\times n\mu=\mu\\[0.55em]
\mathrm{Var}(\overline{X})&=\mathrm{Var}\biggl(\frac{\sum_{i=1}^{n}X_i}{n}\biggr)\\[0.45em]
&=\frac{1}{n^{2}}\sum_{i=1}^{n}\mathrm{Var}(X_i)\\[0.45em]
&=\frac{1}{n^{2}}\times n\sigma^{2}=\frac{\sigma^{2}}{n}
\end{aligned}
$$

</div>

但是，大多數的情形之下，「樣本平均」這個線性轉換未必能夠保證這組隨機樣本的機率分配，在經過轉換過後還是與原先相同。[^same-family] 但是，常態分配卻不同，上述定理即保證了，在「樣本平均」這個線性組合的轉換之下，**常態分配的樣本平均仍然會是常態分配**，也就是

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\text{若}\ X_1,X_2,\ldots,X_n\overset{\mathrm{iid}}{\sim}\mathcal{N}(\mu,\sigma^{2})\text{，則}\ \overline{X}\sim\mathcal{N}\biggl(\mu,\frac{\sigma^{2}}{n}\biggr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\text{若}\ X_1,X_2,\ldots,X_n\overset{\mathrm{iid}}{\sim}\mathcal{N}(\mu,\sigma^{2})\\[0.45em]
\text{則}\ \overline{X}\sim\mathcal{N}\biggl(\mu,\frac{\sigma^{2}}{n}\biggr)
\end{gathered}
$$

</div>

這個結果在後續的統計推論中，將具有舉足輕重的地位。

</div>

(3) 常態分配的圖形如下所示:
{: .topic-paren-item}

<!-- fig-pending: normal-density-empirical
     Fig. 4.4，單一面板，對應書稿 mathstatch4.tex 第 3418 行的 tikzpicture。
     畫的是一條常態分配的密度曲線: 書稿以 3.069*exp(-((x-4)^2)/3) 作圖，相當於
     mu = 4、sigma = 1.224744871391589 的鐘形曲線，繪圖範圍 x 由 0 到 8，取樣 200 點。
     曲線下方整片以灰色填滿 (書稿 fill=gray、opacity=0.2)。
     只畫一條向右的橫軸 (由 (0,0) 到 (8.2,0)，箭頭 stealth)，並在右端標 x; 不畫縱軸，
     兩軸皆不標刻度數值，也不寫軸名。
     曲線上七個位置各拉一條虛線垂直落到橫軸，落點由左至右依序標
     mu-3sigma、mu-2sigma、mu-sigma、mu、mu+sigma、mu+2sigma、mu+3sigma。
     這張圖對應正文所說的鐘形分配經驗法則，caption 起首為 Fig. 4.4.，
     內容說明常態分配的密度曲線與正負一、二、三倍標準差的三個區間。
     檔名 normal-density-empirical.svg，anchor 取 #fig-normal-density-empirical。
     待作者裁定一項: 書稿為了讓最外側兩個標示不互相重疊，正負三倍標準差的落點實際上是
     以 3.1 倍作圖 (第 3439 與 3443 行的 3.1*\d)，網頁重畫時要照書稿保留 3.1 倍，
     還是改為數學上正確的 3 倍並另以縮小字級或錯開標示處理重疊，照書稿保留為預設。
     圖畫好之後，把下一段開頭的「這個圖形」改為指向該 anchor 的 Fig. 4.4 連結。 -->

這個圖形正是 [Theorem 2.37](/teaching-topics/empirical-rule-bell-shaped-distributions/#thm-empirical-rule) 所敘述的鐘形分配經驗法則。[^empirical-rule] 若我們將鐘形分配經驗法則中的期望用在標準常態分配身上，可以得到如下的結果:
{: .topic-paren-cont}

$$
\begin{gathered}
\mathbb{P}\bigl(\lvert Z\rvert<1\bigr)=\mathbb{P}(-1<Z<1)\fallingdotseq0.6826\\[0.45em]
\mathbb{P}\bigl(\lvert Z\rvert<2\bigr)=\mathbb{P}(-2<Z<2)\fallingdotseq0.9544\\[0.45em]
\mathbb{P}\bigl(\lvert Z\rvert<3\bigr)=\mathbb{P}(-3<Z<3)\fallingdotseq0.9974
\end{gathered}
$$

事實上，這個法則背後的原理，就是應用統計學中所用到的常態分配常用尾點的由來，只是**其概念是固定了等式右側的機率，反求等式左側機率函數中的端點**，即如下表示:
{: .topic-paren-cont}

<!-- fig-pending: normal-right-tail-point
     Fig. 4.5，單一面板，對應書稿 mathstatch4.tex 第 3476 行的 tikzpicture。
     畫的是與 Fig. 4.4 同一條密度曲線 (同一個函數 3.069*exp(-((x-4)^2)/3)、
     同一段繪圖範圍 x 由 0 到 8)。
     只畫一條向右的橫軸 (由 (0,0) 到 (8.2,0)，箭頭 stealth)，並在右端標 z; 不畫縱軸，
     不標刻度數值，也不寫軸名。
     右側尾端一小塊以灰色填滿 (書稿取 x 由 7 到 8 的一段，fill=gray、opacity=0.2)。
     該塊的左界由曲線上 x = 7 的點垂直落到橫軸畫一條實線，落點標 z 的下標 alpha。
     另有一條虛線箭頭 (bend left) 由填色區塊中央 (書稿取 x = 7.5 處、高度為該處曲線高的
     一半) 向右上方彎出，端點旁標 alpha，用來指出該塊面積即為 alpha。
     這張圖說明的是固定右側機率 alpha 反求端點的作法，caption 起首為 Fig. 4.5.，
     內容說明標準常態分配的右尾機率與其所對應的右尾點。
     檔名 normal-right-tail-point.svg，anchor 取 #fig-normal-right-tail-point。
     圖畫好之後，把下一段開頭的「上列的圖形」改為指向該 anchor 的 Fig. 4.5 連結。 -->

上列的圖形所指的範圍稱作**右尾機率 <span lang="en">(right-tail probability)</span>**，若轉化為數學式，[^left-tail]即為
{: .topic-paren-cont}

$$
\mathbb{P}(Z>z_{\sssig \alpha})=\alpha
$$

其中 <span class="text-nowrap">$Z\sim\mathcal{N}(0,1)$。</span>
{: .topic-paren-cont}

除了上述與圖形及機率有關的性質外，下面再列出一些與圖形相關的性質:
{: .topic-paren-cont}

- $\mu=\eta=m_o$
- 反曲點: $\mu\pm\sigma$
- $\alpha_3=0$
- $\alpha_4=3$

(4) 標準常態分配是許多分配在滿足特定條件下的**極限分配 <span lang="en">(limiting distribution)</span>**，這是基於**中央極限定理 <span lang="en">(central limit theorem, CLT)</span>** 所衍生的結果，細節與常見的範例將在稍後的章節中談到。
{: .topic-paren-item}

(5) 標準常態分配由於在 $0$ 的左右對稱，故對任意的實數 <span class="text-nowrap">$z$，</span>我們有 $\mathbb{P}(Z<-z)=\mathbb{P}(Z>z)$ 的關係，亦可以寫成 <span class="text-nowrap">$\Phi(-z)=1-\Phi(z)$，</span>這個關係式在推導如**常態機率模型 (probit model)**[^probit] 等較為複雜的模型時具有關鍵的用途。
{: .topic-paren-item}

(6) 若 $X\sim\mathcal{N}(\mu_1,\sigma^{2}_1)$ 與 $Y\sim\mathcal{N}(\mu_2,\sigma^{2}_2)$ 為出自多元常態的二個常態分配，二者不獨立且相關係數為 <span class="text-nowrap">$\rho$，</span>則我們有
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
aX+bY\sim\mathcal{N}\bigl(a\mu_1+b\mu_2,\ a^{2}\sigma^{2}_1+b^{2}\sigma^{2}_2+2ab\rho\sigma_1\sigma_2\bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&aX+bY\sim\mathcal{N}\bigl(a\mu_1+b\mu_2,\\[0.25em]
&\qquad\quad a^{2}\sigma^{2}_1+b^{2}\sigma^{2}_2+2ab\rho\sigma_1\sigma_2\bigr)
\end{aligned}
$$

</div>

特別是當 $\rho=0$ 時，此即性質 (2) 中的線性可加性。[^multivariate]
{: .topic-paren-cont}

[^statistic]: 事實上，統計量的定義就是隨機樣本的函數組合，因此探討統計量的抽樣分配，就機率的角度而言，只是隨機向量函數變換的一環。

[^standardizing]: 事實上，這個動作並不僅限於常態分配才能使用，只要是將一個隨機變數平移至期望值為 $0$ 並且伸縮至變異數為 $1$ 者都可以稱作標準化。而標準化過後的隨機變數，其期望值必定為 $0$ 且變異數必定為 <span class="text-nowrap">$1$。</span>

[^same-family]: 即使我們允許參數不同，而僅要求分配相同，也未必能夠有這個結果。

[^empirical-rule]: 在當時，我們便曾提過，鐘形分配的經驗法則是由常態分配所計算出來的經驗法則，雖然只要是「長得像鐘」的分配都適用，但是用在常態分配時會特別精準。

[^left-tail]: 在部分的教科書中，這個尾點的表示式恰巧與此處相反，為**左尾機率 <span lang="en">(left-tail probability)</span>**，即 <span class="text-nowrap">$\mathbb{P}(Z\leqslant z_{\sssig \alpha})=\Phi(z_{\sssig \alpha})=\alpha$。</span>

[^probit]: **常態機率模型 (probit model)** 是一種二元結果的模型，其概念是針對反應變數 $Y$ 只有成敗兩種結果的情況，以解釋變數 $X$ 來估計或預測成功結果的機率，不應因其名字而與單純的「機率模型 <span lang="en">(probability model)</span>」這個統稱搞混。與其相似的模型還有**邏輯斯模型 (<span lang="en">logistic model</span>**，或稱**邏輯斯迴歸式 <span lang="en">logistic regression</span>)**。

[^multivariate]: 稍後我們將會看到，常態分配有多維度的版本，即**多元常態分配 <span lang="en">(multivariate Normal distribution)</span>**。多元常態分配的一個重要特例是二元常態分配，在二元常態分配中，零相關 (即 <span class="text-nowrap">$\rho=0$)</span> 與獨立是等價的。

## 本篇小結

本篇由 [Theorem 4.20](#thm-gaussian-integral) 的高斯積分開場，這條積分恆等式是後續一切常態分配計算的基礎: 把兩個相同的積分相乘化為平面上的重積分，再以極座標轉換算出 <span class="text-nowrap">$I^{2}=2\pi$，</span>因而得到 $\int_{-\infty}^{\infty}e^{-\frac{1}{2}x^{2}}\,dx=\sqrt{2\pi}$ 這個結果。一般所稱的高斯積分指的是 $e^{-x^{2}}$ 在整個實數域上的定積分，本篇用的是為了計算方便而改寫過的版本。

[Definition 4.21](#def-normal) 的常態分配以 $\mu$ 與 $\sigma^{2}$ 兩個參數界定，值域為整條實數線，機率函數為 $\frac{1}{\sqrt{2\pi\sigma^{2}}}e^{-\frac{(x-\mu)^{2}}{2\sigma^{2}}}$ 這個式子。證明的四個步驟依序是: 以 $u=\frac{x-\mu}{\sigma}$ 的代換把積分化到標準形，再套高斯積分驗證積分為 <span class="text-nowrap">$1$；</span>把指數上的兩項併成完全平方，湊出另一個常態密度而得到 <span class="text-nowrap">$M_{\sssig X}(t)=e^{\mu t+\frac{1}{2}\sigma^{2}t^{2}}$；</span>再由這個動差母函數的一階與二階導數在 $t=0$ 的值得到 $\mathbb{E}(X)$ 與 <span class="text-nowrap">$\mathbb{E}\bigl(X^{2}\bigr)$；</span>最後相減得到 <span class="text-nowrap">$\mathrm{Var}(X)=\sigma^{2}$。</span>由於直接積分相當繁複，這裡採用的次序是先求動差母函數，再由它回頭算期望值與變異數。

定義之後的六點說明之中，第二點給出四款延伸性質。取 $\mu=0$ 與 $\sigma^{2}=1$ 得到的標準常態分配另有專屬的記號 $\phi(z)$ 與 <span class="text-nowrap">$\Phi(z)$，</span>其中 $\Phi(z)$ 只能以積分式存在，沒有解析解。標準化 $Z=\frac{X-\mu}{\sigma}$ 與反標準化 $X=\sigma Z+\mu$ 是一對互逆的線性轉換，兩者的證明都是把 [Theorem 2.39](/teaching-topics/one-to-one-transformations/#thm-mgf-linear-transformation) 的線性轉換公式套上去，算出來的動差母函數再由 [mgf 的唯一性](/teaching-topics/uniqueness-of-the-mgf/#thm-mgf-uniqueness)辨識分配。線性組合可加性把這件事推到 $n$ 個彼此獨立的常態變數: $Y=\sum_{i=1}^{n}a_iX_i+b$ 仍為常態分配，期望值與變異數分別是 $\sum_{i=1}^{n}a_i\mu_i+b$ 與 <span class="text-nowrap">$\sum_{i=1}^{n}a_i^{2}\sigma_i^{2}$。</span>取 $a_i=\frac{1}{n}$ 與 $b=0$ 即得常態隨機樣本的樣本平均數服從 $\mathcal{N}\bigl(\mu,\frac{\sigma^{2}}{n}\bigr)$ 這個結果，它在後續的統計推論中舉足輕重。

其餘各點回到圖形與尾機率。常態分配的密度曲線正是 [Theorem 2.37](/teaching-topics/empirical-rule-bell-shaped-distributions/#thm-empirical-rule) 鐘形分配經驗法則所描述的形狀，用在標準常態分配上分別給出 <span class="text-nowrap">$0.6826$、</span><span class="text-nowrap">$0.9544$</span> 與 $0.9974$ 這三個涵蓋比例。把同一件事反過來看，固定右側的機率 $\alpha$ 再反求端點，得到的即為右尾點的定義式 <span class="text-nowrap">$\mathbb{P}(Z>z_{\sssig \alpha})=\alpha$。</span>此外，常態分配的期望值、中位數與眾數三者相等，反曲點落在 <span class="text-nowrap">$\mu\pm\sigma$，</span>偏態係數為 $0$ 而峰態係數為 <span class="text-nowrap">$3$。</span>最後兩點則預告了後文: 標準常態分配是許多分配在中央極限定理之下的極限分配，而不獨立的兩個常態變數若出自多元常態，其線性組合的變異數還要再加上 $2ab\rho\sigma_1\sigma_2$ 這一項。

[下一篇](/teaching-topics/ch4-p18-candidate/)以四道例題演練常態機率的計算，前三道的作法一致，都是先標準化再把所求化為標準常態的機率；最後一道則由 $2\,\phi(z)\Phi(\lambda z)$ 這個函數出發，先驗證它是一個合法的 pdf，再求其平方所服從的分配。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
