---
title: "條件分配"
subtitle: "Conditional Distributions"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 7
order: 307
permalink: /lecture-notes/conditional-distributions/
date: 2026-08-12
published: false
excerpt: "把隨機向量中的一個或多個隨機變數固定成常數之後，所得到的機率分配即為條件機率分配。二元離散型的條件機率質量函數，定義為聯合機率質量函數除以邊際機率質量函數，它本身仍是一種機率質量函數，也仍然是機率，而且是樣本空間縮小到 $Y=y$ 已經發生的狀況之後，再看 $X=x$ 發生的條件機率。二元連續型的條件機率密度函數同樣是聯合機率密度函數除以邊際機率密度函數，只是它與單變數的機率密度函數一樣不是機率。由圖形來看，固定住 $Y=1.5$ 等於在聯合機率密度函數的曲面上切下一個截面，這個截面還要除以該處本身的邊際機率密度，才會被拉高或降低成一個真正的機率密度函數。"
---

[上一篇](/lecture-notes/marginal-cumulative-distribution-functions/)補上了[邊際累積分配函數](/lecture-notes/marginal-cumulative-distribution-functions/#def-marginal-cdf)，把聯合與邊際的各個機率函數與分配函數之間的關係補齊。本篇把[隨機向量](/lecture-notes/random-vectors-joint-pmf/#def-random-vector)中的一個或多個變數固定成常數，介紹此時的機率分配，並分別給出離散型與連續型的定義。

有些時候，我們常常把隨機向量中的其中幾個變數當成常數，再來協助計算所求機率。我們並不是真的要把該變數當成常數，只是為了方便計算暫且為之。

但是，若真的把其中的一個或多個[隨機變數](/lecture-notes/random-variables-and-pmf/#def-random-variable)「固定成常數」的話，這時候的機率分配會變成**條件機率分配 <span lang="en">(conditional probability distribution)</span>**，以下詳述。

<div id="def-conditional-pmf" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 3.8 (條件機率質量函數, conditional pmf)</div>

令 $(X,Y)$ 為二元**離散型**隨機變數，其 joint pmf 為 <span class="text-nowrap">$p_{\sssig XY}(x,y)$。</span>

若 $Y$ 的 marginal pmf 為 <span class="text-nowrap">$p_{\sssig Y}(y)$，</span>則

$$
p_{\sssig X\mid Y}(x\mid y)=\frac{\,p_{\sssig XY}(x,y)\,}{p_{\sssig Y}(y)}
$$

為 **$X$ 給定 $Y=y$ 下的條件[機率質量函數](/lecture-notes/random-variables-and-pmf/#def-pmf) <span lang="en">(conditional pmf of $X$ given $Y=y$)</span>**。

若 $X$ 的 marginal pmf 為 <span class="text-nowrap">$p_{\sssig X}(x)$，</span>則

$$
p_{\sssig Y\mid X}(y\mid x)=\frac{\,p_{\sssig XY}(x,y)\,}{p_{\sssig X}(x)}
$$

為 **$Y$ 給定 $X=x$ 下的條件機率質量函數 <span lang="en">(conditional pmf of $Y$ given $X=x$)</span>**。

</div>

條件機率質量函數有一些地方需要注意:

(1) conditional pmf 仍然是一種 pmf，並且這種 pmf 只有 $X$ (或 $Y$) 作為隨機變數，$Y=y$ (或 $X=x$) 則視為常數。事實上，**條件分配仍然是一種機率分配**。
{: .topic-paren-item}

(2) conditional pmf 是第一章所談到的[條件機率](/lecture-notes/conditional-probability-information/#definition-conditional-probability)，推廣至離散隨機變數的版本，其直觀意義也是相同的，即**樣本空間縮小至 $Y=y$ (或 $X=x$) 已經發生的狀況下，再來探討此時 $X=x$ (或 $Y=y$) 發生的條件機率**。
{: .topic-paren-item}

(3) 由於 conditional pmf 仍然是一種 pmf，故與 pmf 相同，**conditional pmf 本身就是機率**，而且這種機率**是一種條件機率**。我們可以由這個性質將[上述定義](#def-conditional-pmf)改寫為
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
p_{\sssig Y\mid X}(y\mid x)=\mathbb{P}(Y=y\mid X=x)=\frac{\,\mathbb{P}(X=x,Y=y)\,}{\mathbb{P}(X=x)}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig Y\mid X}(y\mid x)&=\mathbb{P}(Y=y\mid X=x)\\[0.45em]
&=\frac{\,\mathbb{P}(X=x,Y=y)\,}{\mathbb{P}(X=x)}
\end{aligned}
$$

</div>

(4) 當然，由於 conditional pmf 仍是一種 pmf，故具有以下三個性質:
{: .topic-paren-item}

$$
\begin{gathered}
0\leqslant p_{\sssig X\mid Y}(x\mid y)\leqslant 1,\ \forall x\in\mathcal{R}_{\sssig X}\\[0.5em]
\mathbb{P}\bigl(X\in\mathcal{R}_{\sssig X}\bigr)=\sum_{x\in\mathcal{R}_{\sssig X}}p_{\sssig X\mid Y}(x\mid y)=1\\[0.5em]
\mathbb{P}\bigl(X\in A\bigr)=\sum_{x\in A}p_{\sssig X\mid Y}(x\mid y)
\end{gathered}
$$

特別注意的是，這裡的變數只有 $X$ (或 $Y$)，而 $Y=y$ (或 $X=x$) 則**已經是常數**了。
{: .topic-paren-cont}

<div id="def-conditional-pdf" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 3.9 (條件機率密度函數, conditional pdf)</div>

令 $(X,Y)$ 為二元**連續型**隨機變數，其 joint pdf 為 <span class="text-nowrap">$f_{\sssig XY}(x,y)$。</span>

若 $Y$ 的 marginal pdf 為 <span class="text-nowrap">$f_{\sssig Y}(y)$，</span>則

$$
f_{\sssig X\mid Y}(x\mid y)=\frac{\,f_{\sssig XY}(x,y)\,}{f_{\sssig Y}(y)}
$$

為 **$X$ 給定 $Y=y$ 下的條件[機率密度函數](/lecture-notes/probability-density-functions/#def-pdf) <span lang="en">(conditional pdf of $X$ given $Y=y$)</span>**。

若 $X$ 的 marginal pdf 為 <span class="text-nowrap">$f_{\sssig X}(x)$，</span>則

$$
f_{\sssig Y\mid X}(y\mid x)=\frac{\,f_{\sssig XY}(x,y)\,}{f_{\sssig X}(x)}
$$

為 **$Y$ 給定 $X=x$ 下的條件機率密度函數 <span lang="en">(conditional pdf of $Y$ given $X=x$)</span>**。

</div>

條件機率密度函數有一些地方需要注意:

(1) conditional pdf 仍然是一種 pdf，並且這種 pdf 只有 $X$ (或 $Y$) 作為隨機變數，$Y=y$ (或 $X=x$) 則視為常數。但是，由於 [pdf](/lecture-notes/probability-density-functions/#def-pdf) 本身並不是機率，故 **conditional pdf 本身亦不是機率**。
{: .topic-paren-item}

(2) 當然，由於 conditional pdf 仍是一種 pdf，故當然具有以下三個性質:
{: .topic-paren-item}

$$
\begin{gathered}
f_{\sssig X\mid Y}(x\mid y)\geqslant 0,\ \forall x\in\mathcal{R}_{\sssig X}\\[0.5em]
\mathbb{P}\bigl(X\in\mathcal{R}_{\sssig X}\bigr)=\int_{x\in\mathcal{R}_{\sssig X}}f_{\sssig X\mid Y}(x\mid y)\,dx=1\\[0.5em]
\mathbb{P}\bigl(X\in A\bigr)=\int_{x\in A}f_{\sssig X\mid Y}(x\mid y)\,dx
\end{gathered}
$$

特別注意的是，這裡的變數只有 $X$ (或 $Y$)，而 $Y=y$ (或 $X=x$) 則**已經是常數**了。
{: .topic-paren-cont}

(3) conditional pmf 可以解釋為 $Y=y$ 已經發生的事件中，$X=x$ 的條件機率，這一點在 conditional pdf 上將轉為固定在 $Y=y$ 之下來探討 $X$ 的**機率密度**，如下所示:
{: .topic-paren-item}

<figure id="fig-conditional-density-slice" class="topic-figure topic-figure--wide">
  <img src="/images/lecture-notes/conditional-density-slice.svg" alt="一個三維曲面圖。曲面在中央隆起成鐘形，四周向外遞減趨近於零，底面兩軸分別標 x 與 y，鉛直軸標聯合機率密度函數的函數值。y 軸上只標出 1.5 這一個位置，該處有一片沿 x 方向的截面立在曲面上，截面的輪廓以深色曲線描出，其下以淡紅色填滿，形成一片薄片。底面的兩軸與鉛直軸都沒有其他刻度。">
  <figcaption><span class="topic-figure__label">Fig. 3.11.</span> joint pdf 的曲面在 $Y=1.5$ 處切一刀，所得的截面就是圖中填色的那一片薄片。樣本空間縮小到這一片之上，再討論 $X$ 的機率密度，即 conditional pdf。</figcaption>
</figure>

上方圖例中灰色部分，代表 $Y=1.5$ 的空間，而將樣本空間縮小到這個空間上來探討 $X$ 的機率分配，即為 conditional pdf。

但是，上圖所顯示的，其實只是 <span class="text-nowrap">$f_{\sssig XY}(x,1.5)$，</span>而不是真正的 pdf，因為真正的 pdf 需要滿足許多條件，而上述範圍未必恰巧滿足；將 $f_{\sssig XY}(x,1.5)$ 轉為一個真正的 pdf 的做法，就是將其所處的空間 (也就是 $Y=1.5$) 本身的邊際機率密度給除掉，將這個未完成品「拉高」(或降低) 至該有的高度，如下所示:

<figure id="fig-conditional-density-normalize" class="topic-figure topic-figure--wide">
  <img src="/images/lecture-notes/conditional-density-normalize.svg" alt="同一條橫軸上畫著兩條形狀完全相同的鐘形曲線，峰頂落在同一個位置，一條高、一條低，兩端都貼近橫軸。較低的一條曲線之下到橫軸之間整塊以淡紅色填滿，一條細引線由這條曲線的右側往右上方拉出，末端標 f_XY(x, 1.5)；較高的一條曲線不填色，另一條細引線由它的左側往左上方拉出，末端標 f_X|Y(x|1.5)。橫軸右端有箭頭並標 x，圖中沒有鉛直軸，兩軸都沒有刻度。">
  <figcaption><span class="topic-figure__label">Fig. 3.12.</span> 兩條曲線的形狀完全相同，只差在高度。較低的一條是 joint pdf 在 $Y=1.5$ 處的切面 <span class="text-nowrap">$f_{\sssig XY}(x,1.5)$，</span>把它除以該處的邊際機率密度才拉高為 <span class="text-nowrap">$f_{\sssig X\mid Y}(x\mid 1.5)$，</span>成為一個合法的 pdf。</figcaption>
</figure>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

細心一點的讀者或許會發現，這個未完成品的 <span class="text-nowrap">$f_{\sssig XY}(x,1.5)$，</span>其機率密度的「分配模式」已經與真正的 conditional pdf 一樣了，只差在調整成一個合理的 pdf 而已。

事實上，這個發現也是相當合理的，因為 $(X,Y)$ 再怎麼變化，也還是要依循其 joint pdf 變化，條件分配做的事情只是「固定住」其中一個變數而已，故從聯合分配的角度而言，此時的變動情況就被「鎖定」在其 joint pdf 的某一個薄薄的切片上，因此其「分配模式」與真正的條件分配相同，是完全符合直觀的。

</div>

## 本篇小結

[Definition 3.8](#def-conditional-pmf) 把條件機率推廣到二元離散型的情形。給定 $Y=y$ 之下 $X$ 的條件機率質量函數，是[聯合機率質量函數](/lecture-notes/random-vectors-joint-pmf/#def-joint-pmf)除以 $Y$ 的[邊際機率質量函數](/lecture-notes/random-vectors-joint-pmf/#def-marginal-pmf)，給定 $X=x$ 之下 $Y$ 的條件機率質量函數亦同。這種 pmf 只有 $X$ 是隨機變數，$Y=y$ 則視為常數；它本身就是機率，而且就是第一章的條件機率推廣到離散隨機變數的版本，也就是把樣本空間縮小到 $Y=y$ 已經發生的狀況下，再看 $X=x$ 發生的機率。既然它仍是一種 pmf，也就同樣具有介於 $0$ 與 $1$ 之間、在值域上加總為 <span class="text-nowrap">$1$，</span>以及一個事件的機率為該事件上之加總這三個性質。

[Definition 3.9](#def-conditional-pdf) 以完全相同的形式給出二元連續型的情形。條件機率密度函數就是[聯合機率密度函數](/lecture-notes/joint-probability-density-functions/#def-joint-pdf)除以另一個變數的[邊際機率密度函數](/lecture-notes/marginal-probability-density-functions/#def-marginal-pdf)。差別在於 pdf 本身並不是機率，故 conditional pdf 也不是機率，但它同樣具有非負、在值域上積分為 <span class="text-nowrap">$1$，</span>以及一個事件的機率為該事件上之積分這三個性質。

由圖形來看，固定 $Y=1.5$ 等於在 joint pdf 的曲面上切下一個截面，本篇的第一張圖畫的就是這片切面。但這片切面所給的只是 $f_{\sssig XY}(x,1.5)$ 這個式子，它未必恰巧滿足一個 pdf 該有的條件，還要除以 $Y=1.5$ 這個空間本身的邊際機率密度，才會被拉高或降低到該有的高度；第二張圖把調整前後的兩條曲線畫在一起，兩者的形狀完全相同，差別只在高度。

[下一篇](/lecture-notes/conditional-distributions-examples/)以五道例題練習條件機率質量函數與條件機率密度函數的求法，並由其中一題引出截尾分配。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
