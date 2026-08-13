---
title: "多對多函數轉換"
subtitle: "Many-to-Many Transformations of Random Variables"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 24
order: 324
permalink: /teaching-topics/many-to-many-transformations/
date: 2026-08-13
published: false
excerpt: "已知隨機向量 $\\boldsymbol{X}$ 的分配，若令 $\\boldsymbol{Y}=g(\\boldsymbol{X})$ 則 $\\boldsymbol{Y}$ 的分配是什麼？只要 $g(\\cdot)$ 是由 $\\mathbb{R}^n$ 映到 $\\mathbb{R}^m$ 的實值可測向量函數，$\\boldsymbol{Y}$ 就仍然是一個隨機向量。多對多的情形可以由二對二推廣，故本篇只處理二對二: 離散型採 pmf 法，把兩條函數關係當成二元聯立方程式反解，再代回原來的聯合 pmf；連續型採 Jacobian 法，將原變數的 pdf 以新變數表示，再乘上原變數對新變數偏微分所成行列式的絕對值。本篇的五道例題，先以三個伯努利變數示範樣本平均數、中位數與眾數的抽樣分配，接著以 pmf 法反解出兩個變數之和與差的聯合 pmf，再以 Jacobian 法處理三道連續型的轉換，其中包含由均勻與指數分配造出兩個獨立標準常態的作法，以及著名的 Box-Muller 轉換。"
---

[上一篇](/teaching-topics/population-linear-regression/)以母體線性迴歸式，把兩個[隨機變數](/teaching-topics/random-variables-and-pmf/#def-random-variable)之間的線性關係寫成一條直線，並以三道例題示範它的求法。到這裡為止，我們所處理的都是[隨機向量](/teaching-topics/random-vectors-joint-pmf/#def-random-vector)自身的分配、條件分配與由這些分配所導出的各種量數。

本篇要看的是另一件事情。已知 $(X_1,X_2)$ 的聯合分配，令 $Y_1$ 與 $Y_2$ 各為 $X_1$ 與 $X_2$ 的函數，$(Y_1,Y_2)$ 的聯合分配是什麼？我們先說明 $\boldsymbol{Y}=g(\boldsymbol{X})$ 在什麼條件之下仍然是一個隨機向量，接著分離散型與連續型兩個部分，各給出一種求法，最後以五道例題示範。

在[隨機變數的函數轉換](/teaching-topics/one-to-one-transformations/)小節時，我們曾提過隨機變數的轉換。而事實上，我們更常會遇到需要將隨機向量取函數進行轉換的情況，例如**抽樣分配 <span lang="en">(sampling distribution)</span>** 即是在探討**統計量 <span lang="en">(statistics)</span>** 的分配，而**統計量是樣本的函數組合**，所以我們必須先具備求取隨機變數經過函數轉換後的分配的能力，才有辦法進行更深入的探討。

隨機向量的函數轉換的形式如下:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{array}{ccccc}
\boxed{\text{已知}} & \Longrightarrow & \boxed{\text{函數關係}} & \Longrightarrow & \boxed{\text{所求}}\\[0.55em]
\boldsymbol{X}\sim f_{\sssig \boldsymbol{X}}(\boldsymbol{x}) & & \text{令 }\boldsymbol{Y}=g(\boldsymbol{X}) & & \boldsymbol{Y}\sim f_{\sssig \boldsymbol{Y}}(\boldsymbol{y})
\end{array}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{array}{c}
\boxed{\text{已知}}\\[0.3em]
\boldsymbol{X}\sim f_{\sssig \boldsymbol{X}}(\boldsymbol{x})\\[0.55em]
\Downarrow\\[0.55em]
\boxed{\text{函數關係}}\\[0.3em]
\text{令 }\boldsymbol{Y}=g(\boldsymbol{X})\\[0.55em]
\Downarrow\\[0.55em]
\boxed{\text{所求}}\\[0.3em]
\boldsymbol{Y}\sim f_{\sssig \boldsymbol{Y}}(\boldsymbol{y})
\end{array}
$$

</div>

當然，$\boldsymbol{Y}=g(\boldsymbol{X})$ 在此也將是一個隨機向量，此即以下定理。

<div id="thm-measurable-function-of-random-vector" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 3.22 (隨機向量的可測函數, measurable functions of a random vector)</div>

若 $\boldsymbol{X}$ 為一隨機向量，且函數 $g(\cdot)\colon\mathbb{R}^n\to\mathbb{R}^m$ 為一定義在實數上的實值可測向量函數，則 $\boldsymbol{Y}=g(\boldsymbol{X})$ 亦為隨機向量。

</div>

計算 $\boldsymbol{Y}$ 的機率分配之方法眾多，以下分列之。

## 隨機變數的多對多函數轉換

我們在[隨機變數的函數轉換](/teaching-topics/one-to-one-transformations/)小節所介紹的方法，主要是一對一的函數轉換，但若遇到二對二甚至是多對多的函數轉換時，之前的方法在使用上多半會有點問題，因此我們特別介紹多對多的函數轉換該如何處理。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這裡的一對一指的是一個隨機變數是由另一個隨機變數轉換而來，而不是我們在之前所講的一對一函數，這個用法是為了與多個隨機變數是由另外多個隨機變數所共同轉換而來的多對多轉換區隔。

</div>

由於多對多的例子可以輕易由二對二推廣，故在此只介紹二對二的函數轉換，形式如下:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{array}{ccccc}
\boxed{\text{已知}} & \Longrightarrow & \boxed{\text{函數關係}} & \Longrightarrow & \boxed{\text{所求}}\\[0.55em]
(X_1,X_2)\sim f_{\sssig X_1X_2}(x_1,x_2) & & \text{令 }\begin{array}{c} Y_1=g_1(X_1,X_2)\\ Y_2=g_2(X_1,X_2)\end{array} & & (Y_1,Y_2)\sim f_{\sssig Y_1Y_2}(y_1,y_2)
\end{array}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{array}{c}
\boxed{\text{已知}}\\[0.3em]
(X_1,X_2)\sim f_{\sssig X_1X_2}(x_1,x_2)\\[0.55em]
\Downarrow\\[0.55em]
\boxed{\text{函數關係}}\\[0.3em]
\text{令 }\begin{array}{c} Y_1=g_1(X_1,X_2)\\ Y_2=g_2(X_1,X_2)\end{array}\\[0.55em]
\Downarrow\\[0.55em]
\boxed{\text{所求}}\\[0.3em]
(Y_1,Y_2)\sim f_{\sssig Y_1Y_2}(y_1,y_2)
\end{array}
$$

</div>

## 離散型的 pmf 法

在隨機變數為離散的時候，我們採用的做法如下:

**pmf 法**

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
p_{\sssig Y_1Y_2}(y_1,y_2)&=\mathbb{P}(Y_1=y_1,Y_2=y_2)=\mathbb{P}\bigl(g_1(X_1,X_2)=y_1,g_2(X_1,X_2)=y_2\bigr)\\[0.45em]
&=\mathbb{P}\bigl(X_1=h_1(y_1,y_2),X_2=h_2(y_1,y_2)\bigr)=p_{\sssig X_1X_2}\bigl(h_1(y_1,y_2),h_2(y_1,y_2)\bigr)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&p_{\sssig Y_1Y_2}(y_1,y_2)=\mathbb{P}(Y_1=y_1,Y_2=y_2)\\[0.45em]
&\quad =\mathbb{P}\bigl(g_1(X_1,X_2)=y_1,\\[0.2em]
&\qquad\qquad g_2(X_1,X_2)=y_2\bigr)\\[0.45em]
&\quad =\mathbb{P}\bigl(X_1=h_1(y_1,y_2),\\[0.2em]
&\qquad\qquad X_2=h_2(y_1,y_2)\bigr)\\[0.45em]
&\quad =p_{\sssig X_1X_2}\bigl(h_1(y_1,y_2),h_2(y_1,y_2)\bigr)
\end{aligned}
$$

</div>

上述過程中，$g_1(X_1,X_2)=y_1,$ $g_2(X_1,X_2)=y_2$ 變為 $X_1=h_1(y_1,y_2),$ $X_2=h_2(y_1,y_2)$ 事實上就是解二元聯立方程式，將以 $X_1,X_2$ 表示的形式反解為以 $Y_1,Y_2$ 來表示。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

事實上，在多維度對多維度的問題中，[直接列表法](/teaching-topics/one-to-one-transformations/#離散型的函數轉換)雖然還是可以使用，但是多數情況會因為值域結構龐大而導致窮舉的耗時及困難，故 pmf 法以方程式反解的概念反而會是比較簡單的做法。

</div>

## 連續型的 Jacobian 法

而在隨機變數為連續的時候，我們採用的做法如下:

**Jacobian 法**

第一個步驟為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
Y_1=g_1(X_1,X_2),\ Y_2=g_2(X_1,X_2)\ \Longrightarrow\ X_1=h_1(Y_1,Y_2),\ X_2=h_2(Y_1,Y_2)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&Y_1=g_1(X_1,X_2),\ Y_2=g_2(X_1,X_2)\\[0.45em]
&\quad \Longrightarrow X_1=h_1(Y_1,Y_2),\\[0.2em]
&\qquad\qquad X_2=h_2(Y_1,Y_2)
\end{aligned}
$$

</div>

第二個步驟為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig Y_1Y_2}(y_1,y_2)=f_{\sssig X_1X_2}\bigl(h_1(y_1,y_2),h_2(y_1,y_2)\bigr)\bigl\lvert\mathbf{J}\bigr\rvert
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&f_{\sssig Y_1Y_2}(y_1,y_2)\\[0.45em]
&\quad =f_{\sssig X_1X_2}\bigl(h_1(y_1,y_2),h_2(y_1,y_2)\bigr)\bigl\lvert\mathbf{J}\bigr\rvert
\end{aligned}
$$

</div>

其中

$$
\mathbf{J}=\left\lvert
\begin{array}{cc}
\dfrac{\partial h_1(y_1,y_2)}{\partial y_1} & \dfrac{\partial h_1(y_1,y_2)}{\partial y_2}\\[1.1em]
\dfrac{\partial h_2(y_1,y_2)}{\partial y_1} & \dfrac{\partial h_2(y_1,y_2)}{\partial y_2}
\end{array}
\right\rvert
$$

表示體積轉換因子 <span lang="en">(Jacobian)</span>。

事實上，這個 Jacobian 法仍與[一維的 Jacobian 法](/teaching-topics/one-to-one-transformations/#prop-jacobian-method)沒有二致，這在微積分中就是多維度對多維度的變數變換。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

讀者應該把一維的 $\mathbf{J}$ 視為一維度的行列式 (當然，結果並沒有差異)，若這樣來理解 $\mathbf{J}$ 的話，讀者應可發現其實一維的 Jacobian 法只是多維的 Jacobian 法的一個特例而已，其核心精神都是**將原變數的 pdf 以新變數表示，再乘上「原變數對新變數偏微分的行列式 <span lang="en">(determinant)</span>」的絕對值**。

一個特別需要注意的限制是，我們其實並沒有限制隨機變數的多對多轉換，在轉換前後必須是相同的維度，但是若要使用體積轉換因子 Jacobian 來進行轉換的話，轉換前後的維度必須相同，若一定要在不同維度的轉換中使用 Jacobian，其方法我們在下一小節敘述。

</div>

## 抽樣分配與 pmf 法的例題

<div id="ex-three-independent-transformation" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.49</div>

<div lang="en" markdown="1">
Suppose that <span class="text-nowrap">$X_1$,</span> $X_2$ and $X_3$ are independent random variables, each of which records the outcome of a single Bernoulli trial, so that

$$
\mathbb{P}(X_i=0)=\mathbb{P}(X_i=1)=0.5,\quad i=1,2,3
$$

<ol class="topic-list-paren">
  <li>Find the sampling distributions of the sample mean, the sample median and the sample mode of <span class="text-nowrap">$(X_1,X_2,X_3)$.</span></li>
  <li>Evaluate the expected value and the variance of each of the three statistics obtained in (1).</li>
  <li>Find the sampling distributions of the order statistics <span class="text-nowrap">$X_{\sssig (1)}$,</span> $X_{\sssig (2)}$ and $X_{\sssig (3)}$ built from <span class="text-nowrap">$(X_1,X_2,X_3)$.</span></li>
</ol>
</div>

<!-- ref-point: 待第四章的伯努利分配主題發布後，將本題解答中首次出現的
     $\mathrm{Ber}(p=0.5)$ 改為指向該篇的站內連結。 -->

(1) 由題意可知，$X_1,X_2,X_3$ $\overset{\mathrm{iid}}{\sim}$ $\mathrm{Ber}(p=0.5)$
{: .topic-paren-item}

<!-- 版面待量: 本表桌面版八欄, 手機版依 EDITORIAL 二之一與第四節「手機版表格不得需要橫向捲動」
     拆成兩張五欄的表。兩種寬度均尚未實測 (本批不得啟動瀏覽器), 量測時若手機版仍溢位,
     須在 _sass/layout/_topic.scss 另加一個只縮字級與內距、不加灰底列標題欄的表格類別。 -->

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

| prob. | $(X_1,X_2,X_3)$ | $\bar{X}=\frac{1}{3}\sum_{i=1}^{3}X_i$ | $m_e$ | $m_o$ | $X_{\sssig (1)}$ | $X_{\sssig (2)}$ | $X_{\sssig (3)}$ |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| $1/8$ | $(0,0,0)$ | $0$ | $0$ | $0$ | $0$ | $0$ | $0$ |
| $1/8$ | $(0,0,1)$ | $1/3$ | $0$ | $0$ | $0$ | $0$ | $1$ |
| $1/8$ | $(0,1,0)$ | $1/3$ | $0$ | $0$ | $0$ | $0$ | $1$ |
| $1/8$ | $(1,0,0)$ | $1/3$ | $0$ | $0$ | $0$ | $0$ | $1$ |
| $1/8$ | $(0,1,1)$ | $2/3$ | $1$ | $1$ | $0$ | $1$ | $1$ |
| $1/8$ | $(1,0,1)$ | $2/3$ | $1$ | $1$ | $0$ | $1$ | $1$ |
| $1/8$ | $(1,1,0)$ | $2/3$ | $1$ | $1$ | $0$ | $1$ | $1$ |
| $1/8$ | $(1,1,1)$ | $1$ | $1$ | $1$ | $1$ | $1$ | $1$ |

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

| prob. | $(X_1,$<br>$X_2,X_3)$ | $\bar{X}=$<br>$\frac{1}{3}\sum_{i=1}^{3}X_i$ | $m_e$ | $m_o$ |
| :---: | :---: | :---: | :---: | :---: |
| $1/8$ | $(0,0,0)$ | $0$ | $0$ | $0$ |
| $1/8$ | $(0,0,1)$ | $1/3$ | $0$ | $0$ |
| $1/8$ | $(0,1,0)$ | $1/3$ | $0$ | $0$ |
| $1/8$ | $(1,0,0)$ | $1/3$ | $0$ | $0$ |
| $1/8$ | $(0,1,1)$ | $2/3$ | $1$ | $1$ |
| $1/8$ | $(1,0,1)$ | $2/3$ | $1$ | $1$ |
| $1/8$ | $(1,1,0)$ | $2/3$ | $1$ | $1$ |
| $1/8$ | $(1,1,1)$ | $1$ | $1$ | $1$ |

| prob. | $(X_1,$<br>$X_2,X_3)$ | $X_{\sssig (1)}$ | $X_{\sssig (2)}$ | $X_{\sssig (3)}$ |
| :---: | :---: | :---: | :---: | :---: |
| $1/8$ | $(0,0,0)$ | $0$ | $0$ | $0$ |
| $1/8$ | $(0,0,1)$ | $0$ | $0$ | $1$ |
| $1/8$ | $(0,1,0)$ | $0$ | $0$ | $1$ |
| $1/8$ | $(1,0,0)$ | $0$ | $0$ | $1$ |
| $1/8$ | $(0,1,1)$ | $0$ | $1$ | $1$ |
| $1/8$ | $(1,0,1)$ | $0$ | $1$ | $1$ |
| $1/8$ | $(1,1,0)$ | $0$ | $1$ | $1$ |
| $1/8$ | $(1,1,1)$ | $1$ | $1$ | $1$ |

</div>

$$
\begin{gathered}
p_{\sssig \bar{X}}(\bar{x})=\left\lbrace
\begin{array}{c@{\quad}l}
\frac{3}{\,8\,}, & \bar{x}=\frac{1}{\,3\,},\frac{2}{\,3\,}\\[0.7em]
\frac{1}{\,8\,}, & \bar{x}=0,1\\[0.7em]
0, & \text{o.w.}
\end{array}
\right.\\[1.1em]
p_{\sssig m_e}(m_e)=\left\lbrace
\begin{array}{c@{\quad}l}
\frac{1}{\,2\,}, & m_e=0,1\\[0.7em]
0, & \text{o.w.}
\end{array}
\right.\\[1.1em]
p_{\sssig m_o}(m_o)=\left\lbrace
\begin{array}{c@{\quad}l}
\frac{1}{\,2\,}, & m_o=0,1\\[0.7em]
0, & \text{o.w.}
\end{array}
\right.
\end{gathered}
$$

又由上述結果可知
{: .topic-paren-cont}

$$
m_e\sim\mathrm{Ber}(p=0.5),\quad m_o\sim\mathrm{Ber}(p=0.5)
$$

(2) 由 (1) 的結果可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\mathbb{E}(\bar{X})=0\times\frac{1}{\,8\,}+\frac{1}{\,3\,}\times\frac{3}{\,8\,}+\frac{2}{\,3\,}\times\frac{3}{\,8\,}+1\times\frac{1}{\,8\,}=\frac{1}{\,2\,}\\[0.9em]
\mathbb{E}\bigl(\bar{X}^{2}\bigr)=(0)^{2}\times\frac{1}{\,8\,}+\Bigl(\frac{1}{\,3\,}\Bigr)^{2}\times\frac{3}{\,8\,}+\Bigl(\frac{2}{\,3\,}\Bigr)^{2}\times\frac{3}{\,8\,}+(1)^{2}\times\frac{1}{\,8\,}=\frac{1}{\,3\,}\\[0.9em]
\Longrightarrow\ \mathrm{Var}(\bar{X})=\mathbb{E}\bigl(\bar{X}^{2}\bigr)-\bigl[\mathbb{E}(\bar{X})\bigr]^{2}=\frac{1}{\,12\,}
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}(\bar{X})=0\times\frac{1}{\,8\,}+\frac{1}{\,3\,}\times\frac{3}{\,8\,}\\[0.2em]
&\qquad +\frac{2}{\,3\,}\times\frac{3}{\,8\,}+1\times\frac{1}{\,8\,}=\frac{1}{\,2\,}\\[0.9em]
&\mathbb{E}\bigl(\bar{X}^{2}\bigr)=(0)^{2}\times\frac{1}{\,8\,}+\Bigl(\frac{1}{\,3\,}\Bigr)^{2}\times\frac{3}{\,8\,}\\[0.2em]
&\qquad +\Bigl(\frac{2}{\,3\,}\Bigr)^{2}\times\frac{3}{\,8\,}+(1)^{2}\times\frac{1}{\,8\,}=\frac{1}{\,3\,}\\[0.9em]
&\Longrightarrow\ \mathrm{Var}(\bar{X})=\mathbb{E}\bigl(\bar{X}^{2}\bigr)-\bigl[\mathbb{E}(\bar{X})\bigr]^{2}\\[0.2em]
&\qquad =\frac{1}{\,12\,}
\end{aligned}
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\mathbb{E}(m_e)=p=\frac{1}{\,2\,},\quad \mathrm{Var}(m_e)=p(1-p)=\frac{1}{\,4\,}\\[0.9em]
\mathbb{E}(m_o)=p=\frac{1}{\,2\,},\quad \mathrm{Var}(m_o)=p(1-p)=\frac{1}{\,4\,}
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{E}(m_e)=p=\frac{1}{\,2\,}\\[0.7em]
\mathrm{Var}(m_e)=p(1-p)=\frac{1}{\,4\,}\\[0.7em]
\mathbb{E}(m_o)=p=\frac{1}{\,2\,}\\[0.7em]
\mathrm{Var}(m_o)=p(1-p)=\frac{1}{\,4\,}
\end{gathered}
$$

</div>

(3) 由 (1) 的結果中可以發現
{: .topic-paren-item}

$$
\begin{gathered}
p_{\sssig X_{\sssig (1)}}(x_{\sssig (1)})=\left\lbrace
\begin{array}{c@{\quad}l}
\frac{7}{\,8\,}, & x_{\sssig (1)}=0\\[0.7em]
\frac{1}{\,8\,}, & x_{\sssig (1)}=1\\[0.7em]
0, & \text{o.w.}
\end{array}
\right.\\[1.1em]
p_{\sssig X_{\sssig (2)}}(x_{\sssig (2)})=\left\lbrace
\begin{array}{c@{\quad}l}
\frac{1}{\,2\,}, & x_{\sssig (2)}=0\\[0.7em]
\frac{1}{\,2\,}, & x_{\sssig (2)}=1\\[0.7em]
0, & \text{o.w.}
\end{array}
\right.\\[1.1em]
p_{\sssig X_{\sssig (3)}}(x_{\sssig (3)})=\left\lbrace
\begin{array}{c@{\quad}l}
\frac{1}{\,8\,}, & x_{\sssig (3)}=0\\[0.7em]
\frac{7}{\,8\,}, & x_{\sssig (3)}=1\\[0.7em]
0, & \text{o.w.}
\end{array}
\right.
\end{gathered}
$$

也就是
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
X_{\sssig (1)}\sim\mathrm{Ber}\Bigl(p=\frac{1}{\,8\,}\Bigr),\quad X_{\sssig (2)}\sim\mathrm{Ber}\Bigl(p=\frac{1}{\,2\,}\Bigr),\quad X_{\sssig (3)}\sim\mathrm{Ber}\Bigl(p=\frac{7}{\,8\,}\Bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
X_{\sssig (1)}\sim\mathrm{Ber}\Bigl(p=\frac{1}{\,8\,}\Bigr)\\[0.7em]
X_{\sssig (2)}\sim\mathrm{Ber}\Bigl(p=\frac{1}{\,2\,}\Bigr)\\[0.7em]
X_{\sssig (3)}\sim\mathrm{Ber}\Bigl(p=\frac{7}{\,8\,}\Bigr)
\end{gathered}
$$

</div>

</div>

<div id="ex-discrete-joint-transformation" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.50</div>

<div lang="en" markdown="1">
A joint probability mass function

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
f_{\sssig X_1X_2}(x_1,x_2)=p^{x_1+x_2}(1-p)^{4-x_1-x_2}\ \text{ with }\ x_1=0,1,2,\ x_2=0,1,2
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
f_{\sssig X_1X_2}(x_1,x_2)=p^{x_1+x_2}(1-p)^{4-x_1-x_2}\\[0.55em]
\text{with }x_1=0,1,2,\ x_2=0,1,2
\end{gathered}
$$

</div>

Let $Y_1=X_1+X_2$ and <span class="text-nowrap">$Y_2=X_1-X_2$,</span> find the joint pmf of $Y_1$ and <span class="text-nowrap">$Y_2$.</span>
</div>

**pmf 法**

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
p_{\sssig Y_1Y_2}(y_1,y_2)&=\mathbb{P}(Y_1=y_1,Y_2=y_2)=\mathbb{P}(X_1+X_2=y_1,X_1-X_2=y_2)\\[0.45em]
&=\mathbb{P}\Bigl(X_1=\frac{y_1+y_2}{2},X_2=\frac{y_1-y_2}{2}\Bigr)=p_{\sssig X_1X_2}\Bigl(\frac{y_1+y_2}{2},\frac{y_1-y_2}{2}\Bigr)\\[0.45em]
&=p^{\frac{y_1+y_2}{2}+\frac{y_1-y_2}{2}}(1-p)^{4-\frac{y_1+y_2}{2}-\frac{y_1-y_2}{2}}\\[0.45em]
&=p^{y_1}(1-p)^{4-y_1},\quad (y_1,y_2)\in\left\lbrace
\begin{array}{ccc}
(0,0) & (1,-1) & (2,-2)\\[0.3em]
(1,1) & (2,0) & (3,-1)\\[0.3em]
(2,2) & (3,1) & (4,0)
\end{array}
\right\rbrace
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&p_{\sssig Y_1Y_2}(y_1,y_2)=\mathbb{P}(Y_1=y_1,Y_2=y_2)\\[0.45em]
&\quad =\mathbb{P}(X_1+X_2=y_1,X_1-X_2=y_2)\\[0.45em]
&\quad =\mathbb{P}\Bigl(X_1=\frac{y_1+y_2}{2},X_2=\frac{y_1-y_2}{2}\Bigr)\\[0.45em]
&\quad =p_{\sssig X_1X_2}\Bigl(\frac{y_1+y_2}{2},\frac{y_1-y_2}{2}\Bigr)\\[0.45em]
&\quad =p^{\frac{y_1+y_2}{2}+\frac{y_1-y_2}{2}}(1-p)^{4-\frac{y_1+y_2}{2}-\frac{y_1-y_2}{2}}\\[0.45em]
&\quad =p^{y_1}(1-p)^{4-y_1},\\[0.45em]
&\qquad (y_1,y_2)\in\left\lbrace
\begin{array}{ccc}
(0,0) & (1,-1) & (2,-2)\\[0.3em]
(1,1) & (2,0) & (3,-1)\\[0.3em]
(2,2) & (3,1) & (4,0)
\end{array}
\right\rbrace
\end{aligned}
$$

</div>

</div>

## Jacobian 法的例題

<div id="ex-integral-one-variable" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.51</div>

<div lang="en" markdown="1">
Suppose that the continuous random variables $X$ and $Y$ have joint probability density function

$$
f_{\sssig XY}(x,y)=
\left\lbrace
\begin{array}{c@{\quad}l}
24xy, & 0<x<1,\ 0<y<1,\ x+y<1\\[0.5em]
0, & \text{o.w.}
\end{array}
\right.
$$

<ol class="topic-list-paren">
  <li>Determine the joint probability density function of $Z=X+Y$ and <span class="text-nowrap">$W=X$.</span></li>
</ol>
</div>

(1) **Jacobian 法**
{: .topic-paren-item}

第一個步驟為
{: .topic-paren-cont}

$$
Z=X+Y,\ W=X\ \Longrightarrow\ X=W,\ Y=Z-W
$$

第二個步驟為
{: .topic-paren-cont}

<!-- errata-pending: 書稿 mathstatch3.tex 第 4465 行此式寫作
     $f_{\sssig ZW}(z, w) = f_{\sssig X_1X_2}\big(x+y, x)\big|\mathbf{J}\big|$，
     函數下標與代入的引數均有誤: 本題的原變數是 $X$ 與 $Y$ (不是 $X_1,X_2$)，
     且 Jacobian 法要代入的是反解式 $x=h_1(z,w)=w$ 與 $y=h_2(z,w)=z-w$，
     故應為 $f_{\sssig XY}(w,z-w)$。書稿同行的右括號另漏了 `\big` 這個尺寸巨集
     (原文寫作 `\big(x+y, x)`)，屬純排版。
     網頁採正確寫法，待登錄 ERRATA.md，請作者裁定條號。 -->

$$
f_{\sssig ZW}(z,w)=f_{\sssig XY}(w,z-w)\bigl\lvert\mathbf{J}\bigr\rvert
$$

其中
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbf{J}=\left\lvert
\begin{array}{cc}
\dfrac{\partial w}{\partial z} & \dfrac{\partial w}{\partial w}\\[1.1em]
\dfrac{\partial (z-w)}{\partial z} & \dfrac{\partial (z-w)}{\partial w}
\end{array}
\right\rvert
=\left\lvert
\begin{array}{cc}
0 & 1\\[0.4em]
1 & -1
\end{array}
\right\rvert=0-1=-1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbf{J}&=\left\lvert
\begin{array}{cc}
\dfrac{\partial w}{\partial z} & \dfrac{\partial w}{\partial w}\\[1.1em]
\dfrac{\partial (z-w)}{\partial z} & \dfrac{\partial (z-w)}{\partial w}
\end{array}
\right\rvert\\[0.7em]
&=\left\lvert
\begin{array}{cc}
0 & 1\\[0.4em]
1 & -1
\end{array}
\right\rvert=0-1=-1
\end{aligned}
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\Longrightarrow\ f_{\sssig ZW}(z,w)=24w(z-w)\cdot\bigl\lvert-1\bigr\rvert=24w(z-w),\ 0<w<1,\ 0<z<1,\ w<z
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\Longrightarrow\ f_{\sssig ZW}(z,w)=24w(z-w)\cdot\bigl\lvert-1\bigr\rvert\\[0.45em]
&\quad =24w(z-w),\\[0.2em]
&\qquad 0<w<1,\ 0<z<1,\ w<z
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

上述問題中，經過轉換後的範圍需要與原本的範圍相對照，即

$$
\left\lbrace
\begin{array}{c}
0<x<1\\[0.3em]
0<y<1\\[0.3em]
x+y<1
\end{array}
\right.
\Longleftrightarrow
\left\lbrace
\begin{array}{c}
0<w<1\\[0.3em]
0<z-w<1\\[0.3em]
z<1
\end{array}
\right.
\Longleftrightarrow
\left\lbrace
\begin{array}{c}
0<w<1\\[0.3em]
0<z<1\\[0.3em]
w<z
\end{array}
\right.
$$

其圖形如下:

<!-- fig-pending: many-to-many-range
     Fig. 3.20，對應書稿 mathstatch3.tex 第 4484 至 4517 行 (左面板) 與第 4521 至 4552 行
     (右面板) 的兩個 tikzpicture。兩者分別放在一個 .48\textwidth 的 minipage 裡並排
     (第 4483 至 4553 行)，網頁併為一張兩面板的圖 (桌面左右並排，手機改為上下排列)，
     此即 CH3_FIGURE_SPECS.md 第二節所定的「多對多轉換前後的值域對照 (兩面板)」區域圖。

     兩面板共通的部分:
       座標軸為兩條帶箭頭的直線，橫軸自原點畫到 (3.8, 0)、縱軸自原點畫到 (0, 3.8)，
       兩軸都沒有刻度也沒有數值。填色書稿用 gray、opacity 0.2，
       網頁改 journalaccent、透明度 0.15 (CH3_FIGURE_SPECS.md 第一節)。

     左面板 (轉換前，$x$ 與 $y$ 的聯合值域):
       一條實線沿 $y=3-x$ 自 $x=-0.5$ 畫到 $x=3.5$ (書稿的 \def\normaltwo{\x,3-\x})。
       填色區域為 (0, 0)、(0, 3)、(3, 0) 三點所圍的直角三角形，即 $0<x<1$、$0<y<1$
       且 $x+y<1$ 的範圍 (圖上的 3 個單位即數學上的 1)。
       橫軸右端在 (4.3, 0.15) 的下方標 $x$，縱軸上端在 (0, 4.3) 的下方標 $y$。
       在 (2.2, 2.8) 的右側標 $z = x+y = 1$，並自 (1.2, 1.8) 畫一條向左彎的虛線
       指到 (2.2, 2.8)，把該標示連到斜邊上。

     兩面板之間:
       書稿在左面板的 (6, 2) 處放一個 \xRightarrow，箭號上方標「令 $w=x$, $z=x+y$」。
       網頁併圖時把這個箭號放在兩面板之間 (手機改為上下排列時，箭號轉為向下)。

     右面板 (轉換後，$z$ 與 $w$ 的值域):
       兩條實線: 一條沿 $w=z$ 自 $z=-0.5$ 畫到 $z=3.5$，右端標 $z-w = 0$；
       另一條沿 $w=z-3$ 自 $z=2.5$ 畫到 $z=4$，右端標 $z-w = 1$
       (圖上的 3 個單位即數學上的 1，故這兩條線即 $z-w=0$ 與 $z-w=1$)。
       填色區域為 (0, 0)、(3, 3)、(3, 0) 三點所圍的直角三角形，即 $0<w<1$、$0<z<1$
       且 $w<z$ 的範圍。另有一條自 (3, 3) 畫到 (3, 0) 的虛線，即 $z=1$ 這條界線。
       橫軸右端在 (4.15, 0.15) 的下方標 $z$，縱軸上端在 (0, 4.3) 的下方標 $w$。

     繪圖時要裁定的一點: 左面板的實線與右面板的第一條實線都畫到超出填色三角形之外
     (左面板到 $x=3.5$、右面板到 $z=3.5$)，可比照 Fig. 3.1 的既有處置把線收在
     值域範圍之內，屬圖形類的刻意改正，若採用須併入勘誤登錄。

     檔名 many-to-many-range.svg，anchor 取 #fig-many-to-many-range。
     圖畫好之後，本段的「其圖形如下:」改為指向該 anchor 的 Fig. 3.20 連結，並補上 caption；
     本篇小結第三段的「本篇的區域圖」一併改為同一個連結。
-->

</div>

<!-- ref-point: 待第四章的均勻分配、指數分配與常態分配主題發布後，將 Example 3.52 與
     Example 3.53 之中的 $\mathcal{U}(0,2\pi)$、$\mathrm{Exp}(\beta=1)$、$\mathcal{U}(0,1)$
     與標準常態分配 $\mathcal{N}(0,1)$ 各改為指向該處的站內連結。 -->

<div id="ex-uniform-to-exponential" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.52</div>

<div lang="en" markdown="1">
Suppose that $U$ follows the uniform distribution on the interval <span class="text-nowrap">$(0,2\pi)$,</span> that $V$ follows the exponential distribution whose mean is equal to <span class="text-nowrap">$1$,</span> and that $U$ and $V$ are independent. Show that the two random variables

$$
X=\sqrt{2V}\cos(U),\qquad Y=\sqrt{2V}\sin(U)
$$

are independent, each having the standard normal distribution <span class="text-nowrap">$\mathcal{N}(0,1)$.</span>
</div>

由 $U\sim\mathcal{U}(0,2\pi)$ $\indep$ $V\sim\mathrm{Exp}(\beta=1)$ 可知

$$
f_{\sssig UV}(u,v)=\frac{1}{\,2\pi\,}\times e^{-v},\quad 0<u<2\pi,\ v>0
$$

令 $X=\sqrt{2V}\cos(U),$ <span class="text-nowrap">$Y=\sqrt{2V}\sin(U)$，</span>則可知

$$
U=\tan^{-1}\Bigl(\frac{Y}{X}\Bigr),\quad V=\frac{1}{\,2\,}(X^{2}+Y^{2})
$$

且

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbf{J}=\left\lvert
\begin{array}{cc}
\dfrac{\partial u}{\partial x} & \dfrac{\partial u}{\partial y}\\[1.1em]
\dfrac{\partial v}{\partial x} & \dfrac{\partial v}{\partial y}
\end{array}
\right\rvert
=\left\lvert
\begin{array}{cc}
\dfrac{\frac{-y}{x^{2}}}{1+\bigl(\frac{y}{x}\bigr)^{2}} & \dfrac{\frac{1}{x}}{1+\bigl(\frac{y}{x}\bigr)^{2}}\\[1.4em]
x & y
\end{array}
\right\rvert=-1
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbf{J}&=\left\lvert
\begin{array}{cc}
\dfrac{\partial u}{\partial x} & \dfrac{\partial u}{\partial y}\\[1.1em]
\dfrac{\partial v}{\partial x} & \dfrac{\partial v}{\partial y}
\end{array}
\right\rvert\\[0.7em]
&=\left\lvert
\begin{array}{cc}
\dfrac{\frac{-y}{x^{2}}}{1+\bigl(\frac{y}{x}\bigr)^{2}} & \dfrac{\frac{1}{x}}{1+\bigl(\frac{y}{x}\bigr)^{2}}\\[1.4em]
x & y
\end{array}
\right\rvert=-1
\end{aligned}
$$

</div>

則由 Jacobian 法可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f_{\sssig XY}(x,y)&=f_{\sssig UV}\Bigl(\tan^{-1}\Bigl(\frac{y}{x}\Bigr),\frac{1}{\,2\,}(x^{2}+y^{2})\Bigr)\lvert-1\rvert\\[0.45em]
&=\frac{1}{\,2\pi\,}e^{-\frac{\,x^{2}+y^{2}\,}{2}},\ -\infty<x,y<\infty
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&f_{\sssig XY}(x,y)\\[0.45em]
&\quad =f_{\sssig UV}\Bigl(\tan^{-1}\Bigl(\frac{y}{x}\Bigr),\frac{1}{\,2\,}(x^{2}+y^{2})\Bigr)\lvert-1\rvert\\[0.45em]
&\quad =\frac{1}{\,2\pi\,}e^{-\frac{\,x^{2}+y^{2}\,}{2}},\ -\infty<x,y<\infty
\end{aligned}
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\Longrightarrow\ \ f_{\sssig X}(x)=\int_{-\infty}^{\infty}f_{\sssig XY}(x,y)\,dy=\frac{1}{\,\sqrt{2\pi}\,}e^{-\frac{\,x^{2}\,}{2}},\ -\infty<x<\infty\\[0.7em]
f_{\sssig Y}(y)=\int_{-\infty}^{\infty}f_{\sssig XY}(x,y)\,dx=\frac{1}{\,\sqrt{2\pi}\,}e^{-\frac{\,y^{2}\,}{2}},\ -\infty<y<\infty
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ \ &f_{\sssig X}(x)=\int_{-\infty}^{\infty}f_{\sssig XY}(x,y)\,dy\\[0.2em]
&\quad =\frac{1}{\,\sqrt{2\pi}\,}e^{-\frac{\,x^{2}\,}{2}},\ -\infty<x<\infty\\[0.9em]
&f_{\sssig Y}(y)=\int_{-\infty}^{\infty}f_{\sssig XY}(x,y)\,dx\\[0.2em]
&\quad =\frac{1}{\,\sqrt{2\pi}\,}e^{-\frac{\,y^{2}\,}{2}},\ -\infty<y<\infty
\end{aligned}
$$

</div>

並由 $f_{\sssig XY}(x,y)$ $=$ $f_{\sssig X}(x)\,f_{\sssig Y}(y)$ 知道

$$
X,Y\overset{\mathrm{iid}}{\sim}\mathcal{N}(0,1)
$$

</div>

<div id="ex-two-uniform-transformation" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.53 <span lang="en">(Box-Muller transformation)</span></div>

<div lang="en" markdown="1">
If $U_1$ and $U_2$ are random samples from the $\mathcal{U}(0,1)$ distribution, and let

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
Z_1=\sqrt{-2\ln U_1}\cos(2\pi U_2)\quad\text{and}\quad Z_2=\sqrt{-2\ln U_1}\sin(2\pi U_2)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
Z_1=\sqrt{-2\ln U_1}\cos(2\pi U_2)\\[0.55em]
\text{and}\quad Z_2=\sqrt{-2\ln U_1}\sin(2\pi U_2)
\end{gathered}
$$

</div>

show that $Z_1$ and $Z_2$ are independent random variables with a standard normal distribution.
</div>

由 $U_1,U_2\overset{\mathrm{iid}}{\sim}\mathcal{U}(0,1)$ 可知

$$
f_{\sssig U_1U_2}(u_1,u_2)=1\times 1,\quad 0<u_1,u_2<1
$$

令 $Z_1=\sqrt{-2\ln U_1}\cos(2\pi U_2),$ $Z_2=\sqrt{-2\ln U_1}\sin(2\pi U_2)$

則可知

$$
U_1=e^{-\frac{1}{\,2\,}(Z_1^{2}+Z_2^{2})},\quad U_2=\frac{1}{\,2\pi\,}\tan^{-1}\Bigl(\frac{Z_2}{Z_1}\Bigr)
$$

且

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbf{J}=\left\lvert
\begin{array}{cc}
\dfrac{\partial u_1}{\partial z_1} & \dfrac{\partial u_1}{\partial z_2}\\[1.1em]
\dfrac{\partial u_2}{\partial z_1} & \dfrac{\partial u_2}{\partial z_2}
\end{array}
\right\rvert
=\left\lvert
\begin{array}{cc}
-z_1e^{-\frac{1}{\,2\,}(z_1^{2}+z_2^{2})} & -z_2e^{-\frac{1}{\,2\,}(z_1^{2}+z_2^{2})}\\[1.4em]
\dfrac{-\frac{z_2}{z_1^{2}}}{2\pi\bigl[1+\bigl(\frac{z_2}{z_1}\bigr)^{2}\bigr]} & \dfrac{\frac{1}{z_1}}{2\pi\bigl[1+\bigl(\frac{z_2}{z_1}\bigr)^{2}\bigr]}
\end{array}
\right\rvert=-\frac{1}{\,2\pi\,}e^{-\frac{1}{\,2\,}(z_1^{2}+z_2^{2})}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbf{J}&=\left\lvert
\begin{array}{cc}
\dfrac{\partial u_1}{\partial z_1} & \dfrac{\partial u_1}{\partial z_2}\\[1.1em]
\dfrac{\partial u_2}{\partial z_1} & \dfrac{\partial u_2}{\partial z_2}
\end{array}
\right\rvert\\[0.7em]
&=\left\lvert
\begin{array}{cc}
-z_1e^{-\frac{1}{\,2\,}(z_1^{2}+z_2^{2})} & -z_2e^{-\frac{1}{\,2\,}(z_1^{2}+z_2^{2})}\\[1.4em]
\dfrac{-\frac{z_2}{z_1^{2}}}{2\pi\bigl[1+\bigl(\frac{z_2}{z_1}\bigr)^{2}\bigr]} & \dfrac{\frac{1}{z_1}}{2\pi\bigl[1+\bigl(\frac{z_2}{z_1}\bigr)^{2}\bigr]}
\end{array}
\right\rvert\\[0.7em]
&=-\frac{1}{\,2\pi\,}e^{-\frac{1}{\,2\,}(z_1^{2}+z_2^{2})}
\end{aligned}
$$

</div>

由 Jacobian 法可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
f_{\sssig Z_1Z_2}(z_1,z_2)&=f_{\sssig U_1U_2}\Bigl(e^{-\frac{1}{\,2\,}(z_1^{2}+z_2^{2})},\frac{1}{\,2\pi\,}\tan^{-1}\Bigl(\frac{z_2}{z_1}\Bigr)\Bigr)\left\lvert-\frac{1}{\,2\pi\,}e^{-\frac{1}{\,2\,}(z_1^{2}+z_2^{2})}\right\rvert\\[0.45em]
&=\frac{1}{\,2\pi\,}e^{-\frac{\,z_1^{2}+z_2^{2}\,}{2}},\ -\infty<z_1,z_2<\infty
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&f_{\sssig Z_1Z_2}(z_1,z_2)\\[0.45em]
&\quad =f_{\sssig U_1U_2}\Bigl(e^{-\frac{1}{\,2\,}(z_1^{2}+z_2^{2})},\\[0.2em]
&\qquad\qquad \frac{1}{\,2\pi\,}\tan^{-1}\Bigl(\frac{z_2}{z_1}\Bigr)\Bigr)\\[0.2em]
&\qquad\qquad \times\left\lvert-\frac{1}{\,2\pi\,}e^{-\frac{1}{\,2\,}(z_1^{2}+z_2^{2})}\right\rvert\\[0.45em]
&\quad =\frac{1}{\,2\pi\,}e^{-\frac{\,z_1^{2}+z_2^{2}\,}{2}},\ -\infty<z_1,z_2<\infty
\end{aligned}
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\Longrightarrow\ \ f_{\sssig Z_1}(z_1)=\int_{-\infty}^{\infty}f_{\sssig Z_1Z_2}(z_1,z_2)\,dz_2=\frac{1}{\,\sqrt{2\pi}\,}e^{-\frac{\,z_1^{2}\,}{2}},\ -\infty<z_1<\infty\\[0.7em]
f_{\sssig Z_2}(z_2)=\int_{-\infty}^{\infty}f_{\sssig Z_1Z_2}(z_1,z_2)\,dz_1=\frac{1}{\,\sqrt{2\pi}\,}e^{-\frac{\,z_2^{2}\,}{2}},\ -\infty<z_2<\infty
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ \ &f_{\sssig Z_1}(z_1)=\int_{-\infty}^{\infty}f_{\sssig Z_1Z_2}(z_1,z_2)\,dz_2\\[0.2em]
&\quad =\frac{1}{\,\sqrt{2\pi}\,}e^{-\frac{\,z_1^{2}\,}{2}},\ -\infty<z_1<\infty\\[0.9em]
&f_{\sssig Z_2}(z_2)=\int_{-\infty}^{\infty}f_{\sssig Z_1Z_2}(z_1,z_2)\,dz_1\\[0.2em]
&\quad =\frac{1}{\,\sqrt{2\pi}\,}e^{-\frac{\,z_2^{2}\,}{2}},\ -\infty<z_2<\infty
\end{aligned}
$$

</div>

並由 $f_{\sssig Z_1Z_2}(z_1,z_2)$ $=$ $f_{\sssig Z_1}(z_1)\,f_{\sssig Z_2}(z_2)$ 知道

$$
Z_1,Z_2\overset{\mathrm{iid}}{\sim}\mathcal{N}(0,1)
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

本題是著名的 Box-Muller 轉換，這個轉換的用途在於，電腦亂數僅能生成 $\mathcal{U}(0,1)$ 的隨機亂數，而標準常態分配的 cdf 又不具備解析解形式，因而導致[機率積分轉換](/teaching-topics/one-to-one-transformations/#prop-probability-integral-transform) <span lang="en">(probability integral transformation, PIT)</span> 計算不易，導致難以生成標準常態分配的隨機變數值；此時便可透過這個二轉二的特殊轉換，一口氣利用兩個獨立的 $\mathcal{U}(0,1)$ 亂數，得到兩個獨立的標準常態分配亂數。

</div>

## 本篇小結

本篇由隨機向量的函數轉換談起。[Theorem 3.22](#thm-measurable-function-of-random-vector) 說的是，只要 $g(\cdot)$ 是由 $\mathbb{R}^n$ 映到 $\mathbb{R}^m$ 的實值可測向量函數，$\boldsymbol{Y}=g(\boldsymbol{X})$ 就仍然是一個隨機向量，其後才有分配可求。統計量正是樣本的函數組合，抽樣分配所探討的就是統計量的分配，因此求取轉換後的分配，是往後更深入探討的基礎。由於多對多的例子可以由二對二推廣，本篇只處理二對二的情形。

離散型採 pmf 法。把 $Y_1=g_1(X_1,X_2)$ 與 $Y_2=g_2(X_1,X_2)$ 當成二元聯立方程式反解，得到 $X_1=h_1(Y_1,Y_2)$ 與 $X_2=h_2(Y_1,Y_2)$ 這兩條反解式，再把它們代回原本的聯合 pmf。維度一高，直接列表法會因為值域結構龐大而難以窮舉，方程式反解反而簡單。連續型採 Jacobian 法。同樣先反解，再把原變數的 pdf 以新變數表示，並乘上原變數對新變數偏微分所成行列式的絕對值。一維的 Jacobian 法只是它的特例，把一維的 $\mathbf{J}$ 看成一維度的行列式即可；但這個做法要求轉換前後的維度相同。

五道例題分成兩組。[Example 3.49](#ex-three-independent-transformation) 以三個獨立的伯努利變數窮舉八種結果，一次求得樣本平均數、[中位數](/teaching-topics/median/#def-median)、[眾數](/teaching-topics/mode/#def-mode)與三個排序後變數的抽樣分配，並由其中前三個統計量的分配算出各自的[期望值](/teaching-topics/expectation/#def-expectation)與[變異數](/teaching-topics/variance/#def-variance)。[Example 3.50](#ex-discrete-joint-transformation) 是 pmf 法的標準用法。由 $Y_1=X_1+X_2$ 與 $Y_2=X_1-X_2$ 反解得 $X_1=\frac{y_1+y_2}{2}$ 與 $X_2=\frac{y_1-y_2}{2}$ 這兩式，代回之後指數相加相消，聯合 pmf 只剩下 $y_1$ 而與 $y_2$ 無關，但 $(y_1,y_2)$ 的可能取值仍受原本值域的限制。

[Example 3.51](#ex-integral-one-variable) 是 Jacobian 法的第一個例子，其中 $\mathbf{J}=-1$ 這個值說明體積並未被拉伸；本篇的區域圖把轉換前後的值域並列，讀者可以看出原本的三角形在新的兩個變數之下仍是一塊三角形，只是頂點的位置換了。[Example 3.52](#ex-uniform-to-exponential) 與 [Example 3.53](#ex-two-uniform-transformation) 都是由兩個容易生成的變數造出兩個獨立的標準常態。前者取一個 $\mathcal{U}(0,2\pi)$ 與一個平均數為 $1$ 的指數分配，後者取兩個獨立的 $\mathcal{U}(0,1)$ 亂數，兩題的 $\mathbf{J}$ 算完之後，聯合 pdf 都成為兩個標準常態密度的乘積，再各自積分得到兩個邊際 pdf，兩者相乘恰為聯合 pdf，獨立性因而成立。後者即是著名的 Box-Muller 轉換，它讓電腦只憑均勻亂數就能產生標準常態亂數。

[下一篇](/teaching-topics/mgf-method-transformations/)處理轉換前後維度不同的情形，也就是多對一的函數轉換，並介紹在這種情形下特別好用的[動差母函數](/teaching-topics/moment-generating-functions/#def-mgf)法。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
