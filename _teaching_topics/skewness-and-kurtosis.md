---
title: "偏態與峰態"
subtitle: "Skewness and Kurtosis"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 11
order: 211
permalink: /teaching-topics/skewness-and-kurtosis/
date: 2026-06-20
published: true
excerpt: "偏態描述分配尾巴偏向哪一側，峰態則整理標準化四次方離差的平均，並以常態分配為比較基準。兩者把分配形狀轉成可計算的量數。"
---

[上一篇文章](/teaching-topics/mode-and-distribution-shape/)討論眾數與分配形狀。結合更早介紹的期望值與中位數，便可觀察有偏分配中三個中央趨勢量數如何分開。

本篇把這些圖形觀察轉成量數。**偏態 (skewness)** 描述分配偏斜與尾巴方向；**峰態 (kurtosis)** 則透過四階**標準化動差 (standardized moment)**，整理遠離期望值的取值對四階平均的影響。這兩個量數都屬於分配形狀量數 (measures of shape)。

## 由動差看形狀

由不同階數的**動差 (moment)**，可以依序描述隨機變數的位置、分散程度與形狀。對每個正整數 $r$ 與 $c\in\mathbb{R}$，若 $\mathbb{E}(\lvert X-c\rvert^r)<\infty$，則 $\mathbb{E}\big[(X-c)^r\big]$ 稱為 $X$ 相對於 $c$ 的 $r$ 階動差。

常用的選擇有兩種。取 $c=0$ 時，$\mathbb{E}(X^r)$ 稱為 $r$ 階**原動差 (raw moment)**。若 $\mu_X=\mathbb{E}(X)$ 有限，取 $c=\mu_X$ 時，便得到關於期望值的 $r$ 階**主動差 (principal moment)**，也稱為 $r$ 階**中央動差 (central moment)**，記為 $\mu_r=\mathbb{E}\big[(X-\mu_X)^r\big]$。

前面已經看過，二階主動差就是變異數，即 $\mu_2=\mathbb{E}\big[(X-\mu_X)^2\big]=\sigma_X^2$。

二階主動差描述分散程度。若繼續往高階看，三階主動差會保留離差正負號，可用來描述偏態；四階主動差會強烈放大遠離期望值的取值，可用來描述峰態。

不同隨機變數的尺度可能不同，因此直接比較 $\mu_3$ 或 $\mu_4$ 並不合適。標準化後，三階與四階主動差才成為無單位的形狀量數。

## 偏態係數

偏態主要描述分配的非對稱性。若右側尾巴較長，稱為右偏；若左側尾巴較長，稱為左偏。

<div id="definition-214" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.14</div>

令 $X$ 為隨機變數，且 $0<\sigma_X<\infty$。若 $\mu_3=\mathbb{E}\big[(X-\mu_X)^3\big]$ 存在，則定義

$$
\alpha_3
=
\mathbb{E}\left[
\left(\frac{X-\mu_X}{\sigma_X}\right)^3
\right]
=
\frac{\mathbb{E}\big[(X-\mu_X)^3\big]}{\sigma_X^3}
=
\frac{\mu_3}{\sigma_X^3}
$$

為 $X$ 的**動差偏態係數 (moment coefficient of skewness)**。

</div>

在 $\mu_3$ 中，正離差取三次方後仍為正，負離差取三次方後仍為負。遠離期望值的取值又會因為三次方而被放大。因此，若右側尾巴較長或右側極端值影響較強，$\mu_3$ 往往為正；若左側尾巴較長，$\mu_3$ 往往為負。

常用的分類可寫為

$$
\left\{
\begin{array}{c@{\quad}l}
\alpha_3>0, & \text{右偏分配，亦稱正偏分配}\\[0.35em]
\alpha_3=0, & \text{對稱分配的典型情形}\\[0.35em]
\alpha_3<0, & \text{左偏分配，亦稱負偏分配}
\end{array}
\right.
$$

這個分類要配合分配圖形一起判讀。若分配本身對稱且三階動差存在，則 $\alpha_3=0$；反過來說，單憑 $\alpha_3=0$ 不足以保證所有分配都對稱。

<figure class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/skewness-coefficients.svg" alt="右偏、左偏與對稱分配中的偏態係數、眾數、中位數與期望值位置。">
  <figcaption><span class="topic-figure__label">Fig. 2.19.</span> 右偏與左偏描述尾巴方向。常見單峰右偏分配中，$m_o,\eta_X,\mu_X$ 常依序向右分開；左偏時方向相反。</figcaption>
</figure>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

右偏分配的「右」指的是尾巴往右延伸，不是高峰偏在右側。正偏分配的「正」則指 $\alpha_3$ 的符號為正。左偏與負偏也應作同樣區分。
</div>

## 皮爾森偏態係數

前面已經討論過期望值、中位數與眾數在有偏分配中的相對位置。皮爾森偏態係數便利用這三個中央趨勢量數的差距來描述偏態。

<div id="definition-215" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.15</div>

令 $X$ 為隨機變數，且 $0<\sigma_X<\infty$。若 $m_o$ 為 $X$ 的一個眾數，$\eta_X$ 為 $X$ 的一個中位數，則

$$
SK_{P_1}
=
\frac{\mu_X-m_o}{\sigma_X}
$$

稱為 $X$ 的**皮爾森第一偏態係數 (Pearson's first coefficient of skewness)**，亦稱為眾數偏態係數。

另一個常用的版本可寫為

$$
SK_{P_2}
=
\frac{3(\mu_X-\eta_X)}{\sigma_X}
$$

稱為 $X$ 的**皮爾森第二偏態係數 (Pearson's second coefficient of skewness)**，亦稱為中位數偏態係數。

</div>

若眾數或中位數不唯一，係數會隨所選的代表值而不同。因此，實際使用前須先說明所採用的 $m_o$ 或 $\eta_X$。

皮爾森偏態係數來自單峰分配中的一個經驗關係。對許多單峰分配而言，期望值到眾數的距離，大約是期望值到中位數距離的三倍，即

$$
\big|\mu_X-m_o\big|
\doteqdot
3\big|\mu_X-\eta_X\big|
$$

這不是數學定理，所以兩個皮爾森偏態係數未必完全相等。不過，它們都把有偏分配中三個中央趨勢量數的相對位置轉成無單位的數值。

<div class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 2.14</div>

所得或財富分配常呈現右偏。多數人的取值集中在較低或中間區域，少數極高值把右尾拉長。此時期望值會被右尾明顯拉動，中位數受影響較小，眾數則多半留在主要集中位置附近。

因此，常見單峰右偏分配會呈現

$$
m_o\leqslant \eta_X\leqslant \mu_X
$$

左偏分配則方向相反，常呈現

$$
\mu_X\leqslant \eta_X\leqslant m_o
$$

</div>

## 峰態係數

偏態用三階標準化動差處理左右不對稱。峰態則使用四階標準化動差，討論遠離期望值的取值對整體分配形狀的影響。

<div id="definition-216" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.16</div>

令 $X$ 為隨機變數，且 $0<\sigma_X<\infty$。若 $\mu_4=\mathbb{E}\big[(X-\mu_X)^4\big]$ 存在，則定義

$$
\alpha_4
=
\mathbb{E}\left[
\left(\frac{X-\mu_X}{\sigma_X}\right)^4
\right]
=
\frac{\mathbb{E}\big[(X-\mu_X)^4\big]}{\sigma_X^4}
=
\frac{\mu_4}{\sigma_X^4}
$$

為 $X$ 的**峰態係數 (coefficient of kurtosis)**。

</div>

常態分配的峰態係數為 $3$，因此峰態常以 $3$ 作為比較基準。若改用

$$
\kappa=\alpha_4-3
$$

則稱為**超額峰態係數 (coefficient of excess kurtosis)**。超額峰態係數把常態峰的基準移到 $0$。

依照 $\alpha_4$ 與 $3$ 的大小關係，可作下列分類

$$
\left\{
\begin{array}{c@{\quad}l}
\alpha_4>3, & \text{厚尾分配}\\[0.35em]
\alpha_4=3, & \text{常態峰分配}\\[0.35em]
\alpha_4<3, & \text{薄尾分配}
\end{array}
\right.
$$

這些名稱是依峰態係數相對於常態分配所作的分類，不能單獨視為一般尾端衰減速度的分類。$\alpha_4$ 整理的是標準化四次方離差的平均；即使隨機變數的可能取值落在有限區間內，也可能有 $\alpha_4>3$，而 $\alpha_4=3$ 也不表示該分配必為常態分配。

<figure class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/kurtosis-tail-comparison.svg?v=20260721-kurtosis-equal-scale" alt="期望值皆為零且變異數皆為一的拉普拉斯、常態與均勻分配，依峰態係數與常態峰基準所作的比較。">
  <figcaption><span class="topic-figure__label">Fig. 2.20.</span> 三條曲線分別為期望值 $0$、變異數 $1$ 的拉普拉斯分配 (Laplace distribution)、標準常態分配與均勻分配。它們是 $\alpha_4>3$、$\alpha_4=3$ 與 $\alpha_4<3$ 的具體例子；任意兩個分配的尾端厚薄仍須另行比較。</figcaption>
</figure>

<div class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 2.15</div>

峰態的中文名稱容易讓人只注意圖形中央的高峰。但由 $\alpha_4$ 的公式可見，被放大的是標準化離差 $(X-\mu_X)/\sigma_X$ 的四次方。離期望值越遠，四次方後的貢獻越大。因此，$\alpha_4$ 衡量遠離期望值的取值對四階平均的影響。在中心與尺度固定、形狀可相互比較的分配族中，較大的 $\alpha_4$ 常伴隨相對較厚的尾端；不過，這並不是任意兩個分配之間都成立的尾端排序。
</div>

因此，峰態係數不宜只從中央高峰的尖或扁來理解，也不能單獨等同於一般尾端衰減速度。較穩妥的判讀方式，是合併峰態係數、分配圖形與尾部機率。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

厚尾觀念在金融領域很常出現。若用常態分配描述資產報酬 (asset returns)，極端漲跌的機率常會被估得太低；因此，金融計量與風險管理會討論具有較厚尾端的分配，用來刻畫少數但幅度很大的價格變動。金融應用中會把峰態視為尾端風險的一項指標，並回到尾部機率與極端損失本身作判讀。

再往後，讀者會遇到比「有限四階動差」更寬的分配族。例如 $\alpha$-stable 分配 ($\alpha$-stable distributions) 可用來描述厚尾與大幅跳動；當 $0<\alpha<2$ 時，變異數並不存在，四階動差也不存在，因此峰態係數 $\alpha_4$ 不能用來描述它們。這類分配仍延續同一個問題，也就是尾端到底有多厚，極端值會以什麼方式影響加總與長期變動。
</div>

## 偏態與峰態的分工

偏態與峰態都由標準化動差給出，但兩者處理的方向不同。偏態使用三次方，保留離差的正負號，因此能區分右偏與左偏。峰態使用四次方，不保留正負號，而是放大遠離期望值的取值，衡量這些取值對四階平均的影響。

| 量數 | 公式 | 主要描述 |
| --- | --- | --- |
| 偏態係數 | $\alpha_3=\mu_3/\sigma_X^3$ | 尾巴方向與非對稱性 |
| 峰態係數 | $\alpha_4=\mu_4/\sigma_X^4$ | 遠離期望值的取值對四階平均的影響 |

在實際判讀時，偏態與峰態不應取代圖形。它們把形狀壓縮成數值，方便比較與推導；圖形則保留分配的整體樣貌。兩者合併使用，才較能避免把一個分配的形狀看得過於單薄。

## 本篇小結

各階動差把分配的位置、分散程度與形狀連在一起。二階主動差是變異數，三階標準化動差給出偏態係數 $\alpha_3$，四階標準化動差給出峰態係數 $\alpha_4$。

偏態描述尾巴偏向哪一側。右偏或正偏通常對應 $\alpha_3>0$，左偏或負偏通常對應 $\alpha_3<0$。皮爾森偏態係數則利用期望值、中位數與眾數的相對位置描述偏斜程度。

峰態以常態峰 $\alpha_4=3$ 作為比較基準。在中心與尺度固定、形狀可相互比較的分配族中，$\alpha_4>3$ 通常伴隨相對較厚的尾端，$\alpha_4<3$ 則通常伴隨相對較薄的尾端；這不是任意分配之間的尾端排序。峰態不宜只從中央高峰的尖或扁來理解，更應回到標準化後的離差取四次方時，如何放大遠離期望值的取值。

後面若要更系統地處理各階動差，便需要一個能產生動差的工具。這會自然導向[動差母函數](/teaching-topics/moment-generating-functions/)。

## 參考文獻與延伸閱讀

- 黃文璋，2003，《機率論》，初版，華泰文化。
- 黃文璋，2003，《數理統計》，初版，華泰文化。
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Lawrence T. DeCarlo. 1997. “On the Meaning and Use of Kurtosis.” *Psychological Methods* 2 (3): 292–307.
- Sheldon M. Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
