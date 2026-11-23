---
title: "超幾何分配"
subtitle: "The Hypergeometric Distribution"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 4
topic: 7
order: 407
permalink: /lecture-notes/hypergeometric-distribution/
date: 2026-08-12
published: false
excerpt: "超幾何分配描述自有限母體取後不放回抽取 $n$ 個元素時，其中成功類的個數。本篇運用汎德蒙等式驗證其機率質量函數並推導期望值與變異數，說明有限母體校正因子及改採取後放回時與二項分配的對應關係。"
---

[上一篇](/lecture-notes/negative-binomial-distribution/)的[負二項分配](/lecture-notes/negative-binomial-distribution/#def-negative-binomial)仍然建立在伯努利實驗之上，每一次實驗的成功機率固定，實驗與實驗之間也彼此獨立。本篇要處理的情形則不同。母體只有有限多個元素，而且抽出的元素不再放回，因此每抽一次，母體的組成就改變一次，成功類所佔的比例也隨之改變。在這樣的抽樣方式之下，抽出的元素中成功類的個數所服從的分配，即為本篇的超幾何分配。

驗證[二項分配](/lecture-notes/binomial-distribution/#def-binomial)的機率函數合法時，我們用的是 [Theorem 2.18](/lecture-notes/moment-system/#thm-binomial) 的二項式定理；在超幾何分配這裡，所需要的工具則是[汎德蒙等式](#thm-vandermonde-identity)。本篇因而先由這個等式談起，再依序給出超幾何實驗與超幾何分配的定義，接著證明其機率函數合法並推導期望值與變異數，最後以兩道例題作為演練。

## 汎德蒙等式

<div id="thm-vandermonde-identity" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 4.8 (汎德蒙等式, Vandermonde’s identity)</div>

$$
\binom{N}{n}=\sum_{x=0}^{n}\binom{K}{x}\binom{N-K}{n-x}
$$

其中 <span class="text-nowrap">$N\in\mathbb{N}$，</span>$K\in\lbrace\,0,1,\ldots,N\,\rbrace$ 且抽樣數滿足 $n\in\lbrace\,0,1,\ldots,N\,\rbrace$ 這組範圍。

</div>

<div class="topic-proof" markdown="1">
**Proof.**

考慮 $(1+x)^{K}\,(1+x)^{N-K}=(1+x)^{N}$ 這個等式，我們可以先將等號左邊依照二項式定理展開改寫為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
(1+x)^{K}(1+x)^{N-K}&=\left[\sum_{i=0}^{K}\binom{K}{i}x^{i}\right]\left[\sum_{j=0}^{N-K}\binom{N-K}{j}x^{j}\right]\\[0.45em]
&=\sum_{n=0}^{N}\left[\sum_{i=0}^{n}\binom{K}{i}\binom{N-K}{n-i}\right]x^{n}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&(1+x)^{K}(1+x)^{N-K}\\[0.3em]
&=\left[\sum_{i=0}^{K}\binom{K}{i}x^{i}\right]\left[\sum_{j=0}^{N-K}\binom{N-K}{j}x^{j}\right]\\[0.3em]
&=\sum_{n=0}^{N}\left[\sum_{i=0}^{n}\binom{K}{i}\binom{N-K}{n-i}\right]x^{n}
\end{aligned}
$$

</div>

而等號右邊則根據二項式定理可得

$$
(1+x)^{N}=\sum_{n=0}^{N}\binom{N}{n}x^{n}
$$

若比較 $x^{n}$ 之係數，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\binom{N}{n}=\sum_{i=0}^{n}\binom{K}{i}\binom{N-K}{n-i}=\sum_{x=0}^{n}\binom{K}{x}\binom{N-K}{n-x}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\binom{N}{n}&=\sum_{i=0}^{n}\binom{K}{i}\binom{N-K}{n-i}\\[0.3em]
&=\sum_{x=0}^{n}\binom{K}{x}\binom{N-K}{n-x}
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

## 超幾何實驗與超幾何分配

<div id="def-hypergeometric-experiment" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 4.8 (超幾何實驗, hypergeometric experiment)</div>

令一有限母體 <span lang="en">(finite population)</span> 中有 $N$ 個物品，可被分為互斥的「成功類」與「失敗類」，並令成功類物品有 $K$ 個，失敗類物品有 $N-K$ 個。若採取後不放回 <span lang="en">(sampling without replacement)</span> 方式從中抽取 $n$ 個物品，則稱此實驗為超幾何實驗 <span lang="en">(hypergeometric experiment)</span>。

</div>

超幾何實驗可視為 $n$ 次伯努利實驗改採取後不放回的版本，各事件的機率可依古典機率的組合數直接點算。在此實驗下，所抽出的 $n$ 個物品中「成功類」出現的次數即服從超幾何分配 <span lang="en">(hypergeometric distribution)</span>，定義如下。

<div id="def-hypergeometric" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 4.9 (超幾何分配, hypergeometric distribution)</div>

**適用範圍**:

超幾何分配可以描述滿足以下條件的母體在特定條件抽樣時的行為:

- 具有 $N$ 個元素的有限母體中可分為成敗二類，其中成功類具有 $K$ 個元素，失敗類有 $N-K$ 個。
- 針對上述母體以取後不放回的方式抽取 $n$ 個元素，則定義 $X$ 以表示這 $n$ 個元素中成功類的個數。

**值域範圍**:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathcal{R}_{\sssig X}=\lbrace\,\mathrm{max}(0,n+K-N),\ldots,\mathrm{min}(n,K)\,\rbrace
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathcal{R}_{\sssig X}=\lbrace\,&\mathrm{max}(0,n+K-N),\ldots,\\[0.25em]
&\mathrm{min}(n,K)\,\rbrace
\end{aligned}
$$

</div>

**表示式**:

$$
X\sim\mathrm{Hyper}(N,\ K,\ n)
$$

**參數與參數範圍**:

$N\in\mathbb{N}$ 為母體中元素之總數

$K\in\lbrace\,0,1,\ldots,N\,\rbrace$ 為母體中屬於成功類的元素數量

$n\in\lbrace\,0,1,\ldots,N\,\rbrace$ 為抽取元素數量

**機率函數**:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
p_{\sssig X}(x)=\frac{\binom{K}{x}\binom{N-K}{n-x}}{\binom{N}{n}},\ x=\mathrm{max}(0,n+K-N),\ldots,\mathrm{min}(n,K)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig X}(x)&=\frac{\binom{K}{x}\binom{N-K}{n-x}}{\binom{N}{n}},\\[0.35em]
&\quad x=\mathrm{max}(0,n+K-N),\ldots,\\[0.25em]
&\qquad\ \mathrm{min}(n,K)
\end{aligned}
$$

</div>

**期望值、變異數**:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(X)=n\Bigl(\frac{K}{N}\Bigr),\quad \mathrm{Var}(X)=n\Bigl(\frac{K}{N}\Bigr)\Bigl(1-\frac{K}{N}\Bigr)\Bigl(\frac{N-n}{N-1}\Bigr)\ \ (N\geqslant2)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\mathbb{E}(X)=n\Bigl(\frac{K}{N}\Bigr)
$$

$$
\begin{aligned}
\mathrm{Var}(X)&=n\Bigl(\frac{K}{N}\Bigr)\Bigl(1-\frac{K}{N}\Bigr)\Bigl(\frac{N-n}{N-1}\Bigr)\\[0.25em]
&\qquad (N\geqslant2)
\end{aligned}
$$

</div>

(當 $N=1$ 時，<span class="text-nowrap">$\mathrm{Var}(X)=0$</span>。)

</div>

超幾何分配有一些地方需要注意:

(1) 我們證明其機率函數為一個合法的機率函數與期望值、變異數如下:
{: .topic-paren-item}

<div class="topic-proof" markdown="1">
**Proof.**

先驗證機率函數的加總為 <span class="text-nowrap">$1$，</span>即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\sum_{x\in\mathcal{R}_{\sssig X}}p_{\sssig X}(x)&=\sum_{x=0}^{n}\frac{\binom{K}{x}\binom{N-K}{n-x}}{\binom{N}{n}}=\frac{1}{\binom{N}{n}}\sum_{x=0}^{n}\binom{K}{x}\binom{N-K}{n-x}\\[0.45em]
&=\frac{\binom{N}{n}}{\binom{N}{n}}=1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\sum_{x\in\mathcal{R}_{\sssig X}}p_{\sssig X}(x)&=\sum_{x=0}^{n}\frac{\binom{K}{x}\binom{N-K}{n-x}}{\binom{N}{n}}\\[0.3em]
&=\frac{1}{\binom{N}{n}}\sum_{x=0}^{n}\binom{K}{x}\binom{N-K}{n-x}\\[0.3em]
&=\frac{\binom{N}{n}}{\binom{N}{n}}=1
\end{aligned}
$$

</div>

接著求期望值，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\sum_{x=0}^{n}x\,\frac{\binom{K}{x}\binom{N-K}{n-x}}{\binom{N}{n}}=\sum_{x=1}^{n}x\,\frac{K!\,\binom{N-K}{n-x}}{x!\,(K-x)!\,\binom{N}{n}}\\[0.45em]
&=K\sum_{x=1}^{n}\frac{(K-1)!\,\binom{N-K}{n-x}}{(x-1)!\,\bigl[(K-1)-(x-1)\bigr]!\,\binom{N}{n}}=K\sum_{x=1}^{n}\frac{\binom{K-1}{x-1}\binom{N-K}{n-x}}{\binom{N}{n}}\\[0.45em]
&=K\sum_{x=1}^{n}\frac{\binom{K-1}{x-1}\binom{N-K}{n-x}}{\frac{N}{n}\binom{N-1}{n-1}}=K\Bigl(\frac{n}{N}\Bigr)\sum_{y=0}^{n-1}\frac{\binom{K-1}{y}\binom{(N-1)-(K-1)}{(n-1)-y}}{\binom{N-1}{n-1}}\\[0.45em]
&=n\Bigl(\frac{K}{N}\Bigr)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}(X)\\[0.3em]
&=\sum_{x=0}^{n}x\,\frac{\binom{K}{x}\binom{N-K}{n-x}}{\binom{N}{n}}\\[0.3em]
&=\sum_{x=1}^{n}x\,\frac{K!\,\binom{N-K}{n-x}}{x!\,(K-x)!\,\binom{N}{n}}\\[0.3em]
&=K\sum_{x=1}^{n}\\[0.2em]
&\qquad\quad \frac{(K-1)!\,\binom{N-K}{n-x}}{(x-1)!\,\bigl[(K-1)-(x-1)\bigr]!\,\binom{N}{n}}\\[0.3em]
&=K\sum_{x=1}^{n}\frac{\binom{K-1}{x-1}\binom{N-K}{n-x}}{\binom{N}{n}}\\[0.3em]
&=K\sum_{x=1}^{n}\frac{\binom{K-1}{x-1}\binom{N-K}{n-x}}{\frac{N}{n}\binom{N-1}{n-1}}\\[0.3em]
&=K\Bigl(\frac{n}{N}\Bigr)\sum_{y=0}^{n-1}\frac{\binom{K-1}{y}\binom{(N-1)-(K-1)}{(n-1)-y}}{\binom{N-1}{n-1}}\\[0.3em]
&=n\Bigl(\frac{K}{N}\Bigr)
\end{aligned}
$$

</div>

上式中令 <span class="text-nowrap">$y=x-1$，</span>並由[汎德蒙等式](#thm-vandermonde-identity)可知

$$
\sum_{y=0}^{n-1}\frac{\binom{K-1}{y}\binom{(N-1)-(K-1)}{(n-1)-y}}{\binom{N-1}{n-1}}=1
$$

又可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[X(X-1)\bigr]&=\sum_{x=0}^{n}x(x-1)\,\frac{\binom{K}{x}\binom{N-K}{n-x}}{\binom{N}{n}}\\[0.45em]
&=\sum_{x=2}^{n}x(x-1)\,\frac{K!\,\binom{N-K}{n-x}}{x!\,(K-x)!\,\binom{N}{n}}\\[0.45em]
&=K(K-1)\sum_{x=2}^{n}\frac{(K-2)!\,\binom{N-K}{n-x}}{(x-2)!\,\bigl[(K-2)-(x-2)\bigr]!\,\binom{N}{n}}\\[0.45em]
&=K(K-1)\sum_{x=2}^{n}\frac{\binom{K-2}{x-2}\binom{(N-2)-(K-2)}{(n-2)-(x-2)}}{\frac{N(N-1)}{n(n-1)}\binom{N-2}{n-2}}\\[0.45em]
&=K(K-1)\frac{n(n-1)}{N(N-1)}\sum_{y=0}^{n-2}\frac{\binom{K-2}{y}\binom{(N-2)-(K-2)}{(n-2)-y}}{\binom{N-2}{n-2}}\\[0.45em]
&=K(K-1)\frac{n(n-1)}{N(N-1)}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}\bigl[X(X-1)\bigr]\\[0.3em]
&=\sum_{x=0}^{n}x(x-1)\,\frac{\binom{K}{x}\binom{N-K}{n-x}}{\binom{N}{n}}\\[0.3em]
&=\sum_{x=2}^{n}x(x-1)\,\frac{K!\,\binom{N-K}{n-x}}{x!\,(K-x)!\,\binom{N}{n}}\\[0.3em]
&=K(K-1)\sum_{x=2}^{n}\\[0.2em]
&\qquad\quad \frac{(K-2)!\,\binom{N-K}{n-x}}{(x-2)!\,\bigl[(K-2)-(x-2)\bigr]!\,\binom{N}{n}}\\[0.3em]
&=K(K-1)\sum_{x=2}^{n}\\[0.2em]
&\qquad\quad \frac{\binom{K-2}{x-2}\binom{(N-2)-(K-2)}{(n-2)-(x-2)}}{\frac{N(N-1)}{n(n-1)}\binom{N-2}{n-2}}\\[0.3em]
&=K(K-1)\frac{n(n-1)}{N(N-1)}\\[0.25em]
&\qquad\quad \sum_{y=0}^{n-2}\frac{\binom{K-2}{y}\binom{(N-2)-(K-2)}{(n-2)-y}}{\binom{N-2}{n-2}}\\[0.3em]
&=K(K-1)\frac{n(n-1)}{N(N-1)}
\end{aligned}
$$

</div>

於上式中令 <span class="text-nowrap">$y=x-2$，</span>並同樣由[汎德蒙等式](#thm-vandermonde-identity)即可得知

$$
\sum_{y=0}^{n-2}\frac{\binom{K-2}{y}\binom{(N-2)-(K-2)}{(n-2)-y}}{\binom{N-2}{n-2}}=1
$$

由此可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\bigl(X^{2}\bigr)=\mathbb{E}\bigl[X(X-1)\bigr]+\mathbb{E}(X)=\frac{Kn\bigl[(K-1)(n-1)+(N-1)\bigr]}{N(N-1)}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl(X^{2}\bigr)&=\mathbb{E}\bigl[X(X-1)\bigr]+\mathbb{E}(X)\\[0.3em]
&=\frac{Kn\bigl[(K-1)(n-1)+(N-1)\bigr]}{N(N-1)}
\end{aligned}
$$

</div>

最後求變異數，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(X)&=\mathbb{E}\bigl(X^{2}\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}\\[0.45em]
&=\frac{Kn\bigl[(K-1)(n-1)+(N-1)\bigr]}{N(N-1)}-\biggl[K\Bigl(\frac{n}{N}\Bigr)\biggr]^{2}\\[0.45em]
&=n\Bigl(\frac{K}{N}\Bigr)\Bigl(1-\frac{K}{N}\Bigr)\Bigl(\frac{N-n}{N-1}\Bigr)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(X)&=\mathbb{E}\bigl(X^{2}\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}\\[0.3em]
&=\frac{Kn\bigl[(K-1)(n-1)+(N-1)\bigr]}{N(N-1)}\\[0.25em]
&\qquad\quad -\biggl[K\Bigl(\frac{n}{N}\Bigr)\biggr]^{2}\\[0.3em]
&=n\Bigl(\frac{K}{N}\Bigr)\Bigl(1-\frac{K}{N}\Bigr)\Bigl(\frac{N-n}{N-1}\Bigr)
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

前文[第三章的範例](/lecture-notes/variance-of-linear-combination/#ex-hypergeometric-variance)曾將超幾何變數表為相依指標變數之和，藉線性組合的期望值與變異數公式推導同一結果，可與此處運用階乘動差與汎德蒙等式的證法互相參照。

</div>

(2) 由於組合數的定義限制，[汎德蒙等式](#thm-vandermonde-identity)右側的 $\sum_{x=0}^{n}\binom{K}{x}\binom{N-K}{n-x}$ 並非對所有 $x\in\lbrace 0,\ldots,n\rbrace$ 皆具非零組合意義，僅當 $x$ 落在下列集合內時兩項組合數才同時有正值:
{: .topic-paren-item}

$$
\lbrace\,\mathrm{max}(0,n+K-N),\ldots,\mathrm{min}(n,K)\,\rbrace
$$

當 $n>K$ 或 $n>N-K$ 時，超出上述範圍的 $x$ 會使其中一項組合數無對應選法，此時約定 <span class="text-nowrap">$\binom{K}{x}\binom{N-K}{n-x}=0$。</span>
{: .topic-paren-cont}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

舉例而言，箱中有大小與形狀皆相同的紅球 $3$ 顆與白球 $2$ 顆，若取後不放回抽取 $3$ 顆球，不可能發生「抽到 $3$ 顆白球」的情形，對應的可能組合數自然為 <span class="text-nowrap">$0$。</span>一般而言，當**抽取的數量 $n$ 比其中一類的總數 $K$ 或 $N-K$ 還多**時，抽到超過該類元素上限的組合數即為 <span class="text-nowrap">$0$。</span>

</div>

(3) 超幾何分配變異數中的 $\Bigl(\frac{N-n}{N-1}\Bigr)$ 一項，正是[第三章該道範例](/lecture-notes/variance-of-linear-combination/#ex-hypergeometric-variance)介紹過的**有限母體校正因子 <span lang="en">(finite population correction factor, FPC factor)</span>**。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

對有限母體採取後不放回抽樣時，每次抽取都會改變剩餘母體的組成，進而影響整體的變異程度，故須乘上**有限母體校正**項。此外，$\frac{N-n}{\,N-1\,}$ 接近抽樣後剩餘元素佔母體的比例 <span class="text-nowrap">$\frac{N-n}{\,N\,}$，</span>因此在抽樣調查領域中，常透過改寫將有限母體校正因子表為 $\frac{N-n}{\,N\,}$ 的形式以簡化推導。

</div>

(4) 若改採取後放回方式抽樣，每次抽取皆不改變母體結構，無須乘上有限母體校正因子，此時期望值與變異數即回到
{: .topic-paren-item}

$$
n\Bigl(\frac{K}{N}\Bigr)\quad \text{與}\quad n\Bigl(\frac{K}{N}\Bigr)\Bigl(1-\frac{K}{N}\Bigr)
$$

另一種無須有限母體校正的情形為「只抽一個元素」(<span class="text-nowrap">$n=1$</span>)，此時有限母體校正因子等於 <span class="text-nowrap">$1$。</span>從另一角度看，$\Bigl(\frac{K}{N}\Bigr)$ 即為**母體中成功類的比例**，上述期望值與變異數與二項分配完全一致；換言之，超幾何分配可視為有限母體且取後不放回版本的二項分配，兩者對應如下
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\boxed{\ \mathrm{Hyper}\bigl(N,K,n\bigr)\ \ \mathrel{\substack{\xrightarrow{\ \text{取後放回}\ }\\ \xleftarrow{\ \text{有限母體、取後不放回}\ }}}\ \ \mathrm{Bin}\Bigl(n,\ p=\frac{K}{N}\Bigr)\ }
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\boxed{
\begin{gathered}
\mathrm{Hyper}\bigl(N,K,n\bigr)\\[0.4em]
\mathrel{\substack{\xrightarrow{\ \text{取後放回}\ }\\ \xleftarrow{\ \text{有限母體、取後不放回}\ }}}\\[0.4em]
\mathrm{Bin}\Bigl(n,\ p=\frac{K}{N}\Bigr)
\end{gathered}
}
$$

</div>

(5) 有限母體校正旨在反映抽樣過程中母體組成的改變；現實問題中的母體皆屬有限，理論上均涉及此項修正。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

當樣本大小 $n$ 相對於母體總數 $N$ 所佔比例極小時，抽樣對母體組成的改變相當有限，校正因子亦趨近於 <span class="text-nowrap">$1$。</span>實務應用上，若滿足 <span class="text-nowrap">$n/N<5\%$，</span>常直接以無限母體近似處理以簡化運算。

</div>

(6) 超幾何分配的動差母函數會使用到**超幾何函數 <span lang="en">(hypergeometric function)</span>**，由於該函數已經超出本系列所欲探討的範圍，故在此略過。
{: .topic-paren-item}

## 超幾何分配的例題

<div id="ex-hypergeometric-1" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.19</div>

<div lang="en" markdown="1">
A lot of $25$ color television tubes is subjected to an acceptance testing procedure. The procedure consists of drawing five tubes at random, without replacement, and testing them. If two or fewer tubes fail, the remaining ones are accepted; otherwise, the lot is rejected. Assume the lot contains four defective tubes. What is the probability of lot acceptance?
</div>

題目敘述可知，若令 $X$ 表示抽到的五個電視管中壞掉的個數，則

$$
X\sim\mathrm{Hyper}(N=25,\ K=4,\ n=5)
$$

且所求為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(X\leqslant2)=\frac{\binom{4}{0}\binom{21}{5}}{\binom{25}{5}}+\frac{\binom{4}{1}\binom{21}{4}}{\binom{25}{5}}+\frac{\binom{4}{2}\binom{21}{3}}{\binom{25}{5}}\fallingdotseq0.9838
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(X\leqslant2)&=\frac{\binom{4}{0}\binom{21}{5}}{\binom{25}{5}}+\frac{\binom{4}{1}\binom{21}{4}}{\binom{25}{5}}\\[0.3em]
&\qquad+\frac{\binom{4}{2}\binom{21}{3}}{\binom{25}{5}}\\[0.3em]
&\fallingdotseq0.9838
\end{aligned}
$$

</div>

</div>

<div id="ex-hypergeometric-2" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.20</div>

<div lang="en" markdown="1">
The following table lists $12$ universities along with the registration rates of their PhD programs in <span class="text-nowrap">$2017$.</span>

| University | Registration Rate (%) |
|:---:|:---:|
| 台灣大學 | $73.00$ |
| 清華大學 | $81.93$ |
| 中央大學 | $83.89$ |
| 中山大學 | $80.58$ |
| 台灣師範大學 | $88.89$ |
| 政治大學 | $66.26$ |
| 成功大學 | $63.00$ |
| 交通大學 | $72.38$ |
| 陽明大學 | $72.22$ |
| 中興大學 | $74.49$ |
| 長庚大學 | $77.78$ |
| 台灣科技大學 | $80.75$ |
{: .topic-table--matrix}

<ol class="topic-list-paren">
  <li>If five different universities are selected at random from the list, what is the probability that three of them have registration rates between the first and third quartiles?</li>
  <li>If six different universities are selected at random from the list, what is the probability that two or fewer are located in Taipei?</li>
  <li>Suppose universities are selected at random from the list with replacement. If five universities are sampled, what is the probability that the sample contains exactly two universities in Taipei?</li>
</ol>
</div>

(1) 由題目之表格可將註冊率排序為
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
63.00,\ 66.26,\ 72.22,\ 72.38,\ 73.00,\ 74.49,\\[0.35em]
77.78,\ 80.58,\ 80.75,\ 81.93,\ 83.89,\ 88.89
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
63.00,\ 66.26,\ 72.22,\ 72.38,\\[0.35em]
73.00,\ 74.49,\ 77.78,\ 80.58,\\[0.35em]
80.75,\ 81.93,\ 83.89,\ 88.89
\end{gathered}
$$

</div>

由此可得
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
Q_1=\frac{X_{(3)}+X_{(4)}}{2}=72.3,\qquad Q_3=\frac{X_{(9)}+X_{(10)}}{2}=81.34
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
Q_1=\frac{X_{(3)}+X_{(4)}}{2}=72.3,\\[0.45em]
Q_3=\frac{X_{(9)}+X_{(10)}}{2}=81.34
\end{gathered}
$$

</div>

若令 $X$ 表示抽到的五間學校中註冊率在 $Q_1$ 到 $Q_3$ 之間的個數，則
{: .topic-paren-cont}

$$
X\sim\mathrm{Hyper}(N=12,\ K=6,\ n=5)
$$

且所求為
{: .topic-paren-cont}

$$
\mathbb{P}(X=3)=\frac{\binom{6}{3}\binom{6}{2}}{\binom{12}{5}}\fallingdotseq0.3788
$$

(2) 若令 $Y$ 表示抽中六校中位於台北的個數，則
{: .topic-paren-item}

$$
Y\sim\mathrm{Hyper}(N=12,\ K=5,\ n=6)
$$

且所求為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(Y\leqslant2)=\frac{\binom{5}{2}\binom{7}{4}}{\binom{12}{6}}+\frac{\binom{5}{1}\binom{7}{5}}{\binom{12}{6}}+\frac{\binom{5}{0}\binom{7}{6}}{\binom{12}{6}}=0.5
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(Y\leqslant2)&=\frac{\binom{5}{2}\binom{7}{4}}{\binom{12}{6}}+\frac{\binom{5}{1}\binom{7}{5}}{\binom{12}{6}}\\[0.3em]
&\qquad+\frac{\binom{5}{0}\binom{7}{6}}{\binom{12}{6}}\\[0.3em]
&=0.5
\end{aligned}
$$

</div>

(3) 若令 $W$ 表示抽中五校中位於台北的個數，則
{: .topic-paren-item}

$$
W\sim\mathrm{Bin}\Bigl(n=5,\ p=\frac{5}{\,12\,}\Bigr)
$$

且所求為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(W=2)=\binom{5}{2}\Bigl(\frac{5}{\,12\,}\Bigr)^{2}\Bigl(\frac{7}{\,12\,}\Bigr)^{3}\fallingdotseq0.3446
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(W=2)&=\binom{5}{2}\Bigl(\frac{5}{\,12\,}\Bigr)^{2}\Bigl(\frac{7}{\,12\,}\Bigr)^{3}\\[0.3em]
&\fallingdotseq0.3446
\end{aligned}
$$

</div>

</div>

## 本篇小結

[Theorem 4.8](#thm-vandermonde-identity) 的汎德蒙等式把 $\binom{N}{n}$ 這個組合數拆成一連串乘積之和，證明的作法是比較 $(1+x)^{K}(1+x)^{N-K}=(1+x)^{N}$ 兩邊 $x^{n}$ 的係數，左邊依二項式定理展開之後再合併同次項，右邊則直接由二項式定理得到。這個等式在本篇一共用了三次，其中一次用來驗證機率函數的加總為 $1$ 這件事，另外兩次分別出現在期望值與階乘動差的最後一步。

[Definition 4.8](#def-hypergeometric-experiment) 的超幾何實驗把有限母體分成成功類與失敗類，並以取後不放回的方式抽出 $n$ 個元素；[Definition 4.9](#def-hypergeometric) 的超幾何分配則以 $X$ 記錄這 $n$ 個元素中成功類的個數。與二項分配相比，最明顯的差別在於值域的兩端要受 $\mathrm{max}(0,n+K-N)$ 與 $\mathrm{min}(n,K)$ 這兩個數限制，而變異數比二項分配多出一個因子。期望值為 $n(K/N)$ 這個式子，與二項分配把 $p$ 換成母體中成功類的比例之後完全相同。

定義之後的六點說明依序處理了幾件事。第一點是完整的證明；第二點指出組合符號的定義限制，抽取數量比其中一類的總數還多時，對應的乘積被定義為零，汎德蒙等式的加總因而可以寫成由 $0$ 到 <span class="text-nowrap">$n$；</span>第三點與第四點指出變異數中多出來的那個因子即為有限母體校正因子，取後放回時它會消失，只抽一個元素時它等於 <span class="text-nowrap">$1$，</span>兩種情形都不需要校正；第五點與第六點分別交代校正在實務上何時可以省去，以及動差母函數為何在此略去不談。

[Example 4.19](#ex-hypergeometric-1) 是直接的驗收計算，把「壞掉的個數不超過兩個」拆成三項相加。[Example 4.20](#ex-hypergeometric-2) 則把同一份資料用了三次，前兩小題分別以註冊率的四分位數與學校所在地界定成功類，兩者都是取後不放回，因而使用超幾何分配；第三小題改為取後放回，母體結構不再改變，模型隨之換成二項分配，正好與第四點的說明前後呼應。

[下一篇](/lecture-notes/poisson-process-and-distribution/)離開伯努利實驗這一系列的模型，轉入介紹卜瓦松過程，先給出卜瓦松過程的五個條件，再由指數函數的馬克勞林級數推導出卜瓦松分配。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Norman L. Johnson, Adrienne W. Kemp, and Samuel Kotz. 2005. *Univariate Discrete Distributions*. 3rd ed. Wiley.
