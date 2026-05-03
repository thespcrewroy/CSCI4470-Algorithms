# Single Source Shortest Path Problem

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/sssp.png" alt="Single Source Shortest Path Problem" height="600" width="600" />

- There is a single source vertex
- You calculate the shortest distance between the source and all the remaining vertices

## Notes: SSSP Algorithms
1. Bellman Ford (Dynamic Programming)
2. DAG Based Algorithm (Dynamic Programming)
3. Dijkstra's ALgorithm (Greedy)

## Notes: Veriation Problems

### Single Destination Shortest Path Problem

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/sdsp.png" alt="Single Source Destination Shortest Path Problem" height="600" width="600" />

- You have a single destination vertex
- Solve by flipping the directions, and then using one of the SSSP Algorithms

### Single Pair Shortest Path Problem

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/spsp.png" alt="Single Pair Shortest Path" height="600" width="600" />

- You just have one pair
- The SSSP problem algorithms already calcualtes the shortest distance between any path
- Solve by running any of the SSSP algorithms on either one of the two vertices

### All Pair Shortest Path Problem

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/apsp.png" alt="All Pair Shortest Path" height="600" width="600" />

- Calculate the shortest path between all the pairs
- Solutions
  - Dynamic Programming (very high in cost and storage)
  - Run Dijskstra's on all the vertices one time (naive approach, but the best appraoch)

