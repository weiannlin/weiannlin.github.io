---
title: "特徵函數"
subtitle: "Characteristic Functions"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 18
order: 218
permalink: /lecture-notes/characteristic-functions/
date: 2026-08-08
published: true
excerpt: "特徵函數定義為 $\\phi_{\\sssig X}(t)=\\mathbb{E}(e^{itX})$ 這個複數期望值，因 $\\lvert e^{itX}\\rvert=1$ 而對所有實值隨機變數恆存在。本篇介紹其動差生成性質、唯一性與反演公式，並以動差母函數不存在的標準柯西分配示範其用途。"
---

[上一篇](/lecture-notes/probability-cumulant-generating-functions/)介紹了[機率母函數](/lecture-notes/probability-cumulant-generating-functions/#def-pgf)與[累積量母函數](/lecture-notes/probability-cumulant-generating-functions/#def-cgf)。前者把工具函數取為 $t^{X}$ 而生成階乘動差與機率，後者由 mgf 取對數而生成累積量，[Theorem 2.26](/lecture-notes/probability-cumulant-generating-functions/#thm-mgf-pgf-cgf-relation) 並進一步說明 mgf 與 pgf 之間只差一個變數的代換。

母函數的家族還有一位成員。我們在[動差母函數](/lecture-notes/moment-generating-functions/#def-mgf)一篇曾說過，動差母函數不是任何時候都存在。它要求存在某個 $h>0$，使 $\mathbb{E}(e^{tX})$ 在 $-h<t<h$ 之內皆為有限，而 $e^{tX}$ 會隨著 $tX$ 增大而無界地增長，一旦分配的尾巴夠厚，這個[期望值](/lecture-notes/expectation/#def-expectation)便發散。問題既然出在 $e^{tX}$ 本身無界，一個自然的想法便是把工具函數換成一個有界的東西。

只要在指數的自變數乘上**虛數單位 <span lang="en">(imaginary unit)</span>** $i$ (滿足 $i^{2}=-1$)，所得到的 $e^{itX}$ 其絕對值便恆為 $1$，於是期望值 $\mathbb{E}(e^{itX})$ 對每一個實值[隨機變數](/lecture-notes/random-variables-and-pmf/#def-random-variable)與任意實數 $t$ 都存在，這便是**特徵函數 <span lang="en">(characteristic function, cf)</span>**。本篇先交代複數指數所需的歐拉公式，再給出特徵函數的定義與三點注意事項，接著依序介紹其五項基本性質、如何以微分生成原動差、與 mgf 及 pgf 的關係，以及其唯一性與反演公式，最後以**標準柯西分配 <span lang="en">(standard Cauchy distribution)</span>** 的樣本平均數示範唯一性的用法。

在進入定義之前，先交代複數指數的兩個基本事實。以 $i$ 表虛數單位，即 $i^{2}=-1$。對任意實數 $u$，複數指數 $e^{iu}$ 可由**歐拉公式 <span lang="en">(Euler’s formula)</span>** 寫成三角函數的組合，即

$$
e^{iu}=\cos u+i\sin u,\quad u\in\mathbb{R}
$$

由此可得它的絕對值

$$
\lvert e^{iu}\rvert=\bigl(\cos^{2}u+\sin^{2}u\bigr)^{1/2}=1,\quad u\in\mathbb{R}
$$

也就是說，不論 $u$ 取什麼實數值，$e^{iu}$ 的絕對值都是 $1$。這一點正是特徵函數對每個分配都存在的原因。

<div id="def-characteristic-function" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.19 (特徵函數, characteristic function, cf)</div>

若 $X$ 為離散型隨機變數，值域為 $\mathcal{R}\_{\sssig X}$、pmf 為 $p\_{\sssig X}(x)$，則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\phi_{\sssig X}(t)=\mathbb{E}\bigl(e^{itX}\bigr)=\sum_{x\in\mathcal{R}_{\sssig X}}e^{itx}\,p_{\sssig X}(x),\quad t\in\mathbb{R}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\phi_{\sssig X}(t)&=\mathbb{E}\bigl(e^{itX}\bigr)\\[0.45em]
&=\sum_{x\in\mathcal{R}_{\sssig X}}e^{itx}\,p_{\sssig X}(x),\quad t\in\mathbb{R}
\end{aligned}
$$

</div>

被定義為 $X$ 的**特徵函數**。

若 $X$ 為連續型隨機變數，pdf 為 $f\_{\sssig X}(x)$，則其特徵函數為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\phi_{\sssig X}(t)=\mathbb{E}\bigl(e^{itX}\bigr)=\int_{-\infty}^{\infty}e^{itx}\,f_{\sssig X}(x)\,dx,\quad t\in\mathbb{R}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\phi_{\sssig X}(t)&=\mathbb{E}\bigl(e^{itX}\bigr)\\[0.45em]
&=\int_{-\infty}^{\infty}e^{itx}\,f_{\sssig X}(x)\,dx,\quad t\in\mathbb{R}
\end{aligned}
$$

</div>

被定義為 $X$ 的**特徵函數**。

兩型皆可由歐拉公式拆成實部與虛部，即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\phi_{\sssig X}(t)=\mathbb{E}\bigl[\cos(tX)\bigr]+i\,\mathbb{E}\bigl[\sin(tX)\bigr]
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\phi_{\sssig X}(t)&=\mathbb{E}\bigl[\cos(tX)\bigr]+i\,\mathbb{E}\bigl[\sin(tX)\bigr]
\end{aligned}
$$

</div>

</div>

特徵函數有一些地方需要注意:

(1) 與 mgf、pgf 相同，特徵函數的定義式已對 $X$ 的所有可能取值完成積分 (或加總)，結果不再含有隨機變數 <span class="text-nowrap">$X$，</span>而是以 $t$ 為自變數的函數。
{: .topic-paren-item}

(2) 由於 <span class="text-nowrap">$\lvert e^{itX}\rvert=1$，</span>定義式的絕對值恆以 $1$ 為上界，因此對任意實值隨機變數 $X$ 與任意實數 <span class="text-nowrap">$t$，</span>$\phi\_{\sssig X}(t)$ 皆存在。相較於動差母函數須假設 $\mathbb{E}(e^{tX})$ 在某個鄰域 $(-h,h)$ 內有限，特徵函數無須附加此類存在性前提，這是兩者最關鍵的差異。
{: .topic-paren-item}

(3) 特徵函數除可作為**工具函數**[微分生成各階原動差](#thm-cf-generates-moments)外，更具備無條件成立的[**唯一性**](#thm-cf-uniqueness)，且能進一步透過反演公式直接還原 cdf 甚至 pdf，此為動差母函數所不及之處。
{: .topic-paren-item}

<div id="thm-cf-properties" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.27 (特徵函數的基本性質, properties of the cf)</div>

若 $X$ 為一隨機變數，其特徵函數為 <span class="text-nowrap">$\phi\_{\sssig X}(t)$，則</span>

<ol class="topic-list-paren topic-list-paren--math">
  <li>
  $$
  \phi_{\sssig X}(0)=1
  $$
  </li>
  <li>
  $$
  \lvert\phi_{\sssig X}(t)\rvert\leqslant1,\quad\forall\,t\in\mathbb{R}
  $$
  </li>
</ol>

(3) $\phi\_{\sssig X}(t)$ 在 $\mathbb{R}$ 上**均勻連續 <span lang="en">(uniformly continuous)</span>**。
{: .topic-paren-item}

<ol class="topic-list-paren topic-list-paren--start-4 topic-list-paren--math">
  <li>
  $$
  \phi_{\sssig X}(-t)=\overline{\phi_{\sssig X}(t)},\quad\forall\,t\in\mathbb{R}
  $$
  </li>
</ol>

其中 $\overline{\phi\_{\sssig X}(t)}$ 表 $\phi\_{\sssig X}(t)$ 的**共軛複數 <span lang="en">(complex conjugate)</span>**。
{: .topic-paren-cont}

(5) 若 $Y=aX+b$，其中 $a,b\in\mathbb{R}$，則
{: .topic-paren-item}

$$
\phi_{\sssig Y}(t)=e^{ibt}\,\phi_{\sssig X}(at),\quad\forall\,t\in\mathbb{R}
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.**

第 (1) 款由 [Definition 2.19](#def-characteristic-function) 取 $t=0$ 即得

$$
\phi_{\sssig X}(0)=\mathbb{E}\bigl(e^{0}\bigr)=\mathbb{E}(1)=1
$$

第 (2) 款用到**複數值隨機變數 <span lang="en">(complex-valued random variable)</span>** 的基本性質。若 $Z=U+i\,V$ 且實部 $U$ 與虛部 $V$ 皆為實值隨機變數，則其期望值定義為 $\mathbb{E}(Z)=\mathbb{E}(U)+i\,\mathbb{E}(V)$，由此可推得不等式 $\lvert\mathbb{E}(Z)\rvert\leqslant\mathbb{E}(\lvert Z\rvert)$ 在複數值的情形仍然成立。取 $Z=e^{itX}$ 並代入 $\lvert e^{itX}\rvert=1$ 可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lvert\phi_{\sssig X}(t)\rvert=\bigl\lvert\mathbb{E}\bigl(e^{itX}\bigr)\bigr\rvert\leqslant\mathbb{E}\bigl(\bigl\lvert e^{itX}\bigr\rvert\bigr)=\mathbb{E}(1)=1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\lvert\phi_{\sssig X}(t)\rvert&=\bigl\lvert\mathbb{E}\bigl(e^{itX}\bigr)\bigr\rvert\\[0.45em]
&\leqslant\mathbb{E}\bigl(\bigl\lvert e^{itX}\bigr\rvert\bigr)\\[0.45em]
&=\mathbb{E}(1)=1
\end{aligned}
$$

</div>

第 (3) 款在此僅以連續型隨機變數證明，離散型同理可證。對任意 <span class="text-nowrap">$t,h\in\mathbb{R}$，</span>把兩個函數值相減再提出 $e^{itX}$ 可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\bigl\lvert\phi_{\sssig X}(t+h)-\phi_{\sssig X}(t)\bigr\rvert=\Bigl\lvert\mathbb{E}\bigl[e^{itX}\bigl(e^{ihX}-1\bigr)\bigr]\Bigr\rvert\leqslant\mathbb{E}\bigl(\bigl\lvert e^{ihX}-1\bigr\rvert\bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\bigl\lvert\phi_{\sssig X}(t+h)-\phi_{\sssig X}(t)\bigr\rvert&=\Bigl\lvert\mathbb{E}\bigl[e^{itX}\bigl(e^{ihX}-1\bigr)\bigr]\Bigr\rvert\\[0.45em]
&\leqslant\mathbb{E}\bigl(\bigl\lvert e^{ihX}-1\bigr\rvert\bigr)
\end{aligned}
$$

</div>

其中不等號同樣由 $\lvert\mathbb{E}(Z)\rvert\leqslant\mathbb{E}(\lvert Z\rvert)$ 與 $\lvert e^{itX}\rvert=1$ 得到。右側已經與 $t$ 無關，因此只要證明它可以隨著 $h$ 變小而一致地變小即可。給定 $\varepsilon>0$，先取 $c>0$ 夠大，使得

$$
\mathbb{P}\bigl(\lvert X\rvert>c\bigr)<\frac{\,\varepsilon\,}{4}
$$

再把右側的期望值依 $\lvert x\rvert\leqslant c$ 與 $\lvert x\rvert>c$ 拆成兩段，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\bigl(\bigl\lvert e^{ihX}-1\bigr\rvert\bigr)=\int_{\lvert x\rvert\leqslant c}\bigl\lvert e^{ihx}-1\bigr\rvert\,f_{\sssig X}(x)\,dx+\int_{\lvert x\rvert>c}\bigl\lvert e^{ihx}-1\bigr\rvert\,f_{\sssig X}(x)\,dx
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl(\bigl\lvert e^{ihX}-1\bigr\rvert\bigr)&=\int_{\lvert x\rvert\leqslant c}\bigl\lvert e^{ihx}-1\bigr\rvert\,f_{\sssig X}(x)\,dx\\[0.45em]
&\qquad +\int_{\lvert x\rvert>c}\bigl\lvert e^{ihx}-1\bigr\rvert\,f_{\sssig X}(x)\,dx
\end{aligned}
$$

</div>

下面會用到 $\lvert e^{iu}-1\rvert\leqslant\lvert u\rvert$ 這個界限。由歐拉公式可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\bigl\lvert e^{iu}-1\bigr\rvert^{2}=(\cos u-1)^{2}+\sin^{2}u=2(1-\cos u)=4\sin^{2}\frac{u}{\,2\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\bigl\lvert e^{iu}-1\bigr\rvert^{2}&=(\cos u-1)^{2}+\sin^{2}u\\[0.45em]
&=2(1-\cos u)=4\sin^{2}\frac{u}{\,2\,}
\end{aligned}
$$

</div>

再由 $\lvert\sin\frac{u}{\,2\,}\rvert\leqslant\bigl\lvert\frac{u}{\,2\,}\bigr\rvert$ 即得 $\lvert e^{iu}-1\rvert=2\lvert\sin\frac{u}{\,2\,}\rvert\leqslant\lvert u\rvert$。第一段之中 <span class="text-nowrap">$\lvert x\rvert\leqslant c$，</span>因而 $\lvert e^{ihx}-1\rvert\leqslant\lvert hx\rvert\leqslant\lvert h\rvert c$，只要取 $\lvert h\rvert<\frac{\varepsilon}{\,2c\,}$ 便有 $\lvert e^{ihx}-1\rvert<\frac{\varepsilon}{\,2\,}$；第二段之中被積函數以 $\lvert e^{ihx}-1\rvert\leqslant2$ 為界，故

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\bigl(\bigl\lvert e^{ihX}-1\bigr\rvert\bigr)\leqslant\frac{\,\varepsilon\,}{2}+2\times\frac{\,\varepsilon\,}{4}=\varepsilon
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl(\bigl\lvert e^{ihX}-1\bigr\rvert\bigr)&\leqslant\frac{\,\varepsilon\,}{2}+2\times\frac{\,\varepsilon\,}{4}=\varepsilon
\end{aligned}
$$

</div>

這個 $h$ 的取法只與 $c$ 及 $\varepsilon$ 有關而與 $t$ 無關，故 $\phi\_{\sssig X}$ 在 $\mathbb{R}$ 上均勻連續。

第 (4) 款由 $e^{-itx}$ 與 $e^{itx}$ 互為共軛複數，且取共軛與取期望值可以交換順序，故有下式

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\phi_{\sssig X}(-t)=\mathbb{E}\bigl(e^{-itX}\bigr)=\overline{\mathbb{E}\bigl(e^{itX}\bigr)}=\overline{\phi_{\sssig X}(t)}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\phi_{\sssig X}(-t)&=\mathbb{E}\bigl(e^{-itX}\bigr)\\[0.45em]
&=\overline{\mathbb{E}\bigl(e^{itX}\bigr)}=\overline{\phi_{\sssig X}(t)}
\end{aligned}
$$

</div>

第 (5) 款由 $e^{it(aX+b)}=e^{ibt}e^{i(at)X}$，再把與 $X$ 無關的 $e^{ibt}$ 提到期望值之外，可以得到下式

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\phi_{\sssig Y}(t)=\mathbb{E}\bigl(e^{it(aX+b)}\bigr)=e^{ibt}\,\mathbb{E}\bigl(e^{i(at)X}\bigr)=e^{ibt}\,\phi_{\sssig X}(at)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\phi_{\sssig Y}(t)&=\mathbb{E}\bigl(e^{it(aX+b)}\bigr)\\[0.45em]
&=e^{ibt}\,\mathbb{E}\bigl(e^{i(at)X}\bigr)\\[0.45em]
&=e^{ibt}\,\phi_{\sssig X}(at)
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

接下來看特徵函數如何生成原動差。

<div id="thm-cf-generates-moments" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.28 (由 cf 微分生成原動差, moments generated by the cf)</div>

若 $X$ 為一隨機變數，且 $\mathbb{E}(\lvert X\rvert^{r})<\infty$，則其特徵函數 $\phi\_{\sssig X}(t)$ 的 $r$ 階導數存在且連續，並且滿足

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\phi^{(r)}_{\sssig X}(0)=\left.\frac{d^{r}\phi_{\sssig X}(t)}{d\,t^{r}}\right|_{t=0}=i^{r}\,\mathbb{E}\bigl(X^{r}\bigr)=i^{r}\mu_{\sssig r}^{\prime}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\phi^{(r)}_{\sssig X}(0)&=\left.\frac{d^{r}\phi_{\sssig X}(t)}{d\,t^{r}}\right|_{t=0}\\[0.45em]
&=i^{r}\,\mathbb{E}\bigl(X^{r}\bigr)=i^{r}\mu_{\sssig r}^{\prime}
\end{aligned}
$$

</div>

</div>

<div class="topic-proof" markdown="1">
**Proof.**

在此僅以連續型隨機變數證明，離散型同理可證。由 [Definition 2.19](#def-characteristic-function) 對 $t$ 微分 $r$ 次可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\frac{d^{r}\phi_{\sssig X}(t)}{d\,t^{r}}&=\frac{d^{r}}{d\,t^{r}}\int_{-\infty}^{\infty}e^{itx}\,f_{\sssig X}(x)\,dx=\int_{-\infty}^{\infty}\frac{d^{r}}{d\,t^{r}}e^{itx}\,f_{\sssig X}(x)\,dx\\[0.45em]
&=\int_{-\infty}^{\infty}(ix)^{r}e^{itx}\,f_{\sssig X}(x)\,dx=i^{r}\int_{-\infty}^{\infty}x^{r}e^{itx}\,f_{\sssig X}(x)\,dx
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\frac{d^{r}\phi_{\sssig X}(t)}{d\,t^{r}}&=\frac{d^{r}}{d\,t^{r}}\int_{-\infty}^{\infty}e^{itx}\,f_{\sssig X}(x)\,dx\\[0.45em]
&=\int_{-\infty}^{\infty}\frac{d^{r}}{d\,t^{r}}e^{itx}\,f_{\sssig X}(x)\,dx\\[0.45em]
&=\int_{-\infty}^{\infty}(ix)^{r}e^{itx}\,f_{\sssig X}(x)\,dx\\[0.45em]
&=i^{r}\int_{-\infty}^{\infty}x^{r}e^{itx}\,f_{\sssig X}(x)\,dx
\end{aligned}
$$

</div>

其中微分與積分可以交換順序，是因為被積函數取絕對值之後為 <span class="text-nowrap">$\lvert x\rvert^{r}f\_{\sssig X}(x)$，</span>其在 $\mathbb{R}$ 上的積分正是 $\mathbb{E}(\lvert X\rvert^{r})$，依假設為有限。再於 $t=0$ 取值，並代入 $e^{0}=1$ 即得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\phi^{(r)}_{\sssig X}(0)=i^{r}\int_{-\infty}^{\infty}x^{r}e^{0}\,f_{\sssig X}(x)\,dx=i^{r}\int_{-\infty}^{\infty}x^{r}\,f_{\sssig X}(x)\,dx=i^{r}\,\mathbb{E}\bigl(X^{r}\bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\phi^{(r)}_{\sssig X}(0)&=i^{r}\int_{-\infty}^{\infty}x^{r}e^{0}\,f_{\sssig X}(x)\,dx\\[0.45em]
&=i^{r}\int_{-\infty}^{\infty}x^{r}\,f_{\sssig X}(x)\,dx\\[0.45em]
&=i^{r}\,\mathbb{E}\bigl(X^{r}\bigr)
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

[Theorem 2.28](#thm-cf-generates-moments) 是由 $r$ 階絕對動差有限推得 $\phi\_{\sssig X}(t)$ 的 $r$ 階導數存在；若反過來僅已知 $\phi\_{\sssig X}(t)$ 在原點 $t=0$ 處的 $r$ 階導數存在，能否保證 $r$ 階絕對動差有限，則須視階數 $r$ 的奇偶而定。當 $r$ 為偶數時，確可保證 $\mathbb{E}(\lvert X\rvert^{r})<\infty$ 成立；當 $r$ 為奇數時，一般則僅能保證至第 $r-1$ 階的絕對動差存在。

</div>

<div id="thm-cf-mgf-pgf-relation" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.29 (cf 與 mgf、pgf 的關係, relations among cf, mgf and pgf)</div>

若 $X$ 為一隨機變數，則

(1) 在將 $M\_{\sssig X}$ 的自變數延伸到複數的意義之下，有
{: .topic-paren-item}

$$
\phi_{\sssig X}(t)=M_{\sssig X}(it),\quad\forall\,t\in\mathbb{R}
$$

(2) 若 $X$ 另為非負整數隨機變數，則
{: .topic-paren-item}

$$
\phi_{\sssig X}(t)=G_{\sssig X}\bigl(e^{it}\bigr),\quad\forall\,t\in\mathbb{R}
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.**

(1) 由[動差母函數的定義](/lecture-notes/moment-generating-functions/#def-mgf)，把 $M\_{\sssig X}$ 的自變數取為純虛數 $it$ 可得
{: .topic-paren-item}

$$
M_{\sssig X}(it)=\mathbb{E}\bigl(e^{itX}\bigr)=\phi_{\sssig X}(t)
$$

(2) 由[機率母函數的定義](/lecture-notes/probability-cumulant-generating-functions/#def-pgf)，把 $G\_{\sssig X}$ 的自變數取為 $e^{it}$ 可得
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
G_{\sssig X}\bigl(e^{it}\bigr)=\mathbb{E}\Bigl[\bigl(e^{it}\bigr)^{X}\Bigr]=\mathbb{E}\bigl(e^{itX}\bigr)=\phi_{\sssig X}(t)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
G_{\sssig X}\bigl(e^{it}\bigr)&=\mathbb{E}\Bigl[\bigl(e^{it}\bigr)^{X}\Bigr]\\[0.45em]
&=\mathbb{E}\bigl(e^{itX}\bigr)=\phi_{\sssig X}(t)
\end{aligned}
$$

</div>

此處的代入是合法的，因為由 $\lvert e^{it}\rvert=1$ 可知該級數各項的絕對值之和為 $\sum\_{x=0}^{\infty}p\_{\sssig X}(x)=1$，級數絕對收斂。
{: .topic-paren-cont}

原式得證。 <span class="topic-qed">$\square$</span>
{: .topic-paren-cont}
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

嚴格來說，[Definition 2.16](/lecture-notes/moment-generating-functions/#def-mgf) 僅將動差母函數 $M_{\sssig X}(t)$ 定義在實數 $t$ 上，因此 [Theorem 2.29](#thm-cf-mgf-pgf-relation) 第 (1) 款中的 $M_{\sssig X}(it)$ 是將定義式 $\mathbb{E}(e^{tX})$ 的自變數形式地推廣至複數後的寫法，讓讀者能一眼看出 $\phi_{\sssig X}(t)$ 與 $M_{\sssig X}(t)$ 在結構上的對應關係；而特徵函數 $\phi_{\sssig X}(t)$ 本身則是直接定義在實數 $t\in\mathbb{R}$ 上的函數。

</div>

有了基本性質與生成動差的方式之後，接著看特徵函數最有用的一項性質。

<div id="thm-cf-uniqueness" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.30 (特徵函數的唯一性, uniqueness of cf)</div>

若 $X, Y$ 為二隨機變數，則二者之特徵函數 $\phi\_{\sssig X}(t), \phi\_{\sssig Y}(t)$ 對一切 $t\in\mathbb{R}$ 皆相等，若且唯若二者之 cdf 亦相等，即

<div class="topic-math-follow-before" markdown="1">

$$
\phi_{\sssig X}(t)=\phi_{\sssig Y}(t),\ \forall\,t\in\mathbb{R}
$$

</div>

<div class="topic-math-follow" markdown="1">

$$
\Longleftrightarrow\ F_{\sssig X}(s)=F_{\sssig Y}(s),\ \forall\,s\in\mathbb{R}
$$

</div>

</div>

<div class="topic-proof" markdown="1">
**Proof.**

見黃文璋 (2010)，《機率論》，二版，第四章〈唯一性及倒轉公式〉一節；亦見 Billingsley (1995)，*Probability and Measure*，3rd ed.，第五章。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

特徵函數之所以具有唯一性，背後的數學根據是**反演公式 <span lang="en">(inversion formula)</span>** (或稱**倒轉公式**)，它讓我們能夠從特徵函數將原本的分配反算回來。具體而言，若 $a<b$ 皆為 $F_{\sssig X}$ 的連續點，則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig X}(b)-F_{\sssig X}(a)=\frac{1}{\,2\pi\,}\lim_{c\to\infty}\int_{-c}^{c}\frac{e^{-ita}-e^{-itb}}{it}\,\phi_{\sssig X}(t)\,dt
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&F_{\sssig X}(b)-F_{\sssig X}(a)\\[.45em]
&=\frac{1}{\,2\pi\,}\lim_{c\to\infty}\int_{-c}^{c}\frac{e^{-ita}-e^{-itb}}{it}\,\phi_{\sssig X}(t)\,dt
\end{aligned}
$$

</div>

式中的被積函數在 $t=0$ 處是以 $t\to0$ 的極限值 $b-a$ 來定義。

更進一步地，若特徵函數滿足絕對可積條件 $\int_{-\infty}^{\infty}\lvert\phi_{\sssig X}(t)\rvert\,dt<\infty$，則 $X$ 的 pdf 不僅存在、有界且均勻連續，還可以直接由下式反求得到

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X}(x)=\frac{1}{\,2\pi\,}\int_{-\infty}^{\infty}e^{-itx}\,\phi_{\sssig X}(t)\,dt,\quad x\in\mathbb{R}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig X}(x)&=\frac{1}{\,2\pi\,}\int_{-\infty}^{\infty}e^{-itx}\,\phi_{\sssig X}(t)\,dt, ~x\in\mathbb{R}
\end{aligned}
$$

</div>

須注意特徵函數雖對任何分配皆存在，卻不代表每個隨機變數皆具有 pdf；當上述絕對可積條件不成立時 (例如離散型分配)，便只能由第一條反演公式還原其 cdf。

</div>

下例將考慮多個隨機變數滿足**[獨立](/lecture-notes/independent-random-variables/#def-indep-r-v) <span lang="en">(independent)</span>** 且**同分配 <span lang="en">(identically distributed)</span>** 的情形。這兩個性質的嚴格定義與證明將於下一章給出；現階段可先理解為各隨機變數彼此互不影響且服從相同的機率分配。在彼此獨立的前提下，$e^{itX\_{1}},\ldots,e^{itX\_{n}}$ 亦互不影響，其乘積的期望值可拆為個別期望值的乘積，故獨立隨機變數和的特徵函數滿足

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\phi_{\sssig X_{1}+\cdots+X_{n}}(t)=\prod_{j=1}^{n}\phi_{\sssig X_{j}}(t),\quad t\in\mathbb{R}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\phi_{\sssig X_{1}+\cdots+X_{n}}(t)&=\prod_{j=1}^{n}\phi_{\sssig X_{j}}(t), ~t\in\mathbb{R}
\end{aligned}
$$

</div>

<div id="ex-cauchy-sample-mean-cf" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.36</div>

<div lang="en" markdown="1">
Let $X_{1}, X_{2}, \ldots, X_{n}$ be independent and identically distributed random variables, each having the standard Cauchy pdf

$$
f(x)=\frac{1}{\,\pi(1+x^{2})\,},\quad x\in\mathbb{R}
$$

with common characteristic function $\phi(t)=e^{-\lvert t\rvert}$. Show that $\overline{X}\_{n}=\frac{1}{n}\sum\_{j=1}^{n}X\_{j}$ has the same distribution as $X\_{1}$.
</div>

依題意可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\phi_{\sssig \overline{X}_{n}}(t)&=\mathbb{E}\bigl(e^{it\overline{X}_{n}}\bigr)=\mathbb{E}\Bigl(e^{\sum_{j=1}^{n}i\frac{t}{n}X_{j}}\Bigr)=\mathbb{E}\Bigl(\prod_{j=1}^{n}e^{i\frac{t}{n}X_{j}}\Bigr)\\[0.45em]
&=\prod_{j=1}^{n}\mathbb{E}\Bigl(e^{i\frac{t}{n}X_{j}}\Bigr)=\prod_{j=1}^{n}\phi_{\sssig X_{j}}\Bigl(\frac{t}{\,n\,}\Bigr)\\[0.45em]
&=\prod_{j=1}^{n}e^{-\left\lvert\frac{t}{n}\right\rvert}=\Bigl(e^{-\left\lvert\frac{t}{n}\right\rvert}\Bigr)^{n}=e^{-\lvert t\rvert},\quad t\in\mathbb{R}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\phi_{\sssig \overline{X}_{n}}(t)=\mathbb{E}\bigl(e^{it\overline{X}_{n}}\bigr)=\mathbb{E}\Bigl(e^{\sum_{j=1}^{n}i\frac{t}{n}X_{j}}\Bigr)\\[0.45em]
&=\mathbb{E}\Bigl(\prod_{j=1}^{n}e^{i\frac{t}{n}X_{j}}\Bigr)=\prod_{j=1}^{n}\mathbb{E}\Bigl(e^{i\frac{t}{n}X_{j}}\Bigr)\\[0.45em]
&=\prod_{j=1}^{n}\phi_{\sssig X_{j}}\Bigl(\frac{t}{\,n\,}\Bigr)=\prod_{j=1}^{n}e^{-\left\lvert\frac{t}{n}\right\rvert}\\[0.45em]
&=\Bigl(e^{-\left\lvert\frac{t}{n}\right\rvert}\Bigr)^{n}=e^{-\lvert t\rvert},\quad t\in\mathbb{R}
\end{aligned}
$$

</div>

此即 $X\_{1}$ 的特徵函數，故由[特徵函數的唯一性](#thm-cf-uniqueness)知，不論 $n$ 多大皆有

$$
\overline{X}_{n}\sim\mathrm{Cauchy}(0,1)
$$

即 $\overline{X}\_{n}$ 與 $X\_{1}$ 同分配，原式得證。

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這道例題只用到特徵函數的唯一性，便直接求得樣本平均數的分配。值得注意的是，題目中的標準柯西分配連期望值都不存在，自然也就沒有 mgf，但它的 cf 卻是 $e^{-\lvert t\rvert}$ 這樣簡單的形式，正好說明了為什麼我們需要一個對任何分配都存在的母函數。這個結果在第五章討論中央極限定理時還會再用到。

</div>

在本篇的最後，我們將特徵函數與動差母函數放在一起，簡單梳理兩者在性質與應用上的四個主要異同:

(1) 在**存在性**方面，mgf 要求 $\mathbb{E}(e^{tX})$ 在原點 $t=0$ 的某個鄰域內皆有限，並非每個分配都能滿足；cf 則因為 $\lvert e^{itX}\rvert=1$ 恆成立，保證對任何實值隨機變數與任意實數 $t$ 皆存在，如前述的標準柯西分配即為典型例子。
{: .topic-paren-item}

(2) 在**生成動差**方面，兩者皆可透過在 $t=0$ 處微分 $r$ 次來求得 $r$ 階原動差 $\mathbb{E}(X^{r})$ (見 [Theorem 2.21](/lecture-notes/moment-generating-functions/#thm-mgf-generates-moments) 與 [Theorem 2.28](#thm-cf-generates-moments))，只是 cf 每次微分會多乘上一個虛數單位 $i$。此外，mgf 一旦在 $0$ 附近存在便保證各階動差皆存在；cf 則是當 $\mathbb{E}(\lvert X\rvert^{r})<\infty$ 成立時，保證可由前 $r$ 階導數求出對應的動差。
{: .topic-paren-item}

(3) 在**唯一性**方面，兩者皆具有唯一決定分配的性質 (見 [Theorem 2.23](/lecture-notes/uniqueness-of-the-mgf/#thm-mgf-uniqueness) 與 [Theorem 2.30](#thm-cf-uniqueness))，差別僅在於 mgf 的唯一性必須以「動差母函數在 $0$ 附近存在」為前提，而 cf 的唯一性則無須附加任何存在條件。
{: .topic-paren-item}

(4) 在**反求機率分配**方面，使用 mgf 辨認分配時，除了少數離散型分配可由級數形式直接看出 pmf 之外，多半需要仰賴對常見機率模型 mgf 的熟稔度來比對；而 cf 則具備明確的反演公式，在滿足絕對可積條件時甚至能直接積分算出 pdf。
{: .topic-paren-item}

## 本篇小結

[Definition 2.19](#def-characteristic-function) 把 $\mathbb{E}(e^{itX})$ 定義為 $X$ 的特徵函數 $\phi\_{\sssig X}(t)$。由歐拉公式可知 $\lvert e^{itX}\rvert=1$，因此這個期望值不必附加任何存在性條件，對每一個實值隨機變數與每一個 $t$ 都有定義，這正是它與動差母函數最大的差別。

[Theorem 2.27](#thm-cf-properties) 給出五項基本性質，包括 $\phi_{\sssig X}(0)=1$、$\lvert\phi_{\sssig X}(t)\rvert\leqslant1$、在 $\mathbb{R}$ 上均勻連續、$\phi_{\sssig X}(-t)=\overline{\phi_{\sssig X}(t)}$，以及 $Y=aX+b$ 之下的 $\phi_{\sssig Y}(t)=e^{ibt}\phi_{\sssig X}(at)$。[Theorem 2.28](#thm-cf-generates-moments) 指出當 $r$ 階絕對動差有限時，在 $t=0$ 微分 $r$ 次即得 $i^{r}\mathbb{E}(X^{r})$ 之值，每微分一次多出一個虛數單位 <span class="text-nowrap">$i$；</span>至於由導數存在反推自動差存在則需視 $r$ 的奇偶而定。[Theorem 2.29](#thm-cf-mgf-pgf-relation) 把它接回前兩篇的兩個母函數。在自變數延伸至複數的意義下 $\phi\_{\sssig X}(t)=M\_{\sssig X}(it)$ 成立，非負整數隨機變數另有 $\phi\_{\sssig X}(t)=G\_{\sssig X}(e^{it})$ 的關係。[Theorem 2.30](#thm-cf-uniqueness) 則是本篇的重點。特徵函數相等若且唯若分配相同，並且由反演公式可以把 cdf 反算回來，在絕對可積條件下還可算出 pdf。[Example 2.36](#ex-cauchy-sample-mean-cf) 示範了這項性質的用法，標準柯西分配的 $n$ 個獨立觀測值取平均之後，特徵函數仍是 <span class="text-nowrap">$e^{-\lvert t\rvert}$，</span>因此樣本平均數與單一觀測值同分配。

到這裡，動差、動差母函數、機率母函數、累積量母函數與特徵函數已把「以一個函數表示整個分配」這條線走完。[下一篇](/lecture-notes/probability-inequalities/)換一個處境。分配形式並不清楚，手上只有期望值，或再加一個[變異數](/lecture-notes/variance/#def-variance)，此時能對機率說出什麼。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Patrick Billingsley. 1995. *Probability and Measure*. 3rd ed. Wiley.
- Kai Lai Chung. 2001. *A Course in Probability Theory*. 3rd ed. Academic Press.
- Eugene Lukacs. 1970. *Characteristic Functions*. 2nd ed. Griffin.
