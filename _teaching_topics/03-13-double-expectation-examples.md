---
title: "雙重期望值的例題"
subtitle: "Examples of the Double Expectation Theorem"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 13
order: 313
permalink: /lecture-notes/double-expectation-examples/
date: 2026-08-13
published: false
excerpt: "本篇以五道例題示範雙重期望值定理的用法。第一道題由聯合機率密度函數依序求出邊際密度、條件期望值與 $\\mathbb{E}(Y)$ 的值，是這條定理最直接的一種用法；第二道題的 $X$ 在給定 $Y=y$ 之下為常態分配、$Y$ 本身為伽瑪分配，兩者合起來所得的邊際密度在 $k=1$ 時即為 $\\mathrm{Cauchy}(0,1)$ 分配，此時 $\\mathbb{E}(X)$ 不存在，定理的等式因而不成立。第三道題只給了兩個已知數值與一條迴歸函數，仍然求得 $\\mathbb{E}(Y)$ 與 $\\mathbb{E}(XY)$ 兩個值。最後兩道題是礦工脫困與擲銅板的問題，兩者都先設一個輔助變數把實驗切成幾種情形，再讓所求的期望值在等式的兩側同時出現，解一條方程式即可求得。"
---

[上一篇](/lecture-notes/double-expectation-theorem/)由[條件期望值](/lecture-notes/conditional-expectation-and-variance/#def-conditional-expectation)是條件的函數這一點出發，先以[迴歸函數](/lecture-notes/double-expectation-theorem/#thm-regression-function)為這種函數取了名字，再給出[雙重期望值定理](/lecture-notes/double-expectation-theorem/#thm-double-expectation) <span lang="en">(double expectation theorem)</span>，並說明這條定理背後的直觀就是加權平均。先把原始空間依 $Y$ 的取值切成一片一片，在每一片的條件分配上找到重心，再以 $f_{\sssig Y}(y)$ 為權重把這些重心平均起來，所得的就是 $X$ 自己的重心。

本篇以五道例題示範這條定理的用法。前三道題是直接的計算: 第一道由[聯合機率密度函數](/lecture-notes/joint-probability-density-functions/#def-joint-pdf)依序求出邊際密度與條件期望值，再取一次期望值即得 $\mathbb{E}(Y)$ 的值；第二道說明 $\mathbb{E}(X)$ 不存在時，定理的等式會不成立；第三道只給了兩個已知數值與一條迴歸函數，仍然可以求出 $\mathbb{E}(Y)$ 與 $\mathbb{E}(XY)$ 兩個值。後兩道題的型態不同，都是先設一個輔助變數把整個實驗切成幾種情形，再讓所求的期望值在等式的兩側同時出現，解一條方程式即可求得。

<div id="ex-conditional-expectation-density" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.21</div>

<div lang="en" markdown="1">
Suppose that the joint probability density function of $X$ and $Y$ is

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig XY}(x,y)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{6}{\,5\,}\bigl(x+y^{2}\bigr), & 0<x<1,\ 0<y<1\\[0.8em]
0, & \text{o.w.}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig XY}(x,y)&=\left\lbrace
\begin{array}{c@{}l}
\dfrac{6}{\,5\,}\bigl(x+y^{2}\bigr), & 0<x<1,\ 0<y<1\\[0.8em]
0, & \text{o.w.}
\end{array}
\right.
\end{aligned}
$$

</div>

<ol class="topic-list-paren">
  <li>Determine the marginal pdf of <span class="text-nowrap">$X$.</span></li>
  <li>Evaluate <span class="text-nowrap">$\mathbb{E}(Y\mid X=x)$.</span></li>
  <li>Evaluate <span class="text-nowrap">$\mathbb{E}(Y)$.</span></li>
</ol>
</div>

(1) 依照 marginal pdf 定義可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f_{\sssig X}(x)&=\int_{0}^{1}\frac{6}{\,5\,}\bigl(x+y^{2}\bigr)\,dy=\Bigl[\frac{6}{\,5\,}xy+\frac{2}{\,5\,}y^{3}\Bigr]_{0}^{1}\\[0.45em]
&=\frac{6}{\,5\,}x+\frac{2}{\,5\,},\ 0<x<1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig X}(x)&=\int_{0}^{1}\frac{6}{\,5\,}\bigl(x+y^{2}\bigr)\,dy\\[0.45em]
&=\Bigl[\frac{6}{\,5\,}xy+\frac{2}{\,5\,}y^{3}\Bigr]_{0}^{1}\\[0.45em]
&=\frac{6}{\,5\,}x+\frac{2}{\,5\,},\ 0<x<1
\end{aligned}
$$

</div>

(2) 再由 conditional pdf 定義知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig Y\mid X}(y\mid x)=\frac{\frac{6}{\,5\,}\bigl(x+y^{2}\bigr)}{\,\frac{6}{\,5\,}x+\frac{2}{\,5\,}\,}=\frac{3\bigl(x+y^{2}\bigr)}{\,3x+1\,},\ 0<x<1,\ 0<y<1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig Y\mid X}(y\mid x)&=\frac{\frac{6}{\,5\,}\bigl(x+y^{2}\bigr)}{\,\frac{6}{\,5\,}x+\frac{2}{\,5\,}\,}\\[0.45em]
&=\frac{3\bigl(x+y^{2}\bigr)}{\,3x+1\,},\\[0.2em]
&\quad 0<x<1,\ 0<y<1
\end{aligned}
$$

</div>

由此可得
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ \mathbb{E}(Y\mid X=x)&=\int_{0}^{1}y\cdot\frac{3\bigl(x+y^{2}\bigr)}{3x+1}\,dy\\[0.45em]
&=\int_{0}^{1}\Bigl[\frac{3x}{\,3x+1\,}y+\frac{3}{\,3x+1\,}y^{3}\Bigr]dy\\[0.45em]
&=\Bigl[\frac{3x}{\,2(3x+1)\,}y^{2}+\frac{3}{\,4(3x+1)\,}y^{4}\Bigr]_{0}^{1}\\[0.45em]
&=\frac{3x}{\,2(3x+1)\,}+\frac{3}{\,4(3x+1)\,}\\[0.45em]
&=\frac{\,6x+3\,}{12x+4},\ 0<x<1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ \mathbb{E}(Y\mid X=x)&=\int_{0}^{1}y\cdot\frac{3\bigl(x+y^{2}\bigr)}{3x+1}\,dy\\[0.45em]
&=\int_{0}^{1}\Bigl[\frac{3x}{\,3x+1\,}y+\frac{3}{\,3x+1\,}y^{3}\Bigr]dy\\[0.45em]
&=\Bigl[\frac{3x}{\,2(3x+1)\,}y^{2}+\frac{3}{\,4(3x+1)\,}y^{4}\Bigr]_{0}^{1}\\[0.45em]
&=\frac{3x}{\,2(3x+1)\,}+\frac{3}{\,4(3x+1)\,}\\[0.45em]
&=\frac{\,6x+3\,}{12x+4},\ 0<x<1
\end{aligned}
$$

</div>

(3) 由[雙重期望值定理](/lecture-notes/double-expectation-theorem/#thm-double-expectation)可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[\mathbb{E}(Y\mid X)\bigr]&=\int_{0}^{1}\mathbb{E}(Y\mid X=x)\,f_{\sssig X}(x)\,dx\\[0.45em]
&=\int_{0}^{1}\frac{\,6x+3\,}{12x+4}\cdot\Bigl[\frac{6}{\,5\,}x+\frac{2}{\,5\,}\Bigr]dx\\[0.45em]
&=\int_{0}^{1}\Bigl[\frac{\,6x+3\,}{10}\Bigr]dx=\Bigl[\frac{3}{\,10\,}x^{2}+\frac{3}{\,10\,}x\Bigr]_{0}^{1}=\frac{3}{\,5\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[\mathbb{E}(Y\mid X)\bigr]&=\int_{0}^{1}\mathbb{E}(Y\mid X=x)\,f_{\sssig X}(x)\,dx\\[0.45em]
&=\int_{0}^{1}\frac{\,6x+3\,}{12x+4}\cdot\Bigl[\frac{6}{\,5\,}x+\frac{2}{\,5\,}\Bigr]dx\\[0.45em]
&=\int_{0}^{1}\Bigl[\frac{\,6x+3\,}{10}\Bigr]dx\\[0.45em]
&=\Bigl[\frac{3}{\,10\,}x^{2}+\frac{3}{\,10\,}x\Bigr]_{0}^{1}=\frac{3}{\,5\,}
\end{aligned}
$$

</div>

</div>

<div id="ex-beta-conditional-expectation" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.22</div>

<div lang="en" markdown="1">
Suppose that $Y$ has a $\mathrm{Gamma}\bigl(\frac{\,k\,}{2},\frac{\,k\,}{2}\bigr)$ distribution with <span class="text-nowrap">$k>0$,</span> where the gamma density and the gamma function are

$$
\begin{gathered}
f_{\sssig Y}(y)=\frac{\,\lambda^{\alpha}\,y^{\alpha-1}\,e^{-\lambda y}\,}{\Gamma(\alpha)},\ \alpha>0,\ \lambda>0\\[0.55em]
\Gamma(\alpha)=\int_{0}^{\infty}t^{\alpha-1}e^{-t}\,dt,\ \alpha>0
\end{gathered}
$$

and the conditional distribution of $X$ given $Y=y$ is <span class="text-nowrap">$\mathcal{N}\bigl(0,\frac{1}{y}\bigr)$.</span>

<ol class="topic-list-paren">
  <li>Show that the pdf of $X$ is
<div class="topic-math-layout topic-math-layout--desktop">
$$
f_{\sssig X}(x)=\frac{\Gamma\bigl(\frac{k+1}{2}\bigr)}{\sqrt{\pi k}\,\Gamma\bigl(\frac{k}{2}\bigr)}\frac{1}{\bigl(1+\frac{x^{2}}{k}\bigr)^{\frac{k+1}{2}}},\ x\in\mathbb{R}
$$
</div>
<div class="topic-math-layout topic-math-layout--mobile">
$$
\begin{aligned}
f_{\sssig X}(x)&=\frac{\Gamma\bigl(\frac{k+1}{2}\bigr)}{\sqrt{\pi k}\,\Gamma\bigl(\frac{k}{2}\bigr)}\frac{1}{\bigl(1+\frac{x^{2}}{k}\bigr)^{\frac{k+1}{2}}},\\[0.45em]
&\quad x\in\mathbb{R}
\end{aligned}
$$
</div>
  </li>
  <li>Show that $\mathbb{E}(X)\neq\mathbb{E}\bigl[\mathbb{E}(X\mid Y)\bigr]$ in the case <span class="text-nowrap">$k=1$.</span></li>
</ol>
</div>

(1) 由 $Y\sim\mathrm{Gamma}\bigl(\frac{\,k\,}{2},\frac{\,k\,}{2}\bigr)$ 可知
{: .topic-paren-item}

$$
f_{\sssig Y}(y)=\frac{\,k^{\frac{\,k\,}{2}}\,y^{\frac{\,k\,}{2}-1}\,e^{-\frac{\,k\,}{2}y}\,}{\Gamma\bigl(\frac{\,k\,}{2}\bigr)2^{\frac{\,k\,}{2}}},\ y>0
$$

又由 $X\mid(Y=y)\sim\mathcal{N}\bigl(0,\frac{1}{y}\bigr)$ 可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X\mid Y}(x\mid y)=\frac{\sqrt{y}}{\sqrt{2\pi}}\exp\left\lbrace\frac{\,-yx^{2}\,}{2}\right\rbrace,\ x\in\mathbb{R},\ y>0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig X\mid Y}(x\mid y)&=\frac{\sqrt{y}}{\sqrt{2\pi}}\exp\left\lbrace\frac{\,-yx^{2}\,}{2}\right\rbrace,\\[0.45em]
&\quad x\in\mathbb{R},\ y>0
\end{aligned}
$$

</div>

故
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f_{\sssig XY}(x,y)&=f_{\sssig X\mid Y}(x\mid y)\,f_{\sssig Y}(y)\\[0.45em]
&=\frac{\,k^{\frac{\,k\,}{2}}\,y^{\frac{\,k\,}{2}-1}\,e^{-\frac{\,k\,}{2}y}\,}{\Gamma\bigl(\frac{\,k\,}{2}\bigr)2^{\frac{\,k\,}{2}}}\times\frac{\sqrt{y}}{\sqrt{2\pi}}\exp\left\lbrace\frac{\,-yx^{2}\,}{2}\right\rbrace\\[0.45em]
&=\frac{k^{\frac{k}{2}}}{\Gamma\bigl(\frac{k}{2}\bigr)\sqrt{2\pi}\,2^{\frac{k}{2}}}\,y^{\frac{k+1}{2}-1}\\[0.2em]
&\quad \times\exp\left\lbrace-\Bigl(\frac{k}{2}+\frac{\,x^{2}\,}{2}\Bigr)y\right\rbrace,\ x\in\mathbb{R},\ y>0
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig XY}(x,y)&=f_{\sssig X\mid Y}(x\mid y)\,f_{\sssig Y}(y)\\[0.45em]
&=\frac{\,k^{\frac{\,k\,}{2}}\,y^{\frac{\,k\,}{2}-1}\,e^{-\frac{\,k\,}{2}y}\,}{\Gamma\bigl(\frac{\,k\,}{2}\bigr)2^{\frac{\,k\,}{2}}}\\[0.2em]
&\qquad\times\frac{\sqrt{y}}{\sqrt{2\pi}}\exp\left\lbrace\frac{\,-yx^{2}\,}{2}\right\rbrace\\[0.45em]
&=\frac{k^{\frac{k}{2}}}{\Gamma\bigl(\frac{k}{2}\bigr)\sqrt{2\pi}\,2^{\frac{k}{2}}}\,y^{\frac{k+1}{2}-1}\\[0.2em]
&\qquad\times\exp\left\lbrace-\Bigl(\frac{k}{2}+\frac{\,x^{2}\,}{2}\Bigr)y\right\rbrace,\\[0.2em]
&\quad x\in\mathbb{R},\ y>0
\end{aligned}
$$

</div>

再對 $y$ 積分即得
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\Longrightarrow f_{\sssig X}(x)&=\int_{0}^{\infty}f_{\sssig XY}(x,y)\,dy\\[0.45em]
&=\frac{k^{\frac{k}{2}}}{\Gamma\bigl(\frac{k}{2}\bigr)\sqrt{2\pi}\,2^{\frac{k}{2}}}\int_{0}^{\infty}y^{\frac{k+1}{2}-1}\,\exp\left\lbrace-\Bigl(\frac{k}{2}+\frac{\,x^{2}\,}{2}\Bigr)y\right\rbrace\,dy\\[0.45em]
&=\frac{k^{\frac{k}{2}}}{\Gamma\bigl(\frac{k}{2}\bigr)\sqrt{2\pi}\,2^{\frac{k}{2}}}\,\frac{\Gamma\bigl(\frac{k+1}{2}\bigr)}{\bigl(\frac{k}{2}+\frac{\,x^{2}\,}{2}\bigr)^{\frac{k+1}{2}}}\\[0.45em]
&=\frac{\Gamma\bigl(\frac{k+1}{2}\bigr)}{\sqrt{\pi k}\,\Gamma\bigl(\frac{k}{2}\bigr)}\frac{1}{\bigl(1+\frac{x^{2}}{k}\bigr)^{\frac{k+1}{2}}},\ x\in\mathbb{R}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\Longrightarrow f_{\sssig X}(x)&=\int_{0}^{\infty}f_{\sssig XY}(x,y)\,dy\\[0.45em]
&=\frac{k^{\frac{k}{2}}}{\Gamma\bigl(\frac{k}{2}\bigr)\sqrt{2\pi}\,2^{\frac{k}{2}}}\int_{0}^{\infty}y^{\frac{k+1}{2}-1}\\[0.2em]
&\qquad\exp\left\lbrace-\Bigl(\frac{k}{2}+\frac{\,x^{2}\,}{2}\Bigr)y\right\rbrace\,dy\\[0.45em]
&=\frac{k^{\frac{k}{2}}}{\Gamma\bigl(\frac{k}{2}\bigr)\sqrt{2\pi}\,2^{\frac{k}{2}}}\,\frac{\Gamma\bigl(\frac{k+1}{2}\bigr)}{\bigl(\frac{k}{2}+\frac{\,x^{2}\,}{2}\bigr)^{\frac{k+1}{2}}}\\[0.45em]
&=\frac{\Gamma\bigl(\frac{k+1}{2}\bigr)}{\sqrt{\pi k}\,\Gamma\bigl(\frac{k}{2}\bigr)}\frac{1}{\bigl(1+\frac{x^{2}}{k}\bigr)^{\frac{k+1}{2}}},\ x\in\mathbb{R}
\end{aligned}
$$

</div>

(2) 由 (1) 可知，當 $k=1$ 的時候
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X}(x)=\frac{1}{\sqrt{\pi}\,\Gamma\bigl(\frac{1}{2}\bigr)}\frac{1}{\,1+x^{2}\,}=\frac{1}{\,\pi\bigl(1+x^{2}\bigr)\,},\ x\in\mathbb{R}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig X}(x)&=\frac{1}{\sqrt{\pi}\,\Gamma\bigl(\frac{1}{2}\bigr)}\frac{1}{\,1+x^{2}\,}\\[0.45em]
&=\frac{1}{\,\pi\bigl(1+x^{2}\bigr)\,},\ x\in\mathbb{R}
\end{aligned}
$$

</div>

則 $\mathbb{E}(X)$ 不存在，但由於 $\mathbb{E}(X\mid Y=y)=0$ 這個結果，可得
{: .topic-paren-cont}

$$
\Longrightarrow\ \mathbb{E}\bigl[\mathbb{E}(X\mid Y)\bigr]=0
$$

故知道
{: .topic-paren-cont}

$$
\mathbb{E}(X)\neq\mathbb{E}\bigl[\mathbb{E}(X\mid Y)\bigr]
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

第二小題使用到的分配是 $t(1)$ 分配，也是 $\mathrm{Cauchy}(0,1)$ 分配。這個分配的特色是，雖然他是一個單峰對稱於 $0$ 的分配，但由於尾部機率過厚，其一階絕對動差是不存在的，這也導致期望值不存在，讀者不妨以 $\mathbb{E}\bigl(\lvert X\rvert\bigr)$ 的定義驗證看看。

</div>

<div id="ex-conditional-expectation-linear" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.23</div>

<div lang="en" markdown="1">
Suppose that $X$ and $Y$ are random variables for which <span class="text-nowrap">$\mathbb{E}(X)=0$,</span> $\mathrm{Var}(X)=4$ and <span class="text-nowrap">$\mathbb{E}(Y\mid X)=2-3X$.</span> Find $\mathbb{E}(Y)$ and <span class="text-nowrap">$\mathbb{E}(XY)$.</span>
</div>

由[雙重期望值定理](/lecture-notes/double-expectation-theorem/#thm-double-expectation)可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(Y)=\mathbb{E}\bigl[\mathbb{E}(Y\mid X)\bigr]=\mathbb{E}(2-3X)=2-3\,\mathbb{E}(X)=2
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(Y)&=\mathbb{E}\bigl[\mathbb{E}(Y\mid X)\bigr]=\mathbb{E}(2-3X)\\[0.45em]
&=2-3\,\mathbb{E}(X)=2
\end{aligned}
$$

</div>

又由條件期望值的性質知道

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(XY)=\mathbb{E}\bigl[\mathbb{E}(XY\mid X)\bigr]=\mathbb{E}\bigl[X\,\mathbb{E}(Y\mid X)\bigr]=\mathbb{E}\bigl(2X-3X^{2}\bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(XY)&=\mathbb{E}\bigl[\mathbb{E}(XY\mid X)\bigr]\\[0.45em]
&=\mathbb{E}\bigl[X\,\mathbb{E}(Y\mid X)\bigr]\\[0.45em]
&=\mathbb{E}\bigl(2X-3X^{2}\bigr)
\end{aligned}
$$

</div>

且題目已知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}(X)=\mathbb{E}\bigl(X^{2}\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}=\mathbb{E}\bigl(X^{2}\bigr)=4
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(X)&=\mathbb{E}\bigl(X^{2}\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}\\[0.45em]
&=\mathbb{E}\bigl(X^{2}\bigr)=4
\end{aligned}
$$

</div>

故所求為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(XY)=2\,\mathbb{E}(X)-3\,\mathbb{E}\bigl(X^{2}\bigr)=2\times 0-3\times 4=-12
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(XY)&=2\,\mathbb{E}(X)-3\,\mathbb{E}\bigl(X^{2}\bigr)\\[0.45em]
&=2\times 0-3\times 4=-12
\end{aligned}
$$

</div>

</div>

<div id="ex-miner-three-doors" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.24 <span lang="en">(The trapped miner problem)</span></div>

<div lang="en" markdown="1">
A miner is trapped in a mine in which there are three doors. The tunnel behind the first door brings him out to safety after $2$ hours of travel, the tunnel behind the second door brings him back to the mine after $3$ hours of travel, and the tunnel behind the third door brings him back to the mine after $5$ hours of travel. Suppose that on each occasion the miner is equally likely to pick any one of the three doors. Find the expected length of time until he reaches safety.
</div>

令 $X$ 表示礦工脫困所需要的時間，且由題目敘述可假設

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
Y=\left\lbrace
\begin{array}{c@{\quad}l}
1, & \text{選擇第一扇門}\\[0.3em]
2, & \text{選擇第二扇門}\\[0.3em]
3, & \text{選擇第三扇門}
\end{array}
\right.
\qquad\text{則}\qquad
f_{\sssig Y}(y)=\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{1}{\,3\,}, & y=1,2,3\\[0.8em]
0, & \text{o.w.}
\end{array}
\right.
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
Y&=\left\lbrace
\begin{array}{c@{}l}
1, & \text{選擇第一扇門}\\[0.3em]
2, & \text{選擇第二扇門}\\[0.3em]
3, & \text{選擇第三扇門}
\end{array}
\right.\\[0.9em]
\text{則}\ f_{\sssig Y}(y)&=\left\lbrace
\begin{array}{c@{}l}
\dfrac{1}{\,3\,}, & y=1,2,3\\[0.8em]
0, & \text{o.w.}
\end{array}
\right.
\end{aligned}
$$

</div>

依題目敘述可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\mathbb{E}(X\mid Y=1)=2,\ \ \mathbb{E}(X\mid Y=2)=\mathbb{E}(X+3)\\[0.45em]
\text{與}\ \mathbb{E}(X\mid Y=3)=\mathbb{E}(X+5)
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X\mid Y=1)&=2,\\[0.45em]
\mathbb{E}(X\mid Y=2)&=\mathbb{E}(X+3)\\[0.45em]
\text{與}\ \mathbb{E}(X\mid Y=3)&=\mathbb{E}(X+5)
\end{aligned}
$$

</div>

由[雙重期望值定理](/lecture-notes/double-expectation-theorem/#thm-double-expectation)可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\mathbb{E}\bigl[\mathbb{E}(X\mid Y)\bigr]=\sum_{y=1}^{3}\mathbb{E}(X\mid Y=y)\times f_{\sssig Y}(y)\\[0.45em]
&=2\times\frac{1}{\,3\,}+\mathbb{E}(X+3)\times\frac{1}{\,3\,}+\mathbb{E}(X+5)\times\frac{1}{\,3\,}\\[0.45em]
&=\frac{2}{\,3\,}+\bigl[\mathbb{E}(X)+3\bigr]\times\frac{1}{\,3\,}+\bigl[\mathbb{E}(X)+5\bigr]\times\frac{1}{\,3\,}\\[0.45em]
&=\frac{2}{\,3\,}\mathbb{E}(X)+\frac{\,10\,}{3}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\mathbb{E}\bigl[\mathbb{E}(X\mid Y)\bigr]\\[0.45em]
&=\sum_{y=1}^{3}\mathbb{E}(X\mid Y=y)\times f_{\sssig Y}(y)\\[0.45em]
&=2\times\frac{1}{\,3\,}+\mathbb{E}(X+3)\times\frac{1}{\,3\,}\\[0.2em]
&\qquad+\mathbb{E}(X+5)\times\frac{1}{\,3\,}\\[0.45em]
&=\frac{2}{\,3\,}+\bigl[\mathbb{E}(X)+3\bigr]\times\frac{1}{\,3\,}\\[0.2em]
&\qquad+\bigl[\mathbb{E}(X)+5\bigr]\times\frac{1}{\,3\,}\\[0.45em]
&=\frac{2}{\,3\,}\mathbb{E}(X)+\frac{\,10\,}{3}
\end{aligned}
$$

</div>

則所求為

$$
\Longrightarrow\ \mathbb{E}(X)=10
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這題是隨機過程 <span lang="en">(random process)</span> 中的一道重要入門題。

特別需要注意的是，若選擇的為第一道門，則該礦工經過 $2$ 小時後將直接走出礦坑，此即 $\mathbb{E}(X\mid Y=1)=2$ 這個結果；若選擇第二或第三道門，則因為經過 $3$ 及 $5$ 小時後會回到選擇點，且由於該礦工在選擇點時，總是均等機率地選擇其中一道門 (該礦工無法記憶上次的選擇)，故每次選擇時，平均而言，要再花掉的時間與尚未選擇時一模一樣，可是又因為已經浪費了 $3$ 及 $5$ 小時，故平均的脫困時間會分別**增加 $3$ 及 $5$ 小時**，此即 $\mathbb{E}(X\mid Y=2)$ $=\mathbb{E}(X+3)$ 與 $\mathbb{E}(X\mid Y=3)$ <span class="text-nowrap">$=\mathbb{E}(X+5)$。</span>

</div>

<div id="ex-coin-until-two-heads" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.25</div>

<div lang="en" markdown="1">
A coin whose probability of coming up heads is $0.5$ is flipped repeatedly until heads appears twice among the three most recent flips, and $N$ denotes the number of flips made. Find <span class="text-nowrap">$\mathbb{E}(N)$,</span> where $N=2$ whenever the first two flips both come up heads.
</div>

依照題目設定之規則，可令一輔助用之變數

$$
X=\left\lbrace
\begin{array}{c@{\quad}l}
1, & \text{前兩次結果為 HH}\\[0.3em]
2, & \text{前三次結果為 HTH}\\[0.3em]
3, & \text{前三次結果為 HTT}\\[0.3em]
4, & \text{第一次結果為 T}
\end{array}
\right.
$$

依照規則，可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\mathbb{E}(N\mid X=1)=2,\ \mathbb{E}(N\mid X=2)=3,\\[0.45em]
\mathbb{E}(N\mid X=3)=\mathbb{E}(N)+3,\ \mathbb{E}(N\mid X=4)=\mathbb{E}(N)+1
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(N\mid X=1)&=2,\\[0.45em]
\mathbb{E}(N\mid X=2)&=3,\\[0.45em]
\mathbb{E}(N\mid X=3)&=\mathbb{E}(N)+3,\\[0.45em]
\mathbb{E}(N\mid X=4)&=\mathbb{E}(N)+1
\end{aligned}
$$

</div>

且

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X=1)=\frac{1}{\,4\,},\ \mathbb{P}(X=2)=\frac{1}{\,8\,},\ \mathbb{P}(X=3)=\frac{1}{\,8\,},\ \mathbb{P}(X=4)=\frac{1}{\,2\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X=1)&=\frac{1}{\,4\,},\ \mathbb{P}(X=2)=\frac{1}{\,8\,},\\[0.45em]
\mathbb{P}(X=3)&=\frac{1}{\,8\,},\ \mathbb{P}(X=4)=\frac{1}{\,2\,}
\end{aligned}
$$

</div>

則由[雙重期望值定理](/lecture-notes/double-expectation-theorem/#thm-double-expectation)可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(N)&=\mathbb{E}\bigl[\mathbb{E}(N\mid X)\bigr]=\sum_{x=1}^{4}\mathbb{E}(N\mid X=x)\,\mathbb{P}(X=x)\\[0.45em]
&=2\times\frac{1}{\,4\,}+3\times\frac{1}{\,8\,}+\bigl[\mathbb{E}(N)+3\bigr]\times\frac{1}{\,8\,}+\bigl[\mathbb{E}(N)+1\bigr]\times\frac{1}{\,2\,}\\[0.45em]
&=\frac{5}{\,8\,}\mathbb{E}(N)+\frac{\,14\,}{8}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(N)&=\mathbb{E}\bigl[\mathbb{E}(N\mid X)\bigr]\\[0.45em]
&=\sum_{x=1}^{4}\mathbb{E}(N\mid X=x)\,\mathbb{P}(X=x)\\[0.45em]
&=2\times\frac{1}{\,4\,}+3\times\frac{1}{\,8\,}\\[0.2em]
&\qquad+\bigl[\mathbb{E}(N)+3\bigr]\times\frac{1}{\,8\,}\\[0.2em]
&\qquad+\bigl[\mathbb{E}(N)+1\bigr]\times\frac{1}{\,2\,}\\[0.45em]
&=\frac{5}{\,8\,}\mathbb{E}(N)+\frac{\,14\,}{8}
\end{aligned}
$$

</div>

則所求為

$$
\Longrightarrow\ \mathbb{E}(N)=\frac{\,14\,}{3}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

由於規則的原因，本題需要先羅列前幾次的結果進行討論，用以確定接下來的實驗是否還有需要進行，以及討論其是否將累積之正面歸零，這種討論的步驟，是這種題型的關鍵。

</div>

至此，讀者應該已經熟悉[雙重期望值定理](/lecture-notes/double-expectation-theorem/#thm-double-expectation)，是如何以加權平均的方式做出邊際期望值。然而，讀者也許會猜想，這樣透過加權平均得到邊際產物的過程，能不能用在分配本身身上呢？事實上是可以的，這正是接下來要介紹的定理。

## 本篇小結

[Example 3.21](#ex-conditional-expectation-density) 是[雙重期望值定理](/lecture-notes/double-expectation-theorem/#thm-double-expectation)最直接的一種用法。由聯合機率密度函數先積出 <span class="text-nowrap">$f_{\sssig X}(x)$，</span>再由[條件機率密度函數](/lecture-notes/conditional-distributions/#def-conditional-pdf)求得 $\mathbb{E}(Y\mid X=x)=\frac{6x+3}{12x+4}$ 這一條迴歸函數，最後以 $f_{\sssig X}(x)$ 為權重把這個條件期望值平均起來，得到 $\mathbb{E}(Y)=\frac{3}{5}$ 這個值。[Example 3.22](#ex-beta-conditional-expectation) 則提醒讀者定理的前提: $X$ 在給定 $Y=y$ 之下為常態分配、$Y$ 本身為伽瑪分配，兩者合起來所得的邊際密度在 $k=1$ 時是 $t(1)$ 分配，也就是 $\mathrm{Cauchy}(0,1)$ 分配，其尾部機率過厚而使一階絕對動差不存在，$\mathbb{E}(X)$ 因而不存在；但 $\mathbb{E}(X\mid Y=y)$ 恆為 <span class="text-nowrap">$0$，</span>因此 $\mathbb{E}\bigl[\mathbb{E}(X\mid Y)\bigr]$ 仍然算得出來，兩者於是不相等。

[Example 3.23](#ex-conditional-expectation-linear) 所給的條件只有 $\mathbb{E}(X)=0$ 與 $\mathrm{Var}(X)=4$ 兩個數值，以及 $\mathbb{E}(Y\mid X)$ $=$ $2-3X$ 這一條迴歸函數，並不知道分配是什麼，但[雙重期望值定理](/lecture-notes/double-expectation-theorem/#thm-double-expectation)只需要對這條迴歸函數取一次期望值便得到 <span class="text-nowrap">$\mathbb{E}(Y)=2$；</span>再配合把 $X$ 視為常數提到條件期望值之外的性質，$\mathbb{E}(XY)$ 也可以化成 $\mathbb{E}(2X-3X^{2})$ 而求得 $-12$ 這個值。

[Example 3.24](#ex-miner-three-doors) 與 [Example 3.25](#ex-coin-until-two-heads) 是同一種型態。先設一個輔助變數把整個實驗切成幾種情形，礦工題切成三扇門、銅板題切成前幾次的結果，接著寫出每一種情形之下的條件期望值。由於部分情形會使實驗回到原先的狀態，所求的期望值在等式的兩側同時出現，解一條方程式便得到 $\mathbb{E}(X)=10$ 與 <span class="text-nowrap">$\mathbb{E}(N)=\frac{14}{3}$。</span>礦工題之所以是 $\mathbb{E}(X\mid Y=2)=\mathbb{E}(X+3)$ 而不是別的式子，關鍵在於該礦工無法記憶上次的選擇，回到選擇點之後平均還要花掉的時間與尚未選擇時一模一樣，只是白白多花了 $3$ 小時；銅板題則要先羅列前幾次的結果，才能確定實驗是否還要進行，以及累積的正面是否歸零。

[下一篇](/lecture-notes/conditional-law-of-total-probability/)把同一套加權平均用在分配本身上，也就是[隨機變數](/lecture-notes/random-variables-and-pmf/#def-random-variable)版本的全機率定理，並以三道例題示範它在機率計算上的用法。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
