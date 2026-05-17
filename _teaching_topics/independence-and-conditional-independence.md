---
title: "獨立性，資訊不再改變機率"
subtitle: "Independence and Conditional Independence"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 1
topic: 9
order: 109
permalink: /teaching-topics/independence-and-conditional-independence/
date: 2026-05-17
published: true
excerpt: "獨立性描述的是一種特別的資訊關係。若知道事件 B 發生後，事件 A 的機率完全不變，則 B 對 A 沒有提供新的機率資訊。"
---

[上一篇文章](/teaching-topics/bayes-rule-posterior-probability/)把貝氏定理理解為資訊更新規則。觀察到事件 $B$ 後，我們會重新評估某些來源或狀態的機率。

本篇處理另一種同樣重要的情況。若事件 $B$ 已經發生，但這個資訊完全不改變事件 $A$ 的機率，那麼我們會說 $A$ 與 $B$ 彼此獨立。獨立性不是說兩件事都很隨機，也不是說它們沒有任何文字上的關係；它說的是，一件事的發生不改變另一件事的機率評估。

以下固定令 $(S,\mathcal{F},\mathbb{P})$ 為一個機率空間。除非特別說明，文中的事件皆是 $\mathcal{F}$ 中的事件。

## 從條件機率看獨立

若 $\mathbb{P}(B)>0$，由條件機率可知，知道 $B$ 發生後，事件 $A$ 的機率會被改寫為

$$
\mathbb{P}(A\mid B)
$$

若這個數值剛好等於原本的 $\mathbb{P}(A)$，也就是

$$
\mathbb{P}(A\mid B)=\mathbb{P}(A)
$$

那麼知道 $B$ 發生並沒有改變我們對 $A$ 的機率判斷。這就是獨立性的基本意義。

不過，這個寫法需要 $\mathbb{P}(B)>0$。為了讓定義在一般情況下也可使用，我們通常把條件機率式改寫成乘法形式。

<div class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.15</div>

令 $A,B\in\mathcal{F}$。若

$$
\mathbb{P}(A\cap B)=\mathbb{P}(A)\,\mathbb{P}(B)
$$

則稱 $A$ 與 $B$ 為**獨立事件 (independent events)**。
</div>

這個定義是對稱的，因為 $A\cap B=B\cap A$。因此，若 $A$ 與 $B$ 獨立，則可以同時理解為 $B$ 不改變 $A$ 的機率，也可以理解為 $A$ 不改變 $B$ 的機率。

當 $\mathbb{P}(B)>0$ 時，由定義可得

$$
\mathbb{P}(A\mid B)
=\frac{\mathbb{P}(A\cap B)}{\mathbb{P}(B)}
=\frac{\mathbb{P}(A)\,\mathbb{P}(B)}{\mathbb{P}(B)}
=\mathbb{P}(A)
$$

同理，若 $\mathbb{P}(A)>0$，則也有 $\mathbb{P}(B\mid A)=\mathbb{P}(B)$。

<div class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.14 (A Die Roll)</div>

投擲一顆公正骰子一次。令

$$
A=\{2,4,6\},\qquad B=\{1,2,3,4\}
$$

其中 $A$ 表示點數為偶數，$B$ 表示點數不超過 $4$。此時

$$
\mathbb{P}(A)=\frac{3}{6}=\frac{1}{2},\qquad
\mathbb{P}(B)=\frac{4}{6}=\frac{2}{3}
$$

而

$$
A\cap B=\{2,4\}
$$

因此

$$
\mathbb{P}(A\cap B)=\frac{2}{6}=\frac{1}{3}
=\frac{1}{2}\times\frac{2}{3}
=\mathbb{P}(A)\,\mathbb{P}(B)
$$

所以 $A$ 與 $B$ 獨立。換句話說，知道點數不超過 $4$ 後，偶數的比例仍然是 $1/2$。
</div>

## 互斥不是獨立

初學者很容易把互斥與獨立混在一起。這兩者其實方向完全不同。

互斥 (mutually exclusive) 說的是兩事件不能同時發生。若 $A\cap B=\varnothing$，則

$$
\mathbb{P}(A\cap B)=0
$$

但若 $\mathbb{P}(A)>0$ 且 $\mathbb{P}(B)>0$，則

$$
\mathbb{P}(A)\,\mathbb{P}(B)>0
$$

因此，兩個機率皆為正的互斥事件不可能獨立。直觀上也很清楚，若知道 $B$ 已經發生，那麼 $A$ 就不可能發生，這當然大幅改變了 $A$ 的機率。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

互斥強調「不能同時發生」。獨立強調「資訊不改變機率」。如果兩個非空事件互斥，那麼其中一個事件發生，本身就是另一個事件沒有發生的強烈資訊。
</div>

<div class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 1.9</div>

互斥與獨立的關係，可以用下表整理。請特別注意機率為 $0$ 的事件，因為這正是許多人第一次學獨立性時最容易忽略的邊界情況。

| 情況 | $A\cap B=\varnothing$ | $A\cap B\neq\varnothing$ |
| --- | --- | --- |
| $\mathbb{P}(A)>0$ 且 $\mathbb{P}(B)>0$ | $A,B$ 非獨立 | 若 $\mathbb{P}(A\cap B)=\mathbb{P}(A)\,\mathbb{P}(B)$，則 $A,B$ 獨立；否則非獨立 |
| $\mathbb{P}(A)=0$ 或 $\mathbb{P}(B)=0$ | $A,B$ 獨立 | $A,B$ 獨立，因為 $\mathbb{P}(A\cap B)=0$ |

這張表想提醒的是，若兩事件機率皆為正，互斥與獨立幾乎站在相反的方向；但只要其中一個事件機率為 $0$，乘法條件會自動成立。這不是說兩事件在直覺上「沒有關係」，而是獨立性的定義本身只看機率乘法是否成立。
</div>

## 多個事件的獨立

兩個事件的獨立只需要檢查一次交集。但當事件變多時，事情會更細緻。三個事件 $A,B,C$ 彼此成對獨立，並不保證三者共同獨立。

<div class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.16</div>

令 $A_1,\ldots,A_n\in\mathcal{F}$。若對任意 $2\le k\le n$ 與任意相異指標 $i_1,\ldots,i_k$，皆有

$$
\mathbb{P}(A_{i_1}\cap\cdots\cap A_{i_k})
=
\mathbb{P}(A_{i_1})\cdots\mathbb{P}(A_{i_k})
$$

則稱 $A_1,\ldots,A_n$ 為**相互獨立 (mutually independent)**。
</div>

這個定義要求所有子群都滿足乘法規則。若只知道每一對事件都獨立，稱為**成對獨立 (pairwise independent)**；成對獨立比相互獨立弱。

<div class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.15 (Pairwise but Not Mutual)</div>

連續投擲一枚公正硬幣兩次，樣本空間為

$$
S=\{HH,HT,TH,TT\}
$$

令

$$
A=\{HH,HT\},\qquad
B=\{HH,TH\},\qquad
C=\{HH,TT\}
$$

其中 $A$ 表示第一次為正面，$B$ 表示第二次為正面，$C$ 表示兩次結果相同。三者的機率皆為 $1/2$。

任取兩個事件，其交集機率皆為 $1/4$。例如

$$
\mathbb{P}(A\cap B)=\mathbb{P}(\{HH\})=\frac{1}{4}
=\frac{1}{2}\times\frac{1}{2}
$$

因此 $A,B,C$ 成對獨立。但是

$$
A\cap B\cap C=\{HH\}
$$

所以

$$
\mathbb{P}(A\cap B\cap C)=\frac{1}{4}
\neq
\frac{1}{8}
=\mathbb{P}(A)\,\mathbb{P}(B)\,\mathbb{P}(C)
$$

故 $A,B,C$ 並非相互獨立。
</div>

<div class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 1.10</div>

請試著不用公式想想看。若你已經知道第一次為正面，也知道第二次為正面，那麼「兩次結果相同」其實已經被完全決定了。

這正是三個事件沒有相互獨立的地方。每一對事件單獨看都沒有互相洩漏資訊，但三個事件放在一起時，第三個事件會被前兩個事件鎖定。
</div>

## 條件獨立

在貝氏定理與分類問題中，我們常常不是直接假設事件本身獨立，而是說在某個狀態已知後，它們才獨立。這稱為條件獨立。

<div class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.17</div>

令 $A,B,C\in\mathcal{F}$，且 $\mathbb{P}(C)>0$。若

$$
\mathbb{P}(A\cap B\mid C)
=\mathbb{P}(A\mid C)\,\mathbb{P}(B\mid C)
$$

則稱 $A$ 與 $B$ 在給定 $C$ 後**條件獨立 (conditionally independent given $C$)**。
</div>

條件獨立不是獨立的附屬品，而是一個新的參照世界。它說的是，當我們已經固定在 $C$ 所代表的世界裡，$A$ 與 $B$ 不再彼此提供額外資訊。

快篩檢測正是很好的例子。令 $D$ 表示真實罹病狀態，令 $T_1,T_2$ 表示兩次檢測都呈陽性的事件。若我們假設在真實狀態固定後，每次檢測誤差近似獨立，則有

$$
\mathbb{P}(T_1\cap T_2\mid D)
=\mathbb{P}(T_1\mid D)\,\mathbb{P}(T_2\mid D)
$$

也有

$$
\mathbb{P}(T_1\cap T_2\mid D^{\prime})
=\mathbb{P}(T_1\mid D^{\prime})\,\mathbb{P}(T_2\mid D^{\prime})
$$

但這不代表 $T_1$ 與 $T_2$ 在未給定真實狀態時獨立。第一次陽性會提高我們對罹病狀態的機率評估，而罹病狀態又會提高第二次陽性的機率。因此，未給定 $D$ 或 $D^{\prime}$ 時，兩次陽性結果通常會彼此相關。

<div class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 1.11</div>

若在分割的每一塊裡，$A$ 與 $B$ 都條件獨立，能不能推出 $A$ 與 $B$ 本身獨立？答案是否定的。

令 $\{C_1,C_2\}$ 為 $S$ 的一個分割，且

$$
\mathbb{P}(C_1)=\mathbb{P}(C_2)=\frac{1}{2}
$$

假設在 $C_1$ 下，$A$ 與 $B$ 各自發生的條件機率都是 $9/10$；在 $C_2$ 下，$A$ 與 $B$ 各自發生的條件機率都是 $1/10$。再假設在每個分割區塊下，$A$ 與 $B$ 都條件獨立。

於是由全機率定理可得

$$
\mathbb{P}(A)=\mathbb{P}(B)
=
\frac{1}{2}\cdot\frac{9}{10}
+
\frac{1}{2}\cdot\frac{1}{10}
=
\frac{1}{2}
$$

但若要計算 $A\cap B$，同樣要先用分割把它拆成兩塊。

$$
\mathbb{P}(A\cap B)
=
\mathbb{P}(A\cap B\cap C_1)
+
\mathbb{P}(A\cap B\cap C_2)
$$

再由乘法原理與條件獨立性可得

$$
\begin{aligned}
\mathbb{P}(A\cap B)
&=
\mathbb{P}(A\cap B\mid C_1)\mathbb{P}(C_1)
+
\mathbb{P}(A\cap B\mid C_2)\mathbb{P}(C_2) \\[0.35em]
&=
\mathbb{P}(A\mid C_1)\mathbb{P}(B\mid C_1)\mathbb{P}(C_1)
+
\mathbb{P}(A\mid C_2)\mathbb{P}(B\mid C_2)\mathbb{P}(C_2) \\[0.35em]
&=
\frac{1}{2}\left(\frac{9}{10}\right)^2
+
\frac{1}{2}\left(\frac{1}{10}\right)^2
=
\frac{41}{100}
\end{aligned}
$$

而

$$
\mathbb{P}(A)\mathbb{P}(B)=\frac{1}{4}
$$

因此 $A$ 與 $B$ 在每個分割區塊內都條件獨立，混合回整體後卻不獨立。原因是未給定分割區塊時，$A$ 的發生會改變我們對目前落在哪個 $C_i$ 的判斷；而 $B$ 的發生機率也會隨 $C_i$ 改變。這種共同來源會在整體中留下關聯。
</div>

這也是 Naive Bayes classifier 的核心假設。給定類別 $C_k$ 後，模型把特徵 $x_1,\ldots,x_m$ 近似看成條件獨立，因此可以把許多條件機率相乘。這個假設未必完全真實，但它把複雜的聯合分布拆成許多較容易估計的部分。

## 本篇小結

獨立性是條件機率的特殊情況。它描述的不是兩件事沒有任何關聯，而是某個資訊進來後，另一個事件的機率不變。

| 概念 | 形式 | 重點 |
| --- | --- | --- |
| 兩事件獨立 | $\mathbb{P}(A\cap B)=\mathbb{P}(A)\,\mathbb{P}(B)$ | 知道其中一件事，不改變另一件事的機率 |
| 互斥 | $A\cap B=\varnothing$ | 兩件事不能同時發生 |
| 相互獨立 | 所有子群交集都滿足乘法規則 | 多事件一起看也不洩漏額外資訊 |
| 條件獨立 | $\mathbb{P}(A\cap B\mid C)=\mathbb{P}(A\mid C)\,\mathbb{P}(B\mid C)$ | 固定在 $C$ 的世界裡，$A$ 與 $B$ 不再互相提供資訊 |

條件機率問資訊如何改變機率，貝氏定理問資訊如何更新我們對於未知狀態的認知，獨立性則描述資訊進來後機率仍然不變的情形。這三件事合在一起，構成第一章後半部最重要的機率語言。

不過，到目前為止，我們討論的仍是事件的機率。每一個事件 $A$ 對應到一個數 $\mathbb{P}(A)$，這足以建立機率模型的基本語言；但若永遠只逐一討論事件，發展會比較受限。下一章開始，我們會把樣本空間中的結果透過隨機變數映到數線上，使我們不只問某個事件有多可能，也能討論數值與機率之間的函數關係。這一步會讓期望、分配函數與極限分配等更多數學工具自然進入機率論。

## 參考文獻與延伸閱讀

- William Feller, *An Introduction to Probability Theory and Its Applications*, Volume I, chapters on independence.
- Patrick Billingsley, *Probability and Measure*, sections on independent events and independent random variables.
- Y. S. Chow and Henry Teicher, *Probability Theory, Independence, Interchangeability, Martingales*, 3rd ed., Springer, 1997, chapters on independence.
- Christopher M. Bishop, *Pattern Recognition and Machine Learning*, discussion of Naive Bayes and conditional independence.
- Judea Pearl, Madelyn Glymour, and Nicholas P. Jewell, *Causal Inference in Statistics, A Primer*, discussion of conditional independence in graphical thinking.
- David A. Pierce and Richard L. Dykstra, “Independence and the Normal Distribution”, *The American Statistician*, 23(4), 39, 1969. [doi:10.1080/00031305.1969.10481871](https://doi.org/10.1080/00031305.1969.10481871).
- James D. Broffitt, “Zero Correlation, Independence, and Normality”, *The American Statistician*, 40(4), 276–277, 1986. [doi:10.1080/00031305.1986.10475412](https://doi.org/10.1080/00031305.1986.10475412).
- A. Philip Dawid, “Conditional Independence in Statistical Theory”, *Journal of the Royal Statistical Society, Series B*, 41(1), 1–31, 1979. [doi:10.1111/j.2517-6161.1979.tb01052.x](https://doi.org/10.1111/j.2517-6161.1979.tb01052.x).
