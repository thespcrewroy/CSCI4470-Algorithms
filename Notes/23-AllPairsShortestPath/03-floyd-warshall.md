# Floyd Warshall Algorithm

- Dynamic programming based solution
- Looks at all the intermediate vertices in the shortest path from v<sub>i</sub> to v<sub>j</sub>
- p<sub>ij</sub> = (v<sub>1</sub>, v<sub>2</sub>, ..., v<sub>k</sub>) (for k intermediate vertices)
- p<sub>ij</sub>: shortest path from v<sub>i</sub> to v<sub>j</sub>
- 2 Possibilities
  - If vertex v<sub>k</sub> is not part of the shortest path from v<sub>i</sub> to v<sub>j</sub>, then intermediate vertices are (v<sub>1</sub>, v<sub>2</sub>, ..., v<sub>k-1</sub>)
  - If vertex v<sub>k</sub> is part of the shortest path, then we go from v<sub>i</sub> to v<sub>k</sub>, and then from v<sub>k</sub> to v<sub>j</sub> (v<sub>i</sub> ... v<sub>k</sub>, v<sub>k</sub> ... v<sub>j</sub> )

## Notes: Objective Function

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/obj.png" alt="Floyd Obj Func" length="400" width="400" 
/>

d<sub>ij</sub><sup>k</sup>: shortest path from v<sub>i</sub> to v<sub>j</sub> with `k` intermediate vertices

## Notes: Example

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/floyd.png" alt="Floyd Graph" width="300" 
/>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/d0.png" alt="Floyd Graph D0" width="300" 
/>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/d1.png" alt="Floyd Graph D1" width="300" 
/>

- d<sub>ij</sub><sup>0</sup>: shortest between v<sub>i</sub> and v<sub>j</sub> with 0 intermediate vertices
- d<sub>ij</sub><sup>0</sup>: w(v<sub>i</sub>, v<sub>j</sub>)
- D<sup>0</sup> = W (D<sup>0</sup> is initialized with weight matrix `W`)
- Recursively iterate `n` times
    - `n`: number of vertices
    - D<sup>1</sup> &rarr; D<sup>2</sup> &rarr; ... &rarr; D<sup>n</sup>
- D<sup>4</sup> is the final solution in this example since there are 4 vertices
- There is no change from D<sup>0</sup> to D<sup>1</sup>
- We will only show the squares that change below for D<sup>1</sup> ... D<sup>4</sup> to save time

**Calculate d<sub>34</sub><sup>2</sup>**
<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/prego.png" alt="DP Floyd 2" width="400" 
/>

d<sub>34</sub><sup>2</sup> = 4. Store `k = 2`.

Shortest path of from vertex v<sub>3</sub> to v<sub>4</sub> with two intermediate vertices is 4.