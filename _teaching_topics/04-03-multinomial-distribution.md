---
title: "多項分配"
subtitle: "The Multinomial Distribution"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 4
topic: 3
order: 403
permalink: /lecture-notes/multinomial-distribution/
date: 2026-08-12
published: false
excerpt: "多項分配將二項分配推廣至每次實驗具有 $k$ 個互斥類別的情形。本篇介紹三項式定理與多項分配的定義，並以三項分配為例完整證明邊際二項性、類別合併、負共變異數、條件二項性與相關係數等五款性質。"
---

[上一篇](/lecture-notes/binomial-distribution/)把伯努利實驗重複進行 $n$ 次，只記錄「成功類」的發生次數，得到的模型即為二項分配。若一次實驗的出象並不只有成功與失敗兩類，而是被分成 $k$ 個互斥的類別，那麼各個類別的發生次數所構成的隨機向量，服從的便是本篇的多項分配。

驗證二項分配的機率函數合法時，我們用的是 [Theorem 2.18](/lecture-notes/moment-system/#thm-binomial) 的二項式定理；把類別數由兩類推到三類，所需要的工具便是[三項式定理](#thm-trinomial-thm)。本篇因而先由這個定理談起，再給出多項實驗與多項分配的定義，接著以三項分配為例證明機率函數合法，並一次證完三項分配的五款性質，最後以兩道例題作為演練。

## 三項式定理

<div id="thm-trinomial-thm" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 4.1 (三項式定理, trinomial theorem)</div>

$$
(a+b+c)^{n}=\mathop{\sum\sum}\limits_{\substack{x+y+z=n\\ x,y,z\in\mathbb{Z}^{+}}}\frac{n!}{\,x!y!z!\,}\,a^{x}\,b^{y}\,c^{z}
$$

其中 $a,b,c\in\mathbb{R}$ 且 <span class="text-nowrap">$n\in\mathbb{N}$。</span>

</div>

[三項式定理](#thm-trinomial-thm)是 [Theorem 2.18](/lecture-notes/moment-system/#thm-binomial) 擴展至三項的形式；同理可推廣至一般項數的多項式定理 <span lang="en">(multinomial theorem)</span>，此處不再贅述。

## 多項實驗與多項分配

<div id="def-multinomial-trial" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 4.4 (多項實驗, multinomial trial)</div>

若一隨機實驗滿足以下三點，則我們稱此實驗為**多項實驗 <span lang="en">(multinomial trial)</span>**:

<ol class="topic-list-paren">
  <li>實驗可能的出象 <span lang="en">(outcomes)</span> 可被分為 $k$ 個互斥事件，定義為 <span class="text-nowrap">$A_i,\ i=1,2,\ldots,k$。</span></li>
  <li>每次實驗中，$A_i$ 發生的機率 $\mathbb{P}(A_i)=p_i,\ i=1,2,\ldots,k$ 均為固定值，且 <span class="text-nowrap">$\sum_{i=1}^{k}p_{i}=1$。</span></li>
  <li>實驗與實驗間，彼此獨立。</li>
</ol>

</div>

[上列定義](#def-multinomial-trial)中，若我們額外定義 $X_i,\ i=1,\ldots,k$ 表示在 $n$ 次多項實驗中，出象 $A_i$ 出現的次數，則我們可知 $\sum_{i=1}^{k}X_i$ 必定為 <span class="text-nowrap">$n$，</span>且 $\boldsymbol{X}=\bigl[X_1,\ldots,X_k\bigr]^{\mathrm{T}}$ 服從多項分配 <span lang="en">(multinomial distribution)</span>。

由於全部的出象次數總和必定為 <span class="text-nowrap">$n$，</span>因此在多數時候，我們僅會記錄前 $k-1$ 個出象出現的次數，記為

$$
\boldsymbol{X}=\bigl[X_1,\ldots,X_{k-1}\bigr]^{\mathrm{T}}
$$

則最後一個出象的次數 $X_k$ 便可立刻得到。

<div id="def-multinomial" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 4.5 (多項分配, multinomial distribution)</div>

**適用範圍**:

令 $\boldsymbol{X}=\bigl[X_1,\ldots,X_{k-1}\bigr]^{\mathrm{T}}$ 表進行 **$n$ 次**多項實驗中，前 $k-1$ 個出象的發生次數。

**值域範圍**:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathcal{R}_{\sssig \boldsymbol{X}}=\lbrace\,(x_1,\ldots,x_{k-1})\mid\ &0\leqslant x_i\leqslant n,\ x_i\in\mathbb{Z}^{+},\ i=1,\ldots,k-1,\\[0.45em]
&\text{且}\ 0\leqslant\sum_{i=1}^{k-1}x_i\leqslant n\,\rbrace
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathcal{R}_{\sssig \boldsymbol{X}}=\lbrace\,&(x_1,\ldots,x_{k-1})\mid\\[0.3em]
&0\leqslant x_i\leqslant n,\ x_i\in\mathbb{Z}^{+},\\[0.3em]
&i=1,\ldots,k-1,\\[0.3em]
&\text{且}\ 0\leqslant\sum_{i=1}^{k-1}x_i\leqslant n\,\rbrace
\end{aligned}
$$

</div>

**表示式**:

$$
\boldsymbol{X}=\bigl[X_1,\ldots,X_{k-1}\bigr]^{\mathrm{T}}\sim\mathrm{Multi}(n,\ \boldsymbol{p})
$$

其中 $\boldsymbol{p}=\bigl[p_1,\ldots,p_{k-1}\bigr]^{\mathrm{T}}$

**參數與參數範圍**:

$0<p_i<1,\ i=1,\ldots,k-1$ 為多項實驗中，前 $k-1$ 個出象的發生機率，<span class="text-nowrap">$0<\sum_{i=1}^{k-1}p_i<1$。</span>

**機率函數**:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
p_{\sssig \boldsymbol{X}}(\boldsymbol{x})&=\frac{n!}{\,x_1!x_2!\cdots x_{k-1}!\bigl(n-\sum_{i=1}^{k-1}x_i\bigr)!\,}\,p_1^{x_1}p_2^{x_2}\cdots p_{k-1}^{x_{k-1}}\\[0.45em]
&\qquad \cdot\biggl(1-\sum_{i=1}^{k-1}p_i\biggr)^{n-\sum_{i=1}^{k-1}x_i},\\[0.45em]
&\qquad 0\leqslant x_i\leqslant n,\ i=1,\ldots,k-1,\ 0\leqslant\sum_{i=1}^{k-1}x_i\leqslant n
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig \boldsymbol{X}}(\boldsymbol{x})&=\frac{n!}{\,x_1!x_2!\cdots x_{k-1}!\bigl(n-\sum_{i=1}^{k-1}x_i\bigr)!\,}\\[0.3em]
&\qquad \,p_1^{x_1}p_2^{x_2}\cdots p_{k-1}^{x_{k-1}}\\[0.3em]
&\qquad \cdot\biggl(1-\sum_{i=1}^{k-1}p_i\biggr)^{n-\sum_{i=1}^{k-1}x_i},\\[0.3em]
&\quad 0\leqslant x_i\leqslant n,\ i=1,\ldots,k-1,\\[0.3em]
&\quad 0\leqslant\sum_{i=1}^{k-1}x_i\leqslant n
\end{aligned}
$$

</div>

**邊際期望值、邊際變異數、動差母函數**:

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
\mathbb{E}(X_i)=np_i,\qquad \mathrm{Var}(X_i)=np_i(1-p_i),\\[0.35em]
0<p_i<1,\ i=1,\ldots,k-1\\[0.7em]
M_{\sssig \boldsymbol{X}}(\boldsymbol{t})=\left[\sum_{i=1}^{k-1}p_ie^{t_i}+\biggl(1-\sum_{i=1}^{k-1}p_i\biggr)\right]^{n},\\[0.35em]
\boldsymbol{t}=\bigl[t_1,\ldots,t_{k-1}\bigr]^{\mathrm{T}}\in\mathbb{R}^{k-1}
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathbb{E}(X_i)=np_i,\\[0.35em]
\mathrm{Var}(X_i)=np_i(1-p_i),\\[0.3em]
0<p_i<1,\ i=1,\ldots,k-1
\end{gathered}
$$

$$
\begin{aligned}
M_{\sssig \boldsymbol{X}}(\boldsymbol{t})&=\left[\sum_{i=1}^{k-1}p_ie^{t_i}+\biggl(1-\sum_{i=1}^{k-1}p_i\biggr)\right]^{n},\\[0.3em]
&\quad \boldsymbol{t}=\bigl[t_1,\ldots,t_{k-1}\bigr]^{\mathrm{T}}\in\mathbb{R}^{k-1}
\end{aligned}
$$

</div>

</div>

多項分配有一些地方需要注意:

(1) 當 $k=3$ 時，我們稱其為**三項分配 <span lang="en">(trinomial distribution)</span>**，記為
{: .topic-paren-item}

$$
\boldsymbol{X}=\bigl[X_1,X_2\bigr]^{\mathrm{T}}\sim\mathrm{Tri}(n,\boldsymbol{p})
$$

其中 $\boldsymbol{p}=\bigl[p_1,p_2\bigr]^{\mathrm{T}}$ 且參數滿足
{: .topic-paren-cont}

$$
0<p_1,p_2<1,\qquad 0<p_1+p_2<1
$$

以下皆以三項分配為例，多項版本請讀者自行推廣。
{: .topic-paren-cont}

(2) 我們證明三項分配的機率函數為一個合法的機率函數如下:
{: .topic-paren-item}

<div class="topic-proof" markdown="1">
**Proof.**

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathop{\sum\sum}\limits_{\boldsymbol{x}\in\mathcal{R}_{\sssig \boldsymbol{X}}}p_{\sssig \boldsymbol{X}}(\boldsymbol{x})&=\mathop{\sum\sum}\limits_{\substack{0\leqslant x_1,x_2\leqslant n\\ 0\leqslant x_1+x_2\leqslant n}}\frac{n!}{\,x_1!x_2!(n-x_1-x_2)!\,}\,p_1^{x_1}\,p_2^{x_2}\\[0.45em]
&\qquad \cdot\,(1-p_1-p_2)^{n-x_1-x_2}\\[0.45em]
&=\bigl[p_1+p_2+(1-p_1-p_2)\bigr]^{n}=1
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathop{\sum\sum}\limits_{\boldsymbol{x}\in\mathcal{R}_{\sssig \boldsymbol{X}}}p_{\sssig \boldsymbol{X}}(\boldsymbol{x})\\[0.35em]
&=\mathop{\sum\sum}\limits_{\substack{0\leqslant x_1,x_2\leqslant n\\ 0\leqslant x_1+x_2\leqslant n}}\frac{n!}{\,x_1!x_2!(n-x_1-x_2)!\,}\\[0.3em]
&\qquad\cdot\,p_1^{x_1}\,p_2^{x_2}\cdot\,(1-p_1-p_2)^{n-x_1-x_2}\\[0.3em]
&=\bigl[p_1+p_2+(1-p_1-p_2)\bigr]^{n}=1
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

(3) 三項分配的 mgf 為
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
M_{\sssig X_1X_2}(t_1,t_2)=\left[p_1e^{t_1}+p_2e^{t_2}+(1-p_1-p_2)\right]^{n},\ t_1,t_2\in\mathbb{R}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig X_1X_2}(t_1,t_2)&=\left[p_1e^{t_1}+p_2e^{t_2}+(1-p_1-p_2)\right]^{n},\\[0.3em]
&\quad\ t_1,t_2\in\mathbb{R}
\end{aligned}
$$

</div>

搭配[由聯合動差母函數取得邊際動差母函數的定理](/lecture-notes/cross-moments-joint-mgf/#thm-marginal-mgf)，可推得三項分配的多項重要性質，見[下列定理](#thm-trinomial-properties)。
{: .topic-paren-cont}

## 三項分配的性質

<div id="thm-trinomial-properties" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 4.2 (三項分配的性質, trinomial properties)</div>

若 $\boldsymbol{X}=\bigl[X_1,X_2\bigr]^{\mathrm{T}}\sim\mathrm{Tri}(n,\boldsymbol{p})$ 成立，則我們有

(1)
{: .topic-paren-item}

$$
X_1\sim\mathrm{Bin}(n,p_1),\ \text{且}\ X_2\sim\mathrm{Bin}(n,p_2)
$$

(2) 令 <span class="text-nowrap">$W=X_1+X_2$，</span>則
{: .topic-paren-item}

$$
W=X_1+X_2\sim\mathrm{Bin}(n,p_1+p_2)
$$

(3)
{: .topic-paren-item}

$$
\mathrm{Cov}(X_1,X_2)=-n\,p_1\,p_2
$$

(4)
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{gathered}
(X_1\mid X_2=x_2)\sim\mathrm{Bin}\biggl(n-x_2,\ \frac{p_1}{\,1-p_2\,}\biggr)\\[0.6em]
\text{與}\ (X_2\mid X_1=x_1)\sim\mathrm{Bin}\biggl(n-x_1,\ \frac{p_2}{\,1-p_1\,}\biggr)
\end{gathered}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
(X_1\mid X_2=x_2)\sim\mathrm{Bin}\biggl(n-x_2,\ \frac{p_1}{\,1-p_2\,}\biggr)\\[0.55em]
\text{與}\ (X_2\mid X_1=x_1)\sim\mathrm{Bin}\biggl(n-x_1,\ \frac{p_2}{\,1-p_1\,}\biggr)
\end{gathered}
$$

</div>

(5)
{: .topic-paren-item}

$$
\mathrm{Corr}(X_1,X_2)=-\sqrt{\frac{p_1\,p_2}{\,(1-p_1)\,(1-p_2)\,}}
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.**

(1)
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop topic-math-follow-before" markdown="1">

$$
M_{\sssig X_1}(t_1)=M_{\sssig X_1X_2}(t_1,0)=\bigl[p_1e^{t_1}+1-p_1\bigr]^{n},\ t_1\in\mathbb{R}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile topic-math-follow-before" markdown="1">

$$
\begin{aligned}
M_{\sssig X_1}(t_1)&=M_{\sssig X_1X_2}(t_1,0)\\[0.3em]
&=\bigl[p_1e^{t_1}+1-p_1\bigr]^{n},\ t_1\in\mathbb{R}
\end{aligned}
$$

</div>

<div class="topic-math-follow" markdown="1">

$$
\Longleftrightarrow\ X_1\sim\mathrm{Bin}(n,p_1)
$$

</div>

<div class="topic-math-layout topic-math-layout--desktop topic-math-follow-before" markdown="1">

$$
M_{\sssig X_2}(t_2)=M_{\sssig X_1X_2}(0,t_2)=\bigl[p_2e^{t_2}+1-p_2\bigr]^{n},\ t_2\in\mathbb{R}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile topic-math-follow-before" markdown="1">

$$
\begin{aligned}
M_{\sssig X_2}(t_2)&=M_{\sssig X_1X_2}(0,t_2)\\[0.3em]
&=\bigl[p_2e^{t_2}+1-p_2\bigr]^{n},\ t_2\in\mathbb{R}
\end{aligned}
$$

</div>

<div class="topic-math-follow" markdown="1">

$$
\Longleftrightarrow\ X_2\sim\mathrm{Bin}(n,p_2)
$$

</div>

(2) 令 <span class="text-nowrap">$W=X_1+X_2$，</span>則
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
M_{\sssig W}(t)=M_{\sssig X_1X_2}(t,t)=\left[(p_1+p_2)\,e^{t}+(1-p_1-p_2)\right]^{n},\ t\in\mathbb{R}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
M_{\sssig W}(t)&=M_{\sssig X_1X_2}(t,t)\\[0.3em]
&=\left[(p_1+p_2)\,e^{t}+(1-p_1-p_2)\right]^{n},\\[0.3em]
&\quad\ t\in\mathbb{R}
\end{aligned}
$$

</div>

此即
{: .topic-paren-cont}

$$
W=X_1+X_2\sim\mathrm{Bin}(n,p_1+p_2)
$$

(3) 由 (1)、(2) 可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}(X_1)=n\,p_1\,(1-p_1),\qquad \mathrm{Var}(X_2)=n\,p_2\,(1-p_2)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\mathrm{Var}(X_1)=n\,p_1\,(1-p_1),\\[0.45em]
\mathrm{Var}(X_2)=n\,p_2\,(1-p_2)
\end{gathered}
$$

</div>

又可得
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}(X_1+X_2)=n\,(p_1+p_2)\,(1-p_1-p_2)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(X_1+X_2)&=n\,(p_1+p_2)\,(1-p_1-p_2)
\end{aligned}
$$

</div>

且同時
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Var}(X_1+X_2)=\mathrm{Var}(X_1)+\mathrm{Var}(X_2)+2\,\mathrm{Cov}(X_1,X_2)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Var}(X_1+X_2)&=\mathrm{Var}(X_1)+\mathrm{Var}(X_2)\\[0.3em]
&\qquad +2\,\mathrm{Cov}(X_1,X_2)
\end{aligned}
$$

</div>

故可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Cov}(X_1,X_2)=\frac{1}{\,2\,}\,\bigl[\mathrm{Var}(X_1+X_2)-\mathrm{Var}(X_1)-\mathrm{Var}(X_2)\bigr]=-n\,p_1\,p_2
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Cov}(X_1,X_2)&=\frac{1}{\,2\,}\,\bigl[\mathrm{Var}(X_1+X_2)\\[0.3em]
&\qquad -\mathrm{Var}(X_1)-\mathrm{Var}(X_2)\bigr]\\[0.3em]
&=-n\,p_1\,p_2
\end{aligned}
$$

</div>

(4) 由[條件 pmf 之定義](/lecture-notes/conditional-distributions/#def-conditional-pmf)可知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
p_{\sssig X_1\mid X_2}(x_1\mid x_2)&=\frac{\,p_{\sssig X_1X_2}(x_1,x_2)\,}{p_{\sssig X_2}(x_2)}\\[0.45em]
&=\frac{\,\frac{n!}{\,x_1!x_2!(n-x_1-x_2)!\,}\,p_1^{x_1}\,p_2^{x_2}\,(1-p_1-p_2)^{n-x_1-x_2}\,}{\frac{n!}{\,x_2!(n-x_2)!\,}\,p_2^{x_2}\,(1-p_2)^{n-x_2}}\\[0.45em]
&=\frac{\,(n-x_2)!\,}{\,x_1!(n-x_1-x_2)!\,}\biggl(\frac{p_1}{\,1-p_2\,}\biggr)^{x_1}\\[0.45em]
&\qquad \cdot\biggl(\frac{\,1-p_1-p_2\,}{\,1-p_2\,}\biggr)^{n-x_1-x_2},\\[0.45em]
&\qquad 0\leqslant x_1\leqslant n-x_2,\ x_1\in\mathbb{Z}^{+}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&p_{\sssig X_1\mid X_2}(x_1\mid x_2)\\[0.3em]
&=\frac{\,p_{\sssig X_1X_2}(x_1,x_2)\,}{p_{\sssig X_2}(x_2)}\\[0.3em]
&=\biggl(\frac{n!}{\,x_1!x_2!(n-x_1-x_2)!\,}\,p_1^{x_1}\,p_2^{x_2}\\[0.3em]
&\qquad \cdot\,(1-p_1-p_2)^{n-x_1-x_2}\biggr)\\[0.3em]
&\qquad\Big/\biggl(\frac{n!}{\,x_2!(n-x_2)!\,}\,p_2^{x_2}\,(1-p_2)^{n-x_2}\biggr)\\[0.3em]
&=\frac{\,(n-x_2)!\,}{\,x_1!(n-x_1-x_2)!\,}\biggl(\frac{p_1}{\,1-p_2\,}\biggr)^{x_1}\\[0.3em]
&\qquad \cdot\biggl(\frac{\,1-p_1-p_2\,}{\,1-p_2\,}\biggr)^{n-x_1-x_2},\\[0.3em]
&\quad\ 0\leqslant x_1\leqslant n-x_2,\ x_1\in\mathbb{Z}^{+}
\end{aligned}
$$

</div>

此即
{: .topic-paren-cont}

$$
(X_1\mid X_2=x_2)\sim\mathrm{Bin}\biggl(n-x_2,\ \frac{p_1}{\,1-p_2\,}\biggr)
$$

同理可得
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
p_{\sssig X_2\mid X_1}(x_2\mid x_1)&=\frac{\,p_{\sssig X_1X_2}(x_1,x_2)\,}{p_{\sssig X_1}(x_1)}\\[0.45em]
&=\frac{\,\frac{n!}{\,x_1!x_2!(n-x_1-x_2)!\,}\,p_1^{x_1}\,p_2^{x_2}\,(1-p_1-p_2)^{n-x_1-x_2}\,}{\frac{n!}{\,x_1!(n-x_1)!\,}\,p_1^{x_1}\,(1-p_1)^{n-x_1}}\\[0.45em]
&=\frac{\,(n-x_1)!\,}{\,x_2!(n-x_1-x_2)!\,}\biggl(\frac{p_2}{\,1-p_1\,}\biggr)^{x_2}\\[0.45em]
&\qquad \cdot\biggl(\frac{\,1-p_1-p_2\,}{\,1-p_1\,}\biggr)^{n-x_1-x_2},\\[0.45em]
&\qquad 0\leqslant x_2\leqslant n-x_1,\ x_2\in\mathbb{Z}^{+}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&p_{\sssig X_2\mid X_1}(x_2\mid x_1)\\[0.3em]
&=\frac{\,p_{\sssig X_1X_2}(x_1,x_2)\,}{p_{\sssig X_1}(x_1)}\\[0.3em]
&=\biggl(\frac{n!}{\,x_1!x_2!(n-x_1-x_2)!\,}\,p_1^{x_1}\,p_2^{x_2}\\[0.3em]
&\qquad \cdot\,(1-p_1-p_2)^{n-x_1-x_2}\biggr)\\[0.3em]
&\qquad\Big/\biggl(\frac{n!}{\,x_1!(n-x_1)!\,}\,p_1^{x_1}\,(1-p_1)^{n-x_1}\biggr)\\[0.3em]
&=\frac{\,(n-x_1)!\,}{\,x_2!(n-x_1-x_2)!\,}\biggl(\frac{p_2}{\,1-p_1\,}\biggr)^{x_2}\\[0.3em]
&\qquad \cdot\biggl(\frac{\,1-p_1-p_2\,}{\,1-p_1\,}\biggr)^{n-x_1-x_2},\\[0.3em]
&\quad\ 0\leqslant x_2\leqslant n-x_1,\ x_2\in\mathbb{Z}^{+}
\end{aligned}
$$

</div>

此即
{: .topic-paren-cont}

$$
(X_2\mid X_1=x_1)\sim\mathrm{Bin}\biggl(n-x_1,\ \frac{p_2}{\,1-p_1\,}\biggr)
$$

(5) 由 (4) 知
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X_1\mid X_2=x_2)&=(n-x_2)\biggl(\frac{p_1}{\,1-p_2\,}\biggr)=\frac{n\,p_1}{\,1-p_2\,}-\frac{p_1}{\,1-p_2\,}\,x_2,\\[0.35em]
&\qquad x_2=0,\ldots,n
\end{aligned}
$$

$$
\begin{aligned}
\mathbb{E}(X_2\mid X_1=x_1)&=(n-x_1)\biggl(\frac{p_2}{\,1-p_1\,}\biggr)=\frac{n\,p_2}{\,1-p_1\,}-\frac{p_2}{\,1-p_1\,}\,x_1,\\[0.35em]
&\qquad x_1=0,\ldots,n
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(X_1\mid X_2=x_2)&=(n-x_2)\biggl(\frac{p_1}{\,1-p_2\,}\biggr)\\[0.3em]
&=\frac{n\,p_1}{\,1-p_2\,}-\frac{p_1}{\,1-p_2\,}\,x_2,\ x_2=0,\ldots,n
\end{aligned}
$$

$$
\begin{aligned}
\mathbb{E}(X_2\mid X_1=x_1)&=(n-x_1)\biggl(\frac{p_2}{\,1-p_1\,}\biggr)\\[0.3em]
&=\frac{n\,p_2}{\,1-p_1\,}-\frac{p_2}{\,1-p_1\,}\,x_1,\ x_1=0,\ldots,n
\end{aligned}
$$

</div>

由[母體線性迴歸方程式之特性](/lecture-notes/population-linear-regression/#thm-popu-reg)可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathrm{Corr}(X_1,X_2)&=-\sqrt{\biggl(-\frac{p_1}{\,1-p_2\,}\biggr)\biggl(-\frac{p_2}{\,1-p_1\,}\biggr)}\\[0.45em]
&=-\sqrt{\frac{p_1\,p_2}{\,(1-p_1)\,(1-p_2)\,}}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Corr}(X_1,X_2)&=-\sqrt{\biggl(-\frac{p_1}{\,1-p_2\,}\biggr)\biggl(-\frac{p_2}{\,1-p_1\,}\biggr)}\\[0.3em]
&=-\sqrt{\frac{p_1\,p_2}{\,(1-p_1)\,(1-p_2)\,}}
\end{aligned}
$$

</div>

原式得證。 <span class="topic-qed">$\square$</span>
</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

[Theorem 4.2](#thm-trinomial-properties) 的各項性質皆有直接的實驗詮釋。將 $\boldsymbol{X}=\bigl[X_1,X_2\bigr]^{\mathrm{T}}$ 視為 $n$ 次獨立三項實驗中第一類與第二類的發生次數，若只關心第一類的次數，可將第一類視為「成功類」、第二類與第三類合併為「失敗類」，分配遂退化為[二項分配](/lecture-notes/binomial-distribution/#def-binomial)，此即性質 (1)；若關心前兩類的總次數，則相當於將第一類與第二類合併為「成功類」，成功機率為 <span class="text-nowrap">$p_1+p_2$，</span>此即性質 (2)。此外，因實驗總次數固定為 <span class="text-nowrap">$n$，</span>第一類與第二類的發生次數彼此排擠，故性質 (3) 與 (5) 中的共變異數與相關係數皆為負值。

至於性質 (4) 的條件分配，在已知第二類發生次數為 $x_2$ 的條件下，僅須考慮其餘 $n-x_2$ 次「非第二類」的實驗。在此縮減樣本空間中，每次實驗僅剩第一類或第三類兩種可能，第一類的條件發生機率變為 <span class="text-nowrap">$\frac{p_1}{\,1-p_2\,}$，</span>其中分母 $1-p_2$ 為第一類與第三類的機率總和，故條件分配為 $\mathrm{Bin}\bigl(n-x_2,\ \frac{p_1}{\,1-p_2\,}\bigr)$ 這一二項分配。

</div>

## 多項分配的例題

<div id="ex-multinomial-1" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.8</div>

<div lang="en" markdown="1">
A fair die is rolled independently $n$ times. Let $X_j$ be the number of times that face $j$ (<span class="text-nowrap">$j=1,2,\ldots,6$</span>) appears.

<ol class="topic-list-paren">
  <li>If <span class="text-nowrap">$n=20$,</span> what is the probability that <span class="text-nowrap">$X_6=6$,</span> <span class="text-nowrap">$X_5=5$,</span> <span class="text-nowrap">$X_4=4$,</span> and <span class="text-nowrap">$X_3=3$?</span></li>
  <li>For general <span class="text-nowrap">$n$,</span> what is the pmf of <span class="text-nowrap">$X_1+X_2$?</span></li>
  <li>For general <span class="text-nowrap">$n$,</span> what is the covariance of $X_1$ and <span class="text-nowrap">$X_2$?</span></li>
</ol>
</div>

(1) 依照題意可知所求機率為
{: .topic-paren-item}

$$
\frac{20!}{\,6!5!4!3!2!\,}\biggl(\frac{1}{\,6\,}\biggr)^{18}\biggl(\frac{1}{\,3\,}\biggr)^{2}
$$

(2) 依題意可知
{: .topic-paren-item}

$$
\bigl[X_1,X_2\bigr]^{\mathrm{T}}\sim\mathrm{Tri}\left(n,\ \biggl[\frac{1}{\,6\,},\ \frac{1}{\,6\,}\biggr]^{\mathrm{T}}\right)
$$

故 $X_1+X_2\sim\mathrm{Bin}\bigl(n,\frac{1}{\,3\,}\bigr)$ 成立，由此可知
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
p_{\sssig X_1+X_2}(x)=\binom{n}{x}\biggl(\frac{1}{\,3\,}\biggr)^{x}\biggl(\frac{2}{\,3\,}\biggr)^{n-x},\ x=0,1,\ldots,n
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig X_1+X_2}(x)&=\binom{n}{x}\biggl(\frac{1}{\,3\,}\biggr)^{x}\biggl(\frac{2}{\,3\,}\biggr)^{n-x},\\[0.3em]
&\quad\ x=0,1,\ldots,n
\end{aligned}
$$

</div>

(3)
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathrm{Cov}(X_1,X_2)=-n\,\biggl(\frac{1}{\,6\,}\biggr)\,\biggl(\frac{1}{\,6\,}\biggr)=\frac{-n}{\,36\,}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathrm{Cov}(X_1,X_2)&=-n\,\biggl(\frac{1}{\,6\,}\biggr)\,\biggl(\frac{1}{\,6\,}\biggr)\\[0.3em]
&=\frac{-n}{\,36\,}
\end{aligned}
$$

</div>

</div>

<div id="ex-multinomial-2" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 4.9</div>

<div lang="en" markdown="1">
Suppose $2r$ balls are distributed at random into $r$ boxes. Let $X_i$ denote the number of balls in box <span class="text-nowrap">$i$.</span>

<ol class="topic-list-paren">
  <li>Find the joint probability mass function of <span class="text-nowrap">$X_1,\ldots,X_r$.</span></li>
  <li>Find the probability that each box contains exactly $2$ balls.</li>
</ol>
</div>

(1) 依照題意可知隨機變數 $X_1,\ldots,X_r$ 之聯合 pmf 為
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
p_{\sssig X_1\cdots X_r}(x_1,\ldots,x_r)&=\frac{(2r)!}{\,x_1!\cdots x_r!\,}\biggl(\frac{1}{\,r\,}\biggr)^{2r},\\[0.45em]
&\qquad x_1,\ldots,x_r=0,1,\ldots,2r,\ \sum_{i=1}^{r}x_i=2r
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig X_1\cdots X_r}(x_1,\ldots,x_r)&=\frac{(2r)!}{\,x_1!\cdots x_r!\,}\biggl(\frac{1}{\,r\,}\biggr)^{2r},\\[0.3em]
&\quad\ x_1,\ldots,x_r=0,1,\ldots,2r,\\[0.3em]
&\quad\ \sum_{i=1}^{r}x_i=2r
\end{aligned}
$$

</div>

(2) 所求為
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
p_{\sssig X_1\cdots X_r}(2,\ldots,2)=\frac{(2r)!}{\,2!\cdots 2!\,}\biggl(\frac{1}{\,r\,}\biggr)^{2r}=\frac{(2r)!}{\,2^r\,}\biggl(\frac{1}{\,r\,}\biggr)^{2r}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
p_{\sssig X_1\cdots X_r}(2,\ldots,2)&=\frac{(2r)!}{\,2!\cdots 2!\,}\biggl(\frac{1}{\,r\,}\biggr)^{2r}\\[0.3em]
&=\frac{(2r)!}{\,2^r\,}\biggl(\frac{1}{\,r\,}\biggr)^{2r}
\end{aligned}
$$

</div>

</div>

## 本篇小結

[Theorem 4.1](#thm-trinomial-thm) 的三項式定理把 [Theorem 2.18](/lecture-notes/moment-system/#thm-binomial) 的兩項推廣到三項，係數由 $\binom{n}{x}$ 換成 $\frac{n!}{\,x!y!z!\,}$ 這個式子，加總的範圍則是所有滿足 $x+y+z=n$ 的非負整數三元組。同樣的作法可以繼續推到多項式定理。

[Definition 4.4](#def-multinomial-trial) 的多項實驗由三個條件界定，要求出象被分成 $k$ 個互斥事件、各事件的發生機率固定且總和為 <span class="text-nowrap">$1$，</span>以及實驗與實驗之間彼此獨立。由於各類次數的總和必定是 <span class="text-nowrap">$n$，</span>[Definition 4.5](#def-multinomial) 只記錄前 $k-1$ 類的次數，最後一類的次數隨即可以得到；機率函數的分母因而多出 $\bigl(n-\sum_{i=1}^{k-1}x_i\bigr)!$ 這一項，而末尾的機率是 $1-\sum_{i=1}^{k-1}p_i$ 這個數。當 $k=3$ 時稱為三項分配，其機率質量函數的合法性正好可由[三項式定理](#thm-trinomial-thm)一步得出。

[Theorem 4.2](#thm-trinomial-properties) 一次給出三項分配的五款性質，證明的關鍵是三項分配的 mgf。把 $t_2$ 取為 $0$ 即得 $X_1$ 的邊際 mgf，兩個變數的 mgf 都是二項分配的形式，這是 (1)；把兩個變數的引數都取為 $t$ 即得 $X_1+X_2$ 的 mgf，兩類合併之後仍是二項分配，這是 (2)；(3) 由三個變異數與變異數的加法關係反解出[共變異數](/lecture-notes/covariance/#def-covariance)，結果為負值 <span class="text-nowrap">$-n\,p_1\,p_2$；</span>(4) 直接由條件 pmf 的定義相除，約掉之後仍是二項分配，成功機率換成比值 <span class="text-nowrap">$\frac{p_1}{\,1-p_2\,}$；</span>(5) 則由條件期望值為 $x_2$ 的一次式，依母體線性迴歸方程式的特性得到[相關係數](/lecture-notes/correlation-coefficient/#def-corr)。

這五款性質都可以在直觀上得到解釋。只關切第一類時，第二類與第三類合併成「失敗類」，於是回到二項分配；實驗總次數固定，兩類的成功次數彼此排擠，因而呈現負相關；已知第二類的次數之後，剩下的 $n-x_2$ 次實驗只可能落在第一類或第三類，樣本空間縮小，第一類的成功機率隨之變為 <span class="text-nowrap">$\frac{p_1}{\,1-p_2\,}$。</span>

[Example 4.8](#ex-multinomial-1) 把公正骰子擲 $n$ 次的結果視為六類的多項實驗。第一小題把未指定的兩次併成一類，多項係數為 <span class="text-nowrap">$\frac{20!}{\,6!5!4!3!2!\,}$；</span>第二、三小題則只看點數 $1$ 與點數 $2$ 兩類，直接套用 [Theorem 4.2](#thm-trinomial-properties) 的合併性質與共變異數公式。[Example 4.9](#ex-multinomial-2) 把 $2r$ 顆球隨機放入 $r$ 個盒子，各盒的球數服從各類機率皆為 $\frac{1}{\,r\,}$ 的多項分配，每盒恰好兩顆的機率即為機率函數在 $x_1=\cdots=x_r=2$ 的值。

[下一篇](/lecture-notes/geometric-distribution-memoryless/)回到只有成功與失敗兩類的伯努利實驗，但改為一直做到第一次成功為止，所需要的實驗次數即服從幾何分配；該篇並會介紹幾何分配最具代表性的無記憶性。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
