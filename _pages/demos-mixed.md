---
layout: archive
title: "Mixed Distributions"
permalink: /demos/mixed/
author_profile: true
---

{% include base_path %}

<style>
  .mx-section { margin: 1.5rem 0; }
  .mx-section.center { text-align: center; }
  .mx-controls label { display: inline-block; margin: 0.25rem 0.75rem 0.25rem 0; font-size: 0.95rem; }
  .mx-controls select {
    padding: 0.2rem 0.5rem; background: #fff; color: #222;
    border: 1px solid #888; border-radius: 3px;
  }
  .mx-params { margin-top: 0.5rem; }
  .mx-param {
    display: inline-block; margin: 0.4rem 0.75rem;
    text-align: left; min-width: 12rem; vertical-align: top;
  }
  .mx-param-label { display: block; font-size: 0.92rem; margin-bottom: 0.2rem; }
  .mx-param-label strong { color: #2a7ae2; }

  .mx-input-table { margin: 0.75rem auto 0.25rem; border-collapse: collapse; }
  .mx-input-table th, .mx-input-table td { padding: 0.25rem 0.5rem; text-align: center; }
  .mx-input-table th { font-weight: 600; opacity: 0.85; font-size: 0.95rem; }
  .mx-input-table input {
    width: 5em; padding: 0.2rem 0.4rem;
    background: #fff; color: #222; border: 1px solid #888; border-radius: 3px;
    text-align: center;
  }
  .mx-row-rm {
    padding: 0.1rem 0.55rem; cursor: pointer;
    background: transparent; border: 1px solid #888; border-radius: 3px; color: inherit;
  }
  .mx-add {
    margin: 0.4rem 0; padding: 0.4rem 0.9rem; cursor: pointer;
    background: #fff; color: #222; border: 1px solid #888; border-radius: 4px;
  }
  .mx-mass { margin-top: 0.6rem; opacity: 0.8; font-size: 0.92rem; }
  .mx-mass.warn { color: #c0392b; opacity: 1; }
  .mx-mass strong { color: #2a7ae2; }

  .mx-slider-wrap { margin: 1rem auto; max-width: 720px; }
  .mx-slider-wrap label { display: block; margin-bottom: 0.4rem; font-size: 0.95rem; text-align: center; }

  .mx-slider {
    -webkit-appearance: none; appearance: none;
    background: transparent; display: block;
    width: 100%; height: 20px; cursor: pointer; padding: 0;
  }
  .mx-slider::-webkit-slider-runnable-track {
    height: 4px; background: #888; border-radius: 2px;
  }
  .mx-slider::-moz-range-track {
    height: 4px; background: #888; border-radius: 2px; border: none;
  }
  .mx-slider::-webkit-slider-thumb {
    -webkit-appearance: none;
    width: 16px; height: 16px; border-radius: 50%;
    background: #2a7ae2; cursor: pointer; margin-top: -6px;
    border: 2px solid #fff; box-shadow: 0 1px 2px rgba(0,0,0,0.25);
  }
  .mx-slider::-moz-range-thumb {
    width: 16px; height: 16px; border-radius: 50%;
    background: #2a7ae2; cursor: pointer;
    border: 2px solid #fff; box-shadow: 0 1px 2px rgba(0,0,0,0.25);
  }
  .mx-slider-cx {
    margin-left: calc(8.333% - 8px);
    width: calc(89.334% + 16px);
  }
  .mx-slider-cx::-webkit-slider-runnable-track {
    background: linear-gradient(to right, #2a7ae2 0%, #2a7ae2 var(--mx-fill, 50%), #888 var(--mx-fill, 50%), #888 100%);
  }
  .mx-slider-cx::-moz-range-progress {
    height: 4px; background: #2a7ae2; border-radius: 2px; border: none;
  }

  .mx-charts { max-width: 720px; margin-inline: auto; }
  .mx-charts svg { width: 100%; height: auto; display: block; margin-bottom: 0.4rem; }
  .mx-readout {
    margin-top: 0.5rem; padding: 0.4rem 0.75rem;
    border-left: 3px solid #2a7ae2;
    text-align: left; font-size: 0.95rem;
  }
  .mx-readout strong { color: #2a7ae2; font-size: 1.1rem; }
  .mx-readout .breakdown { display: block; margin-top: 0.25rem; opacity: 0.75; font-size: 0.9rem; }
</style>

A **mixed-type distribution** has both a continuous part and one or more point masses. Its CDF is the sum:

$$F(x) = W_c \cdot G(x) + \sum_{x_i \leq x} w_i,$$

where $G$ is the continuous CDF (weight $W_c$) and the $w_i$ are the point masses at $x_i$. The defining visual feature: the CDF picks up a **jump of size exactly $w_i$** at every $x_i$, while remaining smooth in between.

Below, pick a continuous family and add point masses with weights $w_i$. The continuous weight $W_c = 1 - \sum w_i$ is allocated automatically — what's left over after the discrete part. Sweep current $x$ and watch the CDF jump as you cross each $x_i$.

## Interactive

<div class="mx-section center">
  <div class="mx-controls">
    <label>Continuous family:
      <select id="mx-dist">
        <option value="normal">Normal</option>
        <option value="uniform">Uniform</option>
        <option value="exponential">Exponential</option>
        <option value="beta">Beta</option>
        <option value="cauchy">Cauchy</option>
        <option value="logistic">Logistic</option>
      </select>
    </label>
  </div>
  <div class="mx-params" id="mx-params"></div>

  <table class="mx-input-table" id="mx-input"><thead><tr><th>$x_i$</th><th>$w_i$</th><th></th></tr></thead><tbody></tbody></table>
  <button class="mx-add" id="mx-add">+ add point mass</button>
  <div class="mx-mass" id="mx-mass">— </div>
</div>

<div class="mx-slider-wrap">
  <label>Current $x$ = <strong id="mx-x-val">—</strong></label>
  <input type="range" id="mx-x" class="mx-slider mx-slider-cx" min="-3" max="3" step="0.01" value="0">
</div>

<div class="mx-charts">
  <svg id="mx-pdf" viewBox="0 0 600 200" preserveAspectRatio="xMidYMid meet"></svg>
  <svg id="mx-cdf" viewBox="0 0 600 200" preserveAspectRatio="xMidYMid meet"></svg>
  <div class="mx-readout">
    Cumulative $F(x)$ = <strong id="mx-cum">—</strong>
    <span class="breakdown">continuous $W_c \cdot G(x)$ = <span id="mx-cum-cont">—</span>, discrete $\sum_{x_i \leq x} w_i$ = <span id="mx-cum-disc">—</span></span>
  </div>
</div>

## What it shows

**Jumps are the signature of mixed type.** A purely continuous CDF is smooth; a purely discrete CDF is all jumps; a mixed CDF has both. **The jump at $x_i$ has height exactly $w_i$** — the same value you typed into the table. Slide current $x$ across an $x_i$ and watch the CDF lift by $w_i$ in one step, while the corresponding lollipop in the upper panel turns blue.

**Continuous and discrete share the budget.** Adding a point mass $w_i$ removes $w_i$ from the continuous part: the smooth curve scales down by $W_c = 1 - \sum w_j$, and the lost area under the density reappears as the jumps. Total probability stays at 1 by construction.

**Mixed PDF is not a function in the ordinary sense.** Strictly, $f_{\text{mix}}(x) = W_c\, g(x) + \sum_i w_i\, \delta(x - x_i)$, with Dirac deltas at the mass points. The lollipops are just a visual stand-in for those deltas — heights of lollipops carry **probability mass** (unitless), heights of the smooth curve carry **probability density** (per unit $x$). They share an axis here for layout convenience, not because they share units.

<script>
(function() {
  const $ = id => document.getElementById(id);

  function erf(x) {
    const sign = x < 0 ? -1 : 1;
    x = Math.abs(x);
    const a1 = 0.254829592, a2 = -0.284496736, a3 = 1.421413741, a4 = -1.453152027, a5 = 1.061405429, p = 0.3275911;
    const t = 1 / (1 + p * x);
    const y = 1 - (((((a5 * t + a4) * t) + a3) * t + a2) * t + a1) * t * Math.exp(-x * x);
    return sign * y;
  }
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
      params: [
        { key: 'mu',    label: 'μ', min: -3, max: 3, step: 0.05, def: 0 },
        { key: 'sigma', label: 'σ', min: 0.2, max: 3, step: 0.05, def: 1 },
      ],
      pdf: (x, p) => Math.exp(-0.5 * ((x - p.mu) / p.sigma) ** 2) / (p.sigma * Math.sqrt(2 * Math.PI)),
      cdf: (x, p) => 0.5 * (1 + erf((x - p.mu) / (p.sigma * Math.SQRT2))),
      range: (p) => [p.mu - 4 * p.sigma, p.mu + 4 * p.sigma],
    },
    uniform: {
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
      params: [
        { key: 'lambda', label: 'λ', min: 0.1, max: 3, step: 0.05, def: 1 },
      ],
      pdf: (x, p) => x >= 0 ? p.lambda * Math.exp(-p.lambda * x) : 0,
      cdf: (x, p) => x < 0 ? 0 : 1 - Math.exp(-p.lambda * x),
      range: (p) => [-0.5, Math.max(3, 8 / p.lambda)],
    },
    beta: {
      params: [
        { key: 'alpha', label: 'α', min: 0.5, max: 5, step: 0.1, def: 2 },
        { key: 'beta',  label: 'β', min: 0.5, max: 5, step: 0.1, def: 5 },
      ],
      pdf: (x, p) => {
        if (x <= 0 || x >= 1) return 0;
        return Math.exp((p.alpha - 1) * Math.log(x) + (p.beta - 1) * Math.log(1 - x) - logBeta(p.alpha, p.beta));
      },
      cdf: (x, p) => {
        if (x <= 0) return 0;
        if (x >= 1) return 1;
        const N = 200, dt = x / N, lb = logBeta(p.alpha, p.beta);
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
      params: [
        { key: 'x0',    label: 'x₀', min: -3, max: 3, step: 0.05, def: 0 },
        { key: 'gamma', label: 'γ',  min: 0.2, max: 3, step: 0.05, def: 1 },
      ],
      pdf: (x, p) => 1 / (Math.PI * p.gamma * (1 + ((x - p.x0) / p.gamma) ** 2)),
      cdf: (x, p) => 0.5 + Math.atan((x - p.x0) / p.gamma) / Math.PI,
      range: (p) => [p.x0 - 15 * p.gamma, p.x0 + 15 * p.gamma],
    },
    logistic: {
      params: [
        { key: 'mu', label: 'μ', min: -3, max: 3, step: 0.05, def: 0 },
        { key: 's',  label: 's', min: 0.2, max: 3, step: 0.05, def: 1 },
      ],
      pdf: (x, p) => {
        const z = (x - p.mu) / p.s, e = Math.exp(-z);
        return e / (p.s * (1 + e) * (1 + e));
      },
      cdf: (x, p) => 1 / (1 + Math.exp(-(x - p.mu) / p.s)),
      range: (p) => [p.mu - 10 * p.s, p.mu + 10 * p.s],
    },
  };

  let currentDist = 'normal';
  let params = {};
  let points = [{ x: 0, w: 0.3 }];
  let currentX = 0;

  function discreteSum() {
    return points.reduce((s, p) => s + Math.max(0, p.w), 0);
  }
  function continuousW() {
    return Math.max(0, 1 - discreteSum());
  }
  function discreteSumLeft(x) {
    return points.reduce((s, p) => s + (p.x <= x && p.w > 0 ? p.w : 0), 0);
  }

  function resetParams() {
    params = {};
    for (const p of DISTS[currentDist].params) params[p.key] = p.def;
  }

  function renderParams() {
    const d = DISTS[currentDist];
    $('mx-params').innerHTML = d.params.map(p =>
      '<div class="mx-param">' +
        '<span class="mx-param-label">' + p.label + ' = <strong id="mx-pv-' + p.key + '">' + params[p.key].toFixed(2) + '</strong></span>' +
        '<input class="mx-slider" type="range" data-key="' + p.key + '" min="' + p.min + '" max="' + p.max + '" step="' + p.step + '" value="' + params[p.key] + '">' +
      '</div>'
    ).join('');
    $('mx-params').querySelectorAll('input').forEach(el => el.addEventListener('input', onParamChange));
  }
  function onParamChange(e) {
    const k = e.target.dataset.key, v = parseFloat(e.target.value);
    if (!isFinite(v)) return;
    params[k] = v;
    $('mx-pv-' + k).textContent = v.toFixed(2);
    updateXRange();
    render();
  }

  $('mx-dist').addEventListener('change', () => {
    currentDist = $('mx-dist').value;
    resetParams();
    renderParams();
    updateXRange();
    render();
  });

  /* point-mass table */
  const tbody = document.querySelector('#mx-input tbody');
  function renderTable() {
    tbody.innerHTML = '';
    points.forEach((pt, idx) => {
      const tr = document.createElement('tr');
      tr.innerHTML =
        '<td><input type="number" data-i="' + idx + '" data-k="x" step="any" value="' + pt.x + '"></td>' +
        '<td><input type="number" data-i="' + idx + '" data-k="w" step="0.01" min="0" value="' + pt.w + '"></td>' +
        '<td><button class="mx-row-rm" data-i="' + idx + '" title="remove">&times;</button></td>';
      tbody.appendChild(tr);
    });
    tbody.querySelectorAll('input').forEach(el => el.addEventListener('input', onCellEdit));
    tbody.querySelectorAll('.mx-row-rm').forEach(el => el.addEventListener('click', onRowRemove));
  }
  function onCellEdit(e) {
    const i = +e.target.dataset.i, k = e.target.dataset.k, v = parseFloat(e.target.value);
    if (!isFinite(v)) return;
    points[i][k] = v;
    afterPointsChange(false);
  }
  function onRowRemove(e) {
    const i = +e.currentTarget.dataset.i;
    points.splice(i, 1);
    renderTable();
    afterPointsChange(false);
  }
  $('mx-add').addEventListener('click', () => {
    points.push({ x: 0, w: 0.1 });
    renderTable();
    afterPointsChange(false);
  });
  function afterPointsChange() {
    points.sort((a, b) => a.x - b.x);
    updateMass();
    render();
  }

  function updateMass() {
    const dSum = discreteSum();
    const Wc = continuousW();
    const el = $('mx-mass');
    el.innerHTML = 'Discrete $\\sum w_i$ = <strong>' + dSum.toFixed(3) + '</strong>, continuous $W_c$ = <strong>' + Wc.toFixed(3) + '</strong>, total = <strong>' + (dSum + Wc).toFixed(3) + '</strong>';
    if (dSum > 1.0001) {
      el.classList.add('warn');
      el.innerHTML += ' &nbsp; (point masses exceed 1; continuous part clipped to 0)';
    } else {
      el.classList.remove('warn');
    }
    if (window.MathJax && window.MathJax.typesetPromise) window.MathJax.typesetPromise([el]);
  }

  /* current-x slider */
  const slider = $('mx-x');
  function updateSliderFill() {
    const min = parseFloat(slider.min), max = parseFloat(slider.max);
    const pct = (max > min) ? ((currentX - min) / (max - min)) * 100 : 50;
    slider.style.setProperty('--mx-fill', Math.max(0, Math.min(100, pct)).toFixed(1) + '%');
  }
  slider.addEventListener('input', () => {
    currentX = parseFloat(slider.value);
    $('mx-x-val').textContent = currentX.toFixed(2);
    updateSliderFill();
    render();
  });
  function updateXRange() {
    const [lo, hi] = DISTS[currentDist].range(params);
    slider.min = lo; slider.max = hi;
    slider.step = ((hi - lo) / 600).toFixed(4);
    if (currentX < lo || currentX > hi) currentX = (lo + hi) / 2;
    slider.value = currentX;
    $('mx-x-val').textContent = currentX.toFixed(2);
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
    if (yLabel) {
      s += '<text x="' + (M.l - 34) + '" y="' + (M.t + innerH / 2) + '" text-anchor="middle" fill="currentColor" font-size="13" opacity="0.7" transform="rotate(-90 ' + (M.l - 34) + ' ' + (M.t + innerH / 2) + ')">' + yLabel + '</text>';
    }
    return s;
  }

  function drawPDF() {
    const svg = $('mx-pdf');
    const [lo, hi] = DISTS[currentDist].range(params);
    const Wc = continuousW();
    const pdfFn = DISTS[currentDist].pdf;

    const N = 300;
    const cont = [];
    for (let i = 0; i <= N; i++) {
      const x = lo + (hi - lo) * i / N;
      cont.push([x, Wc * pdfFn(x, params)]);
    }
    const fmax = Math.max(...cont.map(p => p[1]), 0);
    const wmax = points.reduce((m, p) => (p.w > 0 && p.x >= lo && p.x <= hi ? Math.max(m, p.w) : m), 0);
    const yMax = Math.max(fmax, wmax, 0.01) * 1.18;
    const yTicks = [0, yMax / 2, yMax];
    let s = drawAxes(lo, hi, yMax, '', yTicks);

    /* shaded area under continuous curve to left of currentX */
    const baseY = yS(yMax, 0);
    let fill = 'M ' + xS(lo, hi, lo).toFixed(1) + ' ' + baseY.toFixed(1);
    let crossed = false;
    for (let i = 0; i < cont.length; i++) {
      const [x, y] = cont[i];
      if (x > currentX) {
        if (!crossed) {
          const [xp, yp] = cont[i - 1];
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
    if (!crossed) fill += ' L ' + xS(lo, hi, hi).toFixed(1) + ' ' + baseY.toFixed(1) + ' Z';
    s += '<path d="' + fill + '" fill="#2a7ae2" fill-opacity="0.22"/>';

    /* density curve */
    let line = '';
    for (let i = 0; i < cont.length; i++) {
      const [x, y] = cont[i];
      line += (i === 0 ? 'M' : 'L') + xS(lo, hi, x).toFixed(1) + ',' + yS(yMax, y).toFixed(1);
    }
    s += '<path d="' + line + '" fill="none" stroke="#2a7ae2" stroke-width="2"/>';

    /* point-mass lollipops */
    for (const pt of points) {
      if (pt.x < lo || pt.x > hi || pt.w <= 0) continue;
      const x = xS(lo, hi, pt.x);
      const yTop = yS(yMax, Math.max(pt.w, 0));
      const yBot = yS(yMax, 0);
      const inLeft = pt.x <= currentX;
      const color = inLeft ? '#2a7ae2' : '#888';
      const opacity = inLeft ? 1 : 0.4;
      const dotR = inLeft ? 5 : 4;
      s += '<line x1="' + x + '" y1="' + yBot + '" x2="' + x + '" y2="' + yTop + '" stroke="' + color + '" stroke-width="2.5" opacity="' + opacity + '"/>';
      s += '<circle cx="' + x + '" cy="' + yTop + '" r="' + dotR + '" fill="' + color + '" opacity="' + opacity + '"/>';
    }

    /* current x marker */
    const cx = xS(lo, hi, currentX);
    s += '<line x1="' + cx + '" y1="' + M.t + '" x2="' + cx + '" y2="' + (M.t + innerH) + '" stroke="currentColor" stroke-opacity="0.5" stroke-dasharray="4,3"/>';

    svg.innerHTML = s;
  }

  function drawCDF() {
    const svg = $('mx-cdf');
    const [lo, hi] = DISTS[currentDist].range(params);
    const Wc = continuousW();
    const cdfFn = DISTS[currentDist].cdf;
    const dSum = discreteSum();
    const yMax = Math.max(1.05, dSum * 1.05);
    const yTicks = [0, 0.25, 0.5, 0.75, 1];
    let s = drawAxes(lo, hi, yMax, 'F(x)', yTicks);

    /* break points: lo, each x_i (sorted, in range, w_i > 0), hi */
    const jumpsSorted = points
      .filter(p => p.w > 0 && p.x > lo && p.x < hi)
      .map(p => ({ x: p.x, w: p.w }))
      .sort((a, b) => a.x - b.x);

    /* segments alternate: smooth, jump, smooth, jump, ..., smooth.
       For smooth segment from x_a to x_b at "discrete offset" off:
         F(x) = Wc * G(x) + off  for  x in [x_a, x_b)  (or up to hi for the last)
       For jump at x_i: vertical from (Wc*G(xi) + offBefore) to (Wc*G(xi) + offAfter) */
    const breaks = [lo];
    for (const j of jumpsSorted) breaks.push(j.x);
    breaks.push(hi);

    let runningOff = 0;  /* discrete sum strictly before this segment */
    for (let segIdx = 0; segIdx < breaks.length - 1; segIdx++) {
      const xa = breaks[segIdx], xb = breaks[segIdx + 1];
      const off = runningOff;
      /* sample smooth segment */
      const N_seg = 80;
      const segPts = [];
      for (let j = 0; j <= N_seg; j++) {
        const x = xa + (xb - xa) * j / N_seg;
        segPts.push([x, Wc * cdfFn(x, params) + off]);
      }
      /* draw with color split at currentX */
      drawColoredPolyline(segPts, currentX, lo, hi, yMax, (str) => { s += str; });

      /* jump at xb (if not the last segment, which ends at hi) */
      if (segIdx < breaks.length - 2) {
        const j = jumpsSorted[segIdx];
        const xj = j.x;
        const yBefore = Wc * cdfFn(xj, params) + off;
        const yAfter  = yBefore + j.w;
        const inLeft = xj <= currentX;
        const color = inLeft ? '#2a7ae2' : '#888';
        const opacity = inLeft ? 1 : 0.5;
        const xpx = xS(lo, hi, xj);
        s += '<line x1="' + xpx + '" y1="' + yS(yMax, yBefore).toFixed(2) + '" x2="' + xpx + '" y2="' + yS(yMax, yAfter).toFixed(2) + '" stroke="' + color + '" stroke-width="2" stroke-dasharray="3,3" opacity="' + opacity + '"/>';
        /* annotate jump magnitude if it's meaningful (≥ 0.03) */
        if (j.w >= 0.03) {
          const yMid = (yS(yMax, yBefore) + yS(yMax, yAfter)) / 2;
          s += '<text x="' + (xpx + 5).toFixed(1) + '" y="' + (yMid + 4).toFixed(1) + '" fill="' + color + '" font-size="11" opacity="' + (inLeft ? 0.95 : 0.55) + '">Δ = ' + j.w.toFixed(2) + '</text>';
        }
        runningOff += j.w;
      }
    }

    /* current x marker, horizontal hint, dot */
    const cumCont = Wc * cdfFn(currentX, params);
    const cumDisc = discreteSumLeft(currentX);
    const cumTotal = cumCont + cumDisc;
    const cxPx = xS(lo, hi, currentX);
    const cyPx = yS(yMax, cumTotal);
    s += '<line x1="' + cxPx + '" y1="' + M.t + '" x2="' + cxPx + '" y2="' + (M.t + innerH) + '" stroke="currentColor" stroke-opacity="0.5" stroke-dasharray="4,3"/>';
    s += '<line x1="' + M.l + '" y1="' + cyPx + '" x2="' + cxPx + '" y2="' + cyPx + '" stroke="#2a7ae2" stroke-opacity="0.4" stroke-dasharray="2,3"/>';
    s += '<circle cx="' + cxPx + '" cy="' + cyPx + '" r="5" fill="#2a7ae2"/>';

    svg.innerHTML = s;
    $('mx-cum').textContent = cumTotal.toFixed(3);
    $('mx-cum-cont').textContent = cumCont.toFixed(3);
    $('mx-cum-disc').textContent = cumDisc.toFixed(3);
  }

  function drawColoredPolyline(pts, cx, lo, hi, yMax, emit) {
    if (pts.length < 2) return;
    const blueColor = '#2a7ae2', grayColor = '#888';
    let leftPath = '', rightPath = '';
    let crossed = false;
    for (let i = 0; i < pts.length; i++) {
      const [x, y] = pts[i];
      const px = xS(lo, hi, x).toFixed(2);
      const py = yS(yMax, y).toFixed(2);
      if (x <= cx) {
        leftPath += (leftPath ? 'L' : 'M') + px + ',' + py;
      } else {
        if (!crossed && leftPath) {
          const [xp, yp] = pts[i - 1];
          const t = (cx - xp) / (x - xp);
          const yc = yp + t * (y - yp);
          const cxPx = xS(lo, hi, cx).toFixed(2);
          const ycPx = yS(yMax, yc).toFixed(2);
          leftPath += 'L' + cxPx + ',' + ycPx;
          rightPath += 'M' + cxPx + ',' + ycPx;
          crossed = true;
        }
        rightPath += (rightPath ? 'L' : 'M') + px + ',' + py;
      }
    }
    if (leftPath && leftPath.length > 1) emit('<path d="' + leftPath + '" fill="none" stroke="' + blueColor + '" stroke-width="2"/>');
    if (rightPath && rightPath.length > 1) emit('<path d="' + rightPath + '" fill="none" stroke="' + grayColor + '" stroke-width="2" opacity="0.55"/>');
  }

  function render() { drawPDF(); drawCDF(); }

  window.addEventListener('resize', render);

  resetParams();
  renderParams();
  renderTable();
  updateMass();
  updateXRange();
  render();
})();
</script>
