---
title: "鐘形分配與經驗法則"
subtitle: "Bell-Shaped Distributions and the Empirical Rule"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 19
order: 219
permalink: /teaching-topics/empirical-rule-bell-shaped-distributions/
date: 2026-07-13
published: true
excerpt: '經驗法則以常態分配為基準，給出期望值左右一個、兩個與三個標準差內的近似機率。這組 68-95-99.7 規則只適用於常態分配或可合理近似常態的分配。'
---

[上一篇文章](/teaching-topics/convexity-jensen-inequality/)討論凸函數與[延森不等式](/teaching-topics/convexity-jensen-inequality/#theorem-28)。更早介紹的[柴比雪夫不等式](/teaching-topics/chebyshev-cantelli-inequalities/#theorem-25)則說明，若只知道期望值與變異數，仍可對隨機變數偏離期望值的機率給出普遍界限。

若進一步知道分配可合理地以**常態分配 (normal distribution)** 近似，便能作出更具體的機率判斷。期望值左右一個、兩個與三個標準差內的機率，大約是 $68\%$、$95\%$ 與 $99.7\%$。這組近似稱為[**經驗法則 (empirical rule)**](#empirical-rule-68-95-997)，亦稱 **68-95-99.7 規則 (68-95-99.7 rule)**。

## 鐘形是一種外觀描述

常態分配的機率密度函數具有對稱、單峰且中央較高的鐘形外觀。不少連續分配也可能呈現近似的土丘形狀，因此常被概括稱為**鐘形分配 (bell-shaped distribution)**。

<div id="note-bell-shaped-scope" class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

鐘形分配不是一個由單一公式界定的正式分配族。對稱與單峰也不足以決定期望值附近的機率，因為不同分配的尾端厚薄可能不同。

因此，[經驗法則](#empirical-rule-68-95-997)應用於常態分配，或有充分理由可用常態分配近似的情形。只知道圖形大致對稱、中央有一個高峰，仍不足以保證期望值左右一個、兩個與三個標準差內的機率約為 $68\%$、$95\%$ 與 $99.7\%$。
</div>

[這項限制](#note-bell-shaped-scope)也說明了[經驗法則](#empirical-rule-68-95-997)與[柴比雪夫不等式](/teaching-topics/chebyshev-cantelli-inequalities/#theorem-25)的差別。[柴比雪夫不等式](/teaching-topics/chebyshev-cantelli-inequalities/#theorem-25)只要求期望值與有限變異數存在，所以適用範圍很廣；[經驗法則](#empirical-rule-68-95-997)加入近似常態的分配形狀條件，因而能給出更接近實際機率的數值。

## 常態分配給出的基準

常態分配將在後面的主題中另行介紹。此處先使用它的記號、標準化結果與對稱性，說明經驗法則所採用的三個機率基準。

<!-- ref-point: 待常態分配主題發布後，將「後面的主題」改為指向該篇文章的站內連結。 -->

令 $X\sim\mathcal{N}(\mu,\sigma^2)$，其中 $\sigma>0$。將 $X$ 標準化可得 $Z=(X-\mu)/\sigma\sim\mathcal{N}(0,1)$。

以 $\Phi$ 表示**標準常態分配 (standard normal distribution)** 的**累積分配函數 (cumulative distribution function, CDF)**，亦即 $\Phi(z)=\mathbb{P}(Z\leqslant z)$。

對任意 $k>0$，由常態分配的對稱性可得

$$
\begin{aligned}
\mathbb{P}(\lvert X-\mu\rvert\leqslant k\sigma)
&=
\mathbb{P}(\lvert Z\rvert\leqslant k) \\[0.35em]
&=
\Phi(k)-\Phi(-k) \\[0.35em]
&=
2\Phi(k)-1
\end{aligned}
$$

取 $k=1,2,3$，便得到

$$
\begin{aligned}
\mathbb{P}(\lvert X-\mu\rvert\leqslant \sigma)
&\doteqdot 0.6827 \\[0.35em]
\mathbb{P}(\lvert X-\mu\rvert\leqslant 2\sigma)
&\doteqdot 0.9545 \\[0.35em]
\mathbb{P}(\lvert X-\mu\rvert\leqslant 3\sigma)
&\doteqdot 0.9973
\end{aligned}
$$

常態分配為連續型分配，單點機率為 $0$。因此，上列事件使用 $<$ 或 $\leqslant$ 會得到相同機率。

<div id="empirical-rule-68-95-997" class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note (Empirical Rule: 68-95-99.7 Rule)</div>

若隨機變數 $X$ 服從常態分配，或其分配可合理地以常態分配近似，且期望值 $\mu_X$ 有限、變異數滿足 $0<\sigma_X^2<\infty$，則可作下列判斷。

| 區間 | 約略機率 |
| :---: | :---: |
| $\mu_X-\sigma_X<X<\mu_X+\sigma_X$ | $68\%$ |
| $\mu_X-2\sigma_X<X<\mu_X+2\sigma_X$ | $95\%$ |
| $\mu_X-3\sigma_X<X<\mu_X+3\sigma_X$ | $99.7\%$ |

若 $X$ 確實服從常態分配，較精確的近似值依序為 $0.6827$、$0.9545$ 與 $0.9973$。
</div>

<!-- ref-point: 待中央極限定理的應用主題完成後，再於該處介紹離散型分配的常態近似與連續性校正。 -->

將這三個中央區間畫在常態曲線下，便可由陰影面積看出它們所涵蓋的機率，如 [Fig. 2.22](#fig-222) 所示。

<figure id="fig-222" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/empirical-rule-normal-coverage.svg" alt="常態密度曲線以期望值為中心，期望值左右一個、兩個與三個標準差的中央區間，依序涵蓋約 68.27%、95.45% 與 99.73% 的機率面積。">
  <figcaption><span class="topic-figure__label">Fig. 2.22.</span> 常態分配中，以期望值 $\mu$ 為中心，左右一個、兩個與三個標準差內的中央區間，分別涵蓋約 $68.27\%$、$95.45\%$ 與 $99.73\%$ 的機率。</figcaption>
</figure>

[經驗法則](#empirical-rule-68-95-997)中的區間都以期望值為中心。第一個區間向左右各延伸一個標準差，總寬度為兩個標準差；第二個區間總寬度為四個標準差；第三個區間總寬度為六個標準差。

這也使 [z-score](/teaching-topics/linear-transformations-standardization/#標準化) 有了直接的機率解釋。在近似常態的分配中，$\lvert z\rvert<1$、$\lvert z\rvert<2$ 與 $\lvert z\rvert<3$ 分別對應上述三個中央區間。

<div id="interlude-221" class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 2.21</div>

[經驗法則](#empirical-rule-68-95-997)處理的是中央區間的機率，不是單一位置的機率。以兩個標準差為例，約 $95\%$ 的機率落在中央區間內，所以區間外兩端合計約有 $5\%$。若分配關於期望值對稱，左右兩端各約有 $2.5\%$。

三個標準差內約有 $99.7\%$，所以區間外兩端合計約有 $0.3\%$。這個數值很小，但並不等於 $0$。落在三個標準差以外的結果仍有可能發生。
</div>

## 與柴比雪夫不等式比較

[柴比雪夫不等式](/teaching-topics/chebyshev-cantelli-inequalities/#theorem-25)對任何具有有限二階動差且變異數為正的隨機變數皆成立。對 $k>0$，它給出

$$
\mathbb{P}(\lvert X-\mu_X\rvert<k\sigma_X)
\geqslant
1-\frac{1}{k^2}
$$

這是一個機率下界。[經驗法則](#empirical-rule-68-95-997)所給的數值則是常態基準下的近似機率，兩者的角色並不相同。

<div id="example-228" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.28 (Normal Coverage and Chebyshev Bounds)</div>

令 $X\sim\mathcal{N}(\mu,\sigma^2)$。比較常態分配的中央區間機率與[柴比雪夫不等式](/teaching-topics/chebyshev-cantelli-inequalities/#theorem-25)所給的下界。

| $k$ | 常態分配機率的近似值 | [柴比雪夫下界](/teaching-topics/chebyshev-cantelli-inequalities/#theorem-25) |
| :---: | :---: | :---: |
| $1$ | $0.6827$ | $0$ |
| $2$ | $0.9545$ | $0.75$ |
| $3$ | $0.9973$ | $8/9\doteqdot 0.8889$ |

以 $k=2$ 為例，[柴比雪夫不等式](/teaching-topics/chebyshev-cantelli-inequalities/#theorem-25)保證

$$
\mathbb{P}(\lvert X-\mu\rvert<2\sigma)
\geqslant
1-\frac{1}{2^2}
=
0.75
$$

常態分配的實際機率則為 $\mathbb{P}(\lvert X-\mu\rvert<2\sigma)\doteqdot0.9545$。

[柴比雪夫下界](/teaching-topics/chebyshev-cantelli-inequalities/#theorem-25)適用於所有具有有限二階動差且變異數為正的分配，因此較為保守。已知 $X$ 服從常態分配後，便可使用常態 CDF 得到較精確的機率。
</div>

## 何時不應使用經驗法則

分配明顯有偏、具有多個高峰、尾端特別厚，或受到明顯截斷時，中央區間機率可能與常態基準相差很多。此時應使用已知的機率質量函數 (probability mass function, pmf)、機率密度函數 (probability density function, pdf) 或 CDF 直接計算；若只知道期望值與變異數，則使用[柴比雪夫不等式](/teaching-topics/chebyshev-cantelli-inequalities/#theorem-25)所給的普遍界限。

樣本直方圖看起來近似鐘形，只能作為初步判斷。樣本大小、組距選擇與尾端觀察都會影響圖形。若要把[經驗法則](#empirical-rule-68-95-997)用於實際資料，仍應先說明常態近似的根據。

## 本篇小結

[經驗法則](#empirical-rule-68-95-997)以常態分配為基準。若 $X$ 服從常態分配，則期望值左右一個、兩個與三個標準差內的機率分別約為 $0.6827$、$0.9545$ 與 $0.9973$。在可合理近似常態的情形中，常簡記為 68-95-99.7 規則。

鐘形分配只是一種外觀描述。對稱、單峰或中央較高都不足以單獨保證[經驗法則](#empirical-rule-68-95-997)成立。若沒有近似常態的根據，應由 pmf、pdf 或 CDF 計算，或使用只依賴期望值與變異數的機率不等式。

前面曾討論分配資訊有限的情形。即使不知道分配的詳細資訊，只知道一、二階動差，或能計算某些有限的指數動差，仍可在相應條件下對事件機率給出上界或下界；若再知道所用函數的凸性或凹性，且相應的期望值存在，也可對函數轉換後的期望值給出上界或下界。

另一種情境則是，我們已經知道 $X$ 的完整分配，並以 $Y=g(X)$ 定義新的隨機變數。此時便可再問，$Y$ 具有什麼樣的分配？

先前的[線性轉換與標準化](/teaching-topics/linear-transformations-standardization/)一文已經處理 $Y=aX+b$。其中，[標準化](/teaching-topics/linear-transformations-standardization/#標準化)以 $Z=(X-\mu_X)/\sigma_X$ 表示 $X$ 與期望值相差幾個標準差，本篇的經驗法則正是藉此把期望值左右若干個標準差內的事件改寫成 $Z$ 的中央區間。當 $X$ 服從常態分配時，$Z$ 服從標準常態分配；當 $X$ 的分配可合理地以常態分配近似時，$Z$ 也只是近似服從標準常態分配。線性轉換只是函數轉換的一種特殊情形；若改為更一般的 $Y=g(X)$，又應如何處理？

在分配資訊有限時，[延森不等式](/teaching-topics/convexity-jensen-inequality/#theorem-28)已說明，若 $g$ 為凸函數或凹函數，且相應的期望值存在，便可比較 $\mathbb{E}[g(X)]$ 與 $g\bigl(\mathbb{E}(X)\bigr)$，從而得到 $\mathbb{E}[g(X)]$ 的下界或上界。若已知 $X$ 的完整分配，且 $\mathbb{E}[g(X)]$ 存在，[函數的期望值](/teaching-topics/expected-value-random-variables/#函數的期望值)也可用來計算這個數值。但無論是這種界限，或是一個已經算出的期望值，都還沒有告訴我們 $Y$ 的完整分配。若還想求得這個分配，便須進一步追蹤 $g$ 如何改變可能取值與事件。

第二章最後兩篇將依序討論離散型與連續型隨機變數的函數轉換。[下一篇文章](/teaching-topics/discrete-random-variable-transformations/)先處理離散型隨機變數。已知 $X$ 的 pmf 與 $Y=g(X)$ 後，我們會先找出所有經 $g$ 映到同一個 $Y$ 值的 $X$ 取值，再將這些取值的機率相加，得到 $Y$ 的 pmf，並由此確定其完整分配。

## 參考文獻與延伸閱讀

- 黃文璋，2003，《機率論》，初版，華泰文化。
- 黃文璋，2003，《數理統計》，初版，華泰文化。
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Sheldon M. Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
