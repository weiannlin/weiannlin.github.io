---
title: "機率收斂的運算性質與連續映射定理"
subtitle: "Operations on Convergence in Probability and the Continuous Mapping Theorem"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 5
topic: 7
order: 507
permalink: /lecture-notes/continuous-mapping-theorem/
date: 2026-08-15
published: false
excerpt: "前面幾篇處理的都是單一序列的收斂，本篇轉而處理兩個機率收斂的序列之間的運算。Theorem 5.10 給出三款結果: 線性組合 $aX_n+bY_n$ 機率收斂至 $ac+bd$、乘積 $X_nY_n$ 機率收斂至 $cd$，以及連續函數轉換 $g(X_n)$ 機率收斂至 $g(c)$，最後一款即連續映射定理。三款的證明都建立在同一個集合包含關係之上，也就是兩項的和偏離其極限之和超過 $a+b$ 時，兩項之中至少有一項各自偏離超過 $a$ 或 $b$，本篇以一則註記把它單獨證明一次。由這三款還可以再得到差與商的結果。其後三道例題演練這些性質與弱大數法則的搭配: 不假設常態母體時樣本變異數仍然機率收斂至 $\\sigma^{2}$、對稱密度之下三次方和的極限分配與樣本二階動差的機率極限，以及伯努利樣本平均數倒數平方根的極限。"
---

[上一篇](/lecture-notes/normal-approximation-continuity-correction/)談常態近似與連續性校正。至此，讀者已經掌握了單一序列的收斂性質，也理解基於[中央極限定理](/lecture-notes/weak-law-and-central-limit-theorem/#thm-central-limit-theorem) <span lang="en">(central limit theorem, CLT)</span>，所得到與[常態分配](/lecture-notes/normal-distribution/#def-normal)相關的一些漸近特性。

然而，有的時候我們會好奇一些更進階的延伸特性，比如序列取了函數轉換後，在極限之下，收斂的對象會發生怎樣的改變呢? 會不會因此就不收斂了呢? 這些問題的解答，便是我們此處要探討的極限相關定理。

本篇先給出[機率收斂](/lecture-notes/convergence-in-probability/#def-converge-in-probability)之下的三項運算性質，其中第三項就是連續映射定理，並在一則註記中補上證明所倚賴的集合包含關係，以及由這三項再導出的差與商。其後以三道例題演練這些性質與[弱大數法則](/lecture-notes/weak-law-and-central-limit-theorem/#thm-weak-law-of-large-numbers) <span lang="en">(weak law of large numbers, WLLN)</span> 的搭配。

## 機率收斂的三項運算性質

<div id="thm-pconv-related" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 5.10 (機率收斂的運算性質與連續映射定理, operations on convergence in probability and the continuous mapping theorem)</div>

若 $X\_{n}\pconv c$、$Y\_{n}\pconv d$，且 $a,b,c$ 與 $d$ 皆為常數，則我們有

<ol class="topic-list-paren topic-list-paren--math">
  <li>
  $$
  aX_{n}+bY_{n}\pconv ac+bd
  $$
  </li>
  <li>
  $$
  X_{n}Y_{n}\pconv cd
  $$
  </li>
</ol>

(3) 若 $g(\cdot)$ 在 $c$ 上連續，則
{: .topic-paren-item}

$$
g(X_{n})\pconv g(c)
$$

上述 (3) 又被稱作**連續映射定理 <span lang="en">(continuous mapping theorem, CMT)</span>**。
{: .topic-paren-cont}

</div>

<div class="topic-proof" markdown="1">
**Proof.**

第 (1) 款由 $X\_{n}\pconv c$ 與 $Y\_{n}\pconv d$ 可知，對任意 $\varepsilon>0$ 我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_{n}-c\rvert>\varepsilon\bigr)=0,\quad\lim_{n\to\infty}\mathbb{P}\bigl(\lvert Y_{n}-d\rvert>\varepsilon\bigr)=0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_{n}-c\rvert>\varepsilon\bigr)&=0,\\[0.45em]
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert Y_{n}-d\rvert>\varepsilon\bigr)&=0
\end{aligned}
$$

</div>

把門檻各乘上 $\lvert a\rvert$ 與 $\lvert b\rvert$ 這兩個常數，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert aX_{n}-ac\rvert>\lvert a\rvert\varepsilon\bigr)=0,\quad\lim_{n\to\infty}\mathbb{P}\bigl(\lvert bY_{n}-bd\rvert>\lvert b\rvert\varepsilon\bigr)=0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert aX_{n}-ac\rvert>\lvert a\rvert\varepsilon\bigr)&=0,\\[0.45em]
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert bY_{n}-bd\rvert>\lvert b\rvert\varepsilon\bigr)&=0
\end{aligned}
$$

</div>

又由於

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lbrace\lvert(aX_{n}+bY_{n})-(ac+bd)\rvert>(\lvert a\rvert+\lvert b\rvert)\varepsilon\rbrace\subset\lbrace\lvert aX_{n}-ac\rvert>\lvert a\rvert\varepsilon\rbrace\cup\lbrace\lvert bY_{n}-bd\rvert>\lvert b\rvert\varepsilon\rbrace
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\lbrace\lvert(aX_{n}+bY_{n})-(ac+bd)\rvert>(\lvert a\rvert+\lvert b\rvert)\varepsilon\rbrace\\[0.45em]
&\qquad\subset\lbrace\lvert aX_{n}-ac\rvert>\lvert a\rvert\varepsilon\rbrace\\[0.45em]
&\qquad\qquad\cup\lbrace\lvert bY_{n}-bd\rvert>\lvert b\rvert\varepsilon\rbrace
\end{aligned}
$$

</div>

可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
&\mathbb{P}\bigl(\lvert(aX_{n}+bY_{n})-(ac+bd)\rvert>(\lvert a\rvert+\lvert b\rvert)\varepsilon\bigr)\\[0.45em]
&\qquad\leqslant\mathbb{P}\Bigl(\lbrace\lvert aX_{n}-ac\rvert>\lvert a\rvert\varepsilon\rbrace\cup\lbrace\lvert bY_{n}-bd\rvert>\lvert b\rvert\varepsilon\rbrace\Bigr)\\[0.45em]
&\qquad\leqslant\mathbb{P}\bigl(\lvert aX_{n}-ac\rvert>\lvert a\rvert\varepsilon\bigr)+\mathbb{P}\bigl(\lvert bY_{n}-bd\rvert>\lvert b\rvert\varepsilon\bigr)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}\bigl(\lvert(aX_{n}+bY_{n})-(ac+bd)\rvert\\[0.25em]
&\qquad\qquad>(\lvert a\rvert+\lvert b\rvert)\varepsilon\bigr)\\[0.45em]
&\qquad\leqslant\mathbb{P}\Bigl(\lbrace\lvert aX_{n}-ac\rvert>\lvert a\rvert\varepsilon\rbrace\\[0.25em]
&\qquad\qquad\cup\lbrace\lvert bY_{n}-bd\rvert>\lvert b\rvert\varepsilon\rbrace\Bigr)\\[0.45em]
&\qquad\leqslant\mathbb{P}\bigl(\lvert aX_{n}-ac\rvert>\lvert a\rvert\varepsilon\bigr)\\[0.25em]
&\qquad\qquad+\mathbb{P}\bigl(\lvert bY_{n}-bd\rvert>\lvert b\rvert\varepsilon\bigr)
\end{aligned}
$$

</div>

兩側同時取極限，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
&\lim_{n\to\infty}\mathbb{P}\bigl(\lvert(aX_{n}+bY_{n})-(ac+bd)\rvert>(\lvert a\rvert+\lvert b\rvert)\varepsilon\bigr)\\[0.45em]
&\qquad\leqslant\lim_{n\to\infty}\mathbb{P}\bigl(\lvert aX_{n}-ac\rvert>\lvert a\rvert\varepsilon\bigr)+\lim_{n\to\infty}\mathbb{P}\bigl(\lvert bY_{n}-bd\rvert>\lvert b\rvert\varepsilon\bigr)=0
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\lim_{n\to\infty}\mathbb{P}\bigl(\lvert(aX_{n}+bY_{n})\\[0.25em]
&\qquad\qquad-(ac+bd)\rvert>(\lvert a\rvert+\lvert b\rvert)\varepsilon\bigr)\\[0.45em]
&\qquad\leqslant\lim_{n\to\infty}\mathbb{P}\bigl(\lvert aX_{n}-ac\rvert>\lvert a\rvert\varepsilon\bigr)\\[0.25em]
&\qquad\qquad+\lim_{n\to\infty}\mathbb{P}\bigl(\lvert bY_{n}-bd\rvert>\lvert b\rvert\varepsilon\bigr)\\[0.25em]
&\qquad\qquad=0
\end{aligned}
$$

</div>

其中 $(\lvert a\rvert+\lvert b\rvert)\varepsilon$ 隨著 $\varepsilon$ 取遍全部的正數，故

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert(aX_{n}+bY_{n})-(ac+bd)\rvert>\varepsilon^{\prime}\bigr)=0,\ \ \forall\,\varepsilon^{\prime}>0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\lim_{n\to\infty}\mathbb{P}\bigl(\lvert(aX_{n}+bY_{n})\\[0.25em]
&\qquad\qquad-(ac+bd)\rvert>\varepsilon^{\prime}\bigr)=0,\\[0.45em]
&\qquad\qquad\qquad\forall\,\varepsilon^{\prime}>0
\end{aligned}
$$

</div>

此即 $aX\_{n}+bY\_{n}\pconv ac+bd$ 這個結果。

第 (2) 款先把差拆成兩項，可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\lbrace\lvert X_{n}Y_{n}-cd\rvert>\varepsilon\rbrace&=\lbrace\lvert X_{n}(Y_{n}-d)+d(X_{n}-c)\rvert>\varepsilon\rbrace\\[0.45em]
&\subset\Bigl\lbrace\lvert X_{n}(Y_{n}-d)\rvert>\frac{\varepsilon}{\,2\,}\Bigr\rbrace\cup\Bigl\lbrace\lvert d(X_{n}-c)\rvert>\frac{\varepsilon}{\,2\,}\Bigr\rbrace
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\lbrace\lvert X_{n}Y_{n}-cd\rvert>\varepsilon\rbrace\\[0.45em]
&=\lbrace\lvert X_{n}(Y_{n}-d)\\[0.25em]
&\qquad\qquad+d(X_{n}-c)\rvert>\varepsilon\rbrace\\[0.45em]
&\subset\Bigl\lbrace\lvert X_{n}(Y_{n}-d)\rvert>\frac{\varepsilon}{\,2\,}\Bigr\rbrace\\[0.25em]
&\qquad\cup\Bigl\lbrace\lvert d(X_{n}-c)\rvert>\frac{\varepsilon}{\,2\,}\Bigr\rbrace
\end{aligned}
$$

</div>

由此可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}\Bigl(\lvert X_{n}(Y_{n}-d)\rvert>\frac{\varepsilon}{\,2\,}\Bigr)&=\mathbb{P}\Bigl(\lvert X_{n}\rvert\lvert Y_{n}-d\rvert>\frac{\varepsilon}{\,2\,}\Bigr)\\[0.45em]
&=\mathbb{P}\Bigl(\Bigl\lbrace\lvert X_{n}\rvert\lvert Y_{n}-d\rvert>\frac{\varepsilon}{\,2\,}\Bigr\rbrace\cap\lbrace\lvert X_{n}\rvert\leqslant\lvert c\rvert+1\rbrace\Bigr)\\[0.45em]
&\qquad+\mathbb{P}\Bigl(\Bigl\lbrace\lvert X_{n}\rvert\lvert Y_{n}-d\rvert>\frac{\varepsilon}{\,2\,}\Bigr\rbrace\cap\lbrace\lvert X_{n}\rvert>\lvert c\rvert+1\rbrace\Bigr)\\[0.45em]
&\leqslant\mathbb{P}\biggl(\lvert Y_{n}-d\rvert>\frac{\varepsilon}{\,2(\lvert c\rvert+1)\,}\biggr)+\mathbb{P}\bigl(\lvert X_{n}\rvert>\lvert c\rvert+1\bigr)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}\Bigl(\lvert X_{n}(Y_{n}-d)\rvert>\frac{\varepsilon}{\,2\,}\Bigr)\\[0.45em]
&=\mathbb{P}\Bigl(\lvert X_{n}\rvert\lvert Y_{n}-d\rvert>\frac{\varepsilon}{\,2\,}\Bigr)\\[0.45em]
&=\mathbb{P}\Bigl(\Bigl\lbrace\lvert X_{n}\rvert\lvert Y_{n}-d\rvert>\frac{\varepsilon}{\,2\,}\Bigr\rbrace\\[0.25em]
&\qquad\qquad\cap\lbrace\lvert X_{n}\rvert\leqslant\lvert c\rvert+1\rbrace\Bigr)\\[0.45em]
&\qquad+\mathbb{P}\Bigl(\Bigl\lbrace\lvert X_{n}\rvert\lvert Y_{n}-d\rvert>\frac{\varepsilon}{\,2\,}\Bigr\rbrace\\[0.25em]
&\qquad\qquad\cap\lbrace\lvert X_{n}\rvert>\lvert c\rvert+1\rbrace\Bigr)\\[0.45em]
&\leqslant\mathbb{P}\biggl(\lvert Y_{n}-d\rvert>\frac{\varepsilon}{\,2(\lvert c\rvert+1)\,}\biggr)\\[0.25em]
&\qquad+\mathbb{P}\bigl(\lvert X_{n}\rvert>\lvert c\rvert+1\bigr)
\end{aligned}
$$

</div>

其中，由於 $X\_{n}\pconv c$，把 $X\_{n}$ 寫成 $(X\_{n}-c)+c$ 再取絕對值，可知 $\lbrace\lvert X\_{n}-c\rvert\leqslant1\rbrace\subset\lbrace\lvert X\_{n}\rvert\leqslant\lvert c\rvert+1\rbrace$，故我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_{n}\rvert\leqslant\lvert c\rvert+1\bigr)\geqslant\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_{n}-c\rvert\leqslant1\bigr)=1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_{n}\rvert\leqslant\lvert c\rvert+1\bigr)&\geqslant\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_{n}-c\rvert\leqslant1\bigr)\\[0.45em]
&=1
\end{aligned}
$$

</div>

又由於

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}\bigl(\lvert X_{n}Y_{n}-cd\rvert>\varepsilon\bigr)&\leqslant\mathbb{P}\Bigl(\lvert X_{n}(Y_{n}-d)\rvert>\frac{\varepsilon}{\,2\,}\Bigr)+\mathbb{P}\Bigl(\lvert d(X_{n}-c)\rvert>\frac{\varepsilon}{\,2\,}\Bigr)\\[0.45em]
&\leqslant\mathbb{P}\biggl(\lvert Y_{n}-d\rvert>\frac{\varepsilon}{\,2(\lvert c\rvert+1)\,}\biggr)+\mathbb{P}\bigl(\lvert X_{n}\rvert>\lvert c\rvert+1\bigr)\\[0.45em]
&\qquad+\mathbb{P}\Bigl(\lvert d(X_{n}-c)\rvert>\frac{\varepsilon}{\,2\,}\Bigr)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}\bigl(\lvert X_{n}Y_{n}-cd\rvert>\varepsilon\bigr)\\[0.45em]
&\leqslant\mathbb{P}\Bigl(\lvert X_{n}(Y_{n}-d)\rvert>\frac{\varepsilon}{\,2\,}\Bigr)\\[0.25em]
&\qquad+\mathbb{P}\Bigl(\lvert d(X_{n}-c)\rvert>\frac{\varepsilon}{\,2\,}\Bigr)\\[0.45em]
&\leqslant\mathbb{P}\biggl(\lvert Y_{n}-d\rvert>\frac{\varepsilon}{\,2(\lvert c\rvert+1)\,}\biggr)\\[0.25em]
&\qquad+\mathbb{P}\bigl(\lvert X_{n}\rvert>\lvert c\rvert+1\bigr)\\[0.25em]
&\qquad+\mathbb{P}\Bigl(\lvert d(X_{n}-c)\rvert>\frac{\varepsilon}{\,2\,}\Bigr)
\end{aligned}
$$

</div>

右側三項在 $n\to\infty$ 之下都趨於零，故

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_{n}Y_{n}-cd\rvert>\varepsilon\bigr)=0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_{n}Y_{n}-cd\rvert>\varepsilon\bigr)&=0
\end{aligned}
$$

</div>

此即 $X\_{n}Y\_{n}\pconv cd$ 這個結果。

第 (3) 款由於 $g(\cdot)$ 在 $c$ 上連續，故由連續之 $\varepsilon-\delta$ 定義可知，對任意 $\varepsilon>0$，存在 $\delta(\varepsilon)>0$，使得

$$
\lvert x-c\rvert<\delta(\varepsilon)\qquad\Longrightarrow\ \lvert g(x)-g(c)\rvert<\varepsilon
$$

故可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lbrace\lvert x-c\rvert<\delta(\varepsilon)\rbrace\subset\lbrace\lvert g(x)-g(c)\rvert<\varepsilon\rbrace,\ \forall\,\varepsilon>0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\lbrace\lvert x-c\rvert<\delta(\varepsilon)\rbrace&\subset\lbrace\lvert g(x)-g(c)\rvert<\varepsilon\rbrace,\\[0.45em]
&\qquad\forall\,\varepsilon>0
\end{aligned}
$$

</div>

此即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}\bigl(\lvert X_{n}-c\rvert<\delta(\varepsilon)\bigr)\leqslant\mathbb{P}\bigl(\lvert g(X_{n})-g(c)\rvert<\varepsilon\bigr),\ \forall\,\varepsilon>0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}\bigl(\lvert X_{n}-c\rvert<\delta(\varepsilon)\bigr)&\leqslant\mathbb{P}\bigl(\lvert g(X_{n})-g(c)\rvert<\varepsilon\bigr),\\[0.45em]
&\qquad\forall\,\varepsilon>0
\end{aligned}
$$

</div>

由於 $X\_{n}\pconv c$，我們有

$$
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_{n}-c\rvert<\delta\bigr)=1,\ \forall\,\delta>0
$$

故可知

<div class="topic-math-layout topic-math-layout--desktop topic-math-follow-before" markdown="1">

$$
\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_{n}-c\rvert<\delta(\varepsilon)\bigr)\leqslant\lim_{n\to\infty}\mathbb{P}\bigl(\lvert g(X_{n})-g(c)\rvert<\varepsilon\bigr)=1,\ \forall\,\varepsilon>0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile topic-math-follow-before" markdown="1">

$$
\begin{aligned}
&\lim_{n\to\infty}\mathbb{P}\bigl(\lvert X_{n}-c\rvert<\delta(\varepsilon)\bigr)\\[0.45em]
&\qquad\leqslant\lim_{n\to\infty}\mathbb{P}\bigl(\lvert g(X_{n})-g(c)\rvert<\varepsilon\bigr)\\[0.25em]
&\qquad\qquad=1,\ \forall\,\varepsilon>0
\end{aligned}
$$

</div>

<div class="topic-math-follow" markdown="1">

$$
\therefore\ g(X_{n})\pconv g(c)
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

上述皆使用到

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lbrace\lvert(X+Y)-(c+d)\rvert>a+b\rbrace\subset\lbrace\lvert X-c\rvert>a\rbrace\cup\lbrace\lvert Y-d\rvert>b\rbrace
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\lbrace\lvert(X+Y)-(c+d)\rvert>a+b\rbrace\\[0.45em]
&\qquad\subset\lbrace\lvert X-c\rvert>a\rbrace\\[0.25em]
&\qquad\qquad\cup\lbrace\lvert Y-d\rvert>b\rbrace
\end{aligned}
$$

</div>

之結果，證明如下。

<div class="topic-proof" markdown="1">
**Proof.**

令 $(x,y)\notin\lbrace\lvert X-c\rvert>a\rbrace\cup\lbrace\lvert Y-d\rvert>b\rbrace$ 則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
&\Longrightarrow\ (x,y)\in\lbrace\lvert X-c\rvert\leqslant a\rbrace\cap\lbrace\lvert Y-d\rvert\leqslant b\rbrace\\[0.45em]
&\Longrightarrow\ (x,y)\in\lbrace\lvert X-c\rvert+\lvert Y-d\rvert\leqslant a+b\rbrace\\[0.45em]
&\Longrightarrow\ (x,y)\in\lbrace\lvert(X+Y)-(c+d)\rvert\leqslant a+b\rbrace\\[0.45em]
&\Longrightarrow\ (x,y)\notin\lbrace\lvert(X+Y)-(c+d)\rvert>a+b\rbrace
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\Longrightarrow\ (x,y)\in\lbrace\lvert X-c\rvert\leqslant a\rbrace\\[0.25em]
&\qquad\qquad\cap\lbrace\lvert Y-d\rvert\leqslant b\rbrace\\[0.45em]
&\Longrightarrow\ (x,y)\in\lbrace\lvert X-c\rvert\\[0.25em]
&\qquad\qquad+\lvert Y-d\rvert\leqslant a+b\rbrace\\[0.45em]
&\Longrightarrow\ (x,y)\in\lbrace\lvert(X+Y)\\[0.25em]
&\qquad\qquad-(c+d)\rvert\leqslant a+b\rbrace\\[0.45em]
&\Longrightarrow\ (x,y)\notin\lbrace\lvert(X+Y)\\[0.25em]
&\qquad\qquad-(c+d)\rvert>a+b\rbrace
\end{aligned}
$$

</div>

由此可知

<div class="topic-math-layout topic-math-layout--desktop topic-math-follow-before" markdown="1">

$$
(x,y)\in\lbrace\lvert(X+Y)-(c+d)\rvert>a+b\rbrace
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile topic-math-follow-before" markdown="1">

$$
\begin{aligned}
&(x,y)\in\lbrace\lvert(X+Y)\\[0.25em]
&\qquad\qquad-(c+d)\rvert>a+b\rbrace
\end{aligned}
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop topic-math-follow" markdown="1">

$$
\Longrightarrow\ (x,y)\in\lbrace\lvert X-c\rvert>a\rbrace\cup\lbrace\lvert Y-d\rvert>b\rbrace
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile topic-math-follow" markdown="1">

$$
\begin{aligned}
&\Longrightarrow\ (x,y)\in\lbrace\lvert X-c\rvert>a\rbrace\\[0.25em]
&\qquad\qquad\cup\lbrace\lvert Y-d\rvert>b\rbrace
\end{aligned}
$$

</div>

此即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lbrace\lvert(X+Y)-(c+d)\rvert>a+b\rbrace\subset\lbrace\lvert X-c\rvert>a\rbrace\cup\lbrace\lvert Y-d\rvert>b\rbrace
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\lbrace\lvert(X+Y)-(c+d)\rvert>a+b\rbrace\\[0.45em]
&\qquad\subset\lbrace\lvert X-c\rvert>a\rbrace\\[0.25em]
&\qquad\qquad\cup\lbrace\lvert Y-d\rvert>b\rbrace
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

此外，由 (1)，我們當然也有

$$
X_{n}-Y_{n}\pconv c-d
$$

又由 CMT 可令 $g(x)=\frac{1}{\,x\,}$ 在 $d\neq0$ 上連續，則我們有 $\frac{1}{\,Y\_{n}\,}\pconv\frac{1}{\,d\,}$，搭配 (2) 可知

$$
\frac{\,X_{n}\,}{Y_{n}}\pconv\frac{c}{\,d\,}
$$

其中 $d\neq0$。

</div>

## 連續映射定理的例題

<div id="ex-s-squared-consistency-general" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.27 ($S^{2}$ 的一致性)</div>

<div lang="en" markdown="1">
Suppose that <span class="text-nowrap">$X_{1},\ldots,X_{n}\iidto(\mu,\sigma^{2})$,</span> and let $S^{2}=\frac{1}{\,n-1\,}\sum_{i=1}^{n}(X_{i}-\overline{X})^{2}$ denote the sample variance of these $n$ observations. Determine the value to which $S^{2}$ converges in probability.
</div>

先把樣本變異數改寫成樣本二階動差與樣本平均數平方的組合，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
S^{2}=\frac{1}{\,n-1\,}\sum_{i=1}^{n}(X_{i}-\overline{X})^{2}=\frac{n}{\,n-1\,}\biggl(\frac{1}{\,n\,}\sum_{i=1}^{n}X_{i}^{2}-\overline{X}^{2}\biggr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
S^{2}&=\frac{1}{\,n-1\,}\sum_{i=1}^{n}(X_{i}-\overline{X})^{2}\\[0.45em]
&=\frac{n}{\,n-1\,}\biggl(\frac{1}{\,n\,}\sum_{i=1}^{n}X_{i}^{2}-\overline{X}^{2}\biggr)
\end{aligned}
$$

</div>

又由 WLLN 可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\overline{X}=\frac{1}{\,n\,}\sum_{i=1}^{n}X_{i}\pconv\mu,\quad\frac{1}{\,n\,}\sum_{i=1}^{n}X_{i}^{2}\pconv\mathbb{E}\bigl(X_{i}^{2}\bigr)=\sigma^{2}+\mu^{2}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\overline{X}=\frac{1}{\,n\,}\sum_{i=1}^{n}X_{i}&\pconv\mu,\\[0.45em]
\frac{1}{\,n\,}\sum_{i=1}^{n}X_{i}^{2}&\pconv\mathbb{E}\bigl(X_{i}^{2}\bigr)=\sigma^{2}+\mu^{2}
\end{aligned}
$$

</div>

其中 $\mathbb{E}(X\_{i}^{2})=\sigma^{2}+\mu^{2}$ 來自[變異數的計算公式](/lecture-notes/variance/#thm-variance-formula)。若令 $g(x)=x^{2}$，則 $g(x)$ 在 $x=\mu$ 上連續，由 CMT 可知

$$
g(\overline{X})=\overline{X}^{2}\pconv\mu^{2}
$$

由此可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
S^{2}=\frac{n}{\,n-1\,}\biggl(\frac{1}{\,n\,}\sum_{i=1}^{n}X_{i}^{2}-\overline{X}^{2}\biggr)\pconv1\times\bigl(\sigma^{2}+\mu^{2}-\mu^{2}\bigr)=\sigma^{2}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
S^{2}&=\frac{n}{\,n-1\,}\biggl(\frac{1}{\,n\,}\sum_{i=1}^{n}X_{i}^{2}-\overline{X}^{2}\biggr)\\[0.45em]
&\pconv1\times\bigl(\sigma^{2}+\mu^{2}-\mu^{2}\bigr)\\[0.25em]
&=\sigma^{2}
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個問題和[範例 5.10](/lecture-notes/levy-continuity-theorem/#ex-s-squared-consistency-mgf)不同的地方在於，這題並沒有常態假設，但 $S^{2}\pconv\sigma^{2}$ 的結果卻仍然不變。

當然，我們也可以由此結果，搭配 CMT，令 $g(x)=\sqrt{x}$ 在 $x>0$ 連續，則我們有

$$
S=\sqrt{S^{2}}\pconv\sqrt{\sigma^{2}}=\sigma
$$

在稍後將有重要的應用。

</div>

<div id="ex-symmetric-density-moments" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.28</div>

<div lang="en" markdown="1">
Suppose that $X_{1},\ldots,X_{n}$ are independent and identically distributed with common distribution function <span class="text-nowrap">$F$,</span> that every moment of the common distribution is finite, and that the density $f=F^{\prime}$ satisfies $f(x)=f(-x)$ for every <span class="text-nowrap">$x$,</span> so that $f$ is symmetric about the origin.

<ol class="topic-list-paren">
  <li>Find the limiting distribution of <span class="text-nowrap">$T_{n}=n^{-\frac{1}{2}}\sum_{i=1}^{n}X_{i}^{3}$.</span></li>
  <li>Find the constant $c$ for which <span class="text-nowrap">$S_{n}\pconv c$,</span> where $S_{n}=n^{-1}\bigl(\sum_{i=1}^{n}X_{i}^{2}+\sum_{i=1}^{n}X_{i}^{3}\bigr)-n^{-2}\bigl(\sum_{i=1}^{n}X_{i}\bigr)^{2}$.</li>
</ol>
</div>

(1) 由於 $f$ 為對稱於 $0$ 之分配，故其奇數階[母體動差](/lecture-notes/moment-system/#def-population-moment)皆為零，即
{: .topic-paren-item}

$$
\mathbb{E}\bigl(X^{2k-1}\bigr)=0,\ \forall\,k=1,2,3,\ldots
$$

又由於 $X$ 之各階動差皆存在，可知 $\mathrm{Var}(X^{3})=\mathbb{E}(X^{6})<\infty$，則由 CLT 可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\sqrt{n}\biggl(\frac{1}{\,n\,}\sum_{i=1}^{n}X_{i}^{3}-\mathbb{E}\bigl(X^{3}\bigr)\biggr)=T_{n}\dconv W\sim\mathcal{N}\bigl(0,\mathbb{E}\bigl(X_{i}^{6}\bigr)\bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\sqrt{n}\biggl(\frac{1}{\,n\,}\sum_{i=1}^{n}X_{i}^{3}-\mathbb{E}\bigl(X^{3}\bigr)\biggr)&=T_{n}\\[0.45em]
&\dconv W\sim\mathcal{N}\bigl(0,\mathbb{E}\bigl(X_{i}^{6}\bigr)\bigr)
\end{aligned}
$$

</div>

(2) 由 WLLN 可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\frac{1}{\,n\,}\sum_{i=1}^{n}X_{i}\pconv\mathbb{E}(X_{i})=0,\quad\frac{1}{\,n\,}\sum_{i=1}^{n}X_{i}^{2}\pconv\mathbb{E}\bigl(X_{i}^{2}\bigr),\quad\frac{1}{\,n\,}\sum_{i=1}^{n}X_{i}^{3}\pconv\mathbb{E}\bigl(X_{i}^{3}\bigr)=0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\frac{1}{\,n\,}\sum_{i=1}^{n}X_{i}&\pconv\mathbb{E}(X_{i})=0,\\[0.45em]
\frac{1}{\,n\,}\sum_{i=1}^{n}X_{i}^{2}&\pconv\mathbb{E}\bigl(X_{i}^{2}\bigr),\\[0.45em]
\frac{1}{\,n\,}\sum_{i=1}^{n}X_{i}^{3}&\pconv\mathbb{E}\bigl(X_{i}^{3}\bigr)=0
\end{aligned}
$$

</div>

又由 CMT 可令 $g(x)=x^{2}$ 在 $x=\mathbb{E}(X\_{i})=0$ 上連續，則可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
g\biggl(\frac{1}{\,n\,}\sum_{i=1}^{n}X_{i}\biggr)=\biggl(\frac{1}{\,n\,}\sum_{i=1}^{n}X_{i}\biggr)^{2}\pconv0^{2}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
g\biggl(\frac{1}{\,n\,}\sum_{i=1}^{n}X_{i}\biggr)&=\biggl(\frac{1}{\,n\,}\sum_{i=1}^{n}X_{i}\biggr)^{2}\\[0.45em]
&\pconv0^{2}
\end{aligned}
$$

</div>

我們有
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
S_{n}&=n^{-1}\biggl(\sum_{i=1}^{n}X_{i}^{2}+\sum_{i=1}^{n}X_{i}^{3}\biggr)-n^{-2}\biggl(\sum_{i=1}^{n}X_{i}\biggr)^{2}\\[0.45em]
&\pconv0+\mathbb{E}\bigl(X_{i}^{2}\bigr)-0^{2}=\mathbb{E}\bigl(X_{i}^{2}\bigr)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
S_{n}&=n^{-1}\biggl(\sum_{i=1}^{n}X_{i}^{2}+\sum_{i=1}^{n}X_{i}^{3}\biggr)\\[0.25em]
&\qquad-n^{-2}\biggl(\sum_{i=1}^{n}X_{i}\biggr)^{2}\\[0.45em]
&\pconv0+\mathbb{E}\bigl(X_{i}^{2}\bigr)-0^{2}\\[0.25em]
&=\mathbb{E}\bigl(X_{i}^{2}\bigr)
\end{aligned}
$$

</div>

</div>

<div id="ex-bernoulli-inverse-square-root" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.29</div>

<div lang="en" markdown="1">
Suppose that <span class="text-nowrap">$X_{1},\ldots,X_{n}\iidto\mathrm{Bernoulli}(p)$,</span> where <span class="text-nowrap">$0<p<1$,</span> and let <span class="text-nowrap">$U_{n}=\frac{1}{\,n\,}\sum_{i=1}^{n}X_{i}$.</span> Find the limiting distribution of $\frac{1}{\,\sqrt{U_{n}}\,}$.
</div>

由 WLLN 可知 $U\_{n}=\frac{1}{\,n\,}\sum\_{i=1}^{n}X\_{i}\pconv p$，其中 $X\_{i}$ 服從[伯努利分配](/lecture-notes/bernoulli-trials-and-distribution/#def-bernoulli)，又由 CMT 可令 $g(x)=\frac{1}{\,\sqrt{x}\,}$ 在 $x=p$ 上連續，則可知

$$
g(U_{n})=\frac{1}{\,\sqrt{U_{n}}\,}\pconv\frac{1}{\,\sqrt{p}\,}
$$

此即

$$
\frac{1}{\,\sqrt{U_{n}}\,}\dconv Y\equiv\frac{1}{\,\sqrt{p}\,}
$$

</div>

## 本篇小結

[Theorem 5.10](#thm-pconv-related) 把機率收斂由單一序列推廣到兩個序列之間的運算，三款結果分別處理線性組合、乘積與連續函數轉換，其中第三款就是連續映射定理。三款證明的共同基礎是同一個集合包含關係: 兩項的和偏離其極限之和超過 $a+b$ 時，兩項之中至少有一項各自偏離超過 $a$ 或 $b$。有了這個包含關係，機率對聯集的上界就把一個難以直接處理的事件，換成兩個已知趨於零的事件之和。

由這三款還可以再往下推。第 (1) 款取 $a=1$ 與 $b=-1$ 即得 $X\_{n}-Y\_{n}\pconv c-d$；連續映射定理取 $g(x)=\frac{1}{\,x\,}$ 得 $\frac{1}{\,Y\_{n}\,}\pconv\frac{1}{\,d\,}$，再搭配第 (2) 款便得到商的結果 $\frac{\,X\_{n}\,}{Y\_{n}}\pconv\frac{c}{\,d\,}$，其中 $d\neq0$。也就是說，四則運算在機率收斂之下都可以逐項處理。

[Example 5.27](#ex-s-squared-consistency-general) 把樣本變異數寫成 $\frac{n}{\,n-1\,}\bigl(\frac{1}{\,n\,}\sum X\_{i}^{2}-\overline{X}^{2}\bigr)$ 這個形式，弱大數法則處理兩個樣本動差，連續映射定理處理 $\overline{X}^{2}$ 這一項，兩者合起來得到 $S^{2}\pconv\sigma^{2}$。與先前以動差母函數處理的版本相比，這一題完全沒有用到常態假設，結果卻相同；再取一次平方根，還得到 $S\pconv\sigma$ 這個在後續推論中很常用的結果。

[Example 5.28](#ex-symmetric-density-moments) 與 [Example 5.29](#ex-bernoulli-inverse-square-root) 則示範這兩條定理如何分工。前者的第一小題要的是極限分配，因此用中央極限定理，對稱性讓 $\mathbb{E}(X^{3})=0$，變異數則化為 $\mathbb{E}(X^{6})$；第二小題要的是機率極限，因此用弱大數法則求出三個樣本動差的極限，再以連續映射定理處理平方項。後者的作法相同，$U\_{n}\pconv p$ 之後取 $g(x)=\frac{1}{\,\sqrt{x}\,}$，得到的極限是一個退化隨機變數，因此收斂到常數 $\frac{1}{\,\sqrt{p}\,}$ 這件事，同時也是分配收斂。

以上各款都是針對機率收斂而生的。如果把分配收斂一併考慮進來，這些運算的結果將稍有變化，下一篇的史拉斯基定理處理的正是這件事，其後並由此發展出 Delta 法。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
