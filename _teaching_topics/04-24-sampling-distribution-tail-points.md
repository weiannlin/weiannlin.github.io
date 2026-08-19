---
title: "常用抽樣分配的尾點關係"
subtitle: "Tail-Point Identities among the Common Sampling Distributions"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 4
topic: 24
order: 424
permalink: /teaching-topics/sampling-distribution-tail-points/
date: 2026-08-15
published: false
excerpt: "四種常用抽樣分配之間既然有分配上的關係，尾點之間也就有相應的恆等關係。本篇的定理列出六條: 前五條是等式，依序把 $t$ 分配與 $\\mathcal{F}$ 分配、$t$ 分配與標準常態分配、標準常態分配與卡方分配及 $\\mathcal{F}$ 分配、$\\mathcal{F}$ 分配與其倒數、卡方分配與 $\\mathcal{F}$ 分配的尾點互相換算；第六條是不等式，說明自由度較大的 $t$ 分配，在相同的右尾機率之下右尾點較小。六條的證明作法一致: 先取一條分配關係，由它指出兩個分配的尾部區域其實描述同一個事件，兩邊的機率因而相等，再把機率的等式改寫成尾點的等式，其中兩個對稱於 $0$ 的分配還要多用一次對稱性，把雙尾的機率折半。證明之中另有四處以圖形說明尾機率區塊在平方或取倒數之後如何互相對應。"
---

[上一篇](/teaching-topics/sampling-distribution-relationships/)列出四種常用抽樣分配彼此之間的分配關係，並且以標準常態分配的密度曲線定下右尾點的記法。既然分配與分配之間有關係，兩個分配的尾機率就必須互相對應，尾點自然也就對應起來。本篇要處理的正是這一組尾點關係。

本篇只有一個定理，其中列出六條關係: 前五條是等式，依序把 [$t$ 分配](/teaching-topics/student-t-distribution/#def-t-distribution)與 [$\mathcal{F}$ 分配](/teaching-topics/snedecor-f-distribution/#def-f-distribution)、$t$ 分配與標準常態分配、標準常態分配與[卡方分配](/teaching-topics/chi-squared-distribution/#def-chi-distribution)及 $\mathcal{F}$ 分配、$\mathcal{F}$ 分配與其倒數、卡方分配與 $\mathcal{F}$ 分配的尾點互相換算；第六條是不等式，說明自由度較大的 $t$ 分配，在相同的右尾機率之下右尾點較小。

六條的證明逐條進行，作法一致: 先取出上一篇的一條分配關係，由它指出兩個分配的尾部區域其實描述同一個事件，兩邊的機率因而相等，再把機率的等式改寫成尾點的等式。其中 $t$ 分配與[標準常態分配](/teaching-topics/normal-distribution/#def-normal)這兩個對稱於 $0$ 的分配還要多用一次對稱性，把雙尾的機率折半。證明之中另有四處以圖形說明尾機率區塊在平方或取倒數之後如何互相對應。

## 常用抽樣分配的尾點關係

<div id="thm-sampling-tail-relations" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 4.28 (常用抽樣分配的尾點關係)</div>

(1)
{: .topic-paren-item}

$$
t_{\frac{\alpha}{2}}(\nu)=\sqrt{\mathcal{F}_{\alpha}(1,\nu)}
$$

(2)
{: .topic-paren-item}

$$
t_{\alpha}(\infty)=z_{\sssig \alpha}
$$

(3)
{: .topic-paren-item}

$$
z_{\frac{\alpha}{2}}=\sqrt{\chi^{2}_{\alpha}(1)}=\sqrt{\mathcal{F}_{\alpha}(1,\infty)}
$$

(4)
{: .topic-paren-item}

$$
\mathcal{F}_{\alpha}(\nu_1,\nu_2)=\frac{1}{\,\mathcal{F}_{1-\alpha}(\nu_2,\nu_1)\,}
$$

(5)
{: .topic-paren-item}

$$
\chi^{2}_{\alpha}(\nu_1)=\nu_1\mathcal{F}_{\alpha}(\nu_1,\infty)
$$

(6)
{: .topic-paren-item}

$$
t_{\alpha}(\nu_1)>t_{\alpha}(\nu_2),\ \forall\,0<\nu_1<\nu_2
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.**

(1) 由[前述關係](/teaching-topics/sampling-distribution-relationships/#thm-sampling-distribution-relations)可知
{: .topic-paren-item}

$$
T\sim t(\nu)\qquad\therefore\, T^{2}\sim\mathcal{F}(1,\nu)
$$

則可知道
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\alpha&=\mathbb{P}\bigl(T^{2}>\mathcal{F}_{\alpha}(1,\nu)\bigr)=\mathbb{P}\bigl(T<-\sqrt{\mathcal{F}_{\alpha}(1,\nu)}\ \text{或}\ T>\sqrt{\mathcal{F}_{\alpha}(1,\nu)}\bigr)\\[0.45em]
&=2\times\mathbb{P}\bigl(T>\sqrt{\mathcal{F}_{\alpha}(1,\nu)}\bigr)\qquad(\,\because t\ \text{分配對稱於}\ 0\,)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\alpha&=\mathbb{P}\bigl(T^{2}>\mathcal{F}_{\alpha}(1,\nu)\bigr)\\[0.45em]
&=\mathbb{P}\bigl(T<-\sqrt{\mathcal{F}_{\alpha}(1,\nu)}\\[0.25em]
&\qquad\ \text{或}\ T>\sqrt{\mathcal{F}_{\alpha}(1,\nu)}\bigr)\\[0.45em]
&=2\times\mathbb{P}\bigl(T>\sqrt{\mathcal{F}_{\alpha}(1,\nu)}\bigr)\\[0.25em]
&\qquad(\,\because t\ \text{分配對稱於}\ 0\,)
\end{aligned}
$$

</div>

由此可得
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
&\Longrightarrow\ \mathbb{P}\bigl(T>\sqrt{\mathcal{F}_{\alpha}(1,\nu)}\bigr)=\frac{\,\alpha\,}{2}\\[0.45em]
&\Longrightarrow\ \sqrt{\mathcal{F}_{\alpha}(1,\nu)}=t_{\frac{\alpha}{2}}(\nu)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\Longrightarrow\ \mathbb{P}\bigl(T>\sqrt{\mathcal{F}_{\alpha}(1,\nu)}\bigr)=\frac{\,\alpha\,}{2}\\[0.45em]
&\Longrightarrow\ \sqrt{\mathcal{F}_{\alpha}(1,\nu)}=t_{\frac{\alpha}{2}}(\nu)
\end{aligned}
$$

</div>

直觀意義上而言，這個恆等關係，可以用下圖來表示:
{: .topic-paren-cont}

<figure id="fig-tail-identity-t-to-f" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/tail-identity-t-to-f.svg" alt="左右兩個面板，中間以一個雙線的向右箭頭相連，箭頭上方標 F = T^2。左面板畫一條左右對稱的鐘形密度曲線，峰頂上方標 t(ν)；橫軸上左右對稱的兩個刻度各由曲線垂直落下一條線到橫軸，軸下由左至右標 −t_{α/2}(ν) 與 t_{α/2}(ν)，中央另有一個刻度，其下另起一排標 0。兩個落點之外、曲線之下到橫軸之間的兩塊尾部以淡紅色填滿，左右對稱。橫軸右端有箭頭，圖中沒有縱軸。右面板畫一條由左上往右下一路遞減的密度曲線，左端在圖頂截斷，右端貼近橫軸，曲線右上方標 F(1, ν)；橫軸靠右處有一個刻度，由曲線垂直落下一條線到橫軸，軸下標 F_α(1, ν)，該刻度以右、曲線之下到橫軸之間的一塊尾部以淡紅色填滿。橫軸原點處另有一個刻度，其下另起一排標 0，該處並立起一條縱軸，兩軸末端都有箭頭。">
  <figcaption><span class="topic-figure__label">Fig. 4.11.</span> 左圖的兩塊對稱尾機率平方之後落在同一個位置，疊起來正好是右圖的那一塊右尾機率，兩邊的尾點因此滿足 <span class="text-nowrap">$t_{\frac{\alpha}{2}}(\nu)=\sqrt{\mathcal{F}_{\alpha}(1,\nu)}$。</span></figcaption>
</figure>

這個恆等式在上圖中的直觀意義是，左圖的兩個對稱的尾機率區塊，在平方過後都會位在正的部分，而這兩部分平方之後的位置是相同的，疊加之後，正好是右圖的右尾機率。
{: .topic-paren-cont}

(2) 在 $t$ 分配的小節中我們已經說明，若 <span class="text-nowrap">$T\sim t(\nu)$，</span>則
{: .topic-paren-item}

$$
T\xrightarrow[\ \nu\to\infty\ ]{\ \mathrm{d}\ }Z\sim\mathcal{N}(0,1)
$$

故
{: .topic-paren-cont}

$$
t_{\alpha}(\infty)=z_{\alpha}
$$

(3) 在卡方分配的小節中我們已知
{: .topic-paren-item}

$$
Z\sim\mathcal{N}(0,1)\qquad\therefore\, Z^{2}\sim\chi^{2}(1)
$$

則可知道
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\alpha&=\mathbb{P}\bigl(Z^{2}>\chi^{2}_{\alpha}(1)\bigr)=\mathbb{P}\bigl(Z<-\sqrt{\chi^{2}_{\alpha}(1)}\ \text{或}\ Z>\sqrt{\chi^{2}_{\alpha}(1)}\bigr)\\[0.45em]
&=2\times\mathbb{P}\bigl(Z>\sqrt{\chi^{2}_{\alpha}(1)}\bigr)\qquad(\,\because\ \text{標準分配對稱於}\ 0\,)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\alpha&=\mathbb{P}\bigl(Z^{2}>\chi^{2}_{\alpha}(1)\bigr)\\[0.45em]
&=\mathbb{P}\bigl(Z<-\sqrt{\chi^{2}_{\alpha}(1)}\\[0.25em]
&\qquad\ \text{或}\ Z>\sqrt{\chi^{2}_{\alpha}(1)}\bigr)\\[0.45em]
&=2\times\mathbb{P}\bigl(Z>\sqrt{\chi^{2}_{\alpha}(1)}\bigr)\\[0.25em]
&\qquad(\,\because\ \text{標準分配對稱於}\ 0\,)
\end{aligned}
$$

</div>

由此可得
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
&\Longrightarrow\ \mathbb{P}\bigl(Z>\sqrt{\chi^{2}_{\alpha}(1)}\bigr)=\frac{\,\alpha\,}{2}\\[0.45em]
&\Longrightarrow\ \sqrt{\chi^{2}_{\alpha}(1)}=z_{\frac{\alpha}{2}}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\Longrightarrow\ \mathbb{P}\bigl(Z>\sqrt{\chi^{2}_{\alpha}(1)}\bigr)=\frac{\,\alpha\,}{2}\\[0.45em]
&\Longrightarrow\ \sqrt{\chi^{2}_{\alpha}(1)}=z_{\frac{\alpha}{2}}
\end{aligned}
$$

</div>

直觀言，這個恆等關係與 (1) 很類似，我們將 $z_{\frac{\alpha}{2}}=\sqrt{\chi^{2}_{\alpha}(1)}$ 的部分用下圖來表示:
{: .topic-paren-cont}

<figure id="fig-tail-identity-z-to-chisq" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/tail-identity-z-to-chisq.svg" alt="左右兩個面板，中間以一個雙線的向右箭頭相連，箭頭上方標 X = Z^2。左面板畫一條左右對稱的鐘形密度曲線，峰頂上方標 N(0, 1)；橫軸上左右對稱的兩個刻度各由曲線垂直落下一條線到橫軸，軸下由左至右標 −z_{α/2} 與 z_{α/2}，中央另有一個刻度，其下另起一排標 0。兩個落點之外、曲線之下到橫軸之間的兩塊尾部以淡紅色填滿，左右對稱。橫軸右端有箭頭，圖中沒有縱軸。右面板畫一條由左上往右下一路遞減的密度曲線，左端在圖頂截斷，右端貼近橫軸，曲線右上方標 χ^2(1)；橫軸靠右處有一個刻度，由曲線垂直落下一條線到橫軸，軸下標 χ^2_α(1)，該刻度以右、曲線之下到橫軸之間的一塊尾部以淡紅色填滿。橫軸原點處另有一個刻度，其下另起一排標 0，該處並立起一條縱軸，兩軸末端都有箭頭。">
  <figcaption><span class="topic-figure__label">Fig. 4.12.</span> 左圖的兩塊對稱尾機率平方之後落在同一個位置，疊起來正好是右圖的那一塊右尾機率，兩邊的尾點因此滿足 <span class="text-nowrap">$z_{\frac{\alpha}{2}}=\sqrt{\chi^{2}_{\alpha}(1)}$。</span></figcaption>
</figure>

此式與 $t$ 和 $\mathcal{F}$ 的關係完全相同，左圖的兩個對稱的尾機率區塊，在平方過後都會位在正的部分，而這兩部分平方之後的位置是相同的，疊加之後，正好是右圖的右尾機率。
{: .topic-paren-cont}

又由前述關係已知
{: .topic-paren-cont}

$$
F\sim\mathcal{F}(\nu_1,\infty)\qquad\therefore\, \nu_1F\sim\chi^{2}(\nu_1)
$$

此處令 <span class="text-nowrap">$\nu_1=1$，</span>則可得到 $\chi^{2}(1)$ 分配就是 $\mathcal{F}(1,\infty)$ 分配，因此
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\chi^{2}_{\alpha}(1)=\mathcal{F}_{\alpha}(1,\infty)\qquad\therefore\, \sqrt{\chi^{2}_{\alpha}(1)}=\sqrt{\mathcal{F}_{\alpha}(1,\infty)}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\chi^{2}_{\alpha}(1)=\mathcal{F}_{\alpha}(1,\infty)\qquad\therefore\, \sqrt{\chi^{2}_{\alpha}(1)}=\sqrt{\mathcal{F}_{\alpha}(1,\infty)}
$$

</div>

由此可得
{: .topic-paren-cont}

$$
z_{\frac{\alpha}{2}}=\sqrt{\chi^{2}_{\alpha}(1)}=\sqrt{\mathcal{F}_{\alpha}(1,\infty)}
$$

(4) 由前述關係可知
{: .topic-paren-item}

$$
F\sim\mathcal{F}(\nu_1,\nu_2)\qquad\therefore\, \frac{1}{\,F\,}\sim\mathcal{F}(\nu_2,\nu_1)
$$

則可知道
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\alpha=\mathbb{P}\bigl(F>\mathcal{F}_{\alpha}(\nu_1,\nu_2)\bigr)=\mathbb{P}\biggl(\frac{1}{\,F\,}<\frac{1}{\,\mathcal{F}_{\alpha}(\nu_1,\nu_2)\,}\biggr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\alpha&=\mathbb{P}\bigl(F>\mathcal{F}_{\alpha}(\nu_1,\nu_2)\bigr)\\[0.45em]
&=\mathbb{P}\biggl(\frac{1}{\,F\,}<\frac{1}{\,\mathcal{F}_{\alpha}(\nu_1,\nu_2)\,}\biggr)
\end{aligned}
$$

</div>

又
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\frac{1}{\,F\,}\sim\mathcal{F}(\nu_2,\nu_1)\qquad\therefore\, \frac{1}{\,\mathcal{F}_{\alpha}(\nu_1,\nu_2)\,}=\mathcal{F}_{1-\alpha}(\nu_2,\nu_1)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\frac{1}{\,F\,}\sim\mathcal{F}(\nu_2,\nu_1)\qquad\therefore\, \frac{1}{\,\mathcal{F}_{\alpha}(\nu_1,\nu_2)\,}=\mathcal{F}_{1-\alpha}(\nu_2,\nu_1)
$$

</div>

從圖形上解釋上述的關係，即如下圖表示:
{: .topic-paren-cont}

<figure id="fig-tail-identity-f-reciprocal" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/tail-identity-f-reciprocal.svg" alt="左右並排兩個面板，各畫一條由左端零升起、在偏左處到達高峰、再向右緩降並拖出長尾的曲線，兩個面板的橫軸與高度比例尺完全相同。左面板的曲線右上方標 F 括號 10 逗號 50，橫軸左端標 0，靠右另有一個刻度標 F 下標 α 括號 10 逗號 50，該刻度之上有一條細的垂直虛線接到曲線，虛線右側、曲線之下到橫軸之間的一塊以淡紅色填滿，這一塊又長又扁。右面板的曲線右上方標 F 括號 50 逗號 10，橫軸上只有一個刻度，標 F 下標 1 減 α 括號 50 逗號 10，位置比左面板的刻度更靠近左端，該處的垂直虛線比左面板的高出許多，填色的一塊改在這條虛線的左側、由橫軸的起點算起，形狀又窄又高。兩個面板之間有一個指向右方的雙線箭頭，箭頭上方標 1 除以 F。">
  <figcaption><span class="topic-figure__label">Fig. 4.13.</span> 取倒數把右尾換成左尾。左面板填色的一塊在界點 $\mathcal{F}_{\alpha}(10,50)$ 的右邊，右面板填色的一塊在界點 $\mathcal{F}_{1-\alpha}(50,10)$ 的左邊，兩塊的機率相同，兩個界點互為倒數。</figcaption>
</figure>

由前述關係可知
{: .topic-paren-cont}

$$
F\sim\mathcal{F}(\nu_1,\infty)\qquad\therefore\, \nu_1F\sim\chi^{2}(\nu_1)
$$

則可知道
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\alpha=\mathbb{P}\bigl(F>\mathcal{F}_{\alpha}(\nu_1,\infty)\bigr)=\mathbb{P}\bigl(\nu_1F>\nu_1\mathcal{F}_{\alpha}(\nu_1,\infty)\bigr)\qquad\therefore\, \nu_1\mathcal{F}_{\alpha}(\nu_1,\infty)=\chi^{2}_{\alpha}(\nu_1)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

<div class="topic-math-follow-before" markdown="1">

$$
\begin{aligned}
\alpha&=\mathbb{P}\bigl(F>\mathcal{F}_{\alpha}(\nu_1,\infty)\bigr)\\[0.45em]
&=\mathbb{P}\bigl(\nu_1F>\nu_1\mathcal{F}_{\alpha}(\nu_1,\infty)\bigr)\\[0.4em]
&\qquad\therefore\, \nu_1\mathcal{F}_{\alpha}(\nu_1,\infty)=\chi^{2}_{\alpha}(\nu_1)
\end{aligned}
$$

</div>

</div>

(5) 由前述關係已知
{: .topic-paren-item}

$$
F\sim\mathcal{F}(\nu_1,\infty)\qquad\therefore\, \nu_1F\sim\chi^{2}(\nu_1)
$$

因此
{: .topic-paren-cont}

$$
\chi^{2}_{\alpha}(\nu_1)=\nu_1\mathcal{F}_{\alpha}(\nu_1,\infty)
$$

(6) 我們將兩種自由度的 $t$ 分配在完全相同的座標尺度上分別畫出來:
{: .topic-paren-item}

<figure id="fig-student-t-same-scale" class="topic-figure topic-figure--wide">
  <img src="/images/teaching-topics/student-t-same-scale.svg" alt="同一組座標軸上疊著兩條左右對稱的鐘形曲線，峰頂落在同一個位置，只以線型分辨，一條實線、一條虛線。虛線那一條峰較高，兩側下降較快；實線那一條峰較低，兩端拖出的尾巴較厚，到圖的兩端仍高於虛線那一條。橫軸兩端都有箭頭，右端標 t，軸上三個刻度由左至右標 0、t 下標 α 括號 10 與 t 下標 α 括號 1，後兩個都在 0 的右邊。t 下標 α 括號 10 之上有一條細的垂直虛線接到虛線那一條曲線，t 下標 α 括號 1 之上另有一條矮得多的垂直虛線接到實線那一條曲線。這兩個刻度右方的曲線之下以淡紅色填滿，前一個刻度到後一個刻度之間填到虛線那一條曲線為止，後一個刻度之後填色的上緣往上一跳，改以實線那一條曲線為界，一路延伸到圖的右端。圖中沒有鉛直軸。右上角的圖例分兩列，上列是一小段實線與 t 括號 1，下列是一小段虛線與 t 括號 10。">
  <figcaption><span class="topic-figure__label">Fig. 4.14.</span> 兩條密度曲線畫在完全相同的座標尺度上，實線那一條的尾巴較厚。兩塊填色的右尾機率相同，虛線那一條的界點 $t_{\alpha}(10)$ 比實線那一條的界點 $t_{\alpha}(1)$ 更靠近 $0$。</figcaption>
</figure>

由上圖中可以發現，自由度較大的 $t$ 分配，在相同的右尾機率下，其右尾點的數值確實較小，也就是
{: .topic-paren-cont}

$$
t_{\alpha}(\nu_1)>t_{\alpha}(\nu_2),\ \forall\,0<\nu_1<\nu_2
$$

原式得證。 <span class="topic-qed">$\square$</span>
</div>

## 本篇小結

[Theorem 4.28](#thm-sampling-tail-relations) 把上一篇的分配關係逐條翻譯成尾點的關係。第 (1) 條由 $T\sim t(\nu)$ 蘊含 $T^{2}\sim\mathcal{F}(1,\nu)$ 出發: $T^{2}$ 落在 $\mathcal{F}_{\alpha}(1,\nu)$ 右邊，等同於 $T$ 落在 $\pm\sqrt{\mathcal{F}_{\alpha}(1,\nu)}$ 之外，而 $t$ 分配對稱於 <span class="text-nowrap">$0$，</span>兩側各佔 <span class="text-nowrap">$\frac{\,\alpha\,}{2}$，</span>因此 $\sqrt{\mathcal{F}_{\alpha}(1,\nu)}$ 正是 $t$ 分配的 $\frac{\,\alpha\,}{2}$ 右尾點。第 (3) 條的作法與此完全相同，只是把 $t$ 換成標準常態、把 $\mathcal{F}(1,\nu)$ 換成 <span class="text-nowrap">$\chi^{2}(1)$；</span>再由 $\mathcal{F}(1,\infty)$ 就是 $\chi^{2}(1)$ 這件事，把 $z_{\frac{\alpha}{2}}$ 同時接上卡方與 $\mathcal{F}$ 兩種尾點。

第 (2) 條不必計算: $t$ 分配的自由度趨於無窮時分配收斂到標準常態分配，尾點自然也跟著相等。第 (4) 條用的是取倒數會把兩個自由度對調這件事: 事件 $F>\mathcal{F}_{\alpha}(\nu_1,\nu_2)$ 與 $\frac{1}{\,F\,}<\frac{1}{\,\mathcal{F}_{\alpha}(\nu_1,\nu_2)\,}$ 是同一個事件，兩者的機率同為 <span class="text-nowrap">$\alpha$；</span>由 $\frac{1}{\,F\,}$ 這一側來看，$\frac{1}{\,\mathcal{F}_{\alpha}(\nu_1,\nu_2)\,}$ 就是 $\mathcal{F}(\nu_2,\nu_1)$ 之下左尾機率為 $\alpha$ 的那個點，也就是 <span class="text-nowrap">$\mathcal{F}_{1-\alpha}(\nu_2,\nu_1)$。</span>第 (5) 條同樣直接: 由 $F\sim\mathcal{F}(\nu_1,\infty)$ 可知 <span class="text-nowrap">$\nu_1F\sim\chi^{2}(\nu_1)$，</span>而不等式 $F>\mathcal{F}_{\alpha}(\nu_1,\infty)$ 兩邊同乘正數 $\nu_1$ 並不改變事件，尾點因而相差 $\nu_1$ 倍。

第 (6) 條是一條不等式。它的證明是把兩種自由度的 $t$ 分配畫在完全相同的座標尺度上直接比較: 自由度較小者的尾巴較厚，同樣的右尾機率 $\alpha$ 所對應的分界點就得往右移，右尾點因而較大。

四張圖之中，前三張分別配在第 (1)、(3) 與 (4) 條上。$t$ 與 $\mathcal{F}$ 那一張、標準常態與卡方那一張，呈現的是同一件事: 平方會把左右兩塊對稱的尾機率折到同一側疊起來，所以雙尾的 $\frac{\,\alpha\,}{2}$ 變成單尾的 <span class="text-nowrap">$\alpha$。</span>$\mathcal{F}$ 與其倒數那一張則呈現右尾與左尾的互換。這六條關係使四種分配的尾點可以互相換算，因此手上只要有其中一種分配的數值表，其餘幾種的尾點都可以推得。

[下一篇](/teaching-topics/sampling-distribution-examples/)以兩道例題演練這些分配關係與尾點關係的用法。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
