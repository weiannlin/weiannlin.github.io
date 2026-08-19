---
title: "交叉動差與聯合動差母函數"
subtitle: "Cross Moments and the Joint Moment Generating Function"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 17
order: 317
permalink: /teaching-topics/cross-moments-joint-mgf/
date: 2026-08-13
published: false
excerpt: "動差可以描述一個機率分配的各種特徵，而 $\\mathbb{E}(X^nY^m)$ 這種交叉動差描述的則是兩個隨機變數共同變化的各種特徵。生成交叉動差的工具，是把單變數的動差母函數推廣到兩個變數之後所得到的聯合動差母函數: 它對 $t_1$ 微分 $n$ 次、對 $t_2$ 微分 $m$ 次再代入零，即得 $(n+m)$ 階交叉動差；只把 $t_1$ 與 $t_2$ 其中一個代入零，則得到該變數的邊際動差母函數。本篇並以兩道例題示範它的用法，一道由聯合動差母函數求共變異數，另一道由展開式認出離散型的聯合與邊際機率質量函數。"
---

[上一篇](/teaching-topics/wald-identity-gamblers-ruin/)以[沃德等式](/teaching-topics/wald-identity-gamblers-ruin/#thm-wald-identity)處理了加總的項數本身也是[隨機變數](/teaching-topics/random-variables-and-pmf/#def-random-variable)的情形。本篇轉而處理兩個隨機變數共同變化的情況。

我們在第二章曾以[母體動差](/teaching-topics/moment-system/#def-population-moment)描述單一機率分配的各種特徵，也曾以[動差母函數](/teaching-topics/moment-generating-functions/#def-mgf)協助生成各階的原動差。本篇先把動差推廣為交叉動差，再把動差母函數推廣為聯合動差母函數，接著看聯合動差母函數如何生成各階交叉動差、又如何轉為邊際動差母函數，最後以兩道例題示範它在計算上的用法。

## 交叉動差

<div id="def-cross-moment" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 3.14 (交差動差, cross moment)</div>

令 $(X, Y)$ 為二元隨機變數，且 <span class="text-nowrap">$n, m \in \mathbb{N}$，</span>則

$\mathbb{E}\bigl(X^nY^m\bigr)$ 被稱為 $X$ 與 $Y$ 的 **$(n+m)$ 階交叉動差 ($(n+m)$-th cross moment)**

</div>

動差能夠用來描述一個機率分配的各種特徵，而交叉動差 (cross moment) 也有同樣的功用，主要是用來描述 **$X$ 與 $Y$ 共同變化的各種特徵**。

## 聯合動差母函數

在介紹單變數隨機變數的動差時，我們曾引入 mgf 來協助我們生成各階的原動差。事實上，mgf 的功能，當然不僅止於生成一個變數的動差，像上面所定義的交叉動差，也能夠由 mgf 協助生成，但是在介紹 mgf 要如何生成兩個變數的交叉動差之前，我們首先要定義兩個或多個隨機變數的**聯合動差母函數 <span lang="en">(joint moment-generating function, joint mgf)</span>**。

<div id="def-joint-mgf" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 3.15 (聯合動差母函數, joint mgf)</div>

若 $X$ 與 $Y$ 為**離散**變數，且對任意正數 <span class="text-nowrap">$h$，</span>下列[期望值](/teaching-topics/expectation/#def-expectation)在 $-h < t_1, t_2 < h$ 皆存在，則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
M_{\sssig XY}(t_1, t_2)=\mathbb{E}\bigl(e^{t_1X+t_2Y}\bigr)=\mathop{\sum\sum}\limits_{(x,y)\in\mathcal{R}_{\sssig XY}}e^{t_1x+t_2y}p_{\sssig XY}(x,y)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig XY}(t_1, t_2)&=\mathbb{E}\bigl(e^{t_1X+t_2Y}\bigr)\\[0.45em]
&=\mathop{\sum\sum}\limits_{(x,y)\in\mathcal{R}_{\sssig XY}}e^{t_1x+t_2y}p_{\sssig XY}(x,y)
\end{aligned}
$$

</div>

被定義為 $X$ 與 $Y$ 之**聯合動差母函數 (joint mgf)**

若 $X$ 與 $Y$ 為連續變數，且對任意正數 <span class="text-nowrap">$h$，</span>下列期望值在 $-h < t_1, t_2 < h$ 皆存在，則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
M_{\sssig XY}(t_1, t_2)=\mathbb{E}\bigl(e^{t_1X+t_2Y}\bigr)=\iint_{(x,y)\in\mathcal{R}_{\sssig XY}}e^{t_1x+t_2y}f_{\sssig XY}(x,y)\,dx\,dy
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig XY}(t_1, t_2)&=\mathbb{E}\bigl(e^{t_1X+t_2Y}\bigr)\\[0.45em]
&=\iint_{(x,y)\in\mathcal{R}_{\sssig XY}}e^{t_1x+t_2y}\\[0.2em]
&\quad f_{\sssig XY}(x,y)\,dx\,dy
\end{aligned}
$$

</div>

被定義為 $X$ 與 $Y$ 之**聯合動差母函數**

</div>

聯合動差母函數與單變數的 mgf 相同，並不是任何時候都存在。一個 joint mgf 必須在 $-h < t_1, t_2 < h$ 的區間內皆有定義才存在，並且一旦 joint mgf 存在，即**保證了該二個隨機變數的各階交叉動差都存在**。

## 由聯合動差母函數生成交叉動差

<div id="thm-generate-cross-moment" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 3.13 (聯合動差母函數生成交叉動差, cross moments from a joint mgf)</div>

若 $X$ 與 $Y$ 為二隨機變數，其聯合動差母函數 $M_{\sssig XY}(t_1, t_2)$ 存在，則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\left.\frac{\partial^{n+m}M_{\sssig XY}(t_1, t_2)}{\partial t_1^{n}\,\partial t_2^{m}}\right|_{t_1=t_2=0}=\mathbb{E}\bigl(X^nY^m\bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\left.\frac{\partial^{n+m}M_{\sssig XY}(t_1, t_2)}{\partial t_1^{n}\,\partial t_2^{m}}\right|_{t_1=t_2=0}&=\mathbb{E}\bigl(X^nY^m\bigr)
\end{aligned}
$$

</div>

</div>

這個定理的證明是 [Theorem 2.21](/teaching-topics/moment-generating-functions/#thm-mgf-generates-moments) 的簡單推廣，故將這個定理的證明省略。有興趣的讀者可自行嘗試推導。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

[Theorem 3.13](#thm-generate-cross-moment) 說明了 joint mgf 如何生出兩個隨機變數之間的各階交叉動差。一個簡單的應用是當 $n=m=1$ 時，我們會得到 <span class="text-nowrap">$\mathbb{E}(XY)$，</span>也就是 $X$ 與 $Y$ 的二階交叉動差，這個交叉動差在後續的小節所介紹的[共變異數](/teaching-topics/covariance/#def-covariance) <span lang="en">(covariance)</span> 會起到關鍵的作用。

</div>

## 由聯合動差母函數取得邊際動差母函數

此外，joint mgf 當然也可以只生成其中一個變數的特徵，因為 joint mgf 能夠輕易轉為**邊際動差母函數 <span lang="en">(marginal mgf)</span>**，詳見下列定理。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

邊際動差母函數即為邊際分配的 mgf。

</div>

<div id="thm-marginal-mgf" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 3.14 (由聯合動差母函數取得邊際動差母函數, marginal mgf from a joint mgf)</div>

若 $X$ 與 $Y$ 為二隨機變數，則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
M_{\sssig XY}(t_1, 0)=\mathbb{E}\bigl(e^{t_1X+0\cdot Y}\bigr)=\mathbb{E}\bigl(e^{t_1X}\bigr)=M_{\sssig X}(t_1)\\[0.55em]
M_{\sssig XY}(0, t_2)=\mathbb{E}\bigl(e^{0\cdot X+t_2Y}\bigr)=\mathbb{E}\bigl(e^{t_2Y}\bigr)=M_{\sssig Y}(t_2)
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig XY}(t_1, 0)&=\mathbb{E}\bigl(e^{t_1X+0\cdot Y}\bigr)\\[0.3em]
&=\mathbb{E}\bigl(e^{t_1X}\bigr)=M_{\sssig X}(t_1)\\[0.7em]
M_{\sssig XY}(0, t_2)&=\mathbb{E}\bigl(e^{0\cdot X+t_2Y}\bigr)\\[0.3em]
&=\mathbb{E}\bigl(e^{t_2Y}\bigr)=M_{\sssig Y}(t_2)
\end{aligned}
$$

</div>

</div>

<div class="topic-proof" markdown="1">
**Proof.**

我們僅以連續型證明第一個情況，其他情況同理可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{\sssig XY}(t_1, 0)&=\mathbb{E}\Bigl(e^{t_1X+0\cdot Y}\Bigr)=\mathbb{E}\bigl(e^{t_1X}\bigr)=\int_{-\infty}^{\infty}\!\!\int_{-\infty}^{\infty}e^{t_1x}f_{\sssig XY}(x, y)\,dx\,dy\\[0.45em]
&=\int_{-\infty}^{\infty}e^{t_1x}\biggl[\int_{-\infty}^{\infty}f_{\sssig XY}(x, y)\,dy\biggr]\,dx=\int_{-\infty}^{\infty}e^{t_1x}f_{\sssig X}(x)\,dx=M_{\sssig X}(t_1)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig XY}(t_1, 0)&=\mathbb{E}\Bigl(e^{t_1X+0\cdot Y}\Bigr)=\mathbb{E}\bigl(e^{t_1X}\bigr)\\[0.45em]
&=\int_{-\infty}^{\infty}\!\!\int_{-\infty}^{\infty}e^{t_1x}f_{\sssig XY}(x, y)\,dx\,dy\\[0.45em]
&=\int_{-\infty}^{\infty}e^{t_1x}\biggl[\int_{-\infty}^{\infty}f_{\sssig XY}(x, y)\,dy\biggr]\,dx\\[0.45em]
&=\int_{-\infty}^{\infty}e^{t_1x}f_{\sssig X}(x)\,dx=M_{\sssig X}(t_1)
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

當然，若是 <span class="text-nowrap">$X\indep Y$，</span>若且唯若我們有 $M_{\sssig XY}(t_1, t_2)$ $=$ $M_{\sssig X}(t_1)\,M_{\sssig Y}(t_2)$ 的結果，讀者應可自行嘗試推導。

</div>

## 由聯合動差母函數求共變異數與[聯合機率質量函數](/teaching-topics/random-vectors-joint-pmf/#def-joint-pmf)

<div id="ex-joint-mgf-two-variables" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.35</div>

<div lang="en" markdown="1">
Suppose that the random variables $X_1$ and $X_2$ have the joint moment-generating function

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
M_{\sssig X_1X_2}(t_1, t_2)=(1-t_1+2t_2)^{-4}(1-t_1)^{-5}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig X_1X_2}(t_1, t_2)&=(1-t_1+2t_2)^{-4}(1-t_1)^{-5}
\end{aligned}
$$

</div>

Determine the covariance of $X_1$ and <span class="text-nowrap">$X_2$.</span>
</div>

由於 $\operatorname{Cov}(X_1, X_2)$ $=$ $\mathbb{E}(X_1X_2)-\mathbb{E}(X_1)\mathbb{E}(X_2)$

故先計算 $\mathbb{E}(X_1X_2)$ 與 <span class="text-nowrap">$\mathbb{E}(X_1)$、</span>$\mathbb{E}(X_2)$

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X_1X_2)&=\left.\frac{\partial^{2}M_{\sssig X_1X_2}(t_1, t_2)}{\partial t_1\,\partial t_2}\right|_{t_1=t_2=0}=\left.\frac{\partial}{\partial t_1}\biggl[\frac{\partial M_{\sssig X_1X_2}(t_1, t_2)}{\partial t_2}\biggr]\right|_{t_1=t_2=0}\\[0.45em]
&=\left.\frac{\partial}{\partial t_1}\biggl[\frac{\partial\,(1-t_1+2t_2)^{-4}(1-t_1)^{-5}}{\partial t_2}\biggr]\right|_{t_1=t_2=0}=\left.\frac{\partial}{\partial t_1}\biggl[-8\Bigl((1-t_1+2t_2)(1-t_1)\Bigr)^{-5}\biggr]\right|_{t_1=t_2=0}\\[0.45em]
&=\left.-40\Bigl((1-t_1+2t_2)^{-6}(1-t_1)^{-5}+(1-t_1+2t_2)^{-5}(1-t_1)^{-6}\Bigr)\right|_{t_1=t_2=0}=-80
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X_1X_2)&=\left.\frac{\partial^{2}M_{\sssig X_1X_2}(t_1, t_2)}{\partial t_1\,\partial t_2}\right|_{t_1=t_2=0}\\[0.45em]
&=\left.\frac{\partial}{\partial t_1}\biggl[\frac{\partial M_{\sssig X_1X_2}(t_1, t_2)}{\partial t_2}\biggr]\right|_{t_1=t_2=0}\\[0.45em]
&=\frac{\partial}{\partial t_1}\biggl[\frac{\partial\,(1-t_1+2t_2)^{-4}(1-t_1)^{-5}}{\partial t_2}\biggr]\\[0.15em]
&\qquad\qquad\qquad\qquad\qquad\biggr|_{t_1=t_2=0}\\[0.45em]
&=\frac{\partial}{\partial t_1}\biggl[-8\Bigl((1-t_1+2t_2)(1-t_1)\Bigr)^{-5}\biggr]\\[0.15em]
&\qquad\qquad\qquad\qquad\qquad\biggr|_{t_1=t_2=0}\\[0.45em]
&=-40\Bigl((1-t_1+2t_2)^{-6}(1-t_1)^{-5}\\[0.25em]
&\quad\ +(1-t_1+2t_2)^{-5}(1-t_1)^{-6}\Bigr)\biggr|_{t_1=t_2=0}\\[0.45em]
&=-80
\end{aligned}
$$

</div>

又 $M_{\sssig X_1}(t_1)$ $=$ $M_{\sssig X_1X_2}(t_1, 0)$ $=$ <span class="text-nowrap">$(1-t_1)^{-9}$，</span>$M_{\sssig X_2}(t_2)$ $=$ $M_{\sssig X_1X_2}(0, t_2)$ $=$ $(1+2t_2)^{-4}$

則可知

<div class="topic-math-layout topic-math-layout--desktop topic-math-follow-before" markdown="1">

$$
\begin{gathered}
\mathbb{E}(X_1)=\left.\frac{\partial M_{\sssig X_1}(t_1)}{\partial t_1}\right|_{t_1=0}=-9(1-0)^{-10}\times(-1)=9\\[0.55em]
\mathbb{E}(X_2)=\left.\frac{\partial M_{\sssig X_2}(t_2)}{\partial t_2}\right|_{t_2=0}=-4(1+0)^{-5}\times 2=-8
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile topic-math-follow-before" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X_1)&=\left.\frac{\partial M_{\sssig X_1}(t_1)}{\partial t_1}\right|_{t_1=0}\\[0.25em]
&=-9(1-0)^{-10}\times(-1)=9\\[0.7em]
\mathbb{E}(X_2)&=\left.\frac{\partial M_{\sssig X_2}(t_2)}{\partial t_2}\right|_{t_2=0}\\[0.25em]
&=-4(1+0)^{-5}\times 2=-8
\end{aligned}
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop topic-math-follow" markdown="1">

$$
\Longrightarrow\ \operatorname{Cov}(X_1, X_2)=\mathbb{E}(X_1X_2)-\mathbb{E}(X_1)\mathbb{E}(X_2)=-80-9\times(-8)=-8
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile topic-math-follow" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ \operatorname{Cov}(X_1, X_2)&=\mathbb{E}(X_1X_2)-\mathbb{E}(X_1)\mathbb{E}(X_2)\\[0.45em]
&=-80-9\times(-8)=-8
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

共變異數的定義及算法在稍後即會提到。

</div>

<div id="ex-joint-mgf-covariance" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.36</div>

<div lang="en" markdown="1">
Suppose that the two random variables $X$ and $Y$ have the joint moment-generating function

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
M_{\sssig XY}(t_1, t_2)=\mathbb{E}\Bigl(e^{t_1X+t_2Y}\Bigr)=\biggl[\frac{1}{\,3\,}(e^{t_1+t_2}+1)+\frac{1}{\,6\,}(e^{t_1}+e^{t_2})\biggr]^{2}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig XY}(t_1, t_2)&=\mathbb{E}\Bigl(e^{t_1X+t_2Y}\Bigr)\\[0.3em]
&=\biggl[\frac{1}{\,3\,}(e^{t_1+t_2}+1)+\frac{1}{\,6\,}(e^{t_1}+e^{t_2})\biggr]^{2}
\end{aligned}
$$

</div>

Find the joint and marginal density functions of $X$ and <span class="text-nowrap">$Y$.</span>
</div>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{\sssig XY}(t_1, t_2)&=\mathbb{E}\Bigl(e^{t_1X+t_2Y}\Bigr)=\biggl[\frac{1}{\,3\,}(e^{t_1+t_2}+1)+\frac{1}{\,6\,}(e^{t_1}+e^{t_2})\biggr]^{2}\\[0.45em]
&=\frac{1}{\,9\,}e^{2t_1+2t_2}+\frac{1}{\,9\,}e^{2t_1+t_2}+\frac{1}{\,9\,}e^{t_1+2t_2}+\frac{5}{\,18\,}e^{t_1+t_2}\\[0.45em]
&\quad +\frac{1}{\,36\,}e^{2t_1}+\frac{1}{\,36\,}e^{2t_2}+\frac{1}{\,9\,}e^{t_1}+\frac{1}{\,9\,}e^{t_2}+\frac{1}{\,9\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig XY}(t_1, t_2)&=\mathbb{E}\Bigl(e^{t_1X+t_2Y}\Bigr)\\[0.45em]
&=\biggl[\frac{1}{\,3\,}(e^{t_1+t_2}+1)+\frac{1}{\,6\,}(e^{t_1}+e^{t_2})\biggr]^{2}\\[0.45em]
&=\frac{1}{\,9\,}e^{2t_1+2t_2}+\frac{1}{\,9\,}e^{2t_1+t_2}\\[0.3em]
&\qquad+\frac{1}{\,9\,}e^{t_1+2t_2}+\frac{5}{\,18\,}e^{t_1+t_2}\\[0.3em]
&\qquad+\frac{1}{\,36\,}e^{2t_1}+\frac{1}{\,36\,}e^{2t_2}\\[0.3em]
&\qquad+\frac{1}{\,9\,}e^{t_1}+\frac{1}{\,9\,}e^{t_2}+\frac{1}{\,9\,}
\end{aligned}
$$

</div>

由[動差母函數的唯一性](/teaching-topics/uniqueness-of-the-mgf/#thm-mgf-uniqueness)可知，$X$ 與 $Y$ 具聯合與[邊際機率質量函數](/teaching-topics/random-vectors-joint-pmf/#def-marginal-pmf)如下

| $Y\backslash X$ | $0$ | $1$ | $2$ | $p_{\sssig Y}(y)$ |
| :---: | :---: | :---: | :---: | :---: |
| $2$ | $\frac{1}{\,36\,}$ | $\frac{1}{\,9\,}$ | $\frac{1}{\,9\,}$ | $\frac{1}{\,4\,}$ |
| $1$ | $\frac{1}{\,9\,}$ | $\frac{5}{\,18\,}$ | $\frac{1}{\,9\,}$ | $\frac{1}{\,2\,}$ |
| $0$ | $\frac{1}{\,9\,}$ | $\frac{1}{\,9\,}$ | $\frac{1}{\,36\,}$ | $\frac{1}{\,4\,}$ |
| $p_{\sssig X}(x)$ | $\frac{1}{\,4\,}$ | $\frac{1}{\,2\,}$ | $\frac{1}{\,4\,}$ | $1$ |
{: .topic-table--joint-pmf}

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

事實上，joint mgf 與 marginal mgf 一樣，能夠刻畫整個分配的所有特徵，因此也具有如 [Theorem 2.23](/teaching-topics/uniqueness-of-the-mgf/#thm-mgf-uniqueness) 的唯一性定理能夠使用，特別是在離散型[隨機向量](/teaching-topics/random-vectors-joint-pmf/#def-random-vector)上，辨認方式完全類同過去，即將 $X, Y$ 的 joint mgf $M_{\sssig XY}(t_1, t_2)$ $=$ $\sum_{(x, y)\in\mathbb{R}^{2}}e^{t_1x+t_2y}\,p_{\sssig XY}(x,y)$ 展開，看成是 $p_{\sssig 1}e^{a_{11}\,t_1+a_{12}\,t_2}$ $+$ $...$ $+$ $p_{\sssig n}e^{a_{n1}\,t_1+a_{n2}\,t_2}$ 的形式，並認出其分配為

$$
p_{\sssig XY}(x,y)=\left\lbrace
\begin{array}{c@{\quad}l}
p_{\sssig 1}, & (x,y)=(a_{11}, a_{12})\\[0.6em]
\vdots & \ \ \ \ \vdots\\[0.6em]
p_{\sssig n}, & (x,y)=(a_{n1}, a_{n2})
\end{array}
\right.
$$

</div>

## 本篇小結

[Definition 3.14](#def-cross-moment) 把單變數的動差推廣為 $\mathbb{E}(X^nY^m)$ 這種交叉動差，用來描述 $X$ 與 $Y$ 共同變化的各種特徵；[Definition 3.15](#def-joint-mgf) 則把動差母函數推廣為聯合動差母函數，離散型以聯合機率質量函數加權求和、連續型以[聯合機率密度函數](/teaching-topics/joint-probability-density-functions/#def-joint-pdf)加權積分。與單變數的 mgf 相同，joint mgf 必須在 $-h < t_1, t_2 < h$ 的整個區間內皆有定義才算存在，而一旦它存在，各階交叉動差也就都跟著存在。

生成的方式由 [Theorem 3.13](#thm-generate-cross-moment) 給出。對 $t_1$ 微分 $n$ 次、對 $t_2$ 微分 $m$ 次，再代入 <span class="text-nowrap">$t_1=t_2=0$，</span>所得即為 $(n+m)$ 階交叉動差。其中 $n=m=1$ 的情形給出 $\mathbb{E}(XY)$ 這個量，它是[下一篇](/teaching-topics/covariance/)定義共變異數時所需的關鍵一項。[Theorem 3.14](#thm-marginal-mgf) 則指出，只要把 $t_1$ 與 $t_2$ 其中一個代入 <span class="text-nowrap">$0$，</span>該變數在指數上的那一項就整個消去，剩下的正是另一個變數自己的動差母函數；證明只需把聯合機率密度函數對其中一個變數積分，得到的就是[邊際機率密度函數](/teaching-topics/marginal-probability-density-functions/#def-marginal-pdf)。

兩道例題示範它在計算上的用法。[Example 3.35](#ex-joint-mgf-two-variables) 先對 $t_2$ 再對 $t_1$ 微分求得 <span class="text-nowrap">$\mathbb{E}(X_1X_2)=-80$，</span>再由 $M_{\sssig X_1X_2}(t_1, 0)$ 與 $M_{\sssig X_1X_2}(0, t_2)$ 取得兩個邊際動差母函數，各微分一次得到 $9$ 與 <span class="text-nowrap">$-8$，</span>合起來即得共變異數為 <span class="text-nowrap">$-8$。</span>[Example 3.36](#ex-joint-mgf-covariance) 則把聯合動差母函數的平方展開成九項，每一項的係數就是一個機率、指數上的兩個係數就是一組取值，由[動差母函數的唯一性](/teaching-topics/uniqueness-of-the-mgf/#thm-mgf-uniqueness)即可把整張聯合與邊際機率質量函數的表填出來。離散型的辨認方式與單變數時完全相同，差別只在指數上由一個變數變成兩個。

[下一篇](/teaching-topics/covariance/)正式給出共變異數的定義，並說明它與二階交叉動差 $\mathbb{E}(XY)$ 之間的關係。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
