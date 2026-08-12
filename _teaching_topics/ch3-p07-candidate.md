---
title: "條件分配"
subtitle: "Conditional Distributions"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 7
order: 307
permalink: /teaching-topics/ch3-p07-candidate/
date: 2026-08-12
published: false
excerpt: "把隨機向量中的一個或多個隨機變數固定成常數之後，所得到的機率分配即為條件機率分配。二元離散型的條件機率質量函數，定義為聯合機率質量函數除以邊際機率質量函數，它本身仍是一種機率質量函數，也仍然是機率，而且是樣本空間縮小到 $Y=y$ 已經發生的狀況之後，再看 $X=x$ 發生的條件機率。二元連續型的條件機率密度函數同樣是聯合機率密度函數除以邊際機率密度函數，只是它與單變數的機率密度函數一樣不是機率。由圖形來看，固定住 $Y=1.5$ 等於在聯合機率密度函數的曲面上切下一個截面，這個截面還要除以該處本身的邊際機率密度，才會被拉高或降低成一個真正的機率密度函數。"
---

[上一篇](/teaching-topics/ch3-p06-candidate/)補上了[邊際累積分配函數](/teaching-topics/ch3-p06-candidate/#def-marginal-cdf)，把聯合與邊際的各個機率函數與分配函數之間的關係補齊。本篇把隨機向量中的一個或多個變數固定成常數，介紹此時的機率分配，並分別給出離散型與連續型的定義。

有些時候，我們常常把隨機向量中的其中幾個變數當成常數，再來協助計算所求機率。我們並不是真的要把該變數當成常數，只是為了方便計算暫且為之。

但是，若真的把其中的一個或多個隨機變數「固定成常數」的話，這時候的機率分配會變成**條件機率分配 <span lang="en">(conditional probability distribution)</span>**，以下詳述。

<div id="def-conditional-pmf" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 3.8 (條件機率質量函數, conditional pmf)</div>

令 $(X,Y)$ 為二元**離散型**隨機變數，其 joint pmf 為 <span class="text-nowrap">$p_{\sssig XY}(x,y)$。</span>

若 $Y$ 的 marginal pmf 為 <span class="text-nowrap">$p_{\sssig Y}(y)$，</span>則

$$
p_{\sssig X\mid Y}(x\mid y)=\frac{\,p_{\sssig XY}(x,y)\,}{p_{\sssig Y}(y)}
$$

為 **$X$ 給定 $Y=y$ 下的條件機率質量函數 <span lang="en">(conditional pmf of $X$ given $Y=y$)</span>**。

若 $X$ 的 marginal pmf 為 <span class="text-nowrap">$p_{\sssig X}(x)$，</span>則

$$
p_{\sssig Y\mid X}(y\mid x)=\frac{\,p_{\sssig XY}(x,y)\,}{p_{\sssig X}(x)}
$$

為 **$Y$ 給定 $X=x$ 下的條件機率質量函數 <span lang="en">(conditional pmf of $Y$ given $X=x$)</span>**。

</div>

條件機率質量函數有一些地方需要注意:

(1) conditional pmf 仍然是一種 pmf，並且這種 pmf 只有 $X$ (或 $Y$) 作為隨機變數，$Y=y$ (或 $X=x$) 則視為常數。事實上，**條件分配仍然是一種機率分配**。
{: .topic-paren-item}

(2) conditional pmf 是第一章所談到的[條件機率](/teaching-topics/conditional-probability-information/#definition-conditional-probability)，推廣至離散隨機變數的版本，其直觀意義也是相同的，即**樣本空間縮小至 $Y=y$ (或 $X=x$) 已經發生的狀況下，再來探討此時 $X=x$ (或 $Y=y$) 發生的條件機率**。
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

為 **$X$ 給定 $Y=y$ 下的條件機率密度函數 <span lang="en">(conditional pdf of $X$ given $Y=y$)</span>**。

若 $X$ 的 marginal pdf 為 <span class="text-nowrap">$f_{\sssig X}(x)$，</span>則

$$
f_{\sssig Y\mid X}(y\mid x)=\frac{\,f_{\sssig XY}(x,y)\,}{f_{\sssig X}(x)}
$$

為 **$Y$ 給定 $X=x$ 下的條件機率密度函數 <span lang="en">(conditional pdf of $Y$ given $X=x$)</span>**。

</div>

條件機率密度函數有一些地方需要注意:

(1) conditional pdf 仍然是一種 pdf，並且這種 pdf 只有 $X$ (或 $Y$) 作為隨機變數，$Y=y$ (或 $X=x$) 則視為常數。但是，由於 [pdf](/teaching-topics/ch2-p03-candidate/#def-pdf) 本身並不是機率，故 **conditional pdf 本身亦不是機率**。
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

<!-- fig-pending: conditional-density-slice
     Fig. 3.11，對應書稿 mathstatch3.tex 第 1287 至 1339 行的 tikzpicture (單面板)。
     以 pgfplots 畫的三維曲面圖，view={50}{45}，width=11cm，
     domain=0:4、y domain=0:4、samples=50，座標軸線本身不畫 (axis line style={draw=none})。
     曲面為書稿自定的 bivar 函數，取 $\mu_1=\mu_2=2$、$\sigma_1=\sigma_2=1$ 之後為
     $\frac{1}{2\pi}\exp\bigl(-((x-2)^2+(y-2)^2)\bigr)\big/2$，是一個中央隆起的鐘形曲面。
     請照書稿這條式子畫，不要代換成標準的二元常態密度: 它的指數部分沒有慣見的
     $\frac{1}{2}$，整體另外再除以 2。書稿的 colormap 名為 whitegray，兩端都是白色，
     也就是曲面不上色，只留網格線；網頁依 CH3_FIGURE_SPECS.md 第 3.2 節改用
     colormap={journalgray}{color(0cm)=(white); color(1cm)=(journalink)}，與其他圖的主線色相稱。
     三軸標示: 兩個水平方向的軸分別標 $x$ 與 $y$，鉛直軸標 $f_{\sssig XY}(x,y)$
     (書稿把 zlabel 轉 -90 度、anchor=west)。$x$ 軸與鉛直軸都不畫刻度
     (xtick=\empty、ztick=\empty)，$y$ 軸只有一個刻度，位置在 1.5，標示文字為 1.5。
     切面: 在 $y=1.5$ 處，把 $(x,\,1.5,\,f_{\sssig XY}(x,1.5))$ 這條曲線之下填滿
     (書稿用 fill=gray、opacity=0.4)，並另以較粗的黑線 (thick、opacity=0.6) 描出該曲線本身。
     這片切面就是正文所說的「灰色部分」，網頁改依 CH3_FIGURE_SPECS.md 第一節的配色，
     填色用 journalaccent、透明度 0.15，切面曲線用 journalink (曲面網格的顏色由上述 colormap 決定)。
     格式依 CH3_FIGURE_SPECS.md 第 3.2 節〔作者裁定 2026-08-13〕: 三維曲面也交 SVG，
     取樣數 samples=40，以 latex 產生 DVI 之後交 dvisvgm -O -d2 -n 轉檔 (原始檔不必改寫)。
     原訂的 PNG 作法已作廢，Fig. 3.2 與 3.3 的既有 PNG 亦待重製為 SVG。
     檔名 conditional-density-slice.svg，anchor 取 #fig-conditional-density-slice。
     另注意本站自訂的字級門檻是 350 px 之下最小可見字 11 px，Fig. 3.2 與 3.3 因
     \sssig 下標而只有 7.7 px 與 5.4 px，本圖畫的時候要先把這一點處理好再交件。
     站上另有一個同名的舊 SVG，屬 CH3_FIGURE_SPECS.md 第四節所列的四張作廢圖之一
     (手寫、無原始檔)，不得沿用，也不要覆寫，它隨作廢草稿留在原地。
     圖畫好之後，下一段的「上方圖例中灰色部分」與本篇小結第三段的「本篇的第一張圖」
     一併改為指向該 anchor 的 Fig. 3.11 連結。
-->

上方圖例中灰色部分，代表 $Y=1.5$ 的空間，而將樣本空間縮小到這個空間上來探討 $X$ 的機率分配，即為 conditional pdf。

但是，上圖所顯示的，其實只是 <span class="text-nowrap">$f_{\sssig XY}(x,1.5)$，</span>而不是真正的 pdf，因為真正的 pdf 需要滿足許多條件，而上述範圍未必恰巧滿足；將 $f_{\sssig XY}(x,1.5)$ 轉為一個真正的 pdf 的做法，就是將其所處的空間 (也就是 $Y=1.5$) 本身的邊際機率密度給除掉，將這個未完成品「拉高」(或降低) 至該有的高度，如下所示:

<!-- fig-pending: conditional-density-normalize
     Fig. 3.12，對應書稿 mathstatch3.tex 第 1349 至 1392 行的 tikzpicture (單面板)。
     純 TikZ 圖，不是 pgfplots。只有一條橫軸: 由原點以箭頭畫到 (8.2, 0)，
     在 (8.5, 0.15) 的下方標 $x$；沒有鉛直軸，兩軸都沒有刻度與數值。
     兩條峰頂同在 $x=4$、形狀相同的鐘形曲線，定義域 0 至 8 (samples=200):
     較低的一條是 $3e^{-(x-4)^2/3}$，峰高 3，其下方以 gray、opacity 0.2 填滿，
     代表尚未調整的 $f_{\sssig XY}(x,1.5)$；較高的一條是 $4.5e^{-(x-4)^2/3}$，峰高 4.5，
     不填色，代表已調整的 $f_{\sssig X\mid Y}(x\mid 1.5)$。兩條曲線的高度比恰為 1.5 比 1，
     這個比值就是正文所說的「除以邊際機率密度」之後被「拉高」的倍數。
     兩條引線: 由較高曲線上 $x=2.8$ 的點往左上方拉一條直線 (終點在該點左 1、上 1 之處)，
     線的左端標 $f_{\sssig X\mid Y}(x\mid 1.5)$；由較低曲線上 $x=6$ 的點往右上方拉一條直線
     (終點在該點右 1、上 1 之處)，線的右端標 $f_{\sssig XY}(x,1.5)$。
     網頁改依 CH3_FIGURE_SPECS.md 第一節的配色，曲線用 journalink、填色用 journalaccent
     並取 0.15 的透明度，兩條引線用 journalmuted。
     檔名 conditional-density-normalize.svg，anchor 取 #fig-conditional-density-normalize。
     圖畫好之後，上一段的「如下所示」與本篇小結第三段的「第二張圖」
     一併改為指向該 anchor 的 Fig. 3.12 連結。
-->

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

細心一點的讀者或許會發現，這個未完成品的 <span class="text-nowrap">$f_{\sssig XY}(x,1.5)$，</span>其機率密度的「分配模式」已經與真正的 conditional pdf 一樣了，只差在調整成一個合理的 pdf 而已。

事實上，這個發現也是相當合理的，因為 $(X,Y)$ 再怎麼變化，也還是要依循其 joint pdf 變化，條件分配做的事情只是「固定住」其中一個變數而已，故從聯合分配的角度而言，此時的變動情況就被「鎖定」在其 joint pdf 的某一個薄薄的切片上，因此其「分配模式」與真正的條件分配相同，是完全符合直觀的。

</div>

## 本篇小結

[Definition 3.8](#def-conditional-pmf) 把條件機率推廣到二元離散型的情形: 給定 $Y=y$ 之下 $X$ 的條件機率質量函數，是[聯合機率質量函數](/teaching-topics/ch3-p01-candidate/#def-joint-pmf)除以 $Y$ 的[邊際機率質量函數](/teaching-topics/ch3-p01-candidate/#def-marginal-pmf)，給定 $X=x$ 之下 $Y$ 的條件機率質量函數亦同。這種 pmf 只有 $X$ 是隨機變數，$Y=y$ 則視為常數；它本身就是機率，而且就是第一章的條件機率推廣到離散隨機變數的版本，也就是把樣本空間縮小到 $Y=y$ 已經發生的狀況下，再看 $X=x$ 發生的機率。既然它仍是一種 pmf，也就同樣具有介於 $0$ 與 $1$ 之間、在值域上加總為 <span class="text-nowrap">$1$，</span>以及一個事件的機率為該事件上之加總這三個性質。

[Definition 3.9](#def-conditional-pdf) 以完全相同的形式給出二元連續型的情形: [聯合機率密度函數](/teaching-topics/ch3-p03-candidate/#def-joint-pdf)除以另一個變數的[邊際機率密度函數](/teaching-topics/ch3-p04-candidate/#def-marginal-pdf)。差別在於 pdf 本身並不是機率，故 conditional pdf 也不是機率，但它同樣具有非負、在值域上積分為 <span class="text-nowrap">$1$，</span>以及一個事件的機率為該事件上之積分這三個性質。

由圖形來看，固定 $Y=1.5$ 等於在 joint pdf 的曲面上切下一個截面，本篇的第一張圖畫的就是這片切面。但這片切面所給的只是 $f_{\sssig XY}(x,1.5)$ 這個式子，它未必恰巧滿足一個 pdf 該有的條件，還要除以 $Y=1.5$ 這個空間本身的邊際機率密度，才會被拉高或降低到該有的高度；第二張圖把調整前後的兩條曲線畫在一起，兩者的形狀完全相同，差別只在高度。

[下一篇](/teaching-topics/ch3-p08-candidate/)以五道例題練習條件機率質量函數與條件機率密度函數的求法，並由其中一題引出截尾分配。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
