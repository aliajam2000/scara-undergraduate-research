# Learning-Based Inverse Kinematics for a 4-DOF SCARA Manipulator

**Undergraduate Research Project — Mechanical Engineering, Sharif University of Technology**  
**Researcher:** Ali Ajam  
**Supervisor:** Dr. Hassan Sayyadi  
**Project grade:** 18.7/20  
**Year:** 2025

## Overview

This undergraduate research project investigates a learning-based approach to inverse kinematics for a four-degree-of-freedom SCARA manipulator with an RRPR configuration. The work combines analytical robot modeling, MATLAB simulation, synthetic data generation, and neural-network regression in Python/PyTorch.

The project first develops the forward and inverse kinematics using Denavit–Hartenberg parameters, then formulates and simulates the robot dynamics. A large synthetic dataset of reachable Cartesian end-effector states and corresponding joint variables is generated from the analytical model. A multilayer perceptron (MLP) is then trained to approximate the inverse-kinematics mapping.

## Research Question

Can a neural network learn the nonlinear mapping from Cartesian end-effector states to SCARA joint variables accurately enough to reproduce the analytical inverse-kinematics solution over the simulated workspace?

## Technical Scope

- 4-DOF SCARA manipulator with RRPR joint configuration
- Forward and inverse kinematics
- Denavit–Hartenberg modeling
- Newton–Euler-based dynamic formulation
- MATLAB simulation and model validation
- Synthetic workspace data generation
- Python / PyTorch neural-network training
- Multilayer perceptron regression for inverse kinematics
- Evaluation using MAE, RMSE, and R²

## Methodology

### 1. Robot Modeling

The SCARA manipulator was modeled using standard Denavit–Hartenberg parameters. Homogeneous transformation matrices were derived to obtain the end-effector pose from the joint variables.

Analytical inverse-kinematics equations were then used to recover the revolute joint angles and prismatic displacement from a desired Cartesian end-effector state.

### 2. Dynamic Simulation

A dynamic model was implemented in MATLAB using the standard manipulator form

\[
M(q)\ddot{q} + N(q,\dot{q})\dot{q} + G(q) = \tau.
\]

The simulation was used to evaluate joint torques/forces over prescribed trajectories and to verify the consistency of the mechanical model.

### 3. Synthetic Dataset Generation

The reachable workspace was sampled numerically. For each valid end-effector state, the analytical inverse-kinematics model generated the corresponding joint variables. Invalid configurations were removed using geometric and mechanical constraints.

The resulting dataset contained more than **100,000 samples** and was stored in CSV form for machine-learning experiments.

**Inputs**

- Cartesian position: `x`, `y`, `z`
- End-effector orientation: `beta`

**Targets**

- `theta1`
- `theta2`
- `d3`
- `theta4`

### 4. Neural-Network Model

A baseline multilayer perceptron was first trained and then improved by increasing network depth and applying additional regularization/training controls.

The reported improved model used three hidden layers with 128, 128, and 64 neurons, ReLU activation, L2 regularization, early stopping, and standardized inputs/outputs.

## Reported Results

The improved model achieved the following metrics in the original project report:

| Metric | Reported value |
|---|---:|
| MAE | 0.6530 |
| RMSE | 1.0421 |
| R² | 0.9998 |

The predicted-versus-reference plots in the report show close agreement across the evaluated joint variables. These results should be interpreted within the simulated-data setting of the project; no physical-robot validation was performed.

## Research Development

This project established the initial SCARA modeling and simulation foundation for later research on payload estimation, passive learning, and the value of active information-gathering motions in repeated robotic manipulation.

A subsequent research study extends the SCARA work toward uncertainty-aware payload identification and batch-level decision-making.

## Repository Contents

```text
.
├── README.md
└── report/
    ├── undergraduate_report_fa.pdf
    └── isme2025_project_paper_fa.pdf
```

- `undergraduate_report_fa.pdf` — full Persian undergraduate project report
- `isme2025_project_paper_fa.pdf` — Persian technical paper prepared in ISME2025 format

## Source-Code Availability

The original MATLAB and Python implementation files are no longer available. This repository therefore serves as an archival research portfolio containing the original reports, methodology, experimental description, and reported results. No unavailable source code is claimed or reconstructed here.

## Notes on Reproducibility

Because the original implementation and dataset are not available, the numerical results in this repository should be treated as **reported results from the archived project documents**, not as independently reproducible outputs from the present repository.

## Citation

If you refer to this project, please cite it as an undergraduate research project by **Ali Ajam**, supervised by **Dr. Hassan Sayyadi**, Department of Mechanical Engineering, Sharif University of Technology, 2025.
