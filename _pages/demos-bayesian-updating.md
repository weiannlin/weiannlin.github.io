---
layout: archive
title: "Rapid Test Bayesian Updating Lab"
permalink: /demos/bayesian-updating/
author_profile: true
---

{% include base_path %}

<style>
  .bu-panel {
    border-left: 2px solid var(--journal-accent);
    padding: 0.85rem 1rem;
    background: rgba(255, 255, 255, 0.12);
    margin: 1rem 0;
  }
  .bu-grid {
    display: grid;
    grid-template-columns: minmax(0, 1fr);
    gap: 1rem;
    align-items: start;
  }
  @media (min-width: 760px) {
    .bu-grid { grid-template-columns: minmax(0, 0.72fr) minmax(0, 1.28fr); }
  }
  .bu-controls label {
    display: block;
    margin: 0.55rem 0;
    font-size: 0.95rem;
  }
  .bu-controls input {
    width: 100%;
    box-sizing: border-box;
    padding: 0.3rem 0.5rem;
    background: var(--journal-bg);
    color: var(--journal-ink);
    border: 1px solid var(--journal-divider);
    border-radius: 2px;
    font-family: 'IBM Plex Mono', Menlo, Consolas, monospace;
    font-size: 0.92rem;
  }
  .bu-model {
    margin-top: 0.75rem;
    padding-top: 0.65rem;
    border-top: 1px solid var(--journal-divider);
    color: var(--journal-ink-soft);
    font-size: 0.92rem;
  }
  .bu-model code {
    background: transparent;
    color: var(--journal-ink);
    font-family: 'IBM Plex Mono', Menlo, Consolas, monospace;
    padding: 0;
  }
  .bu-result-buttons {
    display: grid;
    grid-template-columns: 1fr;
    gap: 0.6rem;
    margin-top: 1rem;
  }
  @media (min-width: 520px) {
    .bu-result-buttons { grid-template-columns: 1fr 1fr; }
  }
  .bu-btn {
    padding: 0.7rem 0.9rem;
    cursor: pointer;
    background: var(--journal-bg);
    color: var(--journal-ink);
    border: 1px solid var(--journal-ink);
    border-radius: 2px;
    font-family: inherit;
    font-size: 0.82rem;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    font-feature-settings: "smcp" 1, "c2sc" 1, "kern" 1;
    transition: background 120ms, color 120ms, border-color 120ms;
  }
  .bu-btn:hover,
  .bu-btn:focus {
    background: var(--journal-ink);
    color: var(--journal-bg);
  }
  .bu-btn.soft {
    border-color: var(--journal-divider);
    color: var(--journal-ink-soft);
  }
  .bu-small-actions {
    display: flex;
    gap: 0.5rem;
    flex-wrap: wrap;
    margin-top: 0.75rem;
  }
  .bu-small-actions .bu-btn {
    padding: 0.42rem 0.85rem;
  }
  .bu-readout {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 0.75rem;
    margin-bottom: 0.9rem;
  }
  .bu-card {
    border: 1px solid var(--journal-divider);
    padding: 0.65rem 0.75rem;
    background: var(--journal-bg);
  }
  .bu-card .label {
    display: block;
    color: var(--journal-ink-soft);
    font-size: 0.78rem;
    letter-spacing: 0.12em;
    text-transform: uppercase;
  }
  .bu-card strong {
    color: var(--journal-accent);
    font-family: 'IBM Plex Mono', Menlo, Consolas, monospace;
    font-size: 1.25rem;
  }
  .bu-bars {
    display: grid;
    gap: 0.55rem;
    margin: 0.8rem 0 1rem;
  }
  .bu-bar-row {
    display: grid;
    grid-template-columns: 6.9rem minmax(0, 1fr) 3.8rem;
    gap: 0.5rem;
    align-items: center;
    font-size: 0.92rem;
  }
  .bu-bar-track {
    position: relative;
    height: 0.72rem;
    background: var(--journal-divider);
    overflow: hidden;
  }
  .bu-bar-fill {
    height: 100%;
    width: 0;
    background: var(--journal-accent);
  }
  .bu-chart-wrap {
    margin-top: 0.6rem;
  }
  .bu-chart-wrap svg {
    width: 100%;
    height: auto;
    display: block;
  }
  .bu-table-wrap {
    overflow-x: auto;
    margin-top: 1rem;
  }
  .bu-history {
    width: 100%;
    border-collapse: collapse;
    font-size: 0.9rem;
  }
  .bu-history thead th {
    text-align: left;
    font-weight: 600;
    opacity: 0.85;
    font-size: 0.78rem;
    letter-spacing: 0.11em;
    text-transform: uppercase;
    color: var(--journal-accent);
    border-top: 1px solid var(--journal-ink);
    border-bottom: 1px solid var(--journal-ink);
    background: transparent;
    white-space: nowrap;
  }
  .bu-history th,
  .bu-history td {
    padding: 0.45rem 0.55rem;
    border-bottom: 1px solid var(--journal-divider);
    vertical-align: top;
  }
  .bu-history td.num {
    font-family: 'IBM Plex Mono', Menlo, Consolas, monospace;
    white-space: nowrap;
  }
  .bu-empty {
    border: 1px dashed var(--journal-divider);
    padding: 0.75rem;
    color: var(--journal-ink-soft);
    font-style: italic;
  }
</style>

Bayes' rule is easiest to see as repeated updating. Start with a prior probability for a hidden state, record one observation, then use the posterior as the next prior.

This lab uses a rapid diagnostic test as the running example. The hidden state is whether a person has the disease. Each test returns one of two observations, positive or negative. The controls let you change the prevalence, sensitivity, and specificity, then watch how the interpretation of the same test result changes.

This is a probability demo, not medical guidance. The repeated-test calculations assume that test errors are conditionally independent given the true health state. Once the true state is fixed, each test is being treated as a fresh piece of evidence. In practice, sampling quality, test batch, timing, and shared biological factors can make repeated tests less independent than the idealized model.

## Interactive

<div class="bu-grid">
  <div class="bu-panel bu-controls">
    <label>Prevalence prior $\mathbb{P}(D)$
      <input id="bu-prior" type="number" min="0.001" max="0.999" step="0.001" value="0.050">
    </label>
    <label>Sensitivity $\mathbb{P}(+\mid D)$
      <input id="bu-sensitivity" type="number" min="0.001" max="0.999" step="0.001" value="0.950">
    </label>
    <label>Specificity $\mathbb{P}(-\mid D^\prime)$
      <input id="bu-specificity" type="number" min="0.001" max="0.999" step="0.001" value="0.900">
    </label>

    <div class="bu-model">
      Sensitivity is the true positive rate, while specificity is the true negative rate. A positive result uses $\mathbb{P}(+\mid D^\prime)=1-\mathrm{specificity}$, so lowering specificity directly raises the false positive rate.
    </div>

    <div class="bu-result-buttons">
      <button class="bu-btn" id="bu-positive">Positive result</button>
      <button class="bu-btn" id="bu-negative">Negative result</button>
    </div>

    <div class="bu-small-actions">
      <button class="bu-btn soft" id="bu-undo">Undo</button>
      <button class="bu-btn soft" id="bu-reset">Reset</button>
    </div>
  </div>

  <div class="bu-panel">
    <div class="bu-readout">
      <div class="bu-card">
        <span class="label">Current $\mathbb{P}(D)$</span>
        <strong id="bu-current">—</strong>
      </div>
      <div class="bu-card">
        <span class="label">Last update</span>
        <strong id="bu-delta">—</strong>
      </div>
    </div>

    <div class="bu-bars">
      <div class="bu-bar-row">
        <span>Disease $D$</span>
        <div class="bu-bar-track"><div class="bu-bar-fill" id="bu-disease-bar"></div></div>
        <span id="bu-disease-val">—</span>
      </div>
      <div class="bu-bar-row">
        <span>No disease</span>
        <div class="bu-bar-track"><div class="bu-bar-fill" id="bu-healthy-bar"></div></div>
        <span id="bu-healthy-val">—</span>
      </div>
    </div>

    <div class="bu-chart-wrap">
      <svg id="bu-chart" viewBox="0 0 600 260" preserveAspectRatio="xMidYMid meet"></svg>
    </div>
  </div>
</div>

<div class="bu-table-wrap">
  <table class="bu-history" id="bu-history">
    <thead>
      <tr>
        <th>Step</th>
        <th>Result</th>
        <th>Prior</th>
        <th>$\mathbb{P}(E\mid D)$</th>
        <th>$\mathbb{P}(E\mid D^\prime)$</th>
        <th>Posterior</th>
      </tr>
    </thead>
    <tbody></tbody>
  </table>
</div>

<div class="bu-empty" id="bu-empty">Click a result button to start the update path.</div>

## What it shows

**One observation, one update.** A positive test is evidence for disease, but the strength of that evidence depends on prevalence and false positives. A negative test is evidence against disease, but a test with imperfect sensitivity can still miss true cases.

**Posterior becomes the next prior.** After one test, the updated probability becomes the starting point for the next test. Consecutive positive results can push the curve upward; consecutive negative results can push it downward.

**High sensitivity and high specificity.** When both are high, a positive result strongly pushes the probability upward, and a negative result strongly pushes it downward. In that setting, each test result carries a lot of information.

**High sensitivity and low specificity.** The test rarely misses true cases, but it also produces many false positives. A negative result can still be reassuring, while a positive result may need more confirmation, especially when the prevalence is low.

**A bridge to Naive Bayes.** Repeated updates are equivalent to multiplying conditional probabilities when the observations are treated as conditionally independent given the hidden state. That is the same simplification behind a Naive Bayes classifier. In this demo, the observations are repeated test results. In a classifier, the observations are features such as words, symptoms, or signals. The mathematical move is the same, and the next topic will make this independence assumption precise.

<script>
(function() {
  const $ = id => document.getElementById(id);
  const clamp = (x, lo, hi) => Math.max(lo, Math.min(hi, x));
  const fmt = x => Number.isFinite(x) ? x.toFixed(3) : '—';
  const pct = x => Number.isFinite(x) ? (100 * x).toFixed(1) + '%' : '—';

  let initialPrior = 0.05;
  let history = [];

  function readInitialPrior() {
    const p = clamp(parseFloat($('bu-prior').value), 0.001, 0.999);
    $('bu-prior').value = p.toFixed(3);
    return p;
  }

  function readSensitivity() {
    const p = clamp(parseFloat($('bu-sensitivity').value), 0.001, 0.999);
    $('bu-sensitivity').value = p.toFixed(3);
    return p;
  }

  function readSpecificity() {
    const p = clamp(parseFloat($('bu-specificity').value), 0.001, 0.999);
    $('bu-specificity').value = p.toFixed(3);
    return p;
  }

  function currentProb() {
    return history.length ? history[history.length - 1].posterior : initialPrior;
  }

  function posterior(prior, probGivenDisease, probGivenNoDisease) {
    const numerator = probGivenDisease * prior;
    const denom = numerator + probGivenNoDisease * (1 - prior);
    return denom > 0 ? numerator / denom : prior;
  }

  function addResult(kind) {
    const sensitivity = readSensitivity();
    const specificity = readSpecificity();
    const prior = currentProb();
    const row = kind === 'positive'
      ? {
          result: 'Positive',
          probGivenDisease: sensitivity,
          probGivenNoDisease: 1 - specificity
        }
      : {
          result: 'Negative',
          probGivenDisease: 1 - sensitivity,
          probGivenNoDisease: specificity
        };
    row.prior = prior;
    row.posterior = posterior(prior, row.probGivenDisease, row.probGivenNoDisease);
    history.push(row);
    render();
  }

  function resetAll() {
    initialPrior = readInitialPrior();
    history = [];
    render();
  }

  function undo() {
    history.pop();
    render();
  }

  function render() {
    const p = currentProb();
    $('bu-current').textContent = fmt(p);
    $('bu-disease-val').textContent = pct(p);
    $('bu-healthy-val').textContent = pct(1 - p);
    $('bu-disease-bar').style.width = pct(p);
    $('bu-healthy-bar').style.width = pct(1 - p);
    if (history.length) {
      const last = history[history.length - 1];
      const d = last.posterior - last.prior;
      const sign = d > 0 ? '+' : '';
      $('bu-delta').textContent = sign + d.toFixed(3);
    } else {
      $('bu-delta').textContent = '—';
    }
    renderTable();
    drawChart();
  }

  function renderTable() {
    const tbody = document.querySelector('#bu-history tbody');
    tbody.innerHTML = '';
    history.forEach((h, i) => {
      const tr = document.createElement('tr');
      tr.innerHTML =
        '<td class="num">' + (i + 1) + '</td>' +
        '<td>' + h.result + '</td>' +
        '<td class="num">' + fmt(h.prior) + '</td>' +
        '<td class="num">' + fmt(h.probGivenDisease) + '</td>' +
        '<td class="num">' + fmt(h.probGivenNoDisease) + '</td>' +
        '<td class="num">' + fmt(h.posterior) + '</td>';
      tbody.appendChild(tr);
    });
    $('bu-empty').style.display = history.length ? 'none' : 'block';
  }

  function drawChart() {
    const svg = $('bu-chart');
    const W = 600, H = 260;
    const M = { l: 54, r: 18, t: 18, b: 42 };
    const iw = W - M.l - M.r;
    const ih = H - M.t - M.b;
    const values = [initialPrior].concat(history.map(h => h.posterior));
    const n = values.length;
    const x = i => M.l + (n === 1 ? 0 : (i / (n - 1)) * iw);
    const y = v => M.t + (1 - v) * ih;

    let html = '';
    html += '<rect x="' + M.l + '" y="' + M.t + '" width="' + iw + '" height="' + ih + '" fill="none" stroke="currentColor" stroke-opacity="0.25"/>';
    [0, 0.25, 0.5, 0.75, 1].forEach(t => {
      const yy = y(t);
      html += '<line x1="' + M.l + '" y1="' + yy + '" x2="' + (M.l + iw) + '" y2="' + yy + '" stroke="currentColor" stroke-opacity="0.10"/>';
      html += '<text x="' + (M.l - 8) + '" y="' + (yy + 4) + '" text-anchor="end" fill="currentColor" font-size="13" opacity="0.72">' + t.toFixed(2) + '</text>';
    });
    html += '<text x="' + M.l + '" y="' + (H - 12) + '" text-anchor="middle" fill="currentColor" font-size="13" opacity="0.75">0</text>';
    html += '<text x="' + (M.l + iw) + '" y="' + (H - 12) + '" text-anchor="middle" fill="currentColor" font-size="13" opacity="0.75">' + Math.max(0, n - 1) + '</text>';

    if (values.length === 1) {
      html += '<circle cx="' + x(0) + '" cy="' + y(values[0]) + '" r="5" fill="var(--journal-accent)"/>';
    } else {
      const pts = values.map((v, i) => x(i).toFixed(2) + ',' + y(v).toFixed(2)).join(' ');
      html += '<polyline points="' + pts + '" fill="none" stroke="var(--journal-accent)" stroke-width="2.5"/>';
      values.forEach((v, i) => {
        html += '<circle cx="' + x(i).toFixed(2) + '" cy="' + y(v).toFixed(2) + '" r="4.2" fill="var(--journal-accent)"/>';
      });
    }
    html += '<text x="' + (M.l + iw / 2) + '" y="' + (H - 12) + '" text-anchor="middle" fill="currentColor" font-size="13" opacity="0.72">observation step</text>';
    html += '<text transform="translate(16 ' + (M.t + ih / 2) + ') rotate(-90)" text-anchor="middle" fill="currentColor" font-size="13" opacity="0.72">ℙ(D)</text>';
    svg.innerHTML = html;
  }

  $('bu-positive').addEventListener('click', () => addResult('positive'));
  $('bu-negative').addEventListener('click', () => addResult('negative'));
  $('bu-undo').addEventListener('click', undo);
  $('bu-reset').addEventListener('click', resetAll);
  $('bu-prior').addEventListener('change', resetAll);
  $('bu-sensitivity').addEventListener('change', resetAll);
  $('bu-specificity').addEventListener('change', resetAll);
  resetAll();
})();
</script>
