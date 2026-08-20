---
title: "常態近似與連續性校正"
subtitle: "Normal Approximation and the Continuity Correction"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 5
topic: 6
order: 506
permalink: /lecture-notes/normal-approximation-continuity-correction/
date: 2026-08-15
published: false
excerpt: "中央極限定理要求樣本大小趨於無窮大，實務上不可能達成，但它所描述的是一個逐步逼近的過程: 只要 $n$ 足夠大，標準化之後的樣本平均數就足夠接近標準常態，因而可以直接以標準常態計算機率，這時稱標準常態分配是它的漸近分配。本篇先寫出漸近的記法，並交代仍應由中央極限定理出發的三個步驟，再說明在有限的 $n$ 之下反標準化不會受到退化或發散的困擾，於是樣本平均數與樣本和各有一個常態近似。接著把同一套作法用在五個具有可加性的常用分配上，分別給出其標準化形式與實務上常用的參數門檻。最後給出連續性校正: 以連續分配近似定義在整數上的離散分配時，區間的端點各挪動 $0.5$，並以樣本比例的例題比較校正前後的兩個答案。"
---

[上一篇](/lecture-notes/weak-law-and-central-limit-theorem/)給出弱大數法則與[中央極限定理](/lecture-notes/weak-law-and-central-limit-theorem/#thm-central-limit-theorem)，並以例題說明標準化之後的樣本平均數如何[分配收斂](/lecture-notes/convergence-in-distribution/#def-converge-in-distribution)至標準常態。本篇處理的是同一件事在實務上的用法。

中央極限定理所要求的條件之中，最難達成的是樣本大小趨於無窮大這一項，因為在實務上我們其實不可能達成這個要求。本篇先寫出「$n$ 足夠大時以標準常態計算」這個漸近的記法，並交代使用它時仍應由中央極限定理出發的三個步驟；接著說明在有限的 $n$ 之下反標準化不會受到退化或發散的困擾，因而樣本平均數與樣本和各有一個常態近似；再把同一套作法用在五個具有可加性的常用分配上，說明它們在什麼條件之下可以漸近為[常態分配](/lecture-notes/normal-distribution/#def-normal)。最後給出連續性校正，處理以連續分配近似離散分配時端點的位置。

## 漸近分配與常態近似

中央極限定理事實上描述的是一個過程，也就是隨著樣本大小越來越大，樣本平均數經由標準化之後會越來越接近標準常態，最終分配收斂至標準常態的過程。

這個過程指出，只要樣本大小**足夠大**，我們應該可以得到**足夠接近**標準常態的結果，也就是直接使用標準常態來計算的結果，將落在可允許的誤差範圍之內。我們將這件事表示為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\frac{\,\overline{X}-\mu\,}{\frac{\sigma}{\sqrt{n}}}\xrightarrow[~n~\text{足夠大}~]{~\mathrm{a}~}\mathcal{N}(0,1)\quad\text{或}\quad\frac{\,\overline{X}-\mu\,}{\frac{\sigma}{\sqrt{n}}}\xrightarrow[~n~\text{足夠大}~]{~\bullet~}\mathcal{N}(0,1)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\frac{\,\overline{X}-\mu\,}{\frac{\sigma}{\sqrt{n}}}&\xrightarrow[~n~\text{足夠大}~]{~\mathrm{a}~}\mathcal{N}(0,1)\\[0.45em]
\text{或}\quad\frac{\,\overline{X}-\mu\,}{\frac{\sigma}{\sqrt{n}}}&\xrightarrow[~n~\text{足夠大}~]{~\bullet~}\mathcal{N}(0,1)
\end{aligned}
$$

</div>

上述寫法代表標準常態分配是 $\frac{\,\overline{X}-\mu\,}{\frac{\sigma}{\sqrt{n}}}$ 的**漸近分配 <span lang="en">(asymptotic distribution)</span>**。

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

但讀者應注意的是，這並不能算是一個嚴謹的數學表示式。雖然部分教科書也採用這樣的寫法，但多半只是在說明這個形式所服從的分配「很接近常態」。

</div>

在嚴謹的數學論證之中，上述結果通常會是在計算機率時使用，但是讀者應注意，使用這個表示法仍應由中央極限定理出發，也就是依下列的步驟處理:

(1) 欲求取 $\mathbb{P}(a<\overline{X}<b)$
{: .topic-paren-item}

(2) 說明由中央極限定理可知
{: .topic-paren-item}

$$
\frac{\,\overline{X}-\mu\,}{\frac{\sigma}{\sqrt{n}}}\dconv Z\sim\mathcal{N}(0,1)
$$

(3) 在 $n$ 有限但是足夠大時，我們可以將所求轉化為
{: .topic-paren-item}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(a<\overline{X}<b)&=\mathbb{P}\Biggl(\frac{a-\mu}{\frac{\sigma}{\sqrt{n}}}<\frac{\overline{X}-\mu}{\frac{\sigma}{\sqrt{n}}}<\frac{b-\mu}{\frac{\sigma}{\sqrt{n}}}\Biggr)\\[0.45em]
&\fallingdotseq\mathbb{P}\Biggl(\frac{a-\mu}{\frac{\sigma}{\sqrt{n}}}<Z<\frac{b-\mu}{\frac{\sigma}{\sqrt{n}}}\Biggr)
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(a<\overline{X}<b)\\[0.3em]
&=\mathbb{P}\Biggl(\frac{a-\mu}{\frac{\sigma}{\sqrt{n}}}<\frac{\overline{X}-\mu}{\frac{\sigma}{\sqrt{n}}}\\[0.2em]
&\qquad\qquad<\frac{b-\mu}{\frac{\sigma}{\sqrt{n}}}\Biggr)\\[0.3em]
&\fallingdotseq\mathbb{P}\Biggl(\frac{a-\mu}{\frac{\sigma}{\sqrt{n}}}<Z<\frac{b-\mu}{\frac{\sigma}{\sqrt{n}}}\Biggr)
\end{aligned}
$$

</div>

這個流程可以簡便地化約為上述的漸近記法，從而直接以下式處理所求的 $\mathbb{P}(a<\overline{X}<b)$

$$
\mathbb{P}\Biggl(\frac{a-\mu}{\frac{\sigma}{\sqrt{n}}}<Z<\frac{b-\mu}{\frac{\sigma}{\sqrt{n}}}\Biggr)
$$

<div id="ex-uniform-sum-normal-approximation" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.21</div>

<div lang="en" markdown="1">
Suppose that $X_1,X_2,\ldots,X_{48}$ are independent and identically distributed random variables, each following the uniform distribution <span class="text-nowrap">$\mathcal{U}(0,1)$.</span> What is the probability that $\sum_{i=1}^{48}X_i\geqslant26$?
</div>

令 $\lbrace X_i\rbrace_{i=1}^{\infty}\iidto\mathcal{U}(0,1)$，則由[均勻分配](/lecture-notes/uniform-distribution-integral-transform/#def-uniform-distribution)的期望值與變異數可知

$$
\mu=\frac{1}{\,2\,},\quad\sigma^{2}=\frac{1}{\,12\,}
$$

由中央極限定理可知

$$
\frac{\,\sum_{i=1}^{n}X_i-\frac{n}{\,2\,}\,}{\sqrt{\frac{n}{\,12\,}}}\dconv Z\sim\mathcal{N}(0,1)
$$

由此可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}\Biggl(\sum_{i=1}^{48}X_i\geqslant26\Biggr)&=\mathbb{P}\Biggl(\frac{\,\sum_{i=1}^{48}X_i-24\,}{\sqrt{4}}\geqslant\frac{\,26-24\,}{\sqrt{4}}\Biggr)\\[0.45em]
&\fallingdotseq\mathbb{P}(Z\geqslant1)=0.1587
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}\Biggl(\sum_{i=1}^{48}X_i\geqslant26\Biggr)\\[0.3em]
&=\mathbb{P}\Biggl(\frac{\,\sum_{i=1}^{48}X_i-24\,}{\sqrt{4}}\geqslant\frac{\,26-24\,}{\sqrt{4}}\Biggr)\\[0.3em]
&\fallingdotseq\mathbb{P}(Z\geqslant1)=0.1587
\end{aligned}
$$

</div>

</div>

## 樣本平均數與樣本和的常態近似

中央極限定理的精妙之處在於，$n\to\infty$ 時分子與分母原本是一起收斂到 $0$ 或一起發散，**但由於兩者斂散的速率相同，因此可以將退化或發散的情形相互抵銷**。這個結構是不可以任意更動的，換言之，**我們不可以對這個標準化的形式任意移項而進行反標準化**。

前述由中央極限定理所衍生的漸近結果，是樣本平均數 $\overline{X}$ 經標準化之後，在有限但足夠大的 $n$ 之下所得到的。由於此時的 $n$ 為有限，故在上述的漸近結果之下，即使反標準化，也不會受到 $n\to\infty$ 所帶來的退化或發散的困擾，換言之，我們有

$$
\overline{X}\xrightarrow[~n~\text{足夠大}~]{~\mathrm{a}~}\mathcal{N}\biggl(\mu,\frac{\sigma^{2}}{n}\biggr)
$$

或是經由樣本和版本的中央極限定理，在 $n$ 有限但足夠大的情況下得到

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\frac{\,\sum_{i=1}^{n}X_i-n\mu\,}{\sqrt{n}\,\sigma}\xrightarrow[~n~\text{足夠大}~]{~\mathrm{a}~}\mathcal{N}(0,1)\quad\text{或}\quad\sum_{i=1}^{n}X_i\xrightarrow[~n~\text{足夠大}~]{~\mathrm{a}~}\mathcal{N}(n\mu,n\sigma^{2})
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\frac{\,\sum_{i=1}^{n}X_i-n\mu\,}{\sqrt{n}\,\sigma}&\xrightarrow[~n~\text{足夠大}~]{~\mathrm{a}~}\mathcal{N}(0,1)\\[0.45em]
\text{或}\quad\sum_{i=1}^{n}X_i&\xrightarrow[~n~\text{足夠大}~]{~\mathrm{a}~}\mathcal{N}(n\mu,n\sigma^{2})
\end{aligned}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

我們還是要特別強調，上述是基於中央極限定理，在 $n\to\infty$ 這個條件不可得的實務情況之下所得到的漸近結果，並不是確切服從常態分配。

</div>

## 具可加性分配的常態近似

因為上述的近似結果都是源自於樣本平均數或樣本和，故針對具有可加性的常用分配，在某些參數足夠大的時候，我們可以將其漸近為常態分配，再行求算其機率，見下列結果。

(1) [二項分配](/lecture-notes/binomial-distribution/#def-binomial) <span lang="en">(binomial distribution)</span> 漸近常態分配: 若 <span class="text-nowrap">$X\sim\mathrm{Bin}(n,p)$，</span>則有
{: .topic-paren-item}

$$
\frac{\,X-np\,}{\sqrt{np(1-p)}}\dconv Z\sim\mathcal{N}(0,1)
$$

實務上，當 $np\geqslant5$ 且 $n(1-p)\geqslant5$ 時，我們有
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\frac{X-np}{\sqrt{np(1-p)}}\xrightarrow[~np,~n(1-p)\geqslant5~]{~\mathrm{a}~}\mathcal{N}(0,1)\quad\text{或}\quad X\xrightarrow[~np,~n(1-p)\geqslant5~]{~\mathrm{a}~}\mathcal{N}\bigl(np,np(1-p)\bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\frac{X-np}{\sqrt{np(1-p)}}&\xrightarrow[~np,~n(1-p)\geqslant5~]{~\mathrm{a}~}\mathcal{N}(0,1)\\[0.45em]
\text{或}\quad X&\xrightarrow[~np,~n(1-p)\geqslant5~]{~\mathrm{a}~}\mathcal{N}\bigl(np,np(1-p)\bigr)
\end{aligned}
$$

</div>

(2) [卜瓦松分配](/lecture-notes/poisson-process-and-distribution/#def-poisson-distribution) <span lang="en">(Poisson distribution)</span> 漸近常態分配: 若 <span class="text-nowrap">$X\sim\mathrm{Poi}(\lambda)$，</span>則有
{: .topic-paren-item}

$$
\frac{\,X-\lambda\,}{\sqrt{\lambda}}\dconv Z\sim\mathcal{N}(0,1)
$$

實務上，當 $\lambda\geqslant9$ 時，我們有
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\frac{\,X-\lambda\,}{\sqrt{\lambda}}\xrightarrow[~\lambda\geqslant9~]{~\mathrm{a}~}\mathcal{N}(0,1)\quad\text{或}\quad X\xrightarrow[~\lambda\geqslant9~]{~\mathrm{a}~}\mathcal{N}(\lambda,\lambda)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\frac{\,X-\lambda\,}{\sqrt{\lambda}}&\xrightarrow[~\lambda\geqslant9~]{~\mathrm{a}~}\mathcal{N}(0,1)\\[0.45em]
\text{或}\quad X&\xrightarrow[~\lambda\geqslant9~]{~\mathrm{a}~}\mathcal{N}(\lambda,\lambda)
\end{aligned}
$$

</div>

(3) [負二項分配](/lecture-notes/negative-binomial-distribution/#def-negative-binomial) <span lang="en">(negative binomial distribution)</span> 漸近常態分配: 若 <span class="text-nowrap">$X\sim\mathcal{NB}(r,p)$，</span>則有
{: .topic-paren-item}

$$
\frac{\,X-\frac{r}{\,p\,}\,}{\sqrt{\frac{\,r(1-p)\,}{p^{2}}}}\dconv Z\sim\mathcal{N}(0,1)
$$

實務上，當 $r$ 足夠大時，我們有
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\frac{\,X-\frac{r}{\,p\,}\,}{\sqrt{\frac{\,r(1-p)\,}{p^{2}}}}\xrightarrow[~r~\text{夠大}~]{~\mathrm{a}~}\mathcal{N}(0,1)\quad\text{或}\quad X\xrightarrow[~r~\text{夠大}~]{~\mathrm{a}~}\mathcal{N}\biggl(\frac{\,r\,}{p},\frac{\,r(1-p)\,}{p^{2}}\biggr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\frac{\,X-\frac{r}{\,p\,}\,}{\sqrt{\frac{\,r(1-p)\,}{p^{2}}}}&\xrightarrow[~r~\text{夠大}~]{~\mathrm{a}~}\mathcal{N}(0,1)\\[0.45em]
\text{或}\quad X&\xrightarrow[~r~\text{夠大}~]{~\mathrm{a}~}\mathcal{N}\biggl(\frac{\,r\,}{p},\frac{\,r(1-p)\,}{p^{2}}\biggr)
\end{aligned}
$$

</div>

(4) [卡方分配](/lecture-notes/chi-squared-distribution/#def-chi-distribution) <span lang="en">(chi-square distribution)</span> 漸近常態分配: 若 <span class="text-nowrap">$X\sim\chi^{2}(\nu)$，</span>則有
{: .topic-paren-item}

$$
\frac{\,X-\nu\,}{\sqrt{2\nu}}\dconv Z\sim\mathcal{N}(0,1)
$$

實務上，當 $\nu$ 足夠大時，我們有
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\frac{\,X-\nu\,}{\sqrt{2\nu}}\xrightarrow[~\nu~\text{夠大}~]{~\mathrm{a}~}\mathcal{N}(0,1)\quad\text{或}\quad X\xrightarrow[~\nu~\text{夠大}~]{~\mathrm{a}~}\mathcal{N}(\nu,2\nu)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\frac{\,X-\nu\,}{\sqrt{2\nu}}&\xrightarrow[~\nu~\text{夠大}~]{~\mathrm{a}~}\mathcal{N}(0,1)\\[0.45em]
\text{或}\quad X&\xrightarrow[~\nu~\text{夠大}~]{~\mathrm{a}~}\mathcal{N}(\nu,2\nu)
\end{aligned}
$$

</div>

(5) [伽瑪分配](/lecture-notes/gamma-distribution/#def-gamma-distribution) <span lang="en">(gamma distribution)</span> 漸近常態分配: 若 <span class="text-nowrap">$X\sim\mathrm{Gamma}(\alpha,\beta)$，</span>則有
{: .topic-paren-item}

$$
\frac{\,X-\alpha\beta\,}{\sqrt{\alpha\beta^{2}}}\dconv Z\sim\mathcal{N}(0,1)
$$

實務上，當 $\alpha$ 足夠大時，我們有
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\frac{\,X-\alpha\beta\,}{\sqrt{\alpha\beta^{2}}}\xrightarrow[~\alpha~\text{夠大}~]{~\mathrm{a}~}\mathcal{N}(0,1)\quad\text{或}\quad X\xrightarrow[~\alpha~\text{夠大}~]{~\mathrm{a}~}\mathcal{N}(\alpha\beta,\alpha\beta^{2})
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\frac{\,X-\alpha\beta\,}{\sqrt{\alpha\beta^{2}}}&\xrightarrow[~\alpha~\text{夠大}~]{~\mathrm{a}~}\mathcal{N}(0,1)\\[0.45em]
\text{或}\quad X&\xrightarrow[~\alpha~\text{夠大}~]{~\mathrm{a}~}\mathcal{N}(\alpha\beta,\alpha\beta^{2})
\end{aligned}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

具可加性的分配在漸近為常態分配時，流程其實都是相同的，就是先透過標準化的結構，由中央極限定理得知分配收斂於標準常態，再在有限的 $n$ 之下使用近似的結果反標準化。

實務上而言，只要 $n$ 很大，這個近似的結果不至於偏離太多，但至於多大的 $n$ 才能使得這個近似的結果足夠精確，則完全取決於實際的使用情境，[^cost] 沒有一個標準的說法。以實務上而言，普遍認為 $n\geqslant30$ 算是一個「大樣本」的分界點。

</div>

## 常態近似與極限分配的例題

<div id="ex-gamma-integral-limit" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.22</div>

<div lang="en" markdown="1">
Show that the central limit theorem implies

$$
\lim_{n\to\infty}\int_{0}^{n}e^{-t}\frac{t^{n-1}}{\,(n-1)!\,}\,dt=\frac{1}{\,2\,}
$$

</div>

可令 <span class="text-nowrap">$T\sim\mathrm{Gamma}(\alpha=n,\ \beta=1)$，</span>則我們有

$$
\int_{0}^{n}e^{-t}\frac{t^{n-1}}{\,(n-1)!\,}\,dt=\mathbb{P}(T\leqslant n)
$$

又由於 $\mathbb{E}(T)=n$ 且 <span class="text-nowrap">$\mathrm{Var}(T)=n$，</span>由中央極限定理可知

$$
\frac{\,T-n\,}{\sqrt{n}}\dconv\mathcal{N}(0,1)
$$

由此可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\lim_{n\to\infty}\int_{0}^{n}e^{-t}\frac{t^{n-1}}{\,(n-1)!\,}\,dt&=\lim_{n\to\infty}\mathbb{P}(T\leqslant n)\\[0.45em]
&=\lim_{n\to\infty}\mathbb{P}\biggl(\frac{\,T-n\,}{\sqrt{n}}\leqslant\frac{\,n-n\,}{\sqrt{n}}\biggr)\\[0.45em]
&=\Phi(0)=\frac{1}{\,2\,}
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\lim_{n\to\infty}\int_{0}^{n}e^{-t}\frac{t^{n-1}}{\,(n-1)!\,}\,dt\\[0.3em]
&=\lim_{n\to\infty}\mathbb{P}(T\leqslant n)\\[0.3em]
&=\lim_{n\to\infty}\mathbb{P}\biggl(\frac{\,T-n\,}{\sqrt{n}}\leqslant\frac{\,n-n\,}{\sqrt{n}}\biggr)\\[0.3em]
&=\Phi(0)=\frac{1}{\,2\,}
\end{aligned}
$$

</div>

</div>

<div id="ex-fair-game-loss-approximation" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.23</div>

<div lang="en" markdown="1">
Suppose that a gambler stakes $5$ dollars on each of $50$ independent fair games. Determine, by means of the central limit theorem, an approximation to the probability that the gambler loses more than $75$ dollars in total.
</div>

令 $X$ 表示 $50$ 次賭局之中贏的次數，可知

$$
X\sim\mathrm{Bin}\biggl(50,\ p=\frac{1}{\,2\,}\biggr)
$$

由題意敘述，輸超過 $75$ 元即表示 <span class="text-nowrap">$X-(50-X)<-15$，</span>其中 $(50-X)$ 表示輸的次數。又由中央極限定理的延伸可知

$$
\frac{\,X-50\times\frac{1}{\,2\,}\,}{\sqrt{50\times\frac{1}{\,2\,}\times\bigl(1-\frac{1}{\,2\,}\bigr)}}\xrightarrow[~\text{CLT}~]{~\mathrm{a}~}\mathcal{N}(0,1)
$$

故所求為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}\bigl(X-(50-X)<-15\bigr)&=\mathbb{P}(2X<35)=\mathbb{P}(X<17.5)\\[0.45em]
&=\mathbb{P}\Biggl(\frac{\,X-50\times\frac{1}{\,2\,}\,}{\sqrt{50\times\frac{1}{\,2\,}\times\bigl(1-\frac{1}{\,2\,}\bigr)}}<\frac{\,17.5-50\times\frac{1}{\,2\,}\,}{\sqrt{50\times\frac{1}{\,2\,}\times\bigl(1-\frac{1}{\,2\,}\bigr)}}\Biggr)\\[0.45em]
&\fallingdotseq\mathbb{P}(Z<-2.12)=0.017
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}\bigl(X-(50-X)<-15\bigr)\\[0.3em]
&=\mathbb{P}(2X<35)=\mathbb{P}(X<17.5)\\[0.3em]
&=\mathbb{P}\Biggl(\frac{\,X-50\times\frac{1}{\,2\,}\,}{\sqrt{50\times\frac{1}{\,2\,}\times\bigl(1-\frac{1}{\,2\,}\bigr)}}\\[0.2em]
&\qquad<\frac{\,17.5-50\times\frac{1}{\,2\,}\,}{\sqrt{50\times\frac{1}{\,2\,}\times\bigl(1-\frac{1}{\,2\,}\bigr)}}\Biggr)\\[0.3em]
&\fallingdotseq\mathbb{P}(Z<-2.12)=0.017
\end{aligned}
$$

</div>

</div>

<div id="ex-gamma-clt" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.24</div>

<div lang="en" markdown="1">
Suppose that $X_n$ follows the distribution <span class="text-nowrap">$\mathrm{Gamma}(n,\lambda)$,</span> whose mean is <span class="text-nowrap">$n/\lambda$,</span> where $n$ is an integer and <span class="text-nowrap">$\lambda>0$.</span> Find the limiting distribution of $(\lambda X_n-n)/\sqrt{n}$ as <span class="text-nowrap">$n\to\infty$,</span> by means of the central limit theorem.
</div>

由伽瑪分配的可加性可令 <span class="text-nowrap">$X_n=\sum_{i=1}^{n}Y_i$，</span>且其中

$$
Y_1,Y_2,\ldots,Y_n\iidto\mathrm{Exp}(\lambda)
$$

則由[指數分配](/lecture-notes/gamma-function-exponential-distribution/#def-exponential-distribution)的期望值與變異數可知

$$
\mathbb{E}(Y_i)=\frac{1}{\,\lambda\,},\quad\mathrm{Var}(Y_i)=\frac{1}{\,\lambda^{2}\,}
$$

由中央極限定理，我們可知

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\frac{\,\lambda X_n-n\,}{\sqrt{n}}=\frac{\,\sum_{i=1}^{n}Y_i-\frac{n}{\,\lambda\,}\,}{\sqrt{\frac{n}{\,\lambda^{2}\,}}}\dconv Z\sim\mathcal{N}(0,1)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\frac{\,\lambda X_n-n\,}{\sqrt{n}}&=\frac{\,\sum_{i=1}^{n}Y_i-\frac{n}{\,\lambda\,}\,}{\sqrt{\frac{n}{\,\lambda^{2}\,}}}\\[0.45em]
&\dconv Z\sim\mathcal{N}(0,1)
\end{aligned}
$$

</div>

</div>

<div id="ex-binomial-poisson-and-normal-approximations" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.25</div>

<div lang="en" markdown="1">
Suppose that $X_1,X_2,\ldots,X_n$ are independent and identically distributed Bernoulli random variables whose probability of success is <span class="text-nowrap">$\mathbb{E}(X)=p$.</span>

<ol class="topic-list-paren">
  <li>Let <span class="text-nowrap">$Y=\sum_{i=1}^{n}X_i$.</span> Determine the distribution of <span class="text-nowrap">$Y$,</span> together with its mean and its variance.</li>
  <li>Following the previous part, suppose further that the sample size $n$ is large, that $p$ is small, and that $n\times p$ stays constant. Determine the distribution by which $Y$ is approximated, together with its mean and its variance. Determine also the approximating distribution when $n\times p$ is not small, say <span class="text-nowrap">$n\times p\geqslant10$.</span></li>
  <li>Following part (1), suppose that $p$ is not too extreme, say <span class="text-nowrap">$0.2\leqslant p\leqslant0.8$,</span> and that the sample size $n$ is not too small. Determine the distribution by which the probability distribution of $Y$ is approximated, together with its mean and its variance.</li>
</ol>
</div>

(1) 由題意可知 <span class="text-nowrap">$X_1,X_2,\ldots,X_n\iidto\mathrm{Ber}(p)$，</span>則由[伯努利分配](/lecture-notes/bernoulli-trials-and-distribution/#def-bernoulli)的可加性可知
{: .topic-paren-item}

$$
Y=\sum_{i=1}^{n}X_i\sim\mathrm{Bin}(n,p)
$$

由此可得
{: .topic-paren-cont}

$$
\mathbb{E}(Y)=np,\quad\mathrm{Var}(Y)=np(1-p)
$$

(2) 承上題結果 <span class="text-nowrap">$Y\sim\mathrm{Bin}(n,p)$，</span>在 $n$ 很大但 $p$ 很小，且 $n\times p$ 為一個定值時，二項分配可由卜瓦松分配近似，也就是
{: .topic-paren-item}

<div class="topic-math-follow-before" markdown="1">

$$
Y\aconv\mathrm{Poi}(\lambda=np)
$$

</div>
<div class="topic-math-follow" markdown="1">
<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\Longrightarrow\ \mathbb{E}(Y)=\lambda=np,\ \mathrm{Var}(Y)=\lambda=np
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ \mathbb{E}(Y)&=\lambda=np,\\[0.2em]
\mathrm{Var}(Y)&=\lambda=np
\end{aligned}
$$

</div>
</div>

又當 $n\times p$ 是一個很大的定值 (題意令 $np\geqslant10$) 時，卜瓦松分配可再近似為常態分配，此即
{: .topic-paren-cont}

$$
Y\aconv\mathcal{N}(np,np)\qquad\therefore\, \mathbb{E}(Y)=np,\ \mathrm{Var}(Y)=np
$$

(3) 當 $p$ 不是一個太極端的值 (且題意假設 $n$ 不會太小) 時，二項分配可近似為常態分配，此即
{: .topic-paren-item}

<div class="topic-math-follow-before" markdown="1">

$$
Y\aconv\mathcal{N}\bigl(np,np(1-p)\bigr)
$$

</div>
<div class="topic-math-follow" markdown="1">
<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\Longrightarrow\ \mathbb{E}(Y)=np,\ \mathrm{Var}(Y)=np(1-p)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\Longrightarrow\ \mathbb{E}(Y)&=np,\\[0.2em]
\mathrm{Var}(Y)&=np(1-p)
\end{aligned}
$$

</div>
</div>

</div>

## 連續性校正

<div id="thm-continuity-correction" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 5.9 (連續性校正, continuity correction)</div>

若 $X$ 為定義在連續整數上的離散隨機變數，且 $X$ 可以連續隨機變數近似，則對任意整數 $a,b$ 且 <span class="text-nowrap">$a<b$，</span>我們有

(1)
{: .topic-paren-item}

$$
\mathbb{P}(a<X<b)\fallingdotseq\mathbb{P}(a+0.5<X<b-0.5)
$$

(2)
{: .topic-paren-item}

$$
\mathbb{P}(a\leqslant X\leqslant b)\fallingdotseq\mathbb{P}(a-0.5<X<b+0.5)
$$

(3)
{: .topic-paren-item}

$$
\mathbb{P}(X=a)\fallingdotseq\mathbb{P}(a-0.5<X<a+0.5)
$$

</div>

<div id="ex-sample-proportion-continuity-correction" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.26</div>

<div lang="en" markdown="1">
Suppose that a director of marketing research draws a random sample of $300$ households in Taipei City for a trial of a new toothpaste package, and that $40\%$ of the households in the city prefer the new package. What is the probability that the sample proportion of the households preferring the new package lies between $0.35$ and <span class="text-nowrap">$0.45$?</span>
</div>

由題目敘述可知，台北市中事實上有 $40\%$ 的家庭比較傾向於新的牙膏包裝，故令

$$
X_1,X_2,\ldots,X_{300}\iidto\mathrm{Ber}(p=0.4)
$$

表示該次抽樣的 $300$ 個樣本，並令 $\hat{p}=\frac{1}{\,300\,}\sum_{i=1}^{300}X_i$ 為樣本比例，則由[線性組合的變異數](/lecture-notes/variance-of-linear-combination/#thm-covar-proper2)可得

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\mathbb{E}(\hat{p})=\frac{1}{\,300\,}\sum_{i=1}^{300}\mathbb{E}(X_i)=0.4,\quad\mathrm{Var}(\hat{p})=\frac{1}{\,300^{2}\,}\sum_{i=1}^{300}\mathrm{Var}(X_i)=\frac{\,0.4\times0.6\,}{300}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\mathbb{E}(\hat{p})&=\frac{1}{\,300\,}\sum_{i=1}^{300}\mathbb{E}(X_i)=0.4,\\[0.45em]
\mathrm{Var}(\hat{p})&=\frac{1}{\,300^{2}\,}\sum_{i=1}^{300}\mathrm{Var}(X_i)\\[0.2em]
&=\frac{\,0.4\times0.6\,}{300}
\end{aligned}
$$

</div>

由中央極限定理可知

$$
\hat{p}\aconv\mathcal{N}\biggl(0.4,\ \frac{0.4\times0.6}{300}\biggr)
$$

則所求為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(0.35\leqslant\hat{p}\leqslant0.45)&=\mathbb{P}\Biggl(\frac{0.35-0.4}{\sqrt{\frac{0.4\times0.6}{300}}}\leqslant\frac{\hat{p}-0.4}{\sqrt{\frac{0.4\times0.6}{300}}}\leqslant\frac{0.45-0.4}{\sqrt{\frac{0.4\times0.6}{300}}}\Biggr)\\[0.45em]
&\fallingdotseq\mathbb{P}(-1.768\leqslant Z\leqslant1.768)=0.961-0.039=0.922
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(0.35\leqslant\hat{p}\leqslant0.45)\\[0.3em]
&=\mathbb{P}\Biggl(\frac{0.35-0.4}{\sqrt{\frac{0.4\times0.6}{300}}}\leqslant\frac{\hat{p}-0.4}{\sqrt{\frac{0.4\times0.6}{300}}}\\[0.2em]
&\qquad\qquad\leqslant\frac{0.45-0.4}{\sqrt{\frac{0.4\times0.6}{300}}}\Biggr)\\[0.3em]
&\fallingdotseq\mathbb{P}(-1.768\leqslant Z\leqslant1.768)\\[0.3em]
&=0.961-0.039=0.922
\end{aligned}
$$

</div>

另外，我們可以考慮連續性校正，則所求為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\begin{aligned}
\mathbb{P}(0.35\leqslant\hat{p}\leqslant0.45)&=\mathbb{P}\Biggl(300\times0.35\leqslant\sum_{i=1}^{300}X_i\leqslant300\times0.45\Biggr)\\[0.45em]
&=\mathbb{P}\Biggl(105\leqslant\sum_{i=1}^{300}X_i\leqslant135\Biggr)\\[0.45em]
&=\mathbb{P}\Biggl(104.5<\sum_{i=1}^{300}X_i<135.5\Biggr)\\[0.45em]
&=\mathbb{P}\Biggl(\frac{104.5-120}{\sqrt{72}}<\frac{\sum_{i=1}^{300}X_i-120}{\sqrt{72}}<\frac{135.5-120}{\sqrt{72}}\Biggr)\\[0.45em]
&\fallingdotseq\mathbb{P}(-1.827<Z<1.827)=0.966-0.034=0.932
\end{aligned}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
&\mathbb{P}(0.35\leqslant\hat{p}\leqslant0.45)\\[0.3em]
&=\mathbb{P}\Biggl(300\times0.35\leqslant\sum_{i=1}^{300}X_i\\[0.2em]
&\qquad\qquad\leqslant300\times0.45\Biggr)\\[0.3em]
&=\mathbb{P}\Biggl(105\leqslant\sum_{i=1}^{300}X_i\leqslant135\Biggr)\\[0.3em]
&=\mathbb{P}\Biggl(104.5<\sum_{i=1}^{300}X_i<135.5\Biggr)\\[0.3em]
&=\mathbb{P}\Biggl(\frac{104.5-120}{\sqrt{72}}<\frac{\sum_{i=1}^{300}X_i-120}{\sqrt{72}}\\[0.2em]
&\qquad\qquad<\frac{135.5-120}{\sqrt{72}}\Biggr)\\[0.3em]
&\fallingdotseq\mathbb{P}(-1.827<Z<1.827)\\[0.3em]
&=0.966-0.034=0.932
\end{aligned}
$$

</div>

</div>

## 本篇小結

本篇處理的是中央極限定理在有限樣本之下的用法。$n\to\infty$ 這個條件實務上無法達成，但中央極限定理本身描述的是一個逐步逼近的過程，因此只要 $n$ 足夠大，直接以標準常態計算所得的機率就落在可允許的誤差範圍之內，這時稱標準常態分配是 $\frac{\,\overline{X}-\mu\,}{\frac{\sigma}{\sqrt{n}}}$ 的漸近分配。這個記法並不嚴謹，使用時仍應由中央極限定理出發，依「寫出所求、由定理得到分配收斂、在有限而足夠大的 $n$ 之下改以標準常態計算」這三個步驟處理，[Example 5.21](#ex-uniform-sum-normal-approximation) 即為一次完整的示範。

標準化的結構之所以不可任意更動，是因為 $n\to\infty$ 時分子與分母原本會一起退化或一起發散，兩者斂散的速率相同，退化或發散的情形才得以相互抵銷。但在 $n$ 有限的漸近結果之下，反標準化不會遇到這個困擾，因而樣本平均數有 $\overline{X}\xrightarrow[~n~\text{足夠大}~]{~\mathrm{a}~}\mathcal{N}\bigl(\mu,\frac{\sigma^{2}}{n}\bigr)$ 這個近似，樣本和也有相應的兩種寫法。要留意的是，這些都是近似的結果，不是確切服從常態分配。

由於近似的來源是樣本平均數與樣本和，具有可加性的分配便都可以依同一套作法處理: 二項分配在 $np\geqslant5$ 且 $n(1-p)\geqslant5$、卜瓦松分配在 $\lambda\geqslant9$、負二項分配在 $r$ 足夠大、卡方分配在 $\nu$ 足夠大、伽瑪分配在 $\alpha$ 足夠大時，各自以其期望值與變異數作為近似常態分配的參數。至於 $n$ 要多大才夠，並沒有標準的說法，實務上普遍以 $n\geqslant30$ 作為大樣本的分界點。

四道例題分別示範四種用法: [Example 5.22](#ex-gamma-integral-limit) 把一個伽瑪分配的積分認成 $\mathbb{P}(T\leqslant n)$，再由中央極限定理得到 $\Phi(0)=\frac{1}{\,2\,}$；[Example 5.23](#ex-fair-game-loss-approximation) 把「輸超過 $75$ 元」翻譯成二項變數的不等式再作常態近似；[Example 5.24](#ex-gamma-clt) 把 $\mathrm{Gamma}(n,\lambda)$ 拆成 $n$ 個指數變數的和，$(\lambda X_n-n)/\sqrt{n}$ 因而正是標準化的形式；[Example 5.25](#ex-binomial-poisson-and-normal-approximations) 則把二項分配的兩種近似並列，$p$ 很小而 $np$ 為定值時用卜瓦松近似，$p$ 不極端時用常態近似。

最後的 [Theorem 5.9](#thm-continuity-correction) 處理的是以連續隨機變數近似定義在連續整數上的離散隨機變數時，區間端點應該放在哪裡: 嚴格不等式的兩端各向內挪 $0.5$、非嚴格不等式的兩端各向外挪 $0.5$，單點機率則換成寬度為 $1$ 的區間。[Example 5.26](#ex-sample-proportion-continuity-correction) 把同一個樣本比例的機率算了兩次，未經校正時得 $0.922$，經連續性校正之後得 $0.932$。

下一篇離開常態近似，回到機率收斂本身，處理機率收斂的運算性質與連續映射定理。

[^cost]: 當然，越大的樣本大小能夠得到越精確的結果，但受限於成本考量，我們往往只能在樣本大小上折衷。如何在有限的成本之下取得足夠精確的近似結果，是一個熱門的**統計最佳化 <span lang="en">(statistical optimization)</span>** 問題。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
