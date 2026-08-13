---
title: "動差母函數法的例題"
subtitle: "Examples of the Moment Generating Function Method"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 26
order: 326
permalink: /teaching-topics/mgf-method-examples/
date: 2026-08-13
published: false
excerpt: "本篇以三道例題演練動差母函數法。第一題只給出兩個獨立變數的 mgf，先由線性組合的 mgf 認出 $U=3X+2Y$ 的分配，再由 mgf 的唯一性回推兩個 pdf，改以 Jacobian 法求得 $U$ 與 $V$ 的聯合 pdf，進而得到 $V$ 的期望值與變異數。第二題求隨機樣本之樣本平均的分配，樣本平均也是一種針對樣本的線性組合，每個樣本的權重都是 $\\frac{1}{n}$ 這個值，而常態分配的任意線性組合仍為常態分配。第三題以三個小題處理獨立均勻樣本的和、對數乘積與最大值，其中兩個變數之和的 pdf 分別以 Jacobian 法與 cdf 法各解一次，並附上座標系轉換前後的值域圖，最後一則註記則指出「排序」其實也是一種函數轉換。"
---

[上一篇](/teaching-topics/mgf-method-transformations/)先以兩道例題示範多對一的作法，即先做一次維度相同的函數轉換，再把不需要的變數積分掉；接著以 [Theorem 3.23](/teaching-topics/mgf-method-transformations/#thm-mgf-two-to-one) 指出，若各變數彼此[獨立](/teaching-topics/independent-random-variables/#def-indep-r-v)且轉換是線性的，則 $W=\sum_{i=1}^{n}a_i\,X_i+b$ 的 mgf 是 $e^{bt}$ 與各項 mgf 的乘積，並以另外兩道例題由 mgf 的唯一性認出轉換後的分配。

本篇以三道例題繼續演練這個做法。[Example 3.57](#ex-independent-mgf-difference) 先由兩個獨立變數的 mgf 認出線性組合的分配，再由 mgf 的唯一性回推出兩個 pdf，改以 [Jacobian 法](/teaching-topics/many-to-many-transformations/#連續型的-jacobian-法)求出另一個變數的[期望值](/teaching-topics/expectation/#def-expectation)與[變異數](/teaching-topics/variance/#def-variance)；[Example 3.58](#ex-random-sample-mgf-mean) 求隨機樣本之樣本平均的分配；[Example 3.59](#ex-independent-mgf-linear) 則以三個小題處理獨立均勻樣本的和、對數乘積與最大值，其中兩個變數之和的 pdf 分別以 Jacobian 法與 cdf 法各解一次。

<div id="ex-independent-mgf-difference" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.57</div>

<div lang="en" markdown="1">
Suppose that $X$ and $Y$ are two independent random variables, that the mgf of $X$ is

$$
M_{\sssig X}(t)=(1-2t)^{-3},\ t<1/2
$$

and that the mgf of $Y$ is

$$
M_{\sssig Y}(t)=(1-3t)^{-2},\ t<1/3
$$

<ol class="topic-list-paren">
  <li>Determine the distribution of <span class="text-nowrap">$U=3X+2Y$.</span></li>
  <li>Evaluate the mean and the variance of <span class="text-nowrap">$V=\frac{2Y}{\,3X+2Y\,}$.</span></li>
</ol>
</div>

(1) 由於 $X$ $\indep$ <span class="text-nowrap">$Y$，</span>故可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
M_{\sssig U}(t)=M_{\sssig X}(3t)\,M_{\sssig Y}(2t)=\bigl[1-2(3t)\bigr]^{-3}\bigl[1-3(2t)\bigr]^{-2}=(1-6t)^{-5},\ t<1/6
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig U}(t)&=M_{\sssig X}(3t)\,M_{\sssig Y}(2t)\\[0.45em]
&=\bigl[1-2(3t)\bigr]^{-3}\bigl[1-3(2t)\bigr]^{-2}\\[0.45em]
&=(1-6t)^{-5},\ t<1/6
\end{aligned}
$$

</div>

由 mgf 的唯一性可知
{: .topic-paren-cont}

$$
U=3X+2Y\sim\mathrm{Gamma}(\alpha=5,\beta=6)
$$

(2) 由 mgf 的唯一性可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X}(x)=\frac{1}{\,2^{3}\Gamma(3)\,}x^{3-1}e^{\frac{-x}{2}},\ x>0\quad\text{及}\quad f_{\sssig Y}(y)=\frac{1}{\,3^{2}\Gamma(2)\,}y^{2-1}e^{\frac{-y}{3}},\ y>0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
f_{\sssig X}(x)=\frac{1}{\,2^{3}\Gamma(3)\,}x^{3-1}e^{\frac{-x}{2}},\ x>0\\[0.55em]
\text{及}\quad f_{\sssig Y}(y)=\frac{1}{\,3^{2}\Gamma(2)\,}y^{2-1}e^{\frac{-y}{3}},\ y>0
\end{gathered}
$$

</div>

且
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f_{\sssig XY}(x,y)&=f_{\sssig X}(x)f_{\sssig Y}(y)=\frac{1}{\,2^{3}\Gamma(3)\,}x^{3-1}e^{\frac{-x}{2}}\times\frac{1}{\,3^{2}\Gamma(2)\,}y^{2-1}e^{\frac{-y}{3}}\\[0.45em]
&=\frac{1}{\,2^{3}\Gamma(3)3^{2}\Gamma(2)\,}x^{3-1}y^{2-1}e^{\frac{-x}{2}+\frac{-y}{3}},\ \ x,y>0
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&f_{\sssig XY}(x,y)=f_{\sssig X}(x)f_{\sssig Y}(y)\\[0.45em]
&\quad =\frac{1}{\,2^{3}\Gamma(3)\,}x^{3-1}e^{\frac{-x}{2}}\times\frac{1}{\,3^{2}\Gamma(2)\,}y^{2-1}e^{\frac{-y}{3}}\\[0.45em]
&\quad =\frac{1}{\,2^{3}\Gamma(3)3^{2}\Gamma(2)\,}x^{3-1}y^{2-1}e^{\frac{-x}{2}+\frac{-y}{3}},\\[0.25em]
&\qquad\qquad x,y>0
\end{aligned}
$$

</div>

令 $U=3X+2Y$ 及 <span class="text-nowrap">$V=\frac{2Y}{\,3X+2Y\,}$，</span>則
{: .topic-paren-cont}

$$
\left\lbrace
\begin{array}{l}
U=3X+2Y\\[0.5em]
V=\dfrac{2Y}{\,3X+2Y\,}
\end{array}
\right.
\ \Rightarrow\
\left\lbrace
\begin{array}{l}
X=\dfrac{U(1-V)}{3}\\[0.7em]
Y=\dfrac{UV}{2}
\end{array}
\right.
$$

且
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbf{J}=
\left\lvert
\begin{array}{cc}
\dfrac{\partial x}{\partial u} & \dfrac{\partial x}{\partial v}\\[0.8em]
\dfrac{\partial y}{\partial u} & \dfrac{\partial y}{\partial v}
\end{array}
\right\rvert=
\left\lvert
\begin{array}{cc}
\dfrac{1-v}{3} & \dfrac{-u}{3}\\[0.8em]
\dfrac{v}{2} & \dfrac{u}{2}
\end{array}
\right\rvert=\frac{u}{6}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbf{J}&=
\left\lvert
\begin{array}{cc}
\dfrac{\partial x}{\partial u} & \dfrac{\partial x}{\partial v}\\[0.8em]
\dfrac{\partial y}{\partial u} & \dfrac{\partial y}{\partial v}
\end{array}
\right\rvert\\[0.6em]
&=
\left\lvert
\begin{array}{cc}
\dfrac{1-v}{3} & \dfrac{-u}{3}\\[0.8em]
\dfrac{v}{2} & \dfrac{u}{2}
\end{array}
\right\rvert=\frac{u}{6}
\end{aligned}
$$

</div>

由 Jacobian 法可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f_{\sssig UV}(u,v)&=f_{\sssig XY}\Bigl(\frac{u(1-v)}{3},\frac{uv}{2}\Bigr)\lvert\mathbf{J}\rvert\\[0.45em]
&=\frac{1}{\,2^{3}\Gamma(3)3^{2}\Gamma(2)\,}\biggl[\frac{u(1-v)}{3}\biggr]^{3-1}\biggl[\frac{uv}{2}\biggr]^{2-1}e^{\frac{-\frac{u(1-v)}{3}}{2}+\frac{-\frac{uv}{2}}{3}}\biggl\lvert\frac{u}{6}\biggr\rvert\\[0.45em]
&=\frac{1}{\,6^{5}\Gamma(2+3)\,}u^{5-1}e^{\frac{-u}{6}}\times\frac{\Gamma(2+3)}{\,\Gamma(2)\Gamma(3)\,}v^{2-1}(1-v)^{3-1},\ \ u>0,\ 0<v<1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&f_{\sssig UV}(u,v)=f_{\sssig XY}\Bigl(\frac{u(1-v)}{3},\frac{uv}{2}\Bigr)\lvert\mathbf{J}\rvert\\[0.45em]
&\quad =\frac{1}{\,2^{3}\Gamma(3)3^{2}\Gamma(2)\,}\biggl[\frac{u(1-v)}{3}\biggr]^{3-1}\\[0.25em]
&\qquad\quad \times\biggl[\frac{uv}{2}\biggr]^{2-1}e^{\frac{-\frac{u(1-v)}{3}}{2}+\frac{-\frac{uv}{2}}{3}}\biggl\lvert\frac{u}{6}\biggr\rvert\\[0.45em]
&\quad =\frac{1}{\,6^{5}\Gamma(2+3)\,}u^{5-1}e^{\frac{-u}{6}}\\[0.25em]
&\qquad\quad \times\frac{\Gamma(2+3)}{\,\Gamma(2)\Gamma(3)\,}v^{2-1}(1-v)^{3-1},\\[0.25em]
&\qquad\qquad u>0,\ 0<v<1
\end{aligned}
$$

</div>

則
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
U\sim\mathrm{Gamma}(\alpha=5,\beta=6)\ \indep\ V\sim\mathrm{Beta}(\alpha=2,\beta=3)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
U\sim\mathrm{Gamma}(\alpha=5,\beta=6)\\[0.45em]
\indep\ V\sim\mathrm{Beta}(\alpha=2,\beta=3)
\end{gathered}
$$

</div>

可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(V)=\frac{2}{\,2+3\,}=\frac{2}{\,5\,},\ \ \ \mathrm{Var}(V)=\frac{2\times3}{\,(2+3+1)(2+3)^{2}\,}=\frac{1}{\,25\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{E}(V)=\frac{2}{\,2+3\,}=\frac{2}{\,5\,}\\[0.55em]
\mathrm{Var}(V)=\frac{2\times3}{\,(2+3+1)(2+3)^{2}\,}=\frac{1}{\,25\,}
\end{gathered}
$$

</div>

</div>

<!-- ref-point: 待第四章的伽瑪分配與貝塔分配主題發布後，將本題中的 Gamma 與 Beta 兩個分配名稱改為指向該處的站內連結。 -->

<div id="ex-random-sample-mgf-mean" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.58</div>

<div lang="en" markdown="1">
Let $X_1, \ldots, X_n$ be a random sample from a distribution with mgf

$$
M_{\sssig X}(t)=e^{\mu t+\sigma^{2}\frac{\,t^{2}\,}{2}},\ t\in\mathbb{R}
$$

Find the distribution of the sample mean, <span class="text-nowrap">$\overline{X}=\frac{1}{\,n\,}\sum_{i=1}^{n}X_i$.</span>
</div>

由於 $X_1, \ldots, X_n$ 為隨機樣本，故知道

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
M_{\sssig \overline{X}}(t)=\prod_{i=1}^{n}M_{\sssig X_i}\Bigl(\frac{1}{n}\,t\Bigr)=\prod_{i=1}^{n}e^{\mu\frac{t}{n}+\sigma^{2}\frac{\,\left(\frac{t}{n}\right)^{2}\,}{2}}=e^{\mu t+\frac{\sigma^{2}}{n}\frac{\,t^{2}\,}{2}},\ t\in\mathbb{R}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig \overline{X}}(t)&=\prod_{i=1}^{n}M_{\sssig X_i}\Bigl(\frac{1}{n}\,t\Bigr)\\[0.45em]
&=\prod_{i=1}^{n}e^{\mu\frac{t}{n}+\sigma^{2}\frac{\,\left(\frac{t}{n}\right)^{2}\,}{2}}\\[0.45em]
&=e^{\mu t+\frac{\sigma^{2}}{n}\frac{\,t^{2}\,}{2}},\ t\in\mathbb{R}
\end{aligned}
$$

</div>

依 mgf 的唯一性可知

$$
\overline{X}\sim\mathcal{N}\Bigl(\mu,\frac{\,\sigma^{2}\,}{n}\Bigr)
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

樣本平均 (sample mean) 也是一種針對樣本的線性組合，每個樣本的權重同為 <span class="text-nowrap">$\frac{1}{n}$。</span>

事實上，常態分配的任意線性組合，其結果都是常態分配，這是常態分配特有的**仿射變換 <span lang="en">(affine transformation)</span>** 性質，在多元常態的矩陣運算中特別有用 (讀者不應忘記，矩陣運算屬於線性運算的一環)。

</div>

<!-- ref-point: 待第四章的常態分配主題發布後，將本則 Note 的「常態分配」改為指向該處的站內連結。 -->

<div id="ex-independent-mgf-linear" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.59</div>

<div lang="en" markdown="1">
Suppose that $X_1, \ldots, X_n$ are independent random variables sharing the common pdf

$$
f_{\sssig X}(x)=\left\lbrace
\begin{array}{cl}
1 &,\ 0<x<1\\[0.2em]
0 &,\ \text{otherwise.}
\end{array}
\right.
$$

<ol class="topic-list-paren">
  <li>Determine the pdf of <span class="text-nowrap">$X_1+X_2$.</span></li>
  <li>Suppose that <span class="text-nowrap">$Y=-2\ln\prod_{i=1}^{n}X_i$.</span> Determine the pdf, the mean and the variance of <span class="text-nowrap">$Y$.</span></li>
  <li>Suppose that <span class="text-nowrap">$X_{\sssig (n)}=\max\lbrace X_1,\ldots,X_n\rbrace$.</span> Determine the pdf, the mean and the variance of <span class="text-nowrap">$X_{\sssig (n)}$.</span></li>
</ol>
</div>

(1) **Jacobian 法**
{: .topic-paren-item}

由於 $X_1$ $\indep$ <span class="text-nowrap">$X_2$，</span>我們有
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X_1X_2}(x_1,x_2)=f_{\sssig X_1}(x_1)\,f_{\sssig X_2}(x_2)=1\times1=1,\ \ 0<x_1,x_2<1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&f_{\sssig X_1X_2}(x_1,x_2)=f_{\sssig X_1}(x_1)\,f_{\sssig X_2}(x_2)\\[0.45em]
&\quad =1\times1=1,\ \ 0<x_1,x_2<1
\end{aligned}
$$

</div>

令 $U=X_1+X_2$ 與 <span class="text-nowrap">$V=X_1$，</span>則
{: .topic-paren-cont}

$$
\left\lbrace
\begin{array}{l}
U=X_1+X_2\\[0.3em]
V=X_1
\end{array}
\right.
\ \Rightarrow\
\left\lbrace
\begin{array}{l}
X_1=V\\[0.3em]
X_2=U-V
\end{array}
\right.
$$

且
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbf{J}=
\left\lvert
\begin{array}{cc}
\dfrac{\partial x_1}{\partial u} & \dfrac{\partial x_1}{\partial v}\\[0.8em]
\dfrac{\partial x_2}{\partial u} & \dfrac{\partial x_2}{\partial v}
\end{array}
\right\rvert=
\left\lvert
\begin{array}{cc}
0 & 1\\[0.3em]
1 & -1
\end{array}
\right\rvert=-1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbf{J}&=
\left\lvert
\begin{array}{cc}
\dfrac{\partial x_1}{\partial u} & \dfrac{\partial x_1}{\partial v}\\[0.8em]
\dfrac{\partial x_2}{\partial u} & \dfrac{\partial x_2}{\partial v}
\end{array}
\right\rvert\\[0.6em]
&=
\left\lvert
\begin{array}{cc}
0 & 1\\[0.3em]
1 & -1
\end{array}
\right\rvert=-1
\end{aligned}
$$

</div>

由 Jacobian 法可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f_{\sssig UV}(u,v)&=f_{\sssig X_1X_2}(v,u-v)\lvert\mathbf{J}\rvert\\[0.45em]
&=1\times\lvert-1\rvert=1,\ \ 0<u<2,\ 0<v<1,\ v<u,\ 0<u-v<1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&f_{\sssig UV}(u,v)=f_{\sssig X_1X_2}(v,u-v)\lvert\mathbf{J}\rvert\\[0.45em]
&\quad =1\times\lvert-1\rvert=1,\\[0.25em]
&\qquad 0<u<2,\ 0<v<1,\\[0.25em]
&\qquad v<u,\ 0<u-v<1
\end{aligned}
$$

</div>

則 $U=X_1+X_2$ 之 marginal pdf 為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig U}(u)=\left\lbrace
\begin{array}{ll}
\displaystyle\int_{0}^{u}f_{\sssig UV}(u,v)\,dv=\int_{0}^{u}1\,dv=u &,\ 0<u<1\\[1.2em]
\displaystyle\int_{u-1}^{1}f_{\sssig UV}(u,v)\,dv=\int_{u-1}^{1}1\,dv=2-u &,\ 1\leqslant u<2
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&f_{\sssig U}(u)\\[0.45em]
&=\left\lbrace
\begin{array}{l}
\displaystyle\int_{0}^{u}f_{\sssig UV}(u,v)\,dv\\[0.4em]
\quad =\displaystyle\int_{0}^{u}1\,dv=u,\ \ 0<u<1\\[1.1em]
\displaystyle\int_{u-1}^{1}f_{\sssig UV}(u,v)\,dv\\[0.4em]
\quad =\displaystyle\int_{u-1}^{1}1\,dv=2-u,\\[0.4em]
\qquad 1\leqslant u<2
\end{array}
\right.
\end{aligned}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

在考慮 $U$ 與 $V$ 的聯合值域時，我們可以先考慮 $X_1$ 與 $X_2$ 的聯合值域，並做座標系轉換。$X_1$ 與 $X_2$ 的聯合值域如下

<!-- fig-pending: transform-original-range
     Fig. 3.21，對應書稿 mathstatch3.tex 第 4868 至 4897 行的 tikzpicture，單面板。
     內容: 座標系轉換之前 $X_1$ 與 $X_2$ 的聯合值域，也就是單位正方形。
     兩條帶箭頭的座標軸自原點分別畫到 (3.8, 0) 與 (0, 3.8)，都沒有刻度線。
     填色區域為 (0,0)、(0,3)、(3,3)、(3,0) 四點所圍的正方形 (書稿用 fill=gray、
     opacity=0.2，網頁依 CH3_FIGURE_SPECS.md 第一節改用 journalaccent、透明度 0.15)。
     正方形的上邊 (0,3) 至 (3,3) 與右邊 (3,0) 至 (3,3) 另以實線描出，左邊與下邊即座標軸。
     標示五處: 橫軸右端外側 (4.3, 0.15) 的下方標 $x_1$；縱軸上端 (0, 4.3) 的下方標 $x_2$；
     (3, 0) 的下方標 $1$；(0, 0) 的下方標 $0$；(0, 3) 的左方標 $1$。
     書稿在圖內定義了 \normaltwo 這條斜線但把繪製指令註解掉了，因此本圖沒有任何斜線。
     檔名 transform-original-range.svg，anchor 取 #fig-transform-original-range。
     圖畫好之後，本段末的「如下」改為指向該 anchor 的 Fig. 3.21 連結，並補上 caption。
-->

令 $U=X_1+X_2$ 及 <span class="text-nowrap">$V=X_1$，</span>我們可將 $U$ 與 $V$ 在原始座標系的範圍繪製如下

<!-- fig-pending: transform-uv-range
     Fig. 3.22，對應書稿 mathstatch3.tex 第 4904 至 4958 行 (左面板) 與第 4961 至 4998 行
     (右面板) 的兩個 tikzpicture。兩者同在第 4902 至 5000 行的 center 之內，各放在一個
     minipage (.58\textwidth 與 .4\textwidth) 裡並排；網頁併為一張兩面板的圖 (桌面左右
     並排，手機改為上下排列)。兩個 tikzpicture 都下了 scale=0.75。
     兩面板共通: 座標軸為兩條帶箭頭的直線，都沒有刻度線；填色書稿用 gray、opacity 0.2，
     網頁改 journalaccent、透明度 0.15。圖上三個單位長等於數值 1。

     左面板 (轉換前的 $(x_1, x_2)$ 平面):
       填色區域為 (0,0)、(0,3)、(3,3)、(3,0) 所圍的單位正方形，上邊與右邊以實線描出。
       兩條實線標出 $u$ 的兩個端點: 一條沿 $x_2=-x_1$ 畫在 domain $-1$ 至 $1$ 之間，
       即 $u=x_1+x_2=0$ 這條線；另一條沿 $x_2=-x_1+6$ 畫在 domain $2$ 至 $4$ 之間，
       即 $u=x_1+x_2=2$ 這條線。另有一條虛線自 (0,3) 畫到 (3,0)，即 $u=1$ 這條線。
       標示: 橫軸右端 (4.5, 0.15) 的下方標 $x_1=v$；縱軸上端 (0, 4.3) 的下方標 $x_2$；
       (3, 0) 的下方標 $1$；(0, 0) 的下方標 $0$；(0, 3) 的左方標 $1$；
       (1.1, -1.1) 的右方標 $u = x_1+x_2 = 0$；(4.1, 2) 的右方標 $u = x_1+x_2 = 2$。
       兩面板之間書稿另放一個帶文字的長箭號 $\xRightarrow{\ \text{令}\ u=x_1+x_2,\ v=x_1\ }$
       (原在左面板的 (7.5, 1.3) 處)。網頁手機版改為上下排列時，這個箭號要一併轉向或
       改置於兩面板之間，畫圖時一併處置。

     右面板 (轉換後的 $(v, u)$ 平面):
       填色區域為 $v$ 自 0 到 1、$u$ 自 $v$ 到 $v+1$ 所圍的平行四邊形，四個頂點依序為
       (0,0)、(3,3)、(3,6)、(0,3)。兩條實線分別沿 $u=v$ 與 $u=v+3$ (即 $v=u$ 與 $v=u-1$)
       畫在 domain $-0.5$ 至 $3.5$ 之間，右邊 (3,3) 至 (3,6) 亦為實線。
       三條虛線: (0,3) 至 (3,3)、(0,6) 至 (3,6)、(3,0) 至 (3,3)。
       標示: 橫軸右端 (4.5, 0.15) 的下方標 $v$；縱軸上端 (0, 7.3) 的下方標 $u$；
       (3, 0) 的下方標 $1$；(0, 0) 的下方標 $0$；(0, 3) 的左方標 $1$；(0, 6) 的左方標 $2$；
       (3.6, 6.6) 的右方標 $v=u-1$；(3.6, 3.6) 的右方標 $v=u$。
       縱軸畫到 (0, 6.8)，比左面板高一倍，兩面板並排時的縱向比例要一併校準。
     檔名 transform-uv-range.svg，anchor 取 #fig-transform-uv-range。
     圖畫好之後，本段末的「繪製如下」改為指向該 anchor 的 Fig. 3.22 連結，並補上 caption。
-->

如此便可以知道 $U$ 與 $V$ 的聯合值域，進一步求取 $U$ 的邊際分配。

</div>

**cdf 法**
{: .topic-paren-cont}

令 <span class="text-nowrap">$U=X_1+X_2$，</span>並考慮 $U$ 的 cdf，我們有
{: .topic-paren-cont}

$$
F_{\sssig U}(u)=\mathbb{P}(U\leqslant u)
$$

又 $U\leqslant u$ 依照 $u$ 的範圍不同，可能有兩種情形
{: .topic-paren-cont}

<!-- fig-pending: sum-range-two-cases
     Fig. 3.23，對應書稿 mathstatch3.tex 第 5013 至 5045 行 (左面板) 與第 5049 至 5080 行
     (右面板) 的兩個 tikzpicture。兩者同在第 5011 至 5082 行的 center 之內，各放在一個
     minipage (.45\textwidth 與 .4\textwidth) 裡並排；網頁併為一張兩面板的圖 (桌面左右
     並排，手機改為上下排列)。畫的是 $U=X_1+X_2$ 的 cdf 依 $u$ 的範圍所分成的兩段積分範圍。
     兩面板共通: 兩條帶箭頭的座標軸自原點分別畫到 (3.5, 0) 與 (0, 3.5)，都沒有刻度線；
     單位正方形的上邊 (0,3) 至 (3,3) 與右邊 (3,0) 至 (3,3) 以實線描出；
     標示 (3.8, 0.15) 的下方為 $x_1$、(0, 4.0) 的下方為 $x_2$、(3, 0) 的下方為 $1$、
     (0, 0) 的下方為 $0$、(0, 3) 的左方為 $1$。填色書稿用 gray、opacity 0.2，
     網頁改 journalaccent、透明度 0.15。圖上三個單位長等於數值 1。

     左面板 ($0<u<1$ 的情形):
       一條實線沿 $x_2=2-x_1$ 畫在 domain $-0.5$ 至 $2.5$ 之間，即 $u=x_1+x_2$ 這條線；
       此時該線與兩軸相交於 (0,2) 與 (2,0)，兩端各略微伸出第一象限之外。
       填色區域為 (0,0)、(0,2) 與 (2,0) 所圍的直角三角形。標示兩處:
       (-0.6, 2.6) 的左方標 $u = x_1+x_2$；面板下方 (1.5, -0.5) 的下方標 $0<u<1$。

     右面板 ($1\leqslant u<2$ 的情形):
       一條實線沿 $x_2=4-x_1$ 畫在 domain $0.5$ 至 $3.5$ 之間，即 $u=x_1+x_2$ 這條線
       此時切過單位正方形的右上角。填色區域為 (0,0)、(0,3)、(1,3)、該線與正方形右邊的
       交點 (3,1)、(3,0) 所圍的五邊形，也就是單位正方形扣掉右上角那個小三角形。
       標示兩處: (3.6, 0.4) 的右方標 $u = x_1+x_2$；面板下方 (1.5, -0.5) 的下方標
       $1\leqslant u<2$。

     兩面板的 \fill 路徑都經由 plot 的起點折返 (左面板繞到 (0,2) 之外、右面板繞到
       (0,4))，那是書稿寫法的副作用，不是要畫的形狀；網頁一律照上面所述的三角形與
       五邊形填色。

     書稿在左面板的右側 (4.0, 1.5) 另放一個「與」字連接兩個面板，這是 LaTeX 並排時的
     排版手法；網頁兩面板改由格線並排，畫圖時決定是否保留該字，若不保留須併入勘誤登錄。
     檔名 sum-range-two-cases.svg，anchor 取 #fig-sum-range-two-cases。
     圖畫好之後，本段末的「兩種情形」改為指向該 anchor 的 Fig. 3.23 連結，並補上 caption。
-->

依照 $0<u<1$ 與 <span class="text-nowrap">$1\leqslant u<2$，</span>我們分列如下
{: .topic-paren-cont}

[$0<u<1$]
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
F_{\sssig U}(u)&=\mathbb{P}(U\leqslant u)=\int^{u}_{0}\int_{0}^{u-x_2}f_{\sssig X_1X_2}(x_1,x_2)\,dx_1\,dx_2\\[0.45em]
&=\int_{0}^{u}\int_{0}^{u-x_2}1\,dx_1\,dx_2=\int_{0}^{u}(u-x_2)\,dx_2\\[0.45em]
&=\left[ux_2-\frac{1}{2}x_2^{2}\right]^{u}_{0}=\frac{u^{2}}{2},\ \ 0<u<1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&F_{\sssig U}(u)=\mathbb{P}(U\leqslant u)\\[0.45em]
&\quad =\int^{u}_{0}\int_{0}^{u-x_2}f_{\sssig X_1X_2}(x_1,x_2)\,dx_1\,dx_2\\[0.45em]
&\quad =\int_{0}^{u}\int_{0}^{u-x_2}1\,dx_1\,dx_2\\[0.45em]
&\quad =\int_{0}^{u}(u-x_2)\,dx_2\\[0.45em]
&\quad =\left[ux_2-\frac{1}{2}x_2^{2}\right]^{u}_{0}=\frac{u^{2}}{2},\\[0.25em]
&\qquad\quad 0<u<1
\end{aligned}
$$

</div>

[$1\leqslant u<2$]
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
F_{\sssig U}(u)&=\mathbb{P}(U\leqslant u)=1-\mathbb{P}(U>u)=1-\int_{u-1}^{1}\int_{u-x_2}^{1}f_{\sssig X_1X_2}(x_1,x_2)\,dx_1\,dx_2\\[0.45em]
&=1-\int_{u-1}^{1}\int_{u-x_2}^{1}1\,dx_1\,dx_2=1-\int_{u-1}^{1}(1-u+x_2)\,dx_2\\[0.45em]
&=1-\left[x_2-ux_2+\frac{1}{2}x_2^{2}\right]^{1}_{u-1}=-\frac{1}{2}u^{2}+2u-1,\ \ 1\leqslant u<2
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&F_{\sssig U}(u)=\mathbb{P}(U\leqslant u)=1-\mathbb{P}(U>u)\\[0.45em]
&\quad =1-\int_{u-1}^{1}\int_{u-x_2}^{1}f_{\sssig X_1X_2}(x_1,x_2)\,dx_1\,dx_2\\[0.45em]
&\quad =1-\int_{u-1}^{1}\int_{u-x_2}^{1}1\,dx_1\,dx_2\\[0.45em]
&\quad =1-\int_{u-1}^{1}(1-u+x_2)\,dx_2\\[0.45em]
&\quad =1-\left[x_2-ux_2+\frac{1}{2}x_2^{2}\right]^{1}_{u-1}\\[0.45em]
&\quad =-\frac{1}{2}u^{2}+2u-1,\ \ 1\leqslant u<2
\end{aligned}
$$

</div>

合併此二種情況，可得
{: .topic-paren-cont}

$$
F_{\sssig U}(u)=\left\lbrace
\begin{array}{cl}
0 &,\ u\leqslant0\\[0.4em]
\dfrac{u^{2}}{2} &,\ 0<u<1\\[0.7em]
-\dfrac{1}{2}u^{2}+2u-1 &,\ 1\leqslant u<2\\[0.7em]
1 &,\ u\geqslant2
\end{array}
\right.
$$

經由微分可以得到 $U$ 之 pdf 為
{: .topic-paren-cont}

$$
f_{\sssig U}(u)=\frac{d\,F_{\sssig U}(u)}{d\,u}=\left\lbrace
\begin{array}{cl}
u &,\ 0<u<1\\[0.4em]
2-u &,\ 1\leqslant u<2
\end{array}
\right.
$$

(2) 首先令 $W_i=-2\ln X_i,$ <span class="text-nowrap">$i=1,2,\ldots,n$，</span>則 <span class="text-nowrap">$Y=\sum_{i=1}^{n}W_i$，</span>並且我們有
{: .topic-paren-item}

$$
X_i=e^{\frac{-W_i}{2}}\ \ \Longrightarrow\ \ \mathbf{J}=\frac{d\,x_i}{d\,w_i}=-\frac{1}{2}e^{-\frac{\,w_i\,}{2}}
$$

又由於 <span class="text-nowrap">$X_i\overset{\mathrm{iid}}{\sim}\mathcal{U}(0,1)$，</span>由 Jacobian 法可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig W_i}(w_i)=f_{\sssig X_i}\bigl(e^{\frac{\,-w_i\,}{2}}\bigr)\lvert\mathbf{J}\rvert=1\times\biggl\lvert-\frac{1}{2}e^{-\frac{\,w_i\,}{2}}\biggr\rvert=\frac{1}{2}e^{-\frac{\,w_i\,}{2}},\ \ w_i>0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&f_{\sssig W_i}(w_i)=f_{\sssig X_i}\bigl(e^{\frac{\,-w_i\,}{2}}\bigr)\lvert\mathbf{J}\rvert\\[0.45em]
&\quad =1\times\biggl\lvert-\frac{1}{2}e^{-\frac{\,w_i\,}{2}}\biggr\rvert\\[0.45em]
&\quad =\frac{1}{2}e^{-\frac{\,w_i\,}{2}},\ \ w_i>0
\end{aligned}
$$

</div>

此即 <span class="text-nowrap">$W_i\overset{\mathrm{iid}}{\sim}\mathrm{Exp}(\beta=2)$，</span>則由 Gamma 分配的可加性可知
{: .topic-paren-cont}

$$
Y=\sum_{i=1}^{n}W_i\sim\mathrm{Gamma}(\alpha=n,\beta=2)
$$

則我們有
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig Y}(y)=\frac{1}{\,2^{n}\Gamma(n)\,}y^{n-1}e^{\frac{-y}{2}},\ \ y>0,\ \ \ \ \mathbb{E}(Y)=n\times2=2n,\ \ \ \mathrm{Var}(Y)=n\times2^{2}=4n
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
f_{\sssig Y}(y)=\frac{1}{\,2^{n}\Gamma(n)\,}y^{n-1}e^{\frac{-y}{2}},\ \ y>0\\[0.55em]
\mathbb{E}(Y)=n\times2=2n\\[0.55em]
\mathrm{Var}(Y)=n\times2^{2}=4n
\end{gathered}
$$

</div>

(3) 由於 <span class="text-nowrap">$X_i\overset{\mathrm{iid}}{\sim}\mathcal{U}(0,1)$，</span>則可知 $F_{\sssig X_i}(x_i)=x_i,$ $0\leqslant x_i\leqslant1$ 及
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
F_{\sssig X_{\sssig (n)}}(x)&=\mathbb{P}(X_{\sssig (n)}\leqslant x)=\mathbb{P}(X_1\leqslant x,\ldots,X_n\leqslant x)\\[0.45em]
&=\mathbb{P}(X_1\leqslant x)\,\mathbb{P}(X_2\leqslant x)\cdots\mathbb{P}(X_n\leqslant x) &&\bigl[\ \because X_1,\ldots,X_n\ \text{獨立}\ \bigr]\\[0.45em]
&=F_{\sssig X_1}(x)\,F_{\sssig X_2}(x)\cdots F_{\sssig X_n}(x)=\bigl[F_{\sssig X_1}(x)\bigr]^{n} &&\bigl[\ \because X_1,\ldots,X_n\ \text{同分配}\ \bigr]\\[0.45em]
&=\left\lbrace
\begin{array}{cl}
0 &,\ x<0\\[0.3em]
x^{n} &,\ 0\leqslant x<1\\[0.3em]
1 &,\ x\geqslant1
\end{array}
\right.
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&F_{\sssig X_{\sssig (n)}}(x)=\mathbb{P}(X_{\sssig (n)}\leqslant x)\\[0.45em]
&\quad =\mathbb{P}(X_1\leqslant x,\ldots,X_n\leqslant x)\\[0.45em]
&\quad =\mathbb{P}(X_1\leqslant x)\,\mathbb{P}(X_2\leqslant x)\cdots\mathbb{P}(X_n\leqslant x)\\[0.25em]
&\qquad\quad \bigl[\ \because X_1,\ldots,X_n\ \text{獨立}\ \bigr]\\[0.45em]
&\quad =F_{\sssig X_1}(x)\,F_{\sssig X_2}(x)\cdots F_{\sssig X_n}(x)\\[0.25em]
&\quad =\bigl[F_{\sssig X_1}(x)\bigr]^{n}\\[0.25em]
&\qquad\quad \bigl[\ \because X_1,\ldots,X_n\ \text{同分配}\ \bigr]\\[0.45em]
&\quad =\left\lbrace
\begin{array}{cl}
0 &,\ x<0\\[0.3em]
x^{n} &,\ 0\leqslant x<1\\[0.3em]
1 &,\ x\geqslant1
\end{array}
\right.
\end{aligned}
$$

</div>

則我們有
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X_{\sssig (n)}}(x)=\frac{d\,F_{\sssig X_{\sssig (n)}}(x)}{d\,x}=nx^{n-1},\ 0<x<1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&f_{\sssig X_{\sssig (n)}}(x)=\frac{d\,F_{\sssig X_{\sssig (n)}}(x)}{d\,x}\\[0.45em]
&\quad =nx^{n-1},\ 0<x<1
\end{aligned}
$$

</div>

此即
{: .topic-paren-cont}

$$
X_{\sssig (n)}\sim\mathrm{Beta}(\alpha=n,\beta=1)
$$

故
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(X_{\sssig (n)})=\frac{n}{\,n+1\,},\ \ \mathrm{Var}(X_{\sssig (n)})=\frac{n\times1}{\,(n+1+1)(n+1)^{2}\,}=\frac{n}{\,(n+2)(n+1)^{2}\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{E}(X_{\sssig (n)})=\frac{n}{\,n+1\,}\\[0.55em]
\begin{aligned}
&\mathrm{Var}(X_{\sssig (n)})=\frac{n\times1}{\,(n+1+1)(n+1)^{2}\,}\\[0.35em]
&\quad =\frac{n}{\,(n+2)(n+1)^{2}\,}
\end{aligned}
\end{gathered}
$$

</div>

</div>

<!-- ref-point: 待第四章的均勻分配、指數分配、伽瑪分配與貝塔分配主題發布後，將 Example 3.59 解答中的 $\mathcal{U}(0,1)$、$\mathrm{Exp}(\beta=2)$、Gamma 分配的可加性與 $\mathrm{Beta}(\alpha=n,\beta=1)$ 各改為指向該處的站內連結。 -->

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

「排序」其實也是一種函數轉換，而「取排序後最大者」則是一種多轉一的轉換。

事實上，「排序」在統計學中被稱作[順序統計量](/teaching-topics/order-statistics/#def-order-stat) <span lang="en">(order statistics)</span>，我們馬上就會看到其相關的性質。

</div>

## 本篇小結

[Example 3.57](#ex-independent-mgf-difference) 把 mgf 法與 Jacobian 法接在同一道題裡。前半只用到獨立時 mgf 相乘這一點，$M_{\sssig U}(t)$ $=$ $M_{\sssig X}(3t)\,M_{\sssig Y}(2t)$ 化簡之後是 <span class="text-nowrap">$(1-6t)^{-5}$，</span>由唯一性即知 $U$ $=$ $3X+2Y$ 服從 <span class="text-nowrap">$\mathrm{Gamma}(\alpha=5,\beta=6)$。</span>後半要求的是 $V$ 的期望值與變異數，而 $V$ 並不是線性組合，[Theorem 3.23](/teaching-topics/mgf-method-transformations/#thm-mgf-two-to-one) 用不上，作法改為由唯一性回推 $X$ 與 $Y$ 的 pdf，寫出聯合 pdf 之後再以 Jacobian 法轉到 $(U,V)$ 上；轉換後的聯合 pdf 恰好拆成一個只含 $u$ 的因式與一個只含 $v$ 的因式，因此 $U$ 與 $V$ 獨立，而 $V$ 服從 <span class="text-nowrap">$\mathrm{Beta}(\alpha=2,\beta=3)$，</span>期望值與變異數分別為 $\frac{2}{5}$ 與 <span class="text-nowrap">$\frac{1}{25}$。</span>

[Example 3.58](#ex-random-sample-mgf-mean) 是線性組合的一個特例。樣本平均也是一種針對樣本的線性組合，只是每個樣本的權重同為 <span class="text-nowrap">$\frac{1}{n}$，</span>因此把 $\frac{t}{n}$ 代入每一項的 mgf 再相乘即可，所得的 $e^{\mu t+\frac{\sigma^{2}}{n}\frac{t^{2}}{2}}$ 仍是常態分配的 mgf，只是變異數縮成 <span class="text-nowrap">$\frac{\sigma^{2}}{n}$。</span>常態分配的任意線性組合都仍是常態分配，這是常態分配特有的仿射變換性質。

[Example 3.59](#ex-independent-mgf-linear) 的三個小題各走一條路。第一小題求兩個獨立均勻變數之和的 pdf，Jacobian 法補上 $V=X_1$ 這個輔助變數以湊足維度，轉換後再把 $V$ 積分掉，積分的上下限依 $u$ 落在 $0<u<1$ 或 $1\leqslant u<2$ 而不同；cdf 法則不必補變數，直接把 $\lbrace U\leqslant u\rbrace$ 畫在 $(x_1,x_2)$ 平面上求面積，同樣分成兩段，微分之後得到同一個三角形密度。第二小題先對每一項作 $W_i=-2\ln X_i$ 的轉換得到 <span class="text-nowrap">$\mathrm{Exp}(\beta=2)$，</span>再由 Gamma 分配的可加性得到 <span class="text-nowrap">$\mathrm{Gamma}(\alpha=n,\beta=2)$。</span>第三小題則利用最大值的事件可以拆成 $n$ 個獨立事件的交集這一點，直接由 cdf 相乘得到 $F_{\sssig X_1}(x)$ 的 $n$ 次方，微分之後即 <span class="text-nowrap">$\mathrm{Beta}(\alpha=n,\beta=1)$。</span>

第一小題的三張圖說明的是同一件事的兩種看法。Jacobian 法的那兩張把單位正方形依 $u=x_1+x_2$ 與 $v=x_1$ 重新畫成 $(v,u)$ 平面上的平行四邊形，$U$ 與 $V$ 的聯合值域一目瞭然；cdf 法的那一張則留在原座標系上，$0<u<1$ 時所求區域是一個三角形，$1\leqslant u<2$ 時改成整個正方形扣掉右上角的三角形，這正是求 $\mathbb{P}(U>u)$ 反而比較好算的原因。

[下一篇](/teaching-topics/order-statistics/)正式給出順序統計量的定義，並以三道例題處理順序統計量的聯合 pdf 與相關的機率計算。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
