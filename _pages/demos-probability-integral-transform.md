---
layout: archive
title: "Probability Integral Transform and Inverse Transform Sampling"
permalink: /demos/probability-integral-transform/
author_profile: true
---

{% include base_path %}

<style>
  .pit-demo {
    --pit-chart-height: 260px;
  }
  .pit-theory-stage {
    position: relative;
  }
  .pit-panel {
    margin: 1rem 0 1.25rem;
    padding: 0.9rem 1rem;
    border-left: 2px solid var(--journal-accent);
    background: var(--journal-accent-soft);
  }
  .pit-controls {
    position: relative;
  }
  .pit-control {
    min-width: 0;
  }
  .pit-control label {
    display: block;
    margin-bottom: 0.35rem;
    font-size: 0.95rem;
  }
  .pit-control select {
    width: 100%;
    min-height: 44px;
    box-sizing: border-box;
    padding: 0.45rem 0.6rem;
    color: var(--journal-ink);
    background: var(--journal-bg);
    border: 1px solid var(--journal-divider);
    border-radius: 2px;
    font: inherit;
  }
  .pit-range-head {
    display: flex;
    justify-content: space-between;
    gap: 0.75rem;
    align-items: baseline;
    padding-right: 5.25rem;
  }
  .pit-range-head output {
    color: var(--journal-accent);
    font-family: 'IBM Plex Mono', Menlo, Consolas, monospace;
    font-weight: 600;
  }
  .pit-control input[type="range"] {
    -webkit-appearance: none;
    appearance: none;
    display: block;
    width: calc(100% + 16px);
    min-height: 44px;
    margin: 0 0 0 -8px;
    padding: 0;
    background: transparent;
    cursor: pointer;
  }
  .pit-control input[type="range"]::-webkit-slider-runnable-track {
    height: 3px;
    border-radius: 2px;
    background: linear-gradient(
      to right,
      var(--journal-accent) 0%,
      var(--journal-accent) var(--pit-fill, 50%),
      var(--journal-divider) var(--pit-fill, 50%),
      var(--journal-divider) 100%
    );
  }
  .pit-control input[type="range"]::-moz-range-track {
    height: 3px;
    border: 0;
    border-radius: 2px;
    background: var(--journal-divider);
  }
  .pit-control input[type="range"]::-moz-range-progress {
    height: 3px;
    border-radius: 2px;
    background: var(--journal-accent);
  }
  .pit-control input[type="range"]::-webkit-slider-thumb {
    -webkit-appearance: none;
    width: 16px;
    height: 16px;
    margin-top: -6.5px;
    border: 2px solid var(--journal-bg);
    border-radius: 50%;
    background: var(--journal-accent);
    box-shadow: 0 1px 2px rgba(31, 28, 24, 0.25);
    cursor: pointer;
  }
  .pit-control input[type="range"]::-moz-range-thumb {
    width: 16px;
    height: 16px;
    border: 2px solid var(--journal-bg);
    border-radius: 50%;
    background: var(--journal-accent);
    box-shadow: 0 1px 2px rgba(31, 28, 24, 0.25);
    cursor: pointer;
  }
  .pit-range-ends {
    display: flex;
    justify-content: space-between;
    margin-top: -0.1rem;
    color: var(--journal-ink-soft);
    font-family: 'IBM Plex Mono', Menlo, Consolas, monospace;
    font-size: 0.76rem;
  }
  .pit-help {
    margin: 0.2rem 0 0;
    color: var(--journal-ink-soft);
    font-size: 0.88rem;
  }
  .pit-help--range {
    margin: -0.85rem 0 0.85rem;
  }
  .pit-actions {
    position: absolute;
    top: -0.1rem;
    right: 0;
    display: flex;
    flex-wrap: wrap;
    gap: 0.65rem;
    align-items: end;
  }
  .pit-button {
    min-height: 44px;
    padding: 0.55rem 1rem;
    cursor: pointer;
    color: var(--journal-ink);
    background: var(--journal-bg);
    border: 1px solid var(--journal-ink);
    border-radius: 2px;
    font-family: inherit;
    font-size: 0.82rem;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    font-feature-settings: "smcp" 1, "c2sc" 1, "kern" 1;
    transition: background 120ms, color 120ms;
  }
  .pit-button:hover {
    color: var(--journal-bg);
    background: var(--journal-ink);
  }
  .pit-button:disabled {
    cursor: not-allowed;
    opacity: 0.58;
  }
  .pit-button:focus-visible,
  .pit-control select:focus-visible,
  .pit-control input[type="range"]:focus-visible {
    outline: 3px solid var(--journal-accent);
    outline-offset: 3px;
  }
  .pit-formulas {
    margin: 1rem 0;
    overflow-x: auto;
    overflow-y: hidden;
    padding-bottom: 0.15rem;
    text-align: center;
  }
  .pit-formulas p {
    margin: 0;
  }
  .pit-demo mjx-container[display="true"] {
    overflow-x: auto;
    overflow-y: hidden;
    padding-bottom: 0.15rem;
  }
  .pit-function-grid {
    display: grid;
    grid-template-columns: repeat(3, minmax(0, 1fr));
    gap: 0.55rem;
    margin: 1rem 0;
  }
  .pit-chart-card {
    min-width: 0;
    padding: 0.55rem 0.4rem 0.5rem;
    border: 1px solid var(--journal-divider);
    background: var(--journal-bg);
  }
  .pit-chart-card h3 {
    margin: 0 0 0.15rem;
    min-height: 2.4em;
    font-size: 1rem;
  }
  .pit-chart-card p {
    min-height: 4.05em;
    margin: 0 0 0.35rem;
    color: var(--journal-ink-soft);
    font-size: 0.84rem;
    line-height: 1.35;
  }
  .pit-chart {
    display: block;
    width: 100%;
    height: auto;
    color: var(--journal-ink);
  }
  .pit-readout-grid {
    display: grid;
    grid-template-columns: repeat(4, minmax(0, 1fr));
    gap: 0.55rem;
    margin: 0.85rem 0;
  }
  .pit-readout-item {
    min-width: 0;
    padding: 0.55rem 0.65rem;
    border-top: 2px solid var(--journal-divider);
    background: var(--journal-accent-soft);
    background: color-mix(in srgb, var(--journal-accent-soft) 55%, transparent);
  }
  .pit-readout-item span {
    display: block;
    margin-bottom: 0.2rem;
    color: var(--journal-ink-soft);
    font-size: 0.78rem;
    line-height: 1.25;
  }
  .pit-readout-item strong {
    display: block;
    overflow-wrap: anywhere;
    color: var(--journal-accent);
    font-family: 'IBM Plex Mono', Menlo, Consolas, monospace;
    font-size: 0.9rem;
    line-height: 1.35;
  }
  .pit-composition {
    margin: 0.85rem 0 1.2rem;
    padding: 0.8rem 1rem;
    border-left: 2px solid var(--journal-accent);
    background: var(--journal-accent-soft);
    text-align: center;
  }
  .pit-composition p {
    margin: 0.2rem 0;
  }
  .pit-composition__route {
    font-family: 'IBM Plex Mono', Menlo, Consolas, monospace;
    font-size: 0.98rem;
  }
  .pit-composition__result {
    color: var(--journal-accent);
    font-weight: 600;
  }
  .pit-simulation-controls {
    display: grid;
    grid-template-columns: minmax(180px, 260px) auto;
    gap: 0.8rem;
    align-items: end;
    margin: 0.8rem 0 1rem;
  }
  .pit-histogram-grid {
    display: grid;
    grid-template-columns: repeat(2, minmax(0, 1fr));
    gap: 1rem;
    margin-top: 0.8rem;
  }
  .pit-histogram-card {
    min-width: 0;
    padding: 0.7rem 0.65rem 0.6rem;
    border: 1px solid var(--journal-divider);
    background: var(--journal-bg);
  }
  .pit-histogram-card h3 {
    margin: 0 0 0.25rem;
    font-size: 1rem;
  }
  .pit-histogram-card p {
    margin: 0 0 0.45rem;
    color: var(--journal-ink-soft);
    font-size: 0.86rem;
  }
  .pit-legend {
    display: flex;
    flex-wrap: wrap;
    gap: 0.55rem 1.2rem;
    margin: 0.55rem 0 0;
    color: var(--journal-ink-soft);
    font-size: 0.86rem;
  }
  .pit-legend span {
    display: inline-flex;
    gap: 0.42rem;
    align-items: center;
  }
  .pit-key {
    display: inline-block;
    width: 1.8rem;
    height: 0.72rem;
    box-sizing: border-box;
  }
  .pit-key--bars {
    background: var(--journal-accent);
    opacity: 0.55;
  }
  .pit-key--density {
    height: 0;
    border-top: 2px dashed var(--journal-ink);
  }
  .pit-status {
    margin: 0.8rem 0 0;
    padding: 0.55rem 0.85rem;
    border-left: 2px solid var(--journal-accent);
  }
  @media (max-width: 720px) {
    .pit-panel {
      position: sticky;
      top: 70px;
      z-index: 10;
      margin: 0.65rem 0 0.35rem;
      padding: 0.65rem 0.75rem;
      background: var(--journal-bg-warm);
      box-shadow: 0 6px 12px rgba(31, 28, 24, 0.12);
    }
    .pit-help--range {
      margin: 0.15rem 0 0.65rem;
    }
    .pit-function-grid {
      grid-template-columns: minmax(0, 1fr);
      grid-auto-flow: row;
      gap: 0.75rem;
    }
    .pit-chart-card {
      padding: 0.5rem 0.45rem 0.35rem;
    }
    .pit-chart-card h3 {
      min-height: 0;
      margin-bottom: 0.05rem;
      font-size: 0.98rem;
    }
    .pit-chart-card p {
      min-height: 0;
      margin-bottom: 0.15rem;
      font-size: 0.82rem;
      line-height: 1.3;
    }
    .pit-chart--theory {
      max-width: 430px;
      margin: 0 auto;
    }
  }
  @media (max-width: 980px) {
    .pit-histogram-grid {
      grid-template-columns: minmax(0, 1fr);
    }
  }
  @media (max-width: 760px) {
    .pit-readout-grid {
      grid-template-columns: repeat(2, minmax(0, 1fr));
    }
    .pit-histogram-grid {
      grid-template-columns: minmax(0, 1fr);
    }
  }
  @media (max-width: 520px) {
    .pit-panel {
      padding: 0.65rem 0.7rem;
    }
    .pit-simulation-controls,
    .pit-readout-grid {
      grid-template-columns: minmax(0, 1fr);
    }
    .pit-button {
      width: 100%;
    }
    #pit-play {
      width: auto;
    }
    .pit-composition {
      padding: 0.75rem;
    }
    .pit-composition__route {
      font-size: 0.88rem;
    }
  }
  @media (prefers-reduced-motion: reduce) {
    #main {
      animation: none !important;
    }
    .pit-button {
      transition: none;
    }
  }
</style>

[Proposition 2.18](/teaching-topics/continuous-random-variable-transformations/#proposition-218) connects a continuous CDF with the standard uniform distribution in both directions. This demo uses the standard Cauchy distribution because its pdf, CDF, and [quantile function](/teaching-topics/quantiles-and-median/#quantile-function) all have closed forms. Its heavy tails also make the changes in local slope especially visible.

The standard Cauchy distribution will be introduced in a later teaching topic. For now, only the following three functions are needed. Its CDF is continuous and strictly increasing, so its quantile function agrees with the ordinary inverse of the CDF. Write $Q=F^{-1}$. Then

<div class="pit-formulas" markdown="1">
$$
\begin{aligned}
f(x)
&=
\frac{1}{\pi(1+x^2)} \\[0.35em]
F(x)
&=
\frac{1}{2}
+
\frac{1}{\pi}\arctan(x) \\[0.35em]
Q(u)
&=
\tan\left(\pi\left(u-\frac{1}{2}\right)\right)
\end{aligned}
$$
</div>

<div class="pit-demo" data-pit-demo markdown="1">

## Follow one value through all three functions

Start with $u$ on the standard uniform scale and set $x=Q(u)$. The same $x$ is marked on the pdf and CDF, while the same $u$ is marked on the quantile function. Move the slider or play the values from left to right.

<div class="pit-theory-stage">
<div class="pit-panel">
  <div class="pit-controls">
    <div class="pit-control">
      <div class="pit-range-head">
        <label for="pit-u">Uniform input u</label>
        <output id="pit-u-value" for="pit-u">0.500</output>
      </div>
      <input id="pit-u" type="range" min="0.05" max="0.95" step="0.001" value="0.500" aria-describedby="pit-u-help pit-theory-summary">
      <div class="pit-range-ends" aria-hidden="true"><span>0.05</span><span>0.95</span></div>
    </div>
    <div class="pit-actions">
      <button class="pit-button" id="pit-play" type="button" aria-pressed="false" aria-controls="pit-pdf-chart pit-cdf-chart pit-quantile-chart pit-theory-summary">Play</button>
    </div>
  </div>
</div>
<p class="pit-help pit-help--range" id="pit-u-help">The displayed interval 0.05 ≤ u ≤ 0.95 keeps the Cauchy tails legible. It does not truncate the distribution.</p>

<div class="pit-function-grid" id="pit-function-grid">
  <section class="pit-chart-card" aria-labelledby="pit-pdf-heading">
    <h3 id="pit-pdf-heading">PDF: density height</h3>
    <p>The height $f(x)$ is the local slope of the CDF at the same $x$.</p>
    <svg id="pit-pdf-chart" class="pit-chart pit-chart--theory" viewBox="0 0 300 220" preserveAspectRatio="xMidYMid meet" role="img" aria-labelledby="pit-pdf-title pit-pdf-desc"></svg>
  </section>
  <section class="pit-chart-card" aria-labelledby="pit-cdf-heading">
    <h3 id="pit-cdf-heading">CDF: accumulated probability</h3>
    <p>The point $(x,u)$ satisfies $u=F(x)$, and the tangent has slope $f(x)$.</p>
    <svg id="pit-cdf-chart" class="pit-chart pit-chart--theory" viewBox="0 0 300 220" preserveAspectRatio="xMidYMid meet" role="img" aria-labelledby="pit-cdf-title pit-cdf-desc"></svg>
  </section>
  <section class="pit-chart-card" aria-labelledby="pit-quantile-heading">
    <h3 id="pit-quantile-heading">Quantile function: ordinary inverse</h3>
    <p>The point $(u,x)$ satisfies $x=Q(u)$, and its slope is $Q'(u)$.</p>
    <svg id="pit-quantile-chart" class="pit-chart pit-chart--theory" viewBox="0 0 300 220" preserveAspectRatio="xMidYMid meet" role="img" aria-labelledby="pit-quantile-title pit-quantile-desc"></svg>
  </section>
</div>

<div class="pit-readout-grid" id="pit-theory-summary">
  <div class="pit-readout-item">
    <span>Uniform input</span>
    <strong id="pit-readout-u">u = 0.500</strong>
  </div>
  <div class="pit-readout-item">
    <span>Cauchy value</span>
    <strong id="pit-readout-x">x = Q(u) = 0.000</strong>
  </div>
  <div class="pit-readout-item">
    <span>CDF slope</span>
    <strong id="pit-readout-f">f(x) = 0.3183</strong>
  </div>
  <div class="pit-readout-item">
    <span>Quantile slope</span>
    <strong id="pit-readout-qprime">Q′(u) = 3.1416</strong>
  </div>
</div>

<div class="pit-composition" aria-live="off">
  <p class="pit-composition__route" id="pit-route">u = 0.500 → Q(u) = 0.000 → F(Q(u)) = 0.500</p>
  <p class="pit-composition__result" id="pit-product">f(Q(u))Q′(u) = 1.0000</p>
</div>
</div>

## Why the two slopes cancel

The pdf gives the local slope of the CDF, so $F'(x)=f(x)$. At the corresponding point $x=Q(u)$, the inverse-function rule gives

$$
Q'(u)
=
\frac{1}{f(Q(u))}
$$

Therefore, the chain rule gives

$$
\frac{d}{du}F(Q(u))
=
f(Q(u))Q'(u)
=
1
$$

The quantile function is not linear. Near $u=0.5$, it changes relatively slowly; near $0$ or $1$, it moves rapidly into the Cauchy tails. The linear growth appears only after $Q$ and $F$ are composed:

$$
F(Q(u))=u
$$

For $0<u<1$, this agrees with the linear part of the standard uniform CDF, and the identity extends continuously to the two endpoints. Because the three charts use different axis scales, the apparent angles of the two tangents should not be compared directly. The displayed derivative values and their product give the relevant comparison.

## Generate a Cauchy sample

The same relationship can be used as an algorithm. Generate independent standard-uniform values $U_1,\ldots,U_n$, and then, for $i=1,\ldots,n$, set

$$
X_i
=
Q(U_i)
=
\tan\left(\pi\left(U_i-\frac{1}{2}\right)\right)
$$

The first histogram should be approximately flat. The second should follow the standard Cauchy density. Uniform values close to $0$ or $1$ are sent far into the Cauchy tails.

<div class="pit-simulation-controls">
  <div class="pit-control">
    <label for="pit-sample-size">Sample size</label>
    <select id="pit-sample-size">
      <option value="100">100</option>
      <option value="500" selected>500</option>
      <option value="2000">2,000</option>
    </select>
  </div>
  <div class="pit-actions">
    <button class="pit-button" id="pit-generate" type="button" aria-controls="pit-uniform-histogram pit-cauchy-histogram pit-sample-status">Generate another sample</button>
  </div>
</div>

<div class="pit-histogram-grid">
  <section class="pit-histogram-card" aria-labelledby="pit-uniform-heading">
    <h3 id="pit-uniform-heading">Before: uniform inputs</h3>
    <p>Histogram of $U_1,\ldots,U_n$ with the density $f_U(u)=1$.</p>
    <svg id="pit-uniform-histogram" class="pit-chart" viewBox="0 0 430 280" preserveAspectRatio="xMidYMid meet" role="img" aria-labelledby="pit-uniform-title pit-uniform-desc"></svg>
  </section>
  <section class="pit-histogram-card" aria-labelledby="pit-cauchy-heading">
    <h3 id="pit-cauchy-heading">After: Cauchy values</h3>
    <p>Histogram of $X_i=Q(U_i)$ with the standard Cauchy pdf.</p>
    <svg id="pit-cauchy-histogram" class="pit-chart" viewBox="0 0 430 280" preserveAspectRatio="xMidYMid meet" role="img" aria-labelledby="pit-cauchy-title pit-cauchy-desc"></svg>
  </section>
</div>

<div class="pit-legend" aria-label="Histogram legend">
  <span><i class="pit-key pit-key--bars" aria-hidden="true"></i>Histogram density</span>
  <span><i class="pit-key pit-key--density" aria-hidden="true"></i>Theoretical density</span>
</div>

<p class="pit-status" id="pit-sample-status" role="status" aria-live="polite"></p>

</div>

## What to notice

**One control links both directions.** Reading from $x$ to $u=F(x)$ is the forward probability integral transform. Reading from $u$ to $x=Q(u)$ is inverse transform sampling.

**The CDF records where probability accumulates.** A large pdf height makes the CDF rise quickly. The quantile function compensates by moving through the corresponding $x$ values more slowly. In the tails, the pdf is small, so the quantile function must move much farther for the same change in $u$.

**The composition follows the uniform CDF, not the quantile curve.** The cancellation is expressed by $f(Q(u))Q'(u)=1$. Consequently, $F(Q(u))=u$ grows linearly even though neither the Cauchy CDF nor its quantile function is linear.

**The plotted Cauchy range is incomplete.** The simulation chart displays only the central interval from $Q(0.05)$ to $Q(0.95)$. Tail observations are counted below the chart, and every histogram density is divided by the full sample size rather than only by the number of visible observations.

The proof, the quantile-function formula used by the transform, and the endpoint convention are in [Proposition 2.18](/teaching-topics/continuous-random-variable-transformations/#proposition-218). To review how a density builds a CDF before applying the transformation, see [From PDF to CDF](/demos/pdf-cdf/).

<script>
(function () {
  const root = document.querySelector('[data-pit-demo]');
  if (!root) return;

  const uSlider = root.querySelector('#pit-u');
  const uOutput = root.querySelector('#pit-u-value');
  const playButton = root.querySelector('#pit-play');
  const pdfChart = root.querySelector('#pit-pdf-chart');
  const cdfChart = root.querySelector('#pit-cdf-chart');
  const quantileChart = root.querySelector('#pit-quantile-chart');
  const readoutU = root.querySelector('#pit-readout-u');
  const readoutX = root.querySelector('#pit-readout-x');
  const readoutF = root.querySelector('#pit-readout-f');
  const readoutQPrime = root.querySelector('#pit-readout-qprime');
  const route = root.querySelector('#pit-route');
  const product = root.querySelector('#pit-product');
  const sampleSizeSelect = root.querySelector('#pit-sample-size');
  const generateButton = root.querySelector('#pit-generate');
  const uniformHistogram = root.querySelector('#pit-uniform-histogram');
  const cauchyHistogram = root.querySelector('#pit-cauchy-histogram');
  const sampleStatus = root.querySelector('#pit-sample-status');

  const PI = Math.PI;
  const U_MIN = 0.05;
  const U_MAX = 0.95;
  const X_MIN = -6.5;
  const X_MAX = 6.5;
  const HIST_X_MIN = Math.tan(PI * (U_MIN - 0.5));
  const HIST_X_MAX = Math.tan(PI * (U_MAX - 0.5));
  const theoryLayoutQuery = window.matchMedia('(max-width: 720px)');
  const THEORY_LAYOUT = theoryLayoutQuery.matches ? {
    width: 430,
    height: 200,
    margin: { left: 52, right: 18, top: 10, bottom: 44 }
  } : {
    width: 300,
    height: 220,
    margin: { left: 44, right: 20, top: 10, bottom: 48 }
  };
  const HIST_LAYOUT = {
    width: 430,
    height: 280,
    margin: { left: 54, right: 14, top: 15, bottom: 48 }
  };

  let playing = false;
  let animationFrame = 0;
  let previousTime = 0;
  let playbackValue = parseFloat(uSlider.value);
  let randomState = 0x51f15e5d;
  let sampleNumber = 0;
  let theoryElements = {};

  function cauchyPDF(x) {
    return 1 / (PI * (1 + x * x));
  }

  function cauchyCDF(x) {
    return 0.5 + Math.atan(x) / PI;
  }

  function cauchyQuantile(u) {
    return Math.tan(PI * (u - 0.5));
  }

  function quantileDerivative(u) {
    const x = cauchyQuantile(u);
    return PI * (1 + x * x);
  }

  function nextUniform() {
    randomState = (Math.imul(1664525, randomState) + 1013904223) >>> 0;
    return (randomState + 0.5) / 4294967296;
  }

  function formatNumber(value, digits) {
    const rounded = value.toFixed(digits);
    if (rounded === '-0.000' || rounded === '-0.0000') {
      return digits === 3 ? '0.000' : '0.0000';
    }
    return rounded.replace('-', '−');
  }

  function tickLabel(value) {
    if (Number.isInteger(value)) return String(value).replace('-', '−');
    return value.toFixed(2).replace(/0+$/, '').replace(/\.$/, '').replace('-', '−');
  }

  function makeScales(layout, xMin, xMax, yMin, yMax) {
    const innerWidth = layout.width - layout.margin.left - layout.margin.right;
    const innerHeight = layout.height - layout.margin.top - layout.margin.bottom;
    return {
      innerWidth: innerWidth,
      innerHeight: innerHeight,
      x: function (value) {
        return layout.margin.left +
          ((value - xMin) / (xMax - xMin)) * innerWidth;
      },
      y: function (value) {
        return layout.margin.top +
          (1 - (value - yMin) / (yMax - yMin)) * innerHeight;
      }
    };
  }

  function axesMarkup(layout, scales, xTicks, yTicks, xLabel, yLabel) {
    const m = layout.margin;
    const bottom = m.top + scales.innerHeight;
    let html = '';
    html += '<rect x="' + m.left + '" y="' + m.top + '" width="' +
      scales.innerWidth + '" height="' + scales.innerHeight +
      '" fill="none" stroke="var(--journal-divider)"/>';

    yTicks.forEach(function (value) {
      const y = scales.y(value);
      html += '<line x1="' + m.left + '" y1="' + y.toFixed(2) +
        '" x2="' + (m.left + scales.innerWidth) + '" y2="' + y.toFixed(2) +
        '" stroke="var(--journal-divider-soft)"/>';
      html += '<text x="' + (m.left - 7) + '" y="' + (y + 4).toFixed(2) +
        '" text-anchor="end" fill="currentColor" font-size="15" opacity="0.76">' +
        tickLabel(value) + '</text>';
    });

    xTicks.forEach(function (value) {
      const x = scales.x(value);
      html += '<line x1="' + x.toFixed(2) + '" y1="' + bottom +
        '" x2="' + x.toFixed(2) + '" y2="' + (bottom + 5) +
        '" stroke="currentColor" opacity="0.55"/>';
      html += '<text x="' + x.toFixed(2) + '" y="' + (bottom + 18) +
        '" text-anchor="middle" fill="currentColor" font-size="15" opacity="0.76">' +
        tickLabel(value) + '</text>';
    });

    html += '<text x="' + (m.left + scales.innerWidth / 2).toFixed(2) +
      '" y="' + (layout.height - 5) +
      '" text-anchor="middle" fill="currentColor" font-size="16" opacity="0.82">' +
      xLabel + '</text>';
    html += '<text x="14" y="' + (m.top + scales.innerHeight / 2).toFixed(2) +
      '" text-anchor="middle" fill="currentColor" font-size="16" opacity="0.82"' +
      ' transform="rotate(-90 14 ' +
      (m.top + scales.innerHeight / 2).toFixed(2) + ')">' +
      yLabel + '</text>';
    return html;
  }

  function pathMarkup(fn, xMin, xMax, points, scales, stroke, width, dash) {
    let path = '';
    for (let i = 0; i <= points; i += 1) {
      const value = xMin + (xMax - xMin) * i / points;
      path += (i === 0 ? 'M' : 'L') +
        scales.x(value).toFixed(2) + ',' + scales.y(fn(value)).toFixed(2);
    }
    return '<path d="' + path + '" fill="none" stroke="' + stroke +
      '" stroke-width="' + width + '"' +
      (dash ? ' stroke-dasharray="' + dash + '"' : '') + '/>';
  }

  function initializeTheoryCharts() {
    const viewBox = '0 0 ' + THEORY_LAYOUT.width + ' ' + THEORY_LAYOUT.height;
    pdfChart.setAttribute('viewBox', viewBox);
    cdfChart.setAttribute('viewBox', viewBox);
    quantileChart.setAttribute('viewBox', viewBox);
    const pdfScales = makeScales(THEORY_LAYOUT, X_MIN, X_MAX, 0, 0.34);
    const cdfScales = makeScales(THEORY_LAYOUT, X_MIN, X_MAX, 0, 1);
    const quantileScales = makeScales(THEORY_LAYOUT, U_MIN, U_MAX, X_MIN, X_MAX);
    const bottom = THEORY_LAYOUT.margin.top + pdfScales.innerHeight;

    let pdfHTML = '<title id="pit-pdf-title">Standard Cauchy probability density function</title>';
    pdfHTML += '<desc id="pit-pdf-desc">The density curve with a marker at the current Cauchy value.</desc>';
    pdfHTML += axesMarkup(
      THEORY_LAYOUT,
      pdfScales,
      [-6, -3, 0, 3, 6],
      [0, 0.1, 0.2, 0.3],
      'x',
      'f(x)'
    );
    pdfHTML += pathMarkup(cauchyPDF, X_MIN, X_MAX, 260, pdfScales, 'var(--journal-ink)', 2.4, '');
    pdfHTML += '<line id="pit-pdf-guide" x1="0" y1="' + bottom +
      '" x2="0" y2="0" stroke="var(--journal-accent)" stroke-width="1.7"' +
      ' stroke-dasharray="7 5"/>';
    pdfHTML += '<circle id="pit-pdf-marker" cx="0" cy="0" r="5.2"' +
      ' fill="var(--journal-accent)" stroke="var(--journal-bg)" stroke-width="1.4"/>';
    pdfChart.innerHTML = pdfHTML;

    let cdfHTML = '<title id="pit-cdf-title">Standard Cauchy cumulative distribution function</title>';
    cdfHTML += '<desc id="pit-cdf-desc">The CDF with a marker and tangent at the current Cauchy value.</desc>';
    cdfHTML += '<defs><clipPath id="pit-cdf-clip"><rect x="' +
      THEORY_LAYOUT.margin.left + '" y="' + THEORY_LAYOUT.margin.top +
      '" width="' + cdfScales.innerWidth + '" height="' + cdfScales.innerHeight +
      '"/></clipPath></defs>';
    cdfHTML += axesMarkup(
      THEORY_LAYOUT,
      cdfScales,
      [-6, -3, 0, 3, 6],
      [0, 0.25, 0.5, 0.75, 1],
      'x',
      'F(x)'
    );
    cdfHTML += pathMarkup(cauchyCDF, X_MIN, X_MAX, 260, cdfScales, 'var(--journal-ink)', 2.4, '');
    cdfHTML += '<g clip-path="url(#pit-cdf-clip)">';
    cdfHTML += '<line id="pit-cdf-v-guide" x1="0" y1="0" x2="0" y2="0"' +
      ' stroke="var(--journal-ink-soft)" stroke-width="1.5" stroke-dasharray="7 5"/>';
    cdfHTML += '<line id="pit-cdf-h-guide" x1="0" y1="0" x2="0" y2="0"' +
      ' stroke="var(--journal-ink-soft)" stroke-width="1.5" stroke-dasharray="7 5"/>';
    cdfHTML += '<line id="pit-cdf-tangent" x1="0" y1="0" x2="0" y2="0"' +
      ' stroke="var(--journal-accent)" stroke-width="2.1"/>';
    cdfHTML += '</g>';
    cdfHTML += '<circle id="pit-cdf-marker" cx="0" cy="0" r="5.2"' +
      ' fill="var(--journal-accent)" stroke="var(--journal-bg)" stroke-width="1.4"/>';
    cdfChart.innerHTML = cdfHTML;

    let quantileHTML = '<title id="pit-quantile-title">Standard Cauchy quantile function</title>';
    quantileHTML += '<desc id="pit-quantile-desc">The quantile function with a marker and tangent at the current uniform input.</desc>';
    quantileHTML += '<defs><clipPath id="pit-quantile-clip"><rect x="' +
      THEORY_LAYOUT.margin.left + '" y="' + THEORY_LAYOUT.margin.top +
      '" width="' + quantileScales.innerWidth + '" height="' + quantileScales.innerHeight +
      '"/></clipPath></defs>';
    quantileHTML += axesMarkup(
      THEORY_LAYOUT,
      quantileScales,
      [0.05, 0.25, 0.5, 0.75, 0.95],
      [-6, -3, 0, 3, 6],
      'u',
      'Q(u)'
    );
    quantileHTML += pathMarkup(
      cauchyQuantile,
      U_MIN,
      U_MAX,
      260,
      quantileScales,
      'var(--journal-ink)',
      2.4,
      ''
    );
    quantileHTML += '<g clip-path="url(#pit-quantile-clip)">';
    quantileHTML += '<line id="pit-quantile-v-guide" x1="0" y1="0" x2="0" y2="0"' +
      ' stroke="var(--journal-ink-soft)" stroke-width="1.5" stroke-dasharray="7 5"/>';
    quantileHTML += '<line id="pit-quantile-h-guide" x1="0" y1="0" x2="0" y2="0"' +
      ' stroke="var(--journal-ink-soft)" stroke-width="1.5" stroke-dasharray="7 5"/>';
    quantileHTML += '<line id="pit-quantile-tangent" x1="0" y1="0" x2="0" y2="0"' +
      ' stroke="var(--journal-accent)" stroke-width="2.1"/>';
    quantileHTML += '</g>';
    quantileHTML += '<circle id="pit-quantile-marker" cx="0" cy="0" r="5.2"' +
      ' fill="var(--journal-accent)" stroke="var(--journal-bg)" stroke-width="1.4"/>';
    quantileChart.innerHTML = quantileHTML;

    theoryElements = {
      pdfScales: pdfScales,
      cdfScales: cdfScales,
      quantileScales: quantileScales,
      pdfGuide: root.querySelector('#pit-pdf-guide'),
      pdfMarker: root.querySelector('#pit-pdf-marker'),
      pdfDesc: root.querySelector('#pit-pdf-desc'),
      cdfVertical: root.querySelector('#pit-cdf-v-guide'),
      cdfHorizontal: root.querySelector('#pit-cdf-h-guide'),
      cdfTangent: root.querySelector('#pit-cdf-tangent'),
      cdfMarker: root.querySelector('#pit-cdf-marker'),
      cdfDesc: root.querySelector('#pit-cdf-desc'),
      quantileVertical: root.querySelector('#pit-quantile-v-guide'),
      quantileHorizontal: root.querySelector('#pit-quantile-h-guide'),
      quantileTangent: root.querySelector('#pit-quantile-tangent'),
      quantileMarker: root.querySelector('#pit-quantile-marker'),
      quantileDesc: root.querySelector('#pit-quantile-desc')
    };
  }

  function setLine(line, x1, y1, x2, y2) {
    line.setAttribute('x1', x1.toFixed(2));
    line.setAttribute('y1', y1.toFixed(2));
    line.setAttribute('x2', x2.toFixed(2));
    line.setAttribute('y2', y2.toFixed(2));
  }

  function setPoint(point, x, y) {
    point.setAttribute('cx', x.toFixed(2));
    point.setAttribute('cy', y.toFixed(2));
  }

  function updateTheory() {
    const u = parseFloat(uSlider.value);
    const x = cauchyQuantile(u);
    const mappedU = cauchyCDF(x);
    const density = cauchyPDF(x);
    const qPrime = quantileDerivative(u);
    const pdfScales = theoryElements.pdfScales;
    const cdfScales = theoryElements.cdfScales;
    const quantileScales = theoryElements.quantileScales;
    const pdfBottom = THEORY_LAYOUT.margin.top + pdfScales.innerHeight;
    const cdfBottom = THEORY_LAYOUT.margin.top + cdfScales.innerHeight;
    const quantileBottom = THEORY_LAYOUT.margin.top + quantileScales.innerHeight;
    const pdfX = pdfScales.x(x);
    const pdfY = pdfScales.y(density);
    const cdfX = cdfScales.x(x);
    const cdfY = cdfScales.y(mappedU);
    const quantileX = quantileScales.x(u);
    const quantileY = quantileScales.y(x);

    setLine(theoryElements.pdfGuide, pdfX, pdfBottom, pdfX, pdfY);
    setPoint(theoryElements.pdfMarker, pdfX, pdfY);

    setLine(theoryElements.cdfVertical, cdfX, cdfBottom, cdfX, cdfY);
    setLine(theoryElements.cdfHorizontal, THEORY_LAYOUT.margin.left, cdfY, cdfX, cdfY);
    const cdfDelta = 1.6;
    setLine(
      theoryElements.cdfTangent,
      cdfScales.x(x - cdfDelta),
      cdfScales.y(mappedU - density * cdfDelta),
      cdfScales.x(x + cdfDelta),
      cdfScales.y(mappedU + density * cdfDelta)
    );
    setPoint(theoryElements.cdfMarker, cdfX, cdfY);

    setLine(theoryElements.quantileVertical, quantileX, quantileBottom, quantileX, quantileY);
    setLine(
      theoryElements.quantileHorizontal,
      THEORY_LAYOUT.margin.left,
      quantileY,
      quantileX,
      quantileY
    );
    const quantileDelta = Math.min(0.065, 2.4 / qPrime);
    setLine(
      theoryElements.quantileTangent,
      quantileScales.x(u - quantileDelta),
      quantileScales.y(x - qPrime * quantileDelta),
      quantileScales.x(u + quantileDelta),
      quantileScales.y(x + qPrime * quantileDelta)
    );
    setPoint(theoryElements.quantileMarker, quantileX, quantileY);

    const uText = formatNumber(u, 3);
    const mappedUText = formatNumber(mappedU, 3);
    const xText = formatNumber(x, 3);
    const fText = formatNumber(density, 4);
    const qPrimeText = formatNumber(qPrime, 4);
    const fill = ((u - U_MIN) / (U_MAX - U_MIN)) * 100;
    uSlider.style.setProperty('--pit-fill', fill.toFixed(3) + '%');
    uOutput.textContent = uText;
    readoutU.textContent = 'u = ' + uText;
    readoutX.textContent = 'x = Q(u) = ' + xText;
    readoutF.textContent = 'f(x) = ' + fText;
    readoutQPrime.textContent = 'Q′(u) = ' + qPrimeText;
    route.textContent = 'u = ' + uText + ' → Q(u) = ' + xText +
      ' → F(Q(u)) = ' + mappedUText;
    product.textContent = 'f(Q(u))Q′(u) = ' +
      formatNumber(density * qPrime, 4);

    theoryElements.pdfDesc.textContent =
      'The standard Cauchy density at x equals ' + x.toFixed(3) +
      ' has height ' + density.toFixed(4) + '.';
    theoryElements.cdfDesc.textContent =
      'The standard Cauchy CDF maps x equals ' + x.toFixed(3) +
      ' to u equals ' + mappedU.toFixed(3) +
      ', with local slope ' + density.toFixed(4) + '.';
    theoryElements.quantileDesc.textContent =
      'The standard Cauchy quantile maps u equals ' + u.toFixed(3) +
      ' to x equals ' + x.toFixed(3) +
      ', with local slope ' + qPrime.toFixed(4) + '.';
  }

  function setPlayState(nextState) {
    playing = nextState;
    playButton.setAttribute('aria-pressed', playing ? 'true' : 'false');
    if (playing) {
      playButton.textContent = 'Pause';
      playbackValue = parseFloat(uSlider.value);
      previousTime = 0;
      animationFrame = window.requestAnimationFrame(advancePlayback);
    } else {
      if (animationFrame) window.cancelAnimationFrame(animationFrame);
      animationFrame = 0;
      previousTime = 0;
      playButton.textContent =
        parseFloat(uSlider.value) >= U_MAX - 0.0005 ? 'Replay' : 'Play';
    }
  }

  function advancePlayback(time) {
    if (!playing) return;
    if (!previousTime) previousTime = time;
    const elapsed = Math.min(50, time - previousTime);
    previousTime = time;
    playbackValue += elapsed * 0.00009;

    if (playbackValue >= U_MAX) {
      playbackValue = U_MAX;
      uSlider.value = U_MAX.toFixed(3);
      updateTheory();
      setPlayState(false);
      return;
    }

    uSlider.value = playbackValue.toFixed(3);
    updateTheory();
    animationFrame = window.requestAnimationFrame(advancePlayback);
  }

  function niceMaximum(value) {
    if (value <= 0.5) return Math.ceil(value * 10) / 10;
    return Math.ceil(value * 5) / 5;
  }

  function histogram(values, min, max, binCount, totalCount) {
    const width = (max - min) / binCount;
    const counts = new Array(binCount).fill(0);
    let below = 0;
    let above = 0;

    values.forEach(function (value) {
      if (value < min) {
        below += 1;
      } else if (value > max) {
        above += 1;
      } else {
        const rawIndex = Math.floor((value - min) / width);
        const index = Math.min(binCount - 1, rawIndex);
        counts[index] += 1;
      }
    });

    return {
      width: width,
      counts: counts,
      densities: counts.map(function (count) {
        return count / (totalCount * width);
      }),
      below: below,
      above: above
    };
  }

  function histogramMarkup(
    chart,
    titleId,
    descId,
    title,
    description,
    hist,
    xMin,
    xMax,
    xTicks,
    theoreticalDensity,
    xLabel
  ) {
    let curveMaximum = 0;
    const curvePoints = 240;
    for (let i = 0; i <= curvePoints; i += 1) {
      const value = xMin + (xMax - xMin) * i / curvePoints;
      curveMaximum = Math.max(curveMaximum, theoreticalDensity(value));
    }
    const barMaximum = Math.max.apply(null, hist.densities);
    const yMax = niceMaximum(Math.max(curveMaximum, barMaximum) * 1.18);
    const scales = makeScales(HIST_LAYOUT, xMin, xMax, 0, yMax);
    const yTicks = [0, yMax / 2, yMax];
    const bottom = HIST_LAYOUT.margin.top + scales.innerHeight;
    let html = '<title id="' + titleId + '">' + title + '</title>';
    html += '<desc id="' + descId + '">' + description + '</desc>';
    html += axesMarkup(
      HIST_LAYOUT,
      scales,
      xTicks,
      yTicks,
      xLabel,
      'density'
    );

    hist.densities.forEach(function (density, index) {
      const leftValue = xMin + index * hist.width;
      const rightValue = leftValue + hist.width;
      const left = scales.x(leftValue) + 0.6;
      const right = scales.x(rightValue) - 0.6;
      const top = scales.y(density);
      html += '<rect x="' + left.toFixed(2) + '" y="' + top.toFixed(2) +
        '" width="' + Math.max(0, right - left).toFixed(2) +
        '" height="' + Math.max(0, bottom - top).toFixed(2) +
        '" fill="var(--journal-accent)" opacity="0.55"/>';
    });

    html += pathMarkup(
      theoreticalDensity,
      xMin,
      xMax,
      curvePoints,
      scales,
      'var(--journal-ink)',
      2.3,
      '8 5'
    );
    chart.innerHTML = html;
  }

  function generateSample() {
    const sampleSize = parseInt(sampleSizeSelect.value, 10);
    const uniforms = [];
    const cauchyValues = [];

    for (let i = 0; i < sampleSize; i += 1) {
      const u = nextUniform();
      uniforms.push(u);
      cauchyValues.push(cauchyQuantile(u));
    }

    const uniformHist = histogram(uniforms, 0, 1, 20, sampleSize);
    const cauchyHist = histogram(
      cauchyValues,
      HIST_X_MIN,
      HIST_X_MAX,
      30,
      sampleSize
    );
    sampleNumber += 1;

    histogramMarkup(
      uniformHistogram,
      'pit-uniform-title',
      'pit-uniform-desc',
      'Histogram of standard uniform inputs',
      'Sample ' + sampleNumber + ' contains ' + sampleSize +
        ' standard uniform values. The dashed line is the density one.',
      uniformHist,
      0,
      1,
      [0, 0.25, 0.5, 0.75, 1],
      function () { return 1; },
      'u'
    );

    histogramMarkup(
      cauchyHistogram,
      'pit-cauchy-title',
      'pit-cauchy-desc',
      'Histogram of inverse-transformed Cauchy values',
      'Sample ' + sampleNumber + ' contains ' + sampleSize +
        ' inverse-transformed values. ' + cauchyHist.below +
        ' lie below the displayed interval and ' + cauchyHist.above +
        ' lie above it. The dashed curve is the standard Cauchy density.',
      cauchyHist,
      HIST_X_MIN,
      HIST_X_MAX,
      [-6, -3, 0, 3, 6],
      cauchyPDF,
      'x'
    );

    sampleStatus.textContent =
      'Sample ' + sampleNumber + ': generated ' + sampleSize +
      ' uniform inputs and transformed all of them. The Cauchy chart displays [' +
      formatNumber(HIST_X_MIN, 3) + ', ' + formatNumber(HIST_X_MAX, 3) +
      ']. Left of this interval: ' + cauchyHist.below +
      '; right of this interval: ' + cauchyHist.above + '.';
  }

  uSlider.addEventListener('input', function () {
    if (playing) setPlayState(false);
    playbackValue = parseFloat(uSlider.value);
    updateTheory();
  });

  playButton.addEventListener('click', function () {
    if (playing) {
      setPlayState(false);
      return;
    }
    if (parseFloat(uSlider.value) >= U_MAX - 0.0005) {
      playbackValue = U_MIN;
      uSlider.value = U_MIN.toFixed(3);
      updateTheory();
    }
    setPlayState(true);
  });

  generateButton.addEventListener('click', generateSample);
  sampleSizeSelect.addEventListener('change', generateSample);

  const reducedMotionQuery = window.matchMedia('(prefers-reduced-motion: reduce)');

  function applyMotionPreference() {
    if (reducedMotionQuery.matches && playing) setPlayState(false);
    playButton.disabled = reducedMotionQuery.matches;
  }

  function applyTheoryLayout() {
    const target = theoryLayoutQuery.matches ? {
      width: 430,
      height: 200,
      margin: { left: 52, right: 18, top: 10, bottom: 44 }
    } : {
      width: 300,
      height: 220,
      margin: { left: 44, right: 20, top: 10, bottom: 48 }
    };
    if (target.width === THEORY_LAYOUT.width && target.height === THEORY_LAYOUT.height) return;
    THEORY_LAYOUT.width = target.width;
    THEORY_LAYOUT.height = target.height;
    THEORY_LAYOUT.margin = target.margin;
    initializeTheoryCharts();
    updateTheory();
  }

  if (typeof reducedMotionQuery.addEventListener === 'function') {
    reducedMotionQuery.addEventListener('change', applyMotionPreference);
  } else if (typeof reducedMotionQuery.addListener === 'function') {
    reducedMotionQuery.addListener(applyMotionPreference);
  }

  if (typeof theoryLayoutQuery.addEventListener === 'function') {
    theoryLayoutQuery.addEventListener('change', applyTheoryLayout);
  } else if (typeof theoryLayoutQuery.addListener === 'function') {
    theoryLayoutQuery.addListener(applyTheoryLayout);
  }

  document.addEventListener('visibilitychange', function () {
    if (document.hidden && playing) setPlayState(false);
  });

  applyMotionPreference();
  initializeTheoryCharts();
  updateTheory();
  generateSample();
}());
</script>
