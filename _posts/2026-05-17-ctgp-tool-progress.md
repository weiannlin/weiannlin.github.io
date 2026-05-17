---
title: "Progress on the ctGP Toolbox"
date: 2026-05-17
permalink: /notes/2026/05/ctgp-tool-progress/
related: false
pagination: false
tags:
  - software
  - Gaussian process
  - Bayesian optimization
---

The ctGP project began as an R implementation for category tree Gaussian process modeling. Over time, the computational core has been gradually redesigned and moved toward C++, with the goal of making the tool more efficient, extensible, and suitable for repeated use in practical modeling and optimization workflows.

Alongside ctGP, two closely related variants are also being developed. The ctmGP version extends the framework toward multi-objective Bayesian optimization, combining category-tree modeling with Pareto-oriented optimization for mixed-variable problems. The ctmfGP version follows a different but related direction, extending the category-tree idea to multi-fidelity prediction and emulation. Together, these projects reflect a broader goal of building a more comprehensive toolkit for Gaussian process modeling and Bayesian optimization with categorical, mixed, multi-objective, and multi-fidelity structures.

The toolbox is not yet publicly released. My current priority is to keep refining the theoretical development and repeatedly improve the package quality, documentation, and workflow design. Once the core methodology and implementation are sufficiently mature, I hope to make the toolbox available for download and use in the near future.
