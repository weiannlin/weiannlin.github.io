---
title: "司徒頓 t 分配與常態母體下的抽樣分配"
subtitle: "Student’s t Distribution and Sampling Distributions under Normality"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 4
topic: 21
order: 421
permalink: /teaching-topics/student-t-distribution/
date: 2026-08-15
published: false
excerpt: "司徒頓 $t$ 分配的建構有賴於一個標準常態變數與一個與之獨立的卡方變數，兩者相除之後所得的商即服從 $t$ 分配，其自由度就是該卡方變數的自由度。本篇先給出定義與機率函數，再借助這個建構式與兩者的獨立性逐階求出各階原動差: 期望值為 $0$、變異數為 $\\frac{\\nu}{\\nu-2}$、偏態係數為 $0$，而峰態係數為 $\\frac{3(\\nu-2)}{\\nu-4}$，並說明自由度不足時各階動差為何發散。接著依序說明自由度趨於無窮時 $t$ 分配收斂至標準常態分配、自由度為 $1$ 時即為標準柯西分配，以及自由度較大者在相同右尾機率之下右尾點較小這件事。最後轉入常態母體下的抽樣分配，證明 $\\frac{\\overline{X}-\\mu}{S/\\sqrt{n}}$ 服從 $t(n-1)$ 分配，並一併整理 $\\sigma^{2}$ 已知時樣本平均數的抽樣分配與樣本變異數的抽樣分配。"
---

[上一篇](/teaching-topics/chi-squared-distribution/)給出[卡方分配](/teaching-topics/chi-squared-distribution/#def-chi-distribution)的定義，並以[科克蘭定理](/teaching-topics/chi-squared-distribution/#thm-cochran-theorem) <span lang="en">(Cochran’s Theorem)</span> 處理常態隨機樣本的平方和如何拆解成兩個獨立的卡方變數。本篇接著介紹常用抽樣分配中的第三個，也就是司徒頓 $t$ 分配。

$t$ 分配的建構有賴於一個標準常態變數與一個與之獨立的卡方變數，其自由度即為該卡方變數的自由度。本篇先給出定義與機率函數，再由這個建構式逐階求出各階原動差，並說明自由度不足時各階動差為何發散。接著依序說明 $t$ 分配與[標準常態分配](/teaching-topics/normal-distribution/#def-normal)的關係、自由度為 $1$ 的特例，以及不同自由度之下密度曲線的形狀。

其後以一道例題檢驗這幾項性質，並由圖形比較不同自由度的右尾點。最後轉入常態母體下的抽樣分配，證明 $\sigma^{2}$ 未知時樣本平均數所對應的統計量服從 $t$ 分配，並一併整理常態母體下另外三個常用的抽樣分配結果。

## 司徒頓 $t$ 分配

<div id="def-t-distribution" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 4.23 (司徒頓 $t$ 分配, Student’s $t$ distribution)</div>

**適用範圍**:

司徒頓 $t$ 分配 <span lang="en">(Student’s $t$ distribution)</span> 也是鐘形的一種，與標準常態分配很類似，但尾部機率較為肥厚。與卡方分配相似的是，司徒頓 $t$ 分配具有**自由度 <span lang="en">(degree of freedom, df)</span>**。

**值域範圍**:

$$
\mathcal{R}_{\sssig T}=\lbrace\,t\mid-\infty<t<\infty\,\rbrace
$$

**表示式**:

$$
T\sim t(\nu)
$$

**自由度**:

$\nu>0$ 為司徒頓 $t$ 分配的自由度，通常設為正整數，但不限於此。

**機率函數**:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig T}(t)=\frac{\Gamma\bigl(\frac{\nu+1}{2}\bigr)}{\Gamma\bigl(\frac{\nu}{2}\bigr)\sqrt{\nu\pi}}\biggl(1+\frac{\,t^{2}\,}{\nu}\biggr)^{-\frac{\nu+1}{2}}=\frac{1}{\,\mathcal{B}\bigl(\frac{\nu}{2},\frac{1}{2}\bigr)\sqrt{\nu}\,}\biggl(1+\frac{\,t^{2}\,}{\nu}\biggr)^{-\frac{\nu+1}{2}},\ -\infty<t<\infty
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig T}(t)&=\frac{\Gamma\bigl(\frac{\nu+1}{2}\bigr)}{\Gamma\bigl(\frac{\nu}{2}\bigr)\sqrt{\nu\pi}}\biggl(1+\frac{\,t^{2}\,}{\nu}\biggr)^{-\frac{\nu+1}{2}}\\[0.45em]
&=\frac{1}{\,\mathcal{B}\bigl(\frac{\nu}{2},\frac{1}{2}\bigr)\sqrt{\nu}\,}\biggl(1+\frac{\,t^{2}\,}{\nu}\biggr)^{-\frac{\nu+1}{2}},\\[0.25em]
&\qquad-\infty<t<\infty
\end{aligned}
$$

</div>

**期望值、變異數**:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(T)&=0,\ \nu>1\quad(\,\nu\leqslant1\ \text{時期望值發散}\,)\\[0.45em]
\mathrm{Var}(T)&=\frac{\nu}{\,\nu-2\,},\ \nu>2\quad(\,\nu\leqslant2\ \text{時變異數發散}\,)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(T)&=0,\ \nu>1\\[0.25em]
&\qquad(\,\nu\leqslant1\ \text{時期望值發散}\,)\\[0.45em]
\mathrm{Var}(T)&=\frac{\nu}{\,\nu-2\,},\ \nu>2\\[0.25em]
&\qquad(\,\nu\leqslant2\ \text{時變異數發散}\,)
\end{aligned}
$$

</div>

</div>

司徒頓 $t$ 分配有一些地方需要注意:

(1) $t$ 分配的建構有賴於獨立的標準常態分配與卡方分配，構造如下:
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\boxed{\ \text{令 }Z\sim\mathcal{N}(0,1)\indep X\sim\chi^{2}(\nu)\text{，定義 }T=\frac{Z}{\,\sqrt{X/\nu}\,}\text{，則 }T\sim t(\nu)\ }
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\boxed{
\begin{aligned}
&\text{令 }Z\sim\mathcal{N}(0,1)\indep X\sim\chi^{2}(\nu)\text{，}\\[0.35em]
&\text{定義 }T=\frac{Z}{\,\sqrt{X/\nu}\,}\text{，則 }T\sim t(\nu)
\end{aligned}
}
$$

</div>

其中，司徒頓 $t$ 分配的自由度 <span class="text-nowrap">$\nu$，</span>正是卡方分配的自由度 <span class="text-nowrap">$\nu$。</span>
{: .topic-paren-cont}

(2) 證明司徒頓 $t$ 分配的各階動差時，我們可以借助 $Z\indep X$ 的特性來完成。證明如下:
{: .topic-paren-item}

<div class="topic-proof" markdown="1">
**Proof.**

先求期望值，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(T)=\mathbb{E}\biggl(\frac{Z}{\,\sqrt{X/\nu}\,}\biggr)=\mathbb{E}(Z)\,\mathbb{E}\biggl(\frac{1}{\,\sqrt{X/\nu}\,}\biggr)=0\times\nu^{\frac{1}{2}}\times\mathbb{E}\bigl(X^{-\frac{1}{2}}\bigr)=0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(T)&=\mathbb{E}\biggl(\frac{Z}{\,\sqrt{X/\nu}\,}\biggr)\\[0.45em]
&=\mathbb{E}(Z)\,\mathbb{E}\biggl(\frac{1}{\,\sqrt{X/\nu}\,}\biggr)\\[0.45em]
&=0\times\nu^{\frac{1}{2}}\times\mathbb{E}\bigl(X^{-\frac{1}{2}}\bigr)=0
\end{aligned}
$$

</div>

其中，$\mathbb{E}\bigl(X^{-\frac{1}{2}}\bigr)$ 在 $\nu=1$ 時並不存在，故 $\mathbb{E}(T)$ 不存在。

接著求二階原動差，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl(T^{2}\bigr)&=\mathbb{E}\biggl(\frac{Z^{2}}{\,X/\nu\,}\biggr)=\mathbb{E}\bigl(Z^{2}\bigr)\times\nu\times\mathbb{E}\biggl(\frac{1}{\,X\,}\biggr)\\[0.45em]
&=1\times\nu\times\mathbb{E}\bigl(X^{-1}\bigr)=\nu\times\frac{1}{\,\nu-2\,}=\frac{\nu}{\,\nu-2\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl(T^{2}\bigr)&=\mathbb{E}\biggl(\frac{Z^{2}}{\,X/\nu\,}\biggr)\\[0.45em]
&=\mathbb{E}\bigl(Z^{2}\bigr)\times\nu\times\mathbb{E}\biggl(\frac{1}{\,X\,}\biggr)\\[0.45em]
&=1\times\nu\times\mathbb{E}\bigl(X^{-1}\bigr)\\[0.45em]
&=\nu\times\frac{1}{\,\nu-2\,}=\frac{\nu}{\,\nu-2\,}
\end{aligned}
$$

</div>

故有

$$
\mathrm{Var}(T)=\frac{\nu}{\,\nu-2\,}
$$

其中，$\mathbb{E}\bigl(X^{-1}\bigr)=\frac{1}{\,\nu-2\,}$ 在 $\nu\leqslant2$ 時並不存在，故 $\mathbb{E}\bigl(T^{2}\bigr)$ 不存在。

再求三階原動差，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}\bigl(T^{3}\bigr)=\mathbb{E}\bigl[Z^{3}(X/\nu)^{-\frac{3}{2}}\bigr]=\mathbb{E}\bigl(Z^{3}\bigr)\,\mathbb{E}\bigl[(X/\nu)^{-\frac{3}{2}}\bigr]=0\times\nu^{\frac{3}{2}}\times\mathbb{E}\bigl(X^{-\frac{3}{2}}\bigr)=0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl(T^{3}\bigr)&=\mathbb{E}\bigl[Z^{3}(X/\nu)^{-\frac{3}{2}}\bigr]\\[0.45em]
&=\mathbb{E}\bigl(Z^{3}\bigr)\,\mathbb{E}\bigl[(X/\nu)^{-\frac{3}{2}}\bigr]\\[0.45em]
&=0\times\nu^{\frac{3}{2}}\times\mathbb{E}\bigl(X^{-\frac{3}{2}}\bigr)=0
\end{aligned}
$$

</div>

故有

$$
\alpha_{3}=0
$$

由此可知 $t$ 分配為對稱分配。其中，$\mathbb{E}\bigl(X^{-\frac{3}{2}}\bigr)$ 在 $\nu\leqslant3$ 時並不存在，故 $\mathbb{E}\bigl(T^{3}\bigr)$ 不存在。

最後求四階原動差，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl(T^{4}\bigr)&=\mathbb{E}\bigl[Z^{4}(X/\nu)^{-2}\bigr]=\mathbb{E}\bigl(Z^{4}\bigr)\,\mathbb{E}\bigl[(X/\nu)^{-2}\bigr]=3\times\nu^{2}\times\mathbb{E}\bigl(X^{-2}\bigr)\\[0.45em]
&=3\times\nu^{2}\times\frac{1}{\,(\nu-2)(\nu-4)\,}=\frac{3\nu^{2}}{\,(\nu-2)(\nu-4)\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl(T^{4}\bigr)&=\mathbb{E}\bigl[Z^{4}(X/\nu)^{-2}\bigr]\\[0.45em]
&=\mathbb{E}\bigl(Z^{4}\bigr)\,\mathbb{E}\bigl[(X/\nu)^{-2}\bigr]\\[0.45em]
&=3\times\nu^{2}\times\mathbb{E}\bigl(X^{-2}\bigr)\\[0.45em]
&=3\times\nu^{2}\times\frac{1}{\,(\nu-2)(\nu-4)\,}\\[0.45em]
&=\frac{3\nu^{2}}{\,(\nu-2)(\nu-4)\,}
\end{aligned}
$$

</div>

故有

$$
\alpha_{4}=\frac{\,3(\nu-2)\,}{\nu-4}>3
$$

由此可知 $t$ 分配為厚尾分配。其中，$\mathbb{E}\bigl(X^{-2}\bigr)=\frac{1}{\,(\nu-2)(\nu-4)\,}$ 在 $\nu\leqslant4$ 時並不存在，故 $\mathbb{E}\bigl(T^{4}\bigr)$ 不存在。

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

$t$ 分配各階原動差的證明，使用到卡方分配的 $k$ 階原動差，讀者可以利用卡方分配也是一種[伽瑪分配](/teaching-topics/gamma-distribution/#def-gamma-distribution)的特色，參考該篇中 $k$ 階原動差的證明計算。

特別的是，當時我們特別指出 <span class="text-nowrap">$k\in\bigl(\lbrace0\rbrace\cup\mathbb{N}\bigr)$，</span>便是為了避免如此處的狀況，也就是當 $\alpha+k$ 是負值時，原動差將發散，這也是 $t(\nu)$ 分配的 $\nu$ 階動差及更高次的動差都不存在的原因。

此外，在證明各種形狀參數的過程中，有時會使用到標準常態分配的特性，譬如 $\mathbb{E}\bigl(Z^{4}\bigr)=3$ 即為標準常態分配的[峰態係數](/teaching-topics/measures-of-shape/#def-kurtosis)，再搭配原動差轉主動差的計算技巧，可以得到各種形狀參數。這些技巧與知識在稍早的章節中已經提過，便不再贅述。

</div>

(3) $t$ 分配與標準常態分配非常相似，其中，當自由度 $\nu$ 上升時，變異數 $\mathrm{Var}(T)=\frac{\nu}{\,\nu-2\,}$ 會向下趨近於 <span class="text-nowrap">$1$；</span>而峰態係數 $\alpha_{4}=\frac{\,3(\nu-2)\,}{\nu-4}$ 則向下趨近於 <span class="text-nowrap">$3$，</span>與標準常態分配越來越接近。進一步而言，我們有
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\boxed{\ \text{若 }T\sim t(\nu)\text{，則 }T\xrightarrow[\ \nu\to\infty\ ]{\ \mathrm{d}\ }Z\sim\mathcal{N}(0,1)\ }
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\boxed{
\begin{aligned}
\text{若 }T&\sim t(\nu)\text{，則}\\[0.35em]
T&\xrightarrow[\ \nu\to\infty\ ]{\ \mathrm{d}\ }Z\sim\mathcal{N}(0,1)
\end{aligned}
}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

在自由度足夠大的前提下，由於標準常態分配與司徒頓 $t$ 分配的期望值都是 <span class="text-nowrap">$0$，</span>峰態係數向下趨近於 $3$ 說明了「在分配的尾部，同樣的位置，$t$ 分配具有較大的機率密度，也具有較大的**尾機率 <span lang="en">(tail-probability)</span>**」；而隨著自由度越來越大，$t$ 分配會越來越接近於標準常態。[^slutsky]

</div>

(4) 自由度為 $1$ 的 $t$ 分配 (即 $t(1)$ 分配)，是 $t$ 分配的特例，也被稱作**標準柯西分配 <span lang="en">(standard Cauchy distribution)</span>**，其機率密度函數為
{: .topic-paren-item}

$$
f_{\sssig X}(x)=\frac{1}{\,\pi(1+x^{2})\,},\ -\infty<x<\infty
$$

且這個分配期望值與變異數皆發散。[^cauchy]
{: .topic-paren-cont}

(5) 司徒頓 $t$ 分配在不同自由度與標準常態分配的圖形如下所示:
{: .topic-paren-item}

<figure id="fig-student-t-density-family" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/student-t-density-family.svg" alt="一條水平座標軸，兩端各有一個箭頭，軸上有十三個刻度，由左至右標為負 6 到 6 的十三個整數，軸的右端標 t。座標軸上方有四條左右對稱的鐘形密度曲線，全部以 0 為中心，並在正負 2 附近彼此交叉。在中央，由低到高依序是點劃線、點線、虛線與一條較粗的實線；在兩側的尾部順序完全相反，點劃線最高，較粗的實線最低、也最早貼上座標軸。圖的右上角有一個圖例，四段短線由上而下依序標為 t 括號 1、t 括號 3、t 括號 10，以及花體 N 括號 0 逗號 1。">
  <figcaption><span class="topic-figure__label">Fig. 4.7.</span> 四條密度曲線畫在同一組座標軸上，都以 $0$ 為中心左右對稱。自由度愈小，中央的高度愈低，兩側的尾部愈厚；自由度愈大，曲線就愈貼近圖例中標為 $\mathcal{N}(0,1)$ 的那一條。</figcaption>
</figure>

上圖可以很清楚地看出來，所謂「$t$ 分配比起標準常態分配較為厚尾」的情況是如何；而且很容易就能看出，隨著自由度越來越大，$t$ 分配也會越來越趨近於標準常態分配。
{: .topic-paren-cont}

## $t$ 分配的性質與不同自由度的右尾點

<div id="ex-student-t-1" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.54</div>

<div lang="en" markdown="1">
Determine which one of the following statements about the $t$ distribution is **incorrect**.

(A) Its mean is allowed to take a negative value.
{: .topic-paren-item}

(B) As the number of degrees of freedom grows, the distribution comes closer to the normal distribution.
{: .topic-paren-item}

(C) The distribution is a symmetric one.
{: .topic-paren-item}

(D) For two degrees of freedom with <span class="text-nowrap">$\nu_1>\nu_2$,</span> the value of $t_{\alpha}(\nu_1)$ always falls below the value of <span class="text-nowrap">$t_{\alpha}(\nu_2)$,</span> where $\alpha$ denotes a right-tail probability.
{: .topic-paren-item}
</div>

答案選 <span class="text-nowrap">(A)，</span>因為若 $t$ 分配的期望值存在，則必定為 <span class="text-nowrap">$0$。</span>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

關於 (D) 選項的敘述，讀者可以下圖進行比對:

<figure id="fig-student-t-tail-comparison" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/student-t-tail-comparison.svg" alt="同一組座標上畫兩條左右對稱的鐘形密度曲線，只以線型分辨。虛線那一條的峰較高，兩側下降較快；實線那一條的峰較低，在離中央較遠處反而高於虛線，兩端的尾部拖得較長。橫軸右半邊有兩個刻度，較靠近中央的一個由虛線曲線垂直落下一條虛線到橫軸，軸下標 t_α(10)；較遠的一個由實線曲線垂直落下一條實線到橫軸，軸下標 t_α(1)。這兩個落點以右、曲線之下到橫軸之間的區域以淡紅色填滿，靠內的一段以虛線曲線為上界，過了較遠的落點之後改以實線曲線為上界，一路延伸到圖的右緣。橫軸中央另有一個刻度，其下另起一排標 0；橫軸右端有箭頭並標 t，圖中沒有縱軸，也沒有縱軸刻度。右上角的圖例分兩列，上列實線標 t(1)，下列虛線標 t(10)。">
  <figcaption><span class="topic-figure__label">Fig. 4.8.</span> 兩條密度曲線各取一塊機率相同的右尾，起點分別為 $t_{\alpha}(10)$ 與 <span class="text-nowrap">$t_{\alpha}(1)$，</span>前者落在後者的左邊。</figcaption>
</figure>

由上圖中可以發現，自由度較大的 $t$ 分配，在相同的右尾機率下，其右尾點的數值確實較小，也就是

$$
t_{\alpha}(\nu_1)>t_{\alpha}(\nu_2),\ \forall\,0<\nu_1<\nu_2
$$

值得一提的是，因為這個理由，我們當然有

$$
z_{\sssig \alpha}<t_{\alpha}(\nu),\ \forall\,\nu>0
$$

</div>

## 常態母體下的抽樣分配

以下轉入常態母體下統計量的抽樣分配: 下列各項結果談的是常態隨機樣本所算出的統計量服從什麼分配，而 $t$ 分配在其中扮演的角色，正是 $\sigma^{2}$ 未知時樣本平均數所對應的分配。

<div id="thm-xbar-samp-dist" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 4.24 (樣本平均數 $\overline{X}$ 的抽樣分配 ($\sigma^{2}$ 未知))</div>

若 <span class="text-nowrap">$X_1,X_2,\ldots,X_n\overset{\mathrm{iid}}{\sim}\mathcal{N}(\mu,\sigma^{2})$，</span>其中 $\mu$ 為待估參數，且 $\sigma^{2}$ 未知，則

$$
T=\frac{\,\overline{X}-\mu\,}{\frac{S}{\,\sqrt{n}\,}}\sim t(n-1)
$$

其中

$$
S^{2}=\frac{1}{\,n-1\,}\sum_{i=1}^{n}\bigl(X_i-\overline{X}\bigr)^{2}
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.**

由科克蘭定理，我們已知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\frac{\,(n-1)S^{2}\,}{\sigma^{2}}\sim\chi^{2}(n-1)\indep\frac{\,\overline{X}-\mu\,}{\frac{\sigma}{\,\sqrt{n}\,}}\sim\mathcal{N}(0,1)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\frac{\,(n-1)S^{2}\,}{\sigma^{2}}&\sim\chi^{2}(n-1)\\[0.35em]
&\indep\frac{\,\overline{X}-\mu\,}{\frac{\sigma}{\,\sqrt{n}\,}}\sim\mathcal{N}(0,1)
\end{aligned}
$$

</div>

若令

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
X=\frac{\,(n-1)S^{2}\,}{\sigma^{2}},\quad Z=\frac{\,\overline{X}-\mu\,}{\frac{\sigma}{\,\sqrt{n}\,}},\quad T=\frac{Z}{\,\sqrt{\frac{X}{\,n-1\,}}\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
X&=\frac{\,(n-1)S^{2}\,}{\sigma^{2}},\\[0.45em]
Z&=\frac{\,\overline{X}-\mu\,}{\frac{\sigma}{\,\sqrt{n}\,}},\\[0.45em]
T&=\frac{Z}{\,\sqrt{\frac{X}{\,n-1\,}}\,}
\end{aligned}
$$

</div>

則 $T$ 符合 $t$ 分配的建構式 <span class="text-nowrap">$T=\frac{Z}{\,\sqrt{X/\nu}\,}$，</span>由此可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
T=\frac{Z}{\,\sqrt{\frac{X}{\,n-1\,}}\,}=\frac{\frac{\overline{X}-\mu}{\frac{\sigma}{\sqrt{n}}}}{\,\sqrt{\frac{\frac{(n-1)S^{2}}{\sigma^{2}}}{n-1}}\,}=\frac{\,\frac{\overline{X}-\mu}{\frac{\sigma}{\sqrt{n}}}\,}{\frac{\,S\,}{\sigma}}=\frac{\,\overline{X}-\mu\,}{\frac{S}{\,\sqrt{n}\,}}\sim t(n-1)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
T&=\frac{Z}{\,\sqrt{\frac{X}{\,n-1\,}}\,}=\frac{\frac{\overline{X}-\mu}{\frac{\sigma}{\sqrt{n}}}}{\,\sqrt{\frac{\frac{(n-1)S^{2}}{\sigma^{2}}}{n-1}}\,}\\[0.45em]
&=\frac{\,\frac{\overline{X}-\mu}{\frac{\sigma}{\sqrt{n}}}\,}{\frac{\,S\,}{\sigma}}=\frac{\,\overline{X}-\mu\,}{\frac{S}{\,\sqrt{n}\,}}\sim t(n-1)
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

事實上，上述定理本身，以及證明這個定理的先決條件，正是在應用統計學中大量使用的，在常態母體下抽樣分配的結果，我們將其一併整理如下:

**樣本平均數 $\overline{X}$ 的抽樣分配 ($\sigma^{2}$ 已知)**:

若 <span class="text-nowrap">$X_1,X_2,\ldots,X_n\overset{\mathrm{iid}}{\sim}\mathcal{N}(\mu,\sigma^{2})$，</span>其中 $\mu$ 為待估參數，且 $\sigma^{2}$ 已知，則我們有

$$
Z=\frac{\,\overline{X}-\mu\,}{\frac{\sigma}{\,\sqrt{n}\,}}\sim\mathcal{N}(0,1)
$$

<div class="topic-proof" markdown="1">
**Proof.**

這個結果只要使用[常態分配的線性組合可加性](/teaching-topics/normal-distribution/)就可以很簡單地得到。 <span class="topic-qed">$\square$</span>
</div>

**樣本變異數 $S^{2}$ 的抽樣分配 ($\mu$ 未知)**:

若 <span class="text-nowrap">$X_1,X_2,\ldots,X_n\overset{\mathrm{iid}}{\sim}\mathcal{N}(\mu,\sigma^{2})$，</span>其中 $\sigma^{2}$ 為待估參數，且 $\mu$ 未知，則我們有

$$
\frac{\,(n-1)S^{2}\,}{\sigma^{2}}\sim\chi^{2}(n-1)
$$

<div class="topic-proof" markdown="1">
**Proof.**

這個結果可由科克蘭定理得到。 <span class="topic-qed">$\square$</span>
</div>

此外，在科克蘭定理的應用中，我們可以一併得到下面這個結果:

$$
\frac{\,\overline{X}-\mu\,}{\frac{\sigma}{\,\sqrt{n}\,}}\indep\frac{\,(n-1)S^{2}\,}{\sigma^{2}}
$$

在建構 $t$ 分配時，這是必不可缺的條件之一。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

在使用科克蘭定理證明上列條件的過程中，我們曾經使用過一個特別的結果，這其實也是一個常態母體下的抽樣分配，此即:

**樣本變異數 $S^{\prime2}$ 的抽樣分配 ($\mu$ 已知)**:

若 <span class="text-nowrap">$X_1,X_2,\ldots,X_n\overset{\mathrm{iid}}{\sim}\mathcal{N}(\mu,\sigma^{2})$，</span>其中 $\sigma^{2}$ 為待估參數，且 $\mu$ 已知，則我們有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\frac{\,nS^{\prime2}\,}{\sigma^{2}}=\frac{\,\sum_{i=1}^{n}(X_i-\mu)^{2}\,}{\sigma^{2}}=\sum_{i=1}^{n}\biggl(\frac{\,X_i-\mu\,}{\sigma}\biggr)^{2}\sim\chi^{2}(n)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\frac{\,nS^{\prime2}\,}{\sigma^{2}}&=\frac{\,\sum_{i=1}^{n}(X_i-\mu)^{2}\,}{\sigma^{2}}\\[0.45em]
&=\sum_{i=1}^{n}\biggl(\frac{\,X_i-\mu\,}{\sigma}\biggr)^{2}\sim\chi^{2}(n)
\end{aligned}
$$

</div>

其中

$$
S^{\prime2}=\frac{1}{\,n\,}\sum_{i=1}^{n}(X_i-\mu)^{2}
$$

<div class="topic-proof" markdown="1">
**Proof.**

這個結果純粹地由常態分配的標準化，搭配卡方分配的特性即可得到。 <span class="topic-qed">$\square$</span>
</div>

這個結果的特別之處在於，實務上不可能用得到這個結果，因為我們不會遇到「已知母體期望值 $\mu$ 卻需要估計母體變異數 $\sigma^{2}$」的情況，[^mu-known] 因此這是個僅存於理論中，可作為推導的橋樑，卻不怎麼實用的結果。

</div>

誠如上述的討論，$t$ 分配是在探討樣本平均數 $\overline{X}$ 的抽樣分配時，經常被使用的一個分配，也因為其性質特殊，我們對於這類的**常用抽樣分配**，比較在意的是其建構方式與其應用，並不是特別在意其作為一個「機率分配」本身的特性。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這些常用的抽樣分配除了前述的標準常態分配、卡方分配與司徒頓 $t$ 分配外，還包含馬上將要提到的**[斯內德克 $\mathcal{F}$ 分配](/teaching-topics/snedecor-f-distribution/#def-f-distribution) <span lang="en">(Snedecor’s $\mathcal{F}$ distribution)</span>**，我們通常將其並稱為統計四大常用抽樣分配。

</div>

[^slutsky]: 這個性質的證明需要使用下一章會提到的**史拉斯基定理 <span lang="en">(Slutsky’s theorem)</span>** 與**連續映射定理 <span lang="en">(continuous mapping theorem)</span>**，並搭配 $X/\nu\xrightarrow[\,\nu\to\infty\,]{\mathrm{p}}1$ 的結果，我們會在稍後將提到的**弱大數法則 (Weak Law of Large Number, WLLN)** 中提到。

[^cauchy]: 其發散的原因正是 $t$ 分配在特定自由度下，高階動差發散的原因。直觀意義上來說，是因為尾部機率過為肥厚，導致 $\mathbb{E}(\lvert X\rvert)$ 發散，就定義上而言即表示期望值不存在，並導致更高階的動差也不存在。

[^mu-known]: 現實世界中，如果我們能知道母體期望值 <span class="text-nowrap">$\mu$，</span>多半表示我們知道母體資料 <span class="text-nowrap">$X_1,X_2,\ldots,X_N$，</span>那麼為何不將母體變異數 $\sigma^{2}$ 一併算出來呢?

## 本篇小結

[Definition 4.23](#def-t-distribution) 的司徒頓 $t$ 分配以一個自由度 $\nu$ 界定，值域為整條實數線，機率函數有兩種等價的寫法，其中以[貝塔函數](/teaching-topics/beta-function-and-distribution/#def-beta-function)表達的那一種把常數項寫成 <span class="text-nowrap">$\frac{1}{\mathcal{B}(\frac{\nu}{2},\frac{1}{2})\sqrt{\nu}}$。</span>這個分配的期望值在 $\nu>1$ 時為 <span class="text-nowrap">$0$、</span>變異數在 $\nu>2$ 時為 <span class="text-nowrap">$\frac{\nu}{\nu-2}$，</span>而定義之中沒有列出動差母函數這一項。

五點說明之中，第一點給出建構式 <span class="text-nowrap">$T=\frac{Z}{\sqrt{X/\nu}}$，</span>其中 $Z$ 為標準常態變數、$X$ 為與之獨立的卡方變數，$t$ 分配的自由度就是 $X$ 的自由度。第二點的證明正是靠這個建構式與獨立性完成: 每一階原動差都拆成 $Z$ 的動差與 $X$ 的負次方動差兩者相乘，奇數階因 $\mathbb{E}(Z)=\mathbb{E}\bigl(Z^{3}\bigr)=0$ 而為 <span class="text-nowrap">$0$，</span>二階與四階則由 $\mathbb{E}\bigl(X^{-1}\bigr)=\frac{1}{\nu-2}$ 與 $\mathbb{E}\bigl(X^{-2}\bigr)=\frac{1}{(\nu-2)(\nu-4)}$ 得到 $\mathrm{Var}(T)=\frac{\nu}{\nu-2}$ 與 <span class="text-nowrap">$\alpha_{4}=\frac{3(\nu-2)}{\nu-4}$。</span>各階動差存在與否也由此得知: $\mathbb{E}\bigl(X^{-\frac{k}{2}}\bigr)$ 要在 $\nu>k$ 時才存在，因此自由度不夠大時，該階以上的動差全部發散。

第三點到第五點把 $t$ 分配放回標準常態分配旁邊比較。$\nu$ 上升時變異數向下趨近 $1$ 而峰態係數向下趨近 <span class="text-nowrap">$3$，</span>極限即為標準常態分配；$\nu=1$ 時則為標準柯西分配，期望值與變異數皆發散。[Example 4.54](#ex-student-t-1) 逐項檢驗這幾件事，答案是期望值那一項: $t$ 分配的期望值只要存在就必定為 <span class="text-nowrap">$0$。</span>其後那則註記由圖形說明另一項: 相同的右尾機率之下，自由度較大者的右尾點較小，也就是 <span class="text-nowrap">$t_{\alpha}(\nu_1)>t_{\alpha}(\nu_2)$</span> 對一切 $0<\nu_1<\nu_2$ 成立，並因此有 <span class="text-nowrap">$z_{\sssig \alpha}<t_{\alpha}(\nu)$。</span>

最後一節轉入常態母體下的抽樣分配。[Theorem 4.24](#thm-xbar-samp-dist) 把 $\sigma$ 換成樣本標準差 $S$ 之後，$\frac{\overline{X}-\mu}{S/\sqrt{n}}$ 服從 $t(n-1)$ 分配，證明的作法是指出它正好符合建構式: 分子是標準化過的樣本平均數，分母是 $\frac{(n-1)S^{2}}{\sigma^{2}}$ 除以自由度之後開根號，而兩者的獨立性由科克蘭定理保證。同一節另外整理了三個結果: $\sigma^{2}$ 已知時 $\frac{\overline{X}-\mu}{\sigma/\sqrt{n}}$ 為標準常態分配、$\mu$ 未知時 $\frac{(n-1)S^{2}}{\sigma^{2}}$ 服從 $\chi^{2}(n-1)$ 分配，以及 $\mu$ 已知時 $\frac{nS^{\prime2}}{\sigma^{2}}$ 服從 $\chi^{2}(n)$ 分配，最後這一個只作為推導的橋樑，實務上用不到。

<!-- ref-point: 下一篇是第四章第 22 篇 (斯內德克 $\mathcal{F}$ 分配與變異數比值的抽樣分配，
     書稿 mathstatch4.tex 第 4344 至 4565 行，其中的 Definition 4.24 anchor 為
     #def-f-distribution)。該篇寫成之後，在此補一段銜接語，連結掛在「下一篇」三個字上。 -->

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
