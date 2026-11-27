---
layout: archive
title: "Stein-Detrended Odd Wave: Zero Correlation Without Mean Independence"
permalink: /demos/stein-wave-uncorrelated/
author_profile: false
---

{% include base_path %}
{% include jd-3d-head.html current="stein-wave-uncorrelated" %}

<div class="jd-prose" markdown="1">

Zero [correlation](/lecture-notes/correlation-coefficient/#def-corr) ($\rho_{\sssig XY}=0$, equivalently $\operatorname{Cov}(X,Y)=0$) is strictly weaker than [mean independence](/lecture-notes/covariance/#note-mean-independence) even when **both** direct and reverse [regression functions](/lecture-notes/double-expectation-theorem/#thm-regression-function) fail mean independence simultaneously. To construct an elementary closed-form example, let $X\sim\mathcal{N}(0,\sigma_1^{2})$ and center the conditional normal slice along a detrended sine wave ($a,\omega,\tau>0$):

<div class="jd-math-desk" markdown="1">

$$
\begin{gathered}
Y\mid(X=x)\sim\mathcal{N}\bigl(h(x),\,\tau^{2}\bigr),\qquad h(x)=a\bigl[\sin(\omega x)-c\,x\bigr]\\[0.32em]
c=\omega\exp\!\left(-\frac{1}{2}\omega^{2}\sigma_1^{2}\right)
\end{gathered}
$$

</div>
<div class="jd-math-mob" markdown="1">

$$
\begin{gathered}
Y\mid(X=x)\sim\mathcal{N}\bigl(h(x),\,\tau^{2}\bigr)\\[0.28em]
h(x)=a\bigl[\sin(\omega x)-c\,x\bigr]\\[0.28em]
c=\omega\exp\!\left(-\frac{1}{2}\omega^{2}\sigma_1^{2}\right)
\end{gathered}
$$

</div>

Since $h(-x)=-h(x)$ is an odd function and $X$ is symmetric around $0$, $\mathbb{E}(Y)=\mathbb{E}[h(X)]=0$. Neither $\mathbb{E}(Y\mid X=x)=h(x)$ nor $\mathbb{E}(X\mid Y=y)$ is constant, so mean independence fails in both directions. Differentiating the normal [characteristic function](/lecture-notes/characteristic-functions/#def-characteristic-function) (or applying [Stein’s lemma](/lecture-notes/standard-normal-moments-stein-lemma/#thm-stein-lemma)) gives $\mathbb{E}[X\sin(\omega X)]=\omega\sigma_1^{2}\exp(-\omega^{2}\sigma_1^{2}/2)=c\,\sigma_1^{2}$, which forces exact zero [covariance](/lecture-notes/covariance/#def-covariance) for every choice of $(a,\omega,\sigma_1,\tau)$:

$$
\operatorname{Cov}(X,Y)=\mathbb{E}\bigl[X\,h(X)\bigr]=a\bigl(\mathbb{E}[X\sin(\omega X)]-c\,\mathbb{E}[X^{2}]\bigr)=0
$$

Since $x\,h(x)\,f_{\sssig X}(x)$ is an **even** function of $x$, zero covariance here does not arise from left-right odd cancellation; instead, positive cross-product bands (where $x\sin(\omega x)>cx^{2}$, including the central core around $x=0$) and negative cross-product bands (where the linear tilt $cx^{2}$ exceeds $x\sin(\omega x)$) integrate to equal and opposite magnitudes over $\mathbb{R}$.

**Parameters to explore below:**

- **Wave frequency $\omega$ and dispersion $\sigma_1$**: As you vary $\omega$ or $\sigma_1$, the detrending slope $c=\omega e^{-\omega^{2}\sigma_1^{2}/2}$ updates automatically so the positive (green) and negative (crimson) bands of the covariance integrand always integrate to `0.0000` over $\mathbb{R}$.
- **Wave amplitude $a$ and slice standard deviation $\tau$**: Increasing $a$ scales the oscillation amplitude of $h(x)$, whereas increasing $\tau$ widens the conditional slices and attenuates the reverse regression curve $\mathbb{E}(X\mid Y=y)$; neither parameter alters $\operatorname{Cov}(X,Y)=0$.

</div>

<script>
window.JD_CONFIG = (function () {
  const SQRT_2PI = Math.sqrt(2 * Math.PI);
  function norm(u, m, s) {
    const z = (u - m) / s;
    return Math.exp(-0.5 * z * z) / (SQRT_2PI * s);
  }
  function steinH(x, p) {
    const c = p.omega * Math.exp(-0.5 * p.omega * p.omega * p.s1 * p.s1);
    return p.a * (Math.sin(p.omega * x) - c * x);
  }
  function jointVal(x, y, p) {
    return norm(x, 0, p.s1) * norm(y, steinH(x, p), p.tau);
  }

  return {
    domainL: 3.2,
    defaultMode: 'x',
    defaultCond3D: true,
    hasStatusStrip: true,
    hasCovPanel: true,
    sliders: [
      { id: 'slice', label: 'Slice x₀', dynamicLabel: st => st.mode === 'x' ? 'Slice position x₀' : 'Slice position y₀', min: -2.50, max: 2.50, step: 0.05, def: 0.85, signed: true },
      { id: 'a', label: 'Wave amplitude a', min: 0.25, max: 1.15, step: 0.05, def: 0.85, signed: false },
      { id: 'omega', label: 'Wave frequency ω', min: 1.20, max: 2.60, step: 0.05, def: 1.80, signed: false },
      { id: 's1', label: 'SD σ₁ of X', min: 0.65, max: 1.30, step: 0.05, def: 1.00, signed: false },
      { id: 'tau', label: 'Cond. SD τ (Y | X = x)', min: 0.30, max: 0.85, step: 0.03, def: 0.42, signed: false }
    ],
    readoutLabels: [
      'Slice area (side-wall marginal)',
      'Stein tilt coefficient c(ω, σ₁)',
      'Active conditional mean & SD',
      'Exact Cov(X, Y) & Corr(X, Y)'
    ],
    evalJoint: (x, y, p) => jointVal(x, y, p),
    evalMargX: (x, p) => norm(x, 0, p.s1),
    evalMargY: (y, p) => {
      const nQ = 161;
      const xMax = Math.max(4.5, 6.0 * p.s1);
      const h = (2 * xMax) / nQ;
      let sum = 0;
      for (let k = 0; k < nQ; k++) sum += jointVal(-xMax + (k + 0.5) * h, y, p);
      return sum * h;
    },
    evalCond: (t, sv, mode, p) => mode === 'x' ? norm(t, steinH(sv, p), p.tau) : null,
    evalDirect: (x, p) => ({ mean: steinH(x, p), sd: p.tau }),
    evalReverse: (y, p) => {
      const nQ = 161;
      const xMax = Math.max(4.5, 6.0 * p.s1);
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
    evalBadges: () => ({
      indep: { holds: false, text: 'Fails' },
      my: { holds: false, text: 'Fails (≠ 0)' },
      mx: { holds: false, text: 'Fails (≠ 0)' },
      cov: { holds: true, text: 'Holds (= 0)' }
    }),
    formatCovCaption: () => 'Even integrand: positive (green) and negative (crimson) cross-product bands integrate to exact 0 over ℝ.',
    formatReadouts: (sc, st, fmt) => {
      const p = st.params;
      const sv = fmt(p.slice, 2, true);
      const c = p.omega * Math.exp(-0.5 * p.omega * p.omega * p.s1 * p.s1);
      const mSym = st.mode === 'x' ? `f_X(${sv})` : `f_Y(${sv})`;
      const cSym = st.mode === 'x' ? `E(Y | X = ${sv})` : `E(X | Y = ${sv})`;
      const areaStr = sc.sliceArea > 0 && sc.sliceArea < 1e-3 ? sc.sliceArea.toExponential(2) : sc.sliceArea.toFixed(4);
      const eqSign = st.mode === 'x' ? '=' : '≒';
      return [
        `${mSym} = ${areaStr}`,
        `c = ω·exp(−½ω²σ₁²) = ${c.toFixed(4)}`,
        sc.hasValidCond && sc.condMean !== null ? `${cSym} ${eqSign} ${fmt(sc.condMean, 3, true)} · SD = ${sc.condSd.toFixed(3)}` : 'Negligible slice density',
        'Cov(X, Y) = 0.0000 · Corr(X, Y) = 0.0000'
      ];
    }
  };
})();
</script>

{% include jd-3d-workbench.html %}
