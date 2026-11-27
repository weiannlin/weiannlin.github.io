---
layout: archive
title: "Demos"
permalink: /demos/
author_profile: true
---

{% include base_path %}

Interactive teaching demos for foundational probability concepts, random variables, and joint distributions.

## Random events

- [The Monty Hall Problem](/demos/monty-hall/) — switching beats staying; play it, simulate it, see why.

## Event probabilities

- [Rapid Test Bayesian Updating Lab](/demos/bayesian-updating/) — change prevalence, sensitivity, and specificity, then watch positive or negative results update the posterior.
- [Simpson’s Paradox Mixing Lab](/demos/simpsons-paradox/) — change the group mix and observe when within-group comparisons reverse after aggregation.

## Random variables

- [From pmf to cdf](/demos/pmf-cdf/) — build a discrete distribution by editing $(x, p)$ points, then sweep a current $x$ to watch the cdf accumulate.
- [From pdf to cdf](/demos/pdf-cdf/) — pick a continuous distribution, tune its parameters, sweep $x$, and watch the running integral build the cdf.
- [Mixed distributions](/demos/mixed/) — combine a continuous family with user-defined point masses; watch the cdf jump by exactly $w_i$ at each $x_i$.
- [Probability Integral Transform and Inverse Transform Sampling](/demos/probability-integral-transform/) — follow one value through the standard Cauchy pdf, cdf, and quantile function, then generate inverse-transformed samples and compare their histograms.

## Random vectors and joint distributions

- [3D Joint Density Surfaces, Conditional Slices, and Regression](/demos/joint-density-3d/) — overview and comparison table for the eight interactive 3D/2D/1D labs below:
  - [Conditional Slices, Side-Wall Marginals, and Area Renormalization](/demos/slice-renormalization/) — compare the raw slice $f\_{\sssig XY}(x\_0, y)$, its side-wall marginal area $f\_{\sssig X}(x\_0)$, and the renormalized conditional pdf $f\_{\sssig Y\mid X}(y\mid x\_0)$.
  - [Skewed Conditional Slices: Conditional Expectation as Centroid, Not Peak](/demos/skewed-slice-centroid/) — contrast the slice peak $y\_{\sssig\mathrm{mode}}(x)$ with the right-tail center of gravity $\mathbb{E}(Y\mid X=x)$ on shifted $\mathrm{Gamma}(2,\theta(x))$ slices.
  - [One-Way Linear Regression and Hyperbolic-Tangent S-Curves](/demos/asymmetric-regression-mixture/) — pair an exact linear regression in one direction with a closed-form $\tanh$ S-curve in the reverse direction.
  - [Nonlinear Regression and Valley Centroids on a Bifurcating Ridge](/demos/bimodal-fork-regression/) — follow a curved ridge that splits into two symmetric crests so $\mathbb{E}(Y\mid X=x)$ lies in the valley between the peaks.
  - [Radially Symmetric Volcano Crater: Mean Independence Without Independence](/demos/volcano-mean-independence/) — vary crater depth $\lambda\in[0,1]$ to observe how slices become dependent for $\lambda>0$ whereas their centroids remain fixed at $0$ in both directions.
  - [Parabolic Ridge: One-Way Mean Independence and Zero Covariance](/demos/parabolic-ridge-covariance/) — combine quadratic $\mathbb{E}(Y\mid X=x)$ with constant $\mathbb{E}(X\mid Y=y)=0$ and odd-lobe cancellation to $\operatorname{Cov}(X,Y)=0$.
  - [Stein-Detrended Odd Wave: Zero Correlation Without Mean Independence](/demos/stein-wave-uncorrelated/) — detrend a sine wave via Stein’s lemma so neither regression curve is constant yet $\operatorname{Cov}(X,Y)=0$.
  - [Bivariate Normal Surface, Conditional Slices, and Regression Lines](/demos/bivariate-normal/) — contrast the direct and reverse linear regression lines against the major axis of the equal-density ellipses.
