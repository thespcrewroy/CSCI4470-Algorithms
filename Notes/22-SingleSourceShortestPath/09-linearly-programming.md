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

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/graph.png" alt="Finalized Constraint Graph" width="600" 
/>

**Add v<sub>0</sub> by connecting it to all vertices with a 0 weight transition.**

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/v0.png" alt="Start Vertex Added" width="600" 
/>

> In this image, all 0 transitions to the vertices from v_0 are not drawn because the graph would look very messey according to the instructor. However, YOU HAVE to draw all of the 0 transitions out of v_0 to the 5 vertices to get credit.

**Run Bellman Ford on v<sub>0</sub>.**
- We cannot use Djikstra because graph can have negative weights
- We cannot use DAG because graph can form a cycle

&delta;(v<sub>0</sub>, v<sub>0</sub>) = x<sub>1</sub> = -5 <br>
&delta;(v<sub>0</sub>, v<sub>2</sub>) = x<sub>2</sub> = -3 <br>
&delta;(v<sub>0</sub>, v<sub>3</sub>) = x<sub>3</sub> = 0 <br>
&delta;(v<sub>0</sub>, v<sub>4</sub>) = x<sub>4</sub> = -1 <br>
&delta;(v<sub>0</sub>, v<sub>5</sub>) = x<sub>5</sub> = -4 <br>


<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/answer.png" alt="Final Solution" width="600" 
/>