---
title: "特徵函數與分配的唯一性"
subtitle: "Characteristic Functions and Uniqueness of Distributions"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 14
order: 214
permalink: /teaching-topics/characteristic-functions/
date: 2026-07-13
published: true
excerpt: '特徵函數 (CF) 以複指數 $e^{itX}$ 描述機率分配。CF 對每個實值隨機變數都存在，能把獨立隨機變數之和轉成函數乘積，並由唯一性定理辨認分配。'
---

[上一篇文章](/teaching-topics/probability-cumulant-generating-functions/)介紹 PGF 與 CGF。對非負整數值隨機變數，將 PGF 的冪級數延伸到複數單位圓，再取 $s=e^{it}$，可得 $G_X(e^{it})=\mathbb{E}(e^{itX})$。本篇把這個複指數期望值推廣到每個實值隨機變數，並稱為**特徵函數 (characteristic function, CF)**。

MGF 不一定在 $0$ 附近存在，CF 卻對所有實值隨機變數與所有實數 $t$ 都存在。這項差異來自複指數的絕對值恆為 $1$。

## Euler 公式與複指數

令 $i$ 表示虛數單位，並滿足 $i^2=-1$。Euler 公式為

$$
e^{iu}=\cos u+i\sin u,
\qquad u\in\mathbb{R}
$$

因此

$$
\lvert e^{iu}\rvert
=
\sqrt{\cos^2u+\sin^2u}
=
1
$$

把 $u$ 換成 $tX$ 後，每個 $e^{itX}$ 都是絕對值為 $1$ 的複數。其期望值可由實部與虛部分別取期望值得到。

<div id="definition-220" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.20</div>

令 $X$ 為實值隨機變數。定義

$$
\varphi_X(t)
=
\mathbb{E}(e^{itX}),
\qquad t\in\mathbb{R}
$$

為 $X$ 的**特徵函數 (characteristic function, CF)**。由 Euler 公式可寫成

$$
\varphi_X(t)
=
\mathbb{E}[\cos(tX)]
+i\mathbb{E}[\sin(tX)]
$$

</div>

若 $X$ 為離散型隨機變數，則

$$
\varphi_X(t)
=
\sum_{x\in\mathcal{R}_X}e^{itx}p_X(x)
$$

若 $X$ 為連續型隨機變數，且 PDF 為 $f_X$，則

$$
\varphi_X(t)
=
\int_{-\infty}^{\infty}e^{itx}f_X(x)\,dx
$$

因為 $\lvert e^{itX}\rvert=1$，所以 $e^{itX}$ 對每個 $t\in\mathbb{R}$ 都可積。CF 的存在不要求 $X$ 有有限期望值、變異數或 MGF。

<div id="note-cf-mgf-relation" class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

若把指數轉換延伸到複數參數 $z$，並寫成

$$
M_X(z)=\mathbb{E}(e^{zX})
$$

則在 $z=it$ 時可得

$$
\varphi_X(t)=M_X(it)
$$

不過，[動差母函數的定義](/teaching-topics/moment-generating-functions/#definition-217)原本只把 $M_X(t)$ 定義在實數參數上。因此，$M_X(it)$ 應視為複數參數的延伸記號，不能當成把 $it$ 直接代入一個只定義在實數域的函數。CF 即使在實數 MGF 不存在時仍然存在。
</div>

<div id="interlude-216" class="topic-box topic-box--interlude" markdown="1">
<div class="topic-box__label">直覺校準 2.16</div>

固定 $t$ 後，$e^{itX}=\cos(tX)+i\sin(tX)$ 的取值都落在複數平面的單位圓上。CF 是這些複數取值依機率加權後的平均，因此其絕對值不會超過 $1$。

這也說明 CF 為何對厚尾分配仍然存在。厚尾分配可能使 $\mathbb{E}(e^{tX})$ 發散；但 $\lvert e^{itX}\rvert=1$，故 CF 對每個實值隨機變數皆存在。
</div>

## CF 的基本性質

<div id="proposition-214" class="topic-box topic-box--proposition" markdown="1">
<div class="topic-box__label">Proposition 2.14 (Basic Properties of CF)</div>

令 $X$ 為實值隨機變數，則 CF 具有下列性質。

<ol class="topic-list-paren">
  <li>$\varphi_X(0)=1$，且對每個 $t\in\mathbb{R}$，皆有 $\lvert\varphi_X(t)\rvert\leqslant 1$。</li>
  <li>$\varphi_X$ 在 $\mathbb{R}$ 上均勻連續。</li>
  <li>若 $Y=aX+b$，其中 $a,b\in\mathbb{R}$，則

$$
\varphi_Y(t)
=
e^{ibt}\varphi_X(at)
$$

  </li>
  <li>對每個 $t\in\mathbb{R}$，皆有

$$
\varphi_X(-t)
=
\overline{\varphi_X(t)}
$$

  </li>
  <li>若 $X_1,\ldots,X_n$ 相互獨立，則

$$
\varphi_{X_1+\cdots+X_n}(t)
=
\prod_{j=1}^{n}\varphi_{X_j}(t)
$$

  </li>
</ol>

</div>

第 (3) 點與[動差母函數的線性轉換公式](/teaching-topics/moment-generating-functions/#mgf-function-transformations)直接對應。若 $Y=aX+b$，MGF 一節已先得到

$$
M_Y(t)
=
e^{bt}M_X(at)
$$

CF 的對應公式為

$$
\varphi_Y(t)
=
e^{ibt}\varphi_X(at)
$$

在兩式中，將 $X$ 乘上 $a$ 都會使函數中的 $t$ 變為 $at$。再加上 $b$ 時，MGF 會多出 $e^{bt}$，CF 則會多出 $e^{ibt}$。MGF 公式只在所需期望值有限的範圍內使用；CF 對所有實數 $t$ 都存在，因此使用其線性轉換公式時不必另行檢查存在區間。

第一項由定義直接得到

$$
\varphi_X(0)=\mathbb{E}(1)=1
$$

以及

$$
\lvert\varphi_X(t)\rvert
\leqslant
\mathbb{E}(\lvert e^{itX}\rvert)
=
1
$$

均勻連續性的證明較為繁瑣，因此收合於下方。有興趣的讀者再行展開閱讀即可。

<details class="topic-proof">
<summary><strong>均勻連續性的證明</strong></summary>
<div markdown="1">

為了證明均勻連續，對任意 $t,h\in\mathbb{R}$ 可得

$$
\begin{aligned}
\lvert\varphi_X(t+h)-\varphi_X(t)\rvert
&=
\left\lvert
\mathbb{E}\left[e^{itX}(e^{ihX}-1)\right]
\right\rvert \\[0.35em]
&\leqslant
\mathbb{E}\left(\lvert e^{ihX}-1\rvert\right)
\end{aligned}
$$

對任意實數 $u$，皆有

$$
\lvert e^{iu}-1\rvert
=
2\left\lvert\sin\left(\frac{u}{2}\right)\right\rvert
\leqslant
\min\{\lvert u\rvert,2\}
$$

以 $\mathbf{1}_A$ 表示事件 $A$ 的指標函數 (indicator function)。取 $M>0$，並把期望值依 $\lvert X\rvert\leqslant M$ 與 $\lvert X\rvert>M$ 分成兩部分，可得

$$
\begin{aligned}
\mathbb{E}\left(\lvert e^{ihX}-1\rvert\right)
&=
\mathbb{E}\left[\lvert e^{ihX}-1\rvert\mathbf{1}_{\{\lvert X\rvert\leqslant M\}}\right] \\[0.35em]
&\quad+
\mathbb{E}\left[\lvert e^{ihX}-1\rvert\mathbf{1}_{\{\lvert X\rvert>M\}}\right] \\[0.35em]
&\leqslant
\lvert h\rvert M+2\mathbb{P}(\lvert X\rvert>M)
\end{aligned}
$$

因 $X$ 為實值隨機變數，當 $M\to\infty$ 時，$\mathbb{P}(\lvert X\rvert>M)\to 0$。給定 $\varepsilon>0$，可取 $M>0$ 使

$$
2\mathbb{P}(\lvert X\rvert>M)<\frac{\varepsilon}{2}
$$

再取 $\delta=\varepsilon/(2M)$。若 $\lvert h\rvert<\delta$，則

$$
\mathbb{E}\left(\lvert e^{ihX}-1\rvert\right)<\varepsilon
$$

右側上界不含 $t$，故 $\varphi_X$ 在整條實數線上均勻連續。

</div>
</details>

若 $Y=aX+b$，則

$$
\begin{aligned}
\varphi_Y(t)
&=
\mathbb{E}[e^{it(aX+b)}] \\[0.35em]
&=
e^{ibt}\mathbb{E}(e^{i(at)X}) \\[0.35em]
&=
e^{ibt}\varphi_X(at)
\end{aligned}
$$

再由 $e^{-itX}=\overline{e^{itX}}$ 可得共軛關係。最後，若 $X_1,\ldots,X_n$ 相互獨立，則

$$
\begin{aligned}
\varphi_{X_1+\cdots+X_n}(t)
&=
\mathbb{E}\left[
\prod_{j=1}^{n}e^{itX_j}
\right] \\[0.35em]
&=
\prod_{j=1}^{n}\mathbb{E}(e^{itX_j}) \\[0.35em]
&=
\prod_{j=1}^{n}\varphi_{X_j}(t)
\end{aligned}
$$

其中第二個等號使用了獨立性。

相互獨立隨機變數的正式定義會在下一章給出。此處先使用它所帶來的乘積性質，也就是獨立隨機變數的函數，其期望值可分解成各期望值的乘積。

<div id="note-cf-product-independence" class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

獨立性足以推出和的 CF 等於各 CF 的乘積；反向敘述並不成立。只知道 $\varphi_{X+Y}(t)=\varphi_X(t)\varphi_Y(t)$ 對所有 $t$ 成立，仍不足以斷定 $X$ 與 $Y$ 獨立。
</div>

## CF 與動差

CF 總是存在，但其導數是否存在取決於動差條件。若對某個正整數 $r$ 有

$$
\mathbb{E}(\lvert X\rvert^r)<\infty
$$

則可把微分移入期望值，得到

$$
\varphi_X^{(r)}(t)
=
\mathbb{E}\left[(iX)^r e^{itX}\right]
$$

令 $t=0$ 可得

$$
\varphi_X^{(r)}(0)
=
i^r\mathbb{E}(X^r)
$$

因此，CF 可在適當動差條件下生成原動差。CF 存在本身則不保證任何正整數階動差存在。

<div id="note-cf-derivative-converse" class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

由動差存在推導 CF 可微時，需要 $\mathbb{E}(\lvert X\rvert^r)<\infty$。反向命題須區分 $r$ 的奇偶。若 CF 在 $t=0$ 的 $r$ 階導數存在，$r$ 為偶數時可推出 $\mathbb{E}(\lvert X\rvert^r)<\infty$；$r$ 為奇數時，一般只能保證 $\mathbb{E}(\lvert X\rvert^{r-1})<\infty$。
</div>

## CF 唯一決定分配

CF 不只整理動差，也能完整辨認機率分配。這項性質不要求 MGF 存在。

<div id="theorem-22" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 2.2 (Uniqueness of CF)</div>

若實值隨機變數 $X$ 與 $Y$ 的 CF 對每個 $t\in\mathbb{R}$ 皆滿足

$$
\varphi_X(t)=\varphi_Y(t)
$$

則 $X$ 與 $Y$ 具有相同機率分配。

</div>

此定理可由 CF 的反演公式證明。若 $F$ 是 $X$ 的 CDF，$a<b$ 且 $a,b$ 都是 $F$ 的連續點，則

$$
F(b)-F(a)
=
\frac{1}{2\pi}
\lim_{T\to\infty}
\int_{-T}^{T}
\frac{e^{-ita}-e^{-itb}}{it}
\varphi_X(t)\,dt
$$

被積函數在 $t=0$ 的值以連續延伸解釋。右側完全由 $\varphi_X$ 決定，因此 CF 可決定所有連續點之間的區間機率，進而決定 CDF。故若 $\varphi_X(t)=\varphi_Y(t)$ 對所有實數 $t$ 成立，兩個 CDF 相同，原式得證。

<div id="note-cf-density-inversion" class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

不能在沒有條件時直接由 CF 寫出 PDF。若

$$
\int_{-\infty}^{\infty}\lvert\varphi_X(t)\rvert\,dt<\infty
$$

則 $X$ 具有有界且連續的 PDF，並可由傅立葉反演公式 (Fourier inversion formula) 求得

$$
f_X(x)
=
\frac{1}{2\pi}
\int_{-\infty}^{\infty}e^{-itx}\varphi_X(t)\,dt
$$

一般分配的反演應使用 CDF 版本及其連續點條件。
</div>

<div id="example-221" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 2.21 (The Cauchy Sample Mean)</div>

令 $X_1,\ldots,X_n$ 為相互獨立且具有標準柯西分配 (standard Cauchy distribution) 的隨機變數，其共同 CF 為

$$
\varphi_X(t)=e^{-\lvert t\rvert}
$$

考慮樣本平均數

$$
\overline{X}_n
=
\frac{1}{n}\sum_{j=1}^{n}X_j
$$

由[線性轉換與獨立和的性質](#proposition-214)可得

$$
\begin{aligned}
\varphi_{\overline{X}_n}(t)
&=
\prod_{j=1}^{n}
\varphi_{X_j}\left(\frac{t}{n}\right) \\[0.35em]
&=
\left[
e^{-\lvert t/n\rvert}
\right]^n \\[0.35em]
&=
e^{-\lvert t\rvert}
\end{aligned}
$$

這正是每個 $X_j$ 的 CF。由[CF 的唯一性](#theorem-22)可知，對每個正整數 $n$，皆有

$$
\overline{X}_n
\overset{d}{=}
X_1
$$

反演公式還能直接求出樣本平均數的 PDF。先檢查絕對可積條件，可得

$$
\begin{aligned}
\int_{-\infty}^{\infty}
\left\lvert\varphi_{\overline{X}_n}(t)\right\rvert\,dt
&=
2\int_0^\infty e^{-t}\,dt \\[0.35em]
&=
2
<
\infty
\end{aligned}
$$

故 $\overline{X}_n$ 具有有界且連續的 PDF。將反演積分在 $t=0$ 的兩側分開。在負半軸上，$\lvert t\rvert=-t$，所以 $e^{-\lvert t\rvert}=e^t$。令 $u=-t$，則 $t=-u$、$dt=-du$，而上下限由 $t\colon -\infty\to 0$ 變成 $u\colon \infty\to 0$。因此，負半軸部分可寫為

$$
\begin{aligned}
\int_{-\infty}^{0}e^{-itx}e^t\,dt
&=
\int_{\infty}^{0}e^{iux}e^{-u}(-du) \\[0.35em]
&=
\int_0^\infty e^{iux}e^{-u}\,du
\end{aligned}
$$

$dt=-du$ 帶來的負號與對調積分上下限帶來的負號相消。把這個結果與正半軸部分相加，再將第一個積分的積分變數 $u$ 改記為 $t$，可得

$$
\begin{aligned}
f_{\overline{X}_n}(x)
&=
\frac{1}{2\pi}
\int_{-\infty}^{\infty}
e^{-itx}e^{-\lvert t\rvert}\,dt \\[0.35em]
&=
\frac{1}{2\pi}
\int_0^\infty e^{iux}e^{-u}\,du \\[-0.05em]
&\quad+
\frac{1}{2\pi}
\int_0^\infty e^{-t}e^{-itx}\,dt \\[0.35em]
&=
\frac{1}{2\pi}
\int_0^\infty
e^{-t}\left(e^{itx}+e^{-itx}\right)\,dt \\[0.35em]
&=
\frac{1}{\pi}
\int_0^\infty e^{-t}\cos(tx)\,dt
\end{aligned}
$$

由 $e^{itx}+e^{-itx}=2\cos(tx)$，上述兩個積分相加後便得到餘弦積分；因子 $2$ 與 $1/(2\pi)$ 合併成 $1/\pi$。

為了繼續計算，將 $\cos(tx)$ 以複指數展開，可得

$$
\begin{aligned}
e^{-t}\cos(tx)
&=
\frac{1}{2}e^{-t}\left(e^{itx}+e^{-itx}\right) \\[0.35em]
&=
\frac{1}{2}\left(e^{-t+itx}+e^{-t-itx}\right) \\[0.35em]
&=
\frac{1}{2}
\left[
e^{-(1-ix)t}
+
e^{-(1+ix)t}
\right]
\end{aligned}
$$

第一項的指數滿足 $-t+itx=-(1-ix)t$，第二項則滿足 $-t-itx=-(1+ix)t$。將上式代入前一個餘弦積分，其中的因子 $1/2$ 與 $1/\pi$ 合併成 $1/(2\pi)$，因此

$$
\begin{aligned}
f_{\overline{X}_n}(x)
&=
\frac{1}{2\pi}
\int_0^\infty
\left[
e^{-(1-ix)t}
+
e^{-(1+ix)t}
\right]\,dt \\[0.35em]
&=
\frac{1}{2\pi}
\int_0^\infty e^{-(1-ix)t}\,dt \\[-0.05em]
&\quad+
\frac{1}{2\pi}
\int_0^\infty e^{-(1+ix)t}\,dt \\[0.35em]
&=
\frac{1}{2\pi}
\left(
\frac{1}{1-ix}
+
\frac{1}{1+ix}
\right) \\[0.35em]
&=
\frac{1}{\pi(1+x^2)}
\quad x\in\mathbb{R}
\end{aligned}
$$

後續兩個複數值廣義積分都收斂，因為 $1-ix$ 與 $1+ix$ 的實部皆為 $1$。所得 PDF 正是標準柯西密度，也就是樣本平均數仍具有標準柯西分配。

標準柯西分配沒有有限期望值與變異數，因此不滿足有限變異數型中央極限定理的前提；中央極限定理不能套用，原因不是它沒有 MGF。

</div>

## 本篇小結

實值隨機變數 $X$ 的 CF 定義為

$$
\varphi_X(t)=\mathbb{E}(e^{itX})
$$

因為 $\lvert e^{itX}\rvert=1$，CF 對所有 $t\in\mathbb{R}$ 都存在。CF 滿足 $\varphi_X(0)=1$、$\lvert\varphi_X(t)\rvert\leqslant 1$ 與均勻連續性；線性轉換可改寫其引數，獨立隨機變數之和則對應 CF 的乘積。

若 $\mathbb{E}(\lvert X\rvert^r)<\infty$，CF 的 $r$ 階導數可生成 $r$ 階原動差。CF 的唯一性則說明，只要兩個 CF 在整條實數線上相同，對應的機率分配便相同。PDF 的反演公式另有絕對可積條件，不能由 CF 存在直接推出。

後續文章將轉向機率不等式。當完整分配未知，只知道非負性與期望值時，馬可夫不等式仍能給出尾端機率的上界。

## 參考文獻與延伸閱讀

- 黃文璋，2003，《機率論》，初版，華泰文化。
- 黃文璋，2003，《數理統計》，初版，華泰文化。
- Patrick Billingsley. 1995. *Probability and Measure*. 3rd ed. Wiley.
- Kai Lai Chung. 2001. *A Course in Probability Theory*. 3rd ed. Academic Press.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
