# Dynamic Programming Approaches to APSP

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/dpbased.png" alt="DP Solution" width="600" 
/>

- l<sub>ij</sub>: shortest path from vertex v<sub>i</sub> to v<sub>j</sub>
- Vertices: v<sub>1</sub>, v<sub>2</sub>, and v<sub>3</sub>
- l<sub>ii</sub> = 0
- For the APSP problem, we are going to calculate the `L` matrix to determine the distances

## Notes: First DP Solution
shortest path from vertex v<sub>i</sub> to v<sub>j</sub> of length `r`.

<p align="left">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/breakdown.png" alt="DP Solution" length="200" width="200" 
/>

l<sub>ij</sub><sup>r</sup> = l<sub>ik</sub><sup>r-1</sup> + w<sub>kj</sub>