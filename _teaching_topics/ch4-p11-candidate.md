---
title: "指數分配的無記憶性與極小值"
subtitle: "The Memoryless Property and Minima of Exponential Variables"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 4
topic: 11
order: 411
permalink: /teaching-topics/ch4-p11-candidate/
date: 2026-08-12
published: false
excerpt: "指數分配的無記憶性說的是，已經等了 $a$ 單位時間而偶發事件仍未發生時，再多等 $b$ 單位時間仍然沒有發生的機率，與從頭開始等 $b$ 單位時間的機率完全相同。本篇先證明這個性質，再證明它的逆敘述: 非負連續隨機變數只要具備無記憶性，就一定服從指數分配，兩者因而互為充要條件。接著轉入兩個獨立指數分配的比較，先指出兩者取極小值之後仍為指數分配，頻率參數為兩者相加，再求出 $Y$ 先發生的機率為 $\\frac{\\lambda_2}{\\,\\lambda_1+\\lambda_2\\,}$ 這個比值。最後以三道例題演練無記憶性的計算、極小值與指標函數的獨立性，以及參數 $\\theta$ 所對應的百分位數。"
---

[上一篇](/teaching-topics/ch4-p10-candidate/)先給出伽瑪函數，再以卜瓦松過程中的等待時間定義[指數分配](/teaching-topics/ch4-p10-candidate/#def-exponential-distribution)，並說明它與卜瓦松分配之間的對偶關係。本篇處理指數分配最具代表性的一項性質，也就是無記憶性 <span lang="en">(memoryless property)</span>: 只要偶發事件還沒有發生，已經等了多久，都不會改變往後還要再等多久的機率。

[幾何分配](/teaching-topics/ch4-p04-candidate/#def-geometric)那一篇已經證明過離散型的無記憶性，也說明了幾何分配與指數分配是唯二具有這個性質的分配。本篇先證明指數分配的版本，再證明它的逆敘述，說明無記憶性反過來也足以決定分配。其後轉入兩個獨立指數分配的比較，分別求出兩者取極小值之後的分配，以及兩者之中哪一個先發生的機率，最後以三道例題作為演練。

## 指數分配的無記憶性

<div id="thm-memoryless-exp" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 4.12 (無記憶性, memoryless property)</div>

若 <span class="text-nowrap">$X\sim\mathrm{Exp}(\beta)$，</span>則

$$
\mathbb{P}(X>a+b\mid X>a)=\mathbb{P}(X>b)
$$

其中 $a,b>0$

</div>

<div class="topic-proof" markdown="1">
**Proof.** 先計算 $X$ 大於某個數值的機率，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X>x)=\int_{x}^{\infty}\frac{1}{\,\beta\,}e^{-\frac{\,t\,}{\beta}}\,dt=\Bigl[-e^{-\frac{\,t\,}{\beta}}\Bigr]^{\infty}_{x}=e^{-\frac{\,x\,}{\beta}}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X>x)&=\int_{x}^{\infty}\frac{1}{\,\beta\,}e^{-\frac{\,t\,}{\beta}}\,dt\\[0.45em]
&=\Bigl[-e^{-\frac{\,t\,}{\beta}}\Bigr]^{\infty}_{x}=e^{-\frac{\,x\,}{\beta}}
\end{aligned}
$$

</div>

則我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X>a+b\mid X>a)&=\frac{\,\mathbb{P}(X>a+b,\ X>a)\,}{\mathbb{P}(X>a)}=\frac{\,\mathbb{P}(X>a+b)\,}{\mathbb{P}(X>a)}\\[0.45em]
&=\frac{e^{-\frac{(a+b)}{\beta}}}{e^{-\frac{a}{\beta}}}=e^{-\frac{b}{\beta}}=\mathbb{P}(X>b)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(X>a+b\mid X>a)\\[0.45em]
&\quad =\frac{\,\mathbb{P}(X>a+b,\ X>a)\,}{\mathbb{P}(X>a)}\\[0.45em]
&\quad =\frac{\,\mathbb{P}(X>a+b)\,}{\mathbb{P}(X>a)}=\frac{e^{-\frac{(a+b)}{\beta}}}{e^{-\frac{a}{\beta}}}\\[0.45em]
&\quad =e^{-\frac{b}{\beta}}=\mathbb{P}(X>b)
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這裡的無記憶性與 [Theorem 4.4](/teaching-topics/ch4-p04-candidate/#thm-memoryless) 是一樣的，差別只在當時是以幾何分配為例，而此處是以指數分配為例；而此處的直觀意義是「只要還沒有等到偶發事件，就永遠像是重新等一次一樣」。

事實上，我們在當時也曾經說明，此二分配是唯二具有無記憶性的分配，且無記憶性的源頭都源自於 $f_{\sssig X}(a)$ 與 $f_{\sssig X}(a+1)$ 的比例是固定的，因而使得 $\mathbb{P}(X>a+b)$ 與 $\mathbb{P}(X>a)$ 的比例同樣也會是固定的，而這個比例便固定在 <span class="text-nowrap">$\mathbb{P}(X>b)$。</span>

</div>

## 連續型無記憶性的逆敘述

我們稍微在此打住。既然指數分配與幾何分配是唯二具有無記憶性的分配，且當時我們曾經證明過，[一個具有無記憶性的非負整數值隨機變數必定是幾何分配](/teaching-topics/ch4-p04-candidate/#thm-geometric-memoryless-converse)，那我們能不能在這裡說明，如果有一非負連續隨機變數具有無記憶性，則這個分配必定是指數分配呢? 答案同樣是可以的，見[下列定理](#thm-exponential-memoryless-converse)。

<div id="thm-exponential-memoryless-converse" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 4.13 (連續型無記憶性的逆敘述, converse of the memoryless property (continuous))</div>

若 $X$ 為一非負連續隨機變數，且已知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X>a+b\mid X>a)=\mathbb{P}(X>b),\ \forall a,b>0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(X>a+b\mid X>a)\\[0.45em]
&\quad =\mathbb{P}(X>b),\ \forall a,b>0
\end{aligned}
$$

</div>

則我們可知

$$
X\sim\mathrm{Exp}(\beta)
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.** 由已知條件，我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X>a+b\mid X>a)&=\frac{\,\mathbb{P}(X>a+b,\ X>a)\,}{\mathbb{P}(X>a)}\\[0.45em]
&=\frac{\,\mathbb{P}(X>a+b)\,}{\mathbb{P}(X>a)}=\mathbb{P}(X>b),\ \forall a,b>0
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(X>a+b\mid X>a)\\[0.45em]
&\quad =\frac{\,\mathbb{P}(X>a+b,\ X>a)\,}{\mathbb{P}(X>a)}\\[0.45em]
&\quad =\frac{\,\mathbb{P}(X>a+b)\,}{\mathbb{P}(X>a)}\\[0.45em]
&\quad =\mathbb{P}(X>b),\ \forall a,b>0
\end{aligned}
$$

</div>

此即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X>a+b)=\mathbb{P}(X>a)\,\mathbb{P}(X>b),\ \forall a,b>0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(X>a+b)=\mathbb{P}(X>a)\,\mathbb{P}(X>b),\\[0.3em]
&\quad\ \forall a,b>0
\end{aligned}
$$

</div>

若令 $R(x)=\mathbb{P}(X>x),\ x>0$ 則

$$
R(a+b)=R(a)\,R(b),\ a,b>0
$$

考慮 <span class="text-nowrap">$R(x+h)=R(x)\,R(h),\ \forall h>0$，</span>則我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\frac{\,R(x+h)-R(x)\,}{h}=\frac{\,R(x)\,R(h)-R(x)\,}{h}=R(x)\frac{\,R(h)-1\,}{h}=R(x)\frac{\,R(h)-R(0)\,}{h}\\[0.7em]
\Longrightarrow\ \lim_{h\to0}\frac{\,R(x+h)-R(x)\,}{h}=R(x)\lim_{h\to0}\frac{\,R(h)-R(0)\,}{h}=R(x)\,R^{\prime}(0)
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\frac{\,R(x+h)-R(x)\,}{h}&=\frac{\,R(x)\,R(h)-R(x)\,}{h}\\[0.45em]
&=R(x)\frac{\,R(h)-1\,}{h}\\[0.45em]
&=R(x)\frac{\,R(h)-R(0)\,}{h}
\end{aligned}
$$

$$
\begin{aligned}
\Longrightarrow\ &\lim_{h\to0}\frac{\,R(x+h)-R(x)\,}{h}\\[0.45em]
&\quad =R(x)\lim_{h\to0}\frac{\,R(h)-R(0)\,}{h}\\[0.45em]
&\quad =R(x)\,R^{\prime}(0)
\end{aligned}
$$

</div>

其中，若令 <span class="text-nowrap">$R^{\prime}(0)=-\frac{1}{\,\beta\,}$，</span>則可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\frac{\,R^{\prime}(x)\,}{R(x)}=R^{\prime}(0)=-\frac{1}{\,\beta\,}\ \Longrightarrow\ \ln R(x)=-\frac{1}{\,\beta\,}x+C
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\frac{\,R^{\prime}(x)\,}{R(x)}=R^{\prime}(0)=-\frac{1}{\,\beta\,}\\[0.5em]
\Longrightarrow\ \ln R(x)=-\frac{1}{\,\beta\,}x+C
\end{gathered}
$$

</div>

(由微分方程求解，$C$ 為積分常數)

且由 $R(0)=\mathbb{P}(X>0)=1$ 代入上式可得 <span class="text-nowrap">$C=0$，</span>此即

$$
R(x)=\mathbb{P}(X>x)=e^{-\frac{x}{\,\beta\,}},\ x>0
$$

由此可知

$$
F_{\sssig X}(x)=1-R(x)=1-e^{-\frac{x}{\,\beta\,}},\ x>0
$$

故可知

$$
X\sim\mathrm{Exp}(\beta),\ \beta>0
$$

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個定理補足了關於指數分配無記憶性的雙向敘述，也就是說，爾後只要我們知道某個非負連續隨機變數服從指數分配，若且唯若其具備無記憶性。

</div>

<div id="ex-exponential-memoryless-1" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.28</div>

<div lang="en" markdown="1">
Suppose that the random variable $X$ has probability density function

$$
f(x)=\frac{1}{\,2\,}e^{-\frac{x}{2}},\ 0\leqslant x<\infty
$$

<ol class="topic-list-paren">
  <li>Determine the mean, the variance and the moment-generating function of <span class="text-nowrap">$X$.</span></li>
  <li>Find the cumulative distribution function of <span class="text-nowrap">$X$.</span></li>
  <li>Evaluate <span class="text-nowrap">$\mathbb{P}(X>5\mid X>2)$.</span></li>
</ol>
</div>

(1) 由題目敘述可知 <span class="text-nowrap">$X\sim\mathrm{Exp}(\beta=2)$，</span>則
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(X)=2,\quad \mathrm{Var}(X)=2^{2}=4,\quad M_{\sssig X}(t)=(1-2t)^{-1},\ t<\frac{1}{\,2\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{E}(X)=2,\quad \mathrm{Var}(X)=2^{2}=4\\[0.5em]
M_{\sssig X}(t)=(1-2t)^{-1},\ t<\frac{1}{\,2\,}
\end{gathered}
$$

</div>

(2) 由 cdf 的定義可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig X}(x)=\int_{0}^{x}\frac{1}{\,2\,}e^{-\frac{t}{\,2\,}}\,dt=\biggl[-e^{-\frac{t}{\,2\,}}\biggr]^{x}_{0}=1-e^{-\frac{x}{2}}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig X}(x)&=\int_{0}^{x}\frac{1}{\,2\,}e^{-\frac{t}{\,2\,}}\,dt\\[0.45em]
&=\biggl[-e^{-\frac{t}{\,2\,}}\biggr]^{x}_{0}=1-e^{-\frac{x}{2}}
\end{aligned}
$$

</div>

(3) 由[指數分配的無記憶性](#thm-memoryless-exp)可以知道
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X>5\mid X>2)=\mathbb{P}(X>3)=1-\mathbb{P}(X\leqslant3)=1-\bigl(1-e^{-\frac{3}{2}}\bigr)=e^{-\frac{3}{2}}\fallingdotseq0.2231
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X>5\mid X>2)&=\mathbb{P}(X>3)\\[0.45em]
&=1-\mathbb{P}(X\leqslant3)\\[0.45em]
&=1-\bigl(1-e^{-\frac{3}{2}}\bigr)\\[0.45em]
&=e^{-\frac{3}{2}}\fallingdotseq0.2231
\end{aligned}
$$

</div>

</div>

## 兩個獨立指數分配的極小值

<div id="thm-min-of-exponentials" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 4.14 (兩個獨立指數分配的極小值, minimum of two exponential variables)</div>

若 <span class="text-nowrap">$X\sim\mathrm{Exp}(\lambda_1)\indep Y\sim\mathrm{Exp}(\lambda_2)$，</span>則

$$
\min\lbrace X,Y\rbrace\sim\mathrm{Exp}(\lambda_1+\lambda_2)
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.** 若令 <span class="text-nowrap">$Z=\min\lbrace X,Y\rbrace$，</span>則我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
F_{\sssig Z}(z)&=\mathbb{P}(Z\leqslant z)=\mathbb{P}\bigl(\min\lbrace X,Y\rbrace\leqslant z\bigr)=1-\mathbb{P}\bigl(\min\lbrace X,Y\rbrace>z\bigr)\\[0.45em]
&=1-\mathbb{P}(X>z,\ Y>z)=1-\mathbb{P}(X>z)\,\mathbb{P}(Y>z)\\[0.45em]
&=1-\bigl(e^{-\lambda_1 z}\bigr)\bigl(e^{-\lambda_2 z}\bigr)=1-e^{-(\lambda_1+\lambda_2)z}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig Z}(z)&=\mathbb{P}(Z\leqslant z)\\[0.45em]
&=\mathbb{P}\bigl(\min\lbrace X,Y\rbrace\leqslant z\bigr)\\[0.45em]
&=1-\mathbb{P}\bigl(\min\lbrace X,Y\rbrace>z\bigr)\\[0.45em]
&=1-\mathbb{P}(X>z,\ Y>z)\\[0.45em]
&=1-\mathbb{P}(X>z)\,\mathbb{P}(Y>z)\\[0.45em]
&=1-\bigl(e^{-\lambda_1 z}\bigr)\bigl(e^{-\lambda_2 z}\bigr)\\[0.45em]
&=1-e^{-(\lambda_1+\lambda_2)z}
\end{aligned}
$$

</div>

又可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig Z}(z)=\frac{d\,F_{\sssig Z}(z)}{d\,z}=(\lambda_1+\lambda_2)e^{-(\lambda_1+\lambda_2)z},\ z>0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig Z}(z)&=\frac{d\,F_{\sssig Z}(z)}{d\,z}\\[0.45em]
&=(\lambda_1+\lambda_2)e^{-(\lambda_1+\lambda_2)z},\ z>0
\end{aligned}
$$

</div>

故可知

$$
Z=\min\lbrace X,Y\rbrace\sim\mathrm{Exp}(\lambda_1+\lambda_2)
$$

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<!-- ref-point: 書稿 mathstatch4.tex 第 2016 行以 \pageref{minGeo} 指向書稿第 742 行的
     那則註記 (幾何分配版本極小值的直觀意義)。網頁沒有頁碼，依 ch4-p04-candidate.md 第
     731 行預留的指示，改為指向該篇 #note-min-geometric-intuition 的站內連結，「頁」與
     頁碼因而不再出現於行文。 -->

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個定理背後的直觀意義與[幾何分配的版本](/teaching-topics/ch4-p04-candidate/#note-min-geometric-intuition)完全相同，因為當我們關注的是 $X$ 與 $Y$ 當中較小者，事實上就好像我們在一個[卜瓦松過程](/teaching-topics/ch4-p08-candidate/#def-poisson-process)中，只要 $X$ 或 $Y$ 所對應的偶發事件，有任一者發生，即視為發生，因此偶發事件發生的頻率 (rate) 應直接疊加。

</div>

## 兩個獨立指數分配的先後次序

<div id="thm-exponential-race" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 4.15 (兩個獨立指數分配的先後次序, which of two exponential variables comes first)</div>

若 <span class="text-nowrap">$X\sim\mathrm{Exp}(\lambda_1)\indep Y\sim\mathrm{Exp}(\lambda_2)$，</span>則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X>Y)=\mathbb{P}\bigl(\min\lbrace X,Y\rbrace=Y\bigr)=\frac{\lambda_2}{\,\lambda_1+\lambda_2\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{P}(X>Y)=\mathbb{P}\bigl(\min\lbrace X,Y\rbrace=Y\bigr)\\[0.5em]
=\frac{\lambda_2}{\,\lambda_1+\lambda_2\,}
\end{gathered}
$$

</div>

</div>

<div class="topic-proof" markdown="1">
**Proof.**

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X>Y)&=\mathbb{E}\bigl[\mathbb{P}(X>Y\mid Y)\bigr]=\int_{0}^{\infty}\mathbb{P}(X>Y\mid Y=y)\,f_{\sssig Y}(y)\,dy\\[0.45em]
&=\int_{0}^{\infty}\mathbb{P}(X>y)\,f_{\sssig Y}(y)\,dy=\int_{0}^{\infty}e^{-\lambda_1 y}\,\lambda_2e^{-\lambda_2 y}\,dy\\[0.45em]
&=\biggl[\frac{-\lambda_2}{\,\lambda_1+\lambda_2\,}e^{-(\lambda_1+\lambda_2)y}\biggr]_{0}^{\infty}=\frac{\lambda_2}{\,\lambda_1+\lambda_2\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(X>Y)=\mathbb{E}\bigl[\mathbb{P}(X>Y\mid Y)\bigr]\\[0.45em]
&\quad =\int_{0}^{\infty}\mathbb{P}(X>Y\mid Y=y)\,f_{\sssig Y}(y)\,dy\\[0.45em]
&\quad =\int_{0}^{\infty}\mathbb{P}(X>y)\,f_{\sssig Y}(y)\,dy\\[0.45em]
&\quad =\int_{0}^{\infty}e^{-\lambda_1 y}\,\lambda_2e^{-\lambda_2 y}\,dy\\[0.45em]
&\quad =\biggl[\frac{-\lambda_2}{\,\lambda_1+\lambda_2\,}e^{-(\lambda_1+\lambda_2)y}\biggr]_{0}^{\infty}\\[0.45em]
&\quad =\frac{\lambda_2}{\,\lambda_1+\lambda_2\,}
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個定理背後的直觀意義是，在卜瓦松過程中，我們考慮 $X$ 與 $Y$ 對應的偶發事件，則 $X>Y$ 之事件等價於「$Y$ 所對應的偶發事件先發生」，而這個事件發生的機率與兩種偶發事件的發生率有關，是 <span class="text-nowrap">$\frac{\lambda_2}{\,\lambda_1+\lambda_2\,}$，</span>若 $Y$ 的偶發事件發生率越高，則這個機率會越接近 <span class="text-nowrap">$1$。</span>

同理，我們亦有下列的結論

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X<Y)=\mathbb{P}(\min\lbrace X,Y\rbrace=X)=\frac{\lambda_1}{\,\lambda_1+\lambda_2\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{P}(X<Y)=\mathbb{P}(\min\lbrace X,Y\rbrace=X)\\[0.5em]
=\frac{\lambda_1}{\,\lambda_1+\lambda_2\,}
\end{gathered}
$$

</div>

此外，若考慮 $X_1,\ldots,X_n$ 為獨立的指數分配隨機變數，頻率參數各自為 <span class="text-nowrap">$\lambda_i,\ i=1,\ldots,n$，</span>則由前述二定理可以推廣得到

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\min\lbrace X_1,\ldots,X_n\rbrace\sim\mathrm{Exp}\Bigl(\lambda=\sum_{i=1}^{n}\lambda_i\Bigr)\\[0.7em]
\text{與}\ \mathbb{P}\bigl(\min\lbrace X_1,\ldots,X_n\rbrace=X_k\bigr)=\frac{\lambda_k}{\,\sum_{i=1}^{n}\lambda_i\,}
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\min\lbrace X_1,\ldots,X_n\rbrace\sim\mathrm{Exp}\Bigl(\lambda=\sum_{i=1}^{n}\lambda_i\Bigr)\\[0.6em]
\text{與}\ \mathbb{P}\bigl(\min\lbrace X_1,\ldots,X_n\rbrace=X_k\bigr)\\[0.3em]
=\frac{\lambda_k}{\,\sum_{i=1}^{n}\lambda_i\,}
\end{gathered}
$$

</div>

</div>

<div id="ex-exponential-memoryless-2" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.29</div>

<div lang="en" markdown="1">
Suppose that the failure time $X$ follows an exponential distribution with parameter <span class="text-nowrap">$\lambda$,</span> and that the termination time <span class="text-nowrap">$Y$,</span> which is itself random, follows an exponential distribution with parameter <span class="text-nowrap">$\theta$,</span> the two variables being independent of each other. Let <span class="text-nowrap">$T=\min(X,Y)$,</span> and let $\delta=1$ when $X\leqslant Y$ and $\delta=0$ when <span class="text-nowrap">$X>Y$.</span>

<ol class="topic-list-paren">
  <li>Evaluate <span class="text-nowrap">$\mathbb{P}(\delta=1)$.</span></li>
  <li>Determine whether $T$ and $\delta$ are independent.</li>
</ol>
</div>

(1) 依照題目敘述可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(\delta=1)&=\mathbb{P}(X\leqslant Y)=1-\mathbb{P}(X>Y)=1-\mathbb{E}\bigl[\mathbb{P}(X>Y\mid Y)\bigr]\\[0.45em]
&=1-\int_{0}^{\infty}\mathbb{P}(X>Y\mid Y=y)\,f_{\sssig Y}(y)\,dy=1-\int_{0}^{\infty}\mathbb{P}(X>y)\,f_{\sssig Y}(y)\,dy\\[0.45em]
&=1-\int_{0}^{\infty}e^{-\lambda y}\,\theta e^{-\theta y}\,dy=1-\biggl[\frac{-\theta}{\,\lambda+\theta\,}e^{-(\lambda+\theta)y}\biggr]_{0}^{\infty}=\frac{\lambda}{\,\lambda+\theta\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(\delta=1)=\mathbb{P}(X\leqslant Y)\\[0.45em]
&\quad =1-\mathbb{P}(X>Y)\\[0.45em]
&\quad =1-\mathbb{E}\bigl[\mathbb{P}(X>Y\mid Y)\bigr]\\[0.45em]
&\quad =1-\int_{0}^{\infty}\mathbb{P}(X>Y\mid Y=y)\\[0.25em]
&\qquad\qquad \times f_{\sssig Y}(y)\,dy\\[0.45em]
&\quad =1-\int_{0}^{\infty}\mathbb{P}(X>y)\,f_{\sssig Y}(y)\,dy\\[0.45em]
&\quad =1-\int_{0}^{\infty}e^{-\lambda y}\,\theta e^{-\theta y}\,dy\\[0.45em]
&\quad =1-\biggl[\frac{-\theta}{\,\lambda+\theta\,}e^{-(\lambda+\theta)y}\biggr]_{0}^{\infty}\\[0.45em]
&\quad =\frac{\lambda}{\,\lambda+\theta\,}
\end{aligned}
$$

</div>

(2) 依題意可先計算
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(T\geqslant t)=\mathbb{P}(\min\lbrace X,Y\rbrace\geqslant t)=\mathbb{P}(X\geqslant t,\ Y\geqslant t)=\mathbb{P}(X\geqslant t)\,\mathbb{P}(Y\geqslant t)=e^{-(\lambda+\theta)t}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(T\geqslant t)&=\mathbb{P}(\min\lbrace X,Y\rbrace\geqslant t)\\[0.45em]
&=\mathbb{P}(X\geqslant t,\ Y\geqslant t)\\[0.45em]
&=\mathbb{P}(X\geqslant t)\,\mathbb{P}(Y\geqslant t)\\[0.45em]
&=e^{-(\lambda+\theta)t}
\end{aligned}
$$

</div>

又由題目設定可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(T\geqslant t\mid\delta=1)&=\frac{\,\mathbb{P}(T\geqslant t,\ \delta=1)\,}{\mathbb{P}(\delta=1)}=\frac{\,\mathbb{P}(Y\geqslant X\geqslant t)\,}{\mathbb{P}(\delta=1)}=\frac{\,\int_{t}^{\infty}\int_{t}^{y}f_{\sssig XY}(x,y)\,dx\,dy\,}{\mathbb{P}(\delta=1)}\\[0.45em]
&=\frac{\,\int_{t}^{\infty}\int_{t}^{y}\lambda\theta e^{-(\lambda x+\theta y)}\,dx\,dy\,}{\frac{\lambda}{\,\lambda+\theta\,}}=\frac{\,\frac{\lambda}{\,\lambda+\theta\,}e^{-(\lambda+\theta)t}\,}{\frac{\lambda}{\,\lambda+\theta\,}}\\[0.45em]
&=e^{-(\lambda+\theta)t}=\mathbb{P}(T\geqslant t),\ \forall t>0
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(T\geqslant t\mid\delta=1)=\frac{\,\mathbb{P}(T\geqslant t,\ \delta=1)\,}{\mathbb{P}(\delta=1)}\\[0.45em]
&\quad =\frac{\,\mathbb{P}(Y\geqslant X\geqslant t)\,}{\mathbb{P}(\delta=1)}\\[0.45em]
&\quad =\frac{\,\int_{t}^{\infty}\int_{t}^{y}f_{\sssig XY}(x,y)\,dx\,dy\,}{\mathbb{P}(\delta=1)}\\[0.45em]
&\quad =\frac{\,\int_{t}^{\infty}\int_{t}^{y}\lambda\theta e^{-(\lambda x+\theta y)}\,dx\,dy\,}{\frac{\lambda}{\,\lambda+\theta\,}}\\[0.45em]
&\quad =\frac{\,\frac{\lambda}{\,\lambda+\theta\,}e^{-(\lambda+\theta)t}\,}{\frac{\lambda}{\,\lambda+\theta\,}}\\[0.45em]
&\quad =e^{-(\lambda+\theta)t}=\mathbb{P}(T\geqslant t),\ \forall t>0
\end{aligned}
$$

</div>

故知道
{: .topic-paren-cont}

$$
T\indep\delta
$$

</div>

<div id="ex-exponential-memoryless-3" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.30</div>

<div lang="en" markdown="1">
Suppose that <span class="text-nowrap">$X\sim\mathrm{Exp}(\theta)$,</span> where the parameter $\theta$ is the mean of <span class="text-nowrap">$X$,</span> so that the density function of $X$ is

$$
f_{\sssig X}(x;\theta)=\frac{1}{\,\theta\,}e^{-x/\theta},\ x>0
$$

Determine the value of $r$ for which $\theta$ is the $r$-th percentile of <span class="text-nowrap">$X$.</span>
</div>

可先計算

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X\leqslant\theta)=\int_{0}^{\theta}\frac{1}{\,\theta\,}e^{-x/\theta}\,dx=1-e^{-1}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X\leqslant\theta)&=\int_{0}^{\theta}\frac{1}{\,\theta\,}e^{-x/\theta}\,dx\\[0.45em]
&=1-e^{-1}
\end{aligned}
$$

</div>

故依照[百分位數](/teaching-topics/quantiles/#def-quantile)定義可知，$\theta$ 除期望值外，同時為第 $100\times(1-e^{-1})$ 百分位數。

</div>

## 本篇小結

[Theorem 4.12](#thm-memoryless-exp) 把 [Theorem 4.4](/teaching-topics/ch4-p04-candidate/#thm-memoryless) 的無記憶性由幾何分配換成指數分配，敘述仍然是 $\mathbb{P}(X>a+b\mid X>a)=\mathbb{P}(X>b)$ 這條等式，只是 $a$ 與 $b$ 由正整數換成正實數。證明的關鍵同樣只有一步，即 $\mathbb{P}(X>x)=e^{-\frac{x}{\beta}}$ 這個機率，兩者相除時 $e^{-\frac{a}{\beta}}$ 恰好被約掉。直觀上，只要還沒有等到偶發事件，就永遠像是重新等一次一樣。

[Theorem 4.13](#thm-exponential-memoryless-converse) 把這件事反過來說。已知條件先化為 $\mathbb{P}(X>a+b)=\mathbb{P}(X>a)\,\mathbb{P}(X>b)$ 這條乘法關係，令 $R(x)=\mathbb{P}(X>x)$ 之後即為 $R(a+b)=R(a)\,R(b)$ 這個函數方程式。把增量為 $h$ 的差商寫出來再取極限，得到 $R^{\prime}(x)=R(x)\,R^{\prime}(0)$ 這條微分方程式；令 $R^{\prime}(0)=-\frac{1}{\beta}$ 並以 $R(0)=1$ 定出積分常數，還原出來的正是指數分配的 cdf。兩個定理合起來，說明非負連續隨機變數服從指數分配與具備無記憶性互為充要條件。[Example 4.28](#ex-exponential-memoryless-1) 即是這個性質最直接的用法: 由 $\mathbb{P}(X>5\mid X>2)$ 直接改寫為 $\mathbb{P}(X>3)$ 這個尾機率，不必再做一次條件機率的積分。

[Theorem 4.14](#thm-min-of-exponentials) 指出兩個獨立指數分配取極小值之後仍為指數分配，頻率參數為 $\lambda_1+\lambda_2$ 這個和。證明由極小值的餘事件下手: $\min\lbrace X,Y\rbrace>z$ 等價於 $X$ 與 $Y$ 都大於 <span class="text-nowrap">$z$，</span>兩個尾機率因獨立而相乘，指數上的頻率因而相加。其直觀意義與[幾何分配的版本](/teaching-topics/ch4-p04-candidate/#note-min-geometric-intuition)完全相同: 兩種偶發事件只要任一者發生即視為發生，發生的頻率自然疊加。

[Theorem 4.15](#thm-exponential-race) 則回答兩者之中哪一個先發生: 以 $Y$ 為條件再取期望值，$\mathbb{P}(X>Y)$ 化為一個可直接積出的積分，結果為 $\frac{\lambda_2}{\,\lambda_1+\lambda_2\,}$ 這個比值，$Y$ 的頻率越高，這個機率越接近 <span class="text-nowrap">$1$。</span>同一組論證可以推廣到 $n$ 個獨立的指數分配，極小值的頻率為各頻率之和，而極小值恰好由第 $k$ 個變數取到的機率為 $\lambda_k$ 在總和之中所佔的比例。[Example 4.29](#ex-exponential-memoryless-2) 把這兩個結果放在一起: 第一小題求的就是 <span class="text-nowrap">$\mathbb{P}(X\leqslant Y)$，</span>第二小題則把 $T$ 的尾機率與其在 $\delta=1$ 之下的條件尾機率算出來，兩者相同因而 $T$ 與 $\delta$ 獨立。[Example 4.30](#ex-exponential-memoryless-3) 換一個角度看參數 $\theta$ 這個量: 它既是期望值，同時也是第 $100\times(1-e^{-1})$ 百分位數。

[下一篇](/teaching-topics/ch4-p12-candidate/)把指數分配所描述的「等到一次偶發事件」推廣為「等到第 $\alpha$ 次偶發事件」，得到的即為伽瑪分配。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
