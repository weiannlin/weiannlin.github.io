---
title: "眾數"
subtitle: "Mode"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 10
order: 210
permalink: /teaching-topics/ch2-p210-candidate/
date: 2026-08-06
published: false
excerpt: "眾數是使機率函數在值域的閉包上取到最大值的那些點，一個分配可以有多個眾數，也可以沒有眾數。連續型求眾數時，先看密度取到最高值的位置落在值域的內點還是邊界點: 落在內點的用一階與二階條件判斷，是內解；落在邊界點的只能由密度本身的增減性質判斷，是角解。離散型則逐點比較機率的大小，對整數值隨機變數另有一個由相鄰機率比值出發的判準，在 pmf 為單峰的前提下可用來求解眾數。"
---

[上一篇](/teaching-topics/ch2-p209-candidate/)以數道例題示範了變異數的求算，說明期望值使平方離差的期望值達到最小，並以泰勒級數展開求出 $g(X)$ 的期望值與變異數的近似值，最後介紹了與期望值同單位的標準差。期望值指出一個分配的中心，變異數與標準差則衡量分散的程度，兩者合起來已能描述一個分配的大致樣貌，但仍有一些從別的角度出發的量數，能補上期望值與變異數看不到的訊息。

本篇介紹其中的眾數。以下先給出眾數的定義，說明它與樣本眾數的區別、可能不唯一的情形，以及在連續型之下判斷內解與角解的作法，再以兩張圖對照這兩種情形，接著以三道例題示範連續型與離散型的求法，最後對整數值隨機變數給出一個由相鄰機率比值出發的判準，並以一道例題示範其用法。

<div id="def-mode" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.9 (眾數, mode)</div>

若 $X$ 為一隨機變數，pdf 為 $f\_{\sssig X}(x)$ (或 pmf 為 $p\_{\sssig X}(x)$)，值域為 $\mathcal{R}\_{\sssig X}$，並以 $\overline{\mathcal{R}\_{\sssig X}}$ 表 $\mathcal{R}\_{\sssig X}$ 的閉包 <span lang="en">(closure)</span>。連續型的密度在 $\overline{\mathcal{R}\_{\sssig X}}$ 的端點上，一律以自值域內部逼近的極限值計 (以該極限存在者為限)。若 $f\_{\sssig X}$ 在 $\overline{\mathcal{R}\_{\sssig X}}$ 上的最大值存在，則使 $f\_{\sssig X}$ 取到這個最大值的那些 $x$ 所成的集合

$$
\lbrace\,x\in\overline{\mathcal{R}_{\sssig X}}\mid f_{\sssig X}(x)=\max_{y\in\overline{\mathcal{R}_{\sssig X}}}f_{\sssig X}(y)\,\rbrace
$$

之中的每一個元素 $m_o$，皆為 $X$ 之**眾數 (mode)**；離散型只需把式中的 $f\_{\sssig X}$ 換成 <span class="text-nowrap">$p\_{\sssig X}$。</span>

</div>

眾數有一些地方需要注意:

(1) 上述定義中的**眾數**較常被稱為**母體眾數 <span lang="en">(population mode)</span>**，用以避免跟敘述統計學中的**樣本眾數 (sample mode)** 混淆。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

與樣本眾數相同，母體眾數亦可能不唯一或不存在，例如稍後將會提到的均勻分配 <span lang="en">(uniform distribution)</span> 即是很好的例子。

</div>

(2) 定義上，母體眾數是指使得機率函數最大化的點，而在直觀解釋上，可以理解為整個分配中**最可能發生的點**。
{: .topic-paren-item}

<div id="note-local-mode" class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

另有一種讀法，把眾數所指的「最大化」看成一種局域的最大化: 只要求密度 (或 pmf) 在該點的一個鄰域 <span lang="en">(neighborhood)</span> 之內取到最大，而不與全體比較，微積分上代表相對極值而非全域極值。在這種讀法之下，若某分配有多個局域的極值 (即**多峰分配 <span lang="en">(multimodal distribution)</span>**)，則該分配的每一個峰所在的點都是眾數。這種讀法通行於多峰分配與密度估計的文獻，[Definition 2.9](#def-mode) 採的則是全域的界定；本篇後面由[相鄰兩點的機率比值](#adjacent-ratio-criterion)出發的兩式，正是這種讀法在離散型的判準。

離散型不能把鄰域的說法照字面搬過來。以整數值隨機變數為例，值域上的每一點都與其餘各點分開，鄰域的半徑取得夠小時，其中就只剩該點自己，局域最大的不等式自動成立，值域上的每一點都會成為眾數；改以值域中左右緊鄰的兩點比較，才避得開這個結果。這個作法有正式的出處: Keilson and Gerber (1971) 對離散型單峰的界定即是相鄰兩點的比較，該文並證出 pmf 為**對數凹 <span lang="en">(log-concave)</span>**，等價於它與任何單峰的離散分配獨立相加之後仍然單峰 (獨立與和是下一章的內容)，這個性質文獻稱為強單峰 <span lang="en">(strong unimodality)</span>。

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

一般而言，連續型變數求解眾數的方法，多半會判斷該點是否是一個函數的**臨界點 <span lang="en">(critical point)</span>**，再判斷其屬於**內點 <span lang="en">(interior point)</span>** 或是**邊界點 <span lang="en">(boundary point)</span>**，最後決定要使用**內解 <span lang="en">(interior solution)</span>**，或是使用**角解 <span lang="en">(corner solution)</span>** 幫助判斷。

其中，內解是指針對函數的內點，使用微積分的一階及二階微分條件，判斷是否為極值；角解則是指直接繪圖，或由函數本身的增減性質，判斷其函數邊界點是否是極值。

</div>

下面使用兩張圖來說明角解及內部解的差異。

<figure id="fig-mode-corner-solution" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/mode-corner-solution.svg" alt="一條機率密度曲線自左端點開始由高處單調遞減，向右趨近於零；橫軸自左端點再向左延伸一小段，使左端點看得出來是值域的邊界。左端點以實心點標出，並有一條虛線由曲線在該點的高度垂直向下連到橫軸，橫軸上該處標為 m_o，曲線上方標 f_X(x)，橫軸右端標 x。">
  <figcaption><span class="topic-figure__label">Fig. 2.12.</span> 角解: 圖中所繪為指數分配 <span lang="en">(exponential distribution)</span> 的密度 <span class="text-nowrap">$f(x)=e^{-x}$，</span><span class="text-nowrap">$x>0$，</span>密度在值域的左端點以極限值取到最高水準 $1$，眾數 $m_o$ 即落在這個邊界點上。</figcaption>
</figure>

<figure id="fig-mode-interior-solution" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/mode-interior-solution.svg" alt="一條右偏的機率密度曲線自左端的零開始上升，在偏左處到達最高點後緩緩下降，右側拖出一條長尾並趨近於零。最高點以虛線垂直向下連到橫軸，橫軸上該處標為 m_o，曲線上方標 f_X(x)，橫軸右端標 x。">
  <figcaption><span class="topic-figure__label">Fig. 2.13.</span> 內部解: 圖中所繪為一個右偏的伽瑪分配 <span lang="en">(gamma distribution)</span> 的密度，密度在值域內部的臨界點 $m_o\fallingdotseq1.765$ 取到最高值，眾數即落在這個內點上。本圖與 <a href="#fig-mode-corner-solution">Fig. 2.12</a> 共用同一組尺度，兩條曲線的峰高相當，可以直接對照。</figcaption>
</figure>

若讀者還記得 [Fig. 2.11](/teaching-topics/ch2-p208-candidate/#fig-variance-comparison) 的變異數比較圖，應該可以發現在當時的圖中，期望值所對應的點，也是使得該分配的機率密度達到最大值的點。這個原因是該圖的分配是**單峰對稱分配 <span lang="en">(unimodal and symmetric distribution)</span>**，故會有此結果。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

稍後要提到的[**中位數 (median)**](/teaching-topics/ch2-p211-candidate/#def-median) 在單峰對稱分配中，亦會與期望值和眾數為同一個點。

</div>

<div id="ex-power-demand-mode" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.10 <span lang="en">(Continued)</span></div>

<div lang="en" markdown="1">
Suppose that $X$ denotes the growth in demand for electrical power, measured in millions of kilowatt hours, in a certain region over the coming $2$ years, and that the density function of $X$ is

$$
f_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{1}{64}x^{3}, & 0<x<4\\[0.7em]
0, & \text{otherwise}
\end{array}
\right.
$$

<ol class="topic-list-paren topic-list-paren--start-5">
  <li>Find the mode of the growth in demand.</li>
</ol>
</div>

(5) 承[前面各小題](/teaching-topics/ch2-p04-candidate/#ex-power-demand-density)的密度函數，先看 $f\_{\sssig X}$ 在值域上的增減性質。由
{: .topic-paren-item}

$$
f^{\prime}_{\sssig X}(x)=\frac{3}{\,64\,}x^{2}>0,\quad 0<x<4
$$

可知 $f\_{\sssig X}$ 在 $(0,4)$ 上嚴格遞增，故在值域內部找不到臨界點，這一題要以角解處理。值域是開區間，右端點 $4$ 並不屬於值域，分段式在該點記為 $0$；依 [Definition 2.9](#def-mode)，比較是在值域的閉包 $[0,4]$ 上進行，端點上的取值改用自值域內部逼近的極限值，即
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\lim_{x\to4^{-}}f_{\sssig X}(x)=\lim_{x\to4^{-}}\frac{1}{\,64\,}x^{3}=\frac{\,4^{3}\,}{64}=1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\lim_{x\to4^{-}}f_{\sssig X}(x)&=\lim_{x\to4^{-}}\frac{1}{\,64\,}x^{3}\\[0.45em]
&=\frac{\,4^{3}\,}{64}=1
\end{aligned}
$$

</div>

$f\_{\sssig X}$ 既嚴格遞增，這個極限值就是比較所得的最大值，眾數即取在右端這個邊界點，所求為
{: .topic-paren-cont}

$$
m_o=4
$$

</div>

<div id="ex-broken-stick-mode" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.9 <span lang="en">(Continued)</span></div>

<div lang="en" markdown="1">
Suppose that a stick of unit length is broken at a single point, and that the position $X$ of the break has the density

$$
f_{\sssig X}(x)=6\,x(1-x),\quad 0<x<1
$$

<ol class="topic-list-paren topic-list-paren--start-3">
  <li>Find the mode of the length of the piece that contains the midpoint.</li>
</ol>
</div>

(3) 承[前一小題](/teaching-topics/ch2-p207-candidate/#ex-broken-stick-expected-length)，含中點的那一段必為較長的一段，故所求為
{: .topic-paren-item}

$$
Y=\max(X,\,1-X)
$$

的眾數。對 $\frac{1}{\,2\,}<y<1$ 有
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{P}(Y\leqslant y)=\mathbb{P}(1-y\leqslant X\leqslant y)=F_{\sssig X}(y)-F_{\sssig X}(1-y)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{P}(Y\leqslant y)&=\mathbb{P}(1-y\leqslant X\leqslant y)\\[0.45em]
&=F_{\sssig X}(y)-F_{\sssig X}(1-y)
\end{aligned}
$$

</div>

兩邊對 $y$ 微分，即得 $Y$ 之 pdf 為
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig Y}(y)=f_{\sssig X}(y)+f_{\sssig X}(1-y)=12\,y(1-y),\quad \frac{1}{\,2\,}<y<1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig Y}(y)&=f_{\sssig X}(y)+f_{\sssig X}(1-y)\\[0.45em]
&=12\,y(1-y),\quad \frac{1}{\,2\,}<y<1
\end{aligned}
$$

</div>

而
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f^{\prime}_{\sssig Y}(y)=12(1-2y)<0,\quad \frac{1}{\,2\,}<y<1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&f^{\prime}_{\sssig Y}(y)=12(1-2y)<0,\\[0.45em]
&\quad \frac{1}{\,2\,}<y<1
\end{aligned}
$$

</div>

可知 $f\_{\sssig Y}$ 在 $\frac{1}{\,2\,}<y<1$ 上嚴格遞減，故在區間內部找不到臨界點。與前一題同理，比較在 $[\frac{1}{\,2\,},1]$ 上進行，左端點上的取值改用極限值 $3$，$f\_{\sssig Y}$ 既嚴格遞減，這個值就是比較所得的最大值，眾數即取在左端這個邊界點，所求為
{: .topic-paren-cont}

$$
m_o=\frac{1}{\,2\,}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這一題問的是含中點那一段長度的眾數，也就是 $Y$ 的眾數，而不是斷點位置 $X$ 的眾數。$X$ 與 $Y$ 的密度並不相同，必須先求出 $f\_{\sssig Y}$ 才能討論。

求出 $f\_{\sssig Y}$ 之後，這一題正好與 [Fig. 2.13](#fig-mode-interior-solution) 的內部解成對照。$f\_{\sssig Y}$ 在 $\frac{1}{\,2\,}<y<1$ 的內部沒有臨界點，一階與二階條件在此無從施力，只能由密度本身的增減性質判斷: 遞減的密度使最高的位置落在左端的邊界上，這就是 [Fig. 2.12](#fig-mode-corner-solution) 的角解。若密度在區間內部先升後降，最高的位置才會落在內部的臨界點上，那才是以一階與二階條件判斷的內解。

</div>

<div id="ex-weekly-accidents-mode" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.15 <span lang="en">(Continued)</span></div>

<div lang="en" markdown="1">
Suppose that $X$ denotes the number of accidents occurring in Ankang City in a week, and that the probability distribution of the number of accidents is given in the following table.

| $x$ | $3$ | $4$ | $5$ | $6$ |
|:---:|:---:|:---:|:---:|:---:|
| $\mathbb{P}(X=x)$ | $0.2$ | $0.3$ | $0.3$ | $0.2$ |
{: .topic-table--matrix}

<ol class="topic-list-paren topic-list-paren--start-3">
  <li>Find the mode of this distribution.</li>
</ol>
</div>

(3) 承[前面各小題](/teaching-topics/ch2-p06-candidate/#ex-weekly-accidents)的機率分配，由表可知 $X=4$ 及 $5$ 都使得 $\mathbb{P}(X=x)$ 達到最大值 $0.3$，故此機率分配的眾數所成的集合為
{: .topic-paren-item}

$$
\lbrace\,4,\,5\,\rbrace
$$

也就是 $4$ 與 $5$ 都是眾數。
{: .topic-paren-cont}

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

離散型隨機變數中，尋找眾數的方式並不若連續型變數這麼直接，若 pmf 較為複雜，尋找眾數的過程可能相當不容易，然而，尋找眾數的觀念是相同的。

</div>

部分教科書上將眾數的定義寫為，眾數 $m_o$ 為滿足

$$
f_{\sssig X}(m_o)\geqslant f_{\sssig X}(x),\quad\forall\,x\in\mathbb{R}
$$

之值 (離散型則記為 $p\_{\sssig X}(m_o)\geqslant p\_{\sssig X}(x)$ 對一切 $x\in\mathbb{R}$ 皆成立)。這個寫法與 [Definition 2.9](#def-mode) 要求的同樣是全域的最大化: 密度在值域之外為 <span class="text-nowrap">$0$，</span>因此在整條實數線上比較與在值域上比較，密度所能達到的最高水準相同。兩者的差別只在值域的端點: 依這個寫法，開區間的端點不屬於值域，密度在其上為 $0$，[Example 2.10 <span lang="en">(Continued)</span>](#ex-power-demand-mode) 那樣密度要到端點才逼近最高水準的分配便沒有眾數；[Definition 2.9](#def-mode) 改在值域的閉包上比較，端點上的取值改用極限值，這一類角解因而有解。

若由此來看，針對離散型隨機變數 (特別是整數值隨機變數)，將有一個比較容易尋找的方式。這裡要先設一個前提: $X$ 的 pmf 為**單峰**的，也就是機率隨 $x$ 遞增到某一點之後便不再回升，一個常見的充分條件是 pmf 為對數凹的。下面的兩個不等式只要求 $m_o$ 的機率不低於左右緊鄰兩點的機率，正是[前面提到的局域讀法](#note-local-mode)在離散型的寫法，對一般的 pmf 未必推得出 [Definition 2.9](#def-mode) 所要的全域最大值；有了單峰的前提，滿足這兩式的點才必定是使 pmf 最大的點。令 $m_o$ 表示隨機變數 $X$ 的眾數，則我們有
{: #adjacent-ratio-criterion}

$$
\left\lbrace
\begin{array}{l}
p_{\sssig X}(m_o)\geqslant p_{\sssig X}(m_o+1)\\[0.35em]
p_{\sssig X}(m_o)\geqslant p_{\sssig X}(m_o-1)
\end{array}
\right.
$$

利用上式，搭配 $X$ 的 pmf，即可求解眾數 <span class="text-nowrap">$m_o$，</span>見下列範例。

<div id="ex-poisson-mode" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.22</div>

令離散型隨機變數 $X$ 具以下 pmf:

$$
p_{\sssig X}(x)=
\left\lbrace
\begin{array}{c@{\quad}l}
\dfrac{e^{-\lambda}\lambda^{x}}{x!}, & x=0,1,2,\ldots\\[0.7em]
0, & \text{otherwise}
\end{array}
\right.
$$

其中 $\lambda>0$，試求該分配之眾數為何？

令 $m_o$ 表示隨機變數 $X$ 的眾數，則我們有

$$
\left\lbrace
\begin{array}{l}
p_{\sssig X}(m_o)\geqslant p_{\sssig X}(m_o+1)\\[0.35em]
p_{\sssig X}(m_o)\geqslant p_{\sssig X}(m_o-1)
\end{array}
\right.
$$

由此，分別可得到

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\frac{p_{\sssig X}(m_o)}{p_{\sssig X}(m_o+1)}=\frac{\dfrac{e^{-\lambda}\lambda^{m_o}}{m_o!}}{\dfrac{e^{-\lambda}\lambda^{m_o+1}}{(m_o+1)!}}=\frac{m_o+1}{\lambda}\geqslant1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\frac{p_{\sssig X}(m_o)}{p_{\sssig X}(m_o+1)}&=\frac{\dfrac{e^{-\lambda}\lambda^{m_o}}{m_o!}}{\dfrac{e^{-\lambda}\lambda^{m_o+1}}{(m_o+1)!}}\\[0.45em]
&=\frac{m_o+1}{\lambda}\geqslant1
\end{aligned}
$$

</div>

與

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\frac{p_{\sssig X}(m_o)}{p_{\sssig X}(m_o-1)}=\frac{\dfrac{e^{-\lambda}\lambda^{m_o}}{m_o!}}{\dfrac{e^{-\lambda}\lambda^{m_o-1}}{(m_o-1)!}}=\frac{\lambda}{m_o}\geqslant1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\frac{p_{\sssig X}(m_o)}{p_{\sssig X}(m_o-1)}&=\frac{\dfrac{e^{-\lambda}\lambda^{m_o}}{m_o!}}{\dfrac{e^{-\lambda}\lambda^{m_o-1}}{(m_o-1)!}}\\[0.45em]
&=\frac{\lambda}{m_o}\geqslant1
\end{aligned}
$$

</div>

合併此二式，可以得到

$$
\lambda-1\leqslant m_o\leqslant\lambda
$$

則所求為

$$
m_o=
\left\lbrace
\begin{array}{c@{\quad}l}
\lambda-1\ \text{或}\ \lambda, & \lambda\in\mathbb{N}\\[0.5em]
[\lambda], & \lambda\notin\mathbb{N}
\end{array}
\right.
$$

其中 $[\lambda]$ 是**高斯符號**，表不大於 $\lambda$ 之最大整數。

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

上面第二個比值除以 $p\_{\sssig X}(m_o-1)$，前提是 $m_o-1$ 仍落在 $X$ 的值域之內。當 $\lambda<1$ 時，由

$$
p_{\sssig X}(0)=e^{-\lambda}>\lambda\,e^{-\lambda}=p_{\sssig X}(1)
$$

可知 pmf 自 $x=0$ 起就一路遞減，眾數為 $0$，此時 $m_o-1=-1$ 並不在值域之內，第二個比值的式子並不適用。這個情形下 $\lambda\notin\mathbb{N}$，$[\lambda]=0$，答案本身仍然對得上，只是不能由該式導出。

</div>

## 本篇小結

[Definition 2.9](#def-mode) 把眾數界定為使機率函數在值域的閉包上取到**最大值**的那些點所成的集合中的元素，連續型的密度在端點上以極限值比較，而這個最大值未必存在。既然是集合，眾數自然可能不只一個，也可能一個都沒有；均勻分配就是不唯一的例子。指稱時以母體眾數與樣本眾數區別，直觀上它是整個分配中最可能發生的點。另有一種只在鄰域之內比較的[局域讀法](#note-local-mode)，在那種讀法之下，多峰分配的每一個峰所在的點都是眾數。

連續型求眾數的作法，是先判斷密度取到最高值的位置落在值域的內點還是邊界點: 落在內點的以一階與二階條件判斷，是 [Fig. 2.13](#fig-mode-interior-solution) 的內解；落在邊界點的只能由密度本身的增減性質判斷，是 [Fig. 2.12](#fig-mode-corner-solution) 的角解。[Example 2.10 <span lang="en">(Continued)</span>](#ex-power-demand-mode) 與 [Example 2.9 <span lang="en">(Continued)</span>](#ex-broken-stick-mode) 都是角解，而且密度所在的區間都是開區間，端點不屬於該區間，比較因而在閉包上進行，端點上的取值改用極限值，眾數即取在該端點。[Example 2.15 <span lang="en">(Continued)</span>](#ex-weekly-accidents-mode) 是離散型，逐點比較機率的大小即可，該題有兩個眾數。

部分教科書把眾數的最大化寫成在整條實數線上比較，與 [Definition 2.9](#def-mode) 同樣要求全域的最大化，差別只在值域的端點算不算數。在 pmf 為單峰的前提之下，整數值隨機變數的眾數可由相鄰兩點的機率比值求得，[Example 2.22](#ex-poisson-mode) 即是一例。[下一篇](/teaching-topics/ch2-p211-candidate/)介紹另一個從位置出發的量數: 中位數。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Alexander M. Mood, Franklin A. Graybill, and Duane C. Boes. 1974. *Introduction to the Theory of Statistics*. 3rd ed. McGraw-Hill.
- Julian Keilson and Hans U. Gerber. 1971. “Some Results for Discrete Unimodality.” *Journal of the American Statistical Association* 66 (334): 386–389.
- Sudhakar Dharmadhikari and Kumar Joag-Dev. 1988. *Unimodality, Convexity, and Applications*. Academic Press.
