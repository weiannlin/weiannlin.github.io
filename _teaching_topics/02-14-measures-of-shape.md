---
title: "形狀量數"
subtitle: "Measures of Shape"
layout: topic
collection: teaching_topics
category: "機率概論"
chapter: 2
topic: 14
order: 214
permalink: /lecture-notes/measures-of-shape/
date: 2026-08-06
published: true
excerpt: "形狀量數把一個分配的樣子化成數值。動差偏態係數 $\\alpha_{3}=\\mu_{3}/\\sigma_{X}^{3}$ 為正、為零、為負，分別對應右偏、對稱與左偏；皮爾森的兩個偏態係數則改由期望值與眾數、中位數之間的距離著手，背後是單峰分配中 $\\lvert\\mu_{X}-m_o\\rvert\\fallingdotseq3\\lvert\\mu_{X}-\\eta_{X}\\rvert$ 這個經驗法則。峰態係數 $\\alpha_{4}=\\mu_{4}/\\sigma_{X}^{4}$ 以常態分配的 $3$ 為比較基準，超額峰態係數則寫成 $\\kappa=\\alpha_{4}-3$；它衡量的是遠離期望值的取值所作的貢獻，不是峰的尖扁，因此改稱厚尾分配與薄尾分配。"
---

[上一篇](/lecture-notes/moment-system/)把[期望值](/lecture-notes/expectation/#def-expectation)與[變異數](/lecture-notes/variance/#def-variance)收進同一套架構之下，一階原動差就是期望值，二階主動差就是變異數。動差的階數再往上走，三階與四階的主動差各自帶著分配的另一面訊息，只是它們的大小同時受到分配尺度的影響，兩個不同單位的[隨機變數](/lecture-notes/random-variables-and-pmf/#def-random-variable)之間無從直接比較，要先除以[標準差](/lecture-notes/variance-standard-deviation/#def-standard-deviation)的相應次方，化成沒有單位的數值。

本篇介紹由此得到的兩個形狀量數。先給動差偏態係數，說明它把分配分成正偏、對稱與負偏三類的作法，以及背後奇函數與偶函數的直觀；接著介紹皮爾森的兩個偏態係數，它們改由期望值、[眾數](/lecture-notes/mode/#def-mode)與[中位數](/lecture-notes/median/#def-median)的相對位置著手，並附上皮爾森的經驗法則與一張三種偏斜情形的對照圖。其後轉入峰態係數，說明以 $3$ 作為比較基準的理由、超額峰態係數的寫法，以及為什麼往後一律改稱厚尾分配與薄尾分配，最後以一張圖比較三種峰態的尾端厚薄。

<div id="def-moment-skewness" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.13 (動差偏態係數, moment coefficient of skewness)</div>

若 $X$ 為一隨機變數，<span class="text-nowrap">$0<\sigma\_{\sssig X}<\infty$，</span>且 <span class="text-nowrap">$\mu\_{\sssig 3}=\mathbb{E}\bigl[(X-\mu\_{\sssig X})^{3}\bigr]<\infty$，</span>則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\alpha_{\sssig 3}=\mathbb{E}\Biggl[\biggl(\frac{X-\mu_{\sssig X}}{\sigma_{\sssig X}}\biggr)^{\!3}\Biggr]=\frac{\mathbb{E}\bigl[(X-\mu_{\sssig X})^{3}\bigr]}{\sigma_{\sssig X}^{3}}=\frac{\mu_{\sssig 3}}{\sigma_{\sssig X}^{3}}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\alpha_{\sssig 3}&=\mathbb{E}\Biggl[\biggl(\frac{X-\mu_{\sssig X}}{\sigma_{\sssig X}}\biggr)^{\!3}\Biggr]\\[0.45em]
&=\frac{\mathbb{E}\bigl[(X-\mu_{\sssig X})^{3}\bigr]}{\sigma_{\sssig X}^{3}}=\frac{\mu_{\sssig 3}}{\sigma_{\sssig X}^{3}}
\end{aligned}
$$

</div>

為 $X$ 之**動差偏態係數 <span lang="en">(moment coefficient of skewness)</span>**。

</div>

動差偏態係數有一些地方需要注意:

(1) 動差偏態係數常常被稱為**偏態係數 <span lang="en">(coefficient of skewness)</span>** 或**皮爾森動差偏態係數 <span lang="en">(Pearson’s moment coefficient of skewness)</span>**。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

這不該和稍後會提到的[**皮爾森偏態係數 <span lang="en">(Pearson’s coefficient of skewness)</span>**](#def-pearson-skewness) 混淆，因為動差偏態係數單純是由動差所定義的，二者間的差異相當明顯。

</div>

(2) **偏態 <span lang="en">(skewness)</span>** 主要是衡量一個分配的**偏斜程度**，或者反過來說，是在衡量一個分配的**對稱程度**。而偏態係數則是用數值化的方式，去度量其偏斜程度究竟有多少。我們將其簡單分類如下:
{: .topic-paren-item}

- 若 <span class="text-nowrap">$\alpha\_{\sssig 3}>0$，</span>則 $X$ 為**正偏分配 <span lang="en">(positive-skewed distribution)</span>** 或**右偏分配 <span lang="en">(right-skewed distribution)</span>**
- 若 <span class="text-nowrap">$\alpha\_{\sssig 3}=0$，</span>則此為**對稱分配 <span lang="en">(symmetric distribution)</span>** 的典型情形
- 若 <span class="text-nowrap">$\alpha\_{\sssig 3}<0$，</span>則 $X$ 為**負偏分配 <span lang="en">(negative-skewed distribution)</span>** 或**左偏分配 <span lang="en">(left-skewed distribution)</span>**

這個分類要配合分配的圖形一起判讀。若分配本身對稱且三階動差存在，則 <span class="text-nowrap">$\alpha\_{\sssig 3}=0$；</span>反過來說，單憑 $\alpha\_{\sssig 3}=0$ 並不足以保證分配對稱。
{: .topic-paren-cont}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

偏態係數有一個數學直觀是，$(X-\mu\_{\sssig X})^{3}$ 是一個以 $\mu\_{\sssig X}$ 為對稱點的奇函數 <span lang="en">(odd function)</span>，若 $X$ 是一個對稱分配，則 $f\_{\sssig X}(x)$ 應是一個對稱於 $\mu\_{\sssig X}$ 的偶函數 <span lang="en">(even function)</span>，那麼二者乘積的積分應為 <span class="text-nowrap">$0$；</span>故若偏態不為 <span class="text-nowrap">$0$，</span>則可由其偏態看出 $f\_{\sssig X}(x)$ 之偏向，進而得到偏態係數為正或負的結果。

</div>

偏斜程度也可以不從動差著手。下面兩個係數改以三個中央趨勢量數之間的距離來衡量偏斜。

<div id="def-pearson-skewness" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.14 (皮爾森偏態係數, Pearson’s coefficient of skewness)</div>

若 $X$ 為一隨機變數，則

(1) 令
{: .topic-paren-item}

$$
SK_{\sssig P_1}=\frac{\mu_{\sssig X}-m_o}{\sigma_{\sssig X}}
$$

則稱 $SK\_{\sssig P\_1}$ 為 $X$ 之**皮爾森第一偏態係數 <span lang="en">(Pearson’s first coefficient of skewness)</span>**，或稱**眾數偏態係數**。
{: .topic-paren-cont}

(2) 令
{: .topic-paren-item}

$$
SK_{\sssig P_2}=\frac{3\,(\mu_{\sssig X}-\eta_{\sssig X})}{\sigma_{\sssig X}}
$$

則稱 $SK\_{\sssig P\_2}$ 為 $X$ 之**皮爾森第二偏態係數 <span lang="en">(Pearson’s second coefficient of skewness)</span>**，或稱**中位數偏態係數**。
{: .topic-paren-cont}

</div>

上面兩式中的 $m_o$ 是 $X$ 的眾數，$\eta\_{\sssig X}$ 是 $X$ 的中位數，$\mu\_{\sssig X}$ 與 $\sigma\_{\sssig X}$ 則是 $X$ 的期望值與標準差。[Definition 2.9](/lecture-notes/mode/#def-mode) 把眾數界定為使機率函數在值域的閉包上取到最大值的那些點，這樣的點可能不只一個，也可能一個都沒有；上面兩個係數的用法，因而以眾數存在且唯一的單峰分配為主。

動差系統與偏態，最早都是由皮爾森 (Karl Pearson, 1857-1936) 創立與研究，其對統計的卓越貢獻，亦使之與費雪 (Ronald A. Fisher, 1890-1962) 被並稱為「近代統計學的兩大奠基者」。

皮爾森第一偏態係數與皮爾森第二偏態係數的設立，與皮爾森在研究分配的偏態時，所發現的一個經驗法則有關，這個經驗法則指出，在一個單峰的分配中，三個量數會有下面的關係

$$
\bigl\lvert\mu_{\sssig X}-m_o\bigr\rvert\fallingdotseq3\,\bigl\lvert\mu_{\sssig X}-\eta_{\sssig X}\bigr\rvert
$$

即**單峰分配期望值與眾數的距離，大約是期望值與中位數的距離的三倍**。

下面我們用圖示一併理解何謂右偏分配、左偏分配與對稱分配，並同時來看看皮爾森的經驗法則所指示的關係為何。

<figure id="fig-skewness-shapes" class="topic-figure topic-figure--wide">
  <img src="/images/lecture-notes/skewness-coefficients.svg" alt="三個上下並排的面板，各有一條橫軸，右端標 x。上面的面板是右偏的密度曲線，峰在偏左處，右側拖出長尾；曲線下方有三條靠得很近的垂直虛線落到橫軸，落點各有刻度，因間距太小，左右兩個標示各自往外移開，以一條斜引線接回自己的刻度，中間那一個仍在刻度正下方，由左至右為 m_o、η_X 與 μ_X，面板右側標 α_3 大於 0。中間的面板是同一條曲線左右翻轉，長尾在左側，虛線、刻度與標示同前，由左至右為 μ_X、η_X 與 m_o，面板左側標 α_3 小於 0。下面的面板是對稱的鐘形曲線，只有一條垂直虛線自峰頂落到橫軸，刻度正下方標為 m_o 等於 η_X 等於 μ_X，面板右側標 α_3 等於 0。">
  <figcaption><span class="topic-figure__label">Fig. 2.17.</span> 右偏、左偏與對稱三種分配的對照，三個面板共用同一段橫軸範圍與同一個縱向比例尺。上面的面板右偏，眾數、中位數與期望值由左至右分開；中間的面板左偏，三者的左右順序恰好相反；下面的面板對稱，三者同在一點。</figcaption>
</figure>

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

所謂正偏分配的「正」，乃是指偏態係數的正，而右偏分配的「右」，則是指該分配的「尾巴」偏向右邊。會特別強調「尾巴」的原因在於，以左偏及右偏稱呼一個分配的偏態時，時常會被誤會是一個分配的「峰」偏往哪邊，但事實上所謂的「偏」對應到的是「極端值的偏向」，也就是「尾巴的偏向」，而不是「峰的偏向」。

</div>

偏態處理的是分配的左右不對稱。若把三次方換成四次方，離差的正負號不再保留，被放大的是離期望值較遠的那些取值，由此得到另一個形狀量數。

<div id="def-kurtosis" class="topic-box topic-box--definition" markdown="1">
<div class="topic-box__label">Definition 2.15 (峰態係數, coefficient of kurtosis)</div>

若 $X$ 為一隨機變數，<span class="text-nowrap">$0<\sigma\_{\sssig X}<\infty$，</span>且 <span class="text-nowrap">$\mu\_{\sssig 4}=\mathbb{E}\bigl[(X-\mu\_{\sssig X})^{4}\bigr]<\infty$，</span>則

<div class="topic-math-layout topic-math-layout--desktop" markdown="1">

$$
\alpha_{\sssig 4}=\mathbb{E}\Biggl[\biggl(\frac{X-\mu_{\sssig X}}{\sigma_{\sssig X}}\biggr)^{\!4}\Biggr]=\frac{\mathbb{E}\bigl[(X-\mu_{\sssig X})^{4}\bigr]}{\sigma_{\sssig X}^{4}}=\frac{\mu_{\sssig 4}}{\sigma_{\sssig X}^{4}}
$$

</div>
<div class="topic-math-layout topic-math-layout--mobile" markdown="1">

$$
\begin{aligned}
\alpha_{\sssig 4}&=\mathbb{E}\Biggl[\biggl(\frac{X-\mu_{\sssig X}}{\sigma_{\sssig X}}\biggr)^{\!4}\Biggr]\\[0.45em]
&=\frac{\mathbb{E}\bigl[(X-\mu_{\sssig X})^{4}\bigr]}{\sigma_{\sssig X}^{4}}=\frac{\mu_{\sssig 4}}{\sigma_{\sssig X}^{4}}
\end{aligned}
$$

</div>

為 $X$ 之**峰態係數 <span lang="en">(coefficient of kurtosis)</span>**。

</div>

峰態係數有一些地方需要注意:

(1) **峰態 <span lang="en">(kurtosis)</span>** 衡量的是標準化之後的離差取四次方的平均，也就是遠離期望值的取值對這個平均所作的貢獻。我們將其簡單分類如下:
{: .topic-paren-item}

- 若 <span class="text-nowrap">$\alpha\_{\sssig 4}>3$，</span>則 $X$ 為**高狹峰分配 <span lang="en">(leptokurtic distribution)</span>** 或**超高斯分配 <span lang="en">(super-Gaussian distribution)</span>**、**厚尾分配 <span lang="en">(thick-tailed distribution)</span>**
- 若 <span class="text-nowrap">$\alpha\_{\sssig 4}=3$，</span>則 $X$ 為**常態峰分配 <span lang="en">(mesokurtic distribution)</span>**
- 若 <span class="text-nowrap">$\alpha\_{\sssig 4}<3$，</span>則 $X$ 為**低矮峰分配 <span lang="en">(platykurtic distribution)</span>** 或**亞高斯分配 <span lang="en">(sub-Gaussian distribution)</span>**、**薄尾分配 <span lang="en">(thin-tailed distribution)</span>**

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

關於峰態的主流中文翻譯，時常容易誤導讀者，這是比較遺憾的地方。高狹峰分配的字面意思，是這個分配會具有比常態分配更尖及更高的峰，但這個想法卻不一定正確，主要的原因在於高狹峰分配的評斷原則，應該是其分配的**尾部是不是比常態分配要來得厚實**；反之，低矮峰分配可能會被認為具有比常態分配更寬闊及更矮的峰，這個想法同樣未必正確，因為其評斷原則是該分配的**尾部是不是比常態分配要來得瘦薄**。因此，為避免混淆讀者，往後若需要提到關於峰態的敘述時，將以**厚尾分配**與**薄尾分配**稱之。

</div>

(2) 峰態係數之所以以 $3$ 為主要的比較對象，乃是因為其比較基準是**常態分配 <span lang="en">(normal distribution)</span>**，或稱為**高斯分配 <span lang="en">(Gaussian distribution)</span>**，而常態分配的峰態係數恰巧是 <span class="text-nowrap">$3$，</span>故我們以 $3$ 作為峰態的比較基準。也因此，部分書籍將峰態係數定為
{: .topic-paren-item}

$$
\kappa=\alpha_{\sssig 4}-3
$$

此為**超額峰態係數 <span lang="en">(coefficient of excess kurtosis)</span>**。
{: .topic-paren-cont}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

常態分配的峰態係數恰巧是 <span class="text-nowrap">$3$，</span>並不意味著所有峰態係數是 $3$ 的分配都是常態分配。

</div>

(3) 峰態係數亦有數學直觀意義，即**峰態係數衡量了遠離期望值的點的貢獻**。其原因在於峰態係數的積分架構，若遠離期望值的點有較高的比重，則峰態係數會因為那些點的機率密度較大，而導致積分的結果也較大；反之，若該分配有相當高的比重都聚集在期望值附近，則因為離差較小的地方具有很高的機率密度，故其積分結果也應比較小。
{: .topic-paren-item}

<div class="topic-box topic-box--note" markdown="1">
<div class="topic-box__label">Note</div>

峰態的概念不應該與變異數、標準差等分散趨勢的概念混淆，這些分散趨勢量數刻劃的是整體的分散性，是一種綜觀整筆資料的分散性的概念，但峰態特別關注的重點則在於是不是有「聚集於單點」的現象，只不過，我們衡量這種群聚現象的方式是以「分配的尾端」進行衡量。[Fig. 2.11](/lecture-notes/variance/#fig-variance-comparison) 所比較的正是前一種整體的分散性。

</div>

下面我們將各種峰態的分配畫在同一張圖上來比較其差異。

<figure id="fig-kurtosis-comparison" class="topic-figure topic-figure--wide">
  <img src="/images/lecture-notes/kurtosis-tail-comparison.svg" alt="三條機率密度曲線畫在同一組座標軸上，都以原點為中心，只以線型分辨。峰最高的一條是長虛線，在原點處形成一個尖角，兩側急降後一度低於實線，再往外兩條就併攏並貼近橫軸，長虛線一路延伸到圖的兩端。峰高居中的一條是實線的鐘形曲線。剩下的一條是點線，在中央維持一段水平，高度低於另外兩條的峰，兩端各以一段垂直的點線落到橫軸，落到軸上之後就不再往外延伸。橫軸上三個刻度落在原點與水平段的兩端，軸下各標其值，右端標 x。右上角的圖例分兩欄，左欄依序為長虛線的 Laplace、實線的 normal 與點線的 uniform，右欄是各自的峰態係數，上方有共用欄頭 α_4。">
  <figcaption><span class="topic-figure__label">Fig. 2.18.</span> 三條曲線分別為期望值 <span class="text-nowrap">$0$、</span>變異數 $1$ 的拉普拉斯分配 <span lang="en">(Laplace distribution)</span>、標準常態分配與均勻分配，峰態係數依序為 <span class="text-nowrap">$6$、</span>$3$ 與 <span class="text-nowrap">$\frac{9}{5}$，</span>正是 <span class="text-nowrap">$\alpha_{\sssig 4}>3$、</span>$\alpha_{\sssig 4}=3$ 與 <span class="text-nowrap">$\alpha_{\sssig 4}<3$ 的</span>具體例子。均勻分配的密度只在 $(-\sqrt{3},\sqrt{3})$ 上為正，在此之外直接為 <span class="text-nowrap">$0$；</span>任意兩個分配的尾端厚薄仍須另行比較。</figcaption>
</figure>

上圖中，與常態峰相比，$\alpha\_{\sssig 4}=6$ 的厚尾分配，雖然確實有比較窄而高的峰，但我們更該注意的是尾巴的部分，厚尾分配的尾部較常態峰更為厚實；而 $\alpha\_{\sssig 4}=\frac{9}{5}$ 的薄尾分配，雖然也確實有比較矮而廣闊的峰，但該分配到了某個點之後其機率密度便直接歸零，故我們可以說該分配**尾部已經薄到為 $0$ 了**，當然相較於常態峰是更為瘦薄的。

## 本篇小結

[Definition 2.13](#def-moment-skewness) 以 $\alpha\_{\sssig 3}=\mu\_{\sssig 3}/\sigma\_{\sssig X}^{3}$ 界定動差偏態係數，把三階主動差除以標準差的三次方，化成沒有單位的數值。$\alpha\_{\sssig 3}>0$ 為正偏分配 (右偏分配)、$\alpha\_{\sssig 3}<0$ 為負偏分配 (左偏分配)，對稱分配則是 $\alpha\_{\sssig 3}=0$ 的典型情形，反過來由 $\alpha\_{\sssig 3}=0$ 並不足以保證分配對稱。這個分類的直觀來自奇函數與偶函數。對稱分配的密度是偶函數，乘上以期望值為對稱點的奇函數 $(X-\mu\_{\sssig X})^{3}$ 之後，積分為 <span class="text-nowrap">$0$。</span>

[Definition 2.14](#def-pearson-skewness) 的兩個皮爾森偏態係數改由中央趨勢量數之間的距離著手。第一偏態係數用期望值與眾數的差，第二偏態係數用期望值與中位數的差再乘以 <span class="text-nowrap">$3$，</span>兩者所以能對得起來，靠的是單峰分配中 $\lvert\mu\_{\sssig X}-m_o\rvert\fallingdotseq3\lvert\mu\_{\sssig X}-\eta\_{\sssig X}\rvert$ 這個經驗法則。[Fig. 2.17](#fig-skewness-shapes) 把右偏、左偏與對稱三種情形排在一起，右偏那一個面板的三個量數由左至右依序分開，兩段距離之比 <span class="text-nowrap">$\fallingdotseq3.049$。</span>要留意的是，右偏的「右」指的是尾巴的偏向，不是峰的偏向。

[Definition 2.15](#def-kurtosis) 以 $\alpha\_{\sssig 4}=\mu\_{\sssig 4}/\sigma\_{\sssig X}^{4}$ 界定峰態係數，衡量的是遠離期望值的取值所作的貢獻。以常態分配的 $3$ 為比較基準，$\alpha\_{\sssig 4}>3$ 為厚尾分配、$\alpha\_{\sssig 4}=3$ 為常態峰分配、$\alpha\_{\sssig 4}<3$ 為薄尾分配，部分書籍另以 $\kappa=\alpha\_{\sssig 4}-3$ 這個超額峰態係數把基準移到 <span class="text-nowrap">$0$。</span>中文譯名容易讓人只看峰的尖扁，實際的判準在尾端的厚薄，[Fig. 2.18](#fig-kurtosis-comparison) 的三條曲線期望值與變異數都相同，差別正在尾端。[下一篇](/lecture-notes/moment-generating-functions/)介紹[動差母函數](/lecture-notes/moment-generating-functions/#def-mgf)，並以三道例題示範動差母函數的求算，以及如何由它算出各階動差。

## 參考文獻與延伸閱讀

- 黃文璋，2010，《機率論》，二版，華泰文化。
- Karl Pearson. 1895. “Contributions to the Mathematical Theory of Evolution. II. Skew Variation in Homogeneous Material.” *Philosophical Transactions of the Royal Society of London (A)* 186: 343–414.
- Peter H. Westfall. 2014. “Kurtosis as Peakedness, 1905–2014. R.I.P.” *The American Statistician* 68 (3): 191–195.
- Theodore M. Porter. 2004. *Karl Pearson: The Scientific Life in a Statistical Age*. Princeton University Press.
