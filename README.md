# ROV Control System Simulator

This project implements a control system for a Remotely Operated Vehicle (ROV). The system reads an ROV’s thruster configuration and Xbox controller input, then translates commands into thrust outputs using linear algebra and a 6 Degrees of Freedom (6 DOF) motion model.

🚀 Project Overview

Goal: Simulate and validate the motion of an ROV given controller inputs and thruster placement.

Core Challenge: Convert high-level movement requests (surge, sway, heave, roll, pitch, yaw) into precise thruster outputs.

Mathematical Foundation: Linear algebraic modeling of thrust vectors, transformation matrices, and torque calculations.

🔑 Key Features

6 DOF Motion Control: Supports surge, sway, heave, roll, pitch, and yaw.

Error Handling & Safety:

Thruster outputs are constrained to [-1, 1].

If a thruster exceeds bounds, it is immediately clamped and removed from the optimization process, ensuring valid physical results.

Numerical Stability:

Applied machine epsilon bounding (np.finfo(float).eps) to minimize floating-point error.

Scaled system matrices to reduce relative error propagation in SVD computations.

Weighted Control Scaling:

Each degree of freedom can be prioritized by a weight vector, ensuring some thrusters or motions are considered “more important” during optimization.

Least-Squares with Constraints:

Solves underdetermined or overdetermined systems using SVD.

Iteratively removes out-of-bounds thrusters to find a valid feasible solution.

📂 Project Structure

main.ipynb – Contains the rov class that would be used to generate optimized thruster settings needed for ROV devices to move underwater.
test#.txt - Contains all the test cases required for the simulation. 

🛠️ Tech Stack

Python: Core simulation and matrix computations

NumPy & SciPy: Linear algebra operations

Jupyter Notebook: Prototyping and testing



