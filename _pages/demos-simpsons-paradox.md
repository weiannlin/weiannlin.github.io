---
layout: single
title: "Simpson’s Paradox Mixing Lab"
permalink: /demos/simpsons-paradox/
author_profile: true
---

<style>
.sp-demo {
  --sp-ink: #1f1b16;
  --sp-muted: #756f66;
  --sp-line: #d4cbbb;
  --sp-paper: #f6f0e5;
  --sp-wash: #fffaf0;
  --sp-red: #a92f32;
  --sp-blue: #2f6f8f;
  --sp-green: #4f7d45;
  color: var(--sp-ink);
}
.sp-demo__intro {
  max-width: 48rem;
}
.sp-demo__panel {
  background: linear-gradient(135deg, var(--sp-wash), var(--sp-paper));
  border: 1px solid var(--sp-line);
  border-left: 5px solid var(--sp-red);
  padding: 1.2rem;
  margin: 1.2rem 0;
}
.sp-demo__controls {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1rem;
}
.sp-control {
  border: 1px solid var(--sp-line);
  background: rgba(255, 255, 255, 0.45);
  padding: 1rem;
}
.sp-control label {
  display: block;
  font-weight: 700;
  margin-bottom: 0.35rem;
}
.sp-control input {
  width: 100%;
}
.sp-control output {
  color: var(--sp-red);
  font-weight: 700;
}
.sp-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(270px, 1fr));
  gap: 1rem;
  margin: 1.2rem 0;
}
.sp-card {
  border: 1px solid var(--sp-line);
  padding: 1rem;
  background: rgba(255, 255, 255, 0.52);
}
.sp-card h3 {
  margin-top: 0;
}
.sp-bar {
  margin: 0.85rem 0;
}
.sp-bar__label {
  display: flex;
  justify-content: space-between;
  gap: 1rem;
  font-size: 0.92rem;
  color: var(--sp-muted);
}
.sp-bar__track {
  height: 1rem;
  border: 1px solid var(--sp-line);
  background: #eee5d5;
  overflow: hidden;
}
.sp-bar__fill {
  height: 100%;
  width: 0;
  transition: width 160ms ease;
}
.sp-bar__fill--new {
  background: var(--sp-blue);
}
.sp-bar__fill--standard {
  background: var(--sp-green);
}
.sp-result {
  border: 1px solid var(--sp-line);
  padding: 1rem;
  background: #fff8ec;
  font-weight: 700;
}
.sp-note {
  color: var(--sp-muted);
  font-size: 0.95rem;
}
</style>

<div class="sp-demo" data-sp-demo>
  <p class="sp-demo__intro">
    This interactive lab uses two surgeons as the running example. The within-group success rates are fixed in the block below. Use the sliders to choose the case mix for Surgeon A and Surgeon B, then watch whether a Simpson reversal appears after the patient groups are mixed.
  </p>

  <div class="sp-demo__panel">
    <div class="sp-demo__controls">
      <div class="sp-control">
        <label for="sp-new-risk">High-risk share for Surgeon A</label>
        <input id="sp-new-risk" type="range" min="0" max="100" value="80">
        <output id="sp-new-risk-value">80%</output>
      </div>
      <div class="sp-control">
        <label for="sp-standard-risk">High-risk share for Surgeon B</label>
        <input id="sp-standard-risk" type="range" min="0" max="100" value="10">
        <output id="sp-standard-risk-value">10%</output>
      </div>
    </div>
  </div>

  <div class="sp-grid">
    <section class="sp-card">
      <h3>Within each risk group</h3>
      <div class="sp-bar">
        <div class="sp-bar__label"><span>Surgeon A, low risk</span><span>90%</span></div>
        <div class="sp-bar__track"><div class="sp-bar__fill sp-bar__fill--new" style="width: 90%"></div></div>
      </div>
      <div class="sp-bar">
        <div class="sp-bar__label"><span>Surgeon B, low risk</span><span>80%</span></div>
        <div class="sp-bar__track"><div class="sp-bar__fill sp-bar__fill--standard" style="width: 80%"></div></div>
      </div>
      <div class="sp-bar">
        <div class="sp-bar__label"><span>Surgeon A, high risk</span><span>60%</span></div>
        <div class="sp-bar__track"><div class="sp-bar__fill sp-bar__fill--new" style="width: 60%"></div></div>
      </div>
      <div class="sp-bar">
        <div class="sp-bar__label"><span>Surgeon B, high risk</span><span>50%</span></div>
        <div class="sp-bar__track"><div class="sp-bar__fill sp-bar__fill--standard" style="width: 50%"></div></div>
      </div>
      <p class="sp-note">Surgeon A is better in both groups. This part never changes.</p>
    </section>

    <section class="sp-card">
      <h3>After mixing groups</h3>
      <div class="sp-bar">
        <div class="sp-bar__label"><span>Surgeon A overall</span><span id="sp-new-overall-label">66%</span></div>
        <div class="sp-bar__track"><div id="sp-new-overall-bar" class="sp-bar__fill sp-bar__fill--new"></div></div>
      </div>
      <div class="sp-bar">
        <div class="sp-bar__label"><span>Surgeon B overall</span><span id="sp-standard-overall-label">77%</span></div>
        <div class="sp-bar__track"><div id="sp-standard-overall-bar" class="sp-bar__fill sp-bar__fill--standard"></div></div>
      </div>
      <p class="sp-result" id="sp-result"></p>
      <p class="sp-note">
        The overall rates are weighted averages. Changing the group mix changes the weights, not the within-group success rates.
      </p>
    </section>
  </div>
</div>

<script>
(function () {
  const root = document.querySelector("[data-sp-demo]");
  if (!root) return;

  const newRisk = root.querySelector("#sp-new-risk");
  const standardRisk = root.querySelector("#sp-standard-risk");
  const newRiskValue = root.querySelector("#sp-new-risk-value");
  const standardRiskValue = root.querySelector("#sp-standard-risk-value");
  const newOverallLabel = root.querySelector("#sp-new-overall-label");
  const standardOverallLabel = root.querySelector("#sp-standard-overall-label");
  const newOverallBar = root.querySelector("#sp-new-overall-bar");
  const standardOverallBar = root.querySelector("#sp-standard-overall-bar");
  const result = root.querySelector("#sp-result");

  const rates = {
    newLow: 0.90,
    newHigh: 0.60,
    standardLow: 0.80,
    standardHigh: 0.50
  };

  function percent(value) {
    return `${Math.round(value * 100)}%`;
  }

  function update() {
    const hNew = Number(newRisk.value) / 100;
    const hStandard = Number(standardRisk.value) / 100;
    const pNew = (1 - hNew) * rates.newLow + hNew * rates.newHigh;
    const pStandard = (1 - hStandard) * rates.standardLow + hStandard * rates.standardHigh;

    newRiskValue.textContent = percent(hNew);
    standardRiskValue.textContent = percent(hStandard);
    newOverallLabel.textContent = percent(pNew);
    standardOverallLabel.textContent = percent(pStandard);
    newOverallBar.style.width = percent(pNew);
    standardOverallBar.style.width = percent(pStandard);

    if (pNew < pStandard) {
      result.textContent = "Simpson reversal. Surgeon A wins inside each risk group, but loses after mixing.";
    } else if (pNew > pStandard) {
      result.textContent = "No reversal under this mix. Surgeon A wins inside each risk group and overall.";
    } else {
      result.textContent = "The overall rates are tied under this mix.";
    }
  }

  newRisk.addEventListener("input", update);
  standardRisk.addEventListener("input", update);
  update();
})();
</script>
