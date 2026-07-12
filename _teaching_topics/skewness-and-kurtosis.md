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
excerpt: "偏態描述分配尾巴偏向哪一側，峰態則透過四階標準化動差 (standardized moment) 刻畫尾端厚薄與集中情況。兩者把分配形狀轉成可計算的量數。"
---

[上一篇文章](/teaching-topics/mode-and-distribution-shape/)討論眾數與分配形狀。結合更早介紹的期望值與中位數，便可觀察有偏分配中三個中央趨勢量數如何分開。

本篇把這些圖形觀察轉成量數。**偏態 (skewness)** 描述分配偏斜與尾巴方向；**峰態 (kurtosis)** 則透過四階**標準化動差 (standardized moment)** 描述尾端厚薄與集中情況。這兩個量數都屬於分配形狀量數 (measures of shape)。

## 由動差看形狀

令 $\mu_X=\mathbb{E}(X)$。由不同階數的**動差 (moment)**，可以依序描述隨機變數的位置、分散程度與形狀。若 $\mathbb{E}(\lvert X-c\rvert^r)<\infty$，則

$$
\mathbb{E}\big[(X-c)^r\big]
$$

稱為 $X$ 相對於 $c$ 的 $r$ 階動差。常用的選擇有兩種。取 $c=0$ 時，$\mathbb{E}(X^r)$ 稱為 $r$ 階**原動差 (raw moment)**；取 $c=\mu_X$ 時，便得到關於期望值的 $r$ 階**主動差 (principal moment)**，也稱為 $r$ 階**中央動差 (central moment)**。

$$
\mu_r=\mathbb{E}\big[(X-\mu_X)^r\big]
$$

前面已經看過，二階主動差就是變異數

$$
\mu_2=\mathbb{E}\big[(X-\mu_X)^2\big]=\sigma_X^2
$$

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

令 $X$ 為隨機變數，且 $0<\sigma_X<\infty$。若 $m_o$ 為 $X$ 的眾數，$\eta_X$ 為 $X$ 的中位數，則

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
\alpha_4>3, & \text{高狹峰分配，亦稱厚尾分配}\\[0.35em]
\alpha_4=3, & \text{常態峰分配}\\[0.35em]
\alpha_4<3, & \text{低矮峰分配，亦稱薄尾分配}
\end{array}
\right.
$$

<figure class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/kurtosis-tail-comparison.svg?v=20260620-kurtosis-tail-lift" alt="厚尾、常態峰與薄尾分配的峰態比較。">
  <figcaption><span class="topic-figure__label">Fig. 2.20.</span> 峰態係數以常態峰 $\alpha_4=3$ 作為比較基準。厚尾分配在遠離期望值的位置仍保有較多機率密度；薄尾分配則較少。</figcaption>
</figure>

<div class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 2.15</div>

峰態的中文名稱容易讓人只盯著圖形中央的高峰。但由 $\alpha_4$ 的公式可見，真正被放大的，是離差除以標準差後的量

$$
\frac{X-\mu_X}{\sigma_X}
$$

的四次方。離期望值越遠，四次方後的貢獻越大。因此，峰態係數很大時，通常表示尾端較厚，遠離期望值的取值對四階平均有較大影響；峰態係數較小時，則表示尾端相對較薄。
</div>

這也是為何高狹峰與低矮峰這兩個名稱不能只按字面理解。高狹峰分配未必只是中央高峰比較尖，低矮峰分配也未必只是中央高峰比較扁。較穩妥的讀法，是把峰態和尾端厚薄一起看。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

厚尾觀念在金融領域很常出現。若用常態分配描述資產報酬 (asset returns)，極端漲跌的機率常會被估得太低；因此，金融計量與風險管理會討論具有較厚尾端的分配，用來刻畫少數但幅度很大的價格變動。金融應用中會把峰態視為尾端風險的一個訊號，並回到尾部機率與極端損失本身作判讀。

再往後，讀者會遇到比「有限四階動差」更寬的分配族。例如 $\alpha$-stable 分配 ($\alpha$-stable distributions) 可用來描述厚尾與大幅跳動；當 $0<\alpha<2$ 時，變異數並不存在，四階動差也不存在，因此峰態係數 $\alpha_4$ 不能用來描述它們。這類分配仍延續同一個問題，也就是尾端到底有多厚，極端值會以什麼方式影響加總與長期變動。
</div>

## 偏態與峰態的分工

偏態與峰態都由標準化動差給出，但兩者處理的方向不同。偏態使用三次方，保留離差的正負號，因此能區分右偏與左偏。峰態使用四次方，不保留正負號，而是放大遠離期望值的取值，用來比較尾端厚薄。

| 量數 | 公式 | 主要描述 |
| --- | --- | --- |
| 偏態係數 | $\alpha_3=\mu_3/\sigma_X^3$ | 尾巴方向與非對稱性 |
| 峰態係數 | $\alpha_4=\mu_4/\sigma_X^4$ | 尾端厚薄與集中情況 |

在實際判讀時，偏態與峰態不應取代圖形。它們把形狀壓縮成數值，方便比較與推導；圖形則保留分配的整體樣貌。兩者合併使用，才較能避免把一個分配的形狀看得過於單薄。

## 本篇小結

各階動差把分配的位置、分散程度與形狀連在一起。二階主動差是變異數，三階標準化動差給出偏態係數 $\alpha_3$，四階標準化動差給出峰態係數 $\alpha_4$。

偏態描述尾巴偏向哪一側。右偏或正偏通常對應 $\alpha_3>0$，左偏或負偏通常對應 $\alpha_3<0$。皮爾森偏態係數則利用期望值、中位數與眾數的相對位置描述偏斜程度。

峰態以常態峰 $\alpha_4=3$ 作為比較基準。$\alpha_4>3$ 通常表示厚尾，$\alpha_4<3$ 通常表示薄尾。峰態不宜只從中央高峰的尖或扁來理解，更應回到標準化後的離差取四次方時，如何放大遠離期望值的取值。

後面若要更系統地處理各階動差，便需要一個能產生動差的工具。這會自然導向[動差母函數](/teaching-topics/moment-generating-functions/)。

## 參考文獻與延伸閱讀

- 黃文璋，2003，《機率論》，初版，華泰文化。
- 黃文璋，2003，《數理統計》，初版，華泰文化。
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Sheldon M. Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
