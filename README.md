# UDE Drone Control System with Monte Carlo Validation

![MATLAB](https://img.shields.io/badge/MATLAB-R2024a-orange.svg)
![Simulink](https://img.shields.io/badge/Simulink-Model--Based%20Design-blue.svg)

## Project Overview

This repository develops a nonlinear Uncertainty and Disturbance Estimator (UDE) controller, and compares it to a standard linear PID controller using flight simulations with stochastic wind. It also includes a **Verification & Validation** framework to test the improved Quadcopter control system. 

The inspiration for this project was to improve package delivery via drones in urban environments. The unique and inconsistent shape of buildings and houses causes wind to be unpredictable throughout a city, and can lead to safety risks if the drone veers off its desired trajectory. 

It uses **MATLAB, Simulink, and Simscape** to simulate **1,000+ Monte Carlo flight iterations**, stress-testing a nonlinear **Uncertainty and Disturbance Estimator (UDE)** against a standard PID baseline. The simulation introduces stochastic environmental variables—including variable wind vectors (0–12.5 m/s) to verify its impact on safety, and the controller's robustness.

https://github.com/user-attachments/assets/fd6ded8a-ac0b-4483-a743-47ebd13b87f3

## Results 
*Based on N=500 stochastic flight iterations.*

| Metric | Result | Engineering Implication |
| :--- | :--- | :--- |
| **Accuracy Gain** | **+30.2%** | UDE significantly outperforms PID in nominal trajectory tracking. |
| **Energy Cost** | **< 0.2%** | The nonlinear controller achieves higher precision with negligible battery penalty. |
| **Safety Risk** | **3.4%** | Detected actuator saturation events in extreme high-wind scenarios. 

**Conclusion:** The UDE controller shows great improvement from the standard PID controller.

**Future Development**
Gain-scheduling, which is having a known table of parameter values depending on the wind-speed, could be introduced using the actuatory saturation data, as well as data from the Monte Carlo Simulation he actuatory saturation data can be used for gain-scheduling, adjusting the controller's parameters depending on the wind speed. This would make the controller more effective, and would further reduce any safety risks. 

## Acknowledgements

**Research Context**
This work was conducted in collaboration with the **Aerial Robotics Club**, a division of the [Flight Systems and Control (FSC) Research Lab](https://flight.utias.utoronto.ca/) at the **University of Toronto Institute for Aerospace Studies (UTIAS)**.

**Simulation Platform**
The visualization and plant model baseline were adapted from the [MathWorks Quadcopter Package Delivery](https://www.mathworks.com/help/sps/ug/quadcopter-drone.html) example. The control architecture was completely re-engineered from the default implementation to support the custom UDE/PID comparison study.
