# 2D-Navier-Stokes-solver-

## Overview:
This code presents a robust MATLAB-based solver for the 2D Navier-Stokes equations on structured grids, accommodating both Dirichlet and Neumann boundary conditions. It employs a central difference scheme for spatial discretization and offers various time integration schemes such as Runge-Kutta Chebyshev, RK2, and explicit Euler. Helmholtz Decomposition is utilized to compose the velocity field into solenoidal and non-solenoidal counterpart. The Chorin projection method is utilized to decompose the velocity field into divergence-free and gradient components, ensuring solution accuracy and satisfying the incompressibility constraint of the Navier-Stokes equations.
Designed with modularity in mind, the code facilitates easy adaptation to different 2D flow problems. Furthermore, it seamlessly handles passive scalar transport, making it suitable for simulating heat transfer and species transport scenarios.

## Usage:
1. Preprocessing:
   - `setparameters`: Configure simulation parameters.
   - `Domain`: Generate the simulation mesh.
   - `Initialization_matrices`: Initialize pressure and velocity matrices.
   - `constructMatrixPoisson`: Create and solve the Poisson matrix using the Preconditioned Conjugate Gradient (PCG) method.
   - `Velocity_boundary_conditions`: Set boundary conditions for velocity.
   - `CreateTimeseriesArrays`: Initialize arrays for kinetic energy and dissipation.
   - `GatherTimeseries`: Store kinetic energy and dissipation rate values for each time iteration.
   - `Residuals_log_intialization`: Prepare arrays to store and plot residuals during simulation.
2. Simulation Run:
   - Execute the simulation loop by running NS2d.m.
   - Time integration schemes (SolveNS_Euler, SolveNS_RKC, or SolveNS_RK2) solve the Navier-Stokes equations.
3. Post-processing:
   - `animation_to_video`: Convert stored frames to a video for visualization.

## Components:
- **Parameters Configuration (`setparameters`):** Customize parameters like grid size and viscosity.
- **Mesh Generation (`Domain`):** Create the grid for the simulation.
- **Matrix Initialization (`Initialization_matrices`):** Set up matrices for equation solving.
- **Poisson Equation Solver (`Poissonsolver`):** Solve the Poisson equation using PCG.
- **Advection Skew Function (`advectionskew`):** Compute the skew symmetric convection term.
- **Laplacian Calculation (`Laplacian`):** Compute the Laplacian of a vector field.
- **Velocity Correction Function (`Velocity_correction`):** Correct the velocity field.
- **Derivative Calculation (`Dx`, `Dy`):** Compute first-order derivatives efficiently.

## Outputs:
- **Velocity Fields:** Obtain velocity values within the domain.
- **Data Saving:** Save relevant data for analysis.

## Notes:
- **Derivative Handles:** Utilize derivative handles for efficient computation via vectorization.
- **Poisson Solver Function:** A specialized function is implemented for stable and efficient Poisson equation solving.
- **Boundary Conditions:** Accommodate both Dirichlet and Neumann boundary conditions for flexibility.
- **Advection Skew Function:** Compute the crucial skew symmetric convection term accurately.
- **Modularity:** The modular design allows for easy customization for various flow problems.
- **Limitation:** Primarily designed for structured 2D grids; might not be suitable for unstructured grids without modification. Attention to grid resolution is crucial for turbulence simulations. Low-resolution DNS simulations can be performed with suitable filters applied to the Navier-Stokes equations.
- **Extension to Heat Transfer Problems:** With minor adjustments, the code handles passive scalar transport, enabling simulation of heat transfer and multiphase species transport problems.

Ensure appropriate parameter and boundary condition settings for accurate simulation and choose the suitable time integration scheme based on accuracy and computational efficiency requirements.
