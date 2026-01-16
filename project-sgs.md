---
layout: default
title: Consistency Requirements for Data-Driven SGS Modeling
---

## Overview

Data-driven subgrid-scale (SGS) models for large-eddy simulation (LES) often demonstrate strong **a-priori** accuracy when trained on filtered DNS data, yet fail to deliver stable or physically consistent **a-posteriori** performance when deployed in actual LES solvers. This work identifies and explains a fundamental source of this inconsistency: **numerical deviation** between filtered high-fidelity data and the governing equations solved in LES.

We show that ignoring this deviation during model development leads to overprediction of small-scale turbulence, numerical instability, and degraded spectral accuracy—particularly for high-capacity nonlinear models.

## Key Idea: Numerical Deviation Matters

When LES equations are compared against filtered DNS, additional terms arise due to:
- Non-commutation between filtering and differentiation
- Grid-resolution mismatch
- Discretization and projection effects

These effects collectively introduce a **numerical deviation term** that is absent from standard a priori training pipelines. Although often small in instantaneous magnitude, this deviation strongly influences long-time LES dynamics.

This work demonstrates that **explicitly incorporating numerical deviation during model training** significantly improves consistency between a-priori and a-posteriori behavior.

## Methodology

- **DNS-aided LES framework**  
  Filtered DNS and LES are evolved side-by-side to directly quantify numerical deviation.

- **Physically constrained model forms**  
  Models are constructed using Galilean-invariant tensor bases derived from local velocity gradients.

- **Two SGS model classes**
  - Eddy-viscosity neural-network model  
  - Complex nonlinear tensor-based neural-network model

- **Training strategies**
  - Standard training (excluding numerical deviation)
  - Consistency-aware training (including numerical deviation in the loss function)

## Publications
- 📖 [Journal Paper →](https://doi.org/10.1103/yykb-6rvf)
- 📖 [Comference Procedding →](https://web.stanford.edu/group/ctr/ctrsp24/v04_HUANG.pdf)
