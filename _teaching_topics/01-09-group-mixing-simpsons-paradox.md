---
title: "分組、混合與辛普森悖論"
subtitle: "Grouping, Mixing, and Simpson’s Paradox"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 1
topic: 9
order: 109
permalink: /lecture-notes/group-mixing-simpsons-paradox/
date: 2026-05-17
published: true
excerpt: "同一個比較在每個分組內都成立，混合後卻可能反轉。辛普森悖論說明，條件機率與全機率定理不只用來計算，也用來檢查比較是否公平。"
---

[上一篇](/lecture-notes/total-probability-bayes-rule/)討論了分割與全機率定理。當樣本空間被切成幾個互斥且沒有遺漏的來源時，整體機率可以看成各來源條件機率的加權平均。

不妨先思考一個常見的情境。假設有兩位外科醫師，其中一位整體的手術成功率較高，直覺上似乎應該優先選擇這位醫師；然而若將病患依病況輕重分組檢視，卻可能發現另一位醫師在每一種病況下的手術成功率其實都更高。

之所以會出現這種現象，是因為整體成功率不只取決於醫師的技術，也取決於病患的風險組成。經驗豐富的醫師可能承接更多高風險、低成功率的重症手術；相對地，另一位醫師即使在各風險分組內的成功率都較低，只要主要處理低風險手術，混合計算後的整體成功率仍可能更高。

這種「在每個分組內的比較方向一致，合併為整體後卻發生反轉」的現象，稱為**辛普森悖論 <span lang="en">(Simpson’s paradox)</span>**。反轉的根源在於不同組別混合時的權重改變，進而改變了整體機率實際比較的基準。

以下固定令 $(S,\mathcal{F},\mathbb{P})$ 為一個機率空間。令 $C_1,\ldots,C_k$ 為樣本空間的一組[分割](/lecture-notes/total-probability-bayes-rule/#definition-partition)，也就是這些事件彼此互斥，且合起來沒有遺漏。

## 混合後的機率是加權平均

令 $A$ 表示某處理方式，令 $Y$ 表示成功事件。假設 $\mathbb{P}(A)>0$，且只針對 $\mathbb{P}(A\cap C_i)>0$ 的分組計算條件成功率。若 $A$ 已經發生，則在分割 $C_1,\ldots,C_k$ 下，由於 [$\mathbb{P}(\,\cdot\,\mid A)$ 仍為機率測度](/lecture-notes/conditional-probability-information/#theorem-conditional-probability-measure)，可套用[全機率定理](/lecture-notes/total-probability-bayes-rule/#theorem-law-of-total-probability)，再由[乘法原理](/lecture-notes/conditional-probability-information/#theorem-18)可得

$$
\begin{aligned}
\mathbb{P}(Y\mid A)
&=\sum_{i=1}^{k}\mathbb{P}(Y\cap C_i\mid A)\\[0.45em]
&=\sum_{i=1}^{k}\mathbb{P}(Y\mid A\cap C_i)\,\mathbb{P}(C_i\mid A)
\end{aligned}
$$

由此可知，整體成功率是以 $\mathbb{P}(C_i\mid A)$ 為權重的加權平均，而非各組成功率的算術平均；至於滿足 $\mathbb{P}(A\cap C_i)=0$ 的分組，其對應權重 $\mathbb{P}(C_i\mid A)=0$ 自然不會影響總和。若兩種處理方式 $A$ 與 $B$ 在各分組間的比例不同，兩者的整體成功率便是以不同權重混合而得的結果。

## 分組內與混合後的比較反轉

假設有兩位醫師，稱為醫師 $A$ 與醫師 $B$。病患可以分為低風險 $C_1$ 與高風險 $C_2$。在每個風險分組內，醫師 $A$ 的手術成功率都比較高。

<div id="example-simpson-reversal" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.27 <span lang="en">(A Simpson Reversal)</span></div>

兩位醫師共治療 $150$ 位病患。以自這 $150$ 位病患中均等可能地隨機抽取一位為隨機實驗，令 $A$、$B$ 分別表示該病患由<span class="text-nowrap">醫師 $A$、醫師 $B$</span> 開刀之事件，$Y$ 表示手術成功之事件，$C_1$、$C_2$ 分別表示低風險與高風險之事件。試比較兩位醫師在分組內與整體的手術成功率。

低風險病患中，醫師 $A$ 有 $9$ 人成功、$1$ 人失敗，醫師 $B$ 有 $72$ 人成功、$18$ 人失敗。因此條件成功率分別為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(Y\mid A\cap C_1)=\frac{9}{10}=0.90
\qquad
\mathbb{P}(Y\mid B\cap C_1)=\frac{72}{90}=0.80
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{P}(Y\mid A\cap C_1)=\frac{9}{10}=0.90\\[0.6em]
\mathbb{P}(Y\mid B\cap C_1)=\frac{72}{90}=0.80
\end{gathered}
$$

</div>

高風險病患中，醫師 $A$ 有 $24$ 人成功、$16$ 人失敗，醫師 $B$ 有 $5$ 人成功、$5$ 人失敗。因此條件成功率分別為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(Y\mid A\cap C_2)=\frac{24}{40}=0.60
\qquad
\mathbb{P}(Y\mid B\cap C_2)=\frac{5}{10}=0.50
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{P}(Y\mid A\cap C_2)=\frac{24}{40}=0.60\\[0.6em]
\mathbb{P}(Y\mid B\cap C_2)=\frac{5}{10}=0.50
\end{gathered}
$$

</div>

在低風險與高風險兩組內，醫師 $A$ 的成功率皆較高。不過若合併為整體來看，醫師 $A$ 的成功率為

$$
\mathbb{P}(Y\mid A)=\frac{9+24}{10+40}=\frac{33}{50}=0.66
$$

醫師 $B$ 的成功率為

$$
\mathbb{P}(Y\mid B)=\frac{72+5}{90+10}=\frac{77}{100}=0.77
$$

若把高風險 $C_2$ 視為困難手術、低風險 $C_1$ 視為容易手術，兩位醫師的成績如下表，每格記為成功人數與病患人數之比，括號內為成功率。

| | 困難手術 $C_2$ | 容易手術 $C_1$ | 整體 |
| :---: | :---: | :---: | :---: |
| 醫師 $A$ | $24/40$ <span class="topic-cell-rate">($0.60$)</span> | $9/10$ <span class="topic-cell-rate">($0.90$)</span> | $33/50$ <span class="topic-cell-rate">($0.66$)</span> |
| 醫師 $B$ | $5/10$ <span class="topic-cell-rate">($0.50$)</span> | $72/90$ <span class="topic-cell-rate">($0.80$)</span> | $77/100$ <span class="topic-cell-rate">($0.77$)</span> |
{: .topic-table--joint-pmf .topic-table--margin-column-only}

於是在兩個分組內醫師 $A$ 的成功率皆高於醫師 <span class="text-nowrap">$B$，</span>混合為整體後卻由醫師 $B$ 領先。
</div>

這個反轉來自兩位醫師接案的風險比例不同。醫師 $A$ 的病患中有 $\frac{40}{50}$ 屬於高風險群，而醫師 $B$ 的病患中只有 $\frac{10}{100}$ 屬於高風險群，因此兩個整體成功率並非在同一組權重下比較。

若想親手調整混合比例，可參考互動展示 [Simpson’s Paradox Mixing Lab](/demos/simpsons-paradox/)，在固定各分組成功率下只改變高風險案例比例，觀察整體比較如何反轉。

<div id="interlude-which-comparison" class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 1.3</div>

若只看整體成功率，醫師 $B$ 的成功率較高；若分別檢視低風險與高風險兩組病患，則是醫師 $A$ 的成功率較高。

這兩種結論看似矛盾，關鍵在於比較目的不同。若要評估兩位醫師在相同病況下的醫療表現，便應控制病患的風險分組，比較各組內的條件成功率；若要描述現行轉介制度下兩位醫師實際呈現的整體結果，混合後的整體成功率也自有其意義。
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

辛普森悖論的命名有一段歷史淵源。類似現象早在 Udny Yule 於 $1903$ 年的研究中便已出現，故也常稱為 <span lang="en">Yule-Simpson effect</span>；直到 Edward H. Simpson 在 $1951$ 年以列聯表清楚剖析這類反轉後，辛普森悖論一名才逐漸流傳開來。

最著名的真實案例之一，是 $1973$ 年加州大學柏克萊分校 <span lang="en">(UC Berkeley)</span> 的研究所入學資料。整體錄取率看似呈現明顯的性別落差，但依各系所分別檢視後，便會發現差異主要源於不同系所的錄取難度與申請人數比例不同。這個案例顯示，同一份資料在分組前後可能導出相反的結論，分析時必須先確認比較的基準。

Colin R. Blyth 則在 $1972$ 年將此現象與決策理論中的確定事件原則 <span lang="en">(sure-thing principle)</span> 連結，指出各組內一致的比較方向，未必能推廣至混合後的整體。
</div>

## 本篇小結

本篇由條件機率的加權平均出發，依序整理下列結果:

| 結果 | 內容 |
| :---: | :---: |
| [加權平均式](#混合後的機率是加權平均) | 整體成功率為各組條件成功率的加權平均 |
| [Example 1.27](#example-simpson-reversal) | 分組內一致的比較方向在混合後反轉 |
| [直覺校準 1.3](#interlude-which-comparison) | 比較的目的決定應看分組內或混合後的成功率 |

辛普森悖論說明，當我們比較兩個機率時，必須先確認兩者是否在同一組條件下計算。

在本篇的醫師案例中，分組內的成功率與混合後的整體成功率之所以方向相反，原因在於兩位醫師面對的低風險與高風險病患比例不同。換言之，將各組資料合併時，不僅隱去了分組資訊，也同時改變了加權平均所使用的權重。

[下一篇](/lecture-notes/bayes-rule-posterior-probability/)會把全機率定理反過來讀。若我們已經觀察到某個結果，該如何回頭判斷它最可能來自哪個來源？這會自然導向貝氏定理。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- G. Udny Yule. 1903. “Notes on the Theory of Association of Attributes in Statistics.” *Biometrika* 2 (2): 121–134.
- Edward H. Simpson. 1951. “The Interpretation of Interaction in Contingency Tables.” *Journal of the Royal Statistical Society, Series B* 13 (2): 238–241.
- Colin R. Blyth. 1972. “On Simpson’s Paradox and the Sure-Thing Principle.” *Journal of the American Statistical Association* 67 (338): 364–366.
- P. J. Bickel, E. A. Hammel, and J. W. O’Connell. 1975. “Sex Bias in Graduate Admissions: Data from Berkeley.” *Science* 187 (4175): 398–404.
- Jan Sprenger and Naftali Weinberger. 2021. “Simpson’s Paradox.” In *The Stanford Encyclopedia of Philosophy*, Summer 2021 ed., edited by Edward N. Zalta.
