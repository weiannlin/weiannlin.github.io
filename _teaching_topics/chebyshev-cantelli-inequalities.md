---
title: "柴比雪夫與坎特利不等式"
subtitle: "Chebyshev's and Cantelli's Inequalities"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 16
order: 216
permalink: /teaching-topics/chebyshev-cantelli-inequalities/
date: 2026-07-13
published: true
excerpt: '柴比雪夫不等式利用期望值與變異數控制雙邊偏離機率；坎特利不等式再針對單一方向給出更精確的界限。'
---

[上一篇的 Theorem 2.4](/teaching-topics/markov-inequality/#theorem-24) 由非負隨機變數的期望值建立尾端機率上界。令 $\mu_X=\mathbb{E}(X)$，且 $\sigma_X^2=\mathrm{Var}(X)$。在已知前二階動差的情況下，我們可以把平方離差放入該不等式，對隨機變數落在特定範圍內的機率進行一些推論。這其中，[柴比雪夫不等式 (Chebyshev's inequality)](#theorem-25) 同時處理期望值左右兩側的偏離；[坎特利不等式 (Cantelli's inequality)](#theorem-26) 則只處理其中一側。兩者都不需要指定 $X$ 屬於哪一種機率分配。

## 平方離差給出雙邊界限

若 $\mathbb{E}(X^2)<\infty$，則 $\mu_X$ 與 $\sigma_X^2$ 皆為有限值。對任意 $k>0$，事件 $\lvert X-\mu_X\rvert\geqslant k$ 與事件 $(X-\mu_X)^2\geqslant k^2$ 完全相同，因此可直接套用 [Theorem 2.4](/teaching-topics/markov-inequality/#theorem-24)。

<div id="theorem-25" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.5 (Chebyshev's Inequality)</div>

令 $X$ 為滿足 $\mathbb{E}(X^2)<\infty$ 的隨機變數，並令 $\mu_X=\mathbb{E}(X)$ 與 $\sigma_X^2=\mathrm{Var}(X)$。對每個 $k>0$，皆有

$$
\begin{aligned}
\mathbb{P}\bigl(\lvert X-\mu_X\rvert\geqslant k\bigr)
&\leqslant
\frac{\sigma_X^2}{k^2} \\[0.35em]
\mathbb{P}\bigl(\lvert X-\mu_X\rvert<k\bigr)
&\geqslant
1-\frac{\sigma_X^2}{k^2}
\end{aligned}
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.** 令 $Y=(X-\mu_X)^2$。因為 $Y\geqslant 0$ 且 $\mathbb{E}(Y)=\sigma_X^2$，由 [Theorem 2.4](/teaching-topics/markov-inequality/#theorem-24) 可得

$$
\begin{aligned}
\mathbb{P}\bigl(\lvert X-\mu_X\rvert\geqslant k\bigr)
&=
\mathbb{P}\bigl((X-\mu_X)^2\geqslant k^2\bigr) \\[0.35em]
&\leqslant
\frac{\mathbb{E}\bigl[(X-\mu_X)^2\bigr]}{k^2} \\[0.35em]
&=
\frac{\sigma_X^2}{k^2}
\end{aligned}
$$

另一個不等式再由餘事件取得。$\square$
</div>

若 $\sigma_X>0$，令 $k=a\sigma_X$，可將 [Theorem 2.5](#theorem-25) 改寫為標準差倍數的形式。對每個 $a>0$，皆有

$$
\begin{aligned}
\mathbb{P}\bigl(\lvert X-\mu_X\rvert\geqslant a\sigma_X\bigr)
&\leqslant
\frac{1}{a^2} \\[0.35em]
\mathbb{P}\bigl(\lvert X-\mu_X\rvert<a\sigma_X\bigr)
&\geqslant
1-\frac{1}{a^2}
\end{aligned}
$$

這個標準差倍數版本必須保留 $\sigma_X>0$ 的條件。若 $\sigma_X=0$，則 $\mathbb{P}(X=\mu_X)=1$，而 $\lvert X-\mu_X\rvert\geqslant a\sigma_X=0$ 的事件機率為 $1$，不能直接使用上式。

<div id="interlude-218" class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 2.18</div>

[Theorem 2.5](#theorem-25) 沒有假設分配對稱、單峰或呈鐘形。若 $\mathbb{E}(X^2)<\infty$ 且 $\sigma_X>0$，則有

$$
\begin{aligned}
\mathbb{P}\bigl(\lvert X-\mu_X\rvert<2\sigma_X\bigr)
&\geqslant
\frac{3}{4} \\[0.35em]
\mathbb{P}\bigl(\lvert X-\mu_X\rvert<3\sigma_X\bigr)
&\geqslant
\frac{8}{9}
\end{aligned}
$$

</div>

## 柴比雪夫界限何時能達到

在 [Theorem 2.5](#theorem-25) 以 $a$ 倍標準差表示距離 $k$ 的版本中，若考慮 $a\geqslant 1$，也就是考慮與期望值相距不小於一倍標準差的範圍，則右側的機率上界 $1/a^2$ 便不大於 $1$，因而開始進入有意義的範圍。當 $a=1$ 時，上界恰好等於 $1$，是有沒有額外資訊的分界；只有在 $a>1$ 時，上界才會小於 $1$。此即表示，使用柴比雪夫界限時，與期望值的距離至少須為一倍標準差，所得到的機率上界才開始有意義；若要得到小於 $1$ 的上界，則距離必須超過一倍標準差。

為了說明這個界限確實可以達到，固定常數 $\mu\in\mathbb{R}$、$\sigma>0$ 與 $a\geqslant 1$，並令 $X$ 在 $\mu-a\sigma$、$\mu$ 與 $\mu+a\sigma$ 三個位置的機率分別滿足

$$
\begin{gathered}
\mathbb{P}(X=\mu-a\sigma)
=
\mathbb{P}(X=\mu+a\sigma)
=
\frac{1}{2a^2} \\[0.35em]
\mathbb{P}(X=\mu)
=
1-\frac{1}{a^2}
\end{gathered}
$$

在這個分配下，$X$ 的期望值為 $\mu$，變異數為 $\sigma^2$；而 $X$ 落在 $\mu-a\sigma$ 或 $\mu+a\sigma$ 的機率總和恰為 $1/a^2$。因此

$$
\mathbb{P}\bigl(\lvert X-\mu\rvert\geqslant a\sigma\bigr)
=
\frac{1}{a^2}
$$

柴比雪夫界限的等號確實可以成立。這表示，只根據期望值與變異數，便無法將 $1/a^2$ 換成另一個對所有分配都成立、而且更小的機率上界。當 $0<a<1$ 時，因為 $1-1/a^2<0$，上述三點設定不再構成機率分配；同時，因為 $1/a^2>1$，通用上界應寫成 $\min\lbrace 1,1/a^2\rbrace=1$。

## 單邊偏離使用坎特利不等式

[Theorem 2.5](#theorem-25) 把左右兩側合在同一個事件中。若只關心 $X$ 大於期望值的方向，便可只對右尾建立上界。下列 [Theorem 2.6](#theorem-26) 也稱為單邊柴比雪夫不等式 (one-sided Chebyshev's inequality)，它利用相同的一二階動差給出較小的單邊界限。

<div id="theorem-26" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.6 (Cantelli's Inequality)</div>

令 $X$ 為滿足 $\mathbb{E}(X^2)<\infty$ 的隨機變數，並令 $\mu_X=\mathbb{E}(X)$ 與 $\sigma_X^2=\mathrm{Var}(X)$。對每個 $k>0$，皆有

$$
\begin{aligned}
\mathbb{P}(X-\mu_X\geqslant k)
&\leqslant
\frac{\sigma_X^2}{\sigma_X^2+k^2} \\[0.35em]
\mathbb{P}(X-\mu_X\leqslant-k)
&\leqslant
\frac{\sigma_X^2}{\sigma_X^2+k^2}
\end{aligned}
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.** 若 $\sigma_X^2=0$，則 $\mathbb{P}(X=\mu_X)=1$。因為 $k>0$，兩個尾端事件的機率皆為 $0$，此時結論成立。

以下令 $\sigma_X^2>0$，並令 $Y=X-\mu_X$。此時 $\mathbb{E}(Y)=0$，且 $\mathbb{E}(Y^2)=\sigma_X^2$。

任取 $c>0$。若 $Y\geqslant k$，則 $(Y+c)^2\geqslant(k+c)^2$，故由 [Theorem 2.4](/teaching-topics/markov-inequality/#theorem-24) 可得

$$
\begin{aligned}
\mathbb{P}(Y\geqslant k)
&\leqslant
\mathbb{P}\bigl((Y+c)^2\geqslant(k+c)^2\bigr) \\[0.35em]
&\leqslant
\frac{\mathbb{E}\bigl[(Y+c)^2\bigr]}{(k+c)^2} \\[0.35em]
&=
\frac{\sigma_X^2+c^2}{(k+c)^2}
\end{aligned}
$$

令 $g(c)=(\sigma_X^2+c^2)/(k+c)^2$，則 $g^{\prime}(c)=2(ck-\sigma_X^2)/(k+c)^3$。當 $0<c<\sigma_X^2/k$ 時，$g^{\prime}(c)<0$；當 $c>\sigma_X^2/k$ 時，$g^{\prime}(c)>0$。因此 $g(c)$ 在 $c=\sigma_X^2/k$ 取得最小值。代入可得

$$
\begin{aligned}
\mathbb{P}(Y\geqslant k)
&\leqslant
\left.
\frac{\sigma_X^2+c^2}{(k+c)^2}
\right|_{c=\sigma_X^2/k} \\[0.45em]
&=
\frac{\sigma_X^2}{\sigma_X^2+k^2}
\end{aligned}
$$

因為 $\mathbb{E}(-Y)=0$ 且 $\mathbb{E}[(-Y)^2]=\sigma_X^2$，把相同結果套用在 $-Y$，即可得到左尾界限。$\square$
</div>

若 $\sigma_X>0$，令 $k=a\sigma_X$，則對每個 $a>0$，皆有

$$
\begin{aligned}
\mathbb{P}(X-\mu_X\geqslant a\sigma_X)
&\leqslant
\frac{1}{1+a^2} \\[0.35em]
\mathbb{P}(X-\mu_X\leqslant-a\sigma_X)
&\leqslant
\frac{1}{1+a^2}
\end{aligned}
$$

坎特利界限同樣可以達到。若 $\sigma_X^2>0$，令 $Y=X-\mu_X$ 只取兩個值，且

$$
\mathbb{P}(Y=k)
=
\frac{\sigma_X^2}{\sigma_X^2+k^2},
\qquad
\mathbb{P}\left(Y=-\frac{\sigma_X^2}{k}\right)
=
\frac{k^2}{\sigma_X^2+k^2}
$$

則 $\mathbb{E}(Y)=0$、$\mathbb{E}(Y^2)=\sigma_X^2$，並且

$$
\mathbb{P}(Y\geqslant k)
=
\frac{\sigma_X^2}{\sigma_X^2+k^2}
$$

左尾等號情形只需把兩個取值的符號反轉。上述使等號成立的分配把機率放在門檻 $k$ 上。若把事件改成 $Y>k$，坎特利上界仍然成立，但這個兩點分配不再達到等號。

原因在於原二點分配中位於門檻 $k$ 的取值不再屬於事件。為了說明 $\mathbb{P}(Y>k)$ 仍可逼近坎特利上界，對每個 $\varepsilon>0$，令 $b=k+\varepsilon$，並令 $Y$ 只取 $b$ 與 $-\sigma_X^2/b$ 兩個值，其機率分別滿足

$$
\mathbb{P}(Y=b)
=
\frac{\sigma_X^2}{\sigma_X^2+b^2},
\qquad
\mathbb{P}\left(Y=-\frac{\sigma_X^2}{b}\right)
=
\frac{b^2}{\sigma_X^2+b^2}
$$

此時 $\mathbb{E}(Y)=0$、$\mathbb{E}(Y^2)=\sigma_X^2$。當 $\varepsilon\downarrow0$ 時，

$$
\mathbb{P}(Y>k)
=
\frac{\sigma_X^2}{\sigma_X^2+(k+\varepsilon)^2}
\longrightarrow
\frac{\sigma_X^2}{\sigma_X^2+k^2}
$$

由此可知，只知道 $\mathbb{E}(Y)=0$ 與 $\mathbb{E}(Y^2)=\sigma_X^2$ 時，不能把 $\sigma_X^2/(\sigma_X^2+k^2)$ 換成另一個對所有滿足這兩個動差條件的分配都成立、而且更小的機率上界。

不過，在上述 $\sigma_X^2>0$ 的情形下，沒有單一分配能在事件 $\lbrace Y>k\rbrace$ 上使坎特利界限取得等號。在 [Theorem 2.6](#theorem-26) 的證明中取 $c=\sigma_X^2/k$。若 $\mathbb{P}(Y>k)>0$，則 $(Y+c)^2>(k+c)^2$ 在事件 $\lbrace Y>k\rbrace$ 上成立，因此

$$
\begin{aligned}
\mathbb{P}(Y>k)
&<
\frac{\mathbb{E}[(Y+c)^2]}{(k+c)^2} \\[0.35em]
&=
\frac{\sigma_X^2}{\sigma_X^2+k^2}
\end{aligned}
$$

若 $\mathbb{P}(Y>k)=0$，事件機率也嚴格小於這個正的上界。

## 已知變異數如何改進界限

<div id="example-223" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.23 (An Income Upper Bound)</div>

延續上一篇的 [Example 2.22](/teaching-topics/markov-inequality/#example-222)，令非負隨機變數 $X$ 表示某地區家庭的年所得。現在假設 $\mathbb{E}(X)=100{,}000$，且 $\sigma_X=80{,}000$。

若只使用非負性與期望值，[Theorem 2.4](/teaching-topics/markov-inequality/#theorem-24) 給出

$$
\mathbb{P}(X\geqslant500{,}000)
\leqslant
\frac{100{,}000}{500{,}000}
=
0.2
$$

此事件包含於雙邊偏離事件中，因此由 [Theorem 2.5](#theorem-25) 可得

$$
\begin{aligned}
\mathbb{P}(X\geqslant500{,}000)
&=
\mathbb{P}(X-100{,}000\geqslant400{,}000) \\[0.35em]
&\leqslant
\mathbb{P}\bigl(\lvert X-100{,}000\rvert\geqslant400{,}000\bigr) \\[0.35em]
&\leqslant
\frac{80{,}000^2}{400{,}000^2}
=
0.04
\end{aligned}
$$

這裡只關心右尾，由 [Theorem 2.6](#theorem-26) 可得較小的上界。

$$
\begin{aligned}
\mathbb{P}(X\geqslant500{,}000)
&=
\mathbb{P}(X-100{,}000\geqslant400{,}000) \\[0.35em]
&\leqslant
\frac{80{,}000^2}{80{,}000^2+400{,}000^2} \\[0.35em]
&=
\frac{1}{26}
\approx
0.03846
\end{aligned}
$$

同一個尾端事件依序得到 $0.2$、$0.04$ 與約 $0.03846$ 三個上界。在這個例子中，加入變異數後，$\mathbb{P}(X\geqslant500{,}000)$ 的上界由 $0.2$ 降為 $0.04$；再利用這個事件只位於右尾，坎特利界限又將上界降為約 $0.03846$。
</div>

## 本篇小結

若 $X$ 具有有限二階動差，[Theorem 2.5](#theorem-25) 給出

$$
\mathbb{P}\bigl(\lvert X-\mu_X\rvert\geqslant k\bigr)
\leqslant
\frac{\sigma_X^2}{k^2}
$$

它不要求指定分配形式，只利用期望值與變異數控制雙邊偏離事件的機率。若只關心其中一側，[Theorem 2.6](#theorem-26) 給出

$$
\mathbb{P}(X-\mu_X\geqslant k)
\leqslant
\frac{\sigma_X^2}{\sigma_X^2+k^2}
$$

對 $a\geqslant1$，在 $\mu-a\sigma$、$\mu$ 與 $\mu+a\sigma$ 三點取值的分配可使柴比雪夫界限取得等號。對坎特利界限而言，事件寫成 $Y\geqslant k$ 時，在 $k$ 與 $-\sigma_X^2/k$ 兩點取值的分配可以取得等號；事件寫成 $Y>k$ 時，令 $b=k+\varepsilon$ 所建立的二點分配只能在 $\varepsilon\downarrow0$ 時逼近上界。將 $k$ 寫成 $a\sigma_X$ 時，仍須假設 $\sigma_X>0$；處理離散型分配時，也必須保留門檻是否包含等號的差別。

[下一篇文章](/teaching-topics/chernoff-inequality/)會把指數轉換與動差母函數放入 [Theorem 2.4](/teaching-topics/markov-inequality/#theorem-24)，得到可依參數最佳化的車諾夫界限。

## 參考文獻與延伸閱讀

- 黃文璋，2003，《機率論》，初版，華泰文化。
- 黃文璋，2003，《數理統計》，初版，華泰文化。
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Sheldon M. Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
