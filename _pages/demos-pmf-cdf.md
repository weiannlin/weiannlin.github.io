---
layout: archive
title: "From PMF to CDF"
permalink: /demos/pmf-cdf/
author_profile: true
---

{% include base_path %}

<style>
  .pc-section { margin: 1.5rem 0; }
  .pc-section.center { text-align: center; }
  .pc-input-table { margin: 0 auto; border-collapse: collapse; }
  .pc-input-table th, .pc-input-table td { padding: 0.25rem 0.5rem; text-align: center; }
  /* Specificity bump: journal-base sets `.page__content table th { text-align: left }`
     which would otherwise win over the rule above. Adding `thead` matches that
     specificity, and the inline <style> wins on document order. */
  .pc-input-table thead th {
    text-align: center;
    font-weight: 600; opacity: 0.85; font-size: 0.78rem;
    letter-spacing: 0.16em; text-transform: uppercase;
    font-feature-settings: "smcp" 1, "c2sc" 1, "kern" 1;
    color: var(--journal-accent);
    border-top: none; border-bottom: 1px solid var(--journal-divider);
    background: transparent;
  }
  .pc-input-table input {
    width: 5em; padding: 0.25rem 0.45rem;
    background: var(--journal-bg); color: var(--journal-ink);
    border: 1px solid var(--journal-divider); border-radius: 2px;
    text-align: center;
    font-family: 'IBM Plex Mono', Menlo, Consolas, monospace;
  }
  .pc-row-rm {
    padding: 0.1rem 0.55rem; cursor: pointer;
    background: transparent; border: 1px solid var(--journal-divider); border-radius: 2px;
    color: var(--journal-ink-soft);
  }
  .pc-row-rm:hover { color: var(--journal-accent); border-color: var(--journal-accent); }
  .pc-add {
    margin: 0.5rem 0; padding: 0.4rem 1rem; cursor: pointer;
    background: var(--journal-bg); color: var(--journal-ink);
    border: 1px solid var(--journal-ink); border-radius: 2px;
    font-family: inherit; font-size: 0.82rem;
    letter-spacing: 0.08em; text-transform: uppercase;
    font-feature-settings: "smcp" 1, "c2sc" 1, "kern" 1;
    transition: background 120ms, color 120ms;
  }
  .pc-add:hover { background: var(--journal-ink); color: var(--journal-bg); }
  .pc-sum { margin-top: 0.4rem; opacity: 0.8; font-size: 0.92rem; font-family: 'IBM Plex Mono', monospace; }
  .pc-sum.warn { color: var(--journal-accent); opacity: 1; }
  .pc-slider-wrap { margin: 1rem auto; max-width: 720px; }
  .pc-slider-wrap label { display: block; margin-bottom: 0.4rem; font-size: 0.95rem; text-align: center; }
  .pc-slider-wrap label strong { font-family: 'IBM Plex Mono', monospace; color: var(--journal-accent); }
  /* Slider input element is widened by one thumb-diameter (16px) and offset so the thumb's CENTER reaches plot_left at value=min and plot_right at value=max. Without this, the browser insets the thumb by half its width and the thumb never aligns with the chart's dashed current-x line at the extremes. */
  .pc-slider-wrap input[type=range] {
    -webkit-appearance: none; appearance: none;
    background: transparent;
    display: block;
    margin-left: calc(8.333% - 8px);
    width: calc(89.334% + 16px);
    height: 20px;
    cursor: pointer;
    padding: 0;
  }
  .pc-slider-wrap input[type=range]::-webkit-slider-runnable-track {
    height: 3px; border-radius: 2px;
    background: linear-gradient(to right, var(--journal-accent) 0%, var(--journal-accent) var(--pc-fill, 50%), var(--journal-divider) var(--pc-fill, 50%), var(--journal-divider) 100%);
  }
  .pc-slider-wrap input[type=range]::-moz-range-track { height: 3px; background: var(--journal-divider); border-radius: 2px; border: none; }
  .pc-slider-wrap input[type=range]::-moz-range-progress { height: 3px; background: var(--journal-accent); border-radius: 2px; border: none; }
  .pc-slider-wrap input[type=range]::-webkit-slider-thumb {
    -webkit-appearance: none;
    width: 16px; height: 16px; border-radius: 50%;
    background: var(--journal-accent); cursor: pointer; margin-top: -6.5px;
    border: 2px solid var(--journal-bg); box-shadow: 0 1px 2px rgba(31,28,24,0.25);
  }
  .pc-slider-wrap input[type=range]::-moz-range-thumb {
    width: 16px; height: 16px; border-radius: 50%;
    background: var(--journal-accent); cursor: pointer;
    border: 2px solid var(--journal-bg); box-shadow: 0 1px 2px rgba(31,28,24,0.25);
  }
  .pc-charts { max-width: 720px; margin-inline: auto; }
  .pc-charts svg { width: 100%; height: auto; display: block; margin-bottom: 0.4rem; }
  .pc-readout {
    margin-top: 0.5rem; padding: 0.4rem 0.85rem;
    border-left: 2px solid var(--journal-accent);
    text-align: left; font-size: 0.95rem;
  }
  .pc-readout strong { color: var(--journal-accent); font-size: 1.1rem; font-family: 'IBM Plex Mono', monospace; }
</style>

The probability mass function (PMF) tells you how much probability sits at each value of a discrete random variable. The cumulative distribution function (CDF) tells you, for each $x$, the total probability of being $\leq x$. They carry the same information; the CDF is just the running sum of the PMF.

Below, you can build your own PMF by editing the $(x, p)$ table. The slider sweeps a "current $x$" across the axis: PMF lollipops at $x \leq$ current $x$ turn red, and their masses sum exactly to the height of the CDF curve at that $x$.

## Interactive

<div class="pc-section center">
  <table class="pc-input-table" id="pc-input"><thead><tr><th>$x$</th><th>$p$</th><th></th></tr></thead><tbody></tbody></table>
  <button class="pc-add" id="pc-add">+ add point</button>
  <div class="pc-sum" id="pc-sum">Total p = —</div>
</div>

<div class="pc-slider-wrap">
  <label>Current $x$ = <strong id="pc-x-val">—</strong></label>
  <input type="range" id="pc-x" min="0" max="6" step="0.01" value="3">
</div>

<div class="pc-charts">
  <svg id="pc-pmf" viewBox="0 0 600 200" preserveAspectRatio="xMidYMid meet"></svg>
  <svg id="pc-cdf" viewBox="0 0 600 200" preserveAspectRatio="xMidYMid meet"></svg>
  <div class="pc-readout">
    Cumulative mass $F(x)$ = <strong id="pc-cum">—</strong>. The red PMF lollipops sum to this; the CDF curve traces it.
  </div>
</div>

## What it shows

The CDF is a **step function**: flat between the PMF's mass points, jumping straight up by $p\_i$ at each $x = x\_i$ where the PMF carries mass. Slide the current $x$ across some $x\_i$ and the CDF jumps while one more PMF lollipop turns red — the same probability mass, viewed two ways.

Convention: this CDF is right-continuous. At each $x=x_i$, $F(x_i)=\mathbb{P}(X\leq x_i)$ already includes the jump.

[The next demo](/demos/pdf-cdf/) replaces the discrete spikes with a smooth density (PDF). The construction is the same idea, but the running **sum** becomes a running **integral**, and the CDF turns from a staircase into a continuous curve.

<script>
(function() {
  const $ = id => document.getElementById(id);
  let points = [{x:1,p:0.1},{x:2,p:0.2},{x:3,p:0.4},{x:4,p:0.2},{x:5,p:0.1}];
  let currentX = 3;

  const tbody = document.querySelector('#pc-input tbody');

  function renderTable() {
    tbody.innerHTML = '';
    points.forEach((pt, idx) => {
      const tr = document.createElement('tr');
      tr.innerHTML =
        '<td><input type="number" data-i="'+idx+'" data-k="x" step="any" value="'+pt.x+'"></td>' +
        '<td><input type="number" data-i="'+idx+'" data-k="p" step="0.01" min="0" value="'+pt.p+'"></td>' +
        '<td><button class="pc-row-rm" data-i="'+idx+'" title="remove">&times;</button></td>';
      tbody.appendChild(tr);
    });
    tbody.querySelectorAll('input').forEach(el => el.addEventListener('input', onCellEdit));
    tbody.querySelectorAll('.pc-row-rm').forEach(el => el.addEventListener('click', onRowRemove));
  }

  function onCellEdit(e) {
    const i = +e.target.dataset.i, k = e.target.dataset.k;
    const v = parseFloat(e.target.value);
    if (!isFinite(v)) return;
    points[i][k] = v;
    afterPointsChange(k === 'x');
  }

  function onRowRemove(e) {
    const i = +e.currentTarget.dataset.i;
    points.splice(i, 1);
    if (points.length === 0) points.push({x:0, p:1});
    renderTable();
    afterPointsChange(true);
  }

  $('pc-add').addEventListener('click', () => {
    const xs = points.map(p => p.x);
    const newX = (xs.length ? Math.max(...xs) : 0) + 1;
    points.push({x: newX, p: 0});
    renderTable();
    afterPointsChange(true);
  });

  const slider = $('pc-x');
  function updateSliderFill() {
    const min = parseFloat(slider.min), max = parseFloat(slider.max);
    const pct = (max > min) ? ((currentX - min) / (max - min)) * 100 : 50;
    slider.style.setProperty('--pc-fill', Math.max(0, Math.min(100, pct)).toFixed(1) + '%');
  }
  slider.addEventListener('input', () => {
    currentX = parseFloat(slider.value);
    $('pc-x-val').textContent = currentX.toFixed(2);
    updateSliderFill();
    render();
  });

  function afterPointsChange(rangeMayHaveChanged) {
    points.sort((a, b) => a.x - b.x);
    if (rangeMayHaveChanged) updateSliderRange();
    updateSum();
    render();
  }

  function updateSliderRange() {
    const xs = points.map(p => p.x);
    if (xs.length === 0) return;
    const lo = Math.min(...xs) - 1, hi = Math.max(...xs) + 1;
    slider.min = lo; slider.max = hi;
    slider.step = ((hi - lo) / 600).toFixed(4);
    if (currentX < lo || currentX > hi) currentX = (lo + hi) / 2;
    slider.value = currentX;
    $('pc-x-val').textContent = currentX.toFixed(2);
    updateSliderFill();
  }

  function updateSum() {
    const total = points.reduce((s, p) => s + (p.p > 0 ? p.p : 0), 0);
    const el = $('pc-sum');
    el.textContent = 'Total p = ' + total.toFixed(3);
    if (Math.abs(total - 1) > 0.001) {
      el.classList.add('warn');
      el.textContent += '   (not 1 — distributions normally sum to 1)';
    } else {
      el.classList.remove('warn');
    }
  }

  /* drawing */
  const W = 600, H = 200, M = { l: 50, r: 14, t: 14, b: 32 };
  const innerW = W - M.l - M.r, innerH = H - M.t - M.b;
  const xScale = (lo, hi, val) => M.l + ((val - lo) / (hi - lo)) * innerW;
  const yScale = (yMax, val) => M.t + (1 - val / yMax) * innerH;

  function axisRange() {
    const xs = points.map(p => p.x);
    const lo = xs.length ? Math.min(...xs) - 1 : -1;
    const hi = xs.length ? Math.max(...xs) + 1 : 1;
    return { lo, hi };
  }

  function drawAxes(xLo, xHi, yMax, yLabel, yTicks) {
    let s = '';
    s += '<rect x="'+M.l+'" y="'+M.t+'" width="'+innerW+'" height="'+innerH+'" fill="none" stroke="currentColor" stroke-opacity="0.25"/>';
    for (const v of yTicks) {
      const y = yScale(yMax, v);
      s += '<line x1="'+M.l+'" y1="'+y.toFixed(1)+'" x2="'+(M.l+innerW)+'" y2="'+y.toFixed(1)+'" stroke="currentColor" stroke-opacity="0.1"/>';
      s += '<text x="'+(M.l-6)+'" y="'+(y+4).toFixed(1)+'" text-anchor="end" fill="currentColor" font-size="13" opacity="0.75">'+v.toFixed(2)+'</text>';
    }
    const xTicks = [xLo, (xLo+xHi)/2, xHi];
    for (const v of xTicks) {
      const x = xScale(xLo, xHi, v);
      s += '<text x="'+x.toFixed(1)+'" y="'+(M.t+innerH+18)+'" text-anchor="middle" fill="currentColor" font-size="13" opacity="0.75">'+v.toFixed(2)+'</text>';
    }
    s += '<text x="'+(M.l-34)+'" y="'+(M.t+innerH/2)+'" text-anchor="middle" fill="currentColor" font-size="13" opacity="0.7" transform="rotate(-90 '+(M.l-34)+' '+(M.t+innerH/2)+')">'+yLabel+'</text>';
    return s;
  }

  function drawPMF() {
    const svg = $('pc-pmf');
    const { lo, hi } = axisRange();
    const yMax = Math.max(...points.map(p => p.p), 0.01) * 1.18;
    const yTicks = [0, yMax/2, yMax];
    let s = drawAxes(lo, hi, yMax, 'p(x)', yTicks);
    for (const pt of points) {
      const x = xScale(lo, hi, pt.x);
      const yTop = yScale(yMax, Math.max(pt.p, 0));
      const yBot = yScale(yMax, 0);
      const inLeft = pt.x <= currentX;
      const color = inLeft ? '#9c2d2d' : '#888';
      const opacity = inLeft ? 1 : 0.4;
      const dotR = inLeft ? 5 : 4;
      s += '<line x1="'+x+'" y1="'+yBot+'" x2="'+x+'" y2="'+yTop+'" stroke="'+color+'" stroke-width="2" opacity="'+opacity+'"/>';
      s += '<circle cx="'+x+'" cy="'+yTop+'" r="'+dotR+'" fill="'+color+'" opacity="'+opacity+'"/>';
    }
    const cx = xScale(lo, hi, currentX);
    s += '<line x1="'+cx+'" y1="'+M.t+'" x2="'+cx+'" y2="'+(M.t+innerH)+'" stroke="currentColor" stroke-opacity="0.5" stroke-dasharray="4,3"/>';
    svg.innerHTML = s;
  }

  function drawCDF() {
    const svg = $('pc-cdf');
    const { lo, hi } = axisRange();
    const totalP = points.reduce((s,p) => s + (p.p > 0 ? p.p : 0), 0);
    const yMax = Math.max(1.05, totalP * 1.1);
    /* y-axis numeric labels always cap at 1.0 even if curve overshoots — 1 is the meaningful probability ceiling. */
    const yTicks = [0, 0.25, 0.5, 0.75, 1];
    let s = drawAxes(lo, hi, yMax, 'F(x)', yTicks);

    let cumPts = [[lo, 0]];
    let acc = 0;
    for (const pt of points) {
      cumPts.push([pt.x, acc]);
      acc += (pt.p > 0 ? pt.p : 0);
      cumPts.push([pt.x, acc]);
    }
    cumPts.push([hi, acc]);

    /* Draw step curve segment by segment. Horizontal segments are solid, blue
       when entirely to the left of currentX (split at currentX if straddling),
       gray otherwise. Vertical jumps are dashed (signal: not part of the
       function's graph between levels) and colored the same way. */
    for (let i = 0; i < cumPts.length - 1; i++) {
      const [ax, ay] = cumPts[i];
      const [bx, by] = cumPts[i + 1];
      const isVertical = (ax === bx);
      if (isVertical) {
        const inLeft = ax <= currentX;
        const color = inLeft ? '#9c2d2d' : '#888';
        const opacity = inLeft ? 1 : 0.5;
        const xPx = xScale(lo, hi, ax);
        s += '<line x1="'+xPx.toFixed(1)+'" y1="'+yScale(yMax, ay).toFixed(1)+'" x2="'+xPx.toFixed(1)+'" y2="'+yScale(yMax, by).toFixed(1)+'" stroke="'+color+'" stroke-width="2" stroke-dasharray="3,3" opacity="'+opacity+'"/>';
      } else {
        const yPx = yScale(yMax, ay);
        const x1 = xScale(lo, hi, ax);
        const x2 = xScale(lo, hi, bx);
        if (bx <= currentX) {
          s += '<line x1="'+x1.toFixed(1)+'" y1="'+yPx.toFixed(1)+'" x2="'+x2.toFixed(1)+'" y2="'+yPx.toFixed(1)+'" stroke="#9c2d2d" stroke-width="2"/>';
        } else if (ax >= currentX) {
          s += '<line x1="'+x1.toFixed(1)+'" y1="'+yPx.toFixed(1)+'" x2="'+x2.toFixed(1)+'" y2="'+yPx.toFixed(1)+'" stroke="#888" stroke-width="2" opacity="0.5"/>';
        } else {
          const xc = xScale(lo, hi, currentX);
          s += '<line x1="'+x1.toFixed(1)+'" y1="'+yPx.toFixed(1)+'" x2="'+xc.toFixed(1)+'" y2="'+yPx.toFixed(1)+'" stroke="#9c2d2d" stroke-width="2"/>';
          s += '<line x1="'+xc.toFixed(1)+'" y1="'+yPx.toFixed(1)+'" x2="'+x2.toFixed(1)+'" y2="'+yPx.toFixed(1)+'" stroke="#888" stroke-width="2" opacity="0.5"/>';
        }
      }
    }

    /* current x marker, horizontal hint to dot, dot */
    const cxPx = xScale(lo, hi, currentX);
    const cumAtCurrent = cumValue(currentX);
    const cyPx = yScale(yMax, cumAtCurrent);
    s += '<line x1="'+cxPx+'" y1="'+M.t+'" x2="'+cxPx+'" y2="'+(M.t+innerH)+'" stroke="currentColor" stroke-opacity="0.5" stroke-dasharray="4,3"/>';
    s += '<line x1="'+M.l+'" y1="'+cyPx+'" x2="'+cxPx+'" y2="'+cyPx+'" stroke="#9c2d2d" stroke-opacity="0.4" stroke-dasharray="2,3"/>';
    s += '<circle cx="'+cxPx+'" cy="'+cyPx+'" r="5" fill="#9c2d2d"/>';

    svg.innerHTML = s;
    $('pc-cum').textContent = cumAtCurrent.toFixed(3);
  }

  function cumValue(x) {
    let acc = 0;
    for (const pt of points) {
      if (pt.x <= x) acc += (pt.p > 0 ? pt.p : 0);
    }
    return acc;
  }

  function render() { drawPMF(); drawCDF(); }

  window.addEventListener('resize', render);

  renderTable();
  updateSliderRange();
  updateSum();
  render();
})();
</script>
