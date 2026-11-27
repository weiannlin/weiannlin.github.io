---
layout: archive
title: "Conditional Slices, Side-Wall Marginals, and Area Renormalization"
permalink: /demos/slice-renormalization/
author_profile: false
---

{% include base_path %}
{% include jd-3d-head.html current="slice-renormalization" %}

<div class="jd-prose" markdown="1">

Cutting a continuous [joint pdf](/lecture-notes/joint-probability-density-functions/#def-joint-pdf) surface $z=f_{\sssig XY}(x,y)$ with a vertical plane $X=x_0$ produces an unnormalized cross-sectional profile $y\mapsto f_{\sssig XY}(x_0,y)$. Although that raw curve already captures the exact relative likelihood of different $y$ values along the cut, the area underneath it is not $1$; by definition of the [marginal pdf](/lecture-notes/marginal-probability-density-functions/#def-marginal-pdf), that cross-sectional area equals the ordinate $f_{\sssig X}(x_0)$ projected onto the back wall:

$$
f_{\sssig X}(x_0)=\int_{-\infty}^{\infty} f_{\sssig XY}(x_0,y)\,dy
$$

Dividing the raw profile by its cross-sectional area rescales every ordinate by the same factor $1/f_{\sssig X}(x_0)$ to form the [conditional pdf](/lecture-notes/conditional-distributions/#def-conditional-pdf) of unit area:

$$
f_{\sssig Y\mid X}(y\mid x_0)=\frac{f_{\sssig XY}(x_0,y)}{f_{\sssig X}(x_0)}
$$

To examine this rescaling in a clean parametric family before introducing covariance or correlation, let $X\sim\mathcal{N}(0,\sigma_1^{2})$ and $Y\mid(X=x)\sim\mathcal{N}(\beta x,\tau^{2})$ ($\sigma_1,\tau>0$, $\beta\in\mathbb{R}$), which gives the joint pdf and side-wall marginals

<div class="jd-math-desk" markdown="1">

$$
\begin{gathered}
f_{\sssig XY}(x,y)=\frac{1}{2\pi\sigma_1\tau}\exp\!\left(-\frac{x^{2}}{2\sigma_1^{2}}-\frac{(y-\beta x)^{2}}{2\tau^{2}}\right)\\[0.32em]
f_{\sssig X}(x)=\phi(x;0,\sigma_1),\qquad f_{\sssig Y}(y)=\phi\!\left(y;\,0,\sqrt{\beta^{2}\sigma_1^{2}+\tau^{2}}\right)
\end{gathered}
$$

</div>
<div class="jd-math-mob" markdown="1">

$$
\begin{gathered}
f_{\sssig XY}(x,y)=\frac{1}{2\pi\sigma_1\tau}\exp\!\left(-\frac{x^{2}}{2\sigma_1^{2}}-\frac{(y-\beta x)^{2}}{2\tau^{2}}\right)\\[0.32em]
f_{\sssig X}(x)=\phi(x;0,\sigma_1)\\[0.28em]
f_{\sssig Y}(y)=\phi\!\left(y;\,0,\sqrt{\beta^{2}\sigma_1^{2}+\tau^{2}}\right)
\end{gathered}
$$

</div>

where $\phi(u;\mu,s)=\frac{1}{\sqrt{2\pi}s}\exp\bigl(-(u-\mu)^{2}/(2s^{2})\bigr)$. Here $\beta$ tilts the orientation of the bell across the $(x,y)$ plane without requiring covariance or correlation notation.

**Parameters and three geometric regimes to inspect below:**

- **Coupling parameter $\beta$ and independence ($\beta=0$)**: Click **β = 0 (indep.)** and sweep $x_0$. The ochre raw slice rises and falls with $f_{\sssig X}(x_0)$, yet with **3D conditional pdf** checked, the crimson conditional arch maintains constant height and matches the side-wall curve $f_{\sssig Y}(y)$ at every slice, illustrating [stochastic independence](/lecture-notes/independent-random-variables/#def-indep-r-v).
- **Upward stretching ($f_{\sssig X}(x_0)<1$) vs. downward scaling ($f_{\sssig X}(x_0)>1$)**: In the tails where $f_{\sssig X}(x_0)<1$, dividing by $f_{\sssig X}(x_0)$ stretches the conditional pdf upward above the raw slice. Click **f &gt; 1 shrink** ($\sigma_1=0.28, x_0=0$) so $f_{\sssig X}(0)\fallingdotseq 1.425>1$; since the raw slice encloses area larger than $1$, renormalization scales the crimson conditional arch **downward** beneath the raw slice.
- **Spotlight focus (`Focus` bar)**: Select **Slice &amp; scaling** or **Marginal pdfs** to dim secondary elements into a faint spatial backdrop without hiding them; continue to [Lab 2](/demos/skewed-slice-centroid/) to see how the center of gravity of each normalized slice defines conditional expectation.

</div>

<script>
window.JD_CONFIG = (function () {
  const SQRT_2PI = Math.sqrt(2 * Math.PI);
  function norm(u, m, s) {
    const z = (u - m) / s;
    return Math.exp(-0.5 * z * z) / (SQRT_2PI * s);
  }
  return {
    domainL: 3.2,
    defaultMode: 'x',
    defaultCond3D: true,
    hideRegression: true,
    sliders: [
      { id: 'slice', label: 'Slice x₀', dynamicLabel: st => st.mode === 'x' ? 'Slice position x₀' : 'Slice position y₀', min: -2.50, max: 2.50, step: 0.05, def: 1.25, signed: true },
      { id: 'beta', label: 'Coupling β', min: -1.20, max: 1.20, step: 0.05, def: 0.75, signed: true },
      { id: 's1', label: 'SD σ₁ of X', min: 0.28, max: 1.40, step: 0.02, def: 0.95, signed: false },
      { id: 'tau', label: 'Cond. SD τ (Y | X = x)', min: 0.35, max: 1.15, step: 0.05, def: 0.60, signed: false }
    ],
    presets: [
      {
        id: 'indep',
        label: 'β = 0 (indep.)',
        title: 'Set β = 0 so conditional slices match the side-wall marginal pdf everywhere',
        apply: (st, setParam, setSliceMode, setFocus, setCond3D) => {
          setParam('beta', 0.00);
          setParam('s1', 0.95);
          setParam('tau', 0.70);
          setParam('slice', 1.20);
          setSliceMode('x');
          setFocus('all');
          if (setCond3D) setCond3D(true);
        }
      },
      {
        id: 'shrink',
        label: 'f > 1 shrink',
        title: 'Concentrate X (σ₁ = 0.28) at x₀ = 0 so the marginal ordinate (≒ 1.425 > 1) scales the conditional pdf downward',
        apply: (st, setParam, setSliceMode, setFocus, setCond3D) => {
          setParam('beta', 0.70);
          setParam('s1', 0.28);
          setParam('tau', 0.60);
          setParam('slice', 0.00);
          setSliceMode('x');
          setFocus('slice');
          if (setCond3D) setCond3D(true);
        }
      }
    ],
    readoutLabels: [
      'Slice area (side-wall marginal)',
      'Renormalization factor',
      'Raw peak vs. conditional peak',
      'Comparison with marginal pdf'
    ],
    evalJoint: (x, y, p) => norm(x, 0, p.s1) * norm(y, p.beta * x, p.tau),
    evalMargX: (x, p) => norm(x, 0, p.s1),
    evalMargY: (y, p) => norm(y, 0, Math.sqrt(p.beta * p.beta * p.s1 * p.s1 + p.tau * p.tau)),
    evalCond: (t, sv, mode, p) => {
      if (mode === 'x') return norm(t, p.beta * sv, p.tau);
      const vy = p.beta * p.beta * p.s1 * p.s1 + p.tau * p.tau;
      const muX = ((p.beta * p.s1 * p.s1) / vy) * sv;
      const sdX = Math.sqrt((p.s1 * p.s1 * p.tau * p.tau) / vy);
      return norm(t, muX, sdX);
    },
    formatReadouts: (sc, st, fmt) => {
      const p = st.params;
      const sv = fmt(p.slice, 2, true);
      const area = sc.sliceArea;
      const areaStr = area < 1e-3 ? area.toExponential(2) : area.toFixed(4);
      const mult = 1 / Math.max(1e-30, area);
      const multStr = mult >= 1000 ? `×${mult.toExponential(1)}` : `×${mult.toFixed(3)}`;
      const dirTxt = mult > 1.02 ? 'stretch up' : (mult < 0.98 ? 'scale down' : 'unit scale');
      const mSym = st.mode === 'x' ? `f_X(${sv})` : `f_Y(${sv})`;
      const margSd = st.mode === 'x' ? Math.sqrt(p.beta * p.beta * p.s1 * p.s1 + p.tau * p.tau) : p.s1;
      const condSd = st.mode === 'x' ? p.tau : Math.sqrt((p.s1 * p.s1 * p.tau * p.tau) / (p.beta * p.beta * p.s1 * p.s1 + p.tau * p.tau));
      const condPeak = 1 / (SQRT_2PI * condSd);
      const rawPeak = area * condPeak;
      const rawStr = rawPeak > 0 && rawPeak < 1e-3 ? rawPeak.toExponential(2) : rawPeak.toFixed(3);
      const indep = Math.abs(p.beta) < 1e-6;
      return [
        `${mSym} = ${areaStr}`,
        `1 / ${mSym} = ${multStr} (${dirTxt})`,
        `raw ${rawStr} → cond ${condPeak.toFixed(3)}`,
        indep ? `Independent (cond pdf ≡ marginal, SD = ${margSd.toFixed(3)})` : `Marginal SD = ${margSd.toFixed(3)} vs. slice SD = ${condSd.toFixed(3)}`
      ];
    }
  };
})();
</script>

{% include jd-3d-workbench.html %}
