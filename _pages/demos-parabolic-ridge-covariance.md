---
layout: archive
title: "Parabolic Ridge: One-Way Mean Independence and Zero Covariance"
permalink: /demos/parabolic-ridge-covariance/
author_profile: false
---

{% include base_path %}
{% include jd-3d-head.html current="parabolic-ridge-covariance" %}

<div class="jd-prose" markdown="1">

[Mean independence](/lecture-notes/covariance/#note-mean-independence) is not a symmetric relation between $X$ and $Y$, and failure of mean independence in one direction still permits exact zero [covariance](/lecture-notes/covariance/#def-covariance). Let $X\sim\mathcal{N}(0,\sigma_1^{2})$ and let $Y$ follow a normal distribution centered along the centered parabola $g(x)=a(x^{2}-\sigma_1^{2})$ ($a>0$, $\tau>0$):

$$
\begin{gathered}
Y\mid(X=x)\sim\mathcal{N}\!\left(a(x^{2}-\sigma_1^{2}),\,\tau^{2}\right)\\[0.32em]
f_{\sssig XY}(x,y)=\phi(x;0,\sigma_1)\,\phi\!\left(y;\,a(x^{2}-\sigma_1^{2}),\,\tau\right)
\end{gathered}
$$

Here $\mathbb{E}(Y)=\mathbb{E}[a(X^{2}-\sigma_1^{2})]=0$. Since the direct [regression function](/lecture-notes/double-expectation-theorem/#thm-regression-function) $\mathbb{E}(Y\mid X=x)=a(x^{2}-\sigma_1^{2})$ varies quadratically with $x$, $Y$ is **not** mean-independent of $X$. On the other hand, $f_{\sssig XY}(-x,y)=f_{\sssig XY}(x,y)$ is an even function of $x$ for every fixed $y$. Slicing horizontally across the upper arms of the parabola ($y_0>\frac{\tau^{2}}{2a\sigma_1^{2}}-a\sigma_1^{2}$) produces a symmetric bimodal conditional density $f_{\sssig X\mid Y}(x\mid y_0)$ centered at $0$, and even symmetry guarantees $\mathbb{E}(X\mid Y=y)=0=\mathbb{E}(X)$ for all $y\in\mathbb{R}$.

Applying the [double expectation theorem](/lecture-notes/double-expectation-theorem/#thm-double-expectation) confirms that $(X,Y)$ has zero covariance despite the strong quadratic dependence:

$$
\operatorname{Cov}(X,Y)=\mathbb{E}\bigl[X\,\mathbb{E}(Y\mid X)\bigr]=a\,\mathbb{E}\bigl[X(X^{2}-\sigma_1^{2})\bigr]=0
$$

In the signed covariance-integrand panel below, the odd function $x\,a(x^{2}-\sigma_1^{2})\,f_{\sssig X}(x)$ forms equal and opposite lobes on $x<0$ and $x>0$ that cancel pairwise to zero.

**Parameters to explore below:**

- **Vertical vs. horizontal cuts**: Click **Vertical cut (x₀ = +1.25)** (under **Slice X = x₀**) to watch the unimodal conditional bell ride up and down the parabola, then click **Bimodal Y-cut (y₀ = +0.75)** (switching to **Slice Y = y₀**) to inspect a symmetric bimodal horizontal slice whose centroid stays fixed at $x=0$.
- **Curvature $a$ and slice standard deviation $\tau$**: Increasing $a$ bends the U-shaped ridge more steeply and increases the lobe heights in the covariance-integrand chart, where both $\mathbb{E}(X\mid Y=y)=0$ and $\operatorname{Cov}(X,Y)=0$ remain unchanged.

</div>

<script>
window.JD_CONFIG = (function () {
  const SQRT_2PI = Math.sqrt(2 * Math.PI);
  function norm(u, m, s) {
    const z = (u - m) / s;
    return Math.exp(-0.5 * z * z) / (SQRT_2PI * s);
  }
  function jointVal(x, y, p) {
    const muY = p.a * (x * x - p.s1 * p.s1);
    return norm(x, 0, p.s1) * norm(y, muY, p.tau);
  }

  return {
    domainL: 3.2,
    defaultMode: 'x',
    defaultCond3D: true,
    hasStatusStrip: true,
    hasCovPanel: true,
    sliders: [
      { id: 'slice', label: 'Slice x₀', dynamicLabel: st => st.mode === 'x' ? 'Slice position x₀' : 'Slice position y₀', min: -2.50, max: 2.50, step: 0.05, def: 1.25, signed: true },
      { id: 'a', label: 'Curvature a', min: 0.25, max: 1.15, step: 0.05, def: 0.65, signed: false },
      { id: 's1', label: 'SD σ₁ of X', min: 0.55, max: 1.25, step: 0.05, def: 0.90, signed: false },
      { id: 'tau', label: 'Cond. SD τ (Y | X = x)', min: 0.30, max: 0.90, step: 0.03, def: 0.48, signed: false }
    ],
    presets: [
      {
        id: 'vert',
        label: 'Vertical cut (x₀ = +1.25)',
        apply: (st, setParam, setSliceMode) => {
          setSliceMode('x');
          setParam('slice', 1.25);
        }
      },
      {
        id: 'horiz',
        label: 'Bimodal Y-cut (y₀ = +0.75)',
        apply: (st, setParam, setSliceMode) => {
          setParam('a', 0.65);
          setParam('s1', 0.90);
          setParam('tau', 0.48);
          setSliceMode('y');
          setParam('slice', 0.75);
        }
      }
    ],
    readoutLabels: [
      'Slice area (side-wall marginal)',
      'Active conditional mean',
      'Conditional vs. marginal SD',
      'Exact covariance Cov(X, Y)'
    ],
    evalJoint: (x, y, p) => jointVal(x, y, p),
    evalMargX: (x, p) => norm(x, 0, p.s1),
    evalMargY: (y, p) => {
      const nQ = 141;
      const xMax = Math.max(4.0, 5.0 * p.s1);
      const h = (2 * xMax) / nQ;
      let sum = 0;
      for (let k = 0; k < nQ; k++) sum += jointVal(-xMax + (k + 0.5) * h, y, p);
      return sum * h;
    },
    evalCond: (t, sv, mode, p) => mode === 'x' ? norm(t, p.a * (sv * sv - p.s1 * p.s1), p.tau) : null,
    evalDirect: (x, p) => ({ mean: p.a * (x * x - p.s1 * p.s1), sd: p.tau }),
    evalReverse: (y, p) => {
      const nQ = 141;
      const xMax = Math.max(4.0, 5.0 * p.s1);
      const h = (2 * xMax) / nQ;
      let s0 = 0, s2 = 0;
      for (let k = 0; k < nQ; k++) {
        const xq = -xMax + (k + 0.5) * h;
        const w = jointVal(xq, y, p);
        s0 += w; s2 += xq * xq * w;
      }
      const fy = s0 * h;
      return { mean: 0, sd: fy > 1e-8 ? Math.sqrt(Math.max(1e-9, (s2 * h) / fy)) : null };
    },
    evalBadges: () => ({
      indep: { holds: false, text: 'Fails' },
      my: { holds: false, text: 'Fails (≠ 0)' },
      mx: { holds: true, text: 'Holds (= 0)' },
      cov: { holds: true, text: 'Holds (= 0)' }
    }),
    formatCovCaption: (sc, st) => st.mode === 'x'
      ? 'Odd integrand x · a(x² − σ₁²) · f_X(x): left and right lobes have equal area and opposite signs, canceling to 0.'
      : 'Along Y = y, E(X | Y = y) = 0 identically, so the reverse covariance integrand y · E(X | Y = y) · f_Y(y) vanishes everywhere.',
    formatReadouts: (sc, st, fmt) => {
      const p = st.params;
      const sv = fmt(p.slice, 2, true);
      const margSdY = Math.sqrt(2 * p.a * p.a * Math.pow(p.s1, 4) + p.tau * p.tau);
      const margSd = st.mode === 'x' ? margSdY : p.s1;
      const mSym = st.mode === 'x' ? `f_X(${sv})` : `f_Y(${sv})`;
      const cSym = st.mode === 'x' ? `E(Y | X = ${sv})` : `E(X | Y = ${sv})`;
      const areaStr = sc.sliceArea > 0 && sc.sliceArea < 1e-3 ? sc.sliceArea.toExponential(2) : sc.sliceArea.toFixed(4);
      const meanNote = st.mode === 'x' ? 'vs. E(Y) = 0' : '= E(X)';
      return [
        `${mSym} = ${areaStr}`,
        sc.hasValidCond && sc.condMean !== null ? `${cSym} = ${fmt(sc.condMean, 3, true)} (${meanNote})` : `${cSym} = 0.000 (tail slice)`,
        sc.hasValidCond && sc.condSd !== null ? `slice SD = ${sc.condSd.toFixed(3)} · marg SD = ${margSd.toFixed(3)}` : `marg SD = ${margSd.toFixed(3)}`,
        'Cov(X, Y) = 0.0000 (odd lobes cancel)'
      ];
    }
  };
})();
</script>

{% include jd-3d-workbench.html %}
