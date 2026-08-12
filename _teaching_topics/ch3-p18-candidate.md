---
title: "共變異數"
subtitle: "Covariance"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 3
topic: 18
order: 318
permalink: /teaching-topics/ch3-p18-candidate/
date: 2026-08-13
published: false
excerpt: "多數的情況並不允許我們假設兩個變數獨立，此時我們關心的是兩者共同變化的情況，而描述這種共同變化的量數便是共變異數，其定義為兩個變數各自減去期望值之後相乘的期望值。共變異數為正表示兩者較常同方向變化，為負表示較常反方向變化，為零則稱零相關。它與變異數具高度相似性，同樣有一條速算公式 $\\operatorname{Cov}(X,Y)$ $=$ $\\mathbb{E}(XY)-\\mathbb{E}(X)\\mathbb{E}(Y)$ 可以使用，也就是相乘的期望值減去期望值的相乘。本篇列出六款性質並逐一證明，其中最值得注意的是獨立、期望值上獨立與零相關三者之間一連串逆不真的強弱關係，最後兩道例題示範離散型共變異數的計算，其中一道的機率列聯表是著名的「梅花座」，零相關卻不獨立。"
---

[上一篇](/teaching-topics/ch3-p17-candidate/)以 [Definition 3.14](/teaching-topics/ch3-p17-candidate/#def-cross-moment) 給出交叉動差，並以 [Theorem 3.13](/teaching-topics/ch3-p17-candidate/#thm-generate-cross-moment) 說明聯合動差母函數如何生成各階的交叉動差，其中 $n=m=1$ 時所得到的 $\mathbb{E}(XY)$ 這個二階交叉動差，正是本篇所要用到的量。

本篇先以 [Definition 3.16](#def-covariance) 給出共變異數，說明它的正負號各自對應什麼樣的共同變化，並導出一條與變異數十分相似的速算公式；接著以 [Theorem 3.15](#thm-covar-proper) 列出六款性質並逐一證明，途中會看到獨立、期望值上獨立與零相關三者之間一連串逆不真的強弱關係；最後以兩道例題示範離散型共變異數的計算。

前面的小節中，我們已經學到[獨立隨機變數](/teaching-topics/ch3-p09-candidate/#def-indep-r-v)的概念，對分析多元隨機變數來說，若有獨立的假設，則能讓分析變得相當容易，因為在獨立的狀況下，有許多優異的性質可以使用；但事實上，多數的情況並不允許我們假設獨立，這時候若可以先固定其中一個變數，再來探討另一個變數，如此也能達到簡化問題的功效，這個概念即是[條件分配](/teaching-topics/ch3-p07-candidate/)。

然而，更多時候我們關心的是兩個變數「共同變化」的情況，這種描述兩個變數「共同變化」的量數便是**共變異數 <span lang="en">(covariance)</span>** 與**[相關係數](/teaching-topics/ch3-p21-candidate/#def-corr) <span lang="en">(correlation coefficient)</span>**。

## 共變異數的定義

<div id="def-covariance" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 3.16 (共變異數, covariance)</div>

若 $X$ 與 $Y$ 為二隨機變數，且期望值分別為 $\mu_{\sssig X}$ 與 <span class="text-nowrap">$\mu_{\sssig Y}$，</span>則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\sigma_{\sssig XY}=\operatorname{Cov}(X,Y)=\mathbb{E}\bigl[(X-\mu_{\sssig X})(Y-\mu_{\sssig Y})\bigr]
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\sigma_{\sssig XY}=\operatorname{Cov}(X,Y)\\[0.45em]
&\quad =\mathbb{E}\bigl[(X-\mu_{\sssig X})(Y-\mu_{\sssig Y})\bigr]
\end{aligned}
$$

</div>

為 $X$ 與 $Y$ 的**共變異數**

</div>

共變異數描述 $X$ 與 $Y$ 間共同變化的情況，簡單分成以下三種狀況:

(1) 若 <span class="text-nowrap">$\operatorname{Cov}(X,Y)>0$，</span>則表示 $X$ 與 $Y$ 比較常**一起高於或一起小於期望值**，即 $X$ 與 $Y$ 較常「同方向變化」，稱 $X$ 與 $Y$ **正相關 <span lang="en">(positively correlated)</span>**。
{: .topic-paren-item}

(2) 若 <span class="text-nowrap">$\operatorname{Cov}(X,Y)<0$，</span>則表示 $X$ 與 $Y$ 較常**一個高於但一個小於期望值**，即 $X$ 與 $Y$ 較常「反方向變化」，稱 $X$ 與 $Y$ **負相關 <span lang="en">(negatively correlated)</span>**。
{: .topic-paren-item}

(3) 若 <span class="text-nowrap">$\operatorname{Cov}(X,Y)=0$，</span>則表示 $X$ 與 $Y$ 並不同向變化也不反向變化，稱 $X$ 與 $Y$ **零相關 <span lang="en">(uncorrelated)</span>**。
{: .topic-paren-item}

共變異數有一個與變異數很像的速算公式如下:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\operatorname{Cov}(X,Y)&=\mathbb{E}\bigl[(X-\mu_{\sssig X})(Y-\mu_{\sssig Y})\bigr]=\mathbb{E}\bigl(XY-X\mu_{\sssig Y}-Y\mu_{\sssig X}+\mu_{\sssig X}\mu_{\sssig Y}\bigr)\\[0.45em]
&=\mathbb{E}(XY)-\mathbb{E}(X)\mu_{\sssig Y}-\mathbb{E}(Y)\mu_{\sssig X}+\mu_{\sssig X}\mu_{\sssig Y}=\mathbb{E}(XY)-\mathbb{E}(X)\mathbb{E}(Y)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\operatorname{Cov}(X,Y)=\mathbb{E}\bigl[(X-\mu_{\sssig X})(Y-\mu_{\sssig Y})\bigr]\\[0.45em]
&\quad =\mathbb{E}\bigl(XY-X\mu_{\sssig Y}-Y\mu_{\sssig X}+\mu_{\sssig X}\mu_{\sssig Y}\bigr)\\[0.45em]
&\quad =\mathbb{E}(XY)-\mathbb{E}(X)\mu_{\sssig Y}-\mathbb{E}(Y)\mu_{\sssig X}\\[0.3em]
&\qquad +\mu_{\sssig X}\mu_{\sssig Y}\\[0.45em]
&\quad =\mathbb{E}(XY)-\mathbb{E}(X)\mathbb{E}(Y)
\end{aligned}
$$

</div>

$$
\Longrightarrow\quad\boxed{\ \operatorname{Cov}(X,Y)=\mathbb{E}(XY)-\mathbb{E}(X)\mathbb{E}(Y)\ }
$$

此即，**相乘的期望值減去期望值的相乘**。

## 共變異數的性質

讀者應該已經發現了，共變異數與變異數間具高度相似性，見下列定理。

<div id="thm-covar-proper" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 3.15 (共變異數的性質, covariance properties)</div>

若 $X$ 與 $Y$ 為二隨機變數，$a, b, c, d$ 為任意常數，則

<ol class="topic-list-paren">
  <li>
  若 <span class="text-nowrap">$X\indep Y$，</span>則
  $$
  \operatorname{Cov}(X,Y)=0
  $$
  </li>
  <li>
  $$
  \operatorname{Cov}(X,a)=0
  $$
  </li>
  <li>
  $$
  \operatorname{Cov}(X,X)=\mathrm{Var}(X)
  $$
  </li>
  <li>
  $$
  \operatorname{Cov}\bigl(aX+c,\,bY+d\bigr)=ab\,\operatorname{Cov}\bigl(X,Y\bigr)
  $$
  </li>
  <li>
  $$
  \operatorname{Cov}(X,Y)=\operatorname{Cov}(Y,X)
  $$
  </li>
  <li>
  若 $\mathbb{E}(Y\mid X)=\mathbb{E}(Y)$ 則
  $$
  \operatorname{Cov}(X,Y)=0
  $$
  </li>
</ol>

</div>

<div class="topic-proof" markdown="1">
**Proof.**

(1) 若 <span class="text-nowrap">$X\indep Y$，</span>則由 [Theorem 3.6](/teaching-topics/ch3-p10-candidate/#thm-indep-exp) 可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(XY)=\mathbb{E}(X)\mathbb{E}(Y)\Longrightarrow\operatorname{Cov}(X,Y)=\mathbb{E}(XY)-\mathbb{E}(X)\mathbb{E}(Y)=0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}(XY)=\mathbb{E}(X)\mathbb{E}(Y)\\[0.45em]
&\quad \Longrightarrow\operatorname{Cov}(X,Y)\\[0.3em]
&\qquad =\mathbb{E}(XY)-\mathbb{E}(X)\mathbb{E}(Y)=0
\end{aligned}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這是一個逆不真的敘述，即獨立是一個比零相關更「強 (strong)」的性質，也就是**獨立能保證零相關，但零相關未必獨立**。

</div>

(2)
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\operatorname{Cov}(X,a)=\mathbb{E}(X\,a)-\mathbb{E}(X)\mathbb{E}(a)=a\mathbb{E}(X)-a\mathbb{E}(X)=0
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\operatorname{Cov}(X,a)=\mathbb{E}(X\,a)-\mathbb{E}(X)\mathbb{E}(a)\\[0.45em]
&\quad =a\mathbb{E}(X)-a\mathbb{E}(X)=0
\end{aligned}
$$

</div>

(3)
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\operatorname{Cov}(X,X)=\mathbb{E}(X\cdot X)-\mathbb{E}(X)\mathbb{E}(X)=\mathbb{E}\bigl(X^{2}\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}=\mathrm{Var}(X)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\operatorname{Cov}(X,X)=\mathbb{E}(X\cdot X)-\mathbb{E}(X)\mathbb{E}(X)\\[0.45em]
&\quad =\mathbb{E}\bigl(X^{2}\bigr)-\bigl[\mathbb{E}(X)\bigr]^{2}=\mathrm{Var}(X)
\end{aligned}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

由於共變異數與變異數的相似性，故往後我們會認為**共變異數可以被當成多元隨機變數間的變異數**，此即**[共變異數矩陣](/teaching-topics/ch3-p20-candidate/#def-covar-matrix) <span lang="en">(covariance matrix)</span>** 的概念，稍後我們便會談到這個性質。

</div>

(4) 由共變異數的定義可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\operatorname{Cov}(aX+c,\,bY+d)&=\mathbb{E}\bigl[(aX+c)(bY+d)\bigr]-\mathbb{E}(aX+c)\,\mathbb{E}(bY+d)\\[0.45em]
&=\mathbb{E}\bigl(aX\,bY+cbY+aXd+cd\bigr)-\bigl[\,a\,\mathbb{E}(X)+c\,\bigr]\bigl[\,b\,\mathbb{E}(Y)+d\,\bigr]\\[0.45em]
&=\Bigl[\,ab\,\mathbb{E}(XY)+bc\,\mathbb{E}(Y)+ad\,\mathbb{E}(X)+cd\,\Bigr]\\[0.3em]
&\quad -\Bigl[\,ab\,\mathbb{E}(X)\mathbb{E}(Y)+bc\,\mathbb{E}(Y)+ad\,\mathbb{E}(X)+cd\,\Bigr]\\[0.45em]
&=ab\,\mathbb{E}(XY)-ab\,\mathbb{E}(X)\mathbb{E}(Y)=ab\,\operatorname{Cov}(X,Y)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\operatorname{Cov}(aX+c,\,bY+d)\\[0.45em]
&\quad =\mathbb{E}\bigl[(aX+c)(bY+d)\bigr]\\[0.3em]
&\qquad -\mathbb{E}(aX+c)\,\mathbb{E}(bY+d)\\[0.45em]
&\quad =\mathbb{E}\bigl(aX\,bY+cbY+aXd+cd\bigr)\\[0.3em]
&\qquad -\bigl[\,a\,\mathbb{E}(X)+c\,\bigr]\bigl[\,b\,\mathbb{E}(Y)+d\,\bigr]\\[0.45em]
&\quad =\Bigl[\,ab\,\mathbb{E}(XY)+bc\,\mathbb{E}(Y)\\[0.3em]
&\qquad\quad +ad\,\mathbb{E}(X)+cd\,\Bigr]\\[0.3em]
&\qquad -\Bigl[\,ab\,\mathbb{E}(X)\mathbb{E}(Y)+bc\,\mathbb{E}(Y)\\[0.3em]
&\qquad\quad +ad\,\mathbb{E}(X)+cd\,\Bigr]\\[0.45em]
&\quad =ab\,\mathbb{E}(XY)-ab\,\mathbb{E}(X)\mathbb{E}(Y)\\[0.45em]
&\quad =ab\,\operatorname{Cov}(X,Y)
\end{aligned}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

二變數間的共同變化的「趨勢」應不會受到平移影響，此即變異數也具備的**平移不變性**。

另一個特色是，**共變異數允許有負值**，這是變異數與標準差所不具有的性質，因此不需要平方伸縮或絕對值伸縮，而是將對一個變數的伸縮**原封不動地反映在其共變異數上**。

此外，在這個性質的證明過程中亦可以看出來，共變異數的運算具有分配律。

我們由性質 (4) 可以延伸出底下這個性質: 若 $X_1,\ldots,X_n$ 與 $Y_1,\ldots,Y_m$ 為隨機變數，$a_1,\ldots,a_n$ 與 $b_1,\ldots,b_m$ 為常數，則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\operatorname{Cov}\biggl(\sum_{i=1}^{n}a_i\,X_i+c,\ \sum_{j=1}^{m}b_j\,Y_j+d\biggr)=\sum_{i=1}^{n}\sum_{j=1}^{m}a_ib_j\,\operatorname{Cov}(X_i,Y_j)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\operatorname{Cov}\biggl(\sum_{i=1}^{n}a_i\,X_i+c,\ \sum_{j=1}^{m}b_j\,Y_j+d\biggr)\\[0.45em]
&\quad =\sum_{i=1}^{n}\sum_{j=1}^{m}a_ib_j\,\operatorname{Cov}(X_i,Y_j)
\end{aligned}
$$

</div>

讀者只要掌握**逐項對應**的特色，應就能參透這個性質。

</div>

(5)
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\operatorname{Cov}(X,Y)=\mathbb{E}(XY)-\mathbb{E}(X)\mathbb{E}(Y)=\mathbb{E}(YX)-\mathbb{E}(Y)\mathbb{E}(X)=\operatorname{Cov}(Y,X)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\operatorname{Cov}(X,Y)=\mathbb{E}(XY)-\mathbb{E}(X)\mathbb{E}(Y)\\[0.45em]
&\quad =\mathbb{E}(YX)-\mathbb{E}(Y)\mathbb{E}(X)=\operatorname{Cov}(Y,X)
\end{aligned}
$$

</div>

(6) 若 <span class="text-nowrap">$\mathbb{E}(Y\mid X)=\mathbb{E}(Y)$，</span>則依照共變異數的定義及[雙重期望值定理](/teaching-topics/ch3-p12-candidate/#thm-double-expectation)可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\operatorname{Cov}(X,Y)&=\mathbb{E}(XY)-\mathbb{E}(X)\mathbb{E}(Y)=\mathbb{E}\bigl[\mathbb{E}(XY\mid X)\bigr]-\mathbb{E}(X)\mathbb{E}\bigl[\mathbb{E}(Y\mid X)\bigr]\\[0.45em]
&=\mathbb{E}\bigl[X\,\mathbb{E}(Y\mid X)\bigr]-\mathbb{E}(X)\mathbb{E}\bigl[\mathbb{E}(Y)\bigr]=\mathbb{E}\bigl[X\,\mathbb{E}(Y)\bigr]-\mathbb{E}(X)\mathbb{E}(Y)=0
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\operatorname{Cov}(X,Y)=\mathbb{E}(XY)-\mathbb{E}(X)\mathbb{E}(Y)\\[0.45em]
&\quad =\mathbb{E}\bigl[\mathbb{E}(XY\mid X)\bigr]-\mathbb{E}(X)\mathbb{E}\bigl[\mathbb{E}(Y\mid X)\bigr]\\[0.45em]
&\quad =\mathbb{E}\bigl[X\,\mathbb{E}(Y\mid X)\bigr]-\mathbb{E}(X)\mathbb{E}\bigl[\mathbb{E}(Y)\bigr]\\[0.45em]
&\quad =\mathbb{E}\bigl[X\,\mathbb{E}(Y)\bigr]-\mathbb{E}(X)\mathbb{E}(Y)=0
\end{aligned}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

$\mathbb{E}(Y\mid X)=\mathbb{E}(Y)$ 在一些地方被稱為**期望值上獨立**，是指**平均而言，$X$ 對 $Y$ 沒有影響**。

<!-- ref-point: 待第三章篇 12 的 Fig. 3.16 (regression-function-surface) 繪出並取得 anchor 之後，將下一段的「立體圖形」改為指向該圖的站內連結。 -->

讀者不妨回想，介紹[雙重期望值定理](/teaching-topics/ch3-p12-candidate/#thm-double-expectation)時的立體圖形中，給定不同的條件，會得到不同的條件分配重心位置 (即條件期望值)，而 $\mathbb{E}(Y\mid X)=\mathbb{E}(Y)$ 即是說明，儘管條件分配可能各有千秋，但是重心位置卻總是相同的；這當然比不上獨立的要求，也就是在每個條件下皆同分配；另一方面，零相關只是指出，$X$ 與 $Y$ 的共同變化關係可以被互相抵銷。

這些條件的強弱關係，可以被歸納成一連串逆不真的敘述，即:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\boxed{\ X\indep Y\quad\Longrightarrow\quad\mathbb{E}(Y\mid X)=\mathbb{E}(Y)\ \bigl(\text{或 }\mathbb{E}(X\mid Y)=\mathbb{E}(X)\bigr)\quad\Longrightarrow\quad\operatorname{Cov}(X,Y)=0\ }
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\boxed{
\begin{gathered}
X\indep Y\\[0.4em]
\Longrightarrow\ \mathbb{E}(Y\mid X)=\mathbb{E}(Y)\\[0.4em]
\bigl(\text{或 }\mathbb{E}(X\mid Y)=\mathbb{E}(X)\bigr)\\[0.4em]
\Longrightarrow\ \operatorname{Cov}(X,Y)=0
\end{gathered}
}
$$

</div>

此外，關於此定理的結果，稍後會再看到一次，是關於共變異數如何透過各種變形的方式計算得到。

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

## 共變異數的計算

<div id="ex-discrete-covariance-table" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.37</div>

<div lang="en" markdown="1">
Suppose that $X$ and $Y$ are discrete random variables whose joint probability distribution is the one recorded in the table below.

| $X\backslash Y$ | $0$ | $1$ | $2$ |
| :---: | :---: | :---: | :---: |
| $0$ | $0.20$ | $0.25$ | $0.05$ |
| $1$ | $0.10$ | $0.30$ | $0.10$ |
{: .topic-table--matrix}

<ol class="topic-list-paren">
  <li>Determine whether $X$ and $Y$ are independent.</li>
  <li>Evaluate <span class="text-nowrap">$\operatorname{Cov}(X,Y)$.</span></li>
</ol>
</div>

(1) 首先先算出邊際分配為
{: .topic-paren-item}

| $X\backslash Y$ | $0$ | $1$ | $2$ | $p_{\sssig X}(x)$ |
| :---: | :---: | :---: | :---: | :---: |
| $0$ | $0.20$ | $0.25$ | $0.05$ | $0.5$ |
| $1$ | $0.10$ | $0.30$ | $0.10$ | $0.5$ |
| $p_{\sssig Y}(y)$ | $0.3$ | $0.55$ | $0.15$ | $1$ |
{: .topic-table--joint-pmf}

則可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
p_{\sssig XY}(0,0)=0.2\neq p_{\sssig X}(0)\,p_{\sssig Y}(0)=0.3\times 0.5=0.15\ \Longrightarrow\ X\not\indep Y
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&p_{\sssig XY}(0,0)=0.2\neq p_{\sssig X}(0)\,p_{\sssig Y}(0)\\[0.45em]
&\quad =0.3\times 0.5=0.15\\[0.45em]
&\quad \Longrightarrow\ X\not\indep Y
\end{aligned}
$$

</div>

(2) 先算出交叉動差與邊際期望值分別為
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(XY)&=\sum_{x=0}^{1}\sum_{y=0}^{2}xy\cdot p_{\sssig XY}(x,y)\\[0.45em]
&=0\cdot 0\cdot 0.2+0\cdot 1\cdot 0.25+0\cdot 2\cdot 0.05+1\cdot 0\cdot 0.1+1\cdot 1\cdot 0.3+1\cdot 2\cdot 0.1=0.5
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}(XY)=\sum_{x=0}^{1}\sum_{y=0}^{2}xy\cdot p_{\sssig XY}(x,y)\\[0.45em]
&\quad =0\cdot 0\cdot 0.2+0\cdot 1\cdot 0.25\\[0.3em]
&\qquad +0\cdot 2\cdot 0.05+1\cdot 0\cdot 0.1\\[0.3em]
&\qquad +1\cdot 1\cdot 0.3+1\cdot 2\cdot 0.1=0.5
\end{aligned}
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\sum_{x=0}^{1}x\cdot p_{\sssig X}(x)=0\cdot 0.5+1\cdot 0.5=0.5\\[0.45em]
\mathbb{E}(Y)&=\sum_{y=0}^{2}y\cdot p_{\sssig Y}(y)=0\cdot 0.3+1\cdot 0.55+2\cdot 0.15=0.85
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}(X)=\sum_{x=0}^{1}x\cdot p_{\sssig X}(x)\\[0.3em]
&\quad =0\cdot 0.5+1\cdot 0.5=0.5\\[0.45em]
&\mathbb{E}(Y)=\sum_{y=0}^{2}y\cdot p_{\sssig Y}(y)\\[0.3em]
&\quad =0\cdot 0.3+1\cdot 0.55+2\cdot 0.15=0.85
\end{aligned}
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\Longrightarrow\ \operatorname{Cov}(X,Y)=\mathbb{E}(XY)-\mathbb{E}(X)\mathbb{E}(Y)=0.5-0.5\times 0.85=0.075
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\Longrightarrow\ \operatorname{Cov}(X,Y)\\[0.3em]
&\quad =\mathbb{E}(XY)-\mathbb{E}(X)\mathbb{E}(Y)\\[0.3em]
&\qquad =0.5-0.5\times 0.85=0.075
\end{aligned}
$$

</div>

</div>

<div id="ex-uncorrelated-not-independent" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 3.38</div>

<div lang="en" markdown="1">
Suppose that $X$ and $Y$ have the joint probability mass function

$$
f_{\sssig XY}(x,y)=0.25
$$

at the four points <span class="text-nowrap">$(x,y)=(1,0)$,</span> <span class="text-nowrap">$(0,1)$,</span> <span class="text-nowrap">$(0,-1)$</span> and <span class="text-nowrap">$(-1,0)$.</span>

<ol class="topic-list-paren">
  <li>Determine whether $X$ and $Y$ are independent.</li>
  <li>Determine whether $X$ and $Y$ are uncorrelated.</li>
</ol>
</div>

(1) 首先先將題目敘述轉為機率列聯表
{: .topic-paren-item}

| $X\backslash Y$ | $-1$ | $0$ | $1$ | $p_{\sssig X}(x)$ |
| :---: | :---: | :---: | :---: | :---: |
| $-1$ | $0$ | $0.25$ | $0$ | $0.25$ |
| $0$ | $0.25$ | $0$ | $0.25$ | $0.5$ |
| $1$ | $0$ | $0.25$ | $0$ | $0.25$ |
| $p_{\sssig Y}(y)$ | $0.25$ | $0.5$ | $0.25$ | $1$ |
{: .topic-table--joint-pmf}

則可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
p_{\sssig XY}(0,0)=0\neq p_{\sssig X}(0)\,p_{\sssig Y}(0)=0.5\times 0.5=0.25\ \Longrightarrow\ X\not\indep Y
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&p_{\sssig XY}(0,0)=0\neq p_{\sssig X}(0)\,p_{\sssig Y}(0)\\[0.45em]
&\quad =0.5\times 0.5=0.25\\[0.45em]
&\quad \Longrightarrow\ X\not\indep Y
\end{aligned}
$$

</div>

(2) 先算出交叉動差與邊際期望值分別為
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(XY)&=\mathop{\sum\sum}\limits_{(x,y)\in\mathcal{R}_{\sssig XY}}xy\cdot p_{\sssig XY}(x,y)\\[0.45em]
&=1\cdot 0\cdot 0.25+0\cdot 1\cdot 0.25+0\cdot (-1)\cdot 0.25+(-1)\cdot 0\cdot 0.25=0
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}(XY)=\mathop{\sum\sum}\limits_{(x,y)\in\mathcal{R}_{\sssig XY}}xy\cdot p_{\sssig XY}(x,y)\\[0.45em]
&\quad =1\cdot 0\cdot 0.25+0\cdot 1\cdot 0.25\\[0.3em]
&\qquad +0\cdot (-1)\cdot 0.25\\[0.3em]
&\qquad +(-1)\cdot 0\cdot 0.25=0
\end{aligned}
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X)&=\sum_{x=-1}^{1}x\cdot p_{\sssig X}(x)=(-1)\cdot 0.25+0\cdot 0.5+1\cdot 0.25=0\\[0.45em]
\mathbb{E}(Y)&=\sum_{y=-1}^{1}y\cdot p_{\sssig Y}(y)=(-1)\cdot 0.25+0\cdot 0.5+1\cdot 0.25=0
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{E}(X)=\sum_{x=-1}^{1}x\cdot p_{\sssig X}(x)\\[0.3em]
&\quad =(-1)\cdot 0.25+0\cdot 0.5+1\cdot 0.25=0\\[0.45em]
&\mathbb{E}(Y)=\sum_{y=-1}^{1}y\cdot p_{\sssig Y}(y)\\[0.3em]
&\quad =(-1)\cdot 0.25+0\cdot 0.5+1\cdot 0.25=0
\end{aligned}
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
&\Longrightarrow\ \operatorname{Cov}(X,Y)=\mathbb{E}(XY)-\mathbb{E}(X)\mathbb{E}(Y)=0-0\times 0=0\\[0.45em]
&\Longrightarrow\ X\ \text{與}\ Y\ \text{零相關}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\Longrightarrow\ \operatorname{Cov}(X,Y)\\[0.3em]
&\quad =\mathbb{E}(XY)-\mathbb{E}(X)\mathbb{E}(Y)\\[0.3em]
&\qquad =0-0\times 0=0\\[0.45em]
&\Longrightarrow\ X\ \text{與}\ Y\ \text{零相關}
\end{aligned}
$$

</div>

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

[Example 3.38](#ex-uncorrelated-not-independent) 的機率列聯表是著名的「梅花座」，是一個零相關但不獨立的經典例子。

</div>

若我們整合了 [Theorem 3.15](#thm-covar-proper) 的 (3) 與 (4)，可以得到一個有趣的結果，見[下列性質](/teaching-topics/ch3-p19-candidate/#thm-covar-proper2)。

## 本篇小結

[Definition 3.16](#def-covariance) 把兩個變數各自減去期望值之後相乘，再取一次期望值，所得的 $\sigma_{\sssig XY}$ 這個量數即為共變異數。它的正負號直接對應兩個變數共同變化的方向: 為正表示兩者較常一起高於或一起小於期望值，也就是同方向變化，稱為正相關；為負表示一個高於而另一個小於期望值，也就是反方向變化，稱為負相關；為零則稱零相關。把定義中的乘積展開再逐項取期望值，可以得到與變異數十分相似的速算公式 $\operatorname{Cov}(X,Y)$ $=$ $\mathbb{E}(XY)-\mathbb{E}(X)\mathbb{E}(Y)$ 這一條，也就是相乘的期望值減去期望值的相乘。

[Theorem 3.15](#thm-covar-proper) 列出六款性質，證明全都由速算公式出發。(1) 用的是 [Theorem 3.6](/teaching-topics/ch3-p10-candidate/#thm-indep-exp) 的獨立時乘積的期望值可以拆開，因此獨立能保證零相關，但這個敘述的逆命題不成立。(2) 與 (5) 分別指出常數與任何隨機變數的共變異數為零，以及共變異數不受兩個變數先後次序的影響。(3) 指出一個變數與自己的共變異數就是變異數，這也是往後把共變異數看成多元隨機變數間的變異數的依據。(4) 說明共變異數具有平移不變性，而伸縮則是原封不動地反映在共變異數上，這與變異數的平方伸縮不同，因為共變異數允許有負值；由 (4) 的證明過程還可以看出共變異數的運算具有分配律，因此兩組線性組合的共變異數可以逐項對應地展開。(6) 用的是[雙重期望值定理](/teaching-topics/ch3-p12-candidate/#thm-double-expectation): 若 <span class="text-nowrap">$\mathbb{E}(Y\mid X)=\mathbb{E}(Y)$，</span>則共變異數為零。這一款與 (1) 合起來，給出獨立、期望值上獨立與零相關三者之間一連串逆不真的強弱關係。

兩道例題示範離散型的算法，作法都是先由聯合機率列聯表求出邊際分配，再分別算出交叉動差與兩個邊際期望值，最後代進速算公式。[Example 3.37](#ex-discrete-covariance-table) 求得的共變異數為 <span class="text-nowrap">$0.075$，</span>兩個變數不獨立。[Example 3.38](#ex-uncorrelated-not-independent) 的兩個邊際期望值與交叉動差都是零，故共變異數為零，但聯合機率並不等於兩個邊際機率的乘積；這張「梅花座」的列聯表就是零相關而不獨立的經典例子。

[下一篇](/teaching-topics/ch3-p19-candidate/)把 [Theorem 3.15](#thm-covar-proper) 的 (3) 與 (4) 整合起來，推導線性組合的變異數。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
