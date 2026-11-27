---
layout: archive
title: "Skewed Conditional Slices: Conditional Expectation as Centroid, Not Peak"
permalink: /demos/skewed-slice-centroid/
author_profile: false
---

{% include base_path %}
{% include jd-3d-head.html current="skewed-slice-centroid" %}

<div class="jd-prose" markdown="1">

Given $X=x_0$, the [conditional expectation](/lecture-notes/conditional-expectation-and-variance/#def-conditional-expectation) $\mathbb{E}(Y\mid X=x_0)=\int_{-\infty}^{\infty} y\,f_{\sssig Y\mid X}(y\mid x_0)\,dy$ is the **center of gravity** (horizontal balance point) of the renormalized conditional slice $f_{\sssig Y\mid X}(\,\cdot\mid x_0)$, not the projection of its highest peak (conditional [mode](/lecture-notes/mode/#def-mode)). When a unimodal conditional slice is skewed rather than symmetric around its peak, the mode and the conditional expectation need not coincide.

To see the distinction directly on a unimodal surface, let $X\sim\mathcal{N}(0,\sigma_1^{2})$ and let $Y\mid(X=x)$ follow a right-skewed shifted [gamma distribution](/lecture-notes/gamma-distribution/#def-gamma-distribution) of shape $\alpha=2$ and scale $\theta(x)=\theta_0+\gamma\ln\bigl(1+e^{1.4x}\bigr)$ ($\theta_0>0$, $\gamma\geqslant 0$), positioned so that the slice peak lies on the straight line $y_{\sssig\mathrm{mode}}(x)=\beta x$. Thus $f_{\sssig Y\mid X}(y\mid x)=0$ for $y<\beta x-\theta(x)$, whereas for $y\geqslant\beta x-\theta(x)$ the conditional pdf is

$$
f_{\sssig Y\mid X}(y\mid x)=\frac{y-\beta x+\theta(x)}{\theta(x)^{2}}\exp\!\left(-\frac{y-\beta x+\theta(x)}{\theta(x)}\right)
$$

Since a $\mathrm{Gamma}(2,\theta)$ variable has mode $\theta$, mean $2\theta$, and variance $2\theta^{2}$, shifting its origin to $\beta x-\theta(x)$ places the slice peak and the direct [regression function](/lecture-notes/double-expectation-theorem/#thm-regression-function) on two distinct curves:

<div class="jd-math-desk" markdown="1">

$$
\begin{gathered}
y_{\sssig\mathrm{mode}}(x)=\beta x,\qquad \mathbb{E}(Y\mid X=x)=\beta x+\theta(x)\\[0.32em]
\mathrm{Var}(Y\mid X=x)=2\,\theta(x)^{2}
\end{gathered}
$$

</div>
<div class="jd-math-mob" markdown="1">

$$
\begin{gathered}
y_{\sssig\mathrm{mode}}(x)=\beta x\\[0.28em]
\mathbb{E}(Y\mid X=x)=\beta x+\theta(x)\\[0.28em]
\mathrm{Var}(Y\mid X=x)=2\,\theta(x)^{2}
\end{gathered}
$$

</div>

At every vertical slice $X=x_0$, the heavy upper tail pulls the center of gravity $\mathbb{E}(Y\mid X=x_0)$ by $+\theta(x_0)$ to the right of the peak, where the slice height equals $(2/e^{2})/(1/e)=2/e\fallingdotseq 0.7358$ ($73.58\%$) of the peak height.

**Parameters and two key experiments below:**

- **Peak vs. centroid on a single slice**: Select **Peak vs. centroid** in the `Focus` bar (or click **Parallel shift (γ = 0)**) to compare the hollow teal marker at the true slice peak $y_{\sssig\mathrm{mode}}(x_0)=\beta x_0$ against the filled crimson fulcrum at the center of gravity $\mathbb{E}(Y\mid X=x_0)=\beta x_0+\theta(x_0)$ on the right-tail flank.
- **Straight peak ridge with a curved regression function**: Click **Straight peak, curved E(Y &#124; X = x)** ($\beta=0, \gamma=0.38$). Every vertical slice attains its peak along the straight line $y=0$, yet as $\theta(x)$ stretches the right tail for larger $x$, the regression curve $\mathbb{E}(Y\mid X=x)=\theta(x)$ bends upward across the base plane.

</div>

<script>
window.JD_CONFIG = (function () {
  const SQRT_2PI = Math.sqrt(2 * Math.PI);
  const SQRT_2 = Math.sqrt(2);
  const GOLDEN_INV = 0.5 * (Math.sqrt(5) - 1);

  function norm(u, m, s) {
    const z = (u - m) / s;
    return Math.exp(-0.5 * z * z) / (SQRT_2PI * s);
  }
  function thetaAt(x, p) {
    const u = 1.4 * x;
    const sp = u > 20 ? u : Math.log(1 + Math.exp(u));
    return p.theta0 + p.gamma * sp;
  }
  function condGamma2(y, x, p) {
    const th = thetaAt(x, p);
    const v = y - p.beta * x + th;
    if (v <= 0) return 0;
    return (v / (th * th)) * Math.exp(-v / th);
  }
  function jointVal(x, y, p) {
    return norm(x, 0, p.s1) * condGamma2(y, x, p);
  }
  function findHorizMode(y0, p) {
    const xLim = Math.max(4.6, 5.5 * p.s1);
    const nScan = 360;
    const h = (2 * xLim) / nScan;
    let bestK = 0, bestZ = -1;
    for (let k = 0; k <= nScan; k++) {
      const xq = -xLim + k * h;
      const z = jointVal(xq, y0, p);
      if (z > bestZ) { bestZ = z; bestK = k; }
    }
    if (bestZ < 1e-8) return null;
    let a = Math.max(-xLim, -xLim + (bestK - 1) * h);
    let b = Math.min(xLim, -xLim + (bestK + 1) * h);
    let c = b - GOLDEN_INV * (b - a);
    let d = a + GOLDEN_INV * (b - a);
    let fc = jointVal(c, y0, p), fd = jointVal(d, y0, p);
    for (let it = 0; it < 18; it++) {
      if (fc > fd) {
        b = d; d = c; fd = fc;
        c = b - GOLDEN_INV * (b - a);
        fc = jointVal(c, y0, p);
      } else {
        a = c; c = d; fc = fd;
        d = a + GOLDEN_INV * (b - a);
        fd = jointVal(d, y0, p);
      }
    }
    const xm = 0.5 * (a + b);
    const zm = jointVal(xm, y0, p);
    return zm > 1e-8 ? { x: xm, rawZ: zm } : null;
  }

  return {
    domainL: 3.4,
    defaultMode: 'x',
    defaultCond3D: true,
    hasRidge: true,
    ridgeFocusLabel: 'Peak vs. centroid',
    ridgeLegendLabel: st => st.mode === 'x'
      ? 'Slice peak (mode) locus y_mode(x)'
      : 'Slice peak (mode) locus x_mode(y)',
    sliders: [
      { id: 'slice', label: 'Slice x₀', dynamicLabel: st => st.mode === 'x' ? 'Slice position x₀' : 'Slice position y₀', min: -2.50, max: 2.50, step: 0.05, def: 0.60, signed: true },
      { id: 'theta0', label: 'Base skew scale θ₀', min: 0.32, max: 0.90, step: 0.02, def: 0.62, signed: false },
      { id: 'gamma', label: 'Tail growth γ', min: 0.00, max: 0.50, step: 0.02, def: 0.00, signed: false },
      { id: 'beta', label: 'Peak-line slope β', min: -0.80, max: 0.80, step: 0.05, def: 0.35, signed: true },
      { id: 's1', label: 'SD σ₁ of X', min: 0.60, max: 1.30, step: 0.05, def: 0.95, signed: false }
    ],
    presets: [
      {
        id: 'const-skew',
        label: 'Parallel shift (γ = 0)',
        title: 'Constant skew scale θ₀ = 0.62 so E(Y | X = x) = βx + θ₀ runs parallel in the right tail of the peak line βx',
        apply: (st, setParam, setSliceMode, setFocus, setCond3D) => {
          setParam('beta', 0.35);
          setParam('theta0', 0.62);
          setParam('gamma', 0.00);
          setParam('s1', 0.95);
          setParam('slice', 0.60);
          setSliceMode('x');
          setFocus('ridge');
          if (setCond3D) setCond3D(true);
        }
      },
      {
        id: 'curved-mean',
        label: 'Straight peak, curved E(Y | X = x)',
        title: 'Set β = 0 and γ = 0.38 so slice peaks stay on y = 0 whereas longer right tails bend E(Y | X = x) upward',
        apply: (st, setParam, setSliceMode, setFocus, setCond3D) => {
          setParam('beta', 0.00);
          setParam('theta0', 0.36);
          setParam('gamma', 0.38);
          setParam('s1', 1.00);
          setParam('slice', 1.10);
          setSliceMode('x');
          setFocus('ridge');
          if (setCond3D) setCond3D(true);
        }
      }
    ],
    readoutLabels: [
      'Slice peak (mode) on cut',
      'Slice centroid (conditional mean)',
      'Centroid shift (mean − mode)',
      'Slice area & conditional SD'
    ],
    evalJoint: (x, y, p) => jointVal(x, y, p),
    evalMargX: (x, p) => norm(x, 0, p.s1),
    evalMargY: (y, p) => {
      const nQ = 301;
      const xMax = Math.max(4.6, 5.5 * p.s1);
      const h = (2 * xMax) / nQ;
      let sum = 0;
      for (let k = 0; k < nQ; k++) sum += jointVal(-xMax + (k + 0.5) * h, y, p);
      return sum * h;
    },
    evalCond: (t, sv, mode, p) => mode === 'x' ? condGamma2(t, sv, p) : null,
    evalDirect: (x, p) => {
      const th = thetaAt(x, p);
      return { mean: p.beta * x + th, sd: SQRT_2 * th };
    },
    evalReverse: (y, p) => {
      const nQ = 301;
      const xMax = Math.max(4.6, 5.5 * p.s1);
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
    evalModeCurvePt: (u, mode, p) => {
      if (mode === 'x') return { x: u, y: p.beta * u };
      const hm = findHorizMode(u, p);
      return hm ? { x: hm.x, y: u } : null;
    },
    evalSliceKnots: (sv, mode, p) => {
      if (mode === 'x') {
        const th = thetaAt(sv, p);
        const ym = p.beta * sv;
        const yMin = ym - th;
        return [yMin - 1e-4, yMin, ym];
      }
      const hm = findHorizMode(sv, p);
      return hm ? [hm.x] : null;
    },
    evalSliceModePoint: (sv, mode, p, st, L) => {
      if (mode === 'x') {
        const ym = p.beta * sv;
        return { x: sv, y: ym, t: ym, rawZ: jointVal(sv, ym, p), inPlot: Math.abs(ym) <= L };
      }
      const hm = findHorizMode(sv, p);
      if (!hm) return null;
      return { x: hm.x, y: sv, t: hm.x, rawZ: hm.rawZ, inPlot: Math.abs(hm.x) <= L };
    },
    formatReadouts: (sc, st, fmt) => {
      const p = st.params;
      const sv = fmt(p.slice, 2, true);
      const areaStr = sc.sliceArea > 0 && sc.sliceArea < 1e-3 ? sc.sliceArea.toExponential(2) : sc.sliceArea.toFixed(4);
      if (st.mode === 'x') {
        const th = thetaAt(p.slice, p);
        const ym = p.beta * p.slice;
        const meanY = ym + th;
        const pkCond = 1 / (Math.E * th);
        const mnCond = (2 / (Math.E * Math.E)) / th;
        return [
          `y_mode(${sv}) = ${fmt(ym, 3, true)} (cond = ${pkCond.toFixed(3)})`,
          `E(Y | X = ${sv}) = ${fmt(meanY, 3, true)} (cond = ${mnCond.toFixed(3)})`,
          `+${th.toFixed(3)} into right tail (73.58% of peak)`,
          `f_X(${sv}) = ${areaStr} · SD = ${(SQRT_2 * th).toFixed(3)}`
        ];
      }
      const xm = sc.ridgeCross && sc.hasValidCond ? sc.ridgeCross.t : null;
      const gap = (xm !== null && sc.condMean !== null) ? sc.condMean - xm : null;
      return [
        xm !== null ? `x_mode(${sv}) ≒ ${fmt(xm, 3, true)}` : 'Outside support / negligible mass',
        sc.condMean !== null && sc.hasValidCond ? `E(X | Y = ${sv}) ≒ ${fmt(sc.condMean, 3, true)}` : 'Outside support / negligible mass',
        gap !== null ? `mean − mode ≒ ${fmt(gap, 3, true)}` : '–',
        `f_Y(${sv}) = ${areaStr} · SD = ${sc.condSd && sc.hasValidCond ? sc.condSd.toFixed(3) : '–'}`
      ];
    }
  };
})();
</script>

{% include jd-3d-workbench.html %}
