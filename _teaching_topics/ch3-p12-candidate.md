---
title: "雙重期望值定理"
subtitle: "The Double Expectation Theorem"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 12
order: 312
permalink: /teaching-topics/ch3-p12-candidate/
date: 2026-08-13
published: false
excerpt: "條件期望值算完之後，被給定的那個值會留下來，因此條件期望值是條件的函數，這個函數即稱為迴歸函數。若把條件本身看成隨機的，$\\mathbb{E}(X\\mid Y)$ 便是 $Y$ 的函數，也就是一個隨機變數，我們因而可以再取一次期望值；雙重期望值定理指出，這一次期望值恰好等於 $X$ 的邊際期望值 $\\mathbb{E}(X)$。它背後的直觀是加權平均: 先把 $X$ 的分配依 $Y$ 的取值切成一片一片的條件分配，在每一片上找到重心，再以 $f_{\\sssig Y}(y)$ 為權重把這些重心平均起來，所得的就是原始空間中的重心。本篇並把這條定理推廣到 $g(X)$ 的版本。"
---

[上一篇](/teaching-topics/ch3-p11-candidate/)以 [Definition 3.11](/teaching-topics/ch3-p11-candidate/#def-conditional-expectation) 與 [Definition 3.13](/teaching-topics/ch3-p11-candidate/#def-conditional-variance) 給出條件期望值與條件變異數，並在最後指出條件期望值是「給定的條件」的函數。

本篇先列出把條件當成常數所得到的三個特例，再以 [Theorem 3.8](#thm-regression-function) 為「條件期望值是條件的函數」中的那個函數取名為迴歸函數，接著討論條件本身是隨機的情形，並由此得到 [Theorem 3.9](#thm-double-expectation) 的雙重期望值定理，最後以一張立體圖說明這條定理背後的加權平均。

在[上一篇](/teaching-topics/ch3-p11-candidate/)我們曾經提過一個特別的觀點，即一旦給定了某個變數 $Y=y$ (或 $X=x$) 後，在這個條件期望值之中，$Y=y$ (或 $X=x$) 即**被視為常數**。我們在此詳細探討這個觀點。

讀者可以回想一下，我們在[初次介紹期望值](/teaching-topics/ch2-p06-candidate/#def-expectation)的時候曾說過，期望值對常數的運算結果就是該常數本身，及變異數對常數的運算結果必定為 $0$ (因為常數沒有變異性)，故我們馬上可以得到以下幾個有用的特例:

- $\mathbb{E}(X\mid X=x)$ $=$ $\mathbb{E}(x\mid X=x)$ $=$ $x\mathbb{E}(1\mid X=x)$ $=$ $x$
- $\mathrm{Var}(X\mid X=x)$ $=$ $\mathrm{Var}(x\mid X=x)$ $=$ $0$
- $\mathbb{E}(XY\mid X=x)$ $=$ $\mathbb{E}(xY\mid X=x)$ $=$ $x\mathbb{E}(Y\mid X=x)$

上述三個特例各有其重要的地方，但我們只需要想著「把 $X$ 當成常數」則這一切都會變得很簡單。這種條件期望值除了是條件的函數以外，我們對其有特別的稱呼。

## 迴歸函數

<div id="thm-regression-function" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 3.8 (迴歸函數, regression function)</div>

條件期望值是條件的函數，即 $\mathbb{E}(X\mid Y=y)$ $=$ $g(y)$ (或 $\mathbb{E}(Y\mid X=x)$ $=$ <span class="text-nowrap">$g(x)$)，</span>我們稱其為 $X$ 對 $Y$ (或 $Y$ 對 $X$) 的迴歸函數 <span lang="en">(regression function of $X$ on $Y$ ($Y$ on $X$))</span>。

</div>

<div class="topic-proof" markdown="1">
**Proof.**

我們僅以連續型證明第一個情況，第二個情況與離散型同理可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X\mid Y=y)&=\int_{x\in\mathcal{R}_{\sssig X}}x\,f_{\sssig X\mid Y}(x\mid y)\,dx=\int_{x\in\mathcal{R}_{\sssig X}}x\frac{f_{\sssig XY}(x,y)}{f_{\sssig Y}(y)}\,dx\\[0.45em]
&=\frac{1}{f_{\sssig Y}(y)}\int_{x\in\mathcal{R}_{\sssig X}}x\,f_{\sssig XY}(x,y)\,dx=g(y)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}(X\mid Y=y)=\int_{x\in\mathcal{R}_{\sssig X}}x\,f_{\sssig X\mid Y}(x\mid y)\,dx\\[0.45em]
&\quad =\int_{x\in\mathcal{R}_{\sssig X}}x\frac{f_{\sssig XY}(x,y)}{f_{\sssig Y}(y)}\,dx\\[0.45em]
&\quad =\frac{1}{f_{\sssig Y}(y)}\int_{x\in\mathcal{R}_{\sssig X}}x\,f_{\sssig XY}(x,y)\,dx=g(y)
\end{aligned}
$$

</div>

其中 $g(y)$ 是 $y$ 的函數。

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

上述定理指出，如果我們正在處理 $X$ 給定 $Y=y$ 的條件期望值，則我們可以將這個條件期望值的結果，與其條件 $y$ 的值產生連結，也就是透過決定一個 $y$ 的值，而直接知道 $X$ 的條件期望值。

</div>

很多時候，我們會看到 $\mathbb{E}(X\mid Y)$ 的設定，這與前面我們所熟知的條件期望值，最大的差異是**條件是隨機的**，這句話的意思是，在期望值的內部，$Y$ 雖然還是常數沒錯，但在期望值的外側時，我們卻**不知道 $Y$ 是哪一個常數**。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這導致**當 $Y$ 被提出期望值的外面後，$Y$ 仍然具有隨機性** (也就是 $Y$ 仍需保持大寫)。

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這個差異即是 $g(y)$ 與 $g(Y)$ 的差異，前者只是數字，後者卻是隨機變數。

</div>

## 雙重期望值定理

如果考慮條件是隨機的情況，[Theorem 3.8](#thm-regression-function) 將變成具有隨機性的版本，即 $\mathbb{E}(X\mid Y)$ $=$ $g(Y)$ 的形式，這樣一來，我們便會發現 $X$ 給定 $Y$ 的條件期望值竟然是 $Y$ 的函數 (亦是一個隨機變數)，而且當 $Y$ 的值產生變化，$\mathbb{E}(X\mid Y)$ $=$ $g(Y)$ 的值亦會隨之變動。

若有此結果，我們便可以再接續探討 $\mathbb{E}(X\mid Y)$ $=$ $g(Y)$ 的期望值，也就是 <span class="text-nowrap">$\mathbb{E}\bigl[\mathbb{E}(X\mid Y)\bigr]$，</span>此即相當重要且知名的**雙重期望值定理 <span lang="en">(double expectation theorem)</span>**。

<div id="thm-double-expectation" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 3.9 (雙重期望值定理, double expectation theorem)</div>

若 $\mathbb{E}(X\mid Y)$ 為 $X$ 對 $Y$ 之條件期望值，且 $\mathbb{E}(X)$ 存在，則

$$
\mathbb{E}\bigl[\mathbb{E}(X\mid Y)\bigr]=\mathbb{E}(X)
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.**

我們以連續型證明如下，離散型同理即可

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl[\mathbb{E}(X\mid Y)\bigr]&=\int_{y\in\mathcal{R}_{\sssig Y}}\mathbb{E}(X\mid Y=y)\,f_{\sssig Y}(y)\,dy\\[0.45em]
&=\int_{y\in\mathcal{R}_{\sssig Y}}\biggl[\int_{x\in\mathcal{R}_{\sssig X}}x\,f_{\sssig X\mid Y}(x\mid y)\,dx\biggr]\,f_{\sssig Y}(y)\,dy\\[0.45em]
&=\int_{y\in\mathcal{R}_{\sssig Y}}\biggl[\int_{x\in\mathcal{R}_{\sssig X}}x\,\frac{f_{\sssig XY}(x,y)}{f_{\sssig Y}(y)}\,dx\biggr]\,f_{\sssig Y}(y)\,dy\\[0.45em]
&=\int_{y\in\mathcal{R}_{\sssig Y}}\int_{x\in\mathcal{R}_{\sssig X}}x\,\frac{f_{\sssig XY}(x,y)}{f_{\sssig Y}(y)}f_{\sssig Y}(y)\,dx\,dy\\[0.45em]
&=\int_{y\in\mathcal{R}_{\sssig Y}}\int_{x\in\mathcal{R}_{\sssig X}}x\,f_{\sssig XY}(x,y)\,dx\,dy=\mathbb{E}(X)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}\bigl[\mathbb{E}(X\mid Y)\bigr]\\[0.45em]
&\quad =\int_{y\in\mathcal{R}_{\sssig Y}}\mathbb{E}(X\mid Y=y)\,f_{\sssig Y}(y)\,dy\\[0.45em]
&\quad =\int_{y\in\mathcal{R}_{\sssig Y}}\biggl[\int_{x\in\mathcal{R}_{\sssig X}}x\,f_{\sssig X\mid Y}(x\mid y)\,dx\biggr]\\[0.2em]
&\qquad\quad f_{\sssig Y}(y)\,dy\\[0.45em]
&\quad =\int_{y\in\mathcal{R}_{\sssig Y}}\biggl[\int_{x\in\mathcal{R}_{\sssig X}}x\,\frac{f_{\sssig XY}(x,y)}{f_{\sssig Y}(y)}\,dx\biggr]\\[0.2em]
&\qquad\quad f_{\sssig Y}(y)\,dy\\[0.45em]
&\quad =\int_{y\in\mathcal{R}_{\sssig Y}}\int_{x\in\mathcal{R}_{\sssig X}}x\,\frac{f_{\sssig XY}(x,y)}{f_{\sssig Y}(y)}f_{\sssig Y}(y)\,dx\,dy\\[0.45em]
&\quad =\int_{y\in\mathcal{R}_{\sssig Y}}\int_{x\in\mathcal{R}_{\sssig X}}x\,f_{\sssig XY}(x,y)\,dx\,dy\\[0.45em]
&\quad =\mathbb{E}(X)
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

[雙重期望值定理](#thm-double-expectation)可以推廣到 $X$ 的函數條件期望值的版本，即

$$
\mathbb{E}\Bigl(\mathbb{E}\bigl[g(X)\mid Y\bigr]\Bigr)=\mathbb{E}\bigl[g(X)\bigr]
$$

這給我們很大的使用方便，例如:

$$
\mathbb{E}\Bigl[\mathbb{E}\bigl(X^{2}\mid Y\bigr)\Bigr]=\mathbb{E}\bigl(X^{2}\bigr)
$$

</div>

我們原先已經知道 $X$ 的條件期望值 $\mathbb{E}(X\mid Y)$ 是 $Y$ 的函數 <span class="text-nowrap">$g(Y)$，</span>若我們將這個 $Y$ 的函數轉換再取一個期望值，則[雙重期望值定理](#thm-double-expectation)指出，**這個期望值竟然等於 $X$ 的邊際期望值**。這是一個相當特別的定理，但卻不算太過意外，因為其背後的直觀即是「加權平均」。

在計算 $g(Y)$ 的期望值時我們知道，其算法是將 $g(Y)$ 乘上其機率函數 $f_{\sssig Y}(y)$ 再行積分，而我們亦知道這個直觀意義就是一種加權平均，其中的權重就是 <span class="text-nowrap">$f_{\sssig Y}(y)$。</span>

而在計算 $\mathbb{E}(X\mid Y)$ 的期望值時，由於 $\mathbb{E}(X\mid Y)$ 是 $Y$ 的函數轉換，故當然也要乘上 $Y$ 的機率函數以符合定義，這也是上列證明的小細節。然而，這個關鍵的小步驟即是看出為何[雙重期望值定理](#thm-double-expectation)是一種加權平均的關鍵，我們將其圖解如下:

<!-- fig-pending: regression-function-surface
     Fig. 3.16，對應書稿 mathstatch3.tex 第 2297 至 2348 行的 tikzpicture (單面板，不是多面板)。
     以 pgfplots 畫的三維曲面圖，view={50}{45}，width=11cm，enlargelimits=false，
     domain=0:4、y domain=0:4、samples=50，座標軸線本身不畫 (axis line style={draw=none})。
     曲面為書稿自定的 bivar 函數，取 $\mu_1=\mu_2=2$、$\sigma_1=\sigma_2=1$ 之後為
     $\frac{1}{2\pi}\exp\bigl(-((x-2)^2+(y-2)^2)\bigr)\big/2$，是一個中央隆起的鐘形曲面。
     請照書稿這條式子畫，不要代換成標準的二元常態密度: 它的指數部分沒有慣見的
     $\frac{1}{2}$，整體另外再除以 2。這與 Fig. 3.11 (conditional-density-slice) 用的是
     同一條 bivar 函數，兩張圖的曲面應完全一致，差別只在切片的張數與 $y$ 軸的刻度標示。
     書稿在圖前另下一道 \pgfplotsset，把 colormap 設為 whitegray (兩端都是白色)，
     也就是曲面不上色、只留網格線；網頁依 CH3_FIGURE_SPECS.md 第 3.2 節改用
     colormap={journalgray}{color(0cm)=(white); color(1cm)=(journalink)}，與其他圖的主線色相稱。
     三軸標示: 兩個水平方向的軸分別標 $x$ 與 $y$，鉛直軸標 $f_{\sssig XY}(x,y)$
     (書稿把 zlabel 轉 -90 度、anchor=west)。$x$ 軸與鉛直軸都不畫刻度
     (xtick=\empty、ztick=\empty)；$y$ 軸有三個刻度，位置依序在 0.7、1.5 與 3，
     標示文字依序為 $y_1$、$y_2$ 與 $y_n$ (注意第三個是 $y_n$，不是 $y_3$)。
     三片切面: 在 $y=0.7$、$y=1.5$ 與 $y=3$ 三處，各把 $(x,\,y,\,f_{\sssig XY}(x,y))$
     這條沿 $x$ 方向的曲線之下填滿 (書稿用 fill=gray、opacity=0.4)，並另以較粗的線
     (thick、opacity=0.6) 描出該曲線本身。這三片就是正文所說的薄片，每一片即
     $X$ 給定 $Y=y$ 的條件分配；網頁改依 CH3_FIGURE_SPECS.md 第一節的配色，
     填色用 journalaccent、透明度 0.15，切面曲線用 journalink
     (曲面網格的顏色由上述 colormap 決定)。三片的高低不同，正是加權平均中權重不同的來源。
     格式依 CH3_FIGURE_SPECS.md 第 3.2 節〔作者裁定 2026-08-13〕: 三維曲面也交 SVG，
     取樣數 samples=40，以 latex 產生 DVI 之後交 dvisvgm -O -d2 -n 轉檔 (原始檔不必改寫)。
     原訂的 PNG 作法已作廢，Fig. 3.2 與 3.3 的既有 PNG 亦待重製為 SVG。
     檔名 regression-function-surface.svg，anchor 取 #fig-regression-function-surface。
     另注意本站自訂的字級門檻是 350 px 之下最小可見字 11 px，Fig. 3.2 與 3.3 因
     \sssig 下標而只有 7.7 px 與 5.4 px，本圖畫的時候要先把這一點處理好再交件。
     圖畫好之後，下一段開頭的「上圖」與本篇小結第三段的「本篇的立體圖」
     一併改為指向該 anchor 的 Fig. 3.16 連結。
-->

上圖的意義在於，$X$ 的分配可以先透過給定不同的 <span class="text-nowrap">$Y$，</span>切割成不同的空間，這個切割出來的空間即為 $X$ 給定 $Y=y$ 的分配。

接著我們可以先在這個空間中，找到該空間上 $X$ 的重心 (即 <span class="text-nowrap">$\mathbb{E}(X\mid Y=y)$)，</span>而再回頭考慮從一開始被給定到 $Y=y$ 的空間的可能性 (即 <span class="text-nowrap">$f_{\sssig Y}(y)$)，</span>再將每個薄片的重心以 $f_{\sssig Y}(y)$ 為權重加權平均，從而得到原始空間中 (即 $X$ 自己的分配) $X$ 的重心所在 (即 <span class="text-nowrap">$\mathbb{E}(X)$)。</span>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

上述流程中最需要注意的核心觀念是，整個原始空間 (即 $X$ 的分配) 可以被 $Y$ 切割成不同的薄片，每個薄片都會形成一個機率分配，而我們是先在這些不同的條件分配上找到重心，並對這些重心進行加權平均，從而得到原始空間中的重心所在。

</div>

## 本篇小結

把條件當成常數，馬上可以得到三個有用的特例: $\mathbb{E}(X\mid X=x)$ $=$ $x$ 與 $\mathrm{Var}(X\mid X=x)$ $=$ $0$ 這兩條，說的是給定之後 $X$ 已經沒有隨機性；$\mathbb{E}(XY\mid X=x)$ $=$ $x\mathbb{E}(Y\mid X=x)$ 這一條，說的是給定的那個值可以像常數一樣提到期望值的外面。[Theorem 3.8](#thm-regression-function) 則為這個函數取了名字: 條件期望值是條件的函數，即 $\mathbb{E}(X\mid Y=y)$ $=$ <span class="text-nowrap">$g(y)$，</span>我們稱其為 $X$ 對 $Y$ 的迴歸函數。證明只用到條件機率密度函數的定義，把 $f_{\sssig Y}(y)$ 提到積分之外，剩下的積分便只與 $y$ 有關。

若把條件本身看成隨機的，$\mathbb{E}(X\mid Y)$ $=$ $g(Y)$ 就是 $Y$ 的函數，也是一個隨機變數，因此還可以再取一次期望值。[Theorem 3.9](#thm-double-expectation) 的雙重期望值定理指出，這一次期望值恰好等於 $X$ 的邊際期望值，即 $\mathbb{E}\bigl[\mathbb{E}(X\mid Y)\bigr]$ $=$ <span class="text-nowrap">$\mathbb{E}(X)$。</span>證明的關鍵一步是把 $\mathbb{E}(X\mid Y=y)$ 乘上 $f_{\sssig Y}(y)$ 之後，$f_{\sssig X\mid Y}(x\mid y)$ 分母上的 $f_{\sssig Y}(y)$ 恰好被消掉，只剩下 $X$ 與 $Y$ 的聯合機率密度函數。這條定理另有 $g(X)$ 的版本，其中 $\mathbb{E}\bigl[\mathbb{E}(X^{2}\mid Y)\bigr]$ $=$ $\mathbb{E}(X^{2})$ 這個特例後續會經常用到。

這條定理背後的直觀就是加權平均。本篇的立體圖把整個原始空間依 $Y$ 的取值切成不同的薄片，每一片都是 $X$ 給定 $Y=y$ 的條件分配；先在每一片上找到重心 $\mathbb{E}(X\mid Y=y)$ 這個值，再以該片自己發生的可能性 $f_{\sssig Y}(y)$ 為權重把這些重心平均起來，所得的就是原始空間中 $X$ 的重心 $\mathbb{E}(X)$ 這個值。乘上 $f_{\sssig Y}(y)$ 這一步之所以是關鍵，正是因為它同時扮演了定義所要求的機率函數與加權平均所要求的權重。

[下一篇](/teaching-topics/ch3-p13-candidate/)以五道例題示範這條定理怎麼用，其中包含期望值不存在時等式不成立的例子，以及讓所求的期望值在等式兩側同時出現、解一條方程式即可求得的作法。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
