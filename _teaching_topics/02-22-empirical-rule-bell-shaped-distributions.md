---
title: "鐘形分配的三個標準差區間"
subtitle: "Three Standard-Deviation Intervals of a Bell-Shaped Distribution"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 22
order: 222
permalink: /teaching-topics/empirical-rule-bell-shaped-distributions/
date: 2026-08-06
published: true
excerpt: "一個分配的形狀若已經大致確定，不必經由機率不等式，也能夠直接說出中央區間的機率，這種由過往經驗得到的判斷稱作經驗法則。鐘形分配經驗法則指出，隨機變數服從常態分配，或其分配可合理地以常態分配近似時，期望值左右一個、兩個與三個標準差之內的機率，依序約為 $0.6827$、$0.9545$ 與 $0.9973$。鐘形與土丘形只是對外觀的概括稱呼，不是某一種確切的分配，因此這三個數值的可靠程度，取決於該分配與常態分配的接近程度。"
---

[上一篇](/teaching-topics/convexity-jensen-inequality/)由[凸函數與凹函數](/teaching-topics/convexity-jensen-inequality/#def-convex-concave)的定義出發，得到延森不等式，把一個[隨機變數](/teaching-topics/random-variables-and-pmf/#def-random-variable)經過函數轉換前後，兩個[期望值](/teaching-topics/expectation/#def-expectation)的大小關係定了下來。機率不等式這一小節到此告一段落。

本篇改由另一個方向作判斷。若已經知道一個分配的形狀大致呈鐘形，我們可以不經由不等式，直接說出期望值左右一個、兩個與三個[標準差](/teaching-topics/variance-standard-deviation/#def-standard-deviation)之內各涵蓋多少機率。以下先說明什麼是經驗法則，接著給出鐘形分配經驗法則的三個機率與兩點使用上的提醒，最後以一張圖把這三個區間的涵蓋比例畫出來。

## 經驗法則

機率不等式在僅有少量的資訊 (例如僅有期望值或[變異數](/teaching-topics/variance/#def-variance)) 下，能夠給出一個大致的機率範圍。稍早介紹的[馬可夫不等式](/teaching-topics/probability-inequalities/#thm-markov)、[柴比雪夫不等式](/teaching-topics/probability-inequalities/#thm-chebyshev)、[車諾夫不等式](/teaching-topics/probability-inequalities/#thm-chernoff)與[延森不等式](/teaching-topics/convexity-jensen-inequality/#thm-jensen)，都是只憑少量的資訊便替某個機率或某個期望值定出界限的結果。然而根據過往的經驗，我們亦能夠給出一些有用的判斷，這種方法稱作**經驗法則 (empirical rule 或 rule of thumb)**。

只知道圖形大致對稱、中央有一個高峰，仍不足以保證期望值左右一個、兩個與三個標準差內的機率約為 $68\%$、$95\%$ 與 $99.7\%$。

<div id="thm-empirical-rule" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.37 (鐘形分配經驗法則, empirical rule of bell-shaped distribution)</div>

若隨機變數 $X$ 服從[常態分配](/teaching-topics/normal-distribution/#def-normal)，或其分配可合理地以常態分配近似，且期望值 $\mu_{\sssig X}$ 有限、變異數滿足 $0<\sigma_{\sssig X}^{2}<\infty$，則

<ol class="topic-list-paren topic-list-paren--math">
  <li>
  $$
  \mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert<\sigma_{\sssig X}\bigr)\fallingdotseq0.6827
  $$
  </li>
  <li>
  $$
  \mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert<2\,\sigma_{\sssig X}\bigr)\fallingdotseq0.9545
  $$
  </li>
  <li>
  $$
  \mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert<3\,\sigma_{\sssig X}\bigr)\fallingdotseq0.9973
  $$
  </li>
</ol>

</div>

鐘形分配經驗法則 <span lang="en">(empirical rule of bell-shaped distribution)</span> 有一些地方需要注意:

(1) 凡是「分配形狀長得像鐘」或是「分配形狀長得像土丘」，我們都稱作**鐘形分配 <span lang="en">(bell-shaped distribution)</span>** 或**土丘形分配 <span lang="en">(mound-shaped distribution)</span>**，但**這不代表它是某種確切的分配，而是一個概括的稱呼**。
{: .topic-paren-item}

(2) 這個經驗法則是從**常態分配 <span lang="en">(normal distribution)</span>** 而來，因此只是一個大約的機率數值，但此數值在該變數是一個常態分配時，便相當準確。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

上列第 (2) 點所說的「從常態分配而來」，具體的算法如下。$X$ 確實服從常態分配時，令 $Z=\frac{\,X-\mu_{\sssig X}\,}{\sigma_{\sssig X}}$，則 $Z$ 服從**[標準常態分配](/teaching-topics/normal-distribution/#def-normal) <span lang="en">(standard normal distribution)</span>**；以 $\Phi$ 表示 $Z$ 的 [cdf](/teaching-topics/cumulative-distribution-functions/#def-cdf)，則對任意 $k>0$ 皆有

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert<k\,\sigma_{\sssig X}\bigr)=\mathbb{P}\bigl(\lvert Z\rvert<k\bigr)=\Phi(k)-\Phi(-k)=2\,\Phi(k)-1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}\bigl(\lvert X-\mu_{\sssig X}\rvert<k\,\sigma_{\sssig X}\bigr)=\mathbb{P}\bigl(\lvert Z\rvert<k\bigr)\\[.45em]
&=\Phi(k)-\Phi(-k)=2\,\Phi(k)-1
\end{aligned}
$$

</div>

$Z$ 為連續型隨機變數，單點機率為 $0$，故第二個等號中的嚴格不等號不影響機率；末一個等號則用到標準常態分配對 $0$ 的對稱性，即 $\Phi(-k)=1-\Phi(k)$。以 $k=1,2,3$ 代入 $2\,\Phi(k)-1$，四捨五入至小數第四位依序為 $0.6827$、$0.9545$ 與 $0.9973$，這正是 [Theorem 2.37](#thm-empirical-rule) 三款的三個數值。$\Phi$ 由標準常態密度的積分定義，沒有以初等函數寫出的表示式，三個數值須以數值方法求得，本篇不另作證明；常態分配與 $\Phi$ 的完整介紹留待[後面的主題](/teaching-topics/normal-distribution/)。

</div>

下面就將這個經驗法則的意涵轉化為圖形。

<figure id="fig-empirical-rule-coverage" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/empirical-rule-normal-coverage.svg" alt="一條鐘形的機率密度曲線畫在一條橫軸之上，橫軸右端標為 x。橫軸上有七個刻度，由左至右依序標為 μ−3σ、μ−2σ、μ−σ、μ、μ+σ、μ+2σ 與 μ+3σ。標為 μ 的刻度上方有一條實線，由曲線的最高點落到橫軸；其餘六個刻度各有一條虛線，由橫軸向上穿過曲線並延伸到曲線上方。曲線之下有三塊左右對稱的陰影，由內而外逐層變淺: 最內一塊的左右界線落在 μ−σ 與 μ+σ，中間一塊落在 μ−2σ 與 μ+2σ，最外一塊落在 μ−3σ 與 μ+3σ。曲線上方另有三組指向左右兩端的箭頭，各標出一組界線所夾的區間，由內而外依序標為 68.27%、95.45% 與 99.73%。">
  <figcaption><span class="topic-figure__label">Fig. 2.23.</span> 常態分配的密度曲線與三個中央區間: 以期望值 $\mu$ 為中心，左右各一個、兩個與三個標準差之內的三塊區域，面積依序約為 <span class="text-nowrap">$0.6827$、</span>$0.9545$ 與 <span class="text-nowrap">$0.9973$，</span>即圖中標示的 <span class="text-nowrap">$68.27\%$、</span>$95.45\%$ 與 <span class="text-nowrap">$99.73\%$。</span></figcaption>
</figure>

## 本篇小結

機率不等式只憑少量的資訊，便替某個機率或某個期望值定出界限。經驗法則的作法不同，先認定分配的形狀，再直接說出中央區間的機率。[Theorem 2.37](#thm-empirical-rule) 就是其中一個，它指出期望值左右一個、兩個與三個標準差之內的機率，依序約為 $0.6827$、$0.9545$ 與 $0.9973$；[Fig. 2.23](#fig-empirical-rule-coverage) 把這三個區間畫在同一條密度曲線之下，三塊陰影的面積正是這三個數值。

使用時有兩點要留意。其一，鐘形與土丘形只是對外觀的概括稱呼，不是某一種確切的分配，因此這三個機率能不能用，取決於該分配與常態分配的接近程度。隨機變數確實服從常態分配時，這三個機率相當準確，只是外觀像鐘則未必。其二，三個數值都是近似值，不宜當成精確的機率。[下一篇](/teaching-topics/one-to-one-transformations/)轉入隨機變數的函數轉換，說明已知 $X$ 的機率分配時，如何求出 $Y=g(X)$ 的機率分配，並以數道例題示範離散型與連續型的作法。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Dennis D. Wackerly, William Mendenhall III, and Richard L. Scheaffer. 2008. *Mathematical Statistics with Applications*. 7th ed. Thomson Brooks/Cole.
- David S. Moore, George P. McCabe, and Bruce A. Craig. 2021. *Introduction to the Practice of Statistics*. 10th ed. Macmillan Learning.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
