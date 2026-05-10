---
title: "分割與全機率定理：從分類到加總"
subtitle: "Partitions and the Law of Total Probability"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 1
topic: 6
order: 106
permalink: /teaching-topics/total-probability-bayes-rule/
date: 2026-05-05
excerpt: "當樣本空間被一組互斥且周延的事件分割時，事件可以被拆成互斥片段；全機率定理將各來源的貢獻加總，成為計算總機率的基本工具。"
---

[上一篇文章](/teaching-topics/conditional-probability-information/)把條件機率理解為「資訊進來以後的重新評估」。本文換一個角度：如果事件 $B$ 可能由許多不同來源造成，我們可以先把樣本空間依來源切開，再分別計算各來源對 $B$ 的貢獻。

這正是**分割 (partition)** 與**全機率定理 (the law of total probability)** 的角色。它們讓我們把一個總機率拆成幾個互斥片段來計算：先切開來源，逐一計算各來源對目標事件的貢獻，最後再加總。

本文固定令 $(S,\mathcal{F},\mathbb{P})$ 為一個機率空間。除非特別說明，文中的事件皆是 $\mathcal{F}$ 中的事件。

## 分割：把樣本空間分成不重疊的來源，但沒有遺漏

許多機率問題都可以先問一句話：這件事可能來自哪幾種互不重疊的情況？例如一件產品可能來自不同機台，一位病患可能屬於不同疾病狀態，一封郵件可能來自不同寄件類型。這些「來源」若剛好能把整個樣本空間切乾淨，就形成一組分割。

<div class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 1.14</div>

令 $A_1,\ldots,A_n\in\mathcal{F}$。若下列兩條件成立，則它們構成 $S$ 的一組**分割 (partition)**：

<ol class="topic-list-paren">
  <li><strong>互斥 (mutually exclusive)</strong>：對任意 $i\neq j$，皆有

$$
A_i\cap A_j=\varnothing
$$

  </li>
  <li><strong>周延 (collectively exhaustive)</strong>：所有事件合起來正好是整個樣本空間，即

$$
\bigcup_{i=1}^{n}A_i=S
$$

  </li>
</ol>
</div>

互斥表示這些來源不會同時發生；周延表示所有可能情況都已被列入。換句話說，分割就是把樣本空間「分成數個不重複而且沒有遺漏的事件」。

<figure class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/total-probability-partition.svg" alt="樣本空間被 A_1 到 A_n 分割，而事件 B 被切成 B cap A_i 的互斥片段。">
  <figcaption><span class="topic-figure__label">Fig. 1.7.</span> 當 $A_1,\ldots,A_n$ 是 $S$ 的一組分割時，事件 $B$ 會被切成 $B\cap A_1,\ldots,B\cap A_n$ 這些互斥片段。</figcaption>
</figure>

## 全機率定理

若 $A_1,\ldots,A_n$ 是 $S$ 的一組分割，那麼任意事件 $B$ 都可以被這組分割切成許多互斥片段：

$$
B=\bigcup_{i=1}^{n}(B\cap A_i)
$$

這件事來自集合的分配律與分割的周延性。把它放進機率裡，就得到一個計算總機率的工具：切成片段，逐片計算，再加總。

<div class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Theorem 1.10 (Law of Total Probability)</div>

令 $A_1,\ldots,A_n$ 為 $S$ 的一組分割，且令 $B\in\mathcal{F}$。則

$$
\mathbb{P}(B)
=\mathbb{P}\left(\bigcup_{i=1}^{n}(B\cap A_i)\right)
=\sum_{i=1}^{n}\mathbb{P}(B\cap A_i)
$$

此性質稱為**全機率定理 (the law of total probability)**。
</div>

<div class="topic-proof" markdown="1">
**Proof.** 因為 $A_1,\ldots,A_n$ 為 $S$ 的一組分割，所以

$$
B=B\cap S
=B\cap\left(\bigcup_{i=1}^{n}A_i\right)
=\bigcup_{i=1}^{n}(B\cap A_i)
$$

此外，$B\cap A_1,\ldots,B\cap A_n$ 兩兩互斥。因此由有限可加性可得

$$
\mathbb{P}(B)
=\mathbb{P}\left(\bigcup_{i=1}^{n}(B\cap A_i)\right)
=\sum_{i=1}^{n}\mathbb{P}(B\cap A_i)
$$

故得證。 $\square$
</div>

若進一步假設 $\mathbb{P}(A_i)>0$，便可以用乘法原理將每個交集機率改寫成

$$
\mathbb{P}(B\cap A_i)=\mathbb{P}(B\mid A_i)\,\mathbb{P}(A_i)
$$

因此全機率定理常用的條件機率版本為

$$
\mathbb{P}(B)=\sum_{i=1}^{n}\mathbb{P}(B\mid A_i)\,\mathbb{P}(A_i)
$$

這個公式的意思很樸素：先看每個來源 $A_i$ 本身有多常出現，再看在該來源之下 $B$ 有多容易發生，最後把所有來源的貢獻加總起來。換句話說，這就是機率問題中的**分而治之**：先把問題依來源切成互不重疊的小問題，再把每一塊的貢獻加回來。在英文片語當中常常聽到的 <span class="text-nowrap">divide-and-conquer</span>，在這裡就是這個意思。

<div class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.10 (The Monty Hall Problem)</div>

蒙提霍爾問題 (Monty Hall problem) 是一個源自真實歷史故事的數學問題。它得名自美國電視遊戲節目 <span class="text-nowrap">Let's Make a Deal</span>；節目主持人正是 Monty Hall。這個實境節目自 1963 年開始播出，核心張力就是「交易」：參賽者可以保留手上的東西，也可以相信主持人的邀請，換成門後、箱子裡或布幕後的未知獎品。這種舞台效果後來被整理成三扇門的標準機率問題；看起來像是剩下兩扇門各半，實際上主持人掌握資訊並刻意打開羊門，才是計算時不能忽略的線索。

考慮這個標準化版本：三扇門中有一扇門後面是車，其餘兩扇門後面是羊。你先選一扇門，主持人知道車在哪裡，並從剩下兩扇門中打開一扇有羊的門。此時若你採取「切換」策略，勝率是多少？

令 $C$ 表示「一開始選到車」，令 $G$ 表示「一開始選到羊」。事件 $C$ 與 $G$ 構成樣本空間的一組分割；其機率為

$$
\mathbb{P}(C)=\frac{1}{3},\qquad
\mathbb{P}(G)=\frac{2}{3}
$$

令 $W$ 表示「切換後獲勝」。若一開始選到車，切換後必定輸；若一開始選到羊，主持人打開另一扇有羊的門後，剩下那扇未開且未選的門必定是車。因此

$$
\mathbb{P}(W\mid C)=0,\qquad
\mathbb{P}(W\mid G)=1
$$

由全機率定理可得

$$
\begin{aligned}
\mathbb{P}(W)
&=\mathbb{P}(W\mid C)\,\mathbb{P}(C)
+\mathbb{P}(W\mid G)\,\mathbb{P}(G)\\[0.45em]
&=0\cdot\frac{1}{3}+1\cdot\frac{2}{3}=\frac{2}{3}
\end{aligned}
$$

所以切換策略的勝率為 $2/3$。
</div>

這個例子的關鍵不是主持人「改變」了車的位置，而是「一開始選對」與「一開始選錯」這兩種情況形成一組分割；全機率定理把兩種情況下切換策略的貢獻分別算出來，再加總成總勝率。

這個問題之所以經典，正是因為它很容易騙過直覺。主持人打開一扇羊門後，眼前只剩兩扇未開的門，許多人會自然地想：既然只剩兩個選項，機率應該各半。但這個想法忽略了主持人的行動不是隨機揭露，而是帶著資訊的篩選。據說連數學家艾迪胥 (Paul Erdős) 也曾一度不接受切換策略較好的結論，直到看見電腦模擬後才被說服。若想把這個 $2/3$ 看成長期相對頻率，也可以到 Demos 中的<a class="text-nowrap" href="/demos/monty-hall/">蒙提霍爾問題實作</a>親自操作：改變策略、增加模擬次數，觀察切換策略的勝率如何逐漸穩定在理論值附近。

<div class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 1.5</div>

Monty Hall 問題還有一個等價外衣，稱為三囚徒問題 (three prisoners problem)。

想像有三位囚徒 $A,B,C$，其中一人將獲赦免，另外兩人會被處決。囚徒 $A$ 不知道誰會獲赦，於是請知道結果的守衛在 $B,C$ 之中，說出一位「確定不會獲赦」的人。守衛回答：「$B$ 不會獲赦。」

請先不要急著算。這時 $A$ 會不會像三門問題中的參賽者一樣，以為「剩下 $A$ 與 $C$，所以自己被赦免的機率變成 $1/2$」？若守衛的規則是：他必須避開 $A$，而且只能說出 $B,C$ 中不會獲赦的人；當 $B,C$ 都不會獲赦時，守衛用對稱方式選一位回答，那麼這個問題和 Monty Hall 的結構相同。

對應關係是：囚徒 $A$ 就像一開始選定的門，守衛說出的囚徒就像主持人打開的羊門，剩下的囚徒 $C$ 就像另一扇未開的門。守衛的回答不是隨便透露一個名字，而是在知道答案後刻意避開某些選項。因此，真正被重新分割的仍是「一開始 $A$ 是否就是獲赦者」這件事，而不是簡單地把兩個剩餘選項均分。
</div>

<div id="example-111" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 1.11 (Manufacturing Defects)</div>

三台機器 $M_1,M_2,M_3$ 製造同一種產品，分別負責總產量的 $20\%,30\%,50\%$；其產品不良率依序為 $5\%,4\%,2\%$。現在從全部產品中隨機抽出一件，問題是：抽到不良品的總機率是多少？

令 $D$ 表示抽到不良品之事件。由題意可知

$$
\mathbb{P}(M_1)=0.2,\quad
\mathbb{P}(M_2)=0.3,\quad
\mathbb{P}(M_3)=0.5
$$

另外，各機器之條件不良率為

$$
\mathbb{P}(D\mid M_1)=0.05,\quad
\mathbb{P}(D\mid M_2)=0.04,\quad
\mathbb{P}(D\mid M_3)=0.02
$$

因此由全機率定理可得

$$
\begin{aligned}
\mathbb{P}(D)
&=\mathbb{P}(D\mid M_1)\,\mathbb{P}(M_1)
+\mathbb{P}(D\mid M_2)\,\mathbb{P}(M_2)
+\mathbb{P}(D\mid M_3)\,\mathbb{P}(M_3)\\[0.45em]
&=0.05\times 0.2+0.04\times 0.3+0.02\times 0.5=0.032
\end{aligned}
$$

所以從全部產品中抽到不良品的機率為 $0.032$。
</div>

<div id="interlude-16-tree" class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 1.6</div>

如果把 Example 1.11 畫成一張橫向樹狀圖，第一層先問「產品來自哪台機器」，第二層才問「它是否為不良品」。三台機器各自分成 $D$ 與 $D^{\prime}$，因此總共有六條路徑。

<figure class="topic-figure topic-figure--medium">
  <img src="/images/teaching-topics/total-probability-tree-defects.svg" alt="三台機器各自分成不良品 D 與非不良品 D prime 的橫向樹狀圖，其中通往 D 的三條路徑以紅色標示。">
  <figcaption><span class="topic-figure__label">Fig. 1.8.</span> 三個來源各自再分成 $D$ 與 $D^{\prime}$，共形成六條路徑；紅框中的三個 $D$ 對應到「有 $D$ 的路徑」。</figcaption>
</figure>

沿著某一條路徑前進時，先乘上走到該來源的機率，再乘上該來源產生 $D$ 的條件機率。例如，走到 $M_1$ 再看到 $D$ 的路徑機率是 $\mathbb{P}(M_1)\,\mathbb{P}(D\mid M_1)$。全機率定理做的事，就是把紅色這三條路徑加起來：這就是有 $D$ 的那三個路徑。
</div>

## 本篇小結

本文的主軸是分割與全機率定理：

| 工具 | 公式 | 核心想法 |
| --- | --- | --- |
| 分割 | $A_i\cap A_j=\varnothing,\ \bigcup_i A_i=S$ | 分類且不重複、不遺漏 |
| 全機率定理 | $\mathbb{P}(B)=\sum_i\mathbb{P}(B\mid A_i)\,\mathbb{P}(A_i)$ | 加總各來源對 $B$ 的貢獻 |

全機率定理回答的是「$B$ 總共多容易發生」。一旦這個總機率被算出來，我們就可以進一步反問：既然 $B$ 已經發生，它最可能是由哪個來源造成？這個反向問題會自然導向貝氏定理。
