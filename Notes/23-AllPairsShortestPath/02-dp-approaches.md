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

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/param1.png" alt="Parameterization 2" length="400" width="400" 
/>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/param2.png" alt="Parameterization 3" length="100" width="150" 
/>

- Similar method to the matrix chain multiplication problem
- Break down the problem to right-side and left-side with the optimal bracket `k`
- Find `k` by varying all the values of `k`, taking the one that gave the minimum multiplication
- l<sub>ij</sub><sup>r</sup> = min{l<sub>ik</sub><sup>r-1</sup> + w<sub>kj</sub>}
- l<sub>ij</sub><sup>r</sup>: shortest path of length `r` does not exit between v<sub>i</sub> and v<sub>j</sub>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/drop.png" alt="Parameterization 4" length="400" width="400" 
/>

- We vary `k` for all the values from  1 to `n`
- `k = j` at one point of time, resulting in **l<sub>i</sub><sup>r-1</sup> + w<sub>jj</sub>**
- However, w<sub>jj</sub> becomes 0 since it is a diamond element
- We end up with just l<sub>i</sub><sup>r-1</sup> when `k = j`, which is same as the first term
- Thus, the first term is embedded in the second term, making it redundant
- We drop the first redundant term

## Notes: First DP Solution Example

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/exampledp.png" alt="DP Example" width="300" 
/>

- l<sub>ij</sub><sup>1</sup>: shortest path of length 1 between v<sub>i</sub> and v<sub>j</sub> <br>
- l<sub>ij</sub><sup>1</sup>: w(v<sub>i</sub>, v<sub>j</sub> ) <br>

<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/weightmatrix.png" alt="Weight Matrix" width="400" 
/>

- L<sup>1</sup> = W (L<sup>1</sup> is initialized with weight matrix `W`) <br>
- Recursively iterate `n - 1` times
    - `n`: number of vertices
    - `n - 1`: number of edges in the path
    - L<sup>1</sup> &rarr; L<sup>2</sup> &rarr; ... &rarr; L<sup>n-1</sup>
- L<sup>3</sup> is the final solution in this example since there are 4 vertices

**Calculate l<sub>12</sub><sup>2</sup>**
<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/dp1.png" alt="DP Part 1" width="400" 
/>

l<sub>12</sub><sup>2</sup> = &infin;. No change.

**Calculate l<sub>13</sub><sup>2</sup>**

l<sub>13</sub><sup>2</sup> = &infin;. No change.

**Calculate l<sub>14</sub><sup>2</sup>**

l<sub>14</sub><sup>2</sup> = &infin;. No change.

**Calculate l<sub>21</sub><sup>2</sup>**
<p align="center">
  <img src="https://github.com/thespcrewroy/CSCI4470-Algorithms/blob/main/Notes/assets/dp2.png" alt="DP Part 2" width="400" 
/>

l<sub>21</sub><sup>2</sup> = -4. Store `k = 4` <br>

Shortest path of length 2 from vertex v<sub>2</sub> to v<sub>1</sub> is -4.