# Navier-Stokes Solver

A grid-based Navier-Stokes equations solver (fluid and smoke simulation) written in Objective-C++ and Metal. An older version of the project written for the CPU, using the Raylib framework, is also included.

## Build and Run
```bash
make
./bin/smoke_gpu
```

### CPU Version
```bash
cd CPU_version
make
./smoke_cpu
```

## Controls
- Left Click: Drag to apply velocity to the fluid
- Right Click: Click/Drag to emit smoke into the grid
- Scroll Wheel: Adjust brush radius
- Space: Pause/Resume the simulation
- R: Reset the simulation
- 1: Smoke visualization (Default)
- 2: Speed visualization
- 3: Toggle Divergence (Pressure Error) visualization
- B: Toggle Solid Mode (Not in CPU version)

---

## Technical Details
Many of the algorithms used for this simulation were found in the [course notes](https://www.cs.ubc.ca/~rbridson/fluidsimulation/fluids_notes.pdf) from the University of British Columbia on Fluid Simulation.

This project solves the Navier-Stokes equations for incompressible fluids using the projection method on a staggered grid. The pressure Poisson equation is solved using Gauss-Seidel iteration. The GPU version specifically utilizes [Red-Black Gauss-Seidel](https://en.wikipedia.org/wiki/Gauss%E2%80%93Seidel_method#Parallel_version) to enable parallel execution across the grid. Advection for both velocity and smoke is handled via a semi-Lagrangian method.
