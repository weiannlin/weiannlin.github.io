---
title: "幾何分配與無記憶性"
subtitle: "The Geometric Distribution and the Memoryless Property"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 4
topic: 4
order: 404
permalink: /teaching-topics/ch4-p04-candidate/
date: 2026-08-12
published: false
excerpt: "幾何分配記錄的是伯努利實驗一直進行到第一次成功為止所需要的實驗次數，其機率函數的前後項比值恆為失敗機率，驗證機率函數合法與推導期望值、變異數、動差母函數所依靠的工具便是幾何級數。本篇先給出幾何級數，再給出幾何分配的定義與完整推導，並說明以失敗次數計數的另一種版本。接著證明幾何分配的無記憶性: 已知實驗次數超過 $a$ 次之後，再多超過 $b$ 次的機率，與重新開始做實驗而超過 $b$ 次的機率相同。最後給出兩個延伸結果: 非負整數值的隨機變數只要具備無記憶性便服從幾何分配，以及兩個獨立幾何變數的極小值仍為幾何分配。"
---

[上一篇](/teaching-topics/ch4-p03-candidate/)把伯努利實驗的兩個類別推廣為 $k$ 個互斥類別，得到多項分配。本篇回到只有成功與失敗兩類的情形，但改變記錄的對象: [二項分配](/teaching-topics/ch4-p02-candidate/#def-binomial)先固定實驗次數，再數其中成功了幾次；本篇的幾何分配則反過來，一直做下去直到第一次成功為止，記錄的是所需要的實驗次數。

驗證二項分配的機率函數合法時，我們用的是 [Theorem 2.18](/teaching-topics/moment-system/#thm-binomial) 的二項式定理；幾何分配的機率函數前後項比值固定，所需要的工具因而是[幾何級數](#thm-geometric-series)。本篇先由這個級數談起，再給出幾何分配的定義並完整推導其期望值、變異數與動差母函數，接著證明幾何分配的[無記憶性](#thm-memoryless)，說明這個性質反過來也足以決定分配，最後給出兩個獨立幾何變數取極小值的結果。

## 幾何級數

<div id="thm-geometric-series" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 4.3 (幾何級數, geometric series)</div>

**幾何級數 (<span lang="en">geometric series</span>**，或譯**等比級數)** 是下列的級數:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
a+ar+ar^{2}+\ldots+ar^{n-1}=\sum_{k=1}^{n}ar^{k-1}=\frac{\,a(1-r^{n})\,}{1-r}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&a+ar+ar^{2}+\ldots+ar^{n-1}\\[0.45em]
&\quad =\sum_{k=1}^{n}ar^{k-1}=\frac{\,a(1-r^{n})\,}{1-r}
\end{aligned}
$$

</div>

其中 $a$ 稱為首項、$n$ 是項數、$r$ 是公比。

這個級數在 $n\to\infty$ 時被稱為**無窮等比級數 <span lang="en">(infinite geometric series)</span>**，且該級數收斂 <span lang="en">(converge)</span> 的等價條件為 <span class="text-nowrap">$0<\lvert r\rvert<1$，</span>並且其結果收斂至 <span class="text-nowrap">$\frac{a}{\,1-r\,}$，</span>此即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
a+ar+ar^{2}+\ldots=\sum_{k=1}^{\infty}ar^{k-1}=\frac{a}{\,1-r\,},\ 0<\lvert r\rvert<1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&a+ar+ar^{2}+\ldots=\sum_{k=1}^{\infty}ar^{k-1}\\[0.45em]
&\quad =\frac{a}{\,1-r\,},\ 0<\lvert r\rvert<1
\end{aligned}
$$

</div>

</div>

幾何級數在高中數學當中是一定會提及的級數之一，在微積分中也是很重要的級數。由於前後項之間的比值恆為公比 <span class="text-nowrap">$r$，</span>故又被稱為等比級數，而這個前後項固定比值的特色，將在幾何分配 <span lang="en">(geometric distribution)</span> 中被應用。

## 幾何分配

<div id="def-geometric" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 4.6 (幾何分配, geometric distribution)</div>

**適用範圍**:

令 $X$ 表進行伯努利實驗，直到出現第一次成功實驗所需要的**實驗次數**。

**值域範圍**:

$$
\mathcal{R}_{\sssig X}=\lbrace\,1,\ldots,\infty\,\rbrace
$$

**表示式**:

$$
X\sim\mathrm{Geo}(p)
$$

**參數與參數範圍**:

$0<p<1$ 為伯努利實驗中，成功類的發生機率。

**機率函數**:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
p_{\sssig X}(x)=p\,(1-p)^{x-1}=p\,q^{x-1},\ x=1,\ldots,\infty
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig X}(x)&=p\,(1-p)^{x-1}=p\,q^{x-1},\\[0.45em]
&\quad\ x=1,\ldots,\infty
\end{aligned}
$$

</div>

其中，$q=1-p$ 為失敗類發生的機率。

**期望值、變異數、動差母函數**:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\mathbb{E}(X)=\frac{1}{\,p\,},\quad \mathrm{Var}(X)=\frac{\,1-p\,}{p^{2}}=\frac{q}{\,p^{2}\,}\\[0.6em]
M_{\sssig X}(t)=\frac{pe^{t}}{\,1-(1-p)e^{t}\,}=\frac{pe^{t}}{\,1-qe^{t}\,},\ t<-\ln q
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{E}(X)=\frac{1}{\,p\,}\\[0.5em]
\mathrm{Var}(X)=\frac{\,1-p\,}{p^{2}}=\frac{q}{\,p^{2}\,}\\[0.5em]
M_{\sssig X}(t)=\frac{pe^{t}}{\,1-(1-p)e^{t}\,}\\[0.3em]
=\frac{pe^{t}}{\,1-qe^{t}\,},\ t<-\ln q
\end{gathered}
$$

</div>

</div>

幾何分配有一些地方需要注意:

(1) 我們證明其機率函數為一個合法的機率函數與期望值、變異數及動差母函數如下:
{: .topic-paren-item}

<div class="topic-proof" markdown="1">
**Proof.** 先驗證機率函數的加總為 <span class="text-nowrap">$1$，</span>即

$$
\sum_{x\in\mathcal{R}_{\sssig X}}p_{\sssig X}(x)=\sum_{x=1}^{\infty}p\,q^{x-1}=\frac{p}{\,1-q\,}=1
$$

接著求期望值，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\sum_{x=1}^{\infty}x\,p\,q^{x-1}=p\sum_{x=1}^{\infty}x\,q^{x-1}=p\sum_{x=1}^{\infty}\frac{d}{\,d\,q\,}\bigl(q^{x}\bigr)=p\frac{d}{\,d\,q\,}\biggl(\sum_{x=1}^{\infty}q^{x}\biggr)\\[0.45em]
&=p\frac{d}{\,d\,q\,}\biggl(\frac{q}{\,1-q\,}\biggr)=p\biggl[\frac{1}{(1-q)^{2}}\biggr]=\frac{p}{\,p^{2}\,}=\frac{1}{\,p\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\sum_{x=1}^{\infty}x\,p\,q^{x-1}=p\sum_{x=1}^{\infty}x\,q^{x-1}\\[0.45em]
&=p\sum_{x=1}^{\infty}\frac{d}{\,d\,q\,}\bigl(q^{x}\bigr)=p\frac{d}{\,d\,q\,}\biggl(\sum_{x=1}^{\infty}q^{x}\biggr)\\[0.45em]
&=p\frac{d}{\,d\,q\,}\biggl(\frac{q}{\,1-q\,}\biggr)=p\biggl[\frac{1}{(1-q)^{2}}\biggr]\\[0.45em]
&=\frac{p}{\,p^{2}\,}=\frac{1}{\,p\,}
\end{aligned}
$$

</div>

又可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[X(X-1)\bigr]&=\sum_{x=1}^{\infty}x(x-1)\,p\,q^{x-1}=p\,q\sum_{x=1}^{\infty}x(x-1)\,q^{x-2}\\[0.45em]
&=p\,q\sum_{x=1}^{\infty}\frac{d^{2}}{\,d\,q^{2}\,}\bigl(q^{x}\bigr)=p\,q\,\frac{d^{2}}{\,d\,q^{2}\,}\biggl(\sum_{x=1}^{\infty}q^{x}\biggr)\\[0.45em]
&=p\,q\frac{d^{2}}{\,d\,q^{2}\,}\biggl(\frac{q}{\,1-q\,}\biggr)=p\,q\,\frac{d}{\,d\,q\,}\biggl[\frac{1}{(1-q)^{2}}\biggr]\\[0.45em]
&=p\,q\biggl[\frac{2}{(1-q)^{3}}\biggr]=\frac{2q}{\,p^{2}\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}\bigl[X(X-1)\bigr]\\[0.45em]
&\quad =\sum_{x=1}^{\infty}x(x-1)\,p\,q^{x-1}\\[0.45em]
&\quad =p\,q\sum_{x=1}^{\infty}x(x-1)\,q^{x-2}\\[0.45em]
&\quad =p\,q\sum_{x=1}^{\infty}\frac{d^{2}}{\,d\,q^{2}\,}\bigl(q^{x}\bigr)\\[0.45em]
&\quad =p\,q\,\frac{d^{2}}{\,d\,q^{2}\,}\biggl(\sum_{x=1}^{\infty}q^{x}\biggr)\\[0.45em]
&\quad =p\,q\frac{d^{2}}{\,d\,q^{2}\,}\biggl(\frac{q}{\,1-q\,}\biggr)\\[0.45em]
&\quad =p\,q\,\frac{d}{\,d\,q\,}\biggl[\frac{1}{(1-q)^{2}}\biggr]\\[0.45em]
&\quad =p\,q\biggl[\frac{2}{(1-q)^{3}}\biggr]=\frac{2q}{\,p^{2}\,}
\end{aligned}
$$

</div>

由此可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\bigl(X^{2}\bigr)=\mathbb{E}\bigl[X(X-1)\bigr]+\mathbb{E}(X)=\frac{\,2(1-p)\,}{p^{2}}+\frac{1}{\,p\,}=\frac{\,2-p\,}{p^{2}}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl(X^{2}\bigr)&=\mathbb{E}\bigl[X(X-1)\bigr]+\mathbb{E}(X)\\[0.45em]
&=\frac{\,2(1-p)\,}{p^{2}}+\frac{1}{\,p\,}=\frac{\,2-p\,}{p^{2}}
\end{aligned}
$$

</div>

則變異數為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}(X)=\mathbb{E}\bigl(X^{2}\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}=\frac{\,2-p\,}{p^{2}}-\Bigl(\frac{1}{\,p\,}\Bigr)^{2}=\frac{\,1-p\,}{p^{2}}=\frac{q}{\,p^{2}\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(X)&=\mathbb{E}\bigl(X^{2}\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}\\[0.45em]
&=\frac{\,2-p\,}{p^{2}}-\Bigl(\frac{1}{\,p\,}\Bigr)^{2}\\[0.45em]
&=\frac{\,1-p\,}{p^{2}}=\frac{q}{\,p^{2}\,}
\end{aligned}
$$

</div>

最後求動差母函數，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
M_{\sssig X}(t)&=\mathbb{E}\bigl(e^{tX}\bigr)=\sum_{x=1}^{\infty}e^{tx}\,p\,q^{x-1}=\frac{p}{\,q\,}\sum_{x=1}^{\infty}\bigl(qe^{t}\bigr)^{x}\\[0.45em]
&=\frac{p}{\,q\,}\cdot\frac{qe^{t}}{\,1-qe^{t}\,}=\frac{pe^{t}}{\,1-qe^{t}\,},\ t<-\ln q
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig X}(t)&=\mathbb{E}\bigl(e^{tX}\bigr)=\sum_{x=1}^{\infty}e^{tx}\,p\,q^{x-1}\\[0.45em]
&=\frac{p}{\,q\,}\sum_{x=1}^{\infty}\bigl(qe^{t}\bigr)^{x}\\[0.45em]
&=\frac{p}{\,q\,}\cdot\frac{qe^{t}}{\,1-qe^{t}\,}\\[0.45em]
&=\frac{pe^{t}}{\,1-qe^{t}\,},\ t<-\ln q
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

(2) 幾何分配的定義可以得到以下幾個延伸性質:
{: .topic-paren-item}

若令 $Y$ 表示進行伯努利實驗，至第一次成功所需要的**失敗次數**，則
{: .topic-paren-cont}

$$
Y=X-1
$$

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個性質的直觀意義在於，幾何分配所進行的伯努利實驗中，只會有一次成功，並且必定是最後一次實驗，故若進行了 $X$ 次實驗，則前面的 $X-1$ 次必定都屬於失敗實驗。

</div>

由於二種定義的幾何分配表示式相同，為了區分二種定義，有些書籍便以**實驗幾何**與**失敗幾何**代稱，或寫出其值域範圍以便區分。失敗幾何 $Y$ 與實驗幾何 $X$ 略有不同:
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\mathcal{R}_{\sssig Y}=\lbrace\,\mathbf{0},1,\ldots,\infty\,\rbrace\\[0.7em]
p_{\sssig Y}(y)=p\,(1-p)^{y}=p\,q^{y},\ y=0,1,\ldots,\infty\\[0.7em]
\mathbb{E}(Y)=\mathbb{E}(X-1)=\mathbb{E}(X)-1=\frac{1}{\,p\,}-1=\frac{\,1-p\,}{p}=\frac{q}{\,p\,}\\[0.7em]
\mathrm{Var}(Y)=\mathrm{Var}(X-1)=\mathrm{Var}(X)\\[0.7em]
M_{\sssig Y}(t)=\mathbb{E}\bigl(e^{tY}\bigr)=\mathbb{E}\bigl[e^{t(X-1)}\bigr]=\mathbb{E}\bigl(e^{tX}\bigr)\,e^{-t}\\[0.3em]
=e^{-t}M_{\sssig X}(t)=\frac{p}{\,1-qe^{t}\,},\ t<-\ln q
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\mathcal{R}_{\sssig Y}=\lbrace\,\mathbf{0},1,\ldots,\infty\,\rbrace
$$

$$
\begin{aligned}
p_{\sssig Y}(y)&=p\,(1-p)^{y}=p\,q^{y},\\[0.45em]
&\quad\ y=0,1,\ldots,\infty
\end{aligned}
$$

$$
\begin{aligned}
\mathbb{E}(Y)&=\mathbb{E}(X-1)=\mathbb{E}(X)-1\\[0.45em]
&=\frac{1}{\,p\,}-1=\frac{\,1-p\,}{p}=\frac{q}{\,p\,}
\end{aligned}
$$

$$
\mathrm{Var}(Y)=\mathrm{Var}(X-1)=\mathrm{Var}(X)
$$

$$
\begin{aligned}
M_{\sssig Y}(t)&=\mathbb{E}\bigl(e^{tY}\bigr)=\mathbb{E}\bigl[e^{t(X-1)}\bigr]\\[0.45em]
&=\mathbb{E}\bigl(e^{tX}\bigr)\,e^{-t}=e^{-t}M_{\sssig X}(t)\\[0.45em]
&=\frac{p}{\,1-qe^{t}\,},\ t<-\ln q
\end{aligned}
$$

</div>

## 無記憶性

<div id="thm-memoryless" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 4.4 (無記憶性, memoryless property)</div>

若 <span class="text-nowrap">$X\sim\mathrm{Geo}(p)$，</span>則

$$
\mathbb{P}(X>a+b\mid X>a)=\mathbb{P}(X>b)
$$

其中 $a,b\in\mathbb{N}$

</div>

<div class="topic-proof" markdown="1">
**Proof.** 對任意 <span class="text-nowrap">$x\in\mathbb{N}$，</span>我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X>x)=\sum_{t=x+1}^{\infty}p\,(1-p)^{t-1}=\frac{\,p\,(1-p)^{x}\,}{\,1-(1-p)\,}=(1-p)^{x}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X>x)&=\sum_{t=x+1}^{\infty}p\,(1-p)^{t-1}\\[0.45em]
&=\frac{\,p\,(1-p)^{x}\,}{\,1-(1-p)\,}=(1-p)^{x}
\end{aligned}
$$

</div>

則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X>a+b\mid X>a)&=\frac{\,\mathbb{P}(X>a+b,\ X>a)\,}{\mathbb{P}(X>a)}=\frac{\,\mathbb{P}(X>a+b)\,}{\mathbb{P}(X>a)}\\[0.45em]
&=\frac{\,(1-p)^{a+b}\,}{(1-p)^{a}}=(1-p)^{b}=\mathbb{P}(X>b)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(X>a+b\mid X>a)\\[0.45em]
&\quad =\frac{\,\mathbb{P}(X>a+b,\ X>a)\,}{\mathbb{P}(X>a)}\\[0.45em]
&\quad =\frac{\,\mathbb{P}(X>a+b)\,}{\mathbb{P}(X>a)}=\frac{\,(1-p)^{a+b}\,}{(1-p)^{a}}\\[0.45em]
&\quad =(1-p)^{b}=\mathbb{P}(X>b)
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

無記憶性從式子上來看，其意義是一但確定實驗次數超過 $a$ 次，則實驗次數超過 $a+b$ 次的機率，和重新進行伯努利實驗而實驗次數超過 $b$ 次的機率一樣。而應用在實際情況的直觀意義則是，不論已經失敗了幾次，都像是「遺忘了過去的結果而重新進行」一樣，並不會因失敗而學習到什麼經驗或有什麼改變。[^gambler]

讀者可以特別注意到，此處所使用的 $\mathbb{P}(X>x)$ 即表示「在第 $x$ 次的實驗仍未成功」的機率。

</div>

<!-- ref-point: 待第三章第 13 篇 (雙重期望值的例題，其中礦工三扇門一題為書稿
     mathstatch3.tex 第 2453 行的 prob 環境，可見編號 範例 3.24，anchor 為
     #ex-miner-three-doors) 發布後，將下面腳註中的「Example 3.24」改為指向該
     anchor 的站內連結。 -->

[^gambler]: 這個敘述便與 Example 3.24 相同，該礦工並無法回想起上次的選擇，**每次選擇都宛若重新開始**，此即無記憶性；事實上，這個性質也可以用來解釋**賭徒謬誤 <span lang="en">(The Gambler’s Fallacy)</span>**，也就是賭徒常常認為「連輸一段時間之後必有大爆發之時」的謬誤。

事實上，幾何分配是唯二具有無記憶性的分配，且是離散分配中唯一具有這個性質的分配；另一個具有無記憶性的分配是**指數分配 <span lang="en">(exponential distribution)</span>**。

幾何分配有一個很特殊的性質是，$p_{\sssig X}(a)$ 與 $p_{\sssig X}(a+1)$ 的比例是固定的，這個特色其實從 pmf 就可以看出來，並不算是需要特別的觀察才能發現的特色，但這正是導致無記憶性的關鍵，因為這種前後比例固定的分配，在無記憶性的推導中，會使得 $\mathbb{P}(X>a+b)$ 與 $\mathbb{P}(X>a)$ 的比例同樣也會是固定的，而這個比例便固定在 <span class="text-nowrap">$\mathbb{P}(X>b)$。</span>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

讀者應可以由推導無記憶性的證明發現，$p_{\sssig X}(a)$ 與 $p_{\sssig X}(a+1)$ 間固定的比例是成敗實驗的**失敗機率** <span class="text-nowrap">$(1-p)$，</span>而 $\mathbb{P}(X>a+b)$ 與 $\mathbb{P}(X>a)$ 之間的差異便在「必須多失敗 $b$ 次」，這個機率是 <span class="text-nowrap">$(1-p)^{b}$，</span>而等比的特色也導致這個機率恰巧等於 <span class="text-nowrap">$\mathbb{P}(X>b)$，</span>因此才能得到無記憶性的性質。

在稍後的小節講到指數分配時，我們會發現指數分配也有這個等比的特色，並且是連續分配中唯一具有這個特色的分配，因此這二個分配才會是唯二具有無記憶性的分配。

</div>

我們稍微在此打住。讀者不妨思考看看，既然幾何分配是因為其分配本身如此特別，才具有無記憶性的特色，那麼當我們確定有一個非負整數值的隨機變數具有無記憶性，我們可不可以反過來說明，這個隨機變數服從幾何分配呢? 答案是可以的，請見[下列定理](#thm-geometric-memoryless-converse)。

<div id="thm-geometric-memoryless-converse" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 4.5 (離散型無記憶性的逆敘述, converse of the memoryless property (discrete))</div>

若 $X$ 為一非負整數值的隨機變數，且已知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X>a+b\mid X>a)=\mathbb{P}(X>b),\ \forall a,b\in\mathbb{N}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(X>a+b\mid X>a)\\[0.45em]
&\quad =\mathbb{P}(X>b),\ \forall a,b\in\mathbb{N}
\end{aligned}
$$

</div>

則我們可知

$$
X\sim\mathrm{Geo}(p)
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.** 由已知條件，我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X>a+b\mid X>a)&=\frac{\,\mathbb{P}(X>a+b,\ X>a)\,}{\mathbb{P}(X>a)}=\frac{\,\mathbb{P}(X>a+b)\,}{\mathbb{P}(X>a)}\\[0.45em]
&=\mathbb{P}(X>b),\ \forall a,b\in\mathbb{N}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(X>a+b\mid X>a)\\[0.45em]
&\quad =\frac{\,\mathbb{P}(X>a+b,\ X>a)\,}{\mathbb{P}(X>a)}\\[0.45em]
&\quad =\frac{\,\mathbb{P}(X>a+b)\,}{\mathbb{P}(X>a)}\\[0.45em]
&\quad =\mathbb{P}(X>b),\ \forall a,b\in\mathbb{N}
\end{aligned}
$$

</div>

此即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X>a+b)=\mathbb{P}(X>a)\,\mathbb{P}(X>b),\ \forall a,b\in\mathbb{N}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(X>a+b)\\[0.45em]
&\quad =\mathbb{P}(X>a)\,\mathbb{P}(X>b),\ \forall a,b\in\mathbb{N}
\end{aligned}
$$

</div>

故對於任意的 <span class="text-nowrap">$k\in\mathbb{N}$，</span>我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X>k)&=\mathbb{P}(X>1)\,\mathbb{P}(X>k-1)=\bigl[\mathbb{P}(X>1)\bigr]^{2}\mathbb{P}(X>k-2)\\[0.45em]
&=\ldots=\bigl[\mathbb{P}(X>1)\bigr]^{k}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X>k)&=\mathbb{P}(X>1)\,\mathbb{P}(X>k-1)\\[0.45em]
&=\bigl[\mathbb{P}(X>1)\bigr]^{2}\mathbb{P}(X>k-2)\\[0.45em]
&=\ldots=\bigl[\mathbb{P}(X>1)\bigr]^{k}
\end{aligned}
$$

</div>

其中，若令 <span class="text-nowrap">$\mathbb{P}(X>1)=(1-p)$，</span>則我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
1-F_{\sssig X}(k)=\mathbb{P}(X>k)=(1-p)^{k}\\[0.6em]
\Longrightarrow\ F_{\sssig X}(x)=\mathbb{P}(X\leqslant x)=1-(1-p)^{x},\ x\in\mathbb{N}
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
1-F_{\sssig X}(k)=\mathbb{P}(X>k)=(1-p)^{k}\\[0.5em]
\Longrightarrow\ F_{\sssig X}(x)=\mathbb{P}(X\leqslant x)\\[0.3em]
=1-(1-p)^{x},\ x\in\mathbb{N}
\end{gathered}
$$

</div>

又可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
p_{\sssig X}(x)&=F_{\sssig X}(x)-F_{\sssig X}(x-1)=1-(1-p)^{x}-\Bigl[1-(1-p)^{x-1}\Bigr]\\[0.45em]
&=(1-p)^{x-1}\bigl[1-(1-p)\bigr]=p\,(1-p)^{x-1},\ x\in\mathbb{N}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig X}(x)&=F_{\sssig X}(x)-F_{\sssig X}(x-1)\\[0.45em]
&=1-(1-p)^{x}-\Bigl[1-(1-p)^{x-1}\Bigr]\\[0.45em]
&=(1-p)^{x-1}\bigl[1-(1-p)\bigr]\\[0.45em]
&=p\,(1-p)^{x-1},\ x\in\mathbb{N}
\end{aligned}
$$

</div>

故可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
X\sim\mathrm{Geo}(p),\ \text{其中}\ p=\mathbb{P}(X\leqslant1)=\mathbb{P}(X=1)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
X\sim\mathrm{Geo}(p),\\[0.4em]
\text{其中}\ p=\mathbb{P}(X\leqslant1)=\mathbb{P}(X=1)
\end{gathered}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個定理補足了關於無記憶性的雙向敘述，也就是說，爾後只要我們知道某個非負整數值的隨機變數服從幾何分配，若且唯若其具備無記憶性。

</div>

## 兩個獨立幾何分配的極小值

<div id="thm-min-of-geometrics" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 4.6 (兩個獨立幾何分配的極小值, minimum of two geometric variables)</div>

若 <span class="text-nowrap">$X\sim\mathrm{Geo}(p_1)\indep Y\sim\mathrm{Geo}(p_2)$，</span>則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\min\lbrace X,Y\rbrace\sim\mathrm{Geo}\bigl(p=1-(1-p_1)(1-p_2)\bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\min\lbrace X,Y\rbrace\\[0.4em]
\sim\mathrm{Geo}\bigl(p=1-(1-p_1)(1-p_2)\bigr)
\end{gathered}
$$

</div>

</div>

<div class="topic-proof" markdown="1">
**Proof.** 若令 <span class="text-nowrap">$Z=\min\lbrace X,Y\rbrace$，</span>則我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
F_{\sssig Z}(z)&=\mathbb{P}(Z\leqslant z)=\mathbb{P}\bigl(\min\lbrace X,Y\rbrace\leqslant z\bigr)=1-\mathbb{P}\bigl(\min\lbrace X,Y\rbrace>z\bigr)\\[0.45em]
&=1-\mathbb{P}(X>z,\ Y>z)=1-\mathbb{P}(X>z)\,\mathbb{P}(Y>z)\\[0.45em]
&=1-(1-p_1)^{z}(1-p_2)^{z}=1-\bigl[(1-p_1)(1-p_2)\bigr]^{z}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
F_{\sssig Z}(z)&=\mathbb{P}(Z\leqslant z)=\mathbb{P}\bigl(\min\lbrace X,Y\rbrace\leqslant z\bigr)\\[0.45em]
&=1-\mathbb{P}\bigl(\min\lbrace X,Y\rbrace>z\bigr)\\[0.45em]
&=1-\mathbb{P}(X>z,\ Y>z)\\[0.45em]
&=1-\mathbb{P}(X>z)\,\mathbb{P}(Y>z)\\[0.45em]
&=1-(1-p_1)^{z}(1-p_2)^{z}\\[0.45em]
&=1-\bigl[(1-p_1)(1-p_2)\bigr]^{z}
\end{aligned}
$$

</div>

又可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
p_{\sssig Z}(z)&=F_{\sssig Z}(z)-F_{\sssig Z}(z-1)\\[0.45em]
&=1-\bigl[(1-p_1)(1-p_2)\bigr]^{z}-\Bigl(1-\bigl[(1-p_1)(1-p_2)\bigr]^{z-1}\Bigr)\\[0.45em]
&=\bigl[1-(1-p_1)(1-p_2)\bigr]\bigl[(1-p_1)(1-p_2)\bigr]^{z-1},\ z\in\mathbb{N}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig Z}(z)&=F_{\sssig Z}(z)-F_{\sssig Z}(z-1)\\[0.45em]
&=1-\bigl[(1-p_1)(1-p_2)\bigr]^{z}\\[0.3em]
&\quad -\Bigl(1-\bigl[(1-p_1)(1-p_2)\bigr]^{z-1}\Bigr)\\[0.45em]
&=\bigl[1-(1-p_1)(1-p_2)\bigr]\\[0.3em]
&\quad \cdot\bigl[(1-p_1)(1-p_2)\bigr]^{z-1},\ z\in\mathbb{N}
\end{aligned}
$$

</div>

故可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
Z=\min\lbrace X,Y\rbrace\sim\mathrm{Geo}\bigl(p=1-(1-p_1)(1-p_2)\bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
Z=\min\lbrace X,Y\rbrace\\[0.4em]
\sim\mathrm{Geo}\bigl(p=1-(1-p_1)(1-p_2)\bigr)
\end{gathered}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<!-- ref-point: 書稿 mathstatch4.tex 第 742 行在下面這則 Note 上放了 \label{minGeo}，
     第 2016 行 (篇 11 指數分配的極小值) 以 \pageref 回指此處。篇 11 寫成之後，於該處
     接上指向本頁 #note-min-geometric-intuition 的站內連結。 -->

<div id="note-min-geometric-intuition" class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個定理背後具有非常直觀的意義，因為當我們關注的是 $X$ 與 $Y$ 當中較小者，事實上就好像我們在進行一系列的伯努利實驗，且只要 $X$ 或 $Y$ 所對應的成功條件，有任一者達成，即視為成功。

在如此的設定之下，所謂的「失敗類」，其發生條件應是在 $X$ 與 $Y$ 所對應的實驗中，皆出現失敗的現象，又因為 $X$ 與 $Y$ 所對應的實驗獨立，因此此處失敗類的機率必為 <span class="text-nowrap">$1-p=(1-p_1)(1-p_2)$，</span>反之，成功類的機率即為 <span class="text-nowrap">$p=1-(1-p_1)(1-p_2)$。</span>

</div>

## 本篇小結

[Theorem 4.3](#thm-geometric-series) 的幾何級數把首項為 <span class="text-nowrap">$a$、</span>公比為 $r$ 的 $n$ 項加總寫成 <span class="text-nowrap">$\frac{\,a(1-r^{n})\,}{1-r}$，</span>並在 $0<\lvert r\rvert<1$ 時使無窮項的加總收斂至 $\frac{a}{\,1-r\,}$ 這個值。前後項的比值恆為公比，正是幾何分配的機率函數所具備的特色。

[Definition 4.6](#def-geometric) 把 $X$ 定義為伯努利實驗做到第一次成功為止所需要的實驗次數，值域為 <span class="text-nowrap">$\lbrace\,1,\ldots,\infty\,\rbrace$，</span>機率函數為 <span class="text-nowrap">$p\,q^{x-1}$。</span>證明的四個步驟依序是: 以無窮等比級數驗證加總為 $1$ 這件事、把 $x\,q^{x-1}$ 看成 $q^{x}$ 的一階導數而求得 <span class="text-nowrap">$\mathbb{E}(X)=\frac{1}{\,p\,}$、</span>再以二階導數取得階乘動差 $\mathbb{E}\bigl[X(X-1)\bigr]=\frac{2q}{\,p^{2}\,}$ 進而算出 <span class="text-nowrap">$\mathrm{Var}(X)=\frac{q}{\,p^{2}\,}$，</span>最後直接由定義求得 <span class="text-nowrap">$M_{\sssig X}(t)=\frac{pe^{t}}{\,1-qe^{t}\,}$，</span>其定義域為 <span class="text-nowrap">$t<-\ln q$。</span>換一種計數方式，改記第一次成功之前的失敗次數，得到的 $Y=X-1$ 即為失敗幾何，其值域自 $0$ 起算，期望值降為 <span class="text-nowrap">$\frac{q}{\,p\,}$，</span>變異數不變，動差母函數則少了分子的 $e^{t}$ 這一項。

[Theorem 4.4](#thm-memoryless) 的無記憶性說的是 $\mathbb{P}(X>a+b\mid X>a)=\mathbb{P}(X>b)$ 這條等式: 已經失敗了 $a$ 次之後，實驗次數再多超過 $b$ 次的機率，與重新進行實驗而次數超過 $b$ 次的機率相同。證明的關鍵只有一步，即 $\mathbb{P}(X>x)=(1-p)^{x}$ 這個尾機率，兩個尾機率相除時 $(1-p)^{a}$ 恰好被約掉。追根究柢，$p_{\sssig X}(a)$ 與 $p_{\sssig X}(a+1)$ 之間固定的比值就是失敗機率 <span class="text-nowrap">$1-p$，</span>尾機率因而也等比，這才是無記憶性的來源。

[Theorem 4.5](#thm-geometric-memoryless-converse) 把這件事反過來說: 非負整數值的隨機變數只要具備無記憶性，尾機率便滿足 $\mathbb{P}(X>a+b)=\mathbb{P}(X>a)\,\mathbb{P}(X>b)$ 這條乘法關係，逐步遞推得到 $\mathbb{P}(X>k)=\bigl[\mathbb{P}(X>1)\bigr]^{k}$ 這個式子，令 $\mathbb{P}(X>1)=1-p$ 之後由 cdf 相減即還原出幾何分配的機率函數。兩個定理合起來，說明服從幾何分配與具備無記憶性互為充要條件。[Theorem 4.6](#thm-min-of-geometrics) 則指出兩個獨立幾何變數的極小值仍為幾何分配，成功機率為 <span class="text-nowrap">$1-(1-p_1)(1-p_2)$，</span>其直觀意義是把兩組實驗併看成一組，只要任一組成功即算成功，失敗類的機率因獨立而相乘。

[下一篇](/teaching-topics/ch4-p05-candidate/)以六道例題演練幾何分配的計算，其中包括第一次抽到指定貼紙所需要的次數、擲硬幣至第一次出現正面而所需次數為奇數的機率，以及把「等到湊齊若干種不同結果」的等待次數拆成數段幾何分配相加的作法。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
