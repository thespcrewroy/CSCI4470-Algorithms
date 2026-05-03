# Dynamic Programming Approaches to APSP

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/dpbased.png" alt="DP Solution" width="600" 
/>

- l<sub>ij</sub>: shortest path from vertex v<sub>i</sub> to v<sub>j</sub>
- Vertices: v<sub>1</sub>, v<sub>2</sub>, and v<sub>3</sub>
- l<sub>ii</sub> = 0
- For the APSP problem, we are going to calculate the `L` matrix to determine the distances

## Notes: First DP Solution

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/breakdown.png" alt="DP Solution" length="200" width="200" 
/>

- Shortest path from vertex v<sub>i</sub> to v<sub>j</sub> of length `r`.
- l<sub>ij</sub><sup>r</sup> = l<sub>ik</sub><sup>r-1</sup> + w<sub>kj</sub>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/param.png" alt="Parameterization" length="400" width="400" 
/>

- Similar method to the matrix chain multiplication problem
- Break down the problem to right-side and left-side with the optimal bracket `k`
- Find `k` by varying all the values of `k`, taking the one that gave the minimum multiplication
- l<sub>ij</sub><sup>r</sup> = min{l<sub>ik</sub><sup>r-1</sup> + w<sub>kj</sub>}
- l<sub>ij</sub><sup>r</sup>: shortest path of length `r` does not exit between v<sub>i</sub> and v<sub>j</sub>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/param1.png" alt="Parameterization 2" length="400" width="400" 
/>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/param2.png" alt="Parameterization 3" length="100" width="150" 
/>