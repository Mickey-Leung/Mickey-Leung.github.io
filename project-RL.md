---
layout: default
title: Reinforcement learning control of gust-induced airfoil lift fluctuations
---

# Reinforcement Learning Control of Airfoil Lift in Gusts

## Overview
Small aircraft and unmanned aerial vehicles can experience large, unpredictable changes in lift when flying through turbulent air. This project develops a **reinforcement-learning (RL) controller** that responds to sparse pressure measurements and adjusts air jets on an airfoil to reduce those fluctuations.

In preliminary tests, the controller reduced lift variability by **18.2%** relative to the uncontrolled flow while maintaining effective control beyond the time interval used for training.

---

## Simulation Setup
The gust environment is modeled by placing a cylinder upstream of a NACA 0012 airfoil. Vortices shed from the cylinder create a strongly unsteady inflow similar to repeated gusts. The flow is simulated using wall-resolved large-eddy simulation at a chord-based Reynolds number of 10,000 and an angle of attack of 5 degrees.

The high-fidelity computational mesh contains approximately 20 million cells. This resolution captures the turbulent cylinder wake, the airfoil boundary layer, and their interaction.

---

## Sensing and Control
The controller observes the flow through **ten surface-pressure sensors** placed at locations identified by the [Correlation-Assisted Attribution Framework (CAAF)](/project-CAAF). It then adjusts distributed blowing and suction over most of the airfoil surface.

The upper and lower surface jets operate in opposite directions so that the total injected and removed mass remains balanced. The RL policy learns directly through interaction with the simulated flow: actions that keep lift near its long-term mean receive a better reward, while large lift deviations are penalized.

The controller uses the V-RACER algorithm and was trained for approximately 150 simulated episodes. Its action changes the jet velocity gradually, producing a smooth feedback response rather than abrupt commands.

---

## Preliminary Results
- The standard deviation of the lift coefficient decreased from **0.708 to 0.579**, an **18.2% reduction**.
- Lift suppression continued after the training interval, indicating that the learned policy generalized to later gust interactions.
- The actuation velocity remained below 10% of the freestream velocity throughout the test.
- Flow-field analysis suggests that the controller changes the path of the leading-edge vortex and reduces unequal aerodynamic forcing between the upper and lower surfaces.

These observations suggest that RL can provide both an effective control strategy and useful physical insight into how gust-induced lift fluctuations can be suppressed.

---

## Next Steps
Future work will evaluate smaller and more practical actuators, test additional cylinder-airfoil configurations, and quantify the controlled leading-edge vortex dynamics in greater detail. Repeated control patterns may also be used to derive simpler feedback laws or open-loop strategies inspired by the learned policy.

---

## Conference Abstract
**Leung, S. C.**, Zhou, D., & Bae, H. J. (2027).<br>
*Reinforcement learning control of gust-induced airfoil lift fluctuations.*<br>
AIAA SciTech 2027 conference abstract.

[⬅ Back to Projects](/#projects)
