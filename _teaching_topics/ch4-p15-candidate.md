---
title: "貝塔函數與貝塔分配"
subtitle: "The Beta Function and the Beta Distribution"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 4
topic: 15
order: 415
permalink: /teaching-topics/ch4-p15-candidate/
date: 2026-08-12
published: false
excerpt: "貝塔函數以 $\\int_{0}^{1}x^{\\alpha-1}(1-x)^{\\beta-1}\\,dx$ 這個積分定義，並可寫成 $\\frac{\\Gamma(\\alpha)\\Gamma(\\beta)}{\\Gamma(\\alpha+\\beta)}$ 這個由伽瑪函數構成的比值，貝塔分配的一切推導都由這條關係式而來。貝塔分配的值域落在 $0$ 到 $1$ 之間，因此經常被用來描述一個機率的分配，期望值為 $\\frac{\\alpha}{\\alpha+\\beta}$、變異數為 $\\frac{\\alpha\\beta}{(\\alpha+\\beta)^{2}(\\alpha+\\beta+1)}$，$k$ 階原動差亦可一併求得。本篇先給出貝塔函數與它的兩項特性，再給出貝塔分配的定義與完整推導，並說明它在貝氏統計學派中作為共軛先驗分配的角色。最後列出三項衍伸性質: $\\alpha=\\beta=1$ 時退回標準均勻分配、標準均勻分配的順序統計量服從貝塔分配，以及機率密度在 $\\frac{\\alpha}{\\alpha+\\beta}$ 附近聚集，而 $\\alpha$ 與 $\\beta$ 的大小決定聚集的程度。"
---

[上一篇](/teaching-topics/ch4-p14-candidate/)以[均勻分配](/teaching-topics/ch4-p14-candidate/#def-uniform-distribution)為主軸，說明它在值域之內每一處的機率密度都相同，並由這個性質給出[機率積分轉換](/teaching-topics/ch4-p14-candidate/#thm-p-i-t)與[逆機率積分轉換](/teaching-topics/ch4-p14-candidate/#thm-i-p-i-t)兩個定理。本篇要看的，同樣是一個取值落在 $0$ 到 $1$ 之間的連續隨機變數，但這一次容許不同位置上的機率密度高低不同，這就是貝塔分配。

推導貝塔分配的期望值與變異數時所要用到的工具是[貝塔函數](#def-beta-function)，而貝塔函數本身又可以寫成一個由[伽瑪函數](/teaching-topics/ch4-p10-candidate/#def-gamma-function)構成的比值。本篇因而先由這個函數談起，列出它的兩項特性，再進入[貝塔分配](#def-beta-distribution)的定義與完整推導，其後說明三項衍伸性質，最後以一張圖比較不同參數之下機率密度聚集的情況。

## 貝塔函數

<div id="def-beta-function" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 4.19 (貝塔函數, beta function)</div>

**貝塔函數 <span lang="en">(beta function)</span>** 是下列的函數:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathcal{B}(\alpha,\beta)\equiv\int_{0}^{1}x^{\alpha-1}(1-x)^{\beta-1}\,dx,\ \alpha,\beta>0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathcal{B}(\alpha,\beta)\equiv\int_{0}^{1}x^{\alpha-1}(1-x)^{\beta-1}\,dx,\\[0.25em]
\alpha,\beta>0
\end{gathered}
$$

</div>

</div>

貝塔函數具有以下的特性:

$$
\begin{gathered}
\mathcal{B}(\alpha,\beta)=\frac{\,\Gamma(\alpha)\Gamma(\beta)\,}{\Gamma(\alpha+\beta)},\ \alpha,\beta>0\\[0.7em]
\mathcal{B}(\alpha,\beta)=\mathcal{B}(\beta,\alpha)
\end{gathered}
$$

## 貝塔分配

<div id="def-beta-distribution" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 4.20 (貝塔分配, beta distribution)</div>

**適用範圍**:

令 $X$ 為一個 $0$ 到 $1$ 之間的連續隨機變數，經常被用來描述為一個機率 $p$ 的分配。

**值域範圍**:

$$
\mathcal{R}_{\sssig X}=\lbrace\,x\mid 0\leqslant x\leqslant1\,\rbrace
$$

**表示式**:

$$
X\sim\mathrm{Beta}(a,\ b)
$$

**參數與參數範圍**:

$\alpha,\beta>0$ 為形狀參數。

**機率函數**:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X}(x)=\frac{\Gamma(\alpha+\beta)}{\,\Gamma(\alpha)\Gamma(\beta)\,}x^{\alpha-1}(1-x)^{\beta-1}=\frac{1}{\,\mathcal{B}(\alpha,\beta)\,}x^{\alpha-1}(1-x)^{\beta-1},\ 0\leqslant x\leqslant1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig X}(x)&=\frac{\Gamma(\alpha+\beta)}{\,\Gamma(\alpha)\Gamma(\beta)\,}x^{\alpha-1}(1-x)^{\beta-1}\\[0.45em]
&=\frac{1}{\,\mathcal{B}(\alpha,\beta)\,}x^{\alpha-1}(1-x)^{\beta-1},\\[0.25em]
&\qquad 0\leqslant x\leqslant1
\end{aligned}
$$

</div>

**期望值、變異數**:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(X)=\frac{\alpha}{\,\alpha+\beta\,},\quad \mathrm{Var}(X)=\frac{\alpha\,\beta}{\,(\alpha+\beta)^{2}(\alpha+\beta+1)\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{E}(X)=\frac{\alpha}{\,\alpha+\beta\,}\\[0.45em]
\mathrm{Var}(X)=\frac{\alpha\,\beta}{\,(\alpha+\beta)^{2}(\alpha+\beta+1)\,}
\end{gathered}
$$

</div>

</div>

貝塔分配 <span lang="en">(beta distribution)</span> 有一些地方需要注意:

(1) 我們證明其機率函數為一個合法的機率函數與期望值、變異數如下:
{: .topic-paren-item}

<div class="topic-proof" markdown="1">
**Proof.** 先驗證機率函數在值域上的積分為 <span class="text-nowrap">$1$，</span>即

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\int_{x\in\mathcal{R}_{\sssig X}}f_{\sssig X}(x)\,dx&=\int_{0}^{1}\frac{\Gamma(\alpha+\beta)}{\,\Gamma(\alpha)\Gamma(\beta)\,}x^{\alpha-1}(1-x)^{\beta-1}\,dx\\[0.45em]
&=\frac{\Gamma(\alpha+\beta)}{\,\Gamma(\alpha)\Gamma(\beta)\,}\int_{0}^{1}x^{\alpha-1}(1-x)^{\beta-1}\,dx=\frac{\Gamma(\alpha+\beta)}{\,\Gamma(\alpha)\Gamma(\beta)\,}\cdot\frac{\,\Gamma(\alpha)\Gamma(\beta)\,}{\Gamma(\alpha+\beta)}=1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\int_{x\in\mathcal{R}_{\sssig X}}f_{\sssig X}(x)\,dx\\[0.45em]
&\quad =\int_{0}^{1}\frac{\Gamma(\alpha+\beta)}{\,\Gamma(\alpha)\Gamma(\beta)\,}x^{\alpha-1}(1-x)^{\beta-1}\,dx\\[0.45em]
&\quad =\frac{\Gamma(\alpha+\beta)}{\,\Gamma(\alpha)\Gamma(\beta)\,}\int_{0}^{1}x^{\alpha-1}(1-x)^{\beta-1}\,dx\\[0.45em]
&\quad =\frac{\Gamma(\alpha+\beta)}{\,\Gamma(\alpha)\Gamma(\beta)\,}\cdot\frac{\,\Gamma(\alpha)\Gamma(\beta)\,}{\Gamma(\alpha+\beta)}=1
\end{aligned}
$$

</div>

接著求期望值，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\int_{x\in\mathcal{R}_{\sssig X}}xf_{\sssig X}(x)\,dx=\frac{\Gamma(\alpha+\beta)}{\,\Gamma(\alpha)\Gamma(\beta)\,}\int_{0}^{1}x^{(\alpha+1)-1}(1-x)^{\beta-1}\,dx\\[0.45em]
&=\frac{\Gamma(\alpha+\beta)}{\,\Gamma(\alpha)\Gamma(\beta)\,}\cdot\frac{\,\Gamma(\alpha+1)\Gamma(\beta)\,}{\Gamma(\alpha+\beta+1)}=\frac{\Gamma(\alpha+\beta)}{\,\Gamma(\alpha)\Gamma(\beta)\,}\cdot\frac{\,\alpha\Gamma(\alpha)\Gamma(\beta)\,}{\,(\alpha+\beta)\Gamma(\alpha+\beta)\,}=\frac{\alpha}{\,\alpha+\beta\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}(X)=\int_{x\in\mathcal{R}_{\sssig X}}xf_{\sssig X}(x)\,dx\\[0.45em]
&\quad =\frac{\Gamma(\alpha+\beta)}{\,\Gamma(\alpha)\Gamma(\beta)\,}\int_{0}^{1}x^{(\alpha+1)-1}(1-x)^{\beta-1}\,dx\\[0.45em]
&\quad =\frac{\Gamma(\alpha+\beta)}{\,\Gamma(\alpha)\Gamma(\beta)\,}\cdot\frac{\,\Gamma(\alpha+1)\Gamma(\beta)\,}{\Gamma(\alpha+\beta+1)}\\[0.45em]
&\quad =\frac{\Gamma(\alpha+\beta)}{\,\Gamma(\alpha)\Gamma(\beta)\,}\cdot\frac{\,\alpha\Gamma(\alpha)\Gamma(\beta)\,}{\,(\alpha+\beta)\Gamma(\alpha+\beta)\,}\\[0.45em]
&\quad =\frac{\alpha}{\,\alpha+\beta\,}
\end{aligned}
$$

</div>

又可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl(X^{2}\bigr)&=\int_{x\in\mathcal{R}_{\sssig X}}x^{2}f_{\sssig X}(x)\,dx=\frac{\Gamma(\alpha+\beta)}{\,\Gamma(\alpha)\Gamma(\beta)\,}\int_{0}^{1}x^{(\alpha+2)-1}(1-x)^{\beta-1}\,dx\\[0.45em]
&=\frac{\Gamma(\alpha+\beta)}{\,\Gamma(\alpha)\Gamma(\beta)\,}\cdot\frac{\,\Gamma(\alpha+2)\Gamma(\beta)\,}{\Gamma(\alpha+\beta+2)}=\frac{\Gamma(\alpha+\beta)}{\,\Gamma(\alpha)\Gamma(\beta)\,}\cdot\frac{\,(\alpha+1)\alpha\Gamma(\alpha)\Gamma(\beta)\,}{\,(\alpha+\beta+1)(\alpha+\beta)\Gamma(\alpha+\beta)\,}\\[0.45em]
&=\frac{\alpha(\alpha+1)}{(\alpha+\beta)(\alpha+\beta+1)}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}\bigl(X^{2}\bigr)=\int_{x\in\mathcal{R}_{\sssig X}}x^{2}f_{\sssig X}(x)\,dx\\[0.45em]
&\quad =\frac{\Gamma(\alpha+\beta)}{\,\Gamma(\alpha)\Gamma(\beta)\,}\int_{0}^{1}x^{(\alpha+2)-1}(1-x)^{\beta-1}\,dx\\[0.45em]
&\quad =\frac{\Gamma(\alpha+\beta)}{\,\Gamma(\alpha)\Gamma(\beta)\,}\cdot\frac{\,\Gamma(\alpha+2)\Gamma(\beta)\,}{\Gamma(\alpha+\beta+2)}\\[0.45em]
&\quad =\frac{\Gamma(\alpha+\beta)}{\,\Gamma(\alpha)\Gamma(\beta)\,}\\[0.25em]
&\qquad \times\frac{\,(\alpha+1)\alpha\Gamma(\alpha)\Gamma(\beta)\,}{\,(\alpha+\beta+1)(\alpha+\beta)\Gamma(\alpha+\beta)\,}\\[0.45em]
&\quad =\frac{\alpha(\alpha+1)}{(\alpha+\beta)(\alpha+\beta+1)}
\end{aligned}
$$

</div>

最後由前兩者求變異數，可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(X)&=\mathbb{E}\bigl(X^{2}\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}=\frac{\alpha(\alpha+1)}{(\alpha+\beta)(\alpha+\beta+1)}-\Bigl(\frac{\alpha}{\alpha+\beta}\Bigr)^{2}\\[0.45em]
&=\frac{\alpha\,\beta}{(\alpha+\beta)^{2}(\alpha+\beta+1)}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathrm{Var}(X)=\mathbb{E}\bigl(X^{2}\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}\\[0.45em]
&\quad =\frac{\alpha(\alpha+1)}{(\alpha+\beta)(\alpha+\beta+1)}-\Bigl(\frac{\alpha}{\alpha+\beta}\Bigr)^{2}\\[0.45em]
&\quad =\frac{\alpha\,\beta}{(\alpha+\beta)^{2}(\alpha+\beta+1)}
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

事實上，我們可以計算 $X$ 的 $k$ 階原動差，這將會讓許多證明變得更容易，我們證明如下:

<div class="topic-proof" markdown="1">
**Proof.** 由機率函數可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}\bigl(X^{k}\bigr)&=\int_{x\in\mathcal{R}_{\sssig X}}x^{k}f_{\sssig X}(x)\,dx=\frac{\Gamma(\alpha+\beta)}{\,\Gamma(\alpha)\Gamma(\beta)\,}\int_{0}^{1}x^{(\alpha+k)-1}(1-x)^{\beta-1}\,dx\\[0.45em]
&=\frac{\Gamma(\alpha+\beta)}{\,\Gamma(\alpha)\Gamma(\beta)\,}\cdot\frac{\,\Gamma(\alpha+k)\Gamma(\beta)\,}{\Gamma(\alpha+\beta+k)}=\frac{\,\Gamma(\alpha+\beta)\Gamma(\alpha+k)\,}{\,\Gamma(\alpha)\Gamma(\alpha+\beta+k)\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}\bigl(X^{k}\bigr)=\int_{x\in\mathcal{R}_{\sssig X}}x^{k}f_{\sssig X}(x)\,dx\\[0.45em]
&\quad =\frac{\Gamma(\alpha+\beta)}{\,\Gamma(\alpha)\Gamma(\beta)\,}\\[0.25em]
&\qquad \times\int_{0}^{1}x^{(\alpha+k)-1}(1-x)^{\beta-1}\,dx\\[0.45em]
&\quad =\frac{\Gamma(\alpha+\beta)}{\,\Gamma(\alpha)\Gamma(\beta)\,}\cdot\frac{\,\Gamma(\alpha+k)\Gamma(\beta)\,}{\Gamma(\alpha+\beta+k)}\\[0.45em]
&\quad =\frac{\,\Gamma(\alpha+\beta)\Gamma(\alpha+k)\,}{\,\Gamma(\alpha)\Gamma(\alpha+\beta+k)\,}
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

</div>

<!-- ref-point: 待第三章第 15 篇 (變異數分解定理，書稿 mathstatch3.tex 第 2783 行的註記，
     該註記即階層模型的出處) 發布後，將下面第 (2) 點的「我們所提到之階層模型」改為指向該處的
     站內連結。書稿此處原寫「在頁 \pageref{hierModel} 中我們所提到之階層模型」，網頁先以行文
     敘述，不放失效連結。 -->

(2) 由於其值域的範圍為 $[0,1]$ 的緣故，貝塔分配常常被用來描述[伯努利實驗](/teaching-topics/ch4-p01-candidate/#def-ber-trial)中，成功機率 $p$ 的分配，這種情況屬於我們所提到之階層模型 <span lang="en">(hierarchical model)</span> 的範疇，也是**貝氏統計學派 <span lang="en">(Bayesian statistics)</span>** 所探討的領域之一。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

貝塔分配在貝氏統計學派中，經常被用來當作成敗伯努利實驗中成功機率的**先驗分配 <span lang="en">(prior distribution)</span>**，其原因在於這貝塔分配是所有成敗實驗相關分配的**共軛先驗分配 <span lang="en">(conjugate prior distribution)</span>**，換言之即**先驗分配與後驗分配 <span lang="en">(posterior distribution)</span> 是同一種分配**。例如: $P\sim\mathrm{Beta}(\alpha,\beta)$ 且 <span class="text-nowrap">$X\mid(P=p)\sim\mathrm{Bin}(n,\ p)$，</span>則後驗分配 $P\mid(X=x)$ 仍是貝塔分配。

除此之外，常見的**先驗-後驗**共軛組合還有**伽瑪-卜瓦松**與**常態-常態**。

</div>

(3) 前述眾多原因刻劃了貝塔分配的一些性質，我們將其衍伸性質列在下方:
{: .topic-paren-item}

第一，若 <span class="text-nowrap">$U\sim\mathrm{Beta}(\alpha=1,\ \beta=1)$，</span>則
{: .topic-paren-cont}

$$
U\sim\mathcal{U}(0,1)
$$

<div class="topic-proof" markdown="1">
**Proof.** 已知 <span class="text-nowrap">$U\sim\mathrm{Beta}(\alpha=1,\ \beta=1)$，</span>則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig U}(u)=\frac{\Gamma(2)}{\,\Gamma(1)\Gamma(1)\,}u^{1-1}(1-u)^{1-1}=1,\ 0<u<1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
f_{\sssig U}(u)&=\frac{\Gamma(2)}{\,\Gamma(1)\Gamma(1)\,}u^{1-1}(1-u)^{1-1}\\[0.45em]
&=1,\ 0<u<1
\end{aligned}
$$

</div>

故可知

$$
U\sim\mathcal{U}(0,1)
$$

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

貝塔分配與[標準均勻分配](/teaching-topics/ch4-p14-candidate/#def-uniform-distribution)的關係匪淺。標準均勻分配可以理解為，在 $[0,1]$ 之間沒有特別可能出現的位置，而貝塔分配則恰巧相反，強調了在 $[0,1]$ 之間比較容易出現的位置，但我們當然也可以經過一些設定，從而讓貝塔分配「退化」回標準均勻分配，這個設定方式就是 <span class="text-nowrap">$\alpha=\beta=1$。</span>

</div>

第二，標準均勻分配的順序統計量 <span lang="en">(order statistics)</span> 服從貝塔分配，而一般的均勻分配的順序統計量也能透過線性轉換而服從貝塔分配。
{: .topic-paren-cont}

<!-- ref-point: 待第三章第 27 篇 (順序統計量的定義，書稿 mathstatch3.tex 第 5133 行起的小節)
     發布後，將上面「順序統計量」四個字改為指向該篇定義 anchor 的站內連結；待第三章第 28 篇
     (順序統計量的抽樣分配，書稿 mathstatch3.tex 第 5391 行起的條列，該處給出標準均勻分配的
     順序統計量服從貝塔分配) 發布後，將下面 Note 中的「我們便曾經提過這個性質了」改為指向該處
     的站內連結。書稿此處原寫「在頁 \pageref{uniformOrder} 中」，網頁先以行文敘述。 -->

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

事實上，讀者應該沒有忘記，我們便曾經提過這個性質了，而當時我們亦曾經提到，順序統計量會「扭曲」原本應是均勻的母體分配，在特定的位置周遭具有較大的機率密度，這一個特點正是標準均勻分配與貝塔分配最大的不同，可見下一個性質的比較。

</div>

第三，$\mathrm{Beta}(\alpha,\beta)$ 分配在 $\frac{\alpha}{\,\alpha+\beta\,}$ 的附近具有較高的機率密度，而 $\alpha,\beta$ 的大小則決定了在 $\frac{\alpha}{\,\alpha+\beta\,}$ 週遭離散的程度 (即變異數)。
{: .topic-paren-cont}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

在貝氏統計學派的領域中，標準均勻分配被視為無法提供任何訊息的先驗分配 <span lang="en">(non-informative prior)</span>，這個原因其實很簡單，因為當我們指定一個機率的先驗分配服從標準均勻分配時，相當於我們對這個分配比較有可能出現的值完全沒有想法；相反地，如果我們設定了較為一般的貝塔分配，說明我們對於這個機率是有事先的想法的，至於這個想法的「強度」可以透過調控 $\alpha$ 與 $\beta$ 數值的大小來決定，見下方圖示的比較。

</div>

下面便將不同參數的貝塔分配畫在同一張圖上，方便讀者比較不同參數的貝塔分配，其機率密度聚集的情況。
{: .topic-paren-cont}

<!-- fig-pending: beta-density-family
     Fig. 4.3，單一面板，對應書稿 mathstatch4.tex 第 3049 行的 tikzpicture (書稿以 center
     置中，內容全部由 pgfplots 的 axis 環境繪出，寬 .8\textwidth、高 .55\textwidth)。
     畫的是五條貝塔分配的機率密度曲線疊在同一張圖上，五組參數依書稿的繪製順序為
     (α, β) = (1, 1)、(2, 4)、(2, 2)、(4, 2)、(8, 8)，
     書稿的線型依序為 thick 實線、dashdotted、一般實線、dashdotdotted、dashed，一律黑色、
     smooth，並各自以 \addlegendentry 標出 $\alpha=1, \beta=1$ 等五組參數。
     密度以 declare function 定義的 (a+b-1)!/((a-1)!(b-1)!) x^(a-1) (1-x)^(b-1) 繪出，
     即五組參數皆為正整數時的貝塔密度。
     座標設定: samples = 600、domain 為 0 至 1、只畫 x 軸 (axis x line=bottom)，
     y 軸不畫 (axis y line=none) 且不顯示刻度數值，兩軸皆不寫軸名，
     xtick 自 0 至 1.1 每 0.1 一格，xmin = -0.1、xmax = 1.1、ymin = 0、ymax = 4。
     檔名 beta-density-family.svg，anchor 取 #fig-beta-density-family，
     caption 起首為 Fig. 4.3.，內容說明五組參數之下機率密度聚集的位置與聚集的程度。
     圖畫好之後，上一段末的「聚集的情況」之後補上指向該 anchor 的 Fig. 4.3 連結；
     其後那一則以「從上圖便可以看出」起首的 Note 即是對本圖的說明，兩者不可分開。 -->

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

從上圖便可以看出，貝塔分配在 $[0,1]$ 區間之內，機率密度大多都在期望值 $\frac{\alpha}{\alpha+\beta}$ 聚集，而即使是一樣的期望值，依照 $\alpha$ 與 $\beta$ 的不同，聚集在期望值周遭的離散程度也不同；若 $\alpha$ 與 $\beta$ 都比較大的時候，則聚集的情況也比較明顯，如 $\alpha=\beta=8$ 與 $\alpha=\beta=2$ 的比較。

此外，我們也可以看出，當 $\alpha=\beta=1$ 的時候，貝塔分配在 $[0,1]$ 之間的機率密度是完全均勻的，也就是標準均勻分配。

</div>

## 本篇小結

[Definition 4.19](#def-beta-function) 的貝塔函數由一個積分界定，也就是 $\int_{0}^{1}x^{\alpha-1}(1-x)^{\beta-1}\,dx$ 這個式子，它的兩項特性一是可以寫成 $\frac{\Gamma(\alpha)\Gamma(\beta)}{\Gamma(\alpha+\beta)}$ 這個由[伽瑪函數](/teaching-topics/ch4-p10-candidate/#def-gamma-function)構成的比值，二是兩個參數對調之後函數值不變。本篇其後的每一步推導，用到的都是第一項特性。

[Definition 4.20](#def-beta-distribution) 的貝塔分配以 $\alpha$ 與 $\beta$ 兩個形狀參數界定，值域為 <span class="text-nowrap">$0\leqslant x\leqslant1$，</span>機率函數的常數項正是貝塔函數的倒數，這使得密度在值域上的積分等於 <span class="text-nowrap">$1$。</span>期望值與變異數的求法完全相同: 把 $x$ 或 $x^{2}$ 併入被積函數，指數上的 $\alpha$ 因而變成 $\alpha+1$ 或 <span class="text-nowrap">$\alpha+2$，</span>積分之後仍是一個貝塔函數，再以 $\Gamma(\alpha+1)=\alpha\Gamma(\alpha)$ 化簡，得到 $\mathbb{E}(X)=\frac{\alpha}{\alpha+\beta}$ 與 $\mathrm{Var}(X)=\frac{\alpha\beta}{(\alpha+\beta)^{2}(\alpha+\beta+1)}$ 這兩個公式。同一個作法對任意的 $k$ 都成立，因而可以一次求得 $k$ 階原動差 $\frac{\Gamma(\alpha+\beta)\Gamma(\alpha+k)}{\Gamma(\alpha)\Gamma(\alpha+\beta+k)}$ 這個式子。

定義之後的三點說明依序是: 貝塔分配的值域使它適合描述一個成功機率，這正是貝氏統計學派中共軛先驗分配的用法，先驗分配取貝塔分配、觀測值取二項分配時，後驗分配仍是貝塔分配；三項衍伸性質則是 $\alpha=\beta=1$ 時退回[標準均勻分配](/teaching-topics/ch4-p14-candidate/#def-uniform-distribution)、標準均勻分配的順序統計量服從貝塔分配，以及機率密度在 $\frac{\alpha}{\alpha+\beta}$ 附近聚集。最後一項也說明了貝塔分配與標準均勻分配的分別: 標準均勻分配對值域上的每一處一視同仁，貝塔分配則指出比較容易出現的位置，而 $\alpha$ 與 $\beta$ 的大小決定了聚集的程度，兩者都大時聚集得比較明顯。

[下一篇](/teaching-topics/ch4-p16-candidate/)給出伽瑪分配與貝塔分配之間的關係: 兩個獨立的伽瑪變數，其中一個除以兩者之和會服從貝塔分配，兩者之和則仍是伽瑪分配，而且這兩個新的變數彼此獨立。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
