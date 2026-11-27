---
layout: archive
title: "Radially Symmetric Volcano Crater: Mean Independence Without Independence"
permalink: /demos/volcano-mean-independence/
author_profile: false
---

{% include base_path %}
{% include jd-3d-head.html current="volcano-mean-independence" %}

<div class="jd-prose" markdown="1">

For two random variables with finite second moments, [stochastic independence](/lecture-notes/independent-random-variables/#def-indep-r-v) implies [mean independence](/lecture-notes/covariance/#note-mean-independence) ($\mathbb{E}(Y\mid X=x)=\mathbb{E}(Y)$ and $\mathbb{E}(X\mid Y=y)=\mathbb{E}(X)$), which in turn implies zero [covariance](/lecture-notes/covariance/#def-covariance). To see why mean independence is strictly weaker than stochastic independence, consider the radially symmetric family indexed by crater depth $\lambda\in[0,1]$ and scale $\sigma>0$:

$$
f_{\sssig XY}(x,y)=(1-\lambda)\,\phi(x;0,\sigma)\,\phi(y;0,\sigma)+\lambda\,\frac{x^{2}+y^{2}}{4\pi\sigma^{4}}e^{-\frac{x^{2}+y^{2}}{2\sigma^{2}}}
$$

At $\lambda=0$, $f_{\sssig XY}$ reduces to an independent bivariate normal bell. At $\lambda=1$ (the pure volcano crater), the density vanishes at the origin $(0,0)$ and rises to a circular rim of radius $\sqrt{2}\sigma$. Integrating over $y$ yields elementary closed forms for both the side-wall [marginal pdf](/lecture-notes/marginal-probability-density-functions/#def-marginal-pdf) and the renormalized [conditional pdf](/lecture-notes/conditional-distributions/#def-conditional-pdf):

$$
\begin{gathered}
f_{\sssig X}(x)=\left(1-\frac{\lambda}{2}+\frac{\lambda x^{2}}{2\sigma^{2}}\right)\phi(x;0,\sigma)\\[0.32em]
f_{\sssig Y\mid X}(y\mid x)=\frac{2(1-\lambda)\sigma^{2}+\lambda(x^{2}+y^{2})}{(2-\lambda)\sigma^{2}+\lambda x^{2}}\,\phi(y;0,\sigma)
\end{gathered}
$$

When $\lambda>0$, $X$ and $Y$ are dependent. In particular, at $\lambda=1$ and $x_0=0$, the conditional slice $f_{\sssig Y\mid X}(y\mid 0)=(y^{2}/\sigma^{2})\phi(y;0,\sigma)$ is bimodal with zero density at $y=0$ and variance $3\sigma^{2}$, whereas for $\lvert x_0\rvert\geqslant\sqrt{2}\sigma$ the slice merges into a single peak whose variance decreases toward $\sigma^{2}$. However, every vertical and horizontal slice is an even function around $0$, so $\mathbb{E}(Y\mid X=x)=0=\mathbb{E}(Y)$, $\mathbb{E}(X\mid Y=y)=0=\mathbb{E}(X)$, and $\operatorname{Cov}(X,Y)=0$ hold identically.

**Parameters to explore below:**

- **Crater depth $\lambda$**: Toggle **Pure crater (λ = 1)** vs. **Indep. normal (λ = 0)** and sweep $x_0$. When $\lambda=0$, the 3D crimson conditional arch stays identical to the side-wall marginal $f_{\sssig Y}(y)$ everywhere; when $\lambda=1$, the conditional slice changes from bimodal at $x_0=0$ to unimodal in the tails whereas its centroid remains fixed at $0$.
- **Radial scale $\sigma$**: Varying $\sigma$ expands or contracts the circular rim radius $\sqrt{2}\sigma$ (at $\lambda=1$).

</div>

<script>
window.JD_CONFIG = (function () {
  const TWO_PI = 2 * Math.PI;
  const SQRT_2PI = Math.sqrt(TWO_PI);
  function norm(u, s) {
    const z = u / s;
    return Math.exp(-0.5 * z * z) / (SQRT_2PI * s);
  }
  function marg1D(u, p) {
    const s2 = p.sigma * p.sigma;
    return (1 - 0.5 * p.lam + (0.5 * p.lam * u * u) / s2) * norm(u, p.sigma);
  }
  function cond1D(v, u0, p) {
    const s2 = p.sigma * p.sigma;
    const num = 2 * (1 - p.lam) * s2 + p.lam * (u0 * u0 + v * v);
    const den = (2 - p.lam) * s2 + p.lam * u0 * u0;
    return (num / Math.max(1e-12, den)) * norm(v, p.sigma);
  }
  function condSd1D(u, p) {
    const s2 = p.sigma * p.sigma;
    const denom = (2 - p.lam) * s2 + p.lam * u * u;
    const v = s2 * (1 + (2 * p.lam * s2) / Math.max(1e-9, denom));
    return Math.sqrt(v);
  }

  return {
    domainL: 3.0,
    defaultMode: 'x',
    defaultCond3D: true,
    hasStatusStrip: true,
    sliders: [
      { id: 'slice', label: 'Slice x₀', dynamicLabel: st => st.mode === 'x' ? 'Slice position x₀' : 'Slice position y₀', min: -2.40, max: 2.40, step: 0.05, def: 0.00, signed: true },
      { id: 'lam', label: 'Crater depth λ', min: 0.00, max: 1.00, step: 0.05, def: 1.00, signed: false },
      { id: 'sigma', label: 'Radial scale σ', min: 0.48, max: 0.95, step: 0.02, def: 0.68, signed: false }
    ],
    presets: [
      {
        id: 'crater',
        label: 'Pure crater (λ = 1)',
        apply: (st, setParam, setSliceMode, setFocus, setCond3D) => {
          setParam('lam', 1.00);
          setParam('slice', 0.00);
          setSliceMode('x');
          setFocus('all');
          if (setCond3D) setCond3D(true);
        }
      },
      {
        id: 'indep',
        label: 'Indep. normal (λ = 0)',
        apply: (st, setParam, setSliceMode, setFocus, setCond3D) => {
          setParam('lam', 0.00);
          setParam('slice', 0.90);
          setSliceMode('x');
          setFocus('all');
          if (setCond3D) setCond3D(true);
        }
      }
    ],
    readoutLabels: [
      'Slice area (side-wall marginal)',
      'Active conditional mean',
      'Conditional SD vs. marginal SD',
      'Max |f_cond − f_marg| on slice'
    ],
    evalJoint: (x, y, p) => {
      const s2 = p.sigma * p.sigma;
      const r2 = x * x + y * y;
      const gInd = Math.exp(-r2 / (2 * s2)) / (TWO_PI * s2);
      const gVol = (r2 / (2 * TWO_PI * s2 * s2)) * Math.exp(-r2 / (2 * s2));
      return (1 - p.lam) * gInd + p.lam * gVol;
    },
    evalMargX: (x, p) => marg1D(x, p),
    evalMargY: (y, p) => marg1D(y, p),
    evalCond: (t, sv, mode, p) => cond1D(t, sv, p),
    evalDirect: (x, p) => ({ mean: 0, sd: condSd1D(x, p) }),
    evalReverse: (y, p) => ({ mean: 0, sd: condSd1D(y, p) }),
    evalBadges: st => {
      const ind = st.params.lam < 1e-4;
      return {
        indep: { holds: ind, text: ind ? 'Holds (λ = 0)' : 'Fails' },
        my: { holds: true, text: 'Holds (= 0)' },
        mx: { holds: true, text: 'Holds (= 0)' },
        cov: { holds: true, text: 'Holds (= 0)' }
      };
    },
    formatReadouts: (sc, st, fmt) => {
      const p = st.params;
      const sv = fmt(p.slice, 2, true);
      const margSd = p.sigma * Math.sqrt(1 + p.lam);
      let maxDiff = 0;
      for (let i = 0; i <= 120; i++) {
        const t = -3.0 + (6.0 * i) / 120;
        const cz = cond1D(t, p.slice, p);
        const mz = marg1D(t, p);
        const df = Math.abs(cz - mz);
        if (df > maxDiff) maxDiff = df;
      }
      const mSym = st.mode === 'x' ? `f_X(${sv})` : `f_Y(${sv})`;
      const cSym = st.mode === 'x' ? `E(Y | X = ${sv})` : `E(X | Y = ${sv})`;
      const areaStr = sc.sliceArea < 1e-3 ? sc.sliceArea.toExponential(2) : sc.sliceArea.toFixed(4);
      return [
        `${mSym} = ${areaStr}`,
        `${cSym} = 0.000 (= ${st.mode === 'x' ? 'E(Y)' : 'E(X)'})`,
        `slice SD = ${sc.condSd.toFixed(3)} · marg SD = ${margSd.toFixed(3)}`,
        maxDiff < 1e-4 ? '0.0000 (slice ≡ marginal)' : `${maxDiff.toFixed(4)} (shape depends on cut)`
      ];
    }
  };
})();
</script>

{% include jd-3d-workbench.html %}
