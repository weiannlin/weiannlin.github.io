---
title: "分組、混合與辛普森悖論"
subtitle: "Grouping, Mixing, and Simpson's Paradox"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 1
topic: 7
order: 107
permalink: /teaching-topics/group-mixing-simpsons-paradox/
date: 2026-05-17
published: true
excerpt: "同一個比較在每個分組內都成立，混合後卻可能反向。辛普森悖論說明，條件機率與全機率定理不只用來計算，也用來檢查比較是否公平。"
---

[上一篇文章](/teaching-topics/total-probability-bayes-rule/)討論了分割與全機率定理。當樣本空間被切成幾個互斥且沒有遺漏的來源時，整體機率可以看成各來源條件機率的加權平均。

先想一個看似直覺的問題。若一位外科醫師整體的手術成功率比另一位醫師更高，我們就應該選擇這位醫師替自己動手術嗎？這件事真的有那麼自然嗎？事實上，另一位醫師在每種病況中的手術成功率，或許都比這位整體成功率較高的醫師還要高。

原因在於，整體成功率不只受到醫師技術影響，也受到接案組成影響。分組內表現較好的醫師，未必接到比較容易的案子；他也可能因為經驗較足，被分派或轉介更多高風險、低成功率的病患。相反地，整體成功率較高的那位醫師即使在各分組內成功率都較低，若主要處理低風險手術，混合後的整體成功率仍可能看起來比較高。

辛普森悖論則說明另一件事。即使每個分組裡的比較方向都相同，把分組混合起來以後，整體比較仍可能反向。這不是機率論出錯，而是混合權重改變了我們正在比較的對象。

以下固定令 $(S,\mathcal{F},\mathbb{P})$ 為一個機率空間。令 $C_1,\ldots,C_k$ 為樣本空間的一個分割，也就是這些事件彼此互斥，且合起來沒有遺漏。

## 混合後的機率是加權平均

令 $A$ 表示某個處理方式，令 $Y$ 表示成功事件。若 $A$ 已經發生，則在分割 $C_1,\ldots,C_k$ 下，由全機率定理可得

$$
\begin{aligned}
\mathbb{P}(Y\mid A)
&=\sum_{i=1}^{k}\mathbb{P}(Y\cap C_i\mid A)\\[0.45em]
&=\sum_{i=1}^{k}\mathbb{P}(Y\mid A\cap C_i)\,\mathbb{P}(C_i\mid A)
\end{aligned}
$$

由此可知，整體成功率不是單純把各組成功率平均，而是用 $\mathbb{P}(C_i\mid A)$ 當權重做加權平均。若兩個處理方式 $A$ 與 $B$ 對應到的分組比例不同，則它們的整體成功率其實是在用不同權重混合不同族群。

## 一個反向的例子

假設有兩位醫師，稱為醫師 $A$ 與醫師 $B$。病患可以分為低風險 $C_1$ 與高風險 $C_2$。在每個風險分組內，醫師 $A$ 的手術成功率都比較高。

<div class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.12 (A Simpson Reversal)</div>

低風險病患中，醫師 $A$ 有 $9$ 人成功、$1$ 人失敗，醫師 $B$ 有 $72$ 人成功、$18$ 人失敗。因此

$$
\mathbb{P}(Y\mid A\cap C_1)=\frac{9}{10}=0.90
\qquad
\mathbb{P}(Y\mid B\cap C_1)=\frac{72}{90}=0.80
$$

高風險病患中，醫師 $A$ 有 $24$ 人成功、$16$ 人失敗，醫師 $B$ 有 $5$ 人成功、$5$ 人失敗。因此

$$
\mathbb{P}(Y\mid A\cap C_2)=\frac{24}{40}=0.60
\qquad
\mathbb{P}(Y\mid B\cap C_2)=\frac{5}{10}=0.50
$$

在低風險與高風險兩組內，醫師 $A$ 都比較好。不過整體來看，醫師 $A$ 的成功率為

$$
\mathbb{P}(Y\mid A)=\frac{9+24}{10+40}=\frac{33}{50}=0.66
$$

醫師 $B$ 的成功率為

$$
\mathbb{P}(Y\mid B)=\frac{72+5}{90+10}=\frac{77}{100}=0.77
$$

於是，分組內醫師 $A$ 都比較好，混合後卻變成醫師 $B$ 看起來比較好。
</div>

這個反向來自分組比例。醫師 $A$ 的病患中高風險者占了 $40/50$，醫師 $B$ 的病患中高風險者只占 $10/100$。兩個整體成功率不是同一組權重下的比較。

<div class="topic-box topic-box--intuition" markdown="1">
<div class="topic-box__label">直覺校準 1.7</div>

若你只看整體成功率，會認為醫師 $B$ 比較好。若你分別看低風險與高風險病患，會認為醫師 $A$ 比較好。

請先不要急著問哪一個結論正確。更好的問題是，這個比較想回答什麼。若目標是比較兩位醫師在相同病況下的手術表現，風險分組可能是必須控制的背景資訊。若目標是描述某個實際制度下的整體結果，混合後的成功率也有它的意義。
</div>

## 一點歷史

辛普森悖論的命名本身也有一點歷史錯位。類似現象早在 Udny Yule 於 1903 年的研究中就已經出現，因此它也常被稱為 Yule-Simpson effect。後來 Edward H. Simpson 在 1951 年用列聯表清楚分析這類反轉，這個名稱才逐漸流傳開來。

它最有名的真實案例之一，是 1973 年 UC Berkeley 研究所入學資料。整體資料看似呈現性別差異，但分科系檢查後，問題其實和不同科系的錄取難度與申請組成密切相關。這也是辛普森悖論迷人的地方。數字沒有說謊，但它會要求我們先問清楚，自己到底正在比較什麼。

## 本篇小結

辛普森悖論不是一個孤立的趣聞。它說明，當我們比較兩個機率時，必須先問清楚，這兩個機率是否在同一個條件世界裡被計算。

在本篇的醫師案例中，分組內的成功率與混合後的成功率給出不同方向，差別來自低風險與高風險病患所占比例不同。也就是說，混合不是把資訊變少而已，它也會改變比較時使用的權重。

下一篇文章會把全機率定理反過來讀。若我們已經觀察到某個結果，該如何回頭判斷它最可能來自哪個來源？這會自然導向[貝氏定理](/teaching-topics/bayes-rule-posterior-probability/)。

若想親手調整混合比例，可以參考互動展示 [Simpson’s Paradox Mixing Lab](/demos/simpsons-paradox/)。它會固定各分組成功率，只讓你改變高風險案例比例，觀察整體比較如何翻轉。

## 參考文獻與延伸閱讀

- G. Udny Yule, “Notes on the Theory of Association of Attributes in Statistics”, *Biometrika*, 2(2), 121–134, 1903. [doi:10.1093/biomet/2.2.121](https://doi.org/10.1093/biomet/2.2.121).
- Edward H. Simpson, “The Interpretation of Interaction in Contingency Tables”, *Journal of the Royal Statistical Society, Series B*, 13(2), 238–241, 1951. [doi:10.1111/j.2517-6161.1951.tb00088.x](https://doi.org/10.1111/j.2517-6161.1951.tb00088.x).
- Colin R. Blyth, “On Simpson’s Paradox and the Sure-Thing Principle”, *Journal of the American Statistical Association*, 67(338), 364–366, 1972. [doi:10.1080/01621459.1972.10482387](https://doi.org/10.1080/01621459.1972.10482387).
- P. J. Bickel, E. A. Hammel, and J. W. O’Connell, “Sex Bias in Graduate Admissions, Data from Berkeley”, *Science*, 187(4175), 398–404, 1975. [doi:10.1126/science.187.4175.398](https://doi.org/10.1126/science.187.4175.398).
- Jan Sprenger and Naftali Weinberger, [Simpson’s Paradox](https://plato.stanford.edu/Archives/fall2022/entries/paradox-simpson/), *The Stanford Encyclopedia of Philosophy*.
