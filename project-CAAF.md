---
layout: default
title: CAAF - Data-driven sensor placement for predictive applications
---

# Correlation-Assisted Attribution Framework (CAAF)

## Overview
Physical systems may offer hundreds of possible sensor locations, but many nearby sensors record nearly the same information. The **Correlation-Assisted Attribution Framework (CAAF)** identifies a small set of informative locations while avoiding this redundancy. It is designed for prediction tasks in nonlinear systems where conventional placement methods can miss important relationships in the data.

---

## How It Works
1. Group candidate sensors that produce similar signals.
2. Keep one representative location from each group.
3. Train a model to predict the quantity of interest from those representatives.
4. Rank the representatives by their contribution to the model and select the desired number of sensors.

This separation between correlation analysis, prediction, and attribution makes CAAF adaptable to different systems and learning models.

---

## Demonstrated Applications
- **Structural health monitoring:** CAAF selected five sensing locations on a cantilever beam and achieved the lowest prediction error among the tested placement methods.
- **Airfoil lift prediction:** Surface-pressure sensors were selected to infer rapidly changing lift under steady and gusty inflows.
- **Turbulent-flow sensing:** Sparse wall-pressure measurements were used to estimate velocity away from the wall, a quantity relevant to active drag reduction.

---

## Airfoil Lift Prediction under Gusts
We generated high-fidelity large-eddy simulations of flow over a NACA 0012 airfoil at a Reynolds number of 10,000. Five configurations covered two baseline flows and three gusty flows produced by cylinders upstream of the airfoil. CAAF selected from 376 possible surface-pressure locations.

The sensors were identified using three flow configurations and then evaluated on all five, including two unseen configurations. CAAF was compared with direct feature attribution, QR-based placement, Bayesian experimental design, and uniform spacing.

![Lift-prediction performance of sensor configurations selected by five placement methods](/Pictures/CAAF_prediction_performance.png){: style="width:100%; border-radius:8px;"}

*Prediction error as sensors are added (top) and error normalized by CAAF across all sensor counts (bottom). Lower values are better; error bars summarize repeated model-training runs.*

CAAF performed best in the sparse-sensor regime across the five flow configurations and remained competitive as more sensors were added. Averaged over sensor counts, it produced the lowest error in three cases and was only slightly behind Bayesian experimental design in the other two. The selected locations also have a physical interpretation: they emphasize the leading-edge stagnation region and separated-flow regions that strongly affect lift.

---

## Key Takeaways
- Correlation-based clustering prevents the sensor budget from being spent on repeated information.
- Target-aware ranking directly connects sensor selection to predictive accuracy.
- The same framework works across structures, aerodynamics, and wall-bounded turbulence.
- Performance depends on representative training data, a reliable prediction model, and a suitable correlation metric.

---

## Reference
**Leung, S. C.**, Zhou, D., & Bae, H. J. (2026).<br>
*Data-driven sensor placement for predictive applications: a Correlation-Assisted Attribution Framework (CAAF).*<br>
*Communications AI & Computing*, **1**, Article 8 (2026).

📂 [Code and data on GitHub →](https://github.com/Mickey-Leung/CAAF)<br>
📖 [Published article →](https://doi.org/10.1038/s44488-026-00011-1)

[⬅ Back to Projects](/#projects)
