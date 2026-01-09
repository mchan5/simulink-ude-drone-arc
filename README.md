# UDE Drone Control System with Monte Carlo Validation

![MATLAB](https://img.shields.io/badge/MATLAB-R2024a-orange.svg)
![Simulink](https://img.shields.io/badge/Simulink-Model--Based%20Design-blue.svg)

## Project Overview

This repository develops a nonlinear Uncertainty and Disturbance Estimator (UDE) controller, and compares it to the standard linear PID controllers using flight simulations with stochastic wind. It also includes a **Verification & Validation** framework to test the improved Quadcopter control system. 

It utilizes **MATLAB, Simulink, and Simscape** to simulate **1,000+ Monte Carlo flight iterations**, stress-testing a nonlinear **Uncertainty and Disturbance Estimator (UDE)** against a standard PID baseline. The simulation introduces stochastic environmental variables—including variable wind vectors (0–12.5 m/s) and payload mass shifts— of advanced control laws.

### Key Objectives
* **Quantify Robustness:** Move beyond simple step-response tests to statistically valid failure analysis.
* **Energy vs. Accuracy:** Analyze the cost of precision using high-fidelity electromechanical motor models.
* **Failure Mode Detection:** Identify edge cases (e.g., actuator saturation) that only appear under stochastic loading.


https://github.com/user-attachments/assets/fd6ded8a-ac0b-4483-a743-47ebd13b87f3


---

## 📊 Key Engineering Insights
*Based on N=500 stochastic flight iterations.*

| Metric | Result | Engineering Implication |
| :--- | :--- | :--- |
| **Accuracy Gain** | **+30.2%** | UDE significantly outperforms PID in nominal trajectory tracking. |
| **Energy Cost** | **< 0.2%** | The nonlinear controller achieves higher precision with negligible battery penalty. |
| **Wind Correlation** | **-0.91** | Performance degrades linearly with wind speed; UDE advantage vanishes at **9.6 m/s**. |
| **Safety Risk** | **3.4%** | Detected actuator saturation events in extreme high-wind scenarios. |

> **Conclusion:** The UDE architecture is the superior choice for precision operations in wind speeds <10 m/s. For hurricane-level disturbances (>10 m/s), a hybrid fallback to PID is recommended to prevent actuator saturation.

---

## 🛠️ Features
* **Automated Monte Carlo Pipeline:** A Master Script that randomizes environmental parameters, runs the Simulink model, and aggregates data automatically.
* **High-Fidelity Physics:** Uses **Simscape** for battery discharge curves and motor dynamics, ensuring energy metrics are realistic.
* **Crash Detection Logic:** Automatically flags unstable flights (RMSE > 30m) to calculate reliability rates.
* **Advanced Analytics:** Calculates complex metrics like *Disturbance Rejection Ratio*, *Integral Absolute Error (IAE)*, and *Control Effort (Jerk)*.


## 📂 File Structure

```text
├── run_master_simulation.m        # ENTRY POINT: Main Monte Carlo automation script
├── quadcopter_package_delivery.slx # The Simulink Plant & Controller Model
├── quadcopter_package_data.m       # Physical parameters (Mass, Inertia, Motor constants)
├── quadcopter_package_select_trajectory.m # Waypoint generation logic
└── utils/                          # Helper functions for Spline generation and Visualization
