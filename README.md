# Adaptive Nonconforming Finite Elements: Error Estimation and Mesh Adaptivity

This repository contains a high-performance numerical simulation package written in FreeFem++ to solve 2D model diffusion problems using nonconforming finite elements. Following advanced error estimation theories, the framework constructs guaranteed a posteriori error estimators via potential and equilibrated flux reconstructions. It drives an automated adaptive mesh refinement loop to optimize local mesh densities around physical singularities.

---

## Key Features & Methods Implemented

* **Crouzeix-Raviart Finite Elements:** Discretizes the partial differential equation using nonconforming piecewise linear polynomials ($P1_{nc}$), which enforce continuity strictly at the midpoints of mesh edges rather than at the vertices.
* **Potential Reconstruction:** Performs a localized post-processing step to map the nonconforming solution $u_h$ onto a continuous, $H^1$-conforming Lagrange workspace ($P^1$ or $P^2$) while strictly imposing essential boundary constraints.
* **Equilibrated Flux Reconstruction:** Utilizes Raviart-Thomas mixed finite elements to construct an equilibrated flux vector field satisfying exact conservation properties.
* **Guaranteed A Posteriori Error Estimation:** Computes explicit, mathematical upper bounds for the exact solution error using the residual energy contributions of the reconstructed potential and flux fields.
* **Dörfler Adaptive Mesh Marking:** Features an automated mesh refinement cycle driven by the local error distribution, utilizing Dörfler marking parameters to selectively subdivide cells and optimize computational degrees of freedom.
* **Singular Regime Configurations:** Benchmarked across both smooth analytical domains and non-convex L-shaped domains featuring a sharp vertex singularity to stress-test adaptive convergence.

---

## Key Findings & Insights

### 1. Nonconforming Mechanics & Structural Reconstructions
* **Midpoint Continuity Advantages:** Crouzeix-Raviart discretizations yield localized computational benefits but generate discontinuous fields across element edges. The potential and flux reconstructions successfully heal these discontinuities, transforming raw numerical inputs into smooth, physically consistent fields.
* **Guaranteed Efficiency:** The equilibrated flux reconstruction technique provides a mathematically proven upper bound for the error. This bound is fully reliable, completely avoiding uncalibrated empirical constants.

### 2. Mesh Adaptivity & Convergence Acceleration
* **Conquering Edge Singularities:** On uniform meshes, domain singularities severely degrade the convergence rate of standard solvers due to infinite gradient blowups at re-entrant corners. 
* **Optimal Degrees of Freedom:** Implementing the adaptive refinement loop automatically concentrates degrees of freedom around the re-entrant vertex. This effectively restores optimal algebraic convergence rates while minimizing total system memory requirements.

---

## Repository Structure

* `project_final.edp`: Unified FreeFem++ source code containing mesh initializers, variational formulation blocks for the $P1_{nc}$ system, reconstruction routines, and the loop controlling adaptive mesh subdivision.
* `report_project_final.pdf`: Full mathematical and academic report outlining the theoretical proofs, error estimator derivations, and graphic convergence plots (in French).

---

## Requirements & Installation

To run this simulation framework, you must have FreeFem++ installed on your machine.
