# Linearly Programming

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/linearly.png" alt="Linearly Programming" width="600" 
/>

- A problem with an objective function and a list of constraints
- Such problems can be solved with linearly programming
- You can also drop the objective function and solve for just the constraint
- Solving with both objective function and constraints is an optimization problem
- Solving with just the constraints is a feasibility problem
- In real world situations, we solve these problems using linear programming techniques

## Constraint Graph Definition

The constraints graph for system Ax&le;b is a weighted graph `G={V, E}`.

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/constraintgraph.png" alt="Constraint Graph Definition" width="600" 
/>

There is a vertex v<sub>0</sub> that is connected with all other vertices with zero `wt`.
## Feasibility Problem Example

**Convert to system of constraints.**

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/constraints.png" alt="Linearly Programming" width="600" 
/>

**Convert to a compact matrix form.**

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/compact.png" alt="Linearly Programming" width="600" 
/>

**Convert to a constraint graph.**