# UDE Drone Control System with Monte Carlo Validation

![MATLAB](https://img.shields.io/badge/MATLAB-R2024a-orange.svg)
![Simulink](https://img.shields.io/badge/Simulink-Model--Based%20Design-blue.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg) <!-- Add your license if applicable -->

## Project Overview
This repository develops a nonlinear **Uncertainty and Disturbance Estimator (UDE)** controller for quadcopters and evaluates its performance against a standard PID baseline. 

Using MATLAB and Simscape, the system was subjected to over **1,000 Monte Carlo flight iterations** under highly stochastic wind vectors. The simulation demonstrates how advanced adaptive control effectively counteracts unpredictable urban wind disturbances, making it highly applicable for robust drone package delivery systems.

https://github.com/user-attachments/assets/fd6ded8a-ac0b-4483-a743-47ebd13b87f3

## Key Features
* **UDE Nonlinear Control:** Implementation of an Uncertainty and Disturbance Estimator to actively compensate for unmodeled dynamics and external wind forces.
* **PID Baseline Comparison:** Side-by-side performance benchmarking against a well-tuned PID controller.
* **Monte Carlo Validation:** Automated testing pipeline running 1,000+ stochastic wind simulations to ensure statistical significance.
* **Simscape Multibody Modeling:** High-fidelity physical modeling of quadcopter dynamics.

## Results 
*Based on N=1000 stochastic flight iterations.*

| Metric | Result | Engineering Implication |
| :--- | :--- | :--- |
| **Accuracy Gain** | **+9.2%** | UDE significantly outperforms PID in nominal trajectory tracking based on RMSE. |
| **Energy Cost** | **< 0.2%** | The nonlinear controller achieves higher precision with negligible battery penalty. |

## Future Development
Gain-scheduling could be introduced using the actuator saturation data to adjust the controller's parameters depending on the wind speed. 

## Acknowledgements
Thank you to [UTIAS Flight Systems and Control Research Lab](https://flight.utias.utoronto.ca/) for their advice for the development of this project.

The visualization model was adapted from [MathWorks Quadcopter Package Delivery](https://www.mathworks.com/help/sps/ug/quadcopter-drone.html).
