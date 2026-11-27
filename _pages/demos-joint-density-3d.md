---
layout: archive
title: "3D Joint Density Surfaces, Conditional Slices, and Regression"
permalink: /demos/joint-density-3d/
author_profile: true
---

{% include base_path %}
{% include jd-3d-head.html current="hub" %}

<style>
  @media (min-width: 1024px) {
    #main {
      max-width: min(95vw, 1440px);
    }
    #main > .archive {
      padding-right: 0;
      width: calc(100% - 250px);
    }
  }
  .jd-group-title {
    margin: 1.35rem 0 0.65rem;
    font-size: 1.06rem;
    border-bottom: 1px solid var(--journal-divider);
    padding-bottom: 0.3rem;
  }
  .jd-cards {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(min(100%, 310px), 1fr));
    gap: 0.85rem;
    margin: 0.65rem 0 1.25rem;
  }
  .jd-card {
    padding: 0.85rem 0.95rem;
    border: 1px solid var(--journal-divider);
    border-left: 3px solid var(--journal-accent);
    background: var(--journal-bg);
    display: flex;
    flex-direction: column;
    justify-content: space-between;
  }
  .jd-card__meta {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    gap: 0.35rem;
    margin-bottom: 0.28rem;
    font-family: 'IBM Plex Mono', Menlo, Consolas, monospace;
    font-size: 0.72rem;
    color: var(--journal-ink-soft);
    letter-spacing: 0.01em;
    text-transform: none;
  }
  .jd-card__meta > span:first-child {
    letter-spacing: 0.04em;
    text-transform: uppercase;
    font-weight: 600;
  }
  .jd-card h3 {
    margin: 0 0 0.38rem;
    font-size: 1.0rem;
    line-height: 1.3;
  }
  .jd-card h3 a {
    color: var(--journal-ink);
    text-decoration: none;
    border-bottom: 1px solid var(--journal-accent);
  }
  .jd-card h3 a:hover {
    color: var(--journal-accent);
    text-decoration: none;
  }
  .jd-card p {
    margin: 0 0 0.55rem;
    font-size: 0.89rem;
    line-height: 1.48;
    color: var(--journal-ink);
  }
  .jd-card__foot {
    margin-top: auto;
  }
  .jd-card__topics {
    margin: 0 0 0.45rem;
    font-size: 0.79rem;
    color: var(--journal-ink-soft);
  }
  .jd-card__cta {
    display: inline-block;
    padding: 0.26rem 0.62rem;
    font-size: 0.77rem;
    letter-spacing: 0.03em;
    color: var(--journal-bg);
    background: var(--journal-accent);
    border-radius: 2px;
    text-decoration: none;
  }
  .jd-card__cta:hover {
    opacity: 0.92;
    color: var(--journal-bg);
    text-decoration: none;
  }
  .jd-table-wrap {
    overflow-x: auto;
    margin: 0.85rem 0 1.2rem;
  }
  .jd-table {
    width: 100%;
    border-collapse: collapse;
    border: none;
    font-size: 0.81rem;
    line-height: 1.38;
  }
  @media (max-width: 820px) {
    .jd-table {
      min-width: 660px;
    }
  }
  .jd-table thead {
    background: transparent;
    border-bottom: none;
  }
  .jd-table th,
  .jd-table td {
    padding: 0.42rem 0.34rem;
    border-right: none;
    border-bottom: 1px solid var(--journal-divider);
    text-align: left;
    vertical-align: middle;
  }
  .archive table.jd-table th,
  .archive table.jd-table td {
    padding: 0.52em 0.62em;
  }
  .jd-table th {
    font-size: 0.81rem;
    font-weight: 700;
    letter-spacing: normal;
    text-transform: none;
    color: var(--journal-ink);
    background: var(--global-thead-color);
    border-top: 1px solid var(--journal-ink);
    border-bottom: 1px solid var(--journal-ink);
  }
  .jd-table th:nth-child(3),
  .jd-table th:nth-child(4),
  .jd-table th:nth-child(5),
  .jd-table th:nth-child(6),
  .jd-table td:nth-child(5),
  .jd-table td:nth-child(6) {
    white-space: nowrap;
  }
  .jd-table td:first-child {
    min-width: 6.8rem;
  }
  .jd-table tbody tr:last-child td {
    border-bottom: 1px solid var(--journal-ink);
  }
</style>

A continuous bivariate [joint pdf](/lecture-notes/joint-probability-density-functions/#def-joint-pdf) $z=f_{\sssig XY}(x,y)$ encodes marginal densities on the side walls, conditional slices across cutting planes, direct and reverse [regression curves](/lecture-notes/double-expectation-theorem/#thm-regression-function) on the base plane, and dependence strength inside one surface. Each sub-page below presents the closed-form pdfs and parameter roles for one analytical distribution family, followed by a unified 3D/2D/1D workbench with spotlight layer dimming (`Focus`) and a pinned parameter dock.

<h2 class="jd-group-title">I. Conditional slices, slice centroids, and regression curves (before covariance)</h2>

<div class="jd-cards">
  <article class="jd-card">
    <div>
      <div class="jd-card__meta"><span>Lab 1</span><span>Renormalization &amp; Marginals</span></div>
      <h3><a href="/demos/slice-renormalization/">Conditional Slices, Side-Wall Marginals, and Area Renormalization</a></h3>
      <p>Plot the raw slice $f_{\sssig XY}(x_0,y)$, the renormalized conditional pdf $f_{\sssig Y\mid X}(y\mid x_0)$, and the side-wall marginals $f_{\sssig X}(x)$, $f_{\sssig Y}(y)$ on one common density scale. Contrast upward stretching ($f_{\sssig X}(x_0)&lt;1$), downward scaling ($f_{\sssig X}(0)&gt;1$), and independence ($\beta=0$) before introducing regression curves.</p>
    </div>
    <div class="jd-card__foot">
      <p class="jd-card__topics">Notes: <a href="/lecture-notes/marginal-probability-density-functions/#def-marginal-pdf">Marginal pdfs</a> · <a href="/lecture-notes/conditional-distributions/#def-conditional-pdf">Conditional Distributions</a> · <a href="/lecture-notes/independent-random-variables/#def-indep-r-v">Independent Random Variables</a></p>
      <a class="jd-card__cta" href="/demos/slice-renormalization/">Open Lab 1 &rarr;</a>
    </div>
  </article>

  <article class="jd-card">
    <div>
      <div class="jd-card__meta"><span>Lab 2</span><span>Centroid vs. slice peak</span></div>
      <h3><a href="/demos/skewed-slice-centroid/">Skewed Conditional Slices: Conditional Expectation as Centroid, Not Peak</a></h3>
      <p>Introduce $\mathbb{E}(Y\mid X=x_0)$ with right-skewed shifted $\mathrm{Gamma}(2,\theta(x))$ slices whose peak lies at $y_{\sssig\mathrm{mode}}(x)=\beta x$ whereas the center of gravity is pulled into the right tail at $\beta x+\theta(x)$, including straight peak ridges paired with curved regression functions.</p>
    </div>
    <div class="jd-card__foot">
      <p class="jd-card__topics">Notes: <a href="/lecture-notes/mode/#def-mode">Mode</a> · <a href="/lecture-notes/conditional-expectation-and-variance/#def-conditional-expectation">Conditional Expectation</a> · <a href="/lecture-notes/gamma-distribution/#def-gamma-distribution">Gamma Distribution</a></p>
      <a class="jd-card__cta" href="/demos/skewed-slice-centroid/">Open Lab 2 &rarr;</a>
    </div>
  </article>

  <article class="jd-card">
    <div>
      <div class="jd-card__meta"><span>Lab 3</span><span>Linear vs. tanh S-curve</span></div>
      <h3><a href="/demos/asymmetric-regression-mixture/">One-Way Linear Regression and Hyperbolic-Tangent S-Curves</a></h3>
      <p>Combine a symmetric two-component Gaussian mixture with homoscedastic linear noise so one regression curve is an exact straight line whereas the reverse regression bends into a closed-form $\tanh$ S-curve via Bayes’ theorem.</p>
    </div>
    <div class="jd-card__foot">
      <p class="jd-card__topics">Notes: <a href="/lecture-notes/bayes-rule-posterior-probability/#theorem-bayes-rule">Bayes’ Rule</a> · <a href="/lecture-notes/conditional-expectation-and-variance/#def-conditional-variance">Conditional Variance</a> · <a href="/lecture-notes/double-expectation-theorem/#thm-regression-function">Regression Function</a></p>
      <a class="jd-card__cta" href="/demos/asymmetric-regression-mixture/">Open Lab 3 &rarr;</a>
    </div>
  </article>

  <article class="jd-card">
    <div>
      <div class="jd-card__meta"><span>Lab 4</span><span>Valley Centroid</span></div>
      <h3><a href="/demos/bimodal-fork-regression/">Nonlinear Regression and Valley Centroids on a Bifurcating Ridge</a></h3>
      <p>Follow a curved ridge that splits smoothly into two symmetric crests for $x&gt;0$. Both direct and reverse regressions are nonlinear, and the conditional expectation sits in the low-density trough between the two peaks.</p>
    </div>
    <div class="jd-card__foot">
      <p class="jd-card__topics">Notes: <a href="/lecture-notes/double-expectation-theorem/#thm-double-expectation">Double Expectation Theorem</a></p>
      <a class="jd-card__cta" href="/demos/bimodal-fork-regression/">Open Lab 4 &rarr;</a>
    </div>
  </article>
</div>

<h2 class="jd-group-title">II. Independence, mean independence, and zero correlation</h2>

Walk step by step down the [one-way implication chain](/lecture-notes/covariance/#note-mean-independence) $X\indep Y \Longrightarrow \mathbb{E}(Y\mid X=x)=\mathbb{E}(Y) \Longrightarrow \operatorname{Cov}(X,Y)=0$ across three zero-covariance counterexamples:

<div class="jd-cards">
  <article class="jd-card">
    <div>
      <div class="jd-card__meta"><span>Lab 5</span><span>Two-way mean independence</span></div>
      <h3><a href="/demos/volcano-mean-independence/">Radially Symmetric Volcano Crater: Mean Independence Without Independence</a></h3>
      <p>Conditional slices change from bimodal at the crater center to unimodal in the tails (violating $X\indep Y$), yet radial symmetry keeps both $\mathbb{E}(Y\mid X=x)=0$ and $\mathbb{E}(X\mid Y=y)=0$ everywhere. Setting $\lambda=0$ recovers the independent normal benchmark.</p>
    </div>
    <div class="jd-card__foot">
      <p class="jd-card__topics">Notes: <a href="/lecture-notes/independent-random-variables/#def-indep-r-v">Independent Random Variables</a> · <a href="/lecture-notes/covariance/#def-covariance">Covariance</a></p>
      <a class="jd-card__cta" href="/demos/volcano-mean-independence/">Open Lab 5 &rarr;</a>
    </div>
  </article>

  <article class="jd-card">
    <div>
      <div class="jd-card__meta"><span>Lab 6</span><span>One-way mean independence</span></div>
      <h3><a href="/demos/parabolic-ridge-covariance/">Parabolic Ridge: One-Way Mean Independence and Zero Covariance</a></h3>
      <p>Here $\mathbb{E}(Y\mid X=x)=a(x^{2}-\sigma_1^{2})$ is quadratic, horizontal slices across the upper arms keep $\mathbb{E}(X\mid Y=y)=0$, and odd lobes of $x\,\mathbb{E}(Y\mid X=x)\,f_{\sssig X}(x)$ cancel pairwise to $\operatorname{Cov}(X,Y)=0$.</p>
    </div>
    <div class="jd-card__foot">
      <p class="jd-card__topics">Notes: <a href="/lecture-notes/covariance/#thm-covar-proper">Covariance Properties</a> · <a href="/lecture-notes/covariance/#note-mean-independence">Mean Independence</a></p>
      <a class="jd-card__cta" href="/demos/parabolic-ridge-covariance/">Open Lab 6 &rarr;</a>
    </div>
  </article>

  <article class="jd-card">
    <div>
      <div class="jd-card__meta"><span>Lab 7</span><span>Cov(X, Y) = 0 only</span></div>
      <h3><a href="/demos/stein-wave-uncorrelated/">Stein-Detrended Odd Wave: Zero Correlation Without Mean Independence</a></h3>
      <p>Under $h(x)=a[\sin(\omega x)-cx]$ with $c=\omega e^{-\omega^{2}\sigma_1^{2}/2}$, neither regression curve is constant, yet positive and negative bands of the even integrand cancel over $\mathbb{R}$ to exact zero correlation.</p>
    </div>
    <div class="jd-card__foot">
      <p class="jd-card__topics">Notes: <a href="/lecture-notes/correlation-coefficient/#def-corr">Correlation Coefficient</a> · <a href="/lecture-notes/standard-normal-moments-stein-lemma/#thm-stein-lemma">Stein’s Lemma</a></p>
      <a class="jd-card__cta" href="/demos/stein-wave-uncorrelated/">Open Lab 7 &rarr;</a>
    </div>
  </article>
</div>

<h2 class="jd-group-title">III. Bivariate normal geometry and three lines</h2>

<div class="jd-cards">
  <article class="jd-card">
    <div>
      <div class="jd-card__meta"><span>Lab 8</span><span>Ellipses &amp; Galton shrinkage</span></div>
      <h3><a href="/demos/bivariate-normal/">Bivariate Normal Surface, Conditional Slices, and Regression Lines</a></h3>
      <p>Contrast the direct regression line $\mathbb{E}(Y\mid X=x)=\rho(\sigma_2/\sigma_1)x$, the reverse regression line, and the major axis (geometric ridge) of the equal-density ellipses to see why each slice peaks at the contour tangent point rather than on the ridge.</p>
    </div>
    <div class="jd-card__foot">
      <p class="jd-card__topics">Notes: <a href="/lecture-notes/population-linear-regression/#thm-popu-reg">Population Linear Regression</a> · <a href="/lecture-notes/bivariate-normal-distribution/#def-bivariate-normal">Bivariate Normal Distribution</a></p>
      <a class="jd-card__cta" href="/demos/bivariate-normal/">Open Lab 8 &rarr;</a>
    </div>
  </article>
</div>

## Summary across all eight interactive labs

<div class="jd-table-wrap">
  <table class="jd-table">
    <thead>
      <tr>
        <th>Lab</th>
        <th>Distribution family</th>
        <th>Direct<br>$\mathbb{E}(Y\mid X=x)$</th>
        <th>Reverse<br>$\mathbb{E}(X\mid Y=y)$</th>
        <th>$X\indep Y$</th>
        <th>$\operatorname{Cov}(X,Y)$</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td><a href="/demos/slice-renormalization/">1. Slice Scaling</a></td>
        <td>Normal $X$, $Y\mid(X=x)\sim\mathcal{N}(\beta x,\tau^{2})$</td>
        <td>Not plotted (slice scaling focus)</td>
        <td>Not plotted (slice scaling focus)</td>
        <td>Iff $\beta=0$</td>
        <td>$\beta\sigma_1^{2}$</td>
      </tr>
      <tr>
        <td><a href="/demos/skewed-slice-centroid/">2. Centroid vs. Peak</a></td>
        <td>Normal $X$, shifted $\mathrm{Gamma}(2,\theta(x))$ for $Y\mid(X=x)$</td>
        <td>$\beta x+\theta(x)$ <span style="white-space:nowrap;">($\neq y_{\sssig\mathrm{mode}}(x)$)</span></td>
        <td>Curved in general</td>
        <td>Iff $\beta=\gamma=0$</td>
        <td>$(\beta+0.7\gamma)\sigma_1^{2}$</td>
      </tr>
      <tr>
        <td><a href="/demos/asymmetric-regression-mixture/">3. One-Way Linear</a></td>
        <td>2-component Gaussian mixture + noise</td>
        <td>Linear $\beta x$ (or $\tanh$)</td>
        <td>$\tanh$ (or linear $\beta y$)</td>
        <td>Iff $\beta=0$</td>
        <td>$\beta(\mu^{2}+s^{2})$</td>
      </tr>
      <tr>
        <td><a href="/demos/bimodal-fork-regression/">4. Bimodal Fork</a></td>
        <td>Curved baseline $g(x)$ + softplus fork $\pm\delta(x)$</td>
        <td>Curved $g(x)$ (valley)</td>
        <td>Curved in general</td>
        <td>Fails</td>
        <td>Nonzero for $a\neq 0$</td>
      </tr>
      <tr>
        <td><a href="/demos/volcano-mean-independence/">5. Volcano Crater</a></td>
        <td>Radially symmetric crater mixture <span style="white-space:nowrap;">($\lambda\in[0,1]$)</span></td>
        <td>Constant $0$</td>
        <td>Constant $0$</td>
        <td>Iff $\lambda=0$</td>
        <td>$0$</td>
      </tr>
      <tr>
        <td><a href="/demos/parabolic-ridge-covariance/">6. Parabolic Ridge</a></td>
        <td>Normal $X$, $Y\mid(X=x)$ <span style="white-space:nowrap;">$\sim\mathcal{N}\bigl(a(x^{2}-\sigma_1^{2}),\tau^{2}\bigr)$</span></td>
        <td>Quadratic $a(x^{2}-\sigma_1^{2})$</td>
        <td>Constant $0$</td>
        <td>Fails</td>
        <td>$0$</td>
      </tr>
      <tr>
        <td><a href="/demos/stein-wave-uncorrelated/">7. Odd Wave</a></td>
        <td>Normal $X$, $Y\mid(X=x)\sim\mathcal{N}(h(x),\tau^{2})$</td>
        <td>Oscillating $h(x)$</td>
        <td>Curved $\neq 0$</td>
        <td>Fails</td>
        <td>$0$</td>
      </tr>
      <tr>
        <td><a href="/demos/bivariate-normal/">8. Bivariate Normal</a></td>
        <td>$\mathcal{BN}(0,0,\sigma_1^{2},\sigma_2^{2},\rho)$</td>
        <td>Linear $\rho\frac{\sigma_2}{\sigma_1}x$</td>
        <td>Linear $\rho\frac{\sigma_1}{\sigma_2}y$</td>
        <td>Iff $\rho=0$</td>
        <td>$\rho\sigma_1\sigma_2$</td>
      </tr>
    </tbody>
  </table>
</div>
