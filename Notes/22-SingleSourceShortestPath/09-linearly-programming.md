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

## Notes: Constraint Graph Definition

The constraints graph for system Ax &le; b is a weighted graph `G={V, E}`.

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/constraintgraph.png" alt="Constraint Graph Definition" width="600" 
/>

There is a vertex v<sub>0</sub> that is connected with all other vertices with zero `wt`.


## Notes: Feasibility Problem Example

**Convert to system of constraints.**

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/constraints.png" alt="Linearly Programming" width="600" 
/>

**Convert to a compact matrix form.**

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/compact.png" alt="Linearly Programming" width="600" 
/>

**Convert to a constraint graph.**

1. x<sub>1</sub> - x<sub>2</sub> &le; 0 &rarr; 0(x<sub>2</sub>, x<sub>1</sub>)
2. x<sub>1</sub> - x<sub>5</sub> &le; 0 &rarr; -1(x<sub>5</sub>, x<sub>1</sub>)
3. x<sub>2</sub> - x<sub>5</sub> &le; 0 &rarr; 1(x<sub>5</sub>, x<sub>2</sub>)
4. x<sub>3</sub> - x<sub>1</sub> &le; 0 &rarr; 5(x<sub>1</sub>, x<sub>3</sub>)
5. x<sub>4</sub> - x<sub>1</sub> &le; 0 &rarr; 4(x<sub>1</sub>, x<sub>4</sub>)
6. x<sub>4</sub> - x<sub>3</sub> &le; 0 &rarr; -1(x<sub>3</sub>, x<sub>4</sub>)
7. x<sub>5</sub> - x<sub>3</sub> &le; 0 &rarr; -3(x<sub>3</sub>, x<sub>5</sub>)
8. x<sub>5</sub> - x<sub>4</sub> &le; 0 &rarr; -3(x<sub>4</sub>, x<sub>5</sub>)