# Johnson's Algorithm For Sparse Graphs

- Better than the DP solutions

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/transform.png" alt="Transformed Johnson" width="400" 
/>

- Reweighs the graph such that there are no negative edges
- Utilizes Bellman-Ford algorithm to reweigh the graph
- Runs Djikstra on all the vertices in the reweighed graph
- h:V&rarr;R is a function that maps a vertex `v` to some real number `r`

## Notes: Objective Function

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/objjohn.png" alt="Johnson Algo Objective Function" length="400" width="400" 
/>

### Updating Weights Example

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/p1.png" alt="Updating Weights" length="400" width="400" 
/>

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/p2.png" alt="Updating Weights" length="400" width="500" 
/>

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/p3.png" alt="Updating Weights" length="100" width="100" 
/>




