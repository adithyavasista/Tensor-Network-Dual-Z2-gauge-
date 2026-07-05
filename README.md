# Z2 Gauge Theory 2D PEPS Simulation

This repository contains the Julia codebase for simulating real-time dynamics of a $Z_2$ gauge theory using 2D Projected Entangled Pair States (PEPS).

### Physics Overview
The simulation computes the total electric flux scaling under a quantum quench. 
* **Current Setup:** The code simulates a pure **bulk quench** by placing the mid-flip defect at the exact geometric center `(4, 3)` of an $8 \times 6$ dual lattice. This allows the entanglement wavefront to expand radially across all four directions.
* **Observables:** Calculates the difference in total electric flux between a vacuum state (SCV) and the defect state (MID) using local Pauli expectations.

### Dependencies
This codebase utilizes the ITensors ecosystem. You will need Julia installed along with the following packages:
* `ITensors.jl`
* `ITensorNetworks.jl`
* `NamedGraphs.jl`
* `Observers.jl`

### Execution
To run the simulations sequentially across multiple bond dimensions (e.g., $D=8$ through $D=14$):


## 🚀 New Feature: Belief Propagation (BP) Simulation

We have added an optimized script, `Belief_Propagation_Dual_gauge.jl`, which utilizes **Belief Propagation (BP)** to handle the tensor network operations much more efficiently.

*   **Simple Update Time Evolution:** Trotterized time evolution is applied via BP-assisted simple updates. This allows for faster gate application while maintaining numerical stability through local truncation.
*   **Global Observables:** Instead of standard edge-by-edge contraction, this script maintains a `BeliefPropagationCache`. This allows us to batch measure the $ZZ$ observables across the entire 2D lattice simultaneously, drastically reducing computation time.

To run this specific simulation:
```bash
julia dual_gauge.jl
julia Belief_Propagation_Dual_gauge.jl
