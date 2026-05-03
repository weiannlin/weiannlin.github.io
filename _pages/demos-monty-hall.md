---
layout: archive
title: "The Monty Hall Problem"
permalink: /demos/monty-hall/
author_profile: true
---

{% include base_path %}

<style>
  .mh-section { margin: 1.5rem 0; }
  .mh-doors { display: flex; gap: 0.75rem; margin: 1rem 0; flex-wrap: wrap; }
  .mh-door {
    font-size: 2.5rem; padding: 0.6rem 1rem; cursor: pointer;
    border: 2px solid #888; background: #f7f7f7; color: #222;
    border-radius: 8px; min-width: 4rem; line-height: 1;
  }
  .mh-door:hover:not(:disabled) { background: #e9e9e9; }
  .mh-door:disabled { cursor: default; opacity: 0.95; }
  .mh-door.picked { border-color: #2a7ae2; box-shadow: 0 0 0 2px #2a7ae2 inset; }
  .mh-door.revealed { background: #fff; }
  .mh-status { margin: 0.5rem 0; min-height: 1.4em; }
  .mh-choice { margin: 0.5rem 0; }
  .mh-choice button, .mh-reset, .mh-run {
    margin-right: 0.5rem; padding: 0.4rem 0.9rem; cursor: pointer;
    background: #fff; color: #222; border: 1px solid #888; border-radius: 4px;
  }
  .mh-tally {
    margin-top: 1rem; padding: 0.4rem 0.75rem;
    border-left: 3px solid #2a7ae2;
    font-size: 0.92rem;
    display: flex; flex-wrap: wrap; gap: 1.25rem;
  }
  .mh-sim label { display: inline-block; margin: 0.25rem 1rem 0.25rem 0; }
  .mh-sim input, .mh-sim select {
    padding: 0.2rem 0.4rem;
    background: #fff; color: #222;
    border: 1px solid #888; border-radius: 3px;
  }
  .mh-sim input[type=number] { width: 6em; }
  .mh-sim-result {
    margin-top: 0.75rem; padding: 0.4rem 0.75rem;
    border-left: 3px solid #2a7ae2;
  }
  .mh-sim-result strong { font-size: 1.2rem; color: #2a7ae2; }
  .mh-sim-result .theo { opacity: 0.7; font-size: 0.9rem; }
</style>

Behind one of three doors is a car. Behind the other two are goats. You pick a door. The host — who knows where the car is — opens one of the remaining doors to reveal a goat, then offers you the chance to switch. **Should you?**

The classical answer is yes: switching wins with probability 2/3, while staying wins only 1/3. Most people find this counterintuitive on first encounter. The game below lets you build intuition by playing; the simulator below that lets you watch the proportion converge.

## Play

<div class="mh-section" id="mh-game">
  <div class="mh-doors">
    <button class="mh-door" data-i="0">🚪</button>
    <button class="mh-door" data-i="1">🚪</button>
    <button class="mh-door" data-i="2">🚪</button>
  </div>
  <div class="mh-status">Pick a door.</div>
  <div class="mh-choice" hidden>
    <button id="mh-stay">Stay</button>
    <button id="mh-switch">Switch</button>
  </div>
  <button class="mh-reset" id="mh-reset" hidden>Play again</button>
  <div class="mh-tally">
    <span>Switching wins: <strong id="mh-sw-wins">0</strong> / <span id="mh-sw-tries">0</span></span>
    <span>Staying wins: <strong id="mh-st-wins">0</strong> / <span id="mh-st-tries">0</span></span>
  </div>
</div>

## Simulate

The classical 3-door setup generalizes: with $N$ doors, after the host opens $N-2$ goat-doors, switching wins with probability $(N-1)/N$ and staying wins with probability $1/N$. Try larger $N$ to see how decisively switching dominates.

<div class="mh-section mh-sim">
  <label>Strategy:
    <select id="mh-strategy">
      <option value="switch">Always switch</option>
      <option value="stay">Always stay</option>
    </select>
  </label>
  <label>Doors ($N$): <input id="mh-doors" type="number" min="3" max="1000" value="3"></label>
  <label>Rounds: <input id="mh-rounds" type="number" min="100" max="1000000" step="1000" value="10000"></label>
  <button class="mh-run" id="mh-run">Run</button>
  <div class="mh-sim-result">
    Empirical $\hat{P}(\mathrm{win}) = $ <strong id="mh-prob">—</strong>
    <span class="theo">vs theoretical <span id="mh-theo">—</span></span>
  </div>
</div>

## Why switching wins

Your initial pick has probability $1/N$ of being the car, so the other $N-1$ doors collectively share probability $(N-1)/N$. The host then eliminates $N-2$ of those goat-doors — but crucially, never the car-door. All of that $(N-1)/N$ probability mass collapses onto the single unopened door that isn't yours. Switching takes that mass; staying keeps your original $1/N$.

The host's knowledge is what makes the puzzle work. If the host opened a remaining door at random (sometimes revealing the car, ending the game), the conditional probabilities would be different.

<script>
(function() {
  // --- interactive 3-door game ---
  const G = { car: -1, pick: -1, opened: -1, phase: 'pick',
              swWins: 0, swTries: 0, stWins: 0, stTries: 0 };
  const $ = id => document.getElementById(id);
  const doors = document.querySelectorAll('#mh-game .mh-door');
  const status = document.querySelector('#mh-game .mh-status');
  const choice = document.querySelector('#mh-game .mh-choice');
  const reset = $('mh-reset');

  function newRound() {
    G.car = Math.floor(Math.random() * 3);
    G.pick = -1; G.opened = -1; G.phase = 'pick';
    doors.forEach(d => {
      d.disabled = false;
      d.classList.remove('picked', 'revealed');
      d.textContent = '🚪';
    });
    status.textContent = 'Pick a door.';
    choice.hidden = true;
    reset.hidden = true;
  }

  function onPick(i) {
    if (G.phase !== 'pick') return;
    G.pick = i;
    doors[i].classList.add('picked');
    const cands = [0, 1, 2].filter(d => d !== G.pick && d !== G.car);
    G.opened = cands[Math.floor(Math.random() * cands.length)];
    doors[G.opened].classList.add('revealed');
    doors[G.opened].textContent = '🐐';
    doors[G.opened].disabled = true;
    status.textContent = 'Door ' + (G.opened + 1) + ' has a goat. Stay with door ' + (G.pick + 1) + ', or switch?';
    G.phase = 'choose';
    choice.hidden = false;
  }

  function onDecide(strategy) {
    if (G.phase !== 'choose') return;
    let final = G.pick;
    if (strategy === 'switch') {
      final = [0, 1, 2].find(d => d !== G.pick && d !== G.opened);
    }
    doors.forEach((d, i) => {
      d.disabled = true;
      d.classList.add('revealed');
      d.textContent = (i === G.car) ? '🚗' : '🐐';
    });
    const won = (final === G.car);
    if (strategy === 'switch') { G.swTries++; if (won) G.swWins++; }
    else { G.stTries++; if (won) G.stWins++; }
    $('mh-sw-wins').textContent = G.swWins;
    $('mh-sw-tries').textContent = G.swTries;
    $('mh-st-wins').textContent = G.stWins;
    $('mh-st-tries').textContent = G.stTries;
    status.textContent = won
      ? 'You won the car! (chose to ' + strategy + ')'
      : 'Goat. (chose to ' + strategy + ')';
    choice.hidden = true;
    reset.hidden = false;
    G.phase = 'done';
  }

  doors.forEach((d, i) => d.addEventListener('click', () => onPick(i)));
  $('mh-stay').addEventListener('click', () => onDecide('stay'));
  $('mh-switch').addEventListener('click', () => onDecide('switch'));
  reset.addEventListener('click', newRound);
  newRound();

  // --- simulator (N doors) ---
  function simulate() {
    const strat = $('mh-strategy').value;
    const N = Math.max(3, Math.min(1000, parseInt($('mh-doors').value, 10) || 3));
    const R = Math.max(100, Math.min(1000000, parseInt($('mh-rounds').value, 10) || 10000));
    let wins = 0;
    // Equivalent reasoning: with host opening all but one of the non-picked doors
    // (and never the car), switching wins iff car !== initial pick.
    for (let r = 0; r < R; r++) {
      const car = Math.floor(Math.random() * N);
      const pick = Math.floor(Math.random() * N);
      const won = (strat === 'switch') ? (car !== pick) : (car === pick);
      if (won) wins++;
    }
    $('mh-prob').textContent = (wins / R).toFixed(4);
    const theo = (strat === 'switch') ? (N - 1) / N : 1 / N;
    $('mh-theo').textContent = theo.toFixed(4);
  }
  $('mh-run').addEventListener('click', simulate);
})();
</script>
