---
title: "非一對一的函數轉換"
subtitle: "Many-to-One Transformations"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 24
order: 224
permalink: /lecture-notes/many-to-one-transformations/
date: 2026-08-06
published: true
excerpt: "$g(\\cdot)$ 不是一對一函數時反函數並不存在，Jacobian 法的公式無法直接套用，cdf 法也不能再靠保序或反序取反函數。通用的作法是將原先的隨機變數分段，直到該段中反函數存在，各段分別轉換為新變數的 pdf 後再連接起來。本篇的三道例題分別以標準常態分配的平方、拉普拉斯分配的絕對值，以及均勻分配在 $(-2,1)$ 上的平方示範這個作法，每一題都以 cdf 法與 Jacobian 法各解一次。"
---

[上一篇](/lecture-notes/one-to-one-transformations/)介紹[隨機變數](/lecture-notes/random-variables-and-pmf/#def-random-variable)的函數轉換，離散型有直接列表法、pmf 法與 mgf 法，連續型有 cdf 法、Jacobian 法與 mgf 法。該篇所處理的 $Y=2X+1$、$Y=\frac{1}{X}$ 與 $Y=\bigl(1+e^{-X}\bigr)^{-1}$，其中的 $g(\cdot)$ 都是一對一函數，反函數直接存在，[pmf 法](/lecture-notes/one-to-one-transformations/#prop-discrete-transformation-pmf)、[cdf 法](/lecture-notes/one-to-one-transformations/#prop-cdf-method)與 [Jacobian 法](/lecture-notes/one-to-one-transformations/#prop-jacobian-method)的公式都能直接套用。

然而 $g(\cdot)$ 的反函數並不是任何時候都存在。該篇在 [Jacobian 法](/lecture-notes/one-to-one-transformations/#prop-jacobian-method)之後已經先交代過這時候的作法。我們只需將原先的隨機變數分段，直到該段中 $g(\cdot)$ 的反函數存在，分段轉換為新變數的 pdf 後，再以分段隨機變數的概念將各段連接起來即可。本篇的三道例題都要用到這個作法，$Y=Z^{2}$、$Y\_{i}=\lvert X\_{i}\rvert$ 與 $Y=X^{2}$ 都不是一對一的轉換，每一題都以 cdf 法與 Jacobian 法各解一次。Jacobian 法正是分段之後再相加，cdf 法則不必先取反函數，直接由 cdf 的定義把 $\lbrace Y\leqslant y\rbrace$ 改寫成 $X$ 的事件即可。

<div id="ex-chi-square-from-normal" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.50</div>

<div lang="en" markdown="1">
Suppose that $Z$ has the probability density function (pdf)

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig Z}(z)=\frac{1}{\,\sqrt{2\pi}\,}e^{-\frac{1}{2}z^{2}},\quad-\infty<z<\infty
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig Z}(z)&=\frac{1}{\,\sqrt{2\pi}\,}e^{-\frac{1}{2}z^{2}}, ~-\infty<z<\infty
\end{aligned}
$$

</div>

Determine the pdf of $Y=Z^{2}$.
</div>

**[ cdf 法 ]**

由 cdf 之定義可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
F_{\sssig Y}(y)&=\mathbb{P}(Y\leqslant y)=\mathbb{P}\bigl(Z^{2}\leqslant y\bigr)=\mathbb{P}\bigl(\lvert Z\rvert\leqslant\sqrt{y}\bigr)\\[0.45em]
&=\mathbb{P}\bigl(-\sqrt{y}\leqslant Z\leqslant\sqrt{y}\bigr)=F_{\sssig Z}\bigl(\sqrt{y}\bigr)-F_{\sssig Z}\bigl(-\sqrt{y}\bigr)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig Y}(y)&=\mathbb{P}(Y\leqslant y)\\[.45em]
&=\mathbb{P}\bigl(Z^{2}\leqslant y\bigr)\\[0.45em]
&=\mathbb{P}\bigl(\lvert Z\rvert\leqslant\sqrt{y}\bigr)\\[0.45em]
&=\mathbb{P}\bigl(-\sqrt{y}\leqslant Z\leqslant\sqrt{y}\bigr)\\[0.45em]
&=F_{\sssig Z}\bigl(\sqrt{y}\bigr)-F_{\sssig Z}\bigl(-\sqrt{y}\bigr)
\end{aligned}
$$

</div>

則可知 $Y$ 的 pdf 為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f_{\sssig Y}(y)&=F^{\prime}_{\sssig Y}(y)=f_{\sssig Z}\bigl(\sqrt{y}\bigr)\,\frac{d\sqrt{y}}{d\,y}-f_{\sssig Z}\bigl(-\sqrt{y}\bigr)\,\frac{d\bigl(-\sqrt{y}\bigr)}{d\,y}\\[0.45em]
&=f_{\sssig Z}\bigl(\sqrt{y}\bigr)\,\frac{1}{\,2\sqrt{y}\,}-f_{\sssig Z}\bigl(-\sqrt{y}\bigr)\,\frac{-1}{\,2\sqrt{y}\,}\\[0.45em]
&=\frac{1}{\,\sqrt{2\pi}\,}e^{-\frac{1}{2}\left(\sqrt{y}\right)^{2}}\cdot\frac{1}{\,2\sqrt{y}\,}+\frac{1}{\,\sqrt{2\pi}\,}e^{-\frac{1}{2}\left(-\sqrt{y}\right)^{2}}\cdot\frac{1}{\,2\sqrt{y}\,}\\[0.45em]
&=\frac{1}{\,\sqrt{2\pi y}\,}e^{-\frac{1}{2}y},\quad y>0
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&f_{\sssig Y}(y)=F^{\prime}_{\sssig Y}(y)\\[0.45em]
&=f_{\sssig Z}\bigl(\sqrt{y}\bigr)\,\frac{d\sqrt{y}}{d\,y}-f_{\sssig Z}\bigl(-\sqrt{y}\bigr)\,\frac{d\bigl(-\sqrt{y}\bigr)}{d\,y}\\[0.45em]
&=f_{\sssig Z}\bigl(\sqrt{y}\bigr)\,\frac{1}{\,2\sqrt{y}\,}-f_{\sssig Z}\bigl(-\sqrt{y}\bigr)\,\frac{-1}{\,2\sqrt{y}\,}\\[0.45em]
&=\frac{1}{\,\sqrt{2\pi}\,}e^{-\frac{1}{2}\left(\sqrt{y}\right)^{2}}\cdot\frac{1}{\,2\sqrt{y}\,}\\[0.2em]
&\qquad\qquad +\frac{1}{\,\sqrt{2\pi}\,}e^{-\frac{1}{2}\left(-\sqrt{y}\right)^{2}}\cdot\frac{1}{\,2\sqrt{y}\,}\\[0.45em]
&=\frac{1}{\,\sqrt{2\pi y}\,}e^{-\frac{1}{2}y},\quad y>0
\end{aligned}
$$

</div>

由此可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
Y\sim\mathrm{Gamma}\Bigl(\alpha=\tfrac{1}{2},\beta=2\Bigr)\quad\text{即}\quad Y\sim\chi^{2}(1)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
Y&\sim\mathrm{Gamma}\Bigl(\alpha=\tfrac{1}{2},\beta=2\Bigr)\\[0.45em]
\text{即}\quad Y&\sim\chi^{2}(1)
\end{aligned}
$$

</div>

**[ Jacobian 法 ]**

$Y=Z^{2}\Longrightarrow Z=\pm\sqrt{Y}$，我們分兩種狀況討論。

**[ $Z=\sqrt{Y}\Longleftrightarrow Z\geqslant0$ ]**

$\mathbf{J}=\dfrac{d\,z}{d\,y}=\dfrac{1}{\,2\sqrt{y}\,}$，且由此可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f^{*}_{\sssig Y}(y)&=f_{\sssig Z}\bigl(\sqrt{y}\bigr)\bigl\lvert\mathbf{J}\bigr\rvert=\frac{1}{\,\sqrt{2\pi}\,}e^{-\frac{1}{2}y}\times\biggl\lvert\frac{1}{\,2\sqrt{y}\,}\biggr\rvert\\[0.45em]
&=\frac{1}{\,2\sqrt{2\pi\,y}\,}e^{-\frac{1}{2}y},\quad y>0
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f^{*}_{\sssig Y}(y)&=f_{\sssig Z}\bigl(\sqrt{y}\bigr)\bigl\lvert\mathbf{J}\bigr\rvert\\[0.45em]
&=\frac{1}{\,\sqrt{2\pi}\,}e^{-\frac{1}{2}y}\times\biggl\lvert\frac{1}{\,2\sqrt{y}\,}\biggr\rvert\\[0.45em]
&=\frac{1}{\,2\sqrt{2\pi\,y}\,}e^{-\frac{1}{2}y},\quad y>0
\end{aligned}
$$

</div>

**[ $Z=-\sqrt{Y}\Longleftrightarrow Z<0$ ]**

$\mathbf{J}=\dfrac{d\,z}{d\,y}=\dfrac{-1}{\,2\sqrt{y}\,}$，且由此可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f^{**}_{\sssig Y}(y)&=f_{\sssig Z}\bigl(-\sqrt{y}\bigr)\bigl\lvert\mathbf{J}\bigr\rvert=\frac{1}{\,\sqrt{2\pi}\,}e^{-\frac{1}{2}y}\times\biggl\lvert\frac{-1}{\,2\sqrt{y}\,}\biggr\rvert\\[0.45em]
&=\frac{1}{\,2\sqrt{2\pi\,y}\,}e^{-\frac{1}{2}y},\quad y>0
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f^{**}_{\sssig Y}(y)&=f_{\sssig Z}\bigl(-\sqrt{y}\bigr)\bigl\lvert\mathbf{J}\bigr\rvert\\[0.45em]
&=\frac{1}{\,\sqrt{2\pi}\,}e^{-\frac{1}{2}y}\times\biggl\lvert\frac{-1}{\,2\sqrt{y}\,}\biggr\rvert\\[0.45em]
&=\frac{1}{\,2\sqrt{2\pi\,y}\,}e^{-\frac{1}{2}y},\quad y>0
\end{aligned}
$$

</div>

則由此可知 $Y$ 之 pdf 為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig Y}(y)=f^{*}_{\sssig Y}(y)+f^{**}_{\sssig Y}(y)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{1}{\,\sqrt{2\pi}\,}\,y^{-\frac{1}{2}}\,e^{-\frac{1}{2}y}, & y>0\\[0.9em]
0, & \text{otherwise}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig Y}(y)&=f^{*}_{\sssig Y}(y)+f^{**}_{\sssig Y}(y)\\[0.45em]
&=\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{1}{\,\sqrt{2\pi}\,}\,y^{-\frac{1}{2}}\,e^{-\frac{1}{2}y}, & y>0\\[0.9em]
0, & \text{otherwise}
\end{array}
\right.
\end{aligned}
$$

</div>

由此可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
Y\sim\mathrm{Gamma}\Bigl(\alpha=\tfrac{1}{2},\beta=2\Bigr)\quad\text{即}\quad Y\sim\chi^{2}(1)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
Y&\sim\mathrm{Gamma}\Bigl(\alpha=\tfrac{1}{2},\beta=2\Bigr)\\[0.45em]
\text{即}\quad Y&\sim\chi^{2}(1)
\end{aligned}
$$

</div>

</div>

<div id="ex-laplace-absolute-exponential" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.51</div>

<div lang="en" markdown="1">
Suppose that $X\_{1},\ldots,X\_{n}$ is a random sample from the Laplace distribution whose location parameter is $\mu=0$ and whose scale parameter is $b=1$. Show that $\lvert X\_{1}\rvert,\ldots,\lvert X\_{n}\rvert$ follow an exponential distribution, and determine the value of its rate parameter.
</div>

**[ cdf 法 ]**

由於本題設定 $X\_{1},\ldots,X\_{n}\overset{\mathrm{iid}}{\sim}\mathrm{Laplace}(\mu=0,\ b=1)$，故我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X_i}(x_{i})=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{1}{2}\exp\bigl(-\lvert x_{i}\rvert\bigr), & x_{i}\in\mathbb{R}\\[0.9em]
0, & \text{otherwise}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
f_{\sssig X_i}(x_{i})=
\left\lbrace
\begin{array}{c@{\!\!}l}
\dfrac{1}{2}\exp\bigl(-\lvert x_{i}\rvert\bigr), & x_{i}\in\mathbb{R}\\[0.9em]
0, & \text{otherwise}
\end{array}
\right.
$$

</div>

令 $Y\_{i}=\lvert X\_{i}\rvert$，$i=1,\ldots,n$，則有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
F_{\sssig Y_i}(y_{i})&=\mathbb{P}(Y_{i}\leqslant y_{i})=\mathbb{P}\bigl(\lvert X_{i}\rvert\leqslant y_{i}\bigr)=\mathbb{P}(-y_{i}\leqslant X_{i}\leqslant y_{i})\\[0.45em]
&=\int_{-y_i}^{y_i}\frac{1}{2}\exp\bigl(-\lvert x_{i}\rvert\bigr)\,dx_{i}=2\int_{0}^{y_i}\frac{1}{2}\exp(-x_{i})\,dx_{i}\\[0.45em]
&=\left\lbrace
\begin{array}{c@{\quad}l}
1-\exp(-y_{i}), & y_{i}\geqslant0\\[0.5em]
0, & \text{otherwise}
\end{array}
\right.
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig Y_i}(y_{i})&=\mathbb{P}(Y_{i}\leqslant y_{i})\\[0.45em]
&=\mathbb{P}\bigl(\lvert X_{i}\rvert\leqslant y_{i}\bigr)\\[0.45em]
&=\mathbb{P}(-y_{i}\leqslant X_{i}\leqslant y_{i})\\[0.45em]
&=\int_{-y_i}^{y_i}\frac{1}{2}\exp\bigl(-\lvert x_{i}\rvert\bigr)\,dx_{i}\\[0.45em]
&=2\int_{0}^{y_i}\frac{1}{2}\exp(-x_{i})\,dx_{i}\\[0.45em]
&=\left\lbrace
\begin{array}{c@{}l}
1-\exp(-y_{i}), & y_{i}\geqslant0\\[0.5em]
0, & \text{otherwise}
\end{array}
\right.
\end{aligned}
$$

</div>

則可知 $Y\_{i}$ 的 pdf 為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig Y_i}(y_{i})=\frac{d\,F_{\sssig Y_i}(y_{i})}{d\,y_{i}}=
\left\lbrace
\begin{array}{c@{\quad}l}
\exp(-y_{i}), & y_{i}\geqslant0\\[0.5em]
0, & \text{otherwise}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig Y_i}(y_{i})&=\frac{d\,F_{\sssig Y_i}(y_{i})}{d\,y_{i}}\\[0.45em]
&=\left\lbrace
\begin{array}{c@{}l}
\exp(-y_{i}), & y_{i}\geqslant0\\[0.5em]
0, & \text{otherwise}
\end{array}
\right.
\end{aligned}
$$

</div>

故可知

$$
Y_{i}\overset{\mathrm{iid}}{\sim}\mathrm{Exp}(\lambda=1),\quad i=1,\ldots,n
$$

**[ Jacobian 法 ]**

由於本題設定 $X\_{1},\ldots,X\_{n}\overset{\mathrm{iid}}{\sim}\mathrm{Laplace}(\mu=0,\ b=1)$，故我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X_i}(x_{i})=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{1}{2}\exp\bigl(-\lvert x_{i}\rvert\bigr), & x_{i}\in\mathbb{R}\\[0.9em]
0, & \text{otherwise}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
f_{\sssig X_i}(x_{i})=
\left\lbrace
\begin{array}{c@{\!\!}l}
\dfrac{1}{2}\exp\bigl(-\lvert x_{i}\rvert\bigr), & x_{i}\in\mathbb{R}\\[0.9em]
0, & \text{otherwise}
\end{array}
\right.
$$

</div>

令 $Y\_{i}=\lvert X\_{i}\rvert$，$i=1,\ldots,n$，則我們分成兩個情況討論。

**[ $X\_{i}\geqslant0$ ]**

$Y\_{i}=X\_{i}\Longrightarrow X\_{i}=Y\_{i}$ 且 <span class="text-nowrap">$\mathbf{J}=\dfrac{d\,x\_{i}}{d\,y\_{i}}=1$，</span>則有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f^{*}_{\sssig Y_i}(y_{i})&=f_{\sssig X_i}(y_{i})\bigl\lvert\mathbf{J}\bigr\rvert=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{1}{2}\exp\bigl(-\lvert y_{i}\rvert\bigr), & y_{i}\geqslant0\\[0.9em]
0, & \text{otherwise}
\end{array}
\right.\\[0.9em]
&=\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{1}{2}\exp(-y_{i}), & y_{i}\geqslant0\\[0.9em]
0, & \text{otherwise}
\end{array}
\right.
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f^{*}_{\sssig Y_i}(y_{i})&=f_{\sssig X_i}(y_{i})\bigl\lvert\mathbf{J}\bigr\rvert\\[0.45em]
&=\left\lbrace
\begin{array}{c@{}l}
\dfrac{1}{2}\exp\bigl(-\lvert y_{i}\rvert\bigr), & y_{i}\geqslant0\\[0.9em]
0, & \text{otherwise}
\end{array}
\right.\\[0.9em]
&=\left\lbrace
\begin{array}{c@{}l}
\dfrac{1}{2}\exp(-y_{i}), & y_{i}\geqslant0\\[0.9em]
0, & \text{otherwise}
\end{array}
\right.
\end{aligned}
$$

</div>

**[ $X\_{i}<0$ ]**

$Y\_{i}=-X\_{i}\Longrightarrow X\_{i}=-Y\_{i}$ 且 <span class="text-nowrap">$\mathbf{J}=\dfrac{d\,x\_{i}}{d\,y\_{i}}=-1$，</span>則有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f^{**}_{\sssig Y_i}(y_{i})&=f_{\sssig X_i}(-y_{i})\bigl\lvert\mathbf{J}\bigr\rvert=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{1}{2}\exp\bigl(-\lvert-y_{i}\rvert\bigr), & y_{i}\geqslant0\\[0.9em]
0, & \text{otherwise}
\end{array}
\right.\\[0.9em]
&=\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{1}{2}\exp(-y_{i}), & y_{i}\geqslant0\\[0.9em]
0, & \text{otherwise}
\end{array}
\right.
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f^{**}_{\sssig Y_i}(y_{i})&=f_{\sssig X_i}(-y_{i})\bigl\lvert\mathbf{J}\bigr\rvert\\[0.45em]
&=\left\lbrace
\begin{array}{c@{}l}
\dfrac{1}{2}\exp\bigl(-\lvert-y_{i}\rvert\bigr), & y_{i}\geqslant0\\[0.9em]
0, & \text{otherwise}
\end{array}
\right.\\[0.9em]
&=\left\lbrace
\begin{array}{c@{}l}
\dfrac{1}{2}\exp(-y_{i}),& y_{i}\geqslant0\\[0.9em]
0,& \text{otherwise}
\end{array}
\right.
\end{aligned}
$$

</div>

則由此可知 $Y\_{i}$ 之 pdf 為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig Y_i}(y_{i})=f^{*}_{\sssig Y_i}(y_{i})+f^{**}_{\sssig Y_i}(y_{i})=
\left\lbrace
\begin{array}{c@{\quad}l}
\exp(-y_{i}), & y_{i}\geqslant0\\[0.5em]
0, & \text{otherwise}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig Y_i}(y_{i})&=f^{*}_{\sssig Y_i}(y_{i})+f^{**}_{\sssig Y_i}(y_{i})\\[0.45em]
&=\left\lbrace
\begin{array}{c@{}l}
\exp(-y_{i}),& y_{i}\geqslant0\\[0.5em]
0,& \text{otherwise}
\end{array}
\right.
\end{aligned}
$$

</div>

故可知

$$
Y_{i}\overset{\mathrm{iid}}{\sim}\mathrm{Exp}(\lambda=1),\quad i=1,\ldots,n
$$

</div>

<div id="ex-uniform-square-transformation" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.52</div>

<div lang="en" markdown="1">
Suppose that $X$ has the probability density function

$$
f_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{1}{3}, & -2<x<1\\[0.9em]
0, & \text{elsewhere}
\end{array}
\right.
$$

Determine both the cdf and the pdf of $Y=X^{2}$.
</div>

**[ cdf 法 ]**

由 cdf 之定義可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
F_{\sssig Y}(y)&=\mathbb{P}(Y\leqslant y)=\mathbb{P}\bigl(X^{2}\leqslant y\bigr)\\[0.6em]
&=\left\lbrace
\begin{array}{c@{\quad}l}
0, & y<0\\[0.5em]
\mathbb{P}\bigl(-\sqrt{y}\leqslant X\leqslant\sqrt{y}\bigr), & 0\leqslant y<1\\[0.5em]
\mathbb{P}\bigl(-\sqrt{y}\leqslant X\leqslant1\bigr), & 1\leqslant y<4\\[0.5em]
1, & y\geqslant4
\end{array}
\right.\\[0.6em]
&=\left\lbrace
\begin{array}{c@{\quad}l}
0, & y<0\\[0.5em]
\dfrac{2}{\,3\,}\sqrt{y}, & 0\leqslant y<1\\[0.9em]
\dfrac{1}{\,3\,}\bigl(1+\sqrt{y}\bigr), & 1\leqslant y<4\\[0.9em]
1, & y\geqslant4
\end{array}
\right.
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&F_{\sssig Y}(y)=\mathbb{P}(Y\leqslant y)=\mathbb{P}\bigl(X^{2}\leqslant y\bigr)\\[0.6em]
&=\left\lbrace
\begin{array}{c@{}l}
0, & y<0\\[0.5em]
\mathbb{P}\bigl(-\sqrt{y}\leqslant X\leqslant\sqrt{y}\bigr), & 0\leqslant y<1\\[0.5em]
\mathbb{P}\bigl(-\sqrt{y}\leqslant X\leqslant1\bigr), & 1\leqslant y<4\\[0.5em]
1, & y\geqslant4
\end{array}
\right.\\[0.7em]
&=\left\lbrace
\begin{array}{c@{}l}
0, & y<0\\[0.5em]
\dfrac{2}{\,3\,}\sqrt{y}, & 0\leqslant y<1\\[0.7em]
\dfrac{1}{\,3\,}\bigl(1+\sqrt{y}\bigr), & 1\leqslant y<4\\[0.7em]
1, & y\geqslant4
\end{array}
\right.
\end{aligned}
$$

</div>

則可以得到 pdf 為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig Y}(y)=\frac{\,d\,F_{\sssig Y}(y)\,}{d\,y}=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{1}{\,3\sqrt{y}\,}, & 0<y<1\\[0.9em]
\dfrac{1}{\,6\sqrt{y}\,}, & 1\leqslant y<4\\[0.9em]
0, & \text{otherwise}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig Y}(y)&=\frac{\,d\,F_{\sssig Y}(y)\,}{d\,y}\\[0.45em]
&=\left\lbrace
\begin{array}{c@{}l}
\dfrac{1}{\,3\sqrt{y}\,}, & 0<y<1\\[0.7em]
\dfrac{1}{\,6\sqrt{y}\,}, & 1\leqslant y<4\\[0.7em]
0, & \text{otherwise}
\end{array}
\right.
\end{aligned}
$$

</div>

**[ Jacobian 法 ]**

$Y=X^{2}\Longrightarrow X=\pm\sqrt{Y}$，我們分兩種狀況討論。

**[ $X=\sqrt{Y}\Longleftrightarrow X\geqslant0$ ]**

$\mathbf{J}=\dfrac{d\,x}{d\,y}=\dfrac{1}{\,2\sqrt{y}\,}$，且由此可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f^{*}_{\sssig Y}(y)=f_{\sssig X}\bigl(\sqrt{y}\bigr)\bigl\lvert\mathbf{J}\bigr\rvert=\frac{1}{3}\times\biggl\lvert\frac{1}{\,2\sqrt{y}\,}\biggr\rvert=\frac{1}{\,6\sqrt{y}\,},\quad 0<y<1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f^{*}_{\sssig Y}(y)&=f_{\sssig X}\bigl(\sqrt{y}\bigr)\bigl\lvert\mathbf{J}\bigr\rvert\\[0.45em]
&=\frac{1}{3}\times\biggl\lvert\frac{1}{\,2\sqrt{y}\,}\biggr\rvert\\[0.45em]
&=\frac{1}{\,6\sqrt{y}\,},\quad 0<y<1
\end{aligned}
$$

</div>

**[ $X=-\sqrt{Y}\Longleftrightarrow X<0$ ]**

$\mathbf{J}=\dfrac{d\,x}{d\,y}=\dfrac{-1}{\,2\sqrt{y}\,}$，且由此可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f^{**}_{\sssig Y}(y)=f_{\sssig X}\bigl(-\sqrt{y}\bigr)\bigl\lvert\mathbf{J}\bigr\rvert=\frac{1}{3}\times\biggl\lvert\frac{-1}{\,2\sqrt{y}\,}\biggr\rvert=\frac{1}{\,6\sqrt{y}\,},\quad 0<y<4
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f^{**}_{\sssig Y}(y)&=f_{\sssig X}\bigl(-\sqrt{y}\bigr)\bigl\lvert\mathbf{J}\bigr\rvert\\[0.45em]
&=\frac{1}{3}\times\biggl\lvert\frac{-1}{\,2\sqrt{y}\,}\biggr\rvert\\[0.45em]
&=\frac{1}{\,6\sqrt{y}\,},\quad 0<y<4
\end{aligned}
$$

</div>

則由此可知 $Y$ 之 pdf 為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig Y}(y)=f^{*}_{\sssig Y}(y)+f^{**}_{\sssig Y}(y)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{1}{\,3\sqrt{y}\,}, & 0<y<1\\[0.9em]
\dfrac{1}{\,6\sqrt{y}\,}, & 1\leqslant y<4\\[0.9em]
0, & \text{otherwise}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig Y}(y)&=f^{*}_{\sssig Y}(y)+f^{**}_{\sssig Y}(y)\\[0.45em]
&=\left\lbrace
\begin{array}{c@{}l}
\dfrac{1}{\,3\sqrt{y}\,}, & 0<y<1\\[0.7em]
\dfrac{1}{\,6\sqrt{y}\,}, & 1\leqslant y<4\\[0.7em]
0, & \text{otherwise}
\end{array}
\right.
\end{aligned}
$$

</div>

並可透過此 pdf 得到 cdf 為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
F_{\sssig Y}(y)&=\mathbb{P}(Y\leqslant y)=\int_{-\infty}^{y}f_{\sssig Y}(t)\,dt\\[0.6em]
&=\left\lbrace
\begin{array}{c@{\quad}l}
0, & y<0\\[0.5em]
\displaystyle\int_{0}^{y}\frac{1}{\,3\sqrt{t}\,}\,dt, & 0\leqslant y<1\\[1.1em]
\displaystyle\int_{0}^{1}\frac{1}{\,3\sqrt{t}\,}\,dt+\int_{1}^{y}\frac{1}{\,6\sqrt{t}\,}\,dt, & 1\leqslant y<4\\[1.1em]
1, & y\geqslant4
\end{array}
\right.\\[0.6em]
&=\left\lbrace
\begin{array}{c@{\quad}l}
0, & y<0\\[0.5em]
\dfrac{2}{\,3\,}\sqrt{y}, & 0\leqslant y<1\\[0.9em]
\dfrac{1}{\,3\,}\bigl(1+\sqrt{y}\bigr), & 1\leqslant y<4\\[0.9em]
1, & y\geqslant4
\end{array}
\right.
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&F_{\sssig Y}(y)=\mathbb{P}(Y\leqslant y) =\int_{-\infty}^{y}f_{\sssig Y}(t)\,dt\\[0.6em]
&=\left\lbrace
\begin{array}{c@{}l}
0, & y<0\\[0.5em]
\int_{0}^{y}\!\frac{1}{\,3\sqrt{t}\,}dt, & 0\leqslant y<1\\[1.1em]
\int_{0}^{1}\!\frac{1}{\,3\sqrt{t}\,}dt+\int_{1}^{y}\!\frac{1}{\,6\sqrt{t}\,}dt, & 1\leqslant y<4\\[0.7em]
1, & y\geqslant4
\end{array}
\right.\\[0.7em]
&=\left\lbrace
\begin{array}{c@{}l}
0, & y<0\\[0.5em]
\dfrac{2}{\,3\,}\sqrt{y}, & 0\leqslant y<1\\[0.7em]
\dfrac{1}{\,3\,}\bigl(1+\sqrt{y}\bigr), & 1\leqslant y<4\\[0.7em]
1, & y\geqslant4
\end{array}
\right.
\end{aligned}
$$

</div>

</div>

## 本篇小結

$g(\cdot)$ 不是一對一函數時，反函數並不存在，作法是將原先的隨機變數分段，直到該段中反函數存在，各段分別轉換之後再連接起來。本篇的三道例題都用上了這個作法。[Example 2.50](#ex-chi-square-from-normal) 由標準常態分配的平方得到 $\chi^{2}(1)$，[Example 2.51](#ex-laplace-absolute-exponential) 由拉普拉斯分配的絕對值得到 $\mathrm{Exp}(1)$，[Example 2.52](#ex-uniform-square-transformation) 則由均勻分配在 $(-2,1)$ 上的平方得到一個分成兩段的密度。cdf 法在這三題之中都不必先取反函數，而是直接由 cdf 的定義把 $\lbrace Y\leqslant y\rbrace$ 改寫成 $X$ 的一個事件再求機率；Jacobian 法則是在每一段上各求一個密度 $f^{*}$ 與 $f^{**}$，再把兩者相加。[Example 2.52](#ex-uniform-square-transformation) 最能看出分段的必要。$X$ 的值域 $(-2,1)$ 對原點並不對稱，$Y$ 落在 $[1,4)$ 之間時只有 $X<0$ 那一段有貢獻，密度因而由 $\frac{1}{\,3\sqrt{y}\,}$ 減為 $\frac{1}{\,6\sqrt{y}\,}$，cdf 也隨之分成四段。

第二章到此結束。全章先由樣本空間上的實值函數定出[隨機變數](/lecture-notes/random-variables-and-pmf/)，再以 pmf、[cdf](/lecture-notes/cumulative-distribution-functions/) 與 [pdf](/lecture-notes/probability-density-functions/) 描述它的機率分配，接著[由 cdf 計算各種區間的機率](/lecture-notes/computing-probabilities-from-cdf/)，並處理離散型與連續型兼具的[混合型](/lecture-notes/mixed-random-variables/)。有了分配之後，[期望值](/lecture-notes/expectation/)、[變異數](/lecture-notes/variance/)、[標準差](/lecture-notes/variance-standard-deviation/)、[眾數](/lecture-notes/mode/)、[中位數](/lecture-notes/median/)與[分位數](/lecture-notes/quantiles/)各自摘要分配的一個面向，[函數期望值與期望值的性質](/lecture-notes/properties-of-expectation/)一篇則回頭處理期望值本身，說明 $\mathbb{E}[g(X)]$ 不必先求出 $g(X)$ 的分配，直接由 $X$ 的分配即可算得，期望值對線性函數也具有可交換性；[動差系統](/lecture-notes/moment-system/)把其中幾個量數收進同一套架構之下，[形狀量數](/lecture-notes/measures-of-shape/)則由三階與四階動差刻畫偏斜的方向與尾巴的厚薄。[動差母函數](/lecture-notes/moment-generating-functions/)換了一個角度: 以一個 $t$ 的函數同時生成各階原動差，並在[唯一性](/lecture-notes/uniqueness-of-the-mgf/#thm-mgf-uniqueness)之下反過來認出分配是哪一個；[機率母函數與累積量母函數](/lecture-notes/probability-cumulant-generating-functions/)則一個把工具函數換成 $t^{X}$、一個由 mgf 取對數，分別生成階乘動差與累積量，[特徵函數](/lecture-notes/characteristic-functions/)再把工具函數換成 $e^{itX}$，因而對每一個隨機變數都存在。機率不等式及相關法則一節回到機率本身。[馬可夫、柴比雪夫與坎特利不等式](/lecture-notes/probability-inequalities/)只用一階與二階動差就替尾機率取得上界，[車諾夫不等式](/lecture-notes/probability-inequalities-examples/)改用整個 mgf 而取得更緊的上界，[延森不等式](/lecture-notes/convexity-jensen-inequality/#thm-jensen)所比較的則是 $\mathbb{E}[g(X)]$ 與 $g[\mathbb{E}(X)]$ 兩者的大小，而[鐘形分配經驗法則](/lecture-notes/empirical-rule-bell-shaped-distributions/#thm-empirical-rule)改由分配的形狀直接說出中央區間的機率。最後這兩篇處理函數轉換，回答已知 $X$ 的分配時 $Y=g(X)$ 的分配要怎麼求，[一對一時直接套公式](/lecture-notes/one-to-one-transformations/)，不是一對一時先分段再合併。[下一章](/lecture-notes/random-vectors-joint-pmf/)把討論的對象由一個隨機變數推廣到多個隨機變數所組成的[隨機向量](/lecture-notes/random-vectors-joint-pmf/#def-random-vector)。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
