---
title: "車諾夫不等式"
subtitle: "Chernoff Inequality"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 17
order: 217
permalink: /teaching-topics/chernoff-inequality/
date: 2026-07-13
published: true
excerpt: '車諾夫不等式把指數轉換放入馬可夫不等式，再對所有使指數動差有限的參數取下確界，得到可依參數調整的尾端機率上界。'
---

[上一篇文章](/teaching-topics/chebyshev-cantelli-inequalities/)利用前二階動差控制偏離期望值之事件的機率。若將非負隨機變數 $e^{tX}$ 放入 [Theorem 2.4](/teaching-topics/markov-inequality/#theorem-24)，便可隨參數 $t$ 的選擇得到不同的尾端機率上界。

對固定的 $t\in\mathbb{R}$，$\mathbb{E}(e^{tX})$ 稱為 $X$ 在參數 $t$ 下的**指數動差 (exponential moment)**。這個期望值可能是正無限大；以下所說的「指數動差有限」，特指 $\mathbb{E}(e^{tX})<\infty$。

若把 $t$ 當成變數，$t\mapsto\mathbb{E}(e^{tX})$ 便是 MGF 所使用的函數形式。然而，MGF 要用微分生成各階原動差，因此依 [Definition 2.17](/teaching-topics/moment-generating-functions/#definition-217)，只有在 $\mathbb{E}(e^{tX})$ 對某個以 $0$ 為內點的開區間內每個 $t$ 皆有限時，才稱 $X$ 具有 MGF。車諾夫界限的要求較弱。右尾只需要選定的一個 $t>0$ 使指數動差有限，左尾則只需要一個這樣的 $t<0$。

## 先確認哪些參數使指數動差有限

為了記錄哪些參數可用，令 $\mathcal{D}_X=\bigl\lbrace t\in\mathbb{R}\mid\mathbb{E}(e^{tX})<\infty\bigr\rbrace$。[車諾夫不等式 (Chernoff inequality)](#theorem-27) 對單一尾端建立界限時，只要求選定的 $t$ 屬於 $\mathcal{D}_X$ 且不等於 $0$；其中 $t>0$ 用於右尾，$t<0$ 則用於左尾。

<div id="theorem-27" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.7 (Chernoff Inequality)</div>

令 $X$ 為實值隨機變數，且 $k\in\mathbb{R}$。

若 $t\in\mathcal{D}_X\cap(0,\infty)$，則

$$
\mathbb{P}(X\geqslant k)
\leqslant
e^{-tk}\mathbb{E}(e^{tX})
$$

若 $t\in\mathcal{D}_X\cap(-\infty,0)$，則

$$
\mathbb{P}(X\leqslant k)
\leqslant
e^{-tk}\mathbb{E}(e^{tX})
$$

</div>

<div class="topic-proof" markdown="1">
**Proof.** 先令 $t\in\mathcal{D}_X\cap(0,\infty)$。指數函數為嚴格遞增函數，因此 $\lbrace X\geqslant k\rbrace=\lbrace e^{tX}\geqslant e^{tk}\rbrace$。

對非負隨機變數 $e^{tX}$ 使用 [Theorem 2.4](/teaching-topics/markov-inequality/#theorem-24)，可得

$$
\begin{aligned}
\mathbb{P}(X\geqslant k)
&=
\mathbb{P}(e^{tX}\geqslant e^{tk}) \\[0.35em]
&\leqslant
\frac{\mathbb{E}(e^{tX})}{e^{tk}} \\[0.35em]
&=
e^{-tk}\mathbb{E}(e^{tX})
\end{aligned}
$$

若 $t\in\mathcal{D}_X\cap(-\infty,0)$，乘上 $t$ 時不等號方向反轉，因此

$$
\lbrace X\leqslant k\rbrace
=
\lbrace tX\geqslant tk\rbrace
=
\lbrace e^{tX}\geqslant e^{tk}\rbrace
$$

再次對 $e^{tX}$ 使用 [Theorem 2.4](/teaching-topics/markov-inequality/#theorem-24)，即得左尾界限。$\square$
</div>

## 在指數動差有限的參數範圍內取下確界

[Theorem 2.7](#theorem-27) 對每個位於 $\mathcal{D}_X$ 的正參數或負參數都成立，因此可在對應範圍內取下確界 (infimum)。若 $\mathcal{D}_X\cap(0,\infty)$ 非空，則

$$
\mathbb{P}(X\geqslant k)
\leqslant
\inf_{t\in\mathcal{D}_X\cap(0,\infty)}
e^{-tk}\mathbb{E}(e^{tX})
$$

若 $\mathcal{D}_X\cap(-\infty,0)$ 非空，則

$$
\mathbb{P}(X\leqslant k)
\leqslant
\inf_{t\in\mathcal{D}_X\cap(-\infty,0)}
e^{-tk}\mathbb{E}(e^{tX})
$$

若 $\mathcal{D}_X$ 包含某個以 $0$ 為內點的開區間，則 $X$ 具有 MGF。在 $M_X(t)$ 有限的範圍內，[累積量母函數](/teaching-topics/probability-cumulant-generating-functions/#definition-219)滿足 $K_X(t)=\log M_X(t)$。因為 $M_X(t)>0$，所以 $M_X(t)=\exp(K_X(t))$。因此，右尾機率的上界可依序改寫為

$$
\begin{gathered}
\inf_{t\in\mathcal{D}_X\cap(0,\infty)}
e^{-tk}\mathbb{E}(e^{tX}) \\[0.35em]
=
\inf_{t\in\mathcal{D}_X\cap(0,\infty)}
e^{-tk}M_X(t) \\[0.35em]
=
\inf_{t\in\mathcal{D}_X\cap(0,\infty)}
e^{-tk}\exp\bigl(K_X(t)\bigr) \\[0.35em]
=
\inf_{t\in\mathcal{D}_X\cap(0,\infty)}
\exp\bigl(K_X(t)-tk\bigr)
\end{gathered}
$$

第一個等號使用 $M_X(t)=\mathbb{E}(e^{tX})$；第二個等號使用 $M_X(t)=\exp(K_X(t))$；最後一個等號則把 $e^{-tk}$ 與 $\exp(K_X(t))$ 合併為同一個指數函數。左尾界限也可依相同方式改寫，只須將下確界的參數範圍改為 $\mathcal{D}_X\cap(-\infty,0)$。

在 $X$ 具有 MGF 的前提下，上述改寫對每個所考慮的 $t\in\mathcal{D}_X$ 都成立。若要以微分求取 $\mathcal{D}_X$ 內部的極小點，才須進一步將 $t$ 限制在 $\mathcal{D}_X$ 的內部；若下確界須由參數逼近定義域邊界而得到，便不能只使用內部的微分條件。對數函數嚴格遞增，因此 $K_X(t)-tk$ 與 $e^{-tk}\mathbb{E}(e^{tX})$ 對參數 $t$ 的大小順序相同；若最小值在所考慮的範圍內取得，兩者會在同一個 $t$ 取得最小值。

<div id="interlude-219" class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 2.19</div>

[Theorem 2.7](#theorem-27) 先把門檻事件轉成指數門檻事件。正參數 $t$ 會放大較大的 $X$，因此適合處理右尾；負參數 $t$ 會放大較小的 $X$，因此適合處理左尾。

固定一個非零且位於 $\mathcal{D}_X$ 的 $t$ 時，車諾夫界限的等號條件非常嚴格。[Theorem 2.4](/teaching-topics/markov-inequality/#theorem-24) 要取等號，必須使 $e^{tX}$ 在尾端事件外等於 $0$，並在事件內等於 $e^{tk}$。因為 $e^{tX}>0$ 恆成立，固定 $t$ 時，等號成立若且唯若 $\mathbb{P}(X=k)=1$。

取下確界後，界限也可能在參數逼近邊界時等於真實機率。例如某個尾端事件根本不可能發生時，界限可能在 $t\to\infty$ 時趨近 $0$。因此，固定 $t$ 的等號條件不能直接當成取下確界後的完整條件。若最小值在某個有限實數 $t\ne0$ 處取得，且 $X$ 不是**退化隨機變數 (degenerate random variable)**，則車諾夫界限為嚴格不等式。
</div>

## 卜瓦松分配的右尾界限

<div id="example-224" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.24 (A Poisson Upper Tail)</div>

令 $X$ 具有參數 $\lambda>0$ 的卜瓦松分配 (Poisson distribution)。其 pmf 為

$$
\mathbb{P}(X=x)
=
e^{-\lambda}\frac{\lambda^x}{x!},
\qquad
x=0,1,2,\ldots
$$

其 MGF 為

$$
\begin{aligned}
M_X(t)
&=
\sum_{x=0}^{\infty}
e^{tx}e^{-\lambda}\frac{\lambda^x}{x!} \\[0.35em]
&=
e^{-\lambda}
\sum_{x=0}^{\infty}
\frac{(\lambda e^t)^x}{x!} \\[0.35em]
&=
\exp\bigl(\lambda(e^t-1)\bigr),
\qquad
t\in\mathbb{R}
\end{aligned}
$$

令 $k$ 為正整數，且 $k>\lambda$。因為這個 MGF 對每個實數 $t$ 都有限，所以 $\mathcal{D}_X=\mathbb{R}$。將 MGF 代入 [Theorem 2.7](#theorem-27) 的右尾界限，可得

$$
\begin{aligned}
\mathbb{P}(X\geqslant k)
&\leqslant
\inf_{t>0}e^{-tk}M_X(t) \\[0.35em]
&=
\inf_{t>0}e^{-tk}\exp\bigl(\lambda(e^t-1)\bigr) \\[0.35em]
&=
\inf_{t>0}\exp\bigl(-tk+\lambda(e^t-1)\bigr)
\end{aligned}
$$

第一個等號代入 $M_X(t)=\exp(\lambda(e^t-1))$；第二個等號使用指數律，把 $e^{-tk}$ 與 $\exp(\lambda(e^t-1))$ 合併為同一個指數函數。

令 $q(t)=-tk+\lambda(e^t-1)$。為了求取 $q(t)$ 在 $t>0$ 時的最小值，先計算

$$
q^{\prime}(t)=-k+\lambda e^t,
\qquad
q^{\prime\prime}(t)=\lambda e^t>0
$$

由 $q^{\prime}(t)=0$ 可得

$$
\begin{aligned}
q^{\prime}(t)=0
&\Longleftrightarrow
-k+\lambda e^t=0 \\[0.35em]
&\Longleftrightarrow
e^t=\frac{k}{\lambda} \\[0.35em]
&\Longleftrightarrow
t=\ln\frac{k}{\lambda}
\end{aligned}
$$

令 $t^{\ast}=\ln(k/\lambda)$。因為 $k>\lambda$，所以 $t^{\ast}>0$。又因為 $q^{\prime\prime}(t)>0$ 對每個 $t>0$ 都成立，所以 $q$ 在 $(0,\infty)$ 上嚴格凸。此時 $q^{\prime}(t^{\ast})=0$，故 $t^{\ast}$ 是 $q$ 在 $t>0$ 時唯一取得最小值的點；換言之，此處的下確界在 $t^{\ast}$ 取得。

將 $t^{\ast}$ 代入 $q(t)$，可得

$$
\begin{aligned}
q(t^{\ast})
&=
-k\ln\frac{k}{\lambda}
+\lambda\left(e^{\ln(k/\lambda)}-1\right) \\[0.35em]
&=
-k\ln\frac{k}{\lambda}
+\lambda\left(\frac{k}{\lambda}-1\right)
\\[0.35em]
&=
-k\ln\frac{k}{\lambda}+k-\lambda
\end{aligned}
$$

指數函數嚴格遞增，所以 $t^{\ast}$ 也使 $\exp(q(t))$ 取得最小值。因此

$$
\begin{aligned}
\mathbb{P}(X\geqslant k)
&\leqslant
\inf_{t>0}\exp(q(t)) \\[0.35em]
&=
\exp(q(t^{\ast})) \\[0.35em]
&=
\exp\left(-k\ln\frac{k}{\lambda}+k-\lambda\right) \\[0.35em]
&=
e^{-\lambda}e^k\left(\frac{k}{\lambda}\right)^{-k} \\[0.35em]
&=
e^{-\lambda}e^k\left(\frac{\lambda}{k}\right)^k \\[0.35em]
&=
e^{-\lambda}\left(\frac{e\lambda}{k}\right)^k
\end{aligned}
$$

若還要把結果改寫成含有 $k!$ 的形式，可利用 $k^k\geqslant k!$。因此

$$
e^{-\lambda}
\left(\frac{e\lambda}{k}\right)^k
\leqslant
\frac{e^{-\lambda}(e\lambda)^k}{k!}
$$

由此可得另一個上界

$$
\mathbb{P}(X\geqslant k)
\leqslant
\frac{e^{-\lambda}(e\lambda)^k}{k!}
$$

含有 $k!$ 的式子較容易與卜瓦松 pmf 對照，卻比前一個最佳化結果更弱。若門檻不是整數，應先利用 $\mathbb{P}(X\geqslant k)=\mathbb{P}(X\geqslant\lceil k\rceil)$，而不能直接對非整數使用 $k!$。
</div>

## 本篇小結

[Theorem 2.7](#theorem-27) 把 $e^{tX}$ 放入 [Theorem 2.4](/teaching-topics/markov-inequality/#theorem-24)。對 $t\in\mathcal{D}_X\cap(0,\infty)$，它控制右尾機率

$$
\mathbb{P}(X\geqslant k)
\leqslant
e^{-tk}\mathbb{E}(e^{tX})
$$

對 $t\in\mathcal{D}_X\cap(-\infty,0)$，它控制左尾機率

$$
\mathbb{P}(X\leqslant k)
\leqslant
e^{-tk}\mathbb{E}(e^{tX})
$$

[Theorem 2.7](#theorem-27) 只要求所選參數處的指數動差有限，不要求 MGF 在 $0$ 附近存在。取下確界時，也必須將 $t$ 限制在 $\mathcal{D}_X$ 的正數範圍或負數範圍。若 $\mathcal{D}_X$ 包含某個以 $0$ 為內點的開區間，則對每個 $t\in\mathcal{D}_X$，都有 $M_X(t)=\mathbb{E}(e^{tX})$。[Example 2.24](#example-224) 顯示，最佳參數可由微分求得；若再以其他不等式改寫結果，所得式子仍是上界，但可能比最佳化後的車諾夫界限更弱。

[下一篇文章](/teaching-topics/convexity-jensen-inequality/)會介紹凸函數、凹函數與[延森不等式](/teaching-topics/convexity-jensen-inequality/#theorem-28)，說明函數轉換如何改變期望值的大小關係。

## 參考文獻與延伸閱讀

- 黃文璋，2003，《機率論》，初版，華泰文化。
- 黃文璋，2003，《數理統計》，初版，華泰文化。
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
- Sheldon M. Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
