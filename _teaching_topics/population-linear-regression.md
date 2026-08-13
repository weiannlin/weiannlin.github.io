---
title: "母體線性迴歸式"
subtitle: "The Population Linear Regression Equation"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 23
order: 323
permalink: /teaching-topics/population-linear-regression/
date: 2026-08-13
published: false
excerpt: "相關係數衡量的是兩個隨機變數之間線性相關的強度，但這條直線本身的截距與斜率究竟是什麼，到目前為止還沒有寫出來。本篇的定理指出，當條件期望值恰好是條件變數的線性函數時，這條直線的截距與斜率完全由兩個變數的期望值、標準差與相關係數決定，此即母體線性迴歸式；證明的作法是先把條件期望值寫成 $\\beta_0+\\beta_1x$ 的形式，再由雙重期望值定理列出兩條式子解聯立方程式。把 $X$ 與 $Y$ 的角色對調可以得到逆迴歸，而正逆迴歸兩條斜率相乘恰好等於相關係數的平方，這給了一個由兩條迴歸式求相關係數的辦法。本篇最後以三道例題示範這條定理的用法。"
---

[上一篇](/teaching-topics/correlation-properties-and-matrix/)由[相關係數](/teaching-topics/correlation-coefficient/#def-corr)的範圍推得 [Theorem 3.20](/teaching-topics/correlation-properties-and-matrix/#thm-var-cov-ineq) 的[變異數](/teaching-topics/variance/#def-variance)-[共變異數](/teaching-topics/covariance/#def-covariance)不等式，再以 [Definition 3.20](/teaching-topics/correlation-properties-and-matrix/#def-corr-matrix) 把數個[隨機變數](/teaching-topics/random-variables-and-pmf/#def-random-variable)兩兩之間的相關係數收成[相關矩陣](/teaching-topics/correlation-properties-and-matrix/#def-corr-matrix)。

相關係數衡量的是 $X$ 與 $Y$ 之間線性相關的強度，但這條直線本身的截距與斜率是什麼，到目前為止還沒有寫出來。本篇要處理的正是這件事。當[條件期望值](/teaching-topics/conditional-expectation-and-variance/#def-conditional-expectation)恰好是條件變數的線性函數時，這條直線的截距與斜率完全由兩個變數的期望值、[標準差](/teaching-topics/variance-standard-deviation/#def-standard-deviation)與相關係數決定。本篇先給出這條定理與它的證明，接著說明它與[迴歸函數](/teaching-topics/double-expectation-theorem/#thm-regression-function)的關係，以及把 $X$ 與 $Y$ 的角色對調之後所得的正迴歸與逆迴歸，最後以三道例題示範它的用法。

## 母體線性迴歸式

<div id="thm-popu-reg" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 3.21 (母體線性迴歸式, population linear regression equation)</div>

若 $X$ 與 $Y$ 為二隨機變數，且條件期望值為條件變數的線性函數，則其形式如下:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\mathbb{E}(Y\mid X=x)=\mu_{\sssig Y}+\rho_{\sssig XY}\frac{\,\sigma_{\sssig Y}\,}{\sigma_{\sssig X}}(x-\mu_{\sssig X})\\[0.55em]
\text{或是}\quad\mathbb{E}(X\mid Y=y)=\mu_{\sssig X}+\rho_{\sssig XY}\frac{\,\sigma_{\sssig X}\,}{\sigma_{\sssig Y}}(y-\mu_{\sssig Y})
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\begin{aligned}
&\mathbb{E}(Y\mid X=x)\\[0.2em]
&\quad =\mu_{\sssig Y}+\rho_{\sssig XY}\frac{\,\sigma_{\sssig Y}\,}{\sigma_{\sssig X}}(x-\mu_{\sssig X})
\end{aligned}\\[0.55em]
\begin{aligned}
&\text{或是}\ \ \mathbb{E}(X\mid Y=y)\\[0.2em]
&\quad =\mu_{\sssig X}+\rho_{\sssig XY}\frac{\,\sigma_{\sssig X}\,}{\sigma_{\sssig Y}}(y-\mu_{\sssig Y})
\end{aligned}
\end{gathered}
$$

</div>

</div>

<div class="topic-proof" markdown="1">
**Proof.**

我們在此只證明第一種情況，第二種情況同理可得

若 $Y$ 在給定 $X=x$ 之下的條件期望值為 $x$ 的線性函數，則可令

$$
\mathbb{E}(Y\mid X=x)=\beta_0+\beta_1x
$$

其中 $\beta_0$ 與 $\beta_1$ 是二常數，分別表截距與斜率

由[雙重期望值定理](/teaching-topics/double-expectation-theorem/#thm-double-expectation)可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(Y)=\mathbb{E}\bigl[\mathbb{E}(Y\mid X)\bigr]=\mathbb{E}(\beta_0+\beta_1X)=\beta_0+\beta_1\mathbb{E}(X)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(Y)&=\mathbb{E}\bigl[\mathbb{E}(Y\mid X)\bigr]\\[0.45em]
&=\mathbb{E}(\beta_0+\beta_1X)=\beta_0+\beta_1\mathbb{E}(X)
\end{aligned}
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\text{又}\ \ \mathbb{E}(XY)&=\mathbb{E}\bigl[\mathbb{E}(XY\mid X)\bigr]=\mathbb{E}\bigl[X\mathbb{E}(Y\mid X)\bigr]=\mathbb{E}\bigl(\beta_0X+\beta_1X^{2}\bigr)\\[0.45em]
&=\beta_0\mathbb{E}(X)+\beta_1\mathbb{E}\bigl(X^{2}\bigr)=\beta_0\mathbb{E}(X)+\beta_1\Bigl(\mathrm{Var}(X)+\bigl[\mathbb{E}(X)\bigr]^{2}\Bigr)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\text{又}\ \ \mathbb{E}(XY)\\[0.45em]
&\quad =\mathbb{E}\bigl[\mathbb{E}(XY\mid X)\bigr]=\mathbb{E}\bigl[X\mathbb{E}(Y\mid X)\bigr]\\[0.45em]
&\quad =\mathbb{E}\bigl(\beta_0X+\beta_1X^{2}\bigr)\\[0.45em]
&\quad =\beta_0\mathbb{E}(X)+\beta_1\mathbb{E}\bigl(X^{2}\bigr)\\[0.45em]
&\quad =\beta_0\mathbb{E}(X)+\beta_1\Bigl(\mathrm{Var}(X)+\bigl[\mathbb{E}(X)\bigr]^{2}\Bigr)
\end{aligned}
$$

</div>

將上述二式解聯立方程式可以得到

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\beta_0=\mu_{\sssig Y}-\frac{\sigma_{\sssig XY}}{\sigma^{2}_{\sssig X}}\mu_{\sssig X}=\mu_{\sssig Y}-\rho_{\sssig XY}\frac{\sigma_{\sssig Y}}{\sigma_{\sssig X}}\mu_{\sssig X}\quad\text{與}\quad\beta_1=\frac{\sigma_{\sssig XY}}{\sigma^{2}_{\sssig X}}=\rho_{\sssig XY}\frac{\sigma_{\sssig Y}}{\sigma_{\sssig X}}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\beta_0=\mu_{\sssig Y}-\frac{\sigma_{\sssig XY}}{\sigma^{2}_{\sssig X}}\mu_{\sssig X}=\mu_{\sssig Y}-\rho_{\sssig XY}\frac{\sigma_{\sssig Y}}{\sigma_{\sssig X}}\mu_{\sssig X}\\[0.55em]
\text{與}\quad\beta_1=\frac{\sigma_{\sssig XY}}{\sigma^{2}_{\sssig X}}=\rho_{\sssig XY}\frac{\sigma_{\sssig Y}}{\sigma_{\sssig X}}
\end{gathered}
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ \mathbb{E}(Y\mid X=x)&=\mu_{\sssig Y}-\rho_{\sssig XY}\frac{\sigma_{\sssig Y}}{\,\sigma_{\sssig X}\,}\mu_{\sssig X}+\rho_{\sssig XY}\frac{\,\sigma_{\sssig Y}\,}{\sigma_{\sssig X}}x\\[0.45em]
&=\mu_{\sssig Y}+\rho_{\sssig XY}\frac{\,\sigma_{\sssig Y}\,}{\sigma_{\sssig X}}(x-\mu_{\sssig X})
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\Longrightarrow\ \mathbb{E}(Y\mid X=x)\\[0.45em]
&\quad =\mu_{\sssig Y}-\rho_{\sssig XY}\frac{\sigma_{\sssig Y}}{\,\sigma_{\sssig X}\,}\mu_{\sssig X}+\rho_{\sssig XY}\frac{\,\sigma_{\sssig Y}\,}{\sigma_{\sssig X}}x\\[0.45em]
&\quad =\mu_{\sssig Y}+\rho_{\sssig XY}\frac{\,\sigma_{\sssig Y}\,}{\sigma_{\sssig X}}(x-\mu_{\sssig X})
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

母體線性迴歸式 <span lang="en">(population linear regression equation)</span> 有一些地方需要注意:

(1) 在 [Theorem 3.8](/teaching-topics/double-expectation-theorem/#thm-regression-function) 中，我們曾稱條件期望值 $\mathbb{E}(Y\mid X=x)$ <span class="text-nowrap">(或 $\mathbb{E}(X\mid Y=y)$)</span> 為 $Y$ 對 $X$ <span class="text-nowrap">(或 $X$ 對 $Y$)</span> 的迴歸函數 <span lang="en">(regression function)</span>。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

事實上，若強調其母體性質，我們應稱其為母體迴歸式 <span lang="en">(population regression equation)</span>，但是，讀者應再一次注意到，**條件期望值雖然是條件變數的函數，卻未必一定是「線性的」函數**，只是當這個函數是線性函數時，會具有以上的性質，並且被稱作母體**線性**迴歸式。

</div>

(2) 由於線性模型 (linear model) 的領域時常將 $X$ 視為解釋變數 <span lang="en">(explanatory variable)</span>、將 $Y$ 視為反應變數 <span lang="en">(response variable)</span>，故我們會認為 $\mathbb{E}(Y\mid X=x)$ $=$ $\beta_0+\beta_1x$ 是**正迴歸 <span lang="en">(direct regression)</span>** 而 $\mathbb{E}(X\mid Y=y)$ $=$ $\alpha_0+\alpha_1y$ 是**逆迴歸 <span lang="en">(reverse regression)</span>**，其中:
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\alpha_0=\mu_{\sssig X}-\frac{\,\sigma_{\sssig XY}\,}{\sigma^{2}_{\sssig Y}}\mu_{\sssig Y}=\mu_{\sssig X}-\rho_{\sssig XY}\frac{\,\sigma_{\sssig X}\,}{\sigma_{\sssig Y}}\mu_{\sssig Y}\quad\text{與}\quad\alpha_1=\frac{\,\sigma_{\sssig XY}\,}{\sigma^{2}_{\sssig Y}}=\rho_{\sssig XY}\frac{\,\sigma_{\sssig X}\,}{\sigma_{\sssig Y}}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\alpha_0=\mu_{\sssig X}-\frac{\,\sigma_{\sssig XY}\,}{\sigma^{2}_{\sssig Y}}\mu_{\sssig Y}=\mu_{\sssig X}-\rho_{\sssig XY}\frac{\,\sigma_{\sssig X}\,}{\sigma_{\sssig Y}}\mu_{\sssig Y}\\[0.55em]
\text{與}\quad\alpha_1=\frac{\,\sigma_{\sssig XY}\,}{\sigma^{2}_{\sssig Y}}=\rho_{\sssig XY}\frac{\,\sigma_{\sssig X}\,}{\sigma_{\sssig Y}}
\end{gathered}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

在不同領域中，$X$ 與 $Y$ 所對應的角色有很多不同的名字，但通常擔任的角色是相同的。

</div>

並且正逆迴歸有這個性質:
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\beta_1\cdot\alpha_1=\rho_{\sssig XY}\frac{\,\sigma_{\sssig Y}\,}{\sigma_{\sssig X}}\cdot\rho_{\sssig XY}\frac{\,\sigma_{\sssig X}\,}{\sigma_{\sssig Y}}=\rho^{2}_{\sssig XY}\\[0.55em]
\Longrightarrow\ \rho_{\sssig XY}=\operatorname{sgn}(\beta_1)\sqrt{\beta_1\cdot\alpha_1}=\operatorname{sgn}(\alpha_1)\sqrt{\beta_1\cdot\alpha_1}
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\beta_1\cdot\alpha_1&=\rho_{\sssig XY}\frac{\,\sigma_{\sssig Y}\,}{\sigma_{\sssig X}}\cdot\rho_{\sssig XY}\frac{\,\sigma_{\sssig X}\,}{\sigma_{\sssig Y}}=\rho^{2}_{\sssig XY}\\[0.45em]
&\Longrightarrow\ \rho_{\sssig XY}=\operatorname{sgn}(\beta_1)\sqrt{\beta_1\cdot\alpha_1}\\[0.45em]
&\qquad\quad\ \ =\operatorname{sgn}(\alpha_1)\sqrt{\beta_1\cdot\alpha_1}
\end{aligned}
$$

</div>

其中，$\rho_{\sssig XY}$ 的正負號與正迴歸及逆迴歸的斜率相同。
{: .topic-paren-cont}

## 母體線性迴歸式的例題

<div id="ex-two-regression-lines" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.46</div>

<div lang="en" markdown="1">
Suppose that two random variables $X$ and $Y$ satisfy the two regression equations

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(Y\mid X)=30-1.5X\quad\text{and}\quad\mathbb{E}(X\mid Y)=12-0.54Y
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{E}(Y\mid X)=30-1.5X\\[0.55em]
\text{and}\quad\mathbb{E}(X\mid Y)=12-0.54Y
\end{gathered}
$$

</div>

Determine the absolute value of the correlation coefficient between $X$ and <span class="text-nowrap">$Y$.</span>
</div>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\rho^{2}_{\sssig XY}=(-1.5)\times(-0.54)=0.81\ \Longrightarrow\ \lvert\rho_{\sssig XY}\rvert=\sqrt{0.81}=0.9
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\rho^{2}_{\sssig XY}&=(-1.5)\times(-0.54)=0.81\\[0.45em]
&\Longrightarrow\ \lvert\rho_{\sssig XY}\rvert=\sqrt{0.81}=0.9
\end{aligned}
$$

</div>

</div>

<div id="ex-height-weight-regression" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.47</div>

<div lang="en" markdown="1">
Suppose that for people in East Asia the correlation coefficient between the height $X$ and the weight $Y$ equals <span class="text-nowrap">$0.65$,</span> and that

$$
\mathbb{E}(Y\mid X=x)=22.5+0.25x
$$

<ol class="topic-list-paren">
  <li>Evaluate the ratio <span class="text-nowrap">$\frac{\mathrm{Var}(Y)}{\mathrm{Var}(X)}$.</span></li>
  <li>Given that <span class="text-nowrap">$\mathbb{E}(X)=170$,</span> find <span class="text-nowrap">$\mathbb{E}(Y)$.</span></li>
</ol>
</div>

(1) 依據[母體線性迴歸式](#thm-popu-reg)，已知 $\mathbb{E}(Y$ $\mid$ $X=x)$ $=$ <span class="text-nowrap">$22.5+0.25x$，</span>則可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
0.25=\rho_{\sssig XY}\frac{\,\sigma_{\sssig Y}\,}{\sigma_{\sssig X}}\quad\text{故}\quad\frac{\,\sigma_{\sssig Y}\,}{\sigma_{\sssig X}}=\frac{0.25}{\,0.65\,}=\frac{5}{\,13\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
0.25=\rho_{\sssig XY}\frac{\,\sigma_{\sssig Y}\,}{\sigma_{\sssig X}}\\[0.55em]
\text{故}\quad\frac{\,\sigma_{\sssig Y}\,}{\sigma_{\sssig X}}=\frac{0.25}{\,0.65\,}=\frac{5}{\,13\,}
\end{gathered}
$$

</div>

$$
\Longrightarrow\ \frac{\,\mathrm{Var}(Y)\,}{\mathrm{Var}(X)}=\frac{5^{2}}{\,13^{2}\,}=\frac{25}{\,169\,}
$$

(2) 再由[雙重期望值定理](/teaching-topics/double-expectation-theorem/#thm-double-expectation)可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(Y)&=\mathbb{E}\bigl[\mathbb{E}(Y\mid X)\bigr]=\mathbb{E}\bigl[22.5+0.25X\bigr]\\[0.45em]
&=22.5+0.25\,\mathbb{E}(X)\ \Longrightarrow\ \mathbb{E}(Y)=65
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(Y)&=\mathbb{E}\bigl[\mathbb{E}(Y\mid X)\bigr]\\[0.45em]
&=\mathbb{E}\bigl[22.5+0.25X\bigr]\\[0.45em]
&=22.5+0.25\,\mathbb{E}(X)\\[0.45em]
&\Longrightarrow\ \mathbb{E}(Y)=65
\end{aligned}
$$

</div>

</div>

<div id="ex-joint-pdf-regression-line" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.48</div>

<div lang="en" markdown="1">
Suppose that the random variables $X$ and $Y$ have the joint pmf

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
p_{\sssig XY}(x,y)=\frac{2}{\,n(n+1)\,},\quad y=1,2,\ldots,x,\ \ x=1,2,\ldots,n
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
p_{\sssig XY}(x,y)=\frac{2}{\,n(n+1)\,},\\[0.55em]
y=1,2,\ldots,x,\ \ x=1,2,\ldots,n
\end{gathered}
$$

</div>

<ol class="topic-list-paren">
  <li>Find <span class="text-nowrap">$\mathbb{E}(X\mid Y=y)$.</span></li>
  <li>Find <span class="text-nowrap">$\mathbb{E}(Y\mid X=x)$.</span></li>
  <li>Determine the correlation coefficient <span class="text-nowrap">$\rho_{\sssig XY}$.</span></li>
</ol>
</div>

(1) 先求 $Y$ 的邊際 pmf 與 $X$ 給定 $Y=y$ 的條件 pmf
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
p_{\sssig Y}(y)=\sum_{x=y}^{n}\frac{2}{\,n(n+1)\,}=\frac{2}{\,n(n+1)\,}(n-y+1),\ y=1,2,\ldots,n
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig Y}(y)&=\sum_{x=y}^{n}\frac{2}{\,n(n+1)\,}\\[0.45em]
&=\frac{2}{\,n(n+1)\,}(n-y+1),\\[0.2em]
&\quad y=1,2,\ldots,n
\end{aligned}
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
p_{\sssig X\mid Y}(x\mid y)=\frac{\,p_{\sssig XY}(x,y)\,}{p_{\sssig Y}(y)}=\frac{1}{\,n-y+1\,},\ 1\leqslant y\leqslant x\leqslant n,\ x,y\in\mathbb{N}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig X\mid Y}(x\mid y)&=\frac{\,p_{\sssig XY}(x,y)\,}{p_{\sssig Y}(y)}=\frac{1}{\,n-y+1\,},\\[0.2em]
&\quad 1\leqslant y\leqslant x\leqslant n,\ x,y\in\mathbb{N}
\end{aligned}
$$

</div>

由此可得
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X\mid Y=y)&=\sum_{x=y}^{n}x\,p_{\sssig X\mid Y}(x\mid y)=\frac{1}{\,n-y+1\,}\frac{\,(y+n)(n-y+1)\,}{2}\\[0.45em]
&=\frac{\,y\,}{2}+\frac{\,n\,}{\,2\,},\ y=1,\ldots,n
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}(X\mid Y=y)=\sum_{x=y}^{n}x\,p_{\sssig X\mid Y}(x\mid y)\\[0.45em]
&\quad =\frac{1}{\,n-y+1\,}\frac{\,(y+n)(n-y+1)\,}{2}\\[0.45em]
&\quad =\frac{\,y\,}{2}+\frac{\,n\,}{\,2\,},\ y=1,\ldots,n
\end{aligned}
$$

</div>

(2) 同理先求 $X$ 的邊際 pmf 與 $Y$ 給定 $X=x$ 的條件 pmf
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
p_{\sssig X}(x)=\sum_{y=1}^{x}\frac{2}{\,n(n+1)\,}=\frac{2x}{\,n(n+1)\,},\ x=1,2,\ldots,n
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig X}(x)&=\sum_{y=1}^{x}\frac{2}{\,n(n+1)\,}=\frac{2x}{\,n(n+1)\,},\\[0.2em]
&\quad x=1,2,\ldots,n
\end{aligned}
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
p_{\sssig Y\mid X}(y\mid x)=\frac{\,p_{\sssig XY}(x,y)\,}{p_{\sssig X}(x)}=\frac{1}{\,x\,},\ 1\leqslant y\leqslant x\leqslant n,\ x,y\in\mathbb{N}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig Y\mid X}(y\mid x)&=\frac{\,p_{\sssig XY}(x,y)\,}{p_{\sssig X}(x)}=\frac{1}{\,x\,},\\[0.2em]
&\quad 1\leqslant y\leqslant x\leqslant n,\ x,y\in\mathbb{N}
\end{aligned}
$$

</div>

由此可得
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(Y\mid X=x)&=\sum_{y=1}^{x}y\,p_{\sssig Y\mid X}(y\mid x)=\frac{1}{\,x\,}\frac{\,x(x+1)\,}{2}\\[0.45em]
&=\frac{\,x\,}{2}+\frac{1}{\,2\,},\ x=1,\ldots,n
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}(Y\mid X=x)=\sum_{y=1}^{x}y\,p_{\sssig Y\mid X}(y\mid x)\\[0.45em]
&\quad =\frac{1}{\,x\,}\frac{\,x(x+1)\,}{2}\\[0.45em]
&\quad =\frac{\,x\,}{2}+\frac{1}{\,2\,},\ x=1,\ldots,n
\end{aligned}
$$

</div>

(3) 兩條迴歸式的斜率都是 <span class="text-nowrap">$\frac{1}{\,2\,}$，</span>故
{: .topic-paren-item}

$$
\rho_{\sssig XY}=+\sqrt{\frac{1}{\,2\,}\times\frac{1}{\,2\,}}=\frac{1}{\,2\,}
$$

</div>

## 本篇小結

[Theorem 3.21](#thm-popu-reg) 處理的是條件期望值恰好為條件變數線性函數的情形。此時這條直線的截距與斜率完全由兩個變數的期望值、標準差與相關係數決定，寫出來就是 $\mathbb{E}(Y\mid X=x)$ $=$ $\mu_{\sssig Y}+\rho_{\sssig XY}\frac{\sigma_{\sssig Y}}{\sigma_{\sssig X}}(x-\mu_{\sssig X})$ 這條式子。證明的作法是先把條件期望值寫成 $\beta_0+\beta_1x$ 的形式，再由[雙重期望值定理](/teaching-topics/double-expectation-theorem/#thm-double-expectation)分別算出 $\mathbb{E}(Y)$ 與 $\mathbb{E}(XY)$ 這兩個值，兩條式子解聯立方程式即得截距與斜率。

我們在 [Theorem 3.8](/teaching-topics/double-expectation-theorem/#thm-regression-function) 就已經稱條件期望值為迴歸函數，此處若要強調母體的性質，應稱其為母體迴歸式；而條件期望值雖然一定是條件變數的函數，卻未必是線性函數，只有在它是線性函數的時候才有上述的形式，因而另外冠上「線性」二字。把 $X$ 與 $Y$ 的角色對調可以得到逆迴歸 $\mathbb{E}(X\mid Y=y)$ $=$ <span class="text-nowrap">$\alpha_0+\alpha_1y$，</span>它的截距與斜率只要把上面的式子中 $X$ 與 $Y$ 的位置互換即可。正逆迴歸兩條斜率相乘恰好是 <span class="text-nowrap">$\rho^{2}_{\sssig XY}$，</span>再配上斜率的正負號就能求得 <span class="text-nowrap">$\rho_{\sssig XY}$，</span>這是一個由兩條迴歸式反求相關係數的辦法。

三道例題都用到這個結構。[Example 3.46](#ex-two-regression-lines) 直接把兩條迴歸式的斜率相乘，開根號即得相關係數的絕對值為 <span class="text-nowrap">$0.9$。</span>[Example 3.47](#ex-height-weight-regression) 由斜率 $0.25$ 與相關係數 $0.65$ 反推兩個標準差的比值，進而得到兩個變數變異數的比值，第二小題則直接由[雙重期望值定理](/teaching-topics/double-expectation-theorem/#thm-double-expectation)求得 $\mathbb{E}(Y)$ 的值。[Example 3.48](#ex-joint-pdf-regression-line) 由聯合 pmf 依序求出兩個邊際 pmf 與兩個條件 pmf，兩個條件期望值都是條件變數的線性函數且斜率同為 <span class="text-nowrap">$\frac{1}{2}$，</span>兩者相乘再開根號即得 $\rho_{\sssig XY}$ 的值。

[下一篇](/teaching-topics/many-to-many-transformations/)離開共變異數與相關係數的主題，開始處理[隨機向量](/teaching-topics/random-vectors-joint-pmf/#def-random-vector)的函數轉換，先介紹多對多的情形。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
