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
excerpt: "當樣本大小足夠大時，可依中央極限定理將標準常態分配視為標準化樣本平均數的漸近分配，進而導出樣本平均數與樣本和的常態近似。本篇整理五個具可加性常用分配的常態近似公式與經驗門檻，並說明以連續分配近似整數值離散分配時的連續性校正。"
---

[上一篇](/lecture-notes/weak-law-and-central-limit-theorem/)給出弱大數法則與[中央極限定理](/lecture-notes/weak-law-and-central-limit-theorem/#thm-central-limit-theorem)，並以例題說明標準化之後的樣本平均數如何[分配收斂](/lecture-notes/convergence-in-distribution/#def-converge-in-distribution)至標準常態。本篇處理的是同一件事在實務上的用法。

中央極限定理的各項前提之中，實務上無法真正達成的是樣本大小趨於無窮大這一條件。本篇先寫出「$n$ 足夠大時以標準常態計算」這個漸近的記法，並交代使用它時仍應由中央極限定理出發的三個步驟；接著說明在有限的 $n$ 之下反標準化不會受到退化或發散的困擾，因而樣本平均數與樣本和各有一個常態近似；再把同一套作法用在五個具有可加性的常用分配上，說明它們在什麼條件之下可以漸近為[常態分配](/lecture-notes/normal-distribution/#def-normal)。最後給出連續性校正，處理以連續分配近似離散分配時端點的位置。

## 漸近分配與常態近似

中央極限定理刻畫隨著樣本大小 $n$ 增大，標準化樣本平均數的抽樣分配逐步逼近標準常態分配、並於極限下分配收斂至 $\mathcal{N}(0,1)$ 的漸近性質。因此只要樣本大小**足夠大**，標準化樣本平均數的分配便會**足夠接近**標準常態分配，直接以標準常態分配計算機率的近似誤差亦落在可允許的範圍內，通常記為

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\frac{\,\overline{X}-\mu\,}{\frac{\sigma}{\sqrt{n}}}\xrightarrow[~n~\text{足夠大}~]{~\mathrm{a}~}\mathcal{N}(0,1)\quad\text{或}\quad\frac{\,\overline{X}-\mu\,}{\frac{\sigma}{\sqrt{n}}}\xrightarrow[~n~\text{足夠大}~]{~\bullet~}\mathcal{N}(0,1)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\frac{\,\overline{X}-\mu\,}{\frac{\sigma}{\sqrt{n}}}\xrightarrow[~n~\text{足夠大}~]{~\mathrm{a}~}\mathcal{N}(0,1)\\[0.45em]
\text{或}\quad\frac{\,\overline{X}-\mu\,}{\frac{\sigma}{\sqrt{n}}}\xrightarrow[~n~\text{足夠大}~]{~\bullet~}\mathcal{N}(0,1)
\end{gathered}
$$

</div>

上述寫法表示標準常態分配為 $\frac{\,\overline{X}-\mu\,}{\frac{\sigma}{\sqrt{n}}}$ 的**漸近分配 <span lang="en">(asymptotic distribution)</span>**。嚴格而言，此記法僅是部分教科書用以表達抽樣分配「相當接近常態」的簡記，並非嚴謹的數學收斂式；在正式論證中計算機率時，仍應從中央極限定理出發，依循下列步驟處理:

(1) 欲求取 $\mathbb{P}(a<\overline{X}<b)$
{: .topic-paren-item}

(2) 說明由中央極限定理可知
{: .topic-paren-item}

$$
\frac{\,\overline{X}-\mu\,}{\frac{\sigma}{\sqrt{n}}}\dconv Z\sim\mathcal{N}(0,1)
$$

(3) 在樣本大小 $n$ 有限但足夠大時，我們可以將所求轉化為
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

這個流程可以簡便地被化約為上述 $\frac{\,\overline{X}-\mu\,}{\frac{\sigma}{\sqrt{n}}}\xrightarrow[~n~\text{足夠大}~]{~\mathrm{a}~}\mathcal{N}(0,1)$ 的表示法，從而直接把所求的 $\mathbb{P}(a<\overline{X}<b)$ 近似為下式來處理

$$
\mathbb{P}\Biggl(\frac{a-\mu}{\frac{\sigma}{\sqrt{n}}}<Z<\frac{b-\mu}{\frac{\sigma}{\sqrt{n}}}\Biggr)
$$

<div id="ex-uniform-sum-normal-approximation" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.21</div>

<div lang="en" markdown="1">
Let $X_1,X_2,\ldots,X_{48}$ be iid $\mathcal{U}(0,1)$ random variables. Find the approximate probability $\mathbb{P}\Bigl(\sum_{i=1}^{48}X_i\geqslant26\Bigr)$.
</div>

令 $\lbrace X_i\rbrace_{i=1}^{\infty}\iidto\mathcal{U}(0,1)$ 為獨立同分配的序列，則由[均勻分配](/lecture-notes/uniform-distribution-integral-transform/#def-uniform-distribution)的期望值與變異數可知

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

在中央極限定理的極限式中，當 $n\to\infty$ 時分子與分母原本會同時收斂至 $0$ (樣本平均數形式) 或同時發散 (樣本和形式)，**仰賴兩者斂散速率相同方能將退化或發散相互抵銷**；此一尺度結構不可任意更動，換言之，在 $n\to\infty$ 的極限式之下，我們**不可對標準化形式任意移項作反標準化**。

相對地，前述由中央極限定理衍生的漸近分配，是在樣本大小 $n$ 有限但足夠大的條件下所得的近似關係；由於此時 $n$ 為有限常數，對 $\frac{\,\overline{X}-\mu\,}{\frac{\sigma}{\sqrt{n}}}\xrightarrow[~n~\text{足夠大}~]{~\mathrm{a}~}\mathcal{N}(0,1)$ 作線性反標準化並不會引發 $n\to\infty$ 下的退化或發散，由此可得

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
\begin{gathered}
\frac{\,\sum_{i=1}^{n}X_i-n\mu\,}{\sqrt{n}\,\sigma}\xrightarrow[~n~\text{足夠大}~]{~\mathrm{a}~}\mathcal{N}(0,1)\\[0.45em]
\text{或}\quad\sum_{i=1}^{n}X_i\xrightarrow[~n~\text{足夠大}~]{~\mathrm{a}~}\mathcal{N}(n\mu,n\sigma^{2})
\end{gathered}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

上述各式皆是依據中央極限定理、在有限大樣本下導出的常態近似關係，僅代表抽樣分配近似於常態分配；除非母體本身即為常態分配，否則 $\overline{X}$ 與 $\sum_{i=1}^{n}X_i$ 並非確切服從常態分配。

</div>

## 具可加性分配的常態近似

因為上述的近似結果都是源自於樣本平均數或樣本和，故針對具有可加性的常用分配，在某些參數足夠大的時候，我們可以將其漸近為常態分配，再行求算其機率，見下列結果。

(1) [二項分配](/lecture-notes/binomial-distribution/#def-binomial) <span lang="en">(binomial distribution)</span> 漸近常態分配: 若 <span class="text-nowrap">$X\sim\mathrm{Bin}(n,p)$，</span>則有
{: .topic-paren-item}

$$
\frac{\,X-np\,}{\sqrt{np(1-p)}}\dconv Z\sim\mathcal{N}(0,1)
$$

實務上，當 $np\geqslant5$ 與 $n(1-p)\geqslant5$ 同時成立時，我們有
{: .topic-paren-cont}

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\frac{X-np}{\sqrt{np(1-p)}}\xrightarrow[~np,~n(1-p)\geqslant5~]{~\mathrm{a}~}\mathcal{N}(0,1)\quad\text{或}\quad X\xrightarrow[~np,~n(1-p)\geqslant5~]{~\mathrm{a}~}\mathcal{N}\bigl(np,np(1-p)\bigr)
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{gathered}
\frac{X-np}{\sqrt{np(1-p)}}\xrightarrow[~np,~n(1-p)\geqslant5~]{~\mathrm{a}~}\mathcal{N}(0,1)\\[0.45em]
\text{或}\quad X\xrightarrow[~np,~n(1-p)\geqslant5~]{~\mathrm{a}~}\mathcal{N}\bigl(np,np(1-p)\bigr)
\end{gathered}
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
\begin{gathered}
\frac{\,X-\lambda\,}{\sqrt{\lambda}}\xrightarrow[~\lambda\geqslant9~]{~\mathrm{a}~}\mathcal{N}(0,1)\\[0.45em]
\text{或}\quad X\xrightarrow[~\lambda\geqslant9~]{~\mathrm{a}~}\mathcal{N}(\lambda,\lambda)
\end{gathered}
$$

</div>

(3) [負二項分配](/lecture-notes/negative-binomial-distribution/#def-negative-binomial) <span lang="en">(negative binomial distribution)</span> 漸近常態分配: 若隨機變數 <span class="text-nowrap">$X\sim\mathcal{NB}(r,p)$，</span>則有
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
\begin{gathered}
\frac{\,X-\frac{r}{\,p\,}\,}{\sqrt{\frac{\,r(1-p)\,}{p^{2}}}}\xrightarrow[~r~\text{夠大}~]{~\mathrm{a}~}\mathcal{N}(0,1)\\[0.45em]
\text{或}\quad X\xrightarrow[~r~\text{夠大}~]{~\mathrm{a}~}\mathcal{N}\biggl(\frac{\,r\,}{p},\frac{\,r(1-p)\,}{p^{2}}\biggr)
\end{gathered}
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
\begin{gathered}
\frac{\,X-\nu\,}{\sqrt{2\nu}}\xrightarrow[~\nu~\text{夠大}~]{~\mathrm{a}~}\mathcal{N}(0,1)\\[0.45em]
\text{或}\quad X\xrightarrow[~\nu~\text{夠大}~]{~\mathrm{a}~}\mathcal{N}(\nu,2\nu)
\end{gathered}
$$

</div>

(5) [伽瑪分配](/lecture-notes/gamma-distribution/#def-gamma-distribution) <span lang="en">(gamma distribution)</span> 漸近常態分配: 若 $X\sim\mathrm{Gamma}(\alpha,\beta)$ 成立，則有
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
\begin{gathered}
\frac{\,X-\alpha\beta\,}{\sqrt{\alpha\beta^{2}}}\xrightarrow[~\alpha~\text{夠大}~]{~\mathrm{a}~}\mathcal{N}(0,1)\\[0.45em]
\text{或}\quad X\xrightarrow[~\alpha~\text{夠大}~]{~\mathrm{a}~}\mathcal{N}(\alpha\beta,\alpha\beta^{2})
\end{gathered}
$$

</div>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

具可加性的分配在推導常態近似時皆依循同一流程，亦即將隨機變數表為獨立同分配變數之和，先由中央極限定理確立標準化結構分配收斂至 <span class="text-nowrap">$\mathcal{N}(0,1)$，</span>再於有限參數下反標準化而得近似常態分配。

至於樣本大小 $n$ 須達多大才能使近似結果足夠精確，取決於母體偏態程度與實際應用對精確度的要求，並無單一標準；應用上常以 $n\geqslant30$ 作為大樣本的經驗分界點。實務抽樣中，增大樣本大小雖可提高精確度，卻也伴隨更高的調查或實驗成本；如何在有限成本下配置樣本以取得足夠精確的近似，屬於**統計最佳化 <span lang="en">(statistical optimization)</span>** 的課題。

</div>

## 常態近似與極限分配的例題

<div id="ex-gamma-integral-limit" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.22</div>

<div lang="en" markdown="1">
Use the central limit theorem to show that

$$
\lim_{n\to\infty}\int_{0}^{n}e^{-t}\frac{t^{n-1}}{\,(n-1)!\,}\,dt=\frac{1}{\,2\,}
$$

</div>

可令 $T\sim\mathrm{Gamma}(\alpha=n,\ \beta=1)$ 服從伽瑪分配，則我們有

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
Suppose a gambler bets $5$ dollars on each of $50$ independent fair games. Use the central limit theorem to approximate the probability that the gambler loses more than $75$ dollars in total.
</div>

令 $X$ 表示 $50$ 次賭局中贏的次數，可知

$$
X\sim\mathrm{Bin}\biggl(50,\ p=\frac{1}{\,2\,}\biggr)
$$

由題意敘述，輸超過 $75$ 元即表示 <span class="text-nowrap">$X-(50-X)<-15$，</span>其中 $(50-X)$ 表輸之次數。又由 CLT 延伸可知

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
Let $X_n$ follow a $\mathrm{Gamma}(n,\lambda)$ distribution with mean <span class="text-nowrap">$n/\lambda$,</span> where $n$ is a positive integer and <span class="text-nowrap">$\lambda>0$.</span> Use the central limit theorem to find the limiting distribution of $(\lambda X_n-n)/\sqrt{n}$ as <span class="text-nowrap">$n\to\infty$.</span>
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
Let $X_1,\ldots,X_n$ be iid Bernoulli random variables with success probability <span class="text-nowrap">$\mathbb{E}(X)=p$.</span>

<ol class="topic-list-paren">
  <li>Let <span class="text-nowrap">$Y=\sum_{i=1}^{n}X_i$.</span> Find the distribution, mean, and variance of <span class="text-nowrap">$Y$.</span></li>
  <li>In <span class="text-nowrap">(1),</span> if the sample size $n$ is large, $p$ is small, and $n\times p$ remains constant, what distribution approximates <span class="text-nowrap">$Y$,</span> and what are its mean and variance? If $n\times p$ is also large (say <span class="text-nowrap">$n\times p\geqslant10$),</span> what further approximating distribution, mean, and variance apply?</li>
  <li>In <span class="text-nowrap">(1),</span> if $p$ is moderate (say <span class="text-nowrap">$0.2\leqslant p\leqslant0.8$)</span> and $n$ is sufficiently large, what distribution approximates <span class="text-nowrap">$Y$,</span> and what are its mean and variance?</li>
</ol>
</div>

(1) 由題意可知 $X_1,X_2,\ldots,X_n\iidto\mathrm{Ber}(p)$ 成立，則由[伯努利分配](/lecture-notes/bernoulli-trials-and-distribution/#def-bernoulli)的可加性可知
{: .topic-paren-item}

$$
Y=\sum_{i=1}^{n}X_i\sim\mathrm{Bin}(n,p)
$$

由此可得
{: .topic-paren-cont}

$$
\mathbb{E}(Y)=np,\quad\mathrm{Var}(Y)=np(1-p)
$$

(2) 承上題結果 <span class="text-nowrap">$Y\sim\mathrm{Bin}(n,p)$，</span>在 $n$ 很大但 $p$ 很小，且 $n\times p$ 為定值時，二項分配可由卜瓦松分配近似，此即
{: .topic-paren-item}

<div class="topic-math-follow-before" markdown="1">

$$
Y\aconv\mathrm{Poi}(\lambda=np)
$$

</div>
<div class="topic-math-follow" markdown="1">

$$
\Longrightarrow\ \mathbb{E}(Y)=\lambda=np,\ \mathrm{Var}(Y)=\lambda=np
$$

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

$$
\Longrightarrow\ \mathbb{E}(Y)=np,\ \mathrm{Var}(Y)=np(1-p)
$$

</div>

</div>

## 連續性校正

<div id="thm-continuity-correction" class="topic-box topic-box--theorem" markdown="1">
<div class="topic-box__label">Theorem 5.9 (連續性校正, continuity correction)</div>

若 $X$ 為定義在連續整數上的離散隨機變數，且 $X$ 可以連續隨機變數近似，則對任意整數 $a,b$ 且 <span class="text-nowrap">$a<b$，</span>我們有

<ol class="topic-list-paren topic-list-paren--math">
  <li>
  $$
  \mathbb{P}(a<X<b)\fallingdotseq\mathbb{P}(a+0.5<X<b-0.5)
  $$
  </li>
  <li>
  $$
  \mathbb{P}(a\leqslant X\leqslant b)\fallingdotseq\mathbb{P}(a-0.5<X<b+0.5)
  $$
  </li>
  <li>
  $$
  \mathbb{P}(X=a)\fallingdotseq\mathbb{P}(a-0.5<X<a+0.5)
  $$
  </li>
</ol>

</div>

<div id="ex-sample-proportion-continuity-correction" class="topic-box topic-box--example" markdown="1">
<div class="topic-box__label">Example 5.26</div>

<div lang="en" markdown="1">
A marketing researcher selects a random sample of $300$ households in Taipei City to test a new toothpaste package. If $40\%$ of all households in Taipei City prefer the new package, find the probability that the sample proportion preferring the new package is between $0.35$ and <span class="text-nowrap">$0.45$.</span>
</div>

依題意，台北市中有 $40\%$ 的家庭較傾向新的牙膏包裝，故令

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
\mathbb{E}(\hat{p})=\frac{1}{\,300\,}\sum_{i=1}^{300}\mathbb{E}(X_i)=0.4
$$

$$
\begin{aligned}
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

另外，若考慮連續性校正，則所求為

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

由於近似的來源是樣本平均數與樣本和，具有可加性的分配便都可以依同一套作法處理，二項分配在 $np\geqslant5$ 且 <span class="text-nowrap">$n(1-p)\geqslant5$、</span>卜瓦松分配在 <span class="text-nowrap">$\lambda\geqslant9$、</span>負二項分配在 $r$ 足夠大、卡方分配在 $\nu$ 足夠大、伽瑪分配在 $\alpha$ 足夠大時，各自以其期望值與變異數作為近似常態分配的參數。至於 $n$ 要多大才夠，並沒有標準的說法，實務上普遍以 $n\geqslant30$ 作為大樣本的分界點。

四道例題分別示範四種用法。[Example 5.22](#ex-gamma-integral-limit) 把一個伽瑪分配的積分認成機率 <span class="text-nowrap">$\mathbb{P}(T\leqslant n)$，</span>再由中央極限定理得到 <span class="text-nowrap">$\Phi(0)=\frac{1}{\,2\,}$；</span>[Example 5.23](#ex-fair-game-loss-approximation) 把「輸超過 $75$ 元」翻譯成二項變數的不等式再作常態近似；[Example 5.24](#ex-gamma-clt) 把 $\mathrm{Gamma}(n,\lambda)$ 拆成 $n$ 個指數變數的和，$(\lambda X_n-n)/\sqrt{n}$ 因而正是標準化的形式；[Example 5.25](#ex-binomial-poisson-and-normal-approximations) 則把二項分配的兩種近似並列，$p$ 很小而 $np$ 為定值時用卜瓦松近似，$p$ 不極端時用常態近似。

最後的 [Theorem 5.9](#thm-continuity-correction) 處理的是以連續隨機變數近似定義在連續整數上的離散隨機變數時，區間端點應該放在哪裡。嚴格不等式的兩端各向內挪 <span class="text-nowrap">$0.5$、</span>非嚴格不等式的兩端各向外挪 <span class="text-nowrap">$0.5$，</span>單點機率則換成寬度為 $1$ 的區間。[Example 5.26](#ex-sample-proportion-continuity-correction) 把同一個樣本比例的機率算了兩次，未經校正時得 <span class="text-nowrap">$0.922$，</span>經連續性校正之後得 <span class="text-nowrap">$0.932$。</span>

[下一篇](/lecture-notes/continuous-mapping-theorem/)離開常態近似，回到機率收斂本身，處理機率收斂的運算性質與連續映射定理。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Sheldon Ross. 2019. *A First Course in Probability*. 10th ed. Pearson.
- Robert V. Hogg, Joseph W. McKean, and Allen T. Craig. 2019. *Introduction to Mathematical Statistics*. 8th ed. Pearson.
- George Casella and Roger L. Berger. 2002. *Statistical Inference*. 2nd ed. Duxbury.
