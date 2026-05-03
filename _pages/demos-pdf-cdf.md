---
layout: archive
title: "From PDF to CDF"
permalink: /demos/pdf-cdf/
author_profile: true
---

{% include base_path %}

<style>
  .dc-section { margin: 1.5rem 0; }
  .dc-section.center { text-align: center; }
  .dc-controls label { display: inline-block; margin: 0.25rem 0.75rem 0.25rem 0; font-size: 0.95rem; }
  .dc-controls select {
    padding: 0.2rem 0.5rem; background: #fff; color: #222;
    border: 1px solid #888; border-radius: 3px;
  }
  .dc-params { margin-top: 0.5rem; }
  .dc-param {
    display: inline-block; margin: 0.4rem 0.75rem;
    text-align: left; min-width: 12rem; vertical-align: top;
  }
  .dc-param-label { display: block; font-size: 0.92rem; margin-bottom: 0.2rem; }
  .dc-param-label strong { color: #2a7ae2; }
  .dc-area { margin-top: 0.6rem; opacity: 0.8; font-size: 0.92rem; }
  .dc-slider-wrap { margin: 1rem auto; max-width: 720px; }
  .dc-slider-wrap label { display: block; margin-bottom: 0.4rem; font-size: 0.95rem; text-align: center; }

  /* Shared base styling for every range input on this page (param sliders + current-x slider). */
  .dc-slider {
    -webkit-appearance: none; appearance: none;
    background: transparent; display: block;
    width: 100%; height: 20px; cursor: pointer; padding: 0;
  }
  .dc-slider::-webkit-slider-runnable-track {
    height: 4px; background: #888; border-radius: 2px;
  }
  .dc-slider::-moz-range-track {
    height: 4px; background: #888; border-radius: 2px; border: none;
  }
  .dc-slider::-webkit-slider-thumb {
    -webkit-appearance: none;
    width: 16px; height: 16px; border-radius: 50%;
    background: #2a7ae2; cursor: pointer; margin-top: -6px;
    border: 2px solid #fff; box-shadow: 0 1px 2px rgba(0,0,0,0.25);
  }
  .dc-slider::-moz-range-thumb {
    width: 16px; height: 16px; border-radius: 50%;
    background: #2a7ae2; cursor: pointer;
    border: 2px solid #fff; box-shadow: 0 1px 2px rgba(0,0,0,0.25);
  }

  /* Current-x slider: extended width so thumb center reaches plot edges, plus gradient progress fill. */
  .dc-slider-cx {
    margin-left: calc(8.333% - 8px);
    width: calc(89.334% + 16px);
  }
  .dc-slider-cx::-webkit-slider-runnable-track {
    background: linear-gradient(to right, #2a7ae2 0%, #2a7ae2 var(--dc-fill, 50%), #888 var(--dc-fill, 50%), #888 100%);
  }
  .dc-slider-cx::-moz-range-progress {
    height: 4px; background: #2a7ae2; border-radius: 2px; border: none;
  }

  .dc-charts { max-width: 720px; margin-inline: auto; }
  .dc-charts svg { width: 100%; height: auto; display: block; margin-bottom: 0.4rem; }
  .dc-readout {
    margin-top: 0.5rem; padding: 0.4rem 0.75rem;
    border-left: 3px solid #2a7ae2;
    text-align: left; font-size: 0.95rem;
  }
  .dc-readout strong { color: #2a7ae2; font-size: 1.1rem; }
</style>

The continuous version of the previous demo. Now $X$ takes values on a continuum, not a discrete set. Probability is described by a **density** $f(x)$ — itself not a probability. A single point has probability zero; only intervals carry probability, given by area:

$$P(a < X \leq b) = \int_a^b f(t)\,dt.$$

The CDF is built the same way as before, with the running sum of point masses replaced by a running integral of density:

$$F(x) = P(X \leq x) = \int_{-\infty}^{x} f(t)\,dt.$$

Pick a distribution, tune its parameters, then sweep the current $x$. The blue area under the density to the left of $x$ equals the height of the CDF at $x$ — the same probability, viewed two ways.

## Interactive

<div class="dc-section center">
  <div class="dc-controls">
    <label>Distribution:
      <select id="dc-dist">
        <option value="normal">Normal</option>
        <option value="uniform">Uniform</option>
        <option value="exponential">Exponential</option>
        <option value="beta">Beta</option>
        <option value="cauchy">Cauchy</option>
        <option value="logistic">Logistic</option>
      </select>
    </label>
  </div>
  <div class="dc-params" id="dc-params"></div>
  <div class="dc-area" id="dc-area">Total area in plot range = —</div>
</div>

<div class="dc-slider-wrap">
  <label>Current $x$ = <strong id="dc-x-val">—</strong></label>
  <input type="range" id="dc-x" class="dc-slider dc-slider-cx" min="-3" max="3" step="0.01" value="0">
</div>

<div class="dc-charts">
  <svg id="dc-pdf" viewBox="0 0 600 200" preserveAspectRatio="xMidYMid meet"></svg>
  <svg id="dc-cdf" viewBox="0 0 600 200" preserveAspectRatio="xMidYMid meet"></svg>
  <div class="dc-readout">
    Cumulative probability $P(X \leq x)$ = <strong id="dc-cum">—</strong>. The blue area under the density equals this; the CDF curve traces it.
  </div>
</div>

## What it shows

**Density vs. probability.** $f(x)$ measures how concentrated probability is around $x$, in units of probability per unit of $x$. It can exceed 1 — try a Normal with $\sigma = 0.2$. Probability itself only emerges by integrating over a region of positive width.

**The CDF stays bounded.** $F(x)$ runs from 0 to 1, monotone non-decreasing, smooth wherever $f$ is finite. No jumps in the continuous case — those required point masses.

**Discrete to continuous.** Compared to the PMF demo, the lollipop spikes have melted into a smooth density and the CDF staircase has straightened into a continuous curve. The accounting principle is unchanged: cumulative probability at $x$ is whatever sits "to the left" of $x$, just measured by area instead of by counting masses.

<script>
(function() {
  const $ = id => document.getElementById(id);

  /* Abramowitz & Stegun 7.1.26 — accurate to ~1.5e-7. */
  function erf(x) {
    const sign = x < 0 ? -1 : 1;
    x = Math.abs(x);
    const a1 = 0.254829592, a2 = -0.284496736, a3 = 1.421413741, a4 = -1.453152027, a5 = 1.061405429, p = 0.3275911;
    const t = 1 / (1 + p * x);
    const y = 1 - (((((a5 * t + a4) * t) + a3) * t + a2) * t + a1) * t * Math.exp(-x * x);
    return sign * y;
  }

  /* Lanczos approximation for log Γ(x), accurate for x > 0. */
  function logGamma(x) {
    const cof = [76.18009172947146, -86.50532032941677, 24.01409824083091,
                 -1.231739572450155, 0.1208650973866179e-2, -0.5395239384953e-5];
    let y = x, tmp = x + 5.5;
    tmp -= (x + 0.5) * Math.log(tmp);
    let ser = 1.000000000190015;
    for (let j = 0; j < 6; j++) { y += 1; ser += cof[j] / y; }
    return -tmp + Math.log(2.5066282746310005 * ser / x);
  }
  function logBeta(a, b) { return logGamma(a) + logGamma(b) - logGamma(a + b); }

  const DISTS = {
    normal: {
      name: 'Normal',
      params: [
        { key: 'mu',    label: 'μ', min: -3, max: 3, step: 0.05, def: 0 },
        { key: 'sigma', label: 'σ', min: 0.2, max: 3, step: 0.05, def: 1 },
      ],
      pdf: (x, p) => Math.exp(-0.5 * ((x - p.mu) / p.sigma) ** 2) / (p.sigma * Math.sqrt(2 * Math.PI)),
      cdf: (x, p) => 0.5 * (1 + erf((x - p.mu) / (p.sigma * Math.SQRT2))),
      range: (p) => [p.mu - 4 * p.sigma, p.mu + 4 * p.sigma],
    },
    uniform: {
      name: 'Uniform',
      params: [
        { key: 'a', label: 'a', min: -3, max: 3, step: 0.1, def: 0 },
        { key: 'b', label: 'b', min: -3, max: 3, step: 0.1, def: 1 },
      ],
      pdf: (x, p) => {
        const lo = Math.min(p.a, p.b), hi = Math.max(p.a, p.b);
        return (hi > lo && x >= lo && x <= hi) ? 1 / (hi - lo) : 0;
      },
      cdf: (x, p) => {
        const lo = Math.min(p.a, p.b), hi = Math.max(p.a, p.b);
        if (hi <= lo) return x >= lo ? 1 : 0;
        if (x <= lo) return 0;
        if (x >= hi) return 1;
        return (x - lo) / (hi - lo);
      },
      range: (p) => {
        const lo = Math.min(p.a, p.b), hi = Math.max(p.a, p.b);
        const pad = Math.max(0.5, (hi - lo) * 0.3);
        return [lo - pad, hi + pad];
      },
    },
    exponential: {
      name: 'Exponential',
      params: [
        { key: 'lambda', label: 'λ', min: 0.1, max: 3, step: 0.05, def: 1 },
      ],
      pdf: (x, p) => x >= 0 ? p.lambda * Math.exp(-p.lambda * x) : 0,
      cdf: (x, p) => x < 0 ? 0 : 1 - Math.exp(-p.lambda * x),
      range: (p) => [-0.5, Math.max(3, 8 / p.lambda)],
    },
    beta: {
      name: 'Beta',
      params: [
        { key: 'alpha', label: 'α', min: 0.5, max: 5, step: 0.1, def: 2 },
        { key: 'beta',  label: 'β', min: 0.5, max: 5, step: 0.1, def: 5 },
      ],
      pdf: (x, p) => {
        if (x <= 0 || x >= 1) return 0;
        return Math.exp((p.alpha - 1) * Math.log(x) + (p.beta - 1) * Math.log(1 - x) - logBeta(p.alpha, p.beta));
      },
      /* No closed-form CDF; use midpoint-rule integration on [0, x]. N=200 is plenty here since the singular cases (α<1 or β<1) are also handled by integrating away from the boundaries. */
      cdf: (x, p) => {
        if (x <= 0) return 0;
        if (x >= 1) return 1;
        const N = 200;
        const dt = x / N;
        const lb = logBeta(p.alpha, p.beta);
        let sum = 0;
        for (let i = 0; i < N; i++) {
          const t = (i + 0.5) * dt;
          sum += Math.exp((p.alpha - 1) * Math.log(t) + (p.beta - 1) * Math.log(1 - t) - lb);
        }
        return sum * dt;
      },
      range: () => [-0.05, 1.05],
    },
    cauchy: {
      name: 'Cauchy',
      params: [
        { key: 'x0',    label: 'x₀', min: -3, max: 3, step: 0.05, def: 0 },
        { key: 'gamma', label: 'γ',  min: 0.2, max: 3, step: 0.05, def: 1 },
      ],
      pdf: (x, p) => 1 / (Math.PI * p.gamma * (1 + ((x - p.x0) / p.gamma) ** 2)),
      cdf: (x, p) => 0.5 + Math.atan((x - p.x0) / p.gamma) / Math.PI,
      /* ±15γ captures only ~96% — Cauchy's tails are genuinely fat; the readout will reflect this. */
      range: (p) => [p.x0 - 15 * p.gamma, p.x0 + 15 * p.gamma],
    },
    logistic: {
      name: 'Logistic',
      params: [
        { key: 'mu', label: 'μ', min: -3, max: 3, step: 0.05, def: 0 },
        { key: 's',  label: 's', min: 0.2, max: 3, step: 0.05, def: 1 },
      ],
      pdf: (x, p) => {
        const z = (x - p.mu) / p.s;
        const e = Math.exp(-z);
        return e / (p.s * (1 + e) * (1 + e));
      },
      cdf: (x, p) => 1 / (1 + Math.exp(-(x - p.mu) / p.s)),
      range: (p) => [p.mu - 10 * p.s, p.mu + 10 * p.s],
    },
  };

  let currentDist = 'normal';
  let params = {};
  let currentX = 0;

  function resetParamsForDist() {
    params = {};
    for (const p of DISTS[currentDist].params) params[p.key] = p.def;
  }

  function renderParams() {
    const d = DISTS[currentDist];
    $('dc-params').innerHTML = d.params.map(p =>
      '<div class="dc-param">' +
        '<span class="dc-param-label">' + p.label + ' = <strong id="dc-pv-' + p.key + '">' + params[p.key].toFixed(2) + '</strong></span>' +
        '<input class="dc-slider" type="range" data-key="' + p.key + '" min="' + p.min + '" max="' + p.max + '" step="' + p.step + '" value="' + params[p.key] + '">' +
      '</div>'
    ).join('');
    $('dc-params').querySelectorAll('input').forEach(el =>
      el.addEventListener('input', onParamChange)
    );
  }

  function onParamChange(e) {
    const k = e.target.dataset.key;
    const v = parseFloat(e.target.value);
    if (!isFinite(v)) return;
    params[k] = v;
    $('dc-pv-' + k).textContent = v.toFixed(2);
    updateXRange();
    render();
  }

  $('dc-dist').addEventListener('change', () => {
    currentDist = $('dc-dist').value;
    resetParamsForDist();
    renderParams();
    updateXRange();
    render();
  });

  const slider = $('dc-x');
  function updateSliderFill() {
    const min = parseFloat(slider.min), max = parseFloat(slider.max);
    const pct = (max > min) ? ((currentX - min) / (max - min)) * 100 : 50;
    slider.style.setProperty('--dc-fill', Math.max(0, Math.min(100, pct)).toFixed(1) + '%');
  }
  slider.addEventListener('input', () => {
    currentX = parseFloat(slider.value);
    $('dc-x-val').textContent = currentX.toFixed(2);
    updateSliderFill();
    render();
  });

  function updateXRange() {
    const [lo, hi] = DISTS[currentDist].range(params);
    slider.min = lo; slider.max = hi;
    slider.step = ((hi - lo) / 600).toFixed(4);
    if (currentX < lo || currentX > hi) currentX = (lo + hi) / 2;
    slider.value = currentX;
    $('dc-x-val').textContent = currentX.toFixed(2);
    updateSliderFill();
  }

  /* drawing */
  const W = 600, H = 200, M = { l: 50, r: 14, t: 14, b: 32 };
  const innerW = W - M.l - M.r, innerH = H - M.t - M.b;
  const xS = (lo, hi, v) => M.l + ((v - lo) / (hi - lo)) * innerW;
  const yS = (yMax, v) => M.t + (1 - v / yMax) * innerH;

  function drawAxes(xLo, xHi, yMax, yLabel, yTicks) {
    let s = '';
    s += '<rect x="' + M.l + '" y="' + M.t + '" width="' + innerW + '" height="' + innerH + '" fill="none" stroke="currentColor" stroke-opacity="0.25"/>';
    for (const v of yTicks) {
      const y = yS(yMax, v);
      s += '<line x1="' + M.l + '" y1="' + y.toFixed(1) + '" x2="' + (M.l + innerW) + '" y2="' + y.toFixed(1) + '" stroke="currentColor" stroke-opacity="0.1"/>';
      s += '<text x="' + (M.l - 6) + '" y="' + (y + 4).toFixed(1) + '" text-anchor="end" fill="currentColor" font-size="13" opacity="0.75">' + v.toFixed(2) + '</text>';
    }
    const xTicks = [xLo, (xLo + xHi) / 2, xHi];
    for (const v of xTicks) {
      const x = xS(xLo, xHi, v);
      s += '<text x="' + x.toFixed(1) + '" y="' + (M.t + innerH + 18) + '" text-anchor="middle" fill="currentColor" font-size="13" opacity="0.75">' + v.toFixed(2) + '</text>';
    }
    s += '<text x="' + (M.l - 34) + '" y="' + (M.t + innerH / 2) + '" text-anchor="middle" fill="currentColor" font-size="13" opacity="0.7" transform="rotate(-90 ' + (M.l - 34) + ' ' + (M.t + innerH / 2) + ')">' + yLabel + '</text>';
    return s;
  }

  function samplePDF(N) {
    const [lo, hi] = DISTS[currentDist].range(params);
    const pdfFn = DISTS[currentDist].pdf;
    const out = [];
    for (let i = 0; i <= N; i++) {
      const x = lo + (hi - lo) * i / N;
      out.push([x, pdfFn(x, params)]);
    }
    return { lo, hi, pts: out };
  }

  function drawPDF() {
    const svg = $('dc-pdf');
    const { lo, hi, pts } = samplePDF(300);
    const fmax = Math.max(...pts.map(p => p[1]), 0.01);
    const yMax = fmax * 1.18;
    const yTicks = [0, yMax / 2, yMax];
    let s = drawAxes(lo, hi, yMax, 'f(x)', yTicks);

    /* shaded area to the left of currentX */
    const baseY = yS(yMax, 0);
    let fill = 'M ' + xS(lo, hi, lo).toFixed(1) + ' ' + baseY.toFixed(1);
    let crossed = false;
    for (let i = 0; i < pts.length; i++) {
      const [x, y] = pts[i];
      if (x > currentX) {
        if (!crossed) {
          /* interpolate to currentX between previous and this point */
          const [xp, yp] = pts[i - 1];
          const t = (currentX - xp) / (x - xp);
          const yc = yp + t * (y - yp);
          fill += ' L ' + xS(lo, hi, currentX).toFixed(1) + ' ' + yS(yMax, yc).toFixed(1);
          fill += ' L ' + xS(lo, hi, currentX).toFixed(1) + ' ' + baseY.toFixed(1) + ' Z';
          crossed = true;
          break;
        }
      }
      fill += ' L ' + xS(lo, hi, x).toFixed(1) + ' ' + yS(yMax, y).toFixed(1);
    }
    if (!crossed) {
      fill += ' L ' + xS(lo, hi, hi).toFixed(1) + ' ' + baseY.toFixed(1) + ' Z';
    }
    s += '<path d="' + fill + '" fill="#2a7ae2" fill-opacity="0.25"/>';

    /* density curve */
    let line = '';
    for (let i = 0; i < pts.length; i++) {
      const [x, y] = pts[i];
      line += (i === 0 ? 'M' : 'L') + xS(lo, hi, x).toFixed(1) + ',' + yS(yMax, y).toFixed(1);
    }
    s += '<path d="' + line + '" fill="none" stroke="#2a7ae2" stroke-width="2"/>';

    /* current x marker */
    const cx = xS(lo, hi, currentX);
    s += '<line x1="' + cx + '" y1="' + M.t + '" x2="' + cx + '" y2="' + (M.t + innerH) + '" stroke="currentColor" stroke-opacity="0.5" stroke-dasharray="4,3"/>';

    svg.innerHTML = s;
  }

  function drawCDF() {
    const svg = $('dc-cdf');
    const [lo, hi] = DISTS[currentDist].range(params);
    const cdfFn = DISTS[currentDist].cdf;
    const yMax = 1.05;
    const yTicks = [0, 0.25, 0.5, 0.75, 1];
    let s = drawAxes(lo, hi, yMax, 'F(x)', yTicks);

    /* sample CDF */
    const N = 300;
    const pts = [];
    for (let i = 0; i <= N; i++) {
      const x = lo + (hi - lo) * i / N;
      pts.push([x, cdfFn(x, params)]);
    }

    /* split-color the curve at currentX */
    const xCpx = xS(lo, hi, currentX);
    let leftPath = '', rightPath = '';
    let started = { left: false, right: false };
    for (let i = 0; i < pts.length; i++) {
      const [x, y] = pts[i];
      const px = xS(lo, hi, x).toFixed(2);
      const py = yS(yMax, y).toFixed(2);
      if (x <= currentX) {
        leftPath += (started.left ? 'L' : 'M') + px + ',' + py;
        started.left = true;
      } else {
        if (!started.right && i > 0) {
          /* interpolate the boundary point at currentX */
          const [xp, yp] = pts[i - 1];
          const t = (currentX - xp) / (x - xp);
          const yc = yp + t * (y - yp);
          const ycPx = yS(yMax, yc).toFixed(2);
          leftPath += 'L' + xCpx.toFixed(2) + ',' + ycPx;
          rightPath += 'M' + xCpx.toFixed(2) + ',' + ycPx;
        }
        rightPath += (started.right ? 'L' : 'M') + px + ',' + py;
        started.right = true;
      }
    }
    if (leftPath) s += '<path d="' + leftPath + '" fill="none" stroke="#2a7ae2" stroke-width="2"/>';
    if (rightPath) s += '<path d="' + rightPath + '" fill="none" stroke="#888" stroke-width="2" opacity="0.55"/>';

    /* current x marker, horizontal hint, dot */
    const cumAtCurrent = cdfFn(currentX, params);
    const cyPx = yS(yMax, cumAtCurrent);
    s += '<line x1="' + xCpx + '" y1="' + M.t + '" x2="' + xCpx + '" y2="' + (M.t + innerH) + '" stroke="currentColor" stroke-opacity="0.5" stroke-dasharray="4,3"/>';
    s += '<line x1="' + M.l + '" y1="' + cyPx + '" x2="' + xCpx + '" y2="' + cyPx + '" stroke="#2a7ae2" stroke-opacity="0.4" stroke-dasharray="2,3"/>';
    s += '<circle cx="' + xCpx + '" cy="' + cyPx + '" r="5" fill="#2a7ae2"/>';

    svg.innerHTML = s;
    $('dc-cum').textContent = cumAtCurrent.toFixed(3);
  }

  function updateArea() {
    const [lo, hi] = DISTS[currentDist].range(params);
    const cdfFn = DISTS[currentDist].cdf;
    const area = cdfFn(hi, params) - cdfFn(lo, params);
    $('dc-area').textContent = 'Total area in plot range = ' + area.toFixed(3);
  }

  function render() {
    drawPDF();
    drawCDF();
    updateArea();
  }

  window.addEventListener('resize', render);

  /* initial */
  resetParamsForDist();
  renderParams();
  updateXRange();
  render();
})();
</script>
