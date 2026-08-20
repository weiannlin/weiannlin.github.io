---
title: "伽瑪分配與貝塔分配的關係"
subtitle: "The Relationship between the Gamma and Beta Distributions"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 4
topic: 16
order: 416
permalink: /lecture-notes/gamma-beta-relationship/
date: 2026-08-12
published: false
excerpt: "兩個比例參數相同且彼此獨立的伽瑪變數，其中一個在兩者之和中所佔的比例服從貝塔分配，兩者之和則仍為伽瑪分配，而且這兩個新變數彼此獨立。本篇以 Jacobian 法完整證明這個結果: 先寫出兩個伽瑪變數的聯合機率密度函數，換元之後求得新變數的聯合機率密度函數，再分別對另一個變數積分而得到兩個邊際機率密度函數。這個結果背後有一個簡單直接的想法，即比例的平均為 $\\frac{a}{\\,a+b\\,}$，恰好是貝塔分配的期望值；其特例是兩個獨立同分配的指數變數，其比例服從標準均勻分配。最後以三道例題演練，依序處理指數變數的比例與和、標準均勻分配之順序統計量的共變異數與全距，以及三個獨立標準均勻變數的極大值與極小值。"
---

[上一篇](/lecture-notes/beta-function-and-distribution/)由[貝塔函數](/lecture-notes/beta-function-and-distribution/#def-beta-function)出發，給出[貝塔分配](/lecture-notes/beta-function-and-distribution/#def-beta-distribution)的定義。貝塔函數本身就是由兩個[伽瑪函數](/lecture-notes/gamma-function-exponential-distribution/#def-gamma-function)的乘積除以另一個伽瑪函數而來，因此貝塔分配與[伽瑪分配](/lecture-notes/gamma-distribution/#def-gamma-distribution)之間存在一項直接的關係，本篇處理的就是這項關係。

本篇先以 [Jacobian 法](/lecture-notes/many-to-many-transformations/#連續型的-jacobian-法)證明: 兩個比例參數相同且彼此獨立的伽瑪變數，其中一個在兩者之和中所佔的比例服從貝塔分配，兩者之和則仍為伽瑪分配，而且這兩個新變數彼此獨立。接著說明這項關係背後的想法，以及它在[指數分配](/lecture-notes/gamma-function-exponential-distribution/#def-exponential-distribution)上的特例。最後以三道例題作為演練，其中兩道涉及[標準均勻分配](/lecture-notes/uniform-distribution-integral-transform/#def-uniform-distribution)的順序統計量 <span lang="en">(order statistic)</span>。

## 伽瑪分配與貝塔分配的關係

<div id="thm-gamma-to-beta" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 4.19 (獨立伽瑪的比值與和, ratio and sum of independent gamma variables)</div>

令

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
X\sim\mathrm{Gamma}(\alpha=a,\ \beta)\indep Y\sim\mathrm{Gamma}(\alpha=b,\ \beta)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
X&\sim\mathrm{Gamma}(\alpha=a,\ \beta)\\[0.5em]
\indep\ Y&\sim\mathrm{Gamma}(\alpha=b,\ \beta)
\end{aligned}
$$

</div>

若令 $U=\frac{X}{\,X+Y\,}$ 與 <span class="text-nowrap">$V=X+Y$，</span>則我們可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
U\sim\mathrm{Beta}(\alpha=a,\ \beta=b)\indep V\sim\mathrm{Gamma}(\alpha=a+b,\ \beta)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
U&\sim\mathrm{Beta}(\alpha=a,\ \beta=b)\\[0.5em]
\indep\ V&\sim\mathrm{Gamma}(\alpha=a+b,\ \beta)
\end{aligned}
$$

</div>

</div>

<div class="topic-proof" markdown="1">
**Proof.**

由 Jacobian 法可知，令

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
U=\frac{X}{\,X+Y\,},\ V=X+Y\qquad\therefore\, X=UV,\ Y=V(1-U)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
U=\frac{X}{\,X+Y\,},\ V=X+Y\qquad\therefore\, X=UV,\ Y=V(1-U)
$$

</div>

則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f_{\sssig XY}(x,y)&=\frac{1}{\,\beta^{a}\Gamma(a)\,}x^{a-1}e^{-\frac{x}{\beta}}\cdot\frac{1}{\,\beta^{b}\Gamma(b)\,}y^{b-1}e^{-\frac{y}{\beta}}\\[0.45em]
&=\frac{1}{\,\beta^{a+b}\Gamma(a)\Gamma(b)\,}x^{a-1}y^{b-1}e^{-\frac{x+y}{\beta}},\ x>0,y>0
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&f_{\sssig XY}(x,y)\\[0.45em]
&=\frac{1}{\,\beta^{a}\Gamma(a)\,}x^{a-1}e^{-\frac{x}{\beta}}\cdot\frac{1}{\,\beta^{b}\Gamma(b)\,}y^{b-1}e^{-\frac{y}{\beta}}\\[0.45em]
&=\frac{1}{\,\beta^{a+b}\Gamma(a)\Gamma(b)\,}x^{a-1}y^{b-1}e^{-\frac{x+y}{\beta}},\\[0.25em]
&\qquad\qquad x>0,y>0
\end{aligned}
$$

</div>

又

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
J=
\left\lvert
\begin{array}{cc}
\dfrac{\partial x}{\partial u} & \dfrac{\partial x}{\partial v}\\[0.8em]
\dfrac{\partial y}{\partial u} & \dfrac{\partial y}{\partial v}
\end{array}
\right\rvert=
\left\lvert
\begin{array}{cc}
\dfrac{\partial (uv)}{\partial u} & \dfrac{\partial (uv)}{\partial v}\\[0.8em]
\dfrac{\partial v(1-u)}{\partial u} & \dfrac{\partial v(1-u)}{\partial v}
\end{array}
\right\rvert=
\left\lvert
\begin{array}{cc}
v & u\\[0.5em]
-v & 1-u
\end{array}
\right\rvert=v
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
J&=
\left\lvert
\begin{array}{cc}
\dfrac{\partial x}{\partial u} & \dfrac{\partial x}{\partial v}\\[0.8em]
\dfrac{\partial y}{\partial u} & \dfrac{\partial y}{\partial v}
\end{array}
\right\rvert\\[0.6em]
&=
\left\lvert
\begin{array}{cc}
\dfrac{\partial (uv)}{\partial u} & \dfrac{\partial (uv)}{\partial v}\\[0.8em]
\dfrac{\partial v(1-u)}{\partial u} & \dfrac{\partial v(1-u)}{\partial v}
\end{array}
\right\rvert\\[0.6em]
&=
\left\lvert
\begin{array}{cc}
v & u\\[0.5em]
-v & 1-u
\end{array}
\right\rvert=v
\end{aligned}
$$

</div>

則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f_{\sssig UV}(u,v)&=f_{\sssig XY}\bigl(uv,\ v(1-u)\bigr)\lvert J\rvert\\[0.45em]
&=\frac{1}{\,\beta^{a+b}\Gamma(a)\Gamma(b)\,}(uv)^{a-1}\bigl[v(1-u)\bigr]^{b-1}e^{-\frac{v}{\beta}}\lvert v\rvert\\[0.45em]
&=\frac{1}{\,\beta^{a+b}\Gamma(a)\Gamma(b)\,}u^{a-1}(1-u)^{b-1}v^{a+b-1}e^{-\frac{v}{\beta}},\ 0<u<1,v>0
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig UV}(u,v)&=f_{\sssig XY}\bigl(uv,\ v(1-u)\bigr)\lvert J\rvert\\[0.45em]
&=\frac{1}{\,\beta^{a+b}\Gamma(a)\Gamma(b)\,}(uv)^{a-1}\\[0.25em]
&\qquad\bigl[v(1-u)\bigr]^{b-1}e^{-\frac{v}{\beta}}\lvert v\rvert\\[0.45em]
&=\frac{1}{\,\beta^{a+b}\Gamma(a)\Gamma(b)\,}u^{a-1}(1-u)^{b-1}\\[0.25em]
&\qquad v^{a+b-1}e^{-\frac{v}{\beta}},\ 0<u<1,v>0
\end{aligned}
$$

</div>

由此可知 $U=\frac{X}{\,X+Y\,}$ 與 $V=X+Y$ 的邊際 pdf 分別為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f_{\sssig U}(u)&=\int_{0}^{\infty}\frac{1}{\,\beta^{a+b}\Gamma(a)\Gamma(b)\,}u^{a-1}(1-u)^{b-1}v^{a+b-1}e^{-\frac{v}{\beta}}\,dv\\[0.45em]
&=\frac{1}{\,\beta^{a+b}\Gamma(a)\Gamma(b)\,}u^{a-1}(1-u)^{b-1}\int_{0}^{\infty}v^{a+b-1}e^{-\frac{v}{\beta}}\,dv\\[0.45em]
&=\frac{1}{\,\beta^{a+b}\Gamma(a)\Gamma(b)\,}u^{a-1}(1-u)^{b-1}\cdot\beta^{a+b}\Gamma(a+b)\\[0.45em]
&=\frac{\Gamma(a+b)}{\,\Gamma(a)\Gamma(b)\,}u^{a-1}(1-u)^{b-1},\ 0<u<1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig U}(u)&=\int_{0}^{\infty}\frac{1}{\,\beta^{a+b}\Gamma(a)\Gamma(b)\,}u^{a-1}(1-u)^{b-1}\\[0.25em]
&\qquad v^{a+b-1}e^{-\frac{v}{\beta}}\,dv\\[0.45em]
&=\frac{1}{\,\beta^{a+b}\Gamma(a)\Gamma(b)\,}u^{a-1}(1-u)^{b-1}\\[0.25em]
&\qquad\int_{0}^{\infty}v^{a+b-1}e^{-\frac{v}{\beta}}\,dv\\[0.45em]
&=\frac{1}{\,\beta^{a+b}\Gamma(a)\Gamma(b)\,}u^{a-1}(1-u)^{b-1}\\[0.25em]
&\qquad\cdot\beta^{a+b}\Gamma(a+b)\\[0.45em]
&=\frac{\Gamma(a+b)}{\,\Gamma(a)\Gamma(b)\,}u^{a-1}(1-u)^{b-1},\ 0<u<1
\end{aligned}
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f_{\sssig V}(v)&=\int_{0}^{1}\frac{1}{\,\beta^{a+b}\Gamma(a)\Gamma(b)\,}u^{a-1}(1-u)^{b-1}v^{a+b-1}e^{-\frac{v}{\beta}}\,du\\[0.45em]
&=\frac{1}{\,\beta^{a+b}\Gamma(a+b)\,}v^{a+b-1}e^{-\frac{v}{\beta}}\int_{0}^{1}\frac{\Gamma(a+b)}{\,\Gamma(a)\Gamma(b)\,}u^{a-1}(1-u)^{b-1}\,du\\[0.45em]
&=\frac{1}{\,\beta^{a+b}\Gamma(a+b)\,}v^{a+b-1}e^{-\frac{v}{\beta}},\ v>0
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig V}(v)&=\int_{0}^{1}\frac{1}{\,\beta^{a+b}\Gamma(a)\Gamma(b)\,}u^{a-1}(1-u)^{b-1}\\[0.25em]
&\qquad v^{a+b-1}e^{-\frac{v}{\beta}}\,du\\[0.45em]
&=\frac{1}{\,\beta^{a+b}\Gamma(a+b)\,}v^{a+b-1}e^{-\frac{v}{\beta}}\\[0.25em]
&\qquad\int_{0}^{1}\frac{\Gamma(a+b)}{\,\Gamma(a)\Gamma(b)\,}u^{a-1}(1-u)^{b-1}\,du\\[0.45em]
&=\frac{1}{\,\beta^{a+b}\Gamma(a+b)\,}v^{a+b-1}e^{-\frac{v}{\beta}},\ v>0
\end{aligned}
$$

</div>

此即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
U\sim\mathrm{Beta}(\alpha=a,\ \beta=b)\indep V\sim\mathrm{Gamma}(\alpha=a+b,\ \beta)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
U&\sim\mathrm{Beta}(\alpha=a,\ \beta=b)\\[0.5em]
\indep\ V&\sim\mathrm{Gamma}(\alpha=a+b,\ \beta)
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個性質背後有一個稍不嚴謹但卻簡單直接的想法，即 $U=\frac{X}{\,X+Y\,}$ 是 $X$ 在 $X+Y$ 間的比例，平均而言，這個比例會是 $X$ 的期望值在 $X+Y$ 的期望值之間的比例，即 $\frac{a\beta}{\,a\beta+b\beta\,}=\frac{a}{\,a+b\,}$ 這個比值，恰好被 $\mathrm{Beta}(a,\ b)$ 分配描述出來。

此外，這個性質也有一個特例，即若

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
X\sim\mathrm{Exp}(\beta)\indep Y\sim\mathrm{Exp}(\beta)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
X&\sim\mathrm{Exp}(\beta)\\[0.5em]
\indep\ Y&\sim\mathrm{Exp}(\beta)
\end{aligned}
$$

</div>

則

$$
U=\frac{X}{\,X+Y\,}\sim\mathcal{U}(0,1)
$$

</div>

## 伽瑪分配與貝塔分配的例題

<div id="ex-gamma-beta-1" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.41</div>

<div lang="en" markdown="1">
Suppose that $X_1$ and $X_2$ are independent and identically distributed random variables whose common probability density function is $f(x)=\frac{e^{-kx}}{\,k!\,}$ for <span class="text-nowrap">$x>0$.</span>

<ol class="topic-list-paren">
  <li>Determine the value of $k$ for which $f$ is a probability density function.</li>
  <li>Find the joint probability density function of $X_1$ and <span class="text-nowrap">$X_2$.</span></li>
  <li>Let $Y_1=X_1+X_2$ and <span class="text-nowrap">$Y_2=\frac{X_1}{\,X_1+X_2\,}$.</span> Find the joint probability density function of $Y_1$ and <span class="text-nowrap">$Y_2$.</span></li>
  <li>Find the marginal probability density function of $Y_1$ and that of <span class="text-nowrap">$Y_2$.</span></li>
  <li>Determine whether $Y_1$ and $Y_2$ are independent.</li>
</ol>
</div>

(1) 由 [pdf 的性質](/lecture-notes/probability-density-functions/#thm-pdf-properties)檢查可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
1&=\int_{0}^{\infty}\frac{e^{-kx}}{\,k!\,}\,dx=\left[\frac{e^{-kx}}{\,(-k)\cdot k!\,}\right]_{0}^{\infty}=-\frac{1}{\,(-k)\cdot k!\,}\qquad\therefore\, k=1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
1&=\int_{0}^{\infty}\frac{e^{-kx}}{\,k!\,}\,dx=\left[\frac{e^{-kx}}{\,(-k)\cdot k!\,}\right]_{0}^{\infty}\\[0.45em]
&=-\frac{1}{\,(-k)\cdot k!\,}\qquad\therefore\, k=1
\end{aligned}
$$

</div>

(2) 由上題結果可知
{: .topic-paren-item}

$$
X_1,X_2\overset{\mathrm{iid}}{\sim}\mathrm{Exp}(\beta=1)
$$

則
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X_1X_2}(x_1,x_2)=f_{\sssig X_1}(x_1)f_{\sssig X_2}(x_2)=e^{-x_1}e^{-x_2}=e^{-(x_1+x_2)},\ x_1>0,x_2>0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig X_1X_2}(x_1,x_2)&=f_{\sssig X_1}(x_1)f_{\sssig X_2}(x_2)\\[0.45em]
&=e^{-x_1}e^{-x_2}=e^{-(x_1+x_2)},\\[0.25em]
&\qquad\qquad x_1>0,x_2>0
\end{aligned}
$$

</div>

(3) 由本小題所給的轉換可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
Y_1=X_1+X_2,\ Y_2=\frac{X_1}{\,X_1+X_2\,}\qquad\therefore\, X_1=Y_1Y_2,\ X_2=Y_1(1-Y_2)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
Y_1=X_1+X_2,\ Y_2=\frac{X_1}{\,X_1+X_2\,}\qquad\therefore\, X_1=Y_1Y_2,\ X_2=Y_1(1-Y_2)
$$

</div>

則由 Jacobian 法可得
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbf{J}=
\left\lvert
\begin{array}{cc}
\dfrac{\partial x_1}{\partial y_1} & \dfrac{\partial x_1}{\partial y_2}\\[0.8em]
\dfrac{\partial x_2}{\partial y_1} & \dfrac{\partial x_2}{\partial y_2}
\end{array}
\right\rvert=
\left\lvert
\begin{array}{cc}
\dfrac{\partial (y_1y_2)}{\partial y_1} & \dfrac{\partial (y_1y_2)}{\partial y_2}\\[0.8em]
\dfrac{\partial y_1(1-y_2)}{\partial y_1} & \dfrac{\partial y_1(1-y_2)}{\partial y_2}
\end{array}
\right\rvert=
\left\lvert
\begin{array}{cc}
y_2 & y_1\\[0.5em]
1-y_2 & -y_1
\end{array}
\right\rvert=-y_1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbf{J}&=
\left\lvert
\begin{array}{cc}
\dfrac{\partial x_1}{\partial y_1} & \dfrac{\partial x_1}{\partial y_2}\\[0.8em]
\dfrac{\partial x_2}{\partial y_1} & \dfrac{\partial x_2}{\partial y_2}
\end{array}
\right\rvert\\[0.6em]
&=
\left\lvert
\begin{array}{cc}
\dfrac{\partial (y_1y_2)}{\partial y_1} & \dfrac{\partial (y_1y_2)}{\partial y_2}\\[0.8em]
\dfrac{\partial y_1(1-y_2)}{\partial y_1} & \dfrac{\partial y_1(1-y_2)}{\partial y_2}
\end{array}
\right\rvert\\[0.6em]
&=
\left\lvert
\begin{array}{cc}
y_2 & y_1\\[0.5em]
1-y_2 & -y_1
\end{array}
\right\rvert=-y_1
\end{aligned}
$$

</div>

此即
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f_{\sssig Y_1Y_2}(y_1,y_2)&=f_{\sssig X_1X_2}\bigl(y_1y_2,\ y_1(1-y_2)\bigr)\lvert\mathbf{J}\rvert\\[0.45em]
&=e^{-y_1}\lvert-y_1\rvert=y_1e^{-y_1},\ y_1>0,0<y_2<1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig Y_1Y_2}(y_1,y_2)&=f_{\sssig X_1X_2}\bigl(y_1y_2,\ y_1(1-y_2)\bigr)\lvert\mathbf{J}\rvert\\[0.45em]
&=e^{-y_1}\lvert-y_1\rvert=y_1e^{-y_1},\\[0.25em]
&\qquad\qquad y_1>0,0<y_2<1
\end{aligned}
$$

</div>

(4) 由 [marginal pdf 的定義](/lecture-notes/marginal-probability-density-functions/#def-marginal-pdf)可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig Y_1}(y_1)=\int_{0}^{1}y_1e^{-y_1}\,dy_2=\Bigl[y_1e^{-y_1}y_2\Bigr]_{0}^{1}=y_1e^{-y_1},\ y_1>0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig Y_1}(y_1)&=\int_{0}^{1}y_1e^{-y_1}\,dy_2=\Bigl[y_1e^{-y_1}y_2\Bigr]_{0}^{1}\\[0.45em]
&=y_1e^{-y_1},\ y_1>0
\end{aligned}
$$

</div>

此即
{: .topic-paren-cont}

$$
Y_1\sim\mathrm{Gamma}(\alpha=2,\ \beta=1)
$$

又
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig Y_2}(y_2)=\int_{0}^{\infty}y_1e^{-y_1}\,dy_1=\int_{0}^{\infty}y_1^{2-1}e^{-\frac{y_1}{1}}\,dy_1=1^{2}\Gamma(2)=1,\ 0<y_2<1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig Y_2}(y_2)&=\int_{0}^{\infty}y_1e^{-y_1}\,dy_1\\[0.45em]
&=\int_{0}^{\infty}y_1^{2-1}e^{-\frac{y_1}{1}}\,dy_1\\[0.45em]
&=1^{2}\Gamma(2)=1,\ 0<y_2<1
\end{aligned}
$$

</div>

此即
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
Y_2\sim\mathrm{Beta}(\alpha=1,\ \beta=1)\ \text{或}\ Y_2\sim\mathcal{U}(0,1)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
Y_2&\sim\mathrm{Beta}(\alpha=1,\ \beta=1)\\[0.5em]
\text{或}\ Y_2&\sim\mathcal{U}(0,1)
\end{aligned}
$$

</div>

(5) 因為下列等式成立
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig Y_1Y_2}(y_1,y_2)=f_{\sssig Y_1}(y_1)f_{\sssig Y_2}(y_2)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&f_{\sssig Y_1Y_2}(y_1,y_2)\\[0.5em]
&=f_{\sssig Y_1}(y_1)f_{\sssig Y_2}(y_2)
\end{aligned}
$$

</div>

且範圍並不互相影響，故可知 <span class="text-nowrap">$Y_1\indep Y_2$。</span>
{: .topic-paren-cont}

</div>

<div id="ex-gamma-beta-2" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.42</div>

<div lang="en" markdown="1">
Suppose that $Y_1,\ldots,Y_n$ are independent and identically distributed random variables, each having the $\mathcal{U}(0,1)$ distribution, and let

$$
Y_{\sssig (1)}\leqslant Y_{\sssig (2)}\leqslant\cdots\leqslant Y_{\sssig (n)}
$$

denote the associated order statistics.

<ol class="topic-list-paren">
  <li>Find <span class="text-nowrap">$\mathrm{Cov}\bigl(Y_{\sssig (r)},Y_{\sssig (s)}\bigr)$,</span> where <span class="text-nowrap">$1\leqslant r<s\leqslant n$.</span></li>
  <li>Let <span class="text-nowrap">$R=Y_{\sssig (n)}-Y_{\sssig (1)}$.</span> Evaluate <span class="text-nowrap">$\mathrm{Var}(R)$.</span></li>
  <li>Suppose further that $X_1,X_2,\ldots,X_n$ are independent and identically distributed $\mathrm{Weibull}(\lambda,\ \alpha)$ random variables, the cumulative distribution function of which is $G(x)=1-e^{-(\lambda x)^{\alpha}}$ for <span class="text-nowrap">$x>0$,</span> $\lambda>0$ and <span class="text-nowrap">$\alpha>0$,</span> and let <span class="text-nowrap">$Z=\max\bigl[G(X_i)\bigr]-\min\bigl[G(X_i)\bigr]$.</span> Evaluate $\mathbb{E}(Z)$ and <span class="text-nowrap">$\mathrm{Var}(Z)$.</span></li>
</ol>
</div>

(1) 由[順序統計量](/lecture-notes/order-statistics-distributions/#thm-order-stat-samp-dist-pdf)，我們可知 $Y_{\sssig (r)}$ 與 $Y_{\sssig (s)}$ 之 joint pdf 為
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f_{Y_{\sssig (r)}Y_{\sssig (s)}}(u,v)&=\frac{n!}{\,(r-1)!(s-r-1)!(n-s)!\,}f_{\sssig Y}(u)f_{\sssig Y}(v)\\[0.45em]
&\quad \times\bigl[F_{\sssig Y}(u)\bigr]^{r-1}\bigl[F_{\sssig Y}(v)-F_{\sssig Y}(u)\bigr]^{s-r-1}\bigl[1-F_{\sssig Y}(v)\bigr]^{n-s},\\[0.25em]
&\qquad\qquad 0<u\leqslant v<1\\[0.45em]
&=\frac{n!}{\,(r-1)!(s-r-1)!(n-s)!\,}u^{r-1}(v-u)^{s-r-1}(1-v)^{n-s},\\[0.25em]
&\qquad\qquad 0<u\leqslant v<1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{Y_{\sssig (r)}Y_{\sssig (s)}}(u,v)&=\frac{n!}{\,(r-1)!(s-r-1)!(n-s)!\,}\\[0.25em]
&\qquad f_{\sssig Y}(u)f_{\sssig Y}(v)\\[0.25em]
&\qquad\times\bigl[F_{\sssig Y}(u)\bigr]^{r-1}\bigl[F_{\sssig Y}(v)-F_{\sssig Y}(u)\bigr]^{s-r-1}\\[0.25em]
&\qquad\bigl[1-F_{\sssig Y}(v)\bigr]^{n-s},\\[0.25em]
&\qquad\qquad 0<u\leqslant v<1\\[0.45em]
&=\frac{n!}{\,(r-1)!(s-r-1)!(n-s)!\,}\\[0.25em]
&\qquad u^{r-1}(v-u)^{s-r-1}(1-v)^{n-s},\\[0.25em]
&\qquad\qquad 0<u\leqslant v<1
\end{aligned}
$$

</div>

由此可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\mathbb{E}\bigl(Y_{\sssig (r)}Y_{\sssig (s)}\bigr)=\int_{0}^{1}\int_{0}^{v}uv\,f_{Y_{\sssig (r)}Y_{\sssig (s)}}(u,v)\,du\,dv=\frac{\,(s+1)r\,}{\,(n+2)(n+1)\,}\\[0.7em]
\mathbb{E}\bigl(Y_{\sssig (r)}\bigr)=\int_{0}^{1}\int_{0}^{v}u\,f_{Y_{\sssig (r)}Y_{\sssig (s)}}(u,v)\,du\,dv=\frac{r}{\,n+1\,}\\[0.7em]
\mathbb{E}\bigl(Y_{\sssig (s)}\bigr)=\int_{0}^{1}\int_{0}^{v}v\,f_{Y_{\sssig (r)}Y_{\sssig (s)}}(u,v)\,du\,dv=\frac{s}{\,n+1\,}\\[0.7em]
\mathrm{Cov}\bigl(Y_{\sssig (r)},Y_{\sssig (s)}\bigr)=\mathbb{E}\bigl(Y_{\sssig (r)}Y_{\sssig (s)}\bigr)-\mathbb{E}\bigl(Y_{\sssig (r)}\bigr)\mathbb{E}\bigl(Y_{\sssig (s)}\bigr)\\[0.3em]
=\frac{r(n+1-s)}{\,(n+1)^2(n+2)\,},\ 1\leqslant r<s\leqslant n
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl(Y_{\sssig (r)}Y_{\sssig (s)}\bigr)&=\int_{0}^{1}\int_{0}^{v}uv\,f_{Y_{\sssig (r)}Y_{\sssig (s)}}(u,v)\,du\,dv\\[0.25em]
&=\frac{\,(s+1)r\,}{\,(n+2)(n+1)\,}\\[0.7em]
\mathbb{E}\bigl(Y_{\sssig (r)}\bigr)&=\int_{0}^{1}\int_{0}^{v}u\,f_{Y_{\sssig (r)}Y_{\sssig (s)}}(u,v)\,du\,dv\\[0.25em]
&=\frac{r}{\,n+1\,}\\[0.7em]
\mathbb{E}\bigl(Y_{\sssig (s)}\bigr)&=\int_{0}^{1}\int_{0}^{v}v\,f_{Y_{\sssig (r)}Y_{\sssig (s)}}(u,v)\,du\,dv\\[0.25em]
&=\frac{s}{\,n+1\,}\\[0.7em]
\mathrm{Cov}\bigl(&Y_{\sssig (r)},Y_{\sssig (s)}\bigr)\\[0.25em]
&=\mathbb{E}\bigl(Y_{\sssig (r)}Y_{\sssig (s)}\bigr)-\mathbb{E}\bigl(Y_{\sssig (r)}\bigr)\mathbb{E}\bigl(Y_{\sssig (s)}\bigr)\\[0.25em]
&=\frac{r(n+1-s)}{\,(n+1)^2(n+2)\,},\\[0.25em]
&\qquad\qquad 1\leqslant r<s\leqslant n
\end{aligned}
$$

</div>

(2) 令 $R=Y_{\sssig (n)}-Y_{\sssig (1)}$ 與 <span class="text-nowrap">$T=Y_{\sssig (1)}$，</span>則 $Y_{\sssig (1)}=T$ 與 <span class="text-nowrap">$Y_{\sssig (n)}=R+T$，</span>由 Jacobian 法可得
{: .topic-paren-item}

$$
\mathbf{J}=
\left\lvert
\begin{array}{cc}
\dfrac{\partial y_{\sssig (1)}}{\partial r} & \dfrac{\partial y_{\sssig (1)}}{\partial t}\\[0.8em]
\dfrac{\partial y_{\sssig (n)}}{\partial r} & \dfrac{\partial y_{\sssig (n)}}{\partial t}
\end{array}
\right\rvert=1
$$

則
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig RT}(r,t)=f_{\sssig Y_{\sssig (1)}Y_{\sssig (n)}}(t,\ r+t)\lvert\mathbf{J}\rvert=\frac{n!}{\,(n-2)!\,}r^{n-2},\ 0<t\leqslant r+t<1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig RT}(r,t)&=f_{\sssig Y_{\sssig (1)}Y_{\sssig (n)}}(t,\ r+t)\lvert\mathbf{J}\rvert\\[0.45em]
&=\frac{n!}{\,(n-2)!\,}r^{n-2},\ 0<t\leqslant r+t<1
\end{aligned}
$$

</div>

此即
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig R}(r)=\int_{0}^{1-r}f_{\sssig RT}(r,t)\,dt=\frac{n!}{\,(n-2)!\,}r^{n-2}(1-r),\ 0<r<1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig R}(r)&=\int_{0}^{1-r}f_{\sssig RT}(r,t)\,dt\\[0.45em]
&=\frac{n!}{\,(n-2)!\,}r^{n-2}(1-r),\ 0<r<1
\end{aligned}
$$

</div>

因此
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
R=Y_{\sssig (n)}-Y_{\sssig (1)}\sim\mathrm{Beta}(\alpha=n-1,\ \beta=2),\quad \mathrm{Var}(R)=\frac{2(n-1)}{\,(n+1)^2(n+2)\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
R&=Y_{\sssig (n)}-Y_{\sssig (1)}\\[0.5em]
&\sim\mathrm{Beta}(\alpha=n-1,\ \beta=2),\\[0.5em]
\mathrm{Var}(R)&=\frac{2(n-1)}{\,(n+1)^2(n+2)\,}
\end{aligned}
$$

</div>

(3) 經由[機率積分轉換](/lecture-notes/uniform-distribution-integral-transform/#thm-p-i-t)可知
{: .topic-paren-item}

$$
G(X_i)\overset{\mathrm{iid}}{\sim}\mathcal{U}(0,1),\ i=1,2,\ldots,n
$$

故事實上
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
Z=\max\bigl[G(X_i)\bigr]-\min\bigl[G(X_i)\bigr]\sim\mathrm{Beta}(\alpha=n-1,\ \beta=2)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
Z&=\max\bigl[G(X_i)\bigr]-\min\bigl[G(X_i)\bigr]\\[0.5em]
&\sim\mathrm{Beta}(\alpha=n-1,\ \beta=2)
\end{aligned}
$$

</div>

因此
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(Z)=\frac{n-1}{\,n+1\,},\quad \mathrm{Var}(Z)=\frac{2(n-1)}{\,(n+1)^2(n+2)\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(Z)&=\frac{n-1}{\,n+1\,},\\[0.5em]
\mathrm{Var}(Z)&=\frac{2(n-1)}{\,(n+1)^2(n+2)\,}
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

事實上，這個問題並不需要如此繁複的做法，我們可以利用[順序統計量的性質](/lecture-notes/order-statistics-distributions/#標準均勻分配的順序統計量與貝塔分配)來處理這個問題，作法如下:

由下列事實

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
Y_{\sssig (s)}-Y_{\sssig (r)}\sim\mathrm{Beta}(\alpha=s-r,\ \beta=n-s+r+1)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&Y_{\sssig (s)}-Y_{\sssig (r)}\\[0.5em]
&\sim\mathrm{Beta}(\alpha=s-r,\ \beta=n-s+r+1)
\end{aligned}
$$

</div>

可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}\bigl(Y_{\sssig (s)}-Y_{\sssig (r)}\bigr)=\frac{\,(s-r)(n-s+r+1)\,}{\,(n+1)^2(n+2)\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathrm{Var}\bigl(Y_{\sssig (s)}-Y_{\sssig (r)}\bigr)\\[0.5em]
&=\frac{\,(s-r)(n-s+r+1)\,}{\,(n+1)^2(n+2)\,}
\end{aligned}
$$

</div>

又由於

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
Y_{\sssig (s)}\sim\mathrm{Beta}(\alpha=s,\ \beta=n-s+1),\quad Y_{\sssig (r)}\sim\mathrm{Beta}(\alpha=r,\ \beta=n-r+1)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
Y_{\sssig (s)}&\sim\mathrm{Beta}(\alpha=s,\ \beta=n-s+1),\\[0.5em]
Y_{\sssig (r)}&\sim\mathrm{Beta}(\alpha=r,\ \beta=n-r+1)
\end{aligned}
$$

</div>

我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}\bigl(Y_{\sssig (s)}\bigr)=\frac{\,s(n-s+1)\,}{(n+1)^2(n+2)},\quad \mathrm{Var}\bigl(Y_{\sssig (r)}\bigr)=\frac{\,r(n-r+1)\,}{(n+1)^2(n+2)}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}\bigl(Y_{\sssig (s)}\bigr)&=\frac{\,s(n-s+1)\,}{(n+1)^2(n+2)},\\[0.5em]
\mathrm{Var}\bigl(Y_{\sssig (r)}\bigr)&=\frac{\,r(n-r+1)\,}{(n+1)^2(n+2)}
\end{aligned}
$$

</div>

搭配

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}\bigl(Y_{\sssig (s)}-Y_{\sssig (r)}\bigr)=\mathrm{Var}\bigl(Y_{\sssig (s)}\bigr)+\mathrm{Var}\bigl(Y_{\sssig (r)}\bigr)-2\,\mathrm{Cov}\bigl(Y_{\sssig (s)},Y_{\sssig (r)}\bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}\bigl(Y_{\sssig (s)}-Y_{\sssig (r)}\bigr)&=\mathrm{Var}\bigl(Y_{\sssig (s)}\bigr)+\mathrm{Var}\bigl(Y_{\sssig (r)}\bigr)\\[0.25em]
&\qquad-2\,\mathrm{Cov}\bigl(Y_{\sssig (s)},Y_{\sssig (r)}\bigr)
\end{aligned}
$$

</div>

即可反解共變異數。

</div>

<div id="ex-gamma-beta-3" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.43</div>

<div lang="en" markdown="1">
Suppose that $X_1,X_2,X_3$ are independent random variables, each having the $\mathcal{U}(0,1)$ distribution. Let $Y_1$ denote the smallest and $Y_3$ the largest among <span class="text-nowrap">$X_1,X_2,X_3$.</span>

<ol class="topic-list-paren">
  <li>Find the probability density function of <span class="text-nowrap">$Y_3-Y_1$.</span></li>
  <li>Evaluate $\mathbb{E}\left[\frac{1}{\,2\,}(Y_1+Y_3)\right]$ and <span class="text-nowrap">$\mathrm{Var}\left[\frac{1}{\,2\,}(Y_1+Y_3)\right]$.</span></li>
</ol>
</div>

(1) 由[順序統計量的性質](/lecture-notes/order-statistics-distributions/#標準均勻分配的順序統計量與貝塔分配)可知
{: .topic-paren-item}

$$
Y_3-Y_1\sim\mathrm{Beta}(\alpha=2,\ \beta=2)
$$

因此
{: .topic-paren-cont}

$$
f_{\sssig Y_3-Y_1}(y)=6y(1-y),\ 0<y<1
$$

(2) 由 $Y_1\sim\mathrm{Beta}(\alpha=1,\ \beta=3)$ 與 $Y_3\sim\mathrm{Beta}(\alpha=3,\ \beta=1)$ 可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\left[\frac{1}{\,2\,}(Y_1+Y_3)\right]=\frac{1}{\,2\,}\mathbb{E}(Y_1)+\frac{1}{\,2\,}\mathbb{E}(Y_3)=\frac{1}{\,2\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\left[\frac{1}{\,2\,}(Y_1+Y_3)\right]&=\frac{1}{\,2\,}\mathbb{E}(Y_1)+\frac{1}{\,2\,}\mathbb{E}(Y_3)=\frac{1}{\,2\,}
\end{aligned}
$$

</div>

且
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}\left[\frac{1}{\,2\,}(Y_1+Y_3)\right]=\frac{1}{\,4\,}\mathrm{Var}(Y_1)+\frac{1}{\,4\,}\mathrm{Var}(Y_3)+\frac{2}{\,2\times 2\,}\mathrm{Cov}(Y_1,Y_3)=\frac{1}{\,40\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathrm{Var}\left[\frac{1}{\,2\,}(Y_1+Y_3)\right]\\[0.45em]
&=\frac{1}{\,4\,}\mathrm{Var}(Y_1)+\frac{1}{\,4\,}\mathrm{Var}(Y_3)\\[0.25em]
&\qquad+\frac{2}{\,2\times 2\,}\mathrm{Cov}(Y_1,Y_3)\\[0.45em]
&=\frac{1}{\,40\,}
\end{aligned}
$$

</div>

其中
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\mathrm{Var}(Y_1)=\frac{1\times 3}{\,(1+3)^2(1+3+1)\,}=\frac{3}{\,80\,},\quad \mathrm{Var}(Y_3)=\frac{3\times 1}{\,(3+1)^2(3+1+1)\,}=\frac{3}{\,80\,}\\[0.7em]
\mathrm{Cov}(Y_1,Y_3)=\frac{1(3+1-3)}{\,(3+1)^2(3+2)\,}=\frac{1}{\,80\,}
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(Y_1)&=\frac{1\times 3}{\,(1+3)^2(1+3+1)\,}=\frac{3}{\,80\,},\\[0.5em]
\mathrm{Var}(Y_3)&=\frac{3\times 1}{\,(3+1)^2(3+1+1)\,}=\frac{3}{\,80\,}\\[0.5em]
\mathrm{Cov}(Y_1,Y_3)&=\frac{1(3+1-3)}{\,(3+1)^2(3+2)\,}=\frac{1}{\,80\,}
\end{aligned}
$$

</div>

</div>

## 本篇小結

[Theorem 4.19](#thm-gamma-to-beta) 把[伽瑪分配](/lecture-notes/gamma-distribution/#def-gamma-distribution)與[貝塔分配](/lecture-notes/beta-function-and-distribution/#def-beta-distribution)接了起來: 兩個比例參數同為 $\beta$ 而形狀參數分別為 $a$ 與 $b$ 的獨立伽瑪變數，其中一個在兩者之和中所佔的比例 $U=\frac{X}{\,X+Y\,}$ 服從 <span class="text-nowrap">$\mathrm{Beta}(\alpha=a,\ \beta=b)$，</span>兩者之和 $V=X+Y$ 則服從 <span class="text-nowrap">$\mathrm{Gamma}(\alpha=a+b,\ \beta)$，</span>而且 $U$ 與 $V$ 彼此獨立。證明採 Jacobian 法，先寫出兩個伽瑪變數的聯合機率密度函數，換元之後所得到的聯合機率密度函數恰好可以拆成只含 $u$ 的一段與只含 $v$ 的一段，兩段各自積分之後，貝塔分配與伽瑪分配的機率函數就分別出現在 $U$ 與 $V$ 的邊際機率密度函數上。

定理之後的說明給出一個稍不嚴謹但簡單直接的想法: 比例的平均是兩個期望值之間的比例，也就是 $\frac{a\beta}{\,a\beta+b\beta\,}=\frac{a}{\,a+b\,}$ 這個比值，恰好是貝塔分配的期望值。同一段也指出一個特例，即兩個比例參數相同且彼此獨立的[指數分配](/lecture-notes/gamma-function-exponential-distribution/#def-exponential-distribution)變數，其比例服從[標準均勻分配](/lecture-notes/uniform-distribution-integral-transform/#def-uniform-distribution)。

三道例題各練一種用法。[Example 4.41](#ex-gamma-beta-1) 先由機率密度函數的合法性定出 <span class="text-nowrap">$k=1$，</span>辨識出兩個變數服從 <span class="text-nowrap">$\mathrm{Exp}(\beta=1)$，</span>再依 Jacobian 法逐步算出 $Y_1=X_1+X_2$ 與 $Y_2=\frac{X_1}{\,X_1+X_2\,}$ 的聯合與邊際機率密度函數，最後由聯合機率密度函數可以拆成兩個邊際機率密度函數的乘積、且範圍互不影響，判定兩者獨立，這正是 [Theorem 4.19](#thm-gamma-to-beta) 在 $a=b=1$ 時的情形。[Example 4.42](#ex-gamma-beta-2) 處理標準均勻分配的順序統計量: 由兩個順序統計量的聯合機率密度函數算出共變異數 <span class="text-nowrap">$\frac{r(n+1-s)}{\,(n+1)^2(n+2)\,}$，</span>再以變數變換求得全距 $R=Y_{\sssig (n)}-Y_{\sssig (1)}$ 服從 <span class="text-nowrap">$\mathrm{Beta}(\alpha=n-1,\ \beta=2)$；</span>第三小題則以機率積分轉換把韋伯變數換成標準均勻變數，所求的量因而與第二小題完全相同。該題之後的說明另給一個省事的作法: 直接引用順序統計量之差服從貝塔分配這個結果，再由變異數的展開式反解共變異數。[Example 4.43](#ex-gamma-beta-3) 是同一組結果在 $n=3$ 上的演練，$Y_3-Y_1$ 服從 <span class="text-nowrap">$\mathrm{Beta}(\alpha=2,\ \beta=2)$，</span>而極小值與極大值之平均的期望值為 <span class="text-nowrap">$\frac{1}{\,2\,}$、</span>變異數為 <span class="text-nowrap">$\frac{1}{\,40\,}$。</span>

[下一篇](/lecture-notes/normal-distribution/)轉入常態相關的機率模型，先給出高斯積分，再定義常態分配，並說明標準化與線性組合的可加性。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
