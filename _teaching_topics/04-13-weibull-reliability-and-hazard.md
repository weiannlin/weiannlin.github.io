---
title: "韋伯分配、可靠度函數與風險函數"
subtitle: "The Weibull Distribution, Reliability and Hazard Functions"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 4
topic: 13
order: 413
permalink: /teaching-topics/weibull-reliability-and-hazard/
date: 2026-08-12
published: false
excerpt: "韋伯分配由 $(X/\\alpha)^{\\gamma}$ 服從 $\\mathrm{Exp}(1)$ 這個分配所界定，其中 $\\alpha$ 為比例參數、$\\gamma$ 為形狀參數，期望值與變異數都要用伽瑪函數表示。本篇先證明其機率函數為合法的機率函數並求得期望值與變異數，再給出可靠度函數與風險函數的定義: 前者是壽命超過 $t$ 的機率，後者是已知在 $t$ 尚未故障之下，下一瞬間故障的機率密度。韋伯分配的風險函數為 $\\frac{\\gamma}{\\alpha}(t/\\alpha)^{\\gamma-1}$ 這個式子，因而在 $\\gamma$ 大於、等於、小於 $1$ 時分別遞增、恆定與遞減，其中恆定的情形正是無記憶性。最後證明由風險函數可以還原出 cdf 與 pdf，並以三道例題演練壽命期望值與條件存活機率的計算。"
---

[上一篇](/teaching-topics/gamma-distribution/)介紹[伽瑪分配](/teaching-topics/gamma-distribution/#def-gamma-distribution)，把等待第一次偶發事件的[指數分配](/teaching-topics/gamma-function-exponential-distribution/#def-exponential-distribution)推廣為等待第 $\alpha$ 次偶發事件所需要的時間。本篇的韋伯分配是另一個方向的推廣: 偶發事件的次數不變，改為要求 $X$ 除以 $\alpha$ 之後再取 $\gamma$ 次方，所得到的量服從 $\mathrm{Exp}(1)$ 這個分配。

韋伯分配的期望值與變異數都要用[伽瑪函數](/teaching-topics/gamma-function-exponential-distribution/#def-gamma-function)表示，本篇先證明其機率函數為合法的機率函數並求出這兩個量，再說明形狀參數取 $1$ 與取 $2$ 時分別對應到哪一個分配。接著給出可靠度函數與風險函數這兩個定義，它們是描述壽命的兩個基本工具，也正是韋伯分配比指數分配更適合描述壽命的原因所在。最後證明風險函數足以反推出 cdf 與 pdf，並以三道例題作為演練。

## 韋伯分配

<div id="def-weibull-distribution" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 4.15 (韋伯分配, Weibull distribution)</div>

**適用範圍**:

令 $X$ 為一個非負連續隨機變數，且 $\alpha,\gamma>0$ 為二常數，若 $X$ 滿足

$$
\left(\frac{\,X\,}{\alpha}\right)^{\gamma}\sim\mathrm{Exp}(1)
$$

則 $X$ 服從韋伯分配。

**值域範圍**:

$$
\mathcal{R}_{\sssig X}=\lbrace\,x\mid x\geqslant0\,\rbrace
$$

**表示式**:

$$
X\sim\mathrm{Weibull}(\alpha,\ \gamma)
$$

**參數與參數範圍**:

$\alpha>0$ 為比例參數；$\gamma>0$ 為形狀參數。

**機率函數**:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X}(x)=\frac{\gamma}{\,\alpha\,}\left(\frac{\,x\,}{\,\alpha\,}\right)^{\gamma-1}e^{-\left(\frac{x}{\alpha}\right)^{\gamma}},\ x\geqslant0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig X}(x)&=\frac{\gamma}{\,\alpha\,}\left(\frac{\,x\,}{\,\alpha\,}\right)^{\gamma-1}e^{-\left(\frac{x}{\alpha}\right)^{\gamma}},\\[0.45em]
&\quad\ x\geqslant0
\end{aligned}
$$

</div>

**期望值、變異數**:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(X)=\alpha\,\Gamma\left(\frac{1}{\,\gamma\,}+1\right),\quad \mathrm{Var}(X)=\alpha^{2}\left[\Gamma\left(\frac{2}{\,\gamma\,}+1\right)-\left[\Gamma\left(\frac{1}{\,\gamma\,}+1\right)\right]^{2}\right]
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\mathbb{E}(X)=\alpha\,\Gamma\left(\frac{1}{\,\gamma\,}+1\right),
$$

$$
\begin{aligned}
\mathrm{Var}(X)=\alpha^{2}\biggl[&\Gamma\left(\frac{2}{\,\gamma\,}+1\right)\\[0.3em]
&\qquad-\left[\Gamma\left(\frac{1}{\,\gamma\,}+1\right)\right]^{2}\biggr]
\end{aligned}
$$

</div>

</div>

韋伯分配 <span lang="en">(Weibull distribution)</span> 有一些地方需要注意:

(1) 我們證明韋伯分配的機率函數為合法的機率函數與期望值、變異數如下。
{: .topic-paren-item}

<div class="topic-proof" markdown="1">
**Proof.**

先驗證機率函數在值域範圍上的積分為 <span class="text-nowrap">$1$，</span>可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\int_{x\in\mathcal{R}_{\sssig X}}f_{\sssig X}(x)\,dx&=\int_{0}^{\infty}\frac{\gamma}{\,\alpha\,}\left(\frac{\,x\,}{\,\alpha\,}\right)^{\gamma-1}e^{-\left(\frac{x}{\alpha}\right)^{\gamma}}\,dx\\[0.45em]
&=\int_{0}^{\infty}e^{-\left(\frac{x}{\alpha}\right)^{\gamma}}\,d\left(\frac{x}{\alpha}\right)^{\gamma}=1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\int_{x\in\mathcal{R}_{\sssig X}}f_{\sssig X}(x)\,dx&=\int_{0}^{\infty}\frac{\gamma}{\,\alpha\,}\left(\frac{\,x\,}{\,\alpha\,}\right)^{\gamma-1}e^{-\left(\frac{x}{\alpha}\right)^{\gamma}}\,dx\\[0.45em]
&=\int_{0}^{\infty}e^{-\left(\frac{x}{\alpha}\right)^{\gamma}}\,d\left(\frac{x}{\alpha}\right)^{\gamma}=1
\end{aligned}
$$

</div>

令 <span class="text-nowrap">$Y=\left(\frac{\,X\,}{\alpha}\right)^{\gamma}\sim\mathrm{Exp}(1)$，</span>我們有 <span class="text-nowrap">$X=\alpha Y^{\frac{1}{\gamma}}$，</span>則可先計算 $Y$ 之 $k$ 階原動差為

$$
\mathbb{E}\bigl(Y^{k}\bigr)=\int_{0}^{\infty}y^{k}\,e^{-y}\,dy=\Gamma(k+1),\ k>0
$$

則可知 $X$ 之一二階原動差為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\mathbb{E}(X)=\mathbb{E}\bigl(\alpha Y^{\frac{1}{\gamma}}\bigr)=\alpha\,\mathbb{E}\bigl(Y^{\frac{1}{\gamma}}\bigr)=\alpha\,\Gamma\left(\frac{1}{\,\gamma\,}+1\right)\\[0.7em]
\mathbb{E}\bigl(X^{2}\bigr)=\mathbb{E}\bigl(\alpha^{2}Y^{\frac{2}{\gamma}}\bigr)=\alpha^{2}\,\mathbb{E}\bigl(Y^{\frac{2}{\gamma}}\bigr)=\alpha^{2}\,\Gamma\left(\frac{2}{\,\gamma\,}+1\right)
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\mathbb{E}\bigl(\alpha Y^{\frac{1}{\gamma}}\bigr)=\alpha\,\mathbb{E}\bigl(Y^{\frac{1}{\gamma}}\bigr)\\[0.45em]
&=\alpha\,\Gamma\left(\frac{1}{\,\gamma\,}+1\right)
\end{aligned}
$$

$$
\begin{aligned}
\mathbb{E}\bigl(X^{2}\bigr)&=\mathbb{E}\bigl(\alpha^{2}Y^{\frac{2}{\gamma}}\bigr)=\alpha^{2}\,\mathbb{E}\bigl(Y^{\frac{2}{\gamma}}\bigr)\\[0.45em]
&=\alpha^{2}\,\Gamma\left(\frac{2}{\,\gamma\,}+1\right)
\end{aligned}
$$

</div>

最後可得變異數為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}(X)=\alpha^{2}\left[\Gamma\left(\frac{2}{\,\gamma\,}+1\right)-\left[\Gamma\left(\frac{1}{\,\gamma\,}+1\right)\right]^{2}\right]
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(X)=\alpha^{2}\biggl[&\Gamma\left(\frac{2}{\,\gamma\,}+1\right)\\[0.3em]
&\qquad-\left[\Gamma\left(\frac{1}{\,\gamma\,}+1\right)\right]^{2}\biggr]
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

(2) 基於韋伯分配的定義，我們可知當 $\gamma=1$ 時，$X$ 服從 <span class="text-nowrap">$\mathrm{Exp}(\beta=\alpha)$，</span>此即
{: #weibull-exp-relation .topic-paren-item}

$$
\mathrm{Weibull}(\alpha,\gamma=1)\sim\mathrm{Exp}(\beta=\alpha)
$$

(3) 當 $\gamma=2$ 時，韋伯分配又被稱作**雷利分配 <span lang="en">(Rayleigh distribution)</span>**，這個分配在 $U,V\overset{\mathrm{iid}}{\sim}\mathcal{N}(0,\sigma^{2})$ 時，可以用來描述 $(U,V)$ 所構成的隨機向量之長度。[^normal-later]
{: .topic-paren-item}

[^normal-later]: 常態分配 <span lang="en">(normal distribution)</span> 在稍後馬上將會提到，讀者在此可以不必心急。

(4) 韋伯分配相較於[指數分配](/teaching-topics/gamma-function-exponential-distribution/#def-exponential-distribution)而言，更適合用來描述生物或機件的壽命，主要的原因與死亡或損壞的風險有關，見下列關於[可靠度](#def-reliability-function)與[風險](#def-hazard-function)的討論。
{: .topic-paren-item}

## 可靠度函數

<div id="def-reliability-function" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 4.16 (可靠度函數, reliability function)</div>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
R_{\sssig X}(t)=\mathbb{P}(X\geqslant t)=1-\mathbb{P}(X<t)=1-F_{\sssig X}(t)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
R_{\sssig X}(t)&=\mathbb{P}(X\geqslant t)=1-\mathbb{P}(X<t)\\[0.45em]
&=1-F_{\sssig X}(t)
\end{aligned}
$$

</div>

</div>

可靠度函數 <span lang="en">(reliability function)</span> 的應用相當廣泛，有以下需要注意的事項:

(1) 若非負隨機變數 $X$ 被用來表示某機件的壽命 <span lang="en">(lifetime)</span> 或存活時間 <span lang="en">(time to failure)</span> 時，其可靠度函數 $R_{\sssig X}(t)$ 可被理解為，該物品能使用超過 $t$ 時間的機率。[^survive-beyond]
{: .topic-paren-item}

[^survive-beyond]: 另有一說是，在 $t$ 時間時，此機件仍未故障的機率。

(2) 在生物統計學 <span lang="en">(biostatistics)</span> 的應用上，我們常以 $X$ 代表某生物的壽命，此時 $R_{\sssig X}(t)$ 常被記為 <span class="text-nowrap">$S_{\sssig X}(t)$，</span>並且被稱為存活函數 <span lang="en">(survivor function)</span>，即該生物能存活超過 $t$ 時間的機率。
{: .topic-paren-item}

(3) 無記憶性 <span lang="en">(memoryless property)</span> 就是以可靠度函數定義的，我們可將其寫為
{: .topic-paren-item}

<div class="topic-math-follow-before" markdown="1">

$$
\mathbb{P}(X>a+b\mid X>a)=\frac{\,\mathbb{P}(X>a+b)\,}{\mathbb{P}(X>a)}=\mathbb{P}(X>b)
$$

</div>

<div class="topic-math-follow" markdown="1">

$$
\Longleftrightarrow\ R_{\sssig X}(a+b)=R_{\sssig X}(a)\,R_{\sssig X}(b)
$$

</div>

事實上，無記憶性可被連結到**風險恆定**的情況，見以下關於風險函數 <span lang="en">(hazard function)</span> 的討論。
{: .topic-paren-cont}

## 風險函數

<div id="def-hazard-function" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 4.17 (風險函數, hazard function)</div>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
h_{\sssig X}(t)&=f(t\mid X\geqslant t)=\frac{f_{\sssig X}(t)}{\mathbb{P}(X\geqslant t)}=\frac{f_{\sssig X}(t)}{1-F_{\sssig X}(t)}\\[0.45em]
&=\frac{f_{\sssig X}(t)}{R_{\sssig X}(t)}=\frac{-R^{\prime}_{\sssig X}(t)}{R_{\sssig X}(t)}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
h_{\sssig X}(t)&=f(t\mid X\geqslant t)=\frac{f_{\sssig X}(t)}{\mathbb{P}(X\geqslant t)}\\[0.45em]
&=\frac{f_{\sssig X}(t)}{1-F_{\sssig X}(t)}=\frac{f_{\sssig X}(t)}{R_{\sssig X}(t)}\\[0.45em]
&=\frac{-R^{\prime}_{\sssig X}(t)}{R_{\sssig X}(t)}
\end{aligned}
$$

</div>

</div>

風險函數有以下需要注意的事項:

(1) 風險函數也被稱為**失效率函數 <span lang="en">(failure-rate function)</span>**，從其定義而言，其意義是指，已知某機件在 $t$ 的時間點上尚未故障的條件下，下一瞬間即將故障的機率密度。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個定義雖然聽起來有一點弔詭，但其實背後的想法相當直觀，因為我們在衡量的是機件在某個瞬間壞掉 (或生物在某個瞬間死亡) 的機率密度，然而，這個情況勢必是**在此瞬間該機件還能運作 (或該生物還存活)**，如此才有討論的意義，故以這個條件機率密度來討論是相當合理的。

基於上述概念，風險函數另有定義如下:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
h_{\sssig X}(t)&=\lim_{\triangle t\to0}\frac{\,\mathbb{P}(t\leqslant X\leqslant t+\triangle t\mid X\geqslant t)\,}{\triangle t}=\frac{\lim_{\triangle t\to0}\mathbb{P}(t\leqslant X\leqslant t+\triangle t)/\triangle t}{\mathbb{P}(X\geqslant t)}\\[0.45em]
&=\frac{1}{\,\mathbb{P}(X\geqslant t)\,}\lim_{\triangle t\to0}\frac{\,\int_{t}^{t+\triangle t}f_{\sssig X}(x)\,dx\,}{\triangle t}=\frac{1}{\,\mathbb{P}(X\geqslant t)\,}\lim_{\triangle t\to0}\frac{\,F_{\sssig X}(t+\triangle t)-F_{\sssig X}(t)\,}{\triangle t}\\[0.45em]
&=\frac{f_{\sssig X}(t)}{\,\mathbb{P}(X\geqslant t)\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&h_{\sssig X}(t)\\[0.45em]
&=\lim_{\triangle t\to0}\frac{\,\mathbb{P}(t\leqslant X\leqslant t+\triangle t\mid X\geqslant t)\,}{\triangle t}\\[0.45em]
&=\frac{\lim_{\triangle t\to0}\mathbb{P}(t\leqslant X\leqslant t+\triangle t)/\triangle t}{\mathbb{P}(X\geqslant t)}\\[0.45em]
&=\frac{1}{\mathbb{P}(X\geqslant t)}\lim_{\triangle t\to0}\frac{\int_{t}^{t+\triangle t}f_{\sssig X}(x)\,dx}{\triangle t}\\[0.45em]
&=\frac{1}{\mathbb{P}(X\geqslant t)}\lim_{\triangle t\to0}\frac{F_{\sssig X}(t+\triangle t)-F_{\sssig X}(t)}{\triangle t}\\[0.45em]
&=\frac{f_{\sssig X}(t)}{\,\mathbb{P}(X\geqslant t)\,}
\end{aligned}
$$

</div>

</div>

(2) 針對[韋伯分配](#def-weibull-distribution)，令 <span class="text-nowrap">$X\sim\mathrm{Weibull}(\alpha,\gamma)$，</span>則 <span class="text-nowrap">$X^{\gamma}\sim\mathrm{Exp}(\beta=\alpha^{\gamma})$，</span>可知可靠度函數為
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X\geqslant t)&=\mathbb{P}(X^{\gamma}\geqslant t^{\gamma})=\int_{t^{\gamma}}^{\infty}\frac{1}{\,\alpha^{\gamma}\,}e^{-\frac{s}{\alpha^{\gamma}}}\,ds\\[0.45em]
&=\left[-e^{-\frac{s}{\alpha^{\gamma}}}\right]^{\infty}_{t^{\gamma}}=e^{-\left(\frac{t}{\alpha}\right)^{\gamma}}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X\geqslant t)&=\mathbb{P}(X^{\gamma}\geqslant t^{\gamma})\\[0.45em]
&=\int_{t^{\gamma}}^{\infty}\frac{1}{\,\alpha^{\gamma}\,}e^{-\frac{s}{\alpha^{\gamma}}}\,ds\\[0.45em]
&=\left[-e^{-\frac{s}{\alpha^{\gamma}}}\right]^{\infty}_{t^{\gamma}}=e^{-\left(\frac{t}{\alpha}\right)^{\gamma}}
\end{aligned}
$$

</div>

故可知道其風險函數為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
h_{\sssig X}(t)=\frac{f_{\sssig X}(t)}{\,\mathbb{P}(X\geqslant t)\,}=\frac{\,\frac{\gamma}{\,\alpha\,}\left(\frac{\,t\,}{\,\alpha\,}\right)^{\gamma-1}e^{-\left(\frac{t}{\alpha}\right)^{\gamma}}\,}{e^{-\left(\frac{t}{\alpha}\right)^{\gamma}}}=\frac{\gamma}{\,\alpha\,}\left(\frac{\,t\,}{\,\alpha\,}\right)^{\gamma-1}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
h_{\sssig X}(t)&=\frac{f_{\sssig X}(t)}{\,\mathbb{P}(X\geqslant t)\,}\\[0.45em]
&=\frac{\,\frac{\gamma}{\,\alpha\,}\left(\frac{\,t\,}{\,\alpha\,}\right)^{\gamma-1}e^{-\left(\frac{t}{\alpha}\right)^{\gamma}}\,}{e^{-\left(\frac{t}{\alpha}\right)^{\gamma}}}\\[0.45em]
&=\frac{\gamma}{\,\alpha\,}\left(\frac{\,t\,}{\,\alpha\,}\right)^{\gamma-1}
\end{aligned}
$$

</div>

由此可以知道以下結論:
{: .topic-paren-cont}

- 若 <span class="text-nowrap">$\gamma>1$，</span>則 $h_{\sssig X}(t)$ 為 $t$ 之遞增函數
- 若 <span class="text-nowrap">$\gamma=1$，</span>則 $h_{\sssig X}(t)$ 為 $t$ 之常數函數
- 若 <span class="text-nowrap">$\gamma<1$，</span>則 $h_{\sssig X}(t)$ 為 $t$ 之遞減函數

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

讀者應該記得，在[韋伯分配的第 (2) 點](#weibull-exp-relation)中我們曾經提過，當 $\gamma=1$ 時，韋伯分配服從指數分配，又當 $\gamma=1$ 時，韋伯分配的風險函數是常數函數，此即稍早所提到的**風險恆定**，亦即風險不隨時間變化。事實上，風險恆定的性質正是[無記憶性](/teaching-topics/exponential-memoryless-and-minima/#thm-memoryless-exp)，此即，只要沒有壞的話，無論現在的時點 (壽命) $t$ 為何，下一個瞬間故障失效的機率密度是固定的，不與 $t$ 有關。

</div>

在上述的三種情況中，除 $\gamma=1$ 另被稱作無記憶性之外，$\gamma>1$ 又被稱作具有**正時間相關性 <span lang="en">(positive duration dependence)</span>**；而 $\gamma<1$ 又被稱作具有**負時間相關性 <span lang="en">(negative duration dependence)</span>**。
{: .topic-paren-cont}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這種命名源自於風險函數對於**已存活時間**的相關性，以機件或生物的壽命而言，通常較貼近於 $\gamma>1$ 的情況，也就是隨著壽命越來越大，損壞 (或死亡) 的風險就越來越高。

這種討論在工業上相當普遍，因為機件所受的損傷只會隨著使用而不斷累積，損壞的風險只會增高，這也是為何稍早曾提過，相較於指數分配而言，韋伯分配更適合用來描述生物或機件的壽命。

</div>

## 由風險函數還原分配

<div id="thm-hazard-to-distribution" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 4.16 (由風險函數還原分配, recovering a distribution from its hazard function)</div>

令 $X$ 為一非負連續隨機變數，則

(1)
{: .topic-paren-item}

$$
F_{\sssig X}(x)=1-\exp\left\lbrace-\int_{0}^{x}h_{\sssig X}(t)\,dt\right\rbrace
$$

(2)
{: .topic-paren-item}

$$
f_{\sssig X}(x)=h_{\sssig X}(x)\,\exp\left\lbrace-\int_{0}^{x}h_{\sssig X}(t)\,dt\right\rbrace
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.**

(1) 由[風險函數之定義](#def-hazard-function)可知
{: .topic-paren-item}

$$
h_{\sssig X}(t)=\frac{f_{\sssig X}(t)}{1-F_{\sssig X}(t)}=-\frac{d}{\,dt\,}\ln\bigl[1-F_{\sssig X}(t)\bigr]
$$

則我們有
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\int_{0}^{x}h_{\sssig X}(t)\,dt&=\int_{0}^{x}-\frac{d}{\,dt\,}\ln\bigl[1-F_{\sssig X}(t)\bigr]\,dt=-\int_{0}^{x}d\ln\bigl[1-F_{\sssig X}(t)\bigr]\\[0.45em]
&=-\ln\bigl[1-F_{\sssig X}(t)\bigr]^{x}_{0}=-\ln\bigl[1-F_{\sssig X}(x)\bigr]
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\int_{0}^{x}h_{\sssig X}(t)\,dt&=\int_{0}^{x}-\frac{d}{\,dt\,}\ln\bigl[1-F_{\sssig X}(t)\bigr]\,dt\\[0.45em]
&=-\int_{0}^{x}d\ln\bigl[1-F_{\sssig X}(t)\bigr]\\[0.45em]
&=-\ln\bigl[1-F_{\sssig X}(t)\bigr]^{x}_{0}\\[0.45em]
&=-\ln\bigl[1-F_{\sssig X}(x)\bigr]
\end{aligned}
$$

</div>

由此可得
{: .topic-paren-cont}

$$
1-F_{\sssig X}(x)=\exp\left\lbrace-\int_{0}^{x}h_{\sssig X}(t)\,dt\right\rbrace\qquad\therefore\, F_{\sssig X}(x)=1-\exp\left\lbrace-\int_{0}^{x}h_{\sssig X}(t)\,dt\right\rbrace
$$

(2) 由 (1) 可知
{: .topic-paren-item}

$$
F_{\sssig X}(x)=1-\exp\left\lbrace-\int_{0}^{x}h_{\sssig X}(t)\,dt\right\rbrace
$$

則
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f_{\sssig X}(x)&=\frac{d}{dx}F_{\sssig X}(x)\\[0.45em]
&=-\exp\left\lbrace-\int_{0}^{x}h_{\sssig X}(t)\,dt\right\rbrace\times\frac{d}{dx}\left(-\int_{0}^{x}h_{\sssig X}(t)\,dt\right)\\[0.45em]
&=h_{\sssig X}(x)\,\exp\left\lbrace-\int_{0}^{x}h_{\sssig X}(t)\,dt\right\rbrace\qquad(\,\text{由微積分基本定理可知}\,)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig X}(x)&=\frac{d}{dx}F_{\sssig X}(x)\\[0.45em]
&=-\exp\left\lbrace-\int_{0}^{x}h_{\sssig X}(t)\,dt\right\rbrace\\[0.25em]
&\qquad \times\frac{d}{dx}\left(-\int_{0}^{x}h_{\sssig X}(t)\,dt\right)\\[0.45em]
&=h_{\sssig X}(x)\,\exp\left\lbrace-\int_{0}^{x}h_{\sssig X}(t)\,dt\right\rbrace\\[0.25em]
&\qquad (\,\text{由微積分基本定理可知}\,)
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

## 韋伯分配與風險函數的例題

<div id="ex-weibull-1" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.35</div>

<div lang="en" markdown="1">
Suppose that the lifetime $T$ of a component is distributed as a Weibull random variable, with probability density function

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig T}(t)=\frac{\,\nu\,t^{\nu-1}\,}{\beta^{\nu}}\exp\left\lbrace-\left(\frac{t}{\beta}\right)^{\nu}\right\rbrace,\ t\geqslant0,\ \nu>0,\ \beta>0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig T}(t)&=\frac{\,\nu\,t^{\nu-1}\,}{\beta^{\nu}}\exp\left\lbrace-\left(\frac{t}{\beta}\right)^{\nu}\right\rbrace,\\[0.45em]
&\quad\ t\geqslant0,\ \nu>0,\ \beta>0
\end{aligned}
$$

</div>

<ol class="topic-list-paren">
  <li>Determine the expected value of <span class="text-nowrap">$T$,</span> which is the mean time to failure of the component, and express it with the gamma function <span class="text-nowrap">$\Gamma(\alpha)=\int_{0}^{\infty}x^{\alpha-1}e^{-x}\,dx$.</span></li>
  <li>Suppose that $T_1,T_2,\ldots,T_n$ are independent and identically distributed with the density given above. Find the distribution of <span class="text-nowrap">$T_{\sssig (1)}=\min(T_1,T_2,\ldots,T_n)$,</span> and determine whether it is again a Weibull distribution.</li>
  <li>Suppose that a system is built from $n$ identical components connected in series, the lifetimes of which are independent and identically distributed with the density given above. Find the mean time to failure (M.T.T.F.) of the system, and determine whether it is larger or smaller than the mean time to failure of a single component.</li>
</ol>
</div>

(1) 由於 <span class="text-nowrap">$T\sim\mathrm{Weibull}(\beta,\nu)$，</span>可令 <span class="text-nowrap">$Y=\left(\frac{\,T\,}{\beta}\right)^{\nu}\sim\mathrm{Exp}(1)$，</span>則由於 <span class="text-nowrap">$T=\beta\,Y^{\frac{1}{\nu}}$，</span>我們有
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(T)&=\mathbb{E}\bigl(\beta\,Y^{\frac{1}{\nu}}\bigr)=\beta\,\mathbb{E}\bigl(Y^{\frac{1}{\nu}}\bigr)=\beta\int_{0}^{\infty}y^{\frac{1}{\nu}}\,e^{-y}\,dy\\[0.45em]
&=\beta\int_{0}^{\infty}y^{\left(\frac{1}{\nu}+1\right)-1}\,e^{-y}\,dy=\beta\,\Gamma\left(\frac{1}{\nu}+1\right)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(T)&=\mathbb{E}\bigl(\beta\,Y^{\frac{1}{\nu}}\bigr)=\beta\,\mathbb{E}\bigl(Y^{\frac{1}{\nu}}\bigr)\\[0.45em]
&=\beta\int_{0}^{\infty}y^{\frac{1}{\nu}}\,e^{-y}\,dy\\[0.45em]
&=\beta\int_{0}^{\infty}y^{\left(\frac{1}{\nu}+1\right)-1}\,e^{-y}\,dy\\[0.45em]
&=\beta\,\Gamma\left(\frac{1}{\nu}+1\right)
\end{aligned}
$$

</div>

(2) 由[順序統計量的性質](/teaching-topics/order-statistics-examples/#thm-order-stat-samp-dist-cdf)，我們有
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
F_{\sssig T_{\sssig (1)}}(t)&=\mathbb{P}(T_{\sssig (1)}\leqslant t)=1-\mathbb{P}(T_{\sssig (1)}>t)=1-\mathbb{P}\bigl(\min(T_1,T_2,\ldots,T_n)>t\bigr)\\[0.45em]
&=1-\mathbb{P}(T_1>t,T_2>t,\ldots,T_n>t)=1-\prod_{i=1}^{n}\mathbb{P}(T_i>t)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig T_{\sssig (1)}}(t)&=\mathbb{P}(T_{\sssig (1)}\leqslant t)\\[0.45em]
&=1-\mathbb{P}(T_{\sssig (1)}>t)\\[0.45em]
&=1-\mathbb{P}\bigl(\min(T_1,T_2,\ldots,T_n)>t\bigr)\\[0.45em]
&=1-\mathbb{P}(T_1>t,T_2>t,\ldots,T_n>t)\\[0.45em]
&=1-\prod_{i=1}^{n}\mathbb{P}(T_i>t)
\end{aligned}
$$

</div>

其中
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(T_i>t)&=\mathbb{P}\left(\frac{\,T_i^{\nu}\,}{\beta^{\nu}}>\frac{\,t^{\nu}\,}{\beta^{\nu}}\right)=1-F_{\sssig Y}\left(\frac{\,t^{\nu}\,}{\beta^{\nu}}\right)\\[0.45em]
&=1-\left(1-e^{-\frac{\,t^{\nu}\,}{\beta^{\nu}}}\right)=e^{-\frac{\,t^{\nu}\,}{\beta^{\nu}}},\ t\geqslant0
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(T_i>t)&=\mathbb{P}\left(\frac{\,T_i^{\nu}\,}{\beta^{\nu}}>\frac{\,t^{\nu}\,}{\beta^{\nu}}\right)\\[0.45em]
&=1-F_{\sssig Y}\left(\frac{\,t^{\nu}\,}{\beta^{\nu}}\right)\\[0.45em]
&=1-\left(1-e^{-\frac{\,t^{\nu}\,}{\beta^{\nu}}}\right)\\[0.45em]
&=e^{-\frac{\,t^{\nu}\,}{\beta^{\nu}}},\ t\geqslant0
\end{aligned}
$$

</div>

故知道
{: .topic-paren-cont}

$$
F_{\sssig T_{\sssig (1)}}(t)=1-e^{-\frac{\,n\,t^{\nu}\,}{\beta^{\nu}}},\ t\geqslant0
$$

由此可知
{: .topic-paren-cont}

$$
f_{\sssig T_{\sssig (1)}}(t)=\frac{\,n\,\nu\,t^{\nu-1}\,}{\beta^{\nu}}e^{-\frac{\,n\,t^{\nu}\,}{\beta^{\nu}}},\ t\geqslant0
$$

此即
{: .topic-paren-cont}

$$
T_{\sssig (1)}\sim\mathrm{Weibull}\left(\beta\,n^{-\frac{1}{\nu}},\ \nu\right)
$$

(3) 由 (1) 之結果可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\bigl(T_{\sssig (1)}\bigr)=\beta\,n^{-\frac{1}{\nu}}\,\Gamma\left(\frac{1}{\nu}+1\right)\leqslant\mathbb{E}(T)=\beta\,\Gamma\left(\frac{1}{\nu}+1\right)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl(T_{\sssig (1)}\bigr)&=\beta\,n^{-\frac{1}{\nu}}\,\Gamma\left(\frac{1}{\nu}+1\right)\\[0.45em]
&\leqslant\mathbb{E}(T)=\beta\,\Gamma\left(\frac{1}{\nu}+1\right)
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

本題的題幹指出，壽命期望值就是故障前平均時間 <span lang="en">(mean time to failure, MTTF)</span>，讀者應該不會感到陌生，因為早在[第二章討論期望值的時候](/teaching-topics/properties-of-expectation/)，我們便曾經提過這件事。

更甚者，我們在當時也曾提過，[Theorem 2.8](/teaching-topics/expectation/#thm-expectation-tail-sum) 的連續型版本可以用來計算 MTTF，此即可靠度函數在值域範圍上的積分，也就是

$$
\mathbb{E}(X)=\int_{0}^{\infty}R_{\sssig X}(x)\,dx
$$

因此若本題並不是給 pdf，而是給了 cdf 或可靠度函數 (甚至是風險函數)，我們同樣可以先求得可靠度函數 <span class="text-nowrap">$R_{\sssig X}(x)$，</span>再透過 [Theorem 2.8](/teaching-topics/expectation/#thm-expectation-tail-sum) 求得壽命之 MTTF。

</div>

<div id="ex-weibull-2" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.36</div>

<div lang="en" markdown="1">
Suppose that an item has a lifetime whose hazard rate function is <span class="text-nowrap">$\lambda(t)=t^{3},\ t>0$.</span>

<ol class="topic-list-paren">
  <li>What is the probability that the item is still working at age <span class="text-nowrap">$2$?</span></li>
  <li>What is the probability that an item which has already been in use for one unit of time is still working at age <span class="text-nowrap">$2$?</span></li>
</ol>
</div>

(1) 令 $X$ 表示該元件壽命之分配，則 $X$ 之 cdf 為
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig X}(x)=1-\exp\left\lbrace-\int_{0}^{x}\lambda(t)\,dt\right\rbrace=1-\exp\left\lbrace-\int_{0}^{x}t^{3}\,dt\right\rbrace=1-e^{-\frac{x^{4}}{4}},\ x>0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig X}(x)&=1-\exp\left\lbrace-\int_{0}^{x}\lambda(t)\,dt\right\rbrace\\[0.45em]
&=1-\exp\left\lbrace-\int_{0}^{x}t^{3}\,dt\right\rbrace\\[0.45em]
&=1-e^{-\frac{x^{4}}{4}},\ x>0
\end{aligned}
$$

</div>

由此可得
{: .topic-paren-cont}

$$
R_{\sssig X}(x)=1-F_{\sssig X}(x)=e^{-\frac{x^{4}}{4}},\ x>0
$$

所求為
{: .topic-paren-cont}

$$
\mathbb{P}(X\geqslant2)=R_{\sssig X}(2)=e^{-4}
$$

(2) 所求為
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X\geqslant2\mid X\geqslant1)&=\frac{\,\mathbb{P}(X\geqslant2,X\geqslant1)\,}{\mathbb{P}(X\geqslant1)}=\frac{\,\mathbb{P}(X\geqslant2)\,}{\mathbb{P}(X\geqslant1)}\\[0.45em]
&=\frac{\,R_{\sssig X}(2)\,}{R_{\sssig X}(1)}=\frac{\,e^{-4}\,}{\,e^{-\frac{1}{4}}\,}=e^{-\frac{15}{4}}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X\geqslant2\mid X\geqslant1)&=\frac{\,\mathbb{P}(X\geqslant2,X\geqslant1)\,}{\mathbb{P}(X\geqslant1)}\\[0.45em]
&=\frac{\,\mathbb{P}(X\geqslant2)\,}{\mathbb{P}(X\geqslant1)}=\frac{\,R_{\sssig X}(2)\,}{R_{\sssig X}(1)}\\[0.45em]
&=\frac{\,e^{-4}\,}{\,e^{-\frac{1}{4}}\,}=e^{-\frac{15}{4}}
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

事實上，這個問題中的風險函數已經足以認出 $X$ 是一個具[韋伯分配](#def-weibull-distribution)之隨機變數，只是本題並不需要刻意從此分配計算機率。

</div>

<div id="ex-weibull-3" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.37</div>

<div lang="en" markdown="1">
Suppose that $T$ is a positive continuous random variable whose hazard rate function is given by

$$
r(t)=\frac{f(t)}{\,1-F(t)\,}
$$

where $f(t)$ denotes the probability density function of $T$ and $F(t)$ denotes its cumulative distribution function. Suppose further that the hazard rate function of the lifetime of a smoker is twice that of a non-smoker, and that a non-smoker aged $50$ lives beyond age $60$ with probability <span class="text-nowrap">$0.7$.</span> What is the probability that a smoker aged $50$ lives beyond age <span class="text-nowrap">$60$?</span>
</div>

依題意可令 $X$ 與 $Y$ 分別表示抽菸者與不抽菸者的壽命，$r_{\sssig X}(t)$ 與 $r_{\sssig Y}(t)$ 分別表示抽菸者與不抽菸者的風險函數，且 <span class="text-nowrap">$r_{\sssig X}(t)=2r_{\sssig Y}(t)$。</span>

由題目設定可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(Y\geqslant60\mid Y\geqslant50)=\frac{\,\mathbb{P}(Y\geqslant60)\,}{\mathbb{P}(Y\geqslant50)}=0.7
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(Y\geqslant60\mid Y\geqslant50)&=\frac{\,\mathbb{P}(Y\geqslant60)\,}{\mathbb{P}(Y\geqslant50)}=0.7
\end{aligned}
$$

</div>

又由於

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(Y\geqslant y)=R_{\sssig Y}(y)=1-F_{\sssig Y}(y)=\exp\left\lbrace-\int_{0}^{y}r_{\sssig Y}(t)\,dt\right\rbrace
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(Y\geqslant y)&=R_{\sssig Y}(y)=1-F_{\sssig Y}(y)\\[0.45em]
&=\exp\left\lbrace-\int_{0}^{y}r_{\sssig Y}(t)\,dt\right\rbrace
\end{aligned}
$$

</div>

我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(Y\geqslant60\mid Y\geqslant50)&=\frac{\,\mathbb{P}(Y\geqslant60)\,}{\mathbb{P}(Y\geqslant50)}=\frac{\,\exp\left\lbrace-\int_{0}^{60}r_{\sssig Y}(t)\,dt\right\rbrace\,}{\,\exp\left\lbrace-\int_{0}^{50}r_{\sssig Y}(t)\,dt\right\rbrace\,}\\[0.45em]
&=\exp\left\lbrace-\int_{50}^{60}r_{\sssig Y}(t)\,dt\right\rbrace=0.7
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(Y\geqslant60\mid Y\geqslant50)&=\frac{\,\mathbb{P}(Y\geqslant60)\,}{\mathbb{P}(Y\geqslant50)}\\[0.45em]
&=\frac{\,\exp\left\lbrace-\int_{0}^{60}r_{\sssig Y}(t)\,dt\right\rbrace\,}{\,\exp\left\lbrace-\int_{0}^{50}r_{\sssig Y}(t)\,dt\right\rbrace\,}\\[0.45em]
&=\exp\left\lbrace-\int_{50}^{60}r_{\sssig Y}(t)\,dt\right\rbrace=0.7
\end{aligned}
$$

</div>

所求為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X\geqslant60\mid X\geqslant50)&=\frac{\,\mathbb{P}(X\geqslant60)\,}{\mathbb{P}(X\geqslant50)}=\frac{\,\exp\left\lbrace-\int_{0}^{60}r_{\sssig X}(t)\,dt\right\rbrace\,}{\,\exp\left\lbrace-\int_{0}^{50}r_{\sssig X}(t)\,dt\right\rbrace\,}\\[0.45em]
&=\exp\left\lbrace-\int_{50}^{60}r_{\sssig X}(t)\,dt\right\rbrace=\exp\left\lbrace-\int_{50}^{60}2r_{\sssig Y}(t)\,dt\right\rbrace\\[0.45em]
&=\left[\exp\left\lbrace-\int_{50}^{60}r_{\sssig Y}(t)\,dt\right\rbrace\right]^{2}=0.7^{2}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(&X\geqslant60\mid X\geqslant50)=\frac{\,\mathbb{P}(X\geqslant60)\,}{\mathbb{P}(X\geqslant50)}\\[0.45em]
&=\frac{\,\exp\left\lbrace-\int_{0}^{60}r_{\sssig X}(t)\,dt\right\rbrace\,}{\,\exp\left\lbrace-\int_{0}^{50}r_{\sssig X}(t)\,dt\right\rbrace\,}\\[0.45em]
&=\exp\left\lbrace-\int_{50}^{60}r_{\sssig X}(t)\,dt\right\rbrace\\[0.45em]
&=\exp\left\lbrace-\int_{50}^{60}2r_{\sssig Y}(t)\,dt\right\rbrace\\[0.45em]
&=\left[\exp\left\lbrace-\int_{50}^{60}r_{\sssig Y}(t)\,dt\right\rbrace\right]^{2}=0.7^{2}
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個問題相當考驗讀者對於風險函數的熟悉程度，且由本題的結果，我們可以發現，事實上，關於求取「已活過 $t$ 歲的人活過 $t+a$ 歲」這種條件機率，可以直接透過風險函數 $t$ 到 $t+a$ 時間段上的積分變換而來，是一個有趣且實用的性質。

</div>

## 本篇小結

[Definition 4.15](#def-weibull-distribution) 由 $\left(\frac{\,X\,}{\alpha}\right)^{\gamma}\sim\mathrm{Exp}(1)$ 這條關係界定韋伯分配，其中 $\alpha$ 是比例參數、$\gamma$ 是形狀參數，機率函數為 $\frac{\gamma}{\,\alpha\,}\left(\frac{\,x\,}{\,\alpha\,}\right)^{\gamma-1}e^{-\left(\frac{x}{\alpha}\right)^{\gamma}}$ 這個式子。證明的三個步驟依序是: 把積分變數換成 $\left(\frac{x}{\alpha}\right)^{\gamma}$ 之後直接驗證積分為 <span class="text-nowrap">$1$、</span>由 $Y\sim\mathrm{Exp}(1)$ 的 $k$ 階原動差 $\Gamma(k+1)$ 得到 $X$ 的一二階原動差，再相減得到變異數。期望值與變異數因而都要用[伽瑪函數](/teaching-topics/gamma-function-exponential-distribution/#def-gamma-function)表示。定義之後的四點說明指出: $\gamma=1$ 時韋伯分配即為 <span class="text-nowrap">$\mathrm{Exp}(\beta=\alpha)$、</span>$\gamma=2$ 時被稱作雷利分配並可用來描述兩個獨立同分配的常態變數所構成之隨機向量的長度，以及韋伯分配比[指數分配](/teaching-topics/gamma-function-exponential-distribution/#def-exponential-distribution)更適合描述壽命的原因在於風險。

[Definition 4.16](#def-reliability-function) 的可靠度函數是 $1-F_{\sssig X}(t)$ 這個尾機率，讀作該物品能使用超過 $t$ 時間的機率；生物統計學上把它記為 $S_{\sssig X}(t)$ 並稱為存活函數。無記憶性正是以它定義的，寫成可靠度函數的形式即 $R_{\sssig X}(a+b)=R_{\sssig X}(a)\,R_{\sssig X}(b)$ 這條乘法關係。[Definition 4.17](#def-hazard-function) 的風險函數則是 $\frac{f_{\sssig X}(t)}{R_{\sssig X}(t)}$ 這個比值，也就是已知在 $t$ 尚未故障的條件下，下一瞬間故障的機率密度；把條件機率的極限寫開來，得到的正是同一個式子。

韋伯分配的風險函數為 $\frac{\gamma}{\,\alpha\,}\left(\frac{\,t\,}{\,\alpha\,}\right)^{\gamma-1}$ 這個式子，指數上的 $\gamma-1$ 決定它是遞增、常數還是遞減: $\gamma>1$ 時風險隨壽命增高，稱為正時間相關性；$\gamma=1$ 時風險恆定，這正是[無記憶性](/teaching-topics/exponential-memoryless-and-minima/#thm-memoryless-exp)，也對應到 $\gamma=1$ 時韋伯分配退回指數分配這件事；$\gamma<1$ 時風險遞減，稱為負時間相關性。機件的損傷只會隨使用而累積，通常較貼近 $\gamma>1$ 的情況，這就是韋伯分配比指數分配更適合描述壽命的理由。[Theorem 4.16](#thm-hazard-to-distribution) 反過來說明風險函數本身就足以決定分配: 把風險函數看成 $-\ln\bigl[1-F_{\sssig X}(t)\bigr]$ 的導數，積分之後即得 cdf，再微分一次即得 pdf。

三道例題各練一種用法。[Example 4.35](#ex-weibull-1) 先以 $Y\sim\mathrm{Exp}(1)$ 求得韋伯分配的壽命期望值，再說明 $n$ 個獨立同分配的韋伯變數取極小值之後仍為韋伯分配，比例參數縮成原來的 $n^{-\frac{1}{\nu}}$ 倍，因此串聯系統的故障前平均時間不會比單一元件來得長。[Example 4.36](#ex-weibull-2) 由風險函數 $\lambda(t)=t^{3}$ 出發，先用 [Theorem 4.16](#thm-hazard-to-distribution) 還原出 cdf 與可靠度函數，再算條件存活機率。[Example 4.37](#ex-weibull-3) 則不必求出分配: 兩個時點的可靠度相除，指數上只剩下風險函數在該時間段上的積分，抽菸者的風險是兩倍，答案因而是不抽菸者機率的平方。

下一篇轉入貝塔相關的機率模型，先介紹均勻分配，再由它給出機率積分轉換與逆機率積分轉換這兩個定理。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
