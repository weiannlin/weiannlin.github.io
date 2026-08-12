---
title: "特徵函數"
subtitle: "Characteristic Functions"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 18
order: 218
permalink: /teaching-topics/ch2-p218-candidate/
date: 2026-08-08
published: false
excerpt: "特徵函數把工具函數換成 $e^{itX}$。由歐拉公式可知 $\\lvert e^{itX}\\rvert=1$，因此 $\\mathbb{E}(e^{itX})$ 對每一個實值隨機變數與每一個 $t$ 都存在，這正是它與動差母函數最大的差別。它同樣以微分生成原動差，$r$ 階動差存在時 $\\phi_{X}^{(r)}(0)=i^{r}\\mathbb{E}(X^{r})$；也同樣具有唯一性，兩個分配相同若且唯若兩者的特徵函數處處相等，而且還能由反演公式反過來求出 cdf 與 pdf。標準柯西分配沒有 mgf，卻有形式簡單的 $\\phi_{X}(t)=e^{-\\lvert t\\rvert}$，其樣本平均數與單一觀測值同分配正是由唯一性得到的。"
---

[上一篇](/teaching-topics/ch2-p217-candidate/)介紹了[機率母函數](/teaching-topics/ch2-p217-candidate/#def-pgf)與[累積量母函數](/teaching-topics/ch2-p217-candidate/#def-cgf): 前者把工具函數取為 $t^{X}$ 而生成階乘動差與機率，後者由 mgf 取對數而生成累積量，[Theorem 2.26](/teaching-topics/ch2-p217-candidate/#thm-mgf-pgf-cgf-relation) 並說明 mgf 與 pgf 之間只差一個變數的代換。

母函數的家族還有一位成員。我們在[動差母函數](/teaching-topics/ch2-p215-candidate/#def-mgf)一篇曾說過，動差母函數不是任何時候都存在: 它要求存在某個 $h>0$，使 $\mathbb{E}(e^{tX})$ 在 $-h<t<h$ 之內皆為有限，而 $e^{tX}$ 會隨著 $tX$ 增大而無界地增長，一旦分配的尾巴夠厚，這個期望值便發散。問題既然出在 $e^{tX}$ 無界，一個自然的想法是把工具函數換成一個有界的東西。

把指數的自變數乘上一個平方等於 $-1$ 的數之後，$e^{itX}$ 的絕對值恆為 $1$，於是 $\mathbb{E}(e^{itX})$ 對每一個實值隨機變數與每一個 $t$ 都存在，這個期望值便是**特徵函數 <span lang="en">(characteristic function, cf)</span>**。本篇先交代複數指數所需的歐拉公式，再給出特徵函數的定義與三點須注意之處，接著依序看它的五項基本性質、如何以微分生成原動差、它與 mgf 及 pgf 的關係，以及它的唯一性，最後以**標準柯西分配 <span lang="en">(standard Cauchy distribution)</span>** 的樣本平均數示範唯一性的用法。

在進入定義之前，先交代複數指數的兩個基本事實。以 $i$ 表**虛數單位 <span lang="en">(imaginary unit)</span>**，即 $i^{2}=-1$。對任意實數 $u$，複數指數 $e^{iu}$ 可由**歐拉公式 <span lang="en">(Euler’s formula)</span>** 寫成三角函數的組合，即

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

若 $X$ 為連續型隨機變數，pdf 為 $f\_{\sssig X}(x)$，則

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
\phi_{\sssig X}(t)&=\mathbb{E}\bigl[\cos(tX)\bigr]\\[0.45em]
&\quad +i\,\mathbb{E}\bigl[\sin(tX)\bigr]
\end{aligned}
$$

</div>

</div>

特徵函數有一些地方需要注意:

(1) 與 mgf、pgf 相同，特徵函數的定義中已經將所有的 $X$ 都積分 (加總) 完了，故其結果是 $t$ 的函數而非 $X$ 的函數。
{: .topic-paren-item}

(2) 由於 $\lvert e^{itX}\rvert=1$，上面兩式的絕對值皆以 $1$ 為界，因此不論 $X$ 是什麼樣的實值隨機變數、$t$ 取什麼實數值，$\phi\_{\sssig X}(t)$ 都存在。這是特徵函數與動差母函數最大的差別。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

[動差母函數](/teaching-topics/ch2-p215-candidate/#def-mgf)要求存在某個 $h>0$，使 $\mathbb{E}(e^{tX})$ 在 $-h<t<h$ 之內皆為有限，這個條件並不是每個分配都滿足；特徵函數沒有這個前提，因此本篇其後的性質與定理都不必附加存在性的條件。

</div>

(3) 特徵函數起先同樣是以**工具函數**的角色被引入，其[生成各階動差的方式](#thm-cf-generates-moments)與 mgf 相似，稍後便會看到。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

和動差母函數一樣，特徵函數後來被發現一個更有用的用途，即[**特徵函數的唯一性**](#thm-cf-uniqueness)；而且它還能由反演公式反過來求出 cdf 與 pdf，這一點是 mgf 做不到的。這兩件事都在本篇稍後說明。

</div>

<div id="thm-cf-properties" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.27 (特徵函數的基本性質, properties of the cf)</div>

若 $X$ 為一隨機變數，其特徵函數為 <span class="text-nowrap">$\phi\_{\sssig X}(t)$，則</span>

<ol class="topic-list-paren">
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

<ol class="topic-list-paren topic-list-paren--start-4">
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
**Proof.** 第 (1) 款由 [Definition 2.19](#def-characteristic-function) 在 $t=0$ 取值即得

$$
\phi_{\sssig X}(0)=\mathbb{E}\bigl(e^{0}\bigr)=\mathbb{E}(1)=1
$$

第 (2) 款用到一項關於**複數值隨機變數 <span lang="en">(complex-valued random variable)</span>** 的事實: 這一型隨機變數 $Z$ 的期望值是實部與虛部各自取期望值，而 $\lvert\mathbb{E}(Z)\rvert\leqslant\mathbb{E}(\lvert Z\rvert)$ 在這一型同樣成立。取 $Z=e^{itX}$ 並代入 $\lvert e^{itX}\rvert=1$ 可得

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
&\bigl\lvert\phi_{\sssig X}(t+h)-\phi_{\sssig X}(t)\bigr\rvert\\[0.45em]
&\quad =\Bigl\lvert\mathbb{E}\bigl[e^{itX}\bigl(e^{ihX}-1\bigr)\bigr]\Bigr\rvert\\[0.45em]
&\quad \leqslant\mathbb{E}\bigl(\bigl\lvert e^{ihX}-1\bigr\rvert\bigr)
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
&\mathbb{E}\bigl(\bigl\lvert e^{ihX}-1\bigr\rvert\bigr)\\[0.45em]
&\quad =\int_{\lvert x\rvert\leqslant c}\bigl\lvert e^{ihx}-1\bigr\rvert\,f_{\sssig X}(x)\,dx\\[0.45em]
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
&\mathbb{E}\bigl(\bigl\lvert e^{ihX}-1\bigr\rvert\bigr)\\[0.45em]
&\quad \leqslant\frac{\,\varepsilon\,}{2}+2\times\frac{\,\varepsilon\,}{4}=\varepsilon
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

若 $X$ 為一隨機變數，且 $\mathbb{E}(\lvert X\rvert^{r})<\infty$，則其特徵函數 $\phi\_{\sssig X}(t)$ 的 $r$ 階導數存在且連續，並且

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
**Proof.** 在此僅以連續型隨機變數證明，離散型同理可證。由 [Definition 2.19](#def-characteristic-function) 對 $t$ 微分 $r$ 次可得

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
&\frac{d^{r}\phi_{\sssig X}(t)}{d\,t^{r}}=\frac{d^{r}}{d\,t^{r}}\int_{-\infty}^{\infty}e^{itx}\,f_{\sssig X}(x)\,dx\\[0.45em]
&\quad =\int_{-\infty}^{\infty}\frac{d^{r}}{d\,t^{r}}e^{itx}\,f_{\sssig X}(x)\,dx\\[0.45em]
&\quad =\int_{-\infty}^{\infty}(ix)^{r}e^{itx}\,f_{\sssig X}(x)\,dx\\[0.45em]
&\quad =i^{r}\int_{-\infty}^{\infty}x^{r}e^{itx}\,f_{\sssig X}(x)\,dx
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

[Theorem 2.28](#thm-cf-generates-moments) 的方向是由動差推導數: 只要 $r$ 階動差存在，$\phi\_{\sssig X}$ 就有 $r$ 階導數。反過來由導數推動差時，結論會弱一些，而且要分奇偶兩種情形: 若 $\phi\_{\sssig X}(t)$ 在 $t=0$ 的 $r$ 階導數存在，則 $r$ 為偶數時可得 $\mathbb{E}(\lvert X\rvert^{r})<\infty$，即 $r$ 階動差存在；$r$ 為奇數時一般只能得到 $r-1$ 階動差存在。也就是說，這個定理的逆向只在偶數階完全成立。

</div>

<div id="thm-cf-mgf-pgf-relation" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.29 (cf 與 mgf、pgf 的關係, relations among cf, mgf and pgf)</div>

若 $X$ 為一隨機變數，則

(1) 在 $M\_{\sssig X}$ 的自變數延伸到複數的意義之下
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

(1) 由[動差母函數的定義](/teaching-topics/ch2-p215-candidate/#def-mgf)，把 $M\_{\sssig X}$ 的自變數取為純虛數 $it$ 可得
{: .topic-paren-item}

$$
M_{\sssig X}(it)=\mathbb{E}\bigl(e^{itX}\bigr)=\phi_{\sssig X}(t)
$$

(2) 由[機率母函數的定義](/teaching-topics/ch2-p217-candidate/#def-pgf)，把 $G\_{\sssig X}$ 的自變數取為 $e^{it}$ 可得
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

此處的代入是合法的: 由 $\lvert e^{it}\rvert=1$ 可知該級數各項的絕對值之和為 $\sum\_{x=0}^{\infty}p\_{\sssig X}(x)=1$，級數絕對收斂。
{: .topic-paren-cont}

原式得證。 <span class="topic-qed">$\square$</span>
{: .topic-paren-cont}
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

[Definition 2.16](/teaching-topics/ch2-p215-candidate/#def-mgf) 只把 $M\_{\sssig X}$ 定義在實自變數上，並且要求該期望值在 $-h<t<h$ 之內皆存在。因此 $M\_{\sssig X}(it)$ 不是把 $it$ 直接代進一個已經定義好的函數，而是把定義式 $\mathbb{E}(e^{tX})$ 中的自變數容許取複數值之後才有的延伸寫法，[Theorem 2.29](#thm-cf-mgf-pgf-relation) 第 (1) 款所說的也正是延伸之後的兩式相等。特徵函數則不需要這一層延伸，它本來就直接定義在實自變數 $t$ 上。

</div>

有了基本性質與生成動差的方式之後，接著看特徵函數最有用的一項性質。

<div id="thm-cf-uniqueness" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.30 (特徵函數的唯一性, uniqueness of cf)</div>

若 $X, Y$ 為二隨機變數，則二者之特徵函數 $\phi\_{\sssig X}(t), \phi\_{\sssig Y}(t)$ 對一切 $t\in\mathbb{R}$ 皆相等，若且唯若二者之 cdf 亦相等，即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\phi_{\sssig X}(t)=\phi_{\sssig Y}(t),\ \forall\,t\in\mathbb{R}\Longleftrightarrow F_{\sssig X}(s)=F_{\sssig Y}(s),\ \forall\,s\in\mathbb{R}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\phi_{\sssig X}(t)=\phi_{\sssig Y}(t),\ \forall\,t\in\mathbb{R}\\[0.45em]
\Longleftrightarrow F_{\sssig X}(s)=F_{\sssig Y}(s),\ \forall\,s\in\mathbb{R}
\end{gathered}
$$

</div>

</div>

<div class="topic-proof" markdown="1">
**Proof.** 見黃文璋 (2010)，《機率論》，二版，第四章〈唯一性及倒轉公式〉一節；亦見 Billingsley (1995)，*Probability and Measure*，3rd ed.，第五章。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

唯一性的來源是**反演公式 <span lang="en">(inversion formula)</span>**，或譯為**倒轉公式**，它把分配由特徵函數反算回來。若 $a<b$ 皆為 $F\_{\sssig X}$ 的連續點，則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
F_{\sssig X}(b)-F_{\sssig X}(a)=\frac{1}{\,2\pi\,}\lim_{c\to\infty}\int_{-c}^{c}\frac{e^{-ita}-e^{-itb}}{it}\,\phi_{\sssig X}(t)\,dt
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&F_{\sssig X}(b)-F_{\sssig X}(a)\\[0.45em]
&\quad =\frac{1}{\,2\pi\,}\lim_{c\to\infty}\\[0.45em]
&\qquad\quad \int_{-c}^{c}\frac{e^{-ita}-e^{-itb}}{it}\,\phi_{\sssig X}(t)\,dt
\end{aligned}
$$

</div>

式中的被積函數在 $t=0$ 沒有定義，該點的值以連續延伸解釋，即取 $t\to0$ 的極限 $b-a$。

至於密度，須另加一個條件。若 $\int\_{-\infty}^{\infty}\lvert\phi\_{\sssig X}(t)\rvert\,dt<\infty$，則 $X$ 的 pdf 存在、有界且均勻連續，並且

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X}(x)=\frac{1}{\,2\pi\,}\int_{-\infty}^{\infty}e^{-itx}\,\phi_{\sssig X}(t)\,dt,\quad x\in\mathbb{R}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig X}(x)&=\frac{1}{\,2\pi\,}\int_{-\infty}^{\infty}e^{-itx}\,\phi_{\sssig X}(t)\,dt,\\[0.45em]
&\quad x\in\mathbb{R}
\end{aligned}
$$

</div>

特徵函數對每個分配都存在，但這並不表示每個隨機變數都有 pdf: 上面這個絕對可積的條件不成立時，反演只能停在 cdf 的層次，不能直接推得 pdf。

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

**獨立 <span lang="en">(independent)</span>** 與**同分配 <span lang="en">(identically distributed)</span>** 是我們在下一個章節才會提到的性質，在此階段讀者不妨想像成，每個隨機變數不互相影響，且客觀條件皆相同。在彼此獨立的前提之下，$e^{itX\_{1}},\ldots,e^{itX\_{n}}$ 也彼此不互相影響，期望值因而可以逐項相乘，即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\phi_{\sssig X_{1}+\cdots+X_{n}}(t)=\prod_{j=1}^{n}\phi_{\sssig X_{j}}(t),\quad t\in\mathbb{R}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\phi_{\sssig X_{1}+\cdots+X_{n}}(t)&=\prod_{j=1}^{n}\phi_{\sssig X_{j}}(t),\\[0.45em]
&\quad t\in\mathbb{R}
\end{aligned}
$$

</div>

正式的定義與證明留到下一個章節，這一式在下面的例題馬上就會用到。

</div>

<div id="ex-cauchy-sample-mean-cf" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.53</div>

<div lang="en" markdown="1">
Suppose that $X\_{1}, X\_{2}, \ldots, X\_{n}$ are independent and identically distributed random variables, each having the standard Cauchy pdf

$$
f(x)=\frac{1}{\,\pi(1+x^{2})\,},\quad x\in\mathbb{R}
$$

with common characteristic function $\phi(t)=e^{-\lvert t\rvert}$. Show that $\overline{X}\_{n}=\frac{1}{n}\sum\_{j=1}^{n}X\_{j}$ follows the same distribution as $X\_{1}$.
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
&\phi_{\sssig \overline{X}_{n}}(t)=\mathbb{E}\bigl(e^{it\overline{X}_{n}}\bigr)\\[0.45em]
&\quad =\mathbb{E}\Bigl(e^{\sum_{j=1}^{n}i\frac{t}{n}X_{j}}\Bigr)\\[0.45em]
&\quad =\mathbb{E}\Bigl(\prod_{j=1}^{n}e^{i\frac{t}{n}X_{j}}\Bigr)\\[0.45em]
&\quad =\prod_{j=1}^{n}\mathbb{E}\Bigl(e^{i\frac{t}{n}X_{j}}\Bigr)\\[0.45em]
&\quad =\prod_{j=1}^{n}\phi_{\sssig X_{j}}\Bigl(\frac{t}{\,n\,}\Bigr)\\[0.45em]
&\quad =\prod_{j=1}^{n}e^{-\left\lvert\frac{t}{n}\right\rvert}=\Bigl(e^{-\left\lvert\frac{t}{n}\right\rvert}\Bigr)^{n}\\[0.45em]
&\quad =e^{-\lvert t\rvert},\quad t\in\mathbb{R}
\end{aligned}
$$

</div>

這正是 $X\_{1}$ 的特徵函數，故由[特徵函數的唯一性](#thm-cf-uniqueness)可知，不論 $n$ 多大，皆有

$$
\overline{X}_{n}\sim\mathrm{Cauchy}(0,1)
$$

即 $\overline{X}\_{n}$ 與 $X\_{1}$ 同分配。原式得證。這道例題在後續章節討論中央極限定理時還會再出現。

</div>

最後把特徵函數與動差母函數放在一起，比較四件事。

第一是存在性。mgf 要求 $\mathbb{E}(e^{tX})$ 在 $t=0$ 的某個鄰域之內為有限，並不是每個分配都滿足；cf 則由 $\lvert e^{itX}\rvert=1$ 保證對每一個實值隨機變數與每一個 $t$ 都存在。[Example 2.53](#ex-cauchy-sample-mean-cf) 的標準柯西分配正是一個例子: 它連期望值都不存在，自然沒有 mgf，卻有 $\phi\_{\sssig X}(t)=e^{-\lvert t\rvert}$ 這個形式簡單的 cf。

第二是生成動差。[Theorem 2.21](/teaching-topics/ch2-p215-candidate/#thm-mgf-generates-moments) 說 mgf 微分 $r$ 次後在 $t=0$ 取值即得 <span class="text-nowrap">$\mathbb{E}(X^{r})$，</span>[Theorem 2.28](#thm-cf-generates-moments) 說 cf 的對應結果多一個 $i^{r}$。兩者的前提也不同: mgf 一旦存在便保證各階動差都存在，cf 這一邊則是逐階要求 $\mathbb{E}(\lvert X\rvert^{r})<\infty$，只換得到 $r$ 階為止。

第三是唯一性。兩者都有: [Theorem 2.23](/teaching-topics/ch2-p216-candidate/#thm-mgf-uniqueness) 說 mgf 相等則分配相等，[Theorem 2.30](#thm-cf-uniqueness) 說 cf 相等則分配相等。差別在於前者附帶了兩個 mgf 都要存在的條件，後者沒有這個附帶條件。

第四是能不能反過來求出分配的密度。mgf 做不到，離散型至多由 $p\_{\sssig 1}e^{a\_{1}t}+\cdots+p\_{\sssig n}e^{a\_{n}t}$ 的形式直接寫出 pmf，連續型只能回頭比對各個常見機率模型的 mgf；cf 則有反演公式，在 $\int\_{-\infty}^{\infty}\lvert\phi\_{\sssig X}(t)\rvert\,dt<\infty$ 之下可以直接算出 pdf。

## 本篇小結

[Definition 2.19](#def-characteristic-function) 把 $\mathbb{E}(e^{itX})$ 定義為 $X$ 的特徵函數 $\phi\_{\sssig X}(t)$。由歐拉公式可知 $\lvert e^{itX}\rvert=1$，因此這個期望值不必附加任何存在性條件，對每一個實值隨機變數與每一個 $t$ 都有定義，這正是它與動差母函數最大的差別。

[Theorem 2.27](#thm-cf-properties) 給了五項基本性質: $\phi\_{\sssig X}(0)=1$、$\lvert\phi\_{\sssig X}(t)\rvert\leqslant1$、在 $\mathbb{R}$ 上均勻連續、$\phi\_{\sssig X}(-t)=\overline{\phi\_{\sssig X}(t)}$，以及 $Y=aX+b$ 之下的 $\phi\_{\sssig Y}(t)=e^{ibt}\phi\_{\sssig X}(at)$。[Theorem 2.28](#thm-cf-generates-moments) 說明它同樣以微分生成原動差，只是每微分一次多出一個 $i$，因而在 $t=0$ 取值時得到 $i^{r}\mathbb{E}(X^{r})$；反過來由導數推動差則要分奇偶。[Theorem 2.29](#thm-cf-mgf-pgf-relation) 把它接回前兩篇的兩個母函數: 在自變數延伸到複數的意義之下 $\phi\_{\sssig X}(t)=M\_{\sssig X}(it)$，而非負整數隨機變數另有 $\phi\_{\sssig X}(t)=G\_{\sssig X}(e^{it})$。[Theorem 2.30](#thm-cf-uniqueness) 則是本篇的重點: 特徵函數相等若且唯若分配相同，並且由反演公式可以把 cdf 反算回來，在絕對可積的條件之下還可以算出 pdf。[Example 2.53](#ex-cauchy-sample-mean-cf) 示範了這項性質的用法，標準柯西分配的 $n$ 個獨立觀測值取平均之後，特徵函數仍是 <span class="text-nowrap">$e^{-\lvert t\rvert}$，</span>因此樣本平均數與單一觀測值同分配。

到這裡，動差、動差母函數、機率母函數、累積量母函數與特徵函數已經把「以一個函數表示整個分配」這條線走完。[下一篇](/teaching-topics/ch2-p219-candidate/)換一個處境: 分配的形式並不清楚，手上只有期望值，或再加上一個變異數，這時候能對機率說出什麼。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Patrick Billingsley. 1995. *Probability and Measure*. 3rd ed. Wiley.
- Kai Lai Chung. 2001. *A Course in Probability Theory*. 3rd ed. Academic Press.
- Eugene Lukacs. 1970. *Characteristic Functions*. 2nd ed. Griffin.
