---
layout: archive
title: "Nonlinear Regression and Valley Centroids on a Bifurcating Ridge"
permalink: /demos/bimodal-fork-regression/
author_profile: false
---

{% include base_path %}
{% include jd-3d-head.html current="bimodal-fork-regression" %}

<div class="jd-prose" markdown="1">

For a general bivariate continuous distribution, neither the direct [regression function](/lecture-notes/double-expectation-theorem/#thm-regression-function) $\mathbb{E}(Y\mid X=x)$ nor the reverse regression function $\mathbb{E}(X\mid Y=y)$ needs to be linear, and a [conditional expectation](/lecture-notes/conditional-expectation-and-variance/#def-conditional-expectation) need not lie near a high-density ridge of the surface. Since $\mathbb{E}(Y\mid X=x)$ is the center of gravity of the renormalized conditional slice $f_{\sssig Y\mid X}(y\mid x)$, whenever a ridge splits into two symmetric branches, the conditional mean follows the low-density valley floor right between the two peaks.

Specifically, let $X\sim\mathcal{N}(0,\sigma_1^{2})$ and define a curved baseline $g(x)=a\sin(1.2x)+0.16(x^{2}-\sigma_1^{2})$ together with a smooth softplus half-separation $\delta(x)=b\ln\bigl(1+e^{1.8(x-0.15)}\bigr)$ ($b\geqslant 0$, $\tau>0$). Given $X=x$, let $Y$ follow the equal-weight two-branch normal mixture

$$
\begin{gathered}
f_{\sssig Y\mid X}(y\mid x)=\frac{1}{2}\phi\bigl(y;g(x)+\delta(x),\tau\bigr)+\frac{1}{2}\phi\bigl(y;g(x)-\delta(x),\tau\bigr)\\[0.32em]
f_{\sssig XY}(x,y)=\phi(x;0,\sigma_1)\,f_{\sssig Y\mid X}(y\mid x)
\end{gathered}
$$

Since the two Gaussian branches at $g(x)\pm\delta(x)$ carry equal probability $1/2$ at every $x$, their midpoint is always $g(x)$, yielding closed-form conditional moments along every vertical slice:

<div class="jd-math-desk" markdown="1">

$$
\mathbb{E}(Y\mid X=x)=g(x),\qquad \mathrm{Var}(Y\mid X=x)=\tau^{2}+\delta(x)^{2}
$$

</div>
<div class="jd-math-mob" markdown="1">

$$
\begin{gathered}
\mathbb{E}(Y\mid X=x)=g(x)\\[0.28em]
\mathrm{Var}(Y\mid X=x)=\tau^{2}+\delta(x)^{2}
\end{gathered}
$$

</div>

For $x<0$, $\delta(x)$ is small relative to $\tau$ and the surface forms a single curved ridge whose peak tracks $g(x)$. For $x>0$, $\delta(x)$ grows linearly and the ridge bifurcates into two distinct crests separated by a trough along $y=g(x)$. By the [double expectation theorem](/lecture-notes/double-expectation-theorem/#thm-double-expectation), averaging the slice centroids with weights $f_{\sssig X}(x)$ gives $\mathbb{E}(Y)=\mathbb{E}[g(X)]=a\cdot 0+0.16(\sigma_1^{2}-\sigma_1^{2})=0$.

**Parameters to explore below:**

- **Slice position $x_0$**: Toggle **Single ridge (x₀ = −1.15)** vs. **Valley slice (x₀ = +1.45)**, or sweep $x_0$ across $0$, to watch the crimson conditional slice split into two peaks whereas its centroid dot stays centered in the trough.
- **Wave amplitude $a$ and fork half-gap $b$**: Adjust $a$ to bend the baseline $g(x)$, or reduce $b$ toward $0$ to merge the two branches back into a single curved ridge.

</div>

<script>
window.JD_CONFIG = (function () {
  const SQRT_2PI = Math.sqrt(2 * Math.PI);
  function norm(u, m, s) {
    const z = (u - m) / s;
    return Math.exp(-0.5 * z * z) / (SQRT_2PI * s);
  }
  function baseG(x, a, s1) {
    return a * Math.sin(1.2 * x) + 0.16 * (x * x - s1 * s1);
  }
  function forkD(x, b) {
    const u = 1.8 * (x - 0.15);
    const sp = u > 20 ? u : Math.log(1 + Math.exp(u));
    return b * sp;
  }
  function condY(y, x, p) {
    const g = baseG(x, p.a, p.s1);
    const d = forkD(x, p.b);
    return 0.5 * norm(y, g + d, p.tau) + 0.5 * norm(y, g - d, p.tau);
  }
  function jointVal(x, y, p) {
    return norm(x, 0, p.s1) * condY(y, x, p);
  }

  return {
    domainL: 3.2,
    defaultMode: 'x',
    defaultCond3D: true,
    sliders: [
      { id: 'slice', label: 'Slice x₀', dynamicLabel: st => st.mode === 'x' ? 'Slice position x₀' : 'Slice position y₀', min: -2.50, max: 2.50, step: 0.05, def: 1.45, signed: true },
      { id: 'a', label: 'Wave amplitude a', min: -0.90, max: 0.90, step: 0.05, def: 0.55, signed: true },
      { id: 'b', label: 'Fork half-gap b', min: 0.00, max: 0.72, step: 0.03, def: 0.48, signed: false },
      { id: 's1', label: 'SD σ₁ of X', min: 0.55, max: 1.35, step: 0.05, def: 1.05, signed: false },
      { id: 'tau', label: 'Branch SD τ', min: 0.25, max: 0.75, step: 0.02, def: 0.36, signed: false }
    ],
    presets: [
      {
        id: 'valley',
        label: 'Valley slice (x₀ = +1.45)',
        title: 'Slice across the bifurcated right side where the conditional expectation lies in the valley between two peaks',
        apply: (st, setParam, setSliceMode, setFocus) => {
          setParam('b', 0.48);
          setParam('tau', 0.36);
          setParam('slice', 1.45);
          setSliceMode('x');
          setFocus('all');
        }
      },
      {
        id: 'unimodal',
        label: 'Single ridge (x₀ = −1.15)',
        title: 'Slice on the left side before the ridge bifurcates',
        apply: (st, setParam, setSliceMode) => {
          setParam('slice', -1.15);
          setSliceMode('x');
        }
      }
    ],
    readoutLabels: [
      'Slice area (side-wall marginal)',
      'Branch half-separation δ(x₀)',
      'Active slice centroid & SD',
      'Slice modality at active cut'
    ],
    evalJoint: (x, y, p) => jointVal(x, y, p),
    evalMargX: (x, p) => norm(x, 0, p.s1),
    evalMargY: (y, p) => {
      const nQ = 121;
      const xMax = Math.max(3.8, 4.6 * p.s1);
      const h = (2 * xMax) / nQ;
      let sum = 0;
      for (let k = 0; k < nQ; k++) sum += jointVal(-xMax + (k + 0.5) * h, y, p);
      return sum * h;
    },
    evalCond: (t, sv, mode, p) => mode === 'x' ? condY(t, sv, p) : null,
    evalDirect: (x, p) => {
      const g = baseG(x, p.a, p.s1);
      const d = forkD(x, p.b);
      return { mean: g, sd: Math.sqrt(p.tau * p.tau + d * d) };
    },
    evalReverse: (y, p) => {
      const nQ = 121;
      const xMax = Math.max(3.8, 4.6 * p.s1);
      const h = (2 * xMax) / nQ;
      let s0 = 0, s1 = 0, s2 = 0;
      for (let k = 0; k < nQ; k++) {
        const xq = -xMax + (k + 0.5) * h;
        const w = jointVal(xq, y, p);
        s0 += w; s1 += xq * w; s2 += xq * xq * w;
      }
      const fy = s0 * h;
      if (fy < 1e-6) return { mean: null, sd: null, fy };
      const mean = (s1 * h) / fy;
      return { mean, sd: Math.sqrt(Math.max(1e-9, (s2 * h) / fy - mean * mean)), fy };
    },
    formatReadouts: (sc, st, fmt) => {
      const p = st.params;
      const sv = fmt(p.slice, 2, true);
      const area = sc.sliceArea;
      const areaStr = area > 0 && area < 1e-3 ? area.toExponential(2) : area.toFixed(4);
      const mSym = st.mode === 'x' ? `f_X(${sv})` : `f_Y(${sv})`;
      const cSym = st.mode === 'x' ? `E(Y | X = ${sv})` : `E(X | Y = ${sv})`;
      if (st.mode === 'x') {
        const d = forkD(p.slice, p.b);
        const bimodal = d > p.tau;
        return [
          `${mSym} = ${areaStr}`,
          `δ(${sv}) = ${d.toFixed(3)} vs. τ = ${p.tau.toFixed(2)}`,
          `${cSym} = ${fmt(sc.condMean, 3, true)} · SD = ${sc.condSd.toFixed(3)}`,
          bimodal ? 'Bimodal (δ > τ): mean sits in valley trough' : 'Unimodal (δ ≤ τ): single merged crest'
        ];
      }
      const mult = area > 1e-6 ? 1 / area : 0;
      const multStr = !sc.hasValidCond ? 'Negligible slice mass' : (mult >= 1000 ? `1 / ${mSym} = ×${mult.toExponential(1)}` : `1 / ${mSym} = ×${mult.toFixed(2)}`);
      const regDesc = (Math.abs(p.a) < 1e-4 && p.b < 1e-4)
        ? 'Quadratic E(Y | X = x), symmetric E(X | Y = y) = 0'
        : 'Both E(Y | X = x) and E(X | Y = y) are nonlinear';
      return [
        `${mSym} = ${areaStr}`,
        multStr,
        sc.condMean !== null && sc.hasValidCond ? `${cSym} ≒ ${fmt(sc.condMean, 3, true)} · SD = ${sc.condSd.toFixed(3)}` : 'Negligible slice density',
        regDesc
      ];
    }
  };
})();
</script>

{% include jd-3d-workbench.html %}
