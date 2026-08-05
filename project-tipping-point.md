---
layout: default
title: Forecasting airfoil wake and stall transitions with Recurrent Neural Operator (RNO)
---

# Forecasting Airfoil Wake and Stall Transitions

![Airfoil stall transition animation](/Pictures/video_stall_transition_high_quality.gif){: style="width:100%; border-radius:8px;"}

*Airfoil stall transition as the angle of attack increases.*

## Overview
This work uses a **Recurrent Neural Operator (RNO)** to forecast two important aerodynamic transitions from data collected before either event occurs:

- **Wake transition:** vortex shedding changes from one vortex at a time to vortex pairs.
- **Static stall:** a small increase in angle of attack causes a rapid loss of lift.

The full paper studies several non-stationary systems; this page focuses on the airfoil case, for which I generated the simulation data.

---

## Airfoil Simulations
I generated two-dimensional large-eddy simulations of incompressible flow over an airfoil while its angle of attack increased at a constant rate. The data cover three forecasting settings:

1. Static stall at a Reynolds number of 1,000.
2. Wake transition at a Reynolds number of 5,000.
3. Static stall after the wake transition at a Reynolds number of 5,000.

These cases form a progression from a relatively smooth low-Reynolds-number flow to a more turbulent flow with two successive transitions.

---

## Forecasting Approach
The RNO learns the time evolution of the flow using only pre-transition data. During a forecast, the method monitors how strongly the predicted velocity field violates mass conservation. A statistically calibrated threshold converts that physics error into an early-warning signal with an uncertainty guarantee.

Only the divergence-free condition is needed; the forecasting system does not require the complete governing equations or examples from after the transition during training.

---

## Results
- RNO accurately forecast both wake transition and static stall before they occurred.
- It maintained more reliable long-range predictions than the tested Markov Neural Operator and recurrent neural network baselines.
- A model trained only on pre-stall data at a Reynolds number of 1,000 successfully forecast both transitions at a Reynolds number of 5,000 without retraining.
- The framework also forecast the later stall event after being trained only on data before the earlier wake transition.

These results show that a learned dynamics model and a lightweight physics check can provide early warning of aerodynamic regime changes, including conditions not represented during training.

---

## My Contribution
- Generated and post-processed the large-eddy simulation data for the airfoil study.
- Provided aerodynamic domain expertise and contributed to manuscript writing.

---

## Reference
**Liu-Schiaffini, M., Singer, C. E., Kovachki, N., Leung, S. C., Bae, H. J., Azizzadenesheli, K., & Anandkumar, A. (2026).**<br>
*Tipping Point Forecasting in Non-Stationary Dynamics on Function Spaces.*<br>
Under review at *Proceedings of the National Academy of Sciences (PNAS)*.

📖 [Preprint →](https://arxiv.org/abs/2308.08794)

---

[⬅ Back to Projects](/#projects)
