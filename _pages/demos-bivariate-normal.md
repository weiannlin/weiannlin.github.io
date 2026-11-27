---
layout: archive
title: "Bivariate Normal Surface, Conditional Slices, and Regression Lines"
permalink: /demos/bivariate-normal/
author_profile: false
---

{% include base_path %}
{% include jd-3d-head.html current="bivariate-normal" %}

<div class="jd-prose" markdown="1">

In the [bivariate normal distribution](/lecture-notes/bivariate-normal-distribution/#def-bivariate-normal) centered at $(\mu_1,\mu_2)=(0,0)$ with standard deviations $\sigma_1,\sigma_2>0$ and [correlation](/lecture-notes/correlation-coefficient/#def-corr) $\rho\in(-1,1)$, the [joint pdf](/lecture-notes/joint-probability-density-functions/#def-joint-pdf) is

$$
f_{\sssig XY}(x,y)=\frac{1}{2\pi\sigma_1\sigma_2\sqrt{1-\rho^{2}}}\exp\!\left(-\frac{1}{2}Q(x,y)\right)
$$

where the quadratic form in the exponent is

$$
Q(x,y)=\frac{1}{1-\rho^{2}}\left[\left(\frac{x}{\sigma_1}\right)^{2}-2\rho\left(\frac{x}{\sigma_1}\right)\left(\frac{y}{\sigma_2}\right)+\left(\frac{y}{\sigma_2}\right)^{2}\right]
$$

The side-wall [marginal pdfs](/lecture-notes/marginal-probability-density-functions/#def-marginal-pdf) are $f_{\sssig X}(x)=\phi(x;0,\sigma_1)$ and $f_{\sssig Y}(y)=\phi(y;0,\sigma_2)$. Slicing the surface along $X=x_0$ and dividing by $f_{\sssig X}(x_0)$ produces a homoscedastic normal [conditional pdf](/lecture-notes/conditional-distributions/#def-conditional-pdf):

$$
Y\mid(X=x_0)\sim\mathcal{N}\!\left(\rho\frac{\sigma_2}{\sigma_1}x_0,\ \sigma_2^{2}(1-\rho^{2})\right)
$$

Its mean traces the [population linear regression equation](/lecture-notes/population-linear-regression/#thm-popu-reg) $\mathbb{E}(Y\mid X=x)=\rho\frac{\sigma_2}{\sigma_1}x$. When $0<\lvert\rho\rvert<1$, this direct regression line is flatter than the major axis (geometric ridge) of the [equal-density ellipses](/lecture-notes/bivariate-normal-distribution/#fig-bivariate-normal-contours) $Q(x,y)=c$. Along a fixed vertical cut $X=x_0$, the slice attains its peak at the ellipse whose tangent at $x_0$ is vertical ($\partial Q/\partial y=0$), whereas the major axis crosses the downhill flank of the slice at a larger $\lvert y\rvert$, producing Galton’s regression toward the mean.

**Parameters and spotlight modes to explore below:**

- **Ridge vs. slice peak**: Click **Spot ridge vs. peak** (or select **Ellipse ridge** in the `Focus` bar) to dim secondary layers and contrast the crimson regression line (filled peak dot) directly against the teal dashed ellipse major axis (hollow flank dot) in 3D, 2D contours, and the 1D slice.
- **Correlation $\rho=0$**: Click **ρ = 0 (indep.)** and sweep $x_0$. The 3D crimson conditional arch stays identical in height and width to the side-wall marginal $f_{\sssig Y}(y)$ at every slice.

</div>

<script>
window.JD_CONFIG = (function () {
  const TWO_PI = 2 * Math.PI;
  const SQRT_2PI = Math.sqrt(TWO_PI);
  function norm(u, m, s) {
    const z = (u - m) / s;
    return Math.exp(-0.5 * z * z) / (SQRT_2PI * s);
  }
  function bvnJoint(x, y, p) {
    const omr2 = Math.max(1e-6, 1 - p.rho * p.rho);
    const zx = x / p.s1, zy = y / p.s2;
    const q = (zx * zx - 2 * p.rho * zx * zy + zy * zy) / omr2;
    return Math.exp(-0.5 * q) / (TWO_PI * p.s1 * p.s2 * Math.sqrt(omr2));
  }
  function ridgeSlopeObj(p) {
    const { rho, s1, s2 } = p;
    if (Math.abs(rho) < 1e-5) {
      if (Math.abs(s1 - s2) < 1e-5) return null;
      return s2 > s1 ? { vertical: true, m: Infinity } : { vertical: false, m: 0 };
    }
    const diff = s2 * s2 - s1 * s1;
    const cov = rho * s1 * s2;
    const disc = Math.sqrt(diff * diff + 4 * cov * cov);
    return { vertical: false, m: (diff + disc) / (2 * cov) };
  }

  return {
    domainL: 3.2,
    defaultMode: 'x',
    defaultCond3D: true,
    hasRidge: true,
    sliders: [
      { id: 'slice', label: 'Slice x₀', dynamicLabel: st => st.mode === 'x' ? 'Slice position x₀' : 'Slice position y₀', min: -2.50, max: 2.50, step: 0.05, def: 1.40, signed: true },
      { id: 'rho', label: 'Correlation ρ', min: -0.90, max: 0.90, step: 0.01, def: 0.75, signed: true },
      { id: 's1', label: 'SD σ₁ of X', min: 0.45, max: 1.45, step: 0.05, def: 1.00, signed: false },
      { id: 's2', label: 'SD σ₂ of Y', min: 0.45, max: 1.45, step: 0.05, def: 1.00, signed: false }
    ],
    presets: [
      {
        id: 'ridge-focus',
        label: 'Spot ridge vs. peak',
        title: 'Highlight the gap between the ellipse major axis and the conditional slice peak at ρ = +0.75',
        apply: (st, setParam, setSliceMode, setFocus, setCond3D) => {
          setParam('rho', 0.75);
          setParam('s1', 1.00);
          setParam('s2', 1.00);
          setParam('slice', 1.40);
          setSliceMode('x');
          setFocus('ridge');
          if (setCond3D) setCond3D(true);
        }
      },
      {
        id: 'indep',
        label: 'ρ = 0 (indep.)',
        title: 'Set ρ = 0 so conditional slices match the side-wall marginal pdf everywhere',
        apply: (st, setParam, setSliceMode, setFocus, setCond3D) => {
          setParam('rho', 0.00);
          setParam('slice', 1.30);
          setSliceMode('x');
          setFocus('all');
          if (setCond3D) setCond3D(true);
        }
      }
    ],
    readoutLabels: [
      'Line slopes dy/dx in (x, y) plane',
      'Slice area & conditional moments',
      'Joint pdf at regression peak',
      'Joint pdf at ellipse ridge crossing'
    ],
    evalJoint: (x, y, p) => bvnJoint(x, y, p),
    evalMargX: (x, p) => norm(x, 0, p.s1),
    evalMargY: (y, p) => norm(y, 0, p.s2),
    evalCond: (t, sv, mode, p) => {
      const sdFactor = Math.sqrt(Math.max(1e-6, 1 - p.rho * p.rho));
      if (mode === 'x') return norm(t, p.rho * (p.s2 / p.s1) * sv, p.s2 * sdFactor);
      return norm(t, p.rho * (p.s1 / p.s2) * sv, p.s1 * sdFactor);
    },
    evalDirect: (x, p) => ({
      mean: p.rho * (p.s2 / p.s1) * x,
      sd: p.s2 * Math.sqrt(Math.max(1e-6, 1 - p.rho * p.rho))
    }),
    evalReverse: (y, p) => ({
      mean: p.rho * (p.s1 / p.s2) * y,
      sd: p.s1 * Math.sqrt(Math.max(1e-6, 1 - p.rho * p.rho))
    }),
    evalRidgeSlope: p => ridgeSlopeObj(p),
    formatReadouts: (sc, st, fmt) => {
      const p = st.params;
      const sv = fmt(p.slice, 2, true);
      const dirSlope = (p.rho * p.s2) / p.s1;
      const revSlopeDx = Math.abs(p.rho) < 1e-5 ? 'vertical' : fmt(p.s2 / (p.rho * p.s1), 2, true);
      const rs = sc.ridgeSlope;
      const ridgeTxt = !rs ? 'isotropic' : (rs.vertical ? 'vertical' : fmt(rs.m, 2, true));
      const cSym = st.mode === 'x' ? `E(Y | X = ${sv})` : `E(X | Y = ${sv})`;
      const fPeak = sc.centroidRawZ;
      const fPeakStr = fPeak > 0 && fPeak < 1e-3 ? fPeak.toExponential(2) : fPeak.toFixed(4);
      let rcTxt = 'Circular contours (ρ = 0, σ₁ = σ₂)';
      if (sc.ridgeCross) {
        const fR = sc.ridgeCross.rawZ;
        const fRStr = fR > 0 && fR < 1e-3 ? fR.toExponential(2) : fR.toFixed(4);
        const pct = fPeak > 1e-12 ? fmt(((fR - fPeak) / fPeak) * 100, 1, false) : '0.0';
        const coordLbl = st.mode === 'x' ? 'y_ridge' : 'x_ridge';
        rcTxt = `${coordLbl} = ${fmt(sc.ridgeCross.t, 3, true)} · f = ${fRStr} (${pct}%)`;
      } else if (rs) {
        const coincides = (st.mode === 'x' && rs.vertical && Math.abs(p.slice) < 1e-5)
          || (st.mode === 'y' && !rs.vertical && Math.abs(rs.m) < 1e-5 && Math.abs(p.slice) < 1e-5);
        rcTxt = coincides ? 'Slice coincides with major axis' : 'Ridge parallel or outside plot window';
      }
      const peakLbl = st.mode === 'x' ? 'y_reg' : 'x_reg';
      return [
        `dir ${fmt(dirSlope, 2, true)} · ridge ${ridgeTxt} · rev ${revSlopeDx}`,
        `${cSym} = ${fmt(sc.condMean, 3, true)} · SD = ${sc.condSd.toFixed(3)}`,
        `${peakLbl} = ${fmt(sc.condMean, 3, true)} · f = ${fPeakStr} (max)`,
        rcTxt
      ];
    }
  };
})();
</script>

{% include jd-3d-workbench.html %}
