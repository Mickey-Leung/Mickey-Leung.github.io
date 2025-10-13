---
layout: default
title: Forecasting airfoil wake and stall transitions with Recurrent Neural Operator (RNO)
---

---
layout: default
title: Forecasting Airfoil Wake and Stall Transitions
---

# Forecasting Airfoil Wake and Stall Transitions

![Airfoil stall transition animation](/images/video_stall_transition_high_quality.gif){: style="width:100%; border-radius:8px;"}

## Overview
This project demonstrates how **Recurrent Neural Operators (RNO)** can be trained to forecast *aerodynamic tipping points*. Specifically, the **airfoil wake transition** and **static stall**—in a 2-D flow over an airfoil with an increasing angle of attack.  
The study is part of a broader framework for **tipping-point forecasting in non-stationary dynamical systems**, capable of learning physics-aware models directly from pre-tipping data.

<!-- ---

## Motivation
In aerodynamics, wake transition and stall mark critical bifurcations in the flow regime:
- **Wake transition:** the shift from single-vortex to vortex-pair shedding.
- **Static stall:** the abrupt loss of lift following a small increase in angle of attack.

Accurately predicting these transitions can help prevent loss of lift and improve active control in aircraft and turbine systems. Traditional solvers require costly simulations over long time horizons to capture such events. RNOs offer a **data-efficient, physics-informed alternative**. -->

---

## Methodology
We trained separate RNO models on pre-tipping flow data at different Reynolds numbers:

1. **Re = 1000:** static stall only  
2. **Re = 5000:** wake transition  
3. **Re = 5000:** combined wake and stall transitions  

Data is generated from **LES (Large-Eddy Simulation)** governed by the incompressible Navier–Stokes equations.  
The **divergence-free condition** ∇·u = 0 was used as the *physics constraint* to quantify deviations from physical laws, forming the basis of a physics-loss metric.

At inference time, the model’s **physics loss** was monitored:
- When the loss exceeded a conformal threshold, a tipping point was forecast.  
- The method was validated across multiple Re values to assess zero-shot generalization.

---

## Results
- RNO achieved accurate forecasts for both wake and stall transitions well before the tipping events occurred.  
- The model maintained stable long-term predictions compared with Markov Neural Operators (MNO) and recurrent neural networks (RNN).  
- Generalization tests showed RNO could forecast unseen regimes. For example, predicting Re = 5000 stall transitions after training only on Re = 1000 data.

These results confirm that RNOs scale to complex spatiotemporal PDE systems, enabling early detection of aerodynamic instabilities with minimal physical priors.

---

<!-- ---

## Key Takeaways
- Robust to **approximate physics** (e.g., conservation laws instead of full PDEs).  
- Scalable to **high-dimensional turbulent flows**.  
- Capable of **zero-shot forecasting** across unseen flow regimes.  
- Offers a promising approach for real-time **stall prediction and flow-control applications**. -->

## My contribution
- Data generation through LES and post-processing.
- Manuscript writing.

---

## Citation
**Liu-Schiaffini, M., Singer, C. E., Kovachki, N., Leung, S. C., Schneider, T., Bae, H. J., Azizzadenesheli, K., & Anandkumar, A. (2025).**  
*Tipping Point Forecasting in Non-Stationary Dynamics on Function Spaces.*  
*PNAS (submitted).*

---

[⬅ Back to Projects](/#projects)
