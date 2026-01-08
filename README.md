# Monte Carlo UAV Validation Framework

**Robustness benchmarking of Nonlinear UDE vs. Linear PID controllers using stochastic flight simulations.**

![MATLAB](https://img.shields.io/badge/MATLAB-R2024a-orange.svg)
![Simulink](https://img.shields.io/badge/Simulink-Model--Based%20Design-blue.svg)
![Status](https://img.shields.io/badge/Status-Validated-brightgreen.svg)

## 📌 Project Overview
This repository contains a rigorous **Verification & Validation (V&V)** framework for Quadcopter control systems. 

It utilizes **MATLAB, Simulink, and Simscape** to automate **1,000+ Monte Carlo flight iterations**, stress-testing a nonlinear **Uncertainty and Disturbance Estimator (UDE)** against a standard PID baseline. The simulation introduces stochastic environmental variables—including variable wind vectors (0–15 m/s) and payload mass shifts—to quantify the "Operational Envelope" of advanced control laws.

### Key Objectives
* **Quantify Robustness:** Move beyond simple step-response tests to statistically valid failure analysis.
* **Energy vs. Accuracy:** Analyze the cost of precision using high-fidelity electromechanical motor models.
* **Failure Mode Detection:** Identify edge cases (e.g., actuator saturation) that only appear under stochastic loading.

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

---

## 🚀 How to Run the Simulation

### Prerequisites
* MATLAB R2022b or newer
* Simulink
* Simscape Electrical (for the motor models)

### Setup & Execution
1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/YOUR_USERNAME/Monte-Carlo-UAV-Validation.git](https://github.com/YOUR_USERNAME/Monte-Carlo-UAV-Validation.git)
    cd Monte-Carlo-UAV-Validation
    ```

2.  **Run the Master Script:**
    Open MATLAB and execute:
    ```matlab
    run_master_simulation
    ```

3.  **View Results:**
    * The script will print a statistical report to the Command Window (Safety Margins, Sensitivity Analysis).
    * It will generate 3 plots:
        1.  **Trend Analysis:** Wind Speed vs. Accuracy Improvement.
        2.  **Histogram:** Distribution of performance gains.
        3.  **Efficiency Frontier:** Energy (Joules) vs. Error (RMSE).

---

## 📂 File Structure

```text
├── run_master_simulation.m        # ENTRY POINT: Main Monte Carlo automation script
├── quadcopter_package_delivery.slx # The Simulink Plant & Controller Model
├── quadcopter_package_data.m       # Physical parameters (Mass, Inertia, Motor constants)
├── quadcopter_package_select_trajectory.m # Waypoint generation logic
└── utils/                          # Helper functions for Spline generation and Visualization
