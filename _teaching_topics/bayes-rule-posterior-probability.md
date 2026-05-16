---
title: "貝氏定理，資訊如何帶來更新"
subtitle: "Bayes' Rule and Updating Information"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 1
topic: 7
order: 107
permalink: /teaching-topics/bayes-rule-posterior-probability/
date: 2026-05-06
published: true
excerpt: "貝氏定理描述資訊進來以後，我們如何重新分配對不同可能狀態的相信程度；它把事前機率、條件機率、總機率與事後機率連在一起。"
---

[上一篇文章](/teaching-topics/total-probability-bayes-rule/)利用分割與全機率定理，把事件 $B$ 的機率拆成不同來源的貢獻後再加總。換句話說，全機率定理回答的是，$B$ 總共多容易發生？

本文把問題反過來看。若 $B$ 已經發生，我們該如何判斷它最可能是由哪個來源造成？這正是**貝氏定理 (Bayes' rule)** 的角色。它不只是另一個條件機率公式，而是在描述一件很重要的事，也就是**資訊進來以後，機率會被更新。**

這裡的「更新」不是說世界本身被資訊改變了。地底下有沒有石油，病人有沒有疾病，一封信是不是垃圾郵件，通常早已有某個真實狀態；改變的是我們掌握的資訊，因此也改變了我們對各種可能狀態的機率評估。

本文固定令 $(S,\mathcal{F},\mathbb{P})$ 為一個機率空間。除非特別說明，文中的事件皆是 $\mathcal{F}$ 中的事件。

## 從總機率到反向追問

假設 $A_1,\ldots,A_n$ 是 $S$ 的一組分割，而事件 $B$ 是我們觀察到的新資訊。從正向角度看，全機率定理告訴我們

$$
\mathbb{P}(B)=\sum_{j=1}^{n}\mathbb{P}(B\mid A_j)\,\mathbb{P}(A_j)
$$

也就是先看來源 $A_j$ 本身有多常出現，再看該來源之下 $B$ 有多容易發生，最後把所有來源對 $B$ 的貢獻加總。

但若 $B$ 已經發生，問題就變成反向的。所有能產生 $B$ 的來源當中，$A_i$ 這條路線佔了多少比例？這個比例就是 $\mathbb{P}(A_i\mid B)$。

這裡有四個重要語言。

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

Bayes 原文中的問題也不是以現代符號寫成，而是透過把球隨機丟到桌面上的想像實驗，思考如何由觀察結果反推未知機率。後來 Laplace 也獨立發展並大幅推廣這種由結果反推原因的想法，因此現代貝氏思想其實同時有 Bayes 與 Laplace 的影子。
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

## Example 1.12 (Exploratory Drilling Result)

假設某公司評估一塊區域是否含有可開採石油。令 $O$ 表示「該區域有石油」。根據過去地質資料，公司先認為

$$
\mathbb{P}(O)=0.2,\qquad
\mathbb{P}(O^{\prime})=0.8
$$

接著公司進行一次試挖。令 $N$ 表示「試挖沒有發現可開採石油」。這裡要特別注意，沒有挖到不代表該區域一定沒有石油。油藏可能很深，試挖點也可能偏離主要油層；若下鑽深度不夠，沒有發現本來就是可能結果。

因此，若該區域真的有石油，試挖仍可能沒有發現，其機率為 $0.2$；若該區域沒有石油，試挖自然不會發現石油。也就是

$$
\mathbb{P}(N\mid O)=0.2,\qquad
\mathbb{P}(N\mid O^{\prime})=1
$$

現在試挖結果真的沒有發現可開採石油。此時該區域仍有石油的事後機率為多少？

由全機率定理可得

$$
\begin{aligned}
\mathbb{P}(N)
&=\mathbb{P}(N\mid O)\,\mathbb{P}(O)
+\mathbb{P}(N\mid O^{\prime})\,\mathbb{P}(O^{\prime})\\[0.45em]
&=0.2\times 0.2+1\times 0.8=0.84
\end{aligned}
$$

因此由貝氏定理可得

$$
\begin{aligned}
\mathbb{P}(O\mid N)
&=\frac{\mathbb{P}(N\mid O)\,\mathbb{P}(O)}{\mathbb{P}(N)}\\[0.45em]
&=\frac{0.2\times 0.2}{0.84}
=\frac{1}{21}\approx 0.048
\end{aligned}
$$

試挖結果確實帶來資訊，使有石油的機率從 $0.2$ 向下修正為約 $0.048$。但它沒有讓機率變成 $0$，因為即使該區域真的有石油，試挖也可能沒有命中可開採的位置。這正是貝氏更新的核心想法，新資訊會推動機率移動，但移動多少，仍取決於事前機率與觀測結果本身的可靠度。

<div class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 1.7</div>

請注意這個例子裡，地底下是否有石油不是試挖後才決定的。試挖改變的不是地底狀態，而是我們對地底狀態的資訊。

這也是貝氏定理在許多應用中迷人的地方。我們可以把「未知但已存在的狀態」納入機率模型。保險中的風險類別、醫療中的疾病狀態、機器學習中的文件類別，都可以被看成尚未被我們完全知道的狀態；新的資料進來後，這些狀態的機率就會被重新分配。
</div>

## 基準率與原本比例

貝氏定理也提醒我們，新資訊不能脫離原本的基準比例來看。醫療檢驗、保險定價與風險評估中，若只看「某訊號在高風險者中多常出現」，卻忘記高風險者原本佔多少比例，就很容易高估事後機率。

在醫療篩檢中，常見的真陽性 (true positive)、偽陽性 (false positive)、真陰性 (true negative) 與偽陰性 (false negative)，其實都可以理解為條件機率。真陽性率是在已知個體真的罹病下，檢驗呈陽性的機率；偽陽性率是在已知個體未罹病下，檢驗卻呈陽性的機率。相對地，真陰性率是在已知個體未罹病下，檢驗呈陰性的機率；偽陰性率則是在已知個體真的罹病下，檢驗卻呈陰性的機率。

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

**貝氏統計 (Bayesian statistics).** 在貝氏統計裡，未知參數本身也被放入機率模型中。資料進來以前，我們用事前分布 (prior distribution) 描述對參數的認識；資料進來以後，則可更新為事後分布 (posterior distribution)。因此，貝氏統計的核心想法正是「資訊帶來更新」。

**Naive Bayes classifier.** 在分類問題中，我們常想計算「看到這些特徵後，資料屬於某類別的機率」。例如垃圾郵件分類會問，在某些字詞出現後，這封信是 spam 的機率多大？Naive Bayes classifier 的基本形式可以寫成

$$
\mathbb{P}(C_k\mid x_1,\ldots,x_m)
\propto
\mathbb{P}(C_k)\prod_{r=1}^{m}\mathbb{P}(x_r\mid C_k)
$$

其中 $C_k$ 是類別，而 $x_1,\ldots,x_m$ 是觀察到的特徵。它之所以稱為 naive，是因為模型通常假設，在給定類別後，這些特徵可以近似看作條件獨立。下一篇會正式討論獨立性；此處只要先把它理解成「給定類別後，特徵之間不再提供太多彼此的額外資訊」即可。

這和本頁搭配的快篩更新 demo 是同一種結構。若把連續幾次檢測結果視為 $x_1,\ldots,x_m$，而把真實疾病狀態視為類別 $C_k$，則每一次陽性或陰性結果，都等於把一個新的條件機率乘進更新式。這樣做之所以合理，正是因為我們暫時假設，在給定真實疾病狀態後，各次檢測誤差可以近似看作彼此獨立。這個假設未必完全真實，但在許多分類與篩檢問題中已經相當有用。
</div>

## 本篇小結

貝氏定理可以視為「全機率定理的反向讀法」，也可以視為一種資訊更新規則。

| 名稱 | 形式 | 角色 |
| --- | --- | --- |
| 事前機率 | $\mathbb{P}(A_i)$ | 資訊進來以前，來源 $A_i$ 原本有多可能 |
| 條件機率 | $\mathbb{P}(B\mid A_i)$ | 若來源為 $A_i$，觀察到 $B$ 有多合理 |
| 總機率／邊際機率 | $\mathbb{P}(B)=\sum_j\mathbb{P}(B\mid A_j)\,\mathbb{P}(A_j)$ | 所有來源合起來，觀察到 $B$ 的總機率 |
| 事後機率 | $\mathbb{P}(A_i\mid B)$ | 資訊 $B$ 出現後，來源 $A_i$ 更新後的可能性 |

條件機率與貝氏定理說明資訊如何改變機率。若資訊進來以後，某個事件的機率完全不變，就會自然導向下一個主題，也就是[獨立性](/teaching-topics/independence-and-conditional-independence/)。
