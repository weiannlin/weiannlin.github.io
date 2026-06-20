---
title: "貝氏定理，資訊如何帶來更新"
subtitle: "Bayes' Rule and Updating Information"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 1
topic: 9
order: 109
permalink: /teaching-topics/bayes-rule-posterior-probability/
date: 2026-05-06
published: true
excerpt: "貝氏定理把全機率定理反過來讀。當某個結果已經被觀察到時，它說明我們如何重新分配對不同可能來源的相信程度。"
---

[上一篇文章](/teaching-topics/group-mixing-simpsons-paradox/)由辛普森悖論說明，分組條件機率與混合後的整體機率可能給出不同方向的比較。由此可知，分割不只是計算技巧，也會影響我們如何理解整體資料。

本篇回到全機率定理本身，並把問題反過來看。全機率定理先問事件 $B$ 可以由哪些來源共同形成；貝氏定理 (Bayes' rule) 則問，若 $B$ 已經發生，我們該如何判斷它最可能是由哪個來源造成。它不只是另一個條件機率公式，而是在描述**資訊進來以後，機率如何被更新**。

這裡的「更新」不是說世界本身被資訊改變了。產品來自哪台機器、病人有沒有疾病、失聯飛機在哪個區域，通常早已有某個真實狀態；改變的是我們掌握的資訊，因此也改變了我們對各種可能狀態的機率評估。

以下固定令 $(S,\mathcal{F},\mathbb{P})$ 為一個機率空間。除非特別說明，文中的事件皆是 $\mathcal{F}$ 中的事件。

## 從總機率到反向追問

假設 $A_1,\ldots,A_n$ 是 $S$ 的一組分割，而事件 $B$ 是我們觀察到的新資訊。從正向角度看，全機率定理給出

$$
\mathbb{P}(B)=\sum_{j=1}^{n}\mathbb{P}(B\mid A_j)\,\mathbb{P}(A_j)
$$

也就是先看來源 $A_j$ 本身有多常出現，再看該來源之下 $B$ 有多容易發生，最後把所有來源對 $B$ 的貢獻加總。

但若 $B$ 已經發生，問題就變成反向的。所有能產生 $B$ 的來源當中，$A_i$ 這條路線佔了多少比例？這個比例就是 $\mathbb{P}(A_i\mid B)$。

這裡有四個常用名稱。

<ol class="topic-list-paren">
  <li>$\mathbb{P}(A_i)$ 是觀察 $B$ 以前，對來源 $A_i$ 的<strong class="text-nowrap">事前機率 (prior probability)</strong>。</li>
  <li>$\mathbb{P}(B\mid A_i)$ 是在來源 $A_i$ 下觀察到 $B$ 的<strong class="text-nowrap">條件機率 (conditional probability)</strong>。</li>
  <li>$\mathbb{P}(B)$ 是所有來源合起來產生 $B$ 的總機率，也可稱為<strong class="text-nowrap">邊際機率 (marginal probability)</strong>。</li>
  <li>$\mathbb{P}(A_i\mid B)$ 是觀察 $B$ 以後，對來源 $A_i$ 的<strong class="text-nowrap">事後機率 (posterior probability)</strong>。</li>
</ol>

這裡的「事前」與「事後」都是相對於事件 $B$ 是否已被觀測到而言。也就是說，$\mathbb{P}(A_i)$ 是尚未把 $B$ 納入資訊時，對來源 $A_i$ 的機率評估；$\mathbb{P}(A_i\mid B)$ 則是在已經知道 $B$ 發生後，重新評估來源 $A_i$ 的機率。它們描述的是資訊狀態的改變，而不必然是事件本身在時間上先後發生。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Historical Note</div>

貝氏定理得名自英國牧師兼數學家 Thomas Bayes。Bayes 生前並未發表這篇機率論文章；他過世後，友人 Richard Price 整理遺稿，才在 1763 年將文章送交 Royal Society 發表。換句話說，今天如此有名的公式，某種意義上是一個「身後被朋友救出來」的定理。

Bayes 原文中的問題沒有採用現代符號，而是透過把球隨機丟到桌面上的想像實驗，思考如何由觀察結果反推未知機率。後來 Laplace 也獨立發展並大幅推廣這種由結果反推原因的想法，因此現代貝氏思想其實同時有 Bayes 與 Laplace 的影子。
</div>

## 貝氏定理

<div class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Theorem 1.11 (Bayes' Rule)</div>

令 $A_1,\ldots,A_n$ 為 $S$ 的一組分割，且對任意 $i$ 皆有 $\mathbb{P}(A_i)>0$。若 $B\in\mathcal{F}$ 且 $\mathbb{P}(B)>0$，則對任意 $i=1,\ldots,n$，皆有

$$
\mathbb{P}(A_i\mid B)
=\frac{\mathbb{P}(B\mid A_i)\,\mathbb{P}(A_i)}
{\sum_{j=1}^{n}\mathbb{P}(B\mid A_j)\,\mathbb{P}(A_j)}
$$

此性質稱為**貝氏定理 (Bayes' rule)**。
</div>

<div class="topic-proof" markdown="1">
**Proof.** 由條件機率定義與乘法原理可知

$$
\mathbb{P}(A_i\mid B)
=\frac{\mathbb{P}(A_i\cap B)}{\mathbb{P}(B)}
=\frac{\mathbb{P}(B\mid A_i)\,\mathbb{P}(A_i)}{\mathbb{P}(B)}
$$

另一方面，由全機率定理可得

$$
\mathbb{P}(B)
=\sum_{j=1}^{n}\mathbb{P}(B\mid A_j)\,\mathbb{P}(A_j)
$$

將分母代入，即得貝氏定理。 $\square$
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

貝氏定理的分母不是一個隨便拿來正規化的常數；它正是由全機率定理算出的事件 $B$ 總機率。也就是說，分母回答「$B$ 可以透過哪些方式發生」，並把所有可能來源都納入；分子則只保留其中一個特定來源 $A_i$ 對事件 $B$ 的貢獻。
</div>

<div id="example-115" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.15 (Defective Item Source)</div>

延續前一篇 [Example 1.13 的機台不良品例子](/teaching-topics/total-probability-bayes-rule/#example-111)。三台機器 $M_1,M_2,M_3$ 製造同一種產品，分別負責總產量的 $20\%,30\%,50\%$；其產品不良率依序為 $5\%,4\%,2\%$。現在從全部產品中隨機抽出一件，且已知它是不良品。求這件不良品來自 $M_1$ 的機率。

令 $D$ 表示抽到不良品之事件。由題意可知

$$
\mathbb{P}(M_1)=0.2,\quad
\mathbb{P}(M_2)=0.3,\quad
\mathbb{P}(M_3)=0.5
$$

且

$$
\mathbb{P}(D\mid M_1)=0.05,\quad
\mathbb{P}(D\mid M_2)=0.04,\quad
\mathbb{P}(D\mid M_3)=0.02
$$

前一篇已由全機率定理算出

$$
\begin{aligned}
\mathbb{P}(D)
&=\mathbb{P}(D\mid M_1)\,\mathbb{P}(M_1)
+\mathbb{P}(D\mid M_2)\,\mathbb{P}(M_2)
+\mathbb{P}(D\mid M_3)\,\mathbb{P}(M_3)\\[0.45em]
&=0.05\times 0.2+0.04\times 0.3+0.02\times 0.5=0.032
\end{aligned}
$$

已知抽到的是不良品後，問題反過來變成「在所有不良品來源中，來自 $M_1$ 的那一部分占多少」。由貝氏定理可得

$$
\begin{aligned}
\mathbb{P}(M_1\mid D)
&=\frac{\mathbb{P}(D\mid M_1)\,\mathbb{P}(M_1)}{\mathbb{P}(D)}\\[0.45em]
&=\frac{0.05\times 0.2}{0.032}
=0.3125
\end{aligned}
$$

因此，這件不良品來自 $M_1$ 的事後機率為 $0.3125$。這個數值不是只看 $M_1$ 的不良率 $5\%$，也不是只看 $M_1$ 的產量比例 $20\%$；它同時使用「產品來自哪台機器」的事前機率，以及「各機器下出現不良品」的條件機率。
</div>

<div id="example-116" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.16 (Unsuccessful Search)</div>

有一架飛機失聯，搜救前先把三個可能區域記為 $A_1,A_2,A_3$，並認為飛機落在三區的事前機率相同。

$$
\mathbb{P}(A_1)=\mathbb{P}(A_2)=\mathbb{P}(A_3)=\frac{1}{3}
$$

若飛機真的在區域 $i$，搜尋該區找到飛機的機率為 $1-p_i$，因此搜尋失敗的機率為 $p_i$。現在先搜尋區域 $1$，但沒有找到飛機。求此時飛機其實在區域 $3$ 的事後機率。

令 $U_1$ 表示「搜尋區域 $1$ 但沒有找到飛機」。若飛機在區域 $1$，搜尋失敗的機率為 $p_1$；若飛機在區域 $2$ 或 $3$，搜尋區域 $1$ 本來就不會找到飛機，因此

$$
\mathbb{P}(U_1\mid A_1)=p_1,\qquad
\mathbb{P}(U_1\mid A_2)=1,\qquad
\mathbb{P}(U_1\mid A_3)=1
$$

由貝氏定理可得

$$
\begin{aligned}
\mathbb{P}(A_3\mid U_1)
&=
\frac{\mathbb{P}(U_1\mid A_3)\mathbb{P}(A_3)}
{\sum_{i=1}^{3}\mathbb{P}(U_1\mid A_i)\mathbb{P}(A_i)}\\[0.45em]
&=
\frac{1\cdot\frac{1}{3}}
{p_1\cdot\frac{1}{3}+1\cdot\frac{1}{3}+1\cdot\frac{1}{3}}
=\frac{1}{2+p_1}
\end{aligned}
$$

這個例子提醒我們，「沒有找到」也是資訊。它並不只表示搜尋失敗，也會降低飛機在已搜尋區域的機率，並相對提高其他區域的事後機率。
</div>

<div class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 1.8</div>

請注意這個例子裡，飛機是否落在區域 $1$ 早已是確定狀態。搜救失敗並不改變飛機的真實位置；它改變的是我們對三個可能區域的機率評估。

這也是貝氏定理在許多應用中有用的地方。我們可以把「未知但已存在的狀態」納入機率模型。保險中的風險類別、醫療中的疾病狀態、搜尋問題中的真實位置，都可以被看成尚未被我們完全知道的狀態；新的資料進來後，這些狀態的機率就會被重新分配。
</div>

## 基準率與原本比例

貝氏定理也說明，新資訊不能脫離原本的基準比例來看。醫療檢驗、保險定價與風險評估中，若只看「某訊號在高風險者中多常出現」，卻忘記高風險者原本佔多少比例，就很容易高估事後機率。

在醫療篩檢中，常見的真陽性 (true positive)、偽陽性 (false positive)、真陰性 (true negative) 與偽陰性 (false negative)，本質上都是條件機率。真陽性率是在已知個體真的罹病下，檢驗呈陽性的機率；偽陽性率是在已知個體未罹病下，檢驗卻呈陽性的機率。相對地，真陰性率是在已知個體未罹病下，檢驗呈陰性的機率；偽陰性率則是在已知個體真的罹病下，檢驗卻呈陰性的機率。

醫學上也常用**敏感性 (sensitivity)** 與**特異性 (specificity)** 來描述檢驗表現。敏感性就是真陽性率，也就是 $\mathbb{P}(+\mid D)$；特異性就是真陰性率，也就是 $\mathbb{P}(-\mid D^{\prime})$。因此，偽陽性率是 $1-\text{specificity}$，而偽陰性率是 $1-\text{sensitivity}$。

讀者也可以打開 [Rapid Test Bayesian Updating Lab](/demos/bayesian-updating/)自行調整盛行率、敏感性與特異性，觀察一次陽性或陰性結果如何改變事後機率。特別可以比較敏感性與特異性都高、以及敏感性高但特異性低時，連續檢測路徑如何不同。

例如某疾病在一個族群中的盛行率只有 $1\%$。假設某檢驗對真正罹病者呈陽性的機率為 $0.99$，而對未罹病者也有 $0.05$ 的偽陽性率。令 $D$ 表示「罹病」，令 $+$ 表示「檢驗呈陽性」。若某人檢驗呈陽性，則

$$
\begin{aligned}
\mathbb{P}(D\mid +)
&=\frac{\mathbb{P}(+\mid D)\,\mathbb{P}(D)}
{\mathbb{P}(+\mid D)\,\mathbb{P}(D)+\mathbb{P}(+\mid D^{\prime})\,\mathbb{P}(D^{\prime})}\\[0.45em]
&=\frac{0.99\times 0.01}{0.99\times 0.01+0.05\times 0.99}\approx 0.167
\end{aligned}
$$

即使檢驗看起來很靈敏，陽性之後真正罹病的機率仍大約只有 $16.7\%$。這不是檢驗沒有用，而是因為罹病者在原族群中本來就很少；偽陽性即使比例不高，乘上大量未罹病者以後，仍可能形成相當大的陽性來源。

## 幾個延伸視角

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Perspective</div>

**貝氏統計 (Bayesian statistics).** 在貝氏統計裡，未知參數本身也被放入機率模型中。資料進來以前，我們用事前分配 (prior distribution) 描述對參數的認識；資料進來以後，則可更新為事後分配 (posterior distribution)。因此，貝氏統計把「資訊帶來更新」放在模型的中心。

本頁搭配的快篩更新 demo 正是貝氏定理的一個具體版本。盛行率提供事前機率，敏感性與特異性提供條件機率，檢測結果則把這些資訊合併成事後機率。

<!-- Future extension, hidden until a machine-learning or classification topic exists:
Naive Bayes 分類法. 在分類問題中，我們常想計算觀察到某些變數後，資料屬於某類別的機率。基本形式可寫成

$$
\mathbb{P}(C_k\mid x_1,\ldots,x_m)
\propto
\mathbb{P}(C_k)\prod_{r=1}^{m}\mathbb{P}(x_r\mid C_k)
$$

其中 $C_k$ 是類別，而 $x_1,\ldots,x_m$ 是觀察到的變數。此法通常假設，在給定類別後，這些觀察變數可以近似看作條件獨立。Reference to preserve for that future extension: David J. Hand and Keming Yu. 2001. “Idiot’s Bayes—Not So Stupid After All?” International Statistical Review 69 (3): 385–398.
-->
</div>

## 本篇小結

貝氏定理可以視為「全機率定理的反向讀法」，也可以視為一種資訊更新規則。

| 名稱 | 形式 | 角色 |
| --- | --- | --- |
| 事前機率 | $\mathbb{P}(A_i)$ | 資訊進來以前，來源 $A_i$ 原本有多可能 |
| 條件機率 | $\mathbb{P}(B\mid A_i)$ | 若來源為 $A_i$，觀察到 $B$ 有多合理 |
| 總機率／邊際機率 | $\mathbb{P}(B)=\sum_j\mathbb{P}(B\mid A_j)\,\mathbb{P}(A_j)$ | 所有來源合起來，觀察到 $B$ 的總機率 |
| 事後機率 | $\mathbb{P}(A_i\mid B)$ | 資訊 $B$ 出現後，來源 $A_i$ 更新後的可能性 |

條件機率、獨立性、全機率定理與貝氏定理合在一起，完成第一章後半部的主要工具。到目前為止，我們討論的仍是事件機率。下一章會從[隨機變數，從樣本空間到數線](/teaching-topics/random-variables-from-sample-space-to-real-line/)開始，把樣本空間中的結果映到實數線上，使函數、期望與分配函數等工具自然進入機率論。

## 參考文獻與延伸閱讀

- 黃文璋，2003，《機率論》，初版，華泰文化。
- Thomas Bayes and Richard Price. 1763. “An Essay towards Solving a Problem in the Doctrine of Chances.” *Philosophical Transactions of the Royal Society of London* 53: 370–418.
- H. O. Hartley. 1963. “In Dr. Bayes’ Consulting Room.” *The American Statistician* 17 (1): 22–24.
- Andrew Gelman, John B. Carlin, Hal S. Stern, David B. Dunson, Aki Vehtari, and Donald B. Rubin. 2013. *Bayesian Data Analysis*. 3rd ed. Chapman and Hall/CRC.
- Morris H. DeGroot and Mark J. Schervish. 2012. *Probability and Statistics*. 4th ed. Pearson.
- Amos Tversky and Daniel Kahneman. 1974. “Judgment under Uncertainty: Heuristics and Biases.” *Science* 185 (4157): 1124–1131.
- Gerd Gigerenzer and Ulrich Hoffrage. 1995. “How to Improve Bayesian Reasoning without Instruction: Frequency Formats.” *Psychological Review* 102 (4): 684–704.
